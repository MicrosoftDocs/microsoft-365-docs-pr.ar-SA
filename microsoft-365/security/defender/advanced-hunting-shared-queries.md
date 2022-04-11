---
title: استخدام الاستعلامات المشتركة في التتبع المتقدم Microsoft 365 Defender
description: ابدأ تتبع التهديدات على الفور باستخدام الاستعلامات المعرفة مسبقا والمشتركة. شارك استعلاماتك إلى الجمهور أو إلى مؤسستك.
keywords: التتبع المتقدم، تتبع التهديدات، تتبع التهديدات عبر الإنترنت، Microsoft 365 Defender، microsoft 365، m365، البحث، الاستعلام، بيانات تتبع الاستخدام، الكشف المخصص، المخطط، kusto، مستودع github، استعلاماتي، الاستعلامات المشتركة
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: maccruz
author: schmurky
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: m365-security-compliance
ms.topic: article
ms.technology: m365d
ms.openlocfilehash: 2e86d733304eeaa0e5e16f3ce1bfde87c21258d4
ms.sourcegitcommit: 9ba00298cfa9ae293e4a57650965fdb3e8ffe07b
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/11/2022
ms.locfileid: "64761595"
---
# <a name="use-shared-queries-in-advanced-hunting"></a>استخدام الاستعلامات المشتركة في التتبع المتقدم

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**ينطبق على:**
- Microsoft 365 Defender
- Microsoft Defender for Endpoint

يمكن مشاركة استعلامات [التتبع المتقدمة](advanced-hunting-overview.md) بين المستخدمين في نفس المؤسسة. يمكنك أيضا حفظ الاستعلامات التي لا يمكن الوصول إليها إلا لك. يمكنك أيضا العثور على استعلامات المجتمع التي تتم مشاركتها بشكل عام على GitHub. تتيح لك هذه الاستعلامات المحفوظة متابعة سيناريوهات محددة لتتبع المخاطر بسرعة دون الحاجة إلى كتابة الاستعلامات من البداية.

ضمن علامة التبويب "استعلامات" في التتبع المتقدم، يمكنك العثور على القوائم المنسدلة **للاستعلامات المشتركة** **والاستعلامات الخاصة بي** **واستعلامات المجتمع**. يمكنك تحديد سهم متجه لأسفل لتوسيع قائمة.


:::image type="content" source="../../media/advanced-hunting-shared-queries-1.png" alt-text="الاستعلامات المشتركة والاستعلامات الخاصة بي واستعلامات المجتمع في مدخل Microsoft 365 Defender" lightbox="../../media/advanced-hunting-shared-queries-1.png":::



## <a name="save-modify-and-share-a-query"></a>حفظ استعلام وتعديله ومشاركته
يمكنك حفظ استعلام جديد أو موجود بحيث لا يمكن الوصول إليه إلا لك أو مشاركته مع مستخدمين آخرين في مؤسستك. 

1. إنشاء استعلام أو تعديله. 

2. انقر فوق الزر المنسدلة **"حفظ استعلام****" وحدد "حفظ باسم**".
    
3. أدخل اسما للاستعلام. 

   :::image type="content" source="../../media/shared-query-2.png" alt-text="الاستعلام الجديد الذي على وشك الحفظ في مدخل Microsoft 365 Defender" lightbox="../../media/shared-query-2.png":::

4. حدد المجلد حيث تريد حفظ الاستعلام.
    - **الاستعلامات المشتركة** — المشتركة مع جميع المستخدمين في مؤسستك
    - **الاستعلامات الخاصة بي** — يمكن الوصول إليها فقط من قبلك
    
5. حدد **"حفظ**". 

## <a name="delete-or-rename-a-query"></a>حذف استعلام أو إعادة تسميته
1. حدد النقاط الثلاث إلى يمين استعلام تريد إعادة تسميته أو حذفه.

    :::image type="content" source="../../media/advanced-hunting-del-save-query.png" alt-text="إعادة تسمية استعلام أو حذفه في صفحة التتبع المتقدم في مدخل Microsoft 365 Defender" lightbox="../../media/advanced-hunting-del-save-query.png":::

2. حدد **"حذف** " وتأكد من الحذف. أو حدد **"إعادة تسمية"** وقم بتوفير اسم جديد للاستعلام.

## <a name="create-a-direct-link-to-a-query"></a>إنشاء ارتباط مباشر لاستعلام
لإنشاء ارتباط يفتح الاستعلام مباشرة في محرر استعلام التتبع المتقدم، قم بإنهاء الاستعلام وحدد **مشاركة الارتباط**.

## <a name="access-community-queries-in-the-github-repo"></a>الوصول إلى استعلامات المجتمع في مستودع GitHub  
يشارك باحثو أمان Microsoft بانتظام استعلامات التتبع المتقدمة في [مستودع عام معين على GitHub](https://github.com/Azure/Azure-Sentinel/tree/master/Hunting%20Queries/Microsoft%20365%20Defender). تتم مراجعة المساهمات في هذا المستودع قبل نشرها. للمساهمة، [انضم إلى GitHub مجانا](https://github.com/).

يمكنك بسهولة العثور على هذه الاستعلامات في القائمة المنسدلة **استعلامات المجتمع** أيضا.

:::image type="content" source="../../media/advanced-hunting-shared-queries-2.png" alt-text="استعلامات المجتمع المنظمة حسب المجلد في مدخل Microsoft 365 Defender" lightbox="../../media/advanced-hunting-shared-queries-2.png":::

يتم تجميع استعلامات المجتمع في مجلدات مثل *الحملات*، *والتجميع*، *والتهرب الدفاعي*، وما إلى ذلك. يتم توفير مزيد من المعلومات حول الاستعلام كتعليقات سطرية في الاستعلام نفسه. 

>[!tip]
>يوفر باحثو أمان Microsoft أيضا استعلامات تتبع متقدمة يمكنك استخدامها لتحديد الأنشطة والمؤشرات المرتبطة بالتهديدات الناشئة. يتم توفير هذه الاستعلامات كجزء من تقارير [تحليلات المخاطر](/windows/security/threat-protection/microsoft-defender-atp/threat-analytics) في Microsoft 365 Defender.


## <a name="related-topics"></a>المواضيع ذات الصلة
- [نظرة عامة متقدمة حول الصيد](advanced-hunting-overview.md)
- [التعرّف على لغة الاستعلام](advanced-hunting-query-language.md)
- [استخدام نتائج الاستعلام](advanced-hunting-query-results.md)
- [البحث عبر الأجهزة ورسائل البريد الإلكتروني والتطبيقات والهويات](advanced-hunting-query-emails-devices.md)
- [فهم المخطط](advanced-hunting-schema-tables.md)
- [تطبيق أفضل ممارسات الاستعلام](advanced-hunting-best-practices.md)