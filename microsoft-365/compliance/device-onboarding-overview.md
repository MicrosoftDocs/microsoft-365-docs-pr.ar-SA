---
title: إلحاق الأجهزة Windows 10 أو Windows 11 في نظرة عامة على Microsoft 365
f1.keywords:
- CSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: ''
audience: ITPro
ms.topic: conceptual
f1_keywords:
- ms.o365.cc.DLPLandingPage
ms.service: O365-seccomp
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
- m365solution-mip
- m365initiative-compliance
search.appverid:
- MET150
description: إلحاق الأجهزة Windows 10 وأجهزة Windows 11 في Microsoft 365
ms.openlocfilehash: 876bd3f2d825fc1b698d3c7b9a76b1c7f115aedf
ms.sourcegitcommit: 7e0094ddff54bcbe5d691dba58d4c4fb86f8b1a9
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 05/04/2022
ms.locfileid: "65187888"
---
# <a name="onboard-windows-10-and-windows-11-devices-into-microsoft-365-overview"></a>نظرة عامة حول إلحاق أجهزة Windows 10 وWindows 11 في Microsoft 365

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

**ينطبق على:**

- [منع فقدان بيانات نقطة النهاية (DLP)](./endpoint-dlp-learn-about.md)
- [إدارة المخاطر الداخلية](insider-risk-management.md)

يتطلب منع فقدان بيانات نقطة النهاية (DLP) وإدارة المخاطر الداخلية إلحاق Windows 10 Windows وأجهزة Windows 11 في الخدمة حتى يتمكنوا من إرسال بيانات المراقبة إلى الخدمات.
 
تسمح لك DLP لنقطة النهاية بمراقبة أجهزة Windows 10 أو Windows 11 والكشف عن وقت استخدام العناصر الحساسة ومشاركتها. يمنحك هذا الرؤية والتحكم الذي تحتاجه لضمان استخدامها وحمايتها بشكل صحيح، وللمساعدة على منع السلوك المحفوظ بالمخاطر الذي قد يعرضها للخطر. لمزيد من المعلومات حول جميع عروض DLP من Microsoft، راجع [التعرف على منع فقدان البيانات](dlp-learn-about-dlp.md). لمعرفة المزيد حول DLP لنقطة النهاية، راجع [التعرف على منع فقدان بيانات نقطة النهاية](endpoint-dlp-learn-about.md).

تستخدم إدارة المخاطر الداخلية النطاق الكامل للخدمة ومؤشرات الجهات الخارجية لمساعدتك على تحديد نشاط المستخدم المحفوفة بالمخاطر وفرزه والعمل عليه بسرعة. باستخدام سجلات من Microsoft 365 وMicrosoft Graph، تتيح لك إدارة المخاطر الداخلية تحديد نهج محددة لتحديد مؤشرات المخاطر واتخاذ إجراءات للتخفيف من هذه المخاطر. لمزيد من المعلومات، راجع [التعرف على إدارة المخاطر الداخلية](insider-risk-management.md).

تتم مشاركة إلحاق الجهاز عبر Microsoft 365 Microsoft Defender لنقطة النهاية (MDE). إذا قمت بالفعل بإلحاق الأجهزة ب MDE، فستظهر في قائمة الأجهزة المدارة ولا توجد خطوات أخرى ضرورية لإلحاق تلك الأجهزة المحددة. كما تقوم أجهزة الإلحاق في مركز التوافق أيضا بإلحاقها ب MDE.

## <a name="before-you-begin"></a>قبل البدء

### <a name="skusubscriptions-licensing"></a>ترخيص SKU/الاشتراكات

تحقق من متطلبات الترخيص [هنا](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#information-protection-data-loss-prevention-for-exchange-online-sharepoint-online-and-onedrive-for-business).

### <a name="permissions"></a>الأذونات

لتمكين إدارة الجهاز، يجب أن يكون الحساب الذي تستخدمه عضوا في أي من هذه الأدوار:

- مسؤول عمومي
- مسؤول الأمان
- مسؤول التوافق

إذا كنت تريد استخدام حساب مخصص لعرض إعدادات إدارة الجهاز، فيجب أن يكون في أحد الأدوار التالية:

- مسؤول عمومي
- مسؤول التوافق
- مسؤول بيانات التوافق
- القارئ العمومي

إذا كنت تريد استخدام حساب مخصص للوصول إلى صفحة الإلحاق/الإلحاق، فيجب أن يكون في أحد الأدوار التالية:

- مسؤول عمومي
- مسؤول التوافق

إذا كنت تريد استخدام حساب مخصص لتشغيل/إيقاف تشغيل مراقبة الجهاز، يجب أن يكون في أحد الأدوار التالية:

- مسؤول عمومي
- مسؤول التوافق

### <a name="prepare-your-windows-devices"></a>إعداد أجهزة Windows

تأكد من أن الأجهزة Windows التي تحتاج إلى إلحاقها تفي بهذه المتطلبات.

1. يجب أن يكون قيد التشغيل Windows 10 الإصدار x64 1809 أو إصدار أحدث أو Windows 11.

2. إصدار عميل مكافحة البرامج الضارة هو 4.18.2110 أو أحدث. تحقق من الإصدار الحالي من خلال فتح تطبيق أمن Windows، وحدد أيقونة الإعدادات، ثم حدد "حول". يتم سرد رقم الإصدار ضمن إصدار عميل مكافحة البرامج الضارة. التحديث إلى أحدث إصدار عميل مكافحة البرامج الضارة عن طريق تثبيت Windows Update KB4052623.

   > [!NOTE]
   > يجب ألا تكون أي من مكونات أمن Windows نشطة، ولكن يجب تمكين [الحماية في الوقت الحقيقي ومراقبة السلوك](/windows/security/threat-protection/microsoft-defender-antivirus/configure-real-time-protection-microsoft-defender-antivirus)).

3. يتم تثبيت تحديثات Windows التالية Windows 10 للأجهزة التي سيتم مراقبتها.

   > [!NOTE]
   > هذه التحديثات ليست شرطا مسبقا لإلحاق جهاز، ولكنها تحتوي على إصلاحات للمشاكل الهامة وبالتالي يجب تثبيتها قبل استخدام المنتج.
   >
    > - بالنسبة Windows 10 1809 - KB4559003 وKB4577069 وKB4580390
    > - بالنسبة Windows 10 1903 أو 1909 - KB4559004 وKB4577062 وKB4580386
    > - بالنسبة Windows 10 2004 - KB4568831، KB4577063

4. يجب أن تكون جميع الأجهزة واحدة من هذه:

   - [تم انضمام Microsoft Azure Active Directory (Azure AD)](/azure/active-directory/devices/concept-azure-ad-join)
   - [مُسجل عبر hybrid Azure AD](/azure/active-directory/devices/concept-azure-ad-join-hybrid)
   - [AAD (دليل Azure النشط) مسجل](/azure/active-directory/user-help/user-help-register-device-on-network)

5. تم تثبيت إصدار معتمد من Microsoft Office وتحديثه. للحصول على الحماية الأكثر قوة وتجربة المستخدم، تأكد من تثبيت Microsoft 365 Apps الإصدار 16.0.14701.0 أو الأحدث.
> [!NOTE]
   > - إذا كنت تقوم بتشغيل Office 365 - 4577063 KB مطلوبة.
   > - إذا كنت تستخدم خيار التحديث الشهري للمؤسسة لإصدارات Microsoft 365 Apps 2004-2008، فستحتاج إلى التحديث إلى الإصدار 2009 أو الإصدارات الأحدث. راجع [محفوظات التحديثات Microsoft 365 Apps (المدرجة حسب التاريخ)](/officeupdates/update-history-microsoft365-apps-by-date) للإصدارات الحالية. لمعرفة المزيد حول المشكلة المعروفة، راجع قسم مجموعة Office [من ملاحظات الإصدار لإصدارات خيار التحديث الحالي في عام 2020](/officeupdates/current-channel#version-2010-october-27).

6. إذا كانت لديك نقاط نهاية تستخدم وكيل جهاز للاتصال بالإنترنت، فاتبع الإجراءات في [تكوين إعدادات وكيل الجهاز والاتصال بالإنترنت حماية البيانات](device-onboarding-configure-proxy.md#configure-device-proxy-and-internet-connection-settings-for-information-protection).

## <a name="onboarding-windows-10-or-windows-11-devices"></a>إلحاق الأجهزة Windows 10 أو Windows 11

يجب تمكين مراقبة الجهاز وإلحاق نقاط النهاية قبل أن تتمكن من مراقبة العناصر الحساسة وحمايتها على الجهاز. يتم تنفيذ كلا الإجراءين في مدخل توافق Microsoft Purview.

عندما تريد إلحاق الأجهزة التي لم يتم إلحاقها بعد، ستقوم بتنزيل البرنامج النصي المناسب ونشره على تلك الأجهزة. اتبع إجراءات إلحاق الجهاز أدناه.

إذا كان لديك بالفعل أجهزة مضمنة في [Microsoft Defender لنقطة النهاية](/windows/security/threat-protection/)، فستظهر بالفعل في قائمة الأجهزة المدارة.

في سيناريو النشر هذا، ستقوم بإلحاق Windows 10 أو Windows 11 الأجهزة التي لم يتم إلحاقها بعد.

1. افتح مدخل [الامتثال ل Microsoft Purview](https://compliance.microsoft.com). اختر **مراقبة الجهاز الإعدادات** >  **Enable**.

   > [!NOTE]
   > على الرغم من أن تمكين إلحاق الجهاز يستغرق عادة حوالي 60 ثانية، يرجى السماح بما يصل إلى 30 دقيقة قبل التعامل مع دعم Microsoft.

2. افتح صفحة إعدادات "مركز التوافق" واختر **"تشغيل مراقبة الجهاز Windows**".

3. اختر **إدارة الأجهزة** لفتح قائمة **الأجهزة** . 

> [!NOTE]
> إذا قمت بنشر Microsoft Defender لنقطة النهاية مسبقا، فسيتم إدراج جميع الأجهزة التي تم إلحاقها أثناء هذه العملية في قائمة **الأجهزة**. ليست هناك حاجة لإلحاقها مرة أخرى.

4. اختر **"إلحاق"** لبدء عملية الإلحاق.

5. اختر الطريقة التي تريد نشرها على هذه الأجهزة الإضافية من قائمة **أسلوب النشر** ثم **قم بتنزيل الحزمة**.

6. اختر الإجراء المناسب الذي يجب اتباعه من الجدول أدناه:

الموضوع | الوصف
:---|:---
[إلحاق Windows 10 أو 11 جهازا باستخدام نهج المجموعة](device-onboarding-gp.md) | استخدم نهج المجموعة لنشر حزمة التكوين على الأجهزة.
[إلحاق Windows 10 أو 11 جهازا باستخدام Microsoft Endpoint Configuration Manager](device-onboarding-sccm.md) | يمكنك استخدام الإصدار 1606 من Microsoft Endpoint Configuration Manager (الفرع الحالي) أو الإصدار 1602 من Microsoft Endpoint Configuration Manager (الفرع الحالي) أو إصدار سابق لنشر حزمة التكوين على الأجهزة.
[إلحاق Windows 10 أو 11 جهازا باستخدام أدوات إدارة الجهاز الأجهزة المحمولة](device-onboarding-mdm.md) | استخدم أدوات إدارة الجهاز الجوال أو Microsoft Intune لنشر حزمة التكوين على الجهاز.
[إلحاق Windows 10 أو 11 جهازا باستخدام برنامج نصي محلي](device-onboarding-script.md) | تعرف على كيفية استخدام البرنامج النصي المحلي لنشر حزمة التكوين على نقاط النهاية.
[أجهزة البنية الأساسية لسطح المكتب الظاهري (VDI) غير الثابتة](device-onboarding-vdi.md) | تعرف على كيفية استخدام حزمة التكوين لتكوين أجهزة VDI.

## <a name="see-also"></a>راجع أيضًا

- [تعرّف على إدارة المخاطر الداخلية](insider-risk-management.md)
- [التعرّف على تفادي فقدان بيانات نقطة النهاية](endpoint-dlp-learn-about.md)
- [استخدام تفادي فقدان البيانات في نقطة النهاية](endpoint-dlp-using.md)
- [التعرّف على تفادي فقدان البيانات](dlp-learn-about-dlp.md)
- [إنشاء نهج DLP واختباره وضبطه](create-test-tune-dlp-policy.md)
- [بدء استخدام مستكشف النشاط](data-classification-activity-explorer.md)
- [مشكلات الأداء في Microsoft Defender لنقطة النهاية](/windows/security/threat-protection/)
- [أدوات وأساليب الإلحاق للأجهزة Windows 10](/windows/security/threat-protection/microsoft-defender-atp/configure-endpoints)
- [اشتراك Microsoft 365](https://www.microsoft.com/microsoft-365/compare-microsoft-365-enterprise-plans?rtc=1)
- [Azure AD الأجهزة المتصلة](/azure/active-directory/devices/concept-azure-ad-join)
- [تنزيل Microsoft Edge الجديدة استنادا إلى Chromium](https://support.microsoft.com/help/4501095/download-the-new-microsoft-edge-based-on-chromium)
