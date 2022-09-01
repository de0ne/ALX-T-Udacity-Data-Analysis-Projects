# Data Wrangling project - @WeRateDogs Twitter Archive

Real world data  rarely come clean. As a student of Udacity Data Analyst Nanodegree program, one of the requirement to graduate is the completion of a data wrangling project.

The aim of this project is to gather data from a variety of sources and in a variety of formats, assess its quality and tidiness, then clean it using python and its libraries. Also performed some analyses and visualization.

The dataset worked on is the tweet archive of Twitter user <font color='blue'>@dog_rates</font>, also known as <font color='blue'>WeRateDogs</font>. WeRateDogs is a Twitter account that rates people's dogs with a humorous comment about the dog. 

The main steps carried out in this project are:
1. Gathering data
2. Accessing data
3. Cleaning data
4. Analysis & Visualization

### 1. Gathering data

In this section, three datasets were gathered namely:
    
1. twitter_archive_enhanced.csv which was downloaded through the link provided by Udacity and imported using the pandas library.
2. image_predictions.tsv which was downloaded programmatically using the requests module. 
3. tweet_json.txt: gotten from twitter by querying the twitter API through the Tweepy library.

### 2. Accessing data

The three pieces of data gathered were accessed both visually and programmatically for quality and tidiness issues. The following issues were discovered.

#### Quality issues

##### The twitter_data table

* It contains null values
* columns not needed were present
* timestamp data type was object instead of datetime
* timestamp column was not properly named
* tweets that do not contain images(e.g retweets) were present

##### The image_predictions table

* columns not needed were present
* p1, p2, and p3 columns were not properly named

##### tweet_archive_master table

* columns not needed were present


#### Tidiness issues
* The twitter_data table contains four columns for the dog breeds
* A single dataframe sould have been created for the three tables
* A single observational unit is stored in multiple columns(text column in twitter_data table and tweet column in tweet_data table.

### 3. Cleaning data
The quality and tidiness isues discovered in the previous section were cleaned. The three steps involved in this cleaning are: Define, Code and Test.

The following quality issues were fixed in the twitter_data table: 

1. in_reply_to_status_id, in_reply_to_user_id and source columns were dropped.

2. the timestamp column was renamed to time_created.

3. the time_created column was change from object type to datetime type.

4. new column named 'dog_stage' was created

5. the doggo, floofer, pupper and puppo columns were dropped.

6. retweeted rows from retweeted_status_id', retweeted_status_user_id and retweeted_status_timestamp columns were removed

7. retweeted_status_id, retweeted_status_user_id and retweeted_status_timestamp columns were dropped


The following quality issues were fixed in the image_predictions table:

1. 'img_num', 'p1_conf', 'p2_conf' and 'p3_conf'columns were dropped.

2. 'p1', 'p2' and , 'p3' columns were renamed to 'prediction_1', 'prediction_2' and 'prediction_3' respectively.


The following tidiness issues were fixed in the twitter_archive_master table:

1. the three dataframes were merged into one single dataframe named 'twitter_archive_master'

2. the 'text' column was dropped as it contains the same information with the tweet column.

3. the columns were rearranged.

### 4. Analysis & Visualization

The insights from this project are:
1. The most common dog stages are pupper, doggo and puppo
3. The top three dogs with most average retweets are Stephan, Duddles and Jamesy
4. The top three dogs with most average likes are Stephan, Jamesy and Duddles
5. There is a linear relationship between no of retweets and no of likes.

##### Insight 1: The most common dog stages are pupper, doggo and puppo

![image1](https://user-images.githubusercontent.com/78403762/187943697-f513d8a0-cf9b-4fa2-b54d-386984a72ca1.png)
* As we can see from the above image, the most dog breeds are pupper, doggo and puppo. Others are doggo, pupper; doggo, floofer and doggo, puppo.

* The occurrence of pupper dog breed is very high compared to other dog breeds.

#### Insight 2: The top three dogs with most average retweets are Stephan, Duddles and Jamesy
#### Insight 3: The top three dogs with most average likes are Stephan, Jamesy and Duddles

![image3](https://user-images.githubusercontent.com/78403762/187943903-baca8681-3417-4dff-98dc-e631b4bc10ca.png)
* The chart above shows the dogs with the most average retweets and average likes '
* Stephen, Duddles and Jamesy are the top three in the average retweets chart.
* Stephen, Jamesy and Duddles are also the top three in the average likes chart.

#### Insight 4: There is a linear relationship between no of retweets and no of likes.

![image4](https://user-images.githubusercontent.com/78403762/187944137-92e0ebb3-477f-4ff9-8bde-e882403b164c.png)

* The chart above shows there is a linear relationship between the no of retweets in a post and the no of likes on the same post. This means that the more the retweets, the more the likes.

* This supports our findings in the average retweets and likes charts as the dog with the most retweets are also the ones with the most likes.
