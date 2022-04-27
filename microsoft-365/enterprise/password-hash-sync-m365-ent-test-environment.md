---
title: مزامنة تجزئة كلمة المرور لبيئة اختبار Microsoft 365
f1.keywords:
- NOCSH
ms.author: kvice
author: kelleyvice-msft
manager: scotv
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
description: 'ملخص: تكوين وشرح مزامنة تجزئة كلمة المرور وتسجيل الدخول لبيئة اختبار Microsoft 365.'
ms.openlocfilehash: 91d4de08382149b5089f0c06295e77965ea022cf
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/27/2022
ms.locfileid: "65093800"
---
# <a name="password-hash-synchronization-for-your-microsoft-365-test-environment"></a>مزامنة تجزئة كلمة المرور لبيئة اختبار Microsoft 365

*يمكن استخدام دليل مختبر الاختبار هذا لكل من Microsoft 365 لبيئات اختبار المؤسسة Office 365 Enterprise.*

تستخدم العديد من المؤسسات الاتصال Azure AD ومزامنة تجزئة كلمة المرور لمزامنة مجموعة الحسابات في مجموعة خدمات المجال Active Directory محلي (AD DS) إلى مجموعة الحسابات في مستأجر Azure AD لاشتراكها Microsoft 365. 

تصف هذه المقالة كيف يمكنك إضافة مزامنة تجزئة كلمة المرور إلى بيئة الاختبار Microsoft 365، ما يؤدي إلى هذا التكوين:
  
![المؤسسة المحاكاة مع بيئة اختبار مزامنة تجزئة كلمة المرور.](../media/password-hash-sync-m365-ent-test-environment/Phase3.png)
  
يتضمن إعداد بيئة الاختبار هذه ثلاث مراحل:
- [المرحلة 1: إنشاء بيئة اختبار المؤسسة المحاكاة Microsoft 365](#phase-1-create-the-microsoft-365-simulated-enterprise-test-environment)
- [المرحلة الثانية: إنشاء مجال testlab وتسجيله](#phase-2-create-and-register-the-testlab-domain)
- [المرحلة 3: تثبيت الاتصال Azure AD على APP1](#phase-3-install-azure-ad-connect-on-app1)
    
> [!TIP]
> للحصول على خريطة مرئية لجميع المقالات في Microsoft 365 لمكدس دليل مختبر اختبار المؤسسة، انتقل إلى [Microsoft 365 لمكدس دليل مختبر اختبار المؤسسة](../downloads/Microsoft365EnterpriseTLGStack.pdf).
  
## <a name="phase-1-create-the-microsoft-365-simulated-enterprise-test-environment"></a>المرحلة 1: إنشاء بيئة اختبار المؤسسة المحاكاة Microsoft 365

اتبع الإرشادات في [تكوين قاعدة المؤسسة المحاكاة Microsoft 365](simulated-ent-base-configuration-microsoft-365-enterprise.md). يبدو التكوين الناتج كما يلي:
  
![تكوين قاعدة المؤسسة المحاكاة.](../media/password-hash-sync-m365-ent-test-environment/Phase1.png)
  
يتكون هذا التكوين من:
  
- اشتراك تجريبي أو مدفوع Microsoft 365 E5.
- إنترانت مؤسسة مبسطة متصلة بالإنترنت، تتكون من أجهزة DC1 وAPP1 و CLIENT1 الظاهرية في شبكة Azure الظاهرية. DC1 هي وحدة تحكم بالمجال ل testlab.<*اسم مجالك العام*> مجال AD DS.

## <a name="phase-2-create-and-register-the-testlab-domain"></a>المرحلة الثانية: إنشاء مجال testlab وتسجيله

في هذه المرحلة، أضف مجال DNS عاما، ثم أضفه إلى اشتراكك.

أولا، العمل مع موفر تسجيل DNS العام لإنشاء اسم مجال DNS عام جديد يستند إلى اسم مجالك الحالي، ثم إضافته إلى اشتراكك. نوصي باستخدام **اسم testlab.<*مجالك*> العام**. على سبيل المثال، إذا كان اسم مجالك العام **<span>contoso.com</span>**، أضف اسم المجال العام: **<span>testlab.contoso.com</span>**.
  
بعد ذلك، أضف **testlab.<مجال *مجالك*> العام** إلى اشتراكك التجريبي أو المدفوع Microsoft 365 من خلال الانتقال إلى عملية تسجيل المجال. يتكون هذا من إضافة سجلات DNS إضافية إلى **testlab.<*مجالك*> العام**. لمزيد من المعلومات، راجع [إضافة مجال إلى Microsoft 365](../admin/setup/add-domain.md).

يبدو التكوين الناتج كما يلي:
  
![تسجيل اسم مجال testlab الخاص بك.](../media/password-hash-sync-m365-ent-test-environment/Phase2.png)
  
يتكون هذا التكوين من:

- > تسجيل اشتراك تجريبي أو مدفوع Microsoft 365 E5 مع اختبار مجال DNS.<*اسم مجالك العام*.
- إنترانت مؤسسة مبسطة متصلة بالإنترنت، تتكون من أجهزة DC1 وAPP1 و CLIENT1 الظاهرية على شبكة فرعية لشبكة Azure الظاهرية.

لاحظ كيف أصبح testlab.<*اسم مجالك العام*> الآن:

- معتمدة من سجلات DNS العامة.
- مسجل في اشتراكاتك Microsoft 365.
- مجال AD DS على إنترانت المحاكاة.
     
## <a name="phase-3-install-azure-ad-connect-on-app1"></a>المرحلة 3: تثبيت الاتصال Azure AD على APP1

في هذه المرحلة، قم بتثبيت أداة الاتصال Azure AD وتكوينها على APP1، ثم تحقق من أنها تعمل.
  
أولا، قم بتثبيت وتكوين الاتصال Azure AD على APP1.

1. من [مدخل Microsoft Azure](https://portal.azure.com)، سجل الدخول باستخدام حساب المسؤول العام، ثم اتصل ب APP1 باستخدام حساب TESTLABUser1\\.
    
2. من سطح المكتب APP1، افتح موجه أوامر Windows PowerShell على مستوى المسؤول، ثم قم بتشغيل هذه الأوامر لتعطيل أمان Internet Explorer المحسن:
    
   ```powershell
   Set-ItemProperty -Path "HKLM:\SOFTWARE\Microsoft\Active Setup\Installed Components\{A509B1A7-37EF-4b3f-8CFC-4F3A74704073}" -Name "IsInstalled" -Value 0
   Set-ItemProperty -Path "HKLM:\SOFTWARE\Microsoft\Active Setup\Installed Components\{A509B1A8-37EF-4b3f-8CFC-4F3A74704073}" -Name "IsInstalled" -Value 0
   Stop-Process -Name Explorer -Force
   ```

3. من شريط المهام، حدد **Internet Explorer** وانتقل إلى [https://aka.ms/aadconnect](https://aka.ms/aadconnect).
    
4. في صفحة Microsoft Azure Active Directory الاتصال، حدد **"تنزيل"**، ثم حدد **"تشغيل**".
    
5. في صفحة **"Welcome to Azure AD الاتصال**"، حدد **"أوافق**"، ثم حدد **"Continue**".
    
6. في صفحة **express الإعدادات**، حدد **"Use express settings**".
    
7. في **الاتصال إلى صفحة Azure AD**، أدخل اسم حساب المسؤول العام في **اسم المستخدم،** وأدخل كلمة المرور الخاصة به في **كلمة المرور**، ثم حدد **"التالي**".
    
8. في صفحة **الاتصال إلى AD DS**، أدخل **TESTLABUser1\\** في **اسم المستخدم،** وأدخل كلمة المرور الخاصة به في **كلمة المرور**، ثم حدد **"التالي**".
    
9. في الصفحة **"جاهز للتكوين"** ، حدد **"تثبيت**".
    
10. في صفحة **"Configuration complete** "، حدد **"Exit**".
    
11. في Internet Explorer، انتقل إلى مركز مسؤولي Microsoft 365 ([https://portal.microsoft.com](https://portal.microsoft.com)).
    
12. في جزء التنقل الأيمن، حدد **"المستخدمون > المستخدمون النشطون**".
    
    لاحظ الحساب المسمى **User1**. هذا الحساب من مجال TESTLAB AD DS وهو دليل على أن مزامنة الدليل قد عملت.
    
13. حدد حساب **User1** ، ثم حدد **التراخيص والتطبيقات**.
    
14. في **تراخيص المنتجات**، حدد موقعك (إذا لزم الأمر)، وقم بتعطيل ترخيص **Office 365 E5**، ثم قم بتمكين ترخيص **Microsoft 365 E5**. 

15. حدد **"حفظ** " في أسفل الصفحة، ثم حدد **"إغلاق**".
    
بعد ذلك، اختبر القدرة على تسجيل الدخول إلى اشتراكك باستخدام **user1@testlab.<اسم مستخدم *اسم*> المجال** لحساب User1:

1. من APP1، سجل الخروج، ثم سجل الدخول مرة أخرى، هذه المرة مع تحديد حساب مختلف.

2. عند مطالبتك باسم مستخدم وكلمة مرور، حدد **user1@testlab.<*اسم*> مجالك** وكلمة مرور User1. يجب تسجيل الدخول بنجاح كمستخدم1.
 
لاحظ أنه على الرغم من أن User1 لديه أذونات مسؤول المجال لمجال TESTLAB AD DS، إلا أنه ليس مسؤولا عاما. لذلك، لن ترى أيقونة **المسؤول** كخيار. 

يبدو التكوين الناتج كما يلي:

![المؤسسة المحاكاة مع بيئة اختبار مزامنة تجزئة كلمة المرور.](../media/password-hash-sync-m365-ent-test-environment/Phase3.png)

يتكون هذا التكوين من: 
  
- Microsoft 365 E5 أو Office 365 E5 الاشتراكات التجريبية أو المدفوعة مع مجال DNS TESTLAB.<*> تسجيل اسم مجالك*.
- إنترانت مؤسسة مبسطة متصلة بالإنترنت، تتكون من أجهزة DC1 وAPP1 و CLIENT1 الظاهرية على شبكة فرعية لشبكة Azure الظاهرية. يتم تشغيل الاتصال Azure AD على APP1 لمزامنة مجال TESTLAB AD DS بشكل دوري مع مستأجر Azure AD لاشتراكك في Microsoft 365.
- تمت مزامنة حساب User1 في مجال TESTLAB AD DS مع مستأجر Azure AD.

## <a name="next-step"></a>الخطوة التالية

استكشف ميزات [وإمكانات الهوية](m365-enterprise-test-lab-guides.md#identity) الإضافية في بيئة الاختبار الخاصة بك.

## <a name="see-also"></a>راجع أيضًا

[Microsoft 365 لدلائل مختبر اختبار المؤسسة](m365-enterprise-test-lab-guides.md)

[نظرة عامة حول Microsoft 365 للمؤسسات](microsoft-365-overview.md)

[موارد ووثائق Microsoft 365 للمؤسسات](/microsoft-365-enterprise/)