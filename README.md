# DHN-simulation
Build for semester project - District heating network simulation.

## Table of Contents
- [Introduction](#introduction)
- [Analysis](#analysis)
- [Technique](#technique)
- [Experiment Results](#experiment-results)
- [Discussion](#discussion)
- [Running the Code](#running-the-code)
- [Citation](#citation)

## Introduction
District heating involves the distribution of heat from a centralized source like a power plant or waste incinerator to various buildings for heating and hot water needs [1]. This system is particularly energy-efficient, cost-effective, and eco-friendly for urban regions in colder climates [2]. Accurate forecasting of district heat load, which is the required heat supply at a specific time [3], is crucial for the efficient operation and planning of these systems. However, forecasting is complex due to the heat demand's non-linear and non-stationary characteristics.

Forecasting district heat load is a complex task that involves predicting future heat demand by analyzing historical data and various influencing factors like weather conditions and building characteristics [3], [7]. The challenge lies in the non-linear and non-stationary nature of heat demand, compounded by numerous influencing factors, which complicates accurate forecasting [6]. In response, researchers are increasingly turning to advanced machine learning (ML) methods, especially deep learning, due to their capacity for discerning intricate patterns and dependencies within data [8], [9]. Within this realm, active deep learning emerges as a particularly effective technique. It enables the model to selectively target the most informative data points within a vast and unlabeled dataset, thereby enhancing forecast accuracy and reducing the effort and expense of data collection [10]. This method is especially suitable for district heat load forecasting, given the often highly variable and intricate nature of the data involved [8].

## Analysis
### Basic knowledge of District Heating Network
**Components:**
- Station (HS): This facility supplies hot water to the network, distributing it through pipes to substations.
- Substations: These are the terminal points of the network, where the heat demand is actualized.
- Pipes: These form the connecting infrastructure of the network.

**Physical parameters:**
1. Temperature (C)
2. Pressure (bar)
3. Mass flow ($m^3/s$)

**Physical relationship and formula:**
Darcy–Weisbach equation
$$
\frac{\Delta p}{L} = f_D \cdot \frac{\rho}{2} \cdot \frac{\langle v \rangle^2}{D_H},
$$
In fluid dynamics, the Darcy–Weisbach equation is an empirical equation that relates the head loss, or pressure loss, due to friction along a given length of pipe to the average velocity of the fluid flow for an incompressible fluid. [] Therefore, the relations between pressure loss and mass flow are found.
  
**Node Representation Approach:**
In this study, a node representation framework is adopted. This means all network components, including the Heating Station, substations, and pipes, are conceptualized as nodes rather than edges. Each node is characterized by three primary attributes: temperature, pressure, and mass flow. This node-centric approach facilitates the implementation of graph neural networks. Additionally, given that the structural configuration of the District Heating Network remains constant, this representation ensures a stable graph structure. It allows for model training focused on varying node attributes while maintaining an unchanged graph structure.

**Known and Predictive Attributes:**
- At the Heating Station: The temperature attribute is known.
- At the Substations: The pressure attribute is known.
- Other Attributes: The remaining attributes, including those at various nodes and interconnecting pipes, are subject to prediction through the model.

### Analysis of the network structure
The network is constructed by one heating station and 89 substations, connected by pipes. There are two different connecting strategies, tree structure and looped structure, and both of them are fully connected. 
- Tree schema: Radial connection, no loop.
  
- Looped schema: There is one loop in the structure, that will cause more complicated behavior of the physical elements distribution.
### Analysis of the yearly data
1. Based on the plot, it's easy to see that we can split the data into summer and winter, according to the different demand patterns. Summer dataset contains the data from June to October, winter dataset contains the rest.
   For the average temperature/pressure plots above, we can further validate that there are distinguishing differences between summer and winter heating supply demand.
2. The temperature difference between supply and return is about 30 °C for all pipes and substations.
3. 
## Technique
### Enhanced K-hop Information Aggregation via Shortest Path Analysis in Graph Networks
The methodology for identifying the shortest paths within a graph structure draws inspiration from established algorithms within the domain of graph theory [Citation Needed]. In the current research, we extend beyond the conventional paradigm of aggregating information solely from the immediate neighbors. We propose an advanced k-hop information gathering technique that systematically captures node attributes connected by the shortest path within a predefined maximal distance. This approach enables the assimilation of a richer informational context over a specified number of network layers.

The enrichment of the information set is achieved by utilizing the k-hop reachability within the network. This technique ensures that for each node, the feature set is not just a function of its adjacent nodes but also includes the attributes of nodes that, although not directly connected, play a significant role in the network's topology by virtue of being within the optimal path framework. By harnessing this expanded k-hop strategy, the proposed model is capable of integrating a more comprehensive representation of the network's structure, thereby enhancing the predictive performance and the accuracy of the subsequent analysis. 

The integration of information over these optimal paths is particularly pertinent in applications where the relational context of the nodes—defined by their shortest path connections—bears substantial influence on the network's functional characteristics. This refined approach to information gathering is anticipated to yield substantial improvements in tasks that are sensitive to the broader structural and relational nuances of the graph.

### Design of the neural network
In this case study, the node regression ct_KHOP model consists of several key components:

1. Initial Multilayer Perceptron (MLP): This component is a sequential model starting with a linear transformation that expands the input features from 2 to 64 dimensions, followed by batch normalization, a non-linear ReLU activation, another linear transformation, and a subsequent batch normalization with ReLU activation.

2. Regression Transformation MLP: A second sequential block is designed with a similar structure to the initial MLP but narrows the feature space from 64 to 1 dimension. This transformation is presumably aimed at regressing the learned embeddings to a single output value, following the non-linear activation and batch normalization steps.

3. Initial and Final Linear Layers: Two separate linear transformations are included, each mapping the 64-dimensional feature space to a single dimension. These layers likely serve as connectors or adapters to the sequential blocks or as additional transformation steps for the features.

4. GCN_SP Modules: The core of the ct_KHOP model lies in its ModuleList of GCN_SP_Layer instances. Each GCN_SP_Layer includes an MLP similar to the initial one, ensuring a consistent transformation of features within the graph convolutional layers. The GCN (Graph Convolutional Network) layer itself is a pivotal part of the model, designed to process graph-structured data by considering node features and the graph topology.

5. Linear Modules: The model includes a ModuleList of linear transformations, each taking a 64-dimensional input to a single-dimensional output. These modules might be used to process node-level features individually or in concert with the GCN layers.

6. Layer Normalization: The model employs layer normalization modules to stabilize the learning process. Each LayerNorm module is configured to normalize a 64-dimensional input feature vector, which could be essential for maintaining training stability across deeper network layers.

The ct_KHOP GNN model is designed to be a sophisticated network designed for regressing graph-structured data. It incorporates multiple processing layers, including MLPs for feature embedding, GCN layers for capturing the graph topology's influence on node features, and linear layers for feature transformation. The model emphasizes normalization and non-linear activation to manage feature distribution and introduce non-linearity, essential for capturing complex patterns within the data. This architecture suggests a focus on learning robust node representations that are subsequently regressed to a target output.

###

## Experiment Results

### Accuracy
[picture of the tree/looped network, temperature and pressure]

Method to compute the return temperature

```markdowna  
![Alt text for your graph](path/to/your/graph.png)
```
## Running the Code
To run the code provided in Colab Notebook, make sure to add the [data] folder to Google drive under path [/content/drive/My Drive/] first. The [data] directory is in link: https://drive.google.com/drive/folders/1xx12tLFajrRgSRFmo05LQ7-vveLED9Rp?usp=drive_link

And follow the order of cells to run the Colab Notebook.

## Citation
[//]Darcy–Weisbach equation. (2024, January 10). In Wikipedia. https://en.wikipedia.org/wiki/Darcy%E2%80%93Weisbach_equation
[]Abboud, R., Dimitrov, R., & Ceylan, İ. İ. (2022). Shortest Path Networks for Graph Property Prediction. ArXiv. /abs/2206.01003
