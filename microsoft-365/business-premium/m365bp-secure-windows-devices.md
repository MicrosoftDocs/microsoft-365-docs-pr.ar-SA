---
title: تأمين أجهزة Windows
f1.keywords:
- CSH
ms.author: deniseb
author: denisebmsft
manager: dansimp
audience: Admin
ms.topic: conceptual
f1_keywords:
- O365E_BCSSetup4WindowsConfig
ms.service: o365-administration
ms.localizationpriority: high
ms.collection:
- M365-subscription-management
- M365-identity-device-management
ms.custom:
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
ROBOTS: NO INDEX, NO FOLLOW
ms.assetid: 21e5551f-fa35-4f13-9418-f80d668b6a2b
description: تعرف على كيفية تكوين إعدادات نهج الجهاز الافتراضي الذي سيتلقاه أي جهاز Windows عند تسجيل الدخول إلى حساب العمل أو المؤسسة التعليمية.
ms.openlocfilehash: 5ac09788d609752d12a6ae6efadfa8739c5a4f9a
ms.sourcegitcommit: c216ffa5da8f431e4380bb133a234ae7d94144c7
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 06/04/2022
ms.locfileid: "65893072"
---
# <a name="secure-windows-devices"></a>تأمين أجهزة Windows

الهدف هنا هو تكوين الإعدادات التي تعد جزءا من نهج الجهاز الافتراضي لنظام التشغيل Windows 10 أو 11. سيتلقى جميع المستخدمين الذين يقومون بتوصيل جهاز Windows، بما في ذلك الأجهزة المحمولة وأجهزة الكمبيوتر الشخصية، عن طريق تسجيل الدخول باستخدام حساب العمل الخاص بهم هذه الإعدادات تلقائيا. نوصي بقبول النهج الافتراضي أثناء الإعداد وإضافة نهج لاحقا تستهدف مجموعات معينة من المستخدمين.

## <a name="before-you-begin"></a>قبل البدء

قبل أن تتمكن من إعداد أجهزة Windows لمستخدمي Microsoft 365 Business Premium، تأكد من أن جميع أجهزة Windows تعمل بنظام التشغيل Windows 10 Pro أو الإصدار 1703 (تحديث المبدعين) أو Windows 11 Pro.

يعد Windows 10 Pro (أو Windows 11 Pro) شرطا أساسيا لنشر Windows 10 Business، وهو عبارة عن مجموعة من الخدمات السحابية وقدرات إدارة الأجهزة التي تكمل Windows 10 Pro وWindows 11 Pro، وتمكن الإدارة المركزية وعناصر التحكم في الأمان من Microsoft 365 Business Premium.

[تعرف على المزيد حول متطلبات Microsoft 365 Business Premium](https://www.microsoft.com/microsoft-365/business/microsoft-365-business-premium?activetab=pivot:techspecstab).

## <a name="windows-10-pro-and-windows-11-pro"></a>Windows 10 Pro وWindows 11 Pro

إذا كانت لديك أجهزة Windows تعمل بإصدارات سابقة من Windows، مثل Windows 7 Pro أو Windows 8 Pro أو Windows 8.1 Pro، فإن اشتراكك في Microsoft 365 Business Premium يؤهلك لترقية هذه الأجهزة إلى Windows 10 Pro أو Windows 11 Pro.
  
لمزيد من المعلومات حول كيفية ترقية أجهزة Windows، راجع المقالات التالية:

- [ترقية Windows Home إلى Windows 10 أو Windows 11 Pro](https://support.microsoft.com/windows/upgrade-windows-home-to-windows-pro-ef34d520-e73f-3198-c525-d1a218cc2818)
- [الترقية إلى Windows 10 Pro](https://support.microsoft.com/windows/upgrade-to-windows-10-pro-71ecc746-0f81-a4c0-bd4b-0db8559e0796)

<!---
Could not find the Win11 equivalent upgrade link.
---> 
  
## <a name="secure-your-windows-10-and-11-devices"></a>تأمين أجهزة Windows 10 و11

تكون كافة الإعدادات قيد **التشغيل** بشكل افتراضي. تتوفر الإعدادات التالية: <br/><br/>

|اعداد  <br/> |الوصف  <br/> |
|:-----|:-----|
|المساعدة في حماية أجهزة الكمبيوتر الشخصية من الفيروسات والتهديدات الأخرى باستخدام برنامج الحماية من الفيروسات من Microsoft Defender  <br/> |يتطلب تشغيل برنامج الحماية من الفيروسات من Microsoft Defender لحماية أجهزة الكمبيوتر من مخاطر الاتصال بالإنترنت.  <br/> |
|المساعدة في حماية أجهزة الكمبيوتر الشخصية من التهديدات المستندة إلى الويب في Microsoft Edge  <br/> |تشغيل الإعدادات في Edge التي تساعد على حماية المستخدمين من المواقع والتنزيلات الضارة.  <br/> |
|المساعدة في حماية الملفات والمجلدات على أجهزة الكمبيوتر الشخصية من الوصول غير المصرح به باستخدام BitLocker  <br/> |يحمي BitLocker البيانات عن طريق تشفير محركات الأقراص الثابتة للكمبيوتر والحماية من تعرض البيانات في حالة فقدان جهاز كمبيوتر أو سرقته. لمزيد من المعلومات، راجع [الأسئلة المتداولة حول BitLocker](/windows/security/information-protection/bitlocker/bitlocker-frequently-asked-questions).  <br/> |
|إيقاف تشغيل شاشة الجهاز عند الخمول لهذا القدر من الوقت  <br/> |التأكد من حماية بيانات الشركة إذا كان المستخدم خاملا. قد يعمل المستخدم في موقع عام، مثل المقهى، ويبتعد أو يتشتت للحظة واحدة، مما يترك جهازه عرضة للنظرات العشوائية. يتيح لك هذا الإعداد التحكم في المدة التي يمكن أن يكون فيها المستخدم خاملا قبل إيقاف تشغيل الشاشة.  <br/> |

## <a name="next-objective"></a>الهدف التالي

[إدارة أجهزة Windows](m365bp-manage-windows-devices.md)
