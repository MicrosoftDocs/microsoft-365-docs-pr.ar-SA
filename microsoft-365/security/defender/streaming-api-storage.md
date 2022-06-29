---
title: دفق أحداث Microsoft 365 Defender إلى حساب التخزين الخاص بك
description: تعرف على كيفية تكوين Microsoft 365 Defender لدفق أحداث التتبع المتقدم إلى حساب التخزين الخاص بك.
keywords: تصدير البيانات الأولية، وتدفق واجهة برمجة التطبيقات، وواجهة برمجة التطبيقات، ومراكز الأحداث، وتخزين Azure، وحساب التخزين، والتتبع المتقدم، ومشاركة البيانات الأولية
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
ms.openlocfilehash: 0f5195e5a74395073267fd4df87f077c6a1d5f20
ms.sourcegitcommit: c6f1486617b39565bfd8f662ee6ad65a9cefd3e3
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 06/29/2022
ms.locfileid: "66530565"
---
# <a name="configure-microsoft-365-defender-to-stream-advanced-hunting-events-to-your-storage-account"></a>تكوين Microsoft 365 Defender لدفق أحداث التتبع المتقدم إلى حساب التخزين الخاص بك

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**ينطبق على:**
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

[!include[Prerelease information](../../includes/prerelease.md)]

## <a name="before-you-begin"></a>قبل البدء

1. إنشاء [حساب تخزين](/azure/storage/common/storage-account-overview) في المستأجر الخاص بك.

2. سجل الدخول إلى [مستأجر Azure](https://ms.portal.azure.com/)، وانتقل إلى **الاشتراكات > اشتراكك > موفري الموارد > التسجيل في Microsoft.Insights**.

### <a name="add-contributor-permissions"></a>إضافة أذونات المساهم

بمجرد إنشاء حساب التخزين، ستحتاج إلى:

1. حدد المستخدم الذي سيقوم بتسجيل الدخول إلى Microsoft 365 Defender كمساهم.

    انتقل إلى **حساب التخزين > التحكم بالوصول (IAM) > إضافة** **والتحقق ضمن تعيينات الدور**.

## <a name="enable-raw-data-streaming"></a>تمكين دفق البيانات الأولية

1. سجل الدخول إلى <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender</a> **كمسؤول عام *أو** _*_مسؤول الأمان_**.

2. انتقل إلى **الإعدادات** \> **Microsoft 365 Defender** \> **Streaming API**. للانتقال مباشرة إلى صفحة **واجهة برمجة التطبيقات المتدفقة** ، استخدم <https://security.microsoft.com/settings/mtp_settings/raw_data_export>.

3. انقر فوق **"إضافة**".

4. في القائمة المنبثقة **"Add new Streaming API settings** " التي تظهر، قم بتكوين الإعدادات التالية:
   1. **الاسم**: اختر اسما للإعدادات الجديدة.
   2. حدد **إعادة توجيه الأحداث إلى Azure Storage**.
   3. في المربع **"معرف مورد حساب التخزين** " الذي يظهر، اكتب **معرف مورد حساب التخزين**. للحصول على **معرف مورد حساب التخزين** الخاص بك، افتح مدخل Azure في <https://portal.azure.com>، انقر فوق **حسابات** \> التخزين انتقل إلى علامة تبويب \> الخصائص لنسخ النص ضمن **معرف مورد حساب التخزين**.

      :::image type="content" source="../defender-endpoint/images/storage-account-resource-id.png" alt-text="معرف مورد حساب التخزين" lightbox="../defender-endpoint/images/storage-account-resource-id.png":::

   4. مرة أخرى في القائمة المنبثقة **"إضافة إعدادات واجهة برمجة تطبيقات الدفق الجديدة** "، اختر **أنواع الأحداث** التي تريد دفقها.

   عند الانتهاء، انقر فوق **"إرسال**".

## <a name="the-schema-of-the-events-in-the-storage-account"></a>مخطط الأحداث في حساب التخزين

- سيتم إنشاء حاوية كائن ثنائي كبير الحجم لكل نوع حدث:

  :::image type="content" source="../defender-endpoint/images/storage-account-event-schema.png" alt-text="مثال على حاوية كائن ثنائي كبير الحجم" lightbox="../defender-endpoint/images/storage-account-event-schema.png":::

- مخطط كل صف في الكائن الثنائي كبير الحجم هو JSON التالي:

  ```JSON
  {
          "time": "<The time Microsoft 365 Defender received the event>"
          "tenantId": "<Your tenant ID>"
          "category": "<The Advanced Hunting table name with 'AdvancedHunting-' prefix>"
          "properties": { <Microsoft 365 Defender Advanced Hunting event as Json> }
  }
  ```

- يحتوي كل كائن ثنائي كبير الحجم على صفوف متعددة.

- يحتوي كل صف على اسم الحدث، والوقت الذي تلقى فيه Defender لنقطة النهاية الحدث، والمستأجر الذي ينتمي إليه (ستحصل فقط على الأحداث من المستأجر)، والحدث بتنسيق JSON في خاصية تسمى "خصائص".

- لمزيد من المعلومات حول مخطط أحداث Microsoft 365 Defender، راجع [نظرة عامة على Advanced Hunting](../defender/advanced-hunting-overview.md).

## <a name="data-types-mapping"></a>تعيين أنواع البيانات

للحصول على أنواع البيانات لخصائص الأحداث، قم بما يلي:

1. سجل الدخول <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">إلى Microsoft 365 Defender</a> وانتقل إلى **التتبع** \> **المتقدم**. للانتقال مباشرة إلى صفحة **التتبع المتقدم** ، استخدم <security.microsoft.com/advanced-hunting>.

2. في علامة التبويب **"استعلام** "، قم بتشغيل الاستعلام التالي للحصول على تعيين أنواع البيانات لكل حدث:

   ```text
   {EventType}
   | getschema
   | project ColumnName, ColumnType
   ```

- فيما يلي مثال لحدث معلومات الجهاز:

  :::image type="content" source="../defender-endpoint/images/machine-info-datatype-example.png" alt-text="مثال على استعلام معلومات الجهاز" lightbox="../defender-endpoint/images/machine-info-datatype-example.png":::

## <a name="monitoring-created-resources"></a>مراقبة الموارد التي تم إنشاؤها

يمكنك مراقبة الموارد التي تم إنشاؤها بواسطة واجهة برمجة التطبيقات المتدفقة باستخدام **Azure Monitor**. لمزيد من المعلومات، راجع [وجهات المراقبة - | Azure Monitor Microsoft Docs](/azure/azure-monitor/logs/logs-data-export?tabs=portal#monitor-destinations).

## <a name="related-topics"></a>المواضيع ذات الصلة

- [نظرة عامة على التتبع المتقدم](../defender/advanced-hunting-overview.md)
- [واجهة برمجة تطبيقات تدفق Microsoft 365 Defender](streaming-api.md)
- [دفق أحداث Microsoft 365 Defender إلى حساب تخزين Azure](streaming-api-storage.md)
- [وثائق حساب تخزين Azure](/azure/storage/common/storage-account-overview)
