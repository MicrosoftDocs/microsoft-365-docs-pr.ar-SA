---
title: مراجعة متطلبات البنية وبنية Microsoft Defender لتطبيقات السحابة
description: تشرح الرسومات التخطيطية التقنية لتطبيقات السحابة ل Microsoft Defender البنية في Microsoft 365 Defender، مما سيساعدك على إنشاء بيئة تجريبية.
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
ms.topic: conceptual
ms.technology: m365d
ms.openlocfilehash: ed36974ae0f32ebc29360ee1039e93c12b2d85c5
ms.sourcegitcommit: 6f3bc00a5cf25c48c61eb3835ac069e9f41dc4db
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 01/24/2022
ms.locfileid: "63578408"
---
# <a name="review-architecture-requirements-and-key-concepts-for-microsoft-defender-for-cloud-apps"></a>مراجعة متطلبات البنية والمفاهيم الأساسية لتطبيقات السحابة ل Microsoft Defender


**ينطبق على:**

- Microsoft 365 Defender

هذه المقالة هي [الخطوة 1 من 3](eval-defender-mcas-overview.md) في عملية إعداد بيئة التقييم ل Microsoft Defender لتطبيقات السحابة إلى جانب Microsoft 365 Defender. لمزيد من المعلومات حول هذه العملية، راجع [مقالة النظرة العامة](eval-defender-identity-overview.md).

قبل تمكين Microsoft Defender لتطبيقات السحابة، تأكد من فهم البنية ويمكنها تلبية المتطلبات. 

## <a name="understand-the-architecture"></a>فهم البنية

Microsoft Defender for Cloud Apps هو وسيط أمان الوصول السحابي (CASB). تعمل CASBs كبوابة للتوسط في الوصول في الوقت الحقيقي بين مستخدمي المؤسسة وموارد السحابة التي يستخدمونها، أينما كان المستخدمون وبصرف النظر عن الجهاز الذي يستخدمونه. يتكامل Microsoft Defender for Cloud Apps بشكل أصلي مع إمكانات أمان Microsoft، بما في ذلك Microsoft 365 Defender.

بدون Defender for Cloud Apps، تكون تطبيقات السحابة التي تستخدمها مؤسستك غير مستخدمة وغير محمية، كما هو موضح.

![هندسة Microsoft Defender لتطبيقات السحابة.](../../media/defender/m365-defender-mcas-architecture-a.png)

في الرسم التوضيحي:
- لا يتم تنظيم استخدام تطبيقات السحابة من قبل المؤسسة ولا يتم اتقاعه. 
- يقع هذا الاستخدام خارج نطاق الحماية التي تم تحقيقها ضمن مؤسسة مدارة. 

#### <a name="discovering-cloud-apps"></a>اكتشاف تطبيقات السحابة

الخطوة الأولى لإدارة استخدام تطبيقات السحابة هي اكتشاف تطبيقات السحابة التي تستخدمها مؤسستك. يوضح الرسم التخطيطي التالي كيفية عمل اكتشاف السحابة مع Defender for Cloud Apps.

![هندسة Microsoft Defender لتطبيقات السحابة - اكتشاف السحابة.](../../media/defender/m365-defender-mcas-architecture-b.png)

في هذا الرسم التوضيحي، هناك طريقتان يمكن استخدامها لمراقبة حركة مرور الشبكة واكتشاف تطبيقات السحابة التي تستخدمها مؤسستك.
- A. يتكامل "اكتشاف تطبيق السحابة" مع Microsoft Defender لنقطة النهاية بشكل أصلي. يقدم Defender for Endpoint تقارير حول تطبيقات السحابة والخدمات التي يتم الوصول إليها من الأجهزة التي تديرها Windows 10 Windows 11 المعلومات. 
- B. للتغطية على جميع الأجهزة المتصلة بشبكة، يتم تثبيت أداة تسجيل Defender for Cloud Apps على جدران الحماية وغيرها من وكلاء لتجميع البيانات من نقاط النهاية. يتم إرسال هذه البيانات إلى Defender for Cloud Apps لتحليلها.

#### <a name="managing-cloud-apps"></a>إدارة تطبيقات السحابة

بعد اكتشاف تطبيقات السحابة وتحليل سلوك كيفية استخدامها من قبل مؤسستك، يمكنك بدء إدارة تطبيقات السحابة التي تختارها. 

![هندسة Microsoft Defender لتطبيقات السحابة - إدارة تطبيقات السحابة.](../../media/defender/m365-defender-mcas-architecture-c.png)

في هذا الرسم التوضيحي:
- يتم فرض الفرض على بعض التطبيقات للاستخدام. هذه طريقة بسيطة للبداية لإدارة التطبيقات.
- يمكنك تمكين المزيد من الرؤية والتحكم من خلال توصيل التطبيقات بموصلات التطبيقات. تستخدم موصلات التطبيقات واجهات برمجة تطبيقات موفري التطبيقات.


#### <a name="applying-session-controls-to-cloud-apps"></a>تطبيق عناصر تحكم جلسة العمل على تطبيقات السحابة

يعمل Microsoft Defender for Cloud Apps كوكيل عكسي، مما يوفر إمكانية وصول الوكيل إلى تطبيقات السحابة المفروضة. يسمح هذا ل Defender for Cloud Apps بتطبيق عناصر تحكم جلسة العمل التي تقوم بتكوينها. 

![هندسة Microsoft Defender لتطبيقات السحابة - التحكم في جلسة عمل وصول الوكيل.](../../media/defender/m365-defender-mcas-architecture-d.png)

في هذا الرسم التوضيحي:
- يتم توجيه الوصول إلى تطبيقات السحابة المفروضة من المستخدمين والأجهزة في مؤسستك من خلال Defender for Cloud Apps.
- يسمح وصول الوكيل هذا بتطبيق عناصر التحكم في جلسة العمل.
- لا تتأثر تطبيقات السحابة التي لم تفرض عليها أي ملاءمة أو لم تفرض عليها أي موافقة صريحة.

تسمح لك عناصر تحكم جلسة العمل بتطبيق معلمات على كيفية استخدام تطبيقات السحابة من قبل مؤسستك. على سبيل المثال، إذا كانت مؤسستك تستخدم Salesforce، يمكنك تكوين نهج جلسة عمل يسمح فقط للأجهزة المدارة بالوصول إلى بيانات مؤسستك في Salesforce. مثال أبسط يمكن أن يكون تكوين نهج لمراقبة حركة المرور من الأجهزة غير الإدارة حتى تتمكن من تحليل مخاطر حركة المرور هذه قبل تطبيق نهج أكثر صرامة.

#### <a name="integrating-with-azure-ad-with-conditional-access-app-control"></a>التكامل مع Azure AD مع التحكم في تطبيق الوصول الشرطي

قد يكون لديك بالفعل تطبيقات SaaS مضافة إلى مستأجر Azure AD لفرض المصادقة متعددة العوامل ونهج الوصول الشرطي الأخرى. يتكامل Microsoft Defender for Cloud Apps بشكل أصلي مع Azure AD. كل ما عليك فعله هو تكوين نهج في Azure AD لاستخدام "التحكم في تطبيق الوصول الشرطي" في Defender for Cloud Apps. هذا توجيه حركة مرور الشبكة لتطبيقات SaaS المدارة هذه من خلال Defender for Cloud Apps كوكيل، مما يسمح ل Defender for Cloud Apps بمراقبة حركة المرور هذه وتطبيق عناصر التحكم في جلسة العمل. 

![هندسة Microsoft Defender لتطبيقات السحابة - تطبيقات SaaS.](../../media/defender/m365-defender-mcas-architecture-e.png)

في هذا الرسم التوضيحي:
- تتكامل تطبيقات SaaS مع مستأجر Azure AD. يسمح هذا ل Azure AD بفرض نهج الوصول الشرطي، بما في ذلك المصادقة متعددة العوامل.
- يضاف نهج إلى Azure Active Directory لتوجيه حركة المرور لتطبيقات SaaS إلى Defender for Cloud Apps. يحدد النهج تطبيقات SaaS التي يجب تطبيق هذا النهج عليها. وبالتالي، بعد أن يفرض Azure AD أي سياسات وصول شرطي تنطبق على تطبيقات SaaS هذه، يوجه Azure AD بعد ذلك (التكلاء) حركة مرور جلسة العمل من خلال Defender for Cloud Apps.
- يقوم Defender for Cloud Apps بمراقبة حركة المرور هذه ويطبق أي من سياسات التحكم في جلسة العمل التي تم تكوينها من قبل المسؤولين. 

من المحتمل أن تكون قد اكتشفت تطبيقات السحابة التي لم يتم إضافتها إلى Azure AD وفرضت عليها الفرضية عليها. يمكنك الاستفادة من التحكم في تطبيق الوصول الشرطي عن طريق إضافة هذه التطبيقات السحابية إلى مستأجر Azure AD ونطاق قواعد الوصول الشرطي.

#### <a name="protecting-your-organization-from-hackers"></a>حماية مؤسستك من المتسللين

يوفر Defender for Cloud Apps حماية فعالة من تلقاء نفسه. ومع ذلك، عند دمجها مع قدرات Microsoft 365 Defender الأخرى، يوفر Defender for Cloud Apps البيانات في الإشارات المشتركة التي تساعد معا على إيقاف الهجمات.

تجدر الإشارة إلى تكرار هذا الرسم التوضيحي من النظرة العامة Microsoft 365 Defender دليل التقييم والتدليل التجريبي. 

![كيف Microsoft 365 Defender سلسلة من التهديدات.](../../media/defender/m365-defender-eval-threat-chain.png)

عند التركيز على الجانب الأيسر من هذا الرسم التوضيحي، يلاحظ Microsoft Defender for Cloud Apps سلوكا غريبا مثل السفر المستحيل والوصول إلى بيانات الاعتماد والتنزيل غير المعتاد أو مشاركة الملفات أو نشاط إعادة توجيه البريد ويرسل هذه المعلومات إلى فريق الأمان. وبالتالي، يساعد Defender for Cloud Apps على منع التنقلات اللاحقة بواسطة المتسللين وسحب البيانات الحساسة. يرتبط Microsoft 356 Defender for Cloud بين الإشارات من كل المكونات لتوفير قصة الهجوم الكاملة.

## <a name="understand-key-concepts"></a>فهم المفاهيم الأساسية

حدد الجدول التالي المفاهيم الأساسية التي من المهم فهمها عند تقييم Microsoft Defender لتطبيقات السحابة وتكوينه ونشره.


|المفهوم  |الوصف |معلومات إضافية  |
|---------|---------|---------|
| لوحة معلومات Defender for Cloud Apps | يقدم نظرة عامة حول المعلومات الأكثر أهمية حول مؤسستك ويمنح ارتباطات إلى تحقيق أعمق.        | [العمل باستخدام لوحة المعلومات ](/cloud-app-security/daily-activities-to-protect-your-cloud-environment)       |
| التحكم في تطبيق الوصول الشرطي    | عكس بنية الوكيل التي تتكامل مع موفر الهوية (IdP) لإعطاء Azure AD نهج الوصول الشرطي وفرض عناصر تحكم جلسة العمل بشكل انتقائي.        |  [حماية التطبيقات باستخدام Microsoft Defender for Cloud Apps Conditional Access App Control](/cloud-app-security/proxy-intro-aad)       |
|  كتالوج تطبيق السحابة   | يوفر لك كتالوج تطبيقات السحابة صورة كاملة مقابل كتالوج Microsoft لأكثر من 16000 تطبيق سحابي مصنفة ومسجلة استنادا إلى أكثر من 80 عامل خطر.    |  [استخدام نقاط مخاطر التطبيق](/cloud-app-security/risk-score)       |
| لوحة معلومات اكتشاف السحابة    | تحلل Cloud Discovery سجلات حركة المرور الخاصة بك وقد تم تصميمها لإعطاء مزيد من المعلومات حول كيفية استخدام تطبيقات السحابة في مؤسستك بالإضافة إلى تقديم التنبيهات ومستويات المخاطر.     |  [استخدام التطبيقات المكتشفة   ](/cloud-app-security/discovered-apps)    |
|التطبيقات المتصلة |يوفر Defender for Cloud Apps حماية من النهاية إلى النهاية للتطبيقات المتصلة باستخدام تكامل السحابة إلى السحابة وموصلات API والوصول في الوقت الحقيقي وتحكم جلسة العمل والاستفادة من عناصر التحكم بالوصول إلى التطبيقات الشرطية. |[حماية التطبيقات المتصلة](/cloud-app-security/protect-connected-apps) |
| | | |

## <a name="review-architecture-requirements"></a>مراجعة متطلبات البنية

### <a name="discovering-cloud-apps"></a>اكتشاف تطبيقات السحابة

لاكتشاف تطبيقات السحابة المستخدمة في بيئتك، يمكنك القيام بما يلي أو كليهما:

- يمكنك العمل بسرعة مع "اكتشاف السحابة" من خلال التكامل مع Microsoft Defender ل Endpoint. يمكنك هذا التكامل الأصلي من البدء فورا في تجميع البيانات على حركة مرور السحابة عبر Windows 11 وأجهزة Windows 10، على الشبكة أو خارجها.
- لاكتشاف جميع تطبيقات السحابة التي يمكن الوصول إليها من قبل جميع الأجهزة المتصلة بالشبكة، انتشر سجل Defender for Cloud Apps الذي تم تجميعه على جدران الحماية الخاصة بك وغيرها من المحترفين. يجمع هذا البيانات من نقاط النهاية ويرسلها إلى Defender for Cloud Apps لتحليلها. يتكامل Defender for Cloud Apps بشكل أصلي مع بعض تكاملات  الأطراف الخارجية للحصول على المزيد من الإمكانات.

يتم تضمين هذه الخيارات في [الخطوة 2. تمكين بيئة التقييم](eval-defender-mcas-enable-eval.md). 

### <a name="applying-azure-ad-conditional-access-policies-to-cloud-apps"></a>تطبيق سياسات الوصول الشرطي ل Azure AD على تطبيقات السحابة

يتطلب التحكم في تطبيق Access الشرطي (القدرة على تطبيق سياسات الوصول الشرطي على تطبيقات السحابة) التكامل مع Azure AD. هذا ليس شرطا للبدء في استخدام Defender for Cloud Apps. إنها خطوة نشجعك على التجربة أثناء مرحلة التجربة — [الخطوة 3. تجريبي ل Microsoft Defender لتطبيقات السحابة](eval-defender-mcas-pilot.md).

## <a name="siem-integration"></a>تكامل SIEM

يمكنك دمج Microsoft Defender لتطبيقات السحابة مع خادم SIEM العام أو مع Microsoft Sentinel لتمكين المراقبة المركزية للتنبيهات والأنشطة من التطبيقات المتصلة. 

بالإضافة إلى ذلك، يتضمن Microsoft Sentinel موصل Microsoft Defender for Cloud Apps لتوفير تكامل أعمق مع Microsoft Sentinel. يمكنك هذا الأمر ليس فقط من الحصول على الرؤية في تطبيقات السحابة الخاصة بك ولكن أيضا للحصول على تحليلات معقدة للتعرف على الهجمات الإلكترونية ومكافحتها والتحكم في كيفية تنقل البيانات.

- [تكامل SIEM العام](/cloud-app-security/siem)
- [تدفق التنبيهات وسجلات "اكتشاف السحابة" من Defender for Cloud Apps إلى Microsoft Sentinel](/azure/sentinel/connect-cloud-app-security)

### <a name="next-steps"></a>الخطوات التالية

الخطوة 2 من 3: [تمكين بيئة التقييم ل Microsoft Defender لتطبيقات السحابة](eval-defender-mcas-enable-eval.md)

العودة إلى نظرة عامة حول [تقييم Microsoft Defender لتطبيقات السحابة](eval-defender-mcas-overview.md)

العودة إلى النظرة العامة لتقييم التقييم [Microsoft 365 Defender](eval-overview.md)
