---
title: إلحاق أجهزة Windows في Azure Virtual Desktop
description: تعرف على إعداد أجهزة Windows إلى Defender لنقطة النهاية في Azure Virtual Desktop
keywords: Azure Virtual Desktop وAVD وmicrosoft defender ونقطة النهاية والإلحاق
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
audience: ITPro
ms.topic: article
author: dansimp
ms.author: dansimp
ms.custom: nextgen
ms.reviewer: ''
manager: dansimp
ms.collection: M365-security-compliance
ms.openlocfilehash: c7f0896d55d5971b3f9e3848ddddb118f024ac54
ms.sourcegitcommit: e8dd5cd434d17af7096d28d467a2b3b021cbb233
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/27/2022
ms.locfileid: "67050623"
---
# <a name="onboard-windows-devices-in-azure-virtual-desktop"></a>إلحاق أجهزة Windows في Azure Virtual Desktop

6 دقائق للقراءة

**ينطبق على:**
- [Defender for Endpoint الخطة 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- Windows multi-session running on Azure Virtual Desktop (AVD)
- [Windows 10 Enterprise متعددة الجلسات](/microsoft-365/security/defender-endpoint/azure-server-integration)

يدعم Microsoft Defender لنقطة النهاية مراقبة كل من جلسات VDI وAzure Virtual Desktop. اعتمادا على احتياجات مؤسستك، قد تحتاج إلى تنفيذ جلسات VDI أو Azure Virtual Desktop لمساعدة موظفيك على الوصول إلى بيانات الشركة وتطبيقاتها من جهاز غير مدار أو موقع بعيد أو سيناريو مماثل. مع Microsoft Defender لنقطة النهاية، يمكنك مراقبة هذه الأجهزة الظاهرية للنشاط الشاذ.

## <a name="before-you-begin"></a>قبل البدء

تعرف على [اعتبارات VDI غير الثابتة](/microsoft-365/security/defender-endpoint/configure-endpoints-vdi#onboard-non-persistent-virtual-desktop-infrastructure-vdi-devices-1). على الرغم من أن [Azure Virtual Desktop](/azure/virtual-desktop/overview) لا يوفر خيارات غير مثابرة، فإنه يوفر طرقا لاستخدام صورة Windows ذهبية يمكن استخدامها لتوفير مضيفين جدد وأجهزة إعادة توزيع. وهذا يزيد من التقلبات في البيئة، ومن ثم يؤثر على الإدخالات التي يتم إنشاؤها وصيانتها في مدخل Microsoft Defender لنقطة النهاية، مما قد يقلل من الرؤية لمحللي الأمان لديك.

> [!NOTE]
> اعتمادا على اختيارك لأسلوب الإلحاق، يمكن أن تظهر الأجهزة في مدخل Microsoft Defender لنقطة النهاية كما يلي:
>
> - إدخال واحد لكل سطح مكتب ظاهري
> - إدخالات متعددة لكل سطح مكتب ظاهري

توصي Microsoft بإلحاق Azure Virtual Desktop كإلحاق واحد لكل سطح مكتب ظاهري. وهذا يضمن أن تجربة التحقيق في مدخل Microsoft Defender لنقطة النهاية في سياق جهاز واحد استنادا إلى اسم الجهاز. يجب على المؤسسات التي تحذف بشكل متكرر مضيفي AVD وتعيد توزيعهم التفكير بشدة في استخدام هذا الأسلوب لأنه يمنع إنشاء كائنات متعددة لنفس الجهاز في مدخل Microsoft Defender لنقطة النهاية. وقد يؤدي ذلك إلى حدوث ارتباك عند التحقيق في الحوادث. بالنسبة إلى بيئات الاختبار أو غير المتنقلة، يمكنك اختيار الاختيار بشكل مختلف.

توصي Microsoft بإضافة البرنامج النصي Microsoft Defender لنقطة النهاية الإلحاق إلى الصورة الذهبية AVD. بهذه الطريقة، يمكنك التأكد من أن هذا البرنامج النصي الإلحاقي يعمل على الفور في التمهيد الأول. يتم تنفيذه كنص بدء التشغيل في البداية على جميع أجهزة AVD التي يتم توفيرها من الصورة الذهبية AVD. ومع ذلك، إذا كنت تستخدم إحدى صور المعرض دون تعديل، فضع البرنامج النصي في موقع مشترك وقم باستدعاءه من نهج مجموعة المجال أو المحلي.

> [!NOTE]
> يقوم موضع وتكوين البرنامج النصي لبدء تشغيل إعداد VDI على الصورة الذهبية AVD بتكوينه كنص بدء تشغيل يتم تشغيله عند بدء تشغيل AVD. **من غير** المستحسن إلحاق الصورة الذهبية الفعلية AVD. اعتبار آخر هو الأسلوب المستخدم لتشغيل البرنامج النصي. يجب أن يتم تشغيله في أقرب وقت ممكن في عملية بدء التشغيل/التوفير لتقليل الوقت بين الجهاز المتوفر لتلقي جلسات العمل وإعداد الجهاز إلى الخدمة. خذ السيناريوهات 1 و2 أدناه هذا في الاعتبار.

### <a name="scenarios"></a>سيناريوهات

هناك عدة طرق لإلحاق جهاز مضيف AVD:

- شغل البرنامج النصي في الصورة الذهبية (أو من موقع مشترك) أثناء بدء التشغيل.
- استخدم أداة إدارة لتشغيل البرنامج النصي.
- من خلال [التكامل مع Microsoft Defender for Cloud](azure-server-integration.md)

#### <a name="scenario-1-using-local-group-policy"></a>*السيناريو 1: استخدام نهج المجموعة المحلية*

يتطلب هذا السيناريو وضع البرنامج النصي في صورة ذهبية ويستخدم نهج المجموعة المحلية للتشغيل في وقت مبكر من عملية التمهيد.

استخدم الإرشادات الموجودة في [إلحاق أجهزة البنية الأساسية لسطح المكتب الظاهري (VDI) غير الثابتة](configure-endpoints-vdi.md).

اتبع الإرشادات الخاصة بإدخال واحد لكل جهاز.

#### <a name="scenario-2-using-domain-group-policy"></a>*السيناريو 2: استخدام نهج مجموعة المجالات*

يستخدم هذا السيناريو برنامجا نصيا مركزيا ويشغله باستخدام نهج مجموعة يستند إلى المجال. يمكنك أيضا وضع البرنامج النصي في الصورة الذهبية وتشغيله بنفس الطريقة.

##### <a name="download-the-windowsdefenderatponboardingpackagezip-file-from-the-microsoft-365-defender-portal"></a>تنزيل ملف WindowsDefenderATPOnboardingPackage.zip من مدخل Microsoft 365 Defender

1. فتح ملف .zip حزمة تكوين VDI (WindowsDefenderATPOnboardingPackage.zip)

    1. في جزء التنقل في مدخل Microsoft 365 Defender، حدد **إعدادات** \> **إلحاق نقاط** \> النهاية **(ضمن** **إدارة الجهاز**).
    1. حدد Windows 10 أو Windows 11 كنظام التشغيل.
    1. في حقل **أسلوب النشر** ، حدد البرامج النصية لإلحاق VDI لنقاط النهاية غير الثابتة.
    1. انقر فوق **"تنزيل الحزمة** " واحفظ ملف .zip.

2. استخراج محتويات ملف .zip إلى موقع مشترك للقراءة فقط يمكن الوصول إليه من قبل الجهاز. يجب أن يكون لديك مجلد يسمى **OptionalParamsPolicy** والملفات **WindowsDefenderATPOnboardingScript.cmd** و **Onboard-NonPersistentMachine.ps1**.

##### <a name="use-group-policy-management-console-to-run-the-script-when-the-virtual-machine-starts"></a>استخدام وحدة تحكم إدارة نهج المجموعة لتشغيل البرنامج النصي عند بدء تشغيل الجهاز الظاهري

1. افتح وحدة تحكم إدارة نهج المجموعة (GPMC)، وانقر بزر الماوس الأيمن فوق الكائن نهج المجموعة (GPO) الذي تريد تكوينه وانقر فوق **"تحرير**".

2. في نهج المجموعة Management Editor، انتقل إلى **إعدادات لوحة التحكم** **في تفضيلات** \> **تكوين** \> الكمبيوتر.

3. انقر بزر الماوس الأيمن فوق **المهام المجدولة**، وانقر فوق **"جديد**"، ثم انقر فوق **"مهمة فورية** " (Windows 7 على الأقل).

4. في النافذة "مهمة" التي يتم فتحها، انتقل إلى علامة التبويب **"عام** ". ضمن **خيارات الأمان** ، انقر فوق **تغيير المستخدم أو المجموعة** واكتب SYSTEM. انقر فوق **"التحقق من الأسماء** " ثم انقر فوق "موافق". يظهر NT AUTHORITY\SYSTEM كحساب المستخدم الذي سيتم تشغيل المهمة عليه.

5. حدد **"تشغيل" سواء تم تسجيل دخول المستخدم أم لا** وحدد خانة الاختيار **"تشغيل بامتيازات أعلى** ".

6. انتقل إلى علامة التبويب **"إجراءات** " وانقر فوق **"جديد**". تأكد **من تحديد "بدء برنامج** " في الحقل "إجراء". أدخل ما يلي:

   `Action = "Start a program"`

   `Program/Script = C:\WINDOWS\system32\WindowsPowerShell\v1.0\powershell.exe`

   `Add Arguments (optional) = -ExecutionPolicy Bypass -command "& \\Path\To\Onboard-NonPersistentMachine.ps1"`

   ثم حدد **"موافق** " وأغلق أي نوافذ GPMC مفتوحة.

#### <a name="scenario-3-onboarding-using-management-tools"></a>*السيناريو 3: الإلحاق باستخدام أدوات الإدارة*

إذا كنت تخطط لإدارة أجهزتك باستخدام أداة إدارة، يمكنك إلحاق الأجهزة باستخدام نقطة نهاية Microsoft Configuration Manager.

لمزيد من المعلومات، راجع [إلحاق أجهزة Windows باستخدام Configuration Manager](configure-endpoints-sccm.md).

> [!WARNING]
> إذا كنت تخطط لاستخدام [مرجع قواعد تقليل الأجزاء المعرضة للهجوم](attack-surface-reduction-rules-reference.md)، لاحظ أنه يجب عدم استخدام القاعدة "[حظر عمليات الإنشاء التي تنشأ من أوامر PSExec وWMI](attack-surface-reduction-rules-reference.md#block-process-creations-originating-from-psexec-and-wmi-commands)"، لأن هذه القاعدة غير متوافقة مع الإدارة من خلال نقطة نهاية Microsoft Configuration Manager. تمنع القاعدة أوامر WMI التي يستخدمها العميل Configuration Manager للعمل بشكل صحيح.

> [!TIP]
> بعد إلحاق الجهاز، يمكنك اختيار تشغيل اختبار الكشف للتحقق من أن الجهاز تم إلحاقه بشكل صحيح إلى الخدمة. لمزيد من المعلومات، راجع [تشغيل اختبار الكشف على جهاز Microsoft Defender لنقطة النهاية تم إلحاقه حديثا](run-detection-test.md).

#### <a name="tagging-your-machines-when-building-your-golden-image"></a>وضع علامة على أجهزتك عند إنشاء صورتك الذهبية

كجزء من الإلحاق، قد ترغب في تعيين علامة جهاز لتمييز أجهزة AVD بسهولة أكبر في مركز أمان Microsoft. لمزيد من المعلومات، راجع [إضافة علامات الجهاز عن طريق تعيين قيمة مفتاح التسجيل](machine-tags.md#add-device-tags-by-setting-a-registry-key-value).

#### <a name="other-recommended-configuration-settings"></a>إعدادات التكوين الموصى بها الأخرى

عند إنشاء صورتك الذهبية، قد تحتاج إلى تكوين إعدادات الحماية الأولية أيضا. لمزيد من المعلومات، راجع [إعدادات التكوين المستحسنة الأخرى](configure-endpoints-gp.md#other-recommended-configuration-settings).

أيضا، إذا كنت تستخدم ملفات تعريف مستخدمي FSlogix، نوصيك باستبعاد الملفات التالية من الحماية الدائمة:

**استبعاد الملفات:**

`%ProgramFiles%\FSLogix\Apps\frxdrv.sys`

`%ProgramFiles%\FSLogix\Apps\frxdrvvt.sys`

`%ProgramFiles%\FSLogix\Apps\frxccd.sys`

`%TEMP%\*.VHD`

`%TEMP%\*.VHDX`

`%Windir%\TEMP\*.VHD`

`%Windir%\TEMP\*.VHDX`

`\\storageaccount.file.core.windows.net\share\*\*.VHD`

`\\storageaccount.file.core.windows.net\share\*\*.VHDX`

**استبعاد العمليات:**

`%ProgramFiles%\FSLogix\Apps\frxccd.exe`

`%ProgramFiles%\FSLogix\Apps\frxccds.exe`

`%ProgramFiles%\FSLogix\Apps\frxsvc.exe`

#### <a name="licensing-requirements"></a>متطلبات الترخيص

ملاحظة حول الترخيص: عند استخدام Windows Enterprise متعدد الجلسات، وفقا لمتطلباتك، يمكنك اختيار إما ترخيص جميع المستخدمين من خلال Microsoft Defender لنقطة النهاية (لكل مستخدم) أو Windows Enterprise E5 أو Microsoft 365 Security أو Microsoft 365 E5 أو ترخيص الجهاز الظاهري من خلال Microsoft Defender for Cloud.
يمكن العثور على متطلبات الترخيص Microsoft Defender لنقطة النهاية في: [متطلبات الترخيص](minimum-requirements.md#licensing-requirements).

### <a name="known-issues-and-limitations"></a>المشاكل والقيود المعروفة

يتم دعم Microsoft Edge فقط لتصفية الويب في Windows 10 جلسات متعددة.

#### <a name="related-links"></a>الارتباطات ذات الصلة

[إضافة استثناءات ل Defender لنقطة النهاية عبر PowerShell](/azure/architecture/example-scenario/wvd/windows-virtual-desktop-fslogix#add-exclusions-for-microsoft-defender-by-using-powershell)
