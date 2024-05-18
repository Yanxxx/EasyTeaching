# Teleoperation-Driven and Keyframe-Based Generalizable Imitation Learning for Construction Robots

# EasyTeaching: Teach robot to learn manipulation tasks with limited amount of human operated task demonstrations
Tasks other than the pick and place task are common in daily life and industrial setup. 
This work is done in 2021. 


![Trajectory tasks](./images/image17)
![Trajectory tasks](./images/image14)
![Trajectory tasks](./images/image15)
![Trajectory tasks](./images/image12)


Teach robot with these tasks are challenging. We proposed a novel teaching paradigm for the robot to learn the trajectory type tasks. 

![Overview of the traing method](./image/overview.png)

In this method, we seperate it into three parts:
1. The keyframe identification method to evaluate the demonstrated data.
2. A reinforcement learning based task exploration and learn from the demonsrated data. 
3. To avoid the ambiguity of image input, we introduced the latent space for the goal generation and robot state representation.


![Keyframe evaluation from demonstrated task episode. The green dots are the operator inputs. The blue dots is the robot trajectory collected from the robot contoller. The red dots are the evaluted keyframe for the task. The green dots are drifted away from the robot trajectory, this is because the human teleoperated the robot and fix the robot movement while operating.](./images/problem-discription.png)

![The reinforcement learning framework](./images/reinforcement-learning.png)

![The latent space generation.](./images/latent-space.png)


Use this method, we did the experiment with the excavation task. 
![Human operated task demonstration.](./images/image37.gif)

![Trained model operated task operation.](./images/image47.gif)

The success rate is of our method is shown below:

![Task success rate.](./images/image140.png)

We also did ablation study on the hyperparameters:

![Ablation Study.](./images/ablation-study.png)

We have submitted this work to the Journal of Computing in Civil Engineering with the following title. The article is accepted and will be published soon. I will update the link after the paper is published. 

# Teleoperation-Driven and Keyframe-Based Generalizable Imitation Learning for Construction Robots
## Abstract
The construction industry faces challenges with low productivity and high injury rates. Robots can improve these issues by automating processes. However, teaching robots to perform complex tasks is difficult. We present a framework that uses human teleoperation data to train robots for repetitive construction tasks. First, we developed a teleoperation method and interface to control robots on construction sites. Second, we propose a method to extract keyframes from human operation data, reducing noise and redundancy in the training data. Third, we model the robot's visual observations of the working space to improve learning performance and reduce computational load. We validated our framework by teaching a robot to generate trajectories for excavation tasks using human operators' teleoperations. Results show that our method outperforms existing approaches, demonstrating its potential for application.
