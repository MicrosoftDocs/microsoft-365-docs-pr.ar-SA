---
title: تنبيه مصنفات الدرجات
description: راجع التنبيهات الخاصة بلهجمات معروفة واتخذ الإجراءات الموصى بها لإعادة معالجة الهجوم وحماية شبكتك.
keywords: الأحداث والتنبيهات، التحقيق، التحليل، الاستجابة، الارتباط، الهجوم، الأجهزة، الأجهزة، المستخدمون، الهويات، الهوية، علبة البريد، البريد الإلكتروني، 365، microsoft، m365
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
ms.topic: how-to
ms.custom:
- autoir
- admindeeplinkDEFENDER
ms.reviewer: evaldm, isco
ms.technology: m365d
ms.openlocfilehash: 129a4f2efd9a47c09535be3ba0f56504f3da697c
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/08/2022
ms.locfileid: "63574751"
---
# <a name="alert-grading-playbooks"></a>تنبيه مصنفات الدرجات

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**ينطبق على:**
- Microsoft 365 Defender

تسمح لك دفاتر تشغيل تصنيف التنبيهات بمراجعة التنبيهات وتصنيفها سريعا للهجمات المعروفة واتخاذ الإجراءات الموصى بها لتصحيح الهجوم وحماية شبكتك. سيساعد تصنيف التنبيه أيضا في تصنيف الحادث بشكل صحيح.

ب أنت باحث الأمان أو محلل مركز عمليات الأمان (SOC)، يجب أن يكون لديك حق الوصول إلى مدخل Microsoft 365 Defender بحيث يمكنك:

- تقييم التنبيهات التي تم إنشاؤها والحوادث المرتبطة بها ومراجعتها. راجع [التحقق من التنبيهات](investigate-alerts.md).
- ابحث في بيانات إشارة الأمان للمستأجر وتحقق من التهديدات المحتملة والأنشطة المريبة. راجع [الصيد المتقدم](advanced-hunting-overview.md).

>[!Note]
>يمكنك تقديم ملاحظات إلى Microsoft حول تنبيهات إيجابية وتنبيهات خاطئة حقيقية، ليس فقط في نهاية التحقيق، ولكن أيضا أثناء عملية التحقيق. يمكن أن يساعد هذا Microsoft في تحليل أحداث الأمان وتصنيفها في المستقبل.
>

## <a name="microsoft-defender-for-office-365"></a>Microsoft Defender Office 365

[يحمي Microsoft Defender Office 365](/microsoft-365/security/office-365-security/defender-for-office-365) مؤسستك من التهديدات الضارة التي تفرضها رسائل البريد الإلكتروني والربط (عناوين URL) وأدوات التعاون. يتضمن defender for Office 365:

- سياسات الحماية من المخاطر

   حدد سياسات الحماية من المخاطر لتعيين مستوى الحماية المناسب لمنظمتك.

- التقارير

  اشاهد تقارير الوقت الحقيقي لمراقبة Defender Office 365 أداء مؤسستك.

- قدرات الاستجابة والتحري عن المخاطر

  استخدم أدوات الطليعة للتحقق من التهديدات وفهمها ومحاكاةها ومنعها.

- قدرات الاستجابة والتحري التلقائي

  وفر الوقت والجهد في التحقق من التهديدات وتخفيفها.

يمكن تصنيف Office 365 على أنها: 

- إيجابية حقيقية (TP) لنشاط ضار تم تأكيده. 
- إيجابية خاطئة (FP) لنشاط غير ضار تم تأكيده.

>[!Note]
>Microsoft 365 Defender المدخل [https://security.microsoft.com](https://security.microsoft.com) الوظائف معا من مداخل أمان Microsoft الموجودة. ويبرز Microsoft 365 Defender الوصول السريع إلى المعلومات والتخطيطات الأسهل وإحضار المعلومات ذات الصلة معا لتسهيل الاستخدام.
>

## <a name="microsoft-defender-for-cloud-apps"></a>Microsoft Defender لتطبيقات السحابة

[Microsoft Defender لتطبيقات السحابة](/defender-cloud-apps) هو وسيط أمان الوصول السحابي (CASB) الذي يدعم أوضاع النشر المختلفة بما في ذلك مجموعة السجلات وموصلات API والوكيل العكسي. فهو يوفر رؤية غنية، والتحكم في تنقل البيانات، وتحليلات متطورة لتحديد التهديدات الإلكترونية ومكافحتها عبر جميع خدمات Microsoft والخدمات السحابية التي تقدمها جهة خارجية.

يتكامل Defender for Cloud Apps بشكل أصلي مع حلول Microsoft الرائدة وقد تم تصميمه مع وضع محترفي الأمان في الاعتبار. فهو يوفر النشر البسيط والإدارة المركزية وإمكانيات التنفيذ التلقائي الابتكارية.

يتضمن إطار عمل Defender for Cloud Apps القدرة على حماية شبكتك من التهديدات الإلكترونية والغريبة، ويكشف عن سلوك غير معتاد عبر تطبيقات السحابة لتحديد برامج الفدية الضارة أو المستخدمين المعرضين للاختطار أو التطبيقات المخادعة. وهو يمكن تحليل الاستخدام عالي المخاطر ويمكنه المعالجة تلقائيا للحد من المخاطر في مؤسستك.

يمكن تصنيف تنبيهات Defender for Cloud Apps كما يلي: 

- TP للنشاط الضار الذي تم تأكيده. 
- إيجابية حقيقية (B-TP) لأي نشاط مريب ولكن ليس ضار، مثل اختبار اختراق أو إجراء مريب آخر معتمد. 
- FP لنشاط غير ضار تم تأكيده.

## <a name="alert-grading-playbooks"></a>تنبيه مصنفات الدرجات

راجع دفاتر التشغيل هذه للحصول على خطوات لت درجات التنبيهات بسرعة أكبر للتهديدات التالية:

- [نشاط إعادة توجيه البريد الإلكتروني المريب](alert-grading-playbook-email-forwarding.md)
- [قواعد معالجة علبة الوارد المريبة](alert-grading-playbook-inbox-manipulation-rules.md)
- [قواعد إعادة توجيه علبة الوارد المريبة](alert-grading-playbook-inbox-forwarding-rules.md)

راجع [التحقق من التنبيهات](investigate-alerts.md) للحصول على معلومات حول كيفية فحص التنبيهات باستخدام Microsoft 365 Defender المدخل.
