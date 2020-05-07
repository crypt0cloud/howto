# Crypt0.Cloud Usage guidelines
Here we are going to show you how to use the sdks provided for the different languages. When all the languages have their own ways of working they all follow this general process.

![alt text](https://raw.githubusercontent.com/crypt0cloud/howto/master/lib_flow.png "Description of transactions")

## Signer Keys
In Crypt0.Cloud there is a variety of posible Signers, every one describing different responsabilities and different authority.

### User Keys
This key are created on the fly by the libraries, to be used in the platform have to be registered self signing the registration transaction (CreateUser) with a user id value to identify the user in the external platform. When registered this transactions can sign the transactions inside a Group. 

### Application Keys
This keys are issued by the Cluster Controller and represent the autority of an applications or an endpoint to create Group Transactions or Single Transactions

## Kinds of Transactions
Every transaction in Crypt0.Cloud have to be signed by the corect key kind, operationally there is two kind of Transactions: Group Transactions, and Transactiosn from a Group.

### Group Transactions
The group transaction is a transaction created by an application key (CreateGroup) and this transaction will hold sub transactions that will carry details for this group. You can imagine this as a folder of transactions.

When a group Transaction is created a list of transaction kinds is required. This kinds enumerate the named kind of the transactions inside the group, for example if you have a group transaction of a Investigation, that group will have proves, veredicts, fillings and notifications, those can be the values of the list of transactions ["prove", "veredict", "filling", "notification"].

When inserted the Sign of the Group becomes the **Parent** value of all the transactios in the Group. 

### Transactions in a Group
This transaction are signed by an User Key but created by an aplication for this reason the process of creating them is asynchronous allowing inovative use cases. 

Signing steps:
- **Creating Signing Request** (CreateSigningRequest): This is created by an aplication completing all the information that will be signed by the user key, returning an id that can be used to retrieve the Signing Request. 
- **Getting Signing Request** (GetSigningRequest): With the id of the Signing Request this method can retrieve the data of the transaction to be signed allowing asincronous signing in case of signing in different devices or platforms. 
- **Sign Signing Request** (SignSigningRequest): This is the actual signing by user key and publishing of the transaction to Crypt0.Cloud.

