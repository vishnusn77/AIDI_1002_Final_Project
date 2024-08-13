
# AIDI 1002 - FINAL PROJECT
# YOLO V4 OBJECT DETECTION
# TEAM:
* VISHNU SREEKUMARAN NAIR
* ANUSREE AMBIKA VISWANATHAN

This repository contains the implementation of the YOLOv4 object detection model, adapted and tested on the Pascal VOC 2007 dataset. The goal of this project is to evaluate the generalization capability of YOLOv4 on a dataset different from its original training set, COCO.

## Installation

### Prerequisites
Ensure you have the following installed:
- CUDA (for GPU support)
- cuDNN (for CUDA)
- OpenCV
- Visual Studio Code (or another IDE)
- CMake

### Steps
1. Clone the repository:
   ```bash
   git clone https://github.com/yourusername/darknet-modified.git
   cd darknet-modified

2. Compile Darknet with GPU and OpenCV support:
   ```bash
   cmake . -DCMAKE_BUILD_TYPE=Release -DCMAKE_CXX_STANDARD=11 -DCUDA_ARCH_NAME=Common -DCMAKE_CUDA_COMPILER=/usr/local/cuda/bin/nvcc
   make

## Dataset Preparation

1. Download the Pascal VOC 2007 dataset from the official Pascal VOC website.

2. Extract the dataset.

3. Convert the Pascal VOC annotations to YOLO format using the provided Python script:
   ```bash
   python voc_to_yolo.py

## Configuration

1. Modify the yolov4.cfg file:

Set classes=20 in each [yolo] layer.
Adjust the filters parameter in the preceding [convolutional] layer to 75.

2. Update the voc.data file:
   ```bash
    classes=20
    train=VOCdevkit/2007_train.txt
    valid=VOCdevkit/2007_val.txt
    names=VOCdevkit/voc.names
    backup=backup/

3. Ensure that the voc.names file contains the correct class names for the Pascal VOC dataset.

## Running the Model

1. Test the YOLOv4 model on an image from the Pascal VOC 2007 dataset:
   ```bash
   ./darknet detector test cfg/voc.data cfg/yolov4.cfg yolov4.weights VOCdevkit/VOC2007/JPEGImages/2007_000032.jpg

2. The output image with bounding boxes and labels will be saved in the predictions.jpg file.