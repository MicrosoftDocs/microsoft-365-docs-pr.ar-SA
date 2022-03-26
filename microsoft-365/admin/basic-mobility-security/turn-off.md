---
title: إيقاف تشغيل التنقل والأمان الأساسيين
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
description: قم بإزالة المجموعات أو النهج من أجل إيقاف تشغيل "التنقل والأمان الأساسيين".
ms.openlocfilehash: ff3fe72e1ca3a6445aa29ac18404aae139a70f8a
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 10/06/2021
ms.locfileid: "63572917"
---
# <a name="turn-off-basic-mobility-and-security"></a>إيقاف تشغيل التنقل والأمان الأساسيين

ول إيقاف تشغيل "التنقل والأمان الأساسيين" بشكل فعال، يمكنك إزالة مجموعات من الأشخاص المعرفة بواسطة مجموعات الأمان من سياسات إدارة الأجهزة، أو إزالة النهج نفسها.

- يمكنك إزالة مجموعات المستخدمين عن طريق إزالة مجموعات أمان المستخدمين من سياسات الأجهزة التي أنشأتها.

- قم بتعطيل التنقل والأمان الأساسيين للجميع عن طريق إزالة كل سياسات الأجهزة الأساسية الخاصة بالتنقل والأمان.

تعمل هذه الخيارات على إزالة فرض التنقل والأمان الأساسي للأجهزة في مؤسستك. لسوء الحظ، لا يمكنك ببساطة "إلغاء توفير" التنقل والأمان الأساسيين بعد إعداده.

> [!IMPORTANT]
> كن على دراية بالتأثر على أجهزة المستخدمين عند إزالة مجموعات أمان المستخدمين من السياسات أو إزالة السياسات نفسها. على سبيل المثال، قد تتم إزالة ملفات تعريف البريد الإلكتروني ورسائل البريد الإلكتروني المخزنة مؤقتا، استنادا إلى الجهاز. لمزيد من المعلومات، راجع   [ما الذي يحدث عند حذف نهج أو إزالة مستخدم من النهج؟](../../admin/basic-mobility-security/create-device-security-policies.md)

## <a name="remove-user-security-groups-from-basic-mobility-and-security-device-policies"></a>إزالة مجموعات أمان المستخدمين من سياسات الأجهزة الأساسية للتنقل والأمان

1. في المستعرض، اكتب: [https://protection.office.com/devicev2](https://protection.office.com/devicev2).

2. حدد نهج جهاز، وحدد **تحرير نهج**.

3. في صفحة  **النشر** ، حدد **إزالة**.

4. ضمن   **مجموعات،** حدد مجموعة أمان.

5. حدد  **إزالة**، وحدد **حفظ**.

## <a name="remove-basic-mobility-and-security-device-policies"></a>إزالة سياسات الأجهزة الأساسية للتنقل والأمان

1. في المستعرض، اكتب: [https://protection.office.com/devicev2](https://protection.office.com/devicev2).

2. حدد نهج جهاز، ثم حدد  **حذف نهج**.

3. في مربع الحوار تحذير، حدد **نعم**.

> [!NOTE]
> للحصول على مزيد من الخطوات لإزالة حظر الأجهزة إذا كانت أجهزة المؤسسة لا تزال في حالة حظر، راجع منشور المدونة إزالة التحكم بالوصول [من](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Removing-Access-Control-from-Mobile-Device-Management-for-Office/ba-p/279934) Mobile Device Management لـ Office 365.
