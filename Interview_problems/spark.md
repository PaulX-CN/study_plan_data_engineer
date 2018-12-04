### RDD

- RDD?
  
  RDD’s are collection of data items that are split into partitions and can be stored in-memory on workers nodes of the spark cluster.


- RDD elements?
  - Partitions
   - Function for computing them
   - Dependency dags
   - Preferred compute location (HDFS block etc.)
   - Partitioner (Hash partitioner etc.)

- Shuffle?

  Data redistributed between nodes by keys

- Narrow/Wide transformation?

  Narrow: data pipelining on same node
  Wide: data shuffling (groupby, join etc.)
  
- repartition/coalesce ?
  
  Repartition: any given new partitions (maybe shuffling)
  Coalesce: smaller amount (no shuffling)
  
- Skew Join Optimization? How to identify?

  Code To determine:
  
  ```skewed_large_rdd.mapPartitions(lambda x: len(x)).collect```
  
  Check the time taken per task (median/max). If few tasks are stuck with much longer time than the others and it's doing a join operation, it's skewed.
  
  Solution: modify the key to add some randomness by doing (original_key, random_int) where random_int takes a value between 0 and N
  
  Code: 
  
  ```skewed_large_rdd.map(lambda x: ((x[0], randint(0, N-1)), x[1])).partitionBy(num_parts)```

- DAG in gray?

  Calculation was cached and thus skipped.

- Accumulator/Broadcast variable

  Accumulator: whenever a task is run the function was run on the task to update the value in driver (can mismatch due to task failure)
  
  Broadcast variable: distributed to all executors ```sc.broadcast(lookupMap)```

- RDD/Dataframe?

  RDD low level API, no schema so less optimization
  
- SparkSQL

  Session scoped, no accessible from other session. Droped once session ends.
  
  