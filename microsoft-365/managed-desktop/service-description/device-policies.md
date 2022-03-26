---
title: تكوين الجهاز
description: تعرف على السياسات الافتراضية المطبقة على أجهزة سطح المكتب المدارة من Microsoft.
keywords: سطح المكتب المدار من Microsoft، Microsoft 365، الخدمة، الوثائق
ms.service: m365-md
author: tiaraquan
ms.localizationpriority: medium
ms.collection: M365-modern-desktop
ms.author: tiaraquan
manager: dougeby
ms.topic: article
ms.openlocfilehash: 19acff97a1541dcf6151b531696cf373e604371f
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/08/2022
ms.locfileid: "63566894"
---
# <a name="device-configuration"></a>تكوين الجهاز

<!--This topic is the target for a "Learn more" link in the Enterprise Agreement (aka.ms/dev-config); do not delete.-->

<!-- Device configuration and Security Addendum-->

عند إعداد جهاز Microsoft Managed Desktop جديد، نضمن تحسين التكوين لسطح المكتب المدار من Microsoft.

يتضمن التكوين مجموعة من السياسات الافتراضية التي تم تعيينها كجزء من عملية التهيئة. يتم تسليم هذه السياسات باستخدام إدارة أجهزة المحمول (MDM) كلما أمكن ذلك. لمزيد من المعلومات، راجع [إدارة أجهزة المحمول](/windows/client-management/mdm/).

>[!NOTE]
>لتجنب التعارضات، لا تغير هذه السياسات.

ستصل الأجهزة بصورة توقيع، ثم تنضم إلى مجال Azure Active Directory عند تسجيل المستخدم الأول الدخول. سيثبت الجهاز تلقائيا السياسات والتطبيقات المطلوبة دون أي تدخل من قبل موظفي المعلومات.

## <a name="default-policies"></a>السياسات الافتراضية

يسلط هذا الجدول الضوء على السياسات الافتراضية التي يتم تطبيقها على جميع أجهزة سطح المكتب المدارة من Microsoft أثناء توفير الجهاز. سيتم إعادة جميع التغييرات التي تم اكتشافها على الكائنات غير المعتمدة من قبل فريق عمليات سطح المكتب المدار من Microsoft والمدارة بواسطة Microsoft Managed Desktop.

| النهج | الوصف
| ----- | ----- |
| أساس الأمان | [يتم تكوين أساس أمان Microsoft](/windows/device-security/windows-security-baselines) لإدارة الأجهزة المحمولة لجميع أجهزة سطح المكتب المدارة من Microsoft. هذا الأساس هو التكوين القياسي في المجال. يتم إصداره بشكل عام واختباره ومراجعته من قبل خبراء أمان Microsoft للحفاظ على أمان أجهزة سطح المكتب المدارة من Microsoft والتطبيقات في مكان العمل الحديث. <br><br>للحد من التهديدات في مشهد التهديدات الأمنية المتغيرة باستمرار، سيتم تحديث أساس أمان Microsoft ونشره على أجهزة سطح المكتب المدارة من Microsoft مع كل تحديث Windows 10 تحديث.<br><br>لمزيد من المعلومات، [راجع Windows أساسيات الأمان](/windows/security/threat-protection/windows-security-baselines).
| قالب الأمان المستحسن لسطح المكتب المدار من Microsoft | هذا القالب هو مجموعة من التغييرات الموصى بها على أساس الأمان الذي يحسن تجربة المستخدم. تم توثيق هذه التغييرات [في ملحق الأمان](#security-addendum). تحدث تحديثات ملحق النهج حسب الحاجة.  
| تحديث النشر | استخدم Windows Update for Business لتنفيذ نشر تدريجي لتحديثات البرامج. لا يمكن لمسؤولي المعلومات تعديل الإعدادات لنهج مجموعة النشر. لمزيد من المعلومات حول النشر المستند إلى المجموعة، راجع كيفية معالجة التحديثات [في Microsoft Managed Desktop](updates.md).
| الاتصالات بالعدادات | بشكل افتراضي، يتم إيقاف تشغيل التحديثات عبر الاتصالات بالعدادات (مثل شبكات LTE). على الرغم من ذلك، يمكن لكل مستخدم تشغيل هذا الإعداد بشكل مستقل عن طريق الانتقال إلى الإعدادات ثم التحديثات **، ثم إلى خيارات متقدمة**. <br><br>إذا كنت تريد السماح لجميع المستخدمين بتمكين التحديثات عبر الاتصالات بالدفع، أرسل [](../working-with-managed-desktop/admin-support.md)طلب تغيير، الذي سيتم تشغيل هذا الإعداد لجميع الأجهزة.
| توافق الجهاز | تم تكوين هذه السياسات لجميع أجهزة سطح المكتب المدارة من Microsoft. يتم إعداد التقارير عن الجهاز على أنه غير متوافق عندما ينجراف من تكوين الأمان المطلوب.

## <a name="windows-diagnostic-data"></a>Windows التشخيصية

 سيتم تعيين الأجهزة لتوفير بيانات تشخيص محسنة ل Microsoft ضمن معرف تجاري معروف. كجزء من Microsoft Managed Desktop، لا يمكن لمسؤولي تقنيات المعلومات تغيير هذه الإعدادات.

بالنسبة للعملاء في مناطق القانون العام لحماية البيانات (GDPR)، يمكن للمستخدمين تقليل مستوى البيانات التشخيصية التي يتم توفيرها، ولكن سيتم تقليل الخدمة. على سبيل المثال، لن يتمكن Microsoft Managed Desktop من تجميع البيانات الضرورية للتكرير على الإعدادات والسياسات لخدمة الأداء واحتياجات الأمان على أفضل نحو. لمزيد من المعلومات، [راجع تكوين Windows التشخيصية في مؤسستك.](/windows/privacy/configure-windows-diagnostic-data-in-your-organization#enhanced-level)

## <a name="security-addendum"></a>ملحق الأمان

 يوضح هذا القسم الخطوط العريضة لنهج التي سيتم نشرها بالإضافة إلى سياسات Microsoft Managed Desktop القياسية المدرجة في [السياسات الافتراضية](#default-policies). تم تصميم هذا التكوين مع وضع الخدمات المالية والصناعات الخاضعة للتنظيم العالي في الاعتبار، كما تم تحسينه للحصول على أعلى مستوى من الأمان مع الحفاظ على إنتاجية المستخدم.

### <a name="additional-security-policies"></a>سياسات أمان إضافية

 تضاف هذه السياسات لزيادة الأمان في الصناعات الخاضعة للتنظيم بشكل كبير:

| النهج | الوصف |
| ----- | ----- |
|مراقبة الأمان | ستقوم Microsoft بمراقبة الأجهزة باستخدام [Microsoft Defender لنقطة النهاية](/windows/security/threat-protection/windows-defender-atp/windows-defender-advanced-threat-protection). إذا تم اكتشاف خطر، ستقوم Microsoft بإعلام العميل وعزل الجهاز وتصحيح المشكلة عن بعد. |
 | تعطيل PowerShell V2 | قامت Microsoft بإزالة PowerShell V2 في أغسطس 2017.<br><br>تم تعطيل هذه الميزة على جميع أجهزة سطح المكتب المدارة من Microsoft. لمزيد من المعلومات حول هذا التغيير، راجع Windows PowerShell [2.0.](https://devblogs.microsoft.com/powershell/windows-powershell-2-0-deprecation/) |
