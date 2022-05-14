---
title: استخدم أوامر cmdlets PowerShell لتكوين وتشغيل برنامج الحماية من الفيروسات من Microsoft Defender
description: في Windows 10 Windows 11، يمكنك استخدام أوامر Cmdlets PowerShell لتشغيل عمليات الفحص وتحديث معلومات الأمان وتغيير الإعدادات في برنامج الحماية من الفيروسات من Microsoft Defender.
keywords: المسح الضوئي، سطر الأوامر، mpcmdrun، Defender
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.date: 10/18/2020
ms.reviewer: ''
manager: dansimp
ms.technology: mde
audience: ITPro
ms.topic: how-to
ms.collection: m365-security-compliance
ms.openlocfilehash: 7afde73e1e1c1e5ff35ee906331aa2756ba55a21
ms.sourcegitcommit: ebbe8713297675db5dcb3e0d9c3ae5e746b99196
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 05/14/2022
ms.locfileid: "65419473"
---
# <a name="use-powershell-cmdlets-to-configure-and-manage-microsoft-defender-antivirus"></a>استخدم أوامر cmdlets PowerShell لتكوين وإدارة برنامج الحماية من الفيروسات من Microsoft Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**ينطبق على:**
- [Microsoft Defender لنقطة النهاية الخطة 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Defender for Endpoint الخطة 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- برنامج الحماية من الفيروسات من Microsoft Defender

**الأنظمة الأساسية**
- بالنسبة لنظام التشغيل

يمكنك استخدام PowerShell لتنفيذ وظائف مختلفة في Windows Defender. على غرار موجه الأوامر أو سطر الأوامر، فإن PowerShell عبارة عن واجهة سطر أوامر مستندة إلى المهام ولغة برمجة نصية مصممة خصيصا لإدارة النظام. يمكنك قراءة المزيد حول ذلك في [مركز PowerShell على MSDN](/previous-versions/msdn10/mt173057(v=msdn.10)).

للحصول على قائمة ب cmdlets ووظائفها والمعلمات المتوفرة، راجع موضوع [Cmdlets لبرنامج الحماية من الفيروسات Defender](/powershell/module/defender) .

PowerShell cmdlets هي الأكثر فائدة في بيئات الخادم Windows التي لا تعتمد على واجهة مستخدم رسومية (GUI) لتكوين البرامج.

> [!NOTE]
> يجب عدم استخدام أوامر cmdlets PowerShell كبديل للبنية الأساسية الكاملة لإدارة نهج الشبكة، مثل [Microsoft Endpoint Configuration Manager](/configmgr) [أو وحدة تحكم إدارة نهج المجموعة](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11)) أو [ برنامج الحماية من الفيروسات من Microsoft Defender نهج المجموعة قوالب ADMX](https://www.microsoft.com/download/101445).

ستؤثر التغييرات التي تم إجراؤها باستخدام PowerShell على الإعدادات المحلية على نقطة النهاية حيث يتم نشر التغييرات أو إجراؤها. وهذا يعني أن عمليات نشر النهج باستخدام نهج المجموعة أو Microsoft Endpoint Configuration Manager أو Microsoft Intune يمكن الكتابة فوق التغييرات التي تم إجراؤها باستخدام PowerShell.

يمكنك [تكوين الإعدادات التي يمكن تجاوزها محليا مع تجاوز النهج المحلي](configure-local-policy-overrides-microsoft-defender-antivirus.md).

يتم تثبيت PowerShell عادة ضمن المجلد `%SystemRoot%\system32\WindowsPowerShell`.

## <a name="use-microsoft-defender-antivirus-powershell-cmdlets"></a>استخدام أوامر cmdlets برنامج الحماية من الفيروسات من Microsoft Defender PowerShell

1. في شريط البحث Windows، اكتب **powershell**.
2. حدد **Windows PowerShell** من النتائج لفتح الواجهة.
3. أدخل أمر PowerShell وأي معلمات.

> [!NOTE]
> قد تحتاج إلى فتح PowerShell في وضع المسؤول. انقر بزر الماوس الأيمن فوق العنصر في قائمة البدء، وانقر فوق **"تشغيل كمسؤول**" ثم انقر فوق **"نعم**" في موجه الأذونات.

لفتح التعليمات عبر الإنترنت لأي من أوامر cmdlets، اكتب ما يلي:

```PowerShell
Get-Help <cmdlet> -Online
```

احذف المعلمة `-online` للحصول على تعليمات مخزنة مؤقتا محليا.

> [!TIP]
> إذا كنت تبحث عن معلومات متعلقة بالحماية من الفيروسات للأنظمة الأساسية الأخرى، فراجع:
> - [تعيين تفضيلات Microsoft Defender لنقطة النهاية على نظام التشغيل macOS](mac-preferences.md)
> - [Microsoft Defender for Endpoint على Mac](microsoft-defender-endpoint-mac.md)
> - [إعدادات نهج برنامج الحماية من الفيروسات في macOS لبرنامج الحماية من الفيروسات من Microsoft Defender Antivirus for Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [تعيين تفضيلات Microsoft Defender لنقطة النهاية على Linux](linux-preferences.md)
> - [مشكلات الأداء في Microsoft Defender لنقطة النهاية على Linux](microsoft-defender-endpoint-linux.md)
> - [تكوين Defender for Endpoint على ميزات Android](android-configure.md)
> - [تكوين Microsoft Defender for Endpoint على ميزات iOS](ios-configure-features.md)

## <a name="related-topics"></a>المواضيع ذات الصلة

- [مواضيع مرجعية لأدوات الإدارة والتكوين](configuration-management-reference-microsoft-defender-antivirus.md)
- [برنامج الحماية من الفيروسات من Microsoft Defender في Windows 10](microsoft-defender-antivirus-in-windows-10.md)
- [برنامج الحماية من الفيروسات من Microsoft Defender Cmdlets](/powershell/module/defender)
