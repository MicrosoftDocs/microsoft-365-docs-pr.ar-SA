---
title: تسجيل الدخول الفردي السلس في Azure AD لبيئة Microsoft 365 الاختبار
f1.keywords:
- NOCSH
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 11/21/2019
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.localizationpriority: medium
ms.collection:
- M365-identity-device-management
- Strat_O365_Enterprise
ms.custom:
- TLGS
- Ent_TLGs
ms.assetid: ''
description: 'ملخص: قم بتكوين تسجيل الدخول المفرد السلس إلى Azure AD واختباره لبيئة Microsoft 365 الاختبار.'
ms.openlocfilehash: 4a420da5251ecef900f2efe9573db1d51a6bd597
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 10/06/2021
ms.locfileid: "63566686"
---
# <a name="azure-ad-seamless-single-sign-on-for-your-microsoft-365-test-environment"></a>تسجيل الدخول الفردي السلس في Azure AD لبيئة Microsoft 365 الاختبار

*يمكن استخدام دليل Test Lab هذا Microsoft 365 لبيئات الاختبار Office 365 Enterprise المؤسسة.*

يقوم Azure AD Single Sign-On تسجيل الدخول إلى المستخدمين تلقائيا عند وجودهم على أجهزة الكمبيوتر الشخصية أو الأجهزة المتصلة بشبكة المؤسسة الخاصة بهم. يوفر Azure AD السلس SSO للمستخدمين إمكانية الوصول السهل إلى التطبيقات المستندة إلى السحابة دون الحاجة إلى أي مكونات إضافية في الموقع.

تصف هذه المقالة كيفية تكوين بيئة اختبار Microsoft 365 ل Azure AD السلس SSO.

يتضمن إعداد Azure AD Seamless SSO مرحلتين:
- [المرحلة 1: تكوين مزامنة كلمة المرور لبيئة Microsoft 365 الاختبار](#phase-1-configure-password-hash-synchronization-for-your-microsoft-365-test-environment)
- [المرحلة 2: تكوين Azure AD الاتصال APP1 ل Azure AD السلس SSO](#phase-2-configure-azure-ad-connect-on-app1-for-azure-ad-seamless-sso)
   
![اختبار دليل المعمل لسحابة Microsoft.](../media/m365-enterprise-test-lab-guides/cloud-tlg-icon.png) 
    
> [!TIP]
> للحصول على خريطة مرئية لكل المقالات في Microsoft 365 دليل اختبار المؤسسة، انتقل إلى Microsoft 365 [دليل اختبار المؤسسة](../downloads/Microsoft365EnterpriseTLGStack.pdf).
  
## <a name="phase-1-configure-password-hash-synchronization-for-your-microsoft-365-test-environment"></a>المرحلة 1: تكوين مزامنة كلمة المرور لبيئة Microsoft 365 الاختبار

اتبع الإرشادات الواردة [في مزامنة كلمة المرور لمزامنة Microsoft 365](password-hash-sync-m365-ent-test-environment.md). 

يبدو التكوين الناتج كما يلي:
  
![المؤسسة التي تم محاكاتها مع بيئة اختبار مزامنة كلمة المرور.](../media/pass-through-auth-m365-ent-test-environment/Phase1.png)
  
يتكون هذا التكوين من:
  
- اشتراك Microsoft 365 E5 تجريبي أو مدفوع.
- إنترانت مؤسسة مبسطة متصلة بالإنترنت، تتكون من أجهزة DC1 و APP1 و CLIENT1 الظاهرية على شبكة فرعية لشبكة Azure الظاهرية.
- يتم تشغيل azure AD الاتصال APP1 لمزامنة مجال خدمات مجال TESTLAB Active Directory (AD DS) بشكل دوري مع مستأجر Azure AD لاشتراكك في Microsoft 365.

## <a name="phase-2-configure-azure-ad-connect-on-app1-for-azure-ad-seamless-sso"></a>المرحلة 2: تكوين Azure AD الاتصال APP1 ل Azure AD السلس SSO

في هذه المرحلة، قم بتكوين Azure AD الاتصال APP1 ل Azure AD السلس SSO، ثم تحقق من أنه يعمل.

### <a name="configure-azure-ad-connect-on-app1"></a>تكوين Azure AD الاتصال APP1

1. من مدخل [Azure،](https://portal.azure.com) سجل الدخول باستخدام حساب المسؤول العام، ثم اتصل ب APP1 باستخدام حساب TESTLAB\User1.

2. من سطح المكتب APP1، يمكنك تشغيل Azure AD الاتصال.

3. في صفحة **الترحيب،** حدد **تكوين**.

4. في صفحة **المهام الإضافية** ، حدد **تغيير تسجيل الدخول** إلى المستخدم، ثم حدد **التالي**.

5. في الصفحة **الاتصال Azure AD**، أدخل بيانات اعتماد حساب المسؤول العام، ثم حدد **التالي**.

6. في صفحة **تسجيل الدخول إلى** المستخدم، حدد **تمكين تسجيل الدخول** الفردي، ثم حدد **التالي**.

7. في الصفحة **تمكين تسجيل الدخول الفردي** ، حدد **إدخال بيانات الاعتماد**.

8. في مربع **أمن Windows**، أدخل **user1** وكلمة المرور لحساب المستخدم1، وحدد **موافق**، ثم حدد **التالي**.

9. في الصفحة **جاهز للتكوين** ، حدد **تكوين**.

10. في الصفحة **اكتمال التكوين** ، حدد **إنهاء**.

11. من مدخل Azure، في الجزء الأيسر، حدد **Azure Active DirectoryAzure** >  **AD** الاتصال. تحقق من ظهور **ميزة تسجيل الدخول** المفرد السلس ك **ممكن**.

بعد ذلك، اختبر إمكانية تسجيل الدخول إلى اشتراكك باستخدام user1@testlab <strong>.</strong>\<*your public domain*> اسم المستخدم لحساب User1.

1. من Internet Explorer على APP1، حدد أيقونة الإعدادات، ثم حدد **خيارات الإنترنت**.
 
2. في **خيارات الإنترنت**، حدد **علامة التبويب الأمان** .

3. حدد **الإنترانت المحلي**، ثم حدد **المواقع**.

4. في **الإنترانت المحلي**، حدد **متقدم**.

5. في **إضافة موقع ويب هذا إلى المنطقة،** أدخل **https <span>://</span>autologon.microsoftazuread-sso.com**، وحدد **AddCloseOK** >  >  > **.**

6. سجل الخروج، ثم سجل الدخول مرة أخرى، هذه المرة مع تحديد حساب مختلف.

7. عند مطالبتك تسجيل الدخول، حدد user1@testlab <strong>.</strong>\<*your public domain*> ثم حدد **التالي**. يجب أن تقوم بنجاح تسجيل الدخول كمستخدم1 دون مطالبتك بكلمة مرور. يثبت ذلك أن Azure AD Seamless SSO يعمل.

لاحظ أنه على الرغم من أن User1 لديه أذونات مسؤول المجال لمجال TESTLAB AD DS، إلا أنه ليس مسؤولا عاما ل Azure AD. وبالتالي، لن ترى أيقونة **المسؤول** كخيار.

فيما يلي التكوين الناتج:

![المؤسسة التي تم محاكاتها مع بيئة اختبار المصادقة المرورية.](../media/pass-through-auth-m365-ent-test-environment/Phase1.png)

يتكون هذا التكوين من:

- يتم Microsoft 365 E5 اشتراكات تجريبية أو مدفوعة باستخدام اختبار مجال DNS.\<*your domain name*> مسجل.
- إنترانت مؤسسة مبسطة متصلة بالإنترنت، تتكون من أجهزة DC1 و APP1 و CLIENT1 الظاهرية على شبكة فرعية لشبكة Azure الظاهرية.
- يتم تشغيل الاتصال Azure AD على APP1 لمزامنة قائمة الحسابات والمجموعات من مستأجر Azure AD لاشتراكك في Microsoft 365 لمجال TESTLAB AD DS.
- يتم تمكين Azure AD Seamless SSO لتمكين أجهزة الكمبيوتر الموجودة على الإنترانت التي تم محاكاتها من تسجيل الدخول Microsoft 365 موارد السحابة دون تحديد كلمة مرور حساب مستخدم.

## <a name="next-step"></a>الخطوة التالية

استكشف [ميزات الهوية الإضافية](m365-enterprise-test-lab-guides.md#identity) وإمكانياتها في بيئة الاختبار.

## <a name="see-also"></a>راجع أيضًا

[Microsoft 365 دليل اختبار المؤسسة](m365-enterprise-test-lab-guides.md)

[Microsoft 365 نظرة عامة حول المؤسسة](microsoft-365-overview.md)

[Microsoft 365 وثائق المؤسسة](/microsoft-365-enterprise/)