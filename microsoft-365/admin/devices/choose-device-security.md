---
title: مقارنة أساليب حماية بيانات الأجهزة والتطبيقات المختلفة
f1.keywords:
- NOCSH
ms.author: sharik
author: skjerland
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
search.appverid:
- MET150
description: الاختيار بين أساليب MDM وMAM المختلفة.
ms.openlocfilehash: cc2eef0fde261ed8ee6eace288d70c53235fc88e
ms.sourcegitcommit: 9255a7e8b398f92d8dae09886ae95dc8577bf29a
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 05/17/2022
ms.locfileid: "65435402"
---
# <a name="options-for-protecting-your-devices-and-app-data-with-microsoft-365"></a>خيارات لحماية أجهزتك وبيانات التطبيق باستخدام Microsoft 365

لديك عدة طرق لتأمين أجهزة مؤسستك وبياناتها باستخدام Microsoft 365 للأعمال والمؤسسات. يمكنك استخدام الخطط المستقلة التالية:

- Intune (جزء من إدارة نقاط النهاية من Microsoft)
- خطط Premium Azure Active Directory.
- التنقل الأساسي والأمان (المضمن في معظم Microsoft 365 لخطط الأعمال والمؤسسات) أو استخدام الاشتراكات التي تتضمن بعض الخطط المستقلة السابقة أو كلها.
- Microsoft Defender for Business (مضمنة في Microsoft 365 Business Premium؛ متوفرة أيضا كخطط مستقلة)
- اشتراك Microsoft 365 Business Premium، والذي يتضمن الأمان والحماية من التهديدات للشركات الصغيرة التي تضم أقل من 300 مستخدم.
- Microsoft 365 Enterprise الخطط التي تتضمن الأمان المتقدم والحماية من التهديدات.

## <a name="device-management-options"></a>خيارات إدارة الأجهزة

- يتم تقديم **التنقل الأساسي والأمان** مع معظم خطط Microsoft 365، وهو الخيار المضمن الوحيد المقدم Microsoft 365 Business Standard Microsoft 365 Business Basic. لمزيد من المعلومات، راجع [توفر Basic Mobility and Security](../basic-mobility-security/choose-between-basic-mobility-and-security-and-intune.md#availability-of-basic-mobility-and-security-and-intune). 

    إذا كان لديك إما Microsoft 365 Business Basic أو Microsoft 365 Business Standard، يمكنك أيضا شراء Intune إذا كانت مؤسستك لديها احتياجات أمان أكثر تعقيدا.
 
- **Microsoft Intune** هي خطة مستقلة يتم تضمينها أيضا مع بعض Microsoft 365 لخطط الأعمال أو المؤسسات. إذا كان لديك Intune إما كجزء مستقل أو كجزء من اشتراكك، فإنه يوفر القدرة على ضبط الجهاز وإدارة بيانات التطبيق. لمزيد من المعلومات حول التوفر مع Microsoft 365، راجع [توفر Intune](../basic-mobility-security/choose-between-basic-mobility-and-security-and-intune.md#availability-of-basic-mobility-and-security-and-intune).

    Microsoft Intune هي خدمة مستندة إلى السحابة تركز على إدارة أجهزة المحمول (MDM) وإدارة تطبيقات المحمول (MAM). يمكنك التحكم في كيفية استخدام أجهزة مؤسستك، بما في ذلك الهواتف المحمولة وأجهزة الكمبيوتر اللوحية وأجهزة الكمبيوتر المحمولة. يمكنك أيضا تكوين نهج محددة للتحكم في التطبيقات. لمزيد من المعلومات، راجع [وثائق Microsoft Intune](/mem/intune/).

- خطط **Premium Azure Active Directory (AD)** هي خطط مستقلة تأتي أيضا مع بعض Microsoft 365 لخطط الأعمال والمؤسسة. لمزيد من المعلومات، راجع [التسعير Azure AD](https://azure.microsoft.com/pricing/details/active-directory/).

     يسمح لك Azure AD Premium P1 وP2 Azure AD Premium بتعيين ميزات الوصول المشروط وإعادة تعيين كلمة مرور الخدمة الذاتية وما إلى ذلك. لمزيد من المعلومات حول قدرات خطط Premium، راجع صفحة [التسعير Azure AD](https://azure.microsoft.com/pricing/details/active-directory/).

- تتضمن **Microsoft 365 Business Premium** Intune وAzure Active Directory Premium P1، Microsoft Defender لـ Office 365 الخطة 1، Microsoft Defender for Business. 
 
    يقدم Microsoft 365 Business Premium مجموعة من قوالب النهج لتأمين أجهزتك وبيانات التطبيق. ويوفر مستوى جيدا من الأمان والحماية من التهديدات لمعظم الشركات التي أقل من 300 مستخدم. لمزيد من المعلومات، راجع [Microsoft 365 Business Premium نظرة عامة](../../business-premium/index.md) [ولمحة عامة عن Microsoft Defender for Business](../../security/defender-business/mdb-overview.md).

- تتضمن **Microsoft 365 لاشتراكات المؤسسة** Microsoft Intune وتتضمن E5 أيضا Azure AD الخطط المتميزة 1 و2.

    يوفر Microsoft 365 E5 أعلى مستوى من الأمان والحماية من التهديدات لجميع اشتراكات Microsoft 365. لمزيد من المعلومات، راجع [Microsoft 365 للحصول على نظرة عامة على المؤسسة](../../enterprise/microsoft-365-overview.md).

## <a name="see-also"></a>راجع أيضًا

[أفضل الممارسات لتأمين Microsoft 365 لخطط الأعمال](../security-and-compliance/secure-your-business-data.md)