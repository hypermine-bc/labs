---
title: "Privacy Preserving Social Login Using Hypersign"
date: 2020-11-16T07:11:24+05:30
draft: false
categories: ["hypersign"]
tags: ["SSO", "social-login", "SSI"]
authors:
  - vishwas
---

## Introduction

Social logins like Facebook, Google are common Single Sign-On (SSO) mechanisms for authentication in websites (also called service providers) these days. The social login helps service providers to quickly onboard a user without requiring them to go through the registration process. This way, on one hand, the service providers can provide seamless onboarding to their user and on the other hand, the user need not to type his details like name, email, phone number, every time he avails a service from a new provider. Moreover, the user does not have to remember multiple usernames and passwords for each of these service providers but just one for social login. Apart from this, the service provider gets user data directly from the social login provider (or also called identity provider i.e. IDP) to build a user profile in their portal.

There are two major problems which have been seen in the social login authentication flow. Most of the social logins providers like Facebook, Google etc. still **rely on password-based authentication** and we all know the problems with passwords like password resetting, password hacks, password forgetting etc. 

The identity provider **stores data of millions and millions of users** and that can become a honeypot for many hackers. Moreover, the identity provider also has the ability to **misuse the userdata without the consent of the user** in many different ways like doing analytics or by selling them to third party etc. [The case of Facebook and Cambridge Analytica is not hidden from anyone](https://en.wikipedia.org/wiki/Facebook%E2%80%93Cambridge_Analytica_data_scandal) where millions of Facebook users' data was acquired without the individuals' consent by Cambridge Analytica, predominantly to be used for **political advertising**. Think about the kind of impact it can have in our lives, it does not just affect a service provider but can even participate in the decision to choose the government. It seems that this is not ending soon, later, Facebook had harvested the email contacts of 1.5 million users without their knowledge or consent when they opened their accounts. You can read the case study on this on [Forbes](https://www.forbes.com/sites/zakdoffman/2019/04/18/facebook-illegally-harvested-data-from-1-5m-users-as-it-leveraged-its-data-machine/?sh=799c73306a2e) and  [Business Insider](https://www.businessinsider.in/politics/facebook-is-asking-some-new-users-for-their-email-passwords-and-appears-to-be-harvesting-their-contacts-without-consent/articleshow/68697026.cms) magazines. This is a very serious problem for the user who is very much concerned about their data privacy and protection as they have to fully trust these IDPs on how they store and manage their data. 

Apart from that, the **social login providers can track**, what and all a user is doing which is scary-

> “Facebook would know if you are travelling using MakeMyTrip or buying something from Amazon”, 

and that becomes another privacy concern for the user.

Having said that, the social login is not being used in serious enterprises since it does not tell, the one who is using the credential (i.e. username and password) possesses it as the credential can be easily shared with peers. Which means it does answer the question of *What you know?* but does not to *What you have?* or *Who you are?*. Additionally, the service providers still have to add another layer of authentication based on Ont Time Password (OTP) for better security. But OTP itself deals with ...which we will discuss in details in some other blog post.

Lastly, the IDP system can be flooded with a huge number of verifications requests since social logins are used in most consumer-facing applications which usually have a large customer based. Now any of the problems related to authentication in social logins, costs the service providers (those who support social login) a user loss and hence loss in business. A user might not be able to use the service if he/she is not able to authenticate himself/herself to the IDP. Think, you have an e-commerce site where a user wants to log in to buy a product during festive sales. Due to some reason (say outage or any other verification problem) if the user is not able to log in, how much can it impact the user experience and hence the business?

## Problem Statement

To summarise there are two sides of it, from 

### End-user perspective 

* **Control**: The end-user do not have control of his data. Although, username and passwords are given but actual data resides with IDP which gives them the ability to misuse.
* **Consent**: These IDPs often do not take consent of the user before sharing their data. i.e. case of Cambridge Analytica.
* **Tracking**: IDP providers can even track where and what user is doing

### Service provider perspective:

* **High trust**:  The provider has to trust on IDP how they store and manage their users' data.
* **Too much dependency**: The provider has to be dependent on Issuer as the issuer needs to be online when a user trying to access the provider's system.

There has to be the end of these kinds of problem where these entities do not respect the privacy and protection of user data. Having said that, I also want to admit that not all identity providers are evil, they ask users information so that a user can avail seamless user experience, for example, no registration required every time a user access a new application. 

It is not that we can remove the IDP completely (that's what we had right? when we did not have SSO). The role of IPDs are crucial since they verify data and as a result, the service provider gets pre-verified data hence both SP and user need to go through the verification process again. But the question is;

> Can we provide seamless user experience but taking better security and privacy majors in mind? 

## Hypersign

Hypersign is a privacy-preserving protocol to protect user data and mitigate risks of data breaches. The protocol built using latest technological stacks like advance **Public Key Cryptography** and **Blockchain** to provide secure, scalable and tamperproof solutions to the end-user as well as the service provider. The Hypersign protocol works on the concept of **Issuance-verification paradigm** which can be fit into many different use cases. One such use case is identity and access management.

![img](/images/privacy-preserving-sso/hypersig.png)

Most of the concepts are self-explanatory in the above figure. Notice, the user directly shares his data (step 5) with the service providers, from the user-agent (such as mobile device), as opposed to earlier where IDP used to share that. This gives full control to the user about his data. Moreover, this data is verified by IDP (step 2) hence the provider can trust the data as long as he trusts the provider. Finally, data are cryptographically signed not just by the issuer but also by the provider (steps 2 and 4) that gives guarantee about the data authenticity and integrity to the provider. 

## Hypersign-Superhero integration for Single Sign-On

The Hypersign comes with its own mobile authenticator app, however, we wanted to prove that how easily the protocol can be implemented with existing solutions so that they can leverage the benefits of Hypersign protocol in their ecosystem without making many changes. Hence we integrated with [Superhero](https://superhero.com/).

### What is Superhero?

|  |  |
| :---: | ---: |
Superhero is a decentralised social networking web application built on top of [AeTernity](https://aeternity.com/) blockchain. In Superhero, a user can make posts and curate others post if they like using cryptocurrency. Think of Facebook on the blockchain with tipping feature instead of likes. Because Superhero is a decentralised application, it comes with Superhero mobile wallet where an end-user can store their private key use it to sign transactions on the blockchain when they curate any content.  | ![ss](/images/privacy-preserving-sso/wallet.png)

### Architecture

![img](/images/privacy-preserving-sso/sso-arch.png)

Let us understand the above architecture with the user journey below.

### User journey

- Once Hypersign is integrated, two new features get added to the Superhero wallet, profile and credentials. A user downloads the wallet and enters his details in the profile page. The `userData` goes to the Superhero server.

| Home page | Profile page |
| :---: | ---: |
![img](/images/privacy-preserving-sso/home-wallet.png) | ![img](/images/privacy-preserving-sso/profile-wallet.png)

- The Superhero server verifies the user-data, say by sending an email or sending OTP on phone depending on what data needed to be verified. In this step, Superhero server acts as **stateless server** - meaning it **does not store** the `user data`. Based on this data, the Superhero server issues a cryptographically signed document (called `SuperheroAuthCredential`) to the user via email. 
- The end-user downloads the `SuperheroAuthCredential` from his email into the mobile app via QR code scanning. Further, the end-user can view the credential detail in the app itself.

| Credential list page | Credential detail page |
| :---: | ---: |
![img](/images/privacy-preserving-sso/credlist-wallet.png) | ![img](/images/privacy-preserving-sso/credenital-wallet.png)

- Now, whenever the end-user wants to authenticate himself into a website, he can use this credential to be able to login into the website using QR code scanning mechanism. He can further use the same and different credential to login into more than one website hence using in SSO environment. Take a look at the figure below.

| Before login | After login |
| :---: | ---: |
![img](/images/privacy-preserving-sso/login.png) | ![img](/images/privacy-preserving-sso/on-success-login.png)  


## Key differentiator

![img](/images/privacy-preserving-sso/comparision.png)

## Conclusion

- We eliminated passwords, so no password related problems at all.
- User now being able to share the verified data directly to the service provider. Hence **privacy is protected**.
- The IDPs verifies user data and provide credential without storing any user information hence **data is protected** as the IDP system can not become a honey pot for hackers.
- The user still be able to log in even though the IDP system is down or not working as the issuer can verify the issued credentials on its own hence the system is **scalable**.
- No multi-factor authentication complexity is required because the private key in a wallet does answers the question of *What I have?*. Further, if biometric is implemented in the mobile app then it also answers the question *Who I am?*. Hence the system is **secured**.
- Finally, a user feels confident in using the authentication mechanism, hence the system is **trustworthy**.

