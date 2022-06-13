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
description: تعرف على كيفية تكوين Rights Management المعلومات (IRM) في Exchange Online لاستخدام خادم خدمة Rights Management Active Directory (AD RMS).
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: dac33407a9a45da59d0b3a766ab8a695a0f5a076
ms.sourcegitcommit: 133bf9097785309da45df6f374a712a48b33f8e9
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 06/10/2022
ms.locfileid: "66018130"
---
# <a name="configure-irm-to-use-an-on-premises-ad-rms-server"></a>تكوين IRM لاستخدام خادم AD RMS

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

للاستخدام مع عمليات النشر المحلية، تستخدم Rights Management المعلومات (IRM) في Exchange Online خدمات Rights Management Active Directory (AD RMS)، وهي تقنية حماية المعلومات في Windows Server 2008 والإصدارات الأحدث. يتم تطبيق حماية IRM على البريد الإلكتروني عن طريق تطبيق قالب نهج حقوق AD RMS على رسالة بريد إلكتروني. يتم إرفاق الحقوق بالرسالة نفسها بحيث تحدث الحماية عبر الإنترنت ودون اتصال وداخل وخارج جدار حماية مؤسستك.

يوضح لك هذا الموضوع كيفية تكوين IRM لاستخدام خادم AD RMS. للحصول على معلومات حول استخدام تشفير رسائل Microsoft Purview مع Azure Active Directory وAzure Rights Management، راجع [الأسئلة المتداولة حول تشفير الرسائل](./ome-faq.yml).

لمعرفة المزيد حول IRM في Exchange Online، راجع [Rights Management المعلومات في Exchange Online](information-rights-management-in-exchange-online.md).

## <a name="what-do-you-need-to-know-before-you-begin"></a>ما الذي تحتاج إلى معرفته قبل البدء؟

- الوقت المقدر لإكمال هذه المهمة: 30 دقيقة

- يجب تعيين أذونات لك قبل أن تتمكن من تنفيذ هذا الإجراء أو الإجراءات. للاطلاع على الأذونات التي تحتاجها، راجع إدخال "المعلومات Rights Management" في [موضوع نهج المراسلة وأذونات التوافق](/Exchange/permissions/feature-permissions/policy-and-compliance-permissions).

- يجب أن يكون خادم AD RMS قيد التشغيل Windows Server 2008 أو إصدار أحدث. للحصول على تفاصيل حول كيفية نشر AD RMS، راجع [تثبيت نظام مجموعة AD RMS](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc726041(v=ws.11)).

- للحصول على تفاصيل حول كيفية تثبيت وتكوين Windows PowerShell والاتصال للخدمة، راجع [الاتصال إلى Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

- للحصول على معلومات حول اختصارات لوحة المفاتيح التي قد تنطبق على الإجراءات الواردة في هذا الموضوع، راجع [اختصارات لوحة المفاتيح لمركز إدارة Exchange في Exchange Online](/Exchange/accessibility/keyboard-shortcuts-in-admin-center).

> [!TIP]
> هل تواجه مشاكل؟ طلب المساعدة في منتديات Exchange. تفضل بزيارة المنتديات في [Exchange Server أو](https://go.microsoft.com/fwlink/p/?linkId=60612) [Exchange Online](https://go.microsoft.com/fwlink/p/?linkId=267542) أو [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkId=285351).

## <a name="how-do-you-do-this"></a>كيف يمكنك القيام بذلك؟
<a name="sectionSection1"> </a>

### <a name="step-1-use-the-ad-rms-console-to-export-a-trusted-publishing-domain-tpd-from-an-ad-rms-server"></a>الخطوة 1: استخدام وحدة تحكم AD RMS لتصدير مجال نشر موثوق به (TPD) من خادم AD RMS

الخطوة الأولى هي تصدير مجال نشر موثوق به (TPD) من خادم AD RMS المحلي إلى ملف XML. يحتوي TPD على الإعدادات التالية اللازمة لاستخدام ميزات RMS:

- شهادة أداة حماية الخادم (SLC) المستخدمة في توقيع الشهادات والتراخيص وتشفيرها

- عناوين URL المستخدمة للترخيص والنشر

- قوالب نهج حقوق AD RMS التي تم إنشاؤها باستخدام SLC المحدد ل TPD هذا

عند استيراد TPD، يتم تخزينه وحمايتها في Exchange Online.

1. افتح وحدة تحكم خدمات Rights Management Active Directory، ثم قم بتوسيع نظام مجموعة AD RMS.

2. في شجرة وحدة التحكم، قم بتوسيع **نهج الثقة**، ثم انقر فوق **"مجالات النشر الموثوق بها**".

3. في جزء النتائج، حدد شهادة المجال الذي تريد تصديره.

4. في جزء **"الإجراءات** "، انقر فوق **"تصدير مجال النشر الموثوق به**".

5. في مربع **ملف مجال النشر** ، انقر فوق **"حفظ باسم"** لحفظ الملف في موقع معين على الكمبيوتر المحلي. اكتب اسم ملف، وتأكد من تحديد `.xml` ملحق اسم الملف، ثم انقر فوق **"حفظ**".

6. في المربعين **"كلمة المرور** " و" **تأكيد كلمة المرور** "، اكتب كلمة مرور قوية سيتم استخدامها لتشفير ملف مجال النشر الموثوق به. سيتعين عليك تحديد كلمة المرور هذه عند استيراد TPD إلى مؤسسة البريد الإلكتروني المستندة إلى السحابة.

### <a name="step-2-use-the-exchange-management-shell-to-import-the-tpd-to-exchange-online"></a>الخطوة 2: استخدام Exchange Management Shell لاستيراد TPD إلى Exchange Online

بعد تصدير TPD إلى ملف XML، يجب استيراده إلى Exchange Online. عند استيراد TPD، يتم أيضا استيراد قوالب AD RMS الخاصة بالمؤسسة. عند استيراد أول TPD، يصبح TPD الافتراضي لمؤسستك المستندة إلى السحابة. إذا قمت باستيراد TPD آخر، يمكنك استخدام المفتاح **الافتراضي** لجعله TPD الافتراضي المتوفر للمستخدمين.

لاستيراد TPD، قم بتشغيل الأمر التالي في Exchange Online PowerShell:

```powershell
Import-RMSTrustedPublishingDomain -FileData ([System.IO.File]::ReadAllBytes('<path to exported TPD file>')) -Name "<name of TPD>" -ExtranetLicensingUrl <URL> -IntranetLicensingUrl <URL>
```

يمكنك الحصول على قيم معلمات _ExtranetLicensingUrl_ و _IntranetLicensingUrl_ في وحدة تحكم خدمات Rights Management Active Directory. حدد نظام مجموعة AD RMS في شجرة وحدة التحكم. يتم عرض عناوين URL للترخيص في جزء النتائج. يتم استخدام عناوين URL هذه من قبل عملاء البريد الإلكتروني عند الحاجة إلى فك تشفير المحتوى ومتى يحتاج Exchange Online إلى تحديد TPD الذي يجب استخدامه.

عند تشغيل هذا الأمر، ستتم مطالبتك بكلمة مرور. أدخل كلمة المرور التي حددتها عند تصدير TPD من خادم AD RMS.

على سبيل المثال، يقوم الأمر التالي باستيراد TPD المسمى TPD المصدر باستخدام ملف XML الذي قمت بتصديره من خادم AD RMS وحفظه على سطح المكتب لحساب المسؤول. يتم استخدام معلمة الاسم لتحديد اسم إلى TPD.

```powershell
Import-RMSTrustedPublishingDomain -FileData ([System.IO.File]::ReadAllBytes('C:\Users\Administrator\Desktop\ExportTPD.xml')) -Name "Exported TPD" -ExtranetLicensingUrl https://corp.contoso.com/_wmcs/licensing -IntranetLicensingUrl https://rmsserver/_wmcs/licensing
```

للحصول على معلومات مفصلة حول بناء الجملة والمعلمة، راجع [Import-RMSTrustedPublishingDomain](/powershell/module/exchange/import-rmstrustedpublishingdomain).

#### <a name="how-do-you-know-that-you-successfully-imported-the-tpd"></a>كيف تعرف أنك قمت باستيراد TPD بنجاح؟

للتحقق من أنك قمت باستيراد TPD بنجاح، قم بتشغيل **Get-RMSTrustedPublishingDomain** cmdlet لاسترداد TPDs في مؤسستك Exchange Online. للحصول على التفاصيل، راجع الأمثلة في [Get-RMSTrustedPublishingDomain](/powershell/module/exchange/get-rmstrustedpublishingdomain).

### <a name="step-3-use-the-exchange-management-shell-to-distribute-an-ad-rms-rights-policy-template"></a>الخطوة 3: استخدام Exchange Management Shell لتوزيع قالب نهج حقوق AD RMS

بعد استيراد TPD، يجب التأكد من توزيع قالب نهج حقوق AD RMS. يكون القالب الموزع مرئيا لمستخدمي Outlook على ويب (المعروف سابقا باسم Outlook Web App)، الذين يمكنهم بعد ذلك تطبيق القوالب على رسالة بريد إلكتروني.

لإرجاع قائمة بكافة القوالب المضمنة في TPD الافتراضي، قم بتشغيل الأمر التالي:

```powershell
Get-RMSTemplate -Type All | fl
```

إذا كانت قيمة معلمة _النوع_ ، `Archived`فلن يكون القالب مرئيا للمستخدمين. تتوفر القوالب الموزعة فقط في TPD الافتراضي في Outlook على ويب.

لتوزيع قالب، قم بتشغيل الأمر التالي:

```powershell
Set-RMSTemplate -Identity "<name of the template>" -Type Distributed
```

على سبيل المثال، يقوم الأمر التالي باستيراد القالب "سرية الشركة".

```powershell
Set-RMSTemplate -Identity "Company Confidential" -Type Distributed
```

للحصول على معلومات مفصلة حول بناء الجملة والمعلمة، راجع [Get-RMSTemplate](/powershell/module/exchange/get-rmstemplate) و [Set-RMSTemplate](/powershell/module/exchange/set-rmstemplate).

#### <a name="the-do-not-forward-template"></a>القالب "عدم إعادة التوجيه"

عند استيراد TPD الافتراضي من مؤسستك المحلية إلى Exchange Online، يتم استيراد قالب نهج حقوق AD RMS يسمى **"عدم إعادة التوجيه**". بشكل افتراضي، يتم توزيع هذا القالب عند استيراد TPD الافتراضي. لا يمكنك استخدام **Set-RMSTemplate** cmdlet لتعديل القالب **"عدم إعادة التوجيه** ".

عند تطبيق القالب **"عدم إعادة التوجيه** " على رسالة، يمكن فقط للمستلمين الذين تمت مخاطبتها في الرسالة قراءة الرسالة. بالإضافة إلى ذلك، لا يمكن للمستلمين القيام بما يلي:

- إعادة توجيه الرسالة إلى شخص آخر.
- نسخ المحتوى من الرسالة.
- طباعة الرسالة.

> [!IMPORTANT]
> لا يمكن أن يمنع القالب **"عدم إعادة توجيه** " نسخ المعلومات الموجودة في رسالة باستخدام برامج التقاط الشاشة أو الكاميرات أو المستخدمين التابعين لجهة خارجية الذين يقومون بنسخ المعلومات يدويا

يمكنك إنشاء قوالب نهج حقوق AD RMS إضافية على خادم AD RMS في مؤسستك المحلية لتلبية متطلبات حماية IRM. إذا قمت بإنشاء قوالب نهج حقوق AD RMS إضافية، يجب تصدير TPD من خادم AD RMS المحلي مرة أخرى وتحديث TPD في مؤسسة البريد الإلكتروني المستندة إلى السحابة.

#### <a name="how-do-you-know-that-you-successfully-distributed-the-ad-rms-rights-policy-template"></a>كيف تعرف أنك قمت بتوزيع قالب نهج حقوق AD RMS بنجاح؟

للتحقق من توزيع قالب نهج حقوق AD RMS بنجاح، قم بتشغيل **Get-RMSTemplate** cmdlet للتحقق من خصائص القالب. للحصول على التفاصيل، راجع الأمثلة في [Get-RMSTemplate](/powershell/module/exchange/get-rmstemplate).

### <a name="step-4-use-the-exchange-management-shell-to-enable-irm"></a>الخطوة 4: استخدام Exchange Management Shell لتمكين IRM

بعد استيراد TPD وتوزيع قالب نهج حقوق AD RMS، قم بتشغيل الأمر التالي لتمكين IRM لمؤسسة البريد الإلكتروني المستندة إلى السحابة.

```powershell
Set-IRMConfiguration -InternalLicensingEnabled $true
```

للحصول على معلومات مفصلة حول بناء الجملة والمعلمة، راجع [Set-IRMConfiguration](/powershell/module/exchange/set-irmconfiguration).

#### <a name="how-do-you-know-that-you-successfully-enabled-irm"></a>كيف تعرف أنك قمت بتمكين IRM بنجاح؟

للتحقق من قيامك بتمكين IRM بنجاح، قم بتشغيل [Get-IRMConfiguration](/powershell/module/exchange/get-irmconfiguration) cmdlet للتحقق من تكوين IRM في مؤسسة Exchange Online.

## <a name="how-do-you-know-this-task-worked"></a>كيف تعرف أن هذه المهمة قد عملت؟
<a name="sectionSection2"> </a>

للتحقق من أنك قمت باستيراد TPD بنجاح وتمكين IRM، قم بما يلي:

- استخدم **Cmdlet Test-IRMConfiguration** لاختبار وظيفة IRM. للحصول على التفاصيل، راجع "المثال 1" في [Test-IRMConfiguration](/powershell/module/exchange/test-irmconfiguration).

- قم بإنشاء رسالة جديدة في Outlook على ويب وحمايتها بواسطة IRM عن طريق تحديد خيار **تعيين الأذونات** من القائمة الموسعة (![أيقونة المزيد من الخيارات).](../media/ITPro-EAC-MoreOptionsIcon.gif)).
