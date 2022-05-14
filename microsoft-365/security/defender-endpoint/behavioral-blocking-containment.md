---
title: الحظر السلوكي والاحتواء
description: تعرف على قدرات الحظر السلوكي والاحتواء في Microsoft Defender لنقطة النهاية
keywords: Microsoft Defender لنقطة النهاية، الكشف التلقائي والاستجابة على النقط النهائية في وضع الحظر، حظر الوضع السلبي
ms.pagetype: security
author: denisebmsft
ms.author: deniseb
manager: dansimp
ms.reviewer: shwetaj
audience: ITPro
ms.topic: article
ms.prod: m365-security
ms.localizationpriority: medium
ms.custom:
- next-gen
- edr
- admindeeplinkDEFENDER
ms.collection: m365-security-compliance
ms.technology: mde
ms.openlocfilehash: f6544a14891a98523d202c19634d0e70a3e839e2
ms.sourcegitcommit: ebbe8713297675db5dcb3e0d9c3ae5e746b99196
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 05/14/2022
ms.locfileid: "65416783"
---
# <a name="behavioral-blocking-and-containment"></a>الحظر السلوكي والاحتواء

**ينطبق على:**
- [Defender for Endpoint الخطة 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)
- برنامج الحماية من الفيروسات من Microsoft Defender

**الأنظمة الأساسية**
- بالنسبة لنظام التشغيل

> هل تريد تجربة Defender لنقطة النهاية؟ [التسجيل للحصول على إصدار تجريبي مجاني.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-assignaccess-abovefoldlink)

## <a name="overview"></a>نظرة عامة

يتم تجاوز مشهد التهديد اليوم من خلال [البرامج الضارة بلا ملفات](/windows/security/threat-protection/intelligence/fileless-threats) والتي تعيش خارج الأرض، والتهديدات متعددة الأشكال للغاية التي تتحور بشكل أسرع من الحلول التقليدية التي يمكن أن تواكبها، والهجمات التي يديرها الإنسان والتي تتكيف مع ما يجده الخصوم على الأجهزة المخترقة. حلول الأمان التقليدية ليست كافية لإيقاف مثل هذه الهجمات؛ تحتاج إلى الذكاء الاصطناعي (الذكاء الاصطناعي) والقدرات المدعومة من التعلم الآلي (ML)، مثل الحظر السلوكي والاحتواء، المضمنة في [Defender لنقطة النهاية](/windows/security).

يمكن أن تساعد قدرات الحظر السلوكي والاحتواء في تحديد التهديدات وإيقافها، استنادا إلى سلوكياتها ومعالجة الأشجار حتى عندما يبدأ تنفيذ التهديد. تعمل مكونات وميزات الجيل التالي من الحماية الكشف التلقائي والاستجابة على النقط النهائية و Defender لنقطة النهاية معا في قدرات الحظر السلوكي والاحتواء.

:::image type="content" source="images/mdatp-next-gen-EDR-behavblockcontain.png" alt-text="الحظر السلوكي والاحتواء في مدخل Microsoft Defender ATP" lightbox="images/mdatp-next-gen-EDR-behavblockcontain.png":::

تعمل قدرات الحظر السلوكي والاحتواء مع مكونات وميزات متعددة من Defender لنقطة النهاية لإيقاف الهجمات على الفور ومنع الهجمات من التقدم.

- يمكن [لحماية الجيل التالي](microsoft-defender-antivirus-in-windows-10.md) (التي تتضمن برنامج الحماية من الفيروسات من Microsoft Defender) الكشف عن التهديدات من خلال تحليل السلوكيات، وإيقاف التهديدات التي بدأت في التشغيل.

- يتلقى [الكشف عن نقطة النهاية والاستجابة](overview-endpoint-detection-response.md) لها (الكشف التلقائي والاستجابة على النقط النهائية) إشارات الأمان عبر الشبكة والأجهزة وسلوك النواة. مع اكتشاف التهديدات، يتم إنشاء التنبيهات. يتم تجميع تنبيهات متعددة من نفس النوع في حوادث، ما يسهل على فريق عمليات الأمان التحقيق والاستجابة.

- يحتوي [Defender لنقطة النهاية](overview-endpoint-detection-response.md) على مجموعة واسعة من البصريات عبر الهويات والبريد الإلكتروني والبيانات والتطبيقات، بالإضافة إلى إشارات سلوك الشبكة ونقطة النهاية والنواة التي يتم تلقيها من خلال الكشف التلقائي والاستجابة على النقط النهائية. أحد مكونات [Microsoft 365 Defender](../defender/microsoft-365-defender.md)، يقوم Defender لنقطة النهاية بمعالجة هذه الإشارات وربطها، ويرفع تنبيهات الكشف، ويربط التنبيهات ذات الصلة في الحوادث.

مع هذه القدرات، يمكن منع المزيد من التهديدات أو حظرها، حتى لو بدأت في التشغيل. كلما تم الكشف عن سلوك مريب، يتم احتواء التهديد، وإنشاء التنبيهات، وتوقف التهديدات في مساراتها.

تعرض الصورة التالية مثالا للتنبيه الذي تم تشغيله بواسطة قدرات الحظر السلوكي والاحتواء:

:::image type="content" source="images/blocked-behav-alert.png" alt-text="صفحة التنبيهات مع تنبيه من خلال الحظر السلوكي والاحتواء" lightbox="images/blocked-behav-alert.png":::

## <a name="components-of-behavioral-blocking-and-containment"></a>مكونات الحظر السلوكي والاحتواء

- **[قواعد تقليل الأجزاء المعرضة للهجوم](attack-surface-reduction.md) المستندة إلى النهج على العميل** يتم منع سلوكيات الهجوم الشائعة المعرفة مسبقا من التنفيذ، وفقا لقواعد تقليل الأجزاء المعرضة للهجوم. عندما تحاول هذه السلوكيات التنفيذ، يمكن رؤيتها في <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender</a> كتنبيهات إعلامية. لا يتم تمكين قواعد تقليل الأجزاء المعرضة للهجوم بشكل افتراضي؛ تقوم بتكوين نهجك في [مدخل Microsoft 365 Defender](/microsoft-365/security/defender/microsoft-365-defender).

- **[الحظر السلوكي للعميل](client-behavioral-blocking.md)** يتم الكشف عن التهديدات على نقاط النهاية من خلال التعلم الآلي، ثم يتم حظرها ومعالجتها تلقائيا. (يتم تمكين الحظر السلوكي للعميل بشكل افتراضي.)

- يتم مراقبة **[حظر حلقة الملاحظات](feedback-loop-blocking.md)** (يشار إليها أيضا باسم الحماية السريعة) الكشف عن التهديدات من خلال الذكاء السلوكي. يتم إيقاف التهديدات ومنعها من التشغيل على نقاط النهاية الأخرى. (يتم تمكين حظر حلقة الملاحظات بشكل افتراضي.)

- يتم حظر البيانات الاصطناعية الضارة أو السلوكيات التي تتم ملاحظتها من خلال الحماية بعد الخرق **[(الكشف التلقائي والاستجابة على النقط النهائية) في وضع الحظر](edr-in-block-mode.md)** والكشف عن السلوكيات الضارة التي تتم ملاحظتها من خلال الحماية بعد الاختراق. تعمل الكشف التلقائي والاستجابة على النقط النهائية في وضع الحظر حتى لو لم يكن برنامج الحماية من الفيروسات من Microsoft Defender هو الحل الأساسي لمكافحة الفيروسات. (لا يتم تمكين الكشف التلقائي والاستجابة على النقط النهائية في وضع الحظر بشكل افتراضي؛ يمكنك تشغيله في Microsoft 365 Defender.)

توقع المزيد في مجال الحظر السلوكي والاحتواء، مع استمرار Microsoft في تحسين ميزات الحماية من التهديدات وقدراتها. للاطلاع على ما تم التخطيط له والطرح الآن، تفضل بزيارة [المخطط Microsoft 365](https://www.microsoft.com/microsoft-365/roadmap).

## <a name="examples-of-behavioral-blocking-and-containment-in-action"></a>أمثلة على الحظر السلوكي والاحتواء أثناء العمل

وقد حظرت قدرات الحظر السلوكي والاحتواء تقنيات المهاجم مثل ما يلي:

- تفريغ بيانات الاعتماد من LSASS
- حقن العمليات التبادلية
- تجويف العملية
- تجاوز التحكم في حساب المستخدم
- العبث بالحماية من الفيروسات (مثل تعطيله أو إضافة البرامج الضارة كاستبعاد)
- الاتصال بالأوامر والتحكم (C&C) لتنزيل الحمولات
- استخراج العملات
- تعديل سجل التمهيد
- هجمات تمرير التجزئة
- تثبيت شهادة الجذر
- محاولة الاستغلال لمختلف الثغرات الأمنية

فيما يلي مثالان واقعيان للحظر السلوكي والاحتواء في العمل.

### <a name="example-1-credential-theft-attack-against-100-organizations"></a>مثال 1: هجوم سرقة بيانات الاعتماد ضد 100 منظمة

كما هو موضح في [البحث السريع عن التهديدات المخادع: يمنع الحظر المستند إلى السلوك الذكاء الاصطناعي الهجمات في مساراتها](https://www.microsoft.com/security/blog/2019/10/08/in-hot-pursuit-of-elusive-threats-ai-driven-behavior-based-blocking-stops-attacks-in-their-tracks)، تم إيقاف هجوم سرقة بيانات الاعتماد ضد 100 منظمة في جميع أنحاء العالم من خلال قدرات الحظر السلوكي والاحتواء. تم إرسال رسائل البريد الإلكتروني للتصيد الاحتيالي الرمح التي تحتوي على مستند استدراج إلى المؤسسات المستهدفة. إذا قام أحد المستلمين بفتح المرفق، فقد تمكن مستند بعيد ذي صلة من تنفيذ التعليمات البرمجية على جهاز المستخدم وتحميل برامج Lokibot الضارة، والتي قامت بسرقة بيانات الاعتماد، وصادرت البيانات المسروقة، وانتظرت المزيد من الإرشادات من خادم الأوامر والتحكم.

تم التقاط نماذج تعلم الأجهزة المستندة إلى السلوك في Defender لنقطة النهاية وأوقفت تقنيات المهاجم في نقطتين في سلسلة الهجوم:

- اكتشفت طبقة الحماية الأولى سلوك الاستغلال. حددت مصنفات تعلم الجهاز في السحابة التهديد بشكل صحيح وأرشدت جهاز العميل على الفور لحظر الهجوم.
- طبقة الحماية الثانية، التي ساعدت في إيقاف الحالات التي تجاوز فيها الهجوم الطبقة الأولى، واكتشفت تجويف العملية، وأوقفت هذه العملية، وأزلت الملفات المقابلة (مثل Lokibot).

بينما تم الكشف عن الهجوم وتوقفه، تم تشغيل تنبيهات، مثل "تنبيه وصول أولي"، وظهرت في [مدخل Microsoft 365 Defender](/microsoft-365/security/defender/microsoft-365-defender).

:::image type="content" source="images/behavblockcontain-initialaccessalert.png" alt-text="تنبيه الوصول الأولي في مدخل Microsoft 365 Defender" lightbox="images/behavblockcontain-initialaccessalert.png":::

يوضح هذا المثال كيف تضيف نماذج تعلم الأجهزة المستندة إلى السلوك في السحابة طبقات جديدة من الحماية من الهجمات، حتى بعد بدء تشغيلها.

### <a name="example-2-ntlm-relay---juicy-potato-malware-variant"></a>مثال 2: ترحيل NTLM - متغير البرامج الضارة Juicy Malware

كما هو موضح في منشور المدونة الأخير، [الحظر السلوكي والاحتواء: تحويل البصريات إلى حماية](https://www.microsoft.com/security/blog/2020/03/09/behavioral-blocking-and-containment-transforming-optics-into-protection)، في يناير 2020، اكتشف Defender لنقطة النهاية نشاط تصعيد امتياز على جهاز في مؤسسة. تم تشغيل تنبيه يسمى "تصعيد الامتيازات المحتملة باستخدام ترحيل NTLM".

:::image type="content" source="images/NTLMalertjuicypotato.png" alt-text="تنبيه NTLM للبرامج الضارة Juicy Malware" lightbox="images/NTLMalertjuicypotato.png":::

تبين أن التهديد عبارة عن برامج ضارة؛ كان متغيرا جديدا لم يظهر من قبل من أداة اختراق معروفة تسمى Juicy Privilege، والتي يستخدمها المهاجمون للحصول على تصعيد الامتيازات على جهاز.

بعد دقائق من تشغيل التنبيه، تم تحليل الملف، وتم التأكيد على أنه ضار. تم إيقاف العملية وحظرها، كما هو موضح في الصورة التالية:

:::image type="content" source="images/Artifactblockedjuicypotato.png" alt-text="البيانات الاصطناعية محظورة"  lightbox="images/Artifactblockedjuicypotato.png":::

بعد بضع دقائق من حظر البيانات الاصطناعية، تم حظر مثيلات متعددة للملف نفسه على نفس الجهاز، ما منع المزيد من المهاجمين أو البرامج الضارة الأخرى من النشر على الجهاز.

يوضح هذا المثال أنه مع قدرات الحظر السلوكي والاحتواء، يتم الكشف عن التهديدات، واحتواءها، وحظرها تلقائيا.

> [!TIP]
> إذا كنت تبحث عن معلومات متعلقة بالحماية من الفيروسات للأنظمة الأساسية الأخرى، فراجع:
> - [تعيين تفضيلات Microsoft Defender لنقطة النهاية على نظام التشغيل macOS](mac-preferences.md)
> - [Microsoft Defender for Endpoint على Mac](microsoft-defender-endpoint-mac.md)
> - [إعدادات نهج برنامج الحماية من الفيروسات في macOS لبرنامج الحماية من الفيروسات من Microsoft Defender Antivirus for Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [تعيين تفضيلات Microsoft Defender لنقطة النهاية على Linux](linux-preferences.md)
> - [مشكلات الأداء في Microsoft Defender لنقطة النهاية على Linux](microsoft-defender-endpoint-linux.md)
> - [تكوين Defender for Endpoint على ميزات Android](android-configure.md)
> - [تكوين Microsoft Defender for Endpoint على ميزات iOS](ios-configure-features.md)

## <a name="next-steps"></a>الخطوات التالية

- [تعرف على المزيد حول Defender لنقطة النهاية](overview-endpoint-detection-response.md)

- [تكوين قواعد تقليل الأجزاء المعرضة للهجوم](attack-surface-reduction.md)

- [تمكين الكشف التلقائي والاستجابة على النقط النهائية في وضع الحظر](edr-in-block-mode.md)

- [الاطلاع على نشاط التهديد العالمي الأخير](https://www.microsoft.com/wdsi/threats)

- [الحصول على نظرة عامة على Microsoft 365 Defender](../defender/microsoft-365-defender.md)
