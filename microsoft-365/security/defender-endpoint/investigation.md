---
title: نوع مورد التحقيق
description: وحدة التحقيق في Microsoft Defender لنقطة النهاية.
keywords: apis، api الخاصة بالرسم البياني، apis المعتمدة، الحصول، التنبيهات، التحقيق
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: m365-security-compliance
ms.topic: article
MS.technology: mde
ms.custom: api
ms.openlocfilehash: 1749404942b42778ecde99417a8e3501c7c4f4cf
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/08/2022
ms.locfileid: "63570626"
---
# <a name="investigation-resource-type"></a>نوع مورد التحقيق

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**
- [خطة Microsoft Defender لنقطة النهاية 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> هل تريد تجربة Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!Include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!Include[Improve request performance](../../includes/improve-request-performance.md)]

تمثيل كيان تحقيق تلقائي في Defender for Endpoint.

لمزيد من المعلومات، راجع [نظرة عامة حول عمليات البحث التلقائية](automated-investigations.md).

## <a name="methods"></a>الأساليب

الأسلوب|نوع الإرجاع|الوصف
:---|:---|:---
["التحقيق في القائمة"](get-investigation-collection.md)|مجموعة التحقيق|الحصول على مجموعة من "التحقيق"
[الحصول على تحقيق واحد](get-investigation-object.md)|كيان التحقيق|يحصل على وحدة تحقيق واحدة.
[بدء التحقيق](initiate-autoir-investigation.md)|كيان التحقيق|بدء التحقيق على جهاز.

## <a name="properties"></a>الخصائص

الخاصية|النوع|الوصف
:---|:---|:---
الم ID|سلسلة|هوية كيان التحقيق. 
startTime|DateTime Nullable|تاريخ وتاريخ إنشاء التحقيق.
endTime|DateTime Nullable|التاريخ والوقت الذي تم فيه إكمال التحقيق.
تم إلغاءBy|سلسلة|وهو المستخدم/التطبيق الذي ألغى هذا التحقيق.
الولاية|تعداد|الحالة الحالية التحقيق. القيم المحتملة هي: "غير معروف"، "تم إنهاؤه"، "تم المعالجة بنجاح"، "نينا"، 'فشل'، 'تم الإصلاح جزئيا'، 'قيد التشغيل'، 'معلقApproval'، 'PendingResource'، 'PartiallyInvestigated'، 'TerminatedByUser'، 'TerminatedBySystem'، 'قائمة الانتظار'، 'InnerFailure'، 'PreexistingAlert'، 'UnsupportedOs'، 'UnsupportedAlertType'، 'SuppressedAlert'.
statusDetails|سلسلة|معلومات إضافية حول حالة التحقيق.
machineId|سلسلة|وهو الجهاز الذي يتم تنفيذ التحقيق عليه.
computerDnsName|سلسلة|اسم الجهاز الذي يتم تنفيذ التحقيق عليه.
triggeringAlertId|سلسلة|هو الم ID للتنبيه الذي حفز التحقيق.

## <a name="json-representation"></a>تمثيل Json

```json
{
    "id": "63004",
    "startTime": "2020-01-06T13:05:15Z",
    "endTime": null,
    "state": "Running",
    "cancelledBy": null,
    "statusDetails": null,
    "machineId": "e828a0624ed33f919db541065190d2f75e50a071",
    "computerDnsName": "desktop-test123",
    "triggeringAlertId": "da637139127150012465_1011995739"
}
```
