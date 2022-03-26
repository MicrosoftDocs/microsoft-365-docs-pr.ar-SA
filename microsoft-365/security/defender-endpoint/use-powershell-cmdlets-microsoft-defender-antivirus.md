---
title: استخدم PowerShell cmdlets لتكوين برنامج الحماية من الفيروسات من Microsoft Defender
description: في Windows 10 Windows 11، يمكنك استخدام PowerShell cmdlets لتشغيل عمليات الفحص وتحديث معلومات الأمان وتغيير الإعدادات في برنامج الحماية من الفيروسات من Microsoft Defender.
keywords: المسح الضوئي، سطر الأوامر، mpcmdrun، defender
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
ms.openlocfilehash: 075a475ef3135769e90362f441077b1638192e99
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 11/24/2021
ms.locfileid: "63571623"
---
# <a name="use-powershell-cmdlets-to-configure-and-manage-microsoft-defender-antivirus"></a>استخدم PowerShell cmdlets لتكوين وإدارة برنامج الحماية من الفيروسات من Microsoft Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**ينطبق على:**
- [خطة Microsoft Defender لنقطة النهاية 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/?linkid=2154037)

يمكنك استخدام PowerShell لتنفيذ دالات متنوعة في Windows Defender. يشبه PowerShell موجه الأوامر أو سطر الأوامر، وهو لغة النصية ومستندة إلى سطر الأوامر والمستندة إلى المهام، وقد تم تصميمها خصيصا لإدارة النظام. يمكنك قراءة المزيد حول ذلك في [مركز PowerShell على MSDN](/previous-versions/msdn10/mt173057(v=msdn.10)).

للحصول على قائمة ب cmdlets ووظائفها والمعلمات المتوفرة، راجع الموضوع [Cmdlets Defender Antivirus](/powershell/module/defender) .

إن PowerShell cmdlets مفيدة جدا في بيئات Windows Server التي لا تعتمد على واجهة مستخدم رسومية (GUI) لتكوين البرنامج.

> [!NOTE]
> يجب عدم استخدام PowerShell cmdlets كبديل للبنية الأساسية الكاملة لإدارة نهج الشبكة، مثل [Microsoft Endpoint Configuration Manager](/configmgr) أو وحدة تحكم إدارة نهج المجموعة أو [](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11))[برنامج الحماية من الفيروسات من Microsoft Defender ADMX القوالب](https://www.microsoft.com/download/101445).

ستؤثر التغييرات التي يتم إدخالها على PowerShell على الإعدادات المحلية في نقطة النهاية حيث يتم نشر التغييرات أو إجراءها. وهذا يعني أن عمليات نشر النهج باستخدام نهج المجموعة Microsoft Endpoint Configuration Manager أو Microsoft Intune الكتابة فوق التغييرات التي تم إدخالها باستخدام PowerShell.

يمكنك [تكوين الإعدادات التي يمكن تجاوزها محليا باستخدام تجاوز النهج المحلي](configure-local-policy-overrides-microsoft-defender-antivirus.md).

يتم عادة تثبيت PowerShell أسفل المجلد `%SystemRoot%\system32\WindowsPowerShell`.

## <a name="use-microsoft-defender-antivirus-powershell-cmdlets"></a>استخدام برنامج الحماية من الفيروسات من Microsoft Defender Cmdlets في PowerShell

1. في شريط Windows، اكتب **powershell**.
2. حدد **Windows PowerShell** من النتائج لفتح الواجهة.
3. أدخل الأمر PowerShell وأي معلمات.

> [!NOTE]
> قد تحتاج إلى فتح PowerShell في وضع المسؤول. انقر بضغطة زر الماوس الأيمن فوق العنصر في قائمة البدء، **وانقر فوق تشغيل** كمسؤول، ثم انقر فوق **نعم** في مطالبة الأذونات.

لفتح التعليمات عبر الإنترنت لأي من cmdlets، اكتب ما يلي:

```PowerShell
Get-Help <cmdlet> -Online
```

تجاهل المعلمة `-online` للحصول على تعليمات المخزنة مؤقتا محليا.

## <a name="related-topics"></a>المواضيع ذات الصلة

- [مواضيع مرجعية لأدوات الإدارة والتكوين](configuration-management-reference-microsoft-defender-antivirus.md)
- [برنامج الحماية من الفيروسات من Microsoft Defender في Windows 10](microsoft-defender-antivirus-in-windows-10.md)
- [برنامج الحماية من الفيروسات من Microsoft Defender Cmdlets](/powershell/module/defender)
