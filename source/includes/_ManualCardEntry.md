# Process Manual Card Entry 

This section describes how to process a credit card by manually keying in the card information to include:

1. Credit Card Number
2. Expiration Date
3. CVV2/CVC Code

The method in which you input the above information is completely up to you. The most common way is to have an on-screen number pad to type in the numbers. Processing credit cards manually is also an optional functionality for your application. If you do not plan on allowing your merchants to accept payment by manually entering a card number, then skip to section the next section "Processing Cash Transactions".

### Required Objects for Manually Entered Transaction
>Code Example

  ```java

CashSaleTransactionRequest request = new CashSaleTransactionRequest(
card, saleAmount, products, gpsLongitude, gpsLatitude, transactionGroupID);

Ingenico.getInstance().payment().processCashTransaction (request, new TransactionCallbackImpl());

 
  ```
  
  ```swift

IMSKeyedCardSaleTransactionRequest *request = [[IMSKeyedCardSaleTransactionRequest alloc] initWithCard:Card
andAmount:amount 
                                    andProducts:nil 
                                    andLongitude:longitude
                                    andLatitude:latitude
                           andTransactionGroupID:transactionGroupID]];
[[Ingenico sharedInstance].Payment processKeyedTransaction:request 
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
  
Object Name | Object Type | Description
--------- | ------- | ----------- | -----------
card | Card |  Credit card information
saleAmount | Amount | Cost of the sale
products | List<Product> | List of the products
gpsLongitude | String | The location’s longitude
gpsLatitude | String | The location’s latitude
transactionGroupID | String | TBI -- set as null


