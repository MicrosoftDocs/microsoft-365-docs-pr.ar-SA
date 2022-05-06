---
title: تكوين Event Hub
description: تعرف على كيفية تكوين Event Hub
keywords: مركز الحدث، وتكوينه، ونتائج التحليلات
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
ms.openlocfilehash: 40211d37b8b036f93b826a383d9d0aa87f44fc68
ms.sourcegitcommit: 292de1a7e5ecc2e9e6187126aebba6d3b9416dff
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 05/06/2022
ms.locfileid: "65243063"
---
# <a name="configure-your-event-hub"></a>تكوين Event Hub

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

تعرف على كيفية تكوين Event Hub بحيث يمكنه استيعاب الأحداث من Microsoft 365 Defender.

## <a name="set-up-the-required-resource-provider-in-the-event-hub-subscription"></a>إعداد موفر الموارد المطلوب في اشتراك Event Hub

1. سجّل الدخول إلى [مدخل Azure](https://portal.azure.com).
1. Select **Subscriptions** > **{ Select the subscription the event hubs will be deployed to }** > **Resource providers**.
1. تحقق من أن **Microsoft.Insights** الموفر مسجل. وإلا، فسجله.

:::image type="content" source="../../media/f893db7a7b1f7aa520e8b9257cc72562.png" alt-text="قائمة صفحة موفري الخدمة في مدخل Microsoft Azure" lightbox="../../media/f893db7a7b1f7aa520e8b9257cc72562.png":::

## <a name="set-up-azure-active-directory-app-registration"></a>إعداد تسجيل تطبيق Azure Active Directory

> ! [ملاحظة] يجب أن يكون لديك دور المسؤول أو يجب تعيين Azure Active Directory (AAD (دليل Azure النشط)) للسماح لغير المسؤولين بتسجيل التطبيقات. يجب أن يكون لديك أيضا دور "المالك" أو "مسؤول وصول المستخدم" لتعيين دور لكيان الخدمة. لمزيد من المعلومات، راجع [إنشاء تطبيق Azure AD & كيان الخدمة في المدخل - النظام الأساسي للهويات في Microsoft \| Microsoft Docs](/azure/active-directory/develop/howto-create-service-principal-portal).

1. إنشاء تسجيل جديد (الذي ينشئ بطبيعته كيان خدمة) في **تسجيلات** \> تطبيق **Azure Active Directory** \> **الجديدة.**

1. املأ النموذج بالاسم فقط (لا يلزم إعادة توجيه URI).

    :::image type="content" source="../../media/336bc84e6be23900c43232b4ef0c253c.png" alt-text="قسم عرض اسم التطبيق في مدخل Microsoft Azure" lightbox="../../media/336bc84e6be23900c43232b4ef0c253c.png":::


    :::image type="content" source="../../media/06ac04c4ff713c2065cec2ef2f99a294.png" alt-text="قسم معلومات النظرة العامة في مدخل Microsoft Azure" lightbox="../../media/06ac04c4ff713c2065cec2ef2f99a294.png":::

1. إنشاء سر بالنقر فوق **شهادات & أسرار** \> **سر عميل جديد**:

    :::image type="content" source="../../media/d2ef88d3d2310d2c60c294b569cdf02e.png" alt-text="قسم بيانات العميل السرية في مدخل Microsoft Azure" lightbox="../../media/d2ef88d3d2310d2c60c294b569cdf02e.png":::
    

> [!WARNING]
> **لن تتمكن من الوصول إلى سر العميل مرة أخرى لذا تأكد من حفظه**.

## <a name="set-up-event-hub-namespace"></a>إعداد مساحة اسم Event Hub

1. إنشاء مساحة اسم Event Hub:

    انتقل **إلى Event Hub \> Add** وحدد مستوى التسعير ووحدات معدل النقل والنفخ التلقائي (يتطلب تسعيرا قياسيا وضمن الميزات) المناسبة للتحميل الذي تتوقعه. لمزيد من المعلومات، راجع [Pricing - Event Hub \| Microsoft Azure](https://azure.microsoft.com/pricing/details/event-hubs/)

    > [!NOTE]
    > يمكنك استخدام مركز حدث موجود، ولكن يتم تعيين معدل النقل والتحجيم على مستوى مساحة الاسم بحيث يوصى بوضع event-hub في مساحة الاسم الخاصة به.

   :::image type="content" source="../../media/ebc4ca37c342ad1da75c4aee4018e51a.png" alt-text="قسم مراكز الأحداث في مدخل Microsoft Azure" lightbox="../../media/ebc4ca37c342ad1da75c4aee4018e51a.png":::

1. ستحتاج أيضا إلى معرف المورد لمساحة اسم Event Hub هذه. انتقل إلى خصائص مساحة \> اسم Azure Event Hub. انسخ النص ضمن معرف المورد وسجله لاستخدامه أثناء قسم تكوين Microsoft 365 أدناه.

    :::image type="content" source="../../media/759498162a4e93cbf17c4130d704d164.png" alt-text="قسم خصائص مراكز الأحداث في مدخل Microsoft Azure" lightbox="../../media/759498162a4e93cbf17c4130d704d164.png":::


1. بمجرد إنشاء مساحة اسم Event Hub، ستحتاج إلى إضافة App Registration Service Principal كقارئ ومتلقي بيانات Azure Event Hubs والمستخدم الذي سيقوم بتسجيل الدخول إلى Microsoft 365 Defender كمساهم (يمكنك أيضا القيام بذلك على مستوى مجموعة الموارد أو الاشتراك).

    يمكنك القيام بهذه الخطوة في **Event Hub Namespace** \> **Access Control (IAM)** \> **Add** and verify under **Role assignments**:

    :::image type="content" source="../../media/9c9c29137b90d5858920202d87680d16.png" alt-text="قسم أساسي لخدمة تسجيل التطبيق في مدخل Microsoft Azure" lightbox="../../media/9c9c29137b90d5858920202d87680d16.png":::

## <a name="set-up-event-hub"></a>إعداد Event Hub

**الخيار 1:**

يمكنك إنشاء Event Hub داخل مساحة الاسم وستتم كتابة **كافة** أنواع الأحداث (الجداول) التي تحددها لتصديرها في Event Hub **هذا** .

**الخيار 2:**

بدلا من تصدير كافة أنواع الأحداث (الجداول) إلى مركز أحداث واحد، يمكنك تصدير كل جدول إلى Event Hub مختلف داخل مساحة اسم Event Hub (مركز أحداث واحد لكل نوع حدث).

في هذا الخيار، سيقوم Microsoft 365 Defender بإنشاء Event Hub نيابة عنك.

> [!NOTE]
> إذا كنت تستخدم مساحة اسم مركز الأحداث **التي ليست** جزءا من نظام مجموعة Event Hub، فستتمكن فقط من اختيار ما يصل إلى 10 أنواع أحداث (جداول) للتصدير في كل الإعدادات تصدير تقوم بتعريفها، بسبب حد Azure البالغ 10 Event Hub لكل مساحة اسم لمركز الحدث.

على سبيل المثال:

:::image type="content" source="../../media/005c1f6c10c34420d387f594987f9ffe.png" alt-text="قسم مراكز الأحداث في مدخل Microsoft Azure" lightbox="../../media/005c1f6c10c34420d387f594987f9ffe.png":::

إذا اخترت هذا الخيار، يمكنك التخطي إلى ["تكوين Microsoft 365 Defender" لإرسال قسم جداول البريد الإلكتروني](#configure-microsoft-365-defender-to-send-email-tables).

إنشاء Event Hub داخل مساحة الاسم الخاصة بك عن طريق تحديد **Event Hub** \> **+ Event Hub**.

يسمح عدد الأقسام بزيادة معدل النقل عبر التوازي، لذلك يوصى بزيادة هذا الرقم استنادا إلى الحمل الذي تتوقعه. يوصى بالاحتفاظ بالرسالة الافتراضية وقيم الالتقاط ل 1 وإيقاف التشغيل.

:::image type="content" source="../../media/1db04b8ec02a6298d7cc70419ac6e6a9.png" alt-text="قسم إنشاء مراكز الأحداث في مدخل Microsoft Azure" lightbox="../../media/1db04b8ec02a6298d7cc70419ac6e6a9.png":::
 

بالنسبة إلى Event Hub (وليس مساحة الاسم) ستحتاج إلى تكوين نهج وصول مشترك مع إرسال، مطالبات الاستماع.  انقر فوق نهج \> **الوصول المشترك ل** **Event Hub** \> **+ Add** ثم قم بتسمية النهج (غير مستخدم في مكان آخر) وتحقق من الإرسال **والاستماع**.

:::image type="content" source="../../media/1867d13f46dc6a0f4cdae6cf00df24db.png" alt-text="صفحة نهج الوصول المشترك في مدخل Microsoft Azure" lightbox="../../media/1867d13f46dc6a0f4cdae6cf00df24db.png":::

## <a name="configure-microsoft-365-defender-to-send-email-tables"></a>تكوين Microsoft 365 Defender لإرسال جداول البريد الإلكتروني

### <a name="set-up-microsoft-365-defender-send-email-tables-to-splunk-via-event-hub"></a>إعداد Microsoft 365 Defender إرسال جداول البريد الإلكتروني إلى Splunk عبر Event Hub

1. سجل الدخول إلى <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender</a> باستخدام حساب يلبي جميع متطلبات الدور التالية:

    - دور المساهم على مستوى مورد *مساحة اسم* Event Hub أو أعلى لمركز الأحداث الذي ستقوم بالتصدير إليه. بدون هذا الإذن، ستحصل على خطأ تصدير عند محاولة حفظ الإعدادات.

    - دور المسؤول العام أو مسؤول الأمان على المستأجر المرتبط Microsoft 365 Defender وAzure.

      :::image type="content" source="../../media/55d5b1c21dd58692fb12a6c1c35bd4fa.png" alt-text="الصفحة الإعدادات لمدخل Microsoft 365 Defender" lightbox="../../media/55d5b1c21dd58692fb12a6c1c35bd4fa.png":::

1. انقر فوق **تصدير \> البيانات الأولية +Add**.

    ستستخدم الآن البيانات التي سجلتها أعلاه.

    **الاسم**: هذه القيمة محلية ويجب أن تكون أي شيء يعمل في بيئتك.

    **إعادة توجيه الأحداث إلى مركز الأحداث**: حدد خانة الاختيار هذه.

    **معرف مورد Event-Hub**: هذه القيمة هي معرف مورد مساحة اسم Event Hub الذي سجلته عند إعداد Event Hub.

    **اسم Event-Hub**: إذا قمت بإنشاء Event Hub داخل مساحة اسم Event Hub، فلصق اسم Event Hub الذي سجلته أعلاه.

    إذا اخترت السماح Microsoft 365 Defender بإنشاء Event Hub لكل أنواع الأحداث (جداول) لك، فاترك هذا الحقل فارغا.

    **أنواع الأحداث**: حدد جداول التتبع المتقدم التي تريد إعادة توجيهها إلى Event Hub ثم إلى تطبيقك المخصص. جداول التنبيه من Microsoft 365 Defender، وجداول الأجهزة من Microsoft Defender لنقطة النهاية (الكشف التلقائي والاستجابة على النقط النهائية)، وجداول البريد الإلكتروني من Microsoft Defender لـ Office 365. تسجل أحداث البريد الإلكتروني كافة معاملات البريد الإلكتروني. يتم أيضا تسجيل URL (ارتباطات خزينة) والمرفقات (خزينة المرفقات) وأحداث ما بعد التسليم (ZAP) ويمكن ربطها بأحداث البريد الإلكتروني في حقل NetworkMessageId.

    :::image type="content" source="../../media/3b2ad64b6ef0f88cf0175f8d57ef8b97.png" alt-text="صفحة إعدادات واجهة برمجة التطبيقات المتدفقة في مدخل Microsoft Azure" lightbox="../../media/3b2ad64b6ef0f88cf0175f8d57ef8b97.png":::

1. تأكد من النقر فوق **"إرسال**".

### <a name="verify-that-the-events-are-being-exported-to-the-event-hub"></a>تحقق من أن الأحداث يتم تصديرها إلى Event Hub

يمكنك التحقق من أن الأحداث يتم إرسالها إلى Event Hub عن طريق تشغيل استعلام تتبع متقدم أساسي. حدد **"استعلام** **التتبع** \> **المتقدم للتتبع**\>" وأدخل الاستعلام التالي:

```console
EmailEvents
|joinkind=fullouterEmailAttachmentInfoonNetworkMessageId
|joinkind=fullouterEmailUrlInfoonNetworkMessageId
|joinkind=fullouterEmailPostDeliveryEventsonNetworkMessageId
|whereTimestamp\>ago(1h)
|count
```

سيظهر لك هذا عدد رسائل البريد الإلكتروني التي تم تلقيها في الساعة الأخيرة التي تم ضمها عبر جميع الجداول الأخرى. كما سيظهر لك ما إذا كنت ترى الأحداث التي يمكن تصديرها إلى مراكز الأحداث. إذا كان هذا العدد يظهر 0، فلن ترى أي بيانات تنتقل إلى Event Hub.

:::image type="content" source="../../media/c305e57dc6f72fa9eb035943f244738e.png" alt-text="صفحة التتبع المتقدمة في مدخل Microsoft Azure" lightbox="../../media/c305e57dc6f72fa9eb035943f244738e.png":::

بمجرد التحقق من وجود بيانات لتصديرها، يمكنك عرض صفحة Event Hub للتحقق من أن الرسائل واردة. قد يستغرق ذلك ما يصل إلى ساعة واحدة.

1. في Azure، انتقل إلى **Event Hub** \> Click على **Namespace** \> **Event Hub** \> وانقر على **Event Hub**.
1. ضمن **"نظرة عامة**"، قم بالتمرير لأسفل وفي الرسم البياني للرسائل، يجب أن تشاهد "الرسائل الواردة". إذا لم تتمكن من رؤية أي نتائج، فلن تكون هناك أي رسائل يمكن للتطبيق المخصص استيعابها.

:::image type="content" source="../../media/e88060e315d76e74269a3fc866df047f.png" alt-text="صفحة النظرة العامة في مدخل azure Microsoft 365" lightbox="../../media/e88060e315d76e74269a3fc866df047f.png":::
