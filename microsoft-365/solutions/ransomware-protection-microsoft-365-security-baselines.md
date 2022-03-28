---
title: الخطوة 1. تكوين خطوط الأمان الأساسية
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
description: استخدم خطوط الأمان الأساسية لحماية مواردك Microsoft 365 برامج الفدية الضارة.
ms.openlocfilehash: 22092994765e9015421c21f2ee057c63463d594d
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/08/2022
ms.locfileid: "63575862"
---
# <a name="step-1-configure-security-baselines"></a>الخطوة 1. تكوين خطوط الأمان الأساسية

كخطوة أولى لمكافحة مهاجمي برامج الفدية الضارة، يجب تكوين خطوط الأمان الأساسية التالية المعرفة من قبل Microsoft:

- [Microsoft 365 الأمان](#microsoft-365-security-baseline)
- [Exchange البريد الإلكتروني](#exchange-email-management-baseline)
- [خطوط أساسية إضافية Windows وبرامج العميل](#additional-baselines)

تحتوي هذه الأساسات على إعدادات التكوين والقواعد المعروفة من قبل المهاجمين، والتي يتم ملاحظة عدم وجودها بسرعة ويتم استغلالها بشكل شائع.

## <a name="microsoft-365-security-baseline"></a>Microsoft 365 أساسي أمان

أولا، تقييم وضع الأمان الخاص بك وتقييسه باستخدام [Microsoft Secure Score](/microsoft-365/security/defender/microsoft-secure-score) واتبع الإرشادات لتحسينه حسب الحاجة.

بعد ذلك، استخدم [قواعد](/microsoft-365/security/defender-endpoint/attack-surface-reduction-rules-deployment) الحد من سطح الهجوم للمساعدة في حظر النشاط المريب والمحتوى المعرض. تتضمن هذه القواعد منع:

- جميع Office من إنشاء عمليات الطفل
- محتوى قابل للتنفيذ من عميل البريد الإلكتروني والبريد الإلكتروني
- الملفات القابلة للتنفيذ من التشغيل إلا إذا كانت تلبي معيار قائمة ذات عمر أو عمر أو قائمة موثوق بها
- تنفيذ البرامج النصية التي يحتمل أن تكون غير مهية
- JavaScript أو VBScript من بدء تشغيل محتوى قابل للتنفيذ تم تنزيله
- Office تطبيقات من إنشاء محتوى قابل للتنفيذ
- Office التطبيقات من إدخال التعليمات البرمجية في عمليات أخرى
- Office تطبيق الاتصالات من إنشاء عمليات الطفل
- العمليات غير الملوثة وغير الموقعة التي يتم تشغيلها من USB
- الاستمرار عبر Windows حدث واجهة الإدارة (WMI)
- سرقة بيانات الاعتماد من Windows فرعي لسلطات الأمان المحلية (lsass.exe)
- إنشاءات العمليات التي تنشأ من أوامر PSExec و WMI

## <a name="exchange-email-management-baseline"></a>Exchange أساسي لإدارة البريد الإلكتروني 

المساعدة على منع الوصول الأولي إلى المستأجر من هجوم مستند إلى البريد الإلكتروني باستخدام إعدادات Exchange الأساسية للبريد الإلكتروني:

- تمكين [برنامج الحماية من الفيروسات من Microsoft Defender البريد الإلكتروني](/microsoft-365/security/defender-endpoint/configure-advanced-scan-types-microsoft-defender-antivirus).
- استخدم Microsoft Defender Office 365 [الحماية](/microsoft-365/security/office-365-security/anti-phishing-protection) من التصيد الاحتيالي والتغطية ضد التهديدات الجديدة والمتغيرات المتعددة الأشكال.
- تحقق من Office 365 تصفية البريد الإلكتروني للتأكد من حظر رسائل البريد الإلكتروني المنتحلة والبريد العشوائي ورسائل البريد الإلكتروني باستخدام البرامج الضارة. استخدم Defender Office 365 الحماية من التصيد الاحتيالي والتغطية ضد التهديدات الجديدة والمتغيرات المتعددة الأشكال. قم بتكوين Defender Office 365 إعادة [فحص](/microsoft-365/security/office-365-security/atp-safe-links) الارتباطات عند النقر فوق رسائل البريد التي [](/microsoft-365/security/office-365-security/zero-hour-auto-purge) تم تسليمها وحذفها استجابة لذكاء التهديدات الذي تم الحصول عليه حديثا.
- راجع أحدث الإعدادات التي تم إصدارها وتحديثها ل  [EOP و Defender Office 365 الأمان](/microsoft-365/security/office-365-security/recommended-settings-for-eop-and-office365-atp).
- قم بتكوين Defender Office 365 إعادة [فحص](/microsoft-365/security/office-365-security/set-up-safe-links-policies) الارتباطات عند النقر فوق رسائل البريد التي تم تسليمها وحذفها استجابة لذكاء التهديدات الذي تم الحصول عليه حديثا.

## <a name="additional-baselines"></a>خطوط أساسية إضافية

تطبيق [خطوط الأمان الأساسية](https://techcommunity.microsoft.com/t5/microsoft-security-baselines/bg-p/Microsoft-Security-Baselines) ل:

- Microsoft Windows 11 أو 10
- Microsoft 365 Apps للمؤسسات
- Microsoft Edge

## <a name="impact-on-users-and-change-management"></a>التأثير على المستخدمين وإدارة التغيير

كأفضل ممارسة لقاعدة تقليل مساحة الهجوم، يمكنك تقييم كيفية تأثير القاعدة على شبكتك من خلال فتح توصية الأمان لهذه القاعدة في إدارة المخاطر والثغرات الأمنية. يصف جزء تفاصيل التوصية تأثير المستخدم، الذي يمكنك استخدامه لتحديد النسبة المئوية للأجهزة التي يمكن أن تقبل نهج جديد لتمكين القاعدة في وضع الحظر دون التأثير سلبا على إنتاجية المستخدم.

بالإضافة إلى Exchange يمكن أن تمنع إعدادات أساس البريد الإلكتروني البريد الإلكتروني الوارد وتمنع إرسال البريد الإلكتروني أو النقر فوق الارتباطات داخل البريد الإلكتروني. قم بتثقيف العاملين لديك حول هذا السلوك وسبب اتخاذ هذه الاحتياطات.

## <a name="resulting-configuration"></a>التكوين الناتج

إليك حماية برامج الفدية الضارة للمستأجر بعد هذه الخطوة.

![الحماية من برامج الفدية الضارة Microsoft 365 المستأجر بعد الخطوة 1](../media/ransomware-protection-microsoft-365/ransomware-protection-microsoft-365-architecture-step1.png)


## <a name="next-step"></a>الخطوة التالية

[![الخطوة 2 للحماية من برامج الفدية الضارة باستخدام Microsoft 365](../media/ransomware-protection-microsoft-365/ransomware-protection-microsoft-365-step2.png)](ransomware-protection-microsoft-365-attack-detection-response.md)

تابع مع [الخطوة 2](ransomware-protection-microsoft-365-attack-detection-response.md) لنشر قدرات الكشف عن الهجمات والاستجابة لها Microsoft 365 المستأجر.
