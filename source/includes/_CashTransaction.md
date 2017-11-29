# Process Cash Transaction

### Description 
In certain payment scenarios, you may need to split the transaction into multiple pieces. One piece will be paid in credit while another is paid in cash. Our SDK also allows you to process a cash transaction if you wish to keep all payment activity within one application and management system.
The ability to process a cash transaction is completely optional. You do not have to implement the ability to process a cash transaction if your application on payment model does not involve cash as a form of payment. If this is the case, you can skip to the next section, "Setting the Environment."

### Required Objects
>Code Example

  ```java

CashSaleTransactionRequest request = new CashSaleTransactionRequest( amount, products, gpsLongitude, gpsLatitude, transactionGroupID);

Ingenico.getInstance().payment().processCashTransaction (request, new TransactionCallbackImpl());


 
  ```
  
Object Name | Object Type | Description
--------- | ------- | ----------- | -----------
amount | Amount | Cost of the sale
products | List<Product> | List of the products
gpsLongitude | String | The location’s longitude
gpsLatitude | String | The location’s latitude
transactionGroupID | String | TBI -- set as null


