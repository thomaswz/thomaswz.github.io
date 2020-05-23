# Firebase

###### Created 17 May 2020, Updated 17 May 2020

## Overview

This is one of the best tool on the web to move from a front-end developer to building a full app. It is basically a 3/4 developer... as the 1/4 of setting up a back end server is not necessary.

## Functions

Functions are built on a local host and then sent to firebase.

## Setup

Part of the local host setup is confusing, and I have not been able to completly set it up.  
This is because I can't get the local emulators to work on initial setup. It references ports localhost:5001 and localhost:8000, but then when I researched further - I found this:

- [Firebase Emulators](https://firebase.google.com/docs/emulator-suite/connect_and_prototype?authuser=0&database=RTDB#web)

which required this setup: to be saved in a file `emulator-suite.js`

```javascript
if (location.hostname === 'localhost') {
  var firebaseConfig = {
    // Point to the RTDB emulator running on localhost.
    // In almost all cases the ns (namespace) is your project ID.
    databaseURL: 'http://localhost:9000?ns=YOUR_DATABASE_NAMESPACE',
  };

  var myApp = firebase.initializeApp(firebaseConfig);
  var db = myApp.database();
}
```

Then it further recommends this for Realtime Database in the same file: `firebase.functions().useFunctionsEmulator("http://localhost:5001")`

The code to invoke the emulators is:  
`firebase emulators:start --only database,functions`

and for test scripts:  
`firebase emulators:exec --only functions,database "./testdir/test.sh"`

## Security Rules testing:

In the browser:
`http://localhost:9000/.inspect/coverage?ns=` and then for the actual rules:
`http://localhost:9000/.inspect/coverage.json?ns=`
