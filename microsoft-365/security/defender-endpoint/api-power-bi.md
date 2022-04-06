---
title: Microsoft Defender لنقطة النهاية واجهات برمجة التطبيقات ل Power BI
ms.reviewer: ''
description: إنشاء تقرير Power Business Intelligence (BI) أعلى Microsoft Defender لنقطة النهاية برمجة التطبيقات.
keywords: apis، apis المعتمدة، تقارير Power BI
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
MS.technology: mde
ms.custom: api
ms.openlocfilehash: 4cad6fd5188745773ce561d1db697989598a1dc5
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/25/2022
ms.locfileid: "64472144"
---
# <a name="create-custom-reports-using-power-bi"></a>إنشاء تقارير مخصصة باستخدام Power BI

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**
- [Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)


- هل تريد تجربة Microsoft Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

في هذا القسم، ستتعلم كيفية إنشاء تقرير Power BI أعلى "Defender" ل واجهات برمجة التطبيقات لنقطة النهاية.

يوضح المثال الأول كيفية توصيل Power BI ب API للصيد المتقدم، بينما يوضح المثال الثاني اتصالا ب واجهات برمجة التطبيقات OData، مثل إجراءات الجهاز أو التنبيهات.

## <a name="connect-power-bi-to-advanced-hunting-api"></a>الاتصال Power BI إلى API للصيد المتقدم

- افتح Microsoft Power BI.

- انقر **فوق الحصول على استعلام** \> **البيانات الفارغ**.

  :::image type="content" source="images/power-bi-create-blank-query.png" alt-text="الخيار &quot;استعلام فارغ&quot; ضمن عنصر القائمة &quot;الحصول على البيانات&quot;" lightbox="images/power-bi-create-blank-query.png":::

- انقر **فوق محرر متقدم**.

  :::image type="content" source="images/power-bi-open-advanced-editor.png" alt-text="عنصر القائمة &quot;المحرر المتقدم&quot;" lightbox="images/power-bi-open-advanced-editor.png":::

- انسخ ما يلي واللصق في المحرر:

```
    let
        AdvancedHuntingQuery = "DeviceEvents | where ActionType contains 'Anti' | limit 20",

        HuntingUrl = "https://api.securitycenter.microsoft.com/api/advancedqueries",

        Response = Json.Document(Web.Contents(HuntingUrl, [Query=[key=AdvancedHuntingQuery]])),

        TypeMap = #table(
            { "Type", "PowerBiType" },
            {
                { "Double",   Double.Type },
                { "Int64",    Int64.Type },
                { "Int32",    Int32.Type },
                { "Int16",    Int16.Type },
                { "UInt64",   Number.Type },
                { "UInt32",   Number.Type },
                { "UInt16",   Number.Type },
                { "Byte",     Byte.Type },
                { "Single",   Single.Type },
                { "Decimal",  Decimal.Type },
                { "TimeSpan", Duration.Type },
                { "DateTime", DateTimeZone.Type },
                { "String",   Text.Type },
                { "Boolean",  Logical.Type },
                { "SByte",    Logical.Type },
                { "Guid",     Text.Type }
            }),

        Schema = Table.FromRecords(Response[Schema]),
        TypedSchema = Table.Join(Table.SelectColumns(Schema, {"Name", "Type"}), {"Type"}, TypeMap , {"Type"}),
        Results = Response[Results],
        Rows = Table.FromRecords(Results, Schema[Name]),
        Table = Table.TransformColumnTypes(Rows, Table.ToList(TypedSchema, (c) => {c{0}, c{2}}))

    in Table
```

- انقر **فوق تم**.

- انقر **فوق تحرير بيانات الاعتماد**.

    :::image type="content" source="images/power-bi-edit-credentials.png" alt-text="عنصر القائمة &quot;تحرير بيانات الاعتماد&quot;" lightbox="images/power-bi-edit-credentials.png":::
    

- حدد **حساب المؤسسة تسجيل** \> **الدخول**.

    :::image type="content" source="images/power-bi-set-credentials-organizational.png" alt-text="الخيار &quot;تسجيل الدخول&quot; في عنصر القائمة &quot;حساب المؤسسة&quot;" lightbox="images/power-bi-set-credentials-organizational.png":::

- أدخل بيانات الاعتماد وانتظر حتى يتم تسجيل الدخول.

- انقر **الاتصال**.

    :::image type="content" source="images/power-bi-set-credentials-organizational-cont.png" alt-text="رسالة تأكيد تسجيل الدخول في عنصر القائمة حساب المؤسسة" lightbox="images/power-bi-set-credentials-organizational-cont.png":::

- ستظهر الآن نتائج الاستعلام ك جدول، كما يمكنك البدء في إنشاء مرئيات فوقه!

- يمكنك تكرار هذا الجدول وإعادة تسميته وتحرير استعلام "البحث المتقدم" داخله للحصول على أي بيانات تريدها.

## <a name="connect-power-bi-to-odata-apis"></a>الاتصال واجهات برمجة التطبيقات في Power BI إلى OData

- الفرق الوحيد عن المثال أعلاه هو الاستعلام داخل المحرر.

- انسخ ما يلي واللصق في المحرر لسحب كافة **إجراءات الجهاز** من مؤسستك:

```
    let

        Query = "MachineActions",

        Source = OData.Feed("https://api.securitycenter.microsoft.com/api/" & Query, null, [Implementation="2.0", MoreColumns=true])
    in
        Source
```

- يمكنك القيام بالشيء نفسه **للتنبيهات** **و الأجهزة**.
- يمكنك أيضا استخدام استعلامات OData لتصفية الاستعلامات، راجع [استخدام استعلامات OData](exposed-apis-odata-samples.md).

## <a name="power-bi-dashboard-samples-in-github"></a>نماذج لوحة معلومات Power BI في GitHub

لمزيد من المعلومات، راجع قوالب [تقارير Power BI](https://github.com/microsoft/MicrosoftDefenderATP-PowerBI).

## <a name="sample-reports"></a>نماذج التقارير

عرض Microsoft Defender لنقطة النهاية تقرير Power BI. لمزيد من المعلومات، راجع [استعراض نماذج التعليمات البرمجية](/samples/browse/?products=mdatp).

## <a name="related-topics"></a>المواضيع ذات الصلة

- [Defender ل واجهات برمجة التطبيقات لنقطة النهاية](apis-intro.md)
- [API للصيد المتقدم](run-advanced-query-api.md)
- [استخدام استعلامات OData](exposed-apis-odata-samples.md)
