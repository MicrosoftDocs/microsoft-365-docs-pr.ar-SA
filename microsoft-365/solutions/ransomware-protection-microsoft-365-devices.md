---
title: الخطوة 4. حماية الأجهزة
author: dansimp
f1.keywords:
- NOCSH
ms.author: dansimp
manager: dansimp
audience: ITPro
ms.topic: article
ms.prod: microsoft-365-enterprise
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
- Strat_O365_Enterprise
- ransomware
- m365solution-ransomware
ms.custom: seo-marvel-jun2020
keywords: برامج الفدية الضارة، برامج الفدية الضارة التي يتم تشغيلها من قبل الإنسان، برامج الفدية الضارة التي يتم تشغيلها من قبل الإنسان، هامور، هجوم مهين، هجوم برامج الفدية الضارة، التشفير، علم الفيروسات المشفرة، الثقة الصفرية
description: استخدم Windows Intune كموفر MDA و MAM Windows 10 أمان لحماية مواردك Microsoft 365 من هجمات برامج الفدية الضارة.
ms.openlocfilehash: 0d7b9a5e125c3f0478948340dce5677a3ae65395
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/08/2022
ms.locfileid: "63583679"
---
# <a name="step-4-protect-devices"></a>الخطوة 4. حماية الأجهزة

للمساعدة في حماية الأجهزة (نقاط النهاية) من جزء الوصول الأولي من هجوم برامج الفدية الضارة:

- نشر [Intune](/mem/intune/fundamentals/what-is-intune) كموفر لإدارة أجهزة المحمول (MDM) وموفر إدارة تطبيقات الأجهزة المحمولة (MAM) للأجهزة الخاصة بك، ثم سجل الأجهزة المملوكة لمنظمتك.
- تنفيذ سياسات [الوصول](/microsoft-365/security/office-365-security/identity-access-policies) إلى الأجهزة والهوية الشائعة للتحقق من صحة بيانات اعتماد حساب المستخدم وفرض متطلبات حماية الجهاز وتوافقه.
- تمكين [حماية الشبكة](/microsoft-365/security/defender-endpoint/network-protection) في Microsoft Defender لنقطة النهاية Microsoft 365 Defender.
- قم [بتكوين الموقع وتنزيل تدقيق](/windows/security/threat-protection/microsoft-defender-smartscreen/microsoft-defender-smartscreen-available-settings) التطبيقات [والتحقق من](/windows/security/threat-protection/microsoft-defender-smartscreen/microsoft-defender-smartscreen-available-settings) الملفات Microsoft Defender SmartScreen حظرها أو تحذيرها.
- تمكين [برنامج الحماية من الفيروسات من Microsoft Defender فحص](/microsoft-365/security/defender-endpoint/configure-advanced-scan-types-microsoft-defender-antivirus) الملفات والمرفقات التي تم تنزيلها.
- قم **بتعيين مستوى أمان سطح المكتب البعيد** إلى **TLS** في Microsoft Defender لنقطة النهاية Microsoft 365 Defender.

## <a name="windows-11-or-10-devices"></a>Windows 11 أو 10 أجهزة

للمساعدة في الحماية من جزء الحركة اللاحقة للهجوم من جهاز Windows 11 أو 10:

- [تشغيل جدار الحماية ل Microsoft Defender](https://support.microsoft.com/windows/turn-microsoft-defender-firewall-on-or-off-ec0844f7-aebd-0583-67fe-601ecf5d774f).
- [تحديث برنامج الحماية من الفيروسات من Microsoft Defender التعريفات](/microsoft-365/security/defender-endpoint/manage-updates-baselines-microsoft-defender-antivirus).

لتقليل تأثير الهجوم:

- استخدم [قواعد الحد من سطح الهجوم والحماية المتقدمة من برامج الفدية الضارة](/microsoft-365/security/defender-endpoint/attack-surface-reduction-rules-reference#use-advanced-protection-against-ransomware).

للمساعدة في الحماية ضد مهاجم يتجنب الدفاعات الأمنية الخاصة بك:

- احتفظ [بالحماية التي يتم تسليمها](/microsoft-365/security/defender-endpoint/enable-cloud-protection-microsoft-defender-antivirus) عبر السحابة برنامج الحماية من الفيروسات من Microsoft Defender تشغيلها.
- استمر برنامج الحماية من الفيروسات من Microsoft Defender [مراقبة](/microsoft-365/security/defender-endpoint/configure-real-time-protection-microsoft-defender-antivirus) سلوك الوقت الحقيقي.
- تشغيل [الحماية في الوقت الحقيقي](/microsoft-365/security/defender-endpoint/configure-real-time-protection-microsoft-defender-antivirus).
- قم تشغيل [الحماية من العبث في Microsoft Defender لنقطة](/microsoft-365/security/defender-endpoint/prevent-changes-to-security-settings-with-tamper-protection) النهاية لمنع إجراء تغييرات ضارة على إعدادات الأمان.

للمساعدة في الحماية من مهاجم ينفذ التعليمات البرمجية كجزء من هجوم:

- قم [برنامج الحماية من الفيروسات من Microsoft Defender.](/mem/intune/user-help/turn-on-defender-windows)
- [حظر مكالمات Win32 API من وحدات Office الماكرو](/microsoft-365/security/defender-endpoint/attack-surface-reduction-rules#block-win32-api-calls-from-office-macros).
- ترحيل كل المصنفات القديمة التي تتطلب وحدات ماكرو Excel 4.0 إلى تنسيق ماكرو VBA المحدث [باستخدام هذه العملية](https://www.microsoft.com/microsoft-365/blog/2010/02/16/migrating-excel-4-macros-to-vba/).
- [تعطيل استخدام وحدات الماكرو غير الموقعة](https://support.microsoft.com/topic/enable-or-disable-macros-in-office-files-12b036fd-d140-4e74-b45e-16fed1a7e5c6). تأكد من توقيع كل وحدات الماكرو الداخلية التي تحتاج إلى العمل [](/deployoffice/security/designate-trusted-locations-for-files-in-office) والاستفادة من المواقع الموثوق بها لضمان عدم تشغيل وحدات الماكرو غير المعروفة في بيئتك.
- إيقاف وحدات ماكرو XLM أو VBA الضارة من خلال ضمان تشغيل فحص الماكرو في وقت التشغيل بواسطة [واجهة](https://www.microsoft.com/security/blog/2021/03/03/xlm-amsi-new-runtime-defense-against-excel-4-0-macro-malware/) مسح البرامج الضارة (AMSI). يتم تشغيل هذه الميزة (التي يتم تمكينها بشكل افتراضي) إذا تم تعيين إعداد  نهج المجموعة لنطاق الفحص في وقت تشغيل الماكرو إلى **تمكين لكل** الملفات أو **تمكين الملفات ذات الثقة المنخفضة**. احصل على أحدث ملفات قوالب نهج المجموعة.

## <a name="impact-on-users-and-change-management"></a>التأثير على المستخدمين وإدارة التغيير

عند تنفيذ هذه الحماية، نفذ إدارة التغيير فيما يلي:

- يمكن [لنهج الوصول](/microsoft-365/security/office-365-security/identity-access-policies) إلى الأجهزة وهوية الصفر الشائعة رفض الوصول إلى المستخدمين الذين لديهم أجهزة غير متوافقة.
- قد يحذر تنزيل الملفات المستخدمين قبل التنزيل أو قد يتم حظره.
- قد Office تشغيل Excel 4.0 أو XLM أو VBA.

## <a name="resulting-configuration"></a>التكوين الناتج

إليك حماية برامج الفدية الضارة للمستأجر للحصول على الخطوات من 1 إلى 4.

![الحماية من برامج الفدية الضارة Microsoft 365 المستأجر بعد الخطوة 4](../media/ransomware-protection-microsoft-365/ransomware-protection-microsoft-365-architecture-step4.png)

## <a name="next-step"></a>الخطوة التالية

[![الخطوة 5 للحماية من برامج الفدية الضارة باستخدام Microsoft 365](../media/ransomware-protection-microsoft-365/ransomware-protection-microsoft-365-step5.png)](ransomware-protection-microsoft-365-information.md)

تابع مع [الخطوة 5](ransomware-protection-microsoft-365-information.md) لحماية المعلومات في Microsoft 365 المستأجر. 
