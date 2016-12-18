---
layout: post
title: If A Data Scientist Drove Uber
comments: true
excerpt: In most of the ceb rides I had my conversation with the cab owner tended towards to the ever-so-important question - “How to generate maximum revenue?” Do I drive at night? Where do I start my trip? What do I optimize for – longer rides in a longer time or repeated shorter rides in the same time? How long do I drive? and alike questions. This post tries to solve some of those questions along with bringing out some interesting insights about cab business.
---

Well, there’s a lot of news recently about founders in the Valley taking to driving Uber for sake of networking and recruiting new talents. Well, in India, also it shouldn’t be far away given I have met some interesting folks on my Uber rides. And, a lot of those times, when the driver was owner of the cab, our conversation tended towards to the ever-so-important question - “How to generate maximum revenue?”

Do I drive at night? Where do I start my trip? What do I optimize for – longer rides in a longer time or repeated shorter rides in the same time? How long do I drive? and alike questions

I had performed the initial analysis on data from NYC for 2013 capturing drop-off and pick-up co-ordinates and time of the day for all cab drivers, along with the fare amount split (fare + tips). The entire script is available on the GitHub link.

#### Interesting Insights First

As a part of Data Exploration, I tried to look deeper into the data to make sense. So I tried plotting distribution of passenger counts, fare amount, tip amount and no of trips per hour at all times of the day.

##### Insight 1 - Busiest times of the day

It starts to drop off sharply at 12 in the night, picks up in the day around morning 8, slackens a bit towards late afternoon, and then peaks at 7 in the night.
![placeholder](/images/NYC_cabs_data/hourwise_dist.png){: style="margin:auto; display:block; height:300px; width:300px; float:right;"}

##### Insight 2 - Busiest locations in the city

The busiest location in the city happens to be an area of 1km2 square around Park Avenue in Manhattan, NYC ( I’ve never been to NYC, just guessing from top 10 busiest locations in NYC, Manhattan seems to be the most happening place !)

![placeholder](/images/NYC_cabs_data/locations.png){: style="margin:auto; display:block; height:300px; width:300px; float:right;"}

##### Insight 3 - Trip fare distribution

Regarding the fare distribution, I was expecting a Gaussian distribution but to my surprise it turned out to be a Poisson. The other more interesting insight was that that in tips the median was roughly 25% of the fare amount. Also, look at the outlier in the tip amount, it goes as high as $200 (that makes suddenly the driving business so lucrative !)

![placeholder](/images/NYC_cabs_data/fare_dist.png){: style="margin:auto; display:block; height:300px; width:300px; float:right;"}


##### Insight 4 - Monday blues !

Interestingly , looking at the patterns of trips for each day of the month, it’s clearly evident that Mondays of the month (1,8,15,22,29) are days with least no of trips . Though 1st was just after Easter Weekend, so presumably the least no. of trips that days justifies for itself.

![placeholder](/images/NYC_cabs_data/daywise_dist.png){: style="margin:auto; display:block; height:300px; width:300px; float:right;"}

<!-- ##### Insight 5 - No of passengers per trip

The no of passenger per trip has some significant trips with 0 passengers. But also more interesting is the no of passengers drops consistently till suddenly it picks up at 5 passengers. -->



#### Going into optimization problem

The first problem was the data was too huge for me to work on my laptop in a small time-frame. So with loss of generality, I cut down on the size by choosing the least, sampling just a single day’s data for purpose of optimizing the revenue of cab-driver.

Though the algo can very well be generalized to any number of day’s data if required. There were a few basic assumptions that I had to carve out for myself for estimating the revenue generation.

- The grid chosen above would be fairly good representation of the dynamics of NYC  and that’s because 1 lat ~ 112 km and 1 long ~ 90 km (at 40 degree lat), so the chosen grid ~600sq km contains >90% of the overall rides
- For optimization of earnings, I have optimized fare amount earnt and not total amount
- There’s a linear relationship between trip fare and trip time, which is to a good extent true, as I could fit a linear regression curve with linear, square & cubic coefficients for time(in minutes) and the coefficients were orders of magnitude separate, proving it’s a linear relationship. (Appendix 2 in the Notebook)
- It’s assumed a driver can choose his own route i.e. find a customer always depending on the route he chooses
- The demand, fare, and trip time for any route and any pickup region don’t vary much within an hour and central measure is a good approximations
- Given there was no information on supply of cabs at a location, it was assumed to be proportional to demand. Hence the probability of getting a cab was assumed uniform, only the demand was checked for a threshold (higher than 20% of the median demand across all regions)

![placeholder](/images/NYC_cabs_data/linear_quations.png){: style="margin:auto; display:block; height:300px; width:300px; float:right;"}

So from the above equations it is clear that for a cab driver to optimize his earning, he would need to optimize for 2 parameters

1. Mean fare per min - The cab should ideally operate on routes that have the maximum fare per min at that hour
2. Trip_time - That is, the cab should never stop in the entire duration. Ideally it should be travelling into demand regions with a minimum demand


The pseudo algorithm would go something like this

Algorithm implemented
1. If starting the day, then search for the region with highest mean fare per min and drive till there before you start the day
2. If drive needs to go to next day, beyond 23:59, make necessary adjustments
3. For selecting the itinerary apply recursively the function to select next best route if end_time is not crossed is as follows
  - For selecting next route,
    - List all the  drop-off locations for which people have used cabs at the start_locaton at the start_time
    - Calculate  the time taken to travel to each of the locations
    - Check for the demand at each of the locations and check if they are above the threshold (20% of median of threshold)
    - Check for the best mean_fare per min across all the routes and choose the best
    - Calculate the time of travel & estimated fare based on data
    - After reaching the dropoff location,adding a 3 mins for transaction, next route selection algo is applied again  
  - If there’s no demand for any cab at the current location (normally happens around late_night) or demand below threshold at all possible dropoff locations
    - Do a 1 degree search for the nearest square on grid which has demand
    - For multiple regions with demand, choose the region with best “mean fare per min” route starting from that region
    - Estimate the time of travel to the region chosen above and add no fare to the corresponding journey
    - If no region found having demand in 1-degree search, keep on increasing degree of search till the best location is found

`def select_next_opt_trip(start_time, start_reg = None, end_time=23,total_fare=0,trip_no=0, start=True,next_day=False):

    #flag to make sure if driving onto next_day, end_time > start_time
    if next_day:
        end_time = end_time +24
        next_day =False

    #flaf to make sure start_time is made to 0, as soon as it's past 23:59
    if start_time >= 24:
        start_time= start_time -24
        end_time = end_time - 24

    #if the flag is start, we start with region which has the highest "mean fare per min" at that hour
    if start:
        start_hour =int(start_time)
        start_reg = df_hourly_rate_per_route['mean_fare_per_min'].loc[start_hour].idxmax()[0]
        print ("He starts in the region {}, [{}] at {}".format(start_reg,grid.reg_to_coord(start_reg),start_time))
        start=False

    # check for the start_time is lesser than end_time - the stopping criterion
    if start_time < end_time:
        if round(start_time)==24:  #to make sure that after 23:30 hrs, start_hour isn't made to be 24
            start_hour =0
        else:                   
            start_hour = round(start_time) # if round(start_time) isn't 24 , round it to nearest integer

        #get the list of possible dropoff regions at the start location at that hour
        df = df_avg_time_routes.loc[start_reg].loc[start_hour]

        #get the avg time for arrival at each of possible dropoff locations
        df['hour_arrival_dropoff'] = round(df['mean_travel_time'].divide(3600) + start_time).astype(int)
        df['expected_demand_arrival_flag'] =0
        df['fare_per_min'] =0

        #get the demand at each dropoff location at the corresponing time of arrival & check if demand > threshold
        #threshold is calculated based on median of demands at that hour across all regions
        for i in range(len(df)):
            try:
                threshold = df_demand_hourly_regions.loc[df['hour_arrival_dropoff'].iloc[i]]['avg_hourly_demand'].median()*0.2
                df['expected_demand_arrival_flag'].iloc[i] = df_demand_hourly_regions.loc[df['hour_arrival_dropoff'].iloc[i]].loc[df.index[i]][0] > threshold
            except:
                continue

        #get the "mean fare per min" parameter for all possible dropoff locations
        for i in range(len(df)):
            try:
                df['fare_per_min'].iloc[i] = df_hourly_rate_per_route.loc[df['hour_arrival_dropoff'].iloc[i]].loc[start_reg].loc[df.index[i]]['mean_fare_per_min']  
            except:
                continue

        #calculate optimum score as product of maximising parameter - "mean fare per min" & demand flag
        df['optimum_score']=df['fare_per_min'].multiply(df['expected_demand_arrival_flag'])

        #see if the best optimum score exists then keep on recursively checking for next rides
        try:
            dropoff_reg = df['optimum_score'].idxmax()

            #if the best score is 0, this implies likely that demand in the best_possible dropoff region is below threshold
            #so search for the nearest best region in the neighbourhood
            if df['optimum_score'].max() ==0:
                print ("Demand is below the threshold, so searching around..")
                adj_reg,travel_time = search_adjacent_region(start_reg,start_time)
                start_time += travel_time
                print ("Starting journey from adjacent region {} at {}:{:2.0f}".format(adj_reg, int(start_time),
                                                                              (start_time-int(start_time))*60))

                return select_next_opt_trip(start_time,adj_reg,end_time, total_fare,trip_no,start,next_day)

            else:

                #Calculate expected dropoff time , fare and keep on recursively choosing the best trip
                dropoff_time = round(start_time + (df['mean_travel_time'].loc[dropoff_reg])/3600,2) + 0.15 # added 0.05 hrs ~ 3 min to account for fare collection and next booking pickup
                trip_no+=1

                #calculate expected fare amount
                expected_mean_fare=round(df_hourly_rate_per_route.loc[start_hour].loc[start_reg].loc[dropoff_reg][' fare_amount'],2)
                total_fare+=expected_mean_fare

                print ('Trip {}: Next dropoff is at {}, [{}] and at {}:{:2.0f}, expected_fare : {:4.2f}'.format(trip_no,
                                                                                       dropoff_reg,
                                                                                       grid.reg_to_coord(dropoff_reg),
                                                                                       int(dropoff_time),
                                                                                       round((dropoff_time-int(dropoff_time))*60),
                                                                                      expected_mean_fare))


                return select_next_opt_trip(dropoff_time, dropoff_reg,end_time, total_fare,trip_no,start,next_day)

        except:

            #if there's no demand at the current pickup region, need to search nearest region for a good pickup
            print ("No demand for cab at region {}".format(start_reg))
            adj_reg,travel_time = search_adjacent_region(start_reg,start_time)
            start_time += travel_time
            print ("Starting journey from adjacent region {} at {}:{:2.0f}".format(adj_reg, int(start_time),
                                                                              (start_time-int(start_time))*60))

            return select_next_opt_trip(start_time,adj_reg,end_time, total_fare,trip_no,start,next_day)



    else:
        print ("It's already {}, time to pack".format(end_time))
        print ("Already earnt fare amount {} for the day!".format(round(total_fare,2)))
        return



def search_adjacent_region(reg,time,degree=3 ):

    print ("Searching adjacent regions around {} at {}:{:2.0f}....".format(reg,int(time),(time-int(time))*60))
    time = int(time)
    best_reg = None
    best_mean_fare = -1

    #vals is the variable indication degree of search
    #if it's 1 degree search , just search adjacent 8 squares for best "mean fare per min" parameter alongwith demand as well
    #search all degrees till we don't find a region with demand
    for vals in range(1,degree):
        reg_1 = int(reg.split(',')[-2])
        reg_2 = int(reg.split(',')[-1])
        reg_list =[]
        # form a list of all the adjacent regions to search on in ith degree search
        for i in range(-vals,vals+1):
            for j in range(-vals,vals+1):
                if (reg_1+i >= 0) & (reg_2+j >=0):
                    reg_element = str(reg_1+i) +',' +str(reg_2+j)
                    reg_list.append(reg_element)
        #for all the regions to be searched in the ith degree check for the best " mean fare per min" if there's demand
        for regs in reg_list:

            try:
                mean_fare = df_hourly_rate_per_route['mean_fare_per_min'].loc[time].loc[regs].max()

                travel_time_list = df_avg_time_routes['mean_travel_time'].loc[(df_avg_time_routes.index.get_level_values('dropoff_reg')==reg) &
                                                 (df_avg_time_routes.index.get_level_values('dropoff_reg') == regs)]

                if (mean_fare > best_mean_fare) & (regs!=reg):
                    best_mean_fare = mean_fare
                    best_reg = regs
                    best_travel_time_list = travel_time_list
            except:
                #if there's no demand at the region being searched , cotinue searching the other regions
                continue

        # if at the end of searching all regions in the ith degree search
        #even if there's one region with demand, we move there
        #if there are more than one, choose the one with best "mean fare per min"
        #if there's no region with demand, increase the degree of search
        if best_reg is not None:
            if len(best_travel_time_list) > 0:
                best_travel_time= (best_travel_time_list.mean())/3600
            else:
                #if there's not any data to predict the average time of travel between current region and adjacent 'best' region
                #take an average time of travel to the adjacent region as 6*degree of search mins (based on observations)
                print("Not enough data to get mean travel time to {} from {}, approx_time : {}".format(reg,best_reg,6*vals))
                best_travel_time = 0.1
            print ("Nearest Best Region found at {} at distance of {} mins ".format(best_reg, round(best_travel_time*60,2)))
            return best_reg, round(best_travel_time,2)
        else:
            print("No good region found near region {} in {} degree search".format(reg,vals))
            continue
        `
##### Insight 5 - Efficient driver

As it turns out, if the driver starts at 8AM, he can earn the median fare ($207) in just 3.11 hours, while for other drivers that is roughly a work of 6 hours
