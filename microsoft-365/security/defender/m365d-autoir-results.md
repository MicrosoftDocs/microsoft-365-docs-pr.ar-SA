---
title: تفاصيل ونتائج تحقيق تلقائي
description: عرض النتائج والنتائج الرئيسية للتحقيق التلقائي في Microsoft 365 Defender
keywords: تلقائي، التحقيق، النتائج، التحليل، التفاصيل، المعالجة، التشغيل التلقائي
search.appverid: met150
ms.prod: m365-security
ms.technology: m365d
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
ms.topic: conceptual
ms.custom:
- autoir
- admindeeplinkDEFENDER
ms.reviewer: evaldm, isco
ms.openlocfilehash: cc53717feed347019540ffcb8c85687a6c28537f
ms.sourcegitcommit: bfbe2574f487ced69e711b48ce140120bd99181b
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/02/2022
ms.locfileid: "66607466"
---
# <a name="details-and-results-of-an-automated-investigation"></a>تفاصيل ونتائج تحقيق تلقائي

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**ينطبق على:**
- Microsoft 365 Defender

مع Microsoft 365 Defender، عند تشغيل [تحقيق تلقائي](m365d-autoir.md)، تتوفر تفاصيل حول هذا التحقيق في أثناء عملية التحقيق التلقائي وبعدها. إذا كان لديك [الأذونات اللازمة](m365d-action-center.md#required-permissions-for-action-center-tasks)، يمكنك عرض هذه التفاصيل في طريقة عرض تفاصيل التحقيق التي توفر لك الحالة المحدثة والقدرة على الموافقة على أي إجراءات معلقة. 

## <a name="new-unified-investigation-page"></a>(جديد) صفحة التحقيق الموحد

تم تحديث صفحة التحقيق مؤخرا لتضمين معلومات عبر أجهزتك والبريد الإلكتروني ومحتوى التعاون. تحدد صفحة التحقيق الموحدة الجديدة لغة مشتركة وتوفر تجربة موحدة للتحقيقات التلقائية عبر [Microsoft Defender لنقطة النهاية](/windows/security/threat-protection/microsoft-defender-atp/microsoft-defender-advanced-threat-protection) [Microsoft Defender لـ Office 365](../office-365-security/defender-for-office-365.md). للوصول إلى صفحة التحقيق الموحدة، حدد الارتباط في الشعار الأصفر الذي ستشاهده على:

- أي صفحة تحقيق في <a href="https://go.microsoft.com/fwlink/p/?linkid=2077143" target="_blank">مركز توافق & الأمان Office 365</a>
- أي صفحة تحقيق في مدخل Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com))
- أي حدث أو تجربة مركز الصيانة في <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">مدخل Microsoft 365 Defender</a>

## <a name="open-the-investigation-details-view"></a>فتح طريقة عرض تفاصيل التحقيق

يمكنك فتح طريقة عرض تفاصيل التحقيق باستخدام إحدى الطرق التالية:

- [تحديد عنصر في مركز الصيانة](#select-an-item-in-the-action-center)
- [تحديد تحقيق من صفحة تفاصيل الحادث](#open-an-investigation-from-an-incident-details-page)

### <a name="select-an-item-in-the-action-center"></a>تحديد عنصر في مركز الصيانة

يجمع [مركز الصيانة](m365d-action-center.md) المحسن ([https://security.microsoft.com/action-center](https://security.microsoft.com/action-center)) [بين إجراءات المعالجة](m365d-remediation-actions.md) عبر أجهزتك والبريد الإلكتروني & محتوى التعاون والهويات. تتضمن الإجراءات المدرجة إجراءات المعالجة التي تم اتخاذها تلقائيا أو يدويا. في مركز الصيانة، يمكنك عرض الإجراءات التي تنتظر الموافقة والإجراءات التي تمت الموافقة عليها أو إكمالها بالفعل. يمكنك أيضا الانتقال إلى مزيد من التفاصيل، مثل صفحة التحقيق.

> [!TIP]
> يجب أن يكون لديك [أذونات معينة](m365d-action-center.md#required-permissions-for-action-center-tasks) للموافقة على الإجراءات أو رفضها أو التراجع عنها.

1. انتقل إلى <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">مدخل Microsoft 365 Defender</a> وسجل الدخول. 

2. في جزء التنقل، اختر **مركز الصيانة**. 

3. في علامة التبويب **"معلق** " أو " **محفوظات** "، حدد عنصرا. يتم فتح جزء القائمة المنبثقة الخاص به.

4. راجع المعلومات في جزء القائمة المنبثقة، ثم اتخذ إحدى الخطوات التالية:
   - حدد **صفحة فتح التحقيق** لعرض مزيد من التفاصيل حول التحقيق.
   - حدد **"موافقة** " لبدء إجراء معلق.
   - حدد **"رفض** " لمنع اتخاذ إجراء معلق.
   - حدد **Go hunt** للانتقال إلى [التتبع المتقدم](advanced-hunting-overview.md).

### <a name="open-an-investigation-from-an-incident-details-page"></a>فتح تحقيق من صفحة تفاصيل الحادث

استخدم صفحة تفاصيل الحادث لعرض معلومات مفصلة حول حادث، بما في ذلك التنبيهات التي تم تشغيلها معلومات حول أي أجهزة متأثرة أو حسابات مستخدمين أو علب بريد.

1. انتقل إلى <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">مدخل Microsoft 365 Defender</a> وسجل الدخول. 

2. في جزء التنقل، اختر **Incidents & alerts** > **Incidents**. 

3. حدد عنصرا في القائمة، ثم اختر **"فتح صفحة الحدث**".

4. حدد علامة التبويب **"Investigations** "، ثم حدد التحقيق في القائمة. يتم فتح جزء القائمة المنبثقة الخاص به.

5. حدد **صفحة التحقيق المفتوح**. 

فيما يلي مثال على ذلك.

:::image type="content" source="../../media/mtp-incidentdetails-tabs.png" alt-text="صفحة التحقيق في مدخل Microsoft 365 Defender" lightbox="../../media/mtp-incidentdetails-tabs.png":::

## <a name="investigation-details"></a>تفاصيل التحقيق

استخدم طريقة عرض تفاصيل التحقيق لرؤية النشاط السابق، الحالي، والمعلق المتعلق بالتحقيق. فيما يلي مثال على ذلك.

:::image type="content" source="../../media/mtp-air-investdetails.png" alt-text="صفحة تفاصيل التحقيق في مدخل Microsoft 365 Defender" lightbox="../../media/mtp-air-investdetails.png":::

في طريقة عرض تفاصيل التحقيق، يمكنك الاطلاع على معلومات حول علامات تبويب **«Investigation graph»** و«**Alerts**» **و«Devices****» و«Identities**» و **«Key findings****» و«Entities**» و«**Log**» و«**Pending actions**»، الموضحة في الجدول التالي.

> [!NOTE]
> تعتمد علامات التبويب المحددة التي تراها في صفحة تفاصيل التحقيق على ما يتضمنه اشتراكك. على سبيل المثال، إذا لم يتضمن اشتراكك Microsoft Defender لـ Office 365 الخطة 2، فلن تظهر علامة تبويب **"علب البريد**".

| التبويب | الوصف |
|:--------|:--------|
| **رسم بياني للتحقيق** | يوفر تمثيلا مرئيا للتحقيق. يصور الكيانات ويسرد التهديدات التي تم العثور عليها، إلى جانب التنبيهات وما إذا كانت أي إجراءات تنتظر الموافقة.<br/>يمكنك تحديد عنصر على الرسم البياني لعرض المزيد من التفاصيل. على سبيل المثال، يؤدي تحديد أيقونة **الدليل** إلى الانتقال إلى علامة التبويب **"دليل** "، حيث يمكنك رؤية الكيانات المكتشفة وأحكامها. |
| **التنبيهات** | يسرد التنبيهات المرتبطة بالتحقيق. يمكن أن تأتي التنبيهات من ميزات الحماية من التهديدات على جهاز المستخدم وفي تطبيقات Office Microsoft Defender for Cloud Apps وميزات Microsoft 365 Defender الأخرى. <br> <br> لاحظ أنه إذا رأيت *نوع تنبيه غير معتمد*، فهذا يعني أن قدرات التحقيق التلقائي لا يمكنها التقاط هذا التنبيه لتشغيل تحقيق تلقائي. ومع ذلك، يمكنك [التحقق من هذه التنبيهات يدويا](investigate-incidents.md#alerts).
| **الاجهزه** | يسرد الأجهزة المضمنة في التحقيق إلى جانب مستوى المعالجة. (تتوافق مستويات المعالجة مع [مستوى التشغيل التلقائي لمجموعات الأجهزة](m365d-configure-auto-investigation-response.md#review-or-change-the-automation-level-for-device-groups).) |
| **صناديق البريد** |يسرد علب البريد التي تأثرت بالتهديدات المكتشفة.  |
| **المستخدمون**  | سرد حسابات المستخدمين المتأثرة بالتهديدات المكتشفة. |
| **الادله** | يسرد أجزاء من الأدلة التي تثيرها التنبيهات أو التحقيقات. يتضمن أحكاما (*ضارة* أو *مريبة* أو *غير معروفة* أو *لم يتم العثور على تهديدات*) وحالة المعالجة. |
| **الكيانات** | يوفر تفاصيل حول كل كيان تم تحليله، بما في ذلك حكم لكل نوع كيان (تم العثور على تهديدات *ضارة* أو *مريبة* أو *لا توجد تهديدات*).|
|**سجل** | يوفر عرضا زمنيا مفصلا لجميع إجراءات التحقيق التي تم اتخاذها بعد تشغيل تنبيه.|
| **محفوظات الإجراءات المعلقة** | سرد العناصر التي تتطلب الموافقة للمتابعة. انتقل إلى مركز الصيانة ([https://security.microsoft.com/action-center](https://security.microsoft.com/action-center)) للموافقة على الإجراءات المعلقة. |

## <a name="next-steps"></a>الخطوات التالية

- [عرض إجراءات الإصلاح وإدارتها](m365d-autoir-actions.md)
- [معرفة المزيد حول إجراءات المعالجة](m365d-remediation-actions.md)
