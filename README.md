# Just Go with the Flow: Self-Supervised Scene Flow Estimation

Code release for the paper Just Go with the Flow: Self-Supervised Scene Flow Estimation, CVPR 2020 (Oral).

Authors: Himangi Mittal, Brian Okorn, David Held

[arxiv] [Project Page]

### Introduction
In this work, we propose a method of scene flow estimation using two self-supervised losses, based on nearest neighbors and cycle consistency. These self-supervised losses allow us to train our method on large unlabeled autonomous driving datasets; the resulting method matches current state-of-the-art supervised performance using no real world annotations and exceeds stateof-the-art performance when combining our self-supervised approach with supervised learning on a smaller labeled dataset.

For more details, please refer to our paper or project page.

### Installation 
#### Requirements
   ```
   CUDA 9.0  
   Tensorflow-gpu 1.9
   Python 3.5
   g++ 5.4.0
   ```
#### Steps
  (a). Clone the repository.
  ```
  git clone https://github.com/HimangiM/Self-Supervised-Scene-Flow-Estimation.git
  ```
  (b). Install dependencies
  ```
  Create a virtualenv
  python3 -m venv sceneflowvenv
  source sceneflowvenv/bin/activate
  cd Self-Supervised-Scene-Flow-Estimation
  pip install -r requirements.txt
  ```
  ```
  Check for CUDA-9.0
  ```
  (c). Compile the operations
  The TF operators are included under src/tf_ops. Check the CUDA compatability and edit the architecture accordingly in makefiles of each folder (tf_ops/sampling, tf_ops/grouping, tf_ops/3d_interpolation). Finally, move into each directory and run make. As a shortcut, you can also run source make_tf_ops.sh after editing the architecture.
    
### Datasets
   You can download the kitti dataset from the google drive link given here (). Each file is in the .npz format and has three keys: pos1, pos2 and gt, representing the first frame of point cloud, second frame of point cloud and the ground truth scene flow vectors for the points in the first frame.The dataset directory should look as follows:
   ```
   KITTI
   |-train
   |-test
   ```
   The data preprocessing file to run the code on KITTI is present in the src folder: kitti_dataset_self_supervised_cycle.py. 
  
### Training, Fine-tuning, and Evaluation
   You can download the pretrained model from here.
   
   To train on KITTI dataset, execute the script:
   ```
   source src/commands/command_train_1nn_cycle_nuscenes_keep_interp_ons_full_fine_tune_kitti_1e4_cache.sh
   ```
### Visualization
You can use Open3d to visualize the results. A sample script is given in the 
   
   
    
