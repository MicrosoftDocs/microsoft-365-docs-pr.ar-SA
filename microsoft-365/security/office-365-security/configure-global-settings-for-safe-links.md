---
title: تكوين الإعدادات العالمية لإعدادات خزينة ارتباطات في Defender for Office 365
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
audience: Admin
ms.topic: how-to
ms.date: ''
ms.localizationpriority: medium
search.appverid:
- MET150
- MOE150
ms.assetid: ''
ms.collection:
- M365-security-compliance
ms.custom: ''
description: يمكن للمسؤولين التعرف على كيفية عرض الإعدادات العالمية وتكوينها (قائمة 'حظر عناوين URL التالية' والحماية لتطبيقات Office 365) ل ارتباطات خزينة في Microsoft Defender Office 365.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 857519e93df9490ebeb178a23a44ddddbdfc83ef
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 01/12/2022
ms.locfileid: "63575406"
---
# <a name="configure-global-settings-for-safe-links-in-microsoft-defender-for-office-365"></a>تكوين الإعدادات خزينة ارتباطات في Microsoft Defender Office 365

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**ينطبق على**
- [Microsoft Defender Office 365 الخطة 1 الخطة 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

> [!IMPORTANT]
> هذه المقالة مخصصة لعملاء الأعمال الذين لديهم [Microsoft Defender Office 365](defender-for-office-365.md). إذا كنت مستخدما منزليا تبحث عن معلومات حول الارتباطات الآمنة في Outlook، فاطلع على [أمان Outlook.com المتقدم](https://support.microsoft.com/office/882d2243-eab9-4545-a58a-b36fee4a46e2).

خزينة الارتباطات هي ميزة في [Microsoft Defender ل Office 365](defender-for-office-365.md) توفر فحص URL لرسائل البريد الإلكتروني الواردة في تدفق البريد، والوقت الذي يتم فيه التحقق من عناوين URL والارتباطات بالنقر فوقها في رسائل البريد الإلكتروني وفي مواقع أخرى. لمزيد من المعلومات، راجع خزينة [ارتباطات في Microsoft Defender Office 365](safe-links.md).

تقوم بتكوين معظم خزينة الارتباطات في خزينة الارتباطات. للحصول على الإرشادات، [راجع إعداد خزينة الارتباطات في Microsoft Defender Office 365](set-up-safe-links-policies.md).

ولكن خزينة الارتباطات تستخدم أيضا الإعدادات العامة التالية التي تقوم بتكوينها خارج خزينة الارتباطات نفسها:

- القائمة **حظر عناوين URL** التالية. ينطبق هذا الإعداد على جميع المستخدمين المضمنين في أي خزينة ارتباطات نشطة. لمزيد من المعلومات، راجع [القائمة "حظر عناوين URL التالية" خزينة الارتباطات](safe-links.md#block-the-following-urls-list-for-safe-links)
- خزينة الارتباطات Office 365 التطبيقات. تنطبق هذه الإعدادات على جميع المستخدمين في المؤسسة المرخص لهم ل Defender for Office 365، بغض النظر عما إذا كان المستخدمون مضمنين في خزينة الارتباطات النشطة أم لا. لمزيد من المعلومات، [راجع خزينة الارتباطات لتطبيقات Office 365.](safe-links.md#safe-links-settings-for-office-365-apps)

يمكنك تكوين إعدادات ارتباطات خزينة العامة في مدخل Microsoft 365 Defender أو في PowerShell (Exchange Online PowerShell لمنظمات Microsoft 365 المؤهلة التي لها علب بريد في Exchange Online؛ EOP PowerShell مستقل ل المؤسسات بدون Exchange Online علب البريد، ولكن باستخدام Microsoft Defender Office 365 الإضافية).

## <a name="what-do-you-need-to-know-before-you-begin"></a>ما الذي تحتاج إلى معرفته قبل البدء؟

- على الرغم من عدم وجود نهج خزينة ارتباطات افتراضي، إلا أن  نهج الأمان المضمن للحماية المسبقة يوفر حماية ارتباطات خزينة لكل المستلمين (المستخدمون غير المحددين في نهج ارتباطات خزينة المخصصة). لمزيد من المعلومات، راجع [سياسات الأمان التي تم الإعداد المسبق لها في EOP و Microsoft Defender Office 365](preset-security-policies.md). يمكنك أيضا إنشاء خزينة الارتباطات لتطبيقها على مستخدمين معينين أو مجموعة أو مجالات معينة. للحصول على الإرشادات، [راجع إعداد خزينة الارتباطات في Microsoft Defender Office 365](set-up-safe-links-policies.md).

- يمكنك فتح Microsoft 365 Defender في <https://security.microsoft.com>. الانتقال مباشرة إلى صفحة ارتباطات خزينة **،** استخدم <https://security.microsoft.com/safelinksv2>.

- للاتصال ب PowerShell Exchange Online، راجع الاتصال [إلى Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell). للاتصال ب EOP PowerShell مستقل، راجع الاتصال [Exchange Online Protection PowerShell](/powershell/exchange/connect-to-exchange-online-protection-powershell).

- يجب تعيين أذونات لك في Exchange Online قبل أن تتمكن  من تنفيذ الإجراءات في هذه المقالة:
  - لتكوين الإعدادات العامة خزينة الارتباطات، يجب أن تكون عضوا في مجموعات دور مسؤول إدارة **المؤسسة أو مسؤول** الأمان.
  - للوصول للقراءة فقط إلى الإعدادات خزينة الارتباطات، يجب أن تكون عضوا في مجموعات دور القارئ العام أو قارئ الأمان. 

  لمزيد من المعلومات، راجع [الأذونات في Exchange Online](/exchange/permissions-exo/permissions-exo).

  **ملاحظات**:

  - توفر إضافة مستخدمين إلى دور Azure Active Directory المناظر في مركز مسؤولي Microsoft 365 للمستخدمين الأذونات والأذونات المطلوبة للميزات الأخرى  في Microsoft 365. لمزيد من المعلومات، راجع [حول أدوار المسؤولين](../../admin/add-users/about-admin-roles.md).
  - توفر **أيضا مجموعة دور "** إدارة [المؤسسات Exchange Online](/Exchange/permissions-exo/permissions-exo#role-groups) طريقة العرض فقط" إمكانية الوصول للقراءة فقط إلى الميزة.

- للحصول على القيم الموصى بها لإعدادات خزينة الارتباطات، راجع خزينة [الارتباطات](recommended-settings-for-eop-and-office365.md#safe-links-settings).

- السماح بتطبيق نهج جديد أو محدث لمدة تصل إلى 30 دقيقة.

- [يتم باستمرار إضافة الميزات الجديدة إلى Microsoft Defender Office 365](defender-for-office-365.md#new-features-in-microsoft-defender-for-office-365). عند إضافة ميزات جديدة، قد تحتاج إلى إجراء تعديلات على سياسات الارتباطات خزينة الموجودة.

## <a name="configure-the-block-the-following-urls-list-in-the-microsoft-365-defender-portal"></a>تكوين القائمة "حظر عناوين URL التالية" في مدخل Microsoft 365 Defender

تحدد **القائمة حظر عناوين URL** التالية الارتباطات التي يجب حظرها دائما بواسطة خزينة الارتباطات في التطبيقات المعتمدة. لمزيد من المعلومات، راجع [القائمة "حظر عناوين URL التالية" خزينة الارتباطات](safe-links.md#block-the-following-urls-list-for-safe-links).

1. في Microsoft 365 Defender على <https://security.microsoft.com>، انتقل إلى  البريد الإلكتروني **&** \>  \> \> سياسات التعاون & قواعد خزينة **الارتباطات** في **القسم "سياسات**". الانتقال مباشرة إلى صفحة ارتباطات خزينة **،** استخدم <https://security.microsoft.com/safelinksv2>.

2. في صفحة **خزينة الارتباطات**، انقر فوق **إعدادات عام**. في خزينة **ارتباطات** المؤسسة التي تظهر، انتقل إلى المربع حظر عناوين **URL** التالية.

3. تكوين إدخال واحد أو أكثر كما هو موضح في بناء جملة الإدخال [للقائمة "حظر عناوين URL التالية](safe-links.md#entry-syntax-for-the-block-the-following-urls-list)".

   عند الانتهاء، انقر فوق **حفظ**.

### <a name="configure-the-block-the-following-urls-list-in-powershell"></a>تكوين القائمة "حظر عناوين URL التالية" في PowerShell

للحصول على تفاصيل حول بناء جملة الإدخال، راجع بناء جملة الإدخال [للقائمة "حظر عناوين URL التالية](safe-links.md#entry-syntax-for-the-block-the-following-urls-list)".

يمكنك استخدام **الأمر Cmdlet Get-AtpPolicyForO365** لعرض الإدخالات الموجودة في الخاصية _BlockURLs_ .

- لإضافة قيم ستحل محل أي إدخالات موجودة، استخدم بناء الجملة التالي في Exchange Online PowerShell أو Exchange Online Protection PowerShell:

  ```powershell
  Set-AtpPolicyForO365 -BlockUrls "Entry1","Entry2",..."EntryN"
  ```

  يضيف هذا المثال الإدخالات التالية إلى القائمة:

  - حظر المجال والمجالات الفرعية والمسارات fabrikam.com.
  - حظر أبحاث المجال الفرعي، وليس المجال الأصل أو المجالات الفرعية الأخرى في tailspintoys.com

  ```powershell
  Set-AtpPolicyForO365 -BlockUrls "fabrikam.com","https://research.tailspintoys.com*"
  ```

- لإضافة قيم أو إزالتها دون التأثير على الإدخالات الأخرى الموجودة، استخدم بناء الجملة التالي:

  ```powershell
  Set-AtpPolicyForO365 -BlockUrls @{Add="Entry1","Entry2"...; Remove="Entry3","Entry4"...}
  ```

  يضيف هذا المثال إدخالا جديدا adatum.com، ويزيل الإدخال fabrikam.com.

  ```powershell
  Set-AtpPolicyForO365 -BlockUrls @{Add="adatum.com"; Remove="fabrikam"}
  ```

## <a name="configure-safe-links-protection-for-office-365-apps-in-the-microsoft-365-defender-portal"></a>تكوين خزينة الارتباطات لتطبيقات Office 365 في مدخل Microsoft 365 Defender

خزينة حماية الارتباطات Office 365 التطبيقات على المستندات في تطبيقات Office سطح المكتب والأجهزة المحمولة وتطبيقات الويب المعتمدة. لمزيد من المعلومات، [راجع خزينة الارتباطات لتطبيقات Office 365.](safe-links.md#safe-links-settings-for-office-365-apps)

1. في Microsoft 365 Defender على <https://security.microsoft.com>، انتقل إلى  البريد الإلكتروني **&** \>  \> \> سياسات التعاون & قواعد خزينة **الارتباطات** في **القسم "سياسات**". الانتقال مباشرة إلى صفحة ارتباطات خزينة **،** استخدم <https://security.microsoft.com/safelinksv2>.

2. في صفحة **خزينة الارتباطات**، انقر فوق **إعدادات عام**. في **خزينة** ارتباطات المؤسسة التي تظهر، قم بتكوين الإعدادات التالية في الإعدادات التي تنطبق على المحتوى في قسم تطبيقات **Office 365 المعتمدة**:

   - **استخدم خزينة الارتباطات في تطبيقات** Office 365: تحقق من أن تبديل هو إلى اليمين لتمكين ارتباطات خزينة لتطبيقات Office 365 المعتمدة: ![تشغيل.](../../media/scc-toggle-on.png).

   - لا تتعقب عندما ينقر المستخدمون فوق الارتباطات المحمية في تطبيقات **Office 365**: حرك زر تبديل إلى اليمين لتعقب نقرات المستخدم المرتبطة عناوين URL المحظورة في تطبيقات Office 365 المعتمدة: ![إيقاف التشغيل.](../../media/scc-toggle-off.png)

   - لا تدع المستخدمين ينقرون عبر عنوان URL الأصلي في تطبيقات **Office 365**: تحقق من أن زر تبديل هو إلى اليمين لمنع المستخدمين من النقر فوق عنوان URL المحظور الأصلي في تطبيقات Office 365 المعتمدة: ![تشغيل.](../../media/scc-toggle-on.png).

   عند الانتهاء، انقر فوق **حفظ**.

### <a name="configure-safe-links-protection-for-office-365-apps-in-powershell"></a>تكوين خزينة حماية الارتباطات لتطبيقات Office 365 في PowerShell

إذا كنت تفضل استخدام PowerShell لتكوين حماية ارتباطات خزينة لتطبيقات Office 365، فاستخدم بناء الجملة التالي في Exchange Online PowerShell أو Exchange Online Protection PowerShell:

```powershell
Set-AtpPolicyForO365 [-EnableSafeLinksForO365Clients <$true | $false> [-AllowClickThrough <$true | $false>] [-TrackClicks <$true | $false>]
```

يضبط هذا المثال الإعدادات التالية لحماية خزينة الارتباطات في Office 365 التالية:

- خزينة ارتباطات Office 365 تطبيقات الويب (لا نستخدم المعلمة _EnableSafeLinksForO365Clients_، والقيمة الافتراضية $true).
- ينقر المستخدم فوق عناوين URL المحظورة في Office 365 تطبيقات متعقبة.
- لا يسمح للمستخدمين بالنقر عبر عنوان URL المحظور الأصلي في تطبيقات Office 365 المعتمدة (لا نستخدم المعلمة _AllowClickThrough_، والقيمة الافتراضية $false).

```powershell
Set-AtpPolicyForO365 -TrackClicks $true
```

للحصول على بناء الجملة المفصل ومعلومات المعلمة، راجع [Set-AtpPolicyForO365](/powershell/module/exchange/set-atppolicyforo365).

## <a name="how-do-you-know-these-procedures-worked"></a>كيف يمكنك معرفة كيفية عمل هذه الإجراءات؟

للتحقق من أنك قمت بتكوين الإعدادات العالمية ل ارتباطات خزينة (القائمة حظر عناوين **URL** التالية وإعدادات حماية تطبيق Office 365)، قم بأي من الخطوات التالية:

- في صفحة **خزينة** <https://security.microsoft.com/safelinksv2>الارتباطات في Microsoft 365 Defender في ، انقر فوق إعدادات عام، وتحقق من الإعدادات في القائمة المطيرة التي تظهر.

- في Exchange Online PowerShell أو Exchange Online Protection PowerShell، يمكنك تشغيل الأمر التالي والتحقق من الإعدادات:

  ```powershell
  Get-AtpPolicyForO365 | Format-List BlockUrls,EnableSafeLinksForO365Clients,AllowClickThrough,TrackClicks
  ```

  للحصول على معلومات مفصلة حول بناء الجملة والمعلمات، راجع [Get-AtpPolicyForO365](/powershell/module/exchange/get-atppolicyforo365).
