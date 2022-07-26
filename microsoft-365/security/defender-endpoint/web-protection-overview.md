---
title: حماية ويب
description: تعرف على حماية الويب في Microsoft Defender لنقطة النهاية وكيف يمكنها حماية مؤسستك
keywords: حماية الويب، والحماية من تهديدات الويب، واستعراض الويب، والأمان، والتصيد الاحتيالي، والبرامج الضارة، والاستغلال، ومواقع الويب، وحماية الشبكة، وEdge، وInternet Explorer، وChrome، وFirefox، ومستعرض الويب، ومواقع الويب الضارة
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
ms.date: 07/25/2022
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.openlocfilehash: e54b3c1c696d05bb0f3815b532a4f0e7e92c6331
ms.sourcegitcommit: 6e570b79944862c86735db455349b685d5b903b6
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/26/2022
ms.locfileid: "67020638"
---
# <a name="web-protection"></a>حماية ويب

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**

- [الخطة 1 من Microsoft Defender لنقطة النهاية](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Defender for Endpoint الخطة 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)


> هل تريد تجربة Defender لنقطة النهاية؟ [التسجيل للحصول على إصدار تجريبي مجاني.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-main-abovefoldlink&rtc=1)


## <a name="about-web-protection"></a>حول حماية الويب

حماية الويب في Microsoft Defender لنقطة النهاية هي قدرة تتكون من [الحماية من تهديدات الويب](web-threat-protection.md) [وتصفية محتوى الويب](web-content-filtering.md) [والمؤشرات المخصصة](manage-indicators.md). تتيح لك حماية الويب تأمين أجهزتك ضد تهديدات الويب وتساعدك على تنظيم المحتوى غير المرغوب فيه. يمكنك العثور على تقارير حماية الويب في مدخل Microsoft 365 Defender عن طريق الانتقال إلى **التقارير > حماية الويب**.

:::image type="content" source="images/web-protection.png" alt-text="بطاقات حماية الويب" lightbox="images/web-protection.png":::

### <a name="web-threat-protection"></a>الحماية من المخاطر على الويب

البطاقات التي تشكل الحماية من تهديدات الويب هي **عمليات الكشف عن تهديدات الويب بمرور الوقت** **وملخص مخاطر الويب**.

تتضمن الحماية من تهديدات الويب ما يلي:

- رؤية شاملة لتهديدات الويب التي تؤثر على مؤسستك.
- قدرات التحقيق عبر نشاط التهديد المرتبط بالويب من خلال التنبيهات وملفات التعريف الشاملة لعناوين URL والأجهزة التي تصل إلى عناوين URL هذه.
- مجموعة كاملة من ميزات الأمان التي تتعقب اتجاهات الوصول العامة إلى مواقع الويب الضارة وغير المرغوب فيها.

لمزيد من المعلومات، راجع [الحماية من تهديدات الويب](web-threat-protection.md).

### <a name="custom-indicators"></a>مؤشرات مخصصة

يتم أيضا تلخيص عمليات الكشف عن المؤشرات المخصصة في تقارير تهديدات الويب الخاصة بالمنظمات ضمن **عمليات الكشف عن تهديدات الويب بمرور الوقت** **وملخص مخاطر الويب**.

يتضمن المؤشر المخصص ما يلي:

- القدرة على إنشاء مؤشرات IP ومؤشرات الاختراق المستندة إلى عنوان URL لحماية مؤسستك من التهديدات.
- قدرات التحقيق على الأنشطة المتعلقة بملفات تعريف IP/URL المخصصة والأجهزة التي تصل إلى عناوين URL هذه.
- القدرة على إنشاء نهج السماح والحظر والتحذير لعناوين IP وعناوين URL.

لمزيد من المعلومات، راجع [إنشاء مؤشرات لعناوين IP وعناوين URL/المجالات](indicator-ip-domain.md)

### <a name="web-content-filtering"></a>تصفية محتوى ويب

تتضمن تصفية محتوى ويب **نشاط ويب حسب الفئة** **وملخص تصفية محتوى ويب** **وملخص نشاط ويب**.

تتضمن تصفية محتوى ويب ما يلي:

- يتم منع المستخدمين من الوصول إلى مواقع الويب في الفئات المحظورة، سواء كانوا يتصفحون محليا أو بالخارج.
- يمكنك نشر نهج متنوعة إلى مجموعات مختلفة من المستخدمين بسهولة باستخدام مجموعات الأجهزة المحددة في [إعدادات التحكم في الوصول المستندة إلى الدور Microsoft Defender لنقطة النهاية](/microsoft-365/security/defender-endpoint/rbac).
- يمكنك الوصول إلى تقارير الويب في نفس الموقع المركزي، مع الرؤية عبر الكتل الفعلية واستخدام الويب.

لمزيد من المعلومات، راجع [تصفية محتوى ويب](web-content-filtering.md).

## <a name="order-of-precedence"></a>ترتيب الأسبقية

تتكون حماية الويب من المكونات التالية، المدرجة بترتيب الأسبقية. يتم فرض كل مكون من هذه المكونات بواسطة عميل SmartScreen في Microsoft Edge ومن قبل عميل Network Protection في جميع المستعرضات والعمليات الأخرى.

- المؤشرات المخصصة (IP/URL، نهج Microsoft Defender for Cloud Apps)
  - سماح
  - تحذير
  - حظر

- تهديدات الويب (البرامج الضارة، التصيد الاحتيالي)
  - SmartScreen Intel، بما في ذلك Exchange Online Protection (EOP)
  - التصعيد

- تصفية محتوى ويب (WCF)

> [!NOTE]
> تنشئ Microsoft Defender for Cloud Apps حاليا مؤشرات لعناوين URL المحظورة فقط.

يتعلق ترتيب الأسبقية بترتيب العمليات التي يتم من خلالها تقييم عنوان URL أو IP. على سبيل المثال، إذا كان لديك نهج تصفية محتوى ويب، يمكنك إنشاء استثناءات من خلال مؤشرات IP/URL المخصصة. مؤشرات الاختراق المخصصة (IoC) أعلى في ترتيب الأسبقية من كتل WCF.

وبالمثل، في أثناء التعارض بين المؤشرات، يسمح دائما بأخذ الأسبقية على الكتل (تجاوز المنطق). وهذا يعني أن مؤشر السماح سيفوز على أي مؤشر كتلة موجود.

يلخص الجدول أدناه بعض التكوينات الشائعة التي من شأنها أن تمثل تعارضات داخل مكدس حماية الويب. كما يحدد التحديدات الناتجة استنادا إلى الأسبقية المذكورة أعلاه.

<br>

****

|نهج المؤشر المخصص|نهج مخاطر الويب|نهج WCF|نهج Defender for Cloud Apps|نتيجه|
|---|---|---|---|---|
|سماح|حظر|حظر|حظر|السماح (تجاوز حماية ويب)|
|سماح|سماح|حظر|حظر|السماح (استثناء WCF)|
|تحذير|حظر|حظر|حظر|تحذير (تجاوز)|
|

لا تدعم المؤشرات المخصصة عناوين IP الداخلية. بالنسبة إلى نهج التحذير عند تجاوزه من قبل المستخدم النهائي، سيتم إلغاء حظر الموقع لمدة 24 ساعة لهذا المستخدم بشكل افتراضي. يمكن تعديل هذا الإطار الزمني بواسطة مسؤول ويتم تمريره لأسفل بواسطة خدمة SmartScreen السحابية. يمكن أيضا تعطيل القدرة على تجاوز تحذير في Microsoft Edge باستخدام CSP لحجب تهديدات الويب (البرامج الضارة/التصيد الاحتيالي). لمزيد من المعلومات، راجع [إعدادات الشاشة الذكية ل Microsoft Edge](/DeployEdge/microsoft-edge-policies#smartscreen-settings-policies).

## <a name="protect-browsers"></a>حماية المستعرضات

في جميع سيناريوهات حماية الويب، يمكن استخدام SmartScreen وحماية الشبكة معا لضمان الحماية عبر كل من مستعرضات وعمليات الجهات الخارجية والأولى. تم تضمين SmartScreen مباشرة في Microsoft Edge، بينما تراقب Network Protection نسبة استخدام الشبكة في مستعرضات وعمليات الجهات الخارجية. يوضح الرسم التخطيطي أدناه هذا المفهوم. هذا الرسم التخطيطي للعملاء اللذين يعملان معا لتوفير تغطية متعددة للمستعرض/التطبيق دقيق لجميع ميزات حماية الويب (المؤشرات، تهديدات الويب، تصفية المحتوى).

:::image type="content" source="../../media/web-protection-protect-browsers.png" alt-text="استخدام smartScreen وحماية الشبكة معا" lightbox="../../media/web-protection-protect-browsers.png":::

## <a name="troubleshoot-endpoint-blocks"></a>استكشاف أخطاء كتل نقاط النهاية وإصلاحها

يتم توحيد الاستجابات من سحابة SmartScreen. يمكن استخدام أدوات مثل Fiddler لفحص الاستجابة من خدمة السحابة، والتي ستساعد في تحديد مصدر الكتلة.

عندما تستجيب خدمة SmartScreen السحابية باستجابة السماح أو الحظر أو التحذير، يتم ترحيل فئة الاستجابة وسياق الخادم مرة أخرى إلى العميل. في Microsoft Edge، فئة الاستجابة هي ما يتم استخدامه لتحديد صفحة الحظر المناسبة لإظهارها (الضار والتصيد الاحتيالي والنهج التنظيمي).

يعرض الجدول أدناه الاستجابات وميزاتها المرتبطة.

<br>

****

|فئة الاستجابة|الميزة المسؤولة عن الكتلة|
|---|---|
|CustomPolicy|WCF|
|CustomBlockList|مؤشرات مخصصة|
|CasbPolicy|Defender for Cloud Apps|
|الخبيثه|تهديدات الويب|
|التصيّد الاحتيالي|تهديدات الويب|
|||

## <a name="advanced-hunting-for-web-protection"></a>التتبع المتقدم لحماية الويب

يمكن استخدام استعلامات Kusto في التتبع المتقدم لتلخيص كتل حماية الويب في مؤسستك لمدة تصل إلى 30 يوما. تستخدم هذه الاستعلامات المعلومات المذكورة أعلاه للتمييز بين مصادر الكتل المختلفة وتلخيصها بطريقة سهلة الاستخدام. على سبيل المثال، يسرد الاستعلام أدناه كافة كتل WCF التي تنشأ من Microsoft Edge.

```kusto
DeviceEvents
| where ActionType == "SmartScreenUrlWarning"
| extend ParsedFields=parse_json(AdditionalFields)
| project DeviceName, ActionType, Timestamp, RemoteUrl, InitiatingProcessFileName, Experience=tostring(ParsedFields.Experience)
| where Experience == "CustomPolicy"
```

وبالمثل، يمكنك استخدام الاستعلام أدناه لإدراج كافة كتل WCF التي تنشأ من Network Protection (على سبيل المثال، كتلة WCF في مستعرض جهة خارجية). لاحظ أنه تم تحديث ActionType وتم تغيير "Experience" إلى "ResponseCategory".

```kusto
DeviceEvents
| where ActionType == "ExploitGuardNetworkProtectionBlocked"
| extend ParsedFields=parse_json(AdditionalFields)
| project DeviceName, ActionType, Timestamp, RemoteUrl, InitiatingProcessFileName, ResponseCategory=tostring(ParsedFields.ResponseCategory)
| where ResponseCategory == "CustomPolicy"
```

لإدراج كتل ناتجة عن ميزات أخرى (مثل المؤشرات المخصصة)، راجع الجدول أعلاه الذي يوضح كل ميزة وفئة الاستجابة الخاصة بها. يمكن أيضا تعديل هذه الاستعلامات للبحث عن بيانات تتبع الاستخدام المتعلقة بأجهزة معينة في مؤسستك. لاحظ أن ActionType المعروض في كل استعلام أعلاه سيعرض فقط تلك الاتصالات التي تم حظرها بواسطة ميزة حماية ويب، وليس كل نسبة استخدام الشبكة.

## <a name="user-experience"></a>تجربة المستخدم

إذا قام مستخدم بزيارة صفحة ويب تشكل مخاطر البرامج الضارة أو التصيد الاحتيالي أو تهديدات الويب الأخرى، فسيشغل Microsoft Edge صفحة حظر تقرأ "تم الإبلاغ عن هذا الموقع على أنه غير آمن" إلى جانب المعلومات المتعلقة بالخطر.

> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/web-protection-malicious-block.png" alt-text="الصفحة المحظورة بواسطة Microsoft Edge" lightbox="../../media/web-protection-malicious-block.png":::

إذا تم حظره بواسطة WCF أو مؤشر مخصص، تظهر صفحة كتلة في Microsoft Edge تخبر المستخدم بأن هذا الموقع محظور من قبل مؤسسته.

> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/web-protection-indicator-blockpage.png" alt-text="الصفحة المحظورة من قبل مؤسستك" lightbox="../../media/web-protection-indicator-blockpage.png":::

على أي حال، لا يتم عرض صفحات الحظر في مستعرضات الجهات الخارجية، وسيرى المستخدم صفحة "فشل الاتصال الآمن" مع إعلام منبثق. اعتمادا على النهج المسؤول عن الكتلة، سيرى المستخدم رسالة مختلفة في الإعلام المنبثق. على سبيل المثال، ستعرض تصفية محتوى ويب الرسالة "تم حظر هذا المحتوى".

> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/web-protection-np-block.png" alt-text="الصفحة المحظورة بواسطة WCF" lightbox="../../media/web-protection-np-block.png":::

## <a name="report-false-positives"></a>الإبلاغ عن الإيجابيات الخاطئة

للإبلاغ عن إيجابية خاطئة للمواقع التي تعتبرها SmartScreen خطرة، استخدم الارتباط الذي يظهر على صفحة الكتلة في Microsoft Edge (كما هو موضح أعلاه).

بالنسبة إلى WCF، يمكنك النزاعات على فئة المجال. انتقل إلى علامة التبويب **"المجالات** " في تقارير WCF، ثم انقر فوق **"عدم دقة التقرير**". سيتم فتح قائمة منبثقة. تعيين أولوية الحدث وتوفير بعض التفاصيل الإضافية، مثل الفئة المقترحة. لمزيد من المعلومات حول كيفية تشغيل WCF وكيفية النزاعات على الفئات، راجع [تصفية محتوى ويب](web-content-filtering.md).

لمزيد من المعلومات حول كيفية إرسال الإيجابيات/السلبيات الخاطئة، راجع ["العنوان" الإيجابيات/السلبيات الخاطئة في Microsoft Defender لنقطة النهاية](defender-endpoint-false-positives-negatives.md).

## <a name="related-information"></a>المعلومات ذات الصلة

<br>

****

|الموضوع|الوصف|
|---|---|
|[الحماية من المخاطر على الويب](web-threat-protection.md) | أوقف الوصول إلى مواقع التصيد الاحتيالي، وناقلات البرامج الضارة، ومواقع الاستغلال، والمواقع غير الموثوق بها أو ذات السمعة المنخفضة، والمواقع التي حظرتها.|
|[تصفية محتوى ويب](web-content-filtering.md) | تعقب الوصول إلى مواقع الويب وتنظيمه استنادا إلى فئات المحتوى الخاصة بها.|
|
