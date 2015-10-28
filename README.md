# CalendarQuickStart

A sample and tutorial demonstrating the use of the Google Calendar API

## Getting started

After reading this tutorial, you should be able to have a working Android
project that uses the Google Calendar API. This tutorial assumes that you're
using [Android Studio] (SDK 1.1 or later), as well as API 22 or later and the
Google Play Services.

> Google Play Services is a set of APIs to allow app developers to take advantage
> of existing Google products (like Gmail, Calendar and Maps) in their own mobile
> applications and possibly enriching the user experience and ability to share
> content.

Read more about it [here].

### Project setup

First of all, open Android Studio to create your app. Enter the _application
name_ and _company domain_, like `yourdomain.com` and the IDE will automatically
setup the project's package name.

Click "Next", target **Phone and Tablet** and preferably select the latest SDK
version (make sure it is API 11 or later!). Then select **Blank Activity** and
finish the wizard.

Now, with the project open on the IDE, open the `build.gradle` file (make sure
it is the module one), now add the following lines to the `dependencies` block:

```groovy
compile 'com.google.android.gms:play-services:6.5.87'
compile 'com.google.apis:google-api-services-calendar:v3-rev119-1.19.1'
compile 'com.google.api-client:google-api-client:1.19.1'
compile 'com.google.api-client:google-api-client-android:1.19.1'
compile 'com.google.api-client:google-api-client-gson:1.19.1'
```

Now right-click the `build.gradle` file in the file navigator and click
"Synchronize `buld.gradle`".

###### Permissions and Manifest File

Now open your `AndroidManifest.xml` file and add the following code right after
the `manifest` tag.

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

On to the next phase, when you will learn to setup the Google Calendar API, to
finally make it all work!

### API setup

Now, you need to get a `SHA1` fingerprint:

`keytool -exportcert -alias androiddebugkey -keystore ~/.android/debug.keystore -list -v`

Enter the password of your choosing and copy the `SHA1` key. This key is gonna
be useful throughout the development of your app but you **CAN'T** use it for
production mode.

Go to your [Google Developers Console] and enable the Calendar API. After the
setup is done, click on the "Consent screen" link, enter an email address and
product name and save it!

After that, click on the "Credentials" link and press "Create new Client ID".
Select the option "Installed application", this is the one you need when developing
a native mobile app, and also select _Android_ as the installed application type.

Enter the package name you obtained in the [Project setup phase], and enter your
generated `SHA1` fingerprint. Now click "Create Client ID".

### Run the app

Now that you have created the app and connected it to the Calendar API, go to
the "Run" menu and click *Run app*! You can either plug your device to the computer
and run the app on it or you can run it on the emulator (we ran it on a Nexus
5 5.1 emulator). Anyway, you gotta have Google Plays services installed in the
system (in case you missed it, go to `Tools -> Android -> SDK Manager`, search
for Google Play Services SDK and install it).

If you receive any error until this step, please submit an [issue] and we'll
try help you as soon as possible.

## Usage Flow

Now with the app installed on our device, we're going to experience the Google
Calendar API usage by fetching our existing events from our Google account.
If you don't have a gmail account, please create one.

![Android01](https://cloud.githubusercontent.com/assets/7546651/7891878/7a447540-0626-11e5-9556-1a337d030190.png)

* Click on _CalendarQuickStart App_ to launch the app

![Android02](https://cloud.githubusercontent.com/assets/7546651/7891879/802d1534-0626-11e5-9e9d-a52494a627dc.png)

* Enter your email and click _NEXT_

![Android03](https://cloud.githubusercontent.com/assets/7546651/7891882/83cbc6b8-0626-11e5-932a-94b606ac76d5.png)

* Enter your password and click _NEXT_

![Android04](https://cloud.githubusercontent.com/assets/7546651/7891884/872c7942-0626-11e5-983f-778a2b8bed3a.png)

* Click _ACCEPT_, this will allow the app to fetch your calendar data from your
Google account.

![Android05](https://cloud.githubusercontent.com/assets/7546651/7891887/8ad735b4-0626-11e5-840a-1744f8790b2d.png)

* Click _MORE_

![Android05](https://cloud.githubusercontent.com/assets/7546651/7891888/8f0b1af6-0626-11e5-8cb6-a2e407625972.png)

* Click _NEXT_

![Android06](https://cloud.githubusercontent.com/assets/7546651/7891892/92d73656-0626-11e5-9c80-2189156c88ba.png)

* Choose your account and click _OK_

![Android07](https://cloud.githubusercontent.com/assets/7546651/7891895/979ac2e8-0626-11e5-83ad-d79277841b5e.png)

* Accept permissions by clicking on _OK_

![Android08](https://cloud.githubusercontent.com/assets/7546651/7891899/9f619e8e-0626-11e5-9cbf-900ef81b5661.png)

* Existing events are returned in plain text. The *CalendarQuickStart* app has
successfully downloaded your events through.

![Desktop](https://cloud.githubusercontent.com/assets/7546651/7891903/a738d988-0626-11e5-99e9-657fde173c05.png)
__Calendar Gmail screenshot__

##### Further Reading for Google Calendar API

If you got hooked and feel like going beyond this tutorial with Calendar integration
(creating and updating events from your app, perhaps?), then you should definitely
take a look at these links:

+ [Quick start](https://developers.google.com/google-apps/calendar/quickstart/android)
+ [API reference](https://developers.google.com/google-apps/calendar/v3/reference/)
+ [Create events](https://developers.google.com/google-apps/calendar/create-events)

##### Contact

* Miguel Araújo <mra2@cin.ufpe.br>
* Rodrigo Alves <rav2@cin.ufpe.br>

### License

See LICENSE file.

[issue]: https://github.com/miguelarauj1o/CalendarQuickStart/issues
[Android Studio]: http://developer.android.com/tools/studio/index.html
[here]: https://developers.google.com/android/guides/overview
[Google Developers Console]: https://console.developers.google.com/start/api?id=calendar
[Project setup phase]: #project-setup
