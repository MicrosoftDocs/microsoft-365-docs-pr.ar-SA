---
title: إنشاء قاعدة إعلامات التهيئة أو إيقاف التشغيل
description: احصل على إعلام عند استخدام برنامج نصي محلي للدخون أو إيقاف التشغيل.
keywords: الboarding، offboarding، محلي، برنامج نصي، إعلام، قاعدة
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
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 0208e21394e350c2b5ffffdca6f8e14ebba227c8
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/25/2022
ms.locfileid: "64476001"
---
# <a name="create-a-notification-rule-when-a-local-onboarding-or-offboarding-script-is-used"></a>إنشاء قاعدة إعلام عند استخدام برنامج نصي محلي للتهيئة أو إيقاف التشغيل

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**ينطبق على:**
- [Microsoft Defender لنقطة النهاية 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> هل تريد تجربة Microsoft Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]


أنشئ قاعدة إعلام بحيث يتم إعلامك عند استخدام برنامج نصي محلي لترك العمل أو إيقاف التشغيل.

## <a name="before-you-begin"></a>قبل البدء

ستحتاج إلى الوصول إلى:

- Power Automate (خطة لكل مستخدم كحد أدنى). لمزيد من المعلومات، [راجع Power Automate الأسعار](https://flow.microsoft.com/pricing/).
- جدول Azure أو SharePoint القائمة أو المكتبة / SQL DB.

## <a name="create-the-notification-flow"></a>إنشاء تدفق الإعلامات

1. في [flow.microsoft.com](https://flow.microsoft.com/).

2. انتقل إلى **تدفقاتي > جديد > مجدول - من فارغ**.

   :::image type="content" source="images/new-flow.png" alt-text="التدفق" lightbox="images/new-flow.png":::


3. إنشاء تدفق مجدول.
   1. أدخل اسم انسياب.
   2. حدد البدء والوقت.
   3. حدد التكرار. على سبيل المثال، كل 5 دقائق.

   :::image type="content" source="images/build-flow.png" alt-text="تدفق الإعلامات" lightbox="images/build-flow.png":::

4. حدد الزر + لإضافة إجراء جديد. سيكون الإجراء الجديد طلب HTTP لجهاز (أجهزة) مركز أمان Defender for Endpoint. يمكنك أيضا استبداله ب "موصل WDATP" (الإجراء: "الأجهزة - الحصول على قائمة الأجهزة").

   :::image type="content" source="images/recurrence-add.png" alt-text="التكرار وإضافة الإجراء" lightbox="images/recurrence-add.png":::

5. أدخل حقول HTTP التالية:

   - الأسلوب: "GET" كقيمة للحصول على قائمة الأجهزة.
   - URI: أدخل `https://api.securitycenter.microsoft.com/api/machines`.
   - المصادقة: حدد "Active Directory OAuth".
   - المستأجر: سجل الدخول https://portal.azure.com إلى **Azure Active Directory >** تسجيلات التطبيقات واحصل على قيمة "اسم المستأجر".
   - الجمهور: `https://securitycenter.onmicrosoft.com/windowsatpservice\`
   - "رقم العميل": https://portal.azure.com سجل الدخول وانتقل إلى **Azure Active Directory > تسجيلات** التطبيقات واحصل على قيمة "اسم العميل".
   - نوع بيانات الاعتماد: حدد "سري".
   - سري: سجل الدخول وانتقل https://portal.azure.com إلى **Azure Active Directory > تسجيلات** التطبيقات واحصل على قيمة "اسم المستأجر".

    :::image type="content" source="images/http-conditions.png" alt-text="شروط HTTP" lightbox="images/http-conditions.png":::

6. أضف خطوة جديدة عن طريق تحديد **إضافة إجراء جديد** ثم ابحث عن **عمليات** البيانات وحدد **Parse JSON**.

   :::image type="content" source="images/data-operations.png" alt-text="إدخال عمليات البيانات" lightbox="images/data-operations.png":::

7. إضافة "محتوى" في **الحقل "محتوى** ".

   :::image type="content" source="images/parse-json.png" alt-text="القسم parse JSON" lightbox="images/parse-json.png":::

8. حدد الارتباط **استخدام التحميل النموذجي لإنشاء** مخطط.

   :::image type="content" source="images/parse-json-schema.png" alt-text="تحليل JSON مع تحميل" lightbox="images/parse-json-schema.png":::

9. نسخ قصاصة JSON التالية ولصقها:

    ```json
    {
        "type": "object",
        "properties": {
            "@@odata.context": {
                "type": "string"
            },
            "value": {
                "type": "array",
                "items": {
                    "type": "object",
                    "properties": {
                        "id": {
                            "type": "string"
                        },
                        "computerDnsName": {
                            "type": "string"
                        },
                        "firstSeen": {
                            "type": "string"
                        },
                        "lastSeen": {
                            "type": "string"
                        },
                        "osPlatform": {
                            "type": "string"
                        },
                        "osVersion": {},
                        "lastIpAddress": {
                            "type": "string"
                        },
                        "lastExternalIpAddress": {
                            "type": "string"
                        },
                        "agentVersion": {
                            "type": "string"
                        },
                        "osBuild": {
                            "type": "integer"
                        },
                        "healthStatus": {
                            "type": "string"
                        },
                        "riskScore": {
                            "type": "string"
                        },
                        "exposureScore": {
                            "type": "string"
                        },
                        "aadDeviceId": {},
                        "machineTags": {
                            "type": "array"
                        }
                    },
                    "required": [
                        "id",
                        "computerDnsName",
                        "firstSeen",
                        "lastSeen",
                        "osPlatform",
                        "osVersion",
                        "lastIpAddress",
                        "lastExternalIpAddress",
                        "agentVersion",
                        "osBuild",
                        "healthStatus",
                        "rbacGroupId",
                        "rbacGroupName",
                        "riskScore",
                        "exposureScore",
                        "aadDeviceId",
                        "machineTags"
                    ]
                }
            }
        }
    }

    ```

10. قم باستخراج القيم من مكالمة JSON وتحقق مما إذا كان الجهاز (الأجهزة) التي تم تشغيلها مسجلا بالفعل في SharePoint على سبيل المثال:

    - إذا كانت الإجابة "نعم"، لن يتم تشغيل أي إعلام
    - إذا لم يكن الأمر لا، سيتم تسجيل الجهاز (الأجهزة) الجديدة التي تم تشغيلها في قائمة SharePoint، وسيرسل إعلام إلى مسؤول Defender for Endpoint

    :::image type="content" source="images/flow-apply.png" alt-text="تطبيق التدفق على كل عنصر" lightbox="images/flow-apply.png":::

    :::image type="content" source="images/apply-to-each.png" alt-text="تطبيق التدفق إلى عنصر &quot;الحصول على العناصر&quot;" lightbox="images/apply-to-each.png":::

11. ضمن **شرط**، أضف التعبير التالي: "length(body('Get_items')?[' value'])" وحدد الشرط ليساوي 0.

    :::image type="content" source="images/apply-to-each-value.png" alt-text="تطبيق التدفق على كل شرط" lightbox="images/apply-to-each-value.png":::
    :::image type="content" source="images/conditions-2.png" alt-text="الشرط-1" lightbox="images/conditions-2.png":::
    :::image type="content" source="images/condition3.png" alt-text="الشرط 2" lightbox="images/condition3.png":::
    :::image type="content" source="images/send-email.png" alt-text="القسم &quot;إرسال بريد إلكتروني&quot;" lightbox="images/send-email.png":::

## <a name="alert-notification"></a>إعلام التنبيه

الصورة التالية هي مثال على إعلام بالبريد الإلكتروني.

:::image type="content" source="images/alert-notification.png" alt-text="شاشة إعلام البريد الإلكتروني" lightbox="images/alert-notification.png":::

## <a name="tips"></a>تلميحات

- يمكنك التصفية هنا باستخدام LastSeen فقط:
  - كل 60 دقيقة:
    - خذ كل الأجهزة التي رأيتها آخر مرة في آخر 7 أيام.

- لكل جهاز:
  - إذا كانت خاصية آخر مرة رأيتها على الفاصل الزمني لمدة ساعة واحدة [-7 أيام، -7days + 60 دقيقة ] -> تنبيه لإمكانية إيقاف التشغيل.
  - إذا كانت المرة الأولى التي رأيتها على الساعة > تنبيه للتكهين.

في هذا الحل، لن يكون لديك تنبيهات مكررة: هناك مستأجرون لديهم أجهزة متعددة. قد يكون الحصول على كل هذه الأجهزة مكلفة جدا وقد يتطلب الترحيل.

يمكنك تقسيمه إلى استعلامين:

1. بالنسبة إلى إيقاف التشغيل، لا يستغرق سوى هذا الفاصل الزمني باستخدام $filter OData وإعلامك فقط إذا تم تحقيق الشروط.
2. خذ كل الأجهزة التي رأيتها آخر مرة في الساعة الماضية وتحقق من الخاصية التي تم تفحصها لأول مرة (إذا كانت الخاصية التي تم تفحصها للمرة الأولى في الساعة الماضية، فيجب أن تكون آخر مرة رأيتها هناك أيضا).
