---
title: حول إعدادات ملف تعريف AutoPilot
ms.author: efrene
author: efrene
manager: scotv
audience: Admin
ms.topic: conceptual
f1.keywords:
- ZTDProfileSettings
- O365E_ZTDProfileSettings
- BCS365_ZTDProfileSettings
ms.service: o365-administration
ms.localizationpriority: medium
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
description: تساعدك ملفات تعريف AutoPilot على التحكم في Windows تثبيت الملفات على أجهزة المستخدمين. تحتوي ملفات التعريف على إعدادات افتراضية واختيارية مثل تخطي Cortana التثبيت.
ms.openlocfilehash: d0b1a15ef8279234868b94ab5c16e449a54cf62f
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/08/2022
ms.locfileid: "63570811"
---
# <a name="about-autopilot-profile-settings"></a>حول إعدادات ملف تعريف AutoPilot

## <a name="autopilot-profile-settings"></a>إعدادات ملف تعريف AutoPilot

> [!NOTE]
> يتم طرح Microsoft Defender for Business Microsoft 365 Business Premium العملاء، بدءا من 1 مارس 2022. يوفر هذا العرض ميزات أمان إضافية للأجهزة. [تعرف على المزيد حول Defender for Business](../../security/defender-business/mdb-overview.md).

يمكنك استخدام ملفات تعريف AutoPilot للتحكم في Windows تثبيت الملفات على أجهزة المستخدمين. تحتوي ملفات التعريف على الإعدادات التالية.
  
 **ميزات AutoPilot الافتراضية (مطلوبة) التي يتم تعيينها تلقائيا:**
  
|**الإعداد**|**الوصف**|
|:-----|:-----|
|تخطي Cortana تسجيل OneDrive و"الشركة الأصلية"  <br/> |يتخطى تثبيت تطبيقات المستهلكين مثل Cortana الشخصية OneDrive. يمكن لمستخدم الجهاز تثبيتها لاحقا طالما أن المستخدم مسؤول محلي على الجهاز. يتم تخطي تسجيل الشركة المصنعة الأصلية لأنه سيتم إدارة الجهاز بواسطة Microsoft 365 Business Premium.  <br/> |
|تجربة تسجيل الدخول باستخدام العلامة التجارية للشركة  <br/> |إذا كانت شركتك لديها علامة تجارية إضافة شركتك [Microsoft 365](../setup/customize-sign-in-page.md) تسجيل الدخول، فإن مستخدم الجهاز سيحصل على هذه التجربة عند تسجيل الدخول.  <br/> |
|التسجيل التلقائي ل MDM باستخدام حسابات AAD (دليل Azure النشط) تم تكوينها.  <br/> |سيتم إدارة هوية المستخدم بواسطة Azure Active Directory، وسي سجل المستخدمون الدخول إلى Windows Microsoft 365 باستخدام بيانات Microsoft 365 Business Premium الخاصة بهم.  <br/> |
   
 **الإعدادات الاختيارية:**
  
|**الإعداد**|**الوصف**|
|:-----|:-----|
|تخطي إعدادات الخصوصية (إيقاف التشغيل بشكل افتراضي)  <br/> |إذا تم تعيين هذا الخيار إلى **تشغيل**، لن يرى مستخدم الجهاز اتفاقية ترخيص الجهاز وسيرى Windows تسجيل الدخول لأول مرة.  <br/> |
|عدم السماح للمستخدم بأن يصبح المسؤول المحلي  <br/> |إذا تم تعيين هذا الخيار إلى **تشغيل**، لن يتمكن مستخدم الجهاز من تثبيت أي تطبيقات شخصية، مثل Cortana.<br/> |

## <a name="see-also"></a>راجع أيضًا

[أفضل 10 طرق لتأمين Microsoft 365 خطط الأعمال](../security-and-compliance/secure-your-business-data.md)