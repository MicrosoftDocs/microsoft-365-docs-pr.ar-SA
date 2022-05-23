---
title: إعداد مجال غير قابل للتوجيه لمزامنة الدليل
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
- O365E_SetupDirSyncLocalDir
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOE150
- MED150
- BCS160
ms.assetid: e7968303-c234-46c4-b8b0-b5c93c6d57a7
description: تعرف على ما يجب فعله إذا كان لديك مجال غير قابل للتوجيه مقترن بحسابات المستخدمين المحليين قبل مزامنتها مع مستأجر Microsoft 365.
ms.openlocfilehash: 9d720b42b345e85031a4fa34b9c1353f868765f1
ms.sourcegitcommit: db1e48af88995193f15bbd5962f5101a6088074b
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 05/23/2022
ms.locfileid: "65637880"
---
# <a name="prepare-a-non-routable-domain-for-directory-synchronization"></a>إعداد مجال غير قابل للتوجيه لمزامنة الدليل

عند مزامنة الدليل المحلي مع Microsoft 365، يجب أن يكون لديك مجال تم التحقق منه في Azure Active Directory (Azure AD). تتم مزامنة أسماء المستخدمين الأساسيين (UPNs) المقترنة بمجال Active Directory محلي Domain Services (AD DS). ومع ذلك، ستتم مزامنة أي UPN يحتوي على مجال غير قابل للتوجيه، مثل "محلي" (على سبيل المثال: billa@contoso.local)، إلى مجال .onmicrosoft.com (على سبيل المثال: billa@contoso.onmicrosoft.com). 

إذا كنت تستخدم حاليا مجالا ".محليا" لحسابات المستخدمين في AD DS، فمن المستحسن تغييرها لاستخدام مجال تم التحقق منه، مثل billa@contoso.com، من أجل المزامنة بشكل صحيح مع مجال Microsoft 365.
  
## <a name="what-if-i-only-have-a-local-on-premises-domain"></a>ماذا لو كان لدي مجال محلي ".محلي" فقط؟

يمكنك استخدام Azure AD الاتصال لمزامنة AD DS مع المستأجر Azure AD لمستأجر Microsoft 365. لمزيد من المعلومات، راجع [دمج الهويات المحلية مع Azure AD](/azure/architecture/reference-architectures/identity/azure-ad).
  
Azure AD الاتصال مزامنة UPN وكلمة المرور الخاصة بالمستخدمين بحيث يمكن للمستخدمين تسجيل الدخول باستخدام نفس بيانات الاعتماد التي يستخدمونها محليا. ومع ذلك، Azure AD الاتصال مزامنة المستخدمين فقط مع المجالات التي يتم التحقق منها بواسطة Microsoft 365. وهذا يعني أنه يتم التحقق من المجال أيضا بواسطة Azure AD لأن الهويات Microsoft 365 تتم إدارتها بواسطة Azure AD. بمعنى آخر، يجب أن يكون المجال مجال إنترنت صالحا (مثل.com أو .org أو .net أو .us). إذا كان AD DS الداخلي يستخدم مجالا غير قابل للتوجيه فقط (على سبيل المثال، "محلي")، فمن المحتمل ألا يتطابق هذا مع المجال الذي تم التحقق منه لمستأجر Microsoft 365. يمكنك إصلاح هذه المشكلة إما عن طريق تغيير مجالك الأساسي في AD DS المحلي، أو بإضافة لاحقة UPN واحدة أو أكثر.
  
### <a name="change-your-primary-domain"></a>تغيير مجالك الأساسي

قم بتغيير مجالك الأساسي إلى مجال قمت بالتحقق منه في Microsoft 365، على سبيل المثال، contoso.com. ثم يتم تحديث كل مستخدم لديه المجال contoso.local إلى contoso.com. ومع ذلك، هذه عملية مضمنة، ويتم وصف حل أسهل في القسم التالي.
  
### <a name="add-upn-suffixes-and-update-your-users-to-them"></a>إضافة لاحقات UPN وتحديث المستخدمين إليها

يمكنك حل المشكلة ".local" عن طريق تسجيل لاحقة UPN جديدة أو لاحقات جديدة في AD DS لمطابقة المجال (أو المجالات) التي تحققت منها في Microsoft 365. بعد تسجيل اللاحقة الجديدة، يمكنك تحديث UPNs للمستخدم لاستبدال ".local" باسم المجال الجديد، على سبيل المثال، بحيث يبدو حساب المستخدم مثل billa@contoso.com.
  
بعد تحديث UPNs لاستخدام المجال الذي تم التحقق منه، تكون جاهزا لمزامنة AD DS المحلي مع Microsoft 365.
  
#### <a name="step-1-add-the-new-upn-suffix"></a>الخطوة 1: إضافة لاحقة UPN الجديدة
  
1. في وحدة تحكم مجال AD DS، في Server Manager، اختر **"أدوات** \> **Active Directory Domains and Trusts**".
    
    **أو إذا لم يكن لديك Windows Server 2012**
    
    اضغط **على مفتاح Windows + R** لفتح مربع الحوار **"تشغيل**"، ثم اكتب في Domain.msc، ثم اختر **"موافق**".
    
    ![اختر مجالات Active Directory والثقة.](../media/46b6e007-9741-44af-8517-6f682e0ac974.png)
  
2. في نافذة **مجالات Active Directory والثقة** ، انقر بزر الماوس الأيمن فوق **مجالات Active Directory والثقة**، ثم اختر **"خصائص**".
    
    ![انقر بزر الماوس الأيمن فوق مجالات Active Directory والثقة واختر "خصائص".](../media/39d20812-ffb5-4ba9-8d7b-477377ac360d.png)
  
3. في علامة التبويب **"لاحقات UPN** "، في المربع **"لاحقات UPN البديلة** "، اكتب لاحقة أو لاحقات UPN الجديدة، ثم اختر **"إضافة** \> **تطبيق**".
    
    ![إضافة لاحقة UPN جديدة.](../media/a4aaf919-7adf-469a-b93f-83ef284c0915.PNG)
  
    اختر **"موافق** " عند الانتهاء من إضافة اللاحقات. 
    
 #### <a name="step-2-change-the-upn-suffix-for-existing-users"></a>الخطوة 2: تغيير لاحقة UPN للمستخدمين الحاليين
  
1. في وحدة تحكم مجال AD DS، في Server Manager اختر **"أدوات** \> **" Active Directory Users and Computers**.
    
    **أو إذا لم يكن لديك Windows Server 2012**
    
    اضغط **على مفتاح Windows + R** لفتح مربع الحوار **"تشغيل**"، ثم اكتب Dsa.msc، ثم انقر فوق **"موافق"**
    
2. حدد مستخدما، وانقر بزر الماوس الأيمن، ثم اختر **"خصائص**".
    
3. على علامة التبويب **"حساب** "، في القائمة المنسدلة للاحقة UPN، اختر لاحقة UPN الجديدة، ثم اختر **"موافق**".
    
    ![إضافة لاحقة UPN جديدة لمستخدم.](../media/54876751-49f0-48cc-b864-2623c4835563.png)
  
4. أكمل هذه الخطوات لكل مستخدم.
    
   
### <a name="use-powershell-to-change-the-upn-suffix-for-all-of-your-users"></a>استخدام PowerShell لتغيير لاحقة UPN لجميع المستخدمين

إذا كان لديك العديد من حسابات المستخدمين للتحديث، فمن الأسهل استخدام PowerShell. يستخدم المثال التالي أوامر cmdlets [Get-ADUser](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/ee617241(v=technet.10)) و [Set-ADUser](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/ee617215(v=technet.10)) لتغيير كافة لاحقات contoso.local إلى contoso.com في AD DS. 

على سبيل المثال، يمكنك تشغيل أوامر PowerShell التالية لتحديث كافة لاحقات contoso.local إلى contoso.com:
    
  ```powershell
  $LocalUsers = Get-ADUser -Filter "UserPrincipalName -like '*contoso.local'" -Properties userPrincipalName -ResultSetSize $null
  $LocalUsers | foreach {$newUpn = $_.UserPrincipalName.Replace("@contoso.local","@contoso.com"); $_ | Set-ADUser -UserPrincipalName $newUpn}
  ```

راجع [الوحدة النمطية Windows PowerShell Active Directory](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/ee617195(v=technet.10)) لمعرفة المزيد حول استخدام Windows PowerShell في AD DS.
