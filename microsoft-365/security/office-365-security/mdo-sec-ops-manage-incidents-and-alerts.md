---
title: إدارة الحوادث والتنبيهات من Defender لـ Office 365 في Microsoft 365 Defender
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
audience: Admin
ms.date: ''
ms.topic: conceptual
ms.localizationpriority: medium
search.appverid:
- MET150
- MOE150
ms.collection:
- M365-security-compliance
ms.custom: ''
description: يمكن لموظفي SecOps معرفة كيفية استخدام قائمة انتظار الحوادث في Microsoft 365 Defender لإدارة الحوادث في Microsoft Defender لـ Office 365.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 8467d77bd3bdd99af0a33f7fc373e61f7e3efb51
ms.sourcegitcommit: 725a92b0b1555572b306b285a0e7a7614d34e5e5
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 05/24/2022
ms.locfileid: "66857326"
---
# <a name="manage-incidents-and-alerts-from-microsoft-defender-for-office-365-in-microsoft-365-defender"></a>إدارة الحوادث والتنبيهات من Microsoft Defender لـ Office 365 في Microsoft 365 Defender

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**ينطبق على:**
- [خطة 1 وخطة 2 من Microsoft Defender لـ Office 365](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

[الحادث](/microsoft-365/security/defender/incidents-overview) في Microsoft 365 Defender هو مجموعة من التنبيهات المرتبطة والبيانات المرتبطة التي تحدد القصة الكاملة للهجوم. Defender لـ Office 365 [التنبيهات](/microsoft-365/compliance/alert-policies#default-alert-policies) والتحقيق [التلقائي والاستجابة (AIR)](office-365-air.md#the-overall-flow-of-air) ونتائج التحقيقات مدمجة في الأصل ومربطة في صفحة **الحوادث** في Microsoft 365 Defender في <https://security.microsoft.com/incidents-queue>. سنشير إلى هذه الصفحة على أنها _قائمة انتظار الحوادث_.

يتم إنشاء التنبيهات عندما يؤثر نشاط ضار أو مريب على كيان (على سبيل المثال، البريد الإلكتروني أو المستخدمون أو علب البريد). توفر التنبيهات رؤى قيمة حول الهجمات قيد التقدم أو الهجمات المكتملة. ومع ذلك، يمكن أن يؤثر الهجوم المستمر على كيانات متعددة، ما ينتج عنه تنبيهات متعددة من مصادر مختلفة. ستقوم بعض التنبيهات المضمنة بتشغيل أدلة مبادئ AIR تلقائيا. تقوم أدلة المبادئ هذه بسلسلة من خطوات التحقيق للبحث عن الكيانات المتأثرة الأخرى أو النشاط المشبوه.

شاهد هذا الفيديو القصير حول كيفية إدارة تنبيهات Microsoft Defender لـ Office 365 في Microsoft 365 Defender.  
> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RWGrL2]

Defender لـ Office 365 التنبيهات والتحقيقات وبياناتها مرتبطة تلقائيا. عند تحديد علاقة، يتم إنشاء حادث من قبل النظام لمنح فرق الأمان رؤية للهجوم بأكمله.

نوصي بشدة بأن تقوم فرق SecOps بإدارة الحوادث والتنبيهات من Defender لـ Office 365 في قائمة انتظار الحوادث في <https://security.microsoft.com/incidents-queue>. هذا النهج له الفوائد التالية:

- خيارات متعددة [للإدارة](/microsoft-365/security/defender/manage-incidents):
  - الاولويات
  - تصفيه
  - تصنيف
  - إدارة العلامات

  يمكنك أخذ الحوادث مباشرة من قائمة الانتظار أو تعيينها إلى شخص ما. يمكن أن تساعد التعليقات ومحفوظات التعليقات في تعقب التقدم.

- إذا كان الهجوم يؤثر على أحمال العمل الأخرى المحمية بواسطة Microsoft Defender<sup>\*</sup>، فإن التنبيهات والتحقيقات وبياناتها ذات الصلة ترتبط أيضا بنفس الحادث.

  <sup>\*</sup>Microsoft Defender لنقطة النهاية، Microsoft Defender for Identity، Microsoft Defender for Cloud Apps.

- منطق الارتباط المعقد غير مطلوب، لأن المنطق يوفره النظام.

- إذا لم يفي منطق الارتباط باحتياجاتك بشكل كامل، يمكنك إضافة تنبيهات إلى الحوادث الحالية أو إنشاء حوادث جديدة.

- تتم إضافة تنبيهات Defender لـ Office 365 ذات الصلة، والتحقيقات في AIR، والإجراءات المعلقة من التحقيقات تلقائيا إلى الحوادث.

- إذا لم يعثر تحقيق AIR على أي تهديد، يتم حل التنبيهات ذات الصلة تلقائيا بواسطة النظام. إذا تم حل جميع التنبيهات داخل حدث، تتغير حالة الحدث أيضا إلى **"تم الحل**".

- يتم تجميع إجراءات الأدلة والاستجابة ذات الصلة تلقائيا في علامة تبويب **الأدلة والاستجابة** للحادث.

- يمكن لأعضاء فريق الأمان اتخاذ إجراءات الاستجابة مباشرة من الحوادث. على سبيل المثال، يمكنهم حذف البريد الإلكتروني مبدئيا في علب البريد أو إزالة قواعد علبة الوارد المريبة من علب البريد.

- يتم إنشاء إجراءات البريد الإلكتروني الموصى بها فقط عندما يكون أحدث موقع تسليم لرسالة بريد إلكتروني ضارة هو علبة بريد سحابية.

- يتم تحديث إجراءات البريد الإلكتروني المعلقة استنادا إلى موقع التسليم الأخير. إذا تمت معالجة البريد الإلكتروني بالفعل بواسطة إجراء يدوي، فستعكس الحالة ذلك.

- يتم إنشاء الإجراءات الموصى بها فقط لمجموعات البريد الإلكتروني والبريد الإلكتروني التي تم تحديدها على أنها أهم التهديدات:
  - البرامج الضاره
  - التصيد الاحتيالي عالي الثقة
  - عناوين URL الضارة
  - ملفات ضارة

> [!NOTE]
> لا تمثل الحوادث الأحداث الثابتة فقط. كما أنها تمثل قصص الهجوم التي تحدث بمرور الوقت. مع تقدم الهجوم، تتم إضافة تنبيهات Defender لـ Office 365 جديدة، وتحقيقات AIR، وبياناتها باستمرار إلى الحادث الحالي.

إدارة الحوادث على صفحة **الحوادث** في مدخل Microsoft 365 Defender على<https://security.microsoft.com/incidents-queue>:

![صفحة الحوادث في مدخل Microsoft 365 Defender.](../../media/mdo-sec-ops-incidents.png)

![القائمة المنبثقة للتفاصيل على صفحة الحوادث في مدخل Microsoft 365 Defender.](../../media/mdo-sec-ops-incident-details.png)

![تصفية القائمة المنبثقة على صفحة الحوادث في مدخل Microsoft 365 Defender.](../../media/mdo-sec-ops-incident-filters.png)

![علامة تبويب ملخص لتفاصيل الحادث في مدخل Microsoft 365 Defender.](../../media/mdo-sec-ops-incident-summary-tab.png)

![علامة تبويب الأدلة والتنبيهات لتفاصيل الحادث في مدخل Microsoft 365 Defender.](../../media/mdo-sec-ops-incident-evidence-and-response-tab.png)

إدارة الحوادث في صفحة **الحوادث** في Microsoft Sentinel على <https://portal.azure.com/#blade/HubsExtension/BrowseResource/resourceType/microsoft.securityinsightsarg%2Fsentinel>:

![صفحة الأحداث في Microsoft Sentinel.](../../media/mdo-sec-ops-microsoft-sentinel-incidents.png)

![صفحة تفاصيل الحادث في Microsoft Sentinel.](../../media/mdo-sec-ops-microsoft-sentinel-incident-details.png)

## <a name="response-actions-to-take"></a>إجراءات الاستجابة التي يجب اتخاذها

يمكن لفرق الأمان اتخاذ مجموعة واسعة من إجراءات الاستجابة على البريد الإلكتروني باستخدام أدوات Defender لـ Office 365:

- يمكنك حذف الرسائل، ولكن يمكنك أيضا اتخاذ الإجراءات التالية على البريد الإلكتروني:
  - الانتقال إلى علبة الوارد
  - الانتقال إلى "غير هام"
  - الانتقال إلى العناصر المحذوفة
  - حذف مبدئي
  - حذف ثابت.

  يمكنك اتخاذ هذه الإجراءات من المواقع التالية:

  - علامة التبويب **"دليل" و"استجابة** " من تفاصيل الحادث في صفحة **"Incidents** "** في <https://security.microsoft.com/incidents-queue> (مستحسن).
  - **مستكشف المخاطر** في <https://security.microsoft.com/threatexplorer>.
  - **مركز الصيانة** الموحد في <https://security.microsoft.com/action-center/pending>.

- يمكنك بدء تشغيل دليل مبادئ AIR يدويا على أي رسالة بريد إلكتروني باستخدام إجراء **التحقيق في المشغل** في مستكشف التهديدات.

- يمكنك الإبلاغ عن عمليات الكشف الإيجابية أو السلبية الخاطئة الخاطئة مباشرة إلى Microsoft باستخدام [مستكشف التهديدات](threat-explorer.md) أو [عمليات إرسال المسؤول](admin-submission.md).

- يمكنك حظر الملفات الضارة أو عناوين URL أو المرسلين غير المعرفين باستخدام [قائمة السماح/الحظر للمستأجر](tenant-allow-block-list.md).

يتم دمج إجراءات Defender لـ Office 365 بسلاسة في تجارب التتبع وتكون محفوظات الإجراءات مرئية على علامة التبويب **«History**» في **مركز الصيانة** الموحد في <https://security.microsoft.com/action-center/history>.

الطريقة الأكثر فعالية لاتخاذ إجراء هي استخدام التكامل المضمن مع الحوادث في Microsoft 365 Defender. يمكنك ببساطة الموافقة على الإجراءات التي أوصى بها AIR في Defender لـ Office 365 على علامة التبويب ["دليل" والاستجابة](/microsoft-365/security/defender/investigate-incidents#evidence-and-response) لحادث في Microsoft 365 Defender. يوصى باستخدام أسلوب الإجراء هذا للأسباب التالية:

- تحقق من قصة الهجوم الكاملة.
- يمكنك الاستفادة من الارتباط المضمن مع أحمال العمل الأخرى: Microsoft Defender لنقطة النهاية، Microsoft Defender for Identity، Microsoft Defender for Cloud Apps.
- يمكنك اتخاذ إجراءات على البريد الإلكتروني من مكان واحد.

يمكنك اتخاذ إجراء على البريد الإلكتروني استنادا إلى نتيجة التحقيق اليدوي أو نشاط التتبع. يسمح [مستكشف التهديدات](threat-explorer.md) لأعضاء فريق الأمان باتخاذ إجراء بشأن أي رسائل بريد إلكتروني قد لا تزال موجودة في علب بريد السحابة. يمكنهم اتخاذ إجراء بشأن الرسائل داخل المؤسسة التي تم إرسالها بين المستخدمين في مؤسستك. تتوفر بيانات مستكشف التهديدات لآخر 30 يوما.

شاهد هذا الفيديو القصير لمعرفة كيفية دمج Microsoft 365 Defender بين التنبيهات من مصادر الكشف المختلفة، مثل Defender لـ Office 365، في الحوادث. 
> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RWGpcs]
