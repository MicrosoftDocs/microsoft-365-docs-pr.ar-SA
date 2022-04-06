---
title: الخطوة 1. تنفيذ نهج حماية التطبيقات
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
description: تكوين حماية تطبيقات الأجهزة المحمولة باستخدام نهج حماية التطبيقات (APP) لمنع نسخ بيانات الشركة المحددة ولصقها في تطبيقات أخرى.
ms.prod: microsoft-365-enterprise
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
- m365solution-managedevices
- m365solution-scenario
ms.custom: ''
keywords: ''
ms.openlocfilehash: e421a62d3b1fa60df7a64a5b9a94e6e46b0a139f
ms.sourcegitcommit: a06bb81fbd727a790a8fe6a3746b8a3cf62a6b24
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/05/2022
ms.locfileid: "64651500"
---
# <a name="step-1-implement-app-protection-policies"></a>الخطوة 1. تنفيذ نهج حماية التطبيقات

تحمي نهج Intune App Protection (APP)، التي يشار إليها أحيانا باسم إدارة تطبيقات الأجهزة المحمولة (MAM)، بيانات الشركة حتى إذا لم تتم إدارة الجهاز نفسه. يسمح لك هذا بتمكين أجهزة (BYO) الشخصية الخاصة بك في العمل حيث قد يحجم المستخدمون عن "تسجيل" أجهزتهم في الإدارة. تضمن نهج حماية التطبيقات عدم إمكانية نسخ بيانات الشركة في التطبيقات التي تحددها ولصقها في تطبيقات أخرى على الجهاز.

![خطوات إنشاء نهج حماية التطبيقات](../media/devices/intune-app-steps.png#lightbox)

في هذا الرسم التوضيحي:
- باستخدام APP، ينشئ Intune جدارا بين بيانات مؤسستك والبيانات الشخصية. تحدد نهج حماية التطبيقات التطبيقات المسموح لها بالوصول إلى بياناتك.
- إذا قام مستخدم بتسجيل الدخول باستخدام بيانات اعتماد المؤسسة الخاصة به، يطبق Intune نهجا في طبقة التطبيق لمنع نسخ بيانات مؤسستك ولصقها في التطبيقات الشخصية ولطلب الوصول إلى هذه البيانات.
- بعد إنشاء نهج حماية التطبيقات، يمكنك فرض حماية البيانات باستخدام نهج الوصول المشروط. 

هذا التكوين يزيد بشكل كبير من وضع الأمان الخاص بك مع أي تأثير تقريبا على تجربة المستخدم.  يمكن للموظفين استخدام تطبيقات مثل Office Microsoft Teams، التي يعرفونها ويحبونها، بينما في الوقت نفسه يمكن لمؤسستك حماية البيانات المضمنة داخل التطبيقات والأجهزة.

إذا كان لديك تطبيقات خط العمل المخصصة التي تحتاج إلى حماية، يمكنك حاليا استخدام أداة التفاف التطبيق لتمكين APP مع هذه التطبيقات. أو، يمكنك التكامل باستخدام Intune App SDK. عندما يكون لتطبيقك نهج حماية تطبيق مطبقة عليه، يمكن إدارته بواسطة Intune ويتم التعرف عليه من قبل Intune كتطبيق مدار. لمزيد من المعلومات حول حماية تطبيقات خط العمل باستخدام Intune، راجع [إعداد التطبيقات لإدارة تطبيقات الأجهزة المحمولة باستخدام Microsoft Intune](/mem/intune/developer/apps-prepare-mobile-application-management).

## <a name="configuring-mobile-app-protection"></a>تكوين حماية تطبيق الأجهزة المحمولة

وينسق هذا التوجيه بإحكام مع [نهج الهوية ثقة معدومة والوصول إلى الجهاز](../security/office-365-security/microsoft-365-policies-configurations.md) الموصى بها. بعد إنشاء نهج حماية التطبيقات الأجهزة المحمولة في Intune، اعمل مع فريق الهوية لتكوين نهج الوصول المشروط في Azure AD الذي يفرض حماية تطبيق الأجهزة المحمولة. 

يميز هذا الرسم التوضيحي النهجين (كما هو موضح في الجدول أسفل الرسم التوضيحي).

[![ثقة معدومة نهج الوصول إلى الهوية والجهاز](../media/devices/identity-device-starting-point.png#lightbox)](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/media/devices/identity-device-starting-point.png)

لتكوين هذه النهج، استخدم الإرشادات والإعدادات الموصى بها المحددة في [ثقة معدومة نهج الوصول إلى الهوية والجهاز](../security/office-365-security/microsoft-365-policies-configurations.md). يرتبط الجدول أدناه مباشرة بإرشادات تكوين هذه النهج في Intune وAzure AD.


|خطوه  |السياسات  |معلومات إضافية  |الترخيص  |
|---------|---------|---------|---------|
|1   |  [تطبيق حماية البيانات لنهج حماية التطبيقات (APP)](../security/office-365-security/identity-access-policies.md#apply-app-data-protection-policies)       | نهج حماية تطبيق Intune واحد لكل نظام أساسي (Windows وiOS/iPadOS وAndroid).        | Microsoft 365 E3 أو E5        |
|2     | [طلب التطبيقات المعتمدة وحماية التطبيقات ](../security/office-365-security/identity-access-policies.md#require-approved-apps-and-app-protection)       |  يفرض حماية تطبيقات الأجهزة المحمولة للهواتف وأجهزة الكمبيوتر اللوحية باستخدام iOS أو iPadOS أو Android.   |  Microsoft 365 E3 أو E5       |
| | | | |

## <a name="next-steps"></a>الخطوات التالية

انتقل إلى [الخطوة 2. تسجيل الأجهزة في Intune](manage-devices-with-intune-enroll.md). 