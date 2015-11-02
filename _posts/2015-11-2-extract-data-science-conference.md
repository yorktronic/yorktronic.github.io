---
layout: post
title: Highlights from Extract data science conference
---

Last week I attended the Extract data science conference in San Francisco, that was sponsored by <a href="https://import.io" target="_blank">import.io</a>. Mostly I attended the "Data Stories" sessions, where people from various companies such as Netflix, Lyft, Yelp, and others presented on some of the problems they worked on and methodologies they used to solve them, among other things. Below are some of the highlights:

## Yelp ##
Travis Brooks, head of data @ Yelp, gave a talk on how they determined the <a href="http://officialblog.yelp.com/2015/01/yelps-top-100-places-to-eat-in-the-us-for-2015.html" target="_blank">Top 100 Places to Eat in the U.S. for 2015"</a> by leveraging data science techniques. This was probably the most interesting talk for me personally, as it was given in a sort of step-by-step problem solving format. Here's a high-level view of the steps:

* Realizing that the relationship between number of reviews and rating have a non-linear relationship with the actual "Bestness" of a place to eat
* Utilizing Smoothing (which is used by IMDB) and Bayesian methods (Dirichlet) to solve the problem
* Discussed "Best" v. "Interesting"

For more information view the Yelp blog post linked above, and for even more data-driven food fun check out <a href="http://fivethirtyeight.com/burrito/#brackets-view" target="_blank">Nate Silver's Burrito Bracket</a>, and for more nerdy math fun check out <a href="https://github.com/CamDavidsonPilon/Probabilistic-Programming-and-Bayesian-Methods-for-Hackers">Bayesian Methods for Hackers</a>.

## Blockspring ##
Paul Katsen from <a href="https://www.blockspring.com/" target="_blank">Blockspring</a> did a 20-minute demo on how to use Blockspring in Google Sheets and Tableau to quickly and easily pull data from various API's without actually writing code. This was super useful for me as I'm going to use it to pull non-huge datasets for some data science stuff. It's free to use, so give it a shot!

## Lyft ##
<a href="https://lyft.com" target="_blank">Lyft</a> CTO Chris Lambert spoke about how Lyft uses rider data to improve their operations and customer service. One of the more intereting things that Chris talked about was the interrelationship between the algorithms they use -- particularly pricing and availability algorithms, and how adjustments to one can dramatically effect the other. 

For example, if you were to allow a pricing algorithm to determine optimal pricing at a given time, it might recommend a fixed price for all rides that is relatively low. He then discussed how this could impact earnings if they were to subsequently optimize by driver availability. My description is sort of vague but the general idea is that if you have multiple data-driven optimization algorithms, you have to pay close attention to what is running when.

Chris also discussed their simulation platform, which uses historical rider data to allow their engineers to thoroughly test changes throughout their services by simulating a real-time environment such as San Francisco or NYC. Finally, he mentioned using natural language processing for customer support tickets, to properly categorize the nature of each piece of customer feedback in order to better priortize and respond. So, data science for help desk tickets. I wonder if they can automate the free / discounted rides based on negative experiences? 

## Etsy ##
<a href="https://etsy.com" target="_blank">Etsy</a> data scientist Kamelia Aryafar spoke about the challenges Etsy faces in gathering and using data on the listing and sale of such a wide variety of items. With 21 million buyers and 1.4 million sellers of products ranging from vintage bags to steampunk-inspired desk lamps and watches made from old computer motherboards, they had to figure out a sensical way to categorize their data. She went over techniques such as <a href="https://en.wikipedia.org/wiki/Matrix_decomposition" target="_blank">Matrix Factorization </a>, <a href="https://en.wikipedia.org/wiki/Latent_Dirichlet_allocation">Latent Dirichlet Allocation (LDA)</a>, and a lot of A/B testing. 

You can view more information about Kamelia's talk on <a href="https://github.com/karyafar/Extract2015">her github.</a>

## Bai du Research ##
Andrew Ng talked about a lot of over-my-head stuff on deep learning. They utilized deep learning based image recognition technology to develop a wearable computer / camera for the blind, to assist blind people with recognizing the world around them. They also built an app called <a href="http://usa.baidu.com/happy-halloween-baidu-research-introduces-faceyou/" target="_blank">FaceYou</a> for iPhone, which uses your phone's camera to alter your face in realtime. Unfortunately Android users are out of luck :\

## Summary ##
I think a couple of these talks in isolation would've been worth the entry fee, so if you're interested in this kind of stuff, maybe go to the Extract conference next year. I'll be there!

/ty