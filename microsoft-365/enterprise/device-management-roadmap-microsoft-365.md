---
title: خارطة طريق إدارة الأجهزة Microsoft 365
keywords: Microsoft 365 Microsoft 365 للمؤسسات ووثائق Microsoft 365 وإدارة أجهزة المحمول و Intune
author: kelleyvice-msft
ms.author: kvice
manager: laurawi
ms.date: 08/10/2020
ms.topic: conceptual
f1.keywords:
- NOCSH
ms.prod: microsoft-365-enterprise
ms.service: ''
ms.technology: ''
ms.assetid: fb4182e6-5e78-45d0-9641-d791c4519441
audience: ITPro
ms.custom: microsoft-intune
description: المخطط لإعداد إدارة الأجهزة Microsoft 365.
ms.openlocfilehash: 0fef31697657b4694090ae7a1b63516920d8c71b
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 01/12/2022
ms.locfileid: "63569352"
---
# <a name="device-management-roadmap-for-microsoft-365"></a>خارطة طريق إدارة الأجهزة Microsoft 365

Microsoft 365 للمؤسسات ميزات للمساعدة في إدارة الأجهزة وتطبيقاتها داخل مؤسستك. تساعدك إدارة الأجهزة المحمولة على تأمين موارد مؤسستك وحمايتها.

هناك خياران لإدارة الأجهزة:

- [Microsoft Intune](#microsoft-intune)
- [التنقل والأمان الأساسيان](#basic-mobility-and-security)

## <a name="microsoft-intune"></a>Microsoft Intune

يمكنك استخدام Microsoft Intune لإدارة الوصول إلى مؤسستك باستخدام إدارة أجهزة المحمول أو إدارة تطبيقات الأجهزة المحمولة. إدارة أجهزة المحمول هي عندما "يسجل" المستخدمون أجهزتهم في Intune. بعد تسجيل الجهاز، يكون جهازا مدارا؛ وبالتالي، يمكنها أن تتلقى سياسات مؤسستك وقواعدها وإعداداتها. على سبيل المثال، يمكنك تثبيت تطبيقات معينة وإنشاء نهج كلمة مرور وتثبيت اتصال VPN والمزيد.

قد لا يرغب المستخدمون الذين لديهم أجهزتهم الشخصية في تسجيل أجهزتهم أو إدارتها بواسطة Intune ونهج مؤسستك. ولكنك لا تزال بحاجة إلى حماية موارد المؤسسة وبياناتها. في هذا السيناريو، يمكنك حماية تطبيقاتك باستخدام إدارة تطبيقات الأجهزة المحمولة. على سبيل المثال، يمكنك استخدام نهج إدارة تطبيقات الأجهزة المحمولة الذي يتطلب من المستخدم إدخال رمز PIN عند الوصول إلى SharePoint عبر الإنترنت على الجهاز.

ستحدد أيضا كيفية إدارة الأجهزة الشخصية والأجهزة المملوكة لمنظمتك. قد ترغب في التعامل مع الأجهزة بشكل مختلف، استنادا إلى استخداماتها.

## <a name="basic-mobility-and-security"></a>التنقل والأمان الأساسيان

هذا مضمن في Microsoft 365 ويساعدك على تأمين أجهزة المحمول الخاصة للمستخدمين وإدارتها مثل أجهزة iPhone وiPads وAndroid Windows الجوال. يمكنك إنشاء سياسات أمان الجهاز وإدارتها، ومسح جهاز عن بعد، وعرض تقارير مفصلة عن الجهاز.

## <a name="choose-between-the-two-options"></a>الاختيار من بين الخيارين

لمساعدتك على تقييم خيار إدارة الأجهزة الأفضل لك بشكل أفضل، راجع [الاختيار بين أمان التنقل الأساسي و Intune](/office365/securitycompliance/choose-between-mdm-and-intune).

استنادا إلى تقييمك، يمكنك بدء إدارة أجهزتك باستخدام:

- [Intune](/microsoft-365/solutions/manage-devices-with-intune-overview)
- [التنقل والأمان الأساسيان](https://support.microsoft.com/office/set-up-basic-mobility-and-security-dd892318-bc44-4eb1-af00-9db5430be3cd)
 
## <a name="identity-and-device-access-recommendations"></a>توصيات الوصول إلى الأجهزة والهوية

توفر Microsoft مجموعة من التوصيات للوصول إلى الهوية [والجهاز لضمان توفير](../security/office-365-security/microsoft-365-policies-configurations.md) قوة عمل آمنة ومنتجة. للوصول إلى الجهاز، استخدم التوصيات والإعدادات في المقالات التالية:

- [المتطلبات الأساسية](../security/office-365-security/identity-access-prerequisites.md)
- [ونهج الوصول إلى الأجهزة والهوية الشائعة](../security/office-365-security/identity-access-policies.md)

## <a name="how-contoso-did-device-management-for-microsoft-365"></a>كيف قام Contoso بإدارة الأجهزة Microsoft 365

للحصول على معلومات حول كيفية نشر شركة خيالية ولكنها تمثيلية متعددة القوميات للبنية الأساسية لإدارة أجهزة المحمول باستخدام Microsoft 365 السحابية، راجع إدارة أجهزة [المحمول ل Contoso](contoso-mdm.md).