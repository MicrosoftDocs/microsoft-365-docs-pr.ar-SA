---
title: تمكين تقييم Microsoft Defender لنقطة النهاية
description: تمكين بيئة الاختبار التجريبي أو الإصدار التجريبي Microsoft 365 Defender، بما في ذلك التحقق من حالة الترخيص ونقاط نهاية الإلحاق
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
ms.openlocfilehash: 2acde87daaff88ec9ce7458218919342a9f1edd8
ms.sourcegitcommit: ac0ae5c2888e2b323e36bad041a4abef196c9c96
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/12/2022
ms.locfileid: "64782490"
---
# <a name="enable-microsoft-defender-for-endpoint-evaluation-environment"></a>تمكين بيئة تقييم Microsoft Defender لنقطة النهاية


ستوجهك هذه المقالة خلال الخطوات المتعلقة بإعداد بيئة التقييم Microsoft Defender لنقطة النهاية باستخدام أجهزة الإنتاج. 


> [!TIP]
> تأتي Microsoft Defender لنقطة النهاية أيضا مع مختبر تقييم داخل المنتج حيث يمكنك إضافة أجهزة تم تكوينها مسبقا وتشغيل المحاكاة لتقييم قدرات النظام الأساسي. يأتي المختبر مع تجربة إعداد مبسطة يمكن أن تساعد في إظهار قيمة Microsoft Defender لنقطة النهاية بسرعة بما في ذلك إرشادات للعديد من الميزات مثل التتبع المتقدم وتحليلات التهديدات. لمزيد من المعلومات، راجع [تقييم القدرات](../defender-endpoint/evaluation-lab.md). <br> الفرق الرئيسي بين الإرشادات الواردة في هذه المقالة ومختبر التقييم هو أن بيئة التقييم تستخدم أجهزة الإنتاج بينما يستخدم مختبر التقييم أجهزة غير إنتاجية. 

استخدم الخطوات التالية لتمكين التقييم Microsoft Defender لنقطة النهاية.

:::image type="content" source="../../media/defender/m365-defender-endpoint-eval-enable-steps.png" alt-text="خطوات تمكين Microsoft Defender لنقطة النهاية في بيئة تقييم Microsoft Defender" lightbox="../../media/defender/m365-defender-endpoint-eval-enable-steps.png":::

- [الخطوة 1. التحقق من حالة الترخيص](#step-1-check-license-state)
- [الخطوة 2. نقاط نهاية الإلحاق](#step-2-onboard-endpoints-using-any-of-the-supported-management-tools)


## <a name="step-1-check-license-state"></a>الخطوة 1. التحقق من حالة الترخيص

ستحتاج أولا إلى التحقق من حالة الترخيص للتحقق من أنه تم توفيره بشكل صحيح. يمكنك القيام بذلك من خلال مركز الإدارة أو من خلال مدخل **Microsoft Azure**.


1. لعرض التراخيص، انتقل إلى **مدخل Microsoft Azure** وانتقل إلى [قسم ترخيص مدخل Microsoft Azure](https://portal.azure.com/#blade/Microsoft_AAD_IAM/LicensesMenuBlade/Products).

   :::image type="content" source="../../media/defender/atp-licensing-azure-portal.png" alt-text="صفحة ترخيص Azure في مدخل Microsoft 365 Defender" lightbox="../../media/defender/atp-licensing-azure-portal.png":::

1. بدلا من ذلك، في مركز الإدارة، انتقل إلى **BillingSubscriptions** > .

    على الشاشة، سترى جميع التراخيص المتوفرة وحالتها **الحالية**.

    :::image type="content" source="../../media/defender/atp-billing-subscriptions.png" alt-text="صفحة تراخيص الفوترة في مدخل Microsoft Azure" lightbox="../../media/defender/atp-billing-subscriptions.png":::
    

## <a name="step-2-onboard-endpoints-using-any-of-the-supported-management-tools"></a>الخطوة 2. إلحاق نقاط النهاية باستخدام أي من أدوات الإدارة المدعومة

بعد التحقق من توفير حالة الترخيص بشكل صحيح، يمكنك البدء في إلحاق الأجهزة إلى الخدمة. 

لغرض تقييم Microsoft Defender لنقطة النهاية، نوصي باختيار جهازين Windows لإجراء التقييم.

يمكنك اختيار استخدام أي من أدوات الإدارة المدعومة، ولكن يوفر Intune التكامل الأمثل. لمزيد من المعلومات، راجع [تكوين Microsoft Defender لنقطة النهاية في Microsoft Intune](/mem/intune/protect/advanced-threat-protection-configure#enable-microsoft-defender-for-endpoint-in-intune).

يوضح موضوع [نشر الخطة](../defender-endpoint/deployment-strategy.md) الخطوات العامة التي تحتاج إلى اتخاذها لنشر Defender لنقطة النهاية.  

شاهد هذا الفيديو للحصول على نظرة عامة سريعة حول عملية الإلحاق وتعرف على الأدوات والأساليب المتوفرة.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4bGqr]

### <a name="onboarding-tool-options"></a>خيارات أداة الإلحاق

يسرد الجدول التالي الأدوات المتوفرة استنادا إلى نقطة النهاية التي تحتاج إلى إلحاقها.

نقطه النهايه | خيارات الأدوات
:---|:---
**بالنسبة لنظام التشغيل** | [البرنامج النصي المحلي (ما يصل إلى 10 أجهزة)](../defender-endpoint/configure-endpoints-script.md) [نهج المجموعة](../defender-endpoint/configure-endpoints-gp.md) [إدارة نقاط النهاية من Microsoft/ الجوال إدارة الأجهزة](../defender-endpoint/configure-endpoints-mdm.md) [Microsoft Endpoint Configuration Manager](../defender-endpoint/configure-endpoints-sccm.md) [والبرامج النصية](../defender-endpoint/configure-endpoints-vdi.md) [ل VDI التكامل مع Microsoft Defender for Cloud](../defender-endpoint/configure-server-endpoints.md#integration-with-microsoft-defender-for-cloud)
**ماك** | [البرامج النصية المحلية](../defender-endpoint/mac-install-manually.md)، [إدارة نقاط النهاية من Microsoft](../defender-endpoint/mac-install-with-intune.md)، [PRO JAMF](../defender-endpoint/mac-install-with-jamf.md)، [إدارة الجهاز الجوال](../defender-endpoint/mac-install-with-other-mdm.md)
**Linux Server** | [البرنامج النصي المحلي](../defender-endpoint/linux-install-manually.md)،  [Puppet](../defender-endpoint/linux-install-with-puppet.md)،  [Ansible](../defender-endpoint/linux-install-with-ansible.md)
**دائره الرقابه الداخليه** | [مستند إلى التطبيق](../defender-endpoint/ios-install.md)
**الروبوت** | [إدارة نقاط النهاية من Microsoft](../defender-endpoint/android-intune.md)



## <a name="next-step"></a>الخطوة التالية
[إعداد الإصدار التجريبي Microsoft Defender لنقطة النهاية](eval-defender-endpoint-pilot.md)
 
العودة إلى النظرة العامة لتقييم [Microsoft Defender لنقطة النهاية](eval-defender-endpoint-overview.md)

العودة إلى النظرة العامة لتقييم [Microsoft 365 Defender](eval-overview.md)
