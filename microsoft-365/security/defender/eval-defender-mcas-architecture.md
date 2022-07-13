---
title: مراجعة متطلبات البنية وبنية Microsoft Defender for Cloud Apps
description: Microsoft Defender for Cloud Apps تشرح الرسومات التخطيطية التقنية البنية في Microsoft 365 Defender، والتي ستساعدك على بناء بيئة تجريبية.
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: bcarter
author: brendacarter
ms.date: 07/09/2021
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365solution-scenario
- m365solution-evalutatemtp
- zerotrust-solution
ms.topic: conceptual
ms.technology: m365d
ms.openlocfilehash: 7cc147f60d3ae7ccd7014476de5c6839fa67131f
ms.sourcegitcommit: 61b22df76e0f81e5ef11c587b129287886151c79
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/12/2022
ms.locfileid: "66747978"
---
# <a name="review-architecture-requirements-and-key-concepts-for-microsoft-defender-for-cloud-apps"></a>مراجعة متطلبات البنية والمفاهيم الرئيسية Microsoft Defender for Cloud Apps


**ينطبق على:**

- Microsoft 365 Defender

هذه المقالة هي [الخطوة 1 من 3](eval-defender-mcas-overview.md) في عملية إعداد بيئة التقييم Microsoft Defender for Cloud Apps جنبا إلى جنب مع Microsoft 365 Defender. لمزيد من المعلومات حول هذه العملية، راجع [مقالة النظرة العامة](eval-defender-identity-overview.md).

قبل تمكين Microsoft Defender for Cloud Apps، تأكد من فهمك للبنية ويمكن أن تفي بالمتطلبات. 

## <a name="understand-the-architecture"></a>فهم البنية

Microsoft Defender for Cloud Apps هو وسيط أمان الوصول إلى السحابة (CASB). تعمل CASBs بمثابة أداة حماية للوسيط للوصول في الوقت الحقيقي بين مستخدمي المؤسسة والموارد السحابية التي يستخدمونها، أينما كان المستخدمون بغض النظر عن الجهاز الذي يستخدمونه. يتكامل Microsoft Defender for Cloud Apps أصلا مع قدرات أمان Microsoft، بما في ذلك Microsoft 365 Defender.

بدون Defender for Cloud Apps، تكون تطبيقات السحابة التي تستخدمها مؤسستك غير مدارة وغير محمية، كما هو موضح.

:::image type="content" source="../../media/defender/m365-defender-mcas-architecture-a.png" alt-text="بنية Microsoft Defender for Cloud Apps" lightbox="../../media/defender/m365-defender-mcas-architecture-a.png":::

في الرسم التوضيحي:
- استخدام تطبيقات السحابة من قبل مؤسسة غير مراقب وغير محمي. 
- يقع هذا الاستخدام خارج الحماية التي تم تحقيقها داخل مؤسسة مدارة. 

#### <a name="discovering-cloud-apps"></a>اكتشاف تطبيقات السحابة

الخطوة الأولى لإدارة استخدام تطبيقات السحابة هي اكتشاف تطبيقات السحابة التي تستخدمها مؤسستك. يوضح هذا الرسم التخطيطي التالي كيفية عمل اكتشاف السحابة مع Defender for Cloud Apps.

:::image type="content" source="../../media/defender/m365-defender-mcas-architecture-b.png" alt-text="تصميم Microsoft Defender for Cloud Apps في اكتشاف السحابة" lightbox="../../media/defender/m365-defender-mcas-architecture-b.png":::


في هذا الرسم التوضيحي، هناك طريقتان يمكن استخدامهما لمراقبة نسبة استخدام الشبكة واكتشاف تطبيقات السحابة التي تستخدمها مؤسستك.
- A. يتكامل Cloud App Discovery مع Microsoft Defender لنقطة النهاية في الأصل. يقوم Defender لنقطة النهاية بالإبلاغ عن التطبيقات والخدمات السحابية التي يتم الوصول إليها من أجهزة Windows 10 Windows 11 التي تديرها تكنولوجيا المعلومات. 
- ب. للتغطية على جميع الأجهزة المتصلة بشبكة، يتم تثبيت مجمع سجل Defender for Cloud Apps على جدران الحماية والوكلاء الآخرين لجمع البيانات من نقاط النهاية. يتم إرسال هذه البيانات إلى Defender for Cloud Apps للتحليل.

#### <a name="managing-cloud-apps"></a>إدارة تطبيقات السحابة

بعد اكتشاف تطبيقات السحابة وتحليل كيفية استخدام هذه التطبيقات من قبل مؤسستك، يمكنك البدء في إدارة تطبيقات السحابة التي تختارها. 

:::image type="content" source="../../media/defender/m365-defender-mcas-architecture-c.png" alt-text="تصميم Microsoft Defender for Cloud Apps أثناء إدارة تطبيقات السحابة" lightbox="../../media/defender/m365-defender-mcas-architecture-c.png":::

في هذا الرسم التوضيحي:
- يتم فرض العقوبات على بعض التطبيقات للاستخدام. هذه العقوبات هي طريقة بسيطة للبدء في إدارة التطبيقات.
- يمكنك تمكين رؤية وتحكم أكبر من خلال توصيل التطبيقات بموصلات التطبيقات. تستخدم موصلات التطبيقات واجهات برمجة التطبيقات لموفري التطبيقات.


#### <a name="applying-session-controls-to-cloud-apps"></a>تطبيق عناصر التحكم في جلسة العمل على تطبيقات السحابة

يعمل Microsoft Defender for Cloud Apps كوكيل عكسي، ما يوفر وصول الوكيل إلى تطبيقات السحابة التي تم فرض العقوبات عليها. يسمح هذا التوفير ل Defender for Cloud Apps بتطبيق عناصر التحكم في جلسة العمل التي تقوم بتكوينها. 

:::image type="content" source="../../media/defender/m365-defender-mcas-architecture-d.png" alt-text="بنية Microsoft Defender for Cloud Apps - التحكم في جلسة عمل وصول الوكيل" lightbox="../../media/defender/m365-defender-mcas-architecture-d.png":::

في هذا الرسم التوضيحي:
- يتم توجيه الوصول إلى تطبيقات السحابة المعتمدة من المستخدمين والأجهزة في مؤسستك من خلال Defender for Cloud Apps.
- يسمح وصول الوكيل هذا بتطبيق عناصر تحكم جلسة العمل.
- لا تتأثر تطبيقات السحابة التي لم تفرض عليك العقوبات أو غير الملغاة بشكل صريح.

تسمح لك عناصر التحكم في جلسة العمل بتطبيق المعلمات على كيفية استخدام مؤسستك لتطبيقات السحابة. على سبيل المثال، إذا كانت مؤسستك تستخدم Salesforce، يمكنك تكوين نهج جلسة عمل يسمح فقط للأجهزة المدارة بالوصول إلى بيانات مؤسستك في Salesforce. مثال أبسط يمكن أن يكون تكوين نهج لمراقبة نسبة استخدام الشبكة من الأجهزة غير المدارة حتى تتمكن من تحليل مخاطر حركة المرور هذه قبل تطبيق نهج أكثر صرامة.

#### <a name="integrating-with-azure-ad-with-conditional-access-app-control"></a>التكامل مع Azure AD مع التحكم بتطبيق الوصول المشروط

قد تكون لديك بالفعل تطبيقات SaaS مضافة إلى مستأجر Azure AD لفرض المصادقة متعددة العوامل ونهج الوصول المشروط الأخرى. يتكامل Microsoft Defender for Cloud Apps أصلا مع Azure AD. كل ما عليك القيام به هو تكوين نهج في Azure AD لاستخدام التحكم في تطبيق الوصول المشروط في Defender for Cloud Apps. يؤدي هذا إلى توجيه نسبة استخدام الشبكة لتطبيقات SaaS المدارة هذه من خلال Defender for Cloud Apps كوكيل، مما يسمح ل Defender for Cloud Apps بمراقبة نسبة استخدام الشبكة هذه وتطبيق عناصر التحكم في جلسة العمل. 

:::image type="content" source="../../media/defender/m365-defender-mcas-architecture-e.png" alt-text="تصميم Microsoft Defender for Cloud Apps - تطبيقات SaaS" lightbox="../../media/defender/m365-defender-mcas-architecture-e.png":::

في هذا الرسم التوضيحي:
- يتم دمج تطبيقات SaaS مع مستأجر Azure AD. يسمح هذا التكامل Azure AD بفرض نهج الوصول المشروط، بما في ذلك المصادقة متعددة العوامل.
- تتم إضافة نهج إلى Azure Active Directory لتوجيه نسبة استخدام الشبكة لتطبيقات SaaS إلى Defender for Cloud Apps. يحدد النهج تطبيقات SaaS التي يجب تطبيق هذا النهج عليها. لذلك، بعد Azure AD يفرض أي نهج وصول مشروط تنطبق على تطبيقات SaaS هذه، Azure AD ثم يوجه (وكلاء) حركة مرور الجلسة من خلال Defender for Cloud Apps.
- يراقب Defender for Cloud Apps نسبة استخدام الشبكة هذه ويطبق أي نهج للتحكم في جلسة العمل التي تم تكوينها من قبل المسؤولين. 

قد تكون اكتشفت تطبيقات سحابية وفرضت عليها العقوبات باستخدام Defender for Cloud Apps التي لم تتم إضافتها إلى Azure AD. يمكنك الاستفادة من التحكم في تطبيق الوصول المشروط عن طريق إضافة تطبيقات السحابة هذه إلى مستأجر Azure AD ونطاق قواعد الوصول المشروط.

#### <a name="protecting-your-organization-from-hackers"></a>حماية مؤسستك من المتسللين

يوفر Defender for Cloud Apps حماية قوية من تلقاء نفسه. ومع ذلك، عند دمجها مع القدرات الأخرى Microsoft 365 Defender، يوفر Defender for Cloud Apps البيانات في الإشارات المشتركة التي تساعد (معا) على إيقاف الهجمات.

يجدر تكرار هذا الرسم التوضيحي من النظرة العامة إلى هذا التقييم Microsoft 365 Defender والدليل التجريبي. 

:::image type="content" source="../../media/defender/m365-defender-eval-threat-chain.png" alt-text="كيف Microsoft 365 Defender إيقاف سلسلة من التهديدات" lightbox="../../media/defender/m365-defender-eval-threat-chain.png":::

مع التركيز على الجانب الأيسر من هذا الرسم التوضيحي، Microsoft Defender for Cloud Apps تلاحظ سلوكا غير طبيعي مثل السفر المستحيل أو الوصول إلى بيانات الاعتماد والتنزيل غير العادي أو مشاركة الملفات أو نشاط إعادة توجيه البريد ويبلغ فريق الأمان عن هذه السلوكيات. لذلك، يساعد Defender for Cloud Apps على منع الحركة الجانبية من قبل المتسللين واختراق البيانات الحساسة. يرتبط Microsoft 356 Defender for Cloud بالإشارات من جميع المكونات لتوفير قصة الهجوم الكاملة.

## <a name="understand-key-concepts"></a>فهم المفاهيم الرئيسية

حدد الجدول التالي المفاهيم الرئيسية التي من المهم فهمها عند تقييم Microsoft Defender for Cloud Apps وتكوينها ونشرها.


|مفهوم  |الوصف |معلومات إضافية  |
|---------|---------|---------|
| لوحة معلومات Defender for Cloud Apps | يقدم نظرة عامة على أهم المعلومات حول مؤسستك ويعطي روابط إلى تحقيق أعمق.        | [العمل مع لوحة المعلومات ](/cloud-app-security/daily-activities-to-protect-your-cloud-environment)       |
| التحكم في تطبيق الوصول المشروط    | عكس بنية الوكيل التي تتكامل مع موفر الهوية (IdP) لمنح نهج الوصول المشروط Azure AD وفرض عناصر التحكم في جلسة العمل بشكل انتقائي.        |  [حماية التطبيقات باستخدام Microsoft Defender for Cloud Apps Conditional Access App Control](/cloud-app-security/proxy-intro-aad)       |
|  كتالوج تطبيقات السحابة   | يوفر لك "كتالوج تطبيقات السحابة" صورة كاملة مقابل كتالوج Microsoft لأكثر من 16000 تطبيق سحابي تم تصنيفها وتسجيلها استنادا إلى أكثر من 80 عامل خطر.    |  [العمل مع درجات مخاطر التطبيق](/cloud-app-security/risk-score)       |
| لوحة معلومات اكتشاف السحابة    | يحلل Cloud Discovery سجلات نسبة استخدام الشبكة الخاصة بك وقد تم تصميمه لإعطاء مزيد من التحليلات حول كيفية استخدام تطبيقات السحابة في مؤسستك بالإضافة إلى إعطاء التنبيهات ومستويات المخاطر.     |  [العمل مع التطبيقات المكتشفة   ](/cloud-app-security/discovered-apps)    |
|التطبيقات المتصلة |يوفر Defender for Cloud Apps حماية من طرف إلى طرف للتطبيقات المتصلة باستخدام تكامل السحابة إلى السحابة وموصلات واجهة برمجة التطبيقات وعناصر التحكم في الوصول في الوقت الحقيقي وجلسات العمل باستخدام عناصر التحكم في الوصول إلى التطبيقات الشرطية. |[حماية التطبيقات المتصلة](/cloud-app-security/protect-connected-apps) |
| | | |

## <a name="review-architecture-requirements"></a>مراجعة متطلبات البنية

### <a name="discovering-cloud-apps"></a>اكتشاف تطبيقات السحابة

لاكتشاف تطبيقات السحابة المستخدمة في بيئتك، يمكنك تنفيذ أحد الأسلوبين التاليين أو كليهما:

- يمكنك بدء الاستخدام والتشغيل بسرعة باستخدام Cloud Discovery من خلال التكامل مع Microsoft Defender لنقطة النهاية. يمكنك هذا التكامل الأصلي من البدء فورا في جمع البيانات حول حركة مرور السحابة عبر Windows 11 والأجهزة Windows 10، على شبكتك وخارجها.
- لاكتشاف جميع تطبيقات السحابة التي يتم الوصول إليها من قبل جميع الأجهزة المتصلة بشبكتك، قم بنشر مجمع سجل Defender for Cloud Apps على جدران الحماية والوكلاء الآخرين. يساعد هذا النشر على جمع البيانات من نقاط النهاية الخاصة بك ويرسلها إلى Defender for Cloud Apps للتحليل. يتكامل Defender for Cloud Apps في الأصل مع بعض وكلاء الجهات الخارجية للحصول على المزيد من القدرات.

يتم تضمين هذه الخيارات في [الخطوة 2. تمكين بيئة التقييم](eval-defender-mcas-enable-eval.md). 

### <a name="applying-azure-ad-conditional-access-policies-to-cloud-apps"></a>تطبيق نهج الوصول المشروط Azure AD على تطبيقات السحابة

يتطلب التحكم في تطبيق الوصول المشروط (القدرة على تطبيق نهج الوصول المشروط على تطبيقات السحابة) التكامل مع Azure AD. هذا التكامل ليس شرطا لبدء استخدام Defender for Cloud Apps. إنها خطوة نشجعك على تجربتها أثناء المرحلة التجريبية - [الخطوة 3. Microsoft Defender for Cloud Apps التجريبية](eval-defender-mcas-pilot.md).

## <a name="siem-integration"></a>تكامل إدارة معلومات الأمان والأحداث

يمكنك دمج Microsoft Defender for Cloud Apps مع خادم SIEM العام أو مع Microsoft Sentinel لتمكين المراقبة المركزية للتنبيهات والأنشطة من التطبيقات المتصلة. 

بالإضافة إلى ذلك، يتضمن Microsoft Sentinel موصلا Microsoft Defender for Cloud Apps لتوفير تكامل أعمق مع Microsoft Sentinel. يتيح لك هذا الترتيب ليس فقط الحصول على رؤية في تطبيقات السحابة الخاصة بك ولكن أيضا الحصول على تحليلات متطورة لتحديد التهديدات الإلكترونية ومكافحتها والتحكم في كيفية انتقال بياناتك.

- [تكامل SIEM العام](/cloud-app-security/siem)
- [تنبيهات الدفق وسجلات اكتشاف السحابة من Defender for Cloud Apps إلى Microsoft Sentinel](/azure/sentinel/connect-cloud-app-security)

### <a name="next-steps"></a>الخطوات التالية

الخطوة 2 من 3: [تمكين بيئة التقييم Microsoft Defender for Cloud Apps](eval-defender-mcas-enable-eval.md)

العودة إلى النظرة العامة لتقييم [Microsoft Defender for Cloud Apps](eval-defender-mcas-overview.md)

العودة إلى النظرة العامة لتقييم [Microsoft 365 Defender](eval-overview.md)
