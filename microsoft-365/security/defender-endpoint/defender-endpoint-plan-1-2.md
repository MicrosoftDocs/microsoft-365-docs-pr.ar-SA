---
title: مقارنة خطط أمان نقطة النهاية من Microsoft
description: قارن خطط أمان نقاط النهاية من Microsoft، مثل Defender for Endpoint Plan 1 مع Defender for Endpoint Plan 2. تعرف على الاختلافات بين الخطط وحدد الخطة التي تناسب احتياجات مؤسستك.
keywords: Defender لنقطة النهاية، الحماية المتقدمة من التهديدات، حماية نقطة النهاية، أمان نقطة النهاية، أمان الجهاز، الأمان عبر الإنترنت
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: ITPro
ms.topic: overview
ms.date: 07/25/2022
ms.prod: m365-security
ms.technology: mdep1
ms.localizationpriority: medium
ms.reviewer: shlomi, efratka
f1.keywords: NOCSH
ms.collection:
- M365-security-compliance
- m365initiative-defender-endpoint
ms.openlocfilehash: 78d5e0c8b3b8405dcd4e0a33b315e000d661b7f4
ms.sourcegitcommit: af6c13d7ab1fe440dd45ce8cd3940774cdda66ef
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/25/2022
ms.locfileid: "67004464"
---
# <a name="compare-microsoft-endpoint-security-plans"></a>مقارنة خطط أمان نقطة النهاية من Microsoft

تم تصميم خطط أمان نقطة النهاية من Microsoft، مثل Microsoft Defender لنقطة النهاية Microsoft 365 Defender، لمساعدة المؤسسات على منع التهديدات المتقدمة واكتشافها والتحقيق فيها والاستجابة لها. يوفر Microsoft Defender for Business Microsoft 365 Business Premium قدرات مماثلة، محسنة للشركات الصغيرة والمتوسطة الحجم. توفر هذه الخطط حماية متقدمة من التهديدات مع الحماية من الفيروسات والحماية من البرامج الضارة، والتخفيف من برامج الفدية الضارة، وأكثر من ذلك، جنبا إلى جنب مع الإدارة المركزية وإعداد التقارير. 

تساعد هذه المقالة على توضيح ما هو مضمن في الخطط التالية: 

- [الخطة 1 من Microsoft Defender لنقطة النهاية](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Defender for Endpoint الخطة 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [الوظيفة الإضافية إدارة الثغرات الأمنية في Microsoft Defender](../defender-vulnerability-management/index.yml)
- [Microsoft Defender for Business](../defender-business/mdb-overview.md) و [Microsoft 365 Business Premium](../../business-premium/index.md)

> [!IMPORTANT]
> توفر هذه المقالة ملخصا لقدرات الحماية من التهديدات في خطط أمان نقاط النهاية من Microsoft؛ ومع ذلك، ليس المقصود أن يكون وصف الخدمة أو مستند عقد الترخيص. لمزيد من المعلومات التفصيلية، راجع [إرشادات ترخيص Microsoft 365 للامتثال & الأمان](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).

## <a name="compare-microsoft-endpoint-security-plans"></a>مقارنة خطط أمان نقطة النهاية من Microsoft

يلخص الجدول التالي ما هو مضمن في خطط أمان نقاط النهاية من Microsoft.

| الخطة | ما هو مضمن |
|:---|:---|
| [Defender لنقطة النهاية الخطة 1](defender-endpoint-plan-1.md) <sup>[[1](#fn1)]</sup> | <ul><li>[حماية الجيل التالي](defender-endpoint-plan-1.md#next-generation-protection) (بما في ذلك مكافحة البرامج الضارة ومكافحة الفيروسات)</li><li>[قواعد تقليل الأجزاء المعرضة للهجوم](defender-endpoint-plan-1.md#attack-surface-reduction)</li><li> [إجراءات الاستجابة اليدوية](defender-endpoint-plan-1.md#manual-response-actions)</li><li>[الإدارة المركزية](defender-endpoint-plan-1.md#centralized-management)</li><li>[تقارير الأمان](defender-endpoint-plan-1.md#reporting)</li><li>[واجهات برمجه التطبيقات](defender-endpoint-plan-1.md#apis)</li><li>[دعم أجهزة Windows 10 وiOS وAndroid OS وmacOS](defender-endpoint-plan-1.md#cross-platform-support)</li></ul>|
| [Defender لنقطة النهاية الخطة 2](microsoft-defender-endpoint.md) <sup>[[2](#fn2)]</sup> | جميع إمكانيات Defender for Endpoint Plan 1، بالإضافة إلى:<ul><li>[اكتشاف الجهاز](device-discovery.md)</li><li>[بيانات الجهاز](machines-view-overview.md)</li><li>[قدرات إدارة الثغرات الأمنية في Core Defender](../defender-vulnerability-management/defender-vulnerability-management-capabilities.md)</li><li>[تحليلات التهديدات](threat-analytics.md)</li><li>[التحقيق التلقائي والاستجابة (AIR)](automated-investigations.md)</li><li>[الصيد المتقدم](advanced-hunting-overview.md)</li><li>[الكشف عن نقطة النهاية والاستجابة لها](overview-endpoint-detection-response.md)</li><li>[خبراء المخاطر في Microsoft](microsoft-threat-experts.md)</li><li>دعم [Windows](configure-endpoints.md) (العميل والخادم) [والأنظمة الأساسية غير التابعة ل Windows](configure-endpoints-non-windows.md) (macOS وiOS وAndroid وLinux)</li></ul> |
| [الوظيفة الإضافية Defender Vulnerability Management](../defender-vulnerability-management/defender-vulnerability-management-capabilities.md) | المزيد من قدرات إدارة الثغرات الأمنية ل Defender لخطة نقطة النهاية 2:<ul><li>[تقييم خطوط الأمان الأساسية](../defender-vulnerability-management/tvm-security-baselines.md)</li><li>[حظر التطبيقات المعرضة للخطر](../defender-vulnerability-management/tvm-block-vuln-apps.md)</li><li>[ملحقات المستعرض](../defender-vulnerability-management/tvm-browser-extensions.md)</li><li>[تقييم الشهادات الرقمية](../defender-vulnerability-management/tvm-certificate-inventory.md)</li><li>[تحليل مشاركة الشبكة](../defender-vulnerability-management/tvm-network-share-assessment.md)</li><li>دعم [Windows](configure-endpoints.md) (العميل والخادم) [والأنظمة الأساسية غير التابعة ل Windows](configure-endpoints-non-windows.md) (macOS وiOS وAndroid وLinux)</li></ul> |
| [Defender for Business](../defender-business/mdb-overview.md) <sup>[[3](#fn3)]</sup> <br/>و<br/>[Microsoft 365 Business Premium](../../business-premium/index.md) | تتضمن [الخدمات المحسنة للشركات الصغيرة والمتوسطة الحجم](../defender-business/compare-mdb-m365-plans.md) ما يلي: <ul><li>حماية البريد الإلكتروني</li><li>حماية Antispam</li><li>الحماية من البرامج الضارة</li><li>حماية الجيل التالي</li><li>قواعد تقليل الأجزاء المعرضة للهجوم</li><li>الكشف عن نقطة النهاية والاستجابة لها</li><li>التحقيق التلقائي والاستجابة (AIR) </li><li>التهديدات وإدارة الثغرات الأمنية</li><li>إعداد التقارير المركزية</li><li>واجهات برمجة التطبيقات (للتكامل مع التطبيقات المخصصة أو حلول التقارير)</li><li>[التكامل مع Microsoft 365 Lighthouse](../defender-business/mdb-lighthouse-integration.md)</li></ul> |

(<a id="fn1">1</a>) يتوفر Microsoft Defender لنقطة النهاية الخطة 1 كتكوين اشتراك مستقل للعملاء التجاريين والتعليمين. كما يتم تضمينه كجزء من Microsoft 365 E3/A3.

(<a id="fn2">2</a>) Microsoft Defender لنقطة النهاية الخطة 2، التي كانت تسمى سابقا Microsoft Defender لنقطة النهاية، متوفرة كتشتراك مستقل. كما يتم تضمينها كجزء من الخطط التالية:

- Windows 11 Enterprise E5/A5
- Windows 10 Enterprise E5/A5
- Microsoft 365 E5/A5/G5 (الذي يتضمن Windows 10 أو Windows 11 Enterprise E5)
- Microsoft 365 E5/A5/G5/F5 Security
- توافق & أمان Microsoft 365 F5

(<a id="fn3">3</a>) يتوفر Microsoft Defender for Business كتشتراك مستقل للشركات الصغيرة والمتوسطة الحجم. كما يتم تضمينه كجزء من Microsoft 365 Business Premium. تتميز هذه الخطط بقدرات أمان متقدمة مع إعداد مبسط وتجربة تكوين.

## <a name="options-for-onboarding-servers"></a>خيارات إلحاق الخوادم

لا يتضمن Defender لنقطة النهاية الخطة 1 و2 (مستقل) و Defender for Business (مستقل) Microsoft 365 Business Premium تراخيص الخادم. لإلحاق الخوادم، اختر من بين الخيارات التالية:

- **Microsoft Defender for Servers Plan 1 أو الخطة 2** كجزء من عرض [Defender for Cloud](/azure/defender-for-cloud/defender-for-cloud-introduction) . لمعرفة المزيد. راجع [نظرة عامة على Microsoft Defender for Servers](/azure/defender-for-cloud/defender-for-servers-introduction).
- **Microsoft Defender for Business الخوادم (معاينة)** للشركات الصغيرة والمتوسطة الحجم. راجع [كيفية الحصول على خوادم Microsoft Defender for Business (معاينة).](../defender-business/get-defender-business-servers.md)

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

- لتجربة Defender لنقطة النهاية، انتقل إلى [صفحة التسجيل التجريبي ل Defender for Endpoint](https://go.microsoft.com/fwlink/p/?LinkID=2168109).
- لتجربة الوظيفة الإضافية إدارة الثغرات الأمنية في Microsoft Defender ل Defender for Endpoint Plan 2، تفضل بزيارة [https://aka.ms/AddonPreviewTrial](https://aka.ms/AddonPreviewTrial). 

## <a name="see-also"></a>راجع أيضًا

- [بدء استخدام Microsoft Security (العروض التجريبية)](https://www.microsoft.com/security/business/get-started/start-free-trial)
- [مشكلات الأداء في Microsoft Defender لنقطة النهاية](microsoft-defender-endpoint.md)
- [Microsoft Defender for Business](../defender-business/mdb-overview.md) (حماية نقطة النهاية للشركات الصغيرة والمتوسطة الحجم)
