---
title: تسجيل الدخول الأحادي السلس إلى Azure AD لبيئة اختبار Microsoft 365
f1.keywords:
- NOCSH
ms.author: kvice
author: kelleyvice-msft
manager: scotv
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
description: 'ملخص: تكوين واختبار تسجيل الدخول الأحادي السلس من Azure AD لبيئة اختبار Microsoft 365.'
ms.openlocfilehash: 2d6af0600044dea59cbcdd9ee51f76c061e3dcd7
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/27/2022
ms.locfileid: "65093295"
---
# <a name="azure-ad-seamless-single-sign-on-for-your-microsoft-365-test-environment"></a>تسجيل الدخول الأحادي السلس إلى Azure AD لبيئة اختبار Microsoft 365

*يمكن استخدام دليل مختبر الاختبار هذا لكل من Microsoft 365 لبيئات اختبار المؤسسة Office 365 Enterprise.*

يسجل Azure AD Seamless Single Sign-On (تسجيل الدخول الأحادي السلس) دخول المستخدمين تلقائيا عندما يكونون على أجهزة الكمبيوتر أو الأجهزة المتصلة بشبكة المؤسسة الخاصة بهم. يوفر Azure AD Seamless SSO للمستخدمين إمكانية الوصول السهل إلى التطبيقات المستندة إلى السحابة دون الحاجة إلى أي مكونات محلية إضافية.

تصف هذه المقالة كيفية تكوين بيئة اختبار Microsoft 365 ل Azure AD Seamless SSO.

يتضمن إعداد Azure AD Seamless SSO مرحلتين:
- [المرحلة 1: تكوين مزامنة تجزئة كلمة المرور لبيئة اختبار Microsoft 365](#phase-1-configure-password-hash-synchronization-for-your-microsoft-365-test-environment)
- [المرحلة 2: تكوين الاتصال Azure AD على APP1 ل Azure AD Seamless SSO](#phase-2-configure-azure-ad-connect-on-app1-for-azure-ad-seamless-sso)
   
![اختبار دلائل المختبر لسحابة Microsoft.](../media/m365-enterprise-test-lab-guides/cloud-tlg-icon.png) 
    
> [!TIP]
> للحصول على خريطة مرئية لجميع المقالات في Microsoft 365 لمكدس دليل مختبر اختبار المؤسسة، انتقل إلى [Microsoft 365 لمكدس دليل مختبر اختبار المؤسسة](../downloads/Microsoft365EnterpriseTLGStack.pdf).
  
## <a name="phase-1-configure-password-hash-synchronization-for-your-microsoft-365-test-environment"></a>المرحلة 1: تكوين مزامنة تجزئة كلمة المرور لبيئة اختبار Microsoft 365

اتبع الإرشادات في [مزامنة تجزئة كلمة المرور Microsoft 365](password-hash-sync-m365-ent-test-environment.md). 

يبدو التكوين الناتج كما يلي:
  
![المؤسسة المحاكاة مع بيئة اختبار مزامنة تجزئة كلمة المرور.](../media/pass-through-auth-m365-ent-test-environment/Phase1.png)
  
يتكون هذا التكوين من:
  
- اشتراك تجريبي أو مدفوع Microsoft 365 E5.
- إنترانت مؤسسة مبسطة متصلة بالإنترنت، تتكون من أجهزة DC1 وAPP1 و CLIENT1 الظاهرية على شبكة فرعية لشبكة Azure الظاهرية.
- يتم تشغيل الاتصال Azure AD على APP1 لمزامنة مجال خدمات مجال ACTIVE DIRECTORY TESTLAB (AD DS) بشكل دوري مع مستأجر Azure AD لاشتراكك في Microsoft 365.

## <a name="phase-2-configure-azure-ad-connect-on-app1-for-azure-ad-seamless-sso"></a>المرحلة 2: تكوين الاتصال Azure AD على APP1 ل Azure AD Seamless SSO

في هذه المرحلة، قم بتكوين الاتصال Azure AD على APP1 ل Azure AD Seamless SSO، ثم تحقق من أنه يعمل.

### <a name="configure-azure-ad-connect-on-app1"></a>تكوين الاتصال Azure AD على APP1

1. من [مدخل Microsoft Azure](https://portal.azure.com)، سجل الدخول باستخدام حساب المسؤول العام، ثم اتصل ب APP1 باستخدام حساب TESTLAB\User1.

2. من سطح المكتب APP1، قم بتشغيل الاتصال Azure AD.

3. في **صفحة الترحيب**، حدد **Configure**.

4. في صفحة **"المهام الإضافية** "، حدد **"تغيير تسجيل دخول المستخدم**"، ثم حدد **"التالي**".

5. في **الاتصال إلى صفحة Azure AD**، أدخل بيانات اعتماد حساب المسؤول العام، ثم حدد **"التالي**".

6. في صفحة **تسجيل دخول المستخدم** ، حدد **"تمكين تسجيل الدخول الأحادي**"، ثم حدد **"التالي**".

7. في صفحة **تمكين تسجيل الدخول الأحادي** ، حدد **"إدخال بيانات الاعتماد**".

8. في مربع الحوار **أمن Windows**، أدخل **user1** وكلمة المرور لحساب user1، وحدد **"موافق**"، ثم حدد **"التالي**".

9. في الصفحة **"جاهز للتكوين"**، حدد **"تكوين".**

10. في صفحة **"Configuration complete** "، حدد **"Exit**".

11. من مدخل Microsoft Azure، في الجزء الأيمن، حدد **Azure Active DirectoryAzure** >  **AD الاتصال**. تحقق من ظهور ميزة **تسجيل الدخول الأحادي السلس** على أنها **ممكنة**.

بعد ذلك، اختبر القدرة على تسجيل الدخول إلى اشتراكك باستخدام <strong>user1@testlab.</strong>\<*your public domain*> اسم المستخدم لحساب User1.

1. من Internet Explorer على APP1، حدد أيقونة الإعدادات، ثم حدد **خيارات الإنترنت**.
 
2. في **خيارات الإنترنت**، حدد علامة التبويب **"أمان** ".

3. حدد **الإنترانت المحلي**، ثم حدد **المواقع**.

4. في **الإنترانت المحلي**، حدد **Advanced**.

5. **في إضافة موقع ويب هذا إلى المنطقة**، أدخل **https <span>://</span>autologon.microsoftazuread-sso.com**، وحدد **AddCloseOKOK** >  >  > .

6. قم بتسجيل الخروج، ثم سجل الدخول مرة أخرى، هذه المرة مع تحديد حساب مختلف.

7. عند مطالبتك بتسجيل الدخول، حدد <strong>user1@testlab.</strong>\<*your public domain*> ثم حدد **"التالي**". يجب تسجيل الدخول بنجاح كمستخدم1 دون مطالبتك بكلمة مرور. وهذا يثبت أن Azure AD Seamless SSO يعمل.

لاحظ أنه على الرغم من أن User1 لديه أذونات مسؤول المجال لمجال TESTLAB AD DS، فإنه ليس مسؤولا عاما ل Azure AD. لذلك، لن ترى أيقونة **المسؤول** كخيار.

إليك التكوين الناتج:

![المؤسسة المحاكاة مع بيئة اختبار المصادقة التمريرية.](../media/pass-through-auth-m365-ent-test-environment/Phase1.png)

يتكون هذا التكوين من:

- اشتراكات تجريبية أو مدفوعة Microsoft 365 E5 مع اختبار مجال DNS.\<*your domain name*> المسجله.
- إنترانت مؤسسة مبسطة متصلة بالإنترنت، تتكون من أجهزة DC1 وAPP1 و CLIENT1 الظاهرية على شبكة فرعية لشبكة Azure الظاهرية.
- يتم تشغيل الاتصال Azure AD على APP1 لمزامنة قائمة الحسابات والمجموعات من مستأجر Azure AD لاشتراكك Microsoft 365 إلى مجال TESTLAB AD DS.
- يتم تمكين تسجيل الدخول الأحادي السلس إلى Azure AD بحيث يمكن لأجهزة الكمبيوتر على الإنترانت المحاكاة تسجيل الدخول إلى Microsoft 365 موارد السحابة دون تحديد كلمة مرور حساب مستخدم.

## <a name="next-step"></a>الخطوة التالية

استكشف ميزات [وإمكانات الهوية](m365-enterprise-test-lab-guides.md#identity) الإضافية في بيئة الاختبار الخاصة بك.

## <a name="see-also"></a>راجع أيضًا

[Microsoft 365 لدلائل مختبر اختبار المؤسسة](m365-enterprise-test-lab-guides.md)

[نظرة عامة حول Microsoft 365 للمؤسسات](microsoft-365-overview.md)

[موارد ووثائق Microsoft 365 للمؤسسات](/microsoft-365-enterprise/)