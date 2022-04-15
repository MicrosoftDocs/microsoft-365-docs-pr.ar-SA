---
title: التقارير في Microsoft Defender for Business
description: احصل على نظرة عامة حول التقارير المتوفرة في Microsoft Defender for Business
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: overview
ms.date: 04/12/2022
ms.prod: m365-security
ms.technology: mdb
ms.localizationpriority: medium
ms.reviewer: shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
ms.openlocfilehash: 3e2b6c8258f6a08c4cbb727c234871788242c6c2
ms.sourcegitcommit: e3bc6563037bd2cce2abf108b3d1bcc2ccf538f6
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/15/2022
ms.locfileid: "64862137"
---
# <a name="reports-in-microsoft-defender-for-business"></a>التقارير في Microsoft Defender for Business

> [!NOTE]
> تم تضمين Microsoft Defender for Business الآن في [Microsoft 365 Business Premium](../../business-premium/index.md). 

تتوفر العديد من التقارير في مدخل Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)). تصف هذه المقالة هذه التقارير وكيفية استخدامها وكيفية العثور عليها.

## <a name="reports-in-defender-for-business"></a>التقارير في Defender for Business

|تقرير  |الوصف  |
|---------|---------|
| **تقرير الأمان**  | يوفر تقرير الأمان معلومات حول هويات شركتك وأجهزتها وتطبيقاتها. للوصول إلى هذا التقرير، في جزء التنقل، اختر **تقرير** **ReportsGeneralSecurity** >  > . <br/><br/>**تلميح** يمكنك عرض معلومات مماثلة على الصفحة الرئيسية لمدخل Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)). |
| **الحماية من التهديدات**  | يوفر تقرير الحماية من التهديدات معلومات حول التنبيهات واتجاهات التنبيه. استخدم عمود **اتجاهات التنبيه** لعرض معلومات حول التنبيهات التي تم تشغيلها خلال آخر 30 يوما. استخدم عمود **حالة التنبيه** لعرض معلومات اللقطة الحالية حول التنبيهات، مثل فئات التنبيهات التي لم يتم حلها وتصنيفها. للوصول إلى هذا التقرير، في جزء التنقل، اختر **حماية** **ReportsEndpointsThreat** >  > . <br/><br/>**تلميح**: يمكنك أيضا استخدام قائمة **الحوادث** لعرض معلومات حول التنبيهات. في جزء التنقل، اختر **"الحوادث** " لعرض الحوادث الحالية وإدارتها. لمعرفة المزيد، راجع [عرض الحوادث وإدارتها في Microsoft Defender for Business](mdb-view-manage-incidents.md). |
| **سلامة الجهاز وتوافقه** | يوفر تقرير سلامة الجهاز وتوافقه معلومات حول صحة الجهاز واتجاهاته. يمكنك استخدام هذا التقرير لتحديد ما إذا كانت أدوات استشعار Defender for Business تعمل بشكل صحيح على الأجهزة والحالة الحالية برنامج الحماية من الفيروسات من Microsoft Defender. للوصول إلى هذا التقرير، في جزء التنقل، اختر **«****ReportsEndpointsDevice** >  >  **health and compliance**». <br/><br/>**تلميح**: يمكنك استخدام قائمة **مخزون الأجهزة** لعرض معلومات حول أجهزة شركتك. في جزء التنقل، اختر **"مخزون الجهاز**". لمعرفة المزيد، راجع [إدارة الأجهزة في Microsoft Defender for Business](mdb-manage-devices.md). |
| **الأجهزة المعرضة للخطر** | يوفر تقرير الأجهزة المعرضة للخطر معلومات حول الأجهزة والاتجاهات. استخدم العمود **Trends** لعرض معلومات حول الأجهزة التي تحتوي على تنبيهات على مدار آخر 30 يوما. استخدم عمود **الحالة** لعرض معلومات اللقطة الحالية حول الأجهزة التي تحتوي على تنبيهات. للوصول إلى هذا التقرير، في جزء التنقل، اختر أجهزة **ReportsEndpointsVulnerable** >  > .<br/><br/>**تلميح**: يمكنك استخدام قائمة **مخزون الأجهزة** لعرض معلومات حول أجهزة شركتك. في جزء التنقل، اختر **"مخزون الجهاز**". لمعرفة المزيد، راجع [إدارة الأجهزة في Microsoft Defender for Business](mdb-manage-devices.md). |
| **حماية ويب** | يعرض تقرير حماية الويب محاولات الوصول إلى مواقع التصيد الاحتيالي، ونواقل البرامج الضارة، ومواقع الاستغلال، والمواقع غير الموثوق بها أو ذات السمعة المنخفضة، والمواقع المحظورة بشكل صريح. تتضمن فئات المواقع المحظورة محتوى البالغين ومواقع الترفيه ومواقع المسؤولية القانونية والمزيد. للوصول إلى هذا التقرير، في جزء التنقل، اختر **حماية** **ReportsEndpointsWeb** >  > .<br/><br/>**تلميح**: إذا لم تكن قد قمت بتكوين حماية الويب لشركتك بعد، فاختر زر **الإعدادات** في طريقة عرض التقرير. ثم، ضمن **"القواعد**"، اختر **تصفية محتوى ويب**. لمعرفة المزيد حول تصفية محتوى ويب، راجع [تصفية محتوى ويب](../defender-endpoint/web-content-filtering.md). |

>
> **هل لديك دقيقة؟**
> يرجى أخذ <a href="https://microsoft.qualtrics.com/jfe/form/SV_0JPjTPHGEWTQr4y" target="_blank">استطلاعنا القصير حول الأمان</a>. يسعدنا أن نستمع إليك!
>

## <a name="see-also"></a>راجع أيضًا

- [بدء استخدام Microsoft Defender for Business](mdb-get-started.md)
- [عرض الحوادث وإدارتها في Microsoft Defender for Business](mdb-view-manage-incidents.md)
- [إدارة الأجهزة في Microsoft Defender for Business](mdb-manage-devices.md)