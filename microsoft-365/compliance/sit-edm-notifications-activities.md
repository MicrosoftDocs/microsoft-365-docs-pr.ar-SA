---
title: إنشاء إعلامات لأنشطة مطابقة البيانات الدقيقة
f1.keywords:
- NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.date: ''
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
search.appverid:
- MOE150
- MET150
description: تعرف على كيفية إنشاء إعلامات لأنشطة مطابقة البيانات بدقة.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: e5f7c2a2d724a66aea1ce55658ff84e6e0da4738
ms.sourcegitcommit: 39838c1a77d4e23df56af74059fb95970223f718
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 01/24/2022
ms.locfileid: "63569531"
---
# <a name="create-notifications-for-exact-data-match-activities"></a>إنشاء إعلامات لأنشطة مطابقة البيانات الدقيقة

عند إنشاء [أنواع معلومات حساسة مخصصة](sit-learn-about-exact-data-match-based-sits.md#learn-about-exact-data-match-based-sensitive-information-types) ذات تطابق دقيق للبيانات (EDM)، يتم إنشاء عدد من الأنشطة في [سجل التدقيق](search-the-audit-log-in-security-and-compliance.md#before-you-search-the-audit-log). يمكنك استخدام [الأمر Cmdlet New-ProtectionAlert](/powershell/module/exchange/new-protectionalert) PowerShell لإنشاء إعلامات تعلمك عند حدوث هذه الأنشطة:

- CreateSchema
- EditSchema
- RemoveSchema
- UploadDataFailed
- UploadDataCompleted

> [!NOTE]
 تتوفر إمكانية إنشاء إعلامات لأنشطة EDM لسحابات العالم سحابة القطاع الحكومي فقط.

## <a name="pre-requisites"></a>المتطلبات الأساسية

يجب أن يكون الحساب الذي تستخدمه واحدا من ما يلي:

- مسؤول عام
- مسؤول التوافق
- Exchange Online مسؤول

لمعرفة المزيد حول أذونات DLP، راجع [الأذونات](data-loss-prevention-policies.md#permissions).

يتم تضمين التصنيف المستند إلى EDM في هذه الاشتراكات:

- Office 365 E5
- Microsoft 365 E5
- التوافق في Microsoft 365 E5
- إدارة وحماية المعلومات في Microsoft E5/A5

لمعرفة المزيد حول ترخيص DLP، راجع Microsoft 365 [إرشادات الترخيص لتوافق & الأمان](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#information-protection).

## <a name="configure-notifications-for-edm-activities"></a>تكوين الإعلامات لأنشطة EDM

1. الاتصال [إلى مركز & التوافق PowerShell](/powershell/exchange/connect-to-scc-powershell).

2. قم بتشغيل `New-ProtectionAlert` الأمر cmdlet باستخدام النشاط الذي تريد إنشاء الإعلام له.  على سبيل المثال، إذا كنت تريد أن يتم إعلامك عند حدوث الإجراء **UploadDataCompleted** ، ف قم بتشغيل:

    ```powershell
    New-ProtectionAlert -Name "EdmUploadCompleteAlertPolicy" -Category Others -NotifyUser <address to send notification to> -ThreatType Activity -Operation UploadDataCompleted -Description "Custom alert policy to track when EDM upload Completed" -AggregationType None
    ```
    
    بالنسبة إلى **UploadDataFailed** ، يمكنك تشغيل:
    
    ```powershell
    New-ProtectionAlert -Name "EdmUploadFailAlertPolicy" -Category Others -NotifyUser <SMTP address to send notification to> -ThreatType Activity -Operation UploadDataFailed -Description "Custom alert policy to track when EDM upload Failed" -AggregationType None -Severity High
    ```

## <a name="related-articles"></a>المقالات ذات الصلة

- [التعرف على أنواع المعلومات الحساسة المستندة إلى مطابقة البيانات بدقة](sit-learn-about-exact-data-match-based-sits.md#learn-about-exact-data-match-based-sensitive-information-types)
- [New-ProtectionAlert](/powershell/module/exchange/new-protectionalert)