---
title: استخدام قواعد الحد من سطح الهجوم لمنع إصابة البرامج الضارة
description: يمكن لقواعد تقليل مساحة الهجوم المساعدة في منع استغلال التطبيقات والبرامج النصية لإصابة الأجهزة بالبرامج الضارة.
keywords: قواعد الحد من سطح الهجوم، asr، hips، نظام منع اقتحام المضيف، قواعد الحماية، مكافحة استغلال، مكافحة استغلال، استغلال، منع الإصابة، Microsoft Defender ل Endpoint
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
ms.collection: m365initiative-m365-defender
ms.date: 1/18/2022
ms.openlocfilehash: 3f3daaa068f067c8d4ffbbf40a4d8ba1d32d04b9
ms.sourcegitcommit: 6e90baef421ae06fd790b0453d3bdbf624b7f9c0
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 02/12/2022
ms.locfileid: "63570742"
---
# <a name="attack-surface-reduction-rules-overview"></a>نظرة عامة حول قواعد الحد من سطح الهجوم

**ينطبق على:**

- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

## <a name="why-attack-surface-reduction-rules-are-important"></a>سبب أهمية قواعد الحد من سطح الهجوم

يتضمن سطح الهجوم الخاص مؤسستك كل الأماكن التي يمكن أن يعرض فيها مهاجم أجهزة مؤسستك أو شبكاتها للخطر. يعني تقليل سطح الهجوم حماية أجهزة مؤسستك وشبكة الاتصال بها، مما يترك للمهاجمين طرقا أقل لتنفيذ الهجمات. يمكن أن يساعدك تكوين قواعد تقليل مساحة الهجوم في Microsoft Defender for Endpoint!

تستهدف قواعد الحد من سطح الهجوم سلوكيات برامج معينة، مثل:

- بدء تشغيل الملفات القابلة للتنفيذ والنصية التي تحاول تنزيل الملفات أو تشغيلها
- تشغيل البرامج النصية غير المريبة أو غير ذلك من البرامج النصية المريبة
- سلوكيات الأداء التي لا تبدأها التطبيقات عادة أثناء العمل العادي يوميا

في بعض الأحيان، يتم رؤية سلوكيات البرامج هذه في التطبيقات المشروعة. ومع ذلك، غالبا ما تعتبر هذه السلوكيات مخاطرة لأنها غالبا ما يتم إساءة استخدامها من قبل المهاجمين من خلال البرامج الضارة. قد تقيد قواعد الحد من سطح الهجوم السلوكيات الضارة المستندة إلى البرامج وتساعد على الحفاظ على أمان مؤسستك.

لمزيد من المعلومات حول تكوين قواعد الحد من سطح الهجوم، راجع [تمكين قواعد الحد من سطح الهجوم](enable-attack-surface-reduction.md).

## <a name="assess-rule-impact-before-deployment"></a>تقييم تأثير القاعدة قبل النشر

يمكنك تقييم كيفية تأثير قاعدة تقليل مساحة الهجوم على الشبكة عن طريق فتح توصية الأمان لهذه [القاعدة في إدارة المخاطر والثغرات الأمنية](/windows/security/threat-protection/#tvm).

:::image type="content" source="images/asrrecommendation.png" alt-text="Reco الأمان لقاعدة الحد من سطح الهجوم.":::

في جزء تفاصيل التوصية، تحقق من تأثير المستخدم لتحديد النسبة المئوية لأجهزتك التي يمكنها قبول نهج جديد لتمكين القاعدة في وضع الحظر دون التأثير سلبا على الإنتاجية.

راجع [المتطلبات](enable-attack-surface-reduction.md#requirements) في مقالة "تمكين قواعد الحد من الهجمات" للحصول على معلومات حول أنظمة التشغيل المعتمدة ومعلومات المتطلبات الإضافية.

## <a name="audit-mode-for-evaluation"></a>وضع التدقيق للتقييم

استخدم [وضع التدقيق](audit-windows-defender.md) لتقييم كيفية تأثير قواعد تقليل مساحة الهجوم على مؤسستك إذا تم تمكينها. تشغيل كافة القواعد في وضع التدقيق أولا حتى تتمكن من فهم كيفية تأثيرها على تطبيقات خط العمل. العديد من تطبيقات خط العمل مكتوبة بمخاوف أمنية محدودة، وقد تقوم بتنفيذ المهام بطرق تبدو مماثلة للبرامج الضارة. من خلال مراقبة بيانات التدقيق [وإضافة استثناءات](enable-attack-surface-reduction.md#exclude-files-and-folders-from-asr-rules) للتطبيقات الضرورية، يمكنك نشر قواعد تقليل مساحة الهجوم دون تقليل الإنتاجية.

## <a name="warn-mode-for-users"></a>وضع التحذير للمستخدمين

(**جديد**!) قبل قدرات وضع التحذير، كان من الممكن تعيين قواعد تقليل مساحة الهجوم التي تم تمكينها إما إلى وضع التدقيق أو وضع الحظر. باستخدام وضع التحذير الجديد، عندما يتم حظر المحتوى بواسطة قاعدة تقليل مساحة الهجوم، يرى المستخدمون مربع حوار يشير إلى أن المحتوى تم حظره. كما يوفر مربع الحوار للمستخدم خيار إلغاء حظر المحتوى. يمكن للمستخدم بعد ذلك إعادة محاولة إجراءه، وتكتمل العملية. عندما يقوم مستخدم ب إلغاء حظر المحتوى، يظل المحتوى بدون حظر لمدة 24 ساعة، ثم حظر السير الذاتية.

يساعد وضع التحذير مؤسستك على وضع قواعد الحد من الهجمات دون منع المستخدمين من الوصول إلى المحتوى الذي يحتاجون إليه لتنفيذ مهامهم.

### <a name="requirements-for-warn-mode-to-work"></a>متطلبات عمل وضع التحذير

يتم دعم وضع التحذير على الأجهزة التي تعمل بالإصدارات التالية من Windows:

- [الإصدار 1809 من Windows 10](/windows/whats-new/whats-new-windows-10-version-1809) أو أي وقت لاحق
- Windows 11
- [Windows Server، الإصدار 1809 أو](/windows-server/get-started/whats-new-in-windows-server-1809) الإصدارات الأحدث

برنامج الحماية من الفيروسات من Microsoft Defender أن يكون قيد التشغيل مع الحماية في الوقت الحقيقي في [الوضع النشط](/windows/security/threat-protection/microsoft-defender-antivirus/microsoft-defender-antivirus-compatibility#functionality-and-features-available-in-each-state).

تأكد أيضا من [برنامج الحماية من الفيروسات من Microsoft Defender](/windows/security/threat-protection/microsoft-defender-antivirus/manage-updates-baselines-microsoft-defender-antivirus#monthly-platform-and-engine-versions) البرامج الضارة وتحديثات البرامج الضارة.

- الحد الأدنى لمتطلبات إصدار النظام الأساسي: `4.18.2008.9`
- الحد الأدنى لمتطلبات إصدار المحرك: `1.1.17400.5`

للحصول على مزيد من المعلومات والحصول على التحديثات، راجع تحديث النظام الأساسي لمكافحة البرامج الضارة [ل Microsoft Defender](https://support.microsoft.com/help/4052623/update-for-microsoft-defender-antimalware-platform).

### <a name="cases-where-warn-mode-is-not-supported"></a>الحالات التي يكون فيها وضع التحذير غير معتمد

لا يدعم وضع التحذير ثلاث قواعد للحد من سطح الهجوم عند تكوينها في إدارة نقاط النهاية من Microsoft. (إذا كنت تستخدم "نهج المجموعة" لتكوين قواعد الحد من سطح الهجوم، يكون وضع التحذير معتمدا.) القواعد الثلاث التي لا تدعم وضع التحذير عند تكوينها في إدارة نقاط النهاية من Microsoft هي كما يلي:

- [حظر JavaScript أو VBScript من بدء تشغيل المحتوى القابل للتنفيذ الذي تم](attack-surface-reduction-rules-reference.md#block-javascript-or-vbscript-from-launching-downloaded-executable-content) تنزيله (GUID `d3e037e1-3eb8-44c8-a917-57927947596d`)
- [حظر الثبات عبر اشتراك حدث WMI](attack-surface-reduction-rules-reference.md#block-persistence-through-wmi-event-subscription) (GUID `e6db77e5-3df2-4cf1-b95a-636979351e5b`)
- [استخدام حماية متقدمة من برامج الفدية](attack-surface-reduction-rules-reference.md#use-advanced-protection-against-ransomware) الضارة (GUID `c1db55ab-c21a-4637-bb3f-a12568109d35`)

كما أن وضع التحذير غير معتمد على الأجهزة التي تعمل بالإصدارات القديمة من Windows. في هذه الحالات، سيتم تشغيل قواعد تقليل مساحة الهجوم التي تم تكوينها للتشغيل في وضع التحذير في وضع الحظر.

## <a name="notifications-and-alerts"></a>الإعلامات والتنبيهات

كلما تم تشغيل قاعدة تقليل مساحة الهجوم، يتم عرض إعلام على الجهاز. يمكنك [تخصيص الإعلام بتفاصيل](attack-surface-reduction-rules-deployment-implement.md#customize-attack-surface-reduction-rules) الشركة ومعلومات الاتصال.

أيضا، عند تشغيل بعض قواعد الحد من سطح الهجوم، يتم إنشاء التنبيهات.

يمكن عرض الإعلامات وأي تنبيهات يتم إنشاؤها في Microsoft 365 Defender <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">المدخل</a>.

للحصول على تفاصيل محددة حول وظيفة الإعلام والتنبيه، راجع: [التنبيه](attack-surface-reduction-rules-reference.md#per-rule-alert-and-notification-details) لكل قاعدة وتفاصيل الإعلام، في المقالة مرجع قواعد تقليل **مساحة الهجوم**.

## <a name="advanced-hunting-and-attack-surface-reduction-events"></a>أحداث متقدمة للصيد والحد من سطح الهجوم

يمكنك استخدام الصيد المتقدم لعرض أحداث الحد من سطح الهجوم. لتسهيل حجم البيانات الواردة، يمكن عرض العمليات الفريدة فقط لكل ساعة باستخدام عمليات البحث المتقدمة. وقت حدث الحد من سطح الهجوم هو المرة الأولى التي يتم فيها رؤية الحدث في غضون ساعة.

على سبيل المثال، افترض أن حدث الحد من سطح الهجوم يقع على 10 أجهزة خلال الساعة 2:00 م. لنفترض أن الحدث الأول وقع في 2:15، والحدث الأخير في 2:45. باستخدام الصيد المتقدم، سترى مثيلا واحدا من هذا الحدث (على الرغم من أنه حدث بالفعل على 10 أجهزة)، وسوف يكون الوقت هو 2:15 م.

لمزيد من المعلومات حول الصيد المتقدم، راجع البحث بشكل استباقي عن [التهديدات المتعلقة بالصيد المتقدم](advanced-hunting-overview.md).

## <a name="attack-surface-reduction-features-across-windows-versions"></a>ميزات الحد من سطح الهجوم Windows الإصدارات

يمكنك تعيين قواعد تقليل مساحة الهجوم للأجهزة التي تقوم بتشغيل أي من الإصدارات والإصدارات التالية من Windows:

- Windows 10 Pro الإصدار [1709](/windows/whats-new/whats-new-windows-10-version-1709) أو الإصدارات الأحدث
- Windows 10 Enterprise الإصدار [1709 أو](/windows/whats-new/whats-new-windows-10-version-1709) الإصدارات الأحدث
- Windows Server، [الإصدار 1803 (قناة نصف سنوية)](/windows-server/get-started/whats-new-in-windows-server-1803) أو إصدار أحدث
- [Windows Server 2019](/windows-server/get-started-19/whats-new-19)
- [Windows Server 2016](/windows-server/get-started/whats-new-in-windows-server-2016)
- [Windows Server 2012 R2](/win32/srvnodes/what-s-new-for-windows-server-2012-r2)

  >[!NOTE]
  >Windows Server 2016 Windows Server 2012 R2 باستخدام الإرشادات الموجودة في [خوادم Windows Onboard](configure-server-endpoints.md#windows-server-2012-r2-and-windows-server-2016) لكي تعمل هذه الميزة.

على الرغم من أن قواعد تقليل مساحة الهجوم لا تتطلب Windows [E5](/windows/deployment/deploy-enterprise-licenses)، إذا كان لديك Windows E5، يمكنك الحصول على قدرات إدارة متقدمة. تتضمن الإمكانات المتقدمة - المتوفرة فقط في Windows E5 - ما يلي:

- عمليات المراقبة والتحليلات ومسير العمل المتوفرة في [Defender for Endpoint](microsoft-defender-endpoint.md)
- قدرات إعداد التقارير والتكوين في [Microsoft 365 Defender](/microsoft-365/security/defender/overview-security-center).

لا تتوفر هذه الإمكانات المتقدمة مع ترخيص Windows Professional أو Windows E3. ومع ذلك، إذا كان لديك هذه التراخيص، يمكنك استخدام "عارض الأحداث" برنامج الحماية من الفيروسات من Microsoft Defender لمراجعة أحداث قاعدة تقليل مساحة الهجوم.

## <a name="review-attack-surface-reduction-events-in-the-microsoft-365-defender-portal"></a>مراجعة أحداث الحد من سطح الهجوم في مدخل Microsoft 365 Defender الهجوم

يوفر Defender for Endpoint تقارير تفصيلية للأحداث والحظر كجزء من سيناريوهات التحقيق في التنبيهات.

يمكنك الاستعلام عن بيانات Defender لنقطة [النهاية في](microsoft-defender-endpoint.md) Microsoft 365 Defender باستخدام [البحث المتقدم](/microsoft-365/security/defender/advanced-hunting-query-language). 

فيما يلي مثال على استعلام:

```kusto
DeviceEvents
| where ActionType startswith 'Asr'
```

## <a name="review-attack-surface-reduction-events-in-windows-event-viewer"></a>مراجعة أحداث الحد من سطح الهجوم في Windows الحدث

يمكنك مراجعة سجل الأحداث Windows لعرض الأحداث التي تم إنشاؤها بواسطة قواعد تقليل مساحة الهجوم:

1. قم [بتنزيل حزمة](https://aka.ms/mp7z2w) التقييم واستخراج الملف *cfa-events.xmlإلى موقع* يمكن الوصول إليه بسهولة على الجهاز.

2. أدخل الكلمات، *عارض* الأحداث، في قائمة البدء لفتح Windows الحدث.

3. ضمن **إجراءات**، حدد **استيراد طريقة عرض مخصصة...**.

4. حدد *الملفcfa-events.xmlمن* حيث تم استخراجه. بدلا من ذلك [، انسخ XML مباشرة](event-views.md).

5. حدد **موافق**.

يمكنك إنشاء طريقة عرض مخصصة تقوم بتصفية الأحداث لإظهار الأحداث التالية فقط، وكلها مرتبطة بالوصول المتحكم به إلى المجلدات:

|"معرّف الحدث"|الوصف|
|---|---|
|5007|حدث عند تغيير الإعدادات|
|1121|حدث عند تشغيل القاعدة في وضع الحظر|
|1122|حدث عند تشغيل القاعدة في وضع التدقيق|

يتم إنشاء "إصدار المحرك" المدرج للأحداث الخاصة بخفض مساحة الهجوم في سجل الأحداث بواسطة Defender for Endpoint، وليس بواسطة نظام التشغيل. يتم دمج Defender for Endpoint مع Windows 10 Windows 11، لذلك تعمل هذه الميزة على جميع الأجهزة التي Windows 10 أو Windows 11 تثبيتها.
