---
title: زيادة الحماية من المخاطر Microsoft 365 Business Premium
f1.keywords:
- NOCSH
ms.author: deniseb
author: denisebmsft
manager: dansimp
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- Adm_O365
- M365-subscription-management
- M365-Campaigns
- m365solution-smb
ms.custom:
- Adm_O365
- MiniMaven
- MSB365
- admindeeplinkMAC
- admindeeplinkEXCHANGE
- admindeeplinkSPO
search.appverid:
- BCS160
- MET150
description: الحصول على تعليمات حول زيادة مستوى الحماية في Microsoft 365 Business Premium
ms.openlocfilehash: c6533b966587235b8f29c1ce53bd9d5579b23b9c
ms.sourcegitcommit: 601ab9ad2b624e3b5e04eed927a08884c885c72a
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/24/2022
ms.locfileid: "64403798"
---
# <a name="increase-threat-protection-for-microsoft-365-business-premium"></a>زيادة الحماية من المخاطر Microsoft 365 Business Premium

في هذا الهدف، يمكنك زيادة الحماية من المخاطر باستخدام Microsoft 365 Business Premium. من المهم حماية المؤسسة من التصيد الاحتيالي والبرامج الضارة وغيرها من التهديدات. هذه التوصيات مناسبة على وجه الخصوص للحملات السياسية، والمكاتب القانونية، ومستشفيات الرعاية الصحية، التي تحتاج بشكل متزايد إلى الأمان.

## <a name="start-with-secure-score"></a>البدء ب "نقاط آمنة"

تقوم Microsoft Secure Score بتحليل أمان مؤسستك استنادا إلى الأنشطة العادية وإعدادات الأمان وتعيين درجة. دون نقاطك الحالية، ثم قم باتخاذ الإجراءات الموصى بها في هذه المقالة لزيادة نقاطك. الهدف هو أن تكون دائما على علم وحاول تحسين نقاطك.

لمزيد من المعلومات، راجع [Microsoft Secure Score](../security/defender/microsoft-secure-score.md).

## <a name="review-and-apply-preset-security-policies"></a>مراجعة سياسات الأمان المحددة مسبقا وتطبيقها

يتضمن اشتراكك [سياسات](../security/office-365-security/preset-security-policies.md) أمان معينة مسبقا تستخدم الإعدادات المستحسنة للحماية من البريد العشوائي والبرامج الضارة والحماية من التصيد الاحتيالي. بشكل افتراضي، يتم تمكين الحماية المضمنة؛ يجب تطبيق حماية قياسية أو صارمة لزيادة مستوى الأمان. 

تتكون سياسات الأمان المحددة مسبقا من:

- ملفات التعريف، التي تحدد مستوى الحماية
- السياسات (مثل مكافحة البريد العشوائي، مكافحة البرامج الضارة، مكافحة التصيد الاحتيالي، خزينة المرفقات، خزينة الارتباطات)
- إعدادات النهج (مثل المجموعات أو المستخدمين أو المجالات لتلقي النهج وأي استثناءات)

يلخص الجدول التالي مستويات الحماية وأنواع النهج المحددة مسبقا.

| مستوى الحماية | الوصف |
|:---|:---|
| **الحماية القياسية** <br/>(*مستحسن لمعظم الشركات*) | تستخدم الحماية القياسية ملف تعريف أساسي مناسب لمعظم المستخدمين <br/><br/>وهي تتضمن مكافحة البريد العشوائي، و مكافحة البرامج الضارة، و مكافحة التصيد الاحتيالي، و إعدادات الخادعة، وإعدادات انتحال الشخصية، خزينة الارتباطات، خزينة المرفقات.  |
| **حماية صارمة**  | تتضمن الحماية تقيدا الأنواع نفسها من السياسات كالحماية القياسية، ولكن مع إعدادات أكثر صرامة. إذا كان يتعين على شركتك تلبية متطلبات أو لوائح أمان إضافية، فنظر في تطبيق حماية صارمة على المستخدمين الذين لديهم أولوية أو أهداف ذات قيمة عالية. |
| **حماية مضمنة** | يحمي من الارتباطات الضارة والمرفقات في البريد الإلكتروني. يتم تمكينه وتطبيقه على جميع المستخدمين بشكل افتراضي.  |

يمكنك تحديد المستخدمين والمجموعات والمجالات لتلقي سياسات معينة مسبقا، كما يمكنك تحديد استثناءات معينة، ولكن لا يمكنك تغيير سياسات معينة مسبقا نفسها.

يمكنك أيضا إنشاء سياسات الأمان الخاصة بك لإعدادات مخصصة لتتناسب مع احتياجات شركتك.




<!--https://docs.microsoft.com/en-us/microsoft-365/security/office-365-security/recommended-settings-for-eop-and-office365?view=o365-worldwide


## Raise the level of protection against malware in mail

Your Office 365 or Microsoft 365 environment includes protection against malware, but you can increase this protection by blocking attachments with file types that are commonly used for malware. To bump up malware protection in email:

1. Go to the <a href="https://go.microsoft.com/fwlink/p/?linkid=2077143" target="_blank">Office 365 Security & Compliance Center</a> and sign in with your admin account credentials.

2. In the left navigation pane, under **Threat management**, choose **Policy** \> **Anti-Malware**.

3. Double-click the default policy to edit this company-wide policy.

4. Click **Settings**.

5. Under **Common Attachment Types Filter**, select **On**. The file types that are blocked are listed in the window directly below this control. Make sure you add these filetypes:

   `ade, adp, ani, bas, bat, chm, cmd, com, cpl, crt, hlp, ht, hta, inf, ins, isp, job, js, jse, lnk, mda, mdb, mde, mdz, msc, msi, msp, mst, pcd, reg, scr, sct, shs, url, vb, vbe, vbs, wsc, wsf, wsh, exe, pif`

   You can add or delete file types later, if needed.

6. Click **Save.**

For more information, see [Anti-malware protection in EOP](../security/office-365-security/anti-malware-protection.md).

## Protect against ransomware

Ransomware restricts access to data by encrypting files or locking computer screens. It then attempts to extort money from victims by asking for "ransom," usually in the form of cryptocurrencies like Bitcoin, in exchange for access to data.

You can protect against ransomware by creating one or more mail flow rules to block file extensions that are commonly used for ransomware (these were added in the [raise the level of protection against malware in mail](#raise-the-level-of-protection-against-malware-in-mail) step), or to warn users who receive these attachments in email.

In addition to the files that you blocked in the previous step, it's also good practice to create a rule to warn users before opening Office file attachments that include macros. Ransomware can be hidden inside macros, so warn users to not open these files from people they don't know.

To create a mail transport rule:

1. Go to the admin center at <https://admin.microsoft.com> and choose **Admin centers** \> **Exchange**.

2. In the **mail flow** category, click **rules**.

3. Click **+**, and then click **Create a new rule**.

4. Click **More options** at the bottom of the dialog box to see the full set of options.

5. Apply the settings in the following table for the rule. Leave the rest of the settings at the default, unless you want to change them.

6. Click **Save**.

|Setting|Warn users before opening attachments of Office files|
|---|---|
|Name|Anti-ransomware rule: warn users|
|Apply this rule if . . .|Any attachment . . . file extension matches . . .|
|Specify words or phrases|Add these file types: <br/> `dotm, docm, xlsm, sltm, xla, xlam, xll, pptm, potm, ppam, ppsm, sldm`|
|Do the following . . .|Notify the recipient with a message|
|Provide message text|Do not open these types of files from people you do not know because they might contain macros with malicious code.|

For more information, see:

- [Ransomware: how to reduce risk](https://www.microsoft.com/security/blog/2020/04/28/ransomware-groups-continue-to-target-healthcare-critical-services-heres-how-to-reduce-risk/)

- [Restore your OneDrive](https://support.microsoft.com//office/fa231298-759d-41cf-bcd0-25ac53eb8a15)

## Stop auto-forwarding for email

Hackers who gain access to a user's mailbox can steal your mail by setting the mailbox to automatically forward email. This can happen even without the user's awareness. You can prevent this from happening by configuring a mail flow rule.

To create a mail transport rule, either watch [this short video](https://support.office.com/article/f9d693ba-5c78-47c0-b156-8e461e062aa7) or follow these steps:

1. In the <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Microsoft 365 admin center</a>, click **Admin centers** \> **Exchange**.

2. In the **mail flow** category, click **rules**.

3. Click **+**, and then click **Create a new rule**.

4. Click **More options** at the bottom of the dialog box to see the full set of options.

5. Apply the settings in the following table. Leave the rest of the settings at the default, unless you want to change them.

6. Click **Save**.

|Setting|Warn users before opening attachments of Office files|
|---|---|
|Name|Prevent auto forwarding of email to external domains|
|Apply this rule if ...|The sender . . . is external/internal . . . Inside the organization|
|Add condition|The message properties . . . include the message type . . . Auto-forward|
|Do the following ...|Block the message . . . reject the message and include an explanation.|
|Provide message text|Auto-forwarding email outside this organization is prevented for security reasons.|

## Protect your email from phishing attacks

If you've configured one or more custom domains for your Office 365 or Microsoft 365 environment, you can configure targeted anti-phishing protection. Anti-phishing protection, part of Microsoft Defender for Office 365, can help protect your organization from malicious impersonation-based phishing attacks and other phishing attacks. If you haven't configured a custom domain, you don't need to do this.

We recommend that you get started with this protection by creating a policy to protect your most important users and your custom domain.

To create an anti-phishing policy in Defender for Office 365, watch [this short training video](https://support.office.com/article/86c425e1-1686-430a-9151-f7176cce4f2c), or complete the following steps:

1. Go to <a href="https://go.microsoft.com/fwlink/p/?linkid=2077143" target="_blank">Office 365 Security & Compliance Center</a>.

2. In the left navigation pane, under **Threat management**, choose **Policy**.

3. On the **Policy** page, choose **Anti-phishing**.

4. On the **Anti-phishing** page, select **+ Create**. A wizard launches that steps you through defining your anti-phishing policy.

5. Specify the name, description, and settings for your policy as recommended in the chart below. For more information, see [Learn about anti-phishing policy in Microsoft Defender for Office 365 options](../security/office-365-security/set-up-anti-phishing-policies.md).

6. After you've reviewed your settings, choose **Create this policy** or **Save**, as appropriate.

|Setting or option|Recommended setting|
|---|---|
|Name|Domain and most valuable staff|
|Description|Ensure most important staff and our domain are not being impersonated.|
|Add users to protect|Select **+ Add a condition, The recipient is**. Type user names or enter the email address of the business owners, partners, or candidate, managers, and other important staff members. You can add up to 20 internal and external addresses that you want to protect from impersonation.|
|Add domains to protect|Select **+ Add a condition, The recipient domain is**. Enter the custom domain associated with your Microsoft 365 subscription, if you defined one. You can enter more than one domain.|
|Choose actions|If email is sent by an impersonated user: Choose **Redirect message to another email address**, and then type the email address of the security administrator; for example, *Alice<span><span>@contoso.com*. <br/> If email is sent by an impersonated domain: Choose **Quarantine message**.|
|Mailbox intelligence|By default, mailbox intelligence is selected when you create a new anti-phishing policy. Leave this setting **On** for best results.|
|Add trusted senders and domains|Here you can add your own domain, or any other trusted domains.|
|Applied to|Select **The recipient domain is**. Under **Any of these**, select **Choose**. Select **+ Add**. Select the check box next to the name of the domain, for example, *contoso.<span><span>com*, in the list, and then select **Add**. Select **Done**.|

For more information, see [Set up anti-phishing policies in Defender for Office 365](../security/office-365-security/set-up-anti-phishing-policies.md).

## Protect against malicious attachments, files, and links with Defender for Office 365

![Banner that point to https://aka.ms/aboutM365preview.](../media/m365admincenterchanging.png)

First, make sure, in the admin center at <https://admin.microsoft.com> that you have the new admin center preview turned on. Turn on the toggle next to the text **The new admin center**.

   ![The new admin center preview on.](../media/previewon.png)

If you don't see the **Setup** page with cards in your tenant yet, see how to complete these steps in Security & Compliance Center. See [Set up Safe Attachments in the Security & Compliance Center](#set-up-safe-attachments-in-the-security--compliance-center) and [Set up Safe Links in the Security & Compliance Center](#set-up-safe-links-in-the-security--compliance-center).

1. In the left nav, choose **Setup**.
2. On the **Setup** page, choose **View** on the **Increase protection from advanced threats** card.

   ![Choose View on the Increase protection from advanced threats.](../media/startatp.png)

3. On the **Increase protection from advanced threats** page, choose **Get started**.
4. On the pane that opens, select the check boxes next to **Links and attachments in email**, **Scan files in SharePoint, OneDrive, and Teams**, and **Scan links in Office desktop and Office Online apps** under **Scan items for malicious content**.
    
   Under **Links and attachments in email**, Type in All Users, or the specific users whose email you want scanned.

   ![Select all check boxes in Increase protection from advanced threats.](../media/setatp.png)

5. Choose **Create policies** to turn on Safe Attachments and Safe Links.

### Set up Safe Attachments in the Security & Compliance Center

People regularly send, receive, and share attachments, such as documents, presentations, spreadsheets, and more. It's not always easy to tell whether an attachment is safe or malicious just by looking at an email message. Microsoft Defender for Office 365 includes Safe Attachment protection, but this protection is not turned on by default. We recommend that you create a new rule to begin using this protection. This protection extends to files in SharePoint, OneDrive, and Microsoft Teams.

To create a Safe Attachment policy, either watch [this short video](https://support.office.com/article/e7e68934-23dc-4b9c-b714-e82e27a8f8a5), or complete the following steps:

1. Go to <a href="https://go.microsoft.com/fwlink/p/?linkid=2077143" target="_blank">Office 365 Security & Compliance Center</a> and sign in with your admin account.

2. In the left navigation pane, under **Threat management**, choose **Policy**.

3. On the Policy page, choose **Safe Attachments**.

4. On the Safe attachments page, apply this protection broadly by selecting the **Turn on ATP for SharePoint, OneDrive, and Microsoft Teams** check box.

5. Select **+** to create a new policy.

6. Apply the settings in the following table.

7. After you review your settings, choose **Create this policy** or **Save**, as appropriate.

|Setting or option|Recommended setting|
|---|---|
|Name|Block current and future emails with detected malware.|
|Description|Block current and future emails and attachments with detected malware.|
|Save attachments unknown malware response|Select **Block - Block the current and future emails and attachments with detected malware**.|
|Redirect attachment on detection|Enable redirection (select this box) <br/> Enter the admin account or a mailbox setup for quarantine. <br/> Apply the above selection if malware scanning for attachments times out or error occurs (select this box).|
|Applied to|The recipient domain is . . . select your domain.|

For more information, see [Set up anti-phishing policies in Defender for Office 365](../security/office-365-security/set-up-anti-phishing-policies.md).

### Set up Safe Links in the Security & Compliance Center

Hackers sometimes hide malicious websites in links in email or other files. Safe Links, part of Microsoft Defender for Office 365, can help protect your organization by providing time-of-click verification of web addresses (URLs) in email messages and Office documents. Protection is defined through Safe Links policies.

We recommend that you do the following:

- Modify the default policy to increase protection.

- Add a new policy targeted to all recipients in your domain.

To set up Safe Links, watch [this short training video](https://support.office.com/article/61492713-53c2-47da-a6e7-fa97479e97fa), or complete the following steps:

1. Go to <a href="https://go.microsoft.com/fwlink/p/?linkid=2077143" target="_blank">Office 365 Security & Compliance Center</a> and sign in with your admin account.

2. In the left navigation pane, under **Threat management**, choose **Policy**.

3. On the Policy page, choose **Safe Links**.

To modify the default policy:

1. On the Safe links page, under **Policies that apply to the entire organization**, select the **Default** policy.

2. Under **Settings that apply to content except email**, select **Microsoft 365 Apps for enterprise, Office for iOS and Android**.

3. Click **Save**.

To create a new policy targeted to all recipients in your domain:

1. On the Safe links page, under **Policies that apply to the entire organization**, click **+** to create a new policy.

2. Apply the settings listed in the following table.

3. Click **Save**.

|Setting or option|Recommended setting|
|---|---|
|Name|Safe links policy for all recipients in the domain|
|Select the action for unknown potentially malicious URLs in messages|Select **On - URLs will be rewritten and checked against a list of known malicious links when user clicks on the link**.|
|Use Safe Attachments to scan downloadable content|Select this box.|
|Applied to|The recipient domain is . . . select your domain.|

For more information, see [Safe Links in Defender for Office 365](../security/office-365-security/safe-links.md).

-->

## <a name="turn-on-the-unified-audit-log"></a>تشغيل سجل التدقيق الموحد

بعد تشغيل البحث في سجل التدقيق في مركز التوافق & الأمان، يمكنك الاحتفاظ بالمسؤول ونشاط المستخدم الآخر في السجل والبحث فيه.

يجب أن يتم تعيين دور "سجلات التدقيق" Exchange Online تشغيل البحث في سجل التدقيق أو إيقاف تشغيله في Microsoft 365 الاشتراك. بشكل افتراضي، يتم تعيين هذا الدور إلى مجموعات دور إدارة التوافق وإدارة المؤسسة على صفحة <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">الأذونات في Exchange مركز الإدارة</a>. المسؤولون العامون Microsoft 365 هم أعضاء في هذه المجموعة بشكل افتراضي.

1. ل تشغيل البحث في سجل التدقيق، انتقل إلى مركز الإدارة في <https://admin.microsoft.com> ، ثم اختر **الأمان** ضمن **مراكز الإدارة** في التنقل الأيسر.
2. في صفحة **Microsoft 365 الأمان**، اختر موارد إضافية، ثم افتح على Office 365 الأمان &  **مركز التوافق**.

    ![اختر فتح على & التوافق.](../media/gotosecandcomp.png)
3. في صفحة الأمان والتوافق، اختر **بحث** ثم **بحث في سجل التدقيق**.
4. في أعلى صفحة البحث في **سجل** التدقيق، اختر **تشغيل التدقيق**.

بعد تشغيل الميزة، يمكنك البحث عن الملفات والمجلدات والعديد من الأنشطة. لمزيد من المعلومات، راجع [البحث في سجل التدقيق](../compliance/search-the-audit-log-in-security-and-compliance.md).

## <a name="tune-up-anonymous-sharing-settings-for-sharepoint-and-onedrive-files-and-folders"></a>ضبط إعدادات المشاركة المجهولة SharePoint والمجلدات OneDrive والمجلدات

(تغيير انتهاء صلاحية الارتباط المجهول الافتراضي إلى 14 يوما، وتغيير نوع المشاركة الافتراضية إلى "أشخاص محددون") لتغيير إعدادات المشاركة OneDrive SharePoint:

1. انتقل إلى مركز الإدارة <https://admin.microsoft.com> في **ثم اختر SharePoint** ضمن **مراكز الإدارة** في التنقل الأيسر.
2. في مركز SharePoint، انتقل إلى **مشاركة السياسات**\>.<a href="https://go.microsoft.com/fwlink/?linkid=2185222" target="_blank"></a>
3. في صفحة  المشاركة، ضمن ارتباطات الملفات والمجلدات، حدد أشخاص محددين، وضمن إعدادات متقدمة لاارتباطات **"** أي شخص"، حدد هذه الارتباطات يجب أن تنتهي صلاحيتها في غضون هذا العدد من الأيام، ثم اكتب في 14 (أو عدد آخر من الأيام التي تريد تقييد مدة صلاحية الارتباط بها).

   ![اختر أشخاص محددين ثم قم بتعيين انتهاء صلاحية الارتباط إلى 14 يوما.](../media/anyonelinks.png)


## <a name="activity-alerts"></a>تنبيهات النشاط

يمكنك استخدام تنبيهات النشاط لتعقب أنشطة المسؤول والمستخدم والكشف عن البرامج الضارة وحادثات منع فقدان البيانات في مؤسستك. يتضمن اشتراكك مجموعة من السياسات الافتراضية، ولكن يمكنك أيضا إنشاء سياسات مخصصة. لمزيد من المعلومات، راجع [سياسات التنبيه](../compliance/alert-policies.md). على سبيل المثال، إذا قمت بتخزين ملف هام في SharePoint لا تريد أن يشاركه أي شخص خارجيا، يمكنك إنشاء إعلام ينبهك إذا قام شخص ما ومشاركته.

يعرض الرسم البياني التالي السياسات الافتراضية المضمنة مع Microsoft 365.

![سياسات التنبيه الافتراضية المضمنة مع Microsoft 365.](../media/alertpolicies.png)

## <a name="disable-or-manage-calendar-sharing"></a>تعطيل مشاركة التقويم أو إدارتها

يمكنك منع الأشخاص في مؤسستك من مشاركة تقويماتهم، أو يمكنك أيضا إدارة ما يمكنهم مشاركته. على سبيل المثال، يمكنك تقييد المشاركة إلى أوقات الحرر/الانشغال فقط.

1. انتقل إلى مركز الإدارة في <https://admin.microsoft.com> واختر **الإعدادات** \> **المؤسسة الإعدادات** >  <a href="https://go.microsoft.com/fwlink/p/?linkid=2053743" target="_blank">**Services**</a>.

1. اختر **التقويم**، واختر ما إذا كان يمكن للأشخاص في مؤسستك مشاركة تقويماتهم مع أشخاص من خارج Office 365 أو Exchange أو مع أي شخص.

   إذا اخترت خيار المشاركة مع أي شخص، يمكنك أن تقرر أيضا مشاركة معلومات الشغل/الشغل فقط.

3. اختر **حفظ التغييرات** في أسفل الصفحة.

   يعرض الرسم البياني التالي مشاركة التقويم غير مسموح بها.

   ![لقطة شاشة لإظهار مشاركة التقويم الخارجي كما هو غير مسموح به.](../media/nocalendarsharing.png)

   يعرض الرسم البياني التالي الإعدادات عند السماح بمشاركة التقويم باستخدام ارتباط بريد إلكتروني مع معلومات الشغل/الشغل فقط.

   ![لقطة شاشة للمشاركة الحرة/المشغولة للتقويم مع أي شخص.](../media/sharefreebusy.png)

إذا تم السماح للمستخدمين بمشاركة تقويماتهم، فشاهد هذه الإرشادات حول [](https://support.office.com/article/7ecef8ae-139c-40d9-bae2-a23977ee58d5) كيفية المشاركة من Outlook على ويب.

