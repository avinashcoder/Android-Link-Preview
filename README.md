[![](https://jitpack.io/v/avinashcoder/Android-Link-Preview.svg)](https://jitpack.io/#avinashcoder/Android-Link-Preview)

# Android-Link-Preview
=================================

[![Android Arsenal](https://img.shields.io/badge/Android%20Arsenal-Android--Link--Preview-green.svg?style=true)](https://android-arsenal.com/details/1/2755)

It makes a preview from an url, grabbing all the information such as title, relevant texts and images.

## Visual Examples
![Preview](images/VSejRyV.gif)



## Requirements
* [jsoup](http://jsoup.org/ "jsoup") is a smart lib to get the html code.


## Installation
### gradle

Simply add the repository to your build.gradle file:
```groovy
repositories {
	jcenter()
	maven { url 'https://jitpack.io' }
}
```

And you can use the artifacts like this:
```groovy
dependencies {
    implementation 'com.github.avinashcoder:Android-Link-Preview:1.0.0'
	// ...
}
```

### ProGuard
If you use ProGuard, it is advised that you keep the jsoup dependencies  by adding 
```groovy
-keeppackagenames org.jsoup.nodes
```
to your ProGuard rules file.


## Usage
#### Instantiating 
```java
import com.coder.link.preview.library.TextCrawler;
// ...
// Create an instance of the TextCrawler to parse your url into a preview.
TextCrawler textCrawler = new TextCrawler();

// ..

// Create the callbacks to handle pre and post exicution of the preview generation.
LinkPreviewCallback linkPreviewCallback = new LinkPreviewCallback() {
    @Override
    public void onPre() {
        // Any work that needs to be done before generating the preview. Usually inflate 
        // your custom preview layout here.
    }

    @Override
    public void onPos(SourceContent sourceContent, boolean b) {
        // Populate your preview layout with the results of sourceContent.
    }
};
```

#### Generate Preview
```java
textCrawler.makePreview( linkPreviewCallback, url);
```
#### Cancel unfinished tasks when views are destroied.
If you are using Android Link Preview inside of an Activity, it is important to cancel unfinished Preview activites at the end of the Activity's lifecycle.

```java
 @Override
    protected void onDestroy() {
        super.onDestroy();
        textCrawler.cancel();
    }
```

Information and Contact
===

Developed by [@Avinash Coder](https://github.com/avinashcoder). 
