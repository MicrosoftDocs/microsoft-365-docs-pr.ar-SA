---
title: إدارة قواعد منع نقاط النهاية ل Microsoft Defender
description: قد تحتاج إلى منع ظهور التنبيهات في المدخل باستخدام قواعد القمع. تعرف على كيفية إدارة قواعد القمع في Microsoft Defender for Endpoint.
keywords: إدارة القمع، القواعد، اسم القاعدة، النطاق، الإجراء، التنبيهات، تشغيل، إيقاف التشغيل
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
ms.topic: article
ms.technology: mde
ms.openlocfilehash: ee488256363cbb008f670bb8c88d3fb88d7c4090
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 11/24/2021
ms.locfileid: "63573306"
---
# <a name="manage-suppression-rules"></a>إدارة قواعد القمع

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**ينطبق على:**
- [خطة Microsoft Defender لنقطة النهاية 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> هل تريد تجربة Microsoft Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)


قد تحتاج إلى منع ظهور التنبيهات في المدخل في بعض السيناريوهات. يمكنك إنشاء قواعد منع لتنبيهات معينة معروفة بأنها غير ملتبسة مثل الأدوات أو العمليات المعروفة في مؤسستك. لمزيد من المعلومات حول كيفية منع التنبيهات، راجع [منع التنبيهات](manage-alerts.md).

يمكنك عرض قائمة بكل قواعد القمع وإدارتها في مكان واحد. يمكنك أيضا تشغيل قاعدة إيقاف تشغيل التنبيهات أو إيقاف تشغيلها.


1. في جزء التنقل **، حدد الإعدادات** \> **تنبيه** \> **قواعد** \> **نقاط النهاية**. يتم عرض قائمة قواعد القمع التي أنشأها المستخدمون في مؤسستك.

2. حدد قاعدة بالنقر فوق خانة الاختيار إلى جانب اسم القاعدة.

3. انقر **فوق تشغيل القاعدة أو** **تحرير القاعدة** أو  **حذف القاعدة**. عند إجراء تغييرات على قاعدة، يمكنك اختيار إصدار التنبيهات التي تم منعها بالفعل، بغض النظر عما إذا كانت هذه التنبيهات تتطابق مع المعايير الجديدة أم لا. 


## <a name="view-details-of-a-suppression-rule"></a>عرض تفاصيل قاعدة منع

1. في جزء التنقل **، حدد الإعدادات** \> **تنبيه** \> **قواعد** \> **نقاط النهاية**. يتم عرض قائمة قواعد القمع التي أنشأها المستخدمون في مؤسستك.

2. انقر فوق اسم قاعدة. يتم عرض تفاصيل القاعدة. سترى تفاصيل القاعدة مثل الحالة والنطاق والتحرك وعدد التنبيهات المتطابقة التي تم إنشاؤها بواسطة وتاريخ إنشاء القاعدة. يمكنك أيضا عرض التنبيهات المقترنة وشروط القاعدة.

## <a name="related-topics"></a>المواضيع ذات الصلة

- [إدارة التنبيهات](manage-alerts.md)
