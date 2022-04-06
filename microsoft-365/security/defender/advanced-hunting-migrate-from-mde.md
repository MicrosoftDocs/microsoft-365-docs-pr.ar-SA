---
title: ترحيل استعلامات التتبع المتقدمة من Microsoft Defender لنقطة النهاية
description: تعرف على كيفية ضبط استعلامات Microsoft Defender لنقطة النهاية حتى تتمكن من استخدامها في Microsoft 365 Defender
keywords: التتبع المتقدم، تتبع التهديدات، تتبع التهديدات عبر الإنترنت، Microsoft 365 Defender، microsoft 365، m365، Microsoft Defender لنقطة النهاية، البحث، الاستعلام، بيانات تتبع الاستخدام، الكشف المخصص، المخطط، kusto، التعيين
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
ms.topic: article
ms.custom: seo-marvel-apr2020
ms.technology: m365d
ms.openlocfilehash: 9fd00df5e61d37e5133f23e5f06973ceb99c4636
ms.sourcegitcommit: 85ce5fd0698b6f00ea1ea189634588d00ea13508
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/06/2022
ms.locfileid: "64666163"
---
# <a name="migrate-advanced-hunting-queries-from-microsoft-defender-for-endpoint"></a>ترحيل استعلامات التتبع المتقدمة من Microsoft Defender لنقطة النهاية

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**ينطبق على:**
- Microsoft 365 Defender

انقل مهام سير عمل التتبع المتقدمة من Microsoft Defender لنقطة النهاية إلى البحث بشكل استباقي عن التهديدات باستخدام مجموعة أوسع من البيانات. في Microsoft 365 Defender، يمكنك الوصول إلى البيانات من حلول أمان Microsoft 365 أخرى، بما في ذلك:

- Microsoft Defender for Endpoint
- Microsoft Defender لـ Office 365
- Microsoft Defender for Cloud Apps
- Microsoft Defender for Identity

>[!NOTE]
>يمكن لمعظم العملاء Microsoft Defender لنقطة النهاية [استخدام Microsoft 365 Defender دون تراخيص إضافية](prerequisites.md#licensing-requirements). لبدء نقل مهام سير عمل التتبع المتقدمة من Defender لنقطة النهاية، [قم بتشغيل Microsoft 365 Defender](m365d-enable.md).

يمكنك الانتقال دون التأثير على سير عمل Defender لنقطة النهاية الحالية. تظل الاستعلامات المحفوظة سليمة، وتستمر قواعد الكشف المخصصة في تشغيل التنبيهات وإنشاءها. ومع ذلك، ستكون مرئية في Microsoft 365 Defender.

## <a name="schema-tables-in-microsoft-365-defender-only"></a>جداول المخطط في Microsoft 365 Defender فقط

يوفر [مخطط التتبع المتقدم Microsoft 365 Defender](advanced-hunting-schema-tables.md) جداول إضافية تحتوي على بيانات من حلول أمان Microsoft 365 مختلفة. تتوفر الجداول التالية فقط في Microsoft 365 Defender:

| اسم الجدول | الوصف |
|------------|-------------|
| [AlertEvidence](advanced-hunting-alertevidence-table.md) | الملفات أو عناوين IP أو عناوين URL أو المستخدمين أو الأجهزة المقترنة بالتنبيهات |
| [AlertInfo](advanced-hunting-alertinfo-table.md) | تنبيهات من Microsoft Defender لنقطة النهاية Microsoft Defender لـ Office 365 Microsoft Defender for Cloud Apps Microsoft Defender for Identity ، بما في ذلك معلومات الخطورة وفئات التهديد  |
| [EmailAttachmentInfo](advanced-hunting-emailattachmentinfo-table.md) | معلومات حول الملفات المرفقة برسائل البريد الإلكتروني |
| [EmailEvents](advanced-hunting-emailevents-table.md) | Microsoft 365 أحداث البريد الإلكتروني، بما في ذلك تسليم البريد الإلكتروني وحظر الأحداث |
| [EmailPostDeliveryEvents](advanced-hunting-emailpostdeliveryevents-table.md) | أحداث الأمان التي تحدث بعد التسليم، بعد تسليم Microsoft 365 رسائل البريد الإلكتروني إلى علبة بريد المستلم |
| [EmailUrlInfo](advanced-hunting-emailurlinfo-table.md) | معلومات حول عناوين URL على رسائل البريد الإلكتروني |
| [IdentityDirectoryEvents](advanced-hunting-identitydirectoryevents-table.md) | الأحداث التي تتضمن وحدة تحكم مجال محلية تقوم بتشغيل Active Directory (AD). يغطي هذا الجدول مجموعة من الأحداث المتعلقة بالهوية وأحداث النظام على وحدة التحكم بالمجال. |
| [IdentityInfo](advanced-hunting-identityinfo-table.md) | معلومات الحساب من مصادر مختلفة، بما في ذلك Azure Active Directory |
| [IdentityLogonEvents](advanced-hunting-identitylogonevents-table.md) | أحداث المصادقة على Active Directory وMicrosoft خدمات الإنترنت |
| [IdentityQueryEvents](advanced-hunting-identityqueryevents-table.md) | استعلامات كائنات Active Directory، مثل المستخدمين والمجموعات والأجهزة والمجالات |

>[!IMPORTANT]
> يمكن عرض الاستعلامات والكشف المخصص الذي يستخدم جداول المخطط المتوفرة فقط في Microsoft 365 Defender فقط في Microsoft 365 Defender.

## <a name="map-devicealertevents-table"></a>جدول Map DeviceAlertEvents

تحل الجداول `AlertInfo` والجداول `AlertEvidence` محل `DeviceAlertEvents` الجدول في مخطط Microsoft Defender لنقطة النهاية. بالإضافة إلى بيانات حول تنبيهات الجهاز، يتضمن هذان الجدولان بيانات حول التنبيهات للهويات والتطبيقات ورسائل البريد الإلكتروني.

استخدم الجدول التالي للتحقق من كيفية `DeviceAlertEvents` تعيين الأعمدة إلى أعمدة في الجداول`AlertInfo`.`AlertEvidence`

> [!TIP]
> بالإضافة إلى الأعمدة في الجدول التالي، `AlertEvidence` يتضمن الجدول العديد من الأعمدة الأخرى التي توفر صورة أكثر شمولية للتنبيهات من مصادر مختلفة. [عرض كافة أعمدة AlertEvidence](advanced-hunting-alertevidence-table.md)

| عمود DeviceAlertEvents | مكان العثور على نفس البيانات في Microsoft 365 Defender |
|-------------|-----------|-------------|-------------|
| `AlertId` | `AlertInfo`والجداول `AlertEvidence` |
| `Timestamp` | `AlertInfo`والجداول `AlertEvidence` |
| `DeviceId` | `AlertEvidence` الجدول |
| `DeviceName` | `AlertEvidence` الجدول |
| `Severity` | `AlertInfo` الجدول |
| `Category` | `AlertInfo` الجدول |
| `Title` | `AlertInfo` الجدول |
| `FileName` | `AlertEvidence` الجدول |
| `SHA1` | `AlertEvidence` الجدول |
| `RemoteUrl` | `AlertEvidence` الجدول |
| `RemoteIP` | `AlertEvidence` الجدول |
| `AttackTechniques` | `AlertInfo` الجدول |
| `ReportId` | يستخدم هذا العمود عادة في Microsoft Defender لنقطة النهاية لتحديد موقع السجلات ذات الصلة في جداول أخرى. في Microsoft 365 Defender، يمكنك الحصول على البيانات ذات الصلة مباشرة من `AlertEvidence` الجدول. |
| `Table` | يستخدم هذا العمود عادة في Microsoft Defender لنقطة النهاية للحصول على معلومات أحداث إضافية في جداول أخرى. في Microsoft 365 Defender، يمكنك الحصول على البيانات ذات الصلة مباشرة من `AlertEvidence` الجدول. |

## <a name="adjust-existing-microsoft-defender-for-endpoint-queries"></a>ضبط استعلامات Microsoft Defender لنقطة النهاية الموجودة

ستعمل الاستعلامات Microsoft Defender لنقطة النهاية كما هي إلا إذا كانت تشير إلى `DeviceAlertEvents` الجدول. لاستخدام هذه الاستعلامات في Microsoft 365 Defender، قم بتطبيق هذه التغييرات:

- استبدال `DeviceAlertEvents` ب `AlertInfo`.
- انضم إلى الجداول `AlertInfo` `AlertEvidence` للحصول على `AlertId` بيانات مكافئة.

### <a name="original-query"></a>الاستعلام الأصلي

يستخدم `DeviceAlertEvents` الاستعلام التالي في Microsoft Defender لنقطة النهاية للحصول على التنبيهات التي تتضمن _powershell.exe_:

```kusto
DeviceAlertEvents
| where Timestamp > ago(7d)
| where AttackTechniques has "PowerShell (T1086)" and FileName == "powershell.exe"
```

### <a name="modified-query"></a>الاستعلام المعدل

تم ضبط الاستعلام التالي لاستخدامه في Microsoft 365 Defender. بدلا من التحقق من اسم الملف مباشرة من `DeviceAlertEvents`، فإنه يربط `AlertEvidence` ويتحقق من اسم الملف في هذا الجدول.

```kusto
AlertInfo
| where Timestamp > ago(7d)
| where AttackTechniques has "PowerShell (T1086)"
| join AlertEvidence on AlertId
| where FileName == "powershell.exe"
```

## <a name="migrate-custom-detection-rules"></a>ترحيل قواعد الكشف المخصصة

عند تحرير قواعد Microsoft Defender لنقطة النهاية على Microsoft 365 Defender، فإنها تستمر في العمل كما كان من قبل إذا نظر الاستعلام الناتج إلى جداول الجهاز فقط.

على سبيل المثال، سيستمر تسليم التنبيهات التي تم إنشاؤها بواسطة قواعد الكشف المخصصة التي تستعلم عن جداول الأجهزة فقط إلى SIEM وإنشاء إعلامات بالبريد الإلكتروني، اعتمادا على كيفية تكوينها في Microsoft Defender لنقطة النهاية. سيستمر أيضا تطبيق أي قواعد منع موجودة في Defender لنقطة النهاية.

بمجرد تحرير قاعدة Defender لنقطة النهاية بحيث تستعلم عن الهوية وجداول البريد الإلكتروني، والتي تتوفر فقط في Microsoft 365 Defender، يتم نقل القاعدة تلقائيا إلى Microsoft 365 Defender.

التنبيهات التي تم إنشاؤها بواسطة القاعدة التي تم ترحيلها:

- لم تعد مرئية في مدخل Defender لنقطة النهاية (مركز حماية Microsoft Defender)
- توقف عن التسليم إلى SIEM أو قم بإنشاء إعلامات بالبريد الإلكتروني. للتغلب على هذا التغيير، قم بتكوين الإعلامات من خلال Microsoft 365 Defender للحصول على التنبيهات. يمكنك استخدام [واجهة برمجة تطبيقات Microsoft 365 Defender](api-incident.md) لتلقي إعلامات لتنبيهات الكشف عن العملاء أو الحوادث ذات الصلة.
- لن يتم منعها بواسطة قواعد منع Microsoft Defender لنقطة النهاية. لمنع إنشاء تنبيهات لبعض المستخدمين أو الأجهزة أو علب البريد، قم بتعديل الاستعلامات المقابلة لاستبعاد هذه الكيانات بشكل صريح.

إذا قمت بتحرير قاعدة بهذه الطريقة، فستتم مطالبتك بالتأكيد قبل تطبيق مثل هذه التغييرات.

يتم عرض التنبيهات الجديدة التي تم إنشاؤها بواسطة قواعد الكشف المخصصة في Microsoft 365 Defender في صفحة تنبيه توفر المعلومات التالية:

- عنوان التنبيه ووصفه
- الأصول المتأثرة
- الإجراءات التي تم اتخاذها استجابة للتنبيه
- نتائج الاستعلام التي قامت بتشغيل التنبيه
- معلومات حول قاعدة الكشف المخصصة

> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/new-alert-page.png" alt-text="مثال على صفحة تنبيه تعرض تنبيهات جديدة تم إنشاؤها بواسطة قواعد الكشف المخصصة في مدخل Microsoft 365 Defender" lightbox="../../media/new-alert-page.png":::

## <a name="write-queries-without-devicealertevents"></a>كتابة الاستعلامات بدون DeviceAlertEvents

في المخطط Microsoft 365 Defender، يتم توفير الجداول `AlertInfo` `AlertEvidence` لاستيعاب مجموعة متنوعة من المعلومات التي تصاحب التنبيهات من مصادر مختلفة.

للحصول على نفس معلومات التنبيه التي استخدمتها للحصول على من `DeviceAlertEvents` الجدول في مخطط Microsoft Defender لنقطة النهاية، قم بتصفية `AlertInfo` الجدول ثم قم بضم `ServiceSource` كل معرف فريد مع `AlertEvidence` الجدول، الذي يوفر معلومات مفصلة عن الحدث والكيان.

راجع نموذج الاستعلام أدناه:

```kusto
AlertInfo
| where Timestamp > ago(7d)
| where ServiceSource == "Microsoft Defender for Endpoint"
| join AlertEvidence on AlertId
```

ينتج عن هذا الاستعلام العديد من الأعمدة أكثر مما `DeviceAlertEvents` هو موجود في المخطط Microsoft Defender لنقطة النهاية. للاحتفاظ بالنتائج قابلة للإدارة، استخدمها `project` للحصول على الأعمدة التي تهتم بها فقط. يعرض المثال أدناه الأعمدة التي قد تكون مهتما بها عندما كشف التحقيق عن نشاط PowerShell:

```kusto
AlertInfo
| where Timestamp > ago(7d)
| where ServiceSource == "Microsoft Defender for Endpoint"
    and AttackTechniques has "powershell"
| join AlertEvidence on AlertId
| project Timestamp, Title, AlertId, DeviceName, FileName, ProcessCommandLine
```

إذا كنت ترغب في التصفية لكيانات معينة مضمنة في التنبيهات، يمكنك القيام بذلك عن طريق تحديد نوع الكيان والقيمة التي ترغب في `EntityType` التصفية لها. يبحث المثال التالي عن عنوان IP محدد:

```kusto
AlertInfo
| where Title == "Insert_your_alert_title"
| join AlertEvidence on AlertId
| where EntityType == "Ip" and RemoteIP == "192.88.99.01"
```

## <a name="see-also"></a>راجع أيضًا

- [تمكين Microsoft 365 Defender](advanced-hunting-query-language.md)
- [نظرة عامة متقدمة حول الصيد](advanced-hunting-overview.md)
- [فهم المخطط](advanced-hunting-schema-tables.md)
- [التتبع المتقدم في Microsoft Defender لنقطة النهاية](/windows/security/threat-protection/microsoft-defender-atp/advanced-hunting-overview)
