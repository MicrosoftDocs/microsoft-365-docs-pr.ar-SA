---
title: المتطلبات الأساسية للوصول إلى الهوية والجهاز للمصادقة المرورية في Microsoft 365 الاختبار
author: kelleyvice-msft
f1.keywords:
- NOCSH
ms.author: kvice
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Strat_O365_Enterprise
ms.custom: ''
description: أنشئ Microsoft 365 اختبار الهوية والوصول إلى الجهاز مع المتطلبات الأساسية للمصادقة المرورية.
ms.openlocfilehash: 662cf1aa45c2d297600baf63bd3970f31d437f95
ms.sourcegitcommit: 6c57f1e90339d5a95c9e7875599dac9d3e032c3a
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 02/04/2022
ms.locfileid: "63566281"
---
# <a name="identity-and-device-access-prerequisites-for-pass-through-authentication-in-your-microsoft-365-test-environment"></a>المتطلبات الأساسية للوصول إلى الهوية والجهاز للمصادقة المرورية في Microsoft 365 الاختبار

*يمكن استخدام دليل Test Lab هذا فقط Microsoft 365 لبيئات اختبار المؤسسة.*

[تكوينات](../security/office-365-security/microsoft-365-policies-configurations.md) الوصول إلى الأجهزة والهوية هي مجموعة من التكوينات ونهج الوصول الشرطي لحماية الوصول إلى كل الخدمات في Microsoft 365 للمؤسسات المتكاملة مع Azure Active Directory (Azure AD).

تصف هذه المقالة كيفية تكوين بيئة اختبار Microsoft 365 تلبي متطلبات تكوين المتطلبات الأساسية للمصادقة المرورية للوصول إلى الهوية والجهاز.[](../security/office-365-security/identity-access-prerequisites.md#prerequisites)

هناك عشر مراحل لإعداد بيئة الاختبار هذه:

1. إنشاء المؤسسة التي تم محاكاتها باستخدام بيئة Microsoft 365 الاختبار
2. تكوين تسجيل الدخول الفردي السلس إلى Azure AD
3. تكوين المواقع المسماة
4. تكوين إعادة كتابة كلمة المرور
5. تكوين إعادة تعيين كلمة مرور الخدمة الذاتية
6. تكوين المصادقة متعددة العوامل
7. تمكين التسجيل التلقائي للجهاز لأجهزة الكمبيوتر Windows المجال
8. تكوين حماية كلمة مرور Azure AD 
9. تمكين حماية هوية Azure AD
10. تمكين المصادقة الحديثة Exchange Online Skype for Business Online

## <a name="phase-1-build-out-your-simulated-enterprise-with-pass-through-authentication-microsoft-365-test-environment"></a>المرحلة 1: إنشاء المؤسسة التي تم محاكاتها باستخدام مصادقة Microsoft 365 الاختبار

اتبع الإرشادات الواردة في [المصادقة المرورية](pass-through-auth-m365-ent-test-environment.md).

إليك التكوين الناتج.

![المؤسسة التي تم محاكاتها مع بيئة اختبار المصادقة المرورية.](../media/pass-through-auth-m365-ent-test-environment/Phase2.png)
 
## <a name="phase-2-configure-azure-ad-seamless-single-sign-on"></a>المرحلة 2: تكوين تسجيل الدخول المفرد السلس إلى Azure AD

اتبع الإرشادات الواردة [في المرحلة 2 من دليل اختبار تسجيل الدخول المفرد إلى Azure AD السلس](single-sign-on-m365-ent-test-environment.md#phase-2-configure-azure-ad-connect-on-app1-for-azure-ad-seamless-sso).

## <a name="phase-3-configure-named-locations"></a>المرحلة 3: تكوين المواقع المسماة

أولا، حدد عناوين IP العامة أو نطاقات العناوين التي تستخدمها مؤسستك.

بعد ذلك، اتبع الإرشادات الواردة في تكوين المواقع المسماة في [Azure Active Directory](/azure/active-directory/reports-monitoring/quickstart-configure-named-locations) لإضافة العناوين أو نطاقات العناوين كمواد مسماة. 

## <a name="phase-4-configure-password-writeback"></a>المرحلة 4: تكوين إعادة كتابة كلمة المرور

اتبع الإرشادات الواردة [في المرحلة 2 من دليل اختبار الاختبار للكتابة بكلمة مرور](password-writeback-m365-ent-test-environment.md#phase-2-enable-password-writeback-for-the-testlab-ad-ds-domain).

## <a name="phase-5-configure-self-service-password-reset"></a>المرحلة 5: تكوين إعادة تعيين كلمة مرور الخدمة الذاتية

اتبع الإرشادات الواردة [في المرحلة 3 من "دليل اختبار الاختبار" لإعادة تعيين كلمة المرور](password-reset-m365-ent-test-environment.md#phase-3-configure-and-test-password-reset). 

عند تمكين إعادة تعيين كلمة المرور للحسابات في مجموعة Azure AD معينة، أضف هذه الحسابات إلى المجموعة **إعادة تعيين** كلمة المرور:

- المستخدم 2
- المستخدم 3
- المستخدم 4
- المستخدم 5

اختبر إعادة تعيين كلمة المرور لحساب المستخدم 2 فقط.

## <a name="phase-6-configure-multi-factor-authentication"></a>المرحلة 6: تكوين مصادقة متعددة العوامل

اتبع الإرشادات الواردة [في المرحلة 2 من دليل](multi-factor-authentication-microsoft-365-test-environment.md#phase-2-enable-and-test-multi-factor-authentication-for-the-user-2-account) اختبار اختبار المصادقة متعددة العوامل لحسابات المستخدمين التالية:

- المستخدم 2
- المستخدم 3
- المستخدم 4
- المستخدم 5

اختبر المصادقة متعددة العوامل لحساب المستخدم 2 فقط.

## <a name="phase-7-enable-automatic-device-registration-of-domain-joined-windows-computers"></a>المرحلة 7: تمكين تسجيل الجهاز التلقائي لأجهزة الكمبيوتر Windows المجال 

اتبع [هذه الإرشادات](/azure/active-directory/devices/hybrid-azuread-join-plan) لتمكين تسجيل الجهاز تلقائيا لأجهزة الكمبيوتر Windows المجال.

## <a name="phase-8-configure-azure-ad-password-protection"></a>المرحلة 8: تكوين حماية كلمة مرور Azure AD 

اتبع [هذه الإرشادات](/azure/active-directory/authentication/concept-password-ban-bad) لحظر كلمات المرور الضعيفة المعروفة والمتغيرات الخاصة بها.

## <a name="phase-9-enable-azure-ad-identity-protection"></a>المرحلة 9: تمكين حماية هوية Azure AD

اتبع الإرشادات الواردة [في المرحلة الثانية من دليل اختبار حماية هوية Azure AD](azure-ad-identity-protection-microsoft-365-test-environment.md#phase-2-use-azure-ad-identity-protection). 

## <a name="phase-10-enable-modern-authentication-for-exchange-online-and-skype-for-business-online"></a>المرحلة 10: تمكين المصادقة الحديثة Exchange Online Skype for Business Online

للحصول Exchange Online، اتبع [هذه الإرشادات](/Exchange/clients-and-mobile-in-exchange-online/enable-or-disable-modern-authentication-in-exchange-online#enable-or-disable-modern-authentication-in-exchange-online-for-client-connections-in-outlook-2013-or-later). 

بالنسبة Skype for Business عبر الإنترنت:

1. الاتصال إلى [Skype for Business Online](/SkypeForBusiness/set-up-your-computer-for-windows-powershell/set-up-your-computer-for-windows-powershell).

2. تشغيل هذا الأمر.

  ```powershell
  Set-CsOAuthConfiguration -ClientAdalAuthOverride Allowed
  ```

3. تحقق من نجاح التغيير باستخدام هذا الأمر.

  ```powershell
  Get-CsOAuthConfiguration
  ```

النتيجة هي بيئة اختبار تلبي متطلبات تكوين المتطلبات الأساسية للمصادقة المرورية [للوصول إلى](../security/office-365-security/identity-access-prerequisites.md#prerequisites) الهوية والجهاز. 

## <a name="next-step"></a>الخطوة التالية

استخدم [سياسات الوصول](../security/office-365-security/identity-access-policies.md) إلى الأجهزة والهوية الشائعة لتكوين النهج التي تقوم ببنية المتطلبات الأساسية وحماية الهويات والأجهزة.

## <a name="see-also"></a>راجع أيضًا

[دليل اختبار الهوية الإضافية](m365-enterprise-test-lab-guides.md#identity)

[نشر الهوية](deploy-identity-solution-overview.md)

[Microsoft 365 دليل اختبار المؤسسة](m365-enterprise-test-lab-guides.md)

[Microsoft 365 نظرة عامة حول المؤسسة](microsoft-365-overview.md)

[Microsoft 365 وثائق المؤسسة](/microsoft-365-enterprise/)
