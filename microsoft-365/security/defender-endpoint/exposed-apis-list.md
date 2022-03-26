---
title: واجهات برمجة تطبيقات نقطة النهاية المدعومة من Microsoft Defender
ms.reviewer: ''
description: تعرف على الكيانات المحددة المعتمدة في Microsoft Defender لنقطة النهاية حيث يمكنك إنشاء مكالمات API إلى.
keywords: apis، apis المعتمدة، الممثل، التنبيهات، الجهاز، المستخدم، المجال، ip، الملف، الاستعلامات المتقدمة، البحث المتقدم
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
ms.openlocfilehash: 94c5698845f556936373ee4548d9aa137f03867b
ms.sourcegitcommit: c11d4a2b9cb891ba22e16a96cb9d6389f6482459
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 12/03/2021
ms.locfileid: "63570669"
---
# <a name="supported-microsoft-defender-for-endpoint-apis"></a>واجهات برمجة تطبيقات نقطة النهاية المدعومة من Microsoft Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:** 
- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/?linkid=2154037)

> هل تريد تجربة Microsoft Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

## <a name="endpoint-uri-and-versioning"></a>نقطة النهاية URI والإصدار

### <a name="endpoint-uri"></a>نقطة النهاية URI

> إن URI الأساسي للخدمة هو: [https://api.securitycenter.microsoft.com](https://api.securitycenter.microsoft.com)
>
> لدى الاستعلامات المستندة إلى OData البادطة '/api'. على سبيل المثال، للحصول على التنبيهات، يمكنك إرسال طلب GET إلى [https://api.securitycenter.microsoft.com/api/alerts](https://api.securitycenter.microsoft.com/api/alerts)

### <a name="versioning"></a>الإصدار

> تدعم API الإصدار.
>
> الإصدار الحالي هو **V1.0**.
>
> لاستخدام إصدار معين، استخدم هذا التنسيق: `https://api.securitycenter.microsoft.com/api/{Version}`. على سبيل المثال: `https://api.securitycenter.microsoft.com/api/v1.0/alerts`
>
> إذا لم تحدد أي إصدار (على سبيل المثال)، `https://api.securitycenter.microsoft.com/api/alerts`ستصل إلى الإصدار الأخير.

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

تعرف على المزيد حول الوحدات المدعمة الفردية حيث يمكنك تشغيل مكالمات API إلى وتفاصيل مثل قيم طلب HTTP، وطلب رؤوس واستجابات متوقعة.

## <a name="in-this-section"></a>في هذا القسم

الموضوع | الوصف
:---|:---
[الصيد المتقدم](run-advanced-query-api.md) | تشغيل الاستعلامات من API.
[أساليب التنبيه وخصائصه](alerts.md) | قم بتشغيل مكالمات API مثل \- الحصول على تنبيهات وإنشاء تنبيه وتحديث التنبيه والمزيد.
[تصدير أساليب التقييم وخصائصه لكل جهاز](get-assessment-methods-properties.md) | تشغيل مكالمات API لجمع تقييمات الضعف على أساس كل جهاز، مثل: \- تقييم تكوين آمن للتصدير وتقييم مخزون البرامج وتقييم نقاط الضعف في برامج التصدير وتقييم نقاط الضعف في برنامج التصدير في دلتا.
[أساليب التحقيق التلقائي وخصائصه](investigation.md) | تشغيل مكالمات API مثل \- الحصول على مجموعة من "التحقيق".
[الحصول على تنبيهات ذات صلة بالمجال](get-domain-related-alerts.md) | تشغيل مكالمات API مثل \- الحصول على الأجهزة ذات الصلة بالمجال وإحصائيات المجال والمزيد.
[أساليب الملفات وخصائصها](files.md) | تشغيل مكالمات API مثل \- الحصول على معلومات الملف والتنبيهات ذات الصلة بالملفات والأجهزة ذات الصلة بالملفات وإحصائيات الملفات.
[أساليب المؤشرات وخصائصها](ti-indicator.md) | قم بتشغيل مكالمة API مثل \- الحصول على مؤشرات وإنشاء مؤشر وحذف مؤشرات.
[الحصول على تنبيهات ذات صلة ب IP](get-ip-related-alerts.md) | يمكنك تشغيل مكالمات API مثل \- الحصول على تنبيهات متعلقة ب IP والحصول على إحصائيات IP.
[أساليب الجهاز وخصائصه](machine.md) | قم بتشغيل مكالمات API مثل \- الحصول على الأجهزة والحصول على الأجهزة حسب الم ID ومعلومات حول المستخدمين الذين تم تسجيل دخولهم وتحرير العلامات والمزيد.
[أساليب إجراءات الجهاز وخصائصه](machineaction.md) | قم بتشغيل استدعاء API مثل \- عزل وتشغيل مسح ضوئي لمكافحة الفيروسات والمزيد.
[أساليب التوصيات وخصائصها](recommendation.md) | تشغيل مكالمات API مثل \- الحصول على توصية بواسطة الم ID.
[أساليب وخصائص نشاط الإصلاح](get-remediation-methods-properties.md) | تشغيل مكالمة API مثل \- الحصول على كل مهام المعالجة، والحصول على مهمة إصلاحية للأجهزة المعرضة والحصول على مهمة إصلاح واحدة بواسطة الم id.
[أساليب النقاط وخصائصها](score.md) | تشغيل مكالمات API مثل \- الحصول على درجة التعرض للضوء أو الحصول على نقاط آمنة للجهاز.
[أساليب البرنامج وخصائصه](software.md) | تشغيل مكالمات API مثل \- الثغرات في القائمة حسب البرنامج.
[أساليب المستخدم](user.md) | تشغيل مكالمات API مثل \- الحصول على تنبيهات متعلقة بالمستخدم والأجهزة ذات الصلة بالمستخدم.
[أساليب الثغرات وخصائصها](vulnerability.md) | تشغيل مكالمات API مثل \- أجهزة القائمة حسب الثغرة الأمنية.

## <a name="see-also"></a>راجع أيضًا

- [واجهات برمجة تطبيقات Microsoft Defender لنقطة النهاية](apis-intro.md)

- [ملاحظات إصدار API ل Microsoft Defender لنقطة النهاية](api-release-notes.md)
