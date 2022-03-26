---
title: إعداد مجال غير قابل التوجيه لمزامنة الدليل
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
description: تعرف على ما يجب فعله إذا كان لديك مجال غير قابل التوجيه مقترن وحسابات المستخدمين في الموقع قبل مزامنتها مع Microsoft 365 المستأجر.
ms.openlocfilehash: bea80123c1a2db11baa07cd3344f65303cdd1084
ms.sourcegitcommit: 355ab75eb7b604c6afbe9a5a1b97ef16a1dec4fc
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 02/14/2022
ms.locfileid: "63572888"
---
# <a name="prepare-a-non-routable-domain-for-directory-synchronization"></a>إعداد مجال غير قابل التوجيه لمزامنة الدليل

عند مزامنة الدليل المحلي مع Microsoft 365، يجب أن يكون لديك مجال متحقق منه في Azure Active Directory (Azure AD). لا يتم مزامنة سوى أسماء المستخدمين الأساسية (UPNs) المقترنة بالمجال المحلي خدمات مجال Active Directory (AD DS). ومع ذلك، فإن أي UPN يحتوي على مجال غير قابل التوجيه، مثل "local" (على سبيل المثال: billa@contoso.local)، سيتم مزامنته إلى مجال .onmicrosoft.com (على سبيل المثال: billa@contoso.onmicrosoft.com). 

إذا كنت تستخدم حاليا مجال "محلي" حسابات المستخدمين في AD DS، فمن المستحسن تغييرها لاستخدام مجال تم التحقق منه، مثل billa@contoso.com، من أجل المزامنة بشكل صحيح مع مجالك Microsoft 365.
  
## <a name="what-if-i-only-have-a-local-on-premises-domain"></a>ماذا لو كان لدي مجال محلي "محلي" فقط؟

يمكنك استخدام Azure AD الاتصال لمزامنة AD DS مع مستأجر Azure AD لمستأجر Microsoft 365 المستأجر. لمزيد من المعلومات، راجع [تكامل الهويات الخاصة بك مع Azure AD](/azure/architecture/reference-architectures/identity/azure-ad).
  
يقوم Azure AD الاتصال مزامنة UPN وكلمة المرور الخاصة بالمستخدمين بحيث يمكن للمستخدمين تسجيل الدخول باستخدام بيانات الاعتماد نفسها التي يستخدمونها في الموقع. ومع ذلك، فإن Azure AD الاتصال يقوم فقط بمزامنة المستخدمين مع المجالات التي تم التحقق منها بواسطة Microsoft 365. وهذا يعني أنه يتم أيضا التحقق من المجال بواسطة Azure AD لأن Microsoft 365 مدارة بواسطة Azure AD. بعبارة أخرى، يجب أن يكون المجال مجال إنترنت صالحا (مثل .com و .org و .net و .us). إذا كانت AD DS الداخلية تستخدم مجالا غير قابل التوجيه فقط (على سبيل المثال، "محلي")، فهذا لا يمكن أن يطابق المجال المتحقق منه لديك Microsoft 365 المستأجر. يمكنك إصلاح هذه المشكلة إما بتغيير مجالك الأساسي في AD DS المحلية، أو بإضافة لاحقة UPN واحدة أو أكثر.
  
### <a name="change-your-primary-domain"></a>تغيير مجالك الأساسي

غير مجالك الأساسي إلى مجال قمت بالتحقق منه في Microsoft 365، على سبيل المثال، contoso.com. يتم بعد ذلك تحديث كل مستخدم لديه المجال contoso.local contoso.com. ومع ذلك، هذه عملية متبعة، كما يتم وصف حل أسهل في القسم التالي.
  
### <a name="add-upn-suffixes-and-update-your-users-to-them"></a>إضافة لاحقات UPN وتحديث المستخدمين إليها

يمكنك حل المشكلة "local" بتسجيل لاحقة UPN أو لاحقات جديدة في AD DS لمطابقة المجال (أو المجالات) الذي تحققت منه في Microsoft 365. بعد تسجيل اللاحقة الجديدة، قم بتحديث أسماء UPN الخاصة بالمستخدم لاستبدال "local" باسم المجال الجديد، على سبيل المثال، بحيث يبدو حساب المستخدم مثل billa@contoso.com.
  
بعد تحديث UPNs لاستخدام المجال الذي تم التحقق منه، ستكون جاهزا لمزامنة AD DS في الموقع مع Microsoft 365.
  
#### <a name="step-1-add-the-new-upn-suffix"></a>الخطوة 1: إضافة لاحقة UPN الجديدة**
  
1. في وحدة تحكم مجال AD DS، في إدارة الخادم، اختر **أدوات** \> **مجالات Active Directory والثقة**.
    
    **أو، إذا لم يكن لديك Windows Server 2012**
    
    اضغط **Windows مفتاح + R** لفتح مربع الحوار تشغيل، ثم  اكتب في Domain.msc، ثم اختر **موافق**.
    
    ![اختر مجالات Active Directory والثقة.](../media/46b6e007-9741-44af-8517-6f682e0ac974.png)
  
2. في نافذة **مجالات Active Directory** وثقته، انقر بز الماوس الأيمن فوق مجالات **Active Directory** وثقته، ثم اختر **خصائص**.
    
    ![انقر بز الماوس الأيمن فوق مجالات Active Directory وثقته واختر خصائص.](../media/39d20812-ffb5-4ba9-8d7b-477377ac360d.png)
  
3. على علامة **التبويب لاحقات UPN** ، في المربع لاحقات **UPN** البديلة، اكتب لاحقة UPN أو لاحقات جديدة، ثم اختر **إضافة** \> **تطبيق**.
    
    ![إضافة لاحقة UPN جديدة.](../media/a4aaf919-7adf-469a-b93f-83ef284c0915.PNG)
  
    اختر **موافق** عند انتهاء إضافة لاحقات. 
    
 #### <a name="step-2-change-the-upn-suffix-for-existing-users"></a>الخطوة 2: تغيير لاحقة UPN للمستخدمين  الموجودين
  
1. في وحدة تحكم مجال AD DS، في إدارة الخادم، اختر **أدوات** \> **Active Directory Users وأجهزة الكمبيوتر**.
    
    **أو، إذا لم يكن لديك Windows Server 2012**
    
    اضغط **Windows مفتاح + R** لفتح مربع الحوار تشغيل، ثم  اكتب في Dsa.msc، ثم انقر فوق **موافق**
    
2. حدد مستخدما، وانقر بضغطة زر الماوس الأيمن، ثم اختر **خصائص**.
    
3. على علامة **التبويب** حساب، في القائمة المنسدل لاحقة UPN، اختر لاحقة UPN الجديدة، ثم اختر **موافق**.
    
    ![إضافة لاحقة UPN جديدة لمستخدم.](../media/54876751-49f0-48cc-b864-2623c4835563.png)
  
4. أكمل هذه الخطوات لكل مستخدم.
    
   
### <a name="use-powershell-to-change-the-upn-suffix-for-all-of-your-users"></a>استخدام PowerShell لتغيير لاحقة UPN لجميع المستخدمين

إذا كان لديك العديد من حسابات المستخدمين لتحديثها، فمن الأسهل استخدام PowerShell. يستخدم المثال التالي cmdlets [Get-ADUser](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/ee617241(v=technet.10)) و [Set-ADUser](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/ee617215(v=technet.10)) لتغيير كل لاحقات contoso.local contoso.com AD DS. 

على سبيل المثال، يمكنك تشغيل أوامر PowerShell التالية لتحديث كل لاحقات contoso.local contoso.com:
    
  ```powershell
  $LocalUsers = Get-ADUser -Filter "UserPrincipalName -like '*contoso.local'" -Properties userPrincipalName -ResultSetSize $null
  $LocalUsers | foreach {$newUpn = $_.UserPrincipalName.Replace("@contoso.local","@contoso.com"); $_ | Set-ADUser -UserPrincipalName $newUpn}
  ```

راجع [Active Directory Windows PowerShell النمطية](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/ee617195(v=technet.10)) للتعرف على المزيد حول استخدام Windows PowerShell في AD DS.