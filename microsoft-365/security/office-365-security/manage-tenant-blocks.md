---
title: إدارة الكتل في قائمة السماح/الحظر للمستأجر
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
description: يمكن للمسؤولين معرفة كيفية تكوين الكتل في قائمة السماح/الحظر للمستأجر في مدخل الأمان.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 60038a2b82ea452ed921d16042cb81d4f0e023a9
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/27/2022
ms.locfileid: "65100644"
---
# <a name="add-blocks-in-the-tenant-allowblock-list"></a>إضافة كتل في قائمة السماح/الحظر للمستأجر

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**ينطبق على**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [خطة 1 وخطة 2 من Microsoft Defender لـ Office 365](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

## <a name="use-the-microsoft-365-defender-portal"></a>استخدام مدخل Microsoft 365 Defender 

### <a name="create-block-sender-entries-in-the-tenant-allowblock-list"></a>إنشاء إدخالات مرسل الحظر في قائمة السماح/الحظر للمستأجر

1. في مدخل Microsoft 365 Defender، انتقل إلى **"نهج & قواعد قواعد** \> **نهج التهديد** \> **" قسم** "\>**السماح/حظر القوائم للمستأجر**".

2. في الصفحة **"السماح بالمستأجر/قائمة الحظر** "، تحقق من تحديد علامة التبويب **"المرسلون** "، ثم انقر فوق ![أيقونة "حظر".](../../media/m365-cc-sc-create-icon.png) **كتلة**.

3. في القائمة المنبثقة **"حظر المرسلين** " التي تظهر، قم بتكوين الإعدادات التالية:
   - **عناوين البريد الإلكتروني أو المجالات الخاصة بالمرسل**: أدخل مرسلا واحدا (عنوان البريد الإلكتروني أو المجال) لكل سطر، بحد أقصى 20.
   - **لا تنتهي صلاحيتها أبدا**: نفذ إحدى الخطوات التالية:
     - تحقق من إيقاف تشغيل الإعداد (![إيقاف التشغيل.](../../media/scc-toggle-off.png)) واستخدم المربع **"إزالة في** " لتحديد تاريخ انتهاء صلاحية الإدخالات.

       او

     - انقل التبديل إلى اليمين لتكوين الإدخالات بحيث لا تنتهي صلاحيتها أبدا: ![تشغيل التشغيل.](../../media/scc-toggle-on.png).
   - **ملاحظة اختيارية**: أدخل نصا وصفيا للإدخالات.

4. عند الانتهاء، انقر فوق **"إضافة**".

> [!NOTE]
> سيتم حظر رسائل البريد الإلكتروني الواردة من هؤلاء المرسلين *كبرم عشوائي عالي الثقة (SCL = 9).* 

### <a name="create-block-url-entries-in-the-tenant-allowblock-list"></a>إنشاء إدخالات عنوان URL للكتلة في قائمة السماح/الحظر للمستأجر

1. في مدخل Microsoft 365 Defender، انتقل إلى **"نهج & قواعد قواعد** \> **نهج التهديد** \> **" قسم** "\>**السماح/حظر القوائم للمستأجر**".

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
> سيتم حظر رسائل البريد الإلكتروني التي تحتوي على عناوين URL هذه على أنها *تصيد احتيالي*. 

### <a name="create-block-file-entries-in-the-tenant-allowblock-list"></a>إنشاء إدخالات ملفات الحظر في قائمة السماح/الحظر للمستأجر

1. في مدخل Microsoft 365 Defender، انتقل إلى **"نهج & قواعد قواعد** \> **نهج التهديد** \> **" قسم** "\>**السماح/حظر القوائم للمستأجر**".

2. في الصفحة **"السماح بالمستأجر/قائمة الحظر** "، حدد علامة التبويب **"ملفات** "، ثم انقر فوق ![أيقونة "حظر".](../../media/m365-cc-sc-create-icon.png) **كتلة**.

3. في القائمة المنبثقة **لملفات الحظر** التي تظهر، قم بتكوين الإعدادات التالية:
   - **إضافة تجزئة الملف**: أدخل قيمة تجزئة SHA256 واحدة لكل سطر، بحد أقصى 20.
   - **لا تنتهي صلاحيتها أبدا**: نفذ إحدى الخطوات التالية:
     - تحقق من إيقاف تشغيل الإعداد (![إيقاف التشغيل.](../../media/scc-toggle-off.png)) واستخدم المربع **"إزالة في** " لتحديد تاريخ انتهاء صلاحية الإدخالات.

     او

     - انقل التبديل إلى اليمين لتكوين الإدخالات بحيث لا تنتهي صلاحيتها أبدا: ![تشغيل التشغيل.](../../media/scc-toggle-on.png).
   - **ملاحظة اختيارية**: أدخل نصا وصفيا للإدخالات.

4. عند الانتهاء، انقر فوق **"إضافة**".

> [!NOTE]
> سيتم حظر رسائل البريد الإلكتروني التي تحتوي على هذه الملفات *كالبرمجيات الضارة*. 

### <a name="create-spoofed-sender-block-entries"></a>إنشاء إدخالات كتلة مرسل منتحلة

**الملاحظات**:

- يسمح فقط _بمزيج_ المستخدم المخادعة _والبنية_ الأساسية المرسلة كما هو محدد في زوج المجال أو حظره من الانتحال.
- عند تكوين إدخال السماح أو الحظر لزوج مجال، لن تظهر الرسائل الواردة من زوج المجال هذا في نتيجة التحليل الذكي المخادعة.
- لا تنتهي صلاحية إدخالات المرسلين المخادعة أبدا.
- يدعم الانتحال كلا من السماح والحظر.

1. في مدخل Microsoft 365 Defender، انتقل إلى **"نهج & قواعد قواعد** \> **نهج التهديد** \> **" قسم** "\>**السماح/حظر القوائم للمستأجر**".

2. في صفحة **"السماح بالمستأجر/قائمة الحظر** "، حدد علامة التبويب **"تزييف هوية** "، ثم انقر فوق ![أيقونة "حظر".](../../media/m365-cc-sc-create-icon.png) **إضافة**.

3. في القائمة المنبثقة **"إضافة أزواج مجالات جديدة** " التي تظهر، قم بتكوين الإعدادات التالية:
   - **إضافة أزواج مجالات جديدة باستخدام أحرف البدل**: أدخل زوج مجال واحد لكل سطر، بحد أقصى 20 زوجا. للحصول على تفاصيل حول بناء الجملة لإدخالات المرسلين المخادعة، راجع [إدارة قائمة السماح/الحظر للمستأجر](tenant-allow-block-list.md).
   - **نوع الانتحال**: حدد إحدى القيم التالية:
     - **داخلي**: المرسل المخادع موجود في مجال ينتمي إلى مؤسستك ( [مجال مقبول](/exchange/mail-flow-best-practices/manage-accepted-domains/manage-accepted-domains)).
     - **خارجي**: المرسل المخادع موجود في مجال خارجي.
   - **الإجراء**: حدد **كتلة**.

4. عند الانتهاء، انقر فوق **"إضافة**".
> [!NOTE]
> سيتم حظر رسائل البريد الإلكتروني الواردة من هؤلاء المرسلين على أنها *تصيد احتيالي*. 

## <a name="use-powershell"></a>استخدام PowerShell

### <a name="add-block-sender-file-or-url-entries-to-the-tenant-allowblock-list"></a>إضافة إدخالات مرسل الحظر أو الملف أو URL إلى قائمة السماح/الحظر للمستأجر

لإضافة إدخالات مرسل أو ملف أو عنوان URL للكتلة في قائمة السماح/الحظر للمستأجر، استخدم بناء الجملة التالي:

```powershell
New-TenantAllowBlockListItems -ListType <Sender | FileHash | Url> -Block -Entries "Value1","Value2",..."ValueN" <-ExpirationDate Date | -NoExpiration> [-Notes <String>]
```

يضيف هذا المثال إدخال مرسل حظر للمرسل المحدد الذي تنتهي صلاحيته في تاريخ معين.

```powershell
New-TenantAllowBlockListItems -ListType Sender -Block -Entries "test@badattackerdomain.com", "test2@anotherattackerdomain.com" -ExpirationDate 8/20/2021
```

يضيف هذا المثال إدخال ملف حظر للملفات المحددة التي لا تنتهي صلاحيتها أبدا.

```powershell
New-TenantAllowBlockListItems -ListType FileHash -Block -Entries "768a813668695ef2483b2bde7cf5d1b2db0423a0d3e63e498f3ab6f2eb13ea3","2c0a35409ff0873cfa28b70b8224e9aca2362241c1f0ed6f622fef8d4722fd9a" -NoExpiration
```

يضيف هذا المثال إدخال URL كتلة contoso.com وكافة المجالات الفرعية (على سبيل المثال، contoso.com www.contoso.com xyz.abc.contoso.com). نظرا لأننا لم نستخدم معلمات ExpirationDate أو NoExpiration، تنتهي صلاحية الإدخال بعد 30 يوما.

```powershell
New-TenantAllowBlockListItems -ListType Url -Block -Entries ~contoso.com
```

للحصول على معلومات مفصلة حول بناء الجملة والمعلمة، راجع [New-TenantAllowBlockListItems](/powershell/module/exchange/new-tenantallowblocklistitems).

### <a name="add-spoofed-sender-block-entries"></a>إضافة إدخالات كتلة مرسل منتحلة 

لإضافة إدخالات المرسل المخادعة في قائمة السماح/الحظر للمستأجر، استخدم بناء الجملة التالي:

```powershell
New-TenantAllowBlockListSpoofItems -SpoofedUser <Domain | EmailAddress | *> -SendingInfrastructure <Domain | IPAddress/24> -SpoofType <External | Internal> -Action <Allow | Block>
```

للحصول على معلومات مفصلة حول بناء الجملة والمعلمة، راجع [New-TenantAllowBlockListSpoofItems](/powershell/module/exchange/new-tenantallowblocklistspoofitems).
