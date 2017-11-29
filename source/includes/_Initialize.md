# Initialize and Login

## Initialize
  ```java

//Example initiating the Ingenico object
Ingenico ingenico = Ingenico.getInstance(); ingenico.initialize(getApplicationContext(),URL, API_KEY, CLIENT_VERSION); ingenico.setLogging(true);

//Example calling the method directly 
Ingenico.getInstance().initialize(getApplicationContext(),URL, API_KEY, CLIENT_VERSION); Ingenico.getInstance().setLogging(true);

 
  ```
  
In order to use the SDK, you will need to first initialize it. The syntax to initialize the SDK is shown to the right. The initialize method is available within the Ingenico instance object. The Ingenico object is a singleton class, so it can either be instantiated or called directly as shown.

## Login
  ```java

private class LoginCallbackImpl implements LoginCallback {
   @Override
   public void done(Integer responseCode, UserProfile user) {
      if (ResponseCode.Success == responseCode) {
      //Login succeeded
      } else {
      //Login failed and the responseCode will indicate the error
      }
   }
}


 
  ```
  
Once the SDK has been initialized, you will need to login and validate a user’s authenticity to use the application. It is recommended that the login functionality should be created using internal security procedures and guidelines. You will need to create the following class based off the abstract class, **LoginCallback**. 

>Once the class has been implemented, you can then call the login method, as shown below, through an **onClick** event:
  
  ```java

Ingenico.getInstance().user().login(username, password, new LoginCallbackImpl());
 
  ```