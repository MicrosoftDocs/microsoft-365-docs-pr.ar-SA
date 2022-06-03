---
title: إنشاء شهادة APNs للأجهزة التي تعمل بـ iOS
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
description: لإدارة أجهزة iOS مثل iPads وiPhones في Basic Mobility and Security، ابدأ بإنشاء شهادة APNs.
ms.openlocfilehash: 10d2e8412cfecf3627c7520123592b371bf01fdb
ms.sourcegitcommit: 1fa0b15f86470c49dddf0d6de59d553a38ae259b
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 06/03/2022
ms.locfileid: "65863511"
---
# <a name="create-an-apns-certificate-for-ios-devices"></a>إنشاء شهادة APNs للأجهزة التي تعمل بـ iOS

لإدارة أجهزة iOS مثل iPads وiPhones في Basic Mobility and Security، أنشئ شهادة APNs.

1. سجل الدخول إلى Microsoft 365 باستخدام حساب المسؤول العام.

1. انتقل إلى [مركز مسؤولي Microsoft 365](https://portal.office.com/adminportal/home?#/MifoDevices)، واختر **شهادة APNs لنظام التشغيل iOS**.

1. في صفحة الإعدادات شهادة الإعلامات المؤقتة من Apple، اختر **"التالي**".

1. حدد "تنزيل ملف CSR" واحفظ طلب توقيع الشهادة في مكان ما على الكمبيوتر الذي ستتذكره. حدد **التالي**.

1. في صفحة إنشاء شهادة APNs:

    1. حدد مدخل Apple APNS لفتح مدخل Apple Push Certificates.

    2. سجل الدخول باستخدام معرف Apple.

       > [!IMPORTANT]
       > استخدم معرف Apple للشركة المقترن بحساب بريد إلكتروني سيبقى مع مؤسستك حتى لو ترك المستخدم الذي يدير الحساب. احفظ هذا المعرف لأنك ستحتاج إلى استخدام المعرف نفسه عندما يكون الوقت قد حان لتجديد الشهادة.

    3. حدد **إنشاء شهادة** واقبل شروط الاستخدام.

    4. استعرض وصولا إلى طلب توقيع الشهادة الذي قمت بتنزيله إلى الكمبيوتر من Microsoft 365، وحدد **Upload**.

       قم بتنزيل شهادة APNs التي تم إنشاؤها بواسطة Apple Push Certificate Portal إلى الكمبيوتر.

       > [!TIP]
       > إذا كنت تواجه مشكلة في تنزيل الشهادة، فقم بتحديث المستعرض.

1. ارجع إلى Microsoft 365، وحدد **"التالي**" للوصول إلى صفحة **شهادة APNS Upload**.

1. استعرض وصولا إلى شهادة APN التي قمت بتنزيلها من مدخل Apple Push Certificates.

1. حدد **إنهاء**.

لإكمال الإعداد، ارجع إلى **إعدادات إدارة** **إدارة أجهزة إدارة** \> نهج **أمان** \> مركز \> التوافق & الأمان.
