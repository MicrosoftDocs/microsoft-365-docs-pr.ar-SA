---
title: تعرف على لغة استعلام الصيد المتقدمة في Microsoft 365 Defender
description: إنشاء استعلام البحث عن المخاطر الأول وتعرف على العوامل الشائعة والجوانب الأخرى للغة استعلام الصيد المتقدم
keywords: الصيد المتقدم، وصيد التهديدات، والصيد عبر الإنترنت، و Microsoft 365 Defender، و microsoft 365، و m365، و البحث، والاستعلام، واللغة، والتعلم، والاستعلام الأول، والتعقب، والأحداث، والتعقب، والكشف المخصص، والم المخطط، و kusto، و عوامل التشغيل، وأنواع البيانات، وتنزيل powershell، مثال الاستعلام
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
ms.openlocfilehash: 7092b4ed30400fb559751d4d939801c1982407f8
ms.sourcegitcommit: 400ef9ac34247978e3de7ecc0b376c4abb6c99d8
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 01/27/2022
ms.locfileid: "63570180"
---
# <a name="learn-the-advanced-hunting-query-language"></a>تعرف على لغة استعلام الصيد المتقدمة

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**ينطبق على:**
- Microsoft 365 Defender
- Microsoft Defender لنقطة النهاية

يستند الصيد المتقدم إلى لغة [استعلام Kusto](/azure/kusto/query/). يمكنك استخدام عوامل تشغيل وعبارات Kusto لإنشاء استعلامات تحدد موقع المعلومات في مخطط [متخصص](advanced-hunting-schema-tables.md). 

شاهد هذا الفيديو القصير للتعرف على بعض أساسيات لغة استعلام Kusto.

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RWRwfJ]
 
لفهم هذه المفاهيم بشكل أفضل، ادير الاستعلام الأول.

## <a name="try-your-first-query"></a>تجربة الاستعلام الأول

في Microsoft 365 Defender، انتقل إلى **البحث لتشغيل** الاستعلام الأول. استخدم المثال التالي: 

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

**[تشغيل هذا الاستعلام في البحث المتقدم](https://security.microsoft.com/hunting?query=H4sIAAAAAAAEAI2TW0sCURSF93PQfxh8Moisp956yYIgQtLoMaYczJpbzkkTpN_et_dcdPQkcpjbmrXXWftyetKTQG5lKqmMpeB9IJksJJKZDOWdZ8wKeP5wvcm3OLgZbMXmXCmIxjnYIfcAVgYvRi8w3TnfsXEDGAG47pCCZXyP5ViO4KeNbt-Up-hEuJmB6lvButnY8XSL-cDl0M2I-GwxVX8Fe2H5zMzHiKjEVB0eEsnBrszfBIWuXOLrxCJ7VqEBfM3DWUYTkNKrv1p5y3X0jwetemzOQ_NSVuuXZ1c6aNTKRaN8VvWhY9n7OS-o6J5r7mYeQypdEKc1m1qfiqpjCSuspsDntt2J61bEvTlXls5AgQfFl5bHM_gr_BhO2RF1rztoBv2tWahrso_TtzkL93KGMGZVr2pe7eWR-xeZl91f_113UOsx3nDR4Y9j5R6kaCq8ajr_YWfFeedsd27L7it-Z6dAZyxsJq1d9-2ZOSzK3y2NVd8-zUPjtZaJnYsIH4Md7AmdeAcd2Cl1XoURc5PzXlfU8U9P54WcswL6t_TW9Q__qX-xygQAAA&runQuery=true&timeRangeId=week)**

### <a name="describe-the-query-and-specify-the-tables-to-search"></a>وصف الاستعلام وتحديد الجداول التي تريد البحث عنها
لقد تم إضافة تعليق قصير إلى بداية الاستعلام لوصف ما هو من أجله. يساعد هذا التعليق إذا قررت لاحقا حفظ الاستعلام ومشاركته مع الآخرين في مؤسستك. 

```kusto
// Finds PowerShell execution events that could involve a download
```

يبدأ الاستعلام نفسه عادة باسم جدول متبوع بعدة عناصر تبدأ بالانبوب (`|`). في هذا المثال، نبدأ بإنشاء اتحاد من جدولين  `DeviceProcessEvents` `DeviceNetworkEvents`، و ، وإضافة عناصر منقطة حسب الحاجة.

```kusto
union DeviceProcessEvents, DeviceNetworkEvents
```
### <a name="set-the-time-range"></a>تعيين النطاق الزمني
إن العنصر الأول الذي يتم الوصول به إلى نقاط هو عامل تصفية الوقت الذي تم تحديد نطاقه إلى الأيام السبعة السابقة. يساعد تحديد النطاق الزمني على ضمان أداء الاستعلامات بشكل جيد، وإرجاع نتائج يمكن إدارتها، و عدم المهلة.

```kusto
| where Timestamp > ago(7d)
```

### <a name="check-specific-processes"></a>التحقق من عمليات معينة
يتبع النطاق الزمني مباشرة البحث عن أسماء ملفات المعالجة التي تمثل تطبيق PowerShell.

```kusto
// Pivoting on PowerShell processes
| where FileName in~ ("powershell.exe", "powershell_ise.exe")
```

### <a name="search-for-specific-command-strings"></a>البحث عن سلاسل أوامر معينة
بعد ذلك، سيبحث الاستعلام عن السلاسل في أسطر الأوامر التي يتم استخدامها عادة لتنزيل الملفات باستخدام PowerShell.

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
الآن بعد أن حدد الاستعلام بوضوح البيانات التي تريد تحديد موقعها، يمكنك تحديد شكل النتائج. `project` إرجاع أعمدة معينة، `top` وحصر عدد النتائج. تساعد عوامل التشغيل هذه على ضمان تنسيق النتائج بشكل جيد وكبيرة إلى حد ما وسهلة المعالجة.

```kusto
| project Timestamp, DeviceName, InitiatingProcessFileName, InitiatingProcessCommandLine, 
FileName, ProcessCommandLine, RemoteIP, RemoteUrl, RemotePort, RemoteIPType
| top 100 by Timestamp
```

حدد **تشغيل الاستعلام** لرؤية النتائج.

>[!TIP]
>يمكنك عرض نتائج الاستعلام كمخططات وضبط عوامل التصفية بسرعة. للحصول على الإرشادات [، اقرأ حول استخدام نتائج الاستعلام](advanced-hunting-query-results.md)

## <a name="learn-common-query-operators"></a>تعرف على عوامل تشغيل الاستعلامات الشائعة

لقد قمت للتو بتشغيل الاستعلام الأول لديك وفكرة عامة حول مكوناته. لقد حان الوقت للتراجع قليلا وتعرف على بعض الأساسيات. تدعم لغة استعلام Kusto المستخدمة بواسطة الصيد المتقدم مجموعة من العوامل، بما في ذلك العوامل الشائعة التالية.

| عامل التشغيل | الوصف والاستخدام |
|--|--|
| `where` | تصفية جدول إلى المجموعة الفرعية للصفوف التي تفي بالتكريس. |
| `summarize` | إنتاج جدول يجمع محتوى جدول الإدخال. |
| `join` | يمكنك دمج صفوف جدولين لتشكيل جدول جديد من خلال مطابقة قيم الأعمدة المحددة من كل جدول. |
| `count` | إرجاع عدد السجلات في مجموعة سجلات الإدخال. |
| `top` | إرجاع أول سجلات N تم فرزها حسب الأعمدة المحددة. |
| `limit` | الرجوع إلى عدد الصفوف المحدد. |
| `project` | حدد الأعمدة لتضمينها وإعادة تسميتها أو إسقاطها وإدراج أعمدة محسبة جديدة. |
| `extend` | إنشاء أعمدة محسوبة و إلحاقها مجموعة النتائج. |
| `makeset` |  إرجاع صفيف ديناميكي (JSON) لمجموعة القيم المميزة التي يأخذها Expr في المجموعة. |
| `find` | ابحث عن الصفوف التي تتطابق مع أحد الإعدادات عبر مجموعة من الجداول. |

لرؤية مثال مباشر على عوامل التشغيل هذه، يمكنك تشغيلها من القسم **بدء** العمل في عملية الصيد المتقدمة.

## <a name="understand-data-types"></a>فهم أنواع البيانات

يدعم الصيد المتقدم أنواع بيانات Kusto، بما في ذلك الأنواع الشائعة التالية:

| نوع البيانات | الآثار المترتبة على الوصف والاستعلام |
|--|--|
| `datetime` | تمثل معلومات البيانات والوقت عادة الamps الزمنية للحدث. [الاطلاع على تنسيقات التاريخ المعتمدة](/azure/data-explorer/kusto/query/scalar-data-types/datetime) |
| `string` | سلسلة أحرف في UTF-8 محاطة بين علامات اقتباس مفردة (`'`) أو علامات اقتباس مزدوجة (`"`). [قراءة المزيد حول السلاسل](/azure/data-explorer/kusto/query/scalar-data-types/string) |
| `bool` | يدعم نوع البيانات هذا `true` الحالات أو `false` يدعمها. [الاطلاع على الحرفيات و عوامل التشغيل المعتمدة](/azure/data-explorer/kusto/query/scalar-data-types/bool) |
| `int` | عدد صحيح 32 بت  |
| `long` | عدد صحيح 64 بت |

لمعرفة المزيد حول أنواع البيانات هذه، [اقرأ حول أنواع بيانات كستو عددية](/azure/data-explorer/kusto/query/scalar-data-types/).

## <a name="get-help-as-you-write-queries"></a>الحصول على تعليمات عند كتابة الاستعلامات
استفد من الوظائف التالية لكتابة الاستعلامات بشكل أسرع:
- **"الاقتراح التلقائي"**، بينما تكتب الاستعلامات، يوفر البحث المتقدم اقتراحات من IntelliSense. 
- **شجرة المخططات**— تمثيل مخطط يتضمن قائمة الجداول والأعمدة الخاصة بها إلى جانب منطقة العمل. لمزيد من المعلومات، مرر فوق عنصر. انقر نقرا مزدوجا فوق عنصر لإدراجه في محرر الاستعلام.
- **[مرجع المخطط —](advanced-hunting-schema-tables.md#get-schema-information-in-the-security-center)** مرجع داخل المدخل مع أوصاف الأعمدة والأعمدة بالإضافة إلى أنواع الأحداث المعتمدة (`ActionType` القيم) والاستعلامات العينة

## <a name="work-with-multiple-queries-in-the-editor"></a>استخدام استعلامات متعددة في المحرر
يمكنك استخدام محرر الاستعلام لتجربة استعلامات متعددة. لاستخدام استعلامات متعددة:

- افصل كل استعلام باستخدام سطر فارغ.
- ضع المؤشر على أي جزء من الاستعلام لتحديد ذلك الاستعلام قبل تشغيله. سيتم تشغيل الاستعلام المحدد فقط. لتشغيل استعلام آخر، حرك المؤشر وفقا لذلك وحدد **تشغيل الاستعلام**.

:::image type="content" source="../../media/learn-work-with-multiple.png" alt-text="مثال لتنفيذ استعلامات متعددة في صفحة **استعلام جديد** في Microsoft 365 Defender" lightbox="../../media/learn-work-with-multiple.png":::

## <a name="use-sample-queries"></a>استخدام استعلامات نموذجية

يوفر **القسم بدء** استخدام بعض الاستعلامات البسيطة باستخدام عوامل التشغيل الشائع استخدامها. حاول تشغيل هذه الاستعلامات وأجري تعديلات صغيرة عليها.

:::image type="content" source="../../media/get-started-section.png" alt-text="المقطع **بدء استخدام** في صفحة ***أدوات الصيد المتقدمة** في مدخل Microsoft 365 Defender" lightbox="../../media/get-started-section.png":::

>[!NOTE]
>وبصرف النظر عن نماذج الاستعلامات الأساسية، يمكنك أيضا الوصول إلى الاستعلامات [المشتركة](advanced-hunting-shared-queries.md) لسيناريوهات محددة لتعقب المخاطر. استكشف الاستعلامات المشتركة على الجانب الأيمن من الصفحة أو مستودع GitHub [الاستعلام.](https://aka.ms/hunting-queries)

## <a name="access-query-language-documentation"></a>وثائق لغة استعلام Access

لمزيد من المعلومات حول لغة استعلام Kusto و عوامل التشغيل المعتمدة، راجع [وثائق لغة استعلام Kusto](/azure/kusto/query/).

>[!NOTE]
>قد لا تتوفر بعض الجداول في هذه المقالة في Microsoft Defender for Endpoint. [قم Microsoft 365 Defender](m365d-enable.md) للبحث عن التهديدات باستخدام المزيد من مصادر البيانات. يمكنك نقل مهام سير عمل الصيد المتقدمة من Microsoft Defender ل Endpoint إلى Microsoft 365 Defender باتباع الخطوات الواردة في ترحيل استعلامات الصيد المتقدمة من [Microsoft Defender ل Endpoint](advanced-hunting-migrate-from-mde.md).

## <a name="related-topics"></a>المواضيع ذات الصلة
- [نظرة عامة متقدمة حول الصيد](advanced-hunting-overview.md)
- [استخدام نتائج الاستعلام](advanced-hunting-query-results.md)
- [استخدام الاستعلامات المشتركة](advanced-hunting-shared-queries.md)
- [البحث عبر الأجهزة ورسائل البريد الإلكتروني والتطبيقات والهويات](advanced-hunting-query-emails-devices.md)
- [فهم المخطط](advanced-hunting-schema-tables.md)
- [تطبيق أفضل ممارسات الاستعلام](advanced-hunting-best-practices.md)