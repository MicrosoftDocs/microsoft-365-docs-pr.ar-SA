---
title: الحظر السلوكي والاحتواء
description: تعرف على قدرات الحظر والاحتواء السلوكية في Microsoft Defender لنقطة النهاية
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
ms.openlocfilehash: f919a93768699c573c87b938cea37a05955ab9f2
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/25/2022
ms.locfileid: "64465322"
---
# <a name="behavioral-blocking-and-containment"></a>الحظر السلوكي والاحتواء

**ينطبق على:**
- [Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> هل تريد تجربة Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-assignaccess-abovefoldlink)

## <a name="overview"></a>نظرة عامة

لقد تم تجاوز مشهد التهديدات اليوم بواسطة البرامج الضارة [](/windows/security/threat-protection/intelligence/fileless-threats) غير الملفية التي تعيش خارج الأرض، كما يمكن أن تستمر التهديدات المتعددة الأشكال التي يتم تكتمها بشكل أسرع من الحلول التقليدية في مواكبة الهجمات التي يتم تشغيلها بواسطة الإنسان وتتكيف مع ما تعثر عليه أجهزة الشرطة على الأجهزة المخروطة. لا تكفي حلول الأمان التقليدية لإيقاف مثل هذه الهجمات؛ تحتاج إلى الذكاء الاصطناعي (AI) وإمكانيات تعلم الجهاز (ML) المضمنة في [Defender for Endpoint](/windows/security)، مثل الحظر السلوكي والاحتواء.

يمكن أن تساعد قدرات الحظر والاحتواء السلوكية على تحديد التهديدات والتوقف عنها، استنادا إلى سلوكياتها وأشجار المعالجة حتى عندما يبدأ التهديد التنفيذ. تعمل ميزات حماية الجيل الكشف التلقائي والاستجابة على النقط النهائية و Defender لمكونات نقطة النهاية وميزاتها معا في قدرات الحظر والاحتواء السلوكية.

:::image type="content" source="images/mdatp-next-gen-EDR-behavblockcontain.png" alt-text="الحظر السلوكي والاحتواء في مدخل MICROSOFT Defender ATP" lightbox="images/mdatp-next-gen-EDR-behavblockcontain.png":::

تعمل قدرات الحظر والاحتواء السلوكية مع مكونات وميزات متعددة ل Defender for Endpoint لإيقاف الهجمات على الفور ومنع تقدم الهجمات.

- [يمكن أن تكشف حماية](microsoft-defender-antivirus-in-windows-10.md) الجيل التالي (التي تتضمن برنامج الحماية من الفيروسات من Microsoft Defender) عن التهديدات من خلال تحليل السلوكيات، وتوقف التهديدات التي بدأت في التشغيل.

- [يتلقى الكشف عن](overview-endpoint-detection-response.md) نقطة النهاية والاستجابة (الكشف التلقائي والاستجابة على النقط النهائية) إشارات أمان عبر الشبكة والأجهزة وسلوك kernel. عند اكتشاف التهديدات، يتم إنشاء التنبيهات. يتم تجميع تنبيهات متعددة من النوع نفسه في أحداث، مما يسهل على فريق عمليات الأمان التحقق منها والاستجابة لها.

- [تتوفر في Defender for Endpoint](overview-endpoint-detection-response.md) مجموعة واسعة من البصريات عبر الهويات والبريد الإلكتروني والبيانات والتطبيقات، بالإضافة إلى إشارات سلوك الشبكة ونقطة النهاية وkernel التي يتم تلقيها عبر الكشف التلقائي والاستجابة على النقط النهائية. مكون [من مكونات Microsoft 365 Defender](../defender/microsoft-365-defender.md)، يوصل Defender for Endpoint هذه الإشارات ويرفع تنبيهات الكشف ويربط التنبيهات ذات الصلة في الأحداث.

باستخدام هذه الإمكانات، يمكن منع المزيد من التهديدات أو حظرها، حتى لو بدأ تشغيلها. وكلما تم اكتشاف سلوك مريب، يتم احتواء الخطر، وإنشاء التنبيهات، وتوقف التهديدات في مساراتها.

تعرض الصورة التالية مثالا عن تنبيه تم تشغيله بواسطة قدرات الحظر والاحتواء السلوكية:

:::image type="content" source="images/blocked-behav-alert.png" alt-text="صفحة التنبيهات مع تنبيه من خلال الحظر السلوكي والاحتواء" lightbox="images/blocked-behav-alert.png":::

## <a name="components-of-behavioral-blocking-and-containment"></a>مكونات الحظر والاحتواء السلوكية

- **قواعد تقليل [](attack-surface-reduction.md)** مساحة الهجوم على العميل والمحركة إلى النهج يتم منع تنفيذ سلوكيات الهجمات الشائعة المحددة مسبقا، وفقا لقواعد الحد من سطح الهجوم. عندما تحاول مثل هذه السلوكيات تنفيذ هذه السلوكيات، يمكن <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender</a> كتنبيهات معلوماتية. لا يتم تمكين قواعد الحد من سطح الهجوم بشكل افتراضي؛ يمكنك تكوين سياساتك في Microsoft 365 Defender [المدخل](/microsoft-365/security/defender/microsoft-365-defender).

- **[الحظر السلوكي للعميل](client-behavioral-blocking.md)** يتم الكشف عن التهديدات على نقاط النهاية من خلال التعلم الآلي، ثم يتم حظرها وتبوينها تلقائيا. (يتم تمكين الحظر السلوكي للعميل بشكل افتراضي.)

- **[يتم ملاحظة حظر تكرار الملاحظات](feedback-loop-blocking.md)** (يشار إليه أيضا بالحماية السريعة) من خلال الذكاء السلوكي. يتم إيقاف التهديدات ومنعها من التشغيل على نقاط نهاية أخرى. (يتم تمكين حظر تكرار الملاحظات بشكل افتراضي.)

- **[يتم حظر](edr-in-block-mode.md)** الكشف عن نقاط النهاية والاستجابة لها (الكشف التلقائي والاستجابة على النقط النهائية) في وضع الحظر، يتم حظر التحف الضارة أو السلوكيات التي يتم ملاحظتها من خلال الحماية بعد الخرق، كما يتم احتواؤها. الكشف التلقائي والاستجابة على النقط النهائية في وضع الحظر حتى برنامج الحماية من الفيروسات من Microsoft Defender لم يكن هذا هو حل الحماية من الفيروسات الأساسي. (الكشف التلقائي والاستجابة على النقط النهائية الإعدادات في وضع الحظر بشكل افتراضي؛ يمكنك تشغيلها في وضع Microsoft 365 Defender.)

توقع المزيد في مجال الحظر السلوكي والاحتواء، بينما تواصل Microsoft تحسين ميزات الحماية من المخاطر وإمكاناتها. لمعرفة ما تم التخطيط له و نشره الآن، تفضل [بزيارة Microsoft 365 التخطيط.](https://www.microsoft.com/microsoft-365/roadmap)

## <a name="examples-of-behavioral-blocking-and-containment-in-action"></a>أمثلة على الحظر السلوكي والاحتواء في العمل

لقد حظرت قدرات الحظر والاحتواء السلوكية أساليب مهاجمين مثل ما يلي:

- تفريغ بيانات الاعتماد من LSASS
- عملية متقاطعة
- تجويف العملية
- تجاوز التحكم في حساب المستخدم
- العبث في برنامج الحماية من الفيروسات (مثل تعطيله أو إضافة البرامج الضارة كالاستثناءات)
- الاتصال الأمر والتحكم (C&C) لتنزيل التحميلات
- تعدين العملات
- تعديل سجل التشغيل
- هجمات تمرير الهاش
- تثبيت شهادة الجذر
- محاولة استغلال نقاط الضعف المختلفة

فيما يلي مثالان في الحياة الحقيقية للحظر السلوكي والاحتواء في العمل.

### <a name="example-1-credential-theft-attack-against-100-organizations"></a>مثال 1: هجوم سرقة بيانات الاعتماد على 100 مؤسسة

كما هو موضح في المطاردة الحثيثة للتهديدات التي تم اخفاءها: إيقاف الهجمات المستندة إلى السلوك المستند إلى [AI](https://www.microsoft.com/security/blog/2019/10/08/in-hot-pursuit-of-elusive-threats-ai-driven-behavior-based-blocking-stops-attacks-in-their-tracks) في مساراتها، تم إيقاف هجوم سرقة بيانات الاعتماد على 100 مؤسسة حول العالم بواسطة قدرات الحظر والاحتواء السلوكية. تم إرسال رسائل البريد الإلكتروني التصيد الاحتيالي التي تحتوي على مستند استدراج إلى المؤسسات المستهدفة. إذا قام مستلم بفتح المرفق، تمكن مستند بعيد ذي صلة من تنفيذ التعليمات البرمجية على جهاز المستخدم وتحميل البرامج الضارة ل Lokibot، التي سرقت بيانات الاعتماد، والبيانات التي تمت سرقتها، وانتظر الحصول على مزيد من الإرشادات من خادم الأوامر والتحكم.

تم ضبط نماذج تعلم الأجهزة المستندة إلى السلوك في Defender for Endpoint وأوقفت أساليب المهاجم في نقطتين في سلسلة الهجوم:

- اكتشفت طبقة الحماية الأولى سلوك استغلال. حددت تصنيفات تعلم الأجهزة في السحابة الخطر بشكل صحيح على أنه تم توجيه جهاز العميل على الفور لحظر الهجوم.
- طبقة الحماية الثانية، التي كانت تساعد على إيقاف حالات اجتياج الهجوم للطبقة الأولى، والكشف عن تجويف العملية، وتوقفت عن هذه العملية، وأزلت الملفات المقابلة (مثل Lokibot).

أثناء اكتشاف الهجوم وتوقفه، تم تشغيل تنبيهات، مثل "تنبيه الوصول الأولي"، وظهرت في مدخل Microsoft 365 Defender[.](/microsoft-365/security/defender/microsoft-365-defender)

:::image type="content" source="images/behavblockcontain-initialaccessalert.png" alt-text="تنبيه الوصول الأولي في مدخل Microsoft 365 Defender" lightbox="images/behavblockcontain-initialaccessalert.png":::

يوضح هذا المثال كيف تضيف نماذج تعلم الأجهزة المستندة إلى السلوك في السحابة طبقات جديدة من الحماية من الهجمات، حتى بعد بدء تشغيلها.

### <a name="example-2-ntlm-relay---juicy-potato-malware-variant"></a>المثال 2: ترحيل NTLM - متغير البرامج الضارة للبطاطس العوسية

كما هو موضح في منشور المدونة الأخير، الحظر السلوكي والاحتواء [:](https://www.microsoft.com/security/blog/2020/03/09/behavioral-blocking-and-containment-transforming-optics-into-protection) تحويل البصريات إلى حماية، في يناير 2020، كشف Defender for Endpoint عن نشاط تصاعد الامتيازات على جهاز في مؤسسة. تم تشغيل تنبيه باسم "تصاعد الامتيازات المحتمل باستخدام ترحيل NTLM".

:::image type="content" source="images/NTLMalertjuicypotato.png" alt-text="تنبيه NTLM للبرامج الضارة &quot;بطاطس الجويسية&quot;" lightbox="images/NTLMalertjuicypotato.png":::

تبين أن الخطر هو برنامج ضار؛ لقد كانت أداة اختراق سيئة السمعة تسمى "بطاطس حلوة"، والتي يستخدمها المتطفلون لتصعيد الامتياز على جهاز ما، هو متغير جديد لم يتم رؤيته من قبل.

بعد دقائق من تشغيل التنبيه، تم تحليل الملف، وتأكد أنه ضار. تم إيقاف العملية الخاصة بها وحظرها، كما هو موضح في الصورة التالية:

:::image type="content" source="images/Artifactblockedjuicypotato.png" alt-text="تم حظر التحف"  lightbox="images/Artifactblockedjuicypotato.png":::

بعد دقائق قليلة من حظر الأداة الفنية، تم حظر مثيلات متعددة لنفس الملف على الجهاز نفسه، مما منع المزيد من المهاجمين أو البرامج الضارة الأخرى من النشر على الجهاز.

يوضح هذا المثال أنه باستخدام قدرات الحظر والاحتواء السلوكية، يتم الكشف عن التهديدات واحتوائها وحظرها تلقائيا.

## <a name="next-steps"></a>الخطوات التالية

- [تعرف على المزيد حول Defender for Endpoint](overview-endpoint-detection-response.md)

- [تكوين قواعد الحد من سطح الهجوم](attack-surface-reduction.md)

- [تمكين الكشف التلقائي والاستجابة على النقط النهائية في وضع الحظر](edr-in-block-mode.md)

- [الاطلاع على نشاط التهديدات العالمية الأخير](https://www.microsoft.com/wdsi/threats)

- [احصل على نظرة عامة Microsoft 365 Defender](../defender/microsoft-365-defender.md)
