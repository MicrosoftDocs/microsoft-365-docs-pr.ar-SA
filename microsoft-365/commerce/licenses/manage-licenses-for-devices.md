---
title: إدارة التراخيص للأجهزة
f1.keywords:
- CSH
author: cmcatee-MSFT
ms.author: cmcatee
manager: scotv
ms.reviewer: shegu, nicholak
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
description: تعرف على كيفية تعيين تراخيص للمجموعات لاستخدامها مع الأجهزة.
ms.custom:
- commerce_licensing
- AdminSurgePortfolio
- okr_SMB
search.appverid: MET150
ms.date: 05/12/2022
ms.openlocfilehash: 5603fd947abdfbc6bede01fe7545a5a0fa99a67d
ms.sourcegitcommit: 4e7ff69f4d7d27c2d419f763cfcb069e3b0d0d9f
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 05/13/2022
ms.locfileid: "65403261"
---
# <a name="manage-licenses-for-devices"></a>إدارة التراخيص للأجهزة

إذا كان لديك Microsoft 365 Apps for enterprise (جهاز) أو Microsoft 365 Apps للتعليم (جهاز)، يمكنك تعيين تراخيص للأجهزة باستخدام مجموعات Azure AD. عندما يكون لدى الجهاز ترخيص، يمكن لأي شخص يستخدم هذا الجهاز استخدام Microsoft 365 Apps for enterprise (المسمى سابقا Office 365 ProPlus). على سبيل المثال، لنفترض أن لديك 20 كمبيوتر محمولا وكمبيوترا لوحيا يستخدمها أشخاص في مؤسستك. عند تعيين ترخيص لكل جهاز، يستخدم كل شخص يسجل الدخول إلى أحد الأجهزة Microsoft 365 Apps for enterprise دون الحاجة إلى ترخيصه الخاص.

> [!IMPORTANT]
> يتوفر الترخيص المستند إلى الجهاز Microsoft 365 Apps for enterprise فقط كرخصة وظيفة إضافية لبعض العملاء التجاريين وبعض عملاء التعليم. بالنسبة للعملاء التجاريين، يكون الترخيص *Microsoft 365 Apps for enterprise (جهاز)* ولا يتوفر إلا من خلال اشتراك اتفاقية Enterprise/اتفاقية Enterprise. بالنسبة لعملاء التعليم، يكون الترخيص *Microsoft 365 Apps للتعليم (الجهاز)* ولا يتوفر إلا من خلال التسجيل لحلول التعليم (EES). لمزيد من المعلومات، اقرأ منشور المدونة حول [توفر التعليم](https://educationblog.microsoft.com/2019/08/attention-it-administrators-announcing-office-365-proplus-device-based-subscription-for-education). للحصول على التوفر التجاري، اتصل بممثل حساب Microsoft.

للبدء، يمكنك إنشاء مجموعة في مركز إدارة Azure Active Directory، ثم تعيين الأجهزة إلى المجموعة. لمعرفة المزيد حول ترخيص الجهاز، بما في ذلك متطلبات الجهاز، وأنواع المجموعات التي يمكنك استخدامها، وكيفية تكوين Microsoft 365 Apps for enterprise لاستخدام ترخيص الجهاز، راجع [الترخيص المستند إلى الجهاز Microsoft 365 Apps for enterprise](/deployoffice/device-based-licensing).

> [!IMPORTANT]
> يجب أن تكون مسؤولا عموميا لإكمال المهام في هذه المقالة.

## <a name="assign-licenses-to-devices"></a>تعيين تراخيص للأجهزة

عند تعيين التراخيص إلى مجموعة، يمكنك تعيين تراخيص لجميع الأجهزة داخل المجموعة. يمكنك تعيين اشتراك واحد فقط لأي مجموعة واحدة.

1. في مركز مسؤولي Microsoft 365، انتقل إلى صفحة <a href="https://go.microsoft.com/fwlink/p/?linkid=842264" target="_blank">BillingLicenses</a> > .
2. في صفحة **"التراخيص"**، اختر **Microsoft 365 Apps للتعليم (جهاز)** أو **Microsoft 365 Apps for enterprise (جهاز).**
3. في الصفحة التالية، اختر اشتراكا، ثم اختر **"تعيين التراخيص**".
4. في جزء **"تعيين التراخيص إلى مجموعة** "، ابدأ بكتابة اسم مجموعة، ثم اختره من النتائج لإضافته إلى القائمة.
5. اختر **"تعيين**"، ثم اختر **"إغلاق**".

## <a name="unassign-licenses-from-devices"></a>إلغاء تعيين التراخيص من الأجهزة

عند إلغاء تعيين التراخيص من مجموعة، يمكنك إزالة التراخيص من جميع الأجهزة داخل المجموعة. تكون جميع التطبيقات والبيانات المقترنة بها للقراءة فقط.

1. في مركز الإدارة، انتقل إلى صفحة <a href="https://go.microsoft.com/fwlink/p/?linkid=842264" target="_blank">BillingLicenses</a> > .
2. في صفحة **"التراخيص"**، اختر **Microsoft 365 Apps للتعليم (جهاز)** أو **Microsoft 365 Apps for enterprise (جهاز).**
3. في الصفحة التالية، اختر اشتراكا، وحدد النقاط الثلاث (مزيد من الإجراءات)، ثم اختر **إلغاء تعيين التراخيص**.
4. في مربع الحوار **"إلغاء تعيين التراخيص**"، اختر **"إلغاء تعيين".**
