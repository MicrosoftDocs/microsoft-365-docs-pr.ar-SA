---
title: محلل الأداء برنامج الحماية من الفيروسات من Microsoft Defender
description: يصف الإجراء لضبط أداء برنامج الحماية من الفيروسات من Microsoft Defender.
keywords: ضبط، أداء، microsoft Defender لنقطة النهاية، برنامج الحماية من الفيروسات للمدافع
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
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 3c517d9adcdc2181b43c430a92be3de9ac889dd6
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/27/2022
ms.locfileid: "65101106"
---
# <a name="performance-analyzer-for-microsoft-defender-antivirus"></a>محلل الأداء برنامج الحماية من الفيروسات من Microsoft Defender

**ينطبق على**
- [Microsoft Defender لنقطة النهاية الخطة 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Defender for Endpoint الخطة 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- برنامج الحماية من الفيروسات من Microsoft Defender

**الأنظمة الأساسية**
- بالنسبة لنظام التشغيل

## <a name="what-is-microsoft-defender-antivirus-performance-analyzer"></a>ما هو محلل الأداء برنامج الحماية من الفيروسات من Microsoft Defender؟

في بعض الحالات، قد تحتاج إلى ضبط أداء برنامج الحماية من الفيروسات من Microsoft Defender في أثناء فحص ملفات ومجلدات معينة. محلل الأداء هو أداة سطر أوامر PowerShell التي تساعد على تحديد الملفات وملحقات الملفات والعمليات التي قد تسبب مشكلات في الأداء على نقاط النهاية الفردية. يمكن استخدام هذه المعلومات لتقييم مشكلات الأداء بشكل أفضل وتطبيق إجراءات المعالجة.

تتضمن بعض الخيارات التي يجب تحليلها ما يلي:

- أهم الملفات التي تؤثر على وقت الفحص
- أهم العمليات التي تؤثر على وقت الفحص
- ملحقات الملفات العلوية التي تؤثر على وقت الفحص
- المجموعات - على سبيل المثال، أعلى الملفات لكل ملحق، أعلى عمليات الفحص لكل ملف، أعلى عمليات الفحص لكل ملف لكل عملية

## <a name="running-performance-analyzer"></a>تشغيل محلل الأداء

تتضمن العملية عالية المستوى لتشغيل محلل الأداء الخطوات التالية:

1. تشغيل محلل الأداء لجمع تسجيل أداء أحداث برنامج الحماية من الفيروسات من Microsoft Defender على نقطة النهاية.

   > [!NOTE]
   > يتم تسجيل أداء أحداث برنامج الحماية من الفيروسات من Microsoft Defender من نوع **Microsoft-Antimalware-Engine** من خلال محلل الأداء.

2. تحليل نتائج الفحص باستخدام تقارير تسجيل مختلفة.

## <a name="using-performance-analyzer"></a>استخدام محلل الأداء

لبدء تسجيل أحداث النظام، افتح PowerShell في الوضع الإداري واتبع الخطوات التالية:

1. تشغيل الأمر التالي لبدء التسجيل:

   `New-MpPerformanceRecording -RecordTo <recording.etl>`

    حيث `-RecordTo` تحدد المعلمة موقع المسار الكامل الذي يتم فيه حفظ ملف التتبع. لمزيد من المعلومات حول cmdlet، راجع [برنامج الحماية من الفيروسات من Microsoft Defender cmdlets](/powershell/module/defender).

2. إذا كانت هناك عمليات أو خدمات يعتقد أنها تؤثر على الأداء، فكرر الحالة من خلال تنفيذ المهام ذات الصلة.

3. اضغط على **ENTER** لإيقاف التسجيل وحفظه، أو **Ctrl+C** لإلغاء التسجيل.

4. تحليل النتائج باستخدام معلمة محلل `Get-MpPerformanceReport`الأداء. على سبيل المثال، عند تنفيذ الأمر `Get-MpPerformanceReport -Path <recording.etl> -TopFiles 3 -TopScansPerFile 10`، يتم تزويد المستخدم بقائمة من أفضل عشرة عمليات مسح ضوئي لأعلى 3 ملفات تؤثر على الأداء.

لمزيد من المعلومات حول معلمات سطر الأوامر وخياراته، راجع [New-MpPerformanceRecording](#new-mpperformancerecording) و [Get-MpPerformanceReport](#get-mpperformancereport).

> [!NOTE]
> عند تشغيل تسجيل، إذا تلقيت رسالة الخطأ "لا يمكن بدء تسجيل الأداء لأن مسجل الأداء Windows قيد التسجيل بالفعل"، فشغل الأمر التالي لإيقاف التتبع الموجود باستخدام الأمر الجديد: **wpr -cancel -instancename MSFT_MpPerformanceRecording**

## <a name="performance-tuning-data-and-information"></a>بيانات ضبط الأداء ومعلوماته

استنادا إلى الاستعلام، سيتمكن المستخدم من عرض البيانات لحسابات الفحص والمدة (الإجمالي/الحد الأدنى/المتوسط/الحد الأقصى/الوسيط)، والمسار، والعملية، وسبب الفحص. تظهر الصورة أدناه نموذج الإخراج لاستعلام بسيط لأعلى 10 ملفات لتأثير الفحص.

:::image type="content" source="images/example-output.png" alt-text="مثال على الإخراج لاستعلام TopFiles أساسي" lightbox="images/example-output.png":::

## <a name="additional-functionality-exporting-and-converting-to-csv-and-json"></a>وظائف إضافية: التصدير والتحويل إلى CSV وJSON

يمكن أيضا تصدير نتائج محلل الأداء وتحويلها إلى ملف CSV أو JSON.
للحصول على أمثلة تصف عملية "التصدير" و"التحويل" من خلال نماذج التعليمات البرمجية، انظر أدناه.

### <a name="for-csv"></a>ل CSV

- **للتصدير**: `(Get-MpPerformanceReport -Path:.\Repro-Install.etl -Topscans:1000). TopScans | Export-CSV -Path:.\Repro-Install-Scans.csv -Encoding:UTF8 -NoTypeInformation`

- **للتحويل**: `(Get-MpPerformanceReport -Path:.\Repro-Install.etl -Topscans:100). TopScans | ConvertTo-Csv -NoTypeInformation`

### <a name="for-json"></a>ل JSON

- **للتحويل**: `(Get-MpPerformanceReport -Path:.\Repro-Install.etl -Topscans:1000). TopScans | ConvertTo-Json -Depth:1`

لضمان إخراج قابل للقراءة آليا للتصدير مع أنظمة معالجة البيانات الأخرى، يوصى باستخدام المعلمة -Raw للحصول على MpPerformanceReport. راجع أدناه للحصول على التفاصيل

## <a name="requirements"></a>الاحتياجات

يحتوي برنامج الحماية من الفيروسات من Microsoft Defender محلل الأداء على المتطلبات الأساسية التالية:

- الإصدارات Windows المعتمدة: Windows 10 و Windows 11 وخادم Windows 2016 وما فوق
- إصدار النظام الأساسي: 4.18.2108.7+
- إصدار PowerShell: PowerShell الإصدار 5.1، PowerShell ISE، Remote PowerShell (4.18.2201.10+)، PowerShell 7.x (4.18.2201.10+)

## <a name="powershell-reference"></a>مرجع PowerShell

هناك اثنان من أوامر Cmdlets PowerShell الجديدة المستخدمة لضبط أداء برنامج الحماية من الفيروسات من Microsoft Defender:

- [New-MpPerformanceRecording](#new-mpperformancerecording)
- [Get-MpPerformanceReport](#get-mpperformancereport)

### <a name="new-mpperformancerecording"></a>New-MpPerformanceRecording

يصف القسم التالي المرجع ل PowerShell cmdlet New-MpPerformanceRecording الجديد. يجمع cmdlet هذا تسجيل أداء عمليات المسح الضوئي برنامج الحماية من الفيروسات من Microsoft Defender.

#### <a name="syntax-new-mpperformancerecording"></a>بناء الجملة: New-MpPerformanceRecording

```powershell
New-MpPerformanceRecording -RecordTo <String >
```

#### <a name="description-new-mpperformancerecording"></a>الوصف: New-MpPerformanceRecording

`New-MpPerformanceRecording` يجمع cmdlet تسجيل أداء عمليات المسح الضوئي برنامج الحماية من الفيروسات من Microsoft Defender. تحتوي تسجيلات الأداء هذه على أحداث عملية Microsoft-Antimalware-Engine وNT kernel ويمكن تحليلها بعد التجميع باستخدام [Get-MpPerformanceReport](#get-mpperformancereport) cmdlet.

يوفر أمر cmdlet هذا `New-MpPerformanceRecording` نظرة ثاقبة على الملفات الإشكالية التي يمكن أن تسبب تدهورا في أداء برنامج الحماية من الفيروسات من Microsoft Defender. يتم توفير هذه الأداة "AS IS"، ولا تهدف إلى تقديم اقتراحات حول الاستثناءات. يمكن أن تقلل الاستثناءات من مستوى الحماية على نقاط النهاية الخاصة بك. وينبغي تعريف الاستثناءات، إن وجدت، بحذر.

لمزيد من المعلومات حول محلل الأداء، راجع [محلل الأداء](/windows-hardware/test/wpt/windows-performance-analyzer) المستندات.

> [!IMPORTANT]
> يتطلب أمر cmdlet هذا امتيازات مسؤول مرتفعة.

**إصدارات نظام التشغيل المدعومة**:

Windows الإصدار 10 والإصدارات الأحدث.

> [!NOTE]
> تتوفر هذه الميزة بدءا من إصدار النظام الأساسي 4.18.2108.X والإصدارات الأحدث.

#### <a name="examples-new-mpperformancerecording"></a>أمثلة: New-MpPerformanceRecording

##### <a name="example-1-collect-a-performance-recording-and-save-it"></a>مثال 1: جمع تسجيل أداء وحفظه

```powershell
New-MpPerformanceRecording -RecordTo:.\Defender-scans.etl
```

يجمع الأمر أعلاه تسجيل أداء ويحفظه في المسار المحدد: **.\Defender-scans.etl**.

##### <a name="example-2-collect-a-performance-recording-for-remote-powershell-session"></a>مثال 2: جمع تسجيل أداء لجلسة عمل Remote PowerShell

```powershell
$s = New-PSSession -ComputerName Server02 -Credential Domain01\User01
New-MpPerformanceRecording -RecordTo C:\LocalPathOnServer02\trace.etl -Session $s
```

يجمع الأمر أعلاه تسجيل أداء على Server02 (كما هو محدد بواسطة الوسيطة $s لجلسة عمل المعلمة) ويحفظه في المسار المحدد: **C:\LocalPathOnServer02\trace.etl** على Server02.

##### <a name="example-3-collect-a-performance-recording-in-non-interactive-mode"></a>مثال 3: جمع تسجيل أداء في وضع غير تفاعلي
```powershell
New-MpPerformanceRecording -RecordTo:.\Defender-scans.etl -Seconds 60 
```
يجمع الأمر أعلاه تسجيل أداء للمدة بالثوان المحددة بواسطة المعلمة -Seconds. يوصى بذلك للمستخدمين الذين يقومون بإجراء مجموعات دفعات لا تتطلب أي تفاعل أو مطالبة.

#### <a name="parameters-new-mpperformancerecording"></a>المعلمات: New-MpPerformanceRecording

##### <a name="-recordto"></a>-RecordTo

تحديد الموقع الذي سيتم فيه حفظ تسجيل أداء Microsoft Defender Antimalware.

```yaml
Type: String
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

##### <a name="-session"></a>-جلسة عمل

تحديد كائن PSSession الذي سيتم فيه إنشاء تسجيل أداء برنامج الحماية من الفيروسات من Microsoft Defender وحفظه. عند استخدام هذه المعلمة، تشير المعلمة RecordTo إلى المسار المحلي على الجهاز البعيد. متوفر مع إصدار نظام Defender الأساسي 4.18.2201.10.

```yaml
Type: PSSession[]
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

##### <a name="-seconds"></a>-ثوان
تحديد مدة تسجيل الأداء بالثوان. يوصى بذلك للمستخدمين الذين يقومون بإجراء مجموعات دفعات لا تتطلب أي تفاعل أو مطالبة.

```yaml
Type: Int32
Position: Named
Default value: 0
Accept pipeline input: False
Accept wildcard characters: False
```

### <a name="get-mpperformancereport"></a>Get-MpPerformanceReport

يصف القسم التالي Get-MpPerformanceReport PowerShell cmdlet. تحليل وتسجيل أداء برنامج الحماية من الفيروسات من Microsoft Defender (MDAV).

#### <a name="syntax-get-mpperformancereport"></a>بناء الجملة: Get-MpPerformanceReport

```powershell
Get-MpPerformanceReport    [-Path] <String>
[-TopScans <Int32>]
[-TopFiles  <Int32>
    [-TopScansPerFile <Int32>]
    [-TopProcessesPerFile  <Int32>
        [-TopScansPerProcessPerFile <Int32>]
    ]
]
[-TopExtensions  <Int32>
    [-TopScansPerExtension <Int32>]
    [-TopProcessesPerExtension <Int32>
        [-TopScansPerProcessPerExtension <Int32>]
        ]
    [-TopFilesPerExtension  <Int32>
        [-TopScansPerFilePerExtension <Int32>]
        ]
    ]
]
[-TopProcesses  <Int32>
    [-TopScansPerProcess <Int32>]
    [-TopExtensionsPerProcess <Int32>
        [-TopScansPerExtensionPerProcess <Int32>]
    ]
]
[-TopFilesPerProcess  <Int32>
    [-TopScansPerFilePerProcess <Int32>]
]
[-MinDuration <String>]
[-Raw]
```

#### <a name="description-get-mpperformancereport"></a>الوصف: Get-MpPerformanceReport

`Get-MpPerformanceReport` يقوم cmdlet بتحليل تسجيل أداء برنامج الحماية من الفيروسات من Microsoft Defender تم جمعه مسبقا ([New-MpPerformanceRecording](#new-mpperformancerecording)) ويبلغ عن مسارات الملفات وملحقات الملفات والعمليات التي تسبب أكبر تأثير عمليات فحص برنامج الحماية من الفيروسات من Microsoft Defender.

يوفر محلل الأداء نظرة ثاقبة على الملفات الإشكالية التي يمكن أن تسبب تدهورا في أداء برنامج الحماية من الفيروسات من Microsoft Defender. يتم توفير هذه الأداة "AS IS" ولا تهدف إلى تقديم اقتراحات حول الاستثناءات. يمكن أن تقلل الاستثناءات من مستوى الحماية على نقاط النهاية الخاصة بك. وينبغي تعريف الاستثناءات، إن وجدت، بحذر.

لمزيد من المعلومات حول محلل الأداء، راجع [محلل الأداء](/windows-hardware/test/wpt/windows-performance-analyzer) المستندات.

**إصدارات نظام التشغيل المدعومة**:

Windows الإصدار 10 والإصدارات الأحدث.

> [!NOTE]
> تتوفر هذه الميزة بدءا من إصدار النظام الأساسي 4.18.2108.X والإصدارات الأحدث.

#### <a name="examples-get-mpperformancereport"></a>أمثلة: Get-MpPerformanceReport

##### <a name="example-1-single-query"></a>مثال 1: استعلام مفرد

```powershell
Get-MpPerformanceReport -Path:.\Defender-scans.etl -TopScans:20
```

##### <a name="example-2-multiple-queries"></a>مثال 2: استعلامات متعددة

```powershell
Get-MpPerformanceReport -Path:.\Defender-scans.etl -TopFiles:10 -TopExtensions:10 -TopProcesses:10 -TopScans:10
```

##### <a name="example-3-nested-queries"></a>مثال 3: الاستعلامات المتداخلة

```powershell
Get-MpPerformanceReport -Path:.\Defender-scans.etl -TopProcesses:10 -TopExtensionsPerProcess:3 -TopScansPerExtensionPerProcess:3
```

##### <a name="example-4-using--minduration-parameter"></a>مثال 4: استخدام معلمة -MinDuration

```powershell
Get-MpPerformanceReport -Path:.\Defender-scans.etl -TopScans:100 -MinDuration:100ms
```
##### <a name="example-5-using--raw-parameter"></a>مثال 5: استخدام المعلمة -Raw

```powershell
Get-MpPerformanceReport -Path:.\Defender-scans.etl -TopFiles:10 -TopExtensions:10 -TopProcesses:10 -TopScans:10 -Raw | ConvertTo-Json
```
استخدام -Raw في الأمر أعلاه يحدد أن الإخراج يجب أن يكون قابلا للقراءة الآلية ويمكن تحويله بسهولة إلى تنسيقات التسلسل مثل JSON

#### <a name="parameters-get-mpperformancereport"></a>المعلمات: Get-MpPerformanceReport

##### <a name="-minduration"></a>-MinDuration

تحديد الحد الأدنى للمدة الزمنية لأي فحص أو إجمالي مدد الفحص للملفات والملحقات والعمليات المضمنة في التقرير؛ يقبل قيما مثل  **0.1234567sec** أو **0.1234ms** أو **0.1us** أو TimeSpan صالح.

```yaml
Type: String
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

##### <a name="-path"></a>-المسار

تحديد المسار (المسارات) إلى موقع واحد أو أكثر.

```yaml
Type: String
Position: 0
Default value: None
Accept pipeline input: True
Accept wildcard characters: False
```
##### <a name="-raw"></a>-Raw

تحديد أن إخراج تسجيل الأداء يجب أن يكون قابلا للقراءة الآلية وقابلا للتحويل بسهولة إلى تنسيقات التسلسل مثل JSON (على سبيل المثال، عبر الأمر تحويل إلى JSON). يوصى بذلك للمستخدمين المهتمين بمعالجة الدفعات مع أنظمة معالجة البيانات الأخرى. 

```yaml
Type: <SwitchParameter>
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

##### <a name="-topextensions"></a>-TopExtensions

تحديد عدد الملحقات العلوية إلى الإخراج، التي تم فرزها حسب "المدة".

```yaml
Type: Int32
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

##### <a name="-topextensionsperprocess"></a>-TopExtensionsPerProcess

تحديد عدد الملحقات العلوية التي يجب إخراجها لكل عملية علوية، تم فرزها حسب "المدة".

```yaml
Type: Int32
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

##### <a name="-topfiles"></a>-TopFiles

يطلب تقرير الملفات العليا ويحدد عدد الملفات العليا التي يجب إخراجها، والتي تم فرزها حسب "المدة".

```yaml
Type: Int32
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

##### <a name="-topfilesperextension"></a>-TopFilesPerExtension

تحديد عدد الملفات العلوية التي يجب إخراجها لكل ملحق علوي، تم فرزها حسب "المدة".

```yaml
Type: Int32
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

##### <a name="-topfilesperprocess"></a>-TopFilesPerProcess

تحديد عدد الملفات العلوية التي يجب إخراجها لكل عملية علوية، تم فرزها حسب "المدة".

```yaml
Type: Int32
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

##### <a name="-topprocesses"></a>-TopProcesses

يطلب تقرير العمليات العليا ويحدد عدد العمليات العليا التي يجب إخراجها، والتي تم فرزها حسب "المدة".

```yaml
Type: Int32
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

##### <a name="-topprocessesperextension"></a>-TopProcessesPerExtension

تحديد عدد العمليات العليا التي يجب إخراجها لكل ملحق علوي، تم فرزها حسب "المدة".

```yaml
Type: Int32
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

##### <a name="-topprocessesperfile"></a>-TopProcessesPerFile

تحديد عدد العمليات العليا التي يجب إخراجها لكل ملف علوي، تم فرزها حسب "المدة".

```yaml
Type: Int32
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

##### <a name="-topscans"></a>-TopScans

يطلب تقرير المسح الأعلى ويحدد عدد عمليات الفحص العليا إلى الإخراج، والتي تم فرزها حسب "المدة".

```yaml
Type: Int32
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

##### <a name="-topscansperextension"></a>-TopScansPerExtension

تحديد عدد عمليات الفحص العلوية لإخراج كل ملحق علوي، تم فرزها حسب "المدة".

```yaml
Type: Int32
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

##### <a name="-topscansperextensionperprocess"></a>-TopScansPerExtensionPerProcess

تحديد عدد عمليات الفحص العلوية لإخراج كل ملحق علوي لكل عملية علوية، تم فرزها حسب "المدة".

```yaml
Type: Int32
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

##### <a name="-topscansperfile"></a>-TopScansPerFile

تحديد عدد عمليات الفحص العلوية لإخراج كل ملف علوي، تم فرزه حسب "المدة".

```yaml
Type: Int32
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

##### <a name="-topscansperfileperextension"></a>-TopScansPerFilePerExtension

تحديد عدد عمليات الفحص العلوية لإخراج كل ملف علوي لكل ملحق علوي، تم فرزه حسب "المدة".

```yaml
Type: Int32
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

##### <a name="-topscansperfileperprocess"></a>-TopScansPerFilePerProcess

تحديد عدد عمليات الفحص العلوية للإخراج لكل ملف علوي لكل عملية علوية، تم فرزها حسب "المدة".

```yaml
Type: Int32
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

##### <a name="-topscansperprocess"></a>-TopScansPerProcess

تحديد عدد عمليات الفحص العليا لإخراج كل عملية علوية في تقرير العمليات العليا، التي تم فرزها حسب "المدة".

```yaml
Type: Int32
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

##### <a name="-topscansperprocessperextension"></a>-TopScansPerProcessPerExtension

تحديد عدد عمليات الفحص العلوية للإخراج لكل عملية علوية لكل ملحق علوي، تم فرزها حسب "المدة".

```yaml
Type: Int32
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

##### <a name="-topscansperprocessperfile"></a>-TopScansPerProcessPerFile

تحديد عدد عمليات الفحص العلوية للإخراج لكل عملية علوية لكل ملف علوي، تم فرزها حسب "المدة".

```yaml
Type: Int32
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

## <a name="additional-resources"></a>موارد إضافية

إذا كنت تبحث عن معلومات متعلقة بالحماية من الفيروسات للأنظمة الأساسية الأخرى، فراجع:

- [تعيين تفضيلات Microsoft Defender لنقطة النهاية على نظام التشغيل macOS](mac-preferences.md)
- [Microsoft Defender for Endpoint على Mac](microsoft-defender-endpoint-mac.md)
- [إعدادات نهج برنامج الحماية من الفيروسات في macOS لبرنامج الحماية من الفيروسات من Microsoft Defender Antivirus for Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
- [تعيين تفضيلات Microsoft Defender لنقطة النهاية على Linux](linux-preferences.md)
- [مشكلات الأداء في Microsoft Defender لنقطة النهاية على Linux](microsoft-defender-endpoint-linux.md)
- [تكوين Defender لنقطة النهاية على ميزات](android-configure.md)-  Android [تكوين Microsoft Defender لنقطة النهاية على ميزات iOS](ios-configure-features.md)
