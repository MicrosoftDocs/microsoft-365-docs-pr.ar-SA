---
title: إعداد مفتاح العميل
ms.author: krowley
author: kccross
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection:
- M365-security-compliance
description: تعرف على كيفية إعداد مفتاح العميل.
ms.openlocfilehash: 42c89c23f823f5f4297f31308516888633a1c06c
ms.sourcegitcommit: 570c3be37b6ab1d59a4988f7de9c9fb5ca38028f
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 05/12/2022
ms.locfileid: "65363159"
---
# <a name="set-up-customer-key"></a>إعداد مفتاح العميل

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

باستخدام Customer Key، يمكنك التحكم في مفاتيح التشفير الخاصة بمؤسستك ثم تكوين Microsoft 365 لاستخدامها لتشفير بياناتك الثابتة في مراكز بيانات Microsoft. بمعنى آخر، يسمح مفتاح العميل للعملاء بإضافة طبقة من التشفير التي تخصهم، باستخدام مفاتيحهم.

إعداد Azure قبل أن تتمكن من استخدام مفتاح العميل. تصف هذه المقالة الخطوات التي تحتاج إلى اتباعها لإنشاء موارد Azure المطلوبة وتكوينها ثم توفر الخطوات لإعداد مفتاح العميل. بعد إعداد Azure، يمكنك تحديد النهج، وبالتالي، أي مفاتيح، لتعيينها لتشفير البيانات عبر أحمال عمل Microsoft 365 المختلفة في مؤسستك. لمزيد من المعلومات حول Customer Key، أو للحصول على نظرة عامة، راجع [تشفير الخدمة باستخدام Microsoft Purview Customer Key](customer-key-overview.md).
  
> [!IMPORTANT]
> نوصي بشدة باتباع أفضل الممارسات الواردة في هذه المقالة. يتم استدعاؤها **كتلميحات** **وهامة**. يمنحك مفتاح العميل التحكم في مفاتيح التشفير الجذر التي يمكن أن يكون نطاقها كبيرا مثل مؤسستك بأكملها. وهذا يعني أن الأخطاء التي تم ارتكابها باستخدام هذه المفاتيح يمكن أن يكون لها تأثير واسع وقد تؤدي إلى انقطاع الخدمة أو فقدان البيانات بشكل لا يمكن الرجوع عنه.
  
## <a name="before-you-set-up-customer-key"></a>قبل إعداد مفتاح العميل

قبل البدء، تأكد من أن لديك اشتراكات Azure المناسبة وترخيص M365/O365 لمؤسستك. يجب استخدام اشتراكات Azure المدفوعة. الاشتراكات التي حصلت عليها من خلال الاشتراكات المجانية والإصدارات التجريبية والرعايات واشتراكات MSDN والاشتراكات ضمن الدعم القديم غير مؤهلة.

> [!IMPORTANT]
> تراخيص M365/O365 الصالحة التي توفر مفتاح عميل M365 هي:
>
> - Office 365 E5
> - Microsoft 365 E5
> - التوافق في Microsoft 365 E5
> - Microsoft 365 E5 حماية البيانات & وحدات SKU للحوكمة
> - Microsoft 365 الأمان والتوافق ل FLW

سيستمر دعم تراخيص خدمات الامتثال المتطورة في Office 365 الموجودة.

لفهم المفاهيم والإجراءات الواردة في هذه المقالة، راجع وثائق [Key Vault Azure](/azure/key-vault/). أيضا، تصبح على دراية بالمصطلحات المستخدمة في Azure، على سبيل المثال، [Azure AD المستأجر](/previous-versions/azure/azure-services/jj573650(v=azure.100)#what-is-an-azure-ad-tenant).
  
إذا كنت بحاجة إلى مزيد من الدعم خارج الوثائق، فاتصل ب Microsoft Consulting Services (MCS) أو Premier Field Engineering (PFE) أو شريك Microsoft للحصول على المساعدة. لتقديم ملاحظات حول Customer Key، بما في ذلك الوثائق، أرسل أفكارك واقتراحاتك ووجهات نظرك إلى customerkeyfeedback@microsoft.com.
  
## <a name="overview-of-steps-to-set-up-customer-key"></a>نظرة عامة على خطوات إعداد مفتاح العميل

لإعداد مفتاح العميل، أكمل هذه المهام بالترتيب المدرج. توفر بقية هذه المقالة إرشادات مفصلة لكل مهمة، أو ترتبط بمزيد من المعلومات لكل خطوة في العملية.
  
**في Azure و Microsoft FastTrack:**
  
ستكمل معظم هذه المهام عن طريق الاتصال عن بعد ب Azure PowerShell. للحصول على أفضل النتائج، استخدم الإصدار 4.4.0 أو إصدار أحدث من Azure PowerShell.
  
- [إنشاء اشتراكين جديدين في Azure](#create-two-new-azure-subscriptions)

- [إرسال طلب لتنشيط مفتاح العميل Office 365](#submit-a-request-to-activate-customer-key-for-office-365)

- [تسجيل اشتراكات Azure لاستخدام فترة استبقاء إلزامية](#register-azure-subscriptions-to-use-a-mandatory-retention-period)

  ستستغرق عملية التسجيل هذه خمسة أيام عمل لإكمالها.
- [الاتصال بالاسم المستعار المطابق ل Microsoft لمتابعة العملية](#contact-the-corresponding-microsoft-alias-to-proceed-with-the-process)

- [إنشاء Key Vault Azure متميز في كل اشتراك](#create-a-premium-azure-key-vault-in-each-subscription)

- [تعيين أذونات لكل مخزن مفاتيح](#assign-permissions-to-each-key-vault)

- [تأكد من تمكين الحذف المبدئي على مخازن المفاتيح](#make-sure-soft-delete-is-enabled-on-your-key-vaults)

- [إضافة مفتاح إلى كل مخزن رئيسي إما عن طريق إنشاء مفتاح أو استيراده](#add-a-key-to-each-key-vault-either-by-creating-or-importing-a-key)

- [التحقق من تاريخ انتهاء صلاحية المفاتيح](#verify-expiration-date-of-your-keys)

- [التحقق من مستوى الاسترداد للمفاتيح](#check-the-recovery-level-of-your-keys)

- [النسخ الاحتياطي ل Azure Key Vault](#back-up-azure-key-vault)

- [الحصول على URI لكل مفتاح Key Vault Azure](#obtain-the-uri-for-each-azure-key-vault-key)
  
## <a name="complete-tasks-in-azure-key-vault-and-microsoft-fasttrack-for-customer-key"></a>إكمال المهام في Azure Key Vault Microsoft FastTrack لمفتاح العميل

أكمل هذه المهام في Azure Key Vault. ستحتاج إلى إكمال هذه الخطوات لجميع DEPs التي تستخدمها مع مفتاح العميل.
  
### <a name="create-two-new-azure-subscriptions"></a>إنشاء اشتراكين جديدين في Azure

يتطلب مفتاح العميل اشتراكين من Azure. كأفضل ممارسة، توصي Microsoft بإنشاء اشتراكات Azure جديدة للاستخدام مع Customer Key. يمكن تخويل مفاتيح Key Vault Azure فقط للتطبيقات في نفس مستأجر Azure Active Directory (Microsoft Azure Active Directory)، يجب إنشاء الاشتراكات الجديدة باستخدام نفس المستأجر Azure AD المستخدم مع مؤسستك حيث سيتم تعيين DEPs. على سبيل المثال، استخدام حساب العمل أو المؤسسة التعليمية الذي لديه امتيازات المسؤول العام في مؤسستك. للحصول على خطوات مفصلة، راجع [التسجيل في Azure كمؤسسة](/azure/active-directory/fundamentals/sign-up-organization).
  
> [!IMPORTANT]
> يتطلب مفتاح العميل مفتاحين لكل نهج تشفير البيانات (DEP). لتحقيق ذلك، يجب إنشاء اشتراكين من Azure. وكأفضل ممارسة، توصي Microsoft بأن يكون لديك أعضاء منفصلون في مؤسستك لتكوين مفتاح واحد في كل اشتراك. يجب عليك فقط استخدام اشتراكات Azure هذه لإدارة مفاتيح التشفير Office 365. يؤدي ذلك إلى حماية مؤسستك في حالة حذف أحد عوامل التشغيل الخاصة بك عن طريق الخطأ أو عن قصد أو بشكل ضار أو إساءة إدارة المفاتيح المسؤولة عنها.

لا يوجد حد عملي لعدد اشتراكات Azure التي يمكنك إنشاؤها لمؤسستك. سيؤدي اتباع أفضل الممارسات هذه إلى تقليل تأثير الخطأ البشري مع المساعدة في إدارة الموارد المستخدمة من قبل Customer Key.
  
### <a name="submit-a-request-to-activate-customer-key-for-office-365"></a>إرسال طلب لتنشيط مفتاح العميل Office 365

بمجرد إنشاء اشتراكي Azure الجديدين، ستحتاج إلى إرسال طلب عرض مفتاح العميل المناسب في [مدخل Microsoft FastTrack](https://fasttrack.microsoft.com/). تعتبر التحديدات التي تجريها في نموذج العرض حول التعيينات المعتمدة داخل مؤسستك ضرورية وضرورية لإكمال تسجيل مفتاح العميل. يضمن الموظفون في تلك الأدوار المحددة داخل مؤسستك أصالة أي طلب لإبطال جميع المفاتيح المستخدمة مع نهج تشفير بيانات Customer Key وإتلافها. ستحتاج إلى القيام بهذه الخطوة مرة واحدة لكل نوع DEP لمفتاح العميل الذي تنوي استخدامه لمؤسستك.

**لا يقدم فريق FastTrack المساعدة مع Customer Key. تستخدم Office 365 ببساطة مدخل FastTrack للسماح لك بإرسال النموذج ولمساعدتنا في تعقب العروض ذات الصلة لمفتاح العميل. بمجرد إرسال طلب FastTrack، تواصل مع فريق إلحاق مفتاح العميل المقابل لبدء عملية الإلحاق.**
  
لإرسال عرض لتنشيط مفتاح العميل، أكمل الخطوات التالية:
  
1. باستخدام حساب العمل أو المؤسسة التعليمية الذي لديه أذونات المسؤول العام في مؤسستك، سجل الدخول إلى [مدخل Microsoft FastTrack](https://fasttrack.microsoft.com/).

2. بمجرد تسجيل الدخول، حدد المجال المناسب.

3. بالنسبة للمجال المحدد، اختر **"طلب الخدمات** " من شريط التنقل العلوي، وراجع قائمة العروض المتوفرة.

4. اختر بطاقة المعلومات الخاصة بالعرض الذي ينطبق عليك:

   - **أحمال عمل Microsoft 365 متعددة:** اختر **تعليمات مفتاح تشفير الطلب لعرض Microsoft 365**.

   - **Exchange Online Skype for Business:** اختر **تعليمات مفتاح تشفير الطلب لعرض Exchange**.

   - **SharePoint Online والملفات OneDrive والملفات Teams:** اختر **تعليمات مفتاح تشفير الطلب لعرض SharePoint OneDrive for Business**.

5. بعد مراجعة تفاصيل العرض، اختر **"متابعة" إلى الخطوة 2**.

6. املأ جميع التفاصيل القابلة للتطبيق والمعلومات المطلوبة في نموذج العرض. انتبه بشكل خاص إلى اختياراتك التي يرغب موظفو مؤسستك في تخويلها للموافقة على الإتلاف الدائم الذي لا رجعة فيه لمفاتيح التشفير والبيانات. بعد إكمال النموذج، اختر **"إرسال**".

### <a name="register-azure-subscriptions-to-use-a-mandatory-retention-period"></a>تسجيل اشتراكات Azure لاستخدام فترة استبقاء إلزامية

يمكن أن يكون الفقدان المؤقت أو الدائم لمفاتيح التشفير الجذر مدمرا أو حتى كارثيا لعملية الخدمة ويمكن أن يؤدي إلى فقدان البيانات. لهذا السبب، تتطلب الموارد المستخدمة مع مفتاح العميل حماية قوية. توفر جميع موارد Azure المستخدمة مع Customer Key آليات حماية تتجاوز التكوين الافتراضي. يمكنك وضع علامة على اشتراكات Azure أو تسجيلها *لفترة استبقاء إلزامية*. تمنع فترة الاستبقاء الإلزامية الإلغاء الفوري وغير القابل للإلغاء لاشتراك Azure. تتطلب الخطوات المطلوبة لتسجيل اشتراكات Azure لفترة استبقاء إلزامية التعاون مع فريق Microsoft 365. ستستغرق هذه العملية خمسة أيام عمل لإكمالها. في السابق، كان يشار أحيانا إلى فترة الاستبقاء الإلزامية باسم "عدم الإلغاء".
  
> [!IMPORTANT]
> قبل الاتصال بفريق Microsoft 365، يجب عليك تنفيذ الخطوات التالية **لكل** اشتراك Azure تستخدمه مع Customer Key. تأكد من تثبيت وحدة [Azure PowerShell Az](/powershell/azure/new-azureps-module-az) قبل البدء.

1. تسجيل الدخول باستخدام Azure PowerShell. للحصول على الإرشادات، راجع [تسجيل الدخول باستخدام Azure PowerShell](/powershell/azure/authenticate-azureps).

2. قم بتشغيل Register-AzProviderFeature cmdlet لتسجيل اشتراكاتك لاستخدام فترة استبقاء إلزامية. أكمل هذا الإجراء لكل اشتراك.

   ```powershell
   Set-AzContext -SubscriptionId <SubscriptionId>
   Register-AzProviderFeature -FeatureName mandatoryRetentionPeriodEnabled -ProviderNamespace Microsoft.Resources
   ```

### <a name="contact-the-corresponding-microsoft-alias-to-proceed-with-the-process"></a>الاتصال بالاسم المستعار المطابق ل Microsoft لمتابعة العملية

>[!NOTE]
> قبل الاتصال باسم Microsoft المستعار المقابل، تحقق من إكمال طلبات FastTrack لمفتاح عميل M365.

- لتمكين مفتاح العميل لتعيين DEP إلى علب بريد Exchange Online فردية، اتصل [exock@microsoft.com](mailto:exock@microsoft.com).

- لتمكين مفتاح العميل لتعيين DEPs لتشفير محتوى SharePoint Online ومحتوى OneDrive for Business (بما في ذلك ملفات Teams) لكافة المستخدمين المستأجرين، اتصل [spock@microsoft.com](mailto:spock@microsoft.com).

- لتمكين مفتاح العميل لتعيين DEPs لتشفير المحتوى عبر أحمال عمل Microsoft 365 متعددة (Exchange Online، Teams، حماية البيانات في Microsoft Purview) لجميع المستخدمين المستأجرين، اتصل [m365-ck@service.microsoft.com](mailto:m365-ck@service.microsoft.com).

- قم بتضمين المعلومات التالية في بريدك الإلكتروني:

     **الموضوع**: مفتاح العميل ل \<*Your tenant's fully qualified domain name*\>

     **النص الأساسي**: تضمين معرفات طلب FastTrack ومعرف الاشتراك **لكل** من خدمات مفتاح العميل التي ترغب في إلحاقها. معرفات الاشتراك هذه هي تلك التي تريد إكمال فترة الاستبقاء الإلزامية وإخراج Get-AzProviderFeature لكل اشتراك.

اتفاقية مستوى الخدمة (SLA) لإكمال هذه العملية هي خمسة أيام عمل بمجرد إعلام Microsoft (والتحقق منها) بتسجيل اشتراكاتك لاستخدام فترة استبقاء إلزامية.

### <a name="verify-the-status-of-each-your-azure-subscriptions"></a>التحقق من حالة كل اشتراك من اشتراكات Azure

بمجرد تلقي إعلام من Microsoft بإكمال التسجيل، تحقق من حالة التسجيل عن طريق تشغيل الأمر Get-AzProviderFeature كما يلي. إذا تم التحقق من ذلك، يقوم الأمر Get-AzProviderFeature بإرجاع قيمة **مسجلة** لخاصية **حالة التسجيل** . أكمل هذه الخطوة **لكل** اشتراك.

   ```powershell
   Set-AzContext -SubscriptionId <SubscriptionId>
   Get-AzProviderFeature -ProviderNamespace Microsoft.Resources -FeatureName mandatoryRetentionPeriodEnabled
   ```

لإكمال العملية، قم بتشغيل الأمر Register-AzResourceProvider. أكمل هذه الخطوة **لكل** اشتراك.

   ```powershell
   Set-AzContext -SubscriptionId <SubscriptionId>
   ```

   ```powershell
   Register-AzResourceProvider -ProviderNamespace Microsoft.KeyVault
   ```

> [!TIP]
> قبل الانتقال، تأكد من تعيين "RegistrationState" إلى "مسجل" مثل الصورة أدناه.
>
> ![فترة الاستبقاء الإلزامية](../media/MandatoryRetentionPeriod.png)

### <a name="create-a-premium-azure-key-vault-in-each-subscription"></a>إنشاء Key Vault Azure متميز في كل اشتراك

يتم توثيق خطوات إنشاء مخزن رئيسي في [بدء استخدام Azure Key Vault](/azure/key-vault/general/overview)، والتي ترشدك من خلال تثبيت وتشغيل Azure PowerShell، والاتصال باشتراك Azure الخاص بك، وإنشاء مجموعة موارد، وإنشاء مخزن رئيسي في مجموعة الموارد هذه.
  
عند إنشاء مخزن رئيسي، يجب اختيار SKU: إما قياسي أو Premium. تسمح وحدة SKU القياسية بحماية مفاتيح Key Vault Azure مع البرامج - لا توجد حماية مفتاح وحدة أمان الأجهزة (HSM) - ويسمح Premium SKU باستخدام HSMs لحماية مفاتيح Key Vault. يقبل Customer Key مخازن المفاتيح التي تستخدم إما SKU، على الرغم من أن Microsoft توصي بشدة باستخدام Premium SKU فقط. تكلفة العمليات مع مفاتيح من أي نوع هي نفسها، لذلك الفرق الوحيد في التكلفة هو التكلفة لكل شهر لكل مفتاح محمي بواسطة HSM. راجع [تسعير Key Vault](https://azure.microsoft.com/pricing/details/key-vault/) للحصول على التفاصيل.
  
> [!IMPORTANT]
> استخدم Premium مخازن مفاتيح SKU والمفاتيح المحمية بواسطة HSM لبيانات الإنتاج، واستخدم فقط مخازن مفاتيح SKU القياسية ومفاتيحها لأغراض الاختبار والتحقق من الصحة.
  
لكل خدمة Microsoft 365 التي ستستخدم بها Customer Key، قم بإنشاء مخزن مفاتيح في كل من اشتراكي Azure اللذين أنشأتهما. على سبيل المثال، لتمكين مفتاح العميل من استخدام DEPs لسيناريوهات Exchange Online SharePoint Online وأحمال العمل المتعددة، ستنشئ ثلاثة أزواج من مخازن المفاتيح.
  
استخدم اصطلاح تسمية للمخازن الرئيسية التي تعكس الاستخدام المقصود من DEP الذي ستقوم بإقران المخازن به. راجع القسم "أفضل الممارسات" أدناه للاطلاع على توصيات اصطلاح التسمية.
  
إنشاء مجموعة منفصلة ومقرنة من المخازن لكل نهج تشفير بيانات. بالنسبة Exchange Online، يتم اختيار نطاق نهج تشفير البيانات من قبلك عند تعيين النهج إلى علبة البريد. يمكن أن تحتوي علبة البريد على نهج واحد فقط معين، ويمكنك إنشاء ما يصل إلى 50 نهجا. يتضمن نطاق نهج SharePoint Online جميع البيانات داخل مؤسسة في موقع جغرافي أو *جغرافي*. يتضمن نطاق نهج حمل العمل المتعدد جميع البيانات عبر أحمال العمل المدعومة لجميع المستخدمين.

يتطلب إنشاء مخازن المفاتيح أيضا إنشاء مجموعات موارد Azure، لأن المخازن الرئيسية تحتاج إلى سعة تخزين (على الرغم من أنها صغيرة) كما أن تسجيل Key Vault، إذا تم تمكينه، يولد أيضا البيانات المخزنة. كأفضل ممارسة توصي Microsoft باستخدام مسؤولين منفصلين لإدارة كل مجموعة موارد، مع الإدارة التي تتماشى مع مجموعة المسؤولين الذين سيديرون جميع موارد مفتاح العميل ذات الصلة.
  
### <a name="assign-permissions-to-each-key-vault"></a>تعيين أذونات لكل مخزن مفاتيح

ستحتاج إلى تحديد ثلاث مجموعات منفصلة من الأذونات لكل مخزن رئيسي، اعتمادا على تنفيذك. على سبيل المثال، ستحتاج إلى تحديد مجموعة واحدة من الأذونات لكل مما يلي:
  
- **مسؤولو Key vault** الذين يقومون بإدارة يوم إلى يوم لخزنة المفاتيح الخاصة بك لمؤسستك. تتضمن هذه المهام النسخ الاحتياطي، وإنشاء، والحصول، والاستيراد، والقائمة، والاستعادة.

  > [!IMPORTANT]
  > لا تتضمن مجموعة الأذونات المعينة لمسؤولي key vault الإذن لحذف المفاتيح. هذه ممارسة مقصودة ومهمة. لا يتم حذف مفاتيح التشفير عادة، لأن القيام بذلك يؤدي إلى إتلاف البيانات بشكل دائم. وكأفضل ممارسة، لا تمنح هذا الإذن لمسؤولي key vault بشكل افتراضي. بدلا من ذلك، احجز هذا للمساهمين في المخزن الرئيسي وتعيينه فقط إلى مسؤول على المدى القصير بمجرد فهم فهم واضح للعواقب.
  
  لتعيين هذه الأذونات لمستخدم في مؤسستك، سجل الدخول إلى اشتراك Azure باستخدام Azure PowerShell. للحصول على الإرشادات، راجع [تسجيل الدخول باستخدام Azure PowerShell](/powershell/azure/authenticate-azureps).

  - قم بتشغيل Set-AzKeyVaultAccessPolicy cmdlet لتعيين الأذونات الضرورية.

   ```powershell
   Set-AzKeyVaultAccessPolicy -VaultName <vault name> -UserPrincipalName <UPN of user> -PermissionsToKeys create,import,list,get,backup,restore
   ```

   على سبيل المثال:

   ```powershell
   Set-AzKeyVaultAccessPolicy -VaultName Contoso-CK-EX-NA-VaultA1 -UserPrincipalName alice@contoso.com -PermissionsToKeys create,import,list,get,backup,restore
   ```

- **المساهمون في Key vault** الذين يمكنهم تغيير الأذونات على Azure Key Vault نفسه. ستحتاج إلى تغيير هذه الأذونات عندما يغادر الموظفون فريقك أو ينضمون إليه. في الحالة النادرة التي يحتاج فيها مسؤولو المخزن الرئيسي بشكل شرعي إلى إذن لحذف مفتاح أو استعادته، ستحتاج أيضا إلى تغيير الأذونات. يجب منح هذه المجموعة من المساهمين في المخزن الرئيسي دور **المساهم** في المخزن الرئيسي الخاص بك. يمكنك تعيين هذا الدور باستخدام azure Resource Manager. للحصول على خطوات مفصلة، راجع [استخدام Role-Based Access Control لإدارة الوصول إلى موارد اشتراك Azure](/azure/active-directory/role-based-access-control-configure). يمتلك المسؤول الذي يقوم بإنشاء اشتراك هذا الوصول ضمنيا، والقدرة على تعيين مسؤولين آخرين لدور المساهم.

- **الأذونات اللازمة Microsoft 365 التطبيقات** لكل مخزن رئيسي تستخدمه لمفتاح العميل، تحتاج إلى منح wrapKey، وإلغاء تحديد المفتاح، والحصول على أذونات إلى كيان خدمة Microsoft 365 المطابق.

  لمنح الإذن Microsoft 365 Service Principal، قم بتشغيل **Set-AzKeyVaultAccessPolicy** cmdlet باستخدام بناء الجملة التالي:

   ```powershell
   Set-AzKeyVaultAccessPolicy -VaultName <vault name> -PermissionsToKeys wrapKey,unwrapKey,get -ServicePrincipalName <Office 365 appID>
   ```

   حيث:
   - *اسم المخزن* هو اسم المخزن الرئيسي الذي أنشأته.
   - بالنسبة Exchange Online Skype for Business، استبدل *Office 365 appID* ب`00000002-0000-0ff1-ce00-000000000000`
   - بالنسبة SharePoint Online والملفات OneDrive for Business والملفات Teams، استبدل *Office 365 appID* ب`00000003-0000-0ff1-ce00-000000000000`
   - بالنسبة إلى نهج حمل العمل المتعدد (Exchange، Teams، حماية البيانات في Microsoft Purview) الذي ينطبق على جميع المستخدمين المستأجرين، استبدل *Office 365 appID* ب`c066d759-24ae-40e7-a56f-027002b5d3e4`

  مثال: تعيين أذونات Exchange Online Skype for Business:

   ```powershell
   Set-AzKeyVaultAccessPolicy -VaultName Contoso-CK-EX-NA-VaultA1 -PermissionsToKeys wrapKey,unwrapKey,get -ServicePrincipalName 00000002-0000-0ff1-ce00-000000000000
   ```

  مثال: تعيين أذونات لملفات SharePoint Online و OneDrive for Business و Teams:

   ```powershell
   Set-AzKeyVaultAccessPolicy -VaultName Contoso-CK-SP-NA-VaultA1 -PermissionsToKeys wrapKey,unwrapKey,get -ServicePrincipalName 00000003-0000-0ff1-ce00-000000000000
   ```

  تأكد *من منح Get و wrapKey و unwrapKey* **لكل** مخزن مفاتيح عن طريق تشغيل *Get-AzKeyVault* cmdlet.

   ```powershell
   Get-AzKeyVault -VaultName <vault name> | fl
   ```  

> [!Tip]
> قبل الانتقال، تأكد من تكوين الأذونات بشكل صحيح لمخزن المفاتيح، ستقوم *أذونات المفاتيح* بإرجاع **wrapKey، إلغاء الالتفاف، الحصول.**
> تأكد من تصحيح الأذونات للخدمة الصحيحة التي تقوم بإلحاقها. يتم سرد *اسم العرض* لكل خدمة أدناه:  
  >
  > - Exchange Online Skype for Business: *Office 365 Exchange Online*
  > - ملفات SharePoint Online و OneDrive و Teams: *Office 365 SharePoint Online*
  > - أحمال عمل Microsoft 365 متعددة: *M365DataAtRestEncryption*
  >  
  > على سبيل المثال، القصاصة البرمجية أدناه هي مثال على التأكد من تكوين الأذونات ل M365DataAtRestEncryption. سيعرض cmdlet أدناه مع مخزن يسمى *mmcexchangevault* الحقول التالية.
  >
  > ```powershell
  >   Get-AzKeyVault -VaultName mmcexchangevault | fl
  >   ```  
  >
  >
  > ![شفرات التشفير لمفتاح العميل Exchange Online.](../media/KeyVaultPermissions.png)

### <a name="make-sure-soft-delete-is-enabled-on-your-key-vaults"></a>تأكد من تمكين الحذف المبدئي على مخازن المفاتيح

عندما تتمكن من استرداد مفاتيحك بسرعة، من غير المحتمل أن تواجه انقطاعا ممتدا في الخدمة بسبب المفاتيح المحذوفة بطريق الخطأ أو الضار. قم بتمكين هذا التكوين، يشار إليه باسم الحذف المبدئي، قبل أن تتمكن من استخدام مفاتيحك مع مفتاح العميل. يتيح لك تمكين الحذف المبدئي استرداد المفاتيح أو المخازن في غضون 90 يوما من الحذف دون الحاجة إلى استعادتها من النسخة الاحتياطية.
  
لتمكين الحذف المبدئي على مخازن المفاتيح، أكمل الخطوات التالية:
  
1. سجل الدخول إلى اشتراك Azure باستخدام Windows PowerShell. للحصول على الإرشادات، راجع [تسجيل الدخول باستخدام Azure PowerShell](/powershell/azure/authenticate-azureps).

2. تشغيل [Get-AzKeyVault](/powershell/module/az.keyvault/get-azkeyvault) cmdlet. في هذا المثال، *اسم المخزن* هو اسم المخزن الرئيسي الذي تقوم بتمكين الحذف المبدئي له:

   ```powershell
   $v = Get-AzKeyVault -VaultName <vault name>
   $r = Get-AzResource -ResourceId $v.ResourceId
   $r.Properties | Add-Member -MemberType NoteProperty -Name enableSoftDelete -Value 'True'
   Set-AzResource -ResourceId $r.ResourceId -Properties $r.Properties
   ```

3. تأكد من تكوين الحذف المبدئي ل key vault عن طريق تشغيل **Get-AzKeyVault** cmdlet. إذا تم تكوين الحذف المبدئي بشكل صحيح ل key vault، فإن *الخاصية Soft Delete Enabled* ترجع قيمة **True**:

   ```powershell
   Get-AzKeyVault -VaultName <vault name> | fl
   ```

> [!TIP]
> قبل الانتقال، تأكد من تمكين "الحذف المبدئي"؟ تم تعيينه إلى "صواب" مثل الصورة أدناه.
>
> <img src="../media/SoftDeleteEnabled.png" alt="SoftDelete" width="400"/>

### <a name="add-a-key-to-each-key-vault-either-by-creating-or-importing-a-key"></a>إضافة مفتاح إلى كل مخزن رئيسي إما عن طريق إنشاء مفتاح أو استيراده

هناك طريقتان لإضافة مفاتيح إلى Key Vault Azure؛ يمكنك إنشاء مفتاح مباشرة في Key Vault، أو يمكنك استيراد مفتاح. يعد إنشاء مفتاح مباشرة في Key Vault أقل تعقيدا، ولكن استيراد مفتاح يوفر تحكما كاملا في كيفية إنشاء المفتاح. استخدم مفاتيح RSA. لا يدعم azure Key Vault الالتفاف وإلغاء التطبيق باستخدام مفاتيح المنحنى البيضاوية.

للحصول على إرشادات لإضافة مفتاح إلى كل مخزن، راجع [Add-AzKeyVaultKey](/powershell/module/az.keyvault/add-azkeyvaultkey).

 للحصول على خطوات مفصلة لإنشاء مفتاح محلي واستيراده إلى مخزن المفاتيح، راجع [كيفية إنشاء المفاتيح المحمية بواسطة HSM ونقلها ل Azure Key Vault](/azure/key-vault/keys/hsm-protected-keys). استخدم إرشادات Azure لإنشاء مفتاح في كل مخزن رئيسي.

### <a name="verify-expiration-date-of-your-keys"></a>التحقق من تاريخ انتهاء صلاحية المفاتيح

للتحقق من عدم تعيين تاريخ انتهاء الصلاحية للمفاتيح، قم بتشغيل الأمر cmdlet [Get-AzKeyVaultKey](/powershell/module/az.keyvault/get-azkeyvault) كما يلي:
  
```powershell
Get-AzKeyVaultKey -VaultName <vault name>
```

لا يمكن لمفتاح العميل استخدام مفتاح منتهي الصلاحية. ستفشل العمليات التي تمت محاولتها باستخدام مفتاح منتهي الصلاحية، وقد يؤدي ذلك إلى انقطاع الخدمة. نوصي بشدة بعدم وجود تاريخ انتهاء صلاحية للمفتاح المستخدم مع Customer Key. لا يمكن إزالة تاريخ انتهاء الصلاحية، بمجرد تعيينه، ولكن يمكن تغييره إلى تاريخ آخر. إذا كان يجب استخدام مفتاح يحتوي على تاريخ انتهاء صلاحية معين، فقم بتغيير قيمة انتهاء الصلاحية إلى 12/31/9999. لن تمر المفاتيح التي تم تعيين تاريخ انتهاء صلاحيتها إلى تاريخ آخر غير 12/31/9999 Microsoft 365 التحقق من الصحة.
  
لتغيير تاريخ انتهاء الصلاحية الذي تم تعيينه إلى أي قيمة أخرى غير 12/31/9999، قم بتشغيل [Update-AzKeyVaultKey](/powershell/module/az.keyvault/update-azkeyvaultkey) cmdlet كما يلي:
  
```powershell
Update-AzKeyVaultKey -VaultName <vault name> -Name <key name> -Expires (Get-Date -Date "12/31/9999")
```

> [!CAUTION]
> لا تعين تواريخ انتهاء الصلاحية على مفاتيح التشفير التي تستخدمها مع مفتاح العميل.  

### <a name="check-the-recovery-level-of-your-keys"></a>التحقق من مستوى الاسترداد للمفاتيح

يتطلب Microsoft 365 تعيين اشتراك Azure Key Vault إلى "عدم الإلغاء" وتمكين الحذف المبدئي للمفاتيح المستخدمة بواسطة "مفتاح العميل". يمكنك تأكيد إعدادات الاشتراكات من خلال النظر إلى مستوى الاسترداد على مفاتيحك.
  
للتحقق من مستوى الاسترداد لمفتاح، في Azure PowerShell، قم بتشغيل Get-AzKeyVaultKey cmdlet كما يلي:
  
```powershell
(Get-AzKeyVaultKey -VaultName <vault name> -Name <key name>).Attributes
```

> [!Tip]
> قبل الانتقال، إذا كانت خاصية *"مستوى الاسترداد* " ترجع أي شيء آخر غير قيمة **Recoveryable+ProtectedSubscription**، فتأكد من تسجيل ميزة *"MandatoryRetentionPeriodEnabled* " في الاشتراك ومن تمكين الحذف المبدئي على كل من مخازن المفاتيح.
>
>    <img src="../media/RecoveryLevel.png" alt="drawing" width="500"/>

### <a name="back-up-azure-key-vault"></a>النسخ الاحتياطي ل Azure Key Vault

بعد الإنشاء مباشرة أو أي تغيير على مفتاح، قم بإجراء نسخة احتياطية وتخزين نسخ من النسخ الاحتياطي، سواء عبر الإنترنت أو دون اتصال.
لإنشاء نسخة احتياطية من مفتاح Azure Key Vault، قم بتشغيل [Backup-AzKeyVaultKey](/powershell/module/az.keyvault/backup-azkeyvaultkey) cmdlet.

### <a name="obtain-the-uri-for-each-azure-key-vault-key"></a>الحصول على URI لكل مفتاح Key Vault Azure

بمجرد إعداد مخازن المفاتيح الخاصة بك وإضافة مفاتيحك، قم بتشغيل الأمر التالي للحصول على URI للمفتاح في كل مخزن مفاتيح. ستستخدم عناوين URL هذه عند إنشاء كل DEP وتعيينه لاحقا، لذا احفظ هذه المعلومات في مكان آمن. قم بتشغيل هذا الأمر مرة واحدة لكل مخزن مفاتيح.
  
في Azure PowerShell:
  
```powershell
(Get-AzKeyVaultKey -VaultName <vault name>).Id
```

## <a name="next-steps"></a>الخطوات التالية

بعد الانتهاء من الخطوات الواردة في هذه المقالة، تصبح جاهزا لإنشاء DEPs وتعيينها. للحصول على الإرشادات، راجع [إدارة مفتاح العميل](customer-key-manage.md).

## <a name="related-articles"></a>المقالات ذات الصلة

- [تشفير الخدمة باستخدام مفتاح العميل](customer-key-overview.md)

- [إدارة مفتاح العميل](customer-key-manage.md)

- [لف مفتاح عميل أو مفتاح توفر أو تدويره](customer-key-availability-key-roll.md)

- [التعرف على مفتاح التوفر](customer-key-availability-key-understand.md)

- [تشفير الخدمة](office-365-service-encryption.md)
