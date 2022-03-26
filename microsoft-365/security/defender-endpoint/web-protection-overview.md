---
title: حماية ويب
description: تعرف على حماية الويب في Microsoft Defender ل Endpoint وكيفية حماية مؤسستك
keywords: حماية الويب، الحماية من المخاطر على الويب، استعراض الويب، الأمان، التصيد الاحتيالي، البرامج الضارة، استغلال، مواقع الويب، حماية الشبكة، Edge، Internet Explorer، Chrome، Firefox، مستعرض ويب، مواقع الويب الضارة
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.openlocfilehash: d21fdd481ade59ca869d5cfe086e537c0c431228
ms.sourcegitcommit: dd6514ae173f1c821d4ec25298145df6cb232e2e
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 01/19/2022
ms.locfileid: "63572311"
---
# <a name="web-protection"></a>حماية ويب

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**

- [خطة Microsoft Defender لنقطة النهاية 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)


> هل تريد تجربة Microsoft Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-main-abovefoldlink&rtc=1)


## <a name="about-web-protection"></a>حول حماية الويب

إن حماية الويب في Microsoft Defender ل Endpoint هي إمكانية ت تشكل الحماية [](web-threat-protection.md)من تهديدات الويب وتصفية محتوى ويب [والمؤشرات المخصصة](manage-indicators.md). [](web-content-filtering.md) تتيح لك حماية الويب حماية أجهزتك من تهديدات الويب وتساعدك على تنظيم المحتوى غير المرغوب فيه. يمكنك العثور على تقارير حماية ويب في Microsoft 365 Defender من خلال الذهاب إلى **تقارير > ويب**.

:::image type="content" alt-text="صورة لكل بطاقات حماية الويب." source="images/web-protection.png" lightbox="images/web-protection.png":::

### <a name="web-threat-protection"></a>الحماية من المخاطر على الويب

إن البطاقات التي تشكل الحماية من المخاطر على **الويب هي عمليات** الكشف عن تهديدات الويب مع مرور الوقت وملخص **تهديدات الويب**.

تتضمن الحماية من المخاطر على الويب ما يلي:

- رؤية شاملة في تهديدات الويب التي تؤثر على مؤسستك.
- قدرات التحقيق عبر نشاط التهديدات المرتبطة ب الويب من خلال التنبيهات وملفات التعريف الشاملة الخاصة عناوين URL والأجهزة التي تعمل على الوصول إلى عناوين URL هذه.
- مجموعة كاملة من ميزات الأمان التي تتعقب اتجاهات الوصول العامة إلى مواقع الويب الضارة وغير المرغوب فيها.

لمزيد من المعلومات، راجع [الحماية من المخاطر على الويب](web-threat-protection.md).

### <a name="custom-indicators"></a>مؤشرات مخصصة

كما يتم تلخيص عمليات الكشف عن المؤشرات المخصصة في تقارير المخاطر على الويب في مؤسستك ضمن عمليات  الكشف عن تهديدات الويب مع مرور الوقت وملخص **تهديدات الويب**.

يتضمن المؤشر المخصص ما يلي:

- القدرة على إنشاء مؤشرات اختراق مستندة إلى عنوان IP وURL لحماية مؤسستك من التهديدات.
- قدرات التحقيق عبر الأنشطة المتعلقة بملفات تعريف IP/URL المخصصة والأجهزة التي تعمل على الوصول إلى عناوين URL هذه.
- القدرة على إنشاء سياسات السماح والحظر والتحذير ل IPs أو عناوين URL.

لمزيد من المعلومات، راجع [إنشاء مؤشرات ل IPs وURLs/domains](indicator-ip-domain.md)

### <a name="web-content-filtering"></a>تصفية محتوى ويب

تتضمن تصفية محتوى ويب نشاط **ويب حسب الفئة** وملخص تصفية محتوى ويب **وملخص نشاط ويب**. 

تتضمن تصفية محتوى ويب ما يلي:

- يتم منع المستخدمين من الوصول إلى مواقع الويب في الفئات المحظورة، سواء كانوا يستعرضون في الموقع أو خارجها.
- يمكنك بسهولة نشر سياسات متنوعة لمجموعات مختلفة من المستخدمين باستخدام مجموعات الأجهزة المعرفة في إعدادات التحكم بالوصول المستند إلى الدور في [Microsoft Defender لنقطة النهاية](/microsoft-365/security/defender-endpoint/rbac).
- يمكنك الوصول إلى تقارير الويب في الموقع المركزي نفسه، مع إمكانية الرؤية عبر الكتل الفعلية واستخدام الويب.

لمزيد من المعلومات، راجع [تصفية محتوى ويب](web-content-filtering.md).

## <a name="order-of-precedence"></a>ترتيب الأسبقية

ت مكون حماية الويب من المكونات التالية، المدرجة حسب ترتيب الأسبقية. يتم فرض كل مكون من هذه المكونات بواسطة عميل SmartScreen في Microsoft Edge ومن قبل عميل Network Protection في كل المستعرضات والعمليات الأخرى.

- المؤشرات المخصصة (IP/URL ونهج Microsoft Defender for Cloud Apps)
  - السماح
  - تحذير
  - حظر

- تهديدات الويب (البرامج الضارة والتصيد الاحتيالي)
  - SmartScreen Intel، بما في ذلك Exchange Online Protection (EOP)
  - تصعيدات

- تصفية محتوى ويب (WCF)

> [!NOTE]
> ينشئ Microsoft Defender for Cloud Apps حاليا مؤشرات عناوين URL المحظورة فقط.

يرتبط ترتيب الأسبقية بالترتيب الذي يتم به تقييم عنوان URL أو IP. على سبيل المثال، إذا كان لديك نهج تصفية محتوى ويب، يمكنك إنشاء استثناءات من خلال مؤشرات IP/URL مخصصة. مؤشرات اختراق مخصصة (IoC) أعلى في ترتيب الأسبقية من كتل WCF.

وبشكل مماثل، أثناء التعارض بين المؤشرات، يسمح دائما بأن تكون الأسبقية على الكتل (منطق التجاوز). وهذا يعني أن مؤشر السماح سيربح على أي مؤشر كتلة موجود.

يلخص الجدول أدناه بعض التكوينات الشائعة التي من شأنها أن تقدم تعارضات داخل مكدس حماية الويب. كما تحدد أيضا التحديدات الناتجة استنادا إلى الأسبقية المذكورة أعلاه.

<br>

****

|نهج المؤشر المخصص|نهج تهديدات الويب|نهج WCF|نهج Defender for Cloud Apps|النتيجة|
|---|---|---|---|---|
|السماح|حظر|حظر|حظر|السماح (تجاوز حماية ويب)|
|السماح|السماح|حظر|حظر|السماح (استثناء WCF)|
|تحذير|حظر|حظر|حظر|التحذير (تجاوز)|
|

لا تدعم المؤشرات المخصصة عناوين IP الداخلية. بالنسبة إلى نهج التحذير عند تجاوز المستخدم له، سيتم إلغاء حظر الموقع لمدة 24 ساعة لهذا المستخدم بشكل افتراضي. يمكن تعديل هذا الإطار الزمني من قبل المسؤول، ويمكن تمريره بواسطة خدمة SmartScreen السحابية. يمكن أيضا تعطيل القدرة على تجاوز تحذير في Microsoft Edge باستخدام CSP لحظر تهديدات الويب (البرامج الضارة/التصيد الاحتيالي). لمزيد من المعلومات، راجع Microsoft Edge [SmartScreen الإعدادات](/DeployEdge/microsoft-edge-policies#smartscreen-settings-policies).

## <a name="protect-browsers"></a>حماية المستعرضات

في كل سيناريوهات حماية الويب، يمكن استخدام SmartScreen و Network Protection معا لضمان الحماية عبر كل من المستعرضات والعمليات الأولى وال الجهة الخارجية. يتم بناء SmartScreen مباشرة في Microsoft Edge، بينما تراقب "حماية الشبكة" حركة المرور في المستعرضات والعمليات الخاصة ب جهة خارجية. يوضح الرسم التخطيطي أدناه هذا المفهوم. هذا الرسم التخطيطي للعملاء الذين يعملون معا لتوفير تغطية متعددة للمستعرض/التطبيق دقيق لجميع ميزات حماية ويب (المؤشرات، تهديدات الويب، تصفية المحتوى).

:::image type="content" alt-text="استخدام SmartScreen وحماية الشبكة معا." source="../../media/web-protection-protect-browsers.png" lightbox="../../media/web-protection-protect-browsers.png":::

## <a name="troubleshoot-endpoint-blocks"></a>استكشاف كتل نقاط النهاية وإصلاحها

يتم توحيد الاستجابات من سحابة SmartScreen. يمكن استخدام أدوات مثل Fiddler لفحص الاستجابة من الخدمة السحابية، مما سيساعد على تحديد مصدر الكتلة.

عندما تستجيب خدمة SmartScreen السحابية مع استجابة السماح أو الحظر أو التحذير، يتم ترحيل فئة الاستجابة وسياق الخادم مرة أخرى إلى العميل. في Microsoft Edge، يتم استخدام فئة الاستجابة لتحديد صفحة الحظر المناسبة لإظهارها (ضار وتصيد احتيالي ونمص هيكلي).

يعرض الجدول أدناه الاستجابات والميزات المرتبطة بها.

<br>

****

|ResponseCategory|الميزة المسؤولة عن الحظر|
|---|---|
|CustomPolicy|WCF|
|CustomBlockList|مؤشرات مخصصة|
|CasbPolicy|Defender for Cloud Apps|
|ضار|تهديدات الويب|
|التصيد الاحتيالي|تهديدات الويب|
|||

## <a name="advanced-hunting-for-web-protection"></a>البحث المتقدم عن الحماية على الويب

يمكن استخدام استعلامات Kusto في الصيد المتقدم لتلخيص كتل حماية الويب في مؤسستك لمدة تصل إلى 30 يوما. تستخدم هذه الاستعلامات المعلومات المذكورة أعلاه للتمييز بين مصادر الكتل المختلفة وتلخيصها بطريقة سهلة الاستخدام. على سبيل المثال، يسرد الاستعلام أدناه كل كتل WCF التي تنشأ من Microsoft Edge.

```kusto
DeviceEvents
| where ActionType == "SmartScreenUrlWarning"
| extend ParsedFields=parse_json(AdditionalFields)
| project DeviceName, ActionType, Timestamp, RemoteUrl, InitiatingProcessFileName, Experience=tostring(ParsedFields.Experience)
| where Experience == "CustomBlockList"
```

وبالمثل، يمكنك استخدام الاستعلام أدناه لقائمة كل كتل WCF التي تنشأ من حماية الشبكة (على سبيل المثال، كتلة WCF في مستعرض جهة خارجية). تجدر الإشارة إلى أنه تم تحديث ActionType وتغيير 'التجربة' إلى 'ResponseCategory'.

```kusto
DeviceEvents
| where ActionType == "ExploitGuardNetworkProtectionBlocked"
| extend ParsedFields=parse_json(AdditionalFields)
| project DeviceName, ActionType, Timestamp, RemoteUrl, InitiatingProcessFileName, ResponseCategory=tostring(ParsedFields.ResponseCategory)
| where ResponseCategory == "CustomPolicy"
```

لقائمة الكتل التي يعود سببها إلى ميزات أخرى (مثل المؤشرات المخصصة)، راجع الجدول أعلاه الذي يوضح كل ميزة وفئة الاستجابة الخاصة بها. قد يتم أيضا تعديل هذه الاستعلامات للبحث عن بيانات التكليف ذات الصلة بآلات معينة في مؤسستك. لاحظ أن نوع الإجراء الموضح في كل استعلام أعلاه سيعرض فقط الاتصالات التي تم حظرها بواسطة ميزة حماية ويب، وليس كل حركة مرور الشبكة.

## <a name="user-experience"></a>تجربة المستخدم

إذا قام مستخدم بزيارة صفحة ويب تشكل خطرا من البرامج الضارة أو التصيد الاحتيالي أو أي تهديدات أخرى على الويب، سيشغل Microsoft Edge صفحة حظر تقرأ "تم إعلام هذا الموقع بأنه غير آمن" إلى جانب المعلومات ذات الصلة بالخطر.

> [!div class="mx-imgBorder"]
> ![الصفحة المحظورة بواسطة Microsoft Edge.](../../media/web-protection-malicious-block.png)

إذا تم حظرها بواسطة WCF أو مؤشر مخصص، تظهر صفحة حظر في Microsoft Edge تخبر المستخدم بأن هذا الموقع تم حظره من قبل المؤسسة.

> [!div class="mx-imgBorder"]
> ![الصفحة التي حظرتها مؤسستك.](../../media/web-protection-indicator-blockpage.png)

على أي حال، لا يتم عرض صفحات الحظر في مستعرضات  الأطراف الخارجية، وسيرى المستخدم صفحة "فشل الاتصال الآمن" إلى جانب إعلام منسدل. استنادا إلى النهج المسؤول عن الحظر، سيشاهد المستخدم رسالة مختلفة في الإعلام المنبثق. على سبيل المثال، ستعرض تصفية محتوى الويب الرسالة 'تم حظر هذا المحتوى'.

> [!div class="mx-imgBorder"]
> ![صفحة تم حظرها بواسطة WCF.](../../media/web-protection-np-block.png)

## <a name="report-false-positives"></a>الإبلاغ عن إيجابيات خاطئة

للتقارير عن خطأ موجب للمواقع التي تعتبرها SmartScreen خطرة، استخدم الارتباط الذي يظهر على صفحة الحظر في Microsoft Edge (كما هو موضح أعلاه).

بالنسبة إلى WCF، يمكنك النزاع على فئة مجال. انتقل إلى **علامة التبويب** المجالات لتقارير WCF، ثم انقر فوق **تقرير عدم الدقة**. سيتم فتح منتفتحة. تعيين أولوية الحادث وتوفير بعض التفاصيل الإضافية، مثل الفئة المقترحة. لمزيد من المعلومات حول كيفية تشغيل WCF وكيفية النزاع على الفئات، راجع [تصفية محتوى ويب](web-content-filtering.md).

لمزيد من المعلومات حول كيفية إرسال الإيجابيات/السلبيات الخاطئة، راجع [عنوان الإيجابيات/السلبيات الخاطئة في Microsoft Defender لنقطة النهاية](defender-endpoint-false-positives-negatives.md).

## <a name="related-information"></a>المعلومات ذات الصلة

<br>

****

|الموضوع|الوصف|
|---|---|
|[الحماية من المخاطر على الويب](web-threat-protection.md) | إيقاف الوصول إلى مواقع التصيد الاحتيالي، و متجهات البرامج الضارة، والمواقع المستغلة، والمواقع غير الملوثة أو ذات السمعة المنخفضة، والمواقع التي قمت بحظرها.|
|[تصفية محتوى ويب](web-content-filtering.md) | تعقب الوصول إلى مواقع الويب وتنظيمه استنادا إلى فئات المحتوى الخاصة بها.|
|
