---
title: تفضل بزيارة مركز الإجراءات لمشاهدة إجراءات الإصلاح
description: استخدام مركز الإجراءات لعرض التفاصيل والنتائج بعد إجراء تحقيق تلقائي
keywords: إجراء، مركز، تلقائي، تلقائي، تحقيق، استجابة، إصلاح
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
author: dansimp
ms.author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
- m365initiative-defender-endpoint
ms.custom: admindeeplinkDEFENDER
ms.topic: how-to
ms.reviewer: ramarom, evaldm, isco, mabraitm, chriggs
ms.date: 01/28/2021
ms.technology: mde
ms.openlocfilehash: 3cd45506601202a4a1bd5a400eeb51a0e07cecc0
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/25/2022
ms.locfileid: "64473024"
---
# <a name="visit-the-action-center-to-see-remediation-actions"></a>تفضل بزيارة مركز الإجراءات لمشاهدة إجراءات الإصلاح

أثناء إجراء تحقيق تلقائي وبعده، يتم تحديد إجراءات المعالجة للكشف عن المخاطر. وفقا للتهديدات الخاصة وكيفية [Microsoft Defender لنقطة النهاية](/windows/security/threat-protection) لمنظمتك، يتم اتخاذ بعض إجراءات المعالجة تلقائيا، بينما تتطلب إجراءات أخرى الموافقة. إذا كنت جزءا من فريق عمليات الأمان في مؤسستك، يمكنك عرض إجراءات المعالجة المعلقة والمكتملة في **مركز الإجراءات**.[](manage-auto-investigation.md#remediation-actions)


**ينطبق على:**
- [Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

## <a name="new-a-unified-action-center"></a>(جديد!) مركز إجراءات موحد


يسرنا أن نعلن عن مركز إجراءات موحد جديد ([https://security.microsoft.com/action-center](https://security.microsoft.com/action-center))!

:::image type="content" source="images/mde-action-center-unified.png" alt-text="صفحة مركز الإجراءات في مدخل Microsoft 365 Defender" lightbox="images/mde-action-center-unified.png":::

يقارن الجدول التالي بين مركز الإجراءات الموحد الجديد ومركز الإجراءات السابق.

|مركز الإجراءات الموحد الجديد  |مركز الإجراءات السابق  |
|---------|---------|
|تسرد الإجراءات المعلقة والمكتملة للأجهزة والبريد الإلكتروني في موقع واحد <br/>([Microsoft Defender لنقطة النهاية](microsoft-defender-endpoint.md) بالإضافة [Microsoft Defender لـ Office 365](/microsoft-365/security/office-365-security/office-365-atp))|قوائم الإجراءات المعلقة والمكتملة للأجهزة <br/> ([Microsoft Defender لنقطة النهاية](microsoft-defender-endpoint.md) فقط)   |
|يقع في:<br/>[https://security.microsoft.com/action-center](https://security.microsoft.com/action-center)         |يقع في:<br/>[https://securitycenter.windows.com/action-center](https://securitycenter.windows.com/action-center)     |
| في مدخل <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender،</a> اختر **مركز الإجراءات**. <p>:::image type="content" source="images/action-center-nav-new.png" alt-text="جزء التنقل إلى مركز الإجراءات في مدخل Microsoft 365 Defender" lightbox="images/action-center-nav-new.png"::: | في المدخل Microsoft 365 Defender، اختر **مركز عمليات البحث التلقائية** > . <p>:::image type="content" source="images/action-center-nav-old.png" alt-text="إصدار أقدم من جزء التنقل إلى مركز الإجراءات في مدخل Microsoft 365 Defender" lightbox="images/action-center-nav-old.png":::  |

يجمع مركز الإجراءات الموحد إجراءات المعالجة عبر Defender for Endpoint Defender لـ Office 365. وهو يعرف لغة شائعة لجميع إجراءات المعالجة، ويوفر تجربة تحقيق موحدة.

يمكنك استخدام مركز الإجراءات الموحد إذا كانت لديك الأذونات المناسبة واشتراك واحد أو أكثر من الاشتراكات التالية:

- [Defender لنقطة النهاية](microsoft-defender-endpoint.md)
- [Defender لـ Office 365](/microsoft-365/security/office-365-security/office-365-atp)
- [Microsoft 365 Defender](/microsoft-365/security/mtp/microsoft-threat-protection)

> [!TIP]
> لمعرفة المزيد، راجع [المتطلبات](/microsoft-365/security/mtp/prerequisites).

## <a name="using-the-action-center"></a>استخدام مركز الإجراءات

للوصول إلى مركز الإجراءات الموحد في مدخل Microsoft 365 Defender المحسن:

1. انتقل إلى Microsoft 365 Defender <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">المدخل</a> ثم سجل الدخول.
2. في جزء التنقل، حدد **مركز الإجراءات**.

عند زيارة مركز الإجراءات، سترى علامة تبويب: **الإجراءات المعلقة** **والمحفوظات**. يلخص الجدول التالي ما ستشاهده على كل علامة تبويب:

|Tab|الوصف|
|---|---|
|**معلق**|يعرض قائمة الإجراءات التي تتطلب الانتباه. يمكنك الموافقة على الإجراءات أو رفضها كل إجراء على الأخرى، أو تحديد إجراءات متعددة إذا كان لها نفس نوع الإجراء (مثل **ملف الفحص**). <p> **تلميح**: تأكد من مراجعة [(](manage-auto-investigation.md) أو رفض) الإجراءات المعلقة في أسرع وقت ممكن بحيث يمكن إكمال عمليات التحقيق التلقائية في الوقت المناسب.|
|**المحفوظات**|يعمل كسجل تدقيق الإجراءات التي تم اتخاذها، مثل: <ul><li>إجراءات الإصلاح التي تم اتخاذها نتيجة عمليات التحقيق التلقائية</li><li>إجراءات الإصلاح التي وافق عليها فريق عمليات الأمان</li><li>الأوامر التي تم تشغيلها والإجراءات التي تم تطبيقها أثناء جلسات الاستجابة المباشرة</li><li>إجراءات المعالجة التي تم اتخاذها بواسطة ميزات الحماية من المخاطر في برنامج الحماية من الفيروسات من Microsoft Defender</li></ul> <p> يوفر طريقة للتراجع عن إجراءات معينة (راجع [التراجع عن الإجراءات المكتملة](manage-auto-investigation.md#undo-completed-actions)).|

يمكنك تخصيص البيانات وفرزها وتصفيتها وتصديرها في مركز الإجراءات.

:::image type="content" source="images/new-action-center-columnsfilters.png" alt-text="مركز الإجراءات مع أعمدة وتصفية" lightbox="images/new-action-center-columnsfilters.png":::

- حدد عنوان عمود لفرز العناصر بترتيب تصاعدي أو تنازلي.
- استخدم عامل تصفية الفترة الزمنية لعرض بيانات اليوم أو الأسبوع أو 30 يوما أو 6 أشهر الماضية.
- اختر الأعمدة التي تريد عرضها.
- حدد عدد العناصر التي يجب تضمينها في كل صفحة من صفحات البيانات.
- استخدم عوامل التصفية لعرض العناصر التي تريد رؤيتها فقط.
- حدد **تصدير** لتصدير النتائج إلى ملف .csv.

## <a name="next-steps"></a>الخطوات التالية

- [عرض إجراءات الإصلاح والموافقة عليها](manage-auto-investigation.md)
- [راجع الدليل التفاعلي: التحقق من التهديدات باستخدام Microsoft Defender لنقطة النهاية](https://aka.ms/MDATP-IR-Interactive-Guide)

## <a name="see-also"></a>راجع أيضًا

- [معالجة الإيجابيات/السلبيات الخاطئة في Microsoft Defender لنقطة النهاية](defender-endpoint-false-positives-negatives.md)
