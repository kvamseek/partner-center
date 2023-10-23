---
title: Get verifiable credentials
ms.topic: article
ms.date: 09/11/2023
ms.service: partner-dashboard
ms.subservice: partnercenter-enroll
description: Complete your identity verification to access Partner Center by obtaining and presenting verifiable credentials from a trusted ID Verification vendor (IDV).
author: guptanikhil007 
ms.author: guptan
---

# Get verifiable credentials from a trusted ID verification vendor

**Appropriate roles**: Global admin | MPN Partner Admin | Account admin | Manager | Owner

Complete your identity verification to access Partner Center programs by obtaining and presenting verifiable credentials (VCs) issued by a trusted ID verification vendor (IDV).

## What are verifiable credentials (VCs)?

Verifiable credentials are an open standard for digital credentials. Verifiable credentials can represent information found in physical credentials, such as a passport or license, or information that has no physical equivalent, such as ownership of a bank account. Verifiable credentials have numerous advantages over physical credentials, most notably that they're digitally signed, which makes them tamper-resistant and instantaneously verifiable.

The entity that generates the credential is called the *Issuer*. The credential is then given to the *holder* who stores it for later use. The Holder can then prove something about themselves by presenting their credentials to a *verifier*.

Some trusted ID verification vendors (IDVs) issue verifiable credentials that validate individuals, organizations, and associations through face recognition technologies (also called a "live selfie"). The issuers match the facial recognition with government-issued IDs and documents to certify verifiable credentials using Microsoft's Distributed Identities Framework. Users can present these certificates from devices that are integrated with Microsoft Authenticator to confirm their credentials without repeatedly undergoing the verification process. If any of the user's attributes change, the verifiable credentials can be removed or blocked to prevent misuse or impersonation. 

## Why is Microsoft requesting verifiable credentials from a trusted IDV?

Bad actors are increasingly using sophisticated techniques to commit fraud against Microsoft and its customers and partners.  An analysis of recent attacks has shown that sophisticated techniques, such as consent phishing, impersonation, and exploitation of process gaps in critical transitions are used to steal customer data, publish malicious apps, and cause damage to Microsoft and its partners directly or indirectly.

To prevent such attacks, Microsoft has enhanced its vetting process and committed to using verifiable credentials from trusted IDVs.

The security of verifiable credentials has been questioned. Verifiable credentials have also been subject to usability concerns. Anyone can issue verifiable credentials about anything. Credentials can be presented to and verified by everyone.

## How do I obtain a verifiable credential for Partner Center?

When a Partner Center program requires a verifiable credential, a link appears that takes you to a page where you can choose from one of our trusted identity verification vendors (IDVs) to obtain a VC certificate. You'll be asked to present a government issued ID and then take a selfie for facial matching. Once the IDV completes the identify verification, they'll issue you a VC certificate that you can store in your mobile Microsoft Authenticator app.

Going forward, if Partner Center requests a VC, you'll get a QR code that you can scan on a mobile device camera. After scanning the QR code, the mobile MS Authenticator app opens, and you'll be able to select your VC certificate.

## Steps to get verifiable credentials

1. Sign in to [Partner Center](https://partner.microsoft.com/dashboard/home), select **Settings** (gear icon) > **Account Settings**.

1. Select the **Legal info** tab on the left. The **Legal business profile** section shows your **Verification status** in the Microsoft AI Cloud Partner Program.

   :::image type="content" source="media/verification/legal-business-profile.png" lightbox="media/verification/legal-business-profile.png" alt-text="Screenshot of the Legal Info tab in Account settings. In Legal business profile, verification status shows as Pending. Fix Now is highlighted.":::

1. If you're prompted for identity verification, select **Fix Now**.

1. Install the **Microsoft Authenticator** app on your iOS or Android mobile device.

1. Get your valid government ID, for example, a passport, a driver's license, or other national ID. The ID should be a physical form of ID that is current and up-to-date.

1. Verify that the name on your ID matches either the Partner Center primary contact or your tenant username.

   > [!NOTE]
   > To see the Partner Center primary contact, select **Account settings**, then select **Legal profile**.
   > To see the Partner Center username, select **Account settings**, then select **User management**.
   > Only the tenant admin can update these names.  

   :::image type="content" source="media/verification/user-management.png" lightbox="media/verification/user-management.png" alt-text="Screenshot of the User management tab in Account settings. In the Users section, text shows the user name that is signed in.":::

1. Select **Start** next to a trusted partner.

   :::image type="content" source="media/verification/our-trusted-partners.png" alt-text="Screenshot of the Our Trusted Partners section of the User Management tab.":::

1. Create verifiable credentials using the trusted partners' pages. The following steps show an example walkthrough using the trusted partner: *AU10TIX*.

   1. Select **Let's Begin**.

      :::image type="content" source="media/verification/au10tix-lets-begin.png" alt-text="Screenshot of the AU10TIX starting page with the button: LET'S BEGIN.":::

   1. Enter your Partner Center user email address.

      :::image type="content" source="media/verification/au10tix-email-approval.png" alt-text="Screenshot of the AU10TIX Email Approval page.":::

      AU10TIX sends an email verification in email that includes a PIN code.

   1. Check your email for the verification mail and enter it to verify your email account.

      :::image type="content" source="media/verification/au10tix-email-pin.png" alt-text="Screenshot of the AU10TIX page: Enter the PIN code we just sent to your inbox.":::

   1. Enter your mobile number that has the Microsoft Authenticator app installed.

      :::image type="content" source="media/verification/au10tix-enter-phone-number.png" alt-text="Screenshot of the AU10TIX page: Great! To continue, please enter your phone number.":::

   1. Select **Start**.

      :::image type="content" source="media/verification/au10tix-prepare-document.png" alt-text="Screenshot of the AU10TIX page: Please prepare your document before starting the process.":::

   1. Use mobile camera to scan the QR code.

      :::image type="content" source="media/verification/au10tix-switch-to-mobile.png" alt-text="Screenshot of the AU10TIX page: Switch to mobile and make it easier on yourself. The page has a prominent QR code to scan.":::

   1. On your mobile device, select **Start**.

      :::image type="content" source="media/verification/au10tix-mobile-prepare-document.png" alt-text="Screenshot of the AU10TIX page on a mobile device, with the text: Please prepare your document before starting the process. An illustration shows a hand holding an ID card.":::

   1. Select **Continue** to allow your browser to have access to the camera.

      :::image type="content" source="./media/verification/au10tix-mobile-click-allow.png" alt-text="Screenshot of the AU10TIX page on a mobile device, with the page: Click allow on your browser camer access prompt. It will appear right after this!":::

   1. Select **Continue** to capture the photo.

      :::image type="content" source="media/verification/au10tix-mobile-capture-your-document.png" alt-text="Screenshot of the AU10TIX page on a mobile device: Capture your document. An illustration shows a camera taking a picture of an ID card.":::

   1. Select **Continue** to verify that you're happy with the picture, or select **Retake** to retake the picture.

      :::image type="content" source="media/verification/au10tix-mobile-happy-with-the-results.png" alt-text="Screenshot of the AU10TIX page on a mobile device, with the text: Happy with the results? A picture of the ID card is shown, with the option: RETAKE.":::

   1. Select **Continue** to take a photo of yourself. Remove glasses and face masks, and ensure the lighting in the room is good.

      :::image type="content" source="media/verification/au10tix-mobile-take-a-selfie.png" alt-text="Screenshot of the AU10TIX page on a mobile device, with the text: Take a selfie. An illustration shows taking a picture of yourself.":::

   1. Once verification is completed, then AU10TIX sends an SMS verification code to your mobile device. Select **Open Authenticator**.

      :::image type="content" source="media/verification/au10tix-mobile-success.png" alt-text="Screenshot of the AU10TIX page on a mobile device, with the text: Success! The button: Open Authenticator is shown.":::

   1. Enter the SMS verification code into the Microsoft Authenticator prompt.

      :::image type="content" source="media/verification/authenticator-mobile-enter-verification-code.png" alt-text="Screenshot of Microsoft Authenticator on a mobile device, with the text: Enter your verification code, with a place to enter a code, and a Next button.":::

   1. Select **Add** to add a verified ID to the Microsoft Authenticator app.
      :::image type="content" source="media/verification/authenticator-mobile-add-a-verified-id.png" alt-text="Screenshot of the Microsoft Authenticator page on a mobile device, with the text: Add a verified ID, and an Add button.":::

   1. Select **VerifiableCredential** to select a credential to share with Partner Center.

      :::image type="content" source="media/verification/authenticator-mobile-share-with-partner-center.png" alt-text="Screenshot of the Microsoft Authenticator page on a mobile device, with the title: Share with Partner Center? and a selection: VerifiableCredential.":::

   1. Select **Confirm**.

      :::image type="content" source="media/verification/authenticator-mobile-share-with-partner-center-2.png" alt-text="Screenshot of the Microsoft Authenticator page on a mobile device, with a preview of the ID card and other info about the credentials. The Confirm button is shown.":::

   1. Select **Share** to share the credentials with Partner Center.

      :::image type="content" source="media/verification/authenticator-mobile-share-with-partner-center-3.png" alt-text="Screenshot of the Microsoft Authenticator page on a mobile device, with text: Share with Partner Center? The Share button is shown.":::

   1. Once the verifiable credential is shared with Partner Center, then the vetting/onboarding process proceeds to employment verification.

      :::image type="content" source="media/verification/legal-employment-verification.png" lightbox="media/verification/legal-employment-verification.png" alt-text="Screenshot of the Legal Info page in Account settings. In the Legal business profile, the steps up to Employment verification are checked as completed.":::

## Frequently asked questions

### Why does the enrollment process require identity verification?

To ensure the partner ecosystem is secure, we might ask for other identify verification before enrollment can be completed.

### How long do I have to complete the verification process?

Sixty days.

### Can I use an existing verifiable credential?

Yes, you can use an existing VC from a Microsoft Partner Center preferred vendor. If you're prompted for a VC, select **Get VC** to see a list of our approved IDVs.

### Which vendors can I use to complete identify verification?

Currently, Microsoft partners with AU10TIX.

### What do I need to complete the identify verification process?

- A government issued ID such as passport or driver's license.
- A mobile device (iOS or Android) with the Microsoft Authenticator app installed.

### How long should the identity verification process take?

We recommend you dedicate 15 minutes to completing the entire process.

### Does my Partner Center username need to match the name on my government issued ID?

Yes, the names must match exactly and be in the same language.

Contact your Partner Center global administrator to update your username if needed.

#### Will the ID verifier (IDV) store my personal data?

Microsoft requires that its trusted ID verifiers adhere to privacy policies and that your data is safely handled and disposed of.

### What email should I provide the AU10TIX?

Provide your Partner Center user email address. The email address is used for PIN verification.

### Why do I need to provide my mobile number to AU10TIX?

A mobile number is required for AU10TIX to send an SMS code later in the process to verify your endpoint device.

AU10TIX will then send this endpoint device the VC certificate to load onto the MS Authenticator app.  

### What if my company doesn't allow me to use a personal mobile device or has issued me a corporate mobile device?

Work with your IT and governance departments on corporate policy.

### What happens if the IDV fails to issue me a VC?

Go to Partner Center/Account Settings/Legal Info page, then select **Contact Support**.

### Does a VC expire?

Yes, a verifiable credential certificate expires either at one year or on the expiration date of the government-issued document, whichever comes first. The Microsoft Authenticator app shows the certificate expiration date.

### What if my attempt to get a verifiable credential fails and I need further support?

For further assistance, [create a support ticket](https://go.microsoft.com/fwlink/?linkid=2167384).
