I was caught up by the possibility to share an Azure setup we use in an educational context. So this little story is written in the context of #AppliedCloudStories (http://aka.ms/applied-cloud-stories).

# AZURE NOTEBOOKS AND COGNITIVE SERVICES WITHIN AN UNIVERSITY CLASS

This story will cover up what and how we used Azure provided Services to enrich the learning experience within a lecture. I was motivated to set this up, cause I'm working as an assistant in that course and I'm working closely together with the professor. 


## WHAT IS THIS ABOUT?
This story shows how we used Azure Notebooks for providing an interactive learning experience in class. In addition to that, our students had to work on a project, which was about an autonomous vehicle that should navigate to a specific target. For that Custom Vision was introduced to the students and we used Azure Cognitive Service as an applied cloud service for that project.

I'm going to describe, why and how we used Azure Notebooks in our class. Also, you'll see how it's possible to use Azure Cognitive Services within Azure Notebooks which will then transit into the usage within the student projects.  


## AZURE NOTEBOOKS
There was always a big motivation for using Jupyter Notebooks within the class. But there are some requirements, that'd slow down the lecture (You know, it's not a Data Science lecture). Azure Notebooks were providing a great environment to use Jupyter Notebooks without explaining how to set up a Jupyter server. It was also easy to share Notebooks with the students. Azure Notebooks provides a couple of different programming languages. One of them is python, which is amazing (The students in our lecture learn python). 

### THE SETUP
The notebooks are capable to run code segments and change code within the environment. So I was creating the slides for the practical exercises in Azure Notebooks. This was great because everyone was able to use the same python environment. No IDE differences, no package differences, no python differences. The students just had to create a Microsoft account or use the one they have, to access the notebook, clone it and run it on free tier to work with it. It's that straight forward. So the students were able to interactively follow the slides and have running examples for the ongoing course.


## COGNITIVE SERVICES
In our class, the students must work on a project, that includes an autonomous vehicle. Every semester it's a little bit different. But there are some things, that won't change:
* It must work with applied cloud technologies
* The autonomous vehicle is the GoPiGo3 from dexter industries (https://www.dexterindustries.com/)

One of the projects was about letting the GoPiGo3 find a specific object within a room and drive to it. For achieving this goal, we introduced custom vision as XaaS (were X stands for AI), which is an applied cloud technologie. 
### THE SETUP

#### AZURE NOTEBOOKS

#### STUDENT PROJECT

## SOME FINAL WORDS