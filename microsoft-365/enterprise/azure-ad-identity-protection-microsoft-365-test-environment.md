---
title: حماية هوية Azure AD Microsoft 365 لبيئة اختبار المؤسسة
f1.keywords:
- NOCSH
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 12/10/2019
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.localizationpriority: medium
ms.collection: M365-identity-device-management
ms.custom:
- TLG
- Ent_TLGs
description: تكوين Azure AD Identity Protection وتحليل الحسابات الحالية في Microsoft 365 لبيئة اختبار المؤسسة.
ms.openlocfilehash: 1f947f9b74b1909aa1e6451ec835a2ad78964f75
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/27/2022
ms.locfileid: "65078746"
---
# <a name="azure-ad-identity-protection-for-your-microsoft-365-for-enterprise-test-environment"></a>حماية هوية Azure AD Microsoft 365 لبيئة اختبار المؤسسة

*يمكن استخدام دليل مختبر الاختبار هذا فقط Microsoft 365 لبيئات اختبار المؤسسة.*

يمكنك استخدام Azure Active Directory (Azure AD) Identity Protection للكشف عن الثغرات الأمنية المحتملة التي تؤثر على هويات مؤسستك، وتكوين الاستجابات التلقائية، والتحقيق في الحوادث. تصف هذه المقالة كيفية استخدام Azure AD Identity Protection لعرض تحليل حسابات بيئة الاختبار الخاصة بك.

يتضمن إعداد Azure AD Identity Protection في Microsoft 365 لبيئة اختبار المؤسسة مرحلتين:

- [المرحلة 1: إنشاء Microsoft 365 لبيئة اختبار المؤسسة](#phase-1-build-out-your-microsoft-365-for-enterprise-test-environment)
- [المرحلة الثانية: استخدام Azure AD Identity Protection](#phase-2-use-azure-ad-identity-protection)

![اختبار دلائل المختبر لسحابة Microsoft.](../media/m365-enterprise-test-lab-guides/cloud-tlg-icon.png) 
    
> [!TIP]
> للحصول على خريطة مرئية لجميع المقالات في Microsoft 365 لمكدس دليل مختبر اختبار المؤسسة، انتقل إلى [Microsoft 365 لمكدس دليل مختبر اختبار المؤسسة](../downloads/Microsoft365EnterpriseTLGStack.pdf).
  
## <a name="phase-1-build-out-your-microsoft-365-for-enterprise-test-environment"></a>المرحلة 1: إنشاء Microsoft 365 لبيئة اختبار المؤسسة

إذا كنت تريد اختبار Azure AD Identity Protection فقط بطريقة خفيفة مع الحد الأدنى من المتطلبات، فاتبع الإرشادات في [تكوين قاعدة خفيفة الوزن](lightweight-base-configuration-microsoft-365-enterprise.md).
  
إذا كنت ترغب في اختبار Azure AD Identity Protection في مؤسسة محاكاة، فاتبع الإرشادات في [مصادقة المرور](pass-through-auth-m365-ent-test-environment.md).
  
> [!NOTE]
> لا يتطلب اختبار Azure AD Identity Protection بيئة اختبار المؤسسة المحاكاة، والتي تتضمن إنترانت محاكاة متصلة بالإنترنت ومزامنة الدليل لمجموعة خدمات مجال Active Directory (AD DS). يتم توفيره هنا كخيار بحيث يمكنك اختبار Azure AD Identity Protection وتجربة ذلك في بيئة تمثل مؤسسة نموذجية.
  
## <a name="phase-2-use-azure-ad-identity-protection"></a>المرحلة الثانية: استخدام Azure AD Identity Protection

1. افتح مثيلا خاصا للمستعرض وسجل الدخول إلى مدخل Azure باستخدام [https://portal.azure.com](https://portal.azure.com) حساب المسؤول العام Microsoft 365 لبيئة اختبار المؤسسة.
2. في مدخل Microsoft Azure، اكتب **حماية الهوية** في مربع البحث، ثم حدد **Azure AD Identity Protection**.
3. في جزء **Identity Protection - Overview** ، حدد كل تقرير لمعرفة ما يقدمه التقرير.
4. ضمن **"إشعار"**، حدد **"Users at risked alerts**".
5. في جزء " **Users at risked alerts** "، حدد **"Medium**".
6. بالنسبة **إلى رسائل البريد الإلكتروني المرسلة إلى المستخدمين التاليين**، حدد **"تضمين** " وتحقق من وجود حساب المسؤول العمومي في قائمة الأعضاء المحددين.
7. حدد **حفظ**.

ضمن **"حماية**"، حدد نهج مختلفة لمعرفة كيفية تكوينها. إذا قمت بإنشاء نهج وتنشيطه، فتأكد من أنه لا يمنع الوصول لجميع المستخدمين، أو قد لا تتمكن من تسجيل الدخول. لمنع حدوث ذلك، قم باستبعاد حسابات مستخدمين معينة، مثل المسؤولين العموميين.

لمزيد من الاختبار والتجريب، راجع [محاكاة أحداث المخاطر](/azure/active-directory/active-directory-identityprotection-playbook).

## <a name="next-step"></a>الخطوة التالية

استكشف ميزات [وإمكانات الهوية](m365-enterprise-test-lab-guides.md#identity) الإضافية في بيئة الاختبار الخاصة بك.

## <a name="see-also"></a>راجع أيضًا

[نشر الهوية](deploy-identity-solution-overview.md)

[Microsoft 365 لدلائل مختبر اختبار المؤسسة](m365-enterprise-test-lab-guides.md)

[نظرة عامة حول Microsoft 365 للمؤسسات](microsoft-365-overview.md)

[موارد ووثائق Microsoft 365 للمؤسسات](/microsoft-365-enterprise/)