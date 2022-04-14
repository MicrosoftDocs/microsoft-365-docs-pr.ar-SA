---
title: Microsoft Defender لنقطة النهاية لعملاء الحكومة الأمريكية
description: تعرف على Microsoft Defender لنقطة النهاية لمتطلبات وقدرات عملاء حكومة الولايات المتحدة المتوفرة
keywords: الحكومة، مجلس التعاون، عال، متطلبات، قدرات، defender، Microsoft Defender لنقطة النهاية، نقطة النهاية، dod
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
ms.openlocfilehash: 32baee17e01aa4223124e21b7d20c219c0dc4b7f
ms.sourcegitcommit: e13c8fc28c68422308c9d356109797cfcf6f77be
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/14/2022
ms.locfileid: "64841852"
---
# <a name="microsoft-defender-for-endpoint-for-us-government-customers"></a>Microsoft Defender لنقطة النهاية لعملاء الحكومة الأمريكية

**ينطبق على:**
- [Microsoft Defender لنقطة النهاية الخطة 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

تستخدم Microsoft Defender لنقطة النهاية لعملاء حكومة الولايات المتحدة، المضمنة في بيئة Azure US Government، نفس التقنيات الأساسية مثل Defender لنقطة النهاية في Azure Commercial.

يتوفر هذا العرض لعملاء سحابة القطاع الحكومي سحابة القطاع الحكومي High و DoD ويستند إلى نفس الوقاية والكشف والتحقيق والمعالجة مثل الإصدار التجاري. ومع ذلك، هناك بعض الاختلافات في توفر القدرات لهذا العرض.

> [!NOTE]
> إذا كنت عميلا سحابة القطاع الحكومي تستخدم Defender لنقطة النهاية في Commercial، فالرجاء الرجوع إلى صفحات الوثائق العامة.

## <a name="licensing-requirements"></a>متطلبات الترخيص

يتطلب Microsoft Defender لنقطة النهاية لعملاء حكومة الولايات المتحدة أحد عروض الترخيص المجمع التالية من Microsoft:

### <a name="desktop-licensing"></a>ترخيص سطح المكتب

<br />

****

|سحابة القطاع الحكومي|سحابة القطاع الحكومي عالية|وزاره الدفاع|
|---|---|---|
|Microsoft 365 سحابة القطاع الحكومي G5|Microsoft 365 E5 ل سحابة القطاع الحكومي High|Microsoft 365 G5 ل DOD|
|Microsoft 365 سحابة القطاع الحكومي أمان G5|Microsoft 365 أمان G5 ل سحابة القطاع الحكومي High|Microsoft 365 أمان G5 ل DOD|
|Microsoft Defender لنقطة النهاية - سحابة القطاع الحكومي|Microsoft Defender لنقطة النهاية ل سحابة القطاع الحكومي High|Microsoft Defender لنقطة النهاية ل DOD|
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

فيما يلي عناوين URL لمدخل Microsoft Defender لنقطة النهاية لعملاء حكومة الولايات المتحدة:

<br />

****

|نوع العميل|URL المدخل|
|---|---|
|سحابة القطاع الحكومي|<https://security.microsoft.com>|
|سحابة القطاع الحكومي عالية|<https://security.microsoft.us>|
|وزاره الدفاع|<https://security.microsoft.us>|
|
> [!NOTE]
> إذا كنت عميلا سحابة القطاع الحكومي وتنتقل من Microsoft Defender لنقطة النهاية تجاري إلى سحابة القطاع الحكومي، فاستخدمه https://transition.security.microsoft.com للوصول إلى بياناتك التجارية Microsoft Defender لنقطة النهاية.

## <a name="endpoint-versions"></a>إصدارات نقطة النهاية

### <a name="standalone-os-versions"></a>إصدارات نظام التشغيل المستقلة

يتم دعم إصدارات نظام التشغيل التالية:

<br />

****

إصدار نظام التشغيل|سحابة القطاع الحكومي|سحابة القطاع الحكومي عالية|وزاره الدفاع
:---|:---:|:---:|:---:
Windows 11|![نعم.](images/svg/check-yes.svg)|![نعم](images/svg/check-yes.svg)|![نعم](images/svg/check-yes.svg)
Windows 10، الإصدار 21H1 والإصدارات الأحدث|![نعم.](images/svg/check-yes.svg)|![نعم](images/svg/check-yes.svg)|![نعم](images/svg/check-yes.svg)
Windows 10، الإصدار 20H2 (مع [KB4586853](https://support.microsoft.com/help/4586853) <sup>1</sup>)|![نعم.](images/svg/check-yes.svg)|![نعم](images/svg/check-yes.svg)|![نعم](images/svg/check-yes.svg)
Windows 10، الإصدار 2004 (مع [KB4586853](https://support.microsoft.com/help/4586853) <sup>1</sup>)|![نعم.](images/svg/check-yes.svg)|![نعم](images/svg/check-yes.svg)|![نعم](images/svg/check-yes.svg)
Windows 10، الإصدار 1909 (مع [KB4586819](https://support.microsoft.com/help/4586819) <sup>1</sup>)|![نعم.](images/svg/check-yes.svg)|![نعم](images/svg/check-yes.svg)|![نعم](images/svg/check-yes.svg)
Windows 10، الإصدار 1903 (مع [KB4586819](https://support.microsoft.com/help/4586819) <sup>1</sup>)|![نعم.](images/svg/check-yes.svg)|![نعم](images/svg/check-yes.svg)|![نعم](images/svg/check-yes.svg)
الإصدار 1809 من Windows 10 (مع [KB4586839](https://support.microsoft.com/help/4586839) <sup>1</sup>)|![نعم.](images/svg/check-yes.svg)|![نعم](images/svg/check-yes.svg)|![نعم](images/svg/check-yes.svg)
Windows 10، الإصدار 1803 (مع [KB4598245](https://support.microsoft.com/help/4598245) <sup>1</sup>)|![نعم.](images/svg/check-yes.svg)|![نعم](images/svg/check-yes.svg)|![نعم](images/svg/check-yes.svg)
Windows 10، الإصدار 1709|![لا.](images/svg/check-no.svg) <br /> ملاحظة: لن يتم دعمه|![نعم](images/svg/check-yes.svg) مع [KB4499147](https://support.microsoft.com/help/4499147) <sup>1</sup> <br /> ملاحظة: [مهمل](/lifecycle/announcements/revised-end-of-service-windows-10-1709)، الرجاء الترقية|![لا](images/svg/check-no.svg) <br /> ملاحظة: لن يتم دعمه
Windows 10، الإصدار 1703 والإصدارات السابقة|![لا.](images/svg/check-no.svg) <br /> ملاحظة: لن يتم دعمه|![لا](images/svg/check-no.svg) <br /> ملاحظة: لن يتم دعمه|![لا](images/svg/check-no.svg) <br /> ملاحظة: لن يتم دعمه
Windows Server 2022|![نعم.](images/svg/check-yes.svg)|![نعم](images/svg/check-yes.svg)|![نعم](images/svg/check-yes.svg)
Windows Server 2019 (مع [KB4586839](https://support.microsoft.com/help/4586839) <sup>1</sup>)|![نعم.](images/svg/check-yes.svg)|![نعم](images/svg/check-yes.svg)|![نعم](images/svg/check-yes.svg)
Windows Server 2016 (حديث) <sup>2</sup>|![نعم.](images/svg/check-yes.svg) <br /> معاينة عامة|![نعم](images/svg/check-yes.svg) <br /> معاينة عامة|![نعم](images/svg/check-yes.svg) <br /> معاينة عامة
Windows Server 2012 R2 (حديث) <sup>2</sup>|![نعم.](images/svg/check-yes.svg) <br /> معاينة عامة|![نعم](images/svg/check-yes.svg) <br /> معاينة عامة|![نعم](images/svg/check-yes.svg) <br /> معاينة عامة
Windows Server 2016 (قديم) <sup>3</sup>|![نعم.](images/svg/check-yes.svg)|![نعم](images/svg/check-yes.svg)|![نعم](images/svg/check-yes.svg)
Windows Server 2012 R2 (قديم) <sup>3</sup>|![نعم.](images/svg/check-yes.svg)|![نعم](images/svg/check-yes.svg)|![نعم](images/svg/check-yes.svg)
Windows Server 2008 R2 SP1 (قديم) <sup>3</sup>|![نعم.](images/svg/check-yes.svg)|![نعم](images/svg/check-yes.svg)|![نعم](images/svg/check-yes.svg)
Windows 8.1 Enterprise (قديم) <sup>3</sup>|![نعم.](images/svg/check-yes.svg)|![نعم](images/svg/check-yes.svg)|![نعم](images/svg/check-yes.svg)
Windows 8 Pro (قديم) <sup>3</sup>|![نعم.](images/svg/check-yes.svg)|![نعم](images/svg/check-yes.svg)|![نعم](images/svg/check-yes.svg)
Windows 7 SP1 Enterprise (قديم) <sup>3</sup>|![نعم.](images/svg/check-yes.svg)|![نعم](images/svg/check-yes.svg)|![نعم](images/svg/check-yes.svg)
Windows 7 SP1 Pro (قديم) <sup>3</sup>|![نعم.](images/svg/check-yes.svg)|![نعم](images/svg/check-yes.svg)|![نعم](images/svg/check-yes.svg)
ينكس|![نعم.](images/svg/check-yes.svg)|![نعم](images/svg/check-yes.svg)|![نعم](images/svg/check-yes.svg)
ماك|![نعم.](images/svg/check-yes.svg)|![نعم](images/svg/check-yes.svg)|![نعم](images/svg/check-yes.svg)
الروبوت|![نعم.](images/svg/check-yes.svg) <br /> معاينة عامة|![نعم](images/svg/check-yes.svg) <br /> معاينة عامة|![نعم](images/svg/check-yes.svg) <br /> معاينة عامة
دائره الرقابه الداخليه|![نعم.](images/svg/check-yes.svg) <br /> معاينة عامة|![نعم](images/svg/check-yes.svg) <br /> معاينة عامة|![نعم](images/svg/check-yes.svg) <br /> معاينة عامة
|

> [!NOTE]
> <sup>1</sup> يجب نشر التصحيح قبل إلحاق الجهاز من أجل تكوين Defender لنقطة النهاية إلى البيئة الصحيحة.
>
> <sup>2</sup> تعرف على [الحل الحديث الموحد Windows 2016 و2012 R2](configure-server-endpoints.md#new-windows-server-2012-r2-and-2016-functionality-in-the-modern-unified-solution). إذا كنت قد قمت مسبقا بإلحاق الخوادم باستخدام MMA، فاتبع الإرشادات المتوفرة في [ترحيل الخادم](server-migration.md) للرحل إلى الحل الجديد.
>
> <sup>3</sup> عند استخدام [عامل مراقبة Microsoft](onboard-downlevel.md#install-and-configure-microsoft-monitoring-agent-mma) ستحتاج إلى اختيار "Azure US Government" ضمن "Azure Cloud" إذا كنت تستخدم [معالج الإعداد](/azure/log-analytics/log-analytics-windows-agents#install-agent-using-setup-wizard)، أو إذا كنت تستخدم [سطر أوامر](/azure/log-analytics/log-analytics-windows-agents#install-agent-using-command-line) أو [برنامج نصي](/azure/log-analytics/log-analytics-windows-agents#install-agent-using-dsc-in-azure-automation) - قم بتعيين المعلمة "OPINSIGHTS_WORKSPACE_AZURE_CLOUD_TYPE" إلى 1. <br /> الحد الأدنى للإصدار المعتمد من MMA هو 10.20.18029 (مارس 2020).

### <a name="os-versions-when-using-microsoft-defender-for-servers"></a>إصدارات نظام التشغيل عند استخدام Microsoft Defender للخوادم

يتم دعم إصدارات نظام التشغيل التالية عند استخدام [Microsoft Defender للخوادم](/azure/security-center/security-center-wdatp):

<br />

****

إصدار نظام التشغيل|سحابة القطاع الحكومي|سحابة القطاع الحكومي عالية|وزاره الدفاع
:---|:---:|:---:|:---:
Windows Server 2022|![نعم.](images/svg/check-yes.svg)|![نعم](images/svg/check-yes.svg)|![نعم](images/svg/check-yes.svg)
Windows Server 2019|![نعم.](images/svg/check-yes.svg)|![نعم](images/svg/check-yes.svg)|![نعم](images/svg/check-yes.svg)
Windows Server 2016‏|![نعم.](images/svg/check-yes.svg)|![نعم](images/svg/check-yes.svg)|![نعم](images/svg/check-yes.svg)
Windows Server 2012 R2|![نعم.](images/svg/check-yes.svg)|![نعم](images/svg/check-yes.svg)|![نعم](images/svg/check-yes.svg)
Windows Server 2008 R2 SP1|![نعم.](images/svg/check-yes.svg)|![نعم](images/svg/check-yes.svg)|![نعم](images/svg/check-yes.svg)
|

## <a name="required-connectivity-settings"></a>إعدادات الاتصال المطلوبة

إذا كان الوكيل أو جدار الحماية يمنع كل نسبة استخدام الشبكة بشكل افتراضي ويسمح بمجالات معينة فقط، فقم بإضافة المجالات المدرجة في الورقة القابلة للتنزيل إلى قائمة المجالات المسموح بها.

يسرد جدول البيانات التالي القابل للتنزيل الخدمات وعناوين URL المقترنة بها التي يجب أن تكون شبكتك قادرة على الاتصال بها. تحقق من عدم وجود جدار حماية أو قواعد تصفية الشبكة التي من شأنها رفض الوصول إلى عناوين URL هذه، أو إنشاء قاعدة *سماح* خاصة بها.

|جدول بيانات قائمة المجالات| الوصف|
|---|---|
|Microsoft Defender لنقطة النهاية قائمة URL للعملاء التجاريين| جدول بيانات لسجلات DNS محددة لمواقع الخدمة والمواقع الجغرافية ونظام التشغيل للعملاء التجاريين. <p> [قم بتنزيل جدول البيانات هنا.](https://download.microsoft.com/download/6/b/f/6bfff670-47c3-4e45-b01b-64a2610eaefa/mde-urls-commercial.xlsx)
| Microsoft Defender لنقطة النهاية قائمة URL ل Gov/سحابة القطاع الحكومي/DoD | جدول بيانات لسجلات DNS محددة لمواقع الخدمة والمواقع الجغرافية ونظام التشغيل لعملاء Gov/سحابة القطاع الحكومي/DoD. <p> [قم بتنزيل جدول البيانات هنا.](https://download.microsoft.com/download/6/a/0/6a041da5-c43b-4f17-8167-79dfdc10507f/mde-urls-gov.xlsx)

لمزيد من المعلومات، راجع [تكوين إعدادات وكيل الجهاز والاتصال بالإنترنت](configure-proxy-internet.md).

> [!NOTE]
> يحتوي جدول البيانات على عناوين URL تجارية أيضا، وتأكد من التحقق من علامات تبويب "حكومة الولايات المتحدة".
>
> عند التصفية، ابحث عن السجلات المسماة باسم "حكومة الولايات المتحدة" وسحابتك المحددة تحت العمود الجغرافي.

## <a name="api"></a>API

بدلا من معرفات الموارد المنتظمة العامة المدرجة في [وثائق واجهة برمجة التطبيقات](apis-intro.md) الخاصة بنا، ستحتاج إلى استخدام معرفات الموارد المنتظمة التالية:

<br />

****

|نوع نقطة النهاية|سحابة القطاع الحكومي|سحابة القطاع الحكومي عالي & DoD|
|---|---|---|
|تسجيل الدخول|`https://login.microsoftonline.com`|`https://login.microsoftonline.us`|
|Defender لواجهة برمجة تطبيقات نقطة النهاية|`https://api-gcc.securitycenter.microsoft.us`|`https://api-gov.securitycenter.microsoft.us`|
|SIEM|`https://wdatp-alertexporter-us.gcc.securitycenter.windows.us`|`https://wdatp-alertexporter-us.securitycenter.windows.us`|
|

## <a name="feature-parity-with-commercial"></a>تماثل الميزة مع التجاري

لا يتمتع Defender لنقطة النهاية لعملاء حكومة الولايات المتحدة بالتماثل الكامل مع العرض التجاري. في حين أن هدفنا هو تقديم جميع الميزات والوظائف التجارية لعملائنا في حكومة الولايات المتحدة، هناك بعض القدرات التي لا تتوفر بعد نريد تسليط الضوء عليها.

هذه هي الثغرات المعروفة:

<br />

****

|اسم الميزة|سحابة القطاع الحكومي|سحابة القطاع الحكومي عالية|وزاره الدفاع|
|---|:---:|:---:|:---:|
|تقييمات الشبكة|![لا](images/svg/check-no.svg) قيد التطوير|![لا](images/svg/check-no.svg) قيد التطوير|![لا](images/svg/check-no.svg) قيد التطوير|
|اكتشاف الشبكة|![نعم](images/svg/check-yes.svg)|![نعم](images/svg/check-yes.svg)|![نعم](images/svg/check-yes.svg)|
|التقارير: التحكم في الجهاز، صحة الجهاز، جدار الحماية|![لا](images/svg/check-no.svg) قيد التطوير|![لا](images/svg/check-no.svg) قيد التطوير|![لا](images/svg/check-no.svg) قيد التطوير|
|تصفية محتوى ويب|![لا](images/svg/check-no.svg) قيد التطوير|![لا](images/svg/check-no.svg) قيد التطوير|![لا](images/svg/check-no.svg) قيد التطوير|
  

هذه هي الميزات والثغرات المعروفة ل [Mobile Threat Defense (Microsoft Defender لنقطة النهاية على Android & iOS)](mtd.md):

<br />

****

|اسم الميزة|سحابة القطاع الحكومي|سحابة القطاع الحكومي عالية|وزاره الدفاع|
|---|:---:|:---:|:---:|
|حماية الويب (مكافحة التصيد الاحتيالي والمؤشرات المخصصة)|![نعم](images/svg/check-yes.svg)|![نعم](images/svg/check-yes.svg)|![نعم](images/svg/check-yes.svg)|
|الحماية من البرامج الضارة (Android-Only)|![لا](images/svg/check-no.svg) قيد التطوير|![لا](images/svg/check-no.svg) قيد التطوير|![لا](images/svg/check-no.svg) قيد التطوير|
|الكشف عن المقاطعة (iOS-Only)|![نعم](images/svg/check-yes.svg)|![نعم](images/svg/check-yes.svg)|![نعم](images/svg/check-yes.svg)|
|الوصول المشروط/التشغيل الشرطي|![نعم](images/svg/check-yes.svg)|![نعم](images/svg/check-yes.svg)|![نعم](images/svg/check-yes.svg)|
|دعم MAM|![نعم](images/svg/check-yes.svg)|![نعم](images/svg/check-yes.svg)|![نعم](images/svg/check-yes.svg)|
|عناصر التحكم في الخصوصية|![نعم](images/svg/check-yes.svg)|![نعم](images/svg/check-yes.svg)|![نعم](images/svg/check-yes.svg)|
|إدارة المخاطر والثغرات الأمنية (TVM)|![لا](images/svg/check-no.svg) قيد التطوير|![لا](images/svg/check-no.svg) قيد التطوير|![لا](images/svg/check-no.svg) قيد التطوير|
  

