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
ms.openlocfilehash: 74da3ee1c2b3339a66ff205989dd978fdd00a530
ms.sourcegitcommit: 99494a5530ad64802f341573ad42796134190296
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 05/13/2022
ms.locfileid: "65396212"
---
# <a name="get-started-with-information-barriers"></a>بدء استخدام حواجز المعلومات

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

تصف هذه المقالة كيفية تكوين نهج حواجز المعلومات (IB) في مؤسستك. يتم تنفيذ العديد من الخطوات، لذا تأكد من مراجعة العملية بأكملها قبل البدء في تكوين نهج IB.

ستقوم بتكوين IB في مؤسستك باستخدام [مدخل التوافق في Microsoft Purview](https://compliance.microsoft.com) أو باستخدام [Office 365 Security and Compliance PowerShell](/powershell/exchange/scc-powershell). بالنسبة للمؤسسات التي تقوم بتكوين IB للمرة الأولى، نوصي باستخدام حل **حواجز المعلومات** في مدخل التوافق. إذا كنت تدير تكوين IB موجودا وكنت مرتاحا لاستخدام PowerShell، فلا يزال لديك هذا الخيار.

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

عند تكوين IB، ستعمل مع العديد من العناصر والمفاهيم.

- يتم تعريف **سمات حساب المستخدم** في Azure Active Directory (أو Exchange Online). يمكن أن تتضمن هذه السمات القسم والمسمى الوظيفي والموقع واسم الفريق وتفاصيل ملف تعريف الوظيفة الأخرى. ستقوم بتعيين المستخدمين أو المجموعات إلى مقاطع باستخدام هذه السمات.
- **المقاطع** هي مجموعات من المجموعات أو المستخدمين التي تم تعريفها في مدخل التوافق أو باستخدام PowerShell التي تستخدم سمات حساب المستخدم أو المجموعة المحددة. راجع قائمة [السمات المدعومة من IB](information-barriers-attributes.md) للحصول على التفاصيل.
- تحدد **نهج IB** حدود الاتصالات أو قيودها. عند تحديد نهج IB، يمكنك الاختيار من بين نوعين من النهج:
  - تمنع نهج *الحظر* مقطعا واحدا من الاتصال بمقطع آخر.
  - *السماح* للنهج بتواصل مقطع واحد مع مقاطع أخرى معينة فقط.

    > [!NOTE]
    > *للسماح* بالنهج، لن تكون المجموعات غير الخاصة ب IB والمستخدمين مرئية للمستخدمين المضمنين في مقاطع ونهج IB. إذا كنت بحاجة إلى أن تكون المجموعات غير الخاصة ب IB والمستخدمين مرئيين للمستخدمين المضمنين في مقاطع ونهج IB، فيجب استخدام نهج *الحظر* .

- يتم **تطبيق النهج** بعد تحديد جميع نهج IB، وأنت مستعد لتطبيقها في مؤسستك.
- **رؤية المستخدمين والمجموعات غير التابعة ل IB**. المستخدمون والمجموعات غير IB هم المستخدمون والمجموعات المستبعدة من مقاطع ونهج IB. اعتمادا على نوع نهج IB (الحظر أو السماح)، سيختلف سلوك هؤلاء المستخدمين والمجموعة في Microsoft Teams، SharePoint، OneDrive، وفي قائمة العناوين العمومية. بالنسبة للمستخدمين المحددين في نهج *السماح* ، لن تكون المجموعات غير التابعة ل IB والمستخدمين مرئية للمستخدمين المضمنين في مقاطع ونهج IB. بالنسبة للمستخدمين المحددين في نهج *الحظر* ، ستكون المجموعات غير الخاصة ب IB والمستخدمين مرئية للمستخدمين المضمنين في مقاطع ونهج IB.
- **دعم المجموعة**. يتم حاليا دعم المجموعات الحديثة فقط في IB ويتم التعامل مع قوائم التوزيع/مجموعات الأمان على أنها مجموعات غير IB.
- **حسابات المستخدمين المخفية/المعطلة**. بالنسبة للحسابات المخفية/المعطلة في مؤسستك، يتم تعيين المعلمة *HiddenFromAddressListEnabled* تلقائيا إلى *True* عندما تكون حسابات المستخدمين مخفية أو معطلة. في المؤسسات التي تدعم IB، يتم منع هذه الحسابات من الاتصال بجميع حسابات المستخدمين الأخرى. في Microsoft Teams، يتم تأمين جميع الدردشات بما في ذلك هذه الحسابات أو تتم إزالة المستخدمين تلقائيا من المحادثات.

## <a name="configuration-overview"></a>نظرة عامة على التكوين

| **الخطوات** | **ما الذي ينطوي عليه الأمر** |
|:------|:----------------|
| **الخطوة 1**: [التأكد من استيفاء المتطلبات الأساسية](#step-1-make-sure-prerequisites-are-met) | - تحقق من أن لديك الاشتراكات والأذونات المطلوبة <br/>- تحقق من أن الدليل الخاص بك يتضمن بيانات لتقسيم المستخدمين<br/>- تمكين [البحث حسب الاسم ل Microsoft Teams](/microsoftteams/teams-scoped-directory-search)<br/>- تأكد من تشغيل تسجيل التدقيق<br/>- تأكد من عدم وجود نهج دفتر عناوين Exchange <br/>- توفير موافقة المسؤول على Microsoft Teams (يتم تضمين الخطوات) |
| **الخطوة 2**: [تقسيم المستخدمين في مؤسستك](#step-2-segment-users-in-your-organization) | - تحديد النهج المطلوبة<br/>- إنشاء قائمة مقاطع لتعريفها<br/>- تحديد السمات التي يجب استخدامها<br/>- تحديد المقاطع من حيث عوامل تصفية النهج |
| **الخطوة 3**: [إنشاء نهج حواجز المعلومات](#step-3-create-ib-policies) | - إنشاء النهج الخاصة بك (لا تنطبق بعد)<br/>- اختر من نوعين (حظر أو السماح) |
| **الخطوة 4**: [تطبيق نهج حواجز المعلومات](#step-4-apply-ib-policies) | - تعيين النهج إلى الحالة النشطة<br/>- تشغيل تطبيق النهج<br/>- عرض حالة النهج |
| **الخطوة 5**: [تكوين حواجز المعلومات على SharePoint OneDrive (اختياري)](#step-5-configuration-for-information-barriers-on-sharepoint-and-onedrive) | - تكوين IB SharePoint و OneDrive |
| **الخطوة 6**: [أوضاع حواجز المعلومات (اختيارية)](#step-6-information-barriers-modes) | - تحديث أوضاع IB إذا كان ذلك ممكنا |

## <a name="step-1-make-sure-prerequisites-are-met"></a>الخطوة 1: التأكد من استيفاء المتطلبات الأساسية

بالإضافة إلى الاشتراكات والأذونات المطلوبة، تأكد من استيفاء المتطلبات التالية قبل تكوين IB:

- **بيانات الدليل**: تأكد من أن بنية مؤسستك تنعكس في بيانات الدليل. لاتخاذ هذا الإجراء، تأكد من تعبئة سمات حساب المستخدم (مثل عضوية المجموعة أو اسم القسم وما إلى ذلك) بشكل صحيح في Azure Active Directory (أو Exchange Online). لمعرفة المزيد، راجع الموارد التالية:
  - [سمات نهج حواجز المعلومات](information-barriers-attributes.md)
  - [إضافة معلومات ملف تعريف المستخدم أو تحديثها باستخدام Azure Active Directory](/azure/active-directory/fundamentals/active-directory-users-profile-azure-portal)
  - [تكوين خصائص حساب المستخدم باستخدام Office 365 PowerShell](../enterprise/configure-user-account-properties-with-microsoft-365-powershell.md)

- **البحث في الدليل المحدد النطاق**: قبل تحديد نهج IB الأول لمؤسستك، يجب [تمكين البحث في الدليل المحدد النطاق في Microsoft Teams](/MicrosoftTeams/teams-scoped-directory-search). انتظر 24 ساعة على الأقل بعد تمكين البحث في الدليل المحدد النطاق قبل إعداد نهج IB أو تعريفها.

- **التحقق من تمكين تسجيل التدقيق**: من أجل البحث عن حالة تطبيق نهج IB، يجب تشغيل تسجيل التدقيق. يتم تمكين التدقيق للمؤسسات Microsoft 365 بشكل افتراضي. قد تكون بعض المؤسسات قد عطلت التدقيق لأسباب محددة. إذا تم تعطيل التدقيق لمؤسستك، فقد يرجع ذلك إلى إيقاف تشغيل مسؤول آخر. نوصي بالتأكيد على أنه لا بأس من إعادة تشغيل التدقيق عند إكمال هذه الخطوة. لمزيد من المعلومات، راجع [تشغيل البحث في سجل التدقيق أو إيقاف تشغيله](turn-audit-log-search-on-or-off.md).

- **إزالة نهج دفتر عناوين Exchange Online الموجودة**: قبل تعريف نهج IB وتطبيقها، يجب إزالة كافة نهج دفتر عناوين Exchange Online الموجودة في مؤسستك. تستند نهج IB إلى نهج دفتر العناوين ولا تتوافق نهج ABPs الحالية مع ABPs التي تم إنشاؤها بواسطة IB. لإزالة نهج دفتر العناوين الموجودة، راجع [إزالة نهج دفتر العناوين في Exchange Online](/exchange/address-books/address-book-policies/remove-an-address-book-policy). لمزيد من المعلومات حول نهج IB Exchange Online، راجع [حواجز المعلومات Exchange Online](information-barriers.md#information-barriers-and-exchange-online).

- **إدارة باستخدام PowerShell (اختياري):** يمكن تعريف مقاطع ونهج IB وإدارتها في Office 365 Security & Compliance PowerShell. على الرغم من توفير العديد من الأمثلة في هذه المقالة، ستحتاج إلى أن تكون على دراية ب PowerShell cmdlets والمعلمات إذا اخترت استخدام PowerShell لتكوين مقاطع ونهج IB وإدارتها. ستحتاج أيضا إلى وحدة Azure Active Directory PowerShell إذا اخترت خيار التكوين هذا.
  - [الاتصال إلى Security & Compliance PowerShell](/powershell/exchange/connect-to-scc-powershell)
  - [تثبيت Azure Active Directory PowerShell ل Graph](/powershell/azure/active-directory/install-adv2)

- **موافقة المسؤول على IB في Microsoft Teams**: عند تطبيق نهج IB، يمكنهم إزالة المستخدمين غير التابعين ل IB من المجموعات (على سبيل المثال، قنوات Teams، التي تستند إلى مجموعات). يساعد هذا التكوين على ضمان بقاء مؤسستك متوافقة مع السياسات واللوائح. استخدم الإجراء التالي لتمكين نهج IB من العمل كما هو متوقع في Microsoft Teams.

   1. المتطلبات الأساسية: [تثبيت Azure Active Directory PowerShell Graph](/powershell/azure/active-directory/install-adv2).

   2. تشغيل أوامر PowerShell cmdlets التالية:

      ```powershell
      Connect-AzureAD -Tenant "<yourtenantdomain.com>"  //for example: Connect-AzureAD -Tenant "Contoso.onmicrosoft.com"
      $appId="bcf62038-e005-436d-b970-2a472f8c1982" 
      $sp=Get-AzureADServicePrincipal -Filter "appid eq '$($appid)'"
      if ($sp -eq $null) { New-AzureADServicePrincipal -AppId $appId }
      Start-Process  "https://login.microsoftonline.com/common/adminconsent?client_id=$appId"
      ```

   3. عند مطالبتك، سجل الدخول باستخدام حساب العمل أو المؤسسة التعليمية Office 365.

   4. في مربع الحوار " **الأذونات المطلوبة** "، راجع المعلومات، ثم اختر **"قبول**".

عند استيفاء جميع المتطلبات الأساسية، انتقل إلى الخطوة التالية.

## <a name="step-2-segment-users-in-your-organization"></a>الخطوة 2: تقسيم المستخدمين في مؤسستك

في هذه الخطوة، ستحدد نهج IB المطلوبة، وإنشاء قائمة بالشرائح لتعريفها، وتحديد المقاطع الخاصة بك. لا يؤثر تعريف المقاطع على المستخدمين، بل يضبط فقط مرحلة تعريف نهج IB ثم تطبيقها.

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

### <a name="define-segments-using-the-compliance-portal"></a>تعريف المقاطع باستخدام مدخل التوافق

لتعريف المقاطع في مدخل التوافق، أكمل الخطوات التالية:

1. سجل الدخول إلى [مدخل التوافق](https://compliance.microsoft.com) باستخدام بيانات الاعتماد لحساب مسؤول في مؤسستك.
2. في مدخل التوافق، حدد **"Information barriersSegments** > **".**
3. في الصفحة **"مقاطع** "، حدد **"مقطع جديد** " لإنشاء مقطع جديد وتكوينه.
4. في صفحة **"الاسم** "، أدخل اسما للمقطع. لا يمكنك إعادة تسمية مقطع بمجرد إنشائه.
5. حدد **التالي**.
6. في صفحة **تصفية مجموعة المستخدمين** ، حدد **"إضافة** " لتكوين سمات المجموعة والمستخدم للمقطع. اختر سمة للمقطع من قائمة السمات المتوفرة.
7. بالنسبة للسمة المحددة، حدد إما *يساوي* أو *لا يساوي* ثم أدخل قيمة السمة. على سبيل المثال، إذا قمت بتحديد *"القسم* " كسمة و" *يساوي*"، يمكنك إدخال *"التسويق* " *كقسم* محدد لحالة هذا المقطع. يمكنك إضافة شروط إضافية لسمة عن طريق تحديد **"إضافة شرط**". إذا كنت بحاجة إلى حذف سمة أو شرط سمة، فحدد أيقونة الحذف للسمة أو الشرط.
8. أضف سمات إضافية حسب الحاجة في صفحة **تصفية مجموعة المستخدمين** ، ثم حدد **"التالي**".
9. في صفحة **مراجعة الإعدادات** ، راجع الإعدادات التي اخترتها للمقطع وأي اقتراحات أو تحذيرات لتحديداتك. حدد **"تحرير"** لتغيير أي من سمات المقطع وشروطه أو حدد **"إرسال** " لإنشاء المقطع.

    > [!IMPORTANT]
    > **تأكد من عدم تداخل المقاطع**. يجب أن ينتمي كل مستخدم سيتأثر بنهج IB إلى مقطع واحد (ومقطع واحد فقط). يجب ألا ينتمي أي مستخدم إلى مقطعين أو أكثر. راجع [المثال: المقاطع المعرفة في Contoso](#contosos-defined-segments) في هذه المقالة للحصول على مثال لسيناريو.

### <a name="define-segments-using-powershell"></a>تعريف المقاطع باستخدام PowerShell

لتعريف المقاطع باستخدام PowerShell، أكمل الخطوات التالية:

1. استخدم **new-OrganizationSegment** cmdlet مع معلمة **UserGroupFilter** التي تتوافق مع [السمة](information-barriers-attributes.md) التي تريد استخدامها.

    | بناء الجمله | المثال |
    |:---------|:----------|
    | `New-OrganizationSegment -Name "segmentname" -UserGroupFilter "attribute -eq 'attributevalue'"` |`New-OrganizationSegment -Name "HR" -UserGroupFilter "Department -eq 'HR'"` <p>في هذا المثال، يتم تعريف مقطع يسمى *HR* باستخدام *HR*، وهي قيمة في سمة *القسم* . يشير جزء **-eq** من cmdlet إلى "يساوي". (بدلا من ذلك، يمكنك استخدام **-ne** لتعني "not equals". راجع [استخدام "يساوي" و"لا يساوي" في تعريفات المقطع](#using-equals-and-not-equals-in-powershell-segment-definitions).) |

    بعد تشغيل كل cmdlet، يجب أن تشاهد قائمة بالتفاصيل حول المقطع الجديد. تتضمن التفاصيل نوع المقطع، ومن قام بإنشائه أو آخر تعديل له، وما إلى ذلك. 

2. كرر هذه العملية لكل مقطع تريد تعريفه.

    > [!IMPORTANT]
    > **تأكد من عدم تداخل المقاطع**. يجب أن ينتمي كل مستخدم سيتأثر بنهج IB إلى مقطع واحد (ومقطع واحد فقط). يجب ألا ينتمي أي مستخدم إلى مقطعين أو أكثر. راجع [المثال: المقاطع المعرفة في Contoso](#contosos-defined-segments) في هذه المقالة للحصول على مثال لسيناريو.

بعد تحديد المقاطع، انتقل إلى [الخطوة 3: إنشاء نهج IB](#step-3-create-ib-policies).

### <a name="using-equals-and-not-equals-in-powershell-segment-definitions"></a>استخدام "يساوي" و"لا يساوي" في تعريفات مقطع PowerShell

في المثال التالي، نقوم بتكوين مقاطع IB باستخدام PowerShell وتحديد مقطع مثل "القسم يساوي الموارد البشرية".

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

## <a name="step-3-create-ib-policies"></a>الخطوة 3: إنشاء نهج IB

عند إنشاء نهج IB، ستحدد ما إذا كنت بحاجة إلى منع الاتصالات بين مقاطع معينة أو تقييد الاتصالات بأجزاء معينة. وبشكل مثالي، ستستخدم الحد الأدنى من نهج IB لضمان توافق مؤسستك مع المتطلبات الداخلية والقانونية ومتطلبات الصناعة. يمكنك استخدام مدخل التوافق أو PowerShell لإنشاء نهج IB وتطبيقها.

> [!TIP]
> للحصول على تناسق تجربة المستخدم، نوصي باستخدام نهج الحظر لمعظم السيناريوهات إن أمكن.

باستخدام قائمة مقاطع المستخدمين ونهج IB التي تريد تعريفها، حدد سيناريو، ثم اتبع الخطوات.

- [السيناريو 1: حظر الاتصالات بين المقاطع](#scenario-1-block-communications-between-segments)
- [السيناريو 2: السماح لمقطع بالاتصال بمقطع واحد فقط](#scenario-2-allow-a-segment-to-communicate-only-with-one-other-segment)

> [!IMPORTANT]
> **تأكد من أنه أثناء تحديد النهج، لا تقوم بتعيين أكثر من نهج واحد إلى مقطع**. على سبيل المثال، إذا قمت بتعريف نهج واحد لمقطع يسمى *Sales*، فلا تحدد نهجا إضافيا لشريحة *المبيعات* .<br> بالإضافة إلى ذلك، أثناء تحديد نهج IB، تأكد من تعيين هذه النهج إلى حالة غير نشطة حتى تصبح جاهزا لتطبيقها. لا يؤثر تعريف (أو تحرير) النهج على المستخدمين حتى يتم تعيين هذه النهج إلى الحالة النشطة ثم تطبيقها.

### <a name="scenario-1-block-communications-between-segments"></a>السيناريو 1: حظر الاتصالات بين المقاطع

عندما تريد منع المقاطع من التواصل مع بعضها البعض، يمكنك تحديد نهجين: نهج لكل اتجاه. كل نهج يمنع الاتصال في اتجاه واحد فقط.

على سبيل المثال، افترض أنك تريد حظر الاتصالات بين المقطع A والمقطع B. في هذه الحالة، يمكنك تحديد نهجين:

- نهج واحد يمنع المقطع A من الاتصال بالمقطع B
- نهج ثان لمنع المقطع B من الاتصال بالمقطع A

#### <a name="create-policies-using-the-compliance-portal-for-scenario-1"></a>إنشاء نهج باستخدام مدخل التوافق للسيناريو 1

لتحديد النهج في مدخل التوافق، أكمل الخطوات التالية:

1. سجل الدخول إلى [مدخل التوافق](https://compliance.microsoft.com) باستخدام بيانات الاعتماد لحساب مسؤول في مؤسستك.
2. في مدخل التوافق، حدد **"Information barriersPolicies** > ".
3. في صفحة **"النهج** "، حدد **"Create policy** " لإنشاء نهج IB جديد وتكوينه.
4. في صفحة **"الاسم** "، أدخل اسما للنهج، ثم حدد **"التالي**".
5. في صفحة **المقطع المعين** ، حدد **"اختيار مقطع**". استخدم مربع البحث للبحث عن مقطع حسب الاسم أو التمرير لتحديد المقطع من القائمة المعروضة. حدد **"إضافة** " لإضافة المقطع المحدد إلى النهج. يمكنك تحديد مقطع واحد فقط.
6. حدد **التالي**.
7. في صفحة **"Communication and collaboration** "، حدد نوع النهج في حقل **"Communication and collaboration** ". خيارات النهج إما *مسموح بها* أو *محظورة*. في هذا السيناريو المثال، سيتم تحديد *Blocked* للنهج الأول.

    >[!IMPORTANT]
    >لا يمكن تغيير الحالة المسموح بها والممكنة للمقاطع بعد إنشاء نهج. لتغيير الحالة بعد إنشاء نهج، يجب حذف النهج وإنشاء نهج جديد.

8. حدد **"اختيار مقطع** " لتعريف الإجراءات الخاصة بالمقطع الهدف. يمكنك تعيين أكثر من مقطع واحد في هذه الخطوة. على سبيل المثال، إذا أردت حظر المستخدمين في مقطع يسمى *"المبيعات"* من الاتصال بالمستخدمين في مقطع يسمى *"أبحاث*"، فقد تكون قد حددت مقطع *المبيعات* في الخطوة 5 وكنت ستعين " *أبحاث"* في خيار **"اختيار المقطع"** في هذه الخطوة.
9. حدد **التالي**.
10. في صفحة **حالة النهج** ، قم بتبديل حالة النهج النشط إلى **"تشغيل**". حدد **"التالي** " للمتابعة.
11. في صفحة **مراجعة الإعدادات** ، راجع الإعدادات التي اخترتها للنهج وأي اقتراحات أو تحذيرات لتحديداتك. حدد **"تحرير"** لتغيير أي من مقاطع النهج وحالته أو حدد **"إرسال** " لإنشاء النهج.

في هذا المثال، يمكنك تكرار الخطوات السابقة لإنشاء نهج *حظر* ثان لتقييد حظر المستخدمين في مقطع يسمى *"أبحاث* " من التواصل مع المستخدمين في مقطع يسمى *"المبيعات*". كنت ستعرف مقطع *"الأبحاث"* في الخطوة 5 وستعين *"المبيعات"* (أو مقاطع متعددة) في خيار **"اختيار المقطع** ".

#### <a name="create-policies-using-powershell-for-scenario-1"></a>إنشاء نهج باستخدام PowerShell للسيناريو 1

لتحديد النهج باستخدام PowerShell، أكمل الخطوات التالية:

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
   - (بعد تحديد جميع النهج الخاصة بك) [تطبيق نهج IB](#step-4-apply-ib-policies)

### <a name="scenario-2-allow-a-segment-to-communicate-only-with-one-other-segment"></a>السيناريو 2: السماح لمقطع بالاتصال بمقطع واحد فقط

عندما تريد السماح لمقطع بالاتصال بمقطع واحد فقط، يمكنك تحديد نهج واحد فقط لهذا المقطع. لا يتطلب المقطع الذي يتم التواصل معه سياسة اتجاهية مماثلة (لأنه يمكنهم التواصل والتعاون مع الجميع بشكل افتراضي).

#### <a name="create-a-policy-using-the-compliance-portal-for-scenario-2"></a>إنشاء نهج باستخدام مدخل التوافق للسيناريو 2

لتحديد النهج في مدخل التوافق، أكمل الخطوات التالية:

1. سجل الدخول إلى [مدخل التوافق](https://compliance.microsoft.com) باستخدام بيانات الاعتماد لحساب مسؤول في مؤسستك.
2. في مدخل التوافق، حدد **"Information barriersPolicies** > ".
3. في صفحة **"النهج** "، حدد **"Create policy** " لإنشاء نهج IB جديد وتكوينه.
4. في صفحة **"الاسم** "، أدخل اسما للنهج، ثم حدد **"التالي**".
5. في صفحة **المقطع المعين** ، حدد **"اختيار مقطع**". استخدم مربع البحث للبحث عن مقطع حسب الاسم أو التمرير لتحديد المقطع من القائمة المعروضة. حدد **"إضافة** " لإضافة المقطع المحدد إلى النهج. يمكنك تحديد مقطع واحد فقط.
6. حدد **التالي**.
7. في صفحة **"Communication and collaboration** "، حدد نوع النهج في حقل **"Communication and collaboration** ". خيارات النهج إما *مسموح بها* أو *محظورة*. في هذا السيناريو المثال، سيتم تحديد *Allowed* للنهج.

    >[!IMPORTANT]
    >لا يمكن تغيير الحالة المسموح بها والممكنة للمقاطع بعد إنشاء نهج. لتغيير الحالة بعد إنشاء نهج، يجب حذف النهج وإنشاء نهج جديد.

8. حدد **"اختيار مقطع** " لتعريف الإجراءات الخاصة بالمقطع الهدف. يمكنك تعيين أكثر من مقطع واحد في هذه الخطوة. على سبيل المثال، إذا أردت السماح للمستخدمين في مقطع يسمى *"التصنيع* " بالاتصال بالمستخدمين في مقطع يسمى *الموارد البشرية*، كنت ستعرف مقطع *التصنيع* في الخطوة 5 وكنت ستعين *الموارد البشرية* في خيار **"اختيار المقطع"** في هذه الخطوة.
9. حدد **التالي**.
10. في صفحة **حالة النهج** ، قم بتبديل حالة النهج النشط إلى **"تشغيل**". حدد **"التالي** " للمتابعة.
11. في صفحة **مراجعة الإعدادات** ، راجع الإعدادات التي اخترتها للنهج وأي اقتراحات أو تحذيرات لتحديداتك. حدد **"تحرير"** لتغيير أي من مقاطع النهج وحالته أو حدد **"إرسال** " لإنشاء النهج.

#### <a name="create-a-policy-using-powershell-for-scenario-2"></a>إنشاء نهج باستخدام PowerShell للسيناريو 2

لتحديد النهج باستخدام PowerShell، أكمل الخطوات التالية:

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
   - (بعد تحديد جميع النهج الخاصة بك) [تطبيق نهج IB](#step-4-apply-ib-policies)

## <a name="step-4-apply-ib-policies"></a>الخطوة 4: تطبيق نهج IB

لا تكون نهج IB سارية حتى تقوم بتعيينها إلى الحالة النشطة وتطبيق النهج.

### <a name="apply-policies-using-the-compliance-portal"></a>تطبيق النهج باستخدام مدخل التوافق

لتطبيق النهج في مدخل التوافق، أكمل الخطوات التالية:

1. سجل الدخول إلى [مدخل التوافق](https://compliance.microsoft.com) باستخدام بيانات الاعتماد لحساب مسؤول في مؤسستك.
2. في مدخل التوافق، حدد تطبيق **Information barriersPolicy** > .
3. في صفحة **تطبيق النهج** ، حدد **تطبيق كافة النهج** لتطبيق كافة نهج IB في مؤسستك.

    >[!NOTE]
    >السماح بمرور 30 دقيقة حتى يبدأ النظام في تطبيق النهج. يطبق النظام نهج المستخدم حسب المستخدم. يعالج النظام حوالي 5000 حساب مستخدم في الساعة.

### <a name="apply-policies-using-powershell"></a>تطبيق النهج باستخدام PowerShell

لتطبيق النهج باستخدام PowerShell، أكمل الخطوات التالية:

1. استخدم **Get-InformationBarrierPolicy** cmdlet لمشاهدة قائمة النهج التي تم تعريفها. لاحظ الحالة والهوية (GUID) لكل نهج.

    بناء الجمله: `Get-InformationBarrierPolicy`

2. لتعيين نهج إلى الحالة النشطة، استخدم **Set-InformationBarrierPolicy** cmdlet مع معلمة **Identity** ، وتعيين معلمة **الحالة** إلى **Active**. 

    | بناء الجمله | المثال |
    |:---------|:----------|
    | `Set-InformationBarrierPolicy -Identity GUID -State Active` | `Set-InformationBarrierPolicy -Identity 43c37853-ea10-4b90-a23d-ab8c93772471 -State Active` <p> في هذا المثال، قمنا بتعيين نهج IB الذي يحتوي على GUID *43c37853-ea10-4b90-a23d-ab8c93772471* إلى الحالة النشطة. |

    كرر هذه الخطوة حسب الاقتضاء لكل نهج.

3. عند الانتهاء من تعيين نهج IB إلى الحالة النشطة، استخدم **Start-InformationBarrierPoliciesApplication** cmdlet في Security & Compliance PowerShell.

    بناء الجمله: `Start-InformationBarrierPoliciesApplication`

    بعد التشغيل `Start-InformationBarrierPoliciesApplication`، اسمح للنظام ب 30 دقيقة لبدء تطبيق النهج. يطبق النظام نهج المستخدم حسب المستخدم. يعالج النظام حوالي 5000 حساب مستخدم في الساعة.

### <a name="view-status-of-user-accounts-segments-policies-or-policy-application"></a>عرض حالة حسابات المستخدمين أو المقاطع أو النهج أو تطبيق النهج

باستخدام PowerShell، يمكنك عرض حالة حسابات المستخدمين والمقاطع والنهج وتطبيق النهج، كما هو مذكور في الجدول التالي.

| لعرض هذه المعلومات | اتخاذ هذا الإجراء |
|:---------------|:----------|
| حسابات المستخدمين | استخدم **Get-InformationBarrierRecipientStatus** cmdlet مع معلمات الهوية. <p> بناء الجمله: `Get-InformationBarrierRecipientStatus -Identity <value> -Identity2 <value>` <p> يمكنك استخدام أي قيمة تعرف كل مستخدم بشكل فريد، مثل الاسم أو الاسم المستعار أو الاسم المميز أو اسم المجال المتعارف عليه أو عنوان البريد الإلكتروني أو GUID. <p> على سبيل المثال:`Get-InformationBarrierRecipientStatus -Identity meganb -Identity2 alexw` <p> في هذا المثال، نشير إلى حسابين للمستخدمين في Office 365: *meganb* for *Megan*، و *alexw* for *Alex*. <p> (يمكنك أيضا استخدام أمر cmdlet هذا لمستخدم واحد: `Get-InformationBarrierRecipientStatus -Identity <value>`) <p> يقوم cmdlet هذا بإرجاع معلومات حول المستخدمين، مثل قيم السمات وأي نهج IB يتم تطبيقها.|
| قطاعات | استخدم **Get-OrganizationSegment** cmdlet.<p> بناء الجمله: `Get-OrganizationSegment` <p> سيعرض أمر cmdlet هذا قائمة بكافة المقاطع المحددة لمؤسستك. |
| نهج IB | استخدم **Get-InformationBarrierPolicy** cmdlet. <p> بناء الجمله: `Get-InformationBarrierPolicy` <p> سيعرض أمر cmdlet هذا قائمة بنهج IB التي تم تعريفها وحالتها. |
| أحدث تطبيق لنهج IB | استخدم **Get-InformationBarrierPoliciesApplicationStatus** cmdlet. <p> بناء الجمله: `Get-InformationBarrierPoliciesApplicationStatus`<p> سيعرض أمر cmdlet هذا معلومات حول ما إذا كان تطبيق النهج مكتملا أو فاشلا أو قيد التقدم. |
| كافة تطبيقات نهج IB|استخدام `Get-InformationBarrierPoliciesApplicationStatus -All`<p> سيعرض أمر cmdlet هذا معلومات حول ما إذا كان تطبيق النهج مكتملا أو فاشلا أو قيد التقدم.|

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
| **الضمني** | يتم توريث نهج IB أو مقاطع مورد Microsoft 365 من نهج IB لأعضاء الموارد. يمكن للمالك إضافة أعضاء طالما أنهم متوافقون مع الأعضاء الحاليين للمورد. هذا الوضع هو وضع IB الافتراضي Microsoft Teams. | ينشئ مستخدم قسم المبيعات فريق Microsoft Teams للتعاون مع الشرائح الأخرى المتوافقة في المؤسسة. |
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

### <a name="contosos-ib-policies"></a>نهج IB لشركة Contoso

تحدد شركة Contoso ثلاثة نهج ل IB، كما هو موضح في الجدول التالي:

| السياسات | تعريف النهج |
|:---------|:--------------------|
| **النهج 1: منع المبيعات من التواصل مع الأبحاث** | `New-InformationBarrierPolicy -Name "Sales-Research" -AssignedSegment "Sales" -SegmentsBlocked "Research" -State Inactive` <p> في هذا المثال، يسمى نهج IB *Sales-Research*. عندما يكون هذا النهج نشطا ومطبقا، سيساعد على منع المستخدمين الموجودين في مقطع المبيعات من الاتصال بالمستخدمين في الجزء "أبحاث". هذا النهج هو نهج أحادي الاتجاه؛ لن يمنع Research من التواصل مع Sales. لذلك، هناك حاجة إلى النهج 2. |
| **النهج 2: منع الأبحاث من التواصل مع المبيعات** | `New-InformationBarrierPolicy -Name "Research-Sales" -AssignedSegment "Research" -SegmentsBlocked "Sales" -State Inactive` <p> في هذا المثال، يطلق على نهج IB اسم *Research-Sales*. عندما يكون هذا النهج نشطا ومطبقا، سيساعد على منع المستخدمين الموجودين في الجزء "أبحاث" من التواصل مع المستخدمين في جزء "المبيعات". |
| **النهج 3: السماح للتصنيع بالاتصال بالموارد البشرية والتسويق فقط** | `New-InformationBarrierPolicy -Name "Manufacturing-HRMarketing" -AssignedSegment "Manufacturing" -SegmentsAllowed "HR","Marketing","Manufacturing" -State Inactive` <p> في هذه الحالة، يسمى نهج IB *Manufacturing-HRMarketing*. عندما يكون هذا النهج نشطا ومطبقا، يمكن للتصنيع الاتصال بالموارد البشرية والتسويق فقط. الموارد البشرية والتسويق غير مقيدين من التواصل مع الشرائح الأخرى. |

مع تحديد المقاطع والنهج، تطبق Contoso النهج عن طريق تشغيل **Start-InformationBarrierPoliciesApplication** cmdlet.

عند انتهاء cmdlet، تكون Contoso متوافقة مع متطلبات الصناعة.

## <a name="resources"></a>الموارد

- [التعرّف على عوائق المعلومات](information-barriers.md)
- [تعرف على المزيد حول حواجز المعلومات في Microsoft Teams](/MicrosoftTeams/information-barriers-in-teams)
- [تعرف على المزيد حول حواجز المعلومات في SharePoint Online](/sharepoint/information-barriers)
- [تعرف على المزيد حول حواجز المعلومات في OneDrive](/onedrive/information-barriers)
