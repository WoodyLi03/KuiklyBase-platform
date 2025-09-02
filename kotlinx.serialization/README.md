# kotlinx.serialization

This patch is built on the official kotlinx.serialization version 1.7.1 to support platform OpenHarmony。

# How to publish 

## 1. download kotlinx.serialization
At first, clone offcial kotlin.serialization project in local:

```
git clone https://github.com/Kotlin/kotlinx.serialization.git
```

checkout tag 1.7.1 and create branch:

```
git checkout -b v1.7.1. 1.7.1.
```

## 2. apply patch

download patch to local, and apply it:

```
git apply kotlinx-serialization.patch
```

## 3. maven configuration

Replace the following `username`, `password`, and `url` with the corresponding published information.
```
 fun configureMavenPublication(rh: RepositoryHandler, project: Project) {
    rh.maven {
        url = xxx
        credentials {
            username = xxx
            password = xxx
        }
    }
}
```

and change your own kotlinx.serialization version
```
version = "xxx"
```

## 4. publish kotlinx.serialization

after gradle sync, enter kotlinx.serialization project' root path, execute `publish` ，publish kotlinx.serialization to your own maven
```
./gradlew publish
```

# How to import

import kotlinx.serialization in `libs.version.toml`

```
serializationVersion = "xxxx"

lib-kotlin-serialization = { group = "org.jetbrains.kotlinx", name = "kotlinx-serialization-json", version.ref = "serializationVersion" }
```

and implementation in module's `build.gradle.kts`
```
implementation(lib.kotlin.serialization)
```