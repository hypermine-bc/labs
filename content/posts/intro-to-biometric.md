---
title: "A quick introduction of Biometrics"
date: 2020-03-14T12:16:05+05:30
draft: false
categories: ["authentication"]
tags: [biometric, fingerprints, "blockchain", "mobile"]
authors:
  - vishwas
---
  

In this blog our purpose is to take an in-depth look on how biometrics works. There are multiple types of Biometrics like, Facial characteristics, Fingerprints, Iris pattern etc. and they are fairly complex to undestand. So we will just focus on *Fingerprints*, to make biometric identification process simple and easy to underastand. We will start with definition of Biometric and its types. Then will talk about how fingerprint works, where we will talk about different stages of fingerprint verfication process. In the final stage of verification process, which is Matching we will only talk about Minutaie based matching using BOZORTH3 algorithm.

Finally, we will conclude the dicussion with how we can make use to this technology in our day to day life to identitify ourself to any service provider without the need of username and password.

## What is Biometrics

Biometrics are biological instruments that can be help to indentify individuals.  It is defined as, the automated methods of identifying or authenticating the identity of a living person based upon one or more intrinsic physical or behavioral traits. The term `biometrics` is derived from the Greek words `bio` (life) and `metrics` (to measure). The major use of Biometric is for identification and access control. It is also used to identify an individual in groups that are under surveillance. 

## Types of Biometrics

There are different forms of biometric technology. Some of them are the following.

- Facial characteristics
- Fingerprint
- Hand geometry
- Retinal pattern
- Iris pattern
- Signature
- Voice

Researchers claims the shape of an ear, the way someone sits and walks, unique body odors, the veins in one’s hands, and even facial contortions are other unique identifiers. In this blog we will only focus on _Fingerprint_.


## Fingerprint

Human fingertips are fully formed at about seven months of fetus developement and ridge configurations which form distinctive patterns. Good thing about these patterns are, when fully developed, they do not change throughtout the life of an individual. Print  of  these  patterns  is  known  as fingerprints.

A bit of history here:

- Fingerprinting  first created  by a  British  surgeon called, [Dr. Henry Faulds](https://en.wikipedia.org/wiki/Henry_Faulds). 
- In late nineteenth century Sir Francis Galton discovered some of the points or characteristics from which fingerprints can be identified. Hence the term “Fingerprint identification” is founded by the Galton points for the science technology.
- Fingerprint identification began its transition to automation in the late 1960.
- In 1969, the Federal Bureau  of  Investigation  (FBI)  developed  a  system  to  automate  fingerprint identification. 
- This  is  first  used  for  manual  process  and  then  it  is  connected  to National Bureau  of Standards  (NBS) known as  National Institute  of Standards  and Technology  (NIST) - an  organization  to  study  the  process  of  automating fingerprint  classification,  feature  extraction  and  matching. 
- In  the  early  1990's,  NIST  began  developing  a  system  to  enable  the  electronic exchange  of  fingerprint  records and  images  by law  enforcement  agencies. 


## How does fingerprint works?

In general there are two stages: **enrollment** and **verification** and/or identification. The enrollment phase creates an association between the user and the user’s biometric characteristics. In this phase the user's biometric is captures using fingerprint scanner in the form of an image. The  capture device  returns an  image, usually  with 256 grey-levels, which  consists  of  dark  (ridges)  and  bright  (valleys)  lines. Then certain unique and identifying features extracted from a user’s fingerprint are stored at the biometric database. Verification involves validating if a claimed user is the actual user. Identification is matching an unknown user from a list of potential candidates

There are two key challanges to address here:
- Scanning fingerprint cards and extracting minutiae (minutiae refers to specific plot points on a fingerprint) from each fingerprint. 
- Feature  extraction, comparing  and  matching list of  minutiae against  list of  large repositories of fingerprints.

## Minutiae


The  most  widespread fingerprint matching approach relies  on  the uniqueness of a fingerprint’s  prominent singular  points  known  as  minutiae.  These  minutiae  are  represented  either  by bifurcation or  termination of  ridges - look at red dots in the figure below.

Basic fingerprint image consists of ridges, valleys, cores, deltas, pores etc as shown in Fig.  The  ridge  endings  and  ridge  bifurication's  are  used  for  comparing  two fingerprints with each other, denoted minutiae based matching.

![s](/images/intro-to-biometric/bifurcation&termination.png)

The figure illustrates ridge ending and ridge bifurcation which plays a vital role in fingerprint detection known as real minutiae. These ridge ending and ridge  bifurcation  do  not  change  over  time,  therefore  well  suited  for  fingerprint matching. Fingerprint usually consists of 40 to 100 minutiae points.  Different systems represents minutiae location differently. 


## Verification

There are various approaches of automatic fingerprint matching that have been proposed  which  include minutiae  based  approaches, and  image  based  approaches. Minutia  based approaches  are  the most  popular  ones  being included  in  almost  all contemporary fingerprint identification and verification system. 

These are vairous stages of fingerprint verification process like shown in the figure below and can be broadly categoriese into the following:

- Fingureprint Capturing
- Pre-Processing
- Feature Extraction 
- Post-Processing
- Matching


The first stage  consists  of  fingerprint  sensing  which  has  been  historically  carried  out  by spreading the finger with ink and pressing it against a paper card and then scanned, resulting in a digital representation. This process is known as **off-line acquisition** and is  still  used  in  law  enforcement  applications.  Currently,  it  is  possible  to  acquire fingerprint  images  by  pressing  the  finger against  the  flat  surface  of  an electronic fingerprint sensor. This process is known as **online acquisition**. 

Acquired image may contain noise that is removed in pre-processing stage and minutiae are extracted from pre-processed image. 

Final  stage for  fingerprint matching  is performed  by passing minutiae patterns  of the fingerprint  to matcher.  This matcher  will produce a match score based on fingerprint matching.        


![s](/images/intro-to-biometric/ProcesssOfVerification.png)


### Pre-processing

Minutiae from  the fingerprint  image can be  extracted directly from  the fingerprint. However the extraction process is difficult and not accurate due to noise present in the fingerprint  image.  Also  the  intensity  of  the  line  pattern  may  differ  between fingerprints.  Due to  these  reasons  the extracted  minutiae  from  the fingerprint may contain both real   and false minutiae.


Pre-processing operation is used for enhancing the contrast of the fingerprint image. Quality of the acquired fingerprint depends on the condition of the finger and  sensor used. So pre-processing  operation  should  be  performed  before extracting  the  minutiae  from  the  fingerprint.

Techniques used:
- Quality  of  the  image  can  also  be  increased  by  using  the  filters. Low  pass  filter decrease the  noise from  the image,  band pass filter  decrease undesired  noise from orientations which helps in preserving true ridges
- Fingerprint enhancement using Fourier Transform 
- Fingerprint enhancement using Histogram Equalization  (Histogram Equalization is a computer image processing technique used to improve contrast in images.)


![as](/images/intro-to-biometric/OriginalVsEnhancedImg.png)

### Minutiae Extraction

Minutiae extraction of the fingerprint is performed by using the algorithm developed by NIST. 

![as](/images/intro-to-biometric/processingStepsExtraction.png)


- Image maps are generated from the input fingerprint. 
- Image binarization is performed and the minutiae are detected from the 
binarized fingerprint image. 
- Removal of false minutiae from the fingerprint happens. 
- Finally, output minutiae file is generated after accessing minutia quality.

### Post-processing

Minutiae extracted from the fingerprint consist of real and false minutiae. The number of  falsely detected  minutiae depends  upon the  quality of the fingerprint. These false minutiae much be filtered to remove as many false minutiae   as possible without removing real minutiae. The redundant minutiae in the fingerprint are of the form:

- Minutiae Points adjacent to each other 
- Minutiae near the border
- Spike, break, bridge, hole. 

![as](/images/intro-to-biometric/false&real.png)

Where, 

- a) Fingerprint image containing both false and real minutiae
- b) Fingerprint image containing real minutiae with "o" in green and false minutiae with "o" in red. 


### Matching

Fingerprint matching is a difficult approach due to quality variations of the fingerprint from the  same user  in time.  These  variations are  due to  changing skin  conditions, noise, errors caused during extraction. 

Types of matching are:

- genuine match : matching is from same person
- imposter matching : matching is from different persons

Some of the fingerprint matching techniques are:

- Correlation-based matching
- Minutiae-based matching
- Ridge feature-based matching

We will only talk about **Minutiae-based matching** since this the one very popular.

**Minutiae-based matching**

Minutiae-based matching performed using **BOZORTH3** algorithm. This algorithm generates a score based on pairing minutiae of the fingerprints. **BOZORTH3** is an algorithm and utility that matches two minutiae patterns with each other and produces a match score. 

Bozorth algorithm includes three steps for fingerprint matching

1. Construction of Intra-Fingerprint Minutiae Comparison Tables
2. Construction of Inter-Fingerprint Compatibility Table
3. Traverse Inter-Fingerprint Compatibility Table constructed in second step

![s](/images/intro-to-biometric/bozorth-algo.png)

First minutiae tables are constructed for both probe and gallery fingerprint as shown in fig below. In the table `X`,`Y` represents the  coordinates of each minutiae,  `T` represents orientation`Θ` and  `D` represents  the  minutiae  quality.  These  tables  containing  all minutiae parameters   are then passed to the minutiae matcher for generating the scores. `S(P1,P2)`  represents  scores  obtained  from  *genuine  match*  where `P1` and `P2` are the fingerprints from same person. `S(G1, G2)` represents scores obtained from *imposter  match*  where `G1` and `G2` are  the fingerprints  from different  persons. As larger the matching score, the fingerprints are more likely from the same person.

## Conclusion

The use of authentication builds a sense of trust for the end users, prevents access to a the network or service to intruders (i.e., external attack), and is necessary for holding a person accountable, in case the threats were a result of her actions (i.e., internal attack). Authentication along with the CIA Triad (confidentiality, integrity and availability) is one of the most important aspects of any cyber-physical system.

One of the simplest ways to implement user authentication is to use single-factor authentication. The widely adopted form of single-factor is to an username and password to log on to a website which tells `Something a user knows!`. It provides limited protection against attackers, hence MFA - Multifactor authentication came into picture which tells `Something the user has!`.  Multi-factor authentication using the first two factors definitely improves the quality of verification, but can still be vulnerable to attacks. If a malicious user steals both the password and smart card of a legitimate user, the attacker can gain access to the user’s account.

In this case, Biometrics seems to be a better option to proof user's identity since it talks about `Something the user is!`

## References

- [Biometrics Data Security Techniques for Portable Mobile Devices](https://link.springer.com/article/10.1007/s41403-017-0026-8)
- [Implementation and evaluation of NIST Biometric Image Software for fingerprint recognition](https://www.researchgate.net/publication/224226922_Implementation_and_evaluation_of_NIST_Biometric_Image_Software_for_fingerprint_recognition)
