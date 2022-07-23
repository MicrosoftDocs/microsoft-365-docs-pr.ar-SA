---
title: إدارة المؤشرات
ms.reviewer: ''
description: إدارة مؤشرات تجزئة ملف أو عنوان IP أو عناوين URL أو المجالات التي تحدد الكشف عن الكيانات ومنعها واستبعادها.
keywords: استيراد، مؤشر، قائمة، ioc، csv، إدارة، مسموح بها، محظورة، حظر، كتلة، نظيفة، ضارة، تجزئة الملف، عنوان ip، urls، المجال
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
ms.openlocfilehash: 4619b24d06af4cdb80916fb9eacbc52b2fa55c21
ms.sourcegitcommit: 0a67e239549752fcdbcff660189f34b51ec273f5
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/23/2022
ms.locfileid: "66983950"
---
# <a name="manage-indicators"></a>إدارة المؤشرات

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**ينطبق على:**
- [الخطة 1 من Microsoft Defender لنقطة النهاية](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Defender for Endpoint الخطة 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)


> هل تريد تجربة Defender لنقطة النهاية؟ [التسجيل للحصول على إصدار تجريبي مجاني.](https://www.microsoft.com/WindowsForBusiness/windows-atp?ocid=docs-wdatp-automationexclusionlist-abovefoldlink)

1. في جزء التنقل، حدد مؤشرات \> **نقاط النهاية** **للإعدادات** \> (ضمن **القواعد**).

2. حدد علامة تبويب نوع الكيان الذي تريد إدارته.

3. قم بتحديث تفاصيل المؤشر وانقر فوق **"حفظ** " أو انقر فوق الزر **"حذف** " إذا كنت تريد إزالة الكيان من القائمة.

## <a name="import-a-list-of-iocs"></a>استيراد قائمة ب IoCs

يمكنك أيضا اختيار تحميل ملف CSV الذي يحدد سمات المؤشرات، والإجراء الذي يجب اتخاذه، وتفاصيل أخرى.

قم بتنزيل نموذج CSV لمعرفة سمات العمود المعتمدة.

1. في جزء التنقل، حدد مؤشرات \> **نقاط النهاية** **للإعدادات** \> (ضمن **القواعد**).

2. حدد علامة تبويب نوع الكيان الذي تريد استيراد مؤشرات له.

3. حدد **ملف Import** \> **Choose**.

4. حدد **استيراد**. قم بذلك لجميع الملفات التي تريد استيرادها.

5. حدد **«Done»**.

> [!NOTE]
> يمكن تحميل 500 مؤشر فقط لكل دفعة.

يعرض الجدول التالي المعلمات المدعومة.

المعلمه|نوع|الوصف
:---|:---|:---
نوع المؤشر|التعداد|نوع المؤشر. القيم المحتملة هي: "FileSha1" و"FileSha256" و"IpAddress" و"DomainName" و"Url". **مطلوب**
قيمة المؤشر|سلسلة|هوية كيان [المؤشر](ti-indicator.md) . **مطلوب**
العمل|التعداد|الإجراء الذي سيتم اتخاذه إذا تم اكتشاف المؤشر في المؤسسة. القيم المحتملة هي: "Alert" و"AlertAndBlock" و"Allowed". **مطلوب**
عنوان|سلسلة|عنوان تنبيه المؤشر. **مطلوب**
وصف|سلسلة| وصف المؤشر. **مطلوب**
انتهاء الصلاحية|DateTimeOffset|وقت انتهاء صلاحية المؤشر بالتنسيق التالي YYYY-MM-DDTHH:MM:SS.0Z. يتم حذف المؤشر إذا مر وقت انتهاء الصلاحية وكل ما يحدث في وقت انتهاء الصلاحية يحدث في قيمة الثوان (SS). **اختياري**
شده|التعداد|خطورة المؤشر. القيم المحتملة هي: "معلوماتي" و"منخفض" و"متوسط" و"عال". **اختياري**
الإجراءات الموصى بها|سلسلة|الإجراءات الموصى بها لتنبيه مؤشر TI. **اختياري**
rbacGroups|سلسلة|قائمة مفصولة بفواصل لمجموعات RBAC التي سيتم تطبيق المؤشر عليها. **اختياري**
الفئه|سلسلة|فئة التنبيه. ومن الأمثلة على ذلك: التنفيذ والوصول إلى بيانات الاعتماد. **اختياري**
mitretechniques|سلسلة|رمز/معرف تقنيات MITRE (مفصول بفاواصل). لمزيد من المعلومات، راجع [تكتيكات المؤسسة](https://attack.mitre.org/tactics/enterprise/). **الاختياري** يوصى بإضافة قيمة في الفئة عند تقنية MITRE.
GenerateAlert|سلسلة|ما إذا كان يجب إنشاء التنبيه. القيم المحتملة هي: صواب أو خطأ. **اختياري**

> [!NOTE]
> لا يتم اعتماد رموز التوجيه Inter-Domain (CIDR) بلا فئة لعناوين IP.
لمزيد من المعلومات، راجع [Microsoft Defender لنقطة النهاية فئات التنبيه تمت محاذاتها الآن مع MITRE ATT&CK!](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/microsoft-defender-atp-alert-categories-are-now-aligned-with/ba-p/732748).

شاهد هذا الفيديو لمعرفة كيف يوفر Microsoft Defender لنقطة النهاية طرقا متعددة لإضافة مؤشرات التسوية (IoCs) وإدارتها. 
> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4qLVw]

## <a name="see-also"></a>راجع أيضًا

- [إنشاء مؤشرات](manage-indicators.md)
- [إنشاء مؤشرات للملفات](indicator-file.md)
- [إنشاء مؤشرات لـ IPs أو عناوين URL/المجالات](indicator-ip-domain.md)
- [إنشاء مؤشرات استنادا إلى الشهادات](indicator-certificates.md)
