---
title: إعداد أجهزة Windows لمستخدمي Microsoft 365 Business Premium
f1.keywords:
- CSH
ms.author: deniseb
author: denisebmsft
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- M365-identity-device-management
- Adm_TOC
ms.custom:
- Core_O365Admin_Migration
- MiniMaven
- MSB365
- OKR_SMB_M365
- TRN_M365B
- OKR_SMB_Videos
- seo-marvel-mar
- AdminSurgePortfolio
- okr_smb
- AdminTemplateSet
- adminvideo
search.appverid:
- BCS160
- MET150
ms.assetid: 2d7ff45e-0da0-4caa-89a9-48cabf41f193
description: إعداد أجهزة Windows التي تعمل Windows 10 Pro للمستخدمين Microsoft 365 Business Premium، ما يتيح الإدارة المركزية وعناصر التحكم في الأمان.
ms.openlocfilehash: b9c8a5eb724a74959983e86dcdcb8f2f8f96b540
ms.sourcegitcommit: e6443eb3a4c826792806873428c0c17b59f4fde5
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 06/05/2022
ms.locfileid: "66857364"
---
# <a name="set-up-windows-devices-for-microsoft-365-business-premium-users"></a>إعداد أجهزة Windows لمستخدمي Microsoft 365 Business Premium

## <a name="before-you-begin"></a>قبل البدء

قبل أن تتمكن من إعداد أجهزة Windows لمستخدمي Microsoft 365 Business Premium، تأكد من تشغيل جميع أجهزة Windows Windows 10 Pro أو الإصدار 1703 (تحديث المبدعين) أو Windows 11 Pro. 

يعد Windows 10 Pro (أو Windows 11 Pro) شرطا أساسيا لنشر Windows 10 Business، وهي مجموعة من الخدمات السحابية وقدرات إدارة الأجهزة التي تكمل Windows 10 Pro Windows 11 Pro ، وتمكين الإدارة المركزية وعناصر التحكم الأمنية Microsoft 365 Business Premium.

[Mer informasjon حول متطلبات Microsoft 365 Business Premium](https://www.microsoft.com/microsoft-365/business/microsoft-365-business-premium?activetab=pivot:techspecstab).

## <a name="windows-10-pro-and-windows-11-pro"></a>Windows 10 Pro Windows 11 Pro

إذا كانت لديك أجهزة Windows تعمل بإصدارات سابقة من Windows، مثل Windows 7 Pro أو Windows 8 Pro أو Windows 8.1 Pro، فإن اشتراكك في Microsoft 365 Business Premium يؤهلك لترقية هذه الأجهزة إلى Windows 10 Pro أو Windows 11 Pro.
  
لمزيد من المعلومات حول كيفية ترقية أجهزة Windows، راجع المقالات التالية:

- [ترقية Windows Home إلى Windows Pro](https://support.microsoft.com/windows/upgrade-windows-home-to-windows-pro-ef34d520-e73f-3198-c525-d1a218cc2818)
- [الترقية إلى Windows 10 Pro](https://support.microsoft.com/windows/upgrade-to-windows-10-pro-71ecc746-0f81-a4c0-bd4b-0db8559e0796)
  
بعد الترقية، راجع [التحقق من اتصال الجهاز Azure AD](#verify-the-device-is-connected-to-azure-ad) للتحقق من حصولك على الترقية، أو للتأكد من عمل الترقية.

## <a name="join-windows-devices-to-your-organizations-azure-ad"></a>انضم إلى أجهزة Windows إلى Azure AD مؤسستك

عند تشغيل جميع أجهزة Windows الخاصة بشركتك Windows 10 Pro أو Windows 11 Pro، يمكنك ضم هذه الأجهزة إلى Azure Active Directory الخاص بمؤسستك (Azure AD). 

1. على جهاز Windows، حدد شعار Windows، ثم أيقونة الإعدادات.
  
2. في **الإعدادات**، انتقل إلى **Accounts** > **Access work أو school** \> **Connect**.
  
3. اكتب عنوان بريدك الإلكتروني، ثم اختر **"التالي**".

4. اتبع المطالبات لإكمال العملية.

## <a name="verify-the-device-is-connected-to-azure-ad"></a>تحقق من اتصال الجهاز Azure AD

للتحقق من حالة المزامنة، في صفحة **Access للعمل أو المؤسسة التعليمية** في **"الإعدادات"**، حدد المنطقة **"متصل ب** _ \<organization name\> _" لعرض الزرين **"معلومات** " و" **قطع الاتصال**". اختر **"معلومات** " للحصول على حالة المزامنة. 
  
في صفحة **حالة المزامنة** ، اختر **"مزامنة** " للحصول على أحدث نهج إدارة الأجهزة المحمولة على الكمبيوتر الشخصي.  
  
## <a name="next-steps"></a>الخطوات التالية

لإعداد أجهزتك المحمولة، راجع [إعداد الأجهزة المحمولة لمستخدمي Microsoft 365 Business Premium](set-up-mobile-devices.md)، 

لزيادة الحماية، راجع [أفضل الممارسات لتأمين خطط Microsoft 365 للأعمال](../security-and-compliance/secure-your-business-data.md).
  

