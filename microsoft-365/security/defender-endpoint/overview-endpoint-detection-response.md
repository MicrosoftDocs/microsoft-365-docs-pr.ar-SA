---
title: نظرة عامة على قدرات الكشف عن نقاط النهاية والاستجابة لها
ms.reviewer: ''
description: تعرف على قدرات الكشف عن نقطة النهاية والاستجابة لها في Microsoft Defender لنقطة النهاية
keywords: Microsoft Defender لنقطة النهاية، الكشف عن نقطة النهاية والاستجابة لها، والاستجابة، والكشف، والأمان عبر الإنترنت، والحماية
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
ms.openlocfilehash: 757064e8867cda8676fd0cf20a662ff04d130e9c
ms.sourcegitcommit: bc35c7826e3403f259725ac72cca5bafd36aa56a
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 06/30/2022
ms.locfileid: "66554500"
---
# <a name="overview-of-endpoint-detection-and-response"></a>نظرة عامة على الكشف عن نقطة النهاية والاستجابة لها

**ينطبق على:**
- [Defender for Endpoint الخطة 1 و 2](defender-endpoint-plan-1-2.md)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> هل تريد تجربة Microsoft Defender لنقطة النهاية؟ [التسجيل للحصول على إصدار تجريبي مجاني.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

توفر قدرات الكشف عن نقطة النهاية والاستجابة لها في Defender لنقطة النهاية عمليات الكشف المتقدمة عن الهجمات التي تقترب من الوقت الحقيقي وقابلة للتنفيذ. يمكن لمحللين أمنيين تحديد أولويات التنبيهات بشكل فعال، والحصول على رؤية في النطاق الكامل للخرق، واتخاذ إجراءات الاستجابة لمعالجة التهديدات.

عند الكشف عن تهديد، يتم إنشاء تنبيهات في النظام للمحلل للتحقيق فيها. يتم تجميع التنبيهات بنفس تقنيات الهجوم أو المنسوبة إلى نفس المهاجم في كيان يسمى _حدثا_. إن تجميع التنبيهات بهذه الطريقة يجعل من السهل على المحللين التحقيق في التهديدات والاستجابة لها بشكل جماعي.

> [!NOTE]
> ليس المقصود من Defender للكشف عن نقطة النهاية أن يكون حل تدقيق أو تسجيل يسجل كل عملية أو نشاط يحدث على نقطة نهاية معينة. يحتوي جهاز الاستشعار الخاص بنا على آلية تقييد داخلية، لذلك فإن معدل تكرار الأحداث المتطابقة لن يغمر السجلات.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4o1j5]

> [!IMPORTANT]
> تتضمن [خطة Defender لنقطة النهاية 1](defender-endpoint-plan-1.md) وخطة [Microsoft Defender for Business](../defender-business/mdb-overview.md) إجراءات الاستجابة اليدوية التالية فقط:
> - تشغيل مسح الحماية من الفيروسات
> - عزل الجهاز
> - إيقاف ملف وعزله
> - إضافة مؤشر لحظر ملف أو السماح به

مستوحاة من عقلية "افتراض الخرق"، يجمع Defender for Endpoint بيانات تتبع الاستخدام السيبراني السلوكي باستمرار. يتضمن ذلك معلومات العملية وأنشطة الشبكة والبصريات العميقة في kernel ومدير الذاكرة وأنشطة تسجيل دخول المستخدم وتغييرات نظام السجل والملفات وغيرها. يتم تخزين المعلومات لمدة ستة أشهر، ما يتيح للمحلل العودة في الوقت المناسب لبدء الهجوم. يمكن للمحلل بعد ذلك أن يحور في طرق عرض مختلفة ويتعامل مع التحقيق من خلال خطوط متجهة متعددة.

تمنحك قدرات الاستجابة القدرة على معالجة التهديدات على الفور من خلال العمل على الكيانات المتأثرة.

## <a name="related-topics"></a>المواضيع ذات الصلة

- [لوحة معلومات عمليات الأمان](security-operations-dashboard.md)
- [قائمة انتظار الأحداث](view-incidents-queue.md)
- [قائمة انتظار التنبيهات](alerts-queue.md)
- [قائمة الأجهزة](machines-view-overview.md)
