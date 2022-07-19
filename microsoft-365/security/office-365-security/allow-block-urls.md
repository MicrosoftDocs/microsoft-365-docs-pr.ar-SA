---
title: السماح بعناوين URL أو حظرها باستخدام قائمة السماح/الحظر للمستأجر
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: how-to
ms.localizationpriority: medium
search.appverid:
- MET150manage-tenant-allows.md
ms.collection:
- M365-security-compliance
description: يمكن للمسؤولين معرفة كيفية السماح بعناوين URL أو حظرها في قائمة السماح/الحظر للمستأجر في مدخل الأمان.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 69d9b4725e0a2c57dac8bb711655b9e0ff02e3e5
ms.sourcegitcommit: 7df8adc9e67ab65e413d7ea7bb0dcb9fd2da1a11
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 06/21/2022
ms.locfileid: "66857416"
---
# <a name="allow-or-block-urls-using-the-tenant-allowblock-list"></a>السماح بعناوين URL أو حظرها باستخدام قائمة السماح/الحظر للمستأجر

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**ينطبق على**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [خطة 1 وخطة 2 من Microsoft Defender لـ Office 365](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

يمكنك استخدام مدخل Microsoft 365 Defender أو PowerShell للسماح بعناوين URL أو حظرها في قائمة السماح/الحظر للمستأجر.

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

  - يجب أن يتبع حرف بدل أيسر فترة لتحديد مجال فرعي. (ينطبق فقط على الكتل)

    على سبيل المثال، `*.contoso.com` مسموح به؛ `*contoso.com` غير مسموح به.

  - يجب أن يتبع حرف البدل الأيمن شرطة مائلة للأمام (/) لتحديد مسار.

    على سبيل المثال، `contoso.com/*` مسموح به؛ `contoso.com*` أو `contoso.com/ab*` غير مسموح به.

  - `*.com*` غير صحيح (ليس مجالا قابلا للحل ولا يتبع حرف البدل الصحيح شرطة مائلة للأمام).

  - لا يسمح بأحرف البدل في عناوين IP.

- يتوفر حرف التلدة (~) في السيناريوهات التالية:

  - يشير التلدة اليسرى إلى مجال وكافة المجالات الفرعية.

    على سبيل المثال `~contoso.com` يتضمن `contoso.com` و `*.contoso.com`.

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
  - contoso.com
  - contoso.com/q=a@contoso.com

- **مطابقة الكتلة**:
  - contoso.com
  - contoso.com/a
  - payroll.contoso.com
  - test.com/contoso.com
  - test.com/q=contoso.com
  - contoso.com
  - contoso.com/q=a@contoso.com

- **الكتلة غير متطابقة**: abc-contoso.com

#### <a name="scenario-left-wildcard-subdomain"></a>السيناريو: حرف بدل أيسر (مجال فرعي)

> [!NOTE]
> ينطبق هذا السيناريو على الكتل فقط.

**الإدخال**: `*.contoso.com`

- **مطابقة الكتلة**:
  - contoso.com
  - xyz.abc.contoso.com

- **الكتلة غير متطابقة**:
  - 123contoso.com
  - contoso.com
  - test.com/contoso.com
  - contoso.com/abc

#### <a name="scenario-right-wildcard-at-top-of-path"></a>السيناريو: حرف بدل أيمن في أعلى المسار

**الإدخال**: `contoso.com/a/*`

- **السماح بالتطابق** **وتطابق الكتلة**:
  - contoso.com/a/b
  - contoso.com/a/b/c
  - contoso.com/a/?q=joe@t.com

- **السماح غير متطابق** **والكتلة غير متطابقة**:
  - contoso.com
  - contoso.com/a
  - contoso.com
  - contoso.com/q=a@contoso.com

#### <a name="scenario-left-tilde"></a>السيناريو: التلدة اليسرى

**الإدخال**: `~contoso.com`

- **السماح بالتطابق** **وتطابق الكتلة**:
  - contoso.com
  - contoso.com
  - xyz.abc.contoso.com

- **السماح غير متطابق** **والكتلة غير متطابقة**:
  - 123contoso.com
  - contoso.com/abc
  - contoso.com/abc

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

> [!NOTE]
> ينطبق هذا السيناريو على الكتل فقط.

**الإدخال**: `*.contoso.com/*`

- **مطابقة الكتلة**:
  - abc.contoso.com/ab
  - abc.xyz.contoso.com/a/b/c
  - contoso.com/a
  - contoso.com/b/a/c
  - xyz.contoso.com/ba

- **الكتلة غير متطابقة**: contoso.com/b

#### <a name="scenario-left-and-right-tilde"></a>السيناريو: التلدة اليمنى واليسرى

**الإدخال**: `~contoso.com~`

- **السماح بالتطابق** **وتطابق الكتلة**:

  - contoso.com
  - contoso.com/a
  - contoso.com
  - contoso.com/b
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

  - conto\*so.com
  - conto~so.com

- **أحرف البدل المزدوجة**

  - contoso.com/\*\*
  - contoso.com/\*/\*

## <a name="create-block-url-entries-in-the-tenant-allowblock-list"></a>إنشاء إدخالات عنوان URL للكتلة في قائمة السماح/الحظر للمستأجر

### <a name="use-microsoft-365-defender"></a>استخدام Microsoft 365 Defender

1. في مدخل Microsoft 365 Defender، <https://security.microsoft.com>انتقل إلى **"نهج & قواعد قواعد** \> **نهج التهديد** \> **" قسم** \> **"السماح/حظر القوائم للمستأجر**". أو للانتقال مباشرة إلى صفحة **"السماح بالمستأجر/قائمة الحظر** "، استخدم <https://security.microsoft.com/tenantAllowBlockList>.

2. في الصفحة **"السماح بالمستأجر/قائمة الحظر** "، تحقق من تحديد علامة التبويب **"عناوين URL** "، ثم انقر فوق ![أيقونة "حظر".](../../media/m365-cc-sc-create-icon.png) **كتلة**.

3. في القائمة المنبثقة **لعناوين URL للكتلة** التي تظهر، قم بتكوين الإعدادات التالية:
   - **إضافة عناوين URL باستخدام أحرف البدل**: أدخل URL واحدا لكل سطر، بحد أقصى 20. للحصول على تفاصيل حول بناء جملة إدخالات URL، راجع قسم بناء جملة URL في [إدارة قائمة السماح/الحظر للمستأجر](tenant-allow-block-list.md).
   - **لا تنتهي صلاحيتها أبدا**: نفذ إحدى الخطوات التالية:
     - تحقق من إيقاف تشغيل الإعداد (![إيقاف التشغيل.](../../media/scc-toggle-off.png)) واستخدم المربع **"إزالة في** " لتحديد تاريخ انتهاء صلاحية الإدخالات.

       او

     - انقل التبديل إلى اليمين لتكوين الإدخالات بحيث لا تنتهي صلاحيتها أبدا: ![تشغيل التشغيل.](../../media/scc-toggle-on.png).
   - **ملاحظة اختيارية**: أدخل نصا وصفيا للإدخالات.

4. عند الانتهاء، انقر فوق **"إضافة**".

> [!NOTE]
> سيتم حظر رسائل البريد الإلكتروني التي تحتوي على عناوين URL هذه على أنها _تصيد احتيالي_.

### <a name="use-powershell"></a>استخدام PowerShell

لإضافة إدخالات عنوان URL للكتلة في قائمة السماح/الحظر للمستأجر، استخدم بناء الجملة التالي:

```powershell
New-TenantAllowBlockListItems -ListType <Url> -Block -Entries "Value1","Value2",..."ValueN" <-ExpirationDate Date | -NoExpiration> [-Notes <String>]
```

يضيف هذا المثال إدخال URL كتلة contoso.com وكافة المجالات الفرعية (على سبيل المثال، contoso.com xyz.abc.contoso.com). نظرا لأننا لم نستخدم معلمات ExpirationDate أو NoExpiration، تنتهي صلاحية الإدخال بعد 30 يوما.

```powershell
New-TenantAllowBlockListItems -ListType Url -Block -Entries ~contoso.com
```

للحصول على معلومات مفصلة حول بناء الجملة والمعلمة، راجع [New-TenantAllowBlockListItems](/powershell/module/exchange/new-tenantallowblocklistitems).

## <a name="create-allow-url-entries"></a>إنشاء إدخالات عنوان URL للسماح

### <a name="use-microsoft-365-defender"></a>استخدام Microsoft 365 Defender

السماح بعناوين URL على صفحة **عمليات الإرسال** في Microsoft 365 Defender.

1. في مدخل Microsoft 365 Defender، <https://security.microsoft.com>انتقل إلى **عمليات الإرسال** \> & الإجراءات **.** أو للانتقال مباشرة إلى صفحة **عمليات الإرسال** ، استخدم <https://security.microsoft.com/reportsubmission>.

2. في الصفحة **"عمليات الإرسال"** ، حدد علامة التبويب **"عناوين URL** "، ثم انقر فوق " ![إرسال إلى Microsoft" للتحليل.](../../media/m365-cc-sc-create-icon.png) **إرسال إلى Microsoft للتحليل**.

3. استخدم القائمة المنبثقة " **إرسال إلى Microsoft" للمراجعة** لإرسال رسالة عن طريق إضافة عنوان URL.

4. في **"تحديد سبب الإرسال إلى قسم Microsoft** "، حدد **"يجب ألا يكون قد تم حظره (إيجابية خاطئة)**".

5. قم بتشغيل **السماح بعناوين URL مثل هذا** الخيار.

6. من القائمة المنسدلة **"إزالة بعد** "، حدد المدة التي تريد أن يعمل فيها خيار السماح.

7. أضف سبب إضافة السماح باستخدام **الملاحظة الاختيارية**. 

8. عند الانتهاء، انقر فوق الزر **"إرسال** ".

    :::image type="content" source="../../media/submit-url-for-analysis.png" alt-text="إرسال URL للتحليل" lightbox="../../media/submit-url-for-analysis.png":::

> [!NOTE]
>
> - عند مصادفة عنوان URL مرة أخرى، لا يتم إرسال عنوان URL للتدقيق أو السمعة ويتم تخطي جميع عوامل التصفية الأخرى المستندة إلى عنوان URL.
> - لذلك بالنسبة إلى رسالة بريد إلكتروني (تحتوي على عنوان URL هذا)، أثناء تدفق البريد، إذا وجدت بقية عوامل التصفية أن البريد الإلكتروني نظيفا، فسيتم تسليم البريد الإلكتروني.

## <a name="view-url-entries"></a>عرض إدخالات URL

لعرض إدخالات عنوان URL للكتلة في قائمة السماح/الحظر للمستأجر، استخدم بناء الجملة التالي:

```powershell
Get-TenantAllowBlockListItems -ListType <URL> [-Entry <SenderValue | FileHashValue | URLValue>] [<-ExpirationDate Date | -NoExpiration>]
```

يرجع هذا المثال كافة عناوين URL المحظورة.

```powershell
Get-TenantAllowBlockListItems -ListType Url -Block
```

للحصول على معلومات مفصلة حول بناء الجملة والمعلمة، راجع [Get-TenantAllowBlockListItems](/powershell/module/exchange/get-tenantallowblocklistitems).

## <a name="modify-url-entries"></a>تعديل إدخالات URL 

لتعديل إدخالات عنوان URL المسموح بها أو حظرها في قائمة السماح/الحظر للمستأجر، استخدم بناء الجملة التالي:

```powershell
Set-TenantAllowBlockListItems -ListType <URL> -Ids <"Id1","Id2",..."IdN"> [<-ExpirationDate Date | -NoExpiration>] [-Notes <String>]
```

يغير هذا المثال تاريخ انتهاء صلاحية إدخال URL للكتلة المحددة.

```powershell
Set-TenantAllowBlockListItems -ListType Url -Ids "RgAAAAAI8gSyI_NmQqzeh-HXJBywBwCqfQNJY8hBTbdlKFkv6BcUAAAl_QCZAACqfQNJY8hBTbdlKFkv6BcUAAAl_oSRAAAA" -ExpirationDate "5/30/2020"
```

للحصول على معلومات مفصلة حول بناء الجملة والمعلمة، راجع [Set-TenantAllowBlockListItems](/powershell/module/exchange/set-tenantallowblocklistitems).

## <a name="remove-url-entries"></a>إزالة إدخالات URL 

لإزالة إدخالات عنوان URL للسماح أو الحظر من قائمة السماح/الحظر للمستأجر، استخدم بناء الجملة التالي:

```powershell
Remove-TenantAllowBlockListItems -ListType <URL> -Ids <"Id1","Id2",..."IdN">
```
يزيل هذا المثال إدخال URL للكتلة المحدد من قائمة السماح/الحظر للمستأجر.

```powershell
Remove-TenantAllowBlockListItems -ListType Url -Ids "RgAAAAAI8gSyI_NmQqzeh-HXJBywBwCqfQNJY8hBTbdlKFkv6BcUAAAl_QCZAACqfQNJY8hBTbdlKFkv6BcUAAAl_oSPAAAA0"
```

للحصول على معلومات مفصلة حول بناء الجملة والمعلمة، راجع [Remove-TenantAllowBlockListItems](/powershell/module/exchange/remove-tenantallowblocklistitems).

## <a name="related-articles"></a>المقالات ذات الصلة

- [عمليات إرسال المسؤول](admin-submission.md)
- [الإبلاغ عن الإيجابيات الخاطئة والسلبيات الخاطئة](report-false-positives-and-false-negatives.md)
- [إدارة السمحات والكتل في قائمة السماح/الحظر للمستأجر](manage-tenant-allow-block-list.md)
- [السماح بالملفات أو حظرها في قائمة السماح/الحظر للمستأجر](allow-block-files.md)
- [السماح برسائل البريد الإلكتروني أو حظرها في قائمة السماح/الحظر للمستأجر](allow-block-email-spoof.md)
