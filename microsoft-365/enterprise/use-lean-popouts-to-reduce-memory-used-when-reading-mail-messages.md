---
title: استخدام النوافذ المنبثقة المائلة لتقليل الذاكرة المستخدمة عند قراءة رسائل البريد
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 12/3/2019
audience: ITPro
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
search.appverid:
- MET150
ms.assetid: a6d6ba01-2562-4c3d-a8f1-78748dd506cf
f1.keywords:
- NOCSH
description: تحتوي هذه المقالة على معلومات حول استخدام النوافذ المنبثقة المائلة لتحسين أداء تنزيل الرسائل في Outlook على ويب.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: aaacacc0c1db418181690a5a4691bd251180d97c
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 10/06/2021
ms.locfileid: "63568787"
---
# <a name="use-lean-popouts-to-reduce-memory-used-when-reading-mail-messages"></a>استخدام النوافذ المنبثقة المائلة لتقليل الذاكرة المستخدمة عند قراءة رسائل البريد

تحتوي هذه المقالة على معلومات لتحسين أداء تنزيل الرسائل في Outlook على ويب. هذه المقالة هي جزء من تخطيط الشبكة وضبط الأداء [Office 365](./network-planning-and-performance.md) المشروع.
  
بصيغتك مسؤول Office 365 أو المسؤول العام أو مسؤول المستخدم، يمكنك تكوين Outlook على ويب لتقديم نوافذ منبثقة مائلة، إصدار أصغر وأقل استخداما للذاكرة من رسائل بريد إلكتروني معينة في Microsoft Edge أو Internet Explorer. عند تكوين النوافذ المنبثقة المائلة Outlook على ويب، يتم تحميل المكونات التي يتم عرضها من جانب الخادم لتحسين الأداء.
  
> [!NOTE]
> حتى مارس 2018، لا تتوفر النوافذ المنبثقة المائلة للرسائل التي تحدد قيود حقوق الاستخدام، مثل إدارة حقوق استخدام المعلومات (IRM).
  
ستستمر هذه الميزات في العمل في النافذة الرئيسية ولكنها غير متوفرة في النوافذ المنبثقة المائلة:
  
- Outlook الإضافية
  
- Skype for Business الحضور
  
## <a name="to-configure-lean-popouts-for-all-users-within-your-office-365-organization"></a>لتكوين النوافذ المنبثقة المائلة لجميع المستخدمين ضمن Office 365 الخاصة بك
  
1. [الاتصال Exchange Online استخدام PowerShell البعيد](/powershell/exchange/connect-to-exchange-online-powershell).
  
2. قم بتشغيل [Cmdlet Set-OrganizationConfig](/powershell/module/exchange/set-organizationconfig) باستخدام المعلمة LeanPopoutEnabled كما يلي:

  ```powershell
  Set-OrganizationConfig -LeanPopoutEnabled <$true |$false >
  ```

  على سبيل المثال، لتمكين النوافذ المنبثقة المائلة لجميع المستخدمين في مؤسستك:
  
  ```powershell
  Set-OrganizationConfig -LeanPopoutEnabled $true
  ```

  لتعطيل النوافذ المنبثقة المائلة لجميع المستخدمين في مؤسستك:

  ```powershell
  Set-OrganizationConfig -LeanPopoutEnabled $false
  ```
