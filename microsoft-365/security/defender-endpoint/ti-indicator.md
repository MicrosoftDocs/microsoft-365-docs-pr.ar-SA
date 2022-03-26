---
title: نوع مورد المؤشر
description: حدد تفاصيل الكيان وحدد انتهاء صلاحية المؤشر باستخدام Microsoft Defender لنقطة النهاية.
keywords: apis، apis المعتمدة، get، TiIndicator، المؤشر، الأخيرة
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
ms.openlocfilehash: 8e8660574f65d614bacfe705d7fad19e39d501a6
ms.sourcegitcommit: c11d4a2b9cb891ba22e16a96cb9d6389f6482459
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 12/03/2021
ms.locfileid: "63572346"
---
# <a name="indicator-resource-type"></a>نوع مورد المؤشر

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**

- [خطة Microsoft Defender لنقطة النهاية 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> هل تريد تجربة Microsoft Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

- راجع صفحة [المؤشرات المقابلة](https://securitycenter.windows.com/preferences2/custom_ti_indicators/files) في المدخل.

الأسلوب|نوع الإرجاع|الوصف
:---|:---|:---
[مؤشرات القائمة](get-ti-indicators-collection.md)|[المؤشر](ti-indicator.md) المجموعة|[كيانات مؤشر](ti-indicator.md) القائمة.
[مؤشر إرسال](post-ti-indicator.md)|[المؤشر](ti-indicator.md)|إرسال كيان [المؤشر أو تحديثه](ti-indicator.md) .
[مؤشرات الاستيراد](import-ti-indicators.md)|[المؤشر](ti-indicator.md) المجموعة|إرسال [كيانات المؤشرات أو](ti-indicator.md) تحديثها.
[مؤشر الحذف](delete-ti-indicator-by-id.md)|بلا محتوى|حذف كيان [المؤشر](ti-indicator.md) .

## <a name="properties"></a>الخصائص

الخاصية|النوع|الوصف
:---|:---|:---
الم id|سلسلة|هوية كيان [المؤشر](ti-indicator.md) .
indicatorValue|سلسلة|قيمة [المؤشر](ti-indicator.md).
indicatorType|تعداد|نوع المؤشر. القيم المحتملة هي: "FileSha1" و"FileSha256" و"FileMd5" و"CertificateThumbprint" و"IpAddress" و"DomainName" و"Url".
تطبيق|سلسلة|التطبيق المقترن بالمؤشر.
إجراء|تعداد|الإجراء الذي سيتم اتخاذه إذا تم اكتشاف المؤشر في المؤسسة. القيم المحتملة هي: "التحذير" و"الحظر" و"التدقيق" و"التنبيه" و"AlertAndBlock" و"BlockAndRemediate" و"مسموح به".
|externalID|سلسلة|المعرف الذي يمكن للعميل إرساله في طلب الارتباط المخصص.|
sourceType|تعداد|"المستخدم" في حال تم إنشاء المؤشر بواسطة مستخدم (على سبيل المثال، من المدخل)، "AadApp" في حالة إرساله باستخدام تطبيق تلقائي عبر واجهة برمجة التطبيقات.
createdBySource|سلسلة|اسم المستخدم/التطبيق الذي قام بتقديم المؤشر.
createdBy|سلسلة|الهوية الفريدة للمستخدم/التطبيق الذي قام بتقديم المؤشر.
lastUpdatedBy|سلسلة|هوية المستخدم/التطبيق الذي قام بتحديث المؤشر آخر مرة.
creationTimeDateTimeUtc|DateTimeOffset|التاريخ والوقت الذي تم فيه إنشاء المؤشر.
expirationTime|DateTimeOffset|وقت انتهاء صلاحية المؤشر.
lastUpdateTime|DateTimeOffset|آخر مرة تم فيها تحديث المؤشر.
الخطورة|تعداد|خطورة المؤشر. القيم المحتملة هي: "معلوماتي" و"منخفض" و"متوسط" و"عال".
العنوان|سلسلة|عنوان المؤشر.
الوصف|سلسلة|وصف المؤشر.
recommendedActions|سلسلة|الإجراءات المستحسنة للمؤشر.
rbacGroupNames|قائمة السلاسل|أسماء أجهزة RBAC التي يتم عرض المؤشر فيها ونشطها. قائمة فارغة في حال تعرضها لجميع الأجهزة.
rbacGroupIds|قائمة السلاسل|RBAC's device ID's where the indicator is exposed and active. قائمة فارغة في حال تعرضها لجميع الأجهزة.
إنشاءAlert|تعداد|**True** إذا كان إنشاء التنبيه مطلوبا، **خطأ** إذا لم يكن من المفترض أن يقوم هذا المؤشر بإنشاء تنبيه.

## <a name="indicator-types"></a>أنواع المؤشرات

أنواع إجراءات المؤشرات المعتمدة بواسطة API هي:

- مسموح به
- التدقيق
- حظر
- BlockAndRemediate
- التحذير (Defender for Cloud Apps فقط)

لمزيد من المعلومات حول وصف أنواع إجراءات الاستجابة، راجع [إنشاء مؤشرات](manage-indicators.md).

> [!Note]
>
> سيتم دعم إجراءات الاستجابة السابقة (AlertAndBlock و Alert) حتى يناير 2022. بعد هذا التاريخ، يجب أن يستخدم جميع العملاء أحد أنواع الإجراءات المذكورة أعلاه.

## <a name="json-representation"></a>تمثيل Json

```json
{
    "id": "994",
    "indicatorValue": "881c0f10c75e64ec39d257a131fcd531f47dd2cff2070ae94baa347d375126fd",
    "indicatorType": "FileSha256",
    "action": "AlertAndBlock",
    "application": null,
    "source": "user@contoso.onmicrosoft.com",
    "sourceType": "User",
    "createdBy": "user@contoso.onmicrosoft.com",
    "severity": "Informational",
    "title": "Michael test",
    "description": "test",
    "recommendedActions": "nothing",
    "creationTimeDateTimeUtc": "2019-12-19T09:09:46.9139216Z",
    "expirationTime": null,
    "lastUpdateTime": "2019-12-19T09:09:47.3358111Z",
    "lastUpdatedBy": null,
    "rbacGroupNames": ["team1"]
}
```
