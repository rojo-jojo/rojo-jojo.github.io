In this article I'll go through the process of building an ML model along with some NLP (natural language processing). Please note that I do not intend to demonstrate this blog as the best way to build an NLP project. What I have in mind is to write code for most of the modules using python standard libraries. Why I want to do that? Firstly, to understand the processes in NLP better. Another reason is that I like to write code for fun, hence I think the more the better. Though this is absolutely not true if you are writing production code.<br>
Since I am not a complete beginner to the field of data science, I cannot claim that my blog with helping beginners understand NLP. There are much better resources on the internet for that. But still if you find any interest in the project and have specific questions you want to ask me then drop a mail to the mail id at the bottom with the phrase "class monitor" in the subject.<br><br>

Let us begin.<br>

I'll start with writing code to create a custom pipeline of these 4 steps - data cleaning, data representation, model training, and model validation. I think data representation part is something that would take-up most of my time since I don't how to translate text data to a form where an ML model can train on it. Let's google things.
<a href = "https://github.com/rojo-jojo/class-monitor"> This is my code repo </a>


Our process -

1. Data cleaning
2. Data representation
3. Model training
4. Model validation

# Data cleaning

I found an article from the top of my regarding what comprises of data cleaning. In a nutshell what we have to do is 

- remove special characters from text
- replace multiple spaces with a single space
- convert everything to same case (lower prefered)
- Tokenization
- Stemming
- Lemetization (dont know what three of these are yet)

[More in this article](https://stackabuse.com/text-classification-with-python-and-scikit-learn/)
<br>
**Tokenization**
<br>
Tokenization is breaking raw text into words, sentences called tokens. This tokenization helps the machine learning algorithm in interpreting the meaning of the text by analyzing the
sequence. There are different methods of tokenizing the data which can affect the performance of your algorithm. There is a blog link somewhere down there which can help you understand them better. A quick example to understand tokenization
> Text - "ML is over-rated . But it pays well."<br>
> Word tokenized form - ['ML','is','over-rated','.','But','it','pays','well.']<br>
> Sentence tokenized form - ['Ml is over-rated', 'But it pays well']

<br>
[More on tokenization techniques](https://towardsdatascience.com/tokenization-for-natural-language-processing-a179a891bad4)<br>
<br>
[Implementing with NLTK in python](https://www.nltk.org/api/nltk.tokenize.html)
<br>

**Stemming and Lemmatization**
<br>
In a nutshell the goal of both of these techniques is to reduce a devirational word to a common base form. Lemmatization reduces a word to it root word also known as a lemma. Stemming also reduces a word to a smaller word, but it is not necessarily a meaningful word<br><br>
> Lemmatization: car, cars, car's, cars' --> car
<br>
> Stemming: car, cars, car's, cars' --> ca

<br><br>
<a href="https://nlp.stanford.edu/IR-book/html/htmledition/stemming-and-lemmatization-1.html">More on lemmatization and stemming </a>
<br><br>
I am not trying that stemming thing. That shit looks unstable to me. I don't know how it even works. I'll just try lemmatization and check if it is adding any real value<br>
We will not discuss removing spaces, special characters etc, as they are self explainatory. You can see the <a href="https://github.com/rojo-jojo/class-monitor/blob/main/build_model/preprocessing.py">preprocessing.py</a> for the actual steps there. 
Let's move on to representation.

# Data Representation
<br>
**What is data respresentation and why we need it?**
<br>
A machine learning model is a mathematical function i.e. it takes a vector of inputs, does some computations and gives a value as output. Since we mentioned mathematical, we have to understand that the input our algorithm will accept only numerical values. How does that work?
We perform an operation on the text to convert it to numeric. Below is math like equation to make things more dificult for you

> T ---> f(T) ---> N

***T** is a text. **f** is an operation we apply on **T** which results in **N**,a numeric type or to simplify a number.*
<br><br>
You might ask what exactly is this f and what is it doing. If you ever come across names like bag of words, tfidf, word embeddings, then know that you are looking at an "f". They convert text to numeric form but what's special about them is that make meaningful conversions. You can also refer this process of applying a function f as *encoding* the text to numeric.
<br><br>
> If you are familar with label encoding from feature engineering in ML then the concept here is similar.

<br><br>
Some definitions before we move on to Bag Of Words<br>

- Document: A document is an individual peice of text on which you want to do an ML operation. Think of a document as similar to a row in tabular data. It represents a single record.

- Corpus: A corpus is the collection of all documents (document is to corpus what row is to a table)

<br>

## Bag Of Words
<br>
BOW is an algorithm that we will implement on our documents in the corpus, that converts the document to a document vector. A document vector is a numeric vector representation of a document in a corpus. Our implementation of BOW will make the concept of document vector clearer.<br>

<b>BOW Algorithm</b>

1. Find all unqiue tokens in your corpus(words for us)
2. For each word get the count of occurrences of it
3. Take every document and replace words in it with the count of occurrences calculated in step two (see bagofwords.py for my implementation from scratch)
4. Pad all text vectors created from tweets to same length. Why? Because every feature vector going into the model should be of the same length.

# Model training

For model training we will start with sklearn models. I have created a <a href="https://github.com/rojo-jojo/class-monitor/blob/main/build_model/train_model.py">train_model.py</a> to log metrics and hyperparameters for the models that I would be experimenting with. This is the <a href="https://github.com/rojo-jojo/class-monitor/blob/main/logs/model_training_logs.jsonl">log file</a>. With very basic feature engineering and a random forest model we are getting poor model performance of f1=0.25 and auc=0.57. I was expecting the initial results to be bad but this is just shit. 
<br><br>
Was not using a standard library for word representation such a bad idea? Do you think not removing stop words screwed us? Is random forest algorithm so 2016 that it can't handle 'AI' problems like tweet classification? I'll try to find out in my next post.

