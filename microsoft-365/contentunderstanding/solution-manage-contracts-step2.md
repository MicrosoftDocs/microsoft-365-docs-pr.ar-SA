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
description: تعرف على كيفية استخدام Microsoft Teams لإنشاء قناة إدارة العقود باستخدام Microsoft 365 جديد.
ms.openlocfilehash: a5a42bedcb6acba4caf8f6f114812c63869ee92e
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 10/06/2021
ms.locfileid: "63571659"
---
# <a name="step-2-use-microsoft-teams-to-create-your-contract-management-channel"></a>الخطوة 2. استخدام Microsoft Teams لإنشاء قناة إدارة العقود

عندما تقوم مؤسستك بتعيين حل لإدارة العقود، تحتاج إلى موقع مركزي حيث يمكن للمساهمين مراجعة العقود وإدارتها. لهذا الغرض، يمكنك [استخدام Microsoft Teams لإعداد](/microsoftteams/) قناة Teams واستخدام الميزات في Teams:

- **أنشئ موقع المساهمين لرؤية كل التعاقدات التي تتطلب اتخاذ إجراء بسهولة.** على سبيل المثال، في Teams، يمكنك إنشاء علامة تبويب العقود في قناة إدارة التعاقدات حيث يمكن للأعضاء رؤية طريقة عرض لوحة مفيدة لكل العقود التي تحتاج إلى الموافقة. يمكنك أيضا تكوين طريقة العرض بحيث تسرد كل "بطاقة" البيانات المهمة التي تهتم بها (مثل *العميل* والمقاول ومبلغ *الرسوم*).

     ![علامة تبويب العقود.](../media/content-understanding/tile-view.png)

- **الحصول على موقع للأعضاء للتفاعل مع بعضهم البعض لمشاهدة الأحداث المهمة.** على سبيل المثال، في Teams، يمكن استخدام علامة  التبويب منشورات للحصول على المحادثات والحصول على التحديثات ورؤية الإجراءات (مثل رفض عضو لتعاقد). عند حدوث شيء ما (مثل تعاقد جديد تم إرساله للموافقة عليه)، يمكن  استخدام علامة التبويب منشورات ليس للإعلان عنها فقط، ولكن أيضا لإبقاء سجل لها. وإذا اشترك الأعضاء في الإعلامات، سيتم إعلامهم كلما كان هناك تحديث.

     ![علامة تبويب المنشورات.](../media/content-understanding/posts.png)

- **الحصول على موقع للأعضاء لرؤية العقود المعتمدة لمعرفة متى يمكن إرسالها للدفع.** في SharePoint، ستحتاج إلى إنشاء قائمة مقابل مع تضمين أعمدة لمبلغ "العميل" و"المتعاقد" و"الرسوم"، وتحديد سطر نص واحد كنوع العمود. ستحتاج إلى إضافة قائمة مقابل Teams علامة  تبويب في قناة إدارة العقود، تماما كما تفعل ل علامة التبويب [العقود](solution-manage-contracts-step2.md#attach-your-sharepoint-document-library-to-the-contracts-tab). **ستضم علامة التبويب** مقابل جميع التعاقدات التي يجب إرسالها للدفع. يمكنك توسيع هذا الحل بسهولة لكتابة هذه المعلومات مباشرة بدلا من ذلك إلى تطبيق مالي من جهة خارجية (على سبيل المثال، Dynamics CRM). 


## <a name="attach-your-sharepoint-document-library-to-the-contracts-tab"></a>إرفاق مكتبة مستندات SharePoint إلى علامة التبويب "العقود"

بعد إنشاء علامة **تبويب** العقود في قناة إدارة العقود، ستحتاج إلى إرفاق SharePoint [مستنداتك بها](https://support.microsoft.com/office/add-a-sharepoint-page-list-or-document-library-as-a-tab-in-teams-131edef1-455f-4c67-a8ce-efa2ebf25f0b). إن SharePoint المستندات التي تريد إرفاقها هي تلك التي قمت بتطبيق نموذج SharePoint Syntex المستند عليها في المقطع السابق.

بعد إرفاق SharePoint المستندات، ستكون قادرا على عرض أي عقود مصنفة من خلال طريقة عرض قائمة افتراضية.

   ![طريقة عرض القائمة SharePoint المكتبة.](../media/content-understanding/list-view.png)

## <a name="customize-your-contracts-tab-tile-view"></a>تخصيص طريقة عرض لوحة علامة التبويب "العقود"

> [!NOTE]
> يشير هذا القسم إلى أمثلة التعليمات البرمجية المضمنة في ملف [ContractTileFormatting.json](https://github.com/pnp/syntex-samples/blob/main/scenario%20assets/Contracts%20Management/View%20Formatter/ContractTileFormatting.json) المضمن في مستودع أصول حل إدارة [العقود](https://github.com/pnp/syntex-samples/tree/main/scenario%20assets/Contracts%20Management).

بينما Teams عرض العقود في طريقة عرض اللوحة، قد ترغب في تخصيصها لعرض بيانات العقد التي تريد جعلها مرئية في بطاقة العقد. على سبيل المثال، بالنسبة  إلى علامة التبويب عقود، من المهم أن يرى الأعضاء العميل والمقاول ومبلغ الرسوم على بطاقة العقد. تم استخراج كل هذه الحقول من كل عقد SharePoint Syntex النموذج الذي تم تطبيقه على مكتبة المستندات. كما تريد أيضا أن تكون قادرا على تغيير شريط رأس اللوحة إلى ألوان مختلفة لكل حالة بحيث يمكن للأعضاء رؤية مكان العقد بسهولة في عملية الموافقة. على سبيل المثال، سيكون لكل العقود المعتمدة شريط رأس أزرق.

   ![طريقة عرض SharePoint مكتبة.](../media/content-understanding/tile.png)

تتطلب طريقة عرض اللوحة المخصصة التي تستخدمها إجراء تغييرات على ملف JSON المستخدم لتنسيق طريقة عرض اللوحة الحالية. يمكنك الرجوع إلى ملف JSON المستخدم لإنشاء طريقة عرض البطاقة بالنظر إلى [ملف ContractTileFormatting.json](https://github.com/pnp/syntex-samples/blob/main/scenario%20assets/Contracts%20Management/View%20Formatter/ContractTileFormatting.json) . في الأقسام التالية، سترى مقاطع معينة من التعليمات البرمجية للميزات في بطاقات العقد.

إذا كنت تريد رؤية التعليمات البرمجية JSON ل طريقة العرض في قناة Teams أو إدخال تغييرات عليها، ففي قناة Teams، حدد القائمة المنسدلة طريقة العرض، ثم حدد تنسيق طريقة العرض **الحالية**.

   ![لقطة شاشة لتنسيق json Teams قناة.](../media/content-understanding/jason-format.png)

## <a name="card-size-and-shape"></a>حجم البطاقة وشكلها

في [الملف ContractTileFormatting.json](https://github.com/pnp/syntex-samples/blob/main/scenario%20assets/Contracts%20Management/View%20Formatter/ContractTileFormatting.json) ، انظر إلى المقطع التالي لمعرفة التعليمات البرمجية الخاصة بكيفية تنسيق حجم البطاقة وشكلها.

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

## <a name="contract-status"></a>حالة التعاقد

تتيح لك التعليمة البرمجية التالية تحديد حالة كل بطاقة عنوان. لاحظ أن كل قيمة حالة (*جديد*، *قيد المراجعة*، تمت الموافقة عليه، *مرفوض) ستعرض* رمز لون مختلف لكل منها. في [ملف ContractTileFormatting.json](https://github.com/pnp/syntex-samples/blob/main/scenario%20assets/Contracts%20Management/View%20Formatter/ContractTileFormatting.json) ، انظر إلى المقطع الذي يعرف الحالة.

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

تعرض كل بطاقة تعاقد ثلاثة حقول تم استخراجها لكل عقد (*العميل* *والمقاول ومبلغ الرسوم*). بالإضافة إلى ذلك، تريد أيضا عرض الوقت/التاريخ الذي تم فيه تصنيف الملف حسب SharePoint Syntex المستخدم لتعريفه.

في [الملف ContractTileFormatting.json](https://github.com/pnp/syntex-samples/blob/main/scenario%20assets/Contracts%20Management/View%20Formatter/ContractTileFormatting.json) ، تحدد المقاطع التالية كل واحد من هذه.

### <a name="client"></a>Client

يعرف هذا القسم كيفية عرض "العميل" على البطاقة، ويستخدم القيمة الخاصة بالتعاقد المحدد.

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

### <a name="contractor"></a>المتعاقد

يعرف هذا القسم كيفية عرض "المتعاقد" على البطاقة، ويستخدم القيمة الخاصة بالتعاقد المحدد.

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

يعرف هذا القسم كيفية عرض "مبلغ الرسوم" على البطاقة، ويستخدم القيمة الخاصة بالتعاقد المحدد.

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

يعرف هذا القسم كيفية عرض "التصنيف" على البطاقة، ويستخدم القيمة الخاصة بالتعاقد المحدد.

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

[الخطوة 3. استخدم Power Automate لإنشاء التدفق لمعالجة العقود الخاصة بك](solution-manage-contracts-step3.md)
