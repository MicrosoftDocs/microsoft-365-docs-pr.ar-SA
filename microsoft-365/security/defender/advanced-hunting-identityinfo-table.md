---
title: جدول IdentityInfo في مخطط الصيد المتقدم
description: تعرف على معلومات حساب المستخدم في جدول IdentityInfo في مخطط الصيد المتقدم
keywords: الصيد المتقدم، وصيد التهديدات، والصيد عبر الإنترنت، Microsoft 365 Defender، microsoft 365، m365، البحث، الاستعلام، بيانات التعقب، مرجع المخطط، kusto، جدول، عمود، نوع البيانات، الوصف، AccountInfo، IdentityInfo، حساب
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
ms.openlocfilehash: b09d1774ab35dbca9119deb98864d6c6f78051a9
ms.sourcegitcommit: 6dcc3b039e0f0b9bae17c386f14ed2b577b453a6
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 12/15/2021
ms.locfileid: "63571485"
---
# <a name="identityinfo"></a>IdentityInfo

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**ينطبق على:**
- Microsoft 365 Defender

يحتوي `IdentityInfo` الجدول في [مخطط](advanced-hunting-overview.md) الصيد المتقدم على معلومات حول حسابات المستخدمين التي تم الحصول عليها من خدمات مختلفة، بما في ذلك Azure Active Directory. استخدم هذا المرجع لإنشاء استعلامات ترجع معلومات من هذا الجدول.

>[!NOTE]
>تمت إعادة تسمية هذا الجدول من `AccountInfo`. أثناء إعادة التسمية، يتم تحديث كل الاستعلامات المحفوظة في المدخل تلقائيا. تحقق من الاستعلامات التي حفظتها في مكان آخر.

للحصول على معلومات حول الجداول الأخرى في مخطط الصيد المتقدم، [راجع مرجع الصيد المتقدم](advanced-hunting-schema-tables.md).

| اسم العمود | نوع البيانات | الوصف |
|-------------|-----------|-------------|
| `AccountObjectId` | `string` | معرف فريد للحساب في Azure AD |
| `AccountUpn` | `string` | اسم المستخدم الأساسي (UPN) للحساب |
| `OnPremSid` | `string` | معرف الأمان المحلي (SID) للحساب |
| `CloudSid` | `string` | معرف الأمان السحابي للحساب |
| `GivenName` | `string` | الاسم أو الاسم الأول لمستخدم الحساب |
| `Surname` | `string` | اسم العائلة أو اسم العائلة أو اسم العائلة لمستخدم الحساب |
| `AccountDisplayName` | `string` | اسم مستخدم الحساب المعروض في دفتر العنوان. عادة ما تكون تركيبة من اسم معين أو أول، وابتداء وسطي، واسم عائلة أو اسم عائلة. |
| `Department` | `string` | اسم القسم الذي ينتمي إليه مستخدم الحساب |
| `JobTitle` | `string` | الملقب الوظيفي لمستخدم الحساب |
| `AccountName` | `string` | اسم المستخدم للحساب |
| `AccountDomain` | `string` | مجال الحساب |
| `EmailAddress` | `string` | عنوان SMTP للحساب |
| `SipProxyAddress` | `string` | عنوان بروتوكول بدء جلسة عمل الصوت عبر IP (VOIP) للحساب |
| `City` | `string` | المدينة حيث يوجد مستخدم الحساب |
| `Country` | `string` | البلد/المنطقة حيث يوجد مستخدم الحساب |
| `IsAccountEnabled` | `boolean` | تشير إلى ما إذا كان الحساب تم تمكينه أم لا |

## <a name="related-topics"></a>المواضيع ذات الصلة
- [نظرة عامة متقدمة حول الصيد](advanced-hunting-overview.md)
- [تعرف على لغة الاستعلام](advanced-hunting-query-language.md)
- [استخدام الاستعلامات المشتركة](advanced-hunting-shared-queries.md)
- [البحث عبر الأجهزة ورسائل البريد الإلكتروني والتطبيقات والهويات](advanced-hunting-query-emails-devices.md)
- [فهم المخطط](advanced-hunting-schema-tables.md)
- [تطبيق أفضل ممارسات الاستعلام](advanced-hunting-best-practices.md)
