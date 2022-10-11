# AGB
This work is mainly based on the framework RepDistiller. And deploy our AGB method in this framework.

## Installation

This repo was tested with Ubuntu 16.04.1 LTS, Python3.6.10, PyTorch 1.8.1, and CUDA 11.1

## running

1. Fetch the pretrained teacehr models by:

    ```
    sh scripts/fetch_pretrained_teachers.sh
    ```
    which will download and save the models to `save/models`

2. Run distillation:

    We offered diffierent train mode for training:

    for example, for manual tuning train, you can use
    ```
    python train_student.py --path_t ./save/models/resnet32x4_vanilla/ckpt_epoch_240.pth --distill kd --model_s resnet8x4 --train_kind 0 -r 0.1 -a 0.9 -b 0 --trial 1
    ```

    or for AGB with angle train:
    ```
    python train_student.py --path_t ./save/models/resnet32x4_vanilla/ckpt_epoch_240.pth --distill kd --model_s resnet8x4 --train_kind 1 --warm_up 0 --angle 0.3
    ``` 
    

    or for AGB method without any weights:
    ```
    python train_student.py --path_t ./save/models/resnet32x4_vanilla/ckpt_epoch_240.pth --distill kd --model_s resnet8x4 --train_kind 1 --warm_up 1
    ```
    
