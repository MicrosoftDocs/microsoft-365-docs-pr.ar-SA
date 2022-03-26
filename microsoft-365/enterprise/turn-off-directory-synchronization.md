---
title: إيقاف تشغيل مزامنة الدليل Microsoft 365
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
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOE150
- MED150
ms.assetid: ee5f861e-bd48-4267-83d1-a4ead4b4a00d
description: في هذه المقالة، ابحث عن معلومات حول استخدام PowerShell إيقاف تشغيل مزامنة الدليل Microsoft 365.
ms.openlocfilehash: 83a3d66493994800a71a1910332a5eb2cdb003cd
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 10/06/2021
ms.locfileid: "63572817"
---
# <a name="turn-off-directory-synchronization-for-microsoft-365"></a>إيقاف تشغيل مزامنة الدليل Microsoft 365
يمكنك استخدام PowerShell إيقاف تشغيل مزامنة الدليل وتحويل المستخدمين المتزامنين إلى مجموعة النظراء فقط. ومع ذلك، من غير المستحسن إيقاف تشغيل مزامنة الدليل كخطوة استكشاف الأخطاء وإصلاحها. إذا كنت بحاجة إلى المساعدة في استكشاف الأخطاء وإصلاحها في مزامنة الدليل، فشاهد مقالة إصلاح المشاكل [المتعلقة بمزامنة الدليل Microsoft 365](fix-problems-with-directory-synchronization.md) التالية. 
  
[اتصل ب](https://support.office.com/article/32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b) دعم منتجات الأعمال إذا لزم الأمر.
  
## <a name="turn-off-directory-synchronization"></a>إيقاف تشغيل مزامنة الدليل  
إيقاف تشغيل مزامنة الدليل:
  
1. أولا، قم بتثبيت البرنامج المطلوب واتصل باشتراكك Microsoft 365. للحصول على الإرشادات، [راجع الاتصال مع Microsoft Azure Active Directory النمطية Windows PowerShell](connect-to-microsoft-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).
    
2. استخدم [Set-MsolDirSyncEnabled](/previous-versions/azure/dn194097(v=azure.100)) لتعطيل مزامنة الدليل: 
    
  ```powershell
  Set-MsolDirSyncEnabled -EnableDirSync $false
  ```

>[!Note]
>إذا كنت تستخدم هذا الأمر، فيجب الانتظار 72 ساعة قبل أن تتمكن من تشغيل مزامنة الدليل مرة أخرى.
>
