---
title: المعلومات القديمة لتشفير رسائل Office 365
f1.keywords:
- NOCSH
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 05/22/2020
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: ''
search.appverid:
- MET150
ms.assetid: 5986b9e1-c824-4f8f-9b7d-a2b0ae2a7fe9
ms.collection:
- M365-security-compliance
ms.custom:
- seo-marvel-apr2020
- admindeeplinkMAC
- admindeeplinkEXCHANGE
description: فهم كيفية نقل الملفات القديمة إلى Office 365 تشفير الرسائل (OME) لمؤسستك.
ms.openlocfilehash: 2d994e2c521f11a70c6946e2f1a9a3a1a5766ba3
ms.sourcegitcommit: 133bf9097785309da45df6f374a712a48b33f8e9
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 06/10/2022
ms.locfileid: "66014895"
---
# <a name="legacy-information-for-office-365-message-encryption"></a>المعلومات القديمة لتشفير رسائل Office 365

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

إذا لم تكن قد نقلت مؤسستك بعد إلى Microsoft Purview Message Encryption، ولكنك قمت بالفعل بنشر OME، فإن المعلومات الواردة في هذه المقالة تنطبق على مؤسستك. توصي Microsoft بوضع خطة للانتقال إلى Microsoft Purview Message Encryption بمجرد أن يكون ذلك معقولا لمؤسستك. للحصول على الإرشادات، راجع [إعداد تشفير رسائل "Microsoft Purview](set-up-new-message-encryption-capabilities.md)". إذا كنت تريد معرفة المزيد حول كيفية تشفير الرسالة الجديدة أولا، فراجع [تشفير الرسالة](ome.md). تشير بقية هذه المقالة إلى سلوك OME قبل إصدار تشفير الرسائل من Microsoft Purview.

باستخدام Office 365 تشفير الرسائل، يمكن لمؤسستك إرسال رسائل البريد الإلكتروني المشفرة وتلقيها بين أشخاص داخل مؤسستك وخارجها. Office 365 يعمل تشفير الرسائل مع Outlook.com وYahoo وGmail وخدمات البريد الإلكتروني الأخرى. يساعد تشفير رسالة البريد الإلكتروني على التأكد من أن المستلمين المقصودين فقط يمكنهم عرض محتوى الرسالة.

فيما يلي بعض الأمثلة:

- يرسل موظف بنكي كشوف بطاقة ائتمان إلى العملاء
- يقدم ممثل شركة التأمين تفاصيل النهج للعملاء
- يطلب وسيط رهن معلومات مالية من عميل للحصول على طلب قرض
- يرسل موفر الرعاية الصحية معلومات الرعاية الصحية إلى المرضى
- يرسل أحد الوكلاء معلومات سرية إلى عميل أو إلى وكيل آخر

## <a name="how-office-365-message-encryption-works-without-the-new-capabilities"></a>كيفية عمل تشفير الرسائل Office 365 بدون القدرات الجديدة

Office 365 تشفير الرسائل هي خدمة عبر الإنترنت تم إنشاؤها على Microsoft Azure Rights Management (Azure RMS). باستخدام Azure RMS، يمكن للمسؤولين تحديد قواعد تدفق البريد لتحديد شروط التشفير. على سبيل المثال، قد تتطلب القاعدة تشفير كافة الرسائل الموجهة إلى مستلم معين.

عندما يرسل شخص ما رسالة بريد إلكتروني في Exchange Online تتطابق مع قاعدة تشفير، يتم إرسال الرسالة مع مرفق HTML. يفتح المستلم مرفق HTML ويتبع الإرشادات لعرض الرسالة المشفرة على مدخل تشفير الرسائل Office 365. يمكن للمستلم اختيار عرض الرسالة عن طريق تسجيل الدخول باستخدام حساب Microsoft أو العمل أو المؤسسة التعليمية المقترنة Office 365، أو باستخدام رمز مرور لمرة واحدة. يساعد كلا الخيارين على ضمان أن المستلم المقصود فقط يمكنه عرض الرسالة المشفرة. هذه العملية مختلفة جدا لتشفير رسالة "Microsoft Purview".

يلخص الرسم التخطيطي التالي مرور رسالة بريد إلكتروني من خلال عملية التشفير وفك التشفير.

![رسم تخطيطي يوضح مسار رسالة بريد إلكتروني مشفرة.](../media/O365-Office365MessageEncryption-Concept.png)

لمزيد من المعلومات، راجع [معلومات الخدمة لتشفير الرسائل Office 365 القديم قبل إصدار تشفير الرسائل من Microsoft Purview](legacy-information-for-message-encryption.md#LegacyServiceInfo).

## <a name="defining-mail-flow-rules-for-office-365-message-encryption-that-dont-use-microsoft-purview-message-encryption"></a>تعريف قواعد تدفق البريد لتشفير الرسائل Office 365 التي لا تستخدم تشفير رسائل Microsoft Purview

لتمكين تشفير الرسائل Office 365 بدون القدرات الجديدة، يحدد المسؤولون Exchange Online والمسؤولين Exchange Online Protection قواعد تدفق البريد Exchange. تحدد هذه القواعد الشروط التي يجب تشفير رسائل البريد الإلكتروني فيها، بالإضافة إلى شروط إزالة تشفير الرسائل. عند تعيين إجراء تشفير لقاعدة، تنفذ الخدمة الإجراء على أي رسائل تطابق شروط القاعدة قبل إرسال الرسائل.

قواعد تدفق البريد مرنة، مما يتيح لك دمج الشروط حتى تتمكن من تلبية متطلبات أمان معينة في قاعدة واحدة. على سبيل المثال، يمكنك إنشاء قاعدة لتشفير كافة الرسائل التي تحتوي على كلمات أساسية محددة ويتم توجيهها إلى مستلمين خارجيين. Office 365 تشفير الرسائل أيضا بتشفير الردود من مستلمي البريد الإلكتروني المشفر، ويمكنك إنشاء قاعدة تقوم بفك تشفير هذه الردود كوسيلة ملائمة لمستخدمي البريد الإلكتروني. وبهذه الطريقة، لن يضطر المستخدمون في مؤسستك إلى تسجيل الدخول إلى مدخل التشفير لعرض الردود.

لمزيد من المعلومات حول كيفية إنشاء قواعد تدفق البريد Exchange، راجع [تعريف القواعد لتشفير الرسائل Office 365](define-mail-flow-rules-to-encrypt-email.md).

### <a name="use-the-eac-to-create-a-mail-flow-rule-for-encrypting-email-messages-without-microsoft-purview-message-encryption"></a>استخدام EAC لإنشاء قاعدة تدفق بريد لتشفير رسائل البريد الإلكتروني دون تشفير رسائل Microsoft Purview

1. في مستعرض ويب، باستخدام حساب العمل أو المؤسسة التعليمية الذي تم منحه أذونات المسؤول العام، [سجل الدخول إلى Office 365](https://support.office.com/article/b9582171-fd1f-4284-9846-bdd72bb28426#ID0EAABAAA=Web_browser).

2. اختر لوحة **المسؤول** .

3. في مركز مسؤولي Microsoft 365، اختر **مراكز** \> الإدارة <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">**Exchange**</a>.

4. في EAC، انتقل إلى **"قواعد** **تدفق** \> البريد" وحدد أيقونة **"جديد**![".](../media/457cd93f-22c2-4571-9f83-1b129bcfb58e.gif) \>**إنشاء قاعدة جديدة**. لمزيد من المعلومات حول استخدام EAC، راجع [مركز إدارة Exchange في Exchange Online](/exchange/exchange-admin-center).

5. في **الاسم**، اكتب اسما للقاعدة، مثل تشفير البريد DrToniRamos@hotmail.com.

6. في **تطبيق هذه القاعدة إذا** حدد شرطا، وأدخل قيمة إذا لزم الأمر. على سبيل المثال، لتشفير الرسائل التي ستنتقل إلى DrToniRamos@hotmail.com:

   1. في **تطبيق هذه القاعدة إذا**، حدد **المستلم.**

   2. حدد اسما موجودا من قائمة جهات الاتصال أو اكتب عنوان بريد إلكتروني جديدا في خانة **الاختيار "أسماء** ".

      - لتحديد اسم موجود، حدده من القائمة ثم انقر فوق **"موافق**".

      - لإدخال اسم جديد، اكتب عنوان بريد إلكتروني في خانة **الاختيار "أسماء** " ثم حدد **"التحقق من الأسماء** \> **" "موافق**".

7. لإضافة المزيد من الشروط، اختر **المزيد من الخيارات** ثم حدد **إضافة شرط** وحدد من القائمة.

   على سبيل المثال، لتطبيق القاعدة فقط إذا كان المستلم خارج مؤسستك، حدد **إضافة شرط** ثم حدد **المستلم خارجي/داخلي** \> **خارج المؤسسة** \> **موافق**.

8. لتمكين التشفير دون استخدام قدرات OME الجديدة، في **القيام بما يلي**، حدد **تعديل أمان** \> الرسالة **تطبيق الإصدار السابق من OME**، ثم اختر **"حفظ**".

   إذا تلقيت رسالة خطأ تفيد بعدم تمكين ترخيص IRM، فأنت لا تستخدم OME القديم.

9. (اختياري) اختر **إضافة إجراء** لتحديد إجراء آخر.

### <a name="use-exchange-online-powershell-to-create-a-mail-flow-rule-for-encrypting-email-messages-without-the-new-ome-capabilities"></a>استخدام Exchange Online PowerShell لإنشاء قاعدة تدفق بريد لتشفير رسائل البريد الإلكتروني دون إمكانات OME الجديدة

1. الاتصال إلى Exchange Online PowerShell. لمزيد من المعلومات، راجع [الاتصال Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

2. إنشاء قاعدة باستخدام **New-TransportRule** cmdlet وتعيين المعلمة _ApplyOME_ إلى `$true`.

   يتطلب هذا المثال تشفير كافة رسائل البريد الإلكتروني المرسلة إلى DrToniRamos@hotmail.com.

   ```powershell
   New-TransportRule -Name "Encrypt rule for Dr Toni Ramos" -SentTo "DrToniRamos@hotmail.com" -SentToScope "NotinOrganization" -ApplyOME $true
   ```

   حيث

   - الاسم الفريد للقاعدة الجديدة هو "تشفير القاعدة للدكتور توني Ramos".
   - تحدد المعلمة _SentTo_ مستلمي الرسالة (المعرف بالاسم وعنوان البريد الإلكتروني والاسم المميز وما إلى ذلك). في هذا المثال، يتم تعريف المستلم بواسطة عنوان البريد الإلكتروني "DrToniRamos@hotmail.com".
   - تحدد المعلمة _SentToScope_ موقع مستلمي الرسالة. في هذا المثال، تكون علبة بريد المستلم في hotmail وليست جزءا من المؤسسة، لذلك يتم استخدام القيمة `NotInOrganization` .

   للحصول على معلومات مفصلة حول بناء الجملة والمعلمة، راجع [New-TransportRule](/powershell/module/exchange/New-TransportRule).

### <a name="remove-encryption-from-email-replies-encrypted-without-microsoft-purview-message-encryption"></a>إزالة التشفير من ردود البريد الإلكتروني المشفرة دون تشفير رسالة "Microsoft Purview"

عندما يرسل مستخدمو البريد الإلكتروني رسائل مشفرة، يمكن لمستلمي هذه الرسائل الرد بردود مشفرة. يمكنك إنشاء قواعد تدفق البريد لإزالة التشفير تلقائيا من الردود حتى لا يضطر مستخدمو البريد الإلكتروني في مؤسستك إلى تسجيل الدخول إلى مدخل التشفير لعرضها. يمكنك استخدام EAC أو Exchange Online PowerShell cmdlets لتعريف هذه القواعد. يمكنك فك تشفير الرسائل المرسلة من داخل مؤسستك أو الرسائل التي تكون ردودا على الرسائل المرسلة من داخل مؤسستك. لا يمكنك فك تشفير الرسائل المشفرة التي تنشأ من خارج مؤسستك.

#### <a name="use-the-eac-to-create-a-rule-for-removing-encryption-from-email-replies-encrypted-without-microsoft-purview-message-encryption"></a>استخدام EAC لإنشاء قاعدة لإزالة التشفير من ردود البريد الإلكتروني المشفرة دون تشفير الرسائل من Microsoft Purview

1. في مستعرض ويب، باستخدام حساب العمل أو المؤسسة التعليمية الذي تم منحه أذونات المسؤول، [سجل الدخول إلى Office 365](https://support.office.com/article/b9582171-fd1f-4284-9846-bdd72bb28426#ID0EAABAAA=Web_browser).

2. اختر لوحة **المسؤول** .

3. في مركز مسؤولي Microsoft 365، اختر **مراكز** \> الإدارة <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">**Exchange**</a>.

4. في EAC، انتقل إلى **"قواعد** **تدفق** \> البريد" وحدد أيقونة **"جديد**![".](../media/457cd93f-22c2-4571-9f83-1b129bcfb58e.gif) \>**إنشاء قاعدة جديدة**. لمزيد من المعلومات حول استخدام EAC، راجع [مركز إدارة Exchange في Exchange Online](/exchange/exchange-admin-center).

5. في **الاسم**، اكتب اسما للقاعدة، مثل إزالة التشفير من البريد الوارد.

6. في **تطبيق هذه القاعدة إذا** حدد الشروط التي يجب إزالة التشفير فيها من الرسائل، مثل **أن المستلم موجود** \> **داخل المؤسسة**.

7. في **القيام بما يلي**، حدد **تعديل أمان** \> الرسالة **إزالة الإصدار السابق من OME**.

8. حدد **حفظ**.

#### <a name="use-exchange-online-powershell-to-create-a-rule-to-remove-encryption-from-email-replies-encrypted-without-the-new-ome-capabilities"></a>استخدم Exchange Online PowerShell لإنشاء قاعدة لإزالة التشفير من ردود البريد الإلكتروني المشفرة دون إمكانات OME الجديدة

1. الاتصال إلى Exchange Online PowerShell. لمزيد من المعلومات، راجع [الاتصال Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

2. إنشاء قاعدة باستخدام **New-TransportRule** cmdlet وتعيين المعلمة _RemoveOME_ إلى `$true`.

   يزيل هذا المثال التشفير من كل البريد المرسل إلى المستلمين في المؤسسة.

   ```powershell
   New-TransportRule -Name "Remove encryption from incoming mail" -SentToScope "InOrganization" -RemoveOME $true
   ```

   حيث

   - الاسم الفريد للقاعدة الجديدة هو "إزالة التشفير من البريد الوارد".
   - تحدد المعلمة _SentToScope_ موقع مستلمي الرسالة. في هذا المثال، يتم استخدام قيمة القيمة `InOrganization` ، والتي تشير إلى أحد الإجراءات التالية:
     - إن المستلم عبارة عن علبة بريد أو مستخدم بريد أو مجموعة أو مجلد عام ممكن للبريد في مؤسستك.
     - عنوان البريد الإلكتروني للمستلم موجود في مجال مقبول تم تكوينه كمجال موثوق به أو مجال الإرسال الداخلي في _مؤسستك، وتم_ إرسال الرسالة أو تلقيها عبر اتصال مصادق عليه.

للحصول على معلومات مفصلة حول بناء الجملة والمعلمة، راجع [New-TransportRule](/powershell/module/exchange/New-TransportRule).

## <a name="sending-viewing-and-replying-to-messages-encrypted-without-the-new-capabilities"></a>إرسال الرسائل المشفرة وعرضها والرد عليها دون الإمكانات الجديدة

باستخدام Office 365 تشفير الرسائل، يتم تشفير رسائل البريد الإلكتروني تلقائيا، استنادا إلى القواعد المعرفة من قبل المسؤول. يصل بريد إلكتروني يحمل رسالة مشفرة إلى علبة الوارد الخاصة بالمستلم مع ملف HTML مرفق.

يتبع المستلمون الإرشادات الواردة في الرسالة لفتح المرفق والمصادقة باستخدام حساب Microsoft أو العمل أو المؤسسة التعليمية المقترنة Office 365. إذا لم يكن لدى المستلمين أي حساب، فسيتم توجيههم لإنشاء حساب Microsoft يسمح لهم بتسجيل الدخول لعرض الرسالة المشفرة. بدلا من ذلك، يمكن للمستلمين اختيار الحصول على رمز مرور لمرة واحدة لعرض الرسالة. بعد تسجيل الدخول أو استخدام رمز تمرير لمرة واحدة، يمكن للمستلمين عرض الرسالة التي تم فك تشفيرها وإرسال رد مشفر.

## <a name="customize-encrypted-messages-with-office-365-message-encryption"></a>تخصيص الرسائل المشفرة باستخدام تشفير الرسائل Office 365

بصفتك مسؤول Exchange Online ومسؤول Exchange Online Protection، يمكنك تخصيص الرسائل المشفرة. على سبيل المثال، يمكنك إضافة العلامة التجارية وشعار شركتك، وتحديد مقدمة، وإضافة نص إخلاء المسؤولية في الرسائل المشفرة وفي المدخل حيث يعرض المستلمون الرسائل المشفرة. باستخدام Exchange Online PowerShell cmdlets، يمكنك تخصيص الجوانب التالية من تجربة العرض لمستلمي رسائل البريد الإلكتروني المشفرة:

- نص تمهيدي للبريد الإلكتروني الذي يحتوي على الرسالة المشفرة
- نص إخلاء المسؤولية للبريد الإلكتروني الذي يحتوي على الرسالة المشفرة
- نص المدخل الذي سيظهر في مدخل عرض الرسائل
- الشعار الذي سيظهر في رسالة البريد الإلكتروني وعرض المدخل

يمكنك أيضا العودة إلى الشكل والأداء الافتراضيين في أي وقت.

يعرض المثال التالي شعارا مخصصا لشركة ContosoPharma في مرفق البريد الإلكتروني:

> [!div class="mx-imgBorder"]
> ![نموذج لصفحة الرسالة المشفرة للعرض.](../media/TA-OME-3attachment2.jpg)

### <a name="to-customize-encryption-email-messages-and-the-encryption-portal-with-your-organizations-brand"></a>لتخصيص رسائل البريد الإلكتروني للتشفير ومدخل التشفير باستخدام العلامة التجارية لمؤسستك

1. [الاتصال إلى Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

2. استخدم Set-OMEConfiguration cmdlet كما هو موضح هنا: [Set-OMEConfiguration](/powershell/module/exchange/set-omeconfiguration) أو استخدم الجدول التالي للحصول على إرشادات.

   **خيارات تخصيص التشفير**

   |لتخصيص هذه الميزة من تجربة التشفير|استخدم أوامر PowerShell Exchange Online هذه|
   |---|---|
   |النص الافتراضي الذي يصاحب رسائل البريد الإلكتروني المشفرة <p> يظهر النص الافتراضي فوق إرشادات عرض الرسائل المشفرة|`Set-OMEConfiguration -Identity <OMEConfigurationIdParameter> -EmailText "<string of up to 1024 characters>"` <p> **على سبيل المثال:** `Set-OMEConfiguration -Identity "OME Configuration" -EmailText "Encrypted message from ContosoPharma secure messaging system"`|
   |بيان إخلاء المسؤولية في البريد الإلكتروني الذي يحتوي على الرسالة المشفرة|`Set-OMEConfiguration -Identity <OMEConfigurationIdParameter> DisclaimerText "<your disclaimer statement, string of up to 1024 characters>"` <p> **على سبيل المثال:** `Set-OMEConfiguration -Identity "OME Configuration" -DisclaimerText "This message is confidential for the use of the addressee only"`|
   |النص الذي يظهر في أعلى مدخل عرض البريد المشفر|`Set-OMEConfiguration -Identity <OMEConfigurationIdParameter> -PortalText "<text for your portal, string of up to 128 characters>"` <p> **على سبيل المثال:** `Set-OMEConfiguration -Identity "OME Configuration" -PortalText "ContosoPharma secure email portal"`|
   |شعار|`Set-OMEConfiguration -Identity <OMEConfigurationIdParameter> -Image <Byte[]>` <p> **المثال:** `Set-OMEConfiguration -Identity "OME configuration" -Image ([System.IO.File]::ReadAllBytes('C:\Temp\contosologo.png'))` <p> تنسيقات الملفات المعتمدة: .png أو .jpg أو .bmp أو tiff. <p> الحجم الأمثل لملف الشعار: أقل من 40 كيلوبايت <p> الحجم الأمثل لصورة الشعار: 170x70 بكسل|

### <a name="to-remove-brand-customizations-from-encryption-email-messages-and-the-encryption-portal"></a>لإزالة تخصيصات العلامة التجارية من رسائل البريد الإلكتروني للتشفير ومدخل التشفير

1. [الاتصال إلى Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

2. استخدم Set-OMEConfiguration cmdlet كما هو موضح هنا: [Set-OMEConfiguration](/powershell/module/exchange/set-omeconfiguration). لإزالة التخصيصات ذات العلامة التجارية لمؤسستك من قيم إخلاء المسؤولية و EmailText و PortalText، قم بتعيين القيمة إلى سلسلة فارغة. `""` بالنسبة لكافة قيم الصور، مثل الشعار، قم بتعيين القيمة إلى `"$null"`.

   **خيارات تخصيص التشفير**

   |لإعادة هذه الميزة من تجربة التشفير مرة أخرى إلى النص الافتراضي والصورة|استخدم أوامر PowerShell Exchange Online هذه|
   |---|---|
   |النص الافتراضي الذي يصاحب رسائل البريد الإلكتروني المشفرة <p> يظهر النص الافتراضي فوق إرشادات عرض الرسائل المشفرة|`Set-OMEConfiguration -Identity <OMEConfigurationIdParameter> -EmailText "<empty string>"` <p> **على سبيل المثال:** `Set-OMEConfiguration -Identity "OME Configuration" -EmailText ""`|
   |بيان إخلاء المسؤولية في البريد الإلكتروني الذي يحتوي على الرسالة المشفرة <p> |`Set-OMEConfiguration -Identity <OMEConfigurationIdParameter> DisclaimerText "<empty string>"` <p> **المثال:** `Set-OMEConfiguration -Identity "OME Configuration" -DisclaimerText ""`|
   |النص الذي يظهر في أعلى مدخل عرض البريد المشفر|`Set-OMEConfiguration -Identity <OMEConfigurationIdParameter> -PortalText "<empty string>"` <p> **مثال على العودة إلى الوضع الافتراضي:** `Set-OMEConfiguration -Identity "OME Configuration" -PortalText ""`|
   |شعار|`Set-OMEConfiguration -Identity <OMEConfigurationIdParameter> -Image <"$null">` <p> **مثال على العودة إلى الوضع الافتراضي:** `Set-OMEConfiguration -Identity "OME configuration" -Image $null`|

## <a name="service-information-for-legacy-office-365-message-encryption-prior-to-the-release-of-the-new-ome-capabilities"></a>معلومات الخدمة لتشفير الرسائل Office 365 القديم قبل إصدار قدرات OME الجديدة
<a name="LegacyServiceInfo"> </a>

يوفر الجدول التالي تفاصيل تقنية لخدمة تشفير الرسائل Office 365 قبل إصدار تشفير الرسائل من Microsoft Purview.

|تفاصيل الخدمة|الوصف|
|---|---|
|متطلبات جهاز العميل|يمكن عرض الرسائل المشفرة على أي جهاز عميل، طالما يمكن فتح مرفق HTML في مستعرض حديث يدعم "نشر النموذج".|
|خوارزمية التشفير وتوافق معايير معالجة المعلومات الفيدرالية (FIPS)|Office 365 يستخدم تشفير الرسائل مفاتيح التشفير نفسها مثل Windows Rights Management معلومات Azure (IRM) ويدعم وضع التشفير 2 (مفتاح 2K لمفتاح RSA و256 بت لأنظمة SHA-1). لمزيد من المعلومات حول أوضاع تشفير IRM الأساسية، راجع [أوضاع تشفير AD RMS](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/hh867439(v=ws.10)).|
|أنواع الرسائل المعتمدة|Office 365 تشفير الرسائل معتمد فقط للعناصر التي تحتوي على معرف فئة رسالة من **IPM. ملاحظة**. لمزيد من المعلومات، راجع [أنواع العناصر وفئات الرسائل](/office/vba/outlook/Concepts/Forms/item-types-and-message-classes).|
|حدود حجم الرسالة|Office 365 يمكن لتشفير الرسائل تشفير الرسائل التي يصل حجمها إلى 25 ميغابايت. لمزيد من التفاصيل حول حدود حجم الرسالة، راجع [Exchange Online حدود](/office365/servicedescriptions/exchange-online-service-description/exchange-online-limits).|
|نهج استبقاء البريد الإلكتروني Exchange Online|لا يقوم Exchange Online بتخزين الرسائل المشفرة.|
|دعم اللغة لتشفير الرسائل Office 365|يدعم تشفير Office 365 الرسائل اللغات Microsoft 365، كما يلي: <p> يتم ترجمة رسائل البريد الإلكتروني الواردة وملفات HTML المرفقة استنادا إلى إعدادات لغة المرسل. <p> يتم ترجمة مدخل العرض استنادا إلى إعدادات المستعرض للمستلم. <p> النص الأساسي (المحتوى) للرسالة المشفرة غير مترجم.|
|معلومات الخصوصية لمدخل OME وتطبيق عارض OME|يوفر [بيان خصوصية مدخل تشفير Office 365 المراسلة](https://privacy.microsoft.com/privacystatement) معلومات مفصلة حول ما تفعله Microsoft ولا تفعله بمعلوماتك الخاصة.|

## <a name="frequently-asked-questions-about-legacy-ome"></a>الأسئلة المتداولة حول OME القديم
<a name="LegacyServiceInfo"> </a>

هل لديك أسئلة حول تشفير الرسائل Office 365؟ فيما يلي بعض الإجابات. إذا لم تتمكن من العثور على ما تحتاجه، فتحقق من [منتديات مجتمع Microsoft التقني للحصول على Office 365](https://techcommunity.microsoft.com/t5/Office-365/ct-p/Office365).

 **س. يرسل المستخدمون رسائل بريد إلكتروني مشفرة إلى مستلمين من خارج مؤسستنا. هل هناك أي شيء يتعين على المستلمين الخارجيين القيام به لقراءة رسائل البريد الإلكتروني المشفرة باستخدام تشفير الرسائل Office 365 والرد عليها؟**

يمكن للمستلمين من خارج مؤسستك الذين يتلقون Microsoft 365 الرسائل المشفرة عرضها بإحدى طريقتين:

- بتسجيل الدخول باستخدام حساب Microsoft أو حساب العمل أو المؤسسة التعليمية المقترن Office 365.

- باستخدام رمز تمرير لمرة واحدة.

 **س. هل يتم تخزين Microsoft 365 الرسائل المشفرة في السحابة أو على خوادم Microsoft؟**

لا، يتم الاحتفاظ بالرسائل المشفرة على نظام البريد الإلكتروني للمستلم، وعندما يفتح المستلم الرسالة، يتم نشرها مؤقتا للعرض على خوادم Microsoft. لا يتم تخزين الرسائل هناك.

 **س. هل يمكنني تخصيص رسائل البريد الإلكتروني المشفرة باستخدام علامتي التجارية؟**

نعم. يمكنك استخدام Exchange Online PowerShell cmdlets لتخصيص النص الافتراضي الذي يظهر في أعلى رسائل البريد الإلكتروني المشفرة ونص إخلاء المسؤولية والشعار الذي تريد استخدامه لرسالة البريد الإلكتروني ومدخل التشفير. تتوفر هذه الميزة الآن في OMEv2. للحصول على التفاصيل، راجع [إضافة علامة تجارية إلى الرسائل المشفرة](add-your-organization-brand-to-encrypted-messages.md).

 **س. هل تتطلب الخدمة ترخيصا لكل مستخدم في مؤسستي؟**

يلزم الحصول على ترخيص لكل مستخدم في المؤسسة يرسل بريدا إلكترونيا مشفرا.

 **س. هل يتطلب المستلمون الخارجيون اشتراكات؟**

لا، لا يتطلب المستلمون الخارجيون اشتراكا لقراءة الرسائل المشفرة أو الرد عليها.

 **س. كيف يختلف Office 365 تشفير الرسائل عن خدمات Rights Management (RMS)؟**

يوفر RMS قدرات حماية حقوق المعلومات لرسائل البريد الإلكتروني الداخلية للمؤسسة من خلال توفير قوالب مضمنة، مثل: عدم إعادة التوجيه وسرية الشركة. Office 365 يدعم تشفير الرسائل تشفير رسائل البريد الإلكتروني للرسائل المرسلة إلى مستلمين خارجيين بالإضافة إلى المستلمين الداخليين.

 **س. كيف يختلف Office 365 تشفير الرسائل عن S/MIME؟**

S/MIME هي في الأساس تقنية تشفير من جانب العميل، وتتطلب إدارة الشهادات المعقدة والبنية الأساسية للنشر. Office 365 يستخدم تشفير الرسائل قواعد تدفق البريد (المعروفة أيضا بقواعد النقل) ولا يعتمد على نشر الشهادات.

 **س. هل يمكنني قراءة الرسائل المشفرة عبر الأجهزة المحمولة؟**

نعم، يمكنك عرض الرسائل على Android وiOS عن طريق تنزيل تطبيقات عارض OME من متجر Google Play ومتجر تطبيقات Apple. افتح مرفق HTML في تطبيق OME Viewer ثم اتبع الإرشادات لفتح الرسالة المشفرة. بالنسبة للأجهزة المحمولة الأخرى، يمكنك فتح مرفق HTML طالما أن عميل البريد يدعم "نشر النموذج".

 **س. هل الردود والرسائل التي تمت إعادة توجيهها مشفرة؟**

نعم. يستمر تشفير الاستجابات طوال مدة مؤشر الترابط.

 **س. هل يوفر Office 365 تشفير الرسائل الترجمة؟**

تتم ترجمة البريد الإلكتروني الوارد ومحتوى HTML استنادا إلى إعدادات البريد الإلكتروني للمرسل. يتم ترجمة مدخل العرض استنادا إلى إعدادات المستعرض الخاصة بالمستلم. ومع ذلك، لا يتم ترجمة النص الأساسي الفعلي (المحتوى) للرسالة المشفرة.

 **س. ما أسلوب التشفير المستخدم لتشفير الرسائل Office 365؟**

يستخدم تشفير الرسائل Office 365 خدمات Rights Management (RMS) كبنية تحتية للتشفير. يعتمد أسلوب التشفير المستخدم على المكان الذي تحصل فيه على مفاتيح RMS المستخدمة لتشفير الرسائل وفك تشفيرها.

- إذا كنت تستخدم Microsoft Azure RMS للحصول على المفاتيح، يتم استخدام وضع التشفير 2. وضع التشفير 2 هو تطبيق تشفير AD RMS محدث ومحسن. وهو يدعم RSA 2048 للتوقيع والتشفير، ويدعم SHA-256 للتوقيع.

- إذا كنت تستخدم Active Directory (AD) RMS للحصول على المفاتيح، يتم استخدام وضع التشفير 1 أو وضع التشفير 2. يعتمد الأسلوب المستخدم على توزيع AD RMS المحلي. وضع التشفير 1 هو تنفيذ تشفير AD RMS الأصلي. وهو يدعم RSA 1024 للتوقيع والتشفير، ويدعم SHA-1 للتوقيع. يستمر دعم هذا الوضع من قبل كافة الإصدارات الحالية من RMS.

لمزيد من المعلومات، راجع [أوضاع تشفير AD RMS](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/hh867439(v=ws.10)).

**س. لماذا تقول بعض الرسائل المشفرة إنها تأتي من** Office365@messaging.microsoft.com؟

عند إرسال رد مشفر من مدخل التشفير أو من خلال تطبيق OME Viewer، يتم تعيين عنوان البريد الإلكتروني المرسل إلى Office365@messaging.microsoft.com لأن الرسالة المشفرة يتم إرسالها من خلال نقطة نهاية Microsoft. يساعد ذلك على منع وضع علامة على الرسائل المشفرة على أنها بريد عشوائي. لا يتم تغيير الاسم المعروض على البريد الإلكتروني والعنوان داخل مدخل التشفير بسبب هذه التسمية. أيضا، تنطبق هذه التسمية فقط على الرسائل المرسلة عبر المدخل، وليس من خلال أي عميل بريد إلكتروني آخر.

 **س. أنا مشترك في Exchange Hosted Encryption (EHE). أين يمكنني معرفة المزيد حول الترقية إلى Office 365 تشفير الرسائل؟**

تمت ترقية جميع عملاء EHE إلى تشفير الرسائل Office 365. لمزيد من المعلومات، تفضل بزيارة [Exchange مركز ترقية التشفير المستضاف](../security/office-365-security/exchange-online-protection-overview.md).

 **س. هل أحتاج إلى فتح أي عناوين URL أو عناوين IP أو منافذ في جدار حماية مؤسستي لدعم تشفير الرسائل Office 365؟**

نعم. يجب إضافة عناوين URL Exchange Online إلى قائمة السماح لمؤسستك لتمكين المصادقة للرسائل المشفرة بواسطة تشفير الرسائل Office 365. للحصول على قائمة بعناوين URL Exchange Online، راجع [عناوين URL Microsoft 365 ونطاقات عناوين IP](../enterprise/urls-and-ip-address-ranges.md).

 **س. كم عدد المستلمين الذين يمكنني إرسال رسالة مشفرة Microsoft 365 إليها؟**

الحد الأقصى للمستلم هو 500 مستلم لكل رسالة، أو عند دمجها بعد توسيع قائمة التوزيع، 11980 حرفا في الحقل " **إلى** " للرسالة، أيهما يأتي أولا.

 **س. هل من الممكن إبطال رسالة تم إرسالها إلى مستلم معين؟**

لا. لا يمكنك إبطال رسالة إلى شخص معين بعد إرسالها.

 **س. هل يمكنني عرض تقرير عن الرسائل المشفرة التي تم تلقيها وقراءتها؟**

لا يوجد تقرير يوضح ما إذا تم عرض رسالة مشفرة، ولكن هناك تقارير Microsoft 365 متوفرة يمكنك الاستفادة منها لتحديد عدد الرسائل التي تطابق قاعدة تدفق بريد معينة (تعرف أيضا باسم قاعدة النقل)، على سبيل المثال.

 **س. ماذا تفعل Microsoft بالمعلومات التي أقدمها من خلال مدخل OME وتطبيق عارض OME؟**

يوفر [بيان خصوصية مدخل تشفير Office 365 المراسلة](https://privacy.microsoft.com/privacystatement) معلومات مفصلة حول ما تفعله Microsoft ولا تفعله بمعلوماتك الخاصة.

**س. ماذا أفعل إذا لم أتلقى رمز المرور لمرة واحدة بعد طلبه؟**

أولا، تحقق من مجلد البريد غير الهام أو البريد العشوائي في عميل البريد الإلكتروني. قد تؤدي إعدادات DKIM وDMARC لمؤسستك إلى تصفية رسائل البريد الإلكتروني هذه كبرم عشوائي.

بعد ذلك، تحقق من العزل في مركز التوافق & الأمان. غالبا ما تنتهي الرسائل التي تحتوي على رمز مرور لمرة واحدة، خاصة الرسائل الأولى التي تتلقاها مؤسستك، في العزل.
