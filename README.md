
# Sticky Note Detector


This directory contains code implementation of custom trained SSD mobilebet v1 FPN model using my sticky-note images dataset i built to detect sticky-notes.

## Requirements
[![Python >= 3.6](https://img.shields.io/badge/Python-3.6-3776AB)](https://www.python.org/downloads/release/python-360/)
[![TensorFlow >= 2.2](https://img.shields.io/badge/TensorFlow-2.2-FF6F00?logo=tensorflow)](https://github.com/tensorflow/tensorflow/releases/tag/v2.2.0)
[![Protobuf Compiler >= 3.0](https://img.shields.io/badge/ProtoBuf%20Compiler-%3E3.0-brightgreen)](https://grpc.io/docs/protoc-installation/#install-using-a-package-manager)

## Table of Contents
- [Requirements](#requirements)
- [Table of Contents](#table-of-contents)
- [Installations and Dependencies](#installations-and-dependencies)
  * [Prepare The Dataset](#prepare-the-dataset)
  * [Training and Evaluation](#training-and-evaluation)
  * [Testing](#testing)
- [Resources](#resources)

## Installations and Dependencies
### Prepare The Dataset
The Images used (unlabeled and labeled ) are available [here](https://app.box.com/s/a0mz20bs694bh0q7gpsie40z04hdatza).<br> 
The images are collected manually and labeled using [**labelImg**](https://github.com/tzutalin/labelImg/blob/master/README.rst).<br>
- labelImg Dependencies: python, [PyQt5](https://www.riverbankcomputing.com/software/pyqt/download), [lxml](https://lxml.de/installation.html).<br>
- Open cmd and go to the labelImg directory:<br>

```
    pyrcc5 -o libs/resources.py resources.qrc

    python labelImg.py
```

### Training and Evaluation

Library               | version       | Download Link
-------------         | ------------- | -------------
Tensorflow GPU        |    2.5.0      | [pip install tensorflow-gpu](https://pypi.org/project/tensorflow-gpu/s)
NVIDIA CUDA Toolkit   |     11.4      | [official link](https://developer.nvidia.com/cuda-downloads)
NVIDIA cuDNN          |     11.4      | [official link](https://developer.nvidia.com/cudnn)

#### Files to use (for tensorflow 2 and above)
- To start training the model
```
models\research\object_detection> python model_main_tf2.py /
                                  --pipeline_config_path=path/pipeline.config /
                                  --model_dir= path/to/model /
                                  --alsologtostderr
```
- To convert the save and export the model 
```
models\research> python object_detection/exporter_main_v2.py /
                 --pipeline_config_path object_detection/path/pipeline.config /
                 --trained_checkpoint_dir=path/to/ckpt /
                 --output_directory=frozen_model
```
### Testing
The model was able to recognize the sticky note with high confidence.<br>
The testing procedure included both images that has sticky note/s and images does not have sticky note/s and it successfully detected all sticky note/s<br>
A sample of the testing results: <br><br>
![testing on image results](https://user-images.githubusercontent.com/54285485/127782305-9226d5ae-7b8f-43a3-90d7-c4e85fd79d5f.png)


## Resources
- Dat Tran's [raccoon_dataset](https://github.com/datitran/raccoon_dataset) : generate TFRecords files
- Tensorflow Object Detection API Documentation [tutorial](https://tensorflow-object-detection-api-tutorial.readthedocs.io/en/latest/)
- google, [unsplash](https://unsplash.com/), [pexels](https://www.pexels.com/) : used to building the sticky-note images dataset
