# Build a chatbot with Microsoft bot framework with Azure and AWS
Ever wanted to create an assistant and use it on channels like Facebook, teams, Cortana or even Alexa? Or make use of your channel? Well, it's going to happen here. In this doc, we're going to build a chatbot with the Microsoft Bot Framework (https://dev.botframework.com/). We're going to do some AI tasks with LUIS (https://www.luis.ai/home). This will enable the Bot the get intentions, without parsing specific terms. Then we create a service for communication with the bot framework in dotnet core. After that, we're building an interface for texting (and maybe speaking) with our bot. Finally, we publish the backend service to Azure. 

This is also the basic setup for Cyber Assistant Social Synthetic Intelligent Echo (Cassie, which is my try on a digital AI assistant).

Let's do it

# Who is this for?
To understand the scenario and the linked project source code, you should at least have:
* Skills in C# (I think, it's not too complicated)
* Knowledge about .NETCore
* Basic idea of Microsoft Azure as a cloud provider 
* Interest in bringing AI in your apps

# Where can you find the project?
The repos to the bot can be find here:
* https://github.com/PascalS86/csandra-bot

# How long will it take?
This doc contains two parts:
* Setup the cognitive services in a dotnetcore service
* Deployment on Azure

The first part is all about setting up the needed services and include them in dotnetcore project. We do also the testing with the botframework emulator.
The second part is all about rounding up the deployment settings on azure and make it all accessible.
* PART I (*reading:* **5 minutes**, *doing:* **30 minutes**)
* PART II (*reading:* **5 minutes**, *doing:* **20 minutes**)

# SETUP NOTES:
## COGNITIVE SERVICES
We use two different cognitive services from the Azure AI (https://azure.microsoft.com/en-us/overview/ai-platform/):
* BOTFRAMEWORK (https://dev.botframework.com/)
* LUIS (https://docs.microsoft.com/en-us/azure/cognitive-services/luis/what-is-luis)
* BING SEARCH (https://azure.microsoft.com/en-us/services/cognitive-services/bing-web-search-api/)
Botframework allows us to deploy the bot to different channels and make it accessible through the web, Skype, Cortana etc.
LUIS stands for Language Understanding Intelligence Service and allows us to get intentions from natural language. 
It's worth looking in cognitive services, because they all have a strong free tier.  


## WEBCHAT
One interface will be the webchat interface with the directline channel. We won't do fancy stuff here, just reuse the app from Microsoft.

## DEPLYOMENT ON AZURE
The Application will be hosted on Azure. Since the free tier for the hosted services has some limits, we have to consider hosting the service somewhere else later or spend some money. There are some details on the hosting, that are important to mention later.

# Some words
I think conversational user interfaces are the next real step in interaction and enhanced user expierence. AI is also getting more more accessable and usable. A bot has the potential to enrich you applications in a quite easy way and make your services available to other platforms as well. For me, this is my approach to generalize my interfaces and interactions for most of my future software (if possible). As that said:...

![JYourUp](https://i.pinimg.com/originals/33/0a/40/330a40815bcac1887d26422a81acf04d.gif)