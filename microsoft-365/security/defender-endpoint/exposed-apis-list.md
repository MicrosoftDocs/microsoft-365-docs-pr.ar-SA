---
title: واجهات Microsoft Defender لنقطة النهاية برمجة التطبيقات المعتمدة
ms.reviewer: ''
description: تعرف على كيانات Microsoft Defender لنقطة النهاية المدعومة المحددة حيث يمكنك إنشاء استدعاءات واجهة برمجة التطبيقات إليها.
keywords: واجهة برمجة التطبيقات، وواجهة برمجة التطبيقات المدعومة، والممثل، والتنبيهات، والجهاز، والمستخدم، والمجال، وip، والملف، والاستعلامات المتقدمة، والتتبع المتقدم
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
ms.openlocfilehash: fe43d4df71b0801ae89149797068873577c77c38
ms.sourcegitcommit: f30616b90b382409f53a056b7a6c8be078e6866f
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 05/03/2022
ms.locfileid: "65174687"
---
# <a name="supported-microsoft-defender-for-endpoint-apis"></a>واجهات Microsoft Defender لنقطة النهاية برمجة التطبيقات المعتمدة

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:** 
- [Defender for Endpoint الخطة 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender for Business](../defender-business/index.yml)

> [!IMPORTANT]
> لا يتم تضمين قدرات التتبع المتقدمة في Defender for Business. راجع [مقارنة Microsoft Defender for Business بالخطط Microsoft Defender لنقطة النهاية 1 و2](../defender-business/compare-mdb-m365-plans.md#compare-microsoft-defender-for-business-to-microsoft-defender-for-endpoint-plans-1-and-2).


> هل تريد تجربة Microsoft Defender لنقطة النهاية؟ [التسجيل للحصول على إصدار تجريبي مجاني.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

## <a name="endpoint-uri-and-versioning"></a>نقطة النهاية URI وتعيين الإصدار

### <a name="endpoint-uri"></a>URI لنقطة النهاية

> URI الأساسي للخدمة هو: [https://api.securitycenter.microsoft.com](https://api.securitycenter.microsoft.com)
>
> تحتوي OData المستندة إلى الاستعلامات على بادئة '/api'. على سبيل المثال، للحصول على التنبيهات، يمكنك إرسال طلب GET إلى [https://api.securitycenter.microsoft.com/api/alerts](https://api.securitycenter.microsoft.com/api/alerts)

### <a name="versioning"></a>الاصدارات

> تدعم واجهة برمجة التطبيقات تعيين الإصدار.
>
> الإصدار الحالي هو **V1.0**.
>
> لاستخدام إصدار معين، استخدم هذا التنسيق: `https://api.securitycenter.microsoft.com/api/{Version}`. على سبيل المثال: `https://api.securitycenter.microsoft.com/api/v1.0/alerts`
>
> إذا لم تحدد أي إصدار (على سبيل المثال `https://api.securitycenter.microsoft.com/api/alerts`) فستصل إلى الإصدار الأخير.

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

تعرف على المزيد حول الكيانات الفردية المدعومة حيث يمكنك تشغيل استدعاءات واجهة برمجة التطبيقات وتفاصيل مثل قيم طلب HTTP ورؤوس الطلبات والاستجابات المتوقعة.

## <a name="in-this-section"></a>في هذا القسم

الموضوع | الوصف
:---|:---
[الصيد المتقدم](run-advanced-query-api.md) | تشغيل الاستعلامات من واجهة برمجة التطبيقات.<p>*لا يتم تضمين قدرات التتبع المتقدمة في [Defender for Business](../defender-business/mdb-overview.md)*.
[أساليب التنبيه وخصائصه](alerts.md) | تشغيل استدعاءات واجهة برمجة التطبيقات مثل \- الحصول على التنبيهات وإنشاء تنبيه وتحديث التنبيه والمزيد.
[تصدير أساليب التقييم وخصائصه لكل جهاز](get-assessment-methods-properties.md) | تشغيل استدعاءات واجهة برمجة التطبيقات لجمع تقييمات الثغرات الأمنية على أساس كل جهاز، مثل: \- تصدير تقييم التكوين الآمن، وتصدير تقييم مخزون البرامج، وتصدير تقييم الثغرات الأمنية للبرامج، وتقييم الثغرات الأمنية في برامج تصدير دلتا.
[أساليب التحقيق التلقائي وخصائصه](investigation.md) | تشغيل استدعاءات واجهة برمجة التطبيقات مثل \- الحصول على مجموعة من التحقيق.
[الحصول على تنبيهات ذات صلة بالمجال](get-domain-related-alerts.md) | تشغيل استدعاءات واجهة برمجة التطبيقات مثل \- الحصول على الأجهزة ذات الصلة بالمجال وإحصائيات المجال والمزيد.
[أساليب الملفات وخصائصها](files.md) | تشغيل استدعاءات واجهة برمجة التطبيقات مثل \- الحصول على معلومات الملف والتنبيهات ذات الصلة بالملفات والأجهزة ذات الصلة بالملفات وإحصائيات الملفات.
[أساليب المؤشرات وخصائصها](ti-indicator.md) | تشغيل استدعاء واجهة برمجة التطبيقات مثل \- الحصول على مؤشرات وإنشاء مؤشر وحذف المؤشرات.
[الحصول على تنبيهات ذات صلة ب IP](get-ip-related-alerts.md) | تشغيل استدعاءات واجهة برمجة التطبيقات مثل \- الحصول على التنبيهات المتعلقة ب IP والحصول على إحصائيات IP.
[أساليب الجهاز وخصائصه](machine.md) | قم بتشغيل استدعاءات واجهة برمجة التطبيقات مثل \- الحصول على الأجهزة والحصول على الأجهزة حسب المعرف ومعلومات حول المستخدمين الذين تم تسجيل دخولهم وتحرير العلامات والمزيد.
[أساليب إجراءات الجهاز وخصائصه](machineaction.md) | تشغيل استدعاء واجهة برمجة التطبيقات مثل \- العزل، وتشغيل فحص مكافحة الفيروسات والمزيد.
[أساليب التوصيات وخصائصها](recommendation.md) | تشغيل استدعاءات واجهة برمجة التطبيقات مثل \- الحصول على توصية بواسطة المعرف.
[أساليب وخصائص نشاط الإصلاح](get-remediation-methods-properties.md) | تشغيل استدعاء واجهة برمجة التطبيقات مثل \- الحصول على جميع مهام المعالجة والحصول على مهمة معالجة الأجهزة المكشوفة والحصول على مهمة معالجة واحدة حسب المعرف.
[أساليب النقاط وخصائصها](score.md) | تشغيل استدعاءات واجهة برمجة التطبيقات مثل \- الحصول على درجة التعرض أو الحصول على درجة أمان الجهاز.
[أساليب البرنامج وخصائصه](software.md) | تشغيل استدعاءات واجهة برمجة التطبيقات مثل \- الثغرات الأمنية في القائمة حسب البرنامج.
[أساليب المستخدم](user.md) | تشغيل استدعاءات واجهة برمجة التطبيقات مثل \- الحصول على التنبيهات المتعلقة بالمستخدم والأجهزة المتعلقة بالمستخدم.
[أساليب الثغرات وخصائصها](vulnerability.md) | تشغيل استدعاءات واجهة برمجة التطبيقات مثل \- أجهزة القائمة حسب الثغرات الأمنية.

## <a name="see-also"></a>راجع أيضًا

- [واجهات برمجة التطبيقات Microsoft Defender لنقطة النهاية](apis-intro.md)

- [ملاحظات إصدار واجهة برمجة تطبيقات Microsoft Defender لنقطة النهاية](api-release-notes.md)
