---
title: استخدام قواعد تقليل الأجزاء المعرضة للهجوم لمنع إصابة البرامج الضارة
description: يمكن أن تساعد قواعد تقليل الأجزاء المعرضة للهجوم في منع المهاجمات من استخدام التطبيقات والبرامج النصية لإصابة الأجهزة بالبرامج الضارة.
keywords: قواعد تقليل الأجزاء المعرضة للهجوم، asr، hips، نظام منع الاختراق المضيف، قواعد الحماية، مكافحة الاستغلال، مكافحة الاستغلال، الاستغلال، منع العدوى، Microsoft Defender لنقطة النهاية
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
audience: ITPro
author: jweston-1
ms.author: v-jweston
ms.reviewer: oogunrinde, sugamar
manager: dansimp
ms.custom:
- asr
- admindeeplinkDEFENDER
ms.technology: mde
ms.topic: article
ms.collection:
- m365initiative-m365-defender
- M365-security-compliance
ms.date: 1/18/2022
ms.openlocfilehash: a1ae7d53ac69b4756417704b4938ff4fb41f9e41
ms.sourcegitcommit: ebbe8713297675db5dcb3e0d9c3ae5e746b99196
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 05/14/2022
ms.locfileid: "65418795"
---
# <a name="attack-surface-reduction-rules-overview"></a>نظرة عامة على قواعد تقليل الأجزاء المعرضة للهجوم

**ينطبق على:**

- [Defender for Endpoint الخطة 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)
- برنامج الحماية من الفيروسات من Microsoft Defender

**الأنظمة الأساسية**
- بالنسبة لنظام التشغيل

## <a name="why-attack-surface-reduction-rules-are-important"></a>لماذا قواعد تقليل الأجزاء المعرضة للهجوم مهمة

يتضمن سطح الهجوم الخاص بمؤسستك جميع الأماكن التي يمكن للمهاجم فيها اختراق أجهزة مؤسستك أو شبكاتها. يعني تقليل سطح الهجوم حماية أجهزة مؤسستك وشبكتها، ما يترك للمهاجمين طرقا أقل لتنفيذ الهجمات. يمكن أن يساعد تكوين قواعد تقليل الأجزاء المعرضة للهجوم في Microsoft Defender لنقطة النهاية!

تستهدف قواعد تقليل الأجزاء المعرضة للهجوم بعض سلوكيات البرامج، مثل:

- تشغيل الملفات والبرامج النصية القابلة للتنفيذ التي تحاول تنزيل الملفات أو تشغيلها
- تشغيل البرامج النصية المشوشة أو المشبوهة
- تنفيذ السلوكيات التي لا تبدأها التطبيقات عادة أثناء العمل اليومي العادي

ينظر إلى مثل هذه السلوكيات البرمجية في بعض الأحيان في التطبيقات المشروعة. ومع ذلك، غالبا ما تعتبر هذه السلوكيات محفوفة بالمخاطر لأنها عادة ما يتم إساءة استخدامها من قبل المهاجمين من خلال البرامج الضارة. يمكن لقواعد تقليل الأجزاء المعرضة للهجوم تقييد السلوكيات المحفوفة بالمخاطر المستندة إلى البرامج والمساعدة في الحفاظ على أمان مؤسستك.

لمزيد من المعلومات حول تكوين قواعد تقليل الأجزاء المعرضة للهجوم، راجع [تمكين قواعد تقليل الأجزاء المعرضة للهجوم](enable-attack-surface-reduction.md).

## <a name="assess-rule-impact-before-deployment"></a>تقييم تأثير القاعدة قبل النشر

يمكنك تقييم كيفية تأثير قاعدة تقليل الأجزاء المعرضة للهجوم على شبكتك عن طريق فتح توصية الأمان لتلك القاعدة في [إدارة المخاطر والثغرات الأمنية](/windows/security/threat-protection/#tvm).

:::image type="content" source="images/asrrecommendation.png" alt-text="توصية ASR" lightbox="images/asrrecommendation.png":::

في جزء تفاصيل التوصية، تحقق من تأثير المستخدم لتحديد النسبة المئوية لأجهزتك التي يمكنها قبول نهج جديد يتيح القاعدة في وضع الحظر دون التأثير سلبا على الإنتاجية.

راجع [المتطلبات](enable-attack-surface-reduction.md#requirements) في مقالة "تمكين قواعد تقليل الأجزاء المعرضة للهجوم" للحصول على معلومات حول أنظمة التشغيل المدعومة ومعلومات المتطلبات الإضافية.

## <a name="audit-mode-for-evaluation"></a>وضع التدقيق للتقييم

استخدم [وضع التدقيق](audit-windows-defender.md) لتقييم كيفية تأثير قواعد تقليل الأجزاء المعرضة للهجوم على مؤسستك إذا تم تمكينها. قم بتشغيل جميع القواعد في وضع التدقيق أولا حتى تتمكن من فهم كيفية تأثيرها على تطبيقات خط العمل. تتم كتابة العديد من تطبيقات خط العمل مع مخاوف أمنية محدودة، وقد تؤدي المهام بطرق تبدو مشابهة للبرامج الضارة. من خلال مراقبة بيانات التدقيق [وإضافة استثناءات](enable-attack-surface-reduction.md#exclude-files-and-folders-from-asr-rules) للتطبيقات الضرورية، يمكنك نشر قواعد تقليل الأجزاء المعرضة للهجوم دون تقليل الإنتاجية.

## <a name="warn-mode-for-users"></a>وضع التحذير للمستخدمين

(**جديد**!) قبل قدرات وضع التحذير، يمكن تعيين قواعد تقليل الأجزاء المعرضة للهجوم التي تم تمكينها إلى وضع التدقيق أو وضع الحظر. باستخدام وضع التحذير الجديد، كلما تم حظر المحتوى بواسطة قاعدة تقليل الأجزاء المعرضة للهجوم، يرى المستخدمون مربع حوار يشير إلى حظر المحتوى. كما يوفر مربع الحوار للمستخدم خيارا لإلغاء حظر المحتوى. يمكن للمستخدم بعد ذلك إعادة محاولة إجراءه، وإكمال العملية. عندما يقوم مستخدم بإلغاء حظر المحتوى، يظل المحتوى غير محظور لمدة 24 ساعة، ثم حظر السير الذاتية.

يساعد وضع التحذير مؤسستك على تطبيق قواعد تقليل الأجزاء المعرضة للهجوم دون منع المستخدمين من الوصول إلى المحتوى الذي يحتاجون إليه لتنفيذ مهامهم.

### <a name="requirements-for-warn-mode-to-work"></a>متطلبات عمل وضع التحذير

يتم دعم وضع التحذير على الأجهزة التي تعمل بالإصدارات التالية من Windows:

- [الإصدار 1809 من Windows 10](/windows/whats-new/whats-new-windows-10-version-1809) أو أحدث
- Windows 11
- [Windows Server، الإصدار 1809](/windows-server/get-started/whats-new-in-windows-server-1809) أو أحدث

يجب تشغيل برنامج الحماية من الفيروسات من Microsoft Defender مع حماية في الوقت الحقيقي في [الوضع النشط](/windows/security/threat-protection/microsoft-defender-antivirus/microsoft-defender-antivirus-compatibility#functionality-and-features-available-in-each-state).

تأكد أيضا من تثبيت [تحديثات برنامج الحماية من الفيروسات من Microsoft Defender ومكافحة البرامج الضارة](/windows/security/threat-protection/microsoft-defender-antivirus/manage-updates-baselines-microsoft-defender-antivirus#monthly-platform-and-engine-versions).

- الحد الأدنى لمتطلبات إصدار النظام الأساسي: `4.18.2008.9`
- الحد الأدنى لمتطلبات إصدار المحرك: `1.1.17400.5`

للحصول على مزيد من المعلومات والحصول على التحديثات، راجع [تحديث النظام الأساسي لمكافحة البرامج الضارة من Microsoft Defender](https://support.microsoft.com/help/4052623/update-for-microsoft-defender-antimalware-platform).

### <a name="cases-where-warn-mode-is-not-supported"></a>الحالات التي لا يكون فيها وضع التحذير معتمدا

لا يدعم وضع التحذير ثلاث قواعد لتقليل الأجزاء المعرضة للهجوم عند تكوينها في إدارة نقاط النهاية من Microsoft. (إذا كنت تستخدم نهج المجموعة لتكوين قواعد تقليل الأجزاء المعرضة للهجوم، يتم دعم وضع التحذير.) القواعد الثلاث التي لا تدعم وضع التحذير عند تكوينها في إدارة نقاط النهاية من Microsoft هي كما يلي:

- [حظر JavaScript أو VBScript من بدء تشغيل المحتوى القابل للتنفيذ الذي تم تنزيله](attack-surface-reduction-rules-reference.md#block-javascript-or-vbscript-from-launching-downloaded-executable-content) (GUID `d3e037e1-3eb8-44c8-a917-57927947596d`)
- [حظر الثبات من خلال اشتراك حدث WMI](attack-surface-reduction-rules-reference.md#block-persistence-through-wmi-event-subscription) (GUID `e6db77e5-3df2-4cf1-b95a-636979351e5b`)
- [استخدام الحماية المتقدمة من برامج الفدية الضارة](attack-surface-reduction-rules-reference.md#use-advanced-protection-against-ransomware) (GUID `c1db55ab-c21a-4637-bb3f-a12568109d35`)

كما أن وضع التحذير غير مدعوم على الأجهزة التي تعمل بإصدارات قديمة من Windows. في هذه الحالات، سيتم تشغيل قواعد تقليل الأجزاء المعرضة للهجوم التي تم تكوينها للتشغيل في وضع التحذير في وضع الحظر.

## <a name="notifications-and-alerts"></a>الإعلامات والتنبيهات

كلما تم تشغيل قاعدة تقليل الأجزاء المعرضة للهجوم، يتم عرض إعلام على الجهاز. يمكنك [تخصيص الإعلام](attack-surface-reduction-rules-deployment-implement.md#customize-attack-surface-reduction-rules) باستخدام تفاصيل الشركة ومعلومات الاتصال.

أيضا، عند تشغيل بعض قواعد تقليل الأجزاء المعرضة للهجوم، يتم إنشاء التنبيهات.

يمكن عرض الإعلامات وأي تنبيهات يتم إنشاؤها في <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">مدخل Microsoft 365 Defender</a>.

للحصول على تفاصيل محددة حول وظيفة الإعلام والتنبيه، راجع: [حسب تنبيه القاعدة وتفاصيل الإعلام](attack-surface-reduction-rules-reference.md#per-rule-alert-and-notification-details)، في مقالة **مرجع قواعد تقليل الأجزاء المعرضة للهجوم**.

## <a name="advanced-hunting-and-attack-surface-reduction-events"></a>التتبع المتقدم وأحداث تقليل الأجزاء المعرضة للهجوم

يمكنك استخدام التتبع المتقدم لعرض أحداث تقليل الأجزاء المعرضة للهجوم. لتبسيط حجم البيانات الواردة، يمكن عرض العمليات الفريدة فقط لكل ساعة مع التتبع المتقدم. وقت حدث تقليل الأجزاء المعرضة للهجوم هو المرة الأولى التي يظهر فيها هذا الحدث في غضون ساعة.

على سبيل المثال، افترض أن حدث تقليل الأجزاء المعرضة للهجوم يحدث على 10 أجهزة خلال الساعة 2:00 مساء. لنفترض أن الحدث الأول حدث في الساعة 2:15، وآخر حدث في الساعة 2:45. مع التتبع المتقدم، سترى مثيلا واحدا من هذا الحدث (على الرغم من أنه حدث بالفعل على 10 أجهزة)، وسيكون الطابع الزمني الخاص به 2:15 م.

لمزيد من المعلومات حول التتبع المتقدم، راجع [البحث بشكل استباقي عن التهديدات باستخدام التتبع المتقدم](advanced-hunting-overview.md).

## <a name="attack-surface-reduction-features-across-windows-versions"></a>ميزات تقليل الأجزاء المعرضة للهجوم عبر إصدارات Windows

يمكنك تعيين قواعد تقليل الأجزاء المعرضة للهجوم للأجهزة التي تقوم بتشغيل أي من الإصدارات والإصدارات التالية من Windows:

- Windows 10 Pro، [الإصدار 1709](/windows/whats-new/whats-new-windows-10-version-1709) أو الإصدارات الأحدث
- Windows 10 Enterprise، [الإصدار 1709](/windows/whats-new/whats-new-windows-10-version-1709) أو أحدث
- Windows Server أو [الإصدار 1803 (التحديث نصف السنوي)](/windows-server/get-started/whats-new-in-windows-server-1803) أو إصدار أحدث
- [Windows Server 2019](/windows-server/get-started-19/whats-new-19)
- [Windows Server 2016](/windows-server/get-started/whats-new-in-windows-server-2016)
- [Windows Server 2012 R2](/win32/srvnodes/what-s-new-for-windows-server-2012-r2)

  >[!NOTE]
  >يجب إلحاق Windows Server 2016 وserver Windows 2012 R2 باستخدام الإرشادات الموجودة في [خوادم Windows](configure-server-endpoints.md#windows-server-2012-r2-and-windows-server-2016) المحلية لكي تعمل هذه الميزة.

على الرغم من أن قواعد تقليل الأجزاء المعرضة للهجوم لا تتطلب [ترخيص E5 Windows](/windows/deployment/deploy-enterprise-licenses)، إذا كان لديك Windows E5، فستحصل على قدرات إدارة متقدمة. تشمل القدرات المتقدمة - المتوفرة فقط في Windows E5 - ما يلي:

- المراقبة والتحليلات ومسير العمل المتوفرة في [Defender لنقطة النهاية](microsoft-defender-endpoint.md)
- قدرات إعداد التقارير والتكوين في [Microsoft 365 Defender](/microsoft-365/security/defender/overview-security-center).

لا تتوفر هذه القدرات المتقدمة مع ترخيص Windows Professional أو Windows E3. ومع ذلك، إذا كان لديك هذه التراخيص، يمكنك استخدام عارض الأحداث وسجلات برنامج الحماية من الفيروسات من Microsoft Defender لمراجعة أحداث قاعدة تقليل الأجزاء المعرضة للهجوم.

## <a name="review-attack-surface-reduction-events-in-the-microsoft-365-defender-portal"></a>مراجعة أحداث تقليل الأجزاء المعرضة للهجوم في مدخل Microsoft 365 Defender

يوفر Defender لنقطة النهاية تقارير مفصلة للأحداث والكتل كجزء من سيناريوهات التحقيق في التنبيه.

يمكنك الاستعلام عن بيانات Defender لنقطة النهاية في [Microsoft 365 Defender](microsoft-defender-endpoint.md) باستخدام [التتبع المتقدم](/microsoft-365/security/defender/advanced-hunting-query-language). 

فيما يلي مثال للاستعلام:

```kusto
DeviceEvents
| where ActionType startswith 'Asr'
```

## <a name="review-attack-surface-reduction-events-in-windows-event-viewer"></a>مراجعة أحداث تقليل الأجزاء المعرضة للهجوم في Windows عارض الأحداث

يمكنك مراجعة سجل أحداث Windows لعرض الأحداث التي تم إنشاؤها بواسطة قواعد تقليل الأجزاء المعرضة للهجوم:

1. قم بتنزيل [حزمة التقييم](https://aka.ms/mp7z2w) واستخراج *الملفcfa-events.xml* إلى موقع يمكن الوصول إليه بسهولة على الجهاز.

2. أدخل الكلمات، *عارض الأحداث*، في قائمة البدء لفتح Windows عارض الأحداث.

3. ضمن **"إجراءات"**، حدد **"استيراد طريقة عرض مخصصة...**".

4. حدد *cfa-events.xml* الملف من حيث تم استخراجه. بدلا من ذلك، [انسخ XML مباشرة](event-views.md).

5. حدد **موافق**.

يمكنك إنشاء طريقة عرض مخصصة تقوم بتصفية الأحداث لإظهار الأحداث التالية فقط، وكلها مرتبطة بالوصول إلى المجلدات التي يتم التحكم فيها:

|معرف الحدث|الوصف|
|---|---|
|5007|حدث عند تغيير الإعدادات|
|1121|حدث عند تشغيل القاعدة في وضع الحظر|
|1122|حدث عند تشغيل القاعدة في وضع التدقيق|

يتم إنشاء "إصدار المحرك" المدرج لأحداث تقليل الأجزاء المعرضة للهجوم في سجل الأحداث بواسطة Defender لنقطة النهاية، وليس بواسطة نظام التشغيل. يتم دمج Defender لنقطة النهاية مع Windows 10 Windows 11، لذلك تعمل هذه الميزة على جميع الأجهزة التي تم تثبيت Windows 10 أو Windows 11 عليها.

> [!TIP]
> إذا كنت تبحث عن معلومات متعلقة بالحماية من الفيروسات للأنظمة الأساسية الأخرى، فراجع:
> - [تعيين تفضيلات Microsoft Defender لنقطة النهاية على نظام التشغيل macOS](mac-preferences.md)
> - [Microsoft Defender for Endpoint على Mac](microsoft-defender-endpoint-mac.md)
> - [إعدادات نهج برنامج الحماية من الفيروسات في macOS لبرنامج الحماية من الفيروسات من Microsoft Defender Antivirus for Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [تعيين تفضيلات Microsoft Defender لنقطة النهاية على Linux](linux-preferences.md)
> - [مشكلات الأداء في Microsoft Defender لنقطة النهاية على Linux](microsoft-defender-endpoint-linux.md)
> - [تكوين Defender for Endpoint على ميزات Android](android-configure.md)
> - [تكوين Microsoft Defender for Endpoint على ميزات iOS](ios-configure-features.md)
