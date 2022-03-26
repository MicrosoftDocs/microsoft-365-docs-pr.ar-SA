---
title: الخطوة 3. إعداد سياسات التوافق للأجهزة التي تعمل باستخدام Intune
ms.author: bcarter
author: brendacarter
f1.keywords:
- Create compliance policies
- Intune device compliance policy
manager: dougeby
audience: ITPro
description: تعرف على كيفية إنشاء سياسات توافق الجهاز التي تحدد الحد الأدنى من المتطلبات لجهاز للوصول إلى بيئتك.
ms.topic: article
ms.prod: microsoft-365-enterprise
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
- m365solution-managedevices
- m365solution-scenario
ms.custom: ''
keywords: ''
ms.openlocfilehash: 7e55ad6bf1d1cb7d95e43cb23b9c74decc8548df
ms.sourcegitcommit: 23166424125b80b2d615643f394a3c023cba641d
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 01/14/2022
ms.locfileid: "63570902"
---
# <a name="step-3-set-up-compliance-policies-for-devices-with-intune"></a>الخطوة 3. إعداد سياسات التوافق للأجهزة التي تعمل باستخدام Intune

يوفر لك تسجيل الأجهزة في الإدارة القدرة على تحقيق المزيد من الأمان والتحكم في البيانات في بيئتك. [الخطوة 2. يمكنك تسجيل الأجهزة في تفاصيل](manage-devices-with-intune-enroll.md) الإدارة حول كيفية تنفيذ ذلك باستخدام Intune و Autopilot. تغطي هذه المقالة الخطوة التالية، وهي تكوين سياسات توافق الأجهزة. 

![خطوات إدارة الأجهزة](../media/devices/intune-mdm-step-2.png#lightbox)

أنت تريد التأكد من أن الأجهزة التي تصل إلى تطبيقاتك وبياناتك تلبي الحد الأدنى من المتطلبات، على سبيل المثال، إنها كلمة مرور أو محمية بدبوس ونظام التشغيل مقتر. إن سياسات التوافق هي الطريقة لتحديد المتطلبات التي يجب أن تلبيها الأجهزة. تستخدم MEM سياسات التوافق هذه لتوضع علامة على الجهاز كمتوافق أو غير متوافق يتم تمرير هذه الحالة الثنائية إلى Azure AD الذي يمكنه استخدام هذه الحالة في قواعد الوصول الشرطي للسماح لجهاز بالوصول إلى الموارد أو منعه. 

## <a name="configuring-device-compliance-policies"></a>تكوين سياسات توافق الأجهزة

يتم تنسيق هذه الإرشادات بشكل كبير مع هوية الصفر الموثوق بها ونهج [الوصول إلى الجهاز الموصى بها](../security/office-365-security/microsoft-365-policies-configurations.md).

يوضح هذا الرسم التوضيحي مكان توافق عمل تحديد نهج التوافق مع مجموعة النهج الموصى بها من الصفر. 

[![نهج الوصول إلى الأجهزة وهوية الثقة الصفرية](../media/devices/identity-device-define-compliance.png#lightbox)](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/media/devices/identity-device-define-compliance.png)

في هذا الرسم التوضيحي، فإن تعريف سياسات توافق الأجهزة هو تبعية لتحقيق مستوى الحماية الموصى به ضمن إطار عمل الثقة الصفرية. 

لتكوين سياسات توافق الأجهزة، استخدم الإرشادات والإعدادات الموصى بها والموصوفة في هوية الصفر الثقة ونهج [الوصول إلى الجهاز](../security/office-365-security/microsoft-365-policies-configurations.md). يرتبط الجدول أدناه مباشرة بتعليمات تكوين هذه السياسات في Intune، بما في ذلك الإعدادات الموصى بها لكل نظام أساسي.


|السياسات |معلومات إضافية  |الترخيص |
|---------|---------|---------|
|[تعريف سياسات توافق الأجهزة ](../security/office-365-security/identity-access-policies.md#define-device-compliance-policies)   |  نهج واحد لكل نظام أساسي       |  Microsoft 365 E3 أو E5       |
|  |         |         |

## <a name="next-steps"></a>الخطوات التالية

انتقل إلى [الخطوة 4. يتطلب أجهزة سليمة ومتوافقة](manage-devices-with-intune-require-compliance.md) للحصول على إرشادات حول كيفية إنشاء قاعدة الوصول الشرطي في Azure AD.