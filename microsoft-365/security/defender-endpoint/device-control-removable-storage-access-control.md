---
title: Microsoft Defender للتحكم في الوصول إلى التخزين القابل للإزالة لجهاز نقطة النهاية، وسائط التخزين القابلة للإزالة
description: معلومات حول Microsoft Defender لنقطة النهاية
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
ms.date: 03/09/2022
ms.openlocfilehash: f696cd3631573bdb2206c665340f35601e4624ac
ms.sourcegitcommit: 9af389e4787383cd97bc807f7799ef6ecf0664d0
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/14/2022
ms.locfileid: "63583273"
---
# <a name="microsoft-defender-for-endpoint-device-control-removable-storage-access-control"></a>عنصر تحكم الوصول إلى التخزين القابل للإزالة من Microsoft Defender للتحكم في جهاز نقطة النهاية

**ينطبق على:**
- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

> [!NOTE]
> تتوفر الآن إدارة نهج المجموعة وإدارة نهج Intune OMA-URI/Custom Policy لهذا المنتج بشكل عام (4.18.2106): راجع مدونة المجتمع التقني: حماية السعة التخزينية والطابعة القابلة للإزالة باستخدام [Microsoft Defender ل Endpoint](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/protect-your-removable-storage-and-printers-with-microsoft/ba-p/2324806).


يمكنك Microsoft Defender للتحكم في الوصول إلى التخزين القابل للإزالة من Microsoft Defender للتحكم في جهاز نقطة النهاية من القيام ب المهمة التالية:

- التدقيق والسماح بالوصول للقراءة أو الكتابة أو التنفيذ إلى مساحة تخزين قابلة للإزالة مع استثناء أو بدونه أو منعه

|الامتياز|الإذن|
|---|---|
|وصول|القراءة والكتابة والتنفيذ|
|وضع الإجراء|التدقيق، السماح، منع|
|دعم CSP|نعم|
|دعم GPO|نعم|
|الدعم المستند إلى المستخدم|نعم|
|دعم يستند إلى جهاز|نعم|

|الإمكانية|الوصف|النشر من خلال Intune|النشر من خلال نهج المجموعة|
|---|---|---|---|
|إنشاء مجموعة وسائط قابلة للإزالة|يسمح لك بإنشاء مجموعة وسائط قابلة لإعادة الإزالة|الخطوة 1 والخطوة 3 في المقطع، [نهج النشر عبر OMA-URI](#deploying-policy-via-oma-uri) | الخطوة 1 في المقطع، [نهج النشر عبر نهج المجموعة](#deploying-policy-via-group-policy)|
|إنشاء النهج|يسمح لك بإنشاء نهج لفرض كل مجموعة وسائط قابلة للإزالة|الخطوات 2 و3 في المقطع، [نهج النشر عبر OMA-URI](#deploying-policy-via-oma-uri) | الخطوة 2 في المقطع، [نهج النشر عبر نهج المجموعة](#deploying-policy-via-group-policy) |
|التنفيذ الافتراضي|يسمح لك بتعيين الوصول الافتراضي (رفض أو السماح) إلى وسائط قابلة للإزالة إذا لم يكن هناك نهج|الخطوة 4 في المقطع، [نهج النشر عبر OMA-URI](#deploying-policy-via-oma-uri) | الخطوة 3 في المقطع، [نهج النشر عبر نهج المجموعة](#deploying-policy-via-group-policy) |
|تمكين عنصر تحكم الوصول إلى التخزين القابل للإزالة أو تعطيله|إذا قمت بتعيين تعطيل، سيتم تعطيل نهج التحكم بالوصول إلى التخزين القابل للإزالة على هذا الجهاز| الخطوة 5 في المقطع، [نهج النشر عبر OMA-URI](#deploying-policy-via-oma-uri) | الخطوة 4 في المقطع، [نهج النشر عبر نهج المجموعة](#deploying-policy-via-group-policy) |
|التقاط معلومات الملف|يسمح لك بإنشاء نهج لالتقاط معلومات الملف عند حدوث وصول للكتابة| الخطوة 2 و6 في المقطع، [نهج النشر عبر OMA-URI](#deploying-policy-via-oma-uri) | الخطوة 2 و5 في المقطع، [نهج النشر عبر نهج المجموعة](#deploying-policy-via-group-policy) |

## <a name="prepare-your-endpoints"></a>تحضير نقاط النهاية

نشر التحكم بالوصول إلى التخزين القابل للإزالة Windows 10 على Windows 11 الأجهزة التي لديها إصدار عميل مكافحة البرامج الضارة **4.18.2103.3** أو إصدار أحدث.

- **4.18.2104 أو** أي وقت لاحق: إضافة SerialNumberId، VID_PID، دعم GPO المستند إلى filepath، ComputerSid

- **4.18.2105 أو** أي وقت لاحق: إضافة دعم أحرف البدل ل HardwareId/DeviceId/InstancePathId/FriendlyNameId/SerialNumberId، وهو مزيج من مستخدم معين على جهاز معين، SSD قابل للإزالة (دعم SanDisk Extreme SSD)/USB المرفق SCSI (UAS)

- **4.18.2107 أو** إصدار لاحق: إضافة دعم Windows Portable Device (WPD) (للأجهزة المحمولة، مثل الأجهزة اللوحية)، إضافة AccountName إلى [أدوات البحث المتقدمة](device-control-removable-storage-access-control.md#view-device-control-removable-storage-access-control-data-in-microsoft-defender-for-endpoint)

- **4.18.2111** أو إصدار أحدث: إضافة "تمكين التحكم بالوصول إلى التخزين القابل للإزالة أو تعطيله"، "التنفيذ الافتراضي"، وقت تحديث نهج جهاز العميل عبر PowerShell، معلومات الملف

- **4.18.2201 أو** أي وقت لاحق: دعم نسخة من ملف مكتوب للتخزين المسموح به من خلال OMA-URI

:::image type="content" source="images/powershell.png" alt-text="واجهة PowerShell.":::

> [!NOTE]
> لا يحتاج أمن Windows أي من مكونات التخزين إلى أن يكون نشطا حيث يمكنك تشغيل "التحكم بالوصول إلى التخزين القابل للإزالة" بشكل مستقل أمن Windows التخزين.

## <a name="policy-properties"></a>خصائص النهج

يمكنك استخدام الخصائص التالية لإنشاء مجموعة تخزين قابلة للإزالة:

> [!NOTE]
> يمكن استخدام التعليقات التي تستخدم علامة تعليق XML `<!-- COMMENT -->` في ملفات القاعدة وXML للمجموعة، ولكن يجب أن تكون داخل علامة XML الأولى، وليس السطر الأول من ملف XML.

### <a name="removable-storage-group"></a>مجموعة التخزين القابلة للإزالة

|اسم الخاصية|الوصف|خيارات|
|---|---|---|
|**GroupId**|يمثل GUID، وهو الم ID فريد، المجموعة وسيستخدم في النهج.||
|**DescriptorIdList**|سرد خصائص الجهاز التي تريد استخدامها لتغطية المجموعة. للحصول على مزيد من التفاصيل، راجع [خصائص الجهاز](device-control-removable-storage-protection.md) لكل خاصية جهاز. كل الخصائص حساسة لالحالتين. |**PrimaryId**: `RemovableMediaDevices`، ، `CdRomDevices``WpdDevices`<p>**BusId**: على سبيل المثال، USB و SCSI<p>**DeviceId**<p>**HardwareId**<p>**InstancePathId**: InstancePathId هي سلسلة تعرف الجهاز في النظام بشكل فريد، على سبيل المثال، `USBSTOR\DISK&VEN_GENERIC&PROD_FLASH_DISK&REV_8.07\8735B611&0`. يمثل الرقم في النهاية (على سبيل &0) الفتحة المتوفرة وقد يتغير من جهاز إلى آخر. للحصول على أفضل النتائج، استخدم أحرف البدل في النهاية. على سبيل المثال، `USBSTOR\DISK&VEN_GENERIC&PROD_FLASH_DISK&REV_8.07\8735B611*`.<p>**FriendlyNameId**<p>**SerialNumberId**<p>**VID**<p>**PID**<p>**VID_PID**<p>`0751_55E0`: مطابقة هذا الزوج المحدد VID/PID<p>`_55E0`: مطابقة أي وسائط مع PID=55E0 <p>`0751_`: مطابقة أي وسائط باستخدام VID=0751|
|**MatchType**|عند وجود خصائص جهاز متعددة يتم استخدامها في `DescriptorIDList`، يحدد MatchType العلاقة.|**MatchAll**: أي سمات ضمن `DescriptorIdList` ستكون علاقة و؛  `DeviceID` `InstancePathID`على سبيل المثال، إذا وضع المسؤول و ، لكل USB متصل، سيتحقق النظام لمعرفة ما إذا كان USB يلبي القيمتين. <p> **MatchAny**: تكون السمات ضمن DescriptorIdList علاقة **أو** ؛ على سبيل المثال `DeviceID` `InstancePathID`، إذا وضع المسؤول و ، لكل USB متصل، سينفذ النظام التنفيذ طالما أن USB له قيمة **DeviceID** أو **InstanceID متطابقة** . |

### <a name="access-control-policy"></a>نهج التحكم في Access

| اسم الخاصية | الوصف | خيارات |
|---|---|---|
| **PolicyRuleId** | يمثل GUID، وهو الم ID فريد، النهج وسيستخدم في إعداد التقارير استكشاف الأخطاء وإصلاحها. | |
| **IncludedIdList** | المجموعة (المجموعات) التي سيتم تطبيق النهج عليها. إذا تم إضافة مجموعات متعددة، سيتم تطبيق النهج على أي وسائط في كل هذه المجموعات.|يجب استخدام "الم ID/GUID" للمجموعة في هذا المثيل. <p> يوضح المثال التالي استخدام GroupID: <p> `<IncludedIdList> <GroupId> {EAA4CCE5-F6C9-4760-8BAD-FDCC76A2ACA1}</GroupId> </IncludedIdList>` |
| **ExcludedIDList** | المجموعة (المجموعات) التي لن يتم تطبيق النهج عليها. | يجب استخدام "الم ID/GUID" للمجموعة في هذا المثيل. |
| **"معرّف الإدخال"** | One PolicyRule يمكن أن يكون له إدخالات متعددة؛ كل إدخال مع GUID فريد يخبر التحكم في الجهاز بتقييد واحد.| |
| **النوع** | تعريف الإجراء لمجموعات التخزين القابلة للإزالة في IncludedIDList. <p>التنفيذ: السماح أو رفض <p>التدقيق: AuditAllowed أو AuditDenied<p> | السماح<p>رفض <p>AuditAllowed: يعرف الإعلام والحدث عند السماح بالوصول <p>AuditDenied: يعرف الإعلام والحدث عند رفض الوصول؛ يجب العمل معا مع **رفض** الإدخال.<p> عند وجود أنواع تعارض لنفس الوسائط، سيطبق النظام النوع الأول من النهج. مثال لنوع التعارض هو **السماح** **والرفض**. |
| **سيد** | تعرف مجموعة المستخدم المحلي Sid أو User Sid أو Sid من كائن AD ما إذا كان يجب تطبيق هذا النهج على مستخدم معين أو مجموعة مستخدمين معينين؛ يمكن أن يكون لمدخل واحد كحد أقصى واحد من Sid ومدخل بدون أي وسيلة من وسائل Sid لتطبيق النهج على الجهاز. |  |
| **ComputerSid** | مجموعة Sid أو مجموعة Sid للكمبيوتر المحلي أو مجموعة Sid للكائن AD، تحدد ما إذا كان يجب تطبيق هذا النهج على جهاز معين أو مجموعة أجهزة معينة؛ يمكن أن يكون لأحد الإدخالات واحد كحد أقصى على ComputerSid واحد، كما أن الإدخال بدون أي كمبيوتر يعني تطبيق النهج على الجهاز. إذا كنت تريد تطبيق إدخال على مستخدم معين وعلى جهاز معين، أضف كل من Sid و ComputerSid إلى الإدخال نفسه. |  |
| **خيارات** | تعريف ما إذا كنت تريد عرض الإعلام أم لا |**عند تحديد "السماح بالنوع"**: <p>0: لا شيء<p>4: تعطيل **AuditAllowed** and **AuditDenied لهذا** الإدخال. حتى لو **حدث** السماح وكان إعداد AuditAllowed مكونا، لن يرسل النظام حدثا. <p>8: قم بالتقاط معلومات الملف والحصول على نسخة من الملف كدليل للوصول للكتابة. <p>16: التقاط معلومات الملف للوصول إلى الكتابة. <p>**عند تحديد النوع رفض**: <p>0: لا شيء<p>4: تعطيل **AuditDenied لهذا** الإدخال. حتى إذا **حدث حظر** وكان إعداد AuditDenied مكونا، لن يظهر النظام إعلاما. <p>**عند تحديد **نوع التدقيقيحدد** كل شيء**: <p>0: لا شيء <p>1: لا شيء <p>2: إرسال الحدث<p>3: إرسال الحدث <p> **عند تحديد **نوع AuditDenied****: <p>0: لا شيء <p>1: إظهار الإعلام <p>2: إرسال الحدث<p>3: إظهار الإعلام وإرسال الحدث |
|AccessMask|تعريف الوصول. | **الوصول إلى مستوى القرص**: <p>1: قراءة <p>2: الكتابة <p>4: تنفيذ <p>**الوصول إلى مستوى نظام الملفات**: <p>8: قراءة نظام الملفات <p>16: كتابة نظام الملفات <p>32: تنفيذ نظام الملفات <p><p>يمكنك الحصول على وصول متعدد من خلال تنفيذ عملية OR ثنائية، على سبيل المثال، سيكون AccessMask للقراءة والكتابة والتنفيذ 7؛ سيكون AccessMask للقراءة والكتابة 3.|

## <a name="common-removable-storage-access-control-scenarios"></a>سيناريوهات "التحكم بالوصول إلى التخزين" الشائعة القابلة للإزالة

لمساعدتك على التعرف على Microsoft Defender ل "التحكم بالوصول إلى التخزين القابل للإزالة لنقطة النهاية"، قمنا بوضع بعض السيناريوهات الشائعة لمتابعتها.

### <a name="scenario-1-prevent-write-and-execute-access-to-all-but-allow-specific-approved-usbs"></a>السيناريو 1: منع الوصول للكتابة والتنفيذ إلى الكل مع السماح ببرنامس USBs معينة معتمدة

1. إنشاء مجموعات

    1. المجموعة 1: أي مساحة تخزينية قابلة للإزالة وCD/DVD. مثال على سعة تخزينية قابلة للإزالة وCD/DVD: المجموعة **9b28fae8-72f7-4267-a1a5-685f747a7146** في العينة أي ملف تخزين قابل للإزالة وملف [CD-DVD Group.xml](https://github.com/microsoft/mdatp-devicecontrol/tree/main/Removable%20Storage%20Access%20Control%20Samples) .

    2. المجموعة 2: الولايات المتحدة الأمريكية المعتمدة استنادا إلى خصائص الجهاز. مثال على حالة الاستخدام هذه هو: المثيل الم ID - المجموعة **65fa649a-a111-4912-9294-fb6337a25038** في نموذج ملفات [USBs Group.xml](https://github.com/microsoft/mdatp-devicecontrol/tree/main/Removable%20Storage%20Access%20Control%20Samples) .

    > [!TIP]
    > استبدل `&` ب `&amp;` في القيمة.

2. إنشاء نهج

    1. النهج 1: حظر الكتابة وتنفيذ الوصول مع السماح ببرنامس USBs المعتمدة. مثال على حالة الاستخدام هذه هو: PolicyRule **c544a991-5786-4402-949e-a032cb790d0e** في نموذج السيناريو 1 حظر الكتابة وتنفيذ الوصول ولكن مع [السماح](https://github.com/microsoft/mdatp-devicecontrol/tree/main/Removable%20Storage%20Access%20Control%20Samples) USBs.xmlالملف.

    2. النهج 2: التدقيق في الكتابة وتنفيذ الوصول إلى USBs المسموح به. مثال على حالة الاستخدام هذه هو: PolicyRule **36ae1037-a639-4cff-946b-b36c53089a4c** في نموذج السيناريو [1 تدقيق الكتابة وتنفيذ](https://github.com/microsoft/mdatp-devicecontrol/tree/main/Removable%20Storage%20Access%20Control%20Samples) الوصول إلى ملف USBs.xmlتمت الموافقة عليه.

### <a name="scenario-2-audit-write-and-execute-access-to-all-but-block-specific-unapproved-usbs"></a>السيناريو 2: التدقيق في الكتابة وتنفيذ الوصول إلى الكل ولكن حظر وحدات USBs معينة غير مرابة

1. إنشاء مجموعات

    1. المجموعة 1: أي مساحة تخزينية قابلة للإزالة وCD/DVD. مثال على حالة الاستخدام هذه هو: المجموعة **9b28fae8-72f7-4267-a1a5-685f747a7146** في العينة أي ملف تخزين قابل للإزالة وملف [CD-DVD Group.xml](https://github.com/microsoft/mdatp-devicecontrol/tree/main/Removable%20Storage%20Access%20Control%20Samples) .

    2. المجموعة 2: تم إلغاء الموافقة على USBs بالاستناد إلى خصائص الجهاز، على سبيل المثال، "مورد الم ID/ المنتج" و"الاسم مألوف" – المجموعة **65fa649a-a111-4912-9294-fb6337a25038 في** نموذج ملفات [USBs Group.xmlغير الممنعة](https://github.com/microsoft/mdatp-devicecontrol/tree/main/Removable%20Storage%20Access%20Control%20Samples) .

    > [!TIP]
    > استبدل `&` ب `&amp;` في القيمة.

2. إنشاء نهج

    1. النهج 1: حظر الوصول للكتابة وتنفيذه إلى الكل ولكن حظر USBs معين غير مفوف به. مثال على حالة الاستخدام هذه هو: PolicyRule **23b8e437-66ac-4b32-b3d7-24044637fc98** في نموذج السيناريو 2 تدقيق الكتابة وتنفيذ الوصول إلى جميع ملفات التدقيق ولكن حظر ملف معين غير [USBs.xml](https://github.com/microsoft/mdatp-devicecontrol/tree/main/Removable%20Storage%20Access%20Control%20Samples) .

    2. النهج 2: التدقيق في الكتابة وتنفيذ الوصول إلى الآخرين. مثال على حالة الاستخدام هذه هو: PolicyRule **b58ab853-9a6f-405c-a194-740e69422b48** في نموذج السيناريو [2 تدقيق الكتابة وتنفيذ الوصول إلى ملف others.xml](https://github.com/microsoft/mdatp-devicecontrol/tree/main/Removable%20Storage%20Access%20Control%20Samples) .

## <a name="deploying-and-managing-policy-via-group-policy"></a>نشر نهج وإدارته عبر نهج المجموعة

تمكنك ميزة التحكم بالوصول إلى التخزين القابلة للإزالة من تطبيق النهج عبر نهج المجموعة على المستخدم أو الجهاز أو كليهما.

### <a name="licensing"></a>الترخيص

قبل بدء استخدام "التحكم بالوصول إلى التخزين القابل للإزالة"، يجب تأكيد اشتراكك Microsoft 365 [التخزين](https://www.microsoft.com/microsoft-365/compare-microsoft-365-enterprise-plans?rtc=2). للوصول إلى عنصر تحكم الوصول إلى التخزين القابل للإزالة واستخدامه، يجب أن يكون لديك Microsoft 365 E3 أو Microsoft 365 E5.

### <a name="deploying-policy-via-group-policy"></a>نهج النشر عبر نهج المجموعة

1. ادمج كافة المجموعات ضمن `<Groups>` `</Groups>` ملف xml واحد.

    توضح الصورة التالية مثال السيناريو 1: منع الوصول للكتابة وتنفيذه [إلى الكل ولكن مع السماح ببرنامجات US معينة](#scenario-1-prevent-write-and-execute-access-to-all-but-allow-specific-approved-usbs) معتمدة.

    :::image type="content" source="images/prevent-write-access-allow-usb.png" alt-text="تعرض الشاشة إعدادات التكوين التي تسمح بأجهزة USBs معينة معتمدة على الأجهزة.":::

2. قم بدمج كل القواعد الموجودة في `<PolicyRules>` `</PolicyRules>` ملف xml واحد.

    إذا كنت تريد تقييد مستخدم معين، فاستخدم خاصية SID في الإدخال. إذا لم يكن هناك SID في إدخال النهج، سيتم تطبيق الإدخال على مثيل تسجيل الدخول للجميع للجهاز.
    
    إذا كنت تريد مراقبة معلومات الملف للوصول إلى الكتابة، فاستخدم AccessMask المناسب مع الخيار المناسب (16)؛ فيما يلي مثال على [معلومات ملف الالتقاط](https://github.com/microsoft/mdatp-devicecontrol/blob/main/Removable%20Storage%20Access%20Control%20Samples/Group%20Policy/Audit%20File%20Information.xml).

    توضح الصورة التالية استخدام خاصية SID، ومثال على السيناريو 1: منع الوصول للكتابة وتنفيذه إلى الكل مع السماح ببرنامج [USBs معين معتمد](#scenario-1-prevent-write-and-execute-access-to-all-but-allow-specific-approved-usbs).

    :::image type="content" source="images/usage-sid-property.png" alt-text="تعرض الشاشة رمزا يشير إلى استخدام سمة الخاصية SID.":::

3. احفظ ملفات XML الأساسية والمجموعة على مجلد مشاركة الشبكة وضع مسار مجلد مشاركة الشبكة في  إعداد نهج **المجموعة:** \>  \> قوالب تكوين الكمبيوتر الإدارية **Windows مكونات** \> \> برنامج الحماية من الفيروسات من Microsoft Defender **التحكم** في الجهاز: 'تعريف عنصر تحكم الجهاز **مجموعات النهج'** **و'تعريف قواعد نهج التحكم في الجهاز'**.

   إذا لم تتمكن من العثور على تكوين النهج UX في نهج المجموعة، يمكنك تنزيل ملفات [WindowsDefender.adml](https://github.com/microsoft/mdatp-devicecontrol/blob/main/Removable%20Storage%20Access%20Control%20Samples/WindowsDefender.adml) و [WindowsDefender.admx](https://github.com/microsoft/mdatp-devicecontrol/blob/main/Removable%20Storage%20Access%20Control%20Samples/WindowsDefender.admx) عن طريق تحديد **Raw** ثم **حفظ باسم**.

   - يجب أن يكون الجهاز الهدف قادرا على الوصول إلى مشاركة الشبكة للحصول على النهج. ومع ذلك، بمجرد قراءة النهج، لن يعود اتصال مشاركة الشبكة مطلوبا، حتى بعد إعادة تشغيل الجهاز.

    :::image type="content" source="images/device-control.png" alt-text="شاشة التحكم في الجهاز.":::

4. فرض افتراضي: يسمح لك بتعيين الوصول الافتراضي (رفض أو السماح) إلى الوسائط القابلة للإزالة إذا لم يكن هناك نهج. على سبيل المثال، لديك نهج فقط (إما رفض أو السماح) لإزالةMediaDevices، ولكن ليس لديك أي نهج ل CdRomDevices أو WpdDevices، كما يمكنك تعيين رفض افتراضي من خلال هذا النهج، سيتم حظر الوصول للقراءة/الكتابة/التنفيذ إلى CdRomDevices أو WpdDevices.

   - بمجرد نشر هذا الإعداد، سترى **السماح الافتراضي** أو **رفض افتراضي**.
   - يجب عليك التفكير في كل من مستوى القرص ومستوى نظام الملفات AccessMask عند تكوين هذا الإعداد، على سبيل المثال، إذا كنت تريد رفض افتراضي مع السماح بس تخزين معين، يجب السماح بالوصول إلى مستوى القرص ومستوى نظام الملف، يجب تعيين AccessMask إلى 63.

    :::image type="content" source="images/148609579-a7df650b-7792-4085-b552-500b28a35885.png" alt-text="السماح الافتراضي أو رفض التعليمات البرمجية الافتراضية ل PowerShell":::

5. تمكين عنصر تحكم الوصول إلى التخزين القابل للإزالة أو تعطيله: يمكنك تعيين هذه القيمة لتعطيل عنصر تحكم الوصول إلى التخزين القابل للإزالة مؤقتا.

    :::image type="content" source="images/148608318-5cda043d-b996-4146-9642-14fccabcb017.png" alt-text="إعدادات التحكم في الجهاز":::

   - بمجرد نشر هذا الإعداد، سترى **تمكين** أو **تعطيل**. معطل، فهذا يعني أن هذا الجهاز لا يقوم بتشغيل نهج التحكم بالوصول إلى التخزين القابل للإزالة.

    :::image type="content" source="images/148609685-4c05f002-5cbe-4aab-9245-83e730c5449e.png" alt-text="التحكم في الجهاز الذي تم تمكينه أو تعطيله في التعليمات البرمجية في PowerShell":::

6. تعيين موقع لنسخة من الملف: إذا كنت تريد الحصول على نسخة من الملف عند حدوث وصول للكتابة، يجب تعيين الموقع حيث يمكن للنظام حفظ النسخة.
    
    يمكنك نشر هذا مع AccessMask و Option المناسبين - راجع الخطوة 2 أعلاه.

    :::image type="content" source="../../media/define-device-control-policy-rules.png" alt-text="نهج المجموعة - تعيين locaiton لدلليل الملف":::

## <a name="deploying-and-managing-policy-via-intune-oma-uri"></a>نشر نهج وإدارته عبر Intune OMA-URI

تمكنك ميزة التحكم بالوصول إلى التخزين القابلة للإزالة من تطبيق النهج عبر OMA-URI على أي من المستخدمين أو الجهازين، أو كليهما.

### <a name="licensing-requirements"></a>متطلبات الترخيص

قبل بدء استخدام "التحكم بالوصول إلى التخزين القابل للإزالة"، يجب تأكيد اشتراكك Microsoft 365 [التخزين](https://www.microsoft.com/microsoft-365/compare-microsoft-365-enterprise-plans?rtc=2). للوصول إلى عنصر تحكم الوصول إلى التخزين القابل للإزالة واستخدامه، يجب أن يكون لديك Microsoft 365 E3 أو Microsoft 365 E5.

### <a name="permission"></a>الإذن

لنشر النهج في Intune، يجب أن يكون للحساب أذونات لإنشاء ملفات تعريف تكوين الجهاز أو تحريرها أو تحديثها أو حذفها. يمكنك إنشاء أدوار مخصصة أو استخدام أي من الأدوار المضمنة باستخدام هذه الأذونات.

- دور إدارة ملفات التعريف والسياسات

- دور مخصص مع تشغيل أذونات إنشاء/تحرير/تحديث/قراءة/حذف/عرض التقارير لملفات تعريف تكوين الجهاز

- المسؤول العام

### <a name="deploying-policy-via-oma-uri"></a>نشر النهج عبر OMA-URI

إدارة نقاط النهاية من Microsoft تكوين الأجهزة في  \>  \><https://endpoint.microsoft.com/>\> مركز إدارة الأجهزة **إنشاء** \> النظام الأساسي **لملف التعريف: Windows 10 واللاحقة & ملف التعريف: مخصص**

1. لكل مجموعة، أنشئ قاعدة OMA-URI:

    - OMA-URI:

      `./Vendor/MSFT/Defender/Configuration/DeviceControl/PolicyGroups/%7b**GroupGUID**%7d/GroupData`

      على سبيل المثال، **بالنسبة إلى أي تخزين قابل للإزالة ومجموعة قرص مضغوط/قرص DVD** في العينة، يجب أن يكون الارتباط:

      `./Vendor/MSFT/Defender/Configuration/DeviceControl/PolicyGroups/%7b9b28fae8-72f7-4267-a1a5-685f747a7146%7d/GroupData`

    - نوع البيانات: سلسلة (ملف XML)

      :::image type="content" source="images/xml-data-type-string.png" alt-text="ملف xml لنوع بيانات STRING.":::

2. لكل نهج، قم أيضا بإنشاء OMA-URI:

    - OMA-URI:

      `./Vendor/MSFT/Defender/Configuration/DeviceControl/PolicyRules/%7b**PolicyRuleGUID**%7d/RuleData`

      على سبيل المثال، لحظر **الكتابة وتنفيذ الوصول مع السماح بالقاعدة USBs** المعتمدة في العينة، يجب أن يكون الارتباط:

      `./Vendor/MSFT/Defender/Configuration/DeviceControl/PolicyRules/%7bc544a991-5786-4402-949e-a032cb790d0e%7d/RuleData`

    - نوع البيانات: سلسلة (ملف XML)
       
    إذا كنت تريد مراقبة معلومات الملف للوصول إلى الكتابة، فاستخدم AccessMask المناسب مع الخيار المناسب (16)؛ فيما يلي مثال على [معلومات ملف الالتقاط](https://github.com/microsoft/mdatp-devicecontrol/blob/main/Removable%20Storage%20Access%20Control%20Samples/Intune%20OMA-URI/Audit%20File%20Information.xml).

3. فرض افتراضي: يسمح لك بتعيين الوصول الافتراضي (رفض أو السماح) إلى الوسائط القابلة للإزالة إذا لم يكن هناك نهج. على سبيل المثال، لديك نهج فقط (إما رفض أو السماح) لإزالةMediaDevices، ولكن ليس لديك أي نهج ل CdRomDevices أو WpdDevices، كما يمكنك تعيين رفض افتراضي من خلال هذا النهج، سيتم حظر الوصول للقراءة/الكتابة/التنفيذ إلى CdRomDevices أو WpdDevices.

    - OMA-URI: `./Vendor/MSFT/Defender/Configuration/DefaultEnforcement`

    - نوع البيانات: Int

      `DefaultEnforcementAllow = 1`
      `DefaultEnforcementDeny = 2`

    - بمجرد نشر هذا الإعداد، سترى **السماح الافتراضي** أو **رفض افتراضي**
    - يجب عليك التفكير في كل من مستوى القرص ومستوى نظام الملفات AccessMask عند تكوين هذا الإعداد، على سبيل المثال، إذا كنت تريد رفض افتراضي مع السماح بس تخزين معين، يجب السماح بالوصول إلى مستوى القرص ومستوى نظام الملف، يجب تعيين AccessMask إلى 63.

    :::image type="content" source="images/148609590-c67cfab8-8e2c-49f8-be2b-96444e9dfc2c.png" alt-text="فرض افتراضي السماح باختصارات PowerShell البرمجية":::

4. تمكين عنصر تحكم الوصول إلى التخزين القابل للإزالة أو تعطيله: يمكنك تعيين هذه القيمة لتعطيل عنصر تحكم الوصول إلى التخزين القابل للإزالة مؤقتا.

   - OMA-URI: `./Vendor/MSFT/Defender/Configuration/DeviceControlEnabled`

   - نوع البيانات: Int `Disable: 0`
     `Enable: 1`

   - بمجرد نشر هذا الإعداد، سترى **"تم التمكين** " أو **"معطل"**

    **معطل** يعني أن هذا الجهاز لا يقوم بتشغيل نهج التحكم بالوصول إلى التخزين القابل للإزالة

    :::image type="content" source="images/148609770-3e555883-f26f-45ab-9181-3fb1ff7a38ac.png" alt-text="التحكم بالوصول إلى التخزين القابل للإزالة في رمز PowerShell":::

5. تعيين موقع نسخة من الملف: إذا كنت تريد الحصول على نسخة من الملف عند حدوث وصول للكتابة، يجب تعيين الموقع حيث يمكن للنظام حفظ النسخة.
    
    - OMA-URI: `./Vendor/MSFT/Defender/Configuration/DataDuplicationRemoteLocation;**username**;**password**`

    - نوع البيانات: سلسلة
    
    يجب عليك نشر هذا مع AccessMask الصحيح و الخيار الصحيح - راجع الخطوة 2 أعلاه.

    :::image type="content" source="../../media/device-control-oma-uri-edit-row.png" alt-text="تعيين locaiton لدلليل الملف":::
    
## <a name="deploying-and-managing-policy-by-using-intune-user-interface"></a>نشر نهج وإدارته باستخدام واجهة مستخدم Intune

تتوفر هذه الإمكانية في مركز إدارة إدارة نقاط النهاية من Microsoft (<https://endpoint.microsoft.com/>). انتقل إلى **نهج الحد** >  من **الحد من Surface SecurityAtack** > **.** اختر **النظام الأساسي: Windows 10 واللاحقة** باستخدام **ملف التعريف: التحكم في الجهاز**.

## <a name="view-device-control-removable-storage-access-control-data-in-microsoft-defender-for-endpoint"></a>عرض بيانات التحكم في الوصول إلى التخزين القابلة للإزالة في Microsoft Defender لنقطة النهاية

يعرض [Microsoft 365 Defender المدخل](https://security.microsoft.com/advanced-hunting) الأحداث التي يتم تشغيلها بواسطة عنصر تحكم الوصول إلى التخزين القابل للإزالة من الجهاز. للوصول إلى Microsoft 365 الأمان، يجب أن يكون لديك الاشتراك التالي:

- Microsoft 365 لتقارير E5

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
//RemovableStorageFileEvent: event triggered by File level enforcement, information of files written to removable storage 
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
| extend DuplicatedOperation = tostring(parsed.DuplicatedOperation)
| extend FileEvidenceLocation = tostring(parsed.TargetFileLocation) 
| project Timestamp, DeviceId, DeviceName, InitiatingProcessAccountName, 
    ActionType, Policy, PolicyRuleId, DuplicatedOperation, 
    MediaClassName, MediaInstanceId, MediaName, MediaProductId, MediaVendorId, MediaSerialNumber,
    FileName, FolderPath, FileSize, FileEvidenceLocation,
    AdditionalFields
| order by Timestamp desc
```
    
:::image type="content" source="images/block-removable-storage.png" alt-text="الشاشة التي تصف انسداد مساحة التخزين القابلة للإزالة.":::

## <a name="frequently-asked-questions"></a>الأسئلة المتكررة

### <a name="what-is-the-removable-storage-media-limitation-for-the-maximum-number-of-usbs"></a>ما هو حد وسائط التخزين القابلة للإزالة لأقصى عدد من وحدات USBs؟

لقد تحققنا من صحة مجموعة USB واحدة بحجم 100000 وسائط - يصل حجمها إلى 7 MB. يعمل النهج في كل من Intune و GPO بدون مشاكل في الأداء.

### <a name="why-does-the-policy-not-work"></a>لماذا لا يعمل النهج؟

السبب الأكثر شيوعا هو عدم وجود إصدار عميل [مكافحة البرامج الضارة المطلوب](/microsoft-365/security/defender-endpoint/device-control-removable-storage-access-control#prepare-your-endpoints).

قد يكون السبب الآخر هو عدم تنسيق ملف XML بشكل صحيح، على سبيل المثال، عدم استخدام تنسيق العلامات الصحيح للعلامة "&" في ملف XML، أو قد يضيف محرر النص علامة ترتيب (BOM) 0xEF 0xBB 0xBF في بداية الملفات، مما يؤدي إلى عدم عمل تحليل XML. أحد الحلول البسيطة هو تنزيل [نموذج الملف](https://github.com/microsoft/mdatp-devicecontrol/tree/main/Removable%20Storage%20Access%20Control%20Samples) (حدد **الخام** ثم **حفظ باسم**) ثم قم بتحديثه.

إذا كنت تقوم بنشر النهج وإدارته عبر نهج المجموعة، فالرجاء التأكد من دمج كل النهج في ملف XML واحد ضمن عقدة أصل تسمى PolicyRules وكل المجموعة في ملف XML واحد ضمن عقدة أصل تسمى المجموعات؛ إذا كنت تدير من خلال Intune، فاحتفظ ب ملف نهج واحد XML، والشيء نفسه، ملف XML واحد في المجموعة.

### <a name="there-is-no-configuration-ux-for-define-device-control-policy-groups-and-define-device-control-policy-rules-on-my-group-policy"></a>لا يوجد تكوين UX ل "تعريف مجموعات نهج التحكم في الجهاز" و"تعريف قواعد نهج التحكم في الجهاز" في نهج المجموعة

لا نقوم ب دعم تكوين نهج المجموعة UX، ولكن لا يزال بإمكانك الحصول على ملفات adml و admx ذات الصلة بالنقر فوق "الخام" و"حفظ باسم" في ملفات [WindowsDefender.adml](https://github.com/microsoft/mdatp-devicecontrol/blob/main/Removable%20Storage%20Access%20Control%20Samples/WindowsDefender.adml) و [WindowsDefender.admx](https://github.com/microsoft/mdatp-devicecontrol/blob/main/Removable%20Storage%20Access%20Control%20Samples/WindowsDefender.admx) .

### <a name="how-can-i-know-whether-the-latest-policy-has-been-deployed-to-the-target-machine"></a>كيف يمكنني معرفة ما إذا تم نشر النهج الأخير على الجهاز الهدف؟

يمكنك تشغيل 'Get-MpComputerStatus' على PowerShell كمسؤول. ستعرض القيمة التالية ما إذا كان قد تم تطبيق النهج الأخير على الجهاز الهدف.

:::image type="icon" source="images/148609885-bea388a9-c07d-47ef-b848-999d794d24b8.png" border="false":::

### <a name="how-can-i-know-which-machine-is-using-out-of-date-antimalware-client-version-in-the-organization"></a>كيف يمكنني معرفة الجهاز الذي يستخدم إصدار عميل مكافحة البرامج الضارة القديمة في المؤسسة؟

يمكنك استخدام الاستعلام التالي للحصول على إصدار عميل مكافحة البرامج الضارة على Microsoft 365 الأمان:

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
