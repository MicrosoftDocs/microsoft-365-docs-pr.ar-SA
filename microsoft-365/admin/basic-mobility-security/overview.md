---
title: نظرة عامة على التنقل الأساسي والأمان Microsoft 365
f1.keywords:
- NOCSH
ms.author: kwekua
author: kwekua
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
ms.custom:
- AdminSurgePortfolio
- AdminTemplateSet
search.appverid:
- MET150
description: يمكنك إدارة الأجهزة المحمولة المتصلة بمؤسستك Microsoft 365 وتأمينها من خلال إعداد Basic Mobility and Security واستخدامها.
ms.openlocfilehash: 9a9b3d433408d4ce5225f1a74351d01150744132
ms.sourcegitcommit: 1fa0b15f86470c49dddf0d6de59d553a38ae259b
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 06/03/2022
ms.locfileid: "65863195"
---
# <a name="overview-of-basic-mobility-and-security-for-microsoft-365"></a>نظرة عامة على التنقل الأساسي والأمان Microsoft 365

يمكنك إدارة الأجهزة المحمولة وتأمينها عندما تكون متصلة بمؤسستك Microsoft 365 باستخدام Basic Mobility and Security. تلعب الأجهزة المحمولة مثل الهواتف الذكية والأجهزة اللوحية المستخدمة للوصول إلى البريد الإلكتروني والتقويم وجهات الاتصال والمستندات الخاصة بالعمل دورا مهما في التأكد من أن الموظفين يقومون بعملهم في أي وقت ومن أي مكان. لذلك من المهم أن تساعد في حماية معلومات مؤسستك عندما يستخدم الأشخاص الأجهزة. يمكنك استخدام Basic Mobility and Security لتعيين نهج أمان الجهاز وقواعد الوصول، ومسح الأجهزة المحمولة إذا فقدت أو سرقت.

:::image type="content" source="../../media/basic-mobility-security/bms-3-setup.png" alt-text="التنقل الأساسي وإعداد الأمان.":::

## <a name="what-types-of-devices-can-you-manage"></a>ما هي أنواع الأجهزة التي يمكنك إدارتها؟

يمكنك استخدام Basic Mobility and Security لإدارة العديد من أنواع الأجهزة المحمولة مثل Windows Phone وAndroid iPhone iPad. لإدارة الأجهزة المحمولة التي يستخدمها الأشخاص في مؤسستك، يجب أن يكون لكل شخص ترخيص Microsoft 365 قابل للتطبيق ويجب أن يكون جهازه مسجلا في Basic Mobility and Security.

لمعرفة ما يدعمه Basic Mobility and Security لكل نوع من الأجهزة، راجع [قدرات Basic Mobility and Security](capabilities.md).

## <a name="setup-steps-for-basic-mobility-and-security"></a>خطوات الإعداد للتنقل الأساسي والأمان

يجب على المسؤول العام Microsoft 365 إكمال الخطوات التالية لتنشيط وإعداد Basic Mobility and Security. للحصول على خطوات مفصلة، اتبع الإرشادات الواردة في [إعداد التنقل الأساسي والأمان](set-up.md). 

فيما يلي ملخص للخطوات:

**الخطوة 1:** قم بتنشيط Basic Mobility and Security باتباع الخطوات الواردة في [إعداد Basic Mobility and Security](set-up.md).

**الخطوة 2:** قم بإعداد Basic Mobility and Security، على سبيل المثال، عن طريق إنشاء شهادة APNs لإدارة أجهزة iOS وإضافة سجل نظام أسماء المجالات (DNS) لمجالك لدعم الهواتف Windows.

**الخطوة 3:** إنشاء نهج الجهاز وتطبيقها على مجموعات من المستخدمين. عند القيام بذلك، يحصل المستخدمون على رسالة تسجيل على أجهزتهم، وعندما يكملون التسجيل، يتم تقييد أجهزتهم من خلال النهج التي قمت بإعدادها لهم. لمزيد من المعلومات، راجع [تسجيل جهازك المحمول باستخدام Basic Mobility and Security](enroll-your-mobile-device.md). 

:::image type="content" source="../../media/basic-mobility-security/basic-mobility-microsoft-purview.png" alt-text="إعدادات نهج الأمان والتنقل الأساسية.":::

## <a name="device-management-tasks"></a>مهام إدارة الجهاز

بعد إعداد Basic Mobility and Security وتسجيل المستخدمين لأجهزتهم، يمكنك إدارة الأجهزة أو حظر الوصول أو مسح جهاز، إذا لزم الأمر. لمعرفة المزيد حول بعض مهام إدارة الأجهزة الشائعة، بما في ذلك مكان إكمال المهام، راجع [إدارة الأجهزة المسجلة في إدارة الجهاز الأجهزة المحمولة Microsoft 365](manage-enrolled-devices.md).

## <a name="other-ways-to-manage-devices-and-apps"></a>طرق أخرى لإدارة الأجهزة والتطبيقات

إذا كنت بحاجة فقط إلى إدارة تطبيقات الأجهزة المحمولة (MAM)، ربما للأشخاص الذين يحدثون مشاريع العمل على أجهزتهم الخاصة، يوفر Intune خيارا آخر إلى جانب تسجيل الأجهزة وإدارتها. يسمح لك اشتراك Intune بإعداد نهج MAM باستخدام مدخل Microsoft Azure، حتى لو لم تكن أجهزة الأشخاص مسجلة في Intune. لمزيد من المعلومات، راجع [نظرة عامة على نهج حماية التطبيقات](/mem/intune/apps/app-protection-policy).

## <a name="related-content"></a>المحتويات ذات الصلة

[إعداد Basic Mobility and Security](set-up.md) (article)\
[تسجيل جهازك المحمول باستخدام Basic Mobility and Security](enroll-your-mobile-device.md) (article)\
[إدارة الأجهزة المسجلة في إدارة الجهاز الجوال ل Microsoft 365](manage-enrolled-devices.md) (المقالة)\
[الحصول على تفاصيل حول الأجهزة المدارة بواسطة Basic Mobility and Security](get-details-about-managed-devices.md) (مقالة)