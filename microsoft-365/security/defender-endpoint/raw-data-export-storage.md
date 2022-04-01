---
title: دفق Microsoft Defender لنقطة النهاية الأحداث إلى حساب التخزين
description: تعرف على كيفية تكوين Microsoft Defender لنقطة النهاية لبث أحداث "الصيد المتقدم" إلى حساب التخزين.
keywords: تصدير البيانات الخام، دفق API، API، مراكز الأحداث، تخزين Azure، حساب التخزين، البحث المتقدم، مشاركة البيانات الخام
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
ms.openlocfilehash: 77220c8e34cfcbcdb6b1ca527786696bb67e5d79
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/25/2022
ms.locfileid: "64465764"
---
# <a name="configure-microsoft-defender-for-endpoint-to-stream-advanced-hunting-events-to-your-storage-account"></a>تكوين Microsoft Defender لنقطة النهاية دفق أحداث "الصيد المتقدم" إلى حساب التخزين

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**

- [Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

> هل تريد تجربة Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-configuresiem-abovefoldlink)

## <a name="before-you-begin"></a>قبل البدء

1. إنشاء حساب [تخزين في](/azure/storage/common/storage-account-overview) المستأجر.

2. سجل دخولك إلى مستأجر [Azure](https://ms.portal.azure.com/)، واذهب إلى الاشتراكات > **اشتراكك > موفري الموارد > التسجيل في Microsoft.insights**.

## <a name="enable-raw-data-streaming"></a>تمكين دفق البيانات الخام

1. سجل [دخولك Microsoft 365 Defender](https://security.microsoft.com) **كمسؤول** عام * أو _*مسؤول _أمان_**.

2. انتقل إلى [صفحة إعدادات تصدير البيانات](https://security.microsoft.com/interoperability/dataexport) في Microsoft 365 Defender.

3. انقر فوق **إضافة إعدادات تصدير البيانات**.

4. اختر اسما لإعداداتك الجديدة.

5. اختر **إعادة توجيه الأحداث إلى Azure Storage**.

6. اكتب " **مورد حساب التخزين" الخاص بك**. للحصول على "مورد حساب التخزين"، انتقل إلى صفحة حساب التخزين على علامة التبويب خصائص مدخل [Azure](https://ms.portal.azure.com/) \> \> انسخ النص ضمن "مورد حساب التخزين **"**:

   :::image type="content" source="images/storage-account-resource-id.png" alt-text="مراكز الأحداث مع &quot;مورد الم ID1&quot;" lightbox="images/storage-account-resource-id.png":::

7. اختر الأحداث التي تريد دفقها وانقر فوق **حفظ**.

## <a name="the-schema-of-the-events-in-the-storage-account"></a>مخطط الأحداث في حساب التخزين

- سيتم إنشاء حاوية blob لكل نوع حدث:

  :::image type="content" source="images/storage-account-event-schema.png" alt-text="مراكز الأحداث مع &quot;مورد الم ID2&quot;" lightbox="images/storage-account-event-schema.png":::

- مخطط كل صف في blob هو JSON التالي:

  ```json
  {
      "time": "<The time WDATP received the event>"
      "tenantId": "<Your tenant ID>"
      "category": "<The Advanced Hunting table name with 'AdvancedHunting-' prefix>"
      "properties": { <WDATP Advanced Hunting event as Json> }
  }
  ```

- يحتوي كل blob على صفوف متعددة.

- يحتوي كل صف على اسم الحدث والوقت الذي تلقى فيه Defender لنقطة النهاية الحدث والمستأجر الذي ينتمي إليه (ستحصل فقط على الأحداث من المستأجر)، والحدث بتنسيق JSON في خاصية تسمى "الخصائص".

- لمزيد من المعلومات حول مخطط أحداث Microsoft Defender لنقطة النهاية، راجع [نظرة عامة حول "الصيد المتقدم](advanced-hunting-overview.md)".

- في البحث المتقدم، يحتوي جدول **DeviceInfo** على عمود يسمى **MachineGroup** يحتوي على مجموعة الجهاز. هنا سيتم تزيين كل حدث بهذا العمود أيضا. لمزيد [من المعلومات،](machine-groups.md) راجع مجموعات الأجهزة.

## <a name="data-types-mapping"></a>تعيين أنواع البيانات

للحصول على أنواع البيانات لخصائص الأحداث لدينا، عليك القيام بواحد من الخطوات التالية:

1. سجل دخولك [Microsoft 365 Defender](https://security.microsoft.com) واذهب إلى [صفحة "الصيد المتقدم](https://security.microsoft.com/hunting-package)".

2. تشغيل الاستعلام التالي لتعيين أنواع البيانات لكل حدث:

   ```kusto
   {EventType}
   | getschema
   | project ColumnName, ColumnType
   ```

- فيما يلي مثال لحدث معلومات الجهاز:

  :::image type="content" source="images/data-types-mapping-query.png" alt-text="مراكز الأحداث مع &quot;مورد ID3&quot;" lightbox="images/data-types-mapping-query.png":::

## <a name="related-topics"></a>المواضيع ذات الصلة

- [نظرة عامة حول "الصيد المتقدم"](advanced-hunting-overview.md)
- [Microsoft Defender لنقطة النهاية API للتدفق](raw-data-export.md)
- [دفق Microsoft Defender لنقطة النهاية الأحداث إلى حساب تخزين Azure](raw-data-export-storage.md)
- [وثائق حساب تخزين Azure](/azure/storage/common/storage-account-overview)
