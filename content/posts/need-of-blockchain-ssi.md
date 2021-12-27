---
title: "Why blockchain is important tool for SSI (The self sovereign identity) system?"
date: 2020-09-27T06:54:36+05:30
draft: false
categories: ["ssi", "blockchain"]
tags: ["SSI", "digital identity", "DID", "authentication", "centralised", "federated", "blockchain", "user-centric"]
banner: "/images/need-of-blockchain-ssi/issue-verification.png.png" 
authors:
  - vishwas
---

This blog can be considered as a follow-up blog (but not necessarily) of a series of blogs on digital identity. 

* [Digital Identity; Past, Present and Future](https://hypermineresearch.netlify.app/posts/ssi-intro/): Where we talked about how digital identity evolved over a period of time and where it is heading to - the SSI.
* [In depth introduction to Self Sovereign Identity (SSI)](https://hypermineresearch.netlify.app/posts/ssi-detail/): We took a deep dive into some of the core components of SSI to understand its terminologies and overall architecture. 

In this blog, we will explore why Blockchain is an important tool to build proper SSI system. Even though it is not necessary for SSI, its need becomes more and more evident when we think deep. The approach we will take to understand that need, is as follows:

* First we will look at one case study and try to articulate the problem statement.
* We will then try to come up with a simple model to solve the problem without blockchain.
* Then we will see what is the problem in that model.
* Finally, we will understand why Blockchain is important for SSI system and what it brings on the table of SSI.

>  The motivation for this blog I got from one of my talks I've given recently on *Digital Identity* where I was asked this question and I felt that my answer did not do justice to the audience because of the time crunch. So I would like to thank them for asking this question. 

## Case study: Flight Ticket Booking System

### User Story

*Vishwas*, a frequent traveller of *XYZ Airline* company requests a flight ticket from Chennai to Patna. Once, the ticket is issued, he goes to the airport to presents his ticket (with other credentials like a passport or voter id etc.) to the security personal - *David*, at the security check. David verifies the ticket **manually** and let him enter into the boarding area. Vishwas then presents his ticket to *Priya* - the flight attendant, who scans the barcode to verify the ticket and let him board the flight. 

**Actors**

* XYZ Airline - The airline company
* Vishwas - The passenger
* David - The security personal
* Priya - The flight attendant

**Observation**

The first thing to notice in this case study is, this system follows **Issuance-Verification paradigm**. Meaning, the use case essentially has three actors; an issuer (the airline company) who issues a ticket (can also be called credential), a holder or subject (the passenger) who requests the credential and holds it and a verifier (the security personal or the flight attendant) who verifies the credential. Take a look at the figure below.

![s](/images/need-of-blockchain-ssi/issue-verification.png.png)

Also, note that the <ins>verification system (security for example) does not belong to the same system where the credential was issued</ins>. For example, the security personnel does not belong to any airline company but belong on third party org, say government. Because of that, the problem is, either the verifier needs **issuers to be online** at the time of verification or the verifier has to verify the credential **manually** as there is no other option left for him. 

For sake of understanding we have two different kinds of verifier in this particular use case:

* The security personnel: from third party org
* The flight attendant:  from the same system

For flight attendant, this problem is not there since she belongs to the same system and she can verify the credential digitally, i.e. using bar code in this case. But for third-party verifier, it is a very important problem which may lead to a major security breach. I am sure you might have noticed how security personal verifies your boarding pass at the security check, he just takes a look on that and let you enter the boarding area. 


### Problem statement

> Since the verification system does not necessarily part of the system where credential was issued, the verifier has to verify the credential manually which leads to a major security breach or has to request the issuance system which may lead to overload the issuance system with a lot of verification request. 

### Solution

#### Model 1 - Digital Signature

We all know how [digital signature](https://en.wikipedia.org/wiki/Digital_signature) works. 

* Alice wants to send message to Bob, she will send the message, `m`, along with the digital signature, `sig` which he produced using her private key (`A_sk`) in a digital signature algorithm. 
* If Bob (the verifier) has to verify whether the message is coming from Alice (the sender) then he can verify the signature `sig` independently using the same digital signature algorithm which Alice had used to sign the message, without making a call to Alice as long as he has Alice's publickey (`A_pk`).  

Take a look at the fig below:

![s](/images/need-of-blockchain-ssi/dig-sig.png)

But then the obvious question is:

> How does Bob gets Alice’s public key?

Alice MUST not send her public key along with the same request otherwise the one (hacker) who is listening to the channel can replace his public key and signature which Bob will be able to verify. Which means there has to be a separate channel/medium to communicate the public key.

#### Model 2 - Digital Signature + Centralised Database

The simplest possible way to solve this problem is, having a common database which both of these parties have access to. All these actors (issuer and verifier) will pre-publish their public key, `A_pk`, `B_pk`  on this common database and whenever a verifier need, he can simply refer to this common DB to fetch the public key. There is no problem in making this database publicly available since public keys are meant to be shared and known to everyone. 

![s](/images/need-of-blockchain-ssi/dig-sig-db.png)

But then the next obvious question is:

> Who owns this database? and what is the guarantee that the public key stored in the DB is not been tampered? 


Now before we go any further let's stop here to think for a moment. If your business does not have a problem in trusting this centralised third party who owns the database, then you do not need any other solution. This solution is sufficient enough for your business. However, I will still leave you with one question;

> How would you ensure the liveliness of this database? This database server is going to get flooded now.

It looks like we circled back to the part of our problem statement. I understand this question does not make sense especially when we work with cloud service providers such as AWS, Azure etc. which promises decent uptime and better scalability options and when we think of just one use case from which requests are coming. But the verification requests can come from several different verifier systems and the load expected to grow exponentially. Think of, Public Key Infrastructure (PKI) based Addhar system, where a user can use his Addhar card in several different systems to avail different services, like tickets, e-bill, insurance etc. And all of these services has to make verification requests to the issuance system.


#### Model 3 - Digital Signature + Blockchain

Now instead of a centralised database, if we use Blockchain which can act as a global repository for public key identifiers (also called Decentralised Public Key Infrastructure (DPKI)) to verify the issuer, it can solve both our problems:

* **Trust**: We switched the trust from one centralised entity to a decentralised network of computers which is not owned by one single party. Hence the verifier can verify credentials without having to trust on a single entity.
* **Data persistence**: *Immutability* is an inherent property of blockchain, that makes us rely on the data which is entered on the chain and give us the confidence of tamper-proofed data.
* **Liveliness**: Blockchain is a network of computers run by so many people across the globe and bringing down the whole network is near to impossible even if we take worst-case scenario of a natural disaster. 
* **Independancy**: Since the blockchain becomes the common infra to hold publickeys, the verifier can fetch the issuer's key from the chain and can verify the credential on his own without making request to the issuance system.

Now, we can see our final model look something like this: 

![s](/images/need-of-blockchain-ssi/ssi-blockchain.png)


## Conclusion

I would like to conclude by saying, that blockchain not just plays an important role in shaping the future of digital identity and will eventually become a major tool to implement SSI ecosystem but also it reopened the discussion of identity again, giving people the hope to implement better identity layer which was missing on the internet. 



