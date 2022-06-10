---
title: تمكين تسميات الحساسية لملفات Office
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
description: يمكن للمسؤولين تمكين دعم وصف الحساسية لملفات Word Excel PowerPoint في SharePoint OneDrive.
ms.openlocfilehash: 9130558bb7ae1af86981e1c052a17565f6d943af
ms.sourcegitcommit: 133bf9097785309da45df6f374a712a48b33f8e9
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 06/10/2022
ms.locfileid: "66014245"
---
# <a name="enable-sensitivity-labels-for-office-files-in-sharepoint-and-onedrive"></a>تمكين تسميات الحساسية لملفات Office في SharePoint وOneDrive

>*[Microsoft 365 إرشادات الترخيص للامتثال & الأمان](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).*

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

تمكين التسمية المضمنة [لملفات Office المدعومة](sensitivity-labels-office-apps.md#office-file-types-supported) في SharePoint OneDrive بحيث يمكن للمستخدمين تطبيق [أوصاف الحساسية](sensitivity-labels.md) في Office على الويب. عند تمكين هذه الميزة، سيرى المستخدمون زر **الحساسية** على الشريط حتى يتمكنوا من تطبيق التسميات، ورؤية أي اسم تسمية مطبق على شريط المعلومات.

يؤدي تمكين هذه الميزة أيضا إلى SharePoint OneDrive القدرة على معالجة محتويات ملفات Office التي تم تشفيرها باستخدام وصف الحساسية. يمكن تطبيق التسمية في Office على الويب أو في تطبيقات سطح المكتب Office وتحميلها أو حفظها في SharePoint OneDrive. حتى تقوم بتمكين هذه الميزة، لا يمكن لهذه الخدمات معالجة الملفات المشفرة، ما يعني أن التأليف المشترك وeDiscovery ومنع فقدان بيانات Microsoft Purview والبحث والميزات التعاونية الأخرى لن تعمل لهذه الملفات.

بعد تمكين تسميات الحساسية لملفات Office في SharePoint OneDrive، للملفات الجديدة والمتغيرة التي تحتوي على تسمية حساسية تطبق التشفير باستخدام مفتاح مستند إلى السحابة (ولا تستخدم [تشفير المفتاح المزدوج](double-key-encryption.md):

- بالنسبة لملفات Word Excel PowerPoint، SharePoint OneDrive التعرف على التسمية ويمكنها الآن معالجة محتويات الملف المشفر.

- عندما يقوم المستخدمون بتنزيل هذه الملفات أو الوصول إليها من SharePoint أو OneDrive، يتم فرض وصف الحساسية وأي إعدادات تشفير من التسمية وتبقى مع الملف، أينما تم تخزينها. تأكد من توفير إرشادات المستخدم لاستخدام التسميات فقط لحماية المستندات. لمزيد من المعلومات، راجع [خيارات Rights Management المعلومات (IRM) وتسميات الحساسية](sensitivity-labels-office-apps.md#information-rights-management-irm-options-and-sensitivity-labels).

- عندما يقوم المستخدمون بتحميل ملفات مسماة ومشفرة إلى SharePoint أو OneDrive، يجب أن يكون لديهم على الأقل حقوق عرض لتلك الملفات. على سبيل المثال، يمكنهم فتح الملفات خارج SharePoint. إذا لم يكن لديهم هذا الحد الأدنى من الاستخدام الصحيح، يكون التحميل ناجحا ولكن الخدمة لا تتعرف على التسمية ولا يمكنها معالجة محتويات الملف.

- استخدم Office على الويب (Word، Excel، PowerPoint) لفتح ملفات Office التي تحتوي على تسميات الحساسية التي تطبق التشفير وتحريرها. يتم فرض الأذونات التي تم تعيينها مع التشفير. يمكنك أيضا استخدام [التسمية التلقائية](apply-sensitivity-label-automatically.md) لهذه المستندات.

- يمكن للمستخدمين الخارجيين الوصول إلى المستندات المسماة بالتشفير باستخدام حسابات الضيوف. لمزيد من المعلومات، راجع [دعم المستخدمين الخارجيين والمحتوى المسمى](sensitivity-labels-office-apps.md#support-for-external-users-and-labeled-content).

- يدعم Office 365 eDiscovery البحث بالنص الكامل عن هذه الملفات وتدعم نهج منع فقدان البيانات (DLP) المحتوى في هذه الملفات.

> [!NOTE]
> إذا تم تطبيق التشفير باستخدام مفتاح محلي (مخطط إدارة المفاتيح يشار إليه غالبا باسم "الاحتفاظ بالمفتاح الخاص بك" أو HYOK)، أو باستخدام [تشفير المفتاح المزدوج](double-key-encryption.md)، لا يتغير سلوك الخدمة لمعالجة محتويات الملف. لذلك بالنسبة إلى هذه الملفات، لن تعمل ميزة التأليف المشترك وeDiscovery والوقاية من فقدان البيانات والبحث والميزات التعاونية الأخرى.
>
> لا يتغير سلوك SharePoint OneDrive أيضا للملفات الموجودة في هذه المواقع المسماة بالتشفير باستخدام مفتاح واحد يستند إلى Azure. لكي تستفيد هذه الملفات من القدرات الجديدة بعد تمكين تسميات الحساسية لملفات Office في SharePoint OneDrive، يجب تنزيل الملفات وتحميلها مرة أخرى أو تحريرها.

بعد تمكين تسميات الحساسية لملفات Office في SharePoint OneDrive، تتوفر ثلاثة [أحداث تدقيق](search-the-audit-log-in-security-and-compliance.md#sensitivity-label-activities) جديدة لمراقبة تسميات الحساسية التي يتم تطبيقها على المستندات في SharePoint OneDrive:

- **تسمية الحساسية المطبقة على الملف**
- **تم تطبيق تسمية الحساسية المتغيرة على الملف**
- **تمت إزالة تسمية الحساسية من الملف**

شاهد الفيديو التالي (بدون صوت) للاطلاع على الإمكانات الجديدة قيد التنفيذ:

> [!VIDEO https://www.microsoft.com/videoplayer/embed//RE4ornZ]

لديك دائما خيار تعطيل تسميات الحساسية لملفات Office في SharePoint OneDrive ([إلغاء الاشتراك](#how-to-disable-sensitivity-labels-for-sharepoint-and-onedrive-opt-out)) في أي وقت.

إذا كنت تقوم حاليا بحماية المستندات في SharePoint باستخدام Rights Management معلومات SharePoint (IRM)، فتأكد من التحقق من قسم [Rights Management المعلومات SharePoint (IRM) وتسميات الحساسية](#sharepoint-information-rights-management-irm-and-sensitivity-labels) في هذه الصفحة.

## <a name="requirements"></a>الاحتياجات

تعمل هذه القدرات الجديدة مع [تسميات الحساسية](sensitivity-labels.md) فقط. إذا كان لديك حاليا تسميات حماية البيانات Azure، فرحلها أولا إلى أوصاف الحساسية حتى تتمكن من تمكين هذه الميزات للملفات الجديدة التي تقوم بتحميلها. للحصول على الإرشادات، راجع [كيفية ترحيل تسميات Azure حماية البيانات إلى تسميات الحساسية الموحدة](/azure/information-protection/configure-policy-migrate-labels).

استخدم إصدار تطبيق المزامنة من OneDrive 19.002.0121.0008 أو إصدار أحدث من Windows والإصدار 19.002.0107.0008 أو إصدار أحدث على Mac. تم إصدار هذين الإصدارين في 28 يناير 2019، ويتم إصدارهما حاليا لجميع الحلقات. لمزيد من المعلومات، راجع [ملاحظات إصدار OneDrive](https://support.office.com/article/845dcf18-f921-435e-bf28-4e24b95e5fc0). بعد تمكين تسميات الحساسية لملفات Office في SharePoint OneDrive، تتم مطالبة المستخدمين الذين يقومون بتشغيل إصدار أقدم من تطبيق المزامنة بتحديثه.

## <a name="limitations"></a>القيود

- لا يمكن SharePoint OneDrive معالجة بعض الملفات التي تم وصفها وتشفيرها من تطبيقات سطح المكتب Office عندما تحتوي هذه الملفات على بيانات PowerQuery أو بيانات مخزنة بواسطة وظائف إضافية مخصصة أو أجزاء XML مخصصة مثل خصائص صفحة الغلاف ومخططات نوع المحتوى ولوحة معلومات المستند المخصصة وXSN المخصصة. ينطبق هذا القيد أيضا على الملفات التي تتضمن [مراجع](https://support.microsoft.com/en-us/office/create-a-bibliography-citations-and-references-17686589-4824-4940-9c69-342c289fa2a5)، وعلى الملفات التي تحتوي على [معرف مستند](https://support.microsoft.com/office/enable-and-configure-unique-document-ids-ea7fee86-bd6f-4cc8-9365-8086e794c984) تمت إضافتها عند تحميلها.

    بالنسبة إلى هذه الملفات، يمكنك إما تطبيق تسمية بدون تشفير بحيث يمكن فتحها لاحقا في Office على الويب، أو إرشاد المستخدمين إلى فتح الملفات في تطبيقات سطح المكتب الخاصة بهم. لا تتأثر الملفات التي تم وصفها وتشفيرها فقط في Office على الويب.

- لا يطبق SharePoint OneDrive تلقائيا تسميات الحساسية على الملفات الموجودة التي قمت بتشفيرها بالفعل باستخدام تسميات حماية البيانات Azure. بدلا من ذلك، لكي تعمل الميزات بعد تمكين تسميات الحساسية لملفات Office في SharePoint OneDrive، أكمل هذه المهام:

    1. تأكد من [ترحيل تسميات Azure حماية البيانات](/azure/information-protection/configure-policy-migrate-labels) إلى تسميات الحساسية [ونشرها](create-sensitivity-labels.md#publish-sensitivity-labels-by-creating-a-label-policy) من مدخل توافق Microsoft Purview.
    2. قم بتنزيل الملفات المسماة ثم قم بتحميلها إلى موقعها الأصلي في SharePoint أو OneDrive.

- لا يمكن SharePoint OneDrive معالجة الملفات المشفرة عندما تحتوي التسمية التي طبقت التشفير على أي من [التكوينات التالية للتشفير](encryption-sensitivity-labels.md#configure-encryption-settings):
  - **اسمح للمستخدمين بتعيين الأذونات عند تطبيق التسمية** وعلبة الاختيار **في Word، PowerPoint، Excel، مطالبة المستخدمين بتحديد الأذونات المحددة**. يشار إلى هذا الإعداد أحيانا باسم "الأذونات المعرفة من قبل المستخدم".
  - **يتم تعيين صلاحية وصول المستخدم إلى المحتوى** إلى قيمة أخرى غير **Never**.
  - تم تحديد **تشفير المفتاح المزدوج**.

    بالنسبة للتسميات التي تحتوي على أي من تكوينات التشفير هذه، لا يتم عرض التسميات للمستخدمين في Office على الويب. بالإضافة إلى ذلك، لا يمكن استخدام القدرات الجديدة مع المستندات المسماة التي تحتوي بالفعل على إعدادات التشفير هذه. على سبيل المثال، لن يتم إرجاع هذه المستندات في نتائج البحث، حتى لو تم تحديثها.

- لأسباب تتعلق بالأداء، عند تحميل مستند أو حفظه إلى SharePoint ولا تطبق تسمية الملف التشفير، قد يستغرق عمود **الحساسية** في مكتبة المستندات بعض الوقت لعرض اسم التسمية. عامل في هذا التأخير إذا كنت تستخدم البرامج النصية أو التنفيذ التلقائي الذي يعتمد على اسم التسمية في هذا العمود.

- إذا تم تسمية مستند أثناء [سحبه في SharePoint](https://support.microsoft.com/office/check-out-check-in-or-discard-changes-to-files-in-a-library-7e2c12a9-a874-4393-9511-1378a700f6de)، فلن يعرض عمود **الحساسية** في مكتبة المستندات اسم التسمية حتى يتم إيداع المستند وفتحه بعد ذلك في SharePoint.

- إذا تم تنزيل مستند مسمى ومشفر من SharePoint أو OneDrive بواسطة تطبيق أو خدمة تستخدم اسم كيان الخدمة، ثم تم تحميله مرة أخرى باستخدام تسمية تطبق إعدادات تشفير مختلفة، فسيفشل التحميل. مثال على السيناريو هو Microsoft Defender for Cloud Apps تغيير وصف الحساسية على ملف من **"سري**" إلى **"سري للغاية**"، أو من **"سري**" إلى **"عام**".

    لا يفشل التحميل إذا كان التطبيق أو الخدمة يقوم أولا بتشغيل [Unlock-SPOSensitivityLabelEncryptedFile](/powershell/module/sharepoint-online/unlock-sposensitivitylabelencryptedFile) cmdlet، كما هو موضح في [قسم إزالة المستند المسمى](#remove-encryption-for-a-labeled-document) . أو قبل التحميل، يتم حذف الملف الأصلي، أو يتم تغيير اسم الملف.

- قد يواجه المستخدمون تأخيرات في القدرة على فتح المستندات المشفرة في سيناريو "حفظ باسم" التالي: باستخدام إصدار سطح المكتب من Office، يختار المستخدم "حفظ باسم" لمستند يحتوي على وصف حساسية يطبق التشفير. يحدد المستخدم SharePoint أو OneDrive للموقع، ثم يحاول على الفور فتح هذا المستند في Office على الويب. إذا كانت الخدمة لا تزال تعالج التشفير، فسيرى المستخدم رسالة تفيد بأنه يجب فتح المستند في تطبيق سطح المكتب الخاص به. إذا حاولوا مرة أخرى بعد بضع دقائق، يتم فتح المستند بنجاح في Office على الويب.

- بالنسبة للمستندات المشفرة، لا يتم اعتماد الطباعة في Office على الويب.

- بالنسبة للمستندات المشفرة في Office على الويب، لا يتم منع النسخ إلى الحافظة ولقطات الشاشة. لمزيد من المعلومات، راجع ["هل يمكن Rights Management منع التقاط الشاشة؟](/azure/information-protection/faqs-rms#can-rights-management-prevent-screen-captures)

- بشكل افتراضي، لا تدعم تطبيقات سطح المكتب وتطبيقات الأجهزة المحمولة Office التأليف المشترك للملفات المسماة بالتشفير. تستمر هذه التطبيقات في فتح الملفات المسماة والمتشفرة في وضع التحرير الحصري.

    > [!NOTE]
    > التأليف المشترك مدعوم الآن Windows macOS. لمزيد من المعلومات، راجع [تمكين التأليف المشترك للملفات المشفرة بتسميات الحساسية](sensitivity-labels-coauthoring.md).

- إذا قام مسؤول بتغيير إعدادات تسمية منشورة تم تطبيقها بالفعل على الملفات التي تم تنزيلها إلى عميل المزامنة الخاص بالمستخدمين، فقد يتعذر على المستخدمين حفظ التغييرات التي يقومون بها على الملف في مجلد المزامنة OneDrive. ينطبق هذا السيناريو على الملفات المسماة بالتشفير، وأيضا عندما يكون تغيير التسمية من تسمية لم تطبق التشفير على تسمية تطبق التشفير. يرى المستخدمون [دائرة حمراء بها خطأ في الأيقونة المتقاطعة البيضاء](https://support.office.com/article/what-do-the-onedrive-icons-mean-11143026-8000-44f8-aaa9-67c985aa49b3)، ويطلب منهم حفظ التغييرات الجديدة كنسخة منفصلة. بدلا من ذلك، يمكنهم إغلاق الملف وإعادة فتحه، أو استخدام Office على الويب.

- يمكن للمستخدمين تجربة مشاكل الحفظ بعد العمل دون اتصال أو في وضع السكون عندما يستخدمون تطبيقات سطح المكتب والأجهزة المحمولة ل Word أو Excel أو PowerPoint بدلا من استخدام Office على الويب. بالنسبة لهؤلاء المستخدمين، عندما يستأنفون جلسة العمل تطبيق Office ويحاولون حفظ التغييرات، فإنهم يرون رسالة فشل التحميل مع خيار لحفظ نسخة بدلا من حفظ الملف الأصلي.

- لا يمكن فتح المستندات التي تم تشفيرها بالطرق التالية في Office على الويب:
  - التشفير الذي يستخدم مفتاحا محليا ("الاحتفاظ بالمفتاح الخاص بك" أو HYOK)
  - التشفير الذي تم تطبيقه باستخدام [تشفير المفتاح المزدوج](double-key-encryption.md)
  - التشفير الذي تم تطبيقه بشكل مستقل عن تسمية، على سبيل المثال، عن طريق تطبيق قالب حماية Rights Management مباشرة.

- التسميات التي تم تكوينها [للغات الأخرى](create-sensitivity-labels.md#additional-label-settings-with-security--compliance-powershell) غير معتمدة وتعرض اللغة الأصلية فقط.

- إذا حذفت تسمية تم تطبيقها على مستند في SharePoint أو OneDrive، بدلا من إزالة التسمية من نهج التسمية المعمول به، فلن يتم تسمية المستند عند تنزيله أو تشفيره. بالمقارنة، إذا تم تخزين المستند المسمى خارج SharePoint أو OneDrive، يظل المستند مشفرا إذا تم حذف التسمية. لاحظ أنه على الرغم من أنك قد تحذف التسميات أثناء مرحلة الاختبار، إلا أنه من النادر جدا حذف تسمية في بيئة إنتاج.

## <a name="how-to-enable-sensitivity-labels-for-sharepoint-and-onedrive-opt-in"></a>كيفية تمكين أوصاف الحساسية SharePoint OneDrive (الاشتراك)

يمكنك تمكين القدرات الجديدة باستخدام مدخل توافق Microsoft Purview، أو باستخدام PowerShell. كما هو الحال مع جميع تغييرات التكوين على مستوى المستأجر SharePoint OneDrive، يستغرق سريان التغيير حوالي 15 دقيقة.

### <a name="use-the-microsoft-purview-compliance-portal-to-enable-support-for-sensitivity-labels"></a>استخدام مدخل الامتثال ل Microsoft Purview لتمكين دعم أوصاف الحساسية

هذا الخيار هو أسهل طريقة لتمكين تسميات الحساسية SharePoint OneDrive، ولكن يجب عليك تسجيل الدخول كمسؤول عام للمستأجر الخاص بك.

1. سجل الدخول إلى [مدخل توافق Microsoft Purview](https://compliance.microsoft.com/) كمسؤول عام، وانتقل إلى **تسميات** **حماية** >  معلومات **الحلول** > 

2. إذا رأيت رسالة لتشغيل القدرة على معالجة المحتوى في Office الملفات عبر الإنترنت، فحدد **"تشغيل الآن**":

    ![قم بتشغيل الزر الآن لتمكين تسميات الحساسية ل Office Online.](../media/sensitivity-labels-turn-on-banner.png)

    يتم تشغيل الأمر على الفور وعند تحديث الصفحة بعد ذلك، لن تتمكن من رؤية الرسالة أو الزر.

> [!NOTE]
> إذا كان لديك Microsoft 365 Multi-Geo، يجب عليك استخدام PowerShell لتمكين هذه الإمكانات لجميع المواقع الجغرافية الخاصة بك. راجع القسم التالي للحصول على التفاصيل.

### <a name="use-powershell-to-enable-support-for-sensitivity-labels"></a>استخدام PowerShell لتمكين دعم أوصاف الحساسية

كبديل لاستخدام مدخل توافق Microsoft Purview، يمكنك تمكين دعم تسميات الحساسية باستخدام [Set-SPOTenant](/powershell/module/sharepoint-online/set-spotenant) cmdlet من SharePoint Online PowerShell.

إذا كان لديك Microsoft 365 Multi-Geo، يجب استخدام PowerShell لتمكين هذا الدعم لجميع المواقع الجغرافية الخاصة بك.

#### <a name="prepare-the-sharepoint-online-management-shell"></a>إعداد SharePoint Online Management Shell

قبل تشغيل أمر PowerShell لتمكين تسميات الحساسية لملفات Office في SharePoint OneDrive، تأكد من تشغيل SharePoint Online Management Shell الإصدار 16.0.19418.12000 أو أحدث. إذا كان لديك الإصدار الأخير بالفعل، يمكنك التخطي إلى [الإجراء التالي](#run-the-powershell-command-to-enable-support-for-sensitivity-labels) لتشغيل أمر PowerShell.

1. إذا قمت بتثبيت إصدار سابق من SharePoint Online Management Shell من معرض PowerShell، يمكنك تحديث الوحدة النمطية عن طريق تشغيل cmdlet التالي.

    ```PowerShell
    Update-Module -Name Microsoft.Online.SharePoint.PowerShell
    ```

2. بدلا من ذلك، إذا قمت بتثبيت إصدار سابق من SharePoint Online Management Shell من مركز تنزيل Microsoft، يمكنك أيضا الانتقال إلى **إضافة برامج أو إزالتها** وإلغاء تثبيت SharePoint Online Management Shell.

3. في مستعرض ويب، انتقل إلى صفحة "مركز التنزيل" وقم [بتنزيل أحدث SharePoint Online Management Shell](https://go.microsoft.com/fwlink/p/?LinkId=255251).

4. حدد لغتك ثم انقر فوق **"تنزيل**".

5. اختر بين ملف .msi x64 وx86. قم بتنزيل ملف x64 إذا قمت بتشغيل الإصدار 64 بت من Windows أو ملف x86 إذا قمت بتشغيل الإصدار 32 بت. إذا كنت لا تعرف، فراجع [أي إصدار من نظام التشغيل Windows أقوم بتشغيله؟](https://support.microsoft.com/help/13443/windows-which-operating-system)

6. بعد تنزيل الملف، قم بتشغيل الملف واتبع الخطوات الواردة في معالج الإعداد.

#### <a name="run-the-powershell-command-to-enable-support-for-sensitivity-labels"></a>تشغيل الأمر PowerShell لتمكين دعم أوصاف الحساسية

لتمكين القدرات الجديدة، استخدم [Set-SPOTenant](/powershell/module/sharepoint-online/set-spotenant) cmdlet مع المعلمة *EnableAIPIntegration* :

1. باستخدام حساب العمل أو المؤسسة التعليمية الذي لديه امتيازات مسؤول عمومي أو مسؤول SharePoint في Microsoft 365، اتصل SharePoint. لمعرفة كيفية ذلك، راجع [بدء استخدام SharePoint Online Management Shell](/powershell/sharepoint/sharepoint-online/connect-sharepoint-online).

    > [!NOTE]
    > إذا كان لديك Microsoft 365 Multi-Geo، فاستخدم معلمة -Url مع [الاتصال-SPOService](/powershell/module/sharepoint-online/connect-sposervice)، وحدد عنوان URL لموقع مركز الإدارة عبر الإنترنت SharePoint لأحد المواقع الجغرافية الخاصة بك.

2. قم بتشغيل الأمر التالي واضغط **على Y** للتأكيد:

    ```PowerShell
    Set-SPOTenant -EnableAIPIntegration $true
    ```
3. بالنسبة Microsoft 365 متعدد المناطق الجغرافية: كرر الخطوتي 1 و2 لكل موقع من المواقع الجغرافية المتبقية.

## <a name="publishing-and-changing-sensitivity-labels"></a>نشر تسميات الحساسية وتغييرها

عند استخدام تسميات الحساسية مع SharePoint OneDrive، ضع في اعتبارك أنك تحتاج إلى السماح بوقت النسخ المتماثل عند نشر تسميات حساسية جديدة أو تحديث تسميات الحساسية الموجودة. هذا مهم بشكل خاص للتسميات الجديدة التي تطبق التشفير.

على سبيل المثال: يمكنك إنشاء تسمية حساسية جديدة تطبق التشفير ونشرها وتظهر بسرعة كبيرة في تطبيق سطح المكتب الخاص بالمستخدم. يطبق المستخدم هذه التسمية على مستند ثم يقوم بتحميلها إلى SharePoint أو OneDrive. إذا لم يكتمل النسخ المتماثل للتسمية للخدمة، فلن يتم تطبيق الإمكانيات الجديدة على هذا المستند عند التحميل. ونتيجة لذلك، لن يتم إرجاع المستند في البحث أو عن eDiscovery ولا يمكن فتح المستند في Office على الويب.

لمزيد من المعلومات حول توقيت التسميات، راجع ["متى تتوقع تطبيق تسميات وتغييرات جديدة](create-sensitivity-labels.md#when-to-expect-new-labels-and-changes-to-take-effect)".

كحماية، نوصي بنشر تسميات جديدة لعدد قليل من مستخدمي الاختبار أولا، والانتظار لمدة ساعة واحدة على الأقل، ثم التحقق من سلوك التسمية على SharePoint OneDrive. انتظر يوما على الأقل قبل إتاحة التسمية لمزيد من المستخدمين إما بإضافة المزيد من المستخدمين إلى نهج التسمية الموجود، أو إضافة التسمية إلى نهج تسمية موجود للمستخدمين القياسيين. بحلول الوقت الذي يرى فيه المستخدمون القياسيون التسمية، فقد تمت مزامنتها بالفعل مع SharePoint OneDrive.

## <a name="sharepoint-information-rights-management-irm-and-sensitivity-labels"></a>SharePoint معلومات Rights Management (IRM) وتسميات الحساسية

[SharePoint المعلومات Rights Management (IRM)](set-up-irm-in-sp-admin-center.md) هي تقنية قديمة لحماية الملفات على مستوى القائمة والمكتبة من خلال تطبيق التشفير والقيود عند تنزيل الملفات. تم تصميم تقنية الحماية القديمة هذه لمنع المستخدمين غير المصرح لهم من فتح الملف في أثناء وجوده خارج SharePoint.

بالمقارنة، توفر تسميات الحساسية إعدادات الحماية للعلامات المرئية (الرؤوس والتذييلات والعلامات المائية) بالإضافة إلى التشفير. تدعم إعدادات التشفير النطاق الكامل [من حقوق الاستخدام](/azure/information-protection/configure-usage-rights) لتقييد ما يمكن للمستخدمين القيام به مع المحتوى، ويتم دعم نفس تسميات الحساسية [للعديد من السيناريوهات](get-started-with-sensitivity-labels.md#common-scenarios-for-sensitivity-labels). يؤدي استخدام أسلوب الحماية نفسه مع إعدادات متسقة عبر أحمال العمل والتطبيقات إلى استراتيجية حماية متسقة.

ومع ذلك، يمكنك استخدام كل من حلول الحماية معا والسلوك كما يلي:

- إذا قمت بتحميل ملف مع وصف الحساسية الذي يطبق التشفير، SharePoint لا يمكن معالجة محتوى هذه الملفات لذلك لا يتم دعم التأليف المشترك وeDiscovery وDLP والبحث لهذه الملفات.

- إذا قمت بتسمية ملف باستخدام Office على الويب، يتم فرض أي إعدادات تشفير من التسمية. بالنسبة إلى هذه الملفات، يتم دعم التأليف المشترك وeDiscovery وDLP والبحث.

- إذا قمت بتنزيل ملف تمت تسميته باستخدام Office على الويب، يتم الاحتفاظ بالتسمية ويتم فرض أي إعدادات تشفير من التسمية بدلا من إعدادات تقييد IRM.

- إذا قمت بتنزيل ملف Office أو ملف PDF غير مشفر بتسمية الحساسية، يتم تطبيق إعدادات IRM.

- إذا قمت بتمكين أي من إعدادات مكتبة IRM الإضافية، والتي تتضمن منع المستخدمين من تحميل المستندات التي لا تدعم IRM، يتم فرض هذه الإعدادات.

باستخدام هذا السلوك، يمكنك التأكد من أن جميع ملفات Office وPDF محمية من الوصول غير المصرح به إذا تم تنزيلها، حتى لو لم يتم وصفها. ومع ذلك، لن تستفيد الملفات المسماة التي يتم تحميلها من القدرات الجديدة.

## <a name="search-for-documents-by-sensitivity-label"></a>البحث عن المستندات حسب وصف الحساسية

استخدم الخاصية المدارة **InformationProtectionLabelId** للعثور على جميع المستندات في SharePoint أو OneDrive التي تحتوي على وصف حساسية معين. استخدم بناء الجملة التالي: `InformationProtectionLabelId:<GUID>`

على سبيل المثال، للبحث عن كافة المستندات التي تمت تسميتها باسم "سري"، وتتضمن هذه التسمية GUID من "8faca7b8-8d20-48a3-8ea2-0f96310a848e"، في مربع البحث، اكتب:

```
InformationProtectionLabelId:8faca7b8-8d20-48a3-8ea2-0f96310a848e
```

لن يعثر البحث على المستندات المسماة في ملف مضغوط، مثل ملف .zip.

للحصول على GUIDs لأوصاف الحساسية الخاصة بك، استخدم [Get-Label](/powershell/module/exchange/get-label) cmdlet:

1. أولا، [اتصل Office 365 Security & Compliance PowerShell](/powershell/exchange/office-365-scc/connect-to-scc-powershell/connect-to-scc-powershell).

    على سبيل المثال، في جلسة PowerShell التي تقوم بتشغيلها كمسؤول، سجل الدخول باستخدام حساب مسؤول عام.

2. ثم قم بتشغيل الأمر التالي:

    ```powershell
    Get-Label |ft Name, Guid
    ```

لمزيد من المعلومات حول استخدام الخصائص [المدارة، راجع إدارة مخطط البحث في SharePoint](/sharepoint/manage-search-schema).

## <a name="remove-encryption-for-a-labeled-document"></a>إزالة التشفير لمستند مسمى

قد تكون هناك حالات نادرة يحتاج فيها مسؤول SharePoint إلى إزالة التشفير من مستند مخزن في SharePoint. يمكن لأي مستخدم لديه [حق استخدام Rights Management](/azure/information-protection/configure-usage-rights#usage-rights-and-descriptions) الخاص بتصدير أو التحكم الكامل المعين له لهذا المستند إزالة التشفير الذي تم تطبيقه بواسطة خدمة Rights Management Azure من Azure حماية البيانات. على سبيل المثال، يمكن للمستخدمين الذين لديهم أي من حقوق الاستخدام هذه استبدال تسمية تطبق التشفير بتسمية بدون تشفير. يمكن [للمستخدم الفائق](/azure/information-protection/configure-super-users) أيضا تنزيل الملف وحفظ نسخة محلية دون التشفير.

كبديل، يمكن [لمسؤول عام أو مسؤول SharePoint](/sharepoint/sharepoint-admin-role) تشغيل [Unlock-SPOSensitivityLabelEncryptedFile](/powershell/module/sharepoint-online/unlock-sposensitivitylabelencryptedFile) cmdlet، الذي يزيل كل من وصف الحساسية والتشفير. يتم تشغيل أمر cmdlet هذا حتى إذا لم يكن لدى المسؤول أذونات الوصول إلى الموقع أو الملف، أو إذا كانت خدمة Rights Management Azure غير متوفرة.

على سبيل المثال:

```powershell
Unlock-SPOSensitivityLabelEncryptedFile -FileUrl "https://contoso.com/sites/Marketing/Shared Documents/Doc1.docx" -JustificationText "Need to decrypt this file"
```

الاحتياجات:

- SharePoint Online Management Shell الإصدار 16.0.20616.12000 أو إصدار أحدث.

- تم تطبيق التشفير بواسطة تسمية حساسية مع إعدادات التشفير المعرفة من قبل المسؤول (إعدادات [التسمية تعيين الأذونات الآن](encryption-sensitivity-labels.md#assign-permissions-now) ). [تشفير المفتاح المزدوج](encryption-sensitivity-labels.md#double-key-encryption) غير معتمد ل cmdlet هذا.

تتم إضافة نص الضبط إلى [حدث التدقيق](search-the-audit-log-in-security-and-compliance.md#sensitivity-label-activities) **لتسمية الحساسية التي تمت إزالتها من الملف**، ويتم أيضا تسجيل إجراء فك التشفير في [تسجيل استخدام الحماية ل Azure حماية البيانات](/azure/information-protection/log-analyze-usage).

## <a name="how-to-disable-sensitivity-labels-for-sharepoint-and-onedrive-opt-out"></a>كيفية تعطيل تسميات الحساسية SharePoint OneDrive (إلغاء الاشتراك)

إذا قمت بتعطيل هذه الإمكانات الجديدة، فستستمر حماية الملفات التي قمت بتحميلها بعد تمكين تسميات الحساسية SharePoint OneDrive بواسطة التسمية لأن إعدادات التسمية تستمر في فرضها. عند تطبيق تسميات الحساسية على الملفات الجديدة بعد تعطيل هذه القدرات الجديدة، لن يعمل البحث عن النص الكامل وeDiscovery والتأليف المشترك.

لتعطيل هذه القدرات الجديدة، يجب استخدام PowerShell. باستخدام SharePoint Online Management Shell و [Set-SPOTenant](/powershell/module/sharepoint-online/set-spotenant) cmdlet، حدد نفس معلمة *EnableAIP Workload* كما هو موضح في قسم [Use PowerShell لتمكين دعم تسميات الحساسية](#use-powershell-to-enable-support-for-sensitivity-labels). ولكن هذه المرة، قم بتعيين قيمة المعلمة إلى خطأ واضغط **على Y** للتأكيد:

```PowerShell
Set-SPOTenant -EnableAIPIntegration $false
```

إذا كان لديك Microsoft 365 Multi-Geo، يجب تشغيل هذا الأمر لكل موقع من مواقعك الجغرافية.

## <a name="next-steps"></a>الخطوات التالية

بعد تمكين تسميات الحساسية لملفات Office في SharePoint OneDrive، ضع في اعتبارك تسمية هذه الملفات تلقائيا باستخدام نهج التسمية التلقائية. لمزيد من المعلومات، راجع [تطبيق وصف الحساسية على المحتوى تلقائيا](apply-sensitivity-label-automatically.md).

هل تحتاج إلى مشاركة مستنداتك المسماة والمتشفرة مع أشخاص من خارج مؤسستك؟  راجع [مشاركة المستندات المشفرة مع مستخدمين خارجيين](sensitivity-labels-office-apps.md#sharing-encrypted-documents-with-external-users).
