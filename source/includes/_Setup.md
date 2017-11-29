# Setup

In order to have access to the SDK, you will need to integrate the .AAR file into your project. The
.AAR file can be found within the Pilot package located on the developer portal’s Software page. 
<aside class="warning">
If you do not see the download available, please contact the Developer Portal support team for help in getting access to the files.
</aside>


## Integrate the .aar File
To integrate the .aar file into your project, please follow the steps below:

* Copy the .aar file to your project
  * Download the mPOS EMV Android SDK from the developer portal
  * Unzip the downloaded contents to a new file destination
  * Open the unzipped folder contents in Windows Explorer
  * Navigate to the /libs folder
  * Copy the .aar file within the directory
  * Navigate to your project’s /libs directory (typically located at: <project directory>/apps/libs)
  * Paste the .aar file to your project’s /libs folder
  
>Insert this code into the dependencies section:

  ```java

  compile 'com.android.support:design:<design version>'
 
  ```
  
* **Update the build.gradle file**
  * Open your Android project
  * Navigate and open the build.gradle (Module.app) file
  * Insert the code in the right-hand column into the dependencies section where:
    * **<design version>** is the design support library you want to use. The latest version can be found [here](http://developer.android.com/tools/support- library/features.html)
	* **<file name>** is the name of the copied .aar file from Step 1. 
  * Copy the .aar file within the directory
  * Navigate to your project’s /libs directory (typically located at: <project directory>/apps/libs)
  * Paste the .aar file to your project’s /libs folder
  
* **Update the targetSDKVersion** (optional)
  * Open your Android project
  * Navigate and open the build.gradle (Module.app) file
  * Change the targetSDKversion parameter within the defaultConfig section to 21.

  <aside class="warning">
The suggested targerSDKversion is 21 or lower. If it is set to 22 or higher, the app developer is responsible for handling runtime permissions.
</aside>

## API key
>Add the constant variable as shown below to your MainActivity.jar file:

  ```java

private final static String API_KEY = "RC46-d78d2d37-f7b7-40c9-bf3g-9ecd05cdc562";
//The string above is only an example and will not work in a live environment

 
  ```
You will need to have an API key that will be used as an authentication measure in order to use the SDK. If you have not received your API key, please contact mPOS SDK support team to have one assigned. It is recommended that you create a constant string variable that holds your API key. In your **MainActivity.java** file, add the constant variable as shown to the right. 

## Point to Ingenico Payment Server
>Add the constant variable as shown below to your MainActivity.jar file:

  ```java

private final static String DEFAULT_BASE_URL = "https://uatmcm.roamdata.com/";

 
  ```
Another constant string variable should be created, which contains the URL to the Ingenico Payment Server. This will also be needed in order to make function calls. In your MainActivity.java file, add the constant variable as shown to the right:

## Set the Client Version
>Add the constant variable as shown below to your MainActivity.jar file:

  ```java

private final static String CLIENT_VERSION = "0.1";

 
  ```
In addition to the payment server and API key, you will also need to set the Client Version through a constant variable. In your MainActivity.java file, add the constant variable as shown below: