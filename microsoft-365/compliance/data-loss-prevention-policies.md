---
title: مرجع منع فقدان البيانات
f1.keywords:
- CSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: ''
audience: ITPro
ms.topic: conceptual
f1_keywords:
- ms.o365.cc.DLPLandingPage
ms.service: O365-seccomp
ms.localizationpriority: ''
ms.collection:
- M365-security-compliance
- SPO_Content
- m365solution-mip
- m365initiative-compliance
search.appverid:
- MET150
ms.custom:
- seo-marvel-apr2020
- admindeeplinkEXCHANGE
ROBOTS: NOINDEX, NOFOLLOW
feedback_system: None
description: مادة مرجعية لمنع فقدان البيانات
ms.openlocfilehash: b7546d41310942a0e6eab99511a78c594822ee2a
ms.sourcegitcommit: 133bf9097785309da45df6f374a712a48b33f8e9
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 06/10/2022
ms.locfileid: "66017275"
---
# <a name="data-loss-prevention-reference"></a>مرجع منع فقدان البيانات

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

> [!IMPORTANT]
> هذا هو الموضوع المرجعي لم يعد المورد الرئيسي لمعلومات منع فقدان البيانات (DLP) من Microsoft Purview. يتم تحديث مجموعة محتوى DLP وإعادة هيكلتها. ستنتقل المواضيع التي تتناولها هذه المقالة إلى مقالات جديدة ومحدثة. لمزيد من المعلومات حول DLP، راجع [التعرف على منع فقدان البيانات](dlp-learn-about-dlp.md).

<!-- this topic needs to be split into smaller, more coherent ones. It is confusing as it is. -->
<!-- move this note to a more appropriate place, no topic should start with a note -->
> [!NOTE]
> تمت مؤخرا إضافة قدرات منع فقدان البيانات إلى Microsoft Teams رسائل الدردشة والقنوات للمستخدمين المرخصين خدمات الامتثال المتطورة في Office 365، والتي تتوفر كخيار مستقل ويتم تضمينها في Office 365 E5 التوافق في Microsoft 365 E5. لمعرفة المزيد حول متطلبات الترخيص، راجع [Microsoft 365 Tenant-Level إرشادات ترخيص الخدمات](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance).



<!-- MOVED TO LEARN ABOUT To comply with business standards and industry regulations, organizations must protect sensitive information and prevent its inadvertent disclosure. Sensitive information can include financial data or personally identifiable information (PII) such as credit card numbers, social security numbers, or health records. With a data loss prevention (DLP) policy in the Microsoft Purview compliance portal, you can identify, monitor, and automatically protect sensitive information across Office 365.

With a DLP policy, you can:

- **Identify sensitive information across many locations, such as Exchange Online, SharePoint Online, OneDrive for Business, and Microsoft Teams.**

    For example, you can identify any document containing a credit card number that's stored in any OneDrive for Business site, or you can monitor just the OneDrive sites of specific people.

- **Prevent the accidental sharing of sensitive information**.

    For example, you can identify any document or email containing a health record that's shared with people outside your organization, and then automatically block access to that document or block the email from being sent.

- **Monitor and protect sensitive information in the desktop versions of Excel, PowerPoint, and Word.**

    Just like in Exchange Online, SharePoint Online, and OneDrive for Business, these Office desktop programs include the same capabilities to identify sensitive information and apply DLP policies. DLP provides continuous monitoring when people share content in these Office programs.

- **Help users learn how to stay compliant without interrupting their workflow.**

    You can educate your users about DLP policies and help them remain compliant without blocking their work. For example, if a user tries to share a document containing sensitive information, a DLP policy can both send them an email notification and show them a policy tip in the context of the document library that allows them to override the policy if they have a business justification. The same policy tips also appear in Outlook on the web, Outlook, Excel, PowerPoint, and Word.

- **View DLP alerts and reports showing content that matches your organization’s DLP policies.**

    To view alerts and metadata related to your DLP policies you can use the [DLP Alerts Management Dashboard](dlp-configure-view-alerts-policies.md). You can also view policy match reports to assess how your organization is complying with a DLP policy. If a DLP policy allows users to override a policy tip and report a false positive, you can also view what users have reported

-->
## <a name="create-and-manage-dlp-policies"></a>إنشاء نهج DLP وإدارتها

يمكنك إنشاء نهج DLP وإدارتها على صفحة منع فقدان البيانات في مدخل توافق Microsoft Purview.

![صفحة منع فقدان البيانات في مدخل توافق Microsoft Purview](../media/943fd01c-d7aa-43a9-846d-0561321a405e.png)

<!-- MOVED TO LEARN ABOUT ## What a DLP policy contains

A DLP policy contains a few basic things:

- Where to protect the content: **locations** such as Exchange Online, SharePoint Online, and OneDrive for Business sites, as well as Microsoft Teams chat and channel messages.

- When and how to protect the content by enforcing **rules** comprised of:

  - **Conditions** the content must match before the rule is enforced. For example, a rule might be configured to look only for content containing Social Security numbers that's been shared with people outside your organization.

  - **Actions** that you want the rule to take automatically when content matching the conditions is found. For example, a rule might be configured to block access to a document and send both the user and compliance officer an email notification.

You can use a rule to meet a specific protection requirement, and then use a DLP policy to group together common protection requirements, such as all of the rules needed to comply with a specific regulation.

For example, you might have a DLP policy that helps you detect the presence of information subject to the Health Insurance Portability and Accountability Act (HIPAA). This DLP policy could help protect HIPAA data (the what) across all SharePoint Online sites and all OneDrive for Business sites (the where) by finding any document containing this sensitive information that's shared with people outside your organization (the conditions) and then blocking access to the document and sending a notification (the actions). These requirements are stored as individual rules and grouped together as a DLP policy to simplify management and reporting.

![Diagram shows that DLP policy contains locations and rules.](../media/c006860c-2d00-42cb-aaa4-5b5638d139f7.png) -->

<!-- MOVED TO LEARN ABOUT ### Locations

DLP policies are applied to sensitive items across Microsoft 365 locations and can be further scoped as detailed in this table.


|Location | Include/exclude by|
|---------|---------|
|Exchange email| distribution groups|
|SharePoint sites |sites |
|OneDrive accounts |accounts |
|Teams chat and channel messages |accounts |
|Windows 10 devices |user or group |
|Microsoft Cloud App Security |instance |
 -->

<!-- moved to dlp-policy-reference.md
If you choose to include specific distribution groups in Exchange, the DLP policy will be scoped only to the members of that group. Similarly excluding a distribution group will exclude all the members of that distribution group from policy evaluation. You can choose to scope a policy to the members of distribution lists, dynamic distribution groups, and security groups. A DLP policy can contain no more than 50 such inclusions and exclusions.

If you choose to include or exclude specific SharePoint sites, a DLP policy can contain no more than 100 such inclusions and exclusions. Although this limit exists, you can exceed this limit by applying either an org-wide policy or a policy that applies to entire locations.

If you choose to include or exclude specific OneDrive accounts or groups, a DLP policy can contain no more than 100 user accounts or 50 groups as inclusion or exclusion.

### Rules

> [!NOTE]
> The default behavior of a DLP policy, when there is no alert configured, is not to alert or trigger. This applies only to default information types. For custom information types, the system will alert even if there is no action defined in the policy.

Rules are what enforce your business requirements on your organization's content. A policy contains one or more rules, and each rule consists of conditions and actions. For each rule, when the conditions are met, the actions are taken automatically. Rules are executed sequentially, starting with the highest-priority rule in each policy.

A rule also provides options to notify users (with policy tips and email notifications) and admins (with email incident reports) that content has matched the rule.

Here are the components of a rule, each explained below.

![Sections of the DLP rule editor.](../media/1859d504-b9c2-45ed-961b-a0092251acc2.png)

#### Conditions

Conditions are important because they determine what types of information you're looking for, and when to take an action. For example, you might choose to ignore content containing passport numbers unless the content contains more than 10 such numbers and is shared with people outside your organization.

Conditions focus on the **content**, such as what types of sensitive information you're looking for, and also on the **context**, such as who the document is shared with. You can use conditions to assign different actions to different risk levels. For example, sensitive content shared internally might be lower risk and require fewer actions than sensitive content shared with people outside the organization.

![List showing available DLP conditions.](../media/0fa43f90-d007-4506-ae93-43e8424fe103.png)

The conditions now available can determine if:

- Content contains a type of sensitive information.

- Content contains a label. For more information, see the below section [Using a retention label as a condition in a DLP policy](#using-a-retention-label-as-a-condition-in-a-dlp-policy).

- Content is shared with people outside or inside your organization.

  > [!NOTE]
  > Users who have non-guest accounts in a host organization's Active Directory or Azure Active Directory tenant are considered as people inside the organization.

#### Types of sensitive information

A DLP policy can help protect sensitive information, which is defined as a **sensitive information type**. Microsoft 365 includes definitions for many common sensitive information types across many different regions that are ready for you to use, such as a credit card number, bank account numbers, national ID numbers, and passport numbers.

![List of available sensitive information types.](../media/3eaa9911-bc94-44be-902f-363dbf3b07fe.png)

When a DLP policy looks for a sensitive information type such as a credit card number, it doesn't simply look for a 16-digit number. Each sensitive information type is defined and detected by using a combination of:

- Keywords.

- Internal functions to validate checksums or composition.

- Evaluation of regular expressions to find pattern matches.

- Other content examination.

This helps DLP detection achieve a high degree of accuracy while reducing the number of false positives that can interrupt peoples' work.

#### Actions

When content matches a condition in a rule, you can apply actions to automatically protect the content.

![List of available DLP actions.](../media/8aef17fc-1e99-4ac7-adfc-0f2c9c1a0697.png)

With the actions now available, you can:

- **Restrict access to the content** Depending on your need, you can restrict access to content in three ways:

  1. Restrict access to content for everyone.
  2. Restrict access to content for people outside the organization.
  3. Restrict access to "Anyone with the link."

  For site content, this means that permissions for the document are restricted for everyone except the primary site collection administrator, document owner, and person who last modified the document. These people can remove the sensitive information from the document or take other remedial action. When the document is in compliance, the original permissions are automatically restored. When access to a document is blocked, the document appears with a special policy tip icon in the library on the site.

  ![Policy tip showing access to document is blocked.](../media/b6cefed3-d212-43d7-8534-4b92b26ebd50.png)

  For email content, this action blocks the message from being sent. Depending on how the DLP rule is configured, the sender sees an NDR or (if the rule uses a notification) a policy tip and/or email notification.

  ![Warning that unauthorized recipients must be removed from the message.](../media/302f9994-912d-41e7-861f-8a4539b3c285.png)

#### User notifications and user overrides

You can use notifications and overrides to educate your users about DLP policies and help them remain compliant without blocking their work. For example, if a user tries to share a document containing sensitive information, a DLP policy can both send them an email notification and show them a policy tip in the context of the document library that allows them to override the policy if they have a business justification.

![User notifications and user overrides sections of DLP rule editor.](../media/37b560d4-6e4e-489e-9134-d4b9daf60296.png)

The email can notify the person who sent, shared, or last modified the content and, for site content, the primary site collection administrator and document owner. In addition, you can add or remove whomever you choose from the email notification.

In addition to sending an email notification, a user notification displays a policy tip:

- In Outlook and Outlook on the web.

- For the document on a SharePoint Online or OneDrive for Business site.

- In Excel, PowerPoint, and Word, when the document is stored on a site included in a DLP policy.

The email notification and policy tip explain why content conflicts with a DLP policy. If you choose, the email notification and policy tip can allow users to override a rule by reporting a false positive or providing a business justification. This can help you educate users about your DLP policies and enforce them without preventing people from doing their work. Information about overrides and false positives is also logged for reporting (see below about the DLP reports) and included in the incident reports (next section), so that the compliance officer can regularly review this information.

Here's what a policy tip looks like in a OneDrive for Business account.

![Policy tip for a document in a OneDrive account.](../media/f9834d35-94f0-4511-8555-0fe69855ce6d.png)

 To learn more about user notifications and policy tips in DLP policies, see [Use notifications and policy tips](use-notifications-and-policy-tips.md).

#### Alerts and Incident reports

When a rule is matched, you can send an alert email to your compliance officer (or any person(s) you choose) with details of the alert. This alert email will carry a link of the [DLP Alerts Management Dashboard](dlp-configure-view-alerts-policies.md) which the compliance officer can go to view the details of alert and events. The dashboard contains details of the event that triggered the alert along with details of the DLP policy matched and the sensitive content detected.

In addition, you can also send an incident report with details of the event. This report includes information about the item that was matched, the actual content that matched the rule, and the name of the person who last modified the content. For email messages, the report also includes as an attachment the original message that matches a DLP policy.

> [!div class="mx-imgBorder"]
> ![Page for configuring incident reports.](../media/Alerts-and-incident-report.png)

DLP scans email differently from items in SharePoint Online or OneDrive for Business. In SharePoint Online and OneDrive for Business, DLP scans existing items as well as new ones and generates an alert and incident report whenever a match is found. In Exchange Online, DLP only scans new email messages and generates a report if there is a policy match. DLP ***does not*** scan or match previously existing email items that are stored in a mailbox or archive.

## Grouping and logical operators

Often your DLP policy has a straightforward requirement, such as to identify all content that contains a U.S. Social Security Number. However, in other scenarios, your DLP policy might need to identify more loosely defined data.

For example, to identify content subject to the U.S. Health Insurance Act (HIPAA), you need to look for:

- Content that contains specific types of sensitive information, such as a U.S. Social Security Number or Drug Enforcement Agency (DEA) Number.

    AND

- Content that's more difficult to identify, such as communications about a patient's care or descriptions of medical services provided. Identifying this content requires matching keywords from very large keyword lists, such as the International Classification of Diseases (ICD-9-CM or ICD-10-CM).

You can easily identify such loosely defined data by using grouping and logical operators (AND, OR). When you create a DLP policy, you can:

- Group sensitive information types.

- Choose the logical operator between the sensitive information types within a group and between the groups themselves.

### Choosing the operator within a group

Within a group, you can choose whether any or all of the conditions in that group must be satisfied for the content to match the rule.

![Group showing the operators within the group.](../media/6a12f1e8-112d-48ee-9a73-82b3dd0542e7.png)

### Adding a group

You can quickly add a group, which can have its own conditions and operator within that group.

![Add group button.](../media/5f72f292-d1f3-4f11-a911-a9f71e10abf6.png)

### Choosing the operator between groups

Between groups, you can choose whether the conditions in just one group or all of the groups must be satisfied for the content to match the rule.

For example, the built-in **U.S. HIPAA** policy has a rule that uses an **AND** operator between the groups so that it identifies content that contains:

- from the group **PII Identifiers** (at least one SSN number **OR** DEA number)

    **AND**

- from the group **Medical Terms** (at least one ICD-9-CM keyword **OR** ICD-10-CM keyword)

![Groups showing the operator between groups.](../media/354aa77f-569c-4847-9dfe-605ee2bb28d1.png)

## The priority by which rules are processed

When you create rules in a policy, each rule is assigned a priority in the order in which it's created — meaning, the rule created first has first priority, the rule created second has second priority, and so on.

> [!div class="mx-imgBorder"]
> ![Rules in priority order.](../media/dlp-rules-in-priority-order.png)

After you have set up more than one DLP policy, you can change the priority of one or more policies. To do that, select a policy, choose **Edit policy**, and use the **Priority** list to specify its priority.

> [!div class="mx-imgBorder"]
> ![Set priority for a policy.](../media/dlp-set-policy-priority.png)

When content is evaluated against rules, the rules are processed in priority order. If content matches multiple rules, the rules are processed in priority order and the most restrictive action is enforced. For example, if content matches all of the following rules, Rule 3 is enforced because it's the highest priority, most restrictive rule:

- Rule 1: only notifies users

- Rule 2: notifies users, restricts access, and allows user overrides

- Rule 3: notifies users, restricts access, and does not allow user overrides

- Rule 4: only notifies users

- Rule 5: restricts access

- Rule 6: notifies users, restricts access, and does not allow user overrides

In this example, note that matches for all of the rules are recorded in the audit logs and shown in the DLP reports, even though only the most restrictive rule is enforced.

Regarding policy tips, note that:

- Only the policy tip from the highest priority, most restrictive rule will be shown. For example, a policy tip from a rule that blocks access to content will be shown over a policy tip from a rule that simply sends a notification. This prevents people from seeing a cascade of policy tips.

- If the policy tips in the most restrictive rule allow people to override the rule, then overriding this rule also overrides any other rules that the content matched.

-->

## <a name="tuning-rules-to-make-them-easier-or-harder-to-match"></a>ضبط القواعد لتسهيل مطابقتها أو صعوبة مطابقتها

بعد أن يقوم الأشخاص بإنشاء نهج DLP وتشغيلها، فإنهم أحيانا ما يعانون من هذه المشكلات:

- يتطابق المحتوى الزائد **عن الحد الذي لا يمثل** معلومات حساسة مع القواعد ، بمعنى آخر، الكثير من الإيجابيات الخاطئة.

- يتطابق المحتوى القليل جدا الذي **يحتوي** على معلومات حساسة مع القواعد. بمعنى آخر، لا يتم فرض إجراءات الحماية على المعلومات الحساسة.

لمعالجة هذه المشاكل، يمكنك ضبط القواعد الخاصة بك عن طريق ضبط عدد المثيلات ومطابقة الدقة لجعل من الصعب أو الأسهل على المحتوى مطابقة القواعد. يحتوي كل نوع من أنواع المعلومات الحساسة المستخدمة في قاعدة على عدد مثيلات ودقة مطابقة.

### <a name="instance-count"></a>عدد المثيلات

يعني عدد المثيلات ببساطة عدد مرات حدوث نوع معين من المعلومات الحساسة التي يجب أن تكون موجودة لكي يتطابق المحتوى مع القاعدة. على سبيل المثال، يطابق المحتوى القاعدة الموضحة أدناه إذا كانت بين 1 و 9 قواعد أمريكية فريدة أو المملكة المتحدة. يتم تحديد أرقام جواز السفر.

> [!NOTE]
> يتضمن عدد المثيلات تطابقات **فريدة** فقط لأنواع المعلومات الحساسة والكلمات الأساسية. على سبيل المثال، إذا احتوت رسالة بريد إلكتروني على 10 تكرارات لرقم بطاقة الائتمان نفسه، فإن عدد مرات الحدوث العشرة هذه هو مثيل واحد لرقم بطاقة الائتمان.

لاستخدام عدد المثيلات لضبط القواعد، تكون الإرشادات مباشرة:

- لتسهيل مطابقة القاعدة، إنقاص عدد **الدقوم** و/أو زيادة **العدد الأقصى** . يمكنك أيضا تعيين **الحد الأقصى** **لأي قيمة** عن طريق حذف القيمة الرقمية.

- لجعل القاعدة أكثر صعوبة في المطابقة، قم بزيادة عدد **الدق.**

عادة، يمكنك استخدام إجراءات أقل تقييدا، مثل إرسال إعلامات المستخدم، في قاعدة ذات عدد المثيلات الأقل (على سبيل المثال، 1-9). ويمكنك استخدام إجراءات أكثر تقييدا، مثل تقييد الوصول إلى المحتوى دون السماح بتجاوزات المستخدم، في قاعدة ذات عدد مثيلات أعلى (على سبيل المثال، 10-أي).

![عدد المثيلات في محرر القاعدة.](../media/e7ea3c12-72c5-4bb3-9590-c924c665e84d.png)

### <a name="match-accuracy"></a>مطابقة الدقة

كما هو موضح أعلاه، يتم تعريف نوع معلومات حساسة واكتشافه باستخدام مجموعة من أنواع مختلفة من الأدلة. عادة ما يتم تعريف نوع المعلومات الحساسة بواسطة مجموعات متعددة من هذه المجموعات، تسمى الأنماط. النمط الذي يتطلب أدلة أقل له دقة مطابقة أقل (أو مستوى الثقة)، بينما النمط الذي يتطلب المزيد من الأدلة له دقة مطابقة أعلى (أو مستوى الثقة). لمعرفة المزيد حول الأنماط الفعلية ومستويات الثقة المستخدمة من قبل كل نوع من أنواع المعلومات [الحساسة، راجع تعريفات كيان نوع المعلومات الحساسة](sensitive-information-type-entity-definitions.md).

على سبيل المثال، يتم تعريف نوع المعلومات الحساسة المسمى "رقم بطاقة الائتمان" بواسطة نمطين:

- نمط بثقة بنسبة 65٪ يتطلب:

  - رقم بتنسيق رقم بطاقة ائتمان.

  - رقم يمرر المجموع الاختباري.

- نمط بثقة بنسبة 85٪ يتطلب ما يلي:

  - رقم بتنسيق رقم بطاقة ائتمان.

  - رقم يمرر المجموع الاختباري.

  - كلمة أساسية أو تاريخ انتهاء الصلاحية بالتنسيق الصحيح.

يمكنك استخدام مستويات الثقة هذه (أو مطابقة الدقة) في القواعد. عادة ما تستخدم إجراءات أقل تقييدا، مثل إرسال إعلامات المستخدم، في قاعدة ذات دقة مطابقة أقل. ويمكنك استخدام إجراءات أكثر تقييدا، مثل تقييد الوصول إلى المحتوى دون السماح بتجاوز المستخدم، في قاعدة ذات دقة تطابق أعلى.

من المهم أن نفهم أنه عند تحديد نوع معين من المعلومات الحساسة، مثل رقم بطاقة الائتمان، في المحتوى، يتم إرجاع مستوى ثقة واحد فقط:

- إذا كانت جميع التطابقات لنمط واحد، يتم إرجاع مستوى الثقة لهذا النمط.

- إذا كانت هناك تطابقات لأكثر من نمط واحد (أي، هناك تطابقات مع مستويي ثقة مختلفين)، يتم إرجاع مستوى ثقة أعلى من أي من الأنماط الفردية فقط. هذا هو الجزء الصعب. على سبيل المثال، بالنسبة لبطاقة الائتمان، إذا تطابق النمطان 65٪ و85٪، يكون مستوى الثقة الذي يتم إرجاعه لنوع المعلومات الحساسة هذا أكبر من 90٪ لأن المزيد من الأدلة يعني المزيد من الثقة.

لذلك إذا كنت ترغب في إنشاء قاعدتين حصريتين بشكل متبادل للبطاقات الائتمانية، واحدة لدقة المطابقة بنسبة 65٪ والأخرى لدقة المطابقة بنسبة 85٪، فإن نطاقات دقة المطابقة ستبدو كما يلي. تلتقط القاعدة الأولى تطابقات النمط 65٪ فقط. تلتقط القاعدة الثانية التطابقات مع تطابق **واحد على الأقل** بنسبة 85٪ **ويمكن أن يكون لها** تطابقات أخرى أقل ثقة.

![قاعدتان مع نطاقات مختلفة لدقة المطابقة.](../media/21bdfe36-7a91-4347-8098-11809a92f9a4.png)

لهذه الأسباب، فإن إرشادات إنشاء قواعد ذات دقة مطابقة مختلفة هي:

- عادة ما يستخدم أدنى مستوى ثقة نفس القيمة **للأدنى** والحد **الأقصى** (وليس للنطاق).

- عادة ما يكون مستوى الثقة الأعلى نطاقا من أعلى مستوى الثقة الأدنى إلى 100.

- تتراوح أي مستويات ثقة بين مستويات الثقة عادة من أعلى مستوى الثقة الأدنى إلى أقل بقليل من مستوى الثقة الأعلى.

## <a name="using-a-retention-label-as-a-condition-in-a-dlp-policy"></a>استخدام تسمية استبقاء كشرط في نهج DLP

عند استخدام [تسمية استبقاء](retention.md#retention-labels) تم إنشاؤها ونشرها مسبقا كشرط في نهج DLP، هناك بعض الأشياء التي يجب أن تكون على علم بها:

- يجب إنشاء تسمية الاستبقاء ونشرها قبل محاولة استخدامها كشرط في نهج DLP.
- قد تستغرق مزامنة تسميات الاستبقاء المنشورة من يوم إلى سبعة أيام. لمزيد من المعلومات، راجع [متى تصبح تسميات الاستبقاء متوفرة للتطبيق على](create-apply-retention-labels.md#when-retention-labels-become-available-to-apply) تسميات الاستبقاء المنشورة في نهج الاستبقاء، [والمدة التي تستغرقها تسميات الاستبقاء لكي تصبح سارية المفعول](apply-retention-labels-automatically.md#how-long-it-takes-for-retention-labels-to-take-effect) لتسميات الاستبقاء المنشورة تلقائيا.
- استخدام تسمية استبقاء في نهج **معتمد فقط للعناصر الموجودة في SharePoint و OneDrive***.

  ![التسميات كشرط.](../media/5b1752b4-a129-4a88-b010-8dcf8a38bb09.png)

  قد ترغب في استخدام تسمية استبقاء في نهج DLP إذا كان لديك عناصر تحت الاستبقاء والتصرف، وتريد أيضا تطبيق عناصر تحكم أخرى عليها، على سبيل المثال:

  - لقد نشرت تسمية استبقاء باسم **السنة الضريبية 2018**، والتي عند تطبيقها على المستندات الضريبية من عام 2018 والمخزنة في SharePoint تحتفظ بها لمدة 10 سنوات ثم تتخلص منها. كما أنك لا تريد مشاركة هذه العناصر خارج مؤسستك، وهو ما يمكنك القيام به باستخدام نهج DLP.

  > [!IMPORTANT]
  > ستحصل على هذا الخطأ إذا حددت تسمية استبقاء كشرط في نهج DLP وقمت أيضا بتضمين Exchange و/أو Teams كموقع: **"حماية المحتوى المسمى في البريد الإلكتروني ورسائل الفرق غير معتمدة. إما إزالة التسمية أدناه أو إيقاف تشغيل Exchange Teams كموقع."** وذلك لأن Exchange النقل لا يقيم بيانات تعريف التسمية أثناء إرسال الرسالة وتسليمها.

### <a name="using-a-sensitivity-label-as-a-condition-in-a-dlp-policy"></a>استخدام وصف الحساسية كشرط في نهج DLP

[تعرف على المزيد](./dlp-sensitivity-label-as-condition.md) حول استخدام وصف الحساسية كشرط في نهج DLP.

### <a name="how-this-feature-relates-to-other-features"></a>كيفية ارتباط هذه الميزة بميزات أخرى

يمكن تطبيق العديد من الميزات على المحتوى الذي يحتوي على معلومات حساسة:

- يمكن [لتسمية الاستبقاء ونهج الاستبقاء](retention.md) فرض إجراءات **الاستبقاء** على هذا المحتوى.

- يمكن لنهج DLP فرض إجراءات **الحماية** على هذا المحتوى. وقبل فرض هذه الإجراءات، يمكن أن يتطلب نهج DLP استيفاء شروط أخرى بالإضافة إلى المحتوى الذي يحتوي على تسمية.

![رسم تخطيطي للميزات التي يمكن تطبيقها على المعلومات الحساسة.](../media/dd410f97-a3a3-455c-a1e9-7ed8ae6893d6.png)

لاحظ أن نهج DLP لديه قدرة اكتشاف أكثر ثراء من التسمية أو نهج الاستبقاء المطبقة على المعلومات الحساسة. يمكن لنهج منع فقدان البيانات فرض إجراءات حماية على المحتوى الذي يحتوي على معلومات حساسة، وإذا تمت إزالة المعلومات الحساسة من المحتوى، يتم التراجع عن إجراءات الحماية هذه في المرة التالية التي يتم فيها مسح المحتوى ضوئيا. ولكن إذا تم تطبيق نهج استبقاء أو تسمية على محتوى يحتوي على معلومات حساسة، فهذا إجراء لمرة واحدة لن يتم التراجع عنه حتى إذا تمت إزالة المعلومات الحساسة.

باستخدام تسمية كشرط في نهج DLP، يمكنك فرض كل من إجراءات الاستبقاء والحماية على المحتوى باستخدام هذه التسمية. يمكنك التفكير في محتوى يحتوي على تسمية تماما مثل المحتوى الذي يحتوي على معلومات حساسة - كل من التسمية ونوع المعلومات الحساسة هما من الخصائص المستخدمة لتصنيف المحتوى، بحيث يمكنك فرض إجراءات على هذا المحتوى.

![رسم تخطيطي لنهج DLP باستخدام التسمية كشرط.](../media/4538fd8f-fb74-4743-bc22-a5de33adfebb.png)

## <a name="simple-settings-vs-advanced-settings"></a>الإعدادات البسيطة مقابل الإعدادات المتقدمة

عند إنشاء نهج DLP، ستختار بين الإعدادات البسيطة أو المتقدمة:

- تسهل **الإعدادات البسيطة** إنشاء النوع الأكثر شيوعا من نهج DLP دون استخدام محرر القواعد لإنشاء القواعد أو تعديلها.

- تستخدم **الإعدادات المتقدمة** محرر القاعدة لمنحك التحكم الكامل في كل إعداد لنهج DLP.

لا تقلق، ضمن التغطية، تعمل الإعدادات البسيطة والإعدادات المتقدمة بنفس الطريقة تماما، من خلال فرض قواعد تتكون من الشروط والإجراءات - فقط مع الإعدادات البسيطة، لا ترى محرر القواعد. إنها طريقة سريعة لإنشاء نهج DLP.

### <a name="simple-settings"></a>إعدادات بسيطة

حتى الآن، فإن سيناريو DLP الأكثر شيوعا هو إنشاء نهج للمساعدة في حماية المحتوى الذي يحتوي على معلومات حساسة من المشاركة مع أشخاص من خارج مؤسستك، واتخاذ إجراء معالجة تلقائية مثل تقييد من يمكنه الوصول إلى المحتوى، وإرسال إعلامات المستخدم النهائي أو المسؤول، وتدقيق الحدث للتحقيق لاحقا. يستخدم الأشخاص DLP للمساعدة في منع الكشف غير المقصود عن المعلومات الحساسة.

لتبسيط تحقيق هذا الهدف، عند إنشاء نهج DLP، يمكنك اختيار **استخدام الإعدادات البسيطة**. توفر هذه الإعدادات كل ما تحتاجه لتنفيذ نهج DLP الأكثر شيوعا، دون الحاجة إلى الانتقال إلى محرر القاعدة.

![خيارات DLP للإعدادات البسيطة والمتقدمة.](../media/33c93824-ead5-43b6-9c3e-fd1630c92a7d.png)

### <a name="advanced-settings"></a>الإعدادات المتقدمة

إذا كنت بحاجة إلى إنشاء نهج DLP أكثر تخصيصا، يمكنك اختيار **استخدام الإعدادات المتقدمة**.

تقدم لك الإعدادات المتقدمة محرر القاعدة، حيث يمكنك التحكم الكامل في كل خيار ممكن، بما في ذلك عدد المثيلات ودقة المطابقة (مستوى الثقة) لكل قاعدة.

للانتقال بسرعة إلى مقطع، انقر فوق عنصر في التنقل العلوي لمحرر القاعدة للانتقال إلى هذا المقطع أدناه.

![قائمة التنقل العلوية لمحرر قاعدة DLP.](../media/c527b97f-ca53-4c79-ad19-1a63be8a8ecc.png)

## <a name="dlp-policy-templates"></a>قوالب نهج DLP

الخطوة الأولى في إنشاء نهج DLP هي اختيار المعلومات التي يجب حمايتها. من خلال البدء بقالب DLP، يمكنك حفظ عمل إنشاء مجموعة جديدة من القواعد من البداية، ومعرفة أنواع المعلومات التي يجب تضمينها بشكل افتراضي. يمكنك بعد ذلك إضافة هذه المتطلبات أو تعديلها لضبط القاعدة لتلبية المتطلبات المحددة لمؤسستك.

يمكن أن يساعدك قالب نهج DLP الذي تم تكوينه مسبقا على اكتشاف أنواع معينة من المعلومات الحساسة، مثل بيانات HIPAA أو بيانات PCI-DSS أو بيانات قانون Gramm-Leach-Bliley أو حتى معلومات تعريف شخصية خاصة بالإعدادات المحلية (P.I.). لتسهيل العثور على الأنواع الشائعة من المعلومات الحساسة وحمايتها، تحتوي قوالب النهج المضمنة في Microsoft 365 بالفعل على أنواع المعلومات الحساسة الأكثر شيوعا اللازمة لبدء الاستخدام.

![قائمة بقوالب نهج منع فقدان البيانات مع التركيز على قالب قانون الحماية من فقدان البيانات في الولايات المتحدة.](../media/791b2403-430b-4987-8643-cc20abbd8148.png)

قد يكون لدى مؤسستك أيضا متطلباتها الخاصة، وفي هذه الحالة يمكنك إنشاء نهج DLP من البداية عن طريق اختيار خيار **النهج المخصص** . النهج المخصص فارغ ولا يحتوي على قواعد مسبقة الصنع.

<!-- ## Roll out DLP policies gradually with test mode

rehomed to Plan for DLP

When you create your DLP policies, you should consider rolling them out gradually to assess their impact and test their effectiveness before fully enforcing them. For example, you don't want a new DLP policy to unintentionally block access to thousands of documents that people require access to in order to get their work done.

If you're creating DLP policies with a large potential impact, we recommend following this sequence:

1. **Start in test mode without Policy Tips** and then use the DLP reports and any incident reports to assess the impact. You can use DLP reports to view the number, location, type, and severity of policy matches. Based on the results, you can fine tune the rules as needed. In test mode, DLP policies will not impact the productivity of people working in your organization.

2. **Move to Test mode with notifications and Policy Tips** so that you can begin to teach users about your compliance policies and prepare them for the rules that are going to be applied. At this stage, you can also ask users to report false positives so that you can further refine the rules.

3. **Start full enforcement on the policies** so that the actions in the rules are applied and the content's protected. Continue to monitor the DLP reports and any incident reports or notifications to make sure that the results are what you intend.

    ![Options for using test mode and turning on policy.](../media/49fafaac-c6cb-41de-99c4-c43c3e380c3a.png)

    You can turn off a DLP policy at any time, which affects all rules in the policy. However, each rule can also be turned off individually by toggling its status in the rule editor.

    ![Options for turning off a rule in a policy.](../media/f7b258ff-1b8b-4127-b580-83c6492f2bef.png)

    You can also change the priority of multiple rules in a policy. To do that, open a policy for editing. In a row for a rule, choose the ellipses (**...**), and then choose an option, such as **Move down** or **Bring to last**.

    > [!div class="mx-imgBorder"]
    > ![Set rule priority.](../media/dlp-set-rule-priority.png)-->

## <a name="dlp-reports"></a>تقارير DLP

بعد إنشاء نهج DLP وتشغيلها، ستحتاج إلى التحقق من أنها تعمل كما تريد وتساعدك على البقاء متوافقا. باستخدام تقارير DLP، يمكنك عرض عدد نهج DLP وتطابقات القواعد بسرعة مع مرور الوقت، وعدد الإيجابيات الزائفة والتجاوزات. لكل تقرير، يمكنك تصفية تلك التطابقات حسب الموقع أو الإطار الزمني، وحتى تضييقه إلى نهج أو قاعدة أو إجراء معين.

باستخدام تقارير DLP، يمكنك الحصول على رؤى الأعمال وما يلي:

- ركز على فترات زمنية محددة وفهم أسباب الارتفاعات والاتجاهات.

- اكتشف العمليات التجارية التي تنتهك نهج الامتثال لمؤسستك.

- فهم أي تأثير تجاري لنهج DLP.

بالإضافة إلى ذلك، يمكنك استخدام تقارير DLP لضبط نهج DLP أثناء تشغيلها.

![لوحة معلومات التقارير في مركز الأمان والتوافق.](../media/6d741252-a0ce-4429-95ba-6c857ecc9a7e.png)

## <a name="how-dlp-policies-work"></a>كيفية عمل نهج DLP

يكشف DLP عن المعلومات الحساسة باستخدام تحليل المحتوى العميق (وليس فقط فحص النص البسيط). يستخدم تحليل المحتوى العميق هذا تطابقات الكلمات الأساسية وتطابقات القاموس وتقييم التعبيرات العادية والوظائف الداخلية والأساليب الأخرى للكشف عن المحتوى الذي يتطابق مع نهج DLP. من المحتمل أن تكون نسبة صغيرة فقط من بياناتك حساسة. يمكن لنهج DLP تحديد ومراقبة وحماية تلك البيانات فقط تلقائيا، دون مساس أو التأثير على الأشخاص الذين يعملون مع بقية المحتوى الخاص بك.

### <a name="policies-are-synced"></a>تتم مزامنة النهج

بعد إنشاء نهج DLP في مدخل توافق Microsoft Purview، يتم تخزينه في مخزن نهج مركزي، ثم تتم مزامنته مع مصادر المحتوى المختلفة، بما في ذلك:

- Exchange Online، ومن هناك إلى Outlook على ويب Outlook.

- مواقع OneDrive for Business.

- SharePoint المواقع عبر الإنترنت.

- Office برامج سطح المكتب (Excel PowerPoint وWord).

- Microsoft Teams القنوات ورسائل الدردشة.

بعد مزامنة النهج إلى المواقع الصحيحة، يبدأ في تقييم المحتوى وفرض الإجراءات.
<!-- what is the time delay for first deployment of a policy and what is the sync schedule? -->

### <a name="policy-evaluation-in-onedrive-for-business-and-sharepoint-online-sites"></a>تقييم النهج في مواقع OneDrive for Business SharePoint Online

عبر جميع مواقع SharePoint عبر الإنترنت ومواقع OneDrive for Business، تتغير المستندات باستمرار ، حيث يتم إنشاؤها وتحريرها ومشاركتها باستمرار وما إلى ذلك. وهذا يعني أن المستندات يمكن أن تتعارض أو تصبح متوافقة مع نهج DLP في أي وقت. على سبيل المثال، يمكن للشخص تحميل مستند لا يحتوي على أي معلومات حساسة إلى موقع الفريق، ولكن في وقت لاحق، يمكن لشخص آخر تحرير المستند نفسه وإضافة معلومات حساسة إليه.

لهذا السبب، تتحقق نهج DLP من المستندات بحثا عن تطابقات النهج بشكل متكرر في الخلفية. يمكنك التفكير في هذا على أنه تقييم نهج غير متزامن.
<!-- what is the frequency? looks like it is tied to the search crawl schedule -->

#### <a name="how-it-works"></a>كيفية عملها

بينما يضيف الأشخاص المستندات أو يغيرونها في مواقعهم، يقوم محرك البحث بمسح المحتوى ضوئيا، بحيث يمكنك البحث عنه لاحقا. في أثناء حدوث ذلك، يتم أيضا مسح المحتوى ضوئيا بحثا عن معلومات حساسة وللتحقق مما إذا كان مشتركا. يتم تخزين أي معلومات حساسة يتم العثور عليها بشكل آمن في فهرس البحث، بحيث يمكن فقط لفريق الامتثال الوصول إليها، ولكن ليس المستخدمين النموذجيين. يتم تشغيل كل نهج DLP قمت بتشغيله في الخلفية (بشكل غير متزامن)، والتحقق من البحث بشكل متكرر عن أي محتوى يطابق النهج، وتطبيق إجراءات لحمايته من التسريبات غير المقصودة.

![رسم تخطيطي يوضح كيفية تقييم نهج DLP للمحتوى بشكل غير متزامن.](../media/bdf73099-039a-4909-ae89-ac12c41992ba.png)

<!-- conflict with a DLP policy is bad wording -->
وأخيرا، يمكن أن تتعارض المستندات مع نهج DLP، ولكن يمكن أن تصبح أيضا متوافقة مع نهج DLP. على سبيل المثال، إذا قام شخص بإضافة أرقام بطاقات ائتمان إلى مستند، فقد يؤدي ذلك إلى حظر نهج DLP الوصول إلى المستند تلقائيا. ولكن إذا قام الشخص في وقت لاحق بإزالة المعلومات الحساسة، يتم التراجع عن الإجراء (في هذه الحالة، الحظر) تلقائيا في المرة التالية التي يتم فيها تقييم المستند مقابل النهج.

يقيم DLP أي محتوى يمكن فهرسته. لمزيد من المعلومات حول أنواع الملفات التي يتم تتبع ارتباطاتها بشكل افتراضي، راجع [ملحقات أسماء الملفات التي تم تتبع ارتباطاتها الافتراضية وأنواع الملفات الموزعة في SharePoint Server](/SharePoint/technical-reference/default-crawled-file-name-extensions-and-parsed-file-types).

> [!NOTE]
> لمنع مشاركة المستندات قبل أن تتاح لنهج DLP الفرصة لتحليلها، يمكن حظر مشاركة الملفات الجديدة في SharePoint حتى تتم فهرسة محتواها. انظر، [ضع علامة على الملفات الجديدة كالملفات الحساسة بشكل افتراضي](/sharepoint/sensitive-by-default) للحصول على معلومات مفصلة.

### <a name="policy-evaluation-in-exchange-online-outlook-and-outlook-on-the-web"></a>تقييم النهج في Exchange Online Outlook Outlook على ويب

عند إنشاء نهج DLP يتضمن Exchange Online كموقع، تتم مزامنة النهج من مدخل توافق Microsoft Purview إلى Exchange Online، ثم من Exchange Online إلى Outlook على ويب Outlook.

عند إنشاء رسالة في Outlook، يمكن للمستخدم رؤية تلميحات النهج عند تقييم المحتوى الذي يتم إنشاؤه مقابل نهج DLP. وبعد إرسال رسالة، يتم تقييمها مقابل نهج DLP كجزء عادي من تدفق البريد، إلى جانب قواعد تدفق البريد Exchange (المعروفة أيضا بقواعد النقل) ونهج DLP التي تم إنشاؤها في <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">مركز إدارة Exchange</a>. تقوم نهج DLP بفحص كل من الرسالة وأي مرفقات.

### <a name="policy-evaluation-in-the-office-desktop-programs"></a>تقييم النهج في برامج سطح المكتب Office

<!-- same capability to identify sensitive information line conflates sensitive information types and such -->
تتضمن Excel PowerPoint وWord نفس القدرة على تحديد المعلومات الحساسة وتطبيق نهج DLP على أنها SharePoint عبر الإنترنت OneDrive for Business. تقوم هذه البرامج Office بمزامنة نهج DLP الخاصة بها مباشرة من مخزن النهج المركزي، ثم تقييم المحتوى باستمرار مقابل نهج DLP عندما يعمل الأشخاص مع المستندات المفتوحة من موقع مضمن في نهج DLP.

تم تصميم تقييم نهج DLP في Office بحيث لا يؤثر على أداء البرامج أو إنتاجية الأشخاص الذين يعملون على المحتوى. إذا كانوا يعملون على مستند كبير، أو كان كمبيوتر المستخدم مشغولا، فقد يستغرق ظهور تلميح نهج بضع ثوان.

### <a name="policy-evaluation-in-microsoft-teams"></a>تقييم النهج في Microsoft Teams
 <!--what do you mean that it's synched to user accounts?  I thought DLP policies were applied to locations not users like sensitivity labels are  -->

عند إنشاء نهج DLP يتضمن Microsoft Teams كموقع، تتم مزامنة النهج من مدخل توافق Microsoft Purview إلى حسابات المستخدمين وقنوات Microsoft Teams ورسائل الدردشة. استنادا إلى كيفية تكوين نهج DLP، عندما يحاول شخص ما مشاركة معلومات حساسة في دردشة Microsoft Teams أو رسالة قناة، يمكن حظر الرسالة أو إبطالها. ولن تفتح المستندات التي تحتوي على معلومات حساسة وتتم مشاركتها مع الضيوف (المستخدمين الخارجيين) لهؤلاء المستخدمين. لمعرفة المزيد، راجع [منع فقدان البيانات Microsoft Teams](dlp-microsoft-teams.md).

## <a name="permissions"></a>الأذونات

بشكل افتراضي، سيكون لدى المسؤولين العموميين، ومسؤولين الأمان، ومسؤولين التوافق حق الوصول لإنشاء نهج DLP وتطبيقه. يحتاج الأعضاء الآخرون في فريق التوافق الذين سينشئون نهج DLP إلى أذونات لمدخل الامتثال ل Microsoft Purview. بشكل افتراضي، سيكون لمسؤول المستأجر حق الوصول إلى هذا الموقع ويمكنه منح مسؤولي الامتثال والأشخاص الآخرين حق الوصول إلى مدخل توافق Microsoft Purview، دون منحهم جميع أذونات مسؤول المستأجر. للقيام بذلك، نوصي بما يلي:

1. إنشاء مجموعة في Microsoft 365 وإضافة مسؤولي الامتثال إليها.

2. إنشاء مجموعة أدوار على صفحة **الأذونات** في مدخل توافق Microsoft Purview.

3. أثناء إنشاء مجموعة الأدوار، استخدم قسم **Choose Roles** لإضافة الدور التالي إلى مجموعة الأدوار: **DLP Compliance Management**.

4. استخدم المقطع **"اختيار أعضاء**" لإضافة مجموعة Microsoft 365 التي قمت بإنشائها من قبل إلى مجموعة الأدوار.

يمكنك أيضا إنشاء مجموعة أدوار مع امتيازات العرض فقط لنهج DLP وتقارير DLP عن طريق منح دور **View-Only DLP Compliance Management** .

لمزيد من المعلومات، راجع [منح المستخدمين حق الوصول إلى مركز التوافق Office 365](../security/office-365-security/grant-access-to-the-security-and-compliance-center.md).

هذه الأذونات مطلوبة فقط لإنشاء نهج DLP وتطبيقه. لا يتطلب تطبيق النهج الوصول إلى المحتوى.

## <a name="find-the-dlp-cmdlets"></a>البحث عن أوامر cmdlets DLP

لاستخدام معظم أوامر cmdlets لمدخل توافق Microsoft Purview، تحتاج إلى:

1. [الاتصال إلى Security & Compliance PowerShell](/powershell/exchange/connect-to-scc-powershell).

2. Use any of these [policy-and-compliance-dlp cmdlets](/powershell/module/exchange/export-dlppolicycollection).

ومع ذلك، تحتاج تقارير DLP إلى سحب البيانات من جميع Microsoft 365، بما في ذلك Exchange Online. لهذا السبب، ***تتوفر أوامر cmdlets لتقارير DLP في Exchange Online Powershell -- وليس في مدخل توافق Microsoft Purview Powershell***. لذلك، لاستخدام cmdlets لتقارير DLP، تحتاج إلى:

1. [الاتصال إلى Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

2. استخدم أيا من أوامر cmdlets هذه لتقارير DLP:

    - [Get-DlpDetectionsReport](/powershell/module/exchange/Get-DlpDetectionsReport)

    - [Get-DlpDetailReport](/powershell/module/exchange/Get-DlpDetailReport)

## <a name="more-information"></a>معلومات إضافية

- [إنشاء نهج DLP من قالب](create-a-dlp-policy-from-a-template.md)

- [إرسال إعلامات وإظهار تلميحات النهج لنهج DLP](use-notifications-and-policy-tips.md)

- [إنشاء نهج DLP لحماية المستندات باستخدام FCI أو خصائص أخرى](protect-documents-that-have-fci-or-other-properties.md)

- [ما تتضمنه قوالب نهج DLP](what-the-dlp-policy-templates-include.md)

- [تعريفات كيان نوع المعلومات الحساسة](sensitive-information-type-entity-definitions.md)

- [دالات نوع المعلومات الحساسة](sit-functions.md)

- [إنشاء نوع معلومات حساسة مخصص](create-a-custom-sensitive-information-type.md)
