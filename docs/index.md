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
  <strong>Alaa Khamis Rashwan</strong><sup>2</sup></p>
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

<div style="text-align: center;">
    <img src="https://raw.githubusercontent.com/kalvinwangzl/tsc_deeprl/refs/heads/main/docs/img/methodfig.png" alt="Image description" width="800" />
</div>

### **Methodology**
<div class="left-align">
<p>The proposed CoLight-DDQN approach integrates Deep Q-learning into the traffic signal control problem by designing and comparing different state representations for traffic environment observation and network architectures. The following subsections provide a detailed explanation of the observation of environmental states and the Q-network structures.</p>

<p>Inspired by conventional methods of MaxPressure, we first adopt the pressure of the intersections for the input of the Q-network which indicates how urgent it is to switch to specific signal phases. Such method makes decisions of actions based on the queue length on each lanes. But the pressure of the intersections does not consider the different traffic loads of different roads as they have different numbers of lanes. Therefore, the second set of observations instead uses the efficient traffic pressure of each traffic flow. It is the pressure divided by the number of lanes of each road. While pressure and efficient pressure successfully indicate the need for each action by the signal agent, one obvious information neglected in such a method is the vehicles that are running at the intersection. Here we use efficient pressure of traffic flow as well as demand of running vehicles for training of the Q-network. In such way we are able to reflect the impact of the information of both still and moving vehicles.</p>

<p>In this paper, we explore the performance combining popular state-of-the-art methods DQN and DDQN. DQN was proposed to use neural network to represent the Q function in reinforcement learning and reached extraordinary performance on gaming, such becoming one of the most popular mechanism in RL methods. Also DDQN is proposed to eliminate overestimation of the reward of some actions. There are two networks, online network and target network, which are updated at different times. Such methods enables better performance of the algorithm. We apply the network structure of MPLight and CoLight. MPLight is already implemented with DDQN and CoLight was implemented with DDQN. Therefore we propose the DDQN version of CoLight.</p>
</div>

<div style="text-align: center;">
    <img src="https://raw.githubusercontent.com/kalvinwangzl/tsc_deeprl/refs/heads/main/docs/img/dataset.png" alt="Image description" width="600" />
</div>

<div style="text-align: center;">
    <img src="https://raw.githubusercontent.com/kalvinwangzl/tsc_deeprl/refs/heads/main/docs/img/volume.png" alt="Image description" width="600" />
</div>

### **Results**
<div class="left-align">
<p>We conducted experiments on 3 sub-datasets of Jinan traffic flow dataset, which contains 12 (3×4) intersections, and Hangzhou traffic flow dataset, which contains 16 (4×4) intersections. All the intersections have four incoming and outgoing roads. For Jinan dataset the three sub-datasets are 1: whole real time data, 2: real data with 2000 vehicles and 3: real data with 2500 vehicles. The visualization as well as the volume of two datsets are shown above. We mainly evaluate the methods on Jinan dataset and test the adaptation ability of the methods on Hangzhou dataset to confirm the adaptive ability of these methods.</p>

<p>The final average travel time results are presented in Table I. The results indicate that incorporating ATS significantly enhances performance compared to Efficient Pressure and Pressure, while Efficient Pressure achieves slightly better results than Pressure. This demonstrates the importance of accounting for both efficient pressure, which reflects stationary vehicles, and the demand of moving vehicles. Furthermore, the findings confirm that modifying the observation in this manner is effective across all Deep Q-learning mechanisms.</p>

<p>The final throughput results are presented in Table II, which is the average number calculated in every 300s. When using Pressure as the observation set, MaxPressure generally achieves higher throughput. However, when Efficient Pressure (E-Pressure) and ATS are used as the observation set, the other three methods outperform MaxPressure. Notably, our CoLight-DDQN method, when combined with ATS as the observation set, achieves the best performance across the entire Jinan dataset.From a methodological perspective, while MaxPressure demonstrates its effectiveness when using the naive Pressure observation, the additional information provided by Efficient Pressure and ATS allows CoLight-DDQN to outperform the other approaches. MPLight performs well on smaller traffic datasets but exhibits poor performance on the full dataset. In contrast, CoLight-based methods demonstrate strong adaptability across all scenarios.</p>

<div style="text-align: center;">
    <img src="https://raw.githubusercontent.com/kalvinwangzl/tsc_deeprl/refs/heads/main/docs/img/table.png" alt="Image description" width="800" />
</div>

<p>We also illustrate the average travel time and throughput curves of 3 RL methods for the two datasets over training rounds 15 to 80 to study their learning performance. Since the early stages of training are unstable, we visualize only the final 65 rounds to highlight the effects of training. The results are consistent with the average travel time analysis, confirming that CoLight-DDQN achieves the lowest average travel time. Additionally, the training process with DDQN exhibits significantly greater stability compared to DQN, with substantially fewer fluctuations, demonstrating the advantages of our approach. However, some sudden dips and spikes are observed in the curves, which can be attributed to outliers when the Q-network converges to a local optimum; these deviations are quickly corrected in subsequent steps. Among all methods, CoLight-DDQN with ATS exhibits the fewest dips and spikes, further validating its stability and robustness in training.</p>

<div style="text-align: center;">
    <img src="https://raw.githubusercontent.com/kalvinwangzl/tsc_deeprl/refs/heads/main/docs/img/traincurve.png" alt="Image description" width="800" />
</div>
</div>

### **Related links**
<div class="left-align">
The CoLight-DDQN is implemented with the codebase of <a href="https://github.com/wingsweihua/colight" target="_blank" style="color: blue; text-decoration: underline;">CoLight</a>, <a href="https://github.com/Chacha-Chen/MPLight" target="_blank" style="color: blue; text-decoration: underline;">MPLight</a>, <a href="https://github.com/LiangZhang1996/Advanced_XLight" target="_blank" style="color: blue; text-decoration: underline;">Advanced_XLight</a>, <a href="https://github.com/LiangZhang1996/Efficient_XLight" target="_blank" style="color: blue; text-decoration: underline;">Efficient_XLight</a>.
</div>
