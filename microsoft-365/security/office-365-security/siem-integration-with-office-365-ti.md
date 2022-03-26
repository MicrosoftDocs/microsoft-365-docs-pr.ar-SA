---
title: تكامل SIEM مع Microsoft Defender Office 365
f1.keywords:
- NOCSH
ms.author: deniseb
author: denisebmsft
manager: dansimp
audience: ITPro
ms.topic: article
ms.localizationpriority: ''
search.appverid:
- MET150
- MOE150
ms.assetid: eb56b69b-3170-4086-82cf-ba40a530fa1b
ms.date: 08/21/2020
ms.collection:
- M365-security-compliance
description: ادمج خادم SIEM الخاص بالمنظمة مع Microsoft Defender Office 365 المخاطر ذات الصلة في Office 365 API لإدارة النشاط.
ms.custom: seo-marvel-apr2020
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 3dbb175ba169c9bb8f4d7240d59d9886391167c3
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 10/06/2021
ms.locfileid: "63565949"
---
# <a name="siem-integration-with-microsoft-defender-for-office-365"></a>تكامل SIEM مع Microsoft Defender Office 365

**ينطبق على**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender Office 365 الخطة 1 الخطة 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]


إذا كانت مؤسستك تستخدم خادم معلومات الأمان وإدارة الأحداث (SIEM)، يمكنك دمج Microsoft Defender Office 365 مع خادم SIEM. يمكنك إعداد هذا التكامل باستخدام Office 365 [API لإدارة النشاط](/office/office-365-management-api/office-365-management-activity-api-reference).

يمكنك تكامل SIEM من عرض المعلومات، مثل البرامج الضارة أو التصيد الاحتيالي الذي كشف عنه Microsoft Defender Office 365، في تقارير خادم SIEM.

- للحصول على مثال حول تكامل SIEM مع Microsoft Defender for Office 365، راجع مدونة المجتمع التقني: تحسين فعالية [SOC مع Defender for Office 365 و API لإدارة O365](https://techcommunity.microsoft.com/t5/microsoft-security-and/improve-the-effectiveness-of-your-soc-with-office-365-atp-and/ba-p/1525185).
- لمعرفة المزيد حول Office 365 واجهات برمجة التطبيقات للإدارة، راجع Office 365 [نظرة عامة على واجهات برمجة التطبيقات للإدارة](/office/office-365-management-api/office-365-management-apis-overview).

## <a name="how-siem-integration-works"></a>كيفية عمل تكامل SIEM

تسترد Office 365 API لإدارة نشاط المؤسسة معلومات حول المستخدم والمسؤول والإجراءات والأحداث المتعلقة ب النظام والسياسات من سجلات نشاط Microsoft 365 و Azure Active Directory في مؤسستك. إذا كانت مؤسستك تستخدم Microsoft Defender Office 365 1 أو 2 أو Office 365 E5، يمكنك استخدام [مخطط Microsoft Defender Office 365.](/office/office-365-management-api/office-365-management-activity-api-schema#office-365-advanced-threat-protection-and-threat-investigation-and-response-schema)

مؤخرا، تم إضافة الأحداث من قدرات الاستجابة والتحريات التلقائية في [Microsoft Defender Office 365 الخطة 2](defender-for-office-365.md#microsoft-defender-for-office-365-plan-1-and-plan-2) إلى Office 365 API لنشاط الإدارة. بالإضافة إلى بيانات حول تفاصيل التحقيق الأساسي مثل الم ID والاسم الحالة، تحتوي أيضا API على معلومات عالية المستوى حول إجراءات التحقيق والكيانات.

يدقق خادم SIEM أو أي نظام آخر مماثل في **حمل عمل التدقيق.عام** للوصول إلى أحداث الكشف. لمعرفة المزيد، راجع [بدء Office 365 واجهات برمجة التطبيقات للإدارة](/office/office-365-management-api/get-started-with-office-365-management-apis).

## <a name="enum-auditlogrecordtype---type-edmint32"></a>Enum: AuditLogRecordType - النوع: Edm.Int32

### <a name="auditlogrecordtype"></a>AuditLogRecordType

يلخص الجدول التالي قيم **AuditLogRecordType** ذات الصلة ب Microsoft Defender Office 365 الأحداث:<br/><br/>

| القيمة | اسم العضو | الوصف |
|---|---|---|
| 28| ThreatIntelligence | أحداث التصيد الاحتيالي والبرامج الضارة من Exchange Online Protection و Microsoft Defender Office 365. |
| 41| ThreatIntelligenceUrl | خزينة ارتباطات وقت الحظر وتجاوز الأحداث من Microsoft Defender Office 365. |
| 47| ThreatIntelligenceAtpContent | أحداث التصيد الاحتيالي والبرامج الضارة لملفات SharePoint عبر الإنترنت OneDrive for Business و Microsoft Teams من Microsoft Defender Office 365. |
| 64| AirInvestigation | أحداث الاستجابة والتحريات التلقائية، مثل تفاصيل التحقيق والتحف ذات الصلة، من Microsoft Defender Office 365 الخطة 2. |

> [!IMPORTANT]
> يجب تعيين دور المسؤول العام أو مسؤول الأمان في مدخل Microsoft 365 Defender لإعداد تكامل SIEM مع Microsoft Defender Office 365. لمزيد من المعلومات، راجع [الأذونات في Microsoft 365 Defender المدخل](permissions-microsoft-365-security-center.md).
>
> يجب تشغيل تسجيل التدقيق لبيئة Microsoft 365 الخاصة بك. للحصول على تعليمات حول ذلك، راجع [تشغيل البحث في سجل التدقيق أو إيقاف تشغيله](../../compliance/turn-audit-log-search-on-or-off.md).

## <a name="see-also"></a>راجع أيضًا

[Office 365 عن التهديدات والرد عليها](office-365-ti.md)

[إجراء عمليات التحقيق والاستجابة التلقائية (AIR) في Office 365](automated-investigation-response-office.md)