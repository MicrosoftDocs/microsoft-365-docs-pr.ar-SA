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
description: استخدم هذه الإجراءات للاستفادة من الكيانات المسماة في سياسات منع فقدان البيانات
ms.openlocfilehash: 5adb410689e597395f1b13152ed62af75fa111d6
ms.sourcegitcommit: 3fb76db6b34e24569417f4c8a41b99f46a780389
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/17/2022
ms.locfileid: "63574666"
---
# <a name="use-named-entities-in-your-data-loss-prevention-policies-preview"></a>استخدام الكيانات المسماة في سياسات منع فقدان البيانات (معاينة)

> [!IMPORTANT]
> يتم طرح ميزة الكيانات المسماة وستظهر في المستأجر عندما تكون متوفرة لك. تحقق من ذلك في مستكشف المحتوى وفي تدفق تأليف نهج منع فقدان البيانات (DLP). 

اقرأ من [خلال التعرف على الكيانات المسماة (معاينة)](named-entities-learn.md) قبل البدء في استخدامها.

## <a name="before-you-begin"></a>قبل البدء

### <a name="skusubscriptions-licensing"></a>ترخيص SKU/الاشتراكات

يجب أن يكون لديك أحد هذه الاشتراكات

- حماية المعلومات والحوكمة
- التوافق في Microsoft 365 E5
- Office 365 E5
- Microsoft 365 E5

للحصول على تفاصيل الترخيص الكاملة، راجع [وصف الخدمة](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#information-protection-data-classification-analytics-overview-content--activity-explorer).

### <a name="permissions"></a>الأذونات

يجب أن يكون للحساب الذي تستخدمه لإنشاء سياسات منع فقدان البيانات (DLP) وتحريرها أذونات **دور إدارة توافق DLP** . لمزيد من المعلومات، راجع منح [المستخدمين حق الوصول إلى Office 365 التوافق](../security/office-365-security/grant-access-to-the-security-and-compliance-center.md)


## <a name="supported-locations"></a>المواقع المعتمدة

يمكنك استخدام كيانات مسماة SITs ونهج محسنة للكشف عن العناصر الحساسة وحمايتها في هذه المواقع:

- SharePoint ويب
- OneDrive الحسابات
- Teams رسائل الدردشة والقناة
- الأجهزة (Windows 10 نقاط النهاية)

لا يتم دعم كيانات مسماة (SITs) ونهج محسنة ل:


- المستودعات المحليه
- Power BI

## <a name="create-and-edit-enhanced-policies"></a>إنشاء سياسات محسنة وتحريرها

لإنشاء نهج DLP أو تحريره، استخدم الإجراءات في [إنشاء نهج DLP واختباره وضبطه](create-test-tune-dlp-policy.md).

## <a name="workloads-and-services-that-support-named-entities"></a>أحمال العمل والخدمات التي تدعم الكيانات المسماة


- **يدعم Microsoft 3655 eDiscovery** استخدام الكيانات المسماة في خدمات الركيزة.
- **يدعم Microsoft Defender for Cloud Apps** استخدام الكيانات المسماة في سياسات Defender for Cloud Apps.
- **تدعم إدارة مخاطر Insider** استخدام الكيانات المسماة في خدمات الركيزة.
- **لا يدعم** توافق الاتصالات استخدام الكيانات المسماة في Exchange النقل وقواعد البيانات عند الراحة.
- **لا يدعم Microsoft Information Governance** (MIG) استخدام الكيانات المسماة في Exchange نقل البيانات والتكريس.
 
### <a name="unified-dlp"></a>DLP الموحد

|حمل العمل/الخدمات  |دعم المعاينة العامة للكيانات المسماة  |
|---------|---------|
|Office نهج عملاء Win32    |غير معتمد  |
|Office نهج عملاء WAC    |معتمد         |
|تلميح نهج OWA     |غير معتمد         |
|Outlook تلميح نهج     |غير معتمد |
|نقاط النهاية (Windows 10 الأجهزة)     |معتمد  |
|Exchange النقل     |غير معتمد |
|OneDrive for Business البيانات عند الراحة     |معتمد         |
|SharePoint البيانات على الإنترنت     |معتمد         |
|Teams البيانات عند الراحة     |معتمد         |
|بيانات رسائل البريد الإلكتروني     |غير معتمد         |
|Microsoft Defender لتطبيقات السحابة     |معتمد         |

### <a name="autolabeling"></a>التصفية التلقائية

|حمل العمل/الخدمات |دعم المعاينة العامة للكيانات المسماة  |
|---------|---------|
|Office عملاء Win32 دون اتصال   |مدعوم، يجب على المستخدم تحديد التسمية وتطبيقها يدويا |
|عملاء Office عبر الإنترنت في Win32 عبر الإنترنت|مدعوم مع نظام الثقة القديم |
|Outlook عبر الإنترنت   |مدعوم مع نظام الثقة القديم  |
|Office WAC     |معتمد |
|OWA     |معتمد |
|Exchange النقل     |غير معتمد |
|OneDrive for Business البيانات عند الراحة     |معتمد |
|SharePoint البيانات على الإنترنت|معتمد|
|ماسح ضوئي لحماية معلومات Azure (AIP)|غير معتمد|

## <a name="known-issues"></a>المشاكل المعروفة

|المشكلة  |التأثير  |
|---------|---------|
|تلميحات نهج DLP (OWA، Outlook، Office عملاء Win32)     |   ستنتج عن تلميحات النهج مع شرط الكيان "بلا تطابق"      |
| دعم اللغة الآسيوية لاسم الشخص (الصينية واليابانية والكورية)    | الكيانات المسماة المعتمدة لتعيين الأحرف المستندة إلى اللغة اللاتينية فقط (أي أن كانجي غير معتمدة) لاسم الشخص        |
|المستودعات المحليه    | غير معتمد كأحمال عمل|

<!--|Devices workload (Endpoint)     | Not supported as a workload – authoring policy with named entities will not be allowed        |-->

## <a name="for-further-information"></a>لمزيد من المعلومات
<!-- - [Sensitive information type entity definitions](sensitive-information-type-entity-definitions.md)-->
- [تعرف على الكيانات المسماة (معاينة)](named-entities-learn.md).
- [إنشاء نهج DLP واختباره وضبطه](create-test-tune-dlp-policy.md)
- [إنشاء نهج DLP من قالب](create-a-dlp-policy-from-a-template.md)
