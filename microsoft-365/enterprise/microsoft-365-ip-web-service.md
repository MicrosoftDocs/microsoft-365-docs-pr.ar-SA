---
title: عنوان IP Office 365 وخدمة ويب URL
ms.author: kvice
author: kelleyvice-msft
manager: scotv
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
description: تعرف على كيفية استخدام عنوان IP Office 365 وخدمة ويب URL لمساعدتك على تحديد نسبة استخدام الشبكة Office 365 وتمييزها بشكل أفضل.
ms.openlocfilehash: b13377c6230c869231b7cecda8375f663cbcd33b
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/27/2022
ms.locfileid: "65100622"
---
# <a name="office-365-ip-address-and-url-web-service"></a>عنوان IP Office 365 وخدمة ويب URL

يساعدك عنوان IP Office 365 وخدمة ويب URL على تحديد نسبة استخدام الشبكة Office 365 وتمييزها بشكل أفضل، مما يسهل عليك تقييم التغييرات وتكوينها والبقاء على اطلاع بها. تحل خدمة الويب المستندة إلى REST هذه محل ملفات XML السابقة القابلة للتنزيل، والتي تم التخلص منها في 2 أكتوبر 2018.

بصفتك عميلا أو مورد جهاز محيط للشبكة، يمكنك البناء مقابل خدمة الويب لعنوان IP Office 365 وإدخالات FQDN. يمكنك الوصول إلى البيانات مباشرة في مستعرض ويب باستخدام عناوين URL هذه:

- للحصول على أحدث إصدار من عناوين URL Office 365 ونطاقات عناوين IP، استخدم [https://endpoints.office.com/version](https://endpoints.office.com/version?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7).
- بالنسبة للبيانات الموجودة في صفحة نطاقات عناوين URL وعناوين IP Office 365 لجدار الحماية والخوادم الوكيلة، استخدم [https://endpoints.office.com/endpoints/worldwide](https://endpoints.office.com/endpoints/worldwide?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7).
- للحصول على جميع التغييرات الأخيرة منذ يوليو 2018 عندما كانت خدمة الويب متوفرة لأول مرة، استخدم [https://endpoints.office.com/changes/worldwide/0000000000](https://endpoints.office.com/changes/worldwide/0000000000?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7).

بصفتك عميلا، يمكنك استخدام خدمة الويب هذه من أجل:

- قم بتحديث برامج PowerShell النصية للحصول على بيانات نقطة النهاية Office 365 وتعديل أي تنسيق لأجهزة الشبكات الخاصة بك.
- استخدم هذه المعلومات لتحديث ملفات PAC المنشورة على أجهزة الكمبيوتر العميلة.

بصفتك مورد جهاز محيط الشبكة، يمكنك استخدام خدمة الويب هذه من أجل:

- إنشاء برامج الأجهزة واختبارها لتنزيل القائمة للتكوين التلقائي.
- تحقق من الإصدار الحالي.
- الحصول على التغييرات الحالية.

> [!NOTE]
> إذا كنت تستخدم Azure ExpressRoute للاتصال Office 365، فالرجاء مراجعة [Azure ExpressRoute Office 365](azure-expressroute.md) للتعرف على خدمات Office 365 المدعومة عبر Azure ExpressRoute. راجع أيضا [المقالة Office 365 عناوين URL ونطاقات عناوين IP](urls-and-ip-address-ranges.md) لفهم طلبات الشبكة لتطبيقات Office 365 التي تتطلب الاتصال بالإنترنت. سيساعد هذا على تكوين أجهزة الأمان المحيطة بشكل أفضل.

لمزيد من المعلومات، اطلع على:

- [منشور مدونة الإعلان في منتدى المجتمع التقني Office 365](https://techcommunity.microsoft.com/t5/Office-365-Blog/Announcing-Office-365-endpoint-categories-and-Office-365-IP/ba-p/177638)
- [Office 365 منتدى المجتمع التقني للأسئلة حول استخدام خدمات الويب](https://techcommunity.microsoft.com/t5/Office-365-Networking/bd-p/Office365Networking)

## <a name="common-parameters"></a>المعلمات الشائعة

هذه المعلمات شائعة عبر جميع أساليب خدمة الويب:

- **format=\<JSON \| CSV\>** —بشكل افتراضي، تنسيق البيانات التي تم إرجاعها هو JSON. استخدم هذه المعلمة الاختيارية لإرجاع البيانات بتنسيق قيم مفصولة بفواصل (CSV).
- **ClientRequestId=\<guid\>** —معرف فريد عمومي (GUID) مطلوب تقوم بإنشاءه لارتباط العميل. إنشاء GUID فريد لكل جهاز يستدعي خدمة الويب (تقوم البرامج النصية المضمنة في هذه الصفحة بإنشاء GUID لك). لا تستخدم معرفات المستخدم الرسومية (GUID) الموضحة في الأمثلة التالية لأنه قد يتم حظرها بواسطة خدمة الويب في المستقبل. تنسيق GUID هو _xxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx_، حيث تمثل x رقم سداسي عشري.

  لإنشاء GUID، يمكنك استخدام الأمر [New-Guid](/powershell/module/microsoft.powershell.utility/new-guid) PowerShell، أو استخدام خدمة عبر الإنترنت مثل [منشئ GUID عبر الإنترنت](https://www.guidgenerator.com/).

## <a name="version-web-method"></a>أسلوب ويب للإصدار

تقوم Microsoft بتحديث عنوان IP Office 365 وإدخالات FQDN في بداية كل شهر. يتم نشر التحديثات خارج النطاق أحيانا بسبب حوادث الدعم أو تحديثات الأمان أو متطلبات التشغيل الأخرى.

يتم تعيين رقم إصدار للبيانات لكل مثيل منشور، ويمكنك أسلوب ويب الإصدار من التحقق من أحدث إصدار من كل مثيل خدمة Office 365. نوصي بالتحقق من الإصدار ليس أكثر من مرة واحدة في الساعة.

معلمات أسلوب ويب للإصدار هي:

- **AllVersions=\<true \| false\>** —بشكل افتراضي، الإصدار الذي تم إرجاعه هو الأحدث. قم بتضمين هذه المعلمة الاختيارية لطلب كافة الإصدارات المنشورة منذ إصدار خدمة الويب لأول مرة.
- **تنسيق=\<JSON \| CSV \| RSS\>** —بالإضافة إلى تنسيقات JSON و CSV، يدعم أسلوب ويب الإصدار أيضا RSS. يمكنك استخدام هذه المعلمة الاختيارية مع _المعلمة AllVersions=true_ لطلب موجز RSS الذي يمكن استخدامه مع Outlook أو برامج قراءة RSS الأخرى.
- **مثيل=\<Worldwide \| China \| USGovDoD \| USGovGCCHigh\>** —تحدد هذه المعلمة الاختيارية المثيل الذي يجب إرجاع الإصدار له. إذا تم حذفها، يتم إرجاع كافة المثيلات. المثيلات الصالحة هي: في جميع أنحاء العالم، الصين، USGovDoD، USGovGCCHigh.

أسلوب ويب الإصدار غير محدود ولا يرجع أي وقت مضى 429 رمز استجابة HTTP. تتضمن الاستجابة لأسلوب ويب الإصدار رأس عنصر تحكم ذاكرة التخزين المؤقت يوصي بالتخزين المؤقت للبيانات لمدة ساعة واحدة. يمكن أن تكون النتيجة من أسلوب ويب الإصدار سجلا واحدا أو صفيفا من السجلات. عناصر كل سجل هي:

- المثيل — الاسم المختصر لمثيل خدمة Office 365.
- أحدث إصدار لنقاط النهاية للمثيل المحدد.
- الإصدارات — قائمة بكافة الإصدارات السابقة للمثيل المحدد. يتم تضمين هذا العنصر فقط إذا كانت معلمة _AllVersions_ صحيحة.

### <a name="version-web-method-examples"></a>أمثلة على أسلوب ويب للإصدار

مثال 1 لطلب URI: <https://endpoints.office.com/version?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7>

يقوم URI هذا بإرجاع أحدث إصدار من كل مثيل خدمة Office 365. مثال على النتيجة:

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
> المعرف الفريد العمومي للمعلمة ClientRequestID في عناوين URL هذه هي مثال فقط. لتجربة معرفات الموارد المنتظمة لخدمة الويب، قم بإنشاء GUID الخاص بك. قد يتم حظر GUIDs الموضحة في هذه الأمثلة بواسطة خدمة الويب في المستقبل.

مثال 2 لطلب URI: <https://endpoints.office.com/version/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7>

يقوم URI هذا بإرجاع أحدث إصدار من مثيل خدمة Office 365 المحدد. مثال على النتيجة:

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

يعرض URI هذا كافة الإصدارات السابقة التي تم نشرها لمثيل خدمة Office 365 في جميع أنحاء العالم. مثال على النتيجة:

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

يعرض URI موجز RSS للإصدارات المنشورة التي تتضمن ارتباطات لقائمة التغييرات لكل إصدار. مثال على النتيجة:

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

## <a name="endpoints-web-method"></a>أسلوب ويب نقاط النهاية

يقوم أسلوب نقاط النهاية على الويب بإرجاع كافة سجلات نطاقات عناوين IP وعناوين URL التي تشكل خدمة Office 365. يجب دائما استخدام أحدث البيانات من طريقة ويب نقاط النهاية لتكوين جهاز الشبكة. توفر Microsoft إشعارا مسبقا قبل 30 يوما من نشر الإضافات الجديدة لمنحك الوقت لتحديث قوائم التحكم بالوصول وقوائم تجاوز الخادم الوكيل. نوصي فقط باستدعاء أسلوب نقاط النهاية على الويب مرة أخرى عندما يشير أسلوب ويب للإصدار إلى توفر إصدار جديد من البيانات.

معلمات أسلوب نقاط النهاية على الويب هي:

- **ServiceAreas=\<Common \| Exchange \| SharePoint \| Skype\>** —قائمة مفصولة بفواصل لمناطق الخدمة. العناصر الصالحة هي _"شائع_" _و"Exchange__" و"SharePoint_" و"_Skype_". نظرا لأن عناصر منطقة الخدمة _الشائعة_ هي شرط أساسي لكافة مناطق الخدمة الأخرى، فإن خدمة الويب تتضمنها دائما. إذا لم تقم بتضمين هذه المعلمة، يتم إرجاع كافة مناطق الخدمة.
- **TenantName=\<tenant_name\>** —اسم مستأجر Office 365 الخاص بك. تأخذ خدمة الويب اسمك المتوفر وتدرجه في أجزاء من عناوين URL التي تتضمن اسم المستأجر. إذا لم تقم بتوفير اسم مستأجر، فإن هذه الأجزاء من عناوين URL تحتوي على حرف البدل (\*).
- **NoIPv6=\<true \| false\>** —قم بتعيين القيمة إلى _true_ لاستبعاد عناوين IPv6 من الإخراج إذا لم تكن تستخدم IPv6 في شبكتك.
- **مثيل=\<Worldwide \| China \| USGovDoD \| USGovGCCHigh\>** —تحدد هذه المعلمة المطلوبة المثيل الذي يجب إرجاع نقاط النهاية منه. المثيلات الصالحة هي: _في جميع أنحاء العالم__، والصين_، _وSSGovDoD_، _وSSGovGCCHigh_.

إذا قمت باستدعاء أسلوب ويب نقاط النهاية عدة مرات من عنوان IP العميل نفسه، فقد تتلقى رمز استجابة HTTP _429 (عدد كبير جدا من الطلبات)._ إذا تلقيت رمز الاستجابة هذا، فانتظر لمدة ساعة واحدة قبل تكرار طلبك، أو قم بإنشاء GUID جديد للطلب. كأفضل ممارسة عامة، قم باستدعاء أسلوب ويب نقاط النهاية فقط عندما يشير أسلوب ويب للإصدار إلى توفر إصدار جديد.

النتيجة من أسلوب نقاط النهاية على الويب هي صفيف من السجلات حيث يمثل كل سجل مجموعة نقاط نهاية معينة. العناصر الخاصة بكل سجل هي:

- المعرف - رقم المعرف غير القابل للتغيير لمجموعة نقاط النهاية.
- serviceArea — منطقة الخدمة التي يشكل هذا جزءا منها: _Common_ أو _Exchange_ _أو SharePoint_ أو _Skype_.
- urls— عناوين URL لمجموعة نقاط النهاية. صفيف JSON لسجلات DNS. يتم حذفه إذا كان فارغا.
- tcpPorts— منافذ TCP لمجموعة نقاط النهاية. يتم تنسيق كافة عناصر المنافذ كقوائم مفصولة بفواصل من المنافذ أو نطاقات المنافذ مفصولة بحرف شرطة (-). تنطبق المنافذ على كافة عناوين IP وكافة عناوين URL في مجموعة نقاط النهاية لفئة معينة. يتم حذفه إذا كان فارغا.
- udpPorts— منافذ UDP لنطاقات عناوين IP في مجموعة نقاط النهاية هذه. يتم حذفه إذا كان فارغا.
- ips — نطاقات عناوين IP المقترنة بمجموعة نقاط النهاية هذه كما هي مقترنة بمنافذ TCP أو UDP المدرجة. صفيف JSON لنطاقات عناوين IP. يتم حذفه إذا كان فارغا.
- الفئة — فئة الاتصال لمجموعة نقاط النهاية. القيم الصالحة هي _"تحسين_" و" _السماح_" و" _افتراضي_". إذا قمت بالبحث في إخراج أسلوب ويب لنقاط النهاية لفئة عنوان IP أو URL معين، فمن الممكن أن يرجع الاستعلام فئات متعددة. في مثل هذه الحالة، اتبع التوصية بفئة الأولوية العليا. على سبيل المثال، إذا ظهرت نقطة النهاية في كل من _"التحسين_ " و" _السماح_"، فيجب عليك اتباع متطلبات _"التحسين_". مطلوب.
- expressRoute — _True_ إذا تم توجيه مجموعة نقاط النهاية هذه عبر ExpressRoute، _False_ إذا لم يكن الأمر.
- مطلوب — _True_ إذا كانت مجموعة نقاط النهاية هذه مطلوبة للحصول على اتصال Office 365 ليتم دعمها. _خطأ_ إذا كانت مجموعة نقاط النهاية هذه اختيارية.
- ملاحظات — بالنسبة لنقاط النهاية الاختيارية، يصف هذا النص Office 365 الوظائف التي قد تكون غير متوفرة إذا تعذر الوصول إلى عناوين IP أو عناوين URL في مجموعة نقاط النهاية هذه في طبقة الشبكة. يتم حذفه إذا كان فارغا.

### <a name="endpoints-web-method-examples"></a>أمثلة على أسلوب نقاط النهاية على الويب

مثال 1 لطلب URI: <https://endpoints.office.com/endpoints/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7>

يحصل URI هذا على كافة نقاط النهاية لمثيل Office 365 في جميع أنحاء العالم لجميع أحمال العمل. مثال على النتيجة التي تعرض مقتطفا من الإخراج:

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

قد يحتوي الإخراج الكامل للطلب في هذا المثال على مجموعات نقاط نهاية أخرى.

مثال 2 لطلب URI: [https://endpoints.office.com/endpoints/Worldwide?ServiceAreas=Exchange&amp; ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/endpoints/Worldwide?ServiceAreas=Exchange&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)

يحصل هذا المثال على نقاط نهاية لمثيل Office 365 Worldwide Exchange Online والتبعيات فقط.

الإخراج، على سبيل المثال، 2 مشابه للمثال 1 باستثناء أن النتائج لن تتضمن نقاط نهاية SharePoint Online أو Skype for Business Online.

## <a name="changes-web-method"></a>تغيير أسلوب ويب

يرجع أسلوب التغييرات على ويب آخر التحديثات التي تم نشرها، عادة ما تكون تغييرات الشهر السابق على نطاقات عناوين IP وعناوين URL.

التغييرات الأكثر أهمية لبيانات نقاط النهاية هي عناوين URL وعناوين IP الجديدة. قد يؤدي الفشل في إضافة عنوان IP إلى قائمة التحكم في الوصول إلى جدار الحماية أو عنوان URL إلى قائمة تجاوز الخادم الوكيل إلى انقطاع Office 365 المستخدمين خلف جهاز الشبكة هذا. على الرغم من المتطلبات التشغيلية، يتم نشر نقاط النهاية الجديدة إلى خدمة الويب قبل 30 يوما من تاريخ توفير نقاط النهاية للاستخدام لمنحك الوقت لتحديث قوائم التحكم في الوصول وقوائم تجاوز الخادم الوكيل.

المعلمة المطلوبة لأسلوب ويب للتغييرات هي:

- **الإصدار=\<YYYYMMDDNN>** —معلمة مسار URL المطلوبة. هذه القيمة هي الإصدار الذي قمت بتطبيقه حاليا. ستقوم خدمة الويب بإرجاع التغييرات منذ ذلك الإصدار. التنسيق هو _YYYYMMDDNN_، حيث _NN_ هو عدد طبيعي يتزايد إذا كان هناك إصدارات متعددة مطلوب نشرها في يوم واحد، مع _00_ يمثل التحديث الأول ليوم معين. تتطلب خدمة الويب أن تحتوي معلمة _الإصدار_ على 10 أرقام بالضبط.

معدل أسلوب التغييرات على الويب محدود بنفس طريقة نقاط النهاية على الويب. إذا تلقيت رمز استجابة 429 HTTP، فانتظر ساعة واحدة قبل تكرار طلبك أو قم بإنشاء GUID جديد للطلب.

النتيجة من أسلوب ويب للتغييرات هي صفيف من السجلات حيث يمثل كل سجل تغييرا في إصدار معين من نقاط النهاية. العناصر الخاصة بكل سجل هي:

- المعرف — المعرف غير القابل للتغيير لسجل التغيير.
- endpointSetId — معرف سجل مجموعة نقاط النهاية الذي تم تغييره.
- disposition—Describes what the change did to the endpoint set record. القيم هي _تغيير_ أو _إضافة_ أو _إزالة_.
- التأثير - لن تكون جميع التغييرات بنفس القدر من الأهمية لكل بيئة. يصف هذا العنصر التأثير المتوقع على بيئة محيط شبكة المؤسسة نتيجة لهذا التغيير. يتم تضمين هذا العنصر فقط في سجلات التغيير **للإصدار 2018112800** والإصدارات الأحدث. خيارات التأثير هي: — AddedIp – تمت إضافة عنوان IP إلى Office 365 وسيكون مباشرا على الخدمة قريبا. يمثل هذا تغييرا تحتاج إلى اتخاذه على جدار حماية أو جهاز محيط شبكة الطبقة 3 الأخرى. إذا لم تقم بإضافة هذا قبل أن نبدأ في استخدامه، فقد تواجه انقطاعا.
  — AddedUrl – تمت إضافة عنوان URL إلى Office 365 وسيكون مباشرا على الخدمة قريبا. يمثل هذا تغييرا تحتاج إلى القيام به على خادم وكيل أو جهاز محيط شبكة تحليل عنوان URL. إذا لم تقم بإضافة عنوان URL هذا قبل أن نبدأ في استخدامه، فقد تواجه انقطاعا.
  — AddedIpAndUrl—تمت إضافة عنوان IP وعنوان URL. يمثل هذا تغييرا تحتاج إلى القيام به إما على جهاز طبقة جدار الحماية 3 أو خادم وكيل أو جهاز تحليل عنوان URL. إذا لم تقم بإضافة زوج IP/URL هذا قبل أن نبدأ في استخدامه، فقد تواجه انقطاعا.
  — RemovedIpOrUrl – تمت إزالة عنوان IP أو URL واحد على الأقل من Office 365. قم بإزالة نقاط نهاية الشبكة من الأجهزة المحيطة بك، ولكن لا يوجد موعد نهائي لك للقيام بذلك.
  — ChangedIsExpressRoute – تم تغيير سمة دعم ExpressRoute. إذا كنت تستخدم ExpressRoute، فقد تحتاج إلى اتخاذ إجراء استنادا إلى التكوين الخاص بك.
  — MovedIpOrUrl – نقلنا عنوان IP أو Url بين مجموعة نقاط النهاية هذه ومجموعة أخرى. بشكل عام، لا يلزم اتخاذ أي إجراء.
  — RemovedDuplicateIpOrUrl – قمنا بإزالة عنوان IP أو Url مكرر ولكن لا يزال منشورا Office 365. بشكل عام، لا يلزم اتخاذ أي إجراء.
  — OtherNonPriorityChanges – لقد قمنا بتغيير شيء أقل أهمية من جميع الخيارات الأخرى، مثل محتويات حقل ملاحظة.
- الإصدار-إصدار مجموعة نقاط النهاية المنشورة التي تم إدخال التغيير فيها. أرقام الإصدارات هي بتنسيق _YYYYMMDDDNN_، حيث _تكون NN_ عددا طبيعيا يتم زيادته إذا كانت هناك إصدارات متعددة مطلوب نشرها في يوم واحد.
- السابق — بنية فرعية تفصل القيم السابقة للعناصر التي تم تغييرها في مجموعة نقاط النهاية. لن يتم تضمين هذا لمجموعات نقاط النهاية المضافة حديثا. يتضمن  _ExpressRoute_ و _serviceArea_ _والفئة_ _والمطلوبة_ _وtcpPorts_ _وodpPorts_ _والملاحظات_.
- الحالي - بنية فرعية توضح بالتفصيل القيم المحدثة لعناصر التغييرات في مجموعة نقاط النهاية. يتضمن _ExpressRoute_ و _serviceArea_ _والفئة_ _والمطلوبة_ _وtcpPorts_ _وodpPorts_ _والملاحظات_.
- إضافة —بنية فرعية توضح بالتفصيل العناصر المراد إضافتها إلى مجموعات مجموعة نقاط النهاية. يتم حذفه إذا لم تكن هناك إضافات.
  — effectiveDate — يحدد البيانات عندما تكون الإضافات مباشرة في الخدمة.
  — ips— العناصر المراد إضافتها إلى صفيف _ips_ .
  — urls- العناصر المراد إضافتها إلى صفيف _urls_ .
- إزالة — بنية فرعية توضح بالتفصيل العناصر المراد إزالتها من مجموعة نقاط النهاية. يتم حذفه إذا لم تكن هناك عمليات إزالة.
  — ips—Items to be removed from the _ips_ array.
  — urls- العناصر المراد إزالتها من صفيف _urls_ .

### <a name="changes-web-method-examples"></a>تغيير أمثلة أسلوب ويب

مثال 1 لطلب URI: <https://endpoints.office.com/changes/worldwide/0000000000?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7>

يتطلب هذا كافة التغييرات السابقة على مثيل خدمة Office 365 في جميع أنحاء العالم. مثال على النتيجة:

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

يتطلب هذا تغييرات منذ الإصدار المحدد إلى مثيل Office 365 Worldwide. في هذه الحالة، يكون الإصدار المحدد هو الأحدث. مثال على النتيجة:

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

## <a name="example-powershell-script"></a>مثال على البرنامج النصي PowerShell

يمكنك تشغيل هذا البرنامج النصي PowerShell لمعرفة ما إذا كانت هناك إجراءات تحتاج إلى اتخاذها للبيانات المحدثة. يمكنك تشغيل هذا البرنامج النصي كمهمة مجدولة للتحقق من وجود تحديث للإصدار. لتجنب التحميل الزائد على خدمة الويب، حاول عدم تشغيل البرنامج النصي أكثر من مرة واحدة في الساعة.

يقوم البرنامج النصي بالآتي:

- التحقق من رقم إصدار نقاط نهاية مثيل Office 365 Worldwide الحالية عن طريق استدعاء واجهة برمجة تطبيقات REST لخدمة الويب.
- التحقق من وجود ملف إصدار حالي بقيمة _$Env:TEMP\O365_endpoints_latestversion.txt_. عادة ما يكون مسار المتغير العمومي **$Env:TEMP** هو _C:\Users\\<username\>\AppData\Local\Temp_.
- إذا كانت هذه هي المرة الأولى التي يتم فيها تشغيل البرنامج النصي، يقوم البرنامج النصي بإرجاع الإصدار الحالي وجميع عناوين IP الحالية وعناوين URL، ويكتب إصدار نقاط النهاية إلى الملف _$Env:TEMP\O365_endpoints_latestversion.txt_ ونقاط النهاية إخراج البيانات إلى الملف _$Env:TEMP\O365_endpoints_data.txt_. يمكنك تعديل مسار و/أو اسم ملف الإخراج عن طريق تحرير هذه الأسطر:

    ``` powershell
    $versionpath = $Env:TEMP + "\O365_endpoints_latestversion.txt"
    $datapath = $Env:TEMP + "\O365_endpoints_data.txt"
    ```

- في كل تنفيذ لاحق للبرنامج النصي، إذا كان أحدث إصدار من خدمة الويب مطابقا للإصدار في ملف _O365_endpoints_latestversion.txt_ ، يخرج البرنامج النصي دون إجراء أي تغييرات.
- عندما يكون أحدث إصدار لخدمة ويب أحدث من الإصدار في ملف _O365_endpoints_latestversion.txt_ ، يقوم البرنامج النصي بإرجاع نقاط النهاية وعوامل التصفية لنقاط نهاية الفئة **السماح** **والتحسين** ، وتحديث الإصدار في ملف _O365_endpoints_latestversion.txt_ ، وكتابة البيانات المحدثة إلى ملف _O365_endpoints_data.txt_ .

ينشئ البرنامج النصي _ClientRequestId_ فريدا للكمبيوتر الذي يتم تنفيذه عليه، ويعيد استخدام هذا المعرف عبر استدعاءات متعددة. يتم تخزين هذا المعرف في ملف _O365_endpoints_latestversion.txt_ .

### <a name="to-run-the-powershell-script"></a>لتشغيل البرنامج النصي PowerShell

1. انسخ البرنامج النصي واحفظه في محرك الأقراص الثابتة المحلي أو موقع البرنامج النصي _Get-O365WebServiceUpdates.ps1._
1. نفذ البرنامج النصي في محرر البرنامج النصي المفضل لديك مثل PowerShell ISE أو VS Code، أو من وحدة تحكم PowerShell باستخدام الأمر التالي:

    ``` powershell
   powershell.exe -file <path>\Get-O365WebServiceUpdates.ps1
    ```

    لا توجد معلمات لتمريرها إلى البرنامج النصي.

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

فيما يلي برنامج نصي Python، تم اختباره باستخدام Python 3.6.3 على Windows 10، يمكنك تشغيله لمعرفة ما إذا كانت هناك إجراءات تحتاج إلى اتخاذها للبيانات المحدثة. يتحقق هذا البرنامج النصي من رقم الإصدار لنقاط نهاية مثيل Office 365 Worldwide. عندما يكون هناك تغيير، فإنه يقوم بتنزيل نقاط النهاية وعوامل التصفية لنقاط نهاية الفئة _السماح_ _والتحسين_ . كما يستخدم ClientRequestId فريدا عبر مكالمات متعددة ويحفظ أحدث إصدار تم العثور عليه في ملف مؤقت. استدعاء هذا البرنامج النصي مرة واحدة في الساعة للتحقق من وجود تحديث للإصدار.

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

## <a name="web-service-interface-versioning"></a>تعيين إصدار واجهة خدمة ويب

قد تكون هناك حاجة إلى تحديثات للمعلمات أو النتائج لأساليب خدمة الويب هذه في المستقبل. بعد نشر إصدار التوفر العام لخدمات الويب هذه، ستبذل Microsoft جهود معقولة لتوفير إشعار مسبق بتحديثات المواد لخدمة الويب. عندما تعتقد Microsoft أن التحديث سيتطلب تغييرات على العملاء الذين يستخدمون خدمة الويب، ستحتفظ Microsoft بالإصدار السابق (إصدار واحد مرة أخرى) من خدمة الويب المتوفرة لمدة 12 شهرا على الأقل بعد إصدار الإصدار الجديد. قد يتعذر على العملاء الذين لا يقومون بالترقية خلال ذلك الوقت الوصول إلى خدمة الويب وأساليبها. يجب على العملاء التأكد من أن عملاء خدمة الويب يستمرون في العمل دون خطأ إذا تم إجراء التغييرات التالية على توقيع واجهة خدمة الويب:

- إضافة معلمة اختيارية جديدة إلى أسلوب ويب موجود لا يجب توفيره من قبل العملاء الأقدم ولا يؤثر على النتيجة التي يتلقاها عميل أقدم.
- إضافة سمة مسماة جديدة في أحد عناصر REST للاستجابة أو أعمدة أخرى إلى CSV للاستجابة.
- إضافة أسلوب ويب جديد باسم جديد لا يتم استدعاؤه من قبل العملاء الأقدم.

## <a name="update-notifications"></a>تحديث الإعلامات

يمكنك استخدام بعض الطرق المختلفة للحصول على إعلامات البريد الإلكتروني عند نشر التغييرات في عناوين IP وعناوين URL إلى خدمة الويب.

- لاستخدام حل Power Automate، راجع ["استخدام Power Automate" لتلقي رسالة بريد إلكتروني لإجراء تغييرات على عناوين IP وعناوين URL Office 365](https://techcommunity.microsoft.com/t5/Office-365-Networking/Use-Microsoft-Flow-to-receive-an-email-for-changes-to-Office-365/m-p/240651).
- لنشر Azure Logic App باستخدام قالب ARM، راجع [Office 365 Update Notification (v1.1).](https://aka.ms/ipurlws-updates-template)
- لكتابة البرنامج النصي للإعلام الخاص بك باستخدام PowerShell، راجع [Send-MailMessage](/powershell/module/microsoft.powershell.utility/send-mailmessage).

## <a name="exporting-a-proxy-pac-file"></a>تصدير ملف PAC الوكيل

[Get-PacFile](https://www.powershellgallery.com/packages/Get-PacFile) هو برنامج نصي PowerShell يقرأ أحدث نقاط نهاية الشبكة من عنوان IP Office 365 وخدمة ويب URL وينشئ نموذج ملف PAC. للحصول على معلومات حول استخدام Get-PacFile، راجع [استخدام ملف PAC للتوجيه المباشر لنسبة استخدام الشبكة Office 365 الحيوية](managing-office-365-endpoints.md#use-a-pac-file-for-direct-routing-of-vital-office-365-traffic).

## <a name="related-topics"></a>المواضيع ذات الصلة
  
[نطاقات عناوين IP وعناوين URL في Office 365](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2)

[إدارة نقاط نهاية Office 365](managing-office-365-endpoints.md)
  
[الأسئلة المتداولة حول نقاط النهاية Office 365](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d)

[مبادئ اتصال الشبكة Office 365](microsoft-365-network-connectivity-principles.md)

[Office 365 الشبكة وضبط الأداء](network-planning-and-performance.md)

[تقييم اتصال الشبكة Office 365](assessing-network-connectivity.md)
  
[جودة الوسائط وأداء اتصال الشبكة في Skype for Business Online](https://support.office.com/article/5fe3e01b-34cf-44e0-b897-b0b2a83f0917)
  
[تحسين شبكتك ل Skype for Business Online](https://support.office.com/article/b363bdca-b00d-4150-96c3-ec7eab5a8a43)

[ضبط الأداء Office 365 باستخدام الخطوط الأساسية ومحفوظات الأداء](performance-tuning-using-baselines-and-history.md)
  
[خطة استكشاف أخطاء الأداء وإصلاحها Office 365](performance-troubleshooting-plan.md)
