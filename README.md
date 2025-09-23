# Safe Guaranteed Dynamics Exploration with Probabilistic Models

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

This repository provides the implementation for the paper "Safe Guaranteed Dynamics Exploration with Probabilistic Models". We introduce **SageDynX**, an online and adaptive algorithm designed to handle tasks with uncertain dynamics in safety-critical environments. The method guarantees both **optimality** and **safety** throughout execution while operating in a **non-episodic setting** with **a-priori unknown dynamics**.

The code is licensed under the MIT license.

## Installation

1. Create new `workspace` folder. This is used as a base directory for the following steps.
2. Place the main repository `sage-dynx`
3. Install dependencies
    1. Download and install [acados](https://docs.acados.org/installation/) (does not need to be in `workspace`).
    2. Install [acados Python interface](https://docs.acados.org/python_interface/index.html).
    3. Install Python requirements
        ```bash
            cd sage-dynx
            pip install -r requirements.txt
        ```

## Usage

1. To run the code, run the following Python script from your base directory:

    ```
        python sage-dynx/main.py -param params_drone_sagedynx -i 3
        python sage-dynx/main.py -param  -i $i

    ```
    where,
    ```
        $param_file: Name of the param file, e.g. "params_drone_sagedynx" or "params_drone_opt"
        $i         : Experiment number, e.g. "1"
    ```
    see params folder for other param file names.

1. For visualizations/videos use the following script once the experiment is completed:

    ```
        python sage-dynx/visu_main.py -param params_drone_sagedynx -i 3
        python sage-dynx/visu_main.py -i $i -param $param_file
    ```
    This will generate a video of the simulation in the folder corresponding to the `$param_file` and the instance `$i`.


1. For reference experiment videos, please refer to the folder "experiment/drone/env_0" and the files named "video_gp.mp4" contained within.


1. The above commands will automatically create subfolders within the experiment directory, named according to the parameter file, environment number, and experiment number. Running the visualization script will generate videos for these experiments in the corresponding folders.

https://github.com/user-attachments/assets/b3200179-b7d4-4b13-a39b-057bdac47013

The video demonstrates the SageDynX algorithm in the drone navigation environment. The drone begins at the initial position (1,1) and aims to follow a heart-shaped reference trajectory while satisfying state constraints indicated by dashed red lines. The green line represents the optimal trajectory computed by a clairvoyant agent (known system dynamics). The dashed black line shows the agent’s trajectory using SageDynX. The thin multicolored lines illustrate predicted trajectories using different sampled dynamics starting from the drone’s position at different time steps, highlighted by cyan dots. SageDynX initially deviates from the optimal behavior, gathers informative data, and quickly converges towards close to optimal performance.
