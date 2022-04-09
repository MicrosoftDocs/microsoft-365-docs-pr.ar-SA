---
title: أدوار مخصصة للتحكم في الوصول استنادا إلى الدور
description: تعرف على كيفية إدارة الأدوار المخصصة في مدخل Microsoft 365 Defender
keywords: الوصول والأذونات Microsoft 365 Defender وM365 والأمان MCAS أمان التطبيقات على السحابة Microsoft Defender لنقطة النهاية ، النطاق، النطاق، RBAC، الوصول المستند إلى الأدوار، الوصول المخصص المستند إلى الأدوار، المصادقة المستندة إلى الأدوار، RBAC في MDO، الأدوار، مجموعات الأدوار، توريث الأذونات، الأذونات الدقيقة
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: conceptual
search.appverid:
- MOE150
- MET150
ms.technology: m365d
ms.openlocfilehash: 94330e319eeb44618c1e11b27da7b3d63c08d203
ms.sourcegitcommit: 1ef176c79a0e6dbb51834fe30807409d4e94847c
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 11/19/2021
ms.locfileid: "64731340"
---
# <a name="custom-roles-in-role-based-access-control-for-microsoft-365-defender"></a>الأدوار المخصصة في التحكم في الوصول استنادا إلى الدور Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

[!INCLUDE [Prerelease](../includes/prerelease.md)]

**ينطبق على:**

- Microsoft 365 Defender
 
هناك نوعان من الأدوار التي يمكن استخدامها للوصول إلى Microsoft 365 Defender:
- **أدوار Azure Active Directory (AD) العمومية**
- **الأدوار المخصصة**

يمكن إدارة الوصول إلى Microsoft 365 Defender بشكل جماعي باستخدام [الأدوار العمومية في Azure Active Directory (AAD (دليل Azure النشط))](m365d-permissions.md)

إذا كنت بحاجة إلى مرونة أكبر والتحكم في الوصول إلى بيانات منتج معينة، يمكن أيضا إدارة الوصول Microsoft 365 Defender عن طريق إنشاء أدوار مخصصة من خلال كل مدخل أمان خاص.  

على سبيل المثال، سيسمح دور مخصص تم إنشاؤه من خلال Microsoft Defender لنقطة النهاية بالوصول إلى بيانات المنتج ذات الصلة، بما في ذلك بيانات نقطة النهاية داخل مدخل Microsoft 365 Defender. وبالمثل، فإن الدور المخصص الذي تم إنشاؤه من خلال Microsoft Defender لـ Office 365 سيسمح بالوصول إلى بيانات المنتج ذات الصلة، بما في ذلك البريد الإلكتروني & بيانات التعاون داخل مدخل Microsoft 365 Defender.

يمكن للمستخدمين الذين لديهم أدوار مخصصة موجودة الوصول إلى البيانات في مدخل Microsoft 365 Defender وفقا لأذونات حمل العمل الحالية الخاصة بهم دون الحاجة إلى تكوين إضافي.

## <a name="create-and-manage-custom-roles"></a>إنشاء أدوار مخصصة وإدارتها
يمكن إنشاء الأدوار والأذونات المخصصة وإدارتها بشكل فردي من خلال كل من بوابات الأمان التالية: 

- Microsoft Defender لنقطة النهاية – [تحرير الأدوار في Microsoft Defender لنقطة النهاية](../defender-endpoint/user-roles.md)
- Microsoft Defender لـ Office 365 – [الأذونات في مركز توافق & الأمان](../office-365-security/permissions-in-the-security-and-compliance-center.md?preserve-view=true&view=o365-worldwide)
- Microsoft Defender for Cloud Apps – [إدارة وصول المسؤول](/cloud-app-security/manage-admins)

يسمح كل دور مخصص تم إنشاؤه من خلال مدخل فردي بالوصول إلى بيانات مدخل المنتج ذي الصلة. على سبيل المثال، سيسمح دور مخصص تم إنشاؤه من خلال Microsoft Defender لنقطة النهاية بالوصول إلى بيانات Defender لنقطة النهاية فقط.

> [!TIP]
> يمكن أيضا الوصول إلى الأذونات والأدوار من خلال مدخل Microsoft 365 Defender عن طريق تحديد الأذونات & الأدوار من جزء التنقل. تتم إدارة الوصول إلى Microsoft Defender for Cloud Apps من خلال مدخل Defender for Cloud Apps ويتحكم في الوصول إلى Microsoft Defender for Identity أيضا.  راجع [Microsoft Defender for Cloud Apps](/cloud-app-security/manage-admins)

> [!NOTE]
> الأدوار المخصصة التي تم إنشاؤها في Microsoft Defender for Cloud Apps لديها حق الوصول إلى بيانات Microsoft Defender for Identity أيضا. لا يمكن للمستخدمين الذين لديهم مسؤول مجموعة المستخدم أو مسؤول التطبيق/المثيل Microsoft Defender for Cloud Apps الوصول إلى بيانات Microsoft Defender for Cloud Apps من خلال مدخل Microsoft 365 Defender.

## <a name="manage-permissions-and-roles-in-the-microsoft-365-defender-portal"></a>إدارة الأذونات والأدوار في مدخل Microsoft 365 Defender
يمكن أيضا إدارة الأذونات والأدوار في مدخل Microsoft 365 Defender:

1. سجل الدخول إلى مدخل Microsoft 365 Defender في security.microsoft.com.
2. في جزء التنقل، حدد **الأذونات & الأدوار**.
3. ضمن رأس **الأذونات** ، حدد **"Roles**".

> [!NOTE]
> ينطبق هذا فقط على Defender لـ Office 365 و Defender لنقطة النهاية. يجب أن يتم الوصول إلى أحمال العمل الأخرى في بواباتها ذات الصلة.


## <a name="required-roles-and-permissions"></a>الأدوار والأذونات المطلوبة
يوضح الجدول التالي الأدوار والأذونات المطلوبة للوصول إلى كل تجربة موحدة في كل حمل عمل. تشير الأدوار المحددة في الجدول أدناه إلى الأدوار المخصصة في المداخل الفردية وغير متصلة بالأدوار العمومية في Azure AD، حتى لو تمت تسميتها بشكل مماثل.

> [!NOTE]
> تتطلب إدارة الحوادث أذونات إدارة لجميع المنتجات التي تشكل جزءا من الحادث.
 
| **أحد الأدوار التالية مطلوب Microsoft 365 Defender**  | **أحد الأدوار التالية مطلوب ل Defender لنقطة النهاية**  | **أحد الأدوار التالية مطلوب Defender لـ Office 365** | **أحد الأدوار التالية مطلوب ل Defender for Cloud Apps** | 
|---------|---------|---------|---------|
| عرض بيانات التحقيق: <ul><li>صفحة التنبيه</li> <li>قائمة انتظار التنبيهات</li> <li>الأحداث</li>  <li>قائمة انتظار الأحداث</li> <li>مركز الصيانة</li></ul>| عرض عمليات أمان البيانات | <ul><li>إدارة التنبيهات للعرض فقط </li> <li>تكوين المؤسسة</li><li>سجلات التدقيق</li> <li>عرض سجلات التدقيق فقط</li> <li>قارئ الأمان</li> <li>مسؤول الأمان</li><li>عرض المستلمين فقط</li></ul>  | <ul><li>المسؤول العام</li> <li>مسؤول الأمان</li> <li>مسؤول التوافق</li> <li>عامل تشغيل الأمان</li> <li>قارئ الأمان</li> <li>القارئ العمومي</li></ul> |
| عرض بيانات التتبع | عرض عمليات أمان البيانات | <ul><li>قارئ الأمان</li> <li>مسؤول الأمان</li> <li>عرض المستلمين فقط</li> | <ul><li>المسؤول العام</li> <li>مسؤول الأمان</li> <li>مسؤول التوافق</li> <li>عامل تشغيل الأمان</li> <li>قارئ الأمان</li> <li>القارئ العمومي</li></ul> |
| إدارة التنبيهات والحوادث | التحقيق في التنبيهات | <ul><li>إدارة التنبيهات</li> <li>مسؤول الأمان</li> | <ul><li>المسؤول العام</li> <li>مسؤول الأمان</li> <li>مسؤول التوافق</li> <li>عامل تشغيل الأمان</li> <li>قارئ الأمان</li></ul> |
| معالجة مركز الصيانة | إجراءات المعالجة النشطة – عمليات الأمان | البحث والإزالة | |
| تعيين عمليات الكشف المخصصة | إدارة إعدادات الأمان |<ul><li>إدارة التنبيهات</li> <li>مسؤول الأمان</li></ul> | <ul><li>المسؤول العام</li> <li>مسؤول الأمان</li> <li>مسؤول التوافق</li> <li>عامل تشغيل الأمان</li> <li>قارئ الأمان</li> <li>القارئ العمومي</li></ul> |
| تحليلات التهديدات | بيانات التنبيهات والحوادث: <ul><li>عرض عمليات أمان البيانات</li></ul>عمليات التخفيف من مخاطر الجهاز التلفزيوني:<ul><li>عرض البيانات - التهديد إدارة الثغرات الأمنية</li></ul> | بيانات التنبيهات والحوادث:<ul> <li>إدارة التنبيهات للعرض فقط</li> <li>إدارة التنبيهات</li> <li>تكوين المؤسسة</li><li>سجلات التدقيق</li> <li>عرض سجلات التدقيق فقط</li><li>قارئ الأمان</li> <li>مسؤول الأمان</li><li>عرض المستلمين فقط</li> </ul> محاولات البريد الإلكتروني التي تم منعها: <ul><li>قارئ الأمان</li> <li>مسؤول الأمان</li><li>عرض المستلمين فقط</li> | غير متوفر لمستخدمي Defender for Cloud Apps أو MDI |

على سبيل المثال، لعرض بيانات التتبع من Microsoft Defender لنقطة النهاية، يجب عرض أذونات عمليات أمان البيانات.  

وبالمثل، لعرض بيانات التتبع من Microsoft Defender لـ Office 365، سيحتاج المستخدمون إلى أحد الأدوار التالية:  

- عرض عمليات أمان البيانات
- قارئ الأمان
- مسؤول الأمان
- عرض المستلمين فقط

## <a name="related-topics"></a>المواضيع ذات الصلة
- [أدوار RBAC](../office-365-security/migrate-to-defender-for-office-365-onboard.md#rbac-roles)
- [إدارة الوصول إلى Microsoft 365 Defender](m365d-permissions.md)
- [إدارة وصول المسؤول ل Defender for Cloud Apps](/cloud-app-security/manage-admins)
