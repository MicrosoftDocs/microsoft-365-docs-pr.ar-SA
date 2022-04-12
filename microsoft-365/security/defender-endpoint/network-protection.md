---
title: استخدام حماية الشبكة للمساعدة في منع الاتصالات بالمواقع غير الصالحة
description: حماية شبكتك عن طريق منع المستخدمين من الوصول إلى عناوين الشبكة الضارة والمريبة المعروفة
keywords: حماية الشبكة، الاستغلال، موقع ويب ضار، ip، المجال، المجالات
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
audience: ITPro
author: denisebmsft
ms.author: deniseb
ms.reviewer: oogunrinde
manager: dansimp
ms.custom: asr
ms.technology: mde
ms.topic: overview
ms.collection:
- m365initiative-m365-defender
- M365-security-compliance
ms.date: ''
ms.openlocfilehash: f58c7afe9c6f532f7f6420d58bcd681778483680
ms.sourcegitcommit: 4f56b4b034267b28c7dd165e78ecfb4b5390087d
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/12/2022
ms.locfileid: "64789327"
---
# <a name="protect-your-network"></a>حماية الشبكة

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**
- [Microsoft Defender لنقطة النهاية الخطة 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)
- برنامج الحماية من الفيروسات من Microsoft Defender

**منصات**
- بالنسبة لنظام التشغيل

> هل تريد تجربة Microsoft Defender لنقطة النهاية؟ [التسجيل للحصول على إصدار تجريبي مجاني.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

## <a name="overview-of-network-protection"></a>نظرة عامة على حماية الشبكة

تساعد حماية الشبكة على حماية الأجهزة من الأحداث المستندة إلى الإنترنت. حماية الشبكة هي قدرة تقليل الأجزاء المعرضة للهجوم. يساعد على منع الموظفين من الوصول إلى المجالات الخطرة من خلال التطبيقات. تعتبر المجالات التي تستضيف رسائل التصيد الاحتيالي وعمليات الاستغلال والمحتوى الضار الآخر على الإنترنت مجالات خطرة. تعمل حماية الشبكة على توسيع نطاق [Microsoft Defender SmartScreen](/windows/security/threat-protection/microsoft-defender-smartscreen/microsoft-defender-smartscreen-overview) لحظر كافة نسبة استخدام شبكة HTTP الصادرة التي تحاول الاتصال بمصادر ذات سمعة منخفضة (استنادا إلى المجال أو اسم المضيف).

تعمل حماية الشبكة على توسيع الحماية في [حماية الويب](web-protection-overview.md) إلى مستوى نظام التشغيل. يوفر وظيفة حماية الويب في Edge للمستعرضات الأخرى المدعومة والتطبيقات غير المستعرضة. بالإضافة إلى ذلك، توفر حماية الشبكة رؤية وحظر مؤشرات التسوية (IOCs) عند استخدامها مع [الكشف عن نقطة النهاية والاستجابة لها](overview-endpoint-detection-response.md). على سبيل المثال، تعمل حماية الشبكة مع [المؤشرات المخصصة](manage-indicators.md) التي يمكنك استخدامها لحظر مجالات أو أسماء مضيفين معينة.

> [!TIP]
> راجع موقع اختبار Microsoft Defender لنقطة النهاية في [demo.wd.microsoft.com](https://demo.wd.microsoft.com?ocid=cx-wddocs-testground) لمعرفة كيفية عمل حماية الشبكة.

> [!NOTE]
> تم إهمال الموقع التجريبي ل Defender لنقطة النهاية في demo.wd.microsoft.com وستتم إزالته في المستقبل.

## <a name="requirements-for-network-protection"></a>متطلبات حماية الشبكة

تتطلب حماية الشبكة Windows 10 Pro أو Enterprise، برنامج الحماية من الفيروسات من Microsoft Defender الحماية في الوقت الحقيقي.

<br>

****

|إصدار Windows|برنامج الحماية من الفيروسات من Microsoft Defender|
|---|---|
|Windows 10 الإصدار 1709 أو إصدار أحدث <p> Windows 11 <p> Windows Server 1803 أو إصدار أحدث|برنامج الحماية من الفيروسات من Microsoft Defender يجب تمكين [الحماية في الوقت الحقيقي](configure-real-time-protection-microsoft-defender-antivirus.md) [والحماية التي توفرها السحابة](enable-cloud-protection-microsoft-defender-antivirus.md)|
|

بعد تمكين الخدمات، قد تحتاج إلى تكوين الشبكة أو جدار الحماية للسماح بالاتصالات بين الخدمات والأجهزة (يشار إليها أيضا بنقاط النهاية).

- `.smartscreen.microsoft.com`
- `.smartscreen-prod.microsoft.com`

## <a name="configuring-network-protection"></a>تكوين حماية الشبكة

لمزيد من المعلومات حول كيفية تمكين حماية الشبكة، راجع **[تمكين حماية الشبكة](enable-network-protection.md)**. استخدم نهج المجموعة أو PowerShell أو MDM CSPs لتمكين حماية الشبكة وإدارتها في شبكتك.

## <a name="viewing-network-protection-events"></a>عرض أحداث حماية الشبكة

تعمل حماية الشبكة بشكل أفضل مع [Microsoft Defender لنقطة النهاية](microsoft-defender-endpoint.md)، والتي تمنحك تقارير مفصلة عن أحداث الحماية من الاستغلال وحظرها كجزء من [سيناريوهات التحقيق في التنبيه](investigate-alerts.md).

عندما تمنع حماية الشبكة الاتصال، يتم عرض إعلام من مركز الصيانة. يمكن لفريق عمليات الأمان [تخصيص الإعلام](attack-surface-reduction-rules-deployment-implement.md#customize-attack-surface-reduction-rules) باستخدام تفاصيل مؤسستك ومعلومات الاتصال الخاصة بها. بالإضافة إلى ذلك، يمكن تمكين قواعد تقليل الأجزاء المعرضة للهجوم الفردي وتخصيصها لتناسب تقنيات معينة للمراقبة.

يمكنك أيضا استخدام [وضع التدقيق](audit-windows-defender.md) لتقييم كيفية تأثير حماية الشبكة على مؤسستك إذا تم تمكينها.

## <a name="review-network-protection-events-in-the-microsoft-365-defender-portal"></a>مراجعة أحداث حماية الشبكة في مدخل Microsoft 365 Defender

يوفر Microsoft Defender لنقطة النهاية تقارير مفصلة عن الأحداث والكتل كجزء من [سيناريوهات التحقيق في التنبيه الخاصة به](investigate-alerts.md). يمكنك عرض هذه التفاصيل في مدخل Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)) في [قائمة انتظار التنبيهات](review-alerts.md) أو باستخدام [التتبع المتقدم](advanced-hunting-overview.md). إذا كنت تستخدم [وضع التدقيق](audit-windows-defender.md)، يمكنك استخدام التتبع المتقدم لمعرفة كيف ستؤثر إعدادات حماية الشبكة على بيئتك إذا تم تمكينها.

فيما يلي مثال على استعلام للتتبع المتقدم:

```kusto
DeviceNetworkEvents
|where ActionType in ('ExploitGuardNetworkProtectionAudited','ExploitGuardNetworkProtectionBlocked', 'ConnectionSuccess')
```

## <a name="review-network-protection-events-in-windows-event-viewer"></a>مراجعة أحداث حماية الشبكة في Windows عارض الأحداث

يمكنك مراجعة سجل أحداث Windows للاطلاع على الأحداث التي يتم إنشاؤها عندما تمنع حماية الشبكة (أو تقوم بالتدقيق) الوصول إلى عنوان IP أو مجال ضار:

1. [نسخ XML مباشرة](event-views.md).

2. حدد **موافق**.

ينشئ هذا الإجراء طريقة عرض مخصصة تقوم بالتصفية لإظهار الأحداث التالية المتعلقة بحماية الشبكة فقط:

<br>

****

|معرف الحدث|الوصف|
|---|---|
|5007|حدث عند تغيير الإعدادات|
|1125|حدث عند تشغيل حماية الشبكة في وضع التدقيق|
|1126|حدث عند تشغيل حماية الشبكة في وضع الحظر|
|

## <a name="network-protection-and-the-tcp-three-way-handshake"></a>حماية الشبكة والتصاق TCP ثلاثي الاتجاهات

مع حماية الشبكة، يتم تحديد ما إذا كان يجب السماح بالوصول إلى موقع أو حظره بعد الانتهاء من [تأكيد الاتصال ثلاثي الاتجاه عبر TCP/IP](/troubleshoot/windows-server/networking/three-way-handshake-via-tcpip). وبالتالي، عندما يتم حظر موقع بواسطة حماية الشبكة، قد ترى نوع `ConnectionSuccess` إجراء ضمن `NetworkConnectionEvents` في مدخل Microsoft 365 Defender، على الرغم من أنه تم حظر الموقع بالفعل. `NetworkConnectionEvents` يتم الإبلاغ عنها من طبقة TCP، وليس من حماية الشبكة. بعد اكتمال عملية تأكيد الاتصال الثلاثية الاتجاه، يتم السماح بالوصول إلى الموقع أو حظره بواسطة حماية الشبكة.

فيما يلي مثال على كيفية عمل ذلك:

1. لنفترض أن المستخدم يحاول الوصول إلى موقع ويب على جهازه. تتم استضافة الموقع على مجال خطير، ويجب حظره بواسطة حماية الشبكة.  

2. تبدأ عملية تأكيد الاتصال ثلاثية الاتجاه عبر TCP/IP. قبل اكتماله، `NetworkConnectionEvents` يتم تسجيل إجراء، ويتم إدراجه `ActionType` ك `ConnectionSuccess`. ومع ذلك، بمجرد اكتمال عملية تأكيد الاتصال الثلاثية الاتجاه، تمنع حماية الشبكة الوصول إلى الموقع. كل هذا يحدث بسرعة كبيرة. تحدث عملية مماثلة مع [Microsoft Defender SmartScreen](/windows/security/threat-protection/microsoft-defender-smartscreen/microsoft-defender-smartscreen-overview)؛ عندما تكتمل عملية تأكيد الاتصال الثلاثية الاتجاه، يتم إجراء تحديد، ويتم إما حظر الوصول إلى موقع أو السماح به.

3. في مدخل Microsoft 365 Defender، يتم سرد تنبيه في [قائمة انتظار التنبيهات](alerts-queue.md). تتضمن تفاصيل هذا التنبيه كلا `NetworkConnectionEvents` من و `AlertEvents`. يمكنك أن ترى أنه تم حظر الموقع، على الرغم من أن لديك `NetworkConnectionEvents` أيضا عنصرا مع ActionType من `ConnectionSuccess`.

## <a name="considerations-for-windows-virtual-desktop-running-windows-10-enterprise-multi-session"></a>اعتبارات Windows سطح المكتب الظاهري الذي يعمل Windows 10 Enterprise جلسات متعددة

نظرا لطبيعة Windows 10 Enterprise متعددة المستخدمين، ضع النقاط التالية في الاعتبار:

1. حماية الشبكة هي ميزة على مستوى الجهاز ولا يمكن استهدافها بجلسات عمل مستخدم معينة.

2. نهج تصفية محتوى ويب أيضا على مستوى الجهاز.

3. إذا كنت بحاجة إلى التفريق بين مجموعات المستخدمين، ففكر في إنشاء مجموعات وتعيينات منفصلة Windows مضيف سطح المكتب الظاهري.

4. اختبر حماية الشبكة في وضع التدقيق لتقييم سلوكها قبل طرحها.

5. ضع في اعتبارك تغيير حجم النشر إذا كان لديك عدد كبير من المستخدمين أو عدد كبير من جلسات العمل متعددة المستخدمين.

### <a name="alternative-option-for-network-protection"></a>خيار بديل لحماية الشبكة

بالنسبة إلى Windows 10 Enterprise Multi-Session 1909 وما فوق، المستخدمة في Windows Virtual Desktop على Azure، يمكن تمكين حماية الشبكة Microsoft Edge باستخدام الأسلوب التالي:

1. استخدم [تشغيل حماية الشبكة](enable-network-protection.md) واتبع الإرشادات لتطبيق النهج الخاص بك.

2. تنفيذ أوامر PowerShell التالية:
  - `Set-MpPreference -EnableNetworkProtection Enabled`
  - `Set-MpPreference -AllowNetworkProtectionOnWinServer 1`
  - `Set-MpPreference -AllowNetworkProtectionDownLevel 1`
  - `Set-MpPreference -AllowDatagramProcessingOnWinServer 1`

## <a name="network-protection-troubleshooting"></a>استكشاف أخطاء حماية الشبكة وإصلاحها

نظرا للبيئة التي يتم فيها تشغيل حماية الشبكة، قد لا تتمكن Microsoft من الكشف عن إعدادات وكيل نظام التشغيل. في بعض الحالات، يتعذر على عملاء حماية الشبكة الوصول إلى خدمة السحابة. لحل مشكلة الاتصال، يجب على العملاء الذين لديهم تراخيص E5 تكوين أحد مفاتيح التسجيل التالية:

```console
reg add "HKLM\Software\Microsoft\Windows Defender" /v ProxyServer /d "<proxy IP address: Port>" /f
reg add "HKLM\Software\Microsoft\Windows Defender" /v ProxyPacUrl /d "<Proxy PAC url>" /f

```

## <a name="see-also"></a>راجع أيضًا

- [تقييم | حماية الشبكة](evaluate-network-protection.md) قم بسيناريو سريع يوضح كيفية عمل الميزة، وما هي الأحداث التي سيتم إنشاؤها عادة.
- [تمكين حماية الشبكة](enable-network-protection.md) | استخدم نهج المجموعة أو PowerShell أو MDM CSPs لتمكين حماية الشبكة وإدارتها في شبكتك.
- [تكوين قدرات تقليل الأجزاء المعرضة للهجوم في Microsoft Intune](/mem/intune/protect/endpoint-security-asr-policy)
