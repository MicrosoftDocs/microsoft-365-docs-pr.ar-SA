---
title: الحصول على API إحصائيات IP
description: احصل على أحدث الإحصائيات ل IP باستخدام Microsoft Defender لنقطة النهاية.
keywords: apis، api للرسم البياني، apis المعتمدة، الحصول، ip، الإحصائيات، انتشار
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
ms.openlocfilehash: a98b78e85956d49c3b7d7e389882e017dcede3a4
ms.sourcegitcommit: c11d4a2b9cb891ba22e16a96cb9d6389f6482459
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 12/03/2021
ms.locfileid: "63575833"
---
# <a name="get-ip-statistics-api"></a>الحصول على API إحصائيات IP

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**
- [خطة Microsoft Defender لنقطة النهاية 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> هل تريد تجربة Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

## <a name="api-description"></a>وصف API
استرداد إحصائيات IP المعطى.

## <a name="limitations"></a>القيود
1. قيود السعر ل API هذه هي 100 مكالمة في الدقيقة و1500 مكالمة في الساعة.
2. القيمة القصوى ل Lookbackhours هي 720 ساعة (30 يوما).

## <a name="permissions"></a>الأذونات

أحد الأذونات التالية مطلوبة لاستدعاء API هذه. لمعرفة المزيد، بما في ذلك كيفية اختيار الأذونات، راجع [استخدام Microsoft Defender ل واجهات برمجة تطبيقات نقطة النهاية](apis-intro.md)

نوع الإذن|الإذن|اسم عرض الأذونات
:---|:---|:---
Application|Ip.read.All|"قراءة ملفات تعريف عناوين IP"
مفوض (حساب العمل أو المدرسة)|Ip.read.All|"قراءة ملفات تعريف عناوين IP"

> [!NOTE]
> عند الحصول على رمز مميز باستخدام بيانات اعتماد المستخدم:
> - يجب أن يكون لدى المستخدم إذن الدور التالي على الأقل: "عرض البيانات" (راجع [إنشاء أدوار وإدارتها](user-roles.md) للحصول على مزيد من المعلومات)

## <a name="http-request"></a>طلب HTTP

```http
GET /api/ips/{ip}/stats
```

## <a name="request-headers"></a>طلب رؤوس

الاسم|النوع|الوصف
:---|:---|:---
التخويل|سلسلة|حامل {token}. **مطلوب**.

## <a name="request-uri-parameters"></a>طلب معلمات URI

الاسم|النوع|الوصف
:---|:---|:---
lookBackHours|Int32|يعرف الساعات التي نبحث فيها مرة أخرى للحصول على الإحصائيات. افتراضيا إلى 30 يوما. **اختياري**.

## <a name="request-body"></a>طلب الحصول على "هيئة"

فارغ

## <a name="response"></a>الاستجابة

إذا نجح و ip كان موجودا - 200 موافق مع البيانات الإحصائية في الجسم. IP صالح ولكن غير موجود - organizationPrevalence 0، IP غير صالح - HTTP 400.

## <a name="example"></a>مثال

### <a name="request-example"></a>مثال على طلب

فيما يلي مثال على الطلب.

```http
GET https://api.securitycenter.microsoft.com/api/ips/10.209.67.177/stats?lookBackHours=48
```

### <a name="response-example"></a>مثال على الاستجابة

فيما يلي مثال على الاستجابة.

```json
{
    "@odata.context": "https://api.securitycenter.microsoft.com/api/$metadata#microsoft.windowsDefenderATP.api.InOrgIPStats",
    "ipAddress": "10.209.67.177",
    "organizationPrevalence": 63515,
    "orgFirstSeen": "2017-07-30T13:36:06Z",
    "orgLastSeen": "2017-08-29T13:32:59Z"
}
```

|الاسم|الوصف|
|---|---|
|مؤسسة|العدد المتميز للأجهزة التي فتحت اتصال الشبكة ب IP هذا.|
|المؤسسة التي رأيتها للمرة الأولى|الاتصال الأول ل IP هذا في المؤسسة.|
|آخر مرة رأيت فيها المؤسسة|الاتصال الأخير ل IP هذا في المؤسسة.|

> [!NOTE]
> تستند معلومات الإحصائية هذه إلى بيانات من الأيام الثلاثين الماضية.
