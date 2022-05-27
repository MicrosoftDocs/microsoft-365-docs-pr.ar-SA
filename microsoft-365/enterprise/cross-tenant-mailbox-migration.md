---
title: ترحيل علبة بريد عبر المستأجرين
description: كيفية نقل علب البريد بين المستأجرين Microsoft 365 أو Office 365.
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.prod: microsoft-365-enterprise
ms.topic: article
f1.keywords:
- NOCSH
ms.date: 05/05/2022
ms.reviewer: georgiah
ms.custom:
- it-pro
- admindeeplinkMAC
- admindeeplinkEXCHANGE
ms.collection:
- M365-subscription-management
ms.openlocfilehash: b2d66fce2b1eeffa4500c01a07f271b5b1a96ab7
ms.sourcegitcommit: 6a981ca15bac84adbbed67341c89235029aad476
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 05/27/2022
ms.locfileid: "65754765"
---
# <a name="cross-tenant-mailbox-migration-preview"></a>ترحيل علبة بريد عبر المستأجرين (معاينة)

عادة، في أثناء عمليات الدمج أو التباعد، تحتاج إلى القدرة على نقل علبة بريد المستخدم Exchange Online إلى مستأجر جديد. يسمح ترحيل علبة البريد عبر المستأجرين لمسؤولي المستأجرين باستخدام واجهات معروفة مثل Remote PowerShell وSED لانتقال المستخدمين إلى مؤسستهم الجديدة.

يمكن للمسؤولين استخدام أمر cmdlet New-MigrationBatch، المتوفر من خلال دور إدارة Move Mailboxes، لتنفيذ عمليات النقل عبر المستأجرين.

يجب أن يكون ترحيل المستخدمين موجودا في نظام Exchange Online المستأجر الهدف كمستخدمي البريد، مع وضع علامة على سمات معينة لتمكين عمليات النقل عبر المستأجرين. سيفشل النظام في النقل للمستخدمين الذين لم يتم إعدادهم بشكل صحيح في المستأجر الهدف.

عند اكتمال عمليات النقل، يتم تحويل علبة بريد المستخدم المصدر إلى MailUser ويتم وضع طابع على targetAddress (الظاهر ك ExternalEmailAddress في Exchange) بعنوان التوجيه إلى المستأجر الوجهة. تترك هذه العملية MailUser القديم في المستأجر المصدر وتسمح بالتوافق وتوجيه البريد. عندما تسمح عمليات العمل، قد يقوم المستأجر المصدر بإزالة MailUser المصدر أو تحويله إلى جهة اتصال بريد.

يتم دعم عمليات ترحيل علب بريد Exchange عبر المستأجرين للمستأجرين في مجموعة مختلطة أو سحابية فقط، أو أي تركيبة من الاثنين.

تصف هذه المقالة عملية نقل علب البريد عبر المستأجرين وتوفر إرشادات حول كيفية إعداد المستأجرين المصدر والهدف لعمليات نقل محتوى علبة البريد Exchange Online.

   > [!NOTE]
   > لقد قمنا مؤخرا بتحديث خطوات الإعداد لتمكين ترحيل علبة البريد عبر المستأجرين حتى لا يتطلب Azure Key Vault! إذا كانت هذه هي المرة الأولى التي تقوم فيها بإلحاقك بهذه المعاينة، فلا يلزم اتخاذ أي إجراء، ويمكنك المضي قدما واتباع الخطوات المفصلة في هذا المستند. إذا بدأت في تكوين المستأجرين باستخدام أسلوب AKV السابق، نوصي بشدة بإيقاف هذا التكوين أو إزالته لبدء استخدام هذا الأسلوب الجديد. إذا كانت عمليات ترحيل علبة البريد قيد التقدم باستخدام أسلوب AKV السابق، فالرجاء الانتظار حتى تكتمل عمليات الترحيل الحالية واتباع الخطوات أدناه لتمكين الأسلوب المبسط الجديد. تتم أرشفة خطوات إعداد Azure Key Vault المطلوبة ولكن يمكن العثور عليها **[هنا](https://github.com/microsoft/cross-tenant/wiki/V1-Content#cross-tenant-mailbox-migration-preview)**، للرجوع إليها.

## <a name="preparing-source-and-target-tenants"></a>إعداد المستأجرين المصدر والهدف

### <a name="prerequisites-for-source-and-target-tenants"></a>المتطلبات الأساسية للمستأجرين المصدر والهدف

قبل البدء، تأكد من أن لديك الأذونات اللازمة لتكوين تطبيق Move Mailbox في Azure وEXO Migration Endpoint وEXO Organization Relationship.

بالإضافة إلى ذلك، يلزم وجود مجموعة أمان واحدة على الأقل ممكنة للبريد في المستأجر المصدر. تستخدم هذه المجموعات لتحديد نطاق قائمة علب البريد التي يمكن أن تنتقل من مستأجر المصدر (أو يشار إليه أحيانا كمورد) إلى المستأجر الهدف. يسمح هذا لمسؤول المستأجر المصدر بتقييد أو تحديد نطاق مجموعة محددة من علب البريد التي تحتاج إلى نقل، مما يمنع المستخدمين غير المقصودين من الترحيل. المجموعات المتداخلة غير معتمدة.

ستحتاج أيضا إلى التواصل مع شركتك الشريكة الموثوق بها (التي ستقوم بنقل علب البريد معها) للحصول على معرف المستأجر Microsoft 365. يتم استخدام معرف المستأجر هذا في الحقل "اسم مجال علاقة المؤسسة".

للحصول على معرف المستأجر للاشتراك، سجل الدخول إلى [مركز مسؤولي Microsoft 365](https://go.microsoft.com/fwlink/p/?linkid=2024339) وانتقل إلى [https://aad.portal.azure.com/\#blade/Microsoft_AAD_IAM/ActiveDirectoryMenuBlade/Properties](https://aad.portal.azure.com/#blade/Microsoft_AAD_IAM/ActiveDirectoryMenuBlade/Properties). انقر فوق أيقونة النسخ لخاصية "معرف المستأجر" لنسخها إلى الحافظة.

### <a name="configuration-steps-to-enable-your-tenants-for-cross-tenant-mailbox-migrations"></a>خطوات التكوين لتمكين المستأجرين من عمليات ترحيل علب البريد عبر المستأجرين

   > [!NOTE]
   > يجب تكوين الهدف (الوجهة) أولا. لإكمال هذه الخطوات، لا يطلب منك الحصول على بيانات اعتماد مسؤول المستأجر أو معرفتها لكل من المستأجر المصدر والهدف. يمكن تنفيذ الخطوات بشكل فردي لكل مستأجر من قبل مسؤولين مختلفين.

### <a name="prepare-the-target-destination-tenant-by-creating-the-migration-application-and-secret"></a>إعداد المستأجر الهدف (الوجهة) عن طريق إنشاء تطبيق الترحيل والبيانات السرية

1. تسجيل الدخول إلى مدخل Azure AD الخاص بك (<https://portal.azure.com>) باستخدام بيانات اعتماد مسؤول المستأجر الهدف

   ![تسجيل الدخول إلى Azure](../media/tenant-to-tenant-mailbox-move/74f26681e12df3308c7823ee7d527587.png)

2. انقر فوق طريقة العرض ضمن إدارة Azure Active Directory.

   ![زر Azure Active Directory](../media/tenant-to-tenant-mailbox-move/109ac3dfbac2403fb288f085767f393b.png)

3. على شريط التنقل الأيمن، حدد تسجيلات التطبيق.

4. تحديد تسجيل جديد

   ![تطبيق جديد](../media/tenant-to-tenant-mailbox-move/b36698df128e705eacff4bff7231056a.png)

5. في صفحة "تسجيل تطبيق"، ضمن أنواع الحسابات المدعومة، حدد "الحسابات" في أي دليل تنظيمي (أي دليل Azure AD - متعدد المستأجرين). ثم، ضمن إعادة توجيه URI (اختياري)، حدد ويب وأدخل <https://office.com>. وأخيرا، حدد "تسجيل".

   ![تسجيل التطبيق](../media/tenant-to-tenant-mailbox-move/edcdf18b9f504c47284fe4afb982c433.png)

6. في الزاوية العلوية اليسرى من الصفحة، سترى إعلاما منبثقا يشير إلى أنه تم إنشاء التطبيق بنجاح.

7. ارجع إلى Home وAzure Active Directory وانقر فوق تسجيلات التطبيق.

8. ضمن التطبيقات المملوكة، ابحث عن التطبيق الذي أنشأته وانقر فوقه.

9. ضمن ^Essentials، ستحتاج إلى نسخ معرف التطبيق (العميل) كما ستحتاج إليه لاحقا لإنشاء URL للمستأجر الهدف.

10. الآن، على شريط التنقل الأيمن، انقر فوق أذونات واجهة برمجة التطبيقات لعرض الأذونات المعينة لتطبيقك.

11. بشكل افتراضي، المستخدم. يتم تعيين أذونات القراءة إلى التطبيق الذي أنشأته، ولكننا لا نطلبها لإجراء عمليات ترحيل علبة البريد، يمكنك إزالة هذا الإذن.

    ![أذونات التطبيق](../media/tenant-to-tenant-mailbox-move/6a8c13a36cb3e10964a6920b8138e12b.png)

12. الآن نحن بحاجة إلى إضافة إذن ترحيل علبة البريد، حدد "إضافة إذن"

13. في نوافذ أذونات واجهة برمجة التطبيقات للطلب، حدد واجهات برمجة التطبيقات التي تستخدمها مؤسستي، وابحث عن Office 365 Exchange Online، وحددها.

    ![تحديد واجهة برمجة التطبيقات](../media/tenant-to-tenant-mailbox-move/0b4dc1eea3910e9c475724d9473aca58.png)

14. بعد ذلك، حدد أذونات التطبيق

15. بعد ذلك، ضمن "تحديد الأذونات"، قم بتوسيع علبة البريد، وتحقق من علبة البريد.الترحيل، وأضف الأذونات في أسفل الشاشة.

    ![تعيين واجهة برمجة التطبيقات](../media/tenant-to-tenant-mailbox-move/0038a4cf74bb13de0feb51800e078803.png)

16. حدد الآن "Certificates & secrets" على شريط التنقل الأيمن لتطبيقك.

17. ضمن أسرار العميل، حدد سر عميل جديد.

    ![أسرار العميل](../media/tenant-to-tenant-mailbox-move/273dafd5e6c6455695f9baf35ef9977a.png)

18. في نافذة Add a client secret، أدخل وصفا، وقم بتكوين إعدادات انتهاء الصلاحية المطلوبة.

      > [!NOTE]
      > هذه هي كلمة المرور التي سيتم استخدامها عند إنشاء نقطة نهاية الترحيل. من المهم للغاية نسخ كلمة المرور هذه إلى الحافظة الخاصة بك أو نسخ كلمة المرور هذه لتأمين/سرية الموقع الآمن لكلمة المرور. هذه هي المرة الوحيدة التي ستتمكن فيها من رؤية كلمة المرور هذه! إذا فقدته بطريقة ما أو كنت بحاجة إلى إعادة تعيينه، يمكنك تسجيل الدخول مرة أخرى إلى مدخل Azure، والانتقال إلى تسجيلات التطبيق، والعثور على تطبيق الترحيل، وتحديد الأسرار & الشهادات، وإنشاء سر جديد لتطبيقك.

19. الآن بعد أن قمت بإنشاء تطبيق الترحيل والبيانات السرية بنجاح، ستحتاج إلى الموافقة على التطبيق. للموافقة على التطبيق، عد إلى الصفحة المنتقل إليها في Azure Active Directory، وانقر فوق تطبيقات Enterprise في جزء التنقل الأيمن، وابحث عن تطبيق الترحيل الذي أنشأته، وحدده، وحدد "الأذونات" على شريط التنقل الأيمن.

20. انقر فوق الزر "منح موافقة المسؤول" ل [المستأجر] الخاص بك.

21. سيتم فتح نافذة مستعرض جديدة وتحديد "قبول".

22. يمكنك العودة إلى نافذة المدخل وتحديد "تحديث" لتأكيد قبولك.

23. صياغة عنوان URL لإرساله إلى شريكك الموثوق به (مسؤول المستأجر المصدر) حتى يتمكنوا أيضا من قبول التطبيق لتمكين ترحيل علبة البريد. فيما يلي مثال على عنوان URL الذي يجب توفيره لهم، ستحتاج إلى معرف التطبيق للتطبيق الذي أنشأته:

    ```powershell
    https://login.microsoftonline.com/sourcetenant.onmicrosoft.com/adminconsent?client_id=[application_id_of_the_app_you_just_created]&redirect_uri=https://office.com
    ```

    > [!NOTE]
    > ستحتاج إلى معرف التطبيق لتطبيق ترحيل علبة البريد الذي أنشأته للتو.
    >
    > ستحتاج إلى استبدال sourcetenant.onmicrosoft.com في المثال أعلاه باسم onmicrosoft.com الصحيح للمستأجرين المصدر.
    >
    > ستحتاج أيضا إلى استبدال [application_id_of_the_app_you_just_created] بمعرف التطبيق لتطبيق ترحيل علبة البريد الذي أنشأته للتو.

### <a name="prepare-the-target-tenant-by-creating-the-exchange-online-migration-endpoint-and-organization-relationship"></a>إعداد المستأجر الهدف عن طريق إنشاء نقطة نهاية ترحيل Exchange Online وعلاقة المؤسسة

1. إنشاء اتصال PowerShell بعيد بالمستأجر Exchange Online الهدف.

2. إنشاء نقطة نهاية ترحيل جديدة لحركات علب البريد عبر المستأجرين

   > [!NOTE]
   > ستحتاج إلى معرف التطبيق لتطبيق ترحيل علبة البريد الذي أنشأته للتو وكلمة المرور (البيانات السرية) التي قمت بتكوينها أثناء هذه العملية. قد يختلف أيضا استنادا إلى Microsoft 365 Cloud Instance الذي تستخدمه لنقطة النهاية. الرجاء الرجوع إلى صفحة [نقاط النهاية Microsoft 365](/microsoft-365/enterprise/microsoft-365-endpoints) وتحديد المثيل الصحيح للمستأجر ومراجعة Exchange Online تحسين العنوان المطلوب واستبداله حسب الاقتضاء.

   ```powershell

   # Enable customization if tenant is dehydrated
   $dehydrated=Get-OrganizationConfig | select isdehydrated
   if ($dehydrated -eq $true) {Enable-OrganizationCustomization}
   $AppId = "[guid copied from the migrations app]"
   $Credential = New-Object -TypeName System.Management.Automation.PSCredential -ArgumentList $AppId, (ConvertTo-SecureString -String "[this is your secret password you saved in the previous steps]" -AsPlainText -Force)
   New-MigrationEndpoint -RemoteServer outlook.office.com -RemoteTenant "sourcetenant.onmicrosoft.com" -Credentials $Credential -ExchangeRemoteMove:$true -Name "[the name of your migration endpoint]" -ApplicationId $AppId
   ```

3. إنشاء كائن علاقة مؤسسة جديد أو تحريره إلى المستأجر المصدر.

   ```powershell
   $sourceTenantId="[tenant id of your trusted partner, where the source mailboxes are]"
   $orgrels=Get-OrganizationRelationship
   $existingOrgRel = $orgrels | ?{$_.DomainNames -like $sourceTenantId}
   If ($null -ne $existingOrgRel)
   {
       Set-OrganizationRelationship $existingOrgRel.Name -Enabled:$true -MailboxMoveEnabled:$true -MailboxMoveCapability Inbound
   }
   If ($null -eq $existingOrgRel)
   {
       New-OrganizationRelationship "[name of the new organization relationship]" -Enabled:$true -MailboxMoveEnabled:$true -MailboxMoveCapability Inbound -DomainNames $sourceTenantId
   }
   ```

### <a name="prepare-the-source-current-mailbox-location-tenant-by-accepting-the-migration-application-and-configuring-the-organization-relationship"></a>إعداد المستأجر المصدر (موقع علبة البريد الحالي) عن طريق قبول تطبيق الترحيل وتكوين علاقة المؤسسة

1. من المستعرض، انتقل إلى ارتباط URL الذي يوفره شريكك الموثوق به للموافقة على تطبيق ترحيل علبة البريد. سيبدو عنوان URL كما يلي:

   ```powershell
   https://login.microsoftonline.com/sourcetenant.onmicrosoft.com/adminconsent?client_id=[application_id_of_the_app_you_just_created]&redirect_uri=https://office.com
   ```

   > [!NOTE]
   > ستحتاج إلى معرف التطبيق لتطبيق ترحيل علبة البريد الذي أنشأته للتو.
   > ستحتاج إلى استبدال sourcetenant.onmicrosoft.com في المثال أعلاه باسم onmicrosoft.com الصحيح للمستأجرين المصدر.
   > ستحتاج أيضا إلى استبدال [application_id_of_the_app_you_just_created] بمعرف التطبيق لتطبيق ترحيل علبة البريد الذي أنشأته للتو.

2. اقبل التطبيق عند ظهور النافذة المنبثقة. يمكنك أيضا تسجيل الدخول إلى مدخل Azure Active Directory الخاص بك والعثور على التطبيق ضمن تطبيقات Enterprise.

3. إنشاء كائن علاقة مؤسسة جديد أو تحريره إلى المستأجر الهدف (الوجهة) من نافذة powerShell Exchange Online البعيدة.

   ```powershell
   $targetTenantId="[tenant id of your trusted partner, where the mailboxes are being moved to]"
   $appId="[application id of the mailbox migration app you consented to]"
   $scope="[name of the mail enabled security group that contains the list of users who are allowed to migrate]"
   $orgrels=Get-OrganizationRelationship
   $existingOrgRel = $orgrels | ?{$_.DomainNames -like $targetTenantId}
   If ($null -ne $existingOrgRel)
   {
       Set-OrganizationRelationship $existingOrgRel.Name -Enabled:$true -MailboxMoveEnabled:$true -MailboxMoveCapability RemoteOutbound -OAuthApplicationId $appId -MailboxMovePublishedScopes $scope
   }
   If ($null -eq $existingOrgRel)
   {
       New-OrganizationRelationship "[name of your organization relationship]" -Enabled:$true -MailboxMoveEnabled:$true -MailboxMoveCapability RemoteOutbound -DomainNames $targetTenantId -OAuthApplicationId $appId -MailboxMovePublishedScopes $scope
   }
   ```

> [!NOTE]
> معرف المستأجر الذي تقوم بإدخاله ك $sourceTenantId $targetTenantId هو GUID وليس اسم مجال المستأجر. للحصول على مثال لمعرف المستأجر ومعلومات حول العثور على معرف المستأجر الخاص بك، راجع [البحث عن معرف المستأجر Microsoft 365](/onedrive/find-your-office-365-tenant-id).

### <a name="how-do-i-know-this-worked"></a>كيف أتأكد من نجاح هذا الأمر؟

يمكنك التحقق من تكوين ترحيل علبة البريد عبر المستأجرين عن طريق تشغيل [Cmdlet Test-MigrationServerAvailability](/powershell/module/exchange/Test-MigrationServerAvailability) مقابل نقطة نهاية الترحيل عبر المستأجر التي قمت بإنشائها على المستأجر الهدف.

   > [!NOTE]
   >
   > - المستأجر الهدف:
   >
   > Test-MigrationServerAvailability -Endpoint "[اسم نقطة نهاية الترحيل عبر المستأجرين]"
   >
   > Get-OrganizationRelationship | اسم fl، DomainNames، MailboxMoveEnabled، MailboxMoveCapability
   >
   > - المستأجر المصدر:
   >
   > Get-OrganizationRelationship | اسم fl، DomainNames، MailboxMoveEnabled، MailboxMoveCapability

### <a name="move-mailboxes-back-to-the-original-source"></a>نقل علب البريد مرة أخرى إلى المصدر الأصلي

إذا كانت علبة البريد مطلوبة للعودة إلى المستأجر المصدر الأصلي، فستحتاج نفس مجموعة الخطوات والبرامج النصية إلى تشغيلها في كل من المستأجرين المستهدفين الجدد والمصدر الجديد. سيتم تحديث كائن "علاقة المؤسسة" الموجود أو إلحاقه، ولن يتم إعادة إنشائه

## <a name="prepare-target-user-objects-for-migration"></a>إعداد كائنات المستخدم الهدف للتهحيل

يجب أن يكون ترحيل المستخدمين موجودا في المستأجر الهدف ونظام Exchange Online (كمستخدمي البريد) المعلمين بسمات محددة لتمكين عمليات النقل عبر المستأجرين. سيفشل النظام في النقل للمستخدمين الذين لم يتم إعدادهم بشكل صحيح في المستأجر الهدف. يوضح القسم التالي تفاصيل متطلبات كائن MailUser للمستأجر الهدف.

### <a name="prerequisites-for-target-user-objects"></a>المتطلبات الأساسية للعناصر المستهدفة للمستخدم

تأكد من تعيين العناصر والسمات التالية في المؤسسة الهدف.

1. بالنسبة لأي علبة بريد تنتقل من مؤسسة مصدر، يجب توفير كائن MailUser في المؤسسة الهدف:

   - يجب أن يكون لدى "مستخدم البريد الهدف" هذه السمات من علبة البريد المصدر أو معينة مع كائن المستخدم الجديد:
      - ExchangeGUID (التدفق المباشر من المصدر إلى الهدف): يجب أن يتطابق GUID لعلبة البريد. لن تستمر عملية النقل إذا لم يكن هذا موجودا على الكائن الهدف.
      - ArchiveGUID (تدفق مباشر من المصدر إلى الهدف): يجب أن يتطابق GUID الأرشيف. لن تستمر عملية النقل إذا لم يكن هذا موجودا على الكائن الهدف. (هذا مطلوب فقط إذا كانت علبة البريد المصدر ممكنة في الأرشيف).
      - LegacyExchangeDN (تدفق ك proxyAddress، "x500:\<LegacyExchangeDN>"): يجب أن يكون LegacyExchangeDN موجودا على MailUser الهدف ك x500: proxyAddress. بالإضافة إلى ذلك، تحتاج أيضا إلى نسخ كافة عناوين x500 من علبة البريد المصدر إلى مستخدم البريد الهدف. لن تستمر عمليات النقل إذا لم تكن موجودة على الكائن الهدف.
      - UserPrincipalName: ستتم محاذاة UPN مع الهوية الجديدة للمستخدم أو الشركة المستهدفة (على سبيل المثال، user@northwindtraders.onmicrosoft.com).
      - عنوان SMTPAddress الأساسي: ستتم محاذاة عنوان SMTP الأساسي مع شركة المستخدم الجديدة (على سبيل المثال، user@northwind.com).
      - TargetAddress/ExternalEmailAddress: سيشير MailUser إلى علبة البريد الحالية للمستخدم المستضافة في المستأجر المصدر (على سبيل المثال user@contoso.onmicrosoft.com). عند تعيين هذه القيمة، تحقق من أن لديك/تقوم أيضا بتعيين PrimarySMTPAddress أو ستقوم هذه القيمة بتعيين PrimarySMTPAddress، مما سيؤدي إلى فشل النقل.
      - لا يمكنك إضافة عناوين وكيل smtp القديمة من علبة البريد المصدر إلى MailUser الهدف. على سبيل المثال، لا يمكنك الاحتفاظ contoso.com على MEU في كائنات المستأجر fabrikam.onmicrosoft.com). ترتبط المجالات بمستأجر واحد Azure AD أو Exchange Online فقط.

     مثال **كائن** MailUser الهدف:

     | السمه            | قيمه                                                                                                                   |
     | -------------------- | ----------------------------------------------------------------------------------------------------------------------- |
     | الاسم المستعار                | LaraN                                                                                                                   |
     | نوع المستلم        | MailUser                                                                                                                |
     | RecipientTypeDetails | MailUser                                                                                                                |
     | UserPrincipalName    | LaraN@northwintraders.onmicrosoft.com                                                                                   |
     | PrimarySmtpAddress   | Lara.Newton@northwind.com                                                                                               |
     | ExternalEmailAddress | SMTP:LaraN@contoso.onmicrosoft.com                                                                                      |
     | ExchangeGuid         | 1ec059c7-8396-4d0b-af4e-d6bd4c12a8d8                                                                                    |
     | Legacyexchangedn     | /o=First Organization/ou=Exchange Administrative Group                                                                  |
     |                      | (FYDIBOHF23SPDLT)/cn=Recipients/cn=74e5385fce4b46d19006876949855035Lara                                                 |
     | عناوين البريد الإلكتروني       | x500:/o=First Organization/ou=Exchange Administrative Group (FYDIBOHF23SPDLT)/cn=Recipients/cn=d11ec1a2cacd4f81858c8190 |
     |                      | 7273f1f9-Lara                                                                                                           |
     |                      | smtp:LaraN@northwindtraders.onmicrosoft.com                                                                             |
     |                      | SMTP:Lara.Newton@northwind.com                                                                                          |

     مثال على كائن علبة بريد **المصدر** :

     | السمه            | قيمه                                                                   |
     | -------------------- | ----------------------------------------------------------------------- |
     | الاسم المستعار                | LaraN                                                                   |
     | نوع المستلم        | UserMailbox                                                             |
     | RecipientTypeDetails | UserMailbox                                                             |
     | UserPrincipalName    | LaraN@contoso.onmicrosoft.com                                           |
     | PrimarySmtpAddress   | Lara.Newton@contoso.com                                                 |
     | ExchangeGuid         | 1ec059c7-8396-4d0b-af4e-d6bd4c12a8d8                                    |
     | Legacyexchangedn     | /o=First Organization/ou=Exchange Administrative Group                  |
     |                      | (FYDIBOHF23SPDLT)/cn=Recipients/cn=d11ec1a2cacd4f81858c81907273f1f9Lara |
     | عناوين البريد الإلكتروني       | smtp:LaraN@contoso.onmicrosoft.com                                      |
     |                      | SMTP:Lara.Newton@contoso.com                                            |

   - قد يتم تضمين سمات إضافية في Exchange إعادة الكتابة المختلطة بالفعل. وإذا لم يكن ذلك، فيجب تضمينها.
   - msExchBlockedSendersHash – إعادة كتابة بيانات المرسل الآمنة والمحظرة عبر الإنترنت من العملاء إلى Active Directory محلي.
   - msExchSafeRecipientsHash – إعادة كتابة بيانات المرسل الآمنة والمحظرة عبر الإنترنت من العملاء إلى Active Directory محلي.
   - msExchSafeSendersHash – إعادة كتابة بيانات المرسل الآمنة والمحظرة عبر الإنترنت من العملاء إلى Active Directory محلي.

2. إذا كانت علبة البريد المصدر موجودة على "التقاضي" وكان حجم "العناصر القابلة للاسترداد" لعل البريد المصدر أكبر من الحجم الافتراضي لقاعدة البيانات (30 غيغابايت)، فلن تستمر عمليات النقل لأن الحصة المستهدفة أقل من حجم علبة البريد المصدر. يمكنك تحديث كائن MailUser الهدف لنقل علامات علبة بريد ELC من البيئة المصدر إلى الهدف، مما يؤدي إلى تشغيل النظام الهدف لتوسيع الحصة النسبية ل MailUser إلى 100 غيغابايت، مما يسمح بالانتقال إلى الهدف. ستعمل هذه التعليمات فقط للهوية المختلطة التي تعمل Azure AD الاتصال، حيث لا يتم عرض أوامر طابع علامات ELC لمسؤولي المستأجرين.

    > [!NOTE]
    > العينة – كما هو الحال، لا يوجد ضمان
    >
    > يفترض هذا البرنامج النصي اتصالا بكل من علبة البريد المصدر (للحصول على قيم المصدر) Active Directory محلي الهدف (لوضع طابع على كائن ADUser). إذا تم تمكين التقاضي أو استرداد عنصر واحد في المصدر، فقم بتعيين هذا على حساب الوجهة.  سيؤدي ذلك إلى زيادة حجم تفريغ حساب الوجهة إلى 100 غيغابايت.

    ```powershell
    $ELCValue = 0
    if ($source.LitigationHoldEnabled) {$ELCValue = $ELCValue + 8} if ($source.SingleItemRecoveryEnabled) {$ELCValue = $ELCValue + 16} if ($ELCValue -gt 0) {Set-ADUser -Server $domainController -Identity $destination.SamAccountName -Replace @{msExchELCMailboxFlags=$ELCValue}}
    ```

3. يمكن للمستأجرين المستهدفين غير المختلطين تعديل الحصة النسبية على مجلد "العناصر القابلة للاسترداد" لمرسلي البريد قبل الترحيل عن طريق تشغيل الأمر التالي لتمكين "احتجاز التقاضي" على كائن MailUser وزيادة الحصة النسبية إلى 100 غيغابايت:

   ```powershell
   Set-MailUser -Identity <MailUserIdentity> -EnableLitigationHoldForMigration
   ```

   لاحظ أن هذا لن يعمل للمستأجرين في المختلط.

4. يجب أن يكون المستخدمون في المؤسسة المستهدفة مرخصين باشتراكات Exchange Online مناسبة تنطبق على المؤسسة. يمكنك تطبيق ترخيص قبل نقل علبة البريد ولكن بمجرد إعداد MailUser الهدف بشكل صحيح باستخدام ExchangeGUID وعناوين الوكيل. سيؤدي تطبيق ترخيص قبل تطبيق ExchangeGUID إلى توفير علبة بريد جديدة في المؤسسة الهدف.

    > [!NOTE]
    > عند تطبيق ترخيص على عنصر علبة بريد أو MailUser، يتم تنقية كافة عناوين وكيل نوع SMTP للتأكد من تضمين المجالات التي تم التحقق منها فقط في صفيف Exchange EmailAddresses.

5. يجب التأكد من أن MailUser الهدف ليس لديه ExchangeGuid سابق لا يتطابق مع ExchangeGuid المصدر. قد يحدث هذا إذا تم ترخيص MEU الهدف مسبقا Exchange Online وتوفير علبة بريد. إذا كان MailUser الهدف مرخصا مسبقا ل ExchangeGuid أو كان لديه ExchangeGuid لا يتطابق مع ExchangeGuid المصدر، فستحتاج إلى إجراء تنظيف للسحابة MEU. بالنسبة إلى وحدات MEUs السحابية هذه، يمكنك تشغيل `Set-User <identity> -PermanentlyClearPreviousMailboxInfo`.

    > [!CAUTION]
    > هذه العملية لا رجعة فيها. إذا كان الكائن يحتوي على علبة بريد softDeleted، فلا يمكن استعادتها بعد هذه النقطة. ومع ذلك، بمجرد مسحها، يمكنك مزامنة ExchangeGuid الصحيح مع الكائن الهدف وستقوم أداة المزامنة عن بعد بتوصيل علبة البريد المصدر بعلبة البريد الهدف التي تم إنشاؤها حديثا. (مرجع مدونة EHLO على المعلمة الجديدة.)

    ابحث عن الكائنات التي كانت في السابق علب بريد باستخدام هذا الأمر.

    ```powershell
    Get-User <identity> | select Name, *recipient* | Format-Table -AutoSize
    ```

    فيما يلي مثال على ذلك.

    ```powershell
    Get-User John@northwindtraders.com |select name, *recipient*| Format-Table -AutoSize

    Name       PreviousRecipientTypeDetails     RecipientType RecipientTypeDetails
    ----       ---------------------------- ------------- --------------------
    John       UserMailbox                  MailUser      MailUser
    ```

    امسح علبة البريد المحذوفة مبدئيا باستخدام هذا الأمر.

    ```powershell
    Set-User <identity> -PermanentlyClearPreviousMailboxInfo
    ```

    فيما يلي مثال على ذلك.

    ```powershell
    Set-User John@northwindtraders.com -PermanentlyClearPreviousMailboxInfo -Confirm

    Are you sure you want to perform this action?
    Delete all existing information about user "John@northwindtraders.com"?. This operation will clear existing values from Previous home MDB and Previous Mailbox GUID of the user. After deletion, reconnecting to the previous mailbox that existed in the cloud will not be possible and any content it had will be unrecoverable PERMANENTLY.
    Do you want to continue?
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [?] Help (default is "Y"): Y
    ```

### <a name="perform-mailbox-migrations"></a>تنفيذ عمليات ترحيل علبة البريد

يتم بدء عمليات ترحيل علبة بريد Exchange عبر المستأجرين من المستأجر الهدف كدفعات ترحيل. تشبه هذه الطريقة التي تعمل بها دفعات الترحيل الداخلي عند الترحيل من Exchange المحلي إلى Microsoft 365.

### <a name="create-migration-batches"></a>إنشاء دفعات الترحيل

فيما يلي مثال على cmdlet دفعة الترحيل لبدء عمليات النقل.

```powershell
New-MigrationBatch -Name T2Tbatch -SourceEndpoint target_source_7977 -CSVData ([System.IO.File]::ReadAllBytes('users.csv')) -Autostart -TargetDeliveryDomain target.onmicrosoft.com

Identity                   Status  Type               TotalCount
--------                   ------  ----               ----------
T2Tbatch                   Syncing ExchangeRemoteMove 1
```

> [!NOTE]
> يجب أن يكون عنوان البريد الإلكتروني في ملف CSV هو العنوان المحدد في المستأجر الهدف، وليس المستأجر المصدر.
>
> [لمزيد من المعلومات حول أمر cmdlet، انقر هنا](/powershell/module/exchange/new-migrationbatch)
>
> [للحصول على مثال لملف CSV، انقر هنا](/exchange/csv-files-for-mailbox-migration-exchange-2013-help)

كما يتم دعم إرسال دفعة الترحيل من <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">مركز إدارة Exchange</a> الجديد عند تحديد خيار عبر المستأجرين.

### <a name="update-on-premises-mailusers"></a>تحديث MailUsers المحلي

بمجرد انتقال علبة البريد من المصدر إلى الهدف، يجب التأكد من تحديث مستخدمي البريد المحليين، في كل من المصدر والهدف، باستخدام targetAddress الجديد. في الأمثلة، targetDeliveryDomain المستخدم في النقل هو **contoso.onmicrosoft.com**. تحديث مستخدمي البريد باستخدام targetAddress هذا.

## <a name="frequently-asked-questions"></a>الأسئلة الشائعة

**هل نحتاج إلى تحديث RemoteMailboxes في المصدر المحلي بعد النقل؟**

نعم، يجب تحديث targetAddress (RemoteRoutingAddress/ExternalEmailAddress) للمستخدمين المحليين المصدر عندما تنتقل علبة بريد المستأجر المصدر إلى المستأجر الهدف.  بينما يمكن أن يتبع توجيه البريد الإحالات عبر العديد من مستخدمي البريد الذين لديهم عناوين هدف مختلفة، يجب أن تستهدف عمليات البحث عن التوفر/الانشغال لمستخدمي البريد موقع مستخدم علبة البريد. لن تلاحق عمليات البحث عن التوفر/الانشغال عمليات إعادة التوجيه المتعددة.

**هل تقوم Teams الاجتماعات بترحيل المستأجرين المشتركين؟**

سيتم نقل الاجتماعات، ومع ذلك لا يتم تحديث عنوان URL للاجتماع Teams عند ترحيل العناصر عبر المستأجر. نظرا لأن عنوان URL سيكون غير صالح في المستأجر الهدف، فستحتاج إلى إزالة اجتماعات Teams وإعادة إنشائها.

**هل يرحل محتوى مجلد الدردشة Teams عبر المستأجرين؟**

لا، لا يقوم محتوى مجلد الدردشة Teams بترحيل المستأجر المشترك.

**كيف يمكنني رؤية فقط الحركات التي هي عمليات نقل عبر المستأجرين، وليس عمليات الإلحاق والتحركات خارج الطائرة؟**

استخدم _المعلمة Flags_ . فيما يلي مثال على ذلك.

```powershell
Get-MoveRequest -Flags "CrossTenant"
```

**هل يمكنك توفير أمثلة على البرامج النصية لنسخ السمات المستخدمة في الاختبار؟**

> [!NOTE]
> العينة – كما هو الحال، لا يوجد ضمان يفترض هذا البرنامج النصي وجود اتصال بكل من علبة البريد المصدر (للحصول على قيم المصدر) والهدف Active Directory محلي خدمات المجال (لوضع طابع على كائن ADUser). إذا تم تمكين التقاضي أو استرداد عنصر واحد في المصدر، فقم بتعيين هذا على حساب الوجهة.  سيؤدي ذلك إلى زيادة حجم تفريغ حساب الوجهة إلى 100 غيغابايت.

   ```powershell
   # This will export users from the source tenant with the CustomAttribute1 = "Cross-Tenant-Project"
   # These are the 'target' users to be moved to the Northwind org tenant
   $outFileUsers = "$home\desktop\UsersToMigrate.txt"
   $outFileUsersXML = "$home\desktop\UsersToMigrate.xml"
   Get-Mailbox -Filter "CustomAttribute1 -like 'Cross-Tenant-Project'" -ResultSize Unlimited | Select-Object -ExpandProperty  Alias | Out-File $outFileUsers
   $mailboxes = Get-Content $outFileUsers
   $mailboxes | ForEach-Object {Get-Mailbox $_} | Select-Object PrimarySMTPAddress,Alias,SamAccountName,FirstName,LastName,DisplayName,Name,ExchangeGuid,ArchiveGuid,LegacyExchangeDn,EmailAddresses | Export-Clixml $outFileUsersXML
   ```

   ```powershell
   # Copy the file $outfile to the desktop of the target on-premises then run the below to create MEU in Target
   $mailboxes = Import-Clixml $home\desktop\UsersToMigrate.xml
   add-type -AssemblyName System.Web
   foreach ($m in $mailboxes) {
       $organization = "@contoso.onmicrosoft.com"
       $mosi = $m.Alias+$organization
       $Password = [System.Web.Security.Membership]::GeneratePassword(16,4) | ConvertTo-SecureString -AsPlainText -Force
       $x500 = "x500:" +$m.LegacyExchangeDn
       $tmpUser = New-MailUser -MicrosoftOnlineServicesID $mosi -PrimarySmtpAddress $mosi -ExternalEmailAddress $m.PrimarySmtpAddress -FirstName $m.FirstName -LastName $m.LastName -Name $m.Name -DisplayName $m.DisplayName -Alias $m.Alias -Password $Password
       $tmpUser | Set-MailUser -EmailAddresses @{add=$x500} -ExchangeGuid $m.ExchangeGuid -ArchiveGuid $m.ArchiveGuid -CustomAttribute1 "Cross-Tenant-Project"
       $tmpx500 = $m.EmailAddresses | ?{$_ -match "x500"}
       $tmpx500 | %{Set-MailUser $m.Alias -EmailAddresses @{add="$_"}}
       }
   ```

   ```powershell
   # Now sync the changes from On-Premises to Azure and Exchange Online in the Target tenant
   # This action should create the target mail enabled users (MEUs) in the Target tenant
   Start-ADSyncSyncCycle
   ```

**كيف يمكننا الوصول إلى Outlook في اليوم 1 بعد نقل علبة بريد الاستخدام؟**

نظرا لأن مستأجرا واحدا فقط يمكنه امتلاك مجال، فلن يتم إقران SMTPAddress الأساسي السابق بالمستخدم في المستأجر الهدف عند اكتمال نقل علبة البريد؛ فقط تلك المجالات المقترنة بالمستأجر الجديد. يستخدم Outlook UPN الجديد للمستخدمين للمصادقة على الخدمة ويتوقع ملف تعريف Outlook العثور على SMTPAddress الأساسي القديم لمطابقة علبة البريد في النظام الهدف. نظرا لأن العنوان القديم غير موجود في النظام الهدف، فلن يتصل ملف تعريف Outlook للعثور على علبة البريد المنقولة حديثا.

لهذا النشر الأولي، سيحتاج المستخدمون إلى إعادة إنشاء ملف التعريف الخاص بهم باستخدام عنوان UPN الجديد وعنوان SMTP الأساسي ومحتوى OST لإعادة المزامنة.

> [!NOTE]
> خطط وفقا لذلك أثناء دفع المستخدمين للإكمال. تحتاج إلى حساب استخدام الشبكة وسعتها عند إنشاء ملفات تعريف العميل Outlook وتنزيل ملفات OST وOAB اللاحقة للعملاء.

**ما Exchange أدوار RBAC التي أحتاج إلى أن أكون عضوا فيها لإعداد نقل عبر المستأجرين أو إكماله؟**

هناك مصفوفة من الأدوار استنادا إلى افتراض المهام المفوضة عند تنفيذ نقل علبة البريد. مطلوب حاليا دوران:

- الدور الأول هو لمهمة إعداد لمرة واحدة تحدد تخويل نقل المحتوى إلى حدود المستأجر/المؤسسة أو الخروج منها. نظرا إلى أن نقل البيانات خارج نطاق تحكم المؤسسة هو مصدر قلق بالغ لجميع الشركات، فإننا اخترنا أعلى دور معين لمسؤول المؤسسة (OrgAdmin). يجب أن يغير هذا الدور أو يقوم بإعداد OrganizationRelationship جديد يعرف علبة البريد -MailboxMoveCapability مع المؤسسة البعيدة. يمكن فقط ل OrgAdmin تغيير إعداد MailboxMoveCapability، بينما يمكن إدارة السمات الأخرى على OrganizationRelationship بواسطة مسؤول المشاركة المتحدة.

- يمكن تفويض دور تنفيذ أوامر النقل الفعلي إلى دالة ذات مستوى أدنى. يتم تعيين دور نقل علب البريد لإمكانية نقل علب البريد داخل المؤسسة أو خارجها.

**كيف نستهدف عنوان SMTP المحدد ل targetAddress (TargetDeliveryDomain) على علبة البريد المحولة (لتحويل MailUser)؟**

Exchange نقل علبة البريد باستخدام الدالة MRS، قم بصياغة targetAddress على علبة البريد المصدر الأصلية عند التحويل إلى MailUser عن طريق مطابقة عنوان بريد إلكتروني (proxyAddress) على الكائن الهدف. تأخذ العملية قيمة -TargetDeliveryDomain التي تم تمريرها إلى أمر النقل، ثم تتحقق من وجود وكيل مطابق لهذا المجال على الجانب الهدف. عندما نجد تطابقا، يتم استخدام proxyAddress المطابق لتعيين ExternalEmailAddress (targetAddress) على كائن علبة البريد المحولة (MailUser الآن).

**كيف تنتقل أذونات علبة البريد؟**

تتضمن أذونات علبة البريد "إرسال نيابة عن" و"الوصول إلى علبة البريد":

- يقوم "إرسال نيابة عن" (AD:publicDelegates) بتخزين DN للمستلمين الذين لهم حق الوصول إلى علبة بريد المستخدم كمفوض. يتم تخزين هذه القيمة في Active Directory ولا يتم نقلها حاليا كجزء من انتقال علبة البريد. إذا كانت علبة البريد المصدر قد تم تعيين الحذف العام لها، فستحتاج إلى إعادة تعيين الحذف العام على علبة البريد الهدف بمجرد اكتمال تحويل MEU إلى علبة البريد في البيئة الهدف عن طريق التشغيل `Set-Mailbox <principle> -GrantSendOnBehalfTo <delegate>`.

- سيتم نقل أذونات علبة البريد المخزنة في علبة البريد مع علبة البريد عند نقل كل من المدير والمفوض إلى النظام الهدف. على سبيل المثال، يتم منح TestUser_7 المستخدم FullAccess إلى TestUser_8 علبة البريد في SourceCompany.onmicrosoft.com المستأجر. بعد اكتمال نقل علبة البريد إلى TargetCompany.onmicrosoft.com، يتم إعداد نفس الأذونات في الدليل الهدف. فيما يلي أمثلة على استخدام *Get-MailboxPermission* TestUser_7 في كل من المستأجرين المصدر والهدف. Exchange cmdlets مسبوقة بالمصدر والهدف وفقا لذلك.

فيما يلي مثال على إخراج إذن علبة البريد قبل النقل.

```powershell
Get-SourceMailboxPermission TestUser_7 | Format-Table -AutoSize User, AccessRights, IsInherited, Deny

User                                             AccessRights                         IsInherited Deny
----                                             ------------                         ----------- ----
NT AUTHORITY\SELF                                {FullAccess, ReadPermission}         False       False
TestUser_8@SourceCompany.onmicrosoft.com         {FullAccess}                         False       False
```

فيما يلي مثال على إخراج إذن علبة البريد بعد النقل.

```powershell
Get-TargetMailboxPermission TestUser_7 | Format-Table -AutoSize User, AccessRights, IsInherited, Deny

User                                             AccessRights                         IsInherited Deny
----                                             ------------                         ----------- ----
NT AUTHORITY\SELF                                {FullAccess, ReadPermission}         False       False
TestUser_8@TargetCompany.onmicrosoft.com         {FullAccess}                         False       False
```

> [!NOTE]
> أذونات التقويم وعلبة البريد عبر المستأجرين غير معتمدة. يجب تنظيم الكيانات والمفوضين في دفعات نقل موحدة بحيث يتم نقل علب البريد المتصلة هذه في نفس الوقت من المستأجر المصدر.

**ما هو وكيل X500 الذي يجب إضافته إلى عناوين وكيل MailUser الهدف لتمكين الترحيل؟**

يتطلب ترحيل علبة البريد عبر المستأجرين أن يتم وضع طابع على قيمة LegacyExchangeDN لكائن علبة البريد المصدر كعنوان بريد إلكتروني x500 على كائن MailUser الهدف.

على سبيل المثال:

```powershell
LegacyExchangeDN value on source mailbox is:
/o=First Organization/ou=Exchange Administrative Group(FYDIBOHF23SPDLT)/cn=Recipients/cn=d11ec1a2cacd4f81858c81907273f1f9Lara

so, the x500 email address to be added to target MailUser object would be:
x500:/o=First Organization/ou=Exchange Administrative Group (FYDIBOHF23SPDLT)/cn=Recipients/cn=d11ec1a2cacd4f81858c81907273f1f9-Lara
```

> [!NOTE]
> بالإضافة إلى وكيل X500 هذا، ستحتاج إلى نسخ كل وكلاء X500 من علبة البريد في المصدر إلى علبة البريد في الهدف.

**هل يمكن للمستأجر المصدر والهدف استخدام نفس اسم المجال؟**

لا. يجب أن تكون أسماء نطاقات المستأجر المصدر والهدف فريدة. على سبيل المثال، مجال مصدر contoso.com والمجال الهدف fourthcoffee.com.

**هل سيتم نقل علب البريد المشتركة وما زالت تعمل؟**

نعم، ومع ذلك، لا نحتفظ إلا بأذونات المتجر كما هو موضح في هذه المقالات:

- [Microsoft Docs | إدارة الأذونات للمستلمين في Exchange Online](/exchange/recipients-in-exchange-online/manage-permissions-for-recipients)

- [| دعم Microsoft كيفية منح أذونات علبة بريد Exchange وعلبة بريد Outlook في Office 365 مخصصة](https://support.microsoft.com/topic/how-to-grant-exchange-and-outlook-mailbox-permissions-in-office-365-dedicated-bac01b2c-08ff-2eac-e1c8-6dd01cf77287)

**هل لديك أي توصيات للدفعات؟**

لا تتجاوز 2000 علبة بريد لكل دفعة. نوصي بشدة بإرسال دفعات قبل أسبوعين من تاريخ القص حيث لا يوجد أي تأثير على المستخدمين النهائيين أثناء المزامنة. إذا كنت بحاجة إلى إرشادات لكميات علب البريد التي تزيد عن 50,000، يمكنك الوصول إلى قائمة توزيع الملاحظات الهندسية في crosstenantmigrationpreview@service.microsoft.com.

**ماذا لو استخدمت تشفير الخدمة مع مفتاح العميل؟**

سيتم فك تشفير علبة البريد قبل النقل. تأكد من تكوين مفتاح العميل في المستأجر الهدف إذا كان لا يزال مطلوبا. راجع [هنا](/microsoft-365/compliance/customer-key-overview) للحصول على مزيد من المعلومات.

**ما هو وقت الترحيل المقدر؟**

لمساعدتك على التخطيط لل ترحيلك، يعرض الجدول الموجود [هنا](/exchange/mailbox-migration/office-365-migration-best-practices#estimated-migration-times) إرشادات حول متى يمكن توقع اكتمال عمليات ترحيل علبة البريد المجمعة أو عمليات الترحيل الفردية. تستند هذه التقديرات إلى تحليل بيانات عمليات ترحيل العملاء السابقة. نظرا لأن كل بيئة فريدة من نوعها، فقد تختلف سرعة الترحيل الدقيقة.

تذكر أن هذه الميزة قيد المعاينة وSLA حاليا، ولا تنطبق أي مستويات خدمة قابلة للتطبيق على أي مشكلات في الأداء أو التوفر أثناء حالة المعاينة لهذه الميزة.

**حماية المستندات في المستأجر المصدر التي يمكن للمستخدمين استخدامها في المستأجر الوجهة.**

الترحيل عبر المستأجرين لا يرحل إلا بيانات علبة البريد ولا يرحل أي شيء آخر. هناك العديد من الخيارات الأخرى، والتي تم توثيقها في منشور المدونة التالي الذي قد يساعد: <https://techcommunity.microsoft.com/t5/security-compliance-and-identity/mergers-and-spinoffs/ba-p/910455>

**هل يمكنني الحصول على نفس التسميات في المستأجر الوجهة كما كان لديك في المستأجر المصدر، إما كمجموعة فقط من التسميات أو مجموعة إضافية من التسميات للمستخدمين الذين تم ترحيلهم اعتمادا على المحاذاة بين المؤسسات.**

نظرا لأن عمليات الترحيل عبر المستأجرين لا تقوم بتصدير التسميات ولا توجد طريقة لمشاركة التسميات بين المستأجرين، يمكنك تحقيق ذلك فقط عن طريق إعادة إنشاء التسميات في المستأجر الوجهة.

**هل تدعم نقل مجموعات Microsoft 365؟**

حاليا لا تدعم ميزة ترحيل علب بريد المستأجرين المشتركين ترحيل مجموعات Microsoft 365.

**هل يمكن لمسؤول المستأجر المصدر إجراء بحث eDiscovery مقابل علبة بريد بعد ترحيل علبة البريد إلى المستأجر الجديد/الهدف؟**

لا، بعد ترحيل علبة بريد المستأجرين، لا يعمل eDiscovery مقابل علبة بريد المستخدم الذي تم ترحيله في المصدر. وذلك لأنه لم يعد هناك علبة بريد في المصدر للبحث مقابلها حيث تم ترحيل علبة البريد إلى المستأجر الهدف والآن ينتمي إلى المستأجر الهدف. eDiscovery، لا يمكن ترحيل علبة البريد بعد إلا في المستأجر الهدف (حيث توجد علبة البريد الآن). إذا كانت هناك نسخة من علبة البريد المصدر تحتاج إلى الاستمرار في المستأجر المصدر بعد الترحيل، يمكن للمسؤول في المصدر نسخ المحتويات إلى علبة بريد بديلة قبل الترحيل لعمليات eDiscovery المستقبلية مقابل البيانات.

## <a name="known-issues"></a>المشاكل المعروفة

- **المشكلة: ستكون وظيفة Teams ما بعد الترحيل في المستأجر المصدر محدودة.** بعد ترحيل علبة البريد إلى المستأجر الهدف، لن يعود Teams في المستأجر المصدر قادرا على الوصول إلى علبة بريد المستخدم. لذلك، إذا قام المستخدم بتسجيل الدخول إلى Teams باستخدام بيانات اعتماد المستأجر المصدر، فسيكون هناك فقدان للوظائف مثل عدم القدرة على تحديث صورة ملف التعريف الخاص بك، وعدم وجود تطبيق تقويم، وعدم القدرة على البحث والانضمام إلى الفرق العامة.

- **المشكلة: لا يمكن ترحيل الأرشيفات الموسعة تلقائيا.** تدعم ميزة الترحيل عبر المستأجر عمليات ترحيل علبة البريد الأساسية وعلبة بريد الأرشيف لمستخدم معين. ومع ذلك، إذا كان لدى المستخدم في المصدر أرشيف موسع تلقائيا – أي أكثر من علبة بريد أرشيف واحدة، فهذا يعني أن الميزة غير قادرة على ترحيل الأرشيفات الإضافية ويجب أن تفشل.

- **المشكلة: يقوم مستخدمو البريد السحابي الذين يعانون من كتلة smtp proxyAddress غير المملوكة لSED بنقل الخلفية.** عند إنشاء كائنات MailUser للمستأجر الهدف، يجب التأكد من أن كافة عناوين وكيل SMTP تنتمي إلى مؤسسة المستأجر الهدف. إذا كان عنوان وكيل SMTP موجودا على مستخدم البريد الهدف الذي لا ينتمي إلى المستأجر المحلي، يتم منع تحويل MailUser إلى علبة البريد. ويرجع ذلك إلى ضماننا بأن عناصر علبة البريد يمكنها فقط إرسال البريد من المجالات التي يكون المستأجر موثوقا بها (المجالات التي يطالب بها المستأجر):

  - عند مزامنة المستخدمين من أماكن العمل باستخدام Azure AD الاتصال، يمكنك توفير كائنات MailUser المحلية باستخدام ExternalEmailAddress الذي يشير إلى المستأجر المصدر حيث توجد علبة البريد (LaraN@contoso.onmicrosoft.com) وطابع PrimarySMTPAddress كمجال موجود في المستأجر الهدف (Lara.Newton@northwind.com). تتم مزامنة هذه القيم مع المستأجر ويتم توفير مستخدم بريد مناسب وجاهز للتهجير. يظهر مثال على كائن هنا.

    ```powershell
    Get-MailUser LaraN | select ExternalEmailAddress, EmailAddresses

    ExternalEmailAddress               EmailAddresses
    --------------------               --------------
    SMTP:LaraN@contoso.onmicrosoft.com {SMTP:lara.newton@northwind.com}
    ```

   > [!NOTE]
   > عنوان _contoso.onmicrosoft.com_ _غير_ موجود في صفيف EmailAddresses / proxyAddresses.

- **المشكلة: يتم تعديل / إعادة تعيين كائنات MailUser ذات عناوين SMTP الأساسية "الخارجية" إلى المجالات المطالب بها "الداخلية" للشركة**

  كائنات MailUser هي مؤشرات لعلب البريد غير المحلية. في حالة عمليات ترحيل علب البريد عبر المستأجرين، نستخدم كائنات MailUser لتمثيل إما علبة البريد المصدر (من منظور المؤسسة المستهدفة) أو علبة البريد الهدف (من منظور المؤسسة المصدر). سيحتوي MailUsers على ExternalEmailAddress (targetAddress) يشير إلى عنوان smtp الخاص بعلبة البريد الفعلية (ProxyTest@fabrikam.onmicrosoft.com) وعنوان primarySMTP الذي يمثل عنوان SMTP المعروض لمستخدم علبة البريد في الدليل. تختار بعض المؤسسات عرض عنوان SMTP الأساسي كعنوان SMTP خارجي، وليس كعنوان يملكه/يتحقق منه المستأجر المحلي (مثل fabrikam.com بدلا من contoso.com).  ومع ذلك، بمجرد تطبيق كائن خطة خدمة Exchange على MailUser عبر عمليات الترخيص، يتم تعديل عنوان SMTP الأساسي لإظهاره كمجال تم التحقق منه من قبل المؤسسة المحلية (contoso.com). هناك سببان محتملان:

  - عند تطبيق أي خطة خدمة Exchange على MailUser، تبدأ عملية Azure AD بفرض تنقية الوكيل للتأكد من أن المؤسسة المحلية غير قادرة على إرسال البريد أو الانتحال أو البريد من مستأجر آخر. ستتم إزالة أي عنوان SMTP على كائن مستلم مع خطط الخدمة هذه إذا لم يتم التحقق من العنوان من قبل المؤسسة المحلية. كما هو الحال في المثال، لا يتم التحقق من المجال Fabikam.com من قبل المستأجر contoso.onmicrosoft.com، لذلك يزيل الفرك هذا المجال fabrikam.com. إذا كنت ترغب في الاحتفاظ بهذه المجالات الخارجية على MailUser، إما قبل الترحيل أو بعد الترحيل، فستحتاج إلى تغيير عمليات الترحيل لشريط التراخيص بعد اكتمال النقل أو قبل النقل للتأكد من تطبيق العلامة التجارية الخارجية المتوقعة على المستخدمين. ستحتاج إلى التأكد من أن كائن علبة البريد مرخص بشكل صحيح لعدم التأثير على خدمة البريد.
  - يظهر مثال على البرنامج النصي لإزالة خطط الخدمة على MailUser في مستأجر contoso.onmicrosoft.com هنا.

    ```powershell
    $LO = New-MsolLicenseOptions -AccountSkuId "contoso:ENTERPRISEPREMIUM" DisabledPlans "LOCKBOX_ENTERPRISE","EXCHANGE_S_ENTERPRISE","INFORMATION_BARRIERS","MIP_S_CLP2","MIP_S_CLP1","MYANALYTICS_P2","EXCHANGE_ANALYTICS","EQUIVIO_ANALYTICS","THREAT_INTELLIGENCE","PAM_ENTERPRISE","PREMIUM_ENCRYPTION"
    Set-MsolUserLicense -UserPrincipalName ProxyTest@contoso.com LicenseOptions $lo
    ```

       تظهر النتائج في مجموعة ServicePlans المعينة هنا.

    ```powershell
    (Get-MsolUser -UserPrincipalName ProxyTest@contoso.com).licenses | Select-Object -ExpandProperty ServiceStatus |sort ProvisioningStatus -Descending

    ServicePlan           ProvisioningStatus
    -----------           ------------------
    ATP_ENTERPRISE        PendingProvisioning
    MICROSOFT_SEARCH      PendingProvisioning
    INTUNE_O365           PendingActivation
    PAM_ENTERPRISE        Disabled
    EXCHANGE_ANALYTICS    Disabled
    EQUIVIO_ANALYTICS     Disabled
    THREAT_INTELLIGENCE   Disabled
    LOCKBOX_ENTERPRISE    Disabled
    PREMIUM_ENCRYPTION    Disabled
    EXCHANGE_S_ENTERPRISE Disabled
    INFORMATION_BARRIERS  Disabled
    MYANALYTICS_P2        Disabled
    MIP_S_CLP1            Disabled
    MIP_S_CLP2            Disabled
    ADALLOM_S_O365        PendingInput
    RMS_S_ENTERPRISE      Success
    YAMMER_ENTERPRISE     Success
    PROJECTWORKMANAGEMENT Success
    BI_AZURE_P2           Success
    WHITEBOARD_PLAN3      Success
    SHAREPOINTENTERPRISE  Success
    SHAREPOINTWAC         Success
    KAIZALA_STANDALONE    Success
    OFFICESUBSCRIPTION    Success
    MCOSTANDARD           Success
    Deskless              Success
    STREAM_O365_E5        Success
    FLOW_O365_P3          Success
    POWERAPPS_O365_P3     Success
    TEAMS1                Success
    MCOEV                 Success
    MCOMEETADV            Success
    BPOS_S_TODO_3         Success
    FORMS_PLAN_E5         Success
    SWAY                  Success
    ```

    لم يعد PrimarySMTPAddress الخاص بالمستخدم مشفرا. المجال fabrikam.com غير مملوك لمستأجر contoso.onmicrosoft.com وسيستمر كعنوان SMTP الأساسي الموضح في الدليل.

    فيما يلي مثال على ذلك.

    ```powershell
    Get-Recipient ProxyTest | Format-Table -AutoSize UserPrincipalName, PrimarySmtpAddress, ExternalEmailAddress, ExternalDirectoryObjectId
    UserPrincipalName               PrimarySmtpAddress              ExternalEmailAddress                 ExternalDirectoryObjectId
    -----------------               ------------------              --------------------                 -------------------------
    ProxyTest@fabrikam.com          ProxyTest@fabrikam.com          SMTP:ProxyTest@fabrikam.com          e2513482-1d5b-4066-936a-cbc7f8f6f817
    ```

    - عند تعيين msExchRemoteRecipientType إلى 8 (DeprovisionMailbox)، لمستخدمي البريد المحليين الذين تم ترحيلهم إلى المستأجر الهدف، سيقوم منطق تنقية الوكيل في Azure بإزالة المجالات غير المملوكة وإعادة تعيين primarySMTP إلى مجال مملوك. من خلال مسح msExchRemoteRecipientType في MailUser المحلي، لم يعد منطق تنقية الوكيل ينطبق.

      فيما يلي المجموعة الكاملة لخطط الخدمة الحالية التي تتضمن Exchange Online.

      | الاسم                                             |
      | ------------------------------------------------ |
      | تخزين eDiscovery (Premium) (500 غيغابايت)             |
      | صندوق تأمين بيانات العملاء                                 |
      | منع فقدان البيانات                             |
      | Exchange Enterprise CAL Services (EOP، DLP)      |
      | Exchange Essentials                              |
      | مؤسسة Exchange                              |
      | Exchange Online (P1)                             |
      | Exchange Online (خطة 1)                         |
      | Exchange Online (خطة 2)                         |
      | أرشفة Exchange Online لـ Exchange Online    |
      | أرشفة Exchange Online لـ Exchange Server    |
      | Exchange Online الوظيفة الإضافية للمستخدم غير النشط             |
      | Exchange Online Kiosk                            |
      | Exchange Online Multi-Geo                        |
      | Exchange Online الخطة 1                           |
      | Exchange Online POP                              |
      | Exchange Online Protection                       |
      | حواجز المعلومات                             |
      | حماية البيانات ل Office 365 - Premium  |
      | حماية البيانات ل Office 365 - قياسي |
      | Insights بواسطة MyAnalytics                          |
      | التدقيق المتقدم Microsoft 365                  |
      | Microsoft Bookings                               |
      | مركز أعمال Microsoft                        |
      | Microsoft MyAnalytics (كامل)                     |
      | Office 365 eDiscovery (Premium)                   |
      | Microsoft Defender لـ Office 365 (الخطة 1)       |
      | Microsoft Defender لـ Office 365 (الخطة 2)       |
      | Office 365 Privileged Access Management          |
      | تشفير Premium في Office 365                 |
