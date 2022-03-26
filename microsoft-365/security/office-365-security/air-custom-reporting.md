---
title: حلول إعداد التقارير المخصصة مع إجراء عمليات تحقيق واستجابات تلقائية
keywords: SIEM، API، AIR، autoIR، Microsoft Defender ل Endpoint، التحقيق التلقائي، التكامل، تقرير مخصص
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
description: تعرف على كيفية دمج الاستجابة والتحري التلقائي مع حل إعداد التقارير المخصص أو من جهة خارجية.
ms.date: 01/29/2021
ms.custom:
- air
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 8d2812f9f2e1100a923dc5f9bb22a9b6df218a78
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/08/2022
ms.locfileid: "63567910"
---
# <a name="custom-or-third-party-reporting-solutions-for-microsoft-defender-for-office-365"></a>حلول التقارير المخصصة أو حلول التقارير من جهة خارجية ل Microsoft Defender Office 365

باستخدام [Microsoft Defender Office 365](defender-for-office-365.md)، يمكنك الحصول على [معلومات مفصلة حول عمليات البحث التلقائية](air-view-investigation-results.md). ومع ذلك، تستخدم بعض المؤسسات أيضا حلا مخصصا أو حلا لإعداد التقارير من جهة خارجية. إذا كانت مؤسستك تريد دمج معلومات حول عمليات التحقيق [](office-365-air.md) التلقائية مع مثل هذا الحل، يمكنك استخدام Office 365 API لنشاط الإدارة.

**ينطبق على**
- [Microsoft Defender Office 365 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

باستخدام [Microsoft Defender Office 365](defender-for-office-365.md)، يمكنك الحصول على [معلومات مفصلة حول عمليات البحث التلقائية](air-view-investigation-results.md). ومع ذلك، تستخدم بعض المؤسسات أيضا حلا مخصصا أو حلا لإعداد التقارير من جهة خارجية. إذا كانت مؤسستك تريد دمج معلومات حول عمليات التحقيق التلقائية مع مثل هذا الحل، يمكنك استخدام Office 365 API لنشاط الإدارة.

|المورد|الوصف|
|:---|:---|
|[Office 365 نظرة عامة على واجهات برمجة التطبيقات للإدارة](/office/office-365-management-api/office-365-management-apis-overview)|توفر Office 365 API لنشاط الإدارة معلومات حول مختلف إجراءات المستخدمين والإدارة والإدارة والسياسات والأحداث من سجلات أنشطة Microsoft 365 و Azure Active Directory.|
|[بدء العمل باستخدام Office 365 واجهات برمجة التطبيقات للإدارة](/office/office-365-management-api/get-started-with-office-365-management-apis)|تستخدم Office 365 API لإدارة التطبيق Azure AD لتوفير خدمات مصادقة لتطبيقك للوصول إلى Microsoft 365 البيانات. اتبع الخطوات في هذه المقالة لإعداد هذا الأمر.|
|[Office 365 API لنشاط الإدارة](/office/office-365-management-api/office-365-management-activity-api-reference)|يمكنك استخدام واجهة برمجة Office 365 نشاط الإدارة لاسترداد معلومات حول المستخدم والمسؤول والإجراءات والأحداث المتعلقة بالإدارة والإدارة والسياسات من سجلات أنشطة Microsoft 365 و Azure AD. اقرأ هذه المقالة لمعرفة المزيد حول كيفية عمل ذلك.|
|[Office 365 مخطط API لنشاط الإدارة](/office/office-365-management-api/office-365-management-activity-api-schema)|يمكنك الحصول على نظرة عامة حول المخطط [Common](/office/office-365-management-api/office-365-management-activity-api-schema#common-schema) وم المخطط [Defender Office 365](/office/office-365-management-api/office-365-management-activity-api-schema#office-365-advanced-threat-protection-and-threat-investigation-and-response-schema) والرد على التهديدات والتحري للتعرف على أنواع معينة من البيانات المتوفرة من خلال Office 365 API لنشاط الإدارة.|
|

## <a name="see-also"></a>راجع أيضًا

- [Microsoft Defender Office 365](defender-for-office-365.md)
- [إجراء عمليات التحقيق والاستجابة التلقائية في Microsoft 365 Defender](/microsoft-365/security/defender/m365d-autoir)
