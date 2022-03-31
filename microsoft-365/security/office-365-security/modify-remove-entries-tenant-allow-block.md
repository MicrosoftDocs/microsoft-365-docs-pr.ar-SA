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
description: يمكن للمسؤولين التعرف على كيفية تعديل الإدخالات وإزالتها في قائمة السماح/الحظر للمستأجر في مدخل الأمان.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: f1ab3f815cc64af6d1383df228ef7961c3afdcec
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/08/2022
ms.locfileid: "63578420"
---
# <a name="modify-and-remove-entries-in-the-tenant-allowblock-list"></a>تعديل الإدخالات وإزالتها في قائمة السماح/الحظر للمستأجر

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**ينطبق على**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender Office 365 الخطة 1 الخطة 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

يمكنك استخدام مدخل Microsoft 365 Defender أو PowerShell لتعديل الإدخالات وإزالتها في قائمة السماح/الحظر للمستأجر.

## <a name="use-the-microsoft-365-defender-portal"></a>استخدام Microsoft 365 Defender المدخل

### <a name="modify-entries-in-the-tenant-allowblock-list"></a>تعديل الإدخالات في قائمة السماح/الحظر للمستأجر

1. في مدخل Microsoft 365 Defender، انتقل  إلى "**&** \>  \> \> قواعد سياسات التهديدات" في القسم **"قوائم السماح/الحظر**" للمستأجر.

2. حدد علامة التبويب التي تحتوي على نوع الإدخال الذي تريد تعديله:
   - **المرسلون**
   - **اانتحال**
   - **عناوين URL**
   - **الملفات**


3. حدد الإدخال الذي تريد تعديله، ثم انقر فوق أيقونة ![تحرير.](../../media/m365-cc-sc-edit-icon.png) **تحرير**. تعتمد القيم التي يمكنك تعديلها في قائمة الطيران التي تظهر على علامة التبويب التي حددتها في الخطوة السابقة:
   - **المرسلون**
     - **لا تنتهي أبدا** و/أو تاريخ انتهاء الصلاحية.
     - **ملاحظة اختيارية**
   - **اانتحال**
     - **الإجراء**: يمكنك تغيير القيمة إلى **السماح** أو **الحظر**.
   - **عناوين URL**
     - **لا تنتهي أبدا** و/أو تاريخ انتهاء الصلاحية.
     - **ملاحظة اختيارية**
   - **الملفات**
     - **لا تنتهي أبدا** و/أو تاريخ انتهاء الصلاحية.
     - **ملاحظة اختيارية**

4. عند الانتهاء، انقر فوق **حفظ**.

> [!NOTE]
> يمكنك تمديد يسمح فقط ب 30 يوما كحد أقصى بعد تاريخ الإنشاء. يمكن تمديد الكتل لمدة تصل إلى 90 يوما، ولكن بخلاف السماح، يمكن أيضا تعيينها إلى لا تنتهي صلاحيتها أبدا.

### <a name="remove-entries-from-the-tenant-allowblock-list"></a>إزالة الإدخالات من قائمة السماح/الحظر للمستأجر

1. في مدخل Microsoft 365 Defender، انتقل  إلى "**&** \>  \> \> قواعد سياسات التهديدات" في القسم **"قوائم السماح/الحظر**" للمستأجر.

2. حدد علامة التبويب التي تحتوي على نوع الإدخال الذي تريد إزالته:
   - **المرسلون**
   - **اانتحال**
   - **عناوين URL**
   - **الملفات**
 
3. حدد الإدخال الذي تريد إزالته، ثم انقر فوق أيقونة ![حذف.](../../media/m365-cc-sc-delete-icon.png) **حذف**.

4. في مربع حوار التحذير الذي يظهر، انقر فوق **حذف**.

## <a name="use-powershell"></a>استخدام PowerShell

### <a name="modify-allow-or-block-sender-file-and-url-entries-in-the-tenant-allowblock-list"></a>تعديل السماح أو حظر إدخالات المرسل والملفات وURL في قائمة السماح/الحظر للمستأجر

لتعديل إدخالات السماح بالمرسل والملفات وURL أو حظرها في قائمة السماح/الحظر للمستأجر، استخدم بناء الجملة التالي:

```powershell
Set-TenantAllowBlockListItems -ListType <Sender | FileHash | Url> -Ids <"Id1","Id2",..."IdN"> [<-ExpirationDate Date | -NoExpiration>] [-Notes <String>]
```

يغير هذا المثال تاريخ انتهاء صلاحية إدخال URL المحظور المحدد.

```powershell
Set-TenantAllowBlockListItems -ListType Url -Ids "RgAAAAAI8gSyI_NmQqzeh-HXJBywBwCqfQNJY8hBTbdlKFkv6BcUAAAl_QCZAACqfQNJY8hBTbdlKFkv6BcUAAAl_oSRAAAA" -ExpirationDate "5/30/2020"
```

للحصول على معلومات مفصلة حول بناء الجملة والمعلمات، راجع [Set-TenantAllowBlockListItems](/powershell/module/exchange/set-tenantallowblocklistitems).

### <a name="remove-allow-or-block-sender-url-or-file-entries-from-the-tenant-allowblock-list"></a>إزالة السماح أو حظر إدخالات المرسل أو URL أو الملف من قائمة السماح/الحظر للمستأجر

لإزالة إدخالات السماح بالمرسل والملف وURL أو حظرها من قائمة السماح/الحظر للمستأجر، استخدم بناء الجملة التالي:

```powershell
Remove-TenantAllowBlockListItems -ListType <Sender | FileHash | Url> -Ids <"Id1","Id2",..."IdN">
```

يزيل هذا المثال إدخال URL الحظر المحدد من قائمة السماح/الحظر للمستأجر.

```powershell
Remove-TenantAllowBlockListItems -ListType Url -Ids "RgAAAAAI8gSyI_NmQqzeh-HXJBywBwCqfQNJY8hBTbdlKFkv6BcUAAAl_QCZAACqfQNJY8hBTbdlKFkv6BcUAAAl_oSPAAAA0"
```

للحصول على بناء جملة تفصيلي ومعلومات المعلمة، راجع [Remove-TenantAllowBlockListItems](/powershell/module/exchange/remove-tenantallowblocklistitems).

### <a name="modify-allow-or-block-spoofed-sender-entries-from-the-tenant-allowblock-list"></a>تعديل السماح أو حظر إدخالات المرسلين المنتحلين من قائمة السماح/الحظر للمستأجر

لتعديل إدخالات المرسلين المنتحلين أو السماح بها أو حظرها في قائمة السماح/الحظر للمستأجر، استخدم بناء الجملة التالي:

```powershell
Set-TenantAllowBlockListSpoofItems -Ids <"Id1","Id2",..."IdN"> -Action <Allow | Block>
```

يغير هذا المثال إدخال المرسل المهزوف من السماح للحظر.

```powershell
Set-TenantAllowBlockListItems -Ids "RgAAAAAI8gSyI_NmQqzeh-HXJBywBwCqfQNJY8hBTbdlKFkv6BcUAAAl_QCZAACqfQNJY8hBTbdlKFkv6BcUAAAl_oSRAAAA" -Action Block
```

للحصول على معلومات مفصلة حول بناء الجملة والمعلمات، راجع [Set-TenantAllowBlockListSpoofItems](/powershell/module/exchange/set-tenantallowblocklistspoofitems).

### <a name="remove-allow-or-block-spoofed-sender-entries-from-the-tenant-allowblock-list"></a>إزالة إدخالات المرسلين المنتحلين أو حظرها من قائمة السماح/الحظر للمستأجر
 
لإزالة إدخالات السماح أو حظر انتحال المرسل من قائمة السماح/الحظر للمستأجر، استخدم بناء الجملة التالي:

```powershell
Remove-TenantAllowBlockListSpoofItems -Ids <"Id1","Id2",..."IdN">
```

للحصول على معلومات مفصلة حول بناء الجملة والمعلمات، راجع [Remove-TenantAllowBlockListSpoofItems](/powershell/module/exchange/remove-tenantallowblocklistspoofitems).
