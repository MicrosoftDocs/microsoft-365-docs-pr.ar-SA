---
title: مجموعة أدوات معمل نشر Windows وOffice 365
f1.keywords:
- NOCSH
ms.author: greglin
author: greg-lindsay
manager: dougeby
ms.date: 11/18/2021
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.localizationpriority: medium
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom: ''
description: تعرف على مكان الوصول إلى Windows Office Deployment Lab Kit.
ms.openlocfilehash: 70a7e5d1c44e0fb80860ce0a1932b00616dcfe94
ms.sourcegitcommit: e911dd506ea066795e418daf7b84c1e11381a21c
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/19/2022
ms.locfileid: "64952677"
---
# <a name="windows-and-office-365-deployment-lab-kit"></a>مجموعة أدوات معمل نشر Windows وOffice 365

تم تصميم مجموعة مختبر نشر Windows Office 365 لمساعدتك على تخطيط واختبار والتحقق من صحة نشر وإدارة أجهزة سطح المكتب التي تعمل Windows 10 Enterprise أو Windows 11 Enterprise Microsoft 365 Apps for enterprise. تغطي المختبرات في مجموعة أدوات باستخدام Microsoft Endpoint Configuration Manager OneDrive Windows Autopilot والمزيد. يوصى بشدة باستخدام هذه المجموعة للمؤسسات التي تستعد لترقيات سطح المكتب. كبيئة معزولة، يعد المختبر مثاليا أيضا لاستكشاف تحديثات أداة النشر واختبار التشغيل التلقائي المرتبط بالنشر.

**Windows 10 والإصدارات Windows 11 من حزمة مختبر النشر متوفرة الآن للتنزيل المجاني في مركز تقييم Microsoft.**

[تنزيل Windows 11 مع مجموعة مختبر نشر Office 365](https://www.microsoft.com/evalcenter/evaluate-windows-11-office-365-lab-kit)<br>
[تنزيل Windows 10 مع مجموعة مختبر نشر Office 365](https://www.microsoft.com/evalcenter/evaluate-lab-kit)

## <a name="a-complete-lab-environment"></a>بيئة معملية كاملة

يوفر لك المختبر بيئة مختبر ظاهرية تم توفيرها تلقائيا، بما في ذلك عملاء سطح المكتب المنضمين إلى المجال، ووحدة تحكم بالمجال، وبوابة إنترنت، ومثيل Configuration Manager تم تكوينه بالكامل. تتضمن المختبرات إصدارات التقييم للمنتجات التالية:

|Windows 10 Lab|Windows 11 Lab|
|---|---|
|Windows 10 Enterprise، الإصدار 21H1|Windows 11 Enterprise|
|Microsoft Endpoint Configuration Manager، إصدار 2103|Microsoft Endpoint Configuration Manager، الإصدار 2111|
|Windows Assessment and Deployment Kit for Windows 10|Windows مجموعة أدوات التقييم والتوزيع Windows 11|
|Windows Server 2019|Windows Server 2022|

كما تم تصميم المختبرات لتكون متصلة بالمختبرات من أجل:

- Microsoft 365 E5
- Microsoft 365 Apps for enterprise
- Office 365 E5 مع Enterprise Mobility + Security (EMS)

## <a name="step-by-step-labs"></a>مختبرات مفصلة خطوة بخطوة

تنقلك دلائل المختبر التفصيلية من خلال سيناريوهات توزيع وإدارة متعددة. تم تحديث المختبرات لأحدث إصدارات Intune و Configuration Manager. ملاحظة: يتوفر الآن إصدار Windows 11 جديد من المختبر. تتضمن دلائل المختبر السيناريوهات التالية:

### <a name="plan-and-prepare-infrastructure"></a>تخطيط البنية الأساسية وإعدادها

- بوابة إدارة السحابة
- إرفاق المستأجر والإدارة المشتركة
- تحليلات نقطة النهاية
- تحسين تسليم التحديث

### <a name="deploy-windows"></a>نشر Windows

- تسلسلات مهام نشر نظام التشغيل في Configuration Manager
- Windows Autopilot

### <a name="service-windows"></a>Windows الخدمة

- Windows الخدمة باستخدام نهج المجموعة
- Windows الخدمة باستخدام Microsoft Intune
- Windows الخدمة مع Configuration Manager

### <a name="deploy-microsoft-365-apps-for-enterprise"></a>نشر Microsoft 365 Apps for enterprise

- النشر المدار على السحابة
- النشر المدار محليا
- Microsoft 365 Apps for enterprise النشر على الأجهزة غير المتصلة ب AD
- النشر المدار على مستوى المؤسسة باستخدام Configuration Manager
- النشر المدار على مستوى المؤسسة باستخدام Microsoft Intune
- Microsoft 365 Apps for enterprise الخدمة باستخدام Configuration Manager
- Microsoft 365 Apps for enterprise الخدمة باستخدام Intune
- توزيع وإدارة LOB مع Microsoft Intune
- نشر Microsoft Teams
- عوامل تصفية التعيين

### <a name="managing-microsoft-edge"></a>إدارة Microsoft Edge

- توزيع Edge وتحديثه
- وضع IE
- إعداد صفحة علامة تبويب جديدة على مستوى المؤسسة

### <a name="security-and-compliance"></a>الأمان والتوافق

- Bitlocker
- برنامج الحماية من الفيروسات من Microsoft Defender
- Windows Hello للأعمال

> [!NOTE]
> الرجاء استخدام اتصال إنترنت واسع النطاق لتنزيل هذا المحتوى والسماح بما يقرب من 30 دقيقة للتوفير التلقائي. تتطلب بيئة المختبر ما لا يقل عن 16 غيغابايت من الذاكرة المتوفرة و150 غيغابايت من مساحة القرص الحرة. للحصول على الأداء الأمثل، يوصى بتوفير 32 غيغابايت من الذاكرة و300 غيغابايت من المساحة الحرة. تنتهي صلاحية مختبر Windows 10 في 16 مايو 2022. تنتهي صلاحية مختبر Windows 11 في 6 مايو 2022. سيتم نشر الإصدارات الجديدة قبل انتهاء الصلاحية.

## <a name="additional-guidance"></a>إرشادات إضافية

- [Windows موارد ووثائق نشر العميل](/windows/deployment)
- [مقاطع فيديو سلسلة توزيع سطح المكتب من Microsoft Mechanics](https://www.aka.ms/watchhowtoshift)
- [نشر نظام التشغيل Microsoft Endpoint Configuration Manager](/mem/configmgr/osd/understand/introduction-to-operating-system-deployment)
- [تاريخ نشر تطبيقات Microsoft 365](/deployoffice/deployment-guide-microsoft-365-apps)
- [بدء استخدام Intune](/intune/get-started-evaluation)

## <a name="related-resources"></a>الموارد ذات الصلة

- [تقديم Microsoft 365](https://www.microsoft.com/microsoft-365/default.aspx)
- [Microsoft 365 للأعمال](https://products.office.com/business/office)
- [تقديم Enterprise Mobility + Security](https://www.microsoft.com/cloud-platform/enterprise-mobility-security)
- [Windows 11 للأعمال](https://www.microsoft.com/windows/business)
