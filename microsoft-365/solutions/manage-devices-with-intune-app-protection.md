---
title: الخطوة 1. تنفيذ سياسات حماية التطبيق
ms.author: bcarter
author: brendacarter
f1.keywords:
- Intune App Protection policies
- APP
- mobile application management
- MAM
- set up mobile ap protection
manager: dougeby
audience: ITPro
ms.topic: article
description: تكوين حماية تطبيق الأجهزة المحمولة باستخدام سياسات حماية التطبيقات (APP) لمنع نسخ بيانات محددة خاصة بالشركة ولصقها في تطبيقات أخرى.
ms.prod: microsoft-365-enterprise
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
- m365solution-managedevices
- m365solution-scenario
ms.custom: ''
keywords: ''
ms.openlocfilehash: 4535e4a05ac8408e57c767999de66c39a4bf0274
ms.sourcegitcommit: 23166424125b80b2d615643f394a3c023cba641d
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 01/14/2022
ms.locfileid: "63575152"
---
# <a name="step-1-implement-app-protection-policies"></a>الخطوة 1. تنفيذ سياسات حماية التطبيق

تحمي سياسات Intune App Protection (APP)، التي يشار إليها أحيانا ب إدارة تطبيقات الأجهزة المحمولة (MAM)، بيانات الشركة حتى لو لم يكن الجهاز نفسه مدارا. يسمح لك ذلك بتمكين الأجهزة الشخصية والإحضارية الخاصة بك في العمل حيث قد يكون المستخدمون غير راغبين في "تسجيل" أجهزتهم في الإدارة. تضمن سياسات حماية التطبيقات عدم نسخ بيانات الشركة في التطبيقات التي تحددها ولصقها في تطبيقات أخرى على الجهاز.

![خطوات إنشاء سياسات حماية التطبيق](../media/devices/intune-app-steps.png#lightbox)

في هذا الرسم التوضيحي:
- باستخدام APP، ينشئ Intune جدارا بين بيانات المؤسسة والبيانات الشخصية. تحدد سياسات حماية التطبيق التطبيقات المسموح لها بالوصول إلى بياناتك.
- إذا قام أحد المستخدمين تسجيل الدخول باستخدام بيانات اعتماد المؤسسة الخاصة به، يطبق Intune نهج على طبقة التطبيق لمنع نسخ بيانات المؤسسة ولصقها للتطبيقات الشخصية ولمتطلب الوصول إلى رمز PIN لهذه البيانات.
- بعد إنشاء نهج حماية التطبيق، يجب فرض حماية البيانات باستخدام نهج وصول شرطي. 

يزيد هذا التكوين إلى حد كبير من وضع الأمان بدون أي تأثير تقريبا على تجربة المستخدم.  يمكن للموظفين استخدام تطبيقات مثل Office Microsoft Teams، يعرفونها ويحبونها، وفي الوقت نفسه يمكن لمنظمتك حماية البيانات المضمنة في التطبيقات والأجهزة.

إذا كان لديك تطبيقات مخصصة لخط العمل تحتاج إلى حماية، يمكنك حاليا استخدام أداة التفاف التطبيق لتمكين التطبيق مع هذه التطبيقات. أو، يمكنك التكامل باستخدام Intune App SDK. عندما يتم تطبيق سياسات حماية التطبيق عليه، يمكن إدارته بواسطة Intune ويتعرف عليه Intune ك تطبيق مدار. لمزيد من المعلومات حول حماية تطبيقات خط العمل باستخدام Intune، راجع إعداد التطبيقات لإدارة تطبيقات الأجهزة المحمولة [باستخدام Microsoft Intune](/mem/intune/developer/apps-prepare-mobile-application-management).

## <a name="configuring-mobile-app-protection"></a>تكوين حماية تطبيق الأجهزة المحمولة

يتم تنسيق هذه الإرشادات بشكل كبير مع هوية الصفر الموثوق بها ونهج [الوصول إلى الجهاز الموصى بها](../security/office-365-security/microsoft-365-policies-configurations.md). بعد إنشاء نهج حماية تطبيق الأجهزة المحمولة في Intune، اعمل مع فريق الهوية لتكوين نهج الوصول الشرطي في Azure AD الذي يفرض حماية تطبيق الأجهزة المحمولة. 

يسلط هذا الرسم التوضيحي الضوء على المنهجين (كما هو موضح في الجدول أسفل الرسم التوضيحي).

[![نهج الوصول إلى الأجهزة وهوية الثقة الصفرية](../media/devices/identity-device-starting-point.png#lightbox)](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/media/devices/identity-device-starting-point.png)

لتكوين هذه النهج، استخدم الإرشادات والإعدادات الموصى بها والموصوفة في الهوية الصفرية ونهج [الوصول إلى الجهاز](../security/office-365-security/microsoft-365-policies-configurations.md). يرتبط الجدول أدناه مباشرة بتعليمات تكوين هذه السياسات في Intune و Azure AD.


|الخطوة  |السياسات  |معلومات إضافية  |الترخيص  |
|---------|---------|---------|---------|
|1   |  [تطبيق حماية بيانات "سياسات حماية التطبيقات" (APP)](../security/office-365-security/identity-access-policies.md#apply-app-data-protection-policies)       | نهج حماية تطبيق Intune واحد لكل نظام أساسي (Windows وiOS/iPadOS وAndroid).        | Microsoft 365 E3 أو E5        |
|2     | [يتطلب التطبيقات المعتمدة وحماية التطبيق ](../security/office-365-security/identity-access-policies.md#require-approved-apps-and-app-protection)       |  يفرض حماية تطبيق الأجهزة المحمولة للهواتف وأجهزة الكمبيوتر اللوحية باستخدام iOS أو iPadOS أو Android.   |  Microsoft 365 E3 أو E5       |
| | | | |

## <a name="next-steps"></a>الخطوات التالية

انتقل إلى [الخطوة 2. تسجيل الأجهزة في الإدارة باستخدام Intune](manage-devices-with-intune-enroll.md). 