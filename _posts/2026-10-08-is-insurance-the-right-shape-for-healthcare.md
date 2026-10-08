---
layout: post
title: Is Insurance The Right Shape For Healthcare?
comments: true
excerpt: "There's no food insurance and no shelter insurance, yet both are more basic needs than healthcare. So why did care, of all things, settle into the shape of a monthly premium?"
---

So this one is again that was always there in mind - why is insurance the shape for healthcare mostly in US and some of the other countries? Having grown up in India - and having experienced care that was completely out-of-pocket, moving to Sydney with govt sponsored care was different. Apart from the consumer experience, having sold to healthcare setups in 80+ countries - it was always fascinating to me how care models looks so different and seemingly works.

The easiest surface explanations that you usually hear are healthcare is something so basic a need that it should be insurance covered always (and in that poorer countries don't have money to cover for all - hence the difference). Now, there can be several counter-points to these but I'll start with a couple:

1. I'm sure food and grocery should be even more basic than care - why is there no food insurance (equivalent of it saw in 90's India - ration system)
2. And why the shape insurance? Like it could be free for everyone. Like why the whole idea of pooling capital from everyone to give everyone a similar service of care?

Now on 2, I think the simplest answer you would hear is costs could be catastrophic unpredictably and hence that needs cushioning, so insurance is the peace of mind solution to that consumer anxiety. The subsequent question is does the underlying economics work? Like if you think about it - people are anxious about food, shelter, movie to watch, staying fit and what not - one could always say "give me $5 every month and I'll make sure you find the product".

If you think about that proposition for a bit, Netflix or even gym membership come surprisingly close to that proposition - pay a subscription fee and you can resolve anxiety/concern/need when it arises. Look at it the other way, insurance is a subscription paid by user or their employer or the govt. for the service of care. And for most parts, all subscriptions are pooling of usage across users - light user compensating for the heavy user.

![Figure 1: A subscription is a pool](/images/insurance_shape/fig1-subscription-pool.svg){: style="margin:auto; display:block;"}

*Figure 1. A subscription is a pool. The fee sits near the average, so what light users pay for and don't use funds what heavy users use beyond it (illustrative).*

This framing, fundamentally pushed to consider the question - in case of no constraint whatsoever, what kind of goods or services do lend themselves to be subscription vs a metered product. Like the same tokens on an AI tools GUI for users is subscription, for API users as metered use. So I think it first makes sense to understand left to market forces, what shape of a product/service would win the users.

## So what is it that makes an economic good subscription-like?

Once you recognise that subscriptions are sort of pooling usage across users, it's easy and quite intuitively deduct that if the usage is fundamentally variable across users - the seller of the good benefits from selling subscriptions. To add the smoothening of the revenue (as a previous CCO, I can strongly vouch that I loved the curves than the random up and down bars!) - one would argue a seller should always sell subscriptions if they have the pricing power in the transaction.

It almost seems right - if you look at Adobe, Microsoft 365 or even your friendly local gym - they seem to benefit from the no-shows or low usage quite as much (a lot of my friends feels they underuse these services!), so clearly subscriptions are working out for the service providers. One could fit the narrative the opposite way for product that you feel you use a lot (and there are enough providers to choose from) like music streaming, AI services - you might feel subscription is steal deal rather paying per music you play.

But that's definitely far from truth. The thing is the previous answer is easy to justify from personal bias - you'll be heavy user of some services where you feel it might be a steal deal and for services you use sparingly, you feel you're quietly paying for someone else's binge. Everyone is a heavy user of something and a light user of something else, so everyone has a story that fits. But if it were true, Colgate (given their market share in US of 35% *([Colgate](https://www.sec.gov/Archives/edgar/data/21665/000115752323000106/a53291858ex99.htm))* or India about ~50%) would sell toothpaste on subscription and so would Visa (sitting at the middle of 58% of all transactions *([PSG Wealth](https://www.psg.co.za/news-and-publications/articles/feature/winelands19dec24-eng))*) should charge subscriptions. So the best way to make sense can't be from a seller POV. Whatever is economically viable and offers the best price for the same item would win customers.

## So what do buyers want?

The founding principle is buyers want to pay as little as possible per unit - and payment is both in terms of money and mental cognition. So the best model that wins most customer business is zero payment from users (and charge through ads - here's [Fred of USV explaining how ads are eventual outcome for a lot of B2C businesses](https://avc.com/2010/01/the-ny-times-freemium-strategy/)). It might be easy to consider the cognition costs is trivial, but studies have shown US gym members prefer monthly subscriptions amounting to ~$17/visit when it would have costed $10/visit if they took it individually *([DellaVigna and Malmendier, 2006](https://eml.berkeley.edu/~ulrike/Papers/gym.pdf))*. Same with phone plans *([Lambrecht and Skiera, 2006](https://www.anderson.ucla.edu/documents/areas/fac/marketing/paying_too_much.pdf))*. So, the cognition cost of thinking at every use is a friction they like to avoid. Seen this way, the perspective flips. Buyers would happily take unlimited everything. It's the sellers who hold back - and they hold back whenever they can't afford for the next use to be free.

## So what can a seller afford next use to be free?

The principle is defined by how much does the next use cost extra and what's the cap for the usage? So if the extra unit's marginal cost is much smaller compared to the fixed cost (the operating leverage or variable cost are other lens on the same decision) then it's easy for seller to offer the next use at zero price. So if you already have a gym, the additional one hour slot is free or if you have a movie hall, the additional seat is free or if you have a phone towers already setup, the additional call or message is free. Whereas if you sold toothpaste, the additional toothpaste's variable cost (of material) is way higher than the fixed cost of manufacturing and corporate costs.

The second principle is also key - how much of your usage is naturally capped and can it be resold. Your views for Netflix is capped at the time you have (hence Netflix caps the number of places you can watch it under a subscription *([Netflix](https://help.netflix.com/en/node/24926))*). Same goes for your AI service GUI usage - it's capped by amount of time you have to type in and get answers. Same for mobile data (to some extent capped by how much you can browse). However a toothpaste if you get unlimited, can be stored and resold.

But there's still some explaining more to do - electricity and even Visa for that matter charge per usage? It seems they put a meter on the usage although the basic logic of marginal cost once you have the electricity network or card network is fairly small and one can argue that the cap of usage if somewhat rationally capped. So if you go back to the point of not using meter in the first place was the visibility of meter deters usage. If the meter is invisible or used by an API - the human cognition is gone (same reason why agents would pay per usage rather than subscription as well). So a meter is worth it if doesn't deter spend.

Finally, the last principle is that any product that basically buys out a capacity for a user (used or not). Like a landlord can't rent out your flat while you're on holiday or consulting firm parks a team member for a client and the member can't work for anyone else. So the cost is paid a fixed amount per time period. Again some of the human labour's inability to be at multiple places at one time is changing with AI.

## So left to the market

The winning product looks like decided by the following set of principles:

1. Buyers want the next use to be free.
2. A seller can give them that only if both coditions hold 
    A) one more use costs it little 
    B) people can't use or hoard an unlimited amount. Otherwise it meters.
3. Even when free is affordable, a seller still meters if the meter earns more than it costs - when the value of each use is visible and varies a lot, and nobody has to hesitate before each one.
4. Anything kept aside for a particular buyer gets charged per month, on top of whatever 2 and 3 decide.

![Figure 2: The four principles as a decision flow](/images/insurance_shape/fig2-four-principles.svg){: style="margin:auto; display:block;"}

*Figure 2. The four principles as a decision flow. Principle 4 adds a monthly charge on top of whichever way the first three land.*

Most things land clearly on one side and stay there for decades. Toothpaste has always been per tube. Newspapers have always sold subscriptions. The fun ones sit near the line and flip whenever the costs move - mobile data, movie passes, and right now, AI.

## Now, healthcare

When I first ran healthcare through this naively years back, I was fairly sure where it would land. A hospital is a huge fixed cost - the building, the equipment, doctors on salary. So one more patient should cost very little, and it should look like Netflix. Pay a membership, walk in whenever. Sounded like something an insurance like subscription should be able to pay for.

But it turns out hospital is an airline. The building is the plane, and every case burns fuel - drugs, consumables, implants, lab reagents, sterilisation, theatre time, and nursing hours rostered to how many beds are full. In Indian private hospitals, materials alone typically run 20 to 30 percent of revenue *([Narayana Health](https://nsearchives.nseindia.com/corporate/Narayana_03082026132353_SE_revised_Investors_presentation_1.pdf))*, and in a knee or cardiac case the implant can be most of the bill. Even the doctor on 'salary' is often on a revenue share or targets that count procedures. So the variable cost for an additional patient is the higher part of the cost.

![Figure 3: A hospital is an airline](/images/insurance_shape/fig3-hospital-is-an-airline.svg){: style="margin:auto; display:block;"}

*Figure 3. What one more use costs the seller (illustrative). One more stream costs Netflix almost nothing; one more patient arrives with their own fuel bill. Cost shares from [Narayana Health's Q1 FY27 results](https://nsearchives.nseindia.com/corporate/Narayana_03082026132353_SE_revised_Investors_presentation_1.pdf).*

So point 2 says meter especially in a country like US where the marginal cost is the expensive clinician labour denominated. That's exactly what the cash-pay world does - in India, across most of Southeast Asia, in the cash-pay corners of the US. Per visit, per scan, per procedure.

Cost doesn't fully settle it, though. Mexico has thousands of small clinics attached to pharmacies, where the pharmacy pays the rent and a consult costs a couple of dollars (very less marginal cost) *([Mexico Business News](https://mexicobusiness.news/health/news/mexicos-pharmacy-clinics-evolve-primary-care-and-drive-growth))*. That's about as cheap as clinical care gets, and they still charge per visit. Something beyond cost is going on.

I think it's this. You can't tell whether you needed what you got - not before, and often not even after. Did I really need that scan? Economists call this a credence good (I wrote a lot about it the *[last article](https://rohitghosh.github.io/2026/09/30/iron-carbon-phase-diagram-in-economics/)*). Now look at what a flat fee does to the doctor. Paid per visit, a doctor earns more by doing more. Paid a flat fee, a doctor earns more by doing less. Doing too much is visible and feels like care. Doing too little is invisible and looks exactly like good judgement. (I've never met anyone who walked out of a clinic complaining they were examined too thoroughly.) If you can't check, you pick the failure you can see. So the patients pick the meter. Not to forget that gyms can create demand by selling aspiration, most of reactive care can't and only predictive care can 'generate' demand per se.

![Figure 4: Two ways to pay a doctor, two ways to fail](/images/insurance_shape/fig4-credence-two-failures.svg){: style="margin:auto; display:block;"}

*Figure 4. Each way of paying a doctor has its own failure. Only one of the two is visible to the patient.*

The US has been running the experiment. Direct primary care sells a flat monthly fee for unlimited GP access. It has been around for longest with very slow growth and de-growth. In 2024, 58% of memberships were paid for by employers, a share that keeps climbing *([Hint Health](https://blog.hint.com/employer-trends-in-direct-primary-care-2025-why-more-employers-are-turning-to-dpc))*. The model is growing through companies. People buying it for themselves are the shrinking part.

So where does flat pricing work for individuals in healthcare? Where there's no clinician and the marginal cost really is zero - meditation apps, wearables, health records. Where you can check the result yourself - a diabetes clinic chain in Mexico sells unlimited annual memberships because blood sugar is a number you can see *([IDB Lab](https://bidlab.org/en/news/expanding-access-affordable-diabetes-care-mexico-through-innovative-health-delivery-models))*, and orthodontists sell a fixed price for the whole course because the result is in the mirror. And where the quantity is fixed - dental plans with two cleanings a year, the annual health check-up package, the fixed-price surgery package. A hospital is happy to take on the risk of how complicated your knee replacement gets. It won't take on the risk of whether you'll need one.

![Figure 5: Where flat pricing works in healthcare](/images/insurance_shape/fig5-where-flat-works.svg){: style="margin:auto; display:block;"}

*Figure 5. Where flat pricing works for individuals in healthcare, and the one risk a hospital will and won't carry.*

## So, is insurance the right shape?

Which brings me back to where I started. If people buying care for themselves pick the meter, where does insurance - a flat monthly fee for care - come from? The usual answer is the one from the start: costs can be catastrophic, so insurance buys peace of mind. That's true about how buyers feel. It doesn't predict if the shape survives economics.

Remember the conditions and why healthcare by default is likely to be metered. Yes, as per rule 2A it's the variable costs, especially expensive clinical labour in US and western countries. So, if a system were to own sites and then clinicians on salary, maybe it can. Hey that sounds like Kaiser Permanente or even Optum of US. But there's third condition where the seams seems to come apart for a subscription like service. It's the cap on usage. Remember that by rule 2B, the usage should be somehow be capped.

Now that demand of rule 2B mandates that such a subscription product be sold to a group. The idea being as a group the usage is fairly capped since under-users can compensate for over-users and if they don't because a major condition/need surfaces across population (like ozempic, covid etc) - then you raise premium or fight it with prior-auth. The groups were fraternal lodges in US, UK, Australia and New Zealand (in early 1800s - early 1900s) *([Beito](https://fee.org/articles/lodge-doctors-and-the-poor/))* and later WWII and laws around tax benefits made the employers the pool to sell to *([JSTOR Daily](https://daily.jstor.org/subtle-subsidies-shaped-u-s-health-care))*. A group of any other collection than healthcare-needs based stops adverse selection making the rule 3 possible of sorts. This is also the reason why individually sold insurance suffered from adverse selection (Mending, Bright Health, Friday Health etc) *([Fierce Healthcare](https://www.fiercehealthcare.com/providers/40000-must-seek-new-coverage-georgia-places-insurtech-friday-receivership))*.

The problem with the insurance thing is tries to achieve satisfy rule 2B, by pooling when it's not a pool-able problem in the first place. Let me explain more:

1. As I explained earlier, the pool contain costs as long as there's no population-wide needs but whenever there's a better innovation that's demanded by a majority - the insurance can't cover it without raising premium on everyone. But the problem is not just majority, even a thing like Ozempic or regular blood draws or an ADHD consultation - things that a significant but not majority of people might find needs for - would have to come after subscription renewal at newer costs. Don't even get me started on the fact that your employer has to choose the best plan.
2. Akerlof's unraveling *([Akerlof, 1970](https://www.jstor.org/stable/1879431))*: Once a cost rises let's say due to a newer cancer medication or even weight loss, the healthy ones leave the group first since they feel they are paying higher for the same. Adverse selection kicks in and weaker ones are left behind, increasing costs even higher on them.

![Figure 6: Akerlof's unravelling](/images/insurance_shape/fig6-unravelling.svg){: style="margin:auto; display:block;"}

*Figure 6. Akerlof's unravelling. Every new costly need starts another turn of the loop.*

The pools that last - Kaiser, Germany's sickness funds, Brazil's employer plans, Australia or UK public health - have two things in common. Someone other than the patient decides who's in (mostly government). And someone other than the patient controls how much care gets supplied. The ones that failed were missing one of the two. The individually sold insurance plans shut down or pivoted to selling to employers. US hospital systems that launched their own insurance plans mostly lost money - only four of the roughly forty started since 2010 were profitable in 2015 *([Healthcare Dive](https://www.healthcaredive.com/news/most-new-provider-sponsored-health-plans-not-profitable/444753/))* - partly because Americans insist on seeing doctors outside the network. The hospital owned the risk without owning the decisions.

![Figure 7: The pools that last](/images/insurance_shape/fig7-pools-that-last.svg){: style="margin:auto; display:block;"}

*Figure 7. The pools that last have someone other than the patient deciding both who is in and how much care is supplied. The ones that failed were missing one of the two.*

So what do people actually do when nobody pools for them? I grew up watching it. They don't buy a monthly plan for everyday care. They pay per visit, and for the big stuff they lean on savings, family, gold, and sometimes a loan. When they do buy insurance, it's almost always hospital-only cover - a cap on the big episode, with everyday care still metered. Hospitals have even built the matching product: a fixed-price surgery package with complications included. The line between metered and pooled turns out to be the size of the episode compared to what the household can pay. A GP visit or a blood test sits below it, so it's metered. Heart surgery sits above it. And above that line, individuals can't build the pool on their own. Either somebody else holds it - an employer, a government - or the care turns into debt, or it doesn't happen at all.

![Figure 8: The episode line](/images/insurance_shape/fig8-episode-line.svg){: style="margin:auto; display:block;"}

*Figure 8. The line between metered and pooled is the size of the episode compared with what the household can pay (illustrative).*

So, in all, I think insurance is not the right shape at all for care needs. By principle 2B, it needs a pooling by employer or other group (after ensuring variable cost is minimal through employing clinician labour by principle 2A) which would have held together if the demands of care remained at one level. Since it doesn't and innovation comes in pockets, the principle 3 leads to fragile groups (unless held together by govt or someone with a mandate).

## And then there's AI

AI makes a doctor's thinking cheap (the marginal cost is lower), and it makes predicting who'll get sick a lot sharper. First one pushes parts of healthcare towards the Netflix bucket making subscription possible. The other quietly breaks pools. The combination is what makes a new world possible at once.
