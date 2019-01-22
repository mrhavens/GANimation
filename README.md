<img src='http://www.albertpumarola.com/images/2018/GANimation/face1_cyc.gif' align="right" width=90>

# GANimation: Anatomically-aware Facial Animation from a Single Image
### [[Project]](http://www.albertpumarola.com/research/GANimation/index.html)[ [Paper]](https://arxiv.org/abs/1807.09251) 
Official implementation of [GANimation](http://www.albertpumarola.com/research/GANimation/index.html). In this work we introduce a novel GAN conditioning scheme based on Action Units (AU) annotations, which describe in a continuous manifold the anatomical facial movements defining a human expression. Our approach permits controlling the magnitude of activation of each AU and combine several of them. For more information please refer to the [paper](https://arxiv.org/abs/1807.09251).

This code was made public to share our research for the benefit of the scientific community. Do NOT use it for immoral purposes.

![GANimation](http://www.albertpumarola.com/images/2018/GANimation/teaser.png)

## Prerequisites
- Python 2.7
- Install PyTorch (version 0.3.1; Linux only), Torch Vision and dependencies from http://pytorch.org
- Install requirements.txt (```pip install -r requirements.txt```)

## Anaconda Install
(Linux only; below shown with CUDA 8, but should work with others; Python 2.7 version of PyTorch v0.3.1 unsupported on Windows)

- conda create -n GANimation python=2.7 anaconda
- conda activate GANimation
- conda install pytorch=0.3.1 torchvision cuda80 -c pytorch
- conda install -c menpo dlib
- pip install --no-dependencies face_recognition
- pip install numpy matplotlib tqdm opencv-contrib-python tensorboardX

## Anaconda TACC Maverick Install
module load cmake/3.7.1 gcc/4.9.3 cuda/8.0 cudnn/5.1
- conda create -n GANimation python=2.7 anaconda
- conda activate GANimation
- conda install pytorch=0.3.1 torchvision cuda80 -c pytorch
- conda install -c menpo dlib
- pip install --no-dependencies face_recognition
- pip install numpy matplotlib tqdm opencv-contrib-python tensorboardX

## TACC Maverick Install
module load cmake/3.7.1 gcc/4.9.3 cuda/8.0 cudnn/5.1 python/2.7.12
- virtualenv GANimation
- source GANimation/bin/activate
- pip install https://download.pytorch.org/whl/cu80/torch-0.3.1-cp27-cp27m-linux_x86_64.whl
- pip install torchvision
- pip install dlib (failed do to no C++11 detected in gcc 4.9.3)

## Data Preparation
The code requires a directory containing the following files:
- `imgs/`: folder with all image
- `aus_openface.pkl`: dictionary containing the images action units.
- `train_ids.csv`: file containing the images names to be used to train.
- `test_ids.csv`: file containing the images names to be used to test.

An example of this directory is shown in `sample_dataset/`.

To generate the `aus_openface.pkl` extract each image Action Units with [OpenFace](https://github.com/TadasBaltrusaitis/OpenFace/wiki/Action-Units) and store each output in a csv file the same name as the image. Then run:
```
python data/prepare_au_annotations.py
```

## Run
To train:
```
bash launch/run_train.sh
```
To test:
```
python test --input_path path/to/img
```

## Citation
If you use this code or ideas from the paper for your research, please cite our paper:
```
@inproceedings{pumarola2018ganimation,
    title={GANimation: Anatomically-aware Facial Animation from a Single Image},
    author={A. Pumarola and A. Agudo and A.M. Martinez and A. Sanfeliu and F. Moreno-Noguer},
    booktitle={Proceedings of the European Conference on Computer Vision (ECCV)},
    year={2018}
}
```
