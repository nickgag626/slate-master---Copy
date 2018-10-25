# Process Cash Transaction

In certain payment scenarios, you may need to split the transaction into multiple pieces. One piece will be paid in credit while another is paid in cash. Our SDK also allows you to process a cash transaction if you wish to keep all payment activity within one application and management system.
The ability to process a cash transaction is completely optional. You do not have to implement the ability to process a cash transaction if your application on payment model does not involve cash as a form of payment. If this is the case, you can skip to the next section, "Setting the Environment."

### Required Objects for Cash Transaction
>Code Example

  ```java

CashSaleTransactionRequest request = new CashSaleTransactionRequest( amount, products, gpsLongitude, gpsLatitude, transactionGroupID);

Ingenico.getInstance().payment().processCashTransaction (request, new TransactionCallbackImpl());


 
  ```
  
  ```swift

[[IMSCashSaleTransactionRequest alloc] initWithAmount:amount
                                    andProducts:nil 
                                    andCustomerInfo:nil
                                    andLongitude:longitude
                                    andLatitude:latitude
                           andTransactionGroupID:transactionGroupID]];
[[Ingenico sharedInstance].Payment processCashTransaction:request 
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
amount | Amount | Cost of the sale
products | List<Product> | List of the products
gpsLongitude | String | The location’s longitude
gpsLatitude | String | The location’s latitude
transactionGroupID | String | TBI -- set as null


