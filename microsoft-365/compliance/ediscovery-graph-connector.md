---
title: موصلات Microsoft Purview eDiscovery Graph
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
manager: laurawi
ms.date: 07/15/2022
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.collection:
- m365-security-compliance
- m365solution-ediscovery
- m365initiative-compliance
- m365solution-overview
ms.localizationpriority: medium
search.appverid:
- SPO160
- MOE150
- MET150
description: يمكن لعملاء Microsoft 365 إجراء عمليات بحث eDiscovery على المحتوى الذي تم استيعابه للبحث في المؤسسة.
ms.openlocfilehash: df6f948f60b74da6868f4f3877ee3a39e97c2a46
ms.sourcegitcommit: 180da7b39cfda7263a89bda0c3b93d9d6e55f3c2
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/19/2022
ms.locfileid: "66843763"
---
# <a name="use-graph-connectors-with-ediscovery-premium"></a>استخدام موصلات Graph مع eDiscovery (Premium)

يمكن لعملاء Microsoft 365 إجراء عمليات بحث eDiscovery على المحتوى الذي تم استيعابه للبحث في المؤسسة. سيساعد هذا المؤسسات على تحسين وضع الامتثال لمصادر المحتوى الخارجية من خلال وضعها ضمن نطاق حلول توافق Microsoft.

باستخدام موصلات Graph، يمكنك تمكين المحتوى من مصادر البيانات الخارجية ليكون متوفرا Microsoft Purview eDiscovery الحل المتميز. Mer informasjon حول إنشاء موصلات Graph لمؤسستك هنا: [نظرة عامة على موصلات Microsoft Graph ل Microsoft Search](/microsoftsearch/connectors-overview).

## <a name="add-graph-connector-as-a-data-source-within-a-case"></a>إضافة موصل الرسم البياني كمصدر بيانات داخل حالة

بمجرد إنشاء موصلات الرسم البياني لمؤسسة وتمكين eDiscovery، سيتوفر خيار إضافة مصدر بيانات Graph Connector إلى الحالة ضمن مواقع غير Microsoft 365. ستكون الموصلات التي تم إنشاؤها وتمكينها فقط متاحة لمدير eDiscovery لتضمينها في حالة ما.

:::image type="content" source="../media/ediscovery-graph-new.png" alt-text="يمكنك تحديد Graph كمصدر بيانات.":::

## <a name="collect-graph-connectors-content"></a>تجميع محتوى موصلات الرسم البياني

عند إضافة محتوى Graph Connectors كمصدر بيانات، يتوفر هذا المحتوى للبحث والجمع. ضمن معالج التجميع، حدد محتوى Graph Connector كمصدر بيانات غير احتجازي، واستخدم شروطا مثل نطاق التاريخ والكلمات الأساسية والمزيد للبحث عبر المحتوى المتصل لجمع محتوى الاهتمام فقط. عند الانتهاء من المعالج، تحصل على تقديرات لكمية المحتوى الذي يحتوي على عدد مرات الوصول إلى معايير البحث الخاصة بك، وتثبيت المجموعة بمجموعة المراجعة.  

## <a name="review-content"></a>مراجعة المحتوى

بمجرد جمعها إلى مجموعة مراجعة، يمكن لمديري eDiscovery مراجعة المحتوى من Graph Connectors لفهم المزيد حول المحتوى والعمل على تقييم ما إذا كانت المعلومات مهمة ومتصلة بالحالة.  

## <a name="export-content"></a>تصدير المحتوى

بمجرد التحقق من أن المحتوى الذي تم جمعه في المراجعة هو المحتوى الصحيح، يصبح هذا المحتوى متوفرا للتصدير من مجموعة المراجعة مباشرة. حدد خيارات التصدير وأرسل مهمة التصدير لمحتوى الموصلات ليتم تصديره من مجموعة المراجعة.
