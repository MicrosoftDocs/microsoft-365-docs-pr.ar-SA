---
title: كيفية استخدام Power Automate موصل لإعداد Flow الأحداث
ms.reviewer: ''
description: استخدم Microsoft Defender لنقطة النهاية Flow موصل لإنشاء تدفق سيتم تشغيله في أي وقت يقع فيه حدث جديد على المستأجر.
keywords: تدفق، apis المعتمدة، api، تدفق Microsoft، الاستعلام، التنفيذ التلقائي، الطاقة التلقائية
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
ms.topic: how-to
MS.technology: mde
ms.custom: api
ms.openlocfilehash: fdb3876de6f74c95858dee01aba9615198282b16
ms.sourcegitcommit: bcea69bacd1b48827bd60af2880909593a1609a4
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 01/25/2022
ms.locfileid: "63572268"
---
# <a name="how-to-use-power-automate-connector-to-set-up-a-flow-for-events"></a>كيفية استخدام Power Automate موصل لإعداد Flow الأحداث

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**
- [خطة Microsoft Defender لنقطة النهاية 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)


> هل تريد تجربة Microsoft Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)


إن أتمتة إجراءات الأمان هو أحد المتطلبات القياسية لكل مركز عمليات أمان حديث (SOC). لكي تعمل فرق SOC بالطريقة الأكثر فعالية، يجب التنفيذ التلقائي. استخدم Microsoft Power Automate لمساعدتك على إنشاء مهام سير عمل تلقائية وإنشاء تنفيذ تلقائي للإجراءات من النهاية إلى النهاية في غضون دقائق قليلة. تدعم Power Automate Microsoft الموصلات المختلفة التي تم إنشاؤها بالضبط لذلك.  

استخدم هذه المقالة لإرشادك في إنشاء عمليات تلقائية يتم تشغيلها بواسطة حدث، على النحو المثال عند إنشاء تنبيه جديد في المستأجر. لدى Microsoft Defender API Power Automate موصل رسمي مع العديد من الإمكانات. 



:::image type="content" alt-text="صورة لتحرير بيانات الاعتماد1." source="images/api-flow-0.png":::

> [!NOTE]
> لمزيد من التفاصيل حول متطلبات ترخيص الموصلات المتميزة، راجع [ترخيص الموصلات المتميزة](/power-automate/triggers-introduction#licensing-for-premium-connectors).


## <a name="usage-example"></a>مثال على الاستخدام

يوضح المثال التالي كيفية إنشاء Flow يتم تشغيلها في أي وقت يتم فيه تشغيل تنبيه جديد على المستأجر. سيتم إرشادك حول تحديد الحدث الذي يبدأ التدفق والخطوة التالية التي سيتم اتخاذها عند حدوث ذلك المشغل.  

1. سجل دخولك إلى [Microsoft Power Automate](https://flow.microsoft.com).

2. انتقل إلى **تدفقاتي** \> **تلقائية** \> **جديدة من فارغة**.

    :::image type="content" alt-text="صورة لتحرير بيانات الاعتماد2." source="images/api-flow-1.png":::

3. اختر اسما لمشغل Flow، وابحث عن "مشغلات MICROSOFT Defender ATP" كمشغل، ثم حدد مشغل التنبيهات الجديد.

    :::image type="content" alt-text="صورة لتحرير بيانات الاعتماد3." source="images/api-flow-2.png":::

لديك الآن Flow يتم تشغيلها في كل مرة يحدث فيها تنبيه جديد.

:::image type="content" alt-text="صورة لتحرير بيانات الاعتماد4." source="images/api-flow-3.png":::

كل ما عليك فعله الآن هو اختيار الخطوات التالية.
على سبيل المثال، يمكنك عزل الجهاز إذا كانت خطورة التنبيه عالية وإرسال رسالة بريد إلكتروني حوله.
يوفر مشغل "التنبيه" فقط "لمعر التنبيه" و"الماينت". يمكنك استخدام الموصل لتوسيع هذه الوحدات.

### <a name="get-the-alert-entity-using-the-connector"></a>الحصول على كيان التنبيه باستخدام الموصل

1. اختر **Microsoft Defender ATP** للخطوة الجديدة.

2. اختر **تنبيهات - احصل على API تنبيه واحد**.

3. قم بتعيين **"معر ى التنبيه** " من الخطوة **الأخيرة كمدخل**.

    :::image type="content" alt-text="صورة لتحرير بيانات الاعتماد5." source="images/api-flow-4.png" lightbox="images/api-flow-4.png":::

### <a name="isolate-the-device-if-the-alerts-severity-is-high"></a>عزل الجهاز إذا كانت خطورة التنبيه عالية

1. إضافة **شرط** كخطوة جديدة.

2. تحقق مما إذا كانت خطورة التنبيه **مساوية للأعلى** .

   إذا كانت الإجابة بنعم، أضف **الإجراء ATP ل Microsoft Defender - عزل** الجهاز باستخدام "الماكرو" وتعليق.

    :::image type="content" alt-text="صورة لتحرير بيانات الاعتماد6." source="images/api-flow-5.png" lightbox="images/api-flow-5.png":::

3. أضف خطوة جديدة للبريد الإلكتروني حول التنبيه والعزل. هناك عدة موصلات بريد إلكتروني سهلة الاستخدام، مثل Outlook Gmail.

4. احفظ التدفق.

يمكنك أيضا **إنشاء تدفق** مجدول يقوم بتشغيل استعلامات "البحث المتقدم" والمزيد!

## <a name="related-topic"></a>موضوع ذو صلة
- [واجهات برمجة تطبيقات Microsoft Defender لنقطة النهاية](apis-intro.md)
