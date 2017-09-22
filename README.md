# iuneed

Marketplace - Sharing Furniture
PWA using polymer

The following app was made in order to approach an in a short amount of time MVP 
at #AllStartup19 
Madrid, Spain

[DEMO](https://youget-it.firebaseapp.com/)

### Team: 

Cinta Martinez - CMO

Marco Tabasco - CTO

Carlos Jimenez - Business

Oscar - CEO

Juan Garassino - UX


### Setup

##### Prerequisites

Install [polymer-cli](https://github.com/Polymer/polymer-cli):

    npm install -g polymer-cli


##### Setup
    # Using CLI
    mkdir iuneed
    cd iuneed
    polymer init shop

    # Or cloning direct from GitHub
    git clone https://github.com/mtabasco/get-it.git
    cd iuneed
    bower install

### Start the development server

    polymer serve

### Run web-component-tester tests

    polymer test

### Build

Build presets provide an easy way to define common build configurations in your `polymer.json` file. There are 2 build presets we put in `polymer.json` file in Shop:

**es5-bundled**

- js: {minify: true, compile: true}
- css: {minify: true}
- html: {minify: true}
- bundle: true
- addServiceWorker: true
- addPushManifest: true
- insertPrefetchLinks: true

**es6-unbundled**

- js: {minify: true, compile: false}
- css: {minify: true}
- html: {minify: true}
- bundle: false
- addServiceWorker: true
- addPushManifest: true
- insertPrefetchLinks: true

Run the command to build the presets:

    polymer build

### Test the build

This command serves the `es5-bundled` build version of the app:

    polymer serve build/es5-bundled

This command serves the `es6-unbundled` build version of the app:

    polymer serve build/es6-unbundled


### Firebase configuration

This project uses firebase hosting, auth and database features.

##### Prerequisites

Create a Google account. This will be used to create a Firebase project.

https://accounts.google.com/SignUpWithoutGmail

Create a firebase account.

https://console.firebase.google.com/

##### Steps

Create a firebase project through console.

Follow the instructions to add Firebase to the web project. You can get your project API key in the project config section.

    <script src="https://www.gstatic.com/firebasejs/4.3.1/firebase.js"></script>
    <script>
    // Initialize Firebase
    var config = {
        apiKey: "xxxx",
        authDomain: "youget-it.firebaseapp.com",
        databaseURL: "https://youget-it.firebaseio.com",
        projectId: "youget-it",
        storageBucket: "",
        messagingSenderId: "831517451524"
    };
    firebase.initializeApp(config);
    </script>

Hosting

Follow the tutorial for host the web app. From command prompt in local computer, in the folder you had download git code:

$ npm install -g firebase-tools

Login to Google account: $ firebase login
Start project: $ firebase init

  Select Firebase hosting when asked
  
  Select the project you have created
  
  Firebase asks you the name of your app's public folder. Enter build/es5-bundled/

  Edit your firebase configuration to add support for URL routing. Add the following to the hosting object in your firebase.json file.

    "rewrites": [
    {
        "source": "!/__/**",
        "destination": "/index.html"
    },
    {
        "source": "**/!(*.js|*.html|*.css|*.json|*.svg|*.png|*.jpg|*.jpeg)",
        "destination": "/index.html"
    }
    ]

  For example, your firebase.json file may look like this afterwards:

    {
        "database": {
            "rules": "database.rules.json"
        },
        "hosting": {
            "public": "build/es5-bundled/",
            "rewrites": [
            {
                "source": "!/__/**",
                "destination": "/index.html"
            },
            {
                "source": "**/!(*.js|*.html|*.css|*.json|*.svg|*.png|*.jpg|*.jpeg)",
                "destination": "/index.html"
            }
            ]
        }
    }

Upload files to firebase (deploy):

$ firebase deploy


