---
title: برنامج الحماية من الفيروسات من Microsoft Defender في Windows
description: تعرف على كيفية إدارة برنامج الحماية من الفيروسات من Microsoft Defender والحماية من البرامج الضارة المضمنة والحماية من الفيروسات وتكوينها واستخدامها.
keywords: برنامج الحماية من الفيروسات من Microsoft Defender، windows defender، الحماية من البرامج الضارة، scep، حماية نقطة نهاية مركز النظام، إدارة تكوين مركز النظام، الفيروسات، البرامج الضارة، التهديد، الكشف، الحماية، الأمان
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: high
ms.topic: article
author: denisebmsft
ms.author: deniseb
ms.reviewer: mkaminska
manager: dansimp
ms.custom: nextgen
ms.technology: mde
ms.collection:
- M365-security-compliance
- m365initiative-defender-endpoint
ms.openlocfilehash: 352b60caa3af581a5d1162b1896b255bfcea873c
ms.sourcegitcommit: 4f56b4b034267b28c7dd165e78ecfb4b5390087d
ms.translationtype: HT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/12/2022
ms.locfileid: "64790229"
---
# <a name="microsoft-defender-antivirus-in-windows"></a>برنامج الحماية من الفيروسات من Microsoft Defender في Windows

**ينطبق على:**

- [Defender for Endpoint الخطة 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- برنامج الحماية من الفيروسات من Microsoft Defender

**الأنظمة الأساسية**
- بالنسبة لنظام التشغيل 

يتوفر برنامج الحماية من الفيروسات من Microsoft Defender في Windows 10 وWindows 11 وفي إصدارات Windows Server.

برنامج الحماية من الفيروسات من Microsoft Defender هو مكون رئيسي لحماية الجيل التالي في Microsoft Defender لنقطة النهاية. تجمع هذه الحماية بين التعلم الآلي وتحليل البيانات الضخمة والبحث المتعمق في مقاومة المخاطر والبنية الأساسية لسحابة Microsoft لحماية الأجهزة (أو نقاط النهاية) في مؤسستك. برنامج الحماية من الفيروسات من Microsoft Defender مضمن في Windows، ويعمل مع Microsoft Defender لنقطة النهاية لتوفير الحماية على جهازك وفي السحابة.

## <a name="compatibility-with-other-antivirus-products"></a>التوافق مع منتجات مكافحة الفيروسات الأخرى

إذا كنت تستخدم منتجا غير تابع لـ Microsoft للحماية من الفيروسات/الحماية من البرامج الضارة على جهازك، فقد تتمكن من تشغيل برنامج الحماية من الفيروسات من Microsoft Defender في الوضع السلبي إلى جانب حل الحماية من الفيروسات غير التابع ل Microsoft. يعتمد ذلك على نظام التشغيل المستخدم وما إذا تم إلحاق جهازك ب Defender لنقطة النهاية. لمعرفة المزيد، راجع [توافق برنامج الحماية من الفيروسات من Microsoft Defender](microsoft-defender-antivirus-compatibility.md).

## <a name="comparing-active-mode-passive-mode-and-disabled-mode"></a>مقارنة الوضع النشط ووضع الخامل ووضع التعطيل

يصف الجدول التالي ما يجب توقعه عندما يكون برنامج الحماية من الفيروسات من Microsoft Defender في الوضع النشط أو الوضع الخامل أو معطلا.

<br/><br/>

| الوضع | ما يحدث |
|---|---|
| الوضع النشط | في الوضع النشط، يتم استخدام برنامج الحماية من الفيروسات من Microsoft Defender كتطبيق مكافحة الفيروسات الأساسي على الجهاز. يتم فحص الملفات، وتتم معالجة التهديدات، ويتم سرد التهديدات المكتشفة في تقارير الأمان الخاصة بمؤسستك وفي تطبيق أمن Windows. |
| الوضع السلبي | في الوضع السلبي، لا يتم استخدام برنامج الحماية من الفيروسات من Microsoft Defender كتطبيق الحماية من الفيروسات الأساسي على الجهاز. يتم فحص الملفات، ويتم الإبلاغ عن التهديدات المكتشفة، ولكن لا تتم معالجة التهديدات بواسطة برنامج الحماية من الفيروسات من Microsoft Defender. <br/><br/> **هام**: يمكن تشغيل برنامج الحماية من الفيروسات من Microsoft Defender في الوضع الخامل فقط على نقاط النهاية التي تم إلحاقها بـ Microsoft Defender لنقطة النهاية. راجع [متطلبات تشغيل برنامج الحماية من الفيروسات من Microsoft Defender في الوضع الخامل](microsoft-defender-antivirus-compatibility.md#requirements-for-microsoft-defender-antivirus-to-run-in-passive-mode). |
| معطل أو غير مثبت | عند التعطيل أو إزالة التثبيت، لا يتم استخدام برنامج الحماية من الفيروسات من Microsoft Defender. لم يتم فحص الملفات، ولم تتم معالجة التهديدات. بشكل عام، لا نوصي بتعطيل برنامج الحماية من الفيروسات من Microsoft Defender أو إلغاء تثبيتها. |

لمعرفة المزيد، راجع [توافق برنامج الحماية من الفيروسات من Microsoft Defender](microsoft-defender-antivirus-compatibility.md).

## <a name="check-the-state-of-microsoft-defender-antivirus-on-your-device"></a>التحقق من حالة برنامج الحماية من الفيروسات من Microsoft Defender على جهازك

إذا كنت تريد التحقق من حالة برنامج الحماية من الفيروسات من Microsoft Defender على جهازك، فيمكنك استخدام إحدى الطرق المتعددة، مثل تطبيق أمن Windows أو Windows PowerShell.

### <a name="use-the-windows-security-app-to-check-status-of-microsoft-defender-antivirus"></a>استخدم تطبيق أمن Windows للتحقق من حالة برنامج الحماية من الفيروسات من Microsoft Defender

1. على جهاز Windows، حدد قائمة البدء، وابدأ بالكتابة `Security`. ثم افتح تطبيق أمن Windows في النتائج.

2. حدد **الحماية من الفيروسات والمخاطر**.

3. ضمن إعدادات **الحماية من الفيروسات والمخاطر**، اختر **إدارة الإعدادات**.

سترى اسم حل الحماية من الفيروسات/الحماية من البرامج الضارة على صفحة الإعدادات.

### <a name="use-powershell-to-check-status-of-microsoft-defender-antivirus"></a>استخدام PowerShell للتحقق من حالة برنامج الحماية من الفيروسات من Microsoft Defender

1. حدد قائمة البدء، وابدأ الكتابة `PowerShell`. ثم افتح Windows PowerShell في النتائج.

2. النوع `Get-MpComputerStatus`.

3. في قائمة النتائج، انظر إلى صف **AMRunningMode**.

   - تعني **العادية** تشغيل برنامج الحماية من الفيروسات من Microsoft Defender في الوضع النشط.

   - يعني **الوضع الخامل** تشغيل برنامج الحماية من الفيروسات من Microsoft Defender، ولكنه ليس منتج الحماية من الفيروسات/الحماية من البرامج الضارة الأساسي على جهازك. يتوفر الوضع السلبي فقط للأجهزة التي تم إلحاقها ب Microsoft Defender لنقطة النهاية والتي تفي بمتطلبات معينة. لمعرفة المزيد، راجع [متطلبات تشغيل برنامج الحماية من الفيروسات من Microsoft Defender في الوضع الخامل](microsoft-defender-antivirus-compatibility.md#requirements-for-microsoft-defender-antivirus-to-run-in-passive-mode).

   - يعني **وضع حظر EDR** أن برنامج الحماية من الفيروسات من Microsoft Defender قيد التشغيل وأن [الكشف والاستجابة لنقطة النهاية (EDR) في وضع الحظر](edr-in-block-mode.md)، وهي إمكانية في Microsoft Defender لنقطة النهاية.

   - يعني **وضع SxS الخامل** تشغيل برنامج الحماية من الفيروسات من Microsoft Defender إلى جانب منتج آخر للحماية من الفيروسات/البرامج الضارة، ويتم استخدام  [الفحص الدوري المحدود](limited-periodic-scanning-microsoft-defender-antivirus.md).

> [!TIP]
> لمعرفة المزيد حول Get-MpComputerStatus PowerShell cmdlet، راجع المقالة المرجعية [Get-MpComputerStatus](/powershell/module/defender/get-mpcomputerstatus).

## <a name="get-your-antivirusantimalware-platform-updates"></a>الحصول على تحديثات النظام الأساسي للحماية من الفيروسات/الحماية من البرامج الضارة

من المهم الحفاظ على تحديث برنامج الحماية من الفيروسات من Microsoft Defender أو أي حل للحماية من الفيروسات/الحماية من البرامج الضارة. تصدر Microsoft تحديثات منتظمة للمساعدة في ضمان حصول أجهزتك على أحدث التقنيات للحماية من البرامج الضارة وتقنيات الهجوم الجديدة. لمعرفة المزيد، راجع [إدارة تحديثات برنامج الحماية من الفيروسات من Microsoft Defender وتطبيق الخطوط الأساسية](manage-updates-baselines-microsoft-defender-antivirus.md).

> [!TIP]
> إذا كنت’ تبحث عن معلومات متعلقة بالحماية من الفيروسات للأنظمة الأساسية الأخرى، فراجع:
> - [تعيين تفضيلات Microsoft Defender لنقطة النهاية على نظام التشغيل macOS](mac-preferences.md)
> - [Microsoft Defender for Endpoint على Mac](microsoft-defender-endpoint-mac.md)
> - [إعدادات نهج برنامج الحماية من الفيروسات في macOS لبرنامج الحماية من الفيروسات من Microsoft Defender Antivirus for Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [تعيين تفضيلات Microsoft Defender لنقطة النهاية على Linux](linux-preferences.md)
> - [مشكلات الأداء في Microsoft Defender لنقطة النهاية على Linux](microsoft-defender-endpoint-linux.md)
> - [تكوين Defender for Endpoint على ميزات Android](android-configure.md)
> - [تكوين Microsoft Defender for Endpoint على ميزات iOS](ios-configure-features.md)

## <a name="see-also"></a>راجع أيضًا

- [إدارة برنامج الحماية من الفيروسات من Microsoft Defender وتكوينه](configuration-management-reference-microsoft-defender-antivirus.md)
- [تقييم برنامج الحماية من الفيروسات من Microsoft Defender](evaluate-microsoft-defender-antivirus.md)
