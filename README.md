
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
    <li><a href="#usage">Usage</a></li>
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
  
<!-- USAGE EXAMPLES -->
## Usage
* sklearn
  ```sh
  npm install npm@latest -g
  ```
* sklearn
  ```sh
  npm install npm@latest -g
  ```
* sklearn
  ```sh
  npm install npm@latest -g
  ```


Results and files etc

scripts
what they do;
some logical flow



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
