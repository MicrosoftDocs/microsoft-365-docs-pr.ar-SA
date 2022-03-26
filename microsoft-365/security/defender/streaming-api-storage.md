---
title: دفق Microsoft 365 Defender الأحداث إلى حساب التخزين
description: تعرف على كيفية تكوين Microsoft 365 Defender لبث أحداث "البحث المتقدم" إلى حساب التخزين.
keywords: تصدير البيانات الخام، دفق API، API، مراكز الأحداث، تخزين Azure، حساب التخزين، البحث المتقدم، مشاركة البيانات الخام
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
ms.openlocfilehash: 159b4a41d423c2a7af3d367185e29af35a378b6b
ms.sourcegitcommit: 542e6b5d12a8d400c3b9be44d849676845609c5f
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 11/15/2021
ms.locfileid: "63575541"
---
# <a name="configure-microsoft-365-defender-to-stream-advanced-hunting-events-to-your-storage-account"></a>تكوين Microsoft 365 Defender دفق أحداث "الصيد المتقدم" إلى حساب التخزين

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**ينطبق على:**
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

[!include[Prerelease information](../../includes/prerelease.md)]

## <a name="before-you-begin"></a>قبل البدء

1. إنشاء حساب [تخزين في](/azure/storage/common/storage-account-overview) المستأجر.

2. سجل دخولك إلى [مستأجر Azure](https://ms.portal.azure.com/)، واذهب إلى الاشتراكات > **اشتراكك > موردي > التسجيل في Microsoft.Insights**.

## <a name="enable-raw-data-streaming"></a>تمكين دفق البيانات الخام

1. سجل <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">دخولك Microsoft 365 Defender</a> **كمسؤول** عام * أو _*مسؤول _أمان_**.

2. انتقل **إلى الإعدادات** \> **Microsoft 365 Defender** \> **برمجة تطبيقات النقل المتدفق**. الانتقال مباشرة إلى صفحة **API** للدفق، استخدم <https://security.microsoft.com/settings/mtp_settings/raw_data_export>.

3. انقر **فوق إضافة**.

4. في قائمة **قائمة برمجة** تطبيقات إعدادات النقل المتدفق الجديدة التي تظهر، قم بتكوين الإعدادات التالية:
   1. **الاسم**: اختر اسما لإعداداتك الجديدة.
   2. حدد **إعادة توجيه الأحداث إلى Azure Storage**.
   3. في المربع **"مورد حساب** التخزين" الذي يظهر، اكتب "معرود موارد **حساب التخزين**". للحصول **على "مورد** حساب التخزين"، افتح مدخل Azure <https://portal.azure.com>في ،  \> \> وانقر فوق حسابات التخزين انتقل إلى علامة التبويب خصائص انسخ النص ضمن "مورد **حساب التخزين**".

      ![صورة لمورد مركز الحدث ID1.](../defender-endpoint/images/storage-account-resource-id.png)

   4. مرة أخرى على **قائمة قائمة برمجة** تطبيقات إضافة إعدادات تدفق جديدة، اختر أنواع **الأحداث** التي تريد دفقها.

   عند الانتهاء، انقر فوق **إرسال**.

## <a name="the-schema-of-the-events-in-the-storage-account"></a>مخطط الأحداث في حساب التخزين

- سيتم إنشاء حاوية blob لكل نوع حدث:

  ![صورة لمورد مركز الحدث ID2.](../defender-endpoint/images/storage-account-event-schema.png)

- مخطط كل صف في blob هو JSON التالي:

  ```JSON
  {
          "time": "<The time Microsoft 365 Defender received the event>"
          "tenantId": "<Your tenant ID>"
          "category": "<The Advanced Hunting table name with 'AdvancedHunting-' prefix>"
          "properties": { <Microsoft 365 Defender Advanced Hunting event as Json> }
  }
  ```

- يحتوي كل blob على صفوف متعددة.

- يحتوي كل صف على اسم الحدث والوقت الذي تلقى فيه Defender لنقطة النهاية الحدث والمستأجر الذي ينتمي إليه (ستحصل فقط على الأحداث من المستأجر)، والحدث بتنسيق JSON في خاصية تسمى "الخصائص".

- للحصول على مزيد من المعلومات حول مخطط Microsoft 365 Defender، راجع [نظرة عامة حول "الصيد المتقدم](../defender/advanced-hunting-overview.md)".

## <a name="data-types-mapping"></a>تعيين أنواع البيانات

للحصول على أنواع البيانات لخصائص الأحداث لدينا، عليك القيام بواحد من الخطوات التالية:

1. سجل <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">دخولك Microsoft 365 Defender</a> واذهب إلى **الصيد** \> **المتقدم للصيد**. انتقل مباشرة إلى صفحة **الصيد** المتقدم، استخدم <security.microsoft.com/advanced-hunting>.

2. على علامة **التبويب** استعلام، تشغيل الاستعلام التالي لتعيين أنواع البيانات لكل حدث:

   ```text
   {EventType}
   | getschema
   | project ColumnName, ColumnType
   ```

- فيما يلي مثال لحدث معلومات الجهاز:

  ![صورة لمورد مركز الحدث ID3.](../defender-endpoint/images/machine-info-datatype-example.png)

## <a name="related-topics"></a>المواضيع ذات الصلة

- [نظرة عامة حول "الصيد المتقدم"](../defender/advanced-hunting-overview.md)
- [Microsoft 365 Defender API للدفق](streaming-api.md)
- [دفق Microsoft 365 Defender الأحداث إلى حساب تخزين Azure](streaming-api-storage.md)
- [وثائق حساب تخزين Azure](/azure/storage/common/storage-account-overview)
