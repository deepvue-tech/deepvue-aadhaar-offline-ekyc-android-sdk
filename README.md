# Deepvue Aadhaar Offline e-KYC Android SDK
![version](https://img.shields.io/badge/version-v0.4-blue)

Aadhaar Paperless Offline eKYC is a secure and shareable document which can be used by any Aadhaar holder for offline verification of identification. The Aadhaar Offline document can be obtained from the UIDAI website. This SDK provides a simple plugin to your mobile App which allows the user to seamlessly share their offline Aadhaar file with the service provider. 

The Aadhaar Offline file will be validated for its digital signature and the KYC data of The Aadhaar holder will be passed to the integrating App as JSON data.

# Table Of Content

- [Prerequisite](#prerequisite)
- [Android SDK Requirements](#android-sdk-requirements)
- [Download](#download)[Using maven repository](#using-maven-repository)
- [Setup](#setup)
- [Permissions](#permissions)
- [Quick Start](#quick-start)
- [Aadhar Offline Result](#handling-the-result)

- [Help](#help)

## Prerequisite


You will need valid credentials to use the Deepvue Aadhaar Offline e-KYC Android SDK, which can be obtained by contacting `hello@deepvue.tech` 


## Android SDK Requirements

**Minimum SDK Version** -  **19** or higher

## Download

#### Using maven repository

Add the following code to your `project` level `build.gradle` file

```groovy
allprojects {

    repositories {
          maven { url 'https://jitpack.io' }
    }

}
```

After that, add the following code to your `app` level `build.gradle` file
```groovy

// ...

dependencies {

    /* Dependencies for Deepveu Aadhaar Offline SDK */
    implementation 'androidx.appcompat:appcompat:<lastest verison>'
    
    implementation 'com.google.android.material:material:<lastest verison>'
   
    // Deepvue aadhar offline core dependency
    implementation 'com.github.deepvue-tech:deepvue-aadhaar-offline-ekyc-android-sdk:<lastest verison>'
   
}
```

## Setup

#### Permissions

Deepvue Aadhaar Offline SDK requires the following permission to operate properly

```xml
<manifest xmlns:android="http://schemas.android.com/apk/res/android" package="your.package.name" >

    <uses-permission android:name="android.permission.INTERNET" />  
    <uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />    
    
    <application>
      ...
    </application>

</manifest>
```
## Quick Start

#### Initiating the Deepvue Aadhaar Offline SDK

Initialize the `Deepvue Aadhaar Offline SDK` instance with the appropriate configurations to invoke the Deepvue Aadhaar Offline SDK


```java
public class MainActivity extends AppCompatActivity {

    // ...
    
    /* (OPTIONAL)  Enter the DeepvueAadharOffline API credentials here */
    private String DEEPVUE_AADHAR_OFFLINE_API_BASE_URL = "ENTER_BASE_URL_HERE"
            , DEEPVUE_AADHAR_OFFLINE_CLIENT_ID = "ENTER_API_KEY_ID_HERE"
            , DEEPVUE_AADHAR_OFFLINE_CLIENT_SEC = "ENTER_API_KEY_SEC_HERE";
   
    
        private fun startKycWithoutFaceMatch() {
        //for KYC without facematch
        AadharOfflineSDK.initialiseSDK(
            DEEPVUE_AADHAR_OFFLINE_API_BASE_URL,
            DEEPVUE_AADHAR_OFFLINE_CLIENT_ID,
            DEEPVUE_AADHAR_OFFLINE_CLIENT_SEC
        ).setLanguage(AadharOfflineSDK.Languages.en)
            .start(this@MainActivity, this)

    }

    @SuppressLint("MissingPermission")
    private fun startKycWithFaceMatch() {
        // for KYC without facematch need camera(mandatory) and storage(below android 11) permission
        AadharOfflineSDK.initialiseSDK(
            DEEPVUE_AADHAR_OFFLINE_API_BASE_URL,
            DEEPVUE_AADHAR_OFFLINE_CLIENT_ID,
            DEEPVUE_AADHAR_OFFLINE_CLIENT_SEC
        )
            .setFaceMatch(true)
            .setLanguage(AadharOfflineSDK.Languages.en)
            .start(this@MainActivity, this)

    }

    // ...

}
```

#### Handling the result

Your activity must implement `AadharOfflineResultCallback` to receive the result.

```java
    // ...
    override fun onFailure() {
        Toast.makeText(this, "Some error occurred", Toast.LENGTH_SHORT).show()
    }

    override fun onKycSuccessResult(result: UploadXMLResponse) {
        Toast.makeText(this, "KYC Success: ${result.aadhaar.name}", Toast.LENGTH_SHORT).show()
    }
    // ...
```

## DeepvueAadharOfflineResult
The result is obtained through the `result` object 

## Help
For any queries/feedback, contact us at `help@deepvue.tech` 
