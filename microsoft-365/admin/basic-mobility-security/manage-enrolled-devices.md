---
title: إدارة الأجهزة المسجلة في إدارة الجهاز الأجهزة المحمولة في Microsoft 365
f1.keywords:
- NOCSH
ms.author: kwekua
author: kwekua
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
ms.custom:
- AdminSurgePortfolio
- admindeeplinkMAC
search.appverid:
- MET150
description: سجل الدخول إلى Microsoft 365 وإعداد Basic Mobility and Security لاستخدام إدارة الأجهزة المحمولة المضمنة لتأمين الأجهزة المحمولة للمستخدمين وإدارتها.
ms.openlocfilehash: b84c97302743177f0a69978ebf358c0fbd1045a8
ms.sourcegitcommit: 1fa0b15f86470c49dddf0d6de59d553a38ae259b
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 06/03/2022
ms.locfileid: "65863540"
---
# <a name="manage-devices-enrolled-in-mobile-device-management-in-microsoft-365"></a>إدارة الأجهزة المسجلة في إدارة الجهاز الأجهزة المحمولة في Microsoft 365

تساعدك إدارة الأجهزة المحمولة المضمنة Microsoft 365 على تأمين الأجهزة المحمولة للمستخدمين وإدارتها مثل أجهزة iPhone وiPad وAndroid والهواتف Windows. الخطوة الأولى هي تسجيل الدخول إلى Microsoft 365 وإعداد Basic Mobility and Security. لمزيد من المعلومات، راجع [إعداد Basic Mobility and Security](set-up.md).

بعد إعداده، يجب على الأشخاص في مؤسستك تسجيل أجهزتهم في الخدمة. لمزيد من المعلومات، راجع [تسجيل جهازك المحمول باستخدام Basic Mobility and Security](enroll-your-mobile-device.md). ثم يمكنك استخدام Basic Mobility and Security للمساعدة في إدارة الأجهزة في مؤسستك. على سبيل المثال، يمكنك استخدام نهج أمان الجهاز للمساعدة في الحد من الوصول إلى البريد الإلكتروني أو الخدمات الأخرى، وعرض تقارير الأجهزة، ومسح الجهاز عن بعد. ستنتقل عادة إلى مركز توافق & الأمان لتنفيذ هذه المهام. لمزيد من المعلومات، راجع [مدخل التوافق في Microsoft Purview](../../compliance/microsoft-365-compliance-center.md).

## <a name="device-management-tasks"></a>مهام إدارة الجهاز

للوصول إلى لوحة إدارة الجهاز، اتبع الخطوات التالية:

1. سجل الدخول إلى مركز مسؤولي Microsoft 365، وانتقل إلى [صفحة إدارة الجهاز الجوال](https://portal.office.com/adminportal/home?#/MifoDevices).

1. حدد **"لنبدأ**".

## <a name="manage-mobile-devices"></a>إدارة الأجهزة المحمولة

بعد إعداد Basic Mobility and Security، إليك بعض الطرق التي يمكنك من خلالها إدارة الأجهزة المحمولة في مؤسستك.

|للقيام بذلك|قم بذلك|
|---|---|
|مسح جهاز|في لوحة إدارة الجهاز، حدد *اسم الجهاز*، ثم **قم بالمسح الكامل** لحذف كافة المعلومات أو **المسح الانتقائي** لحذف معلومات المؤسسة فقط على الجهاز. لمزيد من المعلومات، راجع [مسح جهاز محمول في Basic Mobility and Security](wipe-mobile-device.md).|
|حظر الأجهزة غير المعتمدة من الوصول إلى البريد الإلكتروني Exchange باستخدام Exchange ActiveSync|في لوحة إدارة الجهاز، حدد **Block**.|
|إعداد نهج الجهاز مثل متطلبات كلمة المرور وإعدادات الأمان|في لوحة إدارة الجهاز، حدد نهج **أمان** >  الجهاز **Add +**. لمزيد من المعلومات، راجع [إنشاء نهج أمان الجهاز في Basic Mobility and Security](create-device-security-policies.md).|
|عرض قائمة الأجهزة المحظورة|في لوحة إدارة الجهاز، ضمن **"تحديد طريقة عرض**"، حدد **"محظور".**|
|إلغاء حظر جهاز غير متوافق أو غير معتمد لمستخدم أو مجموعة من المستخدمين|اختر أحد الإجراءات التالية لإلغاء حظر الأجهزة:<br/>- إزالة المستخدم أو المستخدمين من مجموعة الأمان التي تم تطبيق النهج عليها. انتقل إلى مركز مسؤولي Microsoft 365 > <a href="https://go.microsoft.com/fwlink/p/?linkid=2052855" target="_blank">**Groups**</a>، ثم حدد اسم المجموعة. حدد **"تحرير الأعضاء والمسؤولين**".<br/>- قم بإزالة مجموعة الأمان التي يكون المستخدمون عضوا فيها من نهج الجهاز. انتقل إلى نهج **أمان الجهاز** & Security & Compliance Center > **Security policies** > . حدد اسم نهج الجهاز، ثم حدد **تحرير** > **النشر**.<br/>- إلغاء حظر جميع الأجهزة غير المتوافقة لنهج الجهاز. انتقل إلى نهج **أمان الجهاز** & Security & Compliance Center > **Security policies** > . حدد اسم نهج الجهاز ثم حدد **تحرير** > **متطلبات الوصول**. حدد **السماح بالوصول والإبلاغ عن انتهاك**.<br/>- لإلغاء حظر جهاز غير متوافق أو غير معتمد لمستخدم أو مجموعة من المستخدمين، انتقل إلى مركز توافق & الأمان >**إعدادات إدارة الوصول إلى الجهاز** في **إدارة** >  **نهج** >  الأمان. أضف مجموعة أمان مع الأعضاء الذين تريد استبعادهم من حظر الوصول إلى Microsoft 365. لمزيد من المعلومات، راجع [إنشاء مجموعة أمان أو تحريرها أو حذفها في مركز مسؤولي Microsoft 365](../../admin/email/create-edit-or-delete-a-security-group.md).|
|إزالة المستخدمين حتى لا تتم إدارة أجهزتهم من قبل Basic Mobility and Security|لإزالة المستخدم، قم بتحرير مجموعة الأمان التي لديها نهج إدارة الأجهزة للتنقل الأساسي والأمان. لمزيد من المعلومات، راجع [إنشاء مجموعة أمان أو تحريرها أو حذفها في مركز مسؤولي Microsoft 365](../../admin/email/create-edit-or-delete-a-security-group.md).<br/>لإزالة Basic Mobility and Security من جميع مستخدمي Microsoft 365، راجع [إيقاف تشغيل Basic Mobility and Security](turn-off.md).|

Live (v14)
