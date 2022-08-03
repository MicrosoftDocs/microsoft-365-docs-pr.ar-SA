---
title: السماح برسائل البريد الإلكتروني أو حظرها باستخدام قائمة السماح/الحظر للمستأجر
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
- MET150
ms.collection:
- M365-security-compliance
description: يمكن للمسؤولين معرفة كيفية السماح برسائل البريد الإلكتروني وإدخالات المرسلين المخادعة أو حظرها في قائمة السماح/الحظر للمستأجر في مدخل الأمان.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 107aef5dd4cc3098d6e77f45e6b95352997ef738
ms.sourcegitcommit: d7193ee954c01c4172e228d25b941026c8d92d30
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 08/02/2022
ms.locfileid: "67174993"
---
# <a name="allow-or-block-emails-using-the-tenant-allowblock-list"></a>السماح برسائل البريد الإلكتروني أو حظرها باستخدام قائمة السماح/الحظر للمستأجر

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**ينطبق على**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [خطة 1 وخطة 2 من Microsoft Defender لـ Office 365](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

يمكنك استخدام مدخل Microsoft 365 Defender أو PowerShell للسماح برسائل البريد الإلكتروني أو حظرها (بما في ذلك رسائل البريد الإلكتروني المخادعة) باستخدام قائمة السماح/الحظر للمستأجر.

## <a name="create-block-sender-entries"></a>إنشاء إدخالات مرسل الحظر 

### <a name="use-the-microsoft-365-defender-portal"></a>استخدام مدخل Microsoft 365 Defender

1. في مدخل Microsoft 365 Defender، <https://security.microsoft.com>انتقل إلى **"نهج & قواعد قواعد** \> **نهج التهديد** \> **" قسم** \> **"السماح/حظر القوائم للمستأجر**". أو للانتقال مباشرة إلى صفحة **"السماح بالمستأجر/قائمة الحظر** "، استخدم <https://security.microsoft.com/tenantAllowBlockList>.

2. في الصفحة **"السماح بالمستأجر/قائمة الحظر** "، تحقق من تحديد علامة التبويب " **المجالات & العناوين** "، ثم انقر فوق ![أيقونة "حظر".](../../media/m365-cc-sc-create-icon.png) **كتلة**.

3. في **نطاقات الحظر & القائمة المنبثقة للعناوين** التي تظهر، قم بتكوين الإعدادات التالية:
   - **عناوين البريد الإلكتروني أو المجالات**: أدخل عنوان بريد إلكتروني أو مجالا واحدا لكل سطر، بحد أقصى 20.
   - **لا تنتهي صلاحيتها أبدا**: نفذ إحدى الخطوات التالية:
     - تحقق من إيقاف تشغيل الإعداد (![إيقاف التشغيل.](../../media/scc-toggle-off.png)) واستخدم المربع **"إزالة في** " لتحديد تاريخ انتهاء صلاحية الإدخالات.

       أو

     - انقل التبديل إلى اليمين لتكوين الإدخالات بحيث لا تنتهي صلاحيتها أبدا: ![تشغيل التشغيل.](../../media/scc-toggle-on.png).
   - **ملاحظة اختيارية**: أدخل نصا وصفيا للإدخالات.

4. عند الانتهاء، انقر فوق **"إضافة**".

> [!NOTE]
> سيتم حظر رسائل البريد الإلكتروني الواردة من هؤلاء المرسلين _كبرم عشوائي عالي الثقة_ (SCL = 9).
> لن يتمكن المستخدمون في المؤسسة من إرسال رسائل البريد الإلكتروني إلى هذه المجالات والعناوين المحظورة. سيتلقى تقرير بعدم التسليم الذي سيذكر ما يلي: "5.7.1 لا يمكن تسليم رسالتك لأنه تم حظر مستلم واحد أو أكثر من قبل نهج السماح/قائمة الحظر لمؤسستك".

### <a name="use-powershell"></a>استخدام PowerShell

لإضافة إدخالات مرسل الحظر في قائمة السماح/الحظر للمستأجر، استخدم بناء الجملة التالي:

```powershell
New-TenantAllowBlockListItems -ListType <Sender> -Block -Entries "Value1","Value2",..."ValueN" <-ExpirationDate Date | -NoExpiration> [-Notes <String>]
```

يضيف هذا المثال إدخال مرسل حظر للمرسل المحدد الذي تنتهي صلاحيته في تاريخ معين.

```powershell
New-TenantAllowBlockListItems -ListType Sender -Block -Entries "test@badattackerdomain.com", "test2@anotherattackerdomain.com" -ExpirationDate 8/20/2021
```

للحصول على معلومات مفصلة حول بناء الجملة والمعلمة، راجع [New-TenantAllowBlockListItems](/powershell/module/exchange/new-tenantallowblocklistitems).

## <a name="create-allow-sender-entries"></a>إنشاء إدخالات السماح للمرسل 

### <a name="use-microsoft-365-defender"></a>استخدام Microsoft 365 Defender

السماح للمرسلين (أو المجالات) في صفحة **"عمليات الإرسال**" في Microsoft 365 Defender.

لا يمكنك تعديل قائمة السماح/الحظر للمستأجر مباشرة لإضافة إدخالات السماح. بدلا من ذلك، استخدم [عمليات إرسال المسؤول](admin-submission.md) لإرسال الرسالة المحظورة. سيضيف هذا الإجراء عنوان URL أو ملف أو زوج مجال مرسل منتحل أو مجال منتحل (أو مستخدم) و/أو مرسل إلى قائمة السماح/الحظر للمستأجر. إذا لم يتم حظر العنصر، فلن يتم إنشاء السماح. في معظم الحالات التي تم فيها تحديد الرسالة على أنها إيجابية خاطئة تم حظرها بشكل غير صحيح، ستتم إزالة إدخال السماح في تاريخ انتهاء الصلاحية المحدد.

> [!IMPORTANT]
> - نظرا لأن Microsoft تدير إدخالات السماح لك، ستتم إزالة إدخالات السماح للمرسل أو عنوان URL أو الملف غير المطلوبة. يحمي هذا السلوك مؤسستك ويساعد على منع إدخالات السماح التي تم تكوينها بشكل خاطئ. إذا كنت لا توافق على الحكم، فقد تحتاج إلى فتح حالة دعم للمساعدة في تحديد سبب استمرار اعتبار الرسالة سيئة.


1. في مدخل Microsoft 365 Defender، <https://security.microsoft.com>انتقل إلى **عمليات الإرسال** \> & الإجراءات **.** أو للانتقال مباشرة إلى صفحة **عمليات الإرسال** ، استخدم <https://security.microsoft.com/reportsubmission>.

2. في الصفحة **"عمليات الإرسال"** ، تحقق من تحديد علامة التبويب **"رسائل البريد الإلكتروني** "، ثم انقر فوق " ![إرسال إلى Microsoft" للتحليل.](../../media/m365-cc-sc-create-icon.png) **إرسال إلى Microsoft للتحليل**.

3. استخدم القائمة المنبثقة " **إرسال إلى Microsoft" للمراجعة** لإرسال رسالة عن طريق إضافة معرف رسالة الشبكة أو تحميل ملف البريد الإلكتروني.

4. في **"تحديد سبب الإرسال إلى قسم Microsoft** "، حدد **"يجب ألا يكون قد تم حظره (إيجابية خاطئة)**".

5. تشغيل **السماح بالرسائل مثل هذا** الخيار.

6. من القائمة المنسدلة **"إزالة بعد** "، حدد المدة التي تريد أن يعمل فيها خيار السماح.

7. أضف سبب إضافة السماح باستخدام المربع **"ملاحظة اختيارية** ". 

8. عند الانتهاء، حدد الزر **"إرسال** ".

  :::image type="content" source="../../media/admin-submission-allow-messages.png" alt-text="إرسال البرامج الضارة إلى Microsoft للحصول على مثال تحليل." lightbox="../../media/admin-submission-allow-messages.png":::

> [!NOTE]
>
> - أثناء تدفق البريد، استنادا إلى عوامل التصفية التي حددت أن البريد ضار، تتم إضافة الأذونات. على سبيل المثال، يتم تحديد المرسل وعنوان URL على أن يكونا سيئين، وستتم إضافة سماح لكل منهما.
> - عند مصادفة هذا الكيان (المرسل، المجال، URL، الملف) مرة أخرى، يتم تخطي كافة عوامل التصفية المقترنة بهذا الكيان.
> - أثناء تدفق البريد، إذا وجدت بقية عوامل التصفية أن البريد الإلكتروني الذي يحتوي على هذا الكيان نظيفا، فسيتم تسليم البريد الإلكتروني. على سبيل المثال، سيؤدي السماح للمرسل (عند مرور المصادقة) إلى تجاوز جميع الأحكام باستثناء البرامج الضارة والتصيد الاحتيالي عالي الثقة المقترن بمرفق أو عنوان URL.

## <a name="view-sender-entries"></a>عرض إدخالات المرسل 

لعرض إدخالات مرسل الحظر في قائمة السماح/الحظر للمستأجر، استخدم بناء الجملة التالي:

```powershell
Get-TenantAllowBlockListItems -ListType <Sender> [-Entry <SenderValue | FileHashValue | URLValue>] [<-ExpirationDate Date | -NoExpiration>]
```
للحصول على معلومات مفصلة حول بناء الجملة والمعلمة، راجع [Get-TenantAllowBlockListItems](/powershell/module/exchange/get-tenantallowblocklistitems).

## <a name="modify-sender-entries"></a>تعديل إدخالات المرسل 

لتعديل إدخالات السماح أو الحظر في قائمة السماح/الحظر للمستأجر، استخدم بناء الجملة التالي:

```powershell
Set-TenantAllowBlockListItems -ListType <Sender> -Ids <"Id1","Id2",..."IdN"> [<-ExpirationDate Date | -NoExpiration>] [-Notes <String>]
```

للحصول على معلومات مفصلة حول بناء الجملة والمعلمة، راجع [Set-TenantAllowBlockListItems](/powershell/module/exchange/set-tenantallowblocklistitems).

## <a name="remove-sender-entries"></a>إزالة إدخالات المرسل 

لإزالة إدخالات السماح أو الحظر من قائمة السماح/الحظر للمستأجر، استخدم بناء الجملة التالي:

```powershell
Remove-TenantAllowBlockListItems -ListType <Sender> -Ids <"Id1","Id2",..."IdN">
```

للحصول على معلومات مفصلة حول بناء الجملة والمعلمة، راجع [Remove-TenantAllowBlockListItems](/powershell/module/exchange/remove-tenantallowblocklistitems).

## <a name="domain-pair-syntax-for-spoofed-sender-entries"></a>بناء جملة زوج المجال لإدخالات المرسلين المخادعة

يستخدم زوج المجال لمرسل منتحل في قائمة السماح/الحظر للمستأجر بناء الجملة التالي: `<Spoofed user>, <Sending infrastructure>`.

- **المستخدم المخادعة**: تتضمن هذه القيمة عنوان البريد الإلكتروني للمستخدم المخادعة الذي يتم عرضه في المربع **"من** " في عملاء البريد الإلكتروني. يعرف هذا العنوان أيضا بالعنوان `5322.From` . تتضمن القيم الصالحة ما يلي:
  - عنوان بريد إلكتروني فردي (على سبيل المثال، chris@contoso.com).
  - مجال بريد إلكتروني (على سبيل المثال، contoso.com).
  - حرف البدل (على سبيل المثال، \*).

- **إرسال البنية الأساسية**: تشير هذه القيمة إلى مصدر الرسائل من المستخدم المخادعة. تتضمن القيم الصالحة ما يلي:
  - المجال الموجود في بحث DNS العكسي (سجل PTR) لعنوان IP لخادم البريد الإلكتروني المصدر (على سبيل المثال، fabrikam.com).
  - إذا لم يكن لعنوان IP المصدر سجل PTR، فسيتم تعريف البنية الأساسية للإرسال على أنها \<source IP\>/24 (على سبيل المثال، 192.168.100.100/24).
  - مجال DKIM تم التحقق منه.

فيما يلي بعض الأمثلة على أزواج المجالات الصالحة لتحديد المرسلين المخادعة:

- `contoso.com, 192.168.100.100/24`
- `chris@contoso.com, fabrikam.com`
- `*, contoso.net`

الحد الأقصى لعدد إدخالات المرسلين المخادعة هو 1000.

إضافة زوج مجال يسمح فقط أو يحظر *الجمع بين* المستخدم المخادعة *والبنية* الأساسية لإرسال. ولا يسمح بالبريد الإلكتروني من المستخدم المخادعة من أي مصدر، كما أنه لا يسمح بالبريد الإلكتروني من مصدر البنية الأساسية المرسلة لأي مستخدم منتحل.

على سبيل المثال، يمكنك إضافة إدخال السماح لزوج المجال التالي:

- **المجال**: gmail.com
- **البنية الأساسية**: tms.mx.com

يسمح فقط للرسائل الواردة من هذا المجال _وإرسال_ زوج البنية الأساسية بالانتحال. لا يسمح للمرسلين الآخرين الذين يحاولون تزييف gmail.com. يتم التحقق من الرسائل الواردة من المرسلين في مجالات أخرى تنشأ من tms.mx.com بواسطة التحليل الذكي للانتحال.

## <a name="create-blocked-spoofed-sender-entries"></a>إنشاء إدخالات المرسلين المخادعة المحظورة

### <a name="use-microsoft-365-defender"></a>استخدام Microsoft 365 Defender

> [!NOTE]
> سيتم حظر البريد الإلكتروني الوارد من هؤلاء المرسلين على أنه _تصيد احتيالي_.
>
> يسمح فقط _بمزيج_ المستخدم المخادعة _والبنية_ الأساسية المرسلة كما هو محدد في زوج المجال أو حظره من الانتحال.
>
> عند تكوين إدخال السماح أو الحظر لزوج مجال، لن تظهر الرسائل الواردة من زوج المجال هذا في نتيجة التحليل الذكي المخادعة.
>
> لا تنتهي صلاحية إدخالات المرسلين المخادعة أبدا.

1. في مدخل Microsoft 365 Defender، انتقل إلى **"نهج & قواعد قواعد** \> **نهج التهديد** \> **" قسم** "\>**السماح/حظر القوائم للمستأجر**".

2. في الصفحة **"السماح بالمستأجر/قائمة الحظر** "، حدد علامة التبويب " **المرسلون المخادون** "، ثم انقر فوق ![أيقونة "حظر".](../../media/m365-cc-sc-create-icon.png) **إضافة**.

3. في القائمة المنبثقة **"إضافة أزواج مجالات جديدة** " التي تظهر، قم بتكوين الإعدادات التالية:
   - **إضافة أزواج مجالات جديدة باستخدام أحرف البدل**: أدخل زوج مجال واحد لكل سطر، بحد أقصى 20 زوجا. للحصول على تفاصيل حول بناء الجملة لإدخالات المرسلين المخادعة، راجع [إدارة قائمة السماح/الحظر للمستأجر](tenant-allow-block-list.md).
   - **نوع الانتحال**: حدد إحدى القيم التالية:
     - **داخلي**: المرسل المخادع موجود في مجال ينتمي إلى مؤسستك ( [مجال مقبول](/exchange/mail-flow-best-practices/manage-accepted-domains/manage-accepted-domains)).
     - **خارجي**: المرسل المخادع موجود في مجال خارجي.
   - **الإجراء**: حدد **كتلة**.

4. عند الانتهاء، انقر فوق **"إضافة**".

> [!NOTE]
> سيتم حظر رسائل البريد الإلكتروني الواردة من هؤلاء المرسلين على أنها _تصيد احتيالي_.

### <a name="use-powershell"></a>استخدام PowerShell

لإضافة إدخالات المرسل المخادعة في قائمة السماح/الحظر للمستأجر، استخدم بناء الجملة التالي:

```powershell
New-TenantAllowBlockListSpoofItems -SpoofedUser <Domain | EmailAddress | *> -SendingInfrastructure <Domain | IPAddress/24> -SpoofType <External | Internal> -Action <Allow | Block>
```

للحصول على معلومات مفصلة حول بناء الجملة والمعلمة، راجع [New-TenantAllowBlockListSpoofItems](/powershell/module/exchange/new-tenantallowblocklistspoofitems).

## <a name="create-allowed-spoofed-sender-entries"></a>إنشاء إدخالات المرسلين المخادعة المسموح بها 

### <a name="use-the-tenant-allowblock-list-in-microsoft-365-defender"></a>استخدام قائمة السماح/الحظر للمستأجر في Microsoft 365 Defender

> [!NOTE]
>
> - يسمح فقط _بمزيج_ المستخدم المخادعة _والبنية_ الأساسية المرسلة كما هو محدد في زوج المجال أو حظره من الانتحال.
> - عند تكوين إدخال السماح أو الحظر لزوج مجال، لن تظهر الرسائل الواردة من زوج المجال هذا في نتيجة التحليل الذكي المخادعة.
> - لا تنتهي صلاحية إدخالات المرسلين المخادعة أبدا.

1. في مدخل Microsoft 365 Defender، <https://security.microsoft.com>انتقل إلى "نهج تعاون \> **& البريد الإلكتروني****" & قواعد "نهج** \> \> **التهديد****"، قوائم السماح/الحظر للمستأجر** في قسم **"القواعد**". أو للانتقال مباشرة إلى صفحة **"السماح بالمستأجر/قوائم الحظر** "، استخدم <https://security.microsoft.com/tenantAllowBlockList>.

2. في صفحة **"السماح بالمستأجر/قائمة الحظر** "، حدد علامة التبويب " **المرسلون المخادعة** "، ثم انقر فوق " ![إضافة أيقونة".](../../media/m365-cc-sc-create-icon.png) **إضافة**.

3. في القائمة المنبثقة **"إضافة أزواج مجالات جديدة** " التي تظهر، قم بتكوين الإعدادات التالية:
   - **إضافة أزواج مجالات جديدة باستخدام أحرف البدل**: أدخل زوج مجال واحد لكل سطر، بحد أقصى 20 زوجا. للحصول على تفاصيل حول بناء الجملة لإدخالات المرسلين المخادعة، راجع [إدارة قائمة السماح/الحظر للمستأجر](tenant-allow-block-list.md).
   - **نوع الانتحال**: حدد إحدى القيم التالية:
     - **داخلي**: المرسل المخادع موجود في مجال ينتمي إلى مؤسستك ( [مجال مقبول](/exchange/mail-flow-best-practices/manage-accepted-domains/manage-accepted-domains)).
     - **خارجي**: المرسل المخادع موجود في مجال خارجي.
   - **الإجراء**: حدد **السماح**.

4. عند الانتهاء، انقر فوق **"إضافة**".

### <a name="use-admin-submission-in-microsoft-365-defender"></a>استخدام مسؤول الإرسال في Microsoft 365 Defender

يمكنك أيضا السماح للمرسلين المخادعين باستخدام صفحة **عمليات الإرسال** في Microsoft 365 Defender.

استخدم [عمليات إرسال المسؤول](admin-submission.md) لإرسال الرسالة المحظورة. سيضيف هذا الإجراء عنوان URL أو ملف أو زوج مجال مرسل منتحل أو مجال منتحل (أو مستخدم) و/أو مرسل إلى قائمة السماح/الحظر للمستأجر. إذا لم يتم حظر العنصر، فلن يتم إنشاء السماح. 

> [!IMPORTANT]
>
> - يسمح الانتحال بالانتحال داخل المؤسسة، والانتحال عبر المؤسسة وDMARC.
> - لا تنطبق الملاحظة الاختيارية في عمليات إرسال المسؤول على عمليات الانتحال.

1. في مدخل Microsoft 365 Defender، <https://security.microsoft.com>انتقل إلى **عمليات الإرسال** \> & الإجراءات **.** أو للانتقال مباشرة إلى صفحة **عمليات الإرسال** ، استخدم <https://security.microsoft.com/reportsubmission>.

2. في الصفحة **"عمليات الإرسال"** ، تحقق من تحديد علامة التبويب **"رسائل البريد الإلكتروني** "، ثم انقر فوق " ![إرسال إلى Microsoft" للتحليل.](../../media/m365-cc-sc-create-icon.png) **إرسال إلى Microsoft للتحليل**.

3. استخدم القائمة المنبثقة " **إرسال إلى Microsoft" للمراجعة** لإرسال رسالة عن طريق إضافة معرف رسالة الشبكة أو تحميل ملف البريد الإلكتروني.

4. في **"تحديد سبب الإرسال إلى قسم Microsoft** "، حدد **"يجب ألا يكون قد تم حظره (إيجابية خاطئة)**".

5. تشغيل **السماح بالرسائل مثل هذا** الخيار.

6. من القائمة المنسدلة **"إزالة بعد** "، حدد المدة التي تريد أن يعمل فيها خيار السماح على الرغم من أنه لا ينطبق على الانتحال حيث لا تنتهي صلاحيته أبدا.

7. عند الانتهاء، حدد الزر **"إرسال** ".

  :::image type="content" source="../../media/admin-submission-allow-messages.png" alt-text="إرسال البرامج الضارة إلى Microsoft للحصول على مثال تحليل." lightbox="../../media/admin-submission-allow-messages.png":::

> [!NOTE]
>
> - سيتم إنشاء زوج مجال المرسل المخادع وظهوره في علامة تبويب **المرسلين المخادعة** ضمن صفحة **قائمة السماح/الحظر للمستأجر** .


### <a name="use-powershell"></a>استخدام PowerShell

لإضافة إدخالات المرسل المخادعة في قائمة السماح/الحظر للمستأجر في [Exchange Online PowerShell](/powershell/exchange/exchange-online-powershell)، استخدم بناء الجملة التالي:

```powershell
New-TenantAllowBlockListSpoofItems -SpoofedUser <Domain | EmailAddress | *> -SendingInfrastructure <Domain | IPAddress/24> -SpoofType <External | Internal> -Action <Allow | Block>
```

للحصول على معلومات مفصلة حول بناء الجملة والمعلمة، راجع [New-TenantAllowBlockListSpoofItems](/powershell/module/exchange/new-tenantallowblocklistspoofitems).

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

## <a name="modify-spoofed-sender-entries"></a>تعديل إدخالات المرسلين المخادعة 

لتعديل إدخالات المرسلين المخادعة في قائمة السماح/الحظر للمستأجر أو حظرها، استخدم بناء الجملة التالي:

```powershell
Set-TenantAllowBlockListSpoofItems -Ids <"Id1","Id2",..."IdN"> -Action <Allow | Block>
```

يغير هذا المثال إدخال المرسل المخادع من السماح إلى الحظر.

```powershell
Set-TenantAllowBlockListItems -Ids "RgAAAAAI8gSyI_NmQqzeh-HXJBywBwCqfQNJY8hBTbdlKFkv6BcUAAAl_QCZAACqfQNJY8hBTbdlKFkv6BcUAAAl_oSRAAAA" -Action Block
```

للحصول على معلومات مفصلة حول بناء الجملة والمعلمة، راجع [Set-TenantAllowBlockListSpoofItems](/powershell/module/exchange/set-tenantallowblocklistspoofitems).

## <a name="remove-spoofed-sender-entries"></a>إزالة إدخالات المرسلين المخادعة 

لإزالة إدخالات مرسل الانتحال المسموح بها أو حظرها من قائمة السماح/الحظر للمستأجر، استخدم بناء الجملة التالي:

```powershell
Remove-TenantAllowBlockListSpoofItems -Ids <"Id1","Id2",..."IdN">
```

للحصول على معلومات مفصلة حول بناء الجملة والمعلمة، راجع [Remove-TenantAllowBlockListSpoofItems](/powershell/module/exchange/remove-tenantallowblocklistspoofitems).

## <a name="create-impersonated-sender-entries"></a>إنشاء إدخالات المرسلين منتحلة

### <a name="use-admin-submission-in-microsoft-365-defender"></a>استخدام مسؤول الإرسال في Microsoft 365 Defender

يمكنك أيضا السماح للمرسلين المنتحلين باستخدام صفحة **عمليات الإرسال** في Microsoft 365 Defender.

استخدم [عمليات إرسال المسؤول](admin-submission.md) لإرسال الرسالة المحظورة. سيضيف هذا الإجراء عنوان URL أو ملف أو زوج مجال مرسل منتحل أو مجال منتحل (أو مستخدم) و/أو مرسل إلى قائمة السماح/الحظر للمستأجر. إذا لم يتم حظر العنصر، فلن يتم إنشاء السماح. 

> [!IMPORTANT]
>
> - يسمح الانتحال بالعناية بالمجال وانتحال المستخدم.
> - لا يتم الاهتمام بانتحال الرسم البياني من هنا في الوقت الحالي.

1. في مدخل Microsoft 365 Defender، <https://security.microsoft.com>انتقل إلى **عمليات الإرسال** \> & الإجراءات **.** أو للانتقال مباشرة إلى صفحة **عمليات الإرسال** ، استخدم <https://security.microsoft.com/reportsubmission>.

2. في الصفحة **"عمليات الإرسال"** ، تحقق من تحديد علامة التبويب **"رسائل البريد الإلكتروني** "، ثم انقر فوق " ![إرسال إلى Microsoft" للتحليل.](../../media/m365-cc-sc-create-icon.png) **إرسال إلى Microsoft للتحليل**.

3. استخدم القائمة المنبثقة " **إرسال إلى Microsoft" للمراجعة** لإرسال رسالة عن طريق إضافة معرف رسالة الشبكة أو تحميل ملف البريد الإلكتروني.

4. في **"تحديد سبب الإرسال إلى قسم Microsoft** "، حدد **"يجب ألا يكون قد تم حظره (إيجابية خاطئة)**".

5. تشغيل **السماح بالرسائل مثل هذا** الخيار.

6. من القائمة المنسدلة **"إزالة بعد** "، حدد المدة التي تريد أن يعمل فيها خيار السماح على الرغم من أنه لا ينطبق على السماح الذي تم انتحاله حيث لا تنتهي صلاحيته أبدا.

7. عند الانتهاء، حدد الزر **"إرسال** ".

  :::image type="content" source="../../media/admin-submission-allow-messages.png" alt-text="إرسال البرامج الضارة إلى Microsoft للحصول على مثال تحليل." lightbox="../../media/admin-submission-allow-messages.png":::

> [!NOTE]
> سيتم إنشاء المجال (أو المستخدم) الذي تم انتحاله ومرئيا في قسم **المرسلين والمجالات الموثوق بهم** في نهج مكافحة التصيد الاحتيالي في <https://security.microsoft.com/antiphishing>.

## <a name="related-articles"></a>المقالات ذات الصلة

- [عمليات إرسال المسؤول](admin-submission.md)
- [الإبلاغ عن الإيجابيات الخاطئة والسلبيات الخاطئة](report-false-positives-and-false-negatives.md)
- [إدارة السمحات والكتل في قائمة السماح/الحظر للمستأجر](manage-tenant-allow-block-list.md)
- [السماح بالملفات أو حظرها في قائمة السماح/الحظر للمستأجر](allow-block-files.md)
- [السماح بعناوين URL أو حظرها في قائمة السماح/الحظر للمستأجر](allow-block-urls.md)
