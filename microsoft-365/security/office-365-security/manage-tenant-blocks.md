---
title: إدارة كتلك في قائمة السماح/الحظر للمستأجر
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
description: يمكن للمسؤولين التعرف على كيفية تكوين الكتل في قائمة السماح/الحظر للمستأجر في مدخل الأمان.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 4cca466ce4862cc93ec7521bf6bd00fe960f06a9
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/08/2022
ms.locfileid: "63579687"
---
# <a name="add-blocks-in-the-tenant-allowblock-list"></a>إضافة كتل في قائمة السماح/الحظر للمستأجر

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**ينطبق على**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender Office 365 الخطة 1 الخطة 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

## <a name="use-the-microsoft-365-defender-portal"></a>استخدام Microsoft 365 Defender المدخل 

### <a name="create-block-sender-entries-in-the-tenant-allowblock-list"></a>إنشاء إدخالات مرسل الكتلة في قائمة السماح/الحظر للمستأجر

1. في مدخل Microsoft 365 Defender، انتقل  إلى "**&** \>  \> \> قواعد سياسات التهديدات" في القسم **"قوائم السماح/الحظر**" للمستأجر.

2. في صفحة **قائمة السماح/** الحظر للمستأجر، تحقق من تحديد  علامة التبويب المرسلون، ثم انقر فوق أيقونة ![الحظر.](../../media/m365-cc-sc-create-icon.png) **حظر**.

3. في قائمة **حظر المرسلين** التي تظهر، قم بتكوين الإعدادات التالية:
   - **عناوين البريد الإلكتروني للمرسل** أو المجالات: أدخل مرسلا واحدا (عنوان البريد الإلكتروني أو المجال) لكل سطر، بحد أقصى 20.
   - **لا تنتهي صلاحيتها** أبدا: يمكنك القيام بوا واحدة من الخطوات التالية:
     - تحقق من إيقاف تشغيل الإعداد (![إيقاف التشغيل).](../../media/scc-toggle-off.png)) ثم استخدم المربع إزالة عند التشغيل لتحديد  تاريخ انتهاء صلاحية الإدخالات.

       أو

     - نقل تبديل إلى اليمين لتكوين الإدخالات حتى لا تنتهي صلاحيتها أبدا: ![تبديل.](../../media/scc-toggle-on.png).
   - **ملاحظة اختيارية**: أدخل نصا وصفيا الإدخالات.

4. عند الانتهاء، انقر فوق **إضافة**.

> [!NOTE]
> سيتم حظر رسائل البريد الإلكتروني الواردة من هؤلاء المرسلين *كرسالة* عشوائية. 

### <a name="create-block-url-entries-in-the-tenant-allowblock-list"></a>إنشاء إدخالات عنوان URL الحظر في قائمة السماح/الحظر للمستأجر

1. في مدخل Microsoft 365 Defender، انتقل  إلى "**&** \>  \> \> قواعد سياسات التهديدات" في القسم **"قوائم السماح/الحظر**" للمستأجر.

2. في صفحة **قائمة السماح/** الحظر للمستأجر، تحقق من تحديد علامة التبويب **عناوين** URL، ثم انقر فوق أيقونة ![الحظر.](../../media/m365-cc-sc-create-icon.png) **حظر**.

3. في قائمة **حظر عناوين URL** التي تظهر، قم بتكوين الإعدادات التالية:
   - **إضافة عناوين URL مع أحرف البدل**: أدخل URL واحدا لكل سطر، بحد أقصى 20. للحصول على تفاصيل حول بناء جملة إدخالات URL، راجع المقطع بناء جملة URL في [إدارة قائمة السماح/الحظر](tenant-allow-block-list.md) للمستأجر.
   - **لا تنتهي صلاحيتها** أبدا: يمكنك القيام بوا واحدة من الخطوات التالية:
     - تحقق من إيقاف تشغيل الإعداد (![إيقاف التشغيل).](../../media/scc-toggle-off.png)) ثم استخدم المربع إزالة عند التشغيل لتحديد  تاريخ انتهاء صلاحية الإدخالات.

       أو

     - نقل تبديل إلى اليمين لتكوين الإدخالات حتى لا تنتهي صلاحيتها أبدا: ![تبديل.](../../media/scc-toggle-on.png).
   - **ملاحظة اختيارية**: أدخل نصا وصفيا الإدخالات.

4. عند الانتهاء، انقر فوق **إضافة**.

> [!NOTE]
> سيتم حظر رسائل البريد الإلكتروني التي تحتوي على عناوين URL هذه على أنها رسائل *تصيد احتيالي*. 

### <a name="create-block-file-entries-in-the-tenant-allowblock-list"></a>إنشاء إدخالات ملفات الحظر في قائمة السماح/الحظر للمستأجر

1. في مدخل Microsoft 365 Defender، انتقل  إلى "**&** \>  \> \> قواعد سياسات التهديدات" في القسم **"قوائم السماح/الحظر**" للمستأجر.

2. في صفحة **قائمة السماح/** الحظر للمستأجر، حدد علامة **التبويب** ملفات، ثم انقر فوق أيقونة ![الحظر.](../../media/m365-cc-sc-create-icon.png) **حظر**.

3. في قائمة **حظر الملفات** التي تظهر، قم بتكوين الإعدادات التالية:
   - **إضافة فهاشات الملفات**: أدخل قيمة واحدة من علامة تهاني SHA256 لكل سطر، بحد أقصى 20.
   - **لا تنتهي صلاحيتها** أبدا: يمكنك القيام بوا واحدة من الخطوات التالية:
     - تحقق من إيقاف تشغيل الإعداد (![إيقاف التشغيل).](../../media/scc-toggle-off.png)) ثم استخدم المربع إزالة عند التشغيل لتحديد  تاريخ انتهاء صلاحية الإدخالات.

     أو

     - نقل تبديل إلى اليمين لتكوين الإدخالات حتى لا تنتهي صلاحيتها أبدا: ![تبديل.](../../media/scc-toggle-on.png).
   - **ملاحظة اختيارية**: أدخل نصا وصفيا الإدخالات.

4. عند الانتهاء، انقر فوق **إضافة**.

> [!NOTE]
> سيتم حظر رسائل البريد الإلكتروني التي تحتوي على هذه الملفات *كبرامج ضارة*. 

### <a name="create-spoofed-sender-block-entries"></a>إنشاء إدخالات حظر المرسلين المنتحلين

**ملاحظات**:

- يتم السماح _فقط_ بالجمع بين المستخدم المهزوف والبنية الأساسية المرسلة كما هو محدد في زوج المجالات أو حظرها من التهزف.
- عندما تقوم بتكوين إدخال السماح أو الحظر لزوج مجال، لن تظهر الرسائل الواردة من زوج المجال هذا في تحليلات المعلومات المنتحلة.
- لا تنتهي صلاحية إدخالات المرسلين المزحلين أبدا.
- يدعم التهزأ كل من السماح والحظر.

1. في مدخل Microsoft 365 Defender، انتقل  إلى "**&** \>  \> \> قواعد سياسات التهديدات" في القسم **"قوائم السماح/الحظر**" للمستأجر.

2. في صفحة **قائمة السماح/** الحظر للمستأجر، **حدد علامة التبويب** انتحال، ثم انقر فوق أيقونة ![الحظر.](../../media/m365-cc-sc-create-icon.png) **إضافة**.

3. في **قائمة إضافة أزواج مجالات** جديدة التي تظهر، قم بتكوين الإعدادات التالية:
   - **إضافة أزواج مجالات جديدة باستخدام أحرف البدل**: أدخل زوج مجال واحد لكل سطر، بحد أقصى 20. للحصول على تفاصيل حول بناء جملة إدخالات المرسلين المنتحلين، راجع [إدارة قائمة السماح/الحظر](tenant-allow-block-list.md) للمستأجر.
   - **انتحال النوع**: حدد إحدى القيم التالية:
     - **داخلي**: يكون المرسل المنتحل في مجال ينتمي إلى مؤسستك ( [مجال مقبول](/exchange/mail-flow-best-practices/manage-accepted-domains/manage-accepted-domains)).
     - **خارجي**: المرسل المهزوف في مجال خارجي.
   - **الإجراء**: حدد **السماح** أو **الحظر**.

4. عند الانتهاء، انقر فوق **إضافة**.

## <a name="use-powershell"></a>استخدام PowerShell

### <a name="add-block-sender-file-or-url-entries-to-the-tenant-allowblock-list"></a>إضافة إدخالات مرسل الكتلة أو الملف أو URL إلى قائمة السماح/الحظر للمستأجر

لإضافة إدخالات مرسل الكتلة أو الملف أو URL في قائمة السماح/الحظر للمستأجر، استخدم بناء الجملة التالي:

```powershell
New-TenantAllowBlockListItems -ListType <Sender | FileHash | Url> -Block -Entries "Value1","Value2",..."ValueN" <-ExpirationDate Date | -NoExpiration> [-Notes <String>]
```

يضيف هذا المثال إدخال مرسل الحظر للمرسل المحدد تنتهي صلاحيته في تاريخ معين.

```powershell
New-TenantAllowBlockListItems -ListType Sender -Block -Entries "test@badattackerdomain.com", "test2@anotherattackerdomain.com" -ExpirationDate 8/20/2021
```

يضيف هذا المثال إدخال ملف حظر للملفات المحددة التي لا تنتهي صلاحيتها أبدا.

```powershell
New-TenantAllowBlockListItems -ListType FileHash -Block -Entries "768a813668695ef2483b2bde7cf5d1b2db0423a0d3e63e498f3ab6f2eb13ea3","2c0a35409ff0873cfa28b70b8224e9aca2362241c1f0ed6f622fef8d4722fd9a" -NoExpiration
```

يضيف هذا المثال إدخال عنوان URL حظرا contoso.com كافة المناطق الفرعية (على سبيل المثال، contoso.com www.contoso.com xyz.abc.contoso.com). نظرا لأننا لم نستخدم معلمات ExpirationDate أو NoExpiration، تنتهي صلاحية الإدخال بعد 30 يوما.

```powershell
New-TenantAllowBlockListItems -ListType Url -Block -Entries ~contoso.com
```

للحصول على معلومات مفصلة حول بناء الجملة والمعلمات، راجع [New-TenantAllowBlockListItems](/powershell/module/exchange/new-tenantallowblocklistitems).

### <a name="add-spoofed-sender-block-entries"></a>إضافة إدخالات حظر المرسلين المنتحلين 

لإضافة إدخالات المرسلين المنتحلين في قائمة السماح/الحظر للمستأجر، استخدم بناء الجملة التالي:

```powershell
New-TenantAllowBlockListSpoofItems -SpoofedUser <Domain | EmailAddress | *> -SendingInfrastructure <Domain | IPAddress/24> -SpoofType <External | Internal> -Action <Allow | Block>
```

للحصول على معلومات مفصلة حول بناء الجملة والمعلمات، راجع [New-TenantAllowBlockListSpoofItems](/powershell/module/exchange/new-tenantallowblocklistspoofitems).
