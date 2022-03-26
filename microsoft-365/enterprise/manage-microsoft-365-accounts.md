---
title: إدارة Microsoft 365 المستخدمين
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
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
description: تعرف على كيفية إدارة Microsoft 365 المستخدمين.
ms.openlocfilehash: 7f75c74984ce58a8b403f01948075b185047f260
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 10/06/2021
ms.locfileid: "63568788"
---
# <a name="manage-microsoft-365-user-accounts"></a>إدارة Microsoft 365 المستخدمين

يمكنك إدارة Microsoft 365 المستخدمين بعدة طرق مختلفة، استنادا إلى التكوين الذي تقوم به. يمكنك إدارة حسابات المستخدمين في مركز مسؤولي Microsoft 365 [](/admin)[أو PowerShell](manage-user-accounts-and-licenses-with-microsoft-365-powershell.md) أو في خدمات مجال Active Directory (AD DS) أو في مدخل مسؤول Azure Active Directory (Azure AD). 

بمجرد شراء Microsoft 365، يمكن استخدام مركز مسؤولي Microsoft 365 و PowerShell <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank"></a> لإدارة الحسابات. عند إدارة الهويات السحابية، يكون لكل شخص في مؤسستك اسم حساب مستخدم وكلمة مرور منفصلين. إذا كنت تريد التكامل مع البنية الأساسية المحلية لديك ومزامنة حسابات المستخدمين مع Microsoft 365، يمكنك استخدام Azure AD الاتصال لتوفير مزامنة الهويات وكلمات المرور لوظائف تسجيل الدخول الفردي (SSO).
  
## <a name="plan-for-where-and-how-you-will-manage-your-user-accounts"></a>التخطيط للكيفية التي ستدير بها حسابات المستخدمين وكيفية إدارتها

يعتمد مكان إدارة حسابات المستخدمين وكيفية إدارتها على نموذج الهوية الذي تريد استخدامه Microsoft 365. النموذجان الإجماليان مختلطان وسحابي فقط.
  
### <a name="cloud-only"></a>السحابة فقط

يمكنك إنشاء المستخدمين وإدارتهم في <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">مركز مسؤولي Microsoft 365</a>. يمكنك أيضا استخدام PowerShell أو مركز إدارة Azure AD. 
    
### <a name="hybrid"></a>مختلط

يتم مزامنة حسابات المستخدمين Microsoft 365 من AD DS، لذلك يجب استخدام أدوات AD DS في الموقع لإدارة حسابات المستخدمين. 
    
## <a name="managing-accounts"></a>إدارة الحسابات

عند تحديد الطريقة التي ستتبعها مؤسستك لإنشاء الحسابات وإدارتها، يجب أخذ المتطلبات التالية في الاعتبار:
  
- يجب تثبيت برنامج مزامنة الدليل على الخوادم داخل بيئتك المحلية لربط الهويات بين Microsoft 365 وDS AD.
    
- يتطلب أي خيار لمزامنة الدليل، بما في ذلك خيارات SSO، أن تفي سمات AD DS بالمعايير. يتم وصف خصائص السمات المستخدمة في الدليل والتنظيف المطلوب (إن وجدت) في [الإعداد](prepare-for-directory-synchronization.md) لمزامنة الدليل Microsoft 365. 
    
- خطط كيف ستنشئ حسابات Microsoft 365 أخرى.
    
يسرد الجدول التالي أدوات إدارة الحسابات المختلفة.
    
|أداة|ملاحظات|
|:-----|:-----|
|مركز مسؤولي Microsoft 365  <br/> |[إضافة مستخدمين بشكل فردي أو مجمع](../admin/add-users/add-users.md) <br/>  يوفر واجهة ويب بسيطة لإضافة حسابات المستخدمين وتغييرها.  <br/>  لا يمكن استخدامه لتغيير المستخدمين إذا تم تمكين مزامنة الدليل (يمكن تعيين الموقع والترخيص).  <br/>  لا يمكن استخدامه مع خيارات SSO.  <br/> |
|Windows PowerShell  <br/> |[إدارة Microsoft 365 باستخدام Windows PowerShell](./manage-microsoft-365-with-microsoft-365-powershell.md) <br/>  يسمح لك بإضافة مستخدمين في مجموعة من المستخدمين باستخدام برنامج نصي Windows PowerShell نصي.  <br/>  يمكن استخدامه لتعيين الموقع والتراخيص للحسابات، بغض النظر عن كيفية إنشاء الحسابات.  <br/> |
|استيراد مجمع  <br/> |[إضافة عدة مستخدمين في الوقت نفسه](add-several-users-at-the-same-time.md) <br/>  يسمح لك باستيراد ملف CSV لإضافة مجموعة من المستخدمين Microsoft 365.  <br/>  لا يمكن استخدامه مع خيارات SSO.  <br/> |
|Azure AD  <br/> |يمكنك الحصول على إصدار مجاني من Azure AD مع Microsoft 365 اشتراكك. يمكنك تنفيذ وظائف مثل إعادة تعيين كلمة مرور الخدمة الذاتية لمستخدمي السحابة وتخصيص صفحتي "تسجيل الدخول" و"لوحة الوصول" باستخدام الإصدار المجاني. للحصول على وظائف محسنة، يمكنك الترقية إلى الإصدار الأساسي أو Azure AD Premium P1 أو Azure AD Premium P2. راجع [إصدارات Azure AD](/azure/active-directory/fundamentals/active-directory-whatis) للحصول على قائمة الميزات المعتمدة.  <br/> |
|مزامنة الدليل  <br/> |[دمج الهويات في الموقع مع Azure AD](/azure/active-directory/hybrid/whatis-hybrid-identity) <br/>  لمزامنة الدليل مع مزامنة كلمة المرور أو بدونها، استخدم [Azure AD الاتصال إعدادات صريحة](/azure/active-directory/hybrid/how-to-connect-install-express).  <br/>  للحصول على خيارات SSO والغابات المتعددة، استخدم التثبيت [المخصص ل Azure AD الاتصال](/azure/active-directory/hybrid/how-to-connect-install-custom).  <br/>  يوفر البنية الأساسية الضرورية لتمكين SSO.  <br/>  مطلوب للعديد من السيناريوهات المختلطة مثل الترحيل المرحلة والسيناريوهات Exchange  <br/>  مزامنة مجموعات الأمان والمجموعات التي تم تمكين البريد لها من AD DS.  <br/> |
|||
   
- بغض النظر عن الطريقة التي تنوي بها إضافة حسابات المستخدمين إلى Microsoft 365، ستحتاج إلى إدارة العديد من ميزات الحساب، مثل تعيين التراخيص وتحديد الموقع وما إلى ذلك. يمكن إدارة هذه الميزات على المدى الطويل من <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">مركز مسؤولي Microsoft 365 أو يمكنك</a> أيضا إنشاء حسابات [المستخدمين باستخدام PowerShell](./create-user-accounts-with-microsoft-365-powershell.md).
    
    إذا اخترت إضافة جميع المستخدمين وإدارتهم من خلال مركز الإدارة، سيتم تحديد الموقع وتعيين التراخيص في الوقت نفسه عند Microsoft 365 الحساب. ونتيجة لذلك، لا يتطلب الأمر الكثير من التخطيط.
    
    > [!IMPORTANT]
    > يعني إنشاء الحسابات في Microsoft 365 دون تعيين ترخيص (على سبيل المثال، إلى SharePoint Online) أنه يمكن لمالك الحساب عرض مركز Microsoft 365 ولكن لا يمكنه الوصول إلى أي من الخدمات ضمن اشتراك شركتك. بعد تعيين موقع والترخيص، يتم نسخ الحساب بشكل متماثل إلى الخدمة أو الخدمات التي عينتها. يمكن للمستخدم تسجيل الدخول إلى حسابه واستخدام الخدمات التي عينتها له. 
  
## <a name="see-also"></a>راجع أيضًا

[مركز مسؤولي Microsoft 365](/admin)

[PowerShell](manage-user-accounts-and-licenses-with-microsoft-365-powershell.md)