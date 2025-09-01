# kotlinx.datetime

This patch is built on the official kotlinx.datetime version 0.6.5 to support platform OpenHarmony。

# How to publish 

## 1. download kotlinx.datetime
At first, clone offcial kotlin.datetime project in local:

```
git clone https://github.com/Kotlin/kotlinx-datetime.git
```

checkout tag 0.6.5 and create branch:

```
git checkout -b v0.6.5 0.6.5
```

## 2. apply patch

download patch to local, and apply it:

```
git apply kotlinx.datetime.patch
```

## 3. maven configuration

Replace the following `username`, `password`, and `uri` with the corresponding published information.
```
publishing {
   repositories {
        maven {
            credentials {
                username = "xxxxx"
                password = "xxxxx"
            }
            url = uri("xxxxx")
        }
    }
}    
```

and change your own kotlinx.datetime version
```
version = "xxxxx"
```

## 4. publish kotlinx.datetime

after gradle sync, enter kotlinx.datetime project' root path, execute `publish` ，publish kotlinx.datetime to your own maven
```
./gradlew publish
```

# How to import

import kotlinx.datetime in `libs.version.toml`

```
datetimeVersion = "xxxx"

lib-kotlin-datetime = { group = "org.jetbrains.kotlinx", name = "kotlinx-datetime", version.ref = "datetimeVersion" }
```

and implementation in module's `build.gradle.kts`
```
implementation(lib.kotlin.datetime)
```