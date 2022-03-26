---
title: جدول AADSignInEventsBeta في مخطط الصيد المتقدم
description: تعرف على جدول أحداث تسجيل الدخول إلى Azure Active Directory في مخطط الصيد المتقدم
keywords: الصيد المتقدم، وصيد التهديدات، والصيد عبر الإنترنت، و Microsoft 365 Defender، و microsoft 365، و m365، و البحث، و الاستعلام، و بيانات التعقب، و مرجع المخطط، و kusto، و الجدول، و العمود، و نوع البيانات، و الوصف، و الملف، عنوان IP، الجهاز، الجهاز، المستخدم، الحساب، الهوية، AAD (دليل Azure النشط)
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
ms.openlocfilehash: dad3ea9fe4297d93864032130e3f6d6b5f6e4e82
ms.sourcegitcommit: dd6514ae173f1c821d4ec25298145df6cb232e2e
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 01/19/2022
ms.locfileid: "63573294"
---
# <a name="aadsignineventsbeta"></a>AADSignInEventsBeta

**ينطبق على:**

- Microsoft 365 Defender

> [!IMPORTANT]
> الجدول `AADSignInEventsBeta` حاليا في الإصدار بيتا، وهو يتم تقديمه على أساس قصير المدى للسماح لك بالتعقب عبر أحداث تسجيل الدخول إلى Azure Active Directory (AAD (دليل Azure النشط)) . يحتاج العملاء إلى ترخيص Azure Active Directory Premium P2 لتجميع الأنشطة لهذا الجدول وعرضها. ستنتقل كل معلومات مخطط تسجيل الدخول في النهاية إلى `IdentityLogonEvents` الجدول.

يحتوي `AADSignInEventsBeta` الجدول في مخطط الصيد المتقدم على معلومات حول تسجيل الدخول التفاعلي وغير التفاعلي ل Azure Active Directory. تعرف على المزيد حول تسجيل الدخول في تقارير نشاط تسجيل الدخول إلى [Azure Active Directory - معاينة](/azure/active-directory/reports-monitoring/concept-all-sign-ins).

استخدم هذا المرجع لإنشاء استعلامات ترجع معلومات من الجدول. للحصول على معلومات حول الجداول الأخرى في مخطط الصيد المتقدم، راجع [مرجع الصيد المتقدم](/windows/security/threat-protection/microsoft-defender-atp/advanced-hunting-reference).

<br>

****

|اسم العمود|نوع البيانات|الوصف|
|---|---|---|
|`Timestamp`|`datetime`|التاريخ والوقت الذي تم فيه إنشاء السجل|
|`Application`|`string`|التطبيق الذي ينفذ الإجراء المسجل|
|`ApplicationId`|`string`|معرف فريد للتطبيق|
|`LogonType`|`string`|نوع جلسة تسجيل الوصول وتفاعلية وتفاعلية عن بعد (RDP) وشبكة دفعات وخدمة|
|`ErrorCode`|`int`|يحتوي على رمز الخطأ إذا حدث خطأ في تسجيل الدخول. للعثور على وصف لرمز خطأ معين، تفضل بزيارة <https://aka.ms/AADsigninsErrorCodes>.|
|`CorrelationId`|`string`|معرف فريد لحدث تسجيل الدخول|
|`SessionId`|`string`|رقم فريد تم تعيينه إلى مستخدم بواسطة خادم موقع ويب أثناء الزيارة أو جلسة العمل|
|`AccountDisplayName`|`string`|اسم مستخدم الحساب المعروض في دفتر العنوان. عادة ما تكون تركيبة من اسم معين أو أول واسم أولي وسطي واسم عائلة أو اسم عائلة.|
|`AccountObjectId`|`string`|معرف فريد للحساب في Azure AD|
|`AccountUpn`|`string`|اسم المستخدم الأساسي (UPN) للحساب|
|`IsExternalUser`|`int`|تشير إلى ما إذا كان المستخدم الذي قام تسجيل الدخول خارجيا. القيم المحتملة: -1 (غير مجموعة)، 0 (ليس خارجيا)، 1 (خارجي).|
|`IsGuestUser`|`boolean`|تشير إلى ما إذا كان المستخدم الذي سجل الدخول ضيفا في المستأجر|
|`AlternateSignInName`|`string`|اسم المستخدم الأساسي المحلي (UPN) للمستخدم الذي يقوم تسجيل الدخول إلى Azure AD|
|`LastPasswordChangeTimestamp`|`datetime`|التاريخ والوقت الذي قام فيه المستخدم الذي قام آخر تغيير لكلمة المرور الخاصة به|
|`ResourceDisplayName`|`string`|اسم العرض للمورد الذي تم الوصول إليه|
|`ResourceId`|`string`|معرف فريد للمورد الذي تم الوصول إليه|
|`ResourceTenantId`|`string`|معرف فريد لمستأجر المورد الذي تم الوصول إليه|
|`DeviceName`|`string`|اسم المجال المؤهل بالكامل (FQDN) للجهاز|
|`AadDeviceId`|`string`|معرف فريد للجهاز في Azure AD|
|`OSPlatform`|`string`|النظام الأساسي لنظام التشغيل الذي يعمل على الجهاز. تشير إلى أنظمة تشغيل محددة، بما في ذلك تباينات داخل العائلة نفسها، مثل Windows 11 و Windows 10 و Windows 7.|
|`DeviceTrustType`|`string`|تشير إلى نوع الثقة للجهاز الذي تم فيه الدخول. لسيناريوهات الجهاز المدار فقط. القيم المحتملة هي Workplace و AzureAd و ServerAd.|
|`IsManaged`|`int`|تشير إلى ما إذا كان الجهاز الذي بدأ تسجيل الدخول جهازا مدارا (1) أم لا جهازا مدارا (0)|
|`IsCompliant`|`int`|تشير إلى ما إذا كان الجهاز الذي بدأ تسجيل الدخول متوافقا (1) أو غير متوافق (0)|
|`AuthenticationProcessingDetails`|`string`|تفاصيل حول معالج المصادقة|
|`AuthenticationRequirement`|`string`|نوع المصادقة المطلوبة لعملية تسجيل الدخول. القيم المحتملة: تعددFactorAuthentication (MFA كان مطلوبا) و SingleFactorAuthentication (لم تكن هناك حاجة إلى MFA).|
|`TokenIssuerType`|`int`|تشير إلى ما إذا كان مصدر الرمز المميز Azure Active Directory (0) أو خدمات اتحاد Active Directory (1)|
|`RiskLevelAggregated`|`int`|مستوى المخاطر المجمع أثناء تسجيل الدخول. القيم المحتملة: 0 (مستوى المخاطر المجمع غير معين) أو 1 (بلا) أو 10 (منخفض) أو 50 (متوسطة) أو 100 (عالية).|
|`RiskDetails`|`int`|تفاصيل حول الحالة الخطره للمستخدم الذي قام تسجيل الدخول|
|`RiskState`|`int`|تشير إلى حالة المستخدم الخطر. القيم المحتملة: 0 (بلا) أو 1 (تم تأكيد الأمان) أو 2 (تم المعالجة) أو 3 (مستبعد) أو 4 (معرضة للمخاطر) أو 5 (تم تأكيد اختراقها).|
|`UserAgent`|`string`|معلومات وكيل المستخدم من مستعرض الويب أو تطبيق عميل آخر|
|`ClientAppUsed`|`string`|تشير إلى تطبيق العميل المستخدم|
|`Browser`|`string`|تفاصيل حول إصدار المستعرض المستخدم في تسجيل الدخول|
|`ConditionalAccessPolicies`|`string`|تفاصيل سياسات الوصول الشرطي المطبقة على حدث تسجيل الدخول|
|`ConditionalAccessStatus`|`int`|حالة سياسات الوصول الشرطي المطبقة على تسجيل الدخول. القيم المحتملة هي 0 (تم تطبيق سياسات)، أو 1 (فشلت محاولة تطبيق سياسات)، أو 2 (لم يتم تطبيق سياسات).|
|`IPAddress`|`string`|عنوان IP المعين إلى نقطة النهاية والمستخدم أثناء اتصالات الشبكة ذات الصلة|
|`Country`|`string`|رمز من حرفين يشير إلى البلد حيث تم تحديد الموقع الجغرافي لرسالة عنوان IP للعميل|
|`State`|`string`|الحالة التي حدثت فيها عملية تسجيل الدخول، إذا كانت متوفرة|
|`City`|`string`|المدينة حيث يوجد مستخدم الحساب|
|`Latitude`|`string`|الإحداثيات من الشمال إلى الجنوب لموقع تسجيل الدخول|
|`Longitude`|`string`|إحداثيات من الشرق إلى الغرب لموقع تسجيل الدخول|
|`NetworkLocationDetails`|`string`|تفاصيل موقع الشبكة لمعالج المصادقة لحدث تسجيل الدخول|
|`RequestId`|`string`|معرف فريد للطلب|
|`ReportId`|`string`|معرف فريد للحدث|

## <a name="related-articles"></a>المقالات ذات الصلة

- [AADSpnSignInEventsBeta](./advanced-hunting-aadspnsignineventsbeta-table.md)
- [نظرة عامة متقدمة حول الصيد](/windows/security/threat-protection/microsoft-defender-atp/advanced-hunting-overview)
- [تعرف على لغة الاستعلام](/windows/security/threat-protection/microsoft-defender-atp/advanced-hunting-query-language)
- [فهم المخطط](/windows/security/threat-protection/microsoft-defender-atp/advanced-hunting-schema-reference)
