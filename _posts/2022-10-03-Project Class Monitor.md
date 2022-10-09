## Introduction
I saw this tweet by Eth founder Vitalik regarding frauds on twitter platform and how they should open their API for external entities to detect such cases. I am an admirer of Vitalik's work. I found this problem intriguing and decided to solve a similar problem i.e., **how to detect offensive/hate speech on twitter?**
<br>
We will call our solution <em>Class Monitor Project</em>. 
<br>
>Class Monitor - An designation extented by the school authority to a class room which offically holds no power but is annoying anyway
<br>

## Plan
Detecting offensive/hate tweets on twitter is not a novel idea. In fact I saw this an year ago on a competitive data science challenge. I will leverage some of their data for training to see how it fares. ML will be a very small part of our project. What I am interest in is building a complete system. I intend to keep it simple at first and then in different phases over-engineer it to the level of a fancy university project which kids can copy and get a C minus grade. I haven't thought through the whole thing but here is my idea for phase I

### Phase I
1. Build a simple classification model for hate tweets
2. Serve the model with flask api and host it(locally to begin with)
3. Create a Web front-end (JavaScript or TypeScript?) where user can enter a tweet and check whether it is classified as hate speech or not
4. Create a backend where
	- Tweet is taken from front-end
	- Tweet is saved in a local DB
	- ML API is called to get tweet classification
	- Classification response is send to the front-end and saved in the local DB

<br><br>
Read further here
<br>
<a href = "https://rojo-jojo.github.io/2022/10/07/Building-a-tweet-classification-model.html"> 1. Building a tweet classification model using NLP </a>