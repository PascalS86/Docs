# Create MS Teams APP
Here I'm going to go through, what you have to do, to create a MS Teams app.
I followed the docs from here -> (https://docs.microsoft.com/en-us/microsoftteams/platform/).

## What's so special about it?
What impressed me really is, how simple the deployment of MS Teams App is.
Especially if you work with AppStudio. You can either upload it to the Teams Store for everyone, or you can just deploy it within your organization. In the second case, you just need to remember, that you need permission to do so. Soooo, be nice to your admin :)


# How long will it take?
Reading will need about 5 to 10 minutes


# Who is this for?
Everyone who have a web app and want's it to be in teams :)

# So let's do it
I assume, you have a web app (JS, Blazor, MVC or what ever).
This is the to do for making your web app ready.
You'll see some other options in the msteams *manifest.json* file.
## To dos for web app
1. You have to host your app. You can use Azure, Netlify, AWS, or any other kind of webserver.
2. You have to use the javascript sdk -> (https://github.com/OfficeDev/microsoft-teams-library-js). You can find the doc -> (https://docs.microsoft.com/en-us/microsoftteams/platform/tabs/how-to/using-teams-client-sdk)
3. Add the sdk reference in your app like 
```html
<!-- Microsoft Teams JavaScript API (via CDN) -->
<script src="https://statics.teams.cdn.office.net/sdk/v1.6.0/js/MicrosoftTeams.min.js" integrity="sha384-mhp2E+BLMiZLe7rDIzj19WjgXJeI32NkPvrvvZBrMi5IvWup/1NUfS5xuYN5S3VT" crossorigin="anonymous"></script>

```
4. Initialize you app within MS Teams. To do so, I recommend creating a .js file, which calls the *microsoftTeams.initialize()*
```javascript
/*msteams.js file*/
(function () {
  'use strict';
  // Call the initialize API first
  microsoftTeams.initialize();
)();
```
That's it for making your web app ready.

#### Notes
If you test your app locally with ngrok, be sure you setup localhost, or at least set up ssl-certificate to the original route of your machine. Otherwise the desktop app of MS Teams won't show you the content (at least by now).

## To dos for deploying to MS Teams
Microsoft provides three distribution scenarios (https://docs.microsoft.com/en-us/microsoftteams/platform/concepts/deploy-and-publish/overview). I'll focus on the sideloading scenario because this is really easy and can speed up the deployment of business-specific solutions. 

Now the fun part.
1. We install the app **AppStudio** on MS Teams
2. We go to the **manifest editor** tab on **AppStudio**
3. Create a new app, or edit an existing one.
4. You fill in the blanks (e.g. the web apps address). If you add a personal tab, please ensure, you enter a *content URL*, with whatever path is needed, and *website URL* which contains the base  path.
5. Download the manifest (or submit).
6. If you downloaded the manifest (it's a .zip file) and you have the permission to upload your custom app, click on apps
7. Select *upload custom app*
8. select the .zip file

Your done. Your app can now be consumed within your org/team.


