---
title: List of system queries for partner insights programmatic access
description: Learn more about the system queries you can use to access the partner insights analytics data.
ms.topic: reference
ms.service: partner-dashboard
ms.subservice: partnercenter-insights
author: kshitishsahoo
ms.author: ksahoo
ms.date: 07/14/2021
---

# List of system queries for partner insights programmatic access

The following system queries can be used in the [Create Report API](insights-programmatic-access-paradigm.md#create-report-api) directly with a QueryId. The system queries are like the export reports in Partner Center for a six-month (6M) computation period.

For more details on the column names, attributes, and description, refer to the [data definitions](insights-data-definitions.md).

The following sections provide report queries for various reports.

## Customers

The Customers report for the last six months:

Query ID: `6664daf3-c161-423a-92a1-0ea6db2c0384`

### Report query

```sql
SELECT PGAMpnId,MpnId,PartnerName,CustomerName,CustomerTpid,DUNSNumber,CustomerSegment,TopSegment,
CustomerMarket,CustomerStatus,CustomerTenantId,CustomerTenantName,CustomerTenantCountry,TenantDomainName,
Product,RawProductName,ProductPartNumber,SKU,Month,PartnerLocationID,PartnerAttributionType,SalesChannel,
IsDuplicateRowForPGA,AvailableSeats,BilledRevenueUSD,AzureConsumedRevenueUSD
FROM CustomersAndTenants TIMESPAN LAST_6_MONTHS
```

## Seats Subscriptions and Revenue

Seats, subscriptions, and revenue report for the last six months:

Query ID: `c9fc1c79-4408-49ff-97f9-e1aa3f155804`

### Report query

```sql
SELECT PGAMpnId,MpnId,SubscriptionId,SubscriptionStartDate,SubscriptionEndDate,SubscriptionState,month,
IsAutoRenew,CustomerName,CustomerTenantId,CustomerTpid,DUNSNumber,CustomerSegment,TopSegment,CustomerMarket,
ProductFamily,ReportingProductName,Product,RawProductName,ProductPartNumber,SKU,RevSumDivisionName,PartnerName,
SolutionArea,PartnerLocationID,PartnerAttributionType,SalesChannel,PricingLevel,EnrollmentNumber,
IsDuplicateRowForPGA,SubscriptionStartMonth,TotalSoldSeats,TotalAssignedSeats,BilledRevenueUSD,
AzureConsumedRevenueUSD FROM SeatsSubscriptionsAndRevenue TIMESPAN LAST_6_MONTHS
```

## Partner Profile

Profile data:

Query ID: `e65f3a4f-fb99-4319-97ff-59e57566a871`

### Report query

```sql
SELECT MpnId,PartnerName,PGA_MPNId,PGA_PartnerName,City,Country,HierarchyLevel
FROM Profile
```

## Azure Usage

AzureUsage report for the last six months

Query ID: `d1a4d75e-5ca8-4847-845f-ee0a9be6f07b`

### Report query

```sql
SELECT PGAMpnId,SubscriptionId,SubscriptionStartDate,SubscriptionEndDate,FirstUseDate,SubscriptionState,Month,
ServiceName,MeterCategory,UsageUnits,UsageQuantity,CustomerName,CustomerTenantId,CustomerTpid,CustomerSegment,
CustomerMarket,MpnId,PartnerName,PartnerLocationID,PartnerAttributionType,SalesChannel,EnrollmentNumber,
IsACRDuplicateAtPGALevel,ResellerID,ResellerName,MonthlySubscriptionLevelACR,TotalACR
FROM AzureUsage TIMESPAN LAST_6_MONTHS
```

## Office Usage

OfficeUsage report for the last six months

Query ID: `d8349f7b-a7d1-467e-b26d-434d4a50f26a`

### Report query

```sql
SELECT CustomerTenantId,CustomerTpid,WorkloadName,Month,PaidAvailableUnits,MonthlyActiveUsers,CustomerName,
CustomerMarket,CustomerSegment,MPNId,PartnerName,PartnerLocationID,PartnerAttributionType,IsDuplicateRowForPGA
FROM OfficeUsage TIMESPAN LAST_6_MONTHS
```

## Dynamics Usage

DynamicsUsage report for six months

Query ID: `6209a8fd-93af-442e-8b3f-3df0f77e8463`

### Report query

```sql
SELECT SubscriptionId,SubscriptionStartDate,SubscriptionEndDate,SubscriptionStatus,Month,RevSumDivisionName,
RevSumCategoryName,SKU,SKUId,FreeVsPaidSKU,SalesModel,DetailedSalesModel,CustomerName,CustomerTenantId,
CustomerTpid,CustomerSegment,CustomerMarket,MPNId,PartnerName,PartnerLocationID,PartnerAttachType,AvailableSeats,
AssignedSeats,ActiveSeats,DeploymentOpportunity,ActiveUsagePercent
FROM DynamicsUsage TIMESPAN LAST_6_MONTHS
```

## Power BI usage

PowerBIUsage report for six months

Query ID: `40ebfe2f-7183-4427-a911-5c9b45b6df15`

### Report query

```sql
SELECT SubscriptionId,SubscriptionStartDate,SubscriptionEndDate,SubscriptionStatus,Month,SKU,SKUId,
FreeVsPaidSKU,SalesModel,DetailedSalesModel,CustomerName,CustomerTenantId,CustomerTpid,CustomerSegment,
CustomerMarket,MPNId,PartnerName,PartnerLocationID,PartnerAttachType,PartnerHierarchy,AvailableSeats,
AssignedSeats,ActiveSeats,DeploymentOpportunity,ActiveUsagePercent
FROM PowerBIUsage TIMESPAN LAST_6_MONTHS
```

## EMS Usage

EMSUsage report for six months

Query ID: `d7f20ea4-8751-4d6b-b1d7-821c316acd6a`

### Report query

```sql
SELECT SubscriptionId,SubscriptionStartDate,SubscriptionEndDate,SubscriptionStatus,Month,SKU,SKUId,
FreeVsPaidSKU,SalesModel,DetailedSalesModel,CustomerName,CustomerTenantId,CustomerTpid,CustomerSegment,
CustomerMarket,MPNId,PartnerName,PartnerLocationID,PartnerAttachType,PartnerHierarchy,PaidAvailableUnits,
MonthlyActiveUsers,AADPPaidAvailableUnits,IntunePaidAvailableUnits,AzipPaidAvailableUnits,
AADPMonthlyActiveUsers,IntuneMonthlyActiveUsers,AzipMonthlyActiveUsers FROM EMSUsage TIMESPAN LAST_6_MONTHS
```

## Cloud products reseller performance

### Report description

CloudProductsResellerPerformance report for six months

Query ID: `c09c2eda-861b-4664-8ee8-48a14745a26a`

### Report query

```sql
SELECT ResellerMpnId,ResellerName,ResellerMarket,IndirectProviderMPNId,IndirectProviderName,Month,Product,
SubscriptionID,AvailableSeats,AssignedSeats,BilledRevenueUSD,CustomerName,CustomerTPid,CustomerSegment,
CustomerMarket,ResellerStatus
FROM CloudProductsResellerPerformance TIMESPAN LAST_6_MONTHS
```

## CLAS Agreement Renewal propensity

CLASAgreementRenewalsPropensity report for six months

Query ID: `c4fc87ac-4cca-44cd-bf4d-835ac513f9ee`

### Report query

```sql
SELECT MPNID,PartnerName,CustomerID,DUNSNumber,AccountName,Domain,OrgSize,Industry,Vertical,
Area,Subsidiary,SalesTerritory,City,State,PostalCode,Country,Segment,SubSegment,SMCTypeSummary,
IsNonProfit,HasGoogle,HasAWS,AzureCluster,D365FOCluster,D365CECluster,D365BCCluster,M365Cluster,
PowerAppsCluster,LicenseProgram,AgreementID,AgreementEndDate,ExpirationType,ExpiringRevenue,HasEA,
HasOpen,M365UpsellCustomer,RevSumDivisionName,TransactedInTheLast36Months
FROM CLASAgreementRenewalsPropensity
```

## CLAS Azure propensity

CLASAzurePropensity report for six months

Query ID: `9a18bd70-8f90-4bd2-8266-5f6e453e3ee7`

### Report query

```sql
SELECT MPNID,PartnerName,CustomerID,DUNSNumber,AccountName,Domain,OrgSize,Industry,Vertical,Area,Subsidiary,
SalesTerritory,City,State,PostalCode,Country,Segment,SubSegment,SMCTypeSummary,IsNonProfit,
DataAIInnovatewithAIandcloudscaledatabasesineveryappBuildnewintelligentcloudnativeapplications,
DataAIMigrateandmodernizeyourdatacenterSQLServerIBCurrentVersion,DataAIMigrateandmodernizeyourdatacenterSQLServerIBEOS,
DataAIMigrateandmodernizeyourdatacenterSQLServer2012IBEOS,DataAIMigrateandmodernizeyourdatacenterHomogenousmigrationofPostgreSQLandMySQLtoAzure,
DataAIMigrateandmodernizeyourdatacenterMigrateSQLServertoAzureSQLManagedInstanceandVMs,
RealtimeanalyticswithSynapseLinkPBIforlandeddataplatformworkloads,DataAIPowerbusinessdecisionswithCloudScaleAnalyticsMigrationOnPremDWMigrationtoAzureSynapse,
DataAIPowerbusinessdecisionswithCloudScaleAnalyticsMigrationOnPremHadoopMigrationtoAzureDatabricks,
NetNewWinNewAnalyticUseCaseswithSynapseandPBIandAML,DigitalAppInnovationAccelerateinnovationwithLowCodeBuildandmodernizelineofbusinessapplications,
AcceleratesoftwaredeliverythroughDevSecOpswithGitHubandVisualStudio,DigitalAppInnovationEnabledeveloperproductivityandAccelerateDeliveryDrivedeveloperengagement,
BuildcloudnativeappswithKubernetesServerlessanddataModernizeAppswAKS,BuildcloudnativeappswithKubernetesServerlessanddataModernizeAppswRHOpenShiftHighConsumingLinuxIBISV,
DigitalAppInnovationInnovateandscalewithcloudnativeappsDrivedeveloperengagement,DigitalAppInnovationModernizeenterpriseapplicationsModernizeNETappswithdata,
DigitalAppInnovationModernizeenterpriseapplicationsModernizeJavaappswithdata,HighPropensityHighPropensity,
DevelopoperateandsecurewithAzureArcArcenabledservicesandAzureStackHCI,InfraMigrateandModernizeyourInfrastructureandworkloadsAttachMonitorStorageNetworkingandSecurity,
InfraMigrateandModernizeyourInfrastructureandworkloadsWindowsServerIBCurrentVersion,InfraMigrateandModernizeyourInfrastructureandworkloadsWindowsServerIBEOS,
InfraMigrateandModernizeyourInfrastructureandworkloadsWindowsServer2012IBEOS,InfraMigrateandModernizeyourInfrastructureandworkloadsMigrateandmodernizeLinuxOSSDBtoAzure,
InfraMigrateandModernizeyourInfrastructureandworkloadsMigrateandmodernizeVMwaretoAVS,
InfraMigrateandModernizeyourInfrastructureandworkloadsMigrateandmodernizeWindowsServerSQLtoAzure,
InfraMigrateandModernizeyourInfrastructureandworkloadsModernizeVDItoAVDMigrateCitrixIB,
InfraMigrateandModernizeyourInfrastructureandworkloadsModernizeVDItoAVDMigrateVMWareIB,
InfraMigrateandModernizeyourInfrastructureandworkloadsModernizeVDItoAVDCrossSellMWtoAzureWVD,InfraMigrateandModernizeyourInfrastructureandworkloadsModernizeVDItoAVDRDSIB,
InfraModernizeSAPontheMicrosoftCloudExtendandinnovateSAPwithMicrosoftCloudservices,
InfraModernizeSAPontheMicrosoftCloudMigrateandmodernizetoS4HANAviaRISEwithSAPorAzurenative,ExtendEdgeInferencingwithcloudbasedmodeltrainingusingAzureAIInfrastructure,
InfraModernizeyourworkloadswithAzureatanyscalewithHPCAIExtendtoAVDworkloadsrequiringGPUrendering,
InfraModernizeyourworkloadswithAzureatanyscalewithHPCAIModernizeHPCworkloadswithAzureHPCAI,AttachAzureBackupandASRtoeveryproductionVMnewandgoback,
InfraProtectyourdataandensurebusinessresiliencywithBCDRBackuponpremdataandSaaSdatatoAzure,SecurityDefendAgainstThreatswithSIEMXDRDriveSIEMXDRtomodernizesecurityopcenter,
SecuritySecureMultiCloudInfrastructureCloudworkloadprotectionDefenderAttachinWindowsMigration,
SecuritySecureMultiCloudInfrastructureCloudworkloadprotectionWellArchitectedSecurityGoBack,AzureFit,AzureIntent,AzureCluster,WindowsServerDataCenter_HasOpenRenewal,
WindowsServerStandard_HasOpenRenewal,HasGoogle,HasAWS,HasEA,HasOpen,NumberofExistingWorkloads,ExistingWorkloads,NumberofRecommendedWorkloads,RecommendedWorkloads,
Transactedinthelast36months
FROM CLASAzurePropensity
```

## CLAS Dynamics 365 propensity

CLASD365Propensity report for six months

Query ID: `258fdcac-6e9c-4072-af27-b1b3d97be16c`

### Report query

```sql
SELECT MPNID,PartnerName,CustomerID,DUNSNumber,AccountName,Domain,OrgSize,Industry,Vertical,Area,
Subsidiary,SalesTerritory,City,State,PostalCode,Country,Segment,SubSegment,SMCTypeSummary,IsNonProfit,
AccelerateInnovationwithLowCodeDynamicsCompeteBaseMendixOutsystemsSalesforcePowerAppsPowerAutomateModel,ConnectedSalesMarketingUnlockDatatoMaximizeSalesImpact,
EnableaResilientSustainableSupplyChainCrossSellD365SupplyChainAndOrRetailCommercetoexistingD365Sales,
CrossSellD365SupplyChainAndOrRetailCommercetoexistingD365SalesandOracleorSAPCustomers,WinandActivateFirstD365WorkloadasD365SupplyChainwithNonOracleSAPERPCustomers,
ModernizetheServiceExperienceD365CustomerServicesandD365FieldServicesD365SalesPropensity,
OptimizeFinancialOperatingModelsDynamicsOnPremInstallBaseGreatPlainsBCFinancePropensityModel,
OptimizeFinancialOperatingModelsDynamicsOnPremInstallBaseNavisionBCFinancePropensityModel,
OptimizeFinancialOperatingModelsDynamicsOnPremInstallBaseOthersBCFinancePropensityModel,
OptimizeFinancialOperatingModelsDynamicsOnPremInstallBaseSolomonBCFinancePropensityModel,OptimizeFinancialOperatingModelsTransformBusinessOperationsExperience,
D365BCCluster,D365BCFit,D365BCIntent,D365FOCluster,D365FOFit,D365FOIntent,D365CECluster,D365CEFit,D365CEIntent,PowerAppsCluster,PowerAppsFit,PowerAppsIntent,
DynamicsOnPremAXorCRM_HasOpenRenewal,M365UpsellCustomer,HasGoogle,HasAWS,HasEA,HasOpen,Transactedinthelast36months
FROM CLASD365Propensity
```

## CLAS Microsoft 365 propensity

CLASM365Propensity report for six months

Query ID: `fbe00e32-fdde-4465-b3e4-41bbd021a130`

### Report query

```sql
SELECT MPNID,PartnerName,CustomerID,DUNSNumber,AccountName,Domain,OrgSize,Industry,Vertical,Area,
Subsidiary,SalesTerritory,City,State,PostalCode,Country,Segment,SubSegment,SMCTypeSummary,IsNonProfit,DigitalWorkforce3rdPartyHostingService,
DigitalWorkforceAcquirenewcustomerstoMicrosoftHighPropensityProspectforM365ActNowEvaluate,DigitalWorkforceM365A3targetedforA5,DigitalWorkforceSkypeforBusiness,
DigitalWorkforceOnPremAcquisitionCurrentVersion,DigitalWorkforceOnPremAcquisitionEOS,DigitalWorkforceTransitionCustomerCompeteZoomwithM365,
DigitalWorkforceTransitionCustomerCompeteZoomwithoutM365,DigitalWorkforceTransitionCustomerCompeteGoogleWorkspace,DigitalWorkforceUpsellexistingcloudcustomerIntune,
DigitalWorkforceUpsellexistingcloudcustomerM365BBBScustomerstargetedforM365BP,DigitalWorkforceUpsellexistingcloudcustomerM365E3targetedforM365E5,
DigitalWorkforceUpsellexistingcloudcustomerTargetExchangeonline,NextGenWindowsExperiencesCompeteAmazonWorkspaceAWSWorkspaces,NextGenWindowsExperiencesCompeteCitrix,
NextGenWindowsExperiencesCompeteGoogleDaaScompeteitopiaNutanixFrameWorkspot,NextGenWindowsExperiencesCompeteVmwareHorizons,
NextGenWindowsExperiencesCustomerhashardwareandalsoaddlastHWpurchase3years,NextGenWindowsExperiencesCustomerhasW10ProorearlierversionsW11ProTargetW365,
CustomerswithWindowsProendpointsWindows10EnterpriseE3EMSE3orMicrosoft365F3E3E5BPTargetforW365,NextGenWindowsExperiencesGoogleWorkspacecustomerswithoutWindows,
UserswithnonWindowsProendpointsWindowsVDAE3EMSE3orMicrosoft365F3E3F5BPTargetW365,RefreshyourDevicesBusinessPremiumESKUAttach50,RefreshyourDevicesEDUforSurface,
RefreshyourDevicesSurfaceDevices25purchasedinthelast3years,RefreshyourDevicesTargetSurfaceforBS,RefreshyourDevicesTeamsMeetingPresence50,
SeamlessSecurityTransitionCustomerCompeteEndpointSecurityMDB,SeamlessSecurityUpsellexistingcloudcustomerCompeteEndpointSecurityMDB,
SeamlessSecurityUpsellexistingcloudcustomerCompeteGoogleWorkspace,SeamlessSecurityUpsellexistingcloudcustomerM365BBBScustomerstargetedforM365BP,
SeamlessSecurityUpsellexistingcloudcustomerOnPremAcquisitionCurrentVersion,SeamlessSecurityUpsellexistingcloudcustomerTargetExchangeOnline,M365Cluster,M365Fit,M365Intent,
SurfaceCluster,SurfaceFit,SurfaceIntent,M365UpsellCustomer,HasGoogle,HasAWS,HasEA,HasOpen,Transactedinthelast36months
FROM CLASM365Propensity
```

## CLAS Surface propensity

CLASSurfacePropensity report for six months:

Query ID: `ba339743-7594-439f-bb01-1a2e754df7b7`

```sql
SELECT MPNID,PartnerName,CustomerID,DUNSNumber,AccountName,Domain,OrgSize,Industry,Vertical,Area,
Subsidiary,SalesTerritory,City,State,PostalCode,Country,Segment,SubSegment,SMCTypeSummary,IsNonProfit,DigitalWorkforce3rdPartyHostingService,
DigitalWorkforceAcquirenewcustomerstoMicrosoftHighPropensityProspectforM365ActNowEvaluate,DigitalWorkforceM365A3targetedforA5,DigitalWorkforceSkypeforBusiness,
DigitalWorkforceOnPremAcquisitionCurrentVersion,DigitalWorkforceOnPremAcquisitionEOS,DigitalWorkforceTransitionCustomerCompeteZoomwithM365,
DigitalWorkforceTransitionCustomerCompeteZoomwithoutM365,DigitalWorkforceTransitionCustomerCompeteGoogleWorkspace,DigitalWorkforceUpsellexistingcloudcustomerIntune,
DigitalWorkforceUpsellexistingcloudcustomerM365BBBScustomerstargetedforM365BP,DigitalWorkforceUpsellexistingcloudcustomerM365E3targetedforM365E5,
DigitalWorkforceUpsellexistingcloudcustomerTargetExchangeonline,NextGenWindowsExperiencesCompeteAmazonWorkspaceAWSWorkspaces,NextGenWindowsExperiencesCompeteCitrix,
NextGenWindowsExperiencesCompeteGoogleDaaScompeteitopiaNutanixFrameWorkspot,NextGenWindowsExperiencesCompeteVmwareHorizons,
NextGenWindowsExperiencesCustomerhashardwareandalsoaddlastHWpurchase3years,NextGenWindowsExperiencesCustomerhasW10ProorearlierversionsW11ProTargetW365,
CustomerswithWindowsProendpointsWindows10EnterpriseE3EMSE3orMicrosoft365F3E3E5BPTargetforW365,NextGenWindowsExperiencesGoogleWorkspacecustomerswithoutWindows,
UserswithnonWindowsProendpointsWindowsVDAE3EMSE3orMicrosoft365F3E3F5BPTargetW365,RefreshyourDevicesBusinessPremiumESKUAttach50,RefreshyourDevicesEDUforSurface,
RefreshyourDevicesSurfaceDevices25purchasedinthelast3years,RefreshyourDevicesTargetSurfaceforBS,RefreshyourDevicesTeamsMeetingPresence50,
SeamlessSecurityTransitionCustomerCompeteEndpointSecurityMDB,SeamlessSecurityUpsellexistingcloudcustomerCompeteEndpointSecurityMDB,
SeamlessSecurityUpsellexistingcloudcustomerCompeteGoogleWorkspace,SeamlessSecurityUpsellexistingcloudcustomerM365BBBScustomerstargetedforM365BP,
SeamlessSecurityUpsellexistingcloudcustomerOnPremAcquisitionCurrentVersion,SeamlessSecurityUpsellexistingcloudcustomerTargetExchangeOnline,M365Cluster,M365Fit,M365Intent,
SurfaceCluster,SurfaceFit,SurfaceIntent,M365UpsellCustomer,HasGoogle,HasAWS,HasEA,HasOpen,Transactedinthelast36months
FROM CLASSurfacePropensity
```

## Teams Usage 3P Apps

TeamsUsage3PApps report for six months

Query ID: `42d287be-cc76-4109-a066-f3140ad97fe2`

### Report query

```sql
SELECT CustomerId,CustomerTenantId,CustomerName,CustomerCountry,DateKey,AppName,UserCount
FROM TeamsUsage3PApps TIMESPAN LAST_6_MONTHS
```

## Teams usage workload

TeamsUsageWorkload report for six months

Query ID: `817fe875-acb0-4c45-9201-b7a35a60235a`

### Report query

```sql
SELECT CustomerId,CustomerTenantId,MonthKey,SubWorkload,DesktopUsers,WebUsers,MobileUsers,AllUpPartiticipants
FROM TeamsUsageWorkload TIMESPAN LAST_6_MONTHS
```

## Teams usage meetings and calls

TeamsUsageMeetingsAndCalls report for six months

Query ID: `b7bd73a8-47e8-4c57-b915-445708cfd7bf`

### Report query

```sql
SELECT CustomerId,CustomerTenantId,DateKey,SubWorkload,MeetingCount,MeetingDuration
FROM TeamsUsageMeetingsAndCalls TIMESPAN LAST_6_MONTHS
```

## Training completion

Training Completions report for six months

Query ID: `20f5da57-3c2a-481b-b6a0-ec34d6db14e2`

### Report query

```sql
SELECT TrainingActivityId,TrainingTitle,TrainingType,AADUserId,TrainingCompletionDate,Month,IcMCP,MCPID,MPNID,
PartnerName,PartnerCityLocation,PartnerCountryLocation
FROM TrainingCompletions TIMESPAN LAST_6_MONTHS
```

## Microsoft Learn

Microsoft Learn report for the last six months

Query ID: `0e06c7c3-75ab-4cd5-8178-8cf1a2de49cc`

### Report query

```sql
SELECT UserName,UserId,TrainingName,TrainingType,Products,Roles,CompletionDate,MPNId,PartnerName,CustomerMarket
FROM MSLearn TIMESPAN LAST_6_MONTHS
```

## Next steps

- [APIs for accessing partner insights analytics data](insights-programmatic-analytics-available-api.md)
- [Sample application for accessing partner insights analytics data](insights-programmatic-sample-application.md)
