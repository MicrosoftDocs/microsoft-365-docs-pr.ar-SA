---
title: التحقق Microsoft Defender لنقطة النهاية الملفات
description: استخدم خيارات التحقيق للحصول على تفاصيل حول الملفات المقترنة بالتنبيهات أو السلوكيات أو الأحداث.
keywords: التحقيق، التحقيق، الملف، النشاط الضار، الدافع للهجوم، التحليل العميق، تقرير التحليل العميق
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: m365-security-compliance
ms.topic: article
ms.date: 04/24/2018
ms.technology: mde
ms.openlocfilehash: 0cb7523036d6660d4b5556fdfd07e443a359b208
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/25/2022
ms.locfileid: "64466224"
---
# <a name="investigate-a-file-associated-with-a-microsoft-defender-for-endpoint-alert"></a>التحقق من ملف مقترن بتنبيه Microsoft Defender لنقطة النهاية

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**
- [Microsoft Defender لنقطة النهاية 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)


> هل تريد تجربة Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-investigatefiles-abovefoldlink)

تحقق من تفاصيل ملف مقترن بتنبيه أو سلوك أو حدث معين للمساعدة في تحديد ما إذا كان الملف يحتوي على أنشطة ضارة، وتحديد الدافع للهجوم، وفهم النطاق المحتمل للانتهاك.

هناك العديد من الطرق للوصول إلى صفحة ملف التعريف التفصيلية لملف معين. على سبيل المثال، يمكنك استخدام ميزة البحث، أو النقر فوق ارتباط من شجرة عملية التنبيه، أو رسم بياني **للحوادث**، أو مخطط زمني للقطعة، أو تحديد حدث مدرج في المخطط **الزمني للجهاز**. 

بمجرد الوصول إلى صفحة ملف التعريف التفصيلي، يمكنك التبديل بين تخطيطي الصفحة الجديدة والصفحة القديمة من خلال تبديل **صفحة ملف جديدة**. تصف باقي هذه المقالة تخطيط الصفحة الجديد.

يمكنك الحصول على معلومات من المقاطع التالية في طريقة عرض الملف:

- تفاصيل الملف، الكشف عن البرامج الضارة، نقل الملفات
- تحليل معمق
- التنبيهات
- الملحوظة في المؤسسة
- تحليل معمق
- أسماء الملفات

يمكنك أيضا اتخاذ إجراء على ملف من هذه الصفحة.

## <a name="file-actions"></a>إجراءات الملف

على طول الجزء العلوي من صفحة ملف التعريف، أعلى بطاقات معلومات الملف. تتضمن الإجراءات التي يمكنك تنفيذها هنا ما يلي:

- إيقاف وفحص
- مؤشر إضافة/تحرير
- تنزيل ملف
- استشارة خبير في التهديدات
- مركز الإجراءات

لمزيد من المعلومات حول هذه الإجراءات، راجع [اتخاذ إجراء استجابة على ملف](respond-file-alerts.md).

## <a name="file-details-malware-detection-and-file-prevalence"></a>تفاصيل الملف، الكشف عن البرامج الضارة، وقيمة نقل الملفات

تعرض تفاصيل الملف والحادث والكشف عن البرامج الضارة وبطاقات نقل الملفات سمات مختلفة حول الملف.

سترى تفاصيل مثل MD5 للملف ونسبة الكشف عن الفيروسات الإجمالية والكشف عن MICROSOFT Defender AV إذا كان متوفرا، وملفات نقل الملفات.

تعرض بطاقة نقل الملفات مكان رؤية الملف في الأجهزة في المؤسسة وعلى مستوى العالم.

> [!NOTE]
> قد يرى مستخدمون مختلفون قيما غير مختلفة في *الأجهزة في قسم* المؤسسة من بطاقة نقل الملفات. وذلك لأن البطاقة تعرض معلومات استنادا إلى نطاق RBAC الذي لدى المستخدم. وهذا يعني أنه إذا تم منح المستخدم إمكانية الرؤية على مجموعة معينة من الأجهزة، لن يرى سوى حالة الانتشار التنظيمي للملفات على تلك الأجهزة.

:::image type="content" source="images/atp-file-information.png" alt-text="معلومات الملف" lightbox="images/atp-file-information.png":::

## <a name="alerts"></a>التنبيهات

توفر **علامة التبويب** تنبيهات قائمة بالتنبيهات المقترنة بالملف. تغطي هذه القائمة الكثير من المعلومات نفسها مثل قائمة انتظار التنبيهات، باستثناء مجموعة الأجهزة التي ينتمي إليها الجهاز المتأثر، إن وجدت. يمكنك اختيار نوع المعلومات التي تظهر عن طريق تحديد **تخصيص الأعمدة** من شريط الأدوات أعلى رؤوس الأعمدة.

:::image type="content" source="images/atp-alerts-related-to-file.png" alt-text="التنبيهات ذات الصلة بقسم الملف" lightbox="images/atp-alerts-related-to-file.png":::

## <a name="observed-in-organization"></a>الملحوظة في المؤسسة

تسمح **لك علامة التبويب** ملاحظة في المؤسسة بتحديد نطاق تاريخ لمعرفة الأجهزة التي تم ملاحظتها مع الملف.

> [!NOTE]
> ستعرض علامة التبويب هذه العدد الأقصى ل 100 جهاز. لرؤية كل _الأجهزة_ التي تتضمن الملف، قم بتصدير علامة التبويب إلى ملف CSV، عن طريق  تحديد تصدير من قائمة الإجراءات أعلى رؤوس أعمدة علامة التبويب.

:::image type="content" source="images/atp-observed-machines.png" alt-text="أحدث الأجهزة التي تم ملاحظتها مع الملف" lightbox="images/atp-observed-machines.png":::

استخدم شريط التمرير أو محدد النطاق لتحديد فترة زمنية تريد التحقق من الأحداث التي تتضمن الملف بسرعة. يمكنك تحديد نافذة زمنية صغيرة مثل يوم واحد. سيسمح لك هذا الأمر برؤية الملفات التي تواصلت مع عنوان IP هذا فقط في ذلك الوقت، مما يقلل بشكل كبير من عمليات التمرير والبحث غير الضرورية.

## <a name="deep-analysis"></a>تحليل معمق

تسمح **لك** علامة التبويب تحليل أعمق بإرسال [](respond-file-alerts.md#deep-analysis)الملف لتحليله بعمق، للكشف عن مزيد من التفاصيل حول سلوك الملف، بالإضافة إلى التأثير الذي يحدثه داخل مؤسستك. بعد إرسال الملف، سيظهر تقرير التحليل العميق في علامة التبويب هذه بمجرد توفر النتائج. إذا لم يعثر التحليل العميق على أي شيء، سيكون التقرير فارغا وستبقى مساحة النتائج فارغة.

:::image type="content" source="images/submit-file.png" alt-text="علامة التبويب &quot;تحليل أعمق&quot;" lightbox="images/submit-file.png":::

## <a name="file-names"></a>أسماء الملفات

**تسرد علامة التبويب** أسماء الملفات جميع الأسماء التي تم ملاحظة أن الملف يستخدمها، ضمن مؤسستك.

:::image type="content" source="images/atp-file-names.png" alt-text="علامة التبويب &quot;أسماء الملفات&quot;" lightbox="images/atp-file-names.png":::

## <a name="related-topics"></a>المواضيع ذات الصلة

- [عرض قائمة Microsoft Defender لنقطة النهاية الانتظار وتنظيمها](alerts-queue.md)
- [إدارة Microsoft Defender لنقطة النهاية التنبيهات](manage-alerts.md)
- [التحقق Microsoft Defender لنقطة النهاية التنبيهات](investigate-alerts.md)
- [التحقق من الأجهزة في Microsoft Defender لنقطة النهاية الأجهزة](investigate-machines.md)
- [التحقق من عنوان IP المقترن بتنبيه Microsoft Defender لنقطة النهاية الإنترنت](investigate-ip.md)
- [التحقق من مجال مقترن بتنبيه Microsoft Defender لنقطة النهاية](investigate-domain.md)
- [التحقق من حساب مستخدم في Microsoft Defender لنقطة النهاية](investigate-user.md)
- [اتخاذ إجراءات الاستجابة على ملف](respond-file-alerts.md)
