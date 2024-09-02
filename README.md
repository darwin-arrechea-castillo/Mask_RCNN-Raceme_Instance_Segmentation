# Mask R-CNN for Object Detection and Segmentation

Main repos on which this implementation was based:

* https://github.com/matterport/Mask_RCNN
* https://github.com/akTwelve/Mask_RCNN
* https://github.com/DavidReveloLuna/MaskRCNN_Video

This is a customized implementation of [Mask R-CNN](https://arxiv.org/abs/1703.06870) on Python 3, Keras, and TensorFlow. The model generates bounding boxes and segmentation masks for each instance of an object in the image. It's based on Feature Pyramid Network (FPN) and a ResNet101 or ResNet101 backbone. 

This project detects and count the total amount of racemes in tropical forages (Urochloa spp.) throught an web or a desktop based application

# Packages Installation Process
Some issues/challenges were resolved based mainly on the discussion thread: https://github.com/matterport/Mask_RCNN/issues/2886.
The speciic steps for implementing the framework are as follows:

```
1. Create the conda environment:
$ conda create -n maskrcnn3.8.0 python=3.8.0
2. Activate the environment:
$ conda activate maskrcnn3.8.0
3. (Optional) install ipykernel:
$ conda install ipykernel
4. (Optional) Create a kernel assigned to the environment:
$ python -m ipykernel install –user –name maskrcnn3.8.0 –display-name “maskrcnn3.8.0”
5. Install required packages:
$ pip install tensorflow==2.5.0 numpy==1.19.5 scipy==1.4.1 Pillow==8.2.0 cython==0.29.23 matplotlib==3.3.4 scikit-image==0.18.1 h5py==3.1.0 imgaug==0.4.0
6. Install tf GPU support (this is in case you don't have previous GPU support):
$ conda install -c conda-forge cudatoolkit=11.2 cudnn=8.1.0
7. Install adittional packages:
$ conda install ipython[all]==7.16.1
8. Install jupyter:
$ conda install jupyter==1.0.0
```
With the previous packages, everything should work, although sometimes there are additional issues related to missing or outdated  packages. If that happens, you should install/update the following packages:
```
9. Update module:
$ pip install --upgrade charset_normalizer==3.3.2
10. Install additional module:
$ pip install ipython_genutils==7.16.1
11. Clone repository:
$ git clone https://github.com/darwin-arrechea-castillo/Mask_RCNN-Raceme_Instance_Segmentation.git
12. Framework setup: Inside the cloned repo folder and within the conda environment, run:
$ python setup.py install 


```


