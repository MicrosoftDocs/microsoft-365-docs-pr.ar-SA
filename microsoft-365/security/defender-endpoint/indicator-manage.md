---
title: إدارة المؤشرات
ms.reviewer: ''
description: يمكنك إدارة المؤشرات الخاصة بقص الملفات أو عنوان IP أو عناوين URL أو المجالات التي تحدد الكشف عن الكيانات ومنعها واستبعادها.
keywords: استيراد، مؤشر، قائمة، ioc، csv، إدارة، مسموح به، حظر، حظر، نظيف، ضار، هاش ملف، عنوان ip، عناوين url، المجال
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
ms.openlocfilehash: 2f66106dd39b9cd1f590148addfdd2cae89748c6
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 01/12/2022
ms.locfileid: "63573382"
---
# <a name="manage-indicators"></a>إدارة المؤشرات

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**ينطبق على:**
- [خطة Microsoft Defender لنقطة النهاية 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)


> هل تريد تجربة Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://www.microsoft.com/WindowsForBusiness/windows-atp?ocid=docs-wdatp-automationexclusionlist-abovefoldlink)

1. في جزء التنقل **، حدد الإعدادات** \> **نقاط** \> **النهاية** (ضمن **القواعد**).

2. حدد علامة تبويب نوع الكيان الذي تريد إدارته.

3. قم بتحديث تفاصيل المؤشر وانقر فوق حفظ أو  انقر فوق الزر **حذف** إذا كنت تريد إزالة الكيان من القائمة.

## <a name="import-a-list-of-iocs"></a>استيراد قائمة ب IoCs

يمكنك أيضا اختيار تحميل ملف CSV يعرف سمات المؤشرات والتحرك الذي يجب اتخاذه وتفاصيل أخرى.

قم بتنزيل نموذج CSV لمعرفة سمات العمود المعتمدة.

1. في جزء التنقل **، حدد الإعدادات** \> **نقاط** \> **النهاية** (ضمن **القواعد**).

2. حدد علامة تبويب نوع الكيان الذي تريد استيراد المؤشرات له.

3. حدد **استيراد** \> **اختيار ملف**.

4. حدد **استيراد**. يمكنك القيام بذلك لجميع الملفات التي تريد استيرادها.

5. حدد **تم**.

> [!NOTE]
> يمكن تحميل 500 مؤشر فقط لكل دفعة.

يعرض الجدول التالي المعلمات المعتمدة.

المعلمة|النوع|الوصف
:---|:---|:---
indicatorType|تعداد|نوع المؤشر. القيم المحتملة هي: "FileSha1" و"FileSha256" و"IpAddress" و"DomainName" و"Url". **مطلوب**
indicatorValue|سلسلة|هوية كيان [المؤشر](ti-indicator.md) . **مطلوب**
إجراء|تعداد|الإجراء الذي سيتم اتخاذه إذا تم اكتشاف المؤشر في المؤسسة. القيم المحتملة هي: "تنبيه" و"AlertAndBlock" و"مسموح به". **مطلوب**
العنوان|سلسلة|عنوان تنبيه المؤشر. **مطلوب**
الوصف|سلسلة| وصف المؤشر. **مطلوب**
expirationTime|DateTimeOffset|وقت انتهاء صلاحية المؤشر في التنسيق التالي YYYY-MM-DDTHH:MM:SS.0Z. يتم حذف المؤشر إذا مر وقت انتهاء الصلاحية وما يحدث عند وقت انتهاء الصلاحية عند قيمة الثواني (SS). **اختياري**
الخطورة|تعداد|خطورة المؤشر. القيم المحتملة هي: "معلوماتي" و"منخفض" و"متوسط" و"عال". **اختياري**
recommendedActions|سلسلة|تنبيه مؤشر TI الإجراءات الموصى بها. **اختياري**
rbacGroupNames|سلسلة|قائمة مفصولة بفصول فاصلة لأسماء مجموعة RBAC التي سيتم تطبيق المؤشر عليها. **اختياري**
الفئة|سلسلة|فئة التنبيه. وتشمل الأمثلة: التنفيذ والوصول إلى بيانات الاعتماد. **اختياري**
mitretechniques|سلسلة|رمز/id لتقنيات MITRE (مفصولة ب فاصلة). لمزيد من المعلومات، راجع [الأساليب الخاصة بالمؤسسات](https://attack.mitre.org/tactics/enterprise/). **اختياري** من المستحسن إضافة قيمة في الفئة عندما تكون تقنية MITRE.
GenerateAlert|سلسلة|ما إذا كان يجب إنشاء التنبيه أم لا. القيم المحتملة هي: True أو False. **اختياري**



> [!NOTE]
> إن Inter-Domain التوجيه (CIDR) غير معتمدة.
لمزيد من المعلومات، راجع محاذاة [فئات تنبيهات نقطة النهاية في Microsoft Defender الآن مع MITRE ATT&CK!](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/microsoft-defender-atp-alert-categories-are-now-aligned-with/ba-p/732748).

## <a name="see-also"></a>راجع أيضًا

- [إنشاء مؤشرات](manage-indicators.md)
- [إنشاء مؤشرات للملفات](indicator-file.md)
- [إنشاء مؤشرات ل IPs أو عناوين URL/المجالات](indicator-ip-domain.md)
- [إنشاء مؤشرات استنادا إلى الشهادات](indicator-certificates.md)
