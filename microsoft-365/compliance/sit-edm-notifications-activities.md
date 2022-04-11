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
description: تعرف على كيفية إنشاء إعلامات لأنشطة مطابقة البيانات الدقيقة.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 163c1386bed2e1f100a42ab8b22b6404fe6bb145
ms.sourcegitcommit: 9ba00298cfa9ae293e4a57650965fdb3e8ffe07b
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/11/2022
ms.locfileid: "64760262"
---
# <a name="create-notifications-for-exact-data-match-activities"></a>إنشاء إعلامات لأنشطة مطابقة البيانات الدقيقة

عند [إنشاء أنواع معلومات حساسة مخصصة مع مطابقة البيانات الدقيقة (EDM)،](sit-learn-about-exact-data-match-based-sits.md#learn-about-exact-data-match-based-sensitive-information-types) هناك عدد من الأنشطة التي يتم إنشاؤها في [سجل التدقيق](search-the-audit-log-in-security-and-compliance.md#before-you-search-the-audit-log). يمكنك استخدام [New-ProtectionAlert](/powershell/module/exchange/new-protectionalert) PowerShell cmdlet لإنشاء إعلامات تعلمك عند حدوث هذه الأنشطة:

- CreateSchema
- EditSchema
- إزالة الكيمياء
- UploadDataFailed
- UploadDataCompleted

> [!NOTE]
 تتوفر القدرة على إنشاء إعلامات لأنشطة EDM للسحابات العالمية سحابة القطاع الحكومي فقط.

## <a name="pre-requisites"></a>المتطلبات الأساسية

يجب أن يكون الحساب الذي تستخدمه واحدا مما يلي:

- مسؤول عام
- مسؤول التوافق
- مسؤول Exchange Online

لمعرفة المزيد حول أذونات DLP، راجع [الأذونات](data-loss-prevention-policies.md#permissions).

يتم تضمين التصنيف المستند إلى EDM في هذه الاشتراكات:

- Office 365 E5
- Microsoft 365 E5
- التوافق في Microsoft 365 E5
- Microsoft E5/A5 حماية البيانات والحوكمة

لمعرفة المزيد حول ترخيص DLP، راجع [Microsoft 365 إرشادات الترخيص للامتثال & الأمان](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#information-protection).

## <a name="configure-notifications-for-edm-activities"></a>تكوين الإعلامات لأنشطة EDM

1. الاتصال إلى [Security & Compliance Center PowerShell](/powershell/exchange/connect-to-scc-powershell).

2. `New-ProtectionAlert` قم بتشغيل cmdlet باستخدام النشاط الذي تريد إنشاء الإعلام له.  على سبيل المثال، إذا كنت تريد أن يتم إعلامك عند حدوث الإجراء **UploadDataCompleted** ، فشغل:

    ```powershell
    New-ProtectionAlert -Name "EdmUploadCompleteAlertPolicy" -Category Others -NotifyUser <address to send notification to> -ThreatType Activity -Operation UploadDataCompleted -Description "Custom alert policy to track when EDM upload Completed" -AggregationType None
    ```
    
    بالنسبة إلى **UploadDataFailed** ، يمكنك تشغيل:
    
    ```powershell
    New-ProtectionAlert -Name "EdmUploadFailAlertPolicy" -Category Others -NotifyUser <SMTP address to send notification to> -ThreatType Activity -Operation UploadDataFailed -Description "Custom alert policy to track when EDM upload Failed" -AggregationType None -Severity High
    ```

## <a name="related-articles"></a>المقالات ذات الصلة

- [التعرّف على أنواع المعلومات الحساسة المستندة إلى مطابقة البيانات بدقة](sit-learn-about-exact-data-match-based-sits.md#learn-about-exact-data-match-based-sensitive-information-types)
- [New-ProtectionAlert](/powershell/module/exchange/new-protectionalert)