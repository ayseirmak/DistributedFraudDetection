# Distributed Fraud Detection Using Apache Spark and GNN
## Goal of The Project
we propose to use a distributed storage and computation system in order to track money transfers instantly. In particular, we keep our transaction history in a distributed file system as a graph data structure. 
We try to detect illegal activities by using Graph Neural Networks(GNN) in distributed manner. 
We simulate incoming transactions as a mini batch of inference data. Finally, we compare our proposed parallel system with a linear system and show the temporal efficiency of our method.
## Scope of The Project
1. Preparation of the working environment and resources, 
2. Creation of the GCN model,
3. Observe the execution time of training and inference phase of Model.
4. Observe the effects of resources assigned per node and , number of workers per node to distributed training and bare-training
## Used Technologies
BigDL is a distributed deep learning framework for Apache Spark. In this work, we prefer to use ORCA library which is used for scaling out single node Python notebook across large clusters (to process distributed Big Data). 
The ORCA Context object encapsulates the Spark Context and Ray Context Objects. Hence,both the methods from Spark framework and Ray framework can be used in the Driver program. With the Spark Context object, we can execute our training and inference phases on worker nodes (Spark Standalone-Mode) or threads(Spark LocalMode) in distributed manner. In Training and Inference phases, we can call Ray-Distributed-Methods over Ray-Context object. 
### BigDL – ORCA Library for Distributed Training and Inference 
<img width="355" alt="image" src="https://github.com/ayseirmak/DistributedFraudDetection/assets/152956281/cd369e32-d587-46e6-a9f9-f7363e7b3e8b">

Orca-estimator object encapsulates the necessary methods for training and inference of models created on different frameworks such as Tensorflow, Pytorch,
Spark.In this way, framework independent, orca-estimator.fit() and orca-estimator.predict()
methods can be used.
<img width="443" alt="image" src="https://github.com/ayseirmak/DistributedFraudDetection/assets/152956281/7131158b-f832-4152-b888-e43c7c89877b">

### Graph Convolutional Networks
The model contains a prepossessing layer, which is simple a dense layer. 
This layer is followed by two consecutive graph convolutional layers with 32 hidden units.
Output of convolutional layers are fed to another dense layer, which producesthe output of the model.
**Implementation:**
we install **Tensorflow 2.9.2** for creating GCN Model which is both compatible with **Spark 3.3.1** and **ORCA-3 frameworks**

### Spark Cluster Local Standalone Mode
Spark Cluster Modes (Local-Mode / Standalone-Mode) is used to share the resources in the working environment in distributed methods. 
To observe the relationship between the number of worker threads the amount of Core, We share the 16 GB-12 Core RAM to the worker threads via Spark Cluster in LocalMode. Moreover, the execution time of training and inference process has been analyzed by running these pheses on Standalone-Mode, 8 GB-4 Core two Debian VM instances.
**Implementation:**
we install **PySpark 3.3.1** and **ORCA-3** frameworks to Local Machine for Local Cluster Mode and Worker Nodes to Stamdalone Cluster Mode
## Dataset
Elliptic Data Set
A graph consisting of bitcoin transactions occured in two weeks.
  203,769 nodes with 168 features
  234,355 edges
49 connected component
  Each of which a DAG
  Each for a time step
  
<img width="354" alt="image" src="https://github.com/ayseirmak/DistributedFraudDetection/assets/152956281/0d8d333b-4e62-4d0f-96d4-50a50d19d3df">
<img width="526" alt="image" src="https://github.com/ayseirmak/DistributedFraudDetection/assets/152956281/09a48200-ebed-4730-b8b7-ad91f0aa6b15">

## Experiments & Results
<img width="800" alt="image" src="https://github.com/ayseirmak/DistributedFraudDetection/assets/152956281/3f9a3353-00e7-4928-a225-e97b3a390ed4">
<img width="800" alt="image" src="https://github.com/ayseirmak/DistributedFraudDetection/assets/152956281/a044d846-6146-45d1-a01e-ffe64c40d7c6">
<img width="800" alt="image" src="https://github.com/ayseirmak/DistributedFraudDetection/assets/152956281/7cc36c32-9550-45e8-805e-df57394d1f5e">









