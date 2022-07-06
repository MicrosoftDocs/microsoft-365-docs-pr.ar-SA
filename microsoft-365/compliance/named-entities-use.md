---
title: استخدام الكيانات المسماة في نهج DLP
f1.keywords:
- CSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: ''
audience: Admin
search.appverid: MET150
ms.topic: article
f1_keywords:
- ms.o365.cc.UnifiedDLPRuleContainsSensitiveInformation
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
description: استخدم هذه الإجراءات للاستفادة من الكيانات المسماة في نهج منع فقدان البيانات
ms.openlocfilehash: 0cdf544eddf873f3bbf761bd613641433dd2da6b
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/06/2022
ms.locfileid: "66623684"
---
# <a name="use-named-entities-in-your-data-loss-prevention-policies"></a>استخدام الكيانات المسماة في نهج تفادي فقدان البيانات

اقرأ [من خلال التعرف على الكيانات المسماة](named-entities-learn.md) قبل البدء في استخدامها.

## <a name="before-you-begin"></a>قبل البدء

### <a name="skusubscriptions-licensing"></a>ترخيص SKU/الاشتراكات

للحصول على تفاصيل الترخيص الكامل، راجع [وصف الخدمة](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#information-protection-data-classification-analytics-overview-content--activity-explorer).

### <a name="permissions"></a>الأذونات

يجب أن يكون للحساب الذي تستخدمه لإنشاء نهج منع فقدان البيانات (DLP) وتحريرها أذونات دور **DLP Compliance Management** . لمزيد من المعلومات، راجع [منح المستخدمين حق الوصول إلى مركز التوافق Office 365](../security/office-365-security/grant-access-to-the-security-and-compliance-center.md)


## <a name="supported-locations"></a>المواقع المدعومة

يمكنك استخدام وحدات SITs المسماة والنهج المحسنة للكشف عن العناصر الحساسة وحمايتها في هذه المواقع:

- مواقع SharePoint
- حسابات OneDrive
- دردشة Teams ورسائل القناة
- الأجهزة (Windows 10 و11 جهاز نقطة نهاية)
- علب بريد Exchange
- Microsoft Defender for Cloud Apps

لا يتم دعم SITs للكيان المسمى والنهج المحسنة من أجل:

- المستودعات المحلية
- Power BI

## <a name="create-and-edit-enhanced-policies"></a>إنشاء نهج محسنة وتحريرها

لإنشاء نهج DLP أو تحريره، استخدم الإجراءات في [إنشاء نهج DLP واختباره وضبطه](create-test-tune-dlp-policy.md).

## <a name="workloads-and-services-that-support-named-entities"></a>أحمال العمل والخدمات التي تدعم الكيانات المسماة

- يدعم **Microsoft 365 eDiscovery** استخدام الكيانات المسماة في خدمات الركيزة.
- يدعم **Microsoft Defender for Cloud Apps** استخدام الكيانات المسماة في نهج Defender for Cloud Apps في مدخل تطبيقات Defender for Cloud.
- تدعم **Insider Risk Management** استخدام الكيانات المسماة في خدمات الركيزة.
- تدعم **إدارة السجلات** استخدام الكيانات المسماة.
- تدعم **أنواع المعلومات الحساسة لمطابقة البيانات الدقيقة** استخدام الكيانات المسماة.
<!--- **Communication Compliance** doesn't support the use of named entities in Exchange transport rules and data-at-rest.
- **Microsoft Information Governance** (MIG) doesn't support the use of named entities in Exchange transport rules and data-at-rest.-->
 
### <a name="unified-dlp"></a>DLP موحد

|حمل العمل/الخدمات  |دعم الكيانات المسماة  |
|---------|---------|
|تلميح نهج عملاء Office Win32    |غير معتمد  |
|تلميح نهج عملاء Office WAC    |دعم         |
|تلميح نهج OWA     |غير معتمد         |
|تلميح نهج Outlook     |غير معتمد |
|نقاط النهاية (Windows 10 و11 جهازا)     |دعم  |
|قواعد Exchange Transport     |دعم |
|OneDrive for Business البيانات الثابتة     |دعم         |
|بيانات SharePoint Online الثابتة     |دعم         |
|بيانات Teams الثابتة     |دعم         |
|بيانات رسائل البريد الإلكتروني الثابتة     |مدعومة للمستأجرين باستخدام خطة خدمة الخصوصية         |
|Microsoft Defender for Cloud Apps     |دعم         |

### <a name="autolabeling"></a>التسمية التلقائية

|حمل العمل/الخدمات |دعم الكيانات المسماة  |
|---------|---------|
|عملاء Office Win32 دون اتصال   |معتمد، يجب على المستخدم تحديد التسمية وتطبيقها يدويا |
|عملاء Office Win32 عبر الإنترنت عبر الإنترنت|مدعوم بنظام الثقة القديم |
|Outlook عبر الإنترنت   |مدعوم بنظام الثقة القديم  |
|عميل Office WAC     |دعم |
|OWA     |دعم |
|نقل Exchange     |دعم |
|OneDrive for Business البيانات الثابتة     |دعم |
|بيانات SharePoint Online الثابتة|دعم|
|الماسح الضوئي ل Azure حماية البيانات (AIP)|غير معتمد|

## <a name="known-issues"></a>المشاكل المعروفة

|مشكلة  |اثر  |
|---------|---------|
|تلميحات نهج DLP (عملاء OWA وOutlook وOffice Win32)     |   ستؤدي تلميحات النهج مع شرط الكيان إلى "عدم المطابقة"      |
| دعم اللغة الآسيوية لاسم الشخص (الصينية واليابانية والكورية)    | الكيانات المسماة المعتمدة لمجموعة الأحرف المستندة إلى اللاتينية فقط (أي أن kanji غير معتمد) لاسم الشخص        |
|المستودعات المحلية    | غير معتمد كعبء عمل|
|Power BI (معاينة) | غير معتمد

<!--|Devices workload (Endpoint)     | Not supported as a workload – authoring policy with named entities will not be allowed        |-->

## <a name="best-practices-for-using-named-entity-sits"></a>أفضل الممارسات لاستخدام كيانات SITs المسماة

فيما يلي بعض الممارسات التي يمكنك استخدامها عند إنشاء نهج يستخدم كيانا مسمى SIT أو تحريره.

- استخدم عدد المثيلات المنخفضة (من ثلاثة إلى خمسة) عندما تبحث عن البيانات الموجودة في جدول بيانات والكلمة الأساسية المطلوبة من قبل SIT لتلك البيانات موجودة فقط في رأس العمود. على سبيل المثال، لنفترض أنك تبحث عن أرقام الضمان الاجتماعي الأمريكية، وتحدث الكلمة الأساسية `Social Security Number` فقط في رأس العمود. نظرا إلى أن القيم (الدليل القاطع) موجودة في الخلايا أدناه، فمن المحتمل أن تكون المثيلات القليلة الأولى فقط قريبة بما يكفي من الكلمة الأساسية التي سيتم اكتشافها.  

- إذا كنت تستخدم كيانا مسمى SIT، مثل "كافة الأسماء الكاملة"، للمساعدة في العثور على أرقام الضمان الاجتماعي الأمريكية، فاستخدم عدد أكبر من المثيلات مثل 10 أو 50. ثم عندما يتم الكشف عن أسماء الأشخاص وSSNs معا، فمن المرجح أن تحصل على إيجابيات حقيقية.

- يمكنك استخدام [محاكاة التسمية التلقائية](apply-sensitivity-label-automatically.md#learn-about-simulation-mode) لاختبار دقة وحدات SITs المسماة. قم بتشغيل محاكاة باستخدام وحدة مسماة SIT لمعرفة العناصر التي تتطابق مع النهج. باستخدام هذه المعلومات، يمكنك ضبط الدقة عن طريق ضبط عدد المثيلات ومستويات الثقة في النهج المخصصة أو شروط القالب المحسنة. يمكنك تكرار عمليات المحاكاة حتى تكون الدقة هي المكان الذي تريدها فيه، قبل نشر نهج DLP أو سياسة التسمية التلقائية التي تحتوي على كيانات مسماة في الإنتاج. فيما يلي نظرة عامة على التدفق:

1. حدد SIT أو مجموعة من SITs التي تريد اختبارها في وضع المحاكاة، إما مخصصة أو منسوخة ومحررة.
1. حدد وصف الحساسية أو أنشئه ليتم تطبيقه عندما يعثر نهج التسمية التلقائية على تطابق في حسابات Exchange أو SharePoint أو OneDrive.
1. إنشاء نهج وصف تلقائي للحساسية يستخدم SIT من الخطوة 1 ومع نفس الشروط والاستثناءات التي سيتم استخدامها في نهج DLP الخاص بك
1. تشغيل محاكاة النهج
1. عرض النتائج
1. ضبط SIT أو النهج وعدد المثيلات ومستويات الثقة لتقليل الإيجابيات الخاطئة.
1. كرر حتى تحصل على نتائج الدقة التي تريدها.


## <a name="for-further-information"></a>لمزيد من المعلومات
- [تعريفات كيان نوع المعلومات الحساسة](sensitive-information-type-entity-definitions.md)
- [تعرف على الكيانات المسماة](named-entities-learn.md).
- [إنشاء نهج DLP واختباره وضبطه](create-test-tune-dlp-policy.md)
- [إنشاء نهج DLP من قالب](create-a-dlp-policy-from-a-template.md)
