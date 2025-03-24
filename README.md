# EasyTeaching: A Keyframe-Driven Framework for Robotic Manipulation Learning
**Leveraging Limited Human Demonstrations to Enable Versatile Robot Training**

This work was done in 2021. 

### Overview
The EasyTeaching framework is designed to empower robots to learn complex manipulation tasks using a limited number of human-operated demonstrations. Developed in 2021, the approach aims to simplify robot teaching for **non-experts** while overcoming common challenges such as **noisy data, exploration inefficiencies, and the scarcity of demonstration episodes**.

#### The overview of the proposed method is shown in following figure. 
<p align="center">
  <img src="./images/overview.png" />
</p>

### Motivation
The core motivations behind EasyTeaching include:
- **Accessibility**: Enabling non-robotics and non-machine learning experts to teach robots.
- **Efficiency**: Utilizing a minimal set of human demonstrations to train robust robotic policies.**
- **Versatility**: Adapting to a variety of trajectory-based tasks, such as pick-and-place and other complex maneuvers.




### Defining Trajectory Tasks

Trajectory tasks are those in which a robot must follow a specific path defined by a series of states or key points. For example, the pick-and-place task is a specialized form of trajectory task. Although human teleoperation provides a natural way to generate these paths, several challenges arise in practice.
The following figures illustrate a few trajectory tasks. 

<p align="center">
<img src="./images/image14.gif" width="250" />  <img src="./images/image15.gif" width="250" />  <img src="./images/image17.gif" width="250" />
</p>

To elabrate, the pick and place task can be treated as a special case of trajectory task.

### Challenges and Proposed Solutions

#### Challenges
1. **Noisy Demonstration Data:**
     - **Human Factors**: Operators have personal biases, leading to non-uniform movements.
     - **Inherent Noise**: The demonstrated trajectories often include extraneous or suboptimal actions.

2. **Inefficient Random Exploration:**
     - **High Dimensionality**: Many constraints make brute-force exploration computationally expensive.
     - **Low Success Rate**: The probability of stumbling upon a feasible trajectory randomly is extremely low.

3. **Limited Demonstration Episodes:**
     - **Cost of Collection**: Amassing a large dataset of demonstrations is both time-consuming and expensive.

#### Solutions
To tackle these challenges, EasyTeaching introduces a multi-faceted approach:

- **Keyframe Identification:** Extracts crucial states from demonstration data to serve as milestones.

- **Hierarchical Reinforcement Learning:** Divides the task into two policies:

  - **Keyframe Policy:** Generates optimal keyframes based on the current state and the final goal.

  - **Primitive Policy:** Executes low-level actions to reach the keyframe subgoals.

- **Latent Space Representation:** Uses Variational Autoencoders (VAEs) to encode high-dimensional sensory inputs (e.g., RGB-D images) into a compact latent space, reducing computational overhead and mitigating image ambiguity.

### Methodology


**1. Keyframe Extraction and Evaluation**

The process begins with modeling the task as a shortest path problem—from the initial state to the goal state—using dynamic programming-based reinforcement learning. Three types of data points are considered:
  - **Operator Inputs (Green Dots):** Indicate the intended movement.
  - **Robot Trajectories (Blue Dots):** Recorded paths from the robot controller.
  - **Evaluated Keyframes (Red Dots):** Crucial points identified to guide the learning process.

  > Note: The misalignment between operator inputs and robot trajectories highlights the need for refining human demonstrations to better suit robotic control.
<p align="center">
  <img src="./images/problem-discription.png" width="600" /> 
</p>

**2. Reinforcement Learning Framework**

The dual-policy framework comprises:
  - **Keyframe Policy:** Responsible for determining the optimal keyframe given the current robot state and the desired final state.
  - **Primitive Policy:** Generates the low-level actions required to transition from the current state to the determined keyframe.

Both policies benefit from a latent space module that fuses state, subgoal, and goal representations, thereby simplifying the decision-making process.
<p align="center">
  <img src="./images/reinforcement-learning.png" /> 
</p>

**3. Latent Space Generation**

The latent space module is trained with a VAE on a dataset that includes both human demonstration and robot exploration data. This transformation:
  - **Reduces Dimensionality:** Condenses high-dimensional sensory inputs to a manageable latent representation.
  - **Enhances Exploration:** Focuses the reinforcement learning process on the most relevant features, improving both learning speed and policy performance.

<p align="center">
  <img src="./images/latent-space.png" /> 
</p>


#### Experimental Evaluation

**Application to Excavation Tasks**
The framework was validated through a series of experiments on an excavation task. Two key phases were tested:

1. **Human-Operated Demonstrations:** Operators guided the robot to perform the task, providing the initial demonstration data.

2. **Autonomous Robot Operation:** The trained policies were then deployed for autonomous operation.

**Results:**

- The method demonstrated a high success rate compared to existing approaches.

- Ablation studies on the length of the latent space confirmed the robustness of the approach, highlighting the balance between representation detail and computational efficiency.

##### Human operated task demonstration 
<p align="center">
  <img src="./images/image37.gif" width="500" /> 
</p>
##### Trained operation by robot 
 <p align="center">
  <img src="./images/image47.gif" width="500" /> 
</p>

##### The success rate is of our method is shown below:
 <p align="center">
  <img src="./images/image140.png" width="600" /> 
</p>

#### We also did ablation study on the hyperparameters (the length of the encoded latent space):

 <p align="center">
  <img src="./images/ablation-study.png" /> 
</p>

### Future Directions


Further enhancements to EasyTeaching include:

- **Integration of Advanced Encoders:** Replacing the current latent space module with CLIP-based image and language encoders to incorporate contextual and semantic understanding.

- **Expanding to Broader Tasks:** Extending the methodology to more diverse manipulation tasks across different domains.

### Published Work

The work has been submitted to the Journal of Computing in Civil Engineering under the title:

**Teleoperation-Driven and Keyframe-Based Generalizable Imitation Learning for Construction Robots**

[paper](manuscript.pdf)

# Teleoperation-Driven and Keyframe-Based Generalizable Imitation Learning for Construction Robots
## Abstract
The construction industry faces challenges with low productivity and high injury rates. Robots can improve these issues by automating processes. However, teaching robots to perform complex tasks is difficult. We present a framework that uses human teleoperation data to train robots for repetitive construction tasks. First, we developed a teleoperation method and interface to control robots on construction sites. Second, we propose a method to extract keyframes from human operation data, reducing noise and redundancy in the training data. Third, we model the robot's visual observations of the working space to improve learning performance and reduce computational load. We validated our framework by teaching a robot to generate trajectories for excavation tasks using human operators' teleoperations. Results show that our method outperforms existing approaches, demonstrating its potential for application.
