## Switchable Whitening

### Paper

Xingang Pan, Xiaohang Zhan, Jianping Shi, Xiaoou Tang, Ping Luo. ["Switchable Whitening for Deep Representation Learning"](https://arxiv.org/abs/1904.09739), ICCV2019.  

### Introduction

* Switchable Whitening unifies various whitening and standardization techniques in a general form, and adaptively learns their importance ratios for different tasks.
* This repo is for ImageNet classification, we would release Syncronized SW for detection and segmentation later.

### Requirements

* python>=3.6
* pytorch>=1.0.1
* others

    ```sh
    pip install -r requirements.txt
    ```

### Results

Top1/Top5 error on the ImageNet validation set are reported.

| Model                     | BN    | SW (BW+IW)  |
| -------------------       | ------------------ | ------------------ |
| ResNet-50                |  23.58/7.00  |  22.07/6.04  |
| ResNet-101             | 22.48/6.23   | 20.87/5.54    |
| DenseNet-121          | 24.96/7.85    | 23.56/6.85    |
| DenseNet-169          | 24.02/7.06    | 22.48/6.29    |

### Before Start
1. Clone the repository  
    ```Shell
    git clone https://github.com/XingangPan/Switchable-Whitening.git
    ```

2. Download [ImageNet](http://image-net.org/download-images) dataset (if you need to test or train on ImageNet). You may follow the instruction at [fb.resnet.torch](https://github.com/facebook/fb.resnet.torch) to process the validation set.

### Training
1. Train with dataparallel
    ```Shell
    sh experiments/resnet50_sw/run.sh  # remember to modify --data to your ImageNet path
    ```
2. Distributed training based on [slurm](https://slurm.schedmd.com/)
    ```Shell
    sh experiments/resnet50_sw/run_slurm.sh ${PARTITION}
    ```

### Practical concerns

* Inspired by [IterativeNorm](https://arxiv.org/abs/1904.03441), SW is accelarative via Newton's iteration.
* For SW, 4x64 (GPU number x batchsize) performs slightly better than 8x32.

### TODO
1. Pretrained models and code of DenseNet would be released in November.
2. We would release Syncronized SW for detection and segmentation later.

### Citing SW
```  
@inproceedings{pan2018SW,  
  author = {Xingang Pan, Xiaohang Zhan, Jianping Shi, Xiaoou Tang, Ping Luo},  
  title = {Switchable Whitening for Deep Representation Learning},  
  booktitle = {ICCV},  
  year = {2019}  
}
```  