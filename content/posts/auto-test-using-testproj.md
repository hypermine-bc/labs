---
title: "Automation Testing with No-Code approach saved us days of effort"
date: 2022-01-04T11:31:53+05:30
draft: false
categories: ["testing"]
tags: ["automation", "testproject", "testing", "hyperfyre", "security"]
banner: "/images/auto-test-using-testproj/background-img-slider.jpg"
authors:
  [lovely,raj]
---




We all know why testing is an important part of software development life cycle, especially in agile environment, where release cycle time is shorter - you do continuous build-test-release every week or two. When it come to startups, its even more challenging since startups work on "fail-fast" approach which usually has resource crunch and grows exponentially (at least in the initial phases). You don't even realize how soon the product gains 10k users from 1. When the project is small with less number of users, its wise to do manual testing (I may be wrong but that's what worked for us) and not spend too much time in writing code for automation tests because of following reasons   : 

1. Most of the devs are involved in product development (I know they "should" follow [TDD](https://en.wikipedia.org/wiki/Test-driven_development) approach but sometimes it does not work practically, especially when your release cycle is very small). 
2. Lack of experienced testing resources who can also do coding.
3. Since requirements are not very clear at the beginning and there are frequent change, writing code for automation test may not be very useful.

In this blog post, I am going to talk about how we approached our automation testing problems with minimal resource and how it helped us save days of work. 

## Let's begin with the problem

We had two problems in hand: 

1. Our initial test team was not very much comfortable with writing codes (we had been doing manual testing so far),  which means we cannot opt for various automation testing frameworks like Jest, Cypress etc. 
2. Because we were doing manual testing and the project had become considerably large, everytime, before we roll out a new release, we had to spend too much time in manually testing all the modules (around 400 test cases) which takes huge amount of time and effort. And even after spending this much time/effort we were not sure if things will work out as expected.

Our objective was clear, everytime we push any new changes or roll out a new release, the whole UI should get tested automatically, which would ultimately result in **saving a lot of manual test time** and most importantly would **give confidence that nothing would break** in production. 

> The solution was clearly, "Automation Testing" but we had to find out a middle ground where our tester who were not very comfortable with code can also do automation testing. 

## TestProject came to rescue us

As per their doc: 

[TestProject](https://testproject.io/) is an automation solution that simplifies your test automation experience. It provides users with powerful record and playback capabilities along with a developer SDK and the ability to use and create addons to extend the capabilities as needed. TestProject is built on top of open source automation tools like **Selenium and Appium**, but it removes the complexity of managing and installing drivers for each platform and browser that you need to test. 

TestProject is a community driven tool and has a **free forever plan** that is fully featured and that you can get started with in moments. Though, TestProject can be used for the frontend and API testing both, we have used it only for testing our Vue Js frontend. Essentially,what a developer can do is, record the test scenario on the browser and playback whenever they want to test. 

In this blog we are going to learn step by step procedure of how one can setup TestProject for their application to perform automation testing. We will also learn how to see reports and finally we will see a demo of pre-recorded test session to get a clear idea.

## Let's see how we can use TestProject

Now that the **Why** part is clear, let's see the **How** part - how we can use TestProject.
Start with creating a new account on TestProject cloud platform. Follow [this](https://docs.testproject.io/getting-started/creating-an-account) document to create an account. 
Once we created an account, we have to install and setup an **Agent**.

### TestProject Agent

**TestProject Agent** is a tool that connects  with the Test Project cloud platform and helps to execute the test on the local machine. It allows test to run on any computer on which it's installation happens and support all the browsers . It needs to be installed and registered to run the test. Read more about agent in this [doc](https://docs.testproject.io/testproject-agents/what-is-a-testproject-agent).

#### Download and Install Agent

We first need to download agent binary and install it in our local machine. 

- Go to the TestProject app and login.
- After login, go to the **Agents** button in the nav and click on the link for your required platform.
- Download the Agent as per your operating system (the agent is available for Windows, Mac and Linux operating systems)
- Finally, install the Agent. Follow this [doc](https://docs.testproject.io/getting-started/installation-and-setup) to learn more about installation of agent binary in OS of your choice.

#### Register an Agent

Now that our agent is running in our local machine, the next step is to register it with our TestProject account.

- Login to your TestProject account.
- Click on **Agents** button on the on the nav bar and then click on **+ Register Agent** button. Kindly, see the screen short below:

  ![image](https://user-images.githubusercontent.com/90840933/147075476-5dd4b722-dc7a-4287-8723-187420ec6424.png)

- Finally, provide a name to our agent and then press **Save**. It will automatically detect and get connected to the agent present in your machine.

  ![image](https://user-images.githubusercontent.com/90840933/147329483-d2a06f2e-3377-40e8-be03-9a72690cecc7.png)
- Once connection is successful, you will see agent signal to be green otherwise red. 

  ![image](https://user-images.githubusercontent.com/90840933/147326019-8728488e-6293-4957-89b1-ea7cf1159c7b.png)

### Create New Test

Once everything is setup, we can go ahead and start recording our test cases. But before we do that we need to create register an application so that TestProject will know what to record.

#### Creating Project Folder 

An **Application** can be registered inside a *project*. You can think a *project* as a top level container where all your application and their respective tests exists. 

- Make new project folder and give it a name of your choice.

  ![image](https://user-images.githubusercontent.com/90840933/147360452-76de0773-df58-475e-a122-1f09e39c8122.png)

### Register An Application

- Navigate to **Application** page by clicking on  **Application**  button in the side nav.  Click on **New Application** button. `Create a new application` dialog popsup.
- Choose **Web** and press **Next**.

   ![image](https://user-images.githubusercontent.com/90840933/147359446-f7cce2f0-dc4b-45df-9ad7-482dd5268ab0.png)

-  Give a `Name` and `URL` of your web application in the dialog and then press **Done**.

   ![image](https://user-images.githubusercontent.com/90840933/147359730-8a939d57-14f6-418a-a6d2-6d32d5b66927.png)

- The application is registered, and we can now proceed to create and record our new test.

   ![image](https://user-images.githubusercontent.com/90840933/147361304-ab50c47b-7d0a-4f92-8df1-5db438171638.png)
 
### Record and playback test case

To record and playback any project, we have to press on **New Test**, which facilitates the user to create the test step by step  according to the test scenarios and test cases.

 ![image](https://user-images.githubusercontent.com/90840933/147328217-ac29efca-846e-4d97-9c7e-70ab39e6cbe7.png)

- Choose the **Web** option and click **Next** button.

  ![image](https://user-images.githubusercontent.com/90840933/147329270-0f72d3cc-d9d2-4fb1-8415-05a2887b5b23.png)

- Enter test details like name, description.

  ![image](https://user-images.githubusercontent.com/90840933/147361986-64ac0577-c85a-4f86-bc21-224ff5be901b.png)
 
- Click on **Select Web Application** dropbox and  select your registered  project application.

  ![image](https://user-images.githubusercontent.com/90840933/147361816-31863ec5-9c8c-4b88-8b86-f214ea05538a.png)

- To get started, click on the **Record** option and **Start Recording** (we can also choose cloud/file to save the test).

  ![image](https://user-images.githubusercontent.com/90840933/147329144-1c5c408a-a52c-4d9f-9ac0-d8a7667424d1.png)

- After few seconds, new window will get open with test recorder and the project we want to test.

  ![image](https://user-images.githubusercontent.com/90840933/147361876-9b2ffb93-a38a-4269-bec8-8f0a8cc239a1.png)

For more clarity, kindly watch this [Tutorial](https://youtube.com/playlist?list=PLhW3qG5bs-L_QuqpGY-B-1ifP1j4ve3fx).

> These are the basic steps. To know more in depth, follow this cheatsheet ([a blog](https://blog.testproject.io/2021/11/29/testproject-smart-test-recorder-the-ultimate-cheat-sheet/)) and this [doc](https://docs.testproject.io/using-the-smart-test-recorder/web-testing/creating-a-web-test-using-the-testproject-recorder).

### Import A Project

Further more, the TestProject also allows one to import and run the pre-recorded test cases. 

- Go to TestProject app.
- Click on **Open file** Button and import the Test and run it.
 ![image](https://user-images.githubusercontent.com/90840933/147323800-125f2480-21ab-4936-a467-3859a53a9991.png)

### Reports

More interesting part is we can also check **Reports** of our created test which provides us the detailed structure  of the test. 
- Run the created test.
 ![image](https://user-images.githubusercontent.com/90840933/147362226-23e221fa-41c2-43f3-b907-73ae8f0cd8de.png)

- Click on **Reports** button. 
  ![image](https://user-images.githubusercontent.com/90840933/147326809-e3a62d61-b892-47c9-86eb-a3b738ab4220.png)
- Reports  will  display pass/fail , velocity chart , execution time and many more features. Take a look at the sample report.
 ![image](https://user-images.githubusercontent.com/90840933/147362146-68eb2975-7787-49f3-a3e1-5da9c9bd8e22.png) 

Read more about **Reports** in this [doc](https://docs.testproject.io/reports/introduction-to-reports-in-testproject).

##  Demo

Here is a working demo of automation testing of one of our application, [HyperFyre](https://fyre.hypersign.id).

[![Alternate Text](https://user-images.githubusercontent.com/15328561/148012275-20e6ab78-cb27-4cc0-a488-6860f4b46375.png)](https://youtu.be/KUUwcgi_sFg "Automation Testing of Hyperfyre using TestProject")

## Conclusion

The TestProject is a great tool for beginners to dive into the realm of automation testing. It has very less learning curve - saving a lot of testing time. I hope this blog was useful for anyone to get started with TestProject. More about TestProject in the next the blog post where we will understand how TestProject works under the hood, until then, Happy Testing!
