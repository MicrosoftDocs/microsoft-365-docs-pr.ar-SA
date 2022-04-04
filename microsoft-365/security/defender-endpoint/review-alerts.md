---
title: مراجعة التنبيهات في Microsoft Defender لنقطة النهاية
description: راجع معلومات التنبيه، بما في ذلك قصة تنبيه مرئية وتفاصيل لكل خطوة من السلسلة.
keywords: حادث، أحداث، أجهزة، أجهزة، مستخدمين، تنبيهات، تنبيه، تحقيق، رسم بياني، دليل
ms.prod: m365-security
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
- m365-initiative-defender-endpoint
ms.topic: conceptual
ms.date: 5/1/2020
ms.technology: mde
ms.openlocfilehash: 91cd06188a8337f3d0df0b9c67d7c98e389e4351
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/25/2022
ms.locfileid: "64466730"
---
# <a name="review-alerts-in-microsoft-defender-for-endpoint"></a>مراجعة التنبيهات في Microsoft Defender لنقطة النهاية

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**ينطبق على:**
- [Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

> هل تريد تجربة Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-managealerts-abovefoldlink)

توفر صفحة التنبيه في Microsoft Defender لنقطة النهاية سياقا كاملا للتنبيه، من خلال دمج إشارات الهجوم والتنبيهات ذات الصلة بالتنبيه المحدد، لإنشاء قصة تنبيه مفصلة.

يمكنك إجراء الفرز والتحري واتخاذ إجراء فعال بسرعة على التنبيهات التي تؤثر على مؤسستك. فهم سبب تشغيلها وتأثيرها من موقع واحد. تعرف على المزيد في هذه النظرة العامة.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4yiO5]

## <a name="getting-started-with-an-alert"></a>بدء العمل باستخدام تنبيه

سيدفعك تحديد اسم تنبيه في Defender for Endpoint إلى وضعك على صفحة التنبيه الخاصة به. في صفحة التنبيه، سيتم عرض كل المعلومات في سياق التنبيه المحدد. تتكون كل صفحة تنبيه من 4 مقاطع:

1. **يعرض عنوان التنبيه** اسم التنبيه وهو هناك لتذكيرك بالتنبيه الذي بدأ التحقيق الحالي بغض النظر عما قمت بتحديده على الصفحة.
2. [**تسرد الأصول المتأثرة**](#review-affected-assets) بطاقات الأجهزة والمستخدمين المتأثرين بهذا التنبيه التي يمكن النقر فوقها للحصول على مزيد من المعلومات والإجراءات.
3. تعرض **قصة التنبيه** كل الكيانات المرتبطة بالتنبيه، متداخلة بواسطة طريقة عرض الشجرة. سيكون التنبيه في العنوان هو التنبيه الذي يتم التركيز عليه عند أول مرة يتم فيها التركيز على صفحة التنبيه المحددة. الكيانات في قصة التنبيه قابلة للتوسع والنقر، لتوفير معلومات إضافية والاستجابة السريعة من خلال السماح لك لاتخاذ إجراءات مباشرة في سياق صفحة التنبيه. استخدم قصة التنبيه لبدء التحقيق. تعرف على كيفية إجراء [ذلك في التحقق من التنبيهات في Microsoft Defender لنقطة النهاية](/microsoft-365/security/defender-endpoint/investigate-alerts).
4. **سيعرض جزء التفاصيل** تفاصيل التنبيه المحدد في بادئ الأمر، مع التفاصيل والإجراءات المتعلقة بهذا التنبيه. إذا قمت بتحديد أي من الأصول أو الكيانات المتأثرة في قصة التنبيه، سيتغير جزء التفاصيل لتوفير معلومات سياقية والإجراءات للكائن المحدد.

لاحظ حالة الكشف عن تنبيهك.

- تم منعه: تم تجنب الإجراء المريب الذي تم محاولة القيام به. على سبيل المثال، لم يتم كتابة ملف على القرص أو تنفيذه.

  :::image type="content" source="images/detstat-prevented.png" alt-text="الصفحة التي تعرض منع التهديدات" lightbox="images/detstat-prevented.png":::

- تم الحظر: تم تنفيذ سلوك مريب ثم تم حظره. على سبيل المثال، تم تنفيذ عملية، ولكن نظرا لأنها أظهرت في وقت لاحق سلوكيات مريبة، تم إنهاء العملية.

  :::image type="content" source="images/detstat-blocked.png" alt-text="الصفحة التي تعرض حظر خطر" lightbox="images/detstat-blocked.png":::

- تم الكشف عن: تم الكشف عن هجوم وربما لا يزال نشطا.

  :::image type="content" source="images/detstat-detected.png" alt-text="الصفحة التي تعرض الكشف عن خطر" lightbox="images/detstat-detected.png":::

بعد ذلك، يمكنك أيضا مراجعة  تفاصيل التحقيق التلقائي في جزء تفاصيل التنبيه، لمعرفة الإجراءات التي تم اتخاذها بالفعل، بالإضافة إلى قراءة وصف التنبيه حول الإجراءات الموصى بها.

:::image type="content" source="images/alert-air-and-alert-description.png" alt-text="جزء التفاصيل مع تمييز وصف التنبيه وأقسام التحقيق التلقائي" lightbox="images/alert-air-and-alert-description.png":::

تتضمن المعلومات الأخرى المتوفرة في جزء التفاصيل عند فتح التنبيه تقنيات MITRE ومصدرها وتفاصيل سياقية إضافية.

## <a name="review-affected-assets"></a>مراجعة الأصول المتأثرة

سيبدل تحديد جهاز أو بطاقة مستخدم في أقسام الأصول المتأثرة إلى تفاصيل الجهاز أو المستخدم في جزء التفاصيل.

- **بالنسبة للأجهزة**، سيعرض جزء التفاصيل معلومات حول الجهاز نفسه، مثل المجال ونظام التشغيل وIP. تتوفر أيضا التنبيهات النشطة والمستخدمين الذين سجلوا دخولهم على هذا الجهاز. يمكنك اتخاذ إجراء فوري عن طريق عزل الجهاز أو تقييد تنفيذ التطبيق أو تشغيل فحص الحماية من الفيروسات. بدلا من ذلك، يمكنك تجميع حزمة تحقيق أو بدء تحقيق تلقائي أو الانتقال إلى صفحة الجهاز للتحقق من وجهة نظر الجهاز.

   :::image type="content" source="images/device-page-details.png" alt-text="جزء التفاصيل عند تحديد جهاز" lightbox="images/device-page-details.png":::

- بالنسبة **للمستخدمين**، سيعرض جزء التفاصيل معلومات تفصيلية حول المستخدم، مثل اسم SAM و SID الخاص بالمستخدم، بالإضافة إلى أنواع تسجيلات تسجيل الوصول التي ينفذها هذا المستخدم وأي تنبيهات أو أحداث متعلقة به. يمكنك تحديد *فتح صفحة المستخدم* لمواصلة التحقيق من وجهة نظر هذا المستخدم.

   :::image type="content" source="images/user-page-details.png" alt-text="جزء التفاصيل عند تحديد مستخدم" lightbox="images/user-page-details.png":::

## <a name="related-topics"></a>المواضيع ذات الصلة

- [عرض قائمة انتظار الأحداث وتنظيمها](view-incidents-queue.md)
- [التحقيق في الأحداث](investigate-incidents.md)
- [إدارة الأحداث](manage-incidents.md)
