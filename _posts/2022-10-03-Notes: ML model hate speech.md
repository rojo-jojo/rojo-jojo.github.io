This is a free stye ntoes for the ML part of the project

# Research
I have some background in data analysis and machine learning. Not much on the deep learning side but enough to quickly implement something from sklearn or the keras library. My theoritical knowledge is questionable. The general approach I am taking to this problem is not of a data scientist but of a software engineer. I will build code pipelines to throw as multiple data processing and machine learning methodologies at the dataset.
<br>
I'll start with writing code to create a pipeline where I get to a stage where my data is ready to just call model.fit() on a varity of sklearn models. Data representation is what matters here. I have no idea about how to thing about representation for running text data through an algorithm that can only handle 2-D tabular data. Let's google things.

Found this article - [Click Here](https://stackabuse.com/text-classification-with-python-and-scikit-learn/)
<br>
Summary from this:
- We need to clean and standardize our data
- Some standard actions are
	- removing special characters
	- removing multiple spaces
	- convert everything to same case (lower prefered)
	- Lemetization (dont know what it is yet)
- Strategies to convert our data from text to numeric so that our ML model can train on it
	- Bag of words
	- Word embeddings
