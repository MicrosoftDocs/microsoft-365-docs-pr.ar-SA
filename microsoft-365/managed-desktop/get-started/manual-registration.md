---
title: التسجيل اليدوي
description: تسجيل الأجهزة التي يجب إدارتها بواسطة Microsoft Managed Desktop
ms.service: m365-md
author: tiaraquan
f1.keywords:
- NOCSH
ms.author: tiaraquan
ms.localizationpriority: medium
ms.collection: M365-modern-desktop
manager: dougeby
ms.topic: article
audience: Admin
ms.openlocfilehash: aaa1446cbb1ffdc20b023f568a7fd41d6cf01848
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/08/2022
ms.locfileid: "63704953"
---
# <a name="manual-registration"></a>التسجيل اليدوي

يمكن أن يعمل Microsoft Managed Desktop مع الأجهزة الجديدة، أو يمكنك إعادة استخدام الأجهزة التي قد تكون لديك بالفعل. إذا قمت بإعادة استخدام الأجهزة، فيجب إعادة اعادتها. يمكنك تسجيل الأجهزة باستخدام Microsoft Managed Desktop في إدارة نقاط النهاية من Microsoft الإلكتروني.

> [!NOTE]
> هل تعمل مع شريك للحصول على الأجهزة؟ إذا كان الأمر كذلك، فلا داعي للقلق بشأن الحصول على هازات الأجهزة؛ سيهتمون بذلك من أجلك. تأكد من أن شريكك ينشئ علاقة معك في [مركز الشركاء](https://partner.microsoft.com/dashboard). يمكن لشريكك معرفة المزيد في [تعليمات مركز الشركاء](/partner-center/request-a-relationship-with-a-customer). <br><br>بمجرد إنشاء هذه العلاقة، سيسجل شريكك ببساطة الأجهزة بالنيابة عنك ، ولا يتطلب منك اتخاذ أي إجراء آخر. إذا كنت تريد الاطلاع على التفاصيل، أو إذا كان شريكك لديه أسئلة، فشاهد [تسجيل الشريك](partner-registration.md). بمجرد تسجيل الأجهزة، يمكنك متابعة التحقق [من الصورة](#check-the-image) وتسليم [الأجهزة](#deliver-the-device) للمستخدمين.

## <a name="prepare-to-register-brand-new-devices"></a>التحضير لتسجيل الأجهزة الجديدة

بمجرد أن تكون الأجهزة الجديدة في متناول يديك، ستتبع الخطوات التالية:

1. [الحصول على هاش الأجهزة لكل جهاز.](#obtain-the-hardware-hash)
2. [دمج بيانات هاش.](#merge-hash-data)
3. [قم بتسجيل الأجهزة في Microsoft Managed Desktop](#register-devices-by-using-the-admin-portal).
4. [تحقق مرة أخرى من صحة الصورة.](#check-the-image)
5. [تسليم الجهاز](#deliver-the-device).

### <a name="obtain-the-hardware-hash"></a>الحصول على هاش الأجهزة

يعرف Microsoft Managed Desktop كل جهاز بشكل فريد من خلال الإشارة إلى تفرق الأجهزة الخاص به. لديك ثلاثة خيارات للحصول على هذه المعلومات.

**للحصول على هاش الأجهزة:**

- اطلب من مورد الشركة الأصلية لديك استخدام ملف تسجيل AutoPilot، الذي سيتضمن هاشمات الأجهزة.
- تشغيل برنامج [Windows PowerShell نصي](#powershell-script-method) على كل جهاز وجمع النتائج في ملف.
- ابدأ تشغيل كل جهاز، ولكن لا تكمل تجربة Windows، واجمع الهازات على محرك أقراص [محمول قابل للإزالة](#flash-drive-method).

#### <a name="powershell-script-method"></a>أسلوب البرنامج النصي PowerShell

يمكنك استخدام البرنامج النصي [Get-WindowsAutoPilotInfo.ps1](https://www.powershellgallery.com/packages/Get-WindowsAutoPilotInfo) PowerShell على موقع معرض PowerShell على الويب. للحصول على مزيد من المعلومات حول تحديد هوية الجهاز وهش الأجهزة، راجع إضافة [أجهزة Windows Autopilot](/mem/autopilot/add-devices#device-identification).

**لاستخدام أسلوب البرنامج النصي Powershell:**

1. افتح مطالبة PowerShell بحقوق إدارية.
2. تشغيل `Install-Script -Name Get-WindowsAutoPilotInfo`.
3. تشغيل `powershell -ExecutionPolicy Unrestricted Get-WindowsAutoPilotInfo -OutputFile <path>\hardwarehash.csv`.
4. تشغيل `powershell -ExecutionPolicy restricted` لمنع تشغيل البرامج النصية غير المقيدة اللاحقة.

#### <a name="flash-drive-method"></a>أسلوب محرك أقراص Flash

**لاستخدام أسلوب محرك الأقراص flash:**

1. على جهاز آخر غير الجهاز الذي تقوم بتسجيله، قم بإدراج محرك أقراص USB.
2. افتح مطالبة PowerShell بحقوق إدارية.
3. تشغيل `Save-Script -Name Get-WindowsAutoPilotInfo -Path <pathToUsb>`
4. قم تشغيل الجهاز الذي تقوم بتسجيله، *ولكن لا تبدأ تجربة الإعداد*. إذا بدأت تجربة الإعداد عن طريق الخطأ،  فسوف تحتاج إلى إعادة تعيين الجهاز أو إعادة ترتيبه.
5. أدرج محرك أقراص USB، ثم اضغط على SHIFT + F10.
6. افتح مطالبة PowerShell بحقوق إدارية، ثم قم بتشغيل `cd <pathToUsb>`.
7. تشغيل `Set-ExecutionPolicy -ExecutionPolicy Unrestricted`
8. تشغيل `.\Get-WindowsAutoPilotInfo -OutputFile <path>\hardwarehash.csv`
9. إزالة محرك أقراص USB، ثم إيقاف تشغيل الجهاز عن طريق تشغيل `shutdown -s -t 0`

> [!IMPORTANT]
> لا تعمل على الجهاز الذي تقوم بتسجيله مرة أخرى حتى الانتهاء من التسجيل له.

### <a name="merge-hash-data"></a>دمج بيانات هاش

ستحتاج إلى دمج البيانات الموجودة في ملفات CSV في ملف واحد لإكمال التسجيل. فيما يلي نموذج برنامج PowerShell النصي لجعله سهلا:

`Import-CSV -Path (Get-ChildItem -Filter *.csv) | ConvertTo-Csv -NoTypeInformation | % {$_.Replace('"', '')} | Out-File .\aggregatedDevices.csv`

> [!NOTE]
> الأعمدة الإضافية غير معتمدة. علامات الاقتباس غير معتمدة. يمكن استخدام الملفات النصية بتنسيق ANSI فقط (وليس Unicode). تتحسس رؤوس الاصهار حالة التحسس. لن يؤدي تحرير الملف Excel حفظه كملف CSV إلى إنشاء ملف قابل للاستخدام بسبب هذه المتطلبات. تأكد من الاحتفاظ بأي أصفار ناسلة في الأرقام التسلسلية للجهاز.

### <a name="register-devices-by-using-the-admin-portal"></a>تسجيل الأجهزة باستخدام مدخل المسؤول

في [إدارة نقاط النهاية من Microsoft](https://endpoint.microsoft.com/)، حدد **الأجهزة** في جزء التنقل الأيسر. في المقطع Microsoft Managed Desktop، حدد **الأجهزة**. في مساحة عمل أجهزة سطح المكتب المدارة من Microsoft، حدد **+ تسجيل الأجهزة**، مما يفتح إرسالا مطيرا لتسجيل أجهزة جديدة.

<!-- [![Fly-in after selecting Register devices, listing devices with columns for assigned users, serial number, status, last-seen date, and age.](../../media/new-registration-ui.png)](../../media/new-registration-ui.png) -->

<!--Registering any existing devices with Managed Desktop will completely re-image them; make sure you've backed up any important data prior to starting the registration process.-->

**لتسجيل الأجهزة باستخدام مدخل المسؤول:**

1. في **تحميل الملف**، قم بتوفير مسار إلى ملف CSV الذي أنشأته مسبقا.
2. حدد ملف [تعريف الجهاز](../service-description/profiles.md) في القائمة المنسدلة.
3. حدد **تسجيل الأجهزة**. سيضيف النظام الأجهزة إلى قائمة الأجهزة على **الأجهزة**، التي تم وضع علامة عليها ك **تسجيل معلق**. يستغرق التسجيل عادة أقل من 10 دقائق، وعند نجاحه، سيعرض الجهاز على أنه  جاهز للمستخدم مما يعني أنه جاهز وينتظر أن يبدأ المستخدم في استخدامه.

> [!NOTE]
> إذا قمت بتغيير عضوية مجموعة Azure Active Directory (AAD (دليل Azure النشط)) لجهاز يدويا، سيتم إعادة تعيينها تلقائيا إلى المجموعة لملف تعريف الجهاز الخاص بها وإزالتها من أي مجموعات متضاربة.

يمكنك مراقبة تقدم تسجيل الجهاز على الصفحة الرئيسية. تتضمن الولايات المحتملة التي تم التقارير عنها ما يلي:

| الولاية | الوصف |
| -----|-----|
| التسجيل معلق | لم يتم إكمال التسجيل بعد. تحقق مرة أخرى لاحقا. |
| فشل التسجيل | لا يمكن إكمال التسجيل. لمزيد من المعلومات، راجع استكشاف الأخطاء [في تسجيل الجهاز وإصلاحها](#troubleshooting-device-registration). |
| جاهز للمستخدم | نجح التسجيل. الجهاز جاهز الآن لتسليمه إلى المستخدم. سيرشدهم سطح المكتب المدار من Microsoft خلال عملية الإعداد للمرة الأولى، لذا لن تحتاج إلى إجراء أي تحضيرات إضافية. |
| نشط | تم تسليم الجهاز إلى المستخدم وقد تم تسجيله لدى المستأجر الخاص بك. تشير هذه الحالة أيضا إلى أنهم يستخدمون الجهاز بشكل منتظم. |
| غير نشط | تم تسليم الجهاز إلى المستخدم وقد تم تسجيله لدى المستأجر الخاص بك. ومع ذلك، لم يستخدم الجهاز مؤخرا (في الأيام السبعة الأخيرة).  |

#### <a name="troubleshooting-device-registration"></a>استكشاف الأخطاء في تسجيل الجهاز وإصلاحها

| رسالة خطأ | التفاصيل |
|-----| ----- |
| لم يتم العثور على الجهاز | لم نتمكن من تسجيل هذا الجهاز لأننا لم نتمكن من العثور على تطابق لمصنع أو نموذج أو رقم تسلسلي تم توفيره. تأكد من هذه القيم مع مورد جهازك. |
| هاش الأجهزة غير صالح | لم يتم تنسيق هاش الأجهزة التي قدمتها لهذا الجهاز بشكل صحيح. تحقق مرة أخرى من تقطع الأجهزة ثم إعادة إرساله. |
| الجهاز مسجل بالفعل | هذا الجهاز مسجل بالفعل في مؤسستك. لا يلزم اتخاذ أي إجراء آخر. |
| الجهاز الذي تطالب به مؤسسة أخرى | تم بالفعل المطالبة بهذا الجهاز من قبل مؤسسة أخرى. تحقق من مورد جهازك. |
| خطأ غير متوقع | لا يمكن معالجة طلبك تلقائيا. اتصل بالدعم ووفر "الموفر" لموفر الطلب: `<requestId>` |

### <a name="check-the-image"></a>التحقق من الصورة

إذا كان جهازك يأتي من مورد شريك Microsoft Managed Desktop، يجب أن تكون الصورة صحيحة.

كما يمكنك أيضا تطبيق الصورة بنفسك إذا كنت تفضل ذلك. للبدء، اتصل بممثل Microsoft الذي تعمل معه. سيزودك الممثل بموقع الصورة والخطوات اللازمة لتطبيقها.

### <a name="autopilot-group-tag"></a>علامة مجموعة Autopilot

عند استخدام مدخل المسؤول لتسجيل الأجهزة، نقوم تلقائيا بتعيين علامة مجموعة Autopilot المقترنة بملف تعريف الجهاز المدرج في [تسجيل الأجهزة باستخدام مركز الشركاء](partner-registration.md).
تراقب الخدمة كل أجهزة سطح المكتب المدارة من Microsoft يوميا وتعين علامة المجموعة إلى أي أجهزة لا تملكها بالفعل.

### <a name="deliver-the-device"></a>تسليم الجهاز

> [!IMPORTANT]
> قبل تسليم الجهاز إلى المستخدم، تأكد من حصولك على التراخيص المناسبة لهذا المستخدم وتطبيقها.[](../get-ready/prerequisites.md)

إذا تم تطبيق جميع التراخيص، يمكنك [أن تجهز المستخدمين لاستخدام الأجهزة](get-started-devices.md). بعد ذلك، يمكن للمستخدم بدء تشغيل الجهاز والمتابعة عبر تجربة Windows الإعداد.
