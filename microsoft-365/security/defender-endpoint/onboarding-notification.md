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
ms.openlocfilehash: 36713496b5885866dd21a3402dcfe66b4af5b76e
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 11/24/2021
ms.locfileid: "63572242"
---
# <a name="create-a-notification-rule-when-a-local-onboarding-or-offboarding-script-is-used"></a>إنشاء قاعدة إعلام عند استخدام برنامج نصي محلي للتهيئة أو إيقاف التشغيل

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**ينطبق على:**
- [خطة Microsoft Defender لنقطة النهاية 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
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

    ![صورة للتدفق.](images/new-flow.png)

3. إنشاء تدفق مجدول.
   1. أدخل اسم انسياب.
   2. حدد البدء والوقت.
   3. حدد التكرار. على سبيل المثال، كل 5 دقائق.

    ![صورة لتدفق الإعلامات.](images/build-flow.png)

4. حدد الزر + لإضافة إجراء جديد. سيكون الإجراء الجديد طلب HTTP لجهاز (أجهزة) مركز أمان Defender for Endpoint. يمكنك أيضا استبداله ب "موصل WDATP" (الإجراء: "الأجهزة - الحصول على قائمة الأجهزة").

    ![صورة التكرار وإضافة إجراء.](images/recurrence-add.png)

5. أدخل حقول HTTP التالية:

   - الأسلوب: "GET" كقيمة للحصول على قائمة الأجهزة.
   - URI: أدخل `https://api.securitycenter.microsoft.com/api/machines`.
   - المصادقة: حدد "Active Directory OAuth".
   - المستأجر: سجل الدخول https://portal.azure.com إلى **Azure Active Directory >** تسجيلات التطبيقات واحصل على قيمة "اسم المستأجر".
   - الجمهور: `https://securitycenter.onmicrosoft.com/windowsatpservice\`
   - "رقم العميل": https://portal.azure.com سجل الدخول وانتقل إلى **Azure Active Directory > تسجيلات** التطبيقات واحصل على قيمة "اسم العميل".
   - نوع بيانات الاعتماد: حدد "سري".
   - سري: سجل الدخول وانتقل https://portal.azure.com إلى **Azure Active Directory > تسجيلات** التطبيقات واحصل على قيمة "اسم المستأجر".

    ![صورة لشروط HTTP.](images/http-conditions.png)

6. أضف خطوة جديدة عن طريق تحديد **إضافة إجراء جديد** ثم ابحث عن **عمليات** البيانات وحدد **Parse JSON**.

    ![صورة لعمليات البيانات.](images/data-operations.png)

7. إضافة "محتوى" في **الحقل "محتوى** ".

    ![صورة ل parse JSON.](images/parse-json.png)

8. حدد الارتباط **استخدام التحميل النموذجي لإنشاء** مخطط.

    ![صورة ل parse json مع تحميل.](images/parse-json-schema.png)

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

    ![صورة تنطبق على كل منها.](images/flow-apply.png)

    ![صورة لتطبيق على كل مع الحصول على العناصر.](images/apply-to-each.png)

11. ضمن **شرط**، أضف التعبير التالي: "length(body('Get_items')?[' value'])" وحدد الشرط ليساوي 0.

    ![صورة تنطبق على كل شرط.](images/apply-to-each-value.png)
    ![ صورة الشرط1.](images/conditions-2.png)
    ![ صورة الشرط 2.](images/condition3.png)
    ![ صورة إرسال بريد إلكتروني.](images/send-email.png)

## <a name="alert-notification"></a>إعلام التنبيه

الصورة التالية هي مثال على إعلام بالبريد الإلكتروني.

![صورة إعلام بالبريد الإلكتروني.](images/alert-notification.png)

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
