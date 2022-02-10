# Pluto
[![Maven Central](https://maven-badges.herokuapp.com/maven-central/com.mocklets/pluto/badge.svg)](https://maven-badges.herokuapp.com/maven-central/com.plutolib/pluto)
[![CLA assistant](https://cla-assistant.io/readme/badge/mocklets/pluto)](https://cla-assistant.io/mocklets/pluto)
[![Daily Builds](https://github.com/mocklets/pluto/actions/workflows/daily_builds.yml/badge.svg)](https://github.com/mocklets/pluto/actions/workflows/daily_builds.yml)

Pluto is a on-device debugger for Android applications, which helps in inspection of HTTP requests/responses, capture Crashes and ANRs and manipulating application data on-the-go.

It comes with a UI to monitor and share the information, as well as APIs to access and use that information in your application.


<p align="center">
  <img src="https://firebasestorage.googleapis.com/v0/b/pluto-web/o/pluto_summary_gif.gif?alt=media" alt="pluto demo" width="35%"/>
</p>

-----

## Integrate Pluto in your application



### Add Gradle Dependencies

Pluto is distributed through [***mavenCentral***](https://search.maven.org/artifact/com.plutolib/pluto). To use it, you need to add the following Gradle dependency to your build.gradle file of you android app module.



> Note: add both the pluto and the pluto-no-op variant to isolate Pluto from release builds.
```groovy
dependencies {
  debugImplementation 'com.mocklets:pluto:1.2.0'
}
```


### Intialize Pluto

Now to start using Pluto, intialize Pluto SDK from you application class by passing context to it.
```kotlin
Pluto.Installer(this)
  .addPlugin(DemoPlugin("demo_id"))
  .install()
```


### Add Pluto Logs

Pluto allows you to log and persist the user journey through the app, and help debug them without any need to connect to Logcat.
```kotlin
PlutoLog.event("analytics", eventName, HashMap(attributes))
PlutoLog.d("debug_log", "button clicked")
PlutoLog.e("error_log", "api call falied with http_status 400")
PlutoLog.w("warning_log", "warning log")
PlutoLog.i("info_log", "api call completed")
```

But if you are connected to Logcat, PlutoLogs behave similar to Log class, with an improvement to tag the method and file name also. In Logcat, PlutoLogs will look like the following.
```
D/onClick(MainActivity.kt:40) | debug_log: button clicked
E/onFailure(NetworkManager.kt:17) | error_log: api call falied with http_status 400
```

🎉 You are all done!

Now re-build and run your app, you will receive a notification from Pluto, use it to access Pluto UI.

***


## Contribution

**We're looking for contributors, help us improve Pluto.** 😁 

Please refer to your [`Contribution guidelines`](/CONTRIBUTING.md) to get started.

***


## License

```
Copyright 2021 Plutolib.

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

   http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.
```
