---
title: واجهات برمجة تطبيقات استجابة Microsoft Defender لنقطة النهاية المدعومة
description: تعرف على استدعاءات واجهة برمجة تطبيقات Microsoft Defender لنقطة النهاية الخاصة بالاستجابة.
keywords: واجهة برمجة تطبيقات الاستجابة، واجهة برمجة تطبيقات الرسم البياني، واجهة برمجة التطبيقات المدعومة، الفاعل، التنبيهات، الجهاز، المستخدم، المجال، ip، الملف
search.product: eADQiWindows 10XVcnh
search.appverid: met150
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
ms.openlocfilehash: 8dd36e06b90726a01168ccd3ebf12886c127b101
ms.sourcegitcommit: e8dd5cd434d17af7096d28d467a2b3b021cbb233
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/27/2022
ms.locfileid: "67050931"
---
# <a name="supported-microsoft-defender-for-endpoint-query-apis"></a>واجهات برمجة تطبيقات الاستعلام Microsoft Defender لنقطة النهاية المعتمدة

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**ينطبق على:**
- [الخطة 1 من Microsoft Defender لنقطة النهاية](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Defender for Endpoint الخطة 2](https://go.microsoft.com/fwlink/?linkid=2154037)

> [!TIP]
> هل تريد تجربة Defender لنقطة النهاية؟ [التسجيل للحصول على إصدار تجريبي مجاني.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-supported-response-apis-abovefoldlink)

تعرف على استدعاءات واجهة برمجة التطبيقات المدعومة المتعلقة بالاستجابة التي يمكنك تشغيلها وتفاصيل مثل رؤوس الطلبات المطلوبة والاستجابة المتوقعة من المكالمات.

## <a name="in-this-section"></a>في هذا القسم

<br>

****

|الموضوع|الوصف|
|---|---|
|تجميع حزمة التحقيق|قم بتشغيل واجهة برمجة التطبيقات هذه لجمع حزمة تحقيق من جهاز.|
|عزل الجهاز|شغل واجهة برمجة التطبيقات هذه لعزل جهاز عن الشبكة.|
|جهاز أحادي الزول|إزالة جهاز من العزل.|
|تقييد تنفيذ التعليمات البرمجية|تشغيل واجهة برمجة التطبيقات هذه لاحتواء هجوم عن طريق إيقاف العمليات الضارة. يمكنك أيضا تأمين جهاز ومنع المحاولات اللاحقة للبرامج التي يحتمل أن تكون ضارة من التشغيل.|
|تنفيذ التعليمات البرمجية غير المقيد|قم بتشغيل هذا لعكس تقييد نهج التطبيقات بعد التحقق من معالجة الجهاز المخترق.|
|تشغيل مسح الحماية من الفيروسات|ابدأ عن بعد عملية فحص مكافحة الفيروسات للمساعدة في تحديد البرامج الضارة التي قد تكون موجودة على جهاز تم اختراقه ومعالجتها.|
|ملف إيقاف وفحص|قم بتشغيل هذا الاستدعاء لإيقاف تشغيل العمليات وعزل الملفات وحذف الثبات مثل مفاتيح التسجيل.|
|نموذج الطلب|قم بتشغيل هذا الاستدعاء لطلب عينة من ملف من جهاز معين. سيتم جمع الملف من الجهاز وتحميله إلى مساحة تخزين آمنة.|
|حظر الملف|شغل واجهة برمجة التطبيقات هذه لمنع المزيد من نشر هجوم في مؤسستك عن طريق حظر الملفات الضارة المحتملة أو البرامج الضارة المشتبه بها.|
|إلغاء حظر الملف|السماح بتشغيل ملف في المؤسسة باستخدام برنامج الحماية من الفيروسات من Microsoft Defender.|
|الحصول على حزمة SAS URI|تشغيل واجهة برمجة التطبيقات هذه للحصول على URI الذي يسمح بتنزيل حزمة التحقيق.|
|الحصول على كائن MachineAction|تشغيل واجهة برمجة التطبيقات هذه للحصول على كائن MachineAction.|
|الحصول على مجموعة MachineActions|قم بتشغيل هذا للحصول على مجموعة MachineAction.|
|الحصول على مجموعة FileActions|تشغيل واجهة برمجة التطبيقات هذه للحصول على مجموعة FileActions.|
|الحصول على كائن FileMachineAction|قم بتشغيل واجهة برمجة التطبيقات هذه للحصول على كائن FileMachineAction.|
|الحصول على مجموعة FileMachineActions|قم بتشغيل واجهة برمجة التطبيقات هذه للحصول على مجموعة FileMachineAction.|
|
