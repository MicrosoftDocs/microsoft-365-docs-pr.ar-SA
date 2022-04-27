---
title: مصادقة المرور لبيئة اختبار Microsoft 365
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
- TLG
- Ent_TLGs
ms.assetid: ''
description: 'ملخص: تكوين مصادقة المرور لبيئة اختبار Microsoft 365.'
ms.openlocfilehash: f6ad952ebde8556bd3c0c9b7e4e66c006b1c7578
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/27/2022
ms.locfileid: "65094361"
---
# <a name="pass-through-authentication-for-your-microsoft-365-test-environment"></a>مصادقة المرور لبيئة اختبار Microsoft 365

*يمكن استخدام دليل مختبر الاختبار هذا لكل من Microsoft 365 لبيئات اختبار المؤسسة Office 365 Enterprise.*

يمكن للمؤسسات التي تريد استخدام البنية الأساسية لخدمات المجال Active Directory محلي (AD DS) الخاصة بها مباشرة للمصادقة على الخدمات والتطبيقات المستندة إلى السحابة من Microsoft استخدام المصادقة التمريرية. تصف هذه المقالة كيف يمكنك تكوين بيئة اختبار Microsoft 365 للمصادقة التمريرية، ما يؤدي إلى التكوين التالي:
  
![المؤسسة المحاكاة مع بيئة اختبار المصادقة التمريرية.](../media/pass-through-auth-m365-ent-test-environment/Phase2.png)
  
هناك مرحلتان لإعداد بيئة الاختبار هذه:

1.    إنشاء بيئة اختبار المؤسسة المحاكاة Microsoft 365 مع مزامنة تجزئة كلمة المرور.
2.    تكوين الاتصال Azure AD على APP1 للمصادقة التمريرية.
    
![اختبار دلائل المختبر لسحابة Microsoft.](../media/m365-enterprise-test-lab-guides/cloud-tlg-icon.png) 
    
> [!TIP]
> انقر [هنا](../downloads/Microsoft365EnterpriseTLGStack.pdf) للحصول على خريطة مرئية لجميع المقالات في Microsoft 365 لمكدس دليل مختبر اختبار المؤسسة.
  
## <a name="phase-1-configure-password-hash-synchronization-for-your-microsoft-365-test-environment"></a>المرحلة 1: تكوين مزامنة تجزئة كلمة المرور لبيئة اختبار Microsoft 365

اتبع الإرشادات في [مزامنة تجزئة كلمة المرور Microsoft 365](password-hash-sync-m365-ent-test-environment.md). إليك التكوين الناتج.
  
![المؤسسة المحاكاة مع بيئة اختبار مزامنة تجزئة كلمة المرور.](../media/pass-through-auth-m365-ent-test-environment/Phase1.png)
  
يتكون هذا التكوين من: 
  
- Microsoft 365 E5 الاشتراك التجريبي أو المدفوع.
- إنترانت مؤسسة مبسطة متصلة بالإنترنت، تتكون من أجهزة DC1 وAPP1 و CLIENT1 الظاهرية على شبكة فرعية لشبكة Azure الظاهرية. يتم تشغيل الاتصال Azure AD على APP1 لمزامنة مجال TESTLAB AD DS مع مستأجر Azure AD لاشتراكك في Microsoft 365 بشكل دوري.

## <a name="phase-2-configure-azure-ad-connect-on-app1-for-pass-through-authentication"></a>المرحلة 2: تكوين الاتصال Azure AD على APP1 للمصادقة التمريرية

في هذه المرحلة، يمكنك تكوين الاتصال Azure AD على APP1 لاستخدام المصادقة التمريرية، ثم التحقق من أنها تعمل.

### <a name="configure-azure-ad-connect-on-app1"></a>تكوين الاتصال Azure AD على APP1

1.    من [مدخل Microsoft Azure](https://portal.azure.com)، سجل الدخول باستخدام حساب المسؤول العام، ثم اتصل ب APP1 باستخدام حساب TESTLAB\User1.

2.    من سطح المكتب APP1، قم بتشغيل الاتصال Azure AD.

3.    في **صفحة الترحيب**، انقر فوق **"تكوين**".

4.    في صفحة المهام الإضافية، انقر فوق **"تغيير تسجيل دخول المستخدم**"، ثم انقر فوق **"التالي**".

5.    في **الاتصال إلى صفحة Azure AD**، اكتب بيانات اعتماد حساب المسؤول العام، ثم انقر فوق **"التالي**".

6.    في صفحة **تسجيل دخول المستخدم** ، انقر فوق **مصادقة المرور**، ثم انقر فوق **"التالي**".

7.    في الصفحة **"جاهز للتكوين"** ، انقر فوق **"تكوين**".

8.    في صفحة **"التكوين" الكاملة** ، انقر فوق **"إنهاء**".

9.    من مدخل Azure، في الجزء الأيمن، انقر فوق **Azure Active Directory > Azure AD الاتصال**. تحقق من ظهور ميزة **المصادقة التمريرية** على أنها **ممكنة**.

10.    انقر فوق **مصادقة المرور**. يسرد جزء **المصادقة التمريرية** الخوادم التي تم تثبيت "وكلاء المصادقة" فيها. يجب أن تشاهد APP1 في القائمة. أغلق جزء **المصادقة التمريرية** .

بعد ذلك، اختبر القدرة على تسجيل الدخول إلى اشتراكك باستخدام <strong>user1@testlab.</strong>\<your public domain> اسم المستخدم لحساب User1.

1. من APP1، سجل الخروج، ثم سجل الدخول مرة أخرى، هذه المرة مع تحديد حساب مختلف.

2. عند مطالبتك باسم مستخدم وكلمة مرور، حدد <strong>user1@testlab.</strong>\<your public domain> وكلمة مرور User1. يجب تسجيل الدخول بنجاح كمستخدم1.

لاحظ أنه على الرغم من أن User1 لديه أذونات مسؤول المجال لمجال TESTLAB AD DS، إلا أنه ليس مسؤولا عاما. لذلك، لن ترى أيقونة **المسؤول** كخيار.

إليك التكوين الناتج:

![المؤسسة المحاكاة مع بيئة اختبار المصادقة التمريرية.](../media/pass-through-auth-m365-ent-test-environment/Phase2.png)
 
يتكون هذا التكوين من:

- اشتراكات تجريبية أو مدفوعة Microsoft 365 E5 مع اختبار مجال DNS.\<your domain name> المسجله.
- إنترانت مؤسسة مبسطة متصلة بالإنترنت، تتكون من أجهزة DC1 وAPP1 و CLIENT1 الظاهرية على شبكة فرعية لشبكة Azure الظاهرية. يعمل عامل المصادقة على APP1 لمعالجة طلبات المصادقة التمريرية من مستأجر Azure AD لاشتراكك في Microsoft 365.

## <a name="next-step"></a>الخطوة التالية

استكشف ميزات [وإمكانات الهوية](m365-enterprise-test-lab-guides.md#identity) الإضافية في بيئة الاختبار الخاصة بك.

## <a name="see-also"></a>راجع أيضًا

[Microsoft 365 لدلائل مختبر اختبار المؤسسة](m365-enterprise-test-lab-guides.md)

[نظرة عامة حول Microsoft 365 للمؤسسات](microsoft-365-overview.md)

[موارد ووثائق Microsoft 365 للمؤسسات](/microsoft-365-enterprise/)