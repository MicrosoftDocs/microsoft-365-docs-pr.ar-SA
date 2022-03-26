---
title: إدارة السماح والحظر في قائمة السماح/الحظر للمستأجر
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: how-to
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection:
- M365-security-compliance
ms.custom: ''
description: يمكن للمسؤولين معرفة كيفية إدارة السماح والحظر في قائمة السماح/الحظر للمستأجر في مدخل الأمان.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: e27da44a38162955df252e29c1754c93a2dc8967
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/08/2022
ms.locfileid: "63567860"
---
# <a name="manage-the-tenant-allowblock-list"></a>إدارة قائمة السماح/الحظر للمستأجر

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**ينطبق على**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender Office 365 الخطة 1 الخطة 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

> [!NOTE]
>
> توجد بعض الميزات الموضحة في هذه المقالة في معاينة، وتخضع للتغيير، ولا تتوفر في كل المؤسسات.
>
> إذا لم يكن لدى مؤسستك الميزات المنتحلة كما هو موضح في هذه المقالة، فشاهد تجربة الإدارة القديمة المنتحلة في إدارة المرسلين المزحلين باستخدام نهج المعلومات المنتحلة ورؤى المعلومات المنتحلة في [EOP](walkthrough-spoof-intelligence-insight.md).

في Microsoft 365 المؤسسات التي بها علب بريد في Exchange Online أو مؤسسات Exchange Online Protection (EOP) مستقلة بدون علب بريد Exchange Online، قد لا توافق على قرار تصفية EOP. على سبيل المثال، قد يتم وضع علامة على رسالة جيدة كرسالة سيئة (إيجابية خاطئة)، أو قد يتم السماح برسالة سيئة عبرها (سالب خطأ).

توفر لك قائمة السماح/الحظر للمستأجر في مدخل Microsoft 365 Defender طريقة لتجاوز Microsoft 365 وتصفية الأحكام يدويا. يتم استخدام قائمة السماح/الحظر للمستأجر أثناء تدفق البريد للرسائل الواردة (لا تنطبق على الرسائل داخل المؤسسة) وفي وقت نقرات المستخدم. يمكنك تحديد أنواع التجاوز التالية:

- عناوين URL التي يجب حظرها.
- الملفات التي يجب حظرها.
- رسائل البريد الإلكتروني أو المجالات المرسلة التي يجب حظرها.
- المرسلون المنتحلون للسماح أو الحظر. إذا قمت بتجاوز قرار السماح أو الحظر في المعلومات الاستخبارية المنتحلة، يتحول المرسل الم انتحال إلى السماح اليدوي أو حظر الإدخال الذي يظهر فقط على علامة التبويب انتحال في  قائمة السماح/الحظر للمستأجر.[](learn-about-spoof-intelligence.md) يمكنك أيضا إنشاء إدخالات السماح أو الحظر يدويا للمرسلين المزحلين هنا قبل اكتشافهم بواسطة المعلومات المنتحلة.
- عناوين URL المسموح بها.
- الملفات التي يجب السماح بها.
- رسائل البريد الإلكتروني أو المجالات للمرسلين للسماح بها.

تصف هذه المقالة كيفية تكوين الإدخالات في قائمة الحظر/السماح بالمستأجر في مدخل Microsoft 365 Defender أو في PowerShell (Exchange Online PowerShell ل Microsoft 365 المؤسسات التي تضم علب بريد في Exchange Online؛ EOP PowerShell مستقل ل المؤسسات التي لا تتضمن Exchange Online علب البريد).

## <a name="what-do-you-need-to-know-before-you-begin"></a>ما الذي تحتاج إلى معرفته قبل البدء؟

- يمكنك فتح Microsoft 365 Defender في <https://security.microsoft.com>. انتقل مباشرة إلى صفحة **قوائم السماح/** الحظر للمستأجر، استخدم <https://security.microsoft.com/tenantAllowBlockList>.

- يمكنك تحديد الملفات باستخدام قيمة شارة SHA256 للملف. للعثور على قيمة شارة SHA256 لملف في Windows، يمكنك تشغيل الأمر التالي في موجه الأوامر:

  ```console
  certutil.exe -hashfile "<Path>\<Filename>" SHA256
  ```

  مثال على القيمة هي `768a813668695ef2483b2bde7cf5d1b2db0423a0d3e63e498f3ab6f2eb13ea3a`. قيم هاشته الإدراكية (pHash) غير معتمدة.

- يتم وصف قيم URL المتوفرة في بناء جملة [URL للمقسم قائمة السماح/](#url-syntax-for-the-tenant-allowblock-list) الحظر للمستأجر لاحقا في هذه المقالة.

- تسمح قائمة السماح/الحظر للمستأجر ب 500 إدخال كحد أقصى للمرسلين، و500 إدخالات لقائمة عناوين URL، و500 إدخال لتقعيد الملفات، و1024 إدخالا للانتحال (المرسلون المنتحلون).

- الحد الأقصى لعدد الأحرف لكل إدخال هو:
  - ها هوز الملف = 64
  - URL = 250

- يجب أن يكون الإدخال نشطا في غضون 30 دقيقة.

- بشكل افتراضي، ستنتهي صلاحية الإدخالات في قائمة السماح/الحظر للمستأجر بعد 30 يوما. يمكنك تحديد تاريخ أو تعيينه لكي لا تنتهي صلاحيته أبدا.

- للاتصال ب PowerShell Exchange Online، راجع الاتصال [إلى Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell). للاتصال ب EOP PowerShell مستقل، راجع الاتصال [Exchange Online Protection PowerShell](/powershell/exchange/connect-to-exchange-online-protection-powershell).

- يجب تعيين أذونات لك في مدخل Microsoft 365 Defender قبل أن تتمكن من تنفيذ الإجراءات في هذه المقالة:
  - **المرسلون، عناوين URL والملفات**:
    - لإضافة القيم وإزالتها من قائمة السماح/الحظر للمستأجر، يجب أن تكون عضوا في مجموعات دور إدارة المؤسسة أو مسؤول الأمان أو مشغل الأمان  أو يتم تعيين دور **Tenant AllowBlockList Manager**.
    - للوصول للقراءة فقط إلى قائمة السماح/الحظر للمستأجر، يجب أن تكون عضوا في مجموعات دور القارئ العام  أو قارئ الأمان.
  - **التهزاء**: إحدى التركيبات التالية:
    - **إدارة المؤسسة**
    - **مسؤول الأمان** <u>وتكوين</u> **العرض** فقط أو **إدارة المؤسسة لل طريقة العرض فقط**.

  لمزيد من المعلومات، راجع [الأذونات في Exchange Online](/exchange/permissions-exo/permissions-exo).

  > [!NOTE]
  >
  > - توفر إضافة مستخدمين إلى دور Azure Active Directory المناظر في مركز مسؤولي Microsoft 365 للمستخدمين الأذونات والأذونات المطلوبة للميزات الأخرى  في Microsoft 365. لمزيد من المعلومات، راجع [حول أدوار المسؤولين](../../admin/add-users/about-admin-roles.md).
  >
  > - توفر **أيضا مجموعة دور "** إدارة [المؤسسات Exchange Online](/Exchange/permissions-exo/permissions-exo#role-groups) طريقة العرض فقط" إمكانية الوصول للقراءة فقط إلى الميزة.

## <a name="configure-the-tenant-allowblock-list"></a>تكوين قائمة السماح/الحظر للمستأجر

### <a name="use-the-microsoft-365-defender-portal"></a>استخدام Microsoft 365 Defender المدخل

في مدخل Microsoft 365 Defender في <https://security.microsoft.com>،  \>  \> انتقل إلى & قواعد المخاطر قوائم المستأجر **السماح/** الحظر في **المقطع القواعد**. انتقل مباشرة إلى صفحة **قوائم السماح/** الحظر للمستأجر، استخدم <https://security.microsoft.com/tenantAllowBlockList>.

لإضافة كل الكتل، راجع [إضافة كتل في قائمة السماح/الحظر](manage-tenant-blocks.md) للمستأجر.

لإضافة كل السماح، راجع [إضافة السماح في قائمة السماح/الحظر](manage-tenant-allows.md) للمستأجر.

لتعديل كل الكتل والسماحات وإزالتها، راجع تعديل الإدخالات وإزالتها [في قائمة السماح/الحظر](modify-remove-entries-tenant-allow-block.md) للمستأجر.

### <a name="use-exchange-online-powershell-or-standalone-eop-powershell"></a>استخدام Exchange Online PowerShell أو EOP PowerShell مستقل

لإدارة كل عمليات السماح والحظر، راجع إضافة كتل في قائمة السماح [/](manage-tenant-blocks.md)الحظر للمستأجر، وإضافة السماح في قائمة السماح [/](manage-tenant-allows.md)الحظر للمستأجر، وتعديل الإدخالات وإزالتها في قائمة السماح [/الحظر للمستأجر](modify-remove-entries-tenant-allow-block.md).

## <a name="view-entries-in-the-tenant-allowblock-list"></a>عرض الإدخالات في قائمة السماح/الحظر للمستأجر

1. في مدخل Microsoft 365 Defender في <https://security.microsoft.com>،  \>  \> انتقل إلى & قواعد المخاطر قوائم المستأجر **السماح/** الحظر في **المقطع القواعد**. انتقل مباشرة إلى صفحة **قوائم السماح/** الحظر للمستأجر، استخدم <https://security.microsoft.com/tenantAllowBlockList>.

2. حدد علامة التبويب التي تريدها. تعتمد الأعمدة المتوفرة على علامة التبويب التي حددتها:

   - **المرسلون**:
     - **القيمة**: مجال المرسل أو عنوان البريد الإلكتروني.
     - **الإجراء**: القيمة **السماح** أو **الحظر**.
     - **تم التعديل بواسطة**
     - **تم التحديث الأخير**
     - **إزالة في**
     - **ملاحظات**
   - **عناوين URL**:
     - **القيمة**: عنوان URL.
     - **الإجراء**: القيمة **السماح** أو **الحظر**.
     - **تم التعديل بواسطة**
     - **تم التحديث الأخير**
     - **إزالة في**
     - **ملاحظات**
   - **الملفات**
     - **القيمة**: ها هي هاش الملف.
     - **الإجراء**: القيمة **السماح** أو **الحظر**.
     - **تم التعديل بواسطة**
     - **تم التحديث الأخير**
     - **إزالة في**
     - **ملاحظات**
   - **اانتحال**
     - **مستخدم منتحل**
     - **إرسال البنية الأساسية**
     - **منتحل:** القيمة **داخلي أو** **خارجي**.
     - **الإجراء**: كتلة **القيمة** أو **السماح**.

   يمكنك النقر فوق عنوان عمود للفرز بترتيب تصاعدي أو تنازلي.

   يمكنك النقر فوق **تجميع** ل تجميع النتائج. تعتمد القيم المتوفرة على علامة التبويب التي حددتها:

   - **المرسلون**: يمكنك تجميع النتائج حسب **الإجراء**.
   - **عناوين URL**: يمكنك تجميع النتائج حسب **الإجراء**.
   - **الملفات**: يمكنك تجميع النتائج حسب **الإجراء**.
   - **انتحال**: يمكنك تجميع النتائج **حسب نوع الإجراء** أو **انتحال**.

   انقر **فوق** بحث، وأدخل كل قيمة أو جزءا منها، ثم اضغط على ENTER للبحث عن قيمة معينة. عند الانتهاء، انقر فوق ![مسح أيقونة البحث.](../../media/m365-cc-sc-close-icon.png) **مسح البحث**.

   انقر **فوق تصفية** لتصفية النتائج. تعتمد القيم المتوفرة في **القائمة flyout** Filter التي تظهر على علامة التبويب التي حددتها:

   - **المرسلون**
     - **الإجراء**
     - **لا تنتهي صلاحيتها أبدا**
     - **تاريخ التحديث الأخير**
     - **إزالة في**
   - **عناوين URL**
     - **الإجراء**
     - **لا تنتهي صلاحيتها أبدا**
     - **تاريخ التحديث الأخير**
     - **إزالة في**
   - **الملفات**
     - **الإجراء**
     - **لا تنتهي صلاحيتها أبدا**
     - **تم التحديث الأخير**
     - **إزالة في**
   - **اانتحال**
     - **الإجراء**
     - **منتحل النوع**

   عند الانتهاء، انقر فوق **تطبيق**. لمسح عوامل التصفية الموجودة، انقر فوق **عامل التصفية**،  وفي القائمة من القائمة flyout التي تظهر، انقر فوق **مسح عوامل التصفية**.

4. عند الانتهاء، انقر فوق **إضافة**.

## <a name="view-sender-file-or-url-entries-in-the-tenant-allowblock-list"></a>عرض إدخالات المرسل أو الملف أو URL في قائمة السماح/الحظر للمستأجر

لعرض إدخالات المرسل أو الملف أو URL المحظورة في قائمة السماح/الحظر للمستأجر، استخدم بناء الجملة التالي:

```powershell
Get-TenantAllowBlockListItems -ListType <Sender | FileHash | URL> [-Entry <SenderValue | FileHashValue | URLValue>] [<-ExpirationDate Date | -NoExpiration>]
```

يرجع هذا المثال معلومات لقيمة تهاني الملف المحددة.

```powershell
Get-TenantAllowBlockListItems -ListType FileHash -Entry "9f86d081884c7d659a2feaa0c55ad015a3bf4f1b2b0b822cd15d6c15b0f00a08"
```

يرجع هذا المثال كافة عناوين URL المحظورة.

```powershell
Get-TenantAllowBlockListItems -ListType Url -Block
```

للحصول على معلومات مفصلة حول بناء الجملة والمعلمات، راجع [Get-TenantAllowBlockListItems](/powershell/module/exchange/get-tenantallowblocklistitems).

## <a name="view-spoofed-sender-entries"></a>عرض إدخالات المرسلين المنتحلين

لعرض إدخالات المرسلين المنتحلين في قائمة السماح/الحظر للمستأجر، استخدم بناء الجملة التالي:

```powershell
Get-TenantAllowBlockListSpoofItems [-Action <Allow | Block>] [-SpoofType <External | Internal>
```

يرجع هذا المثال كل إدخالات المرسلين المنتحلين في قائمة السماح/الحظر للمستأجر.

```powershell
Get-TenantAllowBlockListSpoofItems
```

يرجع هذا المثال كل إدخالات المرسلين المنتحلين المسموح بها داخليا.

```powershell
Get-TenantAllowBlockListSpoofItems -Action Allow -SpoofType Internal
```

يرجع هذا المثال كل إدخالات المرسلين المحظورين المحظورين التي تكون خارجية.

```powershell
Get-TenantAllowBlockListSpoofItems -Action Block -SpoofType External
```

للحصول على معلومات مفصلة حول بناء الجملة والمعلمات، راجع [Get-TenantAllowBlockListSpoofItems](/powershell/module/exchange/get-tenantallowblocklistspoofitems).

## <a name="url-syntax-for-the-tenant-allowblock-list"></a>بناء جملة URL لقائمة السماح/الحظر للمستأجر

- يتم السماح عناوين IPv4 و IPv6، ولكن منافذ TCP/UDP غير مسموحة.

- ملحقات اسم الملف غير مسموح بها (على سبيل المثال، test.pdf).

- Unicode غير معتمد، ولكن رمز Punycode معتمد.

- يتم السماح با أسماء المضيفين إذا كانت كل العبارات التالية صحيحة:
  - يحتوي اسم المضيف على فترة زمنية.
  - يوجد حرف واحد على الأقل إلى يسار الفترة الزمنية.
  - يوجد حرفان على الأقل إلى يمين الفترة الزمنية.

  على سبيل المثال `t.co` ، مسموح به؛ `.com` أو `contoso.` غير مسموح به.

- لا يتم ضمنيا السماح للمواد الفرعية.

  على سبيل المثال، `contoso.com` لا يتضمن `contoso.com/a`.

- يتم السماح ب أحرف البدل (*) في السيناريوهات التالية:

  - يجب أن تكون أحرف البدل اليسرى متبوعة بفترة لتحديد اسم فرعي.

    على سبيل المثال `*.contoso.com` ، مسموح؛ `*contoso.com` غير مسموح به.

  - يجب أن يتبع أحرف البدل اليمنى الشرطة المائلة للأمام (/) لتحديد مسار.

    على سبيل المثال `contoso.com/*` ، مسموح به؛ `contoso.com*` أو `contoso.com/ab*` غير مسموح به.

  - `*.com*` غير صالح (ليس مجالا قابلا للحل ولا يتبع أحرف البدل الصحيحة الشرطة المائلة للأمام).

  - أحرف البدل غير مسموح بها في عناوين IP.

- يتوفر حرف التيلد (~) في السيناريوهات التالية:

  - يشير التيلde الأيسر إلى مجال وكل المجالات الفرعية.

    على سبيل المثال `~contoso.com` ، يتضمن و `contoso.com` `*.contoso.com`.

- ستفشل إدخالات URL التي تحتوي على بروتوكولات ( `http://`على سبيل المثال، أو `https://`أو `ftp://`أو ) لأن إدخالات URL تنطبق على كل البروتوكولات.

- اسم المستخدم أو كلمة المرور غير معتمدة أو مطلوبة.

- علامات الاقتباس (' أو ") هي أحرف غير صالحة.

- يجب أن يتضمن عنوان URL كل عمليات إعادة التوجيه قدر الإمكان.

### <a name="url-entry-scenarios"></a>سيناريوهات إدخال URL

يتم وصف إدخالات URL الصحيحة ونتائجها في الأقسام التالية.

#### <a name="scenario-no-wildcards"></a>السيناريو: لا توجد أحرف بدل

**الإدخال**: `contoso.com`

- **السماح باحتواء**: contoso.com

- **السماح غير متطابق**:

  - abc-contoso.com
  - contoso.com/a
  - payroll.contoso.com
  - test.com/contoso.com
  - test.com/q=contoso.com
  - www.contoso.com
  - www.contoso.com/q=a@contoso.com

- **مطابقة الحظر**:

  - contoso.com
  - contoso.com/a
  - payroll.contoso.com
  - test.com/contoso.com
  - test.com/q=contoso.com
  - www.contoso.com
  - www.contoso.com/q=a@contoso.com

- **الحظر غير متطابق**: abc-contoso.com

#### <a name="scenario-left-wildcard-subdomain"></a>السيناريو: أحرف البدل اليسرى (فرعي)

**الإدخال**: `*.contoso.com`

- **السماح باحتواء** مطابقة **وحظر متطابق**:

  - www.contoso.com
  - xyz.abc.contoso.com

- **السماح غير متطابق وحظر** **غير متطابق**:

  - 123contoso.com
  - contoso.com
  - test.com/contoso.com
  - www.contoso.com/abc

#### <a name="scenario-right-wildcard-at-top-of-path"></a>السيناريو: أحرف البدل اليمنى في أعلى المسار

**الإدخال**: `contoso.com/a/*`

- **السماح باحتواء** مطابقة **وحظر متطابق**:

  - contoso.com/a/b
  - contoso.com/a/b/c
  - contoso.com/a/?q=joe@t.com

- **السماح غير متطابق وحظر** **غير متطابق**:

  - contoso.com
  - contoso.com/a
  - www.contoso.com
  - www.contoso.com/q=a@contoso.com

#### <a name="scenario-left-tilde"></a>السيناريو: التيلد الأيسر

**الإدخال**: `~contoso.com`

- **السماح باحتواء** مطابقة **وحظر متطابق**:

  - contoso.com
  - www.contoso.com
  - xyz.abc.contoso.com

- **السماح غير متطابق وحظر** **غير متطابق**:

  - 123contoso.com
  - contoso.com/abc
  - www.contoso.com/abc

#### <a name="scenario-right-wildcard-suffix"></a>السيناريو: لاحقة أحرف البدل اليمنى

**الإدخال**: `contoso.com/*`

- **السماح باحتواء** مطابقة **وحظر متطابق**:

  - contoso.com/?q=whatever@fabrikam.com
  - contoso.com/a
  - contoso.com/a/b/c
  - contoso.com/ab
  - contoso.com/b
  - contoso.com/b/a/c
  - contoso.com/ba

- **السماح غير متطابق وحظر** غير **متطابق**: contoso.com

#### <a name="scenario-left-wildcard-subdomain-and-right-wildcard-suffix"></a>السيناريو: البدل الأيسر و اللاحقة اليمنى ل أحرف البدل

**الإدخال**: `*.contoso.com/*`

- **السماح باحتواء** مطابقة **وحظر متطابق**:

  - abc.contoso.com/ab
  - abc.xyz.contoso.com/a/b/c
  - www.contoso.com/a
  - www.contoso.com/b/a/c
  - xyz.contoso.com/ba

- **السماح غير متطابق وحظر** **غير متطابق**: contoso.com/b

#### <a name="scenario-left-and-right-tilde"></a>السيناريو: التيل إلى اليسار واليمين

**الإدخال**: `~contoso.com~`

- **السماح باحتواء** مطابقة **وحظر متطابق**:

  - contoso.com
  - contoso.com/a
  - www.contoso.com
  - www.contoso.com/b
  - xyz.abc.contoso.com

- **السماح غير متطابق وحظر** **غير متطابق**:

  - 123contoso.com
  - contoso.org

#### <a name="scenario-ip-address"></a>السيناريو: عنوان IP

**الإدخال**: `1.2.3.4`

- **السماح** **باحتواء مطابقة وحظر**: 1.2.3.4

- **السماح غير متطابق وحظر** **غير متطابق**:

  - 1.2.3.4/a
  - 11.2.3.4/a

#### <a name="ip-address-with-right-wildcard"></a>عنوان IP مع أحرف البدل اليمنى

**الإدخال**: `1.2.3.4/*`

- **السماح باحتواء** مطابقة **وحظر متطابق**:

  - 1.2.3.4/b
  - 1.2.3.4/baaaa

### <a name="examples-of-invalid-entries"></a>أمثلة على الإدخالات غير الصالحة

الإدخالات التالية غير صالحة:

- **قيم المجال المفقودة أو غير الصالحة**:

  - contoso
  - \*contoso.\*
  - \*.com
  - \*.pdf

- **حرف البدل على نص أو بدون أحرف تباعد**:

  - \*contoso.com
  - contoso.com\*
  - \*1.2.3.4
  - 1.2.3.4\*
  - contoso.com/a\*
  - contoso.com/ab\*

- **عناوين IP التي بها منافذ**:

  - contoso.com:443
  - abc.contoso.com:25

- **أحرف البدل غير الوصفية**:

  - \*
  - \*.\*

- **أحرف البدل المتوسطة**:

  - conto\* so.com
  - conto~so.com

- **أحرف البدل المزدوجة**

  - contoso.com/\*\*
  - contoso.com/\*/\*

## <a name="domain-pair-syntax-for-spoofed-sender-entries-in-the-tenant-allowblock-list"></a>بناء جملة زوج المجال إدخالات المرسلين المنتحلين في قائمة السماح/الحظر للمستأجر

يستخدم زوج مجال لمرسل منتحل في قائمة السماح/الحظر للمستأجر بناء الجملة التالي: `<Spoofed user>, <Sending infrastructure>`.

- **مستخدم منتحل**: تتضمن هذه القيمة عنوان البريد الإلكتروني للمستخدم المزحل المعروض في المربع من في عملاء البريد الإلكتروني. يعرف هذا العنوان أيضا باسم `5322.From` العنوان. تتضمن القيم الصالحة:
  - عنوان بريد إلكتروني فردي (على سبيل المثال، chris@contoso.com).
  - مجال بريد إلكتروني (على سبيل المثال، contoso.com).
  - حرف البدل (على سبيل المثال، \*).

- **إرسال البنية** الأساسية: تشير هذه القيمة إلى مصدر الرسائل من المستخدم المهزوف. تتضمن القيم الصالحة:
  - المجال الذي تم العثور عليه في بحث DNS عكسي (سجل PTR)  عنوان IP الخاص بخادم البريد الإلكتروني المصدر (على سبيل المثال، fabrikam.com).
  - إذا لم يكن عنوان IP المصدر له سجل PTR \<source IP\>، يتم تعريف البنية الأساسية المرسلة على أنها /24 (على سبيل المثال، 192.168.100.100/24).

فيما يلي بعض الأمثلة عن أزواج مجالات صالحة لتحديد المرسلين المزحلين:

- `contoso.com, 192.168.100.100/24`
- `chris@contoso.com, fabrikam.com`
- `*, contoso.net`

الحد الأقصى لعدد إدخالات المرسلين المنتحلين هو 1000.

لا تسمح إضافة زوج مجال إلا بالجمع بين  المستخدم المنتحل والبنية الأساسية المرسلة  أو تمنعها. ولا يسمح بالبريد الإلكتروني الوارد من المستخدم المهزوف من أي مصدر، كما لا يسمح بإرسال البريد الإلكتروني من مصدر البنية الأساسية المرسلة لأي مستخدم منتحل. 

على سبيل المثال، يمكنك إضافة إدخال السماح لزوج المجال التالي:

- **المجال**: gmail.com
- **البنية الأساسية**: tms.mx.com

يسمح فقط بالرسائل *الواردة* من هذا المجال وزوج البنية الأساسية المرسلة للانتحال. المرسلون الآخرين الذين يحاولون انتحال gmail.com غير مسموح. يتم التحقق من الرسائل الواردة من المرسلين في مجالات أخرى tms.mx.com بواسطة المعلومات المنتحلة.
