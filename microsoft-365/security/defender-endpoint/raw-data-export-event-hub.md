---
title: دفق أحداث Microsoft Defender لنقطة النهاية إلى مراكز أحداث Azure
description: تعرف على كيفية تكوين Microsoft Defender لنقطة النهاية لبث أحداث "البحث المتقدم" إلى مركز الأحداث.
keywords: تصدير البيانات الخام، وبرمجة تطبيقات النقل المتدفق، و API، و Azure Event Hubs، ومساحة تخزين Azure، حساب التخزين، والصيد المتقدم، ومشاركة البيانات الخام
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
ms.topic: article
ms.technology: mde
ms.custom: api
ms.openlocfilehash: b1d313ed2980f84318a590df55e0a8d8e7b152ab
ms.sourcegitcommit: cde34d38bdfb6335b980f1c48c6b218da6a64bf8
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 01/20/2022
ms.locfileid: "63570659"
---
# <a name="configure-microsoft-defender-for-endpoint-to-stream-advanced-hunting-events-to-your-azure-event-hubs"></a>تكوين Microsoft Defender لنقطة النهاية لبث أحداث "الصيد المتقدم" إلى مراكز أحداث Azure

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**

- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

> هل تريد تجربة Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-configuresiem-abovefoldlink)

## <a name="before-you-begin"></a>قبل البدء

1. إنشاء مركز [أحداث](/azure/event-hubs/) في المستأجر.

2. سجل دخولك إلى مستأجر [Azure](https://ms.portal.azure.com/)، واذهب إلى الاشتراكات > **اشتراكك > موفري الموارد > التسجيل في Microsoft.insights**.

## <a name="enable-raw-data-streaming"></a>تمكين دفق البيانات الخام

1. سجل دخولك [إلى Microsoft 365 Defender](https://security.microsoft.com) **كمسؤول** عام * أو _*مسؤول _الأمان_**.

2. انتقل إلى [صفحة إعدادات تصدير البيانات](https://security.microsoft.com/interoperability/dataexport) في مدخل Microsoft Defender.

3. انقر فوق **إضافة إعدادات تصدير البيانات**.

4. اختر اسما لإعداداتك الجديدة.

5. اختر **إعادة توجيه الأحداث إلى Azure Event Hubs**.

6. اكتب اسم **"مراكز الأحداث"** وم ID **مورد "مراكز** الأحداث".

   للحصول على "معرّف موارد مراكز الأحداث"، انتقل إلى صفحة مساحة اسم Azure Event Hubs على علامة التبويب خصائص [Azure](https://ms.portal.azure.com/) > \> نسخ النص ضمن **"معرّف المورد"**:

   :::image type="content" alt-text="صورة لمورد مركز الحدث Id1." source="images/event-hub-resource-id.png" lightbox="images/event-hub-resource-id.png":::

7. اختر الأحداث التي تريد دفقها وانقر فوق **حفظ**.

## <a name="the-schema-of-the-events-in-azure-event-hubs"></a>مخطط الأحداث في Azure Event Hubs

```json
{
    "records": [
                    {
                        "time": "<The time WDATP received the event>"
                        "tenantId": "<The Id of the tenant that the event belongs to>"
                        "category": "<The Advanced Hunting table name with 'AdvancedHunting-' prefix>"
                        "properties": { <WDATP Advanced Hunting event as Json> }
                    }
                    ...
                ]
}
```

- تحتوي كل رسالة مركز أحداث في Azure Event Hubs على قائمة بالسجلات.

- يحتوي كل سجل على اسم الحدث، والوقت الذي تلقى فيه Microsoft Defender ل Endpoint الحدث، والمستأجر الذي ينتمي إليه (ستحصل فقط على الأحداث من المستأجر)، والحدث بتنسيق JSON في خاصية تسمى "**الخصائص**".

- لمزيد من المعلومات حول مخطط أحداث نقطة النهاية ل Microsoft Defender، راجع [نظرة عامة حول "الصيد المتقدم](advanced-hunting-overview.md)".

- في البحث المتقدم، يحتوي جدول **DeviceInfo** على عمود يسمى **MachineGroup** يحتوي على مجموعة الجهاز. هنا سيتم تزيين كل حدث بهذا العمود أيضا. لمزيد [من المعلومات،](machine-groups.md) راجع مجموعات الأجهزة.

## <a name="data-types-mapping"></a>تعيين أنواع البيانات

للحصول على أنواع البيانات لخصائص الحدث، اتبع الخطوات التالية:

1. سجل دخولك [Microsoft 365 Defender](https://security.microsoft.com) واذهب إلى [صفحة "الصيد المتقدم](https://security.microsoft.com/hunting-package)".

2. تشغيل الاستعلام التالي لتعيين أنواع البيانات لكل حدث:

   ```kusto
   {EventType}
   | getschema
   | project ColumnName, ColumnType 
   ```

- فيما يلي مثال لحدث معلومات الجهاز:

  ![صورة لمورد مركز الحدث Id2.](images/machine-info-datatype-example.png)

## <a name="related-topics"></a>المواضيع ذات الصلة

- [نظرة عامة حول "الصيد المتقدم"](advanced-hunting-overview.md)
- [API ل Microsoft Defender لنقطة النهاية المتدفقة](raw-data-export.md)
- [دفق أحداث Microsoft Defender لنقطة النهاية إلى حساب تخزين Azure](raw-data-export-storage.md)
- [وثائق Azure Event Hubs](/azure/event-hubs/)
- [استكشاف مشاكل الاتصال وإصلاحها - مراكز أحداث Azure](/azure/event-hubs/troubleshooting-guide)
