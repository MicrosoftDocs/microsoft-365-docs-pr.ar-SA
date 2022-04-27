---
title: العمل مع نتائج استعلام التتبع المتقدمة في Microsoft 365 Defender
description: تحقيق أقصى استفادة من نتائج الاستعلام التي تم إرجاعها بواسطة التتبع المتقدم في Microsoft 365 Defender
keywords: التتبع المتقدم، وتتبع التهديدات، وتتبع التهديدات عبر الإنترنت، Microsoft 365 Defender، وmicrosoft 365، وm365، والبحث، والاستعلام، وبيانات تتبع الاستخدام، والكشف المخصص، والمخطط، وkusto، والتصور، والمخطط، وعوامل التصفية، والتنقل لأسفل
search.product: eADQiWindows 10XVcnh
search.appverid: met150
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
ms.technology: m365d
ms.openlocfilehash: cb17e2a3624471031eb4f72199705d6b8fe06979
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/27/2022
ms.locfileid: "65092856"
---
# <a name="work-with-advanced-hunting-query-results"></a>العمل مع نتائج استعلام التتبع المتقدمة

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**ينطبق على:**
- Microsoft 365 Defender
- Microsoft Defender for Endpoint

[!INCLUDE [Prerelease information](../includes/prerelease.md)]

بينما يمكنك إنشاء استعلامات [التتبع المتقدمة](advanced-hunting-overview.md) لإرجاع معلومات دقيقة، يمكنك أيضا العمل مع نتائج الاستعلام للحصول على مزيد من الرؤى والتحقيق في أنشطة ومؤشرات محددة. يمكنك اتخاذ الإجراءات التالية على نتائج الاستعلام:

- عرض النتائج كجدول أو مخطط
- تصدير الجداول والمخططات
- التنقل لأسفل للحصول على معلومات الكيان التفصيلية
- تعديل الاستعلامات مباشرة من النتائج

## <a name="view-query-results-as-a-table-or-chart"></a>عرض نتائج الاستعلام كجدول أو مخطط

بشكل افتراضي، يعرض التتبع المتقدم نتائج الاستعلام كبيانات جدولية. يمكنك أيضا عرض نفس البيانات مثل المخطط. يدعم التتبع المتقدم طرق العرض التالية:

| نوع العرض | الوصف |
|--|--|
| **الجدول** | عرض نتائج الاستعلام بتنسيق جدولي |
| **مخطط عمودي** | عرض سلسلة من العناصر الفريدة على المحور س كأشرطة عمودية تمثل ارتفاعاتها قيما رقمية من حقل آخر |
| **مخطط دائري** | عرض دائرة مقطعية تمثل عناصر فريدة. يمثل حجم كل دائري قيما رقمية من حقل آخر. |
| **مخطط خطي** | رسم قيم رقمية لسلسلة من العناصر الفريدة وتوصيل القيم المرسومة |
| **مخطط مبعثر** | رسم قيم رقمية لسلسلة من العناصر الفريدة |
| **مخطط مساحي** | رسم القيم الرقمية لسلسلة من العناصر الفريدة وتعبئة المقاطع أسفل القيم المرسومة |
| **مخطط مساحي مكدس** | رسم القيم الرقمية لسلسلة من العناصر الفريدة وتكديس المقاطع المملوءة أسفل القيم المرسومة  |
| **مخطط زمني** | رسم القيم حسب العدد على مقياس زمني خطي |

### <a name="construct-queries-for-effective-charts"></a>إنشاء استعلامات للمخططات الفعالة

عند عرض المخططات، يحدد التتبع المتقدم تلقائيا أعمدة الاهتمام والقيم الرقمية المراد تجميعها. للحصول على مخططات ذات معنى، قم بإنشاء الاستعلامات لإرجاع القيم المحددة التي تريد رؤيتها مرئية. فيما يلي بعض الاستعلامات النموذجية والمخططات الناتجة.

#### <a name="alerts-by-severity"></a>التنبيهات حسب الخطورة

`summarize` استخدم عامل التشغيل للحصول على عدد رقمي للقيم التي تريد تخطيطها. يستخدم `summarize` الاستعلام أدناه عامل التشغيل للحصول على عدد التنبيهات حسب الخطورة.

```kusto
AlertInfo
| summarize Total = count() by Severity
```

عند عرض النتائج، يعرض المخطط العمودي كل قيمة خطورة كعمود منفصل:

:::image type="content" source="../../media/advanced-hunting-column-chart-new.png" alt-text="مثال على مخطط يعرض نتائج التتبع المتقدمة في مدخل Microsoft 365 Defender" lightbox="../../media/advanced-hunting-column-chart-new.png":::
*نتائج الاستعلام عن التنبيهات حسب الخطورة المعروضة كمخطط عمودي*

#### <a name="phishing-emails-across-top-ten-sender-domains"></a>رسائل البريد الإلكتروني للتصيد الاحتيالي عبر أفضل عشرة مجالات للمرسلين

إذا كنت تتعامل مع قائمة بالقيم غير محدودة، يمكنك استخدام `Top` عامل التشغيل لتخطيط القيم التي تحتوي على معظم المثيلات فقط. على سبيل المثال، للحصول على أفضل 10 مجالات مرسل مع رسائل البريد الإلكتروني الأكثر تصيدا احتياليا، استخدم الاستعلام أدناه:

```kusto
EmailEvents
| where ThreatTypes has "Phish"
| summarize Count = count() by SenderFromDomain
| top 10 by Count
```

استخدم طريقة عرض المخطط الدائري لإظهار التوزيع بشكل فعال عبر المجالات العليا:

:::image type="content" source="../../media/advanced-hunting-pie-chart-new.png" alt-text="المخطط الدائري الذي يعرض نتائج التتبع المتقدمة في مدخل Microsoft 365 Defender" lightbox="../../media/advanced-hunting-pie-chart-new.png":::
*مخطط دائري يعرض توزيع رسائل البريد الإلكتروني للتصيد الاحتيالي عبر مجالات أفضل المرسلين*

#### <a name="file-activities-over-time"></a>أنشطة الملف بمرور الوقت
`summarize` باستخدام عامل التشغيل مع الدالة`bin()`، يمكنك التحقق من الأحداث التي تتضمن مؤشر معين بمرور الوقت. يقوم الاستعلام أدناه بحساب الأحداث التي تتضمن الملف `invoice.doc` في فواصل زمنية مدتها 30 دقيقة لإظهار الارتفاعات في النشاط المتعلق بهذا الملف:

```kusto
CloudAppEvents
| union DeviceFileEvents
| where FileName == "invoice.doc"
| summarize FileCount = count() by bin(Timestamp, 30m)
```

يوضح المخطط الخطي أدناه بوضوح الفترات الزمنية التي تتضمن `invoice.doc`المزيد من الأنشطة:

:::image type="content" source="../../media/line-chart-a.png" alt-text="المخطط الخطي الذي يعرض نتائج التتبع المتقدمة في مدخل Microsoft 365 Defender" lightbox="../../media/line-chart-a.png":::
*مخطط خطي يعرض عدد الأحداث التي تتضمن ملفا مع مرور الوقت*

## <a name="export-tables-and-charts"></a>تصدير الجداول والمخططات

بعد تشغيل استعلام، حدد **"تصدير** " لحفظ النتائج في الملف المحلي. تحدد طريقة العرض التي اخترتها كيفية تصدير النتائج:

- **طريقة عرض الجدول** — يتم تصدير نتائج الاستعلام في شكل جدولي كمصنف Microsoft Excel
- **أي مخطط** — يتم تصدير نتائج الاستعلام كصورة JPEG للمخطط المعروض

## <a name="drill-down-from-query-results"></a>التنقل لأسفل من نتائج الاستعلام

لفحص سجل بسرعة في نتائج الاستعلام، حدد الصف المقابل لفتح لوحة **فحص السجل** . توفر اللوحة المعلومات التالية استنادا إلى السجل المحدد:

- **الأصول** - عرض ملخص للأصول الرئيسية (علب البريد والأجهزة والمستخدمين) الموجودة في السجل، مع إثراء بالمعلومات المتوفرة، مثل مستويات المخاطر والتعرض
- **كافة التفاصيل** — كافة القيم من الأعمدة في السجل

:::image type="content" source="../../media/results-inspect-record.png" alt-text="السجل المحدد مع لوحة لفحص السجل في مدخل Microsoft 365 Defender" lightbox="../../media/results-inspect-record.png":::

لعرض مزيد من المعلومات حول كيان معين في نتائج الاستعلام، مثل جهاز أو ملف أو مستخدم أو عنوان IP أو URL، حدد معرف الكيان لفتح صفحة ملف تعريف مفصلة لهذا الكيان.

## <a name="tweak-your-queries-from-the-results"></a>تعديل الاستعلامات من النتائج

حدد النقاط الثلاث إلى يمين أي عمود في لوحة **"فحص السجل** ". يمكنك استخدام الخيارات من أجل:

- البحث بشكل صريح عن القيمة المحددة (`==`)
- استبعاد القيمة المحددة من الاستعلام (`!=`)
- احصل على المزيد من عوامل التشغيل المتقدمة لإضافة القيمة إلى الاستعلام، مثل `contains`، `starts with`و `ends with`

:::image type="content" source="../../media/work-with-query-tweak-query.png" alt-text="جزء &quot;نوع الإجراء&quot; على صفحة فحص السجل في مدخل Microsoft 365 Defender" lightbox="../../media/work-with-query-tweak-query.png":::

> [!NOTE]
> قد لا تتوفر بعض الجداول في هذه المقالة في Microsoft Defender لنقطة النهاية. [قم بتشغيل Microsoft 365 Defender](m365d-enable.md) للبحث عن التهديدات باستخدام المزيد من مصادر البيانات. يمكنك نقل مهام سير عمل التتبع المتقدمة من Microsoft Defender لنقطة النهاية إلى Microsoft 365 Defender باتباع الخطوات الواردة في [ترحيل استعلامات التتبع المتقدمة من Microsoft Defender لنقطة النهاية](advanced-hunting-migrate-from-mde.md).

## <a name="related-topics"></a>المواضيع ذات الصلة

- [نظرة عامة متقدمة حول الصيد](advanced-hunting-overview.md)
- [التعرّف على لغة الاستعلام](advanced-hunting-query-language.md)
- [استخدام الاستعلامات المشتركة](advanced-hunting-shared-queries.md)
- [البحث عبر الأجهزة ورسائل البريد الإلكتروني والتطبيقات والهويات](advanced-hunting-query-emails-devices.md)
- [فهم المخطط](advanced-hunting-schema-tables.md)
- [تطبيق أفضل ممارسات الاستعلام](advanced-hunting-best-practices.md)
- [نظرة عامة على الكشف المخصص](custom-detections-overview.md)
