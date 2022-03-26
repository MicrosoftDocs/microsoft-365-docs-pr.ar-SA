---
title: فهم مفاهيم معلومات المخاطر في Microsoft Defender لنقطة النهاية
description: إنشاء تنبيهات تهديدات مخصصة لمنظمتك وتعرف على المفاهيم حول المعلومات حول التهديدات في Microsoft Defender لنقطة النهاية
keywords: المعلومات الاستخبارية للتهديدات، تعريفات التنبيهات، مؤشرات اختراق، ioc
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: 440f788c4adb757013611bb05621b4eb4f4e9715
ms.sourcegitcommit: 348f3998a029a876a9dcc031f808e9e350804f22
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 12/03/2021
ms.locfileid: "63571510"
---
# <a name="understand-threat-intelligence-concepts"></a>فهم مفاهيم المعلومات الاستخبارية للتهديدات

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**
- [خطة Microsoft Defender لنقطة النهاية 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)



> هل تريد تجربة Microsoft Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-threatindicator-abovefoldlink)

تتضمن هجمات الأمان الإلكتروني المتقدمة أحداثا ضارة وسمات ومعلومات سياقية متعددة معقدة. قد يكون تحديد أي من هذه الأنشطة مؤهلا للشك وتحديده مهمة صعبة. إن معرفتك للسمات المعروفة والأنشطة غير الطبيعية الخاصة ب الصناعة أساسية في معرفة متى يجب استدعاء سلوك ملاحظ على أنه مريب.

باستخدام Microsoft 365 Defender، يمكنك إنشاء تنبيهات تهديدات مخصصة من الممكن أن تساعدك على تعقب أنشطة الهجمات المحتملة في مؤسستك. يمكنك وضع علامة على الأحداث المريبة لتكاتف الدلائل معا وربما إيقاف سلسلة الهجمات. ستظهر تنبيهات التهديدات المخصصة هذه فقط في مؤسستك وستعلم الأحداث التي قمت بتعيينها لتعقبها.

قبل إنشاء تنبيهات التهديدات المخصصة، من المهم معرفة المفاهيم وراء تعريفات التنبيهات ومؤشرات اختراق (IOCs) والعلاقة بينها.

## <a name="alert-definitions"></a>تعريفات التنبيه
تعريفات التنبيه هي سمات سياقية يمكن استخدامها بشكل جماعي لتحديد الدلائل المبكرة على هجوم محتمل على أمن الإنترنت. عادة ما تكون هذه المؤشرات خليطا من الأنشطة والخصائص والإجراءات التي يتخذها مهاجم لتحقيق هدف الهجوم بنجاح. من المهم مراقبة مجموعات السمات هذه في اكتساب أفضلية ضد الهجمات وربما التداخل مع سلسلة الأحداث قبل الوصول إلى هدف المهاجم.

## <a name="indicators-of-compromise-ioc"></a>مؤشرات اختراق (IOC)
إن أجهزة IOCs هي أحداث ضارة معروفة بشكل فردي تشير إلى اختراق شبكة أو جهاز بالفعل. بخلاف تعريفات التنبيهات، تعتبر هذه المؤشرات دليلا على انتهاك. وغالبا ما يتم اشاهدتها بعد تنفيذ هجوم وتوصل إلى الهدف، مثل التهجم. من المهم أيضا تعقب أجهزة IOCs أثناء عمليات التحقيق في الطب الشرعي. على الرغم من أنه قد لا يتمكن من التعامل مع سلسلة الهجمات، إلا أن جمع هذه المؤشرات قد يكون مفيدا في إنشاء المزيد من الدفاعات للهجمات المحتملة في المستقبل.

## <a name="relationship-between-alert-definitions-and-iocs"></a>العلاقة بين تعريفات التنبيهات ومواد IOCs
في سياق Microsoft 365 Defender و Microsoft Defender لنقطة النهاية، تكون تعريفات التنبيه حاويات ل IOCs وتعرف التنبيه، بما في ذلك بيانات التعريف التي يتم رفعها لمطابقة IOC معينة. يتم توفير بيانات تعريف متنوعة كجزء من تعريفات التنبيه. يتم توفير بيانات التعريف مثل اسم تعريف التنبيه للهجوم والخطورة والوصف مع خيارات أخرى.

تحدد كل IOC منطق الكشف الخرساني استنادا إلى نوعه وقيمته والتحرك الذي يحدد كيفية مطابقته. وهو مرتبط بتعريف تنبيه معين يعرف كيفية عرض الكشف كتنبيه على وحدة Microsoft 365 Defender التحكم.

فيما يلي مثال على IOC:
- النوع: Sha1
- القيمة: 92cfceb39d57d914ed8b14d0e37643de0797ae56
- الإجراء: يساوي

تملك أجهزة IOCs علاقة واحد إلى كثير مع تعريفات التنبيهات مثل تعريف التنبيه الذي يمكن أن يكون له العديد من IOCs التي تتوافق معه.


## <a name="related-topics"></a>المواضيع ذات الصلة
- [إدارة المؤشرات](manage-indicators.md)
