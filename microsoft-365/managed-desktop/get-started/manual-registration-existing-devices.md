---
title: التسجيل اليدوي للأجهزة الموجودة
description: تسجيل الأجهزة الموجودة بحيث يمكن إدارتها بواسطة Microsoft Managed Desktop
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
ms.openlocfilehash: 1d100cc3336dcb465e54f4b81d13d50ecd4bfe1e
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/08/2022
ms.locfileid: "63703441"
---
# <a name="manual-registration-for-existing-devices"></a>التسجيل اليدوي للأجهزة الموجودة

>[!NOTE]
>تصف هذه المقالة الخطوات التي يجب عليك اتخاذها لإعادة استخدام الأجهزة التي تملكها بالفعل، وتسجيلها في Microsoft Managed Desktop. إذا كنت تستخدم أجهزة جديدة، فاتبع الخطوات في تسجيل [أجهزة جديدة في Microsoft Managed Desktop بنفسك بدلا من](manual-registration.md) ذلك. <br> <br> تم توثيق العملية للشركاء في [خطوات للشركاء لتسجيل الأجهزة](partner-registration.md).

يمكن أن يعمل Microsoft Managed Desktop مع الأجهزة الجديدة، أو يمكنك إعادة استخدام الأجهزة التي قد تكون لديك بالفعل. إذا قمت بإعادة استخدام الأجهزة، فيجب إعادة اعادتها. يمكنك تسجيل الأجهزة باستخدام Microsoft Managed Desktop في إدارة نقاط النهاية من Microsoft الإلكتروني.

## <a name="prepare-to-register-existing-devices"></a>التحضير لتسجيل الأجهزة الموجودة

**لتسجيل الأجهزة الموجودة:**

1. [الحصول على هاش الأجهزة لكل جهاز.](#obtain-the-hardware-hash)
2. [دمج بيانات هاش.](#merge-hash-data)
3. [قم بتسجيل الأجهزة في Microsoft Managed Desktop](#register-devices-by-using-the-admin-portal).
4. [تحقق مرة أخرى من صحة الصورة.](#check-the-image)
5. [تسليم الجهاز](#deliver-the-device).

### <a name="obtain-the-hardware-hash"></a>الحصول على هاش الأجهزة

يعرف Microsoft Managed Desktop كل جهاز بشكل فريد من خلال الإشارة إلى تفرق الأجهزة الخاص به. لديك أربعة خيارات للحصول على هذه المعلومات من الأجهزة التي تستخدمها بالفعل.

**للحصول على هاش الأجهزة:**

- اطلب من مورد الشركة الأصلية لديك استخدام ملف تسجيل AutoPilot، الذي سيتضمن هاشمات الأجهزة.
- تجميع المعلومات في [Microsoft Endpoint Configuration Manager](#microsoft-endpoint-configuration-manager).
- تشغيل برنامج Windows PowerShell إما باستخدام [Active Directory](#active-directory-powershell-script-method) أو [يدويا](#manual-powershell-script-method) على كل جهاز، وجمع النتائج في ملف.
- ابدأ تشغيل كل جهاز، ولكن لا تكمل تجربة Windows، واجمع الهازات على محرك أقراص [محمول قابل للإزالة](#flash-drive-method).

#### <a name="microsoft-endpoint-configuration-manager"></a>Microsoft Endpoint Configuration Manager

يمكنك استخدام Microsoft Endpoint Configuration Manager لتجميع تهاني الأجهزة من الأجهزة الموجودة التي تريد تسجيلها في Microsoft Managed Desktop. إذا كنت قد أوفيت بكل هذه المتطلبات الأساسية، تكون جاهزا لتجميع المعلومات.

> [!IMPORTANT]
> يجب تشغيل أي أجهزة تريد الحصول على هذه المعلومات لها Windows 10 الإصدار 1703 أو إصدار أحدث.

**لتجميع معلومات هاشش الأجهزة:**

1. في وحدة تحكم إدارة التكوين، حدد **مراقبة**.
2. في مساحة عمل المراقبة، قم بتوسيع عقدة **إعداد** التقارير، وتوسيع **التقارير**، وحدد **عقدة الأجهزة -** عام.
3. يمكنك تشغيل التقرير، **Windows معلومات جهاز Autopilot**، وعرض النتائج.
4. في عارض التقرير، حدد الأيقونة **تصدير** ، وحدد **الخيار CSV (محدد ب** فاصلة).
5. بعد حفظ الملف، ستحتاج إلى تصفية النتائج فقط على الأجهزة التي تخطط لتسجيلها في Microsoft Managed Desktop. بعد ذلك، قم بتحميل البيانات إلى Microsoft Managed Desktop.
    - افتح إدارة نقاط النهاية من Microsoft وانتقل إلى **قائمة الأجهزة**.
    - في المقطع Microsoft Managed Desktop، حدد **الأجهزة**.
    - حدد **+ تسجيل الأجهزة**، مما يفتح تسجيلا مطيرا لتسجيل الأجهزة الجديدة.

لمزيد من المعلومات، راجع [تسجيل الأجهزة باستخدام مدخل المسؤول](#register-devices-by-using-the-admin-portal) أدناه.

#### <a name="active-directory-powershell-script-method"></a>أسلوب البرنامج النصي Active Directory PowerShell

في بيئة Active Directory، يمكنك استخدام الأمر cmdlet PowerShell لتجميع المعلومات عن بعد من الأجهزة في مجموعات Active Directory `Get-WindowsAutoPilotInfo` باستخدام WinRM. يمكنك أيضا استخدام `Get-AD Computer` الأمر cmdlet والحصول على نتائج تمت تصفيتها لاسم نموذج أجهزة معين مضمن في الكتالوج. قبل المتابعة، تأكد من هذه المتطلبات الأساسية، ثم تابع.

**لاستخدام أسلوب البرنامج النصي Active Directory PowerShell:**

1. تأكد من تمكين WinRM.
1. الأجهزة التي تريد تسجيلها نشطة على الشبكة. أي أنها غير منقطعة الاتصال أو م إيقاف تشغيلها.
1. تأكد من أن لديك معلمة بيانات اعتماد المجال التي تملك الإذن للتنفيذ عن بعد على الأجهزة.
1. تأكد من أن Windows جدار الحماية يسمح بالوصول إلى WMI. للقيام بذلك، اتبع الخطوات التالية:

    - افتح لوحة **التحكم Windows جدار حماية Defender** وحدد السماح لتطبيق أو **ميزة من خلال Windows Defender.**
    - ابحث **Windows أدوات الإدارة (WMI)** في القائمة، وتمكين كل من "خاص" و"**عام**"، ثم حدد **موافق**.
1. افتح مطالبة PowerShell بحقوق إدارية.
1. تشغيل *أي من* هذه البرامج النصية:

    ```powershell
    Install-script -name Get-WindowsAutoPilotInfo 
    #example one – leverage Get-ADComputer to enumerate devices 
    Get-ADComputer -filter * | powershell -ExecutionPolicy Unrestricted Get-WindowsAutoPilotInfo.ps1 -credential Domainname\<accountname>
    ```

    ```powershell
    #example two – target specific devices: 
    Set-ExecutionPolicy powershell -ExecutionPolicy Unrestricted Get-WindowsAutoPilotInfo.ps1 -credential Domainname\<accountname> -Name Machine1,Machine2,Machine3
    ```

1. الوصول إلى أي دليل قد يكون فيه إدخالات للأجهزة. قم بإزالة الإدخالات لكل جهاز من *كل* الدلائل، بما في ذلك Windows خدمات مجال Server Active Directory و Azure Active Directory. قد تستغرق المعالجة بالكامل بضع ساعات.
1. الوصول إلى خدمات الإدارة حيث قد تكون هناك إدخالات للأجهزة. قم بإزالة الإدخالات لكل *جهاز من كل* خدمات الإدارة، بما في ذلك Microsoft Endpoint Configuration Manager و Microsoft Intune و Windows Autopilot. قد تستغرق المعالجة بالكامل بضع ساعات.

يمكنك الآن المتابعة [لتسجيل الأجهزة](#register-devices-by-using-the-admin-portal).

#### <a name="manual-powershell-script-method"></a>أسلوب برنامج PowerShell النصي اليدوي

**لاستخدام أسلوب برنامج Powershell النصي اليدوي:**

1. افتح مطالبة PowerShell بحقوق إدارية.
2. تشغيل `Install-Script -Name Get-WindowsAutoPilotInfo`.
3. تشغيل `powershell -ExecutionPolicy Unrestricted Get-WindowsAutoPilotInfo -OutputFile <path>\hardwarehash.csv`.
4. [دمج بيانات هاش.](#merge-hash-data)

#### <a name="flash-drive-method"></a>أسلوب محرك أقراص Flash

**لاستخدام أسلوب محرك الأقراص flash:**

1. على جهاز آخر غير الجهاز الذي تقوم بتسجيله، قم بإدراج محرك أقراص USB.
2. افتح مطالبة PowerShell بحقوق إدارية.
3. تشغيل `Save-Script -Name Get-WindowsAutoPilotInfo -Path <pathToUsb>`.
4. قم تشغيل الجهاز الذي تقوم بتسجيله، *ولكن لا تبدأ تجربة الإعداد*. إذا بدأت تجربة الإعداد عن طريق الخطأ،  فسوف تحتاج إلى إعادة تعيين الجهاز أو إعادة ترتيبه.
5. أدرج محرك أقراص USB، ثم اضغط على SHIFT + F10.
6. افتح مطالبة PowerShell بحقوق إدارية، ثم قم بتشغيل `cd <pathToUsb>`.
7. تشغيل `Set-ExecutionPolicy -ExecutionPolicy Unrestricted`.
8. تشغيل `.\Get-WindowsAutoPilotInfo -OutputFile <path>\hardwarehash.csv`.
9. قم بإزالة محرك أقراص USB، ثم قم بإيقاف تشغيل الجهاز عن طريق تشغيل `shutdown -s -t 0`.
10. [دمج بيانات هاش.](#merge-hash-data)

> [!IMPORTANT]
> لا تعمل على الجهاز الذي تقوم بتسجيله مرة أخرى حتى الانتهاء من التسجيل له.

### <a name="merge-hash-data"></a>دمج بيانات هاش

إذا قمت بتجميع بيانات تجزيش الأجهزة باستخدام أساليب PowerShell اليدوية أو محرك الأقراص flash، فيجب دمج البيانات الموجودة في ملفي CSV في ملف واحد لإكمال التسجيل. فيما يلي نموذج برنامج PowerShell النصي لجعله سهلا:

```powershell
Import-CSV -Path (Get-ChildItem -Filter *.csv) | ConvertTo-Csv -NoTypeInformation | % {$_.Replace('"', '')} | Out-File .\aggregatedDevices.csv
```

مع دمج بيانات هاش في ملف CSV واحد، يمكنك الآن المتابعة [لتسجيل الأجهزة](#register-devices-by-using-the-admin-portal).

## <a name="register-devices-by-using-the-admin-portal"></a>تسجيل الأجهزة باستخدام مدخل المسؤول

في [إدارة نقاط النهاية من Microsoft](https://endpoint.microsoft.com/)، حدد **الأجهزة** في جزء التنقل الأيسر. في المقطع Microsoft Managed Desktop، حدد **الأجهزة**. في مساحة عمل أجهزة سطح المكتب المدارة من Microsoft، حدد **+ تسجيل الأجهزة**، مما يفتح إرسالا مطيرا لتسجيل أجهزة جديدة.

<!-- Update with new picture [![Fly-in after selecting Register devices, listing devices with columns for assigned users, serial number, status, last-seen date, and age.](../../media/new-registration-ui.png)](../../media/new-registration-ui.png) -->

<!--Registering any existing devices with Managed Desktop will completely re-image them; make sure you've backed up any important data prior to starting the registration process.-->

**لتسجيل الأجهزة باستخدام مدخل المسؤول:**

1. في **تحميل الملف**، قم بتوفير مسار إلى ملف CSV الذي أنشأته مسبقا.
2. حدد ملف [تعريف الجهاز](../service-description/profiles.md) في القائمة المنسدلة.
3. حدد **تسجيل الأجهزة**. سيضيف النظام الأجهزة إلى قائمة الأجهزة على شفرة **الأجهزة**. يتم وضع علامة على الأجهزة ك **"معلق التسجيل**". يستغرق التسجيل عادة أقل من 10 دقائق، وعند نجاحه، يظهر الجهاز على أنه **جاهز للمستخدم**. **جاهز للمستخدم** يعني أنه جاهز وينتظر أن يبدأ المستخدم في استخدامه.

> [!NOTE]
> إذا قمت بتغيير عضوية مجموعة Azure Active Directory (AAD (دليل Azure النشط)) لجهاز يدويا، سيتم إعادة تعيينها تلقائيا إلى المجموعة لملف تعريف الجهاز الخاص بها وإزالتها من أي مجموعات متضاربة.

يمكنك مراقبة تقدم تسجيل الجهاز على الصفحة الرئيسية. تتضمن الولايات المحتملة التي تم التقارير عنها ما يلي:

| الولاية | الوصف |
| ----- | ----- |
| التسجيل معلق | لم يتم إكمال التسجيل بعد. تحقق مرة أخرى لاحقا. |
| فشل التسجيل | لا يمكن إكمال التسجيل. لمزيد من المعلومات، راجع استكشاف الأخطاء [في تسجيل الجهاز وإصلاحها](#troubleshooting-device-registration). |
| جاهز للمستخدم | نجح التسجيل. الجهاز جاهز الآن لتسليمه إلى المستخدم. سيرشدهم سطح المكتب المدار من Microsoft خلال عملية الإعداد للمرة الأولى، لذا لن تحتاج إلى إجراء أي تحضيرات إضافية. |
| نشط | تم تسليم الجهاز إلى المستخدم وقد تم تسجيله لدى المستأجر الخاص بك. تشير هذه الحالة أيضا إلى أنهم يستخدمون الجهاز بشكل منتظم. |
| غير نشط | تم تسليم الجهاز إلى المستخدم وقد تم تسجيله لدى المستأجر الخاص بك. ومع ذلك، لم يستخدم المستخدم الجهاز مؤخرا (في الأيام السبعة الأخيرة). |

### <a name="troubleshooting-device-registration"></a>استكشاف الأخطاء في تسجيل الجهاز وإصلاحها

| رسالة خطأ | التفاصيل |
| ----- | ----- |
| لم يتم العثور على الجهاز | لم نتمكن من تسجيل هذا الجهاز لأننا لم نتمكن من العثور على تطابق لمصنع أو نموذج أو رقم تسلسلي تم توفيره. تأكد من هذه القيم مع مورد جهازك. |
| هاش الأجهزة غير صالح | لم يتم تنسيق هاش الأجهزة التي قدمتها لهذا الجهاز بشكل صحيح. تحقق مرة أخرى من تقطع الأجهزة ثم إعادة إرساله. |
| الجهاز مسجل بالفعل | هذا الجهاز مسجل بالفعل في مؤسستك. لا يلزم اتخاذ أي إجراء آخر. |
| الجهاز الذي تطالب به مؤسسة أخرى | تم بالفعل المطالبة بهذا الجهاز من قبل مؤسسة أخرى. تحقق من مورد جهازك. |
| خطأ غير متوقع | لا يمكن معالجة طلبك تلقائيا. اتصل بالدعم ووفر "الموفر" لموفر الطلب: `<requestId>` |

## <a name="check-the-image"></a>التحقق من الصورة

إذا كان جهازك يأتي من مورد شريك Microsoft Managed Desktop، يجب أن تكون الصورة صحيحة.

كما يمكنك أيضا تطبيق الصورة بنفسك إذا كنت تفضل ذلك. للبدء، اتصل بممثل Microsoft الذي تعمل معه وسيوفر لك الموقع والخطوات اللازمة لتطبيق الصورة.

## <a name="deliver-the-device"></a>تسليم الجهاز

> [!IMPORTANT]
> قبل تسليم الجهاز إلى المستخدم، تأكد من حصولك على التراخيص المناسبة لهذا المستخدم وتطبيقها.[](../get-ready/prerequisites.md)

إذا تم تطبيق جميع التراخيص، يمكنك [أن تجهز المستخدمين لاستخدام الأجهزة](get-started-devices.md). بعد ذلك، يمكن للمستخدم بدء تشغيل الجهاز والمتابعة عبر تجربة Windows الإعداد.
