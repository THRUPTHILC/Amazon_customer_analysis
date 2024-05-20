# Amazon_customer_analysis

I have considered the Amazon data of 568454 rows, 10 columns from sqlite database.

**1.Reading data from SQLite DB**
The connection is established to retrieve data from db:
con=sqlite3.connect(r"C:\Users\admin\Desktop\SkillOVilla\Amazon customer\database.sqlite")
Columns:'Id', 'ProductId', 'UserId', 'ProfileName', 'HelpfulnessNumerator'(no of people found it usefull),
       'HelpfulnessDenominator'(total no of reviews), 'Score', 'Time', 'Summary', 'Text'

**2.Data Preparation**
a)Remove irrelevent rows- The rows where 'HelpfulnessNumerator' >'HelpfulnessDenominator'
b)Duplicate rows for unbiased results-"UserId","ProfileName","Time","Text" duplicates are removed.
c)Data type conversion for the columns-Time was in int64, it's converted to dataTime.

**3.Amazon Product recommendation**
Recommends the product for someone who buy more.
Considered the 'No_of_summaries','No_of_texts','avg_score','No_of_products_purchased' to create a list of users for recommending the product to them.

**4.Product which have good number of reviews:**
Identified which product ID is sold with the count. Considering the products which are sold more than 500 times.
Filtered dataframes based on specific index values, using isin() funation

**5.Understanding behaviour of Amazon Users:**
Found behaviour of frequent viewer (Purchased 50 times or more) and non-frequent viewer using lambda(anonymous function).

**6.Are frequesnt users more verbose?**
Identified the customer reviews word by word and collected the length of the reviews for sentimental analysis

**7.Sentimental analysis on data**
Analysing the feelings/intentions-->sentiment analysis. 
The polarity value lies between the range of [-1,1]. 
More close to 0-->neutral.
more close to 1-->positive sentence.
more close to -1-->negetive sentence.
Sample data of 5000 was taken, Using TextBlob the polarity was found.
The list of 10 common words are identified
