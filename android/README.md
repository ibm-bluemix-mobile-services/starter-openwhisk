<img src="https://bluemixassets.eu-gb.mybluemix.net/api/Products/image/logos/whisk.svg?key=[starter-openwhisk]&event=readme-image-view" alt="OpenWhisk Logo" width="200px"/>

## OpenWhisk
Bluemix Mobile Starter for OpenWhisk in Android Java

[![](https://img.shields.io/badge/bluemix-powered-blue.svg)](https://bluemix.net)
[![](https://img.shields.io/badge/platform-android-lightgrey.svg?style=flat)](https://developer.android.com/index.html)

### Table of Contents
* [Summary](#summary)
* [Requirements](#requirements)
* [Configuration](#configuration)
* [Run](#run)
* [License](#license)

### Summary

The Bluemix Mobile Starter for OpenWhisk will showcase how you can invoke OpenWhisk actions from a Mobile App.
It  contains a sample OpenWhisk action `actions/pushAction.js` that will trigger a push notification from OpenWhisk and notifiy the Mobile App that invoked it.

### Requirements
* Android Studio
* OpenWhisk Auth Header

### Configuration
* [Bluemix OpenWhisk](https://bluemix.net/openwhisk/cli)

### Setup the OpenWhisk.

For OpenWhisk setup, you need to get authentication from [Bluemix OpenWhisk](https://bluemix.net/openwhisk/cli). Install OpenWhisk CLI and Auth.

After following the instructions to configure your openwhisk CLI, navigate to `app\res\values\open_whisk_credentials.xml` and use the same entire string value at the end of that CLI call to set the `auth header`.

#### Create Whisk Action

If you plan on enabling push notifications in your Android app, you must follow the [Firebase configuration settings](bluemix.net/docs/services/mobilepush/c_android_enable.html). Mainly adding the 2 package names to your Firebase console and updating the google-play-services.json in your Android app. Start at "Complete the following steps using the Firebase Cloud Messaging (FCM) console."

Once complete, use the following WSK CLI command to create your push action in OpenWhisk. Don't worry about editing the js file, your push instance app secret has been populated automatically.

```
wsk action update pushAction actions/pushAction.js
```

To see the fully qualified name, run in the CLI:

```
wsk action get --summary pushAction
```

Qualified names are formatted by `/namespace/package/action(or trigger)` name.

Again, ensure you have obtained your auth header correctly:

```
authHeader = long string after -auth, formatted like openwhisk appid:auth password
```

Please set the entire auth header accordingly in the `app\res\values\open_whisk_credentials.xml` (as mentioned above), the namespace will be picked up from your auth key.

### Run
After importing into Android Studio, build and run the generated mobile application. You will be greeted with a list of your personal namespace's OpenWhisk actions. Select an action and see the response displayed in real time.

### License
This package contains code licensed under the Apache License, Version 2.0 (the "License"). You may obtain a copy of the License at http://www.apache.org/licenses/LICENSE-2.0 and may also view the License in the LICENSE file within this package.
