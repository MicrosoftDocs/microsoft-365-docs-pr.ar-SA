---
title: مقارنة خطط Microsoft Defender لنقطة النهاية
description: مقارنة Defender لنقطة النهاية الخطة 1 بالخطة 2. تعرف على الاختلافات بين الخطط وحدد الخطة التي تناسب احتياجات مؤسستك.
keywords: Defender لنقطة النهاية، الحماية المتقدمة من التهديدات، حماية نقطة النهاية
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: ITPro
ms.topic: overview
ms.date: 06/17/2022
ms.prod: m365-security
ms.technology: mdep1
ms.localizationpriority: medium
ms.reviewer: shlomi, efratka
f1.keywords: NOCSH
ms.collection:
- M365-security-compliance
- m365initiative-defender-endpoint
ms.openlocfilehash: 00db46643d3f2b49003194075c44970a20ba83e9
ms.sourcegitcommit: 7ac54e1952383d5cd5f084c6a9d247eb747d4904
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 06/17/2022
ms.locfileid: "66139420"
---
# <a name="compare-microsoft-defender-for-endpoint-plans"></a>مقارنة خطط Microsoft Defender لنقطة النهاية

Microsoft Defender لنقطة النهاية هو نظام أساسي لأمان نقطة نهاية المؤسسة مصمم لمساعدة شبكات المؤسسة على منع التهديدات المتقدمة واكتشافها والتحقيق فيها والاستجابة لها. يوفر Defender لنقطة النهاية حماية متقدمة من التهديدات تتضمن مكافحة الفيروسات ومكافحة البرامج الضارة والتخفيف من برامج الفدية الضارة والمزيد، جنبا إلى جنب مع الإدارة المركزية وإعداد التقارير. يمكنك الاختيار من بين الخيارات التالية Microsoft Defender لنقطة النهاية:

- [الخطة 1 من Microsoft Defender لنقطة النهاية](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Defender for Endpoint الخطة 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [إدارة الثغرات الأمنية في Microsoft Defender](../defender-vulnerability-management/index.yml)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

يمكنك استخدام هذه المقالة للمساعدة في توضيح الحماية التي توفرها الميزات المختلفة المتوفرة في Defender for Endpoint Plan 1 و Defender for Endpoint Plan 2 والوظيفة الإضافية الجديدة لإدارة الثغرات الأمنية في Defender.

## <a name="compare-defender-for-endpoint-plans"></a>مقارنة خطط Defender لنقطة النهاية

يلخص الجدول التالي ما هو مضمن في كل خطة Defender لنقطة النهاية.

| الخطة | ما هو مضمن |
|:---|:---|
| [Defender for Endpoint الخطة 1](defender-endpoint-plan-1.md) | <ul><li>[حماية الجيل التالي](defender-endpoint-plan-1.md#next-generation-protection) (بما في ذلك مكافحة البرامج الضارة ومكافحة الفيروسات)</li><li>[قواعد تقليل الأجزاء المعرضة للهجوم](defender-endpoint-plan-1.md#attack-surface-reduction)</li><li> [إجراءات الاستجابة اليدوية](defender-endpoint-plan-1.md#manual-response-actions)</li><li>[الإدارة المركزية](defender-endpoint-plan-1.md#centralized-management)</li><li>[تقارير الأمان](defender-endpoint-plan-1.md#reporting)</li><li>[واجهات برمجه التطبيقات](defender-endpoint-plan-1.md#apis)</li><li>[دعم أجهزة Windows 10 وiOS وAndroid OS وأجهزة macOS](defender-endpoint-plan-1.md#cross-platform-support)</li></ul>|
| [Defender لنقطة النهاية الخطة 2](microsoft-defender-endpoint.md) | جميع إمكانيات Defender for Endpoint Plan 1، بالإضافة إلى:<ul><li>[اكتشاف الجهاز](device-discovery.md)</li><li>[بيانات الجهاز](machines-view-overview.md)</li><li>[قدرات إدارة الثغرات الأمنية في Core Defender](../defender-vulnerability-management/defender-vulnerability-management-capabilities.md)</li><li>[تحليلات التهديدات](threat-analytics.md)</li><li>[التحقيق التلقائي والاستجابة (AIR)](automated-investigations.md)</li><li>[الصيد المتقدم](advanced-hunting-overview.md)</li><li>[الكشف عن نقطة النهاية والاستجابة لها](overview-endpoint-detection-response.md)</li><li>[خبراء المخاطر في Microsoft](microsoft-threat-experts.md)</li><li>دعم [الأنظمة الأساسية Windows](configure-endpoints.md) (العميل والخادم) [والأنظمة الأساسية غير Windows](configure-endpoints-non-windows.md) (macOS وiOS وAndroid وLinux)</li></ul> |
| [الوظيفة الإضافية Defender Vulnerability Management](../defender-vulnerability-management/defender-vulnerability-management-capabilities.md) | إدارة الثغرات الأمنية الإضافية ل Defender لنقطة النهاية الخطة 2:<ul><li>[تقييم خطوط الأمان الأساسية](../defender-vulnerability-management/tvm-security-baselines.md)</li><li>[حظر التطبيقات المعرضة للخطر](../defender-vulnerability-management/tvm-block-vuln-apps.md)</li><li>[ملحقات المستعرض](../defender-vulnerability-management/tvm-browser-extensions.md)</li><li>[تقييم الشهادات الرقمية](../defender-vulnerability-management/tvm-certificate-inventory.md)</li><li>[تحليل مشاركة الشبكة](../defender-vulnerability-management/tvm-network-share-assessment.md)</li><li>دعم [الأنظمة الأساسية Windows](configure-endpoints.md) (العميل والخادم) [والأنظمة الأساسية غير Windows](configure-endpoints-non-windows.md) (macOS وiOS وAndroid وLinux)</li></ul> |

## <a name="mixed-licensing-scenarios"></a>سيناريوهات الترخيص المختلط

لنفترض أن مؤسستك تستخدم مزيجا من اشتراكات أمان نقطة النهاية من Microsoft، مثل Defender لنقطة النهاية الخطة 1 و Defender للخطة 2 لنقطة النهاية. **حاليا، يقوم اشتراك أمان نقطة نهاية Microsoft الأعلى وظيفية بتعيين تجربة المستأجر الخاص بك**. في هذا المثال، ستكون تجربة المستأجر الخاصة بك هي Defender for Endpoint Plan 2 لجميع المستخدمين.

ومع ذلك، **يمكنك الاتصال بالدعم وطلب تجاوز لتجربة المستأجر**. أي، يمكنك طلب تجاوز للاحتفاظ بتجربة Defender for Endpoint 1 لجميع المستخدمين. 

- للحصول على تفاصيل حول التراخيص وشروط المنتج، راجع [شروط الترخيص والمنتج لاشتراكات Microsoft 365](https://www.microsoft.com/licensing/terms/productoffering/Microsoft365/MCA).
- للحصول على معلومات حول كيفية الاتصال بالدعم، راجع [جهة الاتصال Microsoft Defender لنقطة النهاية الدعم](contact-support.md).

> [!TIP]
> إذا كانت مؤسستك شركة صغيرة أو متوسطة الحجم، فراجع المقالات التالية:
> - [ما هو Microsoft Defender for Business؟](../defender-business/mdb-overview.md)
> - [مقارنة ميزات الأمان في خطط Microsoft 365 للشركات الصغيرة والمتوسطة الحجم](../defender-business/compare-mdb-m365-plans.md).

## <a name="start-a-trial"></a>بدء إصدار تجريبي

- لتجربة Defender لنقطة النهاية الخطة 1، تفضل بزيارة [https://aka.ms/mdep1trial](https://aka.ms/mdep1trial).
- لتجربة Defender لنقطة النهاية الخطة 2، تفضل بزيارة [https://aka.ms/MDEp2OpenTrial](https://aka.ms/MDEp2OpenTrial).
- لتجربة الوظيفة الإضافية إدارة الثغرات الأمنية في Microsoft Defender، تفضل بزيارة [https://aka.ms/AddonPreviewTrial](https://aka.ms/AddonPreviewTrial). 

## <a name="see-also"></a>راجع أيضًا

- [Microsoft Defender for Business](../defender-business/mdb-overview.md) (حماية نقطة النهاية للشركات الصغيرة والمتوسطة الحجم)