---
title: حماية مؤسستك من تهديدات الويب
description: تعرف على المزيد حول حماية الويب في Microsoft Defender ل Endpoint وكيفية حماية مؤسستك.
keywords: حماية الويب، الحماية من المخاطر على الويب، استعراض الويب، الأمان، التصيد الاحتيالي، البرامج الضارة، استغلال، مواقع الويب، حماية الشبكة، Edge، Internet Explorer، Chrome، Firefox، مستعرض ويب
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 398fdb8bbfb5bba59fce83e24e7d6cdd496e90bd
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 11/24/2021
ms.locfileid: "63583080"
---
# <a name="protect-your-organization-against-web-threats"></a>حماية مؤسستك من تهديدات الويب

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**
- [خطة Microsoft Defender لنقطة النهاية 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> هل تريد تجربة Microsoft Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-main-abovefoldlink&rtc=1)

تشكل الحماية من المخاطر على الويب جزءا من [حماية الويب](web-protection-overview.md) في Defender for Endpoint. فهو يستخدم [حماية الشبكة](network-protection.md) لحماية أجهزتك من تهديدات الويب. من خلال التكامل مع Microsoft Edge الخارجية الشائعة مثل Chrome وFirefox، توقف الحماية من المخاطر على الويب تهديدات الويب بدون وكيل ويب ويمكنها حماية الأجهزة أثناء وجودها في مكان بعيد أو في الموقع. توقف الحماية من المخاطر على الويب الوصول إلى مواقع التصيد الاحتيالي، و متجهات البرامج الضارة، والمواقع المستغلة، والمواقع غير الملوثة أو ذات السمعة المنخفضة، بالإضافة إلى المواقع التي قمت بحظرها في قائمة المؤشرات [المخصصة](manage-indicators.md).

> [!NOTE]
> قد يستغرق استلام الأجهزة لمؤشرات مخصصة جديدة ما يصل إلى ساعة واحدة.

## <a name="prerequisites"></a>المتطلبات الأساسية

تستخدم حماية الويب حماية الشبكة لتوفير أمان استعراض الويب على Microsoft Edge الويب الخارجية ومستعرضات الويب الخاصة بها.

تشغيل حماية الشبكة على أجهزتك:

- قم بتحرير الأساس أمان Defender لنقطة النهاية ضمن **حماية** & الويب لتمكين حماية الشبكة قبل نشرها أو إعادة نشرها. [تعرف على كيفية مراجعة وتعيين أساس أمان Defender لنقطة النهاية](configure-machines-security-baseline.md#review-and-assign-the-microsoft-defender-for-endpoint-security-baseline)
- تشغيل حماية الشبكة باستخدام تكوين جهاز Intune أو SCCM أو نهج المجموعة أو حل MDM. [اقرأ المزيد حول تمكين حماية الشبكة](enable-network-protection.md)

> [!NOTE]
> إذا قمت بتعيين حماية الشبكة إلى **تدقيق فقط**، لن يكون الحظر متوفرا. وستتمكن أيضا من الكشف عن محاولات الوصول إلى مواقع الويب الضارة وغير المرغوب فيها وتسجيلها Microsoft Edge فقط.

## <a name="configure-web-threat-protection"></a>تكوين الحماية من المخاطر على الويب

يصف الإجراء التالي كيفية تكوين الحماية من المخاطر على الويب باستخدام إدارة نقاط النهاية من Microsoft الإدارة.

1. انتقل إلى إدارة نقاط النهاية من Microsoft إدارة ([https://endpoint.microsoft.com](https://endpoint.microsoft.com))، ثم سجل الدخول.
 
2. اختر **الحد من مستوى** \> الهجوم الأمني **لنقطة النهاية**، ثم اختر **+ إنشاء نهج**.

3. حدد أحد الأنظمة الأساسية، مثل Windows 10 **واللاحقة**، وحدد ملف **تعريف** حماية ويب، ثم اختر **إنشاء**. 

4. على **علامة التبويب أساسيات** ، حدد اسما ووصفا، ثم اختر **التالي**.

5. على علامة **التبويب إعدادات التكوين** ، قم بتوسيع **حماية ويب**، وحدد إعداداتك، ثم اختر **التالي**.

   - تعيين **تمكين حماية الشبكة** إلى **تمكين** حتى يتم تشغيل حماية الويب. بدلا من ذلك، يمكنك تعيين حماية الشبكة إلى وضع **التدقيق** لمعرفة كيفية عملها في بيئتك. في وضع التدقيق، لا تمنع حماية الشبكة المستخدمين من زيارة المواقع أو المجالات، ولكنها تتعقب عمليات الكشف كالأحداث. 
   - لحماية المستخدمين من رسائل التصيد الاحتيالي والبرامج الضارة المحتملة، قم ب تحويل **طلب SmartScreen الإصدار القديم من Microsoft Edge** إلى **نعم**.
   - لمنع المستخدمين من تجاوز التحذيرات حول المواقع التي قد تكون ضارة، قم بتعيين **حظر الوصول إلى الموقع الضار** إلى **نعم**.
   - لمنع المستخدمين من تجاوز التحذيرات وتنزيل الملفات التي لم يتم تحديدها، قم بتعيين **حظر تنزيل** الملف الذي لم يتم تحديده tl **Yes**. 

6. على علامة **التبويب علامات** النطاق، إذا كانت مؤسستك تستخدم علامات النطاق، **فاختر + تحديد** علامات النطاق، ثم اختر **التالي**. (إذا كنت لا تستخدم علامات النطاق، فاختر **التالي**.) لمعرفة المزيد حول علامات النطاق، راجع استخدام التحكم بالوصول المستند إلى الدور (RBAC) والعلامات الخاصة بنطاق الوصول [ل IT الموزعة](/mem/intune/fundamentals/scope-tags).

7. على علامة **التبويب** الواجبات، حدد المستخدمين والأجهزة لتلقي نهج حماية الويب، ثم اختر **التالي**.

8. على علامة **التبويب مراجعة + إنشاء** ، راجع إعدادات النهج، ثم اختر **إنشاء**.

## <a name="related-topics"></a>المواضيع ذات الصلة

- [نظرة عامة حول حماية الويب](web-protection-overview.md)
- [الحماية من المخاطر على الويب](web-threat-protection.md)
- [مراقبة أمان الويب](web-protection-monitoring.md)
- [الاستجابة إلى تهديدات الويب](web-protection-response.md)
- [حماية الشبكة](network-protection.md)
