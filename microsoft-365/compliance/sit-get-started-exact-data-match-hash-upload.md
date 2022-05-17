---
title: تجزئة وتحميل جدول مصدر المعلومات الحساسة للحصول على بيانات مطابقة تماماً لأنواع المعلومات الحساسة
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
description: قم بتجزئة جدول مصدر المعلومات الحساسة وتحميله لتطابق البيانات الدقيقة مع أنواع المعلومات الحساسة.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: d3c45c618caad24084ee9c85410be886863dd733
ms.sourcegitcommit: 9255a7e8b398f92d8dae09886ae95dc8577bf29a
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 05/17/2022
ms.locfileid: "65437624"
---
# <a name="hash-and-upload-the-sensitive-information-source-table-for-exact-data-match-sensitive-information-types"></a>تجزئة وتحميل جدول مصدر المعلومات الحساسة للحصول على بيانات مطابقة تماماً لأنواع المعلومات الحساسة

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

توضح لك هذه المقالة كيفية تجزئة جدول مصدر المعلومات الحساسة وتحميله.

## <a name="hash-and-upload-the-sensitive-information-source-table"></a>تجزئة جدول مصدر المعلومات الحساسة وتحميله

في هذه المرحلة:

1. إعداد مجموعة أمان مخصصة وحساب مستخدم
2. إعداد أداة عامل Upload EDM
3. استخدم أداة عامل Upload EDM لتجزئة جدول مصدر المعلومات الحساسة، مع قيمة ملحية، وتحميله.

يمكن إجراء التجزئة والتحميل باستخدام كمبيوتر واحد أو يمكنك فصل خطوة التجزئة عن خطوة التحميل لمزيد من الأمان.

إذا كنت تريد التجزئة والتحميل من كمبيوتر واحد، فستحتاج إلى القيام بذلك من كمبيوتر يمكنه الاتصال مباشرة بمستأجر Microsoft 365. يتطلب ذلك وجود ملف جدول مصدر المعلومات الحساسة للنص الواضح على هذا الكمبيوتر للتجزئة.

إذا كنت لا تريد عرض ملف جدول مصدر المعلومات الحساسة للنص الواضح على كمبيوتر الوصول المباشر، يمكنك تجزئة الملف على كمبيوتر موجود في موقع آمن ثم نسخ ملف التجزئة وملف الملح إلى كمبيوتر يمكنه الاتصال مباشرة بمستأجر Microsoft 365 لتحميله. في سيناريو التجزئة والتحميل المنفصل، ستحتاج إلى EDMUploadAgent على كلا الكمبيوترين.

> [!IMPORTANT]
> إذا استخدمت مخطط مطابقة البيانات الدقيقة ومعالج نوع المعلومات الحساسة لإنشاء ملف المخطط، ***فيجب*** تنزيل المخطط لهذا الإجراء إذا لم تكن قد قمت بذلك بالفعل. انظر، [تصدير ملف مخطط EDM بتنسيق XML](sit-get-started-exact-data-match-create-schema.md#export-of-the-edm-schema-file-in-xml-format).

> [!NOTE]
> إذا قامت مؤسستك بإعداد [مفتاح العميل Microsoft 365 على مستوى المستأجر](customer-key-overview.md)، فستستفيد مطابقة البيانات الدقيقة من وظائف التشفير الخاصة بها تلقائيا. يتوفر هذا فقط للمستأجرين المرخصين E5 في السحابة التجارية.

### <a name="best-practices"></a>أفضل الممارسات

افصل عمليات التجزئة وتحميل البيانات الحساسة حتى تتمكن من عزل أي مشكلات في العملية بسهولة أكبر.

بمجرد الإنتاج، احتفظ بالخطوتين منفصلتين في معظم الحالات. يضمن تنفيذ عملية التجزئة على كمبيوتر معزول ثم نقل الملف للتحميل إلى كمبيوتر ذي واجهة إنترنت عدم توفر البيانات الفعلية أبدا في نموذج نص واضح في كمبيوتر قد يكون تم اختراقه بسبب اتصاله بالإنترنت.

### <a name="ensure-your-sensitive-data-table-doesnt-have-formatting-issues"></a>تأكد من عدم وجود مشاكل في التنسيق في جدول البيانات الحساسة

قبل تجزئة البيانات الحساسة وتحميلها، قم بإجراء بحث للتحقق من وجود أحرف خاصة قد تسبب مشاكل في تحليل المحتوى.
يمكنك التحقق من أن الجدول بتنسيق مناسب للاستخدام مع EDM باستخدام عامل تحميل EDM مع بناء الجملة التالي:

```powershell
EdmUploadAgent.exe /ValidateData /DataFile [data file] /Schema [schema file]
```

إذا كانت الأداة تشير إلى عدم تطابق في عدد الأعمدة، فقد يعود ذلك إلى وجود فواصل أو أحرف اقتباس داخل القيم في الجدول التي يتم الخلط بينها وبين محددات الأعمدة. إلا إذا كانت تحيط بقيمة كاملة، يمكن أن تؤدي علامات الاقتباس الفردية والمزدوجة إلى خطأ في تحديد مكان بدء عمود فردي أو نهايته.

**إذا وجدت أحرف اقتباس مفردة أو مزدوجة تحيط بالقيم الكاملة**: يمكنك تركها كما هي.

**إذا عثرت على أحرف اقتباس مفردة أو فواصل داخل قيمة**: على سبيل المثال اسم الشخص Tom O'Neil أو المدينة 's-Gravenhage التي تبدأ بحرف فاصلة أحادية، فستحتاج إلى تعديل عملية تصدير البيانات المستخدمة لإنشاء جدول المعلومات الحساسة لإحاطة هذه الأعمدة بعلامات اقتباس مزدوجة.

**إذا تم العثور على أحرف اقتباس مزدوجة داخل القيم**، فقد يكون من الأفضل استخدام التنسيق المحدد بعلامة جدولة للجدول الأقل عرضة لمثل هذه المشاكل.

### <a name="prerequisites"></a>المتطلبات الأساسية

- حساب العمل أو المؤسسة التعليمية Microsoft 365 التي ستتم إضافتها إلى مجموعة أمان **EDMDataUploaders\_**
- جهاز Windows 10 أو Windows Server 2016 مع الإصدار 4.6.2 من .NET <!--4.7.2 un comment this around 9/29-->لتشغيل EDMUploadAgent
- دليل على جهاز التحميل الخاص بك ل:
  - [وكيل Upload EDM](#links-to-edm-upload-agent-by-subscription-type)
  - ملف العنصر الحساس بتنسيق .csv أو .tsv أو توجيه (|)، **PatientRecords.csv** في الأمثلة
  - ملفات تجزئة الإخراج والملح التي تم إنشاؤها في هذا الإجراء
  - اسم مخزن البيانات من ملف **edm.xml** ، على سبيل المثال `PatientRecords`

#### <a name="set-up-the-security-group-and-user-account"></a>إعداد مجموعة الأمان وحساب المستخدم

1. كمسؤول عام، انتقل إلى مركز الإدارة باستخدام [الارتباط المناسب لاشتراكك](sit-get-started-exact-data-match-based-sits-overview.md#portal-links-for-your-subscription) [وأنشئ مجموعة أمان](/office365/admin/email/create-edit-or-delete-a-security-group) تسمى **EDMDataUploaders\_**.

2. إضافة مستخدم واحد أو أكثر إلى مجموعة أمان **EDMDataUploaders\_**. (سيقوم هؤلاء المستخدمون بإدارة قاعدة بيانات المعلومات الحساسة.)

### <a name="hash-and-upload-from-one-computer"></a>التجزئة والتحميل من كمبيوتر واحد

يجب أن يكون لهذا الكمبيوتر حق الوصول المباشر إلى مستأجر Microsoft 365.

> [!NOTE]
> قبل بدء هذا الإجراء، تأكد من أنك عضو في مجموعة أمان **EDMDataUploaders\_**.

> [!TIP]
>بشكل اختياري، يمكنك تشغيل التحقق من الصحة مقابل ملف جدول مصدر المعلومات الحساسة للتحقق من وجود أخطاء قبل التحميل عن طريق التشغيل:
>
> `EdmUploadAgent.exe /ValidateData /DataFile [data file] /Schema [schema file]`
>
> لمزيد من المعلومات حول تشغيل جميع المعلمات المدعومة EdmUploadAgent.exe
>
> `EdmUploadAgent.exe /?`

#### <a name="links-to-edm-upload-agent-by-subscription-type"></a>ارتباطات إلى عامل تحميل EDM حسب نوع الاشتراك

- [تجاري + سحابة القطاع الحكومي](https://go.microsoft.com/fwlink/?linkid=2088639) - يجب على معظم العملاء التجاريين استخدام هذا
- [سحابة القطاع الحكومي-High](https://go.microsoft.com/fwlink/?linkid=2137521) - هذا مخصص لمشتركي السحابة الحكومية ذات الأمان العالي
- [DoD](https://go.microsoft.com/fwlink/?linkid=2137807) - هذا مخصص لعملاء السحابة في وزارة الدفاع الأمريكية

1. إنشاء دليل عمل ل EDMUploadAgent. على سبيل المثال، **C:\EDM\Data**. ضع ملف **PatientRecords.csv** هناك.

2. قم بتنزيل وتثبيت [عامل Upload EDM](#links-to-edm-upload-agent-by-subscription-type) المناسب لاشتراكك في الدليل الذي أنشأته في الخطوة 1.

   > [!NOTE]
   > تم تحديث EDMUploadAgent في الارتباطات أعلاه لإضافة قيمة ملح تلقائيا إلى البيانات المتجزئة. بدلا من ذلك، يمكنك توفير قيمة الملح الخاصة بك. بمجرد استخدام هذا الإصدار، لن تتمكن من استخدام الإصدار السابق من EDMUploadAgent.
   >
   > يمكنك تحميل البيانات باستخدام EDMUploadAgent إلى أي مخزن بيانات معين مرتين فقط في اليوم.

3. قم بتخويل عامل Upload EDM، وافتح نافذة موجه الأوامر كمسؤول، وقم بالتبديل إلى دليل **C:\EDM\Data** ثم قم بتشغيل الأمر التالي:

   `EdmUploadAgent.exe /Authorize`

   > [!IMPORTANT]
   > يجب تشغيل **EdmUploadAgent** من المجلد حيث تم تثبيته، والإشارة إلى المسار الكامل لملفات البيانات.

4. سجل الدخول باستخدام حساب العمل أو المؤسسة التعليمية Microsoft 365 التي تمت إضافتها إلى مجموعة أمان EDM_DataUploaders. يتم استخراج معلومات المستأجر من حساب المستخدم لإجراء الاتصال.

   اختياري: إذا استخدمت مخطط مطابقة البيانات الدقيقة ومعالج نوع المعلومات الحساسة لإنشاء المخطط، ***فيجب*** تنزيله لاستخدامه في هذه الإجراءات إذا لم تكن قد قمت بذلك بالفعل. تشغيل هذا الأمر في نافذة موجه الأوامر:

   ```dos
   EdmUploadAgent.exe /SaveSchema /DataStoreName <schema name> /OutputDir <path to output folder>
   ```

5. لتجزئة البيانات الحساسة وتحميلها، قم بتشغيل الأمر التالي في نافذة موجه الأوامر:

   ```dos
   EdmUploadAgent.exe /UploadData /DataStoreName [DS Name] /DataFile [data file] /HashLocation [hash file location] /Schema [Schema file] /ColumnSeparator ["{Tab}"|"|"] /AllowedBadLinesPercentage [value]
   ```

   > [!NOTE]
   > التنسيق الافتراضي لملف البيانات الحساسة هو قيم مفصولة بفواصل. يمكنك تحديد ملف مفصول بعلامات تبويب عن طريق الإشارة إلى الخيار "{Tab}" باستخدام المعلمة /ColumnSeparator، أو يمكنك تحديد ملف مفصول أنبوبي بالإشارة إلى الخيار "|".
   >
   > على سبيل المثال:`EdmUploadAgent.exe /UploadData /DataStoreName PatientRecords /DataFile C:\Edm\Hash\PatientRecords.csv /HashLocation C:\Edm\Hash /Schema edm.xml /AllowedBadLinesPercentage 5`

   إذا كان جدول المعلومات الحساسة يحتوي على بعض القيم المنسقة بشكل غير صحيح، ولكنك تريد استيراد البيانات المتبقية مع تجاهل الصفوف غير الصالحة على أي حال، يمكنك استخدام المعلمة */AllowedBadLinesPercentage* في الأمر. يحدد المثال أعلاه حد 5 بالمائة. وهذا يعني أن الأداة ستقوم بتجزئة جدول المعلومات الحساسة وتحميله حتى لو كان ما يصل إلى خمسة بالمائة من الصفوف غير صالح.

   سيضيف هذا الأمر تلقائيا قيمة مالحة تم إنشاؤها عشوائيا إلى التجزئة لمزيد من الأمان. اختياريا، إذا كنت تريد استخدام قيمة الملح الخاصة بك، أضف **/Salt \<saltvalue\>** إلى الأمر. يجب أن يكون طول هذه القيمة 64 حرفا ويمكن أن تحتوي فقط على أحرف a-z و0-9 أحرف.

6. تحقق من حالة التحميل عن طريق تشغيل هذا الأمر:

   ```dos
   EdmUploadAgent.exe /GetSession /DataStoreName \<DataStoreName\>
   ```

   على سبيل المثال:`EdmUploadAgent.exe /GetSession /DataStoreName PatientRecords`

   ابحث عن الحالة في **ProcessingInProgress**. تحقق مرة أخرى كل بضع دقائق حتى تتغير الحالة إلى **مكتملة**. بمجرد اكتمال الحالة، تصبح بيانات EDM جاهزة للاستخدام. اعتمادا على حجم ملف جدول مصدر المعلومات الحساسة، قد يستغرق ذلك من بضع دقائق إلى عدة ساعات.

> [!TIP]
> إذا كنت تريد أن يتم إعلامك بمجرد أن تصبح البيانات الحساسة التي تم تحميلها جاهزة للاستخدام، فاتبع الإجراءات الواردة في [إنشاء إعلامات لأنشطة مطابقة البيانات الدقيقة](sit-edm-notifications-activities.md#create-notifications-for-exact-data-match-activities).

### <a name="separate-hash-and-upload"></a>فصل التجزئة والتحميل

تنفيذ التجزئة على كمبيوتر في بيئة آمنة. يجب أن يكون **EDMUploadAgent** مثبتا على كلا الكمبيوترين.

اختياري: إذا استخدمت مخطط مطابقة البيانات الدقيقة ومعالج نوع المعلومات الحساسة لإنشاء المخطط ولم تقم بتنزيله بالفعل، فقم بتشغيل الأمر التالي في نافذة موجه الأوامر لتنزيل الملف بتنسيق XML:

```dos
EdmUploadAgent.exe /SaveSchema /DataStoreName <schema name> /OutputDir <path to output folder>
````

1. على الكمبيوتر في البيئة الآمنة، قم بتشغيل الأمر التالي في نوافذ موجه الأوامر:

   ```dos
   EdmUploadAgent.exe /CreateHash /DataFile [data file] /HashLocation [hash file location] /Schema [Schema file] /AllowedBadLinesPercentage [value]
   ```

   على سبيل المثال:

   ```dos
   EdmUploadAgent.exe /CreateHash /DataFile C:\Edm\Data\PatientRecords.csv /HashLocation C:\Edm\Hash /Schema edm.xml /AllowedBadLinesPercentage 5
   ```

   > [!NOTE]
   > التنسيق الافتراضي لملف البيانات الحساسة هو قيم مفصولة بفواصل. يمكنك تحديد ملف مفصول بعلامات تبويب عن طريق الإشارة إلى الخيار "{Tab}" باستخدام المعلمة /ColumnSeparator، أو يمكنك تحديد ملف مفصول أنبوبي بالإشارة إلى الخيار "|".

   سيؤدي ذلك إلى إخراج ملف متجزئة وملف ملح بهذه الملحقات إذا لم تحدد خيار **/Salt \<saltvalue\>** :

   - . EdmHash
   - . EdmSalt

2. انسخ هذه الملفات بطريقة آمنة إلى الكمبيوتر الذي ستستخدمه لتحميل ملف جدول مصدر المعلومات الحساسة (PatientRecords) إلى المستأجر.

3. قم بتخويل عامل Upload EDM، وافتح نافذة موجه الأوامر كمسؤول، وقم بالتبديل إلى دليل **C:\EDM\Data** ثم قم بتشغيل الأمر التالي:

   ```dos
   EdmUploadAgent.exe /Authorize
   ```

   > [!IMPORTANT]
   > يجب تشغيل **EdmUploadAgent** من المجلد حيث تم تثبيته، والإشارة إلى المسار الكامل لملفات البيانات.

4. سجل الدخول باستخدام حساب العمل أو المؤسسة التعليمية Microsoft 365 التي تمت إضافتها إلى مجموعة أمان EDM_DataUploaders. يتم استخراج معلومات المستأجر من حساب المستخدم لإجراء الاتصال.

5. لتحميل البيانات المتجزئة، قم بتشغيل الأمر التالي في موجه الأوامر Windows:

   ```dos
   EdmUploadAgent.exe /UploadHash /DataStoreName \<DataStoreName\> /HashFile \<HashedSourceFilePath\ /ColumnSeparator ["{Tab}"|"|"]
   ```

   على سبيل المثال:

   ```dos
   EdmUploadAgent.exe /UploadHash /DataStoreName PatientRecords /HashFile C:\\Edm\\Hash\\**PatientRecords.EdmHash**
   ```

6. للتحقق من تحميل بياناتك الحساسة، قم بتشغيل الأمر التالي في نافذة موجه الأوامر:

   ```dos
   EdmUploadAgent.exe /GetDataStore
   ```

   سترى قائمة بمخازن البيانات ووقت آخر تحديث لها.

7. إذا كنت تريد رؤية جميع عمليات تحميل البيانات إلى مخزن معين، فشغل الأمر التالي في موجه أوامر Windows لمشاهدة قائمة بجميع مخازن البيانات ووقت تحديثها:

   ```dos
   EdmUploadAgent.exe /GetSession /DataStoreName <DataStoreName>
   ```

> [!NOTE]
> لأتمتة عملية التجزئة والتحميل بعد إنشائها في المرة الأولى، راجع [تحديث ملف جدول مصدر المعلومات الحساسة المطابق تماما للبيانات](sit-use-exact-data-refresh-data.md).

## <a name="next-step"></a>الخطوة التالية

- [إنشاء بيانات دقيقة تتطابق مع نوع المعلومات الحساسة/حزمة القاعدة](sit-get-started-exact-data-match-create-rule-package.md#create-exact-data-match-sensitive-information-typerule-package)
