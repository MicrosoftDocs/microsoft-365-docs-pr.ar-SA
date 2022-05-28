---
title: إعداد SPF للمساعدة في منع الانتحال
f1.keywords:
- CSH
ms.author: tracyp
author: MSFTTracyP
manager: dansimp
ms.date: 11/21/2019
audience: ITPro
ms.topic: how-to
ms.localizationpriority: high
search.appverid:
- MET150
ms.assetid: 71373291-83d2-466f-86ea-fc61493743a6
ms.collection:
- M365-security-compliance
ms.custom:
- seo-marvel-apr2020
description: تعرف على كيفية تحديث سجل خدمة أسماء المجالات (DNS) لاستخدام إطار نهج المرسل (SPF) مع مجالك المخصص في Office 365.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 33e4a6d3644f7a3aab8992130b2b92e09dd665af
ms.sourcegitcommit: 38a18b0195d99222c2c6da0c80838d24b5f66b97
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 05/28/2022
ms.locfileid: "65772391"
---
# <a name="set-up-spf-to-help-prevent-spoofing"></a>إعداد SPF للمساعدة في منع الانتحال

- [المتطلبات الأساسية](#prerequisites)
- [إنشاء سجل SPF TXT أو تحديثه](#create-or-update-your-spf-txt-record)
- [كيفية التعامل مع المجالات الفرعية؟](#how-to-handle-subdomains)
- [استكشاف أخطاء SPF وإصلاحها](#troubleshooting-spf)

<!--
[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**Applies to**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender for Office 365 plan 1 and plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)
-->

تصف هذه المقالة كيفية تحديث سجل خدمة أسماء المجالات (DNS) بحيث يمكنك استخدام مصادقة البريد الإلكتروني لإطار نهج المرسل (SPF) مع مجالك المخصص في Office 365.

يساعد SPF على *التحقق من صحة* البريد الإلكتروني الصادر المرسل من مجالك المخصص (يأتي من هو الشخص الذي يشير إليه). إنها خطوة أولى في إعداد أساليب مصادقة البريد الإلكتروني الموصى بها بالكامل من SPF [وDKIM](use-dkim-to-validate-outbound-email.md) [وDMARC](use-dmarc-to-validate-email.md).

- [المتطلبات الأساسية](#prerequisites)
- [إنشاء سجل SPF TXT أو تحديثه](#create-or-update-your-spf-txt-record)
  - [كيفية التعامل مع المجالات الفرعية؟](#how-to-handle-subdomains)
- [ماذا تفعل مصادقة البريد الإلكتروني SPF فعليا؟](#what-does-spf-email-authentication-actually-do)
  - [استكشاف أخطاء SPF وإصلاحها](#troubleshooting-spf)
- [مزيد من المعلومات حول SPF](#more-information-about-spf)

## <a name="prerequisites"></a>المتطلبات الأساسية

> [!IMPORTANT]
> إذا كنت **شركة صغيرة**، أو لم تكن على دراية بعناوين IP أو تكوين DNS، فاتصل بسجل مجال الإنترنت (على سبيل المثال. & GoDaddy و Bluehost و web.com) طلب المساعدة في *تكوين DNS ل SPF* (وأي طريقة أخرى لمصادقة البريد الإلكتروني). <p> **إذا لم تستخدم عنوان URL مخصصا** (وعنوان URL المستخدم Office 365 ينتهي **في onmicrosoft.com**)، فقد تم إعداد SPF بالفعل لك في خدمة Office 365.

لنبدأ في العمل.

سيتم إنشاء سجل SPF TXT Office 365 في DNS خارجي لأي مجالات أو مجالات فرعية مخصصة. تحتاج إلى بعض المعلومات لإنشاء السجل. جمع هذه المعلومات:

- سجل SPF TXT لمجالك المخصص، إذا كان موجودا. للحصول على الإرشادات، راجع ["جمع المعلومات" التي تحتاجها لإنشاء سجلات DNS Office 365](../../admin/get-help-with-domains/information-for-dns-records.md).

- انتقل إلى خادم (خوادم) المراسلة وتعرف على عناوين IP الخارجية (المطلوبة من جميع خوادم المراسلة المحلية). على سبيل المثال، **131.107.2.200**.

- أسماء المجالات المطلوب استخدامها لكافة مجالات الجهات الخارجية التي تحتاج إلى تضمينها في سجل SPF TXT. لقد أعد بعض موفري البريد المجمع مجالات فرعية لاستخدامها لعملائهم. على سبيل المثال، قامت شركة MailChimp بإعداد **servers.mcsv.net**.

- تعرف على قاعدة الإنفاذ التي تريد استخدامها لسجل SPF TXT. يوصى بقاعدة **-all** . للحصول على معلومات مفصلة حول خيارات بناء الجملة الأخرى، راجع بناء [جملة سجل SPF TXT Office 365](how-office-365-uses-spf-to-prevent-spoofing.md#SPFSyntaxO365).

> [!IMPORTANT]
> لاستخدام مجال مخصص، يتطلب Office 365 إضافة سجل TXT لإطار نهج المرسل (SPF) إلى سجل DNS للمساعدة في منع تزييف هوية المرسلين.

## <a name="create-or-update-your-spf-txt-record"></a>إنشاء سجل SPF TXT أو تحديثه

1. تأكد من أنك على دراية بناء جملة SPF في الجدول التالي.

    |عنصر|إذا كنت تستخدم...|هل هو شائع للعملاء؟|أضف هذا...|
    |---|---|---|---|
    |1|أي نظام بريد إلكتروني (مطلوب)|المشتركه. تبدأ كافة سجلات SPF TXT بهذه القيمة|`v=spf1`|
    |2|Exchange Online|المشتركه|`include:spf.protection.outlook.com`|
    |3|Exchange Online مخصصة فقط|غير شائع|`ip4:23.103.224.0/19` <br> `ip4:206.191.224.0/19` <br> `ip4:40.103.0.0/16` <br> `include:spf.protection.outlook.com`|
    |4|Office 365 ألمانيا، Microsoft Cloud Germany فقط|غير شائع|`include:spf.protection.outlook.de`|
    |5|نظام البريد الإلكتروني لجهة خارجية|غير شائع|`include:<domain_name>` <p> \<domain_name\> هو مجال نظام البريد الإلكتروني التابع لجهة خارجية.|
    |6|نظام البريد الإلكتروني المحلي. على سبيل المثال، Exchange Online Protection بالإضافة إلى نظام بريد إلكتروني آخر|غير شائع|استخدم أحدها لكل نظام بريد إضافي: <p> `ip4:<IP_address>` <br> `ip6:<IP_address>` <br> `include:<domain_name>` <p> \<IP_address\> وهي \<domain_name\> عنوان IP ومجال نظام البريد الإلكتروني الآخر الذي يرسل البريد نيابة عن مجالك.|
    |7|أي نظام بريد إلكتروني (مطلوب)|المشتركه. تنتهي كافة سجلات SPF TXT بهذه القيمة|`<enforcement rule>` <p> يمكن أن تكون هذه إحدى القيم المتعددة. نوصي بالقيمة `-all`.|

2. إذا لم تكن قد فعلت ذلك بالفعل، فقم بتشكيل سجل SPF TXT باستخدام بناء الجملة من الجدول.

   على سبيل المثال، إذا تمت استضافتك بالكامل في Office 365، أي أنه ليس لديك خوادم بريد محلية، فسيتضمن سجل SPF TXT الصفوف 1 و2 و7 وسيبدو كما يلي:

   ```text
   v=spf1 include:spf.protection.outlook.com -all
   ```

   **المثال أعلاه هو سجل SPF TXT الأكثر شيوعا**. يعمل هذا السجل لكل شخص تقريبا، بغض النظر عما إذا كان مركز بيانات Microsoft موجودا في الولايات المتحدة أو في أوروبا (بما في ذلك ألمانيا) أو في موقع آخر.

   ومع ذلك، إذا اشتريت Office 365 ألمانيا، وهي جزء من Microsoft Cloud Germany، فيجب استخدام عبارة التضمين من السطر 4 بدلا من السطر 2. على سبيل المثال، إذا تمت استضافتك بالكامل في Office 365 ألمانيا، أي أنه ليس لديك خوادم بريد محلية، فسيتضمن سجل SPF TXT الصفوف 1 و4 و7 وسيبدو كما يلي:

   ```text
   v=spf1 include:spf.protection.outlook.de -all
   ```

   إذا تم نشرك بالفعل في Office 365 وقمت بإعداد سجلات SPF TXT لمجالك المخصص، وكنت تقوم بالترحيل إلى Office 365 ألمانيا، فستحتاج إلى تحديث سجل SPF TXT. للقيام بذلك، قم بالتغيير `include:spf.protection.outlook.com` إلى `include:spf.protection.outlook.de`.

3. بمجرد تشكيل سجل SPF TXT، تحتاج إلى تحديث السجل في DNS. **يمكنك الحصول على سجل SPF TXT واحد فقط لمجال.** إذا كان سجل SPF TXT موجودا، بدلا من إضافة سجل جديد، فستحتاج إلى تحديث السجل الموجود. انتقل إلى [إنشاء سجلات DNS Office 365](../../admin/get-help-with-domains/create-dns-records-at-any-dns-hosting-provider.md)، ثم حدد الارتباط لمضيف DNS.

4. اختبر سجل SPF TXT.

## <a name="how-to-handle-subdomains"></a>كيفية التعامل مع المجالات الفرعية؟

من المهم ملاحظة *أنك تحتاج إلى إنشاء سجل منفصل لكل مجال فرعي لأن المجالات الفرعية لا ترث سجل SPF لمجال المستوى الأعلى الخاص بها*.

مطلوب سجل SPF حرف بدل (`*.`) لكل مجال ومجال فرعي لمنع المهاجمين من إرسال البريد الإلكتروني الذي يدعي أنه من المجالات الفرعية غير الموجودة. على سبيل المثال:

```text
*.subdomain.contoso.com. IN TXT "v=spf1 -all"
```

## <a name="troubleshooting-spf"></a>استكشاف أخطاء SPF وإصلاحها

هل تواجه مشكلة في سجل SPF TXT؟ قراءة [استكشاف الأخطاء وإصلاحها: أفضل الممارسات ل SPF في Office 365](how-office-365-uses-spf-to-prevent-spoofing.md#SPFTroubleshoot).

## <a name="what-does-spf-email-authentication-actually-do"></a>ماذا تفعل مصادقة البريد الإلكتروني SPF فعليا؟

يحدد SPF خوادم البريد المسموح لها بإرسال البريد نيابة عنك. بشكل أساسي، تساعد SPF، جنبا إلى جنب مع DKIM وDMARC والتقنيات الأخرى التي تدعمها Office 365، على منع الانتحال والتصيد الاحتيالي. تتم إضافة SPF كسجل TXT يستخدمه DNS لتحديد خوادم البريد التي يمكنها إرسال البريد نيابة عن مجالك المخصص. تشير أنظمة بريد المستلم إلى سجل SPF TXT لتحديد ما إذا كانت رسالة من مجالك المخصص تأتي من خادم مراسلة معتمد.

على سبيل المثال، لنفترض أن مجالك المخصص contoso.com يستخدم Office 365. يمكنك إضافة سجل SPF TXT الذي يسرد خوادم المراسلة Office 365 كخوادم بريد شرعية لمجالك. عندما يتلقى خادم المراسلة رسالة من joe@contoso.com، يبحث الخادم عن سجل SPF TXT contoso.com ويكتشف ما إذا كانت الرسالة صالحة. إذا اكتشف الخادم المتلقي أن الرسالة واردة من خادم آخر غير خوادم المراسلة Office 365 المدرجة في سجل SPF، يمكن لخادم البريد المتلقي اختيار رفض الرسالة باعتبارها بريدا عشوائيا.

أيضا، إذا لم يكن مجالك المخصص يحتوي على سجل SPF TXT، فقد ترفض بعض الخوادم المتلقية الرسالة بشكل صريح. وذلك لأن الخادم المتلقي لا يمكنه التحقق من صحة أن الرسالة تأتي من خادم مراسلة معتمد.

إذا كنت قد قمت بالفعل بإعداد البريد Office 365، فقد قمت بالفعل بتضمين خوادم المراسلة الخاصة ب Microsoft في DNS كسجل SPF TXT. ومع ذلك، هناك بعض الحالات التي قد تحتاج فيها إلى تحديث سجل SPF TXT في DNS. على سبيل المثال:

- في السابق، كان عليك إضافة سجل SPF TXT مختلف إلى مجالك المخصص إذا كنت تستخدم SharePoint Online. لم يعد هذا مطلوبا. يجب أن يقلل هذا التغيير من خطر SharePoint رسائل الإعلام عبر الإنترنت في مجلد البريد الإلكتروني غير الهام. قم بتحديث سجل SPF TXT إذا كنت تصل إلى حد البحث 10 وتتلقى أخطاء تقول أشياء مثل" تجاوز حد البحث" و"عدد كبير جدا من القفزات".

- إذا كانت لديك بيئة مختلطة مع Office 365 Exchange محليا.

- كنت تنوي إعداد DKIM وDMARC (مستحسن).

## <a name="more-information-about-spf"></a>مزيد من المعلومات حول SPF

للحصول على أمثلة متقدمة، مناقشة أكثر تفصيلا حول بناء جملة SPF المدعومة، والانتحال، واستكشاف الأخطاء وإصلاحها، وكيفية دعم Office 365 ل SPF، راجع [كيفية عمل SPF لمنع الانتحال والتصيد الاحتيالي في Office 365](how-office-365-uses-spf-to-prevent-spoofing.md#HowSPFWorks).

## <a name="next-steps-dkim-and-dmarc"></a>الخطوات التالية: DKIM وDMARC

 تم تصميم SPF للمساعدة في منع الانتحال، ولكن هناك تقنيات تزييف هوية لا يمكن ل SPF الحماية منها. للدفاع ضد هذه، بمجرد إعداد SPF، يجب تكوين DKIM وDMARC Office 365.

هدف مصادقة البريد الإلكتروني [**DKIM**](use-dkim-to-validate-outbound-email.md) هو إثبات عدم العبث بمحتويات البريد.

الهدف من مصادقة البريد الإلكتروني [**DMARC**](use-dmarc-to-validate-email.md) هو التأكد من تطابق معلومات SPF وDKIM مع عنوان "من".

 للحصول على أمثلة متقدمة ومناقشة أكثر تفصيلا حول بناء جملة SPF المدعومة، راجع [كيفية عمل SPF لمنع الانتحال والتصيد الاحتيالي في Office 365](how-office-365-uses-spf-to-prevent-spoofing.md#HowSPFWorks).

[استخدام مرسلي ARC الموثوق بهم لتدفقات البريد المشروعة](/microsoft-365/security/office-365-security/use-arc-exceptions-to-mark-trusted-arc-senders?view=o365-21vianet&branch=tracyp_emailauth)

*حدد "هذه الصفحة" ضمن "ملاحظات" إذا كانت لديك ملاحظات حول هذه الوثائق.*
