# Getting started

Add repository to your build gradle:

```kotlin
repositories {
    maven {
        url = uri("https://repo.nekroplex.com/releases")
    }
}
```

Add dependency, also check the latest version in our repository! ([Here](https://repo.nekroplex.com/releases))

```kotlin
dependencies {
    implementation("gg.aquatic.aquaticseries:aquaticlib-17:1.0.3.10:all") {
        exclude("org.jetbrains.kotlin", "kotlin-stdlib")
        exclude("gg.aquatic.aquaticseries", "aquaticlib")
        exclude("gg.aquatic.aquaticseries.core", "core")
        exclude("org.jetbrains.kotlin","kotlin-stdlib")
    }
}
```

The last thing you need is initializing the library using this code:

```kotlin
override fun onEnable() {
    val lib = AquaticSeriesLib.init(this, listOf(
        // LIST OF FEATURES THAT ARE GONNA BE INITIALIZED
    ))
}
```

The library has to be initialized in onEnable as the initialization registers Listeners & Bukkit Runnables.

AquaticLib also contains modular system of features to avoid having features enabled that you are not planning to use
