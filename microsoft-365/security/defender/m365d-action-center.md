---
title: انتقل إلى مركز الإجراءات لعرض مهام الإصلاح والتحري التلقائية والموافقة عليها
description: استخدام مركز الإجراءات لعرض تفاصيل حول التحقيق التلقائي والموافقة على الإجراءات المعلقة
keywords: مركز الإجراءات، الحماية من المخاطر، التحقيق، التنبيه، معلق، تلقائي، الكشف
search.appverid: met150
ms.prod: m365-security
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
ms.topic: how-to
ms.custom:
- autoir
- admindeeplinkDEFENDER
ms.reviewer: evaldm, isco
ms.openlocfilehash: 0bd86f7ba05ce04743f547292105875f3b8234b1
ms.sourcegitcommit: 3b8e009ea1ce928505b8fc3b8926021fb91155f3
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/28/2022
ms.locfileid: "64499056"
---
# <a name="the-action-center"></a>مركز الإجراءات

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**ينطبق على:**
- Microsoft 365 Defender

يوفر مركز الإجراءات تجربة "جزء واحد من الزجاج" لمهام التنبيه والحادث مثل:

- الموافقة على إجراءات المعالجة المعلقة.
- عرض سجل تدقيق إجراءات المعالجة المعتمدة بالفعل.
- مراجعة إجراءات المعالجة المكتملة.

نظرا لأن مركز الإجراءات يوفر طريقة عرض شاملة Microsoft 365 Defender العمل، يمكن لفريق عمليات الأمان العمل بفعالية وفعالية أكبر.

## <a name="the-unified-action-center"></a>مركز الإجراءات الموحد

يسرد مركز الإجراءات الموحد ([https://security.microsoft.com/action-center](https://security.microsoft.com/action-center)) إجراءات المعالجة المعلقة والمكتملة للأجهزة والبريد الإلكتروني & محتوى التعاون والهويات في موقع واحد.

:::image type="content" source="../../media/m3d-action-center-unified.png" alt-text="مركز الإجراءات الموحد في مدخل Microsoft 365 Defender." lightbox="../../media/m3d-action-center-unified.png":::

على سبيل المثال: 

- إذا كنت تستخدم مركز Office 365 الأمان & ([https://protection.office.com](https://protection.office.com))، فجرب مركز الإجراءات الموحد <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">في Microsoft 365 Defender المدخل</a>.
- إذا كنت تستخدم مركز الإجراءات في مركز حماية Microsoft Defender ([https://securitycenter.windows.com/action-center](https://securitycenter.windows.com/action-center))، فجرب مركز الإجراءات الموحد في Microsoft 365 Defender <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">المدخل</a>.
- إذا كنت تستخدم مدخل Microsoft 365 Defender بالفعل<a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank"></a>، فسوف ترى العديد من التحسينات في مركز الإجراءات ([https://security.microsoft.com/action-center](https://security.microsoft.com/action-center)).

يجمع مركز الإجراءات الموحد إجراءات المعالجة عبر Defender for Endpoint Defender لـ Office 365. وهو يعرف لغة شائعة لجميع إجراءات المعالجة ويوفر تجربة تحقيق موحدة. فريق عمليات الأمان لديك لديه تجربة "جزء واحد من الزجاج" لعرض إجراءات المعالجة وإدارتها.  

يمكنك استخدام مركز الإجراءات الموحد إذا كانت لديك الأذونات المناسبة واشتراك واحد أو أكثر من الاشتراكات التالية:

- [Defender لنقطة النهاية](../defender-endpoint/microsoft-defender-endpoint.md)
- [Defender لـ Office 365](/microsoft-365/security/office-365-security/defender-for-office-365)
- [Microsoft 365 Defender](microsoft-365-defender.md)

> [!TIP]
> لمعرفة المزيد، راجع [المتطلبات](./prerequisites.md).

## <a name="using-the-action-center"></a>استخدام مركز الإجراءات

1. انتقل إلى <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender المدخل ثم</a> سجل الدخول. 
2. في جزء التنقل، اختر **مركز الإجراءات**. 

عند زيارة مركز الإجراءات، سترى علامة تبويب: **الإجراءات المعلقة** **والمحفوظات**. يلخص الجدول التالي ما ستشاهده على كل علامة تبويب:

|Tab  |الوصف  |
|---------|---------|
|**معلق**     | يعرض قائمة الإجراءات التي تتطلب الانتباه. يمكنك الموافقة على الإجراءات أو رفضها كل إجراء على الأخرى، أو تحديد إجراءات متعددة إذا كان لها نفس نوع الإجراء (مثل ملف الفحص). <p>**تلميح**: تأكد من مراجعة (أو رفض) الإجراءات المعلقة في أسرع وقت ممكن بحيث يمكن إكمال عمليات التحقيق التلقائية في الوقت المناسب.       |
|**المحفوظات**     | يعمل كسجل تدقيق الإجراءات التي تم اتخاذها، مثل: <br/>- إجراءات الإصلاح التي تم اتخاذها نتيجة عمليات التحقيق التلقائية <br/>- إجراءات المعالجة التي تم اتخاذها على رسائل البريد الإلكتروني أو الملفات أو عناوين URL المريبة أو الضارة<br/>- إجراءات الإصلاح التي وافق عليها فريق عمليات الأمان <br/>- الأوامر التي تم تشغيلها والإجراءات الإصلاحية التي تم تطبيقها أثناء جلسات الاستجابة المباشرة<br/>- إجراءات الإصلاح التي تم اتخاذها بواسطة الحماية من الفيروسات <p>يوفر طريقة للتراجع عن إجراءات معينة (راجع [التراجع عن الإجراءات المكتملة](m365d-autoir-actions.md#undo-completed-actions)).        |

يمكنك تخصيص البيانات وفرزها وتصفيتها وتصديرها في مركز الإجراءات.

:::image type="content" source="../../media/m3d-action-center-columnsfilters.png" alt-text="إمكانات الفرز والتصفية وتخصيص مركز الإجراءات." lightbox="../../media/m3d-action-center-columnsfilters.png":::

- حدد عنوان عمود لفرز العناصر بترتيب تصاعدي أو تنازلي.
- استخدم عامل تصفية الفترة الزمنية لعرض بيانات اليوم أو الأسبوع أو 30 يوما أو 6 أشهر الماضية.
- اختر الأعمدة التي تريد عرضها.
- حدد عدد العناصر التي يجب تضمينها في كل صفحة من صفحات البيانات.
- استخدم عوامل التصفية لعرض العناصر التي تريد رؤيتها فقط.
- حدد **تصدير** لتصدير النتائج إلى ملف .csv.

## <a name="actions-tracked-in-the-action-center"></a>الإجراءات المتعقبة في مركز الإجراءات

يتم تعقب جميع الإجراءات، سواء كانت معلقة للموافقة أو تم اتخاذها بالفعل، في مركز الإجراءات. تتضمن الإجراءات المتوفرة ما يلي:

- تجميع حزمة التحقيق 
- جهاز معزول (يمكن التراجع عن هذا الإجراء) 
- جهاز Offboard 
- تنفيذ رمز الإصدار 
- الإصدار من الفحص 
- عينة الطلب 
- تقييد تنفيذ التعليمات البرمجية (يمكن التراجع عن هذا الإجراء) 
- تشغيل مسح الحماية من الفيروسات 
- إيقاف وفحص 

بالإضافة إلى إجراءات الإصلاح التي يتم اتخاذها تلقائيا نتيجة عمليات التحقيق التلقائية، يتعقب مركز الإجراءات أيضا الإجراءات التي اتخذها فريق الأمان لمعالجة التهديدات التي تم الكشف عنها والإجراءات التي تم اتخاذها نتيجة لمميزات الحماية من المخاطر في Microsoft 365 Defender.[](m365d-autoir.md) لمزيد من المعلومات حول إجراءات المعالجة التلقائية واليدوية، راجع [إجراءات المعالجة](m365d-remediation-actions.md).

## <a name="viewing-action-source-details"></a>عرض تفاصيل مصدر الإجراء

(**جديد!**) يتضمن مركز الإجراءات المحسن الآن عمود **مصدر** الإجراءات الذي يخبرك من أين يأتي كل إجراء. يصف الجدول التالي قيم **مصدر الإجراء** المحتملة:

| قيمة مصدر الإجراء | الوصف |
|:-----|:---|
| **إجراء الجهاز اليدوي** | إجراء يدوي تم اتخاذه على جهاز. تتضمن الأمثلة [عزل الجهاز](../defender-endpoint/respond-machine-alerts.md#isolate-devices-from-the-network) أو [عزل الملفات](../defender-endpoint/respond-file-alerts.md#stop-and-quarantine-files). |
| **إجراء البريد الإلكتروني اليدوي** | إجراء يدوي تم اتخاذه على البريد الإلكتروني. يتضمن المثال حذف رسائل البريد الإلكتروني تلقائيا أو [معالجة رسالة بريد إلكتروني](../office-365-security/remediate-malicious-email-delivered-office-365.md). |
| **إجراء الجهاز التلقائي** | إجراء تلقائي تم اتخاذه على كيان، مثل ملف أو عملية. تتضمن أمثلة الإجراءات التلقائية إرسال ملف إلى الفحص، وتوقف عملية، وإزالة مفتاح تسجيل. (راجع [إجراءات المعالجة في Microsoft Defender لنقطة النهاية](../defender-endpoint/manage-auto-investigation.md#remediation-actions).) |
| **إجراء البريد الإلكتروني التلقائي** | إجراء تلقائي تم اتخاذه على محتوى البريد الإلكتروني، مثل رسالة بريد إلكتروني أو مرفق أو عنوان URL. تتضمن أمثلة الإجراءات التلقائية حذف رسائل البريد الإلكتروني بشكل تلقائي وحظر عناوين URL، إيقاف تشغيل إعادة توجيه البريد الخارجي. (راجع [إجراءات المعالجة في Microsoft Defender لـ Office 365](../office-365-security/air-remediation-actions.md).) |
| **إجراء صيد متقدم** | الإجراءات التي تم اتخاذها على الأجهزة أو البريد الإلكتروني [باستخدام الصيد المتقدم](./advanced-hunting-overview.md). |
| **إجراء المستكشف** | الإجراءات التي تم اتخاذها على محتوى البريد الإلكتروني باستخدام [المستكشف](../office-365-security/threat-explorer.md). |
| **إجراء الاستجابة المباشرة اليدوية** | الإجراءات التي تم اتخاذها على جهاز مع [استجابة مباشرة](../defender-endpoint/live-response.md). تتضمن الأمثلة حذف ملف، إيقاف عملية، وإزالة مهمة مجدولة. |
| **إجراء الاستجابة المباشرة** | الإجراءات التي تم اتخاذها على جهاز باستخدام [Microsoft Defender لنقطة النهاية برمجة التطبيقات](../defender-endpoint/management-apis.md#microsoft-defender-for-endpoint-apis). تتضمن أمثلة الإجراءات عزل جهاز وتشغيل فحص برنامج الحماية من الفيروسات والحصول على معلومات حول ملف. |

## <a name="required-permissions-for-action-center-tasks"></a>الأذونات المطلوبة لمهام مركز الإجراءات

لتنفيذ مهام، مثل الموافقة على الإجراءات المعلقة أو رفضها في مركز الإجراءات، يجب أن يكون لديك الأذونات المعينة كما هو مذكور في الجدول التالي:

|إجراء المعالجة |الأدوار والأذونات المطلوبة |
|--|----|
|Microsoft Defender لنقطة النهاية الإصلاح (الأجهزة) |**دور مسؤول** الأمان المعين في Azure Active Directory (Azure AD) ([https://portal.azure.com](https://portal.azure.com)) أو مركز مسؤولي Microsoft 365 ([https://admin.microsoft.com](https://admin.microsoft.com))<br/>--- أو ---<br/>**دور إجراءات المعالجة النشطة** المعين في Microsoft Defender لنقطة النهاية <br/> <br/> لمعرفة المزيد، راجع الموارد التالية: <br/>- [أدوار Azure AD المضمنة](/azure/active-directory/roles/permissions-reference)<br/>- [إنشاء أدوار وإدارتها للتحكم بالوصول المستند إلى الدور (Microsoft Defender لنقطة النهاية)](../defender-endpoint/user-roles.md)  |
|Microsoft Defender لـ Office 365 الإصلاح (Office البريد الإلكتروني والمحتوى)  |**دور مسؤول** الأمان المعين في Azure AD ([https://portal.azure.com](https://portal.azure.com)) أو مركز مسؤولي Microsoft 365 ([https://admin.microsoft.com](https://admin.microsoft.com))<br/>--- --- <br/>**دور البحث و الازدحام** المعين في مركز & الأمان ([https://protection.office.com](https://protection.office.com)) <br/><br/>**هام**: إذا تم تعيين دور  مسؤول الأمان فقط في مركز التوافق Office 365 الأمان & ([https://protection.office.com](https://protection.office.com))، لن تتمكن من الوصول إلى مركز الإجراءات أو Microsoft 365 Defender الإمكانات. يجب تعيين دور **مسؤول الأمان** في Azure AD أو مركز مسؤولي Microsoft 365. <br/><br/>لمعرفة المزيد، راجع الموارد التالية: <br/>- [أدوار Azure AD المضمنة](/azure/active-directory/roles/permissions-reference)<br/>- [الأذونات في مركز & الأمان](/microsoft-365/security/office-365-security/permissions-in-the-security-and-compliance-center) |

> [!TIP]
> يمكن للمستخدمين **الذين تم تعيين** دور "المسؤول العام" في Azure AD الموافقة على أي إجراء معلق أو رفضه في مركز الإجراءات. ومع ذلك، يجب أن تقوم مؤسستك، كأفضل ممارسة، بحصر عدد الأشخاص الذين تم  تعيين دور "المسؤول العام" لديهم. نوصي **باستخدام مسؤول الأمان**، والإجراءات **الإصلاحية** النشطة، وأدوار البحث و  الازدحام المدرجة في الجدول السابق لأذونات مركز الإجراءات.

## <a name="next-step"></a>الخطوة التالية 

- [عرض إجراءات الإصلاح وإدارتها](m365d-autoir-actions.md)
