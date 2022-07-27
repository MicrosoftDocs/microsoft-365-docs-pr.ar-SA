---
title: Microsoft Defender دون اتصال في Windows
description: يمكنك استخدام Microsoft Defender دون اتصال مباشرة من تطبيق برنامج الحماية من الفيروسات لـ Windows Defender. يمكنك أيضا إدارة كيفية توزيعه في شبكتك.
keywords: المسح الضوئي، والمدافع، دون اتصال
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
ms.date: 07/28/2022
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.reviewer: ''
manager: dansimp
ms.technology: mde
ms.topic: article
ms.collection: M365-security-compliance
ms.openlocfilehash: cc01b6d81d272bfd0ee808131804cf59d4502350
ms.sourcegitcommit: e8dd5cd434d17af7096d28d467a2b3b021cbb233
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/27/2022
ms.locfileid: "67051833"
---
# <a name="run-and-review-the-results-of-a-microsoft-defender-offline-scan"></a>تشغيل نتائج فحص Microsoft Defender في وضع عدم الاتصال ومراجعتها

**ينطبق على:**
- [الخطة 1 من Microsoft Defender لنقطة النهاية](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Defender for Endpoint الخطة 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- برنامج الحماية من الفيروسات من Microsoft Defender

**الأنظمة الأساسية**
- بالنسبة لنظام التشغيل

Microsoft Defender دون اتصال هو أداة فحص مكافحة البرامج الضارة التي تتيح لك تشغيل وتشغيل فحص من بيئة موثوق بها. يتم تشغيل الفحص من خارج نواة Windows العادية حتى تتمكن من استهداف البرامج الضارة التي تحاول تجاوز Windows shell، مثل الفيروسات والجذرات التي تؤدي إلى إصابة سجل التمهيد الرئيسي (MBR) أو الكتابة فوقه.

يمكنك استخدام Microsoft Defender دون اتصال إذا كنت تشك في وجود إصابة بالبرامج الضارة، أو إذا كنت تريد تأكيد تنظيف شامل لنقطة النهاية بعد انتشار البرامج الضارة.

في Windows 10 Windows 11، يمكن تشغيل Microsoft Defender دون اتصال بنقرة واحدة مباشرة من [تطبيق أمن Windows](microsoft-defender-security-center-antivirus.md). في الإصدارات السابقة من Windows، كان على المستخدم تثبيت Microsoft Defender دون اتصال بوسائط قابلة للتمهيد، وإعادة تشغيل نقطة النهاية، وتحميل الوسائط القابلة للتمهيد.

## <a name="prerequisites-and-requirements"></a>المتطلبات الأساسية والمتطلبات

Microsoft Defender دون اتصال في Windows 10 Windows 11 له نفس متطلبات الأجهزة مثل Windows 10.

لمزيد من المعلومات حول متطلبات Windows 10 Windows 11، راجع المواضيع التالية:

- [الحد الأدنى لمتطلبات الأجهزة](/windows-hardware/design/minimum/minimum-hardware-requirements-overview)
- [إرشادات مكونات الأجهزة](/windows-hardware/design/component-guidelines/components)

> [!NOTE]
> Microsoft Defender دون اتصال غير معتمد على الأجهزة التي تحتوي على معالجات ARM أو على وحدات حفظ المخزون في Windows Server.

لتشغيل Microsoft Defender دون اتصال من نقطة النهاية، يجب تسجيل دخول المستخدم باستخدام امتيازات المسؤول.

## <a name="microsoft-defender-offline-updates"></a>تحديثات Microsoft Defender دون اتصال

يستخدم Microsoft Defender دون اتصال آخر تحديثات الحماية المتوفرة على نقطة النهاية؛ يتم تحديثه كلما تم تحديث برنامج الحماية من الفيروسات لـ Windows Defender.

> [!NOTE]
> قبل تشغيل الفحص دون اتصال، يجب محاولة تحديث حماية Microsoft Defender AV. يمكنك إما فرض تحديث باستخدام نهج المجموعة أو مع ذلك تقوم عادة بنشر التحديثات إلى نقاط النهاية، أو يمكنك تنزيل أحدث تحديثات الحماية وتثبيتها يدويا من [مركز الحماية من البرامج الضارة لـ Microsoft](https://www.microsoft.com/security/portal/definitions/adl.aspx).

راجع الموضوع ["إدارة تحديثات معلومات أمان الحماية من الفيروسات من Microsoft Defender](manage-protection-updates-microsoft-defender-antivirus.md) " للحصول على مزيد من المعلومات.

## <a name="usage-scenarios"></a>سيناريوهات الاستخدام

في Windows 10، الإصدار 1607، يمكنك فرض فحص دون اتصال يدويا. بدلا من ذلك، إذا حدد Windows Defender أن Microsoft Defender دون اتصال يحتاج إلى التشغيل، فسيطالب المستخدم بنقطة النهاية.

سيتم أيضا الكشف عن الحاجة إلى إجراء فحص دون اتصال في Microsoft إدارة نقاط النهاية إذا كنت تستخدمه لإدارة نقاط النهاية الخاصة بك.

يمكن أن تحدث المطالبة عبر إعلام، على غرار ما يلي:

:::image type="content" source="../../media/notification.png" alt-text="إعلام لتشغيل Microsoft Defender دون اتصال" lightbox="../../media/notification.png":::

سيتم إعلام المستخدم أيضا داخل عميل Windows Defender.

في Configuration Manager، يمكنك تحديد حالة نقاط النهاية من خلال الانتقال إلى حالة > System Center Endpoint Protection حالة حماية نقطة **النهاية > المراقبة > > حالة حماية نقطة النهاية**.

تتم الإشارة إلى عمليات المسح الضوئي ل Microsoft Defender دون اتصال ضمن **حالة معالجة البرامج الضارة** حيث **يتطلب الفحص دون اتصال**.

:::image type="content" source="../../media/sccm-wdo.png" alt-text="مؤشر الفحص ل Microsoft Defender دون اتصال" lightbox="../../media/sccm-wdo.png":::

## <a name="configure-notifications"></a>تكوين الإعلامات

يتم تكوين إعلامات Microsoft Defender دون اتصال في نفس إعداد النهج مثل إعلامات Microsoft Defender AV الأخرى.

لمزيد من المعلومات حول الإعلامات في Windows Defender، راجع [تكوين الإعلامات التي تظهر في موضوع نقاط النهاية](configure-notifications-microsoft-defender-antivirus.md) .

## <a name="run-a-scan"></a>تشغيل فحص

> [!IMPORTANT]
> قبل استخدام Microsoft Defender دون اتصال، تأكد من حفظ أي ملفات وإيقاف تشغيل البرامج. يستغرق تشغيل الفحص في Microsoft Defender دون اتصال حوالي 15 دقيقة. سيعيد تشغيل نقطة النهاية عند اكتمال الفحص. يتم إجراء الفحص خارج بيئة تشغيل Windows المعتادة. ستظهر واجهة المستخدم مختلفة عن الفحص العادي الذي يقوم به Windows Defender. بعد اكتمال الفحص، ستتم إعادة تشغيل نقطة النهاية وسيتم تحميل Windows بشكل طبيعي.

يمكنك تشغيل فحص Microsoft Defender دون اتصال مع ما يلي:

- PowerShell
- Windows Management Instrumentation (WMI)
- تطبيق أمن Windows

### <a name="use-powershell-cmdlets-to-run-an-offline-scan"></a>استخدام PowerShell cmdlets لتشغيل فحص دون اتصال

استخدم أوامر cmdlet التالية:

```PowerShell
Start-MpWDOScan
```

راجع [استخدام أوامر Cmdlets PowerShell لتكوين أوامر cmdlets لبرنامج الحماية من الفيروسات من Microsoft Defender](use-powershell-cmdlets-microsoft-defender-antivirus.md) و [Defender Antivirus وتشغيلها](/powershell/module/defender/) للحصول على مزيد من المعلومات حول كيفية استخدام PowerShell مع برنامج الحماية من الفيروسات من Microsoft Defender.

### <a name="use-windows-management-instruction-wmi-to-run-an-offline-scan"></a>استخدام تعليمات إدارة Windows (WMI) لتشغيل فحص دون اتصال

استخدم فئة [**MSFT_MpWDOScan**](/previous-versions/windows/desktop/legacy/dn455323(v=vs.85)) لتشغيل فحص دون اتصال.

ستقوم القصاصة البرمجية التالية لبرنامج WMI النصي بتشغيل فحص Microsoft Defender دون اتصال على الفور، مما سيؤدي إلى إعادة تشغيل نقطة النهاية وتشغيل الفحص دون اتصال، ثم إعادة التشغيل والتمهيد في Windows.

```console
wmic /namespace:\\root\Microsoft\Windows\Defender path MSFT_MpWDOScan call Start
```

راجع ما يلي للحصول على مزيد من المعلومات:

- [واجهات برمجة تطبيقات Windows Defender WMIv2](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal)

### <a name="use-the-windows-defender-security-app-to-run-an-offline-scan"></a>استخدام تطبيق Windows Defender Security لتشغيل فحص دون اتصال

1. افتح تطبيق أمن Windows بالنقر فوق أيقونة الدرع في شريط المهام أو البحث في قائمة البدء **ل Defender for Cloud**.

2. انقر فوق التجانب **"فيروس & الحماية من التهديدات** " (أو أيقونة الدرع على شريط القوائم الأيسر) ثم تسمية **المسح المتقدم** :

3. حدد **فحص Microsoft Defender دون اتصال** وانقر فوق **المسح الضوئي الآن**.

    > [!NOTE]
    > في Windows 10، الإصدار 1607، يمكن تشغيل الفحص دون اتصال من ضمن **Windows Settings** \> **Update & أمان** \> **Windows Defender** أو من عميل Windows Defender.

> [!TIP]
> إذا كنت تبحث عن معلومات متعلقة ببرنامج الحماية من الفيروسات للأنظمة الأساسية الأخرى، فاطلع على:
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
