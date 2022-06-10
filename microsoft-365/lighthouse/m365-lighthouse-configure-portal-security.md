---
title: تكوين أمان مدخل Lighthouse Microsoft 365
f1.keywords: CSH
ms.author: sharik
author: SKjerland
manager: scotv
ms-reviewer: vivkuma
audience: Admin
ms.topic: article
ms.prod: microsoft-365-lighthouse
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
ms.custom:
- AdminSurgePortfolio
- M365-Lighthouse
search.appverid: MET150
description: بالنسبة لموفري الخدمات المدارة (MSPs) الذين يستخدمون Microsoft 365 Lighthouse، تعرف على كيفية تكوين أمان المدخل.
ms.openlocfilehash: 5033787f314036f345a00b7f9632851317ed05f0
ms.sourcegitcommit: 133bf9097785309da45df6f374a712a48b33f8e9
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 06/10/2022
ms.locfileid: "66013563"
---
# <a name="configure-microsoft-365-lighthouse-portal-security"></a>تكوين أمان مدخل Lighthouse Microsoft 365

تعد حماية الوصول إلى بيانات العملاء عندما يقوم موفر الخدمة المدارة (MSP) بتفويض أذونات الوصول إلى مستأجريه أولوية أمان عبر الإنترنت. يأتي Microsoft 365 Lighthouse مع كل من القدرات المطلوبة والاختيارية لمساعدتك على تكوين أمان مدخل Lighthouse. يجب إعداد أدوار محددة مع تمكين المصادقة متعددة العوامل (MFA) قبل أن تتمكن من الوصول إلى Lighthouse. يمكنك إعداد Azure AD إدارة الهويات المتميزة (PIM) والوصول المشروط اختياريا.

## <a name="set-up-multifactor-authentication-mfa"></a>إعداد المصادقة متعددة العوامل (MFA)

كما هو مذكور في منشور المدونة [الخاص بك Pa$$word لا يهم](https://techcommunity.microsoft.com/t5/azure-active-directory-identity/your-pa-word-doesn-t-matter/ba-p/731984):

> "كلمة المرور الخاصة بك لا يهم، ولكن MFA لا يهم. استنادا إلى دراساتنا، يكون حسابك أقل عرضة للاختراق بنسبة أكثر من 99.9٪ إذا كنت تستخدم المصادقة متعددة العوامل."

عندما يصل المستخدمون إلى Lighthouse للمرة الأولى، ستتم مطالبتهم بإعداد المصادقة متعددة العوامل (MFA) إذا لم يتم تكوين حسابهم Microsoft 365 بالفعل. لن يتمكن المستخدمون من الوصول إلى Lighthouse حتى تكتمل خطوة إعداد المصادقة متعددة العوامل المطلوبة. لمعرفة المزيد حول أساليب المصادقة، راجع [إعداد تسجيل الدخول Microsoft 365 للمصادقة متعددة العوامل](https://support.microsoft.com/office/ace1d096-61e5-449b-a875-58eb3d74de14).

## <a name="set-up-role-based-access-control"></a>إعداد التحكم في الوصول المستند إلى الدور

يمنح التحكم في الوصول استنادا إلى الدور (RBAC) الوصول إلى الموارد أو المعلومات استنادا إلى أدوار المستخدم. يقتصر الوصول إلى بيانات وإعدادات مستأجر العميل في Lighthouse على أدوار محددة من برنامج Cloud Solution Provider (CSP). لإعداد أدوار RBAC في Lighthouse، نوصي باستخدام امتيازات المسؤول المفوض متعدد المستويات (GDAP) لتنفيذ التعيينات الدقيقة للمستخدمين. لا تزال امتيازات المسؤول المفوض (DAP) مطلوبة للمستأجر للإلحاق بنجاح، ولكن سيتمكن عملاء GDAP فقط قريبا من الإلحاق دون تبعية على DAP. تأخذ أذونات GDAP الأسبقية عندما تتعايش DAP وGDAP مع العميل.

لإعداد علاقة GDAP، راجع [الحصول على أذونات المسؤول متعدد المستويات لإدارة خدمة العميل](/partner-center/gdap-obtain-admin-permissions-to-manage-customer). لمزيد من المعلومات حول الأدوار التي نوصي باستخدام Lighthouse عليها، راجع [نظرة عامة على الأذونات في Microsoft 365 Lighthouse](m365-lighthouse-overview-of-permissions.md).

قد يصل فنيو MSP أيضا إلى Lighthouse باستخدام أدوار وكيل المسؤول أو وكيل Helpdesk عبر امتيازات المسؤول المفوض (DAP).

بالنسبة للإجراءات المتعلقة بالمستأجر غير المتعلقة بالعميل في Lighthouse (على سبيل المثال، الإلحاق، وإلغاء تنشيط/إعادة تنشيط العميل، وإدارة العلامات، ومراجعة السجلات)، يجب أن يكون لفنيي MSP دور معين في مستأجر الشريك. راجع [نظرة عامة على الأذونات في Microsoft 365 Lighthouse](m365-lighthouse-overview-of-permissions.md) للحصول على مزيد من التفاصيل حول أدوار المستأجرين الشركاء.

## <a name="set-up-azure-ad-privileged-identity-management-pim"></a>إعداد Azure AD إدارة الهويات المتميزة (PIM)

يمكن ل MSPs تقليل عدد الأشخاص الذين لديهم حق وصول عالي الامتيازات إلى معلومات أو موارد آمنة باستخدام PIM. تقلل PIM من فرصة وصول شخص ضار إلى الموارد أو المستخدمين المعتمدين عن غير قصد للتأثير على مورد حساس. يمكن ل MSPs أيضا منح المستخدمين أدوار امتيازات عالية في الوقت المناسب للوصول إلى الموارد وإجراء تغييرات واسعة ومراقبة ما يفعله المستخدمون المعينون بالوصول المتميز.

> [!NOTE]
> يتطلب استخدام Azure AD PIM ترخيص P2 Azure AD Premium في المستأجر الشريك.

تقوم الخطوات التالية برفع مستخدمي المستأجرين الشركاء إلى أدوار امتيازات أعلى ذات نطاق زمني باستخدام PIM:

1. إنشاء مجموعة قابلة لتعيين الأدوار كما هو موضح في المقالة [إنشاء مجموعة لتعيين الأدوار في Azure Active Directory](/azure/active-directory/roles/groups-create-eligible).

2. انتقل إلى [Azure AD – كافة المجموعات](https://portal.azure.com/#blade/Microsoft_AAD_IAM/GroupsManagementMenuBlade/AllGroups) وأضف المجموعة الجديدة كعضو في مجموعة أمان للأدوار ذات الامتيازات العالية (على سبيل المثال، مجموعة أمان وكلاء الإدارة ل DAP أو مجموعة أمان خاصة بشكل مماثل لأدوار GDAP).

3. قم بإعداد الوصول المتميز إلى المجموعة الجديدة كما هو موضح في [المقالة "تعيين مالكين مؤهلين وأعضاء لمجموعات الوصول المتميز](/azure/active-directory/privileged-identity-management/groups-assign-member-owner)".

لمعرفة المزيد حول PIM، راجع [ما هو إدارة الهويات المتميزة؟](/azure/active-directory/privileged-identity-management/pim-configure)

## <a name="set-up-risk-based-azure-ad-conditional-access"></a>إعداد الوصول المشروط Azure AD المستند إلى المخاطر

قد تستخدم MSPs الوصول المشروط المستند إلى المخاطر للتأكد من أن أعضاء فريق العمل يثبتون هويتهم باستخدام المصادقة متعددة العوامل (MFA) ومن خلال تغيير كلمة المرور الخاصة بهم عند الكشف عنها كمستخدم محفوف بالمخاطر (مع بيانات اعتماد مسربة أو لكل Azure AD التحليل الذكي للمخاطر). يجب على المستخدمين أيضا تسجيل الدخول من موقع مألوف أو جهاز مسجل عند اكتشافه كسجل دخول محفوف بالمخاطر. تتضمن السلوكيات الأخرى المحفوفة بالمخاطر تسجيل الدخول من عنوان IP ضار أو مجهول أو من موقع سفر غير نمطي أو مستحيل، أو استخدام رمز مميز غير طبيعي، أو استخدام كلمة مرور من نشر كلمة مرور، أو إظهار سلوك تسجيل دخول غير عادي آخر. اعتمادا على مستوى مخاطر المستخدم، قد تختار MSPs أيضا حظر الوصول عند تسجيل الدخول. لمعرفة المزيد حول المخاطر، راجع [ما هي المخاطر؟](/azure/active-directory/identity-protection/concept-identity-protection-risks)

> [!NOTE]
> يتطلب الوصول المشروط ترخيص P2 Azure AD Premium في مستأجر الشريك. لإعداد الوصول المشروط، راجع [تكوين الوصول المشروط ل Azure Active Directory](/appcenter/general/configuring-aad-conditional-access).

## <a name="related-content"></a>المحتويات ذات الصلة

[أذونات إعادة تعيين كلمة المرور](/azure/active-directory/roles/permissions-reference#password-reset-permissions) (مقالة)\
[نظرة عامة على الأذونات في Microsoft 365 Lighthouse](m365-lighthouse-overview-of-permissions.md) (مقالة)\
[عرض أدوار Azure Active Directory في Microsoft 365 Lighthouse](m365-lighthouse-view-your-roles.md) (article)\
[متطلبات Microsoft 365 Lighthouse](m365-lighthouse-requirements.md) (مقالة)\
[نظرة عامة على Microsoft 365 Lighthouse](m365-lighthouse-overview.md) (مقالة)\
[التسجيل للحصول على Microsoft 365 Lighthouse](m365-lighthouse-sign-up.md) (مقالة)\
[الأسئلة المتداولة حول Microsoft 365 Lighthouse](m365-lighthouse-faq.yml) (مقالة)