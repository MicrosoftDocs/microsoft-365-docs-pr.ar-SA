---
title: الاختيار بين Basic Mobility و Security وIntune
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
description: التنقل الأساسي والأمان جزء من خطط Microsoft 365.
ms.openlocfilehash: 0c1c61181d7e8bd5eb0ee000e29285c32a454692
ms.sourcegitcommit: 1c5f9d17a8b095cd88b23f4874539adc3ae021de
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/08/2022
ms.locfileid: "64713834"
---
# <a name="choose-between-basic-mobility-and-security-or-intune"></a>الاختيار بين التنقل الأساسي والأمان أو Intune

[Microsoft Intune](/mem/intune/) هو منتج مستقل مضمن مع خطط Microsoft 365 معينة، في حين أن Basic Mobility and Security هو جزء من خطط Microsoft 365.

 ## <a name="availability-of-basic-mobility-and-security-and-intune"></a>توفر التنقل الأساسي والأمان وIntune

يتم تضمين كل من التنقل الأساسي والأمان وIntune في مجموعة متنوعة من الخطط، الموضحة في الجدول التالي.

| الخطة | أساسيات التنقل والأمان | Microsoft Intune |
|:-----|:-----|:-----|
|تطبيقات Microsoft 365|نعم|لا|
|Microsoft 365 Business Basic|نعم|لا|
|Microsoft 365 Business Standard|نعم|لا|
|Office 365 E1 |نعم|لا|
|Office 365 E3 |نعم|لا|
|Office 365 E5 |نعم|لا|
|Microsoft 365 Business Premium |نعم|نعم|
|Microsoft 365 الخط الأول 3 |نعم|نعم|
|Microsoft 365 Enterprise E3 |نعم|نعم|
|Microsoft 365 Enterprise E5 |نعم|نعم|
|Microsoft 365 Education A1 |نعم|نعم|
|Microsoft 365 Education A3 |نعم|نعم|
|Microsoft 365 Education A5 |نعم|نعم|
|Microsoft Intune |لا|نعم|
|Enterprise Mobility & Security E3 |لا|نعم|
|Enterprise Mobility & Security E5 |لا|نعم|

> [!NOTE]
> لا يمكنك البدء باستخدام Basic Mobility and Security إذا كنت تستخدم Microsoft Intune بالفعل.

 للحصول على التفاصيل، راجع [Microsoft 365 وأوصاف خدمة النظام الأساسي Office 365](/office365/servicedescriptions/office-365-platform-service-description/office-365-platform-service-description).

## <a name="differences-in-capabilities"></a>الاختلافات في القدرات

يوفر لك كل من Microsoft Intune و Basic Mobility and Security المدمجين القدرة على إدارة الأجهزة المحمولة في مؤسستك، ولكن هناك اختلافات رئيسية في الإمكانية، موضحة في الجدول التالي.

> [!NOTE]
> يمكنك إدارة المستخدمين وأجهزتهم المحمولة باستخدام كل من Intune و Basic Mobility و Security في نفس مؤسسة Microsoft 365 Business Standard *عن طريق إعداد Basic Mobility and Security أولا، ثم إضافة Microsoft Intune*. يسمح لك هذا باختيار Basic Mobility and Security أو حل Intune الأكثر ثراء بالميزات. تعيين ترخيص Intune لتمكين ميزات Intune.

| منطقة الميزة | أهم الميزات | أساسيات التنقل والأمان | Microsoft Intune |
|:-----|:-----|:-----|:-----|
|أنواع الأجهزة|إدارة الأنظمة الأساسية المختلفة لنظام التشغيل ومتغيرات وضع الإدارة الرئيسية. |بالنسبة لنظام التشغيل<br/>دائره الرقابه الداخليه<br/>الروبوت<br/>Android Samsung KNOX<br/>|بالنسبة لنظام التشغيل<br/>دائره الرقابه الداخليه<br/>الروبوت<br/>Android Samsung KNOX<br/>mac OS، iPad OS|
|توافق الجهاز|تعيين نهج الأمان وإدارتها، مثل تأمين رقم التعريف الشخصي (PIN) على مستوى الجهاز والكشف عن خرق القفل. |القيود على أجهزة Android. راجع [التفاصيل](capabilities.md). |نعم|
|الوصول المشروط استنادا إلى توافق الجهاز |منع الأجهزة غير المتوافقة من الوصول إلى البريد الإلكتروني وبيانات الشركة من السحابة. |غير معتمد في Windows 10.<br/>تقتصر على التحكم في الوصول إلى Exchange Online SharePoint عبر الإنترنت Outlook. |نعم |
|تكوين الجهاز  |تكوين إعدادات الجهاز (على سبيل المثال، تعطيل الكاميرا)|مجموعة محدودة من الإعدادات.|نعم|
|ملفات تعريف البريد الإلكتروني  |توفير ملف تعريف بريد إلكتروني أصلي على الجهاز. |نعم|نعم|
|ملفات تعريف WiFi |توفير ملف تعريف WiFi أصلي على الجهاز. |لا|نعم|
|ملفات تعريف VPN |توفير ملف تعريف VPN أصلي على الجهاز. |لا|نعم|
|إدارة تطبيقات الأجهزة المحمولة  |نشر تطبيقات خط العمل الداخلية ومن متاجر التطبيقات إلى المستخدمين. |لا|نعم|
|حماية تطبيقات الأجهزة المحمولة  |تمكين المستخدمين من الوصول بأمان إلى معلومات الشركة باستخدام Office تطبيقات الجوال وخط العمل التي يعرفونها، مع ضمان أمان البيانات من خلال المساعدة في تقييد إجراءات مثل النسخ والقص واللصق والحفظ باسم، على التطبيقات التي تتم إدارتها فقط والتي تمت الموافقة عليها لبيانات الشركة. يعمل حتى إذا لم تكن الأجهزة مسجلة في Basic Mobility and Security. راجع حماية بيانات التطبيق باستخدام نهج MAM. |لا|نعم|
|المستعرض المدار  |تمكين استعراض ويب أكثر أمانا باستخدام تطبيق Edge. |لا|نعم|
|برامج تسجيل بدون لمس (AutoPilot) |تسجيل أعداد كبيرة من الأجهزة المملوكة للشركة، مع تبسيط إعداد المستخدم. |لا|نعم|

بالإضافة إلى الميزات المذكورة في الجدول السابق، يتضمن كل من Basic Mobility وIntune مجموعة من الإجراءات البعيدة التي ترسل الأوامر إلى الأجهزة عبر الإنترنت. على سبيل المثال، يمكنك إزالة بيانات Office من جهاز موظف أثناء ترك البيانات الشخصية في مكانها (إيقاف التشغيل)، أو إزالة تطبيقات Office من جهاز الموظف (مسح)، أو إعادة تعيين جهاز إلى إعدادات المصنع الخاصة به (مسح كامل).

تتضمن الإجراءات الأساسية للتنقل والأمان عن بعد إيقاف التشغيل والمسح والمسح الكامل. لمزيد من المعلومات حول الإجراءات الأساسية للتنقل والأمان، راجع [قدرات Basic Mobility and Security](capabilities.md).

مع Intune لديك مجموعة الإجراءات التالية:

- [إعادة تعيين Autopilot](/mem/autopilot/windows-autopilot-reset) (Windows فقط)
- استرداد   [مفتاح Bitlocker](https://support.microsoft.com/windows/finding-your-bitlocker-recovery-key-in-windows-6b71ad27-0b89-ea08-f143-056f5ab347d6) (Windows فقط)
- [استخدام مسح الجهاز أو إيقافه أو إلغاء تسجيله يدويا](/mem/intune/remote-actions/devices-wipe#delete-devices-from-the-intune-portal)
- [تعطيل تأمين](/mem/intune/remote-actions/device-activation-lock-disable)  التنشيط (iOS فقط)
- [بداية جديدة](/mem/intune/remote-actions/device-fresh-start)  (Windows فقط)
- [فحص](/mem/intune/configuration/device-restrictions-windows-10#microsoft-defender-antivirus)  كامل (Windows 10 فقط)
- [تحديد موقع الجهاز](/mem/intune/remote-actions/device-locate)  (iOS فقط)
- [الوضع](/mem/intune/remote-actions/device-lost-mode)  المفقود (iOS فقط)- [المسح السريع](/mem/intune/configuration/device-restrictions-windows-10#microsoft-defender-antivirus) (Windows 10 فقط)
- [التحكم عن بعد لنظام التشغيل Android](/mem/intune/remote-actions/teamviewer-support)
- [تأمين عن بعد](/mem/intune/remote-actions/device-remote-lock)
- [إعادة تسمية الجهاز](/mem/intune/remote-actions/device-rename)
- إعادة [تعيين إعادة تشغيل](/mem/intune/remote-actions/device-restart)  [رمز المرور](/mem/intune/remote-actions/device-passcode-reset) (Windows فقط)
- [تحديث Windows Defender Security Intelligence](https://www.microsoft.com/en-us/wdsi/defenderupdates) (Windows فقط)
- [إعادة تعيين رمز PIN Windows 10](/windows/security/identity-protection/hello-for-business/hello-feature-pin-reset) (Windows فقط)
- [إرسال إعلامات](/mem/intune/remote-actions/custom-notifications#send-a-custom-notification-to-a-single-device)  مخصصة (Android وiOS iPad OS)
- [مزامنة الجهاز](/mem/intune/remote-actions/device-sync)

لمزيد من المعلومات حول إجراءات Intune، راجع [وثائق Microsoft Intune](/mem/intune/).
