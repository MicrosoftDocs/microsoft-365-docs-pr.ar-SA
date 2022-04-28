---
title: إزالة المصادقة الحديثة المختلطة أو تعطيلها من Skype for Business Exchange
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 11/3/2017
audience: ITPro
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
search.appverid:
- MET150
ms.assetid: 5a91b9e3-1508-475b-93e0-710fa5d5cd2d
ms.collection:
- M365-security-compliance
f1.keywords:
- NOCSH
ms.custom:
- seo-marvel-apr2020
description: تشرح هذه المقالة كيفية إزالة المصادقة الحديثة المختلطة أو تعطيلها من Skype for Business Exchange.
ms.openlocfilehash: 27768d5f2ee1a2d223d0979a80d3fff003ed65ec
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/27/2022
ms.locfileid: "65097327"
---
# <a name="removing-or-disabling-hybrid-modern-authentication-from-skype-for-business-and-exchange"></a>إزالة المصادقة الحديثة المختلطة أو تعطيلها من Skype for Business Exchange

*تنطبق هذه المقالة على كل من Microsoft 365 Enterprise و Office 365 Enterprise.*

إذا قمت بتمكين المصادقة الحديثة المختلطة (HMA) فقط للعثور على أنها غير مناسبة للبيئة الحالية الخاصة بك، يمكنك تعطيل HMA. تشرح هذه المقالة كيفية القيام بذلك.
  
## <a name="who-is-this-article-for"></a>روبوت Who هذه المقالة؟

إذا قمت بتمكين المصادقة الحديثة في Skype for Business Online أو محلي و/أو Exchange Online أو محلي ووجدت أنك بحاجة إلى تعطيل HMA، فهذه الخطوات مخصصة لك.

> [!IMPORTANT]
> راجع مقالة "[Skype for Business topologies المدعومة بالمصادقة الحديثة](/skypeforbusiness/plan-your-deployment/modern-authentication/topologies-supported)" إذا كنت تعمل في Skype for Business Online أو محليا، ولديك HMA مختلط الطبولوجيا، وتحتاج إلى إلقاء نظرة على الطبولوجيا المدعومة قبل البدء.
  
## <a name="how-to-disable-hybrid-modern-authentication-exchange"></a>كيفية تعطيل المصادقة الحديثة المختلطة (Exchange)

1. **Exchange المحلي**: افتح Exchange Management Shell وقم بتشغيل الأوامر التالية: 

```powershell
Set-OrganizationConfig -OAuth2ClientProfileEnabled $false
Set-AuthServer -Identity evoSTS -IsDefaultAuthorizationEndpoint $false
```

2. **Exchange Online**: [الاتصال إلى Exchange Online](/powershell/exchange/connect-to-exchange-online-powershell) باستخدام Remote PowerShell. قم بتشغيل الأمر التالي لتحويل علامة  *OAuth2ClientProfileEnabled*  إلى "false":

```powershell    
Set-OrganizationConfig -OAuth2ClientProfileEnabled:$false
```
    
## <a name="how-to-disable-hybrid-modern-authentication-skype-for-business"></a>كيفية تعطيل المصادقة الحديثة المختلطة (Skype for Business)

1. **Skype for Business المحلي**: تشغيل الأوامر التالية في Skype for Business Management Shell:

```powershell
Set-CsOAuthConfiguration -ClientAuthorizationOAuthServerIdentity ""
```

2. **Skype for Business Online**: [الاتصال إلى Skype for Business Online](manage-skype-for-business-online-with-microsoft-365-powershell.md) باستخدام Remote PowerShell. تشغيل الأمر التالي لتعطيل المصادقة الحديثة:

```powershell    
Set-CsOAuthConfiguration -ClientAdalAuthOverride Disallowed
```

[الارتباط مرة أخرى إلى نظرة عامة على المصادقة الحديثة](hybrid-modern-auth-overview.md) . 
