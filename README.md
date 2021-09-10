# ![](https://ga-dash.s3.amazonaws.com/production/assets/logo-9f88ae6c9c3871690e33280fcf557f33.png) Project 3: Web APIs & NLP

---
## Problem Statement
Can we use natural language processing to predict which subreddit a given post came from based on the language used to identify health related discussions and its for future health applications. 

---
## **Executive Summary**
Natural Language Processing is the ability to train computers to learn, understand, and interpret human language. Why is this important? To be specific, Natural Language Processing, more commonly referred to as NLP, is especially important in healthcare. This is because healthcare is riddled with unstructured data in the form of free text that can be found in elecronic medical records. Big data analytics has shown that a whopping 80% of healthcare documentation is unstructured and largely unused. As you can imagine, paramount relevant patient data lies in this unstructured text, that when paired with NLP, can give way to previously hidden but invaluable insights into understanding quality, improving methods, and better results for patients. 

This all sounds so great, right? Not so fast. A major challenge when utilizing NLP in healthcare is access to this patient data. Additionally, the text in electronic medical records is full of medical shorthand, only interpretable to medical professionals. Fortunately, patient health records are not the only source of data in healthcare. This is where utilization of social media has the power to step in. Reddit was chosen as the source for text as Reddit is a user-generated discussion website where members are able to have discussions on any topic imaginable. This allows for a unique opportunity to track health related discussions for future healthcare related applications. By using Natural Language Processing, this project aims to create a model that can accurately predict which subreddit a given post originated from based on the language and keywords used to begin an exploration of identifying health related discussions and its utility for future healthcare applications.

---
## Process
Natural language processing will be used on two different subreddits to create a classification model that can accurately predict where a given post came from to identify where a new post can be found. 

The two chosen subreddits are r/Askscience and r/longevity. Subreddit r/Askscience describes itself as "Ask a science question, get a science answer" and covers a wide range of topics in the natural and social sciences including Biology, Medicine, Physics, Mathematics, Paleontology, Astronomy, Chemistry, Engineering, Computing, and many more. Subreddit r/longevity is a bit more speciific. It covers all information and research related news on healthspan and rejuvenation covering topics such as biomedical rejuvenation through damage repair, metabolism beyond exercise, fasting, stem cell and gene therapies, etc. Subreddit r/Askscience is an all-encompassing, large community made up of over 20 million members while subreddit r/longevity is a much smaller, more specific community made up of about 90,000 members. 

---
### **Data Collection & Cleaning**
Over 170,000 posts and comments from subreddit r/askscience and r/longevity were collected using the Pushshift API in the data exploration and collection phase. However only 50,000 comments were ultimately used to start the process of data cleaning due to lack of usability with removed and deleted posts. When collecting comments with the keywords 'health' and 'symptoms' I was only able to collect 91 comments from subreddit r/longevity. This posed as an extremely difficult obstacle of severely unbalanced classes which I decided to forego due to time contstraints and scope. Therefore I had to readjust my problem statement. After cleaning the data, an additional 20,000 posts were removed from the dataframe. After data cleaning, the classes were unbalanced, approximately 70% of the comments remained from subreddit r/longevity and approximately 30% remained from subreddit r/Askscience. 

### **Data Transformation and Classification Modeling**
NLP techniques, such as Regex and stopwords, CountVectorizer, and TF-IDF Vectorizer were used to transformed the data into matrix representation. The data was then split into training and testing sets and the classes were stratified to ensure that an equal amount of the unbalanced classes were represented in each training and testing set. The training set was then fit on various classification models, such as Logistic Regression, DecisionTree, Gradient Boosting, ADA Boost, XGB, and Random Forest Classifier. I used tools such as Grid Search and Randomized search to test different parameters. 

Success was evaluated using accuracy score on the testing set. The best model found was Logistic Regression that was fit on TF-IDF Vectorizer. The model was fit on the training set, with an accuracy score of 89%, giving an accuracy score on the testing set which acted as 'unseen' data of 87%. Therefore the model was not overfit and not performing poorly to unseen or new data. 

## **Conclusion and Recommendations**
During the initial exploratory data analysis when collecting the data from Reddit's API, I initally gathered 53,000 posts from both subreddits. 300 out of 53,000 posts had self text and the rest were removed or deleted. Therefore I decided to gather comments with different keywords such as 'health' and 'symptoms' in each comment. Again upon inspection of the texts of these comments, most were deleted or removed. Due to time contraints and scope, I decided to move forward with the process using all comments from both subreddits.

The Logisitc Regression model gave a fairly accurate score of 87% on new data. Some explanation as to why this model performed so well may be that the subreddit r/Ask science is all encompassing of the sciences and include topics and therefore keywords found in comments that can be found in subreddit r/longevity and vice versa. Certain keywords such as earth and speed which were in the top 20 most frequent keywords in subreddit r/Askscience will most likely not be found in subreddit r/longevity. However, there were likely crossover key words that can be found in both, such as cells, life, aging, and fasting which the model likely classified as subreddit r/longevity because subreddit r/Askscience encompasses topics and keywords that are found in subreddit r/longevity.

As stated above, due to time constraints, further analysis of removed and deleted posts in the initial phases of collection was limited. However, this does provide further opportunities for research. Further research would include exploring the data collected with the keywords 'health' and 'symptoms' and gathering more posts or comments from a different subreddit that would potentially include an abundance of this keyword.

This model is succuessful in being used to identify where certain discussions can be found in different subreddits to begin the exploration of identifying health related discussions however further data, analysis, and research is needed for its utility for future healthcare applications.


### **Sources**

https://www.reddit.com/r/longevity/
https://www.reddit.com/r/askscience/
https://github.com/pushshift/api
https://www.foreseemed.com/natural-language-processing-in-healthcare