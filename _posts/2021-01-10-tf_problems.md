---
title: Common problems and solutions of TensorFlow GPU installation
author: rexdivakar
date: 2021-01-10 12:33:00 +0800
categories: [deeplearning, tensorflow_error]
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

When i first started using Tensorflow GPU setup, I often encounter problems. I have installed it several times and often encounter the same or similar problems. So I plan to record it and hope it can help others…

## Inconsistent Libraries

![gpu version]({{"/assets/img/gpu_ver.png"| absolute_url}}){: width="700" height="400" }
_gpu driver version_

Initially i used to install the TensorFlow with the improper versions of CUDA & Cudnn often leads me to several problems, even a slight mismatch in versions of libraries and binaries are a trouble some process to fix so i recommend everyone to follow the above chart and install the right versions on your machine.

## Microsoft Visual C + + 2015 redistributable update 3 is not installed

In order for the Tensorflow modules to work perfectly it needs run-time components of Visual C++ libraries. So download and install the below libraries in case u face issues.

<https://www.microsoft.com/en-us/download/details.aspx?id=52685>

## Updating Environment Path to Windows (Set your PATH)

After installation of CUDA and Cudnn libraries don’t forget to add its path to ensure that TensorFlow can find CUDA, you should go to the system environment and add them as mentioned below.

```shell
export PATH="/c/Program Files/NVIDIA GPU Computing Toolkit/CUDA/v9.0/bin:$PATH"
export PATH="/c/Program Files/NVIDIA GPU Computing Toolkit/CUDA/v9.0/extras/CUPTI/libx64:$PATH"
export PATH="/c/tools/cuda/bin:$PATH"
```

![sys_var]({{"/assets/img/sysvar.png"| absolute_url}}){: width="700" height="400" }
_system variables_

## Cudart64 dll Error

When running the tensorflow code, initially we get an error cudart64 which prevents GPU execution. I recommend you to extract the DDL script from zip and paste it to,
> C:\Windows\System32

<https://drive.google.com/file/d/10kKz9YRRmTtMj4vZHTt8fNrrrbgD2ooU/view>

## Test Tensorflow GPU installation

To verify successful installation of tensorflow, try running this in your machine and hope fully it completes without any errors.

```shell
import tensorflow as tf 
#Device Name
print('Device Name: '+tf.test.gpu_device_name())
# Version-check
print('Version: '+tf.__version__)
#CUDA Support
print('CUDA Support: '+str(tf.test.is_built_with_cuda()))
```