---
title: استكشاف أخطاء التنقل والأمان الأساسي وإصلاحها
f1.keywords: NOCSH
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
ms.custom: AdminSurgePortfolio
description: جرب هذه الخطوات لتعقب مشاكل التنقل والأمان الأساسية
ms.openlocfilehash: 1b1b7d67eb07c67c320554c1d64701983da30e15
ms.sourcegitcommit: db1e48af88995193f15bbd5962f5101a6088074b
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 05/23/2022
ms.locfileid: "65636053"
---
# <a name="troubleshoot-basic-mobility-and-security"></a>استكشاف أخطاء التنقل والأمان الأساسي وإصلاحها

إذا كنت تواجه مشاكل عند محاولة تسجيل جهاز في Basic Mobility and Security، فجرب الخطوات هنا لتتبع المشكلة. إذا لم تصحح الخطوات العامة المشكلة، فراجع أحد الأقسام اللاحقة التي تتضمن خطوات محددة لنوع جهازك.

## <a name="steps-to-try-first"></a>الخطوات التي يجب تجربتها أولا

للبدء، تحقق مما يلي:

- تأكد من أن الجهاز غير مسجل بالفعل مع موفر آخر لإدارة الأجهزة المحمولة، مثل Intune.

- تأكد من تعيين الجهاز إلى التاريخ والوقت الصحيحين.

- التبديل إلى شبكة WIFI أو شبكة شبكة الجوال المختلفة على الجهاز.

- بالنسبة لأجهزة Android أو iOS، قم بإلغاء تثبيت تطبيق Intune Company Portal وإعادة تثبيته على الجهاز. 

## <a name="ios-phone-or-tablet"></a>هاتف أو كمبيوتر لوحي يعمل بنظام iOS

- تأكد من إعداد شهادة APNs. لمزيد من المعلومات، راجع [إنشاء شهادة APNs لأجهزة iOS](create-an-apns-certificate-for-ios-devices.md).

- في **الإعدادات** >  **GeneralProfile** >  **(أو إدارة الجهاز)،** تأكد من عدم تثبيت "ملف تعريف الإدارة" بالفعل. إذا كان كذلك، فقم بإزالته.

- إذا رأيت رسالة الخطأ "فشل تسجيل الجهاز"، فقم بتسجيل الدخول إلى Microsoft 365 وتأكد من تعيين ترخيص يتضمن Exchange Online إلى المستخدم الذي قام بتسجيل الدخول إلى الجهاز.

- إذا رأيت رسالة الخطأ، "فشل تثبيت ملف التعريف"، فجرب أحد الإجراءات التالية:

    - تأكد من أن Safari هو المستعرض الافتراضي على الجهاز، وأن ملفات تعريف الارتباط غير معطلة.

    - أعد تشغيل الجهاز، ثم انتقل إلى portal.manage.microsoft.com. سجل الدخول باستخدام معرف المستخدم وكلمة المرور Microsoft 365، وحاول تثبيت ملف التعريف يدويا.

## <a name="windows-rt"></a>Windows RT

- تأكد من إعداد مجالك في Microsoft 365 للعمل مع Basic Mobility and Security. لمزيد من المعلومات، راجع [إعداد Basic Mobility and Security](set-up.md).
    
- تأكد من أن المستخدم يختار **"تشغيل"** بدلا **من اختيار "** انضمام".

## <a name="windows-10-pc"></a>كمبيوتر Windows 10

- تأكد من إعداد مجالك في Microsoft 365 للعمل مع Basic Mobility and Security. لمزيد من المعلومات، راجع [إعداد Basic Mobility and Security](set-up.md).
    
- ما لم يكن لديك Premium Azure Active Directory، تأكد من أن المستخدم يختار **التسجيل في إدارة الجهاز فقط** بدلا من اختيار **الاتصال**.

## <a name="android-phone-or-tablet"></a>هاتف أو كمبيوتر لوحي يعمل بنظام Android

- تأكد من أن الجهاز يعمل بنظام Android.

- تأكد من أن Chrome محدث وتم تعيينه كمستعرض افتراضي.

- إذا رأيت رسالة الخطأ "تعذر علينا تسجيل هذا الجهاز"، فقم بتسجيل الدخول إلى Microsoft 365 وتأكد من تعيين ترخيص يتضمن Exchange Online إلى المستخدم الذي قام بتسجيل الدخول إلى الجهاز.

- تحقق من منطقة الإعلامات على الجهاز لمعرفة ما إذا كانت هناك أي إجراءات مطلوبة للمستخدم النهائي معلقة، وإذا كانت معلقة، فأكمل الإجراءات.