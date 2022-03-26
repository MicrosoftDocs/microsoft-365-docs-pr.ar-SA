---
title: إدارة Microsoft Defender لحوادث نقطة النهاية
description: يمكنك إدارة الأحداث من خلال تعيينها أو تحديث الحالة أو تعيين تصنيفها.
keywords: الأحداث، والإدارة، والتعيين، الحالة، والتصنيف، والتنبيه الحقيقي، والتنبيه إلى خطأ
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
- m365-initiative-defender-endpoint
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 45c08c5a3c304a23b5761d96a4d9aceb1b4f1562
ms.sourcegitcommit: 6e90baef421ae06fd790b0453d3bdbf624b7f9c0
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 02/12/2022
ms.locfileid: "63572274"
---
# <a name="manage-microsoft-defender-for-endpoint-incidents"></a>إدارة Microsoft Defender لحوادث نقطة النهاية

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**ينطبق على:**
- [خطة Microsoft Defender لنقطة النهاية 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> هل تريد تجربة Microsoft Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

تعد إدارة الأحداث جزءا مهما من كل عملية من عمليات الأمن الإلكتروني. يمكنك إدارة الأحداث عن طريق تحديد حادث من قائمة انتظار **الأحداث أو جزء** **إدارة الأحداث**. 


إن تحديد حادث من قائمة انتظار  "الأحداث" يحضر جزء إدارة الحوادث  حيث يمكنك فتح صفحة الحادث للحصول على التفاصيل.


![صورة ل جزء إدارة الأحداث.](images/atp-incidents-mgt-pane-updated.png)

يمكنك تعيين أحداث لنفسك أو تغيير الحالة والتصنيف أو إعادة التسمية أو التعليق عليها لتعقب تقدمها.

> [!TIP]
> للحصول على رؤية إضافية بنظرة سريعة، يتم تلقائيا إنشاء أسماء الأحداث استنادا إلى سمات التنبيه مثل عدد نقاط النهاية المتأثرة أو المستخدمين المتأثرين أو مصادر الكشف أو الفئات. يسمح لك ذلك بفهم نطاق الحادث بسرعة.
>
> على سبيل المثال: *حادث متعدد المراحل على نقاط نهاية متعددة تم اعجابها بواسطة مصادر متعددة.*
>
> ستحتفظ الأحداث التي كانت موجودة قبل طرح تسمية الأحداث التلقائية باسمها.
>


![صورة لصفحة تفاصيل الحادث.](images/atp-incident-details-updated.png)

## <a name="assign-incidents"></a>تعيين أحداث
إذا لم يتم تعيين حادث بعد، يمكنك تحديد **تعيين** إلي لتعيين الحادث لنفسك. ويفترض القيام بذلك ملكية ليس فقط للحادث، ولكن أيضا لكل التنبيهات المقترنة به.

## <a name="set-status-and-classification"></a>تعيين الحالة والتصنيف
### <a name="incident-status"></a>حالة الحادث
يمكنك تصنيف الأحداث **(كنشطة** أو **تم** حلها) عن طريق تغيير الحالة الخاصة بها مع تقدم التحقيق. يساعدك ذلك على تنظيم وإدارة كيفية استجابة فريقك للحوادث.

على سبيل المثال، يمكن لمحلل SoC مراجعة أحداث **Active** العاجلة لليوم، وأن يقرر تعيينها لنفسه من أجل التحقيق فيها.

بدلا من ذلك، قد يحدد محلل SoC الحادث على أنه **تم حله** إذا تم حل الحادث. 

### <a name="classification"></a>التصنيف
يمكنك اختيار عدم تعيين تصنيف، أو تحديد ما إذا كان الحادث صحيحا أو خاطئا. يساعد ذلك الفريق على رؤية الأنماط والتعلم منها.

### <a name="add-comments"></a>إضافة تعليقات
يمكنك إضافة تعليقات وعرض الأحداث التاريخية حول حادث لرؤية التغييرات السابقة التي تم إدخالها عليه.

كلما تم تغيير أو تعليق على تنبيه، يتم تسجيله في قسم التعليقات والمحفوظات.

تظهر التعليقات المضافة على الفور في الجزء.



## <a name="related-topics"></a>المواضيع ذات الصلة
- [قائمة انتظار الأحداث](/microsoft-365/security/defender-endpoint/view-incidents-queue)
- [عرض قائمة انتظار الأحداث وتنظيمها](view-incidents-queue.md)
- [التحقيق في الأحداث](investigate-incidents.md)
