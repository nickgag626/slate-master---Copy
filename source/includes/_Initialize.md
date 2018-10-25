# Initialize and Login

## Initialize
>The Ingenico class acts as an entry point to the Ingenico mPOS SDK.

  ```java

Ingenico.getInstance().initialize(baseURL,
                        apiKey,
                        clientVersion); 

  ```
  
In order to use the SDK, you will need to first initialize it. The method shown here will initialize the singleton instance of Ingenico, and set the API key, Base URL and Client Version. 



Parameter |Type | Description 
--------- | ------- | -----------
baseURL |String | Hostname of the Ingenico Payment Server
apiKey |String | API Key of the client application for the Ingenico Payment Server
clientVersion |String | Version of the client application

## Login
  ```java

class LoginCallbackImpl implements LoginCallback {
    @Override
   public void done(Integer responseCode, UserProfile userProfile) {
        if (ResponseCode.Success == responseCode) {
            /*Login succeeded*/
       } else {
            /*Login failed and the responseCode will indicate the error */
       }
   }
}
     
Ingenico.getInstance().user().login(username, password, new LoginCallbackImpl());

 
  ```
  
Once you have successfully initialized the SDK, you can now log in. Provide your username and password as input parameters (listed below) to successfully log in. 


Parameter |Type | Description 
--------- | ------- | -----------
username |String | Username used to log in to the system
password |String | User's password 
