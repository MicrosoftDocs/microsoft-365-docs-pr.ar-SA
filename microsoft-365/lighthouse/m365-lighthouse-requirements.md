---
title: متطلبات Microsoft 365 Lighthouse
f1.keywords: CSH
ms.author: sharik
author: SKjerland
manager: scotv
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
ms.openlocfilehash: d5f04c39cbce9726fefa4b410be63cd5ee4e959d
ms.sourcegitcommit: 195e4734d9a6e8e72bd355ee9f8bca1f18577615
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/13/2022
ms.locfileid: "64823663"
---
# <a name="requirements-for-microsoft-365-lighthouse"></a>متطلبات Microsoft 365 Lighthouse

Microsoft 365 Lighthouse هو مدخل مسؤول يساعد موفري الخدمات المدارة (MSPs) على تأمين وإدارة الأجهزة والبيانات والمستخدمين على نطاق واسع لعملاء الأعمال الصغيرة والمتوسطة الحجم (SMB).

يجب تسجيل MSPs في برنامج Cloud Solution Provider (CSP) كبائعين غير مباشرين أو شريك Direct Bill لاستخدام Lighthouse.

بالإضافة إلى ذلك، يجب أن يكون كل مستأجر عميل MSP مؤهلا ل Lighthouse من خلال تلبية المتطلبات التالية:

- يجب أن يكون قد تم إعداد الوصول المفوض لموفر الخدمة المدارة (MSP) لكي يتمكن من إدارة مستأجر العميل*
- يجب أن يكون لديك ترخيص Microsoft 365 Business Premium أو Microsoft 365 E3 أو Windows 365 Business واحد على الأقل
- يجب ألا يكون لديك أكثر من 1000 مستخدم مرخص

*مطلوب امتيازات المسؤول المفوض (DAP) لإلحاق العملاء إلى Lighthouse. نوصي أيضا بإنشاء امتيازات المسؤول المفوض متعدد المستويات (GDAP) مع عملائك لتمكين الوصول المفوض بشكل أكثر أمانا. في حين أن DAP وGDAP يتعايشان، فإن GDAP سيكون له الأسبقية للعملاء حيث يوجد كلا النموذجين. قريبا، سيتمكن العملاء الذين يعانون من GDAP فقط (وبدون DAP) من الإلحاق ب Lighthouse.

## <a name="requirements-for-enabling-device-management"></a>متطلبات تمكين إدارة الجهاز

لعرض أجهزة مستأجر العميل على صفحات إدارة الأجهزة، يجب على موفر الخدمات المشتركة (MSP) ما يلي:

- تسجيل جميع أجهزة العملاء في إدارة نقاط النهاية من Microsoft (MEM). لمزيد من المعلومات، راجع [تسجيل الأجهزة في Microsoft Intune](/mem/intune/enrollment/).
- تعيين نهج التوافق لجميع أجهزة العملاء. لمزيد من المعلومات، راجع [إنشاء نهج توافق في Microsoft Intune](/mem/intune/protect/create-compliance-policy).

## <a name="requirements-for-enabling-user-management"></a>متطلبات تمكين إدارة المستخدم

لكي تظهر بيانات العميل في التقارير على صفحات إدارة المستخدم، بما في ذلك المستخدمين المعرضين للمخاطر والمصادقة متعددة العوامل وإعادة تعيين كلمة المرور، يجب أن يكون لدى مستأجري العملاء تراخيص ل Azure Active Directory Premium P1 أو أحدث. يتم تضمين Azure AD Premium P1 مع Microsoft 365 Business Premium Microsoft 365 E3.

## <a name="requirements-for-enabling-threat-management"></a>متطلبات تمكين إدارة التهديدات

لعرض أجهزة المستأجر العميل والتهديدات على صفحات إدارة التهديدات، يجب عليك تسجيل جميع أجهزة مستأجر العميل في إدارة نقاط النهاية من Microsoft (MEM) وحمايتها عن طريق تشغيل برنامج الحماية من الفيروسات من Microsoft Defender.

لمزيد من المعلومات، راجع [تسجيل الأجهزة في Microsoft Intune](/mem/intune/enrollment/).

برنامج الحماية من الفيروسات من Microsoft Defender هو جزء من نظام التشغيل Windows ويتم تمكينه بشكل افتراضي على الأجهزة التي تعمل Windows 10.

> [!NOTE]
> إذا كنت تستخدم حل الحماية من الفيروسات غير التابع ل Microsoft وليس برنامج الحماية من الفيروسات من Microsoft Defender، يتم تعطيل برنامج الحماية من الفيروسات من Microsoft Defender تلقائيا. عند إلغاء تثبيت حل الحماية من الفيروسات غير التابع ل Microsoft، يتم تنشيط برنامج الحماية من الفيروسات من Microsoft Defender تلقائيا لحماية أجهزة Windows من التهديدات.

## <a name="related-content"></a>محتوى ذي صلة

[تكوين أمان مدخل Lighthouse Microsoft 365](m365-lighthouse-configure-portal-security.md) (مقالة)\
[Microsoft 365 نظرة عامة على صفحة توافق جهاز Lighthouse](m365-lighthouse-device-compliance-page-overview.md) (مقالة)\
[Microsoft 365 نظرة عامة على صفحة مستخدمي Lighthouse](m365-lighthouse-users-page-overview.md) (مقالة)\
[نظرة عامة على صفحة إدارة المخاطر Microsoft 365 Lighthouse](m365-lighthouse-threat-management-page-overview.md) (مقالة)\
[الأسئلة المتداولة حول Microsoft 365 Lighthouse](m365-lighthouse-faq.yml) (مقالة)
