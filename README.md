Documentation

What is Cronet:
Cronet is the networking stack of Chromium put into a library for use on mobile. This is the same networking stack that is used in the Chrome browser by over a billion people. It offers an easy-to-use, high performance, standards-compliant, and secure way to perform HTTP requests.. On Android, Cronet offers its own Java asynchronous API as well as support for the java.net.HttpURLConnection API. Cronet takes advantage of multiple technologies that reduce the latency and increase the throughput of the network requests that your app needs to work.

Envoy:
Envoy is built on top of cronet which offers support for Okhttp, Volley, WebView, Cronet basic and java.net.HttpURLConnection. 

Configuring into your project:

In order to use envoy, you will need to download the following project from the link 
https://github.com/greatfire/envoy
After downloading the project from the above link,  Download the cronet.arr files from ReadMe file or click on the below links. There are two variants of cronet.
cronet-debug.aar
cronet-release.aar

Download both and Copy these files and paste it into directory cronet which is inside folder android.
![image](https://user-images.githubusercontent.com/15171546/89523440-45bd8480-d7fc-11ea-8be9-a40fb5126bb8.png)

 
Importing this project as a module into your project:

  Step 1: 


![image](https://user-images.githubusercontent.com/15171546/89523489-5ec63580-d7fc-11ea-8d6e-0d1cbcbff790.png)






Step 2:
Mark check on import module name: cronet and module name: envoy
Mark uncheck on import module name: demo

![image](https://user-images.githubusercontent.com/15171546/89523578-85846c00-d7fc-11ea-933b-5f6e91196b7b.png)

 


Step 3:
Your project’s minimum sdk should be 21 

![image](https://user-images.githubusercontent.com/15171546/89523626-9af99600-d7fc-11ea-96b8-2834ff9df65e.png)


Step 4:
Add following dependencies into your build.gradle (Module:app)

```
implementation project(path: ':envoy')
releaseImplementation project(path: ':cronet', configuration: 'release')
debugImplementation project(path: ':cronet', configuration: 'debug')
```

```
if you are using Okhttp then add this dependency

implementation 'com.squareup.okhttp3:okhttp:4.6.0'
```

```
if you are using Volley then add this dependency

implementation 'com.android.volley:volley:1.1.1'
```

Now sync and build the project. Envoy has successfully integrated into your project.

Examples of Simple URL and Envoy URL:
 
 ![image](https://user-images.githubusercontent.com/15171546/89523711-c0869f80-d7fc-11ea-92bc-da8530eac030.png)


In its simplest form, an envoy URL is just an HTTP(s) URL, such as "https://allowed.example.com/app1/". But envoy also accepts a special URL scheme in this form: "envoy://k1=v1[&kn=vn]?"

Example Usage:
1-	Using basic cronet
 
 https://github.com/greatfire/envoy/blob/e5d54732979bab74412acffca1a7f4c5e8dbd717/android/demo/src/main/java/com/example/myapplication/CronetFragment.java#L73-L132


2-	Using HttpUrlConnection:

https://github.com/greatfire/envoy/blob/e5d54732979bab74412acffca1a7f4c5e8dbd717/android/demo/src/main/java/com/example/myapplication/HttpURLConnectionFragment.java#L52-L122
 

3-	Using Okhttp:
 
https://github.com/greatfire/envoy/blob/e5d54732979bab74412acffca1a7f4c5e8dbd717/android/demo/src/main/java/com/example/myapplication/OkHttpFragment.java#L56-L119


4-	Using Volley:
 
https://github.com/greatfire/envoy/blob/e5d54732979bab74412acffca1a7f4c5e8dbd717/android/demo/src/main/java/com/example/myapplication/VolleyFragment.java#L59-L130


5-	Using Webview:

https://github.com/greatfire/envoy/blob/e5d54732979bab74412acffca1a7f4c5e8dbd717/android/demo/src/main/java/com/example/myapplication/WebViewFragment.java#L41-L56
