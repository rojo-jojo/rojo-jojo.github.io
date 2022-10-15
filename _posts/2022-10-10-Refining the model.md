Previous post - <a href="https://rojo-jojo.github.io/2022/10/07/Building-a-tweet-classification-model.html">Building a tweet classification model</a>
<br>
If you are following this project series then we saw in the previous post that the first iteration of my model performed poorly. How can we make it better?
<br><br>
So my first throught was that there is some problem with the size of my corpus. This was my feature creation process -
- I had to convert my text tweets to numeric
- For that I took my corpus and found the number of occurences for each word. Then in each tweet I replaced the word with the count calculated for that word
- Now each tweet had a numeric representation(lets call it tweet vector). 
- Before training my model I had to make all my tweet vectors of same length. I calculated length of the longest tweet in my corpus. If any tweet's length was smaller than the length of longest tweet I add trailing zeros to that tweet vector to make it's length equal to the longest tweet vector
- Now all my tweet vectors were of same length and ready to train.

<br>
I trained my model and saw that my AUC was 0.57. This was worse than what I was expecting. Those of are familiar with NLP would see that I tried to implement a Bag of words(BOW) represention to create text to numeric vectors. But someone well versed in BOW and looking closely into my steps could easily find a major flaw of in my implementation of BOW. Here it is
<br><br>
<b>What I did</b>
<br>
I took the whole corpus and calculated occurrence of each word. <i> Then I went to each tweet and replaced each word with it's count of occurences in the corpus</i>. This is where I went wrong.
<br><br>
<b>The right way</b>
<br>
- Keep an array of counts for all unique words in the corpus Suppose if there are 1000 unique words in your data then your array of counts would be of length 1000. 
- <u>For each tweet there will be a copy of this array of counts. For the words existing in the tweet the array of counts will keep the count value of those words. 
- All other positions will get a default value like 0 or -1</u>
<br>

For beginner an example could help. You can google bag of words and find detailed explainations.
<br>

After correctly implementing my BOW algorithm I realised that there was no need to make all vectors of same length. If correctly implemented BOW will make all tweet vectors of same length. So I went ahead and trained my model again. The classifier specs remain same as before i.e. it is a sklearn RandomForestClassifier with n_estimators=500 and there are my results now
 - AUC: 0.65
 - f1 score: 0.44
 - precision: 0.77
 - accuracy: 0.94

It is a MAJOR improvement for me. Though we know that these results are far from usable and we can do much more here. But we won't improve it for now cause we have to go to the next steps and they are
1. create a REST API to serve our model's prediction
2. create a front-end to interact with our model

If you are a data science enthusiast and especially someone into NLP, you can just fork my repo and try to upgrade the model. The only constraint is that for now you cannot use deep learning architectures like tensorflow, keras, PyTorch etc because I am going to host this model on a cloud and the DL model serving cost might become a big expense later. So ML based enhancements are welcome and there are many other word representations to try. Text me on linkedIn if you want to contribute.