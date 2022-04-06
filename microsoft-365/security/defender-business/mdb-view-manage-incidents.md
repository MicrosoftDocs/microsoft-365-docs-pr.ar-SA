---
title: عرض الأحداث وإدارتها في Microsoft Defender for Business
description: تعرف على كيفية عرض & التنبيهات والاستجابة للتهديدات وإدارة الأجهزة ومراجعة إجراءات المعالجة
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: how-to
ms.date: 03/15/2022
ms.prod: m365-security
ms.technology: mdb
ms.localizationpriority: medium
ms.reviewer: shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
- m365-initiative-defender-business
ms.openlocfilehash: a814aa4ad002672fa3451ef1bcc524d9b03d4eb5
ms.sourcegitcommit: 3fb76db6b34e24569417f4c8a41b99f46a780389
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/17/2022
ms.locfileid: "63583772"
---
# <a name="view-and-manage-incidents-in-microsoft-defender-for-business"></a>عرض الأحداث وإدارتها في Microsoft Defender for Business

> [!IMPORTANT]
> يتم طرح Microsoft Defender for Business Microsoft 365 Business Premium العملاء[](../../business-premium/index.md)، بدءا من 1 مارس 2022. يتم عرض Defender for Business لاشتراك مستقل في المعاينة، وسينتهى طرحه تدريجيا للعملاء وشركاء المعلومات الذين سجلوا هنا [](https://aka.ms/mdb-preview) لطلبه. تتضمن [المعاينة مجموعة أولية من السيناريوهات](mdb-tutorials.md#try-these-preview-scenarios)، وسنضيف القدرات بشكل منتظم.
> 
> تتعلق بعض المعلومات الواردة في هذه المقالة بالمنتجات/الخدمات التي تم إصدارها مسبقا التي قد يتم تعديلها بشكل كبير قبل إصدارها تجاريا. لا تقدم Microsoft أي ضمانات، صريحة أو ضمنية، للمعلومات المتوفرة هنا. 

عند اكتشاف التهديدات وتنبيهات يتم تشغيلها، يتم إنشاء أحداث. يمكن لفريق الأمان في شركتك عرض الأحداث وإدارتها في Microsoft 365 Defender الإلكتروني.

**تتضمن هذه المقالة**:

- [كيفية مراقبة الأحداث والتنبيهات](#monitor-your-incidents--alerts)

- [خطورة التنبيه](#alert-severity)

- [الخطوات التالية](#next-steps)

>
> **هل لديك دقيقة؟**
> الرجاء إجراء <a href="https://microsoft.qualtrics.com/jfe/form/SV_0JPjTPHGEWTQr4y" target="_blank">استطلاع قصير حول Microsoft Defender for Business</a>. إننا نحب أن نستمع إلى هذه التكاتف!
>

## <a name="monitor-your-incidents--alerts"></a>مراقبة الأحداث & تنبيهاتك

1. في Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com))، في جزء التنقل، حدد **أحداث**. يتم سرد أي أحداث تم إنشاؤها على الصفحة.

   :::image type="content" source="../../media/defender-business/mdb-incidents-list.png" alt-text="لقطة شاشة للقائمة &quot;أحداث&quot;":::

2. حدد تنبيها لفتح جزء منبه، حيث يمكنك معرفة المزيد حول التنبيه. 

   :::image type="content" source="../../media/defender-business/mdb-incident-flyout.png" alt-text="لقطة شاشة لحادث تم تحديده مع فتح منتحل منتحل":::

3. في جزء القائمة المنبهة، يمكنك رؤية عنوان التنبيه، وعرض قائمة الأصول (مثل نقاط النهاية أو حسابات المستخدمين) التي تأثرت، واتخاذ الإجراءات المتوفرة، واستخدام الارتباطات لعرض المزيد من المعلومات وحتى فتح صفحة التفاصيل الخاصة بالتنبيه المحدد. 

> [!TIP]
> تم تصميم Microsoft Defender for Business لمساعدتك على معالجة التهديدات التي تم الكشف عنها من خلال تقديم الإجراءات الموصى بها. عند عرض تنبيه، ابحث عن الإجراءات المستحسنة التي يجب اتخاذها. تجدر الإشارة أيضا إلى خطورة التنبيه، التي يتم تحديدها ليس فقط على أساس خطورة التهديدات، ولكن أيضا على مستوى الخطر الذي تواجهه شركتك. 

## <a name="alert-severity"></a>شدة التنبيه

عندما يقوم برنامج الحماية من الفيروسات من Microsoft Defender بتعيين خطورة التنبيه استنادا إلى الخطورة المطلقة للتهديد المكتشف (البرامج الضارة) والمخاطر المحتملة لنقطة نهاية فردية (إذا كانت ملوثة).
يعين Microsoft Defender for Business خطورة التنبيه استنادا إلى خطورة السلوك الذي تم الكشف عنه، والمخاطر الفعلية لنقطة نهاية (جهاز)، والأهم من ذلك، المخاطر المحتملة التي قد تخطر على شركتك. يسرد الجدول التالي بعض الأمثلة: <br/><br/>

| السيناريو | شدة التنبيه | السبب |
|:---|:---|:---|
| برنامج الحماية من الفيروسات من Microsoft Defender عن أي خطر ويوقفه قبل حدوث أي تلف. | معلوماتية | تم إيقاف هذا التهديد قبل حدوث أي أضرار. |
| برنامج الحماية من الفيروسات من Microsoft Defender عن البرامج الضارة التي كانت تنفذ داخل شركتك. يتم إيقاف البرامج الضارة و إصلاحها. | منخفض | على الرغم من أنه من المحتمل حدوث بعض الأضرار في نقطة نهاية فردية، إلا أن البرامج الضارة لا تشكل الآن أي خطر على شركتك. |
| يتم الكشف عن البرامج الضارة التي يتم تنفيذها بواسطة Microsoft Defender for Business. يتم حظر البرامج الضارة على الفور تقريبا. | متوسط أو عال | تشكل البرامج الضارة خطرا على نقاط النهاية الفردية وعلى شركتك. |
| يتم اكتشاف سلوك مريب ولكن لا يتم اتخاذ أي إجراءات إصلاح بعد. | منخفض أو متوسط أو عال | تعتمد الخطورة على الدرجة التي يشكل السلوك بها خطرا على شركتك. |

## <a name="next-steps"></a>الخطوات التالية

- [الاستجابة للتهديدات وتخفيفها في Microsoft Defender for Business](mdb-respond-mitigate-threats.md)

- [مراجعة إجراءات المعالجة في مركز الإجراءات](mdb-review-remediation-actions.md)

- [عرض سياسات الأجهزة أو تحريرها في Microsoft Defender for Business](mdb-view-edit-policies.md)