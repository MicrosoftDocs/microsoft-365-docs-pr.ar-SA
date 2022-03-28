---
title: استخدام نتائج استعلام البحث المتقدمة في Microsoft 365 Defender
description: تحقيق الاستفادة من نتائج الاستعلام التي يرجعها البحث المتقدم في Microsoft 365 Defender
keywords: الصيد المتقدم، وصيد التهديدات، والصيد عبر الإنترنت، و Microsoft 365 Defender، و microsoft 365، و m365، و البحث، و الاستعلام، و بيانات التعقب، و عمليات الكشف المخصصة، و المخطط، و kusto، و المرئيات، و المخطط، و عوامل التصفية، و التنقل لأسفل
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
ms.openlocfilehash: 41427760a0a02f0dafbb9685da457a473698207c
ms.sourcegitcommit: d32654bdfaf08de45715dd362a7d42199bdc1ee7
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/23/2022
ms.locfileid: "63754990"
---
# <a name="work-with-advanced-hunting-query-results"></a>استخدام نتائج استعلام البحث المتقدمة

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**ينطبق على:**
- Microsoft 365 Defender
- Microsoft Defender لنقطة النهاية

[!INCLUDE [Prerelease information](../includes/prerelease.md)]

على الرغم من أنه يمكنك [](advanced-hunting-overview.md) إنشاء استعلامات بحث متقدمة لإرجاع معلومات دقيقة، يمكنك أيضا استخدام نتائج الاستعلام للحصول على مزيد من المعرفة الدقيقة وتحري أنشطة ومؤشرات معينة. يمكنك اتخاذ الإجراءات التالية على نتائج الاستعلام:

- عرض النتائج ك جدول أو مخطط
- تصدير الجداول والمخططات
- التنقل لأسفل وصولا إلى معلومات الكيان التفصيلية
- تعديل الاستعلامات مباشرة من النتائج أو تطبيق عوامل التصفية

## <a name="view-query-results-as-a-table-or-chart"></a>عرض نتائج الاستعلام ك جدول أو مخطط
بشكل افتراضي، يعرض البحث المتقدم نتائج الاستعلام كالبيانات الجدولية. يمكنك أيضا عرض نفس البيانات كمخطط. يدعم الصيد المتقدم طرق العرض التالية:

| نوع العرض | الوصف |
|--|--|
| **جدول** | عرض نتائج الاستعلام بتنسيق جدولي |
| **مخطط عمودي** | عرض سلسلة من العناصر الفريدة على المحور س كأشرطة عمودية تمثل ارتفاعاتها قيما رقمية من حقل آخر |
| **مخطط عمودي مكدس** | عرض سلسلة من العناصر الفريدة على المحور س كأشرطة عمودية مكدسة تمثل ارتفاعاتها قيما رقمية من حقل واحد أو أكثر من الحقول الأخرى |
| **مخطط دائري** | يعرض المخططات المقطعية التي تمثل عناصر فريدة. يمثل حجم كل دائري قيما رقمية من حقل آخر. |
| **مخطط دونات** | يعرض الأقواس المقطعية التي تمثل عناصر فريدة. يمثل طول كل قوس قيما رقمية من حقل آخر. |
| **مخطط خطي** | رسم قيم رقمية لسلسلة من العناصر الفريدة وربط القيم المرسمة |
| **مخطط مبعثر** | رسم قيم رقمية لسلسلة من العناصر الفريدة |
| **مخطط منطقة** | رسم قيم رقمية لسلسلة من العناصر الفريدة وملء المقاطع أسفل القيم المخططة |

### <a name="construct-queries-for-effective-charts"></a>إنشاء استعلامات للمخططات الفعالة
عند عرض المخططات، يحدد الصيد المتقدم تلقائيا الأعمدة التي تهمك والقيم رقمية لتجميعها. للحصول على مخططات ذات معنى، يمكنك إنشاء الاستعلامات لإرجاع القيم المحددة التي تريد مؤثرات عرضها. فيما يلي بعض الاستعلامات العينة والمخططات الناتجة.

#### <a name="alerts-by-severity"></a>التنبيهات حسب الخطورة
استخدم عامل `summarize` التشغيل للحصول على عدد عدد القيم التي تريد رسم مخطط لها. يستخدم الاستعلام أدناه عامل `summarize` التشغيل للحصول على عدد التنبيهات حسب الخطورة.

```kusto
AlertInfo
| summarize Total = count() by Severity
```
عند عرض النتائج، يعرض المخطط العمودي كل قيمة خطورة كعمود منفصل:

:::image type="content" source="../../media/advanced-hunting-column-chart-new.png" alt-text="مثال لمخطط يعرض نتائج صيد متقدمة في مدخل Microsoft 365 Defender" lightbox="../../media/advanced-hunting-column-chart-new.png":::
*نتائج الاستعلام للتنبيهات حسب الخطورة المعروضة كمخطط عمودي*


#### <a name="phishing-emails-across-top-ten-sender-domains"></a>رسائل البريد الإلكتروني التصيد الاحتيالي عبر أهم عشرة مجالات للمرسلين
إذا كنت تتعامل مع `Top` قائمة قيم غير محدودة، يمكنك استخدام عامل التشغيل لرسم مخطط للقيم فقط باستخدام معظم المثيلات. على سبيل المثال، للحصول على أهم 10 مجالات مرسلين مع رسائل البريد الإلكتروني الأكثر تصيدا احتيالا، استخدم الاستعلام أدناه:

```kusto
EmailEvents
| where ThreatTypes has "Phish" 
| summarize Count = count() by SenderFromDomain 
| top 10 by Count
```
استخدم طريقة عرض المخطط الدائري لإظهار التوزيع عبر المجالات العليا بفعالية:

:::image type="content" source="../../media/advanced-hunting-pie-chart-new.png" alt-text="المخطط الدائري الذي يعرض نتائج الصيد المتقدمة في مدخل Microsoft 365 Defender" lightbox="../../media/advanced-hunting-pie-chart-new.png":::
*مخطط دائري يعرض توزيع رسائل البريد الإلكتروني التصيد الاحتيالي عبر أهم مجالات المرسلين*

#### <a name="file-activities-over-time"></a>أنشطة الملفات مع مرور الوقت
باستخدام عامل `summarize` التشغيل مع الدالة `bin()` ، يمكنك التحقق من الأحداث التي تتضمن مؤشرا معينا مع مرور الوقت. يحسب الاستعلام أدناه `invoice.doc` الأحداث التي تتضمن الملف في فواصل زمنية 30 دقيقة لإظهار ارتفاعات النشاط المرتبطة بهذا الملف:

```kusto
CloudAppEvents
| union DeviceFileEvents
| where FileName == "invoice.doc"
| summarize FileCount = count() by bin(Timestamp, 30m)
```
يسلط المخطط الخطي أدناه الضوء بوضوح على الفترات الزمنية مع المزيد من الأنشطة التي تتضمن `invoice.doc`: 

:::image type="content" source="../../media/line-chart-a.png" alt-text="المخطط الخطي الذي يعرض نتائج الصيد المتقدمة في مدخل Microsoft 365 Defender" lightbox="../../media/line-chart-a.png":::
*مخطط خطي يعرض عدد الأحداث التي تتضمن ملفا مع مرور الوقت*


## <a name="export-tables-and-charts"></a>تصدير الجداول والمخططات
بعد تشغيل استعلام، حدد **تصدير** لحفظ النتائج إلى ملف محلي. تحدد طريقة العرض التي اخترتها كيفية تصدير النتائج:

- **طريقة عرض** الجدول—يتم تصدير نتائج الاستعلام في نموذج جدولي كم مصنف Microsoft Excel جدولي
- **أي مخطط**— يتم تصدير نتائج الاستعلام كصورة JPEG للمخطط الذي تم عرضه

## <a name="drill-down-from-query-results"></a>التنقل لأسفل من نتائج الاستعلام
لفحص سجل بسرعة في نتائج الاستعلام، حدد الصف المقابل لفتح لوحة **السجلات فحص** . توفر اللوحة المعلومات التالية استنادا إلى السجل المحدد:

- **الأصول** — طريقة عرض ملخصة للأصول الرئيسية (علب البريد والأجهزة والمستخدمين) الموجودة في السجل، تم إثراءها بالمعلومات المتوفرة، مثل مستويات المخاطر والتعرض للضوء
- **كل التفاصيل**—كل القيم من الأعمدة في السجل  

:::image type="content" source="../../media/results-inspect-record.png" alt-text="السجل المحدد مع لوحة لفحص السجل في مدخل Microsoft 365 Defender" lightbox="../../media/results-inspect-record.png":::

لعرض مزيد من المعلومات حول كيان معين في نتائج الاستعلام، مثل جهاز أو ملف أو مستخدم أو عنوان IP أو URL، حدد معرف الكيان لفتح صفحة ملف تعريف مفصلة لهذا الكيان.

## <a name="tweak-your-queries-from-the-results"></a>تعديل الاستعلامات من النتائج
حدد النقاط الثلاث إلى يمين أي عمود في لوحة **السجل فحص** . يمكنك استخدام الخيارات التالية:

- البحث بشكل صريح عن القيمة المحددة (`==`)
- استبعاد القيمة المحددة من الاستعلام (`!=`)
- احصل على عوامل تشغيل أكثر تقدما لإضافة القيمة إلى الاستعلام، مثل `contains`و `starts with`و `ends with` 

:::image type="content" source="../../media/work-with-query-tweak-query.png" alt-text="الجزء &quot;نوع الإجراء&quot; على الصفحة &quot;فحص السجل&quot; في مدخل Microsoft 365 Defender" lightbox="../../media/work-with-query-tweak-query.png":::



>[!NOTE]
>قد لا تتوفر بعض الجداول في هذه المقالة في Microsoft Defender ل Endpoint. [قم Microsoft 365 Defender](m365d-enable.md) للبحث عن التهديدات باستخدام المزيد من مصادر البيانات. يمكنك نقل مهام سير عمل الصيد المتقدمة من Microsoft Defender ل Endpoint إلى Microsoft 365 Defender باتباع الخطوات الواردة في ترحيل استعلامات الصيد المتقدمة من [Microsoft Defender ل Endpoint](advanced-hunting-migrate-from-mde.md).

## <a name="related-topics"></a>المواضيع ذات الصلة
- [نظرة عامة متقدمة حول الصيد](advanced-hunting-overview.md)
- [تعرف على لغة الاستعلام](advanced-hunting-query-language.md)
- [استخدام الاستعلامات المشتركة](advanced-hunting-shared-queries.md)
- [البحث عبر الأجهزة ورسائل البريد الإلكتروني والتطبيقات والهويات](advanced-hunting-query-emails-devices.md)
- [فهم المخطط](advanced-hunting-schema-tables.md)
- [تطبيق أفضل ممارسات الاستعلام](advanced-hunting-best-practices.md)
- [نظرة عامة على الكشف المخصص](custom-detections-overview.md)
