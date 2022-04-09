---
title: الخطوة 5. نشر ملفات تعريف الأجهزة في Microsoft Intune
ms.author: bcarter
author: brendacarter
f1.keywords:
- configuration profiles
- Windows security baselines for Intune
- customize configuration profiles
manager: dougeby
audience: ITPro
description: ابدأ باستخدام ملفات تعريف التكوين لفرض إعدادات آمنة على الأجهزة باستخدام Intune لانتقال عناصر التحكم الأمنية هذه إلى السحابة.
ms.topic: article
ms.prod: microsoft-365-enterprise
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
- m365solution-managedevices
- m365solution-scenario
ms.custom: ''
keywords: ''
ms.openlocfilehash: fe137e626d5199f1709504d025411586965ae9fd
ms.sourcegitcommit: 6fefc15dd78139316597083b702286097d45d4dd
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/09/2022
ms.locfileid: "64737426"
---
# <a name="step-5-deploy-device-profiles-in-microsoft-intune"></a>الخطوة 5. نشر ملفات تعريف الأجهزة في Microsoft Intune

تتضمن Microsoft Intune الإعدادات والميزات التي يمكنك تمكينها أو تعطيلها على أجهزة مختلفة داخل مؤسستك. تتم إضافة هذه الإعدادات والميزات إلى "ملفات تعريف التكوين". يمكنك إنشاء ملفات تعريف للأجهزة المختلفة والأنظمة الأساسية المختلفة، بما في ذلك iOS/iPadOS ومسؤول جهاز Android وAndroid Enterprise Windows. ثم استخدم Intune لتطبيق ملف التعريف أو "تعيينه" إلى الأجهزة.

توفر هذه المقالة إرشادات حول بدء استخدام ملفات تعريف التكوين. 


![خطوات لإدارة الأجهزة](../media/devices/intune-mdm-step-4.png#lightbox)

تمنحك ملفات تعريف التكوين القدرة على تكوين حماية مهمة ودمج الأجهزة في التوافق حتى يتمكنوا من الوصول إلى مواردك. في السابق، تم تكوين هذه الأنواع من تغييرات التكوين باستخدام إعدادات نهج المجموعة في خدمات مجال Active Directory. تتضمن استراتيجية الأمان الحديثة نقل عناصر التحكم الأمنية إلى السحابة حيث لا يعتمد فرض عناصر التحكم هذه على الموارد المحلية والوصول. Intune ملفات تعريف التكوين هي طريقة نقل عناصر التحكم الأمنية هذه إلى السحابة. 

لإعطائك فكرة عن نوع ملفات تعريف التكوين التي يمكنك إنشاؤها، راجع [تطبيق الميزات والإعدادات على أجهزتك باستخدام ملفات تعريف الجهاز في Microsoft Intune](/mem/intune/configuration/device-profiles).

## <a name="deploy-windows-security-baselines-for-intune"></a>نشر أساسات الأمان Windows Intune

كنقطة بداية، إذا كنت تريد محاذاة تكوينات جهازك إلى خطوط أمان Microsoft الأساسية، نوصي بخطوط أساس الأمان داخل Microsoft Endpoint Manager. تتمثل ميزة هذا النهج في إمكانية الاعتماد على Microsoft لإبقاء الخطوط الأساسية محدثة مع إصدار Windows 10 و11 ميزة. 

لنشر أساسات الأمان Windows Intune، متوفرة Windows 10 Windows 11. راجع [استخدام أساسيات الأمان لتكوين أجهزة Windows في Intune](/mem/intune/protect/security-baselines) للتعرف على الخطوط الأساسية المتوفرة.

في الوقت الحالي، ما عليك سوى نشر أساس أمان MDM الأكثر ملاءمة. راجع [إدارة ملفات تعريف أساس الأمان في Microsoft Intune ](/mem/intune/protect/security-baselines-configure)لإنشاء ملف التعريف واختيار إصدار الأساس.

في وقت لاحق، عند إعداد Pertahanan Microsoft untuk Titik Akhir والاتصال Intune، قم بنشر خطوط الأساس Defender لنقطة النهاية. يتناول هذا الموضوع في المقالة التالية في هذه السلسلة: [الخطوة 6. مراقبة مخاطر الجهاز والامتثال لأساسيات الأمان](manage-devices-with-intune-monitor-risk.md).

من المهم أن نفهم أن خطوط الأمان الأساسية هذه ليست متوافقة مع CIS أو NIST ولكنها تعكس توصياتها بشكل وثيق. لمزيد من المعلومات، راجع [هل Intune أسس الأمان CIS أو NIST متوافقة؟](https://docs.microsoft.com/mem/intune/protect/security-baselines#are-the-intune-security-baselines-cis-or-nist-compliant)

## <a name="customize-configuration-profiles-for-your-organization"></a>تخصيص ملفات تعريف التكوين لمؤسستك

بالإضافة إلى نشر الخطوط الأساسية التي تم تكوينها مسبقا، تقوم العديد من المؤسسات على نطاق المؤسسة بتنفيذ ملفات تعريف التكوين لمزيد من التحكم الدقيق. يساعد هذا التكوين على تقليل الاعتماد على نهج المجموعة العناصر في بيئة Active Directory محلي ونقل عناصر التحكم في الأمان إلى السحابة. 

يمكن تجميع العديد من الإعدادات التي يمكنك تكوينها باستخدام ملفات تعريف التكوين في أربع فئات، كما هو موضح أدناه.

![Intune فئات ملف تعريف الجهاز](../media/devices/intune-device-profile-categories.png#lightbox)

يصف الجدول التالي الرسم التوضيحي.


|الفئة |الوصف |امثله  |
|---------|---------|---------|
|ميزات الجهاز     | التحكم في الميزات على الجهاز. تنطبق هذه الفئة فقط على أجهزة iOS/iPadOS وmacOS.        | Airprint، والإعلامات، ورسائل شاشة التأمين        |
|قيود الجهاز     | التحكم في الأمان والأجهزة ومشاركة البيانات والمزيد من الإعدادات على الأجهزة        | طلب رقم PIN وتشفير البيانات        |
|تكوين الوصول     |  تكوين جهاز للوصول إلى موارد مؤسستك        | ملفات تعريف البريد الإلكتروني وملفات تعريف VPN وإعدادات Wi-Fi والشهادات        |
|المخصصه     | تعيين تكوين مخصص أو تنفيذ إجراءات التكوين المخصصة       | تعيين إعدادات الشركة المصنعة للمعدات الأصلية، وتنفيذ البرامج النصية PowerShell        |
|    |         |         |

عند تخصيص ملفات تعريف التكوين لمؤسستك، استخدم الإرشادات التالية:
- تبسيط استراتيجية حوكمة الأمان الخاصة بك عن طريق الحفاظ على العدد الإجمالي من السياسات صغيرة.
- يمكنك تجميع الإعدادات في الفئات المذكورة أعلاه، أو الفئات المنطقية لمؤسستك.
- عند نقل عناصر التحكم في الأمان من كائنات نهج المجموعة (GPO) إلى ملفات تعريف التكوين Intune، ضع في اعتبارك ما إذا كانت الإعدادات التي تم تكوينها بواسطة كل عنصر نهج مجموعة لا تزال ذات صلة وتحتاج إلى المساهمة في استراتيجية أمان السحابة العامة. يوفر الوصول المشروط والعديد من النهج التي يمكن تكوينها عبر الخدمات السحابية، بما في ذلك Intune، حماية أكثر تطورا مما يمكن تكوينه في بيئة محلية حيث تم تصميم عناصر نهج المجموعة المخصصة في الأصل.
- استخدم نهج المجموعة Analytics لمقارنة إعدادات عنصر نهج المجموعة الحالية وتعيينها إلى قدرات داخل Microsoft Endpoint Manager. راجع [تحليل عناصر نهج المجموعة المحلية (GPO) باستخدام تحليلات نهج المجموعة](/mem/intune/configuration/group-policy-analytics) في Microsoft Endpoint Manager.
- عند استخدام ملفات تعريف التكوين المخصصة، تأكد من استخدام الإرشادات هنا: [إنشاء ملف تعريف مع إعدادات مخصصة في Intune](/mem/intune/configuration/custom-settings-configure).

## <a name="additional-resources"></a>موارد إضافية

إذا لم تكن متأكدا من مكان البدء بملفات تعريف الأجهزة، يمكن أن يساعدك ما يلي:

- [سيناريوهات موجهة](/mem/intune/fundamentals/guided-scenarios-overview) 
- [أساسيات الأمان](/mem/intune/protect/security-baselines)

إذا كانت بيئتك تتضمن عناصر نهج المجموعة المحلية، فإن الميزات التالية هي انتقال جيد إلى السحابة:

- [تحليلات نهج المجموعة](/mem/intune/configuration/group-policy-analytics)
- [قوالب المسؤول (ADMX)](/mem/intune/configuration/administrative-templates-windows)
- [كتالوج الإعدادات](/mem/intune/configuration/settings-catalog)


## <a name="next-steps"></a>الخطوات التالية
انتقل إلى [الخطوة 6. مراقبة مخاطر الجهاز والامتثال لأساسيات الأمان](manage-devices-with-intune-monitor-risk.md).
