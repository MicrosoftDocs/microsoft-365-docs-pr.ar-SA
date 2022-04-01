---
title: إنشاء ملفات تعريف AutoPilot وتحريرها
f1.keywords:
- NOCSH
ms.author: efrene
author: efrene
manager: scotv
audience: Admin
ms.topic: article
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
- seo-marvel-mar
- AdminSurgePortfolio
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: 5cf7139e-cfa1-4765-8aad-001af1c74faa
description: تعرف على كيفية إنشاء ملف تعريف AutoPilot وتطبيقه على جهاز، بالإضافة إلى تحرير ملف تعريف أو حذفه أو إزالة ملف تعريف من جهاز.
ms.openlocfilehash: 91df801fb1833c9bfe5f1112e6a3cd5fc8efcf5d
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/08/2022
ms.locfileid: "63579718"
---
# <a name="create-and-edit-autopilot-profiles"></a>إنشاء ملفات تعريف AutoPilot وتحريرها

> [!NOTE]
> يتم طرح Microsoft Defender for Business Microsoft 365 Business Premium العملاء، بدءا من 1 مارس 2022. يوفر هذا العرض ميزات أمان إضافية للأجهزة. [تعرف على المزيد حول Defender for Business](../../security/defender-business/mdb-overview.md).

## <a name="create-a-profile"></a>إنشاء ملف تعريف

ينطبق ملف التعريف على جهاز أو مجموعة من الأجهزة،
  
1. في مركز مسؤولي Microsoft 365، اختر **الأجهزة** \> **AutoPilot**.
  
2. في صفحة **AutoPilot** ، اختر علامة **التبويب ملفات التعريف** إنشاء \> **ملف تعريف**.
    
3. في الصفحة **إنشاء ملف تعريف** ، أدخل اسما لملف التعريف الذي يساعدك على تحديده، على سبيل المثال التسويق. قم تشغيل الإعداد الذي تريده، ثم اختر **حفظ**. لمزيد من المعلومات حول إعدادات ملف تعريف AutoPilot، راجع [حول إعدادات ملف تعريف AutoPilot](autopilot-profile-settings.md).
    
    ![أدخل الاسم ثم قم تشغيل الإعدادات في لوحة إنشاء ملف التعريف.](../../media/63b5a00d-6a5d-48d0-9557-e7531e80702a.png)
  
### <a name="apply-profile-to-a-device"></a>تطبيق ملف تعريف على جهاز

بعد إنشاء ملف تعريف، يمكنك تطبيقه على جهاز أو مجموعة من الأجهزة. يمكنك اختيار ملف تعريف موجود في الدليل خطوة بخطوة [](add-autopilot-devices-and-profile.md) وتطبيقه على الأجهزة الجديدة، أو استبدال ملف تعريف موجود لجهاز أو مجموعة من الأجهزة. 
  
1. في الصفحة **إعداد Windows**، اختر علامة **التبويب** أجهزة. 
    
2. حدد خانة الاختيار إلى جانب  اسم \> الجهاز، وفي لوحة الجهاز،  اختر ملف تعريف من القائمة المنسدل حفظ ملف التعريف **المعين**.
    
    ![في لوحة الجهاز، حدد ملف تعريف معين لتطبيقه.](../../media/ed0ce33f-9241-4403-a5de-2dddffdc6fb9.png)
  
## <a name="edit-delete-or-remove-a-profile"></a>تحرير ملف تعريف أو حذفه أو إزالته

بعد تعيين ملف تعريف إلى جهاز، يمكنك تحديثه، حتى لو قمت بالفعل بتعيين الجهاز إلى مستخدم. عندما يتصل الجهاز بالإنترنت، يتم تنزيل أحدث إصدار من ملف التعريف الخاص بك أثناء عملية الإعداد. إذا قام المستخدم باستعادة جهازه إلى الإعدادات الافتراضية للمصنع، سيعيد الجهاز تنزيل آخر التحديثات لملف التعريف الخاص بك. 
  
### <a name="edit-a-profile"></a>تحرير ملف تعريف

1. في الصفحة **إعداد Windows**، اختر علامة **التبويب ملفات** التعريف. 
    
2. حدد خانة الاختيار بجانب اسم الجهاز، وفي لوحة **ملف التعريف** ، قم بتحديث أي من الإعدادات المتوفرة \> **حفظ**.
    
    إذا قمت بذلك قبل أن يقوم مستخدم بتوصيل الجهاز بالإنترنت، يتم تطبيق ملف التعريف على عملية الإعداد.
    
### <a name="delete-a-profile"></a>حذف ملف تعريف

1. في الصفحة **إعداد Windows**، اختر علامة **التبويب ملفات** التعريف. 
    
2. حدد خانة الاختيار بجانب اسم الجهاز، وفي لوحة **ملف التعريف**، حدد **حذف حفظ ملف التعريف**\>.
    
    عند حذف ملف تعريف، تتم إزالته من جهاز أو مجموعة من الأجهزة التي تم تعيينه لها.
    
### <a name="remove-a-profile"></a>إزالة ملف تعريف

1. في الصفحة **إعداد Windows**، اختر علامة **التبويب** أجهزة. 
    
2. حدد خانة الاختيار إلى جانب اسم الجهاز، وفي لوحة الجهاز،  اختر **بلا**  \> من القائمة المنسدل حفظ ملف التعريف **المعين**.
    
## <a name="see-also"></a>راجع أيضًا

[أفضل 10 طرق لتأمين Microsoft 365 خطط الأعمال](../security-and-compliance/secure-your-business-data.md)