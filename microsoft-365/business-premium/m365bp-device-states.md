---
title: حالات الجهاز
f1.keywords:
- NOCSH
ms.author: deniseb
author: denisebmsft
manager: dansimp
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
ms.localizationpriority: high
ms.collection:
- Adm_O365
- M365-subscription-management
- M365-identity-device-management
- Adm_TOC
ms.custom:
- Adm_O365
- Core_O365Admin_Migration
- MiniMaven
- MSB365
- seo-marvel-mar
- AdminSurgePortfolio
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: c3ac23c5-d4b4-4b1b-b7ce-ea759521bf8c
description: تعرف على حالات الأجهزة المختلفة في قائمة إجراءات الجهاز في مسؤول home في Microsoft 365 للأعمال.
ms.openlocfilehash: 07024ea6f4e37e32716c8af3e56f4481104ed975
ms.sourcegitcommit: d1b60ed9a11f5e6e35fbaf30ecaeb9dfd6dd197d
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 06/29/2022
ms.locfileid: "66857442"
---
# <a name="device-states-in-microsoft-365-for-business"></a>حالات الجهاز في Microsoft 365 للأعمال

تنطبق هذه المقالة على Microsoft 365 Business Premium.

> [!NOTE]
> يتم طرح Microsoft Defender for Business للعملاء Microsoft 365 Business Premium، بدءا من 1 مارس 2022. يوفر هذا العرض ميزات أمان إضافية للأجهزة. [Mer informasjon حول Defender for Business](../security/defender-business/mdb-overview.md).

يمكن أن تحتوي الأجهزة الموجودة في قائمة **إجراءات الجهاز** (مسؤول **إجراءات الجهاز** الرئيسي\>) على الحالات التالية.
  
![في قائمة إجراءات الجهاز، يمكنك رؤية حالات الأجهزة.](./../media/a621c47e-45d9-4e1a-beb9-c03254d40c1d.png)
  
|**حاله**|**الوصف**|
|:-----|:-----|
|مدار من قبل Intune  |تتم إدارته بواسطة Microsoft 365 Business Premium.  |
|إيقاف معلق  |Microsoft 365 Business Premium تستعد لإزالة بيانات الشركة من الجهاز.  |
|إيقاف قيد التقدم  |يقوم Microsoft 365 Business Premium حاليا بإزالة بيانات الشركة من الجهاز.  |
|فشل التوقف  | فشل إجراء إزالة بيانات الشركة.  |
|تم إلغاء إيقافه  |تم إلغاء إجراء إيقاف.  |
|المسح معلق  |في انتظار إعادة تعيين المصنع للبدء.  |
|المسح قيد التقدم  |تم إصدار إعادة تعيين المصنع.  |
|فشل المسح  |تعذرت إعادة تعيين المصنع.  |
|تم إلغاء المسح  |تم إلغاء مسح المصنع.  |
|صحيه  |هناك إجراء معلق (أو قيد التقدم)، ولكن الجهاز لم يتم إيداعه لمدة أكثر من 30 يوما.  |
|حذف معلق  |تم تعليق إجراء الحذف.  |
|اكتشف  |لقد كشف Microsoft 365 Business Premium عن الجهاز.  |
   

## <a name="see-also"></a>راجع أيضًا

[أفضل الممارسات لتأمين خطط Microsoft 365 للأعمال](../admin/security-and-compliance/secure-your-business-data.md)