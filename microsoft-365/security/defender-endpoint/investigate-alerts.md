---
title: التحقق من تنبيهات نقطة النهاية ل Microsoft Defender
description: استخدم خيارات التحقيق للحصول على تفاصيل حول التنبيهات التي تؤثر على شبكتك ومعناها وكيفية حلها.
keywords: التحقيق، التحقيق، الأجهزة، الجهاز، قائمة انتظار التنبيهات، لوحة المعلومات، عنوان IP، ملف، إرسال، عمليات الإرسال، التحليل العميق، المخطط الزمني، البحث، المجال، عنوان URL، IP
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
ms.openlocfilehash: f228d0ca44589b9c140226c2b39984c717c7d9f8
ms.sourcegitcommit: 6e90baef421ae06fd790b0453d3bdbf624b7f9c0
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 02/12/2022
ms.locfileid: "63571537"
---
# <a name="investigate-alerts-in-microsoft-defender-for-endpoint"></a>التحقق من التنبيهات في Microsoft Defender لنقطة النهاية

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**
- [خطة Microsoft Defender لنقطة النهاية 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> هل تريد تجربة Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-investigatealerts-abovefoldlink)

تحقق من التنبيهات التي تؤثر على شبكتك، وافهم معاناتها، وكيفية حلها.

حدد تنبيها من قائمة انتظار التنبيهات للذهاب إلى صفحة التنبيه. تحتوي طريقة العرض هذه على عنوان التنبيه والأصول المتأثرة والجانب الجانبي التفاصيل وقصه التنبيه.

من صفحة التنبيه، ابدأ التحقيق بتحديد الأصول المتأثرة أو أي من الوحدات ضمن طريقة عرض شجرة قصة التنبيه. يتم ملء جزء التفاصيل تلقائيا بمعلومات إضافية حول ما قمت بتحديده. لمعرفة نوع المعلومات التي يمكنك عرضها هنا، اقرأ [مراجعة التنبيهات في Microsoft Defender لنقطة النهاية](/microsoft-365/security/defender-endpoint/review-alerts).

## <a name="investigate-using-the-alert-story"></a>التحقق باستخدام قصة التنبيه

تفصيل قصة التنبيه سبب تشغيل التنبيه، والأحداث ذات الصلة التي حدثت قبل ذلك وبعده، بالإضافة إلى الكيانات الأخرى ذات الصلة.

الكيانات قابلة للنقر وكل كيان ليس تنبيه قابلا للتوسع باستخدام أيقونة التوسع على الجانب الأيسر من بطاقة ذلك الكيان. سيتم الإشارة إلى الكيان الذي يتم التركيز عليه بواسطة شريط أزرق إلى الجانب الأيمن من بطاقة ذلك الكيان، مع التركيز على التنبيه في العنوان في بادئ الأمر.

قم بتوسيع الوحدات لعرض التفاصيل بنظرة سريعة. سيبدل تحديد كيان سياق جزء التفاصيل إلى هذا الكيان، وسيسمح لك بمراجعة مزيد من المعلومات، بالإضافة إلى إدارة ذلك الكيان. سيكشف *تحديد ...* على الجانب الأيمن من بطاقة الكيان كل الإجراءات المتوفرة لذلك الكيان. تظهر هذه الإجراءات نفسها في جزء التفاصيل عندما يكون هذا الكيان في التركيز.

> [!NOTE]
> قد يحتوي مقطع قصة التنبيه على أكثر من تنبيه واحد، مع ظهور تنبيهات إضافية ذات صلة بنفس شجرة التنفيذ قبل التنبيه الذي حددته أو بعده.

![مثال على قصة تنبيه مع وضع تنبيه في التركيز وبعض البطاقات الموسعة.](images/alert-story-tree.png)

## <a name="take-action-from-the-details-pane"></a>اتخاذ إجراء من جزء التفاصيل

بعد تحديد كيان يهمك، سيتغير جزء التفاصيل لعرض معلومات حول نوع الكيان المحدد والمعلومات التاريخية عند توفرها، وعرض عناصر التحكم لاتخاذ إجراء على هذا الكيان مباشرة من صفحة التنبيه.

بعد أن تنجز عملية التحقق، ارجع إلى التنبيه الذي بدأت به، وضع علامة على حالة التنبيه على أنها تم حلها وصنفها كتنبيه خاطئ  أو **تنبيه True**. يساعد تصنيف التنبيهات على ضبط هذه الإمكانية لتوفير تنبيهات أكثر حقيقا وتنبيهات أقل خطأ.

إذا قمت بتصنيفه كتنبيه حقيقي، يمكنك أيضا تحديد تحديد، كما هو موضح في الصورة أدناه.

![قصاصة جزء التفاصيل مع تنبيه تم حله وتوسيع منسدل التحديد.](images/alert-details-resolved-true.png)

إذا كنت تواجه تنبيها خاطئا باستخدام تطبيق خط العمل، فقم بإنشاء قاعدة منع لتجنب هذا النوع من التنبيهات في المستقبل.

![الإجراءات والتصنيف في جزء التفاصيل مع تمييز قاعدة القمع.](images/alert-false-suppression-rule.png)

> [!TIP]
> إذا كنت تواجه أي 🙂 مشاكل غير موضحة أعلاه، فاستخدم الزر لتقديم ملاحظات أو فتح تذكرة دعم.


## <a name="related-topics"></a>المواضيع ذات الصلة
- [عرض قائمة انتظار تنبيهات نقطة النهاية في Microsoft Defender وتنظيمها](alerts-queue.md)
- [إدارة تنبيهات Microsoft Defender لنقطة النهاية](manage-alerts.md)
- [التحقق من ملف مقترن بتنبيه Defender لنقطة النهاية](investigate-files.md)
- [التحقق من الأجهزة في القائمة "Defender for Endpoint Devices"](investigate-machines.md)
- [التحقق من عنوان IP مقترن بتنبيه Defender لنقطة النهاية](investigate-ip.md)
- [التحقق من مجال مقترن بتنبيه Defender لنقطة النهاية](investigate-domain.md)
- [التحقق من حساب مستخدم في Defender لنقطة النهاية](investigate-user.md)


