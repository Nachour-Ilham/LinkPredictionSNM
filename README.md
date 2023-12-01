<p style="font-size:62;text-align:center"> <h1><b>Graph Link Prediction</b></h1></p>

<h2> Problem statement: </h2>
Given a directed social graph, have to predict missing links to recommend users (Link Prediction in graph)

<h2> Data Overview</h2>

Taken data from facebook's recruting challenge on [kaggle](https://www.kaggle.com/c/FacebookRecruiting)

Data contains two columns source and destination eac edge in graph 

   | Data columns | Type | 
   |---|---|
   | source_node | int64 |
   | destination_node | int64 |
    
<h2> Mapping the problem into supervised learning problem:</h2>

- Generated training samples of good and bad links from given directed graph and for each link got some features like no of followers, is he followed back, page rank, katz score, adar index, some svd fetures of adj matrix, some weight features etc. and trained ml model based on these features to predict link. 

- Some reference papers and videos :  
    - https://www.cs.cornell.edu/home/kleinber/link-pred.pdf
    - https://www3.nd.edu/~dial/publications/lichtenwalter2010new.pdf
    - https://www.youtube.com/watch?v=2M77Hgy17cg

<h2> Performance metric for supervised learning:</h2>

- Both precision and recall are important so F1 score is good choice
- Confusion matrix


<h2> TODO: </h2>

   ### 1. **Reading and Analyzing the Graph:**
   - Read the CSV file (`'data/train.csv'`) containing information about a social network graph.
   - Use `NetworkX` to create a directed graph (`nx.DiGraph()`) from the edge list.
   - display basic statistics about the graph, such as the number of nodes, edges, and average degree.

   ### 2. **Displaying a Subgraph:**
   - Create a subgraph from a sample of the original graph (`'train_woheader_sample.csv'`).
   - Visualize the subgraph using `NetworkX` and `Matplotlib`.

   ### 3. **Exploratory Data Analysis (EDA):**
   - Analyze the distribution of the number of followers for each person (in-degree) and the number of people each person is following (out-degree).
   - Visualizations include plots, histograms, and boxplots.
   - Identify percentiles and provide insights into the distribution of followers and followings.

   ### 4. **Posing a Problem as a Classification Problem:**
   - Transform the link prediction task into a binary classification problem.
   - Generate negative examples (`missing edges`) by randomly selecting pairs of nodes without an edge. The condition ensures that the shortest path length between the nodes is greater than `2`.

   ### 5. **Train-Test Split:**
   - Separate positive links (`existing edges`) and negative links (`missing edges`) into training and test datasets.
   - The training dataset contains positive links and an equal number of randomly chosen negative links.
   - The test dataset contains positive and negative links that were not used during training.

   ### 6. **Cold Start Problem Analysis:**
   - Analyze the cold start problem by examining common nodes between the training and test graphs.
   - Calculate the number of people common in both graphs and the number of people present in one graph but not the other.

   ### 7. **Final Train and Test Data Sets:**
   - Combine the positive and negative links to create final training and test datasets.
   - Save these datasets, along with corresponding target variables, as CSV files (`train_after_eda.csv`, `test_after_eda.csv`, `train_y.csv`, `test_y.csv`).

   ### 8.  **Further Steps:**
   - Additional steps such as feature generation and model training will be performed in subsequent notebooks.