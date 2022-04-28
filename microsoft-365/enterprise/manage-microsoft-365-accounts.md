---
title: إدارة حسابات المستخدمين Microsoft 365
ms.author: kvice
author: kelleyvice-msft
manager: scotv
audience: Admin
ms.topic: overview
ms.prod: office-online-server
ms.localizationpriority: medium
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- seo-marvel-mar2020
- admindeeplinkMAC
ms.collection:
- Ent_O365
- M365-subscription-management
search.appverid:
- MET150
- MOE150
- MED150
- BCS160
ms.assetid: 98ca5b3f-f720-4d8e-91be-fe656548a25a
description: تعرف على كيفية إدارة حسابات المستخدمين Microsoft 365.
ms.openlocfilehash: dbd1c0a3c1c6fdb10d157299552e83a77f495e3c
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/27/2022
ms.locfileid: "65098329"
---
# <a name="manage-microsoft-365-user-accounts"></a>إدارة حسابات المستخدمين Microsoft 365

يمكنك إدارة حسابات المستخدمين Microsoft 365 بعدة طرق مختلفة، اعتمادا على التكوين الخاص بك. يمكنك إدارة حسابات المستخدمين في [مركز مسؤولي Microsoft 365 أو](/admin) [PowerShell](manage-user-accounts-and-licenses-with-microsoft-365-powershell.md) أو في خدمات مجال Active Directory (AD DS) أو في مدخل مسؤول Azure Active Directory (Azure AD). 

بمجرد شراء Microsoft 365، يمكن استخدام <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">مركز مسؤولي Microsoft 365</a> وPowerShell لإدارة الحسابات. عند إدارة الهويات السحابية، يكون لكل شخص في مؤسستك اسم حساب مستخدم وكلمة مرور منفصلين. إذا كنت تريد التكامل مع البنية الأساسية المحلية لديك ومزامنة حسابات المستخدمين مع Microsoft 365، يمكنك استخدام الاتصال Azure AD لتوفير مزامنة الهويات وكلمات المرور لوظائف تسجيل الدخول الأحادي (SSO).
  
## <a name="plan-for-where-and-how-you-will-manage-your-user-accounts"></a>التخطيط لمكان وكيفية إدارة حسابات المستخدمين

يعتمد مكان وكيفية إدارة حسابات المستخدمين على نموذج الهوية الذي تريد استخدامه Microsoft 365. النموذجان العامان هما السحابة فقط والمختلطة.
  
### <a name="cloud-only"></a>السحابة فقط

يمكنك إنشاء المستخدمين وإدارتهم في <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">مركز مسؤولي Microsoft 365</a>. يمكنك أيضا استخدام PowerShell أو مركز إدارة Azure AD. 
    
### <a name="hybrid"></a>مختلط

تتم مزامنة حسابات المستخدمين مع Microsoft 365 من AD DS، لذلك يجب استخدام أدوات AD DS المحلية لإدارة حسابات المستخدمين. 
    
## <a name="managing-accounts"></a>إدارة الحسابات

عند تحديد الطريقة التي ستقوم بها مؤسستك بإنشاء الحسابات وإدارتها، ضع في اعتبارك المتطلبات التالية:
  
- يجب تثبيت برنامج مزامنة الدليل على خوادم داخل بيئتك المحلية لتوصيل الهويات بين Microsoft 365 و AD DS.
    
- يتطلب أي خيار مزامنة دليل، بما في ذلك خيارات SSO، أن تفي سمات AD DS بالمعايير. يتم وصف تفاصيل السمات المستخدمة في الدليل والتنظيف (إن وجد) في [الإعداد لمزامنة الدليل إلى Microsoft 365](prepare-for-directory-synchronization.md). 
    
- خطط لكيفية إنشاء حسابات Microsoft 365.
    
يسرد الجدول التالي أدوات إدارة الحساب المختلفة.
    
|أداة|ملاحظات|
|:-----|:-----|
|مركز مسؤولي Microsoft 365  <br/> |[إضافة مستخدمين بشكل فردي أو مجمع](../admin/add-users/add-users.md) <br/>  يوفر واجهة ويب بسيطة لإضافة حسابات المستخدمين وتغييرها.  <br/>  لا يمكن استخدام تغيير المستخدمين إذا تم تمكين مزامنة الدليل (يمكن تعيين تعيين الموقع والترخيص).  <br/>  لا يمكن استخدامها مع خيارات SSO.  <br/> |
|Windows PowerShell  <br/> |[إدارة Microsoft 365 باستخدام Windows PowerShell](./manage-microsoft-365-with-microsoft-365-powershell.md) <br/>  يسمح لك بإضافة مستخدمين في مجموعة من المستخدمين باستخدام برنامج نصي Windows PowerShell.  <br/>  يمكن استخدامها لتعيين الموقع والتراخيص للحسابات، بغض النظر عن كيفية إنشاء الحسابات.  <br/> |
|استيراد مجمع  <br/> |[إضافة عدة مستخدمين في الوقت نفسه](add-several-users-at-the-same-time.md) <br/>  يسمح لك باستيراد ملف CSV لإضافة مجموعة من المستخدمين إلى Microsoft 365.  <br/>  لا يمكن استخدامها مع خيارات SSO.  <br/> |
|Azure AD  <br/> |يمكنك الحصول على إصدار مجاني من Azure AD مع اشتراكك في Microsoft 365. يمكنك تنفيذ وظائف مثل إعادة تعيين كلمة مرور الخدمة الذاتية لمستخدمي السحابة، وتخصيص صفحات تسجيل الدخول لوحة الوصول باستخدام الإصدار المجاني. للحصول على وظائف محسنة، يمكنك الترقية إلى الإصدار الأساسي أو Azure AD Premium P1 أو Azure AD Premium P2. راجع [إصدارات Azure AD](/azure/active-directory/fundamentals/active-directory-whatis) للحصول على قائمة الميزات المدعومة.  <br/> |
|مزامنة الدليل  <br/> |[دمج الهويات المحلية مع Azure AD](/azure/active-directory/hybrid/whatis-hybrid-identity) <br/>  لمزامنة الدليل مع مزامنة كلمة المرور أو بدونها، استخدم [الاتصال Azure AD مع الإعدادات السريعة](/azure/active-directory/hybrid/how-to-connect-install-express).  <br/>  بالنسبة إلى الغابات المتعددة وخيارات تسجيل الدخول الأحادي، استخدم [التثبيت المخصص ل Azure AD الاتصال](/azure/active-directory/hybrid/how-to-connect-install-custom).  <br/>  يوفر البنية الأساسية الضرورية لتمكين تسجيل الدخول الأحادي.  <br/>  مطلوب للعديد من السيناريوهات المختلطة مثل الترحيل المرحلي Exchange  <br/>  مزامنة مجموعات الأمان والمجموعات الممكنة للبريد من AD DS.  <br/> |
|||
   
- بغض النظر عن الطريقة التي تنوي بها إضافة حسابات المستخدمين إلى Microsoft 365، تحتاج إلى إدارة العديد من ميزات الحساب، مثل تعيين التراخيص وتحديد الموقع وما إلى ذلك. يمكن إدارة هذه الميزات على المدى الطويل من <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">مركز مسؤولي Microsoft 365</a> أو يمكنك أيضا [إنشاء حسابات المستخدمين باستخدام PowerShell](./create-user-accounts-with-microsoft-365-powershell.md).
    
    إذا اخترت إضافة جميع المستخدمين وإدارتهم من خلال مركز الإدارة، فستحدد الموقع وتعين التراخيص في نفس الوقت الذي تنشئ فيه حساب Microsoft 365. ونتيجة لذلك، لا يلزم الكثير من التخطيط.
    
    > [!IMPORTANT]
    > يعني إنشاء حسابات في Microsoft 365 دون تعيين ترخيص (إلى SharePoint Online، على سبيل المثال) أن مالك الحساب يمكنه عرض مركز Microsoft 365 ولكن لا يمكنه الوصول إلى أي من الخدمات ضمن اشتراك شركتك. بعد تعيين موقع والترخيص، يتم نسخ الحساب إلى الخدمة أو الخدمات التي قمت بتعيينها. يمكن للمستخدم تسجيل الدخول إلى حسابه واستخدام الخدمات التي قمت بتعيينها له. 
  
## <a name="see-also"></a>راجع أيضًا

[مركز مسؤولي Microsoft 365](/admin)

[PowerShell](manage-user-accounts-and-licenses-with-microsoft-365-powershell.md)