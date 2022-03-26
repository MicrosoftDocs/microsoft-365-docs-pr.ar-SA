---
title: تكوين مركز الأحداث
description: تعرف على كيفية تكوين مركز الأحداث
keywords: مركز الأحداث، تكوين، تحليلات
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: m365-security-compliance
ms.custom: admindeeplinkDEFENDER
ms.topic: article
MS.technology: mde
ms.openlocfilehash: a842f9161aa823203354917326653b583e5fddb9
ms.sourcegitcommit: d32654bdfaf08de45715dd362a7d42199bdc1ee7
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/23/2022
ms.locfileid: "63754303"
---
# <a name="configure-your-event-hub"></a>تكوين مركز الأحداث

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

تعرف على كيفية تكوين مركز الأحداث بحيث يمكنه استخدام الأحداث من Microsoft 365 Defender.

## <a name="set-up-the-required-resource-provider-in-the-event-hub-subscription"></a>إعداد موفر الموارد المطلوب في اشتراك "مركز الأحداث"

1. سجّل الدخول إلى [مدخل Azure](https://portal.azure.com).
1. حدد **الاشتراكات** > **{ حدد الاشتراك الذي سيتم نشر مراكز الأحداث له إلى }** > **موفري الموارد**.
1. تحقق من أن **Microsoft.Insights** الموفر مسجل. وإلا، فسجله.

:::image type="content" source="../../media/f893db7a7b1f7aa520e8b9257cc72562.png" alt-text="صفحة قائمة موفري الخدمات في مدخل Microsoft Azure" lightbox="../../media/f893db7a7b1f7aa520e8b9257cc72562.png":::

## <a name="set-up-azure-active-directory-app-registration"></a>إعداد تسجيل تطبيق Azure Active Directory

> ! [ملاحظة] يجب أن يكون لديك دور المسؤول أو يجب تعيين Azure Active Directory (AAD (دليل Azure النشط)) للسماح لغير المسؤولين بتسجيل التطبيقات. يجب أن يكون لديك أيضا دور المالك أو مسؤول وصول المستخدم لتعيين دور أساسي للخدمة. لمزيد من المعلومات، راجع إنشاء [تطبيق Azure AD & أساسي للخدمة في المدخل - \| النظام الأساسي للهويات في Microsoft Microsoft Docs](/azure/active-directory/develop/howto-create-service-principal-portal).

1. إنشاء تسجيل جديد (الذي ينشئ في جوهره خدمة رئيسية) في **تسجيلات تطبيق Azure Active Directory** \>  \> **تسجيل جديد.**

1. قم بتعبئة النموذج بالاسم فقط (لا يلزم إعادة توجيه URI).

    :::image type="content" source="../../media/336bc84e6be23900c43232b4ef0c253c.png" alt-text="مقطع عرض اسم التطبيق في مدخل Microsoft Azure" lightbox="../../media/336bc84e6be23900c43232b4ef0c253c.png":::


    :::image type="content" source="../../media/06ac04c4ff713c2065cec2ef2f99a294.png" alt-text="قسم معلومات النظرة العامة في مدخل Microsoft Azure" lightbox="../../media/06ac04c4ff713c2065cec2ef2f99a294.png":::

1. قم بإنشاء سر بالنقر فوق الشهادات **& أسرار** \> **عميل جديد**:

    :::image type="content" source="../../media/d2ef88d3d2310d2c60c294b569cdf02e.png" alt-text="القسم &quot;سرية العميل&quot; في مدخل Microsoft Azure" lightbox="../../media/d2ef88d3d2310d2c60c294b569cdf02e.png":::
    

> [!WARNING]
> **لن تتمكن من الوصول إلى سرية العميل مرة أخرى لذا تأكد من حفظه**.

## <a name="set-up-event-hub-namespace"></a>إعداد مساحة اسم مركز الحدث

1. إنشاء مساحة اسم مركز الحدث:

    انتقل **إلى مركز \> الأحداث إضافة** وحدد مستوى الأسعار ووحدات النقل والتضخيم التلقائي (يتطلب أسعارا قياسية و ضمن الميزات) المناسبة للتحميل الذي تتوقعه. لمزيد من المعلومات، راجع [الأسعار - مركز الأحداث \| Microsoft Azure](https://azure.microsoft.com/pricing/details/event-hubs/)

    > [!NOTE]
    > يمكنك استخدام مركز حدث موجود، ولكن يتم تعيين النقل والتدرج على مستوى مساحة الاسم لذلك من المستحسن وضع مركز أحداث في مساحة الاسم الخاصة به.

   :::image type="content" source="../../media/ebc4ca37c342ad1da75c4aee4018e51a.png" alt-text="قسم مراكز الأحداث في مدخل Microsoft Azure" lightbox="../../media/ebc4ca37c342ad1da75c4aee4018e51a.png":::

1. ستحتاج أيضا إلى "مورد" لمساحة اسم مركز الحدث هذه. انتقل إلى صفحة مساحة اسم Azure Event Hub Properties \> . انسخ النص ضمن "مورد" وسجله لاستخدامه أثناء Microsoft 365 التكوين أدناه.

    :::image type="content" source="../../media/759498162a4e93cbf17c4130d704d164.png" alt-text="قسم خصائص مراكز الأحداث في مدخل Microsoft Azure" lightbox="../../media/759498162a4e93cbf17c4130d704d164.png":::


1. بمجرد إنشاء مساحة اسم مركز الحدث، ستحتاج إلى إضافة خدمة تسجيل التطبيقات الأساسية كقارئ، ومتلقي بيانات مركز أحداث Azure، والمستخدم الذي سيسجل دخوله إلى Microsoft 365 Defender كمساهم (يمكنك أيضا القيام بذلك على مستوى مجموعة الموارد أو الاشتراك).

    يمكنك القيام بهذه الخطوة في **عنصر** \> تحكم الوصول إلى مساحة اسم مركز الحدث **(IAM)** \> **إضافة** وتحقق ضمن **تعيينات الدور**:

    :::image type="content" source="../../media/9c9c29137b90d5858920202d87680d16.png" alt-text="قسم خدمة تسجيل التطبيقات الرئيسي في مدخل Microsoft Azure" lightbox="../../media/9c9c29137b90d5858920202d87680d16.png":::

## <a name="set-up-event-hub"></a>إعداد مركز الأحداث

**الخيار 1:**

يمكنك إنشاء مركز الأحداث ضمن مساحة الاسم وستكتب كل أنواع  الأحداث (الجداول) التي تحددها للتصدير في **مركز الأحداث هذا**.

**الخيار 2:**

بدلا من تصدير كافة أنواع الأحداث (الجداول) إلى مركز أحداث واحد، يمكنك تصدير كل جدول إلى مركز أحداث مختلف داخل مساحة اسم مركز الحدث (مركز أحداث واحد لكل نوع حدث).

في هذا الخيار، Microsoft 365 Defender إنشاء مركز الأحداث لك.

> [!NOTE]
> إذا كنت تستخدم مساحة اسم مركز الحدث التي لا تكون جزءا  من "مجموعة مراكز الأحداث"، يمكنك فقط اختيار ما يصل إلى 10 أنواع أحداث (جداول) للتصدير في كل تصدير الإعدادات تحدده، بسبب تقييد Azure ل 10 مركز الأحداث لكل مساحة اسم مركز الحدث.

على سبيل المثال:

:::image type="content" source="../../media/005c1f6c10c34420d387f594987f9ffe.png" alt-text="قسم مراكز الأحداث في مدخل Microsoft Azure" lightbox="../../media/005c1f6c10c34420d387f594987f9ffe.png":::

إذا اخترت هذا الخيار، يمكنك الانتقال إلى المقطع تكوين Microsoft 365 Defender [لإرسال جداول البريد](#configure-microsoft-365-defender-to-send-email-tables) الإلكتروني.

يمكنك إنشاء مركز الأحداث ضمن مساحة الاسم عن طريق تحديد **مركز الأحداث** \> **+ مركز الأحداث**.

يسمح "عدد الأقسام" لزيادة معدل النقل عبر التوازي، لذلك من المستحسن زيادة هذا الرقم استنادا إلى التحميل الذي تتوقعه. يوصى باستخدام القيم الافتراضية "استبقاء الرسائل والتقاطها" من 1 و"إيقاف التشغيل".

:::image type="content" source="../../media/1db04b8ec02a6298d7cc70419ac6e6a9.png" alt-text="قسم إنشاء مراكز الأحداث في مدخل Microsoft Azure" lightbox="../../media/1db04b8ec02a6298d7cc70419ac6e6a9.png":::
 

بالنسبة إلى مركز الأحداث (وليس مساحة الاسم) هذه، ستحتاج إلى تكوين نهج الوصول المشترك باستخدام إرسال والاستماع إلى المطالبات. انقر فوق نهج **الوصول** \>  \> المشترك في مركز الأحداث **+ إضافة** ثم قم امنحه اسم نهج (غير مستخدم في أي مكان آخر) ثم تحقق **من إرسال** **والاستماع**.

:::image type="content" source="../../media/1867d13f46dc6a0f4cdae6cf00df24db.png" alt-text="صفحة &quot;سياسات الوصول المشترك&quot; في مدخل Microsoft Azure" lightbox="../../media/1867d13f46dc6a0f4cdae6cf00df24db.png":::

## <a name="configure-microsoft-365-defender-to-send-email-tables"></a>تكوين Microsoft 365 Defender لإرسال جداول البريد الإلكتروني

### <a name="set-up-microsoft-365-defender-send-email-tables-to-splunk-via-event-hub"></a>إعداد Microsoft 365 Defender إرسال جداول البريد الإلكتروني إلى Splunk عبر مركز الأحداث

1. سجل <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">دخولك Microsoft 365 Defender</a> باستخدام حساب يلبي جميع متطلبات الدور التالية:

    - دور المساهم على مستوى موارد مساحة *اسم* مركز الحدث أو أعلى لمحور الأحداث الذي سيتم تصديره. بدون هذا الإذن، ستصلك رسالة خطأ تصدير عند محاولة حفظ الإعدادات.

    - دور المسؤول العام أو مسؤول الأمان على المستأجر Microsoft 365 Defender و Azure.

      :::image type="content" source="../../media/55d5b1c21dd58692fb12a6c1c35bd4fa.png" alt-text="صفحة الإعدادات مدخل Microsoft 365 Defender" lightbox="../../media/55d5b1c21dd58692fb12a6c1c35bd4fa.png":::

1. انقر فوق **تصدير البيانات الخام \> +إضافة**.

    سوف تستخدم الآن البيانات التي قمت بتسجيلها أعلاه.

    **الاسم**: هذه القيمة محلية ويجب أن تكون كل ما يعمل في بيئتك.

    **إعادة توجيه الأحداث إلى مركز الأحداث**: حدد خانة الاختيار هذه.

    **"مورد محور الحدث"**: هذه القيمة هي "مورد مساحة اسم مركز الحدث" الذي قمت بتسجيله عند إعداد "مركز الأحداث".

    **اسم مركز الأحداث**: إذا قمت بإنشاء مركز الأحداث داخل مساحة اسم مركز الأحداث، فلصق اسم مركز الأحداث الذي قمت بتسجيله أعلاه.

    إذا اخترت السماح Microsoft 365 Defender إنشاء مركز الأحداث لكل أنواع الأحداث (الجداول)، فاترك هذا الحقل فارغا.

    **أنواع الأحداث**: حدد جداول "الصيد المتقدم" التي تريد إعادة توجيهها إلى مركز الأحداث ثم إلى تطبيقك المخصص. جداول التنبيهات من Microsoft 365 Defender، وجداول الأجهزة من Microsoft Defender لنقطة النهاية (الكشف التلقائي والاستجابة على النقط النهائية)، وجداول البريد الإلكتروني من Microsoft Defender Office 365. تسجل أحداث البريد الإلكتروني كافة معاملات البريد الإلكتروني. يتم أيضا تسجيل عنوان URL (خزينة ارتباطات) والمرفقات (خزينة المرفقات) والأحداث بعد التسليم (ZAP) ويمكن الانضمام إليها إلى "أحداث البريد الإلكتروني" في الحقل NetworkMessageId.

    :::image type="content" source="../../media/3b2ad64b6ef0f88cf0175f8d57ef8b97.png" alt-text="صفحة إعدادات API المتدفقة في مدخل Microsoft Azure" lightbox="../../media/3b2ad64b6ef0f88cf0175f8d57ef8b97.png":::

1. تأكد من النقر فوق **إرسال**.

### <a name="verify-that-the-events-are-being-exported-to-the-event-hub"></a>التحقق من أن الأحداث يتم تصديرها إلى مركز الأحداث

يمكنك التحقق من أنه يتم إرسال الأحداث إلى مركز الأحداث عن طريق تشغيل استعلام "بحث متقدم" أساسي. حدد **البحث** \> **عن استعلام بحث** \> **متقدم** وأدخل الاستعلام التالي:

```console
EmailEvents
|joinkind=fullouterEmailAttachmentInfoonNetworkMessageId
|joinkind=fullouterEmailUrlInfoonNetworkMessageId
|joinkind=fullouterEmailPostDeliveryEventsonNetworkMessageId
|whereTimestamp\>ago(1h)
|count
```

سيعرض لك ذلك عدد رسائل البريد الإلكتروني التي تم تلقيها في الساعة الأخيرة التي تم ضمها عبر كل الجداول الأخرى. كما سيعرض لك ما إذا كنت ترى أحداثا يمكن تصديرها إلى مراكز الأحداث. إذا كان هذا العدد يظهر 0، فلن ترى أي بيانات يتم فرزها إلى مركز الأحداث.

:::image type="content" source="../../media/c305e57dc6f72fa9eb035943f244738e.png" alt-text="صفحة الصيد المتقدمة في مدخل Microsoft Azure" lightbox="../../media/c305e57dc6f72fa9eb035943f244738e.png":::

بعد التحقق من وجود بيانات لتصديرها، يمكنك عرض صفحة مركز الأحداث للتحقق من أن الرسائل واردة. قد يستغرق ذلك ما يصل إلى ساعة واحدة.

1. في Azure، انتقل إلى **مركز الأحداث** \> انقر فوق  \> مركز أحداث **مساحة الاسم انقر** \> فوق **مركز الأحداث**.
1. ضمن **نظرة** عامة، قم بالتمرير لأسفل وفي الرسم البياني للرسائل، يجب أن ترى الرسائل الواردة. إذا لم تظهر أي نتائج، لن تكون هناك أي رسائل لتطبيقك المخصص الذي تريد ا.

:::image type="content" source="../../media/e88060e315d76e74269a3fc866df047f.png" alt-text="صفحة النظرة العامة في مدخل Microsoft 365 Azure" lightbox="../../media/e88060e315d76e74269a3fc866df047f.png":::
