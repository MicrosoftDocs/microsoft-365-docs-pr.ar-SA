---
title: تمكين تسميات الحساسية لملفات Office في SharePoint OneDrive
f1.keywords:
- NOCSH
ms.author: cabailey
author: cabailey
manager: laurawi
audience: Admin
ms.topic: article
ms.date: ''
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
- SPO_Content
search.appverid:
- MOE150
- MET150
description: يمكن للمسؤولين تمكين دعم تسمية الحساسية لملفات Word Excel PowerPoint في SharePoint OneDrive.
ms.openlocfilehash: 08c3daab9195e98c3b099255f1e7fb38a2324c33
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/08/2022
ms.locfileid: "63567195"
---
# <a name="enable-sensitivity-labels-for-office-files-in-sharepoint-and-onedrive"></a>تمكين تسميات الحساسية لملفات Office في SharePoint OneDrive

>*[Microsoft 365 إرشادات الترخيص لتوافق & الأمان](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).*

قم بتمكين التسميات المضمنة [](sensitivity-labels-office-apps.md#office-file-types-supported) لملفات Office في SharePoint و OneDrive بحيث يمكن للمستخدمين تطبيق تسميات الحساسية في Office على الويب.[](sensitivity-labels.md) عند تمكين هذه الميزة، سيشاهد المستخدمون الزر الحساسية  على الشريط حتى يمكنهم تطبيق التسميات، ورؤية أي اسم تسمية مطبق على شريط المعلومات.

يؤدي تمكين هذه الميزة أيضا إلى SharePoint OneDrive معالجة محتويات ملفات Office التي تم تشفيرها باستخدام تسمية الحساسية. يمكن تطبيق التسمية في Office على الويب أو في Office سطح المكتب وتحميلها أو حفظها في SharePoint OneDrive. حتى تقوم بتمكين هذه الميزة، لن تتمكن هذه الخدمات من معالجة الملفات المشفرة، مما يعني أن ميزة المشاركة في الكتابة و eDiscovery و"منع فقدان البيانات" و"البحث" وميزات التعاون الأخرى لن تعمل مع هذه الملفات.

بعد تمكين تسميات الحساسية لملفات Office في SharePoint و OneDrive، للملفات الجديدة والمتغيرة التي لها تسمية حساسية تطبق التشفير باستخدام مفتاح مستند إلى السحابة (ولا تستخدم تشفير المفتاح [المزدوج:](double-key-encryption.md)

- بالنسبة لملفات Word Excel PowerPoint، SharePoint و OneDrive على التسمية ويمكنهم الآن معالجة محتويات الملف المشفر.

- عندما يقوم المستخدمون بتنزيل هذه الملفات أو الوصول إليها من SharePoint أو OneDrive، يتم فرض تسمية الحساسية وأي إعدادات تشفير من التسمية وتبقى مع الملف، أينما تم تخزينه. تأكد من توفير إرشادات المستخدم لاستخدام التسميات فقط لحماية المستندات. لمزيد من المعلومات، راجع [خيارات إدارة حقوق استخدام المعلومات (IRM) وتسميات الحساسية](sensitivity-labels-office-apps.md#information-rights-management-irm-options-and-sensitivity-labels).

- عندما يقوم المستخدمون بتحميل ملفات ملصقة ومشفرة SharePoint أو OneDrive، يجب أن يكون لديهم على الأقل حقوق عرض تلك الملفات. على سبيل المثال، يمكنهم فتح الملفات خارج SharePoint. إذا لم يكن هذا الحد الأدنى من الاستخدام صحيحا، فهذا يعني أن عملية التحميل ناجحة ولكن الخدمة لا تتعرف على التسمية ولا يمكنها معالجة محتويات الملف.

- استخدم Office على الويب (Word Excel PowerPoint) لفتح ملفات Office بها تسميات الحساسية التي تطبق التشفير وتحريرها. يتم فرض الأذونات التي تم تعيينها باستخدام التشفير. يمكنك أيضا استخدام [التسمية التلقائية](apply-sensitivity-label-automatically.md) لهذه المستندات.

- يمكن للمستخدمين الخارجيين الوصول إلى المستندات التي تم تسميتها بالتشفير باستخدام حسابات الضيوف. لمزيد من المعلومات، راجع [دعم المستخدمين الخارجيين والمحتوى المسمى](sensitivity-labels-office-apps.md#support-for-external-users-and-labeled-content).

- Office 365 eDiscovery البحث بنص كامل عن هذه الملفات، كما تدعم سياسات منع فقدان البيانات (DLP) المحتوى في هذه الملفات.

> [!NOTE]
> إذا تم تطبيق التشفير باستخدام مفتاح في الموقع المحلي (يشار غالبا إلى طبولوجيا إدارة المفاتيح ب "الاستمرار على المفتاح الخاص بك" أو HYOK)، أو باستخدام تشفير المفتاح المزدوج، لا [](double-key-encryption.md)يتغير سلوك الخدمة لمعالجة محتويات الملف. وبالتالي لن تعمل ميزات المشاركة في الكتابة و eDiscovery و"منع فقدان البيانات" و"البحث" وميزات التعاون الأخرى في هذه الملفات.
>
> لا SharePoint سلوك OneDrive للملفات الموجودة في هذه المواقع التي تم تسميتها بالتشفير باستخدام مفتاح واحد مستند إلى Azure. لكي تستفيد هذه الملفات من الإمكانات الجديدة بعد تمكين تسميات الحساسية لملفات Office في SharePoint و OneDrive، يجب تنزيل الملفات وتحميلها مرة أخرى أو تحريرها.

بعد تمكين تسميات الحساسية لملفات Office في SharePoint و OneDrive، تتوفر ثلاثة أحداث تدقيق جديدة لمراقبة تسميات الحساسية التي يتم تطبيقها [](search-the-audit-log-in-security-and-compliance.md#sensitivity-label-activities) على المستندات في SharePoint OneDrive:

- **تسمية الحساسية المطبقة على الملف**
- **تم تطبيق تسمية الحساسية التي تم تغييرها على ملف**
- **تسمية الحساسية التي تمت إزالتها من ملف**

شاهد الفيديو التالي (بدون صوت) لمشاهدة الإمكانات الجديدة في العمل:

> [!VIDEO https://www.microsoft.com/videoplayer/embed//RE4ornZ]

لديك دائما خيار تعطيل تسميات الحساسية لملفات Office في SharePoint [OneDrive (إلغاء](#how-to-disable-sensitivity-labels-for-sharepoint-and-onedrive-opt-out) الاشتراك) في أي وقت.

إذا كنت تحمي المستندات حاليا في SharePoint باستخدام SharePoint إدارة حقوق استخدام المعلومات (IRM)، فتأكد من التحقق من المقطع [إدارة حقوق استخدام المعلومات (IRM) في SharePoint](#sharepoint-information-rights-management-irm-and-sensitivity-labels) وتسميات الحساسية في هذه الصفحة.

## <a name="requirements"></a>المتطلبات

تعمل هذه الإمكانات الجديدة [مع تسميات الحساسية](sensitivity-labels.md) فقط. إذا كان لديك حاليا تسميات Azure Information Protection، فقام أولا بترحيلها إلى تسميات الحساسية حتى تتمكن من تمكين هذه الميزات للملفات الجديدة التي تقوم بتحميلها. للحصول على الإرشادات، [راجع كيفية ترحيل تسميات Azure Information Protection إلى تسميات الحساسية الموحدة](/azure/information-protection/configure-policy-migrate-labels).

استخدم إصدار تطبيق المزامنة من OneDrive 19.002.0121.0008 أو إصدار أحدث في Windows والإصدار 19.002.0107.0008 أو إصدار أحدث على Mac. تم إصدار هذين الإصدارين في 28 يناير 2019، ويتم إصدارهما حاليا لجميع الرنينات. لمزيد من المعلومات، راجع OneDrive [ملاحظات الإصدار](https://support.office.com/article/845dcf18-f921-435e-bf28-4e24b95e5fc0). بعد تمكين تسميات الحساسية لملفات Office في SharePoint و OneDrive، تتم مطالبة المستخدمين الذين يديرون إصدارا قديما من تطبيق المزامنة بتحديثه.

## <a name="limitations"></a>القيود

- لا يمكن SharePoint و OneDrive معالجة بعض الملفات التي تم تسميتها وتشفيرها من تطبيقات سطح المكتب في Office عندما تحتوي هذه الملفات على بيانات PowerQuery أو بيانات مخزنة بواسطة الوظائف الإضافية المخصصة أو أجزاء XML مخصصة مثل خصائص صفحة الغلاف أو المخططات الخاصة بنوع المحتوى أو لوحة معلومات المستند المخصصة وXSN المخصصة. ينطبق هذا القيد أيضا على الملفات التي تتضمن المراجع [](https://support.microsoft.com/en-us/office/create-a-bibliography-citations-and-references-17686589-4824-4940-9c69-342c289fa2a5)والملفات التي تم إضافة "مستند" عليها عند [](https://support.microsoft.com/office/enable-and-configure-unique-document-ids-ea7fee86-bd6f-4cc8-9365-8086e794c984) تحميلها.

    بالنسبة إلى هذه الملفات، يمكنك إما تطبيق تسمية بدون تشفير بحيث يمكن فتحها لاحقا في Office على الويب، أو توجيه المستخدمين لفتح الملفات في تطبيقات سطح المكتب الخاصة بهم. لا تتأثر الملفات التي تم تسميتها وتشفيرها في Office على الويب فقط.

- SharePoint OneDrive تطبيق تسميات الحساسية تلقائيا على الملفات الموجودة التي قمت بتشفيرها بالفعل باستخدام تسميات Azure Information Protection. بدلا من ذلك، لكي تعمل الميزات بعد تمكين تسميات الحساسية لملفات Office في SharePoint OneDrive، أكمل هذه المهام:

    1. تأكد من ترحيل [تسميات Azure Information Protection](/azure/information-protection/configure-policy-migrate-labels) إلى تسميات الحساسية ونشرها من مركز التوافق في Microsoft 365.[](create-sensitivity-labels.md#publish-sensitivity-labels-by-creating-a-label-policy)
    2. قم بتنزيل الملفات الملصقات ثم قم بتحميلها إلى موقعها الأصلي في SharePoint أو OneDrive.

- SharePoint لا OneDrive معالجة الملفات المشفرة عندما يكون للتسمية التي تطبق التشفير أي من عمليات التكوين [التالية للتشفير](encryption-sensitivity-labels.md#configure-encryption-settings):
  - **السماح للمستخدمين بتعيين الأذونات** عند تطبيق التسمية وحدد خانة الاختيار في **Word PowerPoint** و Excel المستخدمين بتحديد الأذونات. يشار في بعض الأحيان إلى هذا الإعداد ب "الأذونات المعرفة من قبل المستخدم".
  - **يتم تعيين وصول المستخدم إلى المحتوى** الذي تنتهي صلاحيته إلى قيمة أخرى غير **أبدا**.
  - **يتم تحديد تشفير المفتاح** المزدوج.

    بالنسبة إلى التسميات التي لها أي من تكوينات التشفير هذه، لا يتم عرض التسميات للمستخدمين في Office على الويب. بالإضافة إلى ذلك، لا يمكن استخدام الإمكانات الجديدة مع المستندات الملصقات التي لديها إعدادات التشفير هذه بالفعل. على سبيل المثال، لن يتم إرجاع هذه المستندات في نتائج البحث، حتى لو تم تحديثها.

- لأسباب تتعلق بالأداء، عند تحميل مستند أو حفظه إلى SharePoint ولا تطبق تسمية الملف التشفير، قد يستغرق عمود الحساسية في مكتبة المستندات بعض الوقت لعرض  اسم التسمية. عامل في هذا التأخير إذا كنت تستخدم البرامج النصية أو التنفيذ التلقائي التي تعتمد على اسم التسمية في هذا العمود.

- إذا تم تسمية مستند أثناء سحبه في SharePoint، [](https://support.microsoft.com/office/check-out-check-in-or-discard-changes-to-files-in-a-library-7e2c12a9-a874-4393-9511-1378a700f6de)فلن يعرض عمود الحساسية في مكتبة المستندات اسم التسمية حتى يتم إيداع المستند وفتحه في SharePoint.

- إذا تم تنزيل مستند مسمي ومشفر من SharePoint أو OneDrive بواسطة تطبيق أو خدمة تستخدم اسم خدمة أساسي، ثم يتم تحميلها مرة أخرى باستخدام تسمية تطبق إعدادات تشفير مختلفة، سيفشل التحميل. سيناريو مثال على ذلك هو أن يغير Microsoft Defender for Cloud Apps تسمية حساسية على ملف من سري  إلى سري للغاية، أو من **سري** إلى **عام**.
    
    لا يفشل التحميل إذا كان التطبيق أو الخدمة يقوم أولا بتشغيل [الأمر cmdlet Unlock-SPOSensitivityLabelEncryptedFile](/powershell/module/sharepoint-online/unlock-sposensitivitylabelencryptedFile)، كما هو موضح في المقطع إزالة [](#remove-encryption-for-a-labeled-document) التشفير لمستند مسمي. أو قبل التحميل، يتم حذف الملف الأصلي أو يتم تغيير اسم الملف.

- قد يتأخر المستخدمون في التمكن من فتح المستندات المشفرة في سيناريو حفظ باسم التالي: باستخدام إصدار سطح المكتب من Office، يختار المستخدم حفظ باسم لمستند به تسمية حساسية تطبق التشفير. يقوم المستخدم SharePoint أو OneDrive الموقع، ثم يحاول على الفور فتح هذا المستند في Office على الويب. إذا كانت الخدمة لا تزال معالجة التشفير، يرى المستخدم رسالة بأنه يجب فتح المستند في تطبيق سطح المكتب الخاص به. إذا حاول مرة أخرى خلال بضع دقائق، يتم فتح المستند بنجاح في Office على الويب.

- بالنسبة للمستندات المشفرة، لا يتم دعم الطباعة في Office على الويب.

- بالنسبة للمستندات المشفرة في Office على الويب، لا يتم منع النسخ إلى الحافظة والتقاط الشاشة. لمزيد من المعلومات، راجع [هل يمكن لإدارة الحقوق منع التقاط الشاشة؟](/azure/information-protection/faqs-rms#can-rights-management-prevent-screen-captures)

- بشكل افتراضي، Office تطبيقات سطح المكتب وتطبيقات الأجهزة المحمولة لا تدعم التأليف المشترك للملفات التي تم تسميتها بالتشفير. تستمر هذه التطبيقات في فتح الملفات الملصقة والم مشفرة في وضع التحرير الخاص.
    
    > [!NOTE]
    > التأليف المشترك معتمد الآن لكل من Windows و macOS. لمزيد من المعلومات، راجع [تمكين التأليف المشترك للملفات المشفرة باستخدام تسميات الحساسية](sensitivity-labels-coauthoring.md).

- إذا غير المسؤول إعدادات تسمية منشورة تم تطبيقها بالفعل على الملفات التي تم تنزيلها إلى عميل مزامنة المستخدمين، فقد يتعذر على المستخدمين حفظ التغييرات التي إدخالها على الملف في مجلد المزامنة OneDrive الخاص بهم. ينطبق هذا السيناريو على الملفات التي تم تسميتها بالتشفير، وأيضا عندما تتغير التسمية من تسمية لم تطبق التشفير على تسمية تطبق التشفير. يرى المستخدمون [دائرة حمراء بها خطأ أيقونة](https://support.office.com/article/what-do-the-onedrive-icons-mean-11143026-8000-44f8-aaa9-67c985aa49b3) بيضاء متقاطعة، ويطالبون بحفظ التغييرات الجديدة كنسخة منفصلة. بدلا من ذلك، يمكنهم إغلاق الملف وإعادة فتحه، أو استخدام Office على الويب.

- يمكن للمستخدمين تجربة Office على الويب حفظ المشاكل بعد العمل دون اتصال أو في وضع السكون عندما يستخدمون تطبيقات سطح المكتب والأجهزة المحمولة ل Word أو Excel أو PowerPoint. بالنسبة لهؤلاء المستخدمين، عندما يستأنفون جلسة تطبيق Office ويحاولون حفظ التغييرات، تظهر رسالة فشل التحميل مع خيار لحفظ نسخة بدلا من حفظ الملف الأصلي.

- لا يمكن فتح المستندات التي تم تشفيرها باستخدام الطرق التالية في Office على الويب:
  - التشفير الذي يستخدم مفتاحا في الموقع المحلي ("اضغط على المفتاح الخاص بك" أو HYOK)
  - التشفير الذي تم تطبيقه باستخدام [تشفير المفتاح المزدوج](double-key-encryption.md)
  - التشفير الذي تم تطبيقه بشكل مستقل عن تسمية، على سبيل المثال، عن طريق تطبيق قالب حماية إدارة الحقوق مباشرة.

- التسميات التي تم تكوينها للغات [أخرى](create-sensitivity-labels.md#additional-label-settings-with-security--compliance-center-powershell) غير معتمدة وهي تعرض اللغة الأصلية فقط.

- إذا حذفت تسمية تم تطبيقها على مستند في SharePoint أو OneDrive، بدلا من إزالة التسمية من نهج التسمية المعمول به، فلن يتم تسمية المستند عند تنزيله أو تشفيره. في المقابل، إذا كان المستند المسمى مخزنا خارج SharePoint أو OneDrive، يظل المستند مشفرا إذا تم حذف التسمية. تجدر الإشارة إلى أنه على الرغم من أنك قد تحذف التسميات أثناء مرحلة الاختبار، إلا أنه من النادر جدا حذف تسمية في بيئة الإنتاج.

## <a name="how-to-enable-sensitivity-labels-for-sharepoint-and-onedrive-opt-in"></a>كيفية تمكين تسميات الحساسية SharePoint OneDrive (الاشتراك)

يمكنك تمكين الإمكانات الجديدة باستخدام مركز التوافق في Microsoft 365 أو باستخدام PowerShell. وكما هو الأمر مع جميع تغييرات التكوين على مستوى المستأجر SharePoint OneDrive، يستغرق الأمر حوالي 15 دقيقة حتى يتم إدخال التغيير حيز التنفيذ.

### <a name="use-the-compliance-center-to-enable-support-for-sensitivity-labels"></a>استخدام مركز التوافق لتمكين دعم تسميات الحساسية

هذا الخيار هو أسهل طريقة لتمكين تسميات الحساسية SharePoint OneDrive، ولكن يجب تسجيل الدخول كمسؤول عام للمستأجر.

1. سجل الدخول [إلى مركز التوافق في Microsoft 365](https://compliance.microsoft.com/) كمسؤول عام، وانتقل إلى **SolutionsInformation**  >  protection

    إذا لم يظهر هذا الخيار على الفور، فحدد أولا **إظهار الكل**.

2. إذا رأيت رسالة ل تشغيل إمكانية معالجة المحتوى في ملفات Office الإنترنت، فحدد **تشغيل الآن**:

    ![الزر "تشغيل الآن" لتمكين تسميات الحساسية Office Online.](../media/sensitivity-labels-turn-on-banner.png)

    يتم تشغيل الأمر على الفور وعندما يتم تحديث الصفحة في المرة التالية، لن ترى الرسالة أو الزر.

> [!NOTE]
> إذا كان لديك Microsoft 365 Geo، فيجب استخدام PowerShell لتمكين هذه الإمكانات لكل المواقع الجغرافية. راجع القسم التالي للحصول على التفاصيل.

### <a name="use-powershell-to-enable-support-for-sensitivity-labels"></a>استخدام PowerShell لتمكين دعم تسميات الحساسية

كبديل لاستخدام مركز التوافق، يمكنك تمكين دعم تسميات الحساسية باستخدام الأمر [Cmdlet Set-SPOTenant](/powershell/module/sharepoint-online/set-spotenant) من SharePoint Online PowerShell.

إذا كان لديك Microsoft 365 Geo، فيجب استخدام PowerShell لتمكين هذا الدعم لكل المواقع الجغرافية.

#### <a name="prepare-the-sharepoint-online-management-shell"></a>إعداد SharePoint Online Management Shell

قبل تشغيل الأمر PowerShell لتمكين تسميات الحساسية لملفات Office في SharePoint و OneDrive، تأكد من تشغيل الإصدار 16.0.19418.12000 أو إصدار أحدث من SharePoint Online Management Shell. إذا كان لديك الإصدار الأخير بالفعل، يمكنك الانتقال إلى [الإجراء التالي](#run-the-powershell-command-to-enable-support-for-sensitivity-labels) لتشغيل الأمر PowerShell.

1. إذا قمت بتثبيت إصدار سابق من SharePoint Online Management Shell من معرض PowerShell، يمكنك تحديث الوحدة النمطية عن طريق تشغيل الأمر cmdlet التالي.

    ```PowerShell
    Update-Module -Name Microsoft.Online.SharePoint.PowerShell
    ```

2. بدلا من ذلك، إذا قمت بتثبيت إصدار سابق من SharePoint Online Management Shell من مركز التنزيل ل Microsoft، يمكنك أيضا الانتقال إلى إضافة برامج أو إزالتها  وإزالة تثبيت SharePoint Online Management Shell.

3. في مستعرض ويب، انتقل إلى صفحة مركز التنزيل وتنزيل [أحدث SharePoint Online Management Shell](https://go.microsoft.com/fwlink/p/?LinkId=255251).

4. حدد اللغة ثم انقر فوق **تنزيل**.

5. اختر بين ملف x64 وx86 .msi. قم بتنزيل ملف x64 إذا قمت بتشغيل إصدار 64 بت من Windows أو ملف x86 إذا قمت بتشغيل الإصدار 32 بت. إذا لم تكن تعرف، فشاهد ما هو إصدار Windows الذي يتم تشغيله[؟](https://support.microsoft.com/help/13443/windows-which-operating-system)

6. بعد تنزيل الملف، قم بتشغيل الملف واتبع الخطوات في معالج الإعداد.

#### <a name="run-the-powershell-command-to-enable-support-for-sensitivity-labels"></a>تشغيل الأمر PowerShell لتمكين دعم تسميات الحساسية

لتمكين الإمكانات الجديدة، استخدم [الأمر Cmdlet Set-SPOTenant](/powershell/module/sharepoint-online/set-spotenant) مع المعلمة *EnableAIPIntegration* :

1. باستخدام حساب العمل أو المؤسسة الدراسية الذي لديه امتيازات المسؤول SharePoint العام في Microsoft 365، اتصل SharePoint. لمعرفة كيفية القيام بذلك، راجع بدء [SharePoint Online Management Shell](/powershell/sharepoint/sharepoint-online/connect-sharepoint-online).

    > [!NOTE]
    > إذا كنت Microsoft 365 Multi-Geo، فاستخدم المعلمة -Url مع [الاتصال-SPOService](/powershell/module/sharepoint-online/connect-sposervice)، وحدد عنوان URL لموقع SharePoint Online Administration Center لأحد مواقعك الجغرافية.

2. تشغيل الأمر التالي واضغط **على Y** لتأكيد:

    ```PowerShell
    Set-SPOTenant -EnableAIPIntegration $true
    ```
3. بالنسبة Microsoft 365 الجغرافيا المتعددة: كرر خطوتين 1 و2 لكل موقع من المواقع الجغرافية المتبقية.

## <a name="publishing-and-changing-sensitivity-labels"></a>نشر تسميات الحساسية وتغييرها

عند استخدام تسميات الحساسية مع SharePoint و OneDrive، ضع في اعتبارك أنك تحتاج إلى السماح بتكرار الوقت عند نشر تسميات حساسية جديدة أو تحديث تسميات الحساسية الموجودة. هذا أمر مهم بشكل خاص بالنسبة إلى التسميات الجديدة التي تطبق التشفير.

على سبيل المثال: يمكنك إنشاء تسمية حساسية جديدة تطبق التشفير ونشرها، وهي تظهر بسرعة كبيرة في تطبيق سطح المكتب للمستخدم. يطبق المستخدم هذه التسمية على مستند ثم يقوم بتحميلها إلى SharePoint أو OneDrive. إذا لم يتم إكمال النسخ المتماثل للتسمية للخدمة، فلن يتم تطبيق الإمكانات الجديدة على هذا المستند عند التحميل. ونتيجة لذلك، لن يتم إرجاع المستند في البحث أو عن eDiscovery ولا يمكن فتح المستند في Office على الويب.

يتم تكرار التغييرات التالية في غضون ساعة واحدة: تسميات الحساسية الجديدة والمحذوفة، وإعدادات نهج تسمية الحساسية التي تتضمن التسميات الموجودة في النهج.

يتم تكرار التغييرات التالية في غضون 24 ساعة: التغييرات في إعدادات تسمية الحساسية لتسميات موجودة.

وبما أن تأخير التكرار لا يكون سوى ساعة واحدة لتسميات الحساسية الجديدة، فمن غير المحتمل أن تخوض السيناريو في المثال. ولكن كضمان، نوصي بنشر تسميات جديدة لبضعة مستخدمين اختباريين أولا، وانتظر لمدة ساعة، ثم تحقق من سلوك التسمية على SharePoint OneDrive. كخطوة أخيرة، اجعل التسمية متوفرة لمزيد من المستخدمين إما بإضافة المزيد من المستخدمين إلى نهج التسمية الموجود، أو إضافة التسمية إلى نهج تسمية موجود للمستخدمين القياسيين. في الوقت الذي يرى فيه المستخدمون القياسيون التسمية، فقد تم مزامنتها SharePoint OneDrive.

## <a name="sharepoint-information-rights-management-irm-and-sensitivity-labels"></a>SharePoint إدارة حقوق استخدام المعلومات (IRM) وتسميات الحساسية

SharePoint إدارة حقوق استخدام المعلومات [(IRM)](set-up-irm-in-sp-admin-center.md) تقنية قديمة لحماية الملفات على مستوى القائمة والمكتبة من خلال تطبيق التشفير والقيود عند تنزيل الملفات. تم تصميم تقنية الحماية القديمة هذه لمنع المستخدمين غير المصرح لهم من فتح الملف أثناء وجوده خارج SharePoint.

في المقابل، توفر تسميات الحساسية إعدادات حماية العلامات المرئية (رؤوس وتسميات توابل وعلامات مائية) بالإضافة إلى التشفير. تدعم إعدادات التشفير النطاق الكامل من حقوق الاستخدام لتقييد ما يمكن للمستخدمين القيام به باستخدام المحتوى، كما يتم دعم تسميات الحساسية نفسها للعديد من [السيناريوهات](get-started-with-sensitivity-labels.md#common-scenarios-for-sensitivity-labels).[](/azure/information-protection/configure-usage-rights) يؤدي استخدام أسلوب الحماية نفسه مع إعدادات متناسقة عبر أحمال العمل والتطبيقات إلى وضع استراتيجية حماية متناسقة.

ومع ذلك، يمكنك استخدام حلي الحماية معا، كما يلي السلوك:

- إذا قمت بتحميل ملف يحتوي على تسمية الحساسية التي تطبق التشفير، فإن SharePoint لا يمكنه معالجة محتوى هذه الملفات بحيث لا يتم دعم المشاركة في المشاركة في التسمية و eDiscovery وDLP والبحث لهذه الملفات.

- إذا قمت تسمية ملف باستخدام Office على الويب، يتم فرض أي إعدادات تشفير من التسمية. بالنسبة إلى هذه الملفات، يتم دعم المشاركة في استخدام كل من eDiscovery وDLP والبحث.

- إذا قمت بتنزيل ملف تم تسميته باستخدام Office على الويب، يتم الاحتفاظ بالتسمية وفرض أي إعدادات تشفير من التسمية بدلا من إعدادات تقييد IRM.

- إذا قمت بتنزيل ملف Office PDF غير مشفر باستخدام تسمية الحساسية، يتم تطبيق إعدادات IRM.

- إذا قمت بتمكين أي من إعدادات مكتبة IRM الإضافية، والتي تتضمن منع المستخدمين من تحميل المستندات التي لا تدعم IRM، يتم فرض هذه الإعدادات.

باستخدام هذا السلوك، يمكنك أن تتأكد من حماية جميع ملفات pdf Office من الوصول غير المصرح به إذا تم تنزيلها، حتى لو لم يتم تسميتها. ومع ذلك، لن تستفيد الملفات الملصقات التي يتم تحميلها من الإمكانات الجديدة.


## <a name="search-for-documents-by-sensitivity-label"></a>البحث عن المستندات حسب تسمية الحساسية

استخدم الخاصية **المدارة InformationProtectionLabelId** للعثور على كل المستندات في SharePoint أو OneDrive لها تسمية حساسية معينة. استخدم بناء الجملة التالي: `InformationProtectionLabelId:<GUID>`

على سبيل المثال، للبحث عن كل المستندات التي تم تسميتها ب "سري"، وكانت هذه التسمية تتضمن GUID من "8faca7b8-8d20-48a3-8ea2-0f96310a848e"، في مربع البحث، اكتب:

```
InformationProtectionLabelId:8faca7b8-8d20-48a3-8ea2-0f96310a848e
```

لن يعثر البحث على المستندات الملصقات في ملف مضغوط، مثل ملف .zip.

للحصول على GUIDs لتسميات الحساسية، استخدم [cmdlet الحصول على تسمية](/powershell/module/exchange/get-label) :

1. أولا، [اتصل بمركز Office 365 الأمان & PowerShell](/powershell/exchange/office-365-scc/connect-to-scc-powershell/connect-to-scc-powershell).

    على سبيل المثال، في جلسة PowerShell التي تقوم بتشغيلها كمسؤول، سجل الدخول باستخدام حساب مسؤول عام.

2. ثم قم بتشغيل الأمر التالي:

    ```powershell
    Get-Label |ft Name, Guid
    ```

لمزيد من المعلومات حول استخدام الخصائص المدارة، راجع [إدارة مخطط البحث في](/sharepoint/manage-search-schema) SharePoint.

## <a name="remove-encryption-for-a-labeled-document"></a>إزالة التشفير لمستند مسمي

قد تكون هناك حالات نادرة يحتاج فيها مسؤول SharePoint إلى إزالة التشفير من مستند مخزن في SharePoint. يمكن لأي مستخدم لديه حق [](/azure/information-protection/configure-usage-rights#usage-rights-and-descriptions) استخدام إدارة الحقوق في التصدير أو التحكم الكامل المعين له لذلك المستند إزالة التشفير الذي تم تطبيقه بواسطة خدمة Azure Rights Management من Azure Information Protection. على سبيل المثال، يمكن للمستخدمين الذين لديهم أي من حقوق الاستخدام هذه استبدال تسمية تطبق التشفير بتسمية بدون تشفير. يمكن [للمستخدم الفهار](/azure/information-protection/configure-super-users) أيضا تنزيل الملف وحفظ نسخة محلية بدون التشفير.

كبديل، يمكن للمسؤول [العام أو المسؤول SharePoint](/sharepoint/sharepoint-admin-role) تشغيل الأمر [cmdlet Unlock-SPOSensitivityLabelEncryptedFile](/powershell/module/sharepoint-online/unlock-sposensitivitylabelencryptedFile)، الذي يزيل كل من تسمية الحساسية والتشفير. يتم تشغيل أمر cmdlet هذا حتى إذا لم يكن لدى المسؤول أذونات الوصول إلى الموقع أو الملف، أو إذا كانت خدمة Azure Rights Management غير متوفرة.

على سبيل المثال:

```powershell
Unlock-SPOSensitivityLabelEncryptedFile -FileUrl "https://contoso.com/sites/Marketing/Shared Documents/Doc1.docx" -JustificationText "Need to decrypt this file"
```

المتطلبات:

- SharePoint Online Management Shell الإصدار 16.0.20616.12000 أو الإصدارات الأحدث.

- تم تطبيق التشفير بواسطة تسمية حساسية مع إعدادات التشفير المعرفة من قبل المسؤول (إعدادات تعيين الأذونات [الآن](encryption-sensitivity-labels.md#assign-permissions-now) التسمية). [تشفير المفتاح المزدوج](encryption-sensitivity-labels.md#double-key-encryption) غير معتمد لهذا الأمر cmdlet.

تتم إضافة نص التبرير إلى [](search-the-audit-log-in-security-and-compliance.md#sensitivity-label-activities) حدث التدقيق لتسمية الحساسية التي تمت إزالتها من الملف، كما يتم تسجيل إجراء فك التشفير في تسجيل استخدام الحماية ل [Azure Information Protection](/azure/information-protection/log-analyze-usage).

## <a name="how-to-disable-sensitivity-labels-for-sharepoint-and-onedrive-opt-out"></a>كيفية تعطيل تسميات الحساسية SharePoint OneDrive (إلغاء الاشتراك)

إذا قمت بتعطيل هذه الإمكانات الجديدة، تستمر حماية الملفات التي قمت بتحميلها بعد تمكين تسميات الحساسية ل SharePoint و OneDrive بواسطة التسمية بسبب استمرار فرض إعدادات التسمية. عند تطبيق تسميات الحساسية على الملفات الجديدة بعد تعطيل هذه الإمكانات الجديدة، لن تعمل ميزة البحث في النص الكامل و eDiscovery والتطبيق المشترك.

لتعطيل هذه الإمكانات الجديدة، يجب استخدام PowerShell. باستخدام SharePoint Online Management Shell و [Cmdlet Set-SPOTenant](/powershell/module/sharepoint-online/set-spotenant)، حدد المعلمة *EnableAIPIntegration* نفسها كما هو موضح في القسم استخدام [PowerShell](#use-powershell-to-enable-support-for-sensitivity-labels) لتمكين دعم تسميات الحساسية. ولكن هذه المرة، قم بتعيين قيمة المعلمة إلى خطأ واضغط **على Y** لتأكيد:

```PowerShell
Set-SPOTenant -EnableAIPIntegration $false
```

إذا كان لديك Microsoft 365 Geo، فيجب تشغيل هذا الأمر لكل موقع من المواقع الجغرافية.

## <a name="next-steps"></a>الخطوات التالية

بعد تمكين تسميات الحساسية لملفات Office في SharePoint و OneDrive، يمكنك وضع تسمية لهذه الملفات تلقائيا باستخدام سياسات التسمية التلقائية. لمزيد من المعلومات، راجع [تطبيق تسمية حساسية على المحتوى تلقائيا](apply-sensitivity-label-automatically.md).

هل تحتاج إلى مشاركة المستندات المشفرة والمسمية مع أشخاص من خارج مؤسستك؟  راجع [مشاركة المستندات المشفرة مع مستخدمين خارجيين](sensitivity-labels-office-apps.md#sharing-encrypted-documents-with-external-users).
