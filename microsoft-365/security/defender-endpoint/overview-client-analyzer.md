---
title: استكشاف الأخطاء في صحة المستشعر وإصلاحها باستخدام Microsoft Defender ل "محلل عميل نقطة النهاية"
description: استكشاف مشاكل حماية المستشعر على الأجهزة وإصلاحها لتحديد التكوين المحتمل أو البيئة أو الاتصال أو مشكلة بيانات المستشعر أو قدراته.
keywords: المستشعر، حماية المستشعر، تكوين خاطئ، غير نشط، عدم وجود بيانات استشعار، بيانات المستشعر، ضعف الاتصالات، الاتصال
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
ms.openlocfilehash: 0de2fbe98527d8fe36f2b8c5d5db0453988501a7
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/08/2022
ms.locfileid: "63574408"
---
# <a name="troubleshoot-sensor-health-using-microsoft-defender-for-endpoint-client-analyzer"></a>استكشاف الأخطاء في صحة المستشعر وإصلاحها باستخدام Microsoft Defender ل "محلل عميل نقطة النهاية"

**ينطبق على:**
- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

يمكن أن يكون Microsoft Defender for Endpoint Client Analyzer (MDECA) مفيدا عند تشخيص مشاكل سلامة المستشعر أو الوثوقية على [](/microsoft-365/security/defender-endpoint/onboard-configure) الأجهزة المجهزة التي تعمل Windows أو Linux أو macOS. على سبيل المثال، قد ترغب في تشغيل المحلل على جهاز يبدو غير صحي وفقا ل حالة حماية المستشعر [المعروضة (](/microsoft-365/security/defender-endpoint/fix-unhealthy-sensors) غير نشط، لا توجد بيانات أدوات استشعار أو اتصالات ضعيف) في مدخل الأمان.

وإلى جانب المشاكل الواضحة المتعلقة بصحة أداة الاستشعار، يمكن ل MDECA تجميع تتبعات وسجلات ومعلومات تشخيصية أخرى من أجل استكشاف الأخطاء وإصلاحها في السيناريوهات المعقدة مثل:

- توافق التطبيقات (AppCompat) أو الأداء أو اتصال الشبكة أو
- سلوك غير متوقع مرتبط بمنع [فقدان البيانات في نقطة النهاية](/microsoft-365/compliance/endpoint-dlp-learn-about).

## <a name="privacy-notice"></a>إشعار الخصوصية

- تستخدم Microsoft Defender for Endpoint Client Analyzer بشكل منتظم بواسطة Microsoft Customer Support Services (CSS) لجمع المعلومات التي ستساعدك على استكشاف المشاكل التي قد تواجهها مع Microsoft Defender for Endpoint وإصلاحها.

- قد تحتوي البيانات التي يتم تجميعها على معلومات تعريف شخصية (PII) و/أو بيانات حساسة، مثل (على وجه لا يقتصر على) عناوين IP وأسماء الكمبيوتر الشخصي وأسماء المستخدمين.

- بعد اكتمال تجميع البيانات، تحفظ الأداة البيانات محليا على الجهاز ضمن ملف مضغوط وملف مضغوط.

- لا يتم إرسال أي بيانات تلقائيا إلى Microsoft. إذا كنت تستخدم الأداة أثناء التعاون في العمل على مشكلة في الدعم، فقد يطلب منك إرسال البيانات المضغوطة إلى Microsoft CSS باستخدام ملف آمن Exchange لتسهيل التحقيق في المشكلة.

لمزيد من المعلومات حول "تأمين Exchange"، راجع كيفية استخدام ملف [آمن Exchange لتبادل الملفات مع دعم Microsoft](/troubleshoot/azure/general/secure-file-exchange-transfer-files)

لمزيد من المعلومات حول بيان الخصوصية، راجع [بيان خصوصية Microsoft](https://privacy.microsoft.com/privacystatement).

## <a name="requirements"></a>المتطلبات

- قبل تشغيل المحلل، نوصي بضمان أن تكوين جدار الحماية أو الوكيل يسمح بالوصول إلى عناوين URL لخدمة [Microsoft Defender لنقطة النهاية](configure-proxy-internet.md#enable-access-to-microsoft-defender-for-endpoint-service-urls-in-the-proxy-server).

- يمكن أن يتم تشغيل المحلل على إصدارات مدعومة من [Windows](minimum-requirements.md#supported-windows-versions) أو [Linux](microsoft-defender-endpoint-linux.md#system-requirements) أو [macOS](microsoft-defender-endpoint-mac.md#system-requirements) إما قبل بعد التكميل في Microsoft Defender لنقطة النهاية.

- بالنسبة Windows الأجهزة، إذا كنت تقوم بتشغيل المحلل مباشرة على أجهزة معينة وليس عن بعد عبر Live [Response](/microsoft-365/security/defender-endpoint/troubleshoot-collect-support-log)، فينبغي السماح بتشغيل SysInternals [PsExec.exe](/sysinternals/downloads/psexec) (مؤقتا على الأقل). يستدعي المحلل أداة PsExec.exe لتشغيل اتصالات السحابة ك "النظام المحلي" ومحاكاة سلوك خدمة SENSE.

    > [!NOTE]
    > على أجهزة Windows، إذا كنت تستخدم قاعدة تقليل الهجوم Surface (ASR) حظر عمليات الإنشاء التي تنشأ من [أوامر PSExec و WMI](attack-surface-reduction-rules-reference.md#block-process-creations-originating-from-psexec-and-wmi-commands)، فقد تحتاج إلى تعطيل القاعدة مؤقتا أو تكوين استثناء لقاعدة [ASR](enable-attack-surface-reduction.md#exclude-files-and-folders-from-asr-rules) للسماح للمحلل بتشغيل عمليات التحقق من الاتصال بالسحابة كما هو متوقع.
