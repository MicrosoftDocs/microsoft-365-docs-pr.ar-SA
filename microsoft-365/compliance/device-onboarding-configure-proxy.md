---
title: تكوين إعدادات اتصال الإنترنت ووكيل الجهاز لحماية المعلومات
f1.keywords:
- CSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: ''
audience: ITPro
ms.topic: conceptual
f1_keywords:
- ms.o365.cc.DLPLandingPage
ms.service: O365-seccomp
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
- m365solution-mip
- m365initiative-compliance
search.appverid:
- MET150
description: تكوين إعدادات اتصال الإنترنت ووكيل الجهاز لحماية المعلومات
ms.openlocfilehash: 2d0bc6484636cffb479ccb96b3458fddf0697cd7
ms.sourcegitcommit: 726a72f135358603c2fde3f4067d834536e6deb2
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 02/03/2022
ms.locfileid: "63575146"
---
# <a name="configure-device-proxy-and-internet-connection-settings-for-information-protection"></a>تكوين إعدادات اتصال الإنترنت ووكيل الجهاز لحماية المعلومات

تستخدم تقنيات Microsoft Endpoint Microsoft Windows HTTP (WinHTTP) للتقرير عن البيانات والتواصل مع خدمة سحابة نقطة نهاية Microsoft. يتم تشغيل الخدمة المضمنة في سياق النظام باستخدام حساب LocalSystem.

> [!TIP]
> بالنسبة إلى المؤسسات التي تستخدم الوكلاء المتقدمين كبوابة إلى الإنترنت، يمكنك استخدام حماية الشبكة للتحقق من خلف وكيل. للحصول على مزيد من المعلومات، راجع [التحقق من أحداث الاتصال التي تقع خلف تكاتف إعادة توجيه](/windows/security/threat-protection/microsoft-defender-atp/investigate-behind-proxy).

يكون إعداد تكوين WinHTTP مستقلا عن إعدادات وكيل استعراض الإنترنت Windows Internet (WinINet) ويمكنه اكتشاف خادم وكيل فقط باستخدام أساليب الاكتشاف التلقائي التالية:

- وكيل شفاف
- بروتوكول الاكتشاف التلقائي لوكيل ويب (WPAD)

> [!NOTE]
> إذا كنت تستخدم وكيل شفاف أو WPAD في طبولوجيا الشبكة، فلا تحتاج إلى إعدادات تكوين خاصة. لمزيد من المعلومات حول استثناءات URL ل Defender لنقطة النهاية في الوكيل، راجع تمكين الوصول إلى عناوين URL لخدمة [DLP السحابية لنقطة النهاية في الخادم الوكيل](#enable-access-to-endpoint-dlp-cloud-service-urls-in-the-proxy-server).

- تكوين وكيل ثابت يدوي:
  - تكوين مستند إلى السجل
  - تم تكوين WinHTTP باستخدام الأمر netsh – مناسب فقط لأسطح المكتب في طبولوجيا ثابتة (على سبيل المثال: سطح مكتب في شبكة شركة خلف الوكيل نفسه)

## <a name="configure-the-proxy-server-manually-using-a-registry-based-static-proxy"></a>تكوين الخادم الوكيل يدويا باستخدام وكيل ثابت مستند إلى السجل

بالنسبة إلى أجهزة نقاط النهاية غير المسموح لها بالاتصال بالإنترنت، ستحتاج إلى تكوين وكيل ثابت يستند إلى السجل. تحتاج إلى تكوين هذا للسماح فقط ل Microsoft Endpoint DLP بلتقارير البيانات التشخيصية والتواصل مع خدمة سحابة نقطة نهاية Microsoft.

يمكن تكوين الوكيل الثابت من خلال نهج المجموعة (GP). يمكن العثور على نهج المجموعة ضمن:

1. فتح **القوالب الإدارية > Windows مكونات** > البيانات والمعاينة > تكوين استخدام الوكيل المصادق عليه لخدمة استخدام المستخدمين المتصلين وبيانات الاستخدام

2. قم بتعيينه إلى **تمكين** وحدد **تعطيل استخدام الوكيل المصادق عليه**:

   ![صورة لإعدادات نهج المجموعة 1.](../media/atp-gpo-proxy1.png)

3. افتح **القوالب الإدارية > Windows مكونات** > إنشاءات تجميع البيانات والمعاينة > تكوين تجارب المستخدمين المتصلة وبيانات بيانات الاستخدام:

   تكوين الوكيل

   ![صورة لإعدادات نهج المجموعة 2.](../media/atp-gpo-proxy2.png)

   يحدد النهج قيمتي تسجيل `TelemetryProxyServer` REG_SZ كقيم REG_DWORD `DisableEnterpriseAuthProxy` أسفل مفتاح التسجيل `HKLM\Software\Policies\Microsoft\Windows\DataCollection`.

   قيمة التسجيل TelemetryProxyServer بهذا التنسيق \<server name or ip\>:\<port\>. على سبيل المثال: **10.0.0.6:8080**

   يجب تعيين قيمة `DisableEnterpriseAuthProxy` السجل إلى 1.

## <a name="configure-the-proxy-server-manually-using-netsh-command"></a>تكوين الخادم الوكيل يدويا باستخدام الأمر "netsh"

استخدم الشبكة لتكوين وكيل ثابت على مستوى النظام.

> [!NOTE]
> سيؤثر هذا على جميع التطبيقات بما في ذلك Windows التي تستخدم WinHTTP مع الوكيل الافتراضي. - ستعطل أجهزة الكمبيوتر المحمولة التي تعمل على تغيير طبولوجيا (على سبيل المثال: من Office إلى home) باستخدام الشبكة. استخدم تكوين الوكيل الثابت المستند إلى السجل.

1. فتح سطر أوامر مرتفع:
    1. انتقل إلى **البدء** وا اكتب **cmd**
    2. انقر ب الماوس **الأيمن فوق موجه الأوامر** وحدد **تشغيل كمسؤول**.

2. أدخل الأمر التالي واضغط على **Enter**:

   `netsh winhttp set proxy <proxy>:<port>`

   على سبيل المثال: **netsh winhttp set proxy 10.0.0.6:8080**

3. لإعادة تعيين وكيل winhttp، أدخل الأمر التالي واضغط على **Enter**:

   `netsh winhttp reset proxy`

راجع [بناء جملة أوامر Netsh والسياقات وتنسيق لمعرفة](/windows-server/networking/technologies/netsh/netsh-contexts) المزيد.

## <a name="enable-access-to-endpoint-dlp-cloud-service-urls-in-the-proxy-server"></a>تمكين الوصول إلى عناوين URL لخدمة Endpoint DLP السحابية في الخادم الوكيل

إذا كان الوكيل أو جدار الحماية يمنع كل حركة المرور بشكل افتراضي ويسمح فقط بمجالات معينة من خلال، أضف المجالات المدرجة في الورقة القابلة للتنزيل إلى قائمة المجالات المسموح بها.

[يسرد جدول البيانات القابل للتنزيل](https://download.microsoft.com/download/8/a/5/8a51eee5-cd02-431c-9d78-a58b7f77c070/mde-urls.xlsx) هذه الخدمات وقوائم URL المقترنة بها التي يجب أن تتمكن شبكتك من الاتصال بها. يجب أن تضمن عدم وجود جدار حماية أو قواعد لتصفية الشبكة من شأنها رفض الوصول إلى عناوين URL هذه، أو قد تحتاج إلى إنشاء قاعدة السماح لها بشكل خاص.

إذا تم تمكين فحص HTTPS (فحص SSL) للوكيل أو جدار الحماية، فاستبعد المجالات المدرجة في الجدول أعلاه من فحص HTTPS.
إذا كان الوكيل أو جدار الحماية يمنع حركة مرور مجهولة، حيث إن DLP لنقطة النهاية يتصل من سياق النظام، فتأكد من السماح ب حركة مرور مجهولة في عناوين URL المدرجة سابقا.

## <a name="verify-client-connectivity-to-microsoft-cloud-service-urls"></a>التحقق من اتصال العميل مع عناوين URL لخدمة Microsoft السحابية

تحقق من اكتمال تكوين الوكيل بنجاح، ومن إمكانية اكتشاف WinHTTP والتواصل عبر الخادم الوكيل في بيئتك، ومن أن الخادم الوكيل يتيح نقل البيانات إلى عناوين URL لخدمة Defender for Endpoint.

1. قم [بتنزيل أداة محلل عميل MDATP](https://aka.ms/mdatpanalyzer) إلى الكمبيوتر الشخصي حيث يتم تشغيل نقطة النهاية DLP.
2. استخراج محتويات MDATPClientAnalyzer.zip على الجهاز.
3. فتح سطر أوامر مرتفع:
    1. انتقل إلى **ابدأ** وا اكتب **cmd**.
    1. انقر ب الماوس **الأيمن فوق موجه الأوامر** وحدد **تشغيل كمسؤول**.
4. أدخل الأمر التالي واضغط على **Enter**:

   `HardDrivePath\MDATPClientAnalyzer.cmd`

   استبدال *HardDrivePath* بالمسار حيث تم تنزيل أداة MDATPClientAnalyzer إلى، على سبيل المثال

   **C:\Work\tools\MDATPClientAnalyzer\MDATPClientAnalyzer.cmd**

5. قم **باستخراجMDATPClientAnalyzerResult.zip** _ التي تم إنشاؤها بواسطة الأداة في المجلد المستخدم في _HardDrivePath*.

6. افتح **MDATPClientAnalyzerResult.txt** وتحقق من أنك قمت بتنفيذ خطوات تكوين الوكيل لتمكين اكتشاف الخادم والوصول إلى عناوين URL للخدمة.  تقوم الأداة بالتحقق من اتصال عناوين URL لخدمة Defender for Endpoint التي تم تكوين Defender for Endpoint client للتفاعل معها. ثم تطبع النتائج في ملف **MDATPClientAnalyzerResult.txtلكل عنوان** URL يمكن استخدامه للتواصل مع خدمات Defender for Endpoint. على سبيل المثال:

   ```DOS
   Testing URL: https://xxx.microsoft.com/xxx
   1 - Default proxy: Succeeded (200)
   2 - Proxy auto discovery (WPAD): Succeeded (200)
   3 - Proxy disabled: Succeeded (200)
   4 - Named proxy: Doesn't exist
   5 - Command-line proxy: Doesn't exist
   ```

إذا كان أحد خيارات الاتصال على الأقل يرجع حالة (200)، يمكن للعميل Defender for Endpoint التواصل مع عنوان URL الذي تم اختباره بشكل صحيح باستخدام أسلوب الاتصال هذا.

ومع ذلك، إذا كانت نتائج التحقق من الاتصال تشير إلى فشل، يتم عرض خطأ HTTP (راجع رموز حالة HTTP). يمكنك بعد ذلك استخدام عناوين URL في الجدول الموضح في تمكين الوصول إلى عناوين URL لخدمة [DLP السحابية لنقطة النهاية في الخادم الوكيل](#enable-access-to-endpoint-dlp-cloud-service-urls-in-the-proxy-server). تعتمد عناوين URL التي ستستخدمها على المنطقة المحددة أثناء إجراء التركب.

> [!NOTE]
>
> لا تتوافق أداة محلل الاتصال مع قاعدة تقليل مساحة الهجوم التي تم إنشاء عملية حظرها [والمنشأة من أوامر PSExec و WMI](/microsoft-365/security/defender-endpoint/attack-surface-reduction-rules-reference#block-process-creations-originating-from-psexec-and-wmi-commands). ستحتاج إلى تعطيل هذه القاعدة مؤقتا لتشغيل أداة الاتصال.
>
> عند تعيين TelemetryProxyServer، في السجل أو عبر نهج المجموعة، سيرجع Defender for Endpoint إلى المباشر إذا لم يكن يمكنه الوصول إلى الوكيل المعرف. موضوعات ذات صلة:
>
> - أجهزة Windows 10 الأجهزة
> - استكشاف مشاكل تشغيل DLP لنقطة نهاية Microsoft وإصلاحها

## <a name="see-also"></a>راجع أيضًا

- [التعرف على منع فقدان بيانات نقطة النهاية](endpoint-dlp-learn-about.md)
- [استخدام منع فقدان البيانات في نقطة النهاية](endpoint-dlp-using.md)
- [التعرف على منع فقدان البيانات](dlp-learn-about-dlp.md)
- [إنشاء نهج DLP واختباره وضبطه](create-test-tune-dlp-policy.md)
- [بدء استخدام "مستكشف النشاط"](data-classification-activity-explorer.md)
- [Microsoft Defender لنقطة النهاية](/windows/security/threat-protection/)
- [أدوات وأساليب ال متنبها Windows 10 الأجهزة](/windows/security/threat-protection/microsoft-defender-atp/configure-endpoints)
- [Microsoft 365 الاشتراك](https://www.microsoft.com/microsoft-365/compare-microsoft-365-enterprise-plans?rtc=1)
- [الأجهزة المنضمة إلى Azure AD](/azure/active-directory/devices/concept-azure-ad-join)
- [قم بتنزيل الملف Microsoft Edge استنادا إلى Chromium](https://support.microsoft.com/help/4501095/download-the-new-microsoft-edge-based-on-chromium)
