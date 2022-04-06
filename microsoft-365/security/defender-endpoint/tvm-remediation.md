---
title: إصلاح الثغرات باستخدام إدارة المخاطر والثغرات الأمنية
description: يمكنك معالجة نقاط ضعف الأمان التي تم اكتشافها من خلال توصيات الأمان، وإنشاء استثناءات إذا لزم الأمر، في إدارة المخاطر والثغرات الأمنية.
keywords: Microsoft Defender لنقطة النهاية، Microsoft Defender لنقطة النهاية tvm، إدارة المخاطر والثغرات الأمنية، & إدارة الثغرات الأمنية، & إدارة الثغرات الأمنية المعالجة، المعالجة بالتلفزيون intune، sccm المعالجة بالتلفزيون
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
- m365initiative-defender-endpoint
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: 9631c38279fbcfcbc4d55b09409af9bb16c783f6
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/25/2022
ms.locfileid: "64476654"
---
# <a name="remediate-vulnerabilities-with-threat-and-vulnerability-management"></a>إصلاح الثغرات باستخدام إدارة المخاطر والثغرات الأمنية

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**
- [Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [التهديدات إدارة الثغرات الأمنية](next-gen-threat-and-vuln-mgt.md)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> هل تريد تجربة Microsoft Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-portaloverview-abovefoldlink)

## <a name="request-remediation"></a>طلب المعالجة

تقوم إدارة المخاطر والثغرات الأمنية في Microsoft Defender لنقطة النهاية سد الفجوة بين مسؤولي الأمان ومسؤولي تكنولوجيا المعلومات من خلال سير عمل طلب المعالجة. يمكن لمسؤولي الأمان مثلك أن يطلبوا من مسؤول تكنولوجيا المعلومات معالجة ثغرة أمنية من صفحات **توصيات** الأمان إلى Intune.

### <a name="enable-microsoft-intune-connection"></a>تمكين Microsoft Intune الاتصال

لاستخدام هذه الإمكانية، يمكنك تمكين Microsoft Intune الاتصال. في مدخل Microsoft 365 Defender، **انتقل إلى الإعدادات** \> **الميزات** \> **المتقدمة العامة**. قم بالتمرير لأسفل وابحث عن **Microsoft Intune الاتصال**. بشكل افتراضي، يتم إيقاف تشغيل تبديل. قم Microsoft Intune **تشغيل** الاتصال **.**

**ملاحظة**: إذا تم تمكين اتصال Intune، يمكنك الحصول على خيار لإنشاء مهمة أمان Intune عند إنشاء طلب إصلاح. لا يظهر هذا الخيار إذا لم يتم تعيين الاتصال.

راجع [استخدام Intune](/intune/atp-manage-vulnerabilities) لإعادة معالجة الثغرات التي حددتها Microsoft Defender لنقطة النهاية للحصول على التفاصيل.

### <a name="remediation-request-steps"></a>خطوات طلب الإصلاح

1. انتقل إلى قائمة **التنقل الخاصة** بإدارة المخاطر والنقاط الضعف في مدخل Microsoft 365 Defender، **وحدد** التوصيات [**الأمان**](tvm-security-recommendation.md).

2. حدد توصية أمان تريد طلب المعالجة لها، ثم حدد **خيارات الإصلاح**.

3. املأ النموذج، بما في ذلك ما تطلب المعالجة له ومجموعات الأجهزة القابلة للتطبيق والأولوية وتاريخ الاستحقاق والملاحظات الاختيارية.
    1. إذا اخترت خيار المعالجة "مطلوب الانتباه"، فإن تحديد تاريخ الاستحقاق لن يكون متوفرا نظرا لأنه لا يوجد أي إجراء محدد.

4. حدد **إرسال الطلب**. ينشئ إرسال طلب إصلاح عنصر نشاط إصلاح ضمن إدارة المخاطر والثغرات الأمنية، والذي يمكن استخدامه لمراقبة تقدم المعالجة لهذه التوصية. لن يؤدي ذلك إلى تشغيل المعالجة أو تطبيق أي تغييرات على الأجهزة.

5. قم بإعلام مسؤول تكنولوجيا المعلومات لديك حول الطلب الجديد واطلب منه تسجيل الدخول إلى Intune للموافقة على الطلب أو رفضه وبدء نشر حزمة.

6. انتقل إلى [**صفحة "المعالجة**](tvm-remediation.md) " لعرض حالة طلب المعالجة.

إذا كنت تريد التحقق من كيفية عرض التذكرة في Intune، فتحقق من استخدام [Intune](/intune/atp-manage-vulnerabilities) في معالجة الثغرات التي حددتها Microsoft Defender لنقطة النهاية للحصول على التفاصيل.

> [!NOTE]
> إذا كان طلبك يتضمن معالجة أكثر من 10000 جهاز، يمكننا فقط إرسال 10000 جهاز لإعادة المعالجة إلى Intune.

بعد تحديد نقاط ضعف الأمان الإلكتروني في مؤسستك و تعيينها إلى توصيات أمان قابلة للتنفيذ، ابدأ [](tvm-security-recommendation.md)في إنشاء مهام الأمان. يمكنك إنشاء المهام من خلال التكامل مع Microsoft Intune التي يتم فيها إنشاء تذاكر الإصلاح.

اخفض من تعرض مؤسستك لنقاط الضعف وزيد من تكوين الأمان من خلال معالجة توصيات الأمان.

## <a name="view-your-remediation-activities"></a>عرض أنشطة الإصلاح

عند إرسال طلب إصلاح من صفحة توصيات الأمان، فإنه ينطلق نشاط المعالجة. يتم إنشاء مهمة أمان يمكن تعقبها في صفحة إدارة المخاطر والثغرات الأمنية، كما يتم إنشاء تذكرة إصلاح في  Microsoft Intune.

إذا اخترت خيار المعالجة "مطلوب الانتباه"، لن يكون هناك شريط تقدم أو حالة تذكرة أو تاريخ الاستحقاق نظرا لأنه لا يوجد أي إجراء فعلي يمكننا مراقبته.

عندما تكون في صفحة المعالجة، حدد نشاط المعالجة الذي تريد عرضه. يمكنك اتباع خطوات الإصلاح أو تعقب التقدم أو عرض التوصية ذات الصلة أو التصدير إلى CSV أو وضع علامة كمكتملة.

:::image type="content" source="../../media/remediation-flyouteolswnew.png" alt-text="صفحة &quot;المعالجة&quot;، التي تحتوي على نشاط إصلاح محدد، مع قائمة من القائمة من خلال هذا النشاط سرد الوصف، وأدوات إدارة الأجهزة وخدمة المعلومات، و&quot;إصلاح الجهاز&quot;" lightbox="../../media/remediation-flyouteolswnew.png":::

> [!NOTE]
> هناك فترة استبقاء لمدة 180 يوما لأنشطة المعالجة المكتملة. للحفاظ على أداء صفحة "المعالجة" على أفضل وجه، تتم إزالة نشاط المعالجة بعد 6 أشهر من اكتمالها.

### <a name="completed-by-column"></a>مكتمل حسب العمود

تعقب الأشخاص الذين أغلقوا نشاط المعالجة باستخدام العمود "مكتمل بواسطة" على صفحة "المعالجة".

- **عنوان البريد** الإلكتروني: البريد الإلكتروني للشخص الذي أكمل المهمة يدويا
- **تأكيد النظام**: تم إكمال المهمة تلقائيا (تم إصلاح جميع الأجهزة)
- **N/A**: المعلومات غير متوفرة لأننا لا نعرف كيفية إكمال هذه المهمة القديمة

:::image type="content" source="images/tvm-completed-by.png" alt-text="تم إنشاؤه بواسطة وإكماله بواسطة أعمدة ذات صفين" lightbox="images/tvm-completed-by.png":::

### <a name="top-remediation-activities-in-the-dashboard"></a>أهم أنشطة الإصلاح في لوحة المعلومات

عرض **أهم أنشطة المعالجة** في لوحة [معلومات إدارة المخاطر **والضعف**](tvm-dashboard-insights.md). حدد أي من الإدخالات التي تريد الانتقال إلى **صفحة "المعالجة** ". يمكنك وضع علامة على نشاط المعالجة على أنه مكتمل بعد أن يتوسط فريق مسؤول المعلومات المهمة.

:::image type="content" source="images/tvm-remediation-activities-card.png" alt-text="بطاقة أهم أنشطة الإصلاح" lightbox="images/tvm-remediation-activities-card.png":::

## <a name="related-articles"></a>المقالات ذات الصلة

- [نظرة عامة إدارة الثغرات الأمنية المخاطر](next-gen-threat-and-vuln-mgt.md)
- [لوحة المعلومات](tvm-dashboard-insights.md)
- [توصيات الأمان](tvm-security-recommendation.md)