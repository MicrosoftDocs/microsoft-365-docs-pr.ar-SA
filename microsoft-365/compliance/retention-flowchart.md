---
title: تقرير انسياب لتحديد متى سيتم الاحتفاظ بصنف ما أو حذفه نهائيا
f1.keywords:
- NOCSH
ms.author: cabailey
author: cabailey
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: conceptual
ms.service: O365-seccomp
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
- SPO_Content
search.appverid:
- MOE150
- MET150
description: استخدام جدول انسياب لتحديد النتيجة عندما يكون العنصر لديه عدة سياسات استبقاء أو تسمية استبقاء ونهج استبقاء
ms.openlocfilehash: b9c3b94dcb50499b6af72fd124da384f90d16da9
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 01/12/2022
ms.locfileid: "63578454"
---
# <a name="flowchart-to-determine-when-an-item-will-be-retained-or-permanently-deleted"></a>تقرير انسياب لتحديد متى سيتم الاحتفاظ بصنف ما أو حذفه نهائيا

>*[Microsoft 365 إرشادات الترخيص لتوافق & الأمان](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).*

استخدم المستعرض التدفقي التالي لتطبيق مبادئ الاستبقاء على عنصر ما لتحديد ما إذا كان النظام سيحتفظ به أو سيحذفه بشكل دائم نتيجة تسمية استبقاء أو نهج استبقاء.[](retention.md#the-principles-of-retention-or-what-takes-precedence)

يتم استخدام تدفق المنطق هذا لأي عنصر عند تطبيق أي من الشروط التالية:

- هناك أكثر من نهج استبقاء واحد مطبق
- هناك تسمية استبقاء ونهج استبقاء واحدة أو أكثر

عندما يخضع عنصر ما إلى احتجاز eDiscovery (أو التقنيات القديمة من الاحتجاز بسبب الدعاوى القضائية أو احتجاز In-Place)، سيتم الاحتفاظ به دائما قبل أن ينساب القرار لنهج الاستبقاء وتسمية الاستبقاء.

إذا لم يكن أي من المصطلحات المستخدمة في هذا الملصق التدفقي مألوفا بالنسبة لك، ف راجع التعرف على سياسات الاستبقاء وتسميات [الاستبقاء](retention.md).


   ![تقرير انسياب لتحديد وقت الاحتفاظ بعنصر ما أو حذفه نهائيا.](../media/retention-flowchart.svg)

> [!NOTE]
> من المهم التمييز بين أطول فترة استبقاء في العنصر مقابل أطول فترة محددة في نهج استبقاء أو تسمية. وبالمثل، بين أقصر تاريخ انتهاء صلاحية للصنف مقابل أقصر فترة محددة في نهج استبقاء.
> 
> لمزيد من المعلومات، راجع الشرح بعد الرسم في [القسم مبادئ الاستبقاء](retention.md#the-principles-of-retention-or-what-takes-precedence) .
