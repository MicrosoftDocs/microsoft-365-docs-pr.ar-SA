---
title: إزالة المصادقة الحديثة المختلطة أو تعطيلها من Skype for Business Exchange
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
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
ms.openlocfilehash: efc84ead5ea8219e77391f2a8ebe51e5fa23da8c
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 10/06/2021
ms.locfileid: "63568948"
---
# <a name="removing-or-disabling-hybrid-modern-authentication-from-skype-for-business-and-exchange"></a>إزالة المصادقة الحديثة المختلطة أو تعطيلها من Skype for Business Exchange

*تنطبق هذه المقالة على كل من Microsoft 365 Enterprise Office 365 Enterprise.*

إذا قمت بتمكين المصادقة الحديثة المختلطة (HMA) فقط للعثور على أنها غير مناسبة لبيئة الحالية، يمكنك تعطيل HMA. تشرح هذه المقالة كيفية ذلك.
  
## <a name="who-is-this-article-for"></a>روبوت Who هذه المقالة؟

إذا قمت بتمكين المصادقة الحديثة في Skype for Business Online أو on-premises و/أو Exchange Online أو on-premises ووجدت أنك بحاجة إلى تعطيل HMA، فها هي الخطوات المناسبة لك.

> [!IMPORTANT]
> راجع مقالة ["Skype for Business](/skypeforbusiness/plan-your-deployment/modern-authentication/topologies-supported) طبولوجيا مدعمة مع المصادقة الحديثة" إذا كنت تعمل في Skype for Business Online أو On-premises، وكان لديك HMA مختلط طبولوجيا، وستحتاج إلى الاطلاع على الطبولوجيا المعتمدة قبل البدء.
  
## <a name="how-to-disable-hybrid-modern-authentication-exchange"></a>كيفية تعطيل المصادقة الحديثة المختلطة (Exchange)

1. **Exchange:** فتح Exchange Management Shell وتشغيل الأوامر التالية: 

```powershell
Set-OrganizationConfig -OAuth2ClientProfileEnabled $false
Set-AuthServer -Identity evoSTS -IsDefaultAuthorizationEndpoint $false
```

2. **Exchange Online**: [الاتصال Exchange Online](/powershell/exchange/connect-to-exchange-online-powershell) Remote PowerShell. قم بتشغيل الأمر التالي لتحويل علامة  *OAuth2ClientProfileEnabled*  إلى "false":

```powershell    
Set-OrganizationConfig -OAuth2ClientProfileEnabled:$false
```
    
## <a name="how-to-disable-hybrid-modern-authentication-skype-for-business"></a>كيفية تعطيل المصادقة الحديثة المختلطة (Skype for Business)

1. **Skype for Business**: تشغيل الأوامر التالية في Skype for Business Management Shell:

```powershell
Set-CsOAuthConfiguration -ClientAuthorizationOAuthServerIdentity ""
```

2. **Skype for Business عبر** [الإنترنت: الاتصال الاتصال Skype for Business عبر الإنترنت](manage-skype-for-business-online-with-microsoft-365-powershell.md) باستخدام Remote PowerShell. قم بتشغيل الأمر التالي لتعطيل المصادقة الحديثة:

```powershell    
Set-CsOAuthConfiguration -ClientAdalAuthOverride Disallowed
```

[ارجع إلى نظرة عامة حول المصادقة الحديثة](hybrid-modern-auth-overview.md) . 
