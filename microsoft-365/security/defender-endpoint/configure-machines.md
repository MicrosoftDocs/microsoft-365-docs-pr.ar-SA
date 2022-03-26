---
title: التأكد من تكوين أجهزتك بشكل صحيح
description: قم بتكوين الأجهزة بشكل صحيح لتعزيز المرونة الشاملة ضد التهديدات وتحسين قدراتك للكشف عن الهجمات والاستجابة لها.
keywords: onboard, Intune management, Microsoft Defender for Endpoint, Microsoft Defender, Windows Defender, attack surface reduction, ASR, security baseline
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.custom: admindeeplinkDEFENDER
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: 61b275e5e42a10743eee744ab44bce48a25fa2eb
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 11/24/2021
ms.locfileid: "63572293"
---
# <a name="ensure-your-devices-are-configured-properly"></a>التأكد من تكوين أجهزتك بشكل صحيح

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**
- [خطة Microsoft Defender لنقطة النهاية 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> هل تريد تجربة Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-onboardconfigure-abovefoldlink)

باستخدام الأجهزة المكونة بشكل صحيح، يمكنك تعزيز المرونة الشاملة ضد التهديدات وتحسين قدراتك للكشف عن الهجمات والاستجابة لها. تساعد إدارة تكوين الأمان على ضمان أن أجهزتك:

- Onboard to Microsoft Defender for Endpoint
- تلبية تكوين الأساس لأساس أمان Defender لنقطة النهاية أو تجاوزه
- وضع عمليات التخفيف من المخاطر الاستراتيجية على سطح الهجوم في مكانها

انقر **فوق إدارة التكوين** من قائمة التنقل لفتح صفحة إدارة تكوين الجهاز.

![صفحة إدارة تكوين الأمان.](images/secconmgmt_main.png)

*صفحة إدارة تكوين الجهاز*

يمكنك تعقب حالة التكوين على مستوى المؤسسة واتخاذ الإجراءات بسرعة استجابة لتغطية سوء التهيئة، ومواصفات التوافق، وتحسينات سطح الهجوم بشكل غير جيد من خلال ارتباطات مباشرة وعمقية إلى صفحات إدارة الأجهزة على مدخل Microsoft Intune <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender</a>.

عند القيام بذلك، يمكنك الاستفادة من:

- رؤية شاملة للأحداث على أجهزتك
- الذكاء القوي للتهديدات وتقنيات تعلم الأجهزة القوية لمعالجة الأحداث الأولية وتحديد نشاط الانتهاك ومؤشرات التهديدات
- مجموعة كاملة من ميزات الأمان التي تم تكوينها لإيقاف تثبيت عمليات التثبيت الضارة بكفاءة، وتطفل ملفات النظام وعملية عملياته، وملء البيانات، وأنشطة التهديد الأخرى
- تقليل المخاطر المحسنة لسطح الهجوم، وزيادة الدفاعات الاستراتيجية إلى أقصى حد ضد نشاط التهديدات مع تقليل التأثير على الإنتاجية

## <a name="enroll-devices-to-intune-management"></a>تسجيل الأجهزة في إدارة Intune

تعمل إدارة تكوين الجهاز بشكل وثيق مع إدارة أجهزة Intune لإنشاء مخزون الأجهزة في مؤسستك وتكوين أمان الأساس. ستكون قادرا على تعقب مشاكل التكوين وإدارتها على أجهزة intune المدارة Windows الأجهزة.

قبل أن تتمكن من التأكد من تكوين أجهزتك بشكل صحيح، قم بتسجيلها في إدارة Intune. إن تسجيل Intune قوي ويشتد على العديد من خيارات التسجيل Windows الأجهزة. لمزيد من المعلومات حول خيارات تسجيل Intune، اقرأ حول [إعداد التسجيل للأجهزة Windows.](/intune/windows-enroll)

> [!NOTE]
> لتسجيل أجهزة Windows Intune، يجب أن يكون قد تم تعيين تراخيص للمسؤولين بالفعل. [اقرأ حول تعيين تراخيص تسجيل الجهاز](/intune/licenses-assign).

> [!TIP]
> لتحسين إدارة الأجهزة من خلال Intune، [قم بتوصيل Intune ب Defender for Endpoint](/intune/advanced-threat-protection#enable-windows-defender-atp-in-intune).

## <a name="obtain-required-permissions"></a>الحصول على الأذونات المطلوبة

بشكل افتراضي، يمكن فقط للمستخدمين الذين تم تعيينهم إلى "المسؤول العام" أو دور "مسؤول خدمة Intune" في Azure AD إدارة ملفات تعريف تكوين الجهاز المطلوبة لتهيئة الأجهزة وتعيينها للأجهزة التي تم تعيينها ونشر أساس الأمان.

إذا تم تعيين أدوار أخرى لك، فتأكد من أن لديك الأذونات اللازمة:

- الأذونات الكاملة لتكوينات الجهاز
- الأذونات الكاملة لأساسيات الأمان
- قراءة الأذونات لنهج توافق الأجهزة
- قراءة الأذونات إلى المؤسسة

![الأذونات المطلوبة في intune.](images/secconmgmt_intune_permissions.png)

*أذونات تكوين الجهاز على Intune*

> [!TIP]
> لمعرفة المزيد حول تعيين الأذونات على Intune، اقرأ [حول إنشاء أدوار مخصصة](/intune/create-custom-role#to-create-a-custom-role).

## <a name="in-this-section"></a>في هذا القسم

الموضوع|الوصف
:---|:---
[الحصول على الأجهزة المجهزة في Defender for Endpoint](configure-machines-onboarding.md)|تعقب حالة التكهين للأجهزة المدارة من Intune والمزيد من الأجهزة من خلال Intune. 
[زيادة التوافق مع خط أساسي أمان Defender for Endpoint](configure-machines-security-baseline.md)|تعقب توافق الأساس وعدم التوافق. نشر أساس الأمان إلى المزيد من أجهزة Intune المدارة.
[تحسين عمليات نشر قاعدة ASR واكتشافها](configure-machines-asr.md)|راجع عمليات نشر القواعد والكشف عن التعديلات باستخدام أدوات تحليل التأثير <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender المدخل</a>.

> هل تريد تجربة Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-onboardconfigure-belowfoldlink)
