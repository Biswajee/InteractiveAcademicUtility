# Interactive Academic Utility for COVID 19 Solution Challenge

The repository contains a gesture driven interactive quiz system with grading service and a news reader service. 
The application can be extensively used as a tool to teach students using only voice and gestures without interacting with any surface. The software 
can also be deployed to monitor quarantined patients in hospitals and to obtain health surveys and the software can even read out most recent news for patients. 
Since, the survey questions, results are stored in cloud, there's no need to manually retrieve survey data from the deployed system or update the survey questions.   

## Prerequisites

The InteractiveAcademicUtility Application uses :
+ Maven Java (for dependencies and application)
+ Python (for image processing)
  + OpenCV (image processing library)
+ Android (for implementing some features like Gson, which isn't available on Maven)
+ IBM Cognitive Services (Watson: text-to-speech SDK)
+ Firebase services used :
  + Firebase Realtime Database (storing test-scores of users)
  + Firebase Admin SDK
  + Firebase Auth (Authenticating into the client platform)


## Installation and running

First, **clone** the repository using command :
`git clone https://github.com/Biswajee/InteractiveAcademicUtility.git`

Make sure you are running **JAVA 8** on your system. If not, head over to install the right one for yourself [here](https://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html).

Install **Android SDK** in your system. This will be required since the application uses certain functionalities available with _android java_ but not in _maven java_.

If you are done, you need to have **python 3.6** installed now and set as your default python program in your environment variable of your system.

Wait, there is still a few more things to do with your newly installed python:

+ Make sure you have pip installed along with python
+ Install the following python libraries using `pip`
  + cv2
  + pyaudio [not implemented]
  + numpy
  + copy

Once you have them installed, perform this:
`pip install --upgrade "watson-developer-cloud>=2.4.1"`

For more information on watson-developer-cloud sdk, head [here](https://github.com/watson-developer-cloud/python-sdk).


At this time, running the sample `InteractiveAcademicUtility.jar` supplied in the repository should work without errors.

Incase, you notice erroneous behaviour, start your terminal in the repository directory and type : `java -jar InteractiveAcademicUtility.jar`.

Please create an _**issue**_ incase you find errors during running. The application requires internet connectivity, so make sure you are online while you start the application.

## Grabbing the API Keys - Building from scratch

The Application uses API from **NewsAPI.org**. So, will require one, its free.
Also set up your **IBM Bluemix account** and create a text-to speech resource. Then get the credentials from there.

Now, you need to create a **Keydata.java** file under directory `src/main/java/com/mycompany/jyotimaven`.

Paste this piece of code inside **Keydata.java**:
```
package com.mycompany.jyotimaven;

public class Keydata {

  public static String NEWS_API_KEY = "";
  public static String BLUEMIX_KEY = "";
}
```

## Maven resources - Building from scratch

In **pom.xml**, paste the following: 

```
<dependency>
            <groupId>com.google.firebase</groupId>
            <artifactId>firebase-admin</artifactId>
            <version>6.5.0</version>
</dependency>

<dependency>
            <groupId>com.android.support</groupId>
            <artifactId>appcompat-v7</artifactId>
            <version>27.1.1</version>
            <scope>system</scope>
            <systemPath>G:/Androidsdk/platform-tools/extras/android/m2repository/com/android/support/appcompat-v7/25.3.1/appcompat-v7-25.3.1-sources.jar</systemPath>
</dependency>
```

Set the path accordingly with your _android sdk_. You may have to download the `platform-tools` if required.

### Add Firebase to your app - Building from scratch

We need to configure, firebase-admin sdk now. Head [here](https://github.com/firebase/firebase-admin-java) and [here](https://firebase.google.com/docs/admin/setup) to know how to do it.

More simply, do as directed below :

To use the Firebase Admin SDKs, you'll need a **Firebase project**, a **service account** to communicate with the Firebase service, and a **configuration file** with your _service account's credentials_.

If you don't already have a Firebase project, add one in the **Firebase console**. The Add project dialog also gives you the option to add Firebase to an existing **Google Cloud Platform project**.

Navigate to the **Service Accounts** tab in your **project's settings page**.

Click the **Generate New Private Key** button at the bottom of the Firebase Admin SDK section of the Service Accounts tab.

After you click the button, a **JSON file** containing your service account's credentials will be downloaded.

## Final steps - Building from scratch

You are all set to build the application. Incase, you are running **Netbeans**, do a `clean build` on the project. Now, the resources will get downloaded to your system.

Once completed, you'll have a target folder in your source repository. Pull up the jar that says`...-with-dependencies to the root folder` and run it.

You will need to create your own `audio/` and `images/` directory to provide some necessary resources now. 

**Credits and footnotes**: The solution was developed as a quick hack and resources used were usually on free tier. In order to scale up, the solution will require additional resources in terms of accessing various APIs. I would also like to thank [@lzane](https://github.com/lzane/) for the concise gesture detection algorithm [here](https://github.com/lzane/Fingers-Detection-using-OpenCV-and-Python). Make sure, you check that as well.
