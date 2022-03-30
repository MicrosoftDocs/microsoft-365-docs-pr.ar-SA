---
title: ترحيل علبة البريد عبر المستأجرين
description: كيفية نقل علب البريد بين Microsoft 365 أو Office 365 المستأجرين.
ms.author: kvice
author: kelleyvice-msft
manager: Laurawi
ms.prod: microsoft-365-enterprise
ms.topic: article
f1.keywords:
- NOCSH
ms.date: 09/21/2020
ms.reviewer: georgiah
ms.custom:
- it-pro
- admindeeplinkMAC
- admindeeplinkEXCHANGE
ms.collection:
- M365-subscription-management
ms.openlocfilehash: a368102b6cb4eabaadd459fd185d18e3a7dc7381
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/08/2022
ms.locfileid: "63577004"
---
# <a name="cross-tenant-mailbox-migration-preview"></a>ترحيل علبة البريد عبر المستأجر (معاينة)

بشكل عام، أثناء عمليات الدمج أو التعمق، تحتاج إلى القدرة على نقل علبة بريد المستخدم Exchange Online بريده إلى مستأجر جديد. يسمح ترحيل علبة البريد عبر المستأجر لمسؤولي المستأجرين باستخدام واجهات معروفة مثل Remote PowerShell و MRS للانتقال إلى المستخدمين إلى المؤسسة الجديدة.

يمكن للمسؤولين استخدام New-MigrationBatch cmdlet، المتوفر من خلال دور إدارة نقل علب البريد، لتنفيذ عمليات نقل المستأجرين عبر المستأجرين.

يجب أن يكون المستخدمون الذين يهاجرون موجودين في نظام المستأجر الهدف Exchange Online باسم "مرسلو البريد"، مع وضع علامة على سمات معينة لتمكين نقل المستأجرين عبر المستأجرين. سيفشل النظام في نقل المستخدمين الذين لم يتم إعدادهم بشكل صحيح في المستأجر الهدف.

عند اكتمال عملية الانتقال، يتم تحويل علبة بريد المستخدم المصدر إلى MailUser، كما يتم وضع الطابع على TargetAddress (الذي يظهر ك ExternalEmailAddress في Exchange) مع عنوان التوجيه إلى المستأجر الوجهة. تترك هذه العملية MailUser القديم في المستأجر المصدر وتسمح بالتعايش المشترك توجيه البريد. عندما تسمح عمليات الأعمال، قد يزيل المستأجر المصدر MailUser المصدر أو يحوله إلى جهة اتصال بريد.

يتم دعم Exchange علب البريد للمستأجرين في المختلط أو السحابة فقط، أو أي تركيبة من الاثنين.

تصف هذه المقالة عملية نقل علب البريد عبر المستأجر وتوفر إرشادات حول كيفية إعداد المستأجرين المصدر والمستأجرين الهدف Exchange Online نقل محتوى علبة البريد.

   > [!NOTE]
   > لقد قمنا مؤخرا بتحديث خطوات الإعداد لتمكين ترحيل علبة البريد عبر المستأجرين بحيث لا يتطلب مخزن مفاتيح Azure بعد الآن! إذا كانت هذه هي المرة الأولى التي تقوم فيها بالمعاينة، فلا حاجة إلى اتخاذ أي إجراء، كما يمكنك المتابعة واتبع الخطوات المفصلة في هذا المستند. إذا كنت قد بدأت في تكوين المستأجرين باستخدام أسلوب AKV السابق، فإننا نوصي بشدة ب إيقاف هذا التكوين أو إزالته لبدء استخدام هذا الأسلوب الجديد. إذا كانت عمليات ترحيل علب البريد في وضع التقدم باستخدام أسلوب AKV السابق، فالرجاء الانتظار حتى تكتمل عمليات الترحيل الموجودة واتبع الخطوات أدناه لتمكين الأسلوب المبسط الجديد. يتم أرشفة خطوات الإعداد المطلوبة في Azure Key Vault ولكن يمكن العثور عليها **[هنا](https://github.com/microsoft/cross-tenant/wiki/V1-Content#cross-tenant-mailbox-migration-preview)**، كمرجع.

## <a name="preparing-source-and-target-tenants"></a>إعداد المستأجرين المصدر والمستأجرين الهدف

### <a name="prerequisites-for-source-and-target-tenants"></a>المتطلبات الأساسية للمستأجرين المصدر والهدف

قبل البدء، تأكد من أن لديك الأذونات اللازمة لتكوين تطبيق نقل علبة البريد في Azure ونقطة نهاية ترحيل EXO وعلاقة مؤسسة EXO.

بالإضافة إلى ذلك، هناك مجموعة أمان واحدة على الأقل تم تمكينها للبريد في المستأجر المصدر مطلوبة. يتم استخدام هذه المجموعات لنطاق قائمة علب البريد التي يمكن أن تنتقل من المستأجر المصدر (أو يشار إليه أحيانا بالموارد) إلى المستأجر الهدف. يسمح هذا لمسؤول المستأجر المصدر بتقييد مجموعة معينة من علب البريد التي يجب نقلها أو تحديد نطاقها، مما يمنع ترحيل المستخدمين غير المقصودين. المجموعات المتداخلة غير معتمدة.

ستحتاج أيضا إلى التواصل مع الشركة الشريكة الموثوق بها (التي سيتم نقل علب البريد معها) للحصول على Microsoft 365 المستأجر الخاص بها. يتم استخدام هذا الم ID المستأجر في الحقل DomainName لعلاقة المؤسسة.

للحصول على هوية المستأجر لاشتراك، سجل الدخول إلى [مركز مسؤولي Microsoft 365 واذهب](https://go.microsoft.com/fwlink/p/?linkid=2024339) إلى [https://aad.portal.azure.com/\#blade/Microsoft_AAD_IAM/ActiveDirectoryMenuBlade/Properties](https://aad.portal.azure.com/#blade/Microsoft_AAD_IAM/ActiveDirectoryMenuBlade/Properties). انقر فوق أيقونة النسخ ل خاصية "المايجر" لنسخها إلى الحافظة.

### <a name="configuration-steps-to-enable-your-tenants-for-cross-tenant-mailbox-migrations"></a>خطوات التكوين لتمكين المستأجرين من ترحيل علب البريد عبر المستأجرين

   > [!NOTE]
   > يجب تكوين الهدف (الوجهة) أولا. لإكمال هذه الخطوات، لست مطالبا بأن يكون لديك أو تعرف بيانات اعتماد مسؤول المستأجر لكل من المستأجر المصدر والمستأجر الهدف. يمكن تنفيذ الخطوات بشكل فردي لكل مستأجر من قبل مسؤولي مختلفين.

### <a name="prepare-the-target-destination-tenant-by-creating-the-migration-application-and-secret"></a>إعداد المستأجر الهدف (الوجهة) عن طريق إنشاء تطبيق الترحيل والسر

1. تسجيل الدخول إلى مدخل Azure AD (<https://portal.azure.com>) باستخدام بيانات اعتماد مسؤول المستأجر الهدف

   ![Azure Logon](../media/tenant-to-tenant-mailbox-move/74f26681e12df3308c7823ee7d527587.png)

2. انقر فوق طريقة العرض ضمن إدارة Azure Active Directory.

   ![زر Azure Active Directory](../media/tenant-to-tenant-mailbox-move/109ac3dfbac2403fb288f085767f393b.png)

3. على شريط التنقل الأيسر، حدد تسجيلات التطبيق.

4. تحديد تسجيل جديد

   ![تطبيق جديد](../media/tenant-to-tenant-mailbox-move/b36698df128e705eacff4bff7231056a.png)

5. في صفحة تسجيل تطبيق، ضمن أنواع الحسابات المعتمدة، حدد الحسابات في أي دليل هيكلي (أي دليل Azure AD - متعدد الصفحات). بعد ذلك، ضمن إعادة توجيه URI (اختياري)، حدد ويب وأدخل <https://office.com>. وأخيرا، حدد تسجيل.

   ![تسجيل التطبيق](../media/tenant-to-tenant-mailbox-move/edcdf18b9f504c47284fe4afb982c433.png)

6. في الزاوية العلوية اليسرى من الصفحة، سترى إعلاما منبثقا يفيد بأنه تم إنشاء التطبيق بنجاح.

7. ارجع إلى الصفحة الرئيسية، Azure Active Directory وانقر فوق تسجيلات التطبيق.

8. ضمن التطبيقات المملوكة، ابحث عن التطبيق الذي أنشأته وانقر فوقه.

9. ضمن ^Essentials، ستحتاج إلى نسخ "عنوان التطبيق" (العميل) كما ستحتاج إليه لاحقا لإنشاء عنوان URL للمستأجر الهدف.

10. الآن، على شريط التنقل الأيسر، انقر فوق أذونات API لعرض الأذونات المعينة لتطبيقك.

11. بشكل افتراضي، المستخدم. يتم تعيين أذونات القراءة للتطبيق الذي أنشأته، ولكننا لا نطلبها لإزالة علبة البريد، يمكنك إزالة هذا الإذن.

    ![أذونات التطبيق](../media/tenant-to-tenant-mailbox-move/6a8c13a36cb3e10964a6920b8138e12b.png)

12. نحتاج الآن إلى إضافة إذن  الترحيل لعلبة البريد، حدد إضافة إذن

13. في النوافذ طلب أذونات API، حدد واجهات برمجة التطبيقات التي تستخدمها المؤسسة، وابحث عن Office 365 Exchange Online، ثم حددها.

    ![حدد API](../media/tenant-to-tenant-mailbox-move/0b4dc1eea3910e9c475724d9473aca58.png)

14. بعد ذلك، حدد أذونات التطبيق

15. بعد ذلك، ضمن تحديد الأذونات، قم بتوسيع علبة البريد، ثم حدد علبة البريد.الترحيل، وأضف الأذونات في الأسفل على الشاشة.

    ![تعيين API](../media/tenant-to-tenant-mailbox-move/0038a4cf74bb13de0feb51800e078803.png)

16. حدد الآن الشهادات & على شريط التنقل الأيسر للتطبيق.

17. ضمن أسرار العميل، حدد سري عميل جديد.

    ![أسرار العميل](../media/tenant-to-tenant-mailbox-move/273dafd5e6c6455695f9baf35ef9977a.png)

18. في النافذة إضافة عميل سري، أدخل وصفا، ثم قم بتكوين إعدادات انتهاء الصلاحية المطلوبة.

      > [!NOTE]
      > هذه هي كلمة المرور التي سيتم استخدامها عند إنشاء نقطة نهاية الترحيل. من المهم للغاية نسخ كلمة المرور هذه إلى الحافظة الخاصة بك ونسخ كلمة المرور هذه إلى موقع آمن/سري لكلمة المرور. هذه هي المرة الوحيدة التي يمكنك فيها رؤية كلمة المرور هذه! إذا فقدته بطريقة ما أو كنت بحاجة إلى إعادة تعيينه، يمكنك تسجيل الدخول مرة أخرى إلى مدخل Azure، انتقل إلى تسجيلات التطبيق، واعثر على تطبيق الترحيل، وحدد شهادات أسرار &، وأنشئ سر جديد لتطبيقك.

19. الآن وقد قمت بإنشاء تطبيق الترحيل والسر بنجاح، ستحتاج إلى الموافقة على التطبيق. للموافقة على التطبيق، ارجع إلى صفحة Azure Active Directory المنتقل إليه، وانقر فوق تطبيقات Enterprise في التنقل الأيسر، واعثر على تطبيق الترحيل الذي أنشأته، وحدده، وحدد الأذونات في التنقل الأيسر.

20. انقر فوق الزر منح موافقة المسؤول ل [المستأجر الخاص بك].

21. سيتم فتح نافذة مستعرض جديدة وحدد قبول.

22. يمكنك العودة إلى نافذة المدخل وتحديد تحديث لتأكيد قبولك.

23. قم بصياغة عنوان URL لإرساله إلى شريكك الموثوق به (مسؤول المستأجر المصدر) بحيث يمكنه أيضا قبول التطبيق لتمكين ترحيل علبة البريد. فيما يلي مثال على عنوان URL لتوفيره لهم ستحتاج إلى "معر ة التطبيق" للتطبيق الذي أنشأته:

    ```powershell
    https://login.microsoftonline.com/sourcetenant.onmicrosoft.com/adminconsent?client_id=[application_id_of_the_app_you_just_created]&redirect_uri=https://office.com
    ```

    > [!NOTE]
    > ستحتاج إلى "معر ة التطبيق" الخاص بتطبيق ترحيل علبة البريد الذي أنشأته للتو.
    >
    > ستحتاج إلى استبدال sourcetenant.onmicrosoft.com أعلاه بالمستأجرين المصدر onmicrosoft.com الصحيح.
    >
    > ستحتاج أيضا إلى استبدال [application_id_of_the_app_you_just_created] بم ID التطبيق الخاص بتطبيق ترحيل علبة البريد الذي أنشأته للتو.

### <a name="prepare-the-target-tenant-by-creating-the-exchange-online-migration-endpoint-and-organization-relationship"></a>إعداد المستأجر الهدف عن طريق إنشاء نقطة Exchange Online نهاية الترحيل وعلاقة المؤسسة

1. إنشاء اتصال PowerShell عن بعد بالهدف Exchange Online المستأجر.

2. إنشاء نقطة نهاية ترحيل جديدة لحركات نقل علب البريد عبر المستأجر

   > [!NOTE]
   > ستحتاج إلى تعريف التطبيق الخاص بتطبيق ترحيل علبة البريد الذي أنشأته للتو وكلمة المرور (السرية) التي قمت بتكوينها أثناء هذه العملية. قد يختلف أيضا Microsoft 365 السحابة الذي تستخدمه نقطة النهاية. الرجاء الرجوع إلى [Microsoft 365 نقاط](/microsoft-365/enterprise/microsoft-365-endpoints) النهاية وتحديد المثيل الصحيح للمستأجر ومراجعة Exchange Online تحسين العنوان المطلوب واستبداله حسب الحاجة.

   ```powershell
   
   # Enable customization if tenant is dehydrated
     $dehydrated=Get-OrganizationConfig | fl isdehydrated
     if ($dehy -eq $true) {Enable-OrganizationCustomization}
     
   $AppId = "[guid copied from the migrations app]"

   $Credential = New-Object -TypeName System.Management.Automation.PSCredential -ArgumentList $AppId, (ConvertTo-SecureString -String "[this is your secret password you saved in the previous steps]" -AsPlainText -Force)

   New-MigrationEndpoint -RemoteServer outlook.office.com -RemoteTenant "sourcetenant.onmicrosoft.com" -Credentials $Credential -ExchangeRemoteMove:$true -Name "[the name of your migration endpoint]" -ApplicationId $AppId
   ```

3. يمكنك إنشاء كائن علاقة مؤسسة جديد أو تحريره إلى المستأجر المصدر.

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

### <a name="prepare-the-source-current-mailbox-location-tenant-by-accepting-the-migration-application-and-configuring-the-organization-relationship"></a>إعداد المستأجر المصدر (موقع علبة البريد الحالي) من خلال قبول تطبيق الترحيل وتكوين علاقة المؤسسة

1. من مستعرض، انتقل إلى ارتباط URL الذي وفره شريكك الموثوق به للموافقة على تطبيق ترحيل علبة البريد. سيبدو عنوان URL كما يلي:

   ```powershell
   https://login.microsoftonline.com/sourcetenant.onmicrosoft.com/adminconsent?client_id=[application_id_of_the_app_you_just_created]&redirect_uri=https://office.com
   ```

   > [!NOTE]
   > ستحتاج إلى "معر ة التطبيق" الخاص بتطبيق ترحيل علبة البريد الذي أنشأته للتو.
   > ستحتاج إلى استبدال sourcetenant.onmicrosoft.com أعلاه بالمستأجرين المصدر onmicrosoft.com الصحيح.
   > ستحتاج أيضا إلى استبدال [application_id_of_the_app_you_just_created] بم ID التطبيق الخاص بتطبيق ترحيل علبة البريد الذي أنشأته للتو.

2. اقبل التطبيق عند ظهور النافذة المنبثقة. يمكنك أيضا تسجيل الدخول إلى مدخل Azure Active Directory والعثور على التطبيق ضمن تطبيقات المؤسسة.

3. يمكنك إنشاء كائن علاقة مؤسسة جديد أو تحريره إلى المستأجر الهدف (الوجهة) من نافذة PowerShell Exchange Online البعيد.

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
> إن اسم نطاق المستأجر الذي تدخله $sourceTenantId $targetTenantId هو GUID وليس اسم مجال المستأجر. للحصول على مثال لمعرف المستأجر ومعلومات حول البحث عن "معرف المستأجر"، راجع البحث عن [Microsoft 365 المستأجر](/onedrive/find-your-office-365-tenant-id).
   
### <a name="how-do-i-know-this-worked"></a>كيف أتأكد من نجاح هذا الأمر؟

يمكنك التحقق من تكوين ترحيل علبة البريد عبر المستأجر عن طريق تشغيل [الأمر cmdlet Test-MigrationServerAvailability](/powershell/module/exchange/Test-MigrationServerAvailability) مقابل نقطة نهاية الترحيل عبر المستأجر التي أنشأتها على المستأجر الهدف.

   > [!NOTE]
   >
   > - المستأجر الهدف:
   > 
   > Test-MigrationServerAvailability -Endpoint "[اسم نقطة نهاية الترحيل عبر المستأجر]"
   >
   > Get-OrganizationRelationship | fl name, DomainNames, MailboxMoveEnabled, MailboxMoveCapability
   >
   > - المستأجر المصدر:
   > 
   > Get-OrganizationRelationship | fl name, DomainNames, MailboxMoveEnabled, MailboxMoveCapability 

### <a name="move-mailboxes-back-to-the-original-source"></a>نقل علب البريد مرة أخرى إلى المصدر الأصلي

إذا كانت علبة البريد مطلوبة للعودة إلى مستأجر المصدر الأصلي، يجب تشغيل مجموعة الخطوات والنصية نفسها في كل من المستأجرين المصدر الجديد والمستأجر الهدف الجديد. سيتم تحديث الكائن "علاقة المؤسسة" الموجود أو إلحاقه، ولن يتم إعادة إنشائه

## <a name="prepare-target-user-objects-for-migration"></a>إعداد كائنات المستخدم الهدف ل الترحيل

يجب أن يكون المستخدمون الذين يهاجرون موجودين في المستأجر الهدف ونظام Exchange Online (كمستخدمي البريد) وضعت عليهم سمات معينة لتمكين نقل المستأجرين عبر المستأجرين. سيفشل النظام في نقل المستخدمين الذين لم يتم إعدادهم بشكل صحيح في المستأجر الهدف. يستعرض القسم التالي تفاصيل متطلبات كائن MailUser للمستأجر الهدف.

### <a name="prerequisites-for-target-user-objects"></a>المتطلبات الأساسية كائنات المستخدم الهدف

تأكد من تعيين العناصر والصفات التالية في المؤسسة الهدف.

1. بالنسبة لأي علبة بريد تنتقل من مؤسسة مصدر، يجب عليك توفير كائن MailUser في المؤسسة الهدف:

   - يجب أن يكون لدى "مرسل البريد الهدف" هذه السمات من علبة البريد المصدر أو تعيينها باستخدام كائن المستخدم الجديد:
      - ExchangeGUID (التدفق المباشر من المصدر إلى الهدف): يجب أن تتطابق علبة البريد GUID. لن يتم متابعة عملية نقل إذا لم يكن موجودا على الكائن الهدف.
      - ArchiveGUID (التدفق المباشر من المصدر إلى الهدف): يجب أن يكون GUID الخاص الأرشيف متطابقا. لن يتم متابعة عملية نقل إذا لم يكن موجودا على الكائن الهدف. (هذا مطلوب فقط إذا كانت علبة البريد المصدر تم تمكين الأرشيف).
      - LegacyExchangeDN (التدفق ك proxyAddress, "x500:\<LegacyExchangeDN>"): يجب أن يكون LegacyExchangeDN موجودا على MailUser الهدف ك x500: proxyAddress. بالإضافة إلى ذلك، ستحتاج أيضا إلى نسخ كل عناوين x500 من علبة البريد المصدر إلى مستخدم البريد الهدف. لن يتم متابعة عمليات الانتقال إذا لم تكن موجودة على الكائن الهدف.
      - UserPrincipalName: ستحاذي UPN هوية المستخدم الجديدة أو الشركة المستهدفة (على سبيل المثال، user@northwindtraders.onmicrosoft.com).
      - SMTPAddress الأساسي: سيتم محاذاة عنوان SMTP الأساسي مع الشركة الجديدة للمستخدم (على سبيل المثال، user@northwind.com).
      - TargetAddress/ExternalEmailAddress: سيرجع MailUser علبة بريد المستخدم الحالية المستضافة في المستأجر المصدر (على سبيل المثال user@contoso.onmicrosoft.com). عند تعيين هذه القيمة، تحقق من أن لديك/تقوم أيضا بتعيين PrimarySMTPAddress أو هذه القيمة سيتم تعيين PrimarySMTPAddress، مما يؤدي إلى فشل النقل.
      - لا يمكنك إضافة عناوين وكيل smtp القديمة من علبة البريد المصدر إلى MailUser الهدف. على سبيل المثال، لا يمكنك الاحتفاظ contoso.com MEU في fabrikam.onmicrosoft.com المستأجر). تقترن المجالات بمستأجر Azure AD أو Exchange Online واحد فقط.

     مثال **على كائن** MailUser الهدف:

     | السمة            | القيمة                                                                                                                   |
     | -------------------- | ----------------------------------------------------------------------------------------------------------------------- |
     | الاسم المستعار                | LaraN                                                                                                                   |
     | RecipientType        | MailUser                                                                                                                |
     | RecipientTypeDetails | MailUser                                                                                                                |
     | UserPrincipalName    | LaraN@northwintraders.onmicrosoft.com                                                                                   |
     | PrimarySmtpAddress   | Lara.Newton@northwind.com                                                                                               |
     | ExternalEmailAddress | SMTP:LaraN@contoso.onmicrosoft.com                                                                                      |
     | ExchangeGuid         | 1ec059c7-8396-4d0b-af4e-d6bd4c12a8d8                                                                                    |
     | LegacyExchangeDN     | /o=First Organization/ou=Exchange الإدارية                                                                  |
     |                      | (FYDIBOHF23SPDLT)/cn=Recipients/cn=74e5385fce4b46d19006876949855035Lara                                                 |
     | EmailAddresses       | x500:/o=First Organization/ou=Exchange المجموعة الإدارية (FYDIBOHF23SPDLT)/cn=Recipients/cn=d11ec1a2cacd4f81858c8190 |
     |                      | 7273f1f9-Lara                                                                                                           |
     |                      | smtp:LaraN@northwindtraders.onmicrosoft.com                                                                             |
     |                      | SMTP:Lara.Newton@northwind.com                                                                                          |
     |                      |                                                                                                                         |

     مثال **حول كائن علبة** بريد المصدر:

     | السمة            | القيمة                                                                   |
     | -------------------- | ----------------------------------------------------------------------- |
     | الاسم المستعار                | LaraN                                                                   |
     | RecipientType        | UserMailbox                                                             |
     | RecipientTypeDetails | UserMailbox                                                             |
     | UserPrincipalName    | LaraN@contoso.onmicrosoft.com                                           |
     | PrimarySmtpAddress   | Lara.Newton@contoso.com                                                 |
     | ExchangeGuid         | 1ec059c7-8396-4d0b-af4e-d6bd4c12a8d8                                    |
     | LegacyExchangeDN     | /o=First Organization/ou=Exchange الإدارية                  |
     |                      | (FYDIBOHF23SPDLT)/cn=Recipients/cn=d11ec1a2cacd4f81858c81907273f1f9Lara |
     | EmailAddresses       | smtp:LaraN@contoso.onmicrosoft.com                                      |
     |                      | SMTP:Lara.Newton@contoso.com                                            |
     |                      |                                                                         |

   - قد يتم تضمين سمات إضافية في Exchange المختلطة بالفعل. وإذا لم يكن الأمر كذلك، يجب تضمينها.
   - msExchBlockedSendersHash – إعادة كتابة بيانات المرسلين الآمنة والمحظرة عبر الإنترنت من العملاء إلى Active Directory في الموقع.
   - msExchSafeRecipientsHash – إعادة كتابة بيانات المرسلين الآمنة والمملوكة عبر الإنترنت من العملاء إلى Active Directory في الموقع.
   - msExchSafeSendersHash – إعادة كتابة بيانات المرسلين الآمنة والمحظرة عبر الإنترنت من العملاء إلى Active Directory في الموقع.

2. إذا كانت علبة البريد المصدر في LitigationHold وكان حجم علبة البريد المصدر "العناصر القابلة لاستردادها" أكبر من حجم قاعدة البيانات الافتراضية (30 غيغابايت)، لن يتم المتابعة نظرا لأن الحصة النسبية الهدف أقل من حجم علبة البريد المصدر. يمكنك تحديث كائن MailUser الهدف لنقل علامة علبة بريد ELC من البيئة المصدر إلى الهدف، مما يؤدي إلى تشغيل النظام الهدف لتوسيع الحصة النسبية ل MailUser إلى 100 غيغابايت، مما يسمح بالنقل إلى الهدف. ستعمل هذه الإرشادات فقط للهوية المختلطة التي تعمل ب Azure AD الاتصال، حيث لا يتم عرض الأوامر الخاصة بطوابع علامة ELC لمسؤولي المستأجرين.

    > [!NOTE]
    > عينة – كما هو، لا يوجد ضمان
    >
    > يفترض هذا البرنامج النصي اتصالا بكل من علبة البريد المصدر (للحصول على قيم المصدر) والهدف المحلي Active Directory (لطوابع كائن ADUser). إذا كان المصدر لديه دعوى قضائية أو تم تمكين استرداد عنصر واحد، فحدد هذا على الحساب الوجهة.  سيزيد ذلك حجم تفريغ حساب الوجهة إلى 100 غيغابايت.

    ```powershell
    $ELCValue = 0
    if ($source.LitigationHoldEnabled) {$ELCValue = $ELCValue + 8} if ($source.SingleItemRecoveryEnabled) {$ELCValue = $ELCValue + 16} if ($ELCValue -gt 0) {Set-ADUser -Server $domainController -Identity $destination.SamAccountName -Replace @{msExchELCMailboxFlags=$ELCValue}}
    ```

3. يمكن للمستأجرين الهدف غير المختلط تعديل الحصة النسبية في مجلد العناصر القابلة لاستردادها لمرسلي البريد قبل الترحيل عن طريق تشغيل الأمر التالي لتمكين الاحتجاز بسبب الدعاوى القضائية على كائن MailUser وزيادة الحصة النسبية إلى 100 غيغابايت: `Set-MailUser -EnableLitigationHoldForMigration`. لاحظ أن هذا لن يعمل مع المستأجرين في المختلط.

4. يجب أن يتم ترخيص المستخدمين في المؤسسة المستهدفة باستخدام Exchange Online المناسبة القابلة للتطبيق على المؤسسة. يمكنك تطبيق ترخيص قبل نقل علبة البريد ولكن فقط بمجرد إعداد MailUser الهدف بشكل صحيح باستخدام ExchangeGUID وعناوين الوكيل. يؤدي تطبيق ترخيص قبل تطبيق ExchangeGUID إلى توفير علبة بريد جديدة في المؤسسة الهدف.

    > [!NOTE]
    > عند تطبيق ترخيص على علبة بريد أو كائن MailUser، يتم مسح كل نوع SMTP proxyAddresses لضمان تضمين المجالات المتحقق منها فقط في صفيف Exchange EmailAddresses.

5. يجب أن تضمن عدم وجود ExchangeGuid سابق لمرسل البريد الهدف لا يطابق ExchangeGuid المصدر. قد يحدث ذلك إذا تم ترخيص MEU الهدف مسبقا Exchange Online علبة بريد وتوفيرها. إذا كان MailUser الهدف مرخصا مسبقا ل ExchangeGuid أو لديه لا يطابق ExchangeGuid المصدر، يجب إجراء عملية تنظيف ل MEU السحابية. بالنسبة إلى MEUs السحابية هذه، يمكنك تشغيل `Set-User <identity> -PermanentlyClearPreviousMailboxInfo`.

    > [!CAUTION]
    > لا يمكن التراجع عن هذه العملية. إذا كان الكائن لديه علبة بريد ناعمة، فلا يمكن استعادتها بعد هذه النقطة. ومع ذلك، بمجرد مسحه، يمكنك مزامنة ExchangeGuid الصحيح مع الكائن الهدف وستتصل MRS علبة البريد المصدر لعلبة البريد الهدف التي تم إنشاؤها حديثا. (مرجع مدونة EHLO على المعلمة الجديدة.)

    ابحث عن العناصر التي كانت في السابق علب بريد باستخدام هذا الأمر.

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

    ألغ مسح علبة البريد المحذوفة تلقائيا باستخدام هذا الأمر.

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

### <a name="perform-mailbox-migrations"></a>تنفيذ عمليات ترحيل علب البريد

يتم بدء Exchange ترحيل علب البريد من المستأجر الهدف ك دفعات ترحيل. تشبه هذه الطريقة التي تعمل بها دفعات الترحيل على متن الطائرة عند الترحيل من Exchange المحلية إلى Microsoft 365.

### <a name="create-migration-batches"></a>إنشاء دفعات الترحيل

فيما يلي مثال على أمر cmdlet الخاص بدفعة الترحيل للانخريط في التحركات.

```powershell
New-MigrationBatch -Name T2Tbatch -SourceEndpoint target_source_7977 -CSVData ([System.IO.File]::ReadAllBytes('users.csv')) -Autostart -TargetDeliveryDomain target.onmicrosoft.com

Identity                   Status  Type               TotalCount
--------                   ------  ----               ----------
T2Tbatch                   Syncing ExchangeRemoteMove 1
```

> [!NOTE]
> يجب أن يكون عنوان البريد الإلكتروني في ملف CSV هو العنوان المحدد في المستأجر الهدف، وليس المستأجر المصدر.
>
> [لمزيد من المعلومات حول cmdlet، انقر هنا](/powershell/module/exchange/new-migrationbatch)
>
> [على سبيل المثال، انقر فوق ملف CSV هنا](/exchange/csv-files-for-mailbox-migration-exchange-2013-help)

يتم أيضا دعم إرسال دفعة الترحيل <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">من مركز إدارة</a> Exchange الجديد عند تحديد خيار المستأجر المتقاطع.

### <a name="update-on-premises-mailusers"></a>تحديث "مرسلو البريد" في الموقع

بمجرد انتقال علبة البريد من مصدر إلى هدف، يجب أن تضمن تحديث مستخدمي البريد في الموقع، في كل من المصدر والهدف، بالهدف الجديدAddress. في الأمثلة، يكون targetDeliveryDomain المستخدم في **عملية contoso.onmicrosoft.com**. قم بتحديث مستخدمي البريد بهذا الهدفAddress.

## <a name="frequently-asked-questions"></a>الأسئلة المتكررة

**هل نحتاج إلى تحديث RemoteMailboxes في المصدر المحلية بعد عملية الانتقال؟**

نعم، يجب تحديث targetAddress (RemoteRoutingAddress/ExternalEmailAddress) للمستخدمين المصدر المحلي عندما تنتقل علبة بريد المستأجر المصدر إلى المستأجر الهدف.  على الرغم من أن توجيه البريد يمكن أن يتبع الإحالات عبر عدة مستخدمين للبريد باستخدام targetAddresses مختلف، يجب أن تستهدف عمليات البحث "الفر/الانشغال" لمستخدمي البريد موقع مستخدم علبة البريد. لن تلاحق عمليات البحث المجانية/المشغولة عمليات إعادة توجيه متعددة.

**هل Teams الاجتماعات المشتركة بين المستأجرين؟**

سيتم نقل الاجتماعات، ولكن عنوان URL Teams لا يتم تحديثه عندما تقوم العناصر بترحيل المستأجر عبر المستأجر. بما أن عنوان URL سيكون غير صالح في المستأجر الهدف، ستحتاج إلى إزالة Teams الاجتماعات وإعادة إنشائها.

**هل يقوم Teams مجلد الدردشة بترحيل المستأجر عبر المستأجر؟**

لا، Teams مجلد الدردشة لا يقوم بترحيل المستأجر عبر المستأجر.

**كيف يمكنني رؤية الانتقالات فقط التي تكون عبر المستأجرين، وليس الانتقال إلى ال متن الطائرة والتنقل خارجها؟**

استخدم _المعلمة Flags_ . فيما يلي مثال على ذلك.

```powershell
Get-MoveRequest -Flags "CrossTenant"
```

**هل يمكنك توفير برامج نصية على سبيل المثال لنسخ السمات المستخدمة في الاختبار؟**

> [!NOTE]
> عينة – كما هو، لا يوجد ضمان يفترض هذا البرنامج النصي اتصالا بكل من علبة البريد المصدر (للحصول على القيم المصدر) والهدف المحلي خدمات مجال Active Directory (لتضمين كائن ADUser). إذا كان المصدر لديه دعوى قضائية أو تم تمكين استرداد عنصر واحد، فحدد هذا على الحساب الوجهة.  سيزيد ذلك حجم تفريغ حساب الوجهة إلى 100 غيغابايت.



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
   Start-ADSyncCycle
   ```

**كيف يمكننا الوصول إلى Outlook يوم 1 بعد نقل علبة بريد الاستخدام؟**

بما أنه يمكن لمستأجر واحد فقط امتلاك مجال، لن يتم إقترن SMTPAddress الأساسي السابق بالمستخدم في المستأجر الهدف عند اكتمال نقل علبة البريد؛ فقط تلك المجالات المقترنة بالمستأجر الجديد. Outlook المستخدمين UPN الجديد للمصادقة على الخدمة ويتوقع ملف تعريف Outlook العثور على SMTPAddress الأساسية القديمة لمطابقة علبة البريد في النظام الهدف. بما أن العنوان القديم غير في النظام الهدف، لن يتصل ملف تعريف outlook للعثور على علبة البريد التي تم نقلها حديثا.

لهذا النشر الأولي، يجب على المستخدمين إعادة إنشاء ملف التعريف الخاص بهم باستخدام عنوان UPN الجديد وعنوان SMTP الأساسي ومحتوى OST resync.

> [!NOTE]
> التخطيط وفقا لذلك عند دفع المستخدمين للاكتمال. يجب مراعاة استخدام الشبكة و السعة عند Outlook ملفات تعريف العميل وتنزيل ملفات OST و OAB اللاحقة إلى العملاء.

**ما Exchange أدوار RBAC التي أحتاج إلى أن أكون عضوا فيها لإعداد نقل عبر المستأجرين أو إكماله؟**

هناك مصفوفة أدوار تستند إلى افتراض الواجبات المفوضة عند تنفيذ نقل علبة البريد. في الوقت الحالي، هناك دوران مطلوبان:

- الدور الأول هو لمهمة إعداد مرة واحدة تقوم بإنشاء تخويل نقل المحتوى إلى حد المستأجر/المؤسسة أو خارجه. بما أن نقل البيانات خارج سيطرتك التنظيمية هو مصدر قلق بالغ لكل الشركات، فقد اخترنا أعلى دور تم تعيينه لمسؤول المؤسسة (OrgAdmin). يجب أن يغير هذا الدور أو قم بإعداد تنظيم مؤسسة جديد يعرف إمكانية -MailboxMoveCapability مع المؤسسة البعيدة. يمكن فقط ل OrgAdmin تغيير إعداد MailboxMoveCapability، بينما يمكن إدارة السمات الأخرى على OrganizationRelationship من قبل مسؤول المشاركة الخارجية.

- يمكن تفويض دور تنفيذ أوامر نقل فعلية إلى دالة ذات مستوى أدنى. يتم تعيين دور نقل علب البريد إلى إمكانية نقل علب البريد داخل المؤسسة أو خارجها.

**كيف نستهدف عنوان SMTP المحدد ل TargetAddress (TargetDeliveryDomain) على علبة البريد التي تم تحويلها (إلى تحويل MailUser)؟**

Exchange علبة البريد باستخدام MRS على وضع targetAddress على علبة البريد المصدر الأصلية عند التحويل إلى MailUser من خلال مطابقة عنوان بريد إلكتروني (proxyAddress) على الكائن الهدف. تأخذ العملية القيمة -TargetDeliveryDomain التي تم تمريرها إلى الأمر نقل، ثم التحقق من وكيل مطابق لذلك المجال على الجانب الهدف. عندما نعثر على تطابق، يتم استخدام الوكيل المطابقAddress لتعيين كائن ExternalEmailAddress (targetAddress) على كائن علبة البريد التي تم تحويلها (الآن MailUser).

**كيف يتم انتقال أذونات علبة البريد؟**

تتضمن أذونات علبة البريد إرسال نيابة عن والوصول إلى علبة البريد:

- يخزن إرسال نيابة عن (AD:publicDelegates) DN للمستلمين الذين لهم حق الوصول إلى علبة بريد المستخدم كمفوض. يتم تخزين هذه القيمة في Active Directory ولا يتم نقلها حاليا كجزء من انتقال علبة البريد. إذا كانت علبة البريد المصدر بها مجموعة publicDelegates، ستحتاج إلى وضع البوابات العامة في علبة البريد الهدف بعد اكتمال تحويل MEU إلى علبة البريد في البيئة الهدف عن طريق تشغيل `Set-Mailbox <principle> -GrantSendOnBehalfTo <delegate>`.

- سيتم نقل أذونات علبة البريد المخزنة في علبة البريد مع علبة البريد عند نقل كل من المدير والمفوض إلى النظام الهدف. على سبيل المثال، TestUser_7 المستخدم FullAccesss لعلبة البريد TestUser_8 في المستأجر SourceCompany.onmicrosoft.com. بعد اكتمال نقل علبة البريد TargetCompany.onmicrosoft.com، يتم إعداد الأذونات نفسها في الدليل الهدف. تظهر الأمثلة التي *تستخدم Get-MailboxPermission* TestUser_7 في كل من المستأجرين المصدر والهدف أدناه. Exchange cmdlets السابقة بالمصدر والهدف وفقا لذلك.

فيما يلي مثال على إخراج إذن علبة البريد قبل عملية نقل.

```powershell
Get-SourceMailboxPermission TestUser_7 | Format-Table -AutoSize User, AccessRights, IsInherited, Deny

User                                             AccessRights                         IsInherited Deny
----                                             ------------                         ----------- ----
NT AUTHORITY\SELF                                {FullAccess, ReadPermission}         False       False
TestUser_8@SourceCompany.onmicrosoft.com         {FullAccess}                         False       False
```

فيما يلي مثال على إخراج إذن علبة البريد بعد عملية الانتقال.

```powershell
Get-TargetMailboxPermission TestUser_7 | Format-Table -AutoSize User, AccessRights, IsInherited, Deny

User                                             AccessRights                         IsInherited Deny
----                                             ------------                         ----------- ----
NT AUTHORITY\SELF                                {FullAccess, ReadPermission}         False       False
TestUser_8@TargetCompany.onmicrosoft.com         {FullAccess}                         False       False
```

> [!NOTE]
> لا يتم دعم أذونات علبة البريد والتقويم عبر المستأجرين. يجب تنظيم الأساسيات والمفوضين في دفعات نقل مدمجة بحيث يتم نقل علب البريد المتصلة هذه في الوقت نفسه من المستأجر المصدر.

**ما هو وكيل X500 الذي يجب إضافته إلى عناوين وكيل MailUser الهدف لتمكين الترحيل؟**

يتطلب ترحيل علبة البريد عبر المستأجرين أن يتم وضع طابع على القيمة LegacyExchangeDN لكائن علبة البريد المصدر كعنوان بريد إلكتروني x500 على كائن MailUser الهدف.

على سبيل المثال:

```powershell
LegacyExchangeDN value on source mailbox is:
/o=First Organization/ou=Exchange Administrative Group(FYDIBOHF23SPDLT)/cn=Recipients/cn=d11ec1a2cacd4f81858c81907273f1f9Lara

so, the x500 email address to be added to target MailUser object would be:
x500:/o=First Organization/ou=Exchange Administrative Group (FYDIBOHF23SPDLT)/cn=Recipients/cn=d11ec1a2cacd4f81858c81907273f1f9-Lara
```

> [!NOTE]
> بالإضافة إلى وكيل X500 هذا، ستحتاج إلى نسخ كل الوكلاء X500 من علبة البريد في المصدر إلى علبة البريد في الهدف.

**هل يمكن للمستأجر المصدر والمستأجر الهدف استخدام اسم المجال نفسه؟**

لا. يجب أن تكون أسماء نطاقات المستأجر المصدر والمستأجر الهدف فريدة. على سبيل المثال، يتم contoso.com مجال المصدر والمجال الهدف fourthcoffee.com.

**هل سيتم نقل علب البريد المشتركة وما زالت تعمل؟**

نعم، ولكننا لا نحتفظ إلا بأذونات المتجر كما هو موضح في المقالات التالية:

- [مستندات Microsoft | إدارة الأذونات للمستلمين في Exchange Online](/exchange/recipients-in-exchange-online/manage-permissions-for-recipients)

- [دعم Microsoft | كيفية منح Exchange علب Outlook البريد في Office 365 مخصصة](https://support.microsoft.com/topic/how-to-grant-exchange-and-outlook-mailbox-permissions-in-office-365-dedicated-bac01b2c-08ff-2eac-e1c8-6dd01cf77287)

**هل لديك أي توصيات بشأن الدفعات؟**

لا تتجاوز 2000 علبة بريد لكل دفعة. نوصي بشدة بتقديم دفعات قبل تاريخ المزامنة بمدة أسبوعين حيث لا يوجد أي تأثير على المستخدمين أثناء المزامنة. إذا كنت بحاجة إلى إرشادات حول علب البريد التي يزيد عددها عن 50000، يمكنك الوصول إلى قائمة توزيع الملاحظات الهندسية في crosstenantmigrationpreview@service.microsoft.com.

**ماذا لو كنت أستخدم تشفير الخدمة مع "مفتاح العميل"؟**

سيتم فك تشفير علبة البريد قبل الانتقال. تأكد من تكوين "مفتاح العميل" في المستأجر الهدف إذا كان لا يزال مطلوبا. راجع [هنا](/microsoft-365/compliance/customer-key-overview) للحصول على مزيد من المعلومات.

**ما هو وقت الترحيل المقدر؟**

لمساعدتك على التخطيط ل الترحيل، يعرض الجدول الحالي هنا [](/exchange/mailbox-migration/office-365-migration-best-practices#estimated-migration-times) إرشادات حول متى يجب توقع اكتمال عمليات ترحيل علب البريد المجمعة أو عمليات الترحيل الفردية. تستند هذه التقديرات إلى تحليل بيانات ترحيلات العملاء السابقة. نظرا لأن كل بيئة فريدة، قد تختلف سرعة الترحيل الدقيقة.

تذكر أن هذه الميزة حاليا قيد المعاينة و SLA، وأي مستويات خدمة مطبقة لا تنطبق على أي مشاكل تتعلق بالأداء أو التوفر أثناء حالة المعاينة لهذه الميزة.

**حماية المستندات في المستأجر المصدر القابلة للاستهلاك من قبل المستخدمين في المستأجر الوجهة.**

ترحيل المستأجر عبر المستأجرين فقط لترحيل بيانات علبة البريد وليس أي شيء آخر. هناك العديد من الخيارات الأخرى، والتي تم توثيقها في منشور المدونة التالي التي قد تساعدك: <https://techcommunity.microsoft.com/t5/security-compliance-and-identity/mergers-and-spinoffs/ba-p/910455>

**هل يمكنني الحصول على التسميات نفسها في المستأجر الوجهة كما كان في المستأجر المصدر، إما كم مجموعة التسميات الوحيدة أو مجموعة إضافية من التسميات للمستخدمين الذين تم ترحيلهم استنادا إلى المحاذاة بين المؤسسات.**

نظرا لأن عمليات الترحيل عبر المستأجرين لا تقوم بتصدير التسميات ولا توجد أي طريقة لمشاركة التسميات بين المستأجرين، يمكنك تحقيق ذلك فقط عن طريق إعادة إنشاء التسميات في المستأجر الوجهة.

**هل تدعم نقل Microsoft 365 المجموعات؟**

لا تدعم حاليا ميزة ترحيل علب البريد عبر المستأجر ترحيل Microsoft 365 المجموعات.

**هل يمكن لمسؤول المستأجر المصدر إجراء بحث eDiscovery في علبة بريد بعد ترحيل علبة البريد إلى المستأجر الجديد/الهدف؟**

لا، بعد ترحيل علبة بريد المستأجر عبر المستأجر، لا يعمل eDiscovery مقابل علبة بريد المستخدم الذي تم ترحيله في المصدر. يعود سبب ذلك إلى عدم وجود علبة بريد في المصدر للبحث عنها حيث تم ترحيل علبة البريد إلى المستأجر الهدف وهي تنتمي الآن إلى المستأجر الهدف. eDiscovery، لا يمكن ترحيل علبة البريد بعد ذلك إلا في المستأجر الهدف (حيث توجد علبة البريد الآن). إذا كانت هناك حاجة إلى استمرار نسخة من علبة البريد المصدر في المستأجر المصدر بعد الترحيل، يمكن للمسؤول في المصدر نسخ المحتويات إلى علبة بريد بديلة قبل الترحيل لعمليات eDiscovery المستقبلية مقابل البيانات.

## <a name="known-issues"></a>المشاكل المعروفة

- **المشكلة: ستقتصر وظائف Teams الترحيل في المستأجر المصدر.** بعد ترحيل علبة البريد إلى المستأجر الهدف، Teams الوصول إلى علبة بريد المستخدم في المستأجر المصدر. وبالتالي، إذا سجل مستخدم الدخول إلى Teams باستخدام بيانات اعتماد المستأجر المصدر، سيفقد المستخدم وظائف مثل عدم القدرة على تحديث صورة ملف التعريف، وعدم وجود تطبيق تقويم، وعدم القدرة على البحث عن الفرق العامة والانضمام إليها.

- **المشكلة: لا يمكن ترحيل الأرشيفات الموسعة بشكل تلقائي.** تدعم ميزة الترحيل عبر المستأجرين ترحيل علبة البريد الأساسية علبة البريد الأساسية علبة بريد الأرشيف لمستخدم معين. إذا كان لدى المستخدم في المصدر أرشيفا موسع بشكل تلقائي ، مما يعني أكثر من علبة بريد أرشيف واحدة، فإن الميزة غير قادرة على ترحيل الأرشيفات الإضافية ويجب أن تفشل.

- **المشكلة: إن "مرسلو بريد السحابة" الذين لا يملكون وكيل smtpAddress يمنعون MRS من نقل الخلفية.** عند إنشاء كائنات MailUser للمستأجر الهدف، يجب التأكد من أن كل عناوين وكيل SMTP تنتمي إلى مؤسسة المستأجر الهدف. إذا كان وكيل SMTPAddress موجودا على مستخدم البريد الهدف الذي لا ينتمي إلى المستأجر المحلي، يتم منع تحويل "مرسل البريد" إلى علبة بريد. يعود سبب ذلك إلى ضماننا بأن كائنات علبة البريد يمكنها فقط إرسال البريد من المجالات التي يكون المستأجر موثوقا بها (المجالات التي يطالب بها المستأجر):

  - عند مزامنة المستخدمين من المحلي باستخدام Azure AD الاتصال، تقوم بتوفير كائنات MailUser المحلية مع ExternalEmailAddress التي تشير إلى المستأجر المصدر حيث توجد علبة البريد (LaraN@contoso.onmicrosoft.com) وستتم وضع طابع على PrimarySMTPAddress كمجال موجود في المستأجر الهدف (Lara.Newton@northwind.com). تتزامن هذه القيم مع المستأجر ويتم توفير مستخدم بريد مناسب وجاهز ل الترحيل. يتم عرض مثال لكائن هنا.

    ```powershell
    Get-MailUser LaraN | select ExternalEmailAddress, EmailAddresses

    ExternalEmailAddress               EmailAddresses
    --------------------               --------------
    SMTP:LaraN@contoso.onmicrosoft.com {SMTP:lara.newton@northwind.com}
    ```

   > [!NOTE]
   > عنوان *contoso.onmicrosoft.com* *غير موجود* في الصفيف EmailAddresses / proxyAddresses.

- **المشكلة: يتم تعديل كائنات MailUser مع عناوين SMTP الأساسية "الخارجية" / إعادة تعيينها إلى المجالات "الداخلية" التي تطالب بها الشركة**

  إن كائنات MailUser هي تشير إلى علب بريد غير محلية. في حالة ترحيل علب البريد عبر المستأجرين، نستخدم كائنات MailUser لتمثيل علبة البريد المصدر (من منظور المؤسسة المستهدفة) أو علبة البريد الهدف (من منظور المؤسسة المصدر). سيكون لدى MailUsers عنوان ExternalEmailAddress (targetAddress) يشير إلى عنوان smtp لعلبة البريد الفعلية (ProxyTest@fabrikam.onmicrosoft.com) وعنوان PRIMARYSMTP الذي يمثل عنوان SMTP المعروض لمستخدم علبة البريد في الدليل. تختار بعض المؤسسات عرض عنوان SMTP الأساسي كعنوان SMTP خارجي، وليس كعنوان يملكه/يتحقق منه المستأجر المحلي (مثل fabrikam.com بدلا من عنوان contoso.com).  ومع ذلك، بمجرد تطبيق Exchange خطة الخدمة على MailUser عبر عمليات الترخيص، يتم تعديل عنوان SMTP الأساسي ليظهر كمجال تم التحقق منه من قبل المؤسسة المحلية (contoso.com). هناك سببان محتملان:

  - عند تطبيق Exchange خدمة بريد إلكتروني على MailUser، تبدأ عملية Azure AD بفرض عملية ازدراج الوكيل لضمان عدم قدرة المؤسسة المحلية على إرسال البريد أو التهويل أو البريد من مستأجر آخر. سيتم إزالة أي عنوان SMTP على كائن مستلم مع خطط الخدمة هذه إذا لم يتم التحقق من العنوان من قبل المؤسسة المحلية. كما هو الحال في المثال، لا يتم Fabikam.com المجال من قبل contoso.onmicrosoft.com المستأجر، لذلك يزيل الازدجال fabrikam.com المجال. إذا كنت ترغب في الاستمرار في هذه المجالات الخارجية على MailUser، إما قبل الترحيل أو بعد الترحيل، ستحتاج إلى تعديل عمليات الترحيل لتجرد التراخيص بعد اكتمال عملية الترحيل أو قبل عملية الانتقال للتأكد من تطبيق العلامة التجارية الخارجية المتوقعة على المستخدمين. ستحتاج إلى التأكد من ترخيص كائن علبة البريد بشكل صحيح لكي لا يؤثر على خدمة البريد.
  - مثال برنامج نصي لإزالة خطط الخدمة على MailUser في contoso.onmicrosoft.com المستأجر هنا.

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

    لم يعد يتم مسح PrimarySMTPAddress للمستخدم. لا fabrikam.com المجال الخاص contoso.onmicrosoft.com المستأجر وسيستمر كعنوان SMTP الأساسي الموضح في الدليل.

    فيما يلي مثال على ذلك.

    ```powershell
    Get-Recipient ProxyTest | Format-Table -AutoSize UserPrincipalName, PrimarySmtpAddress, ExternalEmailAddress, ExternalDirectoryObjectId
    UserPrincipalName               PrimarySmtpAddress              ExternalEmailAddress                 ExternalDirectoryObjectId
    -----------------               ------------------              --------------------                 -------------------------
    ProxyTest@fabrikam.com          ProxyTest@fabrikam.com          SMTP:ProxyTest@fabrikam.com          e2513482-1d5b-4066-936a-cbc7f8f6f817
    ```

    - عند تعيين msExchRemoteRecipientType إلى 8 (DeprovisionMailbox)، بالنسبة لمرسلي البريد المحلي الذين يتم ترحيلهم إلى المستأجر الهدف، سيزيل منطق الازدخ الوكيل في Azure المجالات غير المملوكة ويعيد تعيين PRIMARYSMTP إلى مجال ممتلك. من خلال مسح msExchRemoteRecipientType في MailUser في الموقع، لن يتم تطبيق منطق فرك الوكيل بعد الآن.

      فيما يلي المجموعة الكاملة لخطط الخدمة الحالية التي تتضمن Exchange Online.

      | الاسم                                             |
      | ------------------------------------------------ |
      | Advanced eDiscovery التخزين (500 غيغابايت)              |
      | Customer Lockbox                                 |
      | منع فقدان البيانات                             |
      | Exchange Enterprise CAL Services (EOP، DLP)      |
      | Exchange أساسيات                              |
      | Exchange الأساس                              |
      | Exchange Online (P1)                             |
      | Exchange Online (خطة 1)                         |
      | Exchange Online (خطة 2)                         |
      | أرشفة Exchange Online لـ Exchange Online    |
      | أرشفة Exchange Online لـ Exchange Server    |
      | Exchange Online الإضافية "مستخدم غير نشط"             |
      | Exchange Online Kiosk                            |
      | Exchange Online Multi-Geo                        |
      | Exchange Online 1                           |
      | Exchange Online POP                              |
      | Exchange Online Protection                       |
      | حواجز المعلومات                             |
      | حماية المعلومات Office 365 - Premium  |
      | حماية المعلومات Office 365 - قياسي |
      | Insights بواسطة MyAnalytics                          |
      | Microsoft 365 التدقيق المتقدم                  |
      | Microsoft Bookings                               |
      | مركز أعمال Microsoft                        |
      | Microsoft MyAnalytics (كامل)                     |
      | eDiscovery المتقدم في Office 365                   |
      | Microsoft Defender Office 365 (الخطة 1)       |
      | Microsoft Defender Office 365 (الخطة 2)       |
      | Office 365 إدارة الوصول المتميزة          |
      | Premium التشفير في Office 365                 |
      |                                                  |
