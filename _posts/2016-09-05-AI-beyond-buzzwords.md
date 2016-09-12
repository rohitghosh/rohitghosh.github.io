---
layout: post
title: AI - Beyond Buzzwords & Comparisons To Human Abilities
comments: true
excerpt: Any heated argument on AI these days soon ends up in a predictable trajectory - so DeepMind's AlphaGo beats Go champ,Tesla to compete with Uber using AI driven cars, ethical dilemma of driver-less cars and finally - would robots overpower humankind (on sidelines of the last debate would be venue of the Matrix themed D-Day - Earth or Mars !)...if you’re reading buzzwords everyday and wondering what's AI, what's the big deal about it and where we stand as of today compared to human-like capabilities of AI

---
Any heated argument on AI these days soon ends up in a predictable trajectory - so DeepMind's AlphaGo beats Go champ, Tesla to compete with Uber using AI driven cars, ethical dilemma of driver-less cars and finally - would robots overpower humankind (on sidelines of the last debate would be venue of the Matrix themed D-Day - Earth or Mars !)

So if you’re writing a sci-fi book or you're a tarot-reader then don’t bother to read further.
But, if you’re reading buzzwords everyday and wondering what's AI, what's the big deal about it and where we stand as of today compared to human-like capabilities of AI; may be give the post a read.

### What is AI & what is not ?

AI, coined in 1956 at University of DartMouth by psychologist Rosenblatt,
was defined vaguely as a field aimed to make machines do the same work as humans.
In the years to follow, conventional Machine Learning (ML) algorithms became norm of the day in AI till
something strangely powerful happened in 2012. This was the ImageNet (an image recognition competition)
breakthrough by Prof. Hinton (in Google now) and his students based on Le Net, a Convolutional Net originally
designed by Le Cunn (in FB now), the-then prof at NYU.
This breakthrough was strange cause till then Convolutional Nets (CNNs) had hardly shown any usefulness
beyond hand-written character recognition (here's a [video](https://www.youtube.com/watch?v=FwFduRA_L6Q) on Le Cunn training CNN
back in '93 at Bell Labs) and yet it was powerful  as it  entailed an explosion in AI over
the coming years in ways people in academia and industry had hardly foreseen. See the figure below.
![NIPS & ICML Papers submitted](/images/newplot.png "NIPS & ICML Papers submitted")

To put it simply, AI agents learn from data, preferably huge amounts of data - instead of programmer himself hard-coding and modelling reactions to various use cases. The idea is

>Don't model the World but model the Brain and only then let the modelled Brain learn.

Modelled after brain, in it’s simplest avatar, a net essentially consists of a graph of nodes which processes input sequentially. By ‘processing’ I meant multiplying output from previous node by a weight matrix and applying non-linearity to the product. Learning the weight matrices is the whole game !

Also, it’s not data mining where the pattern is mined from data and then requisite changes are made in the algorithm as per observed pattern. AI is more end-to-end. So when I see a lot of startups using smart but hard-coded logic based algorithms (based on data or otherwise) under alias of AI, I feel it’s gravely misleading.

### Why the hype around AI this time around ?

Interestingly, after perceptrons were introduced in 1956, it was followed by immense hype regarding it's capabilities, sort of what we see around AI now. And sadly, there was a lot of disappointment that followed it. In fact, there were couple of AI winters in the intermediate years. ('74-'80 & '87-'93)

The reasons, both time around, were lack of computational power, coupled with cuts in funding because of economic crashes. Post ’93 even though it regained some lost ground following Le Cunn’s success in handwritten digit recognition, it wasn’t until 2012 that using nets became mainstream, again.

#### So what’s happening right this time around ?

The nets that were hardly 10 layers deep pre-2012, can now reach 1000 layers easily without much trouble in training. Deeper nets kicked off the field of Deep Learning - the deeper the nets, the better the results tend to be in general. The reasons are majorly -

* <em>Higher computational powers</em>: The computational gains because of advent of GPU and parallelised computation was a major force behind the boom of AI this time. In fact, parallelised computation was the recipe for Prof. Hinton's Image Net success in 2012.
* <em>Data, enormous data</em>: Most importantly, the sole reason AI has seen success beyond expectations has been availability of data - something that could’ve only happened in post-internet, post-Google & post-FB era.
* <em>Funding</em>: Apart from the above reasons, the amount of money that has been flowing intp AI in the current boom has been phenomenal- the funding for AI based startups has been pegged somewhere at $310mn for the year 2015.
![Funding in AI Space](/images/AI_quarterly_finance_20160203.jpg)

### What AI can and what it can't

Apparently, AI is pretty good when it comes to visual recognition tasks - take for example - a net that [detects sentiment from facial expression](http://cs231n.stanford.edu/reports2016/022_Report.pdf) (the GIF below, taken from YouTube video demo of HappyNet) or one that can do  stuff such as- make any [celeb gaze whichever way you like](http://sites.skoltech.ru/compvision/projects/deepwarp/)

So when it comes to comparing with human performance in Computer Vision (object detection from images), AI has been able to recognise with 6.8 % error central objects in images compared to humans (the human being researcher Andrej Karapathy himself) with 5.1 % error. When it comes to semantically segmenting out objects from images, recent breakthroughs such as U-Nets are showing some great potential but they involve a lot of supervision costs (i.e. pixel-by-pixel labelling) except this very [recent paper](https://arxiv.org/abs/1506.02106) by Stanford Prof. Li Fei-Fei. Even though from advent of AI-driven cars, it could seem that AI has conquered computer vision, but it is very far from over. In fact, there are [papers](http://arxiv.org/pdf/1606.03556v2.pdf) which prove that machines see quite differently from human beings.

In speech recognition as well, AI has been pretty good (with less than 8% error on vocabulary consisting of all alphabets and numbers). AI has been exceptional at playing strategy games such as Chess, AlphaGo. Also, at [Qure](http://blog.qure.ai/), we can see AI performing better than some physicians on medical diagnosis, something also [reported by IBM’s Watson](http://www.wired.co.uk/article/ibm-watson-medical-doctor) as the underlying tasks involve visual recognition and segmentation tasks at their core.

Even AI is able to [dream](http://deepdreamgenerator.com/) and generate images on its own - in a sense it can develop a sense of creativity - through a technique known as <strong>adversial training</strong>. Though it's not like the creativity we have - to think about objects that never existed. The kind of creativity that AI displays is on the lines of being able to predict a picture correctly when the picture's central part is cropped, after obviously having seen similar images during training.

But when it comes to basic comprehension tasks like bAbI tasks or MC Tests- answering based on comprehensions like -  “Sandra travelled to the office.Sandra went to the bathroom. Where is Sandra? “ AI still lags behind (around ~60% accuracy without supervision, that is when the AI isn’t supplied with any info on where in the comprehension to look for answer vs ~70% accuracy when it’s provided with the cues). Also, when it comes to answer questions based on picture, or  word-sense disambiguation or Named Entity Recognition ( recognising from “Jack was playing tennis yesterday” - that Jack is a person, tennis is a sport and yesterday is time) AI has not been anywhere close to human level accuracy.

## Concluding thoughts

So that was AI-101, with a peek into world of AI and the truth behind it. So while AI can generate some music, predict the [next person dying on popular TV series GoT](http://www.mirror.co.uk/tech/meet-artificial-intelligence-knows-whos-7806263), save the [world from wildfire](http://www.huffingtonpost.in/entry/detecting-ignition-of-wildfires-sooner_b_8028786), [detect flirting from chats](http://www.geekwire.com/2016/patook-llc/) - but currently it has got some serious limitations as well. Well, Artificial Narrow Intelligence (ANI) , Artificial General Intelligence (AGI) & Artificial Super Intelligence (ASI) may be good for hypothetical discussions, in reality it’s probably far-fetched as of today. The boom in AI is real for sure, but the hysteria around AI not so much. And this is something important to remember because the first AI winter was a result of the immense hysteria around perceptrons followed by huge disappointment. If we want to avoid something similar this time, then all of us - researchers, practitioners, investors etc.- need to have realistic expectations in line with current state-of-art research. Obviously, AGI is not impossible in long run given the way things are changing everyday, but if you’re fearing a robot takeover soon or betting your money on AGI taking over on chat bots, it may be a good idea to just sit back and think again.

<strong>P.S.</strong> : If you are a Deep Learning Scientist reading this, and are interested for a challenging as well as impacting role at qure.ai , write to us quickly.

If you're a startup founder reading this and need help in brainstorming the right AI path for your startup given current advances, feel free to contact me. More than happy to help !

<strong>P.P.S.</strong> : All the opinions expressed above are my personal opinions, and don't reflect by any means opinion of Qure or any other firm mentioned above.
