---
title: إلحاق أجهزة macOS في نظرة عامة على Microsoft 365
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
ms.openlocfilehash: 59ccb78060c7749f5690015dc4bab948a88e5222
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/06/2022
ms.locfileid: "66630027"
---
# <a name="onboard-macos-devices-into-microsoft-365-overview"></a>إلحاق أجهزة macOS في نظرة عامة على Microsoft 365

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

يجب أن تتم إدارة أجهزة macOS بالفعل من خلال Intune أو JAMF Pro.
 
- لإلحاق Intune، راجع [دليل النشر: إدارة أجهزة macOS في Microsoft Intune](/mem/intune/fundamentals/deployment-guide-platform-macos) [وتسجيل جهاز Mac باستخدام Intune Company Portal](/mem/intune/user-help/enroll-your-device-in-intune-macos-cp). 
- للإلحاق ب JAMF Pro، راجع [دليل مسؤولي JAMF Pro](https://www.jamf.com/resources/product-documentation/jamf-pro-administrators-guide/) [ودليل التثبيت والتكوين JAMF Pro ل Mac](https://www.jamf.com/resources/product-documentation/jamf-pro-installation-guide-for-mac/)
<!--- Install the v95+ Edge browser on your macOS devices--> 

### <a name="supported-browsers"></a>المستعرضات المدعومة

تدعم نقطة النهاية DLP هذه المستعرضات على macOS Catalina 10.15 أو أعلى:

- Microsoft Edge (أحدث إصدار)
- Safari (أحدث إصدار، macOS فقط)
- Chrome (أحدث إصدار)
- Firefox (أحدث إصدار)

## <a name="licensing-guidance"></a>إرشادات الترخيص

راجع [إرشادات ترخيص Microsoft 365 لحماية المعلومات](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#information-protection-data-loss-prevention-for-exchange-online-sharepoint-online-and-onedrive-for-business).

## <a name="activities-that-can-be-restricted-on-macos"></a>الأنشطة التي يمكن تقييدها على macOS 

بمجرد إلحاق جهاز macOS في حلول Microsoft Purview، يمكنك مراقبة هذه الإجراءات وتقييدها باستخدام نهج منع فقدان البيانات (DLP).

**النسخ إلى وسائط USB القابلة للإزالة** – عند فرضها، يحظر هذا الإجراء نسخ الملفات المحمية أو نقلها أو نقلها من جهاز نقطة النهاية إلى وسائط USB القابلة للإزالة أو تدقيقها 

**النسخ إلى مشاركات الشبكة** – عند فرضه، يحظر هذا الإجراء نسخ الملفات المحمية أو نقلها من جهاز نقطة النهاية إلى أي مشاركة شبكة أو يحذر منها أو يدقق فيها 

**الطباعة** – عند فرضه، يحظر هذا الإجراء أو يحذر أو يدقق عند طباعة الملفات المحمية من جهاز نقطة النهاية 

**نسخ إلى الحافظة** – عند فرضه، يقوم هذا الإجراء بحظر أو تحذير أو تدقيق البيانات في ملف محمي يتم نسخه إلى حافظة على جهاز نقطة النهاية 

**التحميل إلى السحابة** – يحظر هذا الإجراء أو يحذر أو يدقق عندما يتم منع الملفات المحمية من تحميلها أو السماح بتحميلها إلى الخدمات السحابية استنادا إلى قائمة المجالات المسموح بها/غير المسموح بها في الإعدادات العمومية. عند تعيين هذا الإجراء للتحذير أو الحظر، يتم حظر المستعرضات الأخرى (المعرفة في قائمة المستعرضات غير مسموح بها ضمن الإعدادات العمومية) من الوصول إلى الملف. 

**يتم الوصول إليها بواسطة التطبيقات غير مسموح بها** – عند فرضه، يمنع هذا الإجراء التطبيقات الموجودة في قائمة التطبيقات غير مسموح بها (كما هو محدد في الإعدادات العمومية) من الوصول إلى الملفات المحمية على جهاز نقطة النهاية. نماذج السيناريوهات 

## <a name="onboarding-devices-into-device-management"></a>إلحاق الأجهزة بإدارة الأجهزة

يجب تمكين مراقبة الجهاز وإلحاق نقاط النهاية قبل أن تتمكن من مراقبة العناصر الحساسة وحمايتها على الجهاز. يتم تنفيذ كلا الإجراءين في مدخل التوافق في Microsoft Purview.

عندما تريد إلحاق الأجهزة التي لم يتم إلحاقها بعد، ستقوم بتنزيل البرنامج النصي المناسب ونشره على تلك الأجهزة. <!--Follow the [Onboarding devices procedure](endpoint-dlp-getting-started.md#onboarding-devices).-->

<!--If you already have devices onboarded into [Microsoft Defender for Endpoint](/windows/security/threat-protection/), they will already appear in the managed devices list.-->

1. افتح صفحة [إعدادات مدخل التوافق في Microsoft Purview](https://compliance.microsoft.com)  واختر **تمكين مراقبة الجهاز**.

   > [!NOTE]
   > على الرغم من أن تمكين إلحاق الجهاز يستغرق عادة حوالي 60 ثانية، يرجى السماح بما يصل إلى 30 دقيقة قبل التعامل مع دعم Microsoft.

2. افتح صفحة إعدادات مركز التوافق واختر **تشغيل مراقبة جهاز macOS**.

## <a name="next-steps"></a>الخطوات التالية

يلزم إدخال الأجهزة في حلول Microsoft Purview من أجل تلقي بيانات تتبع الاستخدام لأداة استشعار DLP وفرض نهج منع فقدان البيانات. 

الموضوع | الوصف
:---|:---
|[إلحاق أجهزة macOS وإلحاقها في حلول Microsoft Purview باستخدام Intune](device-onboarding-offboarding-macos-intune.md)|لأجهزة macOS التي تتم إدارتها من خلال Intune
|[إلحاق أجهزة macOS وإلغاء إلحاقها بحلول التوافق باستخدام Intune ل Microsoft Defender لعملاء نقطة النهاية](device-onboarding-offboarding-macos-intune-mde.md) |لأجهزة macOS التي تتم إدارتها من خلال Intune والتي تم توزيع Microsoft Defender لنقطة النهاية (MDE) إليها
|[إلحاق أجهزة macOS وإلحاقها في حلول Microsoft Purview باستخدام JAMF Pro](device-onboarding-offboarding-macos-jamfpro.md) | لأجهزة macOS التي تتم إدارتها من خلال JAMF Pro
|[إلحاق أجهزة macOS وإلغاء إلحاقها بحلول التوافق باستخدام JAMF Pro ل Microsoft Defender لعملاء نقطة النهاية](device-onboarding-offboarding-macos-jamfpro-mde.md)|لأجهزة macOS التي تتم إدارتها من خلال JAMF Pro والتي تم توزيع Microsoft Defender لنقطة النهاية (MDE) إليها


## <a name="related-topics"></a>المواضيع ذات الصلة

- [استخدام تفادي فقدان البيانات في نقطة النهاية](endpoint-dlp-using.md#using-endpoint-data-loss-prevention)
- [مصفوفة الدعم لتلميحات نهج DLP عبر تطبيقات Microsoft](dlp-policy-tips-reference.md#support-matrix-for-dlp-policy-tips-across-microsoft-apps)
