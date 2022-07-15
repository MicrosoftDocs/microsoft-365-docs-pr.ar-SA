---
title: الدالة FileProfile() في التتبع المتقدم Microsoft 365 Defender
description: تعرف على كيفية استخدام FileProfile() لإثراء معلومات حول الملفات في نتائج استعلام التتبع المتقدمة
keywords: التتبع المتقدم، تتبع التهديدات، تتبع التهديدات عبر الإنترنت، Microsoft 365 Defender، microsoft 365، m365، البحث، الاستعلام، بيانات تتبع الاستخدام، مرجع المخطط، kusto، FileProfile، ملف تعريف الملف، الوظيفة، الإثراء
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
ms.collection: m365-security-compliance
ms.topic: article
ms.technology: m365d
ms.openlocfilehash: 3e530bd9c1e6af58c83a88fc16b5ac4f9aee60e0
ms.sourcegitcommit: a209c9f86a7b4340a426c4cfed2d36a388c71124
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/15/2022
ms.locfileid: "66797918"
---
# <a name="fileprofile"></a>FileProfile()

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**ينطبق على:**
- Microsoft 365 Defender

`FileProfile()` الوظيفة هي دالة إثراء في [التتبع المتقدم](advanced-hunting-overview.md) الذي يضيف البيانات التالية إلى الملفات التي عثر عليها الاستعلام.

| العمود | نوع البيانات | الوصف |
|------------|---------------|-------------|
| `SHA1` | `string` | SHA-1 من الملف الذي تم تطبيق الإجراء المسجل عليه |
| `SHA256` | `string` | SHA-256 من الملف الذي تم تطبيق الإجراء المسجل عليه |
| `MD5` | `string` | تجزئة MD5 للملف الذي تم تطبيق الإجراء المسجل عليه |
| `FileSize` | `int` | حجم الملف بالبايت |
| `GlobalPrevalence` | `int` | عدد مثيلات الكيان الذي لاحظته Microsoft عالميا |
| `GlobalFirstSeen` | `datetime` | التاريخ والوقت الذي تمت فيه ملاحظة الكيان لأول مرة من قبل Microsoft على مستوى العالم |
| `GlobalLastSeen` | `datetime` | التاريخ والوقت الذي تمت فيه آخر ملاحظة للكيان من قبل Microsoft على مستوى العالم |
| `Signer` | `string` | معلومات حول موقع الملف |
| `Issuer` | `string` | معلومات حول المرجع المصدق المصدر (CA) |
| `SignerHash` | `string` | قيمة تجزئة فريدة تحدد الموقع |
| `IsCertificateValid` | `boolean` | ما إذا كانت الشهادة المستخدمة لتوقيع الملف صالحة |
| `IsRootSignerMicrosoft` | `boolean` | الإشارة إلى ما إذا كان موقع الشهادة الجذر هو Microsoft وأن الملف مضمن في نظام التشغيل Windows |
| `SignatureState` | `string` | حالة توقيع الملف: SignedValid - الملف موقع بتوقيع صالح، SignedInvalid - الملف موقع ولكن الشهادة غير صحيحة، غير موقعة - الملف غير موقع، غير معروف - لا يمكن استرداد معلومات حول الملف
| `IsExecutable` | `boolean` | ما إذا كان الملف ملف Portable Executable (PE) |
| `ThreatName` | `string` | اسم الكشف عن أي برامج ضارة أو تهديدات أخرى تم العثور عليها |
| `Publisher` | `string` | اسم المؤسسة التي نشرت الملف |
| `SoftwareName` | `string` | اسم منتج البرنامج |

## <a name="syntax"></a>بناء الجمله

```kusto
invoke FileProfile(x,y)
```

## <a name="arguments"></a>الحجج

- **x**— يستخدم عمود معرف الملف المراد استخدامه: `SHA1`أو `SHA256`أو `InitiatingProcessSHA1``InitiatingProcessSHA256`; الدالة `SHA1` إذا لم يتم تحديدها
- **y** - حد لعدد السجلات المراد إثراءها، 1-1000؛ تستخدم الدالة 100 إذا لم تكن محددة


>[!TIP]
> ستعرض وظائف الإثراء معلومات تكميلية فقط عند توفرها. إن توفر المعلومات متنوع ويعتمد على الكثير من العوامل. تأكد من مراعاة هذا عند استخدام FileProfile() في الاستعلامات أو في إنشاء عمليات الكشف المخصصة. للحصول على أفضل النتائج، نوصي باستخدام الدالة FileProfile() مع SHA1.

## <a name="examples"></a>أمثلة

### <a name="project-only-the-sha1-column-and-enrich-it"></a>عرض عمود SHA1 فقط وإثرائه

```kusto
DeviceFileEvents
| where isnotempty(SHA1) and Timestamp > ago(1d)
| take 10
| project SHA1
| invoke FileProfile()
```

### <a name="enrich-the-first-500-records-and-list-low-prevalence-files"></a>إثراء أول 500 سجل وسرد ملفات الانتشار المنخفض

```kusto
DeviceFileEvents
| where ActionType == "FileCreated" and Timestamp > ago(1d)
| project CreatedOn = Timestamp, FileName, FolderPath, SHA1
| invoke FileProfile("SHA1", 500) 
| where GlobalPrevalence < 15
```

## <a name="related-topics"></a>المواضيع ذات الصلة
- [نظرة عامة متقدمة حول الصيد](advanced-hunting-overview.md)
- [التعرّف على لغة الاستعلام](advanced-hunting-query-language.md)
- [فهم المخطط](advanced-hunting-schema-tables.md)
- [الحصول على المزيد من أمثلة الاستعلام](advanced-hunting-shared-queries.md)
