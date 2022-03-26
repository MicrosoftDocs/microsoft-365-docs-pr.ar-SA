---
title: تكوين "علبة وارد مركز عليه" لجميع الأشخاص في مؤسستك
f1.keywords:
- NOCSH
ms.author: kwekua
author: kwekua
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: high
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
ms.custom:
- AdminSurgePortfolio
- AdminTemplateSet
- admindeeplinkMAC
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: 613a845c-4b71-41de-b331-acdcf5b6625d
description: إذا كنت مسؤولا عن تكوين إعدادات البريد الإلكتروني لكل شخص في شركة، تشرح هذه المقالة كيفية تكوين "علبة وارد مركز عليه" للمستخدمين.
ms.openlocfilehash: b2c315b6fb4a4c80f245bcf4731b93996753586a
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 10/06/2021
ms.locfileid: "63571058"
---
# <a name="configure-focused-inbox-for-everyone-in-your-organization"></a>تكوين "علبة وارد مركز عليه" لجميع الأشخاص في مؤسستك

إذا كنت مسؤولا عن تكوين طريقة عمل البريد الإلكتروني للجميع في شركة، فإن هذه المقالة لك! وهو يشرح كيفية تخصيصه أو إيقاف تشغيله للأعمال، ويجيب على الأسئلة التي يتم [طرحها بشكل متكرر](#faq-for-focused-inbox).

إذا كنت تريد إيقاف تشغيل "علبة وارد مركز عليه" لنفسك فقط، فالرجاء الاطلاع على [إيقاف تشغيل "علبة وارد مركز عليه](https://support.microsoft.com/office/f714d94d-9e63-4217-9ccb-6cb2986aa1b2)".  

إذا كنت تريد التأكد من أن المستخدمين يتلقون رسائل بريد إلكتروني خاصة بأعمال معينة، على سبيل المثال، من الموارد البشرية أو كشف المرتبات، يمكنك تكوين "علبة وارد مركز عليه" بحيث تصل هذه الرسائل إلى طريقة العرض "مركز عليه". يمكنك أيضا التحكم في ما إذا كان المستخدمون في مؤسستك يرون "علبة وارد مركز عليه" في علبة البريد الخاصة بهم.
  
## <a name="turn-focused-inbox-on-or-off-in-your-organization"></a>تشغيل "علبة وارد مركز عليه" أو إيقاف تشغيلها في مؤسستك

يمكنك استخدام PowerShell ل تشغيل "علبة وارد مركز عليه" أو إيقاف تشغيلها لجميع الأشخاص في مؤسستك. هل تريد القيام بذلك في مركز مسؤولي Microsoft 365؟ أعلم فريق الهندسة لدينا. **[التصويت هنا!](https://go.microsoft.com/fwlink/?linkid=862489)**
  
**إيقاف تشغيل "علبة وارد مركز عليه":**
  
في مثال PowerShell التالي، يتم إيقاف تشغيل "علبة وارد مركز **عليه" في** مؤسستك. ومع ذلك، فهو لا يمنع توفر الميزة للمستخدمين. إذا أرادوا ذلك، يمكنهم إعادة تمكين "علبة وارد مركز عليه" مرة أخرى على كل عميل من عملائهم. 
  
1. [الاتصال إلى Exchange Online PowerShell عن بعد](/powershell/exchange/connect-to-exchange-online-powershell).

2. يجب تعيين أذونات لك قبل تنفيذ هذا الإجراء أو الإجراءات. لمعرفة الأذونات التي تحتاج إليها، راجع إدخال "قواعد النقل" في نهج المراسلة وأذونات [التوافق](/exchange/messaging-policy-and-compliance-permissions-exchange-2013-help).

3. تشغيل **الأمر Cmdlet Get-OrganizationConfig** . 

    ```powershell
    Get-OrganizationConfig
    ```

4. ابحث عن **FocusedInboxOn** لعرض الإعداد الحالي الخاص به: 

    ![استجابة من PowerShell حول حالة "علبة وارد مركز عليه".](../../media/419d8caa-89b9-45c5-91d9-8c023297456e.png)
  
5. قم بتشغيل الأمر cmdlet التالي لتشغيل "علبة وارد المركز عليه".

    ```powershell
    Set-OrganizationConfig -FocusedInboxOn $false
    ```

6. قم بتشغيل **أمر cmdlet Get-OrganizationConfig** مرة أخرى وسترى أنه تم تعيين FocusedInboxOn $false، مما يعني أنه تم إيقاف تشغيله. 

**تشغيل "علبة وارد مركز عليه":**
  
- في الخطوة 5 أعلاه، قم بتشغيل الأمر cmdlet التالي لتشغيل "علبة وارد المركز عليه".

  ```powershell
  Set-OrganizationConfig -FocusedInboxOn $true
  ```
    
## <a name="what-do-users-see-after-i-turn-on-focused-inbox"></a>ما الذي يراه المستخدمون بعد تشغيل "علبة وارد مركز عليه"؟

لن يرى المستخدمون طريقة العرض "مركز عليه" إلا بعد إغلاقهم وإعادة Outlook. عند إعادة Outlook، سيشاهدون تلميحا في Outlook المستخدم يعطيهم خيار استخدام علبة وارد "مركز عليه" الجديدة.
  
![صورة لما تبدو عليه علبة وارد المركز عليه عند فتح المستخدم لأول مرة Outlook على ويب.](../../media/f6ef79e7-0f4c-4a23-b6f0-7c15d927b5f0.png)
  
إذا كنت تقوم بالتبديل من "بريد غير صحيح" إلى "علبة وارد مركز عليه"، يمكنهم أن يقرروا تمكينها ("جرب ذلك") أو استبعاد الميزة. إذا كان لدى المستخدم عدة عملاء (معتمدين)، يمكنهم تمكين/تعطيل "علبة وارد مركز عليه" بشكل فردي على كل منها. يبدو التلميح كما يلي:
  
![صورة لما تبدو عليه "علبة وارد مركز عليه" عند طرحها للمستخدمين Outlook فتحها.](../../media/c034f969-d650-4333-88f1-dd10ade0a94c.png)
  
عندما يقرر المستخدم بدء استخدام "علبة وارد مركز عليه"، يتم تعطيل البريد الإلكتروني بشكل تلقائي. يتم تحويل مجلد البريد العشوائي إلى مجلد قياسي يسمح للمستخدم بإعادة تسميته أو حذفه.
  
## <a name="turn-focused-inbox-on-or-off-for-specific-users"></a>تشغيل "علبة وارد مركز عليه" أو إيقاف تشغيلها لمستخدمين محددين

في هذا المثال، يتم إيقاف تشغيل "علبة وارد مركز **عليه** " ل Tim Matthews في مؤسسة Contoso. ومع ذلك، فإنه لا يمنع توفر الميزة له. إذا أراد ذلك، لا يزال يمكنه إعادة تمكين "علبة وارد مركز عليه" مرة أخرى لكل عميل من عملائه. 
  
1. [الاتصال إلى Exchange Online PowerShell عن بعد](/powershell/exchange/connect-to-exchange-online-powershell).

2. يجب تعيين أذونات لك قبل تنفيذ هذا الإجراء أو الإجراءات. لمعرفة الأذونات التي تحتاج إليها، راجع إدخال "قواعد النقل" في موضوع أذونات التوافق ون نهج المراسلة.

3. تشغيل **cmdlet Get-FocusedInbox** ، على سبيل المثال: 

    ```powershell
    Get-FocusedInbox -Identity <tim@contoso.com>
    ```

4. ابحث عن FocusedInboxOn لعرض الإعداد الحالي الخاص به:

    ![استجابة من PowerShell حول حالة "علبة وارد مركز عليه".](../../media/419d8caa-89b9-45c5-91d9-8c023297456e.png)
  
5. قم بتشغيل cmdlet التالي لتشغيل "علبة وارد المركز عليه":

    ```powershell
    Set-FocusedInbox -Identity <tim@contoso.com> -FocusedInboxOn $false
    ```

    أو، قم بتشغيل الأمر cmdlet التالي لتشغيله:

    ```powershell
    Set-FocusedInbox -Identity <tim@contoso.com> -FocusedInboxOn $true
    ```

## <a name="use-the-ui-to-create-a-transport-rule-to-direct-email-messages-to-the-focused-view-for-all-your-users"></a>استخدام واجهة المستخدم لإنشاء قاعدة نقل لتوجيه رسائل البريد الإلكتروني إلى طريقة العرض "مركز عليه" لجميع المستخدمين

1. انتقل إلى Exchange <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">الإدارة</a>.

2. انتقل إلى **قواعد تدفق** \> **البريد**. حدد أيقونة ![إضافة EAC.](../../media/795e5bdd-48bb-433f-8e07-3c7a19f8eca2.gif) ثم حدد **إنشاء قاعدة جديدة...**. 

3. بعد أن تنجز عملية إنشاء القاعدة الجديدة، حدد **حفظ** لبدء تشغيل القاعدة.

    تعرض الصورة التالية مثالا يتم فيه تسليم كل الرسائل من "قسم كشف المرتبات" إلى "علبة وارد مركز عليه".

    ![كشف المرتبات في مربع التركيز.](../../media/focusedinbox-transport-rule.PNG)

    > [!NOTE]
    > نص قيمة رأس الرسالة في هذا المثال هو **X-MS-Exchange-Organization-BypassFocusedInbox**.
  
## <a name="use-powershell-to-create-a-transport-rule-to-direct-email-messages-to-the-focused-view-for-all-your-users"></a>استخدام PowerShell لإنشاء قاعدة نقل لتوجيه رسائل البريد الإلكتروني إلى طريقة العرض "مركز عليه" لجميع المستخدمين

1. [الاتصال إلى Exchange Online PowerShell عن بعد](/powershell/exchange/connect-to-exchange-online-powershell).

2. يجب تعيين أذونات لك قبل تنفيذ هذا الإجراء أو الإجراءات. لمعرفة الأذونات التي تحتاج إليها، راجع إدخال "قواعد النقل" في نهج المراسلة وأذونات [التوافق](/exchange/messaging-policy-and-compliance-permissions-exchange-2013-help).

3. تشغيل الأمر التالي للسماح بتسليم كل الرسائل من "قسم كشف المرتبات"، على سبيل المثال، إلى "علبة وارد مركز عليه".

    ```powershell
    New-TransportRule -Name <name_of_the_rule> -From "Payroll Department" -SetHeaderName "X-MS-Exchange-Organization-BypassFocusedInbox" -SetHeaderValue "true"
    ```

> [!IMPORTANT]
> في هذا المثال، تكون كل من "X-MS-Exchange-Organization-BypassFocusedInbox" و"true" حساسة لالحالتين.
> بالإضافة إلى ذلك، ستحترم "علبة وارد مركز عليه" رأس X الذي يتخطى البريد الإلكتروني، وبالتالي إذا استخدمت هذا الإعداد في البريد الإلكتروني، سيتم استخدامه في "علبة وارد مركز عليه". للحصول على معلومات مفصلة حول بناء الجملة والمعلمات، راجع [New-TransportRule](/powershell/module/exchange/new-transportrule).

### <a name="how-do-you-know-this-worked"></a>كيف يمكنك معرفة كيفية عمل ذلك؟

يمكنك التحقق من رؤوس رسائل البريد الإلكتروني لمعرفة ما إذا كانت رسائل البريد الإلكتروني منتقلة إلى علبة الوارد بسبب تجاوز قاعدة نقل "علبة وارد مركز عليه". اختر رسالة بريد إلكتروني من علبة بريد في مؤسستك تم تطبيق قاعدة نقل "علبة وارد مركز عليه". انظر إلى رؤوس الرسالة التي تم طابعها، ويجب أن ترى **X-MS-Exchange-Organization-BypassFocusedInbox: رأس** صحيح. وهذا يعني أن التجاوز يعمل. راجع المقالة [عرض معلومات رأس الإنترنت لرسالة](https://go.microsoft.com/fwlink/p/?LinkId=822530) بريد إلكتروني للحصول على معلومات حول كيفية العثور على معلومات الرأس.

### <a name="what-will-the-user-see"></a>ما الذي سيشاهده المستخدم؟

إذا كانت هناك قاعدة نقل في مكانها، سيتم عرض إعلام للتجاوز. Outlook على ويب تعطيل الخيار "الانتقال دائما إلى أخرى" وإظهار تنقيط الأداة. Outlook العملاء على سطح المكتب تحديد "الانتقال دائما إلى أخرى" وسينبثق مربع حوار.

## <a name="turn-onoff-clutter"></a>تشغيل/إيقاف تشغيل "الفوضى"

لقد تلقينا تقارير بأن "الفوضى" توقفت فجأة عن العمل لبعض المستخدمين. إذا حدث ذلك، يمكنك تمكينه مرة أخرى لمستخدمين محددين. راجع [تكوين "الفوضى" لمنظمتك](../email/configure-clutter.md).

## <a name="faq-for-focused-inbox"></a>الأسئلة الشائعة حول "علبة وارد مركز عليه"

فيما يلي إجابات على الأسئلة التي يتم طرحها بشكل متكرر حول "علبة وارد مركز عليه".

### <a name="can-i-control-how-i-roll-out-focused-inbox-in-my-organization"></a>هل يمكنني التحكم في كيفية طرح "علبة وارد مركز عليه" في المؤسسة؟

نعم. يمكنك تشغيل "علبة وارد مركز عليه" أو إيقاف تشغيلها لمنظمتك بكاملها، أو يمكنك تشغيلها أو إيقاف تشغيلها لمستخدمين محددين. انظر أعلاه.
  
### <a name="is-the-focused-inbox-feature-only-available-for-office-2016-clients"></a>هل تتوفر ميزة "علبة وارد التركيز" فقط لعملاء Office 2016؟

نعم، لا يتأثر Office سوى المستخدمين الذين لديهم Office 2016. لن يتم تقديم هذه الميزة Outlook 2013 أو أي وقت سابق.
  
### <a name="how-long-does-it-take-for-focused-inbox-changes-to-take-place-in-outlook"></a>ما المدة التي يستغرقها إجراء تغييرات "علبة وارد المركز عليه" في Outlook؟

بمجرد تشغيل "علبة وارد مركز عليه" أو إيقاف تشغيلها، سيتم تطبيق الإعدادات بمجرد إغلاق المستخدمين وإعادة Outlook.
  
### <a name="what-happens-to-clutter-once-i-turn-on-focused-inbox"></a>ماذا يحدث للتكدث بمجرد تشغيل "علبة وارد مركز عليه"؟

بعد التبديل، لن تتلقى بعد الآن بريدا إلكترونيا أقل قابلا للتنفيذ في مجلد البريد العشوائي. بدلا من ذلك، سيتم تقسيم البريد الإلكتروني بين علامات التبويب "مركز عليه" و"أخرى" في علبة الوارد. الخوارزمية نفسها التي نقلت العناصر إلى مجلد "البريد العشوائي" الآن هي التي تسلط "علبة وارد مركز عليه"، مما يعني أنه سيتم الآن نقل أي رسائل بريد إلكتروني تم تعيينها للانتقال إلى البريد الإلكتروني "بريد غير الهام" إلى "أخرى". ستبقى أي رسائل موجودة بالفعل في مجلد البريد العشوائي هناك حتى تقرر حذفها أو نقلها.
  
اطلع على هذا المنشور الذي أعده [طوني ريدموند](https://www.petri.com/author/tony-redmond)، Microsoft MVP: كيف تستبدل علبة وارد مركز عليه البريد غير المزدحم [داخل](https://www.petri.com/focused-inbox-office-365) Office 365.
  
### <a name="can-i-keep-users-on-clutter-what-is-microsofts-recommendation-when-it-comes-to-using-clutter-vs-focused-inbox"></a>هل يمكنني إبقاء المستخدمين على "الفوضى"؟ ما هي توصية Microsoft عندما يتعلق الأمر باستخدام البريد الإلكتروني غير المعبأ مقابل "علبة وارد مركز عليه"؟

نعم، يمكنك إبقاء المستخدمين على البريد البريدي وتعطيل "علبة وارد مركز عليه"، ومع ذلك، سيتم استبدال "البريد البريدي" بشكل كامل في النهاية ب "علبة وارد مركز عليه"، لذا توصي Microsoft بالتنقل إلى "علبة وارد مركز عليه" الآن. لمعرفة المزيد حول عند استخدام البريد Exchange Online، راجع منشور المدونة هذا: تحديث على "علبة وارد مركز عليه" وخططنا [للتكدث](https://techcommunity.microsoft.com/t5/Outlook-Blog/Update-on-Focused-Inbox-and-our-plans-for-Clutter/ba-p/136448).
  
### <a name="should-i-disable-clutter-for-my-end-users-if-we-are-going-to-move-everyone-to-focused-inbox"></a>هل يجب تعطيل البريد الإلكتروني للمستخدمين النهائيين إذا كنا سننقل الجميع إلى "علبة وارد مركز عليه"؟

لا. من الممكن تعطيل البريد البريدي لعلبة بريد بشكل صريح عن طريق تشغيل Set-Clutter cmdlet. ومع ذلك، إذا قمت بذلك، سيشاهد مالك علبة البريد الرسائل التي تمت إعادة توجيهها مسبقا إلى مجلد البريد العشوائي تبقى في علبة الوارد وسيترتب عليه معالجة هذه الرسائل حتى تتم ترقية عميله إلى إصدار يدعم "علبة وارد مركز عليه". لذلك من الأفضل عدم تعطيل ميزة "الفوضى" حتى يتوفر العملاء الذين تمت ترقيتها.
  
### <a name="why-are-there-two-different-cmdlets-for-managing-focused-inbox"></a>لماذا يوجد اثنين من cmdlets مختلفين لإدارة "علبة وارد المركز عليه"؟

هناك اثنتان من اثنتين مقترنتين ب "علبة وارد مركز عليه".
  
- **مستوى المؤسسة**: حالة علبة وارد مركز عليه، وطوابع وقت التحديث الأخيرة المقترنة.

- **مستوى علبة البريد**: حالة علبة وارد مركز عليها، وطوابع وقت التحديث الأخير المقترنة 

### <a name="how-does-outlook-decide-to-show-the-focused-inbox-experience-with-these-two-states"></a>كيف Outlook عرض تجربة "علبة وارد مركز عليه" مع هاتين اثنتين؟

Outlook عرض التجربة عن طريق اختيار أمر cmdlet الذي له الطابع الزمني الأخير. بشكل افتراضي، يكون كلا الطابعين الزمنيين "null" وفي هذه الحالة، يتم تمكين الميزة.
  
### <a name="why-does-the-get-focusedinbox-cmdlet-return-true-when-ive-turned-focused-inbox-off-in-my-organization"></a>لماذا يقوم Get-FocusedInbox cmdlet بإرجاع "true"، عندما قمت ب إيقاف تشغيل "علبة وارد المركز عليه" في المؤسسة؟

هناك اثنين من cmdlets للتحكم في "علبة وارد المركز عليه". عند تشغيل Get-FocusedInbox علبة بريد، فإنه يرجع حالة مستوى علبة البريد للميزة. يتم اختيار Outlook استنادا إلى حالة cmdlet التي تم تعديلها آخر مرة.
  
### <a name="can-i-run-a-script-to-see-who-has-turned-on-focused-inbox"></a>هل يمكنني تشغيل برنامج نصي لمعرفة من قام بتشغيل "علبة وارد مركز عليه"؟

لا، وهذا حسب التصميم. تمكين علبة وارد المركز عليه هو إعداد من جانب العميل، لذا كل ما يمكن أن يقوم به cmdlet هو إخبارك ما إذا كانت علبة بريد المستخدم مؤهلة لتجربة العميل. من الممكن تمكينه في الوقت نفسه في بعض العملاء وتعطيل الآخرين، على سبيل المثال، تمكينه في تطبيق Outlook وهاتف Outlook المحمول ولكن معطل في Outlook على ويب.

## <a name="related-content"></a>المحتوى ذي الصلة

[تكوين "الفوضى" لمنظمتك](../email/configure-clutter.md) (مقالة)\
[تكوين إعدادات علبة البريد المشتركة](../email/configure-a-shared-mailbox.md) (مقالة)\
[إنشاء التواقيع وإفراج المسؤولية](create-signatures-and-disclaimers.md) (فيديو)
