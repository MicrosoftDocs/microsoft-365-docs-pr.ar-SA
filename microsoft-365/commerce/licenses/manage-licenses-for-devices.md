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
description: تعرف على كيفية تعيين التراخيص إلى مجموعات لاستخدامها مع الأجهزة.
ms.custom:
- commerce_licensing
- AdminSurgePortfolio
- okr_SMB
search.appverid: MET150
ms.date: 08/27/2021
ms.openlocfilehash: fd452cb52a1c65a59e478fb80438ac95a57e8bf6
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/08/2022
ms.locfileid: "63569145"
---
# <a name="manage-licenses-for-devices"></a>إدارة التراخيص للأجهزة

إذا كان لديك Microsoft 365 Apps for enterprise (جهاز) أو Microsoft 365 Apps للتعليم (جهاز)، يمكنك تعيين تراخيص للأجهزة باستخدام مجموعات Azure AD. عندما يكون الجهاز لديه ترخيص، يمكن لأي شخص يستخدم هذا الجهاز استخدام Microsoft 365 Apps for enterprise (المسمى سابقا Office 365 ProPlus). على سبيل المثال، لنقل أن لديك 20 كمبيوتر محمولا وأجهزة كمبيوتر لوحي يستخدمها الأشخاص في مؤسستك. عند تعيين ترخيص لكل جهاز، يستخدم كل شخص يسجل دخوله إلى أحد الأجهزة Microsoft 365 Apps for enterprise دون الحاجة إلى ترخيصه الخاص.

> [!IMPORTANT]
> يتوفر الترخيص المستند إلى Microsoft 365 Apps for enterprise الأجهزة فقط كرخصة إضافية لبعض العملاء التجاريين وبعض عملاء التعليم. بالنسبة للعملاء التجاريين، يكون الترخيص Microsoft 365 Apps for enterprise *(الجهاز)* ولا يتوفر إلا من خلال اتفاقية Enterprise/اتفاقية Enterprise الاشتراك. بالنسبة لعملاء التعليم، يكون الترخيص Microsoft 365 Apps *للتعليم (الجهاز)* وهو متوفر فقط من خلال التسجيل في حلول التعليم (EES). لمزيد من المعلومات، اقرأ منشور المدونة حول [توفر التعليم](https://educationblog.microsoft.com/2019/08/attention-it-administrators-announcing-office-365-proplus-device-based-subscription-for-education). للتوفر التجاري، اتصل بممثل حساب Microsoft.

للبدء، يمكنك إنشاء مجموعة في مركز إدارة Azure Active Directory، ثم تعيين الأجهزة إلى المجموعة. لمعرفة المزيد حول ترخيص الأجهزة، بما في ذلك متطلبات الجهاز وأنواع المجموعات التي يمكنك استخدامها وكيفية تكوين Microsoft 365 Apps for enterprise لاستخدام ترخيص الجهاز، راجع الترخيص المستند إلى [الجهاز](/deployoffice/device-based-licensing) Microsoft 365 Apps for enterprise.

> [!IMPORTANT]
> يجب أن تكون المسؤول العام لإكمال المهام في هذه المقالة.

## <a name="assign-licenses-to-devices"></a>تعيين التراخيص للأجهزة

عندما تقوم بتعيين تراخيص إلى مجموعة، يمكنك تعيين التراخيص إلى جميع الأجهزة ضمن المجموعة. يمكنك تعيين اشتراك واحد فقط إلى أي مجموعة واحدة.

1. في مركز مسؤولي Microsoft 365، انتقل إلى **صفحة BillingLicenses** > .<a href="https://go.microsoft.com/fwlink/p/?linkid=842264" target="_blank"></a>
2. في صفحة **التراخيص**، اختر Microsoft 365 Apps **للتعليم (الجهاز)** أو Microsoft 365 Apps for enterprise **(الجهاز)**).
3. في الصفحة التالية، اختر اشتراكا، ثم اختر **تعيين التراخيص**.
4. في **الجزء تعيين تراخيص إلى** مجموعة، ابدأ بكتابة اسم مجموعة، ثم اختره من النتائج التي تريد إضافتها إلى القائمة.
5. اختر **تعيين**، ثم اختر **إغلاق**.

## <a name="unassign-licenses-from-devices"></a>غير تعيين التراخيص من الأجهزة

عندما تقوم بإزالة تعيين التراخيص من مجموعة، يمكنك إزالة التراخيص من كل الأجهزة ضمن المجموعة. عندئذ تكون جميع التطبيقات والبيانات المقترنة بها للقراءة فقط.

1. في مركز الإدارة، انتقل إلى **صفحة BillingLicenses** > .<a href="https://go.microsoft.com/fwlink/p/?linkid=842264" target="_blank"></a>
2. في صفحة **التراخيص**، اختر Microsoft 365 Apps **للتعليم (الجهاز)** أو Microsoft 365 Apps for enterprise **(الجهاز)**).
3. في الصفحة التالية، اختر اشتراكا، وحدد النقاط الثلاث (المزيد من الإجراءات)، ثم اختر **إلغاء تعيين التراخيص**.
4. في **مربع الحوار "عدم تعيين التراخيص** "، اختر **"غير تعيين**".
