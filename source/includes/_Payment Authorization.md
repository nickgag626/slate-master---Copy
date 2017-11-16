# SDK Example: Payment Authorization

##processAuthTransactionWithCardReader
```java
CreditAuthTransactionRequest request = new CreditAuthTransactionRequest(amount,
productList, longitude, latitude,
transactionGroupID);

Ingenico.getInstance().payment().processAuthTransactionWithCardReader(request
, new TransactionCallbackImpl());

```

```swift
IMSCreditAuthTransactionRequest *request = [[IMSCreditAuthTransactionRequest alloc] initWithAmount:amount
                                                                                       andProducts:productList                                                                                 
                                                                                      andLongitude:longitude
                                                                                       andLatitude:latitude
                                                                             andTransactionGroupID:transactionGroupID
                                                                               andTransactionNotes:transactionNote
                                                                              andMerchantInvoiceID:invocieID
                                                                   andShowNotesAndInvoiceOnReceipt:true
                                                                         andTokenRequestParameters:tokenRequest];
  
  
[[Ingenico sharedInstance].Payment processCreditAuthTransactionWithCardReader:request
                               andUpdateProgress:^(IMSProgressMessage message, NSString *extraMessage)
                               {
                                    /*The progress message indicates the stage the transaction is at*/
                               }
                               andSelectApplication:^(NSArray *applicationList, NSError *error, ApplicationSelectedResponse *appReponse)
                               {
                                    /*This callback indicates the card inserted supports multiple Applications and requires user to pick one for this transaction*/
                               }
                               andOnDone:^(IMSTransactionResponse *response, NSError *error)
                               {
                                    if(!error){
                                        /*Transaction succeeded(code in the response will indicates the result of the transaction)*/
                                    }
                                    else{
                                        /*Transaction failed and the responseCode will indicate the error */
                                        NSInteger responseCode = error.code;
                                    }
                               }];


```

###Description
In order to use the SDK, you will first need to initialize it, login, and setup the card reader. This is done to validate a user’s authenticity to use the application, and begin working with the SDK. Please refer to the Ingenico mPOS SDK User Guide (Section 4) if you need assistance with this. 
One properly initialized and setup, this method call can be used to process a pre-authorized transaction. This will temporarily place the funds on hold, which can then be completed or voided if necessary. 




###Required Objects
Object Name | Object Type | Decription
--------- | ------- | -----------
amount | Amount | Cost of the sale
products | List<Product> | List of the products
longitude | String | The location's longitude
latitude | String | The location's latitude
transactionGroupID | String | TBI - set as null

##processKeyedCreditAuthTransaction
```java
KeyedCreditAuthTransactionRequest request = new KeyedCreditAuthTransactionRequest(card,
                                                                                    saleAmount,
                                                                                    products,
                                                                                    clerkID,
                                                                                    longitude,
                                                                                    latitude,
                                                                                    null,
                                                                                    transactionNote,
                                                                                    merchantInvocieID,
                                                                                    Boolean.TRUE,  //showNotesAndInvoiceOnReceipt
                                                                                    tokenRequest);
Ingenico.getInstance().payment().processKeyedCreditAuthTransaction(request,new TransactionCallbackImpl());


```

```swift

IMSKeyedCreditAuthTransactionRequest *request = [[IMSKeyedCreditAuthTransactionRequest alloc] initWithCard:card
                                                                        andAmount:amount
                                                                      andProducts:products
                                                                       andClerkID:clerkID
                                                                     andLongitude:longitude
                                                                      andLatitude:latitude
                                                            andTransactionGroupID:nil
                                                              andTransactionNotes:transactionNote
                                                             andMerchantInvoiceID:invocieID
                                                  andShowNotesAndInvoiceOnReceipt:true
                                                        andTokenRequestParameters:tokenRequest];
  
[[Ingenico sharedInstance].Payment processKeyedCreditAuthTransaction:request
                               andOnDone:^(IMSTransactionResponse *response, NSError *error)
                               {
                                    if(!error){
                                        /*Transaction succeeded(code in the response will indicates the result of the transaction)*/
                                    }
                                    else{
                                        /*Transaction failed and the responseCode will indicate the error */
                                        NSInteger responseCode = error.code;
                                    }
                               }];


```

###Description
Similar to processing a transaction with the card reader (Section 2_1), you must first initialize the SDK and login before processing a transaction.  
This section describes how to process a pre-authorization transaction by manually keying in the card information to include:

- Credit Card Number
- Expiration Date
- CVV2/CVC Code

The method in which you input the above information is completely up to you. The most common way is to have an on-screen number pad to type in the numbers. Processing credit cards manually is also an optional functionality for your application. 

**If you do not plan on allowing your merchants to accept payment by manually entering a card number, you can disregard this section.****

Again, this will temporarily place the funds on hold, which can then be completed or voided if necessary.




###Required Objects
Object Name | Object Type | Decription
--------- | ------- | -----------
card | Card | Credit Card Information
amount | Amount | Cost of the sale
products | List<Product> | List of the products
clerkID | String | Key identifying the client
longitude | String | The location's longitude
latitude | String | The location's latitude



