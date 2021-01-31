
# A poor man's fork

A fork of [xdtianyu/ColorPicker](https://github.com/xdtianyu/ColorPicker) (a possibly abandoned library) that allows it to build against newer version of Android build tools. 

"poor man's", because this was the bare minimum required to get it to compile. A public function name might have changed in the ctrl-F process.

## How to use this poor man's fork

This will be required for every system where you want to build your project that consumes this library. Someone please feel free to publish this on maven central!

Run:
```
git clone git@github.com:locofocos/ColorPicker.git
cd ColorPicker
./gradlew clean
./gradlew build -x lintVitalRelease -x lint
./gradlew install
./gradlew publishToMavenLocal

# or some combinations of commands like that, until you see the new version appear in your .m2 folder

# go to .m2/repository/org/xdty/preference/color-picker
# if you see an "unspecified" version instead of 0.0.7,
# replace all instances of "unspecified" with 0.0.7 (file contents and filenames).
# (yes I hate doing this. Someone please fix this library, I can't get the build configured)
```

Then in the project where you consume it, add mavenLocal() as a repository in 2 places. See https://stackoverflow.com/a/39015691. Like so:
```
buildscript {
    repositories {
        mavenLocal()
        ...
    }
}

allprojects {
    repositories {
        mavenLocal()
        ...
    }
}
```
Bump the version from 0.0.5 (or whatever you're using) to 0.0.7 (this fork's version). Then compile your project and enjoy.

Original readme below:

# ColorPicker
An easy to use android color picker library. Based on [android-colorpicker](https://github.com/woalk/android-colorpicker).

[![Android Arsenal](https://img.shields.io/badge/Android%20Arsenal-ColorPicker-brightgreen.svg?style=flat)](http://android-arsenal.com/details/1/3324)
[![Build Status](https://travis-ci.org/xdtianyu/ColorPicker.svg?branch=master)](https://travis-ci.org/xdtianyu/ColorPicker)
[![JAR](https://img.shields.io/maven-central/v/org.xdty.preference/color-picker.svg)](http://central.maven.org/maven2/org/xdty/preference/color-picker/)
[ ![Download](https://api.bintray.com/packages/xdtianyu/maven/color-picker/images/download.svg) ](https://bintray.com/xdtianyu/maven/color-picker/_latestVersion)

## Download

Grab via gradle

```
dependencies {
    compile 'org.xdty.preference:color-picker:0.0.5'
}
```

or maven

```
<dependency>
  <groupId>org.xdty.preference</groupId>
  <artifactId>color-picker</artifactId>
  <version>0.0.5</version>
  <type>aar</type>
</dependency>
```

or JAR from [maven central](http://central.maven.org/maven2/org/xdty/preference/color-picker/)

## Usage

For more details, see [example](https://github.com/xdtianyu/ColorPicker/tree/master/example)

```
    <org.xdty.preference.ColorPreference
        android:key="example_color"
        android:title="Color"
        android:summary="This is a color preference"
        tools:dialogTitle="@string/default_color"
        tools:colors="@array/default_rainbow"
        tools:columns="5"
        tools:material="true"
        tools:backwardsOrder="true"
        tools:customStrokeWidth="0"
        tools:strokeColor="@android:color/black"
        android:defaultValue="@color/flamingo"/>
```

## ScreenShot

<img src="https://raw.githubusercontent.com/xdtianyu/CallerInfo/master/screenshots/6.png" alt="screenshot" width="300">
