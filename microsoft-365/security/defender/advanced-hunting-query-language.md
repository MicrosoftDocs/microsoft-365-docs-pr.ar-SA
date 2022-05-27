---
title: تعرف على لغة استعلام التتبع المتقدمة في Microsoft 365 Defender
description: إنشاء استعلام التتبع للمخاطر الأول والتعرف على عوامل التشغيل الشائعة والجوانب الأخرى للغة استعلام التتبع المتقدمة
keywords: التتبع المتقدم، وتتبع التهديدات، وتتبع التهديدات عبر الإنترنت، Microsoft 365 Defender، وmicrosoft 365، وm365، والبحث، والاستعلام، واللغة، والتعلم، والاستعلام الأول، وبيانات تتبع الاستخدام، والأحداث، وبيانات تتبع الاستخدام، والكشف المخصص، والمخطط، وkusto، وعوامل التشغيل، وأنواع البيانات، وتنزيل powershell، مثال الاستعلام
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
ms.openlocfilehash: 724e6c0b0e0a9854df6c87977cacbf1e1a69bfbe
ms.sourcegitcommit: a8fbaf4b441b5325004f7a2dacd9429ec9d80534
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 05/26/2022
ms.locfileid: "65739989"
---
# <a name="learn-the-advanced-hunting-query-language"></a>تعلم لغة استعلام التتبع المتقدمة

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**ينطبق على:**

- Microsoft 365 Defender
- Microsoft Defender for Endpoint

يعتمد التتبع المتقدم على [لغة استعلام Kusto](/azure/kusto/query/). يمكنك استخدام عوامل تشغيل وعبارات Kusto لإنشاء استعلامات تحدد موقع المعلومات في [مخطط](advanced-hunting-schema-tables.md) متخصص. 

شاهد هذا الفيديو القصير لمعرفة بعض أساسيات لغة استعلام Kusto.

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RWRwfJ]
 
لفهم هذه المفاهيم بشكل أفضل، قم بتشغيل الاستعلام الأول.

## <a name="try-your-first-query"></a>جرب استعلامك الأول

في مدخل Microsoft 365 Defender، انتقل إلى **التتبع** لتشغيل الاستعلام الأول. استخدم المثال التالي: 

```kusto
// Finds PowerShell execution events that could involve a download
union DeviceProcessEvents, DeviceNetworkEvents
| where Timestamp > ago(7d)
// Pivoting on PowerShell processes
| where FileName in~ ("powershell.exe", "powershell_ise.exe")
// Suspicious commands
| where ProcessCommandLine has_any("WebClient",
 "DownloadFile",
 "DownloadData",
 "DownloadString",
"WebRequest",
"Shellcode",
"http",
"https")
| project Timestamp, DeviceName, InitiatingProcessFileName, InitiatingProcessCommandLine, 
FileName, ProcessCommandLine, RemoteIP, RemoteUrl, RemotePort, RemoteIPType
| top 100 by Timestamp
```

**[تشغيل هذا الاستعلام في التتبع المتقدم](https://security.microsoft.com/hunting?query=H4sIAAAAAAAEAI2TW0sCURSF93PQfxh8Moisp956yYIgQtLoMaYczJpbzkkTpN_et_dcdPQkcpjbmrXXWftyetKTQG5lKqmMpeB9IJksJJKZDOWdZ8wKeP5wvcm3OLgZbMXmXCmIxjnYIfcAVgYvRi8w3TnfsXEDGAG47pCCZXyP5ViO4KeNbt-Up-hEuJmB6lvButnY8XSL-cDl0M2I-GwxVX8Fe2H5zMzHiKjEVB0eEsnBrszfBIWuXOLrxCJ7VqEBfM3DWUYTkNKrv1p5y3X0jwetemzOQ_NSVuuXZ1c6aNTKRaN8VvWhY9n7OS-o6J5r7mYeQypdEKc1m1qfiqpjCSuspsDntt2J61bEvTlXls5AgQfFl5bHM_gr_BhO2RF1rztoBv2tWahrso_TtzkL93KGMGZVr2pe7eWR-xeZl91f_113UOsx3nDR4Y9j5R6kaCq8ajr_YWfFeedsd27L7it-Z6dAZyxsJq1d9-2ZOSzK3y2NVd8-zUPjtZaJnYsIH4Md7AmdeAcd2Cl1XoURc5PzXlfU8U9P54WcswL6t_TW9Q__qX-xygQAAA&runQuery=true&timeRangeId=week)**

### <a name="describe-the-query-and-specify-the-tables-to-search"></a>وصف الاستعلام وتحديد الجداول التي تريد البحث فيها

تمت إضافة تعليق قصير إلى بداية الاستعلام لوصف ما هو مخصص له. يساعد هذا التعليق إذا قررت لاحقا حفظ الاستعلام ومشاركته مع الآخرين في مؤسستك. 

```kusto
// Finds PowerShell execution events that could involve a download
```

عادة ما يبدأ الاستعلام نفسه باسم جدول متبوعا بعدة عناصر تبدأ بمسار (`|`). في هذا المثال، نبدأ بإنشاء اتحاد من جدولين، و`DeviceNetworkEvents`، `DeviceProcessEvents` وإضافة عناصر piped حسب الحاجة.

```kusto
union DeviceProcessEvents, DeviceNetworkEvents
```

### <a name="set-the-time-range"></a>تعيين النطاق الزمني

العنصر الأول الذي يتم تحريكه هو عامل تصفية الوقت الذي تم تحديد نطاقه إلى الأيام السبعة السابقة. يساعد تحديد النطاق الزمني على ضمان أداء الاستعلامات بشكل جيد، وإرجاع نتائج يمكن إدارتها، ولا مهلة.

```kusto
| where Timestamp > ago(7d)
```

### <a name="check-specific-processes"></a>التحقق من عمليات معينة

يتبع النطاق الزمني على الفور عملية بحث عن أسماء ملفات المعالجة التي تمثل تطبيق PowerShell.

```kusto
// Pivoting on PowerShell processes
| where FileName in~ ("powershell.exe", "powershell_ise.exe")
```

### <a name="search-for-specific-command-strings"></a>البحث عن سلاسل أوامر معينة

بعد ذلك، يبحث الاستعلام عن سلاسل في سطور الأوامر التي تستخدم عادة لتنزيل الملفات باستخدام PowerShell.

```kusto
// Suspicious commands
| where ProcessCommandLine has_any("WebClient",
    "DownloadFile",
    "DownloadData",
    "DownloadString",
    "WebRequest",
    "Shellcode",
    "http",
    "https")
```

### <a name="customize-result-columns-and-length"></a>تخصيص أعمدة النتائج وطولها 

الآن بعد أن حدد الاستعلام البيانات التي تريد تحديد موقعها بوضوح، يمكنك تحديد شكل النتائج. `project` إرجاع أعمدة معينة، والحد `top` من عدد النتائج. تساعد عوامل التشغيل هذه في ضمان أن النتائج منسقة بشكل جيد وكبيرة إلى حد معقول وسهلة المعالجة.

```kusto
| project Timestamp, DeviceName, InitiatingProcessFileName, InitiatingProcessCommandLine, 
FileName, ProcessCommandLine, RemoteIP, RemoteUrl, RemotePort, RemoteIPType
| top 100 by Timestamp
```

حدد **"تشغيل الاستعلام** " لمشاهدة النتائج.

>[!TIP]
>يمكنك عرض نتائج الاستعلام كمخططات وضبط عوامل التصفية بسرعة. للحصول على إرشادات، [اقرأ حول استخدام نتائج الاستعلام](advanced-hunting-query-results.md)

شاهد هذا [الفيديو القصير](https://www.youtube.com/watch?v=8qZx7Pp5XgM) للتعرف على كيفية استخدام لغة استعلام Kusto للانضمام إلى الجداول.

## <a name="learn-common-query-operators"></a>تعرف على عوامل تشغيل الاستعلام الشائعة

لقد قمت بتشغيل استعلامك الأول ولديك فكرة عامة عن مكوناته. حان الوقت للتراجع قليلا وتعلم بعض الأساسيات. تدعم لغة استعلام Kusto المستخدمة من قبل التتبع المتقدم مجموعة من عوامل التشغيل، بما في ذلك العوامل الشائعة التالية.

| المشغل | الوصف والاستخدام |
|--|--|
| `where` | تصفية جدول إلى مجموعة فرعية من الصفوف التي تلبي دالة تقييم. |
| `summarize` | إنشاء جدول يجمع محتوى جدول الإدخال. |
| `join` | دمج صفوف جدولين لتشكيل جدول جديد عن طريق مطابقة قيم العمود (الأعمدة) المحددة من كل جدول. |
| `count` | إرجاع عدد السجلات في مجموعة سجلات الإدخال. |
| `top` | إرجاع السجلات N الأولى التي تم فرزها حسب الأعمدة المحددة. |
| `limit` | العودة إلى العدد المحدد من الصفوف. |
| `project` | حدد الأعمدة لتضمينها وإعادة تسميتها أو إسقاطها وإدراج أعمدة محسوبة جديدة. |
| `extend` | إنشاء أعمدة محسوبة وإلحاقها بمجموعة النتائج. |
| `makeset` |  إرجاع صفيف ديناميكي (JSON) من مجموعة القيم المميزة التي يأخذها Expr في المجموعة. |
| `find` | ابحث عن صفوف تتطابق مع دالة تقييم عبر مجموعة من الجداول. |

لمشاهدة مثال مباشر على عوامل التشغيل هذه، قم بتشغيلها من قسم **بدء الاستخدام** في التتبع المتقدم.

## <a name="understand-data-types"></a>فهم أنواع البيانات

يدعم التتبع المتقدم أنواع بيانات Kusto، بما في ذلك الأنواع الشائعة التالية:

| نوع البيانات | الآثار المترتبة على الوصف والاستعلام |
|--|--|
| `datetime` | تمثل البيانات ومعلومات الوقت عادة الطوابع الزمنية للحدث. [الاطلاع على تنسيقات التاريخ المعتمدة](/azure/data-explorer/kusto/query/scalar-data-types/datetime) |
| `string` | سلسلة الأحرف في UTF-8 محاطة بعلامات اقتباس مفردة (`'`) أو علامات اقتباس مزدوجة (`"`). [قراءة المزيد حول السلاسل](/azure/data-explorer/kusto/query/scalar-data-types/string) |
| `bool` | يعتمد `true` نوع البيانات هذا أو `false` الحالات. [الاطلاع على القيم الحرفية وعوامل التشغيل المعتمدة](/azure/data-explorer/kusto/query/scalar-data-types/bool) |
| `int` | عدد صحيح 32 بت  |
| `long` | عدد صحيح 64 بت |

لمعرفة المزيد حول أنواع البيانات هذه، [اقرأ عن أنواع بيانات Kusto العددية](/azure/data-explorer/kusto/query/scalar-data-types/).

## <a name="get-help-as-you-write-queries"></a>الحصول على المساعدة أثناء كتابة الاستعلامات

استفد من الوظائف التالية لكتابة الاستعلامات بشكل أسرع:
- **الأخطاء التلقائية** — أثناء كتابة الاستعلامات، يوفر التتبع المتقدم اقتراحات من IntelliSense. 
- **شجرة المخطط** — يتم توفير تمثيل مخطط يتضمن قائمة الجداول والأعمدة الخاصة بها إلى جانب منطقة العمل. لمزيد من المعلومات، مرر مؤشر الماوس فوق عنصر. انقر نقرا مزدوجا فوق عنصر لإدراجه في محرر الاستعلام.
- **[مرجع المخطط](advanced-hunting-schema-tables.md#get-schema-information-in-the-security-center)** - مرجع في المدخل مع أوصاف الجدول والأعمدة بالإضافة إلى أنواع الأحداث المعتمدة (`ActionType` القيم) واستعلامات العينة

## <a name="work-with-multiple-queries-in-the-editor"></a>العمل مع استعلامات متعددة في المحرر

يمكنك استخدام محرر الاستعلام لتجربة استعلامات متعددة. لاستخدام استعلامات متعددة:

- افصل كل استعلام بسطر فارغ.
- ضع المؤشر على أي جزء من الاستعلام لتحديد هذا الاستعلام قبل تشغيله. سيؤدي ذلك إلى تشغيل الاستعلام المحدد فقط. لتشغيل استعلام آخر، انقل المؤشر وفقا لذلك وحدد **"تشغيل الاستعلام**".

:::image type="content" source="../../media/multiple-queries.png" alt-text="مثال على تنفيذ استعلامات متعددة في صفحة **New query** في مدخل Microsoft 365 Defender" lightbox="../../media/multiple-queries.png":::

للحصول على مساحة عمل أكثر كفاءة، يمكنك أيضا استخدام علامات تبويب متعددة في نفس صفحة التتبع. حدد **استعلاما جديدا** لفتح علامة تبويب للاستعلام الجديد.

:::image type="content" source="../../media/multitab.png" alt-text="فتح علامة تبويب جديدة عن طريق تحديد إنشاء جديد في التتبع المتقدم في مدخل Microsoft 365 Defender" lightbox="../../media/multitab.png":::

يمكنك بعد ذلك تشغيل استعلامات مختلفة دون فتح علامة تبويب مستعرض جديدة. 

:::image type="content" source="../../media/multitab-examples.png" alt-text="تشغيل استعلامات مختلفة دون مغادرة صفحة التتبع المتقدمة في مدخل Microsoft 365 Defender" lightbox="../../media/multitab-examples.png":::

>[!NOTE] 
> قد يؤدي استخدام علامات تبويب مستعرض متعددة مع التتبع المتقدم إلى فقدان استعلاماتك غير المحفوظة. لمنع حدوث ذلك، استخدم ميزة علامة التبويب داخل التتبع المتقدم بدلا من علامات تبويب مستعرض منفصلة.

## <a name="use-sample-queries"></a>استخدام استعلامات نموذجية

يوفر قسم **"بدء الاستخدام"** بعض الاستعلامات البسيطة باستخدام عوامل التشغيل شائعة الاستخدام. حاول تشغيل هذه الاستعلامات وإجراء تعديلات صغيرة عليها.

:::image type="content" source="../../media/get-started-section.png" alt-text="قسم **Getting started** في صفحة **Advanced hunting** في مدخل Microsoft 365 Defender" lightbox="../../media/get-started-section.png":::

>[!NOTE]
>وبصرف النظر عن نماذج الاستعلام الأساسية، يمكنك أيضا الوصول إلى [الاستعلامات المشتركة](advanced-hunting-shared-queries.md) لسيناريوهات محددة للبحث عن التهديدات. استكشف الاستعلامات المشتركة على الجانب الأيمن من الصفحة أو [مستودع استعلام GitHub](https://aka.ms/hunting-queries).

## <a name="access-query-language-documentation"></a>وثائق لغة استعلام Access

لمزيد من المعلومات حول لغة استعلام Kusto وعوامل التشغيل المدعومة، راجع [وثائق لغة الاستعلام Kusto](/azure/kusto/query/).

>[!NOTE]
>قد لا تتوفر بعض الجداول في هذه المقالة في Microsoft Defender لنقطة النهاية. [قم بتشغيل Microsoft 365 Defender](m365d-enable.md) للبحث عن التهديدات باستخدام المزيد من مصادر البيانات. يمكنك نقل مهام سير عمل التتبع المتقدمة من Microsoft Defender لنقطة النهاية إلى Microsoft 365 Defender باتباع الخطوات الواردة في [ترحيل استعلامات التتبع المتقدمة من Microsoft Defender لنقطة النهاية](advanced-hunting-migrate-from-mde.md).

## <a name="related-topics"></a>المواضيع ذات الصلة

- [نظرة عامة متقدمة حول الصيد](advanced-hunting-overview.md)
- [استخدام نتائج الاستعلام](advanced-hunting-query-results.md)
- [استخدام الاستعلامات المشتركة](advanced-hunting-shared-queries.md)
- [البحث عبر الأجهزة ورسائل البريد الإلكتروني والتطبيقات والهويات](advanced-hunting-query-emails-devices.md)
- [فهم المخطط](advanced-hunting-schema-tables.md)
- [تطبيق أفضل ممارسات الاستعلام](advanced-hunting-best-practices.md)