# BrRacemeCounter: Mask R-CNN for Raceme Instance Segmentation

Main repos on which this implementation was based:

* https://github.com/matterport/Mask_RCNN
* https://github.com/akTwelve/Mask_RCNN
* https://github.com/DavidReveloLuna/MaskRCNN_Video

This is a customized implementation of [Mask R-CNN](https://arxiv.org/abs/1703.06870) on Python 3, Keras, and TensorFlow. The model generates bounding boxes and segmentation masks for each instance of an object in the image. It's based on Feature Pyramid Network (FPN) and a ResNet50 or ResNet101 backbone. 

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
$ pip install --upgrade charset_normalizer
10. Install additional module:
$ pip install ipython_genutils
11. Clone repository:
$ git clone https://github.com/darwin-arrechea-castillo/Mask_RCNN-Raceme_Instance_Segmentation.git
12. Framework setup: Inside the cloned repo folder and within the conda environment, run:
$ python setup.py install
!!! Note: If a change is made to the maskrcnn base files you have to do again the step #12 but first
    you must delete the file "mask_rcnn-2.1-py3.8.egg" located in the folder "...Lib/site-packages"
$ pip install git+https://github.com/philferriere/cocoapi.git#subdirectory=PythonAPI
```



If Git is not installed but a portable version is available (common in servers with usage restrictions), you can resolve this by temporarily adding the portable Git to the system path. Use the following command (example for CIAT processing server):
```
13. Portable Git:
$ $env:PATH += ";Z:\4.Scripts\DarwinArrechea\portables\portableGit\bin".
```

# C++ Compilers
Some packages require C++ compilers to be installed on your system. You can download them from [here](https://visualstudio.microsoft.com/es/visual-cpp-build-tools/). During installation, make sure to select the following components:
- **Workloads:**
  - **Desktop development with C++:** This will install the basic C++ tools required to compile Python packages that need compilation.
- **Individual Components:**
  - Make sure the following options are selected (there might be variations depending on the specific version of the installer, but try to choose the closest options)
      - **MSVC:** C++ compiler. select the latest available version.
      - **Windows 10 SDK:** If using windows 10. For other windows versions, select the SDK corresponding to your version.
      - **C++ CMake tools for windows:** Useful for packages using CMake
      - **C++ ATL for latest v142 build tools (x86 & x64):** Necessary for some compilations.

# Proxy Issues
Most tests were conducted on a server connected to the network via an Ethernet port. This network had restrictions on proxy access.

To install packages within the environment using pip without issues, it was necessary to configure the proxy (http://proxy.unicauca.edu.co with port:3128) to allow HTTPS traffic to https://pypi.org/. 

To use the proxy with pip, the command used was:
```
$ pip install --proxy http://proxy.unicauca.edu.co:3128 package_name
```

If problems persisted due to timeouts, a larger timeout value was set as follows:
```
$ pip install --proxy http://proxy.unicauca.edu.co:3128 --default-timeout=1000 package_name

* 1000 indicates the timeout in seconds.
```

For cloning repositories using Git, the proxy configuration was set with:
```
$ git config --global http.proxy http://proxy.unicauca.edu.co:3128
$ git config --global https.proxy http://proxy.unicauca.edu.co:3128

* This configures Git to use the proxy for all operations.
```

# Desktop App with tkinter
Initially, a simple desktop app was attempted using QT, but the idea was discarded due to compatibility issues between QT and the libraries required for deep learning. Ultimately, the decision was made to implement the app using Tkinter, which is lighter than QT and comes integrated with Python, eliminating compatibility problems.
- **Running the desktop app:**
```
1. Open the “command prompt” or the “anaconda powershell prompt.”
2. Activate the virtual environment:
$ conda activate maskrcnn3.8.0
3. Navigate to the script directory:
$ cd “D:\OneDrive - CGIAR\Documents\CIAT\UI-RacemeCounting\MaskRCNN-RacemeDetector”
4. Run the script:
$ python DesktopApp-BrRacemeCounter.py
```


# Web App with Gradio
The 2.2.15 gradio version is compatible with all the packages already installed.

* Note: During the installation try not to update any other packages.
```
$ pip install gradio==2.2.15
```
Note: You would need to have numpy==1.19.5 y pandas==1.1.5

# Author
Tropical Forages Program, CIAT.

# Aknowledgements
This work was partially funded by Accelerated Breeding Initiatiive of CGIAR.
