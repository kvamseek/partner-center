---
title: Send diagnostics to Microsoft
ms.topic: article
ms.date: 5/10/2023
ms.service: partner-dashboard
ms.subservice: partnercenter-support
description: Collect and send diagnostics to help with your support case.
author: Kim-Davis
ms.author: kimnich
---

# Send diagnostics to Microsoft

**Applies to**: Partner Center | Partner Center for Microsoft Cloud for US Government

**Appropriate roles**: All partners interested in Partner Center

If an error occurs while you're working in Partner Center, you might be prompted to gather error log information and send it to Microsoft. Submitting error logs helps to speed up the resolution of any issues that might have occurred.

To open the client diagnostic tool when prompted, use the following steps:

1. Select **Collect more information** from the link that drops down from the top of the page.

   This tool gathers information that the Partner Support team needs to determine the cause of the error.

1. At the bottom of the diagnostics output (you might have to scroll down), save the report to your local machine.

   :::image type="content" source="media/support/save-diagnostics.png" alt-text="Screenshot showing the 'Save report' button for the screen diagnostics.":::

1. After you save the report to your local machine, open it and review the information in the file.
   The report might contain personal information that you might want to remove before sending to Microsoft.

   Depending on your browser, you might see an empty **Page View** section at the bottom of the **Preview** page. This is OK.

1. Attach the report file to your support request.
   This option is available on Step 1 of creating a support request, under **Additional details**.

   :::image type="content" source="media/support/collect-diagnostics.png" alt-text="Screenshot showing the first step of creating a support request and the ability to upload a file.":::

   You can also add the diagnostics file to an existing support ticket.

> [!NOTE]
> The support team might ask you to collect diagnostics several times so they can get the most up-to-date information.

## Record issue details with an HAR file

To help agents to troubleshoot your issue, consider attaching an HTTP Archive (HAR) file to your support ticket. HAR files are logs of network requests in a web browser.

> [!WARNING]
> HAR files might contain sensitive data about your Partner Center account.

### Using Microsoft Edge and Google Chrome

The following steps show how to use the developer tools to generate a HAR file using Microsoft Edge or Google Chrome. For more information, see [Microsoft Edge DevTools](/microsoft-edge/devtools-guide-chromium/landing/) or [Chrome DevTools](https://developers.google.com/web/tools/chrome-devtools).

1. Go to the web page where you're experiencing the issue.
1. In the top right corner of the window, select the ellipsis ("**...**") icon, then **More tools** > **Developer tools**. You can press F12 as a shortcut.
1. In the **Developer tools** pane, select the **Network** tab.
1. Select **Stop recording network log** and **Clear** to remove existing logs. The Record icon will turn grey.

    :::image type="content" source="media/support/chromium-stop-clear-session.png" alt-text="How to remove existing logs in Microsoft Edge or Google Chrome":::

1. Select **Record network log** to start recording. (When recording starts, the Record icon turns red.)

    :::image type="content" source="media/support/chromium-start-session.png" alt-text="How to start recording in Microsoft Edge or Google Chrome":::

1. Reproduce the issue that you want to troubleshoot.
1. After you've reproduced the issue, select **Stop recording network log**.
1. Select **Export HAR** (which is marked with a downward-facing arrow icon) and save the file.

    :::image type="content" source="media/support/chromium-network-export-har.png" alt-text="How to export an HAR file in Microsoft Edge or Google Chrome":::
1. Attach the HAR file to your support request.

### Using Mozilla Firefox

The following steps show how to use the developer tools in Mozilla Firefox to generate a HAR file. For more information, see [Firefox Developer Tools](https://developer.mozilla.org/docs/Tools).

1. Go to the web page where you're experiencing the issue.
1. Press F12 to launch the developer tools.
1. Select the **Network** tab, then select **Clear** to remove existing logs.

    :::image type="content" source="media/support/firefox-clear-session.png" alt-text="How to remove existing logs in Mozilla Firefox":::

1. Reproduce the issue you want to troubleshoot.
1. After you've reproduced the issue, select **Save All As HAR**.

    :::image type="content" source="media/support/firefox-network-export-har.png" alt-text="How to export an HAR file in Mozilla Firefox":::
1. Attach the HAR file to your support request.

### Using Apple Safari

The following steps show how to use the developer tools in Apple Safari to generate a HAR file. For more information, see [Safari Developer Tools overview](https://support.apple.com/guide/safari-developer/safari-developer-tools-overview-dev073038698/11.0/mac).

1. Select **Safari** > **Preferences** to enable the developer tools in Safari.
1. Go to the **Advanced** tab, then select **Show Develop menu in menu bar**.
1. Go to the web page where you're experiencing the issue.
1. Select **Develop**, then select **Show Web Inspector**.
1. Select the **Network** tab, then select **Clear Network Items** to remove existing logs.

    :::image type="content" source="media/support/safari-clear-session.png" alt-text="How to remove existing logs in Safari":::

1. Reproduce the issue that you want to troubleshoot.
1. After you've reproduced the issue, select **Export** and save the file.

    :::image type="content" source="media/support/safari-network-export-har.png" alt-text="How to export an HAR file in Safari":::
1. Attach the HAR file to your support request.

## Next steps

- [Report problems with Partner Center](report-problems-with-partner-center.md)

