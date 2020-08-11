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
 
 ![image](https://user-images.githubusercontent.com/15171546/89523744-d1371580-d7fc-11ea-909e-b71cc564f713.png)


Make request like this: 


![image](https://user-images.githubusercontent.com/15171546/89523762-dd22d780-d7fc-11ea-8437-66b8a8ae8f53.png)



























2-	Using HttpUrlConnection:

![image](https://user-images.githubusercontent.com/15171546/89523804-ef9d1100-d7fc-11ea-9dab-04dc28ab6b2f.png)

 
Make request like this:
 
![image](https://user-images.githubusercontent.com/15171546/89523837-f9267900-d7fc-11ea-9aca-2bfafad99975.png)



































3-	Using Okhttp:
 
 
 ![image](https://user-images.githubusercontent.com/15171546/89523879-06dbfe80-d7fd-11ea-9084-fcfad3c8f5bc.png)



Make request like this:
 
![image](https://user-images.githubusercontent.com/15171546/89523908-14918400-d7fd-11ea-9f8b-49da421b803f.png)




4-	Using Volley:
 

![image](https://user-images.githubusercontent.com/15171546/89523941-2410cd00-d7fd-11ea-8294-49dcb385740f.png)


![image](https://user-images.githubusercontent.com/15171546/89523964-30952580-d7fd-11ea-8d06-d68ceccc6cb9.png)


Make request like this:

![image](https://user-images.githubusercontent.com/15171546/89524012-3db21480-d7fd-11ea-8c98-1409918b9a82.png)

 


5-	Using Webview:

![image](https://user-images.githubusercontent.com/15171546/89524038-499dd680-d7fd-11ea-8c37-f9d2739a12f5.png)

 
