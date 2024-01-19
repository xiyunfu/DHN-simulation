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

**Physical elements:**
1. Temperature (C)
2. Pressure (bar)
3. Mass flow (m^3/s)

**Physical relationship and formula:**
How to compute the mass flow based on known temperature and pressure. 
How to compute the return temperature based on known supply temperature and pressure.
- Darcy–Weisbach equation
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
### Shortest Path Network
Implement the idea from paper ...
### Design of the neural network
**hyperparameter:**
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
[//]Darcy–Weisbach equation. (2024, January 10). In Wikipedia. https://en.wikipedia.org/wiki/Darcy%E2%80%93Weisbach_equation
