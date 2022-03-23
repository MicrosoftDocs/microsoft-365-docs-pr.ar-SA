---
title: المصادقة المرورية لبيئة Microsoft 365 الاختبار
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
- TLG
- Ent_TLGs
ms.assetid: ''
description: 'ملخص: تكوين المصادقة المرورية لبيئة Microsoft 365 الاختبار.'
ms.openlocfilehash: dcc23662683ffaf65a0ec5fa3698f729dc215af7
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 10/06/2021
ms.locfileid: "63565866"
---
# <a name="pass-through-authentication-for-your-microsoft-365-test-environment"></a>المصادقة المرورية لبيئة Microsoft 365 الاختبار

*يمكن استخدام دليل Test Lab هذا Microsoft 365 لبيئات الاختبار Office 365 Enterprise المؤسسة.*

يمكن أن تستخدم المؤسسات التي تريد استخدام البنية الأساسية لخدمات مجال Active Directory (AD DS) المحلية بشكل مباشر للمصادقة على الخدمات والتطبيقات المستندة إلى السحابة من Microsoft المصادقة المرورية. تصف هذه المقالة كيفية تكوين بيئة اختبار Microsoft 365 للمصادقة المرورية، مما يؤدي إلى التكوين التالي:
  
![المؤسسة التي تم محاكاتها مع بيئة اختبار المصادقة المرورية.](../media/pass-through-auth-m365-ent-test-environment/Phase2.png)
  
هناك مرحلتين لإعداد بيئة الاختبار هذه:

1.    قم بإنشاء Microsoft 365 اختبار المؤسسة محاكاة باستخدام مزامنة كلمة المرور.
2.    قم بتكوين Azure AD الاتصال APP1 للمصادقة المرورية.
    
![اختبار دليل المعمل لسحابة Microsoft.](../media/m365-enterprise-test-lab-guides/cloud-tlg-icon.png) 
    
> [!TIP]
> انقر [هنا](../downloads/Microsoft365EnterpriseTLGStack.pdf) للحصول على خريطة مرئية لكل المقالات في Microsoft 365 دليل اختبار المؤسسة.
  
## <a name="phase-1-configure-password-hash-synchronization-for-your-microsoft-365-test-environment"></a>المرحلة 1: تكوين مزامنة كلمة المرور لبيئة Microsoft 365 الاختبار

اتبع الإرشادات الواردة [في مزامنة كلمة المرور لمزامنة Microsoft 365](password-hash-sync-m365-ent-test-environment.md). إليك التكوين الناتج.
  
![المؤسسة التي تم محاكاتها مع بيئة اختبار مزامنة كلمة المرور.](../media/pass-through-auth-m365-ent-test-environment/Phase1.png)
  
يتكون هذا التكوين من: 
  
- Microsoft 365 E5 الاشتراك التجريبي أو المدفوع.
- إنترانت مؤسسة مبسطة متصلة بالإنترنت، تتكون من أجهزة DC1 و APP1 و CLIENT1 الظاهرية على شبكة فرعية لشبكة Azure الظاهرية. يتم تشغيل الاتصال Azure AD على APP1 لمزامنة مجال TESTLAB AD DS مع مستأجر Azure AD لاشتراكك Microsoft 365 بشكل دوري.

## <a name="phase-2-configure-azure-ad-connect-on-app1-for-pass-through-authentication"></a>المرحلة 2: تكوين Azure AD الاتصال APP1 للمصادقة المرورية

في هذه المرحلة، تقوم بتكوين Azure AD الاتصال APP1 لاستخدام المصادقة المرورية، ثم تحقق من عملها.

### <a name="configure-azure-ad-connect-on-app1"></a>تكوين Azure AD الاتصال APP1

1.    من مدخل [Azure،](https://portal.azure.com) سجل الدخول باستخدام حساب المسؤول العام، ثم اتصل ب APP1 باستخدام حساب TESTLAB\User1.

2.    من سطح المكتب ل APP1، يمكنك تشغيل Azure AD الاتصال.

3.    في صفحة **الترحيب،** انقر فوق **تكوين**.

4.    في صفحة المهام الإضافية، انقر فوق **تغيير تسجيل الدخول إلى** المستخدم، ثم انقر فوق **التالي**.

5.    على الصفحة **الاتصال Azure AD**، اكتب بيانات اعتماد حساب المسؤول العام، ثم انقر فوق **التالي**.

6.    في صفحة **تسجيل الدخول إلى** المستخدم، **انقر فوق مصادقة** المرور، ثم انقر فوق **التالي**.

7.    في الصفحة **جاهز للتكوين** ، انقر فوق **تكوين**.

8.    في الصفحة **اكتمال التكوين** ، انقر فوق **إنهاء**.

9.    من مدخل Azure، في الجزء الأيسر، انقر فوق **Azure Active Directory > Azure AD الاتصال**. تحقق من ظهور **ميزة المصادقة** المرورية **كممكنة**.

10.    انقر **فوق مصادقة تمريرية**. **يسرد جزء** المصادقة المرورية الخوادم التي تم تثبيت "وكلاء المصادقة" عليها. من المفترض أن ترى APP1 في القائمة. أغلق **جزء المصادقة المرورية** .

بعد ذلك، اختبر إمكانية تسجيل الدخول إلى اشتراكك باستخدام user1@testlab <strong>.</strong>\<your public domain> اسم المستخدم لحساب User1.

1. من APP1، سجل الخروج، ثم سجل الدخول مرة أخرى، هذه المرة حدد حسابا مختلفا.

2. عند مطالبتك باسم مستخدم وكلمة مرور، حدد user1@testlab <strong>.</strong>\<your public domain> وكلمة مرور User1. يجب أن تقوم بنجاح تسجيل الدخول كمستخدم1.

لاحظ أنه على الرغم من أن User1 لديه أذونات مسؤول المجال لمجال TESTLAB AD DS، إلا أنه ليس مسؤولا عاما. وبالتالي، لن ترى أيقونة **المسؤول** كخيار.

فيما يلي التكوين الناتج:

![المؤسسة التي تم محاكاتها مع بيئة اختبار المصادقة المرورية.](../media/pass-through-auth-m365-ent-test-environment/Phase2.png)
 
يتكون هذا التكوين من:

- يتم Microsoft 365 E5 اشتراكات تجريبية أو مدفوعة باستخدام اختبار مجال DNS.\<your domain name> مسجل.
- إنترانت مؤسسة مبسطة متصلة بالإنترنت، تتكون من أجهزة DC1 و APP1 و CLIENT1 الظاهرية على شبكة فرعية لشبكة Azure الظاهرية. يتم تشغيل عامل المصادقة على APP1 لمعالجة طلبات المصادقة المرورية من مستأجر Azure AD لاشتراكك Microsoft 365.

## <a name="next-step"></a>الخطوة التالية

استكشف [ميزات الهوية الإضافية](m365-enterprise-test-lab-guides.md#identity) وإمكانياتها في بيئة الاختبار.

## <a name="see-also"></a>راجع أيضًا

[Microsoft 365 دليل اختبار المؤسسة](m365-enterprise-test-lab-guides.md)

[Microsoft 365 نظرة عامة حول المؤسسة](microsoft-365-overview.md)

[Microsoft 365 وثائق المؤسسة](/microsoft-365-enterprise/)