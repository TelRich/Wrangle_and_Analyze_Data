# Wrangle and Analyze Data

The aim of the project was to wrangle the WeRateDog twitter's data and visualize it at the end. The wrangling steps taken to achieve this were, gathering the data, assessing the data and cleaning the data.

## Gathering the data
Three datasets were used for the project, each at different locations having different formats from each other. The first data is contained in the `twitter-archive-enhanced.csv` file. The CSV file was provided by Udacity to be downloaded manually to the local device.

The second data was contained in the `image-predictions.tsv` file. This TSV file was downloaded programmatically using [Request library](https://pypi.org/project/requests/) from the URL https://d17h27t6h515a5.cloudfront.net/topher/2017/August/599fd2ad_image-predictions/image-predictions.tsv. It contains the image predictions of each tweet according to a neural network.

The third data was retrieved from twitter using Twitter's API. Python's (Tweepy library) was used to query the Twitter API for each tweet's JSON data. Contained in this JSON data were each tweet's retweet count and favorite("like") count needed for the project. I also retrieved the timestamped for cleaning purposes. The entire set of JSON data for each tweet was stored in a file called `tweet_json.txt file`.

## Assessing the data
Assessing the data is the second step of data wrangling. In the project this was done in two ways, visual assessment where the data was displayed in the Jupyter Notebook for visual assessment purpose and programmatic assessment where pandas' functions and/or methods [info(), describe(), sample()] were used. The three dataset were assessed individually and this was done to find quality and tidiness issues.
### Quality issues found in the datasets
`twitter-archive-data.csv`

* `archv_data` table has retweet rows
* unusual name in name column such as "a", "the" and "an"
* empty rows of name, and _dogstage are filled with None instead of NaN
* rating_numerator extracted wrongly and it should be float data type.
* some rating_denominator are above 10.
* erroneous data types (tweet_id and timestamp)
* empty dog names in archv_data

`image-predictions.tsv`

* some predictions are not dog breed
* tweet id is integer data type
* The prediction names contain lowercase, uppercase and underscore.

`twtr_data`

* erroneous data types (tweet_id and timestamp)

### Tidiness issues found in the dataset
* one variable in four columns in archv_data table (doggo,floofer,pupper and puppo)
* retweet count and favorite count should be part of archv_data table
* image prediction should be part of archv_data

The above was found when assessing the datasets, both visually and programatically.

## Cleaning the data
Here, all the listed issues above were cleaned. The data used for cleaning is a copy of the original data. The framework,define-code-test was used to clearly document the process.

Missing values should be handled first, but since there was none in the case of our project, tidiness issues were handled first. During this process, the three datas was merged together and was used for cleaning quality issues.

The end result was a high-quality and tidy master pandas DataFrame which was saved to the `twitter_archive_master.csv` file.

**The Act Report contains a brief insights on the cleaned data which are:**
* **What is associated with maximum retweet_count**
* **What is associated with maximum favorite_count**
* **What is associated with the maximum rating**
* **What is the highest confidence score of algorithm 1**