---
title: إدارة موافقة المستخدم على التطبيقات في Microsoft 365
f1.keywords:
- CSH
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
- Adm_NonTOC
ms.custom:
- AdminSurgePortfolio
- AdminTemplateSet
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: 7e453a40-66df-44ab-92a1-96786cb7fb34
description: تعرف على موافقة المستخدم على التطبيقات، وكيفية تشغيلها للسماح لتطبيقات جهة خارجية بالوصول إلى Microsoft 365 المستخدمين.
ms.openlocfilehash: d9a07eb333b0abdb3cb6a890ac2de3d19ad3685b
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 10/06/2021
ms.locfileid: "63570123"
---
# <a name="managing-user-consent-to-apps-in-microsoft-365"></a>إدارة موافقة المستخدم على التطبيقات في Microsoft 365

يتحكم هذا الإعداد في إمكانية منح المستخدمين هذه الموافقة للتطبيقات التي تستخدم OpenID الاتصال و OAuth 2.0 من أجل تسجيل الدخول وطلبات الوصول إلى البيانات. يمكن إنشاء تطبيق من داخل مؤسستك، أو يمكن أن يكون من مؤسسة أخرى Office 365 أو جهة خارجية.

إذا قمت تشغيل هذا الإعداد، ستطالب هذه التطبيقات المستخدمين بإذن الوصول إلى بيانات مؤسستك، ويمكن للمستخدمين اختيار ما إذا كانوا يسمحون به أم لا. إذا قمت ب إيقاف تشغيل هذا الإعداد، فيجب على المسؤولين الموافقة على تلك التطبيقات قبل أن يمكن للمستخدمين استخدامها. في هذه الحالة، يمكنك إعداد سير عمل موافقة المسؤول في مدخل Azure بحيث يمكن للمستخدمين إرسال طلب موافقة المسؤول لاستخدام أي تطبيق تم حظره.

يمكن للمستخدم منح حق الوصول إلى التطبيقات التي يملكها فقط التي يمكنها الوصول إلى Office 365 الخاصة به. ولا يمكنهم منح تطبيق حق الوصول إلى معلومات أي مستخدم آخر.

## <a name="turning-user-consent-on-or-off"></a>تشغيل موافقة المستخدم أو إيقاف تشغيلها

إليك كيفية تشغيل موافقة المستخدم على التطبيقات أو إيقاف تشغيلها.

1. في مركز الإدارة، انتقل إلى  \> صفحة إعدادات الإعدادات **المؤسسةServices** > ، ثم حدد **موافقة المستخدم على التطبيقات**.[](https://go.microsoft.com/fwlink/p/?linkid=2053743)

2. في صفحة **موافقة المستخدم على التطبيقات** ، حدد خيار تشغيل موافقة المستخدم أو إيقاف تشغيلها.

## <a name="related-content"></a>المحتوى ذي الصلة 

[تكوين سير عمل موافقة المسؤول](/azure/active-directory/manage-apps/configure-admin-consent-workflow) (مقالة)\
[إدارة الموافقة على التطبيقات وتقييم طلبات الموافقة](/azure/active-directory/manage-apps/manage-consent-requests) (مقالة)