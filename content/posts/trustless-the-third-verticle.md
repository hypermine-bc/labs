---
title: "Trustless - The third vertical of credentials management"
date: 2020-03-14T18:25:30+05:30
draft: false
categories: ["authentication", "blockchain"]
tags: ["trust", "trustless", "fido", "authentication", "passwordless", "public-key-infrastructure", "cryptography"]
banner: "/images/trustless-the-third-verticle/0_pgKTtVIMQaHATPob.png"
authors:
  - vishwas
---

Identity management (IM) has always been a challenge for companies, whether it's securing their internal employee's access to company systems and applications, or securing their customers to access the web apps and databases. This aspect has two major components, Management of identity and Management by identity. Management of identity is primarily Authentication and Management by identity is Authorization.

Traditionally, common methods of managing digital identities such as usernames and passwords have been proven to be less secure.Verizon has reported that:

> 81% of hacking-related breaches used either stolen or weak passwords.

People started solving this problem either by using Multifactor Authentication [MFA] or by applying complex password policies. Later on, passwordless solutions like [HyperSign](https://hypermine.in/hypersign/) came into picture which is more secure in the 
sense that user does not even have to used password and rather it relies on public-key cryptography to validate the identity of a user. To understand the whole evolution of credential management in details, let's look into how exactly the method of issuing digital identities have been evolving over time.


## The journey

### Approach 1

It all started when service providers [SPs] were storing user credentials *usernames and passwords* in `plain text` in a database. This method raised concerns such as *why should a system administrator be able to see a user's credentials*, and in the event of an attack or breach it was easy to read all the credentials of the entire database.

### Approach 2 

To solve this vulnerability, SPs started encrypting the credentials and stored the `encrypted password` into a database. Although this concealed the credentials, the problem was still not solved. The admins hold the encryption keys and can decrypt the credentials at any time. The definition of the password which dictates that neither a SP nor a system administrator, should be able to recover a user's password, this was obviously a cause for concern. There was one more challenge with this approach, if two users happen to have the same password, the corresponding encrypted text would most likely also be the same.

### Approach 3

SPs then started storing the `HASH of the (password)` in the database. To verify a user's password at login, the SP keeps the user's submitted password in memory [RAM] - so it never needs to read the disk, in order to quickly compute its HASH.
If the computed HASH matches the stored HASH, the server authenticates the login. In this way, they were able to solve the problem of system-admins getting access to the actual credentials. However, this approach did not really solve the problem of two separate users creating the same passwords. The same passwords would be generating the same HASH value and allowing for frequency and pattern identification. This approach is also vulnerable to rainbow table, dictionary, or brute force type attacks.

### Approach 4

To solve the problem of the same HASH, SPs came up with an idea of `SALT`. SALT is a fixed-length arbitrary value (per 
user) that is added to the input of HASH functions to create a unique HASH for every input, regardless of the input not being unique. 
The SPs then started to store the `HASH of (password + random_SALT)`. SALT is stored in the same database along with the usernames and the HASH. This solution works and is still being used extensively. However, this again causes the challenge of storing the SALT in the same database; which is an exposure to the risk of attack (a rainbow table would be useless).
Example: password is `SECRET` and it is SALTed with `SALT` which is a total of 10 characters - `SECRETSALT`. The HASH of 256-bits is 32 characters. If a database has already been calculated for every possible sequence of 10 characters, then the HASH for `SECRETSALT` is already known. Adding the SALT did not actually help in this case. Yes, 256-bits is a lot to calculate but computational power in computers is growing exponentially. It was once believed that 64-bits would be secure forever. Ha-Ha.

### Approach 5

Instead of storing plaintext `SALT` in the database, the SPs started adding `PEPPER` to the equation. Similar to SALT, `PEPPER` is also an arbitrary value; but unlike SALT, it is unique for all users and is not stored in the same database and hence its a secret. SPs now storing a `HASH of (password + random_SALT + unique_PEPPER)` in the database to add an extra layer of security. Now, If the `PEPPER` is to remain a critical secret, then it should also be expected to keep a file full of HASHed password secret too. PEPPERing is like adding a cheap master lock on an already locked bank vault. If we expect to keep our password file secret, then the whole debate about SALTing/PEPPERing is pointless because if an attacker does not have the HASHed password then our problem is anyway solved.

### Approach 6 

To add extra security, people came up with solutions like Multi-factor authentication in which a user has to validate himself more than one time with more than one different authentication methods. MFA reduces the risk for sure, but it lacks in usability and depending on implementation, adds complexity.

---

> Bottom line is, no matter what we do, we end up with the same problem. We start with a problem statement, and a solution to that problem statement, but the solution, in turn, creates another problem, and so on and so forth, we keep going on, running around in circles, adding more and more locks. This is certainly not the way forward and hence `password-less` came into the picture. Solutions like [HyperSign](https://hypermine.in/hypersign/) or Window Hello have done a great job of solving this problem. If you 
want to understand how `password-less` authentication works, you should definitely check out the documentation of the [HyperSign](https://hypermine.in/hypersign/).


## The comparison

![alt](/images/trustless-the-third-verticle/0_pgKTtVIMQaHATPob.png)


The above image is directly taken from Microsofts' Password-less protection whitepaper. Which compares these three features [`Password`, `MFA`, `Password-less`] over verticals of **security** and **convenience**. So, for example, if we look at `Passwords`, though it has low security but it excels in convenience. `MFA`, excels in security but lacks in usability. Whereas, `password-less` excels in security and convenience both.


## Introducing, the third verticle - TrustLess

Blockchain technology introduced the notion of **Trustless**. Let's try to understand this word a bit more before we do further talking. The word *trustless*, sometimes, is very confusing. People do get confused it with *eliminating trust* from the system. But in reality, it is minimizing the amount of trust required from any single actor in the system and they do this by *distributing trust* among different actors. To facilitate trust distribution, one can think of having a consensus, which simply means an *agreement*. The decision which was being taken by one actor of the system is now being taken by multiple actors. But, the question, why would these actors will behave good, can be answered by the term, *incentivization*. Anyways, I do not want to go into these other terminologies and distract you from our main point which is *trustless*.
Now that we have got some idea about this term, let us go back to our discussion of credential management. We have these questions right now to deal with:

1. What is trustless? (*Already discussed*)
2. Is it relevant for our discussion in credential management? If it is, where does it comes into the picture?
3. Do we really need to think about the 3rd verticle or we are all good? (*the trade of*)
4. How can it be implemented (*the approach*) and compared with other two vertices?

## Question #2

![alt](/images/trustless-the-third-verticle/0_ATqf8zkQFN3GPyrx.png)

In order to answer this question, we need to go back a little and see how the password-less authentication works. The above image is taken from ThumbSignIn, which is [FIDO](https://fidoalliance.org/) compliant, where a cryptographic key pair is stored in users' device (say mobile phone). At the time of authenticating himself to a website, instead of providing username and password, a user scans a QR code and signs the message (usually a challenge generated from the server - also called Auth Server / FIDO server sometimes). The produced digital signature is sent to the server which validates the digital signature and sends the response (yes/no) to the website. Based on the response, the website lets the user access the home page.

More detailed architecture can be seen in the diagram below, which is taken from FIDO UAF framework. We have to focus on point #5. As we can see FIDO server, validates the digital signature and send the response to webApp.

![alt](/images/trustless-the-third-verticle/0_6ri2VTIw_9ocqt2Q.png)

So far so good. But here comes the next question and I would request you to think about it before proceeding.

> What is the guarantee that AuthServer will always do the right thing? and will not validate incorrect signatures?

Honestly, I do not know if this thought process is right or not, I am just throwing some idea on you. So, I want you to stop here, think about it, argue on it and then read the next section (by the way we are still not done with our question #2).

In a fully trusted environment, we should not even get this question, right? True, but remember, the purpose of Blockchain - to distribute the trust. We can see, in our current system, that AuthServer/FIDO server is a central trusted party which takes the whole decision. But again, its a trade-off between fully and partially trusted systems, there is no good or bad solution. I will talk about this trade in the next blog when we discuss question #3 and #4. This blog already goes a little longer, so I should stop with the above question.


## Summary

We started with a journey of evolution of credential management and then we talked about how password-less solution excels all previous solutions by comparing password, MFA and password-less over two verticals - security and convenience. We went ahead a step further and introduced a third vertical, trustless. Finally, we have left with two questions, do we need to implement the third vertical and what is the approach to implement it, which we will talk about in the next blog.


--

Hope this blog helps, keep reading!