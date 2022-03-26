---
title: الحصول على معلومات IPs ذات الصلة بالتنبيه
description: يمكنك استرداد كل برامج IPs ذات الصلة بتنبيه معين باستخدام Microsoft Defender لنقطة النهاية.
keywords: apis، api الخاصة بالرسم البياني، apis المعتمدة، الحصول على معلومات التنبيه، معلومات التنبيه، ip ذي الصلة
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
ms.openlocfilehash: c2268658223ff0bce0e879e23ea4a5c1ce843aaf
ms.sourcegitcommit: 0ee2dabe402d44fecb6856af98a2ef7720d25189
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 12/09/2021
ms.locfileid: "63572352"
---
# <a name="get-alert-related-ips-information-api"></a>الحصول على API معلومات IPs ذات الصلة بالتنبيه

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**
- [خطة Microsoft Defender لنقطة النهاية 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> هل تريد تجربة Microsoft Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)


[!Include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!Include[Improve request performance](../../includes/improve-request-performance.md)]

## <a name="api-description"></a>وصف API

استرداد كل برامج IPs ذات الصلة بتنبيه معين.

## <a name="limitations"></a>القيود

1. يمكنك الاستعلام عن التنبيهات التي تم تحديثها آخر مرة وفقا لفترة الاستبقاء التي تم تكوينها.
2. قيود السعر ل API هذه هي 100 مكالمة في الدقيقة و1500 مكالمة في الساعة.

## <a name="permissions"></a>الأذونات

أحد الأذونات التالية مطلوبة لاستدعاء API هذه. لمعرفة المزيد، بما في ذلك كيفية اختيار الأذونات، راجع [استخدام Microsoft Defender ل واجهات برمجة تطبيقات نقطة النهاية](apis-intro.md)

نوع الإذن|الإذن|اسم عرض الأذونات
:---|:---|:---
Application|Ip.read.All|"قراءة ملفات تعريف عناوين IP"
مفوض (حساب العمل أو المدرسة)|Ip.read.All|"قراءة ملفات تعريف عناوين IP"

> [!NOTE]
> عند الحصول على رمز مميز باستخدام بيانات اعتماد المستخدم:
>
> - يجب أن يكون لدى المستخدم إذن الدور التالي على الأقل: "عرض البيانات" (لمزيد من المعلومات، راجع [إنشاء أدوار وإدارتها](user-roles.md)
> - يحتاج المستخدم إلى الوصول إلى الجهاز المقترن بالتنبيه، استنادا إلى إعدادات مجموعة الأجهزة (لمزيد من المعلومات، راجع إنشاء [مجموعات الأجهزة وإدارتها](machine-groups.md)

## <a name="http-request"></a>طلب HTTP

```http
GET /api/alerts/{id}/ips
```

## <a name="request-headers"></a>طلب رؤوس

الاسم|النوع|الوصف
:---|:---|:---
التخويل|سلسلة|حامل {token}. **مطلوب**.

## <a name="request-body"></a>طلب الحصول على "هيئة"

فارغ

## <a name="response"></a>الاستجابة

إذا نجح وتنبيه وكان عنوان IP موجودا - 200 موافق. إذا لم يتم العثور على التنبيه - 404 لم يتم العثور عليه.

## <a name="example"></a>مثال

### <a name="request-example"></a>مثال على طلب

فيما يلي مثال على الطلب.

```http
GET https://api.securitycenter.microsoft.com/alerts/636688558380765161_2136280442/ips
```

### <a name="response-example"></a>مثال على الاستجابة

فيما يلي مثال على الاستجابة.

```json
{
    "@odata.context": "https://api.securitycenter.microsoft.com/$metadata#Ips",
    "value": [
                {
                    "id": "104.80.104.128"
                },
                {
                    "id": "23.203.232.228
                }
                ...
    ]
}
```
