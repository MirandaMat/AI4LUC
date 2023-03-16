# Artificial Intelligence for Land Use and Land Cover Classification (AI4LUC): Source Code

## Overview
The Cerrado biome is known mainly for the great biodiversity of flora, as well as for its agricultural potential. Its varied land use and land cover (LULC) are analyzed to understand social, economic, and environmental aspects. Despite the remote sensing (RS) community has been studying the Cerrado biome, several previous approaches do not use high spatial resolution image sets for classification (contextual and/or pixel-based) via deep learning (DL) techniques. It is also important that a significant number of images (patches) is used in order to have a representative sample of a large biome like Cerrado. Moreover, the procedure of manual labeling within the pixel-based classification (semantic segmentation) requires a lot of time, and thus providing an approach that can automatically generate the masks of the images (patches) is of paramount importance to support practical applications of the research produced by the academia. Supported by these motivations, this master dissertation aims at contributing to the task of pixel-based classification (semantic segmentation) of LULC via DL and a Cerrado dataset of satellite images. In order to meet this goal, a method called Artificial Intelligence for Land Use and Land Cover Classification (AI4LUC) is proposed. Firstly, a dataset regarding the Cerrado biome was created, called CerraData, amounting to unlabeled 2.5 million patches of 256 × 256 pixels. The patches were obtained from the Wide Panchromatic and Multispectral Camera (WPM) of the China-Brazil Earth Resources-4A (CBERS- 4A) satellite. These are images (patches) with a spatial resolution of 2 meters. From it, two different novel labeled versions were designed. Secondly, a new convolutional neural network (CNN), known as CerraNetv3, was created. CerraNetv3 and Google DeepLabv3plus are jointly considered to support the pixel-based classification task. A novel technique has also been proposed to automatically generate and label ref- erence masks, using CerraNetv3, in order to support DeepLabv3plus training for pixel-based classification. AI4LUC was compared to other derived approaches for semantic segmentation and contextual classification to analyze its feasibility. The results report that CerraNetv3 reached the highest score in the contextual classi- fication experiment, scoring with an F1-score of 0.9289. Regarding the automatic mask generation and labeling method, the overall score was 0.6738 and 0.7078 with the F1-score and Precision metrics. DeepLabv3plus scored 0.2805 and 0.2822 for the same metrics. The scores of the mask generation method are related to failures in mask generation in terms of segment quality, and consequently, cause mislabeling by the CerraNetv3 classifier. For this reason, DeepLabv3plus also performed poorly, since reference masks from the training set images were used for network training.

## AI4LUC
The Artificial Intelligence for Land Use and Land Cover Classification1 (AI4LUC) is a method based on the methodology of the DETER, TerraClass, and PRODES projects (INPE, 2019), in terms of image interpretation criteria such as context information and texture, to classify every single pixel of the scene. In line with this, AI4LUC is arranged in three hierarchies: modules, components, and functions, as presented in Figure below.

![image](set_page/img/pipeline.jpeg)

AI4LUC is a general method but an instance of a method was developed based on the Python language, the Conda environment, and using geoprocessing packages for remote sensing images, like GDAL and earthpy. Within the smart mask labeling module, for morphological transformations were used based on scikit-image and OpenCV. Regarding DL and DNNs, frameworks/APIs such as Tensorflow, Keras, scikit-learn, and PyTorch were used. The experiments were run on the [SDumont](https://sdumont.lncc.br/) supercomputer, using Bull Sequana X1120 computing nodes where each one has 2 x Intel Xeon Skylake 6252 CPU, 4 x NVIDIA Volta V100 GPUs, and 384 GB of RAM. For experiments that do not require more GPU capacity, a second computer was used with 8GB of RAM, an Apple M1 processor with an 8-core CPU, 7-core GPU, and 16-core Neural Engine. Further details regarding the method documentation, access [here](https://drive.google.com/file/d/1ez-55LoOPiyaCJdD-LrTJ2-UNBuEPODW/view?usp=share_link)


## How to use the code

To simply run the source code, do the following steps:

### Install the following requirements:
    
    ```
    python==3.9
    CUDA==11.6.1
    torch==1.12
    torchvision==0.13
    tensorflow
    tensorflow-metal (Apple M chips)
    scikit-learn
    scikit-image
    Pillow
    imageio
    imgaug
    rasterio
    numpy
    segmentation-models-pytorch
    tqdm
    ```

### Data Engineering module

### Contextual Classification training module

### Smart mask labeling module

### Pixel-based classification module
To employ DeepLabv3plus and U-Net trained weights you need a Apple M chip. 

### Application module


## Acknowledgments

This research was developed within the [**IDeepS**](https://github.com/vsantjr/IDeepS) project which is supported by the Brazilian LNCC/MCTI via resources of the [SDumont supercomputer](http://sdumont.lncc.br). This research was also supported by the Brazilian agencies CAPES. 

## Reference
