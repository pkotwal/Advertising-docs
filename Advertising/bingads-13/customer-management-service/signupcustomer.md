---
title: SignupCustomer Service Operation - Customer Management
ms.service: bing-ads-customer-management-service
ms.topic: article
author: eric-urban
ms.author: eur
description: Creates a new customer and account.
dev_langs: 
  - csharp
  - java
  - php
  - python
---
# SignupCustomer Service Operation - Customer Management
Creates a new customer and account.  

Typically you must be a user with aggregator [credentials](../guides/account-hierarchy-permissions.md#user-roles) to call this operation. In that case, the operation creates a new customer and account that roll up to your aggregator payment method. The [AdvertiserAccount](advertiseraccount.md) object must include the name of the account, the type of currency to use to settle the account, and the payment method identifier must be set to null. The operation generates an invoice account and sets the payment method identifier to the identifier associated with the aggregator's invoice. You are invoiced for all charges incurred by the customers that you manage.

> [!NOTE]
> Agency customers in the Create Accounts on Behalf of Client pilot ([GetCustomerPilotFeatures](../customer-management-service/getcustomerpilotfeatures.md) returns 793) can sign up a new customer on behalf of a client and optionally link to the new account as an agency. In this case a [UserInvitation](userinvitation.md) is sent and the client must complete sign up steps via the Microsoft Advertising UI e.g., accept the terms and conditions.  

## <a name="request"></a>Request Elements
The *SignupCustomerRequest* object defines the [body](#request-body) and [header](#request-header) elements of the service operation request. The elements must be in the same order as shown in the [Request SOAP](#request-soap). 

> [!NOTE]
> Unless otherwise noted below, all request elements are required.

### <a name="request-body"></a>Request Body Elements

|Element|Description|Data Type|
|-----------|---------------|-------------|
|<a name="account"></a>Account|An [AdvertiserAccount](advertiseraccount.md) that specifies the details of the customer's primary account.|[AdvertiserAccount](advertiseraccount.md)|
|<a name="customer"></a>Customer|A [Customer](customer.md) that specifies the details of the customer that you are adding.|[Customer](customer.md)|
|<a name="parentcustomerid"></a>ParentCustomerId|The customer identifier of the aggregator that will manage the new child customer.<br/><br/>This element is required for aggregators but ignored for agencies when the [UserInvitation](#userinvitation) request element is set.|**long**|
|<a name="userinvitation"></a>UserInvitation|The user invitation to send if you want to sign up a new customer on behalf of a client and optionally link to the new account as an agency.<br/><br/>A client Super Admin user must complete sign up steps via the Microsoft Advertising UI e.g., accept the terms and conditions.<br/><br/>This element is optional and only available for agency customers in the Create Accounts on Behalf of Client pilot ([GetCustomerPilotFeatures](../customer-management-service/getcustomerpilotfeatures.md) returns 793).|[UserInvitation](userinvitation.md)|

### <a name="request-header"></a>Request Header Elements
[!INCLUDE[request-header](./includes/request-header.md)]

## <a name="response"></a>Response Elements
The *SignupCustomerResponse* object defines the [body](#response-body) and [header](#response-header) elements of the service operation response. The elements are returned in the same order as shown in the [Response SOAP](#response-soap).

### <a name="response-body"></a>Response Body Elements

|Element|Description|Data Type|
|-----------|---------------|-------------|
|<a name="accountid"></a>AccountId|A system-generated account identifier corresponding to the new account specified in the request.<br/><br/>Use this identifier with operation requests that require an *AccountId* body element and a *CustomerAccountId* SOAP header element.|**long**|
|<a name="accountnumber"></a>AccountNumber|The system-generated account number that is used to identify the account in the Microsoft Advertising web application.<br/><br/>The account number has the form *xxxxxxxx*, where *xxxxxxxx* is a series of any eight alphanumeric characters.|**string**|
|<a name="createtime"></a>CreateTime|The date and time that the account was added. The date and time value reflects the date and time at the server, not the client. For information about the format of the date and time, see the dateTime entry in [Primitive XML Data Types](https://go.microsoft.com/fwlink/?linkid=859198).|**dateTime**|
|<a name="customerid"></a>CustomerId|A system-generated customer identifier corresponding to the new customer specified in the request.<br/><br/>Use this identifier with operation requests that require a *CustomerId* SOAP header element.|**long**|
|<a name="customernumber"></a>CustomerNumber|A system-generated customer number that is used in the Microsoft Advertising web application.<br/><br/>The customer number has the form *xxxxxxxxxx*, where *xxxxxxxxxx* is a series of any ten alphanumeric characters.|**string**|

### <a name="response-header"></a>Response Header Elements
[!INCLUDE[response-header](./includes/response-header.md)]

## <a name="request-soap"></a>Request SOAP
This template was generated by a tool to show the [order](../guides/services-protocol.md#element-order) of the [body](#request-body) and [header](#request-header) elements for the SOAP request. For supported types that you can use with this service operation, see the [Request Body Elements](#request-body) reference above.

```xml
<s:Envelope xmlns:i="http://www.w3.org/2001/XMLSchema-instance" xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">
  <s:Header xmlns="https://bingads.microsoft.com/Customer/v13">
    <Action mustUnderstand="1">SignupCustomer</Action>
    <AuthenticationToken i:nil="false">ValueHere</AuthenticationToken>
    <DeveloperToken i:nil="false">ValueHere</DeveloperToken>
  </s:Header>
  <s:Body>
    <SignupCustomerRequest xmlns="https://bingads.microsoft.com/Customer/v13">
      <Customer xmlns:e1017="https://bingads.microsoft.com/Customer/v13/Entities" i:nil="false">
        <e1017:CustomerFinancialStatus i:nil="false">ValueHere</e1017:CustomerFinancialStatus>
        <e1017:Id i:nil="false">ValueHere</e1017:Id>
        <e1017:Industry i:nil="false">ValueHere</e1017:Industry>
        <e1017:LastModifiedByUserId i:nil="false">ValueHere</e1017:LastModifiedByUserId>
        <e1017:LastModifiedTime i:nil="false">ValueHere</e1017:LastModifiedTime>
        <e1017:MarketCountry i:nil="false">ValueHere</e1017:MarketCountry>
        <e1017:ForwardCompatibilityMap xmlns:e1018="http://schemas.datacontract.org/2004/07/System.Collections.Generic" i:nil="false">
          <e1018:KeyValuePairOfstringstring>
            <e1018:key i:nil="false">ValueHere</e1018:key>
            <e1018:value i:nil="false">ValueHere</e1018:value>
          </e1018:KeyValuePairOfstringstring>
        </e1017:ForwardCompatibilityMap>
        <e1017:MarketLanguage i:nil="false">ValueHere</e1017:MarketLanguage>
        <e1017:Name i:nil="false">ValueHere</e1017:Name>
        <e1017:ServiceLevel i:nil="false">ValueHere</e1017:ServiceLevel>
        <e1017:CustomerLifeCycleStatus i:nil="false">ValueHere</e1017:CustomerLifeCycleStatus>
        <e1017:TimeStamp i:nil="false">ValueHere</e1017:TimeStamp>
        <e1017:Number i:nil="false">ValueHere</e1017:Number>
        <e1017:CustomerAddress i:nil="false">
          <e1017:City i:nil="false">ValueHere</e1017:City>
          <e1017:CountryCode i:nil="false">ValueHere</e1017:CountryCode>
          <e1017:Id i:nil="false">ValueHere</e1017:Id>
          <e1017:Line1 i:nil="false">ValueHere</e1017:Line1>
          <e1017:Line2 i:nil="false">ValueHere</e1017:Line2>
          <e1017:Line3 i:nil="false">ValueHere</e1017:Line3>
          <e1017:Line4 i:nil="false">ValueHere</e1017:Line4>
          <e1017:PostalCode i:nil="false">ValueHere</e1017:PostalCode>
          <e1017:StateOrProvince i:nil="false">ValueHere</e1017:StateOrProvince>
          <e1017:TimeStamp i:nil="false">ValueHere</e1017:TimeStamp>
          <e1017:BusinessName i:nil="false">ValueHere</e1017:BusinessName>
        </e1017:CustomerAddress>
      </Customer>
      <Account xmlns:e1019="https://bingads.microsoft.com/Customer/v13/Entities" i:nil="false">
        <e1019:BillToCustomerId i:nil="false">ValueHere</e1019:BillToCustomerId>
        <e1019:CurrencyCode i:nil="false">ValueHere</e1019:CurrencyCode>
        <e1019:AccountFinancialStatus i:nil="false">ValueHere</e1019:AccountFinancialStatus>
        <e1019:Id i:nil="false">ValueHere</e1019:Id>
        <e1019:Language i:nil="false">ValueHere</e1019:Language>
        <e1019:LastModifiedByUserId i:nil="false">ValueHere</e1019:LastModifiedByUserId>
        <e1019:LastModifiedTime i:nil="false">ValueHere</e1019:LastModifiedTime>
        <e1019:Name i:nil="false">ValueHere</e1019:Name>
        <e1019:Number i:nil="false">ValueHere</e1019:Number>
        <e1019:ParentCustomerId>ValueHere</e1019:ParentCustomerId>
        <e1019:PaymentMethodId i:nil="false">ValueHere</e1019:PaymentMethodId>
        <e1019:PaymentMethodType i:nil="false">ValueHere</e1019:PaymentMethodType>
        <e1019:PrimaryUserId i:nil="false">ValueHere</e1019:PrimaryUserId>
        <e1019:AccountLifeCycleStatus i:nil="false">ValueHere</e1019:AccountLifeCycleStatus>
        <e1019:TimeStamp i:nil="false">ValueHere</e1019:TimeStamp>
        <e1019:TimeZone i:nil="false">ValueHere</e1019:TimeZone>
        <e1019:PauseReason i:nil="false">ValueHere</e1019:PauseReason>
        <e1019:ForwardCompatibilityMap xmlns:e1020="http://schemas.datacontract.org/2004/07/System.Collections.Generic" i:nil="false">
          <e1020:KeyValuePairOfstringstring>
            <e1020:key i:nil="false">ValueHere</e1020:key>
            <e1020:value i:nil="false">ValueHere</e1020:value>
          </e1020:KeyValuePairOfstringstring>
        </e1019:ForwardCompatibilityMap>
        <e1019:LinkedAgencies i:nil="false">
          <e1019:CustomerInfo>
            <e1019:Id i:nil="false">ValueHere</e1019:Id>
            <e1019:Name i:nil="false">ValueHere</e1019:Name>
          </e1019:CustomerInfo>
        </e1019:LinkedAgencies>
        <e1019:SalesHouseCustomerId i:nil="false">ValueHere</e1019:SalesHouseCustomerId>
        <e1019:TaxInformation xmlns:e1021="http://schemas.datacontract.org/2004/07/System.Collections.Generic" i:nil="false">
          <e1021:KeyValuePairOfstringstring>
            <e1021:key i:nil="false">ValueHere</e1021:key>
            <e1021:value i:nil="false">ValueHere</e1021:value>
          </e1021:KeyValuePairOfstringstring>
        </e1019:TaxInformation>
        <e1019:BackUpPaymentInstrumentId i:nil="false">ValueHere</e1019:BackUpPaymentInstrumentId>
        <e1019:BillingThresholdAmount i:nil="false">ValueHere</e1019:BillingThresholdAmount>
        <e1019:BusinessAddress i:nil="false">
          <e1019:City i:nil="false">ValueHere</e1019:City>
          <e1019:CountryCode i:nil="false">ValueHere</e1019:CountryCode>
          <e1019:Id i:nil="false">ValueHere</e1019:Id>
          <e1019:Line1 i:nil="false">ValueHere</e1019:Line1>
          <e1019:Line2 i:nil="false">ValueHere</e1019:Line2>
          <e1019:Line3 i:nil="false">ValueHere</e1019:Line3>
          <e1019:Line4 i:nil="false">ValueHere</e1019:Line4>
          <e1019:PostalCode i:nil="false">ValueHere</e1019:PostalCode>
          <e1019:StateOrProvince i:nil="false">ValueHere</e1019:StateOrProvince>
          <e1019:TimeStamp i:nil="false">ValueHere</e1019:TimeStamp>
          <e1019:BusinessName i:nil="false">ValueHere</e1019:BusinessName>
        </e1019:BusinessAddress>
        <e1019:AutoTagType i:nil="false">ValueHere</e1019:AutoTagType>
        <e1019:SoldToPaymentInstrumentId i:nil="false">ValueHere</e1019:SoldToPaymentInstrumentId>
      </Account>
      <ParentCustomerId i:nil="false">ValueHere</ParentCustomerId>
      <UserInvitation xmlns:e1022="https://bingads.microsoft.com/Customer/v13/Entities" i:nil="false">
        <e1022:Id>ValueHere</e1022:Id>
        <e1022:FirstName i:nil="false">ValueHere</e1022:FirstName>
        <e1022:LastName i:nil="false">ValueHere</e1022:LastName>
        <e1022:Email i:nil="false">ValueHere</e1022:Email>
        <e1022:CustomerId>ValueHere</e1022:CustomerId>
        <e1022:RoleId>ValueHere</e1022:RoleId>
        <e1022:AccountIds i:nil="false" xmlns:a1="http://schemas.microsoft.com/2003/10/Serialization/Arrays">
          <a1:long>ValueHere</a1:long>
        </e1022:AccountIds>
        <e1022:ExpirationDate>ValueHere</e1022:ExpirationDate>
        <e1022:Lcid>ValueHere</e1022:Lcid>
      </UserInvitation>
    </SignupCustomerRequest>
  </s:Body>
</s:Envelope>
```

## <a name="response-soap"></a>Response SOAP
This template was generated by a tool to show the order of the [body](#response-body) and [header](#response-header) elements for the SOAP response.

```xml
<s:Envelope xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">
  <s:Header xmlns="https://bingads.microsoft.com/Customer/v13">
    <TrackingId d3p1:nil="false" xmlns:d3p1="http://www.w3.org/2001/XMLSchema-instance">ValueHere</TrackingId>
  </s:Header>
  <s:Body>
    <SignupCustomerResponse xmlns="https://bingads.microsoft.com/Customer/v13">
      <CustomerId>ValueHere</CustomerId>
      <CustomerNumber d4p1:nil="false" xmlns:d4p1="http://www.w3.org/2001/XMLSchema-instance">ValueHere</CustomerNumber>
      <AccountId d4p1:nil="false" xmlns:d4p1="http://www.w3.org/2001/XMLSchema-instance">ValueHere</AccountId>
      <AccountNumber d4p1:nil="false" xmlns:d4p1="http://www.w3.org/2001/XMLSchema-instance">ValueHere</AccountNumber>
      <CreateTime>ValueHere</CreateTime>
    </SignupCustomerResponse>
  </s:Body>
</s:Envelope>
```

## <a name="example"></a>Code Syntax
The example syntax can be used with [Bing Ads SDKs](../guides/client-libraries.md). See [Bing Ads API Code Examples](../guides/code-examples.md) for more examples.
```csharp
public async Task<SignupCustomerResponse> SignupCustomerAsync(
	Customer customer,
	AdvertiserAccount account,
	long? parentCustomerId,
	UserInvitation userInvitation)
{
	var request = new SignupCustomerRequest
	{
		Customer = customer,
		Account = account,
		ParentCustomerId = parentCustomerId,
		UserInvitation = userInvitation
	};

	return (await CustomerManagementService.CallAsync((s, r) => s.SignupCustomerAsync(r), request));
}
```
```java
static SignupCustomerResponse signupCustomer(
	Customer customer,
	AdvertiserAccount account,
	java.lang.Long parentCustomerId,
	UserInvitation userInvitation) throws RemoteException, Exception
{
	SignupCustomerRequest request = new SignupCustomerRequest();

	request.setCustomer(customer);
	request.setAccount(account);
	request.setParentCustomerId(parentCustomerId);
	request.setUserInvitation(userInvitation);

	return CustomerManagementService.getService().signupCustomer(request);
}
```
```php
static function SignupCustomer(
	$customer,
	$account,
	$parentCustomerId,
	$userInvitation)
{

	$GLOBALS['Proxy'] = $GLOBALS['CustomerManagementProxy'];

	$request = new SignupCustomerRequest();

	$request->Customer = $customer;
	$request->Account = $account;
	$request->ParentCustomerId = $parentCustomerId;
	$request->UserInvitation = $userInvitation;

	return $GLOBALS['CustomerManagementProxy']->GetService()->SignupCustomer($request);
}
```
```python
response=customermanagement_service.SignupCustomer(
	Customer=Customer,
	Account=Account,
	ParentCustomerId=ParentCustomerId,
	UserInvitation=UserInvitation)
```

## Requirements
Service: [CustomerManagementService.svc v13](https://clientcenter.api.bingads.microsoft.com/Api/CustomerManagement/v13/CustomerManagementService.svc)  
Namespace: https\://bingads.microsoft.com/Customer/v13  

