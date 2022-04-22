---
title: نظرة عامة على صفحة إدارة المخاطر في Microsoft 365 Lighthouse
f1.keywords: NOCSH
ms.author: sharik
author: SKjerland
manager: scotv
audience: Admin
ms.topic: article
ms.prod: microsoft-365-lighthouse
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
ms.custom:
- AdminSurgePortfolio
- M365-Lighthouse
search.appverid: MET150
description: بالنسبة لموفري الخدمات المدارة (MSPs) الذين يستخدمون Microsoft 365 Lighthouse، تعرف على صفحة إدارة المخاطر.
ms.openlocfilehash: fea297845446bd8cbb14c81851afb5d51ce33717
ms.sourcegitcommit: 339d2c2ffea06726f69429f73c1113c649f37b18
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/21/2022
ms.locfileid: "65023338"
---
# <a name="overview-of-the-threat-management-page-in-microsoft-365-lighthouse"></a>نظرة عامة على صفحة إدارة المخاطر في Microsoft 365 Lighthouse 

**ينطبق على:**

- Windows 10

يحمي برنامج الحماية من الفيروسات من Microsoft Defender المستأجرين والمستخدمين والأجهزة من تهديدات البرامج بما في ذلك الفيروسات والبرامج الضارة وبرامج التجسس. إنها حماية قوية ومستمرة مضمنة في Windows 10 ومضمنة مع Microsoft 365 Business Premium وMicrosoft365E3&nbsp;&nbsp;.  
  
للوصول إلى صفحة إدارة المخاطر في Microsoft 365 Lighthouse، حدد **إدارة التهديدات** في جزء التنقل الأيمن لعرض وضع أمان مستأجري العملاء ضد التهديدات. سترى المستأجرين والمستخدمين والأجهزة التي تتطلب انتباهك وتوصياتك التي ستساعدك على تقليل المخاطر.  
  
## <a name="overview-tab"></a>علامة التبويب "نظرة عامة"  
  
في علامة التبويب "نظرة عامة" في صفحة إدارة المخاطر، يمكنك مراقبة حالة الحماية من الفيروسات عبر جميع المستأجرين لتحديد المناطق التي تحتاج إلى الانتباه.

:::image type="content" source="../media/m365-lighthouse-threat-management-page-overview/threatmanagement-overview-tab.png" alt-text="لقطة شاشة لعلامة التبويب &quot;Overview&quot;.":::

## <a name="threats-tab"></a>علامة التبويب "تهديدات"

في علامة التبويب «Threats» في صفحة «Threat management»، يمكنك رؤية التهديدات النشطة والمخففة والمحلة والمتاحة عبر جميع المستأجرين. يمكنك أيضا معالجة التهديدات المتعددة في نفس الوقت عبر جميع المستأجرين من خلال تصفية كل تهديد والتعمق فيه لمعرفة الأجهزة أو المستخدمين أو المستأجرين المتأثرين.

:::image type="content" source="../media/m365-lighthouse-threat-management-page-overview/threatmanagement-threats-tab.png" alt-text="لقطة شاشة لصفحة الأساس الافتراضي.":::
  
يمكنك تصفية التهديدات عن طريق:

- حالة التهديد
- خطورة التهديد
- نوع التهديد
- نطاق التاريخ

يسرد الجدول التالي حالات التهديد المختلفة وتعريفها:<br><br>

| حالة التهديد | تعريف |
|---|---|
| النشطه | التهديد نشط على الجهاز. |
| لا توجد حالة | حالة التهديد غير متوفرة. قم بتشغيل فحص كامل على الجهاز برنامج الحماية من الفيروسات من Microsoft Defender إعادة تحديد التهديد. |
| فشل الإجراء | الجهاز ليس في خطر. فشل إجراء ولكن تم إيقاف تهديد محتمل وهو غير نشط على الجهاز. تشغيل فحص كامل على الجهاز. |
| الخطوات اليدوية المطلوبة | تم إيقاف التهديد ولكنه يتطلب خطوة يدوية لإكمالها، مثل الفحص الكامل أو إعادة تشغيل الجهاز. |
| الفحص الكامل مطلوب | يلزم إجراء فحص كامل للجهاز. |
| إعادة التشغيل مطلوبة | يلزم إعادة تشغيل الجهاز. |
| معالجة مع حالات الفشل غير الحرجة | لقد تمت معالجة التهديد ولا توجد حاجة إلى اتخاذ إجراءات أخرى. |
| الحجر الصحي | تم عزل التهديد. لا توجد حاجة إلى مزيد من الإجراءات. |
| ازاله | تمت إزالة التهديد بنجاح من الجهاز. لا توجد حاجة إلى مزيد من الإجراءات. |
| تنظيف | لقد قامت برنامج الحماية من الفيروسات من Microsoft Defender باسترداد الملفات ومعالجتها. لا توجد حاجة إلى مزيد من الإجراءات. |
| يسمح | يسمح للمسؤول بالبقاء على الجهاز. | 

## <a name="antivirus-protection-tab"></a>علامة تبويب الحماية من الفيروسات

تعرض علامة تبويب الحماية من الفيروسات في صفحة إدارة التهديدات الأجهزة عبر جميع المستأجرين وحالة الحماية برنامج الحماية من الفيروسات من Microsoft Defender الخاصة بهم. يمكنك تقييم الحالة واتخاذ إجراء لجهاز واحد أو أكثر قد يكون عرضة للخطر. يمكنك أيضا تحديد جهاز لعرض المزيد من المعلومات، مثل "نظرة عامة على الجهاز" و"التهديدات الحالية" و"إجراءات الجهاز".

:::image type="content" source="../media/m365-lighthouse-threat-management-page-overview/threatmanagement-antivirus-tab.png" alt-text="لقطة شاشة لعلامة تبويب برنامج الحماية من الفيروسات.":::

## <a name="related-content"></a>المحتويات ذات الصلة

[نشر خطوط الأساس Microsoft 365 Lighthouse](m365-lighthouse-deploy-baselines.md) (مقالة)\
[الأسئلة المتداولة حول Microsoft 365 Lighthouse](m365-lighthouse-faq.yml) (مقالة)
