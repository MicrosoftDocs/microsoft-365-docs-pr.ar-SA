---
title: محلل الأداء برنامج الحماية من الفيروسات من Microsoft Defender
description: يصف الإجراء لضبط أداء برنامج الحماية من الفيروسات من Microsoft Defender.
keywords: ، أداء، microsoft defender لنقطة النهاية، برنامج الحماية من الفيروسات ل defender
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
ms.openlocfilehash: 91dd3dc8563e7bd443362c47190139101a5ede61
ms.sourcegitcommit: 4c207a9bdbb6c8ba372ae37907ccefca031a49f8
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 02/09/2022
ms.locfileid: "63575856"
---
# <a name="performance-analyzer-for-microsoft-defender-antivirus"></a>محلل الأداء برنامج الحماية من الفيروسات من Microsoft Defender

**ينطبق على**
- [خطة Microsoft Defender لنقطة النهاية 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

**ما هو برنامج الحماية من الفيروسات من Microsoft Defender الأداء؟**

في بعض الحالات، قد تحتاج إلى ضبط أداء برنامج الحماية من الفيروسات من Microsoft Defender بينما يقوم بفحص ملفات ومجلدات معينة. محلل الأداء هو أداة سطر أوامر PowerShell تساعد على تحديد الملفات وملحقات الملفات والعمليات التي قد تتسبب في حدوث مشاكل في الأداء على نقاط النهاية الفردية. يمكن استخدام هذه المعلومات لتقييم مشاكل الأداء بشكل أفضل وتطبيق إجراءات المعالجة.

تتضمن بعض الخيارات التي يجب تحليلها ما يلي:

- أهم الملفات التي تؤثر على وقت الفحص
- أهم العمليات التي تؤثر على وقت الفحص
- ملحقات الملفات العلوية التي تؤثر على وقت الفحص
- تركيبات – على سبيل المثال، الملفات العلوية لكل ملحق، عمليات الفحص العليا لكل ملف، عمليات الفحص العليا لكل ملف لكل عملية

## <a name="running-performance-analyzer"></a>محلل الأداء قيد التشغيل

تتضمن العملية عالية المستوى لتشغيل محلل الأداء الخطوات التالية:

1. تشغيل محلل الأداء لتجميع تسجيل أداء برنامج الحماية من الفيروسات من Microsoft Defender الأحداث على نقطة النهاية.

   > [!NOTE]
   > يتم تسجيل برنامج الحماية من الفيروسات من Microsoft Defender من النوع **Microsoft-Antimalware-Engine** من خلال محلل الأداء.

2. تحليل نتائج الفحص باستخدام تقارير تسجيل مختلفة.

## <a name="using-performance-analyzer"></a>استخدام محلل الأداء

لبدء تسجيل أحداث النظام، افتح PowerShell في الوضع الإداري واتبع الخطوات التالية:

1. تشغيل الأمر التالي لبدء التسجيل:

   `New-MpPerformanceRecording -RecordTo <recording.etl>`
 
    حيث `-RecordTo` تحدد المعلمة موقع المسار الكامل حيث يتم حفظ ملف التتبع. لمزيد من المعلومات حول cmdlet، راجع برنامج الحماية من الفيروسات من Microsoft Defender [cmdlets](/powershell/module/defender).

2. إذا كانت هناك عمليات أو خدمات تعتقد أنها تؤثر على الأداء، فعيد إنتاج الحالة بتنفيذ المهام ذات الصلة.

3. اضغط **على ENTER** لإيقاف التسجيل وحفظه، أو **Ctrl+C** لإلغاء التسجيل.

4. تحليل النتائج باستخدام معلمة `Get-MpPerformanceReport`محلل الأداء. على سبيل المثال `Get-MpPerformanceReport -Path <recording.etl> -TopFiles 3 -TopScansPerFile 10`، عند تنفيذ الأمر، يتم تزويد المستخدم بلائحة من أهم عشر عمليات فحص للملفات ال 3 العلوية التي تؤثر على الأداء. 

لمزيد من المعلومات حول معلمات سطر الأوامر وخياراته، راجع [New-MpPerformanceRecording](#new-mpperformancerecording) و [Get-MpPerformanceReport](#get-mpperformancereport).

> [!NOTE]
> عند تشغيل تسجيل، إذا حصلت على الخطأ "يتعذر بدء تسجيل الأداء لأن Windows مسجل الأداء قيد التسجيل"، ف قم بتشغيل الأمر التالي لإيقاف التتبع الموجود باستخدام الأمر الجديد: **wpr -cancel-instancename MSFT_MpPerformanceRecording**

### <a name="performance-tuning-data-and-information"></a>بيانات ومعلومات ضبط الأداء

استنادا إلى الاستعلام، سيكون المستخدم قادرا على عرض البيانات الخاصة بعدد الفحص والمدة (الإجمالي/الحد الأدنى/المتوسط/max/median) والمسار وعملية الفحص والسبب. تعرض الصورة أدناه عينة الإخراج لاستعلام بسيط لأهم 10 ملفات للفحص. 

:::image type="content" source="images/example-output.png" alt-text="مثال إخراج لاستعلام TopFiles أساسي":::

### <a name="additional-functionality-exporting-and-converting-to-csv-and-json"></a>وظائف إضافية: التصدير والتحوير إلى CSV و JSON

يمكن أيضا تصدير نتائج محلل الأداء وتحويلها إلى ملف CSV أو JSON.
للحصول على أمثلة تصف عملية "التصدير" و"التحويل" من خلال الرموز العينة، انظر أدناه.

#### <a name="for-csv"></a>ل CSV

- **للتصدير**: `(Get-MpPerformanceReport -Path:.\Repro-Install.etl -Topscans:1000). TopScans | Export-CSV -Path:.\Repro-Install-Scans.csv -Encoding:UTF8 -NoTypeInformation`

- **للتحويل**: `(Get-MpPerformanceReport -Path:.\Repro-Install.etl -Topscans:100). TopScans | ConvertTo-Csv -NoTypeInformation`

#### <a name="for-json"></a>ل JSON

- **للتحويل**: `(Get-MpPerformanceReport -Path:.\Repro-Install.etl -Topscans:1000). TopScans | ConvertTo-Json -Depth:1`

### <a name="requirements"></a>المتطلبات
برنامج الحماية من الفيروسات من Microsoft Defender أداء محلل الأداء على المتطلبات الأساسية التالية:

- الإصدارات Windows: Windows 10 و Windows 11 و Windows Server 2016 والإصدارات الأحدث
- إصدار النظام الأساسي: 4.18.2108.7+
- إصدار PowerShell: PowerShell الإصدار 5.1، PowerShell ISE، Remote PowerShell (4.18.2201.10+)، PowerShell 7.x (4.18.2201.10+)

## <a name="powershell-reference"></a>مرجع PowerShell
هناك نوعان جديدان من Cmdlets PowerShell يستخدمان لضبط أداء برنامج الحماية من الفيروسات من Microsoft Defender: 

- [New-MpPerformanceRecording](#new-mpperformancerecording)
- [Get-MpPerformanceReport](#get-mpperformancereport)


### <a name="new-mpperformancerecording"></a>New-MpPerformanceRecording

يصف القسم التالي مرجع الأمر cmdlet الجديد في PowerShell New-MpPerformanceRecording. يجمع cmdlet هذا تسجيل أداء برنامج الحماية من الفيروسات من Microsoft Defender المسح الضوئي.

#### <a name="syntax-new-mpperformancerecording"></a>بناء الجملة: New-MpPerformanceRecording

```powershell
New-MpPerformanceRecording -RecordTo <String >
```

#### <a name="description-new-mpperformancerecording"></a>الوصف: New-MpPerformanceRecording
يجمع `New-MpPerformanceRecording` cmdlet تسجيل أداء برنامج الحماية من الفيروسات من Microsoft Defender المسح الضوئي. تحتوي تسجيلات الأداء هذه على أحداث عملية Microsoft-Antimalware-Engine وNT kernel ويمكن تحليلها بعد تجميعها باستخدام [الأمر cmdlet Get-MpPerformanceReport](#get-mpperformancereport) .

يوفر `New-MpPerformanceRecording` الأمر cmdlet هذا نظرة ثاقبة على الملفات التي تسبب مشاكل قد تتسبب في حدوث انخفاض في أداء برنامج الحماية من الفيروسات من Microsoft Defender. يتم توفير هذه الأداة "AS IS"، ولا تهدف إلى تقديم اقتراحات حول الاستثناءات. يمكن أن تقلل الاستثناءات مستوى الحماية على نقاط النهاية. يجب تعريف الاستثناءات، إن وجدت، بحذر.

لمزيد من المعلومات حول محلل الأداء، راجع [مستندات محلل](/windows-hardware/test/wpt/windows-performance-analyzer) الأداء.

> [!IMPORTANT]
> يتطلب الأمر cmdlet هذا امتيازات المسؤول المرتفعة.

**إصدارات نظام التشغيل المعتمدة**

Windows الإصدار 10 والإصدارات الأحدث.

> [!NOTE]
> تتوفر هذه الميزة بدءا من إصدار النظام الأساسي 4.18.2108.X والإصدارات الأحدث.

#### <a name="examples-new-mpperformancerecording"></a>أمثلة: New-MpPerformanceRecording

##### <a name="example-1-collect-a-performance-recording-and-save-it"></a>المثال 1: تجميع تسجيل أداء وحفظه

```powershell
New-MpPerformanceRecording -RecordTo:.\Defender-scans.etl
```

يجمع الأمر أعلاه تسجيل أداء ويحفظه في المسار المحدد: **.\Defender-scans.etl**.

##### <a name="example-2-collect-a-performance-recording-for-remote-powershell-session"></a>المثال 2: تجميع تسجيل أداء لجلسة PowerShell البعيدة

```powershell
$s = New-PSSession -ComputerName Server02 -Credential Domain01\User01
New-MpPerformanceRecording -RecordTo C:\LocalPathOnServer02\trace.etl -Session $s
```

يجمع الأمر أعلاه تسجيل أداء على Server02 (كما هو محدد بواسطة الوسيطة $s من المعلمة Session) ويحفظه في المسار المحدد: **C:\LocalPathOnServer02\trace.etl** على Server02.

#### <a name="parameters-new-mpperformancerecording"></a>المعلمات: New-MpPerformanceRecording

##### <a name="-recordto"></a>-RecordTo
يحدد الموقع الذي يتم فيه حفظ تسجيل أداء Microsoft Defender Antimalware.

```yaml
Type: String
Position: Named
Default value: None
Accept pipeline input: False 
Accept wildcard characters: False
```

##### <a name="-session"></a>-Session 
يحدد كائن PSSession الذي يتم فيه إنشاء برنامج الحماية من الفيروسات من Microsoft Defender تسجيل الأداء وحفظه. عند استخدام هذه المعلمة، تشير المعلمة RecordTo إلى المسار المحلي على الجهاز البعيد. متوفر مع إصدار النظام الأساسي ل Defender 4.18.2201.10.

```yaml
Type: PSSession[]
Position: 0
Default value: None
Accept pipeline input: False 
Accept wildcard characters: False
```

### <a name="get-mpperformancereport"></a>Get-MpPerformanceReport

يصف القسم التالي Get-MpPerformanceReport Cmdlet في PowerShell. تحليل تسجيل أداء برنامج الحماية من الفيروسات من Microsoft Defender (MDAV) والتقارير حوله.

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
```

#### <a name="description-get-mpperformancereport"></a>الوصف: Get-MpPerformanceReport
`Get-MpPerformanceReport` يحلل cmdlet تسجيل أداء برنامج الحماية من الفيروسات من Microsoft Defender تم تجميعه مسبقا ([New-MpPerformanceRecording](#new-mpperformancerecording)) ويسجل مسارات الملفات وملحقات الملفات والعمليات التي تتسبب في التأثير الأعلى على برنامج الحماية من الفيروسات من Microsoft Defender المسح الضوئي.

يوفر محلل الأداء نظرة ثاقبة حول الملفات التي قد تتسبب في حدوث انخفاض في أداء برنامج الحماية من الفيروسات من Microsoft Defender. يتم توفير هذه الأداة "AS IS" ولا تهدف إلى تقديم اقتراحات حول الاستثناءات. يمكن أن تقلل الاستثناءات مستوى الحماية على نقاط النهاية. يجب تعريف الاستثناءات، إن وجدت، بحذر.

لمزيد من المعلومات حول محلل الأداء، راجع [مستندات محلل](/windows-hardware/test/wpt/windows-performance-analyzer) الأداء.

**إصدارات نظام التشغيل المعتمدة**

Windows الإصدار 10 والإصدارات الأحدث.

> [!NOTE]
> تتوفر هذه الميزة بدءا من إصدار النظام الأساسي 4.18.2108.X والإصدارات الأحدث.

#### <a name="examples-get-mpperformancereport"></a>أمثلة: Get-MpPerformanceReport

##### <a name="example-1-single-query"></a>مثال 1: استعلام مفرد 

```powershell
Get-MpPerformanceReport -Path:.\Defender-scans.etl -TopScans:20
```

##### <a name="example-2-multiple-queries"></a>المثال 2: استعلامات متعددة 

```powershell
Get-MpPerformanceReport -Path:.\Defender-scans.etl -TopFiles:10 -TopExtensions:10 -TopProcesses:10 -TopScans:10
```

##### <a name="example-3-nested-queries"></a>المثال 3: الاستعلامات المتداخلة 

```powershell
Get-MpPerformanceReport -Path:.\Defender-scans.etl -TopProcesses:10 -TopExtensionsPerProcess:3 -TopScansPerExtensionPerProcess:3
```

##### <a name="example-4-using--minduration-parameter"></a>المثال 4: استخدام المعلمة -MinDuration

```powershell
Get-MpPerformanceReport -Path:.\Defender-scans.etl -TopScans:100 -MinDuration:100ms
```

#### <a name="parameters-get-mpperformancereport"></a>المعلمات: Get-MpPerformanceReport

##### <a name="-minduration"></a>-MinDuration
تحديد الحد الأدنى لمدة أي مدد مسح ضوئي أو إجمالي للملفات والملحقات والعمليات المضمنة في التقرير؛ يقبل قيما مثل  **0,1234567 ثانية** أو **0,1234 ثانية** أو **0,1us** أو TimeSpan صالح.

```yaml
Type: String
Position: Named
Default value: None
Accept pipeline input: False 
Accept wildcard characters: False
```

##### <a name="-path"></a>-Path
يحدد المسار (المسارات) إلى موقع واحد أو أكثر.

```yaml
Type: String
Position: 0
Default value: None
Accept pipeline input: True
Accept wildcard characters: False
```

### <a name="-topextensions"></a>-TopExtensions 
يحدد عدد الملحقات العليا التي يجب إخراجها، تم فرزها حسب "المدة".

```yaml
Type: Int32
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <a name="-topextensionsperprocess"></a>-TopExtensionsPerProcess 
يحدد عدد الملحقات العليا التي يجب إخراجها لكل عملية عليا، تم فرزها حسب "المدة".

```yaml
Type: Int32
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <a name="-topfiles"></a>-TopFiles
يطلب تقرير ملفات عليا يحدد عدد الملفات الهامة المطلوب إخراجها، تم فرزها حسب "المدة".


```yaml
Type: Int32
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <a name="-topfilesperextension"></a>-TopFilesPerExtension 
يحدد عدد الملفات العليا التي يجب إخراجها لكل ملحق أعلى، تم فرزها حسب "المدة".


```yaml
Type: Int32
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <a name="-topfilesperprocess"></a>-TopFilesPerProcess
يحدد عدد الملفات الهامة التي يجب إخراجها لكل عملية عليا، تم فرزها حسب "المدة".

```yaml
Type: Int32
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <a name="-topprocesses"></a>-TopProcesses
يطلب تقرير العمليات العليا، كما يحدد عدد العمليات العليا المطلوب إخراجها، تم فرزها حسب "المدة".

```yaml
Type: Int32
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <a name="-topprocessesperextension"></a>-TopProcessesPerExtension 
يحدد عدد العمليات العليا التي يجب إخراجها لكل ملحق أعلى، تم فرزها حسب "المدة".


```yaml
Type: Int32
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```


### <a name="-topprocessesperfile"></a>-TopProcessesPerFile
يحدد عدد العمليات العليا التي يجب إخراجها لكل ملف أعلى، تم فرزها حسب "المدة".


```yaml
Type: Int32
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <a name="-topscans"></a>-TopScans
طلب تقرير فحص أعلى يحدد عدد عمليات الفحص العليا المطلوب إخراجها، تم فرزها حسب "المدة".


```yaml
Type: Int32
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```


### <a name="-topscansperextension"></a>-TopScansPerExtension
يحدد عدد عمليات الفحص العليا التي يجب إخراجها لكل ملحق أعلى، تم فرزها حسب "المدة".


```yaml
Type: Int32
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```


### <a name="-topscansperextensionperprocess"></a>-TopScansPerExtensionPerProcess 
يحدد عدد عمليات الفحص العليا التي يجب إخراجها لكل ملحق أعلى لكل عملية عليا، تم فرزها حسب "المدة".


```yaml
Type: Int32
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```


### <a name="-topscansperfile"></a>-TopScansPerFile
يحدد عدد عمليات الفحص العليا التي يجب إخراجها لكل ملف أعلى، تم فرزها حسب "المدة".


```yaml
Type: Int32
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <a name="-topscansperfileperextension"></a>-TopScansPerFilePerExtension 
يحدد عدد عمليات الفحص العليا التي يجب إخراجها لكل ملف أعلى لكل ملحق أعلى، تم فرزه حسب "المدة".


```yaml
Type: Int32
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```


### <a name="-topscansperfileperprocess"></a>-TopScansPerFilePerProcess 
يحدد عدد عمليات الفحص العليا للحصول على الإخراج لكل ملف أعلى لكل عملية عليا، تم فرزها حسب "المدة".


```yaml
Type: Int32
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```


### <a name="-topscansperprocess"></a>-TopScansPerProcess 
يحدد عدد عمليات الفحص العليا التي يجب إخراجها لكل عملية عليا في تقرير العمليات العليا، الذي تم فرزه حسب "المدة".


```yaml
Type: Int32
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <a name="-topscansperprocessperextension"></a>-TopScansPerProcessPerExtension
يحدد عدد عمليات الفحص العليا للحصول على الإخراج لكل عملية عليا لكل ملحق أعلى، تم فرزها حسب "المدة".


```yaml
Type: Int32
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <a name="-topscansperprocessperfile"></a>-TopScansPerProcessPerFile
يحدد عدد عمليات الفحص العليا للحصول على الإخراج لكل عملية عليا لكل ملف أعلى، تم فرزها حسب "المدة".


```yaml
Type: Int32
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```
