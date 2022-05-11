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
ms.date: 05/09/2022
ms.openlocfilehash: a472a2183d642ca8c3231e6ca5129fdf79cad8fd
ms.sourcegitcommit: 7dc7e9fd76adf848f941919f86ca25eecc704015
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 05/11/2022
ms.locfileid: "65317615"
---
# <a name="microsoft-defender-for-endpoint-device-control-removable-storage-access-control"></a>التحكم في الوصول إلى التخزين القابل للإزالة Microsoft Defender لنقطة النهاية Device Control

**ينطبق على:**
- [Defender for Endpoint الخطة 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

> [!NOTE]
> تتوفر الآن إدارة نهج المجموعة وإدارة Intune OMA-URI/Custom Policy لهذا المنتج بشكل عام (4.18.2106): راجع [مدونة المجتمع التقني: حماية التخزين والطابعة القابلين للإزالة باستخدام Microsoft Defender لنقطة النهاية](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/protect-your-removable-storage-and-printers-with-microsoft/ba-p/2324806).

يمكنك Microsoft Defender لنقطة النهاية التحكم في الوصول إلى التخزين القابل للإزالة لعنصر تحكم الجهاز من تنفيذ المهمة التالية:

- تدقيق الوصول إلى التخزين القابل للإزالة أو السماح بقراءته أو كتابته أو تنفيذه أو منعه مع الاستبعاد أو بدونه

|امتياز|اذن|
|---|---|
|وصول|قراءة، كتابة، تنفيذ|
|وضع الإجراء|التدقيق، السماح، منع|
|دعم موفر الخدمات المشتركة (CSP)|نعم|
|دعم عنصر نهج المجموعة|نعم|
|الدعم المستند إلى المستخدم|نعم|
|الدعم المستند إلى الجهاز|نعم|

|القدره|الوصف|التوزيع من خلال Intune|التوزيع من خلال نهج المجموعة|
|---|---|---|---|
|إنشاء مجموعة وسائط قابلة للإزالة|يسمح لك بإنشاء مجموعة وسائط قابلة للإزالة قابلة لإعادة الاستخدام|الخطوة 1 في القسم، [نشر النهج عبر OMA-URI](#deploying-policy-via-oma-uri) | الخطوة 1 في القسم، [نشر النهج عبر نهج المجموعة](#deploying-policy-via-group-policy)|
|إنشاء النهج|يسمح لك بإنشاء نهج لفرض كل مجموعة وسائط قابلة للإزالة|الخطوة 2 في القسم، [نشر النهج عبر OMA-URI](#deploying-policy-via-oma-uri) | الخطوان 2 و3 في القسم، [نشر النهج عبر نهج المجموعة](#deploying-policy-via-group-policy) |
|فرض افتراضي|يسمح لك بتعيين الوصول الافتراضي (رفض أو السماح) إلى الوسائط القابلة للإزالة إذا لم يكن هناك نهج|الخطوة 3 في القسم، [نشر النهج عبر OMA-URI](#deploying-policy-via-oma-uri) | الخطوة 4 في القسم، [نشر النهج عبر نهج المجموعة](#deploying-policy-via-group-policy) |
|تمكين التحكم في الوصول إلى التخزين القابل للإزالة أو تعطيله|إذا قمت بتعيين تعطيل، فسيتم تعطيل نهج التحكم في الوصول إلى التخزين القابل للإزالة على هذا الجهاز| الخطوة 4 في القسم، [نشر النهج عبر OMA-URI](#deploying-policy-via-oma-uri) | الخطوة 5 في القسم، [نشر النهج عبر نهج المجموعة](#deploying-policy-via-group-policy) |
|التقاط معلومات الملف|يسمح لك بإنشاء نهج لتسجيل معلومات الملف عند حدوث الوصول للكتابة| الخطوان 2 و5 في القسم، [نشر النهج عبر OMA-URI](#deploying-policy-via-oma-uri) | الخطوة 2 و6 في القسم، [نشر النهج عبر نهج المجموعة](#deploying-policy-via-group-policy) |

## <a name="prepare-your-endpoints"></a>إعداد نقاط النهاية

نشر التحكم في الوصول إلى التخزين القابل للإزالة على أجهزة Windows 10 وأجهزة Windows 11 التي تحتوي على إصدار عميل مكافحة البرامج الضارة **4.18.2103.3 أو إصدار أحدث**.

- **4.18.2104 أو أحدث**: إضافة SerialNumberId، VID_PID، دعم عنصر نهج المجموعة المستند إلى filepath، ComputerSid

- **4.18.2105 أو الإصدارات الأحدث**: إضافة دعم Wildcard ل HardwareId/DeviceId/InstancePathId/FriendlyNameId/SerialNumberId، وهو مزيج من مستخدم معين على جهاز معين، SSD قابل للإزالة (SanDisk Extreme SSD)/دعم SCSI المرفق USB (UAS)

- **4.18.2107 أو إصدار أحدث**: إضافة دعم Windows Portable Device (WPD) (للأجهزة المحمولة، مثل الأجهزة اللوحية)؛ إضافة AccountName إلى [التتبع المتقدم](device-control-removable-storage-access-control.md#view-device-control-removable-storage-access-control-data-in-microsoft-defender-for-endpoint)

:::image type="content" source="images/powershell.png" alt-text="واجهة PowerShell" lightbox="images/powershell.png":::

> [!NOTE]
> لا تحتاج أي من مكونات أمن Windows إلى أن تكون نشطة حيث يمكنك تشغيل التحكم في الوصول إلى التخزين القابل للإزالة بشكل مستقل عن حالة أمن Windows.

## <a name="policy-properties"></a>خصائص النهج

يمكنك استخدام الخصائص التالية لإنشاء مجموعة تخزين قابلة للإزالة:

> [!NOTE]
> يمكن استخدام التعليقات التي تستخدم تدوين `<!-- COMMENT -->` تعليق XML في ملفات Rule وGroup XML، ولكن يجب أن تكون داخل علامة XML الأولى، وليس السطر الأول من ملف XML.

### <a name="removable-storage-group"></a>مجموعة التخزين القابلة للإزالة

|اسم الخاصية|الوصف|خيارات|
|---|---|---|
|**معرف المجموعة**|يمثل GUID، وهو معرف فريد، المجموعة وسيتم استخدامه في النهج كمعرف المجموعة||
|**قائمة واصفة**|سرد خصائص الجهاز التي تريد استخدامها للتغطية في المجموعة. للحصول على كل خاصية من خصائص الجهاز، راجع ["خصائص الجهاز](device-control-removable-storage-protection.md) " للحصول على مزيد من التفاصيل. جميع الخصائص حساسة لحالة الأحرف. |**PrimaryId**: `RemovableMediaDevices`, , `CdRomDevices``WpdDevices`<p>**BusId**: على سبيل المثال، USB وSCSI<p>**معرف الجهاز**<p>**معرف الأجهزة**<p>**InstancePathId**: InstancePathId هي سلسلة تعرف الجهاز في النظام بشكل فريد، على سبيل المثال. `USBSTOR\DISK&VEN_GENERIC&PROD_FLASH_DISK&REV_8.07\8735B611&0` يمثل الرقم الموجود في النهاية (على سبيل المثال &0) المساحة المتوفرة وقد يتغير من جهاز إلى آخر. للحصول على أفضل النتائج، استخدم حرف بدل في النهاية. على سبيل المثال، `USBSTOR\DISK&VEN_GENERIC&PROD_FLASH_DISK&REV_8.07\8735B611*`.<p>**FriendlyNameId**<p>**معرف الرقم التسلسلي**<p>**VID**<p>**PID**<p>**VID_PID**<p>`0751_55E0`: مطابقة زوج VID/PID هذا بالضبط<p>`_55E0`: مطابقة أي وسائط مع PID=55E0 <p>`0751_`: مطابقة أي وسائط مع VID=0751|
|**نوع المطابقة**|عند وجود خصائص جهاز متعددة يتم استخدامها في `DescriptorIDList`، يحدد MatchType العلاقة.|**MatchAll**: ستكون أي سمات ضمن `DescriptorIdList` العلاقة **و** ، على سبيل المثال، إذا وضع `DeviceID` المسؤول و `InstancePathID`، لكل USB متصل، سيتحقق النظام لمعرفة ما إذا كان USB يلبي القيمتين أم لا. <p> **MatchAny**: السمات ضمن DescriptorIdList ستكون **علاقة أو** ؛ على سبيل المثال، إذا وضع `DeviceID` المسؤول و `InstancePathID`، لكل USB متصل، سيقوم النظام بالإنفاذ طالما أن USB يحتوي على قيمة **DeviceID** أو **InstanceID** متطابقة. |

### <a name="access-control-policy"></a>نهج التحكم بالوصول

| اسم الخاصية | الوصف | خيارات |
|---|---|---|
| **معرف PolicyRule** | يمثل GUID، وهو معرف فريد، النهج وسيتم استخدامه في إعداد التقارير واستكشاف الأخطاء وإصلاحها. | |
| **قائمة معرفات مضمنة** | المجموعة (المجموعات) التي سيتم تطبيق النهج عليها. إذا تمت إضافة مجموعات متعددة، فسيتم تطبيق النهج على أي وسائط في كل هذه المجموعات.|يجب استخدام معرف المجموعة/GUID في هذا المثيل. <p> يوضح المثال التالي استخدام GroupID: <p> `<IncludedIdList> <GroupId> {EAA4CCE5-F6C9-4760-8BAD-FDCC76A2ACA1}</GroupId> </IncludedIdList>` |
| **ExcludedIDList** | المجموعة (المجموعات) التي لن يتم تطبيق النهج عليها. | يجب استخدام معرف المجموعة/GUID في هذا المثيل. |
| **معرف الإدخال** | يمكن أن يحتوي One PolicyRule على إدخالات متعددة؛ يخبر كل إدخال مع GUID فريد التحكم في الجهاز بقيد واحد.| |
| **نوع** | تعريف الإجراء لمجموعات التخزين القابلة للإزالة في IncludedIDList. <p>الإنفاذ: السماح أو الرفض <p>التدقيق: AuditAllowed أو AuditDenied<p> | سماح<p>رفض <p>AuditAllowed: تعريف الإعلام والحدث عند السماح بالوصول <p>AuditDenied: تعريف الإعلام والحدث عند رفض الوصول؛ للعمل مع **رفض** الإدخال.<p> عند وجود أنواع تعارض للوسائط نفسها، سيطبق النظام الأول في النهج. مثال على نوع التعارض هو **السماح** **والرفض**. |
| **سيد** | يحدد معرف المستخدم المحلي أو مجموعة Sid للمستخدم أو Sid لكائن AD ما إذا كان يجب تطبيق هذا النهج على مستخدم معين أو مجموعة مستخدمين معينة؛ يمكن أن يحتوي إدخال واحد على حد أقصى من Sid واحد وإدخال دون أي Sid يعني تطبيق النهج على الجهاز. |  |
| **معرف الكمبيوتر** | يحدد Sid للكمبيوتر المحلي أو مجموعة Sid للكمبيوتر أو Sid لكائن AD ما إذا كان يجب تطبيق هذا النهج على جهاز معين أو مجموعة جهاز معين؛ يمكن أن يحتوي إدخال واحد على أجهزة كمبيوتر واحدة كحد أقصى وإدخال بدون أي ComputerSid يعني تطبيق النهج على الجهاز. إذا كنت تريد تطبيق إدخال على مستخدم معين وجهاز معين، فإضافة كل من Sid و ComputerSid في الإدخال نفسه. |  |
| **خيارات** | تحديد ما إذا كان يجب عرض الإعلام أم لا |**عند تحديد "السماح بالنوع"**: <p>0: لا شيء<p>4: تعطيل **AuditAllowed** و **AuditDenied** لهذا الإدخال. حتى إذا حدث **السماح** وتم تكوين AuditAllowed، فلن يرسل النظام الحدث. <p>8: التقاط معلومات الملف والحصول على نسخة من الملف كدليل للوصول إلى الكتابة. <p>16: التقاط معلومات الملف للوصول للكتابة. <p>**عند تحديد رفض النوع**: <p>0: لا شيء<p>4: تعطيل **AuditDenied** لهذا الإدخال. حتى إذا حدث **الحظر** وتم تكوين AuditDenied، فلن يعرض النظام الإعلام. <p>**عند تحديد Type **AuditAllowed****: <p>0: لا شيء <p>1: لا شيء <p>2: إرسال الحدث<p> **عند تحديد Type **AuditDenied****: <p>0: لا شيء <p>1: إظهار الإعلام <p>2: إرسال الحدث<p>3: إظهار الإعلام وإرسال الحدث |
|AccessMask|تعريف الوصول. | **الوصول إلى مستوى القرص**: <p>1: قراءة <p>2: الكتابة <p>4: تنفيذ <p>**الوصول إلى مستوى نظام الملفات**: <p>8: قراءة نظام الملفات <p>16: كتابة نظام الملفات <p>32: تنفيذ نظام الملفات <p><p>يمكنك الحصول على وصول متعدد عن طريق تنفيذ عملية OR الثنائية، على سبيل المثال، سيكون AccessMask للقراءة والكتابة والتنفيذ 7؛ سيكون AccessMask للقراءة والكتابة 3.|

## <a name="common-removable-storage-access-control-scenarios"></a>سيناريوهات التحكم في الوصول إلى التخزين القابلة للإزالة الشائعة

لمساعدتك في التعرف على Microsoft Defender لنقطة النهاية التحكم في الوصول إلى التخزين القابل للإزالة، قمنا بتجميع بعض السيناريوهات الشائعة لمتابعتها.

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

    2. المجموعة 2: USBs غير معتمدة استنادا إلى خصائص الجهاز، على سبيل المثال، معرف المورد / معرف المنتج، اسم مألوف – المجموعة **65fa649a-a111-4912-9294-fb6337a25038** في نموذج ملف [Group.xmlUSBs غير المعتمد](https://github.com/microsoft/mdatp-devicecontrol/tree/main/Removable%20Storage%20Access%20Control%20Samples) .

    > [!TIP]
    > `&amp;` استبدل `&` بالقيمة.

2. إنشاء نهج

    1. النهج 1: حظر الوصول للكتابة والتنفيذ إلى جميع USBs غير المعتمدة باستثناء حظرها. مثال على حالة الاستخدام هذه هو: PolicyRule **23b8e437-66ac-4b32-b3d7-2404637fc98** في نموذج [السيناريو 2 Audit Write and Execute access to all but block specific unapped USBs.xml](https://github.com/microsoft/mdatp-devicecontrol/tree/main/Removable%20Storage%20Access%20Control%20Samples) file.

    2. النهج 2: تدقيق الكتابة وتنفيذ الوصول إلى الآخرين. مثال على حالة الاستخدام هذه هو: PolicyRule **b58ab853-9a6f-405c-a194-740e69422b48** في نموذج [السيناريو 2 Audit Write and Execute access to others.xml](https://github.com/microsoft/mdatp-devicecontrol/tree/main/Removable%20Storage%20Access%20Control%20Samples) file.

## <a name="deploying-and-managing-policy-via-group-policy"></a>نشر النهج وإدارته عبر نهج المجموعة

تمكنك ميزة التحكم في الوصول إلى التخزين القابل للإزالة من تطبيق النهج عبر نهج المجموعة على المستخدم أو الجهاز أو كليهما.

### <a name="licensing"></a>الترخيص

قبل البدء في التحكم في الوصول إلى التخزين القابل للإزالة، يجب عليك تأكيد [اشتراكك في Microsoft 365](https://www.microsoft.com/microsoft-365/compare-microsoft-365-enterprise-plans?rtc=2). للوصول إلى التحكم في الوصول إلى التخزين القابل للإزالة واستخدامه، يجب أن يكون لديك Microsoft 365 E3 أو Microsoft 365 E5.

### <a name="deploying-policy-via-group-policy"></a>نشر النهج عبر نهج المجموعة

1. دمج كافة المجموعات في `<Groups>` `</Groups>` ملف xml واحد.

    توضح الصورة التالية مثال [السيناريو 1: منع الوصول للكتابة والتنفيذ إلى الكل ولكن السماح ب USBs محددة معتمدة](#scenario-1-prevent-write-and-execute-access-to-all-but-allow-specific-approved-usbs).

    :::image type="content" source="images/prevent-write-access-allow-usb.png" alt-text="إعدادات التكوين التي تسمح ب USBs معتمدة معينة على الأجهزة" lightbox="images/prevent-write-access-allow-usb.png":::

2. دمج كافة القواعد في `<PolicyRules>` `</PolicyRules>` ملف xml واحد.

    إذا كنت تريد تقييد مستخدم معين، فاستخدم خاصية SID في الإدخال. إذا لم يكن هناك SID في إدخال النهج، فسيتم تطبيق الإدخال على مثيل تسجيل الدخول للجميع للجهاز.

    إذا كنت تريد مراقبة معلومات الملف للوصول إلى الكتابة، فاستخدم AccessMask الصحيح مع الخيار الصحيح (16)؛ فيما يلي مثال على [معلومات ملف الالتقاط](https://github.com/microsoft/mdatp-devicecontrol/blob/main/Removable%20Storage%20Access%20Control%20Samples/Group%20Policy/Audit%20File%20Information.xml).

    توضح الصورة التالية استخدام خاصية SID، ومثال [للسيناريو 1: منع الكتابة والتنفيذ من الوصول إلى الكل ولكن السماح بوحدات USBs معينة معتمدة](#scenario-1-prevent-write-and-execute-access-to-all-but-allow-specific-approved-usbs).

    :::image type="content" source="images/usage-sid-property.png" alt-text="التعليمات البرمجية التي تشير إلى استخدام سمة خاصية SID" lightbox="images/usage-sid-property.png":::

3. احفظ ملفات XML للقاعدة والمجموعة على مجلد مشاركة الشبكة وضع مسار مجلد مشاركة الشبكة في إعداد نهج المجموعة: **القوالب** \> الإدارية **لتكوين** \> الكمبيوتر **Windows المكونات** \> **برنامج الحماية من الفيروسات من Microsoft Defender** \> **عنصر تحكم الجهاز**: **"تعريف مجموعات نهج التحكم في الجهاز"** و **"تعريف قواعد نهج التحكم في الجهاز".**

   إذا لم تتمكن من العثور على أسلوب عمل تكوين النهج في نهج المجموعة، يمكنك تنزيل ملفات [WindowsDefender.adml](https://github.com/microsoft/mdatp-devicecontrol/blob/main/Removable%20Storage%20Access%20Control%20Samples/WindowsDefender.adml) [وWindowsDefender.admx](https://github.com/microsoft/mdatp-devicecontrol/blob/main/Removable%20Storage%20Access%20Control%20Samples/WindowsDefender.admx) عن طريق تحديد **Raw** ثم **حفظ باسم**.

   - يجب أن يكون الجهاز الهدف قادرا على الوصول إلى مشاركة الشبكة للحصول على النهج. ومع ذلك، بمجرد قراءة النهج، لن يعد اتصال مشاركة الشبكة مطلوبا، حتى بعد إعادة تشغيل الجهاز.

    :::image type="content" source="images/device-control.png" alt-text="شاشة التحكم في الجهاز" lightbox="images/device-control.png":::

4. الإنفاذ الافتراضي: يسمح لك بتعيين الوصول الافتراضي (رفض أو السماح) إلى الوسائط القابلة للإزالة إذا لم يكن هناك نهج. على سبيل المثال، لديك فقط نهج (إما رفض أو السماح) ل RemovableMediaDevices، ولكن ليس لديك أي نهج ل CdRomDevices أو WpdDevices، ويمكنك تعيين رفض افتراضي من خلال هذا النهج، سيتم حظر الوصول للقراءة/الكتابة/التنفيذ إلى CdRomDevices أو WpdDevices.

   - بمجرد نشر هذا الإعداد، سترى **السماح الافتراضي** أو **الرفض الافتراضي**.
   - ضع في اعتبارك كلا من مستوى القرص ومستوى نظام الملفات في AccessMask عند تكوين هذا الإعداد، على سبيل المثال، إذا كنت تريد الرفض الافتراضي ولكن السماح بتخزين معين، يجب السماح بالوصول إلى كل من مستوى القرص ومستوى نظام الملفات، يجب تعيين AccessMask إلى 63.

    :::image type="content" source="images/148609579-a7df650b-7792-4085-b552-500b28a35885.png" alt-text="السماح الافتراضي أو التعليمات البرمجية الافتراضية لرفض PowerShell":::

5. تمكين التحكم في الوصول إلى التخزين القابل للإزالة أو تعطيله: يمكنك تعيين هذه القيمة لتعطيل التحكم في الوصول إلى التخزين القابل للإزالة مؤقتا.

    :::image type="content" source="images/148608318-5cda043d-b996-4146-9642-14fccabcb017.png" alt-text="إعدادات التحكم في الجهاز":::

   - بمجرد نشر هذا الإعداد، سترى **"ممكن"** أو **"معطل**". يعني التعطيل أن هذا الجهاز لا يحتوي على نهج التحكم في الوصول إلى التخزين القابل للإزالة قيد التشغيل.

    :::image type="content" source="images/148609685-4c05f002-5cbe-4aab-9245-83e730c5449e.png" alt-text="تمكين عنصر تحكم الجهاز أو تعطيله في التعليمات البرمجية ل PowerShell":::

6. تعيين موقع لنسخة من الملف: إذا كنت تريد الحصول على نسخة من الملف عند حدوث الوصول للكتابة، يجب تعيين الموقع الذي يمكن للنظام حفظ النسخة فيه.

    انسخ هذا مع AccessMask و Option المناسبين - راجع الخطوة 2 أعلاه.

    :::image type="content" source="../../media/define-device-control-policy-rules.png" alt-text="نهج المجموعة - تعيين locaiton لدليل الملف":::

## <a name="deploying-and-managing-policy-via-intune-oma-uri"></a>نشر النهج وإدارته عبر Intune OMA-URI

تمكنك ميزة التحكم في الوصول إلى التخزين القابل للإزالة من تطبيق النهج عبر OMA-URI على المستخدم أو الجهاز أو كليهما.

### <a name="licensing-requirements"></a>متطلبات الترخيص

قبل البدء في التحكم في الوصول إلى التخزين القابل للإزالة، يجب عليك تأكيد [اشتراكك في Microsoft 365](https://www.microsoft.com/microsoft-365/compare-microsoft-365-enterprise-plans?rtc=2). للوصول إلى التحكم في الوصول إلى التخزين القابل للإزالة واستخدامه، يجب أن يكون لديك Microsoft 365 E3 أو Microsoft 365 E5.

### <a name="permission"></a>اذن

لنشر النهج في Intune، يجب أن يكون للحساب أذونات لإنشاء ملفات تعريف تكوين الجهاز أو تحريرها أو تحديثها أو حذفها. يمكنك إنشاء أدوار مخصصة أو استخدام أي من الأدوار المضمنة باستخدام هذه الأذونات.

- دور إدارة النهج وملفات التعريف

- دور مخصص مع تشغيل أذونات إنشاء/تحرير/تحديث/قراءة/حذف/عرض التقارير لملفات تعريف تكوين الجهاز

- المسؤول العام

### <a name="deploying-policy-via-oma-uri"></a>نشر النهج عبر OMA-URI

إدارة نقاط النهاية من Microsoft ملفات تعريف مركز إدارة الأجهزة (<https://endpoint.microsoft.com/>) \> **إنشاء** \> النظام الأساسي **لملف التعريف** \>  \> **: Windows 10 وأحدث ملف تعريف &: مخصص**

1. لكل مجموعة، قم بإنشاء قاعدة OMA-URI:

    - OMA-URI:

      `./Vendor/MSFT/Defender/Configuration/DeviceControl/PolicyGroups/%7b**GroupGUID**%7d/GroupData`

      على سبيل المثال، بالنسبة **إلى أي تخزين قابل للإزالة ومجموعة CD/DVD** في العينة، يجب أن يكون الارتباط:

      `./Vendor/MSFT/Defender/Configuration/DeviceControl/PolicyGroups/%7b9b28fae8-72f7-4267-a1a5-685f747a7146%7d/GroupData`

    - نوع البيانات: سلسلة (ملف XML)

      :::image type="content" source="images/xml-data-type-string.png" alt-text="الحقل &quot;نوع البيانات&quot; في الصفحة &quot;إضافة صف&quot;" lightbox="images/xml-data-type-string.png":::

2. لكل نهج، قم أيضا بإنشاء OMA-URI:

    - OMA-URI:

      `./Vendor/MSFT/Defender/Configuration/DeviceControl/PolicyRules/%7b**PolicyRuleGUID**%7d/RuleData`

      على سبيل المثال، بالنسبة إلى **حظر الكتابة وتنفيذ الوصول ولكن السماح بقاعدة USBs المعتمدة** في العينة، يجب أن يكون الارتباط:

      `./Vendor/MSFT/Defender/Configuration/DeviceControl/PolicyRules/%7bc544a991-5786-4402-949e-a032cb790d0e%7d/RuleData`

    - نوع البيانات: سلسلة (ملف XML)

    إذا كنت تريد مراقبة معلومات الملف للوصول إلى الكتابة، فاستخدم AccessMask الصحيح مع الخيار الصحيح (16)؛ فيما يلي مثال على [معلومات ملف الالتقاط](https://github.com/microsoft/mdatp-devicecontrol/blob/main/Removable%20Storage%20Access%20Control%20Samples/Intune%20OMA-URI/Audit%20File%20Information.xml).

3. الإنفاذ الافتراضي: يسمح لك بتعيين الوصول الافتراضي (رفض أو السماح) إلى الوسائط القابلة للإزالة إذا لم يكن هناك نهج. على سبيل المثال، لديك فقط نهج (إما رفض أو السماح) ل RemovableMediaDevices، ولكن ليس لديك أي نهج ل CdRomDevices أو WpdDevices، ويمكنك تعيين رفض افتراضي من خلال هذا النهج، سيتم حظر الوصول للقراءة/الكتابة/التنفيذ إلى CdRomDevices أو WpdDevices.

    - OMA-URI: `./Vendor/MSFT/Defender/Configuration/DefaultEnforcement`

    - نوع البيانات: Int

      `DefaultEnforcementAllow = 1`
      `DefaultEnforcementDeny = 2`

    - بمجرد نشر هذا الإعداد، سترى **السماح الافتراضي** أو **الرفض الافتراضي**
    - ضع في اعتبارك كلا من مستوى القرص ومستوى نظام الملفات في AccessMask عند تكوين هذا الإعداد، على سبيل المثال، إذا كنت تريد الرفض الافتراضي ولكن السماح بتخزين معين، يجب السماح بالوصول إلى كل من مستوى القرص ومستوى نظام الملفات، يجب تعيين AccessMask إلى 63.

    :::image type="content" source="images/148609590-c67cfab8-8e2c-49f8-be2b-96444e9dfc2c.png" alt-text="فرض افتراضي يسمح بالتعليمات البرمجية PowerShell":::

4. تمكين التحكم في الوصول إلى التخزين القابل للإزالة أو تعطيله: يمكنك تعيين هذه القيمة لتعطيل التحكم في الوصول إلى التخزين القابل للإزالة مؤقتا.

   - OMA-URI: `./Vendor/MSFT/Defender/Configuration/DeviceControlEnabled`

   - نوع البيانات: Int `Disable: 0`
     `Enable: 1`

   - بمجرد نشر هذا الإعداد، سترى **"ممكن"** أو **"معطل"**

    **معطل** يعني أن هذا الجهاز لا يحتوي على نهج التحكم في الوصول إلى التخزين القابل للإزالة قيد التشغيل

    :::image type="content" source="images/148609770-3e555883-f26f-45ab-9181-3fb1ff7a38ac.png" alt-text="التحكم في الوصول إلى التخزين القابل للإزالة في التعليمات البرمجية ل PowerShell":::

5. قم بتعيين الموقع لنسخة من الملف: إذا كنت تريد الحصول على نسخة من الملف عند حدوث الوصول للكتابة، يجب تعيين الموقع الذي يمكن للنظام حفظ النسخة فيه.

    - OMA-URI: './Vendor/MSFT/Defender/Configuration/DataDuplicationRemoteLocation

    - نوع البيانات: سلسلة

    يجب نشر هذا مع AccessMask الصحيح والخيار الصحيح - راجع الخطوة 2 أعلاه.

    :::image type="content" source="../../media/device-control-oma-uri-edit-row.png" alt-text="تعيين locaiton لدليل الملف":::

## <a name="deploying-and-managing-policy-by-using-intune-user-interface"></a>نشر النهج وإدارته باستخدام واجهة مستخدم Intune

(*قريبا!*) ستتوفر هذه الإمكانية في مركز إدارة إدارة نقاط النهاية من Microsoft (<https://endpoint.microsoft.com/>). انتقل إلى نهج **تقليل الأجزاء** >  في **Endpoint SecurityAttack** > **.** اختر **النظام الأساسي: Windows 10 والإي وقت لاحق** باستخدام **ملف التعريف: التحكم في الجهاز**.

## <a name="view-device-control-removable-storage-access-control-data-in-microsoft-defender-for-endpoint"></a>عرض بيانات التحكم في الوصول إلى التخزين القابلة للإزالة لعنصر تحكم الجهاز في Microsoft Defender لنقطة النهاية

يعرض [مدخل Microsoft 365 Defender](https://security.microsoft.com/advanced-hunting) الأحداث التي تم تشغيلها بواسطة التحكم في الوصول إلى التخزين القابل للإزالة ل Device Control. للوصول إلى أمان Microsoft 365، يجب أن يكون لديك الاشتراك التالي:

- Microsoft 365 لإعداد تقارير E5

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

![الصوره](https://user-images.githubusercontent.com/81826151/159046476-26ea0a21-8087-4f01-b8ae-5aa73b392d8f.png)

### <a name="what-is-the-removable-storage-media-limitation-for-the-maximum-number-of-usbs"></a>ما هو قيود وسائط التخزين القابلة للإزالة للحد الأقصى لعدد USBs؟

لقد تحققنا من صحة مجموعة USB واحدة مع 100,000 وسائط - يصل حجمها إلى 7 ميغابايت. يعمل النهج في كل من Intune وGPO دون مشاكل في الأداء.

### <a name="why-does-the-policy-not-work"></a>لماذا لا يعمل النهج؟

1. السبب الأكثر شيوعا هو عدم وجود [إصدار عميل مكافحة البرامج الضارة](/microsoft-365/security/defender-endpoint/device-control-removable-storage-access-control#prepare-your-endpoints) المطلوب.

2. قد يكون السبب الآخر هو أن ملف XML غير منسق بشكل صحيح، على سبيل المثال، عدم استخدام تنسيق markdown الصحيح للحرف "&" في ملف XML، أو قد يضيف محرر النص علامة ترتيب البايت (BOM) 0xEF 0xBB 0xBF في بداية الملفات، ما يؤدي إلى عدم عمل تحليل XML. أحد الحلول البسيطة هو تنزيل [ملف العينة](https://github.com/microsoft/mdatp-devicecontrol/tree/main/Removable%20Storage%20Access%20Control%20Samples) (حدد **Raw** ثم **حفظ باسم**) ثم قم بالتحديث.

3. إذا كنت تقوم بنشر النهج وإدارته عبر نهج المجموعة، فالرجاء التأكد من دمج كل PolicyRule في ملف XML واحد داخل عقدة أصل تسمى PolicyRules وجميع المجموعات في ملف XML واحد داخل عقدة أصل تسمى Groups؛ إذا كنت تدير من خلال Intune، فاحتفظ بملف XML واحد ل PolicyRule، والشيء نفسه، ملف XML واحد لمجموعة واحدة.

إذا كنت لا تزال لا تعمل، فقد ترغب في الاتصال بنا ومشاركة سيارة الدعم عن طريق تشغيل cmd مع المسؤول: "٪programfiles٪\Windows Defender\MpCmdRun.exe" -GetFiles

### <a name="there-is-no-configuration-ux-for-define-device-control-policy-groups-and-define-device-control-policy-rules-on-my-group-policy"></a>لا توجد تجربة مستخدم تكوين ل "تعريف مجموعات نهج التحكم في الجهاز" و"تعريف قواعد نهج التحكم في الجهاز" على نهج المجموعة

نحن لا نرجع تجربة المستخدم لتكوين نهج المجموعة، ولكن لا يزال بإمكانك الحصول على ملفات adml و admx ذات الصلة بالنقر فوق 'Raw' و'Save as' في ملفات [WindowsDefender.adml](https://github.com/microsoft/mdatp-devicecontrol/blob/main/Removable%20Storage%20Access%20Control%20Samples/WindowsDefender.adml) [وWindDefender.admx](https://github.com/microsoft/mdatp-devicecontrol/blob/main/Removable%20Storage%20Access%20Control%20Samples/WindowsDefender.admx).

### <a name="how-can-i-know-whether-the-latest-policy-has-been-deployed-to-the-target-machine"></a>كيف يمكنني معرفة ما إذا كان قد تم نشر النهج الأخير على الجهاز المستهدف؟

يمكنك تشغيل "Get-MpComputerStatus" على PowerShell كمسؤول. ستظهر القيمة التالية ما إذا كان قد تم تطبيق أحدث نهج على الجهاز الهدف.

:::image type="icon" source="images/148609885-bea388a9-c07d-47ef-b848-999d794d24b8.png" border="false":::

### <a name="how-can-i-know-which-machine-is-using-out-of-date-antimalware-client-version-in-the-organization"></a>كيف يمكنني معرفة الجهاز الذي يستخدم إصدار عميل مكافحة البرامج الضارة قديم في المؤسسة؟

يمكنك استخدام الاستعلام التالي للحصول على إصدار عميل مكافحة البرامج الضارة على مدخل الأمان Microsoft 365:

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
