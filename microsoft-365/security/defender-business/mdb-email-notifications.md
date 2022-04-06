---
title: إعداد إعلامات البريد الإلكتروني لفريق الأمان
description: إعداد إعلامات البريد الإلكتروني لإخبار الأشخاص بالتنبيهات والثغرات الأمنية باستخدام Microsoft Defender for Business
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: overview
ms.date: 03/15/2022
ms.prod: m365-security
ms.technology: mdb
ms.localizationpriority: medium
ms.reviewer: inbadian, shlomiakirav
f1.keywords: NOCSH
ms.collection: M365-security-compliance
ms.openlocfilehash: bf11ed140d2e0609f2d12d1da3bcc448ff733235
ms.sourcegitcommit: b3530441288b2bc44342e00e9025a49721796903
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/20/2022
ms.locfileid: "63683132"
---
# <a name="set-up-email-notifications"></a>إعداد إعلامات البريد الإلكتروني

> [!IMPORTANT]
> يتم طرح Microsoft Defender for Business Microsoft 365 Business Premium العملاء[](../../business-premium/index.md)، بدءا من 1 مارس 2022. يتم عرض Defender for Business لاشتراك مستقل في المعاينة، وسينتهى طرحه تدريجيا للعملاء وشركاء المعلومات الذين سجلوا هنا [](https://aka.ms/mdb-preview) لطلبه. تتضمن [المعاينة مجموعة أولية من السيناريوهات](mdb-tutorials.md#try-these-preview-scenarios)، وسنضيف القدرات بشكل منتظم.
> 
> تتعلق بعض المعلومات الواردة في هذه المقالة بالمنتجات/الخدمات التي تم إصدارها مسبقا التي قد يتم تعديلها بشكل كبير قبل إصدارها تجاريا. لا تقدم Microsoft أي ضمانات، صريحة أو ضمنية، للمعلومات المتوفرة هنا. 

يمكنك إعداد إعلامات البريد الإلكتروني لفريق الأمان. بعد ذلك، عند إنشاء التنبيهات أو اكتشاف نقاط ضعف جديدة، سيتم إعلام الأشخاص في فريق الأمان تلقائيا. 

## <a name="what-to-do"></a>ما يجب فعله

1. [تعرف على أنواع إعلامات البريد الإلكتروني](#types-of-email-notifications).

2. [عرض إعدادات إعلامات البريد الإلكتروني وتحريرها](#view-and-edit-email-notifications).

3. [تابع إلى الخطوات التالية](#next-steps).


>
> **هل لديك دقيقة؟**
> الرجاء إجراء <a href="https://microsoft.qualtrics.com/jfe/form/SV_0JPjTPHGEWTQr4y" target="_blank">استطلاع قصير حول Microsoft Defender for Business</a>. إننا نحب أن نستمع إلى هذه التكاتف!
>

## <a name="types-of-email-notifications"></a>أنواع إعلامات البريد الإلكتروني

عند إعداد إعلامات البريد الإلكتروني، يمكنك الاختيار من نوعين، كما هو موضح في الجدول التالي: <br/><br/>

| نوع الإعلام  | الوصف  |
|---------|---------|
| نقاط الضعف  | عندما يتم اكتشاف أي حالات استغلال جديدة أو أحداث ثغرة أمنية جديدة، يتلقى المستلمون رسالة بريد إلكتروني. |
| التنبيهات & الثغرات  | عند إنشاء التنبيهات بسبب اكتشاف التهديدات على الأجهزة، أو عند اكتشاف أي حالات استغلال جديدة أو أحداث ثغرة أمنية جديدة، يتلقى المستلمون رسالة بريد إلكتروني. |

> [!TIP]
> **لا تكون إعلامات البريد الإلكتروني الطريقة الوحيدة التي يمكن** لفريق الأمان بها معرفة التنبيهات الجديدة أو نقاط الضعف الجديدة.
> 
> إعلامات البريد الإلكتروني هي طريقة ملائمة للمساعدة في إبقاء فريق الأمان على اطلاع في الوقت الحقيقي. ولكن هناك آخرون! على سبيل المثال، كلما سجل فريق الأمان دخوله Microsoft 365 Defender المدخل ([https://security.microsoft.com](https://security.microsoft.com))، سيشاهد البطاقات التي تسلط الضوء على التهديدات والتنبيهات الجديدة ونقاط الضعف. تم تصميم Defender for Business لتمييع المعلومات المهمة التي يهتم بها فريق الأمان بمجرد تسجيل الدخول.
> 
> يمكن لفريق الأمان أيضا اختيار **"أحداث** " في جزء التنقل لعرض المعلومات. لمعرفة المزيد، راجع [عرض الأحداث وإدارتها في Microsoft Defender for Business](mdb-view-manage-incidents.md).

## <a name="view-and-edit-email-notifications"></a>عرض إعلامات البريد الإلكتروني وتحريرها

لعرض إعدادات إعلامات البريد الإلكتروني أو تحريرها للشركة، اتبع الخطوات التالية:

1. انتقل إلى Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)) ثم سجل الدخول.

2. في جزء التنقل **، حدد الإعدادات**، ثم حدد **نقاط النهاية**. بعد ذلك، ضمن **عام**، حدد **إعلامات البريد الإلكتروني**. 

3. راجع المعلومات في علامات **التبويب التنبيهات** **والنقاط** الأمنية.

   - إذا لم تتمكن من رؤية أي عناصر مدرجة في علامة التبويب تنبيهات، يمكنك إنشاء قاعدة للأشخاص الذين سيتم إعلامهم عند إنشاء التنبيهات. للحصول على تعليمات حول هذه المهمة، راجع [إنشاء قواعد لإشعارات التنبيهات](../defender-endpoint/configure-email-notifications.md).

   - إذا لم تتمكن من رؤية أي عناصر مدرجة في علامة التبويب الثغرات  الأمنية، يمكنك إنشاء قاعدة للأشخاص الذين سيتم إعلامهم كلما تم اكتشاف ثغرة أمنية جديدة. للحصول على تعليمات حول هذه المهمة، راجع [إنشاء قواعد أحداث ثغرة أمنية](../defender-endpoint/configure-vulnerability-email-notifications.md).

   - إذا تم إنشاء قواعد، فحدد قاعدة لتحريرها. يمكنك أيضا حذف قاعدة. 

## <a name="next-steps"></a>الخطوات التالية

تابع إلى:

- [الخطوة 4: الأجهزة المجهزة على Microsoft Defender for Business](mdb-onboard-devices.md)
