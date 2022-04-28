---
title: مخطط إدارة الأجهزة Microsoft 365
keywords: Microsoft 365، Microsoft 365 للمؤسسة، وثائق Microsoft 365، إدارة الأجهزة المحمولة، Intune
author: kelleyvice-msft
ms.author: kvice
manager: scotv
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
description: خارطة الطريق لإعداد إدارة الأجهزة Microsoft 365.
ms.openlocfilehash: eeed1a69fc1724f3feb75f4bc096cad3a3c25cf0
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/27/2022
ms.locfileid: "65095301"
---
# <a name="device-management-roadmap-for-microsoft-365"></a>مخطط إدارة الأجهزة Microsoft 365

تتضمن Microsoft 365 للمؤسسة ميزات للمساعدة في إدارة الأجهزة وتطبيقاتها داخل مؤسستك. تساعدك إدارة الأجهزة المحمولة على تأمين موارد مؤسستك وحمايتها.

هناك خياران لإدارة الأجهزة:

- [Microsoft Intune](#microsoft-intune)
- [أساسيات التنقل والأمان](#basic-mobility-and-security)

## <a name="microsoft-intune"></a>Microsoft Intune

يمكنك استخدام Microsoft Intune لإدارة الوصول إلى مؤسستك باستخدام إدارة أجهزة المحمول أو إدارة تطبيقات الأجهزة المحمولة. إدارة الأجهزة المحمولة هي عندما يقوم المستخدمون "بتسجيل" أجهزتهم في Intune. بعد تسجيل جهاز، يكون جهازا مدارا؛ لذلك، يمكن أن يتلقى نهج مؤسستك وقواعدها وإعداداتها. على سبيل المثال، يمكنك تثبيت تطبيقات معينة وإنشاء نهج كلمة مرور وتثبيت اتصال VPN والمزيد.

قد لا يرغب المستخدمون الذين لديهم أجهزتهم الشخصية في تسجيل أجهزتهم أو أن تتم إدارتهم بواسطة Intune وسياسات مؤسستك. ولكنك لا تزال بحاجة إلى حماية موارد مؤسستك وبياناتها. في هذا السيناريو، يمكنك حماية تطبيقاتك باستخدام إدارة تطبيقات الأجهزة المحمولة. على سبيل المثال، يمكنك استخدام نهج إدارة تطبيقات الأجهزة المحمولة الذي يتطلب من المستخدم إدخال رمز PIN عند الوصول إلى SharePoint Online على الجهاز.

ستحدد أيضا كيفية إدارة الأجهزة الشخصية والأجهزة المملوكة للمؤسسة. قد ترغب في معاملة الأجهزة بشكل مختلف، اعتمادا على استخدامها.

## <a name="basic-mobility-and-security"></a>أساسيات التنقل والأمان

هذا مضمن في Microsoft 365 ويساعدك على تأمين الأجهزة المحمولة للمستخدمين وإدارتها مثل أجهزة iPhone وiPad وAndroids والهواتف Windows. يمكنك إنشاء نهج أمان الجهاز وإدارتها، ومسح جهاز عن بعد، وعرض تقارير مفصلة عن الجهاز.

## <a name="choose-between-the-two-options"></a>الاختيار بين الخيارين

لمساعدتك على تقييم خيار إدارة الجهاز الأفضل بالنسبة لك، راجع [الاختيار بين Basic Mobility Security وIntune](/office365/securitycompliance/choose-between-mdm-and-intune).

استنادا إلى تقييمك، ابدأ في إدارة أجهزتك من خلال:

- [Intune](/microsoft-365/solutions/manage-devices-with-intune-overview)
- [أساسيات التنقل والأمان](https://support.microsoft.com/office/set-up-basic-mobility-and-security-dd892318-bc44-4eb1-af00-9db5430be3cd)
 
## <a name="identity-and-device-access-recommendations"></a>توصيات الوصول إلى الهوية والجهاز

توفر Microsoft مجموعة من التوصيات للوصول [إلى الهوية والجهاز](../security/office-365-security/microsoft-365-policies-configurations.md) لضمان وجود قوة عمل آمنة ومنتجة. للوصول إلى الجهاز، استخدم التوصيات والإعدادات الواردة في هذه المقالات:

- [المتطلبات الأساسية](../security/office-365-security/identity-access-prerequisites.md)
- [نهج الوصول إلى الهوية والجهاز الشائعة](../security/office-365-security/identity-access-policies.md)

## <a name="how-contoso-did-device-management-for-microsoft-365"></a>كيف قامت شركة Contoso بإدارة الأجهزة Microsoft 365

للحصول على معلومات حول كيفية نشر شركة خيالية ولكنها تمثيلية متعددة الجنسيات للبنية الأساسية لإدارة الأجهزة المحمولة باستخدام خدمات السحابة Microsoft 365، راجع [إدارة أجهزة المحمول لشركة Contoso](contoso-mdm.md).