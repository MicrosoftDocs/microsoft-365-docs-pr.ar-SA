---
title: بدء استخدام DLP ل Power BI
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
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
- m365solution-mip
- m365initiative-compliance
ms.custom: admindeeplinkCOMPLIANCE
search.appverid:
- MET150
description: الاستعداد ل DLP وتوزيعه في مواقع PowerBI.
ms.openlocfilehash: f831d42898e491258a53423c1d59b9f50c0b289d
ms.sourcegitcommit: 44ece87e3e0c0c851dfc1e77211ac3e5e4a5b973
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/05/2022
ms.locfileid: "66616926"
---
# <a name="get-started-with-data-loss-prevention-policies-for-power-bi-preview"></a>بدء استخدام سياسات منع فقدان البيانات لـ Power BI (معاينة)

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

لمساعدة المؤسسات على اكتشاف بياناتها الحساسة وحمايتها، تدعم [نهج منع فقدان بيانات Microsoft Purview (DLP)](/microsoft-365/compliance/dlp-learn-about-dlp) Power BI. عندما تتطابق مجموعة بيانات PowerBI مع المعايير في نهج DLP، يمكن تشغيل تنبيه يشرح طبيعة المحتوى الحساس. يتم تسجيل هذا التنبيه أيضا في علامة التبويب " **تنبيهات** منع فقدان البيانات" في مدخل توافق Microsoft للمراقبة والإدارة من قبل المسؤولين. بالإضافة إلى ذلك، يمكن إرسال تنبيهات البريد الإلكتروني إلى المسؤولين والمستخدمين المحددين.

## <a name="considerations-and-limitations"></a>الاعتبارات والقيود

- تنطبق نهج DLP على مساحات العمل. يتم دعم مساحات العمل المستضافة في قدرات Premium Gen2 فقط. لمزيد من المعلومات، راجع [ما هو Power BI Premium Gen2؟](/power-bi/enterprise/service-premium-gen2-what-is).
- تؤثر أحمال عمل تقييم مجموعة بيانات DLP على السعة. لا يتم دعم القياس لأحمال عمل تقييم DLP.
- يتم دعم مساحات عمل التجربة الكلاسيكية والجديدة، طالما أنها مستضافة في قدرات Premium Gen2.
- يجب إنشاء نهج مخصص DLP مخصص ل Power BI. قوالب DLP غير معتمدة.
- تدعم نهج DLP التي يتم تطبيقها على موقع DLP تسميات الحساسية وأنواع المعلومات الحساسة كشروط. 
- لا يتم دعم نهج DLP ل Power BI لمجموعات البيانات النموذجية أو [مجموعات البيانات المتدفقة](/power-bi/connect-data/service-real-time-streaming) أو مجموعات البيانات التي تتصل بمصدر البيانات الخاص بها عبر [DirectQuery](/power-bi/connect-data/desktop-use-directquery) أو [الاتصال المباشر](/power-bi/connect-data/desktop-directquery-about#live-connections).
- لا يتم دعم نهج DLP ل Power BI في السحب ذات السيادة.

## <a name="licensing-and-permissions"></a>الترخيص والأذونات

### <a name="skusubscriptions-licensing"></a>ترخيص SKU/الاشتراكات

قبل البدء باستخدام DLP ل Power BI، يجب عليك تأكيد [اشتراكك في Microsoft 365](https://www.microsoft.com/microsoft-365/compare-microsoft-365-enterprise-plans?rtc=1). للحصول على إرشادات الترخيص الكامل، راجع [إرشادات Microsoft 365 للامتثال & الأمان](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#information-protection).

### <a name="permissions"></a>الأذونات

يمكن عرض البيانات من DLP ل Power BI في [مستكشف النشاط](/microsoft-365/compliance/data-classification-activity-explorer). هناك أربعة أدوار تمنح الإذن لمستكشف النشاط؛ يجب أن يكون الحساب الذي تستخدمه للوصول إلى البيانات عضوا في أي منها.

- المسؤول العام
- مسؤول التوافق
- مسؤول الأمان
- مسؤول بيانات التوافق

## <a name="how-dlp-policies-for-power-bi-work"></a>كيفية عمل نهج DLP ل Power BI

يمكنك تحديد نهج DLP في قسم منع فقدان البيانات من مدخل التوافق. انظر، [تصميم نهج منع فقدان البيانات](dlp-policy-design.md#design-a-data-loss-prevention-policy). في النهج، يمكنك تحديد تسمية (تسميات) الحساسية التي تريد الكشف عنها. يمكنك أيضا تحديد الإجراء (الإجراءات) الذي سيحدث عندما يكشف النهج عن مجموعة بيانات تم تطبيق تسمية حساسية محددة عليها. تدعم نهج DLP إجراءين ل Power BI:

- إعلام المستخدم عبر تلميحات النهج.
- تنبيهات. يمكن إرسال التنبيهات عبر البريد الإلكتروني إلى المسؤولين والمستخدمين. بالإضافة إلى ذلك، يمكن للمسؤولين مراقبة التنبيهات وإدارتها على علامة التبويب **«Alerts** » في مركز الامتثال. 

عند تقييم مجموعة بيانات بواسطة DLP وتطابق الشروط في نهج DLP، يتم تطبيق الإجراءات المحددة في النهج. يتم تقييم مجموعة البيانات عندما تكون مجموعة البيانات:

- نشر
- نشر
- تحديث عند الطلب
- تحديث مجدول

>[!NOTE]
> لا يحدث تقييم DLP لمجموعة البيانات إذا كان أي مما يلي صحيحا:
> - بادئ الحدث هو كيان الخدمة.
> - مالك مجموعة البيانات إما كيان خدمة أو مستخدم B2B.

### <a name="what-happens-when-a-dataset-matches-a-dlp-policy"></a>ماذا يحدث عندما تتطابق مجموعة البيانات مع نهج DLP

عندما تتطابق مجموعة البيانات مع نهج DLP:

- إذا تم تكوين إعلام المستخدم في النهج، فسيتم وضع علامة عليه في خدمة Power BI باستخدام أيقونة الدرع للإشارة إلى أنه يطابق نهج DLP.

    ![لقطة شاشة لشارة تلميح النهج على مجموعة البيانات في القوائم.](../media/dlp-power-bi-policy-tip-on-dataset.png)

    افتح صفحة تفاصيل مجموعة البيانات لرؤية تلميح نهج يشرح تطابق النهج وكيفية معالجة النوع المكتشف من المعلومات الحساسة.

    ![لقطة شاشة لتلميحات النهج في صفحة تفاصيل مجموعة البيانات.](../media/dlp-power-bi-policy-tip-in-dataset-details.png)

    >[!NOTE]
    > إذا قمت بإخفاء تلميح النهج، فلن يتم حذفه. سيظهر في المرة التالية التي تزور فيها الصفحة.

- إذا تم تمكين التنبيهات في النهج، فسيتم تسجيل تنبيه على علامة تبويب **تنبيهات** dlp في مركز الامتثال، وسيتم إرسال رسالة بريد إلكتروني إلى المسؤولين و/أو المستخدمين المحددين (إذا تم تكوينها). تعرض الصورة التالية علامة التبويب **Alerts** في قسم منع فقدان البيانات في مدخل التوافق في Microsoft Purview.

    ![لقطة شاشة لعلامة التبويب Alerts في مركز التوافق.](../media/dlp-power-bi-alerts-tab.png)

## <a name="configure-a-dlp-policy-for-power-bi"></a>تكوين نهج DLP ل Power BI

اتبع الإجراءات في [إنشاء نهج DLP واختباره وضبطه](create-test-tune-dlp-policy.md#create-test-and-tune-a-dlp-policy) واستخدم القالب المخصص.

> [!IMPORTANT]
> عند تحديد مواقع نهج DLP ل Power BI، حدد موقع Power BI فقط. لا تحدد أي مواقع أخرى، هذا التكوين غير معتمد. 

<!--1. Log into the [Microsoft Purview compliance portal](https://compliance.microsoft.com).

1. Choose the **Data loss prevention** solution in the navigation pane, select the **Policies** tab, choose **Create policy**.

    ![Screenshot of D L P create policy page.](media/service-security-dlp-policies-for-power-bi/power-bi-dlp-create.png)

1. Choose the **Custom** category and then the **Custom policy** template.
    
    >[!NOTE]
    >No other categories or templates are currently supported.

    ![Screenshot of D L P choose custom policy page.](media/service-security-dlp-policies-for-power-bi/power-bi-dlp-choose-custom.png)
 
    When done, click **Next**.

1. Name the policy and provide a meaningful description.

    ![Screenshot of D L P policy name description section.](media/service-security-dlp-policies-for-power-bi/power-bi-dlp-name-description.png)
 
    When done, click **Next**.

1. Enable Power BI as a location for the DLP policy. **Disable all other locations**. Currently, DLP policies for Power BI must specify Power BI as the sole location.

    ![Screenshot of D L P choose location page.](media/service-security-dlp-policies-for-power-bi/power-bi-dlp-choose-location.png)

    By default the policy will apply to all workspaces. Alternatively, you can specify particular workspaces to include in the policy as well as workspaces to exclude from the policy.
    >[!NOTE]
    > DLP actions are supported only for workspaces hosted in Premium Gen2 capacities.

    If you select **Choose workspaces** or **Exclude workspaces**, a dialog will allow you to create a list of included (or excluded) workspaces. You must specify workspaces by workspace object ID. Click the info icon for information about how to find workspace object IDs.

    ![Screenshot of D L P choose workspaces dialog.](media/service-security-dlp-policies-for-power-bi/power-bi-dlp-choose-workspaces.png)
 
    After enabling Power BI as a DLP location for the policy and choosing which workspaces the policy will apply to, click **Next**.

1. The **Define policy settings** page appears. Choose **Create or customize advanced DLP rules** to begin defining your policy.

    ![Screenshot of D L P create advanced rule page.](media/service-security-dlp-policies-for-power-bi/power-bi-dlp-create-advanced-rule.png)
 
    When done, click **Next**.

1. On the **Customize advanced DLP rules** page, you can either start creating a new rule or choose an existing rule to edit. Click **Create rule**.

    ![Screenshot of D L P create rule page.](media/service-security-dlp-policies-for-power-bi/power-bi-dlp-create-rule.png)


1. The **Create rule** page appears. On the create rule page, provide a name and description for the rule, and then configure the other sections, which are described following the image below.

    ![Screenshot of D L P create rule form.](media/service-security-dlp-policies-for-power-bi/power-bi-dlp-create-rule-form.png)
 
### Conditions

In the condition section, you define the conditions under which the policy will apply to a dataset. Conditions are created in groups. Groups make it possible to construct complex conditions.

1. Open the conditions section, choose **Add condition** and then **Content contains**.

    ![Screenshot of D L P add conditions content contains section.](media/service-security-dlp-policies-for-power-bi/power-bi-dlp-add-conditions-content-contains.png)
 
    This opens the first group (named Default – you can change this).

1. Choose **Add**, and then **Sensitivity labels**.
        
    >[!NOTE]
    > Sensitive info types are currently not supported.
    
    ![Screenshot of D L P add conditions section.](media/service-security-dlp-policies-for-power-bi/power-bi-dlp-add-conditions.png)
 
    When you choose **Sensitivity labels**, you will be able to choose a particular sensitivity label from a list that will appear.

    You can add additional sensitivity labels to the group. To the right of the group name, you can specify **Any of these** or **All of these**. This determines whether matches on all or any of the labels is required for the condition to hold. Make sure **Any of these** is selected, since datasets can’t have more than one label applied.

    The image below shows a group (Default) that contains two sensitivity label conditions. The logic Any of these means that a match on any one of the sensitivity labels in the group constitutes “true” for that group.

    ![Screenshot of D L P conditions group section.](media/service-security-dlp-policies-for-power-bi/power-bi-dlp-condition-group.png) 
 
    You can create more than one group, and you can control the logic between the groups with **AND** or **OR** logic. 

    The image below shows a rule containing two groups, joined by **OR** logic.

    ![Screenshot of rule with two groups.](media/service-security-dlp-policies-for-power-bi/power-bi-dlp-content-contains.png) 
 
### Exceptions

If the sensitivity label of the dataset matches any of the defined exceptions, the rule won’t be applied to the dataset. 

Exceptions are configured in the same way as conditions, described above.
    
![Screenshot of D L P exceptions section.](media/service-security-dlp-policies-for-power-bi/power-bi-dlp-exceptions-section.png)
 
### Actions

Protection actions are currently unavailable for Power BI DLP policies.

![Screenshot of D L P policy actions section.](media/service-security-dlp-policies-for-power-bi/power-bi-dlp-actions-section.png)


### User notifications

The user notifications section is where you configure your policy tip. Turn on the toggle, select the **Notify users in Office 365 service with a policy tip** and **Policy tips** checkboxes, and write your policy tip in the text box.

![Screenshot of D L P user notification section.](media/service-security-dlp-policies-for-power-bi/power-bi-dlp-user-notification.png)
 
### User overrides
 
User overrides are currently unavailable for Power BI DLP policies.

![Screenshot of D L P user overrides section.](media/service-security-dlp-policies-for-power-bi/power-bi-dlp-user-overrides-section.png) 
 
### Incident reports

Assign a severity level that will be shown in alerts generated from this policy. Enable (default) or disable email notification to admins, specify users or groups for email notification, and configure the details about when notification will occur.

![Screenshot of D L P incident report section.](media/service-security-dlp-policies-for-power-bi/power-bi-dlp-incidence-report.png)
   
### Additional options

![Screenshot of D L P additional options section.](media/service-security-dlp-policies-for-power-bi/power-bi-dlp-additional-options.png)
 
## Monitor and manage policy alerts

Log into the Microsoft Purview compliance portal and navigate to **Data loss prevention > Alerts**.

![Screenshot of D L P Alerts tab.](media/service-security-dlp-policies-for-power-bi/power-bi-dlp-alerts-tab.png)

Click on an alert to start drilling down to its details and to see management options.
-->
## <a name="next-steps"></a>الخطوات التالية

- [التعرّف على تفادي فقدان البيانات](/microsoft-365/compliance/dlp-learn-about-dlp)
- [أوصاف الحساسية في Power BI](/power-bi/enterprise/service-security-sensitivity-label-overview)
- [مخطط التدقيق لأوصاف الحساسية في Power BI](/power-bi/enterprise/service-security-sensitivity-label-audit-schema)
