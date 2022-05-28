---
title: كيفية استخدام DKIM للبريد الإلكتروني في مجالك المخصص
f1.keywords:
- NOCSH
ms.author: tracyp
author: MSFTTracyP
manager: dansimp
ms.date: 04/05/2021
audience: ITPro
ms.topic: article
ms.localizationpriority: high
search.appverid:
- MET150
ms.assetid: 56fee1c7-dc37-470e-9b09-33fff6d94617
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
ms.custom:
- seo-marvel-apr2020
description: تعرف على كيفية استخدام DomainKeys Identified Mail (DKIM) مع Microsoft 365 للتأكد من أن الرسائل المرسلة من مجالك المخصص موثوق بها من قبل أنظمة البريد الإلكتروني الوجهة.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 87f565d5058edff9ebde5af6e2cf84ca3e8262b4
ms.sourcegitcommit: 38a18b0195d99222c2c6da0c80838d24b5f66b97
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 05/28/2022
ms.locfileid: "65772139"
---
# <a name="use-dkim-to-validate-outbound-email-sent-from-your-custom-domain"></a>استخدام DKIM للتحقق من صحة البريد الإلكتروني الصادر المرسل من مجالك المخصص

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**ينطبق على**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [خطة 1 وخطة 2 من Microsoft Defender لـ Office 365](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

 تسرد هذه المقالة الخطوات لاستخدام DomainKeys Identified Mail (DKIM) مع Microsoft 365 للتأكد من أن أنظمة البريد الإلكتروني الوجهة تثق في الرسائل المرسلة الصادرة من مجالك المخصص.

في هذه المقالة:

- [كيفية عمل DKIM بشكل أفضل من SPF وحده لمنع تزييف الهوية الضارة](#how-dkim-works-better-than-spf-alone-to-prevent-malicious-spoofing)
- [خطوات لإنشاء DKIM وتمكينها وتعطيلها من مدخل Microsoft 365 Defender](#steps-to-create-enable-and-disable-dkim-from-microsoft-365-defender-portal)
- [خطوات لترقية مفاتيح 1024 بت يدويا إلى مفاتيح تشفير DKIM 2048 بت](#steps-to-manually-upgrade-your-1024-bit-keys-to-2048-bit-dkim-encryption-keys)
- [خطوات لإعداد DKIM يدويا](#steps-to-manually-set-up-dkim)
- [خطوات تكوين DKIM لأكثر من مجال مخصص واحد](#to-configure-dkim-for-more-than-one-custom-domain)
- [تعطيل نهج توقيع DKIM لمجال مخصص](#disabling-the-dkim-signing-policy-for-a-custom-domain)
- [السلوك الافتراضي ل DKIM و Microsoft 365](#default-behavior-for-dkim-and-microsoft-365)
- [إعداد DKIM بحيث يمكن لخدمة تابعة لجهة خارجية إرسال بريد إلكتروني أو تزييفه نيابة عن مجالك المخصص](#set-up-dkim-so-that-a-third-party-service-can-send-or-spoof-email-on-behalf-of-your-custom-domain)
- [الخطوات التالية: بعد إعداد DKIM Microsoft 365](#next-steps-after-you-set-up-dkim-for-microsoft-365)

> [!NOTE]
> Microsoft 365 إعداد DKIM تلقائيا لمجالات "onmicrosoft.com" الأولية الخاصة به. وهذا يعني أنك لا تحتاج إلى القيام بأي شيء لإعداد DKIM لأي أسماء مجالات أولية (على سبيل المثال، litware.onmicrosoft.com). لمزيد من المعلومات حول المجالات، راجع [الأسئلة المتداولة حول المجالات](../../admin/setup/domains-faq.yml#why-do-i-have-an--onmicrosoft-com--domain).

DKIM هي واحدة من ثلاثية أساليب المصادقة (SPF وDKIM وDMARC) التي تساعد على منع المهاجمين من إرسال الرسائل التي تبدو وكأنها تأتي من مجالك.

يتيح لك DKIM إضافة توقيع رقمي إلى رسائل البريد الإلكتروني الصادرة في رأس الرسالة. عند تكوين DKIM، يمكنك تخويل مجالك لإقران اسمه أو توقيعه برسالة بريد إلكتروني باستخدام مصادقة التشفير. يمكن لأنظمة البريد الإلكتروني التي تتلقى بريدا إلكترونيا من مجالك استخدام هذا التوقيع الرقمي للمساعدة في التحقق مما إذا كان البريد الإلكتروني الوارد شرعيا.

في الأساس، يقوم المفتاح الخاص بتشفير الرأس في البريد الإلكتروني الصادر للمجال. يتم نشر المفتاح العام في سجلات DNS الخاصة بالمجال، ويمكن للخوادم المتلقية استخدام هذا المفتاح لفك ترميز التوقيع. يساعد التحقق من DKIM الخوادم المتلقية على تأكيد أن البريد قادم بالفعل من مجالك وليس من شخص *ينتحل* مجالك.

> [!TIP]
>يمكنك اختيار عدم القيام بأي شيء حول DKIM لمجالك المخصص أيضا. إذا لم تقم بإعداد DKIM لمجالك المخصص، Microsoft 365 بإنشاء زوج مفاتيح خاص وعام، وتمكين توقيع DKIM، ثم تكوين النهج الافتراضي Microsoft 365 لمجالك المخصص.

 يعد تكوين DKIM المضمن في Microsoft-365 تغطية كافية لمعظم العملاء. ومع ذلك، يجب تكوين DKIM يدويا لمجالك المخصص في الظروف التالية:

- لديك أكثر من مجال مخصص واحد في Microsoft 365
- ستقوم بإعداد DMARC أيضا (**مستحسن**)
- تريد التحكم في مفتاحك الخاص
- تريد تخصيص سجلات CNAME
- تريد إعداد مفاتيح DKIM للبريد الإلكتروني الذي ينشأ من مجال تابع لجهة خارجية، على سبيل المثال، إذا كنت تستخدم بريدا مجمعا تابعا لجهة خارجية.

## <a name="how-dkim-works-better-than-spf-alone-to-prevent-malicious-spoofing"></a>كيفية عمل DKIM بشكل أفضل من SPF وحده لمنع تزييف الهوية الضارة
<a name="HowDKIMWorks"> </a>

يضيف SPF معلومات إلى مغلف رسالة ولكن DKIM *يشفر* توقيعا داخل رأس الرسالة. عند إعادة توجيه رسالة، يمكن تجريد أجزاء من مغلف الرسالة من قبل خادم إعادة التوجيه. نظرا لأن التوقيع الرقمي يظل مع رسالة البريد الإلكتروني لأنه جزء من رأس البريد الإلكتروني، فإن DKIM يعمل حتى عندما تتم إعادة توجيه رسالة كما هو موضح في المثال التالي.

![رسم تخطيطي يوضح رسالة تمت إعادة توجيهها تمرر مصادقة DKIM حيث يفشل فحص SPF.](../../media/28f93b4c-97e7-4309-acc4-fd0d2e0e3377.jpg)

في هذا المثال، إذا قمت بنشر سجل SPF TXT لمجالك فقط، فمن الممكن أن يكون خادم البريد الخاص بالمستلم قد وضع علامة على بريدك الإلكتروني كبريد عشوائي وإنشاء نتيجة إيجابية خاطئة. **تؤدي إضافة DKIM في هذا السيناريو إلى تقليل الإبلاغ *الإيجابي الخاطئ* عن البريد العشوائي.** نظرا إلى أن DKIM يعتمد على تشفير المفتاح العام لمصادقة عناوين IP وليس فقط، فإن DKIM يعتبر شكلا أقوى بكثير من المصادقة من SPF. نوصي باستخدام كل من SPF وDKIM، بالإضافة إلى DMARC في النشر الخاص بك.

> [!TIP]
> تستخدم DKIM مفتاحا خاصا لإدراج توقيع مشفر في رؤوس الرسائل. يتم إدراج مجال التوقيع أو المجال الصادر كقيمة للحقل **d=** في الرأس. ثم يستخدم مجال التحقق أو مجال المستلم الحقل **d=** للبحث عن المفتاح العام من DNS، ومصادقة الرسالة. إذا تم التحقق من الرسالة، يتم تمرير التحقق من DKIM.

## <a name="steps-to-create-enable-and-disable-dkim-from-microsoft-365-defender-portal"></a>خطوات لإنشاء DKIM وتمكينها وتعطيلها من مدخل Microsoft 365 Defender

سيتم عرض جميع المجالات المقبولة للمستأجر الخاص بك في مدخل Microsoft 365 Defender ضمن صفحة DKIM. إذا لم تتمكن من رؤيته، فقم بإضافة المجال المقبول من [صفحة المجالات](/microsoft-365/admin/setup/add-domain#add-a-domain).
بمجرد إضافة مجالك، اتبع الخطوات كما هو موضح أدناه لتكوين DKIM.

الخطوة 1: انقر فوق المجال الذي ترغب في تكوين DKIM على صفحة DKIM (https://security.microsoft.com/dkimv2 أو https://protection.office.com/dkimv2).

:::image type="content" source="../../media/126996261-2d331ec1-fc83-4a9d-a014-bd7e1854eb07.png" alt-text="صفحة DKIM في مدخل Microsoft 365 Defender مع تحديد مجال" lightbox="../../media/126996261-2d331ec1-fc83-4a9d-a014-bd7e1854eb07.png":::

الخطوة 2: قم بتحريك التبديل إلى **تمكين**. سترى نافذة منبثقة تفيد بأنك بحاجة إلى إضافة سجلات CNAME.

:::image type="content" source="../../media/127001645-4ccf89e6-6310-4a91-85d6-aaedbfd501d3.png" alt-text="القائمة المنبثقة لتفاصيل المجال مع زر إنشاء مفاتيح DKIM" lightbox="../../media/127001645-4ccf89e6-6310-4a91-85d6-aaedbfd501d3.png":::

الخطوة 3: نسخ CNAMES المعروضة في النافذة المنبثقة

:::image type="content" source="../../media/127001787-3cce2c29-e0e4-4712-af53-c51dcba33c46.png" alt-text="النافذة المنبثقة &quot;Publish CNAMEs&quot; التي تحتوي على سجلي CNAME للنسخ" lightbox="../../media/127001787-3cce2c29-e0e4-4712-af53-c51dcba33c46.png":::

الخطوة 4: نشر سجلات CNAME المنسوخة إلى موفر خدمة DNS.

على موقع موفر DNS على ويب، أضف سجلات CNAME ل DKIM التي تريد تمكينها. تأكد من تعيين الحقول إلى القيم التالية لكل منها:

```text
Record Type: CNAME (Alias)
> Host: Paste the values you copy from DKIM page.
Points to address: Copy the value from DKIM page.
TTL: 3600 (or your provider default)
```

الخطوة 5: العودة إلى صفحة DKIM لتمكين DKIM.

:::image type="content" source="../../media/126995186-9b3fdefa-a3a9-4f5a-9304-1099a2ce7cef.png" alt-text="التبديل لتمكين DKIM" lightbox="../../media/126995186-9b3fdefa-a3a9-4f5a-9304-1099a2ce7cef.png":::

إذا رأيت سجل CNAME غير موجود، فقد يكون ذلك بسبب:

1. المزامنة مع خادم DNS، والتي قد تستغرق بضع ثوان إلى ساعات، إذا استمرت المشكلة في تكرار الخطوات مرة أخرى
2. تحقق من وجود أي أخطاء في لصق النسخ، مثل مساحة إضافية أو علامات تبويب وما إلى ذلك.

إذا كنت ترغب في تعطيل DKIM، فلتبديل مرة أخرى إلى وضع التعطيل

## <a name="steps-to-manually-upgrade-your-1024-bit-keys-to-2048-bit-dkim-encryption-keys"></a>خطوات لترقية مفاتيح 1024 بت يدويا إلى مفاتيح تشفير DKIM 2048 بت
<a name="1024to2048DKIM"> </a>

> [!NOTE]
> Microsoft 365 إعداد DKIM تلقائيا لمجالات *onmicrosoft.com*. لا توجد خطوات مطلوبة لاستخدام DKIM لأي أسماء مجالات أولية (مثل litware.*onmicrosoft.com*). لمزيد من المعلومات حول المجالات، راجع [الأسئلة المتداولة حول المجالات](../../admin/setup/domains-faq.yml#why-do-i-have-an--onmicrosoft-com--domain).

نظرا إلى دعم كل من البت 1024 و2048 لمفاتيح DKIM، ستخبرك هذه التوجيهات بكيفية ترقية مفتاح 1024 بت إلى 2048 في [Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell). الخطوات أدناه مخصصة لحالات الاستخدام، يرجى اختيار الحالة التي تناسب تكوينك بشكل أفضل.

- عند **تكوين DKIM بالفعل**، يمكنك تدوير البت عن طريق تشغيل الأمر التالي:

  ```powershell
  Rotate-DkimSigningConfig -KeySize 2048 -Identity <DkimSigningConfigIdParameter>
  ```

  **او**

- **لتنفيذ جديد ل DKIM**، قم بتشغيل الأمر التالي:

  ```powershell
  New-DkimSigningConfig -DomainName <Domain for which config is to be created> -KeySize 2048 -Enabled $true
  ```

ابق متصلا Exchange Online PowerShell *للتحقق من* التكوين عن طريق تشغيل الأمر التالي:

```powershell
Get-DkimSigningConfig -Identity <Domain for which the configuration was set> | Format-List
```

> [!TIP]
> يصبح هذا المفتاح الجديد 2048 بت ساري المفعول على RotateOnDate، وسيرسل رسائل البريد الإلكتروني باستخدام المفتاح 1024 بت في الأثناء. بعد أربعة أيام، يمكنك الاختبار مرة أخرى باستخدام المفتاح 2048 بت (أي بمجرد أن يدخل الاستدارة حيز التنفيذ إلى المحدد الثاني).

إذا كنت تريد إجراء استدارة إلى المحدد الثاني، بعد أربعة أيام وتأكيد استخدام 2048 بت، فقم بتدوير مفتاح المحدد الثاني يدويا باستخدام cmdlet المناسب المدرج أعلاه.

للحصول على معلومات مفصلة حول بناء الجملة والمعلمة، راجع المقالات التالية: [استدارة DkimSigningConfig](/powershell/module/exchange/rotate-dkimsigningconfig) و [New-DkimSigningConfig](/powershell/module/exchange/new-dkimsigningconfig) و [Get-DkimSigningConfig](/powershell/module/exchange/get-dkimsigningconfig).

## <a name="steps-to-manually-set-up-dkim"></a>خطوات لإعداد DKIM يدويا
<a name="SetUpDKIMO365"> </a>

لتكوين DKIM، سوف تكمل الخطوات التالية:

- [نشر سجلي CNAME لمجالك المخصص في DNS](use-dkim-to-validate-outbound-email.md#Publish2CNAME)
- [تمكين توقيع DKIM لمجالك المخصص](use-dkim-to-validate-outbound-email.md#EnableDKIMinO365)

### <a name="publish-two-cname-records-for-your-custom-domain-in-dns"></a>نشر سجلي CNAME لمجالك المخصص في DNS
<a name="Publish2CNAME"> </a>

لكل مجال تريد إضافة توقيع DKIM له في DNS، تحتاج إلى نشر سجلين CNAME.

> [!NOTE]
> إذا لم تكن قد قرأت المقالة الكاملة، فربما فاتتك معلومات اتصال PowerShell الموفرة للوقت هذه: [الاتصال إلى Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

تشغيل الأوامر التالية في Exchange Online PowerShell لإنشاء سجلات المحدد:

```powershell
New-DkimSigningConfig -DomainName <domain> -Enabled $false
Get-DkimSigningConfig -Identity <domain> | Format-List Selector1CNAME, Selector2CNAME
```

إذا قمت بتوفير مجالات مخصصة بالإضافة إلى المجال الأولي في Microsoft 365، فيجب نشر سجلين CNAME لكل مجال إضافي. لذلك، إذا كان لديك مجالان، يجب نشر سجلي CNAME إضافيين، وهكذا.

استخدم التنسيق التالي لسجلات CNAME.

> [!IMPORTANT]
> إذا كنت أحد عملائنا سحابة القطاع الحكومي العاليين، فإننا نحسب _customDomainIdentifier_ بشكل مختلف! بدلا من البحث عن سجل MX ل _initialDomain_ لحساب _customDomainIdentifier_، بدلا من ذلك نقوم بحسابه مباشرة من المجال المخصص. على سبيل المثال، إذا كان مجالك المخصص هو "contoso.com" يصبح _customDomainIdentifier_ "contoso-com"، يتم استبدال أي فترات بشرطة. لذلك، بغض النظر عن تسجيل MX الذي يشير إليه _initialDomain_ ، ستستخدم دائما الأسلوب أعلاه لحساب _customDomainIdentifier_ لاستخدامه في سجلات CNAME.

```console
Host name:            selector1._domainkey
Points to address or value:    selector1-<customDomainIdentifier>._domainkey.<initialDomain>
TTL:                3600

Host name:            selector2._domainkey
Points to address or value:    selector2-<customDomainIdentifier>._domainkey.<initialDomain>
TTL:                3600
```

المكان:

- بالنسبة Microsoft 365، ستكون المحددات دائما "selector1" أو "selector2".
- _customDomainIdentifier_ هو نفس _customDomainIdentifier_ في سجل MX المخصص لمجالك المخصص الذي يظهر قبل mail.protection.outlook.com. على سبيل المثال، في سجل MX التالي contoso.com المجال، _customDomainIdentifier_ هو contoso-com:

  > contoso.com.  3600 في MX 5 contoso-com.mail.protection.outlook.com

- _initialDomain_ هو المجال الذي استخدمته عند التسجيل للحصول على Microsoft 365. تنتهي المجالات الأولية دائما onmicrosoft.com. للحصول على معلومات حول تحديد مجالك الأولي، راجع [الأسئلة المتداولة حول المجالات](../../admin/setup/domains-faq.yml#why-do-i-have-an--onmicrosoft-com--domain).

على سبيل المثال، إذا كان لديك مجال أولي من cohovineyardandwinery.onmicrosoft.com ومجالين مخصصين cohovineyard.com cohowinery.com، فستحتاج إلى إعداد سجلين CNAME لكل مجال إضافي، لما مجموعه أربعة سجلات CNAME.

```console
Host name:            selector1._domainkey
Points to address or value:    selector1-cohovineyard-com._domainkey.cohovineyardandwinery.onmicrosoft.com
TTL:                3600

Host name:            selector2._domainkey
Points to address or value:    selector2-cohovineyard-com._domainkey.cohovineyardandwinery.onmicrosoft.com
TTL:                3600

Host name:            selector1._domainkey
Points to address or value:    selector1-cohowinery-com._domainkey.cohovineyardandwinery.onmicrosoft.com
TTL:                3600

Host name:            selector2._domainkey
Points to address or value:    selector2-cohowinery-com._domainkey.cohovineyardandwinery.onmicrosoft.com
TTL:                3600
```

> [!NOTE]
> من المهم إنشاء السجل الثاني، ولكن قد يتوفر واحد فقط من المحددات في وقت الإنشاء. في جوهرها، قد يشير المحدد الثاني إلى عنوان لم يتم إنشاؤه بعد. ما زلنا نوصي بإنشاء سجل CNAME الثاني، لأن استدارة المفتاح الخاص بك ستكون سلسة.

### <a name="steps-to-enable-dkim-signing-for-your-custom-domain"></a>خطوات لتمكين توقيع DKIM لمجالك المخصص
<a name="EnableDKIMinO365"> </a>

بمجرد نشر سجلات CNAME في DNS، تصبح جاهزا لتمكين DKIM من تسجيل الدخول عبر Microsoft 365. يمكنك القيام بذلك إما من خلال مركز مسؤولي Microsoft 365 أو باستخدام PowerShell.

#### <a name="to-enable-dkim-signing-for-your-custom-domain-in-the-microsoft-365-defender-portal"></a>لتمكين توقيع DKIM لمجالك المخصص في مدخل Microsoft 365 Defender

1. في مدخل Microsoft 365 Defender، <https://security.microsoft.com>انتقل إلى **نهج التعاون** \> & البريد الإلكتروني **& قواعد** \> **DKIM**  \> في قسم **القواعد**. للانتقال مباشرة إلى صفحة DKIM، استخدم <https://security.microsoft.com/dkimv2>.

2. في صفحة **DKIM** ، حدد المجال بالنقر فوق الاسم.

3. في القائمة المنبثقة للتفاصيل التي تظهر، قم بتغيير **رسائل التوقيع لهذا المجال باستخدام إعداد تواقيع DKIM** إلى **ممكن** (![تشغيل.](../../media/scc-toggle-on.png))

   عند الانتهاء، انقر فوق **مفاتيح استدارة DKIM**.

4. كرر هذه الخطوة لكل مجال مخصص.

5. إذا كنت تقوم بتكوين DKIM للمرة الأولى وشاهدت الخطأ "لم يتم حفظ مفاتيح DKIM لهذا المجال"، فسيتعين عليك استخدام Windows PowerShell لتمكين توقيع DKIM كما هو موضح في الخطوة التالية.

#### <a name="to-enable-dkim-signing-for-your-custom-domain-by-using-powershell"></a>لتمكين توقيع DKIM لمجالك المخصص باستخدام PowerShell

> [!IMPORTANT]
> :::image type="content" source="../../media/dkim.png" alt-text="لم يتم حفظ مفاتيح DKIM لخطأ المجال هذا" lightbox="../../media/dkim.png":::
> إذا كنت تقوم بتكوين DKIM للمرة الأولى وشاهدت الخطأ "لم يتم حفظ مفاتيح DKIM لهذا المجال" فأكمل الأمر في الخطوة 2 أدناه (على سبيل المثال، `Set-DkimSigningConfig -Identity contoso.com -Enabled $true`) لرؤية المفتاح.

1. [الاتصال إلى Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

2. استخدم بناء الجملة التالي:

   ```powershell
   Set-DkimSigningConfig -Identity <Domain> -Enabled $true
   ```

   \<Domain\> هو اسم المجال المخصص الذي تريد تمكين توقيع DKIM له.

   يتيح هذا المثال توقيع DKIM contoso.com المجال:

   ```powershell
   Set-DkimSigningConfig -Identity contoso.com -Enabled $true
   ```

#### <a name="to-confirm-dkim-signing-is-configured-properly-for-microsoft-365"></a>لتأكيد تكوين توقيع DKIM بشكل صحيح Microsoft 365

انتظر بضع دقائق قبل اتباع هذه الخطوات للتأكد من تكوين DKIM بشكل صحيح. يسمح هذا الوقت لنشر معلومات DKIM حول المجال في جميع أنحاء الشبكة.

- أرسل رسالة من حساب ضمن مجالك الممكن Microsoft 365 DKIM إلى حساب بريد إلكتروني آخر مثل outlook.com أو Hotmail.com.
- لا تستخدم حساب aol.com لأغراض الاختبار. قد تتخطى AOL التحقق من DKIM إذا تم تمرير فحص SPF. سيؤدي هذا إلى إلغاء اختبارك.
- افتح الرسالة وانظر إلى الرأس. تختلف إرشادات عرض رأس الرسالة وفقا لعميل المراسلة. للحصول على إرشادات حول عرض رؤوس الرسائل في Outlook، راجع [عرض رؤوس رسائل الإنترنت في Outlook](https://support.microsoft.com/office/cd039382-dc6e-4264-ac74-c048563d212c).

  ستحتوي الرسالة الموقعة على DKIM على اسم المضيف والمجال الذي قمت بتعريفه عند نشر إدخالات CNAME. ستبدو الرسالة مثل هذا المثال:

  ```console
    From: Example User <example@contoso.com>
    DKIM-Signature: v=1; a=rsa-sha256; q=dns/txt; c=relaxed/relaxed;
        s=selector1; d=contoso.com; t=1429912795;
        h=From:To:Message-ID:Subject:MIME-Version:Content-Type;
        bh=<body hash>;
        b=<signed field>;
  ```

- ابحث عن رأس Authentication-Results. بينما تستخدم كل خدمة تلقي تنسيقا مختلفا قليلا لطوابع البريد الوارد، يجب أن تتضمن النتيجة شيئا مثل **DKIM=pass** أو **DKIM=OK**.

## <a name="to-configure-dkim-for-more-than-one-custom-domain"></a>لتكوين DKIM لأكثر من مجال مخصص واحد
<a name="DKIMMultiDomain"> </a>

إذا قررت في مرحلة ما في المستقبل إضافة مجال مخصص آخر وتريد تمكين DKIM للمجال الجديد، فيجب إكمال الخطوات الواردة في هذه المقالة لكل مجال. على وجه التحديد، أكمل جميع الخطوات في [ما تحتاج إلى القيام به لإعداد DKIM يدويا](use-dkim-to-validate-outbound-email.md#SetUpDKIMO365).

## <a name="disabling-the-dkim-signing-policy-for-a-custom-domain"></a>تعطيل نهج توقيع DKIM لمجال مخصص
<a name="DisableDKIMSigningPolicy"> </a>

لا يؤدي تعطيل نهج التوقيع إلى تعطيل DKIM بشكل كامل. بعد فترة من الوقت، سيقوم Microsoft 365 تلقائيا بتطبيق النهج الافتراضي لمجالك، إذا كان النهج الافتراضي لا يزال في الحالة الممكنة. إذا كنت ترغب في تعطيل DKIM بالكامل، فأنت بحاجة إلى تعطيل DKIM على كل من المجالين المخصص والافتراضي. لمزيد من المعلومات، راجع [السلوك الافتراضي ل DKIM Microsoft 365](use-dkim-to-validate-outbound-email.md#DefaultDKIMbehavior).

### <a name="to-disable-the-dkim-signing-policy-by-using-windows-powershell"></a>لتعطيل نهج توقيع DKIM باستخدام Windows PowerShell

1. [الاتصال إلى Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

2. قم بتشغيل أحد الأوامر التالية لكل مجال تريد تعطيل توقيع DKIM له.

   ```powershell
   $p = Get-DkimSigningConfig -Identity <Domain>
   $p[0] | Set-DkimSigningConfig -Enabled $false
   ```

   على سبيل المثال:

   ```powershell
   $p = Get-DkimSigningConfig -Identity contoso.com
   $p[0] | Set-DkimSigningConfig -Enabled $false
   ```

   او

   ```powershell
   Set-DkimSigningConfig -Identity $p[<number>].Identity -Enabled $false
   ```

   حيث _الرقم_ هو فهرس النهج. على سبيل المثال:

   ```powershell
   Set-DkimSigningConfig -Identity $p[0].Identity -Enabled $false
   ```

## <a name="default-behavior-for-dkim-and-microsoft-365"></a>السلوك الافتراضي ل DKIM و Microsoft 365
<a name="DefaultDKIMbehavior"> </a>

إذا لم تقم بتمكين DKIM، Microsoft 365 تلقائيا بإنشاء مفتاح DKIM عام 2048 بت لعنوان توجيه البريد الإلكتروني (MOERA) ل Microsoft Online والمجال الأولي والمفتاح الخاص المقترن الذي نخزنه داخليا في مركز البيانات. بشكل افتراضي، يستخدم Microsoft 365 تكوين توقيع افتراضي للمجالات التي ليس لها نهج مضمن. وهذا يعني أنه إذا لم تقم بإعداد DKIM بنفسك، فسيستخدم Microsoft 365 نهجه الافتراضي والمفاتيح التي يقوم بإنشائها لتمكين DKIM لمجالك.

أيضا، إذا قمت بتعطيل توقيع DKIM على مجالك المخصص بعد تمكينه، بعد فترة من الوقت، Microsoft 365 تطبيق نهج المجال MOERA/initial تلقائيا لمجالك المخصص.

في المثال التالي، افترض أن DKIM fabrikam.com تم تمكينه بواسطة Microsoft 365، وليس من قبل مسؤول المجال. وهذا يعني أن CNAMEs المطلوبة غير موجودة في DNS. ستبدو تواقيع DKIM للبريد الإلكتروني من هذا المجال مماثلة لما يلي:

```console
From: Second Example <second.example@fabrikam.com>
DKIM-Signature: v=1; a=rsa-sha256; q=dns/txt; c=relaxed/relaxed;
    s=selector1-fabrikam-com; d=contoso.onmicrosoft.com; t=1429912795;
    h=From:To:Message-ID:Subject:MIME-Version:Content-Type;
    bh=<body hash>;
    b=<signed field>;
```

في هذا المثال، يحتوي اسم المضيف والمجال على القيم التي يشير إليها CNAME إذا تم تمكين توقيع DKIM fabrikam.com من قبل مسؤول المجال. في نهاية المطاف، سيتم توقيع كل رسالة واحدة يتم إرسالها من Microsoft 365 DKIM. إذا قمت بتمكين DKIM بنفسك، سيكون المجال هو نفس المجال في العنوان من، في هذه الحالة fabrikam.com. إذا لم تقم بذلك، فلن تتم محاذاتها وستستخدم بدلا من ذلك المجال الأولي لمؤسستك. للحصول على معلومات حول تحديد مجالك الأولي، راجع [الأسئلة المتداولة حول المجالات](../../admin/setup/domains-faq.yml#why-do-i-have-an--onmicrosoft-com--domain).

## <a name="set-up-dkim-so-that-a-third-party-service-can-send-or-spoof-email-on-behalf-of-your-custom-domain"></a>إعداد DKIM بحيث يمكن لخدمة تابعة لجهة خارجية إرسال بريد إلكتروني أو تزييفه نيابة عن مجالك المخصص
<a name="SetUp3rdPartyspoof"> </a>

يتيح لك بعض موفري خدمة البريد الإلكتروني المجمعين أو موفري البرامج كخدمة إعداد مفاتيح DKIM للبريد الإلكتروني الذي ينشأ من خدمتهم. يتطلب هذا التنسيق بينك وبين الجهة الخارجية من أجل إعداد سجلات DNS الضرورية. يمكن أن تحتوي بعض خوادم الجهات الخارجية على سجلات CNAME الخاصة بها مع محددات مختلفة. لا توجد اثنتان من المؤسسات تفعل ذلك بنفس الطريقة بالضبط. بدلا من ذلك، تعتمد العملية بالكامل على المؤسسة.

قد تبدو رسالة المثال التي تعرض DKIM مكونة بشكل صحيح contoso.com bulkemailprovider.com كما يلي:

```console
Return-Path: <communication@bulkemailprovider.com>
 From: <sender@contoso.com>
 DKIM-Signature: s=s1024; d=contoso.com
 Subject: Here is a message from Bulk Email Provider's infrastructure, but with a DKIM signature authorized by contoso.com
```

في هذا المثال، من أجل تحقيق هذه النتيجة:

1. منح موفر البريد الإلكتروني المجمع Contoso مفتاح DKIM عام.

2. نشرت شركة Contoso مفتاح DKIM إلى سجل DNS الخاص بها.

3. عند إرسال البريد الإلكتروني، يقوم موفر البريد الإلكتروني المجمع بتوقيع المفتاح باستخدام المفتاح الخاص المقابل. بالقيام بذلك، قام موفر البريد الإلكتروني المجمع بإرفاق توقيع DKIM برأس الرسالة.

4. يؤدي تلقي أنظمة البريد الإلكتروني إلى إجراء فحص DKIM عن طريق مصادقة القيمة DKIM-Signature d=\<domain\> مقابل المجال في العنوان من: (5322.From) للرسالة. في هذا المثال، تتطابق القيم:

   > sender@**contoso.com**

   > d=**contoso.com**

## <a name="identify-domains-that-do-not-send-email"></a>تحديد المجالات التي لا ترسل بريدا إلكترونيا

يجب على المؤسسات أن توضح بشكل صريح ما إذا كان المجال لا يرسل بريدا إلكترونيا عن طريق تحديد `v=DKIM1; p=` سجل DKIM لتلك المجالات. ينصح هذا بتلقي خوادم البريد الإلكتروني بعدم وجود مفاتيح عامة صالحة للمجال، ويجب رفض أي بريد إلكتروني يدعي أنه من هذا المجال. يجب القيام بذلك لكل مجال ومجال فرعي باستخدام حرف بدل DKIM.

على سبيل المثال، سيبدو سجل DKIM كما يلي:

```console
*._domainkey.SubDomainThatShouldntSendMail.contoso.com. TXT "v=DKIM1; p="
```

## <a name="next-steps-after-you-set-up-dkim-for-microsoft-365"></a>الخطوات التالية: بعد إعداد DKIM Microsoft 365
<a name="DKIMNextSteps"> </a>

**على الرغم من أن DKIM مصمم للمساعدة في منع الانتحال، فإن DKIM يعمل بشكل أفضل مع SPF وDMARC.**

بمجرد إعداد DKIM، إذا لم تكن قد قمت بإعداد SPF بالفعل، يجب عليك القيام بذلك. للحصول على مقدمة سريعة إلى SPF وتكوينه بسرعة، راجع [**إعداد SPF في Microsoft 365 للمساعدة في منع انتحال هوية**](set-up-spf-in-office-365-to-help-prevent-spoofing.md). للحصول على فهم أكثر تعمقا لكيفية استخدام Microsoft 365 ل SPF، أو لاستكشاف الأخطاء وإصلاحها أو عمليات النشر غير القياسية مثل عمليات النشر المختلطة، ابدأ [بكيفية استخدام Microsoft 365 إطار نهج المرسل (SPF) لمنع تزييف الهوية](how-office-365-uses-spf-to-prevent-spoofing.md).

بعد ذلك، راجع [**استخدام DMARC للتحقق من صحة البريد الإلكتروني**](use-dmarc-to-validate-email.md). تتضمن [رؤوس رسائل مكافحة البريد العشوائي](anti-spam-message-headers.md) بناء الجملة وحقول الرأس المستخدمة من قبل Microsoft 365 لعمليات التحقق من DKIM.

**سيتحقق هذا الاختبار من أن** تكوين توقيع DKIM قد تم تكوينه بشكل صحيح، وأنه تم نشر إدخالات DNS المناسبة.

> [!NOTE]
> تتطلب هذه الميزة حساب مسؤول Microsoft 365. هذه الميزة غير متوفرة Microsoft 365 Government أو Microsoft 365 التي تديرها 21Vianet أو Microsoft 365 Germany.

<div class="nextstepaction">
<p><a href="https://admin.microsoft.com/AdminPortal/?searchSolutions=DKIM#/homepage" data-linktype="external">تشغيل الاختبارات: DKIM</a></p>
</div>

## <a name="more-information"></a>معلومات إضافية

تدوير المفتاح عبر PowerShell: [استدارة DkimSigningConfig](/powershell/module/exchange/rotate-dkimsigningconfig)

[استخدام DMARC للتحقق من صحة البريد الإلكتروني](/microsoft-365/security/office-365-security/use-dmarc-to-validate-email?view=o365-worldwide&preserve-view=true)

[استخدام مرسلي ARC الموثوق بهم لتدفقات البريد المشروعة](/microsoft-365/security/office-365-security/use-arc-exceptions-to-mark-trusted-arc-senders?view=o365-21vianet&branch=tracyp_emailauth)