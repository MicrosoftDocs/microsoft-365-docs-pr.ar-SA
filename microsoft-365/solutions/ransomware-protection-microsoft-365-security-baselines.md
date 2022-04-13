---
title: الخطوة 1. تكوين أساسات الأمان
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
keywords: برامج الفدية الضارة، برامج الفدية الضارة التي يديرها الإنسان، برامج الفدية الضارة التي يديرها الإنسان، هومور، الهجوم الهجمي، هجوم برامج الفدية الضارة، التشفير، فيروسات التشفير، الثقة الصفرية
description: استخدم أسس الأمان لحماية مواردك Microsoft 365 من هجمات برامج الفدية الضارة.
ms.openlocfilehash: 925a64e1d7852aeed6f596e99b20dbff8b34d1be
ms.sourcegitcommit: 195e4734d9a6e8e72bd355ee9f8bca1f18577615
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/13/2022
ms.locfileid: "64825091"
---
# <a name="step-1-configure-security-baselines"></a>الخطوة 1. تكوين أساسات الأمان

كخطوة أولى لمواجهة مهاجمي برامج الفدية الضارة، يجب تكوين خطوط الأمان الأساسية التالية المعرفة من قبل Microsoft:

- [الأمان في Microsoft 365](#microsoft-365-security-baseline)
- [إدارة البريد الإلكتروني Exchange](#exchange-email-management-baseline)
- [خطوط أساسية إضافية للأجهزة Windows وبرامج العميل](#additional-baselines)

تحتوي هذه الخطوط الأساسية على إعدادات التكوين وقواعد معروفة جيدا من قبل المهاجمين، والتي يتم ملاحظة غيابها بسرعة ويتم استغلالها بشكل شائع.

## <a name="microsoft-365-security-baseline"></a>أساس الأمان Microsoft 365

أولا، قم بتقييم وقياس وضع الأمان الخاص بك باستخدام [نقاط الأمان من Microsoft](/microsoft-365/security/defender/microsoft-secure-score) واتبع الإرشادات لتحسينه حسب الحاجة.

بعد ذلك، استخدم [قواعد تقليل الأجزاء المعرضة للهجوم](/microsoft-365/security/defender-endpoint/attack-surface-reduction-rules-deployment) للمساعدة في حظر النشاط المشبوه والمحتوى الضعيف. تتضمن هذه القواعد منع:

- كافة التطبيقات Office من إنشاء عمليات تابعة
- محتوى قابل للتنفيذ من عميل البريد الإلكتروني والبريد الإلكتروني
- الملفات القابلة للتنفيذ من التشغيل إلا إذا كانت تفي بمعيار الانتشار أو العمر أو القائمة الموثوق بها
- تنفيذ البرامج النصية التي يحتمل أن تكون مشتتة
- JavaScript أو VBScript من بدء تشغيل المحتوى القابل للتنفيذ الذي تم تنزيله
- Office التطبيقات من إنشاء محتوى قابل للتنفيذ
- Office التطبيقات من إدخال التعليمات البرمجية في عمليات أخرى
- Office تطبيق الاتصالات من إنشاء عمليات تابعة
- العمليات غير الموثوق بها وغير الموقعة التي يتم تشغيلها من USB
- الثبات من خلال اشتراك حدث واجهة إدارة Windows (WMI)
- سرقة بيانات الاعتماد من النظام الفرعي لسلطة الأمان المحلية Windows (lsass.exe)
- عمليات إنشاء العمليات التي تنشأ من أوامر PSExec وWMI

## <a name="exchange-email-management-baseline"></a>أساس إدارة البريد الإلكتروني Exchange

المساعدة في منع الوصول الأولي إلى المستأجر من هجوم مستند إلى البريد الإلكتروني باستخدام هذه الإعدادات الأساسية للبريد الإلكتروني Exchange:

- تمكين [فحص البريد الإلكتروني برنامج الحماية من الفيروسات من Microsoft Defender](/microsoft-365/security/defender-endpoint/configure-advanced-scan-types-microsoft-defender-antivirus).
- استخدم Microsoft Defender لـ Office 365 [لحماية التصيد الاحتيالي والتغطية المحسنة](/microsoft-365/security/office-365-security/anti-phishing-protection) ضد التهديدات الجديدة والمتغيرات متعددة الأشكال.
- تحقق من إعدادات تصفية البريد الإلكتروني Office 365 للتأكد من حظر رسائل البريد الإلكتروني المخادعة والبريد العشوائي ورسائل البريد الإلكتروني التي تحتوي على برامج ضارة. استخدم Defender لـ Office 365 لحماية التصيد الاحتيالي والتغطية المحسنة ضد التهديدات الجديدة والمتغيرات متعددة الأشكال. تكوين Defender لـ Office 365 [لإعادة تدقيق الارتباطات عند النقر فوق](/microsoft-365/security/office-365-security/atp-safe-links) [رسائل البريد التي تم تسليمها وحذفها](/microsoft-365/security/office-365-security/zero-hour-auto-purge) استجابة لذكاء التهديد الذي تم الحصول عليه حديثا.
- مراجعة أحدث [الإعدادات الموصى بها لأمان EOP والأمان Defender لـ Office 365](/microsoft-365/security/office-365-security/recommended-settings-for-eop-and-office365-atp) وتحديثها.
- تكوين Defender لـ Office 365 [لإعادة تدقيق الارتباطات عند النقر فوق](/microsoft-365/security/office-365-security/set-up-safe-links-policies) رسائل البريد التي تم تسليمها وحذفها استجابة لذكاء التهديد الذي تم الحصول عليه حديثا.

## <a name="additional-baselines"></a>خطوط أساسية إضافية

تطبيق [خطوط أساس الأمان](https://techcommunity.microsoft.com/t5/microsoft-security-baselines/bg-p/Microsoft-Security-Baselines) ل:

- Microsoft Windows 11 أو 10
- Microsoft 365 Apps للمؤسسة
- Microsoft Edge

## <a name="impact-on-users-and-change-management"></a>التأثير على المستخدمين وإدارة التغيير

كأفضل ممارسة لقاعدة تقليل الأجزاء المعرضة للهجوم، قم بتقييم كيفية تأثير القاعدة على شبكتك عن طريق فتح توصية الأمان لتلك القاعدة في إدارة المخاطر والثغرات الأمنية. يصف جزء تفاصيل التوصية تأثير المستخدم، والذي يمكنك استخدامه لتحديد النسبة المئوية التي يمكن أن تقبلها أجهزتك لنهج جديد يتيح القاعدة في وضع الحظر دون التأثير سلبا على إنتاجية المستخدم.

بالإضافة إلى ذلك، يمكن Exchange إعدادات أساس البريد الإلكتروني حظر البريد الإلكتروني الوارد ومنع إرسال البريد الإلكتروني أو النقر فوق الارتباطات داخل البريد الإلكتروني. اثقف عمالك على هذا السلوك وسبب اتخاذ هذه الاحتياطات.

## <a name="resulting-configuration"></a>التكوين الناتج

إليك حماية برامج الفدية الضارة للمستأجر الخاص بك بعد هذه الخطوة.

![حماية برامج الفدية الضارة لمستأجر Microsoft 365 بعد الخطوة 1](../media/ransomware-protection-microsoft-365/ransomware-protection-microsoft-365-architecture-step1.png)

## <a name="next-step"></a>الخطوة التالية

[![الخطوة 2 للحماية من برامج الفدية الضارة باستخدام Microsoft 365](../media/ransomware-protection-microsoft-365/ransomware-protection-microsoft-365-step2.png)](ransomware-protection-microsoft-365-attack-detection-response.md)

تابع [الخطوة 2](ransomware-protection-microsoft-365-attack-detection-response.md) لنشر قدرات الكشف عن الهجمات والاستجابة لها لمستأجر Microsoft 365 الخاص بك.
