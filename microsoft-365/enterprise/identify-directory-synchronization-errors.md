---
title: عرض أخطاء مزامنة الدليل في Microsoft 365
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- seo-marvel-apr2020
- admindeeplinkMAC
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOE150
- MED150
- MBS150
- GPA150
ms.assetid: b4fc07a5-97ea-4ca6-9692-108acab74067
description: تعرف على كيفية عرض أخطاء مزامنة الدليل والتصحيحات المحتملة في مركز مسؤولي Microsoft 365.
ms.openlocfilehash: 2b832cff65aad0ae7327f440a565e12c7cba66f4
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 10/06/2021
ms.locfileid: "63569614"
---
# <a name="view-directory-synchronization-errors-in-microsoft-365"></a>عرض أخطاء مزامنة الدليل في Microsoft 365

يمكنك عرض أخطاء مزامنة الدليل <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">في مركز مسؤولي Microsoft 365.</a> يتم عرض أخطاء كائن المستخدم فقط. لعرض الأخطاء باستخدام PowerShell، راجع [تحديد العناصر باستخدام DirSyncProvisioningErrors](/azure/active-directory/hybrid/how-to-connect-syncservice-duplicate-attribute-resiliency).

## <a name="view-directory-synchronization-errors-in-the-microsoft-365-admin-center"></a>عرض أخطاء مزامنة الدليل في مركز مسؤولي Microsoft 365

لعرض أي أخطاء في مركز مسؤولي Microsoft 365:
  
1. سجل [الدخول إلى مركز مسؤولي Microsoft 365](https://admin.microsoft.com) باستخدام حساب مسؤول عام. 
    
2. على **الصفحة الرئيسية** ، سترى بطاقة **إدارة** المستخدم. 
    
    ![بطاقة إدارة المستخدم في مركز مسؤولي Microsoft 365.](../media/060006e9-de61-49d5-8979-e77cda198e71.png)
  
3. على البطاقة **، اختر مزامنة** الأخطاء ضمن **Azure AD** الاتصال لرؤية الأخطاء في صفحة أخطاء **مزامنة الدليل.**   
    
    ![مثال على صفحة أخطاء مزامنة الدليل.](../media/882094a3-80d3-4aae-b90b-78b27047974c.png)

4. اختر أي من الأخطاء لعرض جزء التفاصيل مع معلومات حول الخطأ وتلميحات حول كيفية إصلاحه.

   ![مثال التفاصيل الخاصة بخطأ مزامنة الدليل.](../media/a6e302d4-6be7-4e3a-b4b5-81c5a2c02952.png)
  
بعد [العرض، راجع](fix-problems-with-directory-synchronization.md) تصحيح المشاكل المتعلقة بمزامنة الدليل Microsoft 365 لتصحيح أي مشاكل محددة.