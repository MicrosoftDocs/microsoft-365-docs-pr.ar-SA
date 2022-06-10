---
title: إدارة تشفير رسائل Office 365
f1.keywords:
- NOCSH
ms.author: krowley
author: kccross
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.date: 03/04/2022
search.appverid:
- MET150
ms.assetid: 09f6737e-f03f-4bc8-8281-e46d24ee2a74
ms.collection:
- Strat_O365_IP
- M365-security-compliance
ms.custom:
- seo-marvel-apr2020
description: بمجرد الانتهاء من إعداد Office 365 تشفير الرسائل (OME)، تعرف على كيفية تخصيص النشر بعدة طرق.
ms.openlocfilehash: 2e39f811ec23b2f3b068ef5684fca479850a8744
ms.sourcegitcommit: 133bf9097785309da45df6f374a712a48b33f8e9
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 06/10/2022
ms.locfileid: "66014817"
---
# <a name="manage-office-365-message-encryption"></a>إدارة تشفير رسائل Office 365

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

بمجرد الانتهاء من إعداد Office 365 تشفير الرسائل (OME)، يمكنك تخصيص تكوين التوزيع بعدة طرق. على سبيل المثال، يمكنك تكوين ما إذا كنت تريد تمكين رموز المرور لمرة واحدة، وعرض الزر **"تشفير"** في Outlook على ويب، والمزيد. تصف المهام الواردة في هذه المقالة كيفية القيام بذلك.

## <a name="manage-whether-google-yahoo-and-microsoft-account-recipients-can-use-these-accounts-to-sign-in-to-the-office-365-message-encryption-portal"></a>إدارة ما إذا كان يمكن لمستلمي حساب Google وYahoo وMicrosoft استخدام هذه الحسابات لتسجيل الدخول إلى مدخل تشفير الرسائل Office 365

عند إعداد قدرات تشفير الرسائل Office 365 الجديدة، يمكن للمستخدمين في مؤسستك إرسال رسائل إلى مستلمين من خارج مؤسستك. إذا كان المستلم يستخدم *معرفا اجتماعيا* مثل حساب Google أو حساب Yahoo أو حساب Microsoft، يمكن للمستلم تسجيل الدخول إلى مدخل OME باستخدام معرف اجتماعي. إذا أردت، يمكنك اختيار عدم السماح للمستلمين باستخدام المعرف الاجتماعي لتسجيل الدخول إلى مدخل OME.

### <a name="to-manage-whether-recipients-can-use-social-ids-to-sign-in-to-the-ome-portal"></a>لإدارة ما إذا كان يمكن للمستلمين استخدام المعرف الاجتماعي لتسجيل الدخول إلى مدخل OME

1. [الاتصال إلى Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

2. قم بتشغيل Set-OMEConfiguration cmdlet مع المعلمة SocialIdSignIn كما يلي:

   ```powershell
   Set-OMEConfiguration -Identity <"OMEConfigurationIdParameter"> -SocialIdSignIn <$true|$false>
   ```

   على سبيل المثال، لتعطيل المعرف الاجتماعي:

   ```powershell
   Set-OMEConfiguration -Identity "OME Configuration" -SocialIdSignIn $false
   ```

   لتمكين المعرف الاجتماعي:

   ```powershell
   Set-OMEConfiguration -Identity "OME Configuration" -SocialIdSignIn $true
   ```

## <a name="manage-the-use-of-one-time-pass-codes-for-the-office-365-message-encryption-portal"></a>إدارة استخدام رموز المرور لمرة واحدة لمدخل تشفير الرسائل Office 365

إذا لم يستخدم مستلم رسالة مشفرة بواسطة OME Outlook، بغض النظر عن الحساب المستخدم من قبل المستلم، يتلقى المستلم ارتباط عرض ويب محدود الوقت يتيح له قراءة الرسالة. يتضمن هذا الارتباط رمز تمرير لمرة واحدة. بصفتك مسؤولا، يمكنك تحديد ما إذا كان يمكن للمستلمين استخدام رموز المرور لمرة واحدة لتسجيل الدخول إلى مدخل OME.

### <a name="to-manage-whether-ome-generates-one-time-pass-codes"></a>لإدارة ما إذا كان OME ينشئ رموز تمرير لمرة واحدة

1. استخدم حساب العمل أو المؤسسة التعليمية الذي لديه أذونات المسؤول العمومي في مؤسستك والاتصال Exchange Online PowerShell. للحصول على الإرشادات، راجع [الاتصال Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

2. تشغيل Set-OMEConfiguration cmdlet مع المعلمة OTPEnabled:

   ```powershell
   Set-OMEConfiguration -Identity <"OMEConfigurationIdParameter"> -OTPEnabled <$true|$false>
   ```

   على سبيل المثال، لتعطيل رموز المرور لمرة واحدة:

   ```powershell
   Set-OMEConfiguration -Identity "OME Configuration" -OTPEnabled $false
   ```

   لتمكين رموز المرور لمرة واحدة:

   ```powershell
   Set-OMEConfiguration -Identity "OME Configuration" -OTPEnabled $true
   ```

## <a name="manage-the-display-of-the-encrypt-button-in-outlook-on-the-web"></a>إدارة عرض الزر "تشفير" في Outlook على ويب

بصفتك مسؤولا، يمكنك إدارة ما إذا كنت تريد عرض هذا الزر للمستخدمين النهائيين.

### <a name="to-manage-whether-the-encrypt-button-appears-in-outlook-on-the-web"></a>لإدارة ما إذا كان الزر "تشفير" يظهر في Outlook على ويب

1. استخدم حساب العمل أو المؤسسة التعليمية الذي لديه أذونات المسؤول العمومي في مؤسستك والاتصال Exchange Online PowerShell. للحصول على الإرشادات، راجع [الاتصال Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

2. تشغيل Set-IRMConfiguration cmdlet مع المعلمة -SimplifiedClientAccessEnabled:

   ```powershell
   Set-IRMConfiguration -SimplifiedClientAccessEnabled <$true|$false>
   ```

   على سبيل المثال، لتعطيل الزر **"تشفير** ":

   ```powershell
   Set-IRMConfiguration -SimplifiedClientAccessEnabled $false
   ```

   لتمكين الزر **"تشفير** ":

   ```powershell
   Set-IRMConfiguration -SimplifiedClientAccessEnabled $true
   ```

## <a name="enable-service-side-decryption-of-email-messages-for-ios-mail-app-users"></a>تمكين فك تشفير رسائل البريد الإلكتروني من جانب الخدمة لمستخدمي تطبيق بريد iOS

يتعذر على تطبيق بريد iOS فك تشفير الرسائل المحمية بتشفير الرسائل Office 365. بصفتك مسؤول Microsoft 365، يمكنك تطبيق فك التشفير من جانب الخدمة على الرسائل التي يتم تسليمها إلى تطبيق بريد iOS. عندما تختار استخدام فك التشفير من جانب الخدمة، ترسل الخدمة نسخة مشفرة من الرسالة إلى جهاز iOS. يخزن جهاز العميل نسخة تم فك تشفيرها من الرسالة. تحتفظ الرسالة أيضا بمعلومات حول حقوق الاستخدام على الرغم من أن تطبيق بريد iOS لا يطبق حقوق الاستخدام من جانب العميل على المستخدم. يمكن للمستخدم نسخ الرسالة أو طباعتها حتى لو لم يكن لديه حقوق القيام بذلك في الأصل. ومع ذلك، إذا حاول المستخدم إكمال إجراء يتطلب خادم البريد Microsoft 365، مثل إعادة توجيه الرسالة، فلن يسمح الخادم بالإجراء إذا لم يكن لدى المستخدم حق الاستخدام في الأصل للقيام بذلك. ومع ذلك، يمكن للمستخدمين النهائيين العمل حول تقييد استخدام "عدم إعادة التوجيه" عن طريق إعادة توجيه الرسالة من حساب مختلف داخل تطبيق البريد iOS. بغض النظر عما إذا قمت بإعداد فك تشفير البريد من جانب الخدمة، لا يمكن عرض المرفقات إلى البريد المشفر والمحمي بحقوق في تطبيق بريد iOS.

إذا اخترت عدم السماح بإرسال الرسائل التي تم فك تشفيرها إلى مستخدمي تطبيق بريد iOS، فسيتلقى المستخدمون رسالة تنص على أنه ليس لديهم الحقوق لعرض الرسالة. بشكل افتراضي، لا يتم تمكين فك تشفير رسائل البريد الإلكتروني من جانب الخدمة.

لمزيد من المعلومات، ولعرض تجربة العميل، راجع [عرض الرسائل المشفرة على iPhone أو iPad](https://support.microsoft.com/en-us/office/view-protected-messages-on-your-iphone-or-ipad-4d631321-0d26-4bcc-a483-d294dd0b1caf).

### <a name="to-manage-whether-ios-mail-app-users-can-view-messages-protected-by-office-365-message-encryption"></a>لإدارة ما إذا كان يمكن لمستخدمي تطبيق بريد iOS عرض الرسائل المحمية بواسطة تشفير الرسائل Office 365

1. استخدم حساب العمل أو المؤسسة التعليمية الذي لديه أذونات المسؤول العمومي في مؤسستك والاتصال Exchange Online PowerShell. للحصول على الإرشادات، راجع [الاتصال Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

2. تشغيل cmdlet Set-ActiveSyncOrganizations مع المعلمة AllowRMSSupportForUnenlightenedApps:

   ```powershell
   Set-ActiveSyncOrganizationSettings -AllowRMSSupportForUnenlightenedApps <$true|$false>
   ```

   على سبيل المثال، لتكوين الخدمة لفك تشفير الرسائل قبل إرسالها إلى تطبيقات غير مضاءة مثل تطبيق بريد iOS:

   ```powershell
   Set-ActiveSyncOrganizationSettings -AllowRMSSupportForUnenlightenedApps $true
   ```

   أو لتكوين الخدمة لعدم إرسال رسائل تم فك تشفيرها إلى التطبيقات غير المضاءة:

   ```powershell
   Set-ActiveSyncOrganizationSettings -AllowRMSSupportForUnenlightenedApps $false
   ```

> [!NOTE]
> تتجاوز نهج علبة البريد الفردية (OWA/ActiveSync) هذه الإعدادات (على سبيل المثال، إذا تم تعيين -IRMEnabled إلى False ضمن نهج علبة بريد OWA المعنية، أو نهج علبة بريد ActiveSync، فلن يتم تطبيق هذه التكوينات).

## <a name="enable-service-side-decryption-of-email-attachments-for-web-browser-mail-clients"></a>تمكين فك تشفير مرفقات البريد الإلكتروني من جانب الخدمة لعملاء بريد مستعرض الويب

عادة، عند استخدام تشفير Office 365 الرسائل، يتم تشفير المرفقات تلقائيا. بصفتك مسؤولا، يمكنك تطبيق فك التشفير من جانب الخدمة لمرفقات البريد الإلكتروني التي يقوم المستخدمون بتنزيلها من مستعرض ويب.

عند استخدام فك التشفير من جانب الخدمة، ترسل الخدمة نسخة تم فك تشفيرها من الملف إلى الجهاز. لا تزال الرسالة مشفرة. يحتفظ مرفق البريد الإلكتروني أيضا بمعلومات حول حقوق الاستخدام على الرغم من أن المستعرض لا يطبق حقوق الاستخدام من جانب العميل على المستخدم. يمكن للمستخدم نسخ مرفق البريد الإلكتروني أو طباعته حتى لو لم يكن لديه حقوق القيام بذلك في الأصل. ومع ذلك، إذا حاول المستخدم إكمال إجراء يتطلب خادم البريد Microsoft 365، مثل إعادة توجيه المرفق، فلن يسمح الخادم بالإجراء إذا لم يكن لدى المستخدم حق الاستخدام في الأصل للقيام بذلك.

بغض النظر عما إذا كنت تقوم بإعداد فك تشفير المرفقات من جانب الخدمة، لا يمكن للمستخدمين عرض أي مرفقات للبريد المشفر والمحمي بحقوق في تطبيق بريد iOS.

إذا اخترت عدم السماح بمرفقات البريد الإلكتروني التي تم فك تشفيرها، وهو الإعداد الافتراضي، فسيتلقى المستخدمون رسالة تفيد بعدم منحهم الحقوق لعرض المرفق.

لمزيد من المعلومات حول كيفية تنفيذ Microsoft 365 للتشفير لرسائل البريد الإلكتروني ومرفقات البريد الإلكتروني باستخدام خيار Encrypt-Only، راجع [الخيار "تشفير فقط" لرسائل البريد الإلكتروني.](/azure/information-protection/deploy-use/configure-usage-rights#encrypt-only-option-for-emails)

### <a name="to-manage-whether-email-attachments-are-decrypted-on-download-from-a-web-browser"></a>لإدارة ما إذا كان يتم فك تشفير مرفقات البريد الإلكتروني عند التنزيل من مستعرض ويب

1. استخدم حساب العمل أو المؤسسة التعليمية الذي لديه أذونات المسؤول العمومي في مؤسستك والاتصال Exchange Online PowerShell. للحصول على الإرشادات، راجع [الاتصال Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

2. تشغيل Set-IRMConfiguration cmdlet مع المعلمة DecryptAttachmentForEncryptOnly:

   ```powershell
   Set-IRMConfiguration -DecryptAttachmentForEncryptOnly <$true|$false>
   ```

   على سبيل المثال، لتكوين الخدمة لفك تشفير مرفقات البريد الإلكتروني عندما يقوم المستخدم بتنزيلها من مستعرض ويب:

   ```powershell
   Set-IRMConfiguration -DecryptAttachmentForEncryptOnly $true
   ```

   لتكوين الخدمة لمغادرة مرفقات البريد الإلكتروني المشفرة كما هي عند التنزيل:

   ```powershell
   Set-IRMConfiguration -DecryptAttachmentForEncryptOnly $false
   ```

## <a name="ensure-all-external-recipients-use-the-ome-portal-to-read-encrypted-mail"></a>تأكد من أن جميع المستلمين الخارجيين يستخدمون مدخل OME لقراءة البريد المشفر

يمكنك استخدام قوالب العلامة التجارية المخصصة لإجبار المستلمين على تلقي بريد برنامج تضمين يوجههم لقراءة البريد الإلكتروني المشفر في مدخل OME بدلا من استخدام Outlook أو Outlook على ويب. قد ترغب في القيام بذلك إذا كنت تريد تحكما أكبر في كيفية استخدام المستلمين للبريد الذي يتلقونه. على سبيل المثال، إذا عرض المستلمون الخارجيون البريد الإلكتروني في مدخل الويب، يمكنك تعيين تاريخ انتهاء صلاحية للبريد الإلكتروني، ويمكنك إبطال البريد الإلكتروني. يتم دعم هذه الميزات فقط من خلال مدخل OME. يمكنك استخدام الخيار "تشفير" والخيار "عدم إعادة التوجيه" عند إنشاء قواعد تدفق البريد.

### <a name="use-a-custom-template-to-force-all-external-recipients-to-use-the-ome-portal-and-for-encrypted-email"></a>استخدام قالب مخصص لإجبار جميع المستلمين الخارجيين على استخدام مدخل OME والبريد الإلكتروني المشفر

1. استخدم حساب العمل أو المؤسسة التعليمية الذي لديه أذونات المسؤول العمومي في مؤسستك والاتصال Exchange Online PowerShell. للحصول على الإرشادات، راجع [الاتصال Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

2. تشغيل أمر cmdlet New-TransportRule:

   ```powershell
   New-TransportRule -name "<mail flow rule name>" -FromScope "InOrganization" -ApplyRightsProtectionTemplate "<option name>" -ApplyRightsProtectionCustomizationTemplate "<template name>"
   ```

    حيث:

   - `mail flow rule name` هو الاسم الذي تريد استخدامه لقاعدة تدفق البريد الجديدة.

   - `option name` إما أو `Encrypt` `Do Not Forward`.

   - `template name` هو الاسم الذي أعطيته لقالب العلامة التجارية المخصصة، على سبيل المثال `OME Configuration`.

   لتشفير كل رسائل البريد الإلكتروني الخارجية باستخدام قالب "تكوين OME" وتطبيق الخيار Encrypt-Only:

   ```powershell
   New-TransportRule -name "<All outgoing mail>" -FromScope "InOrganization" -ApplyRightsProtectionTemplate "Encrypt" -ApplyRightsProtectionCustomizationTemplate "OME Configuration"
   ```

   لتشفير كل رسائل البريد الإلكتروني الخارجية باستخدام قالب "تكوين OME" وتطبيق الخيار "عدم إعادة التوجيه":

   ```powershell
   New-TransportRule -name "<All outgoing mail>" -FromScope "InOrganization" -ApplyRightsProtectionTemplate "Do Not Forward" -ApplyRightsProtectionCustomizationTemplate "OME Configuration"
   ```

## <a name="customize-the-appearance-of-email-messages-and-the-ome-portal"></a>تخصيص مظهر رسائل البريد الإلكتروني ومدخل OME

للحصول على معلومات مفصلة حول كيفية تخصيص تشفير رسائل Microsoft Purview لمؤسستك، راجع [إضافة العلامة التجارية لمؤسستك إلى الرسائل المشفرة](add-your-organization-brand-to-encrypted-messages.md). لتمكين القدرة على تعقب الرسائل المشفرة وإبطالها، يجب إضافة العلامة التجارية المخصصة إلى مدخل OME.

## <a name="disable-microsoft-purview-message-encryption"></a>تعطيل تشفير الرسائل ل Microsoft Purview

نأمل ألا يصل إلى ذلك، ولكن إذا كنت بحاجة إلى ذلك، فإن تعطيل تشفير الرسائل ل Microsoft Purview أمر مباشر للغاية. أولا، ستحتاج إلى إزالة أي قواعد لتدفق البريد قمت بإنشائها تستخدم تشفير الرسائل من Microsoft Purview. للحصول على معلومات حول إزالة قواعد تدفق البريد، راجع [إدارة قواعد تدفق البريد](/exchange/security-and-compliance/mail-flow-rules/manage-mail-flow-rules). ثم أكمل هذه الخطوات في Exchange Online PowerShell.

### <a name="to-disable-microsoft-purview-message-encryption"></a>لتعطيل تشفير الرسائل ل Microsoft Purview

1. باستخدام حساب العمل أو المؤسسة التعليمية الذي لديه أذونات المسؤول العام في مؤسستك، اتصل Exchange Online PowerShell. للحصول على الإرشادات، راجع [الاتصال Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

2. إذا قمت بتمكين الزر **"تشفير"** في Outlook على ويب، فعطله عن طريق تشغيل Set-IRMConfiguration cmdlet باستخدام المعلمة SimplifiedClientAccessEnabled. وإلا، فانتقل إلى هذه الخطوة.

   ```powershell
   Set-IRMConfiguration -SimplifiedClientAccessEnabled $false
   ```

3. تعطيل تشفير رسالة Microsoft Purview عن طريق تشغيل cmdlet Set-IRMConfiguration مع تعيين المعلمة AzureRMSLicensingEnabled إلى false:

   ```powershell
   Set-IRMConfiguration -AzureRMSLicensingEnabled $false
   ```
