# HOW TO CREATE A DOTNET CORE CLI TEMPLATE
In this doc we're going to create dotnet cli template, that'll work with the *dotnet new* command.
I usually reuse a lot of my styles, extension methods, access methods and helper classes within my projects.
To speedup my project setup, I used to create *NuGet packages* or *project templates*. 
With *dotnet core* and the *dotnet cli* I can plug me into the dotnet development pipline and make use of the CLI (e.g. in *VSCode*).

# What is this about?
So, I'm going to take you through the needed steps to create a template that can be accessed from the *dotnet CLI*.
We're going to that for a project. Lately I worked a lot with blazor (https://dotnet.microsoft.com/apps/aspnet/web-apps/blazor) and so I'm going to set this up based on a blazor project. But you can do it with any other. I'm going to point out the neccessary steps based on the Microsoft docs (https://docs.microsoft.com/de-de/dotnet/core/tools/custom-templates). You can and should check them out as well (@docsmsft on Twitter).

The details can be found here:
* [Create a cli template](CreateACLITemplate.md.md)

# Who is this for?
This is for dotnet core developers, that are working in the dotnet core ecosystem.
You need a running installation of the dotnetcore sdk (https://dotnet.microsoft.com/download).
You should have a general idea about the CLI itself (https://docs.microsoft.com/de-de/dotnet/core/tools/dotnet?tabs=netcore21).

# Where can you find the project?
The linked projects are here:
* My Blazor WASM Template  -> https://github.com/PascalS86/blazor.wasm.template


# How long will it take?
My favorite line as a researcher and developer: *IT DEPENDS*

I'm not telling you, which project you should use or how you set it up. 
For trying, you can just you a sample dotnetcore application.

As a pro, I know we need numbers for estimating how long it'll take.
Here you are: my professional esimation:
* Create a cli template (*reading:* **15 minutes**, *doing:* **30 minutes**)

![I know, what I'm doing](https://66.media.tumblr.com/83cb7e0622630575a812ba3dc5731408/tumblr_ottbc6sLnD1rtels1o4_500.gifv)

# Some words
This kind of stuff is often quite easy to do, and it can really boost your performance to get stuff done. In my professional live, we use those kind of things all the time, to make the total development performance much faster. You can focus on the real things: what you want to do with your project and what you really need to develop. And of course, there are already great templates (like from Amazon for AWS lambda development).