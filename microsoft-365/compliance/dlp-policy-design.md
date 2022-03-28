---
title: تصميم نهج منع فقدان البيانات
f1.keywords:
- NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: ''
audience: ITPro
ms.topic: conceptual
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
search.appverid:
- MET150
description: تعرف على كيفية تصميم نهج منع فقدان البيانات (DLP)
ms.openlocfilehash: 14e9fbb5efd20ddcf3d0a47da41a0cce89c88cee
ms.sourcegitcommit: 3fb76db6b34e24569417f4c8a41b99f46a780389
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/17/2022
ms.locfileid: "63574721"
---
# <a name="design-a-data-loss-prevention-policy"></a>تصميم نهج منع فقدان البيانات

يؤدي أخذ الوقت لتصميم نهج قبل تنفيذه إلى الوصول إلى النتائج المطلوبة بشكل أسرع، ومع وجود عدد أقل من المشاكل غير المقصودة، مقارنة بإنشاء النهج ثم الضبط حسب الإصدار التجريبي والخطأ فقط. سيساعدك توثيق تصميمات النهج أيضا في الاتصالات ومراجعات النهج والاستعراضات وإصلاحها وضبطها بشكل أكبر.

<!--, but excessive tuning to get the intended results can be time consuming.

 if you have to do a lot of tuning to get a policy to yield the intended results can be time consuming .-->

إذا كنت من Microsoft 365 DLP، فمن المفيد استخدام هذه المقالات قبل البدء في تصميم نهج:

- [تعرف على منع فقدان](dlp-learn-about-dlp.md#learn-about-data-loss-prevention) البيانات - تعرفك هذه المقالة على مجال منع فقدان البيانات وتطبيق Microsoft ل DLP
- [التخطيط لمنع فقدان البيانات (DLP)](dlp-overview-plan-for-dlp.md#plan-for-data-loss-prevention-dlp) - من خلال العمل من خلال هذه المقالة، يمكنك:
    - [تحديد المساهمين](dlp-overview-plan-for-dlp.md#identify-stakeholders)
    - [وصف فئات المعلومات الحساسة لحمايتها](dlp-overview-plan-for-dlp.md#describe-the-categories-of-sensitive-information-to-protect)
    - [تعيين الأهداف والاستراتيجية](dlp-overview-plan-for-dlp.md#set-goals-and-strategy)
- [مرجع نهج منع فقدان](dlp-policy-reference.md#data-loss-prevention-policy-reference) البيانات - تقدم هذه المقالة كل مكونات نهج DLP وكيفية تأثير كل منها على سلوك النهج

## <a name="policy-design-overview"></a>نظرة عامة حول تصميم النهج

[يتعلق تصميم نهج في](#policy-design-process) معظمه بتعريف احتياجات عملك بوضوح[](#define-intent-for-the-policy)، وتوثيقها في بيان هدف النهج، ثم تعيين هذه الاحتياجات لتكوين [النهج](#map-business-needs-to-policy-configuration). سوف تستخدم القرارات التي اتخذتها في مرحلة التخطيط لإعلامك ببعض قرارات تصميم النهج. 

### <a name="define-intent-for-the-policy"></a>تعريف الهدف من النهج 

يجب أن تتمكن من تلخيص هدف العمل لكل نهج لديك في بيان واحد. سيدفع تطوير هذا البيان المحادثات في مؤسستك، وعندما يتم تبيانها بالكامل، فإن هذا البيان يربط النهج مباشرة لغرض عمل ويوفر خارطة طريق لتصميم النهج. ستساعدك الخطوات الموجودة في المقالة خطة منع فقدان البيانات [(DLP)](dlp-overview-plan-for-dlp.md#overview-of-planning-process) على بدء بيان هدف النهج.  

تذكر من نظرة [عامة حول تكوين نهج DLP](dlp-learn-about-dlp.md#dlp-policy-configuration-overview) أن كل نهج DLP تتطلب منك:

- اختر ما تريد مراقبته
- اختر المكان الذي تريد مراقبته
- اختيار الشروط التي يجب مطابقتها لكي يتم تطبيق نهج على عنصر
- اختر الإجراء الذي يجب اتخاذه عند استففاء شروط النهج 

على سبيل المثال، إليك المسودة الأولى الوهمية لبيان الهدف الذي يوفر إجابات لجميع الأسئلة الأربعة: 

*"نحن مؤسسة تستند إلى الولايات المتحدة، ونحتاج إلى الكشف عن Office مستندا تحتوي على معلومات العناية الصحية الحساسة التي تغطيها HIPPA المخزنة في OneDrive/SharePoint والحماية من تلك المعلومات التي يتم مشاركتها في رسائل الدردشة والقناة في Teams وتقييد الجميع من مشاركتها مع جهات خارجية غير مصرح بها".* 

بينما تقوم بتطوير تصميم نهج، من المرجح أن تقوم بتعديل العبارة وتوسيعها.

### <a name="map-business-needs-to-policy-configuration"></a>تعيين احتياجات الأعمال إلى تكوين النهج

فلنقطع المثال على مسودة البيان ونرسم خريطة له على نقاط تكوين نهج DLP.

|بيان  |تم الرد على سؤال التكوين ورسم خريطة التكوين  |
|---------|---------|
| "نحن مؤسسة تستند إلى الولايات المتحدة، ونحتاج إلى الكشف عن Office تحتوي على معلومات الرعاية الصحية الحساسة التي تغطيها HIPPA...  |- **ما يجب مراقبته**: Office المستندات، استخدم قالب قانون التأمين الصحي [(HIPAA)](what-the-dlp-policy-templates-include.md#us-health-insurance-act-hipaa) الأميركي </br>- شروط التطابق **: (** تم تكوينه مسبقا ولكن قابل للتحرير) - يحتوي العنصر على رقم SSN و"وكالة مكافحة المخدرات" (DEA) والتصنيف الدولي ل "المرض" (ICD-9-CM) والتصنيف الدولي ل "مواصفة" (ICD-10-CM)، حيث يتم مشاركة المحتوى مع أشخاص من خارج المؤسسة  </br> - دفع المحادثات لتوضيح عتبة المشغل للكشف مثل مستويات الثقة، [وعد](dlp-policy-reference.md#content-contains) المثيلات (يسمى التسامح مع التسريب).[](sensitive-information-type-learn-about.md#more-on-confidence-levels)|
|... المخزنة في OneDrive/SharePoint والحماية من تلك المعلومات التي يتم مشاركتها Teams رسائل الدردشة والقناة... |- **مكان المراقبة**: [تحديد](dlp-policy-reference.md#locations) الموقع عن طريق OneDrive مواقع SharePoint ومواقع Teams الدردشة/القناة أو مجموعات التوزيع أو استبعادها. |
|... وتقييد الجميع من مشاركة هذه العناصر مع جهات خارجية غير مصرح بها"."  | - **الإجراءات التي يجب اتخاذها**: [يمكنك إضافة](dlp-policy-reference.md#actions) *تقييد الوصول أو تشفير المحتوى في Microsoft 365 المواقع* </br> - دفع المحادثة حول الإجراءات التي يجب اتخاذها عند تشغيل نهج ما بما في ذلك إجراءات الحماية مثل قيود المشاركة، والإجراءات المتعلقة بالوعي مثل الإعلامات والتنبيهات، والإجراءات المتعلقة بتمكين المستخدم مثل السماح بتجاوز المستخدم لأي إجراء حظر |

لا يغطي هذا المثال كل نقاط تكوين نهج DLP، بل يجب توسيعه. ولكن يجب أن تفكر في الاتجاه الصحيح بينما تقوم بتطوير بيانات هدف نهج DLP الخاصة بك.

> [!IMPORTANT]
> ضع في اعتبارك أن الموقع (المواقع) الذي تختاره يؤثر على ما إذا كان يمكنك استخدام أنواع المعلومات الحساسة وتسميات الحساسية وتسميات الاستبقاء بالإضافة إلى الإجراءات المتوفرة. راجع مرجع [نهج منع فقدان البيانات](dlp-policy-reference.md#data-loss-prevention-policy-reference).

## <a name="policy-design-process"></a>عملية تصميم النهج

1. أكمل الخطوات في:
    1. [التخطيط لمنع فقدان البيانات (DLP)](dlp-overview-plan-for-dlp.md#plan-for-data-loss-prevention-dlp) - من خلال العمل من خلال هذه المقالة، يمكنك:
        1. [تحديد المساهمين](dlp-overview-plan-for-dlp.md#identify-stakeholders)
        1. [وصف فئات المعلومات الحساسة لحمايتها](dlp-overview-plan-for-dlp.md#describe-the-categories-of-sensitive-information-to-protect)
        1. [تعيين الأهداف والاستراتيجية](dlp-overview-plan-for-dlp.md#set-goals-and-strategy)
        1. [تعريف خطة نشر النهج](dlp-overview-plan-for-dlp.md#policy-deployment)

1. تعرف [على مرجع نهج](dlp-policy-reference.md#data-loss-prevention-policy-reference) منع فقدان البيانات بحيث تفهم كل مكونات نهج DLP وكيفية تأثير كل منها على سلوك النهج.

1. تعرف على ما [تتضمنه قوالب نهج DLP](what-the-dlp-policy-templates-include.md#what-the-dlp-policy-templates-include).

1. تطوير بيان هدف النهج مع المساهمين الأساسيين. راجع المثال السابق في هذه المقالة.

1. حدد كيفية تناسب هذا النهج مع استراتيجية نهج DLP الشاملة.

> [!IMPORTANT]
> لا يمكن إعادة تسمية السياسات بمجرد إنشائها. إذا كان عليك إعادة تسمية نهج، يتعين عليك إنشاء نهج جديد بالاسم المطلوب و إيقاف النهج القديم. لذلك، قرر بنية التسمية التي ستستخدمها كل سياساتك الآن. 

6. تعيين العناصر في بيان هدف النهج إلى خيارات التكوين.

7. تحديد قالب النهج الذي ستبدأ منه أو المعرف مسبقا أو المخصص.

8. انتقل إلى القالب واجمع كل المعلومات المطلوبة قبل إنشاء النهج. من المرجح أن تجد أن هناك بعض نقاط التكوين التي لم يتم تناولها في بيان هدف النهج. هذا جيد. ارجع إلى المساهمين لكي تلب متطلبات أي نقاط تكوين مفقودة. 

9. توثيق تكوين كل إعدادات النهج ومراجعتها مع المساهمين. يمكنك إعادة استخدام بيان هدف النهج لتعيين نقاط التكوين، التي أصبحت الآن مكتملة بالكامل.

10. [أنشئ نهج](create-test-tune-dlp-policy.md#create-test-and-tune-a-dlp-policy) مسودة وارجع إلى خطة [نشر النهج](dlp-overview-plan-for-dlp.md#policy-deployment) .

<!--## Policy design examples

|Customer business needs description  | approach  |
|---------|---------|
|**Contoso Bank** is in a highly regulated industry and has  many different types of sensitive items in many different locations. </br> - knows which types of sensitive information are top priority. </br> - must minimize business disruption as policies are rolled out. </br> -  has IT resources and can hire experts to help plan, design deploy </br> - has a premier support contract with Microsoft| - Take the time to understand what regulations they must comply with and how they are going to comply. </br> -Take the time to understand the better together value of the Microsoft 365 Information Protection stack </br> - Develop sensitivity labeling scheme for prioritized items and apply </br> - Involve business process owners </br>- Design/code policies, deploy in test mode, train users </br>- repeat|
|**TailSpin Toys** doesn’t know what they have or where it is, and have little to no resource depth. They use Teams, OneDrive for Business and Exchange extensively.     |- Start with simple policies on the prioritized locations. </br>- Monitor what gets identified </br>- Apply sensitivity labels accordingly </br>- Refine policies, train users       |
|**Fabrikam** is a small startup and wants to protect its intellectual property, and must move quickly. They are willing to dedicate some resources, but can't afford to hire outside experts. </br>- Sensitive items are all in Microsoft 365 OneDrive for Business/SharePoint </br>- Adoption of OneDrive for Business and SharePoint is slow, employees/shadow IT use DropBox and Google drive to share/store items </br>- Employees value speed of work over data protection discipline </br>- Customer splurged and bought all 18 employees new Windows 10 devices     |- Take advantage of the default DLP policy in Teams </br>- Use restricted by default setting for SharePoint items </br>- Deploy policies that prevent external sharing </br>- Deploy policies to prioritized locations </br>- Deploy policies to Windows 10 devices </br>- Block uploads to non-OneDrive for Business cloud storage      |


1. For example:
    1. Identify your volume thresholds that your company deems to be low-risk (leakage tolerance), perhaps from unintentional sharing and is an opportunity to educate users and the threshold that is concerning or high-risk for your company that may need immediate attention.
    - example volume: “Low risk” for Contoso is 1 credit card number, perhaps it was a personal card that was shared carelessly
    - example volume: “High risk” for Contoso is 2 or more credit card numbers. It doesn’t feel like a common scenario that an employee would engage in accidentally



–   For each of the sensitive information types listed out, list out **who should have access to that data when it’s generated** and **what type of activities should be allowable with that data**


  <!--(Perhaps this is where we can provide some basic categories, templates, activities and actions that are supported by Microsoft. Some of these items are not discoverable until you are deeper within a policy creation flow. If we provide, we should time stamp it for “last updated” or “as of xx/xx/xxx”)
–   (Show table with parent-child relationships between categories, templates and sensitive info types that Microsoft supports) Should be gathered from GA Compliance environment-->

<!--


> [!TIP] The more locations you include ensures broader application of the policy and more consistent coverage. If you include locations that are mostly used for internal collaboration, the responsiveness of collaboration may be impacted.


- whether the protective actions you need are supported throught the associated location or if you need to compromise to extend coverage
    - also usefule for identifying the most restrictive actions available 
    - (we shouldn't mention here that the "content contains" condition is the primary staple for a DLP policy and should be utilized as a starting point for policy creation. The other workload-specific conditions can be ustilized as an extended or granular control of company's DLP policy. Useful for when "too much" data is being restricted and known sensitive data typically falls under certain conditions.)
    - (We can mention here that their quantitative goal such as "protect X% of data across all locations while maintaining x productivity" can be monitored throught alerts or reports. If protection is too high of working against their established goals, they can come back to policy and tweak their conditions/actions)
- Finally, you should have a union of what, hwo and when to be covered which will easily map to generating a live policy via Microsoft DLP. 
- 
5. At this stage you should asses how you should start this policy. ***LINK OUT TO DEPLOYING A POLICY COVERED IN THE PLANNING TOPIC TOO***
    - Test: your company is very large, conservative or the actions established are pretty restrictive
    - Test w/ notifications: same as above, but you get to test out investigation cadence or volume
    - Live: immediately start this policy in your environment. Useful for when data protection is needed immediately, such as a reactive policy creation, or if you're confident in your planning, or if the risk is low (liek audit actions, etc.)
    - keep it off:
-->

<!--## Policy Design Examples

Here are some examples of more detailed policy intent statement to configuration mappings.

*We are a national healthcare provider based in the U.S. We need to protect our patient’s personal information and prevent it from egressing outside of our company’s borders. We want to limit access to our patient’s personal information to only authorized personnel, like our physicians and billing department from our on-premises devices. We've determined that any single instance of any of each information type in any item is not a data risk, but it is a risk when two or more occur in a single item. We have a Microsoft 365 E5 subscription and want to protect all locations and first party apps that are available to us because we can’t afford to have any data leaks. If an event occurs or is prevented, we want to alert our compliance admin and educate our end-users where necessary.*

|Statement  |Configuration question answered and configuration mapping  |
|---------|---------|
| We are a national healthcare provider based in the U.S. We need to protect our patient’s personal information...|- **What to monitor**: All available item types, use the [U.S. Health Insurance Act (HIPAA)](what-the-dlp-policy-templates-include.md#us-health-insurance-act-hipaa) template. </br>- **Conditions for a match**: (preconfigured but editable) - item contains full names, physical addresses, driver's license number, U.S. SSN
| ...and prevent it from egressing outside of our company’s borders... |- **Actions to take**: Block anyone outside the organization from accessing items, block unintentional sharing by internal users with anyone outside the org.|
|...We want to limit access to our patient’s personal information to only authorized personnel, like our physicians and billing department from our on-premises devices...| - **Actions to take**: - Block access to items, block all activities (upload to cloud, copy to clipboard, copy to USB, copy to network share, access by restricted app, print, copy/move via Bluetooth, copy/move via remote desktop) from Windows devices.  </br> - **Where to monitor**: in all Microsoft 365 locations
| ...We've determined that any single instance of any of each information type in any item is not a data risk, but it is a risk when two or more occur in a single item....| - **Conditions for a match**: (preconfigured but editable) any single item contains more than one of these or any two or more of these:  Full Name, U.S. Social Security Number, Drug Enforcement Agency (DEA) number, International Classification of Diseases (ICD-9-CM), International Classification of Diseases (ICD-10-CM), Physical Address, U.S. driver's license number. For example, two instanced of Full Name or one instance of a U.S. Social Security Number along with one instance of Drug Enforcement Agency (DEA) number will trigger a match.

   , content is shared with people outside my organization  </br> - drives conversations to clarify the triggering threshold for detection like [confidence levels](sensitive-information-type-learn-about.md#more-on-confidence-levels), and [instance count](dlp-policy-reference.md#content-contains) (called leakage tolerance).|
|...that are stored in OneDrive/SharePoint and protect against that information being shared Teams chat and channel messages... |- **Where to monitor**:  [Location scoping](dlp-policy-reference.md#locations) by including or excluding OneDrive and SharePoint sites and Teams chat/channel accounts or distribution groups. |
|...and restrict everyone from sharing those items with unauthorized third parties."  | - **Actions to take**: [You add](dlp-policy-reference.md#actions) *Restrict access or encrypt the content in Microsoft 365 locations* </br> - drives conversation on what actions to take when a policy is triggered including protective actions like sharing restrictions, awareness actions like notifications and alerts, and user empowerment actions like allow user overrides of a blocking action |

-->


## <a name="see-also"></a>انظر أيضاً

- [التعرف على منع فقدان البيانات](dlp-learn-about-dlp.md#learn-about-data-loss-prevention)
- [التخطيط لمنع فقدان البيانات (DLP)](dlp-overview-plan-for-dlp.md#plan-for-data-loss-prevention-dlp)
- [مرجع نهج منع فقدان البيانات](dlp-policy-reference.md#data-loss-prevention-policy-reference)
- [مرجع تلميحات نهج منع فقدان البيانات](dlp-policy-tips-reference.md#data-loss-prevention-policy-tips-reference)
- [إنشاء نهج DLP واختباره وضبطه](create-test-tune-dlp-policy.md#create-test-and-tune-a-dlp-policy)