---
title: جدول AADSpnSignInEventsBeta في مخطط التتبع المتقدم
description: تعرف على المعلومات المقترنة بكيان خدمة Azure Active Directory وجدول أحداث تسجيل الدخول إلى الهوية المدارة.
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
ms.openlocfilehash: b1b9d6405abdddea42652cfd4c532df91eeb6b30
ms.sourcegitcommit: 7ab324551afac4fd82abc015247371ebfe6ccac2
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 06/02/2022
ms.locfileid: "65842203"
---
# <a name="aadspnsignineventsbeta"></a>AADSpnSignInEventsBeta

**ينطبق على:**
- Microsoft 365 Defender

> [!IMPORTANT]
> الجدول `AADSpnSignInEventsBeta` حاليا في الإصدار بيتا ويتم تقديمه على أساس قصير الأجل للسماح لك بالتتبع من خلال أحداث تسجيل الدخول إلى Azure Active Directory (AAD). يحتاج العملاء إلى ترخيص Azure Active Directory Premium P2 لجمع الأنشطة وعرضها لهذا الجدول. ستقوم Microsoft في النهاية بنقل كافة معلومات مخطط تسجيل الدخول إلى `IdentityLogonEvents` الجدول.

`AADSpnSignInEventsBeta` يحتوي الجدول في مخطط التتبع المتقدم على معلومات حول كيان خدمة Azure Active Directory وتسجيلات الهوية المدارة. يمكنك معرفة المزيد حول الأنواع المختلفة من عمليات تسجيل الدخول في [تقارير نشاط تسجيل الدخول إلى Azure Active Directory - المعاينة](/azure/active-directory/reports-monitoring/concept-all-sign-ins).

استخدم هذا المرجع لإنشاء استعلامات ترجع معلومات من الجدول.

للحصول على معلومات حول الجداول الأخرى في مخطط التتبع المتقدم، راجع [مرجع التتبع المتقدم](/windows/security/threat-protection/microsoft-defender-atp/advanced-hunting-reference).

<br>

****

|اسم العمود|نوع البيانات|الوصف|
|---|---|---|
|`Timestamp`|`datetime`|تاريخ ووقت إنشاء السجل|
|`Application`|`string`|التطبيق الذي نفذ الإجراء المسجل|
|`ApplicationId`|`string`|معرف فريد للتطبيق|
|`IsManagedIdentity`|`boolean`|الإشارة إلى ما إذا كان قد تم بدء تسجيل الدخول بواسطة هوية مدارة|
|`ErrorCode`|`int`|يحتوي على رمز الخطأ في حالة حدوث خطأ في تسجيل الدخول. للعثور على وصف لرمز خطأ معين، تفضل بزيارة <https://aka.ms/AADsigninsErrorCodes>.|
|`CorrelationId`|`string`|معرف فريد لحدث تسجيل الدخول|
|`ServicePrincipalName`|`string`|اسم كيان الخدمة الذي بدأ تسجيل الدخول|
|`ServicePrincipalId`|`string`|معرف فريد لكيان الخدمة الذي بدأ تسجيل الدخول|
|`ResourceDisplayName`|`string`|اسم العرض للمورد الذي تم الوصول إليه|
|`ResourceId`|`string`|معرف فريد للمورد الذي تم الوصول إليه|
|`ResourceTenantId`|`string`|معرف فريد لمستأجر المورد الذي تم الوصول إليه|
|`IPAddress`|`string`|عنوان IP المعين إلى نقطة النهاية والمستخدم أثناء اتصالات الشبكة ذات الصلة|
|`Country`|`string`|رمز مكون من حرفين يشير إلى البلد الذي تم فيه تخصيص عنوان IP للعميل جغرافيا|
|`State`|`string`|الحالة التي حدث فيها تسجيل الدخول، إذا كان متوفرا|
|`City`|`string`|المدينة التي يوجد فيها مستخدم الحساب|
|`Latitude`|`string`|الإحداثيات الشمالية إلى الجنوبية لموقع تسجيل الدخول|
|`Longitude`|`string`|الإحداثيات من الشرق إلى الغرب لموقع تسجيل الدخول|
|`RequestId`|`string`|معرف فريد للطلب|
|`ReportId`|`string`|معرف فريد للحدث|
||||

## <a name="related-articles"></a>المقالات ذات الصلة

- [AADSignInEventsBeta](./advanced-hunting-aadsignineventsbeta-table.md)
- [نظرة عامة متقدمة حول الصيد](/windows/security/threat-protection/microsoft-defender-atp/advanced-hunting-overview)
- [التعرّف على لغة الاستعلام](/windows/security/threat-protection/microsoft-defender-atp/advanced-hunting-query-language)
- [فهم المخطط](/windows/security/threat-protection/microsoft-defender-atp/advanced-hunting-schema-reference)
