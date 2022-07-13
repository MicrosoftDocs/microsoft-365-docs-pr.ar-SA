---
title: الخطوة 4. طلب أجهزة سليمة ومتوافقة مع Intune
ms.author: bcarter
author: brendacarter
f1.keywords:
- Conditional access policy
- Microsoft Intune
- Intune device management
manager: dougeby
audience: ITPro
description: إنشاء نهج وصول مشروط في Azure AD لطلب أجهزة متوافقة، مع الحفاظ على أمان بيانات الشركة عندما يعمل المستخدمون من أي جهاز في أي موقع.
ms.topic: article
ms.prod: microsoft-365-enterprise
ms.localizationpriority: high
ms.collection:
- Conditional access policy
- Microsoft Intune
- M365-security-compliance
- m365solution-managedevices
- m365solution-scenario
- zerotrust-solution
ms.custom: ''
ms.openlocfilehash: 61191da794c065a46d709d443982849ec4c4d3e3
ms.sourcegitcommit: 61b22df76e0f81e5ef11c587b129287886151c79
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/12/2022
ms.locfileid: "66747934"
---
# <a name="step-4-require-healthy-and-compliant-devices-with-intune"></a>الخطوة 4. طلب أجهزة سليمة ومتوافقة مع Intune

يوفر الوصول المشروط التحقق الإضافي من حالة الجهاز قبل السماح بالوصول إلى خدمة. لا يعمل الوصول المشروط إلا إذا حددت شروطا. في [الخطوة 3. إعداد نهج التوافق](manage-devices-with-intune-compliance-policies.md)، قمت بتعريف نهج التوافق التي تحدد الحد الأدنى من المتطلبات التي يجب على الجهاز تلبيتها للوصول إلى بيئتك. في هذه المقالة، ستقوم بإنشاء نهج الوصول المشروط المطابق في Azure AD لطلب أجهزة متوافقة. يساعد ذلك على الحفاظ على أمان بيانات شركتك مع منح المستخدمين القدرة على العمل من أي جهاز ومن أي موقع.

بعد إعداد نهج توافق الجهاز وتعيينها إلى مجموعات المستخدمين، يتيح Intune Azure AD معرفة ما إذا كان الجهاز متوافقا أم لا. لاستخدام هذه الحالة كشرط للوصول، يجب عليك العمل مع مسؤول Azure AD لإنشاء قاعدة وصول مشروط لطلب أجهزة كمبيوتر وأجهزة محمولة متوافقة.


![خطوات لإدارة الأجهزة](../media/devices/intune-mdm-step-3.png#lightbox)

تتضمن مجموعة قواعد الوصول إلى ثقة معدومة والهوية الموصى بها هذه القاعدة. راجع [المطالبة بأجهزة الكمبيوتر الشخصية والأجهزة المحمولة المتوافقة](../security/office-365-security/identity-access-policies.md#require-compliant-pcs-and-mobile-devices)، كما هو موضح أدناه.


[![ثقة معدومة نهج الوصول إلى الهوية والجهاز](../media/devices/identity-device-require-compliance.png#lightbox)](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/media/devices/identity-device-require-compliance.png)



تأكد من:
- قم بتنسيق مجموعات المستخدمين التي عينتها لنهج التوافق الخاصة بك مع مجموعات المستخدمين المعينة لنهج الوصول المشروط.
- اختبر نهج الوصول المشروط باستخدام قدرات "ماذا لو" و"وضع التدقيق" قبل تعيين نهج الوصول المشروط بشكل كامل. يساعدك هذا على فهم نتائج النهج.
- تعيين فترة سماح تتماشى مع سرية البيانات و/أو التطبيق الذي يتم الوصول إليه. 
- تأكد من أن نهج التوافق لا تتداخل مع أي متطلبات تنظيمية أو متطلبات توافق أخرى. 
- فهم فواصل إيداع الجهاز لنهج التوافق.
- تجنب التعارضات بين نهج التوافق وملفات تعريف التكوين. فهم النتائج إذا اخترت ذلك.

لاستكشاف أخطاء ملفات تعريف الأجهزة وإصلاحها في Intune، بما في ذلك التعارضات بين النهج، راجع [الأسئلة الشائعة والأجوبة باستخدام نهج الجهاز وملفات التعريف في Microsoft Intune](/mem/intune/configuration/device-profile-troubleshoot).

ملاحظة: إذا كنت تريد البدء بطلب أجهزة كمبيوتر متوافقة، وليس أجهزة محمولة، فراجع ["طلب أجهزة الكمبيوتر المتوافقة" (ولكن ليس الهواتف وأجهزة الكمبيوتر اللوحية)](../security/office-365-security/identity-access-policies.md) 

## <a name="next-steps"></a>الخطوات التالية

انتقل إلى الخطوة [5. نشر ملفات تعريف الأجهزة في Microsoft Intune](manage-devices-with-intune-configuration-profiles.md)
