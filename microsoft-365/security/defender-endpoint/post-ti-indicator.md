---
title: API مؤشر إرسال أو تحديث
description: تعرف على كيفية استخدام API لمؤشر إرسال أو تحديث لإرسال كيان مؤشر جديد أو تحديثه في Microsoft Defender لنقطة النهاية.
keywords: apis، api للرسم البياني، apis المعتمدة، إرسال، ti، مؤشر، تحديث
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
ms.openlocfilehash: a3fc1a0ce2f7d02ad8ed6804b99621f78fb859d3
ms.sourcegitcommit: 986ea76ecaceb5fe6b9616e553003e3c5b0df2e7
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 01/25/2022
ms.locfileid: "63570616"
---
# <a name="submit-or-update-indicator-api"></a>API مؤشر إرسال أو تحديث

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**
- [خطة Microsoft Defender لنقطة النهاية 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> هل تريد تجربة Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)


[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

## <a name="api-description"></a>وصف API

إرسال كيان مؤشر جديد أو [تحديثه](ti-indicator.md) .

لا يتم دعم "CIDR" ل IPs.

## <a name="limitations"></a>القيود

1. قيود السعر ل API هذه هي 100 مكالمة في الدقيقة و1500 مكالمة في الساعة.
2. يوجد حد أقصى 15000 مؤشر نشط لكل مستأجر.

## <a name="permissions"></a>الأذونات

أحد الأذونات التالية مطلوبة لاستدعاء API هذه. لمعرفة المزيد، بما في ذلك كيفية اختيار الأذونات، راجع [بدء العمل](apis-intro.md)

نوع الإذن|الإذن|اسم عرض الأذونات
:---|:---|:---
Application|Ti.ReadWrite|"مؤشرات القراءة والكتابة"
Application|Ti.ReadWrite.All|"قراءة كل المؤشرات وكتابتها"
مفوض (حساب العمل أو المدرسة)|Ti.ReadWrite|"مؤشرات القراءة والكتابة"

## <a name="http-request"></a>طلب HTTP

```http
POST https://api.securitycenter.microsoft.com/api/indicators
```

## <a name="request-headers"></a>طلب رؤوس

الاسم|النوع|الوصف
:---|:---|:---
التخويل|سلسلة|حامل {token}. **مطلوب**.
نوع المحتوى|سلسلة|application/json. **مطلوب**.

## <a name="request-body"></a>طلب الحصول على "هيئة"

في هيئة الطلب، زود كائن JSON بالمعلمات التالية:

المعلمة|النوع|الوصف
:---|:---|:---
indicatorValue|سلسلة|هوية كيان [المؤشر](ti-indicator.md) . **مطلوب**
indicatorType|تعداد|نوع المؤشر. القيم المحتملة هي: "FileSha1" و"FileMd5" و"CertificateThumbprint" و"FileSha256" و"IpAddress" و"DomainName" و"Url". **مطلوب**
إجراء|تعداد|الإجراء الذي سيتم اتخاذه إذا تم اكتشاف المؤشر في المؤسسة. القيم المحتملة هي: "تنبيه" و"تحذير" و"حظر" و"تدقيق و"BlockAndRemediate" و"AlertAndBlock" و"مسموح به". **مطلوب**. يجب تعيين المعلمة "GenerateAlert" إلى "TRUE" عند إنشاء إجراء باستخدام "تدقيق".
تطبيق|سلسلة|التطبيق المقترن بالمؤشر. يعمل هذا الحقل فقط مع المؤشرات الجديدة. ولن يتم تحديث القيمة على مؤشر موجود. **اختياري**
العنوان|سلسلة|عنوان تنبيه المؤشر. **مطلوب**
الوصف|سلسلة|وصف المؤشر. **مطلوب**
expirationTime|DateTimeOffset|وقت انتهاء صلاحية المؤشر. **اختياري**
الخطورة|تعداد|خطورة المؤشر. القيم المحتملة هي: "معلوماتي" و"منخفض" و"متوسط" و"عال". **اختياري**
recommendedActions|سلسلة|تنبيه مؤشر TI الإجراءات الموصى بها. **اختياري**
rbacGroupNames|سلسلة|قائمة مفصولة بفصول فاصلة لأسماء مجموعة RBAC التي سيتم تطبيق المؤشر عليها. **اختياري**
إنشاءAlert|تعداد|**True** إذا كان إنشاء التنبيه مطلوبا، **خطأ** إذا لم يكن من المفترض أن يقوم هذا المؤشر بإنشاء تنبيه.
## <a name="response"></a>الاستجابة

- إذا نجح هذا الأسلوب، فيرجع 200 - رمز استجابة موافق و كيان المؤشر الذي تم إنشاؤه / [تحديثه](ti-indicator.md) في هيئة الاستجابة.
- إذا لم ينجح: يتم إرجاع هذا الأسلوب 400 - طلب غير جيد. عادة ما يشير الطلب غير الصحيح إلى وجود هيئة غير صحيحة.

## <a name="example"></a>مثال

### <a name="request"></a>طلب

فيما يلي مثال على الطلب.

```http
POST https://api.securitycenter.microsoft.com/api/indicators
```

```json
{
    "indicatorValue": "220e7d15b011d7fac48f2bd61114db1022197f7f",
    "indicatorType": "FileSha1",
    "title": "test",
    "application": "demo-test",
    "expirationTime": "2020-12-12T00:00:00Z",
    "action": "AlertAndBlock",
    "severity": "Informational",
    "description": "test",
    "recommendedActions": "nothing",
    "rbacGroupNames": ["group1", "group2"]
}
```

## <a name="related-topic"></a>موضوع ذو صلة

- [إدارة المؤشرات](manage-indicators.md)
