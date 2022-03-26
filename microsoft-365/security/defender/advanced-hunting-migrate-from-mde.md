---
title: ترحيل استعلامات البحث المتقدمة من Microsoft Defender ل Endpoint
description: تعرف على كيفية ضبط استعلامات نقطة النهاية في Microsoft Defender حتى تتمكن من استخدامها في Microsoft 365 Defender
keywords: الصيد المتقدم، وصيد التهديدات، والصيد عبر الإنترنت، Microsoft 365 Defender، و microsoft 365، و m365، و Microsoft Defender ل Endpoint، والبحث، والاستعلام، والتعقب، والاكتشافات المخصصة، والمخطط، و kusto، ورسم الخرائط
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
ms.openlocfilehash: e64d1a56468d6e87d23c5720bb231e17ecd5679a
ms.sourcegitcommit: 6f3bc00a5cf25c48c61eb3835ac069e9f41dc4db
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 01/24/2022
ms.locfileid: "63573401"
---
# <a name="migrate-advanced-hunting-queries-from-microsoft-defender-for-endpoint"></a>ترحيل استعلامات البحث المتقدمة من Microsoft Defender ل Endpoint

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**ينطبق على:**
- Microsoft 365 Defender

انتقل مهام سير العمل المتقدمة للصيد من Microsoft Defender for Endpoint للبحث بشكل استباقي عن التهديدات باستخدام مجموعة أكبر من البيانات. في Microsoft 365 Defender، يمكنك الوصول إلى البيانات من حلول أمان Microsoft 365 الأخرى، بما في ذلك:

- Microsoft Defender لنقطة النهاية
- Microsoft Defender Office 365
- Microsoft Defender لتطبيقات السحابة
- Microsoft Defender for Identity

>[!NOTE]
>يمكن لمعظم عملاء Microsoft Defender ل Endpoint [Microsoft 365 Defender دون تراخيص إضافية](prerequisites.md#licensing-requirements). لبدء نقل مهام سير العمل المتقدمة للصيد من Defender for Endpoint، [قم Microsoft 365 Defender](m365d-enable.md).

يمكنك الانتقال دون التأثير على مهام سير عمل Defender for Endpoint الموجودة. تظل الاستعلامات المحفوظة بدون تغيير، كما تستمر قواعد الكشف المخصصة في التشغيل وإنشاء التنبيهات. ومع ذلك، ستكون مرئية في Microsoft 365 Defender. 

## <a name="schema-tables-in-microsoft-365-defender-only"></a>جداول المخططات في Microsoft 365 Defender فقط
يوفر [Microsoft 365 Defender البحث](advanced-hunting-schema-tables.md) المتقدم جداول إضافية تحتوي على بيانات من حلول أمان Microsoft 365 مختلفة. تتوفر الجداول التالية فقط في Microsoft 365 Defender:

| اسم الجدول | الوصف |
|------------|-------------|
| [AlertEvidence](advanced-hunting-alertevidence-table.md) | الملفات أو عناوين IP أو عناوين URL أو المستخدمين أو الأجهزة المقترنة بالتنبيهات |
| [AlertInfo](advanced-hunting-alertinfo-table.md) | تنبيهات من Microsoft Defender لنقطة النهاية و Microsoft Defender ل Office 365 و Microsoft Defender لتطبيقات السحابة و Microsoft Defender for Identity، بما في ذلك معلومات الخطورة وفئات التهديدات  |
| [EmailAttachmentInfo](advanced-hunting-emailattachmentinfo-table.md) | معلومات حول الملفات المرفقة ببريدات البريد الإلكتروني |
| [EmailEvents](advanced-hunting-emailevents-table.md) | Microsoft 365 البريد الإلكتروني، بما في ذلك تسليم البريد الإلكتروني والأحداث المحظورة |
| [EmailPostDeliveryEvents](advanced-hunting-emailpostdeliveryevents-table.md) | أحداث الأمان التي تحدث بعد التسليم، بعد Microsoft 365 تسليم رسائل البريد الإلكتروني إلى علبة بريد المستلم |
| [EmailUrlInfo](advanced-hunting-emailurlinfo-table.md) | معلومات حول عناوين URL على رسائل البريد الإلكتروني |
| [IdentityDirectoryEvents](advanced-hunting-identitydirectoryevents-table.md) | الأحداث التي تتضمن وحدة تحكم المجال المحلي التي تقوم بتشغيل Active Directory (AD). يتناول هذا الجدول مجموعة من الأحداث المتعلقة بالهوية والأحداث المتعلقة بالهوية على وحدة التحكم بالمجال. |
| [IdentityInfo](advanced-hunting-identityinfo-table.md) | معلومات الحساب من مصادر مختلفة، بما في ذلك Azure Active Directory |
| [IdentityLogonEvents](advanced-hunting-identitylogonevents-table.md) | أحداث المصادقة على خدمات Active Directory و Microsoft عبر الإنترنت |
| [IdentityQueryEvents](advanced-hunting-identityqueryevents-table.md) | الاستعلامات الخاصة بكائنات Active Directory، مثل المستخدمين والمجموعات والأجهزة والمجالات |

>[!IMPORTANT]
> يمكن عرض الاستعلامات والاكتشافات المخصصة التي تستخدم جداول المخططات المتوفرة في Microsoft 365 Defender فقط في Microsoft 365 Defender.

## <a name="map-devicealertevents-table"></a>جدول Map DeviceAlertEvents
يستبدل `AlertInfo` الجدولان `AlertEvidence` و `DeviceAlertEvents` الجدول في مخطط Microsoft Defender لنقطة النهاية. بالإضافة إلى بيانات حول تنبيهات الجهاز، يتضمن هذان الجدولان بيانات حول تنبيهات الهويات والتطبيقات ورسائل البريد الإلكتروني.

استخدم الجدول التالي للتحقق من كيفية `DeviceAlertEvents` تعيين الأعمدة إلى أعمدة في الجداول `AlertInfo` و `AlertEvidence` .

>[!TIP]
>بالإضافة إلى الأعمدة `AlertEvidence` في الجدول التالي، يتضمن الجدول العديد من الأعمدة الأخرى التي توفر صورة أكثر شمولية للتنبيهات من مصادر مختلفة. [الاطلاع على كل أعمدة AlertEvidence](advanced-hunting-alertevidence-table.md) 

| عمود DeviceAlertEvents | مكان العثور على البيانات نفسها في Microsoft 365 Defender |
|-------------|-----------|-------------|-------------|
| `AlertId` | `AlertInfo`والجداول `AlertEvidence` |
| `Timestamp` | `AlertInfo`والجداول `AlertEvidence` |
| `DeviceId` | `AlertEvidence` جدول |
| `DeviceName` | `AlertEvidence` جدول |
| `Severity` | `AlertInfo` جدول |
| `Category` | `AlertInfo` جدول |
| `Title` | `AlertInfo` جدول |
| `FileName` | `AlertEvidence` جدول |
| `SHA1` | `AlertEvidence` جدول |
| `RemoteUrl` | `AlertEvidence` جدول |
| `RemoteIP` | `AlertEvidence` جدول |
| `AttackTechniques` | `AlertInfo` جدول |
| `ReportId` | يستخدم هذا العمود عادة في Microsoft Defender لنقطة النهاية لتحديد موقع السجلات المرتبطة في جداول أخرى. في Microsoft 365 Defender، يمكنك الحصول على البيانات ذات الصلة مباشرة من `AlertEvidence` الجدول. |
| `Table` | يستخدم هذا العمود عادة في Microsoft Defender لنقطة النهاية للحصول على معلومات أحداث إضافية في الجداول الأخرى. في Microsoft 365 Defender، يمكنك الحصول على البيانات ذات الصلة مباشرة من `AlertEvidence` الجدول. |

## <a name="adjust-existing-microsoft-defender-for-endpoint-queries"></a>ضبط استعلامات Microsoft Defender الموجودة لنقطة النهاية
ستعمل استعلامات Microsoft Defender لنقطة النهاية كما هي إلا إذا كانت تشير إلى `DeviceAlertEvents` الجدول. لاستخدام هذه الاستعلامات في Microsoft 365 Defender، قم بتطبيق هذه التغييرات:

- استبدل `DeviceAlertEvents` ب `AlertInfo`.
- انضم إلى `AlertInfo` الجداول `AlertEvidence` والجداول للحصول `AlertId` على بيانات مكافئة.

### <a name="original-query"></a>الاستعلام الأصلي
يستخدم الاستعلام التالي `DeviceAlertEvents` في Microsoft Defender لنقطة النهاية للحصول على التنبيهات _التي تتضمنpowershell.exe_:

```kusto
DeviceAlertEvents
| where Timestamp > ago(7d) 
| where AttackTechniques has "PowerShell (T1086)" and FileName == "powershell.exe"
```
### <a name="modified-query"></a>استعلام معدل
تم ضبط الاستعلام التالي لاستخدامه في Microsoft 365 Defender. بدلا من التحقق من اسم الملف مباشرة من `DeviceAlertEvents`، فإنه ينضم `AlertEvidence` ويتحقق من اسم الملف في هذا الجدول.

```kusto
AlertInfo 
| where Timestamp > ago(7d) 
| where AttackTechniques has "PowerShell (T1086)" 
| join AlertEvidence on AlertId
| where FileName == "powershell.exe"
```

## <a name="migrate-custom-detection-rules"></a>ترحيل قواعد الكشف المخصصة

عند تحرير قواعد Microsoft Defender لنقطة النهاية Microsoft 365 Defender، فإنها تستمر في العمل كما كان من قبل إذا كان الاستعلام الناتج ينظر إلى جداول الأجهزة فقط. 

على سبيل المثال، سيستمر تسليم التنبيهات التي يتم إنشاؤها بواسطة قواعد الكشف المخصصة التي تقوم باستعلام جداول الأجهزة فقط إلى SIEM وإنشاء إعلامات بالبريد الإلكتروني، استنادا إلى كيفية تكوينها في Microsoft Defender ل Endpoint. ستستمر أيضا أي قواعد منع موجودة في Defender for Endpoint في تطبيقها.

بمجرد تحرير قاعدة Defender لنقطة النهاية بحيث يتم الاستعلام عن جداول الهوية والبريد الإلكتروني، المتوفرة فقط في Microsoft 365 Defender، يتم نقل القاعدة تلقائيا إلى Microsoft 365 Defender. 

التنبيهات التي تم إنشاؤها بواسطة القاعدة التي تم ترحيلها:

- لم تعد مرئية في مدخل Defender for Endpoint (مركز حماية Microsoft Defender)
- توقف عن التسليم إلى SIEM أو يمكنك إنشاء إعلامات بالبريد الإلكتروني. لتغيير هذا التغيير، قم بتكوين الإعلامات Microsoft 365 Defender للحصول على التنبيهات. يمكنك استخدام Microsoft 365 Defender [API](api-incident.md) لتلقي إعلامات تنبيهات الكشف عن العملاء أو الأحداث ذات الصلة.
- لن يتم منعه بواسطة قواعد منع نقطة النهاية ل Microsoft Defender. لمنع إنشاء تنبيهات لمستخدمين أو أجهزة أو علب بريد معينة، قم بتعديل الاستعلامات المقابلة لاستبعاد تلك الكيانات بشكل صريح.

إذا قمت بتحرير قاعدة بهذه الطريقة، سيتم مطالبتك بتأكيدها قبل تطبيق هذه التغييرات.

يتم عرض التنبيهات الجديدة التي تم إنشاؤها بواسطة قواعد الكشف Microsoft 365 Defender في صفحة تنبيه توفر المعلومات التالية:

- عنوان التنبيه ووصفه 
- الأصول المتأثّر بها
- الإجراءات التي تم اتخاذها استجابة للتنبيه
- نتائج الاستعلام التي تسببت في تشغيل التنبيه 
- معلومات حول قاعدة الكشف المخصص 
 
> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/new-alert-page.png" alt-text="مثال لصفحة تنبيه تعرض تنبيهات جديدة تم إنشاؤها بواسطة قواعد الكشف المخصصة في Microsoft 365 Defender مدخل" lightbox="../../media/new-alert-page.png":::

## <a name="write-queries-without-devicealertevents"></a>كتابة الاستعلامات بدون DeviceAlertEvents

في Microsoft 365 Defender، `AlertInfo` `AlertEvidence` يتم توفير الجداول والجداول لاحتواء مجموعة متنوعة من المعلومات التي تصاحب التنبيهات من مصادر مختلفة. 

`DeviceAlertEvents` للحصول على معلومات التنبيه نفسها التي استخدمتها للحصول على معلومات من الجدول في مخطط Microsoft Defender لنقطة `AlertInfo` `ServiceSource` `AlertEvidence` النهاية، قم بتصفية الجدول حسب، ثم قم بضم كل رقم فريد مع الجدول، الذي يوفر معلومات مفصلة حول الحدث والكيانات. 

راجع الاستعلام النموذجي أدناه:

```kusto
AlertInfo
| where Timestamp > ago(7d)
| where ServiceSource == "Microsoft Defender for Endpoint"
| join AlertEvidence on AlertId
```

يوفر هذا الاستعلام أعمدة أكثر من `DeviceAlertEvents` تلك التي يوفرها مخطط Microsoft Defender لنقطة النهاية. لإبقاء النتائج قابلة للإدارة، استخدمها `project` للحصول على الأعمدة التي تريدها فقط. المثال أدناه المشاريع الأعمدة التي قد تكون مهتما بها عندما كشف التحقيق عن نشاط PowerShell:

```kusto
AlertInfo
| where Timestamp > ago(7d)
| where ServiceSource == "Microsoft Defender for Endpoint"
    and AttackTechniques has "powershell"
| join AlertEvidence on AlertId
| project Timestamp, Title, AlertId, DeviceName, FileName, ProcessCommandLine 
```

إذا كنت تريد التصفية `EntityType` لكيانات معينة مفعلة في التنبيهات، يمكنك القيام بذلك من خلال تحديد نوع الكيان والقيمة التي تريد التصفية لها. في المثال التالي، ابحث عن عنوان IP معين:

```kusto
AlertInfo
| where Title == "Insert_your_alert_title"
| join AlertEvidence on AlertId 
| where EntityType == "Ip" and RemoteIP == "192.88.99.01" 
```

## <a name="see-also"></a>راجع أيضًا
- [تشغيل Microsoft 365 Defender](advanced-hunting-query-language.md)
- [نظرة عامة متقدمة حول الصيد](advanced-hunting-overview.md)
- [فهم المخطط](advanced-hunting-schema-tables.md)
- [الصيد المتقدم في Microsoft Defender لنقطة النهاية](/windows/security/threat-protection/microsoft-defender-atp/advanced-hunting-overview)
