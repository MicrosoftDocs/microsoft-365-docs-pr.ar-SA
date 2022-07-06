---
title: مخطط انسيابي لتحديد متى يتم الاحتفاظ بعنصر أو حذفه
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
description: استخدام مخطط انسيابي لتحديد النتيجة عندما يحتوي العنصر على نهج استبقاء متعددة أو تسمية استبقاء ونهج استبقاء
ms.openlocfilehash: 4e5c1cf887144f89764e88a39ba14a95a2df576c
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/06/2022
ms.locfileid: "66633444"
---
# <a name="flowchart-to-determine-when-an-item-will-be-retained-or-permanently-deleted"></a>مخطط انسيابي لتحديد متى سيتم الاحتفاظ بعنصر أو حذفه نهائيا

>*[إرشادات ترخيص Microsoft 365 للامتثال & الأمان](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).*

استخدم المخطط الانسيابي التالي لتطبيق [مبادئ الاستبقاء](retention.md#the-principles-of-retention-or-what-takes-precedence) على عنصر لتحديد ما إذا كان النظام سيحتفظ به أو يحذفه بشكل دائم كنتيجة لتسمية الاستبقاء أو نهج الاستبقاء.

يتم استخدام تدفق المنطق هذا لعنصر عند تطبيق أي من الشروط التالية:

- هناك أكثر من نهج استبقاء واحد مطبق
- هناك تسمية استبقاء ونهج استبقاء واحد أو أكثر

عندما يكون العنصر خاضعا لقائمة احتجاز eDiscovery (أو التقنيات القديمة ل "احتجاز التقاضي" أو "احتجاز In-Place")، سيتم الاحتفاظ به دائما قبل تدفق القرار لنهج الاستبقاء وتسمية الاستبقاء.

إذا كان أي من المصطلحات المستخدمة في هذا المخطط الانسيابي غير مألوفة بالنسبة لك، فراجع [التعرف على نهج الاستبقاء وتسميات الاستبقاء](retention.md).


   ![مخطط انسيابي لتحديد متى سيتم الاحتفاظ بعنصر أو حذفه نهائيا.](../media/retention-flowchart.svg)

> [!NOTE]
> من المهم التمييز بين أطول فترة استبقاء للعنصر مقابل أطول فترة محددة في نهج الاستبقاء أو التسمية. وبالمثل، بين أقصر تاريخ انتهاء للعنصر مقابل أقصر فترة محددة في نهج الاستبقاء.
> 
> لمزيد من المعلومات، راجع التفسير بعد الرسم في قسم [مبادئ الاستبقاء](retention.md#the-principles-of-retention-or-what-takes-precedence) .
