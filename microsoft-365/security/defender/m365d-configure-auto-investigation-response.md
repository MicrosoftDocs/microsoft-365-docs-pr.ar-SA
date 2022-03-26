---
title: تكوين قدرات الاستجابة والتحري التلقائي في Microsoft 365 Defender
description: تكوين التحقيق والاستجابة التلقائية باستخدام الاختبار الذاتي في Microsoft 365 Defender
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
ms.openlocfilehash: 4ec06a96e345345560a2714fa7e23d91a6f5832f
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/08/2022
ms.locfileid: "63570192"
---
# <a name="configure-automated-investigation-and-response-capabilities-in-microsoft-365-defender"></a>تكوين قدرات الاستجابة والتحري التلقائي في Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

Microsoft 365 Defender إمكانات الاستجابة والتحري التلقائي [القوية](m365d-autoir.md) التي يمكن أن توفر لفريق عمليات الأمان الكثير من الوقت والجهد. باستخدام [القدرة على](m365d-autoir.md#how-automated-investigation-and-self-healing-works) معالجة المخاطر ذاتيا، تحاكي هذه الإمكانات الخطوات التي سيتخذها محلل الأمان للتحقق من التهديدات والاستجابة لها، بسرعة أكبر، وبقدرة أكبر على المقياس.

تصف هذه المقالة كيفية تكوين الاستجابات والتحريات التلقائية في <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender الخطوات التالية</a>:

1. [راجع المتطلبات الأساسية](#prerequisites-for-automated-investigation-and-response-in-microsoft-365-defender).
2. [مراجعة مستوى التنفيذ التلقائي لمجموعات الأجهزة أو تغييره](#review-or-change-the-automation-level-for-device-groups).
3. [راجع سياسات الأمان والتنبيه في Office 365](#review-your-security-and-alert-policies-in-office-365).
4. [تأكد من Microsoft 365 Defender تشغيلها](#make-sure-microsoft-365-defender-is-turned-on).

بعد ذلك، بعد إعداد كل الإجراءات، يمكنك عرض إجراءات المعالجة وإدارتها [في مركز الإجراءات](m365d-autoir-actions.md).

## <a name="prerequisites-for-automated-investigation-and-response-in-microsoft-365-defender"></a>المتطلبات الأساسية للتحري التلقائي والاستجابة في Microsoft 365 Defender

<br>

****

|المتطلب|التفاصيل|
|---|---|
|متطلبات الاشتراك|أحد هذه الاشتراكات: <ul><li>Microsoft 365 E5</li><li>Microsoft 365 A5</li><li>Microsoft 365 E3 باستخدام الأمان في Microsoft 365 E5 الإضافية</li><li>Microsoft 365 A3 باستخدام Microsoft 365 A5 Security الإضافية</li><li>Office 365 E5 بالإضافة إلى Enterprise Mobility + Security E5 بالإضافة إلى Windows E5</li></ul> <p> راجع [Microsoft 365 Defender متطلبات الترخيص](./prerequisites.md#licensing-requirements).|
|متطلبات الشبكة|<ul><li>[تمكين Microsoft Defender for Identity](/azure-advanced-threat-protection/what-is-atp)</li><li>[تم تكوين Microsoft Defender for Cloud Apps](/cloud-app-security/what-is-cloud-app-security)</li><li>[تكامل Microsoft Defender for Identity](/cloud-app-security/mdi-integration)</li></ul>|
|Windows الأجهزة|<ul><li>Windows 11</li><li>Windows 10 الإصدار 1709 أو الإصدار الأحدث المثبت ([راجع Windows الإصدار](/windows/release-information/))</li><li>تم تكوين خدمات الحماية من المخاطر التالية:<ul><li>[Microsoft Defender لنقطة النهاية](../defender-endpoint/configure-endpoints.md)</li><li>[برنامج الحماية من الفيروسات من Microsoft Defender](/windows/security/threat-protection/windows-defender-antivirus/configure-windows-defender-antivirus-features)</li></ul></li></ul>|
|الحماية لمحتوى البريد الإلكتروني Office الملفات|[Microsoft Defender Office 365](/microsoft-365/security/office-365-security/defender-for-office-365#configure-atp-policies) تكوين|
|الأذونات|لتكوين قدرات الاستجابة والتحري التلقائي، يجب تعيين دور المسؤول العام أو مسؤول الأمان في Azure Active Directory (<https://portal.azure.com>) أو في مركز مسؤولي Microsoft 365 (<https://admin.microsoft.com>). <p> للحصول على الأذونات اللازمة للعمل باستخدام إمكانات الاستجابة والتحريات التلقائية، مثل مراجعة الإجراءات المعلقة أو الموافقة عليها أو رفضها، راجع الأذونات المطلوبة لمهام [مركز الإجراءات](m365d-action-center.md#required-permissions-for-action-center-tasks).|
|

## <a name="review-or-change-the-automation-level-for-device-groups"></a>مراجعة مستوى التنفيذ التلقائي لمجموعات الأجهزة أو تغييره

تعتمد عمليات الإصلاح التلقائية التي يتم تشغيلها وما إذا كانت إجراءات المعالجة يتم اتخاذها تلقائيا أو عند الموافقة على أجهزتك فقط على إعدادات معينة، مثل سياسات مجموعة الأجهزة في مؤسستك. راجع مستوى التنفيذ التلقائي الذي تم تكوينه لنهج مجموعة الأجهزة.

1. انتقل إلى Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)) ثم سجل الدخول.

2. انتقل **إلى الإعدادات** >  **EndpointsDevice** >  **ضمن** **أذونات**.

3. راجع سياسات مجموعة الأجهزة. بشكل خاص، انظر إلى العمود **مستوى التنفيذ** التلقائي. نوصي باستخدام **التهديدات الكاملة - المعالجة تلقائيا**.  قد تحتاج إلى إنشاء مجموعات الأجهزة أو تحريرها للحصول على مستوى التنفيذ التلقائي الذي تريده. للحصول على تعليمات حول هذه المهمة، راجع المقالات التالية:
   - [كيفية معالجة التهديدات](/windows/security/threat-protection/microsoft-defender-atp/automated-investigations#how-threats-are-remediated)
   - [إنشاء مجموعات الأجهزة وإدارتها](/windows/security/threat-protection/microsoft-defender-atp/machine-groups)

## <a name="review-your-security-and-alert-policies-in-office-365"></a>راجع سياسات الأمان والتنبيه في Office 365

توفر Microsoft سياسات تنبيه [مضمنة](../../compliance/alert-policies.md) تساعد على تحديد مخاطر معينة. وتتضمن هذه المخاطر Exchange إساءة استخدام أذونات المسؤول، ونشاط البرامج الضارة، والمخاطر الخارجية والداخلية المحتملة، ومخاطر إدارة المعلومات. يمكن أن تؤدي بعض التنبيهات إلى [تشغيل التحقيق التلقائي والاستجابة في Office 365](../office-365-security/office-365-air.md). تأكد من تكوين [ميزات defender Office 365](../office-365-security/defender-for-office-365.md) بشكل صحيح.

على الرغم من أن بعض التنبيهات ونهج الأمان يمكن أن تؤدي إلى تشغيل عمليات تحقيق تلقائية، إلا أنه لا يتم اتخاذ أي إجراءات إصلاح تلقائيا *للبريد الإلكتروني والمحتوى*. بدلا من ذلك، تنتظر كل إجراءات المعالجة للبريد الإلكتروني ومحتوى البريد الإلكتروني موافقة فريق عمليات الأمان في [مركز الإجراءات](m365d-action-center.md).

تساعد إعدادات الأمان في Office 365 على حماية البريد الإلكتروني والمحتوى. لعرض هذه الإعدادات أو تغييرها، اتبع الإرشادات في [الحماية من التهديدات](../office-365-security/protect-against-threats.md).

1. في Microsoft 365 Defender <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">،</a> انتقل إلى سياسات & **القواعد** \> **.**

2. تأكد من تكوين كل السياسات التالية. للحصول على تعليمات وتوصيات، راجع [الحماية من التهديدات](/microsoft-365/security/office-365-security/protect-against-threats).
   - [مكافحة البرامج الضارة](../office-365-security/protect-against-threats.md#part-1---anti-malware-protection-in-eop)
   - [مكافحة التصيد الاحتيالي](../office-365-security/protect-against-threats.md#part-2---anti-phishing-protection-in-eop-and-defender-for-office-365)
   - [خزينة المرفقات](../office-365-security/protect-against-threats.md#safe-attachments-policies-in-microsoft-defender-for-office-365)
   - [الارتباطات الآمنة](../office-365-security/protect-against-threats.md#safe-links-policies-in-microsoft-defender-for-office-365)
   - [مكافحة البريد العشوائي](../office-365-security/protect-against-threats.md#part-3---anti-spam-protection-in-eop)

3. تأكد من [خزينة المرفقات](../office-365-security/mdo-for-spo-odb-and-teams.md) SharePoint OneDrive Microsoft Teams تشغيلها.

4. تأكد من [أن إزالة تلقائية لمدة ساعة صفرية (ZAP) في](../office-365-security/zero-hour-auto-purge.md) Exchange Online تكون في وضع التنفيذ.

5. (هذه الخطوة اختيارية.) راجع Office 365 [التنبيهات في](../../compliance/alert-policies.md) مركز التوافق في Microsoft 365 ([https://compliance.microsoft.com/compliancepolicies](https://compliance.microsoft.com/compliancepolicies)). توجد عدة سياسات تنبيه افتراضية في فئة إدارة المخاطر. يمكن أن تؤدي بعض هذه التنبيهات إلى تشغيل الاستجابة والتحري التلقائي. لمعرفة المزيد، راجع [سياسات التنبيه الافتراضية](../../compliance/alert-policies.md#default-alert-policies).

## <a name="make-sure-microsoft-365-defender-is-turned-on"></a>تأكد من Microsoft 365 Defender تشغيل

:::image type="content" source="../../media/mtp-enable/mtp-on.png" alt-text="كيفية التأكد من تمكين Microsoft 365 Defender." lightbox="../../media/mtp-enable/mtp-on.png":::

1. تسجيل <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">الدخول إلى مدخل</a> Microsoft 365 Defender

2. في جزء التنقل، ابحث عن & والتنبيهات والصيد ومركز الإجراءات كما هو موضح في الصورة  السابقة.
   - إذا رأيت أحداث **& التنبيهات** والصيد ومركز الإجراءات، Microsoft 365 Defender تشغيل. راجع القسم [مراجعة مستوى التنفيذ التلقائي لمجموعات الأجهزة](#review-or-change-the-automation-level-for-device-groups) أو تغييره في هذه المقالة.
   - إذا لم تشاهد *الأحداث* أو مركز **الإجراءات** أو البحث **عن** Microsoft 365 Defender، فقد لا يكون قد تم تشغيل. في هذه الحالة، [تفضل بزيارة مركز الإجراءات](m365d-action-center.md).

> [!TIP]
> هل تحتاج إلى مساعدة؟ راجع [تشغيل Microsoft 365 Defender](m365d-enable.md).

## <a name="next-steps"></a>الخطوات التالية

- [إجراءات المعالجة في Microsoft 365 Defender](m365d-remediation-actions.md)
- [زيارة مركز الإجراءات](m365d-action-center.md)
