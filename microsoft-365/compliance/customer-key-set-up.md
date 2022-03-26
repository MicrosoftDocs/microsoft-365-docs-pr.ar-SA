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
description: تعرف على كيفية إعداد "مفتاح العميل" Microsoft 365.
ms.openlocfilehash: 5c505e5c9545dd679860d9976f587459e64363c3
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 10/06/2021
ms.locfileid: "63566157"
---
# <a name="set-up-customer-key"></a>إعداد مفتاح العميل

باستخدام "مفتاح العميل"، يمكنك التحكم في مفاتيح التشفير في مؤسستك ثم تكوين Microsoft 365 لاستخدامها لتشفير البيانات في مراكز بيانات Microsoft. بعبارة أخرى، يتيح "مفتاح العميل" للعملاء إضافة طبقة تشفير خاصة بهم، باستخدام مفاتيحهم.

قم بإعداد Azure قبل أن تتمكن من استخدام "مفتاح العميل" Office 365. تصف هذه المقالة الخطوات التي تحتاج إلى اتباعها لإنشاء موارد Azure المطلوبة وتكوينها، ثم توفر الخطوات اللازمة لإعداد "مفتاح العميل" في Office 365. بعد إعداد Azure، يمكنك تحديد النهج، وبالتالي المفاتيح التي يجب تعيينها لتشفير البيانات عبر Microsoft 365 العمل المختلفة في مؤسستك. لمزيد من المعلومات حول "مفتاح العميل"، أو للحصول على نظرة عامة، راجع تشفير الخدمة [باستخدام "مفتاح](customer-key-overview.md) العميل" في Office 365.
  
> [!IMPORTANT]
> نوصي بشدة بأن تتبع أفضل الممارسات في هذه المقالة. ويتم استدعاها على أنها **تلميح** **وهام**. يمنحك "مفتاح العميل" التحكم في مفاتيح التشفير الجذر التي يمكن أن يكون نطاقها كبيرا مثل مؤسستك بأكملها. وهذا يعني أن الأخطاء التي ارتكبت باستخدام هذه المفاتيح يمكن أن يكون لها تأثير واسع النطاق وقد تؤدي إلى انقطاع الخدمة أو فقدان البيانات بشكل لا يمكن اصطدامه.
  
## <a name="before-you-set-up-customer-key"></a>قبل إعداد "مفتاح العميل"

قبل البدء، تأكد من أن لديك اشتراكات Azure المناسبة وترخيصها لمنظمتك. استخدم اشتراكات Azure المدفوعة باستخدام اتفاقية Enterprise خدمة سحابية أو موفر خدمة سحابية. لا يتم قبول الدفعات المستندة إلى بطاقة الائتمان. قم بالموافقة على احتياجات الحساب لإعدادها من أجل الفواكة. الاشتراكات التي حصلت عليها من خلال اشتراكات مجانية أو تجريبية أو رعاية أو اشتراكات MSDN أو الاشتراكات ضمن الدعم القديم غير مؤهلة.

Office 365 E5، Microsoft 365 E5، التوافق في Microsoft 365 E5، Microsoft 365 E5 حماية المعلومات & إدارة SKUs مفتاح العميل. خدمات الامتثال المتطورة في Office 365 لم تعد SKU متوفرة للحصول على تراخيص جديدة. سيستمر دعم خدمات الامتثال المتطورة في Office 365 التراخيص الموجودة.

لفهم المفاهيم والإجراءات في هذه المقالة، راجع وثائق [Azure Key Vault](/azure/key-vault/) . تعرف أيضا على المصطلحات المستخدمة في Azure، على سبيل المثال، [مستأجر Azure AD](/previous-versions/azure/azure-services/jj573650(v=azure.100)#what-is-an-azure-ad-tenant).
  
إذا كنت بحاجة إلى المزيد من الدعم خارج الوثائق، فاتصل ب Microsoft Consulting Services (MCS) أو Premier Field Engineering (PFE) أو أحد شركاء Microsoft للحصول على المساعدة. لتقديم ملاحظات حول "مفتاح العميل"، بما في ذلك الوثائق، أرسل الأفكار والاقتراحات والمناظير customerkeyfeedback@microsoft.com.
  
## <a name="overview-of-steps-to-set-up-customer-key"></a>نظرة عامة حول الخطوات اللازمة لإعداد "مفتاح العميل"

لإعداد "مفتاح العميل"، أكمل هذه المهام بالترتيب المدرج. توفر بقية هذه المقالة إرشادات مفصلة لكل مهمة، أو تربط إلى مزيد من المعلومات لكل خطوة في العملية.
  
**في Azure و Microsoft FastTrack:**
  
ستكمل معظم هذه المهام عن طريق الاتصال عن بعد ب Azure PowerShell. للحصول على أفضل النتائج، استخدم الإصدار 4.4.0 أو الإصدارات الأحدث من Azure PowerShell.
  
- [إنشاء اشتراكين جديدين في Azure](#create-two-new-azure-subscriptions)

- [إرسال طلب لتنشيط "مفتاح العميل" Office 365](#submit-a-request-to-activate-customer-key-for-office-365)
 
- [تسجيل اشتراكات Azure لاستخدام فترة استبقاء إلزامية](#register-azure-subscriptions-to-use-a-mandatory-retention-period)

  سيستغرق إكمال عملية التسجيل هذه خمسة أيام عمل.

- [إنشاء مخزن مفاتيح Azure مميز في كل اشتراك](#create-a-premium-azure-key-vault-in-each-subscription)

- [تعيين أذونات لكل مخزن مفاتيح](#assign-permissions-to-each-key-vault)

- [تأكد من تمكين الحذف الناعم على خزن المفاتيح](#make-sure-soft-delete-is-enabled-on-your-key-vaults)

- [إضافة مفتاح إلى كل مخزن مفاتيح إما عن طريق إنشاء مفتاح أو استيراده](#add-a-key-to-each-key-vault-either-by-creating-or-importing-a-key)

- [التحقق من مستوى استرداد المفاتيح](#check-the-recovery-level-of-your-keys)

- [ارجع إلى مخزن مفاتيح Azure](#back-up-azure-key-vault)

- [التحقق من صحة إعدادات تكوين مخزن المفاتيح في Azure](#validate-azure-key-vault-configuration-settings)

- [الحصول على URI لكل مفتاح مخزن مفاتيح Azure](#obtain-the-uri-for-each-azure-key-vault-key)
  
## <a name="complete-tasks-in-azure-key-vault-and-microsoft-fasttrack-for-customer-key"></a>إكمال المهام في مخزن مفاتيح Azure FastTrack Microsoft لمفتاح العميل

أكمل هذه المهام في مخزن مفاتيح Azure. ستحتاج إلى إكمال هذه الخطوات لجميع DEPs التي تستخدمها مع Customer Key.
  
### <a name="create-two-new-azure-subscriptions"></a>إنشاء اشتراكين جديدين في Azure

يتطلب "مفتاح العميل" اشتراكين في Azure. من أفضل الممارسات، توصي Microsoft بإنشاء اشتراكات Azure جديدة لاستخدامها مع "مفتاح العميل". لا يمكن التصريح بمفاتيح مخزن المفاتيح من Azure إلا للتطبيقات في نفس مستأجر Azure Active Directory (Microsoft Azure Active Directory)، ويجب عليك إنشاء الاشتراكات الجديدة باستخدام مستأجر Azure AD نفسه المستخدم مع مؤسستك حيث سيتم تعيين DEPs. على سبيل المثال، استخدام حساب العمل أو المؤسسة الدراسية الذي لديه امتيازات المسؤول العام في مؤسستك. للحصول على خطوات مفصلة، راجع [التسجيل في Azure كمنظمة](/azure/active-directory/fundamentals/sign-up-organization).
  
> [!IMPORTANT]
> يتطلب "مفتاح العميل" مفتاحين لكل نهج تشفير بيانات (DEP). لتحقيق ذلك، يجب إنشاء اشتراكين Azure. من أفضل الممارسات، توصي Microsoft بأن يكون لديك أعضاء منفصلون في مؤسستك لتكوين مفتاح واحد في كل اشتراك. يجب عليك استخدام اشتراكات Azure هذه فقط لإدارة مفاتيح التشفير Office 365. يحمي ذلك مؤسستك في حالة حذف أحد عوامل التشغيل عن طريق الخطأ أو عن قصد أو ضار للمفاتيح التي يتحملون مسؤوليتها أو إساءتها.

لا يوجد حد عملي لعدد اشتراكات Azure التي يمكنك إنشاؤها لمنظمتك. من شأن اتباع أفضل الممارسات هذه تقليل تأثير الخطأ البشري مع المساعدة في إدارة الموارد المستخدمة بواسطة "مفتاح العميل".
  
### <a name="submit-a-request-to-activate-customer-key-for-office-365"></a>إرسال طلب لتنشيط "مفتاح العميل" Office 365

بعد إنشاء اشتراكي Azure الجديدين، ستحتاج إلى إرسال طلب عرض "مفتاح العميل" المناسب [في مدخل Microsoft FastTrack الإلكتروني](https://fasttrack.microsoft.com/). إن التحديدات التي تقوم بها في نموذج العرض حول التعيينات المعتمدة داخل مؤسستك مهمة وضرورية لاكتمال تسجيل مفتاح العميل. يضمن المسؤولون في هذه الأدوار المحددة داخل مؤسستك أصالة أي طلب لإلغاء جميع المفاتيح المستخدمة مع نهج تشفير بيانات "مفتاح العميل" وإتلافها. ستحتاج إلى القيام بهذه الخطوة مرة واحدة لكل نوع من أنواع DEP لمفتاح العميل الذي تنوي استخدامه لمنظمتك.

**لا FastTrack فريق العمل المساعدة في "مفتاح العميل". Office 365 ببساطة FastTrack المدخل للسماح لك بإرسال النموذج ولمساعدتنا على تعقب العروض ذات الصلة لمفتاح العميل. بعد إرسال طلب FastTrack، يمكنك التواصل مع فريق التكميل المناسب لمفتاح العميل لبدء عملية التكميل.**
  
لإرسال عرض لتنشيط "مفتاح العميل"، أكمل الخطوات التالية:
  
1. باستخدام حساب العمل أو المؤسسة الدراسية الذي لديه أذونات المسؤول العام في مؤسستك، سجل الدخول إلى [مدخل Microsoft FastTrack.](https://fasttrack.microsoft.com/)

2. بعد تسجيل الدخول، حدد المجال المناسب.

3. للمجال المحدد، اختر **طلب خدمات** من شريط التنقل العلوي، وراجع قائمة العروض المتوفرة.

4. اختر بطاقة المعلومات الخاصة بالعرض الذي ينطبق عليك:

   - **أحمال Microsoft 365 متعددة:** اختر طلب تعليمات مفتاح التشفير **Microsoft 365** العرض.

   - **Exchange Online Skype for Business:** اختر طلب تعليمات مفتاح التشفير **Exchange** العرض.

   - **SharePoint عبر الإنترنت OneDrive** و Teams الملفات: اختر طلب تعليمات مفتاح التشفير SharePoint **OneDrive for Business** العرض.

5. بعد مراجعة تفاصيل العرض، اختر **متابعة إلى الخطوة 2**.

6. املأ كل التفاصيل القابلة للتطبيق والمعلومات المطلوبة في نموذج العرض. انتبه بشكل خاص إلى التحديدات التي تريد تخويلها من أجل الموظفين في مؤسستك للموافقة على الهلاك الدائم الذي لا يمكن التراجع عنه لمفاتيح التشفير والبيانات. بعد إكمال النموذج، اختر **إرسال**.

### <a name="register-azure-subscriptions-to-use-a-mandatory-retention-period"></a>تسجيل اشتراكات Azure لاستخدام فترة استبقاء إلزامية

يمكن أن يؤدي الفقدان المؤقت أو الدائم لمفاتيح التشفير الجذر إلى تعطيل عملية الخدمة أو حتى حدوث كارثية لها وقد يؤدي إلى فقدان البيانات. لهذا السبب، تتطلب الموارد المستخدمة مع "مفتاح العميل" حماية قوية. توفر كل موارد Azure المستخدمة مع "مفتاح العميل" آليات حماية تتجاوز التكوين الافتراضي. يمكنك وضع علامة على اشتراكات Azure أو تسجيلها لفترة *استبقاء إلزامية*. تمنع فترة الاستبقاء الإلزامية الإلغاء الفوري الذي لا يمكن إلغاءه لاشتراكك في Azure. تتطلب الخطوات المطلوبة لتسجيل اشتراكات Azure لفترة استبقاء إلزامية التعاون مع فريق Microsoft 365. سيستغرق إكمال هذه العملية خمسة أيام عمل. في السابق، كان يشار في بعض الأحيان إلى فترة الاستبقاء الإلزامية ب "عدم الإلغاء".
  
قبل الاتصال بفريق Microsoft 365، يجب عليك القيام بالخطوات التالية لكل اشتراك Azure تستخدمه مع Customer Key. تأكد من تثبيت وحدة [Azure PowerShell Az](/powershell/azure/new-azureps-module-az) النمطية قبل البدء.
  
1. سجل الدخول باستخدام Azure PowerShell. للحصول على الإرشادات، راجع [تسجيل الدخول باستخدام Azure PowerShell](/powershell/azure/authenticate-azureps).

2. قم بتشغيل Register-AzProviderFeature cmdlet لتسجيل اشتراكاتك لاستخدام فترة استبقاء إلزامية. أكمل هذا الإجراء لكل اشتراك.

   ```powershell
   Set-AzContext -SubscriptionId <SubscriptionId>
   Register-AzProviderFeature -FeatureName mandatoryRetentionPeriodEnabled -ProviderNamespace Microsoft.Resources
   ```

3. اتصل ب Microsoft لإكمال العملية.

   - لتمكين "مفتاح العميل" لتعيين DEP إلى علب بريد فردية Exchange Online، [اتصل exock@microsoft.com.](mailto:exock@microsoft.com)

   - لتمكين "مفتاح العميل" لتعيين DEPS لتشفير SharePoint عبر الإنترنت OneDrive for Business (بما في ذلك ملفات Teams) لجميع [مستخدمي](mailto:spock@microsoft.com) المستأجر، اتصل spock@microsoft.com.

   - لتمكين "مفتاح العميل" لتعيين DEPS لتشفير المحتوى عبر أحمال عمل Microsoft 365 متعددة (Exchange Online، Teams، MIP EDM) لجميع المستخدمين المستأجرين، اتصل [m365-ck@service.microsoft.com.](mailto:m365-ck@service.microsoft.com)

   - قم بتضمين المعلومات التالية في بريدك الإلكتروني:

     **الموضوع**: مفتاح العميل ل \<*Your tenant's fully qualified domain name*\>

     **المهى**: قم بتضمين "هويات الاشتراك" التي تريد إكمال فترة الاستبقاء الإلزامية لها وإخراج Get-AzProviderFeature لكل اشتراك.

     إن اتفاقية مستوى الخدمة (SLA) لاكتمال هذه العملية هي خمسة أيام عمل بمجرد إعلام Microsoft (والتحقق منها) بتسجيل اشتراكاتك لاستخدام فترة استبقاء إلزامية.

4. بمجرد تلقي إعلام من Microsoft بإكمال التسجيل، تحقق من حالة تسجيلك عن طريق تشغيل Get-AzProviderFeature على النحو التالي. إذا تم التحقق من Get-AzProviderFeature، فإن الأمر "Get-AzProviderFeature" يرجع قيمة **تم تسجيلها** **لممتلكات "حالة** التسجيل". أكمل هذه الخطوة لكل اشتراك.

   ```powershell
   Set-AzContext -SubscriptionId <SubscriptionId>
   Get-AzProviderFeature -ProviderNamespace Microsoft.Resources -FeatureName mandatoryRetentionPeriodEnabled
   ```

5. لإكمال العملية، تشغيل الأمر Register-AzResourceProvider. أكمل هذه الخطوة لكل اشتراك.

   ```powershell
   Set-AzContext -SubscriptionId <SubscriptionId>
   Register-AzResourceProvider -ProviderNamespace Microsoft.KeyVault
   ```

### <a name="create-a-premium-azure-key-vault-in-each-subscription"></a>إنشاء مخزن مفاتيح Azure مميز في كل اشتراك

تم توثيق الخطوات اللازمة لإنشاء مخزن رئيسي في بدء استخدام [مخزن مفاتيح Azure](/azure/key-vault/general/overview)، الذي يرشدك عبر تثبيت Azure PowerShell وإطلاقه، والاتصال باشتراكك في Azure، وإنشاء مجموعة موارد، وإنشاء مخزن مفاتيح في مجموعة الموارد هذه.
  
عند إنشاء مخزن مفاتيح، يجب اختيار SKU: إما قياسي أو Premium. تسمح وحدة SKU القياسية بحماية مفاتيح المخزن الرئيسي من Azure مع البرامج - لا توجد حماية لمفاتيح وحدة أمان الأجهزة (HSM) - ويسمح وحدة SKU ل Premium باستخدام HSMs لحماية مفاتيح المخزن الرئيسي. يقبل "مفتاح العميل" المخزنات الرئيسية التي تستخدم SKU، على الرغم من أن Microsoft توصي بشدة باستخدام Premium SKU فقط. تكلفة العمليات باستخدام مفاتيح من أي من النوعين هي نفسها، لذا فإن الفرق الوحيد في التكلفة هو التكلفة لكل شهر لكل مفتاح محمي HSM. راجع [سعر المخزن الرئيسي](https://azure.microsoft.com/pricing/details/key-vault/) للحصول على التفاصيل.
  
> [!IMPORTANT]
> استخدم Premium مفاتيح SKU والمفاتيح المحمية HSM لبيانات الإنتاج، ولا تستخدم سوى خزن مفاتيح SKU القياسية ومفاتيحها لأغراض الاختبار والتحقق من الصحة.
  
لكل خدمة Microsoft 365 تستخدم بها "مفتاح العميل"، قم بإنشاء مخزن مفاتيح في كل اشتراك من اشتراكي Azure الذين قمت بإنشاءهما. على سبيل المثال، لتمكين "مفتاح العميل" من استخدام DEPs Exchange Online وسيناريوهات SharePoint Online وأحمال العمل المتعددة، ستنشئ ثلاثة أزواج من خزن المفاتيح.
  
استخدم اصطلاح تسمية للمخزنات الرئيسية التي تعكس الاستخدام المقصود ل DEP الذي سيتم إقران المخزنين به. راجع القسم أفضل الممارسات أدناه لتسمية توصيات الاصطلاح.
  
قم بإنشاء مجموعة منفصلة ومقرونة من المخزن لكل نهج لتشفير البيانات. بالنسبة Exchange Online، يتم اختيار نطاق نهج تشفير البيانات من قبلك عند تعيين النهج إلى علبة البريد. يمكن أن يكون لعلبة البريد نهج واحد فقط تم تعيينه، كما يمكنك إنشاء ما يصل إلى 50 نهج. يتضمن نطاق نهج SharePoint Online كل البيانات ضمن مؤسسة في موقع جغرافي _أو جغرافي._ يتضمن نطاق نهج حمل العمل المتعدد كل البيانات عبر أحمال العمل المعتمدة لجميع المستخدمين.

يتطلب إنشاء المخازن الرئيسية أيضا إنشاء مجموعات موارد Azure، حيث تحتاج مخازن المفاتيح إلى سعة تخزينية (على الرغم من أنها صغيرة) كما أن تسجيل مخزن المفاتيح، إذا تم تمكينه، ينشئ أيضا بيانات مخزنة. من أفضل الممارسات توصي Microsoft باستخدام مسؤولي منفصلين لإدارة كل مجموعة موارد، مع الإدارة التي تتوافق مع مجموعة المسؤولين الذين سيديرون كل موارد "مفتاح العميل" ذات الصلة.
  
> [!IMPORTANT]
> لتكبير التوفر، ضع خزناتك الرئيسية في مناطق قريبة من خدمة Microsoft 365 على سبيل المثال، إذا كانت مؤسستك التي Exchange Online في أمريكا الشمالية، ف ضع خزناتك الرئيسية في أمريكا الشمالية. إذا كانت Exchange Online في أوروبا، ف ضع خزناتك الرئيسية في أوروبا.
>
> استخدم البادئية الشائعة للمخابر الرئيسية، واشتمل على اختصار لاستخدام ونطاق مخزن المفاتيح والمفاتيح الرئيسية (على سبيل المثال، لخدمة Contoso SharePoint حيث تقع المخزنات في أمريكا الشمالية، هناك زوج محتمل من الأسماء هو Contoso-CK-SP-NA-VaultA1 و Contoso-CK-SP-NA-VaultA2. أسماء المخزن هي سلاسل فريدة بشكل عام داخل Azure، لذلك قد تحتاج إلى تجربة أشكال مختلفة من الأسماء المطلوبة في حال تم المطالبة بالأسماء المطلوبة مسبقا من قبل عملاء Azure الآخرين. حتى يوليو 2017، لا يمكن تغيير أسماء المخزن، لذا فإن أفضل ممارسة هي الحصول على خطة مكتوبة للإعداد واستخدام شخص آخر للتحقق من تنفيذ الخطة بشكل صحيح.
>
> قم بإنشاء خزناتك في مناطق غير مزوجة، إذا أمكن ذلك. توفر مناطق Azure التي تم إقرانها توفرا عاليا عبر مجالات فشل الخدمة. وبالتالي، يمكن التفكير في الأزواج الإقليمية على أنها منطقة النسخ الاحتياطي الخاصة ببعضها البعض. وهذا يعني أن مورد Azure الذي يتم وضعه في منطقة واحدة يكتسب تلقائيا تفاوت الخطأ عبر المنطقة المزواجة. لهذا السبب، يعني اختيار مناطق لمخزنين يستخدمان في نهج تشفير البيانات حيث يتم إقران المنطقتين أنه يتم استخدام ما مجموعه منطقتين من التوفر فقط. يوجد في معظم المناطق الجغرافية منطقتين فقط، لذلك لا يمكن تحديد مناطق غير مزوجة بعد. إذا أمكن، اختر منطقتين غير مزوجتين للمخزنين المستخدمين مع نهج تشفير البيانات. يستفيد هذا من إجمالي أربع مناطق توفر. للحصول على مزيد من المعلومات، راجع استمرارية الأعمال واسترداد الكوارث [(BCDR): مناطق Azure الزوجية](/azure/best-practices-availability-paired-regions) للحصول على قائمة حالية بازوجات المناطق.
  
### <a name="assign-permissions-to-each-key-vault"></a>تعيين أذونات لكل مخزن مفاتيح

ستحتاج إلى تحديد ثلاث مجموعات منفصلة من الأذونات لكل مخزن مفاتيح، استنادا إلى تنفيذك. على سبيل المثال، ستحتاج إلى تعريف مجموعة واحدة من الأذونات لكل واحد من الأذونات التالية:
  
- **المسؤولون الرئيسيون في المخزن** الذين يديرون المخزن الرئيسي لم المؤسسة يوميا. تتضمن هذه المهام النسخ الاحتياطي، وإنشاء، والحصول، والاستيراد، والقائمة، والاستعادة.

  > [!IMPORTANT]
  > لا تتضمن مجموعة الأذونات المعينة لمسؤولي المخزن الأساسيين الإذن لحذف المفاتيح. هذه ممارسة مقصودة ومهمة. لا يتم عادة حذف مفاتيح التشفير، لأن القيام بذلك يتلف البيانات بشكل دائم. كأفضل ممارسة، لا تمنح هذا الإذن لمسؤولي المخزن الأساسيين بشكل افتراضي. بدلا من ذلك، احجز هذا الأمر للمساهمين الأساسيين في المخزن وخصصه لمسؤول على المدى القصير بمجرد فهم واضح لعواقب ذلك.
  
  لتعيين هذه الأذونات إلى مستخدم في مؤسستك، سجل الدخول إلى اشتراك Azure باستخدام Azure PowerShell. للحصول على الإرشادات، راجع [تسجيل الدخول باستخدام Azure PowerShell](/powershell/azure/authenticate-azureps).

- قم بتشغيل Set-AzKeyVaultAccessPolicy cmdlet لتعيين الأذونات الضرورية.

   ```powershell
   Set-AzKeyVaultAccessPolicy -VaultName <vault name> -UserPrincipalName <UPN of user> -PermissionsToKeys create,import,list,get,backup,restore
   ```

   على سبيل المثال:

   ```powershell
   Set-AzKeyVaultAccessPolicy -VaultName Contoso-CK-EX-NA-VaultA1 -UserPrincipalName alice@contoso.com -PermissionsToKeys create,import,list,get,backup,restore
   ```

- **مساهمو المخزن الرئيسيون** الذين يمكنهم تغيير الأذونات على مخزن مفاتيح Azure نفسه. ستحتاج إلى تغيير هذه الأذونات عندما يغادر الموظفون فريقك أو ينضمون إليه. في الحالات النادرة التي يحتاج فيها المسؤولون الرئيسيون في المخزن إلى إذن شرعي لحذف مفتاح أو استعادته، ستحتاج أيضا إلى تغيير الأذونات. يجب منح هذه المجموعة من المساهمين الأساسيين في المخزن دور المساهم في المخزن الرئيسي. يمكنك تعيين هذا الدور باستخدام Azure Resource Manager. للحصول على خطوات مفصلة، [راجع استخدام Role-Based Access Control لإدارة الوصول إلى موارد اشتراك Azure](/azure/active-directory/role-based-access-control-configure). لدى المسؤول الذي ينشئ اشتراك هذا الوصول ضمنيا، والقدرة على تعيين مسؤولي آخرين لدور المساهم.

- أذونات **Microsoft 365** لكل مخزن مفاتيح تستخدمه لمفتاح العميل، ستحتاج إلى منح wrapKey، إلغاء الاختصار، والحصول على الأذونات إلى Microsoft 365 أساسي الخدمة. 

  لإعطاء الإذن Microsoft 365 أساسي للخدمة، قم بتشغيل الأمر **Set-AzKeyVaultAccessPolicy** cmdlet باستخدام بناء الجملة التالي:

   ```powershell
   Set-AzKeyVaultAccessPolicy -VaultName <vault name> -PermissionsToKeys wrapKey,unwrapKey,get -ServicePrincipalName <Office 365 appID>
   ```

   المكان:

   - *اسم المخزن* هو اسم المخزن الرئيسي الذي أنشأته.
   - بالنسبة Exchange Online Skype for Business، *استبدل Office 365 appID* ب`00000002-0000-0ff1-ce00-000000000000`
   - بالنسبة SharePoint عبر الإنترنت OneDrive for Business و Teams، *استبدل Office 365 appID* ب`00000003-0000-0ff1-ce00-000000000000`
   - بالنسبة إلى نهج حمل العمل المتعدد (Exchange Teams وMIP EDM) الذي ينطبق على جميع المستخدمين المستأجرين، *استبدل Office 365 appID* ب`c066d759-24ae-40e7-a56f-027002b5d3e4`

  مثال: تعيين الأذونات Exchange Online Skype for Business:

   ```powershell
   Set-AzKeyVaultAccessPolicy -VaultName Contoso-CK-EX-NA-VaultA1 -PermissionsToKeys wrapKey,unwrapKey,get -ServicePrincipalName 00000002-0000-0ff1-ce00-000000000000
   ```

  مثال: تعيين الأذونات للملفات SharePoint عبر الإنترنت OneDrive for Business والأذونات Teams:

   ```powershell
   Set-AzKeyVaultAccessPolicy -VaultName Contoso-CK-SP-NA-VaultA1 -PermissionsToKeys wrapKey,unwrapKey,get -ServicePrincipalName 00000003-0000-0ff1-ce00-000000000000
   ```

### <a name="make-sure-soft-delete-is-enabled-on-your-key-vaults"></a>تأكد من تمكين الحذف الناعم على خزن المفاتيح

عندما تتمكن من استرداد المفاتيح بسرعة، يكون من غير المرجح أن تواجه انقطاعا ممتدا في الخدمة بسبب وجود مفاتيح محذوفة عن طريق الخطأ أو ضار. قم بتمكين هذا التكوين، المشار إليه ب حذف ناعم، قبل أن تتمكن من استخدام المفاتيح مع "مفتاح العميل". يسمح لك تمكين الحذف الناعم باسترداد المفاتيح أو المخزن في غضون 90 يوما من الحذف دون الحاجة إلى استعادتها من النسخة الاحتياطية.
  
لتمكين الحذف الناعم على خزن المفاتيح، أكمل الخطوات التالية:
  
1. سجل الدخول إلى اشتراكك في Azure باستخدام Windows PowerShell. للحصول على الإرشادات، راجع [تسجيل الدخول باستخدام Azure PowerShell](/powershell/azure/authenticate-azureps).

2. تشغيل [الأمر Get-AzKeyVault](/powershell/module/az.keyvault/get-azkeyvault) cmdlet. في هذا المثال، *اسم المخزن* هو اسم المخزن الرئيسي الذي تقوم بتمكين الحذف الناعم له:

   ```powershell
   $v = Get-AzKeyVault -VaultName <vault name>
   $r = Get-AzResource -ResourceId $v.ResourceId
   $r.Properties | Add-Member -MemberType NoteProperty -Name enableSoftDelete -Value 'True'
   Set-AzResource -ResourceId $r.ResourceId -Properties $r.Properties
   ```

3. تأكد من تكوين الحذف الناعم لمخزن المفاتيح عن طريق تشغيل **الأمر Get-AzKeyVault** cmdlet. إذا تم تكوين الحذف الناعم بشكل صحيح لمخزن المفاتيح، فإن الخاصية _تمكين_ الحذف الناعم ترجع قيمة **True**:

   ```powershell
   Get-AzKeyVault -VaultName <vault name> | fl
   ```

### <a name="add-a-key-to-each-key-vault-either-by-creating-or-importing-a-key"></a>إضافة مفتاح إلى كل مخزن مفاتيح إما عن طريق إنشاء مفتاح أو استيراده

هناك طريقتان لإضافة المفاتيح إلى مخزن مفاتيح Azure؛ يمكنك إنشاء مفتاح مباشرة في "مخزن المفاتيح"، أو يمكنك استيراد مفتاح. إن إنشاء مفتاح مباشرة في "مخزن المفاتيح" أقل تعقيدا، ولكن استيراد مفتاح يوفر التحكم الكامل في كيفية إنشاء المفتاح. استخدم مفاتيح RSA. لا يدعم Azure Key Vault التفاف المفاتيح وإبطالها باستخدام مفاتيح المنحنى الشكلي.
  
لإنشاء مفتاح مباشرة في مخزن المفاتيح، قم بتشغيل [cmdlet Add-AzKeyVaultKey](/powershell/module/az.keyvault/add-azkeyvaultkey) كما يلي:
  
```powershell
Add-AzKeyVaultKey -VaultName <vault name> -Name <key name> -Destination <HSM|Software> -KeyOps wrapKey,unwrapKey
```

المكان:

- *اسم المخزن* هو اسم مخزن المفاتيح الذي تريد إنشاء المفتاح فيه.

- *اسم المفتاح* هو الاسم الذي تريد منحه المفتاح الجديد.

  > [!TIP]
  > مفاتيح الاسم التي تستخدم اصطلاح تسمية مماثل كما هو موضح أعلاه لأخزنات المفاتيح. بهذه الطريقة، في الأدوات التي تظهر اسم المفتاح فقط، تكون السلسلة ذات وصف ذاتي.
  
إذا كنت تنوي حماية المفتاح باستخدام HSM، فتأكد من تحديد **HSM** كقيمة للمعلمة _الوجهة_ ، وإلا، فحدد **البرامج**.

على سبيل المثال:
  
```powershell
Add-AzKeyVaultKey -VaultName Contoso-CK-EX-NA-VaultA1 -Name Contoso-CK-EX-NA-VaultA1-Key001 -Destination HSM -KeyOps wrapKey,unwrapKey
```

لاستيراد مفتاح مباشرة إلى مخزن المفاتيح، يجب أن يكون لديك وحدة نمطية nCipher nShield لأمن الأجهزة.
  
تفضل بعض المؤسسات هذا النهج لإنشاء مصدر مفاتيحها، ثم يوفر هذا الأسلوب أيضا إثباتات:
  
- تتضمن مجموعة الأدوات المستخدمة في الاستيراد شهادة من nCipher بأن مفتاح Exchange Key (KEK) المستخدم لتشفير المفتاح الذي تقوم بتوليده غير قابل للتصدير، وقد تم إنشاؤه داخل HSM أصلي تم تصنيعه بواسطة nCipher.

- تتضمن مجموعة الأدوات شهادة من nCipher بأن عالم أمان المخزن الرئيسي ل Azure تم إنشاؤه أيضا على HSM أصلي تم تصنيعه بواسطة nCipher. تثبت هذه الشهادة أن Microsoft تستخدم أيضا أجهزة nCipher الأصلية.

تحقق من مجموعة الأمان لديك لتحديد ما إذا كانت الصدقات أعلاه مطلوبة. للحصول على خطوات مفصلة لإنشاء مفتاح في الموقع واستيراده إلى مخزن المفاتيح، راجع كيفية إنشاء مفاتيح [محمية HSM ونقلها ل Azure Key Vault](/azure/key-vault/keys/hsm-protected-keys). استخدم إرشادات Azure لإنشاء مفتاح في كل مخزن مفاتيح.
  
### <a name="check-the-recovery-level-of-your-keys"></a>التحقق من مستوى استرداد المفاتيح

Microsoft 365 تعيين اشتراك Azure Key Vault إلى "عدم الإلغاء" وتمكين الحذف الناعم للمفاتيح المستخدمة بواسطة "مفتاح العميل". يمكنك تأكيد إعدادات الاشتراكات بالنظر إلى مستوى الاسترداد على المفاتيح.
  
للتحقق من مستوى استرداد أحد المفاتيح، في Azure PowerShell، قم بتشغيل Get-AzKeyVaultKey cmdlet كما يلي:
  
```powershell
(Get-AzKeyVaultKey -VaultName <vault name> -Name <key name>).Attributes
```

إذا كانت  الخاصية مستوى الاسترداد ترجع أي شيء آخر غير قيمة **Recoverable+ProtectedSubscription**، فتأكد من وضع الاشتراك في القائمة عدم الإلغاء ومن تمكين الحذف الناعم على كل مخزن من خزن المفاتيح.
  
### <a name="back-up-azure-key-vault"></a>ارجع إلى مخزن مفاتيح Azure

بعد إنشاء مفتاح أو تغييره مباشرة، قم بإجراء نسخة احتياطية من النسخة الاحتياطية وتخزينها، سواء عبر الإنترنت أو بدون اتصال. لا تتصل بنسخ غير متصلة بأي شبكة. بدلا من ذلك، قم بتخزينها في موقع غير متصل، مثل مرفق تخزين تجاري أو آمن. يجب تخزين نسخة واحدة على الأقل من النسخة الاحتياطية في موقع يمكن الوصول إليه في حالة حدوث كارثة. إن العناصر النقطية الاحتياطية هي الوسيلة الوحيدة لاستعادة المواد الأساسية إذا تم إتلاف مفتاح "المخزن الرئيسي" بشكل دائم أو عرضه بطريقة أخرى غير قابلة للاستخدام. لا تتأهل المفاتيح الخارجية لخزنة مفاتيح Azure والمستوردة إلى مخزن مفاتيح Azure ك نسخة احتياطية لأن بيانات التعريف الضرورية لمفتاح العميل لاستخدام المفتاح غير موجودة مع المفتاح الخارجي. يمكن استخدام النسخة الاحتياطية التي تم أخذها من مخزن مفاتيح Azure فقط لعمليات الاستعادة باستخدام "مفتاح العميل". لذلك، يجب إنشاء نسخة احتياطية من مخزن مفاتيح Azure بعد تحميل مفتاح أو إنشائه.
  
لإنشاء نسخة احتياطية لمفتاح Azure Key Vault، قم بتشغيل cmdlet [Backup-AzKeyVaultKey](/powershell/module/az.keyvault/backup-azkeyvaultkey) كما يلي:

```powershell
Backup-AzKeyVaultKey -VaultName <vault name> -Name <key name>
-OutputFile <filename.backup>
```

تأكد من أن ملف الإخراج يستخدم اللاحقة `.backup`.
  
يتم تشفير ملف الإخراج الناتج عن أمر cmdlet هذا ولا يمكن استخدامه خارج مخزن مفاتيح Azure. لا يمكن استعادة النسخة الاحتياطية إلا إلى اشتراك Azure الذي تم أخذ النسخة الاحتياطية منه.
  
> [!TIP]
> بالنسبة لملف الإخراج، اختر مجموعة من اسم المخزن واسم المفتاح. سيجعل هذا اسم الملف وصفا ذاتيا. كما سيضمن عدم اصطدام أسماء ملفات النسخ الاحتياطي.
  
على سبيل المثال:
  
```powershell
Backup-AzKeyVaultKey -VaultName Contoso-CK-EX-NA-VaultA1 -Name Contoso-CK-EX-NA-VaultA1-Key001 -OutputFile Contoso-CK-EX-NA-VaultA1-Key001-Backup-20170802.backup
```

### <a name="validate-azure-key-vault-configuration-settings"></a>التحقق من صحة إعدادات تكوين مخزن المفاتيح في Azure

إن التحقق من صحة المفاتيح قبل استخدام المفاتيح في DEP اختياري، ولكن يوصى به بشدة. إذا كنت تستخدم خطوات لإعداد المفاتيح والمخزنات غير تلك الموضحة في هذه المقالة، فتحقق من صحة موارد مخزن مفاتيح Azure قبل تكوين "مفتاح العميل".
  
للتحقق من تمكين المفاتيح والعمليات`get``wrapKey``unwrapKey`:
  
تشغيل [Cmdlet Get-AzKeyVault](/powershell/module/az.keyvault/get-azkeyvault) كما يلي:
  
```powershell
Get-AzKeyVault -VaultName <vault name>
```

في الإخراج، ابحث عن نهج Access والهوية Exchange Online (GUID) أو SharePoint عبر الإنترنت (GUID) كما هو مناسب. يجب أن تظهر الأذونات الثلاثة أعلاه ضمن أذونات المفاتيح.
  
إذا كان تكوين نهج الوصول غير صحيح، فدير Set-AzKeyVaultAccessPolicy cmdlet كما يلي:
  
```powershell
Set-AzKeyVaultAccessPolicy -VaultName <vault name> -PermissionsToKeys wrapKey,unwrapKey,get -ServicePrincipalName <Office 365 appID>
```

على سبيل المثال، Exchange Online Skype for Business:
  
```powershell
Set-AzKeyVaultAccessPolicy -VaultName Contoso-CK-EX-NA-VaultA1 
-PermissionsToKeys wrapKey,unwrapKey,get -ServicePrincipalName 00000002-0000-0ff1-ce00-000000000000
```

على سبيل المثال، SharePoint عبر الإنترنت OneDrive for Business:
  
```powershell
Set-AzKeyVaultAccessPolicy -VaultName Contoso-CK-SP-NA-VaultA1
-PermissionsToKeys wrapKey,unwrapKey,get -ServicePrincipalName 00000003-0000-0ff1-ce00-000000000000
```

للتحقق من عدم تعيين تاريخ انتهاء صلاحية للمفاتيح، قم بتشغيل [الأمر Cmdlet Get-AzKeyVaultKey](/powershell/module/az.keyvault/get-azkeyvault) كما يلي:
  
```powershell
Get-AzKeyVaultKey -VaultName <vault name>
```

لا يمكن لمفتاح العميل استخدام مفتاح منتهية الصلاحية. ستفشل العمليات التي تحاول باستخدام مفتاح منتهية الصلاحية، وقد تؤدي إلى انقطاع الخدمة. نوصي بشدة بعدم وجود تاريخ انتهاء صلاحية المفاتيح المستخدمة مع "مفتاح العميل". لا يمكن إزالة تاريخ انتهاء الصلاحية، بمجرد تعيينه، ولكن يمكن تغييره إلى تاريخ مختلف. إذا كان يجب استخدام مفتاح له مجموعة تاريخ انتهاء صلاحية، فغير قيمة انتهاء الصلاحية إلى 9999/12/31. لن تجتاز المفاتيح التي تم تعيين تاريخ انتهاء صلاحيتها إلى تاريخ آخر غير 31/12/9999 Microsoft 365 التحقق من الصحة.
  
لتغيير تاريخ انتهاء الصلاحية الذي تم تعيينه إلى أي قيمة أخرى غير 12/31/9999، قم بتشغيل [cmdlet Update-AzKeyVaultKey](/powershell/module/az.keyvault/update-azkeyvaultkey) كما يلي:
  
```powershell
Update-AzKeyVaultKey -VaultName <vault name> -Name <key name> -Expires (Get-Date -Date "12/31/9999")
```

> [!CAUTION]
> لا تقوم بتعيين تواريخ انتهاء الصلاحية على مفاتيح التشفير التي تستخدمها مع "مفتاح العميل".
  
### <a name="obtain-the-uri-for-each-azure-key-vault-key"></a>الحصول على URI لكل مفتاح مخزن مفاتيح Azure

بعد إعداد خزنات المفاتيح وإضافة المفاتيح، قم بتشغيل الأمر التالي للحصول على URI للمفتاح في كل مخزن مفاتيح. سوف تستخدم URIs هذه عند إنشاء كل DEP وتعيينه في وقت لاحق، لذا احفظ هذه المعلومات في مكان آمن. تشغيل هذا الأمر مرة واحدة لكل مخزن مفاتيح.
  
في Azure PowerShell:
  
```powershell
(Get-AzKeyVaultKey -VaultName <vault name>).Id
```

## <a name="next-steps"></a>الخطوات التالية

بعد إكمال الخطوات في هذه المقالة، تكون جاهزا لإنشاء DEPs وتعيينها. للحصول على الإرشادات، راجع [إدارة مفتاح العميل](customer-key-manage.md).

## <a name="related-articles"></a>المقالات ذات الصلة

- [تشفير الخدمة باستخدام "مفتاح العميل"](customer-key-overview.md)

- [إدارة مفتاح العميل](customer-key-manage.md)

- [لف مفتاح عميل أو مفتاح توفر أو تدويره](customer-key-availability-key-roll.md)

- [التعرف على مفتاح التوفر](customer-key-availability-key-understand.md)

- [تشفير الخدمة](office-365-service-encryption.md)