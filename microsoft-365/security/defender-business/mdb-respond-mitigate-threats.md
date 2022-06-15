---
title: الاستجابة للتهديدات وتخفيفها في Microsoft Defender for Business
description: مع اكتشاف التهديدات في Defender for Business، يمكنك اتخاذ إجراءات للاستجابة لتلك التهديدات. تعرف على كيفية استخدام طريقة عرض مخزون الجهاز.
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: how-to
ms.prod: m365-security
ms.technology: mdb
ms.localizationpriority: medium
ms.reviewer: shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
- m365-initiative-defender-business
ms.openlocfilehash: b7a911991935407f9d512213c9d76c92106b74c8
ms.sourcegitcommit: 66228a5506fdceb4cbf0d55b9de3f2943740134f
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 06/15/2022
ms.locfileid: "66089551"
---
# <a name="respond-to-and-mitigate-threats-in-microsoft-defender-for-business"></a>الاستجابة للتهديدات وتخفيفها في Microsoft Defender for Business

يمكن مدخل Microsoft 365 Defender فريق الأمان من الاستجابة للتهديدات المكتشفة والتخفيف من حدتها. ترشدك هذه المقالة إلى مثال حول كيفية استخدام Defender for Business.


## <a name="view-detected-threats"></a>عرض التهديدات المكتشفة

1. انتقل إلى مدخل Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)) وسجل الدخول.

2. بطاقات الإشعارات على الصفحة الرئيسية. تخبرك البطاقات بنظرة سريعة عن عدد التهديدات التي تم اكتشافها، إلى جانب عدد حسابات المستخدمين ونقاط النهاية (الأجهزة) والأصول الأخرى التي تأثرت. الصورة التالية هي مثال على البطاقات التي قد تراها:

   :::image type="content" source="../../media/defender-business/mdb-examplecards.png" alt-text="لقطة شاشة للبطاقات في مدخل Microsoft 365 Defender":::

3. حدد زرا أو ارتباطا على البطاقة لعرض المزيد من المعلومات واتخاذ إجراء. على سبيل المثال، تتضمن بطاقة **الأجهزة المعرضة للخطر** زر **عرض التفاصيل** . يؤدي تحديد هذا الزر إلى أخذنا إلى صفحة **مخزون الجهاز** ، كما هو موضح في الصورة التالية:

   :::image type="content" source="../../media/defender-business/mdb-deviceinventory.png" alt-text="لقطة شاشة لمخزون الجهاز":::

   تسرد صفحة **مخزون الجهاز** أجهزة الشركة، إلى جانب مستوى المخاطر ومستوى التعرض لها.

4. حدد عنصرا، مثل جهاز. يفتح جزء قائمة منبثقة ويعرض المزيد من المعلومات حول التنبيهات والحوادث التي تم إنشاؤها لهذا العنصر، كما هو موضح في الصورة التالية:  

   :::image type="content" source="../../media/defender-business/mdb-deviceinventory-selecteddeviceflyout.png" alt-text="لقطة شاشة لجزء القائمة المنبثقة لجهاز محدد":::

5. في القائمة المنبثقة، اعرض المعلومات المعروضة. حدد علامة الحذف (...) لفتح قائمة تسرد الإجراءات المتوفرة، كما هو موضح في الصورة التالية: 

   :::image type="content" source="../../media/defender-business/mdb-deviceinventory-selecteddeviceflyout-menu.png" alt-text="لقطة شاشة للإجراءات المتوفرة لجهاز محدد":::

6. حدد إجراء متوفرا. على سبيل المثال، يمكنك اختيار **تشغيل فحص مكافحة الفيروسات**، مما سيؤدي إلى برنامج الحماية من الفيروسات من Microsoft Defender لبدء فحص سريع على الجهاز. أو، يمكنك تحديد **بدء التحقيق التلقائي** لتشغيل تحقيق تلقائي على الجهاز.

## <a name="next-steps"></a>الخطوات التالية

- [مراجعة إجراءات المعالجة في مركز الصيانة](mdb-review-remediation-actions.md)
- [إدارة الأجهزة في Microsoft Defender for Business](mdb-manage-devices.md)
- [عرض الحوادث وإدارتها في Microsoft Defender for Business](mdb-view-manage-incidents.md)
