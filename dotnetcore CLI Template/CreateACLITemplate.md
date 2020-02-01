# CREATE A DOTNET CORE CLI TEMPLATE 
I'm going to make a speed run to the steps, described in the Micrsoft documenation. I use these kind of templates to speed up my project creation. Usually they contain a couple of general helper methods or extension methods as well as styles and project structures, if needed.

In this scenario, I'm going to build a project template based on a *dotnet core application*.
This template will be accessable over the *dotnet new* command.

Let's do it!

## STEP 1: Prepare your project
Go to your application, which will be our template.

A dotnet cli template contains:
* **Sources and folders to be included**
* **.template.config**-folder in your project folder
* **template.json** in the .template.config folder

Yeah, that's it. We just have to add a folder **.template.config** and specify a file called **tempalte.json** in that folder within our project.

The template.json looks like:
```json
{
  "$schema": "http://json.schemastore.org/template",
  "author": "Jon Doe",
  "classifications": [ "Common", "Console" ],
  "identity": "SimpleProject.ConsoleTemplate.CSharp",
  "name": "Simple Project Console App",
  "shortName": "simpleproject"
}
```
Just replace the content to fit your needs.
* **Classifications** are used as tags
* **identity** is the unique template name
* **name** is the displayname
* **shortName** is the name, used in the dotnet cli

## STEP 2: Pack your template as a nuget package
With the dotnet cli, it's quite easy to pack your template.

You can pack it with the command 
```
dotnet pack
```
assuming your project looks now something like this:
```
project_folder
│   MyDotnetTemplates.csproj
│
└───myTemplate
    │   code files and folder...
    │
    └───.template.config
            template.json
    
```

If this is the case, we have to prepare our project file (e.g. csproj).

You have to add and specify the following tags under &lt;PropertyGroup&gt;:
* &lt;PackageType&gt;
* &lt;PackageVersion&gt;
* &lt;PackageId&gt;
* &lt;Title&gt;
* &lt;Authors&gt;
* &lt;Description&gt;
* &lt;PackageTags&gt;
* &lt;TargetFramework&gt;
* &lt;IsPackable&gt; (have to be true)




In this scenario, it'll look something like this:
```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <PackageType>Template</PackageType>
    <PackageVersion>1.0</PackageVersion>
    <PackageId>SimpleProject.ConsoleTemplate</PackageId>
    <Title>SimpleProject ConsoleTemplate</Title>
    <Authors>Me</Authors>
    <Description>Template for a console application</Description>
    <PackageTags>dotnet-new;templates;simpleproject</PackageTags>
    <TargetFramework>netstandard2.0</TargetFramework>
    <IsPackable>true</IsPackable>
  </PropertyGroup>

</Project>
```

Navigate to you where your project is (e.g. .csproj). Run the command 
```
dotnet pack
```
and you'll have a package to install.

# STEP 3: Install your package

