---
title: دعم IPv6 في خدمات Microsoft 365
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 06/02/2022
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: c08786fb-298e-437c-8222-dab7625fc815
description: 'ملخص: يصف دعم IPv6 في مكونات Microsoft 365 وفي عروض الحكومة Microsoft 365.'
ms.openlocfilehash: 2619567e8dac6f4b87cba0108bcf105011c4a87c
ms.sourcegitcommit: 35f167725bec5fd4fe131781a53d96b060cf232d
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 06/03/2022
ms.locfileid: "65872731"
---
# <a name="ipv6-support-in-microsoft-365-services"></a>دعم IPv6 في خدمات Microsoft 365

مع تزايد اعتماد ودعم IPv6 عبر شبكات المؤسسة وموفري الخدمات والأجهزة، يتساءل العديد من العملاء عما إذا كان يمكن لمستخدميهم الاستمرار في الوصول إلى خدمات Microsoft 365 من عملاء IPv6 وشبكات IPv6. يمكن استخدام خدمات Microsoft 365 بنجاح من كل من أجهزة IPv6 المزدوجة المكدس وأجهزة IPv6 فقط. في الواقع، لدينا عدد متزايد من العملاء، من المستهلكين إلى الشركات الكبيرة، الذين يتحركون نحو اعتماد أكبر ل IPv6. بالنسبة لمعظم العملاء، لن تختفي IPv4 تماما من مشهدهم الرقمي، لذلك لا نخطط لطلب IPv6 أو إلغاء تحديد أولويات IPv4 في أي ميزات أو خدمات Microsoft 365.

تتمثل إحدى أولوياتنا الرئيسية مع Microsoft 365 في ضمان تجارب العملاء والمستخدمين السلسة عبر الإنترنت من أي موقع ومن أي جهاز. يتضمن ذلك الوصول إلى Microsoft 365 من أجهزة العملاء التي تستخدم IPv6 في تكوين المكدس المزدوج بالإضافة إلى الانتقال إلى عمليات نشر العميل IPv6 فقط. في معظم الحالات، عند اتباع نموذج قياسي قائم على الإنترنت للاتصال Microsoft 365 كما هو موضح في [مبادئ اتصال الشبكة Microsoft 365](microsoft-365-network-connectivity-principles.md) [وعناوين URL Microsoft 365 ونطاقات عناوين IP](urls-and-ip-address-ranges.md) وأفضل [ممارسات تخطيط الشبكة Microsoft 365](network-and-migration-planning.md#best-practices-for-network-planning-and-improving-migration-performance-for-office-365) ، لن تكون انتقالات IPv6 معطلة لتجربة المستخدم.

توفر العديد من خدمات Microsoft 365 بالفعل دعم IPv6 الأصلي اليوم ويمكن الوصول إليه مباشرة من مكدس IPv6 المزدوج وعملاء IPv6 فقط. يسمح Microsoft 365 أيضا بالوصول من خلال تقنيات ترجمة IPv6 التقليدية إلى IPv4 (مثل وكلاء الأساس 64 أو DNS64/NAT64) شائعة الاستخدام من قبل العملاء وموفري حلول الشبكة للاتصال بموارد إنترنت IPv4.

كما هو الحال مع أي خدمة SaaS والإنترنت بشكل عام، يتم توسيع نطاق واجهات Microsoft 365 والميزات وواجهات برمجة التطبيقات الممكنة في IPv6 بشكل مستمر ودون إجراء العميل المباشر أو التحكم فيه. إذا كنت تقوم بتشغيل خدمات IPv6 أو IPv6 فقط على شبكاتك التي تحتاج إلى الوصول إلى Microsoft 365 والإنترنت، فمن المستحسن تضمين آليات انتقالية ديناميكية ل IPv6/IPv4 مثل DNS64/NAT64 لضمان اتصال IPv6 من طرف إلى طرف Microsoft 365 دون أي عمليات إعادة تكوين أخرى للشبكة.

تم تمكين معظم خدمات Microsoft 365 باستخدام إمكانات IPv6 أو سيتم تمكينها بشفافية كاملة للمستخدمين النهائيين ومسؤولين تكنولوجيا المعلومات. تحتوي بعض سيناريوهات Microsoft 365 (مثل البريد الإلكتروني الوارد المجهول) على متطلبات واعتبارات خاصة للاستخدام بالتزامن مع IPv6. لمزيد من التفاصيل حول متطلبات واعتبارات IPv6 المحددة للسيناريو، يرجى الاتصال بفريق حساب Microsoft أو دعم Microsoft.

فيما يلي ارتباط قصير يمكنك استخدامه للعودة: [https://aka.ms/o365ip6](https://aka.ms/o365ip6)

## <a name="see-also"></a>راجع أيضًا

[نظرة عامة على اتصال الشبكة Microsoft 365](microsoft-365-networking-overview.md)

[إدارة نقاط نهاية Office 365](managing-office-365-endpoints.md)

[نطاقات عناوين IP وعناوين URL في Office 365](urls-and-ip-address-ranges.md)

[عنوان IP لـ Office 365 وخدمة URL على ويب](microsoft-365-ip-web-service.md)

[تقييم اتصال الشبكة Microsoft 365](assessing-network-connectivity.md)

[تخطيط الشبكة وضبط الأداء Microsoft 365](network-planning-and-performance.md)

[ضبط الأداء Office 365 باستخدام الخطوط الأساسية ومحفوظات الأداء](performance-tuning-using-baselines-and-history.md)

[خطة استكشاف أخطاء الأداء وإصلاحها Office 365](performance-troubleshooting-plan.md)

[شبكات تسليم المحتوى](content-delivery-networks.md)

[اختبار اتصال Microsoft 365](https://aka.ms/netonboard)

[كيف تبني Microsoft شبكتها العالمية السريعة والموثوق بها](https://azure.microsoft.com/blog/how-microsoft-builds-its-fast-and-reliable-global-network/)

[مدونة Office 365 Networking](https://techcommunity.microsoft.com/t5/Office-365-Networking/bd-p/Office365Networking)
