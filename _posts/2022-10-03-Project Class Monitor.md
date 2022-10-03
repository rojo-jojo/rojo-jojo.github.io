## Introduction
I saw this tweet by Eth founder Vitalik regarding frauds on twitter platform and how they should open their API for external entities to detect such cases. I found this problem intriguing and decided to solve a similar problem i.e., **how to detect offensive/hate speech on twitter?**

<blockquote class="twitter-tweet"><p lang="en" dir="ltr">So many scam accounts have blue checkmarks these days.<br><br>Seems like a complete failure of blue checkmarks in their current form. I&#39;m definitely seeing the wisdom of turning twitter into an open API and letting third parties try to make the best UIs to solve these problems. <a href="https://t.co/CIwAdpRAkv">pic.twitter.com/CIwAdpRAkv</a></p>&mdash; vitalik.eth (@VitalikButerin) <a href="https://twitter.com/VitalikButerin/status/1576275977352536065?ref_src=twsrc%5Etfw">October 1, 2022</a></blockquote> <script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script>
<br>
You know the phrase that "To a man with a hammer, everything looks like a nail". This is exactly what I am going to do here. I am a data scientist by profession so that is my hammer. 
We will call our solution "Project Class Monitor". 
<br>
>Class Monitor - An designation extented by the school authority to the student body which offically holds no power but is annoying anyway

## Plan
Detecting offensive/hate tweets on twitter is not a novel idea. In fact I saw this an year ago on a competitive data science challenge. I will leverage some of their data for training to see how it fares. ML will be a very small part of our project. What I am interest in is building a complete system. I intend to keep it simple at first and then in different phases over-engineer it to the level of a fancy university project which kids can copy and get a C minus grade. I haven't thought through the whole thing but here is my idea for phase I

### Phase I
1. Build a simple classification model for hate tweets
2. Serve the model with flask api and host it(locally to begin with)
3. Create a Web front-end (JavaScript or TypeScript?) where user can enter a tweet and check whether it is classified as hate speech or not
4. Create a backend where
	- Tweet is take from front-end
	- Tweet is saved in a local DB
	- ML API is called to get tweet classification
	- Classification response is send to the front-end and saved in the local DB