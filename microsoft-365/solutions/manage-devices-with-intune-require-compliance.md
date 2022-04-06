---
title: الخطوة 4. يتطلب أجهزة سليمة ومتوافقة مع Intune
ms.author: bcarter
author: brendacarter
f1.keywords:
- Conditional access policy
- Microsoft Intune
- Intune device management
manager: dougeby
audience: ITPro
description: يمكنك إنشاء نهج وصول شرطي في Azure AD لتطلب أجهزة متوافقة، مع الحفاظ على أمان بيانات الشركة عندما يعمل المستخدمون من أي جهاز في أي موقع.
ms.topic: article
ms.prod: microsoft-365-enterprise
ms.localizationpriority: high
ms.collection:
- Conditional access policy
- Microsoft Intune
- M365-security-compliance
- m365solution-managedevices
- m365solution-scenario
ms.custom: ''
ms.openlocfilehash: 8a953c76a3461b0f6dbf1b3663d5cef41f038371
ms.sourcegitcommit: 23166424125b80b2d615643f394a3c023cba641d
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 01/14/2022
ms.locfileid: "63583747"
---
# <a name="step-4-require-healthy-and-compliant-devices-with-intune"></a>الخطوة 4. يتطلب أجهزة سليمة ومتوافقة مع Intune

يوفر Access الشرطي التحقق الإضافي من حالة الجهاز قبل السماح بالوصول إلى الخدمة. لا يعمل الوصول الشرطي إلا إذا قمت بتحديد الشروط. في [الخطوة 3. إعداد سياسات التوافق،](manage-devices-with-intune-compliance-policies.md) قمت بتعريف سياسات التوافق التي تحدد الحد الأدنى للمتطلبات التي يجب أن يلبيها الجهاز للوصول إلى بيئتك. في هذه المقالة، ستنشئ نهج الوصول الشرطي المطابق في Azure AD لتطلب أجهزة متوافقة. يساعد ذلك على الحفاظ على أمان بيانات الشركة مع منح المستخدمين القدرة على العمل من أي جهاز ومن أي موقع.

بعد إعداد سياسات توافق الجهاز وتعيينها إلى مجموعات المستخدمين، يتيح Intune ل Azure AD معرفة ما إذا كان الجهاز متوافقا أم لا. لاستخدام هذه الحالة كشرط للوصول، يجب العمل مع مسؤول Azure AD لإنشاء قاعدة وصول شرطي لتطلب أجهزة كمبيوتر وأجهزة محمولة متوافقة.


![خطوات لإدارة الأجهزة](../media/devices/intune-mdm-step-3.png#lightbox)

تتضمن مجموعة قواعد الوصول إلى الأجهزة وهوية الصفر الموصى بها هذه القاعدة. راجع [طلب أجهزة كمبيوتر وأجهزة محمولة](../security/office-365-security/identity-access-policies.md#require-compliant-pcs-and-mobile-devices) متوافقة، كما هو موضح أدناه.


[![نهج الوصول إلى الأجهزة وهوية الثقة الصفرية](../media/devices/identity-device-require-compliance.png#lightbox)](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/media/devices/identity-device-require-compliance.png)



تأكد من:
- يمكنك تنسيق مجموعات المستخدمين التي عينتها لنهج التوافق مع مجموعات المستخدمين المعينة لنهج الوصول الشرطي.
- اختبر نهج الوصول الشرطي باستخدام إمكانيات ماذا إذا ووضع التدقيق قبل تعيين نهج الوصول الشرطي بالكامل. يساعدك ذلك على فهم نتائج النهج.
- تعيين فترة سماح تتماشى مع سرية البيانات و/أو التطبيق الذي يتم الوصول إليه. 
- تأكد من أن سياسات التوافق لا تتداخل مع أي متطلبات تنظيمية أو متطلبات توافق أخرى. 
- فهم فحص الجهاز للم فواصل زمنية لنهج التوافق.
- تجنب التعارضات بين سياسات التوافق وملفات تعريف التكوين. فهم النتائج إذا اخترت ذلك.

لاستعلام ملفات تعريف الجهاز في Intune وإصلاحها، بما في ذلك التعارضات بين السياسات، راجع الأسئلة الشائعة والأجوبة باستخدام سياسات الجهاز [وملفات](/mem/intune/configuration/device-profile-troubleshoot) التعريف في Microsoft Intune.

ملاحظة: إذا كنت تريد البدء من خلال طلب أجهزة كمبيوتر متوافقة، وليس أجهزة محمولة، ف راجع طلب أجهزة كمبيوتر [متوافقة (ولكن ليس الهواتف وأجهزة الكمبيوتر اللوحية)](../security/office-365-security/identity-access-policies.md) 

## <a name="next-steps"></a>الخطوات التالية

انتقل إلى الخطوة [5. نشر ملفات تعريف الجهاز في Microsoft Intune](manage-devices-with-intune-configuration-profiles.md)
