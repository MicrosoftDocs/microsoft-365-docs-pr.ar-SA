---
title: Microsoft Defender لنقطة النهاية التحكم في الوصول إلى التخزين القابل للإزالة لعنصر تحكم الجهاز، وسائط التخزين القابلة للإزالة
description: إرشادات حول Microsoft Defender لنقطة النهاية
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.custom: admindeeplinkDEFENDER
ms.topic: conceptual
ms.technology: mde
ms.date: 06/24/2022
ms.openlocfilehash: 7b16821f1e4e7b8829615d836bde52dd71a43a96
ms.sourcegitcommit: e4882e3c66166ea7b834ad2e8fafeab42293e07d
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/30/2022
ms.locfileid: "67099360"
---
# <a name="microsoft-defender-for-endpoint-device-control-removable-storage-access-control"></a>التحكم في الوصول إلى التخزين القابل للإزالة Microsoft Defender لنقطة النهاية Device Control

**ينطبق على:**
- [Defender for Endpoint الخطة 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

> [!NOTE]
> تتوفر الآن إدارة نهج المجموعة وإدارة Intune OMA-URI/Custom Policy لهذا المنتج بشكل عام (4.18.2106): راجع [مدونة المجتمع التقني: حماية التخزين والطابعة القابلين للإزالة باستخدام Microsoft Defender لنقطة النهاية](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/protect-your-removable-storage-and-printers-with-microsoft/ba-p/2324806).

## <a name="device-control-removable-storage-access-control-overview"></a>نظرة عامة على التحكم في الوصول إلى التخزين القابل للإزالة لعنصر تحكم الجهاز

Microsoft Defender لنقطة النهاية تتيح لك ميزة التحكم في الوصول إلى التخزين القابل للإزالة للتحكم في الأجهزة إمكانية تدقيق الوصول إلى التخزين القابل للإزالة أو السماح به أو منعه أو قراءته أو كتابته أو تنفيذه مع استثناء أو بدونه.

|امتياز|إذن|
|---|---|
|وصول|قراءة، كتابة، تنفيذ|
|وضع الإجراء|التدقيق، السماح، منع|
|دعم موفر الخدمات المشتركة (CSP)|نعم|
|دعم عنصر نهج المجموعة|نعم|
|الدعم المستند إلى المستخدم|نعم|
|الدعم المستند إلى الجهاز|نعم|

تمنحك ميزة التحكم في الوصول إلى التخزين القابل للإزالة Microsoft Defender لنقطة النهاية Device Control الإمكانات التالية:

|تمكن|الوصف|التوزيع من خلال Intune|التوزيع من خلال نهج المجموعة|
|---|---|---|---|
|إنشاء مجموعة وسائط قابلة للإزالة|يسمح لك بإنشاء مجموعة وسائط قابلة للإزالة قابلة لإعادة الاستخدام|الخطوة 4 و6 في القسم، [نشر التحكم في الوصول إلى التخزين القابل للإزالة باستخدام Intune OMA-URI](#deploying-removable-storage-access-control-by-using-intune-oma-uri)| الخطوة 4 و6 في القسم، [نشر التحكم في الوصول إلى التخزين القابل للإزالة باستخدام نهج المجموعة](#deploying-removable-storage-access-control-by-using-group-policy)|
|إنشاء النهج|يسمح لك بإنشاء نهج لفرض كل مجموعة وسائط قابلة للإزالة|الخطوة 5 و7 في القسم، [نشر التحكم في الوصول إلى التخزين القابل للإزالة باستخدام Intune OMA-URI](#deploying-removable-storage-access-control-by-using-intune-oma-uri)| الخطوان 5 و7 في القسم، [نشر التحكم في الوصول إلى التخزين القابل للإزالة باستخدام نهج المجموعة](#deploying-removable-storage-access-control-by-using-group-policy)|
|فرض افتراضي|يسمح لك بتعيين الوصول الافتراضي (رفض أو السماح) إلى الوسائط القابلة للإزالة إذا لم يكن هناك نهج|الخطوة 2 في القسم، [نشر التحكم في الوصول إلى التخزين القابل للإزالة باستخدام Intune OMA-URI](#deploying-removable-storage-access-control-by-using-intune-oma-uri) | الخطوة 2 في القسم، [نشر التحكم في الوصول إلى التخزين القابل للإزالة باستخدام نهج المجموعة](#deploying-removable-storage-access-control-by-using-group-policy)|
|تمكين التحكم في الوصول إلى التخزين القابل للإزالة أو تعطيله|إذا قمت بتعيين تعطيل، فسيتم تعطيل نهج التحكم في الوصول إلى التخزين القابل للإزالة على هذا الجهاز| الخطوة 1 في القسم، [نشر التحكم في الوصول إلى التخزين القابل للإزالة باستخدام Intune OMA-URI](#deploying-removable-storage-access-control-by-using-intune-oma-uri)| الخطوة 1 في القسم، [نشر التحكم في الوصول إلى التخزين القابل للإزالة باستخدام نهج المجموعة](#deploying-removable-storage-access-control-by-using-group-policy)|
|التقاط معلومات الملف|يسمح لك بإنشاء نهج لتسجيل معلومات الملف عند حدوث الوصول للكتابة|  | الخطوة 10 في القسم، [نشر التحكم في الوصول إلى التخزين القابل للإزالة باستخدام نهج المجموعة](#deploying-removable-storage-access-control-by-using-group-policy) |

### <a name="prepare-your-endpoints"></a>إعداد نقاط النهاية

نشر التحكم في الوصول إلى التخزين القابل للإزالة على أجهزة Windows 10 وأجهزة Windows 11 التي تحتوي على إصدار عميل مكافحة البرامج الضارة **4.18.2103.3 أو إصدار أحدث**.

- **4.18.2104 أو أحدث**: إضافة `SerialNumberId`دعم `VID_PID`عنصر نهج المجموعة المستند إلى filepath و `ComputerSid`

- **4.18.2105 أو الإصدارات الأحدث**: إضافة دعم Wildcard ل `HardwareId/DeviceId/InstancePathId/FriendlyNameId/SerialNumberId`، مزيج من مستخدم معين على جهاز معين، SSD القابل للإزالة (SSD أقصى SanDisk)/دعم SCSI المرفقة USB (UAS)

- **4.18.2107 أو إصدار أحدث**: إضافة دعم Windows Portable Device (WPD) (للأجهزة المحمولة، مثل أجهزة الكمبيوتر اللوحية)؛ إضافة `AccountName` إلى [التتبع المتقدم](device-control-removable-storage-access-control.md#view-device-control-removable-storage-access-control-data-in-microsoft-defender-for-endpoint)

- **4.18.2205 أو أحدث**: قم بتوسيع التطبيق الافتراضي إلى **Printer**. إذا قمت بتعيينه إلى **"رفض**"، فسيتم حظر الطابعة أيضا، لذلك إذا كنت تريد فقط إدارة التخزين، فتأكد من إنشاء نهج مخصص للسماح بالطابعة.

:::image type="content" source="images/powershell.png" alt-text="واجهة PowerShell" lightbox="images/powershell.png":::

> [!NOTE]
> لا تحتاج أي من مكونات أمن Windows إلى أن تكون نشطة حيث يمكنك تشغيل التحكم في الوصول إلى التخزين القابل للإزالة بشكل مستقل عن حالة أمن Windows.

## <a name="device-control-removable-storage-access-control-policies"></a>نهج التحكم في الوصول إلى التخزين القابلة للإزالة لعنصر تحكم الجهاز

يمكنك استخدام الخصائص التالية لإنشاء مجموعة تخزين قابلة للإزالة:

> [!NOTE]
> يمكن استخدام التعليقات التي تستخدم تدوين `<!-- COMMENT -->` تعليق XML في ملفات Rule وGroup XML، ولكن يجب أن تكون داخل علامة XML الأولى، وليس السطر الأول من ملف XML.

### <a name="removable-storage-group"></a>مجموعة التخزين القابلة للإزالة

|اسم الخاصية|الوصف|خيارات|
|---|---|---|
|**معرف المجموعة**|يمثل GUID، وهو معرف فريد، المجموعة وسيتم استخدامه في النهج.||
|**قائمة واصفة**|سرد خصائص الجهاز التي تريد استخدامها للتغطية في المجموعة. للحصول على كل خاصية من خصائص الجهاز، راجع ["خصائص الجهاز](device-control-removable-storage-protection.md) " للحصول على مزيد من التفاصيل. جميع الخصائص حساسة لحالة الأحرف. |**PrimaryId**: `RemovableMediaDevices`, , `CdRomDevices``WpdDevices`<p>**BusId**: على سبيل المثال، USB وSCSI<p>**معرف الجهاز**<p>**معرف الأجهزة**<p>**InstancePathId**: InstancePathId هي سلسلة تعرف الجهاز في النظام بشكل فريد، على سبيل المثال. `USBSTOR\DISK&VEN_GENERIC&PROD_FLASH_DISK&REV_8.07\8735B611&0` يمثل الرقم الموجود في النهاية (على سبيل المثال &0) المساحة المتوفرة وقد يتغير من جهاز إلى آخر. للحصول على أفضل النتائج، استخدم حرف بدل في النهاية. على سبيل المثال، `USBSTOR\DISK&VEN_GENERIC&PROD_FLASH_DISK&REV_8.07\8735B611*`.<p>**FriendlyNameId**<p>**معرف الرقم التسلسلي**<p>**VID**<p>**PID**<p>**VID_PID**<p>`0751_55E0`: مطابقة زوج VID/PID هذا بالضبط<p>`_55E0`: مطابقة أي وسائط مع PID=55E0 <p>`0751_`: مطابقة أي وسائط مع VID=0751|
|**نوع المطابقة**|عند وجود خصائص جهاز متعددة يتم استخدامها في `DescriptorIDList`، يحدد MatchType العلاقة.|**MatchAll**: ستكون أي سمات ضمن `DescriptorIdList` العلاقة **و** ، على سبيل المثال، إذا وضع `DeviceID` المسؤول و `InstancePathID`، لكل USB متصل، سيتحقق النظام لمعرفة ما إذا كان USB يلبي القيمتين أم لا. <p> **MatchAny**: السمات ضمن DescriptorIdList ستكون **علاقة أو** ؛ على سبيل المثال، إذا وضع `DeviceID` المسؤول و `InstancePathID`، لكل USB متصل، سيقوم النظام بالإنفاذ طالما أن USB يحتوي على قيمة **DeviceID** أو **InstanceID** متطابقة.|

### <a name="access-control-policy"></a>نهج التحكم بالوصول
يمكنك استخدام الخصائص التالية لإنشاء نهج التحكم في الوصول:

| اسم الخاصية | الوصف | خيارات |
|---|---|---|
| **معرف PolicyRule** | يمثل GUID، وهو معرف فريد، النهج وسيتم استخدامه في إعداد التقارير واستكشاف الأخطاء وإصلاحها. | |
| **قائمة معرفات مضمنة** | المجموعة (المجموعات) التي سيتم تطبيق النهج عليها. إذا تمت إضافة مجموعات متعددة، فسيتم تطبيق النهج على أي وسائط في كل هذه المجموعات.|يجب استخدام معرف المجموعة/GUID في هذا المثيل. <p> يوضح المثال التالي استخدام GroupID: <p> `<IncludedIdList> <GroupId> {EAA4CCE5-F6C9-4760-8BAD-FDCC76A2ACA1}</GroupId> </IncludedIdList>` |
| **ExcludedIDList** | المجموعة (المجموعات) التي لن يتم تطبيق النهج عليها. | يجب استخدام معرف المجموعة/GUID في هذا المثيل. |
| **معرف الإدخال** | يمكن أن يحتوي One PolicyRule على إدخالات متعددة؛ يخبر كل إدخال مع GUID فريد التحكم في الجهاز بقيد واحد.| |
| **نوع** | تعريف الإجراء لمجموعات التخزين القابلة للإزالة في IncludedIDList. <p>الإنفاذ: السماح أو الرفض <p>التدقيق: AuditAllowed أو AuditDenied<p> | سماح<p>أنكر <p>AuditAllowed: تعريف الإعلام والحدث عند السماح بالوصول <p>AuditDenied: تعريف الإعلام والحدث عند رفض الوصول؛ للعمل مع **رفض** الإدخال.<p> عند وجود أنواع تعارض للوسائط نفسها، سيطبق النظام الأول في النهج. مثال على نوع التعارض هو **السماح** **والرفض**. |
| **Sid** | يحدد معرف المستخدم المحلي أو مجموعة Sid للمستخدم أو Sid لكائن AD ما إذا كان يجب تطبيق هذا النهج على مستخدم معين أو مجموعة مستخدمين معينة؛ يمكن أن يحتوي إدخال واحد على حد أقصى من Sid واحد وإدخال دون أي Sid يعني تطبيق النهج على الجهاز. |  |
| **معرف الكمبيوتر** | يحدد Sid للكمبيوتر المحلي أو مجموعة Sid للكمبيوتر أو Sid لكائن AD ما إذا كان يجب تطبيق هذا النهج على جهاز معين أو مجموعة جهاز معين؛ يمكن أن يحتوي إدخال واحد على أجهزة كمبيوتر واحدة كحد أقصى وإدخال بدون أي ComputerSid يعني تطبيق النهج على الجهاز. إذا كنت تريد تطبيق إدخال على مستخدم معين وجهاز معين، فإضافة كل من Sid و ComputerSid في الإدخال نفسه. |  |
| **خيارات** | تحديد ما إذا كان يجب عرض الإعلام أم لا |**عند تحديد "السماح بالنوع"**: <p>0: لا شيء<p>4: تعطيل **AuditAllowed** و **AuditDenied** لهذا الإدخال. حتى إذا حدث **السماح** وتم تكوين AuditAllowed، فلن يرسل النظام الحدث. <p>8: التقاط معلومات الملف والحصول على نسخة من الملف كدليل للوصول إلى الكتابة. <p>16: التقاط معلومات الملف للوصول للكتابة. <p>**عند تحديد رفض النوع**: <p>0: لا شيء<p>4: تعطيل **AuditDenied** لهذا الإدخال. حتى إذا حدث **الحظر** وتم تكوين AuditDenied، فلن يعرض النظام الإعلام. <p>**عند تحديد Type **AuditAllowed****: <p>0: لا شيء <p>1: لا شيء <p>2: إرسال الحدث<p> **عند تحديد Type **AuditDenied****: <p>0: لا شيء <p>1: إظهار الإعلام <p>2: إرسال الحدث<p>3: إظهار الإعلام وإرسال الحدث |
|AccessMask|تعريف الوصول. | **الوصول إلى مستوى القرص**: <p>1: قراءة <p>2: الكتابة <p>4: تنفيذ <p>**الوصول إلى مستوى نظام الملفات**: <p>8: قراءة نظام الملفات <p>16: كتابة نظام الملفات <p>32: تنفيذ نظام الملفات <p><p>يمكنك الحصول على وصول متعدد عن طريق تنفيذ عملية OR الثنائية، على سبيل المثال، سيكون AccessMask للقراءة والكتابة والتنفيذ 7؛ سيكون AccessMask للقراءة والكتابة 3.|

## <a name="device-control-removable-storage-access-control-scenarios"></a>سيناريوهات التحكم في الوصول إلى التخزين القابلة للإزالة لعنصر تحكم الجهاز

لمساعدتك على الإلمام Microsoft Defender لنقطة النهاية التحكم في الوصول إلى التخزين القابل للإزالة، قمنا بتجميع بعض السيناريوهات الشائعة لمتابعتها.

### <a name="scenario-1-prevent-write-and-execute-access-to-all-but-allow-specific-approved-usbs"></a>السيناريو 1: منع الكتابة والتنفيذ من الوصول إلى الكل ولكن السماح ب USBs محددة تمت الموافقة عليها

1. إنشاء مجموعات

    1. المجموعة 1: أي تخزين قابل للإزالة وقرص مضغوط/DVD. مثال على التخزين القابل للإزالة والقرص المضغوط/DVD هو: Group **9b28fae8-72f7-4267-a1a5-685f747a7146** في عينة [ملف "Any Removable Storage" و CD-DVD Group.xml](https://github.com/microsoft/mdatp-devicecontrol/tree/main/Removable%20Storage%20Access%20Control%20Samples) .

    2. المجموعة 2: USBs المعتمدة استنادا إلى خصائص الجهاز. مثال لحالة الاستخدام هذه هو: معرف المثيل - المجموعة **65fa649a-a111-4912-9294-fb6337a25038** في نموذج [USBs المعتمد Group.xml](https://github.com/microsoft/mdatp-devicecontrol/tree/main/Removable%20Storage%20Access%20Control%20Samples) الملف.

    > [!TIP]
    > `&amp;` استبدل `&` بالقيمة.

2. إنشاء نهج

    1. النهج 1: حظر الكتابة وتنفيذ الوصول ولكن السماح ب USBs المعتمدة. مثال لحالة الاستخدام هذه هو: PolicyRule **c544a991-5786-4402-949e-a032cb790d0e** في نموذج [السيناريو 1 حظر الكتابة وتنفيذ الوصول ولكن السماح بملف USBs.xmlالمعتمد](https://github.com/microsoft/mdatp-devicecontrol/tree/main/Removable%20Storage%20Access%20Control%20Samples) .

    2. النهج 2: تدقيق الكتابة وتنفيذ الوصول إلى USBs المسموح بها. مثال لحالة الاستخدام هذه هو: PolicyRule **36ae1037-a639-4cff-946b-b36c53089a4c** في نموذج [السيناريو 1 التدقيق الكتابة والتنفيذ الوصول إلى ملف USBs.xmlالمعتمد](https://github.com/microsoft/mdatp-devicecontrol/tree/main/Removable%20Storage%20Access%20Control%20Samples) .

### <a name="scenario-2-audit-write-and-execute-access-to-all-but-block-specific-unapproved-usbs"></a>السيناريو 2: تدقيق الكتابة والتنفيذ الوصول إلى جميع USBs المحددة غير المعتمدة باستثناء حظرها

1. إنشاء مجموعات

    1. المجموعة 1: أي تخزين قابل للإزالة وقرص مضغوط/DVD. مثال لحالة الاستخدام هذه هو: Group **9b28fae8-72f7-4267-a1a5-685f747a7146** في عينة [ملف "Any Removable Storage" و"CD-DVD" Group.xml](https://github.com/microsoft/mdatp-devicecontrol/tree/main/Removable%20Storage%20Access%20Control%20Samples) .

    2. المجموعة 2: USBs غير معتمدة استنادا إلى خصائص الجهاز، على سبيل المثال، معرف المورد / معرف المنتج، اسم مألوف - المجموعة **65fa649a-a111-4912-9294-fb6337a25038** في نموذج ملف [Group.xmlUSBs غير المعتمد](https://github.com/microsoft/mdatp-devicecontrol/tree/main/Removable%20Storage%20Access%20Control%20Samples) .

    > [!TIP]
    > `&amp;` استبدل `&` بالقيمة.

2. إنشاء نهج

    1. النهج 1: حظر الوصول للكتابة والتنفيذ إلى جميع USBs غير المعتمدة باستثناء حظرها. مثال على حالة الاستخدام هذه هو: PolicyRule **23b8e437-66ac-4b32-b3d7-2404637fc98** في نموذج [السيناريو 2 Audit Write and Execute access to all but block specific unapped USBs.xml](https://github.com/microsoft/mdatp-devicecontrol/tree/main/Removable%20Storage%20Access%20Control%20Samples) file.

    2. النهج 2: تدقيق الكتابة وتنفيذ الوصول إلى الآخرين. مثال على حالة الاستخدام هذه هو: PolicyRule **b58ab853-9a6f-405c-a194-740e69422b48** في نموذج [السيناريو 2 Audit Write and Execute access to others.xml](https://github.com/microsoft/mdatp-devicecontrol/tree/main/Removable%20Storage%20Access%20Control%20Samples) file.

## <a name="deploying-and-managing-removable-storage-access-control-by-using-intune-oma-uri"></a>نشر التحكم في الوصول إلى التخزين القابل للإزالة وإدارته باستخدام Intune OMA-URI

تمكنك ميزة التحكم في الوصول إلى التخزين القابل للإزالة من تطبيق النهج باستخدام OMA-URI على المستخدم أو الجهاز أو كليهما.

### <a name="licensing-requirements"></a>متطلبات الترخيص

قبل البدء في التحكم في الوصول إلى التخزين القابل للإزالة، يجب عليك تأكيد [اشتراكك في Microsoft 365](https://www.microsoft.com/microsoft-365/compare-microsoft-365-enterprise-plans?rtc=2). للوصول إلى التحكم في الوصول إلى التخزين القابل للإزالة واستخدامه، يجب أن يكون لديك Microsoft 365 E3 أو Microsoft 365 E5.

### <a name="permission"></a>إذن

لنشر النهج في Intune، يجب أن يكون للحساب أذونات لإنشاء ملفات تعريف تكوين الجهاز أو تحريرها أو تحديثها أو حذفها. يمكنك إنشاء أدوار مخصصة أو استخدام أي من الأدوار المضمنة باستخدام هذه الأذونات.

- دور إدارة النهج وملفات التعريف
- دور مخصص مع تشغيل أذونات إنشاء/تحرير/تحديث/قراءة/حذف/عرض التقارير لملفات تعريف تكوين الجهاز
- المسؤول العام

### <a name="deploying-removable-storage-access-control-by-using-intune-oma-uri"></a>نشر التحكم في الوصول إلى التخزين القابل للإزالة باستخدام Intune OMA-URI

لحظر فئة تخزين معينة قابلة للإزالة ولكن السماح بوسائط معينة، يمكنك استخدام 'IncludedIdList مجموعة من خلال PrimaryId و ExcludedIDList مجموعة من خلال DeviceId/HardwareId/etc.'

انتقل إلى مركز إدارة Microsoft إدارة نقاط النهاية (<https://endpoint.microsoft.com/>) **> Devices > إنشاء > النظام الأساسي لملف التعريف: Windows 10 والإيجابيات الأحدث، نوع ملف التعريف: قوالب > مخصص**

1. تمكين التحكم في الجهاز أو تعطيله كما يلي:

   - ضمن **إعدادات تكوين > المخصصة**، انقر فوق **"إضافة**".
   - في الجزء **"إضافة صف** "، أدخل:
     - **الاسم** **كتمكين عنصر تحكم الجهاز**
     - **OMA-URI** ك `./Vendor/MSFT/Defender/Configuration/DeviceControlEnabled`
     - **نوع البيانات** **كعدد صحيح**
     - **القيمة** ك **1**

       `Disable: 0`
       `Enable: 1`

     - انقر فوق **حفظ**.

   :::image type="content" source="images/enable-rsac.png" alt-text="لقطة شاشة لتمكين نهج التحكم في الوصول إلى التخزين القابل للإزالة" lightbox="images/enable-rsac.png":::

2. تعيين الإنفاذ الافتراضي:

   يمكنك تعيين الوصول الافتراضي (رفض أو السماح) لكافة ميزات التحكم في الجهاز (`RemovableMediaDevices`، ، `CdRomDevices`، `WpdDevices``PrinterDevices`).

   على سبيل المثال، لديك إما نهج **رفض** أو **السماح** ل `RemovableMediaDevices`، ولكن ليس لديك نهج ل `CdRomDevices` أو `WpdDevices`. يمكنك تعيين **"الرفض الافتراضي** " من خلال هذا النهج، ثم الوصول للقراءة/الكتابة/التنفيذ إلى `CdRomDevices` أو `WpdDevices` سيتم حظره. إذا كنت تريد إدارة التخزين فقط، فتأكد من إنشاء نهج **السماح** للطابعة؛ وإلا، سيتم تطبيق هذا الإنفاذ الافتراضي على الطابعات أيضا.

   - في الجزء **"إضافة صف** "، أدخل:
     - **الاسم** **كرفض افتراضي**
     - **OMA-URI** ك `./Vendor/MSFT/Defender/Configuration/DefaultEnforcement`
     - **نوع البيانات** **كعدد صحيح**
     - **القيمة** ك **1** أو **2**

       `DefaultEnforcementAllow = 1`
       `DefaultEnforcementDeny = 2`

     - انقر فوق **حفظ**.

   :::image type="content" source="images/default-deny.png" alt-text="Screenshot of setting Default Enforcement as Deny" lightbox="images/default-deny.png":::

3. رفض التدقيق الافتراضي:

   يمكنك إنشاء نهج تدقيق للرفض الافتراضي كما يلي:

   - في الجزء **"إضافة صف** "، أدخل:
     - **الاسم** **كرفض افتراضي للتدقيق**
     - **OMA-URI** ك `./Vendor/MSFT/Defender/Configuration/DeviceControl/PolicyRules/%7bf3520ea7-fd1b-4237-8ebc-96911db44f8e%7d/RuleData`

       :::image type="content" source="images/audit-default-deny-1.png" alt-text="لقطة شاشة لإنشاء نهج الرفض الافتراضي للتدقيق" lightbox="images/audit-default-deny-1.png":::

     - **نوع البيانات** **كسلسلة (ملف XML)**
     - **ملف XML مخصص** كملف **Deny.xmlافتراضي للتدقيق** .

       مسار ملف XML: <https://github.com/microsoft/mdatp-devicecontrol/blob/main/Removable%20Storage%20Access%20Control%20Samples/Intune%20OMA-URI/Audit%20Default%20Deny.xml>

       استخدم بيانات XML التالية لإنشاء نهج التدقيق الخاص بك للرفض الافتراضي:

       :::image type="content" source="images/audit-default-deny-xml-file-1.png" alt-text="لقطة شاشة لملف xml لرفض التدقيق الافتراضي":::

4. ReadOnly - المجموعة:

   يمكنك إنشاء مجموعة تخزين قابلة للإزالة مع وصول ReadOnly كما يلي:

   - في الجزء **"إضافة صف** "، أدخل:
     - **الاسم** **كأي مجموعة تخزين قابلة للإزالة**
     - **OMA-URI** ك `./Vendor/MSFT/Defender/Configuration/DeviceControl/PolicyGroups/%7b9b28fae8-72f7-4267-a1a5-685f747a7146%7d/GroupData`

       :::image type="content" source="images/any-removable-storage-group.png" alt-text="لقطة شاشة لإنشاء أي مجموعة تخزين قابلة للإزالة" lightbox="images/any-removable-storage-group.png":::

     - **نوع البيانات** **كسلسلة (ملف XML)**
       - **XML مخصص** **كأي ملف تخزين قابل للإزالة وقرص DVD وWPD Group.xml**

         مسار ملف XML: <https://github.com/microsoft/mdatp-devicecontrol/blob/main/Removable%20Storage%20Access%20Control%20Samples/Intune%20OMA-URI/Any%20Removable%20Storage%20and%20CD-DVD%20and%20WPD%20Group.xml>

         استخدم بيانات XML التالية لإنشاء "أي تخزين قابل للإزالة وقرص DVD وWPD Group" مع وصول ReadOnly:

         :::image type="content" source="images/read-only-group-xml-file.png" alt-text="لقطة شاشة لملف xml للمجموعة للقراءة فقط":::

5. ReadOnly - النهج:

   يمكنك إنشاء نهج ReadOnly وتطبيقه على مجموعة التخزين القابلة للإزالة ReadOnly للسماح بنشاط القراءة كما يلي:

   - في الجزء **"إضافة صف** "، أدخل:
     - **الاسم** ك **نشاط السماح بالقراءة**
     - **OMA-URI** ك `./Vendor/MSFT/Defender/Configuration/DeviceControl/PolicyRules/%7bf7e75634-7eec-4e67-bec5-5e7750cb9e02%7d/RuleData`

       :::image type="content" source="images/allow-read-activity.png" alt-text="&quot; lightbox= &quot;images/allow-read-activity.png":::

     - **نوع البيانات** **كسلسلة (ملف XML)**
     - ملف **XML مخصص** كملف **السماح Read.xml**

       مسار ملف XML: <https://github.com/microsoft/mdatp-devicecontrol/blob/main/Removable%20Storage%20Access%20Control%20Samples/Intune%20OMA-URI/Allow%20Read.xml>

       استخدم بيانات XML التالية لإنشاء نهج ReadOnly وتطبيقه على مجموعة التخزين القابلة للإزالة ReadOnly:

       :::image type="content" source="images/read-only-policy-xml-file.png" alt-text="لقطة شاشة لملف xml لنهج القراءة فقط":::

6. إنشاء مجموعة للوسائط المسموح بها: يمكنك إنشاء مجموعة الوسائط المسموح بها كما يلي:
   - في الجزء **"إضافة صف** "، أدخل:
     - **الاسم** كمجموعة **USBs المعتمدة**
     - **OMA-URI** ك `./Vendor/MSFT/Defender/Configuration/DeviceControl/PolicyGroups/%7b65fa649a-a111-4912-9294-fb6337a25038%7d/GroupData`

       :::image type="content" source="images/create-group-allowed-medias.png" alt-text="لقطة شاشة لإنشاء مجموعة USBs المعتمدة" lightbox="images/create-group-allowed-medias.png":::

     - **نوع البيانات** **كسلسلة (ملف XML)**
     - **XML مخصص** كملف **Group.xmlUSBs معتمد**

       مسار ملف XML: <https://github.com/microsoft/mdatp-devicecontrol/blob/main/Removable%20Storage%20Access%20Control%20Samples/Intune%20OMA-URI/Approved%20USBs%20Group.xml>

       استخدم بيانات XML التالية لإنشاء مجموعة وسائط مسموح بها:

       :::image type="content" source="images/create-group-allowed-medias-xml-file.png" alt-text="لقطة شاشة لإنشاء مجموعة لملف xml للوسائط المسموح بها":::

7. إنشاء نهج للسماح لمجموعة USB المعتمدة: يمكنك إنشاء نهج للسماح لمجموعة USB المعتمدة كما يلي:
   - في الجزء **"إضافة صف** "، أدخل:
     - **الاسم** **كلسماح بالوصول ومعلومات ملف التدقيق**
     - **OMA-URI** ك `./Vendor/MSFT/Defender/Configuration/DeviceControl/PolicyRules/%7bb2061588-029e-427d-8404-6dfec096a571%7d/RuleData`

       :::image type="content" source="images/allow-access-audit-file-information-1.png" alt-text="لقطة شاشة للسماح بالوصول ومعلومات ملف التدقيق" lightbox= "images/allow-access-audit-file-information-1.png":::

     - **نوع البيانات** **كسلسلة (ملف XML)**
     - **ملف XML مخصص** **كلسماح بالوصول الكامل والتدقيق file.xml**

       مسار ملف XML: <https://github.com/microsoft/mdatp-devicecontrol/blob/main/Removable%20Storage%20Access%20Control%20Samples/Intune%20OMA-URI/Allow%20full%20access%20and%20audit%20file.xml>

       استخدم بيانات XML التالية لإنشاء نهج للسماح لمجموعة USB المعتمدة:

       :::image type="content" source="images/create-policy-allow-approved-usb-group-xml-intune.png" alt-text="لقطة شاشة لإنشاء نهج للسماح بملف XML لمجموعة USB المعتمد":::

       ماذا يعني '47' في النهج؟ إنه 9 + 2 + 36 = 47:

       - الوصول للقراءة: 1 + 8 = 9.
       - الوصول للكتابة: مستوى القرص 2.
       - التنفيذ: 4 + 32 = 36.

## <a name="deploying-and-managing-policy-by-using-intune-user-interface"></a>نشر النهج وإدارته باستخدام واجهة مستخدم Intune

تتوفر هذه الإمكانية في مركز إدارة Microsoft إدارة نقاط النهاية (<https://endpoint.microsoft.com/>). انتقل إلى نهج **إنشاء** **تقليل** >  الأجزاء المعرضة للهجوم **الأمني** >  لنقطة النهاية. اختر **النظام الأساسي: Windows 10 والإي وقت لاحق** باستخدام **ملف التعريف: التحكم في الجهاز**.

## <a name="deploying-and-managing-removable-storage-access-control-by-using-group-policy"></a>نشر التحكم في الوصول إلى التخزين القابل للإزالة وإدارته باستخدام نهج المجموعة

تمكنك ميزة التحكم في الوصول إلى التخزين القابل للإزالة من تطبيق نهج باستخدام نهج المجموعة على المستخدم أو الجهاز أو كليهما.

### <a name="licensing"></a>الترخيص

قبل البدء في التحكم في الوصول إلى التخزين القابل للإزالة، يجب عليك تأكيد [اشتراكك في Microsoft 365](https://www.microsoft.com/microsoft-365/compare-microsoft-365-enterprise-plans?rtc=2). للوصول إلى التحكم في الوصول إلى التخزين القابل للإزالة واستخدامه، يجب أن يكون لديك Microsoft 365 E3 أو Microsoft 365 E5.

### <a name="deploying-removable-storage-access-control-by-using-group-policy"></a>نشر التحكم في الوصول إلى التخزين القابل للإزالة باستخدام نهج المجموعة

1. تمكين التحكم في الوصول إلى التخزين القابل للإزالة أو تعطيله:

   يمكنك تمكين التحكم في الجهاز كما يلي:

   - انتقل إلى **تكوين الكمبيوتر > القوالب الإدارية > مكونات Windows > ميزات > برنامج الحماية من الفيروسات من Microsoft Defender > التحكم في الجهاز**
   - في نافذة **"التحكم بالجهاز** "، حدد **"ممكن**".

   :::image type="content" source="images/enable-rsac-gp.png" alt-text="لقطة شاشة لتمكين RSAC باستخدام نهج المجموعة " lightbox="images/enable-rsac-gp.png":::

> [!NOTE]
> إذا لم تتمكن من رؤية عناصر نهج المجموعة هذه، فستحتاج إلى إضافة قالب إداري لنهج المجموعة. يمكنك تنزيل القالب الإداري (WindowsDefender.adml وWindowsDefender.admx) من https://github.com/microsoft/mdatp-devicecontrol/tree/main/Removable%20Storage%20Access%20Control%20Samples.

2. تعيين الإنفاذ الافتراضي:

   يمكنك تعيين الوصول الافتراضي (رفض أو السماح) لكافة ميزات التحكم في الجهاز (RemovableMediaDevices، وDdRomDevices، وWpdDevices، و PrinterDevices).

   على سبيل المثال، لديك إما نهج الرفض أو السماح ل RemovableMediaDevices، ولكن ليس لديك أي نهج ل CdRomDevices أو WpdDevices. يمكنك تعيين الرفض الافتراضي من خلال هذا النهج، ثم سيتم حظر الوصول للقراءة/الكتابة/التنفيذ إلى CdRomDevices أو WpdDevices. إذا كنت تريد فقط إدارة التخزين، فتأكد من إنشاء نهج السماح للطابعة، وإلا، فسيتم تطبيق "الإنفاذ الافتراضي" هذا على الطابعة أيضا.

   - انتقل إلى **تكوين الكمبيوتر > القوالب الإدارية > مكونات Windows > ميزات > برنامج الحماية من الفيروسات من Microsoft Defender > التحكم بالجهاز > تحديد الإنفاذ الافتراضي للتحكم في الجهاز**

   - في نافذة **«Select Device Control Default Enforcement»** ، حدد **«Default Deny»**:

   :::image type="content" source="images/set-default-enforcement-deny-gp.png" alt-text="لقطة شاشة لإعداد «Default Enforcement = Deny» باستخدام نهج المجموعة" lightbox="images/set-default-enforcement-deny-gp.png":::

3. رفض التدقيق الافتراضي:

   استخدم بيانات XML التالية لإنشاء نهج التدقيق للرفض الافتراضي:

   :::image type="content" source="images/audit-default-deny-gp.png" alt-text="Screenshot of audit default deny xml data":::

4. ReadOnly - المجموعة:

   استخدم بيانات XML التالية لإنشاء مجموعة تخزين قابلة للإزالة باستخدام الوصول إلى ReadOnly:

   :::image type="content" source="images/read-only-group-gp.png" alt-text="لقطة شاشة لبيانات xml لمجموعة التخزين القابلة للإزالة للقراءة فقط":::

5. ReadOnly - النهج:

   استخدم بيانات XML التالية لإنشاء نهج ReadOnly وتطبيقه على مجموعة التخزين القابلة للإزالة ReadOnly للسماح بنشاط القراءة:

    :::image type="content" source="images/read-only-policy-gp.png" alt-text="لقطة شاشة لبيانات xml للنهج للقراءة فقط" lightbox="images/read-only-policy-gp.png":::

6. إنشاء مجموعة للوسائط المسموح بها:

   استخدم بيانات XML التالية لإنشاء مجموعة وسائط مسموح بها للتخزين القابل للإزالة:

   :::image type="content" source="images/create-group-allowed-medias-gp.png" alt-text="لقطة شاشة لبيانات xml لإنشاء مجموعة للوسائط المسموح بها" lightbox="images/create-group-allowed-medias-gp.png":::

7. إنشاء نهج للسماح لمجموعة USB المعتمدة:

   استخدم بيانات XML التالية لإنشاء نهج للسماح بمجموعة USB المعتمدة:

   :::image type="content" source="images/create-policy-allow-approved-usb-group-xml.png" alt-text="لقطة شاشة لبيانات XML لإنشاء نهج للسماح لمجموعة USB المعتمدة باستخدام نهج المجموعة" lightbox="images/create-policy-allow-approved-usb-group-xml.png":::

   ماذا يعني '47' في النهج؟ إنه 9 + 2 + 36 = 47:

   - الوصول للقراءة: 1+8 = 9.
   - الوصول للكتابة: مستوى القرص 2.
   - التنفيذ: 4 + 32 = 36.

8. دمج المجموعات في ملف XML واحد:

   يمكنك دمج مجموعات نهج التحكم في الجهاز في ملف XML واحد كما يلي:

   - انتقل إلى **القوالب** \> الإدارية **لتكوين** \> الكمبيوتر في **مكونات Windows Components** \> **Microsoft Defender Antivirus** \> **Device Control** \> **، وحدد مجموعات نهج التحكم في الجهاز**.

    :::image type="content" source="images/define-device-control-policy-grps-gp.png" alt-text="لقطة شاشة لتعريف مجموعات نهج التحكم في الجهاز" lightbox="images/define-device-control-policy-grps-gp.png":::

   - في نافذة **تعريف مجموعات نهج التحكم في الجهاز** ، أدخل مسار الملف الذي يحتوي على بيانات مجموعات XML.

     مسار ملف XML: <https://github.com/microsoft/mdatp-devicecontrol/blob/main/Removable%20Storage%20Access%20Control%20Samples/Group%20Policy/Demo_Groups.xml>

     فيما يلي مخطط xml لمجموعات نهج التحكم في الجهاز:

     :::image type="content" source="images/combine-grps-xml-file-gp.png" alt-text="لقطة شاشة لدمج المجموعات في ملف XML واحد":::

9. دمج النهج في ملف XML واحد:

   يمكنك دمج قواعد نهج التحكم في الجهاز في ملف XML واحد كما يلي:

   - انتقل إلى **تكوين الكمبيوتر > القوالب الإدارية > مكونات Windows > Microsoft Defender Antivirus > التحكم في الأجهزة > تحديد قواعد نهج التحكم في الجهاز**

     :::image type="content" source="images/define-device-cntrl-policy-rules-gp.png" alt-text="لقطة شاشة لتحديد قواعد نهج التحكم في الجهاز" lightbox="images/define-device-cntrl-policy-rules-gp.png":::

   - في نافذة **تحديد قواعد نهج التحكم في الجهاز** ، حدد **Enabled**، وأدخل مسار الملف الذي يحتوي على بيانات قواعد XML.

     مسار ملف XML: <https://github.com/microsoft/mdatp-devicecontrol/blob/main/Removable%20Storage%20Access%20Control%20Samples/Group%20Policy/Demo_Policies.xml>

     فيما يلي مخطط xml لقواعد نهج التحكم في الجهاز:

    :::image type="content" source="images/combine-policies-xml-gp.png" alt-text="لقطة شاشة لدمج النهج في ملف XML واحد":::

10. تعيين موقع لنسخة من الملف (دليل):

    إذا كنت تريد الحصول على نسخة من الملف (دليل) عند حدوث الوصول للكتابة، يجب عليك تعيين الموقع الذي يمكن للنظام حفظ النسخة فيه.

    - انتقل إلى **تكوين الكمبيوتر > القوالب الإدارية > Windows Components > Microsoft Defender Antivirus > Device Control > تحديد موقع بيانات دليل التحكم في الأجهزة عن بعد**.

    - في نافذة **تحديد موقع بيانات دليل التحكم في الأجهزة عن بعد** ، حدد **«Enabled»** وأدخل مسار مجلد مشاركة الشبكة أو المحلي.

      :::image type="content" source="images/evidence-data-remote-location-gp.png" alt-text="لقطة شاشة لتحديد موقع بيانات دليل التحكم في الأجهزة عن بعد" lightbox="images/evidence-data-remote-location-gp.png":::

## <a name="view-device-control-removable-storage-access-control-data-in-microsoft-defender-for-endpoint"></a>عرض بيانات التحكم في الوصول إلى التخزين القابلة للإزالة لعنصر تحكم الجهاز في Microsoft Defender لنقطة النهاية

يعرض [مدخل Microsoft 365 Defender](https://security.microsoft.com/advanced-hunting) الأحداث التي تم تشغيلها بواسطة التحكم في الوصول إلى التخزين القابل للإزالة ل Device Control. للوصول إلى أمان Microsoft 365، يجب أن يكون لديك الاشتراك التالي:

- تقارير Microsoft 365 for E5

```kusto
//RemovableStoragePolicyTriggered: event triggered by Disk level enforcement
DeviceEvents
| where ActionType == "RemovableStoragePolicyTriggered"
| extend parsed=parse_json(AdditionalFields)
| extend RemovableStorageAccess = tostring(parsed.RemovableStorageAccess)
| extend RemovableStoragePolicyVerdict = tostring(parsed.RemovableStoragePolicyVerdict)
| extend MediaBusType = tostring(parsed.BusType)
| extend MediaClassGuid = tostring(parsed.ClassGuid)
| extend MediaClassName = tostring(parsed.ClassName)
| extend MediaDeviceId = tostring(parsed.DeviceId)
| extend MediaInstanceId = tostring(parsed.DeviceInstanceId)
| extend MediaName = tostring(parsed.MediaName)
| extend RemovableStoragePolicy = tostring(parsed.RemovableStoragePolicy)
| extend MediaProductId = tostring(parsed.ProductId)
| extend MediaVendorId = tostring(parsed.VendorId)
| extend MediaSerialNumber = tostring(parsed.SerialNumber)
|project Timestamp, DeviceId, DeviceName, InitiatingProcessAccountName, ActionType, RemovableStorageAccess, RemovableStoragePolicyVerdict, MediaBusType, MediaClassGuid, MediaClassName, MediaDeviceId, MediaInstanceId, MediaName, RemovableStoragePolicy, MediaProductId, MediaVendorId, MediaSerialNumber
| order by Timestamp desc
```

```kusto
//information of file written to removable storage
DeviceEvents
| where ActionType contains "RemovableStorageFileEvent"
| extend parsed=parse_json(AdditionalFields)
| extend Policy = tostring(parsed.Policy)
| extend PolicyRuleId = tostring(parsed.PolicyRuleId)
| extend MediaClassName = tostring(parsed.ClassName)
| extend MediaInstanceId = tostring(parsed.InstanceId)
| extend MediaName = tostring(parsed.MediaName)
| extend MediaProductId = tostring(parsed.ProductId)
| extend MediaVendorId = tostring(parsed.VendorId)
| extend MediaSerialNumber = tostring(parsed.SerialNumber)
| extend FileInformationOperation = tostring(parsed.DuplicatedOperation)
| extend FileEvidenceLocation = tostring(parsed.TargetFileLocation)
| project Timestamp, DeviceId, DeviceName, InitiatingProcessAccountName, ActionType, Policy, PolicyRuleId, FileInformationOperation, MediaClassName, MediaInstanceId, MediaName, MediaProductId, MediaVendorId, MediaSerialNumber, FileName, FolderPath, FileSize, FileEvidenceLocation, AdditionalFields
| order by Timestamp desc
```

:::image type="content" source="images/block-removable-storage.png" alt-text="الشاشة تصور حجب التخزين القابل للإزالة.":::

## <a name="frequently-asked-questions"></a>الأسئلة الشائعة

### <a name="how-to-generate-guid-for-group-idpolicyrule-identry-id"></a>كيفية إنشاء معرف GUID لمعرف المجموعة/معرف PolicyRule/معرف الإدخال؟

يمكنك إنشاء GUID من خلال مصدر مفتوح عبر الإنترنت، أو من خلال PowerShell - [كيفية إنشاء GUID من خلال PowerShell](/powershell/module/microsoft.powershell.utility/new-guid)

![صورة](https://user-images.githubusercontent.com/81826151/159046476-26ea0a21-8087-4f01-b8ae-5aa73b392d8f.png)

### <a name="what-are-the-removable-storage-media-and-policy-limitations"></a>ما هي وسائط التخزين القابلة للإزالة وقيود النهج؟

إما من مركز إدارة Microsoft إدارة نقاط النهاية (Intune) أو من خلال Microsoft Graph API، يتم إجراء الاستدعاء الخلفي من خلال OMA-URI (GET للقراءة أو PATCH للتحديث) وبالتالي فإن القيد هو نفسه أي ملف تعريف تكوين مخصص ل OMA-URI في Microsoft وهو رسميا 350000 حرف لملفات XML.

على سبيل المثال، إذا كنت بحاجة إلى كتلتين من الإدخالات لكل معرف أمان مستخدم ل "السماح"/"التدقيق مسموح به" لمستخدمين محددين وكتلتين من الإدخالات في نهاية "رفض" الكل، فستتمكن من إدارة 2276 مستخدما.

### <a name="why-does-the-policy-not-work"></a>لماذا لا يعمل النهج؟

1. السبب الأكثر شيوعا هو عدم وجود [إصدار عميل مكافحة البرامج الضارة](/microsoft-365/security/defender-endpoint/device-control-removable-storage-access-control#prepare-your-endpoints) المطلوب.

2. قد يكون السبب الآخر هو أن ملف XML غير منسق بشكل صحيح، على سبيل المثال، عدم استخدام تنسيق markdown الصحيح للحرف "&" في ملف XML، أو قد يضيف محرر النص علامة ترتيب البايت (BOM) 0xEF 0xBB 0xBF في بداية الملفات، ما يؤدي إلى عدم عمل تحليل XML. أحد الحلول البسيطة هو تنزيل [ملف العينة](https://github.com/microsoft/mdatp-devicecontrol/tree/main/Removable%20Storage%20Access%20Control%20Samples) (حدد **Raw** ثم **حفظ باسم**) ثم قم بالتحديث.

3. إذا كنت تقوم بنشر النهج وإدارته باستخدام نهج المجموعة، فالرجاء التأكد من دمج كل PolicyRule في ملف XML واحد داخل عقدة أصل تسمى PolicyRules وكل المجموعة في ملف XML واحد داخل عقدة أصل تسمى Groups؛ إذا كنت تدير من خلال Intune، فاحتفظ بملف XML واحد من PolicyRule، والشيء نفسه، ملف XML واحد لمجموعة واحدة.

إذا كان لا يزال لا يعمل، فقد ترغب في الاتصال بنا ومشاركة سيارة أجرة الدعم عن طريق تشغيل cmd مع المسؤول: "٪programfiles٪\Windows Defender\MpCmdRun.exe" -GetFiles

### <a name="there-is-no-configuration-ux-for-define-device-control-policy-groups-and-define-device-control-policy-rules-on-my-group-policy"></a>لا توجد تجربة مستخدم تكوين ل "تعريف مجموعات نهج التحكم في الجهاز" و"تعريف قواعد نهج التحكم في الجهاز" على نهج المجموعة

نحن لا نرجع تجربة المستخدم لتكوين نهج المجموعة، ولكن لا يزال بإمكانك الحصول على ملفات adml و admx ذات الصلة بالنقر فوق 'Raw' و'Save as' في ملفات [WindowsDefender.adml](https://github.com/microsoft/mdatp-devicecontrol/blob/main/Removable%20Storage%20Access%20Control%20Samples/WindowsDefender.adml) [وWindDefender.admx](https://github.com/microsoft/mdatp-devicecontrol/blob/main/Removable%20Storage%20Access%20Control%20Samples/WindowsDefender.admx).

### <a name="how-can-i-know-whether-the-latest-policy-has-been-deployed-to-the-target-machine"></a>كيف يمكنني معرفة ما إذا كان قد تم نشر النهج الأخير على الجهاز المستهدف؟

يمكنك تشغيل "Get-MpComputerStatus" على PowerShell كمسؤول. ستظهر القيمة التالية ما إذا كان قد تم تطبيق أحدث نهج على الجهاز الهدف.

:::image type="icon" source="images/148609885-bea388a9-c07d-47ef-b848-999d794d24b8.png" border="false":::

### <a name="how-can-i-know-which-machine-is-using-out-of-date-antimalware-client-version-in-the-organization"></a>كيف يمكنني معرفة الجهاز الذي يستخدم إصدار عميل مكافحة البرامج الضارة قديم في المؤسسة؟

يمكنك استخدام الاستعلام التالي للحصول على إصدار عميل مكافحة البرامج الضارة على مدخل أمان Microsoft 365:

```kusto
//check the antimalware client version
DeviceFileEvents
|where FileName == "MsMpEng.exe"
|where FolderPath contains @"C:\ProgramData\Microsoft\Windows Defender\Platform\"
|extend PlatformVersion=tostring(split(FolderPath, "\\", 5))
//|project DeviceName, PlatformVersion // check which machine is using legacy platformVersion
|summarize dcount(DeviceName) by PlatformVersion // check how many machines are using which platformVersion
|order by PlatformVersion desc
```
