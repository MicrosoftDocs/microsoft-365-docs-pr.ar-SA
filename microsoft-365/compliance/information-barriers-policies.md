---
title: بدء استخدام حواجز المعلومات
description: تعرف على كيفية بدء استخدام حواجز المعلومات.
ms.author: robmazz
author: robmazz
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
ms.collection:
- M365-security-compliance
- m365solution-mip
- m365initiative-compliance
ms.localizationpriority: ''
f1.keywords:
- NOCSH
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 1a9b6a4000b6d96fa8fe60b3abc60ff01676073e
ms.sourcegitcommit: 7b83e2605895fee5c73cd1d01f4cd16e1457a69f
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 11/11/2021
ms.locfileid: "63568563"
---
# <a name="get-started-with-information-barriers"></a>بدء استخدام حواجز المعلومات

باستخدام حواجز المعلومات، يمكنك تعريف سياسات تم تصميمها لمنع شرائح معينة من المستخدمين من التواصل مع بعضهم البعض أو السماح لشرائح معينة بالتواصل مع بعض الشرائح الأخرى فقط. يمكن أن تساعد سياسات حاجز المعلومات مؤسستك على الحفاظ على الامتثال للمعايير واللوائح الصناعية ذات الصلة، وتجنب التعارضات المحتملة في الاهتمامات. لمزيد من المعلومات، راجع [التعرف على حواجز المعلومات](information-barriers.md).

تصف هذه المقالة كيفية تكوين سياسات حاجز المعلومات. هناك العديد من الخطوات التي يجب اتخاذها، لذا تأكد من مراجعة العملية بأكملها قبل بدء تكوين سياسات حاجز المعلومات.

> [!TIP]
> تتضمن هذه المقالة [سيناريو مثال](#example-scenario-contosos-departments-segments-and-policies) لمساعدتك على التخطيط لنهج حاجز المعلومات وتحديدها.

## <a name="concepts"></a>المفاهيم

عند تحديد نهج لعوائق المعلومات، ستعمل مع سمات حساب المستخدم والمشرائح ونهج "الحظر" و/أو "السماح" وتطبيق النهج.

- يتم تعريف سمات حساب المستخدم في Azure Active Directory (أو Exchange Online). يمكن أن تتضمن هذه السمات القسم والملقب الوظيفي والموقع واسم الفريق وتفاصيل ملف التعريف الوظيفي الأخرى.
- إن الشرائح هي مجموعات من المستخدمين الذين تم تعريفهم في مركز التوافق في Microsoft 365 باستخدام سمة حساب **مستخدم محددة**. (راجع [قائمة السمات المعتمدة](information-barriers-attributes.md).)
- تحدد سياسات حاجز المعلومات حدود الاتصالات أو قيودها. عندما تحدد سياسات حاجز المعلومات، يمكنك الاختيار من بين نوعين من السياسات:
  - *تمنع* سياسات الحظر مقطعا من التواصل مع مقطع آخر.
  - *السماح* لنهج السماح لم مقطع واحد بالتواصل مع بعض الشرائح الأخرى فقط.
- يتم تطبيق النهج بعد تعريف كل نهج حاجز المعلومات، وأنك جاهز لتطبيقها في مؤسستك.

## <a name="configuration-at-a-glance"></a>التكوين بنظرة سريعة

| **الخطوات** | **ما الذي يجب أن يحدث** |
|:------|:----------------|
| **الخطوة 1**: [التأكد من تحقيق المتطلبات الأساسية](#step-1-make-sure-prerequisites-are-met) | - التحقق من أن لديك [الأذونات والتراخيص المطلوبة](information-barriers.md#required-licenses-and-permissions)<br/>- التحقق من أن الدليل الخاص بك يتضمن بيانات للمستخدمين المجزئين<br/>- تمكين البحث في الدليل ضمن النطاق عن Microsoft Teams<br/>- تأكد من تشغيل تسجيل التدقيق<br/>- التأكد من عدم Exchange نهج دفتر العنوان في مكانها<br/>- استخدام PowerShell (يتم توفير أمثلة)<br/>- تقديم موافقة المسؤول Microsoft Teams (الخطوات مضمنة) |
| **الخطوة 2**: [تقسيم المستخدمين في مؤسستك](#step-2-segment-users-in-your-organization) | - تحديد ما هي السياسات المطلوبة<br/>- قم بصنع قائمة بالشرائح لتعريفها<br/>- تحديد السمات التي يجب استخدامها<br/>- تعريف الشرائح من حيث عوامل تصفية النهج |
| **الخطوة 3**: [تعريف سياسات حاجز المعلومات](#step-3-define-information-barrier-policies) | - تعريف سياساتك (لا تنطبق بعد)<br/>- اختر من نوعين (الحظر أو السماح) |
| **الخطوة 4**: [تطبيق سياسات حاجز المعلومات](#step-4-apply-information-barrier-policies) | - تعيين النهج إلى الحالة النشطة<br/>- تشغيل تطبيق النهج<br/>- عرض حالة النهج |
| **الخطوة 5**: تكوين عوائق المعلومات على SharePoint [OneDrive (اختياري)](#step-5-configuration-for-information-barriers-on-sharepoint-and-onedrive) | - تكوين حواجز المعلومات SharePoint OneDrive |
| **الخطوة 6**: [أوضاع حواجز المعلومات (اختيارية)](#step-6-information-barriers-modes) | - تحديث أوضاع حاجز المعلومات إذا كان ذلك قابلا للتطبيق |

## <a name="step-1-make-sure-prerequisites-are-met"></a>الخطوة 1: التأكد من تحقيق المتطلبات الأساسية

بالإضافة إلى [الأذونات والتراخيص](information-barriers.md#required-licenses-and-permissions) المطلوبة، تأكد من تلبية المتطلبات التالية قبل تكوين حواجز المعلومات:

- **بيانات الدليل**: تأكد من أن بنية مؤسستك تنعكس في بيانات الدليل. لاتخاذ هذا الإجراء، تأكد من ملء سمات حساب المستخدم، مثل عضوية المجموعة واسم القسم وغير ذلك بشكل صحيح في Azure Active Directory (أو Exchange Online). لمعرفة المزيد، راجع الموارد التالية:
  - [سمات سياسات حاجز المعلومات](information-barriers-attributes.md)
  - [إضافة معلومات ملف تعريف مستخدم أو تحديثها باستخدام Azure Active Directory](/azure/active-directory/fundamentals/active-directory-users-profile-azure-portal)
  - [تكوين خصائص حساب المستخدم باستخدام Office 365 PowerShell](../enterprise/configure-user-account-properties-with-microsoft-365-powershell.md)

- **البحث في الدليل ضمن** نطاق: قبل تحديد نهج حاجز المعلومات الأول في مؤسستك، يجب تمكين البحث في الدليل ضمن [نطاق](/MicrosoftTeams/teams-scoped-directory-search) في Microsoft Teams. انتظر 24 ساعة على الأقل بعد تمكين البحث في الدليل ضمن نطاق قبل إعداد أو تعريف سياسات حاجز المعلومات.

- **Exchange Online التراخيص**: تعمل سياسات عوائق المعلومات فقط إذا تم تعيين ترخيص Exchange Online للمستخدمين الهدف.

- **تحقق من تمكين تسجيل التدقيق**: للبحث عن حالة تطبيق نهج، يجب تشغيل تسجيل التدقيق. يتم تمكين التدقيق Microsoft 365 المؤسسات بشكل افتراضي. قد تكون بعض المؤسسات قد عطلت التدقيق لأسباب معينة. إذا كانت عملية التدقيق معطلة لمنظمتك، فقد يكون ذلك بسبب إيقاف تشغيلها من قبل مسؤول آخر. نوصي بتأكيد أنه لا بأس في تشغيل التدقيق مرة أخرى عند إكمال هذه الخطوة. لمزيد من المعلومات، راجع [تشغيل البحث في سجل التدقيق أو إيقاف تشغيله](turn-audit-log-search-on-or-off.md).

- **لا توجد أي سياسات ل دفتر** العنوان: قبل تحديد سياسات حاجز المعلومات وتطبيقها، تأكد من عدم Exchange نهج دفتر العنوان. تستند حواجز المعلومات إلى سياسات دفتر العنوان، ولكن هذين النوعين من السياسات غير متوافقين. إذا كان لديك مثل هذه السياسات، فتأكد من إزالة سياسات دفتر [العنوان أولا](/exchange/address-books/address-book-policies/remove-an-address-book-policy) . بمجرد تمكين سياسات حاجز المعلومات وتمكين دفتر العنوان الهرمي، سيشاهد جميع المستخدمين غير المضمنين **** في مقطع حاجز المعلومات دفتر العنوان الهرمي في Exchange الإنترنت.[](/exchange/address-books/hierarchical-address-books/hierarchical-address-books)

- **إدارة استخدام PowerShell**: يتم حاليا تعريف سياسات حاجز المعلومات وإدارتها في مركز التوافق & PowerShell. على الرغم من توفر العديد من الأمثلة في هذه المقالة، إلا أنك ستحتاج إلى التعرف على cmdlets والمعلمات في PowerShell. ستحتاج أيضا إلى وحدة Azure Active Directory PowerShell النمطية.
  - [الاتصال إلى مركز & التوافق PowerShell](/powershell/exchange/connect-to-scc-powershell)
  - [تثبيت Azure Active Directory PowerShell Graph](/powershell/azure/active-directory/install-adv2)

- موافقة المسؤول على عوائق المعلومات في **Microsoft Teams**: عند وضع سياسات IB في مكانها، يمكنه إزالة المستخدمين غير المتوافقين مع IB من المجموعات (أي قنوات Teams المستندة إلى المجموعات). يساعد هذا التكوين على ضمان التزام مؤسستك بالأنظمة والسياسات. استخدم الإجراء التالي لتمكين عمل سياسات حاجز المعلومات كما هو متوقع في Microsoft Teams.

   1. المتطلبات الأساسية: [تثبيت Azure Active Directory PowerShell Graph](/powershell/azure/active-directory/install-adv2).

   1. تشغيل cmdlets التالية في PowerShell:

      ```powershell
      Connect-AzureAD -Tenant "<yourtenantdomain.com>"  //for example: Connect-AzureAD -Tenant "Contoso.onmicrosoft.com"
      $appId="bcf62038-e005-436d-b970-2a472f8c1982" 
      $sp=Get-AzureADServicePrincipal -Filter "appid eq '$($appid)'"
      if ($sp -eq $null) { New-AzureADServicePrincipal -AppId $appId }
      Start-Process  "https://login.microsoftonline.com/common/adminconsent?client_id=$appId"
      ```

   1. عند مطالبتك بذلك، سجل الدخول باستخدام حساب العمل أو المدرسة Office 365.

   1. في مربع **الحوار الأذونات المطلوبة** ، راجع المعلومات، ثم اختر **قبول**. يتم تقديم الأذونات التي يطلبها التطبيق أدناه.

      > [!div class="mx-imgBorder"]
      > ![صورة.](https://user-images.githubusercontent.com/8932063/107690955-b1772300-6c5f-11eb-9527-4235de860b27.png)

عند كل المتطلبات الأساسية، انتقل إلى الخطوة التالية.

> [!TIP]
> لمساعدتك على إعداد خطتك، يتم تضمين سيناريو مثال في هذه المقالة. [راجع أقسام Contoso وشرائحه ونهجه](#example-scenario-contosos-departments-segments-and-policies).

## <a name="step-2-segment-users-in-your-organization"></a>الخطوة 2: تقسيم المستخدمين في مؤسستك

أثناء هذه الخطوة، ستحدد سياسات حاجز المعلومات المطلوبة، وتصنع قائمة بالشرائح المطلوب تعريفها، ثم تحدد الشرائح.

### <a name="determine-what-policies-are-needed"></a>تحديد ما هي السياسات المطلوبة

مع وضع القوانين واللوائح الصناعية في الاعتبار، من هي المجموعات ضمن مؤسستك التي ستحتاج إلى سياسات حاجز المعلومات؟ قم بصنع قائمة. هل هناك أي مجموعات يجب منعها من التواصل مع مجموعة أخرى؟ هل هناك أي مجموعات يجب السماح لها بالتواصل مع مجموعة واحدة أو اثنتين فقط؟ فكر في السياسات التي تحتاج إليها على أنها تنتمي إلى إحدى المجموعتين:

- تمنع سياسات "الحظر" إحدى المجموعات من التواصل مع مجموعة أخرى.
- تسمح سياسات "السماح" لمجموعة بالتواصل مع مجموعات معينة أخرى فقط.

عندما يكون لديك القائمة الأولية للمجموعات والسياسات، تابع لتحديد الشرائح التي ستحتاج إليها.

### <a name="identify-segments"></a>تحديد الشرائح

بالإضافة إلى قائمة سياساتك الأولية، يمكنك وضع قائمة بالشرائح لمنظمتك. يجب أن ينتمي المستخدمون الذين سيتم تضمينهم في سياسات حاجز المعلومات إلى مقطع. يمكنك التخطيط للشرائح بعناية حيث يمكن أن يكون المستخدم في مقطع واحد فقط. يمكن تطبيق نهج حاجز معلومات واحد فقط على كل مقطع.

> [!IMPORTANT]
> يمكن للمستخدم أن يكون في مقطع واحد فقط.

حدد السمات في بيانات دليل مؤسستك التي تستخدمها لتعريف الشرائح. يمكنك استخدام *القسم* أو *MemberOf* أو أي من السمات المعتمدة. تأكد من أن لديك قيما في السمة التي تحددها للمستخدمين. [راجع قائمة السمات المعتمدة لعوائق المعلومات](information-barriers-attributes.md).

> [!IMPORTANT]
> **قبل المتابعة إلى المقطع** التالي، تأكد من أن بيانات الدليل بها قيم السمات التي يمكنك استخدامها لتعريف المقاطع. إذا لم تتضمن بيانات الدليل قيما للخصائص التي تريد استخدامها، فيجب تحديث حسابات المستخدمين لتضمين هذه المعلومات قبل المتابعة إلى الحواجز المتعلقة بالمعلومات. للحصول على تعليمات حول ذلك، راجع الموارد التالية:<br/>- [تكوين خصائص حساب المستخدم باستخدام Office 365 PowerShell](../enterprise/configure-user-account-properties-with-microsoft-365-powershell.md)<br/>- [إضافة معلومات ملف تعريف مستخدم أو تحديثها باستخدام Azure Active Directory](/azure/active-directory/fundamentals/active-directory-users-profile-azure-portal)

### <a name="define-segments-using-powershell"></a>تعريف الشرائح باستخدام PowerShell

لا يؤثر تحديد الشرائح على المستخدمين؛ فهو فقط يهيئ مرحلة تعريف سياسات حاجز المعلومات ثم تطبيقها.

1. استخدم **الأمر cmdlet New-OrganizationSegment** مع المعلمة **UserGroupFilter** التي تتوافق مع [السمة](information-barriers-attributes.md) التي تريد استخدامها.

    | بناء الجملة | مثال |
    |:---------|:----------|
    | `New-OrganizationSegment -Name "segmentname" -UserGroupFilter "attribute -eq 'attributevalue'"` |`New-OrganizationSegment -Name "HR" -UserGroupFilter "Department -eq 'HR'"` <p>في هذا المثال، يتم تعريف مقطع يسمى *الموارد* البشرية باستخدام *الموارد البشرية*، وهي قيمة في *سمة القسم* . يشير **الجزء -eq** من الأمر cmdlet إلى "يساوي". (بدلا من ذلك، يمكنك استخدام **-ne** لتعني "not equals". راجع [استخدام "يساوي" و"لا يساوي" في تعريفات المقطع](#using-equals-and-not-equals-in-segment-definitions).) |

    بعد تشغيل كل cmdlet، يجب أن ترى قائمة بتفاصيل حول المقطع الجديد. تتضمن التفاصيل نوع المقطع، ومن أنشأه أو قام بتعديله آخر مرة، وما إلى ذلك. 

2. كرر هذه العملية لكل مقطع تريد تعريفه.

    > [!IMPORTANT]
    > **تأكد من عدم تداخل** الشرائح. يجب أن ينتمي كل مستخدم سيتأثر بعوائق المعلومات إلى مقطع واحد (ومستخدم واحد فقط). يجب ألا ينتمي أي مستخدم إلى مقطعين أو أكثر. (راجع [مثال: الشرائح المعرفة في Contoso](#contosos-defined-segments) في هذه المقالة.)

بعد تحديد الشرائح، تابع لتعريف [سياسات حاجز المعلومات](#step-3-define-information-barrier-policies).

### <a name="using-equals-and-not-equals-in-segment-definitions"></a>استخدام "يساوي" و"لا يساوي" في تعريفات المقطع

في المثال التالي، نقوم بتعريف مقطع مثل "القسم يساوي الموارد البشرية". 

| مثال | ملاحظة |
|:----------|:-------|
|`New-OrganizationSegment -Name "HR" -UserGroupFilter "Department -eq 'HR'"` | لاحظ أنه في هذا المثال، يتضمن تعريف المقطع معلمة "يساوي" تشير إلى **eq-**. |

يمكنك أيضا تعريف الشرائح باستخدام معلمة "لا يساوي"، والموضحة ب **-ne**، كما هو موضح في الجدول التالي:

| بناء الجملة | مثال |
|:---------|:----------|
| `New-OrganizationSegment -Name "NotSales" -UserGroupFilter "Department -ne 'Sales'"` | في هذا المثال، قمنا بتعريف مقطع يسمى *NotSales* يتضمن كل شخص غير في *المبيعات*. يشير **الجزء -ne** من الأمر cmdlet إلى "لا يساوي". |

بالإضافة إلى تعريف الشرائح باستخدام "يساوي" أو "لا يساوي"، يمكنك تعريف مقطع باستخدام معلمتي "يساوي" و"لا يساوي". يمكنك أيضا تعريف عوامل تصفية المجموعات المعقدة باستخدام عوامل تشغيل *AND* و *OR* المنطقية.

| بناء الجملة | مثال |
|:---------|:----------|
| `New-OrganizationSegment -Name "LocalFTE" -UserGroupFilter "Location -eq 'Local'" -and "Position -ne 'Temporary'"` | في هذا المثال، قمنا بتعريف مقطع يسمى *LocalFTE* يتضمن أشخاصا موجودين محليا ومواقفهم غير مدرجة *كمؤقتة*. |
| `New-OrganizationSegment -Name "Segment1" -UserGroupFilter "MemberOf -eq 'group1@contoso.com'' -and MemberOf -ne 'group3@contoso.com'"`| في هذا المثال، قمنا بتعريف مقطع يسمى *المقطع 1* الذي يتضمن الأشخاص الأعضاء في group1@contoso.com وليس أعضاء group3@contoso.com. |
| `New-OrganizationSegment -Name "Segment2" -UserGroupFilter "MemberOf -eq 'group2@contoso.com' -or MemberOf -ne 'group3@contoso.com'"` | في هذا المثال، قمنا بتعريف مقطع يسمى *المقطع 2* الذي يتضمن الأشخاص الأعضاء في group2@contoso.com وليس أعضاء group3@contoso.com. |
| `New-OrganizationSegment -Name "Segment1and2" -UserGroupFilter "(MemberOf -eq 'group1@contoso.com' -or MemberOf -eq 'group2@contoso.com') -and MemberOf -ne 'group3@contoso.com'"`| في هذا المثال، قمنا بتعريف مقطع يسمى *المقطع 1and2* الذي يتضمن أشخاصا من أعضاء group1@contoso.com group2@contoso.com وليس أعضاء group3@contoso.com. |

> [!TIP]
> استخدم تعريفات المقطع التي تتضمن "-eq" أو "-ne" إذا أمكن ذلك. حاول عدم تعريف تعريفات الشرائح المعقدة.

## <a name="step-3-define-information-barrier-policies"></a>الخطوة 3: تعريف سياسات حاجز المعلومات

حدد ما إذا كنت بحاجة إلى منع الاتصالات بين أجزاء معينة، أو تقييد الاتصالات بجزائح معينة. وبشكل مثالي، سوف تستخدم الحد الأدنى لعدد السياسات لضمان امتثال مؤسستك للمتطلبات القانونية ومتطلبات الصناعة.

باستخدام قائمة شرائح المستخدمين ونهج حاجز المعلومات التي تريد تعريفها، حدد سيناريو، ثم اتبع الخطوات.

- [السيناريو 1: حظر الاتصالات بين الشرائح](#scenario-1-block-communications-between-segments)
- [السيناريو 2: السماح لم مقطع بالتواصل مع مقطع آخر فقط](#scenario-2-allow-a-segment-to-communicate-only-with-one-other-segment)

> [!IMPORTANT]
> **تأكد من أنك عند تحديد النهج، لا تقوم** بتعيين أكثر من نهج واحد إلى مقطع. على سبيل المثال، إذا قمت بتعريف نهج واحد لم مقطع يسمى *المبيعات*، لا تحدد نهج إضافي *للمبيعات*.<p> بالإضافة إلى ذلك، عند تحديد سياسات حاجز المعلومات، تأكد من تعيين هذه السياسات إلى حالة غير نشطة حتى تصبح جاهزا لتطبيقها. لا يؤثر تحديد (أو تحرير) النهج على المستخدمين حتى يتم تعيين هذه النهج إلى الحالة النشطة ثم تطبيقها.

(راجع [مثال: سياسات حاجز المعلومات الخاصة ب Contoso](#contosos-information-barrier-policies) في هذه المقالة.)

### <a name="scenario-1-block-communications-between-segments"></a>السيناريو 1: حظر الاتصالات بين الشرائح

عندما تريد منع الشرائح من التواصل مع بعضها البعض، يمكنك تحديد نهجين: أحدهما لكل اتجاه. ويحظر كل نهج الاتصال بطريقة واحدة فقط.

على سبيل المثال، افترض أنك تريد حظر الاتصالات بين المقطع A والمشرق ب. في هذه الحالة، يمكنك تحديد نهج يمنع المقطع A من التواصل مع المقطع ب، ثم تحديد نهج ثان لمنع المقطع ب من التواصل مع المقطع A.

1. لتعريف نهج الحظر الأول، استخدم **الأمر cmdlet New-InformationBarrierPolicy** مع المعلمة **SegmentsBlocked** .

    | بناء الجملة | مثال |
    |:--------|:----------|
    | `New-InformationBarrierPolicy -Name "policyname" -AssignedSegment "segment1name" -SegmentsBlocked "segment2name"` | `New-InformationBarrierPolicy -Name "Sales-Research" -AssignedSegment "Sales" -SegmentsBlocked "Research" -State Inactive` <p> في هذا المثال، قمنا بتعريف نهج يسمى *Sales-Research* لم مقطع يسمى *المبيعات*. عندما يكون نشطا ومطبقا، يمنع هذا النهج الأشخاص في *المبيعات* من التواصل مع أشخاص في مقطع يسمى *أبحاث*. |

2. لتعريف مقطع الحظر الثاني، استخدم الأمر **cmdlet New-InformationBarrierPolicy** مع المعلمة **SegmentsBlocked** مرة أخرى، هذه المرة مع عكس الشرائح.

    | مثال | ملاحظة |
    |:----------|:-------|
    |`New-InformationBarrierPolicy -Name "Research-Sales" -AssignedSegment "Research" -SegmentsBlocked "Sales" -State Inactive` | في هذا المثال، قمنا بتعريف نهج يسمى *أبحاث المبيعات* لمنع *الأبحاث* من الاتصال *بالمبيعات*. |

3. تابع إلى أحد الإجراءات التالية:

   - (إذا لزم الأمر) [تعريف نهج للسماح لم مقطع بالتواصل مع مقطع آخر فقط](#scenario-2-allow-a-segment-to-communicate-only-with-one-other-segment) 
   - (بعد تعريف كل سياساتك) [تطبيق سياسات حاجز المعلومات](#step-4-apply-information-barrier-policies)

### <a name="scenario-2-allow-a-segment-to-communicate-only-with-one-other-segment"></a>السيناريو 2: السماح لم مقطع بالتواصل مع مقطع آخر فقط

1. للسماح لم مقطع واحد بالتواصل مع مقطع واحد فقط، استخدم **الأمر cmdlet New-InformationBarrierPolicy** مع المعلمة **SegmentsAllowed** .

    | بناء الجملة | مثال |
    |:----------|:----------|
    | `New-InformationBarrierPolicy -Name "policyname" -AssignedSegment "segment1name" -SegmentsAllowed "segment2name","segment1name"` | `New-InformationBarrierPolicy -Name "Manufacturing-HR" -AssignedSegment "Manufacturing" -SegmentsAllowed "HR","Manufacturing" -State Inactive` <p> في هذا المثال، قمنا بتعريف نهج يسمى *التصنيع-الموارد البشرية* لم مقطع يسمى *التصنيع*. عندما يكون نشطا ومطبقا، يسمح هذا  النهج للأشخاص في مجال التصنيع بالتواصل فقط مع الأشخاص في مقطع يسمى *الموارد البشرية*. (في هذه الحالة، *لا يمكن للتصنيع* التواصل مع المستخدمين الذين ليسوا جزءا من *الموارد البشرية*.) |

    **إذا لزم الأمر، يمكنك تحديد عدة شرائح باستخدام الأمر cmdlet هذا، كما هو موضح في المثال التالي.**

    | بناء الجملة | مثال |
    |:---------|:----------|
    | `New-InformationBarrierPolicy -Name "policyname" -AssignedSegment "segment1name" -SegmentsAllowed "segment2name", "segment3name","segment1name"` | `New-InformationBarrierPolicy -Name "Research-HRManufacturing" -AssignedSegment "Research" -SegmentsAllowed "HR","Manufacturing","Research" -State Inactive` <p> في هذا المثال، قمنا بتعريف نهج يسمح لمشرق  الأبحاث بالتواصل مع الموارد *البشرية* *والتصنيع فقط*. |

    كرر هذه الخطوة لكل نهج تريد تعريفه للسماح لشرائح معينة بالتواصل مع بعض الشرائح المحددة الأخرى فقط.

2. تابع إلى أحد الإجراءات التالية:

   - (إذا لزم الأمر) [تعريف نهج لحظر الاتصالات بين الشرائح](#scenario-1-block-communications-between-segments) 
   - (بعد تعريف كل سياساتك) [تطبيق سياسات حاجز المعلومات](#step-4-apply-information-barrier-policies)

## <a name="step-4-apply-information-barrier-policies"></a>الخطوة 4: تطبيق سياسات حاجز المعلومات

لن تكون سياسات حاجز المعلومات فعالة إلا بعد تعيينها إلى الحالة النشطة، ثم تطبيق هذه النهج.

1. استخدم **الأمر cmdlet Get-InformationBarrierPolicy** لرؤية قائمة ب والسياسات التي تم تعريفها. لاحظ حالة كل نهج وهويته (GUID).

    بناء الجملة: `Get-InformationBarrierPolicy`

2. لتعيين نهج إلى الحالة النشطة، استخدم الأمر **Cmdlet Set-InformationBarrierPolicy** مع معلمة الهوية، ومعاينة الحالة  إلى **نشط**. 

    | بناء الجملة | مثال |
    |:---------|:----------|
    | `Set-InformationBarrierPolicy -Identity GUID -State Active` | `Set-InformationBarrierPolicy -Identity 43c37853-ea10-4b90-a23d-ab8c93772471 -State Active` <p> في هذا المثال، نقوم بتعيين نهج حاجز المعلومات الذي لديه GUID *43c37853-ea10-4b90-a23d-ab8c93772471* إلى الحالة النشطة. |

    كرر هذه الخطوة بالشكل المناسب لكل نهج.

3. عند الانتهاء من تعيين سياسات حاجز المعلومات إلى الحالة النشطة، استخدم الأمر **cmdlet Start-InformationBarrierPoliciesApplication** في مركز التوافق & الأمان.

    بناء الجملة: `Start-InformationBarrierPoliciesApplication`

    بعد تشغيل `Start-InformationBarrierPoliciesApplication`، اسمح للنظام ب 30 دقيقة لبدء تطبيق هذه السياسات. يطبق النظام سياسات المستخدم حسب المستخدم. يقوم النظام بمعالجة حوالي 5000 حساب مستخدم في الساعة.

### <a name="view-status-of-user-accounts-segments-policies-or-policy-application"></a>عرض حالة حسابات المستخدمين أو الشرائح أو النهج أو تطبيق النهج

باستخدام PowerShell، يمكنك عرض حالة حسابات المستخدمين والشرائح والسياسات وتطبيق النهج، كما هو مذكور في الجدول التالي.

| لعرض هذه المعلومات | اتخاذ هذا الإجراء |
|:---------------|:----------|
| حسابات المستخدمين | استخدم **الأمر Cmdlet Get-InformationBarrierRecipientStatus** مع معلمات الهوية. <p> بناء الجملة: `Get-InformationBarrierRecipientStatus -Identity <value> -Identity2 <value>` <p> يمكنك استخدام أي قيمة تعرف كل مستخدم بشكل فريد، مثل الاسم أو الاسم المستعار أو الاسم المميز أو اسم المجال الماجد أو عنوان البريد الإلكتروني أو GUID. <p> على سبيل المثال:`Get-InformationBarrierRecipientStatus -Identity meganb -Identity2 alexw` <p> في هذا المثال، نشير إلى حسابي مستخدم في Office 365: *ميغان* و *alexw* ل *Alex*. <p> (يمكنك أيضا استخدام الأمر cmdlet هذا لمستخدم واحد: `Get-InformationBarrierRecipientStatus -Identity <value>`) <p> ترجع cmdlet هذه معلومات حول المستخدمين، مثل قيم السمات وأي سياسات حاجز معلومات يتم تطبيقها.|
| الشرائح | استخدم **الأمر Cmdlet Get-OrganizationSegment** .<p> بناء الجملة: `Get-OrganizationSegment` <p> سيعرض cmdlet هذا قائمة بكل الشرائح المعرفة لمنظمتك. |
| سياسات حاجز المعلومات | استخدم **الأمر cmdlet Get-InformationBarrierPolicy** . <p> بناء الجملة: `Get-InformationBarrierPolicy` <p> سيعرض cmdlet هذا قائمة من سياسات حاجز المعلومات التي تم تعريفها، ووضعها. |
| تطبيق نهج حاجز المعلومات الأخير | استخدم **الأمر cmdlet Get-InformationBarrierPoliciesApplicationStatus** . <p> بناء الجملة: `Get-InformationBarrierPoliciesApplicationStatus`<p> سيعرض أمر cmdlet هذا معلومات حول ما إذا كان تطبيق النهج مكتملا أو فشل أو في وضع التقدم. |
| جميع تطبيقات نهج حاجز المعلومات|استخدام `Get-InformationBarrierPoliciesApplicationStatus -All`<p> سيعرض أمر cmdlet هذا معلومات حول ما إذا كان تطبيق النهج مكتملا أو فشل أو في وضع التقدم.|

<!-- IN the " The most recent information barrier policy application, add link to troubleshooting topic -->

### <a name="what-if-i-need-to-remove-or-change-policies"></a>ماذا لو احتجت إلى إزالة أو تغيير السياسات؟

تتوفر الموارد لمساعدتك على إدارة سياسات حاجز المعلومات.

- إذا حدث خطأ ما في حواجز المعلومات، فشاهد استكشاف مشاكل المعلومات [وإصلاحها](/office365/troubleshoot/information-barriers/information-barriers-troubleshooting).
- لمنع تطبيق النهج، راجع [إيقاف تطبيق نهج](information-barriers-edit-segments-policies.md#stop-a-policy-application).
- لإزالة نهج حاجز المعلومات، راجع [إزالة نهج](information-barriers-edit-segments-policies.md#remove-a-policy).
- بإجراء تغييرات على الشرائح أو السياسات، راجع [تحرير (أو إزالة) سياسات حاجز المعلومات](information-barriers-edit-segments-policies.md).

## <a name="step-5-configuration-for-information-barriers-on-sharepoint-and-onedrive"></a>الخطوة 5: تكوين عوائق المعلومات على SharePoint OneDrive

إذا كنت تقوم بتكوين حواجز المعلومات SharePoint OneDrive، ستحتاج إلى تمكين حواجز المعلومات على هذه الخدمات. ستحتاج أيضا إلى تمكين حواجز المعلومات على هذه الخدمات إذا كنت تقوم بتكوين حواجز المعلومات Microsoft Teams. عند إنشاء Microsoft Teams، يتم إنشاء موقع SharePoint تلقائيا وإقترن مع Microsoft Teams لتجربة الملفات. لا يتم احترام سياسات حاجز المعلومات على هذه SharePoint والملفات بشكل افتراضي.

لتمكين حواجز المعلومات في SharePoint OneDrive، اتبع الإرشادات والخطوات الواردة في المقالة استخدام [SharePoint المعلومات.](/sharepoint/information-barriers)

## <a name="step-6-information-barriers-modes"></a>الخطوة 6: أوضاع حواجز المعلومات

يمكن أن تساعد الأوضاع على تعزيز الوصول إلى مورد Microsoft 365 ومشاركته وعضوية المورد استنادا إلى وضع IB الخاص بالموارد. يتم دعم الأوضاع على Microsoft 365 ومجموعات Microsoft Teams OneDrive ومواقع SharePoint، كما يتم تمكينها تلقائيا في تكوين IB الجديد أو الموجود.

يتم دعم أوضاع IB التالية Microsoft 365 الموارد:

| **الوضع** | **الوصف** | **مثال** |
|:-----|:------------|:--------|
| **فتح** | لا توجد أي سياسات أو شرائح IB مقترنة Microsoft 365 الموارد. يمكن دعوة أي شخص لكي يكون عضوا في المورد. | موقع فريق تم إنشاؤه لحدث تنزه لمنظمتك. |
| **مالك معاد (معاينة)** | يتم تحديد نهج IB للمورد Microsoft 365 من نهج IB لمالك المورد. يمكن لمالكي الموارد دعوة أي مستخدم إلى المورد استنادا إلى سياسات IB الخاصة بهم. يكون هذا الوضع مفيدا عندما تريد شركتك السماح بالتعاون بين مستخدمي الشرائح غير المتوافقة الذين يديرهم المالك. يمكن لمالك المورد فقط إضافة أعضاء جدد لكل نهج IB. | يريد نائب رئيس قسم الموارد البشرية التعاون في العمل مع VPs للمبيعات والأبحاث. موقع جديد SharePoint تم تعيينه باستخدام وضع IB يتم ادارته من  قبل مالك لإضافة مستخدمي قسم المبيعات و الأبحاث إلى الموقع نفسه. تقع على عاتق المالك مسؤولية ضمان إضافة الأعضاء المناسبين إلى المورد. |
| **ضمني** | يتم توارث نهج IB أو Microsoft 365 الموارد من نهج IB لأعضاء الموارد. يمكن للمالك إضافة أعضاء طالما أنهم متوافقون مع الأعضاء  الموجودون في المورد. هذا هو وضع IB الافتراضي Microsoft Teams. | ينشئ مستخدم مقطع المبيعات فريق Microsoft Teams للتعاون في العمل مع الشرائح المتوافقة الأخرى في المؤسسة. |
| **صريح** | نهج IB للمورد Microsoft 365 وفقا للشرائح المقترنة بالمورد. يمكن لمالك المورد SharePoint مسؤول الموارد إدارة الشرائح على المورد.  | موقع تم إنشاؤه فقط لأعضاء مقطع المبيعات للتعاون في العمل من خلال ربط مقطع المبيعات بالموقع.   |

لمزيد من المعلومات حول أوضاع حاجز المعلومات وكيفية تكوينها عبر الخدمات، راجع المقالات التالية:

- [أوضاع وعوائق المعلومات Microsoft Teams](/microsoftteams/information-barriers-in-teams)
- [أوضاع وعوائق المعلومات OneDrive](/onedrive/information-barriers)
- [أوضاع حواجز المعلومات SharePoint](/sharepoint/information-barriers)

## <a name="example-scenario-contosos-departments-segments-and-policies"></a>سيناريو المثال: أقسام Contoso وشرائحه ونهجه

لمعرفة كيفية اقتراب المؤسسة من تحديد الشرائح والسياسات، يجب عليك التفكير في سيناريو المثال التالي.

### <a name="contosos-departments-and-plan"></a>أقسام Contoso وخططه

شركة Contoso لديها خمسة أقسام: الموارد البشرية والمبيعات والتسويق والأبحاث والتصنيع. لكي يظل الأشخاص في بعض الأقسام متوافقين مع لوائح الصناعة، لا يفترض أن يتصلوا بأقسام أخرى، كما هو مذكور في الجدول التالي:

| مقطع | يمكن التحدث إلى | لا يمكن التحدث إلى |
|:----------|:--------------|:-----------------|
| الموارد البشرية | الجميع | (بدون قيود) |
| المبيعات | الموارد البشرية والتسويق والتصنيع | أبحاث |
| التسويق | الجميع | (بدون قيود) |
| أبحاث | الموارد البشرية والتسويق والتصنيع | المبيعات |
| التصنيع | الموارد البشرية والتسويق | أي شخص غير الموارد البشرية أو التسويق |

بالنسبة إلى هذه البنية، تتضمن خطة Contoso ثلاثة سياسات لعوائق المعلومات:

1. نهج تم تصميمه لمنع "المبيعات" من التواصل مع "الأبحاث" (ون نهج آخر لمنع "الأبحاث" من التواصل مع "المبيعات").

2. نهج مصمم للسماح للتصنيع بالتواصل مع الموارد البشرية والتسويق فقط.

بالنسبة لهذا السيناريو، ليس من الضروري تعريف سياسات الموارد البشرية أو التسويق.

### <a name="contosos-defined-segments"></a>شرائح Contoso المعرفة

سيستخدم Contoso السمة "القسم" في Azure Active Directory لتعريف الشرائح، كما يلي:

| القسم | تعريف المقطع |
|:-------------|:---------------------|
| الموارد البشرية | `New-OrganizationSegment -Name "HR" -UserGroupFilter "Department -eq 'HR'"` |
| المبيعات | `New-OrganizationSegment -Name "Sales" -UserGroupFilter "Department -eq 'Sales'"` |
| التسويق | `New-OrganizationSegment -Name "Marketing" -UserGroupFilter "Department -eq 'Marketing'"` |
| أبحاث | `New-OrganizationSegment -Name "Research" -UserGroupFilter "Department -eq 'Research'"` |
| التصنيع | `New-OrganizationSegment -Name "Manufacturing" -UserGroupFilter "Department -eq 'Manufacturing'"` |

مع تحديد الشرائح، سيتابع Contoso تعريف السياسات.

### <a name="contosos-information-barrier-policies"></a>سياسات حاجز المعلومات في Contoso

تحدد Contoso ثلاثة سياسات، كما هو موضح في الجدول التالي:

| النهج | تعريف النهج |
|:---------|:--------------------|
| **النهج 1: منع المبيعات من التواصل مع الأبحاث** | `New-InformationBarrierPolicy -Name "Sales-Research" -AssignedSegment "Sales" -SegmentsBlocked "Research" -State Inactive` <p> في هذا المثال، يسمى نهج حاجز المعلومات *Sales-Research*. عندما يكون هذا النهج نشطا ومطبقا، سيساعد في منع المستخدمين في مقطع المبيعات من التواصل مع المستخدمين في المقطع أبحاث. هذا النهج هو نهج في طريقة واحدة؛ لن يمنع "الأبحاث" من التواصل مع "المبيعات". لذلك، النهج 2 مطلوب. |
| **النهج 2: منع الأبحاث من التواصل مع المبيعات** | `New-InformationBarrierPolicy -Name "Research-Sales" -AssignedSegment "Research" -SegmentsBlocked "Sales" -State Inactive` <p> في هذا المثال، يسمى نهج حاجز المعلومات *"أبحاث-مبيعات*". عندما يكون هذا النهج نشطا ومطبقا، سيساعد في منع المستخدمين في المقطع أبحاث من التواصل مع المستخدمين في مقطع المبيعات. |
| **النهج 3: السماح للتصنيع بالتواصل مع الموارد البشرية والتسويق فقط** | `New-InformationBarrierPolicy -Name "Manufacturing-HRMarketing" -AssignedSegment "Manufacturing" -SegmentsAllowed "HR","Marketing","Manufacturing" -State Inactive` <p> في هذه الحالة، يسمى نهج حاجز المعلومات *التصنيع-HRMarketing*. عندما يكون هذا النهج نشطا ومطبقا، يمكن للتصنيع التواصل مع الموارد البشرية والتسويق فقط. لا يتم تقييد الموارد البشرية والتسويق من التواصل مع الشرائح الأخرى. |

باستخدام الشرائح والسياسات المعرفة، يطبق Contoso هذه النهج عن طريق تشغيل **الأمر cmdlet Start-InformationBarrierPoliciesApplication** .

عند انتهاء أمر cmdlet، يتوافق Contoso مع المتطلبات القانونية ومتطلبات الصناعة.

## <a name="resources"></a>الموارد

- [الحصول على نظرة عامة حول حواجز المعلومات](information-barriers.md)
- [تعرف على المزيد حول حواجز المعلومات في Microsoft Teams](/MicrosoftTeams/information-barriers-in-teams)
- [تعرف على المزيد حول حواجز المعلومات في SharePoint Online](/sharepoint/information-barriers)
- [تعرف على المزيد حول حواجز المعلومات في OneDrive](/onedrive/information-barriers)
