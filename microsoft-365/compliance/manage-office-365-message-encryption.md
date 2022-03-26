---
title: إدارة تشفير الرسائل من Office 365
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
description: بعد الانتهاء من إعداد تشفير الرسائل من Office 365 (OME)، تعرف على كيفية تخصيص النشر بطرق متعددة.
ms.openlocfilehash: 49a3957eb4bc2cf1123f04ab0dea77d2adb638b0
ms.sourcegitcommit: a216617d6ff27fe7d3089a047fbeaac5d72fd25c
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/16/2022
ms.locfileid: "63565916"
---
# <a name="manage-office-365-message-encryption"></a>إدارة تشفير الرسائل من Office 365

بعد الانتهاء من إعداد تشفير الرسائل من Office 365 (OME)، يمكنك تخصيص تكوين النشر بطرق متعددة. على سبيل المثال، يمكنك تكوين ما إذا كنت تريد تمكين رموز المرور مرة واحدة أو عرض الزر  تشفير في Outlook على ويب والمزيد. تصف المهام في هذه المقالة كيفية القيام بذلك.

## <a name="manage-whether-google-yahoo-and-microsoft-account-recipients-can-use-these-accounts-to-sign-in-to-the-office-365-message-encryption-portal"></a>إدارة ما إذا كان يمكن لمستلمي حساب Google و Yahoo و Microsoft استخدام هذه الحسابات في تسجيل الدخول إلى مدخل تشفير الرسائل من Office 365 الإلكتروني

عند إعداد إمكانيات تشفير الرسائل من Office 365 الجديدة، يمكن للمستخدمين في مؤسستك إرسال رسائل إلى المستلمين الجهات من خارج مؤسستك. إذا كان المستلم يستخدم الم *ID اجتماعي* مثل حساب Google أو حساب Yahoo أو حساب Microsoft، يمكن للمستلم تسجيل الدخول إلى مدخل OME باستخدام الم ID الاجتماعية. يمكنك اختيار عدم السماح للمستلمين باستخدام الم IDS الاجتماعية في تسجيل الدخول إلى مدخل OME، إذا أردت ذلك.
  
### <a name="to-manage-whether-recipients-can-use-social-ids-to-sign-in-to-the-ome-portal"></a>لإدارة ما إذا كان يمكن للمستلمين استخدام الم IDS الاجتماعية في تسجيل الدخول إلى مدخل OME
  
1. [الاتصال Exchange Online استخدام PowerShell البعيد](/powershell/exchange/connect-to-exchange-online-powershell).

2. تشغيل Set-OMEConfiguration cmdlet باستخدام المعلمة SocialIdSignIn كما يلي:

   ```powershell
   Set-OMEConfiguration -Identity <"OMEConfigurationIdParameter"> -SocialIdSignIn <$true|$false>
   ```

   على سبيل المثال، لتعطيل الم IDS الاجتماعية:

   ```powershell
   Set-OMEConfiguration -Identity "OME Configuration" -SocialIdSignIn $false
   ```

   لتمكين الم IDS الاجتماعية:

   ```powershell
   Set-OMEConfiguration -Identity "OME Configuration" -SocialIdSignIn $true
   ```

## <a name="manage-the-use-of-one-time-pass-codes-for-the-office-365-message-encryption-portal"></a>إدارة استخدام رموز المرور مرة واحدة تشفير الرسائل من Office 365 المدخل

إذا لم يستخدم مستلم الرسالة المشفرة بواسطة OME Outlook، بغض النظر عن الحساب المستخدم بواسطة المستلم، يتلقى المستلم ارتباط عرض ويب لفترة محدودة يتيح له قراءة الرسالة. يتضمن هذا الارتباط رمز مرور مرة واحدة. ب أنت مسؤول، يمكنك تحديد ما إذا كان يمكن للمستلمين استخدام رموز المرور مرة واحدة تسجيل الدخول إلى مدخل OME.
  
### <a name="to-manage-whether-ome-generates-one-time-pass-codes"></a>لإدارة ما إذا كان OME يقوم بإنشاء رموز المرور مرة واحدة
  
1. استخدم حساب العمل أو المؤسسة الدراسية الذي لديه أذونات المسؤول العام في مؤسستك وابدأ جلسة عمل Windows PowerShell واتصل Exchange Online. للحصول على الإرشادات، [راجع الاتصال Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

2. تشغيل Set-OMEConfiguration cmdlet باستخدام المعلمة OTPEnabled:

   ```powershell
   Set-OMEConfiguration -Identity <"OMEConfigurationIdParameter"> -OTPEnabled <$true|$false>
   ```

   على سبيل المثال، لتعطيل رموز المرور مرة واحدة:

   ```powershell
   Set-OMEConfiguration -Identity "OME Configuration" -OTPEnabled $false
   ```

   لتمكين رموز المرور مرة واحدة:

   ```powershell
   Set-OMEConfiguration -Identity "OME Configuration" -OTPEnabled $true
   ```

## <a name="manage-the-display-of-the-encrypt-button-in-outlook-on-the-web"></a>إدارة عرض الزر تشفير في Outlook على ويب

كمسؤول، يمكنك إدارة ما إذا كنت تريد عرض هذا الزر للمستخدمين النهائيين أم لا.
  
### <a name="to-manage-whether-the-encrypt-button-appears-in-outlook-on-the-web"></a>لإدارة ما إذا كان الزر تشفير يظهر في Outlook على ويب
  
1. استخدم حساب العمل أو المؤسسة الدراسية الذي لديه أذونات المسؤول العام في مؤسستك وابدأ جلسة عمل Windows PowerShell واتصل Exchange Online. للحصول على الإرشادات، [راجع الاتصال Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

2. تشغيل Set-IRMConfiguration cmdlet باستخدام المعلمة -SimplifiedClientAccessEnabled:

   ```powershell
   Set-IRMConfiguration -SimplifiedClientAccessEnabled <$true|$false>
   ```

   على سبيل المثال، لتعطيل **الزر تشفير** :

   ```powershell
   Set-IRMConfiguration -SimplifiedClientAccessEnabled $false
   ```

   لتمكين الزر **تشفير** :

   ```powershell
   Set-IRMConfiguration -SimplifiedClientAccessEnabled $true
   ```

## <a name="enable-service-side-decryption-of-email-messages-for-ios-mail-app-users"></a>تمكين فك تشفير رسائل البريد الإلكتروني من جانب الخدمة لمستخدمي تطبيق بريد iOS

لا يمكن لتطبيق البريد في iOS فك تشفير الرسائل المحمية باستخدام تشفير الرسائل من Office 365. كمسؤول Microsoft 365، يمكنك تطبيق فك تشفير من جانب الخدمة للرسائل التي يتم تسليمها إلى تطبيق بريد iOS. عندما تختار استخدام فك تشفير من جانب الخدمة، ترسل الخدمة نسخة فك تشفير من الرسالة إلى جهاز iOS. يخزن الجهاز العميل نسخة مفككة من الرسالة. تحتفظ الرسالة أيضا بمعلومات حول حقوق الاستخدام على الرغم من أن تطبيق بريد iOS لا يطبق حقوق الاستخدام من جانب العميل على المستخدم. يمكن للمستخدم نسخ الرسالة أو طباعتها حتى لو لم يكن لديه في الأصل حقوق القيام بذلك. ومع ذلك، إذا حاول المستخدم إكمال إجراء يتطلب خادم بريد Microsoft 365، مثل إعادة توجيه الرسالة، فلن يسمح الخادم بالتحرك إذا لم يكن للمستخدم حق الاستخدام في الأصل للقيام بذلك. ومع ذلك، يمكن للمستخدمين العمل على تقييد استخدام "عدم إعادة توجيه" من خلال إعادة توجيه الرسالة من حساب مختلف داخل تطبيق البريد في iOS. بغض النظر عما إذا قمت بإعداد فك تشفير البريد من جانب الخدمة، لا يمكن عرض المرفقات إلى البريد المشفر والمحمي بالحقوق في تطبيق البريد في iOS.
  
إذا اخترت عدم السماح بإرسال الرسائل التي تم فك تشفيرها إلى مستخدمي تطبيق البريد في iOS، سيتلقى المستخدمون رسالة تعلمهم بأنه ليس لديهم حقوق عرض الرسالة. بشكل افتراضي، لا يتم تمكين فك تشفير رسائل البريد الإلكتروني من جانب الخدمة.
  
لمزيد من المعلومات، ولرؤية تجربة العميل، راجع عرض الرسائل المشفرة على iPhone [أو iPad](https://support.microsoft.com/en-us/office/view-protected-messages-on-your-iphone-or-ipad-4d631321-0d26-4bcc-a483-d294dd0b1caf).
  
### <a name="to-manage-whether-ios-mail-app-users-can-view-messages-protected-by-office-365-message-encryption"></a>لإدارة ما إذا كان يمكن لمستخدمي تطبيق البريد iOS عرض الرسائل المحمية بواسطة تشفير الرسائل من Office 365
  
1. استخدم حساب العمل أو المؤسسة الدراسية الذي لديه أذونات المسؤول العام في مؤسستك وابدأ جلسة عمل Windows PowerShell واتصل Exchange Online. للحصول على الإرشادات، [راجع الاتصال Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

2. شغل Set-ActiveSyncOrganizations cmdlet باستخدام المعلمة AllowRMSSupportForUnenlightenedApps:

   ```powershell
   Set-ActiveSyncOrganizationSettings -AllowRMSSupportForUnenlightenedApps <$true|$false>
   ```

   على سبيل المثال، لتكوين الخدمة لفك تشفير الرسائل قبل إرسالها إلى تطبيقات غير مضاءة مثل تطبيق بريد iOS:

   ```powershell
   Set-ActiveSyncOrganizationSettings -AllowRMSSupportForUnenlightenedApps $true
   ```

   أو لتكوين الخدمة حتى لا يتم إرسال رسائل تم فك تشفيرها إلى التطبيقات التي لم يتم إضاءتها:

   ```powershell
   Set-ActiveSyncOrganizationSettings -AllowRMSSupportForUnenlightenedApps $false
   ```

> [!NOTE]
> تتجاوز نهج علبة البريد الفردية (OWA/ActiveSync) هذه الإعدادات (أي إذا تم تعيين -IRMEnabled إلى False ضمن نهج علبة بريد OWA أو نهج علبة بريد ActiveSync، فإن هذه التكوينات لن تنطبق).

## <a name="enable-service-side-decryption-of-email-attachments-for-web-browser-mail-clients"></a>تمكين فك تشفير مرفقات البريد الإلكتروني من جانب الخدمة لعملاء البريد في مستعرض ويب

عادة، عند Office 365 تشفير الرسائل، يتم تشفير المرفقات تلقائيا. كمسؤول، يمكنك تطبيق فك تشفير من جانب الخدمة لمرفقات البريد الإلكتروني التي يقوم المستخدمون بتنزيلها من مستعرض ويب.
  
عند استخدام فك تشفير من جانب الخدمة، ترسل الخدمة نسخة فك تشفير من الملف إلى الجهاز. لا تزال الرسالة مشفرة. يحتفظ مرفق البريد الإلكتروني أيضا بمعلومات حول حقوق الاستخدام على الرغم من أن المستعرض لا يطبق حقوق الاستخدام من جانب العميل على المستخدم. يمكن للمستخدم نسخ مرفق البريد الإلكتروني أو طباعته حتى لو لم يكن لديه في الأصل حقوق القيام بذلك. ومع ذلك، إذا حاول المستخدم إكمال إجراء يتطلب خادم بريد Microsoft 365، مثل إعادة توجيه المرفق، فلن يسمح الخادم بالفعل إذا لم يكن لدى المستخدم حق الاستخدام في الأصل للقيام بذلك.
  
وبصرف النظر عما إذا قمت بإعداد فك تشفير المرفقات من جانب الخدمة، لا يمكن للمستخدمين عرض أي مرفقات إلى البريد المشفر والمحمي بحقوق في تطبيق بريد iOS.
  
إذا اخترت عدم السماح بفك تشفير مرفقات البريد الإلكتروني، وهو الإعداد الافتراضي، يتلقى المستخدمون رسالة تعلمهم بأنه ليس لديهم حقوق عرض المرفق.
  
لمزيد من المعلومات حول كيفية Microsoft 365 تشفير رسائل البريد الإلكتروني ومرفقات البريد الإلكتروني باستخدام خيار Encrypt-Only، راجع الخيار تشفير [فقط لر رسائل البريد الإلكتروني.](/azure/information-protection/deploy-use/configure-usage-rights#encrypt-only-option-for-emails)
  
### <a name="to-manage-whether-email-attachments-are-decrypted-on-download-from-a-web-browser"></a>لإدارة ما إذا كان قد تم فك تشفير مرفقات البريد الإلكتروني عند التنزيل من مستعرض ويب
  
1. استخدم حساب العمل أو المؤسسة الدراسية الذي لديه أذونات المسؤول العام في مؤسستك وابدأ جلسة عمل Windows PowerShell واتصل Exchange Online. للحصول على الإرشادات، [راجع الاتصال Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

2. تشغيل Set-IRMConfiguration cmdlet باستخدام المعلمة DecryptAttachmentForEncryptOnly:

   ```powershell
   Set-IRMConfiguration -DecryptAttachmentForEncryptOnly <$true|$false>
   ```

   على سبيل المثال، لتكوين الخدمة لفك تشفير مرفقات البريد الإلكتروني عندما يقوم مستخدم بتنزيلها من مستعرض ويب:

   ```powershell
   Set-IRMConfiguration -DecryptAttachmentForEncryptOnly $true
   ```

   لتكوين الخدمة لترك مرفقات البريد الإلكتروني المشفرة كما هي عند التنزيل:

   ```powershell
   Set-IRMConfiguration -DecryptAttachmentForEncryptOnly $false
   ```

## <a name="ensure-all-external-recipients-use-the-ome-portal-to-read-encrypted-mail"></a>التأكد من أن جميع المستلمين الخارجيين يستخدمون مدخل OME لقراءة البريد المشفر

يمكنك استخدام قوالب العلامة التجارية المخصصة لجبر المستلمين على تلقي بريد ملتف يوجههم لقراءة البريد الإلكتروني المشفر في مدخل OME بدلا من استخدام Outlook أو Outlook على ويب. قد ترغب في القيام بذلك إذا كنت تريد التحكم بشكل أكبر في كيفية استخدام المستلمين للبريد الذي يتلقونه. على سبيل المثال، إذا كان المستلمون الخارجيون يعرضون البريد الإلكتروني في مدخل الويب، يمكنك تعيين تاريخ انتهاء صلاحية للبريد الإلكتروني، كما يمكنك إبطال البريد الإلكتروني. يتم دعم هذه الميزات فقط من خلال مدخل OME. يمكنك استخدام الخيار تشفير و الخيار عدم إعادة توجيه عند إنشاء قواعد تدفق البريد.

### <a name="use-a-custom-template-to-force-all-external-recipients-to-use-the-ome-portal-and-for-encrypted-email"></a>استخدام قالب مخصص لجبر جميع المستلمين الخارجيين على استخدام مدخل OME والبريد الإلكتروني المشفر

1. استخدم حساب العمل أو المؤسسة الدراسية الذي لديه أذونات المسؤول العام في مؤسستك وابدأ جلسة عمل Windows PowerShell واتصل Exchange Online. للحصول على الإرشادات، [راجع الاتصال Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

2. تشغيل New-TransportRule cmdlet:

   ```powershell
   New-TransportRule -name "<mail flow rule name>" -FromScope "InOrganization" -ApplyRightsProtectionTemplate "<option name>" -ApplyRightsProtectionCustomizationTemplate "<template name>"
   ```

    حيث:

   - `mail flow rule name` هو الاسم الذي تريد استخدامه لقاعدة تدفق البريد الجديدة.

   - `option name` إما أو `Encrypt` `Do Not Forward`.

   - `template name` هو الاسم الذي منحته قالب العلامة التجارية المخصص، على سبيل المثال `OME Configuration`.

   لتشفير كل رسائل البريد الإلكتروني الخارجية باستخدام قالب "تكوين OME" وتطبيق Encrypt-Only:

   ```powershell
   New-TransportRule -name "<All outgoing mail>" -FromScope "InOrganization" -ApplyRightsProtectionTemplate "Encrypt" -ApplyRightsProtectionCustomizationTemplate "OME Configuration"
   ```

   لتشفير كل رسائل البريد الإلكتروني الخارجية باستخدام القالب "تكوين OME" وتطبيق الخيار عدم إعادة توجيه:

   ```powershell
   New-TransportRule -name "<All outgoing mail>" -FromScope "InOrganization" -ApplyRightsProtectionTemplate "Do Not Forward" -ApplyRightsProtectionCustomizationTemplate "OME Configuration"
   ```

## <a name="customize-the-appearance-of-email-messages-and-the-ome-portal"></a>تخصيص مظهر رسائل البريد الإلكتروني ومدخل OME

للحصول على معلومات مفصلة حول كيفية تخصيص OME لمنظمتك، راجع إضافة العلامة التجارية لمنظمتك [إلى الرسائل المشفرة](add-your-organization-brand-to-encrypted-messages.md). لتمكين القدرة على تعقب الرسائل المشفرة وإبطالها، يجب إضافة علامتك التجارية المخصصة إلى مدخل OME.
  
## <a name="disable-the-new-capabilities-for-ome"></a>تعطيل الإمكانات الجديدة ل OME

نأمل ألا يكون ذلك سهلا، ولكن إذا كنت بحاجة إلى ذلك، فإن تعطيل الإمكانات الجديدة ل OME أمر بسيط للغاية. أولا، ستحتاج إلى إزالة أي قواعد تدفق بريد أنشأتها تستخدم قدرات OME الجديدة. للحصول على معلومات حول إزالة قواعد تدفق البريد، راجع [إدارة قواعد تدفق البريد](/exchange/security-and-compliance/mail-flow-rules/manage-mail-flow-rules). بعد ذلك، أكمل هذه الخطوات في Exchange Online PowerShell.
  
### <a name="to-disable-the-new-capabilities-for-ome"></a>لتعطيل الإمكانات الجديدة ل OME
  
1. باستخدام حساب العمل أو المؤسسة الدراسية الذي لديه أذونات المسؤول العام في مؤسستك، ابدأ جلسة عمل Windows PowerShell واتصل Exchange Online. للحصول على الإرشادات، [راجع الاتصال Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

2. إذا قمت بتمكين الزر تشفير  في Outlook على ويب، فعطله عن طريق تشغيل الأمر cmdlet Set-IRMConfiguration باستخدام المعلمة SimplifiedClientAccessEnabled. وإلا، فتخطى هذه الخطوة.

   ```powershell
   Set-IRMConfiguration -SimplifiedClientAccessEnabled $false
   ```

3. قم بتعطيل الإمكانات الجديدة ل OME عن طريق تشغيل Set-IRMConfiguration cmdlet مع تعيين معلمة AzureRMSLicensingEnabled إلى خطأ:

   ```powershell
   Set-IRMConfiguration -AzureRMSLicensingEnabled $false
   ```
