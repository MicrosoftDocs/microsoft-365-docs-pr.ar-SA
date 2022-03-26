---
title: عزل المستأجر في Microsoft 365
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
description: تحتوي هذه المقالة على ملخص حول كيفية فرض Microsoft لعزل المستأجر في الخدمات السحابية مثل Microsoft 365.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: b52d936bb00ac0adef0baf428cbc5f9a8f8aba49
ms.sourcegitcommit: 27addd4dac07926528b788215d2dcd0e46301eb1
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/16/2021
ms.locfileid: "63575319"
---
# <a name="tenant-isolation-in-microsoft-365"></a>عزل المستأجر في Microsoft 365

وتتمثل إحدى الفوائد الأساسية للحوسبة السحابية في مفهوم البنية الأساسية المشتركة الشائعة بين العديد من العملاء في الوقت نفسه، مما يؤدي إلى عمليات تحسين الحجم. يسمى هذا المفهوم إيجار *متعدد*. تعمل Microsoft بشكل مستمر لضمان أن هندسة المستأجرين المتعددين لخدمات السحابة تدعم معايير الأمان والسرية والخصوصية والنزاهة والتوفر على مستوى المؤسسة.

استنادا إلى الاستثمارات والخبرات الهامة التي تم جمعها [](https://www.microsoft.com/trust-center) من الحوسبة الموثوق بها [](https://www.microsoft.com/securityengineering/sdl/)و دورة حياة تطوير الأمان، تم تصميم خدمات Microsoft السحابية مع افتراض أن جميع المستأجرين يحتمل أن يكون لديهم مستأجرين محتملين لجميع المستأجرين الآخرين، وقد قمنا بتنفيذ إجراءات أمان لمنع إجراءات مستأجر واحد من التأثير على أمان مستأجر آخر أو خدمته،  أو الوصول إلى محتوى مستأجر آخر.

إن الهدفين الأساسيين للحفاظ على عزل المستأجر في بيئة متعددة المستأجرين هي:

1.    منع تسريب محتوى العميل أو الوصول إليه بشكل غير مصرح به عبر المستأجرين؛ و
2.    منع إجراءات مستأجر واحد من التأثير سلبا على الخدمة لمستأجر آخر

تم تنفيذ أشكال حماية متعددة خلال Microsoft 365 لمنع العملاء من التأثير على خدمات Microsoft 365 أو تطبيقاته أو اكتساب حق وصول غير مصرح به إلى معلومات المستأجرين الآخرين أو نظام Microsoft 365 نفسه، بما في ذلك:

- يتم تحقيق عزل منطقي لمحتوى العميل داخل كل مستأجر لخدمات Microsoft 365 من خلال تخويل Azure Active Directory والتحكم بالوصول المستند إلى الدور.
- SharePoint Online آليات عزل البيانات على مستوى التخزين.
- تستخدم Microsoft الأمان الفعلي الصارم والفحص في الخلفية وإستراتيجية تشفير متعددة الطبقات لحماية سرية محتوى العميل وتكامله. تتوفر Microsoft 365 في مراكز البيانات عناصر تحكم في الوصول إلى المقاييس الحيوية، حيث تتطلب معظمها طباعة نخيل للوصول الفعلي. بالإضافة إلى ذلك، يطلب من جميع موظفي Microsoft المستندين إلى الولايات المتحدة إكمال فحص الخلفية القياسي بنجاح كجزء من عملية التوظيف. لمزيد من المعلومات حول عناصر التحكم المستخدمة للوصول الإداري في Microsoft 365، راجع Microsoft 365 [التحكم بالوصول الإداري](/compliance/assurance/assurance-administrative-access-controls-overview).
- Microsoft 365 تقنيات من جانب الخدمة وتشفير محتوى العميل أثناء الراحة وعند النقل، بما في ذلك BitLocker والتشفير لكل ملف والأمان في طبقة النقل (TLS) والأمان في بروتوكول الإنترنت (IPsec). للحصول على تفاصيل محددة حول التشفير في Microsoft 365، راجع [تقنيات تشفير البيانات في](../compliance/office-365-encryption-in-the-microsoft-cloud-overview.md) Microsoft 365.

توفر الحماية المذكورة أعلاه معا عناصر تحكم عزل منطقية قوية توفر الحماية من المخاطر وتخفيف المخاطر المكافئة للتهديدات التي يوفرها العزل الفعلي فقط.

## <a name="related-links"></a>الارتباطات ذات الصلة

- [التحكم بالعزل والوصول في Azure Active Directory](microsoft-365-isolation-in-azure-active-directory.md)
- [عزل المستأجر في مخطط Office Delve](microsoft-365-isolation-in-graph-and-delve.md)
- [عزل المستأجر في Microsoft 365 البحث](microsoft-365-isolation-in-microsoft-365-search.md)
- [حدود الموارد](/compliance/assurance/assurance-resource-limits)
- [مراقبة حدود المستأجر واختبارها](/compliance/assurance/assurance-monitoring-and-testing)
- [التحكم بالعزل والوصول في Microsoft 365](microsoft-365-isolation-in-microsoft-365.md)