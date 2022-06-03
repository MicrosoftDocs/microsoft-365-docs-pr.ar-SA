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
description: إزالة المجموعات أو النهج لإيقاف تشغيل Basic Mobility and Security.
ms.openlocfilehash: 59a54b9969bf16c7523a6862c6f0960bb1527e8a
ms.sourcegitcommit: 1fa0b15f86470c49dddf0d6de59d553a38ae259b
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 06/03/2022
ms.locfileid: "65863021"
---
# <a name="turn-off-basic-mobility-and-security"></a>إيقاف تشغيل التنقل والأمان الأساسيين

لإيقاف تشغيل Basic Mobility and Security بشكل فعال، يمكنك إزالة مجموعات من الأشخاص المعرفة بواسطة مجموعات الأمان من نهج إدارة الأجهزة، أو إزالة النهج نفسها.

- قم بإزالة مجموعات المستخدمين عن طريق إزالة مجموعات أمان المستخدم من نهج الجهاز التي أنشأتها.

- تعطيل التنقل الأساسي والأمان للجميع عن طريق إزالة جميع نهج الأجهزة الأساسية للتنقل والأمان.

تزيل هذه الخيارات تطبيق Basic Mobility and Security للأجهزة في مؤسستك. لسوء الحظ، لا يمكنك ببساطة "إلغاء التوفير" Basic Mobility and Security بعد إعداده.

> [!IMPORTANT]
> كن على دراية بالتأثير على أجهزة المستخدمين عند إزالة مجموعات أمان المستخدمين من النهج أو إزالة النهج نفسها. على سبيل المثال، قد تتم إزالة ملفات تعريف البريد الإلكتروني ورسائل البريد الإلكتروني المخزنة مؤقتا، اعتمادا على الجهاز. لمزيد من المعلومات، راجع [ماذا يحدث عند حذف نهج أو إزالة مستخدم من النهج؟](../../admin/basic-mobility-security/create-device-security-policies.md)

## <a name="remove-user-security-groups-from-basic-mobility-and-security-device-policies"></a>إزالة مجموعات أمان المستخدم من نهج الأجهزة الأساسية للتنقل والأمان

1. في نوع المستعرض: [https://compliance.microsoft.com/basicmobilityandsecurity](https://compliance.microsoft.com/basicmobilityandsecurity).

2. حدد نهج الجهاز، وحدد **تحرير النهج**.

3. في صفحة **النشر** ، حدد **"إزالة**".

4. ضمن **المجموعات**، حدد مجموعة أمان.

5. حدد **"إزالة**"، وحدد **"حفظ**".

## <a name="remove-basic-mobility-and-security-device-policies"></a>إزالة نهج الأجهزة الأساسية للتنقل والأمان

1. في نوع المستعرض: [https://compliance.microsoft.com/basicmobilityandsecurity](https://compliance.microsoft.com/basicmobilityandsecurity).

2. حدد نهج الجهاز، ثم حدد **"حذف النهج**".

3. في مربع الحوار "تحذير"، حدد **"نعم**".

> [!NOTE]
> لمزيد من الخطوات لإلغاء حظر الأجهزة إذا كانت أجهزة مؤسستك لا تزال في حالة حظر، راجع منشور [المدونة "إزالة التحكم بالوصول" من Mobile Device Management لـ Office 365](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Removing-Access-Control-from-Mobile-Device-Management-for-Office/ba-p/279934).
