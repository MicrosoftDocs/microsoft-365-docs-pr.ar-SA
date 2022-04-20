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
keywords: برامج الفدية الضارة، برامج الفدية الضارة التي يديرها الإنسان، برامج الفدية الضارة التي يديرها الإنسان، هومور، الهجوم الهجمي، هجوم برامج الفدية الضارة، التشفير، فيروسات التشفير، الثقة الصفرية
description: قم بالخطوة من خلال حماية مواردك Microsoft 365 من هجمات برامج الفدية الضارة.
ms.openlocfilehash: fde24132341512d76467284cb2f9c9b11b7d88cc
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/19/2022
ms.locfileid: "64943228"
---
# <a name="deploy-ransomware-protection-for-your-microsoft-365-tenant"></a>نشر الحماية من برامج الفدية الضارة لمستأجر Microsoft 365 الخاص بك

برامج الفدية الضارة هي نوع من الهجمات الضارة التي تتلف الملفات والمجلدات أو تشفرها، ما يمنع الوصول إلى البيانات الهامة. تنتشر برامج الفدية الضارة السلعية عادة مثل فيروس يؤثر على الأجهزة ويتطلب فقط معالجة البرامج الضارة. برامج الفدية الضارة التي يديرها الإنسان هي نتيجة هجوم نشط من قبل المجرمين السيبرانيين الذين يتسللون إلى البنية الأساسية المحلية أو السحابية الخاصة بت تكنولوجيا المعلومات في المؤسسة، ويرفعون امتيازاتهم، وينشرون برامج الفدية الضارة إلى البيانات الهامة.

بمجرد اكتمال الهجوم، يطلب المهاجم أموالا من ضحية مقابل الملفات المحذوفة، أو مفاتيح فك التشفير للملفات المشفرة، أو وعد بعدم تحرير البيانات الحساسة إلى الويب الداكن أو الإنترنت العام. يمكن أيضا استخدام برامج الفدية الضارة التي يديرها الإنسان لإيقاف تشغيل الأجهزة أو العمليات الهامة، مثل تلك اللازمة للإنتاج الصناعي، وإيقاف العمليات التجارية العادية حتى يتم دفع الفدية وتصحيح الضرر، أو تعالج المؤسسة الضرر بنفسها.

يمكن أن يكون هجوم برامج الفدية الضارة التي يديرها الإنسان كارثيا للشركات من جميع الأحجام ويصعب تنظيفه، ما يتطلب إخلاء كامل من الخصوم للحماية من الهجمات المستقبلية. على عكس برامج الفدية الضارة السلعية، يمكن أن تستمر برامج الفدية الضارة التي يديرها الإنسان في تهديد عمليات الشركات بعد طلب الفدية الأولية.

>[!Note]
>يفترض هجوم برامج الفدية الضارة على مستأجر Microsoft 365 أن المهاجم لديه بيانات اعتماد صالحة لحساب المستخدم لمستأجر ولديه حق الوصول إلى جميع الملفات والموارد المسموح بها لحساب المستخدم. يجب على المهاجم الذي ليس لديه أي بيانات اعتماد صالحة لحساب المستخدم فك تشفير البيانات الثابتة التي تم تشفيرها بواسطة Microsoft 365 التشفير الافتراضي والمحسن. لمزيد من المعلومات، راجع [نظرة عامة على التشفير وإدارة المفاتيح](/compliance/assurance/assurance-encryption). 
>

لمزيد من المعلومات حول الحماية من برامج الفدية الضارة عبر منتجات Microsoft، راجع [موارد برامج الفدية الضارة الإضافية](#additional-ransomware-resources) هذه.

## <a name="security-in-the-cloud-is-a-partnership"></a>الأمان في السحابة هو شراكة

أمان خدمات Microsoft السحابية هو شراكة بينك وبين Microsoft:

- تستند خدمات Microsoft السحابية إلى أساس الثقة والأمان. توفر لك Microsoft عناصر تحكم وإمكانات أمان لمساعدتك على حماية بياناتك وتطبيقاتك.
- أنت تملك بياناتك وهوياتك ومسؤولية حمايتها، وأمان مواردك المحلية، وأمان مكونات السحابة التي تتحكم فيها.

من خلال الجمع بين هذه القدرات والمسؤوليات، يمكننا توفير أفضل حماية ضد هجوم برامج الفدية الضارة.

## <a name="ransomware-mitigation-and-recovery-capabilities-provided-with-microsoft-365"></a>قدرات التخفيف من برامج الفدية واستردادها المتوفرة مع Microsoft 365

يمكن لمهاجم برامج الفدية الضارة الذي تسلل إلى مستأجر Microsoft 365 أن يحتفظ بمؤسستك للحصول على فدية عن طريق:

- حذف الملفات أو البريد الإلكتروني
- تشفير الملفات في مكانها
- نسخ الملفات خارج نطاق المستأجر (النقل غير المصرح به للبيانات)

ومع ذلك، Microsoft 365 خدمات الإنترنت لديها العديد من القدرات وعناصر التحكم المضمنة لحماية بيانات العملاء من هجمات برامج الفدية الضارة. توفر الأقسام التالية ملخصا. لمزيد من التفاصيل حول كيفية حماية Microsoft لبيانات العملاء والبرامج [الضارة وحماية برامج الفدية الضارة في Microsoft 365](/compliance/assurance/assurance-malware-and-ransomware-protection).

>[!Note]
>يفترض هجوم برامج الفدية الضارة على مستأجر Microsoft 365 أن المهاجم لديه بيانات اعتماد صالحة لحساب المستخدم لمستأجر ولديه حق الوصول إلى جميع الملفات والموارد المسموح بها لحساب المستخدم. يجب على المهاجم الذي ليس لديه أي بيانات اعتماد صالحة لحساب المستخدم فك تشفير البيانات الثابتة التي تم تشفيرها بواسطة Microsoft 365 التشفير الافتراضي والمحسن. لمزيد من المعلومات، راجع [نظرة عامة على التشفير وإدارة المفاتيح](/compliance/assurance/assurance-encryption). 
>

### <a name="deleting-files-or-email"></a>حذف الملفات أو البريد الإلكتروني

تتم حماية الملفات الموجودة في SharePoint OneDrive for Business بواسطة:

- الاصدارات 

   يحتفظ Microsoft 365 بإصدار 500 إصدار على الأقل من الملف بشكل افتراضي ويمكن تكوينه للاحتفاظ بالمزيد. 

   لتقليل العبء على الأمان وموظفي helpdesk، قم بتدريب المستخدمين على كيفية [استعادة الإصدارات السابقة من الملفات](https://support.microsoft.com/office/restore-a-previous-version-of-an-item-or-file-in-sharepoint-f66dbda0-81f4-4d1e-b08c-793265c58934).

- سلة المحذوفات

   إذا أنشأت برامج الفدية الضارة نسخة مشفرة جديدة من الملف وحذفت الملف القديم، فسيتوفر للعملاء 93 يوما لاستعادتها من سلة المحذوفات. بعد 93 يوما، هناك نافذة لمدة 14 يوما حيث لا يزال بإمكان Microsoft استرداد البيانات. 
  
   لتقليل العبء على الأمان وموظفي مكتب المساعدة، قم بتدريب المستخدمين على كيفية [استعادة الملفات من سلة المحذوفات](https://support.microsoft.com/office/restore-deleted-items-from-the-site-collection-recycle-bin-5fa924ee-16d7-487b-9a0a-021b9062d14b).

- [استعادة الملفات](https://support.microsoft.com/office/restore-your-onedrive-fa231298-759d-41cf-bcd0-25ac53eb8a15)

   حل كامل لاسترداد الخدمة الذاتية SharePoint OneDrive يسمح للمسؤولين والمستخدمين باستعادة الملفات من أي وقت خلال آخر 30 يوما.

   لتقليل العبء على الأمان وموظفي مساعدي تكنولوجيا المعلومات، قم بتدريب المستخدمين على ["استعادة الملفات](https://support.microsoft.com/office/restore-your-onedrive-fa231298-759d-41cf-bcd0-25ac53eb8a15)".


بالنسبة لملفات OneDrive SharePoint، يمكن ل Microsoft العودة إلى نقطة زمنية سابقة لمدة تصل إلى 14 يوما إذا تعرضت لهجوم جماعي.

البريد الإلكتروني محمي بواسطة:

- [استرداد عنصر واحد](/exchange/recipients-in-exchange-online/manage-user-mailboxes/enable-or-disable-single-item-recovery) واستبقاء علبة البريد، حيث يمكنك استرداد العناصر في علبة البريد عند الحذف غير المقصود أو الضار قبل الأوان. يمكنك استعادة رسائل البريد المحذوفة في غضون 14 يوما بشكل افتراضي، ويمكن تكوينها حتى 30 يوما.

- تسمح لك [نهج الاستبقاء](/exchange/security-and-compliance/messaging-records-management/retention-tags-and-policies) بالاحتفاظ بنسخ غير قابلة للتغيير من البريد الإلكتروني لفترة الاستبقاء التي تم تكوينها.

### <a name="encrypting-files-in-place"></a>تشفير الملفات في مكانها

كما هو موضح سابقا، تتم حماية الملفات الموجودة في SharePoint OneDrive for Business من التشفير الضار باستخدام:

- الاصدارات
- سلة المحذوفات
- مكتبة الاحتفاظ

لمزيد من التفاصيل، راجع [التعامل مع تلف البيانات في Microsoft 365](/compliance/assurance/assurance-dealing-with-data-corruption).

### <a name="copying-files-outside-your-tenant"></a>نسخ الملفات خارج نطاق المستأجر 

يمكنك منع مهاجم برامج الفدية الضارة من نسخ الملفات خارج نطاق المستأجر باستخدام:

- [نهج Microsoft Purview Data Loss Prevention (DLP)](/microsoft-365/compliance/dlp-learn-about-dlp)

    الكشف عن المشاركة المحفوفة بالمخاطر أو غير المقصودة أو غير الملائمة للبيانات التي تحتوي على:

    - معلومات شخصية مثل معلومات التعريف الشخصية (PII) للامتثال للوائح الخصوصية الإقليمية.

    - معلومات تنظيم سرية تستند إلى تسميات الحساسية.

- [Microsoft Defender for Cloud Apps](/cloud-app-security/what-is-cloud-app-security)

    حظر تنزيلات المعلومات الحساسة مثل الملفات. 

    يمكنك أيضا استخدام نهج جلسة العمل [ل Defender for Cloud Apps Conditional Access App Control](/cloud-app-security/tutorial-dlp#how-to-discover-and-protect-sensitive-information-in-your-organization) لمراقبة تدفق المعلومات بين مستخدم وتطبيق في الوقت الحقيقي.

## <a name="whats-in-this-solution"></a>ما هو موجود في هذا الحل

يرشدك هذا الحل من خلال نشر ميزات الحماية والتخفيف Microsoft 365 والتكوينات والعمليات الجارية لتقليل قدرة مهاجم برامج الفدية الضارة على استخدام البيانات الهامة في مستأجر Microsoft 365 الخاص بك والاحتفاظ بمؤسستك للحصول على فدية.

![خطوات الحماية من برامج الفدية الضارة باستخدام Microsoft 365](../media/ransomware-protection-microsoft-365/ransomware-protection-microsoft-365-step-grid.png)

الخطوات الواردة في هذا الحل هي:

1. [تكوين أساسات الأمان](ransomware-protection-microsoft-365-security-baselines.md)
2. [نشر الكشف عن الهجمات والاستجابة لها](ransomware-protection-microsoft-365-attack-detection-response.md)
3. [حماية الهويات](ransomware-protection-microsoft-365-identities.md)
4. [حماية الأجهزة](ransomware-protection-microsoft-365-devices.md)
5. [حماية المعلومات](ransomware-protection-microsoft-365-information.md)

فيما يلي الخطوات الخمس للحل المنشور لمستأجر Microsoft 365 الخاص بك.

![حماية برامج الفدية الضارة لمستأجر Microsoft 365](../media/ransomware-protection-microsoft-365/ransomware-protection-microsoft-365-architecture.png)

يستخدم هذا الحل مبادئ [ثقة معدومة](/security/zero-trust/): 

- **تحقق بشكل صريح:** المصادقة والتخويل دائما استنادا إلى جميع نقاط البيانات المتوفرة.
- **استخدام الوصول الأقل امتيازا:** الحد من وصول المستخدم باستخدام Just-In-Time و Just-Enough-Access (JIT/JEA)، والسياسات التكيفية المستندة إلى المخاطر، وحماية البيانات.
- **افترض خرقا:** تقليل نصف قطر التفجير والوصول إلى المقطع. تحقق من التشفير الشامل واستخدم التحليلات للحصول على الرؤية، ودفع الكشف عن التهديدات، وتحسين الدفاعات.

على عكس الوصول التقليدي إلى إنترانت، والذي يثق في كل شيء خلف جدار حماية المؤسسة، ثقة معدومة تعامل كل تسجيل دخول والوصول كما لو كانت تنشأ من شبكة غير خاضعة للرقابة، سواء كانت خلف جدار حماية المؤسسة أو على الإنترنت. يتطلب ثقة معدومة حماية الشبكة والبنية الأساسية والهويات ونقاط النهاية والتطبيقات والبيانات.

## <a name="microsoft-365-capabilities-and-features"></a>Microsoft 365 القدرات والميزات

لحماية مستأجر Microsoft 365 من هجوم برامج الفدية الضارة، استخدم هذه الإمكانات والميزات Microsoft 365 لهذه الخطوات في الحل.

### <a name="1-security-baseline"></a>1. أساس الأمان

| القدرة أو الميزة | الوصف | يساعد... | الترخيص |
|:-------|:-----|:-------|:-------|
| Microsoft Secure Score |  يقيس الوضع الأمني لمستأجر Microsoft 365. | تقييم تكوين الأمان الخاص بك ويقترح تحسينات. | Microsoft 365 E3 أو Microsoft 365 E5 |
| قواعد تقليل الأجزاء المعرضة للهجوم | يقلل من تعرض مؤسستك للهجمات الإلكترونية باستخدام مجموعة متنوعة من إعدادات التكوين. | حظر النشاط المشبوه والمحتوى الضعيف. | Microsoft 365 E3 أو Microsoft 365 E5 |
| إعدادات البريد الإلكتروني Exchange |  تمكين الخدمات التي تقلل من الثغرة الأمنية لمؤسستك في هجوم مستند إلى البريد الإلكتروني. | منع الوصول الأولي إلى المستأجر من خلال التصيد الاحتيالي والهجمات الأخرى المستندة إلى البريد الإلكتروني.  | Microsoft 365 E3 أو Microsoft 365 E5 |
| إعدادات Microsoft Windows و Microsoft Edge و Microsoft 365 Apps للمؤسسات | يوفر تكوينات أمان قياسية في الصناعة معروفة على نطاق واسع ومختبرة جيدا. | منع الهجمات من خلال Windows وEdge Microsoft 365 Apps ل Enterprise. | Microsoft 365 E3 أو Microsoft 365 E5 |
|

### <a name="2-detection-and-response"></a>2. الكشف والاستجابة

| القدرة أو الميزة | الوصف | يساعد على الكشف عن... | الترخيص |
|:-------|:-----|:-------|:-------|
| Microsoft 365 Defender | يجمع بين الإشارات وينسق القدرات في حل واحد. <br><br> تمكين محترفي الأمان من تجميع إشارات التهديد وتحديد النطاق الكامل للتهديدات وتأثيرها. <br><br> أتمتة الإجراءات لمنع الهجوم وعلب البريد ونقاط النهاية وهويات المستخدم المتأثرة أو إيقافها. | الحوادث، وهي التنبيهات والبيانات المدمجة التي تشكل الهجوم. | Microsoft 365 E5 أو Microsoft 365 E3 باستخدام الوظيفة الإضافية الأمان في Microsoft 365 E5 |
| Microsoft Defender for Identity |  يحدد ويكتشف ويتحقق من التهديدات المتقدمة والهويات المخترقة والإجراءات الداخلية الضارة الموجهة إلى مؤسستك من خلال واجهة أمان مستندة إلى السحابة وتستخدم إشارات خدمات المجال Active Directory محلي (AD DS). | اختراق بيانات الاعتماد لحسابات AD DS. | Microsoft 365 E5 أو Microsoft 365 E3 باستخدام الوظيفة الإضافية الأمان في Microsoft 365 E5 |
| Microsoft Defender لـ Office 365 | يحمي مؤسستك من التهديدات الضارة التي تشكلها رسائل البريد الإلكتروني والارتباطات (عناوين URL) وأدوات التعاون. <br><br> الحماية من البرامج الضارة والتصيد الاحتيالي والانتحال وأنواع الهجمات الأخرى. | هجمات التصيد الاحتيالي. | Microsoft 365 E5 أو Microsoft 365 E3 باستخدام الوظيفة الإضافية الأمان في Microsoft 365 E5 |
| Microsoft Defender for Endpoint | تمكين الكشف عن التهديدات المتقدمة والاستجابة لها عبر نقاط النهاية (الأجهزة). | تثبيت البرامج الضارة واختراق الجهاز. | Microsoft 365 E5 أو Microsoft 365 E3 باستخدام الوظيفة الإضافية الأمان في Microsoft 365 E5 |
| Azure Active Directory (Azure AD) Identity Protection | أتمتة الكشف عن المخاطر المستندة إلى الهوية ومعالجتها والتحقيق في تلك المخاطر. | اختراق بيانات الاعتماد لحسابات Azure AD وتصعيد الامتيازات. | Microsoft 365 E5 أو Microsoft 365 E3 باستخدام الوظيفة الإضافية الأمان في Microsoft 365 E5 |
| Defender for Cloud Apps | وسيط أمان الوصول إلى السحابة للاكتشاف والتحقيق والحوكمة عبر جميع خدمات Microsoft وخدمات السحابة التابعة لجهة خارجية. | الحركة الجانبية والتحرير غير المصرح للبيانات. | Microsoft 365 E5 أو Microsoft 365 E3 باستخدام الوظيفة الإضافية الأمان في Microsoft 365 E5 |
|

### <a name="3-identities"></a>3. الهويات

| القدرة أو الميزة | الوصف | يساعد على منع... | الترخيص |
|:-------|:-----|:-------|:-------|
|حماية كلمة مرور Azure AD | حظر كلمات المرور من قائمة شائعة وإدخالات مخصصة. | تحديد كلمة مرور حساب المستخدم السحابي أو المحلي. |Microsoft 365 E3 أو Microsoft 365 E5|
|المصادقة متعددة العوامل المفروضة مع الوصول المشروط | طلب المصادقة متعددة العوامل استنادا إلى خصائص عمليات تسجيل دخول المستخدم باستخدام نهج الوصول المشروط. | اختراق بيانات الاعتماد والوصول إليها. | Microsoft 365 E3 أو Microsoft 365 E5|
|تطبيق المصادقة متعددة العوامل مع الوصول المشروط المستند إلى المخاطر | طلب المصادقة متعددة العوامل استنادا إلى مخاطر تسجيل دخول المستخدم باستخدام حماية هوية Azure AD. |اختراق بيانات الاعتماد والوصول إليها. | Microsoft 365 E5 أو Microsoft 365 E3 باستخدام الوظيفة الإضافية الأمان في Microsoft 365 E5|
|

### <a name="4-devices"></a>4. الأجهزة

لإدارة الأجهزة والتطبيقات:

| القدرة أو الميزة | الوصف | يساعد على منع... | الترخيص |
|:-------|:-----|:-------|:-------|
| Microsoft Intune | إدارة الأجهزة والتطبيقات التي تعمل عليها.  | اختراق الجهاز أو التطبيق والوصول إليه. | Microsoft 365 E3 أو E5 |
|  |  |  |  |

بالنسبة إلى Windows 11 أو 10 أجهزة:

| القدرة أو الميزة | الوصف | يساعد... | الترخيص |
|:-------|:-----|:-------|:-------|
| جدار حماية Microsoft Defender | يوفر جدار حماية يستند إلى المضيف.  | منع الهجمات من نسبة استخدام الشبكة الواردة وغير المرغوب فيها. | Microsoft 365 E3 أو Microsoft 365 E5 |
| برنامج الحماية من الفيروسات من Microsoft Defender | يوفر الحماية من البرامج الضارة للأجهزة (نقاط النهاية) باستخدام التعلم الآلي وتحليل البيانات الضخمة والبحث المتعمق في مقاومة التهديدات والبنية الأساسية السحابية ل Microsoft. | منع تثبيت البرامج الضارة وتشغيلها. | Microsoft 365 E3 أو Microsoft 365 E5 |
| Microsoft Defender SmartScreen | الحماية من التصيد الاحتيالي أو مواقع الويب والتطبيقات الضارة، وتنزيل الملفات التي يحتمل أن تكون ضارة. | الحظر أو التحذير عند التحقق من المواقع والتنزيلات والتطبيقات والملفات. | Microsoft 365 E3 أو Microsoft 365 E5 |
| Microsoft Defender for Endpoint | يساعد على منع التهديدات المتقدمة والكشف عنها والتحقيق فيها والاستجابة لها عبر الأجهزة (نقاط النهاية). | الحماية من العبث بالشبكة. | Microsoft 365 E5 أو Microsoft 365 E3 باستخدام الوظيفة الإضافية الأمان في Microsoft 365 E5 |
|  |  |  |  |

### <a name="5-information"></a>5. معلومات

| القدرة أو الميزة | الوصف | يساعد... | الترخيص |
|:-------|:-----|:-------|:-------|
| الوصول إلى المجلدات الخاضعة للتحكم | يحمي بياناتك من خلال التحقق من التطبيقات مقابل قائمة بالتطبيقات المعروفة الموثوق بها. | منع تغيير الملفات أو تشفيرها بواسطة برامج الفدية الضارة. | Microsoft 365 E3 أو Microsoft 365 E5 |
| Microsoft Purview حماية البيانات | تمكين تطبيق تسميات الحساسية على المعلومات القابلة للفدية | منع استخدام المعلومات التي تم حذفها. | Microsoft 365 E3 أو Microsoft 365 E5 |
| تفادي فقدان البيانات (DLP) | حماية البيانات الحساسة وتقليل المخاطر من خلال منع المستخدمين من مشاركتها بشكل غير مناسب. | منع النقل غير المصرح للبيانات. | Microsoft 365 E3 أو Microsoft 365 E5 |
| Defender for Cloud Apps | وسيط أمان الوصول إلى السحابة للاكتشاف والتحقيق والحوكمة. | الكشف عن الحركة الجانبية ومنع النقل غير المصرح للبيانات. | Microsoft 365 E5 أو Microsoft 365 E3 باستخدام الوظيفة الإضافية الأمان في Microsoft 365 E5 |
|

## <a name="impact-on-users-and-change-management"></a>التأثير على المستخدمين وإدارة التغيير

يمكن أن يؤثر نشر ميزات الأمان الإضافية وتنفيذ المتطلبات ونهج الأمان لمستأجر Microsoft 365 على المستخدمين. 

على سبيل المثال، يمكنك فرض نهج أمان جديد يتطلب من المستخدمين إنشاء فرق جديدة لاستخدامات محددة مع قائمة بحسابات المستخدمين كأعضاء، بدلا من إنشاء فريق لجميع المستخدمين في المؤسسة بسهولة أكبر. يمكن أن يساعد هذا في منع مهاجم برامج الفدية الضارة من استكشاف الفرق غير المتوفرة لحساب المستخدم المخترق للمهاجم واستهداف موارد هذا الفريق في الهجوم اللاحق.

سيحدد حل الأساس هذا متى يمكن أن تؤثر التكوينات الجديدة أو نهج الأمان الموصى بها على المستخدمين حتى تتمكن من تنفيذ إدارة التغيير المطلوبة.

## <a name="next-steps"></a>الخطوات التالية

استخدم هذه الخطوات لنشر حماية شاملة لمستأجر Microsoft 365:

1. [تكوين أساسات الأمان](ransomware-protection-microsoft-365-security-baselines.md)
2. [نشر الكشف عن الهجمات والاستجابة لها](ransomware-protection-microsoft-365-attack-detection-response.md)
3. [حماية الهويات](ransomware-protection-microsoft-365-identities.md)
4. [حماية الأجهزة](ransomware-protection-microsoft-365-devices.md)
5. [حماية المعلومات](ransomware-protection-microsoft-365-information.md)

[![الخطوة 1 للحماية من برامج الفدية الضارة باستخدام Microsoft 365](../media/ransomware-protection-microsoft-365/ransomware-protection-microsoft-365-step1.png)](ransomware-protection-microsoft-365-security-baselines.md)

## <a name="additional-ransomware-resources"></a>موارد برامج الفدية الإضافية

المعلومات الرئيسية من Microsoft:

- [التهديد المتزايد من برامج الفدية الضارة](https://blogs.microsoft.com/on-the-issues/2021/07/20/the-growing-threat-of-ransomware/)، منشور مدونة Microsoft On the Issues في 20 يوليو 2021
- [برامج الفدية الضارة التي يديرها الإنسان](/security/compass/human-operated-ransomware)
- [الحماية السريعة من برامج الفدية الضارة والمساهمة](/security/compass/protect-against-ransomware)
- [تقرير الدفاع الرقمي ل Microsoft 2021](https://www.microsoft.com/security/business/microsoft-digital-defense-report) (راجع الصفحات 10-19)
- [برامج الفدية الضارة: تقرير تحليلات مخاطر التهديدات المنتشرة والمستمرة](https://security.microsoft.com/threatanalytics3/05658b6c-dc62-496d-ad3c-c6a795a33c27/overview) في مدخل Microsoft 365 Defender
- نهج برامج الفدية الضارة لفريق الكشف والاستجابة (DART) من Microsoft [وأفضل الممارسات](/security/compass/incident-response-playbook-dart-ransomware-approach) [ودراسة الحالة](/security/compass/dart-ransomware-case-study)

Microsoft 365:

- [زيادة مرونة برامج الفدية الضارة مع Azure Microsoft 365](https://azure.microsoft.com/resources/maximize-ransomware-resiliency-with-azure-and-microsoft-365/)
- [التعافي من هجوم برامج الفدية الضارة](/microsoft-365/security/office-365-security/recover-from-ransomware)
- [البرامج الضارة والحماية من برامج الفدية الضارة](/compliance/assurance/assurance-malware-and-ransomware-protection)
- [حماية الكمبيوتر الشخصي Windows 10 من برامج الفدية الضارة](https://support.microsoft.com//windows/protect-your-pc-from-ransomware-08ed68a7-939f-726c-7e84-a72ba92c01c3)
- [التعامل مع برامج الفدية الضارة في SharePoint Online](/sharepoint/troubleshoot/security/handling-ransomware-in-sharepoint-online)
- [تقارير تحليلات التهديد حول برامج الفدية الضارة](https://security.microsoft.com/threatanalytics3?page_size=30&filters=tags%3DRansomware&ordering=-lastUpdatedOn&fields=displayName,alertsCount,impactedEntities,reportType,createdOn,lastUpdatedOn,tags,flag) في مدخل Microsoft 365 Defender

Microsoft 365 Defender:

- [البحث عن برامج الفدية الضارة باستخدام التتبع المتقدم](/microsoft-365/security/defender/advanced-hunting-find-ransomware)

Microsoft Azure:

- [Azure Defenses لهجمات برامج الفدية الضارة](https://azure.microsoft.com/resources/azure-defenses-for-ransomware-attack/)
- [زيادة مرونة برامج الفدية الضارة مع Azure Microsoft 365](https://azure.microsoft.com/resources/maximize-ransomware-resiliency-with-azure-and-microsoft-365/)
- [خطة النسخ الاحتياطي والاستعادة للحماية من برامج الفدية الضارة](/security/compass/backup-plan-to-protect-against-ransomware)
- [المساعدة في الحماية من برامج الفدية الضارة باستخدام Microsoft Azure Backup](https://www.youtube.com/watch?v=VhLOr2_1MCg) (فيديو مدته 26 دقيقة)
- [التعافي من اختراق الهوية النظامية](/azure/security/fundamentals/recover-from-identity-compromise)
- [الكشف المتقدم عن الهجوم متعدد المستويات في Microsoft Sentinel](/azure/sentinel/fusion#ransomware)
- [اكتشاف الاندماج لبرنامج الفدية الضارة في Microsoft Sentinel](https://techcommunity.microsoft.com/t5/azure-sentinel/what-s-new-fusion-detection-for-ransomware/ba-p/2621373)

Microsoft Defender for Cloud Apps:

-  [إنشاء نهج الكشف عن الحالات الشاذة في Defender for Cloud Apps](/cloud-app-security/anomaly-detection-policy)

منشورات مدونة فريق أمان Microsoft:

- [3 خطوات لمنع برامج الفدية الضارة والتعافي منها (سبتمبر 2021)](https://www.microsoft.com/security/blog/2021/09/07/3-steps-to-prevent-and-recover-from-ransomware/)
- [دليل لمكافحة برامج الفدية الضارة التي يديرها الإنسان: الجزء الأول (سبتمبر 2021)](https://www.microsoft.com/security/blog/2021/09/20/a-guide-to-combatting-human-operated-ransomware-part-1/)

  الخطوات الرئيسية حول كيفية قيام فريق الكشف والاستجابة من Microsoft (DART) بإجراء التحقيقات في حوادث برامج الفدية الضارة.

- [دليل لمكافحة برامج الفدية الضارة التي يديرها الإنسان: الجزء 2 (سبتمبر 2021)](https://www.microsoft.com/security/blog/2021/09/27/a-guide-to-combatting-human-operated-ransomware-part-2/)

  التوصيات وأفضل الممارسات.

- [القدرة على الصمود من خلال فهم مخاطر الأمان عبر الإنترنت: الجزء 4 - التنقل بين التهديدات الحالية (مايو 2021)](https://www.microsoft.com/security/blog/2021/05/26/becoming-resilient-by-understanding-cybersecurity-risks-part-4-navigating-current-threats/)

  راجع قسم **برامج الفدية الضارة** .

- [هجمات برامج الفدية الضارة التي يديرها الإنسان: كارثة يمكن الوقاية منها (مارس 2020)](https://www.microsoft.com/security/blog/2020/03/05/human-operated-ransomware-attacks-a-preventable-disaster/)

  يتضمن تحليلات سلسلة الهجوم للهجمات الفعلية.

- [استجابة برامج الفدية الضارة - للدفع أو عدم الدفع؟ (ديسمبر 2019)](https://www.microsoft.com/security/blog/2019/12/16/ransomware-response-to-pay-or-not-to-pay/)
- [يستجيب Norsk Hydro لهجوم برامج الفدية الضارة بالشفافية (ديسمبر 2019)](https://www.microsoft.com/security/blog/2019/12/17/norsk-hydro-ransomware-attack-transparency/)
