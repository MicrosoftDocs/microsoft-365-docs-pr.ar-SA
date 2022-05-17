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
ms.openlocfilehash: 8bcbcdeac9f1cadd945c3f7c44e9192d57db7c82
ms.sourcegitcommit: 9255a7e8b398f92d8dae09886ae95dc8577bf29a
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 05/17/2022
ms.locfileid: "65435778"
---
# <a name="create-an-apns-certificate-for-ios-devices"></a>إنشاء شهادة APNs للأجهزة التي تعمل بـ iOS

لإدارة أجهزة iOS مثل iPads وiPhones في Basic Mobility and Security، أنشئ شهادة APNs.

1. سجل الدخول إلى Microsoft 365 باستخدام حساب المسؤول العام.

2. في المستعرض، اكتب <https://protection.office.com/>.

3. حدد **إدارة جهاز** **منع** \> فقدان البيانات، واختر **شهادة APNs لأجهزة iOS**.

4. في صفحة الإعدادات شهادة الإعلامات المؤقتة من Apple، اختر **"التالي**".

5. حدد "تنزيل ملف CSR" واحفظ طلب توقيع الشهادة في مكان ما على الكمبيوتر الذي ستتذكره. حدد **التالي**.

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
