---
title: إبطال البريد الإلكتروني المشفر بواسطة تشفير الرسائل المتقدمة
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
description: كمسؤول ومرسل رسالة، يمكنك إبطال بعض رسائل البريد الإلكتروني التي تم تشفيرها باستخدام تشفير الرسائل المتقدم من Office 365.
ms.openlocfilehash: bf793dce23c91e8b45f96114e6c4a56c866adc32
ms.sourcegitcommit: a216617d6ff27fe7d3089a047fbeaac5d72fd25c
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/16/2022
ms.locfileid: "63566543"
---
# <a name="revoke-email-encrypted-by-advanced-message-encryption"></a>إبطال البريد الإلكتروني المشفر بواسطة تشفير الرسائل المتقدمة

يتم عرض إلغاء البريد الإلكتروني كجزء من تشفير الرسائل المتقدم من Office 365. تشفير الرسائل المتقدم من Office 365 في [Microsoft 365 Enterprise E5](https://www.microsoft.com/microsoft-365/enterprise/home)، Office 365 E5، Microsoft 365 E5 (أسعار الموظفين غير الربحية)، Office 365 Enterprise  E5 (أسعار الموظفين غير الربحية)، Office 365 Education A5. إذا كانت مؤسستك لديها اشتراك لا يتضمن تشفير الرسائل المتقدم من Office 365، يمكنك شراؤه باستخدام التوافق في Microsoft 365 E5 SKU الإضافية ل Microsoft 365 E3، Microsoft 365 E3 ( أسعار الموظفين غير الربحية) أو خدمات الامتثال المتطورة في Office 365 SKU الإضافية Microsoft 365 E3 أو Microsoft 365 E3 (أسعار الموظفين غير الربحية) أو Office 365 SKU.

هذه المقالة هي جزء من سلسلة أكبر من المقالات حول [تشفير الرسائل من Office 365.](ome.md)

إذا تم تشفير رسالة باستخدام تشفير الرسائل المتقدم من Office 365، وأنت مسؤول Microsoft 365 أو كنت مرسل الرسالة، يمكنك إبطال الرسالة في ظروف معينة. يبطل المسؤولون الرسائل باستخدام PowerShell. كمرسل، تقوم بإبطال رسالة أرسلتها مباشرة من Outlook على ويب. تصف هذه المقالة الظروف التي يمكن فيها إلغاء الأمر وكيفية القيام بذلك.

> [!NOTE]
> لضمان توفر إمكانية تعقب رسائل OME وإبطالها، يجب إضافة قالب علامة تجارية مخصص. راجع [إضافة العلامة التجارية لمنظمتك إلى الرسائل المشفرة](add-your-organization-brand-to-encrypted-messages.md)
  
## <a name="encrypted-emails-that-you-can-revoke"></a>رسائل البريد الإلكتروني المشفرة التي يمكنك إبطالها

يمكن للمسؤولين ومرسلي الرسائل إبطال رسائل البريد الإلكتروني المشفرة إذا تلقى المستلم رسالة بريد إلكتروني مشفرة تستند إلى ارتباطات. إذا تلقى المستلم تجربة م داخلية أصلية في عميل Outlook معتمد، لا يمكنك إبطال الرسالة.

يعتمد ما إذا كان المستلم يتلقى تجربة مستندة إلى ارتباط أو تجربة م داخلية على نوع هوية المستلم: يحصل مستلمو حساب Office 365 و Microsoft (على سبيل المثال، مستخدمو outlook.com) على تجربة م داخلة في عملاء Outlook المعتمدين. تحصل جميع أنواع المستلمين الأخرى، مثل مستلمي Gmail و Yahoo، على تجربة مستندة إلى الارتباطات.

يمكن للمسؤولين ومرسلي الرسائل إبطال الرسائل المشفرة باستخدام التشفير المطبق مباشرة من Outlook على ويب. على سبيل المثال، الرسائل المشفرة باستخدام الخيار تشفير فقط.

:::image type="content" source="../media/adhocencryptionrevoke.png" alt-text="لقطة شاشة تعرض خيار التشفير فقط في Outlook على ويب.":::

## <a name="recipient-experience-for-revoked-encrypted-emails"></a>تجربة المستلم في رسائل البريد الإلكتروني المشفرة التي تم إبطالها

بعد إبطال رسالة بريد إلكتروني، يتلقى المستلم رسالة خطأ عند الوصول إلى البريد الإلكتروني المشفر عبر مدخل تشفير الرسائل من Office 365: "تم إبطال الرسالة من قبل المرسل".

![لقطة شاشة تعرض رسالة بريد إلكتروني مشفرة تم إبطالها.](../media/revoked-encrypted-email.png)

## <a name="how-to-revoke-an-encrypted-message-that-you-sent"></a>كيفية إبطال رسالة مشفرة أرسلتها

يمكنك إبطال البريد الذي أرسلته إلى مستلم واحد يستخدم حسابا اجتماعيا مثل gmail.com أو yahoo.com. بعبارة أخرى، يمكنك إبطال رسالة بريد إلكتروني تم إرسالها إلى مستلم واحد تلقى التجربة المستندة إلى الارتباط.

لا يمكنك إبطال بريد أرسلته إلى مستلم يستخدم حساب عمل أو مدرسة من Office 365 أو Microsoft 365 أو مستخدم يستخدم حساب Microsoft، على سبيل المثال، حساب outlook.com Microsoft. 

لإلغاء رسالة مشفرة أرسلتها، أكمل هذه الخطوات

1. في Outlook على ويب، في المجلد **المرسل**، استعرض بحثا عن الرسالة التي تريد إبطالها.

   إذا كان البريد قابلا للإزالة، سترى الارتباط "إزالة الوصول الخارجي" في أعلى الرسالة.

    :::image type="content" source="../media/infoprotect-email-encryption/adhocencryptionrevokesentmsg.png" alt-text="لقطة شاشة تعرض البريد المشفر الذي تريد إبطاله في Outlook على ويب.":::

2. انقر **فوق إزالة الوصول الخارجي** لإبطال الرسالة.

   تظهر الرسالة أنه تم إبطال الحالة الخاصة بها.

   :::image type="content" source="../media/adhocencryptionrevokedmsg.png" alt-text="لقطة شاشة تعرض رسالة مشفرة تم إبطالها في Outlook على ويب.":::

## <a name="how-to-revoke-an-encrypted-message-as-an-administrator"></a>كيفية إبطال رسالة مشفرة كمسؤول

Microsoft 365 المسؤولين على اتباع هذه الخطوات العامة لإلغاء رسالة بريد إلكتروني مشفرة مؤهلة:

- احصل على "عنوان الرسالة" للبريد الإلكتروني.
- تحقق من أنه يمكنك إبطال الرسالة.
- إبطال البريد.

### <a name="step-1-obtain-the-message-id-of-the-email"></a>الخطوة 1. الحصول على "عنوان الرسالة" للبريد الإلكتروني

قبل أن تتمكن من إبطال رسالة بريد مشفرة، اجمع "معرف الرسالة" للبريد. عادة ما يكون MessageId من التنسيق:

`<xxxxxxxxxxxxxxxxxxxxxxx@xxxxxx.xxxx.prod.outlook.com>`  

هناك طرق متعددة للعثور على "المعرف الرسالة" للبريد الإلكتروني الذي تريد إبطاله. يصف هذا القسم خيارين، ولكن يمكنك استخدام أي أسلوب يوفر الم ID.

#### <a name="to-identify-the-message-id-of-the-email-you-want-to-revoke-by-using-message-trace-in-the-security-amp-compliance-center"></a>لتحديد "هوية الرسالة" للبريد الإلكتروني الذي تريد إبطاله باستخدام "تتبع الرسائل" في "مركز توافق &amp; الأمان"

1. ابحث عن البريد الإلكتروني بواسطة المرسل أو المستلم باستخدام تتبع الرسائل الجديدة [في مركز & الأمان](https://blogs.technet.microsoft.com/exchange/2018/05/02/new-message-trace-in-office-365-security-compliance-center/).

2. بمجرد تحديد موقع البريد الإلكتروني، حدده لإحضار جزء تفاصيل **تتبع** الرسائل. قم **بتوسيع مزيد من المعلومات** لتحديد موقع "معرّف الرسالة".

#### <a name="to-identify-the-message-id-of-the-email-you-want-to-revoke-by-using-office-message-encryption-reports-in-the-security-amp-compliance-center"></a>لتحديد "هوية الرسالة" للبريد الإلكتروني الذي تريد إبطاله باستخدام Office تشفير الرسائل في "مركز توافق &amp; الأمان"

1. في مركز توافق &amp; الأمان، انتقل إلى تقرير **تشفير الرسائل**. للحصول على معلومات حول هذا التقرير، راجع [عرض تقارير أمان البريد الإلكتروني في مركز توافق &amp; الأمان](../security/office-365-security/view-email-security-reports.md).

2. اختر الجدول **عرض التفاصيل** وحدد الرسالة التي تريد إبطالها.

3. انقر نقرا مزدوجا فوق الرسالة لعرض التفاصيل التي تتضمن "معرف الرسالة".

### <a name="step-2-verify-that-the-mail-is-revocable"></a>الخطوة 2. التحقق من أن البريد قابل لرداد البريد

للتحقق مما إذا كان يمكنك إبطال رسالة، تحقق مما إذا كان الحقل حالة إبطال الرسالة مرئيا في تقرير التشفير، في الجدول تفاصيل في مركز  توافق &amp; الأمان.

للتحقق مما إذا كان يمكنك إبطال رسالة بريد إلكتروني معينة باستخدام Windows PowerShell، أكمل هذه الخطوات.

1. باستخدام حساب العمل أو المؤسسة الدراسية الذي لديه أذونات المسؤول العام في مؤسستك، ابدأ جلسة عمل Windows PowerShell واتصل Exchange Online. للحصول على الإرشادات، [راجع الاتصال Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

2. تشغيل Get-OMEMessageStatus cmdlet كما يلي:

     ```powershell
     Get-OMEMessageStatus -MessageId "<message id>" | ft -a  Subject, IsRevocable
     ```

   يرجع هذا الأمر موضوع الرسالة وما إذا كانت الرسالة قابلة للإرجاع. على سبيل المثال

     ```console
     Subject        IsRevocable
     -------        -----------
     "Test message" True
     ```

### <a name="step-3-revoke-the-mail"></a>الخطوة 3. إبطال البريد

بعد أن تعرف &amp; "المعرف الرسالة" للبريد الإلكتروني الذي تريد إبطاله، وتتحقق من أن الرسالة قابلة للإلغاء، يمكنك إبطال البريد الإلكتروني باستخدام "مركز توافق الأمان" أو Windows PowerShell.

لإلغاء الرسالة باستخدام مركز توافق &amp; الأمان

1. باستخدام حساب العمل أو المؤسسة الدراسية الذي لديه أذونات المسؤول العام في مؤسستك، اتصل بمركز التوافق & الأمان.

2. في تقرير **التشفير**، في جدول **التفاصيل** للرسالة، اختر **إبطال الرسالة**.

لإلغاء رسالة بريد إلكتروني باستخدام Windows PowerShell، استخدم Set-OMEMessageRevocation cmdlet.

1. باستخدام حساب العمل أو المدرسة الذي لديه أذونات المسؤول العام في مؤسستك، الاتصال إلى [Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

2. تشغيل Set-OMEMessageRevocation cmdlet كما يلي:

    ```powershell
    Set-OMEMessageRevocation -Revoke $true -MessageId "<messageId>"
    ```

3. للتحقق مما إذا تم إبطال البريد الإلكتروني، قم بتشغيل Get-OMEMessageStatus cmdlet كما يلي:

    ```powershell
    Get-OMEMessageStatus -MessageId "<messageId>" | ft -a  Subject, Revoked
    ```

    إذا نجح إلغاء الأمر، فإن الأمر cmdlet يرجع النتيجة التالية:  

     ```console
     Revoked: True
     ```

## <a name="more-information-about-office-365-advanced-message-encryption"></a>مزيد من المعلومات حول تشفير الرسائل المتقدم من Office 365

- [تشفير الرسائل المتقدم من Office 365](ome-advanced-message-encryption.md)

- [تشفير الرسائل المتقدم من Office 365 - انتهاء صلاحية البريد الإلكتروني](ome-advanced-expiration.md)

- [وصف خدمة التوافق ون نهج الرسالة](/office365/servicedescriptions/exchange-online-service-description/message-policy-and-compliance)