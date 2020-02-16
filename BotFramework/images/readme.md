# Build a chatbot with Microsoft bot framework with Azure and AWS
Ever wanted to create an assistant and use it on channels like Facebook, teams, Cortana or even Alexa? Or make use of your channel? Well, it's going to happen here. In this doc, we're going to build a chatbot with the Microsoft Bot Framework (https://dev.botframework.com/). We're going to do some AI tasks with LUIS (https://www.luis.ai/home). This will enable the Bot the get intentions, without parsing specific terms. Then we create a service for communication with the bot framework in dotnet core. After that, we're an interface for texting (and maybe speaking) with our bot will be created. Finally, we publish the backend service to AWS (because the free tier is providing more runtime) and host the Interface on Netlify. 

This is also the basic setup for Cyber Assistant Social Synthetic Intelligent Echo (Cassie, which is my try on a digital AI assistant).

Let's do it

# SETUP NOTES:
1. Building bot framework on azure
2. Build LUIS
3. Build App for BotFramework Backend (dotnet core)
4. Build WebChannel (with blazor)
5. Host on AWS
6. Host WebChannel on Netlify

