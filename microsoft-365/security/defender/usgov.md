---
title: Microsoft 365 Defender لعملاء حكومة الولايات المتحدة
description: تعرف على Microsoft 365 Defender لمتطلبات عملاء حكومة الولايات المتحدة وقدراتهم المتاحة
keywords: الحكومة، مجلس التعاون، عال، متطلبات، قدرات، defender، Microsoft 365 Defender، xdr، dod
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: conceptual
ms.technology: m365d
ms.openlocfilehash: 53fc78159580a27a8af04009f4e5ecd5b18bc4e8
ms.sourcegitcommit: f181e110cdb983788a86f30d5bb018e53c83e64d
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 06/13/2022
ms.locfileid: "66057572"
---
# <a name="microsoft-365-defender-for-us-government-customers"></a>Microsoft 365 Defender لعملاء حكومة الولايات المتحدة

**ينطبق على:**
- Microsoft 365 Defender

تستخدم Microsoft 365 Defender لعملاء حكومة الولايات المتحدة، المضمنة في بيئة Azure US Government، نفس التقنيات الأساسية مثل Microsoft 365 Defender في Azure Commercial.

يتوفر هذا العرض لعملاء سحابة القطاع الحكومي سحابة القطاع الحكومي High و DoD ويستند إلى نفس الوقاية والكشف والتحقيق والمعالجة مثل الإصدار التجاري. ومع ذلك، هناك بعض الاختلافات في توفر القدرات لهذا العرض.

> [!NOTE]
> إذا كنت عميلا سحابة القطاع الحكومي يستخدم Defender for Cloud Apps أو Defender for Endpoint أو Defender for Identity في Commercial، فستحتاج إلى نقل هذه الخدمات إلى إصداراتها سحابة القطاع الحكومي لتكون مؤهلة للحصول على Microsoft 365 Defender سحابة القطاع الحكومي.

## <a name="licensing-requirements"></a>متطلبات الترخيص

يتطلب Microsoft 365 Defender لعملاء حكومة الولايات المتحدة أحد عروض الترخيص المجمع التالية من Microsoft:

### <a name="desktop-licensing"></a>ترخيص سطح المكتب

<br />

****

|سحابة القطاع الحكومي|سحابة القطاع الحكومي عالية|وزاره الدفاع|
|---|---|---|
|Microsoft 365 سحابة القطاع الحكومي G5|Microsoft 365 E5 ل سحابة القطاع الحكومي High|Microsoft 365 G5 ل DOD|
|Microsoft 365 سحابة القطاع الحكومي أمان G5|Microsoft 365 أمان G5 ل سحابة القطاع الحكومي High|Microsoft 365 أمان G5 ل DOD|
|Enterprise Mobility + Security G5 سحابة القطاع الحكومي|Enterprise Mobility + Security E5 ل سحابة القطاع الحكومي High|Enterprise Mobility + Security E5 ل DOD|
|Office 365 G5 سحابة القطاع الحكومي|Office 365 E5 ل سحابة القطاع الحكومي High|Office 365 E5 ل DOD|
|Microsoft Defender for Cloud Apps سحابة القطاع الحكومي|Microsoft Defender for Cloud Apps ل سحابة القطاع الحكومي High|Microsoft Defender for Cloud Apps ل DOD|
|Microsoft Defender لنقطة النهاية - سحابة القطاع الحكومي|Microsoft Defender لنقطة النهاية ل سحابة القطاع الحكومي High|Microsoft Defender لنقطة النهاية ل DOD|
|Microsoft Defender for Identity - سحابة القطاع الحكومي|Microsoft Defender for Identity ل سحابة القطاع الحكومي High|Microsoft Defender for Identity ل DOD|
|سحابة القطاع الحكومي Microsoft Defender لـ Office 365 (الخطة 2)|Microsoft Defender لـ Office 365 (الخطة 2) ل سحابة القطاع الحكومي عالية|Microsoft Defender لـ Office 365 (الخطة 2) ل DOD|
|سحابة القطاع الحكومي Windows 10 Enterprise E5|Windows 10 Enterprise E5 ل سحابة القطاع الحكومي High|Windows 10 Enterprise E5 ل DOD|
|

### <a name="server-licensing"></a>ترخيص الخادم

<br />

****

|سحابة القطاع الحكومي|سحابة القطاع الحكومي عالية|وزاره الدفاع|
|---|---|---|
|سحابة القطاع الحكومي خادم Microsoft Defender لنقطة النهاية|Microsoft Defender لنقطة النهاية Server ل سحابة القطاع الحكومي High|خادم Microsoft Defender لنقطة النهاية ل DOD|
|Microsoft Defender للخوادم|Microsoft Defender للخوادم - Government|Microsoft Defender للخوادم - Government|
|

## <a name="portal-urls"></a>عناوين URL للمدخل

فيما يلي عناوين URL لمدخل Microsoft 365 Defender لعملاء حكومة الولايات المتحدة:

<br />

****

|نوع العميل|URL المدخل|
|---|---|
|سحابة القطاع الحكومي|<https://security.microsoft.com>|
|سحابة القطاع الحكومي عالية|الطرح|
|وزاره الدفاع|الطرح|
|
> [!NOTE]
> إذا كنت عميلا سحابة القطاع الحكومي وتنتقل من Microsoft Defender لنقطة النهاية تجاري إلى سحابة القطاع الحكومي، فاستخدمه https://transition.security.microsoft.com للوصول إلى بياناتك التجارية Microsoft Defender لنقطة النهاية.

## <a name="api"></a>API

بدلا من معرفات الموارد المنتظمة العامة المدرجة في [وثائق واجهة برمجة التطبيقات](api-overview.md) الخاصة بنا، ستحتاج إلى استخدام معرفات الموارد المنتظمة التالية:

<br />

****

|نوع نقطة النهاية|سحابة القطاع الحكومي|سحابة القطاع الحكومي عالي & DoD|
|---|---|---|
|تسجيل الدخول|`https://login.microsoftonline.com`|`https://login.microsoftonline.us`|
|واجهة برمجة تطبيقات Microsoft 365 Defender|`https://api-gcc.security.microsoft.us`|`https://api-gov.security.microsoft.us`|
|

## <a name="feature-parity-with-commercial"></a>تماثل الميزة مع التجاري

Microsoft 365 Defender لعملاء حكومة الولايات المتحدة ليس لديهم تماثل كامل مع العرض التجاري. في حين أن هدفنا هو تقديم جميع الميزات والوظائف التجارية لعملائنا في حكومة الولايات المتحدة، هناك بعض القدرات التي لا تتوفر بعد نريد تسليط الضوء عليها.

هذه هي الثغرات المعروفة:

<br />

****

|اسم الميزة|سحابة القطاع الحكومي|سحابة القطاع الحكومي عالية|وزاره الدفاع|
|---|:---:|:---:|:---:|
|عمليات التكامل: Microsoft Sentinel (الحوادث & بيانات Raw)|![نعم](../defender-endpoint/images/svg/check-yes.svg) في المعاينة العامة|![نعم](../defender-endpoint/images/svg/check-yes.svg) في المعاينة العامة|![نعم](../defender-endpoint/images/svg/check-yes.svg) في المعاينة العامة|
|خبراء المخاطر في Microsoft|![لا](../defender-endpoint/images/svg/check-no.svg) في الأعمال الهندسية المتراكمة|![لا](../defender-endpoint/images/svg/check-no.svg) في الأعمال الهندسية المتراكمة|![لا](../defender-endpoint/images/svg/check-no.svg) في الأعمال الهندسية المتراكمة|

للحصول على قائمة مفصلة بجداول واجهة برمجة تطبيقات تدفق الأحداث، راجع [Microsoft 365 Defender أنواع أحداث الدفق المعتمدة في واجهة برمجة تطبيقات تدفق الأحداث](supported-event-types.md).

## <a name="more-details"></a>مزيد من التفاصيل

لمزيد من المعلومات، راجع صفحات حكومة الولايات المتحدة لأحمال العمل الفردية:

- [Microsoft Defender for Cloud Apps](/enterprise-mobility-security/solutions/ems-cloud-app-security-govt-service-description).
- [Microsoft Defender for Identity](/enterprise-mobility-security/solutions/ems-mdi-govt-service-description).
- [Microsoft Defender لنقطة النهاية](/microsoft-365/security/defender-endpoint/gov).
