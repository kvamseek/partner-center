---
title: Partner Center REST error codes
description: Description of error codes and success responses from the Partner Center APIs.
ms.service: partner-dashboard
ms.subservice: partnercenter-api
ms.topic: article
# Acrolinx: The score of this doc is 70, since the error text is coming from outside source. We cannot change that text.
author: vijay-vala
ms.author: vijvala
ms.date: 06/15/2023
---

# Partner Center REST error codes

**Applies to**: Partner Center | Partner Center operated by 21Vianet |  Partner Center for Microsoft Cloud for US Government

The Partner Center REST APIs return a JSON object that contains a status code. This code that indicates whether your request was successful or why it failed.

## Success responses

A **2xx** status code indicates that the client's request was successfully received, understood, and accepted.

## HTTP status codes

The following **4xx** and **5xx** status codes indicate an error:

- 400: Bad request
- 401: Unauthorized
- 403: Forbidden
- 404: Not found
- 405: Method not allowed
- 406: Not acceptable
- 408: Request timeout
- 409: Conflict
- 412: Precondition failed
- 429: Too many requests
- 500: Internal server error
- 501: Not implemented
- 502: Bad gateway
- 503: Service unavailable
- 504: Gateway timeout

## Error responses

Any response with a **4xx** or **5xx** status code includes an error message with details about the error condition(s) for that code.

The following table and code sample describes the schema of an error response:

| Name   | Type   | Description |
|-------------|--------|------|
| code   | string | Always returned. Indicates the kind of error that occurred. Non-null.  |
| description | string | Always returned. Describes the error in detail, and provides debugging information. Non-null, non-empty. Maximum length is 1024 characters. |
| data   | array  | Only returned for some error types. A list of error objects. |
| source | string | Always returned. The source of the error. |

```json
{
  "code": <string>,
  "description": <string>,
  "data": [

  ],
  "source": <string>
}
WWW-Authenticate: OAuth realm=urn:cpsvc:cpid:{some cid}
```

## Error codes

The following are error codes returned by the APIs:

| HTTP Status    | HTTP Error Code | Error code | Description |
|---------------------|-----------------|------------|----------------|
| OK | 200 | 400072 | This item isn't available. [Learn more](https://go.microsoft.com/fwlink/p/?linkid=2164140) |
| NotImplemented | 501  | 0 | Exception not defined  |
| Unauthorized   | 401  | 400   | Access denied    |
| NotFound | 404  | 1000  | Not found  |
| Forbidden | 403  | 2006  | Partner isn't valid for offer |
| BadRequest | 400  | 2012  | Unable to convert between Commerce and Azure Active Directory subscription IDs. |
| Forbidden | 403  | 2030  | Partner isn't onboarded to sell in country/region |
| Forbidden | 403  | 2032  | Access denied    |
| Forbidden | 403  | 2091  | The offer is no longer available for purchase   |
| BadRequest | 400  | 2100  | The Offers API doesn't support item with ID {0}. Try using the Products and/or SKUs APIs |
| BadRequest | 400  | 3000  | Invalid property |
| Forbidden | 403  | 20002 | The partner ID {0} has no commerce relationship with the customer ID {1}. |
| NotFound | 404  | 20003 | Subscription with ID {0} not found. |
| BadRequest | 400  | 27007 | Invalid promotion code    |
| BadRequest | 400  | 60000 | The customer license migration failed |
| NotFound | 404  | 60002 | User object ID isn't found  |
| NotFound | 404  | 60003 | Tenant not found |
| BadRequest | 400  | 2001  | Subscription quantity can't be increased or decreased while subscription is being suspended |
| BadRequest | 400  | 2002  | Subscription quantity isn't within minimum and maximum allowed quantity |
| BadRequest | 400  | 2006  | Updates on subscriptions for offer {0} aren't allowed |
| BadRequest | 400  | 2011  | Subscription with ID {0} and deleted status can't be updated.    |
| BadRequest | 400  | 2054  | The billing cycle for an existing subscription can't be updated using update-subscription operation. Use update-Order operation |
| BadRequest | 400  | 2055  | Etag is no longer valid |
| BadRequest | 400  | 2071  | PartnerID isn't a valid Advisor |
| NotFound | 404  | 2072  | PartnerID of Indirect Provider isn't valid as Partner On Record |
| Forbidden | 403  | 2085  | The offer isn't eligible for purchase |
| BadRequest | 400  | 4018  | Unable to process this order |
| BadRequest | 400  | 6000  | The billing cycle couldn't be changed because the order contains one or more subscriptions that aren't active    |
| BadRequest | 400  | 6001  | The billing cycle couldn't be changed because one of the order's Offer IDs doesn't support the billing term |
| Forbidden | 403  | 13605 | Either a partner confirmation of the customer acceptance of the Microsoft Customer Agreement must be provided or the customer must accept the Microsoft Customer Agreement in the Microsoft Admin Center before you can complete this purchase |
| NotFound | 404  | 20000 | Order ID not found |
| BadRequest | 400  | 27006 | Use limit is exceeded for Offer ID |
| Conflict | 409  | 27009 | can't enable a child subscription, when the parent subscription isn't Active |
| NotFound | 404  | 400013 | Product wasn't found |
| NotFound | 404  | 400018 | SKU wasn't found |
| NotFound | 404  | 400019 | Availability not found. This error can occur when checking out a cart. Partners that get this error should issue a new GET to ensure they have the current availability ID and retry the cart check out.    |
| BadRequest | 400  | 600002 | Organization registration ID value isn't supported  <br/><br/>This error occurs if the customer's company/organization is **not** located in one of the following countries/regions, but they tried to specify organizationRegistrationNumber. Countries/regions affected:<br/><br/>- Armenia (AM) <br/>- Azerbaijan (AZ)<br/>- Belarus (BY)<br/>- Hungary (HU)<br/>- India (IN)<br/>- Kazakhstan (KZ)<br/>- Kyrgyzstan (KG)<br/>- Moldova (MD)<br/>- Russia (RU)<br/>- Tajikistan (TJ)<br/>- Uzbekistan (UZ)<br/>- Ukraine (UA) |
| BadRequest | 400  | 600049 | Organization registration ID information is missing <br/><br/>This error occurs if the customer's company/organization is located in one of the following countries/regions and the organizationRegistrationNumber hasn't been provided. Countries/regions affected:<br/><br/>- Armenia (AM) <br/>- Azerbaijan (AZ)<br/>- Belarus (BY)<br/>- Hungary (HU)<br/>- India (IN)<br/>- Kazakhstan (KZ)<br/>- Kyrgyzstan (KG)<br/>- Moldova (MD)<br/>- Russia (RU)<br/>- Tajikistan (TJ)<br/>- Uzbekistan (UZ)<br/>- Ukraine (UA)  |
| BadRequest | 400  | 600050 | Organization registration ID information is invalid and should be of the format \{0\} <br/><br/>This error occurs if the organizationRegistrationNumber isn't valid for the customer's company located country/region. \{0\} will have the expected regular expression format of the error. For example: `Organization registration ID information is invalid and should be of the format ^(\\d{7}|\\d{10})$`. |
| BadRequest | 400  | 600051 | Customer phone number is missing <br/><br/>This error occurs if the customer's company/organization is located in one of the following countries/regions but billingProfile.defaultAddress.phoneNumber isn't provided. Countries/regions affected:<br/><br/>- Armenia (AM) <br/>- Azerbaijan (AZ)<br/>- Belarus (BY)<br/>- Hungary (HU)<br/>- India (IN)<br/>- Kazakhstan (KZ)<br/>- Kyrgyzstan (KG)<br/>- Moldova (MD)<br/>- Russia (RU)<br/>- Tajikistan (TJ)<br/>- Uzbekistan (UZ)<br/>- Ukraine (UA)  |
| Unauthorized   | 401  | 800001 | Partner Token missing in request context   |
| BadRequest | 400  | 800002 | Invalid request input  |
| InternalServerError | 500  | 800003 | Unexpected service error |
| BadRequest | 400  | 800004 | Invalid offer ID |
| InternalServerError | 500  | 800005 | Create order isn't successful |
| NotFound | 404  | 800007 | Unable to retrieve provisioning information |
| NotFound | 404  | 800008 | Unable to retrieve cart ID   |
| BadRequest | 400  | 800009 | Error in Cart item(s)  |
| BadRequest | 400  | 800010 | Inventory isn't available for this catalog item |
| BadRequest | 400  | 800011 | This subscription isn't a valid Azure subscription   |
| BadRequest | 400  | 800012 | This subscription isn't an active subscription |
| BadRequest | 400  | 800013 | This subscription isn't enabled for RI purchase |
| Conflict | 409  | 800014 | There's a pending adjustment requested for this order |
| NotFound | 404  | 800015 | PartnerID isn't found    |
| BadRequest | 400  | 800016 | PartnerID isn't a valid Indirect Reseller    |
| BadRequest | 400  | 800017 | The quantity isn't available for this catalog item   |
| BadRequest | 400  | 800018 | The sandbox limit has been met |
| Forbidden | 403  | 800019 | Non-Sandbox tenants aren't allowed to cancel purchases other than software subscriptions and perpetual software   |
| Forbidden | 403  | 800020 | The catalog item isn't eligible for purchase.  |
| BadRequest | 400  | 800021 | This subscription isn't a valid subscription   |
| BadRequest | 400  | 800022 | You may be eligible for this transaction. Contact Support for help |
| Forbidden | 403  | 800023 | You aren't eligible for this transaction because your Credit Line isn't reaching minimum threshold for this purchase. Update your order (or) contact Support for help  |
| BadRequest | 400  | 800024 | You aren't eligible for this transaction  |
| BadRequest | 400  | 800025 | You aren't eligible for this transaction because your Credit Line isn't reaching minimum threshold for this purchase. Update your order (or) contact Support for help  |
| BadRequest | 400  | 800026 | You aren't eligible for this transaction  |
| Forbidden | 403  | 800027 | The catalog item isn't eligible for add or remove quantity |
| Forbidden | 403  | 800028 | The initial purchase term is no longer available for purchase/update    |
| BadRequest | 400  | 800029 | The add-on isn't related to the specified parent subscription    |
| BadRequest | 400  | 800030 | This subscription isn't registered |
| InternalServerError | 500  | 800031 | Purchase system not supported |
| ExpectationFailed   | 417  | 800036 | Pre-condition failed   |
| NotFound | 404  | 800037 | Asset ID not found |
| NotFound | 404  | 800038 | Asset FutureBillingInfo not found  |
| Forbidden | 403  | 800039 | Reseller program status isn't active |
| BadRequest | 400  | 800040 | Asset status can't be changed to {0} from {1}  |
| BadRequest | 400  | 800041 | This item has already been activated  |
| BadRequest | 400  | 800042 | Not supported    |
| Forbidden | 403  | 800043 | Access to pricing information isn't granted    |
| Conflict | 409  | 800060 | Your order is in progress. Check your order history for recent orders in few minutes |
| BadRequest | 400  | 800061 | Order can't be canceled    |
| BadRequest | 400  | 800062 | You aren't eligible for this transaction  |
| BadRequest | 400  | 800063 | This order {0} can't be canceled. Use PATCH /customers/{1}/subscriptions/\<subscriptionId\> to suspend subscriptions |
| Conflict | 409  | 800064 | Cart {0} is being processed by another request  |
| BadRequest | 400  | 800065 | can't check out an already submitted cart {0}. |
| Forbidden | 403  | 800066 | The desired number of subscriptions exceeded the maximum number of subscriptions allowed per customer  |
| Forbidden | 403  | 800067 | The desired seat count exceeded the maximum seat count allowed per subscription |
| Forbidden | 403  | 800068 | The desired number of subscriptions exceeded the maximum number of Azure subscriptions allowed per partner   |
| Forbidden | 403  | 800069 | Order failed Risk Management check |
| BadRequest | 400  | 800070 | Offer isn't available in the specified country/region |
| BadRequest | 400  | 800071 | Line Item number should be from 0 to number of line items count   |
| BadRequest | 400  | 800071 | Line Item number should be from 0 to number of line items count   |
| BadRequest | 400  | 800072 | can't change billing cycle if subscription's SyncState isn't Completed |
| Forbidden | 403  | 800073 | Your customer account is currently under review. Check back in few days. Your patience is appreciated during this time. Learn more at {0}    |
| Forbidden | 403  | 800074 | Your customer account is currently under review. Check back in few days. Your patience is appreciated during this time. Learn more at {0}    |
| Forbidden | 403  | 800075 | Your Customer account wasn't approved. Transactions for this customer aren't allowed. Verify the customer account information is correct. For more information, refer to {0}  |
| NotFound | 404  | 800076 | Subscription history not found |
| Forbidden | 403  | 800077 | Cancelling of seat-based SaaS isn't supported via patch order. Use patch subscription instead.  |
| BadRequest | 400  | 800078 | Transfer can't be created with invalid subscription  |
| BadRequest | 400  | 800080 | Can't change billing cycle if subscription isn't associated with a Mint account   |
| BadRequest | 400  | 800081 | Can't update a subscription before activating it |
| Conflict  | 409  | 800082 | Subscription is not ready to be updated. Try again after sometime |
| InternalServerError | 500  | 800083 | Availability has more than one included quantity options    |
| InternalServerError | 500  | 800084 | Unsupported duration {0} |
| BadRequest | 400  | 800085 | Subscription's billing cycle doesn't match with the original order billing cycle   |
| BadRequest | 400  | 800086 | Customer tenant doesn't have required tags for the offer   |
| InternalServerError | 500  | 800087 | There's an issue with the line item. |
| Forbidden | 403  | 800088 | The requested number of {0} seat/s exceeded the remaining limit of {1} seats allowed per subscription for the CatalogID - {2}  |
| Forbidden | 403  | 800089 | The requested number of {0} asset/s exceeded the remaining limit of {1} assets allowed per customer    |
| BadRequest | 400  | 800090 | Subscription quantity can't be decreased  |
| BadRequest | 400  | 800091 | Can't update a subscription with suspended status    |
| BadRequest | 400  | 800092 | Can't increase the seat quantity for a subscription purchased under the Software Assurance program    |
| BadRequest | 400  | 800093 | The subscription isn't eligible to be auto-renewed   |
| InternalServerError | 500  | 800094 | Update subscription isn't successful |
| BadRequest | 400  | 800095 | Can't update the seat quantity for this subscription |
| BadRequest | 400  | 800096 | Can't update the status for this subscription  |
| BadRequest | 400  | 800097 | Can't update the billing cycle for this subscription |
| BadRequest | 400  | 800098 | Can't update the partner on record for this subscription   |
| NotFound | 404  | 800111 | Azure subscription with the given entitlement ID isn't found.  |
| Forbidden | 403  | 800115 | Overage is already assigned to another tenant. Contact your customer to resolve ownership questions.  |
| Forbidden | 403  | 800114 | You aren't eligible to manage overage for this customer.  |
| Forbidden | 403  | 800112 | Overage can't be set as the customer has legacy Azure subscriptions.  |
| NotFound | 404  | 900100 | Transfer request not found   |
| Conflict | 409  | 900101 | This transfer isn't allowed as original transfer {0} is in progress    |
| BadRequest | 400  | 900102 | Can't process the transfer request for {1} transfer {0}    |
| InternalServerError | 500  | 900103 | Transfer order isn't successful   |
| Conflict | 409  | 900104 | Transfer {0} is being processed by another request    |
| Forbidden | 403  | 900105 | You have one or more Azure subscriptions in the suspended state. Suspended Azure subscriptions can't be transitioned to the Azure plan |
| NotFound | 404  | 900106 | No upgrade request was found |
| BadRequest | 400  | 900107 | Can't process Azure upgrade since Azure catalog item wasn't found |
| Forbidden | 403  | 900108 | Can't process Azure upgrade since customer has no Azure subscriptions. |
| Conflict | 409  | 900109 | This upgrade isn't allowed as original upgrade {0} is in progress |
| BadRequest | 400  | 900110 | Can't process the upgrade request for completed upgrade {0} |
| BadRequest | 400  | 900111 | The upgrade ID provided doesn't belong to customer {0}. The customer is mapped to upgrade ID {1} |
| Conflict | 409  | 900112 | This purchase isn't allowed as the upgrade request {0} is in pending state   |
| Conflict | 409  | 900113 | This purchase isn't allowed as the upgrade request {0} is in progress  |
| Conflict | 409  | 900114 | This purchase isn't allowed as the upgrade request {0} failed    |
| Forbidden | 403  | 900115 | Azure plan can't be moved to suspended state since you have one or more Azure Subscriptions in the active state   |
| BadRequest | 400  | 900116 | Unable to create order. There's a limit to how many Azure plans can be created under sandbox accounts |
| BadRequest | 400  | 900117 | You have passed your {0}-day cancellation window. We are unable to cancel your purchase |
| BadRequest | 400  | 900118 | Invalid Customer ID    |
| Forbidden | 403  | 900119 | Can't process Azure upgrade for Azure Partner Shared Services    |
| Forbidden | 403  | 900120 | Can't process Azure upgrade |
| Forbidden | 403  | 900121 | Unable to process order due to insufficient credit limit, please contact ucmwrcsp@microsoft.com for further assistance   |
| NotFound | 404  | 900122 | Advisor quote not found |
| Forbidden | 403  | 900123 | Microsoft Partner Agreement hasn't been accepted by the indirect reseller    |
| Forbidden | 403  | 900124 | Your company hasn't accepted the Microsoft Partner Agreement (MPA). The global admin of the CSP account must accept the MPA to resume the full transactional capabilities. Search {0} for your global admin and have them sign the MPA on the dashboard {1} to resume full transactional capabilities |
| BadRequest | 400  | 900125 | Advisor partner information not found in the request context |
| BadRequest | 400  | 900126 | Unable to parse enum: {0} For more information, please visit {1}  |
| BadRequest | 400  | 900127 | This operation isn't supported in this environment   |
| BadRequest | 400  | 900128 | An Azure plan is required to purchase a SaaS subscription with a metered billing plan  |
| BadRequest | 400  | 900129 | The specified Azure plan ID wasn't found or there are no active Azure subscriptions under it. An Azure plan with active subscription(s) is required to purchase a SaaS product with a metered billing plan    |
| Forbidden | 403  | 900130 | One or more Azure subscriptions were purchased recently, these subscriptions can't be transitioned at this time. Try again later |
| BadRequest | 400  | 900131 | This transfer request can't be initiated as the customer has legacy Azure subscriptions    |
| BadRequest | 400  | 900132 | This transfer request can't be initiated as the Azure plan isn't active, please enable the Azure plan |
| BadRequest | 400  | 900133 | This transfer request can't be initiated as customer hasn't purchased Azure plan  |
| BadRequest | 400  | 900134 | This transfer request can't be initiated as the Azure plan isn't purchasable |
| InternalServerError | 500  | 900135 | Initiate transfer request failed. Try again later    |
| BadRequest | 400  | 900136 | Transfer can't be initiated as source partner email/domain details missing in the request  |
| Forbidden | 403  | 900137 | Transfer can't be created as partner: {0} not enabled for this feature |
| Forbidden | 403  | 900138 | Transfer can't be created as partner's: {0} national cloud {1} isn't supported    |
| Forbidden | 403  | 900139 | Transfer request can't be accepted. Please request the partner to create transfer without Azure subscription(s)   |
| NotFound | 404  | 900140 | Unable to get Azure Active Directory subscriptions for a customer with tenant ID {0} and source provisioning ID {1} |
| BadRequest | 400  | 900141 | This operation isn't supported    |
| BadRequest | 400  | 900142 | The catalog item ID isn't present |
| BadRequest | 400  | 900143 | The request failed to retrieve all availabilities with productId: {0}, skuId: {1} for a customer with ID: {3} |
| BadRequest | 400  | 900144 | The provisioning SKU ID isn't present |
| BadRequest | 400  | 900145 | This request for transfer of billing ownership can't be completed as Azure reservations don't transfer with subscriptions. Cancel the Azure reservations associated with the subscriptions in your selection and try again.    |
| BadRequest | 400  | 900146 | This request for transfer of billing ownership can't be completed as third-party marketplace products don't transfer with subscriptions. Remove the third-party marketplace products from your selection and try again.  |
| BadRequest | 400  | 900147 | Provide a valid domain associated with the current partner  |
| BadRequest | 400  | 900148 | Transfer creation failed due to source partner details matched with requesting partner |
| Forbidden | 403  | 900149 | {0} program status isn't active.  |
| Forbidden | 403  | 900150 | The supplied role doesn't have the rights to perform the requested operation |
| BadRequest  | 400  | 900169 | One or more of the order items do not support the given currency, USD. Input currency should be either partner or customer (market) currency. |
| InternalServerError | 500  | 900192 | Something went wrong. Try again after some time.  |
| BadRequest | 400  | 900203 | CatalogItemId: {0} requires attestation acceptance.   |
| BadRequest  | 400  | 900206 | Partner Attestation is missing |
| BadRequest | 400  | 900213 | You have passed your {0}-hour cancellation window. We are unable to cancel your purchase   |
| BadRequest | 400  | 900214 | You have passed your {0}-hour window for reducing seats for this subscription.   |
|BadRequest|400|900215|Subscription {0} cannot be migrated to New Commerce because the status is not active.|
|BadRequest|400|900216|Subscription {0} cannot be migrated to New Commerce because the subscription is currently being processed.|
|BadRequest|400|900217|Subscription {0} cannot be migrated to New Commerce because it is less than 24 hours from the term end.|
|BadRequest|400|900218|Subscription {0} cannot be migrated to New Commerce because it has promotions applied to it.|
|BadRequest|400|900219|Subscription {0} cannot be migrated to New Commerce because it has add-ons.|
|BadRequest|400|900220|Subscription {0} cannot be migrated to New Commerce because there is not a valid migration path for this offer yet.|
|BadRequest|400|900221|Subscription {0} cannot be migrated to New Commerce because of one or more reasons (possible reasons: subscription not in Active state - subscription has promotions applied to it - subscription has add-ons attached to it - subscription is too close to term end - subscription offer is not available in New Commerce yet).|
|BadRequest|400|900222|Subscription {0} cannot be migrated to New Commerce because the combination of term duration and billing cycle is not supported for the New-Commerce product.|
|Forbidden|403|900223|Partner tenant ID {0} is not yet allowed to perform migrations to New Commerce on their subscriptions.|
|BadRequest|400|900224|New-Commerce migration {0} could not be found.|
|RequestTimeout|408|900225|There was an unexpected error when processing the New-Commerce migration.|
|Forbidden|403|900226|Subscription {0} cannot be migrated to New Commerce because it has been active for 1 month or less. Please try again later.|
|BadRequest|400|900242|The custom term end date specified for line item 0 does not match with the end date of any active non-trial OnlineServicesNCE subscription or align with the end of the calendar month. Partners should select a new custom term end date.|
|BadRequest|400|900247|Subscription {0} cannot be migrated to New Commerce because the partner ID on record in the current subscription is not valid.|
|BadRequest|400|900248|Migration cannot be performed because two or more add-on migrations were specified with the same current subscription ID|
| BadRequest | 400  | 900257 | You have passed your {0}-day window for reducing seats for this subscription.   |
| BadRequest | 400  | 900258 | The target transition ToSubscriptionId field is invalid. Target subscription must be active.   |
| BadRequest | 400  | 900259 | The target transition ToSubscriptionId field is invalid. Target subscription id can't be the same as the source subscription ID.   |
| BadRequest | 400  | 900236 | The target transition ToSubscriptionId field is invalid. Target subscription CommitmentEndDate must be later than source subscription   |
| BadRequest | 400  | 900260 | The target transition ToSubscriptionId field is invalid. Target subscription must have the same CatalogItemId as in the transition request.   |
| BadRequest | 400  | 900261 | The target transition ToSubscriptionId field is invalid. The target subscription is not ready to be upgraded. Please try again after sometime.   |
| BadRequest | 400  | 900262 | Subscription cannot be migrated to New-Commerce because one or more add-on subscriptions specified in the AddOnMigrations collection do not exist or are not active.   |
| Forbidden | 403  | 900263 | This API method is not supported for legacy subscriptions.|
| BadRequest | 400  | 900267 | Target transition can't have a term duration shorter than that of the source subscription.   |
| BadRequest | 400  | 900268 | The term duration on the target transition is invalid.   |
| BadRequest | 400  | 900269 | The billing cycle is invalid.   |
| BadRequest | 400  | 900270 | The billing cycle cannot be longer than the term.  |
| Conflict  | 409  | 900278 | There is a pending operation on this subscription. Please try again after 24 hours.  |
| BadRequest | 400  | 900279 | Update operations are no longer allowed for this subscription. |
| BadRequest | 400  | 900280 | Update operations are currently not allowed for this subscription.  |
| BadRequest | 400  | 600049 | Organization registration ID information is missing. This error is thrown if the customer's company or organization is located in the following countries/regions: Armenia(AM), Azerbaijan(AZ), Belarus(BY), Hungary(HU), India (IN), Kazakhstan(KZ), Kyrgyzstan(KG), Moldova(MD), Russia(RU), Tajikistan(TJ), Uzbekistan(UZ), Ukraine(UA)but organizationRegistrationNumber isn't passed in. |
| BadRequest | 400  | 600050 | Organization registration ID information is invalid and should be of the format `{0}`. This error is thrown if the organizationRegistrationNumber that is passed in isn't valid for the customer's company located country/region. {0} will have the expected regular expression format of the error. Eg: Organization registration ID information is invalid and should be of the format `^(\\d{7}|\\d{10})$` |
| BadRequest | 400  | 600051 | Customer phone number is missing. This error is thrown if the customer's company or organization is located in the following countries/regions: Armenia(AM), Azerbaijan(AZ), Belarus(BY), Hungary(HU), India (IN), Kazakhstan(KZ), Kyrgyzstan(KG), Moldova(MD), Russia(RU), Tajikistan(TJ), Uzbekistan(UZ), Ukraine(UA) but billingProfile.defaultAddress.phoneNumber isn't passed in.  |
| BadRequest | 400  | 600002 | Organization registration ID value isn't supported. This error is thrown if the customer's company or organization isn't located in the following countries/regions: Armenia (AM), Azerbaijan (AZ), Belarus (BY), Hungary (HU), India (IN), Kazakhstan (KZ), Kyrgyzstan (KG), Moldova (MD), Russia (RU), Tajikistan (TJ), Uzbekistan (UZ), Ukraine (UA), but they tried to specify organizationRegistrationNumber.  |
| BadRequest | 400  | 900244 | The custom term end date specified on the scheduled next term instructions is only valid for OnlineServicesNCE products. |
| BadRequest | 400  | 900245 | The custom term end date specified on the scheduled next term instructions must be within the first term duration after renewal. Also monthly term products cannot align with a subscription ending on the 28th, 29th, or 30th of the month, unless that date is the last day of the month. |
| BadRequest | 400  | 900246 | The custom term end date specified on the scheduled next term instructions does not match with the end date of any active non-trial OnlineServicesNCE subscription or align with the end of the calendar month. |
| BadRequest | 400 | 900252 | Purchase order document is required. |
| BadRequest | 400 | 900253 | When part of tender, either tender link or tender document is required. |
| BadRequest | 400 | 900254 | Invalid metadata. (If the customer price, currency is missing). |
| BadRequest | 400 | 900275 | The requested quantity for line item {0} is not within the allowed quantity for this offer. |
| BadRequest | 400 | 900277 | Your subscription is in the process of being expired. No further updates are allowed on this subscription. |
| BadRequest | 400 | 900291 | The custom term end date specified for the migration must be within the first term duration. Also, monthly term products cannot align with a subscription ending on the 28th, 29th, or 30th of the month, unless that date is the last day of the month.|
| BadRequest | 400 | 900292 | The custom term end date specified for the migration does not match with the end date of any active non-trial OnlineServicesNCE subscription or align with the end of the calendar month.|
| Forbidden | 403 | 900308 | Insufficient privileges to complete the operation.|
| Forbidden  | 403 | 900309 | Access has been blocked by Conditional Access policies. The access policy does not allow token issuance.  Learn more at Users and groups [in Conditional Access policy - Microsoft Entra](/azure/active-directory/conditional-access/concept-conditional-access-users-groups). |
| BadRequest | 400 | 900311 | This subscription has been updated too many times. Please contact partner support if you need to make more updates on this subscription.|
| BadRequest | 400 | 900316 | Partner token is not allowed in license management calls. Please call with partner access token. |
| BadRequest | 400 | 800107 | Term changes are not supported for trial offers. |
| BadRequest | 400 | 800121 | The term duration provided is invalid. |
| BadRequest | 400 | 800122 | The target term duration cannot be shorter than the current term duration.   |
| BadRequest | 400 | 900312 | The selected scope '{0}' in the provisioning context is not supported. |
| BadRequest | 400 | 900313 | Entitlement ID (Azure subscription ID) in the provisioning context is required for the transaction. |
| BadRequest | 400 | 900314 | The Azure subscription associated with the entitlement ID is not active. An active Azure subscription is required to complete the purchase. |
| BadRequest | 400 | 900315 | This product is not eligible for purchase using the provided Azure subscription. |
| BadRequest | 400 | 900317 | Subscription ID (Azure plan ID) in the provisioning context is required for the transaction. |
| BadRequest | 400 | 900318 | The Azure plan associated with the subscription ID was not found or there are no active Azure subscriptions under it. An Azure Plan with active subscription(s) is required to complete the purchase. |
| Forbidden | 403 | 900321 | This operation is not supported for Azure savings plan in Partner Center today. It can however be managed in Azure portal. |
| Forbidden | 403 | 900322 | {0} is not available to purchase in the Sandbox environment. Learn more at {1}. |
| Forbidden | 403 | 900323 | Azure savings plan purchases will inherit the partner on record of the associated Azure Plan. The provided partner on record does not match the value ({0}) on the associated Azure Plan. |
| Forbidden | 403 | 900329 | This resource does not support application-only authentication. |
