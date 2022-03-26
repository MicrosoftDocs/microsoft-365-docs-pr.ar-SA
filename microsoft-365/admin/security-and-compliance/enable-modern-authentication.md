---
title: تمكين المصادقة الحديثة Office 2013 على Windows الأجهزة
f1.keywords:
- NOCSH
ms.author: sharik
author: skjerland
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
ms.custom:
- AdminSurgePortfolio
- okr_smb
- AdminTemplateSet
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: 7dc1c01a-090f-4971-9677-f1b192d6c910
description: تعرف على كيفية تعيين مفاتيح التسجيل لتمكين المصادقة الحديثة للأجهزة التي تم تثبيت Microsoft Office 2013 عليها.
ms.openlocfilehash: 468658c3b346c7923937ff9595699a20306ed6a9
ms.sourcegitcommit: d32654bdfaf08de45715dd362a7d42199bdc1ee7
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/23/2022
ms.locfileid: "63754181"
---
# <a name="enable-modern-authentication-for-office-2013-on-windows-devices"></a>تمكين المصادقة الحديثة Office 2013 على Windows الأجهزة

Microsoft Office 2013 على أجهزة الكمبيوتر Windows Microsoft على المصادقة الحديثة. ولكن، لكي تقوم بتكوينه، ستحتاج إلى تكوين مفاتيح التسجيل التالية:

|مفتاح التسجيل|النوع|القيمة|
|:---|:---:|:---:|
|HKEY_CURRENT_USER\Software\Microsoft\Exchange\AlwaysUseMSOAuthForAutoDiscover|REG_DWORD|1|
|HKEY_CURRENT_USER\Software\Microsoft\Office\15.0\Common\Identity\EnableADAL|REG_DWORD|1|
|HKEY_CURRENT_USER\Software\Microsoft\Office\15.0\Common\Identity\Version|REG_DWORD|1|

> [!NOTE]
> تم تمكين المصادقة الحديثة بالفعل في Office 2016 أو أي وقت لاحق. لست بحاجة إلى تعيين مفاتيح التسجيل هذه للإصدارات الأحدث من Office.

## <a name="enable-modern-authentication-for-office-2013-clients"></a>تمكين المصادقة الحديثة لعملاء Office 2013

1. أغلق Outlook.

2. انسخ النص التالي واللصق فيه المفكرة:

   ```text
   Windows Registry Editor Version 5.00

   [HKEY_CURRENT_USER\Software\Microsoft\Exchange]
   "AlwaysUseMSOAuthForAutoDiscover"=dword:00000001

   [HKEY_CURRENT_USER\Software\Microsoft\Office\15.0\Common]

   [HKEY_CURRENT_USER\Software\Microsoft\Office\15.0\Common\Identity]
   "EnableADAL"=dword:00000001
   "Version"=dword:00000001
   ```

3. احفظ الملف بملحق الملف .reg بدلا من .txt في موقع يسهل عليك العثور عليه. على سبيل المثال، `C:\Data\Office2013_Enable_ModernAuth.reg`.

4. افتح مستكشف الملفات (المعروف سابقا باسم Windows Explorer)، واستعرض موقع ملف .reg الذي حفظته للتو، ثم انقر نقرا مزدوجا فوقه.

5. في مربع **الحوار عنصر تحكم حساب** المستخدم الذي يظهر، انقر فوق **نعم** للسماح للتطبيق بإجراء تغييرات على جهازك.

6. في مربع **الحوار تحذير محرر** السجل الذي يظهر، انقر فوق **نعم** لقبول التغييرات.

بعد تعيين مفاتيح التسجيل، يمكنك تعيين Office 2013 لاستخدام المصادقة متعددة العوامل (MFA) مع Microsoft 365. لمزيد من المعلومات، راجع [إعداد المصادقة متعددة العوامل](set-up-multi-factor-authentication.md).

إذا قمت حاليا تسجيل الدخول إلى أي من تطبيقات Office العميل، يجب تسجيل الخروج ثم تسجيل الدخول مرة أخرى لكي يتم تطبيق التغيير. وبخلاف ذلك، لن تتوفر إعدادات التجوال و MRU حتى يتم إنشاء الهوية.

## <a name="disable-modern-authentication-on-devices"></a>تعطيل المصادقة الحديثة على الأجهزة

يتشابه الإجراء لتعطيل المصادقة الحديثة على جهاز إلى حد كبير، ولكن هناك حاجة إلى عدد أقل من مفاتيح التسجيل، وستحتاج إلى تعيين قيمها إلى 0.

|مفتاح التسجيل|النوع|القيمة|
|---|:---:|:---:|
|HKEY_CURRENT_USER\Software\Microsoft\Exchange\AlwaysUseMSOAuthForAutoDiscover|REG_DWORD|0|
|HKEY_CURRENT_USER\SOFTWARE\Microsoft\Office\15.0\Common\Identity\EnableADAL|REG_DWORD|0|

```text
Windows Registry Editor Version 5.00

[HKEY_CURRENT_USER\Software\Microsoft\Exchange]
"AlwaysUseMSOAuthForAutoDiscover"=dword:00000000

[HKEY_CURRENT_USER\Software\Microsoft\Office\15.0\Common]

[HKEY_CURRENT_USER\Software\Microsoft\Office\15.0\Common\Identity]
"EnableADAL"=dword:00000000
```

## <a name="related-content"></a>المحتوى ذي الصلة

[تسجيل الدخول إلى Office 2013 باستخدام طريقة تحقق ثانية](https://support.microsoft.com/office/2b856342-170a-438e-9a4f-3c092394d3cb)

[Outlook عن كلمة المرور ولا يستخدم المصادقة الحديثة للاتصال Office 365](/outlook/troubleshoot/authentication/outlook-prompt-password-modern-authentication-enabled)
