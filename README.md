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
Component: 
1. The Heating Station(HS): Providing hot water to the substations through pipes.
2. The substations: The end nodes of the network, have heating demand.
3. The pipes: connecting the network.

Node representation:
In this project, node representation is employed, which means that all the components are represented as nodes instead of edges. For each node, there are three main attributes, temperature, pressure and mass flow. Node representation provides a clear way to implement the graph neural network. Further more, considering the characteristic of District Heating simulation that the graph structure always stay the same, node represnetation also provides a more convenient way to have a steady graph structure, training on data only changing the nodes information without changing the graph information.

The known attributes: 
For the heating station: temperature is known
For the substations: pressure is known
The rest attributes are the values that need to be predicted by the model.

### Analysis of the network structure
The network is constructed by one heating station and 89 substations, connected by pipes. There are two different connecting strategies, tree structure and looped structure, and both of them are fully connected. In tree structure, there is no loop, 
### Analysis of the yearly data

split the data into summer and winter, according to the different demand patterns. 
## Technique
### Shortest Path Network
Implement the idea from paper ...
### Design of the neural network
hyperparameter:
max distance:
layer:
lr:
dropout:

###

## Experiment Results
Discuss the results of your experiments. To insert a graph, use the following syntax:
### Accuracy
[picture of the tree/looped network, temperature and pressure]

comparing the accuracy of simulation with using the sensor

Comparing with baseline model

Method to compute the return temperature

```markdown
![Alt text for your graph](path/to/your/graph.png)
```
## Citation

