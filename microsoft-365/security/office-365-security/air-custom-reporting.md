---
title: حلول التقارير المخصصة مع التحقيق التلقائي والاستجابة
keywords: SIEM، واجهة برمجة التطبيقات، AIR، autoIR، Microsoft Defender لنقطة النهاية، التحقيق التلقائي، التكامل، تقرير مخصص
f1.keywords:
- NOCSH
author: dansimp
ms.author: dansimp
manager: dansimp
audience: ITPro
ms.topic: article
ms.localizationpriority: medium
search.appverid:
- MET150
- MOE150
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
description: تعرف على كيفية دمج التحقيق التلقائي والاستجابة مع حل تقارير مخصص أو تابع لجهة خارجية.
ms.date: 01/29/2021
ms.custom:
- air
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: f21ed51cc9e89c2d60c924df377f109c6e29eec6
ms.sourcegitcommit: 725a92b0b1555572b306b285a0e7a7614d34e5e5
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 05/24/2022
ms.locfileid: "65647876"
---
# <a name="custom-or-third-party-reporting-solutions-for-microsoft-defender-for-office-365"></a>حلول التقارير المخصصة أو الخارجية Microsoft Defender لـ Office 365

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**ينطبق على**
- [Microsoft Defender لـ Office 365 الخطة 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

مع [Microsoft Defender لـ Office 365](defender-for-office-365.md)، يمكنك الحصول على [معلومات مفصلة حول التحقيقات التلقائية](air-view-investigation-results.md). ومع ذلك، تستخدم بعض المؤسسات أيضا حل تقارير مخصص أو تابع لجهة خارجية. إذا كانت مؤسستك تريد دمج معلومات حول [التحقيقات التلقائية](office-365-air.md) مع مثل هذا الحل، يمكنك استخدام واجهة برمجة تطبيقات نشاط الإدارة Office 365.

مع [Microsoft Defender لـ Office 365](defender-for-office-365.md)، يمكنك الحصول على [معلومات مفصلة حول التحقيقات التلقائية](air-view-investigation-results.md). ومع ذلك، تستخدم بعض المؤسسات أيضا حل تقارير مخصص أو تابع لجهة خارجية. إذا كانت مؤسستك تريد دمج معلومات حول التحقيقات التلقائية مع مثل هذا الحل، يمكنك استخدام واجهة برمجة تطبيقات نشاط الإدارة Office 365.

|الموارد|الوصف|
|:---|:---|
|[نظرة عامة على واجهات برمجة تطبيقات إدارة Office 365](/office/office-365-management-api/office-365-management-apis-overview)|توفر واجهة برمجة تطبيقات نشاط الإدارة Office 365 معلومات حول مختلف إجراءات وأحداث المستخدم والمسؤول والنظام والنهج من سجلات نشاط Microsoft 365 وAzure Active Directory.|
|[بدء استخدام واجهات برمجة تطبيقات إدارة Office 365](/office/office-365-management-api/get-started-with-office-365-management-apis)|تستخدم واجهة برمجة تطبيقات إدارة Office 365 Azure AD لتوفير خدمات المصادقة للتطبيق الخاص بك للوصول إلى بيانات Microsoft 365. اتبع الخطوات الواردة في هذه المقالة لإعداد ذلك.|
|[مرجع واجهة برمجة تطبيقات نشاط إدارة Office 365](/office/office-365-management-api/office-365-management-activity-api-reference)|يمكنك استخدام واجهة برمجة تطبيقات نشاط الإدارة Office 365 لاسترداد معلومات حول إجراءات وأحداث المستخدم والمسؤول والنظام والنهج من سجلات نشاط Microsoft 365 Azure AD. اقرأ هذه المقالة لمعرفة المزيد حول كيفية عمل ذلك.|
|[مخطط واجهة برمجة التطبيقات لنشاط إدارة Office 365](/office/office-365-management-api/office-365-management-activity-api-schema)|احصل على نظرة عامة على [المخطط الشائع ومخطط](/office/office-365-management-api/office-365-management-activity-api-schema#common-schema) [Defender لـ Office 365 والتحقيق في التهديدات والاستجابة](/office/office-365-management-api/office-365-management-activity-api-schema#office-365-advanced-threat-protection-and-threat-investigation-and-response-schema) لها للتعرف على أنواع معينة من البيانات المتاحة من خلال واجهة برمجة تطبيقات نشاط الإدارة Office 365.|

## <a name="see-also"></a>راجع أيضًا

- [Microsoft Defender لـ Office 365](defender-for-office-365.md)
- [التحقيق التلقائي والاستجابة في Microsoft 365 Defender](/microsoft-365/security/defender/m365d-autoir)
