---
title: استخدام Microsoft 365 فقدان البيانات
f1.keywords:
- CSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: ''
audience: ITPro
ms.topic: how-to
f1_keywords:
- ms.o365.cc.DLPLandingPage
ms.service: O365-seccomp
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
- m365solution-mip
- m365initiative-compliance
search.appverid:
- MET150
description: تعرف على كيفية استخدام Microsoft 365 فقدان البيانات في الماسح الضوئي في الموقع لمسح البيانات ضوئيا في أي مكان وتنفيذ إجراءات حماية لمشتركات الملفات والملفات SharePoint ومكتبات المستندات.
ms.openlocfilehash: d726bfccf7dff2e95e3ccf996544f1db26bf09a2
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 10/06/2021
ms.locfileid: "63572223"
---
# <a name="use-the-microsoft-365-data-loss-prevention-on-premises-scanner"></a>استخدام الماسح الضوئي Microsoft 365 فقدان البيانات

لمساعدتك على التعرف على ميزات DLP في الموقع وكيفية ظاهرها في سياسات DLP، قمنا بوضع بعض السيناريوهات معا لكي تتابعها.

> [!IMPORTANT]
> لا تكون سيناريوهات DLP الداخلية هذه هي الإجراءات الرسمية لإنشاء سياسات DLP وضبطها. راجع المواضيع أدناه عندما تحتاج إلى استخدام سياسات DLP في الحالات العامة:
>
> - [التعرف على منع فقدان البيانات](dlp-learn-about-dlp.md)
> - [بدء استخدام نهج DLP الافتراضي](get-started-with-the-default-dlp-policy.md)
> - [إنشاء نهج DLP من قالب](create-a-dlp-policy-from-a-template.md)
> - [إنشاء نهج DLP واختباره وضبطه](create-test-tune-dlp-policy.md)

### <a name="scenario-discover-files-matching-dlp-rules"></a>السيناريو: اكتشاف الملفات المطابقة لقواعد DLP

البيانات من أسطح الماسح الضوئي ل DLP في مناطق متعددة

#### <a name="activity-explorer"></a>مستكشف النشاط

 يكشف Microsoft DLP للقاعدة في الموقع عن تطابقات قواعد DLP ويبل يها إلى ["مستكشف النشاط](https://compliance.microsoft.com/dataclassification?viewid=activitiesexplorer)".

#### <a name="microsoft-365-audit-log"></a>Microsoft 365 التدقيق

تتوفر تطابقات قواعد DLP في واجهة مستخدم سجل التدقيق، راجع البحث في [](search-the-audit-log-in-security-and-compliance.md) سجل التدقيق في مركز التوافق أو يمكن الوصول إليه بواسطة [Search-UnifiedAuditLog](/powershell/module/exchange/search-unifiedauditlog) PowerShell.

#### <a name="aip"></a>AIP

تتوفر بيانات الاكتشاف في تقرير محلي بتنسيق csv يتم تخزينه ضمن:

**٪localappdata٪\Microsoft\MSIP\Scanner\Reports\DetailedReport_٪timestamp٪.csv report**.

 ابحث عن الأعمدة التالية:

- وضع DLP
- حالة DLP
- تعليق DLP
- اسم قاعدة DLP
- إجراءات DLP
- المالك
- أذونات NTFS الحالية (SDDL)
- أذونات NTFS المطبقة (SDDL)
- نوع أذونات NTFS

### <a name="scenario-enforce-dlp-rule"></a>السيناريو: فرض قاعدة DLP

إذا كنت تريد فرض قواعد DLP على الملفات الممسوحة ضوئيا، فيجب تمكين التنفيذ على كل من مهمة فحص المحتوى في AIP وعلى مستوى النهج في DLP.

#### <a name="configure-dlp-to-enforce-policy-actions"></a>تكوين DLP لفرض إجراءات النهج

1. افتح صفحة [منع فقدان](https://compliance.microsoft.com/datalossprevention?viewid=policies) البيانات وحدد نهج DLP الذي يستهدف مستودعات المواقع المحلي التي قمت بتكوينها في AIP.
2. تحرير النهج.
3. في صفحة **اختبار النهج أو تشغيلها** ، حدد **نعم، قم ب تشغيلها على الفور**.

## <a name="see-also"></a>راجع أيضًا

- [تعرف على ماسح DLP في الموقع](dlp-on-premises-scanner-learn.md)
- [بدء استخدام الماسح الضوئي ل DLP في الموقع](dlp-on-premises-scanner-get-started.md)
- [التعرف على منع فقدان البيانات](dlp-learn-about-dlp.md)
- [إنشاء نهج DLP واختباره وضبطه](create-test-tune-dlp-policy.md)
- [بدء استخدام "مستكشف النشاط"](data-classification-activity-explorer.md)
