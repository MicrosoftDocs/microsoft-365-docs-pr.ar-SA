---
title: دعم حماية البيانات Azure Office 365 المشغل بواسطة 21Vianet
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
description: تعرف على المزيد حول Azure حماية البيانات (AIP) Office 365 المشغلة بواسطة 21Vianet وكيفية تكوينها للعملاء في الصين.
monikerRange: o365-21vianet
ms.openlocfilehash: 3b4906844c76293a1163d17d77b009528ef32f12
ms.sourcegitcommit: ac0ae5c2888e2b323e36bad041a4abef196c9c96
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/12/2022
ms.locfileid: "64782886"
---
# <a name="azure-information-protection-support-for-office-365-operated-by-21vianet"></a>دعم حماية البيانات Azure Office 365 المشغل بواسطة 21Vianet

تتناول هذه المقالة الاختلافات بين دعم Azure حماية البيانات (AIP) Office 365 المشغلة بواسطة 21Vianet والعروض التجارية، بالإضافة إلى إرشادات محددة لتكوين AIP للعملاء في الصين&mdash; بما في ذلك كيفية تثبيت الماسح الضوئي المحلي ل AIP وإدارة مهام فحص المحتوى.

## <a name="differences-between-aip-for-office-365-operated-by-21vianet-and-commercial-offerings"></a>الاختلافات بين AIP Office 365 المشغلة بواسطة 21Vianet والعروض التجارية

في حين أن هدفنا هو تقديم جميع الميزات والوظائف التجارية للعملاء في الصين مع AIP لدينا Office 365 المشغلة من قبل عرض 21Vianet، هناك بعض الوظائف المفقودة التي نود أن نسلط الضوء عليها.

تتضمن القائمة التالية الثغرات الموجودة بين AIP Office 365 المشغلة بواسطة 21Vianet وعروضنا التجارية اعتبارا من يناير 2021:

- يتم دعم تشفير خدمات إدارة حقوق Active Directory (AD RMS) فقط في Microsoft 365 Apps for enterprise (النسخة 11731.10000 أو أحدث). لا يدعم Office Professional Plus AD RMS.

- الترحيل من AD RMS إلى AIP غير متوفر حاليا.
  
- يتم دعم مشاركة رسائل البريد الإلكتروني المحمية مع المستخدمين في السحابة التجارية.
  
- لا تتوفر حاليا مشاركة المستندات ومرفقات البريد الإلكتروني مع المستخدمين في السحابة التجارية. يشمل ذلك Office 365 المشغلة من قبل 21Vianet المستخدمين في السحابة التجارية، وغير Office 365 المشغلة من قبل مستخدمي 21Vianet في السحابة التجارية، والمستخدمين الذين لديهم ترخيص RMS للأفراد.
  
- IRM مع SharePoint (المواقع والمكتبات المحمية بواسطة IRM) غير متوفرة حاليا.
  
- ملحق الجهاز المحمول ل AD RMS غير متوفر حاليا.

- لا يدعم Azure China 21Vianet عارض [الأجهزة المحمولة](/azure/information-protection/rms-client/mobile-app-faq) .

- منطقة AIP من مدخل Azure غير متوفرة للعملاء في الصين. استخدم [أوامر PowerShell](#step-6-install-the-aip-on-premises-scanner-and-manage-content-scan-jobs) بدلا من تنفيذ الإجراءات في المدخل، مثل إدارة مهام فحص المحتوى وتشغيلها.

- تختلف نقاط نهاية AIP في Office 365 المشغلة بواسطة 21Vianet عن نقاط النهاية المطلوبة للخدمات السحابية الأخرى. الاتصال بالشبكة من العملاء إلى نقاط النهاية التالية مطلوب:
    - تنزيل نهج التسمية والتسمية: `*.protection.partner.outlook.cn`
    - خدمة Azure Rights Management: `*.aadrm.cn`

## <a name="configure-aip-for-customers-in-china"></a>تكوين AIP للعملاء في الصين

لتكوين AIP للعملاء في الصين:
1. [تمكين إدارة الحقوق للمستأجر](#step-1-enable-rights-management-for-the-tenant).

1. [أضف كيان خدمة المزامنة حماية البيانات في Microsoft](#step-2-add-the-microsoft-information-protection-sync-service-service-principal).

1. [تكوين تشفير DNS](#step-3-configure-dns-encryption).

1. [تثبيت عميل التسمية الموحد ل AIP وتكوينه](#step-4-install-and-configure-the-aip-unified-labeling-client).

1. [تكوين تطبيقات AIP على Windows](#step-5-configure-aip-apps-on-windows).

1. [تثبيت الماسح الضوئي المحلي ل AIP وإدارة مهام فحص المحتوى](#step-6-install-the-aip-on-premises-scanner-and-manage-content-scan-jobs). 

### <a name="step-1-enable-rights-management-for-the-tenant"></a>الخطوة 1: تمكين إدارة الحقوق للمستأجر

لكي يعمل التشفير بشكل صحيح، يجب تمكين RMS للمستأجر.

1. تحقق مما إذا كان RMS ممكنا:

    1. تشغيل PowerShell كمسؤول.
    2. إذا لم يتم تثبيت الوحدة النمطية AIPService، فشغل `Install-Module AipService`.
    3. استيراد الوحدة النمطية باستخدام `Import-Module AipService`.
    4. الاتصال إلى الخدمة باستخدام `Connect-AipService -environmentname azurechinacloud`.
    5. تشغيل `(Get-AipServiceConfiguration).FunctionalState` والتحقق مما إذا كانت الحالة `Enabled`.

2. إذا كانت الحالة الوظيفية ، فشغل`Disabled``Enable-AipService`.

### <a name="step-2-add-the-microsoft-information-protection-sync-service-service-principal"></a>الخطوة 2: إضافة كيان خدمة مزامنة حماية البيانات في Microsoft

لا يتوفر كيان خدمة **حماية البيانات في Microsoft Sync Service** في مستأجري Azure China بشكل افتراضي، وهو مطلوب ل Azure حماية البيانات. إنشاء كيان هذه الخدمة يدويا عبر الوحدة النمطية Azure Az PowerShell.

1. إذا لم تكن وحدة Azure Az مثبتة لديك، فقم بتثبيتها أو استخدم موردا حيث تأتي وحدة Azure Az مثبتة مسبقا، مثل [Azure Cloud Shell](/azure/cloud-shell/overview). لمزيد من المعلومات، راجع [تثبيت الوحدة النمطية Azure Az PowerShell](/powershell/azure/install-az-ps).

1. الاتصال إلى الخدمة باستخدام [الاتصال-AzAccount](/powershell/module/az.accounts/Connect-AzAccount) cmdlet `azurechinacloud` واسم البيئة:

    ```powershell
    Connect-azaccount -environmentname azurechinacloud
    ```

1. إنشاء **كيان خدمة مزامنة حماية البيانات في Microsoft** يدويا باستخدام [cmdlet New-AzADServicePrincipal](/powershell/module/az.resources/new-azadserviceprincipal) ومعرف `870c4f2e-85b6-4d43-bdda-6ed9a579b725` التطبيق لخدمة المزامنة حماية البيانات في Microsoft:

    ```powershell 
    New-AzADServicePrincipal -ApplicationId 870c4f2e-85b6-4d43-bdda-6ed9a579b725
    ```

1. بعد إضافة كيان الخدمة، أضف الأذونات ذات الصلة المطلوبة إلى الخدمة.

### <a name="step-3-configure-dns-encryption"></a>الخطوة 3: تكوين تشفير DNS

لكي يعمل التشفير بشكل صحيح، يجب أن تتصل تطبيقات العميل Office بمثيل الصين للخدمة وتمهيد التشغيل من هناك. لإعادة توجيه تطبيقات العميل إلى مثيل الخدمة الصحيح، يجب على مسؤول المستأجر تكوين سجل DNS SRV مع معلومات حول عنوان URL ل Azure RMS. بدون سجل DNS SRV، سيحاول تطبيق العميل الاتصال بمثيل السحابة العامة بشكل افتراضي وسيفشل.

أيضا، الافتراض هو أن المستخدمين سيسجلون الدخول باستخدام اسم مستخدم يستند إلى المجال المملوك للمستأجر (على سبيل المثال)، `joe@contoso.cn`وليس `onmschina` اسم المستخدم (على سبيل المثال، `joe@contoso.onmschina.cn`). يتم استخدام اسم المجال من اسم المستخدم لإعادة توجيه DNS إلى مثيل الخدمة الصحيح.

#### <a name="configure-dns-encryption---windows"></a>تكوين تشفير DNS - Windows

1. الحصول على معرف RMS:

    1. تشغيل PowerShell كمسؤول.
    2. إذا لم يتم تثبيت الوحدة النمطية AIPService، فشغل `Install-Module AipService`.
    3. الاتصال إلى الخدمة باستخدام `Connect-AipService -environmentname azurechinacloud`.
    4. تشغيل `(Get-AipServiceConfiguration).RightsManagementServiceId` للحصول على معرف RMS.

2. سجل الدخول إلى موفر DNS، وانتقل إلى إعدادات DNS للمجال، ثم أضف سجل SRV جديدا.

    - الخدمة = `_rmsredir`
    - البروتوكول = `_http`
    - الاسم = `_tcp`
    - الهدف = `[GUID].rms.aadrm.cn` (حيث GUID هو معرف RMS)
    - الأولوية، الوزن، الثوان، TTL = القيم الافتراضية

3. إقران المجال المخصص بالمستأجر في مدخل [Azure](https://portal.azure.cn/#blade/Microsoft_AAD_IAM/ActiveDirectoryMenuBlade/Domains). سيؤدي ذلك إلى إضافة إدخال في DNS، والذي قد يستغرق عدة دقائق للتحقق منه بعد إضافة القيمة إلى إعدادات DNS.

4. سجل الدخول إلى مركز مسؤولي Microsoft 365 باستخدام بيانات اعتماد المسؤول العمومي المطابقة وأضف المجال (على سبيل المثال) `contoso.cn`لإنشاء المستخدم. في عملية التحقق، قد تكون هناك حاجة إلى تغييرات DNS إضافية. بمجرد الانتهاء من التحقق، يمكن إنشاء المستخدمين.

#### <a name="configure-dns-encryption---mac-ios-android"></a>تكوين تشفير DNS - Mac وiOS وAndroid

سجل الدخول إلى موفر DNS، وانتقل إلى إعدادات DNS للمجال، ثم أضف سجل SRV جديدا.

- الخدمة = `_rmsdisco`
- البروتوكول = `_http`
- الاسم = `_tcp`
- الهدف = `api.aadrm.cn`
- المنفذ = `80`
- الأولوية، الوزن، الثوان، TTL = القيم الافتراضية


### <a name="step-4-install-and-configure-the-aip-unified-labeling-client"></a>الخطوة 4: تثبيت عميل التسمية الموحد ل AIP وتكوينه

قم بتنزيل عميل التسمية الموحد ل AIP وتثبيته من [مركز تنزيل Microsoft](https://www.microsoft.com/download/details.aspx?id=53018).

لمزيد من المعلومات، اطلع على:

- [وثائق AIP](/azure/information-protection/)
- [محفوظات إصدار AIP ونهج الدعم](/azure/information-protection/rms-client/unifiedlabelingclient-version-release-history)
- [متطلبات نظام AIP](/azure/information-protection/requirements)
- [التشغيل السريع ل AIP: نشر عميل AIP](/azure/information-protection/quickstart-deploy-client)
- [دليل مسؤول AIP](/azure/information-protection/rms-client/clientv2-admin-guide)
- [دليل مستخدم AIP](/azure/information-protection/rms-client/clientv2-user-guide)
- [التعرف على تسميات الحساسية Microsoft 365](../../compliance/sensitivity-labels.md)

### <a name="step-5-configure-aip-apps-on-windows"></a>الخطوة 5: تكوين تطبيقات AIP على Windows

تحتاج تطبيقات AIP على Windows مفتاح التسجيل التالي للإشارة إلى السحابة السيادية الصحيحة ل Azure China:

- عقدة التسجيل = `HKEY_LOCAL_MACHINE\SOFTWARE\WOW6432Node\Microsoft\MSIP`
- الاسم = `CloudEnvType`
- القيمة = `6` (افتراضي = 0)
- النوع = `REG_DWORD`

> [!IMPORTANT]
> تأكد من عدم حذف مفتاح التسجيل بعد إلغاء التثبيت. إذا كان المفتاح فارغا أو غير صحيح أو غير موجود، فستتصرف الوظيفة كقيمة افتراضية (القيمة الافتراضية = 0 للسحابة التجارية). إذا كان المفتاح فارغا أو غير صحيح، تتم إضافة خطأ طباعة أيضا إلى السجل.

### <a name="step-6-install-the-aip-on-premises-scanner-and-manage-content-scan-jobs"></a>الخطوة 6: تثبيت الماسح الضوئي المحلي ل AIP وإدارة مهام فحص المحتوى

قم بتثبيت الماسح الضوئي المحلي ل AIP لفحص مشاركات الشبكة والمحتوى بحثا عن البيانات الحساسة، وتطبيق تسميات التصنيف والحماية كما تم تكوينها في نهج مؤسستك.

عند تكوين مهام فحص المحتوى وإدارتها، استخدم الإجراء التالي بدلا من [واجهة مدخل Azure](/azure/information-protection/deploy-aip-scanner-configure-install?tabs=azure-portal-only) التي تستخدمها العروض التجارية.

لمزيد من المعلومات، راجع [ما هو الماسح الضوئي الموحد للوصف في Azure حماية البيانات؟](/azure/information-protection/deploy-aip-scanner) [وإدارة مهام فحص المحتوى باستخدام PowerShell فقط](/azure/information-protection/deploy-aip-scanner-prereqs#use-powershell-with-a-disconnected-computer).

**لتثبيت الماسح الضوئي وتكوينه**:

1. سجل الدخول إلى كمبيوتر خادم Windows الذي سيقوم بتشغيل الماسح الضوئي. استخدم حسابا له حقوق المسؤول المحلي ولديه أذونات للكتابة إلى قاعدة بيانات SQL Server الرئيسية.

1. ابدأ مع إغلاق PowerShell. إذا قمت مسبقا بتثبيت عميل AIP والماسح الضوئي، فتأكد من إيقاف خدمة **AIPScanner** .

1. افتح جلسة عمل Windows PowerShell باستخدام الخيار **"تشغيل كمسؤول**".

1. قم بتشغيل [cmdlet Install-AIPScanner](/powershell/module/azureinformationprotection/Install-AIPScanner)، مع تحديد مثيل SQL Server الخاص بك لإنشاء قاعدة بيانات للماسح الضوئي حماية البيانات Azure، واسم ذي معنى لنظام مجموعة الماسح الضوئي الخاص بك.

    ```PowerShell
    Install-AIPScanner -SqlServerInstance <name> -Cluster <cluster name>
    ```

    > [!TIP]
    > يمكنك استخدام نفس اسم نظام المجموعة في الأمر [Install-AIPScanner](/powershell/module/azureinformationprotection/install-aipscanner) لإقران عقد الماسح الضوئي المتعددة بنفس المجموعة. يتيح استخدام المجموعة نفسها لعقد الماسح الضوئي المتعددة للماسحات الضوئية المتعددة العمل معا لإجراء عمليات الفحص الخاصة بك.
    > 

1. تحقق من تثبيت الخدمة الآن باستخدام **Administrative** **ToolsServices** > .

    تسمى الخدمة المثبتة **باسم الماسح الضوئي حماية البيانات Azure** ويتم تكوينها للتشغيل باستخدام حساب خدمة الماسح الضوئي الذي أنشأته.

1. احصل على رمز Azure المميز لاستخدامه مع الماسح الضوئي. يسمح رمز Azure AD المميز للماسح الضوئي بالمصادقة على خدمة azure حماية البيانات، ما يتيح تشغيل الماسح الضوئي بشكل غير تفاعلي. 

    1. افتح مدخل Microsoft Azure وأنشئ تطبيق Azure AD لتحديد رمز مميز للوصول للمصادقة. لمزيد من المعلومات، راجع [كيفية تسمية الملفات بشكل غير تفاعلي ل Azure حماية البيانات](/azure/information-protection/rms-client/clientv2-admin-guide-powershell#how-to-label-files-non-interactively-for-azure-information-protection).
    
        > [!TIP]
        > عند إنشاء تطبيقات Azure AD وتكوينها لأمر [Set-AIPAuthentication](/powershell/module/azureinformationprotection/set-aipauthentication) ، يعرض جزء **أذونات Application API واجهات** **برمجة التطبيقات التي تستخدمها مؤسستي** علامة التبويب بدلا من علامة تبويب **واجهات برمجة التطبيقات من Microsoft** . حدد **واجهات برمجة التطبيقات التي تستخدمها مؤسستي** لتحديد **خدمات إدارة حقوق Azure**. 
        >

    1. من كمبيوتر Windows Server، إذا تم منح حساب خدمة الماسح الضوئي حق **تسجيل الدخول محليا** للتثبيت، فسجل الدخول باستخدام هذا الحساب وابدأ جلسة عمل PowerShell. 
    
        إذا تعذر منح حساب خدمة الماسح الضوئي حق **تسجيل الدخول محليا** للتثبيت، فاستخدم المعلمة *OnBehalfOf* مع [Set-AIPAuthentication](/powershell/module/azureinformationprotection/set-aipauthentication)، كما هو موضح في [كيفية تسمية الملفات بشكل غير تفاعلي ل Azure حماية البيانات](/azure/information-protection/rms-client/clientv2-admin-guide-powershell#how-to-label-files-non-interactively-for-azure-information-protection).

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

    يحتوي الماسح الضوئي الآن على رمز مميز للمصادقة على Azure AD. هذا الرمز المميز صالح لمدة عام واحد أو عامين أو أبدا، وفقا لتكوينك **لسر عميل تطبيق الويب /API** في Azure AD. عند انتهاء صلاحية الرمز المميز، يجب تكرار هذا الإجراء.

1. قم بتشغيل [Set-AIPScannerConfiguration](/powershell/module/azureinformationprotection/set-aipscannerconfiguration) cmdlet لتعيين الماسح الضوئي للعمل في وضع عدم الاتصال. تشغيل:

    ```powershell
    Set-AIPScannerConfiguration -OnlineConfiguration Off
    ```

1. قم بتشغيل [Set-AIPScannerContentScanJob](/powershell/module/azureinformationprotection/set-aipscannercontentscanjob) cmdlet لإنشاء مهمة فحص محتوى افتراضية.

    المعلمة المطلوبة الوحيدة في **Set-AIPScannerContentScanJob** cmdlet هي **فرض**. ومع ذلك، قد تحتاج إلى تعريف إعدادات أخرى لمهمة فحص المحتوى في هذا الوقت. على سبيل المثال:

    ```powershell
    Set-AIPScannerContentScanJob -Schedule Manual -DiscoverInformationTypes PolicyOnly -Enforce Off -DefaultLabelType PolicyDefault -RelabelFiles Off -PreserveFileDetails On -IncludeFileTypes '' -ExcludeFileTypes '.msg,.tmp' -DefaultOwner <account running the scanner>
    ```

    يقوم بناء الجملة أعلاه بتكوين الإعدادات التالية أثناء متابعة التكوين:

    - الاحتفاظ بجدولة تشغيل الماسح الضوئي *يدويا*
    - تعيين أنواع المعلومات التي سيتم اكتشافها استنادا إلى نهج وصف الحساسية
    - *لا* يفرض نهج وصف الحساسية
    - تسمية الملفات تلقائيا استنادا إلى المحتوى، باستخدام التسمية الافتراضية المحددة لنهج وصف الحساسية
    - *لا* يسمح بإعادة تعيين الملفات
    - يحافظ على تفاصيل الملف أثناء المسح الضوئي والتسمية التلقائية، بما في ذلك *تاريخ التعديل**، وآخر تعديل*، وتعديل *بواسطة* القيم
    - تعيين الماسح الضوئي لاستثناء ملفات .msg و.tmp عند التشغيل
    - تعيين المالك الافتراضي إلى الحساب الذي تريد استخدامه عند تشغيل الماسح الضوئي

1. استخدم [cmdlet Add-AIPScannerRepository](/powershell/module/azureinformationprotection/add-aipscannerrepository) لتعريف المستودعات التي تريد مسحها ضوئيا في مهمة فحص المحتوى. على سبيل المثال، قم بتشغيل:

    ```powershell
    Add-AIPScannerRepository -OverrideContentScanJob Off -Path 'c:\repoToScan'
    ```
    
    استخدم إحدى بناءات الجملة التالية، اعتمادا على نوع المستودع الذي تضيفه:

    - لمشاركة شبكة، استخدم `\\Server\Folder`.
    - بالنسبة لمكتبة SharePoint، استخدم `http://sharepoint.contoso.com/Shared%20Documents/Folder`.
    - لمسار محلي: `C:\Folder`
    - لمسار UNC: `\\Server\Folder`

    > [!NOTE]
    > أحرف البدل غير معتمدة ومواقع WebDav غير معتمدة.
    >
    > لتعديل المستودع لاحقا، استخدم [Set-AIPScannerRepository](/powershell/module/azureinformationprotection/set-aipscannerrepository) cmdlet بدلا من ذلك. 


تابع الخطوات التالية حسب الحاجة:

- [تشغيل دورة اكتشاف وعرض التقارير للماسح الضوئي](/azure/information-protection/deploy-aip-scanner-manage#run-a-discovery-cycle-and-view-reports-for-the-scanner)
- [استخدام PowerShell لتكوين الماسح الضوئي لتطبيق التصنيف والحماية](/azure/information-protection/deploy-aip-scanner-configure-install?tabs=azure-portal-only#use-powershell-to-configure-the-scanner-to-apply-classification-and-protection)
- [استخدام PowerShell لتكوين نهج DLP باستخدام الماسح الضوئي](/azure/information-protection/deploy-aip-scanner-configure-install?tabs=azure-portal-only#use-powershell-to-configure-a-dlp-policy-with-the-scanner)

يسرد الجدول التالي أوامر PowerShell cmdlets ذات الصلة بتثبيت الماسح الضوئي وإدارة مهام فحص المحتوى:

| Cmdlet | الوصف |
|--|--|
| [Add-AIPScannerRepository](/powershell/module/azureinformationprotection/add-aipscannerrepository) | إضافة مستودع جديد إلى مهمة فحص المحتوى. |
| [Get-AIPScannerConfiguration](/powershell/module/azureinformationprotection/get-aipscannerconfiguration)|إرجاع تفاصيل حول نظام المجموعة الخاص بك. |
| [Get-AIPScannerContentScanJob](/powershell/module/azureinformationprotection/get-aipscannercontentscanjob) | الحصول على تفاصيل حول مهمة فحص المحتوى. |
| [Get-AIPScannerRepository](/powershell/module/azureinformationprotection/get-aipscannerrepository) | يحصل على تفاصيل حول المستودعات المحددة لمهمة فحص المحتوى. |
| [Remove-AIPScannerContentScanJob](/powershell/module/azureinformationprotection/remove-aipscannercontentscanjob) | حذف مهمة فحص المحتوى. |
| [Remove-AIPScannerRepository](/powershell/module/azureinformationprotection/remove-aipscannerrepository) | إزالة مستودع من مهمة فحص المحتوى. |
| [Set-AIPScannerContentScanJob](/powershell/module/azureinformationprotection/set-aipscannercontentscanjob) | تحديد إعدادات مهمة فحص المحتوى. |
| [Set-AIPScannerRepository](/powershell/module/azureinformationprotection/set-aipscannerrepository) | تعريف الإعدادات لمستودع موجود في مهمة فحص المحتوى. |
| | |

لمزيد من المعلومات، اطلع على:

- [ما هو الماسح الضوئي الموحد للوصف حماية البيانات Azure؟](/azure/information-protection/deploy-aip-scanner)
- [تكوين وتثبيت الماسح الضوئي الموحد للوصف في Azure حماية البيانات (AIP)](/azure/information-protection/deploy-aip-scanner-configure-install?tabs=powershell-only)
- [إدارة مهام فحص المحتوى باستخدام PowerShell فقط](/azure/information-protection/deploy-aip-scanner-prereqs#use-powershell-with-a-disconnected-computer).
