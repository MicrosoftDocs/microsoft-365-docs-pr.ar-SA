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
ms.openlocfilehash: 2d7c370ab34eea2c708769674495a2c51f1a3fcf
ms.sourcegitcommit: ac0ae5c2888e2b323e36bad041a4abef196c9c96
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/12/2022
ms.locfileid: "64782028"
---
# <a name="design-a-data-loss-prevention-policy"></a>تصميم نهج منع فقدان البيانات

سيؤدي تخصيص الوقت اللازم لتصميم نهج قبل تنفيذه إلى الحصول على النتائج المرجوة بشكل أسرع، وبمشكلات أقل غير مقصودة، مقارنة بإنشائه ثم ضبطه عن طريق التجربة والخطأ فقط. سيساعدك أيضا توثيق تصميمات النهج في الاتصالات ومراجعات النهج واستكشاف الأخطاء وإصلاحها والمزيد من الضبط.

<!--, but excessive tuning to get the intended results can be time consuming.

 if you have to do a lot of tuning to get a policy to yield the intended results can be time consuming .-->

إذا كنت جديدا على Microsoft 365 DLP، فمن المفيد العمل من خلال هذه المقالات قبل البدء في تصميم نهج:

- [تعرف على منع فقدان البيانات](dlp-learn-about-dlp.md#learn-about-data-loss-prevention) - تعرفك هذه المقالة على ضابط منع فقدان البيانات وتنفيذ Microsoft ل DLP
- [التخطيط لمنع فقدان البيانات (DLP)](dlp-overview-plan-for-dlp.md#plan-for-data-loss-prevention-dlp) - من خلال العمل من خلال هذه المقالة سوف:
  - [تحديد أصحاب المصلحة](dlp-overview-plan-for-dlp.md#identify-stakeholders)
  - [وصف فئات المعلومات الحساسة التي يجب حمايتها](dlp-overview-plan-for-dlp.md#describe-the-categories-of-sensitive-information-to-protect)
  - [تعيين الأهداف والاستراتيجية](dlp-overview-plan-for-dlp.md#set-goals-and-strategy)
- [مرجع نهج تفادي فقدان البيانات](dlp-policy-reference.md#data-loss-prevention-policy-reference) - تقدم هذه المقالة جميع مكونات نهج DLP وكيف يؤثر كل منها على سلوك النهج

## <a name="policy-design-overview"></a>نظرة عامة على تصميم النهج

يتعلق [تصميم نهج](#policy-design-process) في الغالب [بتحديد احتياجات عملك بوضوح، وتوثيقها في بيان هدف النهج](#define-intent-for-the-policy)، ثم [تعيين تلك الاحتياجات لتكوين النهج](#map-business-needs-to-policy-configuration). ستستخدم القرارات التي اتخذتها في مرحلة التخطيط لإعلام بعض قرارات تصميم النهج.

### <a name="define-intent-for-the-policy"></a>تحديد الهدف للنهج

يجب أن تكون قادرا على تلخيص هدف العمل لكل نهج لديك في بيان واحد. سيؤدي تطوير هذا البيان إلى دفع المحادثات في مؤسستك، وعند الانتهاء من صياغة هذا البيان بشكل كامل، يربط هذا البيان مباشرة السياسة لغرض عمل ويوفر مخططا لتصميم النهج. ستساعدك الخطوات الواردة في مقالة [خطة منع فقدان البيانات (DLP)](dlp-overview-plan-for-dlp.md#overview-of-planning-process) على البدء في بيان هدف النهج الخاص بك.

تذكر من [نظرة عامة على تكوين نهج DLP](dlp-learn-about-dlp.md#dlp-policy-configuration-overview) أن جميع نهج DLP تتطلب منك:

- اختر ما تريد مراقبته
- اختر المكان الذي تريد مراقبته
- اختيار الشروط التي يجب مطابقتها لتطبيق نهج على عنصر
- اختر الإجراء الذي يجب اتخاذه عند استيفاء شروط النهج

على سبيل المثال، إليك مسودة أولى وهمية لبيان الهدف الذي يوفر إجابات على جميع الأسئلة الأربعة:

*"نحن مؤسسة مقرها الولايات المتحدة، ونحتاج إلى الكشف عن المستندات Office التي تحتوي على معلومات الرعاية الصحية الحساسة التي تغطيها HIPPA والمخزنة في OneDrive/SharePoint والحماية من تلك المعلومات التي تتم مشاركتها في Teams رسائل الدردشة والقنوات وتقييد الجميع من مشاركتها مع جهات خارجية غير مصرح بها".*

أثناء تطوير تصميم نهج، من المحتمل أن تقوم بتعديل العبارة وتوسيعها.

### <a name="map-business-needs-to-policy-configuration"></a>تخطيط احتياجات الأعمال لتكوين النهج

دعونا نقسم مثال بيان المسودة إلى أسفل ونضبطه إلى نقاط تكوين نهج DLP.

|بيان|تمت الإجابة عن سؤال التكوين وتعيين التكوين|
|---|---|
|"نحن مؤسسة مقرها الولايات المتحدة، ونحتاج إلى الكشف عن Office المستندات التي تحتوي على معلومات الرعاية الصحية الحساسة التي تغطيها HIPPA...|- **ما يجب مراقبته**: Office المستندات، استخدم قالب [قانون التأمين الصحي (HIPAA) في الولايات المتحدة](what-the-dlp-policy-templates-include.md#us-health-insurance-act-hipaa) </br>- **شروط المطابقة**: (تم تكوينه مسبقا ولكن قابل للتحرير) - يحتوي العنصر على رقم SSN وCED Enforcement Agency (DEA) للولايات المتحدة، والتصنيف الدولي للأدوية (ICD-9-CM)، والتصنيف الدولي الأمراض (ICD-10-CM)، تتم مشاركة المحتوى مع أشخاص من خارج مؤسستي  </br> - يدفع المحادثات لتوضيح حد التشغيل للكشف مثل [مستويات الثقة](sensitive-information-type-learn-about.md#more-on-confidence-levels)، [وعدد المثيلات](dlp-policy-reference.md#content-contains) (يسمى التسامح مع التسرب).|
|... التي يتم تخزينها في OneDrive/SharePoint والحماية من تلك المعلومات التي تتم مشاركتها Teams رسائل الدردشة والقنوات...|- **مكان المراقبة**: [تحديد نطاق الموقع](dlp-policy-reference.md#locations) عن طريق تضمين مواقع OneDrive ومواقع SharePoint أو استبعادها Teams حسابات الدردشة/القناة أو مجموعات التوزيع.|
|... وتقييد الجميع من مشاركة هذه العناصر مع جهات خارجية غير مصرح بها"."|- **الإجراءات التي يجب اتخاذها**: [يمكنك إضافة](dlp-policy-reference.md#actions) *تقييد الوصول أو تشفير المحتوى في مواقع Microsoft 365* </br> - يدفع المحادثة حول الإجراءات التي يجب اتخاذها عند تشغيل نهج، بما في ذلك إجراءات الحماية مثل قيود المشاركة، وإجراءات الوعي مثل الإعلامات والتنبيهات، وإجراءات تمكين المستخدم مثل السماح لتجاوز المستخدم لإجراء حظر|

لا يغطي هذا المثال جميع نقاط التكوين لنهج DLP، بل يجب توسيعه. ولكن يجب أن تحصل على التفكير في الاتجاه الصحيح في أثناء تطوير بيانات هدف نهج DLP الخاصة بك.

> [!IMPORTANT]
> ضع في اعتبارك أن الموقع (المواقع) التي تختارها تؤثر على ما إذا كان يمكنك استخدام أنواع المعلومات الحساسة وتسميات الحساسية وتسميات الاستبقاء بالإضافة إلى الإجراءات المتوفرة. راجع [مرجع نهج تفادي فقدان البيانات](dlp-policy-reference.md#data-loss-prevention-policy-reference).

## <a name="policy-design-process"></a>عملية تصميم النهج

1. أكمل الخطوات الواردة في [خطة منع فقدان البيانات (DLP)](dlp-overview-plan-for-dlp.md#plan-for-data-loss-prevention-dlp) - من خلال العمل من خلال هذه المقالة، سوف تتمكن مما يلي:
   1. [تحديد المساهمين](dlp-overview-plan-for-dlp.md#identify-stakeholders)
   1. [وصف فئات المعلومات الحساسة التي يجب حمايتها](dlp-overview-plan-for-dlp.md#describe-the-categories-of-sensitive-information-to-protect)
   1. [تعيين الأهداف والاستراتيجية](dlp-overview-plan-for-dlp.md#set-goals-and-strategy)
   1. [تحديد خطة نشر النهج](dlp-overview-plan-for-dlp.md#policy-deployment)

2. تعرف على [مرجع نهج تفادي فقدان البيانات](dlp-policy-reference.md#data-loss-prevention-policy-reference) بحيث تفهم جميع مكونات نهج DLP وكيف يؤثر كل منها على سلوك النهج.

3. تعرف على [ما تتضمنه قوالب نهج DLP](what-the-dlp-policy-templates-include.md#what-the-dlp-policy-templates-include).

4. قم بتطوير بيان هدف النهج الخاص بك مع المساهمين الرئيسيين. راجع المثال السابق في هذه المقالة.

5. حدد كيفية ملاءمة هذا النهج لاستراتيجية نهج DLP الشاملة.

   > [!IMPORTANT]
   > لا يمكن إعادة تسمية النهج بمجرد إنشائها. إذا كان عليك إعادة تسمية نهج، فسيتعين عليك إنشاء نهج جديد بالاسم المطلوب وتقاعد النهج القديم. لذا حدد بنية التسمية التي ستستخدمها جميع نهجك الآن.

6. تعيين العناصر في بيان هدف النهج إلى خيارات التكوين.

7. حدد قالب النهج الذي ستبدأ منه، معرفا مسبقا أو مخصصا.

8. انتقل إلى القالب وقم بتجميع كافة المعلومات المطلوبة قبل إنشاء النهج. من المحتمل أن تجد أن هناك بعض نقاط التكوين التي لا تغطيها بيان هدف النهج الخاص بك. هذا جيد. ارجع إلى المساهمين لحل متطلبات أي نقاط تكوين مفقودة.

9. توثيق تكوين جميع إعدادات النهج ومراجعتها مع المساهمين. يمكنك إعادة استخدام تعيين بيان هدف النهج الخاص بك لنقاط التكوين، والتي تم دمجها الآن بالكامل.

10. [إنشاء مسودة](create-test-tune-dlp-policy.md#create-test-and-tune-a-dlp-policy) نهج والرجوع إلى خطة [نشر النهج](dlp-overview-plan-for-dlp.md#policy-deployment) .

<!--## Policy design examples

|Customer business needs description|approach|
|---|---|
|**Contoso Bank** is in a highly regulated industry and has  many different types of sensitive items in many different locations. </br> - knows which types of sensitive information are top priority. </br> - must minimize business disruption as policies are rolled out. </br> -  has IT resources and can hire experts to help plan, design deploy </br> - has a premier support contract with Microsoft|- Take the time to understand what regulations they must comply with and how they are going to comply. </br> -Take the time to understand the better together value of the Microsoft 365 Information Protection stack </br> - Develop sensitivity labeling scheme for prioritized items and apply </br> - Involve business process owners </br>- Design/code policies, deploy in test mode, train users </br>- repeat|
|**TailSpin Toys** doesn’t know what they have or where it is, and have little to no resource depth. They use Teams, OneDrive for Business and Exchange extensively.|- Start with simple policies on the prioritized locations. </br>- Monitor what gets identified </br>- Apply sensitivity labels accordingly </br>- Refine policies, train users|
|**Fabrikam** is a small startup and wants to protect its intellectual property, and must move quickly. They are willing to dedicate some resources, but can't afford to hire outside experts. </br>- Sensitive items are all in Microsoft 365 OneDrive for Business/SharePoint </br>- Adoption of OneDrive for Business and SharePoint is slow, employees/shadow IT use DropBox and Google drive to share/store items </br>- Employees value speed of work over data protection discipline </br>- Customer splurged and bought all 18 employees new Windows 10 devices|- Take advantage of the default DLP policy in Teams </br>- Use restricted by default setting for SharePoint items </br>- Deploy policies that prevent external sharing </br>- Deploy policies to prioritized locations </br>- Deploy policies to Windows 10 devices </br>- Block uploads to non-OneDrive for Business cloud storage|

1. For example:
    1. Identify your volume thresholds that your company deems to be low-risk (leakage tolerance), perhaps from unintentional sharing and is an opportunity to educate users and the threshold that is concerning or high-risk for your company that may need immediate attention.
    - example volume: “Low risk” for Contoso is 1 credit card number, perhaps it was a personal card that was shared carelessly
    - example volume: “High risk” for Contoso is 2 or more credit card numbers. It doesn’t feel like a common scenario that an employee would engage in accidentally

– For each of the sensitive information types listed out, list out **who should have access to that data when it’s generated** and **what type of activities should be allowable with that data**

  <!--(Perhaps this is where we can provide some basic categories, templates, activities and actions that are supported by Microsoft. Some of these items are not discoverable until you are deeper within a policy creation flow. If we provide, we should time stamp it for “last updated” or “as of xx/xx/xxx”)
– (Show table with parent-child relationships between categories, templates and sensitive info types that Microsoft supports) Should be gathered from GA Compliance environment-->

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

|Statement|Configuration question answered and configuration mapping|
|---|---|
|We are a national healthcare provider based in the U.S. We need to protect our patient’s personal information...|- **What to monitor**: All available item types, use the [U.S. Health Insurance Act (HIPAA)](what-the-dlp-policy-templates-include.md#us-health-insurance-act-hipaa) template. </br>- **Conditions for a match**: (preconfigured but editable) - item contains full names, physical addresses, driver's license number, U.S. SSN
|...and prevent it from egressing outside of our company’s borders...|- **Actions to take**: Block anyone outside the organization from accessing items, block unintentional sharing by internal users with anyone outside the org.|
|...We want to limit access to our patient’s personal information to only authorized personnel, like our physicians and billing department from our on-premises devices...|- **Actions to take**: - Block access to items, block all activities (upload to cloud, copy to clipboard, copy to USB, copy to network share, access by restricted app, print, copy/move via Bluetooth, copy/move via remote desktop) from Windows devices.  </br> - **Where to monitor**: in all Microsoft 365 locations
|...We've determined that any single instance of any of each information type in any item is not a data risk, but it is a risk when two or more occur in a single item....|- **Conditions for a match**: (preconfigured but editable) any single item contains more than one of these or any two or more of these:  Full Name, U.S. Social Security Number, Drug Enforcement Agency (DEA) number, International Classification of Diseases (ICD-9-CM), International Classification of Diseases (ICD-10-CM), Physical Address, U.S. driver's license number. For example, two instanced of Full Name or one instance of a U.S. Social Security Number along with one instance of Drug Enforcement Agency (DEA) number will trigger a match.

   , content is shared with people outside my organization  </br> - drives conversations to clarify the triggering threshold for detection like [confidence levels](sensitive-information-type-learn-about.md#more-on-confidence-levels), and [instance count](dlp-policy-reference.md#content-contains) (called leakage tolerance).|
|...that are stored in OneDrive/SharePoint and protect against that information being shared Teams chat and channel messages...|- **Where to monitor**:  [Location scoping](dlp-policy-reference.md#locations) by including or excluding OneDrive and SharePoint sites and Teams chat/channel accounts or distribution groups.|
|...and restrict everyone from sharing those items with unauthorized third parties."|- **Actions to take**: [You add](dlp-policy-reference.md#actions) *Restrict access or encrypt the content in Microsoft 365 locations* </br> - drives conversation on what actions to take when a policy is triggered including protective actions like sharing restrictions, awareness actions like notifications and alerts, and user empowerment actions like allow user overrides of a blocking action|

-->

## <a name="see-also"></a>انظر أيضاً

- [التعرّف على تفادي فقدان البيانات](dlp-learn-about-dlp.md#learn-about-data-loss-prevention)
- [التخطيط لمنع فقدان البيانات (DLP)](dlp-overview-plan-for-dlp.md#plan-for-data-loss-prevention-dlp)
- [مرجع نهج تفادي فقدان البيانات](dlp-policy-reference.md#data-loss-prevention-policy-reference)
- [تلميحات حول نهج تفادي فقد البيانات (DLP)](dlp-policy-tips-reference.md#data-loss-prevention-policy-tips-reference)
- [إنشاء نهج DLP واختباره وضبطه](create-test-tune-dlp-policy.md#create-test-and-tune-a-dlp-policy)