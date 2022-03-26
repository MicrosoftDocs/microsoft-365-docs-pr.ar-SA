---
title: واجهات برمجة تطبيقات استجابة نقطة النهاية المدعومة من Microsoft Defender
description: تعرف على مكالمات Microsoft Defender المحددة ذات الصلة بالاستجابة ل API لنقطة النهاية.
keywords: واجهة برمجة التطبيق (apis) للاستجابة، واجهة برمجة واجهة برمجة التطبيق (apis) الرسوم البيانية، apis المعتمدة، الممثل، التنبيهات، الجهاز، المستخدم، المجال، ip، الملف
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: w10
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
ms.openlocfilehash: dcf73669ab780ec23cbd5551039dc8c74f0502ef
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 11/24/2021
ms.locfileid: "63573263"
---
# <a name="supported-microsoft-defender-for-endpoint-query-apis"></a>واجهات برمجة تطبيقات الاستعلام المعتمدة في Microsoft Defender لنقطة النهاية

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**ينطبق على:**
- [خطة Microsoft Defender لنقطة النهاية 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/?linkid=2154037)

> [!TIP]
> هل تريد تجربة Microsoft Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-supported-response-apis-abovefoldlink)

تعرف على مكالمات API المعتمدة ذات الصلة بالاستجابة التي يمكنك تشغيلها وتفاصيل مثل رؤوس الطلبات المطلوبة والاستجابة المتوقعة من المكالمات.

## <a name="in-this-section"></a>في هذا القسم

<br>

****

|الموضوع|الوصف|
|---|---|
|تجميع حزمة التحقيق|تشغيل API لجمع حزمة تحقيق من جهاز.|
|عزل الجهاز|يمكنك تشغيل API هذه لعزل جهاز من الشبكة.|
|جهاز Unisolate|إزالة جهاز من عزله.|
|تقييد تنفيذ التعليمات البرمجية|تشغيل API هذا لاحتواء هجوم من خلال إيقاف العمليات الضارة. يمكنك أيضا تأمين جهاز ومنع المحاولات اللاحقة للبرامج التي قد تكون ضارة من التشغيل.|
|تنفيذ التعليمات البرمجية لRict|يمكنك تشغيل ذلك لعكس تقييد نهج التطبيقات بعد التحقق من أنه قد تم إصلاح الجهاز الذي تم اختراقه.|
|تشغيل مسح الحماية من الفيروسات|قم ببدء فحص برنامج الحماية من الفيروسات عن بعد للمساعدة في تحديد البرامج الضارة التي قد تكون موجودة على جهاز تم اختراقه وتسوية هذه البرامج.|
|ملف إيقاف وفحص|قم بتشغيل هذا الاستدعاء لإيقاف تشغيل العمليات، وفحص الملفات، وحذف الاستمرار مثل مفاتيح التسجيل.|
|عينة الطلب|تشغيل هذه المكالمة لطلب عينة من ملف من جهاز معين. سيتم تجميع الملف من الجهاز وتحميله إلى مساحة تخزين آمنة.|
|حظر الملف|تشغيل API لمنع نشر هجوم آخر في مؤسستك عن طريق حظر الملفات الضارة أو البرامج الضارة المشتبه بها.|
|إلغاء حظر الملف|السماح بتشغيل ملف في المؤسسة باستخدام برنامج الحماية من الفيروسات من Microsoft Defender.|
|الحصول على حزمة SAS URI|قم بتشغيل API هذه للحصول على URI يسمح بتنزيل حزمة التحقيق.|
|الحصول على كائن MachineAction|تشغيل API هذه للحصول على كائن MachineAction.|
|الحصول على مجموعة MachineActions|تشغيل هذا للحصول على مجموعة MachineAction.|
|الحصول على مجموعة FileActions|تشغيل API هذه للحصول على مجموعة FileActions.|
|الحصول على كائن FileMachineAction|تشغيل API هذه للحصول على كائن FileMachineAction.|
|الحصول على مجموعة FileMachineActions|تشغيل API هذه للحصول على مجموعة FileMachineAction.|
|
