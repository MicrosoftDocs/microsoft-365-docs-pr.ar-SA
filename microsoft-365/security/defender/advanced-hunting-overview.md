---
title: نظرة عامة - البحث المتقدم
description: تعرف على استعلامات البحث المتقدمة في Microsoft 365 وكيفية استخدامها للعثور بشكل استباقي على التهديدات ونقاط الضعف في شبكتك
keywords: الصيد المتقدم، وصيد التهديدات، والصيد عبر الإنترنت، Microsoft 365 Defender، microsoft 365، m365، البحث، الاستعلام، بيانات التعقب، عمليات الكشف المخصصة، المخطط، kusto
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
ms.openlocfilehash: 03f99f6b883a46e0a7c87d6cbdb2abb8f5552a31
ms.sourcegitcommit: 400ef9ac34247978e3de7ecc0b376c4abb6c99d8
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 01/27/2022
ms.locfileid: "63570519"
---
# <a name="proactively-hunt-for-threats-with-advanced-hunting-in-microsoft-365-defender"></a>البحث الاستباقي عن التهديدات باستخدام الصيد المتقدم في Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**ينطبق على:**
- Microsoft 365 Defender

> هل تريد تجربة Microsoft 365 Defender؟ يمكنك [تقييمه في بيئة معملية](m365d-evaluation.md?ocid=cx-docs-MTPtriallab) أو [تشغيل مشروعك التجريبي في الإنتاج](m365d-pilot.md?ocid=cx-evalpilot).
>

الصيد المتقدم هو أداة بحث عن تهديدات تستند إلى استعلام تتيح لك استكشاف ما يصل إلى 30 يوما من البيانات الخام. يمكنك فحص الأحداث في شبكتك بشكل استباقي لتحديد موقع مؤشرات التهديدات والكيانات. يتيح الوصول المرن إلى البيانات البحث بدون قيود عن التهديدات المعروفة والمحتملة.
<br><br>

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4G6DO]

يمكنك استخدام استعلامات البحث عن التهديدات نفسها لإنشاء قواعد الكشف المخصصة. يتم تشغيل هذه القواعد تلقائيا للتحقق من نشاط الانتهاك المشتبه به والآلات التي تم تكوينها بشكل خاطئ والنتائج الأخرى ثم الاستجابة لها.

هذه الإمكانية مماثلة للصيد المتقدم في [Microsoft Defender ل Endpoint](/windows/security/threat-protection/microsoft-defender-atp/advanced-hunting-overview) وهي تدعم الاستعلامات التي تحقق من مجموعة بيانات أوسع من:

- Microsoft Defender لنقطة النهاية
- Microsoft Defender Office 365
- Microsoft Defender لتطبيقات السحابة
- Microsoft Defender for Identity

لاستخدام الصيد المتقدم، [قم Microsoft 365 Defender](m365d-enable.md).

لمزيد من المعلومات حول البحث المتقدم في بيانات Microsoft Defender for Cloud Apps، راجع [الفيديو](https://www.microsoft.com/en-us/videoplayer/embed/RWFISa). 

## <a name="get-started-with-advanced-hunting"></a>بدء استخدام الصيد المتقدم

نوصيك بإجراء عدة خطوات للبدء بسرعة في عملية البحث المتقدم.

| Learning الهدف | الوصف | المورد |
|--|--|--|
| **تعرف على اللغة** | يستند الصيد المتقدم إلى [لغة استعلام Kusto](/azure/kusto/query/)، التي تدعم بناء الجملة نفسه و عوامل التشغيل نفسها. ابدأ تعلم لغة الاستعلام عن طريق تشغيل الاستعلام الأول. | [نظرة عامة حول لغة الاستعلام](advanced-hunting-query-language.md) |
| **تعرف على كيفية استخدام نتائج الاستعلام** | تعرف على المخططات وطرق مختلفة يمكنك من خلالها عرض النتائج أو تصديرها. استكشف كيف يمكنك تعديل الاستعلامات بسرعة، والتحرك لأسفل للحصول على معلومات أكثر ثرية، واتخاذ إجراءات الاستجابة. | - [استخدام نتائج الاستعلام](advanced-hunting-query-results.md)<br /> - [اتخاذ إجراء بشأن نتائج الاستعلام](advanced-hunting-take-action.md) |
| **فهم المخطط** | احصل على فهم جيد و عال المستوى للجداول في المخطط والأعمدة الخاصة بها. تعرف على مكان البحث عن البيانات عند إنشاء الاستعلامات. | - [مرجع المخطط](advanced-hunting-schema-tables.md) <br />- [الانتقال من Microsoft Defender لنقطة النهاية](advanced-hunting-migrate-from-mde.md) |
| **الحصول على تلميحات الخبراء وأمثلة** | تدريب مجانا باستخدام أدلة من خبراء Microsoft. استكشف مجموعات من الاستعلامات المحددة مسبقا التي تغطي سيناريوهات مختلفة لصيد التهديدات. | - [الحصول على تدريب من الخبراء](advanced-hunting-expert-training.md) <br />- [استخدام الاستعلامات المشتركة](advanced-hunting-shared-queries.md) <br />- [الانتقال إلى البحث](advanced-hunting-go-hunt.md) <br />- [البحث عن التهديدات عبر الأجهزة ورسائل البريد الإلكتروني والتطبيقات والهويات](advanced-hunting-query-emails-devices.md) |
| **تحسين الاستعلامات والتعامل مع الأخطاء** | تعرف على كيفية إنشاء استعلامات فعالة خالية من الأخطاء. | - [أفضل ممارسات الاستعلام](advanced-hunting-best-practices.md)<br />- [معالجة الأخطاء](advanced-hunting-errors.md) |
| **إنشاء قواعد الكشف المخصصة** | تعرف على كيفية استخدام استعلامات البحث المتقدمة في تشغيل التنبيهات واتخاذ إجراءات الاستجابة تلقائيا. | - [نظرة عامة على الكشف المخصص](custom-detections-overview.md) <br />- [قواعد الكشف المخصصة](custom-detection-rules.md) |

## <a name="get-access"></a>الحصول على حق الوصول
لاستخدام قدرات متقدمة للصيد أو Microsoft 365 Defender [](microsoft-365-defender.md) أخرى، تحتاج إلى دور مناسب في Azure Active Directory. [اقرأ حول الأدوار والأذونات المطلوبة للصيد المتقدم](custom-roles.md).

بالإضافة إلى ذلك، يتم تحديد الوصول إلى بيانات نقطة النهاية من خلال إعدادات التحكم بالوصول المستند إلى الدور (RBAC) في Microsoft Defender لنقطة النهاية. [اقرأ حول إدارة الوصول إلى Microsoft 365 Defender](m365d-permissions.md).


## <a name="data-freshness-and-update-frequency"></a>تكرار تحديث البيانات وتحديثها
يمكن تصنيف بيانات الصيد المتقدمة إلى نوعين مميزين، يتم دمج كل منهما بشكل مختلف.

- **بيانات الحدث أو** النشاط— ت ملء الجداول حول التنبيهات، والأحداث المتعلقة الأمان، والأحداث في النظام، والتقييمات الروتينية. يتلقى الصيد المتقدم هذه البيانات مباشرة تقريبا بعد أن تقوم أدوات الاستشعار التي تجمعها بإرسالها بنجاح إلى الخدمات السحابية المقابلة. على سبيل المثال، يمكنك الاستعلام عن بيانات الحدث من أدوات الاستشعار الصحية على محطات العمل أو وحدات التحكم بالمجال مباشرة تقريبا بعد توفرها على Microsoft Defender ل Endpoint و Microsoft Defender for Identity.
- **بيانات الكيان** — ت ملء الجداول بمعلومات حول المستخدمين والأجهزة. تأتي هذه البيانات من مصادر بيانات ثابتة نسبيا ومصادر ديناميكية، مثل إدخالات Active Directory وسجلات الأحداث. لتوفير بيانات جديدة، يتم تحديث الجداول بأي معلومات جديدة كل 15 دقيقة، مما يضيف صفوفا قد لا تتم ملؤها بالكامل. يتم دمج البيانات كل 24 ساعة لإدراج سجل يحتوي على أحدث مجموعة بيانات وأكثرها شمولية حول كل كيان.

## <a name="time-zone"></a>المنطقة الزمنية
معلومات الوقت في عملية البحث المتقدم هي في المنطقة الزمنية UTC.

## <a name="related-topics"></a>المواضيع ذات الصلة
- [تعرف على لغة الاستعلام](advanced-hunting-query-language.md)
- [الحصول على تدريب من الخبراء](advanced-hunting-expert-training.md)
- [استخدام الاستعلامات المشتركة](advanced-hunting-shared-queries.md)
- [فهم المخطط](advanced-hunting-schema-tables.md)
- [تطبيق أفضل ممارسات الاستعلام](advanced-hunting-best-practices.md)
- [نظرة عامة على الكشف المخصص](custom-detections-overview.md)
