---
title: برنامج الحماية من الفيروسات من Microsoft Defender في Windows
description: تعرف على كيفية إدارة برنامج الحماية من الفيروسات من Microsoft Defender والحماية من البرامج الضارة والحماية من الفيروسات المضمنة وتكوينها واستخدامها.
keywords: برنامج الحماية من الفيروسات من Microsoft Defender، windows defender، مكافحة البرامج الضارة، scep، حماية نقطة نهاية مركز النظام، مدير تكوين مركز النظام، الفيروسات، البرامج الضارة، التهديد، الكشف، الحماية، الأمان
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
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/12/2022
ms.locfileid: "64790229"
---
# <a name="microsoft-defender-antivirus-in-windows"></a>برنامج الحماية من الفيروسات من Microsoft Defender في Windows

**ينطبق على:**

- [Microsoft Defender لنقطة النهاية الخطة 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- برنامج الحماية من الفيروسات من Microsoft Defender

**منصات**
- بالنسبة لنظام التشغيل 

يتوفر برنامج الحماية من الفيروسات من Microsoft Defender في Windows 10 Windows 11، وفي إصدارات Windows Server.

برنامج الحماية من الفيروسات من Microsoft Defender هو مكون رئيسي لحماية الجيل التالي في Microsoft Defender لنقطة النهاية. تجمع هذه الحماية بين التعلم الآلي وتحليل البيانات الضخمة والبحث المتعمق في مقاومة التهديدات والبنية الأساسية السحابية ل Microsoft لحماية الأجهزة (أو نقاط النهاية) في مؤسستك. برنامج الحماية من الفيروسات من Microsoft Defender مضمنة في Windows، وتعمل مع Microsoft Defender لنقطة النهاية لتوفير الحماية على جهازك وفي السحابة.

## <a name="compatibility-with-other-antivirus-products"></a>التوافق مع منتجات مكافحة الفيروسات الأخرى

إذا كنت تستخدم منتجا غير تابع لبرامج الحماية من الفيروسات/البرامج الضارة من Microsoft على جهازك، فقد تتمكن من تشغيل برنامج الحماية من الفيروسات من Microsoft Defender في الوضع الخامل إلى جانب حل مكافحة الفيروسات غير التابع ل Microsoft. يعتمد ذلك على نظام التشغيل المستخدم وما إذا كان جهازك قد تم إلحاقه ب Defender لنقطة النهاية. لمعرفة المزيد، راجع [توافق برنامج الحماية من الفيروسات من Microsoft Defender](microsoft-defender-antivirus-compatibility.md).

## <a name="comparing-active-mode-passive-mode-and-disabled-mode"></a>مقارنة الوضع النشط، ووضع الخامل، ووضع التعطيل

يصف الجدول التالي ما يجب توقعه عندما يكون برنامج الحماية من الفيروسات من Microsoft Defender في الوضع النشط أو الوضع السلبي أو معطلا.

<br/><br/>

| وضع | ماذا يحدث |
|---|---|
| الوضع النشط | في الوضع النشط، يتم استخدام برنامج الحماية من الفيروسات من Microsoft Defender كتطبيق الحماية من الفيروسات الأساسي على الجهاز. يتم مسح الملفات ضوئيا، ومعالجة التهديدات، وسرد التهديدات المكتشفة في تقارير الأمان الخاصة بمؤسستك وفي تطبيق أمن Windows. |
| الوضع السلبي | في الوضع السلبي، لا يتم استخدام برنامج الحماية من الفيروسات من Microsoft Defender كتطبيق الحماية من الفيروسات الأساسي على الجهاز. يتم مسح الملفات ضوئيا، ويتم الإبلاغ عن التهديدات المكتشفة، ولكن لا تتم معالجة التهديدات بواسطة برنامج الحماية من الفيروسات من Microsoft Defender. <br/><br/> **هام**: يمكن تشغيل برنامج الحماية من الفيروسات من Microsoft Defender في الوضع الخامل فقط على نقاط النهاية التي تم إلحاقها Microsoft Defender لنقطة النهاية. راجع [متطلبات تشغيل برنامج الحماية من الفيروسات من Microsoft Defender في الوضع الخامل](microsoft-defender-antivirus-compatibility.md#requirements-for-microsoft-defender-antivirus-to-run-in-passive-mode). |
| معطل أو غير مثبت | عند التعطيل أو إلغاء التثبيت، لا يتم استخدام برنامج الحماية من الفيروسات من Microsoft Defender. لا يتم مسح الملفات ضوئيا، ولا تتم معالجة التهديدات. بشكل عام، لا نوصي بتعطيل أو إلغاء تثبيت برنامج الحماية من الفيروسات من Microsoft Defender. |

لمعرفة المزيد، راجع [توافق برنامج الحماية من الفيروسات من Microsoft Defender](microsoft-defender-antivirus-compatibility.md).

## <a name="check-the-state-of-microsoft-defender-antivirus-on-your-device"></a>التحقق من حالة برنامج الحماية من الفيروسات من Microsoft Defender على جهازك

إذا كنت تريد التحقق من حالة برنامج الحماية من الفيروسات من Microsoft Defender على جهازك، يمكنك استخدام أحد الأساليب المتعددة، مثل تطبيق أمن Windows أو Windows PowerShell.

### <a name="use-the-windows-security-app-to-check-status-of-microsoft-defender-antivirus"></a>استخدم تطبيق أمن Windows للتحقق من حالة برنامج الحماية من الفيروسات من Microsoft Defender

1. على جهازك Windows، حدد قائمة البدء، وابدأ الكتابة`Security`. ثم افتح تطبيق أمن Windows في النتائج.

2. حدد **الحماية من التهديدات & الفيروسات**.

3. ضمن **إعدادات الحماية من الفيروسات &،** اختر **"إدارة الإعدادات**".

سترى اسم حل الحماية من الفيروسات/الحماية من البرامج الضارة على صفحة الإعدادات.

### <a name="use-powershell-to-check-status-of-microsoft-defender-antivirus"></a>استخدام PowerShell للتحقق من حالة برنامج الحماية من الفيروسات من Microsoft Defender

1. حدد قائمة البدء، وابدأ الكتابة`PowerShell`. ثم افتح Windows PowerShell في النتائج.

2. اكتب `Get-MpComputerStatus`.

3. في قائمة النتائج، انظر إلى صف **AMRunningMode** .

   - **تعني الوسائل العادية** أن برنامج الحماية من الفيروسات من Microsoft Defender قيد التشغيل في الوضع النشط.

   - **يعني الوضع السلبي** برنامج الحماية من الفيروسات من Microsoft Defender قيد التشغيل، ولكنه ليس منتج مكافحة الفيروسات/مكافحة البرامج الضارة الأساسي على جهازك. يتوفر الوضع السلبي فقط للأجهزة التي تم إلحاقها Microsoft Defender لنقطة النهاية والتي تفي بمتطلبات معينة. لمعرفة المزيد، راجع [متطلبات تشغيل برنامج الحماية من الفيروسات من Microsoft Defender في الوضع السلبي](microsoft-defender-antivirus-compatibility.md#requirements-for-microsoft-defender-antivirus-to-run-in-passive-mode).

   - **الكشف التلقائي والاستجابة على النقط النهائية يعني وضع الحظر** تشغيل برنامج الحماية من الفيروسات من Microsoft Defender [والكشف عن نقطة النهاية والاستجابة لها (الكشف التلقائي والاستجابة على النقط النهائية) في وضع الحظر](edr-in-block-mode.md)، تم تمكين القدرة في Microsoft Defender لنقطة النهاية.

   - يعني **وضع SxS الخامل** أن برنامج الحماية من الفيروسات من Microsoft Defender يعمل جنبا إلى جنب مع منتج آخر من برامج الحماية من الفيروسات/الحماية من البرامج الضارة، [ويتم استخدام فحص دوري محدود](limited-periodic-scanning-microsoft-defender-antivirus.md).

> [!TIP]
> لمعرفة المزيد حول Get-MpComputerStatus PowerShell cmdlet، راجع المقالة المرجعية [Get-MpComputerStatus](/powershell/module/defender/get-mpcomputerstatus).

## <a name="get-your-antivirusantimalware-platform-updates"></a>الحصول على تحديثات النظام الأساسي لمكافحة الفيروسات/الحماية من البرامج الضارة

من المهم الحفاظ على تحديث برنامج الحماية من الفيروسات من Microsoft Defender أو أي حل لمكافحة الفيروسات/البرامج الضارة. تصدر Microsoft تحديثات منتظمة للمساعدة في ضمان أن أجهزتك لديها أحدث التقنيات للحماية من البرامج الضارة الجديدة وتقنيات الهجوم. لمعرفة المزيد، راجع [إدارة تحديثات برنامج الحماية من الفيروسات من Microsoft Defender وتطبيق الخطوط الأساسية](manage-updates-baselines-microsoft-defender-antivirus.md).

> [!TIP]
> إذا كنت تبحث عن معلومات متعلقة بالحماية من الفيروسات للأنظمة الأساسية الأخرى، فراجع:
> - [تعيين تفضيلات Microsoft Defender لنقطة النهاية على macOS](mac-preferences.md)
> - [Microsoft Defender لنقطة النهاية على Mac](microsoft-defender-endpoint-mac.md)
> - [إعدادات نهج الحماية من الفيروسات في macOS ل برنامج الحماية من الفيروسات من Microsoft Defender ل Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [تعيين تفضيلات Microsoft Defender لنقطة النهاية على Linux](linux-preferences.md)
> - [مشكلات الأداء في Microsoft Defender لنقطة النهاية على Linux](microsoft-defender-endpoint-linux.md)
> - [تكوين Defender لنقطة النهاية على ميزات Android](android-configure.md)
> - [تكوين Microsoft Defender لنقطة النهاية على ميزات iOS](ios-configure-features.md)

## <a name="see-also"></a>راجع أيضًا

- [برنامج الحماية من الفيروسات من Microsoft Defender الإدارة والتكوين](configuration-management-reference-microsoft-defender-antivirus.md)
- [تقييم حماية برنامج الحماية من الفيروسات من Microsoft Defender](evaluate-microsoft-defender-antivirus.md)
