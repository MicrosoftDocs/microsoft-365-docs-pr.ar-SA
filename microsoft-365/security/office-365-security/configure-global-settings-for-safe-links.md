---
title: تكوين الإعدادات العمومية لإعدادات الارتباطات الآمنة في Defender لـ Office 365
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
description: يمكن للمسؤولين معرفة كيفية عرض الإعدادات العمومية وتكوينها (قائمة "حظر عناوين URL التالية" وحمايتها لتطبيقات Office 365) للارتباطات الآمنة في Microsoft Defender لـ Office 365.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 6c8b40109f20215b86a2264ed1a9f69c8db43bda
ms.sourcegitcommit: d1b60ed9a11f5e6e35fbaf30ecaeb9dfd6dd197d
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 06/29/2022
ms.locfileid: "66487554"
---
# <a name="configure-global-settings-for-safe-links-in-microsoft-defender-for-office-365"></a>تكوين الإعدادات العمومية للارتباطات الآمنة في Microsoft Defender لـ Office 365

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**ينطبق على**
- [خطة 1 وخطة 2 من Microsoft Defender لـ Office 365](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

> [!IMPORTANT]
> هذه المقالة مخصصة لعملاء الأعمال الذين لديهم [Microsoft Defender لـ Office 365](defender-for-office-365.md). إذا كنت مستخدما منزليا تبحث عن معلومات حول الارتباطات الآمنة في Outlook، فراجع [الأمان المتقدم Outlook.com](https://support.microsoft.com/office/882d2243-eab9-4545-a58a-b36fee4a46e2).

تعد الارتباطات الآمنة ميزة في [Microsoft Defender لـ Office 365](defender-for-office-365.md) توفر مسح URL لرسائل البريد الإلكتروني الواردة في تدفق البريد، ووقت التحقق من صحة عناوين URL والارتباطات في رسائل البريد الإلكتروني وفي مواقع أخرى. لمزيد من المعلومات، راجع ["الارتباطات الآمنة" في Microsoft Defender لـ Office 365](safe-links.md).

يمكنك تكوين معظم إعدادات الارتباطات الآمنة في نهج الارتباطات الآمنة. للحصول على الإرشادات، راجع [إعداد نهج الارتباطات الآمنة في Microsoft Defender لـ Office 365](set-up-safe-links-policies.md).

ولكن، تستخدم "الارتباطات الآمنة" أيضا الإعدادات العمومية التالية التي تقوم بتكوينها خارج نهج "الارتباطات الآمنة" نفسها:

- **قائمة "حظر عناوين URL" التالية**. ينطبق هذا الإعداد على كافة المستخدمين المضمنين في أي نهج ارتباطات آمنة نشطة. لمزيد من المعلومات، راجع [قائمة "حظر عناوين URL التالية" للارتباطات الآمنة](safe-links.md#block-the-following-urls-list-for-safe-links)

- حماية الارتباطات الآمنة لتطبيقات Office 365. تنطبق هذه الإعدادات على جميع المستخدمين في المؤسسة المرخص لهم Defender لـ Office 365، بغض النظر عما إذا كان المستخدمون مضمنين في نهج الارتباطات الآمنة النشطة أم لا. لمزيد من المعلومات، راجع [إعدادات الارتباطات الآمنة لتطبيقات Office 365](safe-links.md#safe-links-settings-for-office-365-apps).

يمكنك تكوين إعدادات "الارتباطات الآمنة" العمومية في مدخل Microsoft 365 Defender أو في PowerShell (Exchange Online PowerShell لمؤسسات Microsoft 365 المؤهلة التي لها علب بريد في Exchange Online؛ وEOP PowerShell مستقل للمؤسسات دون Exchange Online علب البريد، ولكن مع Microsoft Defender لـ Office 365 اشتراكات الوظائف الإضافية).

## <a name="what-do-you-need-to-know-before-you-begin"></a>ما الذي تحتاج إلى معرفته قبل البدء؟

- على الرغم من عدم وجود نهج افتراضي للارتباطات الآمنة، يوفر نهج الأمان المعين مسبقا **للحماية المضمنة** حماية الارتباطات الآمنة لجميع المستلمين (المستخدمين الذين لم يتم تعريفهم في نهج الارتباطات الآمنة المخصصة). لمزيد من المعلومات، راجع [نهج الأمان التي تم تعيينها مسبقا في EOP Microsoft Defender لـ Office 365](preset-security-policies.md). يمكنك أيضا إنشاء نهج ارتباطات آمنة لتطبيقها على مستخدمين أو مجموعات أو مجالات معينة. للحصول على الإرشادات، راجع [إعداد نهج الارتباطات الآمنة في Microsoft Defender لـ Office 365](set-up-safe-links-policies.md).

- يمكنك فتح مدخل Microsoft 365 Defender في <https://security.microsoft.com>. للانتقال مباشرة إلى صفحة **"الارتباطات الآمنة** "، استخدم <https://security.microsoft.com/safelinksv2>.

- للاتصال Exchange Online PowerShell، راجع [الاتصال Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell). للاتصال ب EOP PowerShell المستقل، راجع [الاتصال Exchange Online Protection PowerShell](/powershell/exchange/connect-to-exchange-online-protection-powershell).

- يجب تعيين أذونات لك في **Exchange Online** قبل أن تتمكن من تنفيذ الإجراءات الواردة في هذه المقالة:
  - لتكوين الإعدادات العمومية للارتباطات الآمنة، يجب أن تكون عضوا في مجموعات دور مسؤول **الأمان** أو **إدارة المؤسسة**.
  - للوصول للقراءة فقط إلى الإعدادات العمومية للارتباطات الآمنة، يجب أن تكون عضوا في مجموعات دور **القارئ العمومي** أو **قارئ الأمان** .

  لمزيد من المعلومات، راجع [الأذونات في Exchange Online](/exchange/permissions-exo/permissions-exo).

  **الملاحظات**:

  - إضافة مستخدمين إلى دور Azure Active Directory المقابل في مركز مسؤولي Microsoft 365 يمنح المستخدمين الأذونات _والأذونات_ المطلوبة للميزات الأخرى في Microsoft 365. لمزيد من المعلومات، راجع [حول أدوار المسؤولين](../../admin/add-users/about-admin-roles.md).
  - كما توفر مجموعة دور **إدارة المؤسسة للعرض فقط** في [Exchange Online](/Exchange/permissions-exo/permissions-exo#role-groups) إمكانية الوصول للقراءة فقط إلى الميزة.

- للحصول على القيم الموصى بها للإعدادات العمومية للارتباطات الآمنة، راجع [إعدادات الارتباطات الآمنة](recommended-settings-for-eop-and-office365.md#safe-links-settings).

- السماح بما يصل إلى 30 دقيقة لتطبيق نهج جديد أو محدث.

- [تتم إضافة ميزات جديدة باستمرار إلى Microsoft Defender لـ Office 365](defender-for-office-365.md#new-features-in-microsoft-defender-for-office-365). عند إضافة ميزات جديدة، قد تحتاج إلى إجراء تعديلات على نهج الارتباطات الآمنة الموجودة.

## <a name="configure-the-block-the-following-urls-list-in-the-microsoft-365-defender-portal"></a>تكوين قائمة "حظر عناوين URL التالية" في مدخل Microsoft 365 Defender

> [!NOTE]
> يمكنك الآن إدارة إدخالات عنوان URL للكتلة في [قائمة السماح/الحظر للمستأجر](allow-block-urls.md#create-block-url-entries-in-the-tenant-allowblock-list). قائمة "حظر عناوين URL التالية" قيد الإهمال. سنحاول ترحيل الإدخالات الموجودة من قائمة "حظر عناوين URL التالية" لحظر إدخالات URL في قائمة السماح/الحظر للمستأجر. سيتم عزل الرسائل التي تحتوي على عنوان URL المحظور.

تحدد قائمة **"حظر عناوين URL" التالية** الارتباطات التي يجب حظرها دائما بواسطة مسح الارتباطات الآمنة في التطبيقات المدعومة. لمزيد من المعلومات، راجع [قائمة "حظر عناوين URL التالية" للارتباطات الآمنة](safe-links.md#block-the-following-urls-list-for-safe-links).

1. في مدخل Microsoft 365 Defender، <https://security.microsoft.com>انتقل إلى **"نهج التعاون** \> & البريد الإلكتروني **" &** **"الارتباطات الآمنة** **لنهج** \> مخاطر القواعد\>" في قسم **"النهج**". للانتقال مباشرة إلى صفحة **"الارتباطات الآمنة** "، استخدم <https://security.microsoft.com/safelinksv2>.

2. في الصفحة **"ارتباطات آمنة** "، انقر فوق **الإعدادات العمومية**. في **نهج "الارتباطات الآمنة" لمؤسستك** الذي يظهر، انتقل إلى المربع **"حظر عناوين URL" التالية** .

3. تكوين إدخال واحد أو أكثر كما هو موضح في [بناء جملة الإدخال لقائمة "حظر عناوين URL التالية".](safe-links.md#entry-syntax-for-the-block-the-following-urls-list)

   عند الانتهاء، انقر فوق **حفظ**.

### <a name="configure-the-block-the-following-urls-list-in-powershell"></a>تكوين قائمة "حظر عناوين URL التالية" في PowerShell

للحصول على تفاصيل حول بناء جملة الإدخال، راجع [بناء جملة الإدخال لقائمة "حظر عناوين URL التالية".](safe-links.md#entry-syntax-for-the-block-the-following-urls-list)

يمكنك استخدام **Get-AtpPolicyForO365** cmdlet لعرض الإدخالات الموجودة في خاصية _BlockURLs_ .

- لإضافة قيم تحل محل أي إدخالات موجودة، استخدم بناء الجملة التالي في Exchange Online PowerShell أو Exchange Online Protection PowerShell:

  ```powershell
  Set-AtpPolicyForO365 -BlockUrls "Entry1","Entry2",..."EntryN"
  ```

  يضيف هذا المثال الإدخالات التالية إلى القائمة:

  - حظر المجال والمجالات الفرعية والمسارات fabrikam.com.
  - حظر بحث المجال الفرعي، ولكن ليس المجال الأصل أو المجالات الفرعية الأخرى في tailspintoys.com

  ```powershell
  Set-AtpPolicyForO365 -BlockUrls "fabrikam.com","https://research.tailspintoys.com*"
  ```

- لإضافة قيم أو إزالتها دون التأثير على إدخالات موجودة أخرى، استخدم بناء الجملة التالي:

  ```powershell
  Set-AtpPolicyForO365 -BlockUrls @{Add="Entry1","Entry2"...; Remove="Entry3","Entry4"...}
  ```

  يضيف هذا المثال إدخالا جديدا adatum.com، ويزيل الإدخال fabrikam.com.

  ```powershell
  Set-AtpPolicyForO365 -BlockUrls @{Add="adatum.com"; Remove="fabrikam"}
  ```

## <a name="configure-safe-links-protection-for-office-365-apps-in-the-microsoft-365-defender-portal"></a>تكوين حماية الارتباطات الآمنة لتطبيقات Office 365 في مدخل Microsoft 365 Defender

تنطبق حماية الارتباطات الآمنة لتطبيقات Office 365 على المستندات في تطبيقات Office لسطح المكتب والأجهزة المحمولة والويب المعتمدة. لمزيد من المعلومات، راجع [إعدادات الارتباطات الآمنة لتطبيقات Office 365](safe-links.md#safe-links-settings-for-office-365-apps).

1. في مدخل Microsoft 365 Defender، <https://security.microsoft.com>انتقل إلى **"نهج التعاون** \> & البريد الإلكتروني **" &** **"الارتباطات الآمنة** **لنهج** \> مخاطر القواعد\>" في قسم **"النهج**". للانتقال مباشرة إلى صفحة **"الارتباطات الآمنة** "، استخدم <https://security.microsoft.com/safelinksv2>.

2. في الصفحة **"ارتباطات آمنة** "، انقر فوق **الإعدادات العمومية**. في **نهج الارتباطات الآمنة لمؤسستك** الذي يظهر، قم بتكوين الإعدادات التالية في **الإعدادات التي تنطبق على المحتوى في قسم تطبيقات Office 365 المعتمدة**:

   - **استخدم "الارتباطات الآمنة" في تطبيقات Office 365**: تحقق من أن التبديل إلى اليسار لتمكين "الارتباطات الآمنة" لتطبيقات Office 365 المدعومة: ![التبديل.](../../media/scc-toggle-on.png)

   - **لا تتعقب عندما ينقر المستخدمون فوق الارتباطات المحمية في تطبيقات Office 365**: انقل التبديل إلى اليسار لتعقب نقرات المستخدم المتعلقة بعناوين URL المحظورة في تطبيقات Office 365 المعتمدة: ![قم بالتبديل.](../../media/scc-toggle-off.png)

   - **لا تسمح للمستخدمين بالنقر فوق عنوان URL الأصلي في تطبيقات Office 365**: تحقق من أن التبديل إلى اليسار لمنع المستخدمين من النقر فوق عنوان URL المحظور الأصلي في تطبيقات Office 365 المعتمدة: ![التبديل.](../../media/scc-toggle-on.png)

   عند الانتهاء، انقر فوق **حفظ**.

### <a name="configure-safe-links-protection-for-office-365-apps-in-powershell"></a>تكوين حماية الارتباطات الآمنة لتطبيقات Office 365 في PowerShell

إذا كنت تفضل استخدام PowerShell لتكوين حماية الارتباطات الآمنة لتطبيقات Office 365، فاستخدم بناء الجملة التالي في Exchange Online PowerShell أو Exchange Online Protection PowerShell:

```powershell
Set-AtpPolicyForO365 [-EnableSafeLinksForO365Clients <$true | $false> [-AllowClickThrough <$true | $false>] [-TrackClicks <$true | $false>]
```

يقوم هذا المثال بتكوين الإعدادات التالية لحماية الارتباطات الآمنة في تطبيقات Office 365:

- الارتباطات الآمنة لتطبيقات Office 365 قيد التشغيل (لا نستخدم المعلمة _EnableSafeLinksForO365Clients_، والقيمة الافتراضية هي $true).
- يتم تعقب نقرات المستخدم المتعلقة بعناوين URL المحظورة في تطبيقات Office 365 المدعومة.
- لا يسمح للمستخدمين بالنقر عبر عنوان URL المحظور الأصلي في تطبيقات Office 365 المعتمدة (لا نستخدم المعلمة _AllowClickThrough_، والقيمة الافتراضية $false).

```powershell
Set-AtpPolicyForO365 -TrackClicks $true
```

للحصول على معلومات مفصلة حول بناء الجملة والمعلمة، راجع [Set-AtpPolicyForO365](/powershell/module/exchange/set-atppolicyforo365).

## <a name="how-do-you-know-these-procedures-worked"></a>كيف تعرف أن هذه الإجراءات تعمل؟

للتحقق من تكوين الإعدادات العمومية للارتباطات الآمنة بنجاح (قائمة **حظر عناوين URL التالية** وإعدادات حماية تطبيق Office 365)، قم بأي من الخطوات التالية:

- في صفحة **"الارتباطات الآمنة**" في مدخل Microsoft 365 Defender، <https://security.microsoft.com/safelinksv2>انقر فوق **الإعدادات العمومية**، وتحقق من الإعدادات في القائمة المنبثقة التي تظهر.

- في Exchange Online PowerShell أو Exchange Online Protection PowerShell، قم بتشغيل الأمر التالي وتحقق من الإعدادات:

  ```powershell
  Get-AtpPolicyForO365 | Format-List BlockUrls,EnableSafeLinksForO365Clients,AllowClickThrough,TrackClicks
  ```

  للحصول على معلومات مفصلة حول بناء الجملة والمعلمة، راجع [Get-AtpPolicyForO365](/powershell/module/exchange/get-atppolicyforo365).
