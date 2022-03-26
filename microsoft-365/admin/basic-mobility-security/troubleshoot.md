---
title: استكشاف الأخطاء في التنقل والأمان الأساسيين وإصلاحها
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
ms.openlocfilehash: 2ac25e36fced24e5b50e7e89d36dae3e842fda04
ms.sourcegitcommit: cdb90f28e59f36966f8751fa8ba352d233317fc1
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/09/2022
ms.locfileid: "63569427"
---
# <a name="troubleshoot-basic-mobility-and-security"></a>استكشاف الأخطاء في التنقل والأمان الأساسيين وإصلاحها

إذا كنت تواجه مشاكل عند محاولة تسجيل جهاز في التنقل والأمان الأساسيين، فجرب الخطوات هنا لتعقب المشكلة. إذا لم تصلح الخطوات العامة المشكلة، فشاهد أحد المقاطع اللاحقة التي بها خطوات معينة لنوع الجهاز.

## <a name="steps-to-try-first"></a>الخطوات التي يجب محاولة القيام بها أولا

للبدء، تحقق مما يلي:

- تأكد من أن الجهاز غير مسجل بالفعل مع موفر آخر لإدارة أجهزة المحمول، مثل Intune.

- تأكد من تعيين الجهاز إلى التاريخ والوقت الصحيحين.

- التبديل إلى شبكة WIFI أو شبكة خليوية أخرى على الجهاز.

- بالنسبة لأجهزة Android أو iOS، يمكنك إلغاء تثبيت تطبيق Intune Company Portal على الجهاز وإعادة تثبيته. 

## <a name="ios-phone-or-tablet"></a>هاتف أو كمبيوتر لوحي بنظام التشغيل iOS

- تأكد من إعداد شهادة APNs. لمزيد من المعلومات، راجع [إنشاء شهادة APNs للأجهزة التي تعمل ب iOS](create-an-apns-certificate-for-ios-devices.md).

- In  **الإعدادات** >  **GeneralProfile** >  **(or Device Management), make** sure that a Management Profile is not already installed. إذا كان كذلك، ف قم بإزالته.

- إذا رأيت رسالة الخطأ "فشل تسجيل الجهاز"، فسجل الدخول إلى Microsoft 365 وتأكد من تعيين ترخيص يتضمن Exchange Online إلى المستخدم الذي سجل الدخول إلى الجهاز.

- إذا رأيت رسالة الخطأ ، "فشل تثبيت ملف التعريف"، فجرب أحد الخطوات التالية:

    - تأكد من أن Safari هو المستعرض الافتراضي على الجهاز، ومن عدم تعطيل ملفات تعريف الارتباط.

    - إعادة تشغيل الجهاز، ثم الانتقال إلى portal.manage.microsoft.com. سجل الدخول باستخدام Microsoft 365 المستخدم وكلمة المرور، ثم حاول تثبيت ملف التعريف يدويا.

## <a name="windows-rt"></a>Windows RT

- تأكد من إعداد مجالك في Microsoft 365 للعمل مع أساسيات التنقل والأمان. لمزيد من المعلومات، راجع [إعداد التنقل والأمان الأساسيين](set-up.md).
    
- تأكد من اختيار المستخدم  **Onrather من**  اختيار  **الانضمام**.

## <a name="windows-10-pc"></a>Windows 10 الكمبيوتر الشخصي

- تأكد من إعداد مجالك في Microsoft 365 للعمل مع أساسيات التنقل والأمان. لمزيد من المعلومات، راجع [إعداد التنقل والأمان الأساسيين](set-up.md).
    
- ما لم يكن لديك Azure Active Directory Premium، فتأكد من أن المستخدم يختار تسجيل في  **إدارة**  الأجهزة فقط  **بدلا** من الاتصال.

## <a name="android-phone-or-tablet"></a>هاتف أو كمبيوتر لوحي يعمل بنظام Android

- تأكد من أن الجهاز يعمل بنظام Android.

- تأكد من تحديث Chrome ومن تعيينه كمستعرض افتراضي.

- إذا رأيت رسالة الخطأ "لم نتمكن من تسجيل هذا الجهاز"، فسجل الدخول إلى Microsoft 365 وتأكد من تعيين ترخيص يتضمن Exchange Online إلى المستخدم الذي سجل الدخول إلى الجهاز.

- تحقق من منطقة الإعلامات على الجهاز لمعرفة ما إذا كانت هناك أي إجراءات مطلوبة للمستخدم النهائي معلقة، وإذا كانت معلقة، فأكمل الإجراءات.