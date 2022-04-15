---
title: الاستفادة من تصنيف مخزن المصطلحات عند إنشاء مستخرج في Microsoft SharePoint Syntex
ms.author: chucked
author: chuckedmonson
manager: pamgreen
ms.reviewer: ssquires
audience: admin
ms.topic: article
ms.prod: microsoft-365-enterprise
search.appverid: ''
ms.collection:
- enabler-strategic
- m365initiative-syntex
ms.custom: admindeeplinkSPO
ms.localizationpriority: medium
description: استخدم تصنيف مخزن المصطلحات عند إنشاء مستخرج في نموذج فهم المستند في Microsoft SharePoint Syntex.
ms.openlocfilehash: d3f2acf32231558f9f56a62b18c6dd7ffbc4e20f
ms.sourcegitcommit: e3bc6563037bd2cce2abf108b3d1bcc2ccf538f6
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/15/2022
ms.locfileid: "64861477"
---
# <a name="leverage-term-store-taxonomy-when-creating-an-extractor-in-microsoft-sharepoint-syntex"></a>الاستفادة من تصنيف مخزن المصطلحات عند إنشاء مستخرج في Microsoft SharePoint Syntex

</br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4GpJJ]  

</br>

عند إنشاء مستخرج في نموذج فهم المستند باستخدام SharePoint Syntex، يمكنك الاستفادة من مجموعات المصطلحات العمومية في [مخزن المصطلحات](/sharepoint/managed-metadata) لعرض المصطلحات المفضلة للبيانات التي تقوم باستخراجها.  

على سبيل المثال، يحدد النموذج كل مستندات **العقد** التي يتم تحميلها إلى مكتبة المستندات ويصنفها.  بالإضافة إلى ذلك، يستخرج النموذج أيضا قيمة **Contract Service** من كل عقد، وسيعرضها في عمود في طريقة عرض المكتبة. من بين قيم Contract Services المختلفة في العقود، هناك العديد من القيم القديمة التي لم تعد تستخدمها شركتك وتمت إعادة تسميتها. على سبيل المثال، يجب الآن تسمية جميع المراجع إلى شروط خدمات تعاقد *التصميم* *أو الرسومات* أو *الطبولوجيا* باسم *Creative*. كلما استخرج نموذجك أحد الشروط القديمة من مستند العقد، تريد أن يعرض المصطلح الحالي - Creative - في طريقة عرض المكتبة. في المثال أدناه، أثناء تدريب النموذج، نرى أن نموذج مستند واحد يحتوي على المصطلح القديم *للتصميم*.

   ![مخزن المصطلحات.](../media/content-understanding/design.png)</br>

## <a name="use-a-managed-metadata-column-in-your-extractor"></a>استخدام عمود بيانات تعريف مدارة في المستخرج

يتم تكوين مجموعات المصطلحات في مخزن مصطلحات خدمات بيانات التعريف المدارة (MMS) في <a href="https://go.microsoft.com/fwlink/?linkid=2185219" target="_blank">مركز إدارة SharePoint</a>. في المثال أدناه، تم تكوين [مجموعة مصطلحات](/sharepoint/managed-metadata#term-set) *Contract Services* لتضمين عدة شروط، بما في ذلك *Creative*.  توضح التفاصيل الخاصة به أن المصطلح يحتوي على ثلاثة مرادفات (*التصميم* *والرسومات* *والمخططات*) ويجب ترجمة المرادفات إلى *Creative*. 

   ![مجموعة المصطلحات.](../media/content-understanding/term-store.png)</br>

قد يكون هناك العديد من الأسباب التي قد تجعلك ترغب في استخدام مرادف في مجموعة المصطلحات. على سبيل المثال، قد تكون هناك مصطلحات قديمة أو مصطلحات تمت إعادة تسميتها أو تباينات بين أقسام المؤسسات عند التسمية.

لجعل حقل بيانات التعريف المدارة متوفرا للتحديد عند إنشاء مستخرج في النموذج الخاص بك، تحتاج إلى [إضافته كعمود موقع بيانات التعريف المدارة](https://support.microsoft.com/office/8fad9e35-a618-4400-b3c7-46f02785d27f). بعد إضافة عمود الموقع، يمكنك تحديده عند إنشاء المستخرج للنموذج الخاص بك.

   ![خدمة العقد.](../media/content-understanding/contract-services.png)</br>

بعد تطبيق النموذج على مكتبة المستندات، عند تحميل المستندات إلى المكتبة، سيعرض عمود *Creative Services* المصطلح المفضل (*Creative*) عندما يعثر المستخرج على أي من قيم المرادفات (*التصميم* *والرسومات* *والمخططات*).

   ![عمود خدمة العقد.](../media/content-understanding/creative.png)</br>

> [!NOTE]
> إذا كانت مجموعة المصطلحات مفتوحة، فستتم إضافة أي قيم مستخرجة لا تتطابق مع مصطلح مفضل أو قيمة مرادفة كمصطلح جديد إلى جذر مجموعة المصطلحات. يمكن نقل هذه المصطلحات الجديدة أو دمجها أو جعلها مرادفات في مخزن المصطلحات حيث توجد مجموعة المصطلحات.

## <a name="see-also"></a>راجع أيضًا
[مقدمة حول بيانات التعريف المدارة](/sharepoint/managed-metadata#terms)

[إنشاء مستخرج](create-an-extractor.md)

[إنشاء عمود بيانات تعريف مدارة](https://support.microsoft.com/office/create-a-managed-metadata-column-8fad9e35-a618-4400-b3c7-46f02785d27f?redirectSourcePath=%252farticle%252fc2a06717-8105-4aea-890d-3082853ab7b7&ui=en-US&rs=en-US&ad=US)