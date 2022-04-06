---
title: Microsoft Defender في وضع عدم الاتصال في Windows
description: يمكنك استخدام Microsoft Defender في وضع عدم الاتصال مباشرة من برنامج الحماية من الفيروسات لـ Windows Defender التطبيق. يمكنك أيضا إدارة كيفية نشره في شبكتك.
keywords: مسح ضوئي، ومدافع، وغير متصل
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.reviewer: ''
manager: dansimp
ms.technology: mde
ms.topic: article
ms.collection: M365-security-compliance
ms.openlocfilehash: ccb65b865afdf2a0ec0210c3593daee1cb5c09b6
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/25/2022
ms.locfileid: "64476830"
---
# <a name="run-and-review-the-results-of-a-microsoft-defender-offline-scan"></a>تشغيل نتائج فحص Microsoft Defender في وضع عدم الاتصال ومراجعتها

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**ينطبق على:**
- [Microsoft Defender لنقطة النهاية 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

Microsoft Defender في وضع عدم الاتصال أداة مسح البرامج الضارة التي تتيح لك تشغيل عملية فحص وتشغيلها من بيئة موثوق بها. يتم تشغيل الفحص من خارج نواة Windows العادية بحيث يمكن أن تستهدف البرامج الضارة التي تحاول تجاوز قوقعة Windows، مثل الفيروسات ومفاتحي الجذر التي تسبب إصابة سجل التشغيل الرئيسي (MBR) أو تتخطىه.

يمكنك استخدام Microsoft Defender في وضع عدم الاتصال إذا كنت تشك في وجود إصابة بالبرامج الضارة، أو إذا كنت تريد تأكيد تنظيف كامل لنقطة النهاية بعد انتشار البرامج الضارة.

في Windows 10 Windows 11، Microsoft Defender في وضع عدم الاتصال تشغيل التطبيق بنقرة واحدة مباشرة [من أمن Windows التطبيق](microsoft-defender-security-center-antivirus.md). في الإصدارات السابقة من Windows، كان على المستخدم تثبيت Microsoft Defender في وضع عدم الاتصال إلى وسائط قابلة للتمهيد، وإعادة تشغيل نقطة النهاية، وتحميل الوسائط القابلة للتمهيد.

## <a name="prerequisites-and-requirements"></a>المتطلبات والمتطلبات

Microsoft Defender في وضع عدم الاتصال في Windows 10 Windows 11 متطلبات الأجهزة نفسها التي Windows 10.

لمزيد من المعلومات حول Windows 10 ومتطلبات Windows 11، راجع المواضيع التالية:

- [الحد الأدنى لمتطلبات الأجهزة](/windows-hardware/design/minimum/minimum-hardware-requirements-overview)

- [إرشادات مكونات الأجهزة](/windows-hardware/design/component-guidelines/components)

> [!NOTE]
> Microsoft Defender في وضع عدم الاتصال غير معتمد على الأجهزة التي ARM المعالجات أو على Windows المخزنة للخادم.

لتشغيل Microsoft Defender في وضع عدم الاتصال من نقطة النهاية، يجب تسجيل دخول المستخدم باستخدام امتيازات المسؤول.

## <a name="microsoft-defender-offline-updates"></a>Microsoft Defender في وضع عدم الاتصال التحديثات

Microsoft Defender في وضع عدم الاتصال آخر تحديثات الحماية المتوفرة على نقطة النهاية؛ يتم تحديثها كلما برنامج الحماية من الفيروسات لـ Windows Defender تحديثها.

> [!NOTE]
> قبل تشغيل الفحص دون اتصال، يجب أن تحاول تحديث حماية AV من Microsoft Defender. يمكنك فرض تحديث باستخدام نهج المجموعة أو يمكنك عادة نشر التحديثات إلى نقاط النهاية، أو يمكنك تنزيل آخر تحديثات الحماية وتثبيتها [يدويا](https://www.microsoft.com/security/portal/definitions/adl.aspx) من مركز الحماية من البرامج الضارة لـ Microsoft.

راجع [الموضوع إدارة برنامج الحماية من الفيروسات من Microsoft Defender معلومات](manage-protection-updates-microsoft-defender-antivirus.md) الأمان للحصول على مزيد من المعلومات.

## <a name="usage-scenarios"></a>سيناريوهات الاستخدام

في Windows 10، الإصدار 1607، يمكنك فرض الفحص دون اتصال يدويا. بدلا من ذلك، إذا Windows Defender Microsoft Defender في وضع عدم الاتصال يجب تشغيله، سيطالب المستخدم في نقطة النهاية.

سيتم أيضا الكشف عن الحاجة إلى إجراء فحص دون اتصال إدارة نقاط النهاية من Microsoft إذا كنت تستخدمه لإدارة نقاط النهاية.

يمكن أن تحدث المطالبة عبر إعلام، على غرار ما يلي:

:::image type="content" source="../../media/notification.png" alt-text="إعلام لتشغيل Microsoft Defender في وضع عدم الاتصال" lightbox="../../media/notification.png":::

سيتم أيضا إعلام المستخدم داخل Windows Defender.

في Configuration Manager، يمكنك تحديد حالة نقاط النهاية من خلال الانتقال إلى > نظرة عامة > حالة > Endpoint Protection حالة > System Center Endpoint Protection **.**

Microsoft Defender في وضع عدم الاتصال المسح الضوئي **ضمن حالة إصلاح** البرامج الضارة كما هو مطلوب الفحص **دون اتصال**.

:::image type="content" source="../../media/sccm-wdo.png" alt-text="مؤشر فحص Microsoft Defender في وضع عدم الاتصال" lightbox="../../media/sccm-wdo.png":::

## <a name="configure-notifications"></a>تكوين الإعلامات

Microsoft Defender في وضع عدم الاتصال تكوين الإعلامات في إعداد النهج نفسه الذي يتم تكوينه في إعلامات Microsoft Defender AV الأخرى.

لمزيد من المعلومات حول الإعلامات في Windows Defender، راجع الموضوع تكوين الإعلامات التي [تظهر على نقاط](configure-notifications-microsoft-defender-antivirus.md) النهاية.

## <a name="run-a-scan"></a>تشغيل فحص

> [!IMPORTANT]
> قبل استخدام Microsoft Defender في وضع عدم الاتصال، تأكد من حفظ أي ملفات ثم إيقاف تشغيل البرامج. يستغرق تشغيل Microsoft Defender في وضع عدم الاتصال المسح الضوئي حوالي 15 دقيقة. سيعاد تشغيل نقطة النهاية عند اكتمال الفحص. يتم إجراء الفحص خارج بيئة Windows التشغيل العادية. ستبدو واجهة المستخدم مختلفة عن عملية المسح الضوئي العادية التي ينفذها Windows Defender. بعد اكتمال الفحص، سيتم إعادة تشغيل نقطة النهاية Windows بشكل طبيعي.

يمكنك تشغيل عملية فحص Microsoft Defender في وضع عدم الاتصال باستخدام ما يلي:

- PowerShell
- Windows إدارة الأجهزة (WMI)
- تطبيق أمن Windows



### <a name="use-powershell-cmdlets-to-run-an-offline-scan"></a>استخدام PowerShell cmdlets لتشغيل فحص غير متصل

استخدم cmdlets التالية:

```PowerShell
Start-MpWDOScan
```

راجع [استخدام Cmdlets في PowerShell](use-powershell-cmdlets-microsoft-defender-antivirus.md) لتكوين الأمرين [cmdlets](/powershell/module/defender/) برنامج الحماية من الفيروسات من Microsoft Defender و Defender Antivirus وتشغيلها للحصول على مزيد من المعلومات حول كيفية استخدام PowerShell مع برنامج الحماية من الفيروسات من Microsoft Defender.

### <a name="use-windows-management-instruction-wmi-to-run-an-offline-scan"></a>استخدام Windows إدارة الملفات (WMI) لتشغيل فحص غير متصل

استخدم [**الفئة MSFT_MpWDOScan**](/previous-versions/windows/desktop/legacy/dn455323(v=vs.85)) لتشغيل فحص غير متصل.

سيتم تشغيل قصاصة البرامج النصية التالية في WMI على الفور Microsoft Defender في وضع عدم الاتصال، مما يؤدي إلى إعادة تشغيل نقطة النهاية وتشغيل الفحص دون اتصال، ثم إعادة التشغيل Windows.

```console
wmic /namespace:\\root\Microsoft\Windows\Defender path MSFT_MpWDOScan call Start
```

لمزيد من المعلومات، راجع ما يلي:

- [Windows واجهات برمجة التطبيقات ل Defender WMIv2](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal)

### <a name="use-the-windows-defender-security-app-to-run-an-offline-scan"></a>استخدام تطبيق Windows Defender Security لتشغيل فحص غير متصل

1. افتح أمن Windows عن طريق النقر فوق أيقونة الدرع في شريط المهام أو البحث في قائمة البدء ل **Defender for Cloud**.

2. انقر فوق **لوحة الحماية &** الفيروسات (أو أيقونة الدرع على شريط القوائم الأيسر) ثم فوق **تسمية الفحص** المتقدم:

3. حدد **Microsoft Defender في وضع عدم الاتصال المسح الضوئي ثم** انقر فوق **مسح ضوئي الآن**.

    > [!NOTE]
    > في Windows 10، الإصدار 1607، يمكن تشغيل الفحص دون اتصال من **ضمن Windows الإعدادات** \> تحديث **&** \> **أمان Windows Defender** أو من عميل Windows Defender.

## <a name="review-scan-results"></a>مراجعة نتائج الفحص

Microsoft Defender في وضع عدم الاتصال يتم إدراج نتائج الفحص في قسم [محفوظات الفحص أمن Windows التطبيق](microsoft-defender-security-center-antivirus.md).

## <a name="related-articles"></a>المقالات ذات الصلة

- [تخصيص نتائج الفحص والمراجعة وبدءها ومراجعتها](customize-run-review-remediate-scans-microsoft-defender-antivirus.md)
- [برنامج الحماية من الفيروسات من Microsoft Defender في Windows 10](microsoft-defender-antivirus-in-windows-10.md)
