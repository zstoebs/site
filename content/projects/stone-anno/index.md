+++
title = "segmentation of kidney stones in endoscopic video feeds"
date = 2021-11-07T20:39:01-06:00
description = "Really good fast way to color inside the lines of a kidney stone."
summary = "StoneAnno is my first published first-authorship paper, **presenting at SPIE 2022**. With the long-term goal of fully-automated robotic endoscopic surgery, we built a dataset of endoscopic kidney stone removal videos and investigated U-Net, U-Net++, and DenseNet for the segmentation task. We found a U-Net++ model that consistently achieves **>0.9 Dice score**, with low loss, and produces realistic, convincing segmentations. Moving forward, I am implementing our model on hardware for deployment in ORs, as a part of my master's thesis, and I helped Dr. Kavoussi submit an **R21 grant** in October 2021."
categories = ["research"]
tags = ["ml", "seg", "vision", "python", "ai"]
draft = false
toc = true
[schema]
  type = "project"
[[copyright]]
  owner = "Zach Stoebner"
  date = "2021"
  license = "cc-by-nd-4.0"
[[resources]]
  src = "image/thumb.jpg"
  name = "thumbnail"
  title = "unet++ example heatmap output for kidney stone segmentation"
+++

**tl;dr** StoneAnno is my first published first-authorship paper, **presenting at SPIE 2022**. My advisor, Prof. Ipek Oguz, connected me and my friend, David Lu, with Dr. Nick Kavoussi at VUMC who wanted to bring surgical endoscopy out of the dark ages. With the long-term goal of fully-automated robotic endoscopic surgery, we built a dataset of endoscopic kidney stone removal videos and investigated U-Net, U-Net++, and DenseNet for the segmentation task. We found a U-Net++ model that consistently achieves **>0.9 Dice score**, with low loss, and produces realistic, convincing segmentations. Moving forward, I am implementing our model on hardware for deployment in ORs, as a part of my master's thesis, and I helped Dr. Kavoussi submit an **R21 grant** in October 2021. In the early stages of the project, we were also accepted for a poster presentation at the 2021 Engineering & Urology Society annual meeting. 

# Links

**The paper was accepted for SPIE 2022 Medical Imaging: Image Processing. Once the paper is digitally published on the SPIE archive, I will link it here. At that time, I expect to release the code as well.**

[comet.ml project page](https://www.comet.ml/zstoebs/stoneannotation/view/dEmnngcbMromlN06TZBvVj3qb)

# Abstract
Image segmentation has been increasingly applied in medical settings as the advent of AI has skyrocketed the application of deep learning. Urology, specifically, is one field of medicine that is primed for the adoption of a real-time image segmentation system with the aim of automating endoscopic stone treatment. In this project, we explored supervised deep learning models to annotate kidney stones in surgical endoscopic video feeds. In this paper, we describe how we built the dataset from the raw videos and how we developed a pipeline to automate as much of the process as possible. To maintain the project in the long term, we also began to engineer a utilities library to expedite data management at each endpoint of the model’s use. Most importantly, we adapted and analyzed three baseline deep learning models – U-Net, U-Net++, and DenseNet – to predict annotations on the frames of the endoscopic videos with the highest accuracy above 90%. To show clinical promise, we also confirmed that our best trained model can accurately annotate new videos at 30 frames per second. Our results demonstrate that the proposed method justifies continued development and study of image segmentation to annotate ureteroscopic video feeds.

# Results
<figure>
<img src="image/curves.jpg" alt="Dice and loss curves on validation data throughout training"/> 
<figcaption>Figure 1. A comparison of our best models’ Dice score (left) and BCE loss (right) from training. The scores were computed at each step where total steps = ⌈dataset length⌉ ∗ epochs. These curves display 20 epochs of training. Note that the batch size y-axis is scaled to the range of values. DenseNet had the highest and most variant BCE loss, yet its outlier values are relatively low compared to those in other binary classification tasks as BCE does not have an upper bound. </figcaption>
</figure>
<br>

<figure>
<img src="image/val_pred.jpg" alt="Example side-by-side comparison image of a validation image from the last epoch of training of our best U-Net++ model."/> 
<figcaption>Figure 2. Sample frame from the side-by-side video reconstruction of the input, ground truth, automated prediction with U-Net++, and heat map (left to right). The heat map is the raw probability output per pixel whereas the predicted segmentation is the pixels with probabilities ≥ 0.5. The model was able to compute this output at 30 FPS. </figcaption>
</figure>
<br>

<figure>
<img src="image/table.jpg" alt="summary of results between U-Net, U-Net++, and DenseNet for different scoring metrics" /> 
<figcaption> Table 1. Summary of the statistics gathered for each model. The reported value is the maximum value recorded from each baseline’s validation. The highest performances for each metric are denoted in bold. U-Net++ and U-Net claimed the highest scores, each in different metrics, except that they had the same average AUC for their ROC curves. However, the ROC curve is tighter for U-Net++. DenseNet had relatively poor performance.</figcaption>
</figure>
<br>

<figure>
<video src="image/unet++_vid34.mp4" height="224" width="672" controls></video>
<figcaption>Video 1. Example performance video of our best U-Net++ video on new data, not in train / val / test sets. The video shows a saline treatment and a stone that is being broken down with a laser. Detritus from the laser treatment is collecting to the left of the stone. This video is a typical example of what the model would see in a practical setting. </figcaption>
</figure>

# Future
This fall, I helped write an NIH R21 grant with Dr. Kavoussi and Dr. Oguz. Our two aims: 1. to develop a deep learning-based, automatic, real- time segmentation and tracking system during kidney stone surgery, and 2. to generate a real-time 3D navigational map of stone locations. Fingers crossed!!

Currently, I am working on a method to integrate our high-performing model with a contemporary endoscope. Next, I will design a visual GUI to extend the current view from the endoscope. We have shown that the model can compute results a little faster than 30 FPS so I expect that the system will be efficacious in practice. I'm planning on composing my work on this segmentation system into my master's thesis. 

# References
[1] Safi, S., Thiessen, T., and Schmailzl, K. J., “Acceptance and Resistance of New Digital Technologies in Medicine: Qualitative Study,” JMIR Res Protoc 7, e11072 (Dec 2018).

[2] Minaee, S., Boykov, Y. Y., Porikli, F., Plaza, A. J., Kehtarnavaz, N., and Terzopoulos, D., “Image Seg- mentation Using Deep Learning: A Survey,” IEEE Transactions on Pattern Analysis and Machine Intelli- gence 8828(c), 1–20 (2021).

[3] Nithya, A., Appathurai, A., Venkatadri, N., Ramji, D. R., and Anna Palagan, C., “Kidney disease detection and segmentation using artificial neural network and multi-kernel k-means clustering for ultrasound images,” Measurement: Journal of the International Measurement Confederation 149, 106952 (jan 2020).

[4] Viswanath, K. and Gunasundari, R., “Design and analysis performance of kidney stone detection from ultrasound image by level set segmentation and ANN classification,” in [2014 International Conference on Advances in Computing, Communications and Informatics (ICACCI)], IEEE (sep 2014).

[5] Jegou, S., Drozdzal, M., Vazquez, D., Romero, A., and Bengio, Y., “The One Hundred Layers Tiramisu: Fully Convolutional DenseNets for Semantic Segmentation,” IEEE CVPR Workshops , 1175–1183 (2017).

[6] Huang, G., Liu, Z., Van Der Maaten, L., and Weinberger, K. Q., “Densely connected convolutional networks,” IEEE CVPR 2017-Janua, 2261–2269 (2017).

[7] Otsu, N., “A Threshold Selection Method from Gray-level Histograms,” IEEE Transactions on Systems, Man and Cybernetics 9(1), 62–66 (1979).

[8] He, K., Zhang, X., Ren, S., and Sun, J., “Deep residual learning for image recognition,” IEEE CVPR 2016- Decem, 770–778 (2016).

[9] Sørensen, T., “A method of establishing groups of equal amplitude in plant sociology based on similarity of species and its application to analyses of the vegetation on danish commons”,” Kongelige Danske Vidensk- abernes Selskab 5(4), 1–34 (1948).
