---
title: تجميع البيانات من أجل استكشاف الأخطاء وإصلاحها على Windows
description: تعرف على كيفية استخدام محلل العميل لتجميع البيانات لسيناريوهات استكشاف الأخطاء وإصلاحها المعقدة
keywords: analzyer، تجميع البيانات، استكشاف الأخطاء وإصلاحها mdeclientanalyzer، استكشاف الأخطاء وإصلاحها المتقدم
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: m365-security-compliance
ms.topic: conceptual
ms.technology: m365d
ms.openlocfilehash: 513432dfb24af89451c4d8290ce5fde0951819b9
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/08/2022
ms.locfileid: "63575047"
---
# <a name="data-collection-for-advanced-troubleshooting-on-windows"></a>تجميع البيانات من أجل استكشاف الأخطاء وإصلاحها على Windows

**ينطبق على:**
- [خطة Microsoft Defender لنقطة النهاية 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

عند التعاون في العمل مع محترفي دعم Microsoft، قد يطلب منك استخدام محلل العملاء لتجميع البيانات من أجل استكشاف الأخطاء وإصلاحها للسيناريوهات الأكثر تعقيدا. يدعم البرنامج النصي للمحلل معلمات أخرى لهذا الغرض ويمكنه تجميع مجموعة سجلات معينة استنادا إلى الأعراض التي تم ملاحظتها التي يجب التحقق منها.

تشغيل '**MDEClientAnalyzer.cmd /?**' لرؤية قائمة المعلمات المتوفرة ووصفها:

![صورة معلمات محلل العميل في سطر الأوامر.](images/d89a1c04cf8441e4df72005879871bd0.png)

> [!NOTE]
> عند استخدام أي معلمة متقدمة من معلمات استكشاف الأخطاء وإصلاحها، يستدعي المحلل أيضاMpCmdRun.exeلتجميع [ ](/microsoft-365/security/defender-endpoint/command-line-arguments-microsoft-defender-antivirus) سجلات الدعم برنامج الحماية من الفيروسات من Microsoft Defender ذات الصلة.

**-h** - [Windows مسجل](/windows-hardware/test/wpt/wpr-command-line-options) الأداء لتجميع تتبع أداء عام مطول بالإضافة إلى مجموعة السجلات القياسية.

**-l** - المكالمات في شاشة Windows [Performance Monitor](/windows-server/remote/remote-desktop-services/rds-rdsh-performance-counters) لجمع تتبع perfmon خفيف. قد يكون هذا مفيدا عند تشخيص مشاكل انخفاض الأداء البطيئة التي تحدث مع مرور الوقت ولكن من الصعب إعادة إنتاجها عند الطلب.

**-c** - إجراء مكالمات إلى [جهاز عرض العملية](/sysinternals/downloads/procmon) من أجل المراقبة المتقدمة لنظام الملفات في الوقت الحقيقي، والسجل، ونشاط العملية/مؤشر الترابط. يكون هذا الأمر مفيدا بشكل خاص عند استكشاف الأخطاء وإصلاحها لسيناريوهات توافق التطبيقات المختلفة.

**-i** - إجراء مكالمات إلىnetsh.exeمضمن [ لبدء تتبع](/windows/win32/winsock/netsh-exe) جدار الحماية للشبكة والنوافذ يكون مفيدا عند استكشاف المشاكل المختلفة المرتبطة بالشبكة وإصلاحها.

**-b** - تماما مثل '-c' ولكن سيتم بدء تتبع مراقبة العملية أثناء التشغيل التالي وسيتوقف فقط عند استخدام -b مرة أخرى.

**-أ** - يستدعي Windows [تسجيل](/windows-hardware/test/wpt/wpr-command-line-options) الأداء لتجميع تتبع أداء مطول خاص بتحليل مشاكل CPU العالية المرتبطة بعملية مكافحة الفيروسات (MsMpEng.exe).

**-v** - يستخدم وسيطة [ سطرMpCmdRun.exe الحماية](/windows/security/threat-protection/microsoft-defender-antivirus/command-line-arguments-microsoft-defender-antivirus) من الفيروسات مع معظم الأعلام ذات التتبع المطول.

**-t** - يبدأ التتبع المطول لجميع المكونات من جانب العميل ذات الصلة ب DLP نقطة النهاية. هذا مفيد للسيناريوهات التي لا تحدث فيها إجراءات [DLP](/microsoft-365/compliance/endpoint-dlp-learn-about#endpoint-activities-you-can-monitor-and-take-action-on) كما هو متوقع للملفات.

**س** - مكالمات إلى DLPDiagnose.ps1 نصي من دليل "أدوات" المحلل الذي يتحقق من صحة التكوين الأساسي والمتطلبات الأساسية ل DLP لنقطة النهاية.

**-d** - تجمع تفريغ ذاكرة من msSenses.exe (عملية الاستشعار على Windows Server 2016 أو نظام التشغيل الأقدم) والعمليات ذات الصلة.

- \* يمكن استخدام هذه العلامة بالتزامن مع الأعلام المذكورة أعلاه.
- \*\* إن التقاط تفريغ ذاكرة للعمليات المحمية بواسطة [PPL](/windows-hardware/drivers/install/early-launch-antimalware) مثل MsSense.exe أو MsMpEng.exe غير معتمد من قبل المحلل في الوقت نفسه.

**-z** - تكوين مفاتيح التسجيل على الجهاز لتحضيرها للحصول على مجموعة تفريغ ذاكرة الجهاز بالكامل عبر [CrashOnCtrlScroll](/windows-hardware/drivers/debugger/forcing-a-system-crash-from-the-keyboard). قد يكون هذا مفيدا لتحليل مشاكل تجميد الكمبيوتر.

\* اضغط باستمرار على المفتاح CTRL في أقرب اليمين، ثم اضغط على المفتاح SCROLL LOCK مرتين.

**-k** - يستخدم [أداة NotMyFault](/sysinternals/downloads/notmyfault) لجبر النظام على تعطله وإنشاء تفريغ ذاكرة جهاز. قد يكون هذا مفيدا لتحليل مشاكل استقرار نظام التشغيل المختلفة.

يمكن بدء المحلل وكل أعلام السيناريوهات أعلاه عن بعد عن طريق تشغيل 'RemoteMDEClientAnalyzer.cmd'، الذي يتم تجميعه أيضا في مجموعة أدوات المحلل:

![صورة خط الأوامر مع معلومات المحلل.](images/57cab9d82d08f672a92bf9e748ac9572.png)

> [!NOTE]
>
> - عند استخدام RemoteMDEClientAnalyzer.cmd يستدعي إلى psexec لتنزيل الأداة من مشاركة الملف التي تم تكوينها ثم تشغيلها محليا عبر PsExec.exe.
    يستخدم البرنامج النصي CMD العلامة '-r' لتحديد أنه قيد التشغيل عن بعد ضمن سياق النظام، وبالتالي لن يتم تقديم أي مطالبة للمستخدم.
> - يمكن استخدام العلامة نفسها مع MDEClientAnalyzer.cmd لتجنب مطالبة المستخدم الذي يطلب تحديد عدد الدقائق الخاصة بجمع البيانات. على سبيل المثال:
>
>    **MDEClientAnalyzer.cmd -r-i -m 5**
>
>   - **-r** - يشير إلى أنه يتم تشغيل الأداة من بعيد (أو سياق غير تفاعلي)
>   - **-i** - علامة السيناريو الخاصة بجمع تتبع الشبكة مع السجلات الأخرى ذات الصلة
>   - **-m** \# - عدد الدقائق التي يجب تشغيلها (5 دقائق في المثال أعلاه)
