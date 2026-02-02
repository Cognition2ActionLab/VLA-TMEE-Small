## Installing Conda Environment for BC-IB in LIBERO and CortexBench

The following guidance works well for a machine with V100/A100 GPU, cuda 11.8, driver 550.54.14.

First, git clone this repo and `cd` into it.

```bash
# clone project
git clone https://github.com/Cognition2ActionLab/VLA-TMEE-Small.git
cd VLA-TMEE-Small
```

---

#### 1. create python/pytorch env

```bash
# crerate conda environment
conda create -n vla_tmee_small python=3.10
conda activate vla_tmee_small
```

#### 2. install torch

```bash
# install PyTorch, please refer to https://pytorch.org/get-started/previous-versions/ for other CUDA versions. We recommend torch version >= 2.0.0
# e.g. cuda 11.8:
pip install torch==2.2.0 torchvision==0.17.0 torchaudio==2.2.0 --index-url https://download.pytorch.org/whl/cu118
```


#### 3. modify environment variables and install dependencies

```bash
export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/usr/lib/nvidia
export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/usr/local/cuda/lib64
export LD_PRELOAD=/usr/lib/x86_64-linux-gnu/libstdc++.so.6
source ~/.bashrc

sudo apt update && sudo apt upgrade -y
sudo apt install libegl1-mesa libegl1-mesa-dev libgl1-mesa-glx libglfw3 libglfw3-dev libglew-dev libosmesa6 libosmesa6-dev libgles2-mesa
conda install -c conda-forge mesalib
```

#### 4. install LIBERO

```bash
git clone https://github.com/Lifelong-Robot-Learning/LIBERO.git
cd LIBERO
pip install -e .
```


