---
title: "Avatars May Use SSI In Metaverse To Prove Identity"
date: 2022-01-07T13:16:59+05:30
draft: false
categories: ["ssi", "blockchain"]
tags: ["SSI", "digital identity", "blockchain", "metaverse" ]
banner: "/images/metaverse-and-did/metaverse1.jpg" 
authors:
  - vishwas
---


![img](/images/metaverse-and-did/metaverse1.jpg)

Image Credit: https://www.verizon.com 

## Introduction

Metaverse has been in the news for quite some time now. Seems like the next "buzzword" after "blockchain" in the tech space. The tech got a surge especially after [Facebook decided to change its name to **Meta**](https://www.cnbc.com/2021/10/28/facebook-changes-company-name-to-meta.html). In this blog, we will understand what is Metaverse (a very basic intro) and its relationship with digital identities. The focus will be on explaining why decentralized digital identities are an important tool for Metaverse to replicate the real world.


## Metaverse 

So let's understand what is [Metaverse](https://en.wikipedia.org/wiki/Metaverse). 

In a very simple term, Metaverse is essentially a 3D virtual space on the internet that **replicates real-world interactions**. Pay closer attention to the phrase - **replicates real-world interactions** - I will come back to this in a minute. If you really wanna experience Metaverse (which is an old tech),  do check out [Second Life](https://en.wikipedia.org/wiki/Second_Life). Which is a virtual world (nothing but an application) where you can create your avatar and interact with other people as if like the way you interact with them in the real or physical world.  The term Metaverse has its origin in the 1992 science fiction novel [Snow Crash](https://en.wikipedia.org/wiki/Snow_Crash) 


## Replication of real-world interactions on a virtual world

Let us break down the above title. So we have two things here:

**Real World Interactions / experience**: 

Say, I and you decided to meet at the football match, I saw you and you saw me, we shake hands, I know who you are (since I can see you in front of me physically) and you know me who I am. We talked to each other. Not just that we share the same environment (or space), since we both are sitting at the same place. 

**Virtual World**: 

Now imagine the above interaction in an application on the internet without having to physically go to the match. 

You might be wondering what's special about this? Aren't we using applications like Google Meet, Zoom or other chat apps to interact virtually?

Well, true that. But in case of those platforms, we do not get to see each other in 3D. It's like we are just talking to some image. We can not touch or feel each other, the way we can do in the real world. Furthermore, we can not see/experience the space where we both are in those apps. 

I hope you get the point, I am trying to say here. Metaverse aims to give a platform where people can not just able to interact but also share the space and experience it. They can shop from a shopping mall, they can play, they can watch movies and so on exactly like the way they would do in the physical world. Imagine you enter into Amazon store and get to hold the product in your hand and then decide to buy and all of that happens without you having to physically go to any store, right from your laptop. 


## What's the problem?

What's the problem? Now that we know we want to replicate the experience of the real-world in the virtual world via Metaverse - but that brings us complexities of the real-world as well. One of such complexities is identities. Identifying people in the real world is still easy but identifying someone on the internet is way more difficult. The reason for that is, the internet was never built with an identity layer. Why? because the internet was supposed to be used in close proximity within a premise. Where everyone knows each other. So there were not any questions of identifying each other. Everyone knows everyone.

With the invention of the World Wide Web (WWW), it became a commonplace of interactions. Various sectors of society like health and finance have started using the internet for their services. This resulted in very high growth of internet usage across the world and the need for identity on the internet. and this identity problem was solved by issuing usernames and passwords to the internet users by the organizations/services.


## Passwords can not prove your identity

The problem with passwords is, they can be shared. For example, if you share your password with me, then I should be able to prove to the system that I am you. But if you look at the real or physical world I can not take away your identity no matter what (or at least in most cases). The same rationale applies to sharing your OTP or authentication link which came in your email. This reminds me of a famous cartoon published by  Peter Steiner in 1993: 


**On the Internet, nobody knows you're a dog!**

![img](https://upload.wikimedia.org/wikipedia/en/f/f8/Internet_dog.jpg)


I hope you got the point. So what is the right way to prove identity online? 

## So How Do We Identify Ourselves On The Internet?

**Biometric**

One of the ways to prove identity could be using biometric authentication. Where a user uses any of his / her biometric attributes like fingerprint or retina scan to prove identity. But this is not a viable solution because biometric capture needs a special device like a fingerprint scanner which is not been standardized across all devices. 

**Device authentication**

Another way to possibly solve this problem is, using device binding. Meaning, your device can produce a digital signature (exactly the way we sign using pen on paper in the real world) to the verifier (website) and the verifier can verify that signature and give access to the registered device. The reason this is a better approach than pure password is that difficulty in sharing the device with someone else. And one can not also make copies of the device as opposed to passwords which not only can be shared but also can be shared with multiple people at the same time. 

So in this case, the verifier does not verify the user's identity, rather it verifies the user's device and gives access to it. Now the next question is how can a device produce a signature? 

## How does the device generate signatures?

**Digital Signature**

A digital signature is very old and popular technology in the cryptography space where all parties have a pair of keys; `private key (sk)` -  which is kept private and a `public key (pk)` which can be shared with anyone. A prover can use the private key to generate the digital signature and the verifier can use the public key to verify the signature. 

In the device authentication flow, the device can store a private key somewhere safe in the device (there are various ways to do this, one of it [Trusted Execution Environment](https://en.wikipedia.org/wiki/Trusted_execution_environment)) and can be used to produce the digital signature. The digital signature can be then sent to a website or verifier, the verifier uses the devices' public key to verify the signature and let it access the system if everything works.  But the next problem is, how does the website/verifier get the device's public key? 

## How does the verifier get the public key? 

One way could be, the device can share the public key along with the digital signature at the time of authentication.  But in that case, if an attacker is listening to the call, he can simply replace the digital signature and the public key and hence possibly impersonate the system.

The other way could be, the verifier fetches the public key from any common database where the device would have stored his public key. This solution is perfectly fine as long as both parties trust the database provider. But when it comes to a decentralised ecosystem, the key is not to trust any central authority. Because what if the central authority changes the public key in the system or simply refuse to respond to the fetch request done by the verifier? 

## Blockchain came into the picture

You can see we reached a problem which is popularly known as the **trust problem** in a decentralised world. Hence, blockchain comes into the picture. The device can store the public key in a blockchain system which can not be tampered (intrinsic property of blockchain) or deleted. This is nothing but the concept of decentralised identity. In decentralised digital identity, we treat the blockchain as a registry of public-key identifiers in a specified format called [DID document](https://w3c-ccg.github.io/did-primer/). Here DID is referred to as **Decentralized Identifier**. And the process of authentication using DID is called `DID-Auth`.


I would not go into detail about SSI. May you can take a look at [this](https://labs.hypersign.id/posts/ssi-detail/) blog post for that.  


## Real World And Self Sovereign Identity

The Self Sovereign Identity (SSI) provides a framework to implement decentralised digital identity properly. One can use the concept of  `DID-Auth` to establish a secure connection between each other and can then uses the concept of **Verifiable Credential** to share any user data like name, email, phone number etc. The **Verifiable Credential** is exactly like your physical credentials like passport, voter id card, adhaar card etc but in digital form. The **verifiable credential** contains claims about the holder (or users) and the signature of the issuer who issued these claims. It can be shared with the verifier in a P2P fashion to avail any service from them. 

## Metaverse And Self Sovereign Identity

Now imagine Metaverse avatars sharing verifiable credentials to prove identity in the Metaverse. If you have read the novel, **Snow Crash**, the writer mentioned a term called, **Hypercard**. Quoting: 

> "It looks like a business card. The HyperCard is an avatar of sorts. It is used in the Metaverse to represent a chunk of data. It might be text, audio, video, a still image, or any other information that can be represented digitally. If Hiro reaches out and takes the HyperCard, then the data it represents will be transferred from this guy’s system into Hiro’s computer."

You can see where I am going. The verifiable credentials can be thought of as Hypercard and be used to prove the identity of the avatar in Metaverse.


## Conclusion


Hopefully, this blog might give you some perspective of how SSI and blockchain can be very useful for the adoption of Metaverse. Thank you for your time. See you in the next blog!





