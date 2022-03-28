---
title: أجهزة Windows متعددة جلسات العمل في Azure Virtual Desktop
description: اقرأ المزيد في هذه المقالة حول Windows الأجهزة متعددة جلسات العمل في Azure Virtual Desktop
keywords: Azure Virtual Desktop، WVD، microsoft defender، نقطة النهاية، اللوحة
ms.prod: w10
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
ms.openlocfilehash: d97326987af49b9bac44b3578884c72d756d5595
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/08/2022
ms.locfileid: "63575091"
---
# <a name="onboard-windows-multi-session-devices-in-azure-virtual-desktop"></a>أجهزة Windows متعددة جلسات العمل في Azure Virtual Desktop

6 دقائق للقراءة

**ينطبق على:**
- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- Windows جلسات عمل متعددة يتم تشغيلها على Azure Virtual Desktop (AVD)

يدعم Microsoft Defender ل Endpoint مراقبة جلسات سطح المكتب الظاهري ل VDI و Azure. استنادا إلى احتياجات مؤسستك، قد تحتاج إلى تنفيذ جلسات VDI أو Azure Virtual Desktop لمساعدة الموظفين على الوصول إلى بيانات وتطبيقات الشركة من جهاز غير متحكم به أو موقع بعيد أو سيناريو مماثل. باستخدام Microsoft Defender ل Endpoint، يمكنك مراقبة هذه الأجهزة الظاهرية من أجل القيام بنشاط غير متجانس.

## <a name="before-you-begin"></a>قبل البدء

تعرف على اعتبارات [VDI غير الثابتة](/microsoft-365/security/defender-endpoint/configure-endpoints-vdi#onboard-non-persistent-virtual-desktop-infrastructure-vdi-devices-1). على الرغم من أن [Azure Virtual Desktop](/azure/virtual-desktop/overview) لا يوفر خيارات عدم الاستمرار، فإنه يوفر طرقا لاستخدام صورة Windows ذهبية يمكن استخدامها لتوفير أجهزة جديدة للمضيفين و إعادة النشر. يؤدي هذا إلى زيادة حالة التقلبات في البيئة، وبالتالي يؤثر على الإدخالات التي يتم إنشاؤها وصيانتها في مدخل Microsoft Defender لنقطة النهاية، مما يؤدي إلى تقليل مستوى الرؤية لمحللي الأمان.

> [!NOTE]
> استنادا إلى اختيارك لطريقة التكوين، يمكن أن تظهر الأجهزة في مدخل Microsoft Defender ل Endpoint كما يلي:
>
> - إدخال واحد لكل سطح مكتب ظاهري
> - إدخالات متعددة لكل سطح مكتب ظاهري

توصي Microsoft بالتحاق Azure Virtual Desktop كمدخل واحد لكل سطح مكتب ظاهري. يضمن ذلك أن تجربة التحقيق في مدخل Microsoft Defender لنقطة النهاية في سياق جهاز واحد يستند إلى اسم الجهاز. يجب على المؤسسات التي تحذف مضيفي WVD ويعاد نشرهم بشكل متكرر أن تفكر بشدة في استخدام هذا الأسلوب حيث إنه يمنع إنشاء كائنات متعددة لنفس الجهاز في مدخل Microsoft Defender ل Endpoint. قد يؤدي ذلك إلى حدوث إرباك عند التحقق من الأحداث. بالنسبة للبيئات الاختبارية أو غير المتقلبة، يمكنك اختيار اختيار مختلف.

توصي Microsoft بإضافة البرنامج النصي ل Microsoft Defender for Endpoint onboarding إلى الصورة الذهبية ل WVD. بهذه الطريقة، يمكنك التأكد من تشغيل هذا البرنامج النصي ل التكائم مباشرة عند التشغيل الأول. يتم تنفيذه كنص بدء تشغيل في التشغيل الأول على جميع أجهزة WVD التي تم توفيرها من الصورة الذهبية ل WVD. ومع ذلك، إذا كنت تستخدم إحدى صور المعرض بدون تعديل، ف ضع البرنامج النصي في موقع مشترك واتصل به إما من نهج مجموعة المجالات أو المحلي.

> [!NOTE]
> يعمل تعيين موضع البرنامج النصي لبدء تشغيل VDI وتكوينه على الصورة الذهبية WVD على تكوينه كنص بدء تشغيل يتم تشغيله عند بدء تشغيل WVD. لا يوصى **بتكليف** صورة WVD الذهبية الفعلية. ثمة اعتبار آخر وهو الأسلوب المستخدم لتشغيل البرنامج النصي. يجب أن يتم تشغيله في أقرب وقت ممكن من عملية بدء التشغيل/توفير الخدمة لتقليل الوقت بين توفر الجهاز لتلقي جلسات العمل وتوافر الجهاز للخدمة. أسفل السيناريوهات 1 و2، خذ هذا في الاعتبار.

### <a name="scenarios"></a>السيناريوهات

هناك عدة طرق ل متن جهاز مضيف WVD:

- تشغيل البرنامج النصي في الصورة الذهبية (أو من موقع مشترك) أثناء بدء التشغيل.
- استخدم أداة إدارة لتشغيل البرنامج النصي.
- من [خلال التكامل مع Microsoft Defender for Cloud](azure-server-integration.md)

#### <a name="scenario-1-using-local-group-policy"></a>*السيناريو 1: استخدام نهج المجموعة المحلي*

يتطلب هذا السيناريو وضع البرنامج النصي في صورة ذهبية ويستخدم نهج المجموعة المحلية للتشغيل المبكر في عملية التشغيل.

استخدم الإرشادات الموجودة في أجهزة البنية الأساسية لسطح المكتب الظاهري [(VDI) غير الثابتة](configure-endpoints-vdi.md).

اتبع الإرشادات الخاصة إدخال واحد لكل جهاز.

#### <a name="scenario-2-using-domain-group-policy"></a>*السيناريو 2: استخدام نهج مجموعة المجالات*

يستخدم هذا السيناريو برنامج نصي في موقع مركزي ويعمل عليه باستخدام نهج مجموعة مستند إلى المجال. يمكنك أيضا وضع البرنامج النصي في الصورة الذهبية وتشغيله بالطريقة نفسها.

##### <a name="download-the-windowsdefenderatponboardingpackagezip-file-from-the-windows-365-defender-portal"></a>تنزيل WindowsDefenderATPOnboardingPackage.zip من مدخل Windows 365 Defender

1. فتح ملف حزمة تكوين VDI .zip (WindowsDefenderATPOnboardingPackage.zip)

    1. في جزء التنقل Microsoft 365 Defender المدخل **، حدد الإعدادات** \> **نقاط** \> **النهاية (ضمن** **إدارة الأجهزة**).
    1. حدد Windows 10 أو Windows 11 نظام التشغيل.
    1. في الحقل **أسلوب النشر** ، حدد برامج VDI النصية لتكديس نقاط النهاية غير الثابتة.
    1. انقر **فوق تنزيل الحزمة** واحفظ .zip الملف.

2. استخراج محتويات الملف .zip إلى موقع مشترك للقراءة فقط يمكن الوصول إليه من قبل الجهاز. يجب أن يكون لديك مجلد يسمى **OptionalParamsPolicy** والملفات **WindowsDefenderATPOnboardingScript.cmd** **Onboard-NonPersistentMachine.ps1**.

##### <a name="use-group-policy-management-console-to-run-the-script-when-the-virtual-machine-starts"></a>استخدام وحدة تحكم إدارة نهج المجموعة لتشغيل البرنامج النصي عند بدء تشغيل الجهاز الظاهري

1. افتح وحدة تحكم إدارة نهج المجموعة (GPMC)، وانقر بز الماوس الأيمن فوق كائن نهج المجموعة (GPO) الذي تريد تكوينه وانقر فوق **تحرير**.

2. في محرر إدارة نهج المجموعة، انتقل إلى **إعدادات** \>  \> لوحة التحكم في تفضيلات **تكوين الكمبيوتر**.

3. انقر بز الماوس الأيمن فوق **المهام المجدولة**، **وانقر فوق جديد**، ثم انقر فوق مهمة فورية **(على** الأقل Windows 7).

4. في نافذة المهمة التي تفتح، انتقل إلى علامة **التبويب عام** . ضمن **خيارات الأمان،** انقر **فوق تغيير المستخدم أو المجموعة** وا اكتب النظام. انقر **فوق التحقق من الأسماء** ثم فوق موافق. يظهر NT AUTHORITY\SYSTEM ك حساب المستخدم الذي سيتم تشغيل المهمة عليه.

5. حدد **تشغيل ما إذا كان المستخدم قد سجل دخوله** أم لا وحدد خانة الاختيار **تشغيل بأعلى** امتيازات.

6. انتقل إلى علامة **التبويب إجراءات** وانقر فوق **جديد**. تأكد من **تحديد بدء** برنامج في حقل الإجراء. أدخل ما يلي:

   `Action = "Start a program"`

   `Program/Script = C:\WINDOWS\system32\WindowsPowerShell\v1.0\powershell.exe`

   `Add Arguments (optional) = -ExecutionPolicy Bypass -command "& \\Path\To\Onboard-NonPersistentMachine.ps1"`

   ثم حدد **موافق** وأغلق أي نوافذ GPMC مفتوحة.

#### <a name="scenario-3-onboarding-using-management-tools"></a>*السيناريو 3: الboarding باستخدام أدوات الإدارة*

إذا كنت تخطط لإدارة أجهزتك باستخدام أداة إدارة، يمكنك استخدام الأجهزة المجهزة Microsoft Endpoint Configuration Manager.

للحصول على مزيد من المعلومات، راجع [Windows الأجهزة باستخدام "إدارة التكوين](configure-endpoints-sccm.md)".

> [!WARNING]
> إذا كنت تخطط لاستخدام مرجع [](attack-surface-reduction-rules-reference.md)قواعد تقليل مساحة الهجوم، فلاحظ أنه لا يجب استخدام القاعدة "حظر إنشاءات العمليات التي تنشأ من [أوامر PSExec و WMI](attack-surface-reduction-rules-reference.md#block-process-creations-originating-from-psexec-and-wmi-commands)"، لأن هذه القاعدة غير متوافقة مع الإدارة من خلال Microsoft Endpoint Configuration Manager. تمنع القاعدة أوامر WMI التي يستخدمها عميل "إدارة التكوين" لكي تعمل بشكل صحيح.

> [!TIP]
> بعد تشغيل الجهاز، يمكنك اختيار تشغيل اختبار الكشف للتحقق من أن الجهاز مدرج بشكل صحيح في الخدمة. لمزيد من المعلومات، راجع [تشغيل اختبار الكشف على جهاز Microsoft Defender ل Endpoint](run-detection-test.md) تم تشغيله حديثا.

#### <a name="tagging-your-machines-when-building-your-golden-image"></a>وضع علامة على الأجهزة عند إنشاء صورتك الذهبية

كجزء من عملية الضبط، قد ترغب في إعداد علامة جهاز لتمييز أجهزة WVD بسهولة أكبر في مركز أمان Microsoft. لمزيد من المعلومات، راجع [إضافة علامات الجهاز من خلال تعيين قيمة مفتاح تسجيل](machine-tags.md#add-device-tags-by-setting-a-registry-key-value).

#### <a name="other-recommended-configuration-settings"></a>إعدادات التكوين المستحسنة الأخرى

عند إنشاء صورتك الذهبية، قد تحتاج إلى تكوين إعدادات الحماية الأولية أيضا. لمزيد من المعلومات، راجع [إعدادات التكوين المستحسنة الأخرى](configure-endpoints-gp.md#other-recommended-configuration-settings).

أيضا، إذا كنت تستخدم ملفات تعريف المستخدمين في FSlogix، نوصي باستبعاد الملفات التالية من الحماية دائما:

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

ملاحظة حول الترخيص: عند استخدام جلسة عمل متعددة في Windows Enterprise، وفقا لمتطلباتك، يمكنك أن تختار إما ترخيص جميع المستخدمين من خلال Microsoft Defender لنقطة النهاية (لكل مستخدم) أو Windows Enterprise E5 أو أمان Microsoft 365 أو Microsoft 365 E5، أو الحصول على ترخيص VM من خلال Microsoft Defender for Cloud.
يمكن العثور على متطلبات الترخيص ل Microsoft Defender لنقطة النهاية في: [متطلبات الترخيص](minimum-requirements.md#licensing-requirements).

### <a name="known-issues-and-limitations"></a>المشاكل والقيود المعروفة

يتم Microsoft Edge فقط لتصفية الويب في Windows 10 متعددة جلسات العمل.

#### <a name="related-links"></a>الارتباطات ذات الصلة

[إضافة استثناءات ل Defender for Endpoint عبر PowerShell](/azure/architecture/example-scenario/wvd/windows-virtual-desktop-fslogix#add-exclusions-for-microsoft-defender-by-using-powershell)
