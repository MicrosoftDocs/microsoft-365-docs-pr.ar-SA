---
title: IdentityLogonEvents table في مخطط الصيد المتقدم
description: تعرف على أحداث المصادقة التي سجلها Active Directory في جدول IdentityLogonEvents في مخطط الصيد المتقدم
keywords: الصيد المتقدم، وصيد التهديدات، والصيد عبر الإنترنت، و Microsoft 365 Defender، و microsoft 365، و m365، و البحث، و الاستعلام، و بيانات التعقب، و مرجع المخطط، و kusto، و الجدول، و العمود، و نوع البيانات، و الوصف، IdentityLogonEvents، Azure AD، Active Directory، Microsoft Defender for Identity، الهويات
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
ms.openlocfilehash: c5f8de4015ed8b031d3f228f29a6a0d63a57bf2a
ms.sourcegitcommit: 6dcc3b039e0f0b9bae17c386f14ed2b577b453a6
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 12/15/2021
ms.locfileid: "63570520"
---
# <a name="identitylogonevents"></a>IdentityLogonEvents

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**ينطبق على:**
- Microsoft 365 Defender

يحتوي الجدول في مخطط [](advanced-hunting-overview.md) الصيد المتقدم على معلومات حول أنشطة المصادقة التي تم القيام بها من خلال Active Directory المحلية التي تم التقاطها بواسطة أنشطة المصادقة و Microsoft Defender للهوية المتعلقة ب خدمات Microsoft عبر الإنترنت التي تم التقاطها بواسطة Microsoft Defender for Cloud Apps.`IdentityLogonEvents` استخدم هذا المرجع لإنشاء استعلامات ترجع معلومات من هذا الجدول.

>[!TIP]
> للحصول على معلومات مفصلة حول أنواع الأحداث (`ActionType` القيم) المعتمدة بواسطة جدول، استخدم مرجع المخطط المضمن المتوفر في Defender for Cloud.

>[!NOTE]
>يتناول هذا الجدول أنشطة تسجيل الدخول إلى Azure Active Directory (Azure AD) المتعقبة بواسطة Defender for Cloud Apps، خاصة أنشطة تسجيل الدخول والمصادقة التفاعلية باستخدام ActiveSync والبروتوكولات القديمة الأخرى. يمكن عرض تسجيلات الدخول غير التفاعلية غير المتوفرة في هذا الجدول في سجل تدقيق Azure AD. [تعرف على المزيد حول توصيل Defender for Cloud Apps Microsoft 365](/cloud-app-security/connect-office-365-to-microsoft-cloud-app-security)

للحصول على معلومات حول الجداول الأخرى في مخطط الصيد المتقدم، [راجع مرجع الصيد المتقدم](advanced-hunting-schema-tables.md).

| اسم العمود | نوع البيانات | الوصف |
|-------------|-----------|-------------|
| `Timestamp` | `datetime` | التاريخ والوقت الذي تم فيه تسجيل الحدث |
| `ActionType` | `string` | نوع النشاط الذي تم تشغيل الحدث به. راجع [مرجع المخطط داخل المدخل](advanced-hunting-schema-tables.md?#get-schema-information-in-the-security-center) للحصول على التفاصيل |
| `Application` | `string` | التطبيق الذي ينفذ الإجراء المسجل |
| `LogonType` | `string` | نوع جلسة تسجيل تسجيل، على وجه التحديد:<br><br> - **تفاعلي** - يتفاعل المستخدم فعليا مع الجهاز باستخدام لوحة المفاتيح والشاشة المحلية<br><br> - **تسجيلات تسجيل (RDP)** التفاعلية عن بعد - يتفاعل المستخدم مع الجهاز عن بعد باستخدام سطح المكتب البعيد أو خدمات المحطة الطرفية أو المساعدة عن بعد أو عملاء RDP الآخرين<br><br> - **الشبكة** - جلسة العمل التي تبدأ عند الوصول إلى الجهاز باستخدام PsExec أو عند الوصول إلى الموارد المشتركة على الجهاز، كالطابعات والمجلدات المشتركة،<br><br> - **دفعة** - جلسة عمل تبدأ بالمهام المجدولة<br><br> - **الخدمة** - جلسة العمل التي تبدأ بواسطة الخدمات عند بدء تشغيلها |
| `Protocol` | `string` | بروتوكول الشبكة المستخدم |
| `FailureReason` | `string` | معلومات تشرح سبب فشل الإجراء المسجل |
| `AccountName` | `string` | اسم المستخدم للحساب |
| `AccountDomain` | `string` | مجال الحساب |
| `AccountUpn` | `string` | اسم المستخدم الأساسي (UPN) للحساب |
| `AccountSid` | `string` | معرف الأمان (SID) للحساب |
| `AccountObjectId` | `string` | معرف فريد للحساب في Azure AD |
| `AccountDisplayName` | `string` | اسم مستخدم الحساب المعروض في دفتر العنوان. عادة ما تكون تركيبة من اسم معين أو أول، وابتداء وسطي، واسم عائلة أو اسم عائلة. |
| `DeviceName` | `string` | اسم المجال المؤهل بالكامل (FQDN) للجهاز |
| `DeviceType` | `string` | نوع الجهاز |
| `OSPlatform` | `string` | النظام الأساسي لنظام التشغيل الذي يعمل على الجهاز. يشير ذلك إلى أنظمة تشغيل محددة، بما في ذلك تباينات داخل العائلة نفسها، مثل Windows 11 Windows 10 Windows 7. |
| `IPAddress` | `string` | عنوان IP المعين إلى نقطة النهاية والمستخدم أثناء اتصالات الشبكة ذات الصلة |
| `Port` | `string` | منفذ TCP المستخدم أثناء الاتصال |
| `DestinationDeviceName` | `string` | اسم الجهاز الذي يعمل على تشغيل تطبيق الخادم الذي يعالج الإجراء المسجل |
| `DestinationIPAddress` | `string` | عنوان IP للجهاز الذي يعمل على تشغيل تطبيق الخادم الذي يعالج الإجراء المسجل |
| `DestinationPort` | `string` | منفذ الوجهة لاتصالات الشبكة ذات الصلة |
| `TargetDeviceName` | `string` | اسم المجال المؤهل بالكامل (FQDN) للجهاز الذي تم تطبيق الإجراء المسجل عليه |
| `TargetAccountDisplayName` | `string` | اسم العرض للحساب الذي تم تطبيق الإجراء المسجل عليه |
| `Location` | `string` | المدينة أو البلد أو أي موقع جغرافي آخر مقترن بالحدث |
| `Isp` | `string` | موفر خدمة الإنترنت (ISP) المقترن وعنوان IP لنقطة النهاية |
| `ReportId` | `long` | معرف فريد للحدث |
| `AdditionalFields` | `string` | معلومات إضافية حول الكيان أو الحدث |

## <a name="related-topics"></a>المواضيع ذات الصلة
- [نظرة عامة متقدمة حول الصيد](advanced-hunting-overview.md)
- [تعرف على لغة الاستعلام](advanced-hunting-query-language.md)
- [استخدام الاستعلامات المشتركة](advanced-hunting-shared-queries.md)
- [البحث عبر الأجهزة ورسائل البريد الإلكتروني والتطبيقات والهويات](advanced-hunting-query-emails-devices.md)
- [فهم المخطط](advanced-hunting-schema-tables.md)
- [تطبيق أفضل ممارسات الاستعلام](advanced-hunting-best-practices.md)
