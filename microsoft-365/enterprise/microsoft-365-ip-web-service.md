---
title: Office 365 IP وخدمة URL على الويب
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 8/6/2019
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
ms.localizationpriority: high
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
- m365initiative-coredeploy
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- seo-marvel-apr2020
ms.reviewer: pandrew
search.appverid:
- MET150
- MOE150
- BCS160
description: تعرف على كيفية استخدام Office 365 IP وخدمة URL على الويب لمساعدتك على التعرف بشكل أفضل Office 365 المرور على الشبكة.
ms.openlocfilehash: e4976bafbedc8f5289e2992569bbd5de28e9de75
ms.sourcegitcommit: 584b4757f715a3eedf748858461c568f45137438
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/15/2022
ms.locfileid: "63572897"
---
# <a name="office-365-ip-address-and-url-web-service"></a>Office 365 IP وخدمة URL على الويب

تساعدك Office 365 عنوان IP وخدمة URL على تحديد حركة مرور الشبكة Office 365 بشكل أفضل، مما يسهل عليك تقييم التغييرات وتكوينها والبقاء على اتصال بها. تحل خدمة الويب المستندة إلى REST هذه محل ملفات XML السابقة القابلة للتنزيل، والتي تم ازالتها في 2 أكتوبر 2018.

كعميل أو كمورد جهاز محيط للشبكة، يمكنك البناء مقابل خدمة الويب Office 365 IP وإد إدخالات FQDN. يمكنك الوصول إلى البيانات مباشرة في مستعرض ويب باستخدام عناوين URL هذه:

- للحصول على الإصدار الأخير من نطاقات عناوين IP Office 365 URL، استخدم [https://endpoints.office.com/version](https://endpoints.office.com/version?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7).
- بالنسبة للبيانات الموجودة على صفحة نطاقات عناوين IP Office 365 عناوين URL وعنونات IP لجدارات الحماية وخادمات الوكيل، استخدم [https://endpoints.office.com/endpoints/worldwide](https://endpoints.office.com/endpoints/worldwide?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7).
- للحصول على جميع التغييرات الأخيرة منذ يوليو 2018 عندما كانت خدمة الويب متوفرة لأول مرة، استخدم [https://endpoints.office.com/changes/worldwide/0000000000](https://endpoints.office.com/changes/worldwide/0000000000?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7).

كعميل، يمكنك استخدام خدمة الويب هذه من أجل:

- قم بتحديث البرامج النصية في PowerShell للحصول على Office 365 نقاط النهاية وتعديل أي تنسيق لأجهزة الشبكة.
- استخدم هذه المعلومات لتحديث ملفات PAC التي تم نشرها على أجهزة الكمبيوتر العميلة.

كمورد جهاز محيط للشبكة، يمكنك استخدام خدمة الويب هذه من أجل:

- إنشاء برنامج جهاز واختباره لتنزيل القائمة للتكوين التلقائي.
- تحقق من الإصدار الحالي.
- احصل على التغييرات الحالية.

> [!NOTE]
> إذا كنت تستخدم Azure ExpressRoute للاتصال Office 365، فالرجاء مراجعة [Azure ExpressRoute ل Office 365](azure-expressroute.md) لتطلع على خدمات Office 365 المعتمدة عبر Azure ExpressRoute. راجع أيضا المقالة Office 365 [عناوين URL](urls-and-ip-address-ranges.md) ونطاقات عناوين IP لفهم طلبات الشبكة الخاصة Office 365 التطبيقات التي تتطلب اتصالا بالإنترنت. سيساعدك هذا على تكوين أجهزة الأمان المحيطة بشكل أفضل.

لمزيد من المعلومات، اطلع على:

- [منشور مدونة إعلان في منتدى مجتمع Office 365 التقني](https://techcommunity.microsoft.com/t5/Office-365-Blog/Announcing-Office-365-endpoint-categories-and-Office-365-IP/ba-p/177638)
- [Office 365 منتدى المجتمع التقني للأسئلة حول استخدام خدمات الويب](https://techcommunity.microsoft.com/t5/Office-365-Networking/bd-p/Office365Networking)

## <a name="common-parameters"></a>المعلمات الشائعة

هذه المعلمات شائعة عبر جميع أساليب خدمة الويب:

- **format=\<JSON \| CSV\>** —بشكل افتراضي، تنسيق البيانات الذي يتم إرجاعه هو JSON. استخدم هذه المعلمة الاختيارية لإرجاع البيانات بتنسيق قيم مفصولة بفصول (CSV).
- **ClientRequestId=\<guid\>** —GUID مطلوب تقوم بإنشاءه لاقتران العميل. إنشاء GUID فريد لكل جهاز يستدعي خدمة الويب (تقوم البرامج النصية المضمنة في هذه الصفحة بإنشاء GUID لك). لا تستخدم GUIDs الموضحة في الأمثلة التالية لأنه قد يتم حظرها بواسطة خدمة الويب في المستقبل. تنسيق GUID هو _xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx،_ حيث تمثل x رقما ست عشريا.

  لإنشاء GUID، يمكنك استخدام الأمر [New-Guid](/powershell/module/microsoft.powershell.utility/new-guid) PowerShell، أو استخدام خدمة عبر الإنترنت مثل ["منشئ GUID عبر الإنترنت](https://www.guidgenerator.com/)".

## <a name="version-web-method"></a>أسلوب الإصدار على الويب

تقوم Microsoft بتحديث Office 365 IP وإد إدخالات FQDN في بداية كل شهر. في بعض الأحيان، يتم نشر التحديثات خارج النطاق بسبب أحداث الدعم أو تحديثات الأمان أو متطلبات التشغيل الأخرى.

يتم تعيين رقم إصدار للبيانات الخاصة بكل مثيل منشور، وتمكنك طريقة الإصدار على الويب من التحقق من الإصدار الأخير من كل Office 365 الخدمة. نوصي بالتحقق من الإصدار على ألا يزيد عن مرة واحدة في الساعة.

معلمات أسلوب الإصدار على الويب هي:

- **AllVersions=\<true \| false\>** —بشكل افتراضي، الإصدار الذي تم إرجاعه هو الأحدث. قم بتضمين هذه المعلمة الاختيارية لطلب كل الإصدارات المنشورة منذ إصدار خدمة الويب لأول مرة.
- **Format=\<JSON \| CSV \| RSS\>** —بالإضافة إلى تنسيقي JSON و CSV، يدعم أسلوب الإصدار على الويب أيضا RSS. يمكنك استخدام هذه المعلمة الاختيارية مع _المعلمة AllVersions=true_ لطلب موجز RSS يمكن استخدامه مع Outlook RSS أخرى.
- **مثيل=\<Worldwide \| China \| USGovDoD \| USGovGCCHigh\>** —تحدد هذه المعلمة الاختيارية المثيل لإرجاع الإصدار ل. إذا تم حذفها، يتم إرجاع كل المثيلات. المثيلات الصالحة هي: على مستوى العالم، الصين، USGovDoD، USGovGCCHigh.

أسلوب الإصدار على الويب غير محدود ولا يقوم أبدا بإرجاع 429 رمز استجابة HTTP. تتضمن الاستجابة لطريقة الإصدار على الويب رأسا للتحكم في ذاكرة التخزين المؤقت يوصي با التخزين المؤقت للبيانات لمدة ساعة واحدة. يمكن أن تكون النتيجة من أسلوب الإصدار على الويب سجلا واحدا أو صفيفا من السجلات. إن عناصر كل سجل هي:

- مثيل —الاسم القصير لمثيل Office 365 الخدمة.
- أحدث إصدار لنقاط نهاية المثيل المحدد.
- الإصدارات— قائمة بكل الإصدارات السابقة للمثيل المحدد. يتم تضمين هذا العنصر فقط إذا كانت _المعلمة AllVersions_ صحيحة.

### <a name="version-web-method-examples"></a>أمثلة حول أسلوب الإصدار على الويب

مثال 1 لطلب URI: <https://endpoints.office.com/version?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7>

يرجع URI هذا الإصدار الأخير من كل Office 365 خدمة. مثال على النتيجة:

```json
[
 {
  "instance": "Worldwide",
  "latest": "2018063000"
 },
 {
  "instance": "USGovDoD",
  "latest": "2018063000"
 },
 {
  "instance": "USGovGCCHigh",
  "latest": "2018063000"
 },
 {
  "instance": "China",
  "latest": "2018063000"
 }
]
```

> [!IMPORTANT]
> إن GUID لمعلمة ClientRequestID في هذه URIs هي مثال فقط. لمحاولة استخدام URIs لخدمة الويب، يمكنك إنشاء GUID الخاص بك. قد يتم حظر GUIDs الموضحة في هذه الأمثلة بواسطة خدمة الويب في المستقبل.

مثال 2 لطلب URI: <https://endpoints.office.com/version/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7>

يرجع URI هذا الإصدار الأخير من مثيل خدمة Office 365 المحدد. مثال على النتيجة:

```json
{
 "instance": "Worldwide",
 "latest": "2018063000"
}
```

مثال 3 لطلب URI: <https://endpoints.office.com/version/Worldwide?Format=CSV&ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7>

يعرض URI هذا الإخراج بتنسيق CSV. مثال على النتيجة:

```csv
instance,latest
Worldwide,2018063000
```

مثال 4 لطلب URI: <https://endpoints.office.com/version/Worldwide?AllVersions=true&ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7>

يعرض URI هذا كل الإصدارات السابقة التي تم نشرها لمثيل Office 365 الخدمة على مستوى العالم. مثال على النتيجة:

```json
{
  "instance": "Worldwide",
  "latest": "2018063000",
  "versions": [
    "2018063000",
    "2018062000"
  ]
}
```

مثال 5 RSS Feed URI: <https://endpoints.office.com/version/worldwide?clientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7&allVersions=true&format=RSS>

يعرض URI هذا موجز RSS للإصدارات المنشورة التي تتضمن ارتباطات إلى قائمة التغييرات لكل إصدار. مثال على النتيجة:

```xml
<?xml version="1.0" encoding="ISO-8859-1"?>
<rss version="2.0" xmlns:a10="https://www.w3.org/2005/Atom">
<channel>
<link>https://aka.ms/o365ip</link>
<description/>
<language>en-us</language>
<lastBuildDate>Thu, 02 Aug 2018 00:00:00 Z</lastBuildDate>
<item>
<guid isPermaLink="false">2018080200</guid>
<link>https://endpoints.office.com/changes/Worldwide/2018080200?singleVersion&clientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7</link> <description>Version 2018080200 includes 2 changes. IPs: 2 added and 0 removed.</description>
<pubDate>Thu, 02 Aug 2018 00:00:00 Z</pubDate>
</item>
```

## <a name="endpoints-web-method"></a>أسلوب نقاط النهاية على الويب

يرجع أسلوب نقاط النهاية على الويب كل السجلات لنطاقات عناوين IP أو عناوين URL التي Office 365 الخدمة. يجب دائما استخدام أحدث البيانات من أسلوب نقاط النهاية على الويب لتكوين جهاز الشبكة. توفر Microsoft إشعارا مسبقا قبل 30 يوما من نشر إضافات جديدة لتمنحك الوقت لتحديث قوائم التحكم بالوصول وقوائم تجاوز الخادم الوكيل. نوصيك باستدعاء أسلوب نقاط النهاية على الويب مرة أخرى فقط عندما يشير أسلوب الإصدار على الويب إلى توفر إصدار جديد من البيانات.

معلمات أسلوب نقاط النهاية على الويب هي:

- **ServiceAreas=\<Common \| Exchange \| SharePoint \| Skype\>** —قائمة مفصولة بفصول مناطق الخدمة. العناصر الصالحة هي _Common_ _Exchange_ _SharePoint_ _Skype._ بما _أن عناصر_ منطقة الخدمة الشائعة هي أحد المتطلبات الأساسية لكل مناطق الخدمات الأخرى، فإن خدمة الويب تتضمنها دائما. إذا لم تقوم بتضمين هذه المعلمة، يتم إرجاع كل مناطق الخدمة.
- **TenantName=\<tenant_name\>** —اسم Office 365 المستأجر الخاص بك. تأخذ خدمة الويب الاسم الذي تم توفيره و تدرجه في أجزاء من عناوين URL التي تتضمن اسم المستأجر. إذا لم توفر اسم مستأجر، فإن هذه الأجزاء من عناوين URL لها حرف البدل (\*).
- **NoIPv6=\<true \| false\>** —قم بتعيين القيمة إلى _true_ لاستبعاد عناوين IPv6 من الإخراج إذا لم تكن تستخدم IPv6 في شبكتك.
- **مثيل=\<Worldwide \| China \| USGovDoD \| USGovGCCHigh\>** —تحدد هذه المعلمة المطلوبة المثيل الذي يتم إرجاع نقاط النهاية منه. المثيلات الصحيحة هي: _على_ مستوى _العالم والصين_ _و USGovDoD_ و _USGovGCCHigh_.

إذا قمت باستدعاء أسلوب نقاط النهاية على الويب عدة مرات من عنوان IP للعميل نفسه، فقد تتلقى رمز استجابة HTTP _429 (عدد كبير جدا من الطلبات)_. إذا حصلت على رمز الاستجابة هذا، فانتظر ساعة واحدة قبل تكرار طلبك، أو يمكنك إنشاء GUID جديد للطلب. كأفضل ممارسة عامة، اتصل فقط بطريقة ويب نقاط النهاية عندما يشير أسلوب الإصدار على الويب إلى توفر إصدار جديد.

النتيجة من أسلوب نقاط النهاية على الويب هي صفيف من السجلات حيث يمثل كل سجل مجموعة نقاط نهاية معينة. العناصر الخاصة بكل سجل هي:

- الم id—رقم الم Immutable ID من مجموعة نقاط النهاية.
- serviceArea —منطقة الخدمة التي هي جزء من: _Common_ أو _Exchange_ أو _SharePoint_ أو _Skype_.
- عناوين url —عناوين URL الخاصة بنقطة النهاية. صفيف JSON لسجلات DNS. محذف إذا كان فارغا.
- tcpPorts—منافذ TCP الخاصة بتعيين نقطة النهاية. يتم تنسيق كل عناصر المنافذ كقائمة مفصولة بفصول فاصلة للمنافذ أو نطاقات المنافذ مفصولة ب حرف شرطة (-). تنطبق المنافذ على كل عناوين IP وجميع عناوين URL في مجموعة نقاط النهاية لفئة معينة. محذف إذا كان فارغا.
- udpPorts —منافذ UDP لنطاقات عناوين IP في مجموعة نقاط النهاية هذه. محذف إذا كان فارغا.
- عناوين ip — نطاقات عناوين IP المقترنة بمجموعة نقاط النهاية هذه المقترنة بمنافذ TCP أو UDP المدرجة. صفيف JSON لنطاقات عناوين IP. محذف إذا كان فارغا.
- الفئة —فئة الاتصال الخاصة بنقطة النهاية. القيم الصالحة هي _تحسين_ _والسماح_ _وافتراضي_. إذا قمت بالبحث في إخراج أسلوب نقاط النهاية على الويب لفئة عنوان IP أو URL معين، فمن المحتمل أن يرجع الاستعلام فئات متعددة. في مثل هذه الحالة، اتبع التوصية الخاصة بفئة الأولوية العليا. على سبيل المثال، إذا كانت نقطة النهاية تظهر في كل من _"_ تحسين" و"السماح"، يجب اتباع متطلبات _"تحسين_". مطلوب.
- expressRoute — _True_ إذا تم توجيه مجموعة نقاط النهاية هذه عبر ExpressRoute، _False_ إذا لم يتم توجيهها.
- مطلوب — _True_ إذا كانت مجموعة نقاط النهاية هذه مطلوبة للحصول على اتصال Office 365 تكون معتمدة. _خطأ_ إذا كانت مجموعة نقاط النهاية هذه اختيارية.
- ملاحظات—بالنسبة لنقاط النهاية الاختيارية، يصف هذا Office 365 الوظائف التي لن تكون متوفرة إذا لم يكن الوصول إلى عناوين IP أو عناوين URL في مجموعة نقاط النهاية هذه متوفرا في طبقة الشبكة. محذف إذا كان فارغا.

### <a name="endpoints-web-method-examples"></a>أمثلة على أسلوب نقاط النهاية على الويب

مثال 1 لطلب URI: <https://endpoints.office.com/endpoints/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7>

يحصل URI هذا على كل نقاط النهاية Office 365 على مستوى العالم لكل أحمال العمل. مثال على النتيجة التي تعرض مقتطفا من الإخراج:

```json
[
 {
  "id": 1,
  "serviceArea": "Exchange",
  "serviceAreaDisplayName": "Exchange Online",
  "urls":
   [
    "*.protection.outlook.com"
   ],
  "ips":
   [
    "2a01:111:f403::/48", "23.103.132.0/22", "23.103.136.0/21", "23.103.198.0/23", "23.103.212.0/22", "40.92.0.0/14", "40.107.0.0/17", "40.107.128.0/18", "52.100.0.0/14", "213.199.154.0/24", "213.199.180.128/26", "94.245.120.64/26", "207.46.163.0/24", "65.55.88.0/24", "216.32.180.0/23", "23.103.144.0/20", "65.55.169.0/24", "207.46.100.0/24", "2a01:111:f400:7c00::/54", "157.56.110.0/23", "23.103.200.0/22", "104.47.0.0/17", "2a01:111:f400:fc00::/54", "157.55.234.0/24", "157.56.112.0/24", "52.238.78.88/32"
   ],
  "tcpPorts": "443",
  "expressRoute": true,
  "category": "Allow"
 },
 {
  "id": 2,
  "serviceArea": "Exchange",
  "serviceAreaDisplayName": "Exchange Online",
  "urls":
   [
    "*.mail.protection.outlook.com"
   ],
```

سيحتوي الإخراج الكامل للطلب في هذا المثال على مجموعات نقاط نهاية أخرى.

مثال 2 لطلب URI: [https://endpoints.office.com/endpoints/Worldwide?ServiceAreas=Exchange&amp; ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/endpoints/Worldwide?ServiceAreas=Exchange&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)

يحصل هذا المثال على نقاط نهاية للمثيل Office 365 حول العالم Exchange Online والتبعيات فقط.

على سبيل المثال، يشبه الإخراج 2 المثال 1 باستثناء أن النتائج لن تتضمن نقاط نهاية SharePoint Online أو Skype for Business Online.

## <a name="changes-web-method"></a>تغيير أسلوب الويب

ترجع طريقة التغييرات على الويب آخر التحديثات التي تم نشرها، وهي عادة التغييرات التي تم إدخالها في الشهر السابق على نطاقات عناوين IP ومواعيد URL.

إن التغييرات الأكثر أهمية لبيانات نقاط النهاية هي عناوين IP وعناوين URL الجديدة. قد يؤدي عدم إضافة عنوان IP إلى قائمة التحكم بالوصول إلى جدار الحماية أو عنوان URL إلى قائمة تجاوز الخادم الوكيل إلى انقطاع Office 365 خلف جهاز الشبكة هذا. بغض النظر عن متطلبات التشغيل، يتم نشر نقاط النهاية الجديدة لخدمة الويب قبل 30 يوما من تاريخ توفير نقاط النهاية للاستخدام لتوفير الوقت لتحديث قوائم التحكم بالوصول وقوائم تجاوز الخادم الوكيل.

المعلمة المطلوبة لطريقة التغييرات على الويب هي:

- **Version=\<YYYYMMDDNN>** —معلمة مسار URL المطلوبة. هذه القيمة هي الإصدار الذي قمت بتنفيذه حاليا. ستعرض خدمة الويب التغييرات منذ ذلك الإصدار. التنسيق _هو YYYYMMDDNN_، حيث يتم زيادة _عدد NN_ بشكل طبيعي إذا كان هناك إصدارات متعددة مطلوبة للنشر في يوم واحد، مع _00_ تمثل التحديث الأول ليوم معين. تتطلب خدمة الويب أن _تحتوي معلمة_ الإصدار على 10 أرقام بالضبط.

يتم تحديد معدل أسلوب التغييرات على الويب بالطريقة نفسها التي يتم بها تحديد أسلوب نقاط النهاية على الويب. إذا تلقيت رمز استجابة 429 HTTP، فانتظر ساعة واحدة قبل تكرار طلبك أو إنشاء GUID جديد للطلب.

إن النتيجة من أسلوب التغييرات على الويب هي صفيف من السجلات حيث يمثل كل سجل تغييرا في إصدار معين من نقاط النهاية. العناصر الخاصة بكل سجل هي:

- الم id—الم Immutable ID لسجل التغيير.
- endpointSetId —الم ID لسجل مجموعة نقاط النهاية الذي تم تغييره.
- الترتيب — يصف التغيير الذي تم على سجل مجموعة نقاط النهاية. يتم تغيير _القيم أو_ _إضافتها_ أو _إزالتها_.
- التأثير—لن تكون كل التغييرات متساوية الأهمية لكل بيئة. يصف هذا العنصر التأثير المتوقع على البيئة المحيطة بشبكة المؤسسة نتيجة لهذا التغيير. يتم تضمين هذا العنصر فقط في سجلات تغيير **إصدارات 2018112800** والإصدارات الأحدث. خيارات التأثير هي: — إضافةIp – تم إضافة عنوان IP Office 365 وسيبقى على الخدمة قريبا. يمثل ذلك تغييرا تحتاج إلى القيام به على جدار حماية أو جهاز آخر محيط للشبكة من الطبقة 3. إذا لم تكن قد أضفت هذا قبل بدء استخدامه، فقد تواجه انقطاعا.
  — AddedUrl – تم إضافة عنوان URL Office 365 وسيبقى على الخدمة قريبا. يمثل ذلك تغييرا تحتاج إلى القيام به على خادم وكيل أو جهاز محيط ل تحليل عنوان URL للشبكة. إذا لم تكن قد أضفت عنوان URL هذا قبل بدء استخدامه، فقد تواجه انقطاعا.
  — AddedIpAndUrl—تم إضافة عنوان IP وعنوان URL. يمثل ذلك تغييرا تحتاج إلى القيام به إما على جهاز جدار حماية من الطبقة 3 أو خادم وكيل أو جهاز تحليل URL. إذا لم تكن قد أضفت زوج IP/URL هذا قبل بدء استخدامه، فقد تواجه انقطاعا.
  — تمت إزالةIpOrUrl – تمت إزالة عنوان IP أو URL واحد على الأقل من Office 365. قم بإزالة نقاط نهاية الشبكة من أجهزتك المحيطة، ولكن لا يوجد موعد نهائي للقيام بذلك.
  — ChangedIsExpressRoute – تم تغيير سمة دعم ExpressRoute. إذا كنت تستخدم ExpressRoute، فقد تحتاج إلى اتخاذ إجراء وفقا لتكوينك.
  — MovedIpOrUrl – نقلنا عنوان IP أو عنوان URL بين مجموعة نقاط النهاية هذه وآخر. بشكل عام، لا يلزم اتخاذ أي إجراء.
  — RemovedDuplicateIpOrUrl – قمنا بإزالة عنوان IP أو Url مكرر ولكن لا يزال منشورا Office 365. بشكل عام، لا يلزم اتخاذ أي إجراء.
  — OtherNonPriorityChanges – قمنا بتغيير شيء أقل أهمية من كل الخيارات الأخرى، مثل محتويات حقل ملاحظة.
- الإصدار— إصدار مجموعة نقاط النهاية المنشورة التي تم إدخال التغيير فيها. أرقام الإصدارات هي من التنسيق _YYYYMMDDNN_، حيث _يكون NN_ رقما طبيعيا متزايد إذا كانت هناك إصدارات متعددة مطلوبة للنشر في يوم واحد.
- السابق—البنية الفرعية التي تفصيل القيم السابقة للعناصر التي تم تغييرها في مجموعة نقاط النهاية. لن يتم تضمين ذلك  مجموعات نقاط النهاية المضافة حديثا. يتضمن _ExpressRoute_ _و serviceArea والفئة_ _والمطلوب_ _و tcpPorts_ _و udpPorts_ _والملاحظات_.
- الحالية—البنية الفرعية التي تفصيل القيم المحدثة لعناصر التغييرات في مجموعة نقاط النهاية. يتضمن _ExpressRoute_ _و serviceArea والفئة_ _والمطلوب_ _و tcpPorts_ _و udpPorts_ _والملاحظات_.
- إضافة —البنية الفرعية التي تفصيل العناصر التي يجب إضافتها إلى مجموعات مجموعات نقاط النهاية. يتم حذفه إذا لم تكن هناك إضافات.
  — effectiveDate—يعرف البيانات عندما تكون الإضافات مباشرة في الخدمة.
  — ips—العناصر التي يجب إضافتها إلى _صفيف ips_ .
  — عناوين url- العناصر التي يجب إضافتها إلى _صفيف عناوين_ url.
- إزالة—البنية الفرعية التي تفصيل العناصر التي تريد إزالتها من مجموعة نقاط النهاية. يتم حذفه إذا لم تكن هناك أي عمليات إزالة.
  — عناوين ip—العناصر التي يجب إزالتها من صفيف _ips_ .
  — عناوين url- العناصر التي يجب إزالتها من صفيف _عناوين_ url.

### <a name="changes-web-method-examples"></a>أمثلة على أسلوب التغييرات على الويب

مثال 1 لطلب URI: <https://endpoints.office.com/changes/worldwide/0000000000?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7>

يطلب هذا كل التغييرات السابقة على Office 365 الخدمة على مستوى العالم. مثال على النتيجة:

```json
[
 {
  "id": 424,
  "endpointSetId": 32,
  "disposition": "Change",
  "version": "2018062700",
  "remove":
   {
    "urls":
     [
      "*.api.skype.com", "skypegraph.skype.com"
     ]
   }
 },
 {
  "id": 426,
  "endpointSetId": 31,
  "disposition": "Change",
  "version": "2018062700",
  "add":
   {
    "effectiveDate": "20180609",
    "ips":
     [
      "51.140.203.190/32"
     ]
   },
  "remove":
   {
    "ips":
     [
```

مثال 2 لطلب URI: <https://endpoints.office.com/changes/worldwide/2018062700?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7>

يتم من خلال هذا الطلب إجراء تغييرات منذ الإصدار المحدد على Office 365 Worldwide. في هذه الحالة، الإصدار المحدد هو الأحدث. مثال على النتيجة:

```json
[
  {
    "id":3,
    "endpointSetId":33,
    "changeDescription":"Removing old IP prefixes",
    "disposition":"Change",
    "version":"2018031301",
    "remove":{
      "ips":["65.55.127.0/24","66.119.157.192/26","66.119.158.0/25",
      "111.221.76.128/25","111.221.77.0/26","207.46.5.0/24"]
    }
  },
  {
    "id":4,
    "endpointSetId":45,
    "changeDescription":"Removing old IP prefixes",
    "disposition":"Change",
    "version":"2018031301",
    "remove":{
      "ips":["13.78.93.8/32","40.113.87.220/32","40.114.149.220/32",
      "40.117.100.83/32","40.118.214.164/32","104.208.31.113/32"]
    }
  }
]
```

## <a name="example-powershell-script"></a>مثال على برنامج PowerShell النصي

يمكنك تشغيل برنامج PowerShell النصي هذا لمعرفة ما إذا كانت هناك إجراءات يجب اتخاذها للبيانات المحدثة. يمكنك تشغيل هذا البرنامج النصي كمهمة مجدولة للتحقق من وجود تحديث إصدار. لتجنب التحميل الزائد على خدمة الويب، حاول عدم تشغيل البرنامج النصي أكثر من مرة واحدة في الساعة.

يقوم البرنامج النصي ما يلي:

- يتحقق من رقم إصدار نقاط نهاية مثيلات Office 365 على مستوى العالم عن طريق استدعاء REST API لخدمة الويب.
- يتحقق من ملف الإصدار الحالي بسعر _$Env:TEMP\O365_endpoints_latestversion.txt_. عادة ما يكون مسار المتغير العمومي **$Env:TEMP** هو _C:\Users<\\ username\>\AppData\Local\Temp_.
- إذا كانت هذه هي المرة الأولى التي يتم فيها تشغيل البرنامج النصي، يرجع البرنامج النصي الإصدار الحالي وكل عناوين IP وعناوين URL الحالية، ويكتب إصدار نقاط النهاية إلى الملف _$Env:TEMP\O365_endpoints_latestversion.txt_ ويخرج بيانات نقاط النهاية إلى الملف _$Env:TEMP\O365_endpoints_data.txt_. يمكنك تعديل المسار و/أو اسم ملف الإخراج عن طريق تحرير هذه الأسطر:

    ``` powershell
    $versionpath = $Env:TEMP + "\O365_endpoints_latestversion.txt"
    $datapath = $Env:TEMP + "\O365_endpoints_data.txt"
    ```

- في كل تنفيذ لاحق من البرنامج النصي، إذا كان أحدث إصدار من خدمة ويب متطابقا مع الإصدار __ في ملفO365_endpoints_latestversion.txt، يتم إنهاء البرنامج النصي دون إجراء أي تغييرات.
- عندما يكون أحدث إصدار من خدمة ويب أحدث من الإصدار في ملف _O365_endpoints_latestversion.txt_، يرجع البرنامج النصي نقاط النهاية و عوامل التصفية لنقاط نهاية الفئة السماح وتحسين،  ويحدث  الإصدار في ملف _O365_endpoints_latestversion.txt_، ويكتب البيانات المحدثة _إلى ملفO365_endpoints_data.txt_.

ينشئ البرنامج النصي _ClientRequestId_ فريدا للكمبيوتر الذي يتم تنفيذه عليه، ويعيد استخدام هذا الم ID عبر مكالمات متعددة. يتم تخزين هذا الم ID في _O365_endpoints_latestversion.txt_ الملف.

### <a name="to-run-the-powershell-script"></a>لتشغيل البرنامج النصي PowerShell

1. انسخ البرنامج النصي واحفظه في محرك الأقراص الثابت المحلي أو موقع البرنامج النصي _Get-O365WebServiceUpdates.ps1._
1. نفذ البرنامج النصي في محرر البرنامج النصي المفضل لديك مثل PowerShell ISE أو التعليمات البرمجية VS، أو من وحدة تحكم PowerShell باستخدام الأمر التالي:

    ``` powershell
   powershell.exe -file <path>\Get-O365WebServiceUpdates.ps1
    ```

    لا توجد معلمات للتمرير إلى البرنامج النصي.

```powershell
<# Get-O365WebServiceUpdates.ps1
From https://aka.ms/ipurlws
v1.1 8/6/2019

DESCRIPTION
This script calls the REST API of the Office 365 IP and URL Web Service (Worldwide instance)
and checks to see if there has been a new update since the version stored in an existing
$Env:TEMP\O365_endpoints_latestversion.txt file in your user directory's temp folder
(usually C:\Users\<username>\AppData\Local\Temp).
If the file doesn't exist, or the latest version is newer than the current version in the
file, the script returns IPs and/or URLs that have been changed, added or removed in the latest
update and writes the new version and data to the output file $Env:TEMP\O365_endpoints_data.txt.

USAGE
Run as a scheduled task every 60 minutes.

PARAMETERS
n/a

PREREQUISITES
PS script execution policy: Bypass
PowerShell 3.0 or later
Does not require elevation
#>

#Requires -Version 3.0

# web service root URL
$ws = "https://endpoints.office.com"
# path where output files will be stored
$versionpath = $Env:TEMP + "\O365_endpoints_latestversion.txt"
$datapath = $Env:TEMP + "\O365_endpoints_data.txt"

# fetch client ID and version if version file exists; otherwise create new file and client ID
if (Test-Path $versionpath) {
    $content = Get-Content $versionpath
    $clientRequestId = $content[0]
    $lastVersion = $content[1]
    Write-Output ("Version file exists! Current version: " + $lastVersion)
}
else {
    Write-Output ("First run! Creating version file at " + $versionpath + ".")
    $clientRequestId = [GUID]::NewGuid().Guid
    $lastVersion = "0000000000"
    @($clientRequestId, $lastVersion) | Out-File $versionpath
}

# call version method to check the latest version, and pull new data if version number is different
$version = Invoke-RestMethod -Uri ($ws + "/version/Worldwide?clientRequestId=" + $clientRequestId)
if ($version.latest -gt $lastVersion) {
    Write-Host "New version of Office 365 worldwide commercial service instance endpoints detected"
    # write the new version number to the version file
    @($clientRequestId, $version.latest) | Out-File $versionpath
    # invoke endpoints method to get the new data
    $endpointSets = Invoke-RestMethod -Uri ($ws + "/endpoints/Worldwide?clientRequestId=" + $clientRequestId)
    # filter results for Allow and Optimize endpoints, and transform these into custom objects with port and category
    # URL results
    $flatUrls = $endpointSets | ForEach-Object {
        $endpointSet = $_
        $urls = $(if ($endpointSet.urls.Count -gt 0) { $endpointSet.urls } else { @() })
        $urlCustomObjects = @()
        if ($endpointSet.category -in ("Allow", "Optimize")) {
            $urlCustomObjects = $urls | ForEach-Object {
                [PSCustomObject]@{
                    category = $endpointSet.category;
                    url      = $_;
                    tcpPorts = $endpointSet.tcpPorts;
                    udpPorts = $endpointSet.udpPorts;
                }
            }
        }
        $urlCustomObjects
    }
    # IPv4 results
    $flatIp4s = $endpointSets | ForEach-Object {
        $endpointSet = $_
        $ips = $(if ($endpointSet.ips.Count -gt 0) { $endpointSet.ips } else { @() })
        # IPv4 strings contain dots
        $ip4s = $ips | Where-Object { $_ -like '*.*' }
        $ip4CustomObjects = @()
        if ($endpointSet.category -in ("Allow", "Optimize")) {
            $ip4CustomObjects = $ip4s | ForEach-Object {
                [PSCustomObject]@{
                    category = $endpointSet.category;
                    ip = $_;
                    tcpPorts = $endpointSet.tcpPorts;
                    udpPorts = $endpointSet.udpPorts;
                }
            }
        }
        $ip4CustomObjects
    }
    # IPv6 results
    $flatIp6s = $endpointSets | ForEach-Object {
        $endpointSet = $_
        $ips = $(if ($endpointSet.ips.Count -gt 0) { $endpointSet.ips } else { @() })
        # IPv6 strings contain colons
        $ip6s = $ips | Where-Object { $_ -like '*:*' }
        $ip6CustomObjects = @()
        if ($endpointSet.category -in ("Optimize")) {
            $ip6CustomObjects = $ip6s | ForEach-Object {
                [PSCustomObject]@{
                    category = $endpointSet.category;
                    ip = $_;
                    tcpPorts = $endpointSet.tcpPorts;
                    udpPorts = $endpointSet.udpPorts;
                }
            }
        }
        $ip6CustomObjects
    }

    # write output to screen
    Write-Output ("Client Request ID: " + $clientRequestId)
    Write-Output ("Last Version: " + $lastVersion)
    Write-Output ("New Version: " + $version.latest)
    Write-Output ""
    Write-Output "IPv4 Firewall IP Address Ranges"
    ($flatIp4s.ip | Sort-Object -Unique) -join "," | Out-String
    Write-Output "IPv6 Firewall IP Address Ranges"
    ($flatIp6s.ip | Sort-Object -Unique) -join "," | Out-String
    Write-Output "URLs for Proxy Server"
    ($flatUrls.url | Sort-Object -Unique) -join "," | Out-String
    Write-Output ("IP and URL data written to " + $datapath)

    # write output to data file
    Write-Output "Office 365 IP and UL Web Service data" | Out-File $datapath
    Write-Output "Worldwide instance" | Out-File $datapath -Append
    Write-Output "" | Out-File $datapath -Append
    Write-Output ("Version: " + $version.latest) | Out-File $datapath -Append
    Write-Output "" | Out-File $datapath -Append
    Write-Output "IPv4 Firewall IP Address Ranges" | Out-File $datapath -Append
    ($flatIp4s.ip | Sort-Object -Unique) -join "," | Out-File $datapath -Append
    Write-Output "" | Out-File $datapath -Append
    Write-Output "IPv6 Firewall IP Address Ranges" | Out-File $datapath -Append
    ($flatIp6s.ip | Sort-Object -Unique) -join "," | Out-File $datapath -Append
    Write-Output "" | Out-File $datapath -Append
    Write-Output "URLs for Proxy Server" | Out-File $datapath -Append
    ($flatUrls.url | Sort-Object -Unique) -join "," | Out-File $datapath -Append
}
else {
    Write-Host "Office 365 worldwide commercial service instance endpoints are up-to-date."
}
```

## <a name="example-python-script"></a>مثال على برنامج Python النصي

فيما يلي برنامج نصي من Python، تم اختباره باستخدام Python 3.6.3 على Windows 10، يمكنك تشغيله لمعرفة ما إذا كانت هناك إجراءات يجب اتخاذها للبيانات المحدثة. يتحقق هذا البرنامج النصي من رقم الإصدار Office 365 نقاط نهاية مثيلات العالم. عند وجود تغيير، يتم تنزيل نقاط النهاية و عوامل التصفية _لنقاط_ نهاية الفئة السماح وتحسين. كما يستخدم أيضا ClientRequestId فريدا عبر مكالمات متعددة ويحفظ الإصدار الأخير الذي تم العثور عليه في ملف مؤقت. اتصل بهذا البرنامج النصي مرة واحدة كل ساعة للتحقق من تحديث الإصدار.

```python
import json
import tempfile
from pathlib import Path
import urllib.request
import uuid
# helper to call the webservice and parse the response
def webApiGet(methodName, instanceName, clientRequestId):
    ws = "https://endpoints.office.com"
    requestPath = ws + '/' + methodName + '/' + instanceName + '?clientRequestId=' + clientRequestId
    request = urllib.request.Request(requestPath)
    with urllib.request.urlopen(request) as response:
        return json.loads(response.read().decode())
# path where client ID and latest version number will be stored
datapath = Path(tempfile.gettempdir() + '/endpoints_clientid_latestversion.txt')
# fetch client ID and version if data exists; otherwise create new file
if datapath.exists():
    with open(datapath, 'r') as fin:
        clientRequestId = fin.readline().strip()
        latestVersion = fin.readline().strip()
else:
    clientRequestId = str(uuid.uuid4())
    latestVersion = '0000000000'
    with open(datapath, 'w') as fout:
        fout.write(clientRequestId + '\n' + latestVersion)
# call version method to check the latest version, and pull new data if version number is different
version = webApiGet('version', 'Worldwide', clientRequestId)
if version['latest'] > latestVersion:
    print('New version of Office 365 worldwide commercial service instance endpoints detected')
    # write the new version number to the data file
    with open(datapath, 'w') as fout:
        fout.write(clientRequestId + '\n' + version['latest'])
    # invoke endpoints method to get the new data
    endpointSets = webApiGet('endpoints', 'Worldwide', clientRequestId)
    # filter results for Allow and Optimize endpoints, and transform these into tuples with port and category
    flatUrls = []
    for endpointSet in endpointSets:
        if endpointSet['category'] in ('Optimize', 'Allow'):
            category = endpointSet['category']
            urls = endpointSet['urls'] if 'urls' in endpointSet else []
            tcpPorts = endpointSet['tcpPorts'] if 'tcpPorts' in endpointSet else ''
            udpPorts = endpointSet['udpPorts'] if 'udpPorts' in endpointSet else ''
            flatUrls.extend([(category, url, tcpPorts, udpPorts) for url in urls])
    flatIps = []
    for endpointSet in endpointSets:
        if endpointSet['category'] in ('Optimize', 'Allow'):
            ips = endpointSet['ips'] if 'ips' in endpointSet else []
            category = endpointSet['category']
            # IPv4 strings have dots while IPv6 strings have colons
            ip4s = [ip for ip in ips if '.' in ip]
            tcpPorts = endpointSet['tcpPorts'] if 'tcpPorts' in endpointSet else ''
            udpPorts = endpointSet['udpPorts'] if 'udpPorts' in endpointSet else ''
            flatIps.extend([(category, ip, tcpPorts, udpPorts) for ip in ip4s])
    print('IPv4 Firewall IP Address Ranges')
    print(','.join(sorted(set([ip for (category, ip, tcpPorts, udpPorts) in flatIps]))))
    print('URLs for Proxy Server')
    print(','.join(sorted(set([url for (category, url, tcpPorts, udpPorts) in flatUrls]))))

    # TODO send mail (e.g. with smtplib/email modules) with new endpoints data
else:
    print('Office 365 worldwide commercial service instance endpoints are up-to-date')
```

## <a name="web-service-interface-versioning"></a>إصدار واجهة خدمة ويب

قد تكون هناك حاجة إلى إجراء تحديثات للمعلمات أو النتائج لأساليب خدمة الويب هذه في المستقبل. بعد نشر إصدار التوفر العام لخدمات الويب هذه، ستبذل Microsoft جهودا معقولة لتوفير إشعار مسبق بتحديثات المواد لخدمة الويب. عندما تعتقد Microsoft أن التحديث سيتطلب إجراء تغييرات على العملاء الذين يستخدمون خدمة الويب، ستحتفظ Microsoft بالإصدار السابق (إصدار واحد مرة أخرى) من خدمة الويب متوفرا لمدة 12 شهرا على الأقل بعد إصدار الإصدار الجديد. قد يتعذر على العملاء الذين لم تتم الترقية خلال هذا الوقت الوصول إلى خدمة الويب وأساليبها. يجب على العملاء التأكد من استمرار عمل عملاء خدمة الويب بدون أخطاء إذا تم إجراء التغييرات التالية على توقيع واجهة خدمة ويب:

- إضافة معلمة اختيارية جديدة إلى أسلوب ويب موجود لا يحتاج إلى توفيره من قبل العملاء الأقدم ولا يؤثر على النتيجة التي يحصل عليها العميل الأقدم.
- إضافة سمة مسماة جديدة في أحد عناصر استجابة REST أو أعمدة أخرى إلى استجابة CSV.
- إضافة أسلوب ويب جديد باسم جديد لا يتم استدعائه من قبل العملاء الأقدم.

## <a name="update-notifications"></a>تحديث الإعلامات

يمكنك استخدام بعض الطرق المختلفة للحصول على إعلامات البريد الإلكتروني عند نشر التغييرات على عناوين IP وعناوين URL إلى خدمة الويب.

- لاستخدام حل Power Automate، راجع استخدام Power Automate لتلقي رسالة بريد إلكتروني للحصول على تغييرات على Office 365 IP وعناوين [URL](https://techcommunity.microsoft.com/t5/Office-365-Networking/Use-Microsoft-Flow-to-receive-an-email-for-changes-to-Office-365/m-p/240651).
- لنشر تطبيق Azure Logic باستخدام قالب ARM، راجع Office 365 [التحديث (v1.1)](https://aka.ms/ipurlws-updates-template).
- لكتابة برنامج إعلام نصي خاص بك باستخدام PowerShell، راجع [إرسال MailMessage](/powershell/module/microsoft.powershell.utility/send-mailmessage).

## <a name="exporting-a-proxy-pac-file"></a>تصدير ملف PAC وكيل

[Get-PacFile](https://www.powershellgallery.com/packages/Get-PacFile) هو برنامج نصي من PowerShell يقرأ أحدث نقاط نهاية الشبكة من عنوان IP ل Office 365 وخدمة URL على الويب وينشئ ملف PAC عينة. للحصول على معلومات حول استخدام Get-PacFile، راجع استخدام ملف [PAC](managing-office-365-endpoints.md#use-a-pac-file-for-direct-routing-of-vital-office-365-traffic) لتوجيه البيانات Office 365 البيانات بشكل مباشر.

## <a name="related-topics"></a>مواضيع ذات صلة
  
[نطاقات عناوين IP وعناوين URL في Office 365](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2)

[إدارة Office 365 نقاط النهاية](managing-office-365-endpoints.md)
  
[Office 365 الأسئلة الشائعة حول نقاط النهاية](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d)

[Office 365 الاتصال بالشبكة](microsoft-365-network-connectivity-principles.md)

[Office 365 الشبكة وضبط الأداء](network-planning-and-performance.md)

[تقييم Office 365 الشبكة](assessing-network-connectivity.md)
  
[جودة الوسائط وأداء اتصال الشبكة في Skype for Business Online](https://support.office.com/article/5fe3e01b-34cf-44e0-b897-b0b2a83f0917)
  
[تحسين الشبكة ل Skype for Business Online](https://support.office.com/article/b363bdca-b00d-4150-96c3-ec7eab5a8a43)

[Office 365 الأداء باستخدام الأساسات ومحفوظات الأداء](performance-tuning-using-baselines-and-history.md)
  
[خطة استكشاف الأخطاء وإصلاحها Office 365](performance-troubleshooting-plan.md)
