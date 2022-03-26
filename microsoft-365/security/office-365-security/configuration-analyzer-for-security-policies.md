---
title: محلل التكوين لنهج الأمان
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.reviewer: ''
ms.date: ''
audience: ITPro
ms.topic: how-to
ms.localizationpriority: medium
search.appverid:
- MET150
ms.assetid: ''
ms.collection:
- M365-security-compliance
ms.custom: ''
description: يمكن للمسؤولين التعرف على كيفية استخدام محلل التكوين للعثور على سياسات الأمان الموجودة أسفل الإعدادات في الحماية القياسية والحماية تقيد في سياسات الأمان المحددة مسبقا وإصلاحها.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 0acdf6d300984c00bb1b1b060d3e36562983ebca
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 01/12/2022
ms.locfileid: "63569538"
---
# <a name="configuration-analyzer-for-protection-policies-in-eop-and-microsoft-defender-for-office-365"></a>محلل التكوين لنهج الحماية في EOP و Microsoft Defender Office 365

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**ينطبق على**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender Office 365 الخطة 1 الخطة 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

يوفر محلل التكوين في مدخل Microsoft 365 Defender موقع مركزي للعثور على سياسات الأمان وإصلاحها حيث توجد الإعدادات أسفل إعدادات الحماية القياسية وملف تعريف الحماية الصارم في سياسات الأمان التي تم تعيينها [مسبقا](preset-security-policies.md).

يتم تحليل الأنواع التالية من السياسات بواسطة محلل التكوين:

- **Exchange Online Protection (EOP):** يشمل ذلك Microsoft 365 المؤسسات التي تحتوي على علب بريد Exchange Online مؤسسات EOP مستقلة لا Exchange Online علب بريد:
  - [سياسات مكافحة البريد العشوائي](configure-your-spam-filter-policies.md).
  - [سياسات مكافحة البرامج الضارة](configure-anti-malware-policies.md).
  - [سياسات مكافحة التصيد الاحتيالي ل EOP](set-up-anti-phishing-policies.md#spoof-settings).

- **Microsoft Defender Office 365**: يشمل ذلك المؤسسات التي Microsoft 365 E5 اشتراكات الوظائف الإضافية أو Defender Office 365 الإضافية:
  - سياسات مكافحة التصيد الاحتيالي في Microsoft Defender Office 365، والتي تتضمن:
    - الإعدادات [المنتحلة نفسها](set-up-anti-phishing-policies.md#spoof-settings) المتوفرة في سياسات مكافحة التصيد الاحتيالي في EOP.
    - [إعدادات انتحال](set-up-anti-phishing-policies.md#impersonation-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365)
    - [عتبات التصيد الاحتيالي المتقدمة](set-up-anti-phishing-policies.md#advanced-phishing-thresholds-in-anti-phishing-policies-in-microsoft-defender-for-office-365)
  - [خزينة الارتباطات.](set-up-safe-links-policies.md)
  - [خزينة المرفقات](set-up-safe-attachments-policies.md).

يتم وصف قيم إعداد النهج القياسي والتقيدي المستخدمة كخطوط أساسية في الإعدادات المستحسنة ل [EOP و Microsoft Defender Office 365 الأمان](recommended-settings-for-eop-and-office365.md).

## <a name="what-do-you-need-to-know-before-you-begin"></a>ما الذي تحتاج إلى معرفته قبل البدء؟

- يمكنك فتح Microsoft 365 Defender في <https://security.microsoft.com>. الانتقال مباشرة إلى صفحة **محلل** التكوين، استخدم <https://security.microsoft.com/configurationAnalyzer>.

- للاتصال ب PowerShell Exchange Online، راجع الاتصال [إلى Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

- يجب تعيين أذونات لك في مدخل Microsoft 365 Defender قبل أن تتمكن من تنفيذ الإجراءات في هذه المقالة:
  - لاستخدام محلل التكوين وتحديثات لنهج الأمان، يجب أن تكون عضوا في مجموعات دور مسؤول **إدارة** المؤسسة أو مسؤول الأمان. 
  - للوصول للقراءة فقط إلى محلل التكوين، يجب أن تكون عضوا في مجموعات دور القارئ العام أو قارئ  الأمان.

  لمزيد من المعلومات، راجع [الأذونات في Microsoft 365 Defender المدخل](permissions-microsoft-365-security-center.md).

  > [!NOTE]
  >
  > - توفر إضافة مستخدمين إلى دور Azure Active Directory المناظر للمستخدمين الأذونات المطلوبة في مدخل Microsoft 365 Defender والأذونات للميزات الأخرى  في Microsoft 365. لمزيد من المعلومات، راجع [حول أدوار المسؤولين](../../admin/add-users/about-admin-roles.md).
  > - توفر **أيضا مجموعة دور "** إدارة [المؤسسات Exchange Online](/Exchange/permissions-exo/permissions-exo#role-groups) طريقة العرض فقط" إمكانية الوصول للقراءة فقط إلى الميزة.

## <a name="use-the-configuration-analyzer-in-the-microsoft-365-defender-portal"></a>استخدام محلل التكوين في مدخل Microsoft 365 Defender

 في مدخل Microsoft 365 Defender،  <https://security.microsoft.com>انتقل إلى البريد الإلكتروني **&** \> "سياسات التعاون" & "**تكوين** \> \> قواعد المخاطر" في القسم "**سياسات القوالب".** الانتقال مباشرة إلى صفحة **محلل** التكوين، استخدم <https://security.microsoft.com/configurationAnalyzer>.

تحتوي **صفحة محلل التكوين** على ثلاث علامات تبويب رئيسية:

- **التوصيات القياسية**: قارن سياسات الأمان الموجودة بالتوصيات القياسية. يمكنك ضبط قيم الإعدادات لإحضارها إلى المستوى نفسه القياسي.
- **توصيات صارمة**: قارن سياسات الأمان الموجودة بالتوصيات تقيد. يمكنك ضبط قيم الإعدادات لإحضارها إلى مستوى التقيد نفسه.
- **تحليل انحراف التكوين ومحفوظاته**: التدقيق وتعقب تغييرات النهج مع مرور الوقت.

### <a name="standard-recommendations-and-strict-recommendations-tabs-in-the-configuration-analyzer"></a>علامات التبويب "توصيات قياسية" و"توصيات صارمة" في محلل التكوين

بشكل افتراضي، يتم فتح محلل التكوين على علامة **التبويب توصيات** قياسية. يمكنك التبديل إلى علامة **التبويب توصيات** صارمة. الإعدادات والتخطيط والإجراءات هي نفسها في كلتا علامات التبويب.

![الإعدادات والتوصيات في محلل التكوين.](../../media/configuration-analyzer-settings-and-recommendations-view.png)

يعرض المقطع الأول من علامة التبويب عدد الإعدادات في كل نوع من أنواع النهج التي تحتاج إلى تحسين مقارنة بالحماية القياسية أو الحماية تقيد. أنواع السياسات هي:

- **مكافحة البريد العشوائي**
- **مكافحة التصيد الاحتيالي**
- **مكافحة البرامج الضارة**
- **خزينة المرفقات** (إذا كان اشتراكك يتضمن Microsoft Defender Office 365)
- **خزينة الارتباطات** (إذا كان اشتراكك يتضمن Microsoft Defender Office 365)

إذا لم يتم عرض نوع نهج أو رقم، فإن كل النهج من هذا النوع تفي بإعدادات الحماية القياسية أو الصارم الموصى بها.

أما باقي علامات التبويب، فيكمن في جدول الإعدادات التي يجب أن تصل إلى مستوى الحماية القياسية أو الحماية تقيد. يحتوي الجدول على الأعمدة التالية:

- **التوصيات**: قيمة الإعداد في ملف تعريف الحماية القياسية أو الصارم.
- **النهج**: اسم النهج المتأثر الذي يحتوي على الإعداد.
- **اسم مجموعة/إعداد النهج**: اسم الإعداد الذي يتطلب انتباهك.
- **نوع النهج**: مكافحة البريد العشوائي أو مكافحة التصيد الاحتيالي أو مكافحة البرامج الضارة أو خزينة الارتباطات أو خزينة المرفقات.
- **التكوين الحالي**: القيمة الحالية لإعداد.
- **تاريخ التعديل الأخير**: تاريخ آخر تعديل النهج.
- **الحالة**: عادة ما تكون هذه القيمة **غير مبدءة**.

### <a name="change-a-policy-setting-to-the-recommended-value"></a>تغيير إعداد نهج إلى القيمة الموصى بها

في علامة **التبويب حماية قياسية** أو حماية صارمة لمحلل التكوين، حدد الصف في الجدول. تظهر الأزرار التالية:

- **تطبيق التوصية**
- **عرض النهج**
- **تحديث**:

إذا حددت صفا وانقرت فوق تطبيق توصية، يظهر مربع حوار تأكيد (مع خيار عدم إظهار مربع الحوار مرة أخرى). إذا نقرت فوق **موافق**، تحدث الأمور التالية:

- يتم تحديث الإعداد إلى القيمة الموصى بها.
- يختفي **النهج تطبيق التوصية** **وعرض (** يبقى **الزر تحديث** فقط).
- تتغير **قيمة** الحالة للصف إلى **مكتمل**.

إذا حددت صفا وانقرت  فوق عرض النهج، يتم نقلك إلى قائمة منتالية التفاصيل للن نهج متأثر في مدخل Microsoft 365 Defender حيث يمكنك تحديث الإعداد يدويا.

بعد تحديث الإعداد تلقائيا أو يدويا، انقر فوق تحديث لرؤية تقليل  عدد التوصيات وإزالة الصف المحدث من النتائج.

### <a name="configuration-drift-analysis-and-history-tab-in-the-configuration-analyzer"></a>تحليل انحراف التكوين و علامة تبويب المحفوظات في محلل التكوين

تسمح لك علامة التبويب هذه بتعقب التغييرات التي تم إدخالها على سياسات الأمان وكيفية مقارنة هذه التغييرات بإعدادات قياسية أو صارمة. بشكل افتراضي، يتم عرض المعلومات التالية:

- **تاريخ التعديل الأخير**
- **تم التعديل بواسطة**
- **تعيين الاسم**
- **النهج**: اسم النهج المتأثر.
- **النوع**: مكافحة البريد العشوائي أو مكافحة التصيد الاحتيالي أو مكافحة البرامج الضارة أو خزينة ارتباطات أو خزينة المرفقات.
- **تغيير التكوين**: القيمة القديمة والقيمة الجديدة لإعداد
- **انحراف التكوين**: القيمة **زيادة** أو إنقاص التي تشير إلى زيادة الإعداد أو إنقاصه مقارنة بإعداد قياسي أو صارم الموصى به.

لتصفية النتائج، انقر فوق **تصفية**. في القائمة **المستعرضة** عوامل التصفية التي تظهر، يمكنك الاختيار من عوامل التصفية التالية:

- **وقت البدء** وتاريخ **الانتهاء** (التاريخ): يمكنك العودة بعد 90 يوما من اليوم.
- **الحماية القياسية** أو **الحماية تقيد**

عند الانتهاء، انقر فوق **تطبيق**.

لتصدير النتائج إلى ملف .csv، انقر فوق **تصدير**.

لتصفية النتائج **حسب قيمة معينة** تم تعديلها بواسطة أو **تعيين اسم** **أو نوع،** استخدم **المربع** بحث.

![تحليل انحراف التكوين وعرض المحفوظات في محلل التكوين.](../../media/configuration-analyzer-configuration-drift-analysis-view.png)
