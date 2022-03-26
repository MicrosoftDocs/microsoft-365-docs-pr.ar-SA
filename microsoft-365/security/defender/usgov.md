---
title: Microsoft 365 Defender عملاء الحكومة الأمريكية
description: تعرف على Microsoft 365 Defender المتوفرة لعملاء الحكومة الأمريكية
keywords: government, gcc, high, requirements, capabilities, defender, Microsoft 365 Defender, xdr, dod
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
ms.openlocfilehash: 3e8f6e523a5483de99beb0af7d01ab96951b7a3e
ms.sourcegitcommit: 0ee2dabe402d44fecb6856af98a2ef7720d25189
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 12/09/2021
ms.locfileid: "63575167"
---
# <a name="microsoft-365-defender-for-us-government-customers"></a>Microsoft 365 Defender عملاء الحكومة الأمريكية

**ينطبق على:**
- Microsoft 365 Defender

Microsoft 365 Defender لعملاء الحكومة الأمريكية، المضمنين في بيئة Azure US Government، التقنيات الأساسية نفسها التي تستخدمها Microsoft 365 Defender Azure Commercial.

يتوفر هذا العرض لعملاء سحابة القطاع الحكومي سحابة القطاع الحكومي العالية و DoD وهو يستند إلى نفس الإصدار التجاري من المنع والكشف والتحري والوساطة. ومع ذلك، هناك بعض الاختلافات في توفر الإمكانات لهذا العرض.

> [!NOTE]
> إذا كنت عميلا سحابة القطاع الحكومي باستخدام Defender for Cloud Apps أو Defender for Endpoint أو Defender for Identity في الإعلانات التجارية، يجب نقل هذه الخدمات إلى إصدارات سحابة القطاع الحكومي الخاصة بها لتكون مؤهلا للحصول على Microsoft 365 Defender سحابة القطاع الحكومي.

## <a name="licensing-requirements"></a>متطلبات الترخيص

Microsoft 365 Defender عملاء الحكومة الأمريكية أحد عروض الترخيص الكلي التالية من Microsoft:

### <a name="desktop-licensing"></a>ترخيص سطح المكتب

<br />

****

|سحابة القطاع الحكومي|سحابة القطاع الحكومي High|DoD|
|---|---|---|
|Microsoft 365 سحابة القطاع الحكومي G5|Microsoft 365 E5 ل سحابة القطاع الحكومي High|Microsoft 365 G5 ل DOD|
|Microsoft 365 G5 Security سحابة القطاع الحكومي|Microsoft 365 G5 Security سحابة القطاع الحكومي High|Microsoft 365 أمان G5 ل DOD|
|Enterprise Mobility + Security G5 سحابة القطاع الحكومي|Enterprise Mobility + Security E5 سحابة القطاع الحكومي High|Enterprise Mobility + Security E5 ل DOD|
|Office 365 G5 سحابة القطاع الحكومي|Office 365 E5 ل سحابة القطاع الحكومي High|Office 365 E5 ل DOD|
|Microsoft Defender لتطبيقات السحابة سحابة القطاع الحكومي|Microsoft Defender لتطبيقات السحابة سحابة القطاع الحكومي High|Microsoft Defender لتطبيقات السحابة ل DOD|
|Microsoft Defender ل Endpoint - سحابة القطاع الحكومي|Microsoft Defender ل Endpoint for سحابة القطاع الحكومي High|Microsoft Defender لنقطة النهاية ل DOD|
|Microsoft Defender for Identity - سحابة القطاع الحكومي|Microsoft Defender ل Identity for سحابة القطاع الحكومي High|Microsoft Defender for Identity for DOD|
|Microsoft Defender Office 365 (الخطة 2) سحابة القطاع الحكومي|Microsoft Defender Office 365 (الخطة 2) سحابة القطاع الحكومي High|Microsoft Defender Office 365 (الخطة 2) ل DOD|
|Windows 10 Enterprise E5 سحابة القطاع الحكومي|Windows 10 Enterprise E5 سحابة القطاع الحكومي High|Windows 10 Enterprise E5 ل DOD|
|

### <a name="server-licensing"></a>ترخيص الخادم

<br />

****

|سحابة القطاع الحكومي|سحابة القطاع الحكومي High|DoD|
|---|---|---|
|Microsoft Defender ل Endpoint Server سحابة القطاع الحكومي|Microsoft Defender ل Endpoint Server for سحابة القطاع الحكومي High|Microsoft Defender ل Endpoint Server ل DOD|
|Microsoft Defender للخوادم|Microsoft Defender للخوادم - Government|Microsoft Defender للخوادم - Government|
|

## <a name="portal-urls"></a>عناوين URL المدخل

فيما يلي عناوين url Microsoft 365 Defender الإلكتروني لعملاء الحكومة الأمريكية:

<br />

****

|نوع العميل|URL المدخل|
|---|---|
|سحابة القطاع الحكومي|<https://security.microsoft.com>|
|سحابة القطاع الحكومي High|طرح|
|DoD|طرح|
|
> [!NOTE]
> إذا كنت عميلا سحابة القطاع الحكومي وفي عملية الانتقال من Microsoft Defender for Endpoint التجاري https://transition.security.microsoft.com إلى سحابة القطاع الحكومي، فاستخدم للوصول إلى بيانات Microsoft Defender التجارية ل Endpoint.

## <a name="api"></a>API

بدلا من URIs العامة المدرجة في وثائق [API](api-overview.md)، ستحتاج إلى استخدام URIs التالية:

<br />

****

|نوع نقطة النهاية|سحابة القطاع الحكومي|سحابة القطاع الحكومي عالية & DoD|
|---|---|---|
|تسجيل الدخول|`https://login.microsoftonline.com`|`https://login.microsoftonline.us`|
|Microsoft 365 Defender API|`https://api-gcc.security.microsoft.us`|`https://api-gov.security.microsoft.us`|
|

## <a name="feature-parity-with-commercial"></a>المساواة بين الميزات والميزات التجارية

Microsoft 365 Defender عملاء الحكومة الأمريكية عدم التمام الكامل مع العرض التجاري. في حين أن هدفنا هو تقديم جميع الميزات والوظائف التجارية لعملاء الحكومة الأمريكية، إلا أن هناك بعض الإمكانات التي لا نريد تمييزها بعد.

هذه هي الثغرات المعروفة:

<br />

****

|اسم الميزة|سحابة القطاع الحكومي|سحابة القطاع الحكومي High|DoD|
|---|:---:|:---:|:---:|
|عمليات التكامل: Microsoft Sentinel (& البيانات الأولية)|![نعم](../defender-endpoint/images/svg/check-yes.svg)|![نعم](../defender-endpoint/images/svg/check-yes.svg) في المعاينة الخاصة|![نعم](../defender-endpoint/images/svg/check-yes.svg) في المعاينة الخاصة|
|خبراء المخاطر في Microsoft|![لا](../defender-endpoint/images/svg/check-no.svg) على الأعمال الهندسية المتراكمة|![لا](../defender-endpoint/images/svg/check-no.svg) على الأعمال الهندسية المتراكمة|![لا](../defender-endpoint/images/svg/check-no.svg) على الأعمال الهندسية المتراكمة|

## <a name="more-details"></a>مزيد من التفاصيل

لمزيد من المعلومات، راجع أحمال العمل الفردية صفحات US Gov:
- [Microsoft Defender لتطبيقات السحابة](/enterprise-mobility-security/solutions/ems-cloud-app-security-govt-service-description).
- [Microsoft Defender for Identity](/enterprise-mobility-security/solutions/ems-mdi-govt-service-description).
- [Microsoft Defender ل Endpoint](/microsoft-365/security/defender-endpoint/gov).
