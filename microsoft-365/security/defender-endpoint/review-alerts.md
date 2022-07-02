---
title: مراجعة التنبيهات في Microsoft Defender لنقطة النهاية
description: راجع معلومات التنبيه، بما في ذلك قصة تنبيه مرئية وتفاصيل لكل خطوة من خطوات السلسلة.
keywords: الحادث، الحوادث، الأجهزة، الأجهزة، المستخدمين، التنبيهات، التنبيه، التحقيق، الرسم البياني، الأدلة
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
ms.openlocfilehash: 76503c180dfdd2314254efc9315235c0802ab7f8
ms.sourcegitcommit: bfbe2574f487ced69e711b48ce140120bd99181b
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/02/2022
ms.locfileid: "66607510"
---
# <a name="review-alerts-in-microsoft-defender-for-endpoint"></a>مراجعة التنبيهات في Microsoft Defender لنقطة النهاية

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**ينطبق على:**
- [Defender for Endpoint الخطة 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

> هل تريد تجربة Defender لنقطة النهاية؟ [التسجيل للحصول على إصدار تجريبي مجاني.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-managealerts-abovefoldlink)

توفر صفحة التنبيه في Microsoft Defender لنقطة النهاية سياقا كاملا للتنبيه، من خلال الجمع بين إشارات الهجوم والتنبيهات المتعلقة بالتنبيه المحدد، لإنشاء قصة تنبيه مفصلة.

يمكنك فرز التنبيهات التي تؤثر على مؤسستك والتحقيق فيها واتخاذ إجراءات فعالة بشأنها بسرعة. فهم سبب تشغيلها وتأثيرها من موقع واحد. تعرف على المزيد في هذه النظرة العامة.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4yiO5]

## <a name="getting-started-with-an-alert"></a>بدء استخدام تنبيه

سيؤدي تحديد اسم تنبيه في Defender لنقطة النهاية إلى وضعك في صفحة التنبيه الخاصة به. في صفحة التنبيه، سيتم عرض جميع المعلومات في سياق التنبيه المحدد. تتكون كل صفحة تنبيه من 4 أقسام:

1. يظهر **عنوان التنبيه** اسم التنبيه وهو موجود لتذكيرك بالتنبيه الذي بدأ التحقيق الحالي بغض النظر عما حددته على الصفحة.
2. تسرد [**الأصول المتأثرة**](#review-affected-assets) بطاقات الأجهزة والمستخدمين المتأثرين بهذا التنبيه التي يمكن النقر فوقها للحصول على مزيد من المعلومات والإجراءات.
3. تعرض **قصة التنبيه** جميع الكيانات المتعلقة بالتنبيه، المترابطة من خلال طريقة عرض الشجرة. سيكون التنبيه في العنوان هو الذي سيركز عليه عند الوصول لأول مرة إلى صفحة التنبيه المحدد. الكيانات في قصة التنبيه قابلة للتوسيع والنقر، لتوفير معلومات إضافية وتسريع الاستجابة من خلال السماح لك باتخاذ الإجراءات مباشرة في سياق صفحة التنبيه. استخدم قصة التنبيه لبدء التحقيق الخاص بك. تعرف على كيفية [التحقيق في التنبيهات في Microsoft Defender لنقطة النهاية](/microsoft-365/security/defender-endpoint/investigate-alerts).
4. سيظهر **جزء التفاصيل** تفاصيل التنبيه المحدد في البداية، مع التفاصيل والإجراءات المتعلقة بهذا التنبيه. إذا حددت أيا من الأصول أو الكيانات المتأثرة في قصة التنبيه، فسيتغير جزء التفاصيل لتوفير معلومات وإجراءات سياقية للكائن المحدد.

لاحظ حالة الكشف للتنبيه.

- تم منعه: تم تجنب الإجراء المشبوه الذي تم محاولة القيام به. على سبيل المثال، لم تتم كتابة ملف على القرص أو تنفيذه.

  :::image type="content" source="images/detstat-prevented.png" alt-text="الصفحة التي تعرض منع التهديد" lightbox="images/detstat-prevented.png":::

- محظور: تم تنفيذ السلوك المشبوه ثم حظره. على سبيل المثال، تم تنفيذ عملية ولكن نظرا لأنها أظهرت سلوكيات مريبة في وقت لاحق، تم إنهاء العملية.

  :::image type="content" source="images/detstat-blocked.png" alt-text="الصفحة التي تعرض حجب التهديد" lightbox="images/detstat-blocked.png":::

- تم الكشف عن: تم الكشف عن هجوم وربما لا يزال نشطا.

  :::image type="content" source="images/detstat-detected.png" alt-text="الصفحة التي تعرض الكشف عن تهديد" lightbox="images/detstat-detected.png":::

يمكنك بعد ذلك أيضا مراجعة *تفاصيل التحقيق التلقائي* في جزء تفاصيل التنبيه، لمعرفة الإجراءات التي تم اتخاذها بالفعل، بالإضافة إلى قراءة وصف التنبيه للإجراءات الموصى بها.

:::image type="content" source="images/alert-air-and-alert-description.png" alt-text="جزء التفاصيل مع تمييز وصف التنبيه وأقسام التحقيق التلقائي" lightbox="images/alert-air-and-alert-description.png":::

تتضمن المعلومات الأخرى المتوفرة في جزء التفاصيل عند فتح التنبيه تقنيات MITRE والمصدر والتفاصيل السياقية الإضافية.

> [!NOTE]
> إذا رأيت حالة تنبيه *نوع تنبيه غير معتمد* ، فهذا يعني أنه لا يمكن لقدرات التحقيق التلقائي التقاط هذا التنبيه لتشغيل تحقيق تلقائي. ومع ذلك، يمكنك [التحقق من هذه التنبيهات يدويا](../defender/investigate-incidents.md#alerts).

## <a name="review-affected-assets"></a>مراجعة الأصول المتأثرة

سيؤدي تحديد جهاز أو بطاقة مستخدم في أقسام الأصول المتأثرة إلى التبديل إلى تفاصيل الجهاز أو المستخدم في جزء التفاصيل.

- **بالنسبة للأجهزة**، سيعرض جزء التفاصيل معلومات حول الجهاز نفسه، مثل المجال ونظام التشغيل وIP. تتوفر أيضا التنبيهات النشطة والمستخدمين الذين تم تسجيل دخولهم على هذا الجهاز. يمكنك اتخاذ إجراء فوري عن طريق عزل الجهاز، أو تقييد تنفيذ التطبيق، أو تشغيل فحص مكافحة الفيروسات. بدلا من ذلك، يمكنك جمع حزمة تحقيق، أو بدء تحقيق تلقائي، أو الانتقال إلى صفحة الجهاز للتحقيق من وجهة نظر الجهاز.

   :::image type="content" source="images/device-page-details.png" alt-text="جزء التفاصيل عند تحديد جهاز" lightbox="images/device-page-details.png":::

- **بالنسبة للمستخدمين**، سيعرض جزء التفاصيل معلومات مفصلة للمستخدم، مثل اسم SAM الخاص بالمستخدم و SID، بالإضافة إلى أنواع تسجيل الدخول التي يقوم بها هذا المستخدم وأي تنبيهات وحوادث متعلقة به. يمكنك تحديد *"فتح صفحة المستخدم* " لمتابعة التحقيق من وجهة نظر هذا المستخدم.

   :::image type="content" source="images/user-page-details.png" alt-text="جزء التفاصيل عند تحديد مستخدم" lightbox="images/user-page-details.png":::

## <a name="related-topics"></a>المواضيع ذات الصلة

- [عرض قائمة انتظار الأحداث وتنظيمها](view-incidents-queue.md)
- [التحقيق في الأحداث](investigate-incidents.md)
- [إدارة الأحداث](manage-incidents.md)
