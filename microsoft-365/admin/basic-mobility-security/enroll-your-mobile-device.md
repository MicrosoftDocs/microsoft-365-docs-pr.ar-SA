---
title: تسجيل جهازك المحمول باستخدام Basic Mobility and Security
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
- admindeeplinkMAC
search.appverid:
- MET150
description: قبل أن تتمكن من استخدام خدمات Microsoft 365 مع جهازك، قد تحتاج أولا إلى تسجيلها في Basic Mobility and Security for Microsoft 365.
ms.openlocfilehash: 714102cf252e4dc483794f4e4280420256bfb0c3
ms.sourcegitcommit: ac0ae5c2888e2b323e36bad041a4abef196c9c96
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/12/2022
ms.locfileid: "64781128"
---
# <a name="enroll-your-mobile-device-using-basic-mobility-and-security"></a>تسجيل جهازك المحمول باستخدام Basic Mobility and Security

يعد استخدام الهاتف والكمبيوتر اللوحي والأجهزة المحمولة الأخرى للعمل طريقة رائعة للبقاء على اطلاع على مشاريع العمل والعمل عليها أثناء وجودك بعيدا عن المكتب. قبل أن تتمكن من استخدام خدمات Microsoft 365 مع جهازك، قد تحتاج أولا إلى تسجيلها في Basic Mobility and Security Microsoft 365 باستخدام Microsoft Intune Company Portal.

تختار المؤسسات Basic Mobility and Security بحيث يمكن للموظفين استخدام أجهزتهم المحمولة للوصول بأمان إلى البريد الإلكتروني والتقويمات والمستندات الخاصة بالعمل بينما تقوم الشركة بتأمين البيانات المهمة وتلبية متطلبات التوافق الخاصة بهم. لمعرفة المزيد، راجع [نظرة عامة على التنقل الأساسي والأمان Microsoft 365](overview.md). لمزيد من المعلومات، راجع [المعلومات التي يمكن لمؤسستي رؤيتها عند تسجيل جهازي؟](/intune-user-help/what-info-can-your-company-see-when-you-enroll-your-device-in-intune).

> [!IMPORTANT]
> عند تسجيل جهازك في Basic Mobility and Security for Microsoft 365، قد يطلب منك إعداد كلمة مرور، إلى جانب السماح للخيار الذي يسمح لمؤسسة العمل بمسح الجهاز. يمكن إجراء مسح للجهاز من <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">مركز مسؤولي Microsoft 365</a>، على سبيل المثال، لإزالة كافة البيانات من الجهاز إذا تم إدخال كلمة المرور بشكل غير صحيح عدة مرات أو إذا تم قطع شروط الاستخدام.

## <a name="supported-devices"></a>الأجهزة المدعومة

تعمل ميزة التنقل الأساسي والأمان Microsoft 365 المستضافة بواسطة خدمة Intune مع معظم الأجهزة المحمولة وليس جميعها. يتم دعم ما يلي مع Basic Mobility and Security:

- دائره الرقابه الداخليه

- الروبوت

- Windows 8.1 و Windows 10 (الهاتف والكمبيوتر الشخصي)

إذا لم يكن جهازك مدرجا أعلاه، وكنت بحاجة إلى استخدامه مع Basic Mobility and Security، فاتصل بمسؤول العمل أو المؤسسة التعليمية.

> [!TIP]
> إذا كنت تواجه مشكلة في تسجيل جهازك، فراجع [استكشاف أخطاء التنقل والأمان الأساسيين وإصلاحها](troubleshoot.md).

## <a name="set-up-your-mobile-device-with-intune-and-basic-mobility-and-security"></a>إعداد جهازك المحمول باستخدام Intune و Basic Mobility and Security

يتيح Intune Company Portal إدارة الجهاز بواسطة Microsoft 365 و Basic Mobility and Security.

### <a name="iphone-or-ipad"></a>iPhone أو iPad

> [!TIP]
> لن تتمكن من إرسال البريد الإلكتروني وتلقيه حتى تكمل هذه الخطوة.

انتقل إلى App Store Apple، وقم بتنزيل Intune Company Portal وتثبيتها.

لتوصيل وتكوين هاتف أو كمبيوتر لوحي يعمل بنظام التشغيل iOS باستخدام مدخل الشركة Office 365، راجع [إعداد وصول جهاز iOS إلى موارد شركتك](/mem/intune/user-help/enroll-your-device-in-intune-ios).

### <a name="android-phone-or-tablet"></a>هاتف أو كمبيوتر لوحي يعمل بنظام Android

> [!TIP]
> لن تتمكن من إرسال البريد الإلكتروني وتلقيه حتى تكمل هذه الخطوة.

انتقل إلى متجر Google Play، وقم بتنزيل Intune Company Portal وتثبيته.

للاتصال بالهاتف أو الكمبيوتر اللوحي الذي يعمل بنظام Android وتكوينه باستخدام مدخل الشركة Microsoft 365، راجع [تسجيل جهازك باستخدام Company Portal](/mem/intune/user-help/enroll-device-android-company-portal).

### <a name="windows-81-and-windows-10"></a>Windows 8.1 و Windows 10

انتقل إلى Microsoft Store، وقم بتنزيل Intune Company Portal وتثبيته

لتوصيل الهاتف أو الكمبيوتر الشخصي Windows وتكوينه باستخدام مدخل الشركة Microsoft 365، راجع [Windows تسجيل الجهاز في Intune Company Portal](/intune-user-help/windows-enrollment-company-portal).

## <a name="next-steps"></a>الخطوات التالية

بعد تسجيل جهازك في Basic Mobility and Security، يمكنك البدء في استخدام تطبيقات Office على جهازك للعمل مع البريد الإلكتروني والتقويم وجهات الاتصال والمستندات.