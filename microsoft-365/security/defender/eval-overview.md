---
title: تقييم حل XDR Microsoft 365 Defender تجريبي
description: ما هو أمان XDR؟ كيف يمكنك تقييم Microsoft XDR في Microsoft 365 Defender؟ استخدم سلسلة المدونة هذه لتخطط Microsoft 365 Defender التجريبية أو الاختبارية لاختبار حل أمان مصمم لحماية الأجهزة والهوية والبيانات والتطبيقات واختباره. ابدأ رحلة الأمن الإلكتروني ل XDR هنا واختبر هذا الاختبار للإنتاج.
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: tracyp
author: MSFTTracyP
ms.date: 06/25/2021
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365solution-overview
- m365solution-evalutatemtp
ms.topic: conceptual
ms.technology: m365d
ms.openlocfilehash: 2502a4781e9844fca8de3113d64ee1836efddabd
ms.sourcegitcommit: 677dcc74aa898b2a17eb8430a32e675fea4e3fe5
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/17/2022
ms.locfileid: "63574387"
---
# <a name="evaluate-and-pilot-microsoft-365-defender"></a>تقييم التقييم Microsoft 365 Defender

**ينطبق على:**

- Microsoft 365 Defender

## <a name="how-this-article-series-works"></a>كيفية عمل سلسلة المقالة هذه

تم تصميم هذه السلسلة من المقالات لتخطو خطواتك خلال عملية إعداد بيئة XDR تجريبية، من نهاية إلى نهاية، بحيث يمكنك تقييم ميزات وإمكانات Microsoft 365 Defender وحتى ترقية بيئة التقييم مباشرة إلى الإنتاج عندما تكون جاهزا وإذا كنت جاهزا.

إذا كنت تفكر في XDR للمرة الجديدة، يمكنك فحص هذه المقالات السبع المرتبطة للحصول على شعور حول مدى شمولية الحل.

- [كيفية إنشاء البيئة](eval-create-eval-environment.md)
- إعداد أو التعرف على كل تقنية من تقنيات Microsoft XDR هذه
  - [Microsoft Defender for Identity](eval-defender-identity-overview.md)
  - [Microsoft Defender Office](eval-defender-office-365-overview.md)
  - [Microsoft Defender لنقطة النهاية](eval-defender-endpoint-overview.md)
  - [Microsoft Defender لتطبيقات السحابة](eval-defender-mcas-overview.md)
- [كيفية التحقق والرد باستخدام XDR هذا](eval-defender-investigate-respond.md)
- [الترويج لبيئة الإصدار التجريبي للإنتاج](eval-defender-promote-to-production.md)

## <a name="microsoft-365-defender-is-a-microsoft-xdr-cyber-security-solution"></a>Microsoft 365 Defender هو حل أمان Microsoft XDR عبر الإنترنت

Microsoft 365 Defender هو حل للكشف والاستجابة **(XDR)** تم استنيره يجمع بيانات الإشارة والتهديد والتنبيه ويجمعها ويحللها تلقائيا من بيئة Microsoft 365، بما في ذلك نقطة النهاية  والبريد الإلكتروني والتطبيقات والهويات *.* فهي تستفيد من الذكاء الاصطناعي (AI) والتلقائي  لإيقاف الهجمات تلقائيا، وتحول الأصول المتأثرة إلى حالة آمنة.

فكر في XDR كخطوة تبويب في الأمان وتوحيد نقطة النهاية (الكشف عن تهديدات نقاط النهاية والرد عليها أو الكشف التلقائي والاستجابة على النقط النهائية) والبريد الإلكتروني والتطبيق والأمان الهويات في مكان واحد.

## <a name="microsoft-recommendations-for-evaluating-microsoft-365-defender"></a>توصيات Microsoft لتقييم Microsoft 365 Defender

توصي Microsoft بإنشاء تقييمك في اشتراك إنتاج موجود Office 365. بهذه الطريقة، ستكتسب أفكارا حول العالم الحقيقي على الفور، كما يمكنك ضبط الإعدادات للعمل على مكافحة التهديدات الحالية في بيئتك. بعد اكتسابك التجربة وراحتك مع النظام الأساسي، ما عليك سوى ترقية كل مكون، واحدا تلو الآخر، إلى الإنتاج.

## <a name="the-anatomy-of-a-cyber-security-attack"></a>تشريح هجوم أمان عبر الإنترنت

Microsoft 365 Defender مجموعة الدفاع الخاصة بالمؤسسات المستندة إلى السحابة والموحدة والمستندة إلى ما قبل الخرق وبعده. وهو ينسق *المنع والكشف* *والتحري* والاستجابة عبر نقاط النهاية والهويات والتطبيقات والبريد الإلكتروني والتطبيقات التعاونية وكل بياناتها. 

في هذا الرسم التوضيحي، هناك هجوم قيد التقدم. يصل البريد الإلكتروني التصيد الاحتيالي إلى علبة الوارد الخاصة بموظف في مؤسستك، يفتح مرفق البريد الإلكتروني دون أن يدري. يؤدي ذلك إلى تثبيت البرامج الضارة، مما يؤدي إلى سلسلة من الأحداث التي قد تنتهي بسرقة البيانات الحساسة. ولكن في هذه الحالة، يكون Defender for Office 365 في العملية.

![كيف Microsoft 365 Defender سلسلة من التهديدات.](../../media/defender/m365-defender-eval-threat-chain.png)

في الرسم التوضيحي:

- **Exchange Online Protection**، وهو جزء من Microsoft Defender for Office 365، الكشف عن البريد الإلكتروني التصيد الاحتيالي واستخدام قواعد تدفق البريد للتأكد من عدم وصولها أبدا إلى علبة الوارد.
- يختبر **Office 365** عن المرفقات الآمنة المرفق ويحدد أنه ضار، وبالتالي فإن البريد الذي يصل إما لا يكون قابلا للتنفيذ من قبل المستخدم، أو تمنع السياسات وصول البريد على الإطلاق.
- **يدير Defender for Endpoint** الأجهزة التي تتصل بشبكة الشركة ويكشف عن الثغرات في الجهاز والشبكات التي قد يتم استغلالها بخلاف ذلك.
- **يأخذ Defender for Identity** في الاعتبار التغييرات المفاجئة في الحساب مثل تصاعد الامتيازات أو الحركة اللاحقة عالية المخاطر. كما أنه يقدم تقارير حول مشاكل الهوية التي يتم استغلالها بسهولة مثل التفويض غير المقيد في Kerberos، لتصحيحها من قبل فريق الأمان.
- **يلاحظ Microsoft Defender for Cloud Apps** سلوكا غريبا مثل السفر المستحيل والوصول إلى بيانات الاعتماد والتنزيل غير المعتاد أو مشاركة الملفات أو نشاط إعادة توجيه البريد ويرسل هذه المعلومات إلى فريق الأمان.

### <a name="microsoft-365-defender-components-secure-devices-identity-data-and-applications"></a>Microsoft 365 Defender المكونات الآمنة للأجهزة والهوية والبيانات والتطبيقات

Microsoft 365 Defender من تقنيات الأمان هذه، التي تعمل جنبا إلى جنب. لست بحاجة إلى كل هذه المكونات للاستفادة من قدرات XDR Microsoft 365 Defender. ستدرك المكاسب والفعالية من خلال استخدام واحد أو اثنين أيضا.

|مكون|الوصف|المادة المرجعية|
|---|---|---|
|Microsoft Defender for Identity|يستخدم Microsoft Defender for Identity إشارات Active Directory لتحديد التهديدات المتقدمة والهويات المضرة والإجراءات الضارة ل insider الموجهة إلى مؤسستك والكشف عنها التحقيق فيها.|[ما هو Microsoft Defender for Identity؟](/defender-for-identity/what-is)|
|Exchange Online Protection|Exchange Online Protection هي خدمة ترحيل SMTP الأصلية المستندة إلى السحابة وتصفيتها التي تساعد على حماية مؤسستك من البريد العشوائي والبرامج الضارة.|[Exchange Online Protection (EOP) - Office 365](../office-365-security/overview.md)|
|Microsoft Defender Office 365|يحمي Microsoft Defender Office 365 مؤسستك من التهديدات الضارة التي تفرضها رسائل البريد الإلكتروني والربط (عناوين URL) وأدوات التعاون.|[Microsoft Defender Office 365 - Office 365](../office-365-security/overview.md)|
|Microsoft Defender لنقطة النهاية|Microsoft Defender ل Endpoint هو نظام أساسي موحد لحماية الجهاز، والكشف بعد الخرق، والتحري التلقائي، والاستجابة الموصى بها.|[Microsoft Defender لنقطة النهاية - Windows الأمان](../defender-endpoint/microsoft-defender-endpoint.md)|
|Microsoft Defender لتطبيقات السحابة|Microsoft Defender لتطبيقات السحابة هو حل شامل عبر SaaS يوفر رؤية أعمق، وتحكما قويا في البيانات، وحماية محسنة من المخاطر لتطبيقات السحابة.|[ما هو Defender for Cloud Apps؟](/cloud-app-security/what-is-cloud-app-security)|
|حماية هوية Azure AD|تقيم Azure AD Identity Protection بيانات المخاطر من ملايين محاولات تسجيل الدخول وتستخدم هذه البيانات لتقييم مخاطر كل تسجيل الدخول إلى بيئتك. يتم استخدام هذه البيانات بواسطة Azure AD للسماح بالوصول إلى الحساب أو منعه، استنادا إلى كيفية تكوين سياسات الوصول الشرطي. يتم ترخيص Azure AD Identity Protection بشكل منفصل عن Microsoft 365 Defender. يتم تضمينه مع Azure Active Directory Premium P2.|[ما هي حماية الهوية؟](/azure/active-directory/identity-protection/overview-identity-protection)|
||||

## <a name="microsoft-365-defender-architecture"></a>Microsoft 365 Defender التصميم

يوضح الرسم التخطيطي أدناه البنية عالية المستوى للمكونات Microsoft 365 Defender الأساسية. *يتم* توفير تصميم تفصيلي لكل مكون Defender، وسيناريوهات حالة الاستخدام، في سلسلة المقالات هذه.

![Microsoft 365 Defender عالية المستوى.](../../media/defender/m365-defender-eval-architecture.png)

في هذا الرسم التوضيحي:

- Microsoft 365 Defender بين الإشارات من كل مكونات Defender لتوفير استجابة للكشف والاستجابة الموسعة (XDR) عبر المجالات. يشمل ذلك قائمة انتظار موحدة للحوادث، والاستجابة التلقائية لإيقاف الهجمات، والتدبير الذاتي (للأجهزة المعرضة للخطر وهويات المستخدمين، علب البريد)، والصيد عبر التهديدات، وتحليلات التهديدات.
- يحمي Microsoft Defender Office 365 مؤسستك من التهديدات الضارة التي تفرضها رسائل البريد الإلكتروني والربط (عناوين URL) وأدوات التعاون. وهي تشارك الإشارات الناتجة عن هذه الأنشطة مع Microsoft 365 Defender. Exchange Online Protection (EOP) لتوفير حماية شاملة لر واردة من رسائل البريد الإلكتروني والمرفقات.
- يجمع Microsoft Defender for Identity الإشارات من الخوادم التي تقوم بتشغيل خدمات Active Directory المتحدة (AD FS) وخدمات مجال Active Directory المحلية (AD DS). فهو يستخدم هذه الإشارات لحماية بيئة الهوية المختلطة، بما في ذلك الحماية من المتسللين الذين يستخدمون الحسابات المخترقة للتنقل بشكل لاحق عبر محطات العمل في البيئة المحلية.
- يجمع Microsoft Defender for Endpoint الإشارات من الأجهزة التي تستخدمها مؤسستك ويحميها.
- يجمع Microsoft Defender for Cloud Apps الإشارات من استخدام مؤسستك لتطبيقات السحابة ويحمي البيانات المتدفقة بين بيئتك وهذه التطبيقات، بما في ذلك تطبيقات السحابة المفروضة وغير المضمنة.
- تقيم Azure AD Identity Protection بيانات المخاطر من ملايين محاولات تسجيل الدخول وتستخدم هذه البيانات لتقييم مخاطر كل تسجيل الدخول إلى بيئتك. يتم استخدام هذه البيانات بواسطة Azure AD للسماح بالوصول إلى الحساب أو منعه، استنادا إلى كيفية تكوين سياسات الوصول الشرطي. يتم ترخيص Azure AD Identity Protection بشكل منفصل عن Microsoft 365 Defender. يتم تضمينه مع Azure Active Directory Premium P2.

## <a name="microsoft-siem-and-soar-can-use-data-from-microsoft-365-defender"></a>يمكن ل Microsoft SIEM و SOAR استخدام البيانات من Microsoft 365 Defender

مكونات هندسة اختيارية إضافية غير مضمنة في هذا الرسم التوضيحي:

- يمكن دمج بيانات الإشارة المفصلة **من Microsoft 365 Defender في Microsoft Sentinel** ودمجها مع مصادر التسجيل الأخرى لتقديم قدرات SIEM وSAR الكاملة ورؤى.
- لمزيد من القراءة حول استخدام **Microsoft Sentinel، Azure SIEM**، مع Microsoft 365 Defender ك XDR، أطلع على مقالة النظرة العامة هذه [](/azure/sentinel/microsoft-365-defender-sentinel-integration) والخطوات Microsoft 365 Defender Microsoft Sentinel [.](/azure/sentinel/connect-microsoft-365-defender?tabs=MDE)
- لمزيد من المعلومات حول SOAR في Microsoft Sentinel (بما في ذلك الارتباطات إلى دفاتر التشغيل في مستودع Microsoft Sentinel GitHub)، يرجى قراءة [هذه المقالة](/azure/sentinel/automate-responses-with-playbooks).

## <a name="the-evaluation-process-for-microsoft-365-defender-cyber-security"></a>عملية التقييم Microsoft 365 Defender الإنترنت

توصي Microsoft بتمكين مكونات Microsoft 365 بالترتيب الموضح:

![Microsoft 365 Defender عملية تقييم عالية المستوى.](../../media/defender/m365-defender-eval-process.png)

يصف الجدول التالي هذا الرسم التوضيحي.

|الخطوة|ارتباط|الوصف|
|---|---|---|
|1|[إنشاء بيئة التقييم](eval-create-eval-environment.md)|تضمن هذه الخطوة حصولك على الترخيص التجريبي Microsoft 365 Defender.|
|2|[تمكين Defender for Identity](eval-defender-identity-overview.md)|راجع متطلبات التصميم، وتمكين التقييم، وتعرف على البرامج التعليمية للتعرف على أنواع الهجمات المختلفة وتداركها.|
|3|[تمكين Defender Office 365](eval-defender-office-365-overview.md)|تأكد من تلبية متطلبات البنية، وتمكين التقييم، ثم إنشاء بيئة التجربة. يتضمن هذا المكون Exchange Online Protection وبالتالي سيتم تقييم *كليهما* هنا.|
|4|[تمكين Defender لنقطة النهاية](eval-defender-endpoint-overview.md)|تأكد من تلبية متطلبات البنية، وتمكين التقييم، ثم إنشاء بيئة التجربة.|
|5|[تمكين Microsoft Defender لتطبيقات السحابة](eval-defender-mcas-overview.md)|تأكد من تلبية متطلبات البنية، وتمكين التقييم، ثم إنشاء بيئة التجربة.|
|6|[التحقق من التهديدات والاستجابة لها](eval-defender-investigate-respond.md)|محاكاة هجوم والبدء في استخدام قدرات الاستجابة للحوادث.|
|7|[ترقية الإصدار التجريبي إلى إنتاج](eval-defender-promote-to-production.md)|ترقية Microsoft 365 الإنتاجية إلى إنتاج واحد إلى واحد.|
||||

هذا أمر مستحسن بشكل شائع مصمم للاستفادة من قيمة الإمكانات بسرعة استنادا إلى مقدار الجهد المطلوب عادة لنشر القدرات وتكوينها. على سبيل المثال، Office 365 تكوين Defender for Endpoint في وقت أقل من الوقت الذي يستغرقه تسجيل الأجهزة في Defender for Endpoint. وبالطبع، يجب تحديد أولويات المكونات لتلبية احتياجات أعمالك، كما يمكنك تمكينها بترتيب مختلف.

## <a name="go-to-the-next-step"></a>الانتقال إلى الخطوة التالية

[التعرف على و/أو إنشاء Microsoft 365 Defender التقييم](eval-create-eval-environment.md)
