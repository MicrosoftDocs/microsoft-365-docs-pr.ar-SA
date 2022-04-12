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
description: إدارة أجهزة iOS في Basic Mobility and Security.
ms.openlocfilehash: 99aa909bf9adab1464ad3858cfac4a04cc541609
ms.sourcegitcommit: ac0ae5c2888e2b323e36bad041a4abef196c9c96
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/12/2022
ms.locfileid: "64781150"
---
# <a name="create-an-apns-certificate-for-ios-devices"></a>إنشاء شهادة APNs للأجهزة التي تعمل بـ iOS

لإدارة أجهزة iOS مثل iPads وiPhones في Basic Mobility and Security، أنشئ شهادة APNs.

1. سجل الدخول إلى Microsoft 365 باستخدام حساب المسؤول العام.

2. في المستعرض، اكتب <https://protection.office.com/>.

3. حدد **إدارة جهاز** **منع** \> فقدان البيانات، واختر **شهادة APNs لأجهزة iOS**.

4. في صفحة الإعدادات شهادة الإعلامات المؤقتة من Apple، اختر **"التالي**".

5. حدد "تنزيل ملف CSR" واحفظ طلب توقيع الشهادة في مكان ما على الكمبيوتر الذي ستتذكره. حدد **"التالي**".

6. في صفحة إنشاء شهادة APNs:

    1. حدد مدخل Apple APNS لفتح مدخل Apple Push Certificates.

    2. سجل الدخول باستخدام معرف Apple.

       > [!IMPORTANT]
       > استخدم معرف Apple للشركة المقترن بحساب بريد إلكتروني سيبقى مع مؤسستك حتى لو ترك المستخدم الذي يدير الحساب. احفظ هذا المعرف لأنك ستحتاج إلى استخدام المعرف نفسه عندما يكون الوقت قد حان لتجديد الشهادة.

    3. حدد **إنشاء شهادة** واقبل شروط الاستخدام.

    4. استعرض وصولا إلى طلب توقيع الشهادة الذي قمت بتنزيله إلى الكمبيوتر من Microsoft 365، وحدد **Upload**.

       قم بتنزيل شهادة APNs التي تم إنشاؤها بواسطة Apple Push Certificate Portal إلى الكمبيوتر.

       > [!TIP]
       > إذا كنت تواجه مشكلة في تنزيل الشهادة، فقم بتحديث المستعرض.

7. ارجع إلى Microsoft 365، وحدد **"التالي**" للوصول إلى صفحة **شهادة APNS Upload**.

8. استعرض وصولا إلى شهادة APN التي قمت بتنزيلها من مدخل Apple Push Certificates.

9. حدد **إنهاء**.

لإكمال الإعداد، ارجع إلى **إعدادات إدارة** **إدارة أجهزة إدارة** \> نهج **أمان** \> مركز \> التوافق & الأمان.
