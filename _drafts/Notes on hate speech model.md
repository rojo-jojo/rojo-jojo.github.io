This is a free stye notes for the ML part of the project

# Research
I have some background in data analysis and machine learning. Not much on the deep learning side but enough to quickly implement something from sklearn or the keras library. My theoritical knowledge is questionable. The general approach I am taking to this problem is not of a data scientist but of a software engineer. I will build code pipelines to throw as multiple data processing and machine learning methodologies at the dataset.
<br>
I'll start with writing code to create a pipeline where I get to a stage where my data is ready to just call model.fit() on a varity of sklearn models. Data representation is what matters here. I have no idea about how to thing about representation for running text data through an algorithm that can only handle 2-D tabular data. Let's google things.

This article is a good practical summary - [Click Here](https://stackabuse.com/text-classification-with-python-and-scikit-learn/)
<br>

This is what our ML journey is looking like
1. Clean your data and standardize it. Below are some standard steps
	- removing special characters
	- removing multiple spaces
	- convert everything to same case (lower prefered)
	- Lemetization (dont know what it is yet)
2. Strategies to convert our data from text to numeric so that our ML model can train on it
	- Bag of words
	- Word embeddings

## Data cleaning and representation
The actual development we are going to do for the pre-processing is quite simple. So we can give more time for some fundamentals.

**Why do data-cleaning in text analytics?**
A machine learning model is a mathematical function i.e. it takes a vector of inputs, does some computations and gives a value as output. Since we mentioned mathematical, we have to understand that the input our algorithm will accept only numerical values. How does that work?
We perform an operation on the text to convert it to numeric. Below is math like equation to make things more dificult for you

> T ---> f(T) ---> N

***T** is a text. **f** is an operation we apply on **T** which results in **N**,a numeric type or to simplify a number.*
<br><br>
You might ask what exactly is this f and what is it doing. If you ever come across names like bag of words, tfidf, word embeddings, then know that you are looking at an "f". They convert text to numeric form but what's special about them is that make meaningful conversions. You can also refer this process of applying a function f as *encoding* the text to numeric.

> If you are familar with label encoding from feature engineering in ML then the concept here is similar.

Before going into the encoding or numerification of the text, let us understand few other important concepts in text pre-processing which could be useful later.
<br>
**Tokenization**
<br>
Tokenization is breaking raw text into words, sentences called tokens. This tokenization helps the machine learning algorithm in interpreting the meaning of the text by analyzing the
sequence. There are different methods of tokenizing the data which can affect the performance of your algorithm. There is a blog link somewhere down there which can help you understand them better. A quick example to understand tokenization
> Text - "ML is over-rated . But it pays well."<br>
> Word tokenized form - ['ML','is','over-rated','.','But','it','pays','well.']<br>
> Sentence tokenized form - ['Ml is over-rated', 'But it pays well']<br>
[More on tokenization techniques](https://towardsdatascience.com/tokenization-for-natural-language-processing-a179a891bad4)<br>
[Implementing with NLTK in python](https://www.nltk.org/api/nltk.tokenize.html)
<br>

**Stemming and Lemmatization**<br>
In a nutshell the goal of both of these techniques is to reduce a devirational word to a common base form. <br>
> car, cars, car's, cars' --> car
<br>
[Read more about these here](https://nlp.stanford.edu/IR-book/html/htmledition/stemming-and-lemmatization-1.html)







We will skip the cleaning part of removing spaces, special characters etc
