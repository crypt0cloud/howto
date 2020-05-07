# Crypt0.Cloud Usage guidelines

Here we are going to show you how to use the sdks provided for the different languages

## Signer Keys
In Crypt0.Cloud there is a variety of posible Signers, every one describing different responsabilities and different authority.

### User Keys
This key are created on the fly by the libraries, to be used in the platform have to be registered self signing the registration transaction with a user id value to identify the user in the external platform. When registered this transactions can sign the transactions inside a Group. 

### Application Keys
This keys are issued by the Cluster Controller and represent the autority of an applications or an endpoint to create Group Transactions or Single Transactions

## Kinds of Transactions

Every transaction in Crypt0.Cloud have to be signed by the corect party, Every kind of transaction have different signers. From applications
