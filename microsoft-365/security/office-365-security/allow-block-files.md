---
title: السماح بالملفات أو حظرها باستخدام قائمة السماح/الحظر للمستأجر
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
description: يمكن للمسؤولين معرفة كيفية السماح بالملفات أو حظرها في قائمة السماح/الحظر للمستأجر في مدخل الأمان.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: a85af4beda791fb9cc2382a48a701406941d0325
ms.sourcegitcommit: 7df8adc9e67ab65e413d7ea7bb0dcb9fd2da1a11
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 06/21/2022
ms.locfileid: "66857415"
---
# <a name="allow-or-block-files-using-the-tenant-allowblock-list"></a>السماح بالملفات أو حظرها باستخدام قائمة السماح/الحظر للمستأجر

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**ينطبق على**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [خطة 1 وخطة 2 من Microsoft Defender لـ Office 365](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

يمكنك استخدام مدخل Microsoft 365 Defender أو PowerShell للسماح بالملفات أو حظرها في قائمة السماح/الحظر للمستأجر.

## <a name="create-block-file-entries"></a>إنشاء إدخالات ملفات الحظر 

### <a name="use-microsoft-365-defender"></a>استخدام Microsoft 365 Defender

1. في مدخل Microsoft 365 Defender، <https://security.microsoft.com>انتقل إلى **"نهج & قواعد قواعد** \> **نهج التهديد** \> **" قسم** \> **"السماح/حظر القوائم للمستأجر**". أو للانتقال مباشرة إلى صفحة **"السماح بالمستأجر/قائمة الحظر** "، استخدم <https://security.microsoft.com/tenantAllowBlockList>.

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
> سيتم حظر رسائل البريد الإلكتروني التي تحتوي على هذه الملفات _كالبرمجيات الضارة_.

### <a name="use-powershell"></a>استخدام PowerShell

لإضافة إدخالات ملف الكتلة في قائمة السماح/الحظر للمستأجر، استخدم بناء الجملة التالي:

```powershell
New-TenantAllowBlockListItems -ListType <FileHash> -Block -Entries "Value1","Value2",..."ValueN" <-ExpirationDate Date | -NoExpiration> [-Notes <String>]
```

يضيف هذا المثال إدخال ملف حظر للملفات المحددة التي لا تنتهي صلاحيتها أبدا.

```powershell
New-TenantAllowBlockListItems -ListType FileHash -Block -Entries "768a813668695ef2483b2bde7cf5d1b2db0423a0d3e63e498f3ab6f2eb13ea3","2c0a35409ff0873cfa28b70b8224e9aca2362241c1f0ed6f622fef8d4722fd9a" -NoExpiration
```

للحصول على معلومات مفصلة حول بناء الجملة والمعلمة، راجع [New-TenantAllowBlockListItems](/powershell/module/exchange/new-tenantallowblocklistitems).

## <a name="create-allow-file-entries"></a>إنشاء إدخالات الملفات المسموح بها

### <a name="use-microsoft-365-defender"></a>استخدام Microsoft 365 Defender

السماح بالملفات في صفحة **عمليات الإرسال** في Microsoft 365 Defender.

1. في مدخل Microsoft 365 Defender، <https://security.microsoft.com>انتقل إلى **عمليات الإرسال** \> & الإجراءات **.** أو للانتقال مباشرة إلى صفحة **عمليات الإرسال** ، استخدم <https://security.microsoft.com/reportsubmission>.

2. في الصفحة **"عمليات الإرسال"** ، حدد علامة التبويب **"مرفقات البريد الإلكتروني** "، ثم انقر فوق " ![إرسال إلى Microsoft" للتحليل.](../../media/m365-cc-sc-create-icon.png) **إرسال إلى Microsoft للتحليل**.

3. استخدم القائمة المنبثقة " **إرسال إلى Microsoft" للمراجعة** لإرسال رسالة عن طريق إضافة الملف أو الملفات.

4. في **"تحديد سبب الإرسال إلى قسم Microsoft** "، حدد **"يجب ألا يكون قد تم حظره (إيجابية خاطئة)**".

5. قم بتشغيل **السماح بالملفات مثل هذا** الخيار.

6. من القائمة المنسدلة **"إزالة بعد** "، حدد المدة التي تريد أن يعمل فيها خيار السماح.

7. أضف سبب إضافة السماح باستخدام **الملاحظة الاختيارية**. 

8. عند الانتهاء، انقر فوق الزر **"إرسال** ".

  :::image type="content" source="../../media/submit-email-for-analysis.png" alt-text="إرسال البريد الإلكتروني للتحليل." lightbox="../../media/submit-email-for-analysis.png":::

> [!NOTE]
>
> عندما تتم مصادفة الملف مرة أخرى، لا يتم إرساله للتدقيق في السمعة أو الحذف، ويتم تخطي جميع عوامل التصفية الأخرى المستندة إلى الملفات. أثناء تدفق البريد، إذا وجدت بقية عوامل التصفية أن البريد الإلكتروني الذي يحتوي على الملف نظيفا، فسيتم تسليم البريد الإلكتروني.

## <a name="view-file-entries"></a>عرض إدخالات الملف 

لعرض إدخالات ملف الحظر في قائمة السماح/الحظر للمستأجر، استخدم بناء الجملة التالي:

```powershell
Get-TenantAllowBlockListItems -ListType <FileHash> [-Entry <SenderValue | FileHashValue | URLValue>] [<-ExpirationDate Date | -NoExpiration>]
```

يقوم هذا المثال بإرجاع معلومات لقيمة تجزئة الملف المحددة.

```powershell
Get-TenantAllowBlockListItems -ListType FileHash -Entry "9f86d081884c7d659a2feaa0c55ad015a3bf4f1b2b0b822cd15d6c15b0f00a08"
```

للحصول على معلومات مفصلة حول بناء الجملة والمعلمة، راجع [Get-TenantAllowBlockListItems](/powershell/module/exchange/get-tenantallowblocklistitems).

## <a name="modify-file-entries"></a>تعديل إدخالات الملفات

لتعديل إدخالات الملفات المسموح بها أو حظرها في قائمة السماح/الحظر للمستأجر، استخدم بناء الجملة التالي:

```powershell
Set-TenantAllowBlockListItems -ListType <FileHash> -Ids <"Id1","Id2",..."IdN"> [<-ExpirationDate Date | -NoExpiration>] [-Notes <String>]
```

للحصول على معلومات مفصلة حول بناء الجملة والمعلمة، راجع [Set-TenantAllowBlockListItems](/powershell/module/exchange/set-tenantallowblocklistitems).

## <a name="remove-file-entries"></a>إزالة إدخالات الملف 

لإزالة إدخالات الملفات المسموح بها أو حظرها من قائمة السماح/الحظر للمستأجر، استخدم بناء الجملة التالي:

```powershell
Remove-TenantAllowBlockListItems -ListType <FileHash> -Ids <"Id1","Id2",..."IdN">
```

للحصول على معلومات مفصلة حول بناء الجملة والمعلمة، راجع [Remove-TenantAllowBlockListItems](/powershell/module/exchange/remove-tenantallowblocklistitems).

## <a name="related-articles"></a>المقالات ذات الصلة

- [عمليات إرسال المسؤول](admin-submission.md)
- [الإبلاغ عن الإيجابيات الخاطئة والسلبيات الخاطئة](report-false-positives-and-false-negatives.md)
- [إدارة السمحات والكتل في قائمة السماح/الحظر للمستأجر](manage-tenant-allow-block-list.md)
- [السماح برسائل البريد الإلكتروني أو حظرها في قائمة السماح/الحظر للمستأجر](allow-block-email-spoof.md)
- [السماح بعناوين URL أو حظرها في قائمة السماح/الحظر للمستأجر](allow-block-urls.md)
