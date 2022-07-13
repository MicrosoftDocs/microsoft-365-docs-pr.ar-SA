---
title: استخدام Compliance Manager لإدارة إجراءات التحسين
ms.author: chvukosw
author: chvukosw
f1.keywords:
- NOCSH
manager: laurawi
ms.date: 09/29/2020
audience: ITPro
ms.topic: article
ms.prod: microsoft-365-enterprise
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
- Strat_O365_Enterprise
- m365solution-infoprotection
- m365solution-scenario
- zerotrust-solution
ms.custom: admindeeplinkCOMPLIANCE
description: تعرف على كيفية استخدام Compliance Score and Compliance Manager لتحسين مستوى الحماية للبيانات الشخصية.
ms.openlocfilehash: bd0ae7f748a2a3cd5ff52b6363780032033ead44
ms.sourcegitcommit: 61b22df76e0f81e5ef11c587b129287886151c79
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/12/2022
ms.locfileid: "66748682"
---
# <a name="use-compliance-manager-to-manage-improvement-actions"></a>استخدام Compliance Manager لإدارة إجراءات التحسين

يمكن أن يساعدك Microsoft Purview Compliance Manager في إدارة التحسينات المتعلقة بلائحة خصوصية البيانات مثل [القانون العام لحماية البيانات (GDPR)](/compliance/regulatory/gdpr) للاتحاد الأوروبي وقانون [حماية المستهلك في كاليفورنيا CCPA)](/compliance/regulatory/ccpa-faq) وقانون خصوصية HIPAA-HITECH (قانون خصوصية الرعاية الصحية في الولايات المتحدة) وقانون حماية البيانات في البرازيل (LGPD).

توفر هذه المقالة إرشادات حول استخدام هذه الأداة لأغراض خصوصية البيانات.

> [!NOTE]
> وينبغي عدم تفسير التوصيات الواردة من Compliance Manager على أنها ضمان للامتثال. الأمر متروك لك لتقييم والتحقق من فعالية عناصر تحكم العملاء وفقا للبيئة التنظيمية الخاصة بك. تخضع هذه الخدمات للأحكام والشروط الواردة في [شروط الخدمات عبر الإنترنت](https://go.microsoft.com/fwlink/?linkid=2108910). راجع أيضا [إرشادات ترخيص Microsoft 365 للأمان والتوافق](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#compliance-manager)

## <a name="getting-started-with-compliance-manager"></a>بدء استخدام Compliance Manager

#### <a name="what-is-compliance-manager"></a>ما هو Compliance Manager

[Compliance Manager](../compliance/compliance-manager.md) هي أداة لتقييم المخاطر المستندة إلى سير العمل في مدخل التوافق في Microsoft Purview لإدارة أنشطة الامتثال التنظيمي المتعلقة بخدمات Microsoft السحابية. كجزء من اشتراك Microsoft 365 أو Azure Active Directory (Azure AD)، يساعدك Compliance Manager على إدارة الامتثال التنظيمي ضمن نموذج المسؤولية المشتركة لخدمات Microsoft السحابية.

**جاهز لاستخدام التقييمات**

يوفر Compliance Manager قوالب تم إنشاؤها مسبقا [لإنشاء تقييمات](../compliance/compliance-manager-assessments.md) تتماشى مع اللوائح المتعلقة بالخصوصية للبيانات، مثل القانون العام لحماية البيانات (GDPR) وHIAA/HITECH. تحتوي القوالب على تعيين تحكم مضمن لمساعدتك على اتخاذ إجراءات التحسين لتلبية متطلبات اللوائح. يوفر كل تقييم معلومات حول عناصر التحكم التي تستدعيها كل لائحة خاصة بالخدمة المستهدفة، والتي تم تقسيمها بواسطة عناصر التحكم التي تديرها وتتحكم فيها التي تديرها Microsoft.

يساعدك استخدام قالب تم إنشاؤه مسبقا على البدء بسرعة في تقييمات المخاطر. عندما تصبح أكثر كفاءة في استخدام Compliance Manager، يمكنك تخصيص قالب تم إنشاؤه مسبقا عن طريق إضافة عناصر التحكم وإجراءات التحسين الخاصة بك، أو يمكنك إنشاء تقييمات مخصصة خاصة بك لتناسب احتياجات مؤسستك.

عرض [القائمة الكاملة لقوالب التقييم التي](../compliance/compliance-manager-templates-list.md) يوفرها Compliance Manager.

**درجة التوافق في الوقت الحقيقي**

يوفر لك Compliance Manager أيضا درجة توافق تقيس تقدمك في إكمال إجراءات التحسين الموصى بها ضمن عناصر التحكم. يمكنك استخدام هذه النتيجة للمساعدة في مراقبة تقدمك وتحديد أولويات الإجراءات استنادا إلى قدرتها على تقليل المخاطر.

#### <a name="use-the-compliance-manager-quickstart-guide"></a>استخدام دليل التشغيل السريع ل Compliance Manager

يوفر دليل [التشغيل السريع ل Compliance Manager](../compliance/compliance-manager-quickstart.md) خطوات وارتباطات متدرجة إلى الموارد الرئيسية لمساعدتك في العمل مع Compliance Manager:

- [أول زيارة: التعرف على Compliance Manager](../compliance/compliance-manager-quickstart.md#first-visit-get-to-know-compliance-manager)
    - العمل مع لوحة معلومات Compliance Manager
    - فهم درجة التوافق الخاصة بك
    - التعرف على إجراءات التحسين
    - فهم التقييمات والقوالب
- [زيادة: تكوين Compliance Manager لإدارة أنشطة التوافق الخاصة بك](../compliance/compliance-manager-quickstart.md#ramping-up-configure-compliance-manager-to-manage-your-compliance-activities)
    - بناء تقييمك الأول وإدارته
    - تنفيذ أعمال التنفيذ والاختبار على إجراءات التحسين لإكمال عناصر التحكم في تقييماتك
    - فهم كيفية تأثير الإجراءات المختلفة على درجة التوافق الخاصة بك
- [التحجيم: استخدام وظائف متقدمة لتلبية احتياجاتك المخصصة](../compliance/compliance-manager-quickstart.md#scaling-up-use-advanced-functionality-to-meet-your-custom-needs)
    - إنشاء تقييمات مخصصة لتعقب المنتجات غير الخاصة ب Microsoft 365
    - تعديل القوالب الموجودة لإضافة عناصر تحكم أو إزالتها
    - إعداد الاختبار التلقائي لإجراءات التحسين

## <a name="how-your-compliance-score-is-calculated"></a>كيفية حساب نقاط التوافق

يتم حساب درجة التوافق الخاصة بك استنادا إلى مجموعة من تطبيقات التحكم التي يديرها العملاء وMicrosoft. راجع [حساب نقاط التوافق](../compliance/compliance-score-calculation.md) للحصول على شرح مفصل.

يتم تعيين قيمة نقاط لعناصر التحكم استنادا إلى ما إذا كانت إلزامية أو تقديرية، وما إذا كانت وقائية أو مخبرية أو تصحيحية. وتمثل هذه بشكل جماعي خطر عدم تنفيذه بالنسبة إلى عناصر التحكم الأخرى.

كما هو موضح في مقالة حساب نقاط الامتثال، تحصل عناصر التحكم الوقائية على درجة أعلى من تلك المخبرية والتصحيحية، وتحصل عناصر التحكم الإلزامية على درجة أعلى من تلك التي تختصي.

لا تسرد واجهة مستخدم مسؤول نقاط التوافق هذه المعلمات، كما أنها لا توفر القدرة على التصفية حسبها. ومع ذلك، إذا قمت بتنزيل القالب المقترن من Compliance Manager، فإن مجموعة البيانات الناتجة تسرد هذه المعلمات لمعظم اللوائح.

بالنسبة إلى عناصر التحكم التقنية، يقوم Compliance Manager تلقائيا بتحديث درجة إجراء التحسين بمجرد تنفيذ الإجراء واختباره بنجاح. يجب تسجيل إجراءات&mdash;التحكم الأخرى غير التقنية مثل تلك التي تعمل أو المتعلقة بالوثائق&mdash;يدويا كما يتم تنفيذها قبل حساب النقاط في نقاطك.

كما تنفذ العديد منكم إجراءات تحسين معينة لأغراض&mdash;أخرى، على سبيل المثال، استخدام تسميات الاستبقاء لأسباب أخرى غير الامتثال&mdash;لتنظيم خصوصية البيانات بحيث تحصل على رصيد لاستخدام مثل هذه الميزة حتى لو كانت تستخدم لأغراض أخرى، وليس جزءا من إجراء توافق متعمد.

يجب اعتبار درجة الامتثال الخاصة بك مقياسا نسبيا لتتبع التحسين على نطاق واسع. يجب ألا تسعى للحصول على درجة مثالية.

## <a name="additional-guidance"></a>إرشادات إضافية

فيما يلي بعض التلميحات المهمة لاستخدام Compliance Manager لمساعدتك على تحقيق توافق تنظيم خصوصية البيانات:

- يحتوي كل تنظيم خصوصية بيانات على مجموعة من عناصر التحكم التقنية ومواصفات الوثائق ومتطلبات التشغيل والعمليات وإعداد التقارير. تظهر كل هذه في إجراءات التحسين.

- لتركيز طريقة عرض إجراءات التحسين على مجال اهتمامك، يمكنك التصفية حسب نوع الإجراء في علامة التبويب **"حلول** " في مسؤول Compliance Manager. تعرف على المزيد حول [تصفية طريقة عرض لوحة معلومات Compliance Manager](../compliance/compliance-manager-setup.md#filtering-your-dashboard-view).

- يجب اعتبار الأهمية النسبية وأولوية إجراءات التحسين المحددة في Compliance Manager كجزء من مراجعة المخاطر الأوسع بالإضافة إلى مخاطر خصوصية البيانات التي حددت أن مؤسستك تحتاج إلى إدارتها.

- حتى مع تجميع إجراءات التحسين عبر المتطلبات التنظيمية المتعددة، إذا تم تحديد قوالب تقييم اللوائح الخاصة ب GDPR وGGPD وCCPA وHIPA-HITECH، على سبيل المثال، سيتم إدراج ما يقرب من 400 إجراء تحسين في Compliance Manager. لمعالجة هذه القائمة الطويلة بشكل أفضل، استخدم عامل تصفية إجراء التحسين لتقليل مجموعة النتائج إلى قائمة أكثر قابلية للإدارة.

- يوفر عامل تصفية الفئات وسيلة لتصفية إجراءات التحسين عن طريق التجميع المنطقي، والتي تتوافق مع المقالات "تعقب" و"منع" و"حماية" و"استبقاء" و"التحقيق" في هذا الحل الشامل.

- قد تعتبر بعض عناصر التحكم المدرجة في إجراءات التحسين أكثر ارتباطا مباشرة بمقالة تنظيمية معينة، بينما قد ترتبط عناصر التحكم الأخرى بشكل غير مباشر بروح التنظيم، وفي كثير من الأحيان يوصى بالأنشطة أو أفضل الممارسات ببساطة.