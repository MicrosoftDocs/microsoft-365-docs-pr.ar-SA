---
title: استخدام حماية الشبكة للمساعدة على منع الاتصالات بالمواقع غير المسيئة
description: حماية الشبكة من خلال منع المستخدمين من الوصول إلى عناوين الشبكة المعروفة الضارة والمريبة
keywords: حماية الشبكة، استغلالات، موقع ويب ضار، ip، مجال، مجالات
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
ms.openlocfilehash: 7b9443cac6543ac14f6d94bd2809b5263be0a860
ms.sourcegitcommit: b3530441288b2bc44342e00e9025a49721796903
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/20/2022
ms.locfileid: "63681821"
---
# <a name="protect-your-network"></a>حماية الشبكة

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**
- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> هل تريد تجربة Microsoft Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

## <a name="overview-of-network-protection"></a>نظرة عامة حول حماية الشبكة

تساعد حماية الشبكة على حماية الأجهزة من الأحداث المستندة إلى الإنترنت. حماية الشبكة هي إمكانية تقليل مساحة الهجوم. يساعد ذلك على منع الموظفين من الوصول إلى مجالات خطيرة من خلال التطبيقات. تعتبر المجالات التي تستضيف رسائل التصيد الاحتيالي والمستغلة والمحتويات الضارة الأخرى على الإنترنت خطرة. توسع حماية الشبكة نطاق Microsoft Defender SmartScreen لحظر [](/windows/security/threat-protection/microsoft-defender-smartscreen/microsoft-defender-smartscreen-overview) كل عمليات نقل البيانات الصادرة من HTTP (HTTP) التي تحاول الاتصال بمصادر ذات سمعة منخفضة (استنادا إلى المجال أو اسم المضيف).

تعمل حماية الشبكة على توسيع الحماية في [حماية الويب](web-protection-overview.md) إلى مستوى نظام التشغيل. فهو يوفر وظائف حماية الويب في Edge إلى المستعرضات الأخرى المعتمدة والتطبيقات غير المستعرضة. بالإضافة إلى ذلك، توفر حماية الشبكة إمكانية رؤية مؤشرات اختراق (IOCs) وحظرها عند استخدامها مع الكشف عن نقطة النهاية [والاستجابة لها](overview-endpoint-detection-response.md). على سبيل المثال، تعمل حماية [الشبكة مع المؤشرات](manage-indicators.md) المخصصة التي يمكنك استخدامها لحظر مجالات أو أسماء مضيفة معينة.

> [!TIP]
> راجع موقع اختبار Microsoft Defender ل Endpoint [في demo.wd.microsoft.com](https://demo.wd.microsoft.com?ocid=cx-wddocs-testground) لمعرفة كيفية عمل حماية الشبكة.

> [!NOTE]
> تم إهمال موقع عرض Defender for Endpoint demo.wd.microsoft.com، وستزال في المستقبل.

## <a name="requirements-for-network-protection"></a>متطلبات حماية الشبكة

تتطلب حماية الشبكة Windows 10 Pro أو Enterprise، برنامج الحماية من الفيروسات من Microsoft Defender الحماية في الوقت الحقيقي.

<br>

****

|Windows الإصدار|برنامج الحماية من الفيروسات من Microsoft Defender|
|---|---|
|Windows 10 1709 أو إصدار أحدث <p> Windows 11 <p> Windows Server 1803 أو أي وقت لاحق|[برنامج الحماية من الفيروسات من Microsoft Defender تمكين الحماية في الوقت الحقيقي](configure-real-time-protection-microsoft-defender-antivirus.md) والحماية التي [](enable-cloud-protection-microsoft-defender-antivirus.md) يتم تسليمها من السحابة|
|

بعد تمكين الخدمات، قد تحتاج إلى تكوين الشبكة أو جدار الحماية للسماح للاتصالات بين الخدمات وأجهزتك (يشار إليها أيضا بنقاط النهاية).

- `.smartscreen.microsoft.com`
- `.smartscreen-prod.microsoft.com`

## <a name="configuring-network-protection"></a>تكوين حماية الشبكة

لمزيد من المعلومات حول كيفية تمكين حماية الشبكة، راجع **[تمكين حماية الشبكة](enable-network-protection.md)**. استخدم نهج المجموعة أو PowerShell أو MDM CSPs لتمكين حماية الشبكة وإدارتها في الشبكة.

## <a name="viewing-network-protection-events"></a>عرض أحداث حماية الشبكة

تعمل حماية الشبكة بشكل أفضل مع [Microsoft Defender لنقطة](microsoft-defender-endpoint.md) النهاية، مما يوفر لك تقارير مفصلة حول أحداث الحماية من استغلالها وكتلها كجزء من سيناريوهات [التحقيق في التنبيهات](investigate-alerts.md).

عندما تمنع حماية الشبكة الاتصال، يتم عرض إعلام من مركز الإجراءات. يمكن لفريق عمليات الأمان [تخصيص الإعلام](attack-surface-reduction-rules-deployment-implement.md#customize-attack-surface-reduction-rules) باستخدام تفاصيل المؤسسة ومعلومات الاتصال بها. بالإضافة إلى ذلك، يمكن تمكين قواعد الحد من الهجمات الفردية وتخصيصها لتتناسب مع أساليب معينة للمراقبة.

يمكنك أيضا استخدام [وضع التدقيق](audit-windows-defender.md) لتقييم كيفية تأثير حماية الشبكة على مؤسستك إذا تم تمكينها.

## <a name="review-network-protection-events-in-the-microsoft-365-defender-portal"></a>مراجعة أحداث حماية الشبكة في مدخل Microsoft 365 Defender

يوفر Microsoft Defender ل Endpoint تقارير تفصيلية حول الأحداث والحظر كجزء من [سيناريوهات التحقيق في التنبيهات الخاصة به](investigate-alerts.md). يمكنك عرض هذه التفاصيل في Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)) في قائمة انتظار التنبيهات [أو باستخدام](review-alerts.md) [الصيد المتقدم](advanced-hunting-overview.md). إذا كنت [تستخدم وضع التدقيق](audit-windows-defender.md)، يمكنك استخدام البحث المتقدم لمعرفة كيف ستؤثر إعدادات حماية الشبكة على بيئتك إذا تم تمكينها.

فيما يلي استعلام مثال للصيد المتقدم:

```kusto
DeviceNetworkEvents
|where ActionType in ('ExploitGuardNetworkProtectionAudited','ExploitGuardNetworkProtectionBlocked', 'ConnectionSuccess')
```

## <a name="review-network-protection-events-in-windows-event-viewer"></a>مراجعة أحداث حماية الشبكة في Windows الحدث

يمكنك مراجعة سجل Windows الأحداث لرؤية الأحداث التي يتم إنشاؤها عند حظر (أو تدقيق) الوصول إلى IP أو مجال ضار:

1. [انسخ XML مباشرة](event-views.md).

2. حدد **موافق**.

ينشئ هذا الإجراء طريقة عرض مخصصة تقوم بالتصفية لإظهار الأحداث التالية المرتبطة بحماية الشبكة فقط:

<br>

****

|"معرّف الحدث"|الوصف|
|---|---|
|5007|حدث عند تغيير الإعدادات|
|1125|حدث عند تشغيل حماية الشبكة في وضع التدقيق|
|1126|حدث عند تشغيل حماية الشبكة في وضع الحظر|
|

## <a name="network-protection-and-the-tcp-three-way-handshake"></a>حماية الشبكة ومصافحة TCP ثلاثية

باستخدام حماية الشبكة، يتم تحديد ما إذا كنت تريد السماح بالوصول إلى موقع أو حظره بعد إكمال عملية المصافحة ثلاثية الطرق [عبر TCP/IP](/troubleshoot/windows-server/networking/three-way-handshake-via-tcpip). وبالتالي، عندما يتم `ConnectionSuccess` `NetworkConnectionEvents` حظر الموقع بواسطة حماية الشبكة، قد ترى نوع إجراء ضمن في مدخل Microsoft 365 Defender، على الرغم من أنه تم حظر الموقع فعليا. `NetworkConnectionEvents` يتم التقارير من طبقة TCP، وليس من حماية الشبكة. بعد اكتمال عملية المصافحة ثلاثية الأشكال، يتم السماح بالوصول إلى الموقع أو حظره بواسطة حماية الشبكة.

فيما يلي مثال على كيفية عمل ذلك:

1. لنفترض أن المستخدم يحاول الوصول إلى موقع ويب على جهازه. ويحدث أن يكون الموقع مستضافا على مجال خطر، ويجب حظره بواسطة حماية الشبكة.  

2. تبدأ عملية المصافحة ثلاثية الأشكال عبر TCP/IP. قبل اكتمال الإجراء، `NetworkConnectionEvents` يتم تسجيل إجراء، كما `ActionType` يتم إدراجه ك `ConnectionSuccess`. ومع ذلك، بمجرد اكتمال عملية الاتصال باليد ثلاثية، تمنع حماية الشبكة الوصول إلى الموقع. يحدث كل هذا بسرعة كبيرة. تحدث عملية مماثلة مع Microsoft Defender SmartScreen، [](/windows/security/threat-protection/microsoft-defender-smartscreen/microsoft-defender-smartscreen-overview)وعند اكتمال عملية المصافحة ثلاثية الاتجاه يتم تحديدها، أما الوصول إلى موقع ما يتم حظره أو السماح به.

3. في Microsoft 365 Defender، يتم إدراج تنبيه في [قائمة انتظار التنبيهات](alerts-queue.md). تتضمن تفاصيل هذا التنبيه كلا من `NetworkConnectionEvents` و `AlertEvents`. يمكنك أن ترى أن الموقع تم حظره `NetworkConnectionEvents` ، على الرغم من أن لديك أيضا عنصر يحتوي على ActionType الخاص ب `ConnectionSuccess`.

## <a name="considerations-for-windows-virtual-desktop-running-windows-10-enterprise-multi-session"></a>اعتبارات استخدام Windows سطح المكتب الظاهري Windows 10 Enterprise جلسات عمل متعددة

نظرا لطبيعة المستخدمين المتعددين Windows 10 Enterprise، ضع النقاط التالية في الاعتبار:

1. حماية الشبكة هي ميزة على مستوى الجهاز ولا يمكن استهدافها لجلسات مستخدم معينة.

2. كما أن نهج تصفية محتوى ويب عريضة أيضا على الجهاز.

3. إذا كنت بحاجة إلى التمييز بين مجموعات المستخدمين، فنظر في إنشاء مجموعات مضيفين Windows سطح مكتب ظاهرية وواجبات منفصلة.

4. اختبر حماية الشبكة في وضع التدقيق لتقييم سلوكها قبل طرحها.

5. يمكنك إعادة حجم النشر إذا كان لديك عدد كبير من المستخدمين أو عدد كبير من جلسات العمل متعددة المستخدمين.

### <a name="alternative-option-for-network-protection"></a>خيار بديل لحماية الشبكة

بالنسبة Windows 10 Enterprise المتعددة جلسات العمل 1909 وما فوقها، المستخدمة في Windows Virtual Desktop على Azure، يمكن تمكين حماية الشبكة ل Microsoft Edge باستخدام الأسلوب التالي:

1. استخدم [تشغيل حماية الشبكة](enable-network-protection.md) واتبع الإرشادات لتطبيق نهجك.

2. تنفيذ الأمر PowerShell التالي: `Set-MpPreference -AllowNetworkProtectionOnWinServer 1`

## <a name="network-protection-troubleshooting"></a>استكشاف الأخطاء وإصلاحها في حماية الشبكة

نظرا لبيئة تشغيل حماية الشبكة، قد لا تتمكن Microsoft من الكشف عن إعدادات وكيل نظام التشغيل. في بعض الحالات، يتعذر على عملاء حماية الشبكة الوصول إلى خدمة السحابة. لحل مشكلة الاتصال، يجب على العملاء الذين تم منحهم تراخيص E5 تكوين أحد مفاتيح التسجيل التالية:

```console
reg add "HKLM\Software\Microsoft\Windows Defender" /v ProxyServer /d "<proxy IP address: Port>" /f
reg add "HKLM\Software\Microsoft\Windows Defender" /v ProxyPacUrl /d "<Proxy PAC url>" /f

```

## <a name="see-also"></a>راجع أيضًا

- [تقييم حماية](evaluate-network-protection.md) | قم بتنفيذ سيناريو سريع يوضح كيفية عمل الميزة، والأحداث التي سيتم إنشاؤها عادة.
- [تمكين حماية](enable-network-protection.md) | استخدم نهج المجموعة أو PowerShell أو MDM CSPs لتمكين حماية الشبكة وإدارتها في الشبكة.
- [تكوين إمكانات الحد من سطح الهجوم في Microsoft Intune](/mem/intune/protect/endpoint-security-asr-policy)
