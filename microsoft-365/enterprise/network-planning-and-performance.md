---
title: تخطيط الشبكة وضبط الأداء Microsoft 365
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 2/18/2022
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection: Strat_O365_Enterprise
f1.keywords:
- CSH
search.appverid:
- MET150
ms.assetid: e5f1228c-da3c-4654-bf16-d163daee8848
ms.custom:
- seo-marvel-apr2020
- Adm_O365
description: ستساعدك هذه المقالة على تخطيط متطلبات النطاق الترددي للشبكة Microsoft 365، وضبط الأداء وإصلاحه.
ms.openlocfilehash: 628d532a106ce9776443b252c863fa8bdc221b4b
ms.sourcegitcommit: bb493f12701f6d6ee7d5e64b541adb87470bc7bc
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 02/18/2022
ms.locfileid: "63572852"
---
# <a name="network-planning-and-performance-tuning-for-microsoft-365"></a>تخطيط الشبكة وضبط الأداء Microsoft 365
قبل النشر للمرة الأولى أو الترحيل إلى Microsoft 365، يمكنك استخدام المعلومات الواردة في هذه المواضيع لتقدير النطاق الترددي الذي تحتاج إليه، ثم لاختبار والتحقق من أن لديك ما يكفي من النطاق الترددي لنشر النطاق الترددي أو الترحيل إلى Microsoft 365. للحصول على نظرة عامة، راجع: [التخطيط للشبكة وا الترحيل Microsoft 365](network-and-migration-planning.md).
  
|الفئة |الوصف |الفئة |الوصف |
|:-----|:-----|:-----|:-----|
|**تخطيط الشبكة** <br/> ![الشبكة.](../media/5e9dcd06-601b-4b28-88dc-f524e7548794.png)           <br/> |هل تريد الاتصالات السريعة والصفحات التي يتم تحميلها بسرعة؟  <br/> اقرأ [الحصول على أفضل اتصال وأداء في Microsoft 365](https://aka.ms/o365perfprinciples).<br/>اقرأ [Microsoft 365 نظرة عامة حول اتصال الشبكة](microsoft-365-networking-overview.md) لفهم المفاهيم.<br/> |**قياس الشبكة** <br/> ![الحاسبة](../media/d690a132-4884-40eb-a918-526bb3dff3cc.png)           <br/> |اقرأ [Microsoft 365 تحسين الأداء باستخدام الأساسات](performance-tuning-using-baselines-and-history.md) ومحفوظات الأداء وخطط استكشاف الأخطاء وإصلاحها [Microsoft 365](performance-troubleshooting-plan.md).  <br/> استخدم هذه الأدوات [لتقييم شبكتك الموجودة](network-and-migration-planning.md#calculators).  <br/> |
|**Best practices** <br/> ![أفضل الممارسات.](../media/2a659a5c-1007-47d3-a6c6-a19e018ab29b.png)           <br/> |[أفضل الممارسات لتخطيط الشبكة وتحسين أداء الترحيل Microsoft 365](network-and-migration-planning.md#BestPractices). هل تريد بدء مساعدة المستخدمين على الفور؟ راجع [أفضل الممارسات لاستخدام Office 365 على شبكة بطيئة.](https://support.office.com/article/fd16c8d2-4799-4c39-8fd7-045f06640166)  <br/> [Microsoft 365 "](./microsoft-365-network-connectivity-principles.md)مبادئ اتصال الشبكة" على فهم الإرشادات الأخيرة لتحسين Microsoft 365 الشبكة بشكل آمن.  <br/> |**المرجع** <br/> ![دفتر اليومية أو دفتر اليومية](../media/56dff3c1-f605-48d8-811f-7d13ce639ecd.png)           <br/> |هل تريد الحصول على التفاصيل، مثل قائمة عناوين IP والمنافذ؟ راجع مرجع [تخطيط الشبكة Microsoft 365](network-and-migration-planning.md#NetReference).  <br/> |
|![راجع ملصق شبكة Microsoft Cloud ل Enterprise Architects.](../media/3094be9f-2407-4fa5-896d-aa66ef7b9bb9.png)           <br/> |للحصول على خطوات لتحسين شبكتك Microsoft 365 والخدمات السحابية الأخرى من Microsoft، راجع ملصق [شبكة سحابة Microsoft ل Enterprise Architects](../solutions/cloud-architecture-models.md).  <br/> |
   
## <a name="performance-tuning-and-troubleshooting-resources-for-microsoft-365"></a>تحسين الأداء والموارد التي تم استكشاف الأخطاء فيها وإصلاحها Microsoft 365
<a name="apptuning"> </a>

بعد نشر Microsoft 365، يمكنك تحسين الأداء باستخدام المواضيع في هذا القسم. إذا واجهت انخفاض في الأداء، يمكنك أيضا استخدام هذه المواضيع لا استكشاف المشاكل وإصلاحها.
  
 **[ضبط Office 365](tune-microsoft-365-performance.md)**: للحصول على معلومات حول استخدام ترجمة عنوان الشبكة مع Office 365، راجع دعم [NAT مع Office 365](nat-support-with-microsoft-365.md). أطلع أيضا على أهم 10 تلميحات لتحسين اتصال الشبكة Office 365 [وإصلاحها](/archive/blogs/onthewire/top-10-tips-for-optimising-troubleshooting-your-office-365-network-connectivity).
  
 **[ضبط Exchange Online](tune-exchange-online-performance.md)**: استخدم هذه المقالات لضبط Exchange Online الأداء.

 **[إعداد شبكة مؤسستك Microsoft Teams](/microsoftteams/prepare-network)**: استخدم هذه المقالات لتحسين شبكتك Teams.
  
 **[ضبط Skype for Business عبر الإنترنت](tune-skype-for-business-online-performance.md)**: استخدم هذه المقالات لضبط Skype for Business عبر الإنترنت.
  
 **[ضبط SharePoint عبر الإنترنت](tune-sharepoint-online-performance.md)**: استخدم هذه المقالات لضبط SharePoint عبر الإنترنت.
  
 **[ضبط Project Online الأداء](https://support.office.com/article/12ba0ebd-c616-42e5-b9b6-cad570e8409c)**: استخدم هذه المقالة لضبط Project Online الأداء
