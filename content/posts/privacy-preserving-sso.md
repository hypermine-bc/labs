---
title: "Privacy Preserving Sso"
date: 2020-11-16T07:11:24+05:30
draft: true
---


The social login helps service providers to quickly onboard a user without requiring them to go through the registration process. This way, on one hand the service providers are able to provide seamless onboarding to their user and on the other hand, the user need not to type his details like name, email, phone number, every time he avails a service from a new provider. Moreover, the user does not have to remember multiple usernames and passwords for each of these service providers but` just one for social login. Apart from this, the service provider gets user data directly from the social login provider (or 3rd party identity provider i.e. IDP) in order to build a user profile in their portal.

There are two major problems which have been seen in the social login flow. Most of the social logins providers like Facebook, Google etc. still rely on password based authentication and we all know the problems with passwords like password resetting, password hacks, password forgetting etc. Now any of the problems related to authentication in social login, costs the service providers (those who support social login) a user loss and hence loss in business. A user might not be able to use the service if he/she is not able to authenticate himself/herself to the IDP.

The identity provider stores data of millions and millions of users and that can become a honeypot for many hackers. Moreover, the identity provider also has the ability to misuse the usedata without the consent of the user in many different ways like doing analytics, by selling them etc. We have seen many cases related to identity theft and userdata issues in the past. This is a very serious problem for the user who is very much concerned about their data privacy and protection as they have to fully trust these IDPs on how they store and manage their data. Apart from that, the social login providers can track where and all a user is logging into - “Facebook would know if you are travelling using MakeMyTrip or buying something from Amazon”, and that becomes another privacy concern for users.

Having said that, the social login is not being used in serious enterprises since it does not tell, the one who is using the credential actually possesses it as the credential can be easily shared with peers.



As you know Hypersign is going to be Self Soveregin identity layer on Aeternity, we have been working on integration of Hypersign identity protocol in Superhero wallet and finished off the POC version.

So basically the idea is, Superhero user can use the wallet to be able to login into website that supports Superhero login (think of like Facebook login). The moment user install Superhero wallet and create an account, hypersign did (decentralized identifier ) is issued to the user.

![img](/images/privacy-preserving-sso/sso-arch.png)


![img](/images/privacy-preserving-sso/comparision.png)


https://cdn.loom.com/sessions/transcoded/38e6343e829f453381c7f613190c75b8.mp4?Expires=2147472000&Policy=eyJTdGF0ZW1lbnQiOlt7IlJlc291cmNlIjoiaHR0cHM6Ly9jZG4ubG9vbS5jb20vc2Vzc2lvbnMvdHJhbnNjb2RlZC8zOGU2MzQzZTgyOWY0NTMzODFjN2Y2MTMxOTBjNzViOC5tcDQiLCJDb25kaXRpb24iOnsiRGF0ZUxlc3NUaGFuIjp7IkFXUzpFcG9jaFRpbWUiOjIxNDc0NzIwMDB9fX1dfQ__&Signature=W7akoOLcApLb9ctWbwWdQ1iTZ43oOaK7gnYBP5DY34US2lMfBLdbBHe0z~U2hPXkkoFLmJcwG8ZlOqYzsgEViYH2NvsB9JgdX~tqkWBwlNKWe5ARz2bxH7bFz1Mqaa2WEg3KBsKr69NXh1LK-NZr1IASXMeqm7jZ2pKYj-SXdYwWK2KO-J09ol7iqEZTJoU8~vt2M9lfUDZwxEgpbNk3JJROyDuP--2LgLH9A~fx6EOQO3HgZLZY~HhuRQ1Yfm6D2LNOBkxUwYt49eoUaD4hrm~gWF4ikEEflXFVJiATrEI8I7R7zNwQU1fCMdDcbF2gWzhI8IhBMmV-qOghwXte~Q__&Key-Pair-Id=APKAJQIC5BGSW7XXK7FQ


# BankId (as we saw in Sweden)



