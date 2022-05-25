---
title: التحقيق في ملفات Microsoft Defender لنقطة النهاية
description: استخدم خيارات التحقيق للحصول على تفاصيل حول الملفات المرتبطة بالتنبيهات أو السلوكيات أو الأحداث.
keywords: التحقيق، والتحقيق، والملف، والنشاط الضار، ودوافع الهجوم، والتحليل العميق، وتقرير التحليل العميق
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
ms.openlocfilehash: c1f6fa058715f831b1c8ba594bf1604ad92e9ed2
ms.sourcegitcommit: 6c2ab5e8efe74d0dc2df610e2d9d2fdda8aaf074
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 05/25/2022
ms.locfileid: "65669353"
---
# <a name="investigate-a-file-associated-with-a-microsoft-defender-for-endpoint-alert"></a>التحقيق في ملف مقترن بتنبيه Microsoft Defender لنقطة النهاية

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**
- [الخطة 1 من Microsoft Defender لنقطة النهاية](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Defender for Endpoint الخطة 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)


> هل تريد تجربة Defender لنقطة النهاية؟ [التسجيل للحصول على إصدار تجريبي مجاني.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-investigatefiles-abovefoldlink)

تحقق من تفاصيل ملف مقترن بتنبيه أو سلوك أو حدث معين للمساعدة في تحديد ما إذا كان الملف يعرض أنشطة ضارة، وتحديد الدافع للهجوم، وفهم النطاق المحتمل للخرق.

هناك العديد من الطرق للوصول إلى صفحة ملف التعريف التفصيلي لملف معين. على سبيل المثال، يمكنك استخدام ميزة البحث أو النقر فوق ارتباط من **شجرة عملية التنبيه** أو **الرسم البياني للحوادث** أو **المخطط الزمني للبيانات الاصطناعية** أو تحديد حدث مدرج في **المخطط الزمني للجهاز**.

بمجرد الوصول إلى صفحة ملف التعريف المفصلة، يمكنك التبديل بين تخطيطات الصفحة الجديدة والقديمة عن طريق تبديل **صفحة ملف جديدة**. تصف بقية هذه المقالة تخطيط الصفحة الأحدث.

يمكنك الحصول على معلومات من المقاطع التالية في طريقة عرض الملف:

- تفاصيل الملف، الكشف عن البرامج الضارة، انتشار الملف
- بيانات تعريف PE لملف (إذا كانت موجودة)
- تحليل عميق
- التنبيهات
- تمت ملاحظته في المؤسسة
- تحليل عميق
- أسماء الملفات

يمكنك أيضا اتخاذ إجراء على ملف من هذه الصفحة.

## <a name="file-actions"></a>إجراءات الملف

على طول الجزء العلوي من صفحة ملف التعريف، أعلى بطاقات معلومات الملف. تتضمن الإجراءات التي يمكنك تنفيذها هنا ما يلي:

- الإيقاف والعزل
- إضافة/تحرير المؤشر
- تنزيل الملف
- استشارة خبير في التهديدات
- مركز الصيانة

لمزيد من المعلومات حول هذه الإجراءات، راجع [اتخاذ إجراء استجابة على ملف](respond-file-alerts.md).

## <a name="file-details-malware-detection-and-file-prevalence"></a>تفاصيل الملف، والكشف عن البرامج الضارة، وانتشار الملفات

تعرض تفاصيل الملف والحوادث واكتشاف البرامج الضارة وبطاقات انتشار الملفات سمات مختلفة حول الملف.

سترى تفاصيل مثل MD5 للملف، ونسبة الكشف عن إجمالي الفيروسات، والكشف عن Microsoft Defender AV إذا كان متوفرا، وانتشار الملف.

تظهر بطاقة انتشار الملفات مكان ظهور الملف في الأجهزة في المؤسسة وفي جميع أنحاء العالم. يمكنك بسهولة محورية إلى الأجهزة الأولى والأخيرة حيث تمت رؤية الملف، ومتابعة التحقيق في المخطط الزمني للجهاز. 

> [!NOTE]
> قد يرى المستخدمون المختلفون قيما غير متطابقة في *الأجهزة في قسم المؤسسة* من بطاقة انتشار الملفات. وذلك لأن البطاقة تعرض المعلومات استنادا إلى نطاق RBAC الذي يملكه المستخدم. بمعنى أنه إذا تم منح المستخدم رؤية على مجموعة معينة من الأجهزة، فسيرى فقط انتشار تنظيم الملف على تلك الأجهزة.

:::image type="content" source="images/atp-file-information.png" alt-text="معلومات الملف" lightbox="images/atp-file-information.png":::

## <a name="alerts"></a>التنبيهات

توفر علامة التبويب **Alerts** قائمة بالتنبيهات المقترنة بالملف، بالإضافة إلى الحدث المرتبط بالتنبيه. تغطي هذه القائمة الكثير من المعلومات نفسها مثل قائمة انتظار التنبيهات، باستثناء مجموعة الأجهزة، إن وجدت، التي ينتمي إليها الجهاز المتأثر. يمكنك اختيار نوع المعلومات التي يتم عرضها عن طريق تحديد **تخصيص الأعمدة من شريط الأدوات** أعلى رؤوس الأعمدة.

:::image type="content" source="images/atp-alerts-related-to-file.png" alt-text="التنبيهات المتعلقة بمقطع الملف" lightbox="images/atp-alerts-related-to-file.png":::

## <a name="observed-in-organization"></a>تمت ملاحظته في المؤسسة

تسمح لك علامة التبويب **Observed in organization** بتحديد نطاق تاريخ لمعرفة الأجهزة التي تمت ملاحظتها مع الملف.

> [!NOTE]
> ستظهر علامة التبويب هذه عددا أقصى من 100 جهاز. لمشاهدة _جميع_ الأجهزة التي تحتوي على الملف، قم بتصدير علامة التبويب إلى ملف CSV، عن طريق تحديد **"تصدير** " من قائمة الإجراءات أعلى رؤوس أعمدة علامة التبويب.

:::image type="content" source="images/atp-observed-machines.png" alt-text="أحدث الأجهزة التي تمت ملاحظتها مع الملف" lightbox="images/atp-observed-machines.png":::

استخدم شريط التمرير أو محدد النطاق لتحديد فترة زمنية تريد التحقق منها بسرعة بحثا عن الأحداث التي تتضمن الملف. يمكنك الحصول على مساعدة من إشارة التنبيهات عبر النطاق. يمكنك تحديد نافذة زمنية صغيرة مثل يوم واحد. سيسمح لك هذا برؤية الملفات التي اتصلت بعنوان IP هذا فقط في ذلك الوقت، ما يقلل بشكل كبير من التمرير والبحث غير الضروريين.

## <a name="deep-analysis"></a>تحليل عميق

تسمح لك علامة التبويب **Deep analysis** [بإرسال الملف للتحليل العميق](respond-file-alerts.md#deep-analysis)، للكشف عن مزيد من التفاصيل حول سلوك الملف، بالإضافة إلى التأثير الذي يحدثه داخل مؤسستك. بعد إرسال الملف، سيظهر تقرير التحليل العميق في علامة التبويب هذه بمجرد توفر النتائج. إذا لم يعثر التحليل العميق على أي شيء، فسيكون التقرير فارغا وستظل مساحة النتائج فارغة.

:::image type="content" source="images/submit-file.png" alt-text="علامة التبويب Deep analysis" lightbox="images/submit-file.png":::

## <a name="file-names"></a>أسماء الملفات

تسرد علامة التبويب **"أسماء** الملفات" كافة الأسماء التي تمت ملاحظة استخدام الملف فيها، داخل مؤسستك.

:::image type="content" source="images/atp-file-names.png" alt-text="علامة التبويب &quot;أسماء الملفات&quot;" lightbox="images/atp-file-names.png":::

## <a name="action-center"></a>مركز الصيانة

يعرض **مركز الصيانة** مركز الصيانة الذي تمت تصفيته على ملف معين، حتى تتمكن من رؤية الإجراءات المعلقة ومحفوظات الإجراءات التي تم اتخاذها على الملف.

## <a name="related-topics"></a>المواضيع ذات الصلة

- [عرض قائمة انتظار Microsoft Defender لنقطة النهاية وتنظيمها](alerts-queue.md)
- [إدارة تنبيهات Microsoft Defender لنقطة النهاية](manage-alerts.md)
- [التحقيق في تنبيهات Microsoft Defender لنقطة النهاية](investigate-alerts.md)
- [التحقق من الأجهزة في قائمة أجهزة Microsoft Defender لنقطة النهاية](investigate-machines.md)
- [التحقيق في عنوان IP المقترن بتنبيه Microsoft Defender لنقطة النهاية](investigate-ip.md)
- [التحقيق في مجال مقترن بتنبيه Microsoft Defender لنقطة النهاية](investigate-domain.md)
- [التحقيق في حساب مستخدم في Microsoft Defender لنقطة النهاية](investigate-user.md)
- [اتخاذ إجراءات الاستجابة على ملف](respond-file-alerts.md)
