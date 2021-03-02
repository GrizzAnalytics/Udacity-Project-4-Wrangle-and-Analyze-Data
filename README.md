# Udacity-Project-4-Wrangle-and-Analyze-Data

I will walk you through my wrangling process for the #WeRateDogs project. My process went as such:

Data Gathering
Data Assessment
Data Cleaning
Data Storage
I. Data Gathering
First, I started gathering data from three separate places and creating comparable data frames for each. The data I will be pulling from includes:

twitter-archive-enhanced.csv
image-predictions.tsv
Twitter's API
These data sets helped me later when I started getting to the assessment portion of this project. So, I spent some time making sure I'm pulling the correct information, and then I made sure I cleaned the data thoroughly afterwards.

II. Data Assessment
Once I gathered the necessary data, I started assessing it for any quality issues and any tidiness issues. As far as I could tell this data was in serious need of a cleanup, so I needed to make sure I accurately assessed each data frame!

Quality Assessment:
Dropping jpg_url and img_num as they are unneeded now
Not all of the names in name column are actually names
There are some denominators in the rating_denominators column that don't follow the "out of 10" rule, I must fix those
I will fix the numerators that are also greater than 15 and less than 10, as this does not follow the same parameters as #WeRateDogs's rating system
Delete columns that are unnecessary: in_reply_to_status_id, in_reply_to_user_id, retweeted_status_id, retweeted_user_status_id, and retweeted_status_timestamp
Tweet Id should be a string, not an int64
Nameless dogs should be NaN and not none
Remove the underscore and properly capitalize dog breeds in p1, p2, and p3
Tidiness Assessment:
p1, p2, and p3 should be merged into one categorical variable column
Must merge this dataset with tea
III. Data Cleaning
First, I needed to make copies of each dataset. This way I could properly clean the data without altering the actual data set. Once I did that, I decided to do a tidiness clean first, as it seemed to be the least harrowing portion of the process.

Tidiness Cleaning:
Used the .merge() function for tea_clean and clean_p_images
Used the .merge() function for wrd_clean and api_clean
Used the picture prediction to fill in newly defined function dog_breed. a. Used .drop() function for p1, p2, p3, p1_dogs, p1_conf, p2_dogs, p2_conf, p3_dogs, p3_conf
Once I was done tidying up the data set, I started cleaning the quality of the data.

Quality Cleaning:
Used Series.str.replace to remove the underscore from dog breeds, and then use Series.str.capitalize to make sure everything is properly capitalized
Used the .astype() and .apply() functions to change tweet_id from an int64 to a str.
Defined a new function that renames 'None' to 'NaN' called no_names
Defined a new function to help search for missing names from a text column called name_search

Used .drop() function for rows with missing names
Use inull function on retweeted_status_id, retweeted_status_user_id, and retweeted_status_timestamp

Used drop function on in_reply_to_status_id, in_reply_to_user_id, retweeted_status_id, retweeted_status_user_id, and retweeted_status_timestamp
Used .drop() for rows where the denominator is != 10.

Used .drop() function on in_reply_to_status_id, in_reply_to_user_id, retweeted_status_id, retweeted_status_user_id, and retweeted_status_timestamp
Used .drop() for rows that have numerators higher than 15 and lower than 10
Used .drop() for rating_denominators column
IV. Data Storage
Even though I named the new cleaned data set wrd_clean, I stored the data as twitter_archive_master.csv using th
