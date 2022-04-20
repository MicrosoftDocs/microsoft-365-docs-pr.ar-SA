---
title: تكوين قدرات التحقيق والاستجابة التلقائية في Microsoft 365 Defender
description: تكوين التحقيق التلقائي والاستجابة مع الإصلاح الذاتي في Microsoft 365 Defender
search.appverid: MET150
ms.author: dansimp
author: dansimp
manager: dansimp
audience: ITPro
ms.topic: how-to
ms.prod: m365-security
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
ms.custom:
- autoir
- admindeeplinkDEFENDER
ms.reviewer: evaldm, isco
f1.keywords: CSH
ms.technology: m365d
ms.openlocfilehash: 51efeb57c6670f9c798fa254bb0a6242b30c5700
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/19/2022
ms.locfileid: "64944360"
---
# <a name="configure-automated-investigation-and-response-capabilities-in-microsoft-365-defender"></a>تكوين قدرات التحقيق والاستجابة التلقائية في Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

تتضمن Microsoft 365 Defender [قدرات فعالة للتحقيق والاستجابة التلقائية](m365d-autoir.md) التي يمكن أن توفر لفريق عمليات الأمان الكثير من الوقت والجهد. مع [الإصلاح الذاتي](m365d-autoir.md#how-automated-investigation-and-self-healing-works)، تحاكي هذه القدرات الخطوات التي سيتخذها محلل الأمان للتحقيق في التهديدات والاستجابة لها، بشكل أسرع فقط، وبقدرة أكبر على التوسع.

تصف هذه المقالة كيفية تكوين التحقيق التلقائي والاستجابة في <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender</a> مع الخطوات التالية:

1. [راجع المتطلبات الأساسية](#prerequisites-for-automated-investigation-and-response-in-microsoft-365-defender).
2. [مراجعة مستوى التشغيل التلقائي لمجموعات الأجهزة أو تغييره](#review-or-change-the-automation-level-for-device-groups).
3. [راجع نهج الأمان والتنبيه في Office 365](#review-your-security-and-alert-policies-in-office-365).
4. [تأكد من تشغيل Microsoft 365 Defender](#make-sure-microsoft-365-defender-is-turned-on).

بعد ذلك، بعد إعداد كل شيء، يمكنك [عرض إجراءات المعالجة وإدارتها في مركز الصيانة](m365d-autoir-actions.md).

## <a name="prerequisites-for-automated-investigation-and-response-in-microsoft-365-defender"></a>المتطلبات الأساسية للتحقيق التلقائي والاستجابة في Microsoft 365 Defender

<br>

****

|شرط|التفاصيل|
|---|---|
|متطلبات الاشتراك|أحد هذه الاشتراكات: <ul><li>Microsoft 365 E5</li><li>Microsoft 365 A5</li><li>Microsoft 365 E3 مع الوظيفة الإضافية الأمان في Microsoft 365 E5</li><li>Microsoft 365 A3 مع الوظيفة الإضافية Microsoft 365 A5 Security</li><li>Office 365 E5 بالإضافة إلى Enterprise Mobility + Security E5 بالإضافة إلى Windows E5</li></ul> <p> راجع [متطلبات الترخيص Microsoft 365 Defender](./prerequisites.md#licensing-requirements).|
|متطلبات الشبكة|<ul><li>[تمكين Microsoft Defender for Identity](/azure-advanced-threat-protection/what-is-atp)</li><li>[تم تكوين Microsoft Defender for Cloud Apps](/cloud-app-security/what-is-cloud-app-security)</li><li>[تكامل Microsoft Defender for Identity](/cloud-app-security/mdi-integration)</li></ul>|
|متطلبات جهاز Windows|<ul><li>Windows 11</li><li>Windows 10 أو الإصدار 1709 أو إصدار أحدث مثبت (راجع [معلومات إصدار Windows](/windows/release-information/))</li><li>تم تكوين خدمات الحماية من التهديدات التالية:<ul><li>[مشكلات الأداء في Microsoft Defender لنقطة النهاية](../defender-endpoint/configure-endpoints.md)</li><li>[برنامج الحماية من الفيروسات من Microsoft Defender](/windows/security/threat-protection/windows-defender-antivirus/configure-windows-defender-antivirus-features)</li></ul></li></ul>|
|حماية محتوى البريد الإلكتروني وملفات Office|[تم تكوين Microsoft Defender لـ Office 365](/microsoft-365/security/office-365-security/defender-for-office-365#configure-atp-policies)|
|الأذونات|لتكوين قدرات التحقيق والاستجابة التلقائية، يجب تعيين دور المسؤول العام أو مسؤول الأمان في Azure Active Directory (<https://portal.azure.com>) أو في مركز مسؤولي Microsoft 365 (<https://admin.microsoft.com>). <p> للحصول على الأذونات اللازمة للعمل مع قدرات التحقيق والاستجابة التلقائية، مثل مراجعة الإجراءات المعلقة أو الموافقة عليها أو رفضها، راجع [الأذونات المطلوبة لمهام مركز الصيانة](m365d-action-center.md#required-permissions-for-action-center-tasks).|
|

## <a name="review-or-change-the-automation-level-for-device-groups"></a>مراجعة مستوى التشغيل التلقائي لمجموعات الأجهزة أو تغييره

يعتمد تشغيل التحقيقات التلقائية، وما إذا كانت إجراءات المعالجة يتم اتخاذها تلقائيا أو فقط عند الموافقة على أجهزتك على إعدادات معينة، مثل نهج مجموعة الأجهزة الخاصة بمؤسستك. راجع مستوى التشغيل التلقائي الذي تم تكوينه لنهج مجموعة الأجهزة.

1. انتقل إلى مدخل Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)) وسجل الدخول.

2. انتقل إلى **مجموعات الإعدادات** >  **EndpointsDevice** >  ضمن **الأذونات**.

3. راجع نهج مجموعة أجهزتك. على وجه الخصوص، انظر إلى عمود **مستوى التنفيذ التلقائي** . نوصي باستخدام **Full - معالجة التهديدات تلقائيا**.  قد تحتاج إلى إنشاء مجموعات أجهزتك أو تحريرها للحصول على مستوى التشغيل التلقائي الذي تريده. للحصول على تعليمات حول هذه المهمة، راجع المقالات التالية:
   - [كيفية معالجة التهديدات](/windows/security/threat-protection/microsoft-defender-atp/automated-investigations#how-threats-are-remediated)
   - [إنشاء مجموعات الأجهزة وإدارتها](/windows/security/threat-protection/microsoft-defender-atp/machine-groups)

## <a name="review-your-security-and-alert-policies-in-office-365"></a>راجع نهج الأمان والتنبيه في Office 365

توفر Microsoft [نهج تنبيه](../../compliance/alert-policies.md) مضمنة تساعد في تحديد مخاطر معينة. وتشمل هذه المخاطر Exchange إساءة استخدام أذونات المسؤول، ونشاط البرامج الضارة، والتهديدات الخارجية والداخلية المحتملة، ومخاطر إدارة المعلومات. يمكن أن تؤدي بعض التنبيهات إلى [التحقيق التلقائي والاستجابة في Office 365](../office-365-security/office-365-air.md). تأكد من تكوين ميزات [Defender لـ Office 365](../office-365-security/defender-for-office-365.md) بشكل صحيح.

على الرغم من أن بعض التنبيهات وسياسات الأمان يمكن أن تؤدي إلى تحقيقات تلقائية، *لا يتم اتخاذ أي إجراءات معالجة تلقائيا للبريد الإلكتروني والمحتوى*. بدلا من ذلك، تنتظر جميع إجراءات المعالجة لمحتوى البريد الإلكتروني والبريد الإلكتروني موافقة فريق عمليات الأمان في [مركز الصيانة](m365d-action-center.md).

تساعد إعدادات الأمان في Office 365 على حماية البريد الإلكتروني والمحتوى. لعرض هذه الإعدادات أو تغييرها، اتبع الإرشادات الواردة في [الحماية من التهديدات](../office-365-security/protect-against-threats.md).

1. في <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">مدخل Microsoft 365 Defender</a>، انتقل إلى **نهج & نهج المخاطر للقواعد**\>.

2. تأكد من تكوين كافة النهج التالية. للحصول على التعليمات والتوصيات، راجع [الحماية من التهديدات](/microsoft-365/security/office-365-security/protect-against-threats).
   - [مكافحة البرامج الضارة](../office-365-security/protect-against-threats.md#part-1---anti-malware-protection-in-eop)
   - [مكافحة التصيد الاحتيالي](../office-365-security/protect-against-threats.md#part-2---anti-phishing-protection-in-eop-and-defender-for-office-365)
   - [مرفقات آمنة](../office-365-security/protect-against-threats.md#safe-attachments-policies-in-microsoft-defender-for-office-365)
   - [الارتباطات الآمنة](../office-365-security/protect-against-threats.md#safe-links-policies-in-microsoft-defender-for-office-365)
   - [مكافحة البريد العشوائي](../office-365-security/protect-against-threats.md#part-3---anti-spam-protection-in-eop)

3. تأكد من تشغيل [خزينة المرفقات SharePoint OneDrive Microsoft Teams](../office-365-security/mdo-for-spo-odb-and-teams.md).

4. تأكد من أن [الإزالة التلقائية لمدة صفر ساعة (ZAP) في Exchange Online](../office-365-security/zero-hour-auto-purge.md) سارية المفعول.

5. (هذه الخطوة اختيارية.) راجع [نهج التنبيه Office 365](../../compliance/alert-policies.md) في مدخل الامتثال ل Microsoft Purview ([https://compliance.microsoft.com/compliancepolicies](https://compliance.microsoft.com/compliancepolicies)). توجد العديد من نهج التنبيه الافتراضية في فئة إدارة المخاطر. يمكن أن تؤدي بعض هذه التنبيهات إلى التحقيق التلقائي والاستجابة. لمعرفة المزيد، راجع [نهج التنبيه الافتراضية](../../compliance/alert-policies.md#default-alert-policies).

## <a name="make-sure-microsoft-365-defender-is-turned-on"></a>تأكد من تشغيل Microsoft 365 Defender

:::image type="content" source="../../media/mtp-enable/mtp-on.png" alt-text="جزء التنقل الأيمن في مدخل Microsoft 365 Defender عند تشغيل Microsoft 365 Defender" lightbox="../../media/mtp-enable/mtp-on.png":::

1. تسجيل الدخول إلى مدخل <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender</a>

2. في جزء التنقل، ابحث عن **Incidents & Alerts** **وSing** و **Action center** كما هو موضح في الصورة السابقة.
   - إذا رأيت **Incidents & Alerts** **وS hunting** و **Action center**، Microsoft 365 Defender قيد التشغيل. راجع [قسم مراجعة مستوى التنفيذ التلقائي لمجموعات الأجهزة أو تغييره](#review-or-change-the-automation-level-for-device-groups) في هذه المقالة.
   - إذا *لم* تتمكن من رؤية **الحوادث** أو **مركز الصيانة** أو **التتبع**، فقد لا يتم تشغيل Microsoft 365 Defender. في هذه [الحالة، قم بزيارة مركز الصيانة](m365d-action-center.md).

> [!TIP]
> هل تحتاج إلى مساعدة؟ راجع [تشغيل Microsoft 365 Defender](m365d-enable.md).

## <a name="next-steps"></a>الخطوات التالية

- [إجراءات المعالجة في Microsoft 365 Defender](m365d-remediation-actions.md)
- [زيارة مركز الصيانة](m365d-action-center.md)
