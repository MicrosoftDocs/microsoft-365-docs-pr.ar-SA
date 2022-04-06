---
title: Microsoft 365 دليل اختبار المؤسسة
f1.keywords:
- NOCSH
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
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
description: استخدم "أدلة اختبار المعمل" هذه لإعداد عرض تقديمي أو إثبات المبدأ أو بيئات تطوير/اختبار Microsoft 365 للمؤسسة.
ms.openlocfilehash: 18b243a0fea9cb4864a0375740c4ebadcc44d6c3
ms.sourcegitcommit: b3530441288b2bc44342e00e9025a49721796903
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/20/2022
ms.locfileid: "63681645"
---
# <a name="microsoft-365-for-enterprise-test-lab-guides"></a>Microsoft 365 دليل اختبار المؤسسة

*ينطبق هذا على كل من Microsoft 365 للمؤسسة Office 365 Enterprise.*

تساعدك Test Lab Guides (TLGs) على التعرف على منتجات Microsoft بسرعة. فهي توفر إرشادات وصفية لتكوين بيئات اختبار مبسطة ولكنها تمثيلية. يمكنك استخدام هذه البيئات للحصول على عرض تقديمي أو تخصيص أو إنشاء إثباتات معقدة للمفهوم طوال مدة الاشتراك التجريبي أو المدفوع.

تم تصميم TLG لتكون وحدات نمطية. فهي تعتمد على بعضها البعض لإنشاء تكوينات متعددة تتطابق بشكل وثيق مع احتياجات تكوين التعلم أو الاختبار. تساعدك التجربة العملية "لقد قمت بدمجه بنفسي وهو يعمل" على فهم متطلبات نشر منتج أو سيناريو جديد، بحيث يمكنك التخطيط بشكل أفضل لاستضافته في الإنتاج.

يمكنك أيضا استخدام TLG لإنشاء بيئات تمثيلية لتطوير التطبيقات واختبارها، المعروفة أيضا ببيئات dev/test.
  
![اختبار دليل المعمل لسحابة Microsoft.](../media/m365-enterprise-test-lab-guides/cloud-tlg-icon.png)

للحصول على خريطة مرئية لكل المقالات في Microsoft 365 دليل اختبار المؤسسة، قم بتوسيع الرسم التالي أو انتقل إلى Microsoft 365 الخاص بالمكدس دليل اختبار [اختبار المؤسسة](../downloads/Microsoft365EnterpriseTLGStack.pdf).

[![المكدس Microsoft 365 دليل اختبار المؤسسة.](../media/m365-enterprise-test-lab-guides/microsoft-365-enterprise-tlg-stack.png)](../downloads/Microsoft365EnterpriseTLGStack.pdf)

## <a name="base-configuration"></a>تكوين أساس

أولا، قم بإنشاء بيئة اختبار Microsoft 365 [للمؤسسة](/microsoft-365-enterprise/). يمكنك إنشاء نوعين مختلفين من التكوينات الأساسية:

- [تكوين أساسي](lightweight-base-configuration-microsoft-365-enterprise.md) خفيف - استخدم هذا الإعداد عندما تريد تكوين Microsoft 365 ميزات المؤسسة وإمكانياتها في بيئة السحابة فقط، والتي لا تتضمن أي مكونات في الموقع.

- تكوين قاعدة مؤسسة [محاكاة - استخدم](simulated-ent-base-configuration-microsoft-365-enterprise.md) هذا عندما تريد تكوين Microsoft 365 وشرحه لميزات المؤسسة وإمكانياتها في بيئة سحابة مختلطة، والتي تستخدم المكونات المحلية مثل مجال خدمات مجال Active Directory (AD DS).

يمكنك أيضا إنشاء بيئات اختبار Office 365 E5 من خلال عدم Microsoft 365 E5 ترخيص الإصدار التجريبي أو بيئة اختبار الإنتاج.
    
## <a name="identity"></a>الهوية

لإظهار الميزات والقدرات ذات الصلة بالهوية، راجع:

- [مزامنة كلمة المرور](password-hash-sync-m365-ent-test-environment.md)
  
   تمكين مزامنة الدليل المستندة إلى كلمة المرور واختبارها من وحدة تحكم مجال AD DS.

- [المصادقة المرورية](pass-through-auth-m365-ent-test-environment.md)
  
   تمكين المصادقة المرورية واختبارها إلى وحدة تحكم مجال AD DS.

- [المصادقة الخارجية](federated-identity-for-your-microsoft-365-dev-test-environment.md)
  
   تمكين المصادقة المتحدة واختبارها إلى وحدة تحكم مجال AD DS.

- [تسجيل الدخول الفردي السلس في Azure AD](single-sign-on-m365-ent-test-environment.md)
  
   قم بتمكين تسجيل الدخول الفردي السلس من Azure AD واختباره (SSO السلس) باستخدام وحدة تحكم مجال AD DS.

- [المصادقة متعددة العوامل](multi-factor-authentication-microsoft-365-test-environment.md)
  
   تمكين المصادقة الذكية متعددة العوامل المستندة إلى الهاتف واختبارها لحساب مستخدم معين.

- [حماية حسابات المسؤولين العامين](protect-global-administrator-accounts-microsoft-365-test-environment.md)

   تأمين حسابات المسؤول العام باستخدام سياسات الوصول الشرطي.

- [إعادة كتابة كلمة المرور](password-writeback-m365-ent-test-environment.md)

   استخدم كتابة كلمة المرور لتغيير كلمة المرور على حساب مستخدم AD DS من Azure AD.

- [إعادة تعيين كلمة المرور](password-reset-m365-ent-test-environment.md)

   استخدم إعادة تعيين كلمة مرور الخدمة الذاتية لإعادة تعيين كلمة المرور.

- [الترخيص التلقائي وعضوية المجموعة](automate-licenses-group-membership-microsoft-365-test-environment.md)

   اجعل إدارة الحسابات الجديدة أسهل من أي وقت مضى باستخدام الترخيص التلقائي وعضوية المجموعة الديناميكية.

- [حماية هوية Azure AD](azure-ad-identity-protection-microsoft-365-test-environment.md)

   فحص حسابات المستخدمين الحالية للفحص للنقاط الضعف.

- [الوصول إلى الهوية والجهاز](identity-device-access-m365-test-environment.md)

   أنشئ بيئة لاختبار تكوينات الوصول إلى الأجهزة والهوية الموصى بها ونهج الوصول الشرطي.

## <a name="mobile-device-management"></a>إدارة أجهزة المحمول

شرح الميزات والقدرات ذات الصلة بإدارة أجهزة المحمول، راجع:

- [سياسات توافق الأجهزة](mam-policies-for-your-microsoft-365-enterprise-dev-test-environment.md)
    
   قم بإنشاء مجموعة مستخدمين ونهاية لتوافق الأجهزة Windows 10 الأجهزة.
    
- [تسجيل أجهزة iOS وAndroid](enroll-ios-and-android-devices-in-your-microsoft-enterprise-365-dev-test-environ.md)
   
   قم بتسجيل أجهزة iOS أو Android وإدارتها عن بعد.

## <a name="information-protection"></a>حماية المعلومات

لإظهار الميزات والإمكانات المتعلقة بحماية المعلومات، راجع:

- [زيادة Microsoft 365 الأمان](increased-o365-security-microsoft-365-enterprise-dev-test-environment.md)
    
   قم بتكوين الإعدادات لزيادة Microsoft 365 الأمان واتحرى عن أدوات الأمان المضمنة.
  
- [تصنيف البيانات](data-classification-microsoft-365-enterprise-dev-test-environment.md)
    
   تكوين التسميات وتطبيقها على مستند في موقع فريق SharePoint Online.
    
- [إدارة الوصول المتميز](privileged-access-microsoft-365-enterprise-dev-test-environment.md)
    
   تكوين إدارة الوصول المتميز للوصول في الوقت المناسب إلى المهام المتميزة والمتميزة في مؤسستك.