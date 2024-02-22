# Advancing Map-less Underwater Navigation

## Research Question
How can the performance and robustness of map-less underwater navigation for low-cost underwater robots be enhanced by comparing and integrating Advanced Actor-Critic (A2C), Proximal Policy Optimization (PPO), and Trust Region Policy Optimization (TRPO) algorithms, while addressing the challenge of navigation failure in constrained environments?

## Project Overview
This research investigates the efficacy of various reinforcement learning algorithms, including Actor-Critic with Experience Replay (A2C), Proximal Policy Optimization (PPO), and Trust Region Policy Optimization (TRPO), to enhance the navigation capabilities of low-cost underwater robots. The focus is on developing a robust and resilient navigation system integrating advanced sensor fusion techniques for improved depth perception and obstacle avoidance. The project also explores the refinement of reward functions to recover effectively from navigation failures, ensuring consistent progress toward designated goals in diverse underwater environments.

## Key Components
- **Unity Environment**: Development of a Unity-based simulation environment for training and testing the reinforcement learning models.
- **3D Modeling**: Design and integration of detailed 3D models for underwater robots and environments within the Unity framework.
- **ROS Integration**: Utilization of ROS Melodic on Ubuntu 18.04 for real-world application and testing of trained models.
- **Reinforcement Learning Models**: Implementation and comparison of A2C, PPO, and TRPO algorithms for underwater navigation.

## Setup Instructions

### Steps to Build the Unity Project:

1. **Open the Project in Unity**:
   - Launch Unity Hub and add the `Water` project by navigating to the location `/home/ether/Documents/Robotics_Navigation/underwater_env/Water`.
   - Open the project in the Unity Editor.

2. **Build the Project**:
   - Within Unity, go to `File` > `Build Settings`.
   - Select your target platform (for example, Linux if you're on Ubuntu).
   - Click on `Build And Run` or `Build` if you want to just build without running.
   - Choose an output directory where the executable will be placed. You could create a new folder within the `underwater_env` directory, like `Water`, and select that.

3. **Verify the Build**:
   - After the build process is complete, navigate to the output directory you selected (e.g., `/home/ether/Documents/Robotics_Navigation/underwater_env/Water`).
   - Ensure there is an executable file for the Unity environment.
     
### Virtual Environment Setup
Create a Python 3.6 virtual environment named `UW_nav`:
```bash
virtualenv UW_nav --python=python3.8
```

Activate the virtual environment:
```bash
source ~/UW_nav/bin/activate
```

Install the required dependencies:
```bash
pip install -r requirements.txt
```

### ML-Agents Setup
Clone the ML-Agents repository and navigate to it:
```bash
git clone --branch release_18 https://github.com/Unity-Technologies/ml-agents.git
cd ml-agents
```

Install the `ml-agents-envs` and `gym-unity` packages:
```bash
pip install -e ./ml-agents-envs
pip install gym-unity==0.27.0
```

### Training and Testing
For training the models, run:
```bash
python3 ppo_gym.py --save-model-interval 5 --env-name navigation --eval-batch-size 0 --min-batch-size 2048 --num-threads 1 --hist-length 5
```

For testing the models, run:
```bash
python3 ppo_gym_test.py --env-name navigation --eval-batch-size 2000 --hist-length 5
```
<!-- ## Research Findings and Contributions
This project contributes to the field of underwater robotics by:
- Comparatively analyzing the performance of A2C, PPO, and TRPO in map-less navigation scenarios.
- Enhancing the robustness of underwater navigation systems through advanced sensor fusion and reward function refinement.
- Providing insights into overcoming navigation failures in constrained underwater environments.
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
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 -->

### Running on cluster
Install wireguard to you local machine:
   ```bash
   sudo apt install wireguard
   ```
Up the wiregrad interface
   ```bash
   sudo wg-quick up ~/Downloads/mdeowan698.conf
   ```
Connect with cluster:
   ```bash
   ssh <<username>>@sms.lis-lab.fr
   ```
Create a new Conda environment:
   ```bash
   conda create --name <env-name>
   ```
Activate the Conda environment:
   ```bash
   conda activate <env-name>
   ```
Install Python 3.6:
   ```bash
   conda install python=3.8
   ```
Install gdown for downloading files from Google Drive:
   ```bash
   pip install gdown
   ```
Downloading Files from Google Drive
To download files from Google Drive, you can use the `gdown` command followed by the file ID:
```bash
gdown --id <file_id>
```
Running Jupyter Notebook Locally

To run Jupyter Notebook locally, you can use SSH tunneling:
```bash
ssh -N -L 8888:localhost:8888 mdeowan698@sms.lis-lab.fr
```
Then access Jupyter Notebook in your web browser using:
```
http://localhost:8888/
```
Install project dependencies follow Environment Setup

For running on Cluster GPU first check the aviblity of the GPU
```bash
info-cluster
```
Select specific GPU and alocate time you wanted to run
```bash
srun --time=02:00:00 --gres=gpu:1 --partition=mundus --mem=64G --pty bash -l
```
## Acknowledgments
Special thanks to Prof. Ricard Marxer for supervising this project and the University of Toulon for providing the necessary resources and support. Additionally, gratitude is extended to the open-source communities of ROS, Unity, and ML-Agents for their invaluable tools and frameworks.
