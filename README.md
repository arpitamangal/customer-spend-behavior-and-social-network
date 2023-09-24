# Predictive Analytics with MLlib
Predicted customer transactions using recency, frequency, spend behaviour and Social Network metrics over lifetime using MLlib.

Dependent Variable: transactions user had committed during her/his twelve months in Venmo? (Y variable for the predictive analytics

Independent Variables: 
1. Recency: Last time a user was active, 
2. Frequency: how often a user uses Venmo in a month.

- The predictive accuracy of recency and frequency in determining the total number of transactions improves and stabilizes over time, but there may be other influential factors during the early stages that contribute to the variability in the predictions.

3. Customer Spending Behavior: how the percentage of textual description v/s emojis affects transactions in customer lifetime.  
  3.1 Static Profile: % of transactions in 9 different categories  
  3.2 Dynamic Profile: User’s spending profile is evolving over lifetime in Venmo (EOM)  
  3.3 Emoji Only Transactions: If transactions only described using an emoji  

- When spending behaviour profile is included, MSE first drops, then increases and decreases drastically and then increases again. Finally, MSE is mostly same as what it was at the begining of the lifetime. 

4. Social Network Analysis: how does the social network (connectivity) of user affects transactions in customer lifetime    
  4.1 Local Clustering Coefficient (Triplets) Static: how well its neighbors are connected to each other  
  4.2 Local Clustering Coefficient (Triplets) Dynamic: how does connectivity change over lifetime  
  4.2 Page Rank: importance score of user within a network  

- When the social metrics variable is added, the overall trend goes downward but with intermittent increases and decreases.

When all the above variables are included, the MSE drops between lifetime 6-8 and then increases drastically.

## Customer Spending Behavior Profile

Explore how a user’s spending profile is evolving over lifetime in Venmo (EOM)

Data manipulation:

* Separate emoji and text from transaction description
* Tokenise text
* Emojis classified into 7 categories: Event	Travel	Food	Activity	Transportation	People	Utility
* Text classified into 9 categories: People	Food	Event	Activity	Travel	Transportation	Utility	Cash	Illegal/Sarcasm
* Flag for emoji only transactions
* Customer Spend Behaviour Profile (Static, Dynamic): If a user has made 10 transactions, where 5 of them are food and the other 5 are activity, then the user’s spending profile will be 50% food and 50% activity.

Insights: 

- 30% of transaction descriptions do not contain text and only have emoji.
- The most popular emoji's being Pizza, Beer with 2 glasses, Celebration, Wine and Beer.
- The top transaction categories being Food, people, activity.
- User’s spending profile stabilize after the first life point  

## Social Network Analysis

Explore how does the connectivity (social netowrk) of a customer evolve on Venmo (Friends and Friends of Friends)

Clustering Coefficeint: Measure of the degree to which nodes in a graph tend to cluster together.

* Local clustering coefficient: Measures the clustering of a specific node in a graph, indicating how well its neighbors are connected to each other.

LCC(i) = (2 * e_i) / (k_i * (k_i - 1))

where:

e_i: Number of edges between the neighbors of node 'i'  
k_i: Number of neighbors of node 'i' (Degree)  

* Global clustering coefficient: Measures the overall clustering tendency of the entire graph. It provides insight into how interconnected the entire network is.

GCC = (1 / N) * Σ LCC(i) 

where:

N: Total number of nodes in the graph  

* Page Rank of User: Scores the importance of nodes (web pages) within a network. The importance score will always be non -ve real number and all the scores will add to 1. Sometimes expressed as %. 

