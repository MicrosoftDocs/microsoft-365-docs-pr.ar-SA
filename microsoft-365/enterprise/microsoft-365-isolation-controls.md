---
title: Microsoft 365 التحكم بالعزل
ms.author: robmazz
author: robmazz
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Strat_O365_IP
- M365-security-compliance
f1.keywords:
- NOCSH
description: تعرف على كيفية عمل عناصر التحكم بالعزل ضمن Microsoft 365، مما يسمح للخدمات بالعمل المشترك أو البقاء مستقلا حسب الحاجة.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 514b12e44d9e81a18b691ebf3196a3d21157e71b
ms.sourcegitcommit: 27addd4dac07926528b788215d2dcd0e46301eb1
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/16/2021
ms.locfileid: "63569598"
---
# <a name="microsoft-365-isolation-controls"></a>Microsoft 365 التحكم بالعزل 

تعمل Microsoft بشكل مستمر لضمان أن بنية المستأجرين المتعددين Microsoft 365 تدعم معايير الأمان والسرية والخصوصية والنزاهة والمحلية والدولية [والتوفر](https://www.microsoft.com/TrustCenter/Compliance?service=Office#Icons) على مستوى المؤسسة. يجعل حجم ونطاق الخدمات التي تقدمها Microsoft من الصعب وغير الاقتصادية إدارة Microsoft 365 تفاعل بشري كبير. Microsoft 365 الخدمات من خلال عدة مراكز بيانات موزعة على مستوى العالم، كل منها يتم بشكل تلقائي للغاية مع عمليات قليلة تتطلب لمسة بشرية أو أي وصول إلى محتوى العميل. يدعم فريق العمل لدينا هذه الخدمات ومراكز البيانات باستخدام الأدوات التلقائية والوصول عن بعد عالي الأمان. 

Microsoft 365 مجموعة من الخدمات المتعددة التي توفر وظائف أعمال مهمة وتساهم في Microsoft 365 الكاملة. كل واحدة من هذه الخدمات مضمنة ذاتيا ومصممة للتكامل مع بعضها البعض.

Microsoft 365 تم تصميمه بالمبادئ التالية:

 - **[البنية الموجهة للخدمة](/previous-versions/aa480021(v=msdn.10)):** تصميم البرامج وتطويرها في شكل خدمات قابلة للعمل التفاعلي توفر وظائف أعمال محددة بشكل جيد.
 - **[ضمان الأمان](https://www.microsoft.com/download/details.aspx?id=40872)** التشغيلي: إطار عمل يتضمن المعارف المكتسبة من خلال قدرات متنوعة فريدة ل Microsoft، بما في ذلك دورة حياة تطوير الأمان [ل Microsoft ومركز](https://www.microsoft.com/sdl/default.aspx) استجابة [أمان Microsoft](https://technet.microsoft.com/library/dn440717.aspx) ووعيا كبيرا بمشهد خطر الأمن الإلكتروني.

Microsoft 365 الخدمات المشتركة مع بعضها البعض، ولكن تم تصميمها وتنفيذها بحيث يمكن نشرها وتشغيلها كالخدمات العامة، بشكل مستقل عن بعضها البعض. تقوم Microsoft بفصل الواجبات ومجالات المسؤولية Microsoft 365 لتقليل فرص التعديل أو إساءة الاستخدام غير المصرح به أو غير المقصود لأصول المؤسسة. Microsoft 365 الفرق أدوارا محددة كجزء من آلية شاملة للتحكم في الوصول تستند إلى الدور.

## <a name="customer-content-isolation"></a>عزل محتوى العميل

يتم عزل كل محتويات العملاء في نطاق المستأجر عن المستأجرين الآخرين ومن العمليات وبيانات الأنظمة المستخدمة في إدارة Microsoft 365. يتم تنفيذ أشكال متعددة من الحماية خلال Microsoft 365 لتقليل خطر اختراق أي Microsoft 365 أو تطبيق. كما تمنع أشكال الحماية المتعددة الوصول غير المصرح به إلى معلومات المستأجرين أو Microsoft 365 نفسه.

للحصول على معلومات حول كيفية تنفيذ Microsoft لعزل منطقي لبيانات المستأجر داخل Microsoft 365، راجع عزل المستأجر [في](microsoft-365-tenant-isolation-overview.md) Microsoft 365.