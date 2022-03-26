---
title: تمكين تجوال حالة المؤسسة
description: تصف هذه المقالة كيفية تمكين تجوال حالة المؤسسة
keywords: سطح المكتب المدار من Microsoft، Microsoft 365، الخدمة، الوثائق
ms.service: m365-md
author: tiaraquan
ms.localizationpriority: medium
ms.collection: M365-modern-desktop
ms.author: tiaraquan
manager: dougeby
ms.topic: article
ms.openlocfilehash: 65056fc913b88ce0594c9a8b1a89bd2e92b221af
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/08/2022
ms.locfileid: "63566769"
---
# <a name="enable-enterprise-state-roaming"></a>تمكين تجوال حالة المؤسسة

[يتيح "تجوال حالة المؤسسة](/azure/active-directory/devices/enterprise-state-roaming-overview) " للمستخدمين مزامنة بيانات إعدادات المستخدم والتطبيق بأمان إلى السحابة. وهذا يعني أنه سيكون لديهم نفس التجربة بغض النظر عن الجهاز الذي Windows تسجيل الدخول. على سبيل المثال، إذا استبدلت أحد أجهزة سطح المكتب المدارة من Microsoft بجهاز جديد، سيبدو وسيتصرف تماما كالأجهزة الأخيرة.

تجوال حالة المؤسسة هو ميزة اختيارية لخدمة Microsoft Managed Desktop التي يمكنك تكوينها للمستخدمين. ولا يتم تضمينه أو إدارته كجزء من Microsoft Managed Desktop.

لتمكين تجوال حالة المؤسسة، اتبع الخطوات في [تمكين تجوال حالة المؤسسة في Azure Active Directory](/azure/active-directory/devices/enterprise-state-roaming-enable).

>[!NOTE]
>إذا قمت بتمكين "تجوال حالة المؤسسة"، فإن قائمة اللغات المفضلة لديك ست الكتابة فوق اللغة المحددة أثناء إعداد الجهاز. على الرغم من أن المستخدمين يمكنهم إصلاح هذا الأمر بسهولة، إلا أنه قد يتسبب في تجربة تهريب غير متناسقة في البداية. حدد ما إذا كان "تجوال حالة المؤسسة" صحيحا للمستخدمين قبل إعداد الأجهزة.

## <a name="steps-to-get-started-with-microsoft-managed-desktop"></a>خطوات بدء تشغيل Microsoft Managed Desktop

1. [إضافة جهات اتصال المسؤول والتحقق منها في مدخل المسؤول](add-admin-contacts.md).
2. [ضبط الوصول الشرطي](conditional-access.md).
3. [تعيين التراخيص](assign-licenses.md).
4. [نشر Intune Company Portal](company-portal.md).
5. تمكين تجوال حالة المؤسسة (هذا الموضوع).
6. [تحضير الأجهزة](prepare-devices.md).
7. [اجهز المستخدمين لاستخدام الأجهزة](get-started-devices.md).
8. [نشر التطبيقات](deploy-apps.md).
