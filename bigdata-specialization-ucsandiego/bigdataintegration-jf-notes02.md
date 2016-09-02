# Big Data Integration & Processing

## Processing Big Data 


###### 1. Big Data Pipelines and High-Level Operations for Big Data Processing

- **Dataflow Approach**
    - **Big Data Pipeline** - Get created to process data through an aggregated set of steps that an be represented with the split, do, merge pattern with data parallel scalability.
        - Stitching together sets of steps together. (Think ``` ls | wc``` in UNIX). Outfit of one running program gets piped into the next program as input. (Functional Programing)
        - The parallelism of each step in the pipeline is mainly data parallelism. 
        - Running the same functions simultaneously for the elements or partitions of a dataset on multiple cores. (e.g Wordcount)

- **Common Data transformations** (Higher order functions to convert one form to another) 
    - ``` map -> ``` Apply the same operation to each member of a collection.
    - ``` reduce -> ``` 'Collecting' things that have the same 'key'.
    - ``` cross/cartesian -> ``` Multiplication. Do some process to each pair from two sets.
    - ``` match/join -> ``` Selective multiplication. Do some process to each pair from two sets, which have the same 'key'.
    - ``` co-group -> ``` Group common items. Collect similar items first, apply a process to each collection.
    - ``` filter -> ``` Select elements that match a criteria (e.g Filter even numbers, x % 2 == 0)
    

- **Aggregations in Big-Data Pipelines** - An operation on a dataset that performs a specific transformation taking all the related data elements into consideration. By choosing the right **aggregation**, you can generate **compact** and **meaningful** insights.
  - ``` sum  ``` - Summation over all the data elements.
  - ``` group-by ``` - Summations for individual data groups. ```(e.g - {color,total}--> (red,5), (yellow,9) ..```
  - ``` average ``` - Average over items of similar types. 
  - ``` max, min, standard deviation ```
  - Connecting Aggregations - ``` max(sum), min(sum), etc.. ```
  - Boolean aggregation - ``` and, or ```
  - Sets - ``` union, intersection, difference ``` 
  - Strings - ``` concatenation ```
  
- **Analytical Operations (ML) in Big Data Pipelines** (Patterns -> Insights -> Decisions) - To analyze the data to discover meaningful trends and patterns in order to gain insights into the problem being studied. 
  - **Classification** - Predict a categorical (discrete values or categories) target from the input data. (e.g binary classification)
    - E.g; Decision Tree Algorithm - Decisions are modeled as a tree structure. 
  - **Clustering** - The goal is to organize similar items into groups of associations. 
    - E.g; K-Means Clustering - Samples are divided into k clusters
  - **Path Analysis** (Graph analytics) - Find routes from one location to another. (e.g shortest path from home to work)
  - **Connectivity Analysis** (Graph analytics) - Finding and tracking groups (communities) to determine interactions between entities. (e.g linkedin network)
  - Etc...

-----


###### 2. Big Data Processing Tools and Systems

- **Overview**

- **The Integration and Processing Layer**


> [notebooks/spark-example-wc.ipynb - Spark wordcount example using pyspark](notebooks/spark-example-wc.ipynb)










