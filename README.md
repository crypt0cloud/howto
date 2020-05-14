# Crypt0.Cloud Usage guidelines
In this section we show how to use the SDKs provided by Crypt0.Coud for different programming languages. Although each programming language has its own forms of execution, they will all be aligned the following general process.

![alt text](https://raw.githubusercontent.com/crypt0cloud/howto/master/lib_flow.png "Description of transactions")

## Signer Keys
Crypt0.Cloud has a variety of potential signers, each of which describes different responsibilities and different authorities.

### Signing Keys
To be used on the platform, it must be registered by self-signing the registration transaction (CreateKey) with a Key ID to identify it on the external platform. Once the key is registered, they can be used to sign the transactions within a Group.
Keys are automatically created by libraries. 

### Application Keys
These keys are issued by the Controller Cluster and represent the authority of an application or an endpoint to create group transactions or individual transactions.

## Kinds of Transactions
Every transaction in Crypt0.Cloud must be signed by the correct key type, operationally there are two types of Transactions: **Group Transactions** and **Single Transactions** (that belong to a group).

### Group Transactions
Group transactions are transactions created by an Application Key (CreateGroup) and these contain sub-transactions that carry detailed information for this group. You can imagine this as a transaction folder.

When creating a Group Transaction, a list of types of transactions is required within the group; for instance: if you have an *Research Folder* group transaction, that group might contain *Evidences*, *Verdicts*, *Filings*, and *Notifications*, between others. Based on this example, these could be the values ​​of the transaction list: ["evidence", "verdict", "filling", "notification", ...].

When inserted, the Group Signature becomes the primary value of all transactions in the group.

### Simple Transactions (that belong to a group)
This transaction is signed by a Signing Key but created by an application, for this reason the creation process is asynchronous, which allows creating innovative use cases. 

Signing steps:
- **Creating Signing Request** (CreateSigningRequest):  It is created by an application that completes all the information that will be signed by the Signing Key and returns an identification that can be used to retrieve the signature request. 
- **Getting Signing Request** (GetSigningRequest): with the identification of the Signature Request, this method can retrieve the data of the transaction to be signed, allowing an asynchronous signature in case of signing on different devices or platforms. 
- **Sign Signing Request** (SignSigningRequest): This is the actual signing of the Signing Request and posting of the transaction to Crypt0.Cloud with a Signing Key.

