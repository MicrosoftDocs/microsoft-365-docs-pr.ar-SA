---
title: المتطلبات الأساسية للوصول إلى الهوية والجهاز لمزامنة تجزئة كلمة المرور في بيئة اختبار Microsoft 365
author: kelleyvice-msft
f1.keywords:
- NOCSH
ms.author: kvice
manager: scotv
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Strat_O365_Enterprise
ms.custom: ''
description: إنشاء بيئة Microsoft 365 لاختبار الهوية والوصول إلى الجهاز مع المتطلبات الأساسية لمصادقة مزامنة تجزئة كلمة المرور.
ms.openlocfilehash: af357a477ea0aa66881b546d6cefbd517e453e80
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/27/2022
ms.locfileid: "65100358"
---
# <a name="identity-and-device-access-prerequisites-for-password-hash-synchronization-in-your-microsoft-365-test-environment"></a>المتطلبات الأساسية للوصول إلى الهوية والجهاز لمزامنة تجزئة كلمة المرور في بيئة اختبار Microsoft 365

*يمكن استخدام دليل مختبر الاختبار هذا فقط Microsoft 365 لبيئات اختبار المؤسسة.*

[تكوينات الوصول إلى الهوية والجهاز](../security/office-365-security/microsoft-365-policies-configurations.md) هي مجموعة من التكوينات ونهج الوصول المشروط لحماية الوصول إلى جميع الخدمات في Microsoft 365 للمؤسسة المدمجة مع Azure Active Directory (Azure AD).

تصف هذه المقالة كيفية تكوين بيئة اختبار Microsoft 365 تفي بمتطلبات [التكوين المختلط لمصادقة مزامنة تجزئة كلمة المرور](../security/office-365-security/identity-access-prerequisites.md#prerequisites) للوصول إلى الهوية والجهاز.

هناك عشر مراحل لإعداد بيئة الاختبار هذه:

1. إنشاء مؤسسة محاكاة باستخدام بيئة اختبار مزامنة تجزئة كلمة المرور
2. تكوين تسجيل الدخول الأحادي السلس إلى Azure AD
3. تكوين المواقع المسماة
4. تكوين إعادة كتابة كلمة المرور
5. تكوين إعادة تعيين كلمة مرور الخدمة الذاتية لكافة حسابات المستخدمين
6. تكوين المصادقة متعددة العوامل لجميع حسابات المستخدمين
7. تمكين تسجيل الجهاز التلقائي لأجهزة الكمبيوتر Windows المتصلة بالمجال
8. تكوين حماية كلمة مرور Azure AD 
9. تمكين Azure AD Identity Protection
10. تمكين المصادقة الحديثة ل Exchange Online و Skype for Business Online

## <a name="phase-1-build-out-your-simulated-enterprise-with-password-hash-sync-microsoft-365-test-environment"></a>المرحلة 1: إنشاء مؤسستك المحاكاة باستخدام مزامنة تجزئة كلمة المرور Microsoft 365 بيئة الاختبار

اتبع الإرشادات الواردة في دليل اختبار اختبار [مزامنة تجزئة كلمة المرور](password-hash-sync-m365-ent-test-environment.md) .
فيما يلي التكوين الناتج.

![المؤسسة المحاكاة مع بيئة اختبار مزامنة تجزئة كلمة المرور.](../media/password-hash-sync-m365-ent-test-environment/Phase3.png)
 
## <a name="phase-2-configure-azure-ad-seamless-single-sign-on"></a>المرحلة 2: تكوين تسجيل الدخول الأحادي السلس إلى Azure AD

اتبع الإرشادات في [المرحلة 2 من دليل اختبار تسجيل الدخول الأحادي السلس إلى Azure AD](single-sign-on-m365-ent-test-environment.md#phase-2-configure-azure-ad-connect-on-app1-for-azure-ad-seamless-sso).

## <a name="phase-3-configure-named-locations"></a>المرحلة 3: تكوين المواقع المسماة

أولا، حدد عناوين IP العامة أو نطاقات العناوين المستخدمة من قبل مؤسستك.

بعد ذلك، اتبع الإرشادات في [تكوين المواقع المسماة في Azure Active Directory](/azure/active-directory/reports-monitoring/quickstart-configure-named-locations) لإضافة العناوين أو نطاقات العناوين كمواقع مسماة. 

## <a name="phase-4-configure-password-writeback"></a>المرحلة 4: تكوين إعادة كتابة كلمة المرور

اتبع الإرشادات في [المرحلة 2 من دليل اختبار اختبار إعادة كتابة كلمة المرور](password-writeback-m365-ent-test-environment.md#phase-2-enable-password-writeback-for-the-testlab-ad-ds-domain).

## <a name="phase-5-configure-self-service-password-reset"></a>المرحلة 5: تكوين إعادة تعيين كلمة مرور الخدمة الذاتية

اتبع الإرشادات في [المرحلة 3 من دليل اختبار الاختبار المعملي لإعادة تعيين كلمة المرور](password-reset-m365-ent-test-environment.md#phase-3-configure-and-test-password-reset). 

عند تمكين إعادة تعيين كلمة المرور للحسابات في مجموعة Azure AD معينة، أضف هذه الحسابات إلى مجموعة **إعادة تعيين كلمة المرور** :

- المستخدم 2
- المستخدم 3
- المستخدم 4
- المستخدم 5

اختبار إعادة تعيين كلمة المرور لحساب المستخدم 2 فقط.

## <a name="phase-6-configure-multi-factor-authentication"></a>المرحلة 6: تكوين المصادقة متعددة العوامل

اتبع الإرشادات في [المرحلة 2 من دليل مختبر اختبار المصادقة متعددة العوامل](multi-factor-authentication-microsoft-365-test-environment.md#phase-2-enable-and-test-multi-factor-authentication-for-the-user-2-account) لحسابات المستخدمين التالية:

- المستخدم 2
- المستخدم 3
- المستخدم 4
- المستخدم 5

اختبر المصادقة متعددة العوامل لحساب المستخدم 2 فقط.

## <a name="phase-7-enable-automatic-device-registration-of-domain-joined-windows-computers"></a>المرحلة 7: تمكين تسجيل الجهاز التلقائي لأجهزة الكمبيوتر Windows المنضمة إلى المجال 

اتبع [هذه الإرشادات](/azure/active-directory/devices/hybrid-azuread-join-plan) لتمكين تسجيل الجهاز التلقائي لأجهزة الكمبيوتر Windows المتصلة بالمجال.

## <a name="phase-8-configure-azure-ad-password-protection"></a>المرحلة 8: تكوين حماية كلمة مرور Azure AD 

اتبع [هذه الإرشادات](/azure/active-directory/authentication/concept-password-ban-bad) لحظر كلمات المرور الضعيفة المعروفة ومتغيراتها.

## <a name="phase-9-enable-azure-ad-identity-protection"></a>المرحلة 9: تمكين Azure AD Identity Protection

اتبع الإرشادات الواردة في [المرحلة 2 من دليل مختبر اختبار حماية هوية Azure AD](azure-ad-identity-protection-microsoft-365-test-environment.md#phase-2-use-azure-ad-identity-protection). 

## <a name="phase-10-enable-modern-authentication-for-exchange-online-and-skype-for-business-online"></a>المرحلة 10: تمكين المصادقة الحديثة ل Exchange Online و Skype for Business Online

للحصول على Exchange Online، اتبع [هذه الإرشادات](/Exchange/clients-and-mobile-in-exchange-online/enable-or-disable-modern-authentication-in-exchange-online#enable-or-disable-modern-authentication-in-exchange-online-for-client-connections-in-outlook-2013-or-later). 

بالنسبة إلى Skype for Business Online:

1. الاتصال إلى [Skype for Business Online](/SkypeForBusiness/set-up-your-computer-for-windows-powershell/set-up-your-computer-for-windows-powershell).

2. تشغيل هذا الأمر.

  ```powershell
  Set-CsOAuthConfiguration -ClientAdalAuthOverride Allowed
  ```

3. تحقق من نجاح التغيير باستخدام هذا الأمر.

  ```powershell
  Get-CsOAuthConfiguration
  ```

والنتيجة هي بيئة اختبار تفي بمتطلبات [Active Directory مع تكوين المتطلبات الأساسية لمزامنة تجزئة كلمة المرور](../security/office-365-security/identity-access-prerequisites.md#prerequisites) للوصول إلى الهوية والجهاز. 

## <a name="next-step"></a>الخطوة التالية

استخدم [نهج الوصول إلى الأجهزة والهوية الشائعة](../security/office-365-security/identity-access-policies.md) لتكوين النهج التي تعتمد على المتطلبات الأساسية وحماية الهويات والأجهزة.

## <a name="see-also"></a>راجع أيضًا

[دلائل مختبر اختبار الهوية الإضافية](m365-enterprise-test-lab-guides.md#identity)

[نشر الهوية](deploy-identity-solution-overview.md)

[Microsoft 365 لدلائل مختبر اختبار المؤسسة](m365-enterprise-test-lab-guides.md)

[نظرة عامة حول Microsoft 365 للمؤسسات](microsoft-365-overview.md)

[موارد ووثائق Microsoft 365 للمؤسسات](/microsoft-365-enterprise/)
