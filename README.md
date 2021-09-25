# Arrow Gradle config

## Add basic config to a Kotlin Multiplatform project

In an Arrow KMP project, just add to the plugin block:

```kotlin
plugins {
    id("io.arrow.gradle.kotlin.multiplatform")  // this one
    // ...
}

// ...
```

## Publish Kotlin Multiplatform or JVM projects

Add to the root `build.gradle.kts` the next plugin to the plugin block if it is not there yet:

```kotlin
plugins {
    id("io.arrow.gradle.nexus")
    // ...
}
```

In an Arrow KMP project, just add to the plugin block:

```kotlin
plugins {
    id("io.arrow.gradle.kotlin.multiplatform")
    id("io.arrow.gradle.publish.kotlin.multiplatform")  // this one
    // ...
}

// ...
```

Add the POM Gradle properties for the project (modify with the real value):

```properties
pom.name=Sample name
pom.description=Sample description
pom.url=https://github.com/arrow-kt/sample-repo
pom.license.name=The Apache License, Version 2.0
pom.license.url=https://www.apache.org/licenses/LICENSE-2.0.txt
pom.developer.id=arrow-kt
pom.developer.name=The Arrow Authors
pom.smc.url=https://github.com/arrow-kt/sample-repo
pom.smc.connection=scm:git:git@github.com:arrow-kt/sample-repo.git
pom.smc.developerConnection=scm:git:git@github.com:arrow-kt/sample-repo.git
```

And add the next Gradle properties and/or environment variables for signing the artifacts (they must
not be exposed publicly):

- Environment variables

```text
SIGNING_KEY_NAME=[keyName]
SIGNING_KEY_ID=[keyId]
SIGNING_KEY=[key]
SIGNING_KEY_PASSPHRASE=[passphrase]
OSS_USER=[user]
OSS_TOKEN=[token]
OSS_STAGING_PROFILE_ID=[stagingProfileId]
```

- Gradle properties

```properties
signing.gnupg.keyName=[keyName]
signing.gnupg.keyId=[keyId]
signing.gnupg.key=[key]
signing.gnupg.passphrase=[passphrase]
oss.user=[user]
oss.token=[token]
oss.stagingProfileId=[stagingProfileId]
```

> Remember to replace the `signing.gnupg.key` or `SIGNING_KEY` line breaks with `\n`
