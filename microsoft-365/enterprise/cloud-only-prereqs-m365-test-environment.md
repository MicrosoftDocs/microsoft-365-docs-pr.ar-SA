---
title: المتطلبات الأساسية للوصول إلى الهوية والجهاز للسحابة فقط في بيئة اختبار Microsoft 365
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
description: إنشاء بيئة Microsoft 365 لاختبار الهوية والوصول إلى الجهاز مع المتطلبات الأساسية للمصادقة السحابية فقط.
ms.openlocfilehash: 88138600e516412b74c38234647147197742f2de
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/27/2022
ms.locfileid: "65097503"
---
# <a name="identity-and-device-access-prerequisites-for-cloud-only-in-your-microsoft-365-test-environment"></a>المتطلبات الأساسية للوصول إلى الهوية والجهاز للسحابة فقط في بيئة اختبار Microsoft 365

*يمكن استخدام دليل مختبر الاختبار هذا فقط Microsoft 365 لبيئات اختبار المؤسسة.*

[تكوينات الوصول إلى الهوية والجهاز](../security/office-365-security/microsoft-365-policies-configurations.md) هي مجموعة من التكوينات الموصى بها ونهج الوصول المشروط لحماية الوصول إلى جميع الخدمات المدمجة مع Azure Active Directory (Azure AD).

تصف هذه المقالة كيفية تكوين بيئة اختبار Microsoft 365 تفي بمتطلبات [تكوين المتطلبات الأساسية للسحابة فقط](../security/office-365-security/identity-access-prerequisites.md#prerequisites) للوصول إلى الهوية والجهاز.

هناك ثماني مراحل لإعداد بيئة الاختبار هذه:

1. إنشاء بيئة اختبار خفيفة الوزن
2. تكوين المواقع المسماة
3. تكوين إعادة تعيين كلمة مرور الخدمة الذاتية
4. تكوين المصادقة متعددة العوامل
5. تمكين تسجيل الجهاز التلقائي لأجهزة الكمبيوتر Windows المتصلة بالمجال
6. تكوين حماية كلمة مرور Azure AD 
7. تمكين Azure AD Identity Protection
8. تمكين المصادقة الحديثة ل Exchange Online و Skype for Business Online

## <a name="phase-1-build-out-your-lightweight-microsoft-365-test-environment"></a>المرحلة 1: إنشاء بيئة اختبار Microsoft 365 خفيفة الوزن

اتبع الإرشادات في [تكوين قاعدة خفيفة الوزن](lightweight-base-configuration-microsoft-365-enterprise.md).
فيما يلي التكوين الناتج.

![بيئة اختبار Microsoft 3656 Enterprise خفيفة الوزن.](../media/lightweight-base-configuration-microsoft-365-enterprise/Phase4.png)
 
## <a name="phase-2-configure-named-locations"></a>المرحلة 2: تكوين المواقع المسماة

أولا، حدد عناوين IP العامة أو نطاقات العناوين المستخدمة من قبل مؤسستك.

بعد ذلك، اتبع الإرشادات في [تكوين المواقع المسماة في Azure Active Directory](/azure/active-directory/reports-monitoring/quickstart-configure-named-locations) لإضافة العناوين أو نطاقات العناوين كمواقع مسماة. 

## <a name="phase-3-configure-self-service-password-reset"></a>المرحلة 3: تكوين إعادة تعيين كلمة مرور الخدمة الذاتية

اتبع الإرشادات في [المرحلة 3 من دليل اختبار الاختبار المعملي لإعادة تعيين كلمة المرور](password-reset-m365-ent-test-environment.md#phase-3-configure-and-test-password-reset). 

عند تمكين إعادة تعيين كلمة المرور للحسابات في مجموعة Azure AD معينة، أضف هذه الحسابات إلى مجموعة **إعادة تعيين كلمة المرور** :

- المستخدم 2
- المستخدم 3
- المستخدم 4
- المستخدم 5

اختبار إعادة تعيين كلمة المرور لحساب المستخدم 2 فقط.

## <a name="phase-4-configure-multi-factor-authentication"></a>المرحلة 4: تكوين المصادقة متعددة العوامل

اتبع الإرشادات في [المرحلة 2 من دليل مختبر اختبار المصادقة متعددة العوامل](multi-factor-authentication-microsoft-365-test-environment.md#phase-2-enable-and-test-multi-factor-authentication-for-the-user-2-account) لحسابات المستخدمين التالية:

- المستخدم 2
- المستخدم 3
- المستخدم 4
- المستخدم 5

اختبر المصادقة متعددة العوامل لحساب المستخدم 2 فقط.

## <a name="phase-5-enable-automatic-device-registration-of-domain-joined-windows-computers"></a>المرحلة 5: تمكين تسجيل الجهاز التلقائي لأجهزة الكمبيوتر Windows المنضمة إلى المجال 

اتبع [هذه الإرشادات](/azure/active-directory/devices/hybrid-azuread-join-plan) لتمكين تسجيل الجهاز التلقائي لأجهزة الكمبيوتر Windows المتصلة بالمجال.

## <a name="phase-6-configure-azure-ad-password-protection"></a>المرحلة 6: تكوين حماية كلمة مرور Azure AD 

اتبع [هذه الإرشادات](/azure/active-directory/authentication/concept-password-ban-bad) لحظر كلمات المرور الضعيفة المعروفة ومتغيراتها.

## <a name="phase-7-enable-azure-ad-identity-protection"></a>المرحلة 7: تمكين Azure AD Identity Protection

اتبع الإرشادات الواردة في [المرحلة 2 من دليل مختبر اختبار حماية هوية Azure AD](azure-ad-identity-protection-microsoft-365-test-environment.md#phase-2-use-azure-ad-identity-protection). 

## <a name="phase-8-enable-modern-authentication-for-exchange-online-and-skype-for-business-online"></a>المرحلة 8: تمكين المصادقة الحديثة ل Exchange Online و Skype for Business Online

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

والنتيجة هي بيئة اختبار تلبي متطلبات [تكوين المتطلبات الأساسية للسحابة فقط](../security/office-365-security/identity-access-prerequisites.md#prerequisites) للوصول إلى الهوية والجهاز. 

## <a name="next-step"></a>الخطوة التالية

استخدم [نهج الوصول إلى الأجهزة والهوية الشائعة](../security/office-365-security/identity-access-policies.md) لتكوين النهج التي تعتمد على المتطلبات الأساسية وحماية الهويات والأجهزة.

## <a name="see-also"></a>راجع أيضًا

[دلائل مختبر اختبار الهوية الإضافية](m365-enterprise-test-lab-guides.md#identity)

[نشر الهوية](deploy-identity-solution-overview.md)

[Microsoft 365 لدلائل مختبر اختبار المؤسسة](m365-enterprise-test-lab-guides.md)

[نظرة عامة حول Microsoft 365 للمؤسسات](microsoft-365-overview.md)

[موارد ووثائق Microsoft 365 للمؤسسات](/microsoft-365-enterprise/)
