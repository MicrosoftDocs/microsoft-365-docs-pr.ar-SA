---
title: الخطوة 3. استخدم Power Automate لإنشاء التدفق لمعالجة العقود الخاصة بك
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
description: تعرف على كيفية استخدام Power Automate لإنشاء التدفق لمعالجة تعاقداتك باستخدام Microsoft 365 جديد.
ms.openlocfilehash: d83fb6e5ca911cbafc6f064c615ab15ae0f570c7
ms.sourcegitcommit: f3c912780bbcf5a5b47de192202adb3afbd5952b
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 01/26/2022
ms.locfileid: "63575511"
---
# <a name="step-3-use-power-automate-to-create-the-flow-to-process-your-contracts"></a>الخطوة 3. استخدم Power Automate لإنشاء التدفق لمعالجة العقود الخاصة بك

لقد أنشأت قناة إدارة العقود وأرفقت SharePoint مستنداتك. الخطوة التالية هي إنشاء تدفق Power Automate لمعالجة العقود التي يحددها SharePoint Syntex الخاص بك ويصنفها. يمكنك القيام بهذه الخطوة عن طريق [إنشاء Power Automate في مكتبة SharePoint المستندات](https://support.microsoft.com/office/create-a-flow-for-a-list-or-library-in-sharepoint-or-onedrive-a9c3e03b-0654-46af-a254-20252e580d01).

للحصول على حل إدارة العقود، تريد إنشاء Power Automate جديد للقيام بما يلي:

-  بعد تصنيف العقد حسب SharePoint Syntex الخاص بك، غير حالة العقد إلى **قيد المراجعة**.
- بعد ذلك، يتم مراجعة العقد وإما أن يكون معتمدا أو مرفوضا.
- بالنسبة للتعاقدات المعتمدة، يتم نشر معلومات العقد في علامة تبويب لمعالجة الدفع.
- بالنسبة للتعاقدات المرفوضة، يتم إعلام الفريق لمزيد من التحليل. 

يعرض الرسم التخطيطي التالي Power Automate تدفق حل إدارة التعاقدات.

![Flow التخطيطي يعرض الحل بأكمله.](../media/content-understanding/flow-entire-process.png)

## <a name="prepare-your-contract-for-review"></a>تحضير تعاقدك للمراجعة

عند تحديد تعاقد وتصنيفه حسب نموذج SharePoint Syntex المستند، سيغير تدفق Power Automate أولا الحالة إلى **قيد المراجعة**.

![تحديث الحالة.](../media/content-understanding/flow-overview.png)

بعد سحب الملف، غير قيمة الحالة إلى **قيد المراجعة**.

![في حالة المراجعة.](../media/content-understanding/in-review.png)

الخطوة التالية هي إنشاء بطاقة تكييفية تفيد بأن العقد بانتظار مراجعته ونشره إلى قناة إدارة التعاقدات.

![منشور مراجعة العقد.](../media/content-understanding/contract-approval-post.png)


![إنشاء بطاقة تكييفية للمراجعة.](../media/content-understanding/adaptive-card.png)

التعليمة البرمجية التالية هي JSON المستخدمة لهذه الخطوة في Power Automate.

```JSON
{
"$schema": "http://adaptivecards.io/schemas/adaptive-card.json",
"type": "AdaptiveCard",
"version": "1.0",
"body": [
    {
    "type": "TextBlock",
    "text": "Contract approval request",
    "size": "large",
    "weight": "bolder",
     "wrap": true
    },
        {
            "type": "Container",
            "items": [
                {
                    "type": "FactSet",
                    "spacing": "Large",
                    "facts": [
                        {
                            "title": "Client",
                            "value": "@{triggerOutputs()?['body/Client']}"
                        },
                        {
                            "title": "Contractor",
                            "value": "@{triggerOutputs()?['body/Contractor']}"
                        },
                        {
                            "title": "Fee amount",
                            "value": "@{triggerOutputs()?['body/FeeAmount']}"
                        },
                        {
                            "title": "Date created",
                            "value": "@{triggerOutputs()?['body/Modified']} "
                        },
                        {
                            "title": "Link",
                            "value": "[@{triggerOutputs()?['body/{FilenameWithExtension}']}](@{triggerOutputs()?['body/{Link}']})"
                        }
                    ]
                }
            ]
         },
    {
    "type": "TextBlock",
    "text": "Comment:"
    },
        {
            "type": "Input.Text",
            "placeholder": "Enter comments",
            "id": "acComments"
        }
],
"actions": [
    {
    "type": "Action.Submit",
    "title": "Approve",
    "data": {
        "x": "Approve"
    }
    },
    {
    "type": "Action.Submit",
    "title": "Reject",
    "data": {
        "x": "Reject"
    }
    }
]
}
```


## <a name="conditional-context"></a>السياق الشرطي

في التدفق، ستحتاج بعد ذلك إلى إنشاء شرط يتم فيه الموافقة على العقد أو [رفضه](#if-the-contract-is-rejected).[](#if-the-contract-is-approved)

![شرطي.](../media/content-understanding/condition.png)

## <a name="if-the-contract-is-approved"></a>إذا تمت الموافقة على العقد

عند الموافقة على عقد، تحدث الأمور التالية:

- على علامة **التبويب تعاقدات** ، ستتغير الحالة في بطاقة العقد إلى **تمت الموافقة**.

   ![تمت الموافقة على حالة البطاقة.](../media/content-understanding/approved-contracts-tab.png)

- في التدفق، يتم تغيير الحالة إلى **تمت الموافقة**.

   ![Flow الحالة المعتمدة.](../media/content-understanding/status-approved.png)

- في هذا الحل، تضاف بيانات العقد إلى علامة التبويب **مقابل** حتى يمكن إدارة الرواتب. يمكن تمديد هذه العملية للسماح للتدفق بإرسال العقود للدفع بواسطة تطبيق مالي من جهة خارجية (على سبيل المثال، Dynamics CRM).

   ![تم نقل العقد إلى الدفع.](../media/content-understanding/for-payout.png)

- في التدفق، يمكنك إنشاء العنصر التالي لنقل العقود المعتمدة إلى علامة التبويب **مقابل** مقابل مقابل.

   ![Flow للانتقال إلى الدفع.](../media/content-understanding/ready-for-payout.png)

    للحصول على تعبيرات المعلومات المطلوبة من بطاقة Teams، استخدم القيم المعروضة في الجدول التالي.
 
    |الاسم     |Expression |
    |---------|-----------|
    | حالة الموافقة  | body('Post_an_Adaptive_Card_to_a_Teams_channel_and_wait_for_a_response') ؟ ['submitActionId']         |
    | تمت الموافقة من قبل     | body('Post_an_Adaptive_Card_to_a_Teams_channel_and_wait_for_a_response') ؟ ['المستجيب'] ['displayName']        |
    | تاريخ الموافقة     | body('Post_an_Adaptive_Card_to_a_Teams_channel_and_wait_for_a_response') ؟ ['responseTime']         |
    | تعليق     | body('Post_an_Adaptive_Card_to_a_Teams_channel_and_wait_for_a_response') ؟ ['data']؟ ['acComments']         |
    
    يوضح المثال التالي كيفية استخدام مربع الصيغة في Power Automate لكتابة تعبير.

   ![لقطة شاشة Power Automate تعرض صيغة تعبير.](../media/content-understanding/expression-formula-power-automate.png)    

- يتم إنشاء بطاقة تكييفية تفيد بأنه تمت الموافقة على العقد ونقرها في قناة إدارة التعاقدات.

   ![تم نشر الموافقة على العقد.](../media/content-understanding/adaptive-card-approval.png)

   ![الموافقة على البطاقة التكييفية.](../media/content-understanding/adaptive-card.png)


   التعليمة البرمجية التالية هي JSON المستخدمة لهذه الخطوة في Power Automate.

```JSON
{ 
    "type": "AdaptiveCard",
    "body": [
        {
            "type": "Container",
            "style": "emphasis",
            "items": [
                {
                    "type": "ColumnSet",
                    "columns": [
                        {
                            "type": "Column",
                            "items": [
                                {
                                    "type": "TextBlock",
                                    "size": "Large",
                                    "weight": "Bolder",
                                    "text": "CONTRACT APPROVED"
                                }
                            ],
                            "width": "stretch"
                        }
                    ]
                }
            ],
            "bleed": true
        },
        {
            "type": "Container",
            "items": [
                {
                    "type": "FactSet",
                    "spacing": "Large",
                    "facts": [
                        {
                            "title": "Client",
                            "value": "@{triggerOutputs()?['body/Client']}"
                        },
                        {
                            "title": "Contractor",
                            "value": "@{triggerOutputs()?['body/Contractor']}"
                        },
                        {
                            "title": "Fee amount",
                            "value": "@{triggerOutputs()?['body/FeeAmount']}"
                        },
                        {
                            "title": "Approval by",
                            "value": "@{body('Post_an_Adaptive_Card_to_a_Teams_channel_and_wait_for_a_response')?['responder']['displayName']}"
                        },
                        {
                            "title": "Approved date",
                            "value": "@{body('Post_an_Adaptive_Card_to_a_Teams_channel_and_wait_for_a_response')?['responseTime']}"
                        },
                        {
                            "title": "Approval comment",
                            "value": "@{body('Post_an_Adaptive_Card_to_a_Teams_channel_and_wait_for_a_response')?['data']?['acComments']}"
                        },
                        {
                            "title": " ",
                            "value": " "
                        },
                        {
                            "title": "Status",
                            "value": "Ready for payout"
                        }
                    ]
                }
            ]
        }
    ],
    "$schema": "http://adaptivecards.io/schemas/adaptive-card.json",
    "version": "1.2",
    "fallbackText": "This card requires Adaptive Cards v1.2 support to be rendered properly."
}
```

## <a name="if-the-contract-is-rejected"></a>إذا تم رفض العقد

عند رفض العقد، تحدث الأمور التالية:

- على علامة **التبويب تعاقدات**، ستتغير الحالة في بطاقة العقد إلى **مرفوض.**

   ![تم رفض حالة البطاقة.](../media/content-understanding/rejected-contracts-tab.png)

- في التدفق، يمكنك سحب ملف العقد، وتغيير الحالة إلى مرفوض، ثم سحب الملف مرة أخرى.

   ![Flow رفض الحالة في ملف العقد.](../media/content-understanding/reject-flow.png)

- في التدفق، يمكنك إنشاء بطاقة تكييفية تفيد برفض العقد.

   ![Flow الحالة مرفوضة على بطاقة تكييفية.](../media/content-understanding/reject-flow-item.png)

التعليمة البرمجية التالية هي JSON المستخدمة لهذه الخطوة في Power Automate.

```JSON
{ 
    "type": "AdaptiveCard",
    "body": [
        {
            "type": "Container",
            "style": "attention",
            "items": [
                {
                    "type": "ColumnSet",
                    "columns": [
                        {
                            "type": "Column",
                            "items": [
                                {
                                    "type": "TextBlock",
                                    "size": "Large",
                                    "weight": "Bolder",
                                    "text": "CONTRACT REJECTED"
                                }
                            ],
                            "width": "stretch"
                        }
                    ]
                }
            ],
            "bleed": true
        },
        {
            "type": "Container",
            "items": [
                {
                    "type": "FactSet",
                    "spacing": "Large",
                    "facts": [
                        {
                            "title": "Client",
                            "value": "@{triggerOutputs()?['body/Client']}"
                        },
                        {
                            "title": "Contractor",
                            "value": "@{triggerOutputs()?['body/Contractor']}"
                        },
                        {
                            "title": "Fee amount",
                            "value": "@{triggerOutputs()?['body/FeeAmount']}"
                        },
                        {
                            "title": "Rejected by",
                            "value": "@{body('Post_an_Adaptive_Card_to_a_Teams_channel_and_wait_for_a_response')?['responder']['displayName']}"
                        },
                        {
                            "title": "Rejected date",
                            "value": "@{body('Post_an_Adaptive_Card_to_a_Teams_channel_and_wait_for_a_response')?['responseTime']}"
                        },
                        {
                            "title": "Comment",
                            "value": "@{body('Post_an_Adaptive_Card_to_a_Teams_channel_and_wait_for_a_response')?['data']?['acComments']}"
                        },
                        {
                            "title": " ",
                            "value": " "
                        },
                        {
                            "title": "Status",
                            "value": "Needs review"
                        }
                    ]
                }
            ]
        }
    ],
    "$schema": "http://adaptivecards.io/schemas/adaptive-card.json",
    "version": "1.2",
    "fallbackText": "This card requires Adaptive Cards v1.2 support to be rendered properly."
}
```

- يتم نشر البطاقة في قناة إدارة التعاقدات.

   ![Flow بطاقة تكييفية لرفضها.](../media/content-understanding/rejected.png)
