---
title: تفاصيل ونتائج التحقيق التلقائي
description: عرض النتائج والنتائج الأساسية الخاصة بالتحقيق التلقائي في Microsoft 365 Defender
keywords: تلقائي، التحقيق، النتائج، التحليل، التفاصيل، المعالجة، الهاتف التلقائي
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
ms.openlocfilehash: 05e16a32fb21f682a756c32201a69c192d398184
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/08/2022
ms.locfileid: "63575701"
---
# <a name="details-and-results-of-an-automated-investigation"></a>تفاصيل ونتائج التحقيق التلقائي

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**ينطبق على:**
- Microsoft 365 Defender

مع Microsoft 365 Defender، عند تشغيل تحقيق تلقائي، [](m365d-autoir.md) تتوفر تفاصيل حول هذا التحقيق أثناء عملية التحقيق التلقائية وبعدها. إذا كانت لديك الأذونات اللازمة، يمكنك عرض هذه التفاصيل في طريقة عرض تفاصيل التحقيق التي توفر لك الحالة الم تاريخا والقدرة على الموافقة على أي إجراءات معلقة.[](m365d-action-center.md#required-permissions-for-action-center-tasks) 

## <a name="new-unified-investigation-page"></a>(NEW) صفحة التحقيق الموحد

تم تحديث صفحة التحقيق مؤخرا لتضمين معلومات عبر أجهزتك والبريد الإلكتروني ومحتوى التعاون. تعرف صفحة "التحقيق الموحد" الجديدة لغة شائعة وتوفر تجربة موحدة من أجل إجراء عمليات تحقيق تلقائية عبر [Microsoft Defender ل Endpoint](/windows/security/threat-protection/microsoft-defender-atp/microsoft-defender-advanced-threat-protection) و Microsoft [Defender Office 365](../office-365-security/defender-for-office-365.md). للوصول إلى صفحة التحقيق الموحد، حدد الارتباط في الشعار الأصفر الذي ستشاهده على:

- أي صفحة تحقيق في Office 365 <a href="https://go.microsoft.com/fwlink/p/?linkid=2077143" target="_blank">مركز & التوافق</a>
- أي صفحة تحقيق في Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com))
- أي حادث أو تجربة لمركز الإجراءات في <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">مدخل</a> Microsoft 365 Defender

## <a name="open-the-investigation-details-view"></a>فتح طريقة عرض تفاصيل التحقيق

يمكنك فتح طريقة عرض تفاصيل التحقيق باستخدام أحد الأساليب التالية:

- [تحديد عنصر في مركز الإجراءات](#select-an-item-in-the-action-center)
- [تحديد تحقيق من صفحة تفاصيل الحادث](#open-an-investigation-from-an-incident-details-page)

### <a name="select-an-item-in-the-action-center"></a>تحديد عنصر في مركز الإجراءات

يجمع [مركز الإجراءات](m365d-action-center.md) المحسن ([https://security.microsoft.com/action-center](https://security.microsoft.com/action-center)) إجراءات المعالجة عبر [](m365d-remediation-actions.md) أجهزتك والبريد الإلكتروني & ومحتوى التعاون والهويات. تتضمن الإجراءات المدرجة إجراءات الإصلاح التي تم اتخاذها تلقائيا أو يدويا. في مركز الإجراءات، يمكنك عرض الإجراءات التي تنتظر الموافقة والإجراءات التي تمت الموافقة عليها أو إكمالها بالفعل. يمكنك أيضا الانتقال إلى مزيد من التفاصيل، مثل صفحة التحقيق.

> [!TIP]
> يجب أن يكون [لديك أذونات معينة](m365d-action-center.md#required-permissions-for-action-center-tasks) للموافقة على الإجراءات أو رفضها أو التراجع عنها.

1. انتقل إلى <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender المدخل ثم</a> سجل الدخول. 

2. في جزء التنقل، اختر **مركز الإجراءات**. 

3. على علامة **التبويب معلق** **أو محفوظات** ، حدد أحد العناصر. يفتح جزء منتفطها.

4. راجع المعلومات في جزء المعلومات من خلال الجزء الذي يتم التقاطه، ثم قم بوا إحدى الخطوات التالية:
   - حدد **فتح صفحة التحقيق** لعرض مزيد من التفاصيل حول التحقيق.
   - حدد **موافقة** لبدء إجراء معلق.
   - حدد **رفض** لمنع اتخاذ إجراء معلق.
   - حدد **الانتقال إلى البحث** عن [طريق البحث المتقدم](advanced-hunting-overview.md).

### <a name="open-an-investigation-from-an-incident-details-page"></a>فتح تحقيق من صفحة تفاصيل الحادث

استخدم صفحة تفاصيل الحادث لعرض معلومات مفصلة حول حادث، بما في ذلك التنبيهات التي تم تشغيلها معلومات حول أي أجهزة أو حسابات مستخدمين أو علب بريد متأثرة.

1. انتقل إلى <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender المدخل ثم</a> سجل الدخول. 

2. في جزء التنقل، اختر **& تنبيهاتIncidents** > . 

3. حدد عنصر في القائمة، ثم اختر **فتح صفحة الحادث**.

4. حدد علامة **التبويب "التحقيق** "، ثم حدد تحقيق في القائمة. يفتح جزء منتفطها.

5. حدد **فتح صفحة التحقيق**. 

فيما يلي مثال على ذلك.

:::image type="content" source="../../media/mtp-incidentdetails-tabs.png" alt-text="مثال لصفحة تحقيق." lightbox="../../media/mtp-incidentdetails-tabs.png":::

## <a name="investigation-details"></a>تفاصيل التحقيق

استخدم طريقة عرض تفاصيل التحقيق لرؤية النشاط السابق، الحالي، المعلق فيما يتعلق بالتحقيق. فيما يلي مثال على ذلك.

:::image type="content" source="../../media/mtp-air-investdetails.png" alt-text="مثال على تفاصيل التحقيق." lightbox="../../media/mtp-air-investdetails.png":::

في طريقة عرض تفاصيل التحقيق، يمكنك الاطلاع على معلومات على علامات التبويب رسم التحقيق والتنبيهات والأجهزة والهويات والنتائج الرئيسية والكيانات والسجل والإجراءات المعلقة، كما  هو موضح في الجدول التالي. 

> [!NOTE]
> تعتمد علامات التبويب المحددة التي تراها في صفحة تفاصيل التحقيق على ما يتضمنه اشتراكك. على سبيل المثال، إذا لم يتضمن اشتراكك Microsoft Defender Office 365 الخطة 2، فلن ترى علامة التبويب **علب** البريد.

| Tab | الوصف |
|:--------|:--------|
| **رسم بياني للتحري** | يوفر تمثيلا مرئيا للتحري. يصف الكيانات ويدرج التهديدات التي تم العثور عليها، إلى جانب التنبيهات وما إذا كانت هناك أي إجراءات بانتظار الموافقة.<br/>يمكنك تحديد عنصر في الرسم البياني لعرض المزيد من التفاصيل. على سبيل المثال، يأخذك **تحديد أيقونة** الدليل إلى  علامة التبويب دليل، حيث يمكنك رؤية الكيانات التي تم الكشف عنها وحكمها. |
| **التنبيهات** | يسرد التنبيهات المقترنة بالتحقيق. يمكن أن تأتي التنبيهات من ميزات الحماية من المخاطر على جهاز المستخدم، وفي تطبيقات Office، و Microsoft Defender لتطبيقات السحابة، وميزات Microsoft 365 Defender الأخرى.|
| **الأجهزة** | تسرد الأجهزة المضمنة في التحقيق إلى جانب مستوى المعالجة الخاصة بها. (تتوافق مستويات المعالجة [مع مستوى التنفيذ التلقائي لمجموعات الأجهزة](m365d-configure-auto-investigation-response.md#review-or-change-the-automation-level-for-device-groups).) |
| **علب البريد** |يسرد علب البريد التي تؤثر عليها التهديدات التي تم الكشف عنها.  |
| **المستخدمون**  | تسرد حسابات المستخدمين التي تؤثر عليها التهديدات التي تم الكشف عنها. |
| **الدليل** | يسرد أجزاء من الإثباتات التي تم رفعها بواسطة التنبيهات أو التحقيقات. تتضمن الأحكام (*ضار* أو *مريب* أو *غير معروف* أو *عدم* العثور على تهديدات) ووضع المعالجة. |
| **الكيانات** | يوفر تفاصيل حول كل كيان تم تحليله، بما في ذلك قرار لكل نوع *كيان (تهديدات* ضارة أو مريبة أو *عدم العثور على تهديدات*).|
|**سجل** | توفر طريقة عرض مفصلة ومتزامنة لجميع إجراءات التحقيق التي تم اتخاذها بعد تشغيل تنبيه.|
| **محفوظات الإجراءات المعلقة** | تسرد العناصر التي تتطلب الموافقة للمتابعة. انتقل إلى مركز الإجراءات ([https://security.microsoft.com/action-center](https://security.microsoft.com/action-center)) للموافقة على الإجراءات المعلقة. |

## <a name="next-steps"></a>الخطوات التالية

- [عرض إجراءات الإصلاح وإدارتها](m365d-autoir-actions.md)
- [تعرف على المزيد حول إجراءات الإصلاح](m365d-remediation-actions.md)
