---
title: حول إعدادات ملف تعريف Autopilot
ms.author: deniseb
author: denisebmsft
manager: dansimp
audience: Admin
ms.topic: conceptual
f1.keywords:
- ZTDProfileSettings
- O365E_ZTDProfileSettings
- BCS365_ZTDProfileSettings
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
- OKR_SMB_M365
- AdminSurgePortfolio
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: 99bfbf81-e719-4630-9b0f-c187edfa1f8a
description: تساعدك ملفات تعريف Autopilot على التحكم في كيفية تثبيت Windows على أجهزة المستخدم. تحتوي ملفات التعريف على إعدادات افتراضية واختيارية مثل تخطي تثبيت Cortana.
ms.openlocfilehash: 387346c68ad9ff85c3f97e4d8ca8b0ccdb28dcbd
ms.sourcegitcommit: d1b60ed9a11f5e6e35fbaf30ecaeb9dfd6dd197d
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 06/29/2022
ms.locfileid: "66857445"
---
# <a name="about-autopilot-profile-settings"></a>حول إعدادات ملف تعريف Autopilot

## <a name="autopilot-profile-settings"></a>إعدادات ملف تعريف AutoPilot

يمكنك استخدام ملفات تعريف Autopilot للتحكم في كيفية تثبيت Windows على أجهزة المستخدم. تحتوي ملفات التعريف على الإعدادات التالية.
  
## <a name="autopilot-default-features-required-that-are-set-automatically"></a>ميزات Autopilot الافتراضية (مطلوبة) التي يتم تعيينها تلقائيا
  
| اعداد | الوصف |
|:-----|:-----|
|تخطي تسجيل Cortana وOneDrive وOEM  |يتخطى تثبيت تطبيقات المستهلكين مثل Cortana وOneDrive الشخصي. يمكن لمستخدم الجهاز تثبيتها لاحقا طالما أن المستخدم مسؤول محلي على الجهاز. يتم تخطي تسجيل الشركة المصنعة الأصلية لأنه ستتم إدارة الجهاز بواسطة Microsoft 365 Business Premium.  |
|تجربة تسجيل الدخول باستخدام العلامة التجارية لشركتك  |إذا كانت شركتك تملك [علامة تجارية لشركتك إلى صفحة تسجيل الدخول إلى Microsoft 365](../admin/setup/customize-sign-in-page.md)، فسيحصل مستخدم الجهاز على هذه التجربة عند تسجيل الدخول.  |
|التسجيل التلقائي ل MDM باستخدام حسابات AAD المكونة.  |ستتم إدارة هوية المستخدم بواسطة Azure Active Directory، وسيسجل المستخدمون الدخول إلى Windows وMicrosoft 365 باستخدام بيانات اعتماد Microsoft 365 Business Premium الخاصة بهم.  |

## <a name="optional-settings"></a>الإعدادات الاختيارية
  
| اعداد | الوصف |
|:-----|:-----|
|تخطي إعدادات الخصوصية (إيقاف التشغيل بشكل افتراضي)  |إذا تم تعيين هذا الخيار إلى **"تشغيل**"، فلن يرى مستخدم الجهاز اتفاقية ترخيص الجهاز وWindows عند تسجيل الدخول لأول مرة.  |
|عدم السماح للمستخدم بأن يصبح المسؤول المحلي  |إذا تم تعيين هذا الخيار إلى **"تشغيل**"، فلن يتمكن مستخدم الجهاز من تثبيت أي تطبيقات شخصية، مثل Cortana.|

## <a name="see-also"></a>راجع أيضًا

[أفضل الممارسات لتأمين خطط Microsoft 365 للأعمال](../admin/security-and-compliance/secure-your-business-data.md)