---
title: متطلبات Microsoft 365 Lighthouse
f1.keywords: CSH
ms.author: sharik
author: SKjerland
manager: scotv
ms-reviewer: crimora
audience: Admin
ms.topic: article
ms.prod: microsoft-365-lighthouse
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
ms.custom:
- AdminSurgePortfolio
- M365-Lighthouse
search.appverid: MET150
description: بالنسبة لموفري الخدمات المدارة (MSPs)، احصل على قائمة بالمتطلبات لاستخدام Microsoft 365 Lighthouse.
ms.openlocfilehash: 4cea971227f13bf5cf7a59cffa08465e9ed63391
ms.sourcegitcommit: 7e551fa4e9b8b25ed62b5f406143b6b1dae08cbf
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 08/01/2022
ms.locfileid: "67105936"
---
# <a name="requirements-for-microsoft-365-lighthouse"></a>متطلبات Microsoft 365 Lighthouse

Microsoft 365 Lighthouse هو مدخل مسؤول يساعد موفري الخدمات المدارة (MSPs) على تأمين وإدارة الأجهزة والبيانات والمستخدمين على نطاق واسع لعملاء الأعمال الصغيرة والمتوسطة الحجم (SMB).

يجب تسجيل MSPs في برنامج موفر حلول السحابة (CSP) كبائعين غير مباشرين أو شريك Direct Bill لاستخدام Lighthouse.

بالإضافة إلى ذلك، يجب أن يكون كل مستأجر عميل MSP مؤهلا ل Lighthouse من خلال تلبية المتطلبات التالية:

- يجب أن يكون قد تم إعداد الوصول المفوض لموفر الخدمة المدارة (MSP) لكي يتمكن من إدارة مستأجر العميل*
- يجب أن يحتوي على Microsoft 365 Business Premium أو Microsoft 365 E3 أو Microsoft 365 E5 أو Windows 365 Business أو Microsoft Defender for Business واحد على الأقل ترخيص
- يجب ألا يكون لديك أكثر من 2500 مستخدم مرخص

 \*مطلوب إما امتيازات مسؤول متعددة المستويات (GDAP) أو علاقة امتيازات مسؤول مفوض (DAP) لإلحاق العملاء إلى Lighthouse. لم تعد علاقة البائع غير المباشرة مطلوبة لإلحاق Lighthouse. إذا كان DAP وGDAP موجودين في مستأجر عميل، فإن أذونات GDAP لها الأسبقية لفنيي MSP في مجموعات الأمان الممكنة بواسطة GDAP.

## <a name="requirements-for-enabling-device-management"></a>متطلبات تمكين إدارة الجهاز

لعرض أجهزة مستأجر العميل على صفحات إدارة الأجهزة، يجب على موفر الخدمات المشتركة (MSP) ما يلي:

- تسجيل جميع أجهزة العملاء في Microsoft إدارة نقاط النهاية (MEM). لمزيد من المعلومات، راجع [تسجيل الأجهزة في Microsoft Intune](/mem/intune/enrollment/).
- تعيين نهج التوافق لجميع أجهزة العملاء. لمزيد من المعلومات، راجع [إنشاء نهج توافق في Microsoft Intune](/mem/intune/protect/create-compliance-policy).

## <a name="requirements-for-enabling-user-management"></a>متطلبات تمكين إدارة المستخدم

لكي تظهر بيانات العميل في التقارير على صفحات إدارة المستخدم، بما في ذلك المستخدمين المعرضين للمخاطر والمصادقة متعددة العوامل وإعادة تعيين كلمة المرور، يجب أن يكون لدى مستأجري العملاء تراخيص ل Azure Active Directory Premium P1 أو إصدار أحدث. يتم تضمين Azure AD Premium P1 مع Microsoft 365 Business Premium Microsoft 365 E3. يتم تضمين Azure AD Premium P2 مع Microsoft 365 E5.

## <a name="requirements-for-enabling-threat-management"></a>متطلبات تمكين إدارة التهديدات

لعرض أجهزة المستأجر العميل والتهديدات على صفحات إدارة التهديدات، يجب عليك تسجيل جميع أجهزة مستأجر العميل في Microsoft إدارة نقاط النهاية (MEM) وحمايتها عن طريق تشغيل برنامج الحماية من الفيروسات من Microsoft Defender.

لمزيد من المعلومات، راجع [تسجيل الأجهزة في Microsoft Intune](/mem/intune/enrollment/).

يعد برنامج الحماية من الفيروسات من Microsoft Defender جزءا من نظام التشغيل Windows ويتم تمكينه بشكل افتراضي على الأجهزة التي تعمل Windows 10.

> [!NOTE]
> إذا كنت تستخدم حل الحماية من الفيروسات غير التابع ل Microsoft وليس برنامج الحماية من الفيروسات من Microsoft Defender، يتم تعطيل برنامج الحماية من الفيروسات من Microsoft Defender تلقائيا. عند إلغاء تثبيت حل الحماية من الفيروسات غير التابع ل Microsoft، يتم تنشيط برنامج الحماية من الفيروسات من Microsoft Defender تلقائيا لحماية أجهزة Windows من التهديدات.

## <a name="related-content"></a>المحتويات ذات الصلة

[تكوين أمان مدخل Microsoft 365 Lighthouse](m365-lighthouse-configure-portal-security.md) (مقالة)\
[نظرة عامة على صفحة توافق الجهاز في Microsoft 365 Lighthouse](m365-lighthouse-device-compliance-page-overview.md) (مقالة)\
[نظرة عامة على صفحة المستخدمين في Microsoft 365 Lighthouse](m365-lighthouse-users-page-overview.md) (مقال)\
[نظرة عامة على صفحة إدارة المخاطر في Microsoft 365 Lighthouse](m365-lighthouse-threat-management-page-overview.md) (مقال)\
[الأسئلة المتداولة حول Microsoft 365 Lighthouse](m365-lighthouse-faq.yml) (مقالة)
