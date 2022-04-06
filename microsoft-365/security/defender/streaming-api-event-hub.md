---
title: دفق Microsoft 365 Defender الأحداث إلى Azure Event Hub
description: تعرف على كيفية تكوين Microsoft 365 Defender لبث أحداث "البحث المتقدم" إلى مركز الأحداث.
keywords: تصدير البيانات الخام، دفق API، API، Azure Event Hub، تخزين Azure، حساب التخزين، البحث المتقدم، مشاركة البيانات الخام
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
ms.collection: M365-security-compliance
ms.custom: admindeeplinkDEFENDER
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 064ce5f796d59994b9d7ec4c3403711b1d683e56
ms.sourcegitcommit: 3b8e009ea1ce928505b8fc3b8926021fb91155f3
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/28/2022
ms.locfileid: "64500464"
---
# <a name="configure-microsoft-365-defender-to-stream-advanced-hunting-events-to-your-azure-event-hub"></a>تكوين Microsoft 365 Defender دفق أحداث "الصيد المتقدم" إلى مركز الأحداث في Azure

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**ينطبق على:**
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

[!include[Prerelease information](../../includes/prerelease.md)]

## <a name="before-you-begin"></a>قبل البدء

1. إنشاء مركز [أحداث](/azure/event-hubs/) في المستأجر.

2. سجل دخولك إلى [مستأجر Azure](https://ms.portal.azure.com/)، واذهب إلى الاشتراكات > **اشتراكك > موردي > التسجيل في Microsoft.Insights**.

3. إنشاء مساحة اسم مركز الحدث، **انتقل** إلى مركز الأحداث > إضافة مستويات الأسعار ووحدات النقل و"التضخيم التلقائي" المناسبة للتحميل المتوقع وتحديدها. لمزيد من المعلومات، راجع [أسعار مراكز الأحداث](https://azure.microsoft.com/pricing/details/event-hubs/).

### <a name="add-contributor-permissions"></a>إضافة أذونات المساهم

بمجرد إنشاء مساحة اسم مركز الحدث، ستحتاج إلى:

1. تعريف المستخدم الذي سيسجل دخوله Microsoft 365 Defender كمساهم.

2. إذا كنت تريد الاتصال بتطبيق ما، ف أضف خدمة تسجيل التطبيقات الأساسية كقارئ أو Azure Event Hub Data Receiver (يمكن القيام بذلك أيضا على مستوى مجموعة الموارد أو الاشتراك).

    انتقل إلى **مساحة اسم محاور > الوصول (IAM) > إضافة** وتحقق ضمن **تعيينات الدور**.

## <a name="enable-raw-data-streaming"></a>تمكين دفق البيانات الخام

1. سجل <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">دخولك Microsoft 365 Defender كمسؤول</a> **عام *** أو _*مسؤول _أمان_**.

2. انتقل إلى صفحة [إعدادات API المتدفقة](https://security.microsoft.com/settings/mtp_settings/raw_data_export).

3. انقر فوق **إضافة**.

4. اختر اسما لإعداداتك الجديدة.

5. اختر **إعادة توجيه الأحداث إلى Azure Event Hub**.

6. يمكنك تحديد ما إذا كنت تريد تصدير بيانات الحدث إلى مركز حدث واحد، أو تصدير كل جدول حدث إلى مركز حدث مختلف في مساحة اسم مركز الأحداث.

7. لتصدير بيانات الحدث إلى مركز حدث واحد، أدخل اسم **مركز** الأحداث ومصدر " **مركز الأحداث**" الخاص بك.

   للحصول على "مورد **مركز** الأحداث"، انتقل إلى صفحة مساحة اسم Azure Event Hub على علامة التبويب [AzureProperties](https://ms.portal.azure.com/) >  > النص ضمن **"مورد المعر"** :

   :::image type="content" source="../defender-endpoint/images/event-hub-resource-id.png" alt-text="&quot;مورد مركز الأحداث&quot;" lightbox="../defender-endpoint/images/event-hub-resource-id.png":::

8. انتقل [إلى أنواع الأحداث](supported-event-types.md) Microsoft 365 Defender في برمجة تطبيقات دفق الأحداث لمراجعة حالة دعم أنواع الأحداث في Microsoft 365 API للدفق.

9. اختر الأحداث التي تريد دفقها وانقر فوق **حفظ**.

## <a name="the-schema-of-the-events-in-azure-event-hub"></a>مخطط الأحداث في Azure Event Hub

```JSON
{
   "records": [
               {
                  "time": "<The time Microsoft 365 Defender received the event>"
                  "tenantId": "<The Id of the tenant that the event belongs to>"
                  "category": "<The Advanced Hunting table name with 'AdvancedHunting-' prefix>"
                  "properties": { <Microsoft 365 Defender Advanced Hunting event as Json> }
               }
               ...
            ]
}
```

- تحتوي كل رسالة مركز الأحداث في Azure Event Hub على قائمة بالسجلات.

- يحتوي كل سجل على اسم الحدث والوقت Microsoft 365 Defender الحدث والمستأجر الذي ينتمي إليه (ستحصل فقط على الأحداث من المستأجر)، والحدث بتنسيق JSON في خاصية تسمى "**الخصائص**".

- للحصول على مزيد من المعلومات حول مخطط Microsoft 365 Defender، راجع [نظرة عامة حول "الصيد المتقدم](advanced-hunting-overview.md)".

- في البحث المتقدم، يحتوي جدول **DeviceInfo** على عمود يسمى **MachineGroup** يحتوي على مجموعة الجهاز. هنا سيتم تزيين كل حدث بهذا العمود أيضا.

## <a name="data-types-mapping"></a>تعيين أنواع البيانات

للحصول على أنواع البيانات لخصائص الحدث، اتبع الخطوات التالية:

1. سجل دخولك <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender</a> واذهب إلى [صفحة "الصيد المتقدم](https://security.microsoft.com/hunting-package)".

2. تشغيل الاستعلام التالي لتعيين أنواع البيانات لكل حدث:

   ```kusto
   {EventType}
   | getschema
   | project ColumnName, ColumnType
   ```

- فيما يلي مثال لحدث معلومات الجهاز:

  :::image type="content" source="../defender-endpoint/images/machine-info-datatype-example.png" alt-text="استعلام مثال حول معلومات الجهاز" lightbox="../defender-endpoint/images/machine-info-datatype-example.png":::

## <a name="related-topics"></a>المواضيع ذات الصلة

- [نظرة عامة حول "الصيد المتقدم"](advanced-hunting-overview.md)
- [Microsoft 365 Defender API المتدفقة](streaming-api.md)
- [أنواع Microsoft 365 Defender الأحداث المعتمدة في API لتدفق الأحداث](supported-event-types.md)
- [دفق Microsoft 365 Defender الأحداث إلى حساب تخزين Azure](streaming-api-storage.md)
- [وثائق Azure Event Hub](/azure/event-hubs/)
- [استكشاف مشاكل الاتصال وإصلاحها - Azure Event Hub](/azure/event-hubs/troubleshooting-guide)
