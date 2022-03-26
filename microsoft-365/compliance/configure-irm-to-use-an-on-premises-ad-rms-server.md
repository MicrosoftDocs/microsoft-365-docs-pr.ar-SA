---
title: تكوين IRM لاستخدام خادم AD RMS
f1.keywords:
- NOCSH
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 12/13/2017
audience: End User
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- MET150
ms.assetid: 3ecde857-4b7c-451d-b4aa-9eeffc8a8c61
ms.collection:
- M365-security-compliance
description: تعرف على كيفية تكوين إدارة حقوق استخدام المعلومات (IRM) Exchange Online استخدام خادم خدمة إدارة حقوق Active Directory (AD RMS).
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: f87992fc9be676b9485d6ec7a7b7ff1f3a4d39d9
ms.sourcegitcommit: 99067d5eb1fa7b094e7cdb1f7be65acaaa235a54
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 01/29/2022
ms.locfileid: "63566298"
---
# <a name="configure-irm-to-use-an-on-premises-ad-rms-server"></a>تكوين IRM لاستخدام خادم AD RMS

لاستخدامها مع عمليات النشر المحلي، تستخدم إدارة حقوق استخدام المعلومات (IRM) في Exchange Online خدمات إدارة حقوق Active Directory (AD RMS)، تقنية حماية المعلومات في Windows Server 2008 واللاحقة. يتم تطبيق حماية IRM على البريد الإلكتروني من خلال تطبيق قالب نهج حقوق AD RMS على رسالة بريد إلكتروني. يتم إرفاق الحقوق بالرسالة نفسها بحيث تحدث الحماية عبر الإنترنت وغير متصل وداخل جدار الحماية الخاص بالم المؤسسة وخارجه.

يوضح لك هذا الموضوع كيفية تكوين IRM لاستخدام خادم AD RMS. للحصول على معلومات حول استخدام الإمكانات الجديدة تشفير الرسائل من Office 365 Azure Active Directory و Azure Rights Management، راجع الأسئلة [تشفير الرسائل من Office 365 الأسئلة الشائعة](./ome-faq.yml).

لمعرفة المزيد حول إدارة حقوق المعلومات في Exchange Online، راجع [إدارة حقوق استخدام المعلومات في](information-rights-management-in-exchange-online.md) Exchange Online.

## <a name="what-do-you-need-to-know-before-you-begin"></a>ما الذي تحتاج إلى معرفته قبل البدء؟

- الوقت المقدر لإكمال هذه المهمة: 30 دقيقة

- يجب تعيين أذونات لك قبل تنفيذ هذا الإجراء أو الإجراءات. لمعرفة الأذونات التي تحتاج إليها، راجع إدخال "إدارة حقوق استخدام المعلومات" في [موضوع](/Exchange/permissions/feature-permissions/policy-and-compliance-permissions) أذونات التوافق ون نهج المراسلة.

- يجب تشغيل خادم AD RMS Windows Server 2008 أو أي وقت لاحق. للحصول على تفاصيل حول كيفية نشر AD RMS، راجع تثبيت [AD RMS Cluster](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc726041(v=ws.11)).

- للحصول على تفاصيل حول كيفية تثبيت Windows PowerShell الخدمة والاتصال بها، راجع الاتصال Exchange Online [Remote PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

- للحصول على معلومات حول اختصارات لوحة المفاتيح التي قد تنطبق على الإجراءات الواردة في هذا الموضوع، راجع اختصارات لوحة المفاتيح Exchange مركز الإدارة في [Exchange Online](/Exchange/accessibility/keyboard-shortcuts-in-admin-center).

> [!TIP]
> هل تواجه مشاكل؟ اطلب المساعدة في Exchange الأخرى. تفضل [بزيارة المنتديات](https://go.microsoft.com/fwlink/p/?linkId=60612) على Exchange Server أو [Exchange Online](https://go.microsoft.com/fwlink/p/?linkId=267542) أو [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkId=285351).

## <a name="how-do-you-do-this"></a>كيف يمكنك القيام بذلك؟
<a name="sectionSection1"> </a>

### <a name="step-1-use-the-ad-rms-console-to-export-a-trusted-publishing-domain-tpd-from-an-ad-rms-server"></a>الخطوة 1: استخدام وحدة تحكم AD RMS لتصدير مجال نشر موثوق به (TPD) من خادم AD RMS

الخطوة الأولى هي تصدير مجال نشر موثوق به (TPD) من خادم AD RMS المحلي إلى ملف XML. يحتوي TPD على الإعدادات التالية اللازمة لاستخدام ميزات RMS:

- شهادة ترخيص الخادم (SLC) المستخدمة لتوقيع الشهادات والتراخيص وتشفيرها

- عناوين URL المستخدمة للترخيص والنشر

- قوالب نهج حقوق AD RMS التي تم إنشاؤها باستخدام SLC المعين لهذا TPD

عند استيراد TPD، يتم تخزينه وحمايته في Exchange Online.

1. افتح وحدة خدمات إدارة حقوق Active Directory، ثم قم بتوسيع كتلة AD RMS.

2. في شجرة وحدة التحكم، قم بتوسيع **"سياسات الثقة**"، ثم انقر فوق مجالات **النشر الموثوق بها**.

3. في جزء النتائج، حدد الشهادة للمجال الذي تريد تصديره.

4. في الجزء **إجراءات** ، انقر فوق **تصدير مجال النشر الموثوق به**.

5. في المربع **ملف مجال النشر** ، انقر فوق حفظ **باسم** لحفظ الملف في موقع معين على الكمبيوتر المحلي. اكتب اسم ملف، وتأكد من تحديد `.xml` ملحق اسم الملف، ثم انقر فوق **حفظ**.

6. في **المربعين كلمة** **المرور** وتأكيد كلمة المرور، اكتب كلمة مرور قوية سيتم استخدامها لتشفير ملف مجال النشر الموثوق به. يجب تحديد كلمة المرور هذه عند استيراد TPD إلى مؤسسة البريد الإلكتروني المستندة إلى السحابة.

### <a name="step-2-use-the-exchange-management-shell-to-import-the-tpd-to-exchange-online"></a>الخطوة 2: استخدم Exchange Management Shell لاستيراد TPD Exchange Online

بعد تصدير TPD إلى ملف XML، يجب استيراده إلى Exchange Online. عند استيراد TPD، يتم أيضا استيراد قوالب AD RMS الخاصة مؤسستك. عند استيراد أول TPD، يصبح TPD الافتراضي لمنظمتك المستندة إلى السحابة. إذا قمت باستيراد TPD آخر، يمكنك استخدام المفتاح **الافتراضي** لجعله TPD الافتراضي المتوفر للمستخدمين.

لاستيراد TPD، تشغيل الأمر التالي في Windows PowerShell:

```powershell
Import-RMSTrustedPublishingDomain -FileData ([System.IO.File]::ReadAllBytes('<path to exported TPD file>')) -Name "<name of TPD>" -ExtranetLicensingUrl <URL> -IntranetLicensingUrl <URL>
```

يمكنك الحصول على قيم معلمات _ExtranetLicensingUrl_ _وUrnetLicensingUrl_ في وحدة خدمات إدارة حقوق Active Directory التحكم. حدد كتلة AD RMS في شجرة وحدة التحكم. يتم عرض عناوين URL للترخيص في جزء النتائج. يتم استخدام عناوين URL هذه بواسطة عملاء البريد الإلكتروني عند الحاجة إلى فك تشفير المحتوى ومتى Exchange Online يجب تحديد TPD الذي يجب استخدامه.

عند تشغيل هذا الأمر، ستطالب بكلمة مرور. أدخل كلمة المرور التي حددتها عند تصدير TPD من خادم AD RMS.

على سبيل المثال، يقوم الأمر التالي باستيراد TPD المسمى TPD المصدر باستخدام ملف XML الذي قمت بتصديره من خادم AD RMS وحفظه على سطح المكتب لحساب المسؤول. يتم استخدام معلمة الاسم لتحديد اسم ل TPD.

```powershell
Import-RMSTrustedPublishingDomain -FileData ([System.IO.File]::ReadAllBytes('C:\Users\Administrator\Desktop\ExportTPD.xml')) -Name "Exported TPD" -ExtranetLicensingUrl https://corp.contoso.com/_wmcs/licensing -IntranetLicensingUrl https://rmsserver/_wmcs/licensing
```

للحصول على معلومات مفصلة حول بناء الجملة والمعلمات، راجع [Import-RMSTrustedPublishingDomain](/powershell/module/exchange/import-rmstrustedpublishingdomain).

#### <a name="how-do-you-know-that-you-successfully-imported-the-tpd"></a>كيف يمكنك معرفة أنك قمت باستيراد TPD بنجاح؟

للتحقق من أنك قمت باستيراد TPD بنجاح، يمكنك تشغيل الأمر **Cmdlet Get-RMSTrustedPublishingDomain** لاسترداد TPDs في مؤسستك Exchange Online. للحصول على التفاصيل، راجع الأمثلة في [Get-RMSTrustedPublishingDomain](/powershell/module/exchange/get-rmstrustedpublishingdomain).

### <a name="step-3-use-the-exchange-management-shell-to-distribute-an-ad-rms-rights-policy-template"></a>الخطوة 3: استخدام Exchange Management Shell لتوزيع قالب نهج حقوق AD RMS

بعد استيراد TPD، يجب التأكد من توزيع قالب نهج حقوق AD RMS. يكون القالب الموزع مرئيا Outlook على ويب المستخدمين (المعروفين سابقا باسم Outlook Web App)، الذين يمكنهم بعد ذلك تطبيق القوالب على رسالة بريد إلكتروني.

لإرجاع قائمة بكل القوالب المضمنة في TPD الافتراضي، يمكنك تشغيل الأمر التالي:

```powershell
Get-RMSTemplate -Type All | fl
```

إذا كانت قيمة المعلمة _Type_ هي `Archived`، فإن القالب غير مرئي للمستخدمين. تتوفر القوالب الموزعة فقط في TPD الافتراضي في Outlook على ويب.

لتوزيع قالب، قم بتشغيل الأمر التالي:

```powershell
Set-RMSTemplate -Identity "<name of the template>" -Type Distributed
```

على سبيل المثال، يستورد الأمر التالي القالب سري للشركة.

```powershell
Set-RMSTemplate -Identity "Company Confidential" -Type Distributed
```

للحصول على معلومات مفصلة حول بناء الجملة والمعلمات، راجع [Get-RMSTemplate](/powershell/module/exchange/get-rmstemplate) و [Set-RMSTemplate](/powershell/module/exchange/set-rmstemplate).

#### <a name="the-do-not-forward-template"></a>القالب "عدم إعادة توجيه"

عند استيراد TPD الافتراضي من مؤسستك في Exchange Online، يتم استيراد قالب نهج حقوق AD RMS يسمى **"** عدم إعادة توجيه". بشكل افتراضي، يتم توزيع هذا القالب عند استيراد TPD الافتراضي. لا يمكنك استخدام **الأمر Cmdlet Set-RMSTemplate** لتعديل **القالب "عدم إعادة** توجيه".

عند **تطبيق القالب "** عدم إعادة توجيه" على رسالة، يمكن للمستلمين الذين تم تناولهم في الرسالة فقط قراءة الرسالة. بالإضافة إلى ذلك، لا يمكن للمستلمين القيام بما يلي:

- إعادة توجيه الرسالة إلى شخص آخر.
- انسخ المحتوى من الرسالة.
- طباعة الرسالة.

> [!IMPORTANT]
> لا **يمكن أن** يمنع القالب "عدم إعادة توجيه" المعلومات في رسالة من نسخها باستخدام برامج التقاط الشاشة أو الكاميرات أو المستخدمين الذين يحولون المعلومات يدويا

يمكنك إنشاء قوالب نهج حقوق AD RMS إضافية على خادم AD RMS في مؤسستك المحلية لتلبية متطلبات حماية IRM. إذا قمت بإنشاء قوالب نهج حقوق AD RMS إضافية، يجب تصدير TPD من خادم AD RMS الموجود في الموقع مرة أخرى وتحديث TPD في مؤسسة البريد الإلكتروني المستندة إلى السحابة.

#### <a name="how-do-you-know-that-you-successfully-distributed-the-ad-rms-rights-policy-template"></a>كيف يمكنك معرفة أنك قمت بتوزيع قالب نهج حقوق AD RMS بنجاح؟

للتحقق من أنك قمت بتوزيع قالب نهج حقوق AD RMS بنجاح، قم بتشغيل الأمر **Cmdlet Get-RMSTemplate** للتحقق من خصائص القالب. للحصول على التفاصيل، راجع الأمثلة في [Get-RMSTemplate](/powershell/module/exchange/get-rmstemplate).

### <a name="step-4-use-the-exchange-management-shell-to-enable-irm"></a>الخطوة 4: استخدام Exchange Management Shell لتمكين إدارة المعلومات (IRM)

بعد استيراد TPD وتوزيع قالب نهج حقوق AD RMS، قم بتشغيل الأمر التالي لتمكين IRM لمنظمه البريد الإلكتروني المستندة إلى السحابة.

```powershell
Set-IRMConfiguration -InternalLicensingEnabled $true
```

للحصول على معلومات مفصلة حول بناء الجملة والمعلمات، راجع [Set-IRMConfiguration](/powershell/module/exchange/set-irmconfiguration).

#### <a name="how-do-you-know-that-you-successfully-enabled-irm"></a>كيف يمكنك معرفة أنك قمت بتمكين IRM بنجاح؟

للتحقق من أنك قمت بتمكين إدارة حقوق المعلومات (IRM) بنجاح، قم بتشغيل [الأمر Cmdlet Get-IRMConfiguration](/powershell/module/exchange/get-irmconfiguration) للتحقق من تكوين IRM في Exchange Online المؤسسة.

## <a name="how-do-you-know-this-task-worked"></a>كيف يمكنك معرفة كيفية عمل هذه المهمة؟
<a name="sectionSection2"> </a>

للتحقق من أنك قمت باستيراد TPD وتمكين IRM بنجاح، فتحقق مما يلي:

- استخدم **الأمر Cmdlet Test-IRMConfiguration** لاختبار وظائف IRM. للحصول على التفاصيل، راجع "المثال 1" في [Test-IRMConfiguration](/powershell/module/exchange/test-irmconfiguration).

- إنشاء رسالة جديدة في Outlook على ويب حماية إدارة حقوق المعلومات (IRM) عن طريق تحديد الخيار تعيين الأذونات من القائمة الموسعة (![أيقونة خيارات إضافية).).](../media/ITPro-EAC-MoreOptionsIcon.gif)
