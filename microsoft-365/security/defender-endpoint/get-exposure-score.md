---
title: الحصول على نقاط التعرض للضوء
description: استرداد درجة التعرض في المؤسسة.
keywords: apis، api الخاصة بالرسم البياني، apis المعتمدة، الحصول، درجة التعرض للضوء، درجة التعرض في المؤسسة
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
author: dansimp
ms.author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
MS.technology: mde
ms.custom: api
ms.openlocfilehash: 478f109d1f519e8d931716ce90bdcc979fed4b33
ms.sourcegitcommit: 348f3998a029a876a9dcc031f808e9e350804f22
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 12/03/2021
ms.locfileid: "63570509"
---
# <a name="get-exposure-score"></a>الحصول على نقاط التعرض للضوء

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**
- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> هل تريد تجربة Microsoft Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

[!include[Prerelease information](../../includes/prerelease.md)]

استرداد درجة التعرض في المؤسسة.

## <a name="permissions"></a>الأذونات

أحد الأذونات التالية مطلوبة لاستدعاء API هذه. لمعرفة المزيد، بما في ذلك كيفية اختيار الأذونات، راجع [استخدام Microsoft Defender ل واجهات برمجة تطبيقات نقطة النهاية](apis-intro.md)

نوع الإذن|الإذن|اسم عرض الأذونات
---|---|---
Application|Score.Read.All|"قراءة نقاط إدارة المخاطر والضعف"
مفوض (حساب العمل أو المدرسة)|Score.Read|"قراءة نقاط إدارة المخاطر والضعف"

## <a name="http-request"></a>طلب HTTP

```http
GET /api/exposureScore
```

## <a name="request-headers"></a>طلب رؤوس

الاسم|النوع|الوصف
---|---|---
التخويل|سلسلة|حامل {token}. **مطلوب**.

## <a name="request-body"></a>طلب الحصول على "هيئة"

فارغ

## <a name="response"></a>الاستجابة

إذا نجح، ترجع هذه الطريقة 200 موافق، مع بيانات التعرض للضوء في هيئة الاستجابة.

## <a name="example"></a>مثال

### <a name="request"></a>طلب

فيما يلي مثال على الطلب.

```http
GET https://api.securitycenter.microsoft.com/api/exposureScore
```

### <a name="response"></a>الاستجابة

فيما يلي مثال على الاستجابة.

> [!NOTE]
> قد يتم اقتطاع قائمة الاستجابة المعروضة هنا للإيجاز.

```json
{
    "@odata.context": "https://api.securitycenter.microsoft.com/api/$metadata#ExposureScore/$entity",
    "time": "2019-12-03T07:23:53.280499Z",
    "score": 33.491554051195706
}
```

## <a name="see-also"></a>راجع أيضًا

- [إدارة المخاطر المستندة إلى & المخاطر](/microsoft-365/security/defender-endpoint/next-gen-threat-and-vuln-mgt)
- [درجة & التعرض للمخاطر](/microsoft-365/security/defender-endpoint/tvm-exposure-score)
