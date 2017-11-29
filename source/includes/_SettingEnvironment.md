# Setting the Environment

>To set a single allowable device type, you will need to make the following method call:

  ```java

DeviceType deviceType = DeviceType.RP450c; ingenico.device().setDeviceType(deviceType);

   ```
   
>If you need to set multiple allowable device types, you will need to make the following method call:

  ```java

List<DeviceType> audioJackDeviceTypes = new ArrayList<>();
     {
        audioJackDeviceTypes.add(DeviceType.G4x); 
		audioJackDeviceTypes.add(DeviceType.RP450c); 
		audioJackDeviceTypes.add(DeviceType.RP350x); 
		audioJackDeviceTypes.add(DeviceType.RP170c);
     }
ingenico.device().setDeviceTypes(audioJackDeviceTypes);


   ```
  
This section will cover the basics if you want to begin using a card reader to accept transactions. When an Ingenico card reader is plugged into your mobile device, the SDK cycles through a list to determine what kind of card reader was plugged in. The list that it searches through is appended by calling the setDeviceType() or setDeviceTypes() method calls, as shown in the code example.
Once the SDK cycles through this list, it checks to ensure that there is a match. The SDK reads through the list in an organized manner, meaning the first item added is the first type of device checked. It is recommended to append items to this list depending on what card readers are most commonly used.


### Required Objects for Environment

Object Name | Object Type | Description
--------- | ------- | ----------- | -----------
deviceType | DeviceType | Type of card reader being used
audioJackDeviceTypes | List<DeviceType> | List of card reader types


<aside class="notice">
For a full list of card readers for the DeviceType class, refer to the Supported Readers section. 
</aside>