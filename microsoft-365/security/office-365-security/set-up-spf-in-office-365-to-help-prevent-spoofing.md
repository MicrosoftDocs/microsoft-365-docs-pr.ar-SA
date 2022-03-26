---
title: إعداد SPF للمساعدة في منع التهز
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
ms.openlocfilehash: ab7bd0e579bfe26236eb009dc09689ddb90f2782
ms.sourcegitcommit: 43adb0d91af234c34e22d450a9c1d26aa745c2ca
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 10/19/2021
ms.locfileid: "63568603"
---
# <a name="set-up-spf-to-help-prevent-spoofing"></a>إعداد SPF للمساعدة في منع التهز

- [المتطلبات الأساسية](#prerequisites)
- [إنشاء سجل SPF TXT أو تحديثه](#create-or-update-your-spf-txt-record)
- [كيفية التعامل مع المناطق الفرعية؟](#how-to-handle-subdomains)
- [استكشاف الأخطاء في SPF وإصلاحها](#troubleshooting-spf)

<!--
[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Applies to**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender for Office 365 plan 1 and plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)
-->

تصف هذه المقالة كيفية تحديث سجل خدمة أسماء المجالات (DNS) بحيث يمكنك استخدام مصادقة البريد الإلكتروني في إطار نهج المرسل (SPF) مع مجالك المخصص في Office 365.

يساعد SPF *على التحقق من* صحة البريد الإلكتروني الصادر المرسل من مجالك المخصص (يأتي من الشخص الذي يقول أنه كذلك). إنها خطوة أولى في إعداد أساليب مصادقة البريد الإلكتروني الموصى بها بالكامل ل SPF و [DKIM](use-dkim-to-validate-outbound-email.md) و [DMARC](use-dmarc-to-validate-email.md).

- [المتطلبات الأساسية](#prerequisites)
- [إنشاء سجل SPF TXT أو تحديثه](#create-or-update-your-spf-txt-record)
  - [كيفية التعامل مع المناطق الفرعية؟](#how-to-handle-subdomains)
- [ما الذي تقوم به مصادقة البريد الإلكتروني في SPF فعليا؟](#what-does-spf-email-authentication-actually-do)
  - [استكشاف الأخطاء في SPF وإصلاحها](#troubleshooting-spf)
- [مزيد من المعلومات حول SPF](#more-information-about-spf)

## <a name="prerequisites"></a>المتطلبات الأساسية

> [!IMPORTANT]
> إذا كنت شركة **صغيرة**، أو إذا كنت غير مألوف مع عناوين IP أو تكوين DNS، فاتصل جهة تسجيل مجالات الإنترنت (على المثال. GoDaddy و Bluehost و web.com) & المساعدة في تكوين *DNS ل SPF* (وأي طريقة أخرى لمصادقة البريد الإلكتروني). <p> **إذا لم تستخدم** عنوان URL مخصصا (وينتهي عنوان URL المستخدم ل Office 365 في **onmicrosoft.com**)، فقد تم إعداد SPF مسبقا لك في Office 365 الخدمة.

لنبدأ.

سيتم إنشاء سجل SPF TXT Office 365 في DNS خارجي لأي مجالات أو مجالات فرعية مخصصة. تحتاج إلى بعض المعلومات لجعل السجل. جمع هذه المعلومات:

- سجل SPF TXT لمجالك المخصص، إذا كان موجودا. للحصول على الإرشادات، راجع [جمع المعلومات التي تحتاج إليها لإنشاء Office 365 DNS](../../admin/get-help-with-domains/information-for-dns-records.md).

- انتقل إلى خادم (خوادم) المراسلات واكتشف عناوين IP الخارجية (المطلوبة من كل خوادم المراسلات المحلية). على سبيل المثال **، 131.107.2.200**.

- أسماء المجالات التي يجب استخدامها لجميع المجالات التابعة لأي جهة خارجية التي تحتاج إلى تضمينها في سجل SPF TXT. لقد تم إعداد بعض موفري البريد المجمع لمواد فرعية لاستخدامها لعملائهم. على سبيل المثال، قامت MailChimp الشركة **بإعداد** servers.mcsv.net.

- تعرف على قاعدة التنفيذ التي تريد استخدامها لسجل SPF TXT. يوصى **باستخدام القاعدة** الكل. للحصول على معلومات مفصلة حول خيارات بناء الجملة الأخرى، راجع بناء جملة سجل [SPF TXT Office 365](how-office-365-uses-spf-to-prevent-spoofing.md#SPFSyntaxO365).

> [!IMPORTANT]
> لاستخدام مجال مخصص، يتطلب Office 365 إضافة سجل TXT إطار نهج المرسل (SPF) إلى سجل DNS للمساعدة في منع الانتحال.

## <a name="create-or-update-your-spf-txt-record"></a>إنشاء سجل SPF TXT أو تحديثه

1. تأكد من أنك على دراية ب بناء جملة SPF في الجدول التالي.

    <br>

    ****

    |عنصر|إذا كنت تستخدم...|هل هي شائعة للعملاء؟|أضف هذا...|
    |---|---|---|---|
    |1|أي نظام بريد إلكتروني (مطلوب)|شائع. تبدأ كل سجلات SPF TXT بهذه القيمة|`v=spf1`|
    |2|Exchange Online|شائع|`include:spf.protection.outlook.com`|
    |3|Exchange Online مخصص فقط|غير شائع|`ip4:23.103.224.0/19` <br> `ip4:206.191.224.0/19` <br> `ip4:40.103.0.0/16` <br> `include:spf.protection.outlook.com`|
    |4|Office 365 ألمانيا، Microsoft Cloud Germany فقط|غير شائع|`include:spf.protection.outlook.de`|
    |5|نظام البريد الإلكتروني الخاص ب جهة خارجية|غير شائع|`include:<domain_name>` <p> \<domain_name\> هو مجال نظام البريد الإلكتروني الخاص ب جهة خارجية.|
    |6|نظام البريد الإلكتروني في الموقع. على سبيل المثال، Exchange Online Protection بريد إلكتروني آخر|غير شائع|استخدم أحد هذه الأنظمة لكل نظام بريد إضافي: <p> `ip4:<IP_address>` <br> `ip6:<IP_address>` <br> `include:<domain_name>` <p> \<IP_address\> وهي \<domain_name\> عنوان IP ومجال نظام البريد الإلكتروني الآخر الذي يرسل البريد نيابة عن مجالك.|
    |7|أي نظام بريد إلكتروني (مطلوب)|شائع. تنتهي كل سجلات SPF TXT بهذه القيمة|`<enforcement rule>` <p> قد تكون هذه إحدى القيم العديدة. نوصي بالقيمة `-all`.|
    |

2. إذا لم تكن قد فعلت ذلك بعد، فشكل سجل SPF TXT باستخدام بناء الجملة من الجدول.

   على سبيل المثال، إذا كنت مستضافا بالكامل في Office 365، أي ليس لديك خوادم بريد في الموقع، فإن سجل SPF TXT سيتضمن الصفوف 1 و2 و7 وسيبدو كما يلي:

   ```text
   v=spf1 include:spf.protection.outlook.com -all
   ```

   **المثال أعلاه هو سجل SPF TXT الأكثر شيوعا**. يعمل هذا السجل للجميع تقريبا، بغض النظر عما إذا كان مركز بيانات Microsoft موجودا في الولايات المتحدة أو في أوروبا (بما في ذلك ألمانيا) أو في موقع آخر.

   ومع ذلك، إذا اشتريت Office 365 ألمانيا، وهي جزء من Microsoft Cloud Germany، يجب استخدام العبارة المتضمنة من السطر 4 بدلا من السطر 2. على سبيل المثال، إذا كنت مستضافا بالكامل في Office 365 ألمانيا، أي ليس لديك خوادم بريد في الموقع، فإن سجل SPF TXT سيتضمن الصفوف 1 و4 و7 وسيبدو كما يلي:

   ```text
   v=spf1 include:spf.protection.outlook.de -all
   ```

   إذا كنت قد نشرت بالفعل في Office 365 وقد قمت بإعداد سجلات SPF TXT لمجالك المخصص، وتهاجر إلى Office 365 ألمانيا، يجب تحديث سجل SPF TXT. للقيام بذلك، غير إلى `include:spf.protection.outlook.com` `include:spf.protection.outlook.de`.

3. بعد تكوين سجل SPF TXT، ستحتاج إلى تحديث السجل في DNS. **يمكنك الحصول على سجل SPF TXT واحد فقط لمجال.** إذا كان سجل SPF TXT موجودا، فبدلا من إضافة سجل جديد، ستحتاج إلى تحديث السجل الموجود. انتقل إلى [إنشاء سجلات DNS Office 365](../../admin/get-help-with-domains/create-dns-records-at-any-dns-hosting-provider.md)، ثم حدد الارتباط لمضيف DNS.

4. اختبر سجل SPF TXT.

## <a name="how-to-handle-subdomains"></a>كيفية التعامل مع المناطق الفرعية؟

من المهم ملاحظة أنك تحتاج إلى إنشاء سجل منفصل لكل مجال فرعي حيث لا ترث المجالات الفرعية سجل *SPF لمجال المستوى الأعلى الخاص بها*.

يعد سجل أحرف البدل SPF (`*.`) مطلوبا لكل مجال ومجال فرعي لمنع المهاجمين من إرسال بريد إلكتروني يدعي أنه من مجالات فرعية غير موجودة. على سبيل المثال:

```text
*.subdomain.contoso.com. IN TXT "v=spf1 -all"
```

## <a name="troubleshooting-spf"></a>استكشاف الأخطاء في SPF وإصلاحها

هل تواجه مشكلة في سجل SPF TXT؟ اقرأ [استكشاف الأخطاء وإصلاحها: أفضل الممارسات ل SPF في Office 365](how-office-365-uses-spf-to-prevent-spoofing.md#SPFTroubleshoot).

## <a name="what-does-spf-email-authentication-actually-do"></a>ما الذي تقوم به مصادقة البريد الإلكتروني في SPF فعليا؟

يحدد SPF خوادم البريد المسموح لها بإرسال البريد بالنيابة عنك. بشكل أساسي، يساعد SPF، إلى جانب DKIM و DMARC والتقنيات الأخرى التي يدعمها Office 365، على منع الخادعة والتصيد الاحتيالي. يتم إضافة SPF كسجل TXT يستخدم بواسطة DNS لتحديد خوادم البريد التي يمكنها إرسال البريد نيابة عن مجالك المخصص. تشير أنظمة بريد المستلمين إلى سجل SPF TXT لتحديد ما إذا كانت رسالة من مجالك المخصص تأتي من خادم مراسلة معتمد.

على سبيل المثال، لنقول أن مجالك المخصص contoso.com يستخدم Office 365. يمكنك إضافة سجل SPF TXT يسرد Office 365 خوادم المراسلة كخادمات بريد شرعية لمجالك. عندما يتلقى خادم المراسلة رسالة من joe@contoso.com، سيبحث الخادم عن سجل SPF TXT ل contoso.com ويكتشف ما إذا كانت الرسالة صالحة أم لا. إذا اكتشف الخادم المتلقي أن الرسالة تأتي من خادم آخر غير خوادم مراسلات Office 365 المدرجة في سجل SPF، يمكن أن يختار خادم البريد المتلقي رفض الرسالة كرسالة عشوائية.

كذلك، إذا لم يكن لمجالك المخصص سجل SPF TXT، فقد يرفض بعض الخوادم المتلقية الرسالة بشكل صريح. وذلك لأن الخادم المتلقي لا يمكنه التحقق من أن الرسالة تأتي من خادم مراسلة معتمد.

إذا سبق لك إعداد البريد Office 365، فضمنت بالفعل خوادم المراسلة من Microsoft في DNS كسجل SPF TXT. ومع ذلك، هناك بعض الحالات التي قد تحتاج فيها إلى تحديث سجل SPF TXT في DNS. على سبيل المثال:

- في السابق، كان عليك إضافة سجل SPF TXT مختلف إلى مجالك المخصص إذا كنت تستخدم SharePoint Online. لم يعد هذا مطلوبا. يجب أن يقلل هذا التغيير من خطر SharePoint رسائل الإعلام عبر الإنترنت في مجلد البريد الإلكتروني غير الهام. قم بتحديث سجل SPF TXT إذا كنت تصل إلى حد البحث 10 وتتلقى أخطاء مثل "تجاوز حد البحث" و"الكثير من القفزات".

- إذا كان لديك بيئة مختلطة مع Office 365 Exchange المحلية.

- أنت تنوي إعداد DKIM و DMARC (مستحسن).

## <a name="more-information-about-spf"></a>مزيد من المعلومات حول SPF

للحصول على أمثلة متقدمة، راجع كيفية عمل SPF لمنع الانتحال والتصيد الاحتيالي في Office 365 للحصول على أمثلة متقدمة حول بناء جملة [SPF](how-office-365-uses-spf-to-prevent-spoofing.md#HowSPFWorks) المدعوم والانتحال وإصلاحها وكيفية دعم Office 365 ل SPF.

## <a name="next-steps-dkim-and-dmarc"></a>الخطوات التالية: DKIM و DMARC

 تم تصميم SPF للمساعدة في منع ال انتحال، ولكن هناك أساليب انتحال لا يمكن ل SPF حمايتها. للدفاع ضد هذه، بمجرد إعداد SPF، يجب تكوين DKIM و DMARC Office 365.

هدف مصادقة البريد الإلكتروني ل [**DKIM**](use-dkim-to-validate-outbound-email.md) هو إثبات عدم التلاعب بمحتويات البريد.

[**هدف مصادقة البريد الإلكتروني ل DMARC**](use-dmarc-to-validate-email.md) هو التأكد من تطابق معلومات SPF و DKIM مع العنوان من.

 للحصول على أمثلة متقدمة ومناقشة أكثر تفصيلا حول بناء جملة SPF المعتمد، راجع كيفية عمل [SPF](how-office-365-uses-spf-to-prevent-spoofing.md#HowSPFWorks) لمنع الانتحال والتصيد الاحتيالي في Office 365.

*حدد "هذه الصفحة" ضمن "ملاحظات" إذا كانت لديك ملاحظات حول هذه الوثائق.*
