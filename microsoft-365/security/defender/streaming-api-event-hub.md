---
title: دفق أحداث Microsoft 365 Defender إلى Azure Event Hubs
description: تعرف على كيفية تكوين Microsoft 365 Defender لدفق أحداث التتبع المتقدمة إلى مراكز الأحداث.
keywords: تصدير البيانات الأولية، وتدفق واجهة برمجة التطبيقات، وواجهة برمجة التطبيقات، ومراكز أحداث Azure، وتخزين Azure، وحساب التخزين، والتتبع المتقدم، ومشاركة البيانات الأولية
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
ms.openlocfilehash: 9cae28cc69d67bb18058e2c81cd8235ffce79997
ms.sourcegitcommit: 6a981ca15bac84adbbed67341c89235029aad476
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 05/27/2022
ms.locfileid: "65754389"
---
# <a name="configure-microsoft-365-defender-to-stream-advanced-hunting-events-to-your-azure-event-hub"></a>تكوين Microsoft 365 Defender لدفق أحداث التتبع المتقدمة إلى Azure Event Hub

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

[!include[Prerelease information](../../includes/prerelease.md)]

## <a name="prerequisites"></a>المتطلبات الأساسية

قبل تكوين Microsoft 365 Defender لدفق البيانات إلى Event Hubs، تأكد من استيفاء المتطلبات الأساسية التالية:

1. إنشاء مراكز أحداث (للحصول على معلومات، راجع [إعداد مراكز الأحداث](configure-event-hub.md#set-up-event-hubs)).

2. إنشاء مساحة اسم لمراكز الأحداث (للحصول على معلومات، راجع [إعداد مساحة اسم مراكز الأحداث](configure-event-hub.md#set-up-event-hubs-namespace)).

3. إضافة أذونات إلى الكيان الذي لديه امتيازات **المساهم** بحيث يمكن لهذا الكيان تصدير البيانات إلى Event Hubs. لمزيد من المعلومات حول إضافة أذونات، راجع ["إضافة أذونات"](configure-event-hub.md#add-permissions)

> [!NOTE]
> يمكن دمج واجهة برمجة تطبيقات الدفق إما عبر Event Hubs أو Azure Storage Account.

## <a name="enable-raw-data-streaming"></a>تمكين دفق البيانات الأولية

1. سجل الدخول إلى <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">مدخل Microsoft 365 Defender</a> كمدخل ***Global Administrator** _ أو _*_Security Administrator_**.

2. انتقل إلى [صفحة إعدادات واجهة برمجة التطبيقات المتدفقة](https://security.microsoft.com/settings/mtp_settings/raw_data_export).

3. انقر فوق **"إضافة**".

4. اختر اسما للإعدادات الجديدة.

5. اختر **إعادة توجيه الأحداث إلى Azure Event Hub**.

6. يمكنك تحديد ما إذا كنت تريد تصدير بيانات الحدث إلى Event Hub واحد، أو لتصدير كل جدول حدث إلى Event Hubs مختلفة في مساحة اسم Event Hubs.

7. لتصدير بيانات الحدث إلى Event Hub واحد، أدخل **اسم Event Hub** **ومعرف مورد Event Hub**.

   للحصول على **معرف مورد Event Hub**، انتقل إلى صفحة مساحة اسم Azure Event Hubs **على علامة** تبويب [خصائص Azure](https://ms.portal.azure.com/) >  > نسخ النص ضمن **معرف المورد**:

   :::image type="content" source="../defender-endpoint/images/event-hub-resource-id.png" alt-text="معرف مورد Event Hub" lightbox="../defender-endpoint/images/event-hub-resource-id.png":::

8. انتقل إلى [أنواع أحداث Microsoft 365 Defender المعتمدة في واجهة برمجة تطبيقات دفق الأحداث](supported-event-types.md) لمراجعة حالة دعم أنواع الأحداث في واجهة برمجة تطبيقات الدفق Microsoft 365.

9. اختر الأحداث التي تريد دفقها وانقر فوق **"حفظ**".

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

- تحتوي كل رسالة Event Hubs في Azure Event Hubs على قائمة سجلات.

- يحتوي كل سجل على اسم الحدث، والوقت Microsoft 365 Defender تلقي الحدث، والمستأجر الذي ينتمي إليه (ستحصل فقط على الأحداث من المستأجر)، والحدث بتنسيق JSON في خاصية تسمى "**خصائص**".

- لمزيد من المعلومات حول مخطط أحداث Microsoft 365 Defender، راجع [نظرة عامة على Advanced Hunting](advanced-hunting-overview.md).

- في Advanced Hunting، يحتوي جدول **DeviceInfo** على عمود يسمى **MachineGroup** يحتوي على مجموعة الجهاز. هنا سيتم تزيين كل حدث بهذا العمود أيضا.

## <a name="data-types-mapping"></a>تعيين أنواع البيانات

للحصول على أنواع البيانات لخصائص الحدث، قم بالخطوات التالية:

1. سجل الدخول إلى <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender</a> وانتقل إلى [صفحة التتبع المتقدم](https://security.microsoft.com/hunting-package).

2. قم بتشغيل الاستعلام التالي للحصول على تعيين أنواع البيانات لكل حدث:

   ```kusto
   {EventType}
   | getschema
   | project ColumnName, ColumnType
   ```

- فيما يلي مثال لحدث معلومات الجهاز:

  :::image type="content" source="../defender-endpoint/images/machine-info-datatype-example.png" alt-text="استعلام مثال لمعلومات الجهاز" lightbox="../defender-endpoint/images/machine-info-datatype-example.png":::

## <a name="related-topics"></a>المواضيع ذات الصلة

- [نظرة عامة على التتبع المتقدم](advanced-hunting-overview.md)
- [واجهة برمجة تطبيقات تدفق Microsoft 365 Defender](streaming-api.md)
- [أنواع أحداث Microsoft 365 Defender المعتمدة في واجهة برمجة تطبيقات دفق الأحداث](supported-event-types.md)
- [دفق أحداث Microsoft 365 Defender إلى حساب تخزين Azure](streaming-api-storage.md)
- [وثائق Azure Event Hubs](/azure/event-hubs/)
- [استكشاف مشكلات الاتصال وإصلاحها - Azure Event Hubs](/azure/event-hubs/troubleshooting-guide)
