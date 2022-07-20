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
ms.date: 07/19/2022
ms.custom:
- MiniMaven
search.appverid:
- BCS160
- MET150
- MOE150
description: تعرف على كيفية تكوين إعدادات نهج الجهاز الافتراضي الذي سيتلقاه أي جهاز Windows عند تسجيل الدخول إلى حساب العمل أو المؤسسة التعليمية.
ms.openlocfilehash: f497dab832b9980225be2e689d2c980860a01454
ms.sourcegitcommit: c1eaea74c8ffce2f9f477c9469342e88e4a70c14
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/20/2022
ms.locfileid: "66894866"
---
# <a name="secure-windows-devices"></a>تأمين أجهزة Windows

الهدف هنا هو تكوين الإعدادات التي تعد جزءا من نهج الجهاز الافتراضي Windows 10 أو 11. سيتلقى جميع المستخدمين الذين يقومون بتوصيل جهاز Windows، بما في ذلك الأجهزة المحمولة وأجهزة الكمبيوتر الشخصية، عن طريق تسجيل الدخول باستخدام حساب العمل الخاص بهم هذه الإعدادات تلقائيا. نوصي بقبول النهج الافتراضي أثناء الإعداد وإضافة نهج لاحقا تستهدف مجموعات معينة من المستخدمين.

## <a name="before-you-begin"></a>قبل البدء

قبل أن تتمكن من إعداد أجهزة Windows لمستخدمي Microsoft 365 Business Premium، تأكد من تشغيل جميع أجهزة Windows Windows 10 Pro.

Windows 10 Pro هو شرط أساسي لنشر Windows 10 Business، وهي مجموعة من الخدمات السحابية وقدرات إدارة الأجهزة التي تكمل Windows 10 Pro Windows 11 Pro، وتمكن الإدارة المركزية وعناصر التحكم في الأمان Microsoft 365 Business Premium.

[تعرف على المزيد حول متطلبات Microsoft 365 Business Premium](https://www.microsoft.com/microsoft-365/business/microsoft-365-business-premium?activetab=pivot:techspecstab).

## <a name="windows-10-pro"></a>Windows 10 Pro

إذا كانت لديك أجهزة Windows تعمل بإصدارات سابقة من Windows، مثل Windows 7 Pro أو Windows 8 Pro أو Windows 8.1 Pro، فإن اشتراكك في Microsoft 365 Business Premium يؤهلك لترقية هذه الأجهزة إلى Windows 10 Pro أو Windows 11 Pro.
  
لمزيد من المعلومات حول كيفية ترقية أجهزة Windows، راجع [ترقية أجهزة Windows إلى Windows 10 Pro](m365bp-upgrade-windows-10-pro.md).

## <a name="secure-your-windows-10-and-11-devices"></a>تأمين Windows 10 و11 جهازا

تكون كافة الإعدادات قيد **التشغيل** بشكل افتراضي. تتوفر الإعدادات التالية: <br/><br/>

|اعداد  <br/> |الوصف  <br/> |
|:-----|:-----|
|المساعدة في حماية أجهزة الكمبيوتر الشخصية من الفيروسات والتهديدات الأخرى باستخدام برنامج الحماية من الفيروسات من Microsoft Defender  <br/> |يتطلب تشغيل برنامج الحماية من الفيروسات من Microsoft Defender لحماية أجهزة الكمبيوتر من مخاطر الاتصال بالإنترنت.  <br/> |
|المساعدة في حماية أجهزة الكمبيوتر الشخصية من التهديدات المستندة إلى الويب في Microsoft Edge  <br/> |تشغيل الإعدادات في Edge التي تساعد على حماية المستخدمين من المواقع والتنزيلات الضارة.  <br/> |
|المساعدة في حماية الملفات والمجلدات على أجهزة الكمبيوتر الشخصية من الوصول غير المصرح به باستخدام BitLocker  <br/> |يحمي BitLocker البيانات عن طريق تشفير محركات الأقراص الثابتة للكمبيوتر والحماية من تعرض البيانات في حالة فقدان جهاز كمبيوتر أو سرقته. لمزيد من المعلومات، راجع [الأسئلة المتداولة حول BitLocker](/windows/security/information-protection/bitlocker/bitlocker-frequently-asked-questions).  <br/> |
|إيقاف تشغيل شاشة الجهاز عند الخمول لهذا القدر من الوقت  <br/> |التأكد من حماية بيانات الشركة إذا كان المستخدم خاملا. قد يعمل المستخدم في موقع عام، مثل المقهى، ويبتعد أو يتشتت للحظة واحدة، مما يترك جهازه عرضة للنظرات العشوائية. يتيح لك هذا الإعداد التحكم في المدة التي يمكن أن يكون فيها المستخدم خاملا قبل إيقاف تشغيل الشاشة.  <br/> |

## <a name="next-objective"></a>الهدف التالي

[إدارة أجهزة Windows](m365bp-manage-windows-devices.md)
