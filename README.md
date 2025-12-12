# Super Mario Bros RL

This project implements and compares PPO (Proximal Policy Optimization) agents for Super Mario Bros using baseline and curriculum learning approaches.

**Project Title**: Curriculum-Based Reinforcement Learning for Super Mario Bros
**Group 12**: Yoav Feigenbaum, Rishit Sharma, Eshaan Rawat

## Overview

The project contains two notebooks:
- **`ppo_mario_baseline.ipynb`**: Baseline PPO agent trained on the full action space (COMPLEX_MOVEMENT)
- **`ppo_mario_curriculums.ipynb`**: Curriculum learning approaches with incremental actions and rewards

## Prerequisites

- Conda (Miniconda or Anaconda)
- Python 3.10 (required due to Gym environment compatibility)

## Setup

### 1. Clone the Repository

```
git clone https://github.com/eshaanrawat1/cs175_group12.git
cd cs175_group12
```

### 2. Create Conda Environment

Create a new conda environment with Python 3.10:

```
conda create -n mario_rl python=3.10
conda activate mario_rl
pip install -r requirements.txt
```

This will automatically install all reuqired dependencies for the project.

### 3. Install Local Gym-Super-Mario-Bros Package

The project includes a local version of `gym-super-mario-bros` which can be installed as follows: 

```
cd gym-super-mario-bros
pip install -e .
cd ..
```

### 4. Running Notebooks

First activate the conda env

`conda activate mario_rl`

Then, start Jupyter with the command `jupyter notebook <notebook_name>` and open a new notebook and test the first cell in either PPO notebook:

### Baseline Training

1. Open `ppo_mario_baseline.ipynb` in Jupyter
2. Run all cells sequentially

### Curriculum Training

1. Open `ppo_mario_curriculums.ipynb` in Jupyter
2. Run all cells sequentially
3. The notebook will train curriculum-based PPO agents 

### 5. Project Deliverables 

### Training
The training time for this project is usually very long for a working PPO model that can achieve a decent reward, usually around 3 hours for 1M timesteps and 15 hours for 5M timesteps. 

As a result, our group has pre-loaded models which can be used for visualizing our results. If you would like to see a quick training of the models, choose either notebook and run the results up to cell 11A. This runs a trial run and plots results which should take around 6-10 minutes.

If you run cell 11B (full training), you can see periodic heartbeats that track the mean reward, among other steps. The format looks like this: 
```
[Heartbeat] 9,200/1,000,000 steps (0.9%) | Elapsed: 0h01m00s | Speed: 153 steps/s | ETA: 1h47m
------------------------------------------
| rollout/                |              |
|    ep_len_mean          | 298          |
|    ep_rew_mean          | 418          |
| time/                   |              |
|    fps                  | 153          |
|    iterations           | 9            |
|    time_elapsed         | 60           |
|    total_timesteps      | 9216         |
| train/                  |              |
|    approx_kl            | 0.0029891497 |
|    clip_fraction        | 0.0671       |
|    clip_range           | 0.1          |
|    entropy_loss         | -2.45        |
|    explained_variance   | 0.217        |
|    learning_rate        | 0.000248     |
|    loss                 | 110          |
|    n_updates            | 32           |
|    policy_gradient_loss | -0.00391     |
|    value_loss           | 287          |
------------------------------------------
------------------------------------------
| rollout/                |              |
|    ep_len_mean          | 298          |
|    ep_rew_mean          | 418          |
| time/                   |              |
|    fps                  | 152          |
|    iterations           | 10           |
|    time_elapsed         | 66           |
|    total_timesteps      | 10240        |
| train/                  |              |
|    approx_kl            | 0.0018198974 |
|    clip_fraction        | 0.0474       |
|    clip_range           | 0.1          |
|    entropy_loss         | -2.44        |
|    explained_variance   | 0.449        |
|    learning_rate        | 0.000248     |
|    loss                 | 114          |
|    n_updates            | 36           |
|    policy_gradient_loss | -0.00265     |
|    value_loss           | 335          |
------------------------------------------
```

### Demos
If you would like to see a demo of the training results, navigate to the `/demos` folder. 

The gifs that end with generalize show the results of a PPO model trained on level 1-1, and then generalized to see how well they perform on slightly similar levels (2-1, 3-1, 4-1). 

The other videos show the performances of both the baseline and curriculum agents on levels 1-1 and 1-2.

### Models
In the /models directory, we saved a list of pre-loaded models that were used for different training runs. By plugging in a model name for Section 18 (Load Model) in either the baseline or curriculum notebook, you can evaluate and visualize the results of an individual model.

Just replace this line: `model_path = "models/ppo_baseline_1-1/best_model"` with the name of the model such as: `model_path = "models/ppo_baseline_1-2/best_model"`

`ppo_baseline_1-1`: Baseline model trained on level 1-1

`ppo_baseline_1-2`: Baseline model trained on level 1-2

`ppo_curriculum_1-1`: Curriculum model with both incremental rewards and actions trained on level 1-1

`ppo_curriculum_1-2`: Curriculum model with both incremental rewards and actions trained on level 1-2

`ppo_curriculum_2`: Curriculum model with ONLY incremental reward function

`ppo_curriculum_3`: Curriculum model with ONLY incremental reward function (different ordering from #2)

`ppo_curriculum_4`: Curriculum model with ONLY incremental reward function (different ordering from #3)

`ppo_curriculum_5`: Curriculum model with ONLY incremental action space

`ppo_curriculum_7`: Curriculum model with both incremental rewards and actions trained on level 1-1