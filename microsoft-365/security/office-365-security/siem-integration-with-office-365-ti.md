---
title: تكامل SIEM مع Microsoft Defender لـ Office 365
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
description: دمج خادم SIEM الخاص بمؤسستك مع Microsoft Defender لـ Office 365 وأحداث التهديد ذات الصلة في واجهة برمجة تطبيقات إدارة النشاط Office 365.
ms.custom: seo-marvel-apr2020
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 2ffa1e59f368af4b3e99cee9939ed0ead0cc686e
ms.sourcegitcommit: fdd0294e6cda916392ee66f5a1d2a235fb7272f8
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/29/2022
ms.locfileid: "65130987"
---
# <a name="siem-integration-with-microsoft-defender-for-office-365"></a>تكامل SIEM مع Microsoft Defender لـ Office 365

**ينطبق على**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [خطة 1 وخطة 2 من Microsoft Defender لـ Office 365](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

إذا كانت مؤسستك تستخدم خادم إدارة معلومات الأمان والأحداث (SIEM)، يمكنك دمج Microsoft Defender لـ Office 365 مع خادم SIEM. يمكنك إعداد هذا التكامل باستخدام [واجهة برمجة تطبيقات إدارة النشاط Office 365](/office/office-365-management-api/office-365-management-activity-api-reference).

يتيح لك تكامل SIEM عرض المعلومات، مثل البرامج الضارة أو التصيد الاحتيالي الذي تم اكتشافه بواسطة Microsoft Defender لـ Office 365، في تقارير خادم SIEM.

- للاطلاع على مثال على تكامل SIEM مع Microsoft Defender لـ Office 365، راجع [مدونة المجتمع التقني: تحسين فعالية SOC باستخدام Defender لـ Office 365 وواجهة برمجة تطبيقات إدارة O365](https://techcommunity.microsoft.com/t5/microsoft-security-and/improve-the-effectiveness-of-your-soc-with-office-365-atp-and/ba-p/1525185).
- لمعرفة المزيد حول واجهات برمجة تطبيقات الإدارة Office 365، راجع [Office 365 نظرة عامة على واجهات برمجة التطبيقات للإدارة](/office/office-365-management-api/office-365-management-apis-overview).

## <a name="how-siem-integration-works"></a>كيفية عمل تكامل SIEM

تسترد واجهة برمجة تطبيقات إدارة النشاط Office 365 معلومات حول إجراءات وأحداث المستخدم والمسؤول والنظام والنهج من سجلات نشاط Microsoft 365 وAzure Active Directory لمؤسستك. إذا كان لدى مؤسستك Microsoft Defender لـ Office 365 الخطة 1 أو 2 أو Office 365 E5، يمكنك استخدام [مخطط Microsoft Defender لـ Office 365](/office/office-365-management-api/office-365-management-activity-api-schema#office-365-advanced-threat-protection-and-threat-investigation-and-response-schema).

مؤخرا، تمت إضافة أحداث من قدرات التحقيق والاستجابة التلقائية في [Microsoft Defender لـ Office 365 الخطة 2](defender-for-office-365.md#microsoft-defender-for-office-365-plan-1-and-plan-2) إلى واجهة برمجة تطبيقات نشاط الإدارة Office 365. بالإضافة إلى تضمين بيانات حول تفاصيل التحقيق الأساسي مثل المعرف والاسم والحالة، تحتوي واجهة برمجة التطبيقات أيضا على معلومات عالية المستوى حول إجراءات التحقيق والكيانات.

يقوم خادم SIEM أو نظام آخر مشابه باستقصاءات حمل العمل **audit.general** للوصول إلى أحداث الكشف. لمعرفة المزيد، راجع [بدء استخدام واجهات برمجة تطبيقات إدارة Office 365](/office/office-365-management-api/get-started-with-office-365-management-apis).

## <a name="enum-auditlogrecordtype---type-edmint32"></a>تعداد: AuditLogRecordType - النوع: Edm.Int32

### <a name="auditlogrecordtype"></a>AuditLogRecordType

يلخص الجدول التالي قيم **AuditLogRecordType** ذات الصلة بأحداث Microsoft Defender لـ Office 365:<br/><br/>

| قيمه | اسم العضو | الوصف |
|---|---|---|
| 28| التحليل الذكي للمخاطر | أحداث التصيد الاحتيالي والبرامج الضارة من Exchange Online Protection Microsoft Defender لـ Office 365. |
| 41| ThreatIntelligenceUrl | خزينة ارتباطات وقت الحظر وتجاوز حظر الأحداث من Microsoft Defender لـ Office 365. |
| 47| ThreatIntelligenceAtpContent | أحداث التصيد الاحتيالي والبرامج الضارة للملفات في SharePoint Online OneDrive for Business Microsoft Teams من Microsoft Defender لـ Office 365. |
| 64| AirInvestigation | أحداث التحقيق والاستجابة التلقائية، مثل تفاصيل التحقيق والبيانات الاصطناعية ذات الصلة، من Microsoft Defender لـ Office 365 الخطة 2. |

> [!IMPORTANT]
> يجب أن يكون لديك دور المسؤول العام أو مسؤول الأمان المعين في مدخل Microsoft 365 Defender لإعداد تكامل SIEM مع Microsoft Defender لـ Office 365. لمزيد من المعلومات، راجع [الأذونات في مدخل Microsoft 365 Defender](permissions-microsoft-365-security-center.md).
>
> يجب تشغيل تسجيل التدقيق لبيئة Microsoft 365. للحصول على تعليمات حول هذا الأمر، راجع [تشغيل البحث في سجل التدقيق أو إيقاف تشغيله](../../compliance/turn-audit-log-search-on-or-off.md).

## <a name="see-also"></a>راجع أيضًا

[Office 365 التحقيق في التهديدات والاستجابة لها](office-365-ti.md)

[التحقيق التلقائي والاستجابة (AIR) في Office 365](automated-investigation-response-office.md)
