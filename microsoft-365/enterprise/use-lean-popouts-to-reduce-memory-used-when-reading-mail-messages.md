---
title: استخدام النوافذ المنبثقة المرنة لتقليل الذاكرة المستخدمة عند قراءة رسائل البريد
ms.author: kvice
author: kelleyvice-msft
manager: scotv
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
description: تحتوي هذه المقالة على معلومات حول استخدام العناصر المنبثقة المرنة لتحسين أداء تنزيل الرسائل في Outlook على ويب.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 9636fd3beafd169358c4b50cafdc4ac0f9494994
ms.sourcegitcommit: 133bf9097785309da45df6f374a712a48b33f8e9
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 06/10/2022
ms.locfileid: "66012671"
---
# <a name="use-lean-popouts-to-reduce-memory-used-when-reading-mail-messages"></a>استخدام النوافذ المنبثقة المرنة لتقليل الذاكرة المستخدمة عند قراءة رسائل البريد

تحتوي هذه المقالة على معلومات لتحسين أداء تنزيل الرسائل في Outlook على ويب. تشكل هذه المقالة جزءا من [تخطيط الشبكة وضبط الأداء لمشروع Office 365](./network-planning-and-performance.md).
  
بصفتك **مسؤول تطبيق** Office 365 أو **مسؤولا عموميا** أو **مسؤول مستخدم**، يمكنك تكوين Outlook على ويب لتقديم _النوافذ المنبثقة المرنة_، وهو إصدار أصغر وأقل استخداما للذاكرة لبعض رسائل البريد الإلكتروني في Microsoft Edge أو Internet Explorer. عند تكوين العناصر المنبثقة المرنة Outlook على ويب، يتم تحميل المكونات المعروضة من جانب الخادم التي تحسن الأداء.
  
> [!NOTE]
> اعتبارا من مارس 2018، لا تتوفر النوافذ المنبثقة المرنة للرسائل التي تحدد قيود حقوق الاستخدام، مثل المعلومات Rights Management (IRM).
  
ستستمر هذه الميزات في العمل في النافذة الرئيسية ولكنها غير متوفرة في النوافذ المنبثقة المرنة:
  
- Outlook الوظائف الإضافية
  
- حالة الحضور Skype for Business
  
## <a name="to-configure-lean-popouts-for-all-users-within-your-office-365-organization"></a>لتكوين العناصر المنبثقة المرنة لجميع المستخدمين داخل مؤسستك Office 365
  
1. [الاتصال إلى Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).
  
2. قم بتشغيل [Set-OrganizationConfig](/powershell/module/exchange/set-organizationconfig) cmdlet مع المعلمة LeanPopoutEnabled كما يلي:

  ```powershell
  Set-OrganizationConfig -LeanPopoutEnabled <$true |$false >
  ```

  على سبيل المثال، لتمكين النوافذ المنبثقة المرنة لجميع المستخدمين في مؤسستك:
  
  ```powershell
  Set-OrganizationConfig -LeanPopoutEnabled $true
  ```

  لتعطيل النوافذ المنبثقة المرنة لجميع المستخدمين في مؤسستك:

  ```powershell
  Set-OrganizationConfig -LeanPopoutEnabled $false
  ```
