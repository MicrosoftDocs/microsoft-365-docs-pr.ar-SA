---
title: Microsoft 365 لدلائل مختبر اختبار المؤسسة
f1.keywords:
- NOCSH
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 11/20/2019
audience: ITPro
ms.topic: landing-page
ms.service: o365-solutions
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Strat_O365_Enterprise
ms.custom:
- Ent_TLGs
- seo-marvel-apr2020
ms.assetid: 706d5449-45e5-4b0c-a012-ab60501899ad
description: استخدم دلائل مختبر الاختبار هذه لإعداد العرض التوضيحي أو إثبات المفهوم أو بيئات التطوير/الاختبار Microsoft 365 للمؤسسة.
ms.openlocfilehash: 8c4444b599682ad40ebba88b37d83125fccd99f0
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/27/2022
ms.locfileid: "65097415"
---
# <a name="microsoft-365-for-enterprise-test-lab-guides"></a>Microsoft 365 لدلائل مختبر اختبار المؤسسة

*ينطبق هذا على كل من Microsoft 365 للمؤسسة Office 365 Enterprise.*

تساعدك إرشادات مختبر الاختبار (TLGs) على التعرف بسرعة على منتجات Microsoft. وهي توفر تعليمات توجيهية لتكوين بيئات اختبار مبسطة ولكنها تمثيلية. يمكنك استخدام هذه البيئات لعرض إثباتات المبدأ المعقدة أو تخصيصها أو إنشائها طوال مدة الاشتراك التجريبي أو المدفوع.

تم تصميم مجموعات TLG لتكون وحدات نمطية. إنها تعتمد على بعضها لإنشاء تكوينات متعددة تتطابق بشكل وثيق مع احتياجات تكوين التعلم أو الاختبار. تساعدك التجربة العملية "لقد بنيتها بنفسي وتعمل" على فهم متطلبات النشر لمنتج أو سيناريو جديد، بحيث يمكنك التخطيط بشكل أفضل لاستضافته في الإنتاج.

يمكنك أيضا استخدام مجموعات TLG لإنشاء بيئات تمثيلية لتطوير التطبيقات واختبارها، والمعروفة أيضا باسم بيئات التطوير/الاختبار.
  
![اختبار دلائل المختبر لسحابة Microsoft.](../media/m365-enterprise-test-lab-guides/cloud-tlg-icon.png)

للحصول على خريطة مرئية لجميع المقالات في Microsoft 365 لمكدس دليل مختبر اختبار المؤسسة، قم بتوسيع الرسم التالي أو انتقل إلى [Microsoft 365 للمؤسسة Test Lab Guide Stack](../downloads/Microsoft365EnterpriseTLGStack.pdf).

[![Microsoft 365 لمكدس دليل مختبر اختبار المؤسسة.](../media/m365-enterprise-test-lab-guides/microsoft-365-enterprise-tlg-stack.png)](../downloads/Microsoft365EnterpriseTLGStack.pdf)

## <a name="base-configuration"></a>التكوين الأساسي

أولا، قم بإنشاء بيئة اختبار [Microsoft 365 للمؤسسة](/microsoft-365-enterprise/). يمكنك إنشاء نوعين مختلفين من التكوينات الأساسية:

- [تكوين أساسي خفيف الوزن](lightweight-base-configuration-microsoft-365-enterprise.md) - استخدم هذا عندما تريد تكوين Microsoft 365 وشرحها لميزات المؤسسة وقدراتها في بيئة سحابية فقط، والتي لا تتضمن أي مكونات محلية.

- [محاكاة تكوين قاعدة المؤسسة](simulated-ent-base-configuration-microsoft-365-enterprise.md) - استخدم هذا عندما تريد تكوين Microsoft 365 وشرحها لميزات المؤسسة وقدراتها في بيئة سحابية مختلطة، والتي تستخدم مكونات محلية مثل مجال خدمات مجال Active Directory (AD DS).

يمكنك أيضا إنشاء بيئات اختبار Office 365 E5 عن طريق عدم إضافة ترخيص Microsoft 365 E5 إلى بيئة اختبار الإصدار التجريبي أو الإنتاج.
    
## <a name="identity"></a>الهوية

لإظهار الميزات والقدرات المتعلقة بالهوية، راجع:

- [مزامنة تجزئة كلمة المرور](password-hash-sync-m365-ent-test-environment.md)
  
   تمكين مزامنة الدليل المستند إلى تجزئة كلمة المرور واختبارها من وحدة تحكم مجال AD DS.

- [مصادقة المرور](pass-through-auth-m365-ent-test-environment.md)
  
   تمكين واختبار مصادقة المرور إلى وحدة تحكم مجال AD DS.

- [مصادقة جهات الاتصال الخارجية](federated-identity-for-your-microsoft-365-dev-test-environment.md)
  
   تمكين المصادقة الموحدة واختبارها إلى وحدة تحكم مجال AD DS.

- [تسجيل الدخول الأحادي السلس إلى Azure AD](single-sign-on-m365-ent-test-environment.md)
  
   تمكين واختبار تسجيل الدخول الأحادي السلس إلى Azure AD باستخدام وحدة تحكم مجال AD DS.

- [المصادقة متعددة العوامل](multi-factor-authentication-microsoft-365-test-environment.md)
  
   تمكين واختبار المصادقة متعددة العوامل المستندة إلى الهاتف الذكي لحساب مستخدم معين.

- [حماية حسابات المسؤولين العموميين](protect-global-administrator-accounts-microsoft-365-test-environment.md)

   تأمين حسابات المسؤول العام باستخدام نهج الوصول المشروط.

- [إعادة كتابة كلمة المرور](password-writeback-m365-ent-test-environment.md)

   استخدم إعادة كتابة كلمة المرور لتغيير كلمة المرور على حساب مستخدم AD DS من Azure AD.

- [إعادة تعيين كلمة المرور](password-reset-m365-ent-test-environment.md)

   استخدم إعادة تعيين كلمة مرور الخدمة الذاتية لإعادة تعيين كلمة المرور.

- [الترخيص التلقائي وعضوية المجموعة](automate-licenses-group-membership-microsoft-365-test-environment.md)

   اجعل إدارة الحسابات الجديدة أسهل من أي وقت مضى مع الترخيص التلقائي وعضوية المجموعة الديناميكية.

- [حماية الهوية في Azure AD](azure-ad-identity-protection-microsoft-365-test-environment.md)

   فحص حسابات المستخدمين الحالية بحثا عن الثغرات الأمنية.

- [الوصول إلى الهوية والجهاز](identity-device-access-m365-test-environment.md)

   إنشاء بيئة لاختبار التكوينات الموصى بها للوصول إلى الهوية والجهاز ونهج الوصول المشروط.

## <a name="mobile-device-management"></a>إدارة الأجهزة المحمولة

لإظهار الميزات والقدرات المتعلقة بإدارة الأجهزة المحمولة، راجع:

- [نهج توافق الجهاز](mam-policies-for-your-microsoft-365-enterprise-dev-test-environment.md)
    
   إنشاء مجموعة مستخدمين ونهج توافق الأجهزة للأجهزة Windows 10.
    
- [تسجيل أجهزة iOS وAndroid](enroll-ios-and-android-devices-in-your-microsoft-enterprise-365-dev-test-environ.md)
   
   تسجيل أجهزة iOS أو Android وإدارتها عن بعد.

## <a name="information-protection"></a>حماية المعلومات

لإظهار الميزات والقدرات المتعلقة بحماية المعلومات، راجع:

- [أمان Microsoft 365 متزايد](increased-o365-security-microsoft-365-enterprise-dev-test-environment.md)
    
   تكوين الإعدادات لزيادة أمان Microsoft 365 والتحقيق في أدوات الأمان المضمنة.
  
- [تصنيف البيانات](data-classification-microsoft-365-enterprise-dev-test-environment.md)
    
   تكوين التسميات وتطبيقها على مستند في موقع فريق SharePoint Online.
    
- [إدارة الوصول المتميز](privileged-access-microsoft-365-enterprise-dev-test-environment.md)
    
   تكوين إدارة الوصول المتميز للوصول في الوقت المناسب إلى المهام المرتفعة والمتميزة في مؤسستك.