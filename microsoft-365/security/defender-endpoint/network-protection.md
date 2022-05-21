---
title: استخدام حماية الشبكة للمساعدة في منع الاتصالات بالمواقع غير الصالحة
description: حماية شبكتك عن طريق منع المستخدمين من الوصول إلى عناوين الشبكة الضارة والمريبة المعروفة
keywords: حماية الشبكة، مهاجمات، موقع ويب ضار، ip، المجال، المجالات، الأمر والتحكم، SmartScreen، إعلام منبثق
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
audience: ITPro
author: denisebmsft
ms.author: deniseb
ms.reviewer: oogunrinde
manager: dansimp
ms.custom: asr
ms.technology: mde
ms.topic: overview
ms.collection:
- m365initiative-m365-defender
- M365-security-compliance
ms.date: ''
ms.openlocfilehash: 6bf97490d60740b47420d352f7fb537e675678ae
ms.sourcegitcommit: 349f0f54b0397cdd7d8fbb9ef07f1b6654a32d6e
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 05/20/2022
ms.locfileid: "65621146"
---
# <a name="protect-your-network"></a>حماية الشبكة

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**

- [Defender for Endpoint الخطة 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)
- برنامج الحماية من الفيروسات من Microsoft Defender

**الأنظمة الأساسية**
- بالنسبة لنظام التشغيل

> هل تريد تجربة Microsoft Defender لنقطة النهاية؟ [التسجيل للحصول على إصدار تجريبي مجاني.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

## <a name="overview-of-network-protection"></a>نظرة عامة على حماية الشبكة

تساعد حماية الشبكة على حماية الأجهزة من الأحداث المستندة إلى الإنترنت. حماية الشبكة هي قدرة تقليل الأجزاء المعرضة للهجوم. يساعد على منع الموظفين من الوصول إلى المجالات الخطرة من خلال التطبيقات. تعتبر المجالات التي تستضيف رسائل التصيد الاحتيالي وعمليات الاستغلال والمحتوى الضار الآخر على الإنترنت مجالات خطرة. تعمل حماية الشبكة على توسيع نطاق [Microsoft Defender SmartScreen](/windows/security/threat-protection/microsoft-defender-smartscreen/microsoft-defender-smartscreen-overview) لحظر كافة نسبة استخدام شبكة HTTP الصادرة التي تحاول الاتصال بمصادر ذات سمعة منخفضة (استنادا إلى المجال أو اسم المضيف).

تعمل حماية الشبكة على توسيع الحماية في [حماية الويب](web-protection-overview.md) إلى مستوى نظام التشغيل. يوفر وظيفة حماية الويب الموجودة في Microsoft Edge إلى المستعرضات الأخرى المدعومة والتطبيقات غير المستعرضة. توفر حماية الشبكة أيضا رؤية وحظر مؤشرات التسوية (IOCs) عند استخدامها مع [الكشف عن نقطة النهاية والاستجابة لها](overview-endpoint-detection-response.md). على سبيل المثال، تعمل حماية الشبكة مع [المؤشرات المخصصة](manage-indicators.md) التي يمكنك استخدامها لحظر مجالات أو أسماء مضيفين معينة.

> [!TIP]
> راجع موقع اختبار Microsoft Defender لنقطة النهاية في [demo.wd.microsoft.com](https://demo.wd.microsoft.com?ocid=cx-wddocs-testground) لمعرفة كيفية عمل حماية الشبكة.

> [!NOTE]
> تم إهمال الموقع التجريبي ل Defender لنقطة النهاية في demo.wd.microsoft.com وستتم إزالته في المستقبل.

شاهد هذا الفيديو للتعرف على كيفية مساعدة حماية الشبكة في تقليل سطح الهجوم على أجهزتك من عمليات التصيد الاحتيالي وعمليات الاستغلال والمحتوى الضار الآخر.
> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4r4yZ]

## <a name="requirements-for-network-protection"></a>متطلبات حماية الشبكة

تتطلب حماية الشبكة Windows 10 Pro أو Enterprise، برنامج الحماية من الفيروسات من Microsoft Defender الحماية في الوقت الحقيقي.

****

| إصدار Windows | برنامج الحماية من الفيروسات من Microsoft Defender |
|:---|:---|
| Windows 10 الإصدار 1709 أو إصدار أحدث <br> Windows 11 <br> Windows Server 1803 أو إصدار أحدث | [برنامج الحماية من الفيروسات من Microsoft Defender الحماية في الوقت الحقيقي](configure-real-time-protection-microsoft-defender-antivirus.md) <br> ويجب تمكين [الحماية المقدمة من السحابة](enable-cloud-protection-microsoft-defender-antivirus.md) (نشط)|

## <a name="why-network-protection-is-important"></a>سبب أهمية حماية الشبكة

> [!IMPORTANT]
> تتعلق بعض المعلومات بالناتج الذي تم إصداره مسبقا والذي قد يتم تعديله بشكل كبير قبل إصداره تجاريا. لا تقدم Microsoft أي ضمانات، صريحة أو ضمنية، فيما يتعلق بالمعلومات المقدمة هنا.
>
> تتبع معلومات حول الميزات المتوفرة تجاريا معلومات المعاينة العامة.

حماية الشبكة هي جزء من مجموعة تقليل الأجزاء المعرضة للهجوم من الحلول في Microsoft Defender لنقطة النهاية. تتيح حماية الشبكة حظر عناوين URL وعناوين IP للطبقة 3 (طبقة الشبكة). يمكن أن تمنع حماية الشبكة الوصول إلى عناوين URL من مستعرضات الجهات الخارجية واتصالات الشبكة القياسية.

بشكل افتراضي، تقوم حماية الشبكة بحماية أجهزة الكمبيوتر من عناوين URL الضارة المعروفة باستخدام موجز الشاشة الذكية، الذي يحظر عناوين URL الضارة بطريقة مشابهة ل SmartScreen في مستعرض Microsoft Edge. يمكن توسيع وظيفة حماية الشبكة إلى:

- حظر IP / URL من Intel للمخاطر الخاصة بك (المؤشرات)
- حظر الخدمات غير الملغاة من Microsoft Cloud App Security (MCAS)
- حظر المواقع استنادا إلى الفئة (تصفية محتوى ويب)

تعد Network Protections جزءا مهما من مكدس حماية واستجابة Microsoft.

للحصول على تفاصيل حول Network Protection لخادم Windows وLinux وMacOS و MTD، راجع [البحث بشكل استباقي عن التهديدات باستخدام التتبع المتقدم](advanced-hunting-overview.md).

### <a name="block-command-and-control-c2-attacks"></a>حظر هجمات الأوامر والتحكم (C2)

يتم استخدام أجهزة كمبيوتر خادم C2 من قبل المستخدمين الضارين لإرسال الأوامر إلى الأنظمة التي تم اختراقها بواسطة البرامج الضارة، ثم إجراء نوع من التحكم في الأنظمة المخترقة. تخفي هجمات C2 عادة في الخدمات المستندة إلى السحابة مثل مشاركة الملفات وخدمات البريد الإلكتروني، ما يتيح لخوادم C2 تجنب الكشف عن طريق المزج مع نسبة استخدام الشبكة النموذجية.

يمكن استخدام خوادم C2 لبدء الأوامر التي يمكن أن:

- سرقة البيانات (على سبيل المثال، عن طريق التصيد الاحتيالي)
- التحكم في أجهزة الكمبيوتر المخترقة في شبكة الروبوت
- تعطيل التطبيقات المشروعة
- نشر البرامج الضارة، مثل برامج الفدية الضارة

يحدد مكون Network Protection في Microsoft Defender لنقطة النهاية الاتصالات بالبنية الأساسية C2 المستخدمة في هجمات برامج الفدية الضارة التي يديرها الإنسان ويحظرها، باستخدام تقنيات مثل التعلم الآلي وتحديد مؤشر التسوية الذكي (IoC).

#### <a name="network-protection-new-toast-notifications"></a>حماية الشبكة: إعلامات منبثقة جديدة

| تعيين جديد  | فئة الاستجابة  | مصادر |
| :--- | :--- | :--- |
| التصيد | التصيّد الاحتيالي | Smartscreen |
| الخبيثه | الخبيثه | Smartscreen |
| الأمر والتحكم | C2 | Smartscreen |
| الأمر والتحكم | كوكو | Smartscreen |
| الخبيثه | موثوق به | Smartscreen |
| من قبل مسؤول تكنولوجيا المعلومات | CustomBlockList |   |
| من قبل مسؤول تكنولوجيا المعلومات | CustomPolicy |   |

> [!NOTE]
> لا تقوم **customAllowList** بإنشاء إعلامات على نقاط النهاية.

### <a name="new-notifications-for-network-protection-determination"></a>إعلامات جديدة لتحديد حماية الشبكة

تستخدم القدرة الجديدة والمتاحة للجمهور في حماية الشبكة الوظائف في SmartScreen لحظر أنشطة التصيد الاحتيالي من مواقع الأوامر والتحكم الضارة.

عندما يحاول مستخدم زيارة موقع ويب في بيئة يتم فيها تمكين حماية الشبكة، تكون هناك ثلاثة سيناريوهات ممكنة:

- يتمتع URL **بسمعة جيدة معروفة** - في هذه الحالة يسمح للمستخدم بالوصول دون إعاقة، ولا يوجد إعلام منبثق مقدم على نقطة النهاية. في الواقع، يتم تعيين المجال أو URL إلى _"مسموح"._
- يتمتع URL **بسمعة غير معروفة أو غير معروفة** - يتم حظر وصول المستخدم، ولكن مع القدرة على الالتفاف على (إلغاء حظر) الكتلة. في الواقع، يتم تعيين المجال أو url إلى _Audit_.
- يتمتع URL **بسمعة سيئة (ضارة) معروفة** - يتم منع المستخدم من الوصول. في الواقع، يتم تعيين المجال أو url إلى _Block_.

#### <a name="warn-experience"></a>تجربة التحذير

يزور المستخدم موقع ويب:

- إذا كان ل url سمعة غير معروفة أو غير معروفة، فسيقدم إعلام منبثق للمستخدم الخيارات التالية:

  - **موافق** - يتم إصدار الإعلام المنبثق (تمت إزالته)، وتنتهي محاولة الوصول إلى الموقع.
  - **إلغاء الحظر** - لن يحتاج المستخدم إلى الوصول إلى مدخل Windows Defender Security Intelligence (WDSI) للوصول إلى الموقع. سيتمكن المستخدم من الوصول إلى الموقع لمدة 24 ساعة؛ عند هذه النقطة يتم إعادة تمكين الكتلة لمدة 24 ساعة أخرى. يمكن للمستخدم الاستمرار في استخدام **إلغاء الحظر** للوصول إلى الموقع حتى يقوم المسؤول بحظر (حظر) الموقع، وبالتالي إزالة خيار **إلغاء الحظر**.
  - **ملاحظات** - يقدم الإعلام المنبثق للمستخدم ارتباطا لإرسال تذكرة، والتي يمكن للمستخدم استخدامها لإرسال الملاحظات إلى المسؤول في محاولة لضبط الوصول إلى الموقع.

  > [!div class="mx-imgBorder"]
  > ![إظهار إعلام تحذير محتوى التصيد الاحتيالي لحماية الشبكة](images/network-protection-phishing-warn-2.png)

  > [ملاحظة!] الصور المعروضة هنا لتجربة التحذير وتجربة الحظر (أدناه) كل من القائمة **"url المحظور"** كمثال على نص العنصر النائب؛ في بيئة تعمل، سيتم سرد عنوان URL أو المجال الفعلي.  

#### <a name="block-experience"></a>تجربة الحظر

يزور المستخدم موقع ويب:

- إذا كان url يتمتع بسمعة سيئة، فسيقدم إعلام منبثق للمستخدم الخيارات التالية:
  - **موافق** يتم إصدار الإعلام المنبثق (تمت إزالته)، وتنتهي محاولة الوصول إلى الموقع.
  - **ردود الفعل** يقدم الإعلام المنبثق للمستخدم ارتباطا لإرسال تذكرة، والتي يمكن للمستخدم استخدامها لإرسال ملاحظات إلى المسؤول في محاولة لضبط الوصول إلى الموقع.
  
  > [!div class="mx-imgBorder"]
  > ![ إظهار إعلام بحظر محتوى التصيد الاحتيالي المعروف لحماية الشبكة](images/network-protection-phishing-blocked.png)

### <a name="network-protection-c2-detection-and-remediation"></a>حماية الشبكة: الكشف عن C2 والمعالجة

في شكلها الأولي، برامج الفدية الضارة هي تهديد السلع الأساسية، مبرمجة مسبقا وتركز على نتائج محدودة ومحددة (على سبيل المثال، تشفير جهاز كمبيوتر). ومع ذلك، تطورت برامج الفدية الضارة إلى تهديد متطور يستند إلى الإنسان، ومتكيف، ويركز على نطاق أوسع ونتائج أكثر انتشارا؛ مثل الاحتفاظ بأصول المؤسسة بأكملها أو بيانات الفدية.

دعم الأوامر والتحكم (C2) هو جزء رئيسي من تطور برامج الفدية الضارة هذا وهو ما يمكن هذه الهجمات من التكيف مع البيئة التي تستهدفها. يعني فصل الارتباط إلى البنية الأساسية للأوامر والتحكم إيقاف تقدم الهجوم إلى مرحلته التالية.

#### <a name="detecting-and-remediating-cobaltstrike-public-preview"></a>الكشف عن CobaltStrike ومعالجتها (معاينة عامة)

أحد أطر ما بعد الاستغلال الأكثر شيوعا المستخدمة في هجمات برامج الفدية الضارة التي يديرها الإنسان هو CobaltStrike. تتعقب فرق التحليل الذكي للمخاطر عبر Microsoft _التكتيكات والتقنيات والإجراءات_ (TTPs) على مجموعات الأنشطة المتعددة التي تنشر برامج الفدية الضارة لتحديد أنماط السلوك التي يمكن استخدامها للدفاع ضد استراتيجيات محددة ونواقل التهديدات التي تستخدمها الجهات الفاعلة الضارة. تتضمن جميع مجموعات أنشطة برامج الفدية هذه، في مرحلة ما من دورة حياة الهجوم، نشر CobaltStrike Spark على كمبيوتر ضحية لتمكين نشاط لوحة المفاتيح العملي.

يتيح CobaltStrike تخصيص جوانب متعددة من الهجوم، من القدرة على استضافة مستمعين متعددين يستجيبون لبروتوكولات مختلفة، إلى كيفية أداء المكون الرئيسي من جانب العميل (منارة) لحقن التعليمات البرمجية وتشغيل وظائف ما بعد الاستغلال. عندما يكتشف Microsoft Defender CobaltStrike، يمكنه البحث بذكاء عن المؤشرات الرئيسية للاختراق (IoC) وجمعها. بمجرد التقاطها، تتم مشاركة هذه المؤشرات في جميع أنحاء مكدس منتجات Microsoft لأغراض الكشف والحماية.

لا يقتصر اكتشاف الأوامر والتحكم في Microsoft Defender على CobaltStrike. يمكن ل Microsoft Defender التقاط IoCs الرئيسية لعدة مجموعات من البرامج الضارة. تتم مشاركة المؤشرات عبر مكدس حماية Microsoft لحماية العملاء وتنبيههم إذا كان هناك اختراق.

يمكن أن يؤدي حظر اتصال الأوامر والتحكم إلى إعاقة الهجوم المستهدف بشدة، ما يمنح الدفاع الوقت للعثور على متجهات الدخول الأولية وإغلاقها قبل محاولة هجوم أخرى.

<!-- Hide {this intro with no subsequent list items}
[For additional details about Microsoft Defender's command and control detection, see **ADD LINK TO BLOG**.]
-->

## <a name="smart-screen-unblock"></a>إلغاء حظر الشاشة الذكية

تمكن ميزة جديدة في مؤشرات Microsoft Defender لنقطة النهاية المسؤولين من السماح للمستخدمين النهائيين بتجاوز "التحذيرات" التي تم إنشاؤها لبعض عناوين URL وعناوين IP. اعتمادا على سبب حظر URL، عند مصادفة كتلة شاشة ذكية، قد توفر للمسؤولين إمكانية إلغاء حظر الموقع لمدة تصل إلى 24 ساعة. في مثل هذه الحالات، سيظهر إعلام منبثق أمن Windows، مما يسمح للمستخدم النهائي **بإلغاء حظر** عنوان URL أو IP للفترة الزمنية المحددة.  

 > [!div class="mx-imgBorder"]
 > ![إعلام أمن Windows لحماية الشبكة](images/network-protection-smart-screen-block-notification.png)

Microsoft Defender لنقطة النهاية يمكن للمسؤولين تكوين وظيفة إلغاء حظر الشاشة الذكية في [Microsoft 365 Defender](https://security.microsoft.com/)، باستخدام أداة التكوين التالية. من مدخل Microsoft 365 Defender، انتقل إلى المسار إلى ConfigToolName.

<!-- Hide {this intro with no subsequent list items}
[Line 171: Delete the colon and the right angle-brackets. The resulting sentence will be "From the [MS365 Defender] portal, navigate to path to ConfigToolName." Delete "to" and add "the" before path unless a specific description is available. Would a screenshot help? Normally angle brackets or arrows are used in place of certain text rather than in addition.]
-->

 > [!div class="mx-imgBorder"]
 > ![تكوين كتلة الشاشة الذكية لحماية الشبكة ULR ونموذج IP](images/network-protection-smart-screen-block-configuration.png)

## <a name="using-network-protection"></a>استخدام حماية الشبكة

يتم تمكين حماية الشبكة لكل جهاز، والذي يتم عادة باستخدام البنية الأساسية للإدارة. للحصول على الأساليب المدعومة، راجع [تشغيل حماية الشبكة](enable-network-protection.md).

> [!NOTE]
> يجب أن تكون برنامج الحماية من الفيروسات من Microsoft Defender نشطة لتمكين حماية الشبكة.

يمكنك تمكين Network Protection في وضع **التدقيق** أو وضع **الحظر** . إذا كنت تريد تقييم تأثير تمكين Network Protection قبل حظر عناوين IP أو عناوين URL، يمكنك تمكينها في وضع التدقيق لفترة من الوقت لجمع البيانات حول ما سيتم حظره. سجلات وضع التدقيق عندما يتصل المستخدمون بعنوان أو موقع كان سيتم حظره من قبل حماية الشبكة.

## <a name="advanced-hunting"></a>التتبع المتقدم

إذا كنت تستخدم Advanced Hunting لتحديد أحداث التدقيق، فسيكون لديك ما يصل إلى 30 يوما من المحفوظات المتوفرة من وحدة التحكم. راجع [التتبع المتقدم](advanced-hunting-overview.md).

يمكنك العثور على بيانات التدقيق في **التتبع المتقدم** في مدخل Microsoft Defender لنقطة النهاية.  

الأحداث في DeviceEvents مع ActionType of ExploitGuardNetworkProtectionAudited. يتم عرض الكتل بواسطة ExploitGuardNetworkProtectionBlocked.  

يتضمن المثال التالي الإجراءات المحظورة:

DeviceEvents

- Where ActionType in ('ExploitGuardNetworkProtectionAudited','ExploitGuardNetworkProtectionBlocked')

 > [!div class="mx-imgBorder"]
 > ![التتبع المتقدم للتدقيق وتحديد الأحداث](images/network-protection-advanced-hunting.png)

> [!TIP]
> تحتوي هذه الإدخالات على بيانات في عمود AdditionalFields الذي يمنحك معلومات رائعة حول الإجراء، إذا قمت بتوسيع AdditionalFields، يمكنك أيضا الحصول على الحقول: **IsAudit** و **ResponseCategory** و **DisplayName**.

DeviceEvents:

- حيث يحتوي ActionType على "ExploitGuardNetworkProtection"
- توسيع ParsedFields=parse_json(AdditionalFields)
- project DeviceName, ActionType, Timestamp, RemoteUrl, InitiatingProcessFileName, IsAudit=tostring(ParsedFields.IsAudit), ResponseCategory=tostring(ParsedFields.ResponseCategory), DisplayName=tostring(ParsedFields.DisplayName)
- فرز حسب الطابع الزمني

تخبرك فئة الاستجابة بما تسبب في الحدث، على سبيل المثال:

| فئة الاستجابة | الميزة المسؤولة عن الحدث |
|:---|:---|
| CustomPolicy |  WCF  |
| CustomBlockList  |   مؤشرات مخصصة   |
| CasbPolicy   |   Defender for Cloud Apps   |
| الخبيثه   |   تهديدات الويب  |
| التصيّد الاحتيالي  |   تهديدات الويب  |

لمزيد من المعلومات، راجع [استكشاف أخطاء كتل نقاط النهاية وإصلاحها](web-protection-overview.md#troubleshoot-endpoint-blocks).

يمكنك استخدام القائمة الناتجة من عناوين URL وعناوين IP لتحديد ما كان سيتم حظره إذا كان الجهاز في وضع الحظر، بالإضافة إلى الميزة التي حظرتها. راجع كل عنصر في القائمة لتحديد عناوين URL أو عناوين IP سواء كان أي عنصر ضروريا للبيئة الخاصة بك. إذا وجدت أي إدخالات تم تدقيقها والتي تعتبر ضرورية للبيئة الخاصة بك، ف قم بإنشاء مؤشر للسماح بها في شبكتك. السماح لمؤشرات URL / IP بأن تكون لها الأسبقية على أي كتلة.

بمجرد إنشاء مؤشر، يمكنك النظر في حل المشكلة الأساسية:

- الشاشة الذكية – طلب المراجعة
- مؤشر – تعديل المؤشر الموجود
- MCA – مراجعة التطبيق غير المصدق
- WCF – إعادة تصنيف الطلب

باستخدام هذه البيانات، يمكنك اتخاذ قرار مستنير بشأن تمكين حماية الشبكة في وضع الحظر. راجع [ترتيب الأسبقية لكتل حماية الشبكة](web-protection-overview.md#order-of-precedence).

> [!NOTE]
> نظرا لأن هذا إعداد لكل جهاز إذا كانت هناك أجهزة لا يمكنها الانتقال إلى وضع الحظر، يمكنك ببساطة تركها في وضع التدقيق حتى تتمكن من تصحيح التحدي وستستمر في تلقي أحداث التدقيق.

للحصول على معلومات حول كيفية الإبلاغ عن الإيجابيات الخاطئة، راجع [تقرير الإيجابيات الخاطئة](web-protection-overview.md#report-false-positives).

للحصول على تفاصيل حول كيفية إنشاء تقارير Power BI الخاصة بك، راجع [إنشاء تقارير مخصصة باستخدام Power BI](api-power-bi.md).

## <a name="configuring-network-protection"></a>تكوين حماية الشبكة

لمزيد من المعلومات حول كيفية تمكين حماية الشبكة، راجع **[تمكين حماية الشبكة](enable-network-protection.md)**. استخدم نهج المجموعة أو PowerShell أو MDM CSPs لتمكين حماية الشبكة وإدارتها في شبكتك.

بعد تمكين الخدمات، قد تحتاج إلى تكوين الشبكة أو جدار الحماية للسماح بالاتصالات بين الخدمات والأجهزة (يشار إليها أيضا بنقاط النهاية).

- `.smartscreen.microsoft.com`
- `.smartscreen-prod.microsoft.com`

## <a name="viewing-network-protection-events"></a>عرض أحداث حماية الشبكة

تعمل حماية الشبكة بشكل أفضل مع [Microsoft Defender لنقطة النهاية](microsoft-defender-endpoint.md)، والتي تمنحك تقارير مفصلة عن أحداث الحماية من الاستغلال وحظرها كجزء من [سيناريوهات التحقيق في التنبيه](investigate-alerts.md).

عندما تمنع حماية الشبكة الاتصال، يتم عرض إعلام من مركز الصيانة. يمكن لفريق عمليات الأمان [تخصيص الإعلام](attack-surface-reduction-rules-deployment-implement.md#customize-attack-surface-reduction-rules) باستخدام تفاصيل مؤسستك ومعلومات الاتصال الخاصة بها. بالإضافة إلى ذلك، يمكن تمكين قواعد تقليل الأجزاء المعرضة للهجوم الفردي وتخصيصها لتناسب تقنيات معينة للمراقبة.

يمكنك أيضا استخدام [وضع التدقيق](audit-windows-defender.md) لتقييم كيفية تأثير حماية الشبكة على مؤسستك إذا تم تمكينها.

## <a name="review-network-protection-events-in-the-microsoft-365-defender-portal"></a>مراجعة أحداث حماية الشبكة في مدخل Microsoft 365 Defender

يوفر Microsoft Defender لنقطة النهاية تقارير مفصلة عن الأحداث والكتل كجزء من [سيناريوهات التحقيق في التنبيه الخاصة به](investigate-alerts.md). يمكنك عرض هذه التفاصيل في مدخل Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)) في [قائمة انتظار التنبيهات](review-alerts.md) أو باستخدام [التتبع المتقدم](advanced-hunting-overview.md). إذا كنت تستخدم [وضع التدقيق](audit-windows-defender.md)، يمكنك استخدام التتبع المتقدم لمعرفة كيف ستؤثر إعدادات حماية الشبكة على بيئتك إذا تم تمكينها.

فيما يلي مثال استعلام للتتبع المتقدم:

```kusto
DeviceNetworkEvents
|where ActionType in ('ExploitGuardNetworkProtectionAudited','ExploitGuardNetworkProtectionBlocked', 'ConnectionSuccess')
```

## <a name="review-network-protection-events-in-windows-event-viewer"></a>مراجعة أحداث حماية الشبكة في Windows عارض الأحداث

يمكنك مراجعة سجل أحداث Windows للاطلاع على الأحداث التي يتم إنشاؤها عندما تمنع حماية الشبكة (أو تقوم بالتدقيق) الوصول إلى عنوان IP أو مجال ضار:

1. [نسخ XML مباشرة](event-views.md).

2. حدد **موافق**.

ينشئ هذا الإجراء طريقة عرض مخصصة تقوم بالتصفية لإظهار الأحداث التالية المتعلقة بحماية الشبكة فقط:

****

|معرف الحدث|الوصف|
|---|---|
|5007|حدث عند تغيير الإعدادات|
|1125|حدث عند تشغيل حماية الشبكة في وضع التدقيق|
|1126|حدث عند تشغيل حماية الشبكة في وضع الحظر|
|

## <a name="network-protection-and-the-tcp-three-way-handshake"></a>حماية الشبكة والتصاق TCP ثلاثي الاتجاهات

مع حماية الشبكة، يتم تحديد ما إذا كان يجب السماح بالوصول إلى موقع أو حظره بعد الانتهاء من [تأكيد الاتصال ثلاثي الاتجاه عبر TCP/IP](/troubleshoot/windows-server/networking/three-way-handshake-via-tcpip). وبالتالي، عندما يتم حظر موقع بواسطة حماية الشبكة، قد ترى نوع `ConnectionSuccess` إجراء ضمن `NetworkConnectionEvents` في مدخل Microsoft 365 Defender، على الرغم من أنه تم حظر الموقع بالفعل. `NetworkConnectionEvents` يتم الإبلاغ عنها من طبقة TCP، وليس من حماية الشبكة. بعد اكتمال عملية تأكيد الاتصال الثلاثية الاتجاه، يتم السماح بالوصول إلى الموقع أو حظره بواسطة حماية الشبكة.

فيما يلي مثال على كيفية عمل ذلك:

1. لنفترض أن المستخدم يحاول الوصول إلى موقع ويب على جهازه. تتم استضافة الموقع على مجال خطير، ويجب حظره بواسطة حماية الشبكة.  

2. تبدأ عملية تأكيد الاتصال ثلاثية الاتجاه عبر TCP/IP. قبل اكتماله، `NetworkConnectionEvents` يتم تسجيل إجراء، ويتم إدراجه `ActionType` ك `ConnectionSuccess`. ومع ذلك، بمجرد اكتمال عملية تأكيد الاتصال الثلاثية الاتجاه، تمنع حماية الشبكة الوصول إلى الموقع. كل هذا يحدث بسرعة كبيرة. تحدث عملية مماثلة مع [Microsoft Defender SmartScreen](/windows/security/threat-protection/microsoft-defender-smartscreen/microsoft-defender-smartscreen-overview)؛ عندما تكتمل عملية تأكيد الاتصال الثلاثية الاتجاه، يتم إجراء تحديد، ويتم إما حظر الوصول إلى موقع أو السماح به.

3. في مدخل Microsoft 365 Defender، يتم سرد تنبيه في [قائمة انتظار التنبيهات](alerts-queue.md). تتضمن تفاصيل هذا التنبيه كلا `NetworkConnectionEvents` من و `AlertEvents`. يمكنك أن ترى أنه تم حظر الموقع، على الرغم من أن لديك `NetworkConnectionEvents` أيضا عنصرا مع ActionType من `ConnectionSuccess`.

## <a name="considerations-for-windows-virtual-desktop-running-windows-10-enterprise-multi-session"></a>اعتبارات Windows سطح المكتب الظاهري الذي يعمل Windows 10 Enterprise جلسات متعددة

نظرا لطبيعة Windows 10 Enterprise متعددة المستخدمين، ضع النقاط التالية في الاعتبار:

1. حماية الشبكة هي ميزة على مستوى الجهاز ولا يمكن استهدافها بجلسات عمل مستخدم معينة.

2. نهج تصفية محتوى ويب أيضا على مستوى الجهاز.

3. إذا كنت بحاجة إلى التفريق بين مجموعات المستخدمين، ففكر في إنشاء مجموعات وتعيينات منفصلة Windows مضيف سطح المكتب الظاهري.

4. اختبر حماية الشبكة في وضع التدقيق لتقييم سلوكها قبل طرحها.

5. ضع في اعتبارك تغيير حجم النشر إذا كان لديك عدد كبير من المستخدمين أو عدد كبير من جلسات العمل متعددة المستخدمين.

### <a name="alternative-option-for-network-protection"></a>خيار بديل لحماية الشبكة

بالنسبة إلى Windows 10 Enterprise Multi-Session 1909 وما فوق، المستخدمة في Windows Virtual Desktop على Azure، يمكن تمكين حماية الشبكة Microsoft Edge باستخدام الأسلوب التالي:

1. استخدم [تشغيل حماية الشبكة](enable-network-protection.md) واتبع الإرشادات لتطبيق النهج الخاص بك.

2. تنفيذ أوامر PowerShell التالية:
  - `Set-MpPreference -EnableNetworkProtection Enabled`
  - `Set-MpPreference -AllowNetworkProtectionOnWinServer 1`
  - `Set-MpPreference -AllowNetworkProtectionDownLevel 1`
  - `Set-MpPreference -AllowDatagramProcessingOnWinServer 1`

## <a name="network-protection-troubleshooting"></a>استكشاف أخطاء حماية الشبكة وإصلاحها

نظرا للبيئة التي يتم فيها تشغيل حماية الشبكة، قد لا تتمكن Microsoft من الكشف عن إعدادات وكيل نظام التشغيل. في بعض الحالات، يتعذر على عملاء حماية الشبكة الوصول إلى خدمة السحابة. لحل مشكلة الاتصال، يجب على العملاء الذين لديهم تراخيص E5 تكوين أحد مفاتيح التسجيل التالية:

```console
reg add "HKLM\Software\Microsoft\Windows Defender" /v ProxyServer /d "<proxy IP address: Port>" /f
reg add "HKLM\Software\Microsoft\Windows Defender" /v ProxyPacUrl /d "<Proxy PAC url>" /f

```

## <a name="see-also"></a>راجع أيضًا

- [تقييم | حماية الشبكة](evaluate-network-protection.md) قم بسيناريو سريع يوضح كيفية عمل الميزة، وما هي الأحداث التي سيتم إنشاؤها عادة.
- [تمكين حماية الشبكة](enable-network-protection.md) | استخدم نهج المجموعة أو PowerShell أو MDM CSPs لتمكين حماية الشبكة وإدارتها في شبكتك.
- [تكوين قدرات تقليل الأجزاء المعرضة للهجوم في Microsoft Intune](/mem/intune/protect/endpoint-security-asr-policy)
