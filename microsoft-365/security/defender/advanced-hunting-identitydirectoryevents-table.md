---
title: IdentityDirectoryEvents table في مخطط الصيد المتقدم
description: التعرف على وحدة التحكم بالمجال والأحداث في Active Directory في جدول IdentityDirectoryEvents في مخطط الصيد المتقدم
keywords: الصيد المتقدم، وصيد التهديدات، والصيد عبر الإنترنت، و Microsoft 365 Defender، و microsoft 365، و m365، و البحث، و الاستعلام، و بيانات التعقب، و مرجع المخطط، و kusto، و الجدول، و العمود، و نوع البيانات، و الوصف، و IdentityDirectoryEvents، وحدة التحكم بالمجال، Active Directory، Microsoft Defender for Identity، الهويات
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
ms.openlocfilehash: b7d880e0865ebeaf09e40fc543abba37566d2081
ms.sourcegitcommit: 6dcc3b039e0f0b9bae17c386f14ed2b577b453a6
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 12/15/2021
ms.locfileid: "63573402"
---
# <a name="identitydirectoryevents"></a>IdentityDirectoryEvents

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**ينطبق على:**
- Microsoft 365 Defender

يحتوي `IdentityDirectoryEvents` الجدول في [مخطط](advanced-hunting-overview.md) الصيد المتقدم على أحداث تتضمن وحدة تحكم مجال في الموقع المحلي تقوم بتشغيل Active Directory (AD). يلتقط هذا الجدول أحداثا مختلفة ذات صلة بالهوية، مثل تغييرات كلمة المرور وانتهاء صلاحية كلمة المرور والتغييرات في اسم المستخدم الأساسي (UPN). كما يلتقط أحداث النظام على وحدة التحكم بالمجال، مثل جدولة المهام ونشاط PowerShell. استخدم هذا المرجع لإنشاء استعلامات ترجع معلومات من هذا الجدول.

>[!TIP]
> للحصول على معلومات مفصلة حول أنواع الأحداث (`ActionType` القيم) المعتمدة بواسطة جدول، استخدم مرجع المخطط المضمن المتوفر في Defender for Cloud.

للحصول على معلومات حول الجداول الأخرى في مخطط الصيد المتقدم، [راجع مرجع الصيد المتقدم](advanced-hunting-schema-tables.md).

| اسم العمود | نوع البيانات | الوصف |
|-------------|-----------|-------------|
| `Timestamp` | `datetime` | التاريخ والوقت الذي تم فيه تسجيل الحدث |
| `ActionType` | `string` | نوع النشاط الذي تم تشغيل الحدث به. راجع [مرجع المخطط داخل المدخل](advanced-hunting-schema-tables.md?#get-schema-information-in-the-security-center) للحصول على التفاصيل |
| `Application` | `string` | التطبيق الذي ينفذ الإجراء المسجل |
| `TargetAccountUpn` | `string` | اسم المستخدم الأساسي (UPN) للحساب الذي تم تطبيق الإجراء المسجل عليه |
| `TargetAccountDisplayName` | `string` | اسم العرض للحساب الذي تم تطبيق الإجراء المسجل عليه |
| `TargetDeviceName` | `string` | اسم المجال المؤهل بالكامل (FQDN) للجهاز الذي تم تطبيق الإجراء المسجل عليه |
| `DestinationDeviceName` | `string` | اسم الجهاز الذي يعمل على تشغيل تطبيق الخادم الذي يعالج الإجراء المسجل |
| `DestinationIPAddress` | `string` | عنوان IP للجهاز الذي يعمل على تشغيل تطبيق الخادم الذي يعالج الإجراء المسجل |
| `DestinationPort` | `string` | منفذ وجهة النشاط |
| `Protocol` | `string` | البروتوكول المستخدم أثناء الاتصال |
| `AccountName` | `string` | اسم المستخدم للحساب |
| `AccountDomain` | `string` | مجال الحساب |
| `AccountUpn` | `string` | اسم المستخدم الأساسي (UPN) للحساب |
| `AccountSid` | `string` | معرف الأمان (SID) للحساب |
| `AccountObjectId` | `string` | معرف فريد للحساب في Azure Active Directory |
| `AccountDisplayName` | `string` | اسم مستخدم الحساب المعروض في دفتر العنوان. عادة ما تكون تركيبة من اسم معين أو أول، وابتداء وسطي، واسم عائلة أو اسم عائلة. |
| `DeviceName` | `string` | اسم المجال المؤهل بالكامل (FQDN) للجهاز |
| `IPAddress` | `string` | عنوان IP المعين إلى الجهاز أثناء الاتصال |
| `Port` | `string` | منفذ TCP المستخدم أثناء الاتصال |
| `Location` | `string` | المدينة أو البلد أو أي موقع جغرافي آخر مقترن بالحدث |
| `ISP` | `string` | موفر خدمة الإنترنت المقترن وعنوان IP |
| `ReportId` | `long` | معرف فريد للحدث |
| `AdditionalFields` | `string` | معلومات إضافية حول الكيان أو الحدث |

## <a name="related-topics"></a>المواضيع ذات الصلة
- [نظرة عامة متقدمة حول الصيد](advanced-hunting-overview.md)
- [تعرف على لغة الاستعلام](advanced-hunting-query-language.md)
- [استخدام الاستعلامات المشتركة](advanced-hunting-shared-queries.md)
- [البحث عبر الأجهزة ورسائل البريد الإلكتروني والتطبيقات والهويات](advanced-hunting-query-emails-devices.md)
- [فهم المخطط](advanced-hunting-schema-tables.md)
- [تطبيق أفضل ممارسات الاستعلام](advanced-hunting-best-practices.md)
