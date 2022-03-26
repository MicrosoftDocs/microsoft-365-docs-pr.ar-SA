---
title: اتصال واجهات برمجة تطبيقات Microsoft Defender لنقطة النهاية ب Power BI
ms.reviewer: ''
description: إنشاء تقرير Power Business Intelligence (BI) أعلى Microsoft Defender ل واجهات برمجة تطبيقات نقطة النهاية.
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
ms.openlocfilehash: 765af5e4a2e880aa9b6c1208495537ad8cf5f26b
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 11/24/2021
ms.locfileid: "63569913"
---
# <a name="create-custom-reports-using-power-bi"></a>إنشاء تقارير مخصصة باستخدام Power BI

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**
- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)


- هل تريد تجربة Microsoft Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

في هذا القسم، ستتعرف على إنشاء تقرير Power BI أعلى واجهات برمجة التطبيقات ل Defender لنقطة النهاية.

يوضح المثال الأول كيفية توصيل Power BI ب API للصيد المتقدم، بينما يوضح المثال الثاني اتصالا ب واجهات برمجة التطبيقات OData، مثل إجراءات الجهاز أو التنبيهات.

## <a name="connect-power-bi-to-advanced-hunting-api"></a>الاتصال Power BI إلى API للصيد المتقدم

- فتح Microsoft Power BI

- انقر **فوق الحصول على استعلام** \> **البيانات الفارغ**

  ![صورة لإنشاء استعلام فارغ.](images/power-bi-create-blank-query.png)

- انقر **فوق محرر متقدم**

  ![صورة المحرر المتقدم المفتوح.](images/power-bi-open-advanced-editor.png)

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

- انقر **فوق تم**

- انقر **فوق تحرير بيانات الاعتماد**

    ![صورة لتحرير بيانات الاعتماد0.](images/power-bi-edit-credentials.png)

- حدد **حساب المؤسسة تسجيل** \> **الدخول**

    ![صورة لتعيين بيانات الاعتماد1.](images/power-bi-set-credentials-organizational.png)

- أدخل بيانات الاعتماد وانتظر حتى يتم تسجيل الدخول

- انقر **الاتصال**

    ![صورة لتعيين بيانات الاعتماد2.](images/power-bi-set-credentials-organizational-cont.png)

- ستظهر الآن نتائج الاستعلام ك جدول، كما يمكنك بدء إنشاء مرئيات فوقه!

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
- يمكنك أيضا استخدام استعلامات OData لتصفية الاستعلامات، راجع [استخدام استعلامات OData](exposed-apis-odata-samples.md)

## <a name="power-bi-dashboard-samples-in-github"></a>نماذج لوحة معلومات Power BI في GitHub

لمزيد من المعلومات، راجع قوالب [تقارير Power BI](https://github.com/microsoft/MicrosoftDefenderATP-PowerBI).

## <a name="sample-reports"></a>نماذج التقارير

عرض عينات تقرير Microsoft Defender ل Endpoint Power BI. لمزيد من المعلومات، راجع [استعراض نماذج التعليمات البرمجية](/samples/browse/?products=mdatp).

## <a name="related-topics"></a>المواضيع ذات الصلة

- [Defender ل واجهات برمجة التطبيقات لنقطة النهاية](apis-intro.md)
- [API للصيد المتقدم](run-advanced-query-api.md)
- [استخدام استعلامات OData](exposed-apis-odata-samples.md)
