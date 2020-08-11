## Documentation

### What is Cronet:
Cronet is the networking stack of Chromium put into a library for use on mobile. This is the same networking stack that is used in the Chrome browser by over a billion people. It offers an easy-to-use, high performance, standards-compliant, and secure way to perform HTTP requests.. On Android, Cronet offers its own Java asynchronous API as well as support for the java.net.HttpURLConnection API. Cronet takes advantage of multiple technologies that reduce the latency and increase the throughput of the network requests that your app needs to work.

### Envoy:
Envoy is built on top of cronet which offers support for Okhttp, Volley, WebView, Cronet basic and java.net.HttpURLConnection. 

### Configuring into your project:

In order to use envoy, you will need to download the following project from the link 
https://github.com/greatfire/envoy
After downloading the project from the above link,  Download the cronet.arr files from ReadMe file or click on the below links. There are two variants of cronet.
**cronet-debug.aar**
**cronet-release.aar**

Download both and Copy these files and paste it into directory cronet which is inside folder android.
![image](https://user-images.githubusercontent.com/15171546/89523440-45bd8480-d7fc-11ea-8be9-a40fb5126bb8.png)

 
Importing this project as a module into your project:

#### Step 1: 


![image](https://user-images.githubusercontent.com/15171546/89523489-5ec63580-d7fc-11ea-8d6e-0d1cbcbff790.png)






#### Step 2:
Mark check on import module name: cronet and module name: envoy
Mark uncheck on import module name: demo

![image](https://user-images.githubusercontent.com/15171546/89523578-85846c00-d7fc-11ea-933b-5f6e91196b7b.png)

 


#### Step 3:
Your project’s minimum sdk should be 21 

![image](https://user-images.githubusercontent.com/15171546/89523626-9af99600-d7fc-11ea-96b8-2834ff9df65e.png)


#### Step 4:
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

### Examples of Simple URL and Envoy URL:

**a simple URL:** https://allowed.example.com/app1/

**set host:** envoy://?url=https%3A%2F%2Fexample.com%2Fapp1%2F%3Fk1%3Dv1&header_Host=forbidden.example.com

**only MAP url-host to address:** envoy://?url=https%3A%2F%2Fexample.com%2Fapp1%2F%3Fk1%3Dv1&header_Host=forbidden.example.com&address=1.2.3.4

**custom host override:** envoy://?url=https%3A%2F%2Fexample.com%2Fapp1%2F%3Fk1%3Dv1&header_Host=forbidden.example.com&resolve=MAP%20example.com%201.2.3.4

**disable some cipher suites:** envoy://?url=https%3A%2F%2Fallowed.example.com%2Fapp1%2F%3Fk1%3Dv1&header_Host=forbidden.example.com&address=1.2.3.4&disabled_cipher_suites=0xc024,0xc02f

**In example 5:** allowed.example.com will be TLS SNI, forbidden.example.com will be Host HTTP header, 1.2.3.4 will be IP for allowed.example.com.


### Parameters
**keys for envoy://?k1=v1&k2=v2 format:**

**url:** proxy URL, for example, https://allowed.example.com/path/

**header_xxx:** HTTP header, header_Host=my-host` will send Host header with value my-host

**address:** IP address for domain in proxy URL, to replace IP from DNS resolving

**resolve:** resolve map, same as --host-resolver-rules command line for chromium, Chromium docs, lighthouse issue #2817, firefox bug #1523367

**disable_cipher_suites:** cipher suites list to disable, same as --cipher-suite-blacklist command line, chromium bug #58831, Firefox Support Forum

**salt:** a 16 characters long random string, unique to each combination of app-signing key, user, and device, such [ANDROID_ID}(https://developer.android.com/reference/android/provider/Settings.Secure.html#ANDROID_ID).


In its simplest form, an envoy URL is just an HTTP(s) URL, such as "https://allowed.example.com/app1/". But envoy also accepts a special URL scheme in this form: "envoy://k1=v1[&kn=vn]?"

## Example Usage:
### 1-	Using basic cronet
 
 https://github.com/greatfire/envoy/blob/e5d54732979bab74412acffca1a7f4c5e8dbd717/android/demo/src/main/java/com/example/myapplication/CronetFragment.java#L73-L132


### 2-	Using HttpUrlConnection:

https://github.com/greatfire/envoy/blob/e5d54732979bab74412acffca1a7f4c5e8dbd717/android/demo/src/main/java/com/example/myapplication/HttpURLConnectionFragment.java#L52-L122
 

### 3-	Using Okhttp:
 
https://github.com/greatfire/envoy/blob/e5d54732979bab74412acffca1a7f4c5e8dbd717/android/demo/src/main/java/com/example/myapplication/OkHttpFragment.java#L56-L119


### 4-	Using Volley:
 
https://github.com/greatfire/envoy/blob/e5d54732979bab74412acffca1a7f4c5e8dbd717/android/demo/src/main/java/com/example/myapplication/VolleyFragment.java#L59-L130


### 5-	Using Webview:

https://github.com/greatfire/envoy/blob/e5d54732979bab74412acffca1a7f4c5e8dbd717/android/demo/src/main/java/com/example/myapplication/WebViewFragment.java#L41-L56
