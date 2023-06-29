# android-publish
android libs publishing template! (Gradle8.0)

use android studio (gradle8.0) publish a android libs to mvn central.

1. apply mvn-gradle8.0.gradle to your libs module (build.gradle)
```gradle
apply plugin: 'com.android.library'
apply from: '../mvn-gradle8.0.gradle' // copy to your libs project
// apply from: 'https://raw.githubusercontent.com/lazy2b/android-publish/master/mvn-gradle8.0.gradle' // or include from here

android {
    namespace 'com.lazylibs.android-publish'
    compileSdk 33
    defaultConfig {
        minSdk 24
        targetSdk 33
        consumerProguardFiles "consumer-rules.pro"
    }
    compileOptions {
        sourceCompatibility JavaVersion.VERSION_1_8
        targetCompatibility JavaVersion.VERSION_1_8
    }
}

dependencies {
    // some dependecies...
}
```
2. create gradle.properties to your libs module
```
VERSION_NAME=0.0.1-SNAPSHOT
VERSION_CODE=1

GROUP=com.lazylibs
ARTIFACT_ID=adser

POM_NAME=lazylibs-adser
POM_PACKAGING=aar
POM_DESCRIPTION=a adjust(.com) target audience identification libs.
POM_URL=https://github.com/lazy2b/LazyAdser
POM_SCM_URL=https://github.com/lazy2b/LazyAdser
POM_SCM_CONNECTION=scm:git:https://github.com/lazy2b/LazyAdser.git
POM_SCM_DEV_CONNECTION=scm:git:https://github.com/lazy2b/LazyAdser.git
POM_LICENCE_NAME=The Apache Software License, Version 2.0
POM_LICENCE_URL=http://www.apache.org/licenses/LICENSE-2.0.txt
POM_LICENCE_DIST=repo
POM_DEVELOPER_ID=lazy2b
POM_DEVELOPER_NAME=jack.rezie
POM_DEVELOPER_EMAIL=rezielibs@gmail.com
```
3. add your mvn username & password to your gobal gradle.properties (~/.gradle/gradle.properties)
4. sync your project and publishing your libs.
exec gradle task : [your-module]/Tasks/publishing/publishMvnCentralReleasePublicationToMavenRepoRepository
