---
title: استخدم الماسح الضوئي المحلي لمنع فقدان البيانات
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
description: تعرف على كيفية استخدام الماسح الضوئي المحلي لمنع فقدان البيانات لفحص البيانات الثابتة وتنفيذ إجراءات الحماية لمشاركات الملفات المحلية ومجلدات SharePoint المحلية ومكتبات المستندات.
ms.openlocfilehash: ae5ffce9e664ada6e7476bb02b40f4a5c279d441
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/06/2022
ms.locfileid: "66624168"
---
# <a name="use-the-data-loss-prevention-on-premises-scanner"></a>استخدام الماسح الضوئي المحلي لمنع فقدان البيانات

لمساعدتك في التعرف على تفادي فقدان البيانات في Microsoft Purview الميزات المحلية وكيفية إظهارها في نهج DLP، قمنا بتجميع بعض السيناريوهات لمتابعتها.

> [!IMPORTANT]
> سيناريوهات DLP المحلية هذه ليست الإجراءات الرسمية لإنشاء نهج DLP وضبطها. راجع المواضيع أدناه عندما تحتاج إلى العمل مع نهج DLP في المواقف العامة:
>
> - [التعرّف على تفادي فقدان البيانات](dlp-learn-about-dlp.md)
> - [بدء استخدام نهج DLP الافتراضي](get-started-with-the-default-dlp-policy.md)
> - [إنشاء نهج DLP من قالب](create-a-dlp-policy-from-a-template.md)
> - [إنشاء نهج DLP واختباره وضبطه](create-test-tune-dlp-policy.md)

### <a name="scenario-discover-files-matching-dlp-rules"></a>السيناريو: اكتشاف الملفات المطابقة لقواعد DLP

بيانات من أسطح الماسح الضوئي المحلي ل DLP في عدة مناطق

#### <a name="activity-explorer"></a>مستكشف النشاط

 يكشف Microsoft DLP محليا عن تطابقات قاعدة DLP ويبلغ عنها إلى [مستكشف النشاط](https://compliance.microsoft.com/dataclassification?viewid=activitiesexplorer).

#### <a name="microsoft-365-audit-log"></a>سجل تدقيق Microsoft 365

تتوفر تطابقات قاعدة DLP في واجهة مستخدم سجل التدقيق، راجع [البحث في سجل التدقيق في مدخل التوافق في Microsoft Purview](search-the-audit-log-in-security-and-compliance.md) أو يمكن الوصول إليه بواسطة [Search-UnifiedAuditLog](/powershell/module/exchange/search-unifiedauditlog) PowerShell.

#### <a name="aip"></a>الوكاله

تتوفر بيانات الاكتشاف في تقرير محلي بتنسيق csv المخزن ضمن:

**٪localappdata٪\Microsoft\MSIP\Scanner\Reports\DetailedReport_٪timestamp٪.csv التقرير**.

 ابحث عن الأعمدة التالية:

- وضع DLP
- حالة DLP
- تعليق DLP
- اسم قاعدة DLP
- إجراءات DLP
- مالك
- أذونات NTFS الحالية (SDDL)
- أذونات NTFS المطبقة (SDDL)
- نوع أذونات NTFS

### <a name="scenario-enforce-dlp-rule"></a>السيناريو: فرض قاعدة DLP

إذا كنت ترغب في فرض قواعد DLP على الملفات الممسوحة ضوئيا، يجب تمكين الإنفاذ على كل من مهمة فحص المحتوى في AIP وعلى مستوى النهج في DLP.

#### <a name="configure-dlp-to-enforce-policy-actions"></a>تكوين DLP لفرض إجراءات النهج

1. افتح [صفحة منع فقدان البيانات](https://compliance.microsoft.com/datalossprevention?viewid=policies) وحدد نهج DLP الذي يستهدف مستودعات المواقع المحلية التي قمت بتكوينها في AIP.
2. تحرير النهج.
3. في صفحة **الاختبار أو تشغيل النهج** ، حدد **"نعم"، وقم بتشغيلها على الفور**.

## <a name="see-also"></a>راجع أيضًا

- [التعرف على الماسح الضوئي المحلي ل DLP](dlp-on-premises-scanner-learn.md)
- [بدء استخدام الماسح الضوئي المحلي ل DLP](dlp-on-premises-scanner-get-started.md)
- [التعرّف على تفادي فقدان البيانات](dlp-learn-about-dlp.md)
- [إنشاء نهج DLP واختباره وضبطه](create-test-tune-dlp-policy.md)
- [بدء استخدام مستكشف النشاط](data-classification-activity-explorer.md)
