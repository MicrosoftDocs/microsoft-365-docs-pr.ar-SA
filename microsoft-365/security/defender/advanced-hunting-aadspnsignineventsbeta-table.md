---
title: جدول AADSpnSignInEventsBeta في مخطط الصيد المتقدم
description: تعرف على المعلومات المقترنة ب جدول أحداث تسجيل الدخول إلى خدمة Azure Active Directory الرئيسية والمدارة.
keywords: الصيد المتقدم، وصيد التهديدات، والصيد عبر الإنترنت، و Microsoft 365 Defender، و microsoft 365، و m365، و البحث، و الاستعلام، و بيانات التعقب، و مرجع المخطط، و kusto، و الجدول، و العمود، و نوع البيانات، و الوصف، و AlertInfo، و التنبيه، و الكيانات، و الدليل، و ملف، عنوان IP، الجهاز، الجهاز، المستخدم، الحساب، الهوية، AAD (دليل Azure النشط)
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
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: m365d
ms.openlocfilehash: 77cf2d7b74dfc4ccea88661642579f5244e14089
ms.sourcegitcommit: dd6514ae173f1c821d4ec25298145df6cb232e2e
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 01/19/2022
ms.locfileid: "63570415"
---
# <a name="aadspnsignineventsbeta"></a>AADSpnSignInEventsBeta

**ينطبق على:**
- Microsoft 365 Defender

> [!IMPORTANT]
> الجدول `AADSpnSignInEventsBeta` حاليا في الإصدار بيتا، وهو يتم تقديمه على أساس قصير المدى للسماح لك بالتعقب عبر أحداث تسجيل الدخول إلى Azure Active Directory (AAD (دليل Azure النشط)) . يحتاج العملاء إلى ترخيص Azure Active Directory Premium P2 لتجميع الأنشطة لهذا الجدول وعرضها. ستقوم Microsoft في النهاية بنقل كل معلومات مخطط تسجيل الدخول إلى `IdentityLogonEvents` الجدول.

يحتوي `AADSpnSignInEventsBeta` الجدول في مخطط الصيد المتقدم على معلومات حول بيانات تسجيل الدخول الرئيسية لخدمة Azure Active Directory والهوية المدارة. يمكنك معرفة المزيد حول الأنواع المختلفة من تسجيلات الدخول في تقارير نشاط تسجيل الدخول إلى [Azure Active Directory - معاينة](/azure/active-directory/reports-monitoring/concept-all-sign-ins).

استخدم هذا المرجع لإنشاء استعلامات ترجع معلومات من الجدول.

للحصول على معلومات حول الجداول الأخرى في مخطط الصيد المتقدم، راجع [مرجع الصيد المتقدم](/windows/security/threat-protection/microsoft-defender-atp/advanced-hunting-reference).

<br>

****

|اسم العمود|نوع البيانات|الوصف|
|---|---|---|
|`Timestamp`|`datetime`|التاريخ والوقت الذي تم فيه إنشاء السجل|
|`Application`|`string`|التطبيق الذي ينفذ الإجراء المسجل|
|`ApplicationId`|`string`|معرف فريد للتطبيق|
|`IsManagedIdentity`|`boolean`|تشير إلى ما إذا كان تسجيل الدخول قد بدأ بواسطة هوية مدارة|
|`ErrorCode`|`int`|يحتوي على رمز الخطأ إذا حدث خطأ في تسجيل الدخول. للعثور على وصف لرمز خطأ معين، تفضل بزيارة <https://aka.ms/AADsigninsErrorCodes>.|
|`CorrelationId`|`string`|معرف فريد لحدث تسجيل الدخول|
|`ServicePrincipalName`|`string`|اسم الخدمة الأساسية التي بدأت تسجيل الدخول|
|`ServicePrincipalId`|`string`|معرف فريد لمعرف الخدمة الأساسي الذي بدأ تسجيل الدخول|
|`ResourceDisplayName`|`string`|اسم العرض للمورد الذي تم الوصول إليه|
|`ResourceId`|`string`|معرف فريد للمورد الذي تم الوصول إليه|
|`ResourceTenantId`|`string`|معرف فريد لمستأجر المورد الذي تم الوصول إليه|
|`IPAddress`|`string`|عنوان IP المعين إلى نقطة النهاية والمستخدم أثناء اتصالات الشبكة ذات الصلة|
|`Country`|`string`|رمز من حرفين يشير إلى البلد حيث تم تحديد الموقع الجغرافي لرسالة عنوان IP للعميل|
|`State`|`string`|الحالة التي حدثت فيها عملية تسجيل الدخول، إذا كانت متوفرة|
|`City`|`string`|المدينة حيث يوجد مستخدم الحساب|
|`Latitude`|`string`|الإحداثيات من الشمال إلى الجنوب لموقع تسجيل الدخول|
|`Longitude`|`string`|إحداثيات من الشرق إلى الغرب لموقع تسجيل الدخول|
|`RequestId`|`string`|معرف فريد للطلب|
|`ReportId`|`string`|معرف فريد للحدث|
||||

## <a name="related-articles"></a>المقالات ذات الصلة

- [AADSignInEventsBeta](./advanced-hunting-aadsignineventsbeta-table.md)
- [نظرة عامة متقدمة حول الصيد](/windows/security/threat-protection/microsoft-defender-atp/advanced-hunting-overview)
- [تعرف على لغة الاستعلام](/windows/security/threat-protection/microsoft-defender-atp/advanced-hunting-query-language)
- [فهم المخطط](/windows/security/threat-protection/microsoft-defender-atp/advanced-hunting-schema-reference)
