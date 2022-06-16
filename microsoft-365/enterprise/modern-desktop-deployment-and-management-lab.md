---
title: مجموعة أدوات معمل نشر Windows وOffice 365
f1.keywords:
- NOCSH
ms.author: aaroncz
author: cdmm12
manager: dougeby
ms.reviewer: alainme
ms.date: 05/11/2022
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.localizationpriority: medium
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom: ''
description: تعرف على مكان الوصول إلى Windows Office Deployment Lab Kit.
ms.openlocfilehash: 63ec41e1865647caac60aa6fe91f69ed6c878e74
ms.sourcegitcommit: 18bc521a88b7b521bccb0e69d02deac764218087
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 06/16/2022
ms.locfileid: "66115906"
---
# <a name="windows-and-office-365-deployment-lab-kit"></a>مجموعة أدوات معمل نشر Windows وOffice 365

تم تصميم مجموعة مختبر نشر Windows Office 365 لمساعدتك على تخطيط واختبار والتحقق من صحة نشر وإدارة أجهزة سطح المكتب التي تعمل Windows 10 Enterprise أو Windows 11 Enterprise Microsoft 365 Apps for enterprise. تغطي المختبرات في مجموعة أدوات باستخدام Microsoft Endpoint Configuration Manager OneDrive Windows Autopilot والمزيد. يوصى بشدة باستخدام هذه المجموعة للمؤسسات التي تستعد لترقيات سطح المكتب. كبيئة معزولة، يعد المختبر مثاليا أيضا لاستكشاف تحديثات أداة النشر واختبار التشغيل التلقائي المرتبط بالنشر.

هناك إصداران من المعمل متاحان للتنزيل المجاني:  

|Windows 10 Lab|Windows 11 Lab|
|---|---|
|[بيئة التمرين المعملي Win 10](https://download.microsoft.com/download/8/5/e/85e007b0-1f3e-460c-bd0a-5a8c6ec490b5/Win10_21H2_lab.zip)|[بيئة التمرين المعملي Win 11](https://download.microsoft.com/download/9/d/9/9d9e278e-a1ea-4704-85e1-cb24f3806f45/Win11_Lab_05.09.zip)|
|[Win 10 أدلة معملية](https://download.microsoft.com/download/8/5/e/85e007b0-1f3e-460c-bd0a-5a8c6ec490b5/Win10_21H2_guides.zip)|[دلائل التمرين المعملي ل Win 11](https://download.microsoft.com/download/9/d/9/9d9e278e-a1ea-4704-85e1-cb24f3806f45/Win11_Lab_Guides_05.09.zip)|

## <a name="a-complete-lab-environment"></a>بيئة معملية كاملة

يوفر لك المختبر بيئة مختبر ظاهرية تم توفيرها تلقائيا، بما في ذلك عملاء سطح المكتب المنضمين إلى المجال، ووحدة تحكم بالمجال، وبوابة إنترنت، ومثيل Configuration Manager تم تكوينه بالكامل. تتضمن المختبرات إصدارات التقييم للمنتجات التالية:

|Windows 10 Lab|Windows 11 Lab|
|---|---|
|Windows 10 Enterprise، الإصدار 21H2|Windows 11 Enterprise|
|Microsoft Endpoint Configuration Manager، الإصدار 2203|Microsoft Endpoint Configuration Manager، الإصدار 2203|
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
- Credential Guard لـ Windows Defender       
- حماية التطبيقات من Microsoft Defender     
- حماية الإستغلال لـ Windows Defender             
- التحكم في تطبيق Windows Defender   
- Microsoft Defender for Endpoint 


> [!NOTE]
> الرجاء استخدام اتصال إنترنت واسع النطاق لتنزيل هذا المحتوى والسماح بما يقرب من 30 دقيقة للتوفير التلقائي. تتطلب بيئة المختبر ما لا يقل عن 16 غيغابايت من الذاكرة المتوفرة و150 غيغابايت من مساحة القرص الحرة. للحصول على الأداء الأمثل، يوصى بتوفير 32 غيغابايت من الذاكرة و300 غيغابايت من المساحة الحرة. تنتهي صلاحية العملاء الظاهريين بعد 90 يوما من تنشيط المختبر. تنتهي صلاحية الخوادم الظاهرية في 11 سبتمبر 2022. سيتم نشر إصدارات جديدة من المختبرات قبل انتهاء الصلاحية. 

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
- [Windows للأعمال](https://www.microsoft.com/windows/business)
