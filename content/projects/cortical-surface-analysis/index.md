+++
title = "cortical surface analysis for Huntington's disease using linear-mixed models"
date = 2021-09-14T10:38:19-05:00
categories = ["research"]
tags = ["ml", "neuro", "matlab", "R", "stats"]
description = "Noobs think linear regression is easy... try LMMs."
summary = "Although it will be published after [StoneAnno](/projects/stone-anno), this shape analysis is my first completed research project and technically my first first-authorship, **going for submission at <i>Brain</i>**. I wrote code in R and MATLAB to fit LMMs to the cortical data from T1w MRI of HD patients and then performed statistical analyses on the results using SurfStat and random field theory. We found that, with a novel method for measuring gyrification, LGI uniquely detects changes in the insula."
draft = false
toc = true
[schema]
  type = "project"
[[copyright]]
  owner = "Zach Stoebner"
  date = "2021"
  license = "cc-by-nd-4.0"
[[resources]]
  src = "image/lgi.png"
  name = "thumbnail"
  title = "LGI omnibus results show strong correlation in the insula"
+++

**tl;dr** Although it will be published after [StoneAnno](/projects/stone-anno), this shape analysis is my first completed research project and technically my first first-authorship, **going for submission at <i>Brain</i>**. I wrote code in R and MATLAB to fit LMMs to the cortical data from T1w MRI of HD patients and then performed statistical analyses on the results using SurfStat and random field theory. We found that, with a novel method for measuring gyrification, **LGI uniquely detects changes in the insula.** Of note, I learned that complicated statistical anlayses are uniquely challenging, that I love LMMs and RFT, and that they are too esoteric in the current day -- let's make them more accessible!

# Links
**We are in the process of submitting our manuscript at <i>Brain</i>. As soon as it's published, I will link it here. At that time, I expect to release the code as well.**

# Background

[LMMs](https://stats.idre.ucla.edu/other/mult-pkg/introduction-to-linear-mixed-models/)

[random field theory](http://cda.psych.uiuc.edu/web_407_spring_2014/random_field_theory.pdf)

[LGI acquisition method](https://github.com/ilwoolyu/LocalGyrificationIndex)

# Abstract
The striatum has traditionally been the focus of Huntington’s disease research due to the resulting primary insult and its central role in motor symptoms. Beyond the striatum, evidence of cortical alterations caused by Huntington’s disease has surfaced; however, findings are not coherent between studies. A number of studies have used cortical thickness as the cortical metric of interest due to its establishment in the role of Huntington’s disease. In this study, we propose a more comprehensive approach to cortical morphology using cortical thickness (CT), sulcal depth (SD), and local gyrification index (LGI). Our results show consistency with prior findings in cortical thickness, including its limitations. Comparing between cortical thickness and local gyrification index underscores the complementary nature of these two measures; cortical thickness detects changes in the sensorimotor and posterior areas while local gyrification index identifies insular differences. Since the local gyrification index and cortical thickness measures detect changes in different regions, the two used in tandem could provide a clinically relevant measure of disease progression. Our findings suggest that differences in insular regions correspond to earlier neurodegeneration and may provide a complementary cortical measure for detection of subtle cortical changes due to Huntington’s disease. 

# Results
<i>These results are only the top-most. for all of the tables, charts, etc., please check out the paper once it is published.</i>

## CT
<figure>
<img src="image/ct.png" alt="CT omnibus results" /> 
<figcaption>Fig 1. Omnibus test results for CT showing the regions of significant contrast across all patients compared to controls. P-values were adjusted for FWER using random field theory (\alpha=0.01). </figcaption>
</figure>
<br>

## SD
<figure>
<img src="image/sd.png" alt="SD omnibus results" /> 
<figcaption>Fig 2. Omnibus test results for SD showing the regions of significant contrast across all patients compared to controls. P-values were adjusted for FWER using random field theory (\alpha=0.01). </figcaption>
</figure>
<br>

## LGI
<figure>
<img src="image/lgi.png" alt="CT omnibus results"/> 
<figcaption>Fig 3. Omnibus test results for LGI showing the regions of significant contrast across all patients compared to controls. P-values were adjusted for FWER using random field theory (\alpha=0.01). </figcaption>
</figure>
<br>

## Summary
<figure>
<img src="image/summary.jpg" alt="summary of results" /> 
<figcaption> Table 1. Summary of Regions with Significant Changes Per Feature. The percentage of the structure with significant changes are reported, in terms of the number of vertices. Regions are color-coded according to cooccurrence in the three features. Red = regional changes were detected by all three features. Yellow = regional changes were detected by two of the features. Blue = regional changes were detected by one of the features. </figcaption>
</figure>

# Takeaways
A main takeaway was learning the scientific process in action and, most importantly, learning to work with more experienced researchers. I wrote the code and performed all of the analysis that produced our results. However, I did not develop the awesome acquisition method that generated our LGI data nor the statistical theory behind the analysis. Throughout the project, I have relied heavily on the expertise of my co-authors -- all of whom have PhDs whereas I was an undergrad until recently. This first journey in research has been inspiring and indelible. I am beyond grateful for it!

# References
[1]    F. O. Walker, “Huntington’s disease,” Lancet, vol. 369, no. 9557, pp. 218–228, 2007, doi: 10.1016/S0140-6736(07)60111-1.

[2]    J. D. Long et al., “Genetic Modification of Huntington Disease Acts Early in the Prediagnosis Phase,” Am. J. Hum. Genet., vol. 103, no. 3, pp. 349–357, 2018, doi: 10.1016/j.ajhg.2018.07.017.

[3]    J. S. Paulsen et al., “Prediction of manifest Huntington disease with clinical and imaging measures : A 12-year prospective observational study,” vol. 13, no. 12, pp. 1193–1201, 2015, doi: 10.1016/S1474-4422(14)70238-8.Prediction.

[4]    M. E. Ehrlich, “Huntington’s Disease and the Striatal Medium Spiny Neuron: Cell-Autonomous and Non-Cell-Autonomous Mechanisms of Disease,” Neurotherapeutics, vol. 9, no. 2, pp. 270–284, 2012, doi: 10.1007/s13311-012-0112-2.

[5]    K. Hett, H. Johnson, P. Coupe, J. S. Paulsen, J. D. Long, and I. Oguz, “Tensor-Based Grading: A Novel Patch-Based Grading Approach for the Analysis of Deformation Fields in Huntington’s Disease,” Proc. - Int. Symp. Biomed. Imaging, vol. 2020-April, pp. 1091–1095, 2020, doi: 10.1109/ISBI45749.2020.9098692.

[6]    H. Li, H. Zhang, H. Johnson, J. Long, J. Paulsen, and I. Oguz, “Longitudinal subcortical segmentation with deep learning,” in SPIE Medical Imaging 2021: Image Processing, 2021, p. 115960D, doi: https://doi.org/10.1117/12.2582340.

[7]    H. Li et al., “Generalizing MRI subcortical segmentation to Neurodegeneration,” in MLCN Workshop, MICCAI, 2020, pp. 139–147, doi: https://doi.org/10.1007/978-3-030-66843-3_14.

[8]    H. Li, H. Zhang, H. Johnson, J. Long, J. Paulsen, and I. Oguz, “MRI Subcortical Segmentation In Neurodegeneration with Cascaded 3D CNNs,” in SPIE Medical Imaging 2021: Image Processing, 2021, p. 115960W, doi: https://doi.org/10.1117/12.2582005.

[9]    J. S. Paulsen et al., “Striatal and white matter predictors of estimated diagnosis for Huntington disease,” Brain Res. Bull., vol. 82, no. 3–4, pp. 201–207, 2010, doi: 10.1016/j.brainresbull.2010.04.003.

[10]    J. C. Hedreen, C. E. Peyser, S. E. Folstein, and C. A. Ross, “Neuronal loss in layers V and VI of cerebral cortex in Huntington’s disease,” Neurosci. Lett., vol. 133, no. 2, pp. 257–261, 1991, doi: 10.1016/0304-3940(91)90583-F.

[11]    H. D. Rosas et al., “Regional and progressive thinning of the cortical ribbon in Huntington’s disease,” Neurology, vol. 58, no. 5, pp. 695–701, 2002, doi: 10.1212/WNL.58.5.695.

[12]    P. C. Nopoulos et al., “Cerebral cortex structure in prodromal Huntington disease,” Neurobiol. Dis., vol. 40, no. 3, pp. 544–554, 2010, doi: 10.1016/j.nbd.2010.07.014.

[13]    S. J. Tabrizi et al., “Biological and clinical manifestations of Huntington’s disease in the longitudinal TRACK-HD study: cross-sectional analysis of baseline data Sarah,” vol. 8, no. 9, pp. 791–801, 2013, doi: 10.1016/S1474-4422(09)70170-X.Biological.

[14]    B. Fischl and A. M. Dale, “Measuring the thickness of the human cerebral cortex from magnetic resonance images,” Proc. Natl. Acad. Sci. U. S. A., vol. 97, no. 20, pp. 11050–11055, 2000, doi: 10.1073/pnas.200033797.

[15]    I. Lyu, H. Kang, N. D. Woodward, and B. A. Landman, “Sulcal depth-based cortical shape analysis in normal healthy control and schizophrenia groups,” vol. 1057402, no. March 2018, p. 1, 2018, doi: 10.1117/12.2293275.

[16]    I. Lyu, S. H. Kim, J. B. Girault, J. H. Gilmore, and M. A. Styner, “A cortical shape-adaptive approach to local gyrification index,” Med. Image Anal., vol. 48, pp. 244–258, 2018, doi: 10.1016/j.media.2018.06.009.

[17]    D. Wu, A. V. Faria, L. Younes, C. A. Ross, S. Mori, and M. I. Miller, “Whole-brain segmentation and change-point analysis of anatomical brain mri—application in premanifest huntington’s disease,” J. Vis. Exp., vol. 2018, no. 136, pp. 1–9, 2018, doi: 10.3791/57256.

[18]    X. Tan, C. A. Ross, M. I. Miller, and X. Tang, “CHANGEPOINT ANALYSIS OF PUTAMEN AND THALAMUS SUBREGIONS IN PREMANIFEST HUNTINGTON’S DISEASE,” in 2018 IEEE 15th International Symposium on Biomedical Imaging, 2018, no. ISBI, pp. 531–535, doi: 10.1109/ISBI.2018.8363632.

[19]    X. Tang et al., “Regional subcortical shape analysis in premanifest Huntington’s disease,” Hum. Brain Mapp., vol. 40, no. 5, pp. 1419–1433, 2019, doi: 10.1002/hbm.24456.

[20]    Y. Hong et al., “Genetic load determines atrophy in hand cortico-striatal pathways in presymptomatic Huntington’s disease,” Hum. Brain Mapp., vol. 39, no. 10, pp. 3871–3883, 2018, doi: 10.1002/hbm.24217.

[21]    J. S. Paulsen et al., “Detection of Huntington’s disease decades before diagnosis: The Predict-HD study,” J. Neurol. Neurosurg. Psychiatry, vol. 79, no. 8, pp. 874–880, 2008, doi: 10.1136/jnnp.2007.128728.

[22]    Y. Zhang, J. D. Long, J. A. Mills, J. H. Warner, W. Lu, and J. S. Paulsen, “Indexing disease progression at study entry with individuals at-risk for Huntington disease,” Am. J. Med. Genet. Part B Neuropsychiatr. Genet., vol. 156, no. 7, pp. 751–763, 2011, doi: 10.1002/ajmg.b.31232.

[23]    B. Fischl, “FreeSurfer,” Neuroimage, vol. 62, no. 2, pp. 774–781, 2012, doi: 10.1016/j.neuroimage.2012.01.021.FreeSurfer.

[24]    I. Lyu, H. Kang, N. D. Woodward, M. A. Styner, and B. A. Landman, “Hierarchical spherical deformation for cortical surface registration,” Med. Image Anal., vol. 57, pp. 72–88, 2019, doi: 10.1016/j.media.2019.06.013.

[25]    P. Parvathaneni et al., “Cortical Surface Parcellation Using Spherical Convolutional Neural Networks,” Lect. Notes Comput. Sci. (including Subser. Lect. Notes Artif. Intell. Lect. Notes Bioinformatics), vol. 11766 LNCS, pp. 501–509, 2019, doi: 10.1007/978-3-030-32248-9_56.

[26]    A. Klein et al., “Open labels: online feedback for a public resource of manually labeled brain images,” 16th Annu. Meet. Organ. Hum. Brain Mapping., p. 84358, 2010.

[27]    T. W. J. Moorhead et al., “Automated computation of the Gyrification Index in prefrontal lobes: Methods and comparison with manual implementation,” Neuroimage, vol. 31, no. 4, pp. 1560–1566, 2006, doi: 10.1016/j.neuroimage.2006.02.025.

[28]    M. Roberts, J. Hanaway, and D. K. Morest, Atlas of the Human Brain in Section, 2nd ed. Lea & Febiger, 1970.

[29]    I. Lyu, S. H. Kim, N. D. Woodward, M. A. Styner, and B. A. Landman, “TRACE: A Topological Graph Representation for Automatic Sulcal Curve Extraction,” IEEE Trans. Med. Imaging, vol. 37, no. 7, pp. 1653–1663, 2018, doi: 10.1109/TMI.2017.2787589.

[30]    A. Alin, “Multicollinearity,” Wiley Interdiscip. Rev. Comput. Stat., vol. 2, no. 3, pp. 370–374, 2010, doi: 10.1002/wics.84.

[31]    G. Verbeke and G. Molenberghs, Linear Mixed Models for Longitudinal Data, Print. New York: Spinger, 2000.

[32]    K. J. Worsley, M. Andermann, T. Koulis, D. MacDonald, and A. C. Evans, “Detecting changes in nonisotropic images,” Hum. Brain Mapp., vol. 8, no. 2–3, pp. 98–101, 1999, doi: 10.1002/(SICI)1097-0193(1999)8:2/3<98::AID-HBM5>3.0.CO;2-F.

[33]    J. E. Taylor and K. J. Worsley, “Detecting sparse signals in random fields, with an application to brain mapping,” J. Am. Stat. Assoc., vol. 102, no. 479, pp. 913–928, 2007, doi: 10.1198/016214507000000815.

[34]    D. Bates, M. Mächler, B. M. Bolker, and S. C. Walker, “Fitting linear mixed-effects models using lme4,” J. Stat. Softw., vol. 67, no. 1, 2015, doi: 10.18637/jss.v067.i01.

[35]    K. Worsley et al., “SurfStat: A Matlab toolbox for the statistical analysis of univariate and multivariate surface and volumetric data using linear mixed effects models and random field theory,” Neuroimage, vol. 47, p. S102, 2009, doi: 10.1016/s1053-8119(09)70882-1.

[36]    X. Han et al., “Reliability of MRI-derived measurements of human cerebral cortical thickness: The effects of field strength, scanner upgrade and manufacturer,” Neuroimage, vol. 32, no. 1, pp. 180–194, 2006, doi: 10.1016/j.neuroimage.2006.02.051.
