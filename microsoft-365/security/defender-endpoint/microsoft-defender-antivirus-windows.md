---
title: برنامج الحماية من الفيروسات ل Microsoft Defender في Windows
description: تعرف على كيفية إدارة برنامج الحماية من الفيروسات من Microsoft Defender وتكوينه واستخدامه، وهو برنامج الحماية من البرامج الضارة والحماية من الفيروسات المضمن.
keywords: Microsoft Defender Antivirus، windows defender، مكافحة البرامج الضارة، scep، حماية نقطة نهاية مركز النظام، إدارة تكوين مركز النظام، الفيروسات، البرامج الضارة، التهديدات، الكشف، الحماية، الأمان
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
ms.openlocfilehash: b6eabc3527742b6cc7f06d23207db813b827e5f5
ms.sourcegitcommit: aac7e002ec6e10a41baa2d0bd38614b0ed471a70
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 01/27/2022
ms.locfileid: "63573987"
---
# <a name="microsoft-defender-antivirus-in-windows"></a>برنامج الحماية من الفيروسات ل Microsoft Defender في Windows

**ينطبق على:**
- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- Microsoft Defender Antivirus

يتوفر برنامج الحماية من الفيروسات ل Microsoft Defender في Windows 10 و Windows 11، وفي إصدارات Windows Server.

إن برنامج الحماية من الفيروسات ل Microsoft Defender هو مكون رئيسي لحماية الجيل التالي في Microsoft Defender لنقطة النهاية. تجمع هذه الحماية بين التعلم الآلي وتحليل البيانات الكبيرة وأبحاث معمقة لمقاومة المخاطر والبنية الأساسية لسحابة Microsoft لحماية الأجهزة (أو نقاط النهاية) في مؤسستك. إن برنامج الحماية من الفيروسات ل Microsoft Defender مضمن في Windows، ويعمل مع Microsoft Defender ل Endpoint لتوفير الحماية على جهازك وفي السحابة.

## <a name="compatibility-with-other-antivirus-products"></a>التوافق مع منتجات الحماية من الفيروسات الأخرى

إذا كنت تستخدم منتجا غير Microsoft antivirus/antimalware على جهازك، فقد تتمكن من تشغيل Microsoft Defender Antivirus في الوضع السلبي إلى جانب حل مكافحة الفيروسات غير Microsoft. يعتمد ذلك على نظام التشغيل المستخدم وما إذا كان جهازك م في وضع التشغيل في Defender for Endpoint. لمعرفة المزيد، راجع [توافق برنامج الحماية من الفيروسات ل Microsoft Defender](microsoft-defender-antivirus-compatibility.md).

## <a name="comparing-active-mode-passive-mode-and-disabled-mode"></a>مقارنة الوضع النشط، ووضع السلبي، ووضع المعطل

يصف الجدول التالي ما يجب توقعه عندما يكون Microsoft Defender Antivirus في الوضع النشط أو الوضع السلبي أو معطلا.

<br/><br/>

| الوضع | ماذا يحدث |
|---|---|
| الوضع النشط | في الوضع النشط، يتم استخدام برنامج الحماية من الفيروسات ل Microsoft Defender ك تطبيق الحماية من الفيروسات الأساسي على الجهاز. يتم فحص الملفات، كما يتم معالجة التهديدات، كما يتم سرد التهديدات التي تم الكشف عنها في تقارير الأمان الخاصة بالم مؤسستك وفي تطبيق Windows Security. |
| الوضع السلبي | في الوضع السلبي، لا يتم استخدام برنامج الحماية من الفيروسات ل Microsoft Defender ك تطبيق الحماية من الفيروسات الأساسي على الجهاز. يتم مسح الملفات ضوئيا، كما يتم إعداد التقارير عن التهديدات، ولكن لا يتم معالجة التهديدات بواسطة برنامج الحماية من الفيروسات ل Microsoft Defender. <br/><br/> **هام**: يمكن تشغيل برنامج الحماية من الفيروسات ل Microsoft Defender في الوضع السلبي فقط على نقاط النهاية التي تم تشغيلها في Microsoft Defender لنقطة النهاية. راجع [متطلبات تشغيل برنامج الحماية من الفيروسات ل Microsoft Defender في الوضع السلبي](microsoft-defender-antivirus-compatibility.md#requirements-for-microsoft-defender-antivirus-to-run-in-passive-mode). |
| معطل أو غير م تثبيت | عند تعطيله أو إلغاء تثبيته، لا يتم استخدام برنامج الحماية من الفيروسات ل Microsoft Defender. لا يتم فحص الملفات، ولا يتم معالجة التهديدات. بشكل عام، لا نوصي بتعطيل Microsoft Defender Antivirus أو إلغاء تثبيته. |

لمعرفة المزيد، راجع [توافق برنامج الحماية من الفيروسات ل Microsoft Defender](microsoft-defender-antivirus-compatibility.md).

## <a name="check-the-state-of-microsoft-defender-antivirus-on-your-device"></a>التحقق من حالة برنامج الحماية من الفيروسات ل Microsoft Defender على جهازك

إذا كنت تريد التحقق من حالة برنامج الحماية من الفيروسات ل Microsoft Defender على جهازك، يمكنك استخدام أحد الأساليب العديدة، مثل تطبيق Windows Security أو Windows PowerShell.

### <a name="use-the-windows-security-app-to-check-status-of-microsoft-defender-antivirus"></a>استخدام تطبيق Windows Security للتحقق من حالة برنامج الحماية من الفيروسات ل Microsoft Defender

1. على جهاز Windows، حدد قائمة البدء، وابدأ الكتابة `Security`. ثم افتح تطبيق Windows Security في النتائج.

2. حدد **الحماية من & الفيروسات**.

3. ضمن **إعدادات الحماية & الفيروسات،** اختر **إدارة الإعدادات**.

سترى اسم حل الحماية من الفيروسات/مكافحة البرامج الضارة على صفحة الإعدادات.

### <a name="use-powershell-to-check-status-of-microsoft-defender-antivirus"></a>استخدام PowerShell للتحقق من حالة برنامج الحماية من الفيروسات ل Microsoft Defender

1. حدد قائمة البدء، وابدأ بالكتابة `PowerShell`. ثم افتح Windows PowerShell في النتائج.

2. اكتب `Get-MpComputerStatus`.

3. في قائمة النتائج، انظر إلى **الصف AMRunningMode** .

   - **عادي** يعني أن برنامج الحماية من الفيروسات ل Microsoft Defender قيد التشغيل في الوضع النشط.

   - **الوضع السلبي يعني** أن Microsoft Defender Antivirus قيد التشغيل، ولكنه ليس منتج الحماية من الفيروسات/البرامج الضارة الأساسي على جهازك. يتوفر الوضع السلبي فقط للأجهزة التي تم تشغيلها في Microsoft Defender ل Endpoint وتلبي متطلبات معينة. لمعرفة المزيد، راجع [متطلبات تشغيل برنامج الحماية من الفيروسات ل Microsoft Defender في الوضع السلبي](microsoft-defender-antivirus-compatibility.md#requirements-for-microsoft-defender-antivirus-to-run-in-passive-mode).

   - **يعني وضع حظر EDR** أن برنامج الحماية من الفيروسات ل Microsoft Defender قيد التشغيل، كما يتم تمكين الكشف عن نقطة النهاية [والاستجابة لها (EDR)](edr-in-block-mode.md) في وضع الحظر، وهي إمكانية في Microsoft Defender لنقطة النهاية.

   - **يعني وضع SxS السلبي** أن برنامج الحماية من الفيروسات ل Microsoft Defender يعمل إلى جانب منتج آخر من برامج الحماية من الفيروسات/مكافحة البرامج الضارة، كما يتم استخدام الفحص الدوري  [المحدود](limited-periodic-scanning-microsoft-defender-antivirus.md).

> [!TIP]
> لمعرفة المزيد حول Get-MpComputerStatus PowerShell cmdlet، راجع المقالة المرجعية [Get-MpComputerStatus](/powershell/module/defender/get-mpcomputerstatus).

## <a name="get-your-antivirusantimalware-platform-updates"></a>الحصول على تحديثات النظام الأساسي لمكافحة الفيروسات/البرامج الضارة

من المهم الاحتفاظ ب Microsoft Defender Antivirus، أو أي حل من حلول الحماية من الفيروسات/مكافحة البرامج الضارة، مواكبا لأي تحديثات. تصدر Microsoft تحديثات منتظمة للمساعدة في التأكد من أن أجهزتك لديها أحدث التقنيات للحماية من البرامج الضارة وتقنيات الهجوم الجديدة. لمعرفة المزيد، راجع [إدارة تحديثات برنامج الحماية من الفيروسات ل Microsoft Defender وتطبيق الأساسات](manage-updates-baselines-microsoft-defender-antivirus.md).

## <a name="see-also"></a>راجع أيضًا

- [إدارة Microsoft Defender Antivirus وتكوينه](configuration-management-reference-microsoft-defender-antivirus.md)
- [تقييم الحماية من الفيروسات ل Microsoft Defender](evaluate-microsoft-defender-antivirus.md)
