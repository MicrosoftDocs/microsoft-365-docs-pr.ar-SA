---
title: تكامل خادم SIEM مع خدمات وتطبيقات Microsoft 365
f1.keywords:
- NOCSH
ms.author: deniseb
author: denisebmsft
manager: dansimp
audience: ITPro
ms.topic: article
ms.date: 11/18/2019
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
ms.custom:
- Ent_Solutions
- SIEM
- seo-marvel-apr2020
description: احصل على نظرة عامة حول تكامل خادم إدارة معلومات الأمان والأحداث (SIEM) مع خدمات السحابة والتطبيقات Microsoft 365
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: ffb457a378539691627eff3ad24b24ef782705c1
ms.sourcegitcommit: 6c2ab5e8efe74d0dc2df610e2d9d2fdda8aaf074
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 05/25/2022
ms.locfileid: "65670191"
---
# <a name="security-information-and-event-management-siem-server-integration-with-microsoft-365-services-and-applications"></a>تكامل خادم إدارة معلومات الأمان والأحداث (SIEM) مع خدمات وتطبيقات Microsoft 365

**ينطبق على**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [خطة 1 وخطة 2 من Microsoft Defender لـ Office 365](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

## <a name="summary"></a>الملخص

هل تستخدم مؤسستك خادم إدارة معلومات الأمان والأحداث (SIEM) أو تخطط للحصول عليه؟ قد تتساءل عن كيفية تكاملها مع Microsoft 365 أو Office 365. توفر هذه المقالة قائمة بالموارد التي يمكنك استخدامها لدمج خادم SIEM مع خدمات وتطبيقات Microsoft 365.

> [!TIP]
> إذا لم يكن لديك خادم SIEM حتى الآن وتستكشف خياراتك، ففكر في **[Microsoft Sentinel](/azure/sentinel/overview)**.

## <a name="do-i-need-a-siem-server"></a>هل أحتاج إلى خادم SIEM؟

يعتمد ما إذا كنت بحاجة إلى خادم SIEM على العديد من العوامل، مثل متطلبات الأمان لمؤسستك ومكان وجود بياناتك. يتضمن Microsoft 365 مجموعة متنوعة من ميزات الأمان التي تلبي احتياجات الأمان للعديد من المؤسسات دون خوادم إضافية، مثل خادم SIEM. بعض المؤسسات لديها ظروف خاصة تتطلب استخدام خادم SIEM. فيما يلي بعض الأمثلة:

- لدى *شركة Fabrikam* بعض المحتويات والتطبيقات في أماكن العمل، وبعضها في السحابة (لديها نشر سحابي مختلط). للحصول على تقارير الأمان عبر جميع محتوياتها وتطبيقاتها، قامت شركة Fabrikam بتنفيذ خادم SIEM.
- *Contoso* هي مؤسسة خدمات مالية لديها متطلبات أمنية صارمة بشكل خاص. لقد أضافوا خادم SIEM إلى بيئتهم للاستفادة من الحماية الأمنية الإضافية التي يحتاجونها.

## <a name="siem-server-integration-with-microsoft-365"></a>تكامل خادم SIEM مع Microsoft 365

يمكن أن يتلقى خادم SIEM بيانات من مجموعة متنوعة من خدمات وتطبيقات Microsoft 365. يسرد الجدول التالي العديد من خدمات وتطبيقات Microsoft 365، إلى جانب مدخلات خادم SIEM وموارده لمعرفة المزيد.

<br/><br/>

|خدمة Microsoft 365 أو تطبيق|مدخلات/أساليب خادم SIEM|الموارد لمعرفة المزيد|
|---|---|---|
|[Microsoft Defender لـ Office 365](defender-for-office-365.md)|سجلات التدقيق|[تكامل SIEM مع Microsoft Defender لـ Office 365](siem-integration-with-office-365-ti.md)|
|[مشكلات الأداء في Microsoft Defender لنقطة النهاية](/windows/security/threat-protection/)|نقطة نهاية HTTPS المستضافة في Azure <p> واجهة برمجة تطبيقات REST|[سحب التنبيهات إلى أدوات SIEM](../defender-endpoint/configure-siem.md)|
|[Microsoft Defender for Cloud Apps](/cloud-app-security/what-is-cloud-app-security)|تكامل السجل|[تكامل SIEM مع Microsoft Defender for Cloud Apps](/cloud-app-security/siem)|

> [!TIP]
> ألق نظرة على [Microsoft Sentinel](/azure/sentinel/overview). يأتي Microsoft Sentinel مزودا بموصلات لحلول Microsoft. تتوفر هذه الموصلات "خارج الصندوق" وتوفر التكامل في الوقت الحقيقي. يمكنك استخدام Microsoft Sentinel مع حلول Microsoft 365 Defender وخدمات Microsoft 365، بما في ذلك Office 365، Azure AD، Microsoft Defender for Identity، Microsoft Defender for Cloud Apps والمزيد.

### <a name="audit-logging-must-be-turned-on"></a>يجب تشغيل تسجيل التدقيق

تأكد من تشغيل تسجيل التدقيق قبل تكوين تكامل خادم SIEM.

- للحصول على SharePoint Online و OneDrive for Business وAzure Active Directory، راجع [تشغيل التدقيق أو إيقاف تشغيله](../../compliance/turn-audit-log-search-on-or-off.md).
- للحصول على Exchange Online، راجع [إدارة تدقيق علبة البريد](../../compliance/enable-mailbox-auditing.md).

## <a name="integration-steps-if-your-siem-is-microsoft-sentinel"></a>خطوات التكامل إذا كان SIEM الخاص بك هو Microsoft Sentinel

تأكد من أن خطتك الحالية تسمح بتكامل Microsoft Sentinel (على سبيل المثال، لديك Microsoft Defender لـ Office 365 الخطة 2 أو أعلى)، وأن حسابك في Microsoft Defender لـ Office 365 أو Microsoft 365 Defender هو *أمان المسؤول*. وأخيرا، تأكد من أن لديك *أذونات الكتابة في Microsoft Sentinel*.

1. انتقل إلى Microsoft Sentinel.
1. على شريط التنقل إلى يمين **موصلات بيانات** **التكوين** >  على الشاشة.
1. **ابحث عن** Microsoft 365 Defender وحدد **موصل Microsoft 365 Defender (معاينة**).
1. على يمين الشاشة، حدد **"فتح صفحة الموصل**".
1. ضمن **"Configuration** >" حدد **"الاتصال incidents & alerts"**
    1. إيقاف تشغيل كافة قواعد إنشاء الحوادث في Microsoft للمنتجات المحددة حاليا.
1. قم بالتمرير إلى **Microsoft Defender لـ Office 365** في قسم **أحداث الاتصال** من الصفحة.

لاحظ أنه يمكنك اختيار جداول من *أي منتج آخر من منتجات Microsoft Defender* تجدها مفيدة وقابلة للتطبيق أثناء إكمال الخطوة النهائية، (أدناه).

7. حدد **EmailEvents** و **EmailUrlInfo** و **EmailAttachmentInfo** و **EmailPostDeliveryEvents** > **وقم بتطبيق التغييرات**.

## <a name="more-resources"></a>موارد إضافية

[دمج حلول الأمان في Microsoft Defender for Cloud](/azure/security-center/security-center-partner-integration#exporting-data-to-a-siem)

[دمج تنبيهات Microsoft Graph واجهة برمجة تطبيقات الأمان مع SIEM](/graph/security-integration)
