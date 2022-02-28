# Android Integration

## Installation

Download our github repository for android repo.

Add Repositories in your Project build.gradle
```
String storageUrl = System.env.FLUTTER_STORAGE_BASE_URL ?: "https://storage.googleapis.com"
    repositories {
        maven {
            url 'github repo path you downloaded'
        }
        maven {
            url "$storageUrl/download.flutter.io"
        }
        ...
    }
```
Add Dependency in your app build.gradle
```
dependencies {
    implementation 'sdk.deepvue.tech.offline_aadhaar_ekyc:flutter_release:1.0'
    ...
}
```
Open you Manifest File and add below activity
```
        <activity
            android:name="io.flutter.embedding.android.FlutterActivity"
            android:configChanges="orientation|keyboardHidden|keyboard|screenSize|locale|layoutDirection|fontScale|screenLayout|density|uiMode"
            android:exported="true"
            android:hardwareAccelerated="true"
            android:theme="@style/Theme.AppCompat"
            android:windowSoftInputMode="adjustResize" />
```
Copy **OkycSdkHandler.kt** and paste it in your app
## Usage

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