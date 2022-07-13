---
title: تقييم Microsoft 365 Defender وتجربتها، وهو حل XDR
description: ما هو أمان XDR؟ كيف يمكنك تقييم Microsoft XDR في Microsoft 365 Defender؟ استخدم سلسلة المدونات هذه لتخطيط بيئة الاختبار التجريبي أو التجربة Microsoft 365 Defender لاختبار حل أمان مصمم لحماية الأجهزة والهوية والبيانات والتطبيقات وتجربته. ابدأ رحلة الأمان السيبراني ل XDR هنا وابدأ هذا الاختبار إلى الإنتاج.
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
- zerotrust-solution
ms.topic: conceptual
ms.technology: m365d
ms.openlocfilehash: 5256a578abb515f7d8d2d6e73b5a01fe71404dd0
ms.sourcegitcommit: 61b22df76e0f81e5ef11c587b129287886151c79
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/12/2022
ms.locfileid: "66750067"
---
# <a name="evaluate-and-pilot-microsoft-365-defender"></a>تقييم Microsoft 365 Defender وإعداد إصدار تجريبي منه

**ينطبق على:**

- Microsoft 365 Defender

## <a name="how-this-article-series-works"></a>كيفية عمل سلسلة المقالات هذه

تم تصميم هذه السلسلة من المقالات لترشدك خلال العملية بأكملها لإعداد بيئة XDR تجريبية، من *طرف إلى طرف*، حتى تتمكن من تقييم ميزات وإمكانيات Microsoft 365 Defender وحتى الترويج لبيئة التقييم مباشرة إلى الإنتاج عندما تكون جاهزا وإذا كنت جاهزا.

إذا كنت جديدا في التفكير في XDR، يمكنك مسح هذه المقالات المرتبطة 7 ضوئيا للتعرف على مدى شمولية الحل.

- [كيفية إنشاء البيئة](eval-create-eval-environment.md)
- إعداد كل تقنية من تقنيات Microsoft XDR هذه أو التعرف عليها
  - [Microsoft Defender للهوية](eval-defender-identity-overview.md)
  - [Microsoft Defender ل Office](eval-defender-office-365-overview.md)
  - [مشكلات الأداء في Microsoft Defender لنقطة النهاية](eval-defender-endpoint-overview.md)
  - [Microsoft Defender for Cloud Apps](eval-defender-mcas-overview.md)
- [كيفية التحقيق والاستجابة باستخدام XDR هذا](eval-defender-investigate-respond.md)
- [ترقية بيئة الإصدار التجريبي إلى الإنتاج](eval-defender-promote-to-production.md)

## <a name="microsoft-365-defender-is-a-microsoft-xdr-cyber-security-solution"></a>Microsoft 365 Defender هو حل أمان إلكتروني من Microsoft XDR

Microsoft 365 Defender هو **حل الكشف والاستجابة eXtended (XDR)** الذي يجمع تلقائيا بيانات الإشارة والتهديدات والتنبيهات ويربطها ويحللها من *خلال* بيئة Microsoft 365، بما *في ذلك نقطة النهاية والبريد الإلكتروني والتطبيقات والهويات*. فهو يستفيد من الذكاء الاصطناعي (الذكاء الاصطناعي) والأتمتة لإيقاف الهجمات *تلقائيا* ، ومعالجة الأصول المتأثرة في حالة آمنة.

فكر في XDR كخطوة تالية في الأمان، ونقطة النهاية الموحدة (الكشف عن نقطة النهاية والاستجابة لها أو EDR)، والبريد الإلكتروني، والتطبيق، وأمان الهوية في مكان واحد.

## <a name="microsoft-recommendations-for-evaluating-microsoft-365-defender"></a>توصيات Microsoft لتقييم Microsoft 365 Defender

توصي Microsoft بإنشاء تقييمك في اشتراك إنتاج موجود من Office 365. بهذه الطريقة سوف تحصل على رؤى في العالم الحقيقي على الفور ويمكنك ضبط الإعدادات للعمل ضد التهديدات الحالية في بيئتك. بعد اكتساب الخبرة والراحة مع النظام الأساسي، ما عليك سوى ترقية كل مكون، واحدا تلو الآخر، إلى الإنتاج.

## <a name="the-anatomy-of-a-cyber-security-attack"></a>تشريح هجوم أمني عبر الإنترنت

Microsoft 365 Defender هي مجموعة دفاع مؤسسة مستندة إلى السحابة وموحدة وما قبل الاختراق وما بعدها. وهو ينسق *الوقاية* *والكشف* *والتحقيق* *والاستجابة* عبر نقاط النهاية والهويات والتطبيقات والبريد الإلكتروني والتطبيقات التعاونية وجميع بياناتها.

في هذا التوضيح، هناك هجوم جار. يصل البريد الإلكتروني للتصيد الاحتيالي إلى علبة الوارد الخاصة بموظف في مؤسستك، يفتح مرفق البريد الإلكتروني دون علم. يؤدي ذلك إلى تثبيت البرامج الضارة، ما يؤدي إلى سلسلة من الأحداث التي قد تنتهي بسرقة البيانات الحساسة. ولكن في هذه الحالة، Defender لـ Office 365 قيد التشغيل.

:::image type="content" source="../../media/defender/m365-defender-eval-threat-chain.png" alt-text="محاولات الهجوم المختلفة" lightbox="../../media/defender/m365-defender-eval-threat-chain.png":::

في الرسم التوضيحي:

- **Exchange Online Protection**، جزء من Microsoft Defender لـ Office 365، يمكنه الكشف عن البريد الإلكتروني للتصيد الاحتيالي واستخدام قواعد تدفق البريد للتأكد من عدم وصوله إلى علبة الوارد.
- **Defender لـ Office 365** تختبر المرفقات الآمنة المرفق وتحدد أنه ضار، وبالتالي فإن البريد الذي يصل إما غير قابل للتنفيذ من قبل المستخدم، أو تمنع النهج وصول البريد على الإطلاق.
- يدير **Defender لنقطة النهاية** الأجهزة التي تتصل بشبكة الشركة ويكتشف ثغرات الجهاز والشبكة التي قد يتم استغلالها بخلاف ذلك.
- يدون **Defender for Identity** التغييرات المفاجئة في الحساب مثل تصعيد الامتيازات أو الحركة الجانبية عالية المخاطر. كما أنه يبلغ عن مشكلات الهوية التي تم استغلالها بسهولة مثل تفويض Kerberos غير المقيد، لتصحيحها من قبل فريق الأمان.
- **Microsoft Defender for Cloud Apps** تلاحظ سلوكا غير طبيعي مثل السفر المستحيل أو الوصول إلى بيانات الاعتماد والتنزيل غير العادي أو مشاركة الملفات أو نشاط إعادة توجيه البريد ويبلغ فريق الأمان عن ذلك.

### <a name="microsoft-365-defender-components-secure-devices-identity-data-and-applications"></a>مكونات Microsoft 365 Defender أجهزة وهوية وبيانات وتطبيقات آمنة

تتكون Microsoft 365 Defender من تقنيات الأمان هذه، وتعمل جنبا إلى جنب. لا تحتاج إلى جميع هذه المكونات للاستفادة من قدرات XDR Microsoft 365 Defender. ستحقق المكاسب والكفاءات من خلال استخدام واحد أو اثنين أيضا.

|مكون|الوصف|مادة مرجعية|
|---|---|---|
|Microsoft Defender للهوية|يستخدم Microsoft Defender for Identity إشارات Active Directory لتحديد التهديدات المتقدمة والهويات المخترقة والإجراءات الداخلية الضارة الموجهة إلى مؤسستك واكتشافها والتحقيق فيها.|[ما هو Microsoft Defender للهوية؟](/defender-for-identity/what-is)|
|Exchange Online Protection|Exchange Online Protection هي خدمة ترحيل وتصفية SMTP الأصلية المستندة إلى السحابة التي تساعد على حماية مؤسستك من البريد العشوائي والبرامج الضارة.|[نظرة عامة على Exchange Online Protection (EOP) - Office 365](../office-365-security/overview.md)|
|Microsoft Defender لـ Office 365|Microsoft Defender لـ Office 365 يحمي مؤسستك من التهديدات الضارة التي تشكلها رسائل البريد الإلكتروني والارتباطات (عناوين URL) وأدوات التعاون.|[Microsoft Defender لـ Office 365 - Office 365](../office-365-security/overview.md)|
|Microsoft Defender for Endpoint|Microsoft Defender لنقطة النهاية هو نظام أساسي موحد لحماية الجهاز، والكشف بعد الاختراق، والتحقيق التلقائي، والاستجابة الموصى بها.|[Microsoft Defender لنقطة النهاية - أمان Windows](../defender-endpoint/microsoft-defender-endpoint.md)|
|Microsoft Defender for Cloud Apps|Microsoft Defender for Cloud Apps هو حل شامل عبر SaaS يجلب رؤية عميقة، وعناصر تحكم قوية في البيانات، وحماية محسنة من التهديدات لتطبيقات السحابة الخاصة بك.|[ما هو Defender for Cloud Apps؟](/cloud-app-security/what-is-cloud-app-security)|
|حماية الهوية في Azure AD|تقوم Azure AD Identity Protection بتقييم بيانات المخاطر من مليارات محاولات تسجيل الدخول وتستخدم هذه البيانات لتقييم مخاطر كل تسجيل دخول إلى بيئتك. يتم استخدام هذه البيانات من قبل Azure AD للسماح بالوصول إلى الحساب أو منعه، اعتمادا على كيفية تكوين نهج الوصول المشروط. Azure AD Identity Protection مرخص بشكل منفصل عن Microsoft 365 Defender. يتم تضمينه مع Azure Active Directory Premium P2.|[ما هي Identity Protection؟](/azure/active-directory/identity-protection/overview-identity-protection)|
||||

## <a name="microsoft-365-defender-architecture"></a>تصميم Microsoft 365 Defender

يوضح الرسم التخطيطي أدناه بنية عالية المستوى لمكونات Microsoft 365 Defender الرئيسية والتكاملات. يتم توفير بنية *مفصلة* لكل مكون Defender، وسيناريوهات حالة الاستخدام، خلال هذه السلسلة من المقالات.

:::image type="content" source="../../media/defender/m365-defender-eval-architecture.png" alt-text="بنية عالية المستوى لمدخل Microsoft 365 Defender" lightbox="../../media/defender/m365-defender-eval-architecture.png":::

في هذا الرسم التوضيحي:

- Microsoft 365 Defender يجمع بين الإشارات من جميع مكونات Defender لتوفير الكشف الموسع والاستجابة (XDR) عبر المجالات. يتضمن ذلك قائمة انتظار موحدة للحوادث، والاستجابة التلقائية لإيقاف الهجمات، والمعالجة الذاتية (للأجهزة المخترقة وهويات المستخدمين وعلب البريد)، والتتبع عبر التهديدات، وتحليلات التهديدات.
- Microsoft Defender لـ Office 365 تحمي مؤسستك من التهديدات الضارة التي تشكلها رسائل البريد الإلكتروني والارتباطات (عناوين URL) وأدوات التعاون. وهو يشارك الإشارات الناتجة عن هذه الأنشطة مع Microsoft 365 Defender. يتم دمج Exchange Online Protection (EOP) لتوفير الحماية الشاملة لرسائل البريد الإلكتروني والمرفقات الواردة.
- يجمع Microsoft Defender for Identity الإشارات من الخوادم التي تعمل ب Active Directory Federated Services (AD FS) وخدمات المجال Active Directory محلي (AD DS). ويستخدم هذه الإشارات لحماية بيئة الهوية المختلطة الخاصة بك، بما في ذلك الحماية من المتسللين الذين يستخدمون الحسابات المخترقة للتنقل لاحقا عبر محطات العمل في البيئة المحلية.
- Microsoft Defender لنقطة النهاية يجمع الإشارات من الأجهزة التي تستخدمها مؤسستك ويحميها.
- Microsoft Defender for Cloud Apps يجمع إشارات من استخدام مؤسستك لتطبيقات السحابة ويحمي البيانات المتدفقة بين بيئتك وهذه التطبيقات، بما في ذلك تطبيقات السحابة المعتمدة وغير المفروضة.
- تقوم Azure AD Identity Protection بتقييم بيانات المخاطر من مليارات محاولات تسجيل الدخول وتستخدم هذه البيانات لتقييم مخاطر كل تسجيل دخول إلى بيئتك. يتم استخدام هذه البيانات من قبل Azure AD للسماح بالوصول إلى الحساب أو منعه، اعتمادا على كيفية تكوين نهج الوصول المشروط. Azure AD Identity Protection مرخص بشكل منفصل عن Microsoft 365 Defender. يتم تضمينه مع Azure Active Directory Premium P2.

## <a name="microsoft-siem-and-soar-can-use-data-from-microsoft-365-defender"></a>يمكن ل Microsoft SIEM وSOAR استخدام البيانات من Microsoft 365 Defender

مكونات البنية الاختيارية الإضافية غير مضمنة في هذا الرسم التوضيحي:

- **يمكن دمج بيانات الإشارة المفصلة من جميع مكونات Microsoft 365 Defender في Microsoft Sentinel** ودمجها مع مصادر التسجيل الأخرى لتقديم إمكانات وتفاصيل SIEM وSOAR الكاملة.
- **لمزيد من القراءة حول استخدام Microsoft Sentinel، وهو AZURE SIEM، مع Microsoft 365 Defender** ك XDR، ألق نظرة على [مقالة النظرة العامة](/azure/sentinel/microsoft-365-defender-sentinel-integration) هذه [وخطوات تكامل](/azure/sentinel/connect-microsoft-365-defender?tabs=MDE) Microsoft Sentinel Microsoft 365 Defender.
- لمزيد من المعلومات حول SOAR في Microsoft Sentinel (بما في ذلك ارتباطات أدلة المبادئ في مستودع Microsoft Sentinel GitHub)، يرجى قراءة [هذه المقالة](/azure/sentinel/automate-responses-with-playbooks).

## <a name="the-evaluation-process-for-microsoft-365-defender-cyber-security"></a>عملية التقييم Microsoft 365 Defender الأمن السيبراني

توصي Microsoft بتمكين مكونات Microsoft 365 بالترتيب الموضح:

:::image type="content" source="../../media/defender/m365-defender-eval-process.png" alt-text="عملية تقييم عالية المستوى في مدخل Microsoft 365 Defender" lightbox="../../media/defender/m365-defender-eval-process.png":::

يصف الجدول التالي هذا الرسم التوضيحي.

|  الرقم التسلسلي   |خطوه  |الوصف  |
|------|---------|---------|
|1     | [إنشاء بيئة التقييم](eval-create-eval-environment.md)       |تضمن هذه الخطوة حصولك على الترخيص التجريبي Microsoft 365 Defender.         |
|2     | [تمكين Defender for Identity](eval-defender-identity-overview.md)        | راجع متطلبات البنية، وتمكين التقييم، وتصفح البرامج التعليمية لتحديد ومعالجة أنواع الهجمات المختلفة.   |
|3     | [تمكين Defender لـ Office 365 ](eval-defender-office-365-overview.md)       | تأكد من تلبية متطلبات البنية وتمكين التقييم ثم إنشاء بيئة الإصدار التجريبي. يتضمن هذا المكون Exchange Online Protection وهكذا ستقوم بالفعل بتقييم *كليهما* هنا.      |
|4     | [تمكين Defender لنقطة النهاية ](eval-defender-endpoint-overview.md)       | تأكد من تلبية متطلبات البنية وتمكين التقييم ثم إنشاء بيئة الإصدار التجريبي.         |
|5     | [تمكين Microsoft Defender for Cloud Apps](eval-defender-mcas-overview.md)        |  تأكد من تلبية متطلبات البنية وتمكين التقييم ثم إنشاء بيئة الإصدار التجريبي.        |
|6     | [التحقق من التهديدات والاستجابة لها](eval-defender-investigate-respond.md)        |   محاكاة هجوم والبدء في استخدام قدرات الاستجابة للحوادث.      |
|7     | [ترقية الإصدار التجريبي إلى الإنتاج](eval-defender-promote-to-production.md)        | ترقية مكونات Microsoft 365 إلى الإنتاج واحدا تلو الآخر.        |

هذا أمر موصى به عادة مصمم للاستفادة من قيمة القدرات بسرعة استنادا إلى مقدار الجهد المطلوب عادة لنشر القدرات وتكوينها. على سبيل المثال، يمكن تكوين Defender لـ Office 365 في وقت أقل من الوقت المستغرق لتسجيل الأجهزة في Defender لنقطة النهاية. بالطبع، يجب عليك تحديد أولويات المكونات لتلبية احتياجات عملك، ويمكن تمكينها بترتيب مختلف.

## <a name="go-to-the-next-step"></a>الانتقال إلى الخطوة التالية

[التعرف على بيئة التقييم Microsoft 365 Defender و/أو إنشائها](eval-create-eval-environment.md)
