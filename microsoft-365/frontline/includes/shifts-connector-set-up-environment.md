---
author: LanaChin
ms.author: v-lanachin
ms.date: 03/31/2022
ms.topic: include
audience: admin
ms.service: msteams
ms.openlocfilehash: 3d4ec38f0007460fa119e69eadc79cd9c51887ee
ms.sourcegitcommit: 5e5c2c1f7c321b5eb1c5b932c03bdd510005de13
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/15/2022
ms.locfileid: "66823625"
---
1. تثبيت الإصدار 7 من PowerShell أو إصدار أحدث. للحصول على إرشادات خطوة بخطوة، راجع [تثبيت PowerShell على Windows](/powershell/scripting/install/installing-powershell-on-windows).

1. تشغيل PowerShell في وضع المسؤول.
1. تثبيت وحدة Microsoft Graph PowerShell.

    ```powershell
    Install-Module Microsoft.Graph
    Import-Module Microsoft.Graph
    ```

    تحقق من أنه الإصدار 1.6.1 أو أحدث.

    ```powershell
    Get-InstalledModule Microsoft.Graph 
    ```

1. تثبيت الوحدة النمطية معاينة Teams PowerShell.

    ```powershell
    Install-Module -Name MicrosoftTeams -AllowPrerelease -Force
    Import-Module MicrosoftTeams 
    ```

    تحقق من أنه الإصدار 4.1.0 على الأقل ويحتوي على أوامر cmdlets لموصل Shifts.

    ```powershell
    Get-Command -Module MicrosoftTeams -Name *teamsshiftsconnection* 
    ```

1. قم بتعيين PowerShell للإنهاء إذا حدث خطأ عند تشغيل البرنامج النصي.

    ```powershell
    $ErrorActionPreference = "Stop" 
    ```

1. تمكين تشغيل البرامج النصية في Windows.

    ```powershell
    Set-ExecutionPolicy bypass 
    ```