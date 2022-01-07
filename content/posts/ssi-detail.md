---
title: "In depth introduction to Self Sovereign Identity (SSI)"
date: 2020-06-14T16:34:31+05:30
draft: false
categories: ["authentication", "blockchain"]
tags: ["SSI", "digital identity", "DID", "authentication", "centralised", "federated", "user-centric"]
banner: "/images/ssi-detail/Verifiable-credential-example.png"
authors:
  [vishwas,likitha]
---

In our [previous](https://labs.hypersign.id/posts/ssi-intro/) blog titles - Digital Identity: Past, Present and Future, we went through the journey of digital identity and tried understanding how it evolved over the period and where it is heading. We ended our discussion with the basic introduction of Self Sovereign Identity (SSI) system. If you have not read that blog, I encourage you to read that first before proceeding with this blog. In this blog, we will take a deeper dive into SSI and will try understanding how it works under the hood. We will also try to find out how SSI systems can be implemented, its components and the architecture.

![ssidifference](/images/ssi-detail/curr-vs-trad-model.png)

With the figure above, we can quickly recall the difference between the existing identity model and that of a decentralised digital identity called Self Sovereign Identity (SSI) from our previous discussion. Putting it simply, we can say the **user being the controller of identity** is what makes the SSI different from the current identity frameworks.

## What is SSI?

To understand it in a much simple way, let us see what is the problem with our current identity system; The possibility of losing our identity is a serious problem in the digital world.  Take a look at the previous two identity models, centralised and IDP models. Where someone else has control of the user's identity. For example, vloggers could lose their identities if YouTube closes their accounts. A common internet citizen like you and I could lose a big part of our life if Facebook revokes our credentials. 

![ssidifference](/images/ssi-detail/traditional-model.png)

As digital accounts become a major part of our identities, we need a paradigm that allows us to bring identity back under our control. And that's where SSI comes into the picture. Where the control is brought back to the end-user and all participants are the same (with equal power) in the ecosystems. See the figure below.

![ssidifference](/images/ssi-detail/ssi-diagram.png)

On the other hand the SSI has formed several misconceptions about its functionalities with the complex context of its name. Before knowing anything about the SSI, let us see what it is not;

## Myths of SSI

- Self-sovereign means self-attested.
- SSI attempts to reduce the government’s power over an identity owner.
- SSI creates a national or “universal ID” credential.
- SSI gives absolute control over identity.
- There’s a “main” issuer of credentials.
- There’s a built-in method of authenticating.
- The user-centric identity is the same as SSI.

Timothy Ruff, in his blog on [7 myths of the self-sovereign identity](https://medium.com/evernym/7-myths-of-self-sovereign-identity-67aea7416b1) has clarified each one of these myths. So SSI never aims to remove real-world identity issuers like the government out of the system. It is more like an **impression of our physical identities like Aadhaar cards or Passports into the digital world** where the user controls his identity once issued by the issuer.

**Manual verification process**

Recollect the plane boarding scenario to illustrate, where we use a physical identity (aadhar card) as proof of our identity to the security officer. The physical identity here gives you (a user) the full authority on how and where to use it despite being issued by the government (the issuer). At the other end, the officer verifies your passport without the need for the third party by validating the issuer’s seal. Here there is two part of the flow, *user holding his identity* and *verifier verifying user’s identity*. The first part seems to be reasonably correct since the user has full control of physical identity which he is holding either in his pocket or wallet. But the problem is with the verification, where the verifier does not necessarily connect to the issuer to verify it. The process is a completely manual and hence high chance of fault. We have heard of [many such cases](https://www.indiatoday.in/india/story/pakistan-isi-agents-caught-in-delhi-after-weeks-of-surveillance-1684128-2020-06-01), where fake aadhar cards being used in the country. The problem is more lengthy and time taking when the user is geographically far away from the verifier. We can see there is a need for a digital system here which is not just secure but also portable and not time taking.

**Need of digital system - The problem remains the same** 

Talking about verifying identity digitally, the current way of doing it is very vague. For example, if your bank asks you to send the id cards, you scan them and send it over email or other communication mediums. Even you send the digital copy of id card, the verifier still using manul process to verify the identity. In this case there is one more problem exists, which is, you are not only trusting on your bank to secure your id card but also on the medium (email company in this case) which you used to send it over.

## 10 Principles of SSI

- **Existence** — Users must have an independent existence.
- **Control** — Users must control their identities.
- **Access** — Users must have access to their data
- **Transparency** — Systems and algorithms must be transparent.
- **Persistence** — Identities must be long-lived.
- **Portability** — Information and services about identity must be transportable
- **Interoperability** — Identities should be as widely usable as possible.
- **Consent** — Users must agree to the use of their identity.
- **Minimisation** — Disclosure of claims must be minimised
- **Protection** — The rights of users must be protected

## Working of SSI

SSI consists of three different actors involved in its framework as shown in the figure below. The Holder or the user is the owner of the credentials, the issuer is the issuing authority of [verifiable credentials](https://www.w3.org/TR/vc-data-model/#dfn-verifiable-credentials) and the verifier is the one who verifies the credentials. The figure below explains the trust relation between the actors.

![ssidifference](/images/ssi-detail/Verifiable-credential.png)

Every use case that inherits the technique of Decentralised Identity (DID) introduced by SSI may have to follow the three simple steps given below.

- The user connects to the issuer and collects the verifiable credentials and stores them in their digital wallet. 
- The user establishes a secure connection (maybe by scanning QR code) with the verifier using the cryptographic keys. The private key is stored locally in the wallet and the public key is shared with the verifier.
- Finally, the user can select the verifiable credentials from the wallets as per the requirement and share it with the verifier to prove their identity. 

### Blockchain fits into infrastructure of SSI

A DID can be registered with any type of decentralized network—or even exchanged peer-to-peer. So why would someone choose to register a DID on a blockchain? What do blockchains provide that other types of electronic identifiers and addresses we have been using for decades—telephone numbers, domain names, email addresses—do not?

Let’s understand the problem with an example of TLS (or HTTPS); 

The Public key infrastructure (PKI) used in modern browsers relies on a small number (a few hundred) of certificate authorities (CAs) to be the roots of trust. The number is small so that your browser can easily manage them. The owner of a private key, such as a website, gives their public key to a CA who signs it with their own private key and issues a public key certificate. That’s what your browser is checking for each time you connect to a website that offers an encrypted HTTPS connection. You can see the flow in the following diagram; This is how you know you’re dealing with the site you think you are.

![ssidifference](/images/ssi-detail/Verifiable-credential-example.png)

If a CA makes a mistake on a digital certificate, or if their service goes down or has a security lapse, or if they raise their prices, or if they go out of business—the [whole system falls apart](www.slate.com/articles/technology/future_tense/2016/12/how_the_2011_hack_of_diginotar_changed_the_internet_s_infrastructure.html).

Blockchains being highly tamper-resistant transactional distributed databases that no single party controls. This means they can provide an authoritative source of data that many different peers can trust without any single peer being in control. From the standpoint of SSI—and specifically for registering and resolving the DIDs and public keys that enable digital wallets and digital agents to securely communicate and exchange verifiable credentials, Blockchain is most helpful since it solves a problem that has never had a solution in the history of cryptography: they are globally distributed databases that;

> Can serve as a source of truth for public keys (of Issuers) without being subject to single points of failure or attack. 

This is what provides the strong foundation needed for the ubiquitous adoption of the verifiable digital credentials at the heart of SSI.

## Basic building blocks of SSI

Now that we have understood the fundamentals of SSI, let’s go deeper and try to understand the architecture of SSI -  we will look at a layered diagram (called SSI stack) to understand that. But before that lets take a look at the four building blocks of SSI systems. 

![ssidifference](/images/ssi-detail/components.png)

### DID -  The Decentralised Digital Identifier 

A Decentralized Identifier (DID) is a new type of identifier that is globally unique, resolvable with high availability, and cryptographically verifiable. The DID are addresses on the DLT of those public keys of users. DID is associated with cryptographic materials such as public key and service endpoints and are used to establish secure communication channels. Also note that one user can have more than one DIDs. 
In short it fulfils 4 requirements of SSI system:

- **Permanent** - It never need to change
- **Resolvable** - You can look it up to get metadata
- **Cryptographically verifiable** - You can prove the ownership using cryptography
- **Decentralization** - No centralised registration authority is required.

**Different than UUIDs and URNs**

DIDs are different than [UUIDs](https://en.wikipedia.org/wiki/Universally_unique_identifier) or [URNs](https://en.wikipedia.org/wiki/Uniform_Resource_Name) in the sense that UUIDs are not globally resolvable and URNs - if resolvable - require a centralised registration authority. In addition neither UUIDs or URNs inherently address - the ability to cryptographically verify ownership of the identifier. DIDs are lifetime portable  digital identity which does not depend on any centralised authority.. Have a look at how at its design:

![ssidifference](/images/ssi-detail/did-design.png)

Example of DID of [Sovrin](https://sovrin.org/wp-content/uploads/Sovrin-Protocol-and-Token-White-Paper.pdf) SSI:

![ssidifference](/images/ssi-detail/did-ex.png)

DID infrastructure can be thought of as a global key-value database in which the database is all DID-compatible blockchains, distributed ledgers, or decentralized networks. In this virtual database, the key is a DID, and the value is a DID document.

![ssidifference](/images/ssi-detail/key-value.png)

#### DID Document

The purpose of the DID document is to describe the public keys, authentication protocols, and service endpoints necessary to bootstrap cryptographically-verifiable interactions with the identified entity. It includes six components:

- DID (for self descrption)
- Set of public keys (for verification)
- Set of auth methods (for authentication protocol)
- Set of service endpoint (for interaction)
- Timestamp (for audit histroy)
- Signature (for integrity)

Note: The service endpoints, enable further interactions with the DID controller. For instance, a DID can reference the location of associated personal data, which a requester would need to ask the DID controller for permission to access.

Example of a DID document:

![ssidifference](/images/ssi-detail/did-doc.png)

> Essentially, the DID Doc contains metadata for authenticating DID

### DKMS - Decentralised Key Management System

[DKMS](https://github.com/WebOfTrustInfo/rwot4-paris/blob/master/topics-and-advance-readings/dkms-decentralized-key-mgmt-system.md) deal with the question of:

> How a user will manage all those DIDs and private keys? And what will happen if they lose them?

DKMS is an emerging open standard for managing user’s DIDs and private keys. The foundation for DKMS is laid by the [DID specification](https://github.com/hyperledger/indy-sdk/blob/677a0439487a1b7ce64c2e62671ed3e0079cc11f/doc/design/005-dkms/DKMS%20Design%20and%20Architecture%20V3.md). It applies to wallets where the user stores his DIDs and private keys. The concept is to have a standard for developing wallets so that the user does not worry about security, privacy or vendor lock-in.

### DID Auth

DID Auth is a ceremony where an identity owner, with the help of various components such as web browsers, mobile devices, and other agents, proves to a relying party that they are in control of a DID. Essentially DID Auth is the protocol for authentication and authorization in SSI systems.  DID Auth includes the ability to establish mutually authenticated communication channels and to authenticate to web sites and applications. Authorization, Verifiable Credentials, and Capabilities are built on top of DID Auth. 

**Ways of authentication - One or Two way**

A successful DID Auth interaction may create the required conditions to allow the parties to exchange further data in a trustworthy way. DID Auth may be a one-way interaction where party A proves control of a DIDA to party B, or a two-way interaction where mutual proof of control of DIDs is achieved. In the latter case, party A proves control of DIDA to party B and party B proves control of DIDB to party A.

**How does it work?**

Similar to other authentication methods, DID Auth relies on a challenge-response cycle in which a *relying party* authenticates the DID of an *identity owner*.  During this cycle, an identity owner demonstrates control of their authentication material that was generated and distributed during DID Record Creation through execution of the authentication-proof mechanism.

![ssidifference](/images/ssi-detail/did-auth.png)

### Verifiable Credentials

Most credentials are physical. They are easy to forge, impersonate the true owner, can be lost or damaged., expensive to create and issue, can not scale, can not be easily verified and disclose more information than needed. 

Usually, any credentials (e.g. voter I d, driver’s license etc.) can be verified and hence, be called as verifiable credentials. Digital credentials hold the same information as in physical credentials but represented digitally. So, the term verifiable credentials here represents the digital credentials in combination with technologies like digital signatures. Formally, It can be defined as a tamper-evident credential whose authorship can be cryptographically verified. The verifiable credential ecosystem can be understood from the following diagram:

![ssidifference](/images/ssi-detail/ssi.png)


## SSI Stack

Now that we know the building blocks of the SSI system, let's take a look at the SSI stack to understand the architecture of SSI systems. At a high level, DKMS architecture consists of three logical layers as shown in figure below:

- The **DID layer** is the foundational layer consisting of DIDs registered and resolved via distributed ledgers.
- The **cloud layer** consists of server-side agents and wallets that provide a means of communicating and mediating between the DID layer and the edge layer. This layer enables encrypted peer-to-peer communications for exchange and verification of DIDs, public keys, and verifiable credentials.
- The **edge layer** consists of the local devices, agents, and wallets used directly by identity owners to generate and store most private keys and perform most key management operations.


![ssidifference](/images/ssi-detail/ssi-stack.png)

## Conclusion

The SSI space is very new and still evolving. If you want to learn more about SSI and want to be updated, you can subscribe to SSI meetup Youtube [channel](https://www.youtube.com/playlist?list=UUSqSTlKdbbCM1muGOhDa3Og) or join [SSI communities](https://internetidentityworkshop.com/schedule/) or connect to [IRC](http://irc.w3.org/?channels=ccg). It would be really interesting to see how the government reacts to SSI based identity management systems. Countries like South Korea, Canada and the USA have already started building SSI based systems for managing identities. 

## References

- https://sovrin.org/faq/what-is-self-sovereign-identity/
- https://github.com/WebOfTrustInfo/rwot7-toronto/blob/master/final-documents/convincing-dad.md
- https://medium.com/decentralized-identity/the-self-sovereign-identity-stack-8a2cc95f2d45
- https://www.youtube.com/watch?v=RllH91rcFdE
- https://w3c-ccg.github.io/did-primer/
- https://github.com/WebOfTrustInfo/rwot6-santabarbara/blob/master/final-documents/did-auth.md
- https://github.com/WebOfTrustInfo/rebooting-the-web-of-trust-fall2016/blob/master/final-documents/did-implementer-draft-10.pdf
- https://www.slideshare.net/SSIMeetup/introduction-to-did-auth-with-markus-sabadello
- https://www.slideshare.net/SSIMeetup/decentralized-key-management-dkms-an-essential-missing-piece-of-the-ssi-puzzle-drummondreed
- https://github.com/WebOfTrustInfo/rwot4-paris/blob/master/topics-and-advance-readings/did-auth.md
- https://www.slideshare.net/SSIMeetup/decentralized-identifiers-dids-the-fundamental-building-block-of-selfsovereign-identity-ssi
- https://livebook.manning.com/book/self-sovereign-identity/chapter-2/v-3/1
- https://livebook.manning.com/book/self-sovereign-identity/chapter-3/v-4/33


**Please donate to ak_Wc1r3YGs4WxCjQ72KfxcKnWbJru3Regu2wPNs6auUZYyiZVT6 if you feel its worth it. Thank you !!** 







