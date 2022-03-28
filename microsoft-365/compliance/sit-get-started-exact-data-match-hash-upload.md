---
title: قم بتهش جدول مصدر المعلومات الحساس وتحميله للحصول على بيانات دقيقة تتطابق مع أنواع المعلومات الحساسة
f1.keywords:
- NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
audience: Admin
ms.topic: how-to
ms.service: O365-seccomp
ms.date: ''
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
search.appverid:
- MOE150
- MET150
description: يطابق جدول مصدر المعلومات الحساس وتحميله للبيانات الدقيقة أنواع المعلومات الحساسة.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 8d3effe3d46375ffcaec268e4b3fc6d53fc5044e
ms.sourcegitcommit: 3fb76db6b34e24569417f4c8a41b99f46a780389
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/17/2022
ms.locfileid: "63575142"
---
# <a name="hash-and-upload-the-sensitive-information-source-table-for-exact-data-match-sensitive-information-types"></a>قم بتهش جدول مصدر المعلومات الحساس وتحميله للحصول على بيانات دقيقة تتطابق مع أنواع المعلومات الحساسة

توضح لك هذه المقالة كيفية تزحزح جدول مصدر المعلومات الحساس وتحميله.

## <a name="hash-and-upload-the-sensitive-information-source-table"></a>تهش جدول مصدر المعلومات الحساس وتحميله

في هذه المرحلة، يمكنك:

1. إعداد مجموعة أمان مخصصة حساب مستخدم
2. إعداد أداة Upload EDM
3. استخدم أداة Upload EDM لتفيش الجدول، مع قيمة ملح، جدول مصدر المعلومات الحساس، وتحميله.

يمكن القيام بالتحميل والتقحم باستخدام كمبيوتر واحد أو يمكنك فصل خطوة التكهيل عن خطوة التحميل لمزيد من الأمان.

إذا كنت تريد اانتهاك وتحميلها من كمبيوتر واحد، ستحتاج إلى القيام بذلك من كمبيوتر يمكنه الاتصال مباشرة Microsoft 365 المستأجر. يتطلب هذا أن يكون ملف جدول مصدر المعلومات الحساسة للنص واضحا على هذا الكمبيوتر لتقنصه.

إذا كنت لا تريد عرض ملف جدول مصدر المعلومات الحساسة للنص الواضح على كمبيوتر الوصول المباشر، يمكنك تزحزحه على كمبيوتر في موقع آمن ثم نسخ ملف هاش وملف الملح إلى كمبيوتر يمكنه الاتصال مباشرة إلى مستأجر Microsoft 365 لتحميله. في سيناريو التحميل والتقشف المفصولين، ستحتاج إلى EDMUploadAgent على جهازي الكمبيوتر.

> [!IMPORTANT]
> إذا استخدمت معالج مخطط مطابقة البيانات الدقيقة ونوع المعلومات الحساسة لإنشاء ملف المخطط، فيجب تنزيل المخطط لهذا الإجراء إذا لم  تكن قد فعلت ذلك بعد. راجع [تصدير ملف مخطط EDM بتنسيق XML](sit-get-started-exact-data-match-create-schema.md#export-of-the-edm-schema-file-in-xml-format).

> [!NOTE]
> إذا كانت مؤسستك قد قمت بإعداد ["مفتاح العميل"](customer-key-overview.md) Microsoft 365 المستأجر، فإن تطابق البيانات الدقيق سيستخدم وظائف التشفير الخاصة به تلقائيا. يتوفر هذا فقط للمستأجرين المرخصين في E5 في السحابة التجارية.

### <a name="best-practices"></a>أفضل الممارسات

افصل بين عمليات تفرق البيانات الحساسة وتحميلها بحيث يمكنك عزل أي مشاكل في العملية بسهولة أكبر.
 
بعد الإنتاج، احتفظ بخطوتين منفصلتين في معظم الحالات. يؤدي تنفيذ عملية التكهيل على كمبيوتر معزول ثم نقل الملف للتحميل إلى كمبيوتر مواجه للإنترنت إلى ضمان عدم توفر البيانات الفعلية أبدا في نموذج نصي واضح في كمبيوتر ربما تم اختراقه بسبب اتصاله بالإنترنت.

### <a name="ensure-your-sensitive-data-table-doesnt-have-formatting-issues"></a>تأكد من عدم وجود مشاكل في التنسيق في جدول البيانات الحساسة. 

قبل أن تقوم بتقحم البيانات الحساسة وتحميلها، قم بالبحث للتحقق من وجود أحرف خاصة قد تسبب مشاكل في تحليل المحتوى. يمكنك التحقق من أن الجدول بتنسيق مناسب للاستخدام مع EDM باستخدام وكيل تحميل EDM مع بناء الجملة التالي:

```powershell
EdmUploadAgent.exe /ValidateData /DataFile [data file] /Schema [schema file] 
```

إذا كانت الأداة تشير إلى عدم تطابق في عدد الأعمدة، فقد يعود سبب ذلك إلى وجود فهامات أو أحرف اقتباس داخل القيم الموجودة في الجدول والتي يتم الخلط بينها وبين قيم مفهاة الأعمدة. ما لم تكن تحيط بقيمة كاملة، يمكن أن تتسبب علامات الاقتباس الفردية المزدوجة في تحديد الأداة بشكل غير جيد حيث يبدأ عمود فردي أو ينتهي. 

**إذا وجدت أحرف اقتباس مفردة أو مزدوجة تحيط بالقيم الكاملة**: يمكنك تركها كما هي.

إذا وجدت أحرف اقتباس مفردة أو فواصل داخل **قيمة: على** سبيل المثال، اسم الشخص توم أو س-رفنهاج المدينة الذي يبدأ ب حرف فاصلة عليا، ستحتاج إلى تعديل عملية تصدير البيانات المستخدمة لإنشاء جدول المعلومات الحساس لإحاطة مثل هذه الأعمدة ب علامات اقتباس مزدوجة.

**إذا تم العثور على أحرف** اقتباس مزدوجة داخل القيم، فقد يكون من الأفضل استخدام التنسيق المحدد ب علامة الجدول الجدول الأقل عرضة لمثل هذه المشاكل.

### <a name="prerequisites"></a>المتطلبات الأساسية

- حساب العمل أو المدرسة Microsoft 365 التي سيتم إضافتها إلى مجموعة أمان **EDMDataUploaders\_**
- جهاز Windows 10 أو Windows Server 2016 مع إصدار .NET 4.6.2 <!--4.7.2 un comment this around 9/29-->لتشغيل EDMUploadAgent
- دليل على جهاز التحميل ل:
  - [وكيل Upload EDM](#links-to-edm-upload-agent-by-subscription-type)
  - ملف العنصر الحساس بتنسيق .csv أو .tsv أو pipe (|)،PatientRecords.csvفي الأمثلة ****
  - مفيش الإخراج وملفات الملح التي تم إنشاؤها في هذا الإجراء
  - اسم موقع البيانات من ملف **edm.xml** ، على سبيل المثال `PatientRecords`

#### <a name="set-up-the-security-group-and-user-account"></a>إعداد مجموعة الأمان حساب المستخدم

1. كمسؤول عام، انتقل إلى مركز الإدارة باستخدام الارتباط المناسب لاشتراكك وأنشئ مجموعة أمان [](/office365/admin/email/create-edit-or-delete-a-security-group) **تسمى EDMDataUploaders\_**.[](sit-get-started-exact-data-match-based-sits-overview.md#portal-links-for-your-subscription)

2. أضف مستخدما واحدا أو أكثر إلى مجموعة أمان **EDMDataUploaders\_**. (سيتولى هؤلاء المستخدمون إدارة قاعدة بيانات المعلومات الحساسة.)

### <a name="hash-and-upload-from-one-computer"></a>اانتهاك وتحميلها من كمبيوتر واحد

يجب أن يكون لهذا الكمبيوتر حق الوصول المباشر إلى Microsoft 365 المستأجر.

> [!NOTE]
> قبل بدء هذا الإجراء، تأكد من أنك عضو في مجموعة أمان **EDMDataUploaders\_**.

> [!TIP] 
>بشكل اختياري، يمكنك تشغيل التحقق من الصحة مقابل ملف جدول مصدر المعلومات الحساس للتحقق من وجود أخطاء قبل التحميل عن طريق تشغيل:
>
> `EdmUploadAgent.exe /ValidateData /DataFile [data file] /Schema [schema file]`
>
> لمزيد من المعلومات حول جميع المعلمات EdmUploadAgent.exe التي يتم تشغيلها
>
> `EdmUploadAgent.exe /?`

#### <a name="links-to-edm-upload-agent-by-subscription-type"></a>ارتباطات إلى وكيل تحميل EDM حسب نوع الاشتراك

- [التجاري + سحابة القطاع الحكومي](https://go.microsoft.com/fwlink/?linkid=2088639) - يجب على معظم العملاء التجاريين استخدام هذا
- [سحابة القطاع الحكومي-High](https://go.microsoft.com/fwlink/?linkid=2137521) - هذا خاص لمشتركي السحابة الحكومية عالية الأمان
- [DoD](https://go.microsoft.com/fwlink/?linkid=2137807) - هذا خاص لعملاء السحابة في وزارة الدفاع الأمريكية

1. إنشاء دليل عمل ل EDMUploadAgent. على سبيل المثال **، C:\EDM\Data**. ضع الملف **PatientRecords.csv** هناك.

2. قم بتنزيل Upload [EDM](#links-to-edm-upload-agent-by-subscription-type) المناسب وتثبيته لاشتراكك في الدليل الذي أنشأته في الخطوة 1.

   > [!NOTE]
   > تم تحديث EDMUploadAgent في الارتباطات أعلاه لإضافة قيمة ملح تلقائيا إلى البيانات المفصلة. بدلا من ذلك، يمكنك توفير قيمة الملح الخاصة بك. بمجرد استخدام هذا الإصدار، لن تتمكن من استخدام الإصدار السابق من EDMUploadAgent.
   >
   > يمكنك تحميل البيانات باستخدام EDMUploadAgent إلى أي مخزن بيانات معين مرتين فقط في اليوم.

3. قم ب تخويل Upload EDM، وافتح نافذة موجه الأوامر كمسؤول، والتبديل إلى **دليل C:\EDM\Data** ثم قم بتشغيل الأمر التالي:

   `EdmUploadAgent.exe /Authorize`

> [!IMPORTANT]
> يجب تشغيل **EdmUploadAgent** من المجلد حيث تم تثبيته، مع الإشارة إلى المسار الكامل إلى ملفات البيانات. 

4. سجل الدخول باستخدام حساب العمل أو المدرسة Microsoft 365 الذي تم إضافته إلى مجموعة EDM_DataUploaders الأمان. يتم استخراج معلومات المستأجر من حساب المستخدم للاتصال.

   اختياري: إذا استخدمت معالج مخطط مطابقة البيانات بدقة ونوع المعلومات الحساسة لإنشاء المخطط، فيجب تنزيله لاستخدامه في  هذه الإجراءات إذا لم تكن قد قمت بذلك بالفعل. تشغيل هذا الأمر في نافذة موجه الأوامر:

   ```dos
   EdmUploadAgent.exe /SaveSchema /DataStoreName <schema name> /OutputDir <path to output folder>
   ```

5. لتجريب البيانات الحساسة وتحميلها، قم بتشغيل الأمر التالي في نافذة موجه الأوامر:

   ```dos
   EdmUploadAgent.exe /UploadData /DataStoreName [DS Name] /DataFile [data file] /HashLocation [hash file location] /Schema [Schema file] /ColumnSeparator ["{Tab}"|"|"] /AllowedBadLinesPercentage [value]
   ```
   > [!NOTE]
> التنسيق الافتراضي لملف البيانات الحساسة هو قيم مفصولة بفصول. يمكنك تحديد ملف مفصول ب علامة تبويب عن طريق الإشارة إلى الخيار "{Tab}" باستخدام المعلمة /ColumnSeparator، أو يمكنك تحديد ملف مفصول بواسطة توجيه الخيار "|".

   مثال: **EdmUploadAgent.exe /UploadData /DataStoreName PatientRecords /DataFile C:\Edm\Hash\PatientRecords.csv /HashLocation C:\Edm\Hash /Schema edm.xml /AllowedBadLinesPercentage 5**

إذا كان جدول المعلومات الحساسة به بعض القيم التي تم تنسيقها بشكل غير صحيح، ولكنك تريد استيراد البيانات المتبقية مع تجاهل الصفوف غير الصالحة على أي حال، يمكنك استخدام *المعلمة /AllowedBadLinesPercentage* في الأمر. يحدد المثال أعلاه عتبة خمسة بالمائة. وهذا يعني أن الأداة ستتقحم جدول المعلومات الحساسة وترفعه حتى لو كانت نسبة تصل إلى خمسة في المئة من الصفوف غير صالحة. 

سيضيف هذا الأمر تلقائيا قيمة ملح تم إنشاؤها عشوائيا إلى ها هوة لمزيد من الأمان. بشكل اختياري، إذا كنت تريد استخدام قيمة الملح الخاصة بك، أضف **/Salt <saltvalue>** إلى الأمر. يجب أن تكون هذه القيمة 64 حرفا في الطول ويمكن أن تحتوي فقط على أحرف أ-ي و0-9 أحرف.

6. تحقق من حالة التحميل عن طريق تشغيل هذا الأمر:

   ```dos
   EdmUploadAgent.exe /GetSession /DataStoreName \<DataStoreName\>
   ```

   مثال: **EdmUploadAgent.exe /GetSession /DataStoreName PatientRecords**

   ابحث عن الحالة لتكون في **ProcessingInProgress**. تحقق مرة أخرى كل بضع دقائق حتى تتغير الحالة إلى **مكتمل**. بمجرد اكتمال الحالة، تكون بيانات EDM جاهزة للاستخدام. استنادا إلى حجم ملف جدول مصدر المعلومات الحساس، قد يستغرق ذلك بضع دقائق إلى عدة ساعات. 

> [!TIP]
> إذا كنت تريد أن يتم إعلامك بمجرد أن تكون البيانات الحساسة التي تم تحميلها جاهزة للاستخدام، فاتبع الإجراءات الواردة في إنشاء إعلامات لأنشطة [مطابقة البيانات بدقة](sit-edm-notifications-activities.md#create-notifications-for-exact-data-match-activities).

### <a name="separate-hash-and-upload"></a>فصل هاش وتحميله

تنفيذ الهاش على جهاز كمبيوتر في بيئة آمنة. يجب أن يكون **EDMUploadAgent مثبتا** على جهازي الكمبيوتر.

اختياري: إذا استخدمت معالج مخطط مطابقة البيانات بدقة ونوع المعلومات الحساسة لإنشاء المخطط ولم تكن قد قمت بتنزيلها بالفعل، ف قم بتشغيل الأمر التالي في نافذة موجه الأوامر لتنزيل الملف بتنسيق XML:

```dos
EdmUploadAgent.exe /SaveSchema /DataStoreName <schema name> /OutputDir <path to output folder>
````

1. على الكمبيوتر في البيئة الآمنة، تشغيل الأمر التالي في نوافذ موجه الأوامر:

   ```dos
   EdmUploadAgent.exe /CreateHash /DataFile [data file] /HashLocation [hash file location] /Schema [Schema file] /AllowedBadLinesPercentage [value]
   ```

   على سبيل المثال:

   ```dos
   EdmUploadAgent.exe /CreateHash /DataFile C:\Edm\Data\PatientRecords.csv /HashLocation C:\Edm\Hash /Schema edm.xml /AllowedBadLinesPercentage 5
   ```

> [!NOTE]
> التنسيق الافتراضي لملف البيانات الحساسة هو قيم مفصولة بفصول. يمكنك تحديد ملف مفصول ب علامة تبويب عن طريق الإشارة إلى الخيار "{Tab}" باستخدام المعلمة /ColumnSeparator، أو يمكنك تحديد ملف مفصول بواسطة توجيه الخيار "|".


   سيخرج هذا ملفا مفواصلا وملفا ملحا بهذه الملحقات إذا لم تحدد **الخيار /Salt <saltvalue>** :

   - . EdmHash
   - . EdmSalt


2. انسخ هذه الملفات بطريقة آمنة إلى الكمبيوتر الذي تستخدمه لتحميل ملف جدول مصدر المعلومات الحساس (PatientRecords) إلى المستأجر.

3. قم ب تخويل Upload EDM، وافتح نافذة موجه الأوامر كمسؤول، والتبديل إلى **دليل C:\EDM\Data** ثم قم بتشغيل الأمر التالي:

   `EdmUploadAgent.exe /Authorize`

> [!IMPORTANT]
> يجب تشغيل **EdmUploadAgent** من المجلد حيث تم تثبيته، مع الإشارة إلى المسار الكامل إلى ملفات البيانات. 

4. سجل الدخول باستخدام حساب العمل أو المدرسة Microsoft 365 الذي تم إضافته إلى مجموعة EDM_DataUploaders الأمان. يتم استخراج معلومات المستأجر من حساب المستخدم للاتصال.

5. لتحميل البيانات المفوبة، قم بتشغيل الأمر التالي في Windows موجه الأوامر:

   ```dos
   EdmUploadAgent.exe /UploadHash /DataStoreName \<DataStoreName\> /HashFile \<HashedSourceFilePath\ /ColumnSeparator ["{Tab}"|"|"]
   ```

   على سبيل المثال:

   ```dos
   EdmUploadAgent.exe /UploadHash /DataStoreName PatientRecords /HashFile C:\\Edm\\Hash\\**PatientRecords.EdmHash**
   ```

6. للتحقق من تحميل البيانات الحساسة، قم بتشغيل الأمر التالي في نافذة موجه الأوامر:

   ```dos
   EdmUploadAgent.exe /GetDataStore
   ```
   سترى قائمة مخازن البيانات ومتى تم تحديثها آخر مرة.

7. إذا كنت تريد رؤية كل تحميلات البيانات إلى مخزن معين، ف قم بتشغيل الأمر التالي في موجه أوامر Windows لرؤية قائمة بكل مخازن البيانات ومتى تم تحديثها:

   ```dos
   EdmUploadAgent.exe /GetSession /DataStoreName <DataStoreName>
   ```
     
## <a name="next-step"></a>الخطوة التالية

- [إنشاء بيانات دقيقة تتطابق مع نوع المعلومات الحساسة/حزمة القاعدة](sit-get-started-exact-data-match-create-rule-package.md#create-exact-data-match-sensitive-information-typerule-package)

