---
title: تكوين أمان Microsoft 365 المنارة
f1.keywords: CSH
ms.author: sharik
author: SKjerland
manager: scotv
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
description: بالنسبة إلى موفري الخدمات المدارة (MSPs) Microsoft 365 المنارة، تعرف على كيفية تكوين أمان المدخل.
ms.openlocfilehash: 532ce9d6e90ea4d502c6898a105702d525f05a1b
ms.sourcegitcommit: adea59259a5900cad5de29ddf46d1ca9e9e1c82f
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/04/2022
ms.locfileid: "64632678"
---
# <a name="configure-microsoft-365-lighthouse-portal-security"></a>تكوين أمان Microsoft 365 المنارة

إن حماية الوصول إلى بيانات العملاء عندما يقوم موفر الخدمة المدارة (MSP) بتفويض أذونات الوصول إلى المستأجرين من أولويات الأمان الإلكتروني. Microsoft 365 المنارة مع القدرات المطلوبة والاختيارية لمساعدتك على تكوين أمان مدخل المنارة. يجب إعداد أدوار معينة مع تمكين المصادقة متعددة العوامل (MFA) قبل أن تتمكن من الوصول إلى المنارة. يمكنك بشكل اختياري إعداد Azure AD إدارة الهويات المتميزة (PIM) والوصول الشرطي.

## <a name="set-up-multifactor-authentication-mfa"></a>إعداد المصادقة متعددة العوامل (MFA)

كما هو مذكور في منشور المدونة [لا يهم $word Pa$:](https://techcommunity.microsoft.com/t5/azure-active-directory-identity/your-pa-word-doesn-t-matter/ba-p/731984)

> "كلمة المرور الخاصة بك لا تهم، ولكن MFA تهمك. استنادا إلى دراساتنا، فإن احتمال تعرض حسابك للانتهاك أقل بنسبة 99.9٪ إذا كنت تستخدم MFA."

عندما يصل المستخدمون إلى "المنارة" للمرة الأولى، سيتم مطالبتهم بإعداد MFA إذا لم يتم تكوين Microsoft 365 الخاص بهم بالفعل. لن يتمكن المستخدمون من الوصول إلى "المنارة" حتى تكتمل خطوة إعداد MFA المطلوبة. لمعرفة المزيد حول أساليب المصادقة، راجع إعداد Microsoft 365 [تسجيل الدخول للمصادقة متعددة العوامل](https://support.microsoft.com/office/ace1d096-61e5-449b-a875-58eb3d74de14).

## <a name="set-up-role-based-access-control"></a>إعداد عنصر تحكم الوصول المستند إلى الدور

يمنح التحكم بالوصول المستند إلى الدور (RBAC) إمكانية الوصول إلى الموارد أو المعلومات استنادا إلى أدوار المستخدمين. يقتصر الوصول إلى بيانات وإعدادات مستأجر العميل في المنارة على أدوار معينة من برنامج Cloud Solution Provider (CSP). لإعداد أدوار RBAC في المنارة، نوصي باستخدام امتيازات المسؤول المفوض (GDAP) لتنفيذ التعيينات الدقيقة للمستخدمين. لا تزال امتيازات المسؤول المفوض (DAP) مطلوبة للمستأجر للتمكن من التمكن من الوصول إلى امتيازات المسؤول المفوض (DAP) بنجاح، ولكن سيتمكن عملاء GDAP فقط قريبا من التمكن من العمل دون تبعية ل DAP. يكون لأذونات GDAP الأسبقية عند تباعد DAP و GDAP للعميل. 

لإعداد علاقة GDAP، راجع الحصول على أذونات المسؤول [المفردة لإدارة خدمة أحد العملاء](/partner-center/gdap-obtain-admin-permissions-to-manage-customer). لمزيد من المعلومات حول الأدوار التي نوصي باستخدام "المنارة"، راجع نظرة عامة على الأذونات [في Microsoft 365 المنارة](m365-lighthouse-overview-of-permissions.md).

يمكن أيضا لتقنيي MSP الوصول إلى المنارة باستخدام أدوار "وكيل المسؤول" أو "وكيل المساعدة" عبر "امتيازات المسؤول المفوض" (DAP).

بالنسبة إلى الإجراءات ذات الصلة بالمستأجر غير المتعلقة بالعملاء في "المنارة" (على سبيل المثال، التكميل، إلغاء تنشيط/إعادة تنشيط العميل، إدارة العلامات، مراجعة السجلات)، يجب أن يكون لفنيي MSP دور تم تعيينه في المستأجر الشريك. راجع [نظرة عامة حول الأذونات في Microsoft 365 المنارة](m365-lighthouse-overview-of-permissions.md) للحصول على مزيد من التفاصيل حول أدوار المستأجر الشريك.

## <a name="set-up-azure-ad-privileged-identity-management-pim"></a>إعداد Azure AD إدارة الهويات المتميزة (PIM)

يمكن أن يقلل MSPs من عدد الأشخاص الذين لديهم حق الوصول إلى الدور المتميز للوصول إلى المعلومات أو الموارد الآمنة باستخدام PIM. يقلل PIM من فرصة وصول شخص ضار إلى الموارد أو المستخدمين المخضرين الذين يؤثرون على مورد حساس عن غير قصد. بإمكان MSPs أيضا منح المستخدمين أدوار امتيازات عالية في الوقت المناسب للوصول إلى الموارد، وإدوار تغييرات واسعة النطاق، ومراقبة ما يقوم به المستخدمون المعينون من خلال الوصول المميز لهم. 

> [!NOTE]
> يتطلب استخدام Azure AD PIM ترخيص Azure AD Premium P2 في مستأجر الشريك.

ترفع الخطوات التالية مستخدمي المستأجر الشريك إلى أدوار امتيازات أعلى ذات نطاق وقت باستخدام PIM:

1. إنشاء مجموعة قابلة لتعيين الأدوار كما هو موضح في المقالة إنشاء مجموعة لتعيين [الأدوار في Azure Active Directory](/azure/active-directory/roles/groups-create-eligible).

2. انتقل إلى [Azure AD –](https://portal.azure.com/#blade/Microsoft_AAD_IAM/GroupsManagementMenuBlade/AllGroups) كل المجموعات وأضف المجموعة الجديدة كعضو في مجموعة أمان لأدوار عالية الامتيازات (على سبيل المثال، مجموعة أمان وكلاء الإدارة ل DAP أو مجموعة أمان خاصة مماثلة لأدوار GDAP).

3. قم بإعداد الوصول المتميز إلى المجموعة الجديدة كما هو موضح في المقالة تعيين المالكين والأعضاء المؤهلين [لمجموعات الوصول المتميزة](/azure/active-directory/privileged-identity-management/groups-assign-member-owner).

لمعرفة المزيد حول PIM، راجع [ما هو إدارة الهويات المتميزة؟](/azure/active-directory/privileged-identity-management/pim-configure)

## <a name="set-up-risk-based-azure-ad-conditional-access"></a>إعداد الوصول الشرطي ل Azure AD المستند إلى المخاطر

قد يستخدم MSPs الوصول الشرطي المستند إلى المخاطر للتأكد من أن أعضاء فريق العمل يثبتون هويتهم باستخدام MFA وتغيير كلمة المرور الخاصة بهم عند الكشف عنها كمستخدم خطر (باستخدام بيانات الاعتماد التي تم تسريبها أو حسب معلومات المخاطر في Azure AD). يجب على المستخدمين أيضا تسجيل الدخول من موقع مألوف أو جهاز مسجل عند الكشف عن أنه تسجيل الدخول إلى موقع خطر. تتضمن السلوكيات الأخرى التي يمكن أن تكون ذات مخاطر تسجيل الدخول من عنوان IP ضار أو مجهول أو من موقع غير معتاد أو غير ممكن للسفر، أو استخدام رمز مميز غير عادي، أو استخدام كلمة مرور من برنامج تدخين كلمة مرور، أو اظهار سلوك تسجيل الدخول غير المعتاد الآخر. استنادا إلى مستوى مخاطر المستخدم، قد يختار MSPs أيضا حظر الوصول عند تسجيل الدخول. لمعرفة المزيد حول المخاطر، راجع [ما هي المخاطر؟](/azure/active-directory/identity-protection/concept-identity-protection-risks) 

> [!NOTE]
> يتطلب الوصول الشرطي ترخيص Azure AD Premium P2 في المستأجر الشريك. لإعداد الوصول الشرطي، راجع [تكوين الوصول الشرطي إلى Azure Active Directory](/appcenter/general/configuring-aad-conditional-access).

## <a name="related-content"></a>المحتوى ذي الصلة

[أذونات إعادة تعيين كلمة المرور](/azure/active-directory/roles/permissions-reference#password-reset-permissions) (مقالة)\
[متطلبات Microsoft 365 المنارة](m365-lighthouse-requirements.md) (مقالة)\
[نظرة عامة Microsoft 365 المنارة](m365-lighthouse-overview.md) (مقالة)\
[التسجيل للحصول على Microsoft 365 المنارة](m365-lighthouse-sign-up.md) (مقالة)\
[Microsoft 365 الأسئلة الشائعة حول المنارة](m365-lighthouse-faq.yml) (مقالة)