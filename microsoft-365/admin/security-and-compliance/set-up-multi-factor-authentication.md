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
description: تعرف على كيفية إعداد المصادقة متعددة العوامل لمنظمتك.
monikerRange: o365-worldwide
ms.openlocfilehash: 1279220ceb8de5c5fdb4361a258e2c2bfc1f7061
ms.sourcegitcommit: 6e90baef421ae06fd790b0453d3bdbf624b7f9c0
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 02/12/2022
ms.locfileid: "63569225"
---
# <a name="set-up-multifactor-authentication"></a>إعداد المصادقة متعددة العوامل

تعني المصادقة متعددة العوامل أنه يجب عليك أنت وموظفيك توفير أكثر من طريقة واحدة Microsoft 365 إحدى أسهل الطرق لتأمين أعمالك. استنادا إلى فهمك للمصادقة متعددة العوامل [(MFA)](multi-factor-authentication-microsoft-365.md) ودعمها في Microsoft 365، حان الوقت لإعدادها وإدائها إلى مؤسستك. 

> [!IMPORTANT]
> إذا اشتريت اشتراكك أو الإصدار التجريبي بعد 21 أكتوبر 2019، ومطالبتك ب MFA عند تسجيل الدخول، تم تمكين إعدادات الأمان الافتراضية تلقائيا لاشتراكك[](/azure/active-directory/fundamentals/concept-fundamentals-security-defaults).

> [!TIP]
> إذا كنت بحاجة إلى مساعدة بشأن الخطوات في هذا الموضوع، فنظر [في العمل مع أحد متخصصي Microsoft small business](https://go.microsoft.com/fwlink/?linkid=2186871). باستخدام "المساعدة في العمل"، يمكنك أنت وموظفيك الوصول على مدار الساعة إلى المتخصصين في الشركات الصغيرة بينما تنمو أعمالك، من التكهين إلى الاستخدام اليومي.

## <a name="watch-turn-on-multifactor-authentication"></a>شاهد: تشغيل المصادقة متعددة العوامل

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE2MuO3?autoplay=false]

1. انتقل إلى مركز مسؤولي Microsoft 365 في <a href="https://admin.microsoft.com/ " target="_blank">https://admin.microsoft.com</a>.
1. حدد  **إظهار الكل**، ثم اختر **مركز إدارة Azure Active Directory**.
1. حدد **Azure Active Directory**، **خصائص****، إدارة إعدادات الأمان الافتراضية**.
1. ضمن **تمكين إعدادات الأمان الافتراضية**، حدد **نعم** ثم **حفظ**.

## <a name="before-you-begin"></a>قبل البدء

- يجب أن تكون المسؤول العام لإدارة MFA. لمزيد من المعلومات، راجع [حول أدوار المسؤولين](../add-users/about-admin-roles.md).
- إذا تم تشغيل MFA القديمة لكل مستخدم، ف [قم إيقاف تشغيل MFA القديمة لكل مستخدم](#turn-off-legacy-per-user-mfa).
- إذا كان Office عملاء 2013 Windows الأجهزة، ف قم [تشغيل المصادقة الحديثة لعملاء Office 2013](./enable-modern-authentication.md).
- متقدم: إذا كان لديك خدمات دليل جهة خارجية باستخدام خدمات اتحاد Active Directory (AD FS)، ف قم بإعداد Azure MFA Server. لمزيد من المعلومات، راجع [السيناريوهات المتقدمة باستخدام مصادقة Azure AD متعددة العوامل وحلول VPN الخاصة لجهة](/azure/active-directory/authentication/howto-mfaserver-nps-vpn) خارجية.

### <a name="turn-off-legacy-per-user-mfa"></a>إيقاف تشغيل MFA القديمة لكل مستخدم

إذا قمت مسبقا تشغيل MFA لكل مستخدم، فيجب إيقاف تشغيله قبل تمكين إعدادات الأمان الافتراضية.

1. في مركز مسؤولي Microsoft 365، في التنقل الأيسر، اختر **المستخدمون** \> **النشطون**.
1. في صفحة **المستخدمون النشطون** ، اختر **مصادقة متعددة العوامل**.
1. في صفحة المصادقة متعددة العوامل، حدد كل مستخدم ثم قم بتعيين حالة المصادقة متعددة العوامل إلى **معطل**.

## <a name="turn-security-defaults-on-or-off"></a>تشغيل إعدادات الأمان الافتراضية أو إيقاف تشغيلها

بالنسبة لمعظم المؤسسات، توفر إعدادات الأمان الافتراضية مستوى جيدا من أمان تسجيل الدخول الإضافي. لمزيد من المعلومات، راجع [ما هي إعدادات الأمان الافتراضية؟](/azure/active-directory/fundamentals/concept-fundamentals-security-defaults)

إذا كان اشتراكك جديدا، فقد تكون إعدادات الأمان الافتراضية قد تم تشغيلها لك تلقائيا.

يمكنك تمكين إعدادات الأمان الافتراضية أو تعطيلها **من جزء الخصائص** ل Azure Active Directory (Azure AD) في مدخل Azure.

1. سجل [الدخول إلى مركز مسؤولي Microsoft 365](https://admin.microsoft.com) باستخدام بيانات اعتماد المسؤول العام.
2. في التنقل الأيسر، اختر **إظهار الكل** و ضمن **مراكز الإدارة**، اختر **Azure Active Directory**.
3. في مركز **إدارة Azure Active Directory،** اختر **خصائص Azure Active Directory** \> **.**
4. في أسفل الصفحة، اختر **إدارة إعدادات الأمان الافتراضية**.
5. اختر **نعم** لتمكين إعدادات الأمان الافتراضية أو **لا** لتعطيل إعدادات الأمان الافتراضية، ثم اختر **حفظ**.

إذا كنت [تستخدم سياسات الوصول](/azure/active-directory/conditional-access/concept-baseline-protection) الشرطي الأساسية، سيطلب منك إيقاف تشغيلها قبل الانتقال إلى استخدام إعدادات الأمان الافتراضية.

1. انتقل إلى [صفحة الوصول الشرطي - السياسات](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ConditionalAccessBlade/Policies).
2. اختر كل نهج أساسي **تم تشغيله،** ثم قم **بتعيين تمكين النهج** إلى **إيقاف التشغيل**.
3. انتقل إلى [صفحة Azure Active Directory - خصائص](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ActiveDirectoryMenuBlade/Properties).
4. في أسفل الصفحة، اختر **إدارة إعدادات الأمان الافتراضية**.
5. اختر **نعم** لتمكين إعدادات الأمان **الافتراضية ولا** لتعطيل إعدادات الأمان الافتراضية، ثم اختر **حفظ**.

## <a name="use-conditional-access-policies"></a>استخدام سياسات الوصول الشرطي

إذا كانت مؤسستك بحاجة إلى المزيد من احتياجات أمان تسجيل الدخول، يمكن أن توفر لك سياسات الوصول الشرطي المزيد من التحكم. يتيح لك الوصول الشرطي إنشاء سياسات تتفاعل مع أحداث تسجيل الدخول وتحديدها وطلب إجراءات إضافية قبل منح المستخدم حق الوصول إلى تطبيق أو خدمة.

> [!IMPORTANT]
> إيقاف تشغيل كل من إعدادات MFA والأمان لكل مستخدم قبل تمكين سياسات الوصول الشرطي.

يتوفر الوصول الشرطي للعملاء الذين اشتروا Azure AD Premium P1، أو التراخيص التي تتضمن ذلك، مثل Microsoft 365 Business Premium والتراخيص Microsoft 365 E3. لمزيد من المعلومات، راجع [إنشاء نهج الوصول الشرطي](/azure/active-directory/authentication/tutorial-enable-azure-mfa).

يتوفر الوصول الشرطي المستند إلى المخاطر من خلال ترخيص Azure AD Premium P2 أو التراخيص التي تتضمن ذلك، مثل Microsoft 365 E5. لمزيد من المعلومات، راجع [الوصول الشرطي المستند إلى المخاطر](/azure/active-directory/conditional-access/howto-conditional-access-policy-risk).

لمزيد من المعلومات حول Azure AD P1 و P2، راجع [أسعار Azure Active Directory](https://azure.microsoft.com/pricing/details/active-directory/).

### <a name="turn-on-modern-authentication-for-your-organization"></a>تشغيل المصادقة الحديثة لمنظمتك

بالنسبة لمعظم الاشتراكات، يتم تشغيل المصادقة الحديثة تلقائيا، ولكن إذا اشتريت اشتراكك قبل أغسطس 2017، فمن المرجح أنك ستحتاج إلى تشغيل المصادقة الحديثة لكي تتمكن من الحصول على ميزات مثل المصادقة متعددة العوامل للعمل في عملاء Windows مثل Outlook.


1. في <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">مركز مسؤولي Microsoft 365،</a> في التنقل الأيسر **، اختر الإعدادات** \> **المؤسسة.**
2. ضمن علامة **التبويب خدمات****، اختر مصادقة** حديثة، وفي جزء المصادقة الحديثة، تأكد من **تحديد تمكين** المصادقة الحديثة. اختر **حفظ التغييرات**.


## <a name="next-steps"></a>الخطوات التالية

- [كيفية التسجيل للحصول على أسلوب التحقق الإضافي](https://support.microsoft.com/office/ace1d096-61e5-449b-a875-58eb3d74de14)
- [ما هو: المصادقة متعددة العوامل](https://support.microsoft.com/help/4577374/what-is-multifactor-authentication)
- [كيفية تسجيل الدخول بعد التسجيل](https://support.microsoft.com/office/2b856342-170a-438e-9a4f-3c092394d3cb)
- [كيفية تغيير أسلوب التحقق الإضافي](https://support.microsoft.com/office/956ec8d0-7081-4518-a701-f8414cc20831)

## <a name="related-content"></a>المحتوى ذي الصلة

[إعداد المصادقة متعددة العوامل](set-up-multi-factor-authentication.md) (فيديو)

[تشغيل المصادقة متعددة العوامل لهاتفك](https://support.microsoft.com/office/ace1d096-61e5-449b-a875-58eb3d74de14)
