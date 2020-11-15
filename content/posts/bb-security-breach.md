---
title: "Data breaches have become common in consumer-facing apps in India; How Hypersign can help?"
date: 2020-11-02T18:20:11+05:30
draft: false
categories: ["blockchain", "hypersign"]
tags: ["userdata", "privacy", "DID", "data-protection", "security"]
authors:
  - vishwas
---

## Abstract

The consumer-facing applications are more vulnerable for data breaches as they have a large customer base and they usually stored the user data in a central location. The consumer-facing app provider often has to choose between security and usability and they end up giving priority to the later one as usability become important growth factor. That allows a hacker to steal user data. In this blog, we are going to talk about problems, challenges which service providers face, especially with respect to user data protection and privacy, and what could be possible ways to solve that problem. In the end, we will introduce to Hypersign and analyze how Hypersign can reduce the risk of data breaches.

## Introduction 

Consumer-facing applications have comparatively more users than employee-facing application. In the consumer-facing application, trust becomes a very important factor in the growth as end-user always has choice/option to switch between providers. One of the important factor to gain the trust of a user is, data security. Providers mostly have to store user personal data to provide a seamless user experience as usability becomes equally important for the consumer-facing application. So, on the one hand, the providers has to deal with better security majors and on the other hand best user experience. The data set is huge for consumer-facing application and is stored centrally, these data set becomes honeypot for a hacker. That brings a challenge and responsibility for the provider that how do they store and manage the user's - personal data. 

A few days back we have seen a major [security breach](https://timesofindia.indiatimes.com/business/india-business/bigbasket-faces-potential-data-breach-details-of-2-cr-users-put-on-sale-on-dark-web/articleshow/79115354.cms) in one of the consumer-facing application called, BigBasket - which is an application to buy grocery online. The grocery e-commerce platform has faced a potential data breach which could have leaked details of its around 2 crore users, according to cyber intelligence firm Cyble. The data include emailId, password hashes, contact numbers, addresses, dob, location, IP address etc.

This is not the first hack of user data on the consumer-facing application. Previously, this year we have seen [Unacademy hack](https://www.theweek.in/news/sci-tech/2020/05/07/unacademy-hacked-data-of-20-mn-users-up-for-sale.html). Having said that, I believe it would be too early to give any judgment in case of Bigbast as the investigation still going on but certainly we have been seeing Indian companies ignoring user data protection and privacy to some extent. 

We wanted to investigate (or rather understand) the problem because of two reasons, one we at Hypermine works on these kinds of problem statements and we understand the concerns of those users who care about their data and the other, even I am the user of BigBasket so I believe my details have also got hacked. So now the hacker knows:

> Vishwas, a resident of Chennai whose phone number is 1234 and email is XYZ@examplemail.com and who is 27 years old, buys fruits every week!

I will come back to this statement in a bit.

## But why do they store data in the first place?

It is not that all providers are evil, they ask users to store their information so that a user can avail seamless user experience. End-user do not have to fill their information (say address) every time they shop. Furthermore, analytics can be performed on the data collected from the user. Providers do analytics to provide better or add on services to their customers. Moreover, data are also used for monitoring purposes so that in the event of any issue, the provider can investigate the issue to find the root cause and resolve it.

![mg](/images/bb-security-breach/why-do-store.png "Image credit: Google")


## Possible Solutions?

Now that we understand the problem statement and the reason why data is so important for providers to take from their customer, we can start thinking about how to solve the problem.

For sake of understanding let me re-define  the problem statement

> Providers have to store user personal data to provide better experience but at the same time personal data stored at centralised location becomes honeypot for hackers.

If we try to think of solutions we have two options:

### Do not store any data at all!

This option does not seem to be very realistic one as we miss seamless UX. The end-user will have to enter his details every time he uses service. Moreover, the service provider (SP) won’t be able to perform analytics and monitoring as there is no data stored.

### Encrypt all data!

Encrypting seems to be a better solution than the previous one but comes with a cost. Cryptography can slow down the system drastically, if not implemented properly. Analytics and Monitoring systems would then need the key to decrypt and perform operations - key management system needs to be implemented.

---

Both of these solutions seems to sit at extreme ends. We need to find a way somewhere in the middle to satisfy both worlds. We want to build a system where end-user should feel confident in using the system at the same time the provider should be able to perform all operations the way they were using earlier.

---

## Hypersign

Hypersign is a privacy-preserving protocol to protect user data and mitigate risks of data breaches. The protocol built using latest technological stacks like advance **Public Key Cryptography** and **Blockchain** to provide secure, scalable and tamperproof solutions to the end-user as well as the service provider.

Though the protocol works best with the decentralised environment, it can be also be deployed in a private setting easily in a centralised fashion. It helps:
    

![mg](/images/bb-security-breach/hs.png)


The Hypersign works on the concept of **Issuance-verification paradigm** which can be fit into many different use cases. The Issuance verification paradigm works with three stakeholders:

- **User**: Who has user data.
- **Issuer**: The one who verifies user data and issues credentials based on user data.
- **Verifier**: The one who verifies credentials, upon verification provides the service. 


### Legacy system

Let us understand how the current system works:

In the current system, the issuance system (in red in the fig below) holds the responsibility of issuing, holding and verifying the credentials (Note the size of the red circle). Giving responsibility to ONE system is a bad design for two reasons: 

- a) It causes scalability issue: The system can get flooded with a lot of verification requests which can cause the system to slow.
- b) Become honeypot for hackers: Keeping all data at one place becomes honeypot for the hacker, that what could happen in BigBasket case.

It may happen that the issuance and verification system can co-exist within the same organization. But this abstraction is made for clarity and scalability for consumer-facing application. 

Although the user gets username and passwords as authentication credentials users do not hold his actual data not even the critical ones like credit card details, address, phone number etc. because of that user data is being shared from issuance system (in red) to the service provider (in blue) and not from the user, take a look at the figure below.

![mg](/images/bb-security-breach/legacy.png)

### System with Hypersign

Let us see how the Hypersign protocol works:

The protocol __distributes responsibilities__ among all stakeholders (note the size of each item, they all have equal right and responsibility). User can give userdata to the issuer which issuer can verify and issue a cryptographically signed document (called credential) back to the user. The issuer does not necessarily have to store user data. In fact it even can act as a **simple stateless server**. Optionally, they can store data in encrypted form which can only to accessible to end-user. The end user will have ability to store this verifed credential locally (optionally on cloud) in a user agent (say mobile device) which only user has access to.
  
The user can now present this credential to the provider whenever required. The __data is now being shared in P2P__ fashion. The verifier can verify it cryptographically __without making a call to issuer__ by not flooding the issuance system with a lot of verification requests, hence scalable!

![mg](/images/bb-security-breach/hs-protocol.png)

### How does it help in data breaches?

To understand that, we first need to understand the types and characteristics of the dataset; which could be categorized into these: 

![mg](/images/bb-security-breach/dataset.png)

So now,

The **end-user** shares *highly* or *moderately* critical *verified* data like credit card details, email, phone number directly using a user-agent (i.e. mobile device) with the service provider peer to peer. Hence no critical data is stored for the hack. At the same time, a user still gets the same or better user experience because the user need not to type these details every time they avail service. Furthermore, the user can share partial information instead of sharing all.


On the other hand **service Providers** can store *least critical* data the way they were storing earlier but this time they will store these data with respect to specially design cryptographic identifier called DID. This DID do not reveals any information about a user. Can still use analytics and monitoring systems they way they were using earlier. A few critical data can also be stored but encrypted by a key which only user has access to. Further user can delegate the access if required.

#### What if the data now gets hacked...

So now instead of this information getting leaked:

> Vishwas, a resident of Chennai whose phone number is 1234 and email is XYZ@examplemail.com and who is 27 years old, buys fruits every week!

We end up leaking this:

> A person, who is an adult, buys a product every week!

As you can see, no critical information of end-users gets leaked hence they feel more trust and confident in using the system. The application-specific data like order list, product id and all might not be much of use for hackers.


## Conclusion

In the end, I have two points to make:

- Providers must feel responsible for how they store and manage user data.
- This calls for strong user data protection bill in India similar to what we have in Europe, the GDPR.