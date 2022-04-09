---
title: نظرة عامة - التتبع المتقدم
description: تعرف على استعلامات التتبع المتقدمة في Microsoft 365 وكيفية استخدامها للعثور بشكل استباقي على التهديدات ونقاط الضعف في شبكتك
keywords: التتبع المتقدم، والتتبع من التهديدات، وتتبع التهديدات عبر الإنترنت، Microsoft 365 Defender، وmicrosoft 365، وm365، والبحث، والاستعلام، وبيانات تتبع الاستخدام، والكشف المخصص، والمخطط، وkusto
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: maccruz
author: schmurky
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
ms.topic: article
ms.custom: seo-marvel-apr2020
ms.technology: m365d
ms.openlocfilehash: 1ee8d8fbd3b1a56f83106ffaf6be937fa984c272
ms.sourcegitcommit: dd7e5b67ff4ae4e7f74490e437c1795933c74cc7
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/08/2022
ms.locfileid: "64731428"
---
# <a name="proactively-hunt-for-threats-with-advanced-hunting-in-microsoft-365-defender"></a>البحث بشكل استباقي عن التهديدات مع التتبع المتقدم في Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**ينطبق على:**
- Microsoft 365 Defender

التتبع المتقدم هو أداة تتبع المخاطر المستندة إلى الاستعلام التي تتيح لك استكشاف ما يصل إلى 30 يوما من البيانات الأولية. يمكنك فحص الأحداث في شبكتك بشكل استباقي لتحديد مؤشرات التهديد والكيانات. يتيح الوصول المرن إلى البيانات التتبع غير المقيد لكل من التهديدات المعروفة والمحتملة.
<br><br>

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4G6DO]

يمكنك استخدام نفس استعلامات تتبع التهديدات لإنشاء قواعد الكشف المخصصة. يتم تشغيل هذه القواعد تلقائيا للتحقق من نشاط الخرق المشتبه به والأجهزة المكونة بشكل خاطئ والنتائج الأخرى ثم الاستجابة لها.

تشبه هذه الإمكانية [التتبع المتقدم في Microsoft Defender لنقطة النهاية](/windows/security/threat-protection/microsoft-defender-atp/advanced-hunting-overview) وتدعم الاستعلامات التي تتحقق من مجموعة بيانات أوسع من:

- Microsoft Defender for Endpoint
- Microsoft Defender لـ Office 365
- Microsoft Defender for Cloud Apps
- Microsoft Defender for Identity

لاستخدام التتبع المتقدم، [قم بتشغيل Microsoft 365 Defender](m365d-enable.md).

لمزيد من المعلومات حول التتبع المتقدم في بيانات Microsoft Defender for Cloud Apps، راجع [الفيديو](https://www.microsoft.com/en-us/videoplayer/embed/RWFISa). 

## <a name="get-started-with-advanced-hunting"></a>بدء استخدام التتبع المتقدم

نوصي بالانتقال إلى عدة خطوات للبدء بسرعة في التتبع المتقدم.

| الهدف Learning | الوصف | الموارد |
|--|--|--|
| **تعلم اللغة** | يعتمد التتبع المتقدم على [لغة استعلام Kusto](/azure/kusto/query/)، التي تدعم نفس بناء الجملة وعوامل التشغيل. ابدأ في تعلم لغة الاستعلام عن طريق تشغيل الاستعلام الأول. | [نظرة عامة على لغة الاستعلام](advanced-hunting-query-language.md) |
| **تعرف على كيفية استخدام نتائج الاستعلام** | تعرف على المخططات والطرق المختلفة التي يمكنك من خلالها عرض النتائج أو تصديرها. استكشف كيف يمكنك تعديل الاستعلامات بسرعة، والتنقل لأسفل للحصول على معلومات أكثر ثراء، واتخاذ إجراءات الاستجابة. | - [العمل مع نتائج الاستعلام](advanced-hunting-query-results.md)<br /> - [اتخاذ إجراء بشأن نتائج الاستعلام](advanced-hunting-take-action.md) |
| **فهم المخطط** | احصل على فهم جيد وعالي المستوى للجداول في المخطط وأعمدةها. تعرف على مكان البحث عن البيانات عند إنشاء الاستعلامات. | - [مرجع المخطط](advanced-hunting-schema-tables.md) <br />- [الانتقال من Microsoft Defender لنقطة النهاية](advanced-hunting-migrate-from-mde.md) |
| **الحصول على تلميحات وأمثلة الخبراء** | التدريب مجانا باستخدام أدلة من خبراء Microsoft. استكشاف مجموعات من الاستعلامات المعرفة مسبقا التي تغطي سيناريوهات تتبع التهديدات المختلفة. | - [الحصول على تدريب الخبراء](advanced-hunting-expert-training.md) <br />- [استخدام الاستعلامات المشتركة](advanced-hunting-shared-queries.md) <br />- [الانتقال إلى التتبع](advanced-hunting-go-hunt.md) <br />- [البحث عن التهديدات عبر الأجهزة ورسائل البريد الإلكتروني والتطبيقات والهويات](advanced-hunting-query-emails-devices.md) |
| **تحسين الاستعلامات ومعالجة الأخطاء** | فهم كيفية إنشاء استعلامات فعالة وخالية من الأخطاء. | - [أفضل ممارسات الاستعلام](advanced-hunting-best-practices.md)<br />- [معالجة الأخطاء](advanced-hunting-errors.md) |
| **إنشاء قواعد الكشف المخصصة** | فهم كيفية استخدام استعلامات التتبع المتقدمة لتشغيل التنبيهات واتخاذ إجراءات الاستجابة تلقائيا. | - [نظرة عامة على عمليات الكشف المخصصة](custom-detections-overview.md) <br />- [قواعد الكشف المخصصة](custom-detection-rules.md) |

## <a name="get-access"></a>الحصول على حق الوصول
لاستخدام قدرات التتبع المتقدمة أو [قدرات Microsoft 365 Defender](microsoft-365-defender.md) الأخرى، تحتاج إلى دور مناسب في Azure Active Directory. [اقرأ عن الأدوار والأذونات المطلوبة للتتبع المتقدم](custom-roles.md).

كما يتم تحديد الوصول إلى بيانات نقطة النهاية بواسطة إعدادات التحكم في الوصول استنادا إلى الدور (RBAC) في Microsoft Defender لنقطة النهاية. [اقرأ حول إدارة الوصول إلى Microsoft 365 Defender](m365d-permissions.md).


## <a name="data-freshness-and-update-frequency"></a>حداثة البيانات وتكرار التحديث
يمكن تصنيف بيانات التتبع المتقدمة إلى نوعين متميزين، يتم دمج كل منهما بشكل مختلف.

- **بيانات الحدث أو النشاط** — تعبئة جداول حول التنبيهات وأحداث الأمان وأحداث النظام والتقييمات الروتينية. يتلقى التتبع المتقدم هذه البيانات مباشرة تقريبا بعد أن تنقلها أجهزة الاستشعار التي تجمعها بنجاح إلى الخدمات السحابية المقابلة. على سبيل المثال، يمكنك الاستعلام عن بيانات الحدث من أجهزة استشعار صحية على محطات العمل أو وحدات التحكم بالمجال مباشرة تقريبا بعد توفرها على Microsoft Defender لنقطة النهاية Microsoft Defender for Identity.
- **بيانات الكيان** — تملأ الجداول بمعلومات حول المستخدمين والأجهزة. تأتي هذه البيانات من مصادر بيانات ثابتة نسبيا ومصادر ديناميكية، مثل إدخالات Active Directory وسجلات الأحداث. لتوفير بيانات جديدة، يتم تحديث الجداول بأي معلومات جديدة كل 15 دقيقة، وإضافة صفوف قد لا يتم ملؤها بالكامل. كل 24 ساعة، يتم دمج البيانات لإدراج سجل يحتوي على أحدث مجموعة بيانات أكثر شمولا حول كل كيان.

## <a name="time-zone"></a>المنطقة الزمنية
معلومات الوقت في التتبع المتقدم في المنطقة الزمنية UTC.

## <a name="related-topics"></a>المواضيع ذات الصلة
- [التعرّف على لغة الاستعلام](advanced-hunting-query-language.md)
- [الحصول على تدريب من الخبراء](advanced-hunting-expert-training.md)
- [استخدام الاستعلامات المشتركة](advanced-hunting-shared-queries.md)
- [فهم المخطط](advanced-hunting-schema-tables.md)
- [تطبيق أفضل ممارسات الاستعلام](advanced-hunting-best-practices.md)
- [نظرة عامة على الكشف المخصص](custom-detections-overview.md)
