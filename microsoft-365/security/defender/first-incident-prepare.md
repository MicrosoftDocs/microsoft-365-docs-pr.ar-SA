---
title: إعداد وضع الأمان الخاص بك لحادثك الأول
description: قم بإعداد وضع الأمان لمستأجر Microsoft 365 الخاص بك للحدث الأول في Microsoft 365 Defender.
keywords: الحوادث والتنبيهات والتحقيق والارتباط والهجوم والأجهزة والأجهزة والمستخدمين والهويات والهوية وعلبة البريد والبريد الإلكتروني و365 وmicrosoft وm365
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
ms.topic: conceptual
search.appverid:
- MOE150
- MET150
ms.technology: m365d
ms.openlocfilehash: 0dbff9e88ed00dd8aa08fd64543266c3aef75d79
ms.sourcegitcommit: 85ce5fd0698b6f00ea1ea189634588d00ea13508
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/06/2022
ms.locfileid: "64664073"
---
# <a name="prepare-your-security-posture-for-your-first-incident"></a>إعداد وضع الأمان الخاص بك لحادثك الأول

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**ينطبق على:**
- Microsoft 365 Defender

يتضمن التحضير لمعالجة الحوادث إعداد حماية كافية لشبكة المؤسسة من أنواع مختلفة من الحوادث الأمنية. لتقليل مخاطر الحوادث الأمنية، يوصي المعهد الوطني للمعايير والتكنولوجيا (NIST) بالعديد من الممارسات الأمنية بما في ذلك تقييمات المخاطر، وتصلب أمان المضيف، وتكوين الشبكات بشكل آمن، ومنع البرامج الضارة.

يمكن أن تساعد Microsoft 365 Defender في معالجة العديد من جوانب منع الحوادث:

- تنفيذ إطار [عمل ثقة معدومة](/security/zero-trust/)
- تحديد وضع الأمان الخاص بك عن طريق تعيين درجة باستخدام [نقاط Microsoft الآمنة](microsoft-secure-score.md)
- منع التهديدات من خلال تقييمات الثغرات الأمنية في [إدارة المخاطر والثغرات الأمنية](../defender-endpoint/next-gen-threat-and-vuln-mgt.md)
- فهم أحدث تهديدات الأمان حتى تتمكن من الاستعداد لها باستخدام [تحليلات التهديدات](threat-analytics.md)

## <a name="step-1-implement-zero-trust"></a>الخطوة 1. تنفيذ ثقة معدومة

[ثقة معدومة](/security/zero-trust/) هي فلسفة أمنية متكاملة واستراتيجية شاملة تأخذ في الاعتبار الطبيعة المعقدة لأي بيئة حديثة، بما في ذلك القوى العاملة المتنقلة والمستخدمين والأجهزة والتطبيقات والبيانات، أينما كانوا. من خلال توفير جزء واحد من الزجاج لإدارة جميع عمليات الكشف بطريقة متسقة، Microsoft 365 Defender يمكن أن تجعل من السهل على فريق عمليات الأمان تنفيذ [المبادئ التوجيهية](/security/zero-trust/#guiding-principles-of-zero-trust) ثقة معدومة.

يمكن لمكونات Microsoft 365 Defender عرض انتهاكات القواعد التي تم تنفيذها لإنشاء نهج الوصول المشروط ثقة معدومة عن طريق دمج البيانات من Microsoft Defender لنقطة النهاية  أو موردي أمان الأجهزة المحمولة الآخرين كمصدر معلومات لنهج توافق الأجهزة وتنفيذ نهج الوصول المشروط المستندة إلى الجهاز.

يؤثر خطر الجهاز مباشرة على الموارد التي يمكن الوصول إليها من قبل مستخدم هذا الجهاز. إن رفض الوصول إلى الموارد استنادا إلى معايير معينة هو الموضوع الرئيسي ثقة معدومة ويوفر Microsoft 365 Defender المعلومات اللازمة لتحديد معايير مستوى الثقة. على سبيل المثال، يمكن Microsoft 365 Defender توفير مستوى إصدار البرنامج لجهاز من خلال صفحة إدارة المخاطر والثغرات الأمنية بينما تقيد نهج الوصول المشروط الأجهزة التي تحتوي على إصدارات قديمة أو عرضة للخطر.

الأتمتة هي جزء حاسم من تنفيذ وصيانة بيئة ثقة معدومة مع تقليل عدد التنبيهات التي من المحتمل أن تؤدي إلى أحداث الاستجابة للحوادث (IR). يمكن أتمتة مكونات Microsoft 365 Defender مثل [إجراءات المعالجة](m365d-autoir.md) (المعروفة باسم التحقيقات في حادث في مدخل Microsoft 365 Defender) وإجراءات الإعلام وحتى إنشاء تذاكر الدعم كما هو الحال في [ServiceNow](https://microsoft.service-now.com/sp/).

## <a name="step-2-determine-your-organizations-security-posture"></a>الخطوة 2. تحديد وضع الأمان لمؤسستك

بعد ذلك، يمكن للمؤسسات استخدام [درجة أمان Microsoft](microsoft-secure-score.md) في Microsoft 365 Defender لتحديد وضع الأمان الحالي والنظر في توصيات حول كيفية تحسينه. كلما ارتفعت الدرجة، زادت توصيات الأمان وإجراءات التحسين التي اتخذتها المؤسسة. يمكن أخذ توصيات درجة الأمان عبر منتجات مختلفة والسماح للمؤسسات برفع درجاتها أعلى.

:::image type="content" source="../../media/first-incident-prepare/first-incident-secure-score.png" alt-text="صفحة نقاط الأمان من Microsoft في مدخل Microsoft 365 Defender" lightbox="../../media/first-incident-prepare/first-incident-secure-score.png":::

## <a name="step-3-assess-your-organizations-vulnerability-exposure"></a>الخطوة 3. تقييم تعرض مؤسستك للثغرات الأمنية

يمكن أن يساعد منع الحوادث في تبسيط جهود العمليات الأمنية للتركيز على الحوادث الأمنية الحرجة والمهمة المستمرة. غالبا ما تكون الثغرات الأمنية في البرامج نقطة دخول يمكن منعها للهجمات التي يمكن أن تؤدي إلى سرقة البيانات أو فقدان البيانات أو تعطيل العمليات التجارية. إذا لم تكن هناك هجمات مستمرة، يجب أن تسعى العمليات الأمنية جاهدة لتحقيق مستوى مقبول من [التعرض للثغرات الأمنية](../defender-endpoint/tvm-exposure-score.md) والحفاظ عليه في مؤسستها.

للتحقق من تقدم تصحيح البرامج، تفضل بزيارة صفحة [إدارة المخاطر والثغرات الأمنية](../defender-endpoint/next-gen-threat-and-vuln-mgt.md) في Defender لنقطة النهاية، والتي يمكنك الوصول إليها من Microsoft 365 Defender من خلال علامة تبويب **المزيد من الموارد**.

:::image type="content" source="../../media/first-incident-prepare/first-incident-vulnerability.png" alt-text="صفحة التهديد والثغرات الأمنية في مدخل Microsoft 365 Defender" lightbox="../../media/first-incident-prepare/first-incident-vulnerability.png":::

## <a name="4-understand-emerging-threats"></a>4. فهم التهديدات الناشئة

استخدم [تحليلات التهديدات](threat-analytics.md) في مدخل Microsoft 365 Defender لمواكبة مشهد التهديد الأمني الحالي. ينشئ باحثو أمان Microsoft الخبراء تقارير تصف أحدث التهديدات الإلكترونية بالتفصيل حتى تتمكن من فهم كيفية تأثيرها على اشتراكك في Microsoft 365 والأجهزة والمستخدمين. يمكن أن تتضمن هذه التقارير ما يلي:

- الجهات الفاعلة النشطة للمخاطر وحملاتها
- تقنيات الهجوم الشائعة والجديدة
- الثغرات الأمنية الحرجة
- أسطح الهجوم الشائعة
- البرامج الضارة الشائعة

كما تبحث تحليلات التهديد في التكوين والتنبيهات الخاصة بك لتحديد مدى تعرضك للخطر وما إذا كانت هناك تنبيهات نشطة تنطبق على تقرير.

يمكنك تنفيذ توصيات التهديد الناشئ لتعزيز وضعك الأمني وتقليل مساحة سطح الهجوم.

اقض وقتا في جدولك الزمني للتحقق بانتظام من قسم [Threat Analytics](threat-analytics.md) في مدخل Microsoft 365 Defender. راجع [أمثلة عمليات الأمان Microsoft 365 Defender](incidents-overview.md#example-security-operations-for-microsoft-365-defender) للحصول على مزيد من المعلومات.

## <a name="next-step"></a>الخطوة التالية

تعرف على كيفية [فرز الحوادث وتحليلها](first-incident-analyze.md).

## <a name="see-also"></a>راجع أيضًا

- [نظرة عامة على الحوادث](incidents-overview.md)
- [التحقيق في الأحداث](investigate-incidents.md)
- [إدارة الأحداث](manage-incidents.md)
