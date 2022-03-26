---
title: نظرة عامة حول الصيد المتقدم في Microsoft Defender لنقطة النهاية
description: استخدام قدرات البحث عن المخاطر في Microsoft Defender لنقطة النهاية لإنشاء استعلامات تعثر على التهديدات ونقاط الضعف في شبكتك
keywords: الصيد المتقدم، وصيد التهديدات، وصيد التهديدات الإلكترونية، و mdatp، و microsoft defender atp، و microsoft defender لنقطة النهاية، و wdatp، و البحث، و الاستعلام، و بيانات التعقب، و عمليات الكشف المخصصة، و المخطط، و kusto، المنطقة الزمنية، UTC
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: maccruz
author: schmurky
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 2e1b6a5bb77dc757861a5d7f56d8a4380c6fc6c1
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 11/24/2021
ms.locfileid: "63573835"
---
# <a name="proactively-hunt-for-threats-with-advanced-hunting"></a>البحث الاستباقي عن التهديدات باستخدام الصيد المتقدم

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**
- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/?linkid=2154037)

> هل تريد تجربة Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-advancedhunting-abovefoldlink)

الصيد المتقدم هو أداة بحث عن تهديدات تستند إلى استعلام تتيح لك استكشاف ما يصل إلى 30 يوما من البيانات الخام. يمكنك فحص الأحداث في شبكتك بشكل استباقي لتحديد موقع مؤشرات التهديدات والكيانات. يتيح الوصول المرن إلى البيانات البحث بدون قيود عن التهديدات المعروفة والمحتملة.

شاهد هذا الفيديو للحصول على نظرة عامة سريعة حول الصيد المتقدم والبرامج التعليمية القصيرة التي سوف تحصل على البدء بسرعة.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4bGqo]

يمكنك استخدام استعلامات البحث عن المخاطر نفسها لإنشاء قواعد الكشف المخصصة. يتم تشغيل هذه القواعد تلقائيا للتحقق من نشاط الانتهاك المشتبه به والآلات التي تم تكوينها بشكل خاطئ والنتائج الأخرى ثم الاستجابة لها.

> [!TIP]
> استخدم [الصيد](/microsoft-365/security/defender/advanced-hunting-overview) المتقدم في Microsoft 365 Defender للبحث عن التهديدات باستخدام البيانات من Defender for Endpoint و Microsoft Defender for Office 365 و Microsoft Defender for Cloud Apps و Microsoft Defender for Identity. [قم Microsoft 365 Defender](/microsoft-365/security/defender/m365d-enable).

تعرف على المزيد حول كيفية نقل مهام سير عمل الصيد المتقدمة من Microsoft Defender ل Endpoint إلى Microsoft 365 Defender في ترحيل استعلامات الصيد المتقدمة من [Microsoft Defender ل Endpoint](/microsoft-365/security/defender/advanced-hunting-migrate-from-mde).

## <a name="get-started-with-advanced-hunting"></a>بدء استخدام الصيد المتقدم

انتقل إلى الخطوات التالية لزيادة معارفك المتقدمة في مجال الصيد.

نوصيك بالتخلص من عدة خطوات للانتهاء بسرعة وتشغيله باستخدام الصيد المتقدم.

<br>

****

|Learning الهدف|الوصف|المورد|
|---|---|---|
|**تعرف على اللغة**|يستند الصيد المتقدم إلى [لغة استعلام Kusto](/azure/kusto/query/)، التي تدعم بناء الجملة نفسه و عوامل التشغيل نفسها. ابدأ تعلم لغة الاستعلام عن طريق تشغيل الاستعلام الأول.|[نظرة عامة حول لغة الاستعلام](advanced-hunting-query-language.md)|
|**تعرف على كيفية استخدام نتائج الاستعلام**|تعرف على المخططات وطرق مختلفة يمكنك من خلالها عرض النتائج أو تصديرها. استكشف كيفية تعديل الاستعلامات بسرعة والتحرك لأسفل للحصول على معلومات أكثر ثرية.|[استخدام نتائج الاستعلام](advanced-hunting-query-results.md)|
|**فهم المخطط**|احصل على فهم جيد و عال المستوى للجداول في المخطط والأعمدة الخاصة بها. تعرف على مكان البحث عن البيانات عند إنشاء الاستعلامات.|[مرجع المخطط](advanced-hunting-schema-reference.md)|
|**استخدام استعلامات محددة مسبقا**|استكشف مجموعات من الاستعلامات المحددة مسبقا التي تغطي سيناريوهات مختلفة لصيد التهديدات.|[الاستعلامات المشتركة](advanced-hunting-shared-queries.md)|
|**تحسين الاستعلامات والتعامل مع الأخطاء**|تعرف على كيفية إنشاء استعلامات فعالة خالية من الأخطاء.|[أفضل ممارسات الاستعلام](advanced-hunting-best-practices.md) <p> [معالجة الأخطاء](advanced-hunting-errors.md)|
|**الحصول على تغطية كاملة**|استخدم إعدادات التدقيق لتوفير تغطية أفضل للبيانات لمنظمتك.|[توسيع تغطية الصيد المتقدمة](advanced-hunting-extend-data.md)|
|**تشغيل تحقيق سريع**|يمكنك تشغيل استعلام بحث متقدم بسرعة للتحقق من النشاط المريب.|[البحث بسرعة عن معلومات الكيان أو الحدث باستخدام *البحث السريع*](advanced-hunting-go-hunt.md)|
|**تحتوي على تهديدات وتنازلات في العنوان**|الاستجابة للهجمات من خلال تقييد الملفات وتقييد تنفيذ التطبيق والإجراءات الأخرى|[اتخاذ إجراء بشأن نتائج استعلام البحث المتقدمة](advanced-hunting-take-action.md)|
|**إنشاء قواعد الكشف المخصصة**|تعرف على كيفية استخدام استعلامات البحث المتقدمة في تشغيل التنبيهات واتخاذ إجراءات الاستجابة تلقائيا.|[نظرة عامة على الكشف المخصص](overview-custom-detections.md) <p> [قواعد الكشف المخصصة](custom-detection-rules.md)|
|

## <a name="data-freshness-and-update-frequency"></a>تكرار تحديث البيانات وتحديثها

يمكن تصنيف بيانات الصيد المتقدمة إلى نوعين مميزين، يتم دمج كل منهما بشكل مختلف.

- **بيانات النشاط أو الحدث**: ملء الجداول حول التنبيهات، والأحداث المتعلقة الأمان، والأحداث في النظام، والتقييمات الروتينية. يتلقى الصيد المتقدم هذه البيانات مباشرة تقريبا بعد أن تقوم أدوات الاستشعار التي تجمعها بإرسالها بنجاح إلى Defender for Endpoint.
- **بيانات الكيان**: ت ملء الجداول بمعلومات مدمجة حول المستخدمين والأجهزة. تأتي هذه البيانات من مصادر بيانات ثابتة نسبيا ومصادر ديناميكية، مثل إدخالات Active Directory وسجلات الأحداث. لتوفير بيانات جديدة، يتم تحديث الجداول بأي معلومات جديدة كل 15 دقيقة، مما يضيف صفوفا قد لا تتم ملؤها بالكامل. يتم دمج البيانات كل 24 ساعة لإدراج سجل يحتوي على أحدث مجموعة بيانات وأكثرها شمولية حول كل كيان.

## <a name="time-zone"></a>المنطقة الزمنية

توجد معلومات الوقت في الصيد المتقدم حاليا في المنطقة الزمنية UTC.

## <a name="related-topics"></a>المواضيع ذات الصلة

- [تعرف على لغة الاستعلام](advanced-hunting-query-language.md)
- [استخدام نتائج الاستعلام](advanced-hunting-query-results.md)
- [استخدام الاستعلامات المشتركة](advanced-hunting-shared-queries.md)
- [فهم المخطط](advanced-hunting-schema-reference.md)
- [تطبيق أفضل ممارسات الاستعلام](advanced-hunting-best-practices.md)
- [نظرة عامة على الكشف المخصص](overview-custom-detections.md)
- [نظرة عامة حول حساب التخزين](/azure/storage/common/storage-account-overview)
- [Azure Event Hubs — نظام أساسي كبير لتدفق البيانات وخدمة استخدام الأحداث](/azure/event-hubs/event-hubs-about)
