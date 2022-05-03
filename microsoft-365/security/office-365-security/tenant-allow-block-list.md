---
title: إدارة السمحات والكتل في قائمة السماح/الحظر للمستأجر
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
description: يمكن للمسؤولين معرفة كيفية إدارة الأذونات والكتل في قائمة السماح/الحظر للمستأجر في مدخل الأمان.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: a067672a013f3e0ed7b9009604f8a4fe000ea47f
ms.sourcegitcommit: f30616b90b382409f53a056b7a6c8be078e6866f
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 05/03/2022
ms.locfileid: "65172818"
---
# <a name="manage-the-tenant-allowblock-list"></a>إدارة قائمة السماح/الحظر للمستأجر

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**ينطبق على**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [خطة 1 وخطة 2 من Microsoft Defender لـ Office 365](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

في المؤسسات Microsoft 365 التي لها علب بريد في مؤسسات Exchange Online Protection Exchange Online أو مستقلة (EOP) بدون علب بريد Exchange Online، قد لا توافق على قرار تصفية EOP. على سبيل المثال، قد يتم وضع علامة على رسالة جيدة على أنها سيئة (إيجابية خاطئة)، أو قد يتم السماح برسالة سيئة من خلال (سلبي خطأ).

توفر لك قائمة السماح/الحظر للمستأجر في مدخل Microsoft 365 Defender طريقة لتجاوز أحكام تصفية Microsoft 365 يدويا. يتم استخدام قائمة السماح/الحظر للمستأجر أثناء تدفق البريد للرسائل الواردة (لا ينطبق على الرسائل داخل المؤسسة) وفي وقت نقرات المستخدم. يمكنك تحديد أنواع التجاوزات التالية:

- عناوين URL المراد حظرها.
- الملفات المطلوب حظرها.
- رسائل البريد الإلكتروني أو المجالات المراد حظرها من قبل المرسل.
- المرسلون المخادحون للسماح أو الحظر. إذا تجاوزت قرار السماح أو الحظر في [رؤى التحليل الذكي المخادعة](learn-about-spoof-intelligence.md)، يصبح المرسل المخادع اسما يدويا أو حظر الإدخال الذي يظهر فقط على علامة تبويب **تزييف** الهوية في قائمة السماح/الحظر للمستأجر. يمكنك أيضا إنشاء إدخالات السماح أو الحظر يدويا للمرسلين المخادعة هنا قبل اكتشافهم بواسطة التحليل الذكي المخادعة.
- عناوين URL المطلوب السماح بها.
- الملفات المطلوب السماح بها.
- رسائل البريد الإلكتروني أو المجالات التي يجب السماح بها للمرسل.

تصف هذه المقالة كيفية تكوين الإدخالات في قائمة السماح/الحظر للمستأجر في مدخل Microsoft 365 Defender أو في PowerShell (Exchange Online PowerShell للمؤسسات Microsoft 365 مع علب البريد في Exchange Online؛ EOP PowerShell مستقل للمؤسسات دون Exchange Online علب البريد).

## <a name="what-do-you-need-to-know-before-you-begin"></a>ما الذي تحتاج إلى معرفته قبل البدء؟

- يمكنك فتح مدخل Microsoft 365 Defender في <https://security.microsoft.com>. للانتقال مباشرة إلى صفحة **قوائم السماح/الحظر للمستأجر** ، استخدم <https://security.microsoft.com/tenantAllowBlockList>.

- يمكنك تحديد الملفات باستخدام قيمة تجزئة SHA256 للملف. للبحث عن قيمة تجزئة SHA256 لملف في Windows، قم بتشغيل الأمر التالي في موجه الأوامر:

  ```console
  certutil.exe -hashfile "<Path>\<Filename>" SHA256
  ```

  قيمة المثال هي `768a813668695ef2483b2bde7cf5d1b2db0423a0d3e63e498f3ab6f2eb13ea3a`. قيم التجزئة المقبولة (pHash) غير معتمدة.

- يتم وصف قيم URL المتوفرة في [بناء جملة URL لمقطع السماح بالمستأجر/قائمة الحظر](#url-syntax-for-the-tenant-allowblock-list) لاحقا في هذه المقالة.

- تسمح قائمة السماح/الحظر للمستأجر ب 500 إدخال كحد أقصى للمرسلين و500 إدخال لعناوين URL و500 إدخال لتجزئة الملفات و1024 إدخالا للانتحال (المرسلين المخادعة).

- الحد الأقصى لعدد الأحرف لكل إدخال هو:
  - تجزئة الملف = 64
  - URL = 250

- يجب أن يكون الإدخال نشطا في غضون 30 دقيقة.

- بشكل افتراضي، ستنتهي صلاحية الإدخالات في قائمة السماح/الحظر للمستأجر بعد 30 يوما. يمكنك تحديد تاريخ أو تعيينه على ألا تنتهي صلاحيته أبدا.

- للاتصال Exchange Online PowerShell، راجع [الاتصال إلى Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell). للاتصال ب EOP PowerShell مستقل، راجع [الاتصال إلى Exchange Online Protection PowerShell](/powershell/exchange/connect-to-exchange-online-protection-powershell).

- يجب تعيين أذونات لك في Exchange Online قبل أن تتمكن من تنفيذ الإجراءات الواردة في هذه المقالة:
  - **المرسلون وعناوين URL والملفات**:
    - لإضافة قيم وإزالتها من قائمة السماح/الحظر للمستأجر، يجب أن تكون عضوا في
      - **إدارة المؤسسة** أو مجموعة دور **مسؤول الأمان** (**دور مسؤول الأمان**)
      - مجموعة دور **عامل تشغيل الأمان** (**Tenant AllowBlockList Manager**).
    - للوصول للقراءة فقط إلى قائمة السماح/الحظر للمستأجر، يجب أن تكون عضوا في
      - مجموعة دور **القارئ العمومي**
      - مجموعة دور **قارئ الأمان**
  - **الانتحال**: إحدى المجموعات التالية:
    - **إدارة المؤسسة**
    - **مسؤول الأمان** <u>وتكوين</u> **العرض فقط** أو **إدارة المؤسسة للعرض فقط**.

  لمزيد من المعلومات، راجع [الأذونات في Exchange Online](/exchange/permissions-exo/permissions-exo).

  > [!NOTE]
  >
  > - إضافة مستخدمين إلى دور Azure Active Directory المقابل في مركز مسؤولي Microsoft 365 يمنح المستخدمين الأذونات *والأذونات* المطلوبة للميزات الأخرى في Microsoft 365. لمزيد من المعلومات، راجع [حول أدوار المسؤولين](../../admin/add-users/about-admin-roles.md).
  >
  > - كما توفر مجموعة دور **إدارة المؤسسة للعرض فقط** في [Exchange Online](/Exchange/permissions-exo/permissions-exo#role-groups) إمكانية الوصول للقراءة فقط إلى الميزة.

## <a name="configure-the-tenant-allowblock-list"></a>تكوين قائمة السماح/الحظر للمستأجر

### <a name="use-the-microsoft-365-defender-portal"></a>استخدام مدخل Microsoft 365 Defender

في مدخل Microsoft 365 Defender في <https://security.microsoft.com>، انتقل إلى **نهج & قواعد قواعد** \> **التهديدات** **لقوائم السماح/الحظر** الخاصة بنهج المخاطر \> في قسم **القواعد**. للانتقال مباشرة إلى صفحة **قوائم السماح/الحظر للمستأجر** ، استخدم <https://security.microsoft.com/tenantAllowBlockList>.

لإضافة كافة الكتل، راجع [إضافة كتل في قائمة السماح/الحظر للمستأجر](manage-tenant-blocks.md).

لإضافة كل السماحات، راجع ["إضافة السماح" في قائمة السماح/الحظر للمستأجر](manage-tenant-allows.md).

لتعديل كافة الكتل والسماح وإزالتها، راجع [تعديل الإدخالات وإزالتها في قائمة السماح/الحظر للمستأجر](modify-remove-entries-tenant-allow-block.md).

### <a name="use-exchange-online-powershell-or-standalone-eop-powershell"></a>استخدام Exchange Online PowerShell أو EOP PowerShell المستقل

لإدارة كافة اللسماحات والكتل، راجع [إضافة كتل في قائمة السماح/الحظر للمستأجر](manage-tenant-blocks.md)، [وإضافة السماح في قائمة السماح/الحظر للمستأجر](manage-tenant-allows.md)، [وتعديل الإدخالات وإزالتها في قائمة السماح/الحظر للمستأجر](modify-remove-entries-tenant-allow-block.md).

## <a name="view-entries-in-the-tenant-allowblock-list"></a>عرض الإدخالات في قائمة السماح/الحظر للمستأجر

1. في مدخل Microsoft 365 Defender في <https://security.microsoft.com>، انتقل إلى **نهج & قواعد قواعد** \> **التهديدات** **لقوائم السماح/الحظر** الخاصة بنهج المخاطر \> في قسم **القواعد**. للانتقال مباشرة إلى صفحة **قوائم السماح/الحظر للمستأجر** ، استخدم <https://security.microsoft.com/tenantAllowBlockList>.

2. حدد علامة التبويب التي تريدها. تعتمد الأعمدة المتوفرة على علامة التبويب التي حددتها:

   - **المرسلون**:
     - **القيمة**: مجال المرسل أو عنوان البريد الإلكتروني.
     - **الإجراء**: القيمة **السماح** أو **الحظر**.
     - **تم التعديل بواسطة**
     - **تاريخ التحديث الأخير**
     - **إزالة في**
     - **ملاحظات**
   - **عناوين URL**:
     - **القيمة**: عنوان URL.
     - **الإجراء**: القيمة **السماح** أو **الحظر**.
     - **تم التعديل بواسطة**
     - **تاريخ التحديث الأخير**
     - **إزالة في**
     - **ملاحظات**
   - **الملفات**
     - **القيمة**: تجزئة الملف.
     - **الإجراء**: القيمة **السماح** أو **الحظر**.
     - **تم التعديل بواسطة**
     - **تاريخ التحديث الأخير**
     - **إزالة في**
     - **ملاحظات**
   - **التحايل**
     - **مستخدم منتحل**
     - **إرسال البنية الأساسية**
     - **نوع الانتحال**: القيمة **الداخلية** أو **الخارجية**.
     - **الإجراء**: **كتلة** القيمة أو **السماح**.

   يمكنك النقر فوق عنوان عمود للفرز بترتيب تصاعدي أو تنازلي.

   يمكنك النقر فوق **"تجميع** " لتجميع النتائج. تعتمد القيم المتوفرة على علامة التبويب التي حددتها:

   - **المرسلون**: يمكنك تجميع النتائج حسب **الإجراء**.
   - **عناوين URL**: يمكنك تجميع النتائج حسب **الإجراء**.
   - **الملفات**: يمكنك تجميع النتائج حسب **الإجراء**.
   - **تزييف هوية**: يمكنك تجميع النتائج حسب **نوع الإجراء** أو **الانتحال**.

   انقر فوق **"بحث**"، وأدخل كل قيمة أو جزء منها، ثم اضغط على ENTER للعثور على قيمة معينة. عند الانتهاء، انقر فوق ![أيقونة "مسح البحث".](../../media/m365-cc-sc-close-icon.png) **مسح البحث**.

   انقر فوق **"تصفية** " لتصفية النتائج. تعتمد القيم المتوفرة في القائمة المنبثقة " **تصفية"** التي تظهر على علامة التبويب التي حددتها:

   - **المرسلين**
     - **العمل**
     - **عدم انتهاء الصلاحية مطلقا**
     - **تاريخ التحديث الأخير**
     - **إزالة في**
   - **عناوين url**
     - **العمل**
     - **عدم انتهاء الصلاحية مطلقا**
     - **تاريخ التحديث الأخير**
     - **إزالة في**
   - **الملفات**
     - **العمل**
     - **عدم انتهاء الصلاحية مطلقا**
     - **تاريخ التحديث الأخير**
     - **إزالة في**
   - **التحايل**
     - **العمل**
     - **نوع تزييف هوية**

   عند الانتهاء، انقر فوق **"تطبيق**". لمسح عوامل التصفية الموجودة، انقر فوق **"تصفية**"، وفي القائمة المنبثقة " **تصفية** " التي تظهر، انقر فوق **"مسح عوامل التصفية**".

3. عند الانتهاء، انقر فوق **"إضافة**".

## <a name="view-sender-file-or-url-entries-in-the-tenant-allowblock-list"></a>عرض إدخالات المرسل أو الملف أو URL في قائمة السماح/الحظر للمستأجر

لعرض إدخالات مرسل الحظر أو الملف أو URL في قائمة السماح/الحظر للمستأجر، استخدم بناء الجملة التالي:

```powershell
Get-TenantAllowBlockListItems -ListType <Sender | FileHash | URL> [-Entry <SenderValue | FileHashValue | URLValue>] [<-ExpirationDate Date | -NoExpiration>]
```

يقوم هذا المثال بإرجاع معلومات لقيمة تجزئة الملف المحددة.

```powershell
Get-TenantAllowBlockListItems -ListType FileHash -Entry "9f86d081884c7d659a2feaa0c55ad015a3bf4f1b2b0b822cd15d6c15b0f00a08"
```

يرجع هذا المثال كافة عناوين URL المحظورة.

```powershell
Get-TenantAllowBlockListItems -ListType Url -Block
```

للحصول على معلومات مفصلة حول بناء الجملة والمعلمة، راجع [Get-TenantAllowBlockListItems](/powershell/module/exchange/get-tenantallowblocklistitems).

## <a name="view-spoofed-sender-entries"></a>عرض إدخالات المرسلين المخادعة

لعرض إدخالات المرسلين المخادعة في قائمة السماح/الحظر للمستأجر، استخدم بناء الجملة التالي:

```powershell
Get-TenantAllowBlockListSpoofItems [-Action <Allow | Block>] [-SpoofType <External | Internal>
```

يقوم هذا المثال بإرجاع كافة إدخالات المرسلين المخادعة في قائمة السماح/الحظر للمستأجر.

```powershell
Get-TenantAllowBlockListSpoofItems
```

يقوم هذا المثال بإرجاع كافة إدخالات المرسلين المخادعة المسموح بها والمضمنة.

```powershell
Get-TenantAllowBlockListSpoofItems -Action Allow -SpoofType Internal
```

يقوم هذا المثال بإرجاع كافة إدخالات المرسلين المخادعة المحظورة الخارجية.

```powershell
Get-TenantAllowBlockListSpoofItems -Action Block -SpoofType External
```

للحصول على معلومات مفصلة حول بناء الجملة والمعلمة، راجع [Get-TenantAllowBlockListSpoofItems](/powershell/module/exchange/get-tenantallowblocklistspoofitems).

## <a name="url-syntax-for-the-tenant-allowblock-list"></a>بناء جملة URL لقائمة السماح/الحظر للمستأجر

- يسمح بعناوين IPv4 وIPv6، ولكن منافذ TCP/UDP غير مسموحة.

- ملحقات اسم الملف غير مسموح بها (على سبيل المثال، test.pdf).

- Unicode غير معتمد، ولكن Punycode هو.

- يسمح بأسماء المضيفين إذا كانت كل العبارات التالية صحيحة:
  - يحتوي اسم المضيف على نقطة.
  - يوجد حرف واحد على الأقل إلى يسار الفترة.
  - يوجد حرفان على الأقل إلى يمين الفترة الزمنية.

  على سبيل المثال، `t.co` مسموح به؛ `.com` أو `contoso.` غير مسموح به.

- لا يتم إدراج المسارات الفرعية للأذونات.

  على سبيل المثال، `contoso.com` لا يتضمن `contoso.com/a`.

- يسمح بأحرف البدل (*) في السيناريوهات التالية:

  - يجب أن يتبع حرف بدل أيسر فترة لتحديد مجال فرعي.

    على سبيل المثال، `*.contoso.com` مسموح به؛ `*contoso.com` غير مسموح به.

  - يجب أن يتبع حرف البدل الأيمن شرطة مائلة للأمام (/) لتحديد مسار.

    على سبيل المثال، `contoso.com/*` مسموح به؛ `contoso.com*` أو `contoso.com/ab*` غير مسموح به.

  - `*.com*` غير صحيح (ليس مجالا قابلا للحل ولا يتبع حرف البدل الصحيح شرطة مائلة للأمام).

  - لا يسمح بأحرف البدل في عناوين IP.

- يتوفر حرف التلدة (~) في السيناريوهات التالية:

  - يشير التلدة اليسرى إلى مجال وكافة المجالات الفرعية.

    على سبيل المثال `~contoso.com` يتضمن `contoso.com` و `*.contoso.com`.

- ستفشل إدخالات URL التي تحتوي على بروتوكولات (على سبيل المثال، `http://`أو `https://`، أو `ftp://`) لأن إدخالات URL تنطبق على كافة البروتوكولات.

- اسم المستخدم أو كلمة المرور غير معتمدة أو مطلوبة.

- علامات الاقتباس (' أو ") عبارة عن أحرف غير صحيحة.

- يجب أن يتضمن URL كافة عمليات إعادة التوجيه حيثما أمكن ذلك.

### <a name="url-entry-scenarios"></a>سيناريوهات إدخال URL

يتم وصف إدخالات URL الصحيحة ونتائجها في المقاطع التالية.

#### <a name="scenario-no-wildcards"></a>السيناريو: لا توجد أحرف بدل

**الإدخال**: `contoso.com`

- **السماح بالتطابق**: contoso.com

- **السماح غير متطابق**:

  - abc-contoso.com
  - contoso.com/a
  - payroll.contoso.com
  - test.com/contoso.com
  - test.com/q=contoso.com
  - www.contoso.com
  - www.contoso.com/q=a@contoso.com

- **مطابقة الكتلة**:

  - contoso.com
  - contoso.com/a
  - payroll.contoso.com
  - test.com/contoso.com
  - test.com/q=contoso.com
  - www.contoso.com
  - www.contoso.com/q=a@contoso.com

- **الكتلة غير متطابقة**: abc-contoso.com

#### <a name="scenario-left-wildcard-subdomain"></a>السيناريو: حرف بدل أيسر (مجال فرعي)

**الإدخال**: `*.contoso.com`

- **السماح بالتطابق** **وتطابق الكتلة**:

  - www.contoso.com
  - xyz.abc.contoso.com

- **السماح غير متطابق** **والكتلة غير متطابقة**:

  - 123contoso.com
  - contoso.com
  - test.com/contoso.com
  - www.contoso.com/abc

#### <a name="scenario-right-wildcard-at-top-of-path"></a>السيناريو: حرف بدل أيمن في أعلى المسار

**الإدخال**: `contoso.com/a/*`

- **السماح بالتطابق** **وتطابق الكتلة**:

  - contoso.com/a/b
  - contoso.com/a/b/c
  - contoso.com/a/?q=joe@t.com

- **السماح غير متطابق** **والكتلة غير متطابقة**:

  - contoso.com
  - contoso.com/a
  - www.contoso.com
  - www.contoso.com/q=a@contoso.com

#### <a name="scenario-left-tilde"></a>السيناريو: التلدة اليسرى

**الإدخال**: `~contoso.com`

- **السماح بالتطابق** **وتطابق الكتلة**:

  - contoso.com
  - www.contoso.com
  - xyz.abc.contoso.com

- **السماح غير متطابق** **والكتلة غير متطابقة**:

  - 123contoso.com
  - contoso.com/abc
  - www.contoso.com/abc

#### <a name="scenario-right-wildcard-suffix"></a>السيناريو: لاحقة حرف بدل أيمن

**الإدخال**: `contoso.com/*`

- **السماح بالتطابق** **وتطابق الكتلة**:

  - contoso.com/?q=whatever@fabrikam.com
  - contoso.com/a
  - contoso.com/a/b/c
  - contoso.com/ab
  - contoso.com/b
  - contoso.com/b/a/c
  - contoso.com/ba

- **السماح غير متطابق** **والحظر غير متطابق**: contoso.com

#### <a name="scenario-left-wildcard-subdomain-and-right-wildcard-suffix"></a>السيناريو: المجال الفرعي لحرف البدل الأيسر ولاحقة حرف البدل الأيمن

**الإدخال**: `*.contoso.com/*`

- **السماح بالتطابق** **وتطابق الكتلة**:

  - abc.contoso.com/ab
  - abc.xyz.contoso.com/a/b/c
  - www.contoso.com/a
  - www.contoso.com/b/a/c
  - xyz.contoso.com/ba

- **السماح غير متطابق** **والحظر غير متطابق**: contoso.com/b

#### <a name="scenario-left-and-right-tilde"></a>السيناريو: التلدة اليمنى واليسرى

**الإدخال**: `~contoso.com~`

- **السماح بالتطابق** **وتطابق الكتلة**:

  - contoso.com
  - contoso.com/a
  - www.contoso.com
  - www.contoso.com/b
  - xyz.abc.contoso.com

- **السماح غير متطابق** **والكتلة غير متطابقة**:

  - 123contoso.com
  - contoso.org

#### <a name="scenario-ip-address"></a>السيناريو: عنوان IP

**الإدخال**: `1.2.3.4`

- **السماح بالتطابق** **وتطابق الكتلة**: 1.2.3.4

- **السماح غير متطابق** **والكتلة غير متطابقة**:

  - 1.2.3.4/a
  - 11.2.3.4/a

#### <a name="ip-address-with-right-wildcard"></a>عنوان IP مع حرف بدل أيمن

**الإدخال**: `1.2.3.4/*`

- **السماح بالتطابق** **وتطابق الكتلة**:

  - 1.2.3.4/b
  - 1.2.3.4/baaaa

### <a name="examples-of-invalid-entries"></a>أمثلة للإدخالات غير الصالحة

الإدخالات التالية غير صحيحة:

- **قيم المجال المفقودة أو غير الصالحة**:

  - Contoso
  - \*contoso.\*
  - \*.com
  - \*.pdf

- **حرف بدل على نص أو بدون أحرف تباعد**:

  - \*contoso.com
  - contoso.com\*
  - \*1.2.3.4
  - 1.2.3.4\*
  - contoso.com/a\*
  - contoso.com/ab\*

- **عناوين IP ذات المنافذ**:

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

## <a name="domain-pair-syntax-for-spoofed-sender-entries-in-the-tenant-allowblock-list"></a>بناء جملة زوج المجال لإدخالات المرسلين المخادعة في قائمة السماح/الحظر للمستأجر

يستخدم زوج المجال لمرسل منتحل في قائمة السماح/الحظر للمستأجر بناء الجملة التالي: `<Spoofed user>, <Sending infrastructure>`.

- **المستخدم المخادعة**: تتضمن هذه القيمة عنوان البريد الإلكتروني للمستخدم المخادعة الذي يتم عرضه في المربع **"من** " في عملاء البريد الإلكتروني. يعرف هذا العنوان أيضا بالعنوان `5322.From` . تتضمن القيم الصالحة ما يلي:
  - عنوان بريد إلكتروني فردي (على سبيل المثال، chris@contoso.com).
  - مجال بريد إلكتروني (على سبيل المثال، contoso.com).
  - حرف البدل (على سبيل المثال، \*).

- **إرسال البنية الأساسية**: تشير هذه القيمة إلى مصدر الرسائل من المستخدم المخادعة. تتضمن القيم الصالحة ما يلي:
  - المجال الموجود في بحث DNS العكسي (سجل PTR) لعنوان IP لخادم البريد الإلكتروني المصدر (على سبيل المثال، fabrikam.com).
  - إذا لم يكن لعنوان IP المصدر سجل PTR، فسيتم تعريف البنية الأساسية للإرسال على أنها \<source IP\>/24 (على سبيل المثال، 192.168.100.100/24).

فيما يلي بعض الأمثلة على أزواج المجالات الصالحة لتحديد المرسلين المخادعة:

- `contoso.com, 192.168.100.100/24`
- `chris@contoso.com, fabrikam.com`
- `*, contoso.net`

الحد الأقصى لعدد إدخالات المرسلين المخادعة هو 1000.

إضافة زوج مجال يسمح فقط أو يحظر *الجمع بين* المستخدم المخادعة *والبنية* الأساسية لإرسال. ولا يسمح بالبريد الإلكتروني من المستخدم المخادعة من أي مصدر، كما أنه لا يسمح بالبريد الإلكتروني من مصدر البنية الأساسية المرسلة لأي مستخدم منتحل.

على سبيل المثال، يمكنك إضافة إدخال السماح لزوج المجال التالي:

- **المجال**: gmail.com
- **البنية الأساسية**: tms.mx.com

يسمح فقط للرسائل الواردة من هذا المجال *وإرسال* زوج البنية الأساسية بالانتحال. لا يسمح للمرسلين الآخرين الذين يحاولون تزييف gmail.com. يتم التحقق من الرسائل الواردة من المرسلين في مجالات أخرى تنشأ من tms.mx.com بواسطة التحليل الذكي للانتحال.
