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
ms.openlocfilehash: 0c7fe1d3ccf1b74641be1d05506f1cc53b743218
ms.sourcegitcommit: bb493f12701f6d6ee7d5e64b541adb87470bc7bc
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 02/18/2022
ms.locfileid: "63566510"
---
# <a name="data-loss-prevention-reference"></a>مرجع منع فقدان البيانات

> [!IMPORTANT]
> لم يعد هذا الموضوع المرجعي المورد الرئيسي Microsoft 365 معلومات منع فقدان البيانات (DLP). يتم تحديث مجموعة محتويات DLP وإعادة هيكلتها. سيتم نقل المواضيع التي تم تناولها في هذه المقالة إلى مقالات جديدة محدثة. لمزيد من المعلومات حول DLP، راجع [التعرف على منع فقدان البيانات](dlp-learn-about-dlp.md).

<!-- this topic needs to be split into smaller, more coherent ones. It is confusing as it is. -->
<!-- move this note to a more appropriate place, no topic should start with a note -->
> [!NOTE]
> لقد تم مؤخرا إضافة قدرات منع فقدان البيانات إلى Microsoft Teams رسائل الدردشة والقنوات للمستخدمين المرخص لهم خدمات الامتثال المتطورة في Office 365، والذي يتوفر كخيار مستقل ومضمن في Office 365 E5 و التوافق في Microsoft 365 E5. لمعرفة المزيد حول متطلبات الترخيص، راجع Microsoft 365 Tenant-Level [ترخيص الخدمات](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance).



<!-- MOVED TO LEARN ABOUT To comply with business standards and industry regulations, organizations must protect sensitive information and prevent its inadvertent disclosure. Sensitive information can include financial data or personally identifiable information (PII) such as credit card numbers, social security numbers, or health records. With a data loss prevention (DLP) policy in the Office 365 Security &amp; Compliance Center, you can identify, monitor, and automatically protect sensitive information across Office 365.

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
## <a name="create-and-manage-dlp-policies"></a>إنشاء سياسات DLP وإدارتها

يمكنك إنشاء سياسات DLP وإدارتها على صفحة منع فقدان البيانات في Microsoft 365 التوافق.

![صفحة منع فقدان البيانات في Office 365 توافق &amp; الأمان.](../media/943fd01c-d7aa-43a9-846d-0561321a405e.png)

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

## <a name="tuning-rules-to-make-them-easier-or-harder-to-match"></a>ضبط القواعد لتسهيل مطابقتها أو تصعب مطابقتها

بعد إنشاء الأشخاص لنهج DLP وتشغيلها، قد يخوضون أحيانا هذه المشاكل:

- يتطابق المحتوى الذي **لا** يتحسس المعلومات مع القواعد، بكلمات أخرى، عدد كبير جدا من الإيجابيات الخاطئة.

- يتطابق المحتوى القليل **جدا الذي يتحسس** المعلومات مع القواعد. بعبارة أخرى، لا يتم فرض إجراءات الحماية على المعلومات الحساسة.

لمعالجة هذه المشاكل، يمكنك ضبط القواعد من خلال ضبط عدد المثيلات ومطابقة الدقة لجعل المحتوى أكثر صعوبة أو سهولة لمطابقة القواعد. يحتوي كل نوع من أنواع المعلومات الحساسة المستخدمة في قاعدة على كل من دقة عدد المثيلات والمطابقة.

### <a name="instance-count"></a>عدد المثيلات

عدد المثيلات يعني ببساطة عدد مرات حدوث نوع معين من المعلومات الحساسة التي يجب أن تكون موجودة لكي يطابق المحتوى القاعدة. على سبيل المثال، يتطابق المحتوى مع القاعدة الموضحة أدناه إذا كانت بين 1 و9 فريدة من نوعها في الولايات المتحدة أو المملكة المتحدة. يتم تحديد أرقام جواز السفر.

> [!NOTE]
> يتضمن عدد المثيلات **التطابقات** الفريدة فقط لأنواع المعلومات الحساسة والكلمات الأساسية. على سبيل المثال، إذا احتوى البريد الإلكتروني على 10 تكرارات لرقم بطاقة الائتمان نفسه، يتم حساب عدد التكرارات ال 10 هذه كمثيل واحد لرقم بطاقة الائتمان.

لاستخدام عدد المثيلات لضبط القواعد، تكون الإرشادات مباشرة:

- لتسهيل مطابقة القاعدة، قم بخفض **عدد** الحد الأدنى و/أو زيادة **الحد الأقصى** للعد. يمكنك أيضا تعيين **الحد الأقصى** لأي **قيمة** عن طريق حذف القيمة الرقمية.

- لتجعل من الصعب مطابقة القاعدة، قم بزيادة **عدد** ال دقائق.

تستخدم عادة إجراءات أقل تقييدا، مثل إرسال إعلامات المستخدمين، في قاعدة ذات عدد مثيل أقل (على سبيل المثال، 1-9). كما يمكنك استخدام إجراءات أكثر تقييدا، مثل تقييد الوصول إلى المحتوى دون السماح للمستخدم بتجاوزه، في قاعدة ذات عدد مثيل أعلى (على سبيل المثال، 10-أي).

![عدد المثيلات في محرر القاعدة.](../media/e7ea3c12-72c5-4bb3-9590-c924c665e84d.png)

### <a name="match-accuracy"></a>مطابقة الدقة

كما هو موضح أعلاه، يتم تعريف نوع معلومات حساسة والكشف عنها باستخدام مجموعة من أنواع مختلفة من الدلائل. عادة، يتم تعريف نوع المعلومات الحساسة من خلال مجموعات متعددة من هذا النوع، تسمى الأنماط. النمط الذي يتطلب إثباتا أقل دقة مطابقة أقل (أو مستوى ثقة)، في حين أن النمط الذي يتطلب المزيد من الأدلة له دقة مطابقة أعلى (أو مستوى ثقة). لمعرفة المزيد حول الأنماط الفعلية ومستويات الثقة المستخدمة بواسطة كل نوع معلومات حساسة، راجع تعريفات [كيان نوع المعلومات الحساسة](sensitive-information-type-entity-definitions.md).

على سبيل المثال، يتم تعريف نوع المعلومات الحساسة المسمى "رقم بطاقة الائتمان" من خلال نمطين:

- نمط بثقة 65٪ يتطلب:

  - رقم بتنسيق رقم بطاقة ائتمان.

  - رقم يمرر الاختبارات.

- نمط بثقة 85٪ يتطلب:

  - رقم بتنسيق رقم بطاقة ائتمان.

  - رقم يمرر الاختبارات.

  - كلمة أساسية أو تاريخ انتهاء صلاحية بتنسيق صحيح.

يمكنك استخدام مستويات الثقة هذه (أو مطابقة الدقة) في القواعد. عادة، يمكنك استخدام إجراءات أقل تقييدا، مثل إرسال إعلامات المستخدم، في قاعدة ذات دقة مطابقة أقل. كما يمكنك استخدام إجراءات أكثر تقييدا، مثل تقييد الوصول إلى المحتوى دون السماح للمستخدم بتجاوزه، في قاعدة ذات دقة مطابقة أعلى.

من المهم فهم أنه عند تحديد نوع معين من المعلومات الحساسة، مثل رقم بطاقة الائتمان، في المحتوى، يتم إرجاع مستوى ثقة واحد فقط:

- إذا كانت كل المطابقات لنمط واحد، يتم إرجاع مستوى الثقة لهذا النمط.

- إذا كانت هناك تطابقات لأكثر من نمط واحد (أي، هناك تطابقات مع مستويي ثقة مختلفين)، يتم إرجاع مستوى ثقة أعلى من أي من الأنماط الفردية فقط. هذا هو الجزء المخادع. على سبيل المثال، إذا تطابق النمطان 65٪ و85٪ لبطاقة الائتمان، فإن مستوى الثقة الذي يتم إرجاعه لنوع المعلومات الحساس هذا أكبر من 90٪ لأن المزيد من الدلائل يعني المزيد من الثقة.

وبالتالي، إذا كنت تريد إنشاء قواعد حصرية متبادلة لبطاقة الائتمان، واحدة لدقة مطابقة بنسبة 65٪ واحدة لدقة مطابقة بنسبة 85٪، فإن نطاقات دقة مطابقة ستبدو كما هي. تلتقط القاعدة الأولى تطابقات النمط 65٪ فقط. تلتقط القاعدة الثانية تطابقات **بنسبة تطابق واحدة** على الأقل بنسبة 85٪ ويمكن أن يكون  لها تطابقات أخرى ذات ثقة أقل.

![هناك قواعد ذات نطاقات مختلفة لدقة مطابقة.](../media/21bdfe36-7a91-4347-8098-11809a92f9a4.png)

لهذه الأسباب، فإن إرشادات إنشاء قواعد ذات دقة مطابقة مختلفة هي:

- يستخدم أدنى مستوى ثقة عادة القيمة نفسها **لقيمة الحد** الأدنى **وقيمة الحد** الأقصى (وليس النطاق).

- عادة ما يكون أعلى مستوى ثقة هو نطاق يتراوح بين أعلى مستوى الثقة الأدنى و100.

- تتراوح عادة أي مستويات ثقة بين مستويات الثقة بين مستويات الثقة الأدنى إلى أقل من مستوى الثقة الأعلى.

## <a name="using-a-retention-label-as-a-condition-in-a-dlp-policy"></a>استخدام تسمية استبقاء كشرط في نهج DLP

عند استخدام تسمية استبقاء تم إنشاؤها [](retention.md#retention-labels) ونشرها مسبقا كشرط في نهج DLP، هناك بعض الأمور التي يجب أن تكون على علم بها:

- يجب إنشاء تسمية الاستبقاء ونشرها قبل محاولة استخدامها كشرط في نهج DLP.
- قد تستغرق مزامنة تسميات الاستبقاء المنشورة من يوم إلى سبعة أيام. لمزيد من المعلومات، راجع [](create-apply-retention-labels.md#when-retention-labels-become-available-to-apply) عندما تصبح تسميات الاستبقاء متوفرة لتطبيقها على تسميات الاستبقاء المنشورة في [](apply-retention-labels-automatically.md#how-long-it-takes-for-retention-labels-to-take-effect) نهج استبقاء، ومدى الوقت الذي يستغرقه تطبيق تسميات الاستبقاء على تسميات الاستبقاء التي يتم نشرها بشكل تلقائي.
- يتم دعم استخدام تسمية استبقاء في نهج ***فقط للعناصر الموجودة في SharePoint OneDrive***.

  ![التسميات كشرط.](../media/5b1752b4-a129-4a88-b010-8dcf8a38bb09.png)

  قد ترغب في استخدام تسمية استبقاء في نهج DLP إذا كانت لديك عناصر تحت الاستبقاء والتصرف، وتريد أيضا تطبيق عناصر تحكم أخرى عليها، على سبيل المثال:

  - لقد نشرت تسمية استبقاء باسم سنة **الضريبة 2018**، والتي تحتفظ بها المستندات الضريبية من عام 2018 المخزنة في SharePoint لمدة 10 سنوات ثم يتم التخلص منها. ولا تريد أيضا مشاركة هذه العناصر خارج مؤسستك، وهو ما يمكنك القيام به باستخدام نهج DLP.

  > [!IMPORTANT]
  > ستصلك رسالة الخطأ هذه إذا قمت بتحديد تسمية استبقاء كشرط في نهج DLP، كما قمت بتضمين Exchange و/أو Teams كمواضع: "حماية المحتوى المسمى في رسائل البريد الإلكتروني وفرق العمل غير **معتمدة. يمكنك إما إزالة التسمية أدناه أو إيقاف Exchange Teams كموا موقع".** وذلك لأن Exchange النقل لا يقيم بيانات تعريف التسمية أثناء إرسال الرسالة وتسليمها.

### <a name="using-a-sensitivity-label-as-a-condition-in-a-dlp-policy"></a>استخدام تسمية حساسية كشرط في نهج DLP

[تعرف على](./dlp-sensitivity-label-as-condition.md) المزيد حول استخدام تسمية الحساسية كشرط في سياسات DLP.

### <a name="how-this-feature-relates-to-other-features"></a>كيفية ارتباط هذه الميزة بالميزات الأخرى

يمكن تطبيق العديد من الميزات على المحتوى الذي يحتوي على معلومات حساسة:

- يمكن [أن تفرض تسمية الاستبقاء ونهاية](retention.md) الاستبقاء إجراءات **الاستبقاء** على هذا المحتوى.

- يمكن أن يفرض نهج DLP **إجراءات** الحماية على هذا المحتوى. وقبل فرض هذه الإجراءات، قد يتطلب نهج DLP الحصول على شروط أخرى بالإضافة إلى المحتوى الذي يحتوي على تسمية.

![رسم تخطيطي للميزات التي يمكن تطبيقها على المعلومات الحساسة.](../media/dd410f97-a3a3-455c-a1e9-7ed8ae6893d6.png)

تجدر الإشارة إلى أن نهج DLP لديه إمكانية كشف أغنى من التسمية أو نهج الاستبقاء المطبق على المعلومات الحساسة. يمكن أن يفرض نهج DLP إجراءات حماية على المحتوى الذي يحتوي على معلومات حساسة، وإذا تمت إزالة المعلومات الحساسة من المحتوى، يتم التراجع عن إجراءات الحماية هذه في المرة التالية التي يتم فيها فحص المحتوى. ولكن إذا تم تطبيق نهج استبقاء أو تسمية على محتوى يحتوي على معلومات حساسة، فلن يتم التراجع عن هذا الإجراء مرة واحدة حتى لو تمت إزالة المعلومات الحساسة.

باستخدام تسمية كشرط في نهج DLP، يمكنك فرض إجراءات الاستبقاء والحماية على المحتوى باستخدام هذه التسمية. يمكنك التفكير في محتوى يحتوي على تسمية تماما مثل المحتوى الذي يحتوي على معلومات حساسة - كل من التسمية ونوع المعلومات الحساسة من الخصائص المستخدمة لتصنيف المحتوى، بحيث يمكنك فرض الإجراءات على هذا المحتوى.

![رسم تخطيطي لنهوض DLP باستخدام التسمية كشرط.](../media/4538fd8f-fb74-4743-bc22-a5de33adfebb.png)

## <a name="simple-settings-vs-advanced-settings"></a>الإعدادات البسيطة مقابل الإعدادات المتقدمة

عند إنشاء نهج DLP، ستختار من بين الإعدادات البسيطة أو المتقدمة:

- **تجعل الإعدادات** البسيطة من السهل إنشاء النوع الأكثر شيوعا من نهج DLP دون استخدام محرر القاعدة لإنشاء القواعد أو تعديلها.

- **تستخدم الإعدادات المتقدمة** محرر القاعدة لتمنحك التحكم الكامل في كل إعداد من إعدادات نهج DLP.

لا تقلق، ضمن الأغطية، تعمل الإعدادات البسيطة والإعدادات المتقدمة بالطريقة نفسها تماما، من خلال فرض القواعد المكونة من الشروط والإجراءات— فقط باستخدام الإعدادات البسيطة، لن ترى محرر القاعدة. إنها طريقة سريعة لإنشاء نهج DLP.

### <a name="simple-settings"></a>إعدادات بسيطة

إن سيناريو DLP الأكثر شيوعا هو إنشاء نهج للمساعدة في حماية المحتوى الذي يحتوي على معلومات حساسة من المشاركة مع أشخاص من خارج مؤسستك، فضلا عن اتخاذ إجراء إصلاح تلقائي مثل تقييد الأشخاص الذين يمكنهم الوصول إلى المحتوى، وإرسال إعلامات المستخدم النهائي أو المسؤول، وتدقيق الحدث من أجل إجراء تحقيق لاحق. يستخدم الأشخاص DLP للمساعدة في منع الكشف عن المعلومات الحساسة عن غير قصد.

لتبسيط تحقيق هذا الهدف، عند إنشاء نهج DLP، يمكنك اختيار **استخدام الإعدادات البسيطة**. توفر هذه الإعدادات كل ما تحتاج إليه لتنفيذ نهج DLP الأكثر شيوعا، دون الحاجة إلى الانتقال إلى محرر القاعدة.

![خيارات DLP لإعدادات بسيطة ومتقدمة.](../media/33c93824-ead5-43b6-9c3e-fd1630c92a7d.png)

### <a name="advanced-settings"></a>الإعدادات المتقدمة

إذا كنت بحاجة إلى إنشاء المزيد من سياسات DLP المخصصة، يمكنك اختيار **استخدام الإعدادات المتقدمة**.

تقدم لك الإعدادات المتقدمة محرر القاعدة، حيث يمكنك التحكم الكامل في كل خيار ممكن، بما في ذلك عدد المثيلات والدقة المطابقة (مستوى الثقة) لكل قاعدة.

للتنقل بسرعة إلى مقطع ما، انقر فوق عنصر في الجزء العلوي من التنقل في محرر القاعدة للذهاب إلى ذلك المقطع أدناه.

![قائمة التنقل العلوية لمحرر قاعدة DLP.](../media/c527b97f-ca53-4c79-ad19-1a63be8a8ecc.png)

## <a name="dlp-policy-templates"></a>قوالب نهج DLP

الخطوة الأولى في إنشاء نهج DLP هي اختيار المعلومات التي يجب حمايتها. من خلال البدء باستخدام قالب DLP، يمكنك حفظ العمل على إنشاء مجموعة جديدة من القواعد من البداية، واكتشاف أنواع المعلومات التي يجب تضمينها بشكل افتراضي. يمكنك بعد ذلك الإضافة إلى هذه المتطلبات أو تعديلها لضبط القاعدة لتلبية المتطلبات المحددة لمنظمتك.

يمكن أن يساعدك قالب نهج DLP الذي تم تكوينه مسبقا على الكشف عن أنواع معينة من المعلومات الحساسة، مثل بيانات HIPAA أو بيانات PCI-DSS أو بيانات Gramm-Leach-Bliley Act أو حتى معلومات تعريف شخصية خاصة ب الإعدادات المحلية (P.I.). لسهولة البحث عن أنواع المعلومات الحساسة الشائعة وحمايتها، تحتوي قوالب النهج المضمنة في Microsoft 365 بالفعل على أنواع المعلومات الحساسة الأكثر شيوعا الضرورية للبدء.

![قائمة القوالب الخاصة ونهج منع فقدان البيانات مع التركيز على قالب قانون مكافحة فقدان البيانات في الولايات المتحدة.](../media/791b2403-430b-4987-8643-cc20abbd8148.png)

قد يكون لمنظمتك أيضا متطلباتها الخاصة، وفي هذه الحالة يمكنك إنشاء نهج DLP من البداية عن طريق تحديد **خيار النهج** المخصص. النهج المخصص فارغ ولا يحتوي على قواعد مسبقة الإعداد.

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

بعد إنشاء سياسات DLP و تشغيلها، سترغب في التحقق من عملها كما أردت ومساعدتك على البقاء متوافقا. باستخدام تقارير DLP، يمكنك بسرعة عرض عدد تطابقات نهج DLP ولقاعدةها مع مرور الوقت وعدد الموجبة والتجاوزات الخاطئة. لكل تقرير، يمكنك تصفية تلك المطابقات حسب الموقع أو الإطار الزمني، وحتى تضييق نطاقها إلى نهج أو قاعدة أو إجراء معين.

باستخدام تقارير DLP، يمكنك الحصول على تحليلات الأعمال و:

- ركز على فترات زمنية معينة وافهم أسباب الارتفاعات والاتجاهات.

- اكتشف عمليات الأعمال التي تنتهك سياسات التوافق الخاصة مؤسستك.

- فهم أي تأثير أعمال لنهج DLP.

بالإضافة إلى ذلك، يمكنك استخدام تقارير DLP لضبط سياسات DLP عند تشغيلها.

![لوحة معلومات التقارير في مركز الأمان والتوافق.](../media/6d741252-a0ce-4429-95ba-6c857ecc9a7e.png)

## <a name="how-dlp-policies-work"></a>كيفية عمل سياسات DLP

تكتشف DLP المعلومات الحساسة باستخدام تحليل المحتوى العميق (وليس فقط فحص النص البسيط). يستخدم تحليل المحتوى العميق هذا تطابقات الكلمات الأساسية ومطابقات القاموس وتقييم التعبيرات العادية والوظائف الداخلية والأساليب الأخرى للكشف عن المحتوى الذي يتطابق مع سياسات DLP. من المحتمل أن تكون نسبة مئوية صغيرة فقط من بياناتك حساسة. يمكن أن يحدد نهج DLP هذه البيانات فقط ويراقبها ويحميها تلقائيا، من دون أن يؤثر ذلك على الأشخاص الذين يعملون مع المحتوى الباقي أو يؤثر عليه.

### <a name="policies-are-synced"></a>تتم مزامنة السياسات

بعد إنشاء نهج DLP &amp; في مركز توافق الأمان، يتم تخزينه في مخزن نهج مركزي، ثم تتم مزامنته مع مصادر المحتوى المختلفة، بما في ذلك:

- Exchange Online، ومن هناك إلى Outlook على ويب Outlook.

- OneDrive for Business المواقع.

- SharePoint مواقع عبر الإنترنت.

- Office برامج سطح المكتب (Excel PowerPoint و Word).

- Microsoft Teams القنوات ورسائل الدردشة.

بعد مزامنة النهج إلى المواقع المناسبة، يبدأ بتقييم المحتوى وفرض الإجراءات.
<!-- what is the time delay for first deployment of a policy and what is the sync schedule? -->

### <a name="policy-evaluation-in-onedrive-for-business-and-sharepoint-online-sites"></a>تقييم النهج في OneDrive for Business SharePoint عبر الإنترنت

في كل مواقع SharePoint عبر الإنترنت OneDrive for Business، تتغير المستندات باستمرار، حيث يتم إنشاؤها وتحريرها ومشاركتها وما إلى ذلك. وهذا يعني أن المستندات قد تخالف نهج DLP أو تصبح متوافقة معه في أي وقت. على سبيل المثال، يمكن لشخص ما تحميل مستند لا يحتوي على معلومات حساسة إلى موقع الفريق، ولكن في وقت لاحق، يمكن لشخص آخر تحرير المستند نفسه وإضافة معلومات حساسة له.

لهذا السبب، تحقق نهج DLP من تطابق المستندات مع النهج بشكل متكرر في الخلفية. يمكنك التفكير في ذلك على أنه تقييم نهج غير متزامن.
<!-- what is the frequency? looks like it is tied to the search crawl schedule -->

#### <a name="how-it-works"></a>كيفية عمل ذلك

بينما يقوم الأشخاص بإضافة مستندات أو تغييرها في مواقعهم، يقوم محرك البحث بفحص المحتوى، بحيث يمكنك البحث عنه لاحقا. أثناء حدوث ذلك، يتم أيضا فحص المحتوى للحصول على معلومات حساسة والتحقق مما إذا كان مشتركا. يتم تخزين أي معلومات حساسة يتم العثور عليها بأمان في فهرس البحث، بحيث يمكن لفريق التوافق فقط الوصول إليها، وليس المستخدمين النموذجين. يتم تشغيل كل نهج DLP قمت بتشغيله في الخلفية (بشكل غير متزامن)، والتحقق من البحث بشكل متكرر عن أي محتوى يتطابق مع نهج، وتطبيق إجراءات لحمايته من التسريبات غير المتزامنة.

![رسم تخطيطي يعرض كيفية تقييم نهج DLP للمحتوى بشكل غير متزامن.](../media/bdf73099-039a-4909-ae89-ac12c41992ba.png)

<!-- conflict with a DLP policy is bad wording -->
وأخيرا، يمكن أن تعارض المستندات مع نهج DLP، ولكنها قد تصبح أيضا متوافقة مع نهج DLP. على سبيل المثال، إذا أضف أحد الأشخاص أرقام بطاقات الائتمان إلى مستند، فقد يتسبب نهج DLP في حظر الوصول إلى المستند تلقائيا. ولكن إذا أزل الشخص المعلومات الحساسة في وقت لاحق، يتم التراجع تلقائيا عن الإجراء (في هذه الحالة الحظر) في المرة التالية التي يتم فيها تقييم المستند مقابل النهج.

تقيم DLP أي محتوى يمكن فهرسته. لمزيد من المعلومات حول أنواع الملفات التي يتم تتبع ارتباطاتها بشكل افتراضي، راجع ملحقات أسماء الملفات التي تم تتبع ارتباطاتها الافتراضية وأنواع الملفات التي تم تحليلها [في SharePoint Server](/SharePoint/technical-reference/default-crawled-file-name-extensions-and-parsed-file-types).

> [!NOTE]
> لمنع مشاركة المستندات قبل أن تتاح لنهج DLP فرصة تحليلها، يمكن حظر مشاركة الملفات الجديدة في SharePoint حتى يتم فهرسة محتواها. راجع وضع [علامة على الملفات الجديدة كحساسة بشكل افتراضي](/sharepoint/sensitive-by-default) للحصول على معلومات مفصلة.

### <a name="policy-evaluation-in-exchange-online-outlook-and-outlook-on-the-web"></a>تقييم النهج في Exchange Online Outlook Outlook على ويب

عند إنشاء نهج DLP يتضمن Exchange Online كموا موقع، تتم مزامنة النهج من مركز توافق الأمان في Office 365 إلى Exchange Online، ثم من Exchange Online &amp; إلى Outlook على ويب و Outlook.

عند إنشاء رسالة في Outlook، يمكن للمستخدم رؤية تلميحات النهج عند تقييم المحتوى الذي يتم إنشاؤه مقابل نهج DLP. وبعد إرسال رسالة، يتم تقييمها مقابل سياسات DLP كجزء عادي من تدفق البريد، إلى جانب قواعد تدفق البريد في Exchange (المعروفة أيضا بقواعد النقل) ونهج DLP التي تم إنشاؤها في <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">Exchange مركز</a> إدارة البريد. تمسح سياسات DLP الرسالة وأي مرفقات.

### <a name="policy-evaluation-in-the-office-desktop-programs"></a>تقييم النهج في Office سطح المكتب

<!-- same capability to identify sensitive information line conflates sensitive information types and such -->
Excel PowerPoint و Word نفس الإمكانية لتحديد المعلومات الحساسة وتطبيق سياسات DLP SharePoint عبر الإنترنت OneDrive for Business. تعمل Office هذه البرامج على مزامنة نهج DLP مباشرة من مخزن النهج المركزي، ثم تقييم المحتوى بشكل مستمر مقابل نهج DLP عندما يعمل الأشخاص على المستندات المفتوحة من موقع مضمن في نهج DLP.

تم تصميم تقييم نهج DLP في Office بحيث لا يؤثر على أداء البرامج أو إنتاجية الأشخاص الذين يعملون على المحتوى. إذا كانوا يعملون على مستند كبير، أو كان كمبيوتر المستخدم مشغولا، فقد يستغرق ظهور تلميح نهج بضع ثوان.

### <a name="policy-evaluation-in-microsoft-teams"></a>تقييم النهج في Microsoft Teams
 <!--what do you mean that it's synched to user accounts?  I thought DLP policies were applied to locations not users like sensitivity labels are  -->

عند إنشاء نهج DLP يتضمن Microsoft Teams كموا موقع، تتم مزامنة النهج من مركز توافق الأمان في Office 365 &amp; إلى حسابات المستخدمين Microsoft Teams ورسائل الدردشة والقنوات. استنادا إلى كيفية تكوين سياسات DLP، عندما يحاول شخص ما مشاركة معلومات حساسة في رسالة Microsoft Teams أو قناة، يمكن حظر الرسالة أو إبطالها. ولن يتم فتح المستندات التي تحتوي على معلومات حساسة والمشتركة مع الضيوف (المستخدمون الخارجيون) لهؤلاء المستخدمين. لمعرفة المزيد، راجع [منع فقدان البيانات Microsoft Teams](dlp-microsoft-teams.md).

## <a name="permissions"></a>الأذونات

بشكل افتراضي، سيكون للمسؤولين العامين، لمسؤولي الأمان، ومسؤولي التوافق حق الوصول لإنشاء نهج DLP وتطبيقه. يحتاج الأعضاء الآخرين في فريق التوافق الذين سينشئون سياسات DLP إلى أذونات لمركز توافق &amp; الأمان. بشكل افتراضي &amp; ، سيكون لمسؤول المستأجر حق الوصول إلى هذا الموقع ويمكنه منح موظفي التوافق و الأشخاص الآخرين حق الوصول إلى مركز توافق الأمان، دون منحهم كل الأذونات من مسؤول المستأجر. للقيام بذلك، نوصي بما يلي:

1. أنشئ مجموعة في Microsoft 365 وأضف موظفي التوافق فيها.

2. إنشاء مجموعة دور على صفحة **الأذونات** في مركز توافق &amp; الأمان.

3. أثناء إنشاء مجموعة الأدوار، استخدم المقطع اختيار **الأدوار** لإضافة الدور التالي إلى مجموعة الأدوار: **إدارة توافق DLP**.

4. استخدم المقطع **اختيار أعضاء** لإضافة Microsoft 365 التي أنشأتها من قبل إلى مجموعة الدور.

يمكنك أيضا إنشاء مجموعة دور مع امتيازات العرض فقط لنهج DLP والتقارير DLP من خلال منح دور إدارة توافق **DLP ل View-only** .

لمزيد من المعلومات، راجع منح [المستخدمين حق الوصول إلى Office 365 التوافق.](../security/office-365-security/grant-access-to-the-security-and-compliance-center.md)

هذه الأذونات مطلوبة فقط لإنشاء نهج DLP وتطبيقه. لا يتطلب تطبيق النهج الوصول إلى المحتوى.

## <a name="find-the-dlp-cmdlets"></a>البحث عن cmdlets ل DLP

لاستخدام معظم cmdlets لمركز توافق &amp; الأمان، ستحتاج إلى:

1. [الاتصال إلى مركز Office 365 الأمان &amp; باستخدام PowerShell البعيد](/powershell/exchange/connect-to-scc-powershell).

2. استخدم أي من هذه [cmdlets الخاصة ب نهج وتوافق-dlp](/powershell/module/exchange/export-dlppolicycollection).

ومع ذلك، تحتاج تقارير DLP إلى سحب البيانات من Microsoft 365، بما في ذلك Exchange Online. لهذا السبب، **تتوفر cmdlets لتقارير DLP في Exchange Online Powershell ، &amp; وليس في مركز توافق الأمان في Powershell**. وبالتالي، لاستخدام cmdlets لتقارير DLP، ستحتاج إلى:

1. [الاتصال إلى Exchange Online PowerShell عن بعد](/powershell/exchange/connect-to-exchange-online-powershell).

2. استخدم أي من هذه cmdlets لتقارير DLP:

    - [Get-DlpDetectionsReport](/powershell/module/exchange/Get-DlpDetectionsReport)

    - [Get-DlpDetailReport](/powershell/module/exchange/Get-DlpDetailReport)

## <a name="more-information"></a>معلومات إضافية

- [إنشاء نهج DLP من قالب](create-a-dlp-policy-from-a-template.md)

- [إرسال الإعلامات وإظهار تلميحات النهج لنهج DLP](use-notifications-and-policy-tips.md)

- [إنشاء نهج DLP لحماية المستندات باستخدام FCI أو خصائص أخرى](protect-documents-that-have-fci-or-other-properties.md)

- [ما تتضمنه قوالب نهج DLP](what-the-dlp-policy-templates-include.md)

- [تعريفات كيان نوع المعلومات الحساسة](sensitive-information-type-entity-definitions.md)

- [دالات نوع المعلومات الحساسة](sit-functions.md)

- [إنشاء نوع معلومات حساسة مخصصة](create-a-custom-sensitive-information-type.md)
