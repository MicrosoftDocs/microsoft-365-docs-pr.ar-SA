---
title: دعم Azure Information Protection Office 365 التي يتم تشغيلها بواسطة 21Vianet
f1.keywords:
- NOCSH
ms.author: sharik
author: skjerland
manager: scotv
audience: Admin
ms.topic: overview
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_NonTOC
ms.custom: AdminSurgePortfolio
search.appverid:
- MET150
- GEU150
- GEA150
description: تعرف على المزيد حول Azure Information Protection (AIP) Office 365 التي يتم تشغيلها بواسطة 21Vianet وكيفية تكوينها للعملاء في الصين.
monikerRange: o365-21vianet
ms.openlocfilehash: 44681286bce5e16a08f7400a2dbb083288a6f3b7
ms.sourcegitcommit: bae72428d229827cba4c807d9cd362417afbcccb
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 02/02/2022
ms.locfileid: "63569164"
---
# <a name="azure-information-protection-support-for-office-365-operated-by-21vianet"></a>دعم Azure Information Protection Office 365 التي يتم تشغيلها بواسطة 21Vianet

تغطي هذه المقالة الاختلافات بين دعم Azure Information Protection (AIP) ل Office 365 الذي يتم تشغيله بواسطة 21Vianet والعرض التجاري، بالإضافة إلى إرشادات محددة لتكوين AIP للعملاء في الصين&mdash;، بالإضافة إلى كيفية تثبيت الماسح الضوئي AIP المحلي وإدارة مهام فحص المحتوى.

## <a name="differences-between-aip-for-office-365-operated-by-21vianet-and-commercial-offerings"></a>الاختلافات بين AIP Office 365 التي يتم تشغيلها بواسطة 21Vianet والعرض التجاري

في حين أن هدفنا هو تقديم جميع الميزات والوظائف التجارية للعملاء في الصين باستخدام AIP ل Office 365 الذي يتم تشغيله بواسطة عرض 21Vianet، هناك بعض الوظائف المفقودة التي نريد تمييزها.

تتضمن القائمة التالية الفراغات الموجودة بين AIP Office 365 التي يتم تشغيلها بواسطة 21Vianet والعرض التجاري لدينا حتى يناير 2021:

- خدمات إدارة حقوق Active Directory تشفير (AD RMS) فقط في Microsoft 365 Apps for enterprise (البنية 11731.10000 أو أي وقت لاحق). Office Professional Plus لا تدعم AD RMS.

- الترحيل من AD RMS إلى AIP غير متوفر حاليا.
  
- يتم دعم مشاركة رسائل البريد الإلكتروني المحمية مع المستخدمين في السحابة التجارية.
  
- لا تتوفر حاليا مشاركة المستندات ومرفقات البريد الإلكتروني مع المستخدمين في السحابة التجارية. يشمل ذلك Office 365 التي يتم تشغيلها من قبل مستخدمي 21Vianet في السحابة التجارية وغير Office 365 التي يتم تشغيلها بواسطة 21Vianet المستخدمين في السحابة التجارية والمستخدمين الذين لديهم ترخيص RMS للأفراد.
  
- إدارة حقوق المعلومات SharePoint (المواقع والمكتبات المحمية من IRM) غير متوفرة حاليا.
  
- ملحق الجهاز المحمول ل AD RMS غير متوفر حاليا.

- لا [يدعم](/azure/information-protection/rms-client/mobile-app-faq) Azure China 21Vianet عارض الأجهزة المحمولة.

- لا تتوفر منطقة AIP في مدخل Azure للعملاء في الصين. استخدم [أوامر PowerShell](#step-6-install-the-aip-on-premises-scanner-and-manage-content-scan-jobs) بدلا من تنفيذ إجراءات في المدخل، مثل إدارة مهام فحص المحتوى وتشغيلها.

- تختلف نقاط نهاية AIP Office 365 التي يتم تشغيلها بواسطة 21Vianet عن نقاط النهاية المطلوبة للخدمات السحابية الأخرى. اتصال الشبكة من العملاء بنقاط النهاية التالية مطلوب:
    - تنزيل سياسات التسمية والتسميات: `*.protection.partner.outlook.cn`
    - خدمة Azure Rights Management: `*.aadrm.cn`

## <a name="configure-aip-for-customers-in-china"></a>تكوين AIP للعملاء في الصين

لتكوين AIP للعملاء في الصين:
1. [تمكين إدارة الحقوق للمستأجر](#step-1-enable-rights-management-for-the-tenant).

1. [أضف حماية البيانات في Microsoft خدمة المزامنة الأساسية](#step-2-add-the-microsoft-information-protection-sync-service-service-principal).

1. [تكوين تشفير DNS](#step-3-configure-dns-encryption).

1. [قم بتثبيت عميل تسمية AIP الموحد وتكوينه](#step-4-install-and-configure-the-aip-unified-labeling-client).

1. [تكوين تطبيقات AIP على Windows](#step-5-configure-aip-apps-on-windows).

1. [قم بتثبيت ماسح AIP المحلي وإدارة مهام فحص المحتوى](#step-6-install-the-aip-on-premises-scanner-and-manage-content-scan-jobs). 

### <a name="step-1-enable-rights-management-for-the-tenant"></a>الخطوة 1: تمكين إدارة الحقوق للمستأجر

لكي يعمل التشفير بشكل صحيح، يجب تمكين RMS للمستأجر.

1. تحقق مما إذا تم تمكين RMS:

    1. تشغيل PowerShell كمسؤول.
    2. إذا لم تكن الوحدة النمطية AIPService مثبتة، ف تشغيل `Install-Module AipService`.
    3. استيراد الوحدة النمطية باستخدام `Import-Module AipService`.
    4. الاتصال إلى الخدمة باستخدام `Connect-AipService -environmentname azurechinacloud`.
    5. قم `(Get-AipServiceConfiguration).FunctionalState` بتشغيل وتحقق مما إذا كانت الحالة هي `Enabled`.

2. إذا كانت الحالة الوظيفية هي `Disabled`، ف تشغيل `Enable-AipService`.

### <a name="step-2-add-the-microsoft-information-protection-sync-service-service-principal"></a>الخطوة 2: إضافة حماية البيانات في Microsoft خدمة المزامنة الأساسية

لا **حماية البيانات في Microsoft** الأساسي لخدمة مزامنة خدمة المزامنة في مستأجري Azure China بشكل افتراضي، وهو مطلوب لحماية معلومات Azure. أنشئ هذه الخدمة الأساسية يدويا عبر وحدة Azure Az PowerShell النمطية.

1. إذا لم تكن وحدة Azure Az النمطية مثبتة لديك، فقم بتثبيتها أو استخدم موردا حيث تكون وحدة Azure Az النمطية مثبتة مسبقا، مثل [Azure Cloud Shell](/azure/cloud-shell/overview). لمزيد من المعلومات، راجع [تثبيت وحدة Azure Az PowerShell النمطية](/powershell/azure/install-az-ps).

1. الاتصال إلى الخدمة باستخدام [الاتصال cmdlet الاتصال AzAccount](/powershell/module/az.accounts/Connect-AzAccount) واسم `azurechinacloud` البيئة:

    ```powershell
    Connect-azaccount -environmentname azurechinacloud
    ```

1. إنشاء **حماية البيانات في Microsoft** خدمة المزامنة الأساسية يدويا باستخدام cmdlet `870c4f2e-85b6-4d43-bdda-6ed9a579b725` الجديد [AzADServicePrincipal](/powershell/module/az.resources/new-azadserviceprincipal) وم id التطبيق لخدمة حماية البيانات في Microsoft المزامنة:

    ```powershell 
    New-AzADServicePrincipal -ApplicationId 870c4f2e-85b6-4d43-bdda-6ed9a579b725
    ```

1. بعد إضافة الخدمة الأساسية، أضف الأذونات ذات الصلة المطلوبة للخدمة.

### <a name="step-3-configure-dns-encryption"></a>الخطوة 3: تكوين تشفير DNS

لكي يعمل التشفير بشكل صحيح، Office تطبيقات العميل الاتصال مثيل الصين للخدمة والأحذية من هناك. لإعادة توجيه تطبيقات العميل إلى مثيل الخدمة الصحيح، يجب على مسؤول المستأجر تكوين سجل DNS SRV مع معلومات حول عنوان URL Azure RMS. بدون سجل DNS SRV، سيحاول تطبيق العميل الاتصال بمثيل السحابة العامة بشكل افتراضي وسيفشل.

كما أن الافتراض هو أن المستخدمين سيسجلون دخولهم باستخدام اسم مستخدم يستند إلى المجال الممتلك للمستأجر ( `joe@contoso.cn`على سبيل المثال، ) `onmschina` وليس اسم المستخدم (على سبيل المثال، `joe@contoso.onmschina.cn`). يتم استخدام اسم المجال من اسم المستخدم لإعادة توجيه DNS إلى مثيل الخدمة الصحيح.

#### <a name="configure-dns-encryption---windows"></a>تكوين تشفير DNS - Windows

1. احصل على "معر RMS":

    1. تشغيل PowerShell كمسؤول.
    2. إذا لم تكن الوحدة النمطية AIPService مثبتة، ف تشغيل `Install-Module AipService`.
    3. الاتصال إلى الخدمة باستخدام `Connect-AipService -environmentname azurechinacloud`.
    4. تشغيل `(Get-AipServiceConfiguration).RightsManagementServiceId` للحصول على "ID" ل RMS.

2. سجل دخولك إلى موفر DNS، وانتقل إلى إعدادات DNS للمجال، ثم أضف سجل SRV جديدا.

    - الخدمة = `_rmsredir`
    - البروتوكول = `_http`
    - Name = `_tcp`
    - Target = `[GUID].rms.aadrm.cn` (حيث GUID هو RMS ID)
    - الأولوية، الوزن، الثواني، TTL = القيم الافتراضية

3. إقران المجال المخصص بالمستأجر في [مدخل Azure](https://portal.azure.cn/#blade/Microsoft_AAD_IAM/ActiveDirectoryMenuBlade/Domains). سيضيف ذلك إدخالا في DNS، قد يستغرق التحقق منه عدة دقائق بعد إضافة القيمة إلى إعدادات DNS.

4. سجل دخولك إلى مركز مسؤولي Microsoft 365 باستخدام بيانات اعتماد المسؤول العام المطابقة وأضف المجال (`contoso.cn`على سبيل المثال، ) لإنشاء المستخدم. في عملية التحقق من الهوية، قد تكون هناك حاجة إلى تغييرات DNS إضافية. بعد أن يتم التحقق، يمكن إنشاء المستخدمين.

#### <a name="configure-dns-encryption---mac-ios-android"></a>تكوين تشفير DNS - Mac و iOS و Android

سجل دخولك إلى موفر DNS، وانتقل إلى إعدادات DNS للمجال، ثم أضف سجل SRV جديدا.

- الخدمة = `_rmsdisco`
- البروتوكول = `_http`
- Name = `_tcp`
- Target = `api.aadrm.cn`
- المنفذ = `80`
- الأولوية، الوزن، الثواني، TTL = القيم الافتراضية


### <a name="step-4-install-and-configure-the-aip-unified-labeling-client"></a>الخطوة 4: تثبيت عميل تسمية AIP الموحد وتكوينه

قم بتنزيل عميل التسمية الموحد AIP وتثبيته من [مركز التنزيل ل Microsoft](https://www.microsoft.com/download/details.aspx?id=53018).

لمزيد من المعلومات، اطلع على:

- [وثائق AIP](/azure/information-protection/)
- [محفوظات إصدار AIP ونسخة الدعم](/azure/information-protection/rms-client/unifiedlabelingclient-version-release-history)
- [متطلبات نظام AIP](/azure/information-protection/requirements)
- [سريع ل AIP: نشر عميل AIP](/azure/information-protection/quickstart-deploy-client)
- [دليل مسؤول AIP](/azure/information-protection/rms-client/clientv2-admin-guide)
- [دليل مستخدم AIP](/azure/information-protection/rms-client/clientv2-user-guide)
- [التعرف على Microsoft 365 الحساسية](../../compliance/sensitivity-labels.md)

### <a name="step-5-configure-aip-apps-on-windows"></a>الخطوة 5: تكوين تطبيقات AIP على Windows

تحتاج تطبيقات AIP Windows إلى مفتاح التسجيل التالي ليشير بها إلى السحابة السيادية الصحيحة ل Azure China:

- عقدة السجل = `HKEY_LOCAL_MACHINE\SOFTWARE\WOW6432Node\Microsoft\MSIP`
- Name = `CloudEnvType`
- Value = `6` (default = 0)
- Type = `REG_DWORD`

> [!IMPORTANT]
> تأكد من عدم حذف مفتاح التسجيل بعد إلغاء التثبيت. إذا كان المفتاح فارغا أو غير صحيح أو غير موجود، فإن الوظيفة ستتصرف كقيمة افتراضية (القيمة الافتراضية = 0 للسحابة التجارية). إذا كان المفتاح فارغا أو غير صحيح، فيضاف خطأ طباعة أيضا إلى السجل.

### <a name="step-6-install-the-aip-on-premises-scanner-and-manage-content-scan-jobs"></a>الخطوة 6: تثبيت ماسح AIP المحلي وإدارة مهام فحص المحتوى

ثبت الماسح الضوئي المحلي AIP لمسح الشبكة ومشتركات المحتوى ضوئيا للبيانات الحساسة، وتطبيق تسميات التصنيف والحماية كما تم تكوينها في نهج مؤسستك.

عند تكوين مهام فحص المحتوى وإدارتها، استخدم الإجراء التالي بدلا من واجهة [مدخل Azure](/azure/information-protection/deploy-aip-scanner-configure-install?tabs=azure-portal-only) المستخدمة بواسطة العروض التجارية.

لمزيد من المعلومات، راجع [ما هو ماسح](/azure/information-protection/deploy-aip-scanner) التسمية الموحد لحماية معلومات Azure؟ وإدارة مهام فحص المحتوى [باستخدام PowerShell فقط](/azure/information-protection/deploy-aip-scanner-prereqs#use-powershell-with-a-disconnected-computer).

**لتثبيت الماسح الضوئي وتكوينه**:

1. سجل الدخول إلى Windows Server الذي سيدير الماسح الضوئي. استخدم حسابا له حقوق المسؤول المحلي لديه أذونات للكتابة على SQL Server الرئيسية.

1. ابدأ ب PowerShell مغلق. إذا قمت مسبقا بتثبيت عميل AIP والماسح الضوئي، فتأكد من إيقاف خدمة **AIPScanner** .

1. افتح جلسة Windows PowerShell باستخدام **الخيار تشغيل كمسؤول**.

1. قم بتشغيل [الأمر cmdlet Install-AIPScanner](/powershell/module/azureinformationprotection/Install-AIPScanner)، مع تحديد مثيل SQL Server لإنشاء قاعدة بيانات للماسح الضوئي Azure Information Protection، واسم ذي معنى لنسخة الماسح الضوئي.

    ```PowerShell
    Install-AIPScanner -SqlServerInstance <name> -Cluster <cluster name>
    ```

    > [!TIP]
    > يمكنك استخدام اسم المجموعة نفسه في الأمر [Install-AIPScanner](/powershell/module/azureinformationprotection/install-aipscanner) لاقتران عقد ماسح ضوئي متعددة بنفس المجموعة. يؤدي استخدام المجموعة نفسها لعقد الماسح الضوئي المتعددة إلى تمكين العديد من الماسحات الضوئية من العمل معا لتنفيذ عمليات الفحص.
    > 

1. تحقق من تثبيت الخدمة الآن باستخدام **الأدوات** **الإداريةServices** > .

    تسمى الخدمة المثبتة **Azure Information Protection Scanner** وقد تم تكوينها للتشغيل باستخدام حساب خدمة الماسح الضوئي الذي أنشأته.

1. احصل على رمز Azure مميز لاستخدامه مع الماسح الضوئي. يتيح الرمز المميز Azure AD للماسح الضوئي المصادقة على خدمة Azure Information Protection، مما يمكن الماسح الضوئي من العمل بشكل غير تفاعلي. 

    1. افتح مدخل Azure وأنشئ تطبيق Azure AD لتحديد رمز وصول مميز للمصادقة. لمزيد من المعلومات، [راجع كيفية تسمية الملفات بطريقة غير تفاعلية ل Azure Information Protection](/azure/information-protection/rms-client/clientv2-admin-guide-powershell#how-to-label-files-non-interactively-for-azure-information-protection).
    
        > [!TIP]
        > عند إنشاء تطبيقات Azure AD وتكوينها لأوامر [Set-AIPAuthentication](/powershell/module/azureinformationprotection/set-aipauthentication)، يعرض جزء أذونات "طلب **API**" علامة التبويب واجهات برمجة التطبيقات التي تستخدمها مؤسستك بدلا من علامة التبويب **واجهات** برمجة تطبيقات Microsoft. حدد **واجهات برمجة التطبيقات التي تستخدمها المؤسسة** لتحديد **Azure Rights Management Services**. 
        >

    1. من الكمبيوتر Windows Server، إذا تم منح حساب خدمة الماسح الضوئي تسجيل الدخول محليا مباشرة إلى التثبيت، فسجل الدخول باستخدام هذا الحساب وابدأ جلسة عمل PowerShell. 
    
        إذا لم يتم منح حساب خدمة الماسح الضوئي تسجيل  الدخول محليا مباشرة من أجل التثبيت، فاستخدم المعلمة *OnBehalfOf* مع [Set-AIPAuthentication](/powershell/module/azureinformationprotection/set-aipauthentication)، كما هو موضح في كيفية تسمية ملفات غير تفاعلية ل [Azure Information Protection](/azure/information-protection/rms-client/clientv2-admin-guide-powershell#how-to-label-files-non-interactively-for-azure-information-protection).

    1. تشغيل [Set-AIPAuthentication](/powershell/module/azureinformationprotection/set-aipauthentication)، مع تحديد القيم المنسوخة من تطبيق Azure AD:

      ```PowerShell
      Set-AIPAuthentication -AppId <ID of the registered app> -AppSecret <client secret sting> -TenantId <your tenant ID> -DelegatedUser <Azure AD account>
      ```

      على سبيل المثال:

      ```PowerShell
      $pscreds = Get-Credential CONTOSO\scanner
      Set-AIPAuthentication -AppId "77c3c1c3-abf9-404e-8b2b-4652836c8c66" -AppSecret "OAkk+rnuYc/u+]ah2kNxVbtrDGbS47L4" -DelegatedUser scanner@contoso.com -TenantId "9c11c87a-ac8b-46a3-8d5c-f4d0b72ee29a" -OnBehalfOf $pscreds
      Acquired application access token on behalf of CONTOSO\scanner.
      ```

    أصبح للماسح الضوئي الآن رمز مميز للمصادقة على Azure AD. هذا الرمز المميز صالح لمدة سنة واحدة أو عامين أو لا يكون صالحا أبدا، وفقا لتكوين سرية عميل **تطبيق ويب /API** في Azure AD. عند انتهاء صلاحية الرمز المميز، يجب تكرار هذا الإجراء.

1. قم بتشغيل [الأمر cmdlet Set-AIPScannerConfiguration](/powershell/module/azureinformationprotection/set-aipscannerconfiguration) لتعيين الماسح الضوئي للعمل في الوضع غير المتصل. تشغيل:

    ```powershell
    Set-AIPScannerConfiguration -OnlineConfiguration Off
    ```

1. قم بتشغيل [الأمر cmdlet Set-AIPScannerContentScanJob](/powershell/module/azureinformationprotection/set-aipscannercontentscanjob) لإنشاء مهمة فحص محتوى افتراضية.

    المعلمة الوحيدة المطلوبة في **الأمر Cmdlet Set-AIPScannerContentScanJob** هي **فرض**. ومع ذلك، قد ترغب في تحديد إعدادات أخرى لمهمة فحص المحتوى في الوقت نفسه. على سبيل المثال:

    ```powershell
    Set-AIPScannerContentScanJob -Schedule Manual -DiscoverInformationTypes PolicyOnly -Enforce Off -DefaultLabelType PolicyDefault -RelabelFiles Off -PreserveFileDetails On -IncludeFileTypes '' -ExcludeFileTypes '.msg,.tmp' -DefaultOwner <account running the scanner>
    ```

    بناء الجملة أعلاه تكوين الإعدادات التالية أثناء متابعة التكوين:

    - يحافظ على جدولة تشغيل الماسح الضوئي *يدويا*
    - تعيين أنواع المعلومات التي سيتم اكتشافها استنادا إلى نهج تسمية الحساسية
    - لا *يفرض* نهج تسمية الحساسية
    - تسميات الملفات تلقائيا استنادا إلى المحتوى، باستخدام التسمية الافتراضية المعرفة لن نهج تسمية الحساسية
    - لا *يسمح* ب إعادة وضع التكبيل على الملفات
    - الاحتفاظ بتفاصيل الملف أثناء الفحص والتسميات التلقائية، بما في ذلك تاريخ التعديل والتعديل الأخير وتعديل *القيم*
    - تعيين الماسح الضوئي لاستبعاد ملفات .msg و .tmp عند التشغيل
    - تعيين المالك الافتراضي للحساب الذي تريد استخدامه عند تشغيل الماسح الضوئي

1. استخدم [الأمر cmdlet Add-AIPScannerRepository](/powershell/module/azureinformationprotection/add-aipscannerrepository) لتعريف المستودعات التي تريد فحصها في مهمة فحص المحتوى. على سبيل المثال، تشغيل:

    ```powershell
    Add-AIPScannerRepository -OverrideContentScanJob Off -Path 'c:\repoToScan'
    ```
    
    استخدم أحد بناء الجملة التالي، استنادا إلى نوع المستودع الذي تضيفه:

    - للحصول على مشاركة شبكة، استخدم `\\Server\Folder`.
    - للحصول على SharePoint، استخدم `http://sharepoint.contoso.com/Shared%20Documents/Folder`.
    - لمسار محلي: `C:\Folder`
    - لمسار UNC: `\\Server\Folder`

    > [!NOTE]
    > أحرف البدل غير معتمدة ومواقع WebDav غير معتمدة.
    >
    > لتعديل المستودع لاحقا، استخدم الأمر [Cmdlet Set-AIPScannerRepository](/powershell/module/azureinformationprotection/set-aipscannerrepository) بدلا من ذلك. 


تابع الخطوات التالية حسب الحاجة:

- [تشغيل دورة اكتشاف وعرض التقارير للماسح الضوئي](/azure/information-protection/deploy-aip-scanner-manage#run-a-discovery-cycle-and-view-reports-for-the-scanner)
- [استخدام PowerShell لتكوين الماسح الضوئي لتطبيق التصنيف والحماية](/azure/information-protection/deploy-aip-scanner-configure-install?tabs=azure-portal-only#use-powershell-to-configure-the-scanner-to-apply-classification-and-protection)
- [استخدام PowerShell لتكوين نهج DLP باستخدام الماسح الضوئي](/azure/information-protection/deploy-aip-scanner-configure-install?tabs=azure-portal-only#use-powershell-to-configure-a-dlp-policy-with-the-scanner)

يسرد الجدول التالي قوائم PowerShell cmdlets ذات الصلة بتثبيت الماسح الضوئي وإدارة مهام فحص المحتوى:

| Cmdlet | الوصف |
|--|--|
| [Add-AIPScannerRepository](/powershell/module/azureinformationprotection/add-aipscannerrepository) | إضافة مستودع جديد إلى مهمة فحص المحتوى. |
| [Get-AIPScannerConfiguration](/powershell/module/azureinformationprotection/get-aipscannerconfiguration)|إرجاع تفاصيل حول نظام المجموعة. |
| [Get-AIPScannerContentScanJob](/powershell/module/azureinformationprotection/get-aipscannercontentscanjob) | الحصول على تفاصيل حول مهمة فحص المحتوى. |
| [Get-AIPScannerRepository](/powershell/module/azureinformationprotection/get-aipscannerrepository) | الحصول على تفاصيل حول المستودعات المعرفة لمهمة فحص المحتوى. |
| [Remove-AIPScannerContentScanJob](/powershell/module/azureinformationprotection/remove-aipscannercontentscanjob) | حذف مهمة فحص المحتوى. |
| [Remove-AIPScannerRepository](/powershell/module/azureinformationprotection/remove-aipscannerrepository) | يزيل مستودعا من مهمة فحص المحتوى. |
| [Set-AIPScannerContentScanJob](/powershell/module/azureinformationprotection/set-aipscannercontentscanjob) | تعريف الإعدادات لمهمة فحص المحتوى. |
| [Set-AIPScannerRepository](/powershell/module/azureinformationprotection/set-aipscannerrepository) | تعريف الإعدادات لمستودع موجود في مهمة فحص المحتوى. |
| | |

لمزيد من المعلومات، اطلع على:

- [ما هو ماسح تسميات Azure Information Protection الموحد؟](/azure/information-protection/deploy-aip-scanner)
- [تكوين الماسح الضوئي الموحد لتسمية Azure Information Protection (AIP) وتثبيته](/azure/information-protection/deploy-aip-scanner-configure-install?tabs=powershell-only)
- [يمكنك إدارة مهام فحص المحتوى باستخدام PowerShell فقط](/azure/information-protection/deploy-aip-scanner-prereqs#use-powershell-with-a-disconnected-computer).
