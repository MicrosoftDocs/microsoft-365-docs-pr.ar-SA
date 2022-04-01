---
title: استخدام الاستعلامات المشتركة في Microsoft 365 Defender البحث المتقدم
description: ابدأ بالصيد الفوري للتهديدات باستخدام استعلامات محددة مسبقا ومشتركة. شارك الاستعلامات إلى الجمهور أو إلى مؤسستك.
keywords: الصيد المتقدم، وصيد التهديدات، وصيد التهديدات الإلكترونية، و Microsoft 365 Defender، و microsoft 365، و m365، و البحث، و الاستعلام، و بيانات التعقب، و عمليات الكشف المخصصة، و المخطط، و kusto، و github repo، والاستعلامات، والاستعلامات المشتركة
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
ms.openlocfilehash: 96db917808094487039a13740cba80ad751f062f
ms.sourcegitcommit: d32654bdfaf08de45715dd362a7d42199bdc1ee7
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/23/2022
ms.locfileid: "63755515"
---
# <a name="use-shared-queries-in-advanced-hunting"></a>استخدام الاستعلامات المشتركة في البحث المتقدم

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**ينطبق على:**
- Microsoft 365 Defender
- Microsoft Defender لنقطة النهاية



[يمكن مشاركة استعلامات](advanced-hunting-overview.md) الصيد المتقدمة بين المستخدمين في المؤسسة نفسها. يمكنك أيضا العثور على الاستعلامات المشتركة بشكل عام على GitHub. تسمح لك هذه الاستعلامات بمتابعة سيناريوهات معينة خاصة بالصيد دون الحاجة إلى كتابة الاستعلامات من البداية.

:::image type="content" source="../../media/shared-query-1.png" alt-text="معلومات الاستعلامات المشتركة في مدخل Microsoft 365 Defender" lightbox="../../media/shared-query-1.png":::

## <a name="save-modify-and-share-a-query"></a>حفظ استعلام وتعديله ومشاركته
يمكنك حفظ استعلام جديد أو موجود بحيث يمكن الوصول إليه من قبلك فقط أو مشاركته مع مستخدمين آخرين في مؤسستك. 

1. إنشاء استعلام أو تعديله. 

2. انقر فوق **الزر المنسدل** حفظ الاستعلام وحدد **حفظ باسم**.
    
3. أدخل اسما للاستعلام. 

   :::image type="content" source="../../media/shared-query-2.png" alt-text="الاستعلام الجديد الذي على وشك أن يتم حفظه في مدخل Microsoft 365 Defender" lightbox="../../media/shared-query-2.png":::

4. حدد المجلد الذي تريد حفظ الاستعلام فيه.
    - **الاستعلامات المشتركة** — المشتركة لجميع المستخدمين في مؤسستك
    - **الاستعلامات الخاصة بى** — يمكن الوصول إليها من قبلك فقط
    
5. حدد **حفظ**. 

## <a name="delete-or-rename-a-query"></a>حذف استعلام أو إعادة تسميته
1. حدد النقاط الثلاث إلى يمين الاستعلام الذي تريد إعادة تسميته أو حذفه.

    :::image type="content" source="../../media/shared-query-3.png" alt-text="خيارات استعلام مشترك في صفحة &quot;الصيد المتقدم&quot; في مدخل Microsoft 365 Defender" lightbox="../../media/shared-query-3.png":::

2. حدد **حذف** وأكد الحذف. أو حدد **إعادة تسمية** وأقدم اسما جديدا للاستعلام.

## <a name="create-a-direct-link-to-a-query"></a>إنشاء ارتباط مباشر إلى استعلام
لإنشاء ارتباط يفتح الاستعلام مباشرة في محرر استعلام البحث المتقدم، قم بوضع اللمسات الأخيرة على الاستعلام وحدد **مشاركة الارتباط**.

## <a name="access-queries-in-the-github-repository"></a>استعلامات الوصول في مستودع GitHub  
يشارك الباحثون في مجال الأمان من Microsoft بشكل منتظم استعلامات الصيد المتقدمة في مستودع عام معين [على GitHub](https://aka.ms/hunting-queries). هذا المستودع مفتوح للمساهمات. للمساهمة، [انضم GitHub مجانا](https://github.com/).

>[!tip]
>يوفر الباحثون في مجال الأمان من Microsoft أيضا استعلامات بحث متقدمة يمكنك استخدامها لتحديد موقع الأنشطة والمؤشرات المقترنة بالتهيؤات الناشئة. يتم توفير هذه الاستعلامات [كجزء من تقارير](/windows/security/threat-protection/microsoft-defender-atp/threat-analytics) تحليل المخاطر في Microsoft 365 Defender.


## <a name="related-topics"></a>المواضيع ذات الصلة
- [نظرة عامة متقدمة حول الصيد](advanced-hunting-overview.md)
- [تعرف على لغة الاستعلام](advanced-hunting-query-language.md)
- [استخدام نتائج الاستعلام](advanced-hunting-query-results.md)
- [البحث عبر الأجهزة ورسائل البريد الإلكتروني والتطبيقات والهويات](advanced-hunting-query-emails-devices.md)
- [فهم المخطط](advanced-hunting-schema-tables.md)
- [تطبيق أفضل ممارسات الاستعلام](advanced-hunting-best-practices.md)