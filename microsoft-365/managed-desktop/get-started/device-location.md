---
title: Windows 10 موقع الخدمة
description: يصف كيفية تشغيل Windows الموقع على أجهزتك
keywords: سطح المكتب المدار من Microsoft، Microsoft 365، الخدمة، الوثائق
ms.service: m365-md
author: tiaraquan
f1.keywords:
- NOCSH
ms.author: tiaraquan
ms.localizationpriority: medium
ms.collection: M365-modern-desktop
manager: dougeby
ms.topic: article
audience: Admin
ms.openlocfilehash: b12f0d188c8347762443cc80e24cfdd7c6280acc
ms.sourcegitcommit: 6c57f1e90339d5a95c9e7875599dac9d3e032c3a
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 02/04/2022
ms.locfileid: "63571372"
---
# <a name="windows-10-location-service"></a>Windows 10 موقع الخدمة

يتم تسجيل الأجهزة في Microsoft Managed Desktop باستخدام Windows Autopilot. تسمح لنا هذه العملية بإدارتها باستخدام Azure Active Directory Microsoft Intune.

بشكل افتراضي Windows 10 يتم تعطيل خدمة موقع Windows 10 عند تشغيل جهاز للمرة الأولى، ما لم يتم تمكين هذه الميزة في إعدادات الخصوصية أثناء تجربة "خارج المربع". يتم إخفاء هذه الإعدادات أثناء تسجيل Autopilot في Microsoft Managed Desktop. لمزيد من المعلومات حول كيفية إعداد Autopilot، راجع تجربة التشغيل الأول [مع Autopilot وصفحة حالة التسجيل](esp-first-run.md).

لهذا السبب، لا يمكن لأجهزة سطح المكتب المدارة من Microsoft الحصول على موقع جهازها، كما أنها تحد من وظائف العديد من Windows، مثل المناطق الزمنية. لمزيد من المعلومات حول Windows 10 الموقع، راجع Windows 10 [خدمة الموقع والخصوصية](https://support.microsoft.com/windows/windows-10-location-service-and-privacy-3a8eee0a-5b0b-dc07-eede-2a5ca1c49088).

لست بحاجة إلى استخدام خدمة الموقع لكي تتمكن من المشاركة في Microsoft Managed Desktop. سيتم تقييد تجربة المستخدم. على سبيل المثال، لن تتمكن الأجهزة من تحديد المنطقة الزمنية التي تكون فيها تلقائيا عندما يعمل المستخدمون في منطقة زمنية مختلفة.

## <a name="enable-the-location-service"></a>تمكين خدمة الموقع

يمكنك إما:

- الاشتراك في استخدام خدمة الموقع عند تسجيل الأجهزة في خدمة سطح المكتب المدار من Microsoft، أو
- يمكنك تشغيل الخدمة أو إيقاف تشغيلها بعد التسجيل.

### <a name="opt-in-during-enrollment"></a>الاشتراك أثناء التسجيل

يمكنك تمكين خدمة سطح المكتب المدار من Microsoft لخدمة الموقع. أثناء تسلسل التسجيل، سيطلب منك تحديد ما إذا كنت تريد السماح Windows 10 خدمة الموقع على الأجهزة.

### <a name="control-the-location-service-after-enrollment"></a>التحكم في خدمة الموقع بعد التسجيل

يمكنك تشغيل خدمة الموقع (أو إيقاف تشغيلها) في أي وقت من خلال إرسال طلب [دعم من خلال](../working-with-managed-desktop/admin-support.md) [مدخل المسؤول](access-admin-portal.md).

## <a name="how-microsoft-managed-desktop-configures-the-windows-10-location-service"></a>كيفية تكوين Microsoft Managed Desktop لخدمة موقع Windows 10 Microsoft

إذا اخترت استخدام خدمة الموقع، فنحن نستخدم الحد الأدنى من الإعدادات الضرورية دون التأثير على خصوصية المستخدمين. لمزيد من المعلومات، [راجع Windows 10 خدمة الموقع والخصوصية](https://support.microsoft.com/windows/windows-10-location-service-and-privacy-3a8eee0a-5b0b-dc07-eede-2a5ca1c49088).

يعمل Microsoft Managed Desktop على تمكين **إعداد** خصوصية الموقع في  إعدادات Windows **السماح بالوصول إلى الموقع على هذا الجهاز**. تبدو واجهة المستخدم كما يلي:

 :::image type="content" source="../../media/MMD-location-services-UI.png" alt-text="إعدادات الموقع في Windows الإعدادات.":::

> [!NOTE]
> إذا اخترت استخدام خدمة الموقع، فهذا ينطبق فقط على Windows التشغيل نفسه. لا يسمح للتطبيقات باستخدام خدمات الموقع. يمكن لكل مستخدم اختيار ما إذا كنت تريد السماح للتطبيقات بالوصول إلى موقعها.
