---
title: هوية شركة Contoso
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
- M365-identity-device-management
- Strat_O365_Enterprise
ms.custom: ''
description: كيف تستفيد شركة Contoso من الهوية كخدمة (IDaaS) وتوفر المصادقة المستندة إلى السحابة لموظفيها والمصادقة الموحدة لشركائها وعملائها.
ms.openlocfilehash: fc53ae761f26776c4bd632704505d2eafe8daa88
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/27/2022
ms.locfileid: "65094427"
---
# <a name="identity-for-the-contoso-corporation"></a>هوية شركة Contoso

توفر Microsoft خدمة الهوية كخدمة (IDaaS) عبر عروضها السحابية من خلال Azure Active Directory (Azure AD). لاعتماد Microsoft 365 للمؤسسة، كان على حل Contoso IDaaS استخدام موفر الهوية المحلي الخاص به وتضمين المصادقة الموحدة مع موفري الهوية الموثوق بهم الحاليين التابعين لجهات خارجية.

## <a name="the-contoso-active-directory-domain-services-forest"></a>غابة خدمات مجال Active Directory Contoso

تستخدم Contoso غابة خدمات مجال Active Directory واحدة (AD DS) ل contosocom\. مع سبعة مجالات فرعية، واحدة لكل منطقة من مناطق العالم. يحتوي المقر الرئيسي، والمكاتب المركزية الإقليمية، والمكاتب الفرعية على وحدات تحكم بالمجال للمصادقة والتخويل المحليين.

فيما يلي غابة Contoso مع المجالات الإقليمية لأجزاء مختلفة من العالم التي تحتوي على مراكز إقليمية.

:::image type="content" alt-text="غابة Contoso ومجالاتها في جميع أنحاء العالم." source="../media/contoso-identity/contoso-identity-fig1.png" lightbox="../media/contoso-identity/contoso-identity-fig1.png":::
 
قررت شركة Contoso استخدام الحسابات والمجموعات في غابة contosocom\. للمصادقة والتخويل لأحمال العمل والخدمات Microsoft 365.

## <a name="the-contoso-federated-authentication-infrastructure"></a>البنية الأساسية للمصادقة الموحدة ل Contoso

تسمح شركة Contoso ب:

- يمكن للعملاء استخدام حسابات Microsoft أو Facebook أو Google Mail لتسجيل الدخول إلى موقع ويب العام للشركة.
- يمكن للبائعين والشركاء استخدام حسابات LinkedIn أو Salesforce أو بريد Google لتسجيل الدخول إلى إكسترانت شريك الشركة.

فيما يلي Contoso DMZ التي تحتوي على موقع ويب عام، وإكسترانت شريك، ومجموعة من خوادم خدمات الأمان المشترك لـ Active Directory (AD FS). يتصل DMZ بالإنترنت الذي يحتوي على العملاء والشركاء وخدمات الإنترنت.

![دعم Contoso للمصادقة الموحدة للعملاء والشركاء.](../media/contoso-identity/contoso-identity-fig2.png)
 
تسهل خوادم AD FS في DMZ مصادقة بيانات اعتماد العميل من قبل موفري الهوية للوصول إلى موقع الويب العام وبيانات اعتماد الشريك للوصول إلى إكسترانت الشريك.

قررت شركة Contoso الاحتفاظ بهذه البنية الأساسية وتخصيصها لمصادقة العميل والشركاء. يحقق مهندسو الهوية في Contoso في تحويل هذه البنية الأساسية إلى حلول Azure AD [B2B](/azure/active-directory/b2b/hybrid-organizations) [وB2C](/azure/active-directory-b2c/solution-articles) .

## <a name="hybrid-identity-with-password-hash-synchronization-for-cloud-based-authentication"></a>الهوية المختلطة مع مزامنة تجزئة كلمة المرور للمصادقة المستندة إلى السحابة

أرادت شركة Contoso استخدام غابة AD DS المحلية الخاصة بها للمصادقة Microsoft 365 موارد السحابة. قررت استخدام مزامنة تجزئة كلمة المرور (PHS).

يقوم PHS بمزامنة غابة AD DS المحلية مع مستأجر Azure AD Microsoft 365 لاشتراك المؤسسة، ونسخ حسابات المستخدمين والمجموعة وإصدار متجزئة من كلمات مرور حساب المستخدم.

لإجراء مزامنة الدليل، نشرت شركة Contoso أداة الاتصال Azure AD على خادم في مركز بيانات باريس الخاص بها.

فيما يلي الخادم الذي يقوم بتشغيل Azure AD الاتصال التحقق من غابة Contoso AD DS للتغييرات ثم مزامنة هذه التغييرات مع مستأجر Azure AD.

![البنية الأساسية لمزامنة دليل Contoso PHS.](../media/contoso-identity/contoso-identity-fig4.png)
 
## <a name="conditional-access-policies-for-zero-trust-identity-and-device-access"></a>نهج الوصول المشروط للهوية ثقة معدومة والوصول إلى الجهاز

أنشأت شركة Contoso مجموعة من نهج Azure AD وIntune [Conditional Access](../security/office-365-security/identity-access-policies.md) لثلاثة مستويات حماية:

- تنطبق حماية *نقطة البداية* على جميع حسابات المستخدمين.
- تنطبق حماية *المؤسسة* على القيادة العليا والموظفين التنفيذيين.
- تنطبق الحماية *الأمنية المتخصصة* على مستخدمين محددين في أقسام الشؤون المالية والشؤون القانونية والبحثية الذين لديهم إمكانية الوصول إلى بيانات منظمة للغاية.

فيما يلي المجموعة الناتجة من نهج الوصول المشروط لهوية Contoso والجهاز.

:::image type="content" alt-text="نهج الوصول المشروط لهوية شركة Contoso وجهازها." source="../media/contoso-identity/contoso-identity-fig5.png" lightbox="../media/contoso-identity/contoso-identity-fig5.png":::
 
## <a name="next-step"></a>الخطوة التالية

تعرف على كيفية استخدام Contoso للبنية الأساسية Microsoft Endpoint Configuration Manager [لنشر Windows 10 Enterprise الحالية والحفاظ عليها](contoso-win10.md) عبر مؤسستها.

## <a name="see-also"></a>راجع أيضًا

[نشر الهوية Microsoft 365](deploy-identity-solution-overview.md)

[نظرة عامة حول Microsoft 365 للمؤسسات](microsoft-365-overview.md)

[اختبار إرشادات المختبر](m365-enterprise-test-lab-guides.md)