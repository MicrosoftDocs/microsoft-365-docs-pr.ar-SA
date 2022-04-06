---
title: IdentityQueryEvents table في مخطط الصيد المتقدم
description: تعرف على أحداث استعلام Active Directory في جدول IdentityQueryEvents في مخطط الصيد المتقدم
keywords: الصيد المتقدم، وصيد التهديدات، والصيد عبر الإنترنت، و Microsoft 365 Defender، و Microsoft 365، و m365، و البحث، و الاستعلام، و بيانات التعقب، و مرجع المخطط، و kusto، و الجدول، العمود، نوع البيانات، الوصف، IdentityQueryEvents، Azure AD، Active Directory، Microsoft Defender for Identity، الهويات، استعلامات LDAP
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
ms.openlocfilehash: 0b3c98b629d8984b984af3f3dba25a65ab7671e6
ms.sourcegitcommit: 6dcc3b039e0f0b9bae17c386f14ed2b577b453a6
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 12/15/2021
ms.locfileid: "63583189"
---
# <a name="identityqueryevents"></a>IdentityQueryEvents

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**ينطبق على:**
- Microsoft 365 Defender

يحتوي `IdentityQueryEvents` الجدول في [مخطط](advanced-hunting-overview.md) الصيد المتقدم على معلومات حول الاستعلامات التي يتم تنفيذها مقابل كائنات Active Directory، مثل المستخدمين والمجموعات والأجهزة والمجالات. استخدم هذا المرجع لإنشاء استعلامات ترجع معلومات من هذا الجدول.

>[!TIP]
> للحصول على معلومات مفصلة حول أنواع الأحداث (`ActionType` القيم) المعتمدة بواسطة جدول، استخدم مرجع المخطط المضمن المتوفر في Defender for Cloud.

للحصول على معلومات حول الجداول الأخرى في مخطط الصيد المتقدم، [راجع مرجع الصيد المتقدم](advanced-hunting-schema-tables.md).

| اسم العمود | نوع البيانات | الوصف |
|-------------|-----------|-------------|
| `Timestamp` | `datetime` | التاريخ والوقت الذي تم فيه تسجيل الحدث |
| `ActionType` | `string` | نوع النشاط الذي تم تشغيل الحدث به. راجع [مرجع المخطط داخل المدخل](advanced-hunting-schema-tables.md?#get-schema-information-in-the-security-center) للحصول على التفاصيل |
| `Application` | `string` | التطبيق الذي ينفذ الإجراء المسجل |
| `QueryType` | `string` | نوع الاستعلام، مثل QueryGroup أو QueryUser أو EnumerateUsers |
| `QueryTarget` | `string` | اسم المستخدم أو المجموعة أو الجهاز أو المجال أو أي نوع كيان آخر يتم الاستعلام فيه |
| `Query` | `string` | سلسلة مستخدمة لتشغيل الاستعلام |
| `Protocol` | `string` | البروتوكول المستخدم أثناء الاتصال |
| `AccountName` | `string` | اسم المستخدم للحساب |
| `AccountDomain` | `string` | مجال الحساب |
| `AccountUpn` | `string` | اسم المستخدم الأساسي (UPN) للحساب |
| `AccountSid` | `string` | معرف الأمان (SID) للحساب |
| `AccountObjectId` | `string` | معرف فريد للحساب في Azure AD |
| `AccountDisplayName` | `string` | اسم مستخدم الحساب المعروض في دفتر العنوان. عادة ما تكون تركيبة من اسم معين أو أول، وابتداء وسطي، واسم عائلة أو اسم عائلة. |
| `DeviceName` | `string` | اسم المجال المؤهل بالكامل (FQDN) لنقطة النهاية |
| `IPAddress` | `string` | عنوان IP المعين إلى نقطة النهاية والمستخدم أثناء اتصالات الشبكة ذات الصلة |
| `Port` | `string` | منفذ TCP المستخدم أثناء الاتصال |
| `DestinationDeviceName` | `string` | اسم الجهاز الذي يعمل على تشغيل تطبيق الخادم الذي يعالج الإجراء المسجل |
| `DestinationIPAddress` | `string` | عنوان IP للجهاز الذي يعمل على تشغيل تطبيق الخادم الذي يعالج الإجراء المسجل |
| `DestinationPort` | `string` | منفذ الوجهة لاتصالات الشبكة ذات الصلة |
| `TargetDeviceName` | `string` | اسم المجال المؤهل بالكامل (FQDN) للجهاز الذي تم تطبيق الإجراء المسجل عليه |
| `TargetAccountUpn` | `string` | اسم المستخدم الأساسي (UPN) للحساب الذي تم تطبيق الإجراء المسجل عليه |
| `TargetAccountDisplayName` | `string` | اسم العرض للحساب الذي تم تطبيق الإجراء المسجل عليه |
| `Location` | `string` | المدينة أو البلد أو أي موقع جغرافي آخر مقترن بالحدث |
| `ReportId` | `long` | معرف فريد للحدث |
| `AdditionalFields` | `string` | معلومات إضافية حول الكيان أو الحدث |

## <a name="related-topics"></a>المواضيع ذات الصلة
- [نظرة عامة متقدمة حول الصيد](advanced-hunting-overview.md)
- [تعرف على لغة الاستعلام](advanced-hunting-query-language.md)
- [استخدام الاستعلامات المشتركة](advanced-hunting-shared-queries.md)
- [البحث عبر الأجهزة ورسائل البريد الإلكتروني والتطبيقات والهويات](advanced-hunting-query-emails-devices.md)
- [فهم المخطط](advanced-hunting-schema-tables.md)
- [تطبيق أفضل ممارسات الاستعلام](advanced-hunting-best-practices.md)
