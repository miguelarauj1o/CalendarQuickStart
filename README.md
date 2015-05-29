# CalendarQuickStart

A sample and tutorial demonstrating the use of the Google Calendar API

## Getting started

After reading this tutorial, you should be able to have a working Android project that uses the Google Calendar API. This tutorial assumes that you're using [Android Studio] (SDK 1.1 or later), as well as API 22 or later and the Google Play Services.

### Project setup

First of all, open Android Studio to create your app. Enter the _application name_ and company domain, like `yourdomain.com` and the IDE will automatically setup the project's package name.

Click "Next", target **Phone and Tablet** and preferably select the latest SDK version (make sure it is API 11 or later!). Then select **Blank Activity** and finish the wizard.

Now, with the project open on the IDE, open the `build.gradle` file (make sure it is the module one), now add the following lines to the `dependencies` block:

```groovy
compile 'com.google.android.gms:play-services:6.5.87'
compile 'com.google.apis:google-api-services-calendar:v3-rev119-1.19.1'
compile 'com.google.api-client:google-api-client:1.19.1'
compile 'com.google.api-client:google-api-client-android:1.19.1'
compile 'com.google.api-client:google-api-client-gson:1.19.1'
```

Now right-click the `build.gradle` file in the file navigator and click "Synchronize `buld.gradle`".

###### Permissions and Manifest File

Now open your `AndroidManifest.xml` file and add the following code right after the `manifest` tag.

```xml
<uses-permission android:name="android.permission.INTERNET" />
<uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
<uses-permission android:name="android.permission.GET_ACCOUNTS" />
```

And add the following code right before closing the `application` tag:

```xml
<meta-data
    android:name="com.google.android.gms.version"
    android:value="@integer/google_play_services_version" />
```

On to the next phase, when you will learn to setup the Google Calendar API, to finally make it all work!

### API setup

Now, you need to get a SHA1 fingerprint:

`keytool -exportcert -alias androiddebugkey -keystore ~/.android/debug.keystore -list -v`

Enter the password of your choosing and copy the `SHA1` key. This key is gonna be useful throughout the development of your app but you **can't** use it for production mode.

Go to your [Google Developers Console] and enable the Calendar API. After the setup is done, click on the "Consent screen" link, enter an email address and product name and save it!

After that, click on the "Credentials" link and press "Create new Client ID". Select the option "Installed application", this is the one you need when developing a native mobile app, and also select _Android_ as the installed application type.

Enter the package name you obtained in the [Project setup phase], and enter your generated SHA1 fingerprint. Now click "Create Client ID".

### Run the app

Now that you have created the app and connected it to the Calendar API, go to the "Run" menu and click *Run app*! You can either plug your device to the computer and run the app on it or you can run it on the emulator. Anyway, you gotta have Google Plays services installed in the system.

## Usage Flow

##### Further Reading for Google Calendar API

+ Quick start
+ API reference
+ Create events

##### Contact

* Rodrigo Alves <rav2@cin.ufpe.br>
* Miguel Araújo <mra2@cin.ufpe.br>

### License

MIT License

[Android Studio]: http://developer.android.com/tools/studio/index.html
[Google Developers Console]: https://console.developers.google.com/start/api?id=calendar
[Project setup phase]: #project-setup
[Quick start]: https://developers.google.com/google-apps/calendar/quickstart/android
[API reference]: https://developers.google.com/google-apps/calendar/v3/reference/
[Create events]: https://developers.google.com/google-apps/calendar/create-events
