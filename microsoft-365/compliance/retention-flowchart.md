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
ms.openlocfilehash: cf35a89faf3ed526c94acf362f1a927eb36420f0
ms.sourcegitcommit: 5c64002236561000c5bd63c71423e8099e803c2d
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 05/09/2022
ms.locfileid: "65286791"
---
# <a name="flowchart-to-determine-when-an-item-will-be-retained-or-permanently-deleted"></a>مخطط انسيابي لتحديد متى سيتم الاحتفاظ بعنصر أو حذفه نهائيا

>*[Microsoft 365 إرشادات الترخيص للامتثال & الأمان](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).*

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

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
