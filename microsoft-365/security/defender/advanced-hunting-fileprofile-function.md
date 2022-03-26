---
title: FileProfile() (الدالة FileProfile() في عملية البحث المتقدم Microsoft 365 Defender
description: تعرف على كيفية استخدام FileProfile() لإثراء المعلومات حول الملفات في نتائج استعلام البحث المتقدم
keywords: الصيد المتقدم، وصيد التهديدات، والصيد عبر الإنترنت، Microsoft 365 Defender، microsoft 365، m365، البحث، الاستعلام، بيانات التعقب، مرجع المخطط، kusto، FileProfile، ملف تعريف الملف، الدالة، الإثراء
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
ms.openlocfilehash: 2cd8c91717af8390160bf45a625ae3a3044ee387
ms.sourcegitcommit: 6dcc3b039e0f0b9bae17c386f14ed2b577b453a6
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 12/15/2021
ms.locfileid: "63570381"
---
# <a name="fileprofile"></a>FileProfile()

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**ينطبق على:**
- Microsoft 365 Defender

الدالة `FileProfile()` هي دالة إثراء في [البحث](advanced-hunting-overview.md) المتقدم تضيف البيانات التالية إلى الملفات التي عثر عليها الاستعلام.

| عمود | نوع البيانات | الوصف |
|------------|---------------|-------------|
| `SHA1` | `string` | SHA-1 للملف الذي تم تطبيق الإجراء المسجل عليه |
| `SHA256` | `string` | SHA-256 للملف الذي تم تطبيق الإجراء المسجل عليه |
| `MD5` | `string` | MD5 من الملف الذي تم تطبيق الإجراء المسجل عليه |
| `FileSize` | `int` | حجم الملف بالبايت |
| `GlobalPrevalence` | `int` | عدد مثيلات الكيان الذي لاحظته Microsoft بشكل عام |
| `GlobalFirstSeen` | `datetime` | التاريخ والوقت الذي راقبت فيه Microsoft الكيان للمرة الأولى على مستوى العالم |
| `GlobalLastSeen` | `datetime` | تاريخ وتاريخ آخر مراقبة للكيان من قبل Microsoft على مستوى العالم |
| `Signer` | `string` | معلومات حول توقيع الملف |
| `Issuer` | `string` | معلومات حول المرجع المشهادات المصدر (CA) |
| `SignerHash` | `string` | قيمة هاش فريدة تحدد موقع |
| `IsCertificateValid` | `boolean` | ما إذا كانت الشهادة المستخدمة لتوقيع الملف صالحة |
| `IsRootSignerMicrosoft` | `boolean` | تشير إلى ما إذا كان موقع الشهادة الجذر هو Microsoft |
| `SignatureState` | `string` | حالة توقيع الملف: SignedValid - تم توقيع الملف بتوقيع صالح، SignedInvalid - تم توقيع الملف ولكن الشهادة غير صالحة، غير موقعة - الملف غير موقع، غير معروف - لا يمكن استرداد معلومات حول الملف
| `IsExecutable` | `boolean` | ما إذا كان الملف ملف Portable Executable (PE) |
| `ThreatName` | `string` | اسم الكشف عن أي برامج ضارة أو تهديدات أخرى تم العثور عليها |
| `Publisher` | `string` | اسم المؤسسة التي نشرت الملف |
| `SoftwareName` | `string` | اسم منتج البرنامج |

## <a name="syntax"></a>بناء الجملة

```kusto
invoke FileProfile(x,y)
```

## <a name="arguments"></a>الوسيطات

- **x-عمود** "ملف الم ID" لاستخدامه: `SHA1`أو أو `SHA256`أو `InitiatingProcessSHA1`أو `InitiatingProcessSHA256`; تستخدم الدالة `SHA1` إذا لم يكن محددا
- **y**— الحد لعدد السجلات التي تريد إثراءها، 1-1000؛ تستخدم الدالة 100 إذا لم يكن محددا


>[!TIP]
> لن تظهر دالات الإثراء المعلومات التكميلية إلا عندما تكون متوفرة. يختلف توفر المعلومات ويعتمد على العديد من العوامل. تأكد من وضع هذا في الاعتبار عند استخدام FileProfile() في الاستعلامات أو عند إنشاء اكتشافات مخصصة. للحصول على أفضل النتائج، نوصي باستخدام الدالة FileProfile() مع SHA1.

## <a name="examples"></a>أمثلة

### <a name="project-only-the-sha1-column-and-enrich-it"></a>Project عمود SHA1 فقط وإثراءه

```kusto
DeviceFileEvents
| where isnotempty(SHA1) and Timestamp > ago(1d)
| take 10
| project SHA1
| invoke FileProfile()
```

### <a name="enrich-the-first-500-records-and-list-low-prevalence-files"></a>إثراء أول 500 سجل وقائمة ملفات منخفضة المستوى

```kusto
DeviceFileEvents
| where ActionType == "FileCreated" and Timestamp > ago(1d)
| project CreatedOn = Timestamp, FileName, FolderPath, SHA1
| invoke FileProfile("SHA1", 500) 
| where GlobalPrevalence < 15
```

## <a name="related-topics"></a>المواضيع ذات الصلة
- [نظرة عامة متقدمة حول الصيد](advanced-hunting-overview.md)
- [تعرف على لغة الاستعلام](advanced-hunting-query-language.md)
- [فهم المخطط](advanced-hunting-schema-tables.md)
- [الحصول على مزيد من أمثلة الاستعلام](advanced-hunting-shared-queries.md)
