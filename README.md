# Overview

This project aims to determine the presence of bias in Amazon product reviews as a result of the Vine program. As per [Amazon's website](https://www.amazon.com/vine/about), "Amazon Vine invites the msot trusted reviewers on Amazon to post opinions about products to help their fellow customers make informed purchase decisions. Amazon invites customers to become Vine Voices based on the insightful reviews they published on their past purchases and helpfulness of their reviews. Amazon offers Vine members free products that have been submitted to the program by participating selling partners. Vine reviews are the independent opinions of the Vine Voices and the selling partners cannot influence, modify or edit the reviews."

Given the availability of review data from Amazon Web Service's (AWS) Simple Storage Service (S3), our project aims to leverage AWS's Remote Database Services (RDS) and Google's Colaboratory with PySpark to Extract, Transform, and Load the review data into a Postgres database. We were successfully able to do so, making the dataset temporarily accessible remotely to any others who needed the data. 

With the database secured, the next task was to address our original question: can we observe any bias in ratings due to the Vine program? The 'grocery' database stood out as an interesting place to start. We began by looking only at product reviews with more than 20 votes, and then those qualified as helpful more than 50% of the time. This gave us a dataset of product reviews had been engaged with to begin answering our questions.

# Results

- Vine reviews represented a vast minority of reviews in the grocery reviews set. 
    - Out of 28,235 reviews, only 61 of them were paid through the Vine program. 
    - This limits the accuracy of our analysis dramatically, as we have a very small number of paid reviews to analyze. 

- Vine reviewers submitted 20 5-star reviews, compared to a total of 15,672 5-star reviews submitted by non-Vine reviewers

- Vine reviewers submitted a lower percentage of 5-star reviews than the general public
    - ![Paid Reviews](https://github.com/ipbrieske/Amazon_Vine_Analysis/blob/main/Images/paid_results.png)
    - ![Unpaid Reviews](https://github.com/ipbrieske/Amazon_Vine_Analysis/blob/main/Images/unpaid_results.png)
    - While the general public submitted 55.6% of all reviews as 5-star, Vine reviewers only submitted 32.8% of their reviews as 5-star. 

# Summary

From our results, it would appear that Vine Voices are slightly biased toward lower ratings, at least when it comes to groceries. This would track with Amazon's stated purpose of the program: to encourage reliable reviews of products. As Amazon serves as the host for a variety of vendors, it is in their best interest to provide customers with the most accurate product data, to encourage the sales of high-quality products, and conversely discourage the sale of low-quality products. This analysis is limited by the very low pool of Vine reviews to draw from, as a larger sample size would give us a more accurate view of how Vine reviewers compare to the general public. It was surprising to see such a high percentage of 5-star reviews amongst general customers, as we expected users to voice their discontent with products more often than their satisfaction. 

In order to get a better sense of this distribution, we did attempt to plot a histogram and KDE of the star reviews, to get a sense of the differnce in distribution of the datasets. Unfortunately, this plotting is not yet supported by PySpark, but would be possible in a Pandas dataframe. In addition, T-testing of each of these distributions would give us an exceptionally precise value of their differences. 
