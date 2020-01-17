This is Part II of III from [How to create a blazor web app with datastore, authentication/authorization and hosting for nothing](readme.md)

# Azure AD B2C
Azure AD B2C is a solution to manage authentication for a single user. That's very shortened, but for this setup, it's enough to remember. Before we can use the Azure AD B2C authentication, we need to set it up and configure it, so our web application can consume the authentication service. I won't go through the setup process, because Azure provided some good step by step tutorials (https://docs.microsoft.com/en-us/azure/active-directory-b2c/tutorial-create-tenant).
After your tenant is ready, we can continue with our setup.

**Now we have problem here:** 

Usually, you would handle your authentication on your backend, but we are serverless. What can we do? Well, there are a couple of options, we could use.
* Create a webservice (this is what I don't want to do)
* Use serverless functions, e.g. Azure Functions or AWS lambda functions (sure, we could do that)
* Do it the SPA way *with blazor magic* (we make use of the javascript interoperability of blazor)

I decided to go with option 3. Feel free and share your experiences :)

## MSAL.js
I'm going to use msal.js (https://github.com/AzureAD/microsoft-authentication-library-for-js/tree/dev/lib/msal-core) (docs under https://docs.microsoft.com/de-de/azure/active-directory/develop/msal-js-initializing-client-applications) and include it within my project. 

I created my javascript interop (https://docs.microsoft.com/de-de/aspnet/core/blazor/javascript-interop?view=aspnetcore-3.1) code for the exchange of the sign-in status, to update the UI. 

I'm not going to step into deep into blazor javascript interop at this point, but the shared listings should give you an idea, about the usage (if you want me to do a bit more details about blazor javascript interop, feel free to reach out and let me know).

```javascript
// configuration to initialize msal
const msalConfig = {
    auth: {
        clientId: "", //This is your client ID
        authority: "https://login.microsoftonline.com/common", //This is your tenant info
        redirectURI: ""
    },
    cache: {
        cacheLocation: "localStorage",
        storeAuthStateInCookie: true
    }
};
// instantiate MSAL
const myMSALObj = new Msal.UserAgentApplication(msalConfig);
// request to signin - returns an idToken
var requestObj = {
    scopes: ["user.read"]
};


// signin and acquire a token silently with POPUP flow. Fall back in case of failure with silent acquisition to popup
function signIn(session) {
    myMSALObj.loginPopup(requestObj).then(function (loginResponse) {
        // Call Blazor Code, if needed
        session.invokeMethodAsync('BlazorJSInteropSample', 'someParameterData')
        .then((message) => {
            console.log(message);
        });

    }).catch(function (error) {
        console.log(error);
    });
}

// signout the user
function logout(session) {
    // Removes all sessions, need to call AAD endpoint to do full logout
    myMSALObj.logout();
  }

// Blazor jsinterop functions:
window.signIn = signIn;
window.logout = logout;
```

With that code, we can login the user, get the user object and can also request for a jwt token, to make authorized calls (e.g. against a AWS lambda function).

To take the token or the data into your *C#* code, you call the code from javascript. A sample code is provided below.
```csharp
//Includ JSRuntime
 private readonly IJSRuntime _jsRuntime;
.
.
.
//Initialize JSRuntime
 public JSInteropClass(IJSRuntime jsRuntime)
{
            _jsRuntime = jsRuntime;
}
.
.
.
//Call of the JSFunction window.logout
public async void SignOut(){
            if(_jsRuntime != null)
                await _jsRuntime.InvokeVoidAsync("logout", this);
            ClearSessionData();
        } 
.
.
.
//Callable CSharp method
[JSInvokable("BlazorJSInteropSample")]
        public void BlazorJSInteropSample(string data){
            //Do what you need
        }
```

# Summary Blazor WASM set up (AZURE AD B2C PART)
Yeah, know you can use authentication and authorization (at least you should get an idea).
We did in this section:
* Set up Azure AD B2C (follow the instruction in the Azure documentation)
* Use MSAL.js to establish an authentication flow
* Work with the user object and pass it token/user object to blazor C# methods through javascript interop.

Still, no server needed. Still serverless. Still free!