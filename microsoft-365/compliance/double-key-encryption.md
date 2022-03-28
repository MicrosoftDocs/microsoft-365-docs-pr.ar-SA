---
title: تشفير المفتاح المزدوج (DKE)
description: تمكنك DKE من حماية البيانات عالية الحساسية مع الحفاظ على التحكم الكامل بالمفتاح.
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
ms.openlocfilehash: b16733a1d42ca245f096038f567be6fbd0c3fb2a
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/08/2022
ms.locfileid: "63575247"
---
# <a name="double-key-encryption-for-microsoft-365"></a>تشفير المفتاح المزدوج Microsoft 365

> *ينطبق على: تشفير المفتاح المزدوج Microsoft 365 [Microsoft 365 والتوافق](https://www.microsoft.com/microsoft-365/business/compliance-management) وحماية [معلومات Azure](https://azure.microsoft.com/pricing/details/information-protection)*
>
> *إرشادات حول: [Azure Information Protection عميل التسمية الموحد Windows](/azure/information-protection/faqs#whats-the-difference-between-the-azure-information-protection-classic-and-unified-labeling-clients)*


> *وصف الخدمة ل: [Microsoft 365 التوافق](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance)*

يستخدم تشفير المفتاح المزدوج (DKE) مفتاحين معا للوصول إلى المحتوى المحمي. تخزن Microsoft مفتاحا واحدا في Microsoft Azure، وأنت تحمل المفتاح الآخر. يمكنك الاحتفاظ بالتحكم الكامل في أحد المفاتيح باستخدام خدمة تشفير المفتاح المزدوج. يمكنك تطبيق الحماية باستخدام عميل التسمية الموحد لحماية معلومات Azure على المحتوى عالي الحساسية.

يدعم التشفير المزدوج للمفتاح عمليات النشر في السحابة أو في الموقع. تساعد عمليات النشر هذه على ضمان أن تظل البيانات المشفرة معتمة أينما قمت بتخزين البيانات المحمية.

لمزيد من المعلومات حول مفاتيح المستأجر الجذر الافتراضية المستندة إلى السحابة، راجع تخطيط مفتاح مستأجر [Azure Information Protection وتطبيقه](/azure/information-protection/plan-implement-tenant-key).

## <a name="when-your-organization-should-adopt-dke"></a>متى يجب أن تعتمد مؤسستك DKE

التشفير المزدوج للمفتاح مخصص للبيانات الأكثر حساسية التي تخضع لمتطلبات الحماية الأكثر صرامة. DKE غير مخصص لجميع البيانات. بشكل عام، سوف تستخدم تشفير المفتاح المزدوج لحماية جزء صغير فقط من بياناتك الإجمالية. يجب أن تحرص على تحديد البيانات الصحيحة التي يجب تناولها باستخدام هذا الحل قبل النشر. في بعض الحالات، قد تحتاج إلى تضييق نطاقك واستخدام حلول أخرى لمعظم بياناتك، مثل حماية البيانات في Microsoft مفاتيح مدارة بواسطة Microsoft أو BYOK. هذه الحلول كافية للمستندات التي لا تخضع للحماية والمتطلبات التنظيمية المحسنة. كما تمكنك هذه الحلول من استخدام الخدمات الأكثر Office 365؛ الخدمات التي لا يمكنك استخدامها مع المحتوى المشفر ل DKE. على سبيل المثال:

- قواعد النقل بما في ذلك مكافحة البرامج الضارة والبريد العشوائي الذي يتطلب رؤية المرفق
- Microsoft Delve
- eDiscovery
- البحث عن المحتوى وفهرسته
- Office ويب بما في ذلك وظائف المشاركة في المشاركة في العمل

لن تتمكن أي تطبيقات أو خدمات خارجية غير متكاملة مع DKE عبر حماية البيانات في Microsoft SDK (MIP) من تنفيذ إجراءات على البيانات المشفرة.

يدعم حماية البيانات في Microsoft SDK 1.7+ تشفير المفتاح المزدوج. يمكن للتطبيقات التي تتكامل مع SDK الحصول على سبب لهذه البيانات باستخدام أذونات وتكاملات كافية في مكانها.

استخدم قدرات حماية المعلومات من Microsoft (التصنيف والتسميات) لحماية معظم بياناتك الحساسة ولا تستخدم DKE إلا للبيانات المهمة. التشفير المزدوج ذو الصلة بالبيانات الحساسة في المجالات الخاضعة للتنظيم بشكل كبير مثل الخدمات المالية والرعاية الصحية.

إذا كان لدى مؤسستك أي من المتطلبات التالية، يمكنك استخدام DKE للمساعدة في تأمين المحتوى الخاص بك:

- أنت تريد التأكد من أنه *يمكنك* فقط فك تشفير المحتوى المحمي، تحت كل الظروف.
- لا تريد أن يكون لدى Microsoft حق الوصول إلى البيانات المحمية بمفردها.
- لديك متطلبات تنظيمية لمسك المفاتيح داخل حد جغرافي. يتم الاحتفاظ بكل المفاتيح التي تحتفظ بها لتشفير البيانات وفك تشفيرها في مركز البيانات.

## <a name="system-and-licensing-requirements-for-dke"></a>متطلبات النظام والترخيص ل DKE

**يأتي التشفير المزدوج للمفتاح Microsoft 365** مع Microsoft 365 E5. إذا لم يكن لديك ترخيص Microsoft 365 E5، يمكنك التسجيل للحصول على [إصدار تجريبي](https://aka.ms/M365E5ComplianceTrial). لمزيد من المعلومات حول هذه التراخيص، راجع Microsoft 365 [إرشادات الترخيص لتوافق & الأمان](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).

**Azure Information Protection**. تعمل DKE مع تسميات الحساسية وتتطلب حماية معلومات Azure.

تتوفر تسميات حساسية DKE للمستخدمين النهائيين من خلال زر الحساسية في عميل التسمية الموحد ل AIP في Office سطح المكتب. قم بتثبيت هذه المتطلبات الأساسية على كل كمبيوتر عميل حيث تريد حماية المستندات المحمية واستهلاكها.

**Microsoft Office لتطبيقات** المؤسسة الإصدار 2009 أو الإصدارات الأحدث (إصدارات سطح المكتب من Word PowerPoint Excel) على Windows.

**Azure Information Protection Unified Labeling Client versions** 2.7.93.0 أو إصدار أحدث. قم بتنزيل عميل التسمية الموحد وتثبيته من [مركز التنزيل في Microsoft](https://www.microsoft.com/download/details.aspx?id=53018).

## <a name="supported-environments-for-storing-and-viewing-dke-protected-content"></a>البيئات المعتمدة لتخزين المحتوى المحمي من DKE وعرضه

**التطبيقات المعتمدة**. [Microsoft 365 Apps for enterprise](https://www.microsoft.com/microsoft-365/business/microsoft-365-apps-for-enterprise-product) على Windows، بما في ذلك Word Excel PowerPoint.

**دعم المحتوى عبر الإنترنت**. يمكنك تخزين المستندات والملفات المحمية باستخدام تشفير المفتاح المزدوج عبر الإنترنت في كل من microsoft SharePoint OneDrive for Business. يجب تسمية المستندات والملفات وحمايتها باستخدام DKE بواسطة التطبيقات المعتمدة قبل التحميل إلى هذه المواقع. يمكنك مشاركة محتوى مشفر عبر البريد الإلكتروني، ولكن لا يمكنك عرض المستندات والملفات المشفرة عبر الإنترنت. بدلا من ذلك، يجب عرض المحتوى المحمي باستخدام تطبيقات سطح المكتب المعتمدة والعملاء على الكمبيوتر المحلي.

## <a name="overview-of-deploying-dke"></a>نظرة عامة حول نشر DKE

ستتبع هذه الخطوات العامة لإعداد DKE. بعد إكمال هذه الخطوات، يمكن للمستخدمين حماية بياناتك عالية الحساسية باستخدام تشفير المفتاح المزدوج.

1. نشر خدمة DKE كما هو موضح في هذه المقالة.

2. إنشاء تسمية باستخدام تشفير المفتاح المزدوج. في مركز التوافق في Microsoft 365، انتقل إلى **حماية** المعلومات وأنشئ تسمية جديدة باستخدام تشفير المفتاح المزدوج. راجع [تقييد الوصول إلى المحتوى باستخدام تسميات الحساسية لتطبيق التشفير](./encryption-sensitivity-labels.md).

3. استخدم تسميات تشفير المفاتيح المزدوجة. يمكنك حماية البيانات عن طريق تحديد التسمية "مشفرة بمفتاح مزدوج" من شريط الحساسية في Microsoft Office.

هناك عدة طرق يمكنك من خلالها إكمال بعض الخطوات لنشر تشفير المفتاح المزدوج. توفر هذه المقالة إرشادات مفصلة بحيث يمكن للمسؤولين الأقل خبرة نشر الخدمة بنجاح. إذا كنت مرتاحا للقيام بذلك، يمكنك اختيار استخدام الأساليب الخاصة بك.

## <a name="deploy-dke"></a>نشر DKE

تستخدم هذه المقالة وفيديو النشر Azure كوجهة نشر لخدمة DKE. إذا كنت تقوم بالنشر إلى موقع آخر، ستحتاج إلى توفير القيم الخاصة بك.

شاهد فيديو [نشر تشفير مزدوج المفاتيح](https://youtu.be/vDWfHN_kygg) لمشاهدة نظرة عامة مفصلة خطوة بخطوة حول المفاهيم في هذه المقالة. يستغرق إكمال الفيديو حوالي 18 دقيقة.

ستتبع هذه الخطوات العامة لإعداد التشفير المزدوج للمفتاح لمنظمتك.

1. [تثبيت المتطلبات الأساسية للبرامج لخدمة DKE](#install-software-prerequisites-for-the-dke-service)
1. [نسخ مستودع التشفير المزدوج GitHub المفاتيح المزدوجة](#clone-the-dke-github-repository)
1. [تعديل إعدادات التطبيق](#modify-application-settings)
1. [إنشاء مفاتيح اختبار](#generate-test-keys)
1. [إنشاء المشروع](#build-the-project)
1. [نشر خدمة DKE ونشر مخزن المفاتيح](#deploy-the-dke-service-and-publish-the-key-store)
1. [التحقق من صحة النشر](#validate-your-deployment)
1. [تسجيل متجر المفاتيح](#register-your-key-store)
1. [إنشاء تسميات الحساسية باستخدام DKE](#create-sensitivity-labels-using-dke)
1. [تمكين DKE في العميل](#enable-dke-in-your-client)
1. [ترحيل الملفات المحمية من تسميات HYOK إلى تسميات DKE](#migrate-protected-files-from-hyok-labels-to-dke-labels)

عندما تنتهي، يمكنك تشفير المستندات والملفات باستخدام DKE. للحصول على معلومات، راجع [تطبيق تسميات الحساسية على الملفات والبريد الإلكتروني في](https://support.microsoft.com/office/2f96e7cd-d5a4-403b-8bd7-4cc636bae0f9) Office.

### <a name="install-software-prerequisites-for-the-dke-service"></a>تثبيت المتطلبات الأساسية للبرامج لخدمة DKE

ثبت هذه المتطلبات الأساسية على الكمبيوتر حيث تريد تثبيت خدمة DKE.

**.NET Core 3.1 SDK**. قم بتنزيل SDK وتثبيته من [تنزيل .NET Core 3.1](https://dotnet.microsoft.com/download/dotnet-core/3.1).

**Visual Studio التعليمات البرمجية**. قم Visual Studio التعليمات البرمجية من [https://code.visualstudio.com/](https://code.visualstudio.com). بمجرد تثبيته، Visual Studio التعليمات البرمجية وحدد **عرض** \> **الملحقات**. ثبت هذه الملحقات.

- C# Visual Studio التعليمات البرمجية

- NuGet مدير الحِزَم

**موارد Git**. قم بتنزيل أحد ما يلي وتثبيته.

- [Git](https://git-scm.com/downloads)

- [GitHub سطح المكتب](https://desktop.github.com/)

- [GitHub Enterprise](https://github.com/enterprise)

**OpenSSL** يجب أن يكون [OpenSSL مثبتا](https://slproweb.com/products/Win32OpenSSL.html) لديك [لإنشاء مفاتيح اختبار](#generate-test-keys) بعد نشر DKE. تأكد من أنك تقوم باستدعاءه بشكل صحيح من مسار متغيرات البيئة. على سبيل المثال، راجع "إضافة دليل التثبيت إلى PATH" للحصول [https://www.osradar.com/install-openssl-windows/](https://www.osradar.com/install-openssl-windows/) على التفاصيل.

### <a name="clone-the-dke-github-repository"></a>نسخ مستودع DKE GitHub

توفر Microsoft ملفات مصدر DKE في مستودع GitHub البيانات. يمكنك نسخ المستودع لإنشاء المشروع محليا لاستخدام مؤسستك. يقع مستودع GitHub DKE في [https://github.com/Azure-Samples/DoubleKeyEncryptionService](https://github.com/Azure-Samples/DoubleKeyEncryptionService).

الإرشادات التالية مخصصة لمستخدمي التعليمات البرمجية غير Visual Studio من الخبرة:

1. في المستعرض، انتقل إلى: [https://github.com/Azure-Samples/DoubleKeyEncryptionService](https://github.com/Azure-Samples/DoubleKeyEncryptionService).

2. في الجانب الأيسر من الشاشة، حدد **التعليمات البرمجية**. قد يظهر إصدار واجهة المستخدم زر "نسخ" **أو "** تنزيل". بعد ذلك، في المنسدلة التي تظهر، حدد أيقونة النسخ لنسخ عنوان URL إلى الحافظة.

    على سبيل المثال:

   > [!div class="mx-imgBorder"]
   > ![استنسخ مستودع خدمة تشفير المفاتيح المزدوجة من GitHub.](../media/dke-clone.png)

3. في Visual Studio البرمجية، حدد **عرض** \> **لوح الأوامر** وحدد **Git: استنساخ**. للبدء في الانتقال إلى الخيار في `git: clone` القائمة، ابدأ بالكتابة لتصفية الإدخالات ثم حددها من القائمة المنسدل. على سبيل المثال:

   > [!div class="mx-imgBorder"]
   > ![Visual Studio رمز GIT:استنساخ.](../media/dke-vscode-clone.png)

4. في مربع النص، اللصق URL الذي نسخته من Git وحدد **نسخ من GitHub**.

5. في **مربع الحوار تحديد مجلد** الذي يظهر، استعرض بحثا عن موقع لتخزين المستودع وحدده. في المطالبة، حدد **فتح**.

    يتم فتح المستودع في Visual Studio، ويعرض فرع Git الحالي في الجزء السفلي الأيسر. على سبيل المثال، يجب أن يكون الفرع **هو الرئيسي**. على سبيل المثال:

   ![لقطة شاشة لإعادة تشغيل DKE في Visual Studio يعرض الفرع الرئيسي.](../media/dke-vscode-main-branch.jpg)

6. إذا لم تكن في الفرع الرئيسي، ستحتاج إلى تحديده. في Visual Studio، حدد الفرع واختر **الرئيسي** من قائمة الفروع التي يتم عرضها.

   > [!IMPORTANT]
   > يضمن تحديد الفرع الرئيسي أن لديك الملفات الصحيحة لإنشاء المشروع. إذا لم تختار الفرع الصحيح، سيفشل نشرك.

لديك الآن مستودع مصدر DKE تم إعداده محليا. بعد [ذلك، قم بتعديل إعدادات التطبيق](#modify-application-settings) لمنظمتك.

### <a name="modify-application-settings"></a>تعديل إعدادات التطبيق

لنشر خدمة DKE، يجب تعديل الأنواع التالية من إعدادات التطبيق:

- [إعدادات الوصول الأساسية](#key-access-settings)
- [إعدادات المستأجر والمفتاح](#tenant-and-key-settings)

يمكنك تعديل إعدادات التطبيق في ملف appsettings.json. يقع هذا الملف في DoubleKeyEncryptionService repo الذي نسخته محليا ضمن DoubleKeyEncryptionService\src\customer-key-store. على سبيل المثال، Visual Studio التعليمات البرمجية، يمكنك الاستعراض إلى الملف كما هو موضح في الصورة التالية.

![تحديد موقع ملف appsettings.json ل DKE.](../media/dke-appsettingsjson.png)

#### <a name="key-access-settings"></a>إعدادات الوصول الأساسية

اختر ما إذا كنت تريد استخدام البريد الإلكتروني أو تخويل الدور. يدعم DKE أسلوبا واحدا فقط من أساليب المصادقة هذه في كل مرة.

- **تخويل البريد الإلكتروني**. السماح لمنظمتك بتفويض الوصول إلى المفاتيح استنادا إلى عناوين البريد الإلكتروني فقط.

- **تخويل الدور**. السماح لمنظمتك بتفويض الوصول إلى المفاتيح استنادا إلى مجموعات Active Directory، ويتطلب أن تقوم خدمة الويب باستعلام LDAP.

##### <a name="to-set-key-access-settings-for-dke-using-email-authorization"></a>لتعيين إعدادات الوصول الأساسية ل DKE باستخدام تخويل البريد الإلكتروني

1. افتح **ملف appsettings.json** وحدد موقع `AuthorizedEmailAddress` الإعداد.

2. أضف عنوان البريد الإلكتروني أو العناوين التي تريد تخويلها. افصل عناوين البريد الإلكتروني المتعددة باستخدام علامات اقتباس مزدوجة ونهاية. على سبيل المثال:

   ```json
   "AuthorizedEmailAddress": ["email1@company.com", "email2@company.com ", "email3@company.com"]
   ```

3. حدد موقع `LDAPPath` الإعداد وأزل النص بين `If you use role authorization (AuthorizedRoles) then this is the LDAP path.` علامات الاقتباس المزدوجة. اترك علامات الاقتباس المزدوجة في مكانها. عند الانتهاء، يجب أن يبدو الإعداد كما هو.

   ```json
   "LDAPPath": ""
   ```

4. حدد موقع `AuthorizedRoles` الإعداد واحذف السطر بأكمله.

تعرض هذه الصورة **ملف appsettings.json** الذي تم تنسيقه بشكل صحيح لتخويل البريد الإلكتروني.

   ![يعرض ملف appsettings.json أسلوب تخويل البريد الإلكتروني.](../media/dke-email-accesssetting.png)

##### <a name="to-set-key-access-settings-for-dke-using-role-authorization"></a>لتعيين إعدادات الوصول الأساسية ل DKE باستخدام تخويل الدور

1. افتح **ملف appsettings.json** وحدد موقع `AuthorizedRoles` الإعداد.

2. أضف أسماء مجموعة Active Directory التي تريد تخويلها. افصل أسماء مجموعات متعددة باستخدام علامات اقتباس مزدوجة ونهاية. على سبيل المثال:

   ```json
   "AuthorizedRoles": ["group1", "group2", "group3"]
   ```

3. حدد موقع `LDAPPath` الإعداد وأضف مجال Active Directory. على سبيل المثال:

   ```json
   "LDAPPath": "contoso.com"
   ```

4. حدد موقع `AuthorizedEmailAddress` الإعداد واحذف السطر بأكمله.

تعرض هذه الصورة **ملف appsettings.json** الذي تم تنسيقه بشكل صحيح لتخويل الدور.

   ![يعرض ملف appsettings.json أسلوب تخويل الدور.](../media/dke-role-accesssetting.png)

#### <a name="tenant-and-key-settings"></a>إعدادات المستأجر والمفتاح

يقع مستأجر DKE وإعدادات المفاتيح في **ملف appsettings.json** .

##### <a name="to-configure-tenant-and-key-settings-for-dke"></a>لتكوين إعدادات المستأجر والمفتاح ل DKE

1. افتح **ملف appsettings.json** .

2. حدد موقع `ValidIssuers` الإعداد واستبدله `<tenantid>` بمحدد المستأجر. يمكنك تحديد موقع "هوية المستأجر" عن طريق الذهاب إلى مدخل Azure وعرض [خصائص المستأجر](https://aad.portal.azure.com/#blade/Microsoft_AAD_IAM/ActiveDirectoryMenuBlade/Properties). على سبيل المثال:

   ```json
   "ValidIssuers": [
     "https://sts.windows.net/9c99431e-b513-44be-a7d9-e7b500002d4b/"
   ]
   ```

> [!NOTE]
> إذا كنت تريد تمكين الوصول الخارجي B2B إلى متجر المفاتيح، ستحتاج أيضا إلى تضمين هؤلاء المستأجرين الخارجيين كجزء من قائمة جهات إصدار صالحة.

`JwtAudience`حدد موقع . استبدل `<yourhostname>` باسم المضيف للجهاز حيث سيتم تشغيل خدمة DKE. على سبيل المثال:

  > [!IMPORTANT]
  > يجب أن تتطابق قيمة ل `JwtAudience` مع اسم *مضيفك تماما*. يمكنك استخدام **localhost:5001** أثناء تصحيح الأخطاء. ومع ذلك، عندما تنتهي من تصحيح الأخطاء، تأكد من تحديث هذه القيمة إلى اسم مضيف الخادم.

- `TestKeys:Name`. أدخل اسما للمفتاح. على سبيل المثال: `TestKey1`
- `TestKeys:Id`. قم بإنشاء GUID وأدخله كقيمة `TestKeys:ID` . على سبيل المثال، `DCE1CC21-FF9B-4424-8FF4-9914BD19A1BE`. يمكنك استخدام موقع مثل ["منشئ GUID عبر الإنترنت"](https://guidgenerator.com/) لإنشاء GUID عشوائيا.

تعرض هذه الصورة التنسيق الصحيح لإعدادات المستأجر والمفاتيح في **appsettings.json**. `LDAPPath` تم تكوينه لتخويل الدور.

![إظهار إعدادات المستأجر والمفتاح الصحيحة ل DKE في ملف appsettings.json.](../media/dke-appsettingsjson-tenantkeysettings.png)

### <a name="generate-test-keys"></a>إنشاء مفاتيح اختبار

بعد تحديد إعدادات التطبيق، تكون جاهزا لإنشاء مفاتيح اختبار عامة وخاصة.

لإنشاء المفاتيح:

1. من Windows قائمة البدء، تشغيل موجه الأوامر OpenSSL.

1. تغيير إلى المجلد حيث تريد حفظ مفاتيح الاختبار. يتم تخزين الملفات التي تقوم بإنشاتها من خلال إكمال الخطوات في هذه المهمة في المجلد نفسه.

1. إنشاء مفتاح الاختبار الجديد.

   ```console
   openssl req -x509 -newkey rsa:2048 -keyout key.pem -out cert.pem -days 365
   ```

1. إنشاء المفتاح الخاص.

   إذا قمت بتثبيت إصدار OpenSSL 3 أو إصدار أحدث، فتابع تشغيل الأمر التالي:
  
  ```console
  openssl rsa -in key.pem -out privkeynopass.pem -outform PEM -traditional
  ```
  
>  بخلاف ذلك، تشغيل الأمر التالي:
>  ```console
>  openssl rsa -in key.pem -out privkeynopass.pem -outform PEM
>  ```

1. إنشاء المفتاح العمومي.

   ```console
   openssl rsa -in key.pem -pubout > pubkeyonly.pem
   ```

1. في محرر نص، افتح **pubkeyonly.pem**. انسخ كل المحتوى في **ملف pubkeyonly.pem**`PublicPem`، باستثناء الأسطر الأولى والأخيرة، إلى مقطع **ملف appsettings.json**.

1. في محرر نص، افتح **privkeynopass.pem**. انسخ كل المحتوى في ملف **privkeynopass.pem**`PrivatePem`، باستثناء الأسطر الأولى والأخيرة، إلى مقطع **ملف appsettings.json**.

1. قم بإزالة كل المسافات الفارغة والخطوط الجديدة في المقطعين `PublicPem` و `PrivatePem` .

    > [!IMPORTANT]
    > عند نسخ هذا المحتوى، لا تحذف أي بيانات PEM.

1. في Visual Studio، استعرض إلى ملف **Startup.cs**. يقع هذا الملف في إعادة استنساخ DoubleKeyEncryptionService الذي نسخته محليا ضمن DoubleKeyEncryptionService\src\customer-key-store\.

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

    يجب أن تبدو نتائج النهاية مماثلة للنتائج التالية.

    ![startup.cs file للمعاينة العامة.](../media/dke-startupcs-usetestkeys.png)

أنت الآن جاهز لبناء [مشروع DKE](#build-the-project).

### <a name="build-the-project"></a>إنشاء المشروع

استخدم الإرشادات التالية لإنشاء مشروع DKE محليا:

1. في Visual Studio التعليمات البرمجية، في مستودع خدمة DKE، حدد **عرض** \> لوح الأوامر ثم اكتب **إنشاء** عند المطالبة.

2. من القائمة، اختر **المهام: تشغيل مهمة إنشاء**.

   إذا لم يتم العثور على مهام إنشاء، فحدد **تكوين مهمة إنشاء** وإنشاء واحدة ل .NET core كما يلي.

   ![تكوين مهمة إنشاء مفقودة ل .NET.](../media/dke-configurebuildtask.png)

   1. اختر **إنشاء مهام.json من قالب**.

      ![إنشاء ملف tasks.json من قالب ل DKE.](../media/dke-createtasksjsonfromtemplate.png)

   2. من قائمة أنواع القوالب، حدد **.NET Core**.

      ![حدد القالب الصحيح ل DKE.](../media/dke-tasksjsontemplate.png)

   3. في مقطع البناء، حدد موقع المسار إلى **ملف customerkeystore.csproj** . إذا لم يكن هناك، أضف السطر التالي:

      ```json
      "${workspaceFolder}/src/customer-key-store/customerkeystore.csproj",
      ```

   4. قم بتشغيل البنية مرة أخرى.

3. تحقق من عدم وجود أخطاء حمراء في نافذة الإخراج.

   إذا كانت هناك أخطاء حمراء، فتحقق من إخراج وحدة التحكم. تأكد من أنك أكملت كل الخطوات السابقة بشكل صحيح وأن إصدارات الإصدارات الصحيحة موجودة.

4. حدد **تشغيل** \> **بدء تصحيح الأخطاء** لتصحيح الأخطاء في العملية. إذا تم مطالبتك بتحديد بيئة، فحدد **.NET core**.

   يتم تشغيل مصحح الأخطاء الأساسي .NET عادة إلى `https://localhost:5001`. لعرض مفتاح الاختبار، انتقل `https://localhost:5001` إلى الشرطة المائلة للأمام (/) وأ إلحاقها باسم المفتاح. على سبيل المثال:

   ```https
   https://localhost:5001/TestKey1
   ```

   يجب أن يتم عرض المفتاح بتنسيق JSON.

اكتمل الإعداد الآن. قبل نشر مفتاح المفاتيح، في appsettings.json، لإعداد JwtAudience، تأكد من تطابق قيمة اسم المضيف تماما مع اسم مضيف خدمة التطبيق. ربما قمت بتغييره إلى localhost لاستعلام البنية وإصلاحها.

### <a name="deploy-the-dke-service-and-publish-the-key-store"></a>نشر خدمة DKE ونشر مخزن المفاتيح

بالنسبة إلى عمليات نشر الإنتاج، انشر الخدمة إما في سحابة جهة خارجية أو [انشرها إلى نظام المحلي](/aspnet/core/tutorials/publish-to-iis?preserve-view=true&tabs=netcore-cli&view=aspnetcore-3.1).

قد تفضل استخدام أساليب أخرى لنشر المفاتيح. حدد الأسلوب الذي يعمل بشكل أفضل لمنظمتك.

بالنسبة إلى عمليات النشر التجريبية، يمكنك النشر في Azure والبدء على الفور.

#### <a name="to-create-an-azure-web-app-instance-to-host-your-dke-deployment"></a>لإنشاء مثيل Azure Web App لاستضافة نشر DKE

لنشر مخزن المفاتيح، ستنشئ مثيل خدمة تطبيق Azure لاستضافة نشر DKE. بعد ذلك، ستنشر المفاتيح التي تم إنشاؤها إلى Azure.

1. في المستعرض، سجل الدخول إلى [مدخل Microsoft Azure](https://ms.portal.azure.com)، واذهب إلى **App** **ServicesAdd** > .

2. حدد اشتراكك ومجموعتك من الموارد وحدد تفاصيل المثيل.

   - أدخل اسم المضيف للكمبيوتر حيث تريد تثبيت خدمة DKE. تأكد من أنه الاسم نفسه الذي تم تعريفه لإعداد JwtAudience في [**ملف appsettings.json**](#tenant-and-key-settings) . القيمة التي تقوم بتوفيرها للاسم هي أيضا WebAppInstanceName.

   - بالنسبة **للنشر**، حدد **التعليمات** البرمجية، وبالنسبة إلى **مكدس وقت** التشغيل، حدد **.NET Core 3.1**.

   على سبيل المثال:

   > [!div class="mx-imgBorder"]
   > ![إضافة خدمة التطبيق.](../media/dke-azure-add-app-service.png)

3. في أسفل الصفحة، حدد **مراجعة + إنشاء**، ثم حدد **إضافة**.

4. يمكنك القيام بوا أحد الخطوات التالية لنشر المفاتيح التي تم إنشاؤها:

   - [النشر عبر ZipDeployUI](#publish-via-zipdeployui)
   - [النشر عبر FTP](#publish-via-ftp)
   - [النشر عبر Visual Studio 2019 أو أي وقت لاحق](/aspnet/core/tutorials/)

#### <a name="publish-via-zipdeployui"></a>النشر عبر ZipDeployUI

1. انتقل إلى `https://<WebAppInstanceName>.scm.azurewebsites.net/ZipDeployUI`.

   على سبيل المثال: `https://dkeservice.scm.azurewebsites.net/ZipDeployUI`

2. في codebase لمتجر المفاتيح، انتقل إلى **مجلد customer-key-store\src\customer-key-store** ، وتحقق من أن هذا المجلد يحتوي على **ملف customerkeystore.csproj** .

3. تشغيل: **نشر dotnet**

   تعرض نافذة الإخراج الدليل الذي تم نشر النشر فيه.

   على سبيل المثال: `customer-key-store\src\customer-key-store\bin\Debug\netcoreapp3.1\publish\`

4. أرسل كل الملفات الموجودة في دليل النشر إلى ملف .zip. عند إنشاء .zip، تأكد من أن كل الملفات الموجودة في الدليل في المستوى الجذر لملف .zip.

5. اسحب الملف .zip الذي أنشأته إلى موقع ZipDeployUI الذي فتحته أعلاه. على سبيل المثال: `https://dkeservice.scm.azurewebsites.net/ZipDeployUI`

يتم نشر DKE، كما يمكنك الاستعراض بحثا عن مفاتيح الاختبار التي أنشأتها. تابع التحقق [من صحة النشر](#validate-your-deployment) أدناه.

#### <a name="publish-via-ftp"></a>النشر عبر FTP

1. الاتصال إلى خدمة التطبيقات التي أنشأتها [أعلاه](#deploy-the-dke-service-and-publish-the-key-store).

   في المستعرض، انتقل إلى: **Azure portalApp** >  **ServiceDeployment** >  **CenterManual** >  **DeploymentFTPDashboard** >  > .

2. انسخ سلاسل الاتصال المعروضة إلى ملف محلي. سوف تستخدم هذه السلاسل للاتصال ب Web App Service وتحميل الملفات عبر FTP.

   على سبيل المثال:

   ![نسخ سلاسل الاتصال من لوحة معلومات FTP.](../media/dke-ftp-dashboard.png)

3. في codebase للتخزين الرئيسي، انتقل إلى **دليل customer-key-store\src\customer-key-store**.

4. تحقق من أن هذا الدليل يحتوي على **ملف customerkeystore.csproj** .

5. تشغيل: **نشر dotnet**

   يحتوي الإخراج على الدليل الذي تم نشر النشر فيه.

   على سبيل المثال: `customer-key-store\src\customer-key-store\bin\Debug\netcoreapp3.1\publish\`

6. أرسل كل الملفات الموجودة في دليل النشر إلى ملف zip. عند إنشاء .zip، تأكد من أن كل الملفات الموجودة في الدليل في المستوى الجذر لملف .zip.

7. من عميل FTP، استخدم معلومات الاتصال التي نسختها للاتصال ب خدمة التطبيق. Upload الملف .zip الذي أنشأته في الخطوة السابقة إلى الدليل الجذر ل Web App.

يتم نشر DKE، كما يمكنك الاستعراض بحثا عن مفاتيح الاختبار التي أنشأتها. بعد ذلك [، تحقق من صحة النشر](#validate-your-deployment).

### <a name="validate-your-deployment"></a>التحقق من صحة النشر

بعد نشر DKE باستخدام أحد الأساليب الموضحة أعلاه، تحقق من صحة النشر وإعدادات المتجر الرئيسي.

تشغيل:

```powershell
src\customer-key-store\scripts\key_store_tester.ps1 dkeserviceurl/mykey
```

على سبيل المثال:

```powershell
key_store_tester.ps1 https://mydkeservice.com/mykey
```

تأكد من عدم ظهور أي أخطاء في الإخراج. عندما تكون جاهزا، [سجل متجر المفاتيح](#register-your-key-store).

اسم المفتاح يتحسس حالة التحسس. أدخل اسم المفتاح كما يظهر في ملف appsettings.json.

## <a name="register-your-key-store"></a>تسجيل متجر المفاتيح

تمكنك الخطوات التالية من تسجيل خدمة DKE. تسجيل خدمة DKE هي الخطوة الأخيرة في نشر DKE قبل أن تتمكن من بدء إنشاء التسميات.

لتسجيل خدمة DKE:

1. في المستعرض، افتح مدخل [Microsoft Azure](https://ms.portal.azure.com/)، واذهب إلى **جميع تسجيلات** \> تطبيق **هوية** \> **الخدمات**.

2. حدد **تسجيل جديد**، وأدخل اسما ذا معنى.

3. حدد نوع حساب من الخيارات المعروضة.

   إذا كنت تستخدم Microsoft Azure مع مجال غير مخصص، مثل **onmicrosoft.com**، فحدد الحسابات في دليل المؤسسة هذا فقط **(Microsoft فقط - مستأجر واحد).**

   على سبيل المثال:

   > [!div class="mx-imgBorder"]
   > ![تسجيل تطبيق جديد.](../media/dke-app-registration.png)

4. في أسفل الصفحة، حدد **تسجيل** لإنشاء تسجيل التطبيق الجديد.

5. في تسجيل التطبيق الجديد، في الجزء الأيسر، ضمن **إدارة**، حدد **المصادقة**.

6. حدد **إضافة نظام أساسي**.

7. في النافذة **المنبثقة تكوين الأنظمة الأساسية** ، حدد **ويب**.

8. ضمن **إعادة توجيه URI،** أدخل URI لخدمة التشفير المزدوج. أدخل عنوان URL لخدمة التطبيق، بما في ذلك اسم المضيف والمجال.

   على سبيل المثال: `https://mydkeservicetest.com`

   - يجب أن يكون عنوان URL الذي تدخله متطابقا مع اسم المضيف حيث يتم نشر خدمة DKE.
   - يجب أن يكون المجال [مجالا متحققا منه](/azure/active-directory/develop/reference-breaking-changes#appid-uri-in-single-tenant-applications-will-require-use-of-default-scheme-or-verified-domains).
   - إذا كنت تقوم باختبارها محليا باستخدام Visual Studio، فاستخدم `https://localhost:5001`.
   - في جميع الحالات، يجب أن يكون النظام **https**.

   تأكد من أن اسم المضيف يتطابق تماما مع اسم مضيف خدمة التطبيق. ربما قمت بتغييره إلى `localhost` استكشاف الأخطاء وإصلاحها في البنية. في **appsettings.json،** هذه القيمة هي اسم المضيف الذي قمت بتعيينه ل `JwtAudience`.

9. ضمن **المنحة الضمنية**، حدد خانة **الاختيار رموز الم** ID المميزة.

10. حدد **حفظ** لحفظ التغييرات.

11. في الجزء الأيسر، حدد عرض **API**، بجانب URI لم ID التطبيق، أدخل عنوان URL لخدمة التطبيق، بما في ذلك اسم المضيف والمجال، ثم حدد **تعيين**.

12. في الصفحة **عرض API في** المنطقة النطاقات المعرفة بواسطة منطقة **API** هذه، حدد **إضافة نطاق**. في النطاق الجديد:

    1. تعريف اسم **النطاق user_impersonation.**

    2. حدد المسؤولين والمستخدمين الذين يمكنهم الموافقة.

    3. تعريف أي قيم متبقة مطلوبة.

    4. حدد **إضافة نطاق**.

    5. حدد **حفظ** في الأعلى لحفظ التغييرات.

13. في الصفحة **عرض API في** منطقة تطبيقات العميل المعتمد،  حدد **إضافة تطبيق عميل**.

    في تطبيق العميل الجديد:

    1. تعريف "المعرف العميل" ك `d3590ed6-52b3-4102-aeff-aad2292ab01c`. هذه القيمة هي Microsoft Office العميل، وتمكن Office الحصول على رمز وصول مميز لمتجر المفاتيح.

    2. ضمن **النطاقات المعتمدة**، **حدد** user_impersonation نطاق العمل.

    3. حدد **إضافة تطبيق**.

    4. حدد **حفظ** في الأعلى لحفظ التغييرات.

    5. كرر هذه الخطوات، ولكن هذه المرة، حدد "المعرف العميل" ك `c00e9d32-3c8d-4a7d-832b-029040e7db99`. هذه القيمة هي Azure Information Protection Unified Labeling client ID.

تم الآن تسجيل خدمة DKE الخاصة بك. تابع عن [طريق إنشاء تسميات باستخدام DKE](#create-sensitivity-labels-using-dke).

## <a name="create-sensitivity-labels-using-dke"></a>إنشاء تسميات الحساسية باستخدام DKE

في مركز التوافق في Microsoft 365، أنشئ تسمية حساسية جديدة وطبق التشفير كما لو لم ترغب في ذلك. حدد **استخدام تشفير المفتاح المزدوج** وأدخل عنوان URL لنقطة النهاية للمفتاح. يجب تضمين اسم المفتاح الذي وفرته في المقطع "TestKeys" من ملف appsettings.json في عنوان URL.

على سبيل المثال: `https://testingdke1.azurewebsites.net/KEYNAME`

> [!div class="mx-imgBorder"]
> ![حدد استخدام تشفير المفتاح المزدوج في مركز التوافق في Microsoft 365.](../media/dke-use-dke.png)

ستبدأ أي تسميات DKE تضيفها بالظهور للمستخدمين في الإصدارات الأخيرة من Microsoft 365 Apps for enterprise.

> [!NOTE]
> قد يستغرق تحديث العملاء باستخدام التسميات الجديدة ما يصل إلى 24 ساعة.

### <a name="enable-dke-in-your-client"></a>تمكين DKE في العميل

إذا كنت أحد Office Insider، يتم تمكين DKE لك. وبخلاف ذلك، يمكنك تمكين DKE للعميل بإضافة مفاتيح التسجيل التالية:

```console
   [HKEY_LOCAL_MACHINE\SOFTWARE\WOW6432Node\Microsoft\MSIPC\flighting]
   "DoubleKeyProtection"=dword:00000001

   [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSIPC\flighting]
   "DoubleKeyProtection"=dword:00000001
```

## <a name="migrate-protected-files-from-hyok-labels-to-dke-labels"></a>ترحيل الملفات المحمية من تسميات HYOK إلى تسميات DKE

بعد الانتهاء من إعداد DKE، يمكنك ترحيل المحتوى الذي قمت بحمايتها باستخدام تسميات HYOK إلى تسميات DKE، إذا أردت ذلك. للترحيل، سوف تستخدم ماسح AIP الضوئي. للبدء باستخدام الماسح الضوئي، راجع [ما هو ماسح](/azure/information-protection/deploy-aip-scanner) التسمية الموحد لحماية معلومات Azure؟.

إذا لم تقوم بترحيل المحتوى، سيبقى المحتوى المحمي من HYOK غير متأثر.

## <a name="other-deployment-options"></a>خيارات النشر الأخرى

ندرك أن تنفيذ المرجع القياسي هذا باستخدام المفاتيح المستندة إلى البرامج قد لا يكون كافيا لبعض العملاء في الصناعات الخاضعة للتنظيم بشكل كبير لتلبية التزاماتهم واحتياجاتهم المحسنة. لقد قمنا بالمشاركة مع موردي وحدة أمان الأجهزة (HSM) الخاصة بالجهات الخارجية لدعم خيارات إدارة المفاتيح المحسنة في خدمة DKE، بما في ذلك:

- [ائتمن](https://www.entrust.com/digital-security/hsm/services/packaged-services/double-key-encryption-integration#:~:text=Entrust%20Double%20Key%20Encryption%20for%20Microsoft%20AIP%2C%20offered,trust%20for%20the%20protection%20of%20sensitive%20cryptographic%20keys.)

- [Thales](https://cpl.thalesgroup.com/cloud-security/encryption/double-key-encryption)

التواصل مباشرة مع هؤلاء الموردين للحصول على مزيد من المعلومات والإرشادات حول حلول DKE HSM في السوق.
