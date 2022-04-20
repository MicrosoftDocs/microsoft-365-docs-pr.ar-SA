---
title: تعديل الإدخالات وإزالتها في قائمة السماح/الحظر للمستأجر
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
description: يمكن للمسؤولين معرفة كيفية تعديل الإدخالات وإزالتها في قائمة السماح/الحظر للمستأجر في مدخل الأمان.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 7da986c42421c797f2d01b1e61d50c06933e373f
ms.sourcegitcommit: 45bc65972d4007b2aa7760d4457a0d2699f81926
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/20/2022
ms.locfileid: "64970864"
---
# <a name="modify-and-remove-entries-in-the-tenant-allowblock-list"></a>تعديل الإدخالات وإزالتها في قائمة السماح/الحظر للمستأجر

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**ينطبق على**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [خطة 1 وخطة 2 من Microsoft Defender لـ Office 365](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

يمكنك استخدام مدخل Microsoft 365 Defender أو PowerShell لتعديل الإدخالات وإزالتها في قائمة السماح/الحظر للمستأجر.

## <a name="use-the-microsoft-365-defender-portal"></a>استخدام مدخل Microsoft 365 Defender

### <a name="modify-entries-in-the-tenant-allowblock-list"></a>تعديل الإدخالات في قائمة السماح/الحظر للمستأجر

1. في مدخل Microsoft 365 Defender، انتقل إلى **"نهج & قواعد قواعد** \> **نهج التهديد** \> **" قسم** "\>**السماح/حظر القوائم للمستأجر**".

2. حدد علامة التبويب التي تحتوي على نوع الإدخال الذي تريد تعديله:
   - **المرسلين**
   - **التحايل**
   - **عناوين url**
   - **الملفات**

3. حدد الإدخال الذي تريد تعديله، ثم انقر فوق ![أيقونة "تحرير".](../../media/m365-cc-sc-edit-icon.png) **تحرير**. تعتمد القيم التي يمكنك تعديلها في القائمة المنبثقة التي تظهر على علامة التبويب التي حددتها في الخطوة السابقة:
   - **المرسلين**
     - **لا تنتهي الصلاحية** أبدا و/أو تاريخ انتهاء الصلاحية.
     - **ملاحظة اختيارية**
   - **التحايل**
     - **الإجراء**: يمكنك تغيير القيمة إلى **السماح** أو **الحظر**.
   - **عناوين url**
     - **لا تنتهي الصلاحية** أبدا و/أو تاريخ انتهاء الصلاحية.
     - **ملاحظة اختيارية**
   - **الملفات**
     - **لا تنتهي الصلاحية** أبدا و/أو تاريخ انتهاء الصلاحية.
     - **ملاحظة اختيارية**

4. عند الانتهاء، انقر فوق **حفظ**.

> [!NOTE]
> يمكنك فقط تمديد السماح لمدة 30 يوما كحد أقصى بعد تاريخ الإنشاء. يمكن تمديد الكتل لمدة تصل إلى 90 يوما، ولكن على عكس السماح، يمكن أيضا تعيينها إلى عدم انتهاء الصلاحية أبدا.

### <a name="remove-entries-from-the-tenant-allowblock-list"></a>إزالة الإدخالات من قائمة السماح/الحظر للمستأجر

1. في مدخل Microsoft 365 Defender، انتقل إلى **"نهج & قواعد قواعد** \> **نهج التهديد** \> **" قسم** "\>**السماح/حظر القوائم للمستأجر**".

2. حدد علامة التبويب التي تحتوي على نوع الإدخال الذي تريد إزالته:
   - **المرسلين**
   - **التحايل**
   - **عناوين url**
   - **الملفات**

3. حدد الإدخال الذي تريد إزالته، ثم انقر فوق ![أيقونة "حذف".](../../media/m365-cc-sc-delete-icon.png) **حذف**.

4. في مربع حوار التحذير الذي يظهر، انقر فوق **"حذف**".

## <a name="use-powershell"></a>استخدام PowerShell

### <a name="modify-allow-or-block-sender-file-and-url-entries-in-the-tenant-allowblock-list"></a>تعديل السماح أو حظر إدخالات المرسل والملف وعنوان URL في قائمة السماح/الحظر للمستأجر

لتعديل إدخالات السماح والملف وعنوان URL أو حظرها في قائمة السماح/الحظر للمستأجر، استخدم بناء الجملة التالي:

```powershell
Set-TenantAllowBlockListItems -ListType <Sender | FileHash | Url> -Ids <"Id1","Id2",..."IdN"> [<-ExpirationDate Date | -NoExpiration>] [-Notes <String>]
```

يغير هذا المثال تاريخ انتهاء صلاحية إدخال URL للكتلة المحددة.

```powershell
Set-TenantAllowBlockListItems -ListType Url -Ids "RgAAAAAI8gSyI_NmQqzeh-HXJBywBwCqfQNJY8hBTbdlKFkv6BcUAAAl_QCZAACqfQNJY8hBTbdlKFkv6BcUAAAl_oSRAAAA" -ExpirationDate "5/30/2020"
```

للحصول على معلومات مفصلة حول بناء الجملة والمعلمة، راجع [Set-TenantAllowBlockListItems](/powershell/module/exchange/set-tenantallowblocklistitems).

### <a name="remove-allow-or-block-sender-url-or-file-entries-from-the-tenant-allowblock-list"></a>إزالة السماح أو حظر إدخالات المرسل أو URL أو الملف من قائمة السماح/الحظر للمستأجر

لإزالة إدخالات المرسل والملف وعنوان URL المسموح بها أو حظرها من قائمة السماح/الحظر للمستأجر، استخدم بناء الجملة التالي:

```powershell
Remove-TenantAllowBlockListItems -ListType <Sender | FileHash | Url> -Ids <"Id1","Id2",..."IdN">
```

يزيل هذا المثال إدخال URL للكتلة المحدد من قائمة السماح/الحظر للمستأجر.

```powershell
Remove-TenantAllowBlockListItems -ListType Url -Ids "RgAAAAAI8gSyI_NmQqzeh-HXJBywBwCqfQNJY8hBTbdlKFkv6BcUAAAl_QCZAACqfQNJY8hBTbdlKFkv6BcUAAAl_oSPAAAA0"
```

للحصول على معلومات مفصلة حول بناء الجملة والمعلمة، راجع [Remove-TenantAllowBlockListItems](/powershell/module/exchange/remove-tenantallowblocklistitems).

### <a name="modify-allow-or-block-spoofed-sender-entries-from-the-tenant-allowblock-list"></a>تعديل إدخالات المرسلين المخادعة المسموح بها أو حظرها من قائمة السماح/الحظر للمستأجر

لتعديل إدخالات المرسلين المخادعة في قائمة السماح/الحظر للمستأجر أو حظرها، استخدم بناء الجملة التالي:

```powershell
Set-TenantAllowBlockListSpoofItems -Ids <"Id1","Id2",..."IdN"> -Action <Allow | Block>
```

يغير هذا المثال إدخال المرسل المخادع من السماح إلى الحظر.

```powershell
Set-TenantAllowBlockListItems -Ids "RgAAAAAI8gSyI_NmQqzeh-HXJBywBwCqfQNJY8hBTbdlKFkv6BcUAAAl_QCZAACqfQNJY8hBTbdlKFkv6BcUAAAl_oSRAAAA" -Action Block
```

للحصول على معلومات مفصلة حول بناء الجملة والمعلمة، راجع [Set-TenantAllowBlockListSpoofItems](/powershell/module/exchange/set-tenantallowblocklistspoofitems).

### <a name="remove-allow-or-block-spoofed-sender-entries-from-the-tenant-allowblock-list"></a>إزالة إدخالات المرسلين المخادعة المسموح بها أو حظرها من قائمة السماح/الحظر للمستأجر

لإزالة إدخالات مرسل الانتحال المسموح بها أو حظرها من قائمة السماح/الحظر للمستأجر، استخدم بناء الجملة التالي:

```powershell
Remove-TenantAllowBlockListSpoofItems -Ids <"Id1","Id2",..."IdN">
```

للحصول على معلومات مفصلة حول بناء الجملة والمعلمة، راجع [Remove-TenantAllowBlockListSpoofItems](/powershell/module/exchange/remove-tenantallowblocklistspoofitems).
