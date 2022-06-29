---
title: دفق أحداث Microsoft Defender لنقطة النهاية إلى حساب التخزين الخاص بك
description: تعرف على كيفية تكوين Microsoft Defender لنقطة النهاية لدفق أحداث التتبع المتقدم إلى حساب التخزين الخاص بك.
keywords: تصدير البيانات الأولية، وتدفق واجهة برمجة التطبيقات، وواجهة برمجة التطبيقات، ومراكز الأحداث، وتخزين Azure، وحساب التخزين، والتتبع المتقدم، ومشاركة البيانات الأولية
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
ms.openlocfilehash: c94830e4f9dbfe16a8dfafba35aecb5a36efddf5
ms.sourcegitcommit: d1b60ed9a11f5e6e35fbaf30ecaeb9dfd6dd197d
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 06/29/2022
ms.locfileid: "66493432"
---
# <a name="configure-microsoft-defender-for-endpoint-to-stream-advanced-hunting-events-to-your-storage-account"></a>تكوين Microsoft Defender لنقطة النهاية لدفق أحداث التتبع المتقدم إلى حساب التخزين الخاص بك

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**

- [Defender for Endpoint الخطة 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

> هل تريد تجربة Defender لنقطة النهاية؟ [التسجيل للحصول على إصدار تجريبي مجاني.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-configuresiem-abovefoldlink)

## <a name="before-you-begin"></a>قبل البدء

1. إنشاء [حساب تخزين](/azure/storage/common/storage-account-overview) في المستأجر الخاص بك.

2. سجل الدخول إلى [مستأجر Azure](https://ms.portal.azure.com/)، وانتقل إلى **الاشتراكات > اشتراكك > موفري الموارد > التسجيل في Microsoft.insights**.

## <a name="enable-raw-data-streaming"></a>تمكين دفق البيانات الأولية

1. سجل الدخول إلى [Microsoft 365 Defender](https://security.microsoft.com) **كمسؤول عام *أو** _*_مسؤول الأمان_**.

2. انتقل إلى [صفحة إعدادات تصدير البيانات](https://security.microsoft.com/settings/mtp_settings/raw_data_export) في Microsoft 365 Defender.

3. انقر فوق **"إضافة إعدادات تصدير البيانات**".

4. اختر اسما للإعدادات الجديدة.

5. اختر **إعادة توجيه الأحداث إلى Azure Storage**.

6. اكتب **معرف مورد حساب التخزين**. للحصول على **معرف مورد حساب التخزين**، انتقل إلى صفحة حساب التخزين على علامة تبويب \> خصائص [مدخل](https://ms.portal.azure.com/) \> Azure انسخ النص ضمن **معرف مورد حساب التخزين**:

   :::image type="content" source="images/storage-account-resource-id.png" alt-text="مراكز الأحداث ذات معرف المورد1" lightbox="images/storage-account-resource-id.png":::

7. اختر الأحداث التي تريد دفقها وانقر فوق **"حفظ**".

## <a name="the-schema-of-the-events-in-the-storage-account"></a>مخطط الأحداث في حساب التخزين

- سيتم إنشاء حاوية كائن ثنائي كبير الحجم لكل نوع حدث:

  :::image type="content" source="images/storage-account-event-schema.png" alt-text="مراكز الأحداث ذات معرف المورد2" lightbox="images/storage-account-event-schema.png":::

- مخطط كل صف في الكائن الثنائي كبير الحجم هو JSON التالي:

  ```json
  {
    "time": "<The time WDATP received the event>"
    "tenantId": "<Your tenant ID>"
    "category": "<The Advanced Hunting table name with 'AdvancedHunting-' prefix>"
    "properties": { <WDATP Advanced Hunting event as Json> }
  }
  ```

- يحتوي كل كائن ثنائي كبير الحجم على صفوف متعددة.

- يحتوي كل صف على اسم الحدث، والوقت الذي تلقى فيه Defender لنقطة النهاية الحدث، والمستأجر الذي ينتمي إليه (ستحصل فقط على الأحداث من المستأجر)، والحدث بتنسيق JSON في خاصية تسمى "خصائص".

- لمزيد من المعلومات حول مخطط أحداث Microsoft Defender لنقطة النهاية، راجع [نظرة عامة على Advanced Hunting](advanced-hunting-overview.md).

- في Advanced Hunting، يحتوي جدول **DeviceInfo** على عمود يسمى **MachineGroup** يحتوي على مجموعة الجهاز. هنا سيتم تزيين كل حدث بهذا العمود أيضا. راجع [مجموعات الأجهزة](machine-groups.md) للحصول على مزيد من المعلومات.

## <a name="data-types-mapping"></a>تعيين أنواع البيانات

للحصول على أنواع البيانات لخصائص الأحداث، قم بما يلي:

1. سجل الدخول إلى [Microsoft 365 Defender](https://security.microsoft.com) وانتقل إلى [صفحة التتبع المتقدم](https://security.microsoft.com/hunting-package).

2. قم بتشغيل الاستعلام التالي للحصول على تعيين أنواع البيانات لكل حدث:

   ```kusto
   {EventType}
   | getschema
   | project ColumnName, ColumnType
   ```

- فيما يلي مثال لحدث معلومات الجهاز:

  :::image type="content" source="images/data-types-mapping-query.png" alt-text="مراكز الأحداث ذات معرف المورد3" lightbox="images/data-types-mapping-query.png":::

## <a name="related-topics"></a>المواضيع ذات الصلة

- [نظرة عامة على التتبع المتقدم](advanced-hunting-overview.md)
- [واجهة برمجة تطبيقات تدفق Microsoft Defender لنقطة النهاية](raw-data-export.md)
- [دفق أحداث Microsoft Defender لنقطة النهاية إلى حساب تخزين Azure](raw-data-export-storage.md)
- [وثائق حساب تخزين Azure](/azure/storage/common/storage-account-overview)
