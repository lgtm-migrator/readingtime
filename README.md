[![License (3-Clause BSD)](https://img.shields.io/badge/license-BSD%203--Clause-blue.svg?style=flat-square)](https://opensource.org/licenses/BSD-3-Clause) [![Release](https://img.shields.io/github/release/ethauvin/readingtime.svg)](https://github.com/ethauvin/readingtime/releases/latest) [![Maven Central](https://img.shields.io/maven-central/v/net.thauvin.erik/readingtime.svg?label=maven%20central)](https://search.maven.org/search?q=g:%22net.thauvin.erik%22%20AND%20a:%22readingtime%22)

[![Quality Gate Status](https://sonarcloud.io/api/project_badges/measure?project=ethauvin_readingtime&metric=alert_status)](https://sonarcloud.io/dashboard?id=ethauvin_readingtime) [![GitHub CI](https://github.com/ethauvin/readingtime/actions/workflows/gradle.yml/badge.svg)](https://github.com/ethauvin/readingtime/actions/workflows/gradle.yml) [![CircleCI](https://circleci.com/gh/ethauvin/readingtime/tree/master.svg?style=shield)](https://circleci.com/gh/ethauvin/readingtime/tree/master)

# Estimated Reading Time for Blog Posts, Articles, etc.

A simple Kotlin/Java implementation of [Medium's Read Time calculation](https://blog.medium.com/read-time-and-you-bc2048ab620c).

## Examples (TL;DR)

```kotlin
import net.thauvin.erik.readingtime.ReadingTime

// ...

val rt = ReadingTime(htmlText)
println(rt.calcEstimatedReadTime()) // eg: 2 min read

```

To get the estimated reading time in seconds use the `calcReadingTimeInSec()` function.

 - View [Kotlin](https://github.com/ethauvin/readingtime/blob/master/examples/src/main/kotlin/com/example/ReadingTimeExample.kt) or [Java](https://github.com/ethauvin/readingtime/blob/master/examples/src/main/java/com/example/ReadingTimeSample.java) Examples.

### Gradle, Maven, etc.

To use with [Gradle](https://gradle.org/), include the following dependency in your [build](https://github.com/ethauvin/readingtime/blob/master/examples/build.gradle.kts) file:

```gradle
repositories {
    mavenCentral()
}

dependencies {
    implementation("net.thauvin.erik:readingtime:0.9.1")
}
```

Instructions for using with Maven, Ivy, etc. can be found on [Maven Central](https://search.maven.org/search?q=g:%22net.thauvin.erik%22%20AND%20a:%22readingtime%22).

### Properties

The following properties are available:

```kotlin
ReadingTime(
    text,
    wpm = 275,
    postfix = "min read",
    plural = "min read",
    excludeImages = false, 
    extra = 0,
    roundingMode = RoundingMode.HALF_EVEN
)

```

Property                    | Description
:-------------------------- |:-----------------------------------------------------------------------------------------------------------------------
`text`                      | The text to be evaluated. (Required)
`wpm`                       | The words per minute reading average.
`postfix`                   | The value to be appended to the reading time.
`plural`                    | The value to be appended if the reading time is more than 1 minute.
`excludeImages`             | Images are excluded from the reading time when set.
`extra`                     | Additional seconds to be added to the total reading time.
`roundingMode`              | The [rounding mode](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/math/RoundingMode.html) to apply.

### Functions

A couple of useful functions are also available:

```kotlin
ReadingTime.wordCount(htmlText) // Returns the count of words. (HTML stripped)
ReadingTime.imgCount(htmlText) // Returns the count of images. (HTML img tags)
```

### JSP

A JSP tag is also available for easy incorporation into web applications:

```jsp
<%@taglib uri="https://erik.thauvin.net/taglibs/readingtime" prefix="t"%>
<t:readingtime
    wpm="275"
    postfix="min read"
    plural="min read"
    excludeImages="false"
    extra="0">some_text</t:readingtime>
```

None of the attributes are required.
