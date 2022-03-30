---
title: إنشاء شهادة APNs للأجهزة التي تعمل ب iOS
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
description: إدارة أجهزة iOS في التنقل والأمان الأساسيين.
ms.openlocfilehash: f2539ac1c27bd63c13766e197fc12fafc3906f07
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 10/06/2021
ms.locfileid: "63576980"
---
# <a name="create-an-apns-certificate-for-ios-devices"></a>إنشاء شهادة APNs للأجهزة التي تعمل ب iOS

لإدارة أجهزة iOS مثل iPad وiPhone في أساسيات التنقل والأمان، أنشئ شهادة APNs.

1. سجل الدخول Microsoft 365 باستخدام حساب المسؤول العام.

2. في المستعرض، اكتب <https://protection.office.com/>.

3. حدد  **منع فقدان البيانات** >  **إدارة** الأجهزة، واختر **شهادة APNs للأجهزة التي تعمل ب iOS**.

4. في صفحة شهادة الإعلامات من Apple الإعدادات،  **اخترNext**.

5. حدد تنزيل ملف CSR واحفظ طلب توقيع الشهادة في مكان ما على الكمبيوتر ستتذكره.   **SelectNext**.

6. في الصفحة إنشاء شهادة APNs:

    1. حدد Apple APNS Portal لفتح مدخل شهادات Apple Push.

    2. سجل الدخول باستخدام Apple ID.

       > [!IMPORTANT]
       > استخدم "Apple ID" شركة مقترنة باستخدام حساب بريد إلكتروني سيبقى مع مؤسستك حتى لو غادر المستخدم الذي يدير الحساب. احفظ هذا المعرف لأنك ستحتاج إلى استخدام المعرف نفسه عندما يكون الوقت قد حان لتجديد الشهادة.

    3. حدد   **إنشاء شهادة وقبول**  شروط الاستخدام.

    4. استعرض بحثا عن طلب توقيع الشهادة الذي قمت بتنزيلها إلى الكمبيوتر من Microsoft 365، **ثم حدد Upload**.

       قم بتنزيل شهادة APNs التي تم إنشاؤها بواسطة مدخل شهادة Apple Push إلى الكمبيوتر.

       > [!TIP]
       > إذا كنت تواجه مشكلة في تنزيل الشهادة، ف قم بتحديث المستعرض.

7. ارجع إلى Microsoft 365، وحدد **التالي**  للوصول إلى Upload   **شهادة APNS** .

8. استعرض بحثا عن شهادة APN التي قمت بتنزيلها من مدخل شهادات Apple Push.

9.   **حددFinish**.

لإكمال الإعداد، ارجع إلى مركز التوافق & الأمان > **إدارة**  **** >> الأمان  **إدارة إدارة إعدادات الأمان**.
