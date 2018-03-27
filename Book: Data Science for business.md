# CHAPTER 2 Business Problems and Data Science Solutions

### The Data Mining Process:

    1. Business Understanding 
    2. Data Understanding 
    3. Data Preparation 
    4. Modeling
    5. Evaluation
    6. Deployment




### P44. A critical skill in data science is the ability to decompose a data analytics problem into pieces such that each piece matches a known task for which tools are available.

    1. Classification and class probability estimation attempt to predict, for each individual in a population, which of a (small) set of classes this individual belongs to.
    
        An example classification question would be: “Among all the customers of MegaTelCo, which are likely to respond to a given offer?” In this example the two classes could be called will respond and will not respond .
    
    2. Regression (“value estimation”) attempts to estimate or predict, for each individual, the numerical value of some variable for that individual.
    
        An example regression question would be: “How much will a given customer use the service?”
    
    3. Similarity matching attempts to identify similar individuals based on data known about them.
    
        Similarity matching is the basis for one of the most popular methods for making product recommendations (finding people who are similar to you in terms of the products they have liked or have purchased).
    
    4. Clustering attempts to group individuals in a population together by their similarity,but not driven by any specific purpose.
    
        An example clustering question would be: “Do our customers form natural groups or segments?” Clustering is useful in preliminary domain exploration to see which natural groups exist because these groups in turn may suggest other data mining tasks or approaches.
    
    5. Co-occurrence grouping (also known as frequent itemset mining, association rule discovery, and market-basket analysis) attempts to find associations between entities based on transactions involving them.
    
        For example, analyzing purchase records from a supermarket may uncover that ground meat is purchased together with hot sauce much more frequently than we might expect.
    
    6. Profiling (also known as behavior description) attempts to characterize the typical behavior of an individual, group, or population.
    
        For example, if we know what kind of purchases a person typically makes on a credit card, we can determine whether a new charge on the card fits that profile or not. We can use the degree of mismatch as a suspicion score and issue an alarm if it is too high.
    
    7. Link prediction attempts to predict connections between data items, usually by suggesting that a link should exist, and possibly also estimating the strength of the link.
    
        Link prediction is common in social networking systems: “Since you and Karen share 10 friends, maybe you’d like to be Karen’s friend?”
    
    8. 8. Data reduction attempts to take a large set of data and replace it with a smaller set of data that contains much of the important information in the larger set.
    
    9. Causal modeling attempts to help us understand what events or actions actually influence others.
    
    
## Churn prediction

For business applications we often want a numerical prediction over a categorical target. In the churn example, a basic yes/no prediction of whether a customer is likely to continue to subscribe to the service may not be sufficient; we want to model the probability that the customer will continue. This is still considered classification modeling rather than regression because the underlying target is categorical. Where necessary for clarity, this is called “class probability estimation.”

## Data Mining and Its Results

There is another important distinction pertaining to mining data: the difference between (1) mining the data to find patterns and build models, and (2) using the results of data mining.

# CHAPTER 3 Introduction to Predictive Modeling: From Correlation to Supervised Segmentation  







# CHAPTER 4 Fitting a Model to Data




# CHAPTER 5 Overfitting and Its Avoidance



# CHAPTER 6 Similarity, Neighbors, and Clusters



# CHAPTER 7 Decision Analytic Thinking I: What Is a Good Model




# CHAPTER 8 
