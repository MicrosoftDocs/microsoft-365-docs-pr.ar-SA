---
title: الحصص النسبية المتقدمة للصيد ومعاينات الاستخدام في Microsoft 365 Defender
description: فهم مختلف الحصص النسبية ومعاينات الاستخدام (حدود الخدمة) التي تحافظ على استجابة خدمة الصيد المتقدمة
keywords: الصيد المتقدم، وصيد التهديدات، والصيد عبر الإنترنت، و Microsoft 365 Defender، و microsoft 365، و m365، و البحث، و الاستعلام، و بيانات التعقب، و المخطط، و kusto، وحد CPU، وحد الاستعلام، والموارد، والحد الأقصى للنتائج، والحصة النسبية، والمعلمات، والتخصيص
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: maccruz
author: schmurky
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: m365-security-compliance
ms.topic: article
ms.technology: m365d
ms.openlocfilehash: fe0ad42ac0ebfc7f6816e412ab6ffb0ac9291b44
ms.sourcegitcommit: bf3965b46487f6f8cf900dd9a3af8b213a405989
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 11/02/2021
ms.locfileid: "63569905"
---
# <a name="advanced-hunting-quotas-and-usage-parameters"></a>الحصص النسبية المتقدمة للصيد ومعا معلمات الاستخدام

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**ينطبق على:**
- Microsoft 365 Defender

للحفاظ على أداء الخدمة والاستجابة لها، يقوم الصيد المتقدم بتعيين الحصص النسبية ومعلمات الاستخدام المختلفة (المعروفة أيضا باسم "حدود الخدمة"). تنطبق هذه الحصص النسبية والمعلمات بشكل منفصل على الاستعلامات التي يتم تشغيلها يدويا وعلى الاستعلامات التي يتم تشغيلها باستخدام [قواعد الكشف المخصصة](custom-detection-rules.md). يجب على العملاء الذين يديرون استعلامات متعددة بشكل منتظم الانتباه إلى هذه الحدود وتطبيق [أفضل ممارسات التحسين](advanced-hunting-best-practices.md) لتقليل حالات الانقطاع.

راجع الجدول التالي لفهم الحصص النسبية ومعلمات الاستخدام الموجودة.

| الحصة النسبية أو المعلمة | الحجم | دورة التحديث | الوصف |
|--|--|--|--|
| نطاق البيانات | 30 يوماً | كل استعلام | يمكن لكل استعلام البحث عن البيانات من الأيام الثلاثين الماضية. |
| مجموعة النتائج | 10000 صف | كل استعلام | يمكن أن يرجع كل استعلام ما يصل إلى 10000 سجل. |
| 2013 | 10 دقائق | كل استعلام | يمكن تشغيل كل استعلام لمدة تصل إلى 10 دقائق. إذا لم تكتمل في غضون 10 دقائق، فعرض الخدمة خطأ.
| موارد CPU | استنادا إلى حجم المستأجر | كل 15 دقيقة | يعرض [المدخل خطأ كلما](advanced-hunting-errors.md) تم تشغيل استعلام واستهلك المستأجر أكثر من 10٪ من الموارد المخصصة. يتم حظر الاستعلامات إذا وصل المستأجر إلى 100٪ حتى بعد دورة ال 15 دقيقة التالية. |

>[!NOTE] 
>تنطبق مجموعة منفصلة من الحصص النسبية والمعلمات على استعلامات الصيد المتقدمة التي يتم تنفيذها من خلال API. [اقرأ حول واجهات برمجة التطبيقات المتقدمة للصيد](./api-advanced-hunting.md)

## <a name="related-topics"></a>المواضيع ذات الصلة

- [أفضل الممارسات المتقدمة للصيد](advanced-hunting-best-practices.md)
- [معالجة أخطاء الصيد المتقدمة](advanced-hunting-errors.md)
- [نظرة عامة متقدمة حول الصيد](advanced-hunting-overview.md)
- [نظرة عامة على الكشف المخصص](custom-detections-overview.md)