---
title: إيقاف تشغيل مزامنة الدليل Microsoft 365
ms.author: kvice
author: kelleyvice-msft
manager: scotv
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
description: في هذه المقالة، ابحث عن معلومات حول استخدام PowerShell لإيقاف تشغيل مزامنة الدليل Microsoft 365.
ms.openlocfilehash: 5082f89032c17e549f11f8397126f6d059937c48
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/27/2022
ms.locfileid: "65077347"
---
# <a name="turn-off-directory-synchronization-for-microsoft-365"></a>إيقاف تشغيل مزامنة الدليل Microsoft 365
يمكنك استخدام PowerShell لإيقاف تشغيل مزامنة الدليل وتحويل المستخدمين المتزامنين إلى السحابة فقط. ومع ذلك، من غير المستحسن إيقاف تشغيل مزامنة الدليل كخطوة استكشاف الأخطاء وإصلاحها. إذا كنت بحاجة إلى مساعدة في استكشاف أخطاء مزامنة الدليل وإصلاحها، فراجع [إصلاح المشاكل المتعلقة بمزامنة الدليل لمقالة Microsoft 365](fix-problems-with-directory-synchronization.md). 
  
[اتصل بالدعم](https://support.office.com/article/32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b) لمنتجات الأعمال إذا لزم الأمر.
  
## <a name="turn-off-directory-synchronization"></a>إيقاف تشغيل مزامنة الدليل  
لإيقاف تشغيل مزامنة الدليل:
  
1. أولا، قم بتثبيت البرنامج المطلوب والاتصال باشتراكك في Microsoft 365. للحصول على الإرشادات، راجع [الاتصال مع الوحدة النمطية Microsoft Azure Active Directory Windows PowerShell](connect-to-microsoft-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).
    
2. استخدم [Set-MsolDirSyncEnabled](/previous-versions/azure/dn194097(v=azure.100)) لتعطيل مزامنة الدليل: 
    
  ```powershell
  Set-MsolDirSyncEnabled -EnableDirSync $false
  ```

>[!Note]
>إذا كنت تستخدم هذا الأمر، يجب الانتظار 72 ساعة قبل أن تتمكن من تشغيل مزامنة الدليل مرة أخرى.
>
