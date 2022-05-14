---
title: Microsoft Defender في وضع عدم الاتصال في Windows
description: يمكنك استخدام Microsoft Defender في وضع عدم الاتصال مباشرة من تطبيق برنامج الحماية من الفيروسات لـ Windows Defender. يمكنك أيضا إدارة كيفية توزيعه في شبكتك.
keywords: المسح الضوئي، والمدافع، دون اتصال
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
ms.openlocfilehash: 690437de177ce1f6c466166970a8b7143d230916
ms.sourcegitcommit: ebbe8713297675db5dcb3e0d9c3ae5e746b99196
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 05/14/2022
ms.locfileid: "65415629"
---
# <a name="run-and-review-the-results-of-a-microsoft-defender-offline-scan"></a>تشغيل نتائج فحص Microsoft Defender في وضع عدم الاتصال ومراجعتها

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**ينطبق على:**
- [Microsoft Defender لنقطة النهاية الخطة 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Defender for Endpoint الخطة 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- برنامج الحماية من الفيروسات من Microsoft Defender

**الأنظمة الأساسية**
- بالنسبة لنظام التشغيل

Microsoft Defender في وضع عدم الاتصال هي أداة فحص مكافحة البرامج الضارة التي تتيح لك تشغيل وتشغيل فحص من بيئة موثوق بها. يتم تشغيل الفحص من خارج نواة Windows العادية حتى تتمكن من استهداف البرامج الضارة التي تحاول تجاوز Windows shell، مثل الفيروسات و rootkits التي تسبب الفيروسات أو الكتابة فوق سجل التمهيد الرئيسي (MBR).

يمكنك استخدام Microsoft Defender في وضع عدم الاتصال إذا كنت تشك في وجود إصابة بالبرامج الضارة، أو إذا كنت تريد تأكيد تنظيف شامل لنقطة النهاية بعد انتشار البرامج الضارة.

في Windows 10 Windows 11، يمكن تشغيل Microsoft Defender في وضع عدم الاتصال بنقرة واحدة مباشرة من [تطبيق أمن Windows](microsoft-defender-security-center-antivirus.md). في الإصدارات السابقة من Windows، كان على المستخدم تثبيت Microsoft Defender في وضع عدم الاتصال إلى وسائط قابلة للتمهيد، وإعادة تشغيل نقطة النهاية، وتحميل الوسائط القابلة للتمهيد.

## <a name="prerequisites-and-requirements"></a>المتطلبات الأساسية والمتطلبات

Microsoft Defender في وضع عدم الاتصال في Windows 10 Windows 11 لها نفس متطلبات الأجهزة مثل Windows 10.

لمزيد من المعلومات حول متطلبات Windows 10 Windows 11، راجع المواضيع التالية:

- [الحد الأدنى لمتطلبات الأجهزة](/windows-hardware/design/minimum/minimum-hardware-requirements-overview)

- [إرشادات مكونات الأجهزة](/windows-hardware/design/component-guidelines/components)

> [!NOTE]
> Microsoft Defender في وضع عدم الاتصال غير معتمد على الأجهزة التي تحتوي على معالجات ARM، أو على Windows Server Stock Keeping Units.

لتشغيل Microsoft Defender في وضع عدم الاتصال من نقطة النهاية، يجب تسجيل دخول المستخدم بامتيازات المسؤول.

## <a name="microsoft-defender-offline-updates"></a>تحديثات Microsoft Defender في وضع عدم الاتصال

تستخدم Microsoft Defender في وضع عدم الاتصال أحدث تحديثات الحماية المتوفرة على نقطة النهاية؛ ويتم تحديثها كلما تم تحديث برنامج الحماية من الفيروسات لـ Windows Defender.

> [!NOTE]
> قبل تشغيل الفحص دون اتصال، يجب محاولة تحديث حماية Microsoft Defender AV. يمكنك إما فرض تحديث باستخدام نهج المجموعة أو مع ذلك تقوم عادة بنشر التحديثات إلى نقاط النهاية، أو يمكنك تنزيل أحدث تحديثات الحماية وتثبيتها يدويا من [مركز الحماية من البرامج الضارة لـ Microsoft](https://www.microsoft.com/security/portal/definitions/adl.aspx).

راجع موضوع ["إدارة تحديثات معلومات الأمان برنامج الحماية من الفيروسات من Microsoft Defender](manage-protection-updates-microsoft-defender-antivirus.md)" للحصول على مزيد من المعلومات.

## <a name="usage-scenarios"></a>سيناريوهات الاستخدام

في Windows 10، الإصدار 1607، يمكنك فرض فحص دون اتصال يدويا. بدلا من ذلك، إذا حدد Windows Defender أن Microsoft Defender في وضع عدم الاتصال يحتاج إلى التشغيل، فسيطالب المستخدم بنقطة النهاية.

سيتم أيضا الكشف عن الحاجة إلى إجراء فحص دون اتصال في إدارة نقاط النهاية من Microsoft إذا كنت تستخدمه لإدارة نقاط النهاية الخاصة بك.

يمكن أن تحدث المطالبة عبر إعلام، على غرار ما يلي:

:::image type="content" source="../../media/notification.png" alt-text="إعلام لتشغيل Microsoft Defender في وضع عدم الاتصال" lightbox="../../media/notification.png":::

سيتم إعلام المستخدم أيضا داخل عميل Windows Defender.

في Configuration Manager، يمكنك تحديد حالة نقاط النهاية من خلال الانتقال إلى حالة **> System Center Endpoint Protection > المراقبة > حالة > Endpoint Protection الأمان**.

تتم الإشارة إلى عمليات المسح الضوئي Microsoft Defender في وضع عدم الاتصال ضمن **حالة معالجة البرامج الضارة** كما **يتطلب الفحص دون اتصال**.

:::image type="content" source="../../media/sccm-wdo.png" alt-text="مؤشر الفحص بحثا عن Microsoft Defender في وضع عدم الاتصال" lightbox="../../media/sccm-wdo.png":::

## <a name="configure-notifications"></a>تكوين الإعلامات

يتم تكوين إعلامات Microsoft Defender في وضع عدم الاتصال في نفس إعداد النهج مثل إعلامات Microsoft Defender AV الأخرى.

لمزيد من المعلومات حول الإعلامات في Windows Defender، راجع [تكوين الإعلامات التي تظهر في موضوع نقاط النهاية](configure-notifications-microsoft-defender-antivirus.md).

## <a name="run-a-scan"></a>تشغيل فحص

> [!IMPORTANT]
> قبل استخدام Microsoft Defender في وضع عدم الاتصال، تأكد من حفظ أي ملفات وإيقاف تشغيل البرامج. يستغرق فحص Microsoft Defender في وضع عدم الاتصال حوالي 15 دقيقة للتشغيل. سيعيد تشغيل نقطة النهاية عند اكتمال الفحص. يتم إجراء الفحص خارج بيئة التشغيل Windows المعتادة. ستظهر واجهة المستخدم مختلفة عن الفحص العادي الذي يتم إجراؤه بواسطة Windows Defender. بعد اكتمال الفحص، ستتم إعادة تشغيل نقطة النهاية وسيتم تحميل Windows بشكل طبيعي.

يمكنك تشغيل فحص Microsoft Defender في وضع عدم الاتصال مع ما يلي:

- PowerShell
- Windows Management Instrumentation (WMI)
- تطبيق أمن Windows



### <a name="use-powershell-cmdlets-to-run-an-offline-scan"></a>استخدام PowerShell cmdlets لتشغيل فحص دون اتصال

استخدم أوامر cmdlet التالية:

```PowerShell
Start-MpWDOScan
```

راجع [استخدام أوامر Cmdlets PowerShell لتكوين وتشغيل أوامر](use-powershell-cmdlets-microsoft-defender-antivirus.md) [cmdlets لبرنامج الحماية من الفيروسات](/powershell/module/defender/) برنامج الحماية من الفيروسات من Microsoft Defender و Defender لمزيد من المعلومات حول كيفية استخدام PowerShell مع برنامج الحماية من الفيروسات من Microsoft Defender.

### <a name="use-windows-management-instruction-wmi-to-run-an-offline-scan"></a>استخدام Windows Management Instruction (WMI) لتشغيل فحص دون اتصال

استخدم فئة [**MSFT_MpWDOScan**](/previous-versions/windows/desktop/legacy/dn455323(v=vs.85)) لتشغيل فحص دون اتصال.

ستقوم القصاصة البرمجية التالية لبرنامج WMI النصي بتشغيل فحص Microsoft Defender في وضع عدم الاتصال على الفور، مما سيؤدي إلى إعادة تشغيل نقطة النهاية وتشغيل الفحص دون اتصال، ثم إعادة التشغيل والتمهيد إلى Windows.

```console
wmic /namespace:\\root\Microsoft\Windows\Defender path MSFT_MpWDOScan call Start
```

راجع ما يلي للحصول على مزيد من المعلومات:

- [واجهات برمجة تطبيقات Windows Defender WMIv2](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal)

### <a name="use-the-windows-defender-security-app-to-run-an-offline-scan"></a>استخدام تطبيق Windows Defender Security لتشغيل فحص دون اتصال

1. افتح تطبيق أمن Windows بالنقر فوق أيقونة الدرع في شريط المهام أو البحث في قائمة البدء **ل Defender for Cloud**.

2. انقر فوق التجانب **"فيروس & الحماية من التهديدات** " (أو أيقونة الدرع على شريط القوائم الأيسر) ثم تسمية **المسح المتقدم** :

3. حدد **Microsoft Defender في وضع عدم الاتصال الفحص** وانقر فوق **المسح الضوئي الآن**.

    > [!NOTE]
    > في Windows 10، الإصدار 1607، يمكن تشغيل الفحص دون اتصال من ضمن **Windows الإعدادات** \> **تحديث & Windows Defender** \> أو من عميل Windows Defender.

## <a name="review-scan-results"></a>مراجعة نتائج الفحص

Microsoft Defender في وضع عدم الاتصال سيتم سرد نتائج الفحص في [قسم محفوظات الفحص لتطبيق أمن Windows](microsoft-defender-security-center-antivirus.md).

> [!TIP]
> إذا كنت تبحث عن معلومات متعلقة بالحماية من الفيروسات للأنظمة الأساسية الأخرى، فراجع:
> - [تعيين تفضيلات Microsoft Defender لنقطة النهاية على نظام التشغيل macOS](mac-preferences.md)
> - [Microsoft Defender for Endpoint على Mac](microsoft-defender-endpoint-mac.md)
> - [إعدادات نهج برنامج الحماية من الفيروسات في macOS لبرنامج الحماية من الفيروسات من Microsoft Defender Antivirus for Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [تعيين تفضيلات Microsoft Defender لنقطة النهاية على Linux](linux-preferences.md)
> - [مشكلات الأداء في Microsoft Defender لنقطة النهاية على Linux](microsoft-defender-endpoint-linux.md)
> - [تكوين Defender for Endpoint على ميزات Android](android-configure.md)
> - [تكوين Microsoft Defender for Endpoint على ميزات iOS](ios-configure-features.md)

## <a name="related-articles"></a>المقالات ذات الصلة

- [تخصيص نتائج عمليات الفحص والمعالجة وبدءها ومراجعتها](customize-run-review-remediate-scans-microsoft-defender-antivirus.md)
- [برنامج الحماية من الفيروسات من Microsoft Defender في Windows 10](microsoft-defender-antivirus-in-windows-10.md)
