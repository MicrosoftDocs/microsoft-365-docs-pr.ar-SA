---
title: بدء استخدام حواجز المعلومات
description: تعرف على كيفية البدء بحواجز المعلومات في Microsoft Purview.
keywords: حواجز Microsoft 365، Microsoft Purview، التوافق، المعلومات
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
ms.openlocfilehash: ef2c8c5c4dfdbb1598c8f6edc5344da9351b6ad7
ms.sourcegitcommit: 570c3be37b6ab1d59a4988f7de9c9fb5ca38028f
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 05/12/2022
ms.locfileid: "65363281"
---
# <a name="get-started-with-information-barriers"></a>بدء استخدام حواجز المعلومات

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

تصف هذه المقالة كيفية تكوين نهج حاجز المعلومات (IB) في مؤسستك. يتم تنفيذ العديد من الخطوات، لذا تأكد من مراجعة العملية بأكملها قبل البدء في تكوين نهج IB.

يجب أن تكون على دراية ب [PowerShell cmdlets](/powershell/exchange/scc-powershell) من أجل تحديد نهج IB أو التحقق من صحتها أو تحريرها. على الرغم من أننا نقدم العديد من الأمثلة على PowerShell cmdlets في هذه المقالة، ستحتاج إلى معرفة تفاصيل أخرى (مثل قيم المعلمات) لمؤسستك.

لمزيد من المعلومات حول سيناريوهات وميزات IB، راجع [التعرف على حواجز المعلومات](information-barriers.md).

> [!TIP]
> لمساعدتك على إعداد خطتك، يتم تضمين [سيناريو مثال](#example-scenario-contosos-departments-segments-and-policies) في هذه المقالة.

## <a name="required-subscriptions-and-permissions"></a>الاشتراكات والأذونات المطلوبة

قبل البدء في استخدام IB، يجب عليك تأكيد اشتراكك في Microsoft 365 وأي وظائف إضافية. للوصول إلى IB واستخدامه، يجب أن يكون لدى مؤسستك أحد الاشتراكات أو الوظائف الإضافية التالية:

- اشتراك Microsoft 365 E5/A5 (إصدار مدفوع أو تجريبي)
- اشتراك Office 365 E5/A5/A3/A1 (إصدار مدفوع أو تجريبي)
- خدمات الامتثال المتطورة في Office 365 الوظيفة الإضافية (لم تعد متوفرة للاشتراكات الجديدة)
- اشتراك Microsoft 365 E3/A3/A1 + الوظيفة الإضافية Microsoft 365 E5/A5 Compliance
- اشتراك Microsoft 365 E3/A3/A1 + الوظيفة الإضافية Microsoft 365 E5/A5 Insider Risk Management

لمزيد من المعلومات، راجع [إرشادات الترخيص Microsoft 365 للامتثال & الأمان](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#information-protection).

[لإدارة نهج IB](information-barriers-policies.md)، يجب تعيين أحد الأدوار التالية:

- مسؤول عام Microsoft 365
- مسؤول عام Office 365
- مسؤول التوافق
- إدارة الامتثال ل IB

لمعرفة المزيد حول الأدوار والأذونات، راجع [الأذونات في مركز التوافق & الأمان Office 365](../security/office-365-security/permissions-in-the-security-and-compliance-center.md).

## <a name="configuration-concepts"></a>مفاهيم التكوين

عند تحديد نهج ل IB، ستعمل مع العديد من العناصر والمفاهيم.

- يتم تعريف **سمات حساب المستخدم** في Azure Active Directory (أو Exchange Online). يمكن أن تتضمن هذه السمات القسم والمسمى الوظيفي والموقع واسم الفريق وتفاصيل ملف تعريف الوظيفة الأخرى.
- **المقاطع** هي مجموعات من المستخدمين الذين تم تعريفهم في مدخل التوافق في Microsoft Purview باستخدام **سمة حساب مستخدم** محددة. راجع قائمة [السمات المدعومة من IB](information-barriers-attributes.md) للحصول على التفاصيل.
- **رؤية المستخدمين والمجموعات غير التابعة ل IB**. المستخدمون والمجموعات غير IB هم المستخدمون والمجموعات المستبعدة من مقاطع ونهج IB. اعتمادا على نوع نهج IB (الحظر أو السماح)، سيختلف سلوك هؤلاء المستخدمين والمجموعة في Microsoft Teams، SharePoint، OneDrive، وفي قائمة العناوين العمومية. بالنسبة للمستخدمين المحددين في نهج *السماح* ، لن تكون المجموعات غير التابعة ل IB والمستخدمين مرئية للمستخدمين المضمنين في مقاطع ونهج IB. بالنسبة للمستخدمين المحددين في نهج *الحظر* ، ستكون المجموعات غير الخاصة ب IB والمستخدمين مرئية للمستخدمين المضمنين في مقاطع ونهج IB.
- **دعم المجموعة**. يتم حاليا دعم المجموعات الحديثة فقط في IB ويتم التعامل مع قوائم التوزيع/مجموعات الأمان على أنها مجموعات غير IB.
- **حسابات المستخدمين المخفية/المعطلة**. بالنسبة للحسابات المخفية/المعطلة في مؤسستك، يتم تعيين المعلمة *HiddenFromAddressListEnabled* تلقائيا إلى *True* عندما تكون حسابات المستخدمين مخفية أو معطلة. في المؤسسات التي تدعم IB، يتم منع هذه الحسابات من الاتصال بجميع حسابات المستخدمين الأخرى. في Microsoft Teams، يتم تأمين جميع الدردشات بما في ذلك هذه الحسابات أو تتم إزالة المستخدمين تلقائيا من المحادثات.
- تحدد **نهج IB** حدود الاتصالات أو قيودها. عند تحديد نهج حاجز المعلومات، يمكنك الاختيار من بين نوعين من النهج:
  - تمنع نهج *الحظر* مقطعا واحدا من الاتصال بمقطع آخر.
  - *السماح* للنهج بتواصل مقطع واحد مع مقاطع أخرى معينة فقط.

    > [!NOTE]
    > **للسماح** بالنهج، لن تكون المجموعات غير الخاصة ب IB والمستخدمين مرئية للمستخدمين المضمنين في مقاطع ونهج IB. إذا كنت بحاجة إلى أن تكون المجموعات غير الخاصة ب IB والمستخدمين مرئيين للمستخدمين المضمنين في مقاطع ونهج IB، فيجب استخدام نهج **الحظر** .

- يتم *تطبيق النهج* بعد تحديد جميع نهج IB، وأنت مستعد لتطبيقها في مؤسستك.

## <a name="configuration-at-a-glance"></a>التكوين بنظرة سريعة

| **الخطوات** | **ما الذي ينطوي عليه الأمر** |
|:------|:----------------|
| **الخطوة 1**: [التأكد من استيفاء المتطلبات الأساسية](#step-1-make-sure-prerequisites-are-met) | - تحقق من أن لديك الاشتراكات والأذونات المطلوبة <br/>- تحقق من أن الدليل الخاص بك يتضمن بيانات لتقسيم المستخدمين<br/>- تمكين [البحث حسب الاسم ل Microsoft Teams](/microsoftteams/teams-scoped-directory-search)<br/>- تأكد من تشغيل تسجيل التدقيق<br/>- تأكد من عدم وجود نهج دفتر عناوين Exchange<br/>- استخدام PowerShell (تتوفر أمثلة)<br/>- توفير موافقة المسؤول على Microsoft Teams (يتم تضمين الخطوات) |
| **الخطوة 2**: [تقسيم المستخدمين في مؤسستك](#step-2-segment-users-in-your-organization) | - تحديد النهج المطلوبة<br/>- إنشاء قائمة مقاطع لتعريفها<br/>- تحديد السمات التي يجب استخدامها<br/>- تحديد المقاطع من حيث عوامل تصفية النهج |
| **الخطوة 3**: [تحديد نهج حاجز المعلومات](#step-3-define-information-barrier-policies) | - تحديد النهج الخاصة بك (لا تنطبق بعد)<br/>- اختر من نوعين (حظر أو السماح) |
| **الخطوة 4**: [تطبيق نهج حاجز المعلومات](#step-4-apply-information-barrier-policies) | - تعيين النهج إلى الحالة النشطة<br/>- تشغيل تطبيق النهج<br/>- عرض حالة النهج |
| **الخطوة 5**: [تكوين حواجز المعلومات على SharePoint OneDrive (اختياري)](#step-5-configuration-for-information-barriers-on-sharepoint-and-onedrive) | - تكوين IB SharePoint و OneDrive |
| **الخطوة 6**: [أوضاع حواجز المعلومات (اختيارية)](#step-6-information-barriers-modes) | - تحديث أوضاع IB إذا كان ذلك ممكنا |

## <a name="step-1-make-sure-prerequisites-are-met"></a>الخطوة 1: التأكد من استيفاء المتطلبات الأساسية

بالإضافة إلى الاشتراكات والأذونات المطلوبة، تأكد من استيفاء المتطلبات التالية قبل تكوين IB:

- **بيانات الدليل**: تأكد من أن بنية مؤسستك تنعكس في بيانات الدليل. لاتخاذ هذا الإجراء، تأكد من تعبئة سمات حساب المستخدم (مثل عضوية المجموعة أو اسم القسم وما إلى ذلك) بشكل صحيح في Azure Active Directory (أو Exchange Online). لمعرفة المزيد، راجع الموارد التالية:
  - [سمات نهج حاجز المعلومات](information-barriers-attributes.md)
  - [إضافة معلومات ملف تعريف المستخدم أو تحديثها باستخدام Azure Active Directory](/azure/active-directory/fundamentals/active-directory-users-profile-azure-portal)
  - [تكوين خصائص حساب المستخدم باستخدام Office 365 PowerShell](../enterprise/configure-user-account-properties-with-microsoft-365-powershell.md)

- **البحث في الدليل المحدد النطاق**: قبل تحديد نهج IB الأول لمؤسستك، يجب [تمكين البحث في الدليل المحدد النطاق في Microsoft Teams](/MicrosoftTeams/teams-scoped-directory-search). انتظر 24 ساعة على الأقل بعد تمكين البحث في الدليل المحدد النطاق قبل إعداد نهج IB أو تعريفها.

- **التحقق من تمكين تسجيل التدقيق**: من أجل البحث عن حالة تطبيق نهج IB، يجب تشغيل تسجيل التدقيق. يتم تمكين التدقيق للمؤسسات Microsoft 365 بشكل افتراضي. قد تكون بعض المؤسسات قد عطلت التدقيق لأسباب محددة. إذا تم تعطيل التدقيق لمؤسستك، فقد يرجع ذلك إلى إيقاف تشغيل مسؤول آخر. نوصي بالتأكيد على أنه لا بأس من إعادة تشغيل التدقيق عند إكمال هذه الخطوة. لمزيد من المعلومات، راجع [تشغيل البحث في سجل التدقيق أو إيقاف تشغيله](turn-audit-log-search-on-or-off.md).

- **إزالة نهج دفتر عناوين Exchange Online الموجودة**: قبل تعريف نهج IB وتطبيقها، يجب إزالة كافة نهج دفتر عناوين Exchange Online الموجودة في مؤسستك. تستند نهج IB إلى نهج دفتر العناوين ولا تتوافق نهج ABPs الحالية مع ABPs التي تم إنشاؤها بواسطة IB. لإزالة نهج دفتر العناوين الموجودة، راجع [إزالة نهج دفتر العناوين في Exchange Online](/exchange/address-books/address-book-policies/remove-an-address-book-policy). لمزيد من المعلومات حول نهج IB Exchange Online، راجع [حواجز المعلومات Exchange Online](information-barriers.md#information-barriers-and-exchange-online).

- **إدارة باستخدام PowerShell**: حاليا، يتم تعريف نهج IB وإدارتها في Security & Compliance Center PowerShell. على الرغم من توفير العديد من الأمثلة في هذه المقالة، ستحتاج إلى أن تكون على دراية ب PowerShell cmdlets والمعلمات. ستحتاج أيضا إلى وحدة Azure Active Directory PowerShell.
  - [الاتصال إلى Security & Compliance Center PowerShell](/powershell/exchange/connect-to-scc-powershell)
  - [تثبيت Azure Active Directory PowerShell ل Graph](/powershell/azure/active-directory/install-adv2)

- **موافقة المسؤول على IB في Microsoft Teams**: عند تطبيق نهج IB، يمكنهم إزالة المستخدمين غير التابعين ل IB من المجموعات (على سبيل المثال، قنوات Teams، التي تستند إلى مجموعات). يساعد هذا التكوين على ضمان بقاء مؤسستك متوافقة مع السياسات واللوائح. استخدم الإجراء التالي لتمكين نهج IB من العمل كما هو متوقع في Microsoft Teams.

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

## <a name="step-2-segment-users-in-your-organization"></a>الخطوة 2: تقسيم المستخدمين في مؤسستك

أثناء هذه الخطوة، يمكنك تحديد نهج IB المطلوبة، وإنشاء قائمة بالشرائح لتعريفها، ثم تعريف المقاطع الخاصة بك.

### <a name="determine-what-policies-are-needed"></a>تحديد النهج المطلوبة

بالنظر إلى احتياجات مؤسستك، حدد المجموعات داخل مؤسستك التي ستحتاج إلى نهج IB. اطرح على نفسك الأسئلة التالية:

- هل هناك لوائح داخلية أو قانونية أو صناعية تتطلب تقييد التواصل والتعاون بين المجموعات والمستخدمين في مؤسستك؟
- هل هناك أي مجموعات أو مستخدمين يجب منعهم من التواصل مع مجموعة أخرى من المستخدمين؟
- هل هناك أي مجموعات أو مستخدمين يجب السماح لهم بالاتصال بمجموعتين أو مجموعتين آخرين فقط من المستخدمين؟

فكر في النهج التي تحتاجها على أنها تنتمي إلى أحد النوعين:

- تمنع نهج *الحظر* مجموعة من الاتصال بمجموعة أخرى.
- *تسمح* النهج للمجموعة بالاتصال بمجموعات معينة فقط.

عندما يكون لديك قائمة أولية بالمجموعات والنهج المطلوبة، تابع لتحديد الشرائح التي ستحتاجها لنهج IB.

### <a name="identify-segments"></a>تحديد المقاطع

بالإضافة إلى قائمة النهج الأولية، قم بإنشاء قائمة مقاطع لمؤسستك. يجب أن ينتمي المستخدمون الذين سيتم تضمينهم في نهج IB إلى مقطع. التخطيط لأجزاءك بعناية كمستخدم يمكن أن يكون في مقطع واحد فقط. يمكن أن يكون لكل مقطع نهج IB واحد فقط مطبق.

> [!IMPORTANT]
> يمكن أن يكون المستخدم في مقطع واحد فقط.

حدد السمات في بيانات الدليل الخاصة بالمؤسسة التي ستستخدمها لتعريف المقاطع. يمكنك استخدام *القسم* أو *العضو* أو أي من سمات IB المدعومة. تأكد من وجود قيم في السمة التي تحددها للمستخدمين. لمزيد من المعلومات، راجع [السمات المدعومة ل IB](information-barriers-attributes.md).

> [!IMPORTANT]
> **قبل المتابعة إلى المقطع التالي، تأكد من أن بيانات الدليل تحتوي على قيم للسمات التي يمكنك استخدامها لتعريف المقاطع**. إذا لم تتضمن بيانات الدليل قيما للسمات التي تريد استخدامها، فيجب تحديث حسابات المستخدمين لتضمين تلك المعلومات قبل المتابعة في تكوين IB. للحصول على مساعدة في هذا الأمر، راجع الموارد التالية:<br/>- [تكوين خصائص حساب المستخدم باستخدام Office 365 PowerShell](../enterprise/configure-user-account-properties-with-microsoft-365-powershell.md)<br/>- [إضافة معلومات ملف تعريف المستخدم أو تحديثها باستخدام Azure Active Directory](/azure/active-directory/fundamentals/active-directory-users-profile-azure-portal)

### <a name="define-segments-using-powershell"></a>تعريف المقاطع باستخدام PowerShell

المهمة التالية هي تعريف المقاطع لمؤسستك. لا يؤثر تعريف المقاطع على المستخدمين، بل يضبط فقط مرحلة تعريف نهج IB ثم تطبيقها.

1. استخدم **new-OrganizationSegment** cmdlet مع معلمة **UserGroupFilter** التي تتوافق مع [السمة](information-barriers-attributes.md) التي تريد استخدامها.

    | بناء الجمله | المثال |
    |:---------|:----------|
    | `New-OrganizationSegment -Name "segmentname" -UserGroupFilter "attribute -eq 'attributevalue'"` |`New-OrganizationSegment -Name "HR" -UserGroupFilter "Department -eq 'HR'"` <p>في هذا المثال، يتم تعريف مقطع يسمى *HR* باستخدام *HR*، وهي قيمة في سمة *القسم* . يشير جزء **-eq** من cmdlet إلى "يساوي". (بدلا من ذلك، يمكنك استخدام **-ne** لتعني "not equals". راجع [استخدام "يساوي" و"لا يساوي" في تعريفات المقطع](#using-equals-and-not-equals-in-segment-definitions).) |

    بعد تشغيل كل cmdlet، يجب أن تشاهد قائمة بالتفاصيل حول المقطع الجديد. تتضمن التفاصيل نوع المقطع، ومن قام بإنشائه أو آخر تعديل له، وما إلى ذلك. 

2. كرر هذه العملية لكل مقطع تريد تعريفه.

    > [!IMPORTANT]
    > **تأكد من عدم تداخل المقاطع**. يجب أن ينتمي كل مستخدم سيتأثر بنهج IB إلى مقطع واحد (ومقطع واحد فقط). يجب ألا ينتمي أي مستخدم إلى مقطعين أو أكثر. راجع [المثال: المقاطع المعرفة في Contoso](#contosos-defined-segments) في هذه المقالة للحصول على مثال لسيناريو.

بعد تحديد المقاطع الخاصة بك، انتقل إلى [الخطوة 3: تحديد نهج حاجز المعلومات](#step-3-define-information-barrier-policies).

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
| `New-OrganizationSegment -Name "LocalFTE" -UserGroupFilter "Location -eq 'Local'" -and "Position -ne 'Temporary'"` | في هذا المثال، حددنا مقطعا يسمى *LocalFTE* يتضمن المستخدمين الموجودين محليا والذين لم يتم إدراج مواضعهم ك *"مؤقت*". |
| `New-OrganizationSegment -Name "Segment1" -UserGroupFilter "MemberOf -eq 'group1@contoso.com'' -and MemberOf -ne 'group3@contoso.com'"`| في هذا المثال، حددنا مقطعا يسمى *Segment1* يتضمن المستخدمين الأعضاء في group1@contoso.com وليس أعضاء group3@contoso.com. |
| `New-OrganizationSegment -Name "Segment2" -UserGroupFilter "MemberOf -eq 'group2@contoso.com' -or MemberOf -ne 'group3@contoso.com'"` | في هذا المثال، حددنا مقطعا يسمى *Segment2* يتضمن المستخدمين الأعضاء في group2@contoso.com وليس أعضاء group3@contoso.com. |
| `New-OrganizationSegment -Name "Segment1and2" -UserGroupFilter "(MemberOf -eq 'group1@contoso.com' -or MemberOf -eq 'group2@contoso.com') -and MemberOf -ne 'group3@contoso.com'"`| في هذا المثال، حددنا مقطعا يسمى *Segment1and2* يتضمن مستخدمين في group1@contoso.com group2@contoso.com وليس أعضاء group3@contoso.com. |

> [!TIP]
> إذا كان ذلك ممكنا، فاستخدم تعريفات المقاطع التي تتضمن "-eq" أو "-ne". حاول عدم تعريف تعريفات المقاطع المعقدة.

## <a name="step-3-define-information-barrier-policies"></a>الخطوة 3: تحديد نهج حاجز المعلومات

حدد ما إذا كنت بحاجة إلى منع الاتصالات بين مقاطع معينة أو قصر الاتصالات على مقاطع معينة. وبشكل مثالي، ستستخدم الحد الأدنى من نهج IB لضمان توافق مؤسستك مع المتطلبات الداخلية والقانونية ومتطلبات الصناعة.

> [!TIP]
> للحصول على تناسق تجربة المستخدم، نوصي باستخدام نهج الحظر لمعظم السيناريوهات إن أمكن.

باستخدام قائمة مقاطع المستخدمين ونهج IB التي تريد تعريفها، حدد سيناريو، ثم اتبع الخطوات.

- [السيناريو 1: حظر الاتصالات بين المقاطع](#scenario-1-block-communications-between-segments)
- [السيناريو 2: السماح لمقطع بالاتصال بمقطع واحد فقط](#scenario-2-allow-a-segment-to-communicate-only-with-one-other-segment)

> [!IMPORTANT]
> **تأكد من أنه أثناء تحديد النهج، لا تقوم بتعيين أكثر من نهج واحد إلى مقطع**. على سبيل المثال، إذا قمت بتعريف نهج واحد لمقطع يسمى *Sales*، فلا تحدد نهجا إضافيا *للمبيعات*.<p> بالإضافة إلى ذلك، أثناء تحديد نهج IB، تأكد من تعيين هذه النهج إلى حالة غير نشطة حتى تصبح جاهزا لتطبيقها. لا يؤثر تعريف (أو تحرير) النهج على المستخدمين حتى يتم تعيين هذه النهج إلى الحالة النشطة ثم تطبيقها.

### <a name="scenario-1-block-communications-between-segments"></a>السيناريو 1: حظر الاتصالات بين المقاطع

عندما تريد منع المقاطع من التواصل مع بعضها البعض، يمكنك تحديد نهجين: نهج لكل اتجاه. كل نهج يمنع الاتصال في اتجاه واحد فقط.

على سبيل المثال، افترض أنك تريد حظر الاتصالات بين المقطع A والمقطع B. في هذه الحالة، يمكنك تحديد نهج واحد يمنع المقطع A من الاتصال بالمقطع B، ثم تحدد نهجا ثانيا لمنع المقطع B من الاتصال بالمقطع A.

1. لتحديد نهج الحظر الأول، استخدم **New-InformationBarrierPolicy** cmdlet مع المعلمة **SegmentsBlocked** .

    | بناء الجمله | المثال |
    |:--------|:----------|
    | `New-InformationBarrierPolicy -Name "policyname" -AssignedSegment "segment1name" -SegmentsBlocked "segment2name"` | `New-InformationBarrierPolicy -Name "Sales-Research" -AssignedSegment "Sales" -SegmentsBlocked "Research" -State Inactive` <p> في هذا المثال، حددنا نهجا يسمى *Sales-Research* لجزء يسمى *Sales*. عند تنشيط هذا النهج وتطبيقه، يمنع المستخدمين في *"المبيعات"* من الاتصال بالمستخدمين في مقطع يسمى *"أبحاث*". |

2. لتعريف مقطع الحظر الثاني، استخدم **New-InformationBarrierPolicy** cmdlet مع **المعلمة SegmentsBlocked** مرة أخرى، هذه المرة مع عكس المقاطع.

    | المثال | ملاحظه |
    |:----------|:-------|
    |`New-InformationBarrierPolicy -Name "Research-Sales" -AssignedSegment "Research" -SegmentsBlocked "Sales" -State Inactive` | في هذا المثال، حددنا نهجا يسمى *Research-Sales* لمنع *الأبحاث* من التواصل مع *المبيعات*. |

3. تابع إلى أحد الإجراءات التالية:

   - (إذا لزم الأمر) [تعريف نهج للسماح لمقطع بالاتصال بمقطع واحد فقط](#scenario-2-allow-a-segment-to-communicate-only-with-one-other-segment) 
   - (بعد تحديد جميع النهج الخاصة بك) [تطبيق نهج حاجز المعلومات](#step-4-apply-information-barrier-policies)

### <a name="scenario-2-allow-a-segment-to-communicate-only-with-one-other-segment"></a>السيناريو 2: السماح لمقطع بالاتصال بمقطع واحد فقط

عندما تريد السماح لمقطع بالاتصال بمقطع واحد فقط، يمكنك تحديد نهج واحد فقط لهذا المقطع. لا يتطلب المقطع الذي يتم التواصل معه سياسة اتجاهية مماثلة (لأنه يمكنهم التواصل والتعاون مع الجميع بشكل افتراضي).

1. للسماح لمقطع واحد بالاتصال بمقطع واحد فقط، استخدم **New-InformationBarrierPolicy** cmdlet مع المعلمة **SegmentsAllowed** .

    | بناء الجمله | المثال |
    |:----------|:----------|
    | `New-InformationBarrierPolicy -Name "policyname" -AssignedSegment "segment1name" -SegmentsAllowed "segment2name","segment1name"` | `New-InformationBarrierPolicy -Name "Manufacturing-HR" -AssignedSegment "Manufacturing" -SegmentsAllowed "HR","Manufacturing" -State Inactive` <p> في هذا المثال، حددنا نهجا يسمى *Manufacturing-HR* لمقطع يسمى *التصنيع*. عند تنشيطه وتطبيقه، يسمح هذا النهج للمستخدمين في *التصنيع* بالاتصال فقط مع المستخدمين في مقطع يسمى *الموارد البشرية*. في هذه الحالة، لا يمكن ل *Manufacturing* التواصل مع المستخدمين الذين ليسوا جزءا من *الموارد البشرية*. |

    **إذا لزم الأمر، يمكنك تحديد مقاطع متعددة باستخدام أمر cmdlet هذا، كما هو موضح في المثال التالي.**

    | بناء الجمله | المثال |
    |:---------|:----------|
    | `New-InformationBarrierPolicy -Name "policyname" -AssignedSegment "segment1name" -SegmentsAllowed "segment2name", "segment3name","segment1name"` | `New-InformationBarrierPolicy -Name "Research-HRManufacturing" -AssignedSegment "Research" -SegmentsAllowed "HR","Manufacturing","Research" -State Inactive` <p> في هذا المثال، حددنا نهجا يسمح لقسم *الأبحاث* بالاتصال *بالموارد البشرية* *والتصنيع* فقط. |

    كرر هذه الخطوة لكل نهج تريد تعريفه للسماح لمقاطع معينة بالاتصال ببعض المقاطع المحددة الأخرى فقط.

2. تابع إلى أحد الإجراءات التالية:

   - (إذا لزم الأمر) [تعريف نهج لحظر الاتصالات بين المقاطع](#scenario-1-block-communications-between-segments) 
   - (بعد تحديد جميع النهج الخاصة بك) [تطبيق نهج حاجز المعلومات](#step-4-apply-information-barrier-policies)

## <a name="step-4-apply-information-barrier-policies"></a>الخطوة 4: تطبيق نهج حاجز المعلومات

لا تكون نهج IB سارية حتى تقوم بتعيينها إلى الحالة النشطة وتطبيق النهج.

1. استخدم **Get-InformationBarrierPolicy** cmdlet لمشاهدة قائمة النهج التي تم تعريفها. لاحظ الحالة والهوية (GUID) لكل نهج.

    بناء الجمله: `Get-InformationBarrierPolicy`

2. لتعيين نهج إلى الحالة النشطة، استخدم **Set-InformationBarrierPolicy** cmdlet مع معلمة **Identity** ، وتعيين معلمة **الحالة** إلى **Active**. 

    | بناء الجمله | المثال |
    |:---------|:----------|
    | `Set-InformationBarrierPolicy -Identity GUID -State Active` | `Set-InformationBarrierPolicy -Identity 43c37853-ea10-4b90-a23d-ab8c93772471 -State Active` <p> في هذا المثال، قمنا بتعيين نهج IB الذي يحتوي على GUID *43c37853-ea10-4b90-a23d-ab8c93772471* إلى الحالة النشطة. |

    كرر هذه الخطوة حسب الاقتضاء لكل نهج.

3. عند الانتهاء من تعيين نهج IB إلى الحالة النشطة، استخدم **Start-InformationBarrierPoliciesApplication** cmdlet في Security & Compliance Center PowerShell.

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

### <a name="what-if-i-need-to-remove-or-change-policies"></a>ماذا لو كنت بحاجة إلى إزالة النهج أو تغييرها؟

تتوفر الموارد لمساعدتك في إدارة نهج IB.

- لتحرير نهج IB أو إيقافها أو إزالتها، راجع [إدارة نهج حواجز المعلومات](information-barriers-edit-segments-policies.md).
- إذا حدث خطأ ما في IB، فراجع [استكشاف أخطاء حواجز المعلومات وإصلاحها](/office365/troubleshoot/information-barriers/information-barriers-troubleshooting).

## <a name="step-5-configuration-for-information-barriers-on-sharepoint-and-onedrive"></a>الخطوة 5: تكوين حواجز المعلومات على SharePoint OneDrive

إذا كنت تقوم بتكوين IB SharePoint OneDrive، فستحتاج إلى تمكين IB على هذه الخدمات. ستحتاج أيضا إلى تمكين IB على هذه الخدمات إذا كنت تقوم بتكوين IB Microsoft Teams. عند إنشاء فريق في فريق Microsoft Teams، يتم تلقائيا إنشاء موقع SharePoint وإقرانه Microsoft Teams لتجربة الملفات. لا يتم احترام نهج IB على هذا الموقع والملفات SharePoint الجديدة بشكل افتراضي.

لتمكين IB في SharePoint OneDrive، اتبع الإرشادات والخطوات الواردة في [حواجز استخدام المعلومات مع المقالة SharePoint](/sharepoint/information-barriers).

## <a name="step-6-information-barriers-modes"></a>الخطوة 6: أوضاع حواجز المعلومات

يمكن أن تساعد الأوضاع في تعزيز الوصول والمشاركة والعضوية لمورد Microsoft 365 استنادا إلى وضع IB الخاص بالمورد. يتم دعم الأوضاع على مواقع مجموعات Microsoft 365 Microsoft Teams OneDrive SharePoint ويتم تمكينها تلقائيا في تكوين IB الجديد أو الحالي.

يتم دعم أوضاع IB التالية على موارد Microsoft 365:

| **الوضع** | **الوصف** | **المثال** |
|:-----|:------------|:--------|
| **فتح** | لا توجد أي نهج أو مقاطع ل IB مقترنة بمورد Microsoft 365. يمكن دعوة أي شخص ليكون عضوا في المورد. | موقع فريق تم إنشاؤه لحدث نزهة لمؤسستك. |
| **مالك متوسط (معاينة)** | يتم تحديد نهج IB لمورد Microsoft 365 من نهج IB لمالك المورد. يمكن لمالكي الموارد دعوة أي مستخدم إلى المورد استنادا إلى نهج IB الخاصة بهم. يعد هذا الوضع مفيدا عندما تريد شركتك السماح بالتعاون بين مستخدمي الشرائح غير المتوافقين الذين يديرهم المالك. يمكن لمالك المورد فقط إضافة أعضاء جدد وفقا لنهج IB. | يريد نائب الرئيس للموارد البشرية التعاون مع أجهزة ظاهرية للمبيعات والأبحاث. موقع SharePoint جديد تم تعيينه باستخدام مالك وضع IB *الذي تم الإشراف عليه* لإضافة كل من مستخدمي قسم المبيعات والأبحاث إلى نفس الموقع. تقع على عاتق المالك مسؤولية ضمان إضافة الأعضاء المناسبين إلى المورد. |
| **الضمني** | يتم توريث نهج IB أو مقاطع مورد Microsoft 365 من نهج IB لأعضاء الموارد. يمكن للمالك إضافة أعضاء طالما أنهم متوافقون مع الأعضاء الحاليين للمورد. هذا هو وضع IB الافتراضي Microsoft Teams. | ينشئ مستخدم قسم المبيعات فريق Microsoft Teams للتعاون مع الشرائح الأخرى المتوافقة في المؤسسة. |
| **صريحه** | نهج IB لمورد Microsoft 365 هو حسب الأجزاء المقترنة بالمورد. مالك المورد أو مسؤول SharePoint لديه القدرة على إدارة المقاطع على المورد.  | موقع تم إنشاؤه فقط لأعضاء مقطع المبيعات للتعاون من خلال ربط مقطع المبيعات بالموقع.   |

لمزيد من المعلومات حول أوضاع IB وكيفية تكوينها عبر الخدمات، راجع المقالات التالية:

- [أوضاع حواجز المعلومات Microsoft Teams](/microsoftteams/information-barriers-in-teams)
- [أوضاع حواجز المعلومات OneDrive](/onedrive/information-barriers)
- [أوضاع حواجز المعلومات SharePoint](/sharepoint/information-barriers)

## <a name="example-scenario-contosos-departments-segments-and-policies"></a>سيناريو مثال: أقسام Contoso وأجزاءها وسياساتها

لمعرفة كيفية تعامل المؤسسة مع تحديد المقاطع والنهج، ضع في اعتبارك سيناريو المثال التالي.

### <a name="contosos-departments-and-plan"></a>أقسام Contoso وخطتها

تمتلك شركة Contoso خمسة أقسام: *الموارد البشرية* *والمبيعات* *والتسويق* *والبحث* *والتصنيع*. من أجل البقاء متوافقا مع اللوائح الصناعية، لا يفترض بالمستخدمين في بعض الأقسام التواصل مع الأقسام الأخرى، كما هو مذكور في الجدول التالي:

| الجزء | يمكن التواصل مع | لا يمكن التواصل مع |
|:----------|:--------------|:-----------------|
| ساعه | الجميع | (بدون قيود) |
| المبيعات | الموارد البشرية والتسويق والتصنيع | أبحاث |
| التسويق | الجميع | (بدون قيود) |
| أبحاث | الموارد البشرية والتسويق والتصنيع | المبيعات |
| التصنيع | الموارد البشرية، التسويق | أي شخص آخر غير الموارد البشرية أو التسويق |

بالنسبة إلى هذه البنية، تتضمن خطة Contoso ثلاثة نهج IB:

1. نهج IB مصمم لمنع المبيعات من التواصل مع الأبحاث
2. نهج IB آخر لمنع الأبحاث من التواصل مع المبيعات.
3. نهج IB مصمم للسماح للتسويق بالاتصال بالموارد البشرية والتسويق فقط.

بالنسبة لهذا السيناريو، ليس من الضروري تحديد نهج IB *للموارد البشرية* أو *التسويق*.

### <a name="contosos-defined-segments"></a>مقاطع Contoso المحددة

ستستخدم Contoso سمة القسم في Azure Active Directory لتعريف المقاطع، كما يلي:

| اداره | تعريف المقطع |
|:-------------|:---------------------|
| ساعه | `New-OrganizationSegment -Name "HR" -UserGroupFilter "Department -eq 'HR'"` |
| المبيعات | `New-OrganizationSegment -Name "Sales" -UserGroupFilter "Department -eq 'Sales'"` |
| التسويق | `New-OrganizationSegment -Name "Marketing" -UserGroupFilter "Department -eq 'Marketing'"` |
| أبحاث | `New-OrganizationSegment -Name "Research" -UserGroupFilter "Department -eq 'Research'"` |
| التصنيع | `New-OrganizationSegment -Name "Manufacturing" -UserGroupFilter "Department -eq 'Manufacturing'"` |

مع تحديد الشرائح، تستمر شركة Contoso في تحديد نهج IB.

### <a name="contosos-information-barrier-policies"></a>نهج حاجز المعلومات في Contoso

تحدد شركة Contoso ثلاثة نهج ل IB، كما هو موضح في الجدول التالي:

| السياسات | تعريف النهج |
|:---------|:--------------------|
| **النهج 1: منع المبيعات من التواصل مع الأبحاث** | `New-InformationBarrierPolicy -Name "Sales-Research" -AssignedSegment "Sales" -SegmentsBlocked "Research" -State Inactive` <p> في هذا المثال، يسمى نهج حاجز المعلومات *Sales-Research*. عندما يكون هذا النهج نشطا ومطبقا، سيساعد على منع المستخدمين الموجودين في مقطع المبيعات من الاتصال بالمستخدمين في الجزء "أبحاث". هذا النهج هو نهج أحادي الاتجاه؛ لن يمنع Research من التواصل مع Sales. لذلك، هناك حاجة إلى النهج 2. |
| **النهج 2: منع الأبحاث من التواصل مع المبيعات** | `New-InformationBarrierPolicy -Name "Research-Sales" -AssignedSegment "Research" -SegmentsBlocked "Sales" -State Inactive` <p> في هذا المثال، يسمى نهج حاجز المعلومات *Research-Sales*. عندما يكون هذا النهج نشطا ومطبقا، سيساعد على منع المستخدمين الموجودين في الجزء "أبحاث" من التواصل مع المستخدمين في جزء "المبيعات". |
| **النهج 3: السماح للتصنيع بالاتصال بالموارد البشرية والتسويق فقط** | `New-InformationBarrierPolicy -Name "Manufacturing-HRMarketing" -AssignedSegment "Manufacturing" -SegmentsAllowed "HR","Marketing","Manufacturing" -State Inactive` <p> في هذه الحالة، يسمى نهج IB *Manufacturing-HRMarketing*. عندما يكون هذا النهج نشطا ومطبقا، يمكن للتصنيع الاتصال بالموارد البشرية والتسويق فقط. الموارد البشرية والتسويق غير مقيدين من التواصل مع الشرائح الأخرى. |

مع تحديد المقاطع والنهج، تطبق Contoso النهج عن طريق تشغيل **Start-InformationBarrierPoliciesApplication** cmdlet.

عند انتهاء cmdlet، تكون Contoso متوافقة مع متطلبات الصناعة.

## <a name="resources"></a>الموارد

- [التعرّف على عوائق المعلومات](information-barriers.md)
- [تعرف على المزيد حول حواجز المعلومات في Microsoft Teams](/MicrosoftTeams/information-barriers-in-teams)
- [تعرف على المزيد حول حواجز المعلومات في SharePoint Online](/sharepoint/information-barriers)
- [تعرف على المزيد حول حواجز المعلومات في OneDrive](/onedrive/information-barriers)
