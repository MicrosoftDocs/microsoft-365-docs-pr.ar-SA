---
title: المتطلبات الأساسية للوصول إلى الهوية والجهاز للسحابة فقط في بيئة اختبار Microsoft 365 الخاصة بك
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
description: أنشئ Microsoft 365 اختبار الهوية والوصول إلى الجهاز مع المتطلبات الأساسية للمصادقة السحابية فقط.
ms.openlocfilehash: a0d9a50552b981f8595f661330a7c200e1d54f8a
ms.sourcegitcommit: 6c57f1e90339d5a95c9e7875599dac9d3e032c3a
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 02/04/2022
ms.locfileid: "63568527"
---
# <a name="identity-and-device-access-prerequisites-for-cloud-only-in-your-microsoft-365-test-environment"></a>المتطلبات الأساسية للوصول إلى الهوية والجهاز للسحابة فقط في بيئة اختبار Microsoft 365 الخاصة بك

*يمكن استخدام دليل Test Lab هذا فقط Microsoft 365 لبيئات اختبار المؤسسة.*

[تكوينات](../security/office-365-security/microsoft-365-policies-configurations.md) الوصول إلى الأجهزة والهوية هي مجموعة من التكوينات الموصى بها ونهج الوصول الشرطي لحماية الوصول إلى جميع الخدمات المتكاملة مع Azure Active Directory (Azure AD).

تصف هذه المقالة كيفية تكوين بيئة اختبار Microsoft 365 تلبي متطلبات تكوين المتطلبات الأساسية للسحابة فقط للوصول إلى الهوية والجهاز.[](../security/office-365-security/identity-access-prerequisites.md#prerequisites)

هناك ثماني مراحل لإعداد بيئة الاختبار هذه:

1. إنشاء بيئة الاختبار الخفيفة
2. تكوين المواقع المسماة
3. تكوين إعادة تعيين كلمة مرور الخدمة الذاتية
4. تكوين المصادقة متعددة العوامل
5. تمكين التسجيل التلقائي للجهاز لأجهزة الكمبيوتر Windows المجال
6. تكوين حماية كلمة مرور Azure AD 
7. تمكين حماية هوية Azure AD
8. تمكين المصادقة الحديثة Exchange Online Skype for Business Online

## <a name="phase-1-build-out-your-lightweight-microsoft-365-test-environment"></a>المرحلة 1: إنشاء بيئة اختبار Microsoft 365 خفيفة

اتبع الإرشادات في [تكوين الأساس الخفيف](lightweight-base-configuration-microsoft-365-enterprise.md).
إليك التكوين الناتج.

![بيئة اختبار Microsoft 3656 Enterprise الخفيفة.](../media/lightweight-base-configuration-microsoft-365-enterprise/Phase4.png)
 
## <a name="phase-2-configure-named-locations"></a>المرحلة 2: تكوين المواقع المسماة

أولا، حدد عناوين IP العامة أو نطاقات العناوين التي تستخدمها مؤسستك.

بعد ذلك، اتبع الإرشادات الواردة في تكوين المواقع المسماة في [Azure Active Directory](/azure/active-directory/reports-monitoring/quickstart-configure-named-locations) لإضافة العناوين أو نطاقات العناوين كمواد مسماة. 

## <a name="phase-3-configure-self-service-password-reset"></a>المرحلة 3: تكوين إعادة تعيين كلمة مرور الخدمة الذاتية

اتبع الإرشادات الواردة [في المرحلة 3 من "دليل اختبار الاختبار" لإعادة تعيين كلمة المرور](password-reset-m365-ent-test-environment.md#phase-3-configure-and-test-password-reset). 

عند تمكين إعادة تعيين كلمة المرور للحسابات في مجموعة Azure AD معينة، أضف هذه الحسابات إلى المجموعة **إعادة تعيين** كلمة المرور:

- المستخدم 2
- المستخدم 3
- المستخدم 4
- المستخدم 5

اختبر إعادة تعيين كلمة المرور لحساب المستخدم 2 فقط.

## <a name="phase-4-configure-multi-factor-authentication"></a>المرحلة 4: تكوين مصادقة متعددة العوامل

اتبع الإرشادات الواردة [في المرحلة 2 من دليل](multi-factor-authentication-microsoft-365-test-environment.md#phase-2-enable-and-test-multi-factor-authentication-for-the-user-2-account) اختبار اختبار المصادقة متعددة العوامل لحسابات المستخدمين التالية:

- المستخدم 2
- المستخدم 3
- المستخدم 4
- المستخدم 5

اختبر المصادقة متعددة العوامل لحساب المستخدم 2 فقط.

## <a name="phase-5-enable-automatic-device-registration-of-domain-joined-windows-computers"></a>المرحلة 5: تمكين تسجيل الجهاز تلقائيا لأجهزة الكمبيوتر Windows المجال 

اتبع [هذه الإرشادات](/azure/active-directory/devices/hybrid-azuread-join-plan) لتمكين تسجيل الجهاز تلقائيا لأجهزة الكمبيوتر Windows المجال.

## <a name="phase-6-configure-azure-ad-password-protection"></a>المرحلة 6: تكوين حماية كلمة مرور Azure AD 

اتبع [هذه الإرشادات](/azure/active-directory/authentication/concept-password-ban-bad) لحظر كلمات المرور الضعيفة المعروفة والمتغيرات الخاصة بها.

## <a name="phase-7-enable-azure-ad-identity-protection"></a>المرحلة 7: تمكين حماية هوية Azure AD

اتبع الإرشادات الواردة [في المرحلة الثانية من دليل اختبار حماية هوية Azure AD](azure-ad-identity-protection-microsoft-365-test-environment.md#phase-2-use-azure-ad-identity-protection). 

## <a name="phase-8-enable-modern-authentication-for-exchange-online-and-skype-for-business-online"></a>المرحلة 8: تمكين المصادقة الحديثة Exchange Online Skype for Business Online

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

النتيجة هي بيئة اختبار تلبي متطلبات تكوين المتطلبات الأساسية للسحابة فقط [](../security/office-365-security/identity-access-prerequisites.md#prerequisites) للوصول إلى الهوية والجهاز. 

## <a name="next-step"></a>الخطوة التالية

استخدم [سياسات الوصول](../security/office-365-security/identity-access-policies.md) إلى الأجهزة والهوية الشائعة لتكوين النهج التي تقوم ببنية المتطلبات الأساسية وحماية الهويات والأجهزة.

## <a name="see-also"></a>راجع أيضًا

[دليل اختبار الهوية الإضافية](m365-enterprise-test-lab-guides.md#identity)

[نشر الهوية](deploy-identity-solution-overview.md)

[Microsoft 365 دليل اختبار المؤسسة](m365-enterprise-test-lab-guides.md)

[Microsoft 365 نظرة عامة حول المؤسسة](microsoft-365-overview.md)

[Microsoft 365 وثائق المؤسسة](/microsoft-365-enterprise/)
