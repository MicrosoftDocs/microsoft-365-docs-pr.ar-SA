---
title: تهيئة أجهزة macOS في نظرة عامة على Microsoft 365
f1.keywords: NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: ''
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
search.appverid:
- MET150
description: التعرف على إلحاق أجهزة macOS في حلول التوافق
ms.openlocfilehash: 6cc3323a94ee609c3c6674c12eb99fad3f18f3b4
ms.sourcegitcommit: e911dd506ea066795e418daf7b84c1e11381a21c
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/19/2022
ms.locfileid: "64952700"
---
# <a name="onboard-macos-devices-into-microsoft-365-overview"></a>تهيئة أجهزة macOS في نظرة عامة على Microsoft 365

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

يمكن إلحاق أجهزة MacOS في حلول Microsoft Purview باستخدام إما Intune أو JAMF Pro. تختلف إجراءات الإلحاق استنادا إلى حل الإدارة الذي تستخدمه. إذا تم بالفعل إلحاق أجهزة macOS في Microsoft Defender لنقطة النهاية (MDE)، فهناك خطوات أقل. راجع [الخطوات التالية](#next-steps) للحصول على ارتباطات للإجراءات المناسبة لك.

**ينطبق على:**

- [منع فقدان بيانات نقطة النهاية (DLP)](./endpoint-dlp-learn-about.md)
- [إدارة المخاطر الداخلية](insider-risk-management.md)

## <a name="before-you-begin"></a>قبل البدء

قبل البدء باستخدام DLP لنقطة النهاية على أجهزة macOS (Catalina 10.15 أو أحدث)، يجب أن تتعرف على هذه المقالات:

- [التعرّف على تفادي فقدان بيانات نقطة النهاية](endpoint-dlp-learn-about.md)
- [للحصول على متطلبات إضافية لنشر Endpoint DLP، راجع البدء في تفادي فقدان البيانات على الأجهزة.](endpoint-dlp-getting-started.md)

إذا لم تكن على دراية ب DLP على الإطلاق، يجب أن تتعرف على هذه المقالات أيضا:

- [التعرّف على تفادي فقدان البيانات](dlp-learn-about-dlp.md#learn-about-data-loss-prevention)
- [التخطيط لمنع فقدان البيانات (DLP)](dlp-overview-plan-for-dlp.md#plan-for-data-loss-prevention-dlp)
- [مرجع نهج تفادي فقدان البيانات](dlp-policy-reference.md#data-loss-prevention-policy-reference)

إذا لم تكن على دراية ب Insider Risk، يجب أن تتعرف على هذه المقالات:

 - [إدارة المخاطر الداخلية](insider-risk-management.md)
 - [خطة لإدارة المخاطر الداخلية](insider-risk-management-plan.md#plan-for-insider-risk-management)

يجب أن تتم إدارة أجهزة macOS بالفعل من خلال Pro Intune أو JAMF.
 
- لإلحاق Intune، راجع [دليل النشر: إدارة أجهزة macOS في Microsoft Intune](/mem/intune/fundamentals/deployment-guide-platform-macos) [وتسجيل جهاز Mac باستخدام Intune Company Portal](/mem/intune/user-help/enroll-your-device-in-intune-macos-cp). 
- للإلحاق ب JAMF Pro راجع، [دليل مسؤولي PRO JAMF](https://www.jamf.com/resources/product-documentation/jamf-pro-administrators-guide/) و [JAMF Pro دليل التثبيت والتكوين ل Mac](https://www.jamf.com/resources/product-documentation/jamf-pro-installation-guide-for-mac/)
- تثبيت مستعرض v95+ Edge على أجهزة macOS 

## <a name="licensing-guidance"></a>إرشادات الترخيص

راجع Microsoft 365 [إرشادات الترخيص لحماية المعلومات](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#information-protection-data-loss-prevention-for-exchange-online-sharepoint-online-and-onedrive-for-business).

## <a name="activities-that-can-be-restricted-on-macos"></a>الأنشطة التي يمكن تقييدها على macOS 

بمجرد إلحاق جهاز macOS في حلول Microsoft Purview، يمكنك مراقبة هذه الإجراءات وتقييدها باستخدام نهج منع فقدان البيانات (DLP).

**النسخ إلى وسائط USB القابلة للإزالة** – عند فرضها، يحظر هذا الإجراء نسخ الملفات المحمية أو نقلها أو نقلها من جهاز نقطة النهاية إلى وسائط USB القابلة للإزالة أو تدقيقها 

**النسخ إلى مشاركات الشبكة** – عند فرضه، يحظر هذا الإجراء نسخ الملفات المحمية أو نقلها من جهاز نقطة النهاية إلى أي مشاركة شبكة أو يحذر منها أو يدقق فيها 

**الطباعة** – عند فرضه، يحظر هذا الإجراء أو يحذر أو يدقق عند طباعة الملفات المحمية من جهاز نقطة النهاية 

**نسخ إلى الحافظة** – عند فرضه، يقوم هذا الإجراء بحظر أو تحذير أو تدقيق البيانات في ملف محمي يتم نسخه إلى حافظة على جهاز نقطة النهاية 

**Upload إلى السحابة** – يحظر هذا الإجراء الملفات المحمية أو يحذر منها أو يدققها عندما يتم منع تحميل الملفات المحمية أو يسمح بتحميلها إلى الخدمات السحابية استنادا إلى قائمة المجالات المسموح بها/غير المسموح بها في الإعدادات العمومية. عند تعيين هذا الإجراء للتحذير أو الحظر، يتم حظر المستعرضات الأخرى (المعرفة في قائمة المستعرضات غير مسموح بها ضمن الإعدادات العمومية) من الوصول إلى الملف. 

**يتم الوصول إليها بواسطة التطبيقات غير مسموح بها** – عند فرضه، يمنع هذا الإجراء التطبيقات الموجودة في قائمة التطبيقات غير مسموح بها (كما هو محدد في الإعدادات العمومية) من الوصول إلى الملفات المحمية على جهاز نقطة النهاية. نماذج السيناريوهات 

## <a name="onboarding-devices-into-device-management"></a>إلحاق الأجهزة بإدارة الأجهزة

يجب تمكين مراقبة الجهاز وإلحاق نقاط النهاية قبل أن تتمكن من مراقبة العناصر الحساسة وحمايتها على الجهاز. يتم تنفيذ كلا الإجراءين في مدخل توافق Microsoft Purview.

عندما تريد إلحاق الأجهزة التي لم يتم إلحاقها بعد، ستقوم بتنزيل البرنامج النصي المناسب ونشره على تلك الأجهزة. <!--Follow the [Onboarding devices procedure](endpoint-dlp-getting-started.md#onboarding-devices).-->

<!--If you already have devices onboarded into [Microsoft Defender for Endpoint](/windows/security/threat-protection/), they will already appear in the managed devices list.-->

1. افتح صفحة **الإعدادات** [مدخل الامتثال ل Microsoft Purview](https://compliance.microsoft.com) واختر **تمكين مراقبة الجهاز**.

   > [!NOTE]
   > على الرغم من أن تمكين إلحاق الجهاز يستغرق عادة حوالي 60 ثانية، يرجى السماح بما يصل إلى 30 دقيقة قبل التعامل مع دعم Microsoft.

2. افتح صفحة إعدادات مركز التوافق واختر **تشغيل مراقبة جهاز macOS**.

## <a name="next-steps"></a>الخطوات التالية

يلزم إدخال الأجهزة في حلول Microsoft Purview من أجل تلقي بيانات تتبع الاستخدام لأداة استشعار DLP وفرض نهج منع فقدان البيانات. 

الموضوع | الوصف
:---|:---
|[إلحاق أجهزة macOS وإلحاقها في حلول Microsoft Purview باستخدام Intune](device-onboarding-offboarding-macos-intune.md)|لأجهزة macOS التي تتم إدارتها من خلال Intune
|[إلحاق أجهزة macOS وإلحاقها في حلول التوافق باستخدام Intune لعملاء Microsoft Defender لنقطة النهاية](device-onboarding-offboarding-macos-intune-mde.md) |لأجهزة macOS التي تتم إدارتها من خلال Intune والتي تم توزيع Microsoft Defender لنقطة النهاية (MDE) إليها
|[إلحاق أجهزة macOS وإلحاقها في حلول Microsoft Purview باستخدام JAMF Pro](device-onboarding-offboarding-macos-jamfpro.md) | لأجهزة macOS التي تتم إدارتها من خلال JAMF Pro
|[إلحاق أجهزة macOS وإلحاقها بحلول التوافق باستخدام PRO JAMF لعملاء Microsoft Defender لنقطة النهاية](device-onboarding-offboarding-macos-jamfpro-mde.md)|لأجهزة macOS التي تتم إدارتها من خلال PRO JAMF والتي تم توزيع Microsoft Defender لنقطة النهاية (MDE) عليها


## <a name="related-topics"></a>المواضيع ذات الصلة

- [استخدام تفادي فقدان البيانات في نقطة النهاية](endpoint-dlp-using.md#using-endpoint-data-loss-prevention)
- [مصفوفة الدعم لتلميحات نهج DLP عبر تطبيقات Microsoft](dlp-policy-tips-reference.md#support-matrix-for-dlp-policy-tips-across-microsoft-apps)
