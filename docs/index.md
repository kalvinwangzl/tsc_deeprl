---
layout: none
title: A CoLight-DDQN Approach for Adaptive Traffic Signal Control
permalink: /
---

<style>
  body {
    text-align: left;
    font-family: Arial, sans-serif;
    margin: 20 200px;
    padding: 0;
  }
  h1 {
    text-align: center;
    font-size: 36px;
    font-weight: bold;
    margin-left: 200px;  
    margin-right: 200px;
  }
  h3 {
    text-align: left;
    font-size: 24px;
    font-weight: bold;
    margin-top: 20px;
    margin-bottom: 10px;
    margin-left: 200px;
    margin-right: 200px;
  }
  .subtitle {
    text-align: center;
    font-size: 22px;
    font-weight: normal;
  }
  .author {
    text-align: center;
    font-size: 18px;
    margin: 5px 0;
    line-height: 1.6;
  }
  .affiliation {
    text-align: center;
    font-size: 16px;
    color: gray;
  }
  .highlight {
    font-size: 20px;
    font-weight: bold;
    color: #555;
  }
  .links {
    text-align: center;
  }
  .links img {
    width: 80px;
    margin: 10px;
  }
  .links a {
    text-decoration: none;
    font-size: 18px;
    color: #007bff;
  }
  .left-align {
    text-align: left;
    margin: 0 200px;
  }
</style>

# **A CoLight-DDQN Approach for Adaptive Traffic Signal Control**

<div class="author">
  <p><strong>Tongyu Liu</strong><sup>1</sup> &nbsp;&nbsp; 
  <strong>Zile Wang</strong><sup>1</sup> &nbsp;&nbsp;
  <strong>Alaa Khamis Rashwan</strong><sup>1,2</sup></p>
  <p><sup>1</sup> University of Toronto &nbsp;&nbsp; <sup>2</sup> KFUPM</p>
</div>

<div class="links">
  <a href="https://github.com/kalvinwangzl/Traffic-Signal-Control-with-CoLight-DDQN">
    <img src="https://github.githubassets.com/images/modules/logos_page/GitHub-Mark.png" alt="Code" width="50">
    <br>Code
  </a>
</div>

### **Abstract**
<div class="left-align">
Traffic Signal Control (TSC) is a critical challenge in the optimization of urban traffic networks, where efficient management of traffic flow is essential for improving transportation systems. While traditional TSC methods are effective in specific scenarios, they often struggle to adapt to the dynamic and complex nature of real-world traffic environments. In recent years, Reinforcement Learning (RL) methods have gained traction due to their ability to continuously learn and adapt to fluctuations in traffic flow. This paper investigates the selection of environmental observation states and Q-network architectures within the framework of Deep Q-Learning for TSC.  We propose an approach that integrates the CoLight model, which utilizes a graph attention block, with Double Deep Q-Networks (DDQN) to enhance the stability and performance of the learning process. The proposed CoLight-DDQN method is evaluated through extensive experiments, including tests on datasets from both Jinan and Hangzhou, showing its superior ability to reduce intersection travel time and increase throughput when compared to existing state-of-the-art TSC methods. These results highlight the robustness and adaptability of the CoLight-DDQN framework in optimizing traffic signal control across different urban environments.
</div>

### **Methodology**
<div class="left-align">
<p>The proposed CoLight-DDQN approach integrates Deep Q-learning into the traffic signal control problem by designing and comparing different state representations for traffic environment observation and network architectures. The following subsections provide a detailed explanation of the observation of environmental states and the Q-network structures.</p>

<p>Inspired by conventional methods of MaxPressure, we first adopt the pressure of the intersections for the input of the Q-network which indicates how urgent it is to switch to specific signal phases. Such method makes decisions of actions based on the queue length on each lanes. But the pressure of the intersections does not consider the different traffic loads of different roads as they have different numbers of lanes. Therefore, the second set of observations instead uses the efficient traffic pressure of each traffic flow. It is the pressure divided by the number of lanes of each road. While pressure and efficient pressure successfully indicate the need for each action by the signal agent, one obvious information neglected in such a method is the vehicles that are running at the intersection. Here we use efficient pressure of traffic flow as well as demand of running vehicles for training of the Q-network. In such way we are able to reflect the impact of the information of both still and moving vehicles.</p>

<p>In this paper, we explore the performance combining popular state-of-the-art methods DQN and DDQN. DQN was proposed to use neural network to represent the Q function in reinforcement learning and reached extraordinary performance on gaming, such becoming one of the most popular mechanism in RL methods. Also DDQN is proposed to eliminate overestimation of the reward of some actions. There are two networks, online network and target network, which are updated at different times. Such methods enables better performance of the algorithm. We apply the network structure of MPLight and CoLight. MPLight is already implemented with DDQN and CoLight was implemented with DDQN. Therefore we propose the DDQN version of CoLight.</p>
</div>

### **Dataset**
<div class="left-align">
在这里放实验图表，描述实验结果...
</div>

### **Results**
<div class="left-align">
在这里放实验图表，描述实验结果...
</div>
