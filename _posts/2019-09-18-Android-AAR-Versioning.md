---
title: Android AAR versioning
layout: post
summary: Android AAR Library 버전 정보 입력
---
### build.gradle 작성
~~~java
android {
    compileSdkVersion 28
    defaultConfig {
        minSdkVersion 21
        targetSdkVersion 28
        versionCode 1
        versionName "1.1.0"
    }

    buildTypes {
        release {
            project.archivesBaseName='com.sori.sdk'
            minifyEnabled false
        }
    }

    libraryVariants.all {
        variant -> variant.outputs.all {
            output -> if (outputFile != null && outputFileName.endsWith('.aar')) {
                outputFileName = "${archivesBaseName}-${defaultConfig.versionName}.aar"
            }
        }
    }
}
~~~

### output
```
com.sori.sdk-1.1.0.aar
```
