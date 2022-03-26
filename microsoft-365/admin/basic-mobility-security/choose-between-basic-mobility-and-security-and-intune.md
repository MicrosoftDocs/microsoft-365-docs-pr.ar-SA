---
title: الاختيار بين التنقل والأمان الأساسيين و Intune
f1.keywords:
- NOCSH
ms.author: kwekua
author: kwekua
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
ms.custom:
- AdminSurgePortfolio
- AdminTemplateSet
search.appverid:
- MET150
description: التنقل والأمان الأساسيان جزء من Microsoft 365 الأساسية.
ms.openlocfilehash: 79e5a641ad4c7c1966d1014376c9f1698caeff16
ms.sourcegitcommit: cdb90f28e59f36966f8751fa8ba352d233317fc1
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/09/2022
ms.locfileid: "63572904"
---
# <a name="choose-between-basic-mobility-and-security-or-intune"></a>الاختيار بين التنقل والأمان الأساسيين أو Intune

[Microsoft Intune](/mem/intune/) منتج مستقل مضمن مع خطط Microsoft 365، في حين أن التنقل والأمان الأساسيين هو جزء من Microsoft 365 الأساسية.

 ## <a name="availability-of-basic-mobility-and-security-and-intune"></a>توفر التنقل والأمان الأساسيين و Intune

يتم تضمين كل من التنقل الأساسي والأمان و Intune في مجموعة متنوعة من الخطط، كما هو موضح في الجدول التالي.

| الخطة | التنقل والأمان الأساسيان | Microsoft Intune |
|:-----|:-----|:-----|
|تطبيقات Microsoft 365|نعم|لا|
|Microsoft 365 Business Basic|نعم|لا|
|Microsoft 365 Business Standard|نعم|لا|
|Office 365 E1 |نعم|لا|
|Office 365 E3 |نعم|لا|
|Office 365 E5 |نعم|لا|
|Microsoft 365 Business Premium |نعم|نعم|
|Microsoft 365 الأول 3 |نعم|نعم|
|Microsoft 365 Enterprise E3 |نعم|نعم|
|Microsoft 365 Enterprise E5 |نعم|نعم|
|Microsoft 365 Education A1 |نعم|نعم|
|Microsoft 365 Education A3 |نعم|نعم|
|Microsoft 365 Education A5 |نعم|نعم|
|Microsoft Intune |لا|نعم|
|Enterprise Mobility & Security E3 |لا|نعم|
|Enterprise Mobility & Security E5 |لا|نعم|

> [!NOTE]
> لا يمكنك بدء استخدام "التنقل والأمان الأساسيين" إذا كنت تستخدم Microsoft Intune.

 للحصول على التفاصيل، راجع Microsoft 365 [Office 365 أوصاف خدمة النظام الأساسي](/office365/servicedescriptions/office-365-platform-service-description/office-365-platform-service-description).

## <a name="differences-in-capabilities"></a>الاختلافات في القدرات

Microsoft Intune التنقل والأمان الأساسيين القدرة على إدارة الأجهزة المحمولة في مؤسستك، ولكن هناك اختلافات رئيسية في الإمكانية، كما هو موضح في الجدول التالي.

> [!NOTE]
> يمكنك إدارة المستخدمين وأجهزتهم المحمولة باستخدام كل من Intune و Basic Mobility والأمان في مؤسسة Microsoft 365 Business Standard نفسها من خلال إعداد *Basic Mobility and Security* أولا، ثم إضافة Microsoft Intune. يسمح لك ذلك باختيار التنقل والأمان الأساسيين أو حل Intune الغني بالميزات. تعيين ترخيص Intune لتمكين ميزات Intune.

| منطقة الميزة | تمييزات الميزات | التنقل والأمان الأساسيان | Microsoft Intune |
|:-----|:-----|:-----|:-----|
|أنواع الأجهزة|إدارة الأنظمة الأساسية المختلفة ل OS والمتغيرات الرئيسية في وضع الإدارة. |بالنسبة لنظام التشغيل<br/>iOS<br/>Android<br/>Android Samsung KNOX<br/>|بالنسبة لنظام التشغيل<br/>iOS<br/>Android<br/>Android Samsung KNOX<br/>mac OS، iPad OS|
|توافق الجهاز|قم بتعيين سياسات الأمان وإدارتها، مثل تأمين رقم التعريف الشخصي (PIN) على مستوى الجهاز والكشف عن فاتحة القفل. |القيود المفروضة على أجهزة Android. راجع [التفاصيل](capabilities.md). |نعم|
|الوصول الشرطي استنادا إلى توافق الأجهزة |منع الأجهزة غير المتوافقة من الوصول إلى البريد الإلكتروني وبيانات الشركة من السحابة. |غير معتمد على Windows 10.<br/>يقتصر على التحكم في الوصول إلى Exchange Online SharePoint عبر الإنترنت Outlook. |نعم |
|تكوين الجهاز  |تكوين إعدادات الجهاز (على سبيل المثال، تعطيل الكاميرا)|مجموعة محدودة من الإعدادات.|نعم|
|ملفات تعريف البريد الإلكتروني  |توفير ملف تعريف أصلي للبريد الإلكتروني على الجهاز. |نعم|نعم|
|ملفات تعريف WiFi |توفير ملف تعريف WiFi أصلي على الجهاز. |لا|نعم|
|ملفات تعريف VPN |توفير ملف تعريف VPN أصلي على الجهاز. |لا|نعم|
|إدارة تطبيقات الأجهزة المحمولة  |نشر تطبيقات خط العمل الداخلية ومن متاجر التطبيقات إلى المستخدمين. |لا|نعم|
|حماية تطبيقات الأجهزة المحمولة  |تمكن المستخدمين من الوصول الآمن إلى معلومات الشركة باستخدام تطبيقات Office الخاصة بالهاتف المحمول وخط العمل التي يعرفونها، مع ضمان أمان البيانات من خلال المساعدة في تقييد إجراءات مثل النسخ والقص واللصق والحفظ باسم، فقط لتلك التطبيقات المدارة المعتمدة لبيانات الشركة. يعمل حتى لو لم تكن الأجهزة مسجله في Basic Mobility and Security. راجع حماية بيانات التطبيق باستخدام سياسات MAM. |لا|نعم|
|المستعرض المدار  |تمكين استعراض ويب أكثر أمانا باستخدام تطبيق Edge. |لا|نعم|
|برامج تسجيل اللمس الصفرية (AutoPilot) |قم بتسجيل أعداد كبيرة من الأجهزة المملوكة للشركات، مع تبسيط إعداد المستخدم. |لا|نعم|
|||

بالإضافة إلى الميزات المدرجة في الجدول السابق، تتضمن كل من أساسيات التنقل والأمان و Intune مجموعة من الإجراءات البعيدة التي ترسل الأوامر إلى الأجهزة عبر الإنترنت. على سبيل المثال، يمكنك إزالة بيانات Office من جهاز موظف أثناء ترك البيانات الشخصية في مكانها (إيقاف التشغيل)، أو إزالة تطبيقات Office من جهاز موظف (مسح)، أو إعادة تعيين جهاز إلى إعدادات المصنع (مسح كامل).

تتضمن الإجراءات الأساسية للتنقل والأمان عن بعد إيقاف العمل ومسحه ومسحه بالكامل. لمزيد من المعلومات حول إجراءات التنقل والأمان الأساسية، راجع إمكانات [التنقل والأمان الأساسيين](capabilities.md).

باستخدام Intune، لديك مجموعة الإجراءات التالية:

-   إعادة تعيين Autopilot (Windows فقط
-  [تدوير مفتاح Bitlocker](/mem/intune/protect/encrypt-devices#rotate-bitlocker-recovery-keys)  (Windows فقط)
-  [استخدام مسح الجهاز أو إيقافه أو إلغاء استخدامه يدويا](/mem/intune/remote-actions/devices-wipe#delete-devices-from-the-intune-portal)
-  [تعطيل loc التنشيط](/mem/intune/remote-actions/device-activation-lock-disable)  (iOS فقط)
-  [بداية جديدة](/mem/intune/remote-actions/device-fresh-start)  (Windows فقط)
- [فحص كامل](/mem/intune/configuration/device-restrictions-windows-10#microsoft-defender-antivirus)  (Windows 10 فقط)
- [تحديد موقع الجهاز](/mem/intune/remote-actions/device-locate)  (iOS فقط)
- [وضع مفقود](/mem/intune/remote-actions/device-lost-mode)  (iOS فقط)- [المسح السريع](/mem/intune/configuration/device-restrictions-windows-10#microsoft-defender-antivirus)(Windows 10 فقط)
- [التحكم عن بعد لنظام التشغيل Android](/mem/intune/remote-actions/teamviewer-support)
- [تأمين عن بعد](/mem/intune/remote-actions/device-remote-lock)
- [إعادة تسمية الجهاز](/mem/intune/remote-actions/device-rename)
-  [إعادة تعيين إعادة تشغيل](/mem/intune/remote-actions/device-passcode-reset) [](/mem/intune/remote-actions/device-restart) رمز المرور(Windows فقط)
-  تحديث Windows أمان Defender (Windows فقط)
-  Windows 10 إعادة تعيين رمز PIN (Windows فقط)
-  [إرسال إعلامات مخصصة](/mem/intune/remote-actions/custom-notifications#send-a-custom-notification-to-a-single-device)  (Android و iOS و iPad OS)
-  [مزامنة الجهاز](/mem/intune/remote-actions/device-sync)

لمزيد من المعلومات حول إجراءات Intune، راجع Microsoft Intune [الوثائق](/mem/intune/).
