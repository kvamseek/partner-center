---
title: Upload a list of devices to an existing batch for the specified customer
description: How to upload a list of information about devices to an existing batch for the specified customer. This associates the devices with a device batch already created.
ms.date: 09/22/2023
ms.service: partner-dashboard
ms.subservice: partnercenter-api
ms.topic: article
author: amitravat
ms.author: amrava
---

# Upload a list of devices to an existing batch for the specified customer

**Applies to**: Partner Center

How to upload a list of information about devices to an existing batch for the specified customer. This associates the devices with a device batch already created.

## Prerequisites

- Credentials as described in [Partner Center authentication](partner-center-authentication.md). This scenario supports authentication with both standalone App and App+User credentials.

- A customer ID (`customer-tenant-id`). If you don't know the customer's ID, you can look it up in [Partner Center](https://partner.microsoft.com/dashboard) by selecting the **Customers** workspace, then the customer from the customer list, then **Account**. On the customer's Account page, look for the **Microsoft ID** in the **Customer Account Info** section. The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).

- The device batch identifier.

- The list of device resources that provide the information about the individual devices.

## GDAP roles

You'll need at least one of the following GDAP roles:

- Intune Administrator
- Cloud Device Administrator
- Windows 365 Administrator
- Directory Reader
- Global reader
- User Administrator
- Privileged Role Administrator
- Directory Writers

## C\#

To upload a list of devices to an existing device batch, first, instantiate a new [List/dotnet/api/system.collections.generic.list-1) of type [**Device**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.device) and populate the list with the devices. The following combinations of populated properties are required at a minimum for identifying each device:

- [**HardwareHash**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.device.hardwarehash) + [**ProductKey**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.device.productkey).

- [**HardwareHash**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.device.hardwarehash) + [**SerialNumber**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.device.serialnumber).

- [**HardwareHash**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.device.hardwarehash) + [**ProductKey**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.device.productkey) + [**SerialNumber**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.device.serialnumber).

- [**HardwareHash**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.device.hardwarehash) only.

- [**ProductKey**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.device.productkey) only.

- [**SerialNumber**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.device.serialnumber) + [**OemManufacturerName**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.device.oemmanufacturername) + [**ModelName**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.device.modelname).

Then, call the [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) method with the customer identifier to retrieve an interface to operations on the specified customer. Next, call the [**DeviceBatches.ById**](/dotnet/api/microsoft.store.partnercenter.devicesdeployment.idevicesbatchcollection.byid) method with the device batch identifier to get an interface to operations for the specified batch. Finally, call the [**Devices.Create**](/dotnet/api/microsoft.store.partnercenter.devicesdeployment.idevicecollection.create) or [**CreateAsync**](/dotnet/api/microsoft.store.partnercenter.devicesdeployment.idevicecollection.createasync) method with the list of devices to add the devices to the device batch.

``` csharp
IAggregatePartner partnerOperations;
string selectedCustomerId;
string selectedDeviceBatchId;

List<Device> devicesToBeUploaded = new List<Device>
{
    new Device
    {
        HardwareHash = "DummyHash1234",
        ProductKey = "00329-00000-0003-AA606",
        SerialNumber = "2R9-ZNP67"
    },

    new Device
    {
        HardwareHash = "DummyHash12345",
        ProductKey = "00329-00000-0003-AA606",
        SerialNumber = "2R9-ZNP67"
    }
};

var trackingLocation =
    partnerOperations.Customers.ById(selectedCustomerId).DeviceBatches.ById(selectedDeviceBatchId).Devices.Create(devicesToBeUploaded);
```

**Sample**: [Console test app](console-test-app.md). **Project**: Partner Center SDK Samples **Class**: CreateDevices.cs

## REST request

### Request syntax

| Method   | Request URI                                                                                                            |
|----------|------------------------------------------------------------------------------------------------------------------------|
| **POST** | [*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-id}/deviceBatches/{devicebatch-id}/devices HTTP/1.1 |

### URI parameter

Use the following path and query parameters when creating the request.

| Name           | Type   | Required | Description                                           |
|----------------|--------|----------|-------------------------------------------------------|
| customer-id    | string | Yes      | A GUID-formatted string that identifies the customer. |
| devicebatch-id | string | Yes      | A string identifier that identifies the device batch. |

### Request headers

For more information, see [Partner Center REST headers](headers.md).

### Request body

The request body must contain an array of [Device](device-deployment-resources.md#device) objects. The following combinations of fields for identifying a device are accepted:

- hardwareHash + productKey.
- hardwareHash + serialNumber.
- hardwareHash + productKey + serialNumber.
- hardwareHash only.
- productKey only.
- serialNumber + oemManufacturerName + modelName.

### Request example

```http
POST https://api.partnercenter.microsoft.com/v1/customers/c7f3c849-129f-4b85-a96d-4f8e88b315a3/deviceBatches/Test/devices HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: e286d69b-7f5f-4098-8999-21d3b54e4e47
MS-CorrelationId: 772871a9-399b-4f3b-b8c7-38f550e4f22a
X-Locale: en-US
MS-PartnerCenter-Application: Partner Center .NET SDK Samples
Content-Type: application/json
Host: api.partnercenter.microsoft.com
Content-Length: 482
Expect: 100-continue

[{
        "Id": null,
        "SerialNumber": "2R9-ZNP67",
        "ProductKey": "00329-00000-0003-AA606",
        "HardwareHash": "DummyHash1234",
        "Policies": null,
        "CreatedBy": null,
        "UploadedDate": "0001-01-01T00:00:00",
        "AllowedOperations": null,
        "Attributes": {
            "ObjectType": "Device"
        }
    }, {
        "Id": null,
        "SerialNumber": "2R9-ZNP67",
        "ProductKey": "00329-00000-0003-AA606",
        "HardwareHash": "DummyHash12345",
        "Policies": null,
        "CreatedBy": null,
        "UploadedDate": "0001-01-01T00:00:00",
        "AllowedOperations": null,
        "Attributes": {
            "ObjectType": "Device"
        }
    }
]
```

> [!IMPORTANT]
> As of June 2023, the latest Partner Center .NET SDK release 3.4.0 is now archived. You can [download the SDK release from GitHub](https://github.com/microsoft/partner-center-sdk-for-dotNET), along with a [readme file](https://github.com/microsoft/partner-center-sdk-for-dotNET#readme) that contains useful information.
>
> Partners are encouraged to continue to use the [Partner Center REST APIs](partner-center-rest-api-reference.md).

## REST response

If successful, the response contains a **Location** header that has a URI that can be used to retrieve device upload status. Save this URI for use with other related REST APIs.

### Response success and error codes

Each response comes with an HTTP status code that indicates success or failure and additional debugging information. Use a network trace tool to read this code, error type, and additional parameters. For the full list, see [Partner Center REST error codes](error-codes.md).

### Response example

```http
HTTP/1.1 202 Accepted
Content-Length: 0
Location: /customers/c7f3c849-129f-4b85-a96d-4f8e88b315a3/batchJobStatus/16c00110-e79a-433d-aa28-f69dd60df671
MS-CorrelationId: 772871a9-399b-4f3b-b8c7-38f550e4f22a
MS-RequestId: e286d69b-7f5f-4098-8999-21d3b54e4e47
MS-CV: OBkGN9pSN0a5xvua.0
MS-ServerId: 101112012
Date: Thu, 28 Sep 2017 20:08:46 GMT
```
