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
description: تعرف على كيفية استخدام DomainKeys Identified Mail (DKIM) مع Microsoft 365 للتأكد من أن الرسائل المرسلة من مجالك المخصص موثوق بها بواسطة أنظمة البريد الإلكتروني الوجهة.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 25333a1616bb1f4e4e529c17813bdd58f4c768b4
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/08/2022
ms.locfileid: "63565878"
---
# <a name="use-dkim-to-validate-outbound-email-sent-from-your-custom-domain"></a>استخدام DKIM للتحقق من صحة البريد الإلكتروني الصادر المرسل من مجالك المخصص

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**ينطبق على**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender Office 365 الخطة 1 الخطة 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

 تسرد هذه المقالة خطوات استخدام DomainKeys Identified Mail (DKIM) مع Microsoft 365 للتأكد من أن أنظمة البريد الإلكتروني الوجهة تثق بالرسائل المرسلة من مجالك المخصص.

في هذه المقالة:

- [كيفية عمل DKIM بشكل أفضل من SPF وحده لمنع اانتحال البرامج الضارة](#how-dkim-works-better-than-spf-alone-to-prevent-malicious-spoofing)
- [خطوات إنشاء DKIM وتمكينها وتعطيلها من Microsoft 365 Defender مدخل](#steps-to-create-enable-and-disable-dkim-from-microsoft-365-defender-portal)
- [خطوات لترقية مفاتيح 1024 بت يدويا إلى مفاتيح تشفير DKIM لل 2048 بت](#steps-to-manually-upgrade-your-1024-bit-keys-to-2048-bit-dkim-encryption-keys)
- [خطوات لإعداد DKIM يدويا](#steps-to-manually-set-up-dkim)
- [خطوات لتكوين DKIM لأكثر من مجال مخصص واحد](#to-configure-dkim-for-more-than-one-custom-domain)
- [تعطيل نهج توقيع DKIM لمجال مخصص](#disabling-the-dkim-signing-policy-for-a-custom-domain)
- [السلوك الافتراضي ل DKIM Microsoft 365](#default-behavior-for-dkim-and-microsoft-365)
- [إعداد DKIM بحيث يمكن لخدمة جهة خارجية إرسال بريد إلكتروني أو اتهابها نيابة عن مجالك المخصص](#set-up-dkim-so-that-a-third-party-service-can-send-or-spoof-email-on-behalf-of-your-custom-domain)
- [الخطوات التالية: بعد إعداد DKIM Microsoft 365](#next-steps-after-you-set-up-dkim-for-microsoft-365)

> [!NOTE]
> Microsoft 365 تلقائيا إلى إعداد DKIM لمجالاتها onmicrosoft.com الأولية. وهذا يعني أنك لست بحاجة إلى القيام بأي شيء لإعداد DKIM لأي أسماء مجالات أولية (على سبيل المثال، litware.onmicrosoft.com). لمزيد من المعلومات حول المجالات، راجع [الأسئلة الشائعة حول المجالات](../../admin/setup/domains-faq.yml#why-do-i-have-an--onmicrosoft-com--domain).

DKIM هو أحد ثلاثة أساليب المصادقة (SPF و DKIM و DMARC) التي تساعد في منع المهاجمين من إرسال الرسائل التي تبدو كأنها تأتي من مجالك.

يتيح لك DKIM إضافة توقيع رقمي إلى رسائل البريد الإلكتروني الصادرة في رأس الرسالة. عند تكوين DKIM، يمكنك تخويل مجالك لاقران اسمه أو توقيعه برسالة بريد إلكتروني باستخدام مصادقة التشفير. يمكن نظم البريد الإلكتروني التي تحصل على بريد إلكتروني من مجالك استخدام هذا التوقيع الرقمي للمساعدة في التحقق مما إذا كان البريد الإلكتروني الوارد شرعيا أم لا.

بشكل أساسي، يقوم المفتاح الخاص بتشفير الرأس في البريد الإلكتروني الصادر لمجال. يتم نشر المفتاح العمومي في سجلات DNS للمجال، ويمكن للخوادم المتلقية استخدام هذا المفتاح لفك ترميز التوقيع. تساعد عملية التحقق من صحة DKIM الخوادم المتلقية على تأكيد أن البريد يأتي بالفعل من مجالك وليس من قبل شخص *ينتحل* مجالك.

> [!TIP]
>يمكنك اختيار عدم القيام بأي شيء حيال DKIM لمجالك المخصص أيضا. إذا لم تكن قد قمت بإعداد DKIM لمجالك المخصص، فإن Microsoft 365 ينشئ زوج مفاتيح عامة وخاصة، ويمكن توقيع DKIM، ثم ينشئ نهج Microsoft 365 الافتراضي لمجالك المخصص.

 إن تكوين DKIM المضمن في Microsoft-365 هو تغطية كافية لمعظم العملاء. ومع ذلك، يجب تكوين DKIM يدويا لمجالك المخصص في الحالات التالية:

- لديك أكثر من مجال مخصص واحد في Microsoft 365
- سوف تقوم بإعداد DMARC أيضا (**مستحسن**)
- تريد التحكم في المفتاح الخاص
- تريد تخصيص سجلات CNAME
- تريد إعداد مفاتيح DKIM للبريد الإلكتروني الذي ينشأ عن مجال جهة خارجية، على سبيل المثال، إذا كنت تستخدم مرسل بريد مجمع من جهة خارجية.

## <a name="how-dkim-works-better-than-spf-alone-to-prevent-malicious-spoofing"></a>كيفية عمل DKIM بشكل أفضل من SPF وحده لمنع اانتحال البرامج الضارة
<a name="HowDKIMWorks"> </a>

يضيف SPF معلومات إلى مغلف رسالة ولكن *DKIM يقوم* بتشفير توقيع داخل رأس الرسالة. عند إعادة توجيه رسالة، يمكن أن يجرد خادم إعادة توجيه أجزاء من مغلف هذه الرسالة. نظرا لأن التوقيع الرقمي يبقى مع رسالة البريد الإلكتروني لأنه جزء من رأس البريد الإلكتروني، تعمل DKIM حتى عند إعادة توجيه رسالة كما هو موضح في المثال التالي.

![رسم تخطيطي يعرض رسالة مع توجيهها تمر بمصادقة DKIM حيث يفشل فحص SPF.](../../media/28f93b4c-97e7-4309-acc4-fd0d2e0e3377.jpg)

في هذا المثال، إذا قمت بنشر سجل SPF TXT لمجالك فقط، فقد يكون خادم البريد للمستلم قد وضع علامة على بريدك الإلكتروني كبريد عشوائي وأنتج نتيجة إيجابية خاطئة. **تساعد إضافة DKIM في هذا السيناريو على تقليل *الإبلاغ عن البريد العشوائي الإيجابي* الزائف.** نظرا لأن DKIM تعتمد على تشفير المفاتيح العمومية لمصادقة عناوين IP وليس فقط، تعتبر DKIM شكلا أقوى بكثير من المصادقة من SPF. نوصي باستخدام كل من SPF و DKIM، بالإضافة إلى DMARC في عملية النشر.

> [!TIP]
> تستخدم DKIM مفتاحا خاصا لإدراج توقيع مشفر في رؤوس الرسائل. يتم إدراج مجال التوقيع أو المجال الصادر كقيمة الحقل **d=** في الرأس. بعد ذلك، يستخدم المجال الذي يتحقق من الصحة، أو مجال المستلم، الحقل **d=** للبحث عن المفتاح العمومي من DNS، ومصادقة الرسالة. إذا تم التحقق من الرسالة، يتم تمرير شيك DKIM.

## <a name="steps-to-create-enable-and-disable-dkim-from-microsoft-365-defender-portal"></a>خطوات إنشاء DKIM وتمكينها وتعطيلها من Microsoft 365 Defender مدخل

سيتم عرض جميع المجالات المقبولة للمستأجر في مدخل Microsoft 365 Defender ضمن صفحة DKIM. إذا لم تشاهده، أضف مجالك المقبول من [صفحة المجالات](/microsoft-365/admin/setup/add-domain#add-a-domain).
بعد إضافة مجالك، اتبع الخطوات كما هو موضح أدناه لتكوين DKIM.

الخطوة 1: انقر فوق المجال الذي تريد تكوين DKIM على صفحة DKIM (https://security.microsoft.com/dkimv2 أو https://protection.office.com/dkimv2).

![صفحة DKIM في مدخل Microsoft 365 Defender مع تحديد مجال.](../../media/126996261-2d331ec1-fc83-4a9d-a014-bd7e1854eb07.png)

الخطوة 2: قم ب تمرير تبديل إلى **تمكين**. سترى نافذة منبثقة تفيد بحاجتك إلى إضافة سجلات CNAME.

![قم ب تمرير تبديل إلى تمكين لتمكين DKIM.](../../media/126995186-9b3fdefa-a3a9-4f5a-9304-1099a2ce7cef.png)

الخطوة 3: نسخ CNAMES المعروضة في النافذة المنبثقة

الخطوة 4: نشر سجلات CNAME المنسوخة إلى موفر خدمة DNS.

على موقع موفر DNS على الويب، أضف سجلات CNAME ل DKIM التي تريد تمكينها. تأكد من تعيين الحقول إلى القيم التالية لكل منها:

```text
Record Type: CNAME (Alias)
> Host: Paste the values you copy from DKIM page.
Points to address: Copy the value from DKIM page.
TTL: 3600 (or your provider default)
```

الخطوة 5: العودة إلى صفحة DKIM لتمكين DKIM.

![قم ب تمرير تبديل إلى تمكين لتمكين DKIM.](../../media/126995186-9b3fdefa-a3a9-4f5a-9304-1099a2ce7cef.png)

إذا رأيت أن سجل CNAME غير موجود، فقد يكون ذلك بسبب:

1. المزامنة مع خادم DNS، والتي قد تستغرق بضع ثوان إلى ساعات، إذا استمرت المشكلة في تكرار الخطوات مرة أخرى
2. تحقق من وجود أي أخطاء في لصق النسخ، مثل المساحة الإضافية أو علامات التبويب وما إلى ذلك.

إذا كنت ترغب في تعطيل DKIM، فعاد إلى وضع تعطيل

## <a name="steps-to-manually-upgrade-your-1024-bit-keys-to-2048-bit-dkim-encryption-keys"></a>خطوات لترقية مفاتيح 1024 بت يدويا إلى مفاتيح تشفير DKIM لل 2048 بت
<a name="1024to2048DKIM"> </a>

> [!NOTE]
> Microsoft 365 تلقائيا إلى إعداد DKIM *onmicrosoft.com* المجالات. لا يلزم اتخاذ أي خطوات لاستخدام DKIM لأي أسماء مجالات أولية (مثل litware.*onmicrosoft.com*). لمزيد من المعلومات حول المجالات، راجع [الأسئلة الشائعة حول المجالات](../../admin/setup/domains-faq.yml#why-do-i-have-an--onmicrosoft-com--domain).

نظرا لأن كل من البت 1024 و2048 معتمدان لمفاتيح DKIM، ستخبرك هذه التوجيهات بكيفية ترقية مفتاح 1024 بت إلى 2048 [في Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell). الخطوات أدناه هي لقضيتين من حالات الاستخدام، يرجى اختيار الخيار الأكثر ملائمة لتكوينك.

- عند تكوين **DKIM بالفعل**، يمكنك تدوير البت عن طريق تشغيل الأمر التالي:

  ```powershell
  Rotate-DkimSigningConfig -KeySize 2048 -Identity <DkimSigningConfigIdParameter>
  ```

  **أو**

- لتنفيذ **DKIM جديد**، تشغيل الأمر التالي:

  ```powershell
  New-DkimSigningConfig -DomainName <Domain for which config is to be created> -KeySize 2048 -Enabled $true
  ```

ابق على اتصال Exchange Online PowerShell للتحقق *من التكوين* عن طريق تشغيل الأمر التالي:

```powershell
Get-DkimSigningConfig -Identity <Domain for which the configuration was set> | Format-List
```

> [!TIP]
> يتم تأثير هذا المفتاح الجديد 2048 بت على RotateOnDate، وسيرسل رسائل بريد إلكتروني باستخدام المفتاح 1024 بت في المؤقت. بعد أربعة أيام، يمكنك الاختبار مرة أخرى باستخدام مفتاح 2048 بت (أي بمجرد أن يتم تأثير الاستدارة على المحدد الثاني).

إذا كنت تريد إجراء استدارة إلى المحدد الثاني، بعد أربعة أيام وتأكيد استخدام 2048 بت، قم بتدوير مفتاح المحدد الثاني يدويا باستخدام أمر cmdlet المناسب المدرج أعلاه.

للحصول على معلومات مفصلة حول بناء الجملة والمعلمات، راجع المقالات التالية: [استدارة-DkimSigningConfig](/powershell/module/exchange/rotate-dkimsigningconfig) و [New-DkimSigningConfig](/powershell/module/exchange/new-dkimsigningconfig) و [Get-DkimSigningConfig](/powershell/module/exchange/get-dkimsigningconfig).

## <a name="steps-to-manually-set-up-dkim"></a>خطوات لإعداد DKIM يدويا
<a name="SetUpDKIMO365"> </a>

لتكوين DKIM، ستكمل الخطوات التالية:

- [نشر سجلي CNAME لمجالك المخصص في DNS](use-dkim-to-validate-outbound-email.md#Publish2CNAME)
- [تمكين توقيع DKIM لمجالك المخصص](use-dkim-to-validate-outbound-email.md#EnableDKIMinO365)

### <a name="publish-two-cname-records-for-your-custom-domain-in-dns"></a>نشر سجلي CNAME لمجالك المخصص في DNS
<a name="Publish2CNAME"> </a>

لكل مجال تريد إضافة توقيع DKIM له في DNS، ستحتاج إلى نشر سجلي CNAME.

> [!NOTE]
> إذا لم تقرأ المقالة بالكامل، فقد تكون قد فاتتك معلومات اتصال PowerShell التي توفر الوقت: الاتصال إلى Exchange Online [PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

قم بتشغيل الأوامر التالية في Exchange Online PowerShell لإنشاء سجلات المحدد:

```powershell
New-DkimSigningConfig -DomainName <domain> -Enabled $false
Get-DkimSigningConfig -Identity <domain> | Format-List Selector1CNAME, Selector2CNAME
```

إذا قمت بتوفير مجالات مخصصة بالإضافة إلى المجال الأولي في Microsoft 365، فيجب نشر سجلي CNAME لكل مجال إضافي. وبالتالي، إذا كان لديك مجالان، فيجب نشر سجلي CNAME إضافيين، وهكذا.

استخدم التنسيق التالي لسجلات CNAME.

> [!IMPORTANT]
> إذا كنت أحد عملاءنا سحابة القطاع الحكومي عالية، فنحن نقوم بحساب _customDomainIdentifier_ بشكل مختلف! بدلا من البحث عن سجل MX للمجال الأولي  لحساب _customDomainIdentifier_، بدلا من ذلك نقوم بحسابه مباشرة من المجال المخصص. على سبيل المثال، إذا كان مجالك المخصص "contoso.com" يتحول _customDomainIdentifier_ إلى "contoso-com"، يتم استبدال أي فترات شرطة. لذلك، بغض النظر عن سجل MX الأولي _الذي يشير إلىه_ المجال، سوف تستخدم دائما الأسلوب أعلاه لحساب _customDomainIdentifier_ لاستخدامه في سجلات CNAME.

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
- _customDomainIdentifier_ هو نفس _customDomainIdentifier_ في سجل MX المخصص لمجالك المخصص الذي يظهر قبل mail.protection.outlook.com. على سبيل المثال، في سجل MX التالي contoso.com المجال، _يكون customDomainIdentifier_ هو contoso-com:

  > contoso.com.  3600 في MX 5 contoso-com.mail.protection.outlook.com

- _initialDomain_ هو المجال الذي استخدمته عند تسجيل Microsoft 365. تنتهي المجالات الأولية دائما في onmicrosoft.com. للحصول على معلومات حول تحديد مجالك الأولي، راجع [الأسئلة الشائعة حول المجالات](../../admin/setup/domains-faq.yml#why-do-i-have-an--onmicrosoft-com--domain).

على سبيل المثال، إذا كان لديك مجال أولي ل cohovineyardandwinery.onmicrosoft.com ومجالان مخصصان cohovineyard.com و cohowinery.com، يجب إعداد سجلي CNAME لكل مجال إضافي، لما مجموعه أربعة سجلات CNAME.

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
> من المهم إنشاء السجل الثاني، ولكن قد يتوفر محدد واحد فقط في وقت الإنشاء. بشكل أساسي، قد يشير المحدد الثاني إلى عنوان لم يتم إنشاؤه بعد. ما زلنا نوصي بإنشاء سجل CNAME الثاني، لأن استدارة المفتاح ستكون سلسة.

### <a name="steps-to-enable-dkim-signing-for-your-custom-domain"></a>خطوات لتمكين توقيع DKIM لمجالك المخصص
<a name="EnableDKIMinO365"> </a>

بعد نشر سجلات CNAME في DNS، ستكون جاهزا لتمكين تسجيل الدخول عبر DKIM Microsoft 365. يمكنك القيام بذلك إما من خلال مركز مسؤولي Microsoft 365 أو باستخدام PowerShell.

#### <a name="to-enable-dkim-signing-for-your-custom-domain-in-the-microsoft-365-defender-portal"></a>لتمكين توقيع DKIM لمجالك المخصص في مدخل Microsoft 365 Defender

1. في مدخل Microsoft 365 Defender في <https://security.microsoft.com>، انتقل إلى البريد الإلكتروني & **سياسات** \>  \>  \> التعاون & قواعد المخاطر **DKIM** في **القسم القواعد**. الانتقال مباشرة إلى صفحة DKIM، استخدم <https://security.microsoft.com/dkimv2>.

2. في صفحة **DKIM** ، حدد المجال بالنقر فوق الاسم.

3. في قائمة التفاصيل التي تظهر، قم بتغيير إعداد توقيع رسائل هذا المجال باستخدام **تواقيع DKIM** إلى **"** تمكين" (![تبديل).](../../media/scc-toggle-on.png))

   عند الانتهاء، انقر فوق **تدوير مفاتيح DKIM**.

4. كرر هذه الخطوة لكل مجال مخصص.

5. إذا كنت تقوم بتكوين DKIM للمرة الأولى وشاهدت الخطأ "لم يتم حفظ مفاتيح DKIM لهذا المجال"، فسينبغي عليك استخدام Windows PowerShell لتمكين توقيع DKIM كما هو موضح في الخطوة التالية.

#### <a name="to-enable-dkim-signing-for-your-custom-domain-by-using-powershell"></a>لتمكين توقيع DKIM لمجالك المخصص باستخدام PowerShell

> [!IMPORTANT]
> :::image type="content" source="../../media/dkim.png" alt-text="الخطأ 'لا توجد مفاتيح DKIM محفوظة لهذا المجال.'":::
> إذا كنت تقوم بتكوين DKIM للمرة الأولى وشاهدت رسالة الخطأ "لا توجد مفاتيح DKIM محفوظة لهذا المجال"، فأكمل الأمر في الخطوة 2 أدناه ( `Set-DkimSigningConfig -Identity contoso.com -Enabled $true`على سبيل المثال، ) لرؤية المفتاح.

1. [الاتصال إلى Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

2. استخدم بناء الجملة التالي:

   ```powershell
   Set-DkimSigningConfig -Identity <Domain> -Enabled $true
   ```

   \<Domain\> هو اسم المجال المخصص الذي تريد تمكين توقيع DKIM له.

   يمكن هذا المثال توقيع DKIM لمجال contoso.com:

   ```powershell
   Set-DkimSigningConfig -Identity contoso.com -Enabled $true
   ```

#### <a name="to-confirm-dkim-signing-is-configured-properly-for-microsoft-365"></a>لتأكيد تكوين توقيع DKIM بشكل صحيح Microsoft 365

انتظر بضع دقائق قبل اتباع هذه الخطوات للتأكد من تكوين DKIM بشكل صحيح. يتيح هذا الوقت لنشر معلومات DKIM حول المجال عبر الشبكة.

- أرسل رسالة من حساب ضمن مجالك Microsoft 365 DKIM إلى حساب بريد إلكتروني آخر مثل outlook.com أو Hotmail.com.
- لا تستخدم حسابا aol.com لأغراض الاختبار. قد يتخطى AOL التحقق من DKIM إذا تم تمرير شيك SPF. سيبطل هذا الاختبار.
- افتح الرسالة وانظر إلى الرأس. ستختلف إرشادات عرض رأس الرسالة استنادا إلى عميل المراسلة. للحصول على إرشادات حول عرض رؤوس الرسائل في Outlook، راجع عرض رؤوس الرسائل عبر الإنترنت [في](https://support.microsoft.com/office/cd039382-dc6e-4264-ac74-c048563d212c) Outlook.

  ستحتوي الرسالة الموقعة على DKIM على اسم المضيف والمجال الذي حددته عند نشر إدخالات CNAME. ستبدو الرسالة بهذا المثال:

  ```console
    From: Example User <example@contoso.com>
    DKIM-Signature: v=1; a=rsa-sha256; q=dns/txt; c=relaxed/relaxed;
        s=selector1; d=contoso.com; t=1429912795;
        h=From:To:Message-ID:Subject:MIME-Version:Content-Type;
        bh=<body hash>;
        b=<signed field>;
  ```

- ابحث عن رأس Authentication-Results. في حين تستخدم كل خدمة مستلمة تنسيقا مختلفا بعض الشيء لطوابع البريد الوارد، يجب أن تتضمن النتيجة شيئا مثل **DKIM=pass** أو **DKIM=OK**.

## <a name="to-configure-dkim-for-more-than-one-custom-domain"></a>لتكوين DKIM لأكثر من مجال مخصص واحد
<a name="DKIMMultiDomain"> </a>

إذا قررت في مرحلة ما في المستقبل إضافة مجال مخصص آخر وتريد تمكين DKIM للمجال الجديد، فيجب إكمال الخطوات في هذه المقالة لكل مجال. على وجه التحديد، أكمل كل الخطوات في [ما تحتاج إلى القيام به لإعداد DKIM يدويا](use-dkim-to-validate-outbound-email.md#SetUpDKIMO365).

## <a name="disabling-the-dkim-signing-policy-for-a-custom-domain"></a>تعطيل نهج توقيع DKIM لمجال مخصص
<a name="DisableDKIMSigningPolicy"> </a>

لا يعمل تعطيل نهج التوقيع على تعطيل DKIM بشكل كامل. بعد فترة زمنية، Microsoft 365 تطبيق النهج الافتراضي لمجالك تلقائيا، إذا كان النهج الافتراضي لا يزال في حالة التمكين. إذا كنت ترغب في تعطيل DKIM بالكامل، يجب تعطيل DKIM على كل من المجالين المخصص والافتراضي. لمزيد من المعلومات، راجع [السلوك الافتراضي ل DKIM Microsoft 365](use-dkim-to-validate-outbound-email.md#DefaultDKIMbehavior).

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

   أو

   ```powershell
   Set-DkimSigningConfig -Identity $p[<number>].Identity -Enabled $false
   ```

   حيث _الرقم_ هو فهرس النهج. على سبيل المثال:

   ```powershell
   Set-DkimSigningConfig -Identity $p[0].Identity -Enabled $false
   ```

## <a name="default-behavior-for-dkim-and-microsoft-365"></a>السلوك الافتراضي ل DKIM Microsoft 365
<a name="DefaultDKIMbehavior"> </a>

إذا لم تقوم بتمكين DKIM، يقوم Microsoft 365 تلقائيا بإنشاء مفتاح DKIM عام 2048 بت ل عنوان توجيه البريد الإلكتروني ل Microsoft Online (MOERA)/المجال الأولي والمفتاح الخاص المقترن الذي نقوم بتخزينه داخليا في مركز البيانات. بشكل افتراضي Microsoft 365 تستخدم هذه Microsoft 365 تكوين توقيع افتراضي للمجالات التي ليس لديها نهج في مكانها. وهذا يعني أنه إذا لم تقوم بإعداد DKIM بنفسك، Microsoft 365 استخدام النهج والمفاتيح الافتراضية التي ينشئها لتمكين DKIM لمجالك.

أيضا، إذا قمت بتعطيل توقيع DKIM على مجالك المخصص بعد تمكينه، بعد مرور فترة زمنية، سيطبق Microsoft 365 تلقائيا نهج المجال MOERA/الأولي لمجالك المخصص.

في المثال التالي، افترض أن DKIM fabrikam.com تم تمكينه بواسطة Microsoft 365، وليس من قبل مسؤول المجال. وهذا يعني أن أسماء CNAMEs المطلوبة غير موجودة في DNS. ستبدو تواقيع DKIM للبريد الإلكتروني من هذا المجال على شكل ما يلي:

```console
From: Second Example <second.example@fabrikam.com>
DKIM-Signature: v=1; a=rsa-sha256; q=dns/txt; c=relaxed/relaxed;
    s=selector1-fabrikam-com; d=contoso.onmicrosoft.com; t=1429912795;
    h=From:To:Message-ID:Subject:MIME-Version:Content-Type;
    bh=<body hash>;
    b=<signed field>;
```

في هذا المثال، يحتوي اسم المضيف والمجال على القيم التي يشير CNAME لها إذا تم تمكين توقيع DKIM fabrikam.com بواسطة مسؤول المجال. وفي النهاية، ستكون كل رسالة مرسلة من Microsoft 365 موقعة من DKIM. إذا قمت بتمكين DKIM بنفسك، سيكون المجال هو نفسه المجال في العنوان من: ، في هذه الحالة fabrikam.com. إذا لم تفعل ذلك، فإنه لن يتم محاذاته وبدلا من ذلك سيستخدم المجال الأولي الخاص مؤسستك. للحصول على معلومات حول تحديد مجالك الأولي، راجع [الأسئلة الشائعة حول المجالات](../../admin/setup/domains-faq.yml#why-do-i-have-an--onmicrosoft-com--domain).

## <a name="set-up-dkim-so-that-a-third-party-service-can-send-or-spoof-email-on-behalf-of-your-custom-domain"></a>إعداد DKIM بحيث يمكن لخدمة جهة خارجية إرسال بريد إلكتروني أو اتهابها نيابة عن مجالك المخصص
<a name="SetUp3rdPartyspoof"> </a>

يتيح لك بعض موفري خدمات البريد الإلكتروني المجمع، أو موفري البرامج كخدمات، إعداد مفاتيح DKIM للبريد الإلكتروني الذي ينشأ من خدمتهم. يتطلب ذلك التنسيق بينك وبين جهة خارجية من أجل إعداد سجلات DNS الضرورية. يمكن أن يكون لبعض الخوادم الخارجية سجلات CNAME الخاصة بها مع محددات مختلفة. لا يمكن لمنظمتين القيام بذلك بالطريقة نفسها تماما. بدلا من ذلك، تعتمد العملية بشكل كامل على المؤسسة.

مثال على رسالة تعرض DKIM مكونة بشكل صحيح contoso.com bulkemailprovider.com تبدو كما يلي:

```console
Return-Path: <communication@bulkemailprovider.com>
 From: <sender@contoso.com>
 DKIM-Signature: s=s1024; d=contoso.com
 Subject: Here is a message from Bulk Email Provider's infrastructure, but with a DKIM signature authorized by contoso.com
```

في هذا المثال، لتحقيق هذه النتيجة:

1. منح موفر البريد الإلكتروني المجمع شركة Contoso مفتاح DKIM عام.

2. نشرت شركة Contoso المفتاح DKIM إلى سجل DNS الخاص بها.

3. عند إرسال البريد الإلكتروني، يوقع موفر البريد الإلكتروني المجمع المفتاح باستخدام المفتاح الخاص المقابل. من خلال القيام بذلك، يقوم موفر البريد الإلكتروني المجمع ب إرفاق توقيع DKIM إلى رأس الرسالة.

4. يؤدي استلام أنظمة البريد الإلكتروني إلى إجراء فحص DKIM من خلال مصادقة قيمة DKIM-Signature d=\<domain\> مقابل المجال في العنوان من: (5322.From) للرسالة. في هذا المثال، تتطابق القيم:

   > sender@**contoso.com**

   > d=**contoso.com**

## <a name="identify-domains-that-do-not-send-email"></a>تحديد المجالات التي لا ترسل بريدا إلكترونيا

يجب أن توضح المؤسسات بشكل صريح ما إذا كان `v=DKIM1; p=` المجال لا يرسل بريدا إلكترونيا عن طريق التحديد في سجل DKIM لتلك المجالات. وينصح ذلك بتلقي خوادم البريد الإلكتروني بعدم وجود مفاتيح عامة صالحة للمجال، ويجب رفض أي بريد إلكتروني يدعي أنه من هذا المجال. يجب القيام بذلك لكل مجال ومجال فرعي باستخدام أحرف البدل DKIM.

على سبيل المثال، سيبدو سجل DKIM كما يلي:

```console
*._domainkey.SubDomainThatShouldntSendMail.contoso.com. TXT "v=DKIM1; p="
```

## <a name="next-steps-after-you-set-up-dkim-for-microsoft-365"></a>الخطوات التالية: بعد إعداد DKIM Microsoft 365
<a name="DKIMNextSteps"> </a>

**على الرغم من أن DKIM مصمم للمساعدة في منع االانتحال، إلا أن DKIM تعمل بشكل أفضل مع SPF و DMARC.**

بعد إعداد DKIM، إذا لم تكن قد قمت بإعداد SPF بالفعل، يجب عليك القيام بذلك. للحصول على مقدمة سريعة حول SPF وتكوينه بسرعة، راجع إعداد [**SPF في Microsoft 365 للمساعدة في منع التهزف**](set-up-spf-in-office-365-to-help-prevent-spoofing.md). لفهم كيفية استخدام Microsoft 365 SPF أو عمليات النشر غير القياسية أو استكشاف الأخطاء وإصلاحها مثل عمليات النشر المختلط، ابدأ بكيفية استخدام Microsoft 365 إطار نهج المرسل [(SPF)](how-office-365-uses-spf-to-prevent-spoofing.md) لمنع الانتحال.

بعد ذلك، [**راجع استخدام DMARC للتحقق من صحة البريد الإلكتروني**](use-dmarc-to-validate-email.md). [تتضمن رؤوس رسائل مكافحة البريد](anti-spam-message-headers.md) العشوائي حقلي بناء الجملة والرأس المستخدمين بواسطة Microsoft 365 DKIM.

**سيتحقق هذا الاختبار** من تكوين توقيع DKIM بشكل صحيح، ومن نشر إدخالات DNS الصحيحة.

> [!NOTE]
> تتطلب هذه الميزة حساب مسؤول Microsoft 365 جديد. لا تتوفر هذه الميزة Microsoft 365 Government أو Microsoft 365 التي يتم تشغيلها بواسطة 21Vianet أو Microsoft 365 Germany.

<div class="nextstepaction">
<p><a href="https://admin.microsoft.com/AdminPortal/?searchSolutions=DKIM#/homepage" data-linktype="external">تشغيل الاختبارات: DKIM</a></p>
</div>

## <a name="more-information"></a>معلومات إضافية

استدارة المفتاح عبر PowerShell: [Rotate-DkimSigningConfig](/powershell/module/exchange/rotate-dkimsigningconfig)

[استخدام DMARC للتحقق من صحة البريد الإلكتروني](use-dmarc-to-validate-email.md)
