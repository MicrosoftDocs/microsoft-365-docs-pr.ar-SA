---
title: التحقيق في تنبيهات Microsoft Defender لنقطة النهاية
description: استخدم خيارات التحقيق للحصول على تفاصيل حول التنبيهات التي تؤثر على شبكتك، وما تعنيه، وكيفية حلها.
keywords: التحقيق والتحقيق والأجهزة والجهاز وقوائم انتظار التنبيهات ولوحة المعلومات وعنوان IP والملف والإرسال والإرسال والتحليل العميق والمخطط الزمني والبحث والمجال وعنوان URL وIP
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
- m365-initiative-defender-endpoint
ms.topic: article
ms.date: 04/24/2018
ms.technology: mde
ms.openlocfilehash: e4d379ee476276d24b683878bc4978addf220ced
ms.sourcegitcommit: 85ce5fd0698b6f00ea1ea189634588d00ea13508
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/06/2022
ms.locfileid: "64665789"
---
# <a name="investigate-alerts-in-microsoft-defender-for-endpoint"></a>التحقيق في التنبيهات في Microsoft Defender لنقطة النهاية

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**
- [Microsoft Defender لنقطة النهاية الخطة 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender لنقطة النهاية الخطة 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> هل تريد تجربة Defender لنقطة النهاية؟ [التسجيل للحصول على إصدار تجريبي مجاني.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-investigatealerts-abovefoldlink)

تحقق من التنبيهات التي تؤثر على شبكتك، وفهم ما تعنيه، وكيفية حلها.

حدد تنبيها من قائمة انتظار التنبيهات للانتقال إلى صفحة التنبيه. تحتوي طريقة العرض هذه على عنوان التنبيه والأصول المتأثرة والجزء الجانبي للتفاصيل وقصة التنبيه.

من صفحة التنبيه، ابدأ التحقيق الخاص بك عن طريق تحديد الأصول المتأثرة أو أي من الكيانات ضمن طريقة عرض شجرة قصة التنبيه. يملأ جزء التفاصيل تلقائيا بمعلومات إضافية حول ما قمت بتحديده. لمعرفة نوع المعلومات التي يمكنك عرضها هنا، اقرأ [تنبيهات المراجعة في Microsoft Defender لنقطة النهاية](/microsoft-365/security/defender-endpoint/review-alerts).

## <a name="investigate-using-the-alert-story"></a>التحقيق باستخدام قصة التنبيه

توضح قصة التنبيه تفاصيل سبب تشغيل التنبيه، والأحداث ذات الصلة التي حدثت قبل وبعد، بالإضافة إلى الكيانات الأخرى ذات الصلة.

الكيانات قابلة للنقر وكل كيان ليس تنبيها قابل للتوسيع باستخدام أيقونة التوسيع على الجانب الأيسر من بطاقة هذا الكيان. ستتم الإشارة إلى الكيان الذي يتم التركيز عليه بواسطة شريط أزرق إلى الجانب الأيمن من بطاقة هذا الكيان، مع وضع التنبيه في العنوان في التركيز في البداية.

قم بتوسيع الكيانات لعرض التفاصيل في لمحة. سيؤدي تحديد كيان إلى تبديل سياق جزء التفاصيل إلى هذا الكيان، وسيسمح لك بمراجعة مزيد من المعلومات، بالإضافة إلى إدارة هذا الكيان. سيؤدي تحديد *...* إلى يمين بطاقة الكيان إلى الكشف عن جميع الإجراءات المتاحة لهذا الكيان. تظهر هذه الإجراءات نفسها في جزء التفاصيل عندما يكون هذا الكيان في التركيز.

> [!NOTE]
> قد يحتوي قسم قصة التنبيه على أكثر من تنبيه واحد، مع ظهور تنبيهات إضافية متعلقة بنفس شجرة التنفيذ قبل التنبيه الذي حددته أو بعده.

:::image type="content" source="images/alert-story-tree.png" alt-text="قصة تنبيه مع تركيز تنبيه وبعض البطاقات الموسعة" lightbox="images/alert-story-tree.png":::

## <a name="take-action-from-the-details-pane"></a>اتخاذ إجراء من جزء التفاصيل

بمجرد تحديد كيان اهتمام، سيتغير جزء التفاصيل لعرض معلومات حول نوع الكيان المحدد، والمعلومات التاريخية عندما يكون متوفرا، ويقدم عناصر تحكم **لاتخاذ إجراء** بشأن هذا الكيان مباشرة من صفحة التنبيه.

بمجرد الانتهاء من التحقيق، ارجع إلى التنبيه الذي بدأت به، وضع علامة على حالة التنبيه على أنها **تم حلها** وتصنيفها على أنها **تنبيه خطأ** أو **تنبيه True**. يساعد تصنيف التنبيهات على ضبط هذه الإمكانية لتوفير تنبيهات أكثر صواب وتنبيهات أقل خطأ.

إذا قمت بتصنيفه على أنه تنبيه حقيقي، يمكنك أيضا تحديد تحديد، كما هو موضح في الصورة أدناه.

:::image type="content" source="images/alert-details-resolved-true.png" alt-text="جزء التفاصيل مع تنبيه تم حله وتوسيع القائمة المنسدلة لتحديد" lightbox="images/alert-details-resolved-true.png":::

إذا كنت تواجه تنبيها خطأ مع تطبيق خط العمل، ف قم بإنشاء قاعدة منع لتجنب هذا النوع من التنبيه في المستقبل.

:::image type="content" source="images/alert-false-suppression-rule.png" alt-text="الإجراءات والتصنيف في جزء التفاصيل مع تمييز قاعدة المنع" lightbox="images/alert-false-suppression-rule.png":::

> [!TIP]
> إذا كنت تواجه أي مشاكل غير موضحة 🙂 أعلاه، فاستخدم الزر لتقديم ملاحظات أو لفتح تذكرة دعم.

## <a name="related-topics"></a>المواضيع ذات الصلة

- [عرض قائمة انتظار Microsoft Defender لنقطة النهاية Alerts وتنظيمها](alerts-queue.md)
- [إدارة تنبيهات Microsoft Defender لنقطة النهاية](manage-alerts.md)
- [التحقيق في ملف مقترن بتنبيه Defender لنقطة النهاية](investigate-files.md)
- [التحقيق في الأجهزة في قائمة أجهزة Defender لنقطة النهاية](investigate-machines.md)
- [التحقيق في عنوان IP المقترن بتنبيه Defender لنقطة النهاية](investigate-ip.md)
- [التحقيق في مجال مقترن بتنبيه Defender لنقطة النهاية](investigate-domain.md)
- [التحقيق في حساب مستخدم في Defender لنقطة النهاية](investigate-user.md)
