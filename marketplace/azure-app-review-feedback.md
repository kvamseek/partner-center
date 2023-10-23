---
title: Review feedback for Azure apps offers - Microsoft commercial marketplace 
description: Handle feedback for your Azure application offer from the Microsoft Azure Marketplace review team. You can access feedback in Azure DevOps with your Partner Center credentials. 
ms.service: marketplace 
ms.subservice: partnercenter-marketplace-publisher
ms.topic: conceptual
ms.date: 9/22/2022
ms.author: mingshen
author: mingshen-ms
---

# Handle review feedback for Azure application offers

This article explains how to access feedback from the Microsoft Azure Marketplace review team in [Azure DevOps](https://azure.microsoft.com/services/devops/). If critical issues are found in your Azure application offer during the **Microsoft review** step, you can sign into this system to view detailed information about these issues (review feedback). After you fix all issues, you must resubmit your offer to continue to publish it on Azure Marketplace. The following diagram illustrates how this feedback process relates to the publishing process.

You can [download our TTK](/azure/azure-resource-manager/templates/test-toolkit) and test your offers locally before you submit them to ensure that they will pass once you go live.

:::image type="content" alt-text="Screenshot of Azure apps verification process." source ="./media/azure-app/azure-apps-verification-process.png" lightbox="./media/azure-app/azure-apps-verification-process.png" :::

Typically, review issues are referenced as a pull request (PR). Each PR is linked to an online Azure DevOps item, which contains details about the issue. The following image displays an example of the Partner Center experience if issues are found during reviews. 

:::image type="content" source="media/azure-app/publishing-status.png" alt-text="Publishing status":::

The PR that contains specific details about the submission will be mentioned in the “View Certification Report” link. For complex situations, the review and support teams may also email you.

## Azure DevOps access

All users with access to the “developer” role in Partner Center will have access to view the PR items referenced in review feedback.

## Reviewing the pull request

Use the following procedure to review issues documented in the pull request.

1. In the **Microsoft review** sections of Publishing steps form, select a PR link to launch your browser and navigate to the **Overview** (home) page for this PR. The following image depicts an example of the critical issue home page for the Contoso sample app offer. This page contains useful summary information about the review issues found in the Azure app.

    :::image type="content" source="media/azure-app/pr-home-page-thumb.png" alt-text="Pull request home page." lightbox="media/azure-app/pr-home-page.png":::

1. (Optional) On the right side of the window, in the section **Policies**, select the issue message (in this example: **Policy Validation failed**) to investigate the low-level details of the issue, including the associated log files. Errors are typically displayed at the bottom of the log files.

1. In the menu on the left-side of the home page, select **Files** to display the list files that comprise the technical assets for this offer. The Microsoft reviewers should have added comments describing the discovered critical issues. In the following example, two issues have been discovered.

    :::image type="content" source="media/azure-app/pr-files-page-thumb.png" alt-text="Screenshot that highlights Files and the two issues that were discovered." lightbox="media/azure-app/pr-files-page.png":::

1. Select each comment node in the left tree to navigate to the comment in context of the surrounding code. Fix your source code in your team's project to correct the issue described by the comment.

>[!NOTE]
>You cannot edit your offer's technical assets within the review team's Azure DevOps environment. For publishers, this is a read-only environment for the contained source code. However, you can leave replies to the comments for the benefit of the Microsoft review team.

   In the following example, the publisher has reviewed, corrected, and replied to the first issue.

   :::image type="content" source="media/azure-app/first-comment-reply.png" alt-text="First fix and comment reply":::

## Next steps

- After you correct the critical issues documented in the review PR(s), you must [republish your Azure app offer](azure-app-offer-setup.md).