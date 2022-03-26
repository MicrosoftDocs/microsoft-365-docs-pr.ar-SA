---
title: نشر الحماية من برامج الفدية الضارة لمستأجر Microsoft 365 الخاص بك
author: dansimp
f1.keywords:
- NOCSH
ms.author: dansimp
manager: dansimp
audience: ITPro
ms.topic: article
ms.prod: microsoft-365-enterprise
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
- Strat_O365_Enterprise
- ransomware
- m365solution-ransomware
- m365solution-overview
ms.custom: seo-marvel-jun2020
keywords: برامج الفدية الضارة، برامج الفدية الضارة التي يتم تشغيلها من قبل الإنسان، برامج الفدية الضارة التي يتم تشغيلها من قبل الإنسان، هامور، هجوم مهين، هجوم برامج الفدية الضارة، التشفير، علم الفيروسات المشفرة، الثقة الصفرية
description: خطوة من خلال حماية مواردك Microsoft 365 من هجمات برامج الفدية الضارة.
ms.openlocfilehash: c356a0e3fac83c77a7e1eb1eda6e169405f43863
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/08/2022
ms.locfileid: "63570834"
---
# <a name="deploy-ransomware-protection-for-your-microsoft-365-tenant"></a>نشر الحماية من برامج الفدية الضارة لمستأجر Microsoft 365 الخاص بك

برامج الفدية الضارة هي نوع من الهجمات غير الضارة التي تدمر الملفات والمجلدات أو تشفيرها، مما يمنع الوصول إلى البيانات الهامة. عادة ما تنتشر برامج الفدية الضارة السلعية مثل فيروس ينقل الفيروسات إلى الأجهزة ويتطلب فقط معالجة البرامج الضارة. برامج الفدية الضارة التي يتم تشغيلها بواسطة الإنسان هي نتيجة هجوم نشط من قبل مجرمي الإنترنت الذين يتسللون إلى البنية الأساسية المحلية أو السحابية ل IT في المؤسسة، ويرفعون امتيازاتهم، وينشرون برامج الفدية الضارة إلى البيانات الهامة.

بمجرد اكتمال الهجوم، يطلب مهاجم أموالا من ضحيتين مقابل الملفات المحذوفة، أو مفاتيح فك تشفير الملفات المشفرة، أو وعدا ب عدم تحرير البيانات الحساسة إلى الويب الداكن أو الإنترنت العام. يمكن أيضا استخدام برامج الفدية الضارة التي يتم تشغيلها من قبل الإنسان لإيقاف تشغيل الأجهزة أو العمليات الهامة، مثل تلك اللازمة للإنتاج الصناعي، مع إيقاف العمليات التجارية العادية حتى يتم دفع الفدية وتصحيح الضرر، أو تقوم المؤسسة بمعالجة الضرر نفسه.

يمكن أن يكون هجوم برامج الفدية الضارة الذي يتم تشغيله من قبل الإنسان كارثيا للشركات من جميع الأحجام ويصعب تنظيفه، مما يتطلب حماية كاملة من برامج الفدية الضارة للحماية من الهجمات المستقبلية. بخلاف برامج الفدية الضارة السلعية، يمكن أن تستمر برامج الفدية الضارة التي يتم تشغيلها من قبل الإنسان في تهديد عمليات الشركات بعد طلب الفدية الأولي.

>[!Note]
>يفترض هجوم برامج الفدية الضارة على مستأجر Microsoft 365 أن المهاجم لديه بيانات اعتماد حساب مستخدم صالحة لمستأجر وأن لديه حق الوصول إلى كل الملفات والموارد المسموح بها لحساب المستخدم. يجب على المهاجم الذي لا تتوفر لديه بيانات اعتماد حساب مستخدم صالحة فك تشفير البيانات التي تم تشفيرها بواسطة Microsoft 365 التشفير الافتراضي والمحسن. لمزيد من المعلومات، راجع [التشفير و نظرة عامة حول الإدارة الأساسية](/compliance/assurance/assurance-encryption). 
>

لمزيد من المعلومات حول الحماية من برامج الفدية الضارة عبر منتجات Microsoft، راجع موارد [برامج الفدية الضارة الإضافية هذه](#additional-ransomware-resources).

## <a name="security-in-the-cloud-is-a-partnership"></a>الأمان في السحابة هو شراكة

إن أمان خدمات Microsoft السحابية هو شراكة بينك وبين Microsoft:

- لقد تم بناء خدمات Microsoft السحابية على أساس الثقة والأمان. توفر لك Microsoft قدرات وإمكانيات عناصر التحكم في الأمان لمساعدتك على حماية البيانات والتطبيقات.
- أنت تملك بياناتك وهوياتك ومسؤولية حمايتها، والأمان الخاص بالموارد المحلية، والأمان لمكونات السحابة التي تتحكم بها.

ومن خلال دمج هذه القدرات والمسؤوليات، يمكننا توفير أفضل حماية من هجوم برامج الفدية الضارة.

## <a name="ransomware-mitigation-and-recovery-capabilities-provided-with-microsoft-365"></a>إمكانات تخفيف برامج الفدية الضارة واستردادها المتوفرة مع Microsoft 365

يمكن لمهاجم برامج الفدية الضارة الذي قام Microsoft 365 المستأجر بامراق مؤسستك للحصول على فدية عن طريق:

- حذف الملفات أو البريد الإلكتروني
- تشفير الملفات في مكانها
- نسخ الملفات خارج نطاق المستأجر (حذف البيانات)

ومع ذلك، Microsoft 365 الخدمات عبر الإنترنت العديد من الإمكانات المضمنة و عناصر التحكم لحماية بيانات العملاء من هجمات برامج الفدية الضارة. توفر الأقسام التالية ملخصا. لمزيد من التفاصيل حول كيفية حماية Microsoft لبيانات العملاء والبرامج الضارة وحماية برامج الفدية [الضارة في](/compliance/assurance/assurance-malware-and-ransomware-protection) Microsoft 365.

>[!Note]
>يفترض هجوم برامج الفدية الضارة على مستأجر Microsoft 365 أن المهاجم لديه بيانات اعتماد حساب مستخدم صالحة لمستأجر وأن لديه حق الوصول إلى كل الملفات والموارد المسموح بها لحساب المستخدم. يجب على المهاجم الذي لا تتوفر لديه بيانات اعتماد حساب مستخدم صالحة فك تشفير البيانات التي تم تشفيرها بواسطة Microsoft 365 التشفير الافتراضي والمحسن. لمزيد من المعلومات، راجع [التشفير و نظرة عامة حول الإدارة الأساسية](/compliance/assurance/assurance-encryption). 
>

### <a name="deleting-files-or-email"></a>حذف الملفات أو البريد الإلكتروني

الملفات الموجودة SharePoint OneDrive for Business محمية بواسطة:

- الإصدار 

   Microsoft 365 على ما لا يقل عن 500 إصدار من ملف بشكل افتراضي ويمكن تكوينه للاحتفاظ المزيد. 

   لتقليل العبئ على الأمان ومساعدة فريق العمل، تدرب المستخدمين على كيفية استعادة [الإصدارات السابقة من الملفات](https://support.microsoft.com/office/restore-a-previous-version-of-an-item-or-file-in-sharepoint-f66dbda0-81f4-4d1e-b08c-793265c58934).

- سلة المعاد تدويرها

   إذا أنشأت برامج الفدية الضارة نسخة مشفرة جديدة من الملف وحذفت الملف القديم، فإن العملاء لديهم 93 يوما لاستعادته من سلة المحذف. بعد مرور 93 يوما، هناك نافذة 14 يوما حيث لا تزال Microsoft تستطيع استرداد البيانات. 
  
   لتقليل العبئ على الأمان ومساعدة فريق العمل، قم بتدريب المستخدمين على كيفية استعادة الملفات من [سلة المعاد تدويرها](https://support.microsoft.com/office/restore-deleted-items-from-the-site-collection-recycle-bin-5fa924ee-16d7-487b-9a0a-021b9062d14b).

- [استعادة الملفات](https://support.microsoft.com/office/restore-your-onedrive-fa231298-759d-41cf-bcd0-25ac53eb8a15)

   حل كامل لاسترداد الخدمة الذاتية SharePoint OneDrive يسمح للمسؤولين والمستخدمين باستعادة الملفات من أي وقت خلال آخر 30 يوما.

   لتقليل العبئ على الأمان وموظفي المساعدة في استخدام المعلومات، تدرب المستخدمين على [استعادة الملفات](https://support.microsoft.com/office/restore-your-onedrive-fa231298-759d-41cf-bcd0-25ac53eb8a15).


بالنسبة OneDrive ملفات SharePoint، يمكن لشركة Microsoft العودة إلى نقطة سابقة في الوقت المحدد لمدة تصل إلى 14 يوما إذا تعرضت لهجمات جماعية.

البريد الإلكتروني محمي من خلال:

- [استرداد عنصر واحد واستبقاء](/exchange/recipients-in-exchange-online/manage-user-mailboxes/enable-or-disable-single-item-recovery) علبة البريد، حيث يمكنك استرداد العناصر الموجودة في علبة البريد عند حذفها عن غير قصد أو ضار. يمكنك استرداد رسائل البريد المحذوفة في غضون 14 يوما بشكل افتراضي، ويمكن تكوينها حتى 30 يوما.

- [تسمح لك سياسات الاستبقاء](/exchange/security-and-compliance/messaging-records-management/retention-tags-and-policies) بالاحتفاظ بنسخ غير قابلة للحفظ من البريد الإلكتروني لفترة الاستبقاء التي تم تكوينها.

### <a name="encrypting-files-in-place"></a>تشفير الملفات في مكانها

كما هو موضح مسبقا، الملفات الموجودة في SharePoint OneDrive for Business محمية من التشفير الضار باستخدام:

- الإصدار
- سلة المعاد تدويرها
- مكتبة "الاحتفاظ بالمحفظة"

للحصول على مزيد من التفاصيل، راجع [التعامل مع تلف البيانات في Microsoft 365](/compliance/assurance/assurance-dealing-with-data-corruption).

### <a name="copying-files-outside-your-tenant"></a>نسخ الملفات خارج نطاق المستأجر 

يمكنك منع مهاجم برامج الفدية الضارة من نسخ الملفات خارج نطاق المستأجر باستخدام:

- [سياسات منع فقدان البيانات (DLP)](/microsoft-365/compliance/dlp-learn-about-dlp)

    الكشف عن مشاركة البيانات التي تحتوي على:

    - المعلومات الشخصية مثل معلومات التعريف الشخصية (PII) للتوافق مع لوائح الخصوصية الإقليمية.

    - معلومات المؤسسة السرية استنادا إلى تسميات الحساسية.

- [Microsoft Defender لتطبيقات السحابة](/cloud-app-security/what-is-cloud-app-security)

    حظر تنزيلات المعلومات الحساسة مثل الملفات. 

    يمكنك أيضا استخدام سياسات جلسات العمل ل [Defender for Cloud Apps Conditional Access App Control](/cloud-app-security/tutorial-dlp#how-to-discover-and-protect-sensitive-information-in-your-organization) لمراقبة تدفق المعلومات بين مستخدم وتطبيق في الوقت الحقيقي.

## <a name="whats-in-this-solution"></a>ما هو في هذا الحل

يسحبك هذا الحل من خلال نشر ميزات الحماية وتخفيف Microsoft 365 والتكوينات والعمليات الجارية لتقليل قدرة مهاجم برامج الفدية الضارة على استخدام البيانات الهامة في مستأجر Microsoft 365 مع الاستمرار في مؤسستك للحصول على فدية.

![خطوات الحماية من برامج الفدية الضارة باستخدام Microsoft 365](../media/ransomware-protection-microsoft-365/ransomware-protection-microsoft-365-step-grid.png)

الخطوات في هذا الحل هي:

1. [تكوين خطوط الأمان الأساسية](ransomware-protection-microsoft-365-security-baselines.md)
2. [نشر الكشف عن الهجمات والاستجابة لها](ransomware-protection-microsoft-365-attack-detection-response.md)
3. [حماية الهويات](ransomware-protection-microsoft-365-identities.md)
4. [حماية الأجهزة](ransomware-protection-microsoft-365-devices.md)
5. [حماية المعلومات](ransomware-protection-microsoft-365-information.md)

فيما يلي الخطوات الخمس للحل الذي تم نشره Microsoft 365 المستأجر.

![الحماية من برامج الفدية الضارة لمستأجر Microsoft 365 مستأجر](../media/ransomware-protection-microsoft-365/ransomware-protection-microsoft-365-architecture.png)

يستخدم هذا الحل مبادئ [الثقة الصفرية](/security/zero-trust/): 

- **تحقق بشكل صريح:** المصادقة والتفويض دائما استنادا إلى كل نقاط البيانات المتوفرة.
- **استخدام أقل وصول للامتيازات:** تقييد وصول المستخدمين باستخدام Just-In-Time و Just-Enough-Access (JIT/JEA) ونهج التكييف المستندة إلى المخاطر وحماية البيانات.
- **افترض خرق:** تقليل نصف قطر الناسف والوصول إلى المقطع. تحقق من التشفير النهائي واستخدام التحليلات للحصول على الرؤية، والكشف عن تهديدات محرك الأقراص، وتحسين الدفاعات.

بخلاف الوصول التقليدي إلى الإنترانت، الذي يثق في كل شيء خلف جدار الحماية الخاص بأي مؤسسة، يعامل Zero Trust كل تسجيل دخول والوصول كما لو كان منبثقا من شبكة غير خاضعة للتحكم، سواء كان ذلك خلف جدار حماية المؤسسة أو على الإنترنت. يتطلب "الثقة الصفرية" الحماية للشبكة والبنية الأساسية والهويات ونقاط النهاية والتطبيقات والبيانات.

## <a name="microsoft-365-capabilities-and-features"></a>Microsoft 365 وميزات

لحماية المستأجر Microsoft 365 من هجوم برامج الفدية الضارة، استخدم هذه Microsoft 365 وميزات هذه الخطوات في الحل.

### <a name="1-security-baseline"></a>1. أساس الأمان

| الإمكانية أو الميزة | الوصف | يساعد... | الترخيص |
|:-------|:-----|:-------|:-------|
| Microsoft Secure Score |  يقيس الوضع الأمني لمستأجر Microsoft 365 المستأجر. | تقييم تكوين الأمان واقتراح التحسينات. | Microsoft 365 E3 أو Microsoft 365 E5 |
| قواعد تقليل الأجزاء المعرضة للهجوم | يقلل من ضعف مؤسستك أمام الهجمات الإلكترونية باستخدام مجموعة متنوعة من إعدادات التكوين. | حظر النشاط المريب والمحتوى المعرض. | Microsoft 365 E3 أو Microsoft 365 E5 |
| Exchange البريد الإلكتروني |  تمكين الخدمات التي تقلل من ضعف مؤسستك أمام هجوم مستند إلى البريد الإلكتروني. | منع الوصول الأولي إلى المستأجر من خلال التصيد الاحتيالي وهجمة أخرى مستندة إلى البريد الإلكتروني.  | Microsoft 365 E3 أو Microsoft 365 E5 |
| تطبيقات Windows Microsoft Edge و Microsoft 365 Apps إعدادات المؤسسة | يوفر تكوينات أمان قياسية في المجال معروفة على نطاق واسع ومعاينة بشكل جيد. | منع الهجمات عبر Windows و Edge و Microsoft 365 Apps ل Enterprise. | Microsoft 365 E3 أو Microsoft 365 E5 |
|

### <a name="2-detection-and-response"></a>2. الكشف والاستجابة

| الإمكانية أو الميزة | الوصف | يساعد على الكشف عن... | الترخيص |
|:-------|:-----|:-------|:-------|
| Microsoft 365 Defender | يجمع بين الإشارات وإمكانيات التكاتف في حل واحد. <br><br> تمكن محترفي الأمان من جمع إشارات الخطر معا وتحديد النطاق الكامل للتهديد وتأثيره. <br><br> أتمتة الإجراءات لمنع الهجوم أو إيقافه والتئام علب البريد ونقاط النهاية وهويات المستخدم المتأثرة ذاتيا. | الأحداث، وهي التنبيهات المدمجة والبيانات التي تكو هجمة. | Microsoft 365 E5 أو Microsoft 365 E3 باستخدام الأمان في Microsoft 365 E5 الإضافية |
| Microsoft Defender for Identity |  يقوم بتحديد التهديدات المتقدمة والهويات المتهكة والإجراءات الضارة ل insider الموجهة إلى مؤسستك من خلال واجهة أمان مستندة إلى السحابة، كما يستخدم إشارات خدمات مجال Active Directory (AD DS) المحلية. | اختراق بيانات الاعتماد الخاصة وحسابات AD DS. | Microsoft 365 E5 أو Microsoft 365 E3 باستخدام الأمان في Microsoft 365 E5 الإضافية |
| Microsoft Defender Office 365 | يحمي مؤسستك من التهديدات الضارة التي تشكلها رسائل البريد الإلكتروني والربط (عناوين URL) وأدوات التعاون. <br><br> يحمي من البرامج الضارة والتصيد الاحتيالي والخادع وأنواع الهجمات الأخرى. | هجمات التصيد الاحتيالي. | Microsoft 365 E5 أو Microsoft 365 E3 باستخدام الأمان في Microsoft 365 E5 الإضافية |
| Microsoft Defender لنقطة النهاية | تمكين الكشف عن التهديدات المتقدمة والاستجابة لها عبر نقاط النهاية (الأجهزة). | تثبيت البرامج الضارة و اختراق الجهاز. | Microsoft 365 E5 أو Microsoft 365 E3 باستخدام الأمان في Microsoft 365 E5 الإضافية |
| حماية هوية Azure Active Directory (Azure AD) | أتمتة عملية الكشف عن المخاطر المستندة إلى الهوية وتحري تلك المخاطر وتوضيتها. | اختراق بيانات الاعتماد الخاصة وحسابات Azure AD وتصعيد الامتيازات. | Microsoft 365 E5 أو Microsoft 365 E3 باستخدام الأمان في Microsoft 365 E5 الإضافية |
| Defender for Cloud Apps | وسيط أمان الوصول السحابي للاكتشاف، والتحري، والحوكمة عبر جميع خدمات السحابة الخاصة بك من Microsoft و الجهة الخارجية. | الحركة اللاحقة وملء البيانات. | Microsoft 365 E5 أو Microsoft 365 E3 باستخدام الأمان في Microsoft 365 E5 الإضافية |
|

### <a name="3-identities"></a>3. الهويات

| الإمكانية أو الميزة | الوصف | يساعد على منع... | الترخيص |
|:-------|:-----|:-------|:-------|
|حماية كلمة مرور Azure AD | حظر كلمات المرور من قائمة شائعة وإد إدخالات مخصصة. | تحديد كلمة مرور حساب المستخدم في السحابة أو المستخدمين. |Microsoft 365 E3 أو Microsoft 365 E5|
|فرض MFA باستخدام "الوصول المشروط" | يتطلب MFA استنادا إلى خصائص تسجيل دخول المستخدم باستخدام سياسات الوصول الشرطي. | اختراق بيانات الاعتماد والوصول إليها. | Microsoft 365 E3 أو Microsoft 365 E5|
|فرض MFA باستخدام الوصول الشرطي المستند إلى المخاطر | يتطلب MFA استنادا إلى مخاطر تسجيل الدخول من قبل المستخدم باستخدام حماية هوية Azure AD. |اختراق بيانات الاعتماد والوصول إليها. | Microsoft 365 E5 أو Microsoft 365 E3 باستخدام الأمان في Microsoft 365 E5 الإضافية|
|

### <a name="4-devices"></a>4. الأجهزة

لإدارة الأجهزة والتطبيقات:

| الإمكانية أو الميزة | الوصف | يساعد على منع... | الترخيص |
|:-------|:-----|:-------|:-------|
| Microsoft Intune | إدارة الأجهزة والتطبيقات التي يتم تشغيلها عليها.  | اختراق الجهاز أو التطبيق والوصول إليه. | Microsoft 365 E3 أو E5 |
|  |  |  |  |

بالنسبة Windows 11 أو 10 أجهزة:

| الإمكانية أو الميزة | الوصف | يساعد... | الترخيص |
|:-------|:-----|:-------|:-------|
| جدار الحماية ل Microsoft Defender | يوفر جدار حماية مستند إلى المضيف.  | منع الهجمات من حركة مرور الشبكة الواردة وغير المرغوب فيها. | Microsoft 365 E3 أو Microsoft 365 E5 |
| برنامج الحماية من الفيروسات من Microsoft Defender | يوفر الحماية من البرامج الضارة للأجهزة (نقاط النهاية) باستخدام التعلم الآلي وتحليل البيانات الكبيرة وأبحاث معمقة لمقاومة المخاطر والبنية الأساسية لسحابة Microsoft. | منع تثبيت البرامج الضارة وتشغيلها. | Microsoft 365 E3 أو Microsoft 365 E5 |
| Microsoft Defender SmartScreen | يحمي من التصيد الاحتيالي أو مواقع الويب والبرامج الضارة والتطبيقات، وتنزيل الملفات التي يحتمل أن تكون ضارة. | الحظر أو التحذير عند التحقق من المواقع والتنزيلها والتطبيقات والملفات. | Microsoft 365 E3 أو Microsoft 365 E5 |
| Microsoft Defender لنقطة النهاية | يساعد على منع التهديدات المتقدمة والكشف عنها والكشف عنها والاستجابة لها عبر الأجهزة (نقاط النهاية). | الحماية من التلاعب بالشبكة. | Microsoft 365 E5 أو Microsoft 365 E3 باستخدام الأمان في Microsoft 365 E5 الإضافية |
|  |  |  |  |

### <a name="5-information"></a>5. المعلومات

| الإمكانية أو الميزة | الوصف | يساعد... | الترخيص |
|:-------|:-----|:-------|:-------|
| الوصول إلى المجلدات الخاضعة للتحكم | يحمي بياناتك من خلال التحقق من التطبيقات من قائمة التطبيقات المعروفة الموثوق بها. | منع تعديل الملفات أو تشفيرها بواسطة برامج الفدية الضارة. | Microsoft 365 E3 أو Microsoft 365 E5 |
| حماية البيانات في Microsoft | تمكين تطبيق تسميات الحساسية على المعلومات القابلة للفدية | منع استخدام المعلومات التي تم تبادلها. | Microsoft 365 E3 أو Microsoft 365 E5 |
| منع فقدان البيانات (DLP) | يحمي البيانات الحساسة ويقلل من المخاطر من خلال منع المستخدمين من مشاركتها بشكل غير مناسب. | منع عملية exfiltration للبيانات. | Microsoft 365 E3 أو Microsoft 365 E5 |
| Defender for Cloud Apps | وسيط أمان الوصول السحابي للاكتشاف والتحري والحوكمة. | الكشف عن الحركة اللاحقة ومنع عملية ازاله البيانات. | Microsoft 365 E5 أو Microsoft 365 E3 باستخدام الأمان في Microsoft 365 E5 الإضافية |
|

## <a name="impact-on-users-and-change-management"></a>التأثير على المستخدمين وإدارة التغيير

قد يؤثر نشر ميزات الأمان الإضافية وتطبيق المتطلبات ونهج الأمان Microsoft 365 المستأجر على المستخدمين. 

على سبيل المثال، يمكنك فرض نهج أمان جديد يتطلب من المستخدمين إنشاء فرق جديدة خاصة باستخدام قائمة حسابات المستخدمين كأعضاء، بدلا من إنشاء فريق لجميع المستخدمين في المؤسسة بسهولة أكبر. من الممكن أن يساعد هذا الأمر على منع مهاجم برامج الفدية الضارة من استكشاف الفرق غير المتوفرة لحساب المستخدم المساس للمهاجم واستهداف موارد ذلك الفريق في الهجوم اللاحق.

سيحدد حل الأساس هذا متى يمكن أن تؤثر عمليات التكوين الجديدة أو سياسات الأمان الموصى بها على المستخدمين حتى تتمكن من تنفيذ إدارة التغيير المطلوبة.

## <a name="next-steps"></a>الخطوات التالية

استخدم هذه الخطوات لنشر حماية شاملة لمستأجر Microsoft 365 الخاص بك:

1. [تكوين خطوط الأمان الأساسية](ransomware-protection-microsoft-365-security-baselines.md)
2. [نشر الكشف عن الهجمات والاستجابة لها](ransomware-protection-microsoft-365-attack-detection-response.md)
3. [حماية الهويات](ransomware-protection-microsoft-365-identities.md)
4. [حماية الأجهزة](ransomware-protection-microsoft-365-devices.md)
5. [حماية المعلومات](ransomware-protection-microsoft-365-information.md)

[![الخطوة 1 للحماية من برامج الفدية الضارة باستخدام Microsoft 365](../media/ransomware-protection-microsoft-365/ransomware-protection-microsoft-365-step1.png)](ransomware-protection-microsoft-365-security-baselines.md)

## <a name="additional-ransomware-resources"></a>موارد برامج الفدية الضارة الإضافية

المعلومات الأساسية من Microsoft:

- [التهديدات المتزايدة التي تشكلها برامج الفدية الضارة](https://blogs.microsoft.com/on-the-issues/2021/07/20/the-growing-threat-of-ransomware/)، نشر مدونة Microsoft حول المشاكل في 20 يوليو 2021
- [برامج الفدية الضارة التي يتم تشغيلها من قبل الإنسان](/security/compass/human-operated-ransomware)
- [الحماية السريعة من برامج الفدية الضارة وافيروسات الفدية الضارة](/security/compass/protect-against-ransomware)
- [تقرير الدفاع الرقمي ل Microsoft 2021](https://www.microsoft.com/security/business/microsoft-digital-defense-report) (راجع الصفحات من 10 إلى 19)
- [برامج الفدية الضارة: تقرير](https://security.microsoft.com/threatanalytics3/05658b6c-dc62-496d-ad3c-c6a795a33c27/overview) تحليل التهديدات المستمرة والمستمرة في مدخل Microsoft 365 Defender
- نهج برامج الفدية الضارة الخاصة بفريق الاستجابة والكشف من Microsoft (DART) [وأفضل الممارسات](/security/compass/incident-response-playbook-dart-ransomware-approach) [و دراسة الحالة](/security/compass/dart-ransomware-case-study)

Microsoft 365:

- [زيادة مرونة برامج الفدية الضارة باستخدام Azure Microsoft 365](https://azure.microsoft.com/resources/maximize-ransomware-resiliency-with-azure-and-microsoft-365/)
- [الاستعادة من هجوم برامج الفدية الضارة](/microsoft-365/security/office-365-security/recover-from-ransomware)
- [الحماية من البرامج الضارة وفيروسات الفدية الضارة](/compliance/assurance/assurance-malware-and-ransomware-protection)
- [حماية الكمبيوتر الشخصي Windows 10 من برامج الفدية الضارة](https://support.microsoft.com//windows/protect-your-pc-from-ransomware-08ed68a7-939f-726c-7e84-a72ba92c01c3)
- [التعامل مع برامج الفدية الضارة في SharePoint Online](/sharepoint/troubleshoot/security/handling-ransomware-in-sharepoint-online)
- [تقارير تحليلات المخاطر الخاصة بفيروسات الفدية](https://security.microsoft.com/threatanalytics3?page_size=30&filters=tags%3DRansomware&ordering=-lastUpdatedOn&fields=displayName,alertsCount,impactedEntities,reportType,createdOn,lastUpdatedOn,tags,flag) الضارة في مدخل Microsoft 365 Defender

Microsoft 365 Defender:

- [البحث عن برامج الفدية الضارة مع الصيد المتقدم](/microsoft-365/security/defender/advanced-hunting-find-ransomware)

Microsoft Azure:

- [هجوم Azure Defenses for Ransomware](https://azure.microsoft.com/resources/azure-defenses-for-ransomware-attack/)
- [زيادة مرونة برامج الفدية الضارة باستخدام Azure Microsoft 365](https://azure.microsoft.com/resources/maximize-ransomware-resiliency-with-azure-and-microsoft-365/)
- [خطة النسخ الاحتياطي والاستعادة للحماية من برامج الفدية الضارة](/security/compass/backup-plan-to-protect-against-ransomware)
- [المساعدة في الحماية من برامج الفدية الضارة باستخدام Microsoft Azure Backup](https://www.youtube.com/watch?v=VhLOr2_1MCg) (فيديو لمدة 26 دقيقة)
- [الاستعادة من اختراق الهوية المهينة](/azure/security/fundamentals/recover-from-identity-compromise)
- [الكشف المتقدم عن الهجمات متعددة الكواليس في Microsoft Sentinel](/azure/sentinel/fusion#ransomware)
- [الكشف عن الفدية الضارة في Microsoft Sentinel](https://techcommunity.microsoft.com/t5/azure-sentinel/what-s-new-fusion-detection-for-ransomware/ba-p/2621373)

Microsoft Defender لتطبيقات السحابة:

-  [إنشاء سياسات الكشف عن الشذوذ في Defender for Cloud Apps](/cloud-app-security/anomaly-detection-policy)

منشورات مدونة فريق أمان Microsoft:

- [3 خطوات لمنع برامج الفدية الضارة واستردادها (سبتمبر 2021)](https://www.microsoft.com/security/blog/2021/09/07/3-steps-to-prevent-and-recover-from-ransomware/)
- [دليل لمكافحة برامج الفدية الضارة التي يتم تشغيلها من قبل الإنسان: الجزء 1 (سبتمبر 2021)](https://www.microsoft.com/security/blog/2021/09/20/a-guide-to-combatting-human-operated-ransomware-part-1/)

  الخطوات الأساسية حول كيفية إدارة فريق الكشف والاستجابة (DART) من Microsoft لإجراء عمليات التحقيق في أحداث برامج الفدية الضارة.

- [دليل لمكافحة برامج الفدية الضارة التي يتم تشغيلها من قبل الإنسان: الجزء 2 (سبتمبر 2021)](https://www.microsoft.com/security/blog/2021/09/27/a-guide-to-combatting-human-operated-ransomware-part-2/)

  التوصيات وأفضل الممارسات.

- [أن تصبح مرنا من خلال فهم مخاطر الأمن الإلكتروني: الجزء 4 — التنقل عبر التهديدات الحالية (مايو 2021)](https://www.microsoft.com/security/blog/2021/05/26/becoming-resilient-by-understanding-cybersecurity-risks-part-4-navigating-current-threats/)

  راجع قسم **برامج الفدية** الضارة.

- [هجمات برامج الفدية الضارة التي يتم تشغيلها من قبل الإنسان: كارثة يمكن تفاديها (مارس 2020)](https://www.microsoft.com/security/blog/2020/03/05/human-operated-ransomware-attacks-a-preventable-disaster/)

  يتضمن تحليلات سلسلة الهجمات للهجمات الفعلية.

- [استجابة برامج الفدية الضارة - للدفع أو عدم الدفع؟ (ديسمبر 2019)](https://www.microsoft.com/security/blog/2019/12/16/ransomware-response-to-pay-or-not-to-pay/)
- [تستجيب Norsk Hydro لهجمات برامج الفدية الضارة بشفافية (ديسمبر 2019)](https://www.microsoft.com/security/blog/2019/12/17/norsk-hydro-ransomware-attack-transparency/)
