# Deferred-AwaitTuple-KT

Deferred-AwaitTuple-KT contains helper functions for Deferred, to await their emissions into typed tuples.

Under the hood, it uses Tuples-KT to help provide await calls from 2 to 36 arity.

```kotlin
val moviesAsync = async { moviesApi.getMovieNowPlayingList() }
val tvSeriesAsync = async { moviesApi.getTvSeriesNowPlayingList() }
val genresAsync = async { moviesApi.getMovieGenres() }

val (movies, tvSeries, genres) = awaitTuple(moviesAsync, tvSeriesAsync, genresAsync)
```

## Why?

It's useful when you want to await multiple deferreds and get the results, without defining an actual class with an actual name to do it, or having to manually invoke `await()` on each separately at the right time.

It is analogous to `awaitAll()` except you can do it with different types.

## Using Deferred-AwaitTuple-KT

In order to use Deferred-AwaitTuple-KT, you need to add `jitpack` to your project root `build.gradle.kts`
(or `build.gradle`):

``` kotlin
// build.gradle.kts
allprojects {
    repositories {
        // ...
        maven { setUrl("https://jitpack.io") }
    }
    // ...
}
```

or

``` groovy
// build.gradle
allprojects {
    repositories {
        // ...
        maven { url "https://jitpack.io" }
    }
    // ...
}
```

In newer projects, you need to also update the `settings.gradle` file's `dependencyResolutionManagement` block:

```
dependencyResolutionManagement {
    repositoriesMode.set(RepositoriesMode.FAIL_ON_PROJECT_REPOS)
    repositories {
        google()
        mavenCentral()
        maven { url 'https://jitpack.io' }  // <--
        jcenter() // Warning: this repository is going to shut down soon
    }
}
```


and then, add the dependency to your module's `build.gradle.kts` (or `build.gradle`):

``` kotlin
// build.gradle.kts
implementation("com.github.Zhuinden:deferred-awaittuple-kt:1.0.0")
```

or

``` groovy
// build.gradle
implementation 'com.github.Zhuinden:deferred-awaittuple-kt:1.0.0'
```

## License

    Copyright 2025 Gabor Varadi

    Licensed under the Apache License, Version 2.0 (the "License");
    you may not use this file except in compliance with the License.
    You may obtain a copy of the License at

       http://www.apache.org/licenses/LICENSE-2.0

    Unless required by applicable law or agreed to in writing, software
    distributed under the License is distributed on an "AS IS" BASIS,
    WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
    See the License for the specific language governing permissions and
    limitations under the License.
