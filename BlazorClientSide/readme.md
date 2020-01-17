# How to create a blazor web app with datastore, authentication/authorization and hosting for nothing

We have a couple of options for creating a web application and host it. So this is not brand new. But inspired by Cecil Phillips (@cecilphillip on twitter) and Burke Hollands (@burkeholland on twitter) session on build 2019 (https://mybuild.techcommunity.microsoft.com/sessions/77173?source=sessions#top-anchor), so I was thinking how can I set this up for private projects as cheap as possible.

Thankfully Microsoft Azure, Amazon AWS and Netlify (oh thank you Sarah Edo * @sarah_edo on twitter * for open my eyes about Netlify) provide a couple of features and services, that you can use for exactly that.

# What is this about?

What are we going to do? Well, this is all about cheap as possible solution for creating a web application. We use Microsoft blazor (client) (https://dotnet.microsoft.com/apps/aspnet/web-apps/blazor) for creating a web application. This app is going to use AWS lambda function to interact with the cloud storage AWS DynamoDB. After that, we create authorization/authentication with Azure AD B2C. And finally we host our App on. This is not step by step tutorial for each technology, but it'll contain the relevant code snippets (and you can look it up on GitHub as well).

This doc will contain three parts:
1. [AWS DynamoDB and AWS Lambda](AWS_Lambda_DynamoDB.md)
2. [Azure AD B2C](Azure_AD_B2C.md)
3. Host on Netlify

# Who is this for?
Well, I decided to write it down primarly as a reminder for myself. But it's publicly available, soooo.... To understand the scenario, the linked project source code and the scenario, you should at least have:
* Skills in C# (I think, it's not too complicated)
* Knowledge about .NETCore
* Ideas about the cloud (we use two cloud providers here)
* SERVERLESS approach (but it's more of a sidenote. We build our app serverless)
* Basic javascript 

# Where can you find the project?
The linked projects are here:
* AWS Lambda  -> https://github.com/PascalS86/my-comic.AWS-Lambda
* Blazor wasm -> https://github.com/PascalS86/my-comic.wasm

# How long will it take?
My favorite line as a researcher and developer: *IT DEPENDS*

If you just go through the single parts, you will find your self doing the basic work quite fast.

If you try to link it to the project, it could take some more time.

But, as I'm used to numbers for my estimation, I'm going to give you one:
* PART I (*reading:* **10 minutes**, *doing:* **45 minutes**)
* PART II (*reading:* **10 minutes**, *doing:* **60 minutes**)
* PART III (*reading:* **- minutes**, *doing:* **- minutes**)

# How is the setup?

## WEBAPP TECH
I created a web application with blazor (webassembly)  (https://docs.microsoft.com/en-us/aspnet/core/blazor/get-started?view=aspnetcore-3.1&tabs=visual-studio). You need at least dotnetcore 3.1 to build the project, which was created with these technologies.


## DATASTORE
For the datastore, I'll use Amazon AWS DynamoDB, which offers a 25 GB NoSQL Storage for free (https://aws.amazon.com/dynamodb/features/). In that case, it's cheaper than Azure Table Storage, as long as you don't have massive data and CRUD operations. 

![Amazon DynamoDB](images\dynamoDB-freetier.PNG)

## ACCESS FROM WASM
For accessing the data, I'm going to use lambda function in AWS (https://aws.amazon.com/lambda/features/). This is needed, because back in 1/10/20 there was an issue with the SDK, when you use wasm for you blazor application. So we are serverless here (Simona Contin (@simona_cotin on twitter) will cheer for that setup approach :D). For private purpose I use lambda function instead of azure functions (https://azure.microsoft.com/en-us/services/functions/), because they are cheaper for my scenario (private application, and let's face it, the traffic is not that much).

![Amazon Lambda](images\lambda.PNG) 

## AUTHENTICATION/AUTHORIZATION
For authenticate the user, I decided to go for Azure AD B2C (https://azure.microsoft.com/en-us/services/active-directory-b2c/). It has free tier and provides us with the user administration from Azure AD. Keep in mind, that this is a serverless application, which means our code is mostly execute on client-side. This means **"authentication checks can be bypassed because all client-side code can be modified by users. The same is true for all client-side app technologies, including JavaScript SPA frameworks or native apps for any operating system."** (https://docs.microsoft.com/en-us/aspnet/core/security/blazor/?view=aspnetcore-3.1&tabs=visual-studio-code). We use the authentication mechanism to pass them to our AWS lambda function to and work with the permissions, we need. 

![Azure AD B2C](images\azure-ad-freetier.PNG)



## HOSTING
I'm going to use Netlify for hosting my blazor application. Find out more (https://www.netlify.com/). For private projects or proof of concepts, they offer a free tier. 
![Netlify Pricing](images\netflify-pricing.png)