# Setup

In order to begin using the SDK, you will need to integrate the .aar file into your project. The .aar file can be found within the SDK package located on the developer portal’s software page. 

<aside class="notice">
The .aar file will include everything you need to begin building your application, including all Ingenico source code and resource files. 
</aside>


## Integrate the .aar File
To integrate the .aar file into your project, please follow the steps below:

* **Copy the .aar file to your project** <br/>
  1. Download the mPOS EMV Android SDK from the [developer portal](https://developer.ingenico.us/).
  2. Unzip the downloaded contents to a new file destination.
  3. Open the unzipped folder contents.
  4. Navigate to the `/libs` folder.
  5. Copy the .aar file within the directory.
  6. Navigate to your project’s `/libs` directory (typically located at: `project directory/apps/libs)`.
  7. Paste the .aar file to your project’s `/libs` folder.
  
  
>Insert this code into the dependencies section:

  ```java

  
dependencies {
    compile fileTree(include: ['*.jar'], dir: 'libs')
    compile(name:'file name', ext:'aar')
}
repositories{
    flatDir{
        dirs 'libs'
    }
}'
 
  ```
  
* **Update the build.gradle file**
  1. Open your Android project.
  2. Navigate and open the `build.gradle` (Module.app) file.
  3. Insert the code in the right-hand column into the dependencies section where: 
		* `file name` is the name of the copied .aar file from Step 1 (e.g. ingenico-mpos-sdk-v1.0.0-release). 
