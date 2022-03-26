---
title: إنشاء نهج DLP من قالب
f1.keywords:
- NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: 6/29/2018
audience: Admin
ms.topic: how-to
f1_keywords:
- ms.o365.cc.NewPolicyFromTemplate
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
search.appverid:
- MET150
ms.custom:
- seo-marvel-mar2020
- admindeeplinkCOMPLIANCE
description: في هذه المقالة، ستتعرف على كيفية إنشاء سياسات DLP باستخدام أحد القوالب المضمنة في Office 365.
ms.openlocfilehash: 965e5198887ec64072efffd35ffa7739c90af6a4
ms.sourcegitcommit: e3bff611439354e6339bb666a88682078f32ec13
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 02/03/2022
ms.locfileid: "63568542"
---
# <a name="create-a-dlp-policy-from-a-template"></a>إنشاء نهج DLP من قالب

الطريقة الأسهل والأكثر شيوعا للبدء باستخدام سياسات DLP هي استخدام أحد القوالب المضمنة في Microsoft 365 التوافق. يمكنك استخدام أحد هذه القوالب كما هو، أو تخصيص القواعد لتلبية متطلبات التوافق الخاصة لمنظمتك.

Microsoft 365 أكثر من 40 قالبا جاهزا للاستخدام يمكن أن تساعدك على تلبية مجموعة واسعة من الاحتياجات التنظيمية والاحتياجات العامة لسياسة الأعمال. راجع؛ [قوالب النهج](dlp-policy-reference.md#policy-templates) لقائمة كاملة. 

يمكنك ضبط قالب عن طريق تعديل أي من قواعده الموجودة أو إضافة قواعد جديدة. على سبيل المثال، يمكنك إضافة أنواع جديدة من المعلومات الحساسة إلى قاعدة، أو تعديل عددها في قاعدة ما لتجعل من الصعب أو الأسهل تشغيلها، أو السماح للأشخاص بتجاوز الإجراءات في قاعدة من خلال توفير مبرر عمل، أو تغيير الأشخاص الذين يتم إرسال الإعلامات والتقارير المتعلقة بالحوادث لهم. إن قالب نهج DLP هو نقطة بداية مرنة للعديد من سيناريوهات التوافق الشائعة.

يمكنك أيضا اختيار القالب مخصص، الذي لا يحتوي على قواعد افتراضية، وتكوين نهج DLP من البداية، لتلبية متطلبات التوافق الخاصة لمنظمتك.

## <a name="permissions"></a>الأذونات

يحتاج أعضاء فريق التوافق الذين سينشئون سياسات DLP إلى أذونات لمركز التوافق. بشكل افتراضي، سيكون لمسؤول المستأجر حق الوصول الذي يمكنه منح موظفي التوافق و الأشخاص الآخرين حق الوصول. اتبع الخطوات التالية:
  
1. أنشئ مجموعة في Microsoft 365 وأضف موظفي التوافق فيها.
    
2. إنشاء مجموعة دور على صفحة **الأذونات** في مركز توافق &amp; الأمان. 

3. أثناء إنشاء مجموعة الأدوار، استخدم المقطع اختيار **الأدوار** لإضافة الدور التالي إلى مجموعة الأدوار: **إدارة توافق DLP**.
    
4. استخدم المقطع **اختيار أعضاء** لإضافة Microsoft 365 التي أنشأتها من قبل إلى مجموعة الدور.

استخدم دور **إدارة توافق DLP ل View-only** لإنشاء مجموعة دور مع امتيازات العرض فقط لنهج DLP والتقارير DLP.

لمزيد من المعلومات، راجع منح [المستخدمين حق الوصول إلى Office 365 التوافق.](../security/office-365-security/grant-access-to-the-security-and-compliance-center.md)
  
هذه الأذونات مطلوبة لإنشاء نهج DLP وتطبيقه لا لفرض النهج.

### <a name="roles-and-role-groups-in-preview"></a>الأدوار ومجموعات الأدوار في المعاينة

هناك أدوار ومجموعات أدوار في المعاينة يمكنك اختبارها لضبط عناصر التحكم بالوصول.

فيما يلي قائمة بأدوار حماية البيانات في Microsoft (MIP) في المعاينة. لمعرفة المزيد حولها، راجع [الأدوار في مركز & الأمان](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center)

- مسؤول حماية المعلومات
- محلل حماية المعلومات
- حماية المعلوماتمحقق
- قارئ حماية المعلومات

فيما يلي قائمة مجموعات دور MIP التي تكون في المعاينة. لمعرفة المزيد حول، راجع [مجموعات الدور في مركز & الأمان](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#role-groups-in-the-security--compliance-center)

- حماية المعلومات
- مسؤولو حماية المعلومات
- محللو حماية المعلومات
- الباحثون عن حماية المعلومات
- قراء حماية المعلومات

### <a name="create-the-dlp-policy-from-a-template"></a>إنشاء نهج DLP من قالب

1. سجل <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">الدخول إلى مركز التوافق في Microsoft 365</a>.

2. في مركز التوافق للتنقل \> الأيسر \> **حلول** \> **منع فقدان** \> البيانات **نهج** \> **+ إنشاء نهج**.

    ![إنشاء زر نهج.](../media/b1e48a08-92e2-47ca-abdc-4341694ddc7c.png)
          
3. اختر قالب نهج DLP الذي يحمي أنواع المعلومات الحساسة التي تحتاج إليها \> **التالي**.

4. تسمية النهج **التالي**\>.
 
<!--In this example, you'll select **Privacy** \> **U.S. Personally Identifiable Information (PII) Data** because it already includes most of the types of sensitive information that you want to protect - you'll add a couple later.

    When you select a template, you can read the description on the right to learn what types of sensitive information the template protects.

    ![Page for choosing a DLP policy template.](../media/775266f6-ad87-4080-8d7c-97f2e7403b30.png)-->

5. لاختيار المواقع التي تريد أن يحميها نهج DLP وإما قبول النطاق الافتراضي لكل موقع أو تخصيص النطاق. راجع، [مواقع](dlp-policy-reference.md#locations) خيارات تحديد الموقع.

6. اختر \> **التالي**.
 
1. القيام بوا واحد من الخطوات التالية:

   - اختر **كافة المواقع في Office 365** \> **التالي**.
   - اختر **السماح لي باختيار مواقع محددة** \> **التالي**. في هذا المثال، اختر هذا.

   لتضمين موقع كامل أو استبعاده مثل كل Exchange الإلكتروني أو كل حسابات OneDrive، قم بتبديل **حالة** هذا الموقع أو إيقاف تشغيله.

   لتضمين مواقع SharePoint أو حسابات OneDrive for Business، قم بتبديل الحالة إلى تشغيل، ثم  انقر فوق الارتباطات ضمن تضمين لاختيار مواقع أو حسابات  معينة. عند تطبيق نهج على موقع، يتم تطبيق القواعد التي تم تكوينها في هذا النهج تلقائيا على كل المواقع الفرعية لهذا الموقع.

   ![خيارات للمواقع التي يمكن تطبيق نهج DLP عليها.](../media/all-locations.png)

   في هذا المثال، لحماية المعلومات الحساسة المخزنة في كل حسابات OneDrive for Business، قم إيقاف تشغيل الحالة لكل  من البريد الإلكتروني Exchange ومواقع **SharePoint**، واترك الحالة في حسابات **OneDrive**  **.**

7. اختر **مراجعة الإعدادات الافتراضية وتخصيصها من القالب** \> **التالي**.

8. يحتوي قالب نهج DLP على قواعد محددة مسبقا مع شروط والإجراءات التي تكشف عن أنواع معينة من المعلومات الحساسة وتتصرف بناء عليها. يمكنك تحرير أي من القواعد الموجودة أو حذفها أو إيقاف تشغيلها أو إضافة قواعد جديدة. عند القيام بذلك، انقر فوق **التالي**.

    ![القواعد الموسعة في قالب نهج PII الأمريكية.](../media/3bc9f1b6-f8ad-4334-863a-24448bb87687.png)

9. اختر الكشف عن وقت مشاركة هذا المحتوى داخل مؤسستك أو خارجها إذا قمت بتحديد أي من هذه المواقع:
    1. Exchange
    1. SharePoint
    1. OneDrive
    1. Teams رسائل الدردشة والقناة 

10. اختر **التالي**.

11. في صفحة **إجراءات الحماية** ، يمكنك تخصيص إعلامات تلميح النهج ورسائل البريد الإلكتروني الإعلامية. تمكين **عندما يتطابق المحتوى** مع شروط النهج، قم بإظهار تلميحات النهج للمستخدمين وأرسل إليهم إعلاما بالبريد الإلكتروني، ثم اختر **تخصيص التلميح والبريد الإلكتروني**.
12. اختر **التالي**.


<!--    In this example, the U.S. PII Data template includes two predefined rules:

   - **Low volume of content detected U.S. PII** This rule looks for files containing between 1 and 10 occurrences of each of three types of sensitive information (ITIN, SSN, and U.S. passport numbers), where the files are shared with people outside the organization. If found, the rule sends an email notification to the primary site collection administrator, document owner, and person who last modified the document.

   - **High volume of content detected U.S. PII** This rule looks for files containing 10 or more occurrences of each of the same three sensitive information types, where the files are shared with people outside the organization. If found, this action also sends an email notification, plus it restricts access to the file. For content in a OneDrive for Business account, this means that permissions for the document are restricted for everyone except the primary site collection administrator, document owner, and person who last modified the document.

    To meet your organization's specific requirements, you may want to make the rules easier to trigger, so that a single occurrence of sensitive information is enough to block access for external users. After looking at these rules, you understand that you don't need low and high count rules—you need only a single rule that blocks access if any occurrence of sensitive information is found.

    So you expand the rule named **Low volume of content detected U.S. PII** \> **Delete rule**.

    ![Delete rule button.](../media/bc36f7d2-0fae-4af1-92e8-95ba51077b12.png)

9. Now, in this example, you need to add two sensitive information types (U.S. bank account numbers and U.S. driver's license numbers), allow people to override a rule, and change the count to any occurrence. You can do all of this by editing one rule, so select **High volume of content detected U.S. PII** \> **Edit rule**.

    ![Edit rule button.](../media/eaf54067-4945-4c98-8dd6-fb2c5d6de075.png)

10. To add a sensitive information type, in the **Conditions** section \> **Add or change types**. Then, under **Add or change types** \> choose **Add** \> select **U.S. Bank Account Number** and **U.S. Driver's License Number** \> **Add** \> **Done**.

    ![Option to Add or change types.](../media/c6c3ae86-f7db-40a8-a6e4-db11692024be.png)

    ![Add or change types pane.](../media/fdbb96af-b914-4a6c-a97b-bbd014689965.png)

11. To change the count (the number of instances of sensitive information required to trigger the rule), under **Instance count** \> choose the **min** value for each type \> enter 1. The minimum count cannot be empty. The maximum count can be empty; an empty **max** value convert to **any**.

    When finished, the min count for all of the sensitive information types should be **1** and the max count should be **any**. In other words, any occurrence of this type of sensitive information will satisfy this condition.

    ![Instance counts for sensitive information types.](../media/5c6e08cb-59a9-4558-b54b-d899836d4737.png)

12. For the final customization, you don't want your DLP policies to block people from doing their work when they have a valid business justification or encounter a false positive, so you want the user notification to include options to override the blocking action.

    In the **User notifications** section, you can see that email notifications and policy tips are turned on by default for this rule in the template.

    In the **User overrides** section, you can see that overrides for a business justification are turned on, but overrides to report false positives are not. Choose **Override the rule automatically if they report it as a false positive**.

    ![User notifications section and User overrides section.](../media/62720e7a-a939-4c03-b414-67748f3d64a0.png)

13. At the top of the rule editor, change the name of this rule from the default **High volume of content detected U.S. PII** to **Any content detected with U.S. PII** because it's now triggered by any occurrence of its sensitive information types.

14. At the bottom of the rule editor \> **Save**.

15. Review the conditions and actions for this rule \> **Next**.

    On the right, notice the **Status** switch for the rule. If you turn off an entire policy, all rules contained in the policy are also turned off. However, here you can turn off a specific rule without turning off the entire policy. This can be useful when you need to investigate a rule that is generating a large number of false positives.

16. On the next page, read and understand the following, and then choose whether to turn on the rule or test it out first \> **Next**.

     Before you create your DLP policies, you should consider rolling them out gradually to assess their impact and test their effectiveness before you fully enforce them. For example, you don't want a new DLP policy to unintentionally block access to thousands of documents that people require to get their work done.

    If you're creating DLP policies with a large potential impact, we recommend following this sequence:

17. Start in test mode without Policy Tips and then use the DLP reports to assess the impact. You can use DLP reports to view the number, location, type, and severity of policy matches. Based on the results, you can fine tune the rules as needed. In test mode, DLP policies will not impact the productivity of people working in your organization.

18. Move to Test mode with notifications and Policy Tips so that you can begin to teach users about your compliance policies and prepare them for the rules that are going to be applied. At this stage, you can also ask users to report false positives so that you can further refine the rules.

19. Turn on the policies so that the rules are enforced and the content's protected. Continue to monitor the DLP reports and any incident reports or notifications to make sure that the results are what you intend.

    ![Options for using test mode and turning on policy.](../media/49fafaac-c6cb-41de-99c4-c43c3e380c3a.png)

20. Review your settings for this policy \> choose **Create**.

After you create and turn on a DLP policy, it's deployed to any content sources that it includes, such as SharePoint Online sites or OneDrive for Business accounts, where the policy begins automatically enforcing its rules on that content.


## Example: Identify sensitive information across all OneDrive for Business sites and restrict access for people outside your organization

OneDrive for Business accounts make it easy for people across your organization to collaborate and share documents. But a common concern for compliance officers is that sensitive information stored in OneDrive for Business accounts may be inadvertently shared with people outside your organization. A DLP policy can help mitigate this risk.

In this example, you'll create a DLP policy that identifies U.S. PII data, which includes Individual Taxpayer Identification Numbers (ITIN), Social Security Numbers, and U.S. passport numbers. You'll get started by using a template, and then you'll modify the template to meet your organization's compliance requirements—specifically, you'll:

- Add a couple of types of sensitive information—U.S. bank account numbers and U.S. driver's license numbers—so that the DLP policy protects even more of your sensitive data.

- Make the policy more sensitive, so that a single occurrence of sensitive information is enough to restrict access for external users.

- Allow users to override the actions by providing a business justification or reporting a false positive. This way, your DLP policy won't prevent people in your organization from getting their work done, provided they have a valid business reason for sharing the sensitive information.


## View the status of a DLP policy

At any time, you can view the status of your DLP policies on the **Policy** page in the **Data loss prevention** section of the Security &amp; Compliance Center. Here you can find important information, such as whether a policy was successfully enabled or disabled, or whether the policy is in test mode.

Here are the different statuses and what they mean.

<br>

****

|Status|Explanation|
|---|---|
|**Turning on…**|The policy is being deployed to the content sources that it includes. The policy is not yet enforced on all sources.|
|**Testing, with notifications**|The policy is in test mode. The actions in a rule are not applied, but policy matches are collected and can be viewed by using the DLP reports. Notifications about policy matches are sent to the specified recipients.|
|**Testing, without notifications**|The policy is in test mode. The actions in a rule are not applied, but policy matches are collected and can be viewed by using the DLP reports. Notifications about policy matches are not sent to the specified recipients.|
|**On**|The policy is active and enforced. The policy was successfully deployed to all its content sources.|
|**Turning off...**|The policy is being removed from the content sources that it includes. The policy may still be active and enforced on some sources. Turning off a policy may take up to 45 minutes.|
|**Off**|The policy is not active and not enforced. The settings for the policy (sources, keywords, duration, etc) are saved.|
|**Deleting...**|The policy is in the process of being deleted. The policy is not active and not enforced. It normally takes an hour for a policy to delete.|
|

## Turn off a DLP policy

You can edit or turn off a DLP policy at any time. Turning off a policy disables all of the rules in the policy.

To edit or turn off a DLP policy, on the **Policy** page \> select the policy \> **Edit policy**.

![Edit policy button.](../media/ce319e92-0519-44fe-9507-45a409eaefe4.png)

In addition, you can turn off each rule individually by editing the policy and then toggling off the **Status** of that rule, as described above.

## More information

- [Learn about data loss prevention](dlp-learn-about-dlp.md)
- [Send notifications and show policy tips for DLP policies](use-notifications-and-policy-tips.md)
- [Create a DLP policy to protect documents with FCI or other properties](protect-documents-that-have-fci-or-other-properties.md)
- [What the DLP policy templates include](what-the-dlp-policy-templates-include.md)
- [Sensitive information type entity definitions](sensitive-information-type-entity-definitions.md)
