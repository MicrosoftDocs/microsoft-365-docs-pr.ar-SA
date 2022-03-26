---
title: هوية شركة Contoso Corporation
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
- M365-identity-device-management
- Strat_O365_Enterprise
ms.custom: ''
description: كيف تستفيد شركة Contoso من الهوية كخدمة (IDaaS) وتوفر المصادقة المستندة إلى السحابة لموظفيها والمصادقة الخارجية لشركائها والعملاء.
ms.openlocfilehash: 1e1fb2a74c3c3b491ddfda2b0b88e4ad11926a5a
ms.sourcegitcommit: 6c57f1e90339d5a95c9e7875599dac9d3e032c3a
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 02/04/2022
ms.locfileid: "63565870"
---
# <a name="identity-for-the-contoso-corporation"></a>هوية شركة Contoso Corporation

توفر Microsoft الهوية كخدمة (IDaaS) عبر عروضها السحابية من خلال Azure Active Directory (Azure AD). لاعتماد Microsoft 365 للمؤسسات، كان يجب على حل Contoso IDaaS استخدام موفر الهوية المحلية الخاص بهم وأن يتضمن المصادقة المتحدة مع موفري الهويات الموثوق بهم الجهات الخارجية.

## <a name="the-contoso-active-directory-domain-services-forest"></a>غابة خدمات مجال Contoso Active Directory

تستخدم Contoso غابة خدمات مجال Active Directory (AD DS) واحدة ل contosocom\. مع سبعة مجالات فرعية، واحدة لكل منطقة في العالم. تحتوي المقرات الرئيسية، والمكاتب الإقليمية الرئيسية، مكاتب الأقمار الصناعية على وحدات تحكم المجالات للمصادقة المحلية والتخويل.

إليك غابة Contoso ذات المجالات الإقليمية لأجزاء مختلفة من العالم التي تحتوي على محاور إقليمية.

:::image type="content" alt-text="غابات Contoso ومجالاتها حول العالم." source="../media/contoso-identity/contoso-identity-fig1.png" lightbox="../media/contoso-identity/contoso-identity-fig1.png":::
 
قررت شركة Contoso استخدام الحسابات والمجموعات في غابة contosocom\. للمصادقة والتخويل لأحمال العمل Microsoft 365 والخدمات الخاصة بها.

## <a name="the-contoso-federated-authentication-infrastructure"></a>البنية الأساسية للمصادقة الخارجية في Contoso

تسمح Contoso ب:

- يستخدم العملاء حسابات Microsoft أو Facebook أو Google Mail الخاصة بهم من أجل تسجيل الدخول إلى موقع ويب عام للشركة.
- الموردون والشركاء لاستخدام حسابات LinkedIn أو Salesforce أو Google Mail الخاصة بهم تسجيل الدخول إلى إكسترانت شريك الشركة.

إليك Contoso DMZ الذي يحتوي على موقع ويب عام وإكسترانت شريك، وعلى مجموعة من خوادم خدمات خدمات Active Directory Federation (AD FS). إن DMZ متصلة بالإنترنت الذي يحتوي على العملاء والشركاء وخدمات الإنترنت.

![دعم Contoso للمصادقة الخارجية للعملاء والشركاء.](../media/contoso-identity/contoso-identity-fig2.png)
 
تسهل خوادم AD FS في DMZ مصادقة بيانات اعتماد العملاء من قبل موفري الهويات للوصول إلى موقع ويب العام وبيانات اعتماد الشريك للوصول إلى إكسترانت الشريك.

قررت شركة Contoso الاحتفاظ بهذه البنية الأساسية وتكريسها لمصادقة العميل ومصادقة الشريك. يحقق مهندسو هوية Contoso في تحويل هذه البنية الأساسية إلى حلول Azure AD [B2B](/azure/active-directory/b2b/hybrid-organizations) [وB2C](/azure/active-directory-b2c/solution-articles) .

## <a name="hybrid-identity-with-password-hash-synchronization-for-cloud-based-authentication"></a>الهوية المختلطة مع مزامنة كلمة المرور للمصادقة المستندة إلى السحابة

أراد Contoso استخدام غابة AD DS المحلية الخاصة به للمصادقة Microsoft 365 السحابة. وقررت استخدام مزامنة كلمة المرور المتزامنة (PHS).

يقوم PHS بمزامنة غابة AD DS المحلية مع مستأجر Azure AD الخاص باشتراك Microsoft 365 للمؤسسة ونسخ حسابات المستخدمين والمجموعة ونسخ إصدار مفاص من كلمات مرور حساب المستخدم.

للقيام بمزامنة الدليل، نشر Contoso أداة Azure AD الاتصال على خادم في مركز بيانات باريس.

إليك الخادم الذي يعمل على Azure AD الاتصال في غابة Contoso AD DS للحصول على التغييرات ثم مزامنة هذه التغييرات مع مستأجر Azure AD.

![البنية الأساسية لمزامنة دليل Contoso PHS.](../media/contoso-identity/contoso-identity-fig4.png)
 
## <a name="conditional-access-policies-for-zero-trust-identity-and-device-access"></a>سياسات الوصول الشرطي لهوية "الثقة الصفرية" والوصول إلى الجهاز

أنشأ Contoso مجموعة من سياسات Azure AD و Intune [Conditional Access](../security/office-365-security/identity-access-policies.md) لثلاثة مستويات حماية:

- *تنطبق حماية نقاط* البداية على كل حسابات المستخدمين.
- *تنطبق* حماية المؤسسة على القيادة العليا والموظفين التنفيذيين.
- *تنطبق حماية* الأمان المتخصصة على مستخدمين محددين في الأقسام المالية والقانونية وأقسام الأبحاث الذين لديهم حق الوصول إلى بيانات منظمة إلى حد كبير.

إليك المجموعة الناتجة من هوية Contoso ونهج الوصول الشرطي للجهاز.

:::image type="content" alt-text="هوية Contoso ونهج الوصول الشرطي للجهاز." source="../media/contoso-identity/contoso-identity-fig5.png" lightbox="../media/contoso-identity/contoso-identity-fig5.png":::
 
## <a name="next-step"></a>الخطوة التالية

تعرف على كيفية استخدام Contoso Microsoft Endpoint Configuration Manager الأساسية لنشر المعلومات الحالية [Windows 10 Enterprise](contoso-win10.md) المؤسسة.

## <a name="see-also"></a>راجع أيضًا

[نشر الهوية Microsoft 365](deploy-identity-solution-overview.md)

[Microsoft 365 نظرة عامة حول المؤسسة](microsoft-365-overview.md)

[أدلة الاختبار المعملية](m365-enterprise-test-lab-guides.md)