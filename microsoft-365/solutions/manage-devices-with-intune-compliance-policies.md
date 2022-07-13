---
title: الخطوة 3. إعداد نهج التوافق للأجهزة باستخدام Intune
ms.author: bcarter
author: brendacarter
f1.keywords:
- Create compliance policies
- Intune device compliance policy
manager: dougeby
audience: ITPro
description: تعرف على كيفية إنشاء نهج توافق الجهاز التي تحدد الحد الأدنى من متطلبات الجهاز للوصول إلى بيئتك.
ms.topic: article
ms.prod: microsoft-365-enterprise
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
- m365solution-managedevices
- m365solution-scenario
- zerotrust-solution
ms.custom: ''
keywords: ''
ms.openlocfilehash: ae2866d2cabf21616b7aea74220dcf5ce8e4d4eb
ms.sourcegitcommit: 61b22df76e0f81e5ef11c587b129287886151c79
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/12/2022
ms.locfileid: "66750287"
---
# <a name="step-3-set-up-compliance-policies-for-devices-with-intune"></a>الخطوة 3. إعداد نهج التوافق للأجهزة باستخدام Intune

يتيح لك تسجيل الأجهزة في Intune القدرة على تحقيق قدر أكبر من الأمان والتحكم في البيانات في بيئتك. [الخطوة 2. تسجيل الأجهزة في تفاصيل Intune](manage-devices-with-intune-enroll.md) كيفية إنجاز ذلك باستخدام Intune. تتناول هذه المقالة الخطوة التالية، وهي تكوين نهج توافق الجهاز. 

![خطوات إدارة الأجهزة](../media/devices/intune-mdm-step-2.png#lightbox)

تريد التأكد من أن الأجهزة التي تصل إلى تطبيقاتك وبياناتك تلبي الحد الأدنى من المتطلبات، على سبيل المثال، إنها محمية بكلمة مرور أو محمية بواسطة الدبوس ونظام التشغيل محدث. نهج التوافق هي الطريقة لتحديد المتطلبات التي يجب أن تفي بها الأجهزة. تستخدم MEM نهج التوافق هذه لوضع علامة على جهاز على أنه متوافق أو غير متوافق، يتم تمرير هذه الحالة الثنائية إلى Azure AD التي يمكنها استخدام هذه الحالة في قواعد الوصول المشروط للسماح لجهاز أو منعه من الوصول إلى الموارد. 

## <a name="configuring-device-compliance-policies"></a>تكوين نهج توافق الجهاز

وينسق هذا التوجيه بإحكام مع [نهج الهوية ثقة معدومة والوصول إلى الجهاز](../security/office-365-security/microsoft-365-policies-configurations.md) الموصى بها.

يسلط هذا الرسم التوضيحي الضوء على مكان ملاءمة عمل تحديد نهج التوافق مع مجموعة النهج العامة ثقة معدومة الموصى بها. 

[![ثقة معدومة نهج الوصول إلى الهوية والجهاز](../media/devices/identity-device-define-compliance.png#lightbox)](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/media/devices/identity-device-define-compliance.png)

في هذا التوضيح، يعد تحديد نهج توافق الأجهزة تبعية لتحقيق المستوى الموصى به من الحماية داخل إطار عمل ثقة معدومة. 

لتكوين نهج توافق الجهاز، استخدم الإرشادات والإعدادات الموصى بها المحددة في [ثقة معدومة نهج الوصول إلى الأجهزة والهوية](../security/office-365-security/microsoft-365-policies-configurations.md). يرتبط الجدول أدناه مباشرة بإرشادات تكوين هذه النهج في Intune، بما في ذلك الإعدادات الموصى بها لكل نظام أساسي.


|السياسات |معلومات إضافية  |الترخيص |
|---------|---------|---------|
|[تحديد نهج توافق الجهاز ](../security/office-365-security/identity-access-policies.md#define-device-compliance-policies)   |  نهج واحد لكل نظام أساسي       |  Microsoft 365 E3 أو E5       |
|  |         |         |

## <a name="next-steps"></a>الخطوات التالية

انتقل إلى [الخطوة 4. طلب أجهزة سليمة ومتوافقة](manage-devices-with-intune-require-compliance.md) للحصول على إرشادات حول كيفية إنشاء قاعدة الوصول المشروط في Azure AD.