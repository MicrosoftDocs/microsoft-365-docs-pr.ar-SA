---
title: تمكين SharePoint Multi-Geo في موقعك الجغرافي على القمر الصناعي
ms.reviewer: adwood
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: o365-solutions
f1.keywords:
- NOCSH
ms.custom: seo-marvel-apr2020
ms.collection:
- Strat_SP_gtc
- SPO_Content
ms.localizationpriority: medium
description: توفر هذه المقالة معلومات للمسؤولين العامين SharePoint حول تمكين SharePoint Multi-Geo مواقع الأقمار الصناعية الجغرافية.
ms.openlocfilehash: b542c1ee77c7b4ca7a6179bac5ce5eaa1090606a
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/08/2022
ms.locfileid: "63570028"
---
# <a name="enabling-sharepoint-multi-geo-in-your-satellite-geo-location"></a>تمكين SharePoint Multi-Geo في موقعك الجغرافي على القمر الصناعي

هذه المقالة للمسؤولين العامين أو مسؤولي SharePoint الذين أنشأوا موقع أقمار صناعية متعددة الجغرافيا قبل أن **تصبح قدرات SharePoint Multi-Geo** متوفرة بشكل عام في 27 مارس 2019، والذين لم يقوموا بتمكين SharePoint Multi-Geo في موقع (مواقع) الأقمار الصناعية الجغرافية. 

>[!Note]
>إذا أضفت موقع جغرافي جديد بعد **27 مارس 2019**، لست بحاجة إلى تنفيذ هذه الإرشادات، حيث سيتم تمكين موقعك الجغرافي الجديد OneDrive SharePoint Multi-Geo.

ستسمح لك هذه الإرشادات بتمكين SharePoint في موقع القمر الصناعي، بحيث يمكن لمستخدمي الأقمار الصناعية متعددة الجغرافيا الاستفادة من إمكانيات OneDrive وإمكانيات SharePoint Multi-Geo في O365. 

>[!IMPORTANT]
>تجدر الإشارة إلى أن هذه طريقة تمكين واحدة. بمجرد تعيين وضع SPO، لن تتمكن من إعادة المستأجر إلى وضع "الجغرافيا OneDrive"، دون أي تصعيد مع الدعم. 

## <a name="to-set-a-geo-location-into-spo-mode"></a>لتعيين موقع جغرافي إلى وضع SPO

لتعيين موقع جغرافي إلى وضع SPO، اتصل بموقع الجغرافيا الذي تريد تعيينه في وضع SPO:

1.    فتح حسابك SharePoint Online Management Shell 
2.    Connect-SPOService -URL "https://$tenantGeo-admin.sharepoint.com" -بيانات الاعتماد $credential
3.    Set-SPOMultiGeoExperience</br></br>
![Set-SPOMultiGeoExperience.](../media/Set-SPO-MultiGeo.jpg)
4.    تستغرق هذه العملية عادة ساعة تقريبا بينما نقوم بإجراء عمليات نشر متنوعة في الخدمة ونعيد ختم المستأجر. بعد ساعة واحدة على الأقل، يرجى تنفيذ Get-SPOMultiGeoExperience.  سيعرض لك ذلك ما إذا كان هذا الموقع الجغرافي في وضع SPO.</br></br>
![Set-SPOMultiGeoExperience.](../media/Get-SPO-MultiGeo.jpg)

 
 
 
>[!Note]
>يتم تحديث بعض ذاكرة التخزين المؤقت في الخدمة كل 24 ساعة، لذا فمن المحتمل أن تكون عمل الموقع الجغرافي للأقمار الصناعية بشكل متقطع لمدة تصل إلى 24 ساعة كما لو كان لا يزال في وضع ODB. لا يسبب هذا أي مشاكل تقنية. 
 
لمزيد من المعلومات حول SharePoint Multi-Geo، [يرجى الرجوع إلى](multi-geo-capabilities-in-onedrive-and-sharepoint-online-in-microsoft-365.md) aka.ms/sharepointmultigeo


