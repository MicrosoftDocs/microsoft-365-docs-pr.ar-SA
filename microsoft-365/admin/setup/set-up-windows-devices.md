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
description: إعداد أجهزة Windows تعمل Windows 10 Pro للمستخدمين Microsoft 365 Business Premium، ما يتيح الإدارة المركزية وعناصر التحكم في الأمان.
ms.openlocfilehash: 57db37f73d2b9145f7c4fb9c1ee1005318c629d7
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/27/2022
ms.locfileid: "65096215"
---
# <a name="set-up-windows-devices-for-microsoft-365-business-premium-users"></a>إعداد أجهزة Windows لمستخدمي Microsoft 365 Business Premium

## <a name="before-you-begin"></a>قبل البدء

قبل أن تتمكن من إعداد أجهزة Windows للمستخدمين Microsoft 365 Business Premium، تأكد من تشغيل جميع أجهزة Windows Windows 10 Pro أو الإصدار 1703 (تحديث المبدعين) أو Windows 11 Pro. 

يعد Windows 10 Pro (أو Windows 11 Pro) شرطا أساسيا لنشر Windows 10 Business، وهي مجموعة من الخدمات السحابية وقدرات إدارة الأجهزة التي تكمل Windows 10 Pro Windows 11 Pro ، وتمكين الإدارة المركزية وعناصر التحكم الأمنية Microsoft 365 Business Premium.

[تعرف على المزيد حول متطلبات Microsoft 365 Business Premium](https://www.microsoft.com/microsoft-365/business/microsoft-365-business-premium?activetab=pivot:techspecstab).

## <a name="windows-10-pro-and-windows-11-pro"></a>Windows 10 Pro Windows 11 Pro

إذا كان لديك أجهزة Windows تعمل بإصدارات سابقة من Windows، مثل Windows 7 Pro أو Windows 8 Pro أو Windows 8.1 Pro، فإن اشتراكك في Microsoft 365 Business Premium يحق لك قم بترقية هذه الأجهزة إلى Windows 10 Pro أو Windows 11 Pro.
  
لمزيد من المعلومات حول كيفية ترقية Windows الأجهزة، راجع المقالات التالية:

- [ترقية Windows Home إلى Windows Pro](https://support.microsoft.com/windows/upgrade-windows-home-to-windows-pro-ef34d520-e73f-3198-c525-d1a218cc2818)
- [الترقية إلى Windows 10 Pro](https://support.microsoft.com/windows/upgrade-to-windows-10-pro-71ecc746-0f81-a4c0-bd4b-0db8559e0796)
  
بعد الترقية، راجع [التحقق من اتصال الجهاز ب Azure AD](#verify-the-device-is-connected-to-azure-ad) للتحقق من حصولك على الترقية، أو للتأكد من عمل الترقية.

## <a name="join-windows-devices-to-your-organizations-azure-ad"></a>الانضمام Windows الأجهزة إلى Azure AD الخاص بمؤسستك

عندما تعمل جميع أجهزة Windows الخاصة بشركتك Windows 10 Pro أو Windows 11 Pro، يمكنك ضم هذه الأجهزة إلى Azure Active Directory (Azure AD) الخاص بمؤسستك. 

1. على جهاز Windows، حدد شعار Windows، ثم أيقونة الإعدادات.
  
2. في **الإعدادات**، انتقل إلى **الاتصال** **العمل أو المؤسسة التعليمية** \> في **AccountsAccess** > .
  
3. اكتب عنوان بريدك الإلكتروني، ثم اختر **"التالي**".

4. اتبع المطالبات لإكمال العملية.

## <a name="verify-the-device-is-connected-to-azure-ad"></a>التحقق من اتصال الجهاز ب Azure AD

للتحقق من حالة المزامنة، في صفحة **Access للعمل أو المؤسسة التعليمية** في **الإعدادات**، حدد المنطقة **"متصل ب** _ \<organization name\> _" لعرض الزرين **"معلومات**" و"**قطع اتصال**". اختر **"معلومات** " للحصول على حالة المزامنة. 
  
في صفحة **حالة المزامنة** ، اختر **"مزامنة** " للحصول على أحدث نهج إدارة الأجهزة المحمولة على الكمبيوتر الشخصي.  
  
## <a name="next-steps"></a>الخطوات التالية

لإعداد أجهزتك المحمولة، راجع [إعداد الأجهزة المحمولة لمستخدمي Microsoft 365 Business Premium](set-up-mobile-devices.md)، 

لزيادة الحماية، راجع [أفضل 10 طرق لتأمين Microsoft 365 لخطط الأعمال](../security-and-compliance/secure-your-business-data.md).
  

