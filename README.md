# -paymentgateway_payumoney

### PayU Money Payment Gateway


Integrating payment gateways for e-commerce sites usually require a business to be a registered entity i.e. a sole proprietorship, a pvt. ltd., etc. But here is an option for you to sell online and start accepting online payments even without registering your business. How is that possible? Well, here’s the solution. PayU Money is essentially a payment gateway solution for individuals and the following is a review of the payment gateway.

#### Q.How do I accept online payments if my business is not registered?
A.  PayU Money is necessarily a savings account payment gateway for individuals. You can start receiving payments on your online store, even if your business is not registered. The only pre-requisite is, you should have a Savings Bank A/C. If all your documents are in order, you can start accepting online payments on your store in just 48 hours. But usually the entire process takes up to 20-25 days to complete.


#### Q. What is PayU Money?

PayU Money

A. PayU Money is a leading online payments solution company in India, which started operations in October 2011. And, since then it has grown into the fastest growing consumer payment processor in the online payment space. As of now, PayU Money boasts of having more than 1200 merchants on board.

#### Q. What documents are required to integrate PayU Money on the online store?

A. To integrate PayU Money on your online store, you only need to submit 3 documents, namely:

1.Your Pan Card copy,
2.KYC Document (Aadhar Card, Passport, Voter ID, Driver’s License), and
3.Bank Verification Letter or Cancelled Cheque  of Savings Bank Account

#### Q. What are the different charges levied with PayU Money PG?

A. There is absolutely no Setup fee or AMC levied with PayU Money. The only charge borne by you is the TDR% i.e. Transaction Discount Rate. Details of which are as follows:

Different Charges	PayU Money Payment Gateway
Set-Up Fee	0
AMC	0
TDR%	2.9% + Service Tax (12.36% of TDR Value)


#### Q. How do these charges translate per transaction?

A. Given below are 2 examples to help you better understand the per transaction costs that will be borne by you.

|Case A|
|------|
|Transaction Amount	Rs. 100|
|TDR%	2.9%|
|Transaction cost	Rs. 2.9|
|Case B|
|Transaction Amount	Rs.200|
|TDR%	2.9%|
|Transaction cost	Rs. 5.8|

#### Q. Is the above transaction cost, inclusive of service tax?

A. No, the above costs are NOT INCLUSIVE of service tax.

So when service tax, i.e. 12.36% is levied on the above numbers, the transaction costs are:

|Case A|
|------|
|Transaction Cost	Rs. 2.9|
|Service Tax	12.36% = Rs. 0.35|
|Total Transaction Cost	Rs. 2.9 + 0.35 = Rs. 3.25|
|Case B|
|Transaction Cost	Rs. 5.8|
|Service Tax	12.36% = Rs. 0.71|
|Total Transaction Cost	Rs. 5.8 + 0.71 = Rs. 6.51|
 

#### Q. How long does it take the payment gateway to get activated?

A. If all your documents are in order, PayU Money offers immediate activation of the payment gateway i.e. within 48 hours of the PayU Money receiving the papers. But usually, the entire process takes 15-20 working days to complete.

#### Q. How does PayU Money work?

A. So here’s how PayU Money processes the transactions on your store:

1.Customer A buys the product from your store and makes a payment
2.PayU Money receives the payment on your behalf and sends you (the store owner) a notification about the same
3.After receiving the notification, you dispatch the product to customer A
4.Customer A receives the products
5.You enter the Order Received details on your PayU Money Merchant Portal
6.PayU Money sends a notification to Customer A to confirm order received
7.PayU Money waits for customer to confirm delivery of the products for a period of 3 days. As soon as customer confirms, payment is transferred to your (the store owner’s) bank account. If customer doesn’t cofirm within the 3 days, PayU Money still transfers the payment to your account, at the end of 3 days.

#### Q: Why does PayU Money release payment only after they receive a confirmation from the customer?

A. In India, the payment gateway space is rather complicated; having a registered business and all makes it complicated. Two of the major pains of getting a payment gateway are:
1. Loads of paperwork needed to get a registered payment gateway for your business
2. High turnaround time after you have sent in your papers. It takes about 15-30 days to completely activate all payment options on your site.

Hats off to PayU Money for having saved all of us from these trials. They are taking a big risk on your part, to accept payments online without much documentation.

And that is why, by releasing a payment only after the customer acknowledges delivery of the product, they are making sure no fraudulent activities take place through their payment gateway.

Q. How is PayU Money different from the other more conventional payment gateways?

A. Like mentioned earlier, PayU Money is a payment gateway alternative for non-registered business i.e. individuals with nothing more than an individual savings A/C. Some of the other points of distinction are listed below:


|Conventional Payment Gateways | PayU Money Payment Gateway|
|------------------------------|---------------------------|
|Requires a company to be registered	| No company registration required|
|Needs a Current bank A/C in the name of the company|All you need is an individual Savings bank A/C|
|Loads of documents required to get an authorized payment gateway	|Just a Savings bank A/C and a PAN Card required
15-20 working days required to activate payment gateway	|
|If all documents are in order, PayU Money is activated on your |store within 48 hours of the PayU Money receiving the papers.|
|Store owner receives payment in T+2 days|	Payment is received as soon as customer confirms delivery|
 

### PayU Money Implementation

#### Step 1:
The end point 
https://tc9gXXXXnjf.execute-api.us-east-1.amazonaws.com/dev/paymentgatewaydatapreprocessor

Request Type:
POST

``` json
Payload:
{
“amount”:””,
“email”:””,
“first_name”:””,
“phone”:””
}
```

#### Step 2:
A lambda PaymentGatewayDataPreprocess will be invoked and will set furl,key,productinfo.service_provider,surl,txnid 

the following payload will be created.
``` json
Payload:
{
“amount”:””,
“email”:””,
“first_name”:””,
“phone”:””,

“furl,key”:””,
“productinfo”:””,
“service_provider”:””,
“surl”:””,
“txnid”:”” 
}
```


#### Step 3:
This payload/information will be saved in database 

#### Step 4,5,6:
The payload will be delivered to client/user.



#### Step 7:
a virtual page will be generated will all the required fields and submitted to PayU server then
User gets redirect to PayU money payment gateway.
User will now initiate with the payment and will pay the required amount.



#### Step 8:
Here transaction status based on success/failure will be send by PayU to the below endpoint.
https://XXXXX.execute-api.us-east-1.amazonaws.com/dev/


#### Step 9:
calculate hash with the returning item from the PayU.
Match the hash given by PayU to check weather data is authentic or is not tampered.



reference:
https://www.payumoney.com/dev-guide/webcheckout/redirect.html

Hash for Normal Payment Response:
`salt|status||||||udf5|udf4|udf3|udf2|udf1|email|firstname|productinfo|amount|txnid|key`



below is the success sample payload of PayU money and now with the below data I must check its authenticity.
Ex.
``` json
{  
   "split_info":"XXX17743",
   "customerName":"Test user",
   "additionalCharges":"",
   "paymentMode":"DC",
   "hash":"XXX00c3a13f37c1271df8c0ebe67c4aad2d29a2086e80aaa3d16580bbe38f9ffd0c3996eab241aa730a4efe512c6c15730ca66020064d71d85dcb68631119f29",
   "status":"Success",
   "error_Message":"No Error",
   "paymentId":"59017743",
   "productInfo":"Description1",
   "customerEmail":"storedcard8@yopmail.com",
   "customerPhone":"6709133497",
   "merchantTransactionId":"XXX6753-59017743",
   "amount":"100.0",
   "udf2":"",
   "notificationId":"37208",
   "udf1":"",
   "udf5":"",
   "udf4":"",
   "udf3":""
}
```

Here the salt ie private key is missing. (it’s missing and confidential, since its not given in the payload and to create hash that exact salt key required. Hence no one can tamper that data without salt key )
Here now check the authenticity of data:
Create hash string first with the given data in following sequence provide your salt key given by PayU and take rest of the things from response:
`salt|status||||||udf5|udf4|udf3|udf2|udf1|email|firstname|productinfo|amount|txnid|key`

`fE0aTrjr|success||||||||||| storedcard8@yopmail.com |Test user| Description1|100.0|4826753-59017743|UFu3ed`

now generate hash for the string 
`fE0aTrjr|success||||||||||| storedcard8@yopmail.com |Test user| Description1|100.0|4826753-59017743|UFu3ed`
now say the hash code u get is 
`64700c3a13f37c1271df8c0ebe67c4aad2d29a2086e80aaa3d16580bbe38f9ffd0c3996eab241aa730a4efe512c6c15730ca66020064d71d85dcb68631119f29`
Now check this hash code with the given code by PayU if both are same the data is vailid and not tampered.

#### Step 10:
Save data in database.

#### Step 11,12,13:
Reply user with appropriate message 
Payment success/failure.


![Throughput Graph](https://github.com/PiyushMittl/-paymentgateway_payumoney/blob/master/payumoney.png)
