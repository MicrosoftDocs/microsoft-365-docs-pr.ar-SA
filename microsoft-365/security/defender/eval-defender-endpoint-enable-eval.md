---
title: تمكين Microsoft Defender لتقييم نقطة النهاية
description: تمكين بيئة Microsoft 365 Defender التجريبية أو التجريبية، بما في ذلك التحقق من حالة الترخيص ونقاط نهاية التهيئة
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: macapara
author: mjcaparas
ms.date: 07/09/2021
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365solution-scenario
- m365solution-evalutatemtp
ms.topic: conceptual
ms.technology: m365d
ms.openlocfilehash: 846fd6854b8e2dcb408aaa55348380bb91c6b907
ms.sourcegitcommit: 6f3bc00a5cf25c48c61eb3835ac069e9f41dc4db
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 01/24/2022
ms.locfileid: "63574004"
---
# <a name="enable-microsoft-defender-for-endpoint-evaluation-environment"></a>تمكين بيئة تقييم Microsoft Defender لنقطة النهاية


سترشدك هذه المقالة عبر الخطوات اللازمة لإعداد بيئة التقييم ل Microsoft Defender لنقطة النهاية باستخدام أجهزة الإنتاج. 


> [!TIP]
> يأتي Microsoft Defender ل Endpoint أيضا مع معمل تقييم داخل المنتج حيث يمكنك إضافة أجهزة تم تكوينها مسبقا وتشغيل عمليات محاكاة لتقييم قدرات النظام الأساسي. يتضمن المعمل تجربة إعداد مبسطة يمكن أن تساعد على توضيح قيمة Microsoft Defender لنقطة النهاية بسرعة بما في ذلك إرشادات للعديد من الميزات مثل تحليلات الصيد والتهديدات المتقدمة. لمزيد من المعلومات، راجع [تقييم الإمكانات](../defender-endpoint/evaluation-lab.md). <br> الفرق الرئيسي بين الإرشادات المتوفرة في هذه المقالة ومعمل التقييم هو أن بيئة التقييم تستخدم أجهزة الإنتاج في حين يستخدم معمل التقييم أجهزة غير إنتاج. 

استخدم الخطوات التالية لتمكين تقييم Microsoft Defender لنقطة النهاية.

![خطوات لتمكين Microsoft Defender لنقطة النهاية في بيئة تقييم Microsoft Defender.](../../media/defender/m365-defender-endpoint-eval-enable-steps.png)

- [الخطوة 1. التحقق من حالة الترخيص](#step-1-check-license-state)
- [الخطوة 2. نقاط نهاية الألواح](#step-2-onboard-endpoints-using-any-of-the-supported-management-tools)


## <a name="step-1-check-license-state"></a>الخطوة 1. التحقق من حالة الترخيص

ستحتاج أولا إلى التحقق من حالة الترخيص للتحقق من توفيره بشكل صحيح. يمكنك القيام بذلك من خلال مركز الإدارة أو من خلال **مدخل Microsoft Azure**.


1. لعرض التراخيص، انتقل إلى مدخل **Microsoft Azure** وانتقل إلى قسم [ترخيص مدخل Microsoft Azure](https://portal.azure.com/#blade/Microsoft_AAD_IAM/LicensesMenuBlade/Products).

   ![صورة لصفحة ترخيص Azure.](../../media/defender/atp-licensing-azure-portal.png)

1. بدلا من ذلك، في مركز الإدارة، انتقل إلى **BillingSubscriptions** > .

    على الشاشة، سترى كل التراخيص التي تم توفيرها ووضعها **الحالي**.

    ![صورة لتراخيص الفوترة.](../../media/defender/atp-billing-subscriptions.png)

## <a name="step-2-onboard-endpoints-using-any-of-the-supported-management-tools"></a>الخطوة 2. نقاط نهاية الألواح باستخدام أي من أدوات الإدارة المعتمدة

بعد التحقق من توفير حالة الترخيص بشكل صحيح، يمكنك بدء تشغيل الأجهزة المجهزة للخدمة. 

لغرض تقييم Microsoft Defender ل Endpoint، نوصي باختيار جهازين Windows لإجراء التقييم عليها.

يمكنك اختيار استخدام أي من أدوات الإدارة المعتمدة، ولكن Intune يوفر التكامل الأمثل. لمزيد من المعلومات، راجع [تكوين Microsoft Defender لنقطة النهاية في Microsoft Intune](/mem/intune/protect/advanced-threat-protection-configure#enable-microsoft-defender-for-endpoint-in-intune).

يوضح [موضوع نشر](../defender-endpoint/deployment-strategy.md) الخطة الخطوات العامة التي تحتاج إلى اتخاذها لنشر Defender لنقطة النهاية.  

شاهد هذا الفيديو للحصول على نظرة عامة سريعة حول عملية التوفر وتعرف على الأدوات والأساليب المتوفرة.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4bGqr]

### <a name="onboarding-tool-options"></a>خيارات أدوات الboarding

يسرد الجدول التالي الأدوات المتوفرة استنادا إلى نقطة النهاية التي تحتاج إلى الاستناد إليها.

نقطة النهاية | خيارات الأدوات
:---|:---
**بالنسبة لنظام التشغيل** | [البرنامج النصي المحلي (](../defender-endpoint/configure-endpoints-script.md)ما يصل إلى 10 أجهزة[](../defender-endpoint/configure-endpoints-gp.md))، نهج المجموعة[، إدارة نقاط النهاية من Microsoft/ إدارة](../defender-endpoint/configure-endpoints-mdm.md) الأجهزة المحمولة، [Microsoft Endpoint Configuration Manager](../defender-endpoint/configure-endpoints-sccm.md)، [برامج VDI](../defender-endpoint/configure-endpoints-vdi.md) النصية، التكامل [مع Microsoft Defender for Cloud](../defender-endpoint/configure-server-endpoints.md#integration-with-azure-defender)
**macOS** | [البرامج النصية المحلية](../defender-endpoint/mac-install-manually.md)[، إدارة نقاط النهاية من Microsoft](../defender-endpoint/mac-install-with-intune.md)، [JAMF Pro](../defender-endpoint/mac-install-with-jamf.md)[، إدارة أجهزة المحمول](../defender-endpoint/mac-install-with-other-mdm.md)
**Linux Server** | [برنامج نصي محلي](../defender-endpoint/linux-install-manually.md)[، مهى](../defender-endpoint/linux-install-with-puppet.md)، [غير قابل للطي](../defender-endpoint/linux-install-with-ansible.md)
**iOS** | [مستند إلى التطبيق](../defender-endpoint/ios-install.md)
**Android** | [إدارة نقاط النهاية من Microsoft](../defender-endpoint/android-intune.md)



## <a name="next-step"></a>الخطوة التالية
[إعداد التجربة ل Microsoft Defender لنقطة النهاية](eval-defender-endpoint-pilot.md)
 
العودة إلى نظرة عامة حول [تقييم Microsoft Defender لنقطة النهاية](eval-defender-endpoint-overview.md)

العودة إلى النظرة العامة لتقييم التقييم [Microsoft 365 Defender](eval-overview.md)
