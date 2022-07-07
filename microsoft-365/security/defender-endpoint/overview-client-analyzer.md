---
title: استكشاف أخطاء حماية أداة الاستشعار وإصلاحها باستخدام Microsoft Defender لنقطة النهاية Client Analyzer
description: استكشاف أخطاء حماية أداة الاستشعار على الأجهزة وإصلاحها لتحديد مشكلة التكوين أو البيئة أو الاتصال أو بيانات تتبع الاستخدام المحتملة التي تؤثر على بيانات المستشعر أو القدرة.
keywords: أداة الاستشعار، صحة جهاز الاستشعار، تكوين خاطئ، غير نشط، لا توجد بيانات أداة استشعار، بيانات جهاز الاستشعار، الاتصالات الضعيفة، الاتصال
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: m365-security-compliance
ms.topic: conceptual
ms.technology: m365d
ms.openlocfilehash: cad957dff57da6598e7b7db470998979d2bd0f63
ms.sourcegitcommit: 1734c95ce72d9c8af695cb4b49b1e40d921a1fee
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/07/2022
ms.locfileid: "66685581"
---
# <a name="troubleshoot-sensor-health-using-microsoft-defender-for-endpoint-client-analyzer"></a>استكشاف أخطاء حماية أداة الاستشعار وإصلاحها باستخدام Microsoft Defender لنقطة النهاية Client Analyzer

**ينطبق على:**
- [الخطة 1 من Microsoft Defender لنقطة النهاية](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Defender for Endpoint الخطة 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

يمكن أن يكون Microsoft Defender لنقطة النهاية Client Analyzer (MDECA) مفيدا عند تشخيص مشكلات صحة المستشعر أو الموثوقية على [الأجهزة الملحقة](/microsoft-365/security/defender-endpoint/onboard-configure) التي تعمل إما بنظام التشغيل Windows أو Linux أو macOS. على سبيل المثال، قد ترغب في تشغيل المحلل على جهاز يبدو أنه غير سليم وفقا [لحالة حماية جهاز الاستشعار](/microsoft-365/security/defender-endpoint/fix-unhealthy-sensors) المعروض (غير نشط أو بلا بيانات مستشعر أو اتصالات ضعيفة) في مدخل الأمان.

بالإضافة إلى المشكلات الواضحة المتعلقة بصحة المستشعر، يمكن ل MDECA جمع التتبعات والسجلات ومعلومات التشخيص الأخرى لاستكشاف السيناريوهات المعقدة وإصلاحها مثل:

- توافق التطبيق (AppCompat) أو الأداء أو اتصال الشبكة أو
- سلوك غير متوقع متعلق [بمنع فقدان بيانات نقطة النهاية](/microsoft-365/compliance/endpoint-dlp-learn-about).

## <a name="privacy-notice"></a>إشعار الخصوصية

- يتم استخدام أداة محلل العميل Microsoft Defender لنقطة النهاية بانتظام من قبل خدمات دعم العملاء من Microsoft (CSS) لجمع المعلومات التي ستساعد على استكشاف المشكلات التي قد تواجهها مع Microsoft Defender لنقطة النهاية وإصلاحها.

- قد تحتوي البيانات المجمعة على معلومات تعريف شخصية (PII) و/أو بيانات حساسة، مثل (على سبيل المثال لا الحصر) عناوين IP وأسماء أجهزة الكمبيوتر الشخصية وأسماء المستخدمين.

- بمجرد اكتمال جمع البيانات، تحفظ الأداة البيانات محليا على الجهاز داخل مجلد فرعي وملف مضغوط مضغوط.

- لا يتم إرسال أي بيانات تلقائيا إلى Microsoft. إذا كنت تستخدم الأداة أثناء التعاون بشأن مشكلة في الدعم، فقد يطلب منك إرسال البيانات المضغوطة إلى Microsoft CSS باستخدام Secure File Exchange لتسهيل التحقيق في المشكلة.

لمزيد من المعلومات حول "تبادل الملفات الآمن"، راجع [كيفية استخدام "تبادل الملفات الآمن" لتبادل الملفات مع دعم Microsoft](/troubleshoot/azure/general/secure-file-exchange-transfer-files)

لمزيد من المعلومات حول بيان الخصوصية، راجع [بيان خصوصية Microsoft](https://privacy.microsoft.com/privacystatement).

## <a name="requirements"></a>الاحتياجات

- قبل تشغيل المحلل، نوصي بالتأكد من أن تكوين الوكيل أو جدار الحماية يسمح بالوصول إلى [عناوين URL للخدمة Microsoft Defender لنقطة النهاية](configure-proxy-internet.md#enable-access-to-microsoft-defender-for-endpoint-service-urls-in-the-proxy-server).

- يمكن تشغيل المحلل على الإصدارات المدعومة من [Windows](minimum-requirements.md#supported-windows-versions) أو [Linux](microsoft-defender-endpoint-linux.md#system-requirements) أو [macOS](microsoft-defender-endpoint-mac.md#system-requirements) إما قبل إلحاقه Microsoft Defender لنقطة النهاية.

- بالنسبة إلى أجهزة Windows، إذا كنت تقوم بتشغيل المحلل مباشرة على أجهزة معينة وليس عن بعد عبر [Live Response](/microsoft-365/security/defender-endpoint/troubleshoot-collect-support-log)، فيجب السماح [ بتشغيل SysInternalsPsExec.exe](/sysinternals/downloads/psexec) (مؤقتا على الأقل). يستدعي المحلل أداة PsExec.exe لتشغيل عمليات التحقق من اتصال السحابة كنظام محلي ومحاكاة سلوك خدمة SENSE.

    > [!NOTE]
    > على أجهزة Windows، إذا كنت تستخدم عمليات إنشاء عمليات كتلة قاعدة تقليل الأجزاء المعرضة للهجوم (ASR) [التي تنشأ من أوامر PSExec وWMI](attack-surface-reduction-rules-reference.md#block-process-creations-originating-from-psexec-and-wmi-commands)، فقد ترغب في تعطيل القاعدة مؤقتا أو [تكوين استثناء لقاعدة ASR](enable-attack-surface-reduction.md#exclude-files-and-folders-from-asr-rules) للسماح للمحلل بتشغيل عمليات التحقق من الاتصال إلى السحابة كما هو متوقع.
