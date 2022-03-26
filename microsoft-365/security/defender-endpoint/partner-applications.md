---
title: تطبيقات الشركاء في Microsoft Defender لنقطة النهاية
ms.reviewer: ''
description: عرض تطبيقات الشركاء المعتمدة لتحسين قدرات الكشف عن النظام الأساسي، والتحري عنه، وخطره
keywords: الشركاء، التطبيقات،  الأطراف الخارجية، الاتصالات، sentinelone، lookout، bitdefender، corrata، morphisec، paloalto، ziften، هاتف محمول أفضل
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
ms.openlocfilehash: e7470115d053cd892b87399b53ba0b471c3cda8e
ms.sourcegitcommit: 6e90baef421ae06fd790b0453d3bdbf624b7f9c0
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 02/12/2022
ms.locfileid: "63570425"
---
# <a name="partner-applications-in-microsoft-defender-for-endpoint"></a>تطبيقات الشركاء في Microsoft Defender لنقطة النهاية

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**
- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> هل تريد تجربة Microsoft Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

يدعم Defender for Endpoint تطبيقات  الأطراف الخارجية للمساعدة في تحسين قدرات الكشف والتحري والخطر في النظام الأساسي.

يساعد دعم حلول الجهات الخارجية على زيادة تنظيم الدفاعات وتكاملها وتوحيدها من موردين آخرين باستخدام Microsoft Defender ل Endpoint؛ تمكين فرق الأمان من الاستجابة بشكل فعال للتهديدات الحديثة.

يتكامل Microsoft Defender for Endpoint بسلاسة مع حلول الأمان الموجودة. يوفر التكامل التكامل مع الحلول التالية مثل:

- SIEM
- حلول إدارة خدمات المعلومات والتذاكر
- موفرو خدمات الأمان المدارة (MSSP)
- استخدام مؤشرات IoC ومطابقتها
- إجراء عمليات استنفار تلقائية للجهاز و إصلاحها استنادا إلى التنبيهات الخارجية
- التكامل مع أنظمة تكاتف الأمان والاستجابة التلقائية (SOAR)

## <a name="supported-applications"></a>التطبيقات المعتمدة

### <a name="security-information-and-analytics"></a>معلومات الأمان وتحليلاتها

شعار|اسم الشريك|الوصف
:---|:---|:---
![صورة لشعار AttackIQ.](images/attackiq-logo.png)|[النظام الأساسي ل AttackIQ](https://go.microsoft.com/fwlink/?linkid=2103502)|يتحقق النظام الأساسي ل AttackIQ من صحة تكوين Defender لنقطة النهاية بشكل صحيح عن طريق بدء هجمات مستمرة بأمان على أصول الإنتاج
![صورة لشعار Microsoft Sentinel.](images/sentinel-logo.png)|[AzureSentinel](https://go.microsoft.com/fwlink/?linkid=2135705)|دفق التنبيهات من Microsoft Defender ل Endpoint إلى Microsoft Sentinel
![صورة لشعار Cymulate.](images/cymulate-logo.png)|[Cymulate](https://go.microsoft.com/fwlink/?linkid=2135574)|ربط نتائج Defender لنقطة النهاية بمحاكاة الهجمات للتحقق من دقة الكشف والإجراءات الفعالة للاستجابة
![صورة لشعار الأمان المرن.](images/elastic-security-logo.png)|[أمان مرن](https://go.microsoft.com/fwlink/?linkid=2139303)|الأمان المرن هو حل مجاني ومفتول لمنع التهديدات والكشف عنها والاستجابة لها
![صورة لشعار IBM QRadar.](images/ibm-qradar-logo.png)|[IBM QRadar](https://go.microsoft.com/fwlink/?linkid=2113903)|تكوين IBM QRadar لتجميع الاكتشافات من Defender for Endpoint
![صورة لشعار Micro Focus ArcSight.](images/arcsight-logo.png)|[Micro Focus ArcSight](https://go.microsoft.com/fwlink/?linkid=2113548)|استخدام Micro Focus ArcSight لسحب Defender للكشف عن نقاط النهاية
![صورة لشعار RSA NetWitness.](images/rsa-netwitness-logo.png)|[RSA NetWitness](https://go.microsoft.com/fwlink/?linkid=2118566)|Stream Defender لتنبيهات نقطة النهاية إلى RSA NetWitness باستخدام Microsoft Graph API
![صورة لشعار SafeBreach.](images/safebreach-logo.png)|[SafeBreach](https://go.microsoft.com/fwlink/?linkid=2114114)|الحصول على الرؤية في أحداث أمان Defender for Endpoint التي ترتبط تلقائيا بمحاكاة SafeBreach
![صورة لشعار عنصر التحكم في نقاط الضعف في Skybox.](images/skybox-logo.png)|[عنصر تحكم ثغرة Skybox](https://go.microsoft.com/fwlink/?linkid=2127467)|يخترق عنصر تحكم ثغرة Skybox الضوضاء التي إدارة الثغرات الأمنية سياق العمل والشبكات والمخاطر للكشف عن الثغرات في المخاطر
![صورة لشعار Splunk.](images/splunk-logo.png)|[Splunk](https://go.microsoft.com/fwlink/?linkid=2129805)|تسمح الوظائف الإضافية Defender for Endpoint لمستخدمي Splunk ببلاب كل التنبيهات ومعلومات الدعم إلى Splunk
![صورة لشعار XM Cyber.](images/xmcyber-logo.png)|[XM Cyber](https://go.microsoft.com/fwlink/?linkid=2136700)|تحديد أولويات استجابتك لتنبيه استنادا إلى عوامل الخطر والأصول ذات القيمة العالية

### <a name="orchestration-and-automation"></a>الأتمتة والأتمتة

شعار|اسم الشريك|الوصف
:---|:---|:---
![صورة لشعار CyberSponse CyOps.](images/cybersponse-logo.png)|[CyberSponse CyOps](https://go.microsoft.com/fwlink/?linkid=2115943)|CyOps يتكامل مع Defender for Endpoint لأتمتة دفاتر تشغيل الاستجابة للحوادث عالية السرعة للعملاء
![صورة لشعار Delta Risk ActiveEye.](images/delta-risk-activeeye-logo.png)|[Delta Risk ActiveEye](https://go.microsoft.com/fwlink/?linkid=2127468)|تعمل Delta Risk، وهي موفر رائد لخدمات SOC-as-a-Service والأمان، على دمج Defender for Endpoint مع النظام الأساسي ل SOAR الأصلي على السحابة، ActiveEye.
![صورة لشعار شركة Demisto، وهو شعار شركة Palo Alto Networks.](images/demisto-logo.png)|[Demisto، شركة بالو ألتو Networks](https://go.microsoft.com/fwlink/?linkid=2108414)|يتكامل Demisto مع Defender for Endpoint لتمكين فرق الأمان من تنظيم مراقبة أمان نقاط النهاية وإثرائها والاستجابة لها وأتمتةها
![صورة لشعار Microsoft Flow & Azure Functions.](images/ms-flow-logo.png)|[Microsoft Flow & Azure](https://go.microsoft.com/fwlink/?linkid=2114300)|استخدام موصلات Defender لنقطة النهاية لتطبيقات Azure Logic & Microsoft Flow لأتمتة إجراءات الأمان
![صورة لشعار Rapid7 InsightConnect.](images/rapid7-logo.png)|[Rapid7 InsightConnect](https://go.microsoft.com/fwlink/?linkid=2116040)|تتكامل InsightConnect مع Defender for Endpoint لتسريع عمليات الأمان التي تكثافة الوقت وتبسيطها ودمجها
![صورة لشعار ServiceNow.](images/servicenow-logo.png)|[ServiceNow](https://go.microsoft.com/fwlink/?linkid=2135621)|تنبيهات إلى حل عمليات أمان ServiceNow استنادا إلى تكامل Microsoft Graph API
![صورة لشعار "مسبح".](images/swimlane-logo.png)|[مسبح](https://go.microsoft.com/fwlink/?linkid=2113902)|تكبير قدرات الاستجابة للحوادث باستخدام "مسبح" و"Defender" لنقطة النهاية معا

### <a name="threat-intelligence"></a>المعلومات الاستخبارية للتهديدات

شعار|اسم الشريك|الوصف
:---|:---|:---
![صورة شعار النظام الأساسي لمشاركة معلومات البرامج الضارة في MISP.](images/misp-logo.png)|[MISP (النظام الأساسي لمشاركة معلومات البرامج الضارة)](https://go.microsoft.com/fwlink/?linkid=2127543)|دمج مؤشرات المخاطر من النظام الأساسي لمشاركة المعلومات حول المخاطر المفتوحة المصدر في بيئة Defender لنقطة النهاية
![صورة شعار Palo Alto Networks.](images/paloalto-logo.png)|[Palo Alto Networks](https://go.microsoft.com/fwlink/?linkid=2099582)|تحسين حماية نقطة النهاية من خلال توسيع التركيز التلقائي ومو موجزات التهديدات الأخرى إلى Defender لنقطة النهاية باستخدام MineMeld
![صورة شعار ThreatConnect.](images/threatconnect-logo.png)|[ThreatConnect](https://go.microsoft.com/fwlink/?linkid=2114115)|تنبيه و/أو حظر معلومات التهديدات المخصصة من ThreatConnect Playbooks باستخدام Defender لمؤشرات نقطة النهاية

### <a name="network-security"></a>أمان الشبكة

شعار|اسم الشريك|الوصف
:---|:---|:---
![صورة شعار Aruba ClearPass Policy Manager.](images/aruba-logo.png)|[إدارة نهج Aruba ClearPass](https://go.microsoft.com/fwlink/?linkid=2127544)|التأكد من تثبيت Defender لنقطة النهاية وتحديثه على كل نقطة نهاية قبل السماح بالوصول إلى الشبكة
![صورة لشعار سداسي أزرق للشبكة.](images/bluehexagon-logo.png)|[سداسي أزرق للشبكة](https://go.microsoft.com/fwlink/?linkid=2104613)|قامت السداسيات الزرقاء ببناء أول نظام أساسي للتعلم العميق في الوقت الحقيقي للحماية من تهديدات الشبكة
![صورة لشعار Corelight.](images/logo-corelight.png)| [Corelight]( https://corelight.com/integrations/iot-security)| باستخدام البيانات، المرسلة من أجهزة شبكة Corelight، Microsoft 365 Defender رؤية أكثر في أنشطة الشبكة للأجهزة غير المراقبة، بما في ذلك الاتصال بأجهزة أخرى غير مستخدمة أو شبكات خارجية.
![صورة لشعار CyberMDX.](images/cybermdx-logo.png)|[CyberMDX](https://go.microsoft.com/fwlink/?linkid=2135620)|تدمج خدمة MdX عبر الإنترنت أصول الرعاية الصحية الشاملة والرؤية ومنع المخاطر وإعادة التعيين في بيئة Defender for Endpoint
![صورة شعار HYAS Protect.](images/hyas-logo.png)|[HYAS Protect](https://go.microsoft.com/fwlink/?linkid=2156763)|تستخدم HYAS Protect المعرفة الموثوقة للبنية الأساسية للمهاجمين لحماية Microsoft Defender لنقاط نهاية نقطة النهاية بشكل استباقي من الهجمات الإلكترونية
![صورة لشعار الكشف عن شبكة Vectra والاستجابة لها (NDR).](images/vectra-logo.png)|[الكشف عن شبكة Vectra والاستجابة لها (NDR)](https://go.microsoft.com/fwlink/?linkid=866934)|يطبق Vectra & أمان المعلومات للكشف عن الهجمات الإلكترونية والرد عليها في الوقت الحقيقي

### <a name="cross-platform"></a>النظام الأساسي المتقاطع

شعار|اسم الشريك|الوصف
:---|:---|:---
![صورة لشعار Bitdefender.](images/bitdefender-logo.png)|[Bitdefender](https://go.microsoft.com/fwlink/?linkid=860032)|Bitdefender GravityZone هو نظام أساسي لحماية نقاط نهاية الجيل التالي من طبقات يوفر حماية شاملة ضد النطاق الكامل للتهديدات الإلكترونية المعقدة
![صورة لشعار Better Mobile.](images/bettermobile-logo.png)|[هاتف محمول أفضل](https://go.microsoft.com/fwlink/?linkid=2086214)|حل MTD المستند إلى AI لإيقاف تهديدات الأجهزة المحمولة & التصيد الاحتيالي. استعراض الإنترنت الخاص لحماية خصوصية المستخدم
![صورة لشعار Corrata.](images/corrata-logo.png)|[Corrata](https://go.microsoft.com/fwlink/?linkid=2081148)|حل الأجهزة المحمولة - حماية أجهزتك المحمولة مع إمكانية الرؤية والتحكم من Corrata
![صورة لشعار "البحث".](images/lookout-logo.png)|[البحث](https://go.microsoft.com/fwlink/?linkid=866935)|الحصول على بيانات بيانات عن بعد الحماية من المخاطر على الأجهزة المحمولة التي تعمل بنظامي التشغيل Android و iOS
![صورة لشعار Symantec Endpoint Protection Mobile.](images/symantec-logo.png)|[Symantec Endpoint Protection Mobile](https://go.microsoft.com/fwlink/?linkid=2090992)|يساعد SEP Mobile الشركات على توقع التهديدات الأمنية ونقاط الضعف على الأجهزة المحمولة والكشف عنها ومنعها
![صورة لشعار Zimperium.](images/zimperium-logo.png)|[Zimperium](https://go.microsoft.com/fwlink/?linkid=2118044)|توسيع "Defender" لنقطة النهاية إلى iOS وAndroid التعلم الآلي "الدفاع عن الأجهزة المحمولة" المستندة إلى

## <a name="other-integrations"></a>عمليات التكامل الأخرى

شعار|اسم الشريك|الوصف
:---|:---|:---
![صورة لشعار "تصفية ويب" في Cyren.](images/cyren-logo.png)|[عامل تصفية ويب من Cyren](https://go.microsoft.com/fwlink/?linkid=2108221)|تحسين "Defender" لنقطة النهاية باستخدام تصفية ويب المتقدمة
![صورة لشعار Morphisec.](images/morphisec-logo.png)|[Morphisec](https://go.microsoft.com/fwlink/?linkid=2086215)|يوفر "نقل الهدف الدفاعي" لمنع المخاطر المتقدمة التي تم توفيرها. دمج بيانات التحليلات الجنائية مباشرة في لوحات معلومات WD Defender for Cloud للمساعدة في تحديد أولويات التنبيهات وتحديد درجة الجهاز المعرضة للمخاطر وإبصار المخطط الزمني الكامل للهجوم بما في ذلك معلومات الذاكرة الداخلية
![صورة لشعار سحابة THOR.](images/nextron-thor-logo.png)|[THOR Cloud](https://go.microsoft.com/fwlink/?linkid=862988)|توفير الفحص المباشر للطب الشرعي عند الطلب باستخدام قاعدة توقيع مع التركيز على التهديدات المستمرة

## <a name="siem-integration"></a>تكامل SIEM

يدعم Defender for Endpoint تكامل SIEM من خلال أساليب متعددة. يمكن أن يتضمن ذلك واجهة نظام SIEM متخصصة مع موصلات خارج المربع، وواجهة برمجة تطبيقات عامة للتنبيه لتمكين التنفيذات المخصصة، وواجهة برمجة تطبيقات إجراء لتمكين إدارة حالة التنبيه.

## <a name="ticketing-and-it-service-management"></a>إدارة خدمات المعلومات والتذاكر

يساعد تكامل حل حجز التذاكر على تنفيذ عمليات الاستجابة اليدوية والتلقائية. يمكن أن يساعد Defender for Endpoint على إنشاء تذاكر تلقائيا عند إنشاء تنبيه وحل التنبيهات عند إغلاق التذاكر باستخدام API للتنبيهات.

## <a name="security-orchestration-and-automation-response-soar-integration"></a>تكامل الأمان والاستجابة التلقائية (SOAR)

يمكن أن تساعد حلول "التكامل" في إنشاء دفاتر تشغيل ودمج نموذج البيانات الغنية والإجراءات التي يعرضها Defender ل واجهات برمجة التطبيقات في نقطة النهاية لاستجابات منسوعة، مثل الاستعلام لبيانات الجهاز، وتحريك عزل الجهاز، وحظر/السماح، وحل التنبيه وغيرها.

## <a name="external-alert-correlation-and-automated-investigation-and-remediation"></a>ارتباط التنبيه الخارجي والتحري التلقائي والوساطة

يوفر Defender for Endpoint قدرات فريدة للتحري والرد التلقائي لدفع الاستجابة للحوادث على نطاق واسع.

يساعد دمج إمكانية الاستجابة والتحري التلقائية مع حلول أخرى مثل IDS وجدران الحماية على معالجة التنبيهات وتقليل التعقيدات المحيطة بارتباط إشارة الشبكة والجهاز، مما يعمل على تبسيط إجراءات المعالجة الخاصة بالتحري والتهديدات على الأجهزة بفعالية.

يمكن إرسال التنبيهات الخارجية إلى Defender لنقطة النهاية. يتم عرض هذه التنبيهات جنبا إلى جنب مع تنبيهات إضافية مستندة إلى الجهاز من Defender لنقطة النهاية. توفر طريقة العرض هذه سياقا كاملا للتنبيه ويمكنها الكشف عن القصة الكاملة للهجوم.

## <a name="indicators-matching"></a>مؤشرات متطابقة

يمكنك استخدام المعلومات الخاصة بالتهديات من الموفرين والموفرين للاحتفاظ بمؤشرات اختراق (IOCs) واستخدامها.

يسمح لك Defender for Endpoint بالتكامل مع هذه الحلول والعمل على أجهزة IoCs من خلال ربط بيانات التكليف الغنية بإنشاء تنبيهات. يمكنك أيضا استخدام إمكانات الاستجابة التلقائية والمنع لحظر التنفيذ واتخاذ إجراءات المعالجة عند وجود تطابق.

يدعم Defender لنقطة النهاية حاليا مطابقة IOC ومؤشرات الشبكة ومطابقتها. يتم دعم الحظر لمؤشرات الملفات.

## <a name="support-for-non-windows-platforms"></a>دعم الأنظمة الأساسية غير Windows

يوفر Defender for Endpoint تجربة عمليات أمان مركزية Windows الأنظمة الأساسية Windows، بما في ذلك الأجهزة المحمولة. وستتمكن من رؤية التنبيهات من أنظمة التشغيل المدعمة المختلفة (OS) في المدخل وحماية شبكة مؤسستك بشكل أفضل.
