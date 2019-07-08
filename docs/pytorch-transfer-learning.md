<img src="https://github.com/dusty-nv/jetson-inference/raw/master/docs/images/deep-vision-header.jpg">
<p align="right"><sup><a href="detectnet-camera-2.md">Back</a> | <a href="pytorch-cat-dog.md">Next</a> | </sup><a href="../README.md#hello-ai-world"><sup>Contents</sup></a>
<br/>
<sup>Transfer Learning</sup></s></p>

# Transfer Learning with PyTorch

Transfer learning is a technique for re-training a DNN model on a new dataset, which takes less time than training a network from scratch.  With transfer learning, the weights of a pre-trained model are fine-tuned to classify a customized dataset.  In these examples, we'll be using the <a href="https://arxiv.org/abs/1512.03385">ResNet-18</a> network, although you can experiment with other networks too.

<p align="center"><a href="https://arxiv.org/abs/1512.03385"><img src="https://github.com/dusty-nv/jetson-inference/raw/python/docs/images/pytorch-resnet-18.png" width="600"></a></p>

Although training is typically performed on a PC, server, or cloud instance with discrete GPU(s) due to the often large datasets used and the associated computational demands, by using transfer learning we're able to re-train various networks onboard Jetson to get started with training our own models.  

<a href=https://pytorch.org/>PyTorch</a> is the machine learning framework that we'll be using, and example datasets along with training scripts are provided to use below, in addition to a camera-based tool for collecting and labelling your own data captured from a live camera feed.  

## Installing PyTorch

If you chose to install PyTorch when you [built the repo](building-repo-2.md), then 

## Mounting Swap

If you are using Jetson Nano, you should mount 4GB of swap space as training uses up a lot of extra memory.  Run these commands on Nano to create a swap file:

``` bash
sudo fallocate -l 4G /mnt/4GB.swap
sudo mkswap /mnt/4GB.swap
sudo swapon /mnt/4GB.swap
```

Then add the following line to the end of `/etc/fstab` to make the change persistent:

``` bash
/mnt/4GB.swap  none  swap  sw 0  0
```

Now your swap file will automatically be mounted after reboots.  To check the usage, run `swapon -s` or `sudo tegrastats`.
 
## Training Datasets

Below are step-by-step instructions to re-training models on some example datasets with transfer learning, in addition to collecting your own data to create your own customized models: 

* [Re-training on Cat/Dog Dataset](pytorch-cat-dog.md)
* [Re-training on PlantCLEF Dataset](pytorch-plants.md)
* [Collecting your own Datasets](pytorch-collect.md)

<p align="right">Next | <b><a href="pytorch-cat-dog.md">Re-training on the Cat/Dog Dataset</a></b>
<br/>
Back | <b><a href="detectnet-camera-2.md">Running the Live Camera Detection Demo</a></p>
</b><p align="center"><sup>© 2016-2019 NVIDIA | </sup><a href="../README.md#hello-ai-world"><sup>Table of Contents</sup></a></p>