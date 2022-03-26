---
title: يمكنك الاستفادة من مستخرج مخزن المصطلحات عند إنشاء مستخرج في Microsoft SharePoint Syntex
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
description: استخدم مستخرج مخزن المصطلحات عند إنشاء مستخرج في نموذج فهم المستند في Microsoft SharePoint Syntex.
ms.openlocfilehash: 909f26026ddf26163a12e1d14c1790f4af93a160
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/08/2022
ms.locfileid: "63569051"
---
# <a name="leverage-term-store-taxonomy-when-creating-an-extractor-in-microsoft-sharepoint-syntex"></a>يمكنك الاستفادة من مستخرج مخزن المصطلحات عند إنشاء مستخرج في Microsoft SharePoint Syntex

</br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4GpJJ]  

</br>

عند إنشاء مستخرج في نموذج فهم المستند باستخدام SharePoint Syntex، يمكنك الاستفادة من مجموعات المصطلحات العالمية في مخزن المصطلحات لعرض المصطلحات المفضلة [](/sharepoint/managed-metadata) للبيانات التي تستخرجها.  

على سبيل المثال، يحدد النموذج كل مستندات العقد التي يتم تحميلها إلى  مكتبة المستندات ويصنفها.  بالإضافة إلى ذلك، يستخرج النموذج أيضا قيمة **خدمة** التعاقد من كل عقد، وسيعرضها في عمود في طريقة عرض المكتبة. من بين قيم خدمات التعاقدات المتعددة في العقود، هناك العديد من القيم القديمة التي لم تعد شركتك تستخدمها وقد تمت إعادة تسميتها. على سبيل المثال، يجب أن تسمى كل المراجع إلى مصطلحات تصميم أو رسومات أو  خدمات عقود طبوغرافيا الآن باسم *Creative*. عندما يستخرج النموذج أحد المصطلحات القديمة من مستند عقد، تريد أن يعرض المصطلح الحالي - الإبداعي - في طريقة عرض المكتبة. في المثال أدناه، أثناء تدريب النموذج، سنرى أن نموذج مستند واحد يحتوي على مصطلح تصميم *قديم.*

   ![مخزن المصطلحات.](../media/content-understanding/design.png)</br>

## <a name="use-a-managed-metadata-column-in-your-extractor"></a>استخدام عمود بيانات التعريف المدارة في المستخرج

يتم تكوين مجموعات المصطلحات في مخزن المصطلحات خدمات بيانات التعريف المدارة (MMS) SharePoint <a href="https://go.microsoft.com/fwlink/?linkid=2185219" target="_blank">مركز الإدارة</a>. في المثال أدناه، تم تكوين مجموعة مصطلحات *خدمات* [](/sharepoint/managed-metadata#term-set) التعاقد لتضمين عدة شروط، بما في ذلك *Creative*.  تظهر التفاصيل الخاصة به أن المصطلح له ثلاثة مرادفات *(التصميم* والرسومات والتضاريس *) ويجب* ترجمة المرادفات إلى *Creative*. 

   ![مجموعة المصطلحات.](../media/content-understanding/term-store.png)</br>

قد يكون هناك العديد من الأسباب التي قد تدعوك إلى استخدام مرادف في مجموعة المصطلحات. على سبيل المثال، قد تكون هناك مصطلحات قديمة أو مصطلحات أعيدت تسميتها أو تباينات بين أقسام المؤسسة عند التسمية.

لجعل حقل بيانات التعريف المدارة متوفرا لتحديد وقت إنشاء المستخرج في النموذج، ستحتاج إلى إضافته [كعمود موقع بيانات تعريف مدارة](https://support.microsoft.com/office/8fad9e35-a618-4400-b3c7-46f02785d27f). بعد إضافة عمود الموقع، يمكنك تحديده عند إنشاء المستخرج للنموذج.

   ![خدمة التعاقد.](../media/content-understanding/contract-services.png)</br>

بعد تطبيق النموذج على مكتبة المستندات، عند تحميل المستندات إلى المكتبة، سيعرض العمود Creative *Services* المصطلح *المفضل (Creative*) عندما يعثر المستخرج على أي من قيم المرادفات *(تصميم* ورسومات وتبوغرافيا *).*

   ![عمود خدمة التعاقد.](../media/content-understanding/creative.png)</br>


## <a name="see-also"></a>انظر أيضاً
[مقدمة حول بيانات التعريف المدارة](/sharepoint/managed-metadata#terms)

[إنشاء مستخرج](create-an-extractor.md)

[إنشاء عمود بيانات تعريف مدارة](https://support.microsoft.com/office/create-a-managed-metadata-column-8fad9e35-a618-4400-b3c7-46f02785d27f?redirectSourcePath=%252farticle%252fc2a06717-8105-4aea-890d-3082853ab7b7&ui=en-US&rs=en-US&ad=US)