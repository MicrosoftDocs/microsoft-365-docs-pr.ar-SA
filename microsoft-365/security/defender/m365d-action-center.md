---
title: انتقل إلى مركز الصيانة لعرض مهام التحقيق والمعالجة التلقائية والموافقة عليها
description: استخدام مركز الصيانة لعرض تفاصيل حول التحقيق التلقائي والموافقة على الإجراءات المعلقة
keywords: مركز الصيانة، الحماية من التهديدات، التحقيق، التنبيه، معلق، مؤتمت، الكشف
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
ms.openlocfilehash: 631849997fffc0e4f90a9aa9d1850646b764a52a
ms.sourcegitcommit: d1b60ed9a11f5e6e35fbaf30ecaeb9dfd6dd197d
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 06/29/2022
ms.locfileid: "66493476"
---
# <a name="the-action-center"></a>مركز الصيانة

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**ينطبق على:**
- Microsoft 365 Defender

يوفر مركز الصيانة تجربة "جزء واحد من الزجاج" لمهام الحدث والتنبيه مثل:

- الموافقة على إجراءات المعالجة المعلقة.
- عرض سجل تدقيق لإجراءات المعالجة المعتمدة بالفعل.
- مراجعة إجراءات المعالجة المكتملة.

نظرا لأن مركز الصيانة يوفر عرضا شاملا Microsoft 365 Defender في العمل، يمكن لفريق عمليات الأمان لديك العمل بفعالية وكفاءة أكبر.

## <a name="the-unified-action-center"></a>مركز الصيانة الموحد

يسرد مركز الإجراءات الموحد ([https://security.microsoft.com/action-center](https://security.microsoft.com/action-center)) إجراءات المعالجة المعلقة والمكتملة لأجهزتك والبريد الإلكتروني & محتوى التعاون والهويات في موقع واحد.

:::image type="content" source="../../media/m3d-action-center-unified.png" alt-text="مركز الصيانة الموحد في مدخل Microsoft 365 Defender." lightbox="../../media/m3d-action-center-unified.png":::

على سبيل المثال: 

- إذا كنت تستخدم مسبقا Office 365 Security & Compliance Center ([https://protection.office.com](https://protection.office.com))، فجرب مركز الإجراءات الموحد في <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">مدخل Microsoft 365 Defender</a>.
- إذا كنت تستخدم مركز الصيانة في مركز حماية Microsoft Defender ([https://securitycenter.windows.com/action-center](https://securitycenter.windows.com/action-center))، فجرب مركز الإجراءات الموحد في <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">مدخل Microsoft 365 Defender</a>.
- إذا كنت تستخدم مدخل <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender</a> بالفعل، فسترى العديد من التحسينات في مركز الصيانة ([https://security.microsoft.com/action-center](https://security.microsoft.com/action-center)).

يجمع مركز الإجراءات الموحد بين إجراءات المعالجة عبر Defender لنقطة النهاية Defender لـ Office 365. وهو يحدد لغة مشتركة لجميع إجراءات المعالجة ويوفر تجربة تحقيق موحدة. يتمتع فريق عمليات الأمان لديك بتجربة "جزء واحد من الزجاج" لعرض إجراءات المعالجة وإدارتها.  

يمكنك استخدام مركز الصيانة الموحد إذا كان لديك الأذونات المناسبة واشتراك واحد أو أكثر من الاشتراكات التالية:

- [Defender لنقطة النهاية](../defender-endpoint/microsoft-defender-endpoint.md)
- [دليل إعداد Microsoft Defender لـ Office 365](/microsoft-365/security/office-365-security/defender-for-office-365)
- [Microsoft 365 Defender](microsoft-365-defender.md)

> [!TIP]
> لمعرفة المزيد، راجع [المتطلبات](./prerequisites.md).

## <a name="using-the-action-center"></a>استخدام مركز الصيانة

1. انتقل إلى <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">مدخل Microsoft 365 Defender</a> وسجل الدخول. 
2. في جزء التنقل، اختر **مركز الصيانة**. 

عند زيارة مركز الصيانة، سترى علامتي تبويب: **الإجراءات المعلقة** **والمحفوظات**. يلخص الجدول التالي ما ستراه في كل علامة تبويب:

|التبويب  |الوصف  |
|---------|---------|
|**المعلقه**     | عرض قائمة بالإجراءات التي تتطلب الانتباه. يمكنك الموافقة على الإجراءات أو رفضها كل على حدة، أو تحديد إجراءات متعددة إذا كان لها نفس نوع الإجراء (مثل ملف العزل). <p>**تلميح**: تأكد من مراجعة (أو رفض) الإجراءات المعلقة والموافقة عليها في أقرب وقت ممكن بحيث يمكن إكمال التحقيقات التلقائية في الوقت المناسب.       |
|**التاريخ**     | يعمل كسجل تدقيق للإجراءات التي تم اتخاذها، مثل: <br/>- إجراءات المعالجة التي تم اتخاذها نتيجة للتحقيقات التلقائية <br/>- إجراءات المعالجة التي تم اتخاذها على رسائل البريد الإلكتروني أو الملفات أو عناوين URL المشبوهة أو الضارة<br/>- إجراءات المعالجة التي وافق عليها فريق عمليات الأمان <br/>- الأوامر التي تم تشغيلها وإجراءات المعالجة التي تم تطبيقها أثناء جلسات الاستجابة المباشرة<br/>- إجراءات المعالجة التي تم اتخاذها بواسطة الحماية من الفيروسات <p>يوفر طريقة للتراجع عن إجراءات معينة (راجع [التراجع عن الإجراءات المكتملة](m365d-autoir-actions.md#undo-completed-actions)).        |

يمكنك تخصيص البيانات وفرزها وتصفيتها وتصديرها في مركز الصيانة.

:::image type="content" source="../../media/m3d-action-center-columnsfilters.png" alt-text="إمكانيات فرز مركز الصيانة وتصفيتها وتخصيصها" lightbox="../../media/m3d-action-center-columnsfilters.png":::

- حدد عنوان عمود لفرز العناصر بترتيب تصاعدي أو تنازلي.
- استخدم عامل تصفية الفترة الزمنية لعرض بيانات اليوم أو الأسبوع أو 30 يوما أو 6 أشهر الماضية.
- اختر الأعمدة التي تريد عرضها.
- حدد عدد العناصر المراد تضمينها في كل صفحة من البيانات.
- استخدم عوامل التصفية لعرض العناصر التي تريد رؤيتها فقط.
- حدد **"تصدير** " لتصدير النتائج إلى ملف .csv.

## <a name="actions-tracked-in-the-action-center"></a>الإجراءات المتعقبة في مركز الصيانة

يتم تعقب جميع الإجراءات، سواء كانت معلقة للموافقة أو تم اتخاذها بالفعل، في مركز الصيانة. تتضمن الإجراءات المتوفرة ما يلي:

- تجميع حزمة التحقيق 
- عزل الجهاز (يمكن التراجع عن هذا الإجراء) 
- جهاز إيقاف التجهيز 
- تنفيذ التعليمات البرمجية للإصدار 
- تحرير من العزل 
- نموذج الطلب 
- تقييد تنفيذ التعليمات البرمجية (يمكن التراجع عن هذا الإجراء) 
- تشغيل مسح الحماية من الفيروسات 
- الإيقاف والعزل 
- عزل الأجهزة من الشبكة

بالإضافة إلى إجراءات المعالجة التي يتم اتخاذها تلقائيا نتيجة [للتحقيقات التلقائية](m365d-autoir.md)، يتعقب مركز الإجراءات أيضا الإجراءات التي اتخذها فريق الأمان لمعالجة التهديدات المكتشفة، والإجراءات التي تم اتخاذها نتيجة لميزات الحماية من التهديدات في Microsoft 365 Defender. لمزيد من المعلومات حول إجراءات المعالجة التلقائية واليدوية، راجع [إجراءات المعالجة](m365d-remediation-actions.md).

## <a name="viewing-action-source-details"></a>عرض تفاصيل مصدر الإجراء

(**جديد!**) يتضمن مركز الصيانة المحسن الآن عمود **مصدر الإجراء** الذي يخبرك من أين جاء كل إجراء. يصف الجدول التالي قيم **مصدر الإجراء** المحتملة:

| قيمة مصدر الإجراء | الوصف |
|:-----|:---|
| **إجراء الجهاز اليدوي** | إجراء يدوي تم اتخاذه على جهاز. وتشمل الأمثلة [عزل الجهاز](../defender-endpoint/respond-machine-alerts.md#isolate-devices-from-the-network) أو [عزل الملفات](../defender-endpoint/respond-file-alerts.md#stop-and-quarantine-files). |
| **إجراء البريد الإلكتروني اليدوي** | إجراء يدوي تم اتخاذه على البريد الإلكتروني. يتضمن المثال حذف رسائل البريد الإلكتروني مبدئيا أو [معالجة رسالة بريد إلكتروني](../office-365-security/remediate-malicious-email-delivered-office-365.md). |
| **إجراء الجهاز التلقائي** | إجراء تلقائي تم اتخاذه على كيان، مثل ملف أو عملية. تتضمن أمثلة الإجراءات التلقائية إرسال ملف إلى العزل وإيقاف عملية وإزالة مفتاح التسجيل. (راجع [إجراءات المعالجة في Microsoft Defender لنقطة النهاية](../defender-endpoint/manage-auto-investigation.md#remediation-actions).) |
| **إجراء البريد الإلكتروني التلقائي** | إجراء تلقائي تم اتخاذه على محتوى البريد الإلكتروني، مثل رسالة بريد إلكتروني أو مرفق أو عنوان URL. تتضمن أمثلة الإجراءات التلقائية حذف رسائل البريد الإلكتروني مبدئيا، وحظر عناوين URL، وإيقاف تشغيل إعادة توجيه البريد الخارجي. (راجع [إجراءات المعالجة في Microsoft Defender لـ Office 365](../office-365-security/air-remediation-actions.md).) |
| **إجراء التتبع المتقدم** | الإجراءات التي يتم اتخاذها على الأجهزة أو البريد الإلكتروني مع [التتبع المتقدم](./advanced-hunting-overview.md). |
| **إجراء المستكشف** | الإجراءات التي تم اتخاذها على محتوى البريد الإلكتروني باستخدام [Explorer](../office-365-security/threat-explorer.md). |
| **إجراء الاستجابة المباشرة اليدوي** | الإجراءات التي تم اتخاذها على جهاز مع [استجابة مباشرة](../defender-endpoint/live-response.md). تتضمن الأمثلة حذف ملف وإيقاف عملية وإزالة مهمة مجدولة. |
| **إجراء الاستجابة المباشرة** | الإجراءات التي تم اتخاذها على جهاز مع [واجهات برمجة التطبيقات Microsoft Defender لنقطة النهاية](../defender-endpoint/management-apis.md#microsoft-defender-for-endpoint-apis). تتضمن أمثلة الإجراءات عزل جهاز، وتشغيل فحص مكافحة الفيروسات، والحصول على معلومات حول ملف. |

## <a name="required-permissions-for-action-center-tasks"></a>الأذونات المطلوبة لمهام مركز الصيانة

لتنفيذ المهام، مثل الموافقة على الإجراءات المعلقة أو رفضها في مركز الإجراءات، يجب أن يكون لديك أذونات معينة كما هو مذكور في الجدول التالي:

|إجراء المعالجة |الأدوار والأذونات المطلوبة |
|--|----|
|Microsoft Defender لنقطة النهاية المعالجة (الأجهزة) |دور **مسؤول الأمان** المعين في Azure Active Directory (Azure AD) ([https://portal.azure.com](https://portal.azure.com)) أو مركز مسؤولي Microsoft 365 ([https://admin.microsoft.com](https://admin.microsoft.com))<br/>--- أو ---<br/>دور **إجراءات المعالجة النشطة** المعين في Microsoft Defender لنقطة النهاية <br/> <br/> لمعرفة المزيد، راجع الموارد التالية: <br/>- [Azure AD الأدوار المضمنة](/azure/active-directory/roles/permissions-reference)<br/>- [إنشاء أدوار للتحكم في الوصول استنادا إلى الدور وإدارتها (Microsoft Defender لنقطة النهاية)](../defender-endpoint/user-roles.md)  |
|Microsoft Defender لـ Office 365 المعالجة (محتوى Office والبريد الإلكتروني)  |دور **مسؤول الأمان** المعين في Azure AD ([https://portal.azure.com](https://portal.azure.com)) أو مركز مسؤولي Microsoft 365 ([https://admin.microsoft.com](https://admin.microsoft.com))<br/>--- --- <br/>دور **البحث والإزالة** المعين في مركز توافق & الأمان ([https://protection.office.com](https://protection.office.com)) <br/><br/>**هام**: إذا تم تعيين دور **مسؤول الأمان** فقط في مركز التوافق & الأمان Office 365 ([https://protection.office.com](https://protection.office.com))، فلن تتمكن من الوصول إلى مركز الصيانة أو قدرات Microsoft 365 Defender. يجب تعيين دور **مسؤول الأمان** في Azure AD أو مركز مسؤولي Microsoft 365. <br/><br/>لمعرفة المزيد، راجع الموارد التالية: <br/>- [Azure AD الأدوار المضمنة](/azure/active-directory/roles/permissions-reference)<br/>- [الأذونات في مركز توافق & الأمان](/microsoft-365/security/office-365-security/permissions-in-the-security-and-compliance-center) |

> [!TIP]
> يمكن للمستخدمين الذين لديهم دور **المسؤول العام** المعين في Azure AD الموافقة على أي إجراء معلق أو رفضه في مركز الإجراءات. ومع ذلك، كأفضل ممارسة، يجب على مؤسستك تحديد عدد الأشخاص الذين تم تعيين دور **المسؤول العام** لهم. نوصي باستخدام **مسؤول الأمان** **وإجراءات المعالجة النشطة** وأدوار **البحث والإزالة** المدرجة في الجدول السابق لأذونات مركز الصيانة.

## <a name="next-step"></a>الخطوة التالية 

- [عرض إجراءات الإصلاح وإدارتها](m365d-autoir-actions.md)
