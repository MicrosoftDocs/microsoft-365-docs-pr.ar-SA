---
title: الخطوة 5. إدارة الأجهزة والتطبيقات Microsoft 365 لمستأجري المؤسسات
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.audience: ITPro
ms.topic: article
ms.prod: microsoft-365-enterprise
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Strat_O365_Enterprise
- m365solution-tenantmanagement
- tenant-management
- m365solution-scenario
ms.custom:
- Ent_Solutions
description: نشر الخيار الصحيح لإدارة الأجهزة والتطبيقات لمستأجري Microsoft 365.
ms.openlocfilehash: 3999d30aaeee9ebfc2af90b0aeeeaea1b46986fb
ms.sourcegitcommit: ebbe8713297675db5dcb3e0d9c3ae5e746b99196
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 05/14/2022
ms.locfileid: "65419451"
---
# <a name="step-5-device-and-app-management-for-your-microsoft-365-for-enterprise-tenants"></a>الخطوة 5. إدارة الأجهزة والتطبيقات Microsoft 365 لمستأجري المؤسسات

يتضمن Microsoft 365 للمؤسسة ميزات للمساعدة في إدارة الأجهزة واستخدام التطبيقات على تلك الأجهزة داخل مؤسستك مع إدارة أجهزة المحمول (MDM) وإدارة تطبيقات المحمول (MAM). يمكنك إدارة أجهزة iOS وAndroid macOS Windows لحماية الوصول إلى موارد مؤسستك، بما في ذلك بياناتك. على سبيل المثال، يمكنك منع إرسال رسائل البريد الإلكتروني إلى أشخاص من خارج مؤسستك أو عزل بيانات المؤسسة عن البيانات الشخصية على الأجهزة الشخصية للعامل.

فيما يلي مثال على التحقق من صحة المستخدمين وأجهزتهم واستخدامهم لتطبيقات الإنتاجية المحلية والسحابية مثل Microsoft Teams وإدارتها.

![التحقق من صحة المستخدمين والأجهزة والتطبيقات وإدارتها.](../media/tenant-management-overview/tenant-management-device-app-mgmt.png)

لمساعدتك على تأمين موارد مؤسستك وحمايتها، تتضمن Microsoft 365 للمؤسسة ميزات للمساعدة في إدارة الأجهزة ووصولها إلى التطبيقات. هناك خياران لإدارة الأجهزة:

- Microsoft Intune، وهو حل شامل لإدارة الأجهزة والتطبيقات للمؤسسات.
- Basic Mobility and Security، وهي مجموعة فرعية من خدمات Intune المضمنة مع جميع منتجات Microsoft 365 لإدارة الأجهزة في مؤسستك. لمزيد من المعلومات، راجع [قدرات التنقل الأساسي والأمان](../admin/basic-mobility-security/capabilities.md).

إذا كان لديك Microsoft 365 E3 أو E5، يجب عليك استخدام Intune.

## <a name="microsoft-intune"></a>Microsoft Intune

يمكنك استخدام [Microsoft Intune](/mem/intune/fundamentals/planning-guide) لإدارة الوصول إلى مؤسستك باستخدام MDM أو MAM. MDM هو عندما يقوم المستخدمون "بتسجيل" أجهزتهم في Intune. بعد تسجيل الجهاز، يكون جهازا مدارا ويمكنه تلقي نهج مؤسستك وقواعدها وإعداداتها. على سبيل المثال، يمكنك تثبيت تطبيقات معينة وإنشاء نهج كلمة مرور وتثبيت اتصال VPN والمزيد.

قد لا يرغب المستخدمون الذين لديهم أجهزتهم الشخصية في تسجيل أجهزتهم أو أن تتم إدارتهم بواسطة Intune وسياسات مؤسستك. ولكنك لا تزال بحاجة إلى حماية موارد مؤسستك وبياناتها. في هذا السيناريو، يمكنك حماية تطبيقاتك باستخدام MAM. على سبيل المثال، يمكنك استخدام نهج MAM الذي يتطلب من المستخدم إدخال رمز PIN عند الوصول إلى SharePoint على الجهاز.

ستحدد أيضا كيفية إدارة الأجهزة الشخصية والأجهزة المملوكة للمؤسسة. قد ترغب في معاملة الأجهزة بشكل مختلف، اعتمادا على استخدامها.

## <a name="identity-and-device-access-configurations"></a>تكوينات الوصول إلى الأجهزة والهويات

توفر Microsoft مجموعة من التكوينات [للوصول إلى الهوية والجهاز](../security/office-365-security/microsoft-365-policies-configurations.md) لضمان قوة عمل آمنة ومنتجة. تتضمن هذه التكوينات استخدام:

- نهج الوصول المشروط Azure AD
- Microsoft Intune نهج توافق الأجهزة وحماية التطبيقات
- نهج مخاطر مستخدم Azure AD Identity Protection
- نهج إضافية لتطبيقات السحابة

فيما يلي مثال على تطبيق هذه الإعدادات والنهج للتحقق من صحة المستخدمين وأجهزتهم وتقييدهم واستخدامهم لتطبيقات الإنتاجية المحلية والسحابية مثل Microsoft Teams.

![تكوينات الوصول إلى الهوية والجهاز للمتطلبات والقيود على المستخدمين وأجهزتهم واستخدامهم للتطبيقات.](../media/tenant-management-overview/tenant-management-device-app-mgmt-golden-config.png)

للوصول إلى الجهاز وإدارة التطبيقات، استخدم التكوينات في هذه المقالات:

- [المتطلبات الأساسية](../security/office-365-security/identity-access-prerequisites.md)
- [نهج الوصول إلى الهوية والجهاز الشائعة](../security/office-365-security/identity-access-policies.md)

## <a name="results-of-step-5"></a>نتائج الخطوة 5

بالنسبة لإدارة الأجهزة والتطبيقات لمستأجر Microsoft 365، حددت إعدادات Intune وسياساته للتحقق من صحة المستخدمين وأجهزتهم واستخدامهم لتطبيقات الإنتاجية المحلية والسحابية وتقييدها.

فيما يلي مثال على مستأجر مع إدارة الأجهزة والتطبيقات في Intune مع تمييز العناصر الجديدة.

![مثال لمستأجر مع إدارة الأجهزة والتطبيقات في Intune.](../media/tenant-management-overview/tenant-management-tenant-build-step5.png)

في هذا الرسم التوضيحي، يحتوي المستأجر على:

- الأجهزة المملوكة للمؤسسة المسجلة في Intune.
- نهج الأجهزة والتطبيقات في Intune للأجهزة المسجلة والشخصية.

## <a name="ongoing-maintenance-for-device-and-app-management"></a>الصيانة المستمرة لإدارة الأجهزة والتطبيقات

على أساس مستمر، قد تحتاج إلى: 

- إدارة تسجيل الجهاز.
- راجع الإعدادات والنهج للحصول على متطلبات الأمان والتطبيقات والأجهزة الإضافية.
