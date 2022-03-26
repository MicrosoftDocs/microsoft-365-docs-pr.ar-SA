---
title: Microsoft Defender for Endpoint لعملاء الحكومة الأمريكية
description: تعرف على Microsoft Defender لنقطة النهاية المتوفرة لعملاء الحكومة الأمريكية
keywords: government, gcc, high, requirements, capabilities, defender, Microsoft Defender for Endpoint, endpoint, dod
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
ms.technology: mde
ms.openlocfilehash: b9a083404da3ad4edc3ccf2f88e1c459dc6f08e2
ms.sourcegitcommit: 2697938d2d4fec523b501c5e7b0b8ec8f34e59b0
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/12/2022
ms.locfileid: "63570711"
---
# <a name="microsoft-defender-for-endpoint-for-us-government-customers"></a>Microsoft Defender for Endpoint لعملاء الحكومة الأمريكية

**ينطبق على:**
- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

يستخدم Microsoft Defender for Endpoint لعملاء الحكومة الأمريكية، المضمنين في بيئة Azure US Government، نفس التقنيات الأساسية مثل Defender for Endpoint في Azure Commercial.

يتوفر هذا العرض لعملاء سحابة القطاع الحكومي سحابة القطاع الحكومي العالية و DoD وهو يستند إلى نفس الإصدار التجاري من المنع والكشف والتحري والوساطة. ومع ذلك، هناك بعض الاختلافات في توفر الإمكانات لهذا العرض.

> [!NOTE]
> إذا كنت عميلا سحابة القطاع الحكومي باستخدام Defender for Endpoint في الإعلانات التجارية، فالرجاء الرجوع إلى صفحات الوثائق العامة.

## <a name="licensing-requirements"></a>متطلبات الترخيص

يتطلب Microsoft Defender for Endpoint لعملاء الحكومة الأمريكية أحد عروض الترخيص الكلي التالية من Microsoft:

### <a name="desktop-licensing"></a>ترخيص سطح المكتب

<br />

****

|سحابة القطاع الحكومي|سحابة القطاع الحكومي High|DoD|
|---|---|---|
|Microsoft 365 سحابة القطاع الحكومي G5|Microsoft 365 E5 ل سحابة القطاع الحكومي High|Microsoft 365 G5 ل DOD|
|Microsoft 365 G5 Security سحابة القطاع الحكومي|Microsoft 365 G5 Security سحابة القطاع الحكومي High|Microsoft 365 أمان G5 ل DOD|
|Microsoft Defender ل Endpoint - سحابة القطاع الحكومي|Microsoft Defender ل Endpoint for سحابة القطاع الحكومي High|Microsoft Defender لنقطة النهاية ل DOD|
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

فيما يلي عناوين URL لمدخل Microsoft Defender لنقطة النهاية لعملاء الحكومة الأمريكية:

<br />

****

|نوع العميل|URL المدخل|
|---|---|
|سحابة القطاع الحكومي|<https://security.microsoft.com>|
|سحابة القطاع الحكومي High|<https://security.microsoft.us>|
|DoD|<https://security.microsoft.us>|
|
> [!NOTE]
> إذا كنت عميلا سحابة القطاع الحكومي وفي عملية الانتقال من Microsoft Defender for Endpoint التجاري https://transition.security.microsoft.com إلى سحابة القطاع الحكومي، فاستخدم للوصول إلى بيانات Microsoft Defender التجارية ل Endpoint.

## <a name="endpoint-versions"></a>إصدارات نقطة النهاية

### <a name="standalone-os-versions"></a>إصدارات نظام التشغيل مستقلة

يتم دعم إصدارات نظام التشغيل التالية:

<br />

****

إصدار نظام التشغيل|سحابة القطاع الحكومي|سحابة القطاع الحكومي High|DoD
:---|:---:|:---:|:---:
Windows 11|![نعم.](images/svg/check-yes.svg)|![نعم](images/svg/check-yes.svg)|![نعم](images/svg/check-yes.svg)
Windows 10 الإصدار 21H1 والإصدارات الأحدث|![نعم.](images/svg/check-yes.svg)|![نعم](images/svg/check-yes.svg)|![نعم](images/svg/check-yes.svg)
Windows 10، الإصدار 20H2 ([مع KB4586853](https://support.microsoft.com/help/4586853) <sup>1</sup>)|![نعم.](images/svg/check-yes.svg)|![نعم](images/svg/check-yes.svg)|![نعم](images/svg/check-yes.svg)
Windows 10، الإصدار 2004 ([مع KB4586853](https://support.microsoft.com/help/4586853) <sup>1</sup>)|![نعم.](images/svg/check-yes.svg)|![نعم](images/svg/check-yes.svg)|![نعم](images/svg/check-yes.svg)
Windows 10، الإصدار 1909 ([مع KB4586819](https://support.microsoft.com/help/4586819) <sup>1</sup>)|![نعم.](images/svg/check-yes.svg)|![نعم](images/svg/check-yes.svg)|![نعم](images/svg/check-yes.svg)
Windows 10، الإصدار 1903 ([مع KB4586819](https://support.microsoft.com/help/4586819) <sup>1</sup>)|![نعم.](images/svg/check-yes.svg)|![نعم](images/svg/check-yes.svg)|![نعم](images/svg/check-yes.svg)
الإصدار 1809 من Windows 10 ([مع KB4586839](https://support.microsoft.com/help/4586839) <sup>1</sup>)|![نعم.](images/svg/check-yes.svg)|![نعم](images/svg/check-yes.svg)|![نعم](images/svg/check-yes.svg)
Windows 10، الإصدار 1803 ([مع KB4598245](https://support.microsoft.com/help/4598245) <sup>1</sup>)|![نعم.](images/svg/check-yes.svg)|![نعم](images/svg/check-yes.svg)|![نعم](images/svg/check-yes.svg)
Windows 10، الإصدار 1709|![لا.](images/svg/check-no.svg) <br /> ملاحظة: لن يتم دعم|![نعم](images/svg/check-yes.svg) مع [KB4499147](https://support.microsoft.com/help/4499147) <sup>1</sup> <br /> ملاحظة: [مهمل،](/lifecycle/announcements/revised-end-of-service-windows-10-1709) يرجى الترقية|![لا](images/svg/check-no.svg) <br /> ملاحظة: لن يتم دعم
Windows 10 الإصدار 1703 والإصدارات السابقة|![لا.](images/svg/check-no.svg) <br /> ملاحظة: لن يتم دعم|![لا](images/svg/check-no.svg) <br /> ملاحظة: لن يتم دعم|![لا](images/svg/check-no.svg) <br /> ملاحظة: لن يتم دعم
Windows Server 2022|![نعم.](images/svg/check-yes.svg)|![نعم](images/svg/check-yes.svg)|![نعم](images/svg/check-yes.svg)
Windows Server 2019 ([مع KB4586839](https://support.microsoft.com/help/4586839) <sup>1</sup>)|![نعم.](images/svg/check-yes.svg)|![نعم](images/svg/check-yes.svg)|![نعم](images/svg/check-yes.svg)
Windows Server 2016 (Modern) <sup>2</sup>|![نعم.](images/svg/check-yes.svg) <br /> معاينة عامة|![نعم](images/svg/check-yes.svg) <br /> معاينة عامة|![نعم](images/svg/check-yes.svg) <br /> معاينة عامة
Windows Server 2012 R2 (Modern) <sup>2</sup>|![نعم.](images/svg/check-yes.svg) <br /> معاينة عامة|![نعم](images/svg/check-yes.svg) <br /> معاينة عامة|![نعم](images/svg/check-yes.svg) <br /> معاينة عامة
Windows Server 2016 (Legacy) <sup>3</sup>|![نعم.](images/svg/check-yes.svg)|![نعم](images/svg/check-yes.svg)|![نعم](images/svg/check-yes.svg)
Windows Server 2012 R2 (Legacy) <sup>3</sup>|![نعم.](images/svg/check-yes.svg)|![نعم](images/svg/check-yes.svg)|![نعم](images/svg/check-yes.svg)
Windows Server 2008 R2 SP1 (Legacy) <sup>3</sup>|![نعم.](images/svg/check-yes.svg)|![نعم](images/svg/check-yes.svg)|![نعم](images/svg/check-yes.svg)
Windows 8.1 Enterprise (القديم) <sup>3</sup>|![نعم.](images/svg/check-yes.svg)|![نعم](images/svg/check-yes.svg)|![نعم](images/svg/check-yes.svg)
Windows 8 Pro (القديم) <sup>3</sup>|![نعم.](images/svg/check-yes.svg)|![نعم](images/svg/check-yes.svg)|![نعم](images/svg/check-yes.svg)
Windows 7 SP1 Enterprise (Legacy) <sup>3</sup>|![نعم.](images/svg/check-yes.svg)|![نعم](images/svg/check-yes.svg)|![نعم](images/svg/check-yes.svg)
Windows 7 SP1 Pro (Legacy) <sup>3</sup>|![نعم.](images/svg/check-yes.svg)|![نعم](images/svg/check-yes.svg)|![نعم](images/svg/check-yes.svg)
Linux|![نعم.](images/svg/check-yes.svg)|![نعم](images/svg/check-yes.svg)|![نعم](images/svg/check-yes.svg)
macOS|![نعم.](images/svg/check-yes.svg)|![نعم](images/svg/check-yes.svg)|![نعم](images/svg/check-yes.svg)
Android|![لا.](images/svg/check-no.svg) في التطوير|![لا](images/svg/check-no.svg) في التطوير|![لا](images/svg/check-no.svg) في التطوير
iOS|![لا.](images/svg/check-no.svg) في التطوير|![لا](images/svg/check-no.svg) في التطوير|![لا](images/svg/check-no.svg) في التطوير
|

> [!NOTE]
> <sup>1</sup> يجب نشر التصحيح قبل تهيئة الجهاز من أجل تكوين Defender لنقطة النهاية إلى البيئة الصحيحة.
>
> <sup>2</sup> تعرف على [الحل الحديث الموحد Windows 2016 و2012 R2](configure-server-endpoints.md#new-windows-server-2012-r2-and-2016-functionality-in-the-modern-unified-solution-preview). إذا سبق لك أن قمت بتكحيل الخوادم باستخدام MMA، فاتبع الإرشادات المتوفرة في ترحيل [الخادم](server-migration.md) للترحيل إلى الحل الجديد.
>
> <sup>3</sup> عند استخدام [Microsoft Monitoring Agent](onboard-downlevel.md#install-and-configure-microsoft-monitoring-agent-mma)، ستحتاج إلى اختيار "Azure US Government" ضمن "Azure Cloud" إذا كنت تستخدم معالج الإعداد، [](/azure/log-analytics/log-analytics-windows-agents#install-agent-using-setup-wizard)أو إذا كنت تستخدم سطر أوامر أو [](/azure/log-analytics/log-analytics-windows-agents#install-agent-using-command-line) برنامج نصي [-](/azure/log-analytics/log-analytics-windows-agents#install-agent-using-dsc-in-azure-automation) فحدد المعلمة "OPINSIGHTS_WORKSPACE_AZURE_CLOUD_TYPE" إلى 1. <br /> الحد الأدنى للإصدار المعتمد من MMA هو 10.20.18029 (مارس 2020).

### <a name="os-versions-when-using-microsoft-defender-for-servers"></a>إصدارات نظام التشغيل عند استخدام Microsoft Defender للخوادم

يتم دعم إصدارات نظام التشغيل التالية عند استخدام [Microsoft Defender للخوادم](/azure/security-center/security-center-wdatp):

<br />

****

إصدار نظام التشغيل|سحابة القطاع الحكومي|سحابة القطاع الحكومي High|DoD
:---|:---:|:---:|:---:
Windows Server 2022|![نعم.](images/svg/check-yes.svg)|![نعم](images/svg/check-yes.svg)|![نعم](images/svg/check-yes.svg)
Windows Server 2019|![نعم.](images/svg/check-yes.svg)|![نعم](images/svg/check-yes.svg)|![نعم](images/svg/check-yes.svg)
Windows Server 2016‏|![نعم.](images/svg/check-yes.svg)|![نعم](images/svg/check-yes.svg)|![نعم](images/svg/check-yes.svg)
Windows Server 2012 R2|![نعم.](images/svg/check-yes.svg)|![نعم](images/svg/check-yes.svg)|![نعم](images/svg/check-yes.svg)
Windows Server 2008 R2 SP1|![نعم.](images/svg/check-yes.svg)|![نعم](images/svg/check-yes.svg)|![نعم](images/svg/check-yes.svg)
|

## <a name="required-connectivity-settings"></a>إعدادات الاتصال المطلوبة

إذا كان الوكيل أو جدار الحماية يمنع كل حركة المرور بشكل افتراضي ويسمح فقط بمجالات معينة من خلال، أضف المجالات المدرجة في الورقة القابلة للتنزيل إلى قائمة المجالات المسموح بها.

يسرد جدول البيانات القابل للتنزيل التالي الخدمات ومواعيد URL المقترنة بها التي يجب أن تتمكن شبكتك من الاتصال بها. تحقق من عدم وجود جدار حماية أو قواعد لتصفية الشبكة من شأنها رفض الوصول إلى عناوين URL هذه، أو إنشاء قاعدة السماح  خاصة بها.

|جدول بيانات قائمة المجالات| الوصف|
|---|---|
| قائمة URL ل Microsoft Defender لنقطة النهاية لعملاء Gov/سحابة القطاع الحكومي/DoD | جدول بيانات لسجلات DNS معينة لمواقع الخدمات والمواقع الجغرافية و OS لعملاء Gov/سحابة القطاع الحكومي/DoD. <p> [قم بتنزيل جدول البيانات هنا.](https://download.microsoft.com/download/6/a/0/6a041da5-c43b-4f17-8167-79dfdc10507f/mde-urls-gov.xlsx)

لمزيد من المعلومات، راجع [تكوين إعدادات](configure-proxy-internet.md) اتصال الإنترنت ووكيل الجهاز.

> [!NOTE]
> يحتوي جدول البيانات أيضا على عناوين URL تجارية، وتأكد من التحقق من علامات التبويب "US Gov".
>
> عند التصفية، ابحث عن السجلات التي تسمى "US Gov" وسحابتك المحددة أسفل العمود الجغرافي.

## <a name="api"></a>API

بدلا من URIs العامة المدرجة في وثائق [API](apis-intro.md)، ستحتاج إلى استخدام URIs التالية:

<br />

****

|نوع نقطة النهاية|سحابة القطاع الحكومي|سحابة القطاع الحكومي عالية & DoD|
|---|---|---|
|تسجيل الدخول|`https://login.microsoftonline.com`|`https://login.microsoftonline.us`|
|Defender ل API لنقطة النهاية|`https://api-gcc.securitycenter.microsoft.us`|`https://api-gov.securitycenter.microsoft.us`|
|SIEM|`https://wdatp-alertexporter-us.gcc.securitycenter.windows.us`|`https://wdatp-alertexporter-us.securitycenter.windows.us`|
|

## <a name="feature-parity-with-commercial"></a>المساواة بين الميزات والميزات التجارية

لا يتكرن Defender for Endpoint لعملاء الحكومة الأمريكية تماما مع العرض التجاري. في حين أن هدفنا هو تقديم جميع الميزات والوظائف التجارية لعملاء الحكومة الأمريكية، إلا أن هناك بعض الإمكانات التي لا نريد تمييزها بعد.

هذه هي الثغرات المعروفة:

<br />

****

|اسم الميزة|سحابة القطاع الحكومي|سحابة القطاع الحكومي High|DoD|
|---|:---:|:---:|:---:|
|تقييمات الشبكة|![لا](images/svg/check-no.svg) في التطوير|![لا](images/svg/check-no.svg) في التطوير|![لا](images/svg/check-no.svg) في التطوير|
|اكتشاف الشبكة|![نعم](images/svg/check-yes.svg)|![نعم](images/svg/check-yes.svg)|![نعم](images/svg/check-yes.svg)|
|التقارير: التحكم في الجهاز، حماية الجهاز، جدار الحماية|![لا](images/svg/check-no.svg) في التطوير|![لا](images/svg/check-no.svg) في التطوير|![لا](images/svg/check-no.svg) في التطوير|
|تصفية محتوى ويب|![لا](images/svg/check-no.svg) في التطوير|![لا](images/svg/check-no.svg) في التطوير|![لا](images/svg/check-no.svg) في التطوير|
