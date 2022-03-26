---
title: متطلبات Microsoft 365 المنارة
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
description: بالنسبة لموفري الخدمات المدارة (MSPs)، احصل على قائمة بالمتطلبات لاستخدام Microsoft 365 المنارة.
ms.openlocfilehash: b26eb34c728121b4c6f2474dd52aa2a6824d92d6
ms.sourcegitcommit: 9c8eca862a2f0fdca7a66c641e382e37fcaefa10
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/24/2022
ms.locfileid: "63775401"
---
# <a name="requirements-for-microsoft-365-lighthouse"></a>متطلبات Microsoft 365 المنارة

Microsoft 365 Lighthouse هو مدخل مسؤول يساعد موفري الخدمات المدارة (MSPs) على حماية الأجهزة والبيانات والمستخدمين وإدارتها على نطاق واسع لعملاء الشركات الصغيرة والمتوسطة الحجم (SMB).  

يجب أن يكون MSPs مسجلا في برنامج Cloud Solution Provider (CSP) ك بائع غير مباشر أو شريك فاتورة مباشرة لاستخدام المنارة.  

بالإضافة إلى ذلك، يجب أن يكون كل مستأجر عميل MSP مؤهلا ل "المنارة" من خلال تلبية المتطلبات التالية:
 
- يجب أن يكون لديك حق وصول مفوض تم إعداده لموفر الخدمة المدارة (MSP) لكي يتمكن من إدارة مستأجر العميل*
- يجب أن يكون لديك ترخيص Microsoft 365 Business Premium أو Microsoft 365 E3 أو Windows 365 Business
- يجب ألا يكون هناك أكثر من 1000 مستخدم مرخص

*امتيازات المسؤول المفوض (DAP) مطلوبة لتكئب العملاء على المنارة. نوصي أيضا بإنشاء امتيازات المسؤول المفوض (GDAP) مع العملاء لتمكين وصول مفوض أكثر أمانا. بينما يكون DAP و GDAP مترابطين، فإن GDAP سيكون له الأسبقية للعملاء حيث يكون النموذجان في مكانهما. قريبا، سيتمكن العملاء الذين لا يوجد معهم سوى GDAP (بدون DAP) من التمكن من الوصول إلى المنارة.

## <a name="requirements-for-enablingdevice-management"></a>متطلبات تمكين إدارة الأجهزة

لعرض أجهزة مستأجر العميل على صفحات إدارة الأجهزة، يجب أن يقوم MSP بما يلي:

- تسجيل جميع أجهزة العملاء في إدارة نقاط النهاية من Microsoft (MEM).لمزيد من المعلومات، راجع [تسجيل الأجهزة في Microsoft Intune](/mem/intune/enrollment/).
- تعيين سياسات التوافق إلى جميع أجهزة العملاء.لمزيد من المعلومات، راجع [إنشاء نهج توافق في Microsoft Intune](/mem/intune/protect/create-compliance-policy).

## <a name="requirements-for-enabling-usermanagement"></a>متطلبات تمكين إدارة المستخدمين

لكي تظهر بيانات العملاء في تقارير على صفحات إدارة المستخدمين، بما في ذلك المستخدمون الخطرون والمصادقة متعددة العوامل وإعادة تعيين كلمة المرور، يجب أن يكون لدى مستأجري العملاء تراخيص Azure Active Directory Premium P1 أو إصدار لاحق. يتم تضمين azure AD Premium P1 مع Microsoft 365 Business Premium Microsoft 365 E3.

## <a name="requirements-for-enablingthreat-management"></a>متطلبات تمكين إدارة المخاطر

لعرض أجهزة مستأجري العملاء والتهديدات على صفحات إدارة المخاطر، يجب تسجيل جميع أجهزة مستأجري العملاء في إدارة نقاط النهاية من Microsoft (MEM) وحمايتهم عن طريق تشغيل برنامج الحماية من الفيروسات من Microsoft Defender.  

لمزيد من المعلومات، راجع [تسجيل الأجهزة في Microsoft Intune](/mem/intune/enrollment/).  

برنامج الحماية من الفيروسات من Microsoft Defender جزء من نظام Windows، كما أنه يتم تمكينه بشكل افتراضي على الأجهزة التي تعمل Windows 10.  

> [!NOTE]
> إذا كنت تستخدم حلا من برامج الحماية من الفيروسات غير Microsoft وليس برنامج الحماية من الفيروسات من Microsoft Defender، برنامج الحماية من الفيروسات من Microsoft Defender تلقائيا. عندما تقوم ب إلغاء تثبيت حل مكافحة الفيروسات برنامج الحماية من الفيروسات من Microsoft Defender Microsoft، يتم تنشيط البرنامج تلقائيا لحماية Windows من التهديدات.

## <a name="related-content"></a>المحتوى ذي الصلة

[تكوين Microsoft 365 مدخل المنارة](m365-lighthouse-configure-portal-security.md) (مقالة)\
[Microsoft 365 نظرة عامة حول توافق جهاز المنارة](m365-lighthouse-device-compliance-page-overview.md) (مقالة)\
[Microsoft 365 نظرة عامة على صفحة مستخدمي المنارة](m365-lighthouse-users-page-overview.md) (مقالة)\
[Microsoft 365 نظرة عامة حول إدارة المخاطر في المنارة](m365-lighthouse-threat-management-page-overview.md) (مقالة)\
[Microsoft 365 الأسئلة الشائعة حول المنارة](m365-lighthouse-faq.yml)  (مقالة)

