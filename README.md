# Deepvue Aadhaar Offline e-KYC Android SDK

Aadhaar Paperless Offline eKYC is a secure and shareable document which can be used by any Aadhaar holder for offline verification of identification. The Aadhaar Offline document can be obtained from the UIDAI website. This SDK provides a simple plugin to your mobile App which allows the user to seamlessly share their offline Aadhaar file with the service provider. 

The Aadhaar Offline file will be validated for its digital signature and the KYC data of The Aadhaar holder will be passed to the integrating App as JSON data.


# Table Of Content

- [Prerequisite](#prerequisite)
- [Setup](#setup)
- [Usage](#usage)
- [Failure Status Codes](#failure-status-codes)
- [Help](#help)

## Prerequisite

You will need valid credentials to use the Deepvue Aadhaar Offline e-KYC React Native SDK, which can be obtained by contacting `hello@deepvue.tech` 

## Setup

#### Android
1. Download our Android dependencies from [here](https://deepvue-public-storage.s3.ap-south-1.amazonaws.com/offline-aadhaar-ekyc/android/v0.0.2/deepvue-okyc-android-plugin.zip).

2. Extract above dependencies locally in your system.

3. Add below Repositories in your `project.build.gradle`
```
repositories {
    maven {
        url 'path to downloaded android dependencies' //e.g. '/home/user/Downloads/deepvue-okyc-android-plugin/repo'
    }
    maven {
        url "https://storage.googleapis.com"
    }
    ...
}
```
4. Add Dependency in your `app.build.gradle`
```
dependencies {
    implementation 'sdk.deepvue.tech.offline_aadhaar_ekyc:flutter_release:0.0.2'
    ...
}
```
5. Open you Manifest File and add below activity
```
<activity
    android:name="io.flutter.embedding.android.FlutterActivity"
    android:configChanges="orientation|keyboardHidden|keyboard|screenSize|locale|layoutDirection|fontScale|screenLayout|density|uiMode"
    android:exported="true"
    android:hardwareAccelerated="true"
    android:theme="@style/Theme.AppCompat"
    android:windowSoftInputMode="adjustResize">
</activity>
...
```
5. Copy below files and add to your `app` alongside `MainApplication.java` file
    - [OkycSdkHandler.java](https://github.com/deepvue-tech/deepvue-aadhaar-offline-ekyc-android-sdk/blob/master/android/OkycSdkHandler.java)
    - [OkycSdkHandlerCallback.java](https://github.com/deepvue-tech/deepvue-aadhaar-offline-ekyc-android-sdk/blob/master/android/OkycSdkHandlerCallback.java)

## Usage
You can use below code to trigger SDK from your application on a button click or a similar event.

```kotlin
 OkycSdkHandler(
                baseUrl = "base-url",
                clientId = "client-id",
                clientSecret = "client-secret",
                useFaceMatch = true,
                imageUrl = "image-url",
                callback = object : Callback {
                    override fun onFailure(code: Int) {
                        // On Failure Code
                    }

                    override fun onSuccess(response: String) {
                       // On Success Response
                    }
                }
            ).startSdk(context)

```
## Failure Status Codes
Following error codes will be returned on the `onFailure` method of the callback

| CODE | DESCRIPTION                  |
| ---- | ---------------------------- |
| 801  | SDK Invalid Credentials             |
| 802  | Permission Denied       |
| 803  | User Interrupted            |
| 804  | No Internet Available |
| 805  | Network Error         |
| 806  | OTP Limit Exceeded       |
| 807  | Mobile Number Not Linked to Aadhaar             |
| 808  | File Download Failed 
| 809  | File Upload Failed |
| 810  | Face Match Failed            |
| 404  | UIDAI Website Server Down            |


## Help
For any queries/feedback, contact us at `hello@deepvue.tech` 
