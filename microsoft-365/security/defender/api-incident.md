---
title: Microsoft 365 Defender واجهات برمجة التطبيقات للحوادث ونوع مورد الحوادث
description: تعرف على أساليب وخصائص نوع مورد الحوادث في Microsoft 365 Defender
keywords: الحادث، الحوادث، واجهة برمجة التطبيقات
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: conceptual
search.appverid:
- MOE150
- MET150
ms.technology: m365d
ms.custom: api
ms.openlocfilehash: 45a6e14d6c3514a63869cc9d7229cda8dd511334
ms.sourcegitcommit: e4882e3c66166ea7b834ad2e8fafeab42293e07d
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/30/2022
ms.locfileid: "67100064"
---
# <a name="microsoft-365-defender-incidents-api-and-the-incidents-resource-type"></a>واجهة برمجة تطبيقات أحداث Microsoft 365 Defender ونوع مورد الحوادث

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**ينطبق على:**

- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> [!IMPORTANT]
> تتعلق بعض المعلومات بالناتج الذي تم إصداره مسبقا والذي قد يتم تعديله بشكل كبير قبل إصداره تجاريا. لا تقدم Microsoft أي ضمانات، صريحة أو ضمنية، فيما يتعلق بالمعلومات المقدمة هنا.

[الحادث](incidents-overview.md) هو مجموعة من التنبيهات ذات الصلة التي تساعد على وصف هجوم. يتم تجميع الأحداث من كيانات مختلفة في مؤسستك تلقائيا بواسطة Microsoft 365 Defender. يمكنك استخدام واجهة برمجة تطبيقات الحوادث للوصول برمجيا إلى أحداث مؤسستك والتنبيهات ذات الصلة.

## <a name="quotas-and-resource-allocation"></a>الحصص النسبية وتخصيص الموارد

يمكنك طلب ما يصل إلى 50 مكالمة في الدقيقة أو 1500 مكالمة في الساعة. كل أسلوب له أيضا الحصص النسبية الخاصة به. لمزيد من المعلومات حول الحصص النسبية الخاصة بالأسلوب، راجع المقالة الخاصة بالأسلوب الذي تريد استخدامه.

`429` يشير رمز استجابة HTTP إلى أنك وصلت إلى حصة نسبية، إما حسب عدد الطلبات المرسلة، أو حسب وقت التشغيل المخصص. سيتضمن نص الاستجابة الوقت حتى تتم إعادة تعيين الحصة النسبية التي وصلت إليها.

## <a name="permissions"></a>الأذونات

تتطلب واجهة برمجة تطبيقات الحوادث أنواعا مختلفة من الأذونات لكل أسلوب من أساليبها. لمزيد من المعلومات حول الأذونات المطلوبة، راجع مقالة الأسلوب المعني.

## <a name="methods"></a>أساليب

أسلوب | نوع الإرجاع | الوصف
-|-|-
[سرد الأحداث](api-list-incidents.md) | قائمة [الحوادث](api-incident.md) | الحصول على قائمة بالحوادث.
[حدث التحديث](api-update-incidents.md) | [حادث](api-incident.md) | تحديث حدث معين.
[الحصول على حادث](api-get-incident.md) | [حادث](api-incident.md) | احصل على حادث واحد.

## <a name="request-body-response-and-examples"></a>نص الطلب والاستجابة والأمثلة

راجع مقالات الأسلوب المعنية للحصول على مزيد من التفاصيل حول كيفية إنشاء طلب أو تحليل استجابة، وللامثلة العملية.

## <a name="common-properties"></a>الخصائص الشائعة

مال | نوع | الوصف
-|-|-
معرف الحدث | طويل | معرف فريد للحدث.
redirectIncidentId | قيمة خالية طويلة | معرف الحدث الذي تم دمج الحدث الحالي فيه.
اسم الحدث | خيط | اسم الحدث.
createdTime | DateTimeOffset | التاريخ والوقت (في UTC) تم إنشاء الحدث.
lastUpdateTime | DateTimeOffset | التاريخ والوقت (في UTC) الذي تم فيه آخر تحديث للحدث.
معين إلى | خيط | مالك الحدث.
شده | قائمة تعداد | خطورة الحدث. القيم المحتملة هي: ```UnSpecified```و، ```Informational```و، ```Low```و، ```Medium```و ```High```.
حالة | قائمة تعداد | تحديد الحالة الحالية للحادث. القيم المحتملة هي: ```Active```و، ```InProgress```و، ```Resolved```و ```Redirected```.
تصنيف | قائمة تعداد | مواصفات الحدث. القيم المحتملة هي: ```Unknown```, , ```TruePositive``````FalsePositive```.
عزم | قائمة تعداد | تحديد تحديد الحادث. القيم المحتملة هي: ```NotAvailable```, ```Apt```, ```Malware```, ```SecurityPersonnel```, , ```SecurityTesting```, ```Other``````UnwantedSoftware```.
العلامات | قائمة السلاسل | قائمة بعلامات الحادث.
التعليقات | قائمة تعليقات الحوادث | يحتوي كائن تعليق الحدث على: سلسلة تعليق وسلسلة createdBy ووقت تاريخ createTime.
تنبيهات | قائمة التنبيهات | قائمة التنبيهات ذات الصلة. راجع الأمثلة في وثائق واجهة [برمجة تطبيقات أحداث القائمة](api-list-incidents.md) .

>[!NOTE]
>حوالي 29 أغسطس 2022، سيتم إهمال قيم تحديد التنبيه المدعومة مسبقا ('Apt' و'SecurityPersonnel') ولن تعود متوفرة عبر واجهة برمجة التطبيقات.

## <a name="related-articles"></a>المقالات ذات الصلة

- [نظرة عامة على واجهات برمجة التطبيقات Microsoft 365 Defender](api-overview.md)
- [نظرة عامة على الحوادث](incidents-overview.md)
- [قائمة بواجهة برمجة التطبيقات للأحداث](api-list-incidents.md)
- [تحديث واجهة برمجة تطبيقات الحدث](api-update-incidents.md)
