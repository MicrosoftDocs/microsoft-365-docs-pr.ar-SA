---
title: إبطال البريد الإلكتروني المشفر بواسطة تشفير الرسائل المتقدم
f1.keywords:
- NOCSH
ms.author: krowley
author: kccross
manager: laurawi
audience: Admin
ms.topic: conceptual
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.date: 03/04/2022
ms.collection:
- Strat_O365_IP
- M365-security-compliance
search.appverid:
- MET150
description: بصفتك مسؤولا ومرسل رسائل، يمكنك إبطال بعض رسائل البريد الإلكتروني التي تم تشفيرها باستخدام تشفير الرسائل المتقدم من Office 365.
ms.openlocfilehash: 313cbe990e322285fc81465329fa5e19b52e2701
ms.sourcegitcommit: 9ba00298cfa9ae293e4a57650965fdb3e8ffe07b
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/11/2022
ms.locfileid: "64759380"
---
# <a name="revoke-email-encrypted-by-advanced-message-encryption"></a>إبطال البريد الإلكتروني المشفر بواسطة تشفير الرسائل المتقدم

يتم تقديم إبطال البريد الإلكتروني كجزء من تشفير الرسائل المتقدم من Office 365. يتم تضمين تشفير الرسائل المتقدم من Office 365 في [Microsoft 365 Enterprise E5](https://www.microsoft.com/microsoft-365/enterprise/home)، Office 365 E5، Microsoft 365 E5 (أسعار الموظفين غير الربحية)، Office 365 Enterprise  E5 (تسعير الموظفين غير الربحي)، Office 365 Education A5. إذا كان لدى مؤسستك اشتراك لا يتضمن تشفير الرسائل المتقدم من Office 365، يمكنك شراؤه باستخدام الوظيفة الإضافية التوافق في Microsoft 365 E5 SKU Microsoft 365 E3، Microsoft 365 E3 ( تسعير الموظفين غير الربحي، أو الوظيفة الإضافية خدمات الامتثال المتطورة في Office 365 SKU Microsoft 365 E3 أو Microsoft 365 E3 (أسعار الموظفين غير الربحية) أو وحدات SKU Office 365.

تشكل هذه المقالة جزءا من سلسلة أكبر من المقالات حول [Office 365 تشفير الرسائل](ome.md).

إذا تم تشفير رسالة باستخدام تشفير الرسائل المتقدم من Office 365، وكنت مسؤولا Microsoft 365 أو كنت مرسل الرسالة، يمكنك إبطال الرسالة في ظل شروط معينة. يقوم المسؤولون بإبطال الرسائل باستخدام PowerShell. كمرسل، يمكنك إبطال رسالة أرسلتها مباشرة من Outlook على ويب. تصف هذه المقالة الظروف التي يكون فيها الإبطال ممكنا وكيفية القيام بذلك.

> [!NOTE]
> لضمان توفر القدرة على تعقب رسائل OME وإبطالها، يجب إضافة قالب علامة تجارية مخصص. راجع [إضافة العلامة التجارية لمؤسستك إلى الرسائل المشفرة](add-your-organization-brand-to-encrypted-messages.md)
  
## <a name="encrypted-emails-that-you-can-revoke"></a>رسائل البريد الإلكتروني المشفرة التي يمكنك إبطالها

يمكن للمسؤولين ومرسلي الرسائل إبطال رسائل البريد الإلكتروني المشفرة إذا تلقى المستلم رسالة بريد إلكتروني مشفرة مستندة إلى ارتباطات ذات علامة تجارية. إذا تلقى المستلم تجربة مضمنة أصلية في عميل Outlook معتمد، فلن تتمكن من إبطال الرسالة.

يعتمد ما إذا كان المستلم يتلقى تجربة مستندة إلى ارتباط أو تجربة مضمنة على نوع هوية المستلم: Office 365 ومستلمي حساب Microsoft (على سبيل المثال، outlook.com المستخدمين) الحصول على تجربة مضمنة في عملاء Outlook المعتمدين. تحصل جميع أنواع المستلمين الأخرى، مثل مستلمي Gmail وYahoo، على تجربة مستندة إلى الارتباط.

يمكن للمسؤولين ومرسلي الرسائل إبطال الرسائل المشفرة باستخدام التشفير المطبق مباشرة من Outlook على ويب. على سبيل المثال، الرسائل المشفرة باستخدام الخيار "تشفير فقط".

:::image type="content" source="../media/adhocencryptionrevoke.png" alt-text="لقطة شاشة تعرض خيار تشفير فقط في Outlook على ويب.":::

## <a name="recipient-experience-for-revoked-encrypted-emails"></a>تجربة المستلم لرسائل البريد الإلكتروني المشفرة التي تم إبطالها

بمجرد إبطال رسالة بريد إلكتروني، يتلقى المستلم خطأ عند الوصول إلى البريد الإلكتروني المشفر من خلال مدخل تشفير الرسالة Office 365: "تم إبطال الرسالة من قبل المرسل".

![لقطة شاشة تعرض رسالة بريد إلكتروني مشفرة تم إبطالها.](../media/revoked-encrypted-email.png)

## <a name="how-to-revoke-an-encrypted-message-that-you-sent"></a>كيفية إبطال رسالة مشفرة أرسلتها

يمكنك إبطال البريد الذي أرسلته إلى مستلم واحد يستخدم حسابا اجتماعيا مثل gmail.com أو yahoo.com. بمعنى آخر، يمكنك إبطال رسالة بريد إلكتروني تم إرسالها إلى مستلم واحد تلقى التجربة المستندة إلى الارتباط.

لا يمكنك إبطال البريد الذي أرسلته إلى مستلم يستخدم حساب عمل أو مؤسسة تعليمية من Office 365 أو Microsoft 365 أو مستخدم يستخدم حساب Microsoft، على سبيل المثال، حساب outlook.com. 

لإبطال رسالة مشفرة أرسلتها، أكمل هذه الخطوات

1. في Outlook على ويب، في المجلد **المرسل**، استعرض وصولا إلى الرسالة التي تريد إبطالها.

   إذا كان البريد قابلا للاسترداد، فسترى الارتباط "إزالة الوصول الخارجي" في أعلى الرسالة.

    :::image type="content" source="../media/infoprotect-email-encryption/adhocencryptionrevokesentmsg.png" alt-text="لقطة شاشة تعرض البريد المشفر الذي تريد إبطاله في Outlook على ويب.":::

2. انقر فوق **"إزالة الوصول الخارجي** " لإبطال الرسالة.

   تظهر الرسالة أن حالتها قد تم إبطالها.

   :::image type="content" source="../media/adhocencryptionrevokedmsg.png" alt-text="لقطة شاشة تعرض رسالة مشفرة تم إبطالها في Outlook على ويب.":::

## <a name="how-to-revoke-an-encrypted-message-as-an-administrator"></a>كيفية إبطال رسالة مشفرة كمسؤول

Microsoft 365 يتبع المسؤولون هذه الخطوات العامة لإبطال رسالة بريد إلكتروني مشفرة مؤهلة:

- احصل على معرف الرسالة للبريد الإلكتروني.
- تحقق من أنه يمكنك إبطال الرسالة.
- إبطال البريد.

### <a name="step-1-obtain-the-message-id-of-the-email"></a>الخطوة 1. الحصول على معرف الرسالة للبريد الإلكتروني

قبل أن تتمكن من إبطال بريد مشفر، قم بجمع معرف الرسالة للبريد. عادة ما يكون معرف الرسالة بالتنسيق:

`<xxxxxxxxxxxxxxxxxxxxxxx@xxxxxx.xxxx.prod.outlook.com>`  

هناك طرق متعددة للعثور على معرف الرسالة للبريد الإلكتروني الذي تريد إبطاله. يصف هذا القسم بعض الخيارات، ولكن يمكنك استخدام أي أسلوب يوفر المعرف.

#### <a name="to-identify-the-message-id-of-the-email-you-want-to-revoke-by-using-message-trace-in-the-security-amp-compliance-center"></a>لتعريف معرف الرسالة للبريد الإلكتروني الذي تريد إبطاله باستخدام "تتبع الرسائل" في مركز توافق الأمان &amp;

1. ابحث عن البريد الإلكتروني بواسطة المرسل أو المستلم باستخدام ["تتبع الرسائل الجديدة" في مركز التوافق & الأمان](https://blogs.technet.microsoft.com/exchange/2018/05/02/new-message-trace-in-office-365-security-compliance-center/).

2. بمجرد تحديد موقع البريد الإلكتروني، حدده لإظهار جزء **تفاصيل تتبع الرسائل** . قم بتوسيع **مزيد من المعلومات** لتحديد موقع معرف الرسالة.

#### <a name="to-identify-the-message-id-of-the-email-you-want-to-revoke-by-using-office-message-encryption-reports-in-the-security-amp-compliance-center"></a>لتحديد معرف الرسالة للبريد الإلكتروني الذي تريد إبطاله باستخدام تقارير تشفير الرسائل Office في مركز توافق الأمان &amp;

1. في مركز توافق الأمان &amp; ، انتقل إلى **تقرير تشفير الرسائل**. للحصول على معلومات حول هذا التقرير، راجع [عرض تقارير أمان البريد الإلكتروني في مركز توافق الأمان&amp;](../security/office-365-security/view-email-security-reports.md).

2. اختر جدول **"عرض التفاصيل** " وحدد الرسالة التي تريد إبطالها.

3. انقر نقرا مزدوجا فوق الرسالة لعرض التفاصيل التي تتضمن معرف الرسالة.

### <a name="step-2-verify-that-the-mail-is-revocable"></a>الخطوة 2. التحقق من أن البريد قابل للاسترداد

للتحقق مما إذا كان يمكنك إبطال رسالة، تحقق مما إذا كان حقل حالة الإبطال مرئيا في تقرير التشفير، في جدول **التفاصيل** في مركز توافق الأمان &amp; .

للتحقق مما إذا كان يمكنك إبطال رسالة بريد إلكتروني معينة باستخدام Windows PowerShell، أكمل هذه الخطوات.

1. باستخدام حساب العمل أو المؤسسة التعليمية الذي لديه أذونات المسؤول العام في مؤسستك، ابدأ جلسة عمل Windows PowerShell وقم بالاتصال Exchange Online. للحصول على الإرشادات، راجع [الاتصال Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

2. شغل أمر cmdlet Get-OMEMessageStatus كما يلي:

     ```powershell
     Get-OMEMessageStatus -MessageId "<message id>" | ft -a  Subject, IsRevocable
     ```

   يقوم هذا الأمر بإرجاع موضوع الرسالة وما إذا كانت الرسالة قابلة للاستدعاء. على سبيل المثال

     ```console
     Subject        IsRevocable
     -------        -----------
     "Test message" True
     ```

### <a name="step-3-revoke-the-mail"></a>الخطوة 3. إبطال البريد

بمجرد معرفة معرف الرسالة للبريد الإلكتروني الذي تريد إبطاله، والتحقق من أن الرسالة قابلة للاستدعاء، يمكنك إبطال البريد الإلكتروني باستخدام مركز توافق الأمان &amp; أو Windows PowerShell.

لإبطال الرسالة باستخدام مركز توافق الأمان &amp;

1. باستخدام حساب العمل أو المؤسسة التعليمية الذي لديه أذونات المسؤول العام في مؤسستك، اتصل بمركز التوافق & الأمان.

2. في **تقرير التشفير**، في جدول **التفاصيل** للرسالة، اختر **"إبطال الرسالة**".

لإبطال رسالة بريد إلكتروني باستخدام Windows PowerShell، استخدم Set-OMEMessageRevocation cmdlet.

1. باستخدام حساب العمل أو المؤسسة التعليمية الذي لديه أذونات المسؤول العمومي في مؤسستك، [الاتصال Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

2. شغل أمر cmdlet Set-OMEMessageRevocation كما يلي:

    ```powershell
    Set-OMEMessageRevocation -Revoke $true -MessageId "<messageId>"
    ```

3. للتحقق مما إذا تم إبطال البريد الإلكتروني، قم بتشغيل Get-OMEMessageStatus cmdlet كما يلي:

    ```powershell
    Get-OMEMessageStatus -MessageId "<messageId>" | ft -a  Subject, Revoked
    ```

    إذا نجح الإبطال، يقوم cmdlet بإرجاع النتيجة التالية:  

     ```console
     Revoked: True
     ```

## <a name="more-information-about-office-365-advanced-message-encryption"></a>مزيد من المعلومات حول تشفير الرسائل المتقدم من Office 365

- [تشفير الرسائل المتقدم من Office 365](ome-advanced-message-encryption.md)

- [تشفير الرسائل المتقدم من Office 365 - انتهاء صلاحية البريد الإلكتروني](ome-advanced-expiration.md)

- [نهج الرسالة ووصف خدمة التوافق](/office365/servicedescriptions/exchange-online-service-description/message-policy-and-compliance)