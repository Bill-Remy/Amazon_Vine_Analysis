# Amazon_Vine_Analysis

## Overview Of Analysis

### Purpose and Scope
The purpose of this analysis is to determine if compensated reviewers as part of the Amazaon Vine program provide biased reviews for products.  The scope was limited to one data set of Amazon reviews from large list of available datasets.  For this particular review the following dataset was used:

https://s3.amazonaws.com/amazon-reviews-pds/tsv/amazon_reviews_us_Sports_v1_00.tsv.gz

### Analytical Methods

The analysis consisted of a four step process:
- Isoloate all reviews with more than 20 votes to filter out less relevant reviews
- Capture ratings where helpful votes were more than half the total votes to further reduce the dataset
- Divide the votes into Vine(Paid) and non-Vine(unpaid) reviews
- Calculate the percentage of five star reviews for Vine and non-Vine to exmaine for bias

#### Step 1 Isoloate Vine reviews with more than 20 Votes

The data was read fromt the Amazon tab delimited file into a dataframe - vine_df and also filtering the data for more than 20 total votes.  A sample of the resulting data frame is shown below.

<img src="Vine_reviews.png">

#### Step 2 Capture Ratio of Helpful Votes to Total Votes greather than 50%

In order to accomplish Step 2 of the analysis a field called Helpful_Vote_Ratio was calcualated as helpful_votes / total_votes and was then filtered for all rows greater than 50%.  This dataframe(helpful_df) is shown below.

<img src="helpful_reviews.png">

#### Step 3 Seperate Pain vs. UnPaid Reviews

To seperate Vine-Paid reviews from non-Vine unpaid reviews the "vine" column of the dataframe was filtered by "Y" or "N" into seperate dataframes.  Paid reviews, vine="Y", were seperated into the paid_df data frame.  Unpaind reviews, vine="N", were seperated into the unpaid_df dataframe.  Examples of both are shown below.

**Paid Reviews**

<img src="paid_reviews.png">

**Unpaid Reviews**

<img src="unpaid_reviews.png">

#### Step 4 Calculate Statistics for 5 Star Reviews

| Type of Review | Total Reviews | 5 Star Reviews | % 5 Stars |
|----------------|---------------|----------------|-----------|
| Paid -Vine     | 311           | 129            | 41.5 %    |
| Unpaid         | 57,509        | 30,631         | 53.3%     |
| Total          | 57,820        | 30,760         | 53.2%     |

### Resulys and Summary of Analysis

There are a couple of clear observations from the dataset analyzed.  First, for this category of products the paid Vine reviews were a very small portion of the total reviews.  Second, the 5-Star reviews provied by the compensated reviewers were materially lower than the unpaid reviewers.  In fact the percentage of Vine 5-Star reviews were 22% less than the unpaid reviewers.  It's clear that in this particular category of products the compensated reviewers did not show a bias of over rating items.  

Another observation is that given the low number of compensated reviewers it would not materially change the percentage of 5-Star reviews even if all of the Vine reviewers gave a 5-Star Review.  If 100% of Vine reviews were 5-Stars, the total 5-Start review percent would only change to 53.5%.
