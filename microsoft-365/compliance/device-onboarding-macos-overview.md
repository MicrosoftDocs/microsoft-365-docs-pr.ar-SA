---
title: أجهزة macOS المجهزة في Microsoft 365 عامة (معاينة)
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
description: تعرف على كيفية وضع أجهزة macOS في حلول التوافق
ms.openlocfilehash: 783179ae749ac7cd6de671435927ba5bbdbdacad
ms.sourcegitcommit: 9d563faeaa50b59b0b468dbb373d886e5270f58e
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/24/2022
ms.locfileid: "64387004"
---
# <a name="onboard-macos-devices-into-microsoft-365-overview-preview"></a>أجهزة macOS المجهزة في Microsoft 365 عامة (معاينة)

يمكن تكدس أجهزة MacOS في Microsoft 365 التوافق باستخدام إما Intune أو JAMF Pro. تختلف إجراءات التكهين استنادا إلى حل الإدارة الذي تستخدمه. إذا تم بالفعل استخدام أجهزة macOS في Microsoft Defender لنقطة النهاية (MDE)، فهناك خطوات أقل. راجع [الخطوات التالية](#next-steps) للحصول على ارتباطات إلى الإجراءات المناسبة لك.

**ينطبق على:**

- [منع فقدان بيانات نقطة النهاية (DLP)](./endpoint-dlp-learn-about.md)
- [إدارة مخاطر Insider](insider-risk-management.md#learn-about-insider-risk-management-in-microsoft-365)

## <a name="before-you-begin"></a>قبل البدء

قبل بدء استخدام Endpoint DLP على أجهزة macOS (Catalina 10.15 أو أي وقت لاحق)، يجب أن تطلع نفسك على المقالات التالية:

- [التعرف على منع فقدان بيانات نقطة النهاية](endpoint-dlp-learn-about.md#learn-about-microsoft-365-endpoint-data-loss-prevention)
- [بدء استخدام منع فقدان بيانات نقطة النهاية](endpoint-dlp-getting-started.md#get-started-with-endpoint-data-loss-prevention)

إذا لم تكن ملما باستخدام DLP على الإطلاق، يجب عليك التعرف على هذه المقالات أيضا:

- [التعرف على منع فقدان البيانات](dlp-learn-about-dlp.md#learn-about-data-loss-prevention)
- [التخطيط لمنع فقدان البيانات (DLP)](dlp-overview-plan-for-dlp.md#plan-for-data-loss-prevention-dlp)
- [مرجع نهج منع فقدان البيانات](dlp-policy-reference.md#data-loss-prevention-policy-reference)

إذا لم تكن ملما باستخدام Insider Risk، يجب أن تألف استخدام هذه المقالات:

 - [إدارة مخاطر Insider](insider-risk-management.md#learn-about-insider-risk-management-in-microsoft-365)
 - [التخطيط لإدارة مخاطر insider](insider-risk-management-plan.md#plan-for-insider-risk-management)

يجب أن تكون أجهزة macOS مدارة بالفعل من خلال Intune أو JAMF Pro.
 
- للالتحاق في Intune، راجع دليل النشر: إدارة أجهزة [macOS في](/mem/intune/fundamentals/deployment-guide-platform-macos) Microsoft Intune تسجيل [جهاز Mac](/mem/intune/user-help/enroll-your-device-in-intune-macos-cp) باستخدام Intune Company Portal. 
- للتركيب في JAMF Pro، راجع دليل مسؤولي [JAMF Pro](https://www.jamf.com/resources/product-documentation/jamf-pro-administrators-guide/) و [JAMF Pro دليل التكوين والتثبيت ل Mac](https://www.jamf.com/resources/product-documentation/jamf-pro-installation-guide-for-mac/)
- تثبيت مستعرض v95+ Edge على أجهزة macOS 

## <a name="licensing-guidance"></a>إرشادات الترخيص

راجع، [Microsoft 365 إرشادات الترخيص لحماية المعلومات](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#information-protection-data-loss-prevention-for-exchange-online-sharepoint-online-and-onedrive-for-business).

## <a name="activities-that-can-be-restricted-on-macos"></a>الأنشطة التي يمكن تقييدها على macOS 

بمجرد أن يتم تشغيل جهاز macOS في Microsoft 365 التوافق، يمكنك مراقبة هذه الإجراءات وتقييدها باستخدام سياسات منع فقدان البيانات (DLP).

**النسخ إلى وسائط USB** قابلة للإزالة – عند فرضها، يمنع هذا الإجراء نسخ الملفات المحمية أو نقلها أو نقلها من جهاز نقطة نهاية إلى وسائط USB قابلة للإزالة 

**النسخ إلى مشاركة** الشبكة – عند فرض هذا الإجراء، يمنع عملية نسخ الملفات المحمية أو نقلها أو يدقق فيها من جهاز نقطة نهاية إلى أي مشاركة على الشبكة 

**الطباعة** – عند فرضها، يتم حظر هذا الإجراء أو تحذيره أو تدقيقه عند طباعة الملفات المحمية من جهاز نقطة نهاية 

**نسخ إلى الحافظة** – عند فرضها، يمنع هذا الإجراء البيانات الموجودة في ملف محمي يتم نسخها إلى الحافظة على جهاز نقطة نهاية أو يحذر منها أو يدقق فيها 

**Upload** السحابة – تمنع عمليات الإجراء هذه أو تحذر أو تدققها عندما يتم منع الملفات المحمية من تحميلها أو السماح بتحميلها إلى الخدمات السحابية استنادا إلى قائمة المجالات المسموح بها/غير المسموح بها في الإعدادات العامة. عند تعيين هذا الإجراء للتحذير أو الحظر، يتم حظر المستعرضات الأخرى (المعرفة في قائمة المستعرضات غير المحظورة ضمن الإعدادات العامة) من الوصول إلى الملف. 

الوصول إليها بواسطة تطبيقات غير مسموح **بها – عند** فرضها، يمنع هذا الإجراء التطبيقات الموجودة في قائمة التطبيقات غير المدينة (كما هو محدد في الإعدادات العامة) من الوصول إلى الملفات المحمية على جهاز نقطة نهاية. نماذج السيناريوهات 

## <a name="onboarding-devices-into-device-management"></a>تشغيل الأجهزة في إدارة الأجهزة

يجب تمكين مراقبة الجهاز وإلوحاء نقاط النهاية قبل أن تتمكن من مراقبة العناصر الحساسة على جهاز وحمايتها. يتم كلا هذين الإجراءات في مدخل Microsoft 365 التوافق.

عندما تريد أن تقوم بتركب الأجهزة التي لم يتم تشغيلها بعد، يمكنك تنزيل البرنامج النصي المناسب ونشره على تلك الأجهزة. <!--Follow the [Onboarding devices procedure](endpoint-dlp-getting-started.md#onboarding-devices).-->

<!--If you already have devices onboarded into [Microsoft Defender for Endpoint](/windows/security/threat-protection/), they will already appear in the managed devices list.-->

1. افتح صفحة [مركز التوافق ل Microsoft](https://compliance.microsoft.com) **الإعدادات** **واختر تمكين مراقبة الجهاز**.

   > [!NOTE]
   > على الرغم من أن تمكين تشغيل الجهاز يستغرق عادة حوالي 60 ثانية، يرجى السماح بما يصل إلى 30 دقيقة قبل التفاعل مع دعم Microsoft.

2. افتح صفحة إعدادات مركز التوافق واختر **تشغيل مراقبة أجهزة macOS**.

## <a name="next-steps"></a>الخطوات التالية

إن وضع الأجهزة في Microsoft 365 حلول التوافق مطلوب لتلقي بيانات استخدام أدوات استشعار DLP وفرض سياسات منع فقدان البيانات. 

الموضوع | الوصف
:---|:---
|[أجهزة macOS التي يتم تشغيلها أو إيقاف تشغيلها في Microsoft 365 التوافق باستخدام Intune (معاينة)](device-onboarding-offboarding-macos-intune.md#onboard-and-offboard-macos-devices-into-microsoft-365-compliance-solutions-using-intune-preview)|بالنسبة إلى أجهزة macOS التي يتم إدارتها من خلال Intune
|[أجهزة macOS التي تعمل باللوح واللوح خارجها في حلول التوافق باستخدام Intune لعملاء Microsoft Defender لنقطة النهاية (معاينة)](device-onboarding-offboarding-macos-intune-mde.md#onboard-and-offboard-macos-devices-into-compliance-solutions-using-intune-for-microsoft-defender-for-endpoint-customers-preview) |بالنسبة إلى أجهزة macOS التي يتم إدارتها من خلال Intune Microsoft Defender لنقطة النهاية (MDE) التي تم نشرها عليها
|[أجهزة macOS التي يتم تشغيلها أو إيقاف تشغيلها في Microsoft 365 التوافق باستخدام JAMF Pro (معاينة)](device-onboarding-offboarding-macos-jamfpro.md#onboard-and-offboard-macos-devices-into-microsoft-365-compliance-solutions-using-jamf-pro-preview) | بالنسبة إلى أجهزة macOS التي يتم إدارتها من خلال JAMF Pro
|[أجهزة macOS التي يتم تشغيلها أو إيقاف تشغيلها في حلول التوافق باستخدام JAMF Pro لعملاء Microsoft Defender لنقطة النهاية (معاينة)](device-onboarding-offboarding-macos-jamfpro-mde.md#onboard-and-offboard-macos-devices-into-compliance-solutions-using-jamf-pro-for-microsoft-defender-for-endpoint-customers-preview)|بالنسبة إلى أجهزة macOS التي يتم إدارتها من خلال PRO JAMF التي تم نشرها Microsoft Defender لنقطة النهاية (MDE) عليها


## <a name="related-topics"></a>المواضيع ذات الصلة

- [استخدام منع فقدان البيانات في نقطة النهاية](endpoint-dlp-using.md#using-endpoint-data-loss-prevention)
- [مصفوفة الدعم لتلميحات نهج DLP عبر تطبيقات Microsoft](dlp-policy-tips-reference.md#support-matrix-for-dlp-policy-tips-across-microsoft-apps)
