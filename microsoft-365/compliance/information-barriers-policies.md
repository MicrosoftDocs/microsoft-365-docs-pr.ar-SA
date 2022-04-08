---
title: بدء استخدام حواجز المعلومات
description: تعرف على كيفية البدء بحواجز المعلومات.
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
ms.openlocfilehash: fb6de09c0c020631f42d8f2f09cb236affb94417
ms.sourcegitcommit: 1c5f9d17a8b095cd88b23f4874539adc3ae021de
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/08/2022
ms.locfileid: "64713526"
---
# <a name="get-started-with-information-barriers"></a>بدء استخدام حواجز المعلومات

مع حواجز المعلومات، يمكنك تحديد النهج المصممة لمنع شرائح معينة من المستخدمين من التواصل مع بعضها البعض أو السماح لشرائح معينة بالاتصال فقط مع شرائح أخرى معينة. يمكن أن تساعد سياسات حاجز المعلومات مؤسستك على الحفاظ على الامتثال للمعايير واللوائح الصناعية ذات الصلة، وتجنب تضاربات الاهتمام المحتملة. لمزيد من المعلومات، راجع [التعرف على حواجز المعلومات](information-barriers.md).

تصف هذه المقالة كيفية تكوين نهج حاجز المعلومات. يتم تنفيذ العديد من الخطوات، لذا تأكد من مراجعة العملية بأكملها قبل البدء في تكوين نهج حاجز المعلومات.

> [!TIP]
> تتضمن هذه المقالة [مثالا لسيناريو](#example-scenario-contosos-departments-segments-and-policies) لمساعدتك على تخطيط نهج حاجز المعلومات وتحديدها.

## <a name="concepts"></a>المفاهيم

عند تحديد نهج لحواجز المعلومات، ستعمل مع سمات حساب المستخدم والأجزاء ونهج "الحظر" و/أو نهج "السماح" وتطبيق النهج.

- يتم تعريف سمات حساب المستخدم في Azure Active Directory (أو Exchange Online). يمكن أن تتضمن هذه السمات القسم والمسمى الوظيفي والموقع واسم الفريق وتفاصيل ملف تعريف الوظيفة الأخرى.
- المقاطع هي مجموعات من المستخدمين الذين تم تعريفهم في مركز التوافق في Microsoft 365 باستخدام **سمة حساب مستخدم** محددة. (راجع [قائمة السمات المعتمدة](information-barriers-attributes.md).)
- تحدد نهج حاجز المعلومات حدود الاتصالات أو قيودها. عند تحديد نهج حاجز المعلومات، يمكنك الاختيار من بين نوعين من النهج:
  - تمنع نهج *الحظر* مقطعا واحدا من الاتصال بمقطع آخر.
  - *السماح* للنهج بتواصل مقطع واحد مع مقاطع أخرى معينة فقط.
- يتم تطبيق النهج بعد تحديد جميع نهج حاجز المعلومات، وأنت مستعد لتطبيقها في مؤسستك.

## <a name="configuration-at-a-glance"></a>التكوين بنظرة سريعة

| **الخطوات** | **ما الذي ينطوي عليه الأمر** |
|:------|:----------------|
| **الخطوة 1**: [التأكد من استيفاء المتطلبات الأساسية](#step-1-make-sure-prerequisites-are-met) | - تحقق من أن لديك [التراخيص والأذونات المطلوبة](information-barriers.md#required-licenses-and-permissions)<br/>- تحقق من أن الدليل الخاص بك يتضمن بيانات لتقسيم المستخدمين<br/>- تمكين [البحث حسب الاسم ل Microsoft Teams](/microsoftteams/teams-scoped-directory-search)<br/>- تأكد من تشغيل تسجيل التدقيق<br/>- تأكد من عدم وجود نهج دفتر عناوين Exchange<br/>- استخدام PowerShell (تتوفر أمثلة)<br/>- توفير موافقة المسؤول على Microsoft Teams (يتم تضمين الخطوات) |
| **الخطوة 2**: [تقسيم المستخدمين في مؤسستك](#step-2-segment-users-in-your-organization) | - تحديد النهج المطلوبة<br/>- إنشاء قائمة مقاطع لتعريفها<br/>- تحديد السمات التي يجب استخدامها<br/>- تحديد المقاطع من حيث عوامل تصفية النهج |
| **الخطوة 3**: [تحديد نهج حاجز المعلومات](#step-3-define-information-barrier-policies) | - تحديد النهج الخاصة بك (لا تنطبق بعد)<br/>- اختر من نوعين (حظر أو السماح) |
| **الخطوة 4**: [تطبيق نهج حاجز المعلومات](#step-4-apply-information-barrier-policies) | - تعيين النهج إلى الحالة النشطة<br/>- تشغيل تطبيق النهج<br/>- عرض حالة النهج |
| **الخطوة 5**: [تكوين حواجز المعلومات على SharePoint OneDrive (اختياري)](#step-5-configuration-for-information-barriers-on-sharepoint-and-onedrive) | - تكوين حواجز المعلومات SharePoint OneDrive |
| **الخطوة 6**: [أوضاع حواجز المعلومات (اختيارية)](#step-6-information-barriers-modes) | - تحديث أوضاع حاجز المعلومات إذا كان ذلك ممكنا |

## <a name="step-1-make-sure-prerequisites-are-met"></a>الخطوة 1: التأكد من استيفاء المتطلبات الأساسية

بالإضافة إلى [التراخيص والأذونات المطلوبة](information-barriers.md#required-licenses-and-permissions)، تأكد من استيفاء المتطلبات التالية قبل تكوين حواجز المعلومات:

- **بيانات الدليل**: تأكد من أن بنية مؤسستك تنعكس في بيانات الدليل. لاتخاذ هذا الإجراء، تأكد من تعبئة سمات حساب المستخدم، مثل عضوية المجموعة أو اسم القسم وما إلى ذلك بشكل صحيح في Azure Active Directory (أو Exchange Online). لمعرفة المزيد، راجع الموارد التالية:
  - [سمات نهج حاجز المعلومات](information-barriers-attributes.md)
  - [إضافة معلومات ملف تعريف المستخدم أو تحديثها باستخدام Azure Active Directory](/azure/active-directory/fundamentals/active-directory-users-profile-azure-portal)
  - [تكوين خصائص حساب المستخدم باستخدام Office 365 PowerShell](../enterprise/configure-user-account-properties-with-microsoft-365-powershell.md)

- **البحث في الدليل المحدد النطاق**: قبل تحديد نهج حاجز المعلومات الأول لمؤسستك، يجب [تمكين البحث في الدليل في نطاق في Microsoft Teams](/MicrosoftTeams/teams-scoped-directory-search). انتظر 24 ساعة على الأقل بعد تمكين البحث في الدليل المحدد النطاق قبل إعداد نهج حاجز المعلومات أو تعريفها.

- **Exchange Online التراخيص**: تعمل نهج حواجز المعلومات فقط إذا تم تعيين ترخيص Exchange Online للمستخدمين المستهدفين.

- **التحقق من تمكين تسجيل التدقيق**: من أجل البحث عن حالة تطبيق نهج، يجب تشغيل تسجيل التدقيق. يتم تمكين التدقيق للمؤسسات Microsoft 365 بشكل افتراضي. قد تكون بعض المؤسسات قد عطلت التدقيق لأسباب محددة. إذا تم تعطيل التدقيق لمؤسستك، فقد يرجع ذلك إلى إيقاف تشغيل مسؤول آخر. نوصي بالتأكيد على أنه لا بأس من إعادة تشغيل التدقيق عند إكمال هذه الخطوة. لمزيد من المعلومات، راجع [تشغيل البحث في سجل التدقيق أو إيقاف تشغيله](turn-audit-log-search-on-or-off.md).

- **لا توجد نهج دفاتر العناوين**: قبل تحديد نهج حاجز المعلومات وتطبيقها، تأكد من عدم وجود نهج دفتر عناوين Exchange. تستند حواجز المعلومات إلى نهج دفتر العناوين، ولكن نوعي النهج غير متوافقين. إذا كان لديك مثل هذه النهج، فتأكد من [إزالة نهج دفتر العناوين](/exchange/address-books/address-book-policies/remove-an-address-book-policy) أولا. بمجرد تمكين نهج حاجز المعلومات وتمكين دفتر العناوين الهرمي، سيتمكن جميع المستخدمين **_غير المضمنين_** في مقطع حاجز المعلومات من رؤية [دفتر العناوين الهرمي](/exchange/address-books/hierarchical-address-books/hierarchical-address-books) في Exchange عبر الإنترنت.

- **إدارة استخدام PowerShell**: حاليا، يتم تحديد نهج حاجز المعلومات وإدارتها في Security & Compliance Center PowerShell. على الرغم من توفير العديد من الأمثلة في هذه المقالة، ستحتاج إلى أن تكون على دراية ب PowerShell cmdlets والمعلمات. ستحتاج أيضا إلى وحدة Azure Active Directory PowerShell.
  - [الاتصال إلى Security & Compliance Center PowerShell](/powershell/exchange/connect-to-scc-powershell)
  - [تثبيت Azure Active Directory PowerShell ل Graph](/powershell/azure/active-directory/install-adv2)

- **موافقة المسؤول على حواجز المعلومات في Microsoft Teams**: عند تطبيق نهج IB، يمكنهم إزالة المستخدمين غير المتوافقين مع IB من المجموعات (على سبيل المثال، قنوات Teams، التي تستند إلى مجموعات). يساعد هذا التكوين على ضمان بقاء مؤسستك متوافقة مع السياسات واللوائح. استخدم الإجراء التالي لتمكين نهج حاجز المعلومات من العمل كما هو متوقع في Microsoft Teams.

   1. المتطلبات الأساسية: [تثبيت Azure Active Directory PowerShell Graph](/powershell/azure/active-directory/install-adv2).

   1. تشغيل أوامر PowerShell cmdlets التالية:

      ```powershell
      Connect-AzureAD -Tenant "<yourtenantdomain.com>"  //for example: Connect-AzureAD -Tenant "Contoso.onmicrosoft.com"
      $appId="bcf62038-e005-436d-b970-2a472f8c1982" 
      $sp=Get-AzureADServicePrincipal -Filter "appid eq '$($appid)'"
      if ($sp -eq $null) { New-AzureADServicePrincipal -AppId $appId }
      Start-Process  "https://login.microsoftonline.com/common/adminconsent?client_id=$appId"
      ```

   1. عند مطالبتك، سجل الدخول باستخدام حساب العمل أو المؤسسة التعليمية Office 365.

   1. في مربع الحوار " **الأذونات المطلوبة** "، راجع المعلومات، ثم اختر **"قبول**". يتم توفير الأذونات التي يطلبها التطبيق أدناه.

      > [!div class="mx-imgBorder"]
      > ![الصوره.](https://user-images.githubusercontent.com/8932063/107690955-b1772300-6c5f-11eb-9527-4235de860b27.png)

عند استيفاء جميع المتطلبات الأساسية، انتقل إلى الخطوة التالية.

> [!TIP]
> لمساعدتك على إعداد خطتك، يتم تضمين سيناريو مثال في هذه المقالة. [راجع أقسام Contoso وأجزاءها وسياساتها](#example-scenario-contosos-departments-segments-and-policies).

## <a name="step-2-segment-users-in-your-organization"></a>الخطوة 2: تقسيم المستخدمين في مؤسستك

خلال هذه الخطوة، يمكنك تحديد نهج حاجز المعلومات المطلوبة، وإنشاء قائمة بالشرائح لتعريفها، ثم تحديد المقاطع الخاصة بك.

### <a name="determine-what-policies-are-needed"></a>تحديد النهج المطلوبة

بالنظر إلى اللوائح القانونية والصناعية، من هم المجموعات داخل مؤسستك التي ستحتاج إلى سياسات حاجز المعلومات؟ إنشاء قائمة. هل هناك أي مجموعات يجب منعها من التواصل مع مجموعة أخرى؟ هل هناك أي مجموعات يجب السماح لها بالاتصال بمجموعتين أو مجموعتين آخرين فقط؟ فكر في النهج التي تحتاجها على أنها تنتمي إلى إحدى المجموعتين:

- تمنع نهج "الحظر" مجموعة واحدة من الاتصال بمجموعة أخرى.
- تسمح نهج "السماح" للمجموعة بالاتصال بمجموعات معينة أخرى فقط.

عندما يكون لديك قائمة أولية بالمجموعات والنهج، تابع لتحديد الشرائح التي ستحتاج إليها.

### <a name="identify-segments"></a>تحديد المقاطع

بالإضافة إلى قائمة النهج الأولية، قم بإنشاء قائمة مقاطع لمؤسستك. يجب أن ينتمي المستخدمون الذين سيتم تضمينهم في نهج حاجز المعلومات إلى مقطع. التخطيط لأجزاءك بعناية كمستخدم يمكن أن يكون في مقطع واحد فقط. يمكن أن يكون لكل مقطع نهج حاجز معلومات واحد فقط مطبق.

> [!IMPORTANT]
> يمكن أن يكون المستخدم في مقطع واحد فقط.

حدد السمات في بيانات الدليل الخاصة بالمؤسسة التي ستستخدمها لتعريف المقاطع. يمكنك استخدام *القسم* أو *العضو* أو أي من السمات المدعومة. تأكد من وجود قيم في السمة التي تحددها للمستخدمين. [راجع قائمة السمات المدعومة لحواجز المعلومات](information-barriers-attributes.md).

> [!IMPORTANT]
> **قبل المتابعة إلى المقطع التالي، تأكد من أن بيانات الدليل تحتوي على قيم للسمات التي يمكنك استخدامها لتعريف المقاطع**. إذا لم تتضمن بيانات الدليل قيما للسمات التي تريد استخدامها، فيجب تحديث حسابات المستخدمين لتضمين تلك المعلومات قبل المتابعة مع حواجز المعلومات. للحصول على مساعدة في هذا الأمر، راجع الموارد التالية:<br/>- [تكوين خصائص حساب المستخدم باستخدام Office 365 PowerShell](../enterprise/configure-user-account-properties-with-microsoft-365-powershell.md)<br/>- [إضافة معلومات ملف تعريف المستخدم أو تحديثها باستخدام Azure Active Directory](/azure/active-directory/fundamentals/active-directory-users-profile-azure-portal)

### <a name="define-segments-using-powershell"></a>تعريف المقاطع باستخدام PowerShell

لا يؤثر تعريف المقاطع على المستخدمين؛ إنها تضبط فقط مرحلة تعريف نهج حاجز المعلومات ثم تطبيقها.

1. استخدم **new-OrganizationSegment** cmdlet مع معلمة **UserGroupFilter** التي تتوافق مع [السمة](information-barriers-attributes.md) التي تريد استخدامها.

    | بناء الجمله | المثال |
    |:---------|:----------|
    | `New-OrganizationSegment -Name "segmentname" -UserGroupFilter "attribute -eq 'attributevalue'"` |`New-OrganizationSegment -Name "HR" -UserGroupFilter "Department -eq 'HR'"` <p>في هذا المثال، يتم تعريف مقطع يسمى *HR* باستخدام *HR*، وهي قيمة في سمة *القسم* . يشير جزء **-eq** من cmdlet إلى "يساوي". (بدلا من ذلك، يمكنك استخدام **-ne** لتعني "not equals". راجع [استخدام "يساوي" و"لا يساوي" في تعريفات المقطع](#using-equals-and-not-equals-in-segment-definitions).) |

    بعد تشغيل كل cmdlet، يجب أن تشاهد قائمة بالتفاصيل حول المقطع الجديد. تتضمن التفاصيل نوع المقطع، ومن قام بإنشائه أو آخر تعديل له، وما إلى ذلك. 

2. كرر هذه العملية لكل مقطع تريد تعريفه.

    > [!IMPORTANT]
    > **تأكد من عدم تداخل المقاطع**. يجب أن ينتمي كل مستخدم سيتأثر بحواجز المعلومات إلى مقطع واحد (وواحد فقط). يجب ألا ينتمي أي مستخدم إلى مقطعين أو أكثر. (راجع [المثال: مقاطع Contoso المعرفة](#contosos-defined-segments) في هذه المقالة.)

بعد تحديد المقاطع الخاصة بك، تابع [لتعريف نهج حاجز المعلومات](#step-3-define-information-barrier-policies).

### <a name="using-equals-and-not-equals-in-segment-definitions"></a>استخدام "يساوي" و"لا يساوي" في تعريفات المقاطع

في المثال التالي، نقوم بتعريف مقطع مثل "القسم يساوي الموارد البشرية". 

| المثال | ملاحظه |
|:----------|:-------|
|`New-OrganizationSegment -Name "HR" -UserGroupFilter "Department -eq 'HR'"` | لاحظ أنه في هذا المثال، يتضمن تعريف المقطع معلمة "يساوي" تشير إلى **أنها -eq**. |

يمكنك أيضا تعريف المقاطع باستخدام معلمة "not equals"، والموضحة باسم **-ne**، كما هو موضح في الجدول التالي:

| بناء الجمله | المثال |
|:---------|:----------|
| `New-OrganizationSegment -Name "NotSales" -UserGroupFilter "Department -ne 'Sales'"` | في هذا المثال، حددنا مقطعا يسمى *NotSales* يتضمن كل الأشخاص غير الموجودين في *المبيعات*. يشير الجزء **-ne** من cmdlet إلى "not equals". |

بالإضافة إلى تعريف المقاطع باستخدام "يساوي" أو "لا يساوي"، يمكنك تعريف مقطع باستخدام معلمات "يساوي" و"لا يساوي". يمكنك أيضا تعريف عوامل تصفية المجموعة المعقدة باستخدام عوامل *التشغيل AND* *وOR* المنطقية.

| بناء الجمله | المثال |
|:---------|:----------|
| `New-OrganizationSegment -Name "LocalFTE" -UserGroupFilter "Location -eq 'Local'" -and "Position -ne 'Temporary'"` | في هذا المثال، حددنا مقطعا يسمى *LocalFTE* يتضمن الأشخاص الموجودين محليا والذين لم يتم إدراج مواضعهم ك *"مؤقت*". |
| `New-OrganizationSegment -Name "Segment1" -UserGroupFilter "MemberOf -eq 'group1@contoso.com'' -and MemberOf -ne 'group3@contoso.com'"`| في هذا المثال، حددنا مقطعا يسمى *Segment1* يتضمن الأشخاص الأعضاء في group1@contoso.com وليس أعضاء group3@contoso.com. |
| `New-OrganizationSegment -Name "Segment2" -UserGroupFilter "MemberOf -eq 'group2@contoso.com' -or MemberOf -ne 'group3@contoso.com'"` | في هذا المثال، حددنا مقطعا يسمى *Segment2* يتضمن الأشخاص الأعضاء في group2@contoso.com وليس أعضاء group3@contoso.com. |
| `New-OrganizationSegment -Name "Segment1and2" -UserGroupFilter "(MemberOf -eq 'group1@contoso.com' -or MemberOf -eq 'group2@contoso.com') -and MemberOf -ne 'group3@contoso.com'"`| في هذا المثال، حددنا مقطعا يسمى *Segment1and2* يتضمن أعضاء group1@contoso.com group2@contoso.com وليس أعضاء group3@contoso.com. |

> [!TIP]
> إذا كان ذلك ممكنا، فاستخدم تعريفات المقاطع التي تتضمن "-eq" أو "-ne". حاول عدم تعريف تعريفات المقاطع المعقدة.

## <a name="step-3-define-information-barrier-policies"></a>الخطوة 3: تحديد نهج حاجز المعلومات

حدد ما إذا كنت بحاجة إلى منع الاتصالات بين مقاطع معينة، أو قصر الاتصالات على مقاطع معينة. وبشكل مثالي، ستستخدم الحد الأدنى من النهج لضمان توافق مؤسستك مع المتطلبات القانونية ومتطلبات الصناعة.

مع قائمة مقاطع المستخدم ونهج حاجز المعلومات التي تريد تحديدها، حدد سيناريو، ثم اتبع الخطوات.

- [السيناريو 1: حظر الاتصالات بين المقاطع](#scenario-1-block-communications-between-segments)
- [السيناريو 2: السماح لمقطع بالاتصال بمقطع واحد فقط](#scenario-2-allow-a-segment-to-communicate-only-with-one-other-segment)

> [!IMPORTANT]
> **تأكد من أنه أثناء تحديد النهج، لا تقوم بتعيين أكثر من نهج واحد إلى مقطع**. على سبيل المثال، إذا قمت بتعريف نهج واحد لمقطع يسمى *Sales*، فلا تحدد نهجا إضافيا *للمبيعات*.<p> بالإضافة إلى ذلك، أثناء تحديد نهج حاجز المعلومات، تأكد من تعيين هذه النهج إلى حالة غير نشطة حتى تصبح جاهزا لتطبيقها. لا يؤثر تعريف (أو تحرير) النهج على المستخدمين حتى يتم تعيين هذه النهج إلى الحالة النشطة ثم تطبيقها.

(راجع [المثال: نهج حاجز المعلومات لشركة Contoso](#contosos-information-barrier-policies) في هذه المقالة.)

### <a name="scenario-1-block-communications-between-segments"></a>السيناريو 1: حظر الاتصالات بين المقاطع

عندما تريد منع المقاطع من التواصل مع بعضها البعض، يمكنك تحديد نهجين: نهج لكل اتجاه. يحظر كل نهج الاتصال في اتجاه واحد فقط.

على سبيل المثال، افترض أنك تريد حظر الاتصالات بين المقطع A والمقطع B. في هذه الحالة، يمكنك تحديد نهج واحد يمنع المقطع A من الاتصال بالمقطع B، ثم تحدد نهجا ثانيا لمنع المقطع B من الاتصال بالمقطع A.

1. لتحديد نهج الحظر الأول، استخدم **New-InformationBarrierPolicy** cmdlet مع المعلمة **SegmentsBlocked** .

    | بناء الجمله | المثال |
    |:--------|:----------|
    | `New-InformationBarrierPolicy -Name "policyname" -AssignedSegment "segment1name" -SegmentsBlocked "segment2name"` | `New-InformationBarrierPolicy -Name "Sales-Research" -AssignedSegment "Sales" -SegmentsBlocked "Research" -State Inactive` <p> في هذا المثال، حددنا نهجا يسمى *Sales-Research* لجزء يسمى *Sales*. عند تنشيط هذا النهج وتطبيقه، يمنع الأشخاص في *"المبيعات"* من التواصل مع أشخاص في مقطع يسمى *"أبحاث*". |

2. لتعريف مقطع الحظر الثاني، استخدم **New-InformationBarrierPolicy** cmdlet مع **المعلمة SegmentsBlocked** مرة أخرى، هذه المرة مع عكس المقاطع.

    | المثال | ملاحظه |
    |:----------|:-------|
    |`New-InformationBarrierPolicy -Name "Research-Sales" -AssignedSegment "Research" -SegmentsBlocked "Sales" -State Inactive` | في هذا المثال، حددنا نهجا يسمى *Research-Sales* لمنع *الأبحاث* من التواصل مع *المبيعات*. |

3. تابع إلى أحد الإجراءات التالية:

   - (إذا لزم الأمر) [تعريف نهج للسماح لمقطع بالاتصال بمقطع واحد فقط](#scenario-2-allow-a-segment-to-communicate-only-with-one-other-segment) 
   - (بعد تحديد جميع النهج الخاصة بك) [تطبيق نهج حاجز المعلومات](#step-4-apply-information-barrier-policies)

### <a name="scenario-2-allow-a-segment-to-communicate-only-with-one-other-segment"></a>السيناريو 2: السماح لمقطع بالاتصال بمقطع واحد فقط

1. للسماح لمقطع واحد بالاتصال بمقطع واحد فقط، استخدم **New-InformationBarrierPolicy** cmdlet مع المعلمة **SegmentsAllowed** .

    | بناء الجمله | المثال |
    |:----------|:----------|
    | `New-InformationBarrierPolicy -Name "policyname" -AssignedSegment "segment1name" -SegmentsAllowed "segment2name","segment1name"` | `New-InformationBarrierPolicy -Name "Manufacturing-HR" -AssignedSegment "Manufacturing" -SegmentsAllowed "HR","Manufacturing" -State Inactive` <p> في هذا المثال، حددنا نهجا يسمى *Manufacturing-HR* لمقطع يسمى *التصنيع*. عند تنشيطه وتطبيقه، يسمح هذا النهج للأشخاص في *التصنيع* بالاتصال فقط مع الأشخاص في مقطع يسمى *الموارد البشرية*. (في هذه *الحالة، يتعذر على التصنيع* الاتصال بالمستخدمين الذين ليسوا جزءا من *الموارد البشرية*.) |

    **إذا لزم الأمر، يمكنك تحديد مقاطع متعددة باستخدام أمر cmdlet هذا، كما هو موضح في المثال التالي.**

    | بناء الجمله | المثال |
    |:---------|:----------|
    | `New-InformationBarrierPolicy -Name "policyname" -AssignedSegment "segment1name" -SegmentsAllowed "segment2name", "segment3name","segment1name"` | `New-InformationBarrierPolicy -Name "Research-HRManufacturing" -AssignedSegment "Research" -SegmentsAllowed "HR","Manufacturing","Research" -State Inactive` <p> في هذا المثال، حددنا نهجا يسمح لقسم *الأبحاث* بالاتصال *بالموارد البشرية* *والتصنيع* فقط. |

    كرر هذه الخطوة لكل نهج تريد تعريفه للسماح لمقاطع معينة بالاتصال ببعض المقاطع المحددة الأخرى فقط.

2. تابع إلى أحد الإجراءات التالية:

   - (إذا لزم الأمر) [تعريف نهج لحظر الاتصالات بين المقاطع](#scenario-1-block-communications-between-segments) 
   - (بعد تحديد جميع النهج الخاصة بك) [تطبيق نهج حاجز المعلومات](#step-4-apply-information-barrier-policies)

## <a name="step-4-apply-information-barrier-policies"></a>الخطوة 4: تطبيق نهج حاجز المعلومات

لا تكون نهج حاجز المعلومات سارية حتى تقوم بتعيينها إلى الحالة النشطة، ثم تطبق النهج.

1. استخدم **Get-InformationBarrierPolicy** cmdlet لمشاهدة قائمة النهج التي تم تعريفها. لاحظ الحالة والهوية (GUID) لكل نهج.

    بناء الجمله: `Get-InformationBarrierPolicy`

2. لتعيين نهج إلى الحالة النشطة، استخدم **Set-InformationBarrierPolicy** cmdlet مع معلمة **Identity** ، وتعيين معلمة **الحالة** إلى **Active**. 

    | بناء الجمله | المثال |
    |:---------|:----------|
    | `Set-InformationBarrierPolicy -Identity GUID -State Active` | `Set-InformationBarrierPolicy -Identity 43c37853-ea10-4b90-a23d-ab8c93772471 -State Active` <p> في هذا المثال، قمنا بتعيين نهج حاجز المعلومات الذي يحتوي على GUID *43c37853-ea10-4b90-a23d-ab8c93772471* إلى الحالة النشطة. |

    كرر هذه الخطوة حسب الاقتضاء لكل نهج.

3. عند الانتهاء من تعيين نهج حاجز المعلومات إلى الحالة النشطة، استخدم **Start-InformationBarrierPoliciesApplication** cmdlet في Security & Compliance Center.

    بناء الجمله: `Start-InformationBarrierPoliciesApplication`

    بعد التشغيل `Start-InformationBarrierPoliciesApplication`، اسمح للنظام ب 30 دقيقة لبدء تطبيق النهج. يطبق النظام نهج المستخدم حسب المستخدم. يعالج النظام حوالي 5000 حساب مستخدم في الساعة.

### <a name="view-status-of-user-accounts-segments-policies-or-policy-application"></a>عرض حالة حسابات المستخدمين أو المقاطع أو النهج أو تطبيق النهج

باستخدام PowerShell، يمكنك عرض حالة حسابات المستخدمين والمقاطع والنهج وتطبيق النهج، كما هو مذكور في الجدول التالي.

| لعرض هذه المعلومات | اتخاذ هذا الإجراء |
|:---------------|:----------|
| حسابات المستخدمين | استخدم **Get-InformationBarrierRecipientStatus** cmdlet مع معلمات الهوية. <p> بناء الجمله: `Get-InformationBarrierRecipientStatus -Identity <value> -Identity2 <value>` <p> يمكنك استخدام أي قيمة تعرف كل مستخدم بشكل فريد، مثل الاسم أو الاسم المستعار أو الاسم المميز أو اسم المجال المتعارف عليه أو عنوان البريد الإلكتروني أو GUID. <p> على سبيل المثال:`Get-InformationBarrierRecipientStatus -Identity meganb -Identity2 alexw` <p> في هذا المثال، نشير إلى حسابين للمستخدمين في Office 365: *meganb* for *Megan*، و *alexw* for *Alex*. <p> (يمكنك أيضا استخدام أمر cmdlet هذا لمستخدم واحد: `Get-InformationBarrierRecipientStatus -Identity <value>`) <p> يقوم أمر cmdlet هذا بإرجاع معلومات حول المستخدمين، مثل قيم السمات وأي نهج حاجز معلومات يتم تطبيقها.|
| قطاعات | استخدم **Get-OrganizationSegment** cmdlet.<p> بناء الجمله: `Get-OrganizationSegment` <p> سيعرض أمر cmdlet هذا قائمة بكافة المقاطع المحددة لمؤسستك. |
| نهج حاجز المعلومات | استخدم **Get-InformationBarrierPolicy** cmdlet. <p> بناء الجمله: `Get-InformationBarrierPolicy` <p> سيعرض أمر cmdlet هذا قائمة بنهج حاجز المعلومات التي تم تحديدها وحالتها. |
| أحدث تطبيق لنهج حاجز المعلومات | استخدم **Get-InformationBarrierPoliciesApplicationStatus** cmdlet. <p> بناء الجمله: `Get-InformationBarrierPoliciesApplicationStatus`<p> سيعرض أمر cmdlet هذا معلومات حول ما إذا كان تطبيق النهج مكتملا أو فاشلا أو قيد التقدم. |
| جميع تطبيقات نهج حاجز المعلومات|استخدام `Get-InformationBarrierPoliciesApplicationStatus -All`<p> سيعرض أمر cmdlet هذا معلومات حول ما إذا كان تطبيق النهج مكتملا أو فاشلا أو قيد التقدم.|

<!-- IN the " The most recent information barrier policy application, add link to troubleshooting topic -->

### <a name="what-if-i-need-to-remove-or-change-policies"></a>ماذا لو كنت بحاجة إلى إزالة النهج أو تغييرها؟

تتوفر الموارد لمساعدتك في إدارة نهج حاجز المعلومات.

- إذا حدث خطأ ما في حواجز المعلومات، فراجع [استكشاف أخطاء حواجز المعلومات وإصلاحها](/office365/troubleshoot/information-barriers/information-barriers-troubleshooting).
- لإيقاف تطبيق النهج، راجع [إيقاف تطبيق النهج](information-barriers-edit-segments-policies.md#stop-a-policy-application).
- لإزالة نهج حاجز المعلومات، راجع [إزالة نهج](information-barriers-edit-segments-policies.md#remove-a-policy).
- لإجراء تغييرات على المقاطع أو النهج، راجع [تحرير (أو إزالة) نهج حاجز المعلومات](information-barriers-edit-segments-policies.md).

## <a name="step-5-configuration-for-information-barriers-on-sharepoint-and-onedrive"></a>الخطوة 5: تكوين حواجز المعلومات على SharePoint OneDrive

إذا كنت تقوم بتكوين حواجز المعلومات SharePoint OneDrive، فستحتاج إلى تمكين حواجز المعلومات على هذه الخدمات. ستحتاج أيضا إلى تمكين حواجز المعلومات على هذه الخدمات إذا كنت تقوم بتكوين حواجز المعلومات Microsoft Teams. عند إنشاء فريق Microsoft Teams، يتم تلقائيا إنشاء موقع SharePoint وإقرانه Microsoft Teams لتجربة الملفات. لا يتم احترام نهج حاجز المعلومات على هذا الموقع SharePoint والملفات بشكل افتراضي.

لتمكين حواجز المعلومات في SharePoint OneDrive، اتبع الإرشادات والخطوات الواردة في [حواجز استخدام المعلومات مع المقالة SharePoint](/sharepoint/information-barriers).

## <a name="step-6-information-barriers-modes"></a>الخطوة 6: أوضاع حواجز المعلومات

يمكن أن تساعد الأوضاع في تعزيز الوصول والمشاركة والعضوية لمورد Microsoft 365 استنادا إلى وضع IB الخاص بالمورد. يتم دعم الأوضاع على مواقع مجموعات Microsoft 365 Microsoft Teams OneDrive SharePoint ويتم تمكينها تلقائيا في تكوين IB الجديد أو الحالي.

يتم دعم أوضاع IB التالية على موارد Microsoft 365:

| **وضع** | **الوصف** | **المثال** |
|:-----|:------------|:--------|
| **فتح** | لا توجد أي نهج أو مقاطع ل IB مقترنة بمورد Microsoft 365. يمكن دعوة أي شخص ليكون عضوا في المورد. | موقع فريق تم إنشاؤه لحدث نزهة لمؤسستك. |
| **مالك متوسط (معاينة)** | يتم تحديد نهج IB لمورد Microsoft 365 من نهج IB لمالك المورد. يمكن لمالكي الموارد دعوة أي مستخدم إلى المورد استنادا إلى نهج IB الخاصة بهم. يعد هذا الوضع مفيدا عندما تريد شركتك السماح بالتعاون بين مستخدمي الشرائح غير المتوافقين الذين يديرهم المالك. يمكن لمالك المورد فقط إضافة أعضاء جدد وفقا لنهج IB. | يريد نائب الرئيس للموارد البشرية التعاون مع أجهزة ظاهرية للمبيعات والأبحاث. موقع SharePoint جديد تم تعيينه باستخدام مالك وضع IB *الذي تم الإشراف عليه* لإضافة كل من مستخدمي قسم المبيعات والأبحاث إلى نفس الموقع. تقع على عاتق المالك مسؤولية ضمان إضافة الأعضاء المناسبين إلى المورد. |
| **الضمني** | يتم توريث نهج IB أو مقاطع مورد Microsoft 365 من نهج IB لأعضاء الموارد. يمكن للمالك إضافة أعضاء طالما أنها متوافقة مع الأعضاء الحاليين للمورد. هذا هو وضع IB الافتراضي Microsoft Teams. | ينشئ مستخدم قسم المبيعات فريق Microsoft Teams للتعاون مع الشرائح الأخرى المتوافقة في المؤسسة. |
| **صريحه** | نهج IB لمورد Microsoft 365 هو حسب الأجزاء المقترنة بالمورد. مالك المورد أو مسؤول SharePoint لديه القدرة على إدارة المقاطع على المورد.  | موقع تم إنشاؤه فقط لأعضاء مقطع المبيعات للتعاون من خلال ربط مقطع المبيعات بالموقع.   |

لمزيد من المعلومات حول أوضاع حاجز المعلومات وكيفية تكوينها عبر الخدمات، راجع المقالات التالية:

- [أوضاع حواجز المعلومات Microsoft Teams](/microsoftteams/information-barriers-in-teams)
- [أوضاع حواجز المعلومات OneDrive](/onedrive/information-barriers)
- [أوضاع حواجز المعلومات SharePoint](/sharepoint/information-barriers)

## <a name="example-scenario-contosos-departments-segments-and-policies"></a>سيناريو مثال: أقسام Contoso وأجزاءها وسياساتها

لمعرفة كيفية تعامل المؤسسة مع تحديد المقاطع والنهج، ضع في اعتبارك سيناريو المثال التالي.

### <a name="contosos-departments-and-plan"></a>أقسام Contoso وخطتها

تمتلك شركة Contoso خمسة أقسام: الموارد البشرية والمبيعات والتسويق والبحث والتصنيع. من أجل البقاء متوافقا مع اللوائح الصناعية، لا يفترض أن يتواصل الأشخاص في بعض الأقسام مع الأقسام الأخرى، كما هو مذكور في الجدول التالي:

| الجزء | يمكن التحدث إلى | لا يمكن التحدث إلى |
|:----------|:--------------|:-----------------|
| ساعه | الجميع | (بدون قيود) |
| المبيعات | الموارد البشرية والتسويق والتصنيع | أبحاث |
| التسويق | الجميع | (بدون قيود) |
| أبحاث | الموارد البشرية والتسويق والتصنيع | المبيعات |
| التصنيع | الموارد البشرية، التسويق | أي شخص آخر غير الموارد البشرية أو التسويق |

بالنسبة إلى هذه البنية، تتضمن خطة Contoso ثلاثة نهج لحواجز المعلومات:

1. نهج مصمم لمنع المبيعات من التواصل مع الأبحاث (ونهج آخر لمنع الأبحاث من التواصل مع المبيعات).

2. نهج مصمم للسماح للتسويق بالاتصال بالموارد البشرية والتسويق فقط.

بالنسبة لهذا السيناريو، ليس من الضروري تحديد نهج للموارد البشرية أو التسويق.

### <a name="contosos-defined-segments"></a>مقاطع Contoso المحددة

ستستخدم Contoso سمة القسم في Azure Active Directory لتعريف المقاطع، كما يلي:

| اداره | تعريف المقطع |
|:-------------|:---------------------|
| ساعه | `New-OrganizationSegment -Name "HR" -UserGroupFilter "Department -eq 'HR'"` |
| المبيعات | `New-OrganizationSegment -Name "Sales" -UserGroupFilter "Department -eq 'Sales'"` |
| التسويق | `New-OrganizationSegment -Name "Marketing" -UserGroupFilter "Department -eq 'Marketing'"` |
| أبحاث | `New-OrganizationSegment -Name "Research" -UserGroupFilter "Department -eq 'Research'"` |
| التصنيع | `New-OrganizationSegment -Name "Manufacturing" -UserGroupFilter "Department -eq 'Manufacturing'"` |

مع تحديد المقاطع، تستمر Contoso في تحديد النهج.

### <a name="contosos-information-barrier-policies"></a>نهج حاجز المعلومات في Contoso

تحدد شركة Contoso ثلاثة نهج، كما هو موضح في الجدول التالي:

| السياسات | تعريف النهج |
|:---------|:--------------------|
| **النهج 1: منع المبيعات من التواصل مع الأبحاث** | `New-InformationBarrierPolicy -Name "Sales-Research" -AssignedSegment "Sales" -SegmentsBlocked "Research" -State Inactive` <p> في هذا المثال، يسمى نهج حاجز المعلومات *Sales-Research*. عندما يكون هذا النهج نشطا ومطبقا، سيساعد على منع المستخدمين الموجودين في مقطع المبيعات من الاتصال بالمستخدمين في الجزء "أبحاث". هذا النهج هو نهج أحادي الاتجاه؛ لن يمنع Research من التواصل مع Sales. لذلك، هناك حاجة إلى النهج 2. |
| **النهج 2: منع الأبحاث من التواصل مع المبيعات** | `New-InformationBarrierPolicy -Name "Research-Sales" -AssignedSegment "Research" -SegmentsBlocked "Sales" -State Inactive` <p> في هذا المثال، يسمى نهج حاجز المعلومات *Research-Sales*. عندما يكون هذا النهج نشطا ومطبقا، سيساعد على منع المستخدمين الموجودين في الجزء "أبحاث" من التواصل مع المستخدمين في جزء "المبيعات". |
| **النهج 3: السماح للتصنيع بالاتصال بالموارد البشرية والتسويق فقط** | `New-InformationBarrierPolicy -Name "Manufacturing-HRMarketing" -AssignedSegment "Manufacturing" -SegmentsAllowed "HR","Marketing","Manufacturing" -State Inactive` <p> في هذه الحالة، يسمى نهج حاجز المعلومات *Manufacturing-HRMarketing*. عندما يكون هذا النهج نشطا ومطبقا، يمكن للتصنيع الاتصال بالموارد البشرية والتسويق فقط. الموارد البشرية والتسويق غير مقيدين من التواصل مع الشرائح الأخرى. |

مع تحديد المقاطع والنهج، تطبق Contoso النهج عن طريق تشغيل **Start-InformationBarrierPoliciesApplication** cmdlet.

عند انتهاء cmdlet، تكون Contoso متوافقة مع المتطلبات القانونية ومتطلبات الصناعة.

## <a name="resources"></a>الموارد

- [الحصول على نظرة عامة على حواجز المعلومات](information-barriers.md)
- [تعرف على المزيد حول حواجز المعلومات في Microsoft Teams](/MicrosoftTeams/information-barriers-in-teams)
- [تعرف على المزيد حول حواجز المعلومات في SharePoint Online](/sharepoint/information-barriers)
- [تعرف على المزيد حول حواجز المعلومات في OneDrive](/onedrive/information-barriers)
