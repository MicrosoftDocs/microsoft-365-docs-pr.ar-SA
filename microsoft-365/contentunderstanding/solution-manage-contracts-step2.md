---
title: الخطوة 2. استخدام Microsoft Teams لإنشاء قناة إدارة العقود
ms.author: chucked
author: chuckedmonson
manager: pamgreen
ms.reviewer: ssquires
audience: admin
ms.topic: article
ms.date: ''
ms.prod: microsoft-365-enterprise
search.appverid: ''
ms.localizationpriority: medium
ROBOTS: ''
description: تعرف على كيفية استخدام Microsoft Teams لإنشاء قناة إدارة العقود باستخدام حل Microsoft 365.
ms.openlocfilehash: 6020b6e57af285e96c7998454dc46e5eb19bc5f9
ms.sourcegitcommit: 344a254ca268a2f65cf199d9158a47e08861ffa5
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 05/12/2022
ms.locfileid: "65368034"
---
# <a name="step-2-use-microsoft-teams-to-create-your-contract-management-channel"></a>الخطوة 2. استخدام Microsoft Teams لإنشاء قناة إدارة العقود

عندما تقوم مؤسستك بإعداد حل لإدارة العقود، تحتاج إلى موقع مركزي حيث يمكن للمساهمين مراجعة العقود وإدارتها. لهذا الغرض، يمكنك استخدام [Microsoft Teams](/microsoftteams/) لإعداد قناة Teams واستخدام الميزات في Teams من أجل:

- **إنشاء موقع لأصحاب المصلحة للاطلاع بسهولة على جميع العقود التي تتطلب اتخاذ إجراء.** على سبيل المثال، في Teams يمكنك إنشاء علامة تبويب **"العقود**" في قناة "إدارة العقود" حيث يمكن للأعضاء رؤية عرض إطار متجانب مفيد لكافة العقود التي تحتاج إلى موافقة. يمكنك أيضا تكوين طريقة العرض بحيث تسرد كل "بطاقة" البيانات المهمة التي تهتم بها (مثل *العميل* *والمقاول* *ومبلغ الرسوم*).

     ![علامة تبويب العقود.](../media/content-understanding/tile-view.png)

- **لديك موقع للأعضاء للتفاعل مع بعضهم البعض ورؤية الأحداث المهمة.** على سبيل المثال، في Teams، يمكن استخدام علامة التبويب **"منشورات**" لإجراء المحادثات والحصول على التحديثات ورؤية الإجراءات (مثل رفض أحد الأعضاء للعقد). عند حدوث شيء ما (مثل عقد جديد تم إرساله للموافقة عليه)، يمكن استخدام علامة التبويب **"منشورات** " ليس فقط للإعلان عنه، ولكن أيضا للاحتفاظ بسجل له. وإذا اشترك الأعضاء في الإعلامات، فسيتم إعلامهم كلما كان هناك تحديث.

     ![علامة التبويب "منشورات".](../media/content-understanding/posts.png)

- **لديك موقع للأعضاء للاطلاع على العقود المعتمدة لمعرفة متى يمكن إرسالها للدفع.** في SharePoint، ستحتاج إلى إنشاء قائمة **مقابل المقابل المالي** وتضمين **أعمدة للعميل** **والمقاول** **ومبلغ الرسوم**، وتحديد **سطر نص واحد** كنوع العمود. ستحتاج إلى إضافة قائمة **"مقابل المقابل المالي**" كعلامة تبويب Teams في قناة "إدارة العقود"، على غرار [ما ستفعله لعلامة التبويب **"العقود**](solution-manage-contracts-step2.md#attach-your-sharepoint-document-library-to-the-contracts-tab)". ستدرج علامة التبويب **"مقابل المقابل المالي**" جميع العقود التي ستحتاج إلى إرسالها للدفع. يمكنك بسهولة توسيع هذا الحل لكتابة هذه المعلومات مباشرة إلى تطبيق مالي تابع لجهة خارجية (على سبيل المثال، Dynamics CRM). 


## <a name="attach-your-sharepoint-document-library-to-the-contracts-tab"></a>إرفاق مكتبة مستندات SharePoint بعلامة التبويب Contracts

بعد إنشاء علامة تبويب **"العقود**" في قناة "إدارة العقود"، تحتاج إلى [إرفاق مكتبة مستندات SharePoint بها](https://support.microsoft.com/office/add-a-sharepoint-page-list-or-document-library-as-a-tab-in-teams-131edef1-455f-4c67-a8ce-efa2ebf25f0b). مكتبة المستندات SharePoint التي تريد إرفاقها هي المكتبة التي قمت بتطبيق نموذج فهم المستندات SharePoint Syntex عليها في المقطع السابق.

بعد إرفاق مكتبة المستندات SharePoint، ستتمكن من عرض أي عقود مصنفة من خلال طريقة عرض قائمة افتراضية.

   ![طريقة عرض قائمة لمكتبة SharePoint.](../media/content-understanding/list-view.png)

## <a name="customize-your-contracts-tab-tile-view"></a>تخصيص طريقة عرض تجانب علامة التبويب Contracts

> [!NOTE]
> يشير هذا القسم إلى أمثلة التعليمات البرمجية الموجودة في ملف [ContractTileFormatting.json](https://github.com/pnp/syntex-samples/blob/main/scenario%20samples/Contracts%20Management/View%20Formatter/ContractTileFormatting.json) المضمن في [مستودع أصول حل إدارة العقود](https://github.com/pnp/syntex-samples/tree/main/scenario%20samples/Contracts%20Management).

بينما يتيح لك Teams عرض عقودك في طريقة عرض اللوحة، قد تحتاج إلى تخصيصها لعرض بيانات العقد التي تريد إظهارها في بطاقة العقد. على سبيل المثال، بالنسبة لعلامة التبويب **Contracts** ، من المهم أن يرى الأعضاء مبلغ العميل والمقاول والرسوم على بطاقة العقد. تم استخراج كل هذه الحقول من كل عقد من خلال نموذج SharePoint Syntex الذي تم تطبيقه على مكتبة المستندات. تريد أيضا أن تكون قادرا على تغيير شريط رأس اللوحة إلى ألوان مختلفة لكل حالة بحيث يمكن للأعضاء بسهولة معرفة مكان العقد في عملية الموافقة. على سبيل المثال، ستحتوي جميع العقود المعتمدة على شريط رأس أزرق.

   ![طريقة عرض اللوحة لمكتبة SharePoint.](../media/content-understanding/tile.png)

تتطلب طريقة عرض اللوحة المخصصة التي تستخدمها إجراء تغييرات على ملف JSON المستخدم لتنسيق طريقة عرض اللوحة الحالية. يمكنك الرجوع إلى ملف JSON المستخدم لإنشاء طريقة عرض البطاقة من خلال النظر إلى ملف [ContractTileFormatting.json](https://github.com/pnp/syntex-samples/blob/main/scenario%20samples/Contracts%20Management/View%20Formatter/ContractTileFormatting.json) . في الأقسام التالية، سترى أقساما معينة من التعليمات البرمجية للميزات الموجودة في بطاقات العقد.

إذا كنت تريد رؤية رمز JSON أو إجراء تغييرات عليه لطريقة العرض الخاصة بك في قناة Teams، في القناة Teams، حدد القائمة المنسدلة لطريقة العرض، ثم حدد **"تنسيق طريقة العرض الحالية**".

   ![لقطة شاشة لتنسيق json في قناة Teams.](../media/content-understanding/jason-format.png)

## <a name="card-size-and-shape"></a>حجم البطاقة وشكلها

في ملف [ContractTileFormatting.json](https://github.com/pnp/syntex-samples/blob/main/scenario%20samples/Contracts%20Management/View%20Formatter/ContractTileFormatting.json) ، انظر إلى القسم التالي للاطلاع على التعليمات البرمجية لكيفية تنسيق حجم البطاقة وشكلها.

```JSON
                  {
                    "elmType": "div",
                    "style": {
                      "background-color": "#f5f5f5",
                      "padding": "5px",
                      "width": "180px"
                    },
                    "children": [
                      {
                        "elmType": "img",
                        "attributes": {
                          "src": "@thumbnail.large"
                        },
                        "style": {
                          "width": "185px",
                          "height": "248px"
                        }
                      }
```

## <a name="contract-status"></a>حالة العقد

تتيح لك التعليمات البرمجية التالية تحديد حالة كل بطاقة عنوان. لاحظ أن كل قيمة حالة (*جديدة*، *قيد المراجعة*، *معتمدة*، *مرفوضة*) ستعرض رمز لون مختلف لكل منهما. في ملف [ContractTileFormatting.json](https://github.com/pnp/syntex-samples/blob/main/scenario%20samples/Contracts%20Management/View%20Formatter/ContractTileFormatting.json) ، انظر إلى المقطع الذي يحدد الحالة.

```JSON
          {
            "elmType": "div",
            "children": [
              {
                "elmType": "div",
                "style": {
                  "color": "white",
                  "background-color": "=if([$Status] == 'New', '#00b7c3', if([$Status] == 'In review', '#ffaa44', if([$Status] == 'Approved', '#0078d4', if([$Status] == 'Rejected', '#d13438', '#8378de'))))",
                  "padding": "5px 15px",
                  "height": "auto",
                  "text-transform": "uppercase",
                  "font-size": "12.5px"
                },
                "txtContent": "[$Status]"
              }
```

## <a name="extracted-fields"></a>الحقول المستخرجة

ستعرض كل بطاقة عقد ثلاثة حقول تم استخراجها لكل عقد (*العميل* *والمقاول* *ومبلغ الرسوم*). بالإضافة إلى ذلك، تريد أيضا عرض الوقت/التاريخ الذي تم فيه تصنيف الملف بواسطة نموذج SharePoint Syntex المستخدم لتعريفه.

في ملف [ContractTileFormatting.json](https://github.com/pnp/syntex-samples/blob/main/scenario%20samples/Contracts%20Management/View%20Formatter/ContractTileFormatting.json) ، تعرف الأقسام التالية كل من هذه.

### <a name="client"></a>Client

يحدد هذا القسم كيفية عرض "العميل" على البطاقة، ويستخدم قيمة العقد المحدد.

```JSON
                      {
                        "elmType": "div",
                        "style": {
                          "color": "#767676",
                          "font-size": "12px"
                        },
                        "txtContent": "Client"
                      },
                      {
                        "elmType": "div",
                        "style": {
                          "margin-bottom": "12px",
                          "font-size": "16px",
                          "font-weight": "600"
                        },
                        "txtContent": "[$Client]"
                      },
```

### <a name="contractor"></a>المقاول

يحدد هذا القسم كيفية عرض "المتعهد" على البطاقة، ويستخدم قيمة العقد المحدد.

```JSON
                        {
                          "elmType": "div",
                          "txtContent": "Contractor",
                          "style": {
                            "color": "#767676",
                            "font-size": "12px",
                            "margin-bottom": "2px"
                          }
                        },
                        {
                          "elmType": "div",
                          "style": {
                            "margin-bottom": "12px",
                            "font-size": "14px"
                          },
                          "txtContent": "[$Contractor]"
                        },
```

### <a name="fee-amount"></a>مبلغ الرسوم

يحدد هذا القسم كيفية عرض "مبلغ الرسوم" على البطاقة، ويستخدم قيمة العقد المحدد.

```JSON
                      {
                        "elmType": "div",
                        "txtContent": "Fee amount",
                        "style": {
                          "color": "#767676",
                          "font-size": "12px",
                          "margin-bottom": "2px"
                        }
                      },
                      {
                        "elmType": "div",
                        "style": {
                          "margin-bottom": "12px",
                          "font-size": "14px"
                        },
                        "txtContent": "[$FeeAmount]"
                      },
```

### <a name="classification-date"></a>تاريخ التصنيف

يحدد هذا القسم كيفية عرض "التصنيف" على البطاقة، ويستخدم قيمة العقد المحدد.

```JSON
                      {
                        "elmType": "div",
                        "txtContent": "Classified",
                        "style": {
                          "color": "#767676",
                          "font-size": "12px",
                          "margin-bottom": "2px"
                        }
                      },
                      {
                        "elmType": "div",
                        "style": {
                          "margin-bottom": "12px",
                          "font-size": "14px"
                        },
                        "txtContent": "[$PrimeLastClassified]"
                      }
```

## <a name="next-step"></a>الخطوة التالية

[الخطوة 3. استخدم Power Automate لإنشاء التدفق لمعالجة عقودك](solution-manage-contracts-step3.md)
