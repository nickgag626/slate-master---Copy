#Getting Started
The new mPOS EMV SDK will be available to clients who register through the [Ingenico Developer Portal](http://developer.ingenico.us). Once you have obtained credentials for the portal, navigate to the Software tab on the banner and download the SDK package. 


## Developer Portal
The Ingenico Developer Portal serves as a distribution channel for our mPOS SDK material, as well as a collaborative environment for third-party developers to get the support they need for their projects and applications. 

<br/>A request for an account can be made at (http://developer.ingenico.us), and will be reviewed by the internal Ingenico team before an account is activated. (Note: This allows creation of a user account only, therefore each user (Developer) for an ISV will need to register and create their own account.)

<br/>Once approved, an NDA will be executed and a new client/customer record will be created in the portal for future portal notifications, updates, and any other changes.

<br/>Existing clients who utilize the ROAMpay API or who are clients for RUA or another API product through Netsuite, will be asked to register on the developer portal in order to access the new mPOS EMV SDK.


## Supported Devices

For a list of supported devices, please reference the [Ingenico Device Compatability page](http://mobile-solutions.ingenico.com/device-compatibility/) 


## Unsupported Devices
At Ingenico Mobile Solutions, we attempt to support as wide of a variety of mobile devices as possible. If a device is not found on our list of compatible devices, the mPOS SDK will attempt to establish communication between the card reader and mobile device through default settings dependent on the mobile device manufacturer and model. If communication still cannot be established, then the methods below can be attempted that may be able to establish the connection between card reader and mobile device.

Contact Technical Support
If the card reader cannot connect to the mobile device successfully, you can contact our technical support team and have our engineers investigate the incompatibility issue. We will manually add the mobile device parameters necessary into our mPOS SDK as well as make any firmware revisions, changes, and fixes to our card reader in order to provide compatibility. If you are interested in contacting our technical support team, please ensure you have the following:

* At least one available support block on your Ingenico Mobile Solutions account
  * You will need one support block for every mobile device that is incompatible.
  * Your support block will be refunded if we are unable to provide compatibility and support for the requested mobile device.
* Mobile device manufacturer
* Exact model of the device
* Android version being tested on
* Parameters retrieved from the calibration tool (if any)
* If the issue is present on audio jack, Bluetooth, or both

Once we receive all the information, our support staff will queue the issue to our engineers. You will be provided a case number and updated regularly on the issue and it’s progress. The time it takes to add support for mobile devices vary from device to device. Some mobile devices can be added on the same day and some may take several days to complete. During this time, if you have any questions, feel free to ask any of the support staff. If you the inquiry is urgent, please also include the SDK Product Manager as a CC. 

##JavaDoc Resource
The SDK comes with an included Javadoc resource which contains information regarding all API classes, methods, exceptions, and other definitions. The Javadoc can be found in the **\libs** folder of the SDK package that was downloaded. The filename for the Javadoc resource is as follows: **ingenico-mpos-sdk- v1.X.X-javadoc.jar**. In order to properly open the Javadoc, please extract all contents within the jar file into a separate folder and locate the **index.html** file.