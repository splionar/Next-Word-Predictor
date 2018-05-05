### About This Application

This application is the capstone project of Data Science Specialization by John Hopkins University on Coursera in collaboration with SwiftKey.

### Background

Predicting the words one intend to type can speed up typing and reduce misspelling. This has been enabled by the exponential growth of text data and implementation of Natural Language Processing (NLP) algorithm. 

This application demonstrates the capability of creating next word predictions and making word completion based on user input sentences/phrases.

### Method
The predictive model is created by learning text data from Twitter, news, and blog corpus. N-grams of size 1,2 and 3 are obtained from the sample after appropriate cleaning, i.e. conversion to lowercase, removal of number and special characters. 

Backoff model is then generated by the following rules: Generate 4 words prediction using frequencies of the learned N-grams with the higher degree of N-gram as priority. Discount/smoothing is not applied in this model to speed up computation of the predictions, while caching mechanism is implemented.
	
### Algorithm Example

- **Goal:** Make prediction for word completion

- **Input Sentence:** "I want to go to am" 

- From the sentence above:
  + **trigram input:** go to 
  + **bigram input:** to 
  + **filter:** am (no filter if sentence is ended with space)

- **Algorithm will work as following:**

  + Look for the top 4 words starting with "am" from trigram frequencies table. 

  + If less than 4 words appear, look for the top words starting with "am" from bigram frequencies table that are different from previous results to fill in the blanks.

  + If still less than 4 words appear, look for the top words starting with "am" from unigram frequencies table that are different from previous results to fill in the blanks .

- **Caching mechanism:** Each time the user key in new filter, if there is no change in trigram and bigram input, possible word predictions are cached so that filtering only needs to scan through the cached possible predictions, instead of keep generating n-gram frequencies table.

### Links

- Code and source files: https://github.com/splionar/Next-Word-Predictor
- Milestone report describing exploratory data analysis and text mining: http://rpubs.com/splionar/milestone-report
- Presentation: http://rpubs.com/splionar/presentation-nwp
