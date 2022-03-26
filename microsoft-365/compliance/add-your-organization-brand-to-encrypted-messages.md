---
title: إضافة العلامة التجارية لمنظمتك إلى الرسائل المشفرة
f1.keywords:
- NOCSH
ms.author: krowley
author: kccross
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.date: 4/1/2020
search.appverid:
- MET150
- MOE150
ms.assetid: 7a29260d-2959-42aa-8916-feceff6ee51d
ms.collection:
- Strat_O365_IP
- M365-security-compliance
ms.custom:
- seo-marvel-apr2020
- seo-marvel-jun2020
- admindeeplinkMAC
- admindeeplinkEXCHANGE
description: تعرف على Office 365 يمكن للمسؤولين العامين تطبيق العلامة التجارية لمنظمتك على رسائل البريد الإلكتروني المشفرة & محتويات مدخل التشفير.
ms.openlocfilehash: b96f87886b6f1dc5ca78de068b86dbbcfb9e460d
ms.sourcegitcommit: 99067d5eb1fa7b094e7cdb1f7be65acaaa235a54
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 01/29/2022
ms.locfileid: "63568553"
---
# <a name="add-your-organizations-brand-to-your-microsoft-365-for-business-message-encryption-encrypted-messages"></a>إضافة العلامة التجارية لمنظمتك إلى الرسائل المشفرة لتشفير Microsoft 365 للأعمال

يمكنك تطبيق العلامة التجارية للشركة لتخصيص مظهر رسائل البريد الإلكتروني الخاصة بالشركة ومدخل التشفير. ستحتاج إلى تطبيق أذونات المسؤول العام على حساب العمل أو المؤسسة الدراسية قبل أن تتمكن من البدء. بمجرد الحصول على هذه الأذونات، استخدم Get-OMEConfiguration Set-OMEConfiguration Windows PowerShell cmdlets لتخصيص هذه الأجزاء من رسائل البريد الإلكتروني المشفرة:

- نص تمهيدي
- نص إخلاء المسؤولية
- URL لبيان خصوصية مؤسستك
- النص في مدخل OME
- الشعار الذي يظهر في رسالة البريد الإلكتروني ومدخل OME، أو ما إذا كنت تريد استخدام شعار على الإطلاق
- لون الخلفية في رسالة البريد الإلكتروني ومدخل OME

يمكنك أيضا العودة إلى شكله الافتراضي ومظهره في أي وقت.

إذا كنت تريد المزيد من التحكم، فاستخدم تشفير الرسائل المتقدم من Office 365 لإنشاء قوالب متعددة لر رسائل البريد الإلكتروني المشفرة التي تم إنشاؤها من مؤسستك. استخدم هذه القوالب للتحكم في أجزاء من تجربة المستخدم النهائي. على سبيل المثال، حدد ما إذا كان يمكن للمستلمين استخدام حسابات Google و Yahoo و Microsoft تسجيل الدخول إلى مدخل التشفير. استخدم القوالب لتنفيذ العديد من حالات الاستخدام، مثل:

- الأقسام الفردية، مثل الشؤون المالية والمبيعات وما إلى ذلك.
- منتجات مختلفة
- مناطق جغرافية مختلفة أو بلدان مختلفة
- ما إذا كنت تريد السماح بإبطال رسائل البريد الإلكتروني
- ما إذا كنت تريد انتهاء صلاحية رسائل البريد الإلكتروني المرسلة إلى مستلمين خارجيين بعد عدد محدد من الأيام.

بعد إنشاء القوالب، يمكنك تطبيقها على رسائل البريد الإلكتروني المشفرة باستخدام Exchange تدفق البريد. إذا كان لديك تشفير الرسائل المتقدم من Office 365، يمكنك إبطال أي بريد إلكتروني قمت بعلامة تجارية له باستخدام هذه القوالب.

## <a name="work-with-ome-branding-templates"></a>استخدام قوالب العلامة التجارية ل OME

يمكنك تعديل العديد من الميزات داخل قالب العلامة التجارية. يمكنك تعديل القالب الافتراضي وليس إزالته. إذا كان لديك تشفير رسائل متقدم، يمكنك أيضا إنشاء قوالب مخصصة وتعديلها وإزالتها. استخدم Windows PowerShell لاستخدام قالب علامة تجارية واحد في كل مرة.

- [Set-OMEConfiguration](/powershell/module/exchange/set-omeconfiguration) - تعديل قالب العلامة التجارية الافتراضي أو قالب علامة تجارية مخصص أنشأته.
- [New-OMEConfiguration](/powershell/module/exchange/new-omeconfiguration) - إنشاء قالب علامة تجارية جديدة، تشفير الرسائل المتقدمة فقط.
- [Remove-OMEConfiguration](/powershell/module/exchange/remove-omeconfiguration) - إزالة قالب علامة تجارية مخصص، تشفير الرسائل المتقدم فقط. لا يمكنك حذف قالب العلامة التجارية الافتراضي.

## <a name="modify-an-ome-branding-template"></a>تعديل قالب العلامة التجارية OME

استخدم Windows PowerShell لتعديل قالب علامة تجارية واحد في كل مرة. إذا كان لديك تشفير رسائل متقدم، يمكنك أيضا إنشاء قوالب مخصصة وتعديلها وإزالتها.

1. باستخدام حساب العمل أو المؤسسة الدراسية الذي لديه أذونات المسؤول العام في مؤسستك، ابدأ جلسة عمل Windows PowerShell واتصل Exchange Online. للحصول على الإرشادات، [راجع الاتصال Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

2. استخدم Set-OMEConfiguration cmdlet كما هو موضح في [Set-OMEConfiguration](/powershell/module/exchange/Set-OMEConfiguration) أو استخدم الرسم الجدول التالي للحصول على الإرشادات.

![أجزاء البريد الإلكتروني القابلة للتخصيص.](../media/ome-template-breakout.png)

<br>

****

|**لتخصيص هذه الميزة لتجربة التشفير**|**استخدام هذه الأوامر**|
|---|---|
|لون الخلفية|`Set-OMEConfiguration -Identity "<OMEConfigurationName>" -BackgroundColor "<#RRGGBB hexadecimal color code or name value>"` <p> **مثال:** <p> `Set-OMEConfiguration -Identity "Branding Template 1" -BackgroundColor "#ffffff"` <p> لمزيد من المعلومات حول ألوان الخلفية، راجع المقطع [ألوان الخلفية](#background-color-reference) لاحقا في هذه المقالة.|
|شعار|`Set-OMEConfiguration -Identity "<OMEConfigurationName>" -Image <Byte[]>` <p> **مثال:** <p> `Set-OMEConfiguration -Identity "Branding Template 1" -Image ([System.IO.File]::ReadAllBytes('C:\Temp\contosologo.png'))` <p> تنسيقات الملفات المعتمدة: .png أو .jpg أو .bmp أو tiff. <p> الحجم الأمثل لملف الشعار: أقل من 40 كيلوB <p> الحجم الأمثل للصورة: 170x70 بكسل. إذا تجاوزت صورتك هذه الأبعاد، فإن الخدمة تقوم تغيير حجم الشعار لعرضه في المدخل. لا تقوم الخدمة بتعديل ملف الرسم نفسه. للحصول على أفضل النتائج، استخدم الحجم الأمثل.|
|نص بجانب اسم المرسل وعنوان بريده الإلكتروني|`Set-OMEConfiguration -Identity "<OMEConfigurationName>" -IntroductionText "<String up to 1024 characters>"` <p> **مثال:** <p> `Set-OMEConfiguration -Identity "Branding Template 1" -IntroductionText "has sent you a secure message."`|
|النص الذي يظهر على الزر "قراءة الرسالة"|`Set-OMEConfiguration -Identity "<OMEConfigurationName>" -ReadButtonText "<String up to 1024 characters>"` <p> **مثال:** <p> `Set-OMEConfiguration -Identity "OME Configuration" -ReadButtonText "Read Secure Message."`|
|النص الذي يظهر أسفل الزر "قراءة الرسالة"|`Set-OMEConfiguration -Identity "<OMEConfigurationName>" -EmailText "<String up to 1024 characters>"` <p> **مثال:** <p> `Set-OMEConfiguration -Identity "OME Configuration" -EmailText "Encrypted message from ContosoPharma secure messaging system."`|
|URL لاارتباط بيان الخصوصية|`Set-OMEConfiguration -Identity "<OMEConfigurationName>" -PrivacyStatementURL "<URL>"` <p> **مثال:** <p> `Set-OMEConfiguration -Identity "Branding Template 1" -PrivacyStatementURL "https://contoso.com/privacystatement.html"`|
|بيان إخلاء المسؤولية في رسالة البريد الإلكتروني التي تحتوي على الرسالة المشفرة|`Set-OMEConfiguration -Identity "<OMEConfigurationName>" -DisclaimerText "<Disclaimer statement. String of up to 1024 characters.>"` <p> **مثال:** <p> `Set-OMEConfiguration -Identity "Branding Template 1" -DisclaimerText "This message is confidential for the use of the addressee only."`|
|النص الذي يظهر في أعلى مدخل عرض البريد المشفر|`Set-OMEConfiguration -Identity "<OMEConfigurationName>" -PortalText "<Text for your portal. String of up to 128 characters.>"` <p> **مثال:** <p> `Set-OMEConfiguration -Identity "OME Configuration" -PortalText "ContosoPharma secure email portal."`|
|لتمكين المصادقة أو تعطيلها باستخدام رمز المرور مرة واحدة لهذا القالب المخصص|`Set-OMEConfiguration -Identity "<OMEConfigurationName>" -OTPEnabled <$true|$false>` <p> **أمثلة:** <br/>لتمكين رموز المرور مرة واحدة لهذا القالب المخصص <p> `Set-OMEConfiguration -Identity "Branding Template 1" -OTPEnabled $true` <p> لتعطيل رموز المرور مرة واحدة لهذا القالب المخصص <p> `Set-OMEConfiguration -Identity "Branding Template 1" -OTPEnabled $false`|
|لتمكين المصادقة أو تعطيلها باستخدام هويات Microsoft أو Google أو Yahoo لهذا القالب المخصص|`Set-OMEConfiguration -Identity "<OMEConfigurationName>" -SocialIdSignIn <$true|$false>` <p> **أمثلة:** <br/>لتمكين المعرف الاجتماعي لهذا القالب المخصص <p> `Set-OMEConfiguration -Identity "Branding Template 1" -SocialIdSignIn $true` <p> لتعطيل المعرف الاجتماعي لهذا القالب المخصص <p> `Set-OMEConfiguration -Identity "Branding Template 1" -SocialIdSignIn $false`|
|

## <a name="create-an-ome-branding-template-advanced-message-encryption"></a>إنشاء قالب العلامة التجارية ل OME (تشفير الرسائل المتقدمة)

إذا كان لديك تشفير الرسائل المتقدم من Office 365، يمكنك إنشاء قوالب مخصصة للعلامة التجارية لمنظمتك باستخدام [الأمر cmdlet New-OMEConfiguration](/powershell/module/exchange/new-omeconfiguration). بعد إنشاء القالب، يمكنك تعديل القالب باستخدام Set-OMEConfiguration cmdlet كما هو موضح في تعديل قالب العلامة التجارية [ل OME](#modify-an-ome-branding-template). يمكنك إنشاء قوالب متعددة.

لإنشاء قالب علامة تجارية مخصص جديد:

1. باستخدام حساب العمل أو المؤسسة الدراسية الذي لديه أذونات المسؤول العام في مؤسستك، ابدأ جلسة عمل Windows PowerShell واتصل Exchange Online. للحصول على الإرشادات، [راجع الاتصال Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

2. استخدم [الأمر cmdlet New-OMEConfiguration](/powershell/module/exchange/new-omeconfiguration) لإنشاء قالب جديد.

   ```powershell
   New-OMEConfiguration -Identity "<OMEConfigurationName>"
   ```

   على سبيل المثال

   ```powershell
   New-OMEConfiguration -Identity "Custom branding template"
   ```

## <a name="return-the-default-branding-template-to-its-original-values"></a>إرجاع قالب العلامة التجارية الافتراضي إلى قيمه الأصلية

لإزالة كل التعديلات من القالب الافتراضي، بما في ذلك تخصيصات العلامة التجارية، وما إلى ذلك، أكمل الخطوات التالية:

1. باستخدام حساب العمل أو المؤسسة الدراسية الذي لديه أذونات المسؤول العام في مؤسستك، ابدأ جلسة عمل Windows PowerShell واتصل Exchange Online. للحصول على الإرشادات، [راجع الاتصال Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

2. استخدم **الأمر cmdlet Set-OMEConfiguration** كما هو موضح في [Set-OMEConfiguration](/powershell/module/exchange/Set-OMEConfiguration). لإزالة التخصيصات التي تحمل علامة تجارية لم مؤسستك من قيم إخلاء المسؤولية وText البريد الإلكتروني و PortalText، قم بتعيين القيمة إلى سلسلة فارغة، `""`. لكل قيم الصور، مثل شعار، قم بتعيين القيمة إلى `"$null"`.

   يصف الجدول التالي خيارات تخصيص التشفير الافتراضية.

   <br>

   ****

   |لإعادة هذه الميزة لتجربة التشفير إلى النص والصورة الافتراضيين|استخدام هذه الأوامر|
   |:-----|:-----|
   |النص الافتراضي الذي يأتي مع رسائل البريد الإلكتروني المشفرة. يظهر النص الافتراضي أعلى الإرشادات الخاصة بعرض الرسائل المشفرة|`Set-OMEConfiguration -Identity "<OMEConfigurationName>" -EmailText "<empty string>"` <p> **مثال:** <p> `Set-OMEConfiguration -Identity "OME Configuration" -EmailText ""`|
   |بيان إخلاء المسؤولية في رسالة البريد الإلكتروني التي تحتوي على الرسالة المشفرة|`Set-OMEConfiguration -Identity "<OMEConfigurationName>" DisclaimerText "<empty string>"` <p> **مثال:** <p> `Set-OMEConfiguration -Identity "OME Configuration" -DisclaimerText ""`|
   |النص الذي يظهر في أعلى مدخل عرض البريد المشفر|`Set-OMEConfiguration -Identity "<OMEConfigurationName>" -PortalText "<empty string>"` <p> **مثال للعودة إلى الوضع الافتراضي:** <p> `Set-OMEConfiguration -Identity "OME Configuration" -PortalText ""`|
   |شعار|`Set-OMEConfiguration -Identity "<OMEConfigurationName>" -Image <"$null">` <p> **مثال للعودة إلى الوضع الافتراضي:** <p> `Set-OMEConfiguration -Identity "OME configuration" -Image $null`|
   |لون الخلفية|`Set-OMEConfiguration -Identity "<OMEConfigurationName>" -BackgroundColor "$null">` <p> **مثال للعودة إلى الوضع الافتراضي:** <p> `Set-OMEConfiguration -Identity "OME configuration" -BackgroundColor $null`|
   |

## <a name="remove-a-custom-branding-template-advanced-message-encryption"></a>إزالة قالب علامة تجارية مخصص (تشفير الرسائل المتقدمة)

يمكنك فقط إزالة قوالب العلامة التجارية التي قمت بإخراجها أو حذفها. لا يمكنك إزالة قالب العلامة التجارية الافتراضي.

لإزالة قالب علامة تجارية مخصص:

1. باستخدام حساب العمل أو المؤسسة الدراسية الذي لديه أذونات المسؤول العام في مؤسستك، ابدأ جلسة عمل Windows PowerShell واتصل Exchange Online. للحصول على الإرشادات، [راجع الاتصال Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

2. استخدم **cmdlet Remove-OMEConfiguration** كما يلي:

   ```powershell
   Remove-OMEConfiguration -Identity ""<OMEConfigurationName>"
   ```

   على سبيل المثال

   ```powershell
   Remove-OMEConfiguration -Identity "Branding template 1"
   ```

   لمزيد من المعلومات، راجع [Remove-OMEConfiguration](/powershell/module/exchange/remove-omeconfiguration).

## <a name="create-an-exchange-mail-flow-rule-that-applies-your-custom-branding-to-encrypted-emails"></a>إنشاء قاعدة Exchange البريد الإلكتروني التي تطبق علامتك التجارية المخصصة على رسائل البريد الإلكتروني المشفرة

> [!IMPORTANT]
> يمكن للتطبيقات التي تقوم بفحص البريد وتعديله أن تمنع تطبيق علامة OME التجارية بشكل صحيح.

بعد تعديل القالب الافتراضي أو إنشاء قوالب جديدة للعلامة التجارية، يمكنك إنشاء Exchange تدفق البريد لتطبيق العلامة التجارية المخصصة استنادا إلى شروط معينة. ستعرض هذه القاعدة العلامة التجارية المخصصة في السيناريوهات التالية:

- إذا قام المستخدم بتشفير البريد الإلكتروني يدويا باستخدام Outlook أو Outlook على ويب، Outlook Web App
- إذا تم تشفير البريد الإلكتروني تلقائيا بواسطة قاعدة تدفق Exchange البريد الإلكتروني أو نهج منع فقدان البيانات

للحصول على معلومات حول كيفية إنشاء قاعدة تدفق Exchange البريد الإلكتروني التي تطبق التشفير، راجع تعريف قواعد تدفق البريد لتشفير رسائل البريد الإلكتروني في [Office 365.](define-mail-flow-rules-to-encrypt-email.md)

1. في مستعرض ويب، باستخدام حساب عمل أو مدرسة تم منحه أذونات المسؤول العام، سجل الدخول [إلى](https://support.office.com/article/b9582171-fd1f-4284-9846-bdd72bb28426#ID0EAABAAA=Web_browser) Office 365.

2. اختر لوحة **المسؤول** .

3. في <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">مركز مسؤولي Microsoft 365،</a> اختر **مراكز الإدارة Exchange** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">**.**</a>

4. في EAC، انتقل إلى **قواعد تدفق** \> **البريد** وحدد **أيقونة جديد** ![جديد.](../media/457cd93f-22c2-4571-9f83-1b129bcfb58e.gif) \>**إنشاء قاعدة جديدة**. لمزيد من المعلومات حول استخدام EAC، راجع Exchange [مركز الإدارة في Exchange Online](/exchange/exchange-admin-center).

5. في **الاسم**، اكتب اسما للقاعدة، مثل العلامة التجارية لقسم المبيعات.

6. في **تطبيق هذه القاعدة إذا**، حدد الشرط يقع  المرسل داخل المؤسسة والشروط الأخرى التي تريدها من قائمة الشروط المتوفرة. على سبيل المثال، قد ترغب في تطبيق قالب علامة تجارية معين على:

   - جميع رسائل البريد الإلكتروني المشفرة المرسلة من أعضاء قسم الشؤون المالية
   - رسائل البريد الإلكتروني المشفرة المرسلة باستخدام كلمة أساسية معينة مثل "خارجي" أو "شريك"
   - رسائل البريد الإلكتروني المشفرة المرسلة إلى مجال معين

7. من **قم بما يلي**، حدد **تعديل أمان الرسالة** \> **تطبيق العلامة التجارية المخصصة على رسائل OME**. بعد ذلك، من المنسدل، حدد قالب علامة تجارية.

8. (اختياري) يمكنك تكوين قاعدة تدفق البريد لتطبيق التشفير والعلامة التجارية المخصصة. من **قم بما يلي**، حدد **تعديل أمان الرسالة**، ثم اختر تطبيق تشفير الرسائل من Office 365 **وحماية الحقوق**. حدد قالب RMS من القائمة، واختر **حفظ**، ثم اختر **موافق**.

   تتضمن قائمة القوالب القوالب والخيارات الافتراضية وأي قوالب مخصصة تقوم بإنشاءها. إذا كانت القائمة فارغة، فتأكد من إعداد تشفير الرسائل من Office 365 باستخدام الإمكانات الجديدة. للحصول على الإرشادات، راجع [إعداد قدرات تشفير الرسائل من Office 365 الجديدة](set-up-new-message-encryption-capabilities.md). للحصول على معلومات حول القوالب الافتراضية، راجع تكوين القوالب وإدارتها [ل Azure Information Protection](/information-protection/deploy-use/configure-policy-templates). للحصول على معلومات حول الخيار **عدم إعادة توجيه** ، راجع [الخيار عدم إعادة توجيه رسائل البريد الإلكتروني](/information-protection/deploy-use/configure-usage-rights#do-not-forward-option-for-emails). للحصول على معلومات حول **خيار التشفير فقط** ، راجع [الخيار تشفير رسائل البريد الإلكتروني فقط](/information-protection/deploy-use/configure-usage-rights#encrypt-only-option-for-emails).

   اختر **إضافة إجراء** إذا كنت تريد تحديد إجراء آخر.

## <a name="background-color-reference"></a>مرجع لون الخلفية

تكون أسماء الألوان التي يمكنك استخدامها للون الخلفية محدودة. بدلا من اسم اللون، يمكنك استخدام قيمة التعليمات البرمجية (`#RRGGBB`). يمكنك استخدام قيمة التعليمات البرمجية الهمكسية التي تتوافق مع اسم لون، أو يمكنك استخدام قيمة رمز ستيكسي مخصصة. تأكد من إحاطة قيمة التعليمات البرمجية الهمكسية بين علامات اقتباس (على سبيل المثال، `"#f0f8ff"`).

يتم وصف أسماء ألوان الخلفية المتوفرة وقيم التعليمات البرمجية المطابقة لها في الجدول التالي.

|**اسم اللون**|**رمز اللون**|
|---|---|
|`aliceblue`|#f0f8ff|
|`antiquewhite`|#faebd7|
|`aqua`|#00ffff|
|`aquamarine`|#7fffd4|
|`azure`|#f0ffff|
|`beige`|#f5f5dc|
|`bisque`|#ffe4c4|
|`black`|#000000|
|`blanchedalmond`|#ffebcd|
|`blue`|#0000ff|
|`blueviolet`|#8a2be2|
|`brown`|#a52a2a|
|`burlywood`|#deb887|
|`cadetblue`|#5f9ea0|
|`chartreuse`|#7fff00|
|`chocolate`|#d2691e|
|`coral`|#ff7f50|
|`cornflowerblue`|#6495ed|
|`cornsilk`|#fff8dc|
|`crimson`|#dc143c|
|`cyan`|#00ffff|
|`darkblue`|#00008b|
|`darkcyan`|#008b8b|
|`darkgoldenrod`|#b8860b|
|`darkgray`|#a9a9a9|
|`darkgreen`|#006400|
|`darkkhaki`|#bdb76b|
|`darkmagenta`|#8b008b|
|`darkolivegreen`|#556b2f|
|`darkorange`|#ff8c00|
|`darkorchid`|#9932cc|
|`darkred`|#8b0000|
|`darksalmon`|#e9967a|
|`darkseagreen`|#8fbc8f|
|`darkslateblue`|#483d8b|
|`darkslategray`|#2f4f4f|
|`darkturquoise`|#00ced1|
|`darkviolet`|#9400d3|
|`deeppink`|#ff1493|
|`deepskyblue`|#00bfff|
|`dimgray`|#696969|
|`dodgerblue`|#1e90ff|
|`firebrick`|#b22222|
|`floralwhite`|#fffaf0|
|`forestgreen`|#228b22|
|`fuchsia`|#ff00ff|
|`gainsboro`|#dcdcdc|
|`ghostwhite`|#f8f8ff|
|`gold`|#ffd700|
|`goldenrod`|#daa520|
|`gray`|#808080|
|`green`|#008000|
|`greenyellow`|#adff2f|
|`honeydew`|#f0fff0|
|`hotpink`|#ff69b4|
|`indianred`|#cd5c5c|
|`indigo`|#4b0082|
|`ivory`|#fffff0|
|`khaki`|#f0e68c|
|`lavender`|#e6e6fa|
|`lavenderblush`|#fff0f5|
|`lawngreen`|#7cfc00|
|`lemonchiffon`|#fffacd|
|`lightblue`|#add8e6|
|`lightcoral`|#f08080|
|`lightcyan`|#e0ffff|
|`lightgoldenrodyellow`|#fafad2|
|`lightgray`|#d3d3d3|
|`lightgrey`|#d3d3d3|
|`lightgreen`|#90ee90|
|`lightpink`|#ffb6c1|
|`lightsalmon`|#ffa07a|
|`lightseagreen`|#20b2aa|
|`lightskyblue`|#87cefa|
|`lightslategray`|#778899|
|`lightsteelblue`|#b0c4de|
|`lightyellow`|#ffffe0|
|`lime`|#00ff00|
|`limegreen`|#32cd32|
|`linen`|#faf0e6|
|`magenta`|#ff00ff|
|`maroon`|#800000|
|`mediumaquamarine`|#66cdaa|
|`mediumblue`|#0000cd|
|`mediumorchid`|#ba55d3|
|`mediumpurple`|#9370db|
|`mediumseagreen`|#3cb371|
|`mediumslateblue`|#7b68ee|
|`mediumspringgreen`|#00fa9a|
|`mediumturquoise`|#48d1cc|
|`mediumvioletred`|#c71585|
|`midnightblue`|#191970|
|`mintcream`|#f5fffa|
|`mistyrose`|#ffe4e1|
|`moccasin`|#ffe4b5|
|`navajowhite`|#ffdead|
|`navy`|#000080|
|`oldlace`|#fdf5e6|
|`olive`|#808000|
|`olivedrab`|#6b8e23|
|`orange`|#ffa500|
|`orangered`|#ff4500|
|`orchid`|#da70d6|
|`palegoldenrod`|#eee8aa|
|`palegreen`|#98fb98|
|`paleturquoise`|#afeeee|
|`palevioletred`|#db7093|
|`papayawhip`|#ffefd5|
|`peachpuff`|#ffdab9|
|`peru`|#cd853f|
|`pink`|#ffc0cb|
|`plum`|#dda0dd|
|`powderblue`|#b0e0e6|
|`purple`|#800080|
|`red`|#ff0000|
|`rosybrown`|#bc8f8f|
|`royalblue`|#4169e1|
|`saddlebrown`|#8b4513|
|`salmon`|#fa8072|
|`sandybrown`|#f4a460|
|`seagreen`|#00ff00|
|`seashell`|#fff5ee|
|`sienna`|#a0522d|
|`silver`|#c0c0c0|
|`skyblue`|#87ceeb|
|`slateblue`|#6a5acd|
|`slategray`|#708090|
|`snow`|#fffafa|
|`springgreen`|#00ff7f|
|`steelblue`|#4682b4|
|`tan`|#d2b48c|
|`teal`|#008080|
|`thistle`|#d8bfd8|
|`tomato`|#ff6347|
|`turquoise`|#40e0d0|
|`violet`|#ee82ee|
|`wheat`|#f5deb3|
|`white`|#ffffff|
|`whitesmoke`|#f5f5f5|
|`yellow`|#ffff00|
|`yellowgreen`|#9acd32|
