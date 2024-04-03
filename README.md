<p align="center">
  <img alt="CometChat" src="https://assets.cometchat.io/website/images/logos/banner.png">
</p>

# CometChat Cordova Ionic SDK

CometChat enables you to add voice, video & text chat for your website & app.
This guide demonstrates how to add chat to an Ionic App using CometChat.



## Prerequisites :star:
Before you begin, ensure you have met the following requirements:<br/>
 ✅ &nbsp; You have [`Visual Studio Code`](https://code.visualstudio.com/) or any other code editor installed in your machine.<br/>
 ✅ &nbsp; To run native projects you will need to have [`Android Studio`](https://capacitorjs.com/docs/android) & [`Xcode`](https://capacitorjs.com/docs/ios) installed in your machine.<br/>
 ✅ &nbsp; You have [`npm`](https://www.npmjs.com/get-npm) installed in your machine.<br/>
 ✅ &nbsp; You have read [CometChat Key Concepts](https://prodocs.cometchat.com/docs/concepts).<br/>

<hr/>

## Installing CometChat Cordova Ionic SDK
## Setup :wrench:

To setup Cordova Ionic SDK, you  need to first register on CometChat Dashboard. [Click here to sign up](https://app.cometchat.com/login).

### i. Get your Application Keys :key:

<a href="https://app.cometchat.io" target="_blank">Signup for CometChat</a> and then:

1. Create a new app: Click **Add App** option available  →  Enter App Name & other information  → Create App
2. At the Top in **QuickStart** section you will find **Auth Key** & **App ID** or else you can head over to the **API & Auth Keys** section and note the **Auth Key** and **App ID**
<img align="center" src="https://files.readme.io/4b771c5-qs_copy.jpg"/>

<hr/>

### ii. Add the CometChat Dependency
<ul>
<li>
<b>Install via NPM</b><br/>
1. Run the following command to install the CometChat Cordova Ionic SDK<br/>

```javascript
	npm install @cometchat/chat-sdk-ionic@4.0.0 --save
```

 You can refer to the below link for instructions on how to do so:<br/>
[📝 Add CometChat Dependency](https://prodocs.cometchat.com/docs/cordova-ionic-quick-start#add-the-cometchat-dependency)
</li>
</ul>
<hr/>

## Configure CometChat Cordova Ionic SDK

### i. Initialize CometChat 🌟
We suggest you call the init() method on app startup, preferably in the index.js file.

```javascript
var appID = "APP_ID";
var region = "REGION";
var appSetting = new CometChat.AppSettingsBuilder().subscribePresenceForAllUsers().setRegion(region).build();
CometChat.init(appID, appSetting).then(
  () => {
    console.log("Initialization completed successfully");
  },
  error => {
    console.log("Initialization failed with error:", error);
  }
);
```

| :information_source: &nbsp; <b> Note: Make sure to replace `region` and `appID` with your credentials.</b> |
|------------------------------------------------------------------------------------------------------------|

### ii. Create User 👤
Once initialisation is successful, you will need to create a user. You need to use createUser() method to create user on the fly.
```javascript
let authKey = "AUTH_KEY";
var uid = "user1";
var name = "Kevin";

var user = new CometChat.User(uid);

user.setName(name);

CometChat.createUser(user, authKey).then(
  user => {
    console.log("user created", user);
  },error => {
    console.log("error", error);
  }
);
```
>:information_source: <b>Note: Make sure that UID and name are specified as these are mandatory fields to create a user.</b>
<hr/>

### iii. Login User 👤
Once you have created the user successfully, you will need to log the user into CometChat using the login() method.
```javascript
var UID = "SUPERHERO1";
var authKey = "AUTH_KEY";

CometChat.getLoggedinUser().then(
  user => {
    if(!user){
      CometChat.login(UID, authKey).then(
        user => {
          console.log("Login Successful:", { user });    
        },
        error => {
          console.log("Login failed with exception:", { error });    
        }
      );
    }else{
      // User already logged in
    }
  }, error => {
    console.log("getLoggedinUser failed with exception:", { error });
  }
);
```

| :information_source: &nbsp; <b>Note - The login() method needs to be called only once. Also replace AUTH_KEY with your App Auth Key.</b> |
|------------------------------------------------------------------------------------------------------------|

## Help and Support
For issues running the project or integrating with our UI Kits, consult our [documentation](https://www.cometchat.com/docs/ionic-cordova-capacitor-chat-sdk/overview) or create a [support ticket](https://help.cometchat.com/hc/en-us) or seek real-time support via the [CometChat Dashboard](https://app.cometchat.com/).
