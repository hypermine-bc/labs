---
title: "Digital Identity: Past; Present; Future"
date: 2020-04-19T18:25:30+05:30
draft: false
categories: ["authentication", "blockchain"]
tags: ["SSI", "digital identity", "DID", "authentication", "centralised", "federated", "user-centric"]
authors:
  [vishwas,likitha]
---


Today, many countries across the globe are implementing digital identities to accelerate the adoption of their digital services.  While going through the research articles on digital identities, one of the questions raised is “why is the digital industry looking up for it?”. We'd like to share some experiences on this journey, let’s start with a basic question “what is an identity?” take a moment to think… and try to put the thoughts into a clear definition.

An identity can simply be told as the representation of who you claim to be and who you are. For example, you can be represented by your Name, Age, Profession, Address etc., these claims about you are called identities. As we know, to prove these identities, we use authorised documents like Passport, Aadhaar Card, Office/Student ID card etc., these are known as identity instruments. By now, you may guess how the Digital Identity can be defined; it's just an electronic assertion to yourself. 

## Is it really required, If so why?

To answer this, I would like to take you back to those days of new [internet](https://www.history.com/news/who-invented-the-internet) developments in the late 1960’s where the invention was to serve the purpose of secure and message sharing. As a result of limited and known users there was no layer of identity and authentication in the design of internet framework.
With the invention of the World Wide Web (WWW), the users made it a common platform for data sciences. Various sectors of society like health and finance have started using the internet for their services. This resulted in a very high [growth]( https://ourworldindata.org/internet) of internet usage across the world. Alongside, there was also impact on security that affected privacy, access and ownership of information online etc. 

<span style="display:block;text-align:center">![whyidentity](/images/ssi-intro/why-identity.png)</span>

How the transition was handled by the service providers? Any guesses !!

This transition has increased the volume as well as the complexity of the communications online. Privacy and security cannot be guaranteed in an increasingly borderless digital environment by just building walls around sensitive information especially in the sectors like finance and health care. At the same time, it has raised the expectations of the users while pressing the need for the digital identities for the service provider to be able to capture and restrict unauthorised users. The [World Economic Forum WEF](http://www3.weforum.org/docs/WEF_A_Blueprint_for_Digital_Identity.pdf) have given the key points that have pressed the need for digital identities.

 > As we make the transition as a society to conducting business online quickly and efficiently, we must not let our security and privacy standards slip through the cracks - Michelle Johnston.

That explains we have a strong requirement of digital identities. Let us now see, if digital identity management design addresses all of the security and privacy concerns.

## Journey of Digital Identity

Digital identity has evolved from the principle of **centralized identity** ever since the internet was launched. The name centralized itself explains that there exists a single authority who manages the digital identities. So, let's start with the first approach used for digital identity where, both the service provider(SP) and identity provider (IDP) had shared the same space. This means the users can directly register with the service provider as shown in the fig below. This is the traditional system of accessing the service with username and password; A *silo* approach. 

<span style="display:block;text-align:center">![whyidentity](/images/ssi-intro/silo.png)</span>

In practice, we can observe that this increases the cost of the application and also the users have to memorize multiple usernames/passwords which is tedious. So, It was transformed with a goal of low cost and better usability into a **centralised identity** mechanism. Apart from reducing the cost it also helps the service provider in solving the question “whom to trust?” by inducing the central authority called identity providers (IDP). To keep it clear, once the user submits their claims to the IDP, which verifies and issues the digital identity; using which the user can gain access to the required services offered by the service providers as shown in fig below.

<span style="display:block;text-align:center">![whyidentity](/images/ssi-intro/sso.png)</span>

Microsoft Passport, Google SSO are the best examples of this system. With this process of empowering a central IDP, do you feel that it solves all the issues of privacy and security? Nah!!. storing the identity parameters with a third party always creates a risk to privacy, limited user control and may lead to misuse of authority. we can also see that it extends its drawbacks to usability as it doesn’t support cross-organisation accessibility.

By learning the downsides of the centralised mechanism, the organisations came up with the hierarchical authority by tweaking the concept of centralized authorities but despite resolving existing concerns, this made the system more complex by balkanising the identities.

Now, with these issues it was more challenging to the SPs to balance the privacy and security concerns. So, they came up with a federated strategy; the second phase of a digital identity management system which is known as **federated digital identities**. The core idea behind this is to allow cross-organisational access within the trusted boundaries and maintaining the user's privacy in parallel as shown in fig below.

<span style="display:block;text-align:center">![whyidentity](/images/ssi-intro/f-sso.png)</span>

Though it achieved its goal of cross-organisational access, the control of identities is still not with the user. This breaks the privacy principle as the identity parameters are exposed to multiple organisations. Therefore this can only be used for specific applications like,

- Provide access to the users outside the traditional organisation perimeter after mergers and acquisitions. 
- Provide access to users who own a public organization ID, for example, ORCID ID, etc.

Till now we have observed that the root cause of digital identities not being able to provide privacy and security is the involvement of the intermediate authorities and the control of the identities!!! So, the organisations have come up with the next level of digital identity management system which aims to give the owner of the identities complete control over it.

The best example of this would be social logins, where you would see login with Gmail or Facebook while registering with a new application. Before you login to the application using your gmail identity, Google requests your consent before allowing the new application to access your data. Therefore, providing users with the right to restrict the exposure of their information. This type of digital identity system is known as **[user-centric digital identities]( http://citeseerx.ist.psu.edu/viewdoc/download?doi=10.1.1.408.9490&rep=rep1&type=pdf)**. This is the existing type of digital identity system. 

Still, the user identity details are stored at the identity provider. which means the risk of security and privacy raised with the centralised identity management system is not addressed. Hence, it suffers from many shortcomings like minimal exposure of credentials, elimination of central authority etc., that need to be fixed before it can be considered truly secure, privacy-friendly and usable.

> Somehow, security and privacy have become a distant dream !!☹️

The centralized identity providers have become regular and easy targets for hackers to obtain users' information, which resulted in the data breaches and identity theft. The research taken up in this objective has come up with a completely decentralised identity management system known as **Self-Sovereign Identity (SSI)**.

<span style="display:block;text-align:center">![whyidentity](/images/ssi-intro/timeline.png)

Now the question is, will it break the distant dream of the industry?
SSI aims at giving back the user full control on its identity.  This adds a layer of security and flexibility by allowing the identity holder to reveal only the necessary data for any given interaction.

Unlike other systems, it provides a trusted communication between the users and the organisations by eliminating the central authorities. At the same time, users and organizations can secure digitally signed claims related to them in a digital wallet instead of the central storages. A digital wallet resembles our physical wallet that holds a stack of identity documents. These claims stored are cryptographically signed to make them verifiable. 

Verifiable Claims issued, can be used wherever they are trusted. In such a sense, digital identity is as powerful as its claims, making it sufficiently secure for even high-trust industries such as banking, healthcare and government.

Nevertheless, user control is the essence of self-sovereign identity. To achieve this it follows a set of [guiding principles](https://medium.com/metadium/introduction-to-self-sovereign-identity-and-its-10-guiding-principles-97c1ba603872#8267). With all these components included SSI offers comparatively strong and secure while maintaining the privacy concerns.

In recent days, decentralised identity management organisations such as uPort, ShoCard, Sovring, [Hypersign](https://hypermine.in/hypersign/) etc, are implementing an SSI based identity management solutions. Hypersign is a simple-to-use authentication solution which is transparent and stores user data in a manner that is only accessible to the owner. It leverages the use of technologies like Blockchain and Public Key Cryptography to achieve SSI. More about Hypersign can be read [here](https://hypermine.in/hypersign/)

Maybe in my next blog, we will explore more into SSI and how blockchain can help to implement SSI. We will also take a closure look on [Hypersign protocol](https://github.com/hypermine-bc/hypersign) to understand the implementation details of SSI.

## References:

- http://www.lifewithalacrity.com/2016/04/the-path-to-self-soverereign-identity.html#dfref-1717
- https://www.pwc.com/it/it/publications/assets/docs/blockchain-and-digital-identity.pdf
- https://securityboulevard.com/2019/11/self-sovereign-identity-a-distant-dream-or-an-immediate-possibility/
- https://www.bundesblock.de/wp-content/uploads/2019/01/ssi-paper.pdf
