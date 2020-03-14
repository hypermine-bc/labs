---
title: "A quick introduction to Biometrics"
date: 2020-03-14T12:16:05+05:30
draft: true
---



 

<!-- toc -->
- [Introduction](#Introduction)
- [What is Biometrics](#What-is-Biometrics)
- [Types of Biometrics](#Types-of-Biometrics)
- [Fingerprint](#Fingerprint)
  * [How does fingerprint works](#How-does-fingerprint-works)
    + [Enrollement](#Enrollement)
    + [Verification](#Verification)
- [References](#References)



## Introduction



## What is Biometrics




## Types of Biometrics

- Facial characteristics
- Fingerprints
- Hand geometry
- Retinal pattern
- Iris pattern
- Signature
- Voice


In this blog we will only focus on _Fingerprints_.

## Fingerprint

Human fingertips are fully formed at about seven months of fetus developement and ridge configurations which form distinctive patterns. Good thing about these patterns are, when fully developed, they do not change throughtout the life of an individual. Print  of  these  patterns  is  known  as fingerprints


A bit of history here:

- Fingerprinting  first created  by a  British  surgeon called, [Dr. Henry Faulds](https://en.wikipedia.org/wiki/Henry_Faulds)
- In late nineteenth century Sir Francis Galton discovered some of the points or characteristics from which fingerprints can be identified. Hence the term “Fingerprint identification” is founded by the Galton points for the science technology.
- Fingerprint identification began its transition to automation in the late 1960.
- In 1969, the Federal Bureau  of  Investigation  (FBI)  developed  a  system  to  automate  fingerprint identification. 
- This  is  first  used  for  manual  process  and  then  it  is  connected  to National Bureau  of Standards  (NBS) known as  National Institute  of Standards  and Technology  (NIST)
- In  the  early  1990's,  NIST  began  developing  a  system  to  enable  the  electronic exchange  of  fingerprint  records and  images  by law  enforcement  agencies. 
- 

### How does fingerprint works?

One  of  the  most  important  tasks  considering  an automatic  fingerprint  recognition system is the  *minutiae biometric pattern extraction* from the  captured image  of the fingerprint 


The  capture device  returns an  image, usually  with 256 grey-levels, which  consists  of  dark  (ridges)  and  bright  (valleys)  lines.  The  most  widespread fingerprint matching approach relies  on  the uniqueness of a fingerprint’s  prominent singular  points  known  as  minutiae.  These  minutiae  are  represented  either  by bifurcation or  termination of  ridges
     
## Enrollement



### Verification

Basic fingerprint image consists of ridges, valleys, cores, deltas, pores etc as shown in Fig.  The  ridge  endings  and  ridge  bifurication's  are  used  for  comparing  two fingerprints with each other, denoted minutiae based matching.

![s](/images/intro-to-biometric/bifurcation&termination.png)

Fig. 2.5b illustrates ridge ending and ridge bifurcation which plays a vital role in fingerprint detection known as real minutiae. These ridge ending and ridge  bifurcation  do  not  change  over  time,  therefore  well  suited  for  fingerprint matching. Fingerprint usually consists of 40 to 100 minutiae points. Minutiae location is represented  by a  coordinate location  of the  fingerprint image.  Different systems represents minutiae location differently. 


#### Prepocessing and Post processing

Minutiae from  the fingerprint  image can be  extracted directly from  the fingerprint. However the extraction process is difficult and not accurate due to noise present in the fingerprint  image.  Also  the  intensity  of  the  line  pattern  may  differ  between fingerprints.  Due to  these  reasons  the extracted  minutiae  from  the fingerprint may contain both real   and false minutiae.



**Pre-processing** 

Pre-processing operation is used for enhancing the contrast of the fingerprint image. Quality of the acquired fingerprint depends on the condition of the finger and  sensor used. So pre-processing  operation  should  be  performed  before extracting  the  minutiae  from  the  fingerprint.

Techniques used:
- Quality  of  the  image  can  also  be  increased  by  using  the  filters. Low  pass  filter decrease the  noise from  the image,  band pass filter  decrease undesired  noise from orientations which helps in preserving true ridges
- Fingerprint enhancement using Fourier Transform 
- Fingerprint enhancement using Histogram Equalization  (Histogram Equalization is a computer image processing technique used to improve contrast in images.)


#### Minutiae Extraction

Minutiae extraction of the fingerprint is performed by using the algorithm developed by  NIST. 

![as](/images/intro-to-biometric/processingStepsExtraction.png)


- Image maps are generated from the input fingerprint
- Image binarization is performed and the minutiae are detected from the 
binarized fingerprint image.
- Removal of false minutiae from the fingerprint


**Post-processing**

Minutiae extracted from the fingerprint consist of real and false minutiae. The number of  falsely detected  minutiae depends  upon the  quality of the fingerprint. These false minutiae much be filtered to remove as many false minutiae   as possible without removing real minutiae.


#### Minutiae Matching



- genuine match : matching is from same person
- imposter matching : matching is from different persons
- Fingerprint matching techniques
    - Correlation-based matching
    - Minutiae-based matching : performed using BOZORTH3 algorithm
    - Ridge feature-based matching


**BOZORTH3**

Minutiae-based matching : performed using BOZORTH3 algorithm
This algorithm generates a  score based  on pairing  minutiae of  the fingerprints.   BOZORTH3 is an algorithm and utility that matches two minutiae patterns with each other and produces a match score. 

Matching between the fingerprint can be   
- one-to-one verification 
- one-to-many identification. 

Bozorth algorithm includes three steps for fingerprint matching

1. Construction of Intra-Fingerprint Minutiae Comparison Tables
2. Construction of Inter-Fingerprint Compatibility Table
3. Traverse Inter-Fingerprint Compatibility Table constructed in second step



![s](/images/intro-to-biometric/bozorth-algo.png)


- First minutiae tables are constructed for both probe and
gallery fingerprint as shown in fig below. In  the table  X,Y represents the  coordinates of each minutiae,  T represents orientation  and  D represents  the  minutiae  quality.  These  tables  containing  all minutiae parameters   are then passed to the minutiae matcher for generating the scores.    S(P1,P2)  represents  scores  obtained  from  genuine  matach  where P1 and P2 are the fingerprints from same person. S(G1, G2) represents scores obtained from imposter  matach  where G1 and G2 are  the fingerprints  from different  persons. As larger the matching score, the fingerprints are more likely from the same person.


## References

- [Biometrics Data Security Techniques for Portable Mobile Devices](https://link.springer.com/article/10.1007/s41403-017-0026-8)
- [Implementation and evaluation of NIST Biometric Image Software for fingerprint recognition](https://www.researchgate.net/publication/224226922_Implementation_and_evaluation_of_NIST_Biometric_Image_Software_for_fingerprint_recognition)
