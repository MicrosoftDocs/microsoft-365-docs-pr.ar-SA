---
title: استخدام الكيانات المسماة في سياسات منع فقدان البيانات (معاينة)
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
ms.openlocfilehash: 9b3a8899ef4b64c682289e29df19648a00d4f048
ms.sourcegitcommit: 85ce5fd0698b6f00ea1ea189634588d00ea13508
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/06/2022
ms.locfileid: "64665151"
---
# <a name="use-named-entities-in-your-data-loss-prevention-policies-preview"></a>استخدام الكيانات المسماة في سياسات منع فقدان البيانات (معاينة)

> [!IMPORTANT]
> يتم طرح ميزة الكيانات المسماة وستظهر في المستأجر الخاص بك عندما تكون متوفرة لك. تحقق منها في مستكشف المحتوى وفي تدفق تأليف نهج منع فقدان البيانات (DLP). 

اقرأ من خلال [التعرف على الكيانات المسماة (معاينة)](named-entities-learn.md) قبل البدء في استخدامها.

## <a name="before-you-begin"></a>قبل البدء

### <a name="skusubscriptions-licensing"></a>ترخيص SKU/الاشتراكات

يجب أن يكون لديك أحد هذه الاشتراكات

- حماية البيانات والحوكمة
- التوافق في Microsoft 365 E5
- Office 365 E5
- Microsoft 365 E5

للحصول على تفاصيل الترخيص الكامل، راجع [وصف الخدمة](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#information-protection-data-classification-analytics-overview-content--activity-explorer).

### <a name="permissions"></a>الأذونات

يجب أن يكون للحساب الذي تستخدمه لإنشاء نهج منع فقدان البيانات (DLP) وتحريرها أذونات دور **DLP Compliance Management** . لمزيد من المعلومات، راجع [منح المستخدمين حق الوصول إلى مركز التوافق Office 365](../security/office-365-security/grant-access-to-the-security-and-compliance-center.md)


## <a name="supported-locations"></a>المواقع المدعومة

يمكنك استخدام وحدات SITs المسماة والنهج المحسنة للكشف عن العناصر الحساسة وحمايتها في هذه المواقع:

- مواقع SharePoint
- حسابات OneDrive
- Teams رسائل الدردشة والقنوات
- الأجهزة (Windows 10 أجهزة نقطة النهاية)

لا يتم دعم SITs للكيان المسمى والنهج المحسنة من أجل:


- المستودعات المحلية
- Power BI

## <a name="create-and-edit-enhanced-policies"></a>إنشاء نهج محسنة وتحريرها

لإنشاء نهج DLP أو تحريره، استخدم الإجراءات في [إنشاء نهج DLP واختباره وضبطه](create-test-tune-dlp-policy.md).

## <a name="workloads-and-services-that-support-named-entities"></a>أحمال العمل والخدمات التي تدعم الكيانات المسماة


- يدعم **Microsoft 3655 eDiscovery** استخدام الكيانات المسماة في خدمات الركيزة.
- **يدعم Microsoft Defender for Cloud Apps** استخدام الكيانات المسماة في نهج Defender for Cloud Apps.
- تدعم **Insider Risk Management** استخدام الكيانات المسماة في خدمات الركيزة.
<!--- **Communication Compliance** doesn't support the use of named entities in Exchange transport rules and data-at-rest.
- **Microsoft Information Governance** (MIG) doesn't support the use of named entities in Exchange transport rules and data-at-rest.-->
 
### <a name="unified-dlp"></a>DLP موحد

|حمل العمل/الخدمات  |دعم المعاينة العامة للكيانات المسماة  |
|---------|---------|
|تلميح نهج عملاء Office Win32    |غير معتمد  |
|تلميح نهج عملاء Office WAC    |دعم         |
|تلميح نهج OWA     |غير معتمد         |
|تلميح نهج Outlook     |غير معتمد |
|نقاط النهاية (أجهزة Windows 10)     |دعم  |
|قواعد النقل Exchange     |غير معتمد |
|OneDrive for Business البيانات الثابتة     |دعم         |
|بيانات SharePoint Online الثابتة     |دعم         |
|Teams البيانات الثابتة     |دعم         |
|بيانات رسائل البريد الإلكتروني الثابتة     |غير معتمد         |
|Microsoft Defender for Cloud Apps     |دعم         |

### <a name="autolabeling"></a>التسمية التلقائية

|حمل العمل/الخدمات |دعم المعاينة العامة للكيانات المسماة  |
|---------|---------|
|Office عملاء Win32 دون اتصال   |معتمد، يجب على المستخدم تحديد التسمية وتطبيقها يدويا |
|عملاء Office Win32 عبر الإنترنت عبر الإنترنت|مدعوم بنظام الثقة القديم |
|Outlook عبر الإنترنت   |مدعوم بنظام الثقة القديم  |
|عميل Office WAC     |دعم |
|OWA     |دعم |
|نقل Exchange     |غير معتمد |
|OneDrive for Business البيانات الثابتة     |دعم |
|بيانات SharePoint Online الثابتة|دعم|
|الماسح الضوئي ل Azure حماية البيانات (AIP)|غير معتمد|

## <a name="known-issues"></a>المشاكل المعروفة

|المساله  |اثر  |
|---------|---------|
|تلميحات نهج DLP (عملاء OWA، Outlook، Office Win32)     |   ستؤدي تلميحات النهج مع شرط الكيان إلى "عدم المطابقة"      |
| دعم اللغة الآسيوية لاسم الشخص (الصينية واليابانية والكورية)    | الكيانات المسماة المعتمدة لمجموعة الأحرف المستندة إلى اللاتينية فقط (أي أن kanji غير معتمد) لاسم الشخص        |
|المستودعات المحلية    | غير معتمد كعبء عمل|

<!--|Devices workload (Endpoint)     | Not supported as a workload – authoring policy with named entities will not be allowed        |-->

## <a name="for-further-information"></a>لمزيد من المعلومات
<!-- - [Sensitive information type entity definitions](sensitive-information-type-entity-definitions.md)-->
- [تعرف على الكيانات المسماة (معاينة).](named-entities-learn.md)
- [إنشاء نهج DLP واختباره وضبطه](create-test-tune-dlp-policy.md)
- [إنشاء نهج DLP من قالب](create-a-dlp-policy-from-a-template.md)
