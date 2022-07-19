---
title: دليل المبادئ التجريبي - Microsoft Defender لنقطة النهاية
description: استخدم هذا الدليل لتحقيق أقصى استفادة من الإصدار التجريبي المجاني لمدة 90 يوما. تعرف على كيفية مساعدة Defender لنقطة النهاية في منع التهديدات المتقدمة واكتشافها والتحقيق فيها والاستجابة لها.
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: ITPro
ms.topic: how-to
ms.date: 07/07/2022
ms.prod: m365-security
ms.technology: mde
ms.localizationpriority: medium
ms.reviewer: ''
f1.keywords: NOCSH
ms.openlocfilehash: 2b7a4d47d07fd609fb9dd424f2a8b89af2ed0b9b
ms.sourcegitcommit: 9fdb5c5b9eaf0c8a8d62b579a5fb5a5dc2d29fa9
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/11/2022
ms.locfileid: "66857536"
---
# <a name="trial-playbook-microsoft-defender-for-endpoint"></a>دليل المبادئ التجريبي: Microsoft Defender لنقطة النهاية

مرحبا بك في دليل المبادئ التجريبي Microsoft Defender لنقطة النهاية Plan 2!

دليل المبادئ هذا هو دليل بسيط لمساعدتك على تحقيق أقصى استفادة من الإصدار التجريبي المجاني. باستخدام الخطوات المقترحة في هذه المقالة من فريق Microsoft Defender، ستتعرف على كيفية مساعدة Defender for Endpoint في منع التهديدات المتقدمة واكتشافها والتحقيق فيها والاستجابة لها.

## <a name="what-is-defender-for-endpoint"></a>ما هو Defender لنقطة النهاية؟

[Defender for Endpoint](microsoft-defender-endpoint.md) هو نظام أساسي لأمان نقطة نهاية المؤسسة يستخدم المجموعة التالية من التكنولوجيا المضمنة في Windows وخدمة السحابة القوية من Microsoft: 

- **أجهزة الاستشعار السلوكية لنقطة النهاية**: مضمنة في Windows، تجمع أجهزة الاستشعار هذه الإشارات السلوكية وتعالجها من نظام التشغيل وترسل بيانات المستشعر إلى مثيل السحابة الخاص والمعزول ل Defender لنقطة النهاية.

- **تحليلات أمان السحابة**: تتم ترجمة استخدام البيانات الضخمة وتعلم الأجهزة وبصريات Microsoft الفريدة عبر النظام البنائي ل Windows والمنتجات السحابية للمؤسسات (مثل Microsoft 365) والأصول عبر الإنترنت والإشارات السلوكية إلى رؤى واكتشافات واستجابات موصى بها للتهديدات المتقدمة.

- **التحليل الذكي للمخاطر**: تم إنشاؤه من قبل متتبعي Microsoft وفرق الأمان، وزيادة التحليل الذكي للمخاطر الذي يوفره الشركاء، ويمكن التحليل الذكي للمخاطر Defender لنقطة النهاية من تحديد أدوات المهاجم وتقنياته وإجراءاته، وإنشاء تنبيهات عند ملاحظتها في بيانات المستشعر المجمعة.

<center><h2>Microsoft Defender لنقطة النهاية</center></h2>
<table>
<tr>
<td><a href="microsoft-defender-endpoint.md#tvm"><center><img src="images/logo-mdvm.png" alt="Vulnerability Management"> <br><b> Core Defender Vulnerability Management</b></center></a></td>
<td><a href="microsoft-defender-endpoint.md#asr"><center><img src="images/asr-icon.png" alt="Attack surface reduction"><br><b>تقليل الأجزاء المعرضة للهجوم</b></center></a></td>
<td><center><a href="microsoft-defender-endpoint.md#ngp"><img src="images/ngp-icon.png" alt="Next-generation protection"><br> <b>حماية الجيل التالي</b></a></center></td>
<td><center><a href="microsoft-defender-endpoint.md#edr"><img src="images/edr-icon.png" alt="Endpoint detection and response"><br> <b>الكشف عن نقطة النهاية والاستجابة لها</b></a></center></td>
<td><center><a href="microsoft-defender-endpoint.md#ai"><img src="images/air-icon.png" alt="Automated investigation and remediation"><br> <b>التحقيق التلقائي والمعالجة</b></a></center></td>
<td><center><a href="microsoft-defender-endpoint.md#mte"><img src="images/mte-icon.png" alt="Microsoft Threat Experts"><br> <b>خبراء المخاطر في Microsoft</b></a></center></td>
</tr>
<tr>
<td colspan="7">
<a href="microsoft-defender-endpoint.md#apis"><center><b>التكوين والإدارة المركزيان، واجهات برمجة التطبيقات</a></b></center></td>
</tr>
<tr>
<td colspan="7"><a href="microsoft-defender-endpoint.md#mtp"><center><b>Microsoft 365 Defender</a></center></b></td>
</tr>
</table>
<br>

**لنبدأ!**

## <a name="set-up-your-trial"></a>إعداد الإصدار التجريبي

1. [تأكيد حالة الترخيص](#step-1-confirm-your-license-state).
2. [قم بإعداد التحكم في الوصول استنادا إلى الدور ومنح الأذونات لفريق الأمان.](#step-2-set-up-role-based-access-control-and-grant-permissions-to-your-security-team)
3. [تفضل بزيارة مدخل Microsoft 365 Defender](#step-3-visit-the-microsoft-365-defender-portal).
4. [إلحاق نقاط النهاية باستخدام أي من أدوات الإدارة المدعومة](#step-4-onboard-endpoints-using-any-of-the-supported-management-tools).
5. [تكوين القدرات](#step-5-configure-capabilities).
6. [الخبرة Microsoft Defender لنقطة النهاية من خلال هجمات المحاكاة](#step-6-experience-microsoft-defender-for-endpoint-through-simulated-attacks).
7. [إعداد مختبر تقييم Microsoft Defender لنقطة النهاية](#step-7-set-up-the-microsoft-defender-for-endpoint-evaluation-lab).

## <a name="step-1-confirm-your-license-state"></a>الخطوة 1: تأكيد حالة الترخيص

للتأكد من توفير اشتراك Defender لنقطة النهاية بشكل صحيح، يمكنك التحقق من حالة الترخيص إما في مركز مسؤولي Microsoft 365 ([https://admin.microsoft.com](https://admin.microsoft.com)) أو Azure Active Directory ([https://portal.azure.com](https://portal.azure.com/#blade/Microsoft_AAD_IAM/LicensesMenuBlade/Products)).

[تحقق من حالة الترخيص](production-deployment.md#check-license-state).

## <a name="step-2-set-up-role-based-access-control-and-grant-permissions-to-your-security-team"></a>الخطوة 2: إعداد التحكم في الوصول استنادا إلى الدور ومنح الأذونات لفريق الأمان

توصي Microsoft باستخدام مفهوم الامتيازات الأقل. يستخدم Defender لنقطة النهاية أدوارا مضمنة داخل Azure Active Directory. [راجع الأدوار المختلفة المتوفرة](/azure/active-directory/roles/permissions-reference) واختر الأدوار المناسبة لفريق الأمان. قد تحتاج بعض الأدوار إلى تطبيقها مؤقتا وإزالتها بعد اكتمال التجربة.

استخدم [إدارة الهويات المتميزة](/azure/active-directory/active-directory-privileged-identity-management-configure) لإدارة أدوارك لتوفير تدقيق وتحكم ومراجعة وصول إضافية للمستخدمين الذين لديهم أذونات دليل.

يدعم Defender لنقطة النهاية طريقتين لإدارة الأذونات:

- إدارة الأذونات الأساسية: تعيين الأذونات إما للوصول الكامل أو للقراءة فقط. يمكن للمستخدمين الذين لديهم أدوار المسؤول العام أو مسؤول الأمان في Azure Active Directory الوصول الكامل. دور قارئ الأمان لديه حق الوصول للقراءة فقط ولا يمنح حق الوصول لعرض مخزون الأجهزة/الأجهزة.
- التحكم في الوصول استنادا إلى الدور (RBAC): تعيين أذونات متعددة المستويات عن طريق تحديد الأدوار، وتعيين Azure AD مجموعات المستخدمين للأدوار، ومنح مجموعات المستخدمين حق الوصول إلى مجموعات الأجهزة. لمزيد من المعلومات، راجع [إدارة الوصول إلى المدخل باستخدام التحكم في الوصول المستند إلى الدور](rbac.md).

## <a name="step-3-visit-the-microsoft-365-defender-portal"></a>الخطوة 3: زيارة مدخل Microsoft 365 Defender

مدخل Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)) هو المكان الذي يمكنك فيه الوصول إلى قدرات Defender لنقطة النهاية.

1. [راجع ما يجب توقعه](../defender/microsoft-365-defender-portal.md) في مدخل Microsoft 365 Defender.

2. انتقل إلى [https://security.microsoft.com](https://security.microsoft.com) وسجل الدخول.

3. في جزء التنقل، راجع قسم **نقاط النهاية** للوصول إلى قدراتك. 

## <a name="step-4-onboard-endpoints-using-any-of-the-supported-management-tools"></a>الخطوة 4: إلحاق نقاط النهاية باستخدام أي من أدوات الإدارة المدعومة 

يوضح هذا القسم الخطوات العامة لإلحاق الأجهزة (نقاط النهاية).

1. [شاهد هذا الفيديو](https://www.microsoft.com/videoplayer/embed/RE4bGqr) للحصول على نظرة عامة سريعة حول عملية الإلحاق وتعرف على الأدوات والأساليب المتوفرة.

2. راجع [خيارات أداة إلحاق جهازك](onboarding.md) وحدد الخيار الأنسب للبيئة الخاصة بك. 

## <a name="step-5-configure-capabilities"></a>الخطوة 5: تكوين القدرات 

بعد إلحاق الأجهزة (نقاط النهاية)، ستقوم بتكوين القدرات المختلفة، مثل الكشف عن نقطة النهاية والاستجابة لها، وحماية الجيل التالي، وتقليل الأجزاء المعرضة للهجوم.

استخدم [هذا الجدول](onboarding.md) لاختيار المكونات التي تريد تكوينها. نوصي بتكوين جميع القدرات المتاحة، ولكن يمكنك تخطي تلك التي لا تنطبق.

## <a name="step-6-experience-microsoft-defender-for-endpoint-through-simulated-attacks"></a>الخطوة 6: تجربة Microsoft Defender لنقطة النهاية من خلال هجمات المحاكاة

قد تحتاج إلى تجربة Defender لنقطة النهاية قبل إلحاق أكثر من عدد قليل من الأجهزة إلى الخدمة. للقيام بذلك، يمكنك تشغيل محاكاة الهجوم الخاضعة للرقابة على عدد قليل من أجهزة الاختبار. بعد تشغيل هجمات المحاكاة، يمكنك مراجعة كيفية عرض Defender لنقطة النهاية لنشاط ضار واستكشاف كيفية تمكين استجابة فعالة.

لتشغيل أي من عمليات المحاكاة المقدمة، تحتاج إلى [جهاز واحد على الأقل تم إلحاقه](onboard-configure.md).

1. الوصول إلى البرامج التعليمية. في مدخل Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com))، في جزء التنقل، ضمن **نقاط النهاية**، اختر **البرامج التعليمية**.

2. اقرأ مستند المعاينة المتوفر مع كل سيناريو هجوم. يتضمن كل مستند متطلبات نظام التشغيل والتطبيق والتعليمات التفصيلية الخاصة بسيناريو الهجوم.

3. [تشغيل محاكاة](attack-simulations.md).

## <a name="step-7-set-up-the-microsoft-defender-for-endpoint-evaluation-lab"></a>الخطوة 7: إعداد مختبر تقييم Microsoft Defender لنقطة النهاية   

تم تصميم مختبر تقييم Microsoft Defender لنقطة النهاية للقضاء على تعقيدات تكوين الجهاز والبيئة بحيث يمكنك التركيز على تقييم قدرات النظام الأساسي وتشغيل المحاكاة ورؤية ميزات الوقاية والكشف والمعالجة في العمل. باستخدام تجربة الإعداد المبسطة في مختبر التقييم، يمكنك التركيز على تشغيل سيناريوهات الاختبار الخاصة بك والمحاكاة مسبقة الصنع لمعرفة كيفية أداء Defender لنقطة النهاية.

- [شاهد نظرة عامة على الفيديو](https://www.microsoft.com/videoplayer/embed/RE4qLUM) لمختبر التقييم
- [بدء استخدام المختبر](evaluation-lab.md) 


## <a name="see-also"></a>راجع أيضًا

- [وثائق Defender for Endpoint الفنية](microsoft-defender-endpoint.md)
- [مكتبة المحتوى التقني لأمان Microsoft](https://www.microsoft.com/security/content-library/Home/Index)
- [عرض توضيحي ل Defender لنقطة النهاية](https://cdx.transform.microsoft.com/experience-detail/d5eca65d-13a3-464d-9171-c24cf9dd6050)

