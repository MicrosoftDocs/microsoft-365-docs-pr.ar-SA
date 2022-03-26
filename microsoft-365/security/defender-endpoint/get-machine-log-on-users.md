---
title: الحصول على API لمستخدمي تسجيل تسجيل الوصول إلى الجهاز
description: تعرف على كيفية استخدام API للحصول على مستخدمو تسجيل الدخول إلى الجهاز لاسترداد مجموعة من المستخدمين الذين سجلوا دخولهم على جهاز في Microsoft Defender لنقطة النهاية.
keywords: apis، api الخاصة بالرسم البياني، apis المعتمدة، الحصول، الجهاز، تسجيل الدخول، المستخدمون
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
ms.openlocfilehash: 1c8635e7037f72830584d09d229891822a2e1f52
ms.sourcegitcommit: 2716cb48cc6127f6b851d177af23f276fb07bfc9
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 12/13/2021
ms.locfileid: "63569827"
---
# <a name="get-machine-logon-users-api"></a>الحصول على API لمستخدمي تسجيل تسجيل الوصول إلى الجهاز

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**ينطبق على:** 
- [خطة Microsoft Defender لنقطة النهاية 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/?linkid=2154037)

> هل تريد تجربة Microsoft Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]


## <a name="api-description"></a>وصف API
استرداد مجموعة من المستخدمين الذين سجلوا دخولهم على جهاز معين.

## <a name="limitations"></a>القيود
1. يمكنك الاستعلام عن التنبيهات التي تم تحديثها آخر مرة وفقا لفترة الاستبقاء التي تم تكوينها.
2. قيود السعر ل API هذه هي 100 مكالمة في الدقيقة و1500 مكالمة في الساعة.

## <a name="permissions"></a>الأذونات

أحد الأذونات التالية مطلوبة لاستدعاء API هذه. لمعرفة المزيد، بما في ذلك كيفية اختيار الأذونات، راجع [استخدام Microsoft Defender ل واجهات برمجة تطبيقات نقطة النهاية](apis-intro.md)

نوع الإذن|الإذن|اسم عرض الأذونات
:---|:---|:---
Application |User.read.All |"قراءة ملفات تعريف المستخدمين"
مفوض (حساب العمل أو المدرسة) | User.read.All | "قراءة ملفات تعريف المستخدمين"

> [!NOTE]
> عند الحصول على رمز مميز باستخدام بيانات اعتماد المستخدم:
>
> - يجب أن يكون لدى المستخدم إذن الدور التالي على الأقل: "عرض البيانات". لمزيد من المعلومات، راجع [إنشاء أدوار وإدارتها](user-roles.md).
> - ستتضمن الاستجابة المستخدمين فقط إذا كان الجهاز مرئيا للمستخدم، استنادا إلى إعدادات مجموعة الأجهزة. لمزيد من المعلومات، راجع [إنشاء مجموعات الأجهزة وإدارتها](machine-groups.md).

## <a name="http-request"></a>طلب HTTP

```http
GET /api/machines/{id}/logonusers
```

## <a name="request-headers"></a>طلب رؤوس

الاسم|النوع|الوصف
:---|:---|:---
التخويل | سلسلة | حامل {token}. **مطلوب**.

## <a name="request-body"></a>طلب الحصول على "هيئة"

فارغ

## <a name="response"></a>الاستجابة

إذا نجح الجهاز وكان موجودا - 200 موافق [مع قائمة كيانات](user.md) المستخدمين في الجسم. إذا لم يتم العثور على الجهاز - 404 لم يتم العثور عليه.

## <a name="example"></a>مثال

### <a name="request"></a>طلب

فيما يلي مثال على الطلب.

```http
GET https://api.securitycenter.microsoft.com/api/machines/1e5bc9d7e413ddd7902c2932e418702b84d0cc07/logonusers
```

### <a name="response"></a>الاستجابة

فيما يلي مثال على الاستجابة.

```http
HTTP/1.1 200 OK
Content-type: application/json
{
    "@odata.context": "https://api.securitycenter.microsoft.com/api/$metadata#Users",
    "value": [
        {
            "id": "contoso\\user1",
            "accountName": "user1",
            "accountDomain": "contoso",
            "firstSeen": "2019-12-18T08:02:54Z",
            "lastSeen": "2020-01-06T08:01:48Z",
            "logonTypes": "Interactive",
            "isDomainAdmin": true,
            "isOnlyNetworkUser": false
        },
        ...
    ]
}
```
