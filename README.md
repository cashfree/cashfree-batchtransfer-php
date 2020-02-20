# Cashfree Payout Integration Kit for PHP

Below is an integration flow on how to use Cashfree's payouts.
Please go through the payout docs [here](https://dev.cashfree.com/payouts)
<br/>
This kit is linked to the standard transfer flow. Go [here](https://dev.cashfree.com/payouts/integrations/batch-transfer) to get a better understanding.
<br/>

## Functionalities

The following kit contains the following functionalities:
    <ol>
    <li> [getToken](https://dev.cashfree.com/api-reference/payouts-api#authorise): to get the auth token to be used in all          following calls.
    <li> [requestbBatchTrasnfer](https://dev.cashfree.com/api-reference/payouts-api#batch-transfer): to request a batch transfer
    <li> [getBatchTransferStatus](https://dev.cashfree.com/api-reference/payouts-api#get-batch-transfer-status-request): to get the status of the requested batch transfer
    </ol>

## Build Steps

follow the following build steps to compile the Integration kit:
  1. Download the code and cd into the directory containing the code.

## Set Up

### Pre Requisites:
The following kit uses information stored within the index.php file. Before running the code for the first time open the index.php file
and add the relevant details:
  1. ClientId: This is a unique identifier that identifies the merchant. For more information please go [here](https://dev.cashfree.com/development/api/credentials).
  2. ClientSecret: Corresponding secret key for the given ClientId that helps Cashfree identify the merchant. For more information please go [here](https://dev.cashfree.com/development/api/credentials).
  3. Environment: Environment to be hit. The following values are accepted prod: for production, test: for the test environment.

### IP Whitelisting:

Your IP has to be whitelisted to hit Cashfree's server. For more information please go [here](https://dev.cashfree.com/development/api/ip-whitelisting).

### Batch Transfer:
The following kit needs batch transfer details in order to create a batch transfer.
The kit reads the batchTransfer details from the index.php file. Under the BatchTransfer section. For a list of required fields go [here](https://dev.cashfree.com/api-reference/payouts-api#batch-transfer).

Sample Fields to add a beneficiary using bankAccount and ifsc are:
  1. batchTransferId: uniqueId of the batch transfer.
  2. batchFormat: format of the batch transfer, accepted values: BANK_ACCOUNT and BENEFICIARY_ID.
  3. deleteBene: optional field, needed if the batch format is bank account, to delete beneficiaries that already exist with the same account details but different names. If set will delete and readd the beneficiary, else will throw an error.
  4. batch: an array of transfers to be done.
  
  Batch format for BANK_TRANSFER:
  
  1. transferId: unique identifier of the transfer.
  2. amount: amount to be sent.
  3. phone: phone number of the recipient.
  4. bankAccount: bank account of the recipient.
  5. ifsc: recipient's bank accounts's ifsc.
  6. email: email of the recipient.
  7. name: name of the recipient.
  <br/>
  Batch format for BENEFICIARY_ID
  
  1. transferId: unique identifier of the transfer.
  2. amount: amount to be sent.
  3. beneId: id of the beneficiary

## Usage

Once the index.php file is setup you can run the executable, to run the entire flow. Authorize, check and add beneficiary, 
request for a payout transfer and get the transfer status.

run the following line in the terminal to run the script
```
  php index.php
```

You can change the necessary values in the index.php file as per your requirements and re-run the script whenever needed.

## Doubts

Reach out to techsupport@cashfree.com in case of doubts.
 


