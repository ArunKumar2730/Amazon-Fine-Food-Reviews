# Implementation-of-Bag-of-Words

The Bag of Words(BoW) concept which is a term used to specify the problems that have a 'bag of words' or a collection of text data that needs to be worked with. The basic idea of BoW is to take a piece of text and count the frequency of the words in that text. It is important to note that the BoW concept treats each word individually and the order in which the words occur does not matter.
Using a process which we will go through now, we can convert a collection of documents to a matrix, with each document being a row and each word(token) being the column, and the corresponding (row,column) values being the frequency of occurrence of each word or token in that document.

Here,I have taken Amazon food review dataset (source : kaggle). 

we will be using sklearns count vectorizer method which does the following:

It tokenizes the string(separates the string into individual words) and gives an integer ID to each token.
It counts the occurrence of each of those tokens.
Please Note:

The CountVectorizer method automatically converts all tokenized words to their lower case form so that it does not treat words like 'He' and 'he' differently. It does this using the lowercase parameter which is by default set to True.
It also ignores all punctuation so that words followed by a punctuation mark (for example: 'hello!') are not treated differently than the same words not prefixed or suffixed by a punctuation mark (for example: 'hello'). It does this using the token_pattern parameter which has a default regular expression which selects tokens of 2 or more alphanumeric characters.
The third parameter to take note of is the stop_words parameter. Stop words refer to the most commonly used words in a language. They include words like 'am', 'an', 'and', 'the' etc. By setting this parameter value to english, CountVectorizer will automatically ignore all words(from our input text) that are found in the built in list of english stop words in scikit-learn. This is extremely helpful as stop words can skew our calculations when we are trying to find certain key words that are indicative of spam.
We will dive into the application of each of these into our model in a later step, but for now it is important to be aware of such preprocessing techniques available to us when dealing with textual data.

Step 1: Data cleaning before implementiong BOW

Step 1.1 - Remove HTML tags
Instruction - Use BeautifulSoup library to perform this step 

Step1.2 - Remove https links from text
Instruction -  Use regular expression module to perform this

Step1.3 - Remove numbers from text
Instruction - Use regular expression module to perform this

Step1.4 - Remove Special character from text
Instruction - Use regular expression module to perform this

Step1.5 - Remove Stopwords
Instruction - CountVectorizer takes care of this internally. We need to pass paramter stop_words = 'english.

Step1.6 - Remove Punctuation
Instruction - CountVectorizer takes care of this internally


Step 2: Implementing Bag of Words in scikit-learn

Now that we have implemented the BoW concept from scratch, let's go ahead and use scikit-learn to do this process in a clean and succinct way. We will use the same document set as we used in the previous step.

Instructions: Import the sklearn.feature_extraction.text.CountVectorizer method and create an instance of it called 'count_vector'.
Data preprocessing with CountVectorizer()

In Step 1, we implemented a version of the CountVectorizer() method from scratch that entailed cleaning our data first. This cleaning involved converting all of our data by removing HTML tags and removing all special characters etc. CountVectorizer() has certain parameters which take care of these steps for us. They are:

lowercase = True The lowercase parameter has a default value of True which converts all of our text to its lower case form.

token_pattern = (?u)\b\w\w+\b The token_pattern parameter has a default regular expression value of (?u)\b\w\w+\b which ignores all punctuation marks and treats them as delimiters, while accepting alphanumeric strings of length greater than or equal to 2, as individual tokens or words.

stop_words = The stop_words parameter, if set to english will remove all words from our document set that match a list of English stop words which is defined in scikit-learn. Considering the size of our dataset and the fact that we are dealing with SMS messages and not larger text sources like e-mail, we will not be setting this parameter value.

You can take a look at all the parameter values of your count_vector object by simply printing out the object as follows:

The get_feature_names() method returns our feature names for this dataset, which is the set of words that make up our vocabulary for 'documents'.


Note:

Here I have done implementing BOW on the whole dataset.But before implementing BOW,split dataset into train and test set to avoid data leakage problem.




