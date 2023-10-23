---
title: Find desktop count and fee level
ms.topic: how-to
ms.date: 02/02/2022
description: Learn how to use the Channel Incentives platform (CHIP) to find the desktop count and fee level information for an agreement.
ms.service: partner-dashboard
ms.subservice: partnercenter-incentives
author: Karthic83
ms.author: kashanum
---

# Locate the desktop count and fee level for an agreement

**Appropriate roles**: Primary contact or program admin

You can sign in to [explore.ms](https://www.explore.ms/) to review the agreement, or download a file providing agreement details for desktop count and fee level.

## To locate the information

### Method 1 – Explore.ms

1. Open [explore.ms](https://www.explore.ms/) in Internet Explorer.

   > [!NOTE]
   > You cannot perform this function in Google Chrome or Microsoft Edge.

2. Sign in with your Work/School account or live ID.

3. In the **Reports** field, select **Agreements**.

4. On the resulting page, enter the agreement number in the **Search** field, and then select **Select/Order Columns**.

5. In the pop-up window, select **Agreement Desktop Count** from the available columns list, and then select the right arrow to add the column. Select **OK**.

6. Select **Search.**

7. In the resulting screen, scroll through the results to find the **Agreement Desktop Count** column.

8. Use the desktop count to determine the fee level based on the rate table below.

| Fee level | Desktop count |
| ------ | :-----------: |
|  A | 0 – 2,399    |
|  B | 2,400 – 5,999    |
|  C | 6,000 – 14,999    |
|  D | 15,000+   |

> [!NOTE]
> Enterprise Incentive levels are based on the desktop or user count (whichever is higher) in Commercial and Public Sector (PS) enrollments. For enrollments with no natural associated desktop or user count, Microsoft applies a desktop count based on the desktop count or user count of the accompanying EA.
>
> If there is no accompanying EA, the Fee Level is based on the pricing level of the enrollment. The pricing level of the deal can also be viewed on [www.explore.ms](https://www.explore.ms/).
>
> If there are multiple pool and/or pricing levels on the existing EA/EAS,  Microsoft will pay incentives at the highest assigned pricing/pool level, with level A being the lowest and level D being the highest.

#### Pool and pricing levels

After searching for the agreement number in explore.ms using the steps outlined above, select the agreement number. Doing so takes you to the agreement details page, which shows the **Agreement Summary** and **Offerings**. The offerings section contains the pricing levels.

### Method 2 - Channel Incentives Platform (CHIP)

1. Sign in to [CHIP](https://channelincentives.microsoft.com) and select LSP Incentives.

2. From the **Partner Payment Summary** page, select the reporting month you want to view, and then select **Calculation Details** from the dropdown under **Export to Excel**:

   :::image type="content" source="media/chip/chiplocate.png" lightbox="media/chip/chiplocate.png" alt-text="Locate program details.":::

3. The export will start, and you can either open the file or save/save as to a destination.

4. When the report is open, go to the **DetailReport-FlatFile** tab at far bottom left:

:::image type="content" source="media/chip/flatfile.png" lightbox="media/chip/flatfile.png" alt-text="Flat file download.":::

You can now search for the agreement number you're looking for in column J. and you'll find the assigned desktop count in column R, labeled Agreement_DesktopCount. You can also confirm the Fee Level for this agreement in column ‘AI' labeled Tier.

## Next steps

- [Troubleshoot CHIP access issues](chip-access-trouble.md)
