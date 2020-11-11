---
title: "Securtiy breaches have become common in consumer facing applications"
date: 2020-11-02T18:20:11+05:30
draft: true
---

**Trust** is one of the major important factors for the growth of cosumer-facing application. Usually, the number of users of consumer-facing applications are compareively higher than employee-facing application. In case of employee-facing applicatoin the trust is kind of implicit - the moment a employee accept the offer letter, the trust gets 

Now the reason we started our story with trust and not the security becuase secutiry come next to trust. One you trust a system, you expect the system to be secure. Now this trust-and-security can make or break a system,specially for cosumer-facing application as the degree to trust if very high. Additionally, there cosumer-facing application also has to face compitions as end user has ability to swtich between these providers to avail same kind of service. 

The cosumer-facing applications mostly have to store user personal data inorder to provide a service seamlessly. Now that brings a challenge and responsibiliyt to the provider that how do they store and mange the user's personal data. A few days back we have seen a major [security breach](https://timesofindia.indiatimes.com/business/india-business/bigbasket-faces-potential-data-breach-details-of-2-cr-users-put-on-sale-on-dark-web/articleshow/79115354.cms) in a consumer facing application called, BigBasket. We wanted to investigate because of two reasons, one we at hypermine works on these kind of probleme stateme and the other, even I am the user of BigBasket so I beleive my personal details (like addereess and phonenumer) have also got hacked. So now the hacker knows this info:

> Vishwas, whose phone number is 1234 and email is XYZ@tempmail.com and whoes age is 27, buys fruites every week and is a resident of so and so city!

I will come back to statement in a bit. But before that what is case here:


## What had happened?

As reported by TOI:

> grocery e-commerce platform Bigbasket has faced a potential data breach which could have leaked details of its around 2 crore users, according to cyber intelligence firm Cyble. 

> Cyble said that a hacker has put data allegedly belonging to to Bigbasket on sale for around Rs 30 lakh. Team at Cyble found the database of Big Basket for sale in a.

> The leak contains a database portion; with the table name 'member_member'. The size of the SQL file is about 15B, containing close to 20 millions user_data.

> The data inclued, emailId, password hashes, contact numbers, addresses, dob, location, IP address etc.

Now this is not the first hack of user data on consumer-facing applicatoin. Previously, this year we have seen [Unacademy hack](https://www.theweek.in/news/sci-tech/2020/05/07/unacademy-hacked-data-of-20-mn-users-up-for-sale.html here is what happened withh Unacademy in Jan 2020) as well as [twitter hack](). Althouh, it is not fair to compare Unacademy and twitter hack but in both cases user reputation and security is at risk. having said that, I believe it would be too early to give any judegment in case of Bigbast as the investigation still going on but certainly we have been seeing Indian companies ignoring user data prtotection and prviacy to some extent. 

## What measures could have taken to prevent this?

### Encryption 

Now if we think about the solution, one simplest (but yet complex one) solution which comes into our mind is, encrypt all data you store. But there certainly a reson behind why do they not do that? One answer could be to provide seamless user experience to theri customers. Beucase UX is very important factor for the grwoth of the customer faceing app. Moreover, the cryptography can slow down the whole system drastically if not implement properly. 

Additionally, the service providers do analytics on the app database to provide better user expereicen to their customer, now if the data is encrypted into the db, then the analytics systems need to know the key to decryte it before performing analytics. By the way there are possible way like, Homomorphic encription with which it is possible to perform basic analysics evne on encrypted data, but lets not bringg that into this blog. 

Morve over, the data bases are also fuel for monitoring systems, so now the monitoring systems, need to know the key to decrypt the data. 

### Why to store the data?

One solutiion can be, why do provders even store the cirtical data in the first place? 


### Understading data set

It is very important to undersatn the data set properly in order to propsoe any solution like enryption. Becuase you might end up solving their one problem but create another. For example, instead of revealing this information to hacked (in case system got hacked):


> Vishwas, whose phone number is 1234 and email is XYZ@tempmail.com and whoes age is 27, buys fruites every week and is a resident of so and so city!


If we end up revealing this:

> A person, is an adult who buys fruites every week and is resident of India.


Look at the above two stateme very carefully and analysize what information does both of these messages reveals and which is more careful for user's privacy.

### tradeoff between usuability and security


Two major things is more or less equally important for consumer-facing applilciont.

1. Seamless user experience
2. high security for users personal information like, name, email, phonumer, ip, address adn credit card detials.

Now for devleoper of application it is a tradeoff, they need to decide which is most priporty. Consumer-facing applicaiotn often tends towwards usability than security as the growth rate is very muchc depended on what user see, feel and expereicen witht he application. But on long run, they have to face challenges what Bigbasket is facing right now.  By the way, had it happened in Europe, the user data protoettchtion and privay law is so stricts that the company might have to deal with leagal consequences. 


## Hypersign

Hypersign is customer identity and access managment (CIAM) solution which provides security, 

- Built using Publick key cryptograpy and DLT, the Hypersign provides enough confidence to the serivce providers about their security of user data and also to the end user about their data on how and where they use it.
- the solutioin is fexlible to fit into any kind of consumer facking applicaitons be it mobile app, or web app.