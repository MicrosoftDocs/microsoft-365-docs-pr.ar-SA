---
title: Microsoft 365 Defender واجهات برمجة التطبيقات للحوادث ونوع مورد الأحداث
description: تعرف على أساليب وخصائص نوع مورد "الحوادث" في Microsoft 365 Defender
keywords: حادث، أحداث، api
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
ms.openlocfilehash: a1a3f119e0aafe75b58df9c2330a950d5ab31ead
ms.sourcegitcommit: 6f3bc00a5cf25c48c61eb3835ac069e9f41dc4db
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 01/24/2022
ms.locfileid: "63572236"
---
# <a name="microsoft-365-defender-incidents-api-and-the-incidents-resource-type"></a>Microsoft 365 Defender API للحوادث ونوع مورد الأحداث

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**ينطبق على:**

- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> [!IMPORTANT]
> تتعلق بعض المعلومات بالمنتج الذي تم إصداره مسبقا والذي قد يتم تعديله بشكل كبير قبل طرحه تجاريا. لا تقدم Microsoft أي ضمانات، صريحة أو ضمنية، فيما يتعلق بالمعلومات المتوفرة هنا.

إن [الحادث](incidents-overview.md) عبارة عن مجموعة من التنبيهات ذات الصلة التي تساعد على وصف هجوم. يتم تجميع الأحداث من كيانات مختلفة في مؤسستك تلقائيا حسب Microsoft 365 Defender. يمكنك استخدام API للحوادث للوصول إلى الأحداث والتنبيهات ذات الصلة في مؤسستك بشكل مبرمجة.

## <a name="quotas-and-resource-allocation"></a>الحصص النسبية وتخصيص الموارد

يمكنك طلب ما يصل إلى 50 مكالمة في الدقيقة أو 1500 مكالمة في الساعة. تحتوي كل طريقة أيضا على الحصص النسبية الخاصة بها. لمزيد من المعلومات حول الحصص النسبية الخاصة ب الأسلوب، راجع المقالة الخاصة بالطريقة التي تريد استخدامها.

يشير `429` رمز استجابة HTTP إلى أنك وصلت إلى الحصة النسبية، إما حسب عدد الطلبات المرسلة أو حسب وقت التشغيل المخصص. سيتضمن جهاز الاستجابة الوقت حتى يتم إعادة تعيين الحصة النسبية التي وصلت إليها.

## <a name="permissions"></a>الأذونات

تتطلب API للحوادث أنواعا مختلفة من الأذونات لكل من أساليبها. لمزيد من المعلومات حول الأذونات المطلوبة، راجع مقالة الأسلوب المعني.

## <a name="methods"></a>الأساليب

الأسلوب | نوع الإرجاع | الوصف
-|-|-
[سرد الأحداث](api-list-incidents.md) | [قائمة](api-incident.md) الأحداث | الحصول على قائمة بالحوادث.
[تحديث الحادث](api-update-incidents.md) | [حادث](api-incident.md) | تحديث حادث معين.
[الحصول على حادث](api-get-incident.md) | [حادث](api-incident.md) | احصل على حادث واحد.

## <a name="request-body-response-and-examples"></a>طلب المطلب والرد والأمثلة

راجع مقالات الأسلوب الخاصة للحصول على مزيد من التفاصيل حول كيفية إنشاء طلب أو تحليل استجابة، وأمثلة عملية.

## <a name="common-properties"></a>الخصائص الشائعة

الخاصية | النوع | الوصف
-|-|-
incidentId | طويل | الم ID فريد للحادث.
redirectIncidentId | طويل قابل للبطلان | تم دمج "معرّف الحادث" للحادث الحالي فيه.
incidentName | سلسلة | اسم الحادث.
createdTime | DateTimeOffset | التاريخ والوقت (في UTC) تم إنشاء الحادث.
lastUpdateTime | DateTimeOffset | التاريخ والوقت (في UTC) تم آخر تحديث للحادث.
assignedTo | سلسلة | مالك الحادث.
الخطورة | تعداد | خطورة الحادث. القيم المحتملة هي: ```UnSpecified```و ```Informational```و ```Low```و ```Medium```و و ```High```.
الحالة | تعداد | تحدد الحالة الحالية للحادث. القيم المحتملة هي: ```Active```و ```InProgress```و ```Resolved```و و ```Redirected```.
تصنيف | تعداد | مواصفات الحادث. القيم المحتملة هي: ```Unknown```، ```FalsePositive```و . ```TruePositive```
تحديد | تعداد | تحدد تحديد الحادث. القيم المحتملة هي: ```NotAvailable```، ، ```Apt```، ```Malware```، ```SecurityPersonnel```، ```UnwantedSoftware``````SecurityTesting```، ```Other```.
العلامات | قائمة السلسلة | قائمة علامات الأحداث.
التعليقات | قائمة تعليقات الأحداث | يحتوي كائن تعليق الحادث على: سلسلة التعليق وسلسلة createdBy وإنشاء وقت التاريخ.
التنبيهات | قائمة التنبيهات | قائمة التنبيهات ذات الصلة. راجع الأمثلة في [وثائق API لحوادث](api-list-incidents.md) القائمة.

## <a name="related-articles"></a>المقالات ذات الصلة

- [Microsoft 365 Defender نظرة عامة على واجهات برمجة التطبيقات](api-overview.md)
- [نظرة عامة حول الأحداث](incidents-overview.md)
- [API لحوادث القائمة](api-list-incidents.md)
- [API لحادث التحديث](api-update-incidents.md)
