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
ms.openlocfilehash: c390e3b9858a4d7d8fc37ea5c5e6f1901d5e20fb
ms.sourcegitcommit: 3fb76db6b34e24569417f4c8a41b99f46a780389
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/17/2022
ms.locfileid: "63567725"
---
# <a name="enable-modern-authentication-for-office-2013-on-windows-devices"></a>تمكين المصادقة الحديثة Office 2013 على Windows الأجهزة

لتمكين المصادقة الحديثة لأي أجهزة Windows تم تثبيت Office 2013 عليها، ستحتاج إلى تعيين مفاتيح تسجيل معينة.
  
## <a name="enable-modern-authentication-for-office-2013-clients"></a>تمكين المصادقة الحديثة لعملاء Office 2013

> [!NOTE]
> تم تمكين المصادقة الحديثة Office عملاء 2016، لست بحاجة إلى تعيين مفاتيح التسجيل Office 2016. 
  
لتمكين المصادقة الحديثة لأي أجهزة تعمل Windows (على سبيل المثال، على أجهزة الكمبيوتر المحمولة وأجهزة الكمبيوتر اللوحية)، التي تم تثبيت Microsoft Office 2013 عليها، ستحتاج إلى تعيين مفاتيح التسجيل التالية. يجب تعيين المفاتيح على كل جهاز تريد تمكينه للمصادقة الحديثة:

<br>

****

|مفتاح التسجيل|النوع|القيمة|
|:---|:---:|---:|
|HKEY_CURRENT_USER\Software\Microsoft\Exchange\AlwaysUseMSOAuthForAutoDiscover|REG_DWORD|1|
|HKEY_CURRENT_USER\Software\Microsoft\Office\15.0\Common\Identity\EnableADAL|REG_DWORD|1|
|HKEY_CURRENT_USER\Software\Microsoft\Office\15.0\Common\Identity\Version|REG_DWORD|1|

قم بإنشاء مفاتيح التسجيل التالية أو تعديلها لتجبر Outlook استخدام أسلوب مصادقة أحدث لخدمات الويب، مثل EWS و Autodiscover. نوصي المستخدمين Outlook استخدام المصادقة الحديثة.

1. إنهاء Outlook.

2. ابدأ "محرر السجل" باستخدام أحد الإجراءات التالية، كما هو مناسب للإصدار الذي تستخدمه من Windows:

   - **Windows 10 Windows 8.1 Windows 8:** اضغط على مفتاح Windows + R لفتح مربع الحوار تشغيل. اكتب *regedit.exe*، ثم اضغط على **Enter.**
   - **Windows 7:** **انقر فوق***بدء،regedit.exe* في مربع البحث، ثم اضغط على **Enter.**

3. في محرر السجل، حدد موقع مفتاح السجل الفرعي التالي وانقر فوقه:

   ```console
   HKEY_CURRENT_USER\Software\Microsoft\Exchange\
   ```

4. إذا كان *المفتاح AlwaysUseMSOAuthForAutoDiscover* مفقودا، ففي القائمة تحرير، قم ب الإشارة إلى **جديد** ثم حدد **قيمة DWORD**. اكتب *AlwaysUseMSOAuthForAutoDiscover*، ثم اضغط على **Enter.**

5. انقر ب الماوس *الأيمن فوق AlwaysUseMSOAuthForAutoDiscover*، ثم انقر فوق **تعديل.**

6. في المربع **بيانات** القيمة، اكتب **1**، ثم انقر فوق **موافق.**

7. في محرر السجل، حدد موقع مفتاح السجل الفرعي التالي وانقر فوقه:

   ```console
   HKEY_CURRENT_USER\Software\Microsoft\Office\15.0\Common\Identity\
   ```

8. إذا كان *مفتاحي EnableADAL والإصدار* موجودين بالفعل، فعدل القيم إذا لزم الأمر، ثم قم بالخروج من محرر السجل. إذا لم يتم ذلك، في القائمة تحرير، قم ب الإشارة إلى **جديد** ثم حدد **قيمة DWORD** لإنشاء المفاتيح المفقودة. 

9. على سبيل المثال، إذا كان *المفتاح EnableADAL* مفقودا، فاختر *EnableADAL*، ثم اضغط على **مفتاح Enter.**

10. انقر ب زر الماوس *الأيمن فوق EnableADAL*، ثم انقر فوق **تعديل.**

11. في المربع **بيانات** القيمة، اكتب **1**، ثم انقر فوق **موافق.**

12. اتبع العملية نفسها لمفتاح الإصدار إذا لزم الأمر. 

13. **إنهاء محرر السجل.**

بعد تعيين مفاتيح التسجيل، يمكنك تعيين تطبيقات أجهزة Office 2013 لاستخدام المصادقة متعددة العوامل [(MFA)](set-up-multi-factor-authentication.md) مع Microsoft 365. 
  
إذا كنت تقوم حاليا تسجيل الدخول باستخدام أي من تطبيقات العميل، يجب تسجيل الخروج ثم تسجيل الدخول مرة أخرى لكي يتم تطبيق التغيير. وبخلاف ذلك، لن تتوفر إعدادات التجوال و MRU حتى يتم إنشاء الهوية.
  
## <a name="disable-modern-authentication-on-devices"></a>تعطيل المصادقة الحديثة على الأجهزة

لتعطيل المصادقة الحديثة على جهاز، قم بتعيين مفاتيح التسجيل التالية على الجهاز:

<br>

****

|مفتاح التسجيل|النوع|القيمة|
|:---|:---:|---:|
|HKEY_CURRENT_USER\SOFTWARE\Microsoft\Office\15.0\Common\Identity\EnableADAL|REG_DWORD|0|
|HKEY_CURRENT_USER\Software\Microsoft\Exchange\AlwaysUseMSOAuthForAutoDiscover|REG_DWORD|0|
   
## <a name="related-content"></a>المحتوى ذي الصلة

[سجل الدخول إلى Office 2013 باستخدام أسلوب تحقق ثان](https://support.microsoft.com/office/2b856342-170a-438e-9a4f-3c092394d3cb) (مقالة)\
[Outlook عن](/outlook/troubleshoot/authentication/outlook-prompt-password-modern-authentication-enabled) كلمة المرور ولا يستخدم المصادقة الحديثة للاتصال Office 365 (مقالة)
