---
title: تشفير المفتاح المزدوج (DKE)
description: يمكنك DKE من حماية البيانات شديدة الحساسية مع الحفاظ على التحكم الكامل في المفتاح الخاص بك.
author: kccross
ms.author: krowley
manager: laurawi
ms.date: 02/28/2022
ms.topic: conceptual
ms.service: information-protection
audience: Admin
ms.reviewer: esaggese
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
ms.custom: admindeeplinkCOMPLIANCE
ms.openlocfilehash: 74194d4bca71350c180799e071936b75044a6b4e
ms.sourcegitcommit: 612ce4d15d8a2fdbf7795393b50af477d81b6139
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 05/24/2022
ms.locfileid: "65663679"
---
# <a name="double-key-encryption"></a>تشفير المفتاح المزدوج

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

> *ينطبق على: تشفير المفتاح المزدوج Microsoft Purview [، Microsoft Purview](https://www.microsoft.com/microsoft-365/business/compliance-management)، [وAzure حماية البيانات](https://azure.microsoft.com/pricing/)*
>
> *إرشادات ل: [عميل تسمية موحد ل Azure حماية البيانات Windows](/azure/information-protection/faqs#whats-the-difference-between-the-azure-information-protection-classic-and-unified-labeling-clients)*

> *وصف الخدمة ل: [Microsoft Purview](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance)*

يستخدم تشفير المفتاح المزدوج (DKE) مفتاحين معا للوصول إلى المحتوى المحمي. تخزن Microsoft مفتاحا واحدا في Microsoft Azure، وتحتفظ بالمفتاح الآخر. يمكنك الحفاظ على التحكم الكامل لأحد مفاتيحك باستخدام خدمة تشفير المفتاح المزدوج. يمكنك تطبيق الحماية باستخدام عميل التسمية الموحد ل Azure حماية البيانات على المحتوى الحساس للغاية.

يدعم تشفير المفتاح المزدوج كلا من عمليات النشر السحابية والمحلية. تساعد عمليات النشر هذه على ضمان بقاء البيانات المشفرة معتمة أينما قمت بتخزين البيانات المحمية.

لمزيد من المعلومات حول مفاتيح جذر المستأجر الافتراضية المستندة إلى السحابة، راجع [تخطيط وتنفيذ مفتاح مستأجر Azure حماية البيانات](/azure/information-protection/plan-implement-tenant-key).

## <a name="when-your-organization-should-adopt-dke"></a>متى يجب على مؤسستك اعتماد DKE

إن تشفير المفتاح المزدوج مخصص لبياناتك الأكثر حساسية التي تخضع لأدق متطلبات الحماية. DKE غير مخصص لجميع البيانات. بشكل عام، ستستخدم تشفير المفتاح المزدوج لحماية جزء صغير فقط من بياناتك الإجمالية. يجب عليك بذل العناية اللازمة في تحديد البيانات الصحيحة التي يجب تغطيتها بهذا الحل قبل النشر. في بعض الحالات، قد تحتاج إلى تضييق نطاقك واستخدام حلول أخرى لمعظم بياناتك، مثل حماية البيانات في Microsoft Purview باستخدام المفاتيح التي تديرها Microsoft أو BYOK. هذه الحلول كافية للمستندات التي لا تخضع لحماية محسنة ومتطلبات تنظيمية. كما تمكنك هذه الحلول من استخدام خدمات Office 365 الأقوى؛ وهي الخدمات التي لا يمكنك استخدامها مع المحتوى المشفر ل DKE. على سبيل المثال:

- قواعد النقل بما في ذلك مكافحة البرامج الضارة والبريد العشوائي التي تتطلب رؤية المرفق
- Microsoft Delve
- eDiscovery
- البحث عن المحتوى وفهرسته
- Office Web Apps بما في ذلك وظيفة التأليف المشترك

لن تتمكن أي تطبيقات أو خدمات خارجية غير مدمجة مع DKE من خلال حماية البيانات في Microsoft (MIP) SDK من تنفيذ الإجراءات على البيانات المشفرة.

يدعم حماية البيانات في Microsoft SDK 1.7+ تشفير المفتاح المزدوج. يمكن للتطبيقات التي تتكامل مع SDK لدينا التفكير في هذه البيانات مع وجود أذونات وتكاملات كافية.

استخدم قدرات حماية البيانات في Microsoft Purview (التصنيف والتسمية) لحماية معظم بياناتك الحساسة واستخدام DKE فقط للبيانات المهمة. يعد تشفير المفتاح المزدوج مناسبا للبيانات الحساسة في الصناعات شديدة التنظيم مثل الخدمات المالية والرعاية الصحية.

إذا كان لدى مؤسستك أي من المتطلبات التالية، يمكنك استخدام DKE للمساعدة في تأمين المحتوى الخاص بك:

- تريد التأكد من أنه *يمكنك فقط* فك تشفير المحتوى المحمي، في جميع الظروف.
- لا تريد أن يكون لدى Microsoft حق الوصول إلى البيانات المحمية بمفردها.
- لديك متطلبات تنظيمية للاحتفاظ المفاتيح داخل حدود جغرافية. يتم الاحتفاظ بجميع المفاتيح التي تحتفظ بها لتشفير البيانات وفك تشفيرها في مركز البيانات.

## <a name="system-and-licensing-requirements-for-dke"></a>متطلبات النظام والترخيص ل DKE

يأتي **تشفير المفتاح المزدوج** مع Microsoft 365 E5. إذا لم يكن لديك ترخيص Microsoft 365 E5، يمكنك التسجيل للحصول على [إصدار تجريبي](https://aka.ms/M365E5ComplianceTrial). لمزيد من المعلومات حول هذه التراخيص، راجع [إرشادات الترخيص Microsoft 365 للامتثال & الأمان](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).

**Azure حماية البيانات**. يعمل DKE مع تسميات الحساسية ويتطلب حماية البيانات Azure.

يتم توفير تسميات حساسية DKE للمستخدمين النهائيين من خلال زر الحساسية في عميل الوصف الموحد AIP في تطبيقات سطح المكتب Office. قم بتثبيت هذه المتطلبات الأساسية على كل كمبيوتر عميل حيث تريد حماية المستندات المحمية واستهلاكها.

**Microsoft Office Apps for enterprise** الإصدار 2009 أو الإصدارات الأحدث (إصدارات سطح المكتب من Word و PowerPoint Excel) على Windows.

**Azure حماية البيانات إصدارات عميل التسمية الموحدة** 2.7.93.0 أو أحدث. قم بتنزيل عميل التسمية الموحدة وتثبيته من [مركز تنزيل Microsoft](https://www.microsoft.com/download/details.aspx?id=53018).

## <a name="supported-environments-for-storing-and-viewing-dke-protected-content"></a>البيئات المدعومة لتخزين المحتوى المحمي ب DKE وعرضه

**التطبيقات المدعومة**. [Microsoft 365 Apps for enterprise](https://www.microsoft.com/microsoft-365/business/microsoft-365-apps-for-enterprise-product) العملاء على Windows، بما في ذلك Word و Excel و PowerPoint.

**دعم المحتوى عبر الإنترنت**. يمكنك تخزين المستندات والملفات المحمية بتشفير المفتاح المزدوج عبر الإنترنت في كل من Microsoft SharePoint OneDrive for Business. يجب عليك تسمية المستندات والملفات وحمايتها باستخدام DKE بواسطة التطبيقات المدعومة قبل التحميل إلى هذه المواقع. يمكنك مشاركة المحتوى المشفر عبر البريد الإلكتروني، ولكن لا يمكنك عرض المستندات والملفات المشفرة عبر الإنترنت. بدلا من ذلك، يجب عرض المحتوى المحمي باستخدام تطبيقات سطح المكتب والعملاء المعتمدين على الكمبيوتر المحلي.

## <a name="overview-of-deploying-dke"></a>نظرة عامة على توزيع DKE

ستتبع هذه الخطوات العامة لإعداد DKE. بمجرد الانتهاء من هذه الخطوات، يمكن للمستخدمين النهائيين حماية بياناتك الحساسة للغاية باستخدام تشفير المفتاح المزدوج.

1. نشر خدمة DKE كما هو موضح في هذه المقالة.

2. إنشاء تسمية باستخدام تشفير المفتاح المزدوج. في مدخل التوافق في Microsoft Purview، انتقل إلى **حماية المعلومات** وأنشئ تسمية جديدة باستخدام تشفير المفتاح المزدوج. راجع [تقييد الوصول إلى المحتوى باستخدام تسميات الحساسية لتطبيق التشفير](./encryption-sensitivity-labels.md).

3. استخدم تسميات تشفير المفتاح المزدوج. حماية البيانات عن طريق تحديد تسمية مشفر المفتاح المزدوج من شريط الحساسية في Microsoft Office.

هناك عدة طرق يمكنك من خلالها إكمال بعض الخطوات لنشر تشفير المفتاح المزدوج. توفر هذه المقالة إرشادات مفصلة بحيث يقوم المسؤولون الأقل خبرة بنشر الخدمة بنجاح. إذا كنت مرتاحا للقيام بذلك، يمكنك اختيار استخدام أساليبك الخاصة.

## <a name="deploy-dke"></a>توزيع DKE

تستخدم هذه المقالة وفيديو النشر Azure كوجهة توزيع لخدمة DKE. إذا كنت تقوم بالنشر في موقع آخر، فستحتاج إلى توفير قيمك الخاصة.

شاهد [فيديو نشر تشفير المفتاح المزدوج](https://youtu.be/vDWfHN_kygg) للاطلاع على نظرة عامة خطوة بخطوة على المفاهيم الواردة في هذه المقالة. يستغرق إكمال الفيديو حوالي 18 دقيقة.

ستتبع هذه الخطوات العامة لإعداد تشفير المفتاح المزدوج لمؤسستك.

1. [تثبيت المتطلبات الأساسية للبرامج لخدمة DKE](#install-software-prerequisites-for-the-dke-service)
1. [استنساخ مستودع GitHub تشفير المفتاح المزدوج](#clone-the-dke-github-repository)
1. [تعديل إعدادات التطبيق](#modify-application-settings)
1. [إنشاء مفاتيح اختبار](#generate-test-keys)
1. [إنشاء المشروع](#build-the-project)
1. [نشر خدمة DKE ونشر مخزن المفاتيح](#deploy-the-dke-service-and-publish-the-key-store)
1. [التحقق من صحة النشر](#validate-your-deployment)
1. [تسجيل مخزن المفاتيح](#register-your-key-store)
1. [إنشاء تسميات الحساسية باستخدام DKE](#create-sensitivity-labels-using-dke)
1. [تمكين DKE في عميلك](#enable-dke-in-your-client)
1. [ترحيل الملفات المحمية من تسميات HYOK إلى تسميات DKE](#migrate-protected-files-from-hyok-labels-to-dke-labels)

عند الانتهاء، يمكنك تشفير المستندات والملفات باستخدام DKE. للحصول على معلومات، راجع [تطبيق تسميات الحساسية على ملفاتك والبريد الإلكتروني في Office](https://support.microsoft.com/office/2f96e7cd-d5a4-403b-8bd7-4cc636bae0f9).

### <a name="install-software-prerequisites-for-the-dke-service"></a>تثبيت المتطلبات الأساسية للبرامج لخدمة DKE

قم بتثبيت هذه المتطلبات الأساسية على الكمبيوتر حيث تريد تثبيت خدمة DKE.

**.NET Core 3.1 SDK**. قم بتنزيل SDK وتثبيته من [تنزيل .NET Core 3.1](https://dotnet.microsoft.com/download/dotnet-core/3.1).

**Visual Studio التعليمات البرمجية**. تنزيل Visual Studio Code من [https://code.visualstudio.com/](https://code.visualstudio.com). بمجرد التثبيت، قم بتشغيل Visual Studio التعليمات البرمجية وحدد **View** \> **Extensions**. تثبيت هذه الملحقات.

- C# للتعليمات البرمجية Visual Studio

- nuGet مدير الحِزَم

**موارد Git**. قم بتنزيل أحد الإجراءات التالية وتثبيته.

- [بوابه](https://git-scm.com/downloads)

- [GitHub سطح المكتب](https://desktop.github.com/)

- [GitHub Enterprise](https://github.com/enterprise)

**بينسل** يجب أن يكون [OpenSSL](https://slproweb.com/products/Win32OpenSSL.html) مثبتا [لإنشاء مفاتيح اختبار](#generate-test-keys) بعد نشر DKE. تأكد من استدعائه بشكل صحيح من مسار متغيرات البيئة الخاصة بك. على سبيل المثال، راجع "إضافة دليل التثبيت إلى PATH" للحصول على [https://www.osradar.com/install-openssl-windows/](https://www.osradar.com/install-openssl-windows/) التفاصيل.

### <a name="clone-the-dke-github-repository"></a>استنساخ مستودع GitHub DKE

توفر Microsoft ملفات مصدر DKE في مستودع GitHub. يمكنك استنساخ المستودع لإنشاء المشروع محليا لاستخدام مؤسستك. يوجد مستودع GitHub DKE في [https://github.com/Azure-Samples/DoubleKeyEncryptionService](https://github.com/Azure-Samples/DoubleKeyEncryptionService).

الإرشادات التالية مخصصة لمستخدمي git أو Visual Studio Code عديمي الخبرة:

1. في المستعرض، انتقل إلى: [https://github.com/Azure-Samples/DoubleKeyEncryptionService](https://github.com/Azure-Samples/DoubleKeyEncryptionService).

2. باتجاه الجانب الأيسر من الشاشة، حدد **التعليمات البرمجية**. قد يظهر إصدار واجهة المستخدم زر **النسخ أو التنزيل** . ثم في القائمة المنسدلة التي تظهر، حدد أيقونة النسخ لنسخ عنوان URL إلى الحافظة.

    على سبيل المثال:

   > [!div class="mx-imgBorder"]
   > ![استنساخ مستودع خدمة تشفير المفتاح المزدوج من GitHub.](../media/dke-clone.png)

3. في Visual Studio Code، حدد **View** \> **Command Palette** وحدد **Git: Clone**. للانتقال إلى الخيار في القائمة، ابدأ الكتابة `git: clone` لتصفية الإدخالات ثم حددها من القائمة المنسدلة. على سبيل المثال:

   > [!div class="mx-imgBorder"]
   > ![Visual Studio Code GIT:Clone option.](../media/dke-vscode-clone.png)

4. في مربع النص، الصق عنوان URL الذي نسخته من Git وحدد **Clone من GitHub**.

5. في مربع الحوار **"تحديد مجلد"** الذي يظهر، استعرض وصولا إلى موقع لتخزين المستودع وحدده. في المطالبة، حدد **"فتح**".

    يفتح المستودع في Visual Studio Code، ويعرض فرع Git الحالي في أسفل اليسار. على سبيل المثال، يجب أن يكون الفرع **رئيسيا**. على سبيل المثال:

   ![لقطة شاشة لمورد DKE في Visual Studio Code يعرض الفرع الرئيسي.](../media/dke-vscode-main-branch.jpg)

6. إذا لم تكن في الفرع الرئيسي، فستحتاج إلى تحديده. في Visual Studio Code، حدد الفرع واختر **الفرع الرئيسي** من قائمة الفروع التي يتم عرضها.

   > [!IMPORTANT]
   > يضمن تحديد الفرع الرئيسي أن لديك الملفات الصحيحة لإنشاء المشروع. إذا لم تختر الفرع الصحيح، فسيفشل التوزيع.

لديك الآن مستودع مصدر DKE الخاص بك تم إعداده محليا. بعد ذلك، [قم بتعديل إعدادات التطبيق](#modify-application-settings) لمؤسستك.

### <a name="modify-application-settings"></a>تعديل إعدادات التطبيق

لنشر خدمة DKE، يجب تعديل الأنواع التالية من إعدادات التطبيق:

- [إعدادات الوصول إلى المفاتيح](#key-access-settings)
- [إعدادات المستأجر والمفتاح](#tenant-and-key-settings)

يمكنك تعديل إعدادات التطبيق في ملف appsettings.json. يوجد هذا الملف في مستودع DoubleKeyEncryptionService الذي نسخته محليا ضمن DoubleKeyEncryptionService\src\customer-key-store. على سبيل المثال، في Visual Studio Code، يمكنك الاستعراض وصولا إلى الملف كما هو موضح في الصورة التالية.

![تحديد موقع ملف appsettings.json ل DKE.](../media/dke-appsettingsjson.png)

#### <a name="key-access-settings"></a>إعدادات الوصول إلى المفاتيح

اختر ما إذا كنت تريد استخدام البريد الإلكتروني أو تخويل الدور. يدعم DKE أسلوبا واحدا فقط من أساليب المصادقة هذه في كل مرة.

- **تخويل البريد الإلكتروني**. يسمح لمؤسستك بتخويل الوصول إلى المفاتيح استنادا إلى عناوين البريد الإلكتروني فقط.

- **تخويل الدور**. يسمح لمؤسستك بتخويل الوصول إلى المفاتيح استنادا إلى مجموعات Active Directory، ويتطلب أن تقوم خدمة الويب بالاستعلام عن LDAP.

##### <a name="to-set-key-access-settings-for-dke-using-email-authorization"></a>لتعيين إعدادات الوصول الرئيسية ل DKE باستخدام تخويل البريد الإلكتروني

1. افتح ملف **appsettings.json** وحدد موقع `AuthorizedEmailAddress` الإعداد.

2. أضف عنوان البريد الإلكتروني أو العناوين التي تريد تخويلها. افصل عناوين البريد الإلكتروني المتعددة باستخدام علامات اقتباس وفاواصل مزدوجة. على سبيل المثال:

   ```json
   "AuthorizedEmailAddress": ["email1@company.com", "email2@company.com ", "email3@company.com"]
   ```

3. `LDAPPath` حدد موقع الإعداد وقم بإزالة النص `If you use role authorization (AuthorizedRoles) then this is the LDAP path.` بين علامتي الاقتباس المزدوجتين. اترك علامات الاقتباس المزدوجة في مكانها. عند الانتهاء، يجب أن يبدو الإعداد كما يلي.

   ```json
   "LDAPPath": ""
   ```

4. `AuthorizedRoles` حدد موقع الإعداد واحذف السطر بأكمله.

تعرض هذه الصورة ملف **appsettings.json** المنسق بشكل صحيح للتخويل بالبريد الإلكتروني.

   ![ملف appsettings.json يعرض طريقة تخويل البريد الإلكتروني.](../media/dke-email-accesssetting.png)

##### <a name="to-set-key-access-settings-for-dke-using-role-authorization"></a>لتعيين إعدادات الوصول الرئيسية ل DKE باستخدام تخويل الدور

1. افتح ملف **appsettings.json** وحدد موقع `AuthorizedRoles` الإعداد.

2. أضف أسماء مجموعة Active Directory التي تريد تخويلها. افصل أسماء مجموعات متعددة باستخدام علامات اقتباس وفاواصل مزدوجة. على سبيل المثال:

   ```json
   "AuthorizedRoles": ["group1", "group2", "group3"]
   ```

3. `LDAPPath` حدد موقع الإعداد وأضف مجال Active Directory. على سبيل المثال:

   ```json
   "LDAPPath": "contoso.com"
   ```

4. `AuthorizedEmailAddress` حدد موقع الإعداد واحذف السطر بأكمله.

تعرض هذه الصورة ملف **appsettings.json** المنسق بشكل صحيح للحصول على تخويل الدور.

   ![ملف appsettings.json يعرض أسلوب تخويل الدور.](../media/dke-role-accesssetting.png)

#### <a name="tenant-and-key-settings"></a>إعدادات المستأجر والمفتاح

يوجد مستأجر DKE وإعدادات المفاتيح في ملف **appsettings.json** .

##### <a name="to-configure-tenant-and-key-settings-for-dke"></a>لتكوين إعدادات المستأجر والمفتاح ل DKE

1. افتح ملف **appsettings.json** .

2. `ValidIssuers` حدد موقع الإعداد واستبدله `<tenantid>` بمعرف المستأجر. يمكنك تحديد موقع معرف المستأجر الخاص بك عن طريق الانتقال إلى مدخل Azure وعرض [خصائص المستأجر](https://aad.portal.azure.com/#blade/Microsoft_AAD_IAM/ActiveDirectoryMenuBlade/Properties). على سبيل المثال:

   ```json
   "ValidIssuers": [
     "https://sts.windows.net/9c99431e-b513-44be-a7d9-e7b500002d4b/"
   ]
   ```

> [!NOTE]
> إذا كنت تريد تمكين وصول B2B الخارجي إلى مخزن المفاتيح الخاص بك، فستحتاج أيضا إلى تضمين هذه المستأجرين الخارجيين كجزء من قائمة المصدرين الصالحين.

`JwtAudience`حدد موقع . استبدل `<yourhostname>` باسم مضيف الجهاز حيث سيتم تشغيل خدمة DKE. على سبيل المثال:

  > [!IMPORTANT]
  > يجب أن تتطابق قيمة `JwtAudience` المضيف *تماما* مع اسم المضيف. يمكنك استخدام **localhost:5001** أثناء تصحيح الأخطاء. ومع ذلك، عند الانتهاء من تصحيح الأخطاء، تأكد من تحديث هذه القيمة إلى اسم مضيف الخادم.

- `TestKeys:Name`. أدخل اسما للمفتاح. على سبيل المثال: `TestKey1`
- `TestKeys:Id`. إنشاء GUID وإدخاله كقيمة `TestKeys:ID` . على سبيل المثال، `DCE1CC21-FF9B-4424-8FF4-9914BD19A1BE`. يمكنك استخدام موقع مثل [منشئ GUID عبر الإنترنت](https://guidgenerator.com/) لإنشاء GUID عشوائيا.

تعرض هذه الصورة التنسيق الصحيح لإعدادات المستأجر والمفاتيح في **appsettings.json**. `LDAPPath` تم تكوينه للتخويل الدور.

![يعرض إعدادات المستأجر والمفتاح الصحيحة ل DKE في ملف appsettings.json.](../media/dke-appsettingsjson-tenantkeysettings.png)

### <a name="generate-test-keys"></a>إنشاء مفاتيح اختبار

بمجرد تحديد إعدادات التطبيق الخاص بك، تكون جاهزا لإنشاء مفاتيح اختبار عامة وخاصة.

لإنشاء المفاتيح:

1. من Windows قائمة البدء، قم بتشغيل موجه الأوامر OpenSSL.

1. قم بالتغيير إلى المجلد حيث تريد حفظ مفاتيح الاختبار. يتم تخزين الملفات التي تقوم بإنشائها بإكمال الخطوات الواردة في هذه المهمة في المجلد نفسه.

1. إنشاء مفتاح الاختبار الجديد.

   ```console
   openssl req -x509 -newkey rsa:2048 -keyout key.pem -out cert.pem -days 365
   ```

1. إنشاء المفتاح الخاص.

   إذا قمت بتثبيت الإصدار 3 من OpenSSL أو إصدار أحدث، فشغل الأمر التالي:
  
  ```console
  openssl rsa -in key.pem -out privkeynopass.pem -outform PEM -traditional
  ```
  
>  بخلاف ذلك، قم بتشغيل الأمر التالي:
>  ```console
>  openssl rsa -in key.pem -out privkeynopass.pem -outform PEM
>  ```

1. إنشاء المفتاح العام.

   ```console
   openssl rsa -in key.pem -pubout > pubkeyonly.pem
   ```

1. في محرر النص، افتح **pubkeyonly.pem**. انسخ كل المحتوى في ملف **pubkeyonly.pem** ، باستثناء السطرين الأول والأخير، في `PublicPem` قسم ملف **appsettings.json** .

1. في محرر النص، افتح **privkeynopass.pem**. انسخ كل المحتوى في ملف **privkeynopass.pem** ، باستثناء السطرين الأول والأخير، في `PrivatePem` قسم **ملف appsettings.json** .

1. إزالة كافة المسافات الفارغة والخطوط الجديدة في كل من المقاطع`PublicPem`.`PrivatePem`

    > [!IMPORTANT]
    > عند نسخ هذا المحتوى، لا تحذف أيا من بيانات PEM.

1. في Visual Studio Code، استعرض وصولا إلى ملف **Startup.cs**. يوجد هذا الملف في مستودع DoubleKeyEncryptionService الذي نسخته محليا ضمن DoubleKeyEncryptionService\src\customer-key-store\.

1. حدد موقع الأسطر التالية:

    ```csharp
        #if USE_TEST_KEYS
        #error !!!!!!!!!!!!!!!!!!!!!! Use of test keys is only supported for testing,
        DO NOT USE FOR PRODUCTION !!!!!!!!!!!!!!!!!!!!!!!!!!!!!
        services.AddSingleton<ippw.IKeyStore, ippw.TestKeyStore>();
        #endif
    ```

1. استبدل هذه الأسطر بالنص التالي:

    ```csharp
    services.AddSingleton<ippw.IKeyStore, ippw.TestKeyStore>();
    ```

    يجب أن تبدو النتائج النهائية مشابهة للآتي.

    ![ملف startup.cs للمعاينة العامة.](../media/dke-startupcs-usetestkeys.png)

أنت الآن جاهز [لبناء مشروع DKE الخاص بك](#build-the-project).

### <a name="build-the-project"></a>إنشاء المشروع

استخدم الإرشادات التالية لإنشاء مشروع DKE محليا:

1. في Visual Studio Code، في مستودع خدمة DKE، حدد **"View** \> **Command Palette"** ثم اكتب **الإنشاء** في المطالبة.

2. من القائمة، اختر **المهام: تشغيل مهمة الإنشاء**.

   إذا لم يتم العثور على مهام إنشاء، فحدد **"تكوين مهمة الإنشاء** " وأنشئ واحدة ل .NET core كما يلي.

   ![تكوين مهمة إنشاء مفقودة ل .NET.](../media/dke-configurebuildtask.png)

   1. اختر **إنشاء tasks.json من القالب**.

      ![إنشاء ملف tasks.json من قالب ل DKE.](../media/dke-createtasksjsonfromtemplate.png)

   2. من قائمة أنواع القوالب، حدد **.NET Core**.

      ![حدد القالب الصحيح ل DKE.](../media/dke-tasksjsontemplate.png)

   3. في قسم الإنشاء، حدد موقع المسار إلى ملف **customerkeystore.csproj** . إذا لم يكن موجودا هناك، أضف السطر التالي:

      ```json
      "${workspaceFolder}/src/customer-key-store/customerkeystore.csproj",
      ```

   4. تشغيل البنية مرة أخرى.

3. تحقق من عدم وجود أخطاء حمراء في نافذة الإخراج.

   إذا كانت هناك أخطاء حمراء، فتحقق من إخراج وحدة التحكم. تأكد من إكمال كافة الخطوات السابقة بشكل صحيح وأن إصدارات الإصدار الصحيحة موجودة.

4. حدد **تشغيل تصحيح** \> **أخطاء البدء** لتصحيح العملية. إذا تمت مطالبتك بتحديد بيئة، فحدد **.NET core**.

   عادة ما يتم تشغيل مصحح أخطاء .NET الأساسي إلى `https://localhost:5001`. لعرض مفتاح الاختبار الخاص بك، انتقل إلى `https://localhost:5001` شرطة مائلة للأمام (/) وإلحاقها واسم المفتاح الخاص بك. على سبيل المثال:

   ```https
   https://localhost:5001/TestKey1
   ```

   يجب عرض المفتاح بتنسيق JSON.

اكتمل الإعداد الآن. قبل نشر مخزن المفاتيح، في appsettings.json، لإعداد JwtAudience، تأكد من تطابق قيمة اسم المضيف تماما مع اسم مضيف App Service. ربما قمت بتغييره إلى localhost لاستكشاف أخطاء البنية وإصلاحها.

### <a name="deploy-the-dke-service-and-publish-the-key-store"></a>نشر خدمة DKE ونشر مخزن المفاتيح

بالنسبة إلى عمليات نشر الإنتاج، انشر الخدمة إما في سحابة تابعة لجهة خارجية أو [انشرها على نظام محلي](/aspnet/core/tutorials/publish-to-iis?preserve-view=true&tabs=netcore-cli&view=aspnetcore-3.1).

قد تفضل أساليب أخرى لنشر المفاتيح الخاصة بك. حدد الأسلوب الذي يعمل بشكل أفضل لمؤسستك.

بالنسبة إلى عمليات النشر التجريبية، يمكنك النشر في Azure والبدء على الفور.

#### <a name="to-create-an-azure-web-app-instance-to-host-your-dke-deployment"></a>لإنشاء مثيل Azure Web App لاستضافة توزيع DKE

لنشر مخزن المفاتيح، ستقوم بإنشاء مثيل Azure App Service لاستضافة توزيع DKE الخاص بك. بعد ذلك، ستقوم بنشر المفاتيح التي تم إنشاؤها إلى Azure.

1. في المستعرض، سجل الدخول إلى [مدخل Microsoft Azure](https://ms.portal.azure.com)، وانتقل إلى **App Services** > **Add**.

2. حدد اشتراكك ومجموعة الموارد وحدد تفاصيل المثيل.

   - أدخل اسم مضيف الكمبيوتر حيث تريد تثبيت خدمة DKE. تأكد من أنه نفس اسم الاسم المحدد لإعداد JwtAudience في ملف [**appsettings.json**](#tenant-and-key-settings) . القيمة التي توفرها للاسم هي أيضا WebAppInstanceName.

   - **للنشر،** حدد **التعليمات البرمجية**، **ولمكدس وقت التشغيل**، حدد **.NET Core 3.1**.

   على سبيل المثال:

   > [!div class="mx-imgBorder"]
   > ![إضافة App Service.](../media/dke-azure-add-app-service.png)

3. في أسفل الصفحة، حدد **Review + create**، ثم حدد **Add**.

4. قم بأحد الإجراءات التالية لنشر المفاتيح التي تم إنشاؤها:

   - [النشر عبر ZipDeployUI](#publish-via-zipdeployui)
   - [النشر عبر FTP](#publish-via-ftp)
   - [النشر عبر Visual Studio 2019 أو أحدث](/aspnet/core/tutorials/)

#### <a name="publish-via-zipdeployui"></a>النشر عبر ZipDeployUI

1. الانتقال إل `https://<WebAppInstanceName>.scm.azurewebsites.net/ZipDeployUI`

   على سبيل المثال: `https://dkeservice.scm.azurewebsites.net/ZipDeployUI`

2. في قاعدة التعليمات البرمجية لمخزن المفاتيح، انتقل إلى مجلد **customer-key-store\src\customer-key-store** ، وتحقق من أن هذا المجلد يحتوي على ملف **customerkeystore.csproj** .

3. تشغيل: **نشر dotnet**

   تعرض نافذة الإخراج الدليل الذي تم نشر النشر فيه.

   على سبيل المثال: `customer-key-store\src\customer-key-store\bin\Debug\netcoreapp3.1\publish\`

4. إرسال كافة الملفات في دليل النشر إلى ملف .zip. عند إنشاء ملف .zip، تأكد من أن كافة الملفات الموجودة في الدليل في المستوى الجذر لملف .zip.

5. اسحب ملف .zip الذي أنشأته وأفلته في موقع ZipDeployUI الذي فتحته أعلاه. على سبيل المثال: `https://dkeservice.scm.azurewebsites.net/ZipDeployUI`

يتم نشر DKE ويمكنك الاستعراض للوصول إلى مفاتيح الاختبار التي قمت بإنشائها. تابع [التحقق من صحة النشر](#validate-your-deployment) أدناه.

#### <a name="publish-via-ftp"></a>النشر عبر FTP

1. الاتصال إلى App Service التي أنشأتها [أعلاه](#deploy-the-dke-service-and-publish-the-key-store).

   في المستعرض، انتقل إلى: لوحة **معلومات** **FTP** > **للتوزيع** >  اليدوي **لمركز** > **نشر خدمة** >  التطبيقات **لمدخل** >  Microsoft Azure.

2. انسخ سلاسل الاتصال المعروضة إلى ملف محلي. ستستخدم هذه السلاسل للاتصال بخدمة تطبيق الويب وتحميل الملفات عبر FTP.

   على سبيل المثال:

   ![نسخ سلاسل الاتصال من لوحة معلومات FTP.](../media/dke-ftp-dashboard.png)

3. في قاعدة التعليمات البرمجية لتخزين المفتاح، انتقل إلى **دليل مخزن مفاتيح العملاء\src\customer-key-store**.

4. تحقق من أن هذا الدليل يحتوي على ملف **customerkeystore.csproj** .

5. تشغيل: **نشر dotnet**

   يحتوي الإخراج على الدليل الذي تم نشر النشر فيه.

   على سبيل المثال: `customer-key-store\src\customer-key-store\bin\Debug\netcoreapp3.1\publish\`

6. إرسال كافة الملفات في دليل النشر إلى ملف مضغوط. عند إنشاء ملف .zip، تأكد من أن كافة الملفات الموجودة في الدليل في المستوى الجذر لملف .zip.

7. من عميل FTP، استخدم معلومات الاتصال التي نسختها للاتصال بخدمة التطبيقات. Upload ملف .zip الذي أنشأته في الخطوة السابقة إلى الدليل الجذر لتطبيق الويب الخاص بك.

يتم نشر DKE ويمكنك الاستعراض للوصول إلى مفاتيح الاختبار التي قمت بإنشائها. بعد ذلك، [تحقق من صحة التوزيع.](#validate-your-deployment)

### <a name="validate-your-deployment"></a>التحقق من صحة النشر

بعد نشر DKE باستخدام إحدى الطرق الموضحة أعلاه، تحقق من صحة النشر وإعدادات مخزن المفاتيح.

تشغيل:

```powershell
src\customer-key-store\scripts\key_store_tester.ps1 dkeserviceurl/mykey
```

على سبيل المثال:

```powershell
key_store_tester.ps1 https://mydkeservice.com/mykey
```

تأكد من عدم ظهور أي أخطاء في الإخراج. عندما تصبح جاهزا، [قم بتسجيل مخزن المفاتيح.](#register-your-key-store)

اسم المفتاح حساس لحالة الأحرف. أدخل اسم المفتاح كما يظهر في ملف appsettings.json.

## <a name="register-your-key-store"></a>تسجيل مخزن المفاتيح

تمكنك الخطوات التالية من تسجيل خدمة DKE. تسجيل خدمة DKE هي الخطوة الأخيرة في نشر DKE قبل أن تتمكن من البدء في إنشاء التسميات.

لتسجيل خدمة DKE:

1. في المستعرض، افتح [مدخل Microsoft Azure](https://ms.portal.azure.com/)، وانتقل إلى **تسجيلات تطبيق** **هوية** \> **جميع الخدمات**\>.

2. حدد **تسجيلا جديدا**، وأدخل اسما ذا معنى.

3. حدد نوع حساب من الخيارات المعروضة.

   إذا كنت تستخدم Microsoft Azure مع مجال غير مخصص، مثل **onmicrosoft.com**، فحدد **الحسابات في دليل المؤسسة هذا فقط (Microsoft فقط - مستأجر واحد).**

   على سبيل المثال:

   > [!div class="mx-imgBorder"]
   > ![تسجيل تطبيق جديد.](../media/dke-app-registration.png)

4. في أسفل الصفحة، حدد **"تسجيل** " لإنشاء "تسجيل التطبيق" الجديد.

5. في تسجيل التطبيق الجديد، في الجزء الأيمن، ضمن **"إدارة**"، حدد **"المصادقة**".

6. حدد **إضافة نظام أساسي**.

7. في القائمة المنبثقة **"تكوين الأنظمة الأساسية** "، حدد **"ويب**".

8. ضمن **عناوين URL لإعادة التوجيه**، أدخل URI الخاص بخدمة تشفير المفتاح المزدوج. أدخل عنوان URL لخدمة التطبيقات، بما في ذلك اسم المضيف والمجال.

   على سبيل المثال: `https://mydkeservicetest.com`

   - يجب أن يتطابق URL الذي تقوم بإدخاله مع اسم المضيف حيث يتم نشر خدمة DKE.
   - يجب أن يكون المجال [مجالا تم التحقق منه](/azure/active-directory/develop/reference-breaking-changes#appid-uri-in-single-tenant-applications-will-require-use-of-default-scheme-or-verified-domains).
   - إذا كنت تختبر محليا باستخدام Visual Studio، فاستخدم `https://localhost:5001`.
   - في جميع الحالات، يجب أن يكون النظام **https**.

   تأكد من تطابق اسم المضيف تماما مع اسم مضيف App Service. ربما قمت بتغييره إلى `localhost` استكشاف أخطاء البنية وإصلاحها. في **appsettings.json**، هذه القيمة هي اسم المضيف الذي قمت بتعيينه ل `JwtAudience`.

9. ضمن **"منحة ضمنية**"، حدد خانة الاختيار **"رموز المعرف المميزة** ".

10. حدد **"حفظ"** لحفظ التغييرات.

11. في الجزء الأيمن، حدد **"عرض واجهة برمجة التطبيقات**"، إلى جانب معرف التطبيق URI، وأدخل عنوان URL لخدمة التطبيقات، بما في ذلك اسم المضيف والمجال، ثم حدد **"تعيين**".

12. لا يزال في صفحة **"عرض واجهة برمجة التطبيقات** "، في **النطاقات المعرفة بواسطة منطقة واجهة برمجة التطبيقات هذه** ، حدد **"إضافة نطاق**". في النطاق الجديد:

    1. تعريف اسم النطاق على أنه **user_impersonation**.

    2. حدد المسؤولين والمستخدمين الذين يمكنهم الموافقة.

    3. تعريف أي قيم متبقية مطلوبة.

    4. حدد **إضافة نطاق**.

    5. حدد **"حفظ** " في الأعلى لحفظ التغييرات.

13. لا يزال في صفحة **«كشف واجهة برمجة التطبيقات** »، في منطقة **تطبيقات العميل المعتمد** ، حدد **«Add a client application**».

    في تطبيق العميل الجديد:

    1. تعريف معرف العميل ك `d3590ed6-52b3-4102-aeff-aad2292ab01c`. هذه القيمة هي معرف العميل Microsoft Office، وتمكن Office من الحصول على رمز وصول مميز لمخزن المفاتيح.

    2. ضمن **النطاقات المعتمدة**، حدد نطاق **user_impersonation** .

    3. حدد **إضافة تطبيق**.

    4. حدد **"حفظ** " في الأعلى لحفظ التغييرات.

    5. كرر هذه الخطوات، ولكن هذه المرة، حدد معرف العميل ك `c00e9d32-3c8d-4a7d-832b-029040e7db99`. هذه القيمة هي معرف عميل التسمية الموحد ل Azure حماية البيانات.

تم الآن تسجيل خدمة DKE الخاصة بك. تابع [عن طريق إنشاء تسميات باستخدام DKE](#create-sensitivity-labels-using-dke).

## <a name="create-sensitivity-labels-using-dke"></a>إنشاء تسميات الحساسية باستخدام DKE

في مدخل التوافق في Microsoft Purview، قم بإنشاء وصف حساسية جديد وتطبيق التشفير كما تفعل بخلاف ذلك. حدد **"استخدام تشفير المفتاح المزدوج** " وأدخل عنوان URL لنقطة النهاية للمفتاح الخاص بك. تحتاج إلى تضمين اسم المفتاح الذي قمت بتوفيره داخل قسم "TestKeys" من ملف appsettings.json في عنوان URL.

على سبيل المثال: `https://testingdke1.azurewebsites.net/KEYNAME`

> [!div class="mx-imgBorder"]
> ![حدد "استخدام تشفير المفتاح المزدوج" في مدخل التوافق في Microsoft Purview.](../media/dke-use-dke.png)

ستبدأ تسميات DKE التي تضيفها في الظهور للمستخدمين في أحدث إصدارات Microsoft 365 Apps for enterprise.

> [!NOTE]
> قد يستغرق تحديث العملاء باستخدام التسميات الجديدة ما يصل إلى 24 ساعة.

### <a name="enable-dke-in-your-client"></a>تمكين DKE في عميلك

إذا كنت Office Insider، يتم تمكين DKE لك. بخلاف ذلك، قم بتمكين DKE للعميل عن طريق إضافة مفاتيح التسجيل التالية:

```console
   [HKEY_LOCAL_MACHINE\SOFTWARE\WOW6432Node\Microsoft\MSIPC\flighting]
   "DoubleKeyProtection"=dword:00000001

   [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSIPC\flighting]
   "DoubleKeyProtection"=dword:00000001
```

## <a name="migrate-protected-files-from-hyok-labels-to-dke-labels"></a>ترحيل الملفات المحمية من تسميات HYOK إلى تسميات DKE

إذا أردت، بمجرد الانتهاء من إعداد DKE، يمكنك ترحيل المحتوى الذي قمت بحمايته باستخدام تسميات HYOK إلى تسميات DKE. للرحل، ستستخدم الماسح الضوئي ل AIP. لبدء استخدام الماسح الضوئي، راجع [ما هو الماسح الضوئي الموحد للوصف حماية البيانات Azure؟](/azure/information-protection/deploy-aip-scanner).

إذا لم تقم بترحيل المحتوى، فسيظل المحتوى المحمي في HYOK غير متأثر.

## <a name="other-deployment-options"></a>خيارات النشر الأخرى

ندرك أنه بالنسبة إلى بعض العملاء في الصناعات المنظمة للغاية، قد لا يكون هذا التنفيذ المرجعي القياسي باستخدام المفاتيح المستندة إلى البرامج كافيا للوفاء بالتزامات الامتثال المحسنة واحتياجاتهم. لقد عقدنا شراكة مع موردي وحدة أمان الأجهزة (HSM) التابعين لجهات خارجية لدعم خيارات إدارة المفاتيح المحسنة في خدمة DKE، بما في ذلك:

- [تعهد](https://www.entrust.com/digital-security/hsm/services/packaged-services/double-key-encryption-integration#:~:text=Entrust%20Double%20Key%20Encryption%20for%20Microsoft%20AIP%2C%20offered,trust%20for%20the%20protection%20of%20sensitive%20cryptographic%20keys.)

- [طاليس](https://cpl.thalesgroup.com/cloud-security/encryption/double-key-encryption)

تواصل مباشرة مع هؤلاء الموردين للحصول على مزيد من المعلومات والإرشادات حول حلول DKE HSM داخل السوق.
