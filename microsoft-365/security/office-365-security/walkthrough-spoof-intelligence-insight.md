---
title: إدارة المرسلين المخادعين باستخدام نهج التحليل الذكي المخادعة والرؤى الذكية المنتحلة
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: overview
ms.localizationpriority: medium
search.appverid:
- MET150
- MOE150
ms.assetid: 59a3ecaf-15ed-483b-b824-d98961d88bdd
ms.collection:
- M365-security-compliance
description: يمكن للمسؤولين معرفة كيفية استخدام نهج التحليل الذكي المخادعة والرؤى الذكية المخادعة للسماح بالمرسلين المخادعة المكتشفين أو حظرهم.
ms.custom:
- seo-marvel-apr2020
ms.technology: mdo
ms.prod: m365-security
ROBOTS: NOINDEX, NOFOLLOW
ms.openlocfilehash: 55ed1bd871d78c6d130a933799ec3f62d36d7736
ms.sourcegitcommit: 58ec09f1fd66af9717dc2743585d06d358ec7360
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/30/2022
ms.locfileid: "65144652"
---
# <a name="manage-spoofed-senders-using-the-spoof-intelligence-policy-and-spoof-intelligence-insight-in-eop"></a>إدارة المرسلين المخادعين باستخدام نهج التحليل الذكي المخادعة والرؤى الذكية المنتحلة في EOP

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**ينطبق على**
- [خطة 1 وخطة 2 من Microsoft Defender لـ Office 365](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

> [!IMPORTANT]
> تتوفر الآن إدارة المرسلين المخادعة في مدخل Microsoft 365 Defender فقط على علامة تبويب **الانتحال** في قائمة السماح/الحظر للمستأجر. للاطلاع على الإجراءات الحالية في مدخل Microsoft 365 Defender، راجع [التحليل الذكي للانتحال في EOP](learn-about-spoof-intelligence.md).
>
> إدارة المرسلين المخادعة في Exchange Online PowerShell أو EOP PowerShell المستقل قيد الترحيل حصريا إلى **\*cmdlets -TenantAllowBlockListSpoofItems** و **Get-SpoofIntelligenceInsight** و **Get-SpoofMailReport** cmdlets. للاطلاع على الإجراءات التي تستخدم أوامر cmdlets هذه، راجع المقالات التالية:
>
> - [عرض إدخالات المرسلين المخادعة باستخدام PowerShell](tenant-allow-block-list.md#view-spoofed-sender-entries)
> - [إضافة إدخالات السماح للمرسلين المخادعين باستخدام PowerShell](manage-tenant-allows.md#add-spoofed-sender-allow-entries-using-powershell)
> - [إضافة إدخالات كتلة مرسل منتحلة باستخدام PowerShell](manage-tenant-blocks.md#add-spoofed-sender-block-entries)
> - [تعديل إدخالات المرسلين المخادعة باستخدام PowerShell](modify-remove-entries-tenant-allow-block.md#modify-allow-or-block-spoofed-sender-entries-from-the-tenant-allowblock-list)
> - [إزالة إدخالات المرسلين المخادعة باستخدام PowerShell](modify-remove-entries-tenant-allow-block.md#remove-allow-or-block-spoofed-sender-entries-from-the-tenant-allowblock-list)
>
> تجربة إدارة المرسلين القديمة المخادعة باستخدام أوامر cmdlets **Get-PhishFilterPolicy** و **Set-PhishFilterPolicy** قيد الإهمال، ولكن لا تزال معروضة في هذه المقالة للاكتمال حتى تتم إزالة أوامر cmdlets في كل مكان.

## <a name="what-do-you-need-to-know-before-you-begin"></a>ما الذي تحتاج إلى معرفته قبل البدء؟

- للاتصال Exchange Online PowerShell، راجع [الاتصال إلى Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell). للاتصال ب EOP PowerShell مستقل، راجع [الاتصال إلى Exchange Online Protection PowerShell](/powershell/exchange/connect-to-exchange-online-protection-powershell).

- يجب تعيين أذونات لك في **Exchange Online** قبل أن تتمكن من تنفيذ الإجراءات الواردة في هذه المقالة:
  - لتعديل نهج التحليل الذكي للانتحال أو تمكين أو تعطيل التحليل الذكي للانتحال، يجب أن تكون عضوا في:
    - **إدارة المؤسسة**
    - **مسؤول الأمان** <u>وتكوين</u> **العرض فقط** أو **إدارة المؤسسة للعرض فقط**.
  - للوصول للقراءة فقط إلى نهج التحليل الذكي المخادعة، يجب أن تكون عضوا في مجموعات دور **القارئ العمومي** أو **قارئ الأمان** .

  لمزيد من المعلومات، راجع [الأذونات في Exchange Online](/exchange/permissions-exo/permissions-exo).

  **الملاحظات**:

  - إضافة مستخدمين إلى دور Azure Active Directory المقابل في مركز مسؤولي Microsoft 365 يمنح المستخدمين الأذونات _والأذونات_ المطلوبة للميزات الأخرى في Microsoft 365. لمزيد من المعلومات، راجع [حول أدوار المسؤولين](../../admin/add-users/about-admin-roles.md).
  - كما توفر مجموعة دور **إدارة المؤسسة للعرض فقط** في [Exchange Online](/Exchange/permissions-exo/permissions-exo#role-groups) إمكانية الوصول للقراءة فقط إلى الميزة.

- يتم وصف خيارات التحليل الذكي للانتحال في [إعدادات تزييف الهوية في نهج مكافحة التصيد الاحتيالي](set-up-anti-phishing-policies.md#spoof-settings).

- يمكنك تمكين إعدادات التحليل الذكي للانتحال وتعطيلها وتكوينها في نهج مكافحة التصيد الاحتيالي. للحصول على إرشادات تستند إلى اشتراكك، راجع أحد المواضيع التالية:

  - [تكوين نهج مكافحة التصيد الاحتيالي في EOP](configure-anti-phishing-policies-eop.md).
  - [تكوين نهج مكافحة التصيد الاحتيالي في Microsoft Defender لـ Office 365](configure-mdo-anti-phishing-policies.md).

- للحصول على الإعدادات الموصى بها للتحلي الذكي للانتحال، راجع [إعدادات نهج مكافحة التصيد الاحتيالي EOP](recommended-settings-for-eop-and-office365.md#eop-anti-phishing-policy-settings).

## <a name="use-powershell-to-manage-spoofed-senders"></a>استخدام PowerShell لإدارة المرسلين المخادعة

لعرض المرسلين المسموح بهم والمحظرين في التحليل الذكي للانتحال، استخدم بناء الجملة التالي:

```powershell
Get-PhishFilterPolicy [-AllowedToSpoof <Yes | No | Partial>] [-ConfidenceLevel <Low | High>] [-DecisionBy <Admin | SpoofProtection>] [-Detailed] [-SpoofType <Internal | External>]
```

يقوم هذا المثال بإرجاع معلومات مفصلة حول كافة المرسلين المسموح لهم بانتحال المستخدمين في مجالاتك.

```powershell
Get-PhishFilterPolicy -AllowedToSpoof Yes -Detailed -SpoofType Internal
```

للحصول على معلومات مفصلة حول بناء الجملة والمعلمة، راجع [Get-PhishFilterPolicy](/powershell/module/exchange/get-phishfilterpolicy).

لتكوين المرسلين المسموح بهم والمحظرين في التحليل الذكي للانتحال، اتبع الخطوات التالية:

1. التقط القائمة الحالية للمرسلين المخادعة المكتشفين عن طريق كتابة إخراج **Get-PhishFilterPolicy** cmdlet إلى ملف CSV عن طريق تشغيل الأمر التالي:

   ```powershell
   Get-PhishFilterPolicy -Detailed | Export-CSV "C:\My Documents\Spoofed Senders.csv"
   ```

2. تحرير ملف CSV لإضافة القيم التالية أو تعديلها:
   - **المرسل** (المجال في سجل PTR للخادم المصدر أو عنوان IP/24)
   - **SpoofedUser**: إحدى القيم التالية:
     - عنوان البريد الإلكتروني للمستخدم الداخلي.
     - مجال البريد الإلكتروني للمستخدم الخارجي.
     - قيمة فارغة تشير إلى أنك تريد حظر أو السماح بأي رسائل منتحلة من **المرسل** المحدد أو السماح بها، بغض النظر عن عنوان البريد الإلكتروني المخادع.
   - **AllowedToSpoof** (نعم أو لا)
   - **SpoofType** (داخلي أو خارجي)

   احفظ الملف، واقرأ الملف، وقم بتخزين المحتويات كمتغير مسمى `$UpdateSpoofedSenders` عن طريق تشغيل الأمر التالي:

   ```powershell
   $UpdateSpoofedSenders = Get-Content -Raw "C:\My Documents\Spoofed Senders.csv"
   ```

3. `$UpdateSpoofedSenders` استخدم المتغير لتكوين نهج التحليل الذكي للانتحال عن طريق تشغيل الأمر التالي:

   ```powershell
   Set-PhishFilterPolicy -Identity Default -SpoofAllowBlockList $UpdateSpoofedSenders
   ```

للحصول على معلومات مفصلة حول بناء الجملة والمعلمة، راجع [Set-PhishFilterPolicy](/powershell/module/exchange/set-phishfilterpolicy).

## <a name="how-do-you-know-these-procedures-worked"></a>كيف تعرف أن هذه الإجراءات تعمل؟

للتحقق من أنك قمت بتكوين التحليل الذكي للانتحال مع المرسلين المسموح لهم وغير المسموح لهم بالانتحال، قم بتشغيل الأوامر التالية في PowerShell لعرض المرسلين المسموح لهم وغير المسموح لهم بالانتحال:

  ```powershell
  Get-PhishFilterPolicy -AllowedToSpoof Yes -SpoofType Internal
  Get-PhishFilterPolicy -AllowedToSpoof No -SpoofType Internal
  Get-PhishFilterPolicy -AllowedToSpoof Yes -SpoofType External
  Get-PhishFilterPolicy -AllowedToSpoof No -SpoofType External
  ```

- في PowerShell، قم بتشغيل الأمر التالي لتصدير قائمة كافة المرسلين المخادعة إلى ملف CSV:

   ```powershell
   Get-PhishFilterPolicy -Detailed | Export-CSV "C:\My Documents\Spoofed Senders.csv"
   ```
