---
title: TensorFlow Deep learning Setup using GPU
author: rexdivakar
date: 2020-09-08 11:33:00 +0800
categories: [deeplearning, tensorflow_setup]
tags: [tensorflow, gpu]
math: true
mermaid: true
toc: true # table of contents
comments: true
pin: false

# image:
#   path: /commons/devices-mockup.png
#   width: 800
#   height: 500
#   alt: Deep Learning frameworks.
---

![Deep Learning frameworks]({{"/assets/img/tf_deeplearning.png"| absolute_url}}){: width="700" height="400" }
_Deep Learning frameworks_

The interest on deep-learning has been growing enormous in the past couple of months but in order to get started we need a stable development environment. I find many beginners facing problems while installing libraries and setting up environment. As i have faced first time when i was trying. So this guide is totally for beginners.

# Installation Setup

We will cover the following steps:

1. Install Anaconda & Python
2. Install/ Update GPU Drivers
3. Install CUDA Toolkit & cuDNN
4. Add Environment Variables to the PATH in Windows
5. Install TensorFlow & Keras
6. Verify the package run

### (Step-1) Installation of Anaconda

In this step, kindly download the Anaconda Python package manager for your platform (Windows/Linux) and install it accordingly.

<https://www.anaconda.com/products/distribution>

### (Step-2) Install GPU Drivers — CUDA 10.1 requires 418.x or higher

Now, Choose your appropriate graphics driver and install it, I recommend you to update to the latest version for better performance.

![Nvidia Drivers]({{"/assets/img/nvidia_driver.png"| absolute_url}}){: width="700" height="400" }
_nvidia driver download_

NVIDIA Drivers: <https://www.nvidia.com/Download/index.aspx?lang=en-us>

### (STEP-3) Install CUDA Toolkit — TensorFlow supports CUDA 10.1 (TensorFlow >= 2.1.0)

![Cuda toolkit]({{"/assets/img/cuda.png"| absolute_url}}){: width="700" height="400" }
_cuda toolkit download_

> `Note:` Kindly choose the CUDA version according to your Nvidia GPU version to avoid errors.
{: .prompt-tip }

Note: Kindly choose the CUDA version according to your Nvidia GPU version to avoid errors.

1. Choose the desired platform and download it  [**Cuda Toolkit**](https://developer.nvidia.com/cuda-downloads?target_os=Windows&target_arch=x86_64&target_version=10)

> Make sure you have the right CUDA version and drivers installed else the setup won't work!

2. Install CUDA Toolkit with default settings and usually it takes time so bare with it!

![cuda]({{"/assets/img/c_tool.png"| absolute_url}}){: width="700" height="400" }
_cuda toolkit_

### (Step-4) Adding Cudnn libraries

Cudnn libraries provide accelerated performance on GPU usage, so we need to add it in for smoother and efficient performance.

<https://developer.nvidia.com/cudnn-download-survey>

It will prompt you to create an account, go ahead and sign up and download the appropriate version for your platform.

Now extract the Cudnn libraries zip file and copy all the files to

> “C:\Program Files\NVIDIA GPU Computing Toolkit\CUDA\v10.2”

location and overwrite the files on that location.

### (Step-5) Add Environment Variables to the PATH in Windows

1. Open Run using (Win + R) and type sysdm.cpl and press Enter
2. Under System Properties, please select the Tab Advanced.
3. In Environment Variables go to System variables
4. Click on Add and save the below path,
5. Click ok and Save it.

> Variable name = CUDA_PATH

> Variable value = C:\Program Files\NVIDIA GPU Computing Toolkit\CUDA\v10.0

### (Step-6) Install TensorFlow & Keras

Open command prompt and type in,

```shell
pip install tensorflow-gpu
```

After successful installation try running this below program to verify its successful setup.

```python
import tensorflow as tf
# Device Name
print('Device Name: '+tf.test.gpu_device_name()
# Version-check
print('Version: '+tf.__version__)
# CUDA Support
print('CUDA Support: '+str(tf.test.is_built_with_cuda()))
```

![tf_setup]({{"/assets/img/tf_setup.png"| absolute_url}}){: width="700" height="400" }
_cuda tf_setup_

If you face any library missing issue then kindly download the below zip extract it and paste it over

<https://drive.google.com/file/d/10kKz9YRRmTtMj4vZHTt8fNrrrbgD2ooU/view?usp=sharing>

``` commandprompt
C:\Windows\System32
```

In case u need packages and setup directly, then you can refer my Github Repo

<https://github.com/rexdivakar/Deep-Learning-Setup>

Congratulations! 😉 You have successfully created an environment for using TensorFlow, Keras (with Tensorflow backend) over GPU on Windows!
