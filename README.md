# my checkstyle configuration

## How to use it in your project
Either as a direct dependency in your build.gradle (or via plugin).

In your build.gradle, you have to create a new configuration.
This declaration should be roughly after the _buildScript_ and _apply plugin_ parts.

```groovy
configurations {
    checkstyleConfig
}
```

In the dependencies block you have to declare the following

```groovy
checkstyleConfig 'TODO:my-checkstyle:1.0.0'
```

to configure checkstyle, you have to declare the following block

```groovy
checkstyle {
    toolVersion = "8.8"
    sourceSets = [project.sourceSets.main]
    ignoreFailures = true
    config = resources.text.fromArchiveEntry(configurations.checkstyleConfig, "checkstyle.xml")
}
```

## How to use with Intellij plugins? 

**So there is no copy of checkstyle.xml anymore in my project, how do I link to a checkstyle file with my plugin?**

Easiest way around this problem is to checkout this project and to link your plugin config to the file in this project's resources folder.
