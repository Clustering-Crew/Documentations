Jetson Nano native python version = Python 3.6

if you need to install other python versions > 3.6 follow the other documentation.
## Step 1 - Create Virtual environment with python3.6

Install Virtual environment package.

```bash
sudo apt-get install python3-venv
```

```bash
sudo -H python3 -m venv <VIRTUAL_ENVIRONMENT>
```

## Step 2 - Install Pytorch with CUDA support for python3.6

This piece of command is taken from [GitHub Issues](https://github.com/JaidedAI/EasyOCR/issues/491) 

According to the source - 

#### 1 - Upgrade your Pip version 

```bash
wget https://bootstrap.pypa.io/3.6/get-pip.py
sudo python3 get-pip.py
rm get-pip.py
```

For any python version > 3.6 - https://bootstrap.pypa.io/get-pip.py

#### 2- Install Torch with CUDA support

```bash
wget https://nvidia.box.com/shared/static/p57jwntv436lfrd78inwl7iml6p13fzh.whl -O torch-1.9.0-cp36-cp36m-linux_aarch64.whl
sudo apt-get install python3-pip libopenblas-base libopenmpi-dev 
sudo -H pip3 install Cython
sudo -H pip3 install torch-1.9.0-cp36-cp36m-linux_aarch64.whl
```

#### 3 - Check the installation Pytorch Compatibility with CUDA

```python
import torch

print("torch with cuda: "+ torch.cuda.is_available())
print("CUDNN version: " + torch.backends.cudnn.version())
```

When installation Pytorch you might encounter the following errors - 

```bash
Illegal Instruction
```

```
Illegal Instruction
(Core Dumped)
```

This error is caused by the numpy version >=1.19.5 . In order to debug the error you need numpy version < 1.19.4.

```bash
sudo -H pip3 install numpy==1.19.4
```

#### 4 - Install EasyOCR

```bash
sudo -H pip3 install easyocr
```

**Note : During this step `opencv-python-headless` takes long time to get installed. DO NOT TERMINATE THE PROCESS**

