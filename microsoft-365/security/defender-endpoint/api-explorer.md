---
title: مستكشف API في Microsoft Defender لنقطة النهاية
ms.reviewer: ''
description: استخدام "مستكشف API" لإنشاء استعلامات API واختبارها وإرسالها لأية API متوفرة
keywords: api، مستكشف، إرسال، طلب، الحصول، نشر،
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: conceptual
ms.technology: mde
ms.custom: api
ms.openlocfilehash: 6e7d0e5927a85f2f3952221c294fe2387c268546
ms.sourcegitcommit: 348f3998a029a876a9dcc031f808e9e350804f22
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 12/03/2021
ms.locfileid: "63571495"
---
# <a name="api-explorer"></a>مستكشف API

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**
- [خطة Microsoft Defender لنقطة النهاية 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

إن Microsoft Defender ل "مستكشف API لنقطة النهاية" هو أداة تساعدك على استكشاف مختلف واجهات برمجة تطبيقات Defender لنقطة النهاية بشكل تفاعلي.

يسهل "مستكشف API" إنشاء استعلامات API واختبارها وإرسالها لأي نقطة نهاية متوفرة في Defender لنقطة النهاية API. استخدم "مستكشف API" لاتخاذ إجراءات أو البحث عن بيانات قد لا تكون متوفرة بعد من خلال واجهة المستخدم.

تكون الأداة مفيدة أثناء تطوير التطبيق. وهو يتيح لك تنفيذ استعلامات واجهة برمجة التطبيق التي تحترم إعدادات وصول المستخدم، مما يقلل من الحاجة إلى إنشاء رموز وصول مميزه.

يمكنك أيضا استخدام الأداة لاستكشاف معرض الاستعلامات العينة ونسخ نماذج التعليمات البرمجية لالنتيجة وإنشاء معلومات تصحيح الأخطاء.

باستخدام "مستكشف API"، يمكنك:

- تشغيل الطلبات لأي أسلوب ورؤية الاستجابات في الوقت الحقيقي
- استعرض نماذج API بسرعة وتعرف على المعلمات التي يدعمها
- إجراء مكالمات API بسهولة؛ لا حاجة إلى المصادقة بعد تسجيل الدخول إلى مدخل الإدارة

## <a name="access-api-explorer"></a>الوصول إلى مستكشف API

من قائمة التنقل اليسرى، حدد **الشركاء & واجهات برمجة التطبيقات** \> **API Explorer**.

## <a name="supported-apis"></a>واجهات برمجة التطبيقات المعتمدة

يدعم "مستكشف واجهات برمجة التطبيقات" كل واجهات برمجة التطبيقات التي يقدمها Defender لنقطة النهاية.

تتوفر قائمة واجهات برمجة التطبيقات المعتمدة في وثائق [واجهات برمجة التطبيقات](apis-intro.md).

## <a name="get-started-with-the-api-explorer"></a>بدء استخدام مستكشف API

1. في الجزء الأيسر، توجد قائمة بطلبات العينة التي يمكنك استخدامها.
2. اتبع الارتباطات وانقر فوق **تشغيل الاستعلام**.

قد تتطلب بعض العينات تحديد معلمة في عنوان URL، على سبيل المثال، {machine-ID}.

## <a name="faq"></a>الأسئلة المتداولة

**هل أحتاج إلى رمز API مميز لاستخدام "مستكشف API"؟** <br>
لا حاجة إلى بيانات الاعتماد للوصول إلى API. يستخدم "مستكشف API" الرمز المميز لمدخل إدارة Defender for Endpoint كلما طلب ذلك.

يتم استخدام بيانات اعتماد مصادقة المستخدم التي تم تسجيل دخولها للتحقق من أن "مستكشف API" معتمد للوصول إلى البيانات بالنيابة عنك.

تكون طلبات API المحددة محدودة استنادا إلى امتيازات RBAC. على سبيل المثال، يقتصر طلب "مؤشر إرسال" على دور مسؤول الأمان.
