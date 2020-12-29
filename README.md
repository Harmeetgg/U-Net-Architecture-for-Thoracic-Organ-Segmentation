
[![Contributors][contributors-shield]][contributors-url]
[![LinkedIn][linkedin-shield]][linkedin-url]



<!-- PROJECT LOGO -->
<br />
<p align="center">
  <a href="https://github.com/Karndeep-UCSD/ECE228_Project">
    <img src="images/logo.jpg" alt="Logo" width="280" height="254">
  </a>

  <h3 align="center">U-Net Architecture for Thoracic Organ Segmentation</h3>

  <p align="center">
    Annotation of Computed Tomography(CT) Scans is a tedious process where a radiologist manually combs through a volume of images marking individual pixel that contain an organ of interest. In this project, we seek to automate the process of segmenting organs in CT scans with deep learning. The U-Net architecture is implemented in tensorflow and trained to autonomously segment the heart, lungs, spine, and esophagus from a thoracic CT scans. 
  </p>
</p>



<!-- TABLE OF CONTENTS -->
<details open="open">
  <summary>Table of Contents</summary>
  <ol>
    <li><a href="#project-overview">Project Overview</a></li>
    <li><a href="#prerequisites">Prerequisites</a></li>
    <li><a href="#data-availability">Data Availability</a></li>
    <li><a href="#usage">Usage</a></li>
    <li><a href="#results">Results</a></li>
    <li><a href="#contact">Contact</a></li>
  </ol>
</details>



<!-- PROJECT OVERVIEW -->
## Project Overview
<p>
  This project demonstrates the use of machine learning approaches to auto-segment organs present in computed tomography (CT) scans of the human thoracic region. Segmenting organs such as the lung, spine, heart, and esophagus are important for early detection of organs-at-risk (OARs), however the conventional segmentation process is labor and time intensive (manual contouring of CT slices, usually taking 1-2 hours) and is subject to human error and bias. 
</p>

<br />
<p align="center">
  <img src="images/Unet_diagram.png" alt="Logo" width="660" height="440">
</p>

<p>  
  The U-Net is a Convolutional Network designed specifically for biomedical image segmentation. An image is input into the network. The network outputs a binary mask corresponding to the region of interest. The network architecture resembles that of an autoencoder, consisting of a contracting path, a bottleneck, and an expanding path. Skip connections connect blocks in the contractile path to corresponding layers in the expanding path, preserving spatial information. Dropout layers were included in the model to improve generalization. This is coupled to a binary cross entropy loss. For training, the Adam optimizer was used. Due to the kernel size used for each of the 23 convolutional layers, the model is only able to accurately predict information in the central two thirds of the image. This is due to a loss of information at the edges of the matrix with every convolution.
</p>

<p>
  This method was inspired by result of the Thoracic Auto-Segmentation Challenge organized at the 2017 Annual Meeting of American Association of Physicists on Medicine. (AAPM) Using the benchmark dataset and accuracy criteria provided by this challenge, we were able to reproduce the following organ segmentation accuracy with our model.
</p>

<br />
<p align="center">
  <img src="images/result_table.png" alt="Logo" width="374" height="174">
</p>


### Prerequisites
This repository uses function from the following Python libraries.

* tensorflow
* numpy
* sklearn
* skimage
* pydicom
* matplotlib
* os
* glob
* random

### Data Availability
<p>
  Data can be downloaded from: [DataSet]( https://wiki.cancerimagingarchive.net/display/Public/Lung+CT+Segmentation+Challenge+2017). Data is stored in following file structure:
</p>

<p align="center">
   NBIA_CT_Data > [Patient Data Folders] > A Single Folder > [Dicom folder, segmentation folder] > Dicom files
</p>
  
  
## Usage

1. Generate Labels
  ```sh
  Generate_Labels.py
  ```
  This function serves to preprocess our the data provided by the AAMP competition. Dicom segmentation files are taken and converted to 3D binary masks, one per organ, and saved as npy files. CT dicoms are preprocessed and saved volumetrically as .npy files.
  
2. Convert 3D volumes to set of 2D images for training
  ```sh
  3d_2d_conversion.ipynb
  ```
  This function takes the 3D npy files made by Generate_Labels.py and generates 512x512 2D slices. They are saved as individual .npy files. It first does this for the CT volumes, then for the individual organ segmentations. Organ slices are saved to an organ specific folder.
  
3. Training and Testing Model
  ```sh
  2D_UNet.ipynb
  ```
  This is the main notebook that loads CT slices, preprocesses data, fits, and tests the model. Data is loaded using a generator with a variable <i> batch_size, </i> which determines how many CT stacks can be injested with each call to the generator function. <i> Dice </i> and <i> Intersection Over Union(IOU) </i> are used as metrics while fitting the model. 

## Results
  
  <video width="320" height="240" controls>
    <source src="https://github.com/Karndeep-UCSD/ECE228_Project/tree/master/documentation/ECE228_Lung_12.mp4" type="video/mp4">
  </video>


<!-- CONTACT -->
## Contact

Karndeep Singh Rai-Bhatti - [Linkedin]( https://linkedin.com/in/karndeep-raibhatti) - karndeep.raibhatti@gmail.com

Project Link: [https://github.com/Karndeep-UCSD/ECE228_Project](https://github.com/Karndeep-UCSD/ECE228_Project)

other names here



<!-- MARKDOWN LINKS & IMAGES -->
<!-- https://www.markdownguide.org/basic-syntax/#reference-style-links -->
[contributors-shield]: https://img.shields.io/github/contributors/othneildrew/Best-README-Template.svg?style=for-the-badge
[contributors-url]: https://github.com/othneildrew/Best-README-Template/graphs/contributors
[linkedin-shield]: https://img.shields.io/badge/-LinkedIn-black.svg?style=for-the-badge&logo=linkedin&colorB=555
[linkedin-url]: https://linkedin.com/in/othneildrew
