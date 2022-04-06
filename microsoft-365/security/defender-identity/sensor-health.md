---
title: Microsoft Defender for Identity وإعدادات أدوات الاستشعار في Microsoft 365 Defender
description: تعرف على كيفية Microsoft Defender for Identity أدوات الاستشعار ومراقبة صحتها في Microsoft 365 Defender
ms.date: 06/07/2021
ms.topic: how-to
author: dcurwin
ms.author: dacurwin
ms.service: microsoft-defender-for-identity
ms.custom: admindeeplinkDEFENDER
manager: raynew
ms.collection: M365-security-compliance
ms.openlocfilehash: 246fd5ca880ca2d7e187283d06f19d071f5d7e0e
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/25/2022
ms.locfileid: "64468512"
---
# <a name="microsoft-defender-for-identity-sensor-health-and-settings-in-microsoft-365-defender"></a>Microsoft Defender for Identity وإعدادات أدوات الاستشعار في Microsoft 365 Defender

**ينطبق على:**

- Microsoft 365 Defender
- Defender for Identity

تشرح هذه المقالة كيفية تكوين أدوات استشعار Microsoft Defender for Identity [](/defender-for-identity) ومراقبتها [في Microsoft 365 Defender](/microsoft-365/security/defender/overview-security-center).

>[!IMPORTANT]
>كجزء من عملية التحقق من Microsoft 365 Defender، تغيرت بعض الخيارات والتفاصيل من موقعها في مدخل Defender for Identity. الرجاء قراءة التفاصيل أدناه لاكتشاف مكان العثور على كل من الميزات المألوفة والميزات الجديدة.

## <a name="view-defender-for-identity-sensor-settings-and-status"></a>عرض إعدادات أدوات استشعار الهوية ل Defender for Identity (عرض Defender for Identity sensor) ووضعها

1. في <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender</a>، **انتقل إلى الإعدادات** ثم **الهويات**.

   :::image type="content" source="../../media/defender-identity/settings-identities.png" alt-text="خيار الهويات على الإعدادات الصفحة" lightbox="../../media/defender-identity/settings-identities.png":::

1. حدد صفحة **أدوات الاستشعار** ، التي تعرض كل أدوات الاستشعار الخاصة ب Defender for Identity. لكل مستشعر، سترى اسمه وعضوية مجاله، رقم الإصدار، إذا كان يجب تأخير التحديثات، حالة الخدمة، حالة التحديث، حالة الصحة، عدد المشاكل الصحية، ومتى تم إنشاء المستشعر.

    [![صفحة المستشعر.](../../media/defender-identity/sensor-page.png)](../../media/defender-identity/sensor-page.png#lightbox)

    >[!NOTE]
    >في مدخل Defender for Identity، كانت إعدادات المستشعر ومعلومات الصحة في مواقع منفصلة. لاحظ أنه Microsoft 365 Defender في نفس الصفحة.

1. إذا حددت **عوامل التصفية**، يمكنك اختيار عوامل التصفية التي ستتوفر. بعد ذلك، مع كل عامل تصفية، يمكنك اختيار أدوات الاستشعار التي تريد عرضها.

    [![عوامل تصفية المستشعر.](../../media/defender-identity/sensor-filters.png)](../../media/defender-identity/sensor-filters.png#lightbox)

    :::image type="content" source="../../media/defender-identity/filtered-sensor.png" alt-text="المستشعر الذي تمت تصفيته" lightbox="../../media/defender-identity/filtered-sensor.png":::

1. إذا قمت بتحديد أحد أدوات الاستشعار، سيتم عرض جزء مع معلومات حول المستشعر ووضعه الصحي.

    [![تفاصيل المستشعر.](../../media/defender-identity/sensor-details.png)](../../media/defender-identity/sensor-details.png#lightbox)

1. إذا قمت بتحديد أي من مشاكل الصحة، ستحصل على جزء مع مزيد من التفاصيل حولها. إذا اخترت مشكلة مغلقة، يمكنك إعادة فتحها من هنا.

   :::image type="content" source="../../media/defender-identity/issue-details.png" alt-text="تفاصيل المشكلة" lightbox="../../media/defender-identity/issue-details.png":::
    

1. إذا حددت **إدارة المستشعر**، سيتم فتح جزء حيث يمكنك تكوين تفاصيل المستشعر.

   :::image type="content" source="../../media/defender-identity/manage-sensor.png" alt-text="الخيار &quot;إدارة المستشعر&quot;" lightbox="../../media/defender-identity/manage-sensor.png":::

   :::image type="content" source="../../media/defender-identity/configure-sensor-details.png" alt-text="الصفحة التي تقوم بتكوين إعدادات المستشعر عليها" lightbox="../../media/defender-identity/configure-sensor-details.png":::

1. في صفحة **أدوات الاستشعار** ، يمكنك تصدير قائمة أدوات الاستشعار إلى ملف .csv عن طريق تحديد **تصدير**.

   :::image type="content" source="../../media/defender-identity/export-sensors.png" alt-text="قائمة تصدير أدوات الاستشعار" lightbox="../../media/defender-identity/export-sensors.png":::

## <a name="add-a-sensor"></a>إضافة مستشعر

من صفحة **أدوات الاستشعار** ، يمكنك إضافة مستشعر جديد.

1. حدد **إضافة مستشعر**.

   :::image type="content" source="../../media/defender-identity/add-sensor.png" alt-text="الخيار &quot;إضافة مستشعر&quot;" lightbox="../../media/defender-identity/add-sensor.png":::

1. سيتم فتح جزء، مما يوفر لك زرا لتنزيل مثبت المستشعر ومفتاح وصول تم إنشاؤه.

   :::image type="content" source="../../media/defender-identity/installer-access-key.png" alt-text="خيارات تنزيل المثبت وإعادة إنشاء المفتاح" lightbox="../../media/defender-identity/installer-access-key.png":::

1. حدد **تنزيل المثبت** لحفظ الحزمة محليا. يتضمن ملف zip الملفات التالية:

    - مثبت استشعار Defender for Identity

    - ملف إعداد التكوين الذي يحتوي على المعلومات المطلوبة للاتصال بالخدمة السحابية ل Defender for Identity

1. انسخ **مفتاح Access**. مفتاح الوصول مطلوب لمستشعر Defender for Identity للاتصال مثيل Defender for Identity الخاص بك. مفتاح الوصول هو كلمة مرور مرة واحدة لنشر المستشعر، وبعد ذلك يتم إجراء كل الاتصالات باستخدام شهادات للمصادقة وتشفير TLS. استخدم **الزر إعادة إنشاء المفتاح** إذا كنت بحاجة إلى إعادة إنشاء مفتاح الوصول الجديد. ولن يؤثر ذلك على أي أدوات استشعار تم نشرها مسبقا، لأنه يستخدم فقط للتسجيل الأولي لمستشعر الاستشعار.

1. انسخ الحزمة إلى الخادم المخصص أو وحدة التحكم بالمجال التي تقوم بتثبيت مستشعر Defender for Identity عليها.

## <a name="see-also"></a>راجع أيضًا

- [إدارة تنبيهات أمان Defender for Identity](manage-security-alerts.md)
