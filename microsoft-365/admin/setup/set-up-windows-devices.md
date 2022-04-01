---
title: إعداد أجهزة Windows للمستخدمين Microsoft 365 Business Premium
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
description: قم بإعداد Windows أجهزة تعمل Windows 10 Pro للمستخدمين Microsoft 365 Business Premium، مما يمكن الإدارة المركزية و عناصر التحكم في الأمان.
ms.openlocfilehash: f64114ac6a117ac3eacc9b6aa9de31366e847f33
ms.sourcegitcommit: 601ab9ad2b624e3b5e04eed927a08884c885c72a
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/24/2022
ms.locfileid: "64403578"
---
# <a name="set-up-windows-devices-for-microsoft-365-business-premium-users"></a>إعداد أجهزة Windows للمستخدمين Microsoft 365 Business Premium

## <a name="before-you-begin"></a>قبل البدء

قبل أن تتمكن من إعداد أجهزة Windows لمستخدمي Microsoft 365 Business Premium، تأكد من تشغيل جميع أجهزة Windows Windows 10 Pro أو الإصدار 1703 (تحديث المبدعين) أو Windows 11 Pro. 

Windows 10 Pro (أو Windows 11 Pro) أحد المتطلبات الأساسية لنشر Windows 10 Business، وهو مجموعة من الخدمات السحابية وإمكانيات إدارة الأجهزة التي تكمل Windows 10 Pro Windows 11 Pro ، وتمكين الإدارة المركزية و عناصر التحكم في الأمان الخاصة Microsoft 365 Business Premium.

[تعرف على المزيد حول متطلبات Microsoft 365 Business Premium](https://www.microsoft.com/microsoft-365/business/microsoft-365-business-premium?activetab=pivot:techspecstab).

## <a name="windows-10-pro-and-windows-11-pro"></a>Windows 10 Pro Windows 11 Pro

إذا كان لديك Windows تعمل بالإصدارات السابقة من Windows، مثل Windows 7 Pro أو Windows 8 Pro أو Windows 8.1 Pro، فإن اشتراكك في Microsoft 365 Business Premium سيحق لك ترقية هذه الأجهزة Windows 10 Pro أو Windows 11 Pro.
  
لمزيد من المعلومات حول كيفية ترقية أجهزة Windows، راجع المقالات التالية:

- [ترقية Windows الصفحة الرئيسية إلى Windows Pro](https://support.microsoft.com/windows/upgrade-windows-home-to-windows-pro-ef34d520-e73f-3198-c525-d1a218cc2818)
- [الترقية إلى Windows 10 Pro](https://support.microsoft.com/windows/upgrade-to-windows-10-pro-71ecc746-0f81-a4c0-bd4b-0db8559e0796)
  
بعد الترقية، راجع التحقق من اتصال الجهاز ب [Azure AD](#verify-the-device-is-connected-to-azure-ad) للتحقق من أن لديك الترقية، أو للتأكد من عمل الترقية.

## <a name="join-windows-devices-to-your-organizations-azure-ad"></a>الانضمام Windows الأجهزة إلى Azure AD الخاص مؤسستك

عند تشغيل جميع أجهزة Windows الخاصة بالشركة Windows 10 Pro أو Windows 11 Pro، يمكنك ضم هذه الأجهزة إلى Azure Active Directory الخاص بالشركة (Azure AD). 

1. على جهاز Windows، حدد Windows، ثم الإعدادات أيقونة.
  
2. في **الإعدادات**، انتقل إلى **AccountsAccesss**  >  للعمل أو **المدرسة**\> الاتصال.
  
3. اكتب عنوان بريدك الإلكتروني، ثم اختر **التالي**.

4. اتبع المطالبات لإكمال العملية.

## <a name="verify-the-device-is-connected-to-azure-ad"></a>التحقق من اتصال الجهاز ب Azure AD

للتحقق من حالة المزامنة، في صفحة **Access** للعمل أو المدرسة في الإعدادات، حدد المنطقة متصل **ب _** \<organization name\> _ للكشف عن الأزرار **معلومات وقطع** **الاتصال**. اختر **معلومات** للحصول على حالة المزامنة. 
  
في صفحة **حالة المزامنة** ، اختر **مزامنة** للحصول على أحدث سياسات إدارة أجهزة المحمول على الكمبيوتر الشخصي.  
  
## <a name="next-steps"></a>الخطوات التالية

لإعداد أجهزتك المحمولة، راجع إعداد الأجهزة [المحمولة للمستخدمين Microsoft 365 Business Premium،](set-up-mobile-devices.md) 

لزيادة الحماية، راجع أفضل [10 طرق لتأمين Microsoft 365 لخطط الأعمال](../security-and-compliance/secure-your-business-data.md).
  
