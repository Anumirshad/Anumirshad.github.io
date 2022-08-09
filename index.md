# API Documentation (Verify API)
## Getting Started

### Description

ICG Verify API endpoints include all the information to use the ICG Verify Service and perform ACH Verification

#### Base URL
The API uses the following base URL:


> https://verify.icheckdev.com 

#### Authorization 
This API uses the following header parameters for authentication.
|Header       | Default   |Description|
|-------------|-----------|-----------|
|Authorization| None      | API Access token provided by the Auth API after User authentication| 

The request looks like this:
```markdown
curl https://verify.icheckdev.com \
  -H 'Authorization: {AUTHORIZATION}'
 ```
 
 ```markdown
 GET / HTTP/1.1
Host: {HOST}
Authorization: {AUTHORIZATION}
```

## API Endpoints
## ICG Verify
### ICG Verify Process
#### Description
Validates the check based on the routing and account numbers provided.
#### POST
```markdown
curl -X POST \
  --url 'https://verify.icheckdev.com/IcgVerify/Process' \
  -H 'Authorization: Authorization'\
  -H 'Accept: application/json'\
  -H 'Content-Type: application/json' \
  --data-raw '{
  "bankAccount": {
    "routingNumber": "routingNumber0",
    "accountNumber": "accountNumber4"
  }
}`
```
Above are listed all the possible codes returned from the process

|ICG Code | ICG Decision Value | Description |
|---------|--------------------|-------------|
|I001|ACCEPT |There is no negative information known on the account|
|I002|DECLINED|Customer has returned item(s) in the past 12 months that were returned due to unauthorized.The number of unauthorized returns reported with also be returned in a property message field|
|I003|DECLINED|The RVD database does not have a current unpaid return but the account has been reported as closed or a returned item that has been paid was returned as account closed|
|I004|DECLINED|The RVD database does not have a current unpaid return but we have seen returns in the past for Account not Fount or Invalid account number at the bank|
|I005|DECLINED|Customer has returned items(s) in the past 12 months that were returned due to being ineligible|
|I006|DECLINED|Customer has no unpaid returns at this time in RVD but has a history of returns in the last 12 months|
|I007|DECLINED|Account reported Closed|
|I008|DECLINED|Bank routing number is not a vaild US routing #|
|I009|DECLINED|Negative Data - Negative information was found|
|I010|WARNING|The routing number submitted belongs to a financial institution; however, this financial institution does not report information to the National Shared Database.No positive or negative information found for this routing number and account number.|
|I011|WARNING|Account number format is suspicious|
|I012|DECLINED|Account Number is less than 3 digits or contains an invalid character|


This endpoint requires [authentication](https://developers.icheckdev.com/Verify/#/http/getting-started/how-to-get-started/authorization).
```markdown
POST /IcgVerify/Process
```
#### Explorer 
> Parameter*
> Request*

|Names|Description|
|-----|-----------|
|bankAccount(required)|[ICG Verify Models Icg Verification ICG Verify Bank Account](https://developers.icheckdev.com/Verify/#/http/models/structures/icg-verify-models-icg-verification-icg-verify-bank-account)
|ruleNum|String Rule number-assigned by MicroBilt|
|gatewayLive|Boolean Enable or disable the live|



### ICG Verify Process Extended
#### Description
This is the extended version of the ICG Verify feature. It only can be used if the merchant provided has the permission FEATURE_ICG_VERIFY_EXTENDED assigned to the related user authenticated.

This feature exploits all the microbilt options to validate an account based on many other parameters besides the Bank Route Number and Account Number.

The responses on this endpoint are same as the one listed above in the 'ICG Verify Process' section

#### POST
```markdown
curl -X POST \
  --url 'https://verify.icheckdev.com/IcgVerify/ProcessExt' \
  -H 'Authorization: Authorization'\
  -H 'Accept: application/json'\
  -H 'Content-Type: application/json' \
  --data-raw '{
  "bankAccount": {
    "routingNumber": "routingNumber0",
    "accountNumber": "accountNumber4"
  }
}'
```
This endpoint requires [authentication](https://developers.icheckdev.com/Verify/#/http/getting-started/how-to-get-started/authorization)
```markdown
POST /IcgVerify/ProcessExt
```

## ICG Verify Legacy
### ICG Verify Legacy Process
#### Description
Validates the check based on the routing and account numbers provided.

#### POST

```markdown
curl -X POST \
  --url 'https://verify.icheckdev.com/IcgVerifyLegacy/Process' \
  -H 'Authorization: Authorization'\
  -H 'Accept: application/json'\
  -H 'Content-Type: application/json' \
  --data-raw '{
  "bankAccount": {
    "routingNumber": "routingNumber0",
    "accountNumber": "accountNumber4"
  }
}'
```
This endpoint requires [authentication](https://developers.icheckdev.com/Verify/#/http/getting-started/how-to-get-started/authorization)
```markdown
POST /IcgVerifyLegacy/Process
```

For more details see [Basic writing and formatting syntax](https://docs.github.com/en/github/writing-on-github/getting-started-with-writing-and-formatting-on-github/basic-writing-and-formatting-syntax).

### Jekyll Themes

Your Pages site will use the layout and styles from the Jekyll theme you have selected in your [repository settings](https://github.com/Anumirshad/Anumirshad.github.io/settings/pages). The name of this theme is saved in the Jekyll `_config.yml` configuration file.

### Support or Contact

Having trouble with Pages? Check out our [documentation](https://docs.github.com/categories/github-pages-basics/) or [contact support](https://support.github.com/contact) and we’ll help you sort it out.
