---
title: إعداد المصادقة متعددة العوامل للمستخدمين
f1.keywords:
- NOCSH
ms.author: kwekua
author: kwekua
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: high
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
ms.custom:
- AdminSurgePortfolio
- AdminTemplateSet
- admindeeplinkMAC
- adminvideo
- business_assist
search.appverid:
- BCS160
- MET150
- MOE150
- BEA160
- GEA150
ms.assetid: 8f0454b2-f51a-4d9c-bcde-2c48e41621c6
description: تعرف على كيفية إعداد المصادقة متعددة العوامل لمؤسستك.
monikerRange: o365-worldwide
ms.openlocfilehash: 00a92a7755c0200d0ad707e84ceb13fac7c978c9
ms.sourcegitcommit: e9692a40dfe1f8c2047699ae3301c114a01b0d3a
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/01/2022
ms.locfileid: "66603848"
---
# <a name="set-up-multifactor-authentication-for-microsoft-365"></a>إعداد المصادقة متعددة العوامل ل Microsoft 365

اطلع على [تعليمات Microsoft 365 small business](https://go.microsoft.com/fwlink/?linkid=2197659) على YouTube.

تعني المصادقة متعددة العوامل أنه يجب عليك أنت وموظفيك توفير أكثر من طريقة واحدة لتسجيل الدخول إلى Microsoft 365 هي واحدة من أسهل الطرق لتأمين عملك. استنادا إلى فهمك [للمصادقة متعددة العوامل (MFA) ودعمها في Microsoft 365](multi-factor-authentication-microsoft-365.md)، حان الوقت لإعدادها وطرحها في مؤسستك. 

> [!IMPORTANT]
> إذا اشتريت اشتراكك أو إصدارك التجريبي بعد 21 أكتوبر 2019، وتمت مطالبتك بمصادقة متعددة العوامل (MFA) عند تسجيل الدخول، فسيتم تمكين [إعدادات الأمان الافتراضية](/azure/active-directory/fundamentals/concept-fundamentals-security-defaults) تلقائيا لاشتراكك.

> [!TIP]
> إذا كنت بحاجة إلى مساعدة في الخطوات الواردة في هذا الموضوع، ففكر في [العمل مع أحد متخصصي الشركات الصغيرة من Microsoft](https://go.microsoft.com/fwlink/?linkid=2186871). باستخدام مساعد الأعمال، يمكنك أنت وموظفيك الوصول على مدار الساعة إلى خبراء الشركات الصغيرة أثناء تنمية أعمالك، بدءا من الإلحاق إلى الاستخدام اليومي.

## <a name="watch-turn-on-multifactor-authentication"></a>المراقبة: تشغيل المصادقة متعددة العوامل

اطلع على هذا الفيديو والبعض الآخر على [قناتنا على YouTube](https://go.microsoft.com/fwlink/?linkid=2197909).

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE2MuO3?autoplay=false]

1. انتقل إلى مركز مسؤولي Microsoft 365 في <a href="https://admin.microsoft.com/ " target="_blank">https://admin.microsoft.com</a>.
1. حدد **"إظهار الكل**"، ثم اختر **مركز مسؤول Azure Active Directory**.
1. حدد **Azure Active Directory**، **والخصائص**، **وإدارة إعدادات الأمان الافتراضية**.
1. ضمن **"تمكين إعدادات الأمان الافتراضية"**، حدد **"نعم"** ثم **"حفظ**".

## <a name="before-you-begin"></a>قبل البدء

- يجب أن تكون مسؤولا عموميا لإدارة المصادقة متعددة العوامل. لمزيد من المعلومات، راجع [حول أدوار المسؤولين](../add-users/about-admin-roles.md).
- إذا كان لديك مصادقة متعددة العوامل قديمة لكل مستخدم قيد التشغيل، [فقم بإيقاف تشغيل المصادقة متعددة العوامل القديمة لكل مستخدم](#turn-off-legacy-per-user-mfa).
- إذا كان لديك عملاء Office 2013 على أجهزة Windows، [فقم بتشغيل المصادقة الحديثة لعملاء Office 2013](./enable-modern-authentication.md).
- متقدم: إذا كان لديك خدمات دليل تابعة لجهة خارجية مع خدمات الأمان المشترك لـ Active Directory (AD FS)، فقم بإعداد خادم Azure MFA. راجع [السيناريوهات المتقدمة مع Azure AD Multifactor Authentication وحلول VPN لجهات خارجية](/azure/active-directory/authentication/howto-mfaserver-nps-vpn) للحصول على مزيد من المعلومات.

### <a name="turn-off-legacy-per-user-mfa"></a>إيقاف تشغيل المصادقة متعددة العوامل القديمة لكل مستخدم

إذا سبق لك تشغيل المصادقة متعددة العوامل لكل مستخدم، فيجب إيقاف تشغيلها قبل تمكين إعدادات الأمان الافتراضية.

1. في مركز مسؤولي Microsoft 365، في جزء التنقل الأيمن، اختر **المستخدمين النشطين للمستخدمين**\>.
1. في صفحة **"المستخدمون النشطون** "، اختر **المصادقة متعددة العوامل**.
1. في صفحة المصادقة متعددة العوامل، حدد كل مستخدم وعين حالة المصادقة متعددة العوامل إلى **"معطل**".

## <a name="turn-security-defaults-on-or-off"></a>تشغيل إعدادات الأمان الافتراضية أو إيقاف تشغيلها

بالنسبة لمعظم المؤسسات، توفر إعدادات الأمان الافتراضية مستوى جيدا من أمان تسجيل الدخول الإضافي. لمزيد من المعلومات، راجع [ما هي إعدادات الأمان الافتراضية؟](/azure/active-directory/fundamentals/concept-fundamentals-security-defaults)

إذا كان اشتراكك جديدا، فقد تكون إعدادات الأمان الافتراضية قيد التشغيل تلقائيا.

يمكنك تمكين إعدادات الأمان الافتراضية أو تعطيلها من جزء **الخصائص** ل Azure Active Directory (Azure AD) في مدخل Microsoft Azure.

1. سجل الدخول إلى [مركز مسؤولي Microsoft 365](https://admin.microsoft.com) باستخدام بيانات اعتماد المسؤول العمومي.
2. في جزء التنقل الأيمن، اختر **"إظهار الكل**" وضمن **مراكز مسؤول**، اختر **Azure Active Directory**.
3. في **مركز إدارة Azure Active Directory**، اختر **خصائص** **Azure Active Directory**\>.
4. في أسفل الصفحة، اختر **"إدارة إعدادات الأمان الافتراضية**".
5. اختر **"نعم** " لتمكين إعدادات الأمان الافتراضية أو **"لا** " لتعطيل إعدادات الأمان الافتراضية، ثم اختر **"حفظ**".

إذا كنت تستخدم [نهج الوصول المشروط الأساسية](/azure/active-directory/conditional-access/concept-baseline-protection)، فستتم مطالبتك بإيقاف تشغيلها قبل الانتقال إلى استخدام إعدادات الأمان الافتراضية.

1. انتقل إلى [صفحة الوصول المشروط - النهج](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ConditionalAccessBlade/Policies).
2. اختر كل نهج أساسي قيد **التشغيل** وقم بتعيين **"تمكين النهج** " إلى **"إيقاف تشغيل**".
3. انتقل إلى [صفحة Azure Active Directory - Properties](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ActiveDirectoryMenuBlade/Properties).
4. في أسفل الصفحة، اختر **"إدارة إعدادات الأمان الافتراضية**".
5. اختر **"نعم** " لتمكين إعدادات الأمان الافتراضية و **"لا** " لتعطيل إعدادات الأمان الافتراضية، ثم اختر **"حفظ**".

## <a name="use-conditional-access-policies"></a>استخدام نهج الوصول المشروط

إذا كانت مؤسستك بحاجة إلى أمان تسجيل الدخول بشكل أكثر دقة، يمكن أن توفر لك نهج الوصول المشروط المزيد من التحكم. يتيح لك الوصول المشروط إنشاء النهج التي تتفاعل مع أحداث تسجيل الدخول وتحديدها وطلب إجراءات إضافية قبل منح المستخدم حق الوصول إلى تطبيق أو خدمة.

> [!IMPORTANT]
> قم بإيقاف تشغيل كل من المصادقة متعددة العوامل لكل مستخدم والإعدادات الافتراضية للأمان قبل تمكين نهج الوصول المشروط.

يتوفر الوصول المشروط للعملاء الذين اشتروا Azure AD Premium P1، أو التراخيص التي تتضمن هذا، مثل Microsoft 365 Business Premium، Microsoft 365 E3. لمزيد من المعلومات، راجع [إنشاء نهج الوصول المشروط](/azure/active-directory/authentication/tutorial-enable-azure-mfa).

يتوفر الوصول المشروط المستند إلى المخاطر من خلال Azure AD ترخيص Premium P2، أو التراخيص التي تتضمن هذا، مثل Microsoft 365 E5. لمزيد من المعلومات، راجع [الوصول المشروط المستند إلى المخاطر](/azure/active-directory/conditional-access/howto-conditional-access-policy-risk).

لمزيد من المعلومات حول Azure AD P1 وP2، راجع [أسعار Azure Active Directory](https://azure.microsoft.com/pricing/details/active-directory/).

### <a name="turn-on-modern-authentication-for-your-organization"></a>تشغيل المصادقة الحديثة لمؤسستك

بالنسبة لمعظم الاشتراكات، يتم تشغيل المصادقة الحديثة تلقائيا، ولكن إذا اشتريت اشتراكك قبل أغسطس 2017، فمن المحتمل أنك ستحتاج إلى تشغيل المصادقة الحديثة للحصول على ميزات مثل المصادقة متعددة العوامل للعمل في عملاء Windows مثل Outlook.

1. في <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">مركز مسؤولي Microsoft 365</a>، في جزء التنقل الأيمن، اختر إعدادات **Settings** \> **Org**.
2. ضمن علامة التبويب **"الخدمات** "، اختر **المصادقة الحديثة**، وفي جزء **المصادقة الحديثة** ، تأكد من تحديد **تمكين المصادقة الحديثة** . اختر **"حفظ التغييرات**".

## <a name="next-steps"></a>الخطوات التالية

- [كيفية التسجيل للحصول على طريقة التحقق الإضافية الخاصة بهم](https://support.microsoft.com/office/ace1d096-61e5-449b-a875-58eb3d74de14)
- [ما هو: المصادقة متعددة العوامل](https://support.microsoft.com/help/4577374/what-is-multifactor-authentication)
- [كيفية تسجيل الدخول بعد التسجيل](https://support.microsoft.com/office/2b856342-170a-438e-9a4f-3c092394d3cb)
- [كيفية تغيير أسلوب التحقق الإضافي](https://support.microsoft.com/office/956ec8d0-7081-4518-a701-f8414cc20831)

## <a name="related-content"></a>المحتويات ذات الصلة

[إعداد المصادقة متعددة العوامل](set-up-multi-factor-authentication.md) (فيديو)\

[تشغيل المصادقة متعددة العوامل لهاتفك](https://support.microsoft.com/office/ace1d096-61e5-449b-a875-58eb3d74de14) (مقالة)\

[إعدادات الأمان الافتراضية والمصادقة متعددة العوامل](/microsoft-365/business-premium/m365bp-conditional-access) (المقالة)