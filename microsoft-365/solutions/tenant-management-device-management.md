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
description: نشر الخيار الصحيح لإدارة الأجهزة والتطبيقات Microsoft 365 المستأجرين.
ms.openlocfilehash: 09fd96977fbde0f546049d24b1705d27b4c92080
ms.sourcegitcommit: 22cae7ec541268d519d45518c32f22bf5811aec1
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 02/10/2022
ms.locfileid: "63570142"
---
# <a name="step-5-device-and-app-management-for-your-microsoft-365-for-enterprise-tenants"></a>الخطوة 5. إدارة الأجهزة والتطبيقات Microsoft 365 لمستأجري المؤسسات

Microsoft 365 للمؤسسات ميزات للمساعدة على إدارة الأجهزة واستخدام التطبيقات على هذه الأجهزة داخل مؤسستك باستخدام إدارة أجهزة المحمول (MDM) وإدارة تطبيقات الأجهزة المحمولة (MAM). يمكنك إدارة أجهزة iOS وAndroid و macOS Windows لحماية الوصول إلى موارد مؤسستك، بما في ذلك بياناتك. على سبيل المثال، يمكنك منع إرسال رسائل البريد الإلكتروني إلى أشخاص من خارج مؤسستك أو عزل بيانات المؤسسة عن البيانات الشخصية على الأجهزة الشخصية الخاصة بالعامل.

فيما يلي مثال للتحقق من صحة المستخدمين وأجهزتهم وإدارتهم واستخدامهم لتطبيقات الإنتاجية المحلية والسحابية مثل Microsoft Teams.

![التحقق من صحة المستخدمين والأجهزة والتطبيقات وإدارتها.](../media/tenant-management-overview/tenant-management-device-app-mgmt.png)

لمساعدتك على حماية موارد مؤسستك وحمايتها، تتضمن Microsoft 365 للمؤسسات ميزات للمساعدة في إدارة الأجهزة والوصول إلى التطبيقات. هناك خياران لإدارة الأجهزة:

- Microsoft Intune، وهو حل شامل لإدارة الأجهزة والتطبيقات للمؤسسات.
- التنقل والأمان الأساسي، وهي مجموعة فرعية من خدمات Intune المضمنة مع Microsoft 365 الأساسية لإدارة الأجهزة في مؤسستك. لمزيد من المعلومات، راجع [إمكانات التنقل والأمان الأساسيين](../admin/basic-mobility-security/capabilities.md).

إذا كان لديك Microsoft 365 E3 أو E5، يجب استخدام Intune.

## <a name="microsoft-intune"></a>Microsoft Intune

يمكنك استخدام [Microsoft Intune](/mem/intune/fundamentals/planning-guide) لإدارة الوصول إلى مؤسستك باستخدام MDM أو MAM. إن MDM هي عندما "يسجل" المستخدمون أجهزتهم في Intune. بعد تسجيل الجهاز، يكون جهازا مدارا ويمكنه تلقي سياسات المؤسسة وقواعدها وإعداداتها. على سبيل المثال، يمكنك تثبيت تطبيقات معينة وإنشاء نهج كلمة مرور وتثبيت اتصال VPN والمزيد.

قد لا يرغب المستخدمون الذين لديهم أجهزتهم الشخصية في تسجيل أجهزتهم أو إدارتها بواسطة Intune ونهج مؤسستك. ولكنك لا تزال بحاجة إلى حماية موارد المؤسسة وبياناتها. في هذا السيناريو، يمكنك حماية تطبيقاتك باستخدام MAM. على سبيل المثال، يمكنك استخدام نهج MAM يتطلب من المستخدم إدخال رمز PIN عند SharePoint على الجهاز.

ستحدد أيضا كيفية إدارة الأجهزة الشخصية والأجهزة المملوكة لمنظمتك. قد ترغب في التعامل مع الأجهزة بشكل مختلف، استنادا إلى استخداماتها.

## <a name="identity-and-device-access-configurations"></a>تكوينات الوصول إلى الأجهزة والهوية

توفر Microsoft مجموعة من التكوينات للوصول إلى الهوية [والجهاز لضمان توفير](../security/office-365-security/microsoft-365-policies-configurations.md) قوة عمل آمنة ومنتجة. تتضمن هذه التكوينات استخدام:

- سياسات الوصول الشرطي في Azure AD
- Microsoft Intune توافق الأجهزة ونهج حماية التطبيقات
- سياسات مخاطر مستخدم Azure AD Identity Protection
- سياسات إضافية لتطبيقات السحابة

فيما يلي مثال لتطبيق هذه الإعدادات والسياسات للتحقق من صحة المستخدمين وأجهزتهم وتقييدهم واستخدامهم لتطبيقات الإنتاجية المحلية وتطبيقات الإنتاجية السحابية مثل Microsoft Teams.

![تكوينات الوصول إلى الأجهزة والهوية للمتطلبات والقيود المفروضة على المستخدمين وأجهزتهم واستخدامهم للتطبيقات.](../media/tenant-management-overview/tenant-management-device-app-mgmt-golden-config.png)

للوصول إلى الأجهزة وإدارة التطبيقات، استخدم التكوينات في المقالات التالية:

- [المتطلبات الأساسية](../security/office-365-security/identity-access-prerequisites.md)
- [ونهج الوصول إلى الأجهزة والهوية الشائعة](../security/office-365-security/identity-access-policies.md)

## <a name="results-of-step-5"></a>نتائج الخطوة 5

لإدارة الأجهزة والتطبيقات لمستأجر Microsoft 365 الخاص بك، لقد حددت إعدادات ونهج Intune للتحقق من صحة المستخدمين وأجهزتهم واستخدامهم لتطبيقات الإنتاجية المحلية والسحابية وتقييدها.

فيما يلي مثال لمستأجر مع إدارة أجهزة Intune والتطبيقات مع تمييز العناصر الجديدة.

![مثال لمستأجر مع جهاز Intune وإدارة التطبيق.](../media/tenant-management-overview/tenant-management-tenant-build-step5.png)

في هذا الرسم التوضيحي، يكون للمستأجر:

- الأجهزة المملوكة لمنظمه مسجله في Intune.
- جهاز Intune ونهج التطبيق للأجهزة الشخصية والمسجلة.

## <a name="ongoing-maintenance-for-device-and-app-management"></a>الصيانة المستمرة لإدارة الأجهزة والتطبيقات

بشكل مستمر، قد تحتاج إلى: 

- إدارة تسجيل الجهاز.
- راجع الإعدادات والسياسات لتطبيقات وأجهزة ومتطلبات أمان إضافية.