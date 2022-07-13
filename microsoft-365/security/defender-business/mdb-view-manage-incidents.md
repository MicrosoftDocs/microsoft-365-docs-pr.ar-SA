---
title: عرض الحوادث وإدارتها في Microsoft Defender for Business
description: عرض التنبيهات وإدارتها، والاستجابة للتهديدات، وإدارة الأجهزة، ومراجعة إجراءات المعالجة على التهديدات المكتشفة في Defender for Business.
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: how-to
ms.prod: m365-security
ms.technology: mdb
ms.localizationpriority: medium
ms.reviewer: shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
- m365-initiative-defender-business
ms.openlocfilehash: 0072cd6088d7fa560e5dbd6f449b766cb6afb694
ms.sourcegitcommit: fa90763559239c4c46c5e848939126763879d8e4
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/13/2022
ms.locfileid: "66772632"
---
# <a name="view-and-manage-incidents-in-microsoft-defender-for-business"></a>عرض الحوادث وإدارتها في Microsoft Defender for Business

مع اكتشاف التهديدات وتشغيل التنبيهات، يتم إنشاء الحوادث. يمكن لفريق أمان شركتك عرض الحوادث وإدارتها في مدخل Microsoft 365 Defender.

**تتضمن هذه المقالة**:

- [كيفية مراقبة الحوادث والتنبيهات](#monitor-your-incidents--alerts)
- [خطورة التنبيه](#alert-severity)
- [الخطوات التالية](#next-steps)


## <a name="monitor-your-incidents--alerts"></a>مراقبة التنبيهات & الأحداث

1. في مدخل Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com))، في جزء التنقل، حدد **Incidents**. يتم سرد أي حوادث تم إنشاؤها على الصفحة.

   :::image type="content" source="../../media/defender-business/mdb-incidents-list.png" alt-text="لقطة شاشة لقائمة الحوادث":::

2. حدد تنبيها لفتح جزء القائمة المنبثقة الخاص به، حيث يمكنك معرفة المزيد حول التنبيه. 

   :::image type="content" source="../../media/defender-business/mdb-incident-flyout.png" alt-text="لقطة شاشة للحادث المحدد مع فتح القائمة المنبثقة":::

3. في جزء القائمة المنبثقة، يمكنك رؤية عنوان التنبيه، وعرض قائمة الأصول (مثل نقاط النهاية أو حسابات المستخدمين) التي تأثرت، واتخاذ الإجراءات المتوفرة، واستخدام الارتباطات لعرض المزيد من المعلومات وحتى فتح صفحة التفاصيل للتنبيه المحدد. 

> [!TIP]
> تم تصميم Defender for Business لمساعدتك على معالجة التهديدات المكتشفة من خلال تقديم إجراءات موصى بها. عند عرض تنبيه، ابحث عن الإجراءات الموصى بها التي يجب اتخاذها. لاحظ أيضا خطورة التنبيه، والتي يتم تحديدها ليس فقط على أساس خطورة التهديد، ولكن أيضا على مستوى المخاطر التي تتعرض لها شركتك. 

## <a name="alert-severity"></a>شدة التنبيه

عندما يقوم برنامج الحماية من الفيروسات من Microsoft Defender بتعيين خطورة تنبيه استنادا إلى الخطورة المطلقة للمخاطر المكتشفة (البرامج الضارة) والمخاطر المحتملة لنقطة نهاية فردية (إذا كانت مصابة). يعين Defender for Business خطورة تنبيه استنادا إلى خطورة السلوك المكتشف، والمخاطر الفعلية لنقطة نهاية (جهاز)، والأهم من ذلك، الخطر المحتمل لشركتك. يسرد الجدول التالي بعض الأمثلة:

| السيناريو | خطورة التنبيه وسببه |
|:---|:---|
| يكتشف برنامج الحماية من الفيروسات من Microsoft Defender التهديد ويوقفه قبل أن يتسبب في أي ضرر. | اعلاميه <br/><br/>تم إيقاف التهديد قبل حدوث أي تلف. |
| يكتشف برنامج الحماية من الفيروسات من Microsoft Defender البرامج الضارة التي كانت تنفذ داخل شركتك. يتم إيقاف البرامج الضارة ومعالجتها. | منخفضه <br/><br/>على الرغم من أن بعض الضرر قد يكون قد حدث لنقطة نهاية فردية، فإن البرامج الضارة الآن لا تشكل أي تهديد لشركتك. |
| يتم الكشف عن البرامج الضارة التي يتم تنفيذها بواسطة Defender for Business. يتم حظر البرامج الضارة على الفور تقريبا. | متوسط أو مرتفع <br/><br/>تشكل البرامج الضارة تهديدا لنقاط النهاية الفردية وشركتك. |
| يتم الكشف عن سلوك مريب ولكن لم يتم اتخاذ أي إجراءات معالجة حتى الآن. | منخفض أو متوسط أو مرتفع <br/><br/>تعتمد الخطورة على الدرجة التي يشكل بها السلوك تهديدا لشركتك. |

## <a name="next-steps"></a>الخطوات التالية

- [الاستجابة للتهديدات وتخفيفها في Defender for Business](mdb-respond-mitigate-threats.md)
- [مراجعة إجراءات المعالجة في مركز الصيانة](mdb-review-remediation-actions.md)
- [عرض نهج الأجهزة أو تحريرها في Defender for Business](mdb-view-edit-policies.md)