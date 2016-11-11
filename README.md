ALClabs-gradle
==============

This project contains the shared part of the [gradle](http://www.gradle.org) build file used to simplify building and deploying addons for WebCtrl.

To use this, create a gradle project in your IDE and  include the following in the header of your gradle build file (before your project's info and dependencies)
```
        configurations { gradleScript }
        repositories { 
            maven { url: 'http://repo.alcshare.com'} 
        }
        dependencies { 
            gradleScript group: 'com.alcshare', name: 'addon-gradle', ext: 'gradle', version: '1.7' 
        }
        apply from: configurations.gradleScript.resolve().iterator().next()
```
This shared gradle file includes:

*   plugin war
*   plugin groovy (which includes java)
*   plugin idea
*   plugin eclipse
*   sets up maven central as a repo
*   configures the war task to use an all lower case name without a version in the war name
*   wrapper task to generate a gradle wrapper
*   deploy task to deploy an exploded war to your WebCTRL webapp directory
*   gradle GUI launcher

If you run gradlew for a project using this shared file without any parameters, it will launch the gradle gui.

The first time you run the deploy task, it will prompt you for the location of your WebCTRL installation, so it can deploy your web app correctly.
