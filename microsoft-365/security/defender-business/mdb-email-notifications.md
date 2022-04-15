---
title: إعداد إعلامات البريد الإلكتروني لفريق الأمان
description: إعداد إعلامات البريد الإلكتروني لإبلاغ الأشخاص بالتنبيهات والثغرات الأمنية باستخدام Microsoft Defender for Business
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: overview
ms.date: 04/12/2022
ms.prod: m365-security
ms.technology: mdb
ms.localizationpriority: medium
ms.reviewer: inbadian, shlomiakirav
f1.keywords: NOCSH
ms.collection: M365-security-compliance
ms.openlocfilehash: a65634a5827e60d710cec56ca10835c73053cb10
ms.sourcegitcommit: e3bc6563037bd2cce2abf108b3d1bcc2ccf538f6
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/15/2022
ms.locfileid: "64862841"
---
# <a name="set-up-email-notifications"></a>إعداد إعلامات البريد الإلكتروني

> [!NOTE]
> تم تضمين Microsoft Defender for Business الآن في [Microsoft 365 Business Premium](../../business-premium/index.md). 

يمكنك إعداد إعلامات البريد الإلكتروني لفريق الأمان. بعد ذلك، عند إنشاء التنبيهات، أو اكتشاف ثغرات أمنية جديدة، سيتم إعلام الأشخاص في فريق الأمان تلقائيا. 

## <a name="what-to-do"></a>ما يجب فعله

1. [تعرف على أنواع إعلامات البريد الإلكتروني](#types-of-email-notifications).

2. [عرض إعدادات إعلام البريد الإلكتروني وتحريرها](#view-and-edit-email-notifications).

3. [تابع إلى خطواتك التالية](#next-steps).


>
> **هل لديك دقيقة؟**
> يرجى أخذ <a href="https://microsoft.qualtrics.com/jfe/form/SV_0JPjTPHGEWTQr4y" target="_blank">استطلاعنا القصير حول الأمان</a>. يسعدنا أن نستمع إليك!
>

## <a name="types-of-email-notifications"></a>أنواع إعلامات البريد الإلكتروني

عند إعداد إعلامات البريد الإلكتروني، يمكنك الاختيار من بين نوعين، كما هو موضح في الجدول التالي:

| نوع الإعلام  | الوصف  |
|---------|---------|
| نقاط الضعف  | كلما تم الكشف عن أي مهاجمات أو أحداث ثغرة أمنية جديدة، يتلقى المستلمون رسالة بريد إلكتروني. |
| التنبيهات & الثغرات الأمنية  | عند إنشاء التنبيهات بسبب اكتشاف التهديدات على الأجهزة، أو عند الكشف عن أي مهاجمات أو أحداث ثغرة أمنية جديدة، يتلقى المستلمون رسالة بريد إلكتروني. |

> [!TIP]
> **إعلامات البريد الإلكتروني ليست الطريقة الوحيدة التي يمكن لفريق الأمان من خلالها معرفة التنبيهات أو الثغرات الأمنية الجديدة**.
> 
> تعد إعلامات البريد الإلكتروني طريقة ملائمة للمساعدة في إبقاء فريق الأمان على علم، في الوقت الحقيقي. ولكن هناك آخرون! على سبيل المثال، كلما قام فريق الأمان بتسجيل الدخول إلى مدخل Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com))، سيرى البطاقات التي تسلط الضوء على التهديدات والتنبيهات والثغرات الأمنية الجديدة. تم تصميم Defender for Business لتسليط الضوء على المعلومات المهمة التي يهتم بها فريق الأمان بمجرد تسجيل الدخول.
> 
> يمكن لفريق الأمان أيضا اختيار **"الحوادث"** في جزء التنقل لعرض المعلومات. لمعرفة المزيد، راجع [عرض الحوادث وإدارتها في Microsoft Defender for Business](mdb-view-manage-incidents.md).

## <a name="view-and-edit-email-notifications"></a>عرض إعلامات البريد الإلكتروني وتحريرها

لعرض إعدادات إعلام البريد الإلكتروني لشركتك أو تحريرها، اتبع الخطوات التالية:

1. انتقل إلى مدخل Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)) وسجل الدخول.

2. في جزء التنقل، حدد **الإعدادات**، ثم حدد **نقاط النهاية**. ثم، ضمن **"عام**"، حدد **إعلامات البريد الإلكتروني**. 

3. راجع المعلومات الموجودة في علامتي التبويب **«Alerts** » و« **Vulnerabilities** ».

   - إذا لم تتمكن من رؤية أي عناصر مدرجة في علامة التبويب **"تنبيهات** "، يمكنك إنشاء قاعدة للأشخاص ليتم إعلامهم عند إنشاء التنبيهات. للحصول على تعليمات حول هذه المهمة، راجع [إنشاء قواعد لإعلامات التنبيه](../defender-endpoint/configure-email-notifications.md).

   - إذا لم تتمكن من رؤية أي عناصر مدرجة في علامة التبويب **"الثغرات الأمنية** "، يمكنك إنشاء قاعدة للأشخاص ليتم إعلامهم كلما تم اكتشاف ثغرة أمنية جديدة. للحصول على تعليمات حول هذه المهمة، راجع [إنشاء قواعد لأحداث الثغرات الأمنية](../defender-endpoint/configure-vulnerability-email-notifications.md).

   - إذا كانت لديك قواعد تم إنشاؤها، فحدد قاعدة لتحريرها. يمكنك أيضا حذف قاعدة. 

## <a name="next-steps"></a>الخطوات التالية

تابع إلى:

- [الخطوة 4: إلحاق الأجهزة Microsoft Defender for Business](mdb-onboard-devices.md)
