# Building a Debit/Credit Transaction

### Description 
  
The process in which you make the method calls to make a debit or credit transaction is nearly identical with only the method name differentiating the two processes.

You first have to set the environment, as described in the previous section. Once the environment is setup, you will be able to attach the card readers to your mobile device allowing you to process debit/credit transactions.


### Required Objects

Object Name | Object Type | Description
--------- | ------- | ----------- | -----------
card | Card |  Credit card information
saleAmount | Amount | Cost of the sale
products | List<Product> | List of the products
gpsLongitude | String | The location’s longitude
gpsLatitude | String | The location’s latitude
transactionGroupID | String | TBI -- set as null
Context | Android Context | 

### Initialize the Card Reader
>As mentioned, after setting the environment, you will want to connect the card reader. Once the card reader is connected via audio jack, make the following call:
 
 ```java

Ingenico.getInstance().device().initialize(context);

   ```

This method calls initializes the card reader to work with the device. In order to get the initialize command to successfully run, you will need to ensure that your application has audio permissions.

Once the initialize command is run, it will iterate through your selected device types that have been set in section 7. This process can take several seconds and up to a minute. In order to reduce the time the initialize process takes, you can reduce the amount of allowable device types if they are not being used in your environment. In a testing environment, this can greatly reduce the QA process.


### Setup the Card Reader

>Setup the PublicKeys and ApplicationIDs to the connected reader:

 ```java

if(Ingenico.getInstance().device().isSetupRequired()){ 
     Ingenico.getInstance().device().setup(new 
	 DeviceSetupCallbackImpl());
}

class DeviceSetupCallbackImpl implements DeviceSetupCallback{
     @Override
     public void done(Integer responseCode) {
         if (ResponseCode.Success == responseCode) {
             //Implement the success logic
         } else {
              //Implement the failure logic - code in the response will indicates the reason*/
         }
    }
}

   ```

Once the card reader has been initialized, you will need to set it up so that it can communicate with the mobile device and receive commands. The setup method sets the PublicKeys and ApplicationIDs to the connected card reader. 

  
## Process Credit Sale Transaction
>Process a Credit Transaction: 
 
 ```java

Ingenico.getInstance().payment().processCreditSaleTransactionWithCardReader (request, new TransactionCallbackImpl());

CreditSaleTransactionRequest request = new CreditSaleTransactionRequest( amount, products, gpsLongitude, gpsLatitude, transactionGroupID);

   ```

>Similarly, to process a debit card transaction:

 ```java

Ingenico.getInstance().payment().processDebitSaleTransactionWithCardReader (request, new TransactionCallbackImpl());

   ```
Once the card reader is initialized and setup, it can then be used to process a credit card transaction. The method and callback implementation is shown to the right. 





