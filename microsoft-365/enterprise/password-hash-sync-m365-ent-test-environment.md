---
title: مزامنة كلمة المرور لبيئة اختبار Microsoft 365 المرور
f1.keywords:
- NOCSH
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 05/26/2020
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.localizationpriority: medium
ms.collection:
- M365-identity-device-management
- Strat_O365_Enterprise
ms.custom:
- TLG
- Ent_TLGs
- seo-marvel-apr2020
ms.assetid: ''
description: 'ملخص: تكوين مزامنة كلمة المرور وشرحها و تسجيل الدخول لبيئة Microsoft 365 الاختبار.'
ms.openlocfilehash: 746a0e1112df6ebf99569bfed58d08d0a4519d7a
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 10/06/2021
ms.locfileid: "63566491"
---
# <a name="password-hash-synchronization-for-your-microsoft-365-test-environment"></a>مزامنة كلمة المرور لبيئة اختبار Microsoft 365 المرور

*يمكن استخدام دليل Test Lab هذا Microsoft 365 لبيئات الاختبار Office 365 Enterprise المؤسسة.*

تستخدم العديد من المؤسسات مزامنة Azure AD الاتصال وكلمة المرور لمزامنة مجموعة الحسابات في غابة خدمات مجال Active Directory (AD DS) المحلية إلى مجموعة الحسابات في مستأجر Azure AD لاشتراك Microsoft 365. 

تصف هذه المقالة كيفية إضافة مزامنة كلمة المرور إلى Microsoft 365 الاختبار، مما يؤدي إلى هذا التكوين:
  
![المؤسسة التي تم محاكاتها مع بيئة اختبار مزامنة كلمة المرور.](../media/password-hash-sync-m365-ent-test-environment/Phase3.png)
  
يتضمن إعداد بيئة الاختبار هذه ثلاث مراحل:
- [المرحلة 1: إنشاء Microsoft 365 اختبار المؤسسة التي تم محاكاتها](#phase-1-create-the-microsoft-365-simulated-enterprise-test-environment)
- [المرحلة الثانية: إنشاء مجال testlab وتسجيله](#phase-2-create-and-register-the-testlab-domain)
- [المرحلة 3: تثبيت Azure AD الاتصال APP1](#phase-3-install-azure-ad-connect-on-app1)
    
> [!TIP]
> للحصول على خريطة مرئية لكل المقالات في Microsoft 365 دليل اختبار المؤسسة، انتقل إلى Microsoft 365 [دليل اختبار المؤسسة](../downloads/Microsoft365EnterpriseTLGStack.pdf).
  
## <a name="phase-1-create-the-microsoft-365-simulated-enterprise-test-environment"></a>المرحلة 1: إنشاء Microsoft 365 اختبار المؤسسة التي تم محاكاتها

اتبع الإرشادات الموجودة في [تكوين قاعدة المؤسسة المحاكاة Microsoft 365](simulated-ent-base-configuration-microsoft-365-enterprise.md). يبدو التكوين الناتج كما يلي:
  
![تكوين قاعدة المؤسسة الذي تم محاكاته.](../media/password-hash-sync-m365-ent-test-environment/Phase1.png)
  
يتكون هذا التكوين من:
  
- اشتراك Microsoft 365 E5 تجريبي أو مدفوع.
- إنترانت مؤسسة مبسطة متصلة بالإنترنت، تتكون من أجهزة DC1 و APP1 و CLIENT1 الظاهرية في شبكة Azure الظاهرية. DC1 هي وحدة تحكم مجال ل testlab.<اسم *مجالك* العام> AD DS.

## <a name="phase-2-create-and-register-the-testlab-domain"></a>المرحلة الثانية: إنشاء مجال testlab وتسجيله

في هذه المرحلة، أضف مجال DNS عام، ثم أضفه إلى اشتراكك.

أولا، اعمل مع موفر تسجيل DNS العام لإنشاء اسم مجال DNS عام جديد يستند إلى اسم مجالك الحالي، ثم قم بإضافته إلى اشتراكك. نوصي باستخدام **testlab.<*مجالك العام*>**. على سبيل المثال، إذا كان اسم مجالك العام **<span>contoso.com</span>**، أضف اسم المجال العام: **<span>testlab.contoso.com</span>**.
  
بعد ذلك، أضف **testlab.<*مجالك*>** العام إلى Microsoft 365 التجريبي أو المدفوع من خلال إجراء عملية تسجيل المجال. يتكون ذلك من إضافة سجلات DNS إضافية إلى **testlab.<*مجالك*>** العام. لمزيد من المعلومات، راجع [إضافة مجال Microsoft 365](../admin/setup/add-domain.md).

يبدو التكوين الناتج كما يلي:
  
![تسجيل اسم مجال testlab.](../media/password-hash-sync-m365-ent-test-environment/Phase2.png)
  
يتكون هذا التكوين من:

- يتم Microsoft 365 E5 تجريبي أو مدفوع باستخدام اختبار مجال DNS.<اسم مجالك العام> تسجيله.
- إنترانت مؤسسة مبسطة متصلة بالإنترنت، تتكون من أجهزة DC1 و APP1 و CLIENT1 الظاهرية على شبكة فرعية لشبكة Azure الظاهرية.

لاحظ كيف أن testlab.<*اسم مجالك* العام> الآن:

- معتمدة بواسطة سجلات DNS العامة.
- مسجل في Microsoft 365 اشتراكاتك.
- مجال AD DS على إنترانت المحاكاة.
     
## <a name="phase-3-install-azure-ad-connect-on-app1"></a>المرحلة 3: تثبيت Azure AD الاتصال APP1

في هذه المرحلة، قم بتثبيت أداة Azure AD الاتصال على APP1 وتكوينها، ثم تحقق من عملها.
  
أولا، قم بتثبيت Azure AD وتكوينه الاتصال APP1.

1. من مدخل [Azure،](https://portal.azure.com) سجل الدخول باستخدام حساب المسؤول العام، ثم اتصل ب APP1 باستخدام حساب TESTLABUser1\\.
    
2. من سطح المكتب ل APP1، افتح موجه أوامر على مستوى المسؤول Windows PowerShell، ثم قم بتشغيل هذه الأوامر لتعطيل الأمان المحسن ل Internet Explorer:
    
   ```powershell
   Set-ItemProperty -Path "HKLM:\SOFTWARE\Microsoft\Active Setup\Installed Components\{A509B1A7-37EF-4b3f-8CFC-4F3A74704073}" -Name "IsInstalled" -Value 0
   Set-ItemProperty -Path "HKLM:\SOFTWARE\Microsoft\Active Setup\Installed Components\{A509B1A8-37EF-4b3f-8CFC-4F3A74704073}" -Name "IsInstalled" -Value 0
   Stop-Process -Name Explorer -Force
   ```

3. من شريط المهام، حدد **Internet Explorer** واذهب إلى [https://aka.ms/aadconnect](https://aka.ms/aadconnect).
    
4. في صفحة Microsoft Azure Active Directory الاتصال، حدد **تنزيل**، ثم حدد **تشغيل**.
    
5. في صفحة **مرحبا بك في Azure AD الاتصال**، حدد **أوافق**، ثم حدد **متابعة**.
    
6. في صفحة **Express الإعدادات**، حدد **استخدام الإعدادات المعبرة**.
    
7. على الصفحة **الاتصال Azure AD**، أدخل اسم حساب المسؤول العام في اسم المستخدم، وأدخل  كلمة المرور الخاصة به في كلمة المرور، ثم حدد **التالي**.
    
8. في الصفحة **الاتصال AD DS**، أدخل **TESTLABUser1\\** في اسم المستخدم، وأدخل  كلمة المرور الخاصة به في كلمة المرور، ثم حدد **التالي**.
    
9. في الصفحة **جاهز لتكوين** ، حدد **تثبيت**.
    
10. في الصفحة **اكتمال التكوين** ، حدد **إنهاء**.
    
11. في Internet Explorer، انتقل إلى مركز مسؤولي Microsoft 365 ([https://portal.microsoft.com](https://portal.microsoft.com)).
    
12. في جزء التنقل الأيسر، حدد **المستخدمون > المستخدمون النشطون**.
    
    لاحظ الحساب المسمى **User1**. هذا الحساب من مجال TESTLAB AD DS وهو دليل على عمل مزامنة الدليل.
    
13. حدد حساب **User1** ، ثم حدد **التراخيص والتطبيقات**.
    
14. في **تراخيص المنتجات**، حدد موقعك (إذا لزم الأمر)، **Office 365 E5** ترخيص المنتج، ثم **قم بتمكين** Microsoft 365 E5 الترخيص. 

15. حدد **حفظ** في أسفل الصفحة، ثم حدد **إغلاق**.
    
بعد ذلك، اختبر إمكانية تسجيل الدخول إلى اشتراكك باستخدام user1@testlab **.<>** اسم مجالك اسم المستخدم لحساب User1:

1. من APP1، سجل الخروج، ثم سجل الدخول مرة أخرى، هذه المرة حدد حسابا مختلفا.

2. عند مطالبتك باسم مستخدم وكلمة مرور، حدد user1@testlab **.<*اسم*>** المجال وكلمة مرور User1. يجب أن تقوم بنجاح تسجيل الدخول كمستخدم1.
 
لاحظ أنه على الرغم من أن User1 لديه أذونات مسؤول المجال لمجال TESTLAB AD DS، إلا أنه ليس مسؤولا عاما. وبالتالي، لن ترى أيقونة **المسؤول** كخيار. 

يبدو التكوين الناتج كما يلي:

![المؤسسة التي تم محاكاتها مع بيئة اختبار مزامنة كلمة المرور.](../media/password-hash-sync-m365-ent-test-environment/Phase3.png)

يتكون هذا التكوين من: 
  
- Microsoft 365 E5 أو Office 365 E5 اشتراكات تجريبية أو مدفوعة باستخدام مجال DNS TESTLAB.<*اسم* مجالك> مسجل.
- إنترانت مؤسسة مبسطة متصلة بالإنترنت، تتكون من أجهزة DC1 و APP1 و CLIENT1 الظاهرية على شبكة فرعية لشبكة Azure الظاهرية. يتم تشغيل الاتصال Azure AD على APP1 لمزامنة مجال TESTLAB AD DS بشكل دوري مع مستأجر Azure AD لاشتراكك Microsoft 365.
- تم مزامنة حساب User1 في مجال TESTLAB AD DS مع مستأجر Azure AD.

## <a name="next-step"></a>الخطوة التالية

استكشف [ميزات الهوية الإضافية](m365-enterprise-test-lab-guides.md#identity) وإمكانياتها في بيئة الاختبار.

## <a name="see-also"></a>راجع أيضًا

[Microsoft 365 دليل اختبار المؤسسة](m365-enterprise-test-lab-guides.md)

[Microsoft 365 نظرة عامة حول المؤسسة](microsoft-365-overview.md)

[Microsoft 365 وثائق المؤسسة](/microsoft-365-enterprise/)