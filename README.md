# Disneyland-reviews-analytics
Analyzing  reviews of 3Disneyland branches using text analytics methods
Executive Summary

The project is designed to conduct a text analysis of Disneyland reviews from Hong Kong theme park, Paris theme park and California theme park. The goal of this project is to improve the performance of Disneyland theme parks to increase revenue and customers’ satisfaction since most guests will not only visit Disneyland only once in their lives. 
From 2016 to 2019, the review scores changed over time for three parks. The project analyzed the reason for the change including the continuous decrease of California theme park’s review score while Hong Kong theme park's increase in the same period. With topic modeling and sentiment analysis, the factors that influenced the customer experience showed up. Since the dataset pointed out the reviewers’ location, the resident and non-resident customers may have different opinions over some features. Based on these points, the project will figure out the most important features for each theme park, the aspects that resident customers and non-resident customers care most about and the key topics that customers expressed in the positive and negative reviews.The project result will be a good indicator for the management of each theme park to improve themselves to offer a better experience to their customers in the future. 

Business Goal Analysis 
According to the financial report released by the Disney group, Disneyland has suffered from revenue shortfalls over the past 3 years while the cost of revenue consecutively remains high. Through the project, the management team is able to improve the features of theme parks. 
Studies have attempted to explore the behavior of tourists at theme parks because of the increasing importance of this aspect in the tourism and hospitality industry (Nuryyev & Achyldurdyyeva, 2015). Existing studies have focused on exploring tourists’ expected experiences (Chen & Lamberti, 2013), participation experience, movement pattern (Tsai & Chung, 2012; Zhang et al., 2017), and behavioral intention (Bigné et al., 2005). Evidently, understanding visitor behavior is important for theme park managers to market their theme parks and design day rundown. The insights generated from this project is supposed to clearly help the management team improve customer satisfaction and proactively manage the customer experience. 

Dataset Description
The dataset is obtained through Kaggle. The link to the dataset is https://www.kaggle.com/arushchillar/disneyland-reviews. The dataset includes 42,000 reviews of 3 Disneyland branches, including Paris, California and Hong Kong. It is posted by visitors on Tripadvisor. This data, collected from February 2016 to December 2019. The 30MB .csv file contains the following attributes:
Review_ID: unique id is given to each review
Rating: ranging from 1 (unsatisfied) to 5 (satisfied)
Year_Month: when the reviewer visited the theme park
Reviewer_Location: country of origin of visitors
Review_Text: comments made by visitors
Disneyland_Branch: location of Disneyland Park





System Design 



5. System implementation 


Trigram
Once the data is cleaned and ready to use, we collected all the negative reviews(ratings <= 3) and split them into three data frames by three different branches which are Hongkong, Paris, and California. For each data frame, negative reviews that contain topics of food, staff, price and weather are filtered, and the top 30 bigram keywords are listed.




Topic Modeling(LDA model) 
We applied Latent Dirichlet Allocation (LDA) model to the reviews in the entire document to have a better understanding of the topics that are discussed in the reviews. The number of topics has an impact on the quality of discovered topics. The algorithm was run multiple times to determine the optimal number of topics for the final model. We selected the number of topics as 20, which is sufficient for our dataset. Based on the keywords that appeared in each topic, we named the topic for ease of interpretation. Table 1 represents 15 popular keywords in some example topics. 

Topic Hotel
hotel
stay
breakfast
resort
buffet
room
child 
memory
service
eat
Topic Food Option 
food
prepare
restaurant
meal 
burger 
quality
choice
drink 
section
serve 
Topic Meeting princess/Mickey Mouse
princess
photo
daughter 
mouse
sit
book
minnie
picture
spot
queue
Topic Castle theme 
queue
hour
firework
night
show
visit
evening
castle
stay
close


Table 1. Popular 15 keywords in four example topics 

After the keywords were classified into 20 topics, we wrote a function to predict the given text documents. The topic with the highest probability is the dominant topic. We assigned the dominant topic to each review in the dataset. An example of the output is shown below. 


6. Evaluation 

Evaluation 
Vader, TextBlob, Word2Vec & Random Forest
For reviews without ratings, it is hard to identify the sentiment of the reviews. Therefore, we applied two prediction models by analyzing reviews sentiments and one machine learning model. By comparing the results of three classification reports, we reached the best algorithm to predict reviews’ ratings for Disneyland 
   




        

Given the results of the three models, we could find that the combination of Word2Vec and Random Forest has the highest accuracy, precision, recall, f-score, which we can conclude that this machine learning model has the best performance. Managers could use this model to predict those missing ratings in their daily works.

Result & Discussion 
Topic Modeling 
Knowing the differences in topic popularity in the negative reviews could help managers run the theme park. The result of topic modeling for three branches, California, Paris, and Hongkong are shown in Figure 1. The topic latent in full-text data of the reviews were grouped into 20 topics, including facilities, hotel, location, food option, cast member, queues, food price, transportation, Meeting princess/Mickey Mouse, weather, non-human characters, trip planning, experience, holiday, peak time, staff, riding, roller coaster experience, assistance, and castle theme. 



The most frequent topics that are discussed in the negative reviews are queues, followed by staff for three branches. Long queues for rides and attractions are a main issue for the theme park. Besides, visitors complain that the staff at the theme park are not very helpful and rude. Visitors have commonly discussed the weather, experience, and food price in the negative reviews of California parks. The common topics are experience, weather, and food price in the Hong Kong branch. The other frequently mentioned topics in the Paris park are food price, experience, and castle theme. The study indicates that there are some similarities of discovered topics among the three theme parks. Since queues for rides and attractions are an essential factor that affects visitors' experience, managers should consider improving visitors' experience by reducing the waiting time of rides and attractions. One way is to recommend alternative rides to prevent popular rides are being overloaded or provide entertainment while visitors are waiting in line.  

We Choose topics such as food, stuff, price and weather to analyze. From the results of trigram method, in topic food, we could find that for negative reviews in all branches, (food, inside, park), (outside, food, allowed), (food, quite, expensive), (food, outlets, closed), (buy, bad, food) are most meaningful combinations with high frequency. Interestingly, in the Hong Kong Branch, the combination of (food, choices, plentiful) appears, however, In other two branches, the combination of (food, choices, plentiful) will be replaced by (food, choices, limited) and (food, options, limited).
In topic staff, we could find that, for negative reviews in Hong Kong Branch, (staff, friendly, helpful) is the most common word combination. On the contrary, for the Paris and California branch, there exists some (staff, rude, unhelpful) combination.
In topic price, we can find that, (pay, full, price) and (full, price, ticket) are the most common word combinations for all three branches.
In topic weather, we can find that (due, bad, weather), (hot, humid, weather), (cancelled, due, weather) and (queuing, hot, weather) are the most common word combinations for all three branches.




















7. Conclusion and Future Direction
After executing our plan and analyzing the data, we found that food is a feature that customers are all dissatisfied with. For the Hong Kong park, people are mad at the policy that outside food is not allowed. Besides this point, the other two theme parks also received negative reviews regarding monotonous food such as simply fast food everywhere. 
As for the staff, the management team of Paris theme park and California theme park should pay attention to the attitude of their staff based on their reviews. 
To develop the customer loyalty, offering discounts to the customers visited before is a good choice since people are complaining that they are paying a full price. 
The facility for people waiting in line should be improved for all the parks. The customers are not satisfied especially under extreme weather conditions such as raining or sustained high temperature. 
In the future, we are looking forward to analyzing more based on specific business domain needs and including more potentially relevant variables. Especially focus on how the marketing team of Disneyland in different locations with various focus can draw specific information from the report to help improve the certain ongoing problems. 
On the other hand, it is important to not only focus on different topics or topic models of Disneyland, but also analyze users' reviews based on time series or time constraint. Compare the sentiment change through time in 3 different Disneyland locations is meaningful to understand the efforts that Disneyland has been working throughout the 10-years period.
Last but not the least, besides deep dive of dimensionality reductions, we are hoping to utilize the neural network with weighted voting and reinforcement learning methodology of balancing unknown fields and known fields to furthermore improve our models’ performance and accuracy in the future.



8. Reference
Nuryyev, G., & Achyldurdyyeva, J. (2015). Visitor behaviour and profitability of Turkmenbashi World of Fairytales in Turkmenistan. Journal of Hospitality and Tourism Technology, 6 (1), 73–88. https://doi.org/10.1108/JHTT-01-2015-0006

Chen, S., & Lamberti, L. (2013). Segmenting Chinese tourists by the expected experience at theme parks. International Journal of Engineering Business Management, 5, 5–22. https://doi.org/10.5772/56605

Tsai, C. Y., & Chung, S. H. (2012). A personalized route recommendation service for theme parks using RFID information and tourist behavior. Decision Support Systems, 52(2), 514–527. https://doi.org/10.1016/j.dss.2011.10.013

Bigné, J. E., Andreu, L., & Gnoth, J. (2005). The theme park experience: An analysis of pleasure, arousal and satisfaction. Tourism Management, 26(6), 833–844. https://
doi.org/10.1016/j.tourman.2004.05.006
