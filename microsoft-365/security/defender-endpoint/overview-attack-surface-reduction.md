---
title: فهم واستخدام تقليل الأجزاء المعرضة للهجوم (ASR)
ms.reviewer: ''
description: تعرف على قدرات تقليل الأجزاء المعرضة للهجوم Microsoft Defender لنقطة النهاية.
keywords: asr، تقليل الأجزاء المعرضة للهجوم، قواعد تقليل الأجزاء المعرضة للهجوم، Microsoft Defender لنقطة النهاية، microsoft defender، مكافحة الفيروسات، av، windows defender
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
author: jweston-1
ms.author: v-jweston
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.custom: asr
ms.topic: conceptual
ms.technology: mde
ms.collection:
- m365initiative-m365-defender
- M365-security-compliance
ms.date: 05/16/2022
ms.openlocfilehash: 7c09db2138502ee8c1b491028308c56f23687a0d
ms.sourcegitcommit: 61b22df76e0f81e5ef11c587b129287886151c79
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/12/2022
ms.locfileid: "66748990"
---
# <a name="understand-and-use-attack-surface-reduction-capabilities"></a>فهم واستخدام قدرات تقليل الأجزاء المعرضة للهجوم

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**

- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)
- [الخطة 1 من Microsoft Defender لنقطة النهاية](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Defender for Endpoint الخطة 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- برنامج الحماية من الفيروسات من Microsoft Defender

**الأنظمة الأساسية**
- بالنسبة لنظام التشغيل

> [!TIP]
> هل تريد تجربة Microsoft Defender لنقطة النهاية؟ [التسجيل للحصول على إصدار تجريبي مجاني.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

الأسطح المعرضة للهجوم هي جميع الأماكن التي تكون فيها مؤسستك عرضة للتهديدات الإلكترونية والهجمات. يتضمن Defender لنقطة النهاية العديد من القدرات للمساعدة في تقليل أسطح الهجوم. شاهد الفيديو التالي لمعرفة المزيد حول تقليل الأجزاء المعرضة للهجوم.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4woug]

## <a name="configure-attack-surface-reduction-capabilities"></a>تكوين قدرات تقليل الأجزاء المعرضة للهجوم

لتكوين تقليل الأجزاء المعرضة للهجوم في بيئتك، اتبع الخطوات التالية:

1. [تمكين العزل المستند إلى الأجهزة ل Microsoft Edge](/windows/security/threat-protection/microsoft-defender-application-guard/install-md-app-guard).

2. [تمكين قواعد تقليل الأجزاء المعرضة للهجوم](attack-surface-reduction-rules-deployment.md)

3. تمكين التحكم في التطبيق.

   1. مراجعة النهج الأساسية في Windows. راجع [نهج قاعدة الأمثلة](/windows/security/threat-protection/windows-defender-application-control/example-wdac-base-policies).
   2. راجع [دليل تصميم Windows Defender Application Control](/windows/security/threat-protection/windows-defender-application-control/windows-defender-application-control-design-guide).
   3. راجع [نشر نهج التحكم في تطبيق Windows Defender (WDAC](/windows/security/threat-protection/windows-defender-application-control/windows-defender-application-control-deployment-guide)).

4. [تمكين الوصول المتحكم به إلى المجلد](enable-controlled-folders.md).

5. [حماية التخزين القابلة للإزالة](device-control-removable-storage-protection.md)

6. [تشغيل حماية الشبكة](enable-network-protection.md).

7. [تمكين نظرة عامة على حماية الويب](web-protection-overview.md)

8. [تمكين الحماية من الاستغلال](enable-exploit-protection.md).

9. إعداد جدار حماية الشبكة.

   1. احصل على نظرة عامة على [جدار حماية Windows Defender مع أمان متقدم](/windows/security/threat-protection/windows-firewall/windows-firewall-with-advanced-security).
   2. استخدم [دليل تصميم جدار حماية Windows Defender](/windows/security/threat-protection/windows-firewall/windows-firewall-with-advanced-security-design-guide) لتحديد كيفية تصميم نهج جدار الحماية.
   3. استخدم [دليل نشر جدار حماية Windows Defender](/windows/security/threat-protection/windows-firewall/windows-firewall-with-advanced-security-deployment-guide) لإعداد جدار حماية مؤسستك باستخدام أمان متقدم.

> [!TIP]
> في معظم الحالات، عند تكوين قدرات تقليل الأجزاء المعرضة للهجوم، يمكنك الاختيار من بين عدة أساليب:
>
> - Microsoft إدارة نقاط النهاية (التي تتضمن الآن Microsoft Intune ونقطة نهاية Microsoft Configuration Manager)
> - نهج المجموعة
> - PowerShell cmdlets

## <a name="test-attack-surface-reduction-in-microsoft-defender-for-endpoint"></a>اختبار تقليل الأجزاء المعرضة للهجوم في Microsoft Defender لنقطة النهاية

كجزء من فريق الأمان في مؤسستك، يمكنك تكوين قدرات تقليل الأجزاء المعرضة للهجوم للتشغيل في وضع التدقيق لمعرفة كيفية عملها. يمكنك تمكين ميزات أمان ASR التالية في وضع التدقيق:

- قواعد تقليل الأجزاء المعرضة للهجوم
- الحماية من استغلال
- حماية الشبكة
- والوصول المتحكم به إلى المجلد

يتيح لك وضع التدقيق رؤية سجل لما كان *سيحدث* إذا قمت بتمكين الميزة.

يمكنك تمكين وضع التدقيق عند اختبار كيفية عمل الميزات. يساعد تمكين وضع التدقيق للاختبار فقط على منع وضع التدقيق من التأثير على تطبيقات خط العمل. يمكنك أيضا الحصول على فكرة عن عدد محاولات تعديل الملفات المشبوهة التي تحدث على مدى فترة زمنية معينة.

لن تمنع الميزات أو تمنع تعديل التطبيقات أو البرامج النصية أو الملفات. ومع ذلك، سيقوم سجل أحداث Windows بتسجيل الأحداث كما لو كانت الميزات ممكنة بالكامل. باستخدام وضع التدقيق، يمكنك مراجعة سجل الأحداث لمعرفة تأثير الميزة إذا تم تمكينها.

للعثور على الإدخالات التي تم تدقيقها، انتقل إلى **Applications and Services** \> **Microsoft** \> **Windows** \> **Defender** \> **Operational**.

استخدم Defender لنقطة النهاية للحصول على تفاصيل أكبر لكل حدث. هذه التفاصيل مفيدة بشكل خاص للتحقيق في قواعد تقليل الأجزاء المعرضة للهجوم. يتيح لك استخدام وحدة تحكم Defender لنقطة النهاية [التحقق من المشكلات كجزء من المخطط الزمني للتنبيه وسيناريوهات التحقيق](investigate-alerts.md).

يمكنك تمكين وضع التدقيق باستخدام نهج المجموعة وPowerShell وموفري خدمات التكوين (CSPs).

| خيارات التدقيق | كيفية تمكين وضع التدقيق | كيفية عرض الأحداث |
|---|---|---|
| ينطبق التدقيق على جميع الأحداث | [تمكين الوصول إلى المجلدات الخاضعة للتحكم](enable-controlled-folders.md) | [أحداث الوصول إلى المجلدات التي يتم التحكم فيها](evaluate-controlled-folder-access.md#review-controlled-folder-access-events-in-windows-event-viewer) |
| ينطبق التدقيق على القواعد الفردية | [الخطوة 1: اختبار قواعد ASR باستخدام وضع التدقيق](attack-surface-reduction-rules-deployment-test.md#step-1-test-asr-rules-using-audit) | [الخطوة 2: فهم صفحة الإبلاغ عن قواعد تقليل الأجزاء المعرضة للهجوم](attack-surface-reduction-rules-deployment-test.md#step-2-understand-the-attack-surface-reduction-rules-reporting-page-in-the-microsoft-365-defender-portal) |
| ينطبق التدقيق على جميع الأحداث | [تمكين حماية الشبكة](enable-network-protection.md) | [أحداث حماية الشبكة](evaluate-network-protection.md#review-network-protection-events-in-windows-event-viewer) |
| ينطبق التدقيق على عمليات التخفيف الفردية | [تمكين الحماية من استغلال](enable-exploit-protection.md) | [أحداث الحماية من الاستغلال](exploit-protection.md#review-exploit-protection-events-in-windows-event-viewer) |

### <a name="attack-surface-reduction-asr-rules"></a>قواعد تقليل الأجزاء المعرضة للهجوم

يتم تعريف قواعد تقليل الأجزاء المعرضة للهجوم (ASR) مسبقا لتقوية الأسطح الهجومية الشائعة المعروفة. هناك العديد من الأساليب التي يمكنك استخدامها لتنفيذ قواعد تقليل الأجزاء المعرضة للهجوم. يتم توثيق الأسلوب المفضل في مواضيع نشر قواعد تقليل الأجزاء المعرضة للهجوم (ASR) التالية:

- [نظرة عامة على دليل نشر قواعد الحد من سطح الهجوم (ASR)](attack-surface-reduction-rules-deployment.md)
- [تخطيط نشر قواعد تقليل الأجزاء المعرضة للهجوم (ASR)](attack-surface-reduction-rules-deployment-plan.md)
- [اختبار قواعد تقليل الأجزاء المعرضة للهجوم (ASR)](attack-surface-reduction-rules-deployment-test.md)
- [تمكين قواعد تقليل الأجزاء المعرضة للهجوم (ASR)](attack-surface-reduction-rules-deployment-implement.md)
- [تشغيل قواعد تقليل الأجزاء المعرضة للهجوم (ASR)](attack-surface-reduction-rules-deployment-operationalize.md)

## <a name="view-attack-surface-reduction-events"></a>عرض أحداث تقليل الأجزاء المعرضة للهجوم

راجع أحداث تقليل الأجزاء المعرضة للهجوم في عارض الأحداث لمراقبة القواعد أو الإعدادات التي تعمل. يمكنك أيضا تحديد ما إذا كانت أي إعدادات "مزعجة" أو تؤثر على سير العمل اليومي.

تعد مراجعة الأحداث مفيدة عند تقييم الميزات. يمكنك تمكين وضع التدقيق للميزات أو الإعدادات، ثم مراجعة ما كان سيحدث إذا تم تمكينها بالكامل.

يسرد هذا القسم كافة الأحداث والميزة أو الإعدادات المقترنة بها، ويصف كيفية إنشاء طرق عرض مخصصة للتصفية إلى أحداث معينة.

احصل على تقارير مفصلة حول الأحداث والكتل والتحذيرات كجزء من أمن Windows إذا كان لديك اشتراك E5 واستخدم [Microsoft Defender لنقطة النهاية](microsoft-defender-endpoint.md).

### <a name="use-custom-views-to-review-attack-surface-reduction-capabilities"></a>استخدام طرق عرض مخصصة لمراجعة قدرات تقليل الأجزاء المعرضة للهجوم

إنشاء طرق عرض مخصصة في عارض الأحداث Windows لمشاهدة الأحداث فقط لإمكانيات وإعدادات معينة. أسهل طريقة هي استيراد طريقة عرض مخصصة كملف XML. يمكنك نسخ XML مباشرة من هذه الصفحة.

يمكنك أيضا الانتقال يدويا إلى منطقة الحدث التي تتوافق مع الميزة.

#### <a name="import-an-existing-xml-custom-view"></a>استيراد طريقة عرض XML مخصصة موجودة

1. أنشئ ملف .txt فارغا وانسخ XML لطريقة العرض المخصصة التي تريد استخدامها في ملف .txt. قم بذلك لكل طريقة عرض مخصصة تريد استخدامها. أعد تسمية الملفات كما يلي (تأكد من تغيير النوع من .txt إلى .xml):
    - طريقة عرض مخصصة لأحداث الوصول إلى المجلدات المتحكم فيها: *cfa-events.xml*
    - طريقة عرض مخصصة لأحداث الحماية من الاستغلال: *ep-events.xml*
    - عرض مخصص لأحداث تقليل الأجزاء المعرضة للهجوم: *asr-events.xml*
    - طريقة العرض المخصصة لأحداث الحماية/الشبكة: *np-events.xml*

2. اكتب **عارض الأحداث** في قائمة البدء وافتح **عارض الأحداث**.

3. تحديد **طريقة** **عرض استيراد الإجراء** \> المخصصة...

   > [!div class="mx-imgBorder"]
   > ![حركة تمييز "استيراد طريقة عرض مخصصة" على يمين نافذة "العارض الزوجي".](images/events-import.gif)

4. انتقل إلى المكان الذي قمت باستخراج ملف XML الخاص بطريقة العرض المخصصة التي تريدها وحدده.

5. حدد **"فتح**".

6. سينشئ طريقة عرض مخصصة تقوم بتصفية لإظهار الأحداث المتعلقة بتلك الميزة فقط.

#### <a name="copy-the-xml-directly"></a>نسخ XML مباشرة

1. اكتب **عارض الأحداث** في قائمة البدء وافتح **عارض الأحداث** Windows.

2. في اللوحة اليمنى، ضمن **"إجراءات"**، حدد **"إنشاء طريقة عرض مخصصة"...**

   > [!div class="mx-imgBorder"]
   > ![حركة تسلط الضوء على خيار إنشاء طريقة عرض مخصصة على نافذة عارض الأحداث.](images/events-create.gif)

3. انتقل إلى علامة التبويب XML وحدد **تحرير الاستعلام يدويا**. سترى تحذيرا يفيد بأنه لا يمكنك تحرير الاستعلام باستخدام علامة التبويب **"تصفية"** إذا كنت تستخدم خيار XML. حدد **"نعم**".

4. الصق رمز XML للميزة التي تريد تصفية الأحداث منها في قسم XML.

5. حدد **موافق**. حدد اسما لعامل التصفية. يؤدي ذلك إلى إنشاء طريقة عرض مخصصة تقوم بتصفية لإظهار الأحداث المتعلقة بهذه الميزة فقط.

#### <a name="xml-for-attack-surface-reduction-rule-events"></a>XML لأحداث قاعدة تقليل الأجزاء المعرضة للهجوم

```xml
<QueryList>
  <Query Id="0" Path="Microsoft-Windows-Windows Defender/Operational">
   <Select Path="Microsoft-Windows-Windows Defender/Operational">*[System[(EventID=1121 or EventID=1122 or EventID=5007)]]</Select>
   <Select Path="Microsoft-Windows-Windows Defender/WHC">*[System[(EventID=1121 or EventID=1122 or EventID=5007)]]</Select>
  </Query>
</QueryList>
```

#### <a name="xml-for-controlled-folder-access-events"></a>XML لأحداث الوصول إلى المجلدات التي يتم التحكم فيها

```xml
<QueryList>
  <Query Id="0" Path="Microsoft-Windows-Windows Defender/Operational">
   <Select Path="Microsoft-Windows-Windows Defender/Operational">*[System[(EventID=1123 or EventID=1124 or EventID=5007)]]</Select>
   <Select Path="Microsoft-Windows-Windows Defender/WHC">*[System[(EventID=1123 or EventID=1124 or EventID=5007)]]</Select>
  </Query>
</QueryList>
```

#### <a name="xml-for-exploit-protection-events"></a>XML لأحداث الحماية من الاستغلال

```xml
<QueryList>
  <Query Id="0" Path="Microsoft-Windows-Security-Mitigations/KernelMode">
   <Select Path="Microsoft-Windows-Security-Mitigations/KernelMode">*[System[Provider[@Name='Microsoft-Windows-Security-Mitigations' or @Name='Microsoft-Windows-WER-Diag' or @Name='Microsoft-Windows-Win32k' or @Name='Win32k'] and ( (EventID &gt;= 1 and EventID &lt;= 24)  or EventID=5 or EventID=260)]]</Select>
   <Select Path="Microsoft-Windows-Win32k/Concurrency">*[System[Provider[@Name='Microsoft-Windows-Security-Mitigations' or @Name='Microsoft-Windows-WER-Diag' or @Name='Microsoft-Windows-Win32k' or @Name='Win32k'] and ( (EventID &gt;= 1 and EventID &lt;= 24)  or EventID=5 or EventID=260)]]</Select>
   <Select Path="Microsoft-Windows-Win32k/Contention">*[System[Provider[@Name='Microsoft-Windows-Security-Mitigations' or @Name='Microsoft-Windows-WER-Diag' or @Name='Microsoft-Windows-Win32k' or @Name='Win32k'] and ( (EventID &gt;= 1 and EventID &lt;= 24)  or EventID=5 or EventID=260)]]</Select>
   <Select Path="Microsoft-Windows-Win32k/Messages">*[System[Provider[@Name='Microsoft-Windows-Security-Mitigations' or @Name='Microsoft-Windows-WER-Diag' or @Name='Microsoft-Windows-Win32k' or @Name='Win32k'] and ( (EventID &gt;= 1 and EventID &lt;= 24)  or EventID=5 or EventID=260)]]</Select>
   <Select Path="Microsoft-Windows-Win32k/Operational">*[System[Provider[@Name='Microsoft-Windows-Security-Mitigations' or @Name='Microsoft-Windows-WER-Diag' or @Name='Microsoft-Windows-Win32k' or @Name='Win32k'] and ( (EventID &gt;= 1 and EventID &lt;= 24)  or EventID=5 or EventID=260)]]</Select>
   <Select Path="Microsoft-Windows-Win32k/Power">*[System[Provider[@Name='Microsoft-Windows-Security-Mitigations' or @Name='Microsoft-Windows-WER-Diag' or @Name='Microsoft-Windows-Win32k' or @Name='Win32k'] and ( (EventID &gt;= 1 and EventID &lt;= 24)  or EventID=5 or EventID=260)]]</Select>
   <Select Path="Microsoft-Windows-Win32k/Render">*[System[Provider[@Name='Microsoft-Windows-Security-Mitigations' or @Name='Microsoft-Windows-WER-Diag' or @Name='Microsoft-Windows-Win32k' or @Name='Win32k'] and ( (EventID &gt;= 1 and EventID &lt;= 24)  or EventID=5 or EventID=260)]]</Select>
   <Select Path="Microsoft-Windows-Win32k/Tracing">*[System[Provider[@Name='Microsoft-Windows-Security-Mitigations' or @Name='Microsoft-Windows-WER-Diag' or @Name='Microsoft-Windows-Win32k' or @Name='Win32k'] and ( (EventID &gt;= 1 and EventID &lt;= 24)  or EventID=5 or EventID=260)]]</Select>
   <Select Path="Microsoft-Windows-Win32k/UIPI">*[System[Provider[@Name='Microsoft-Windows-Security-Mitigations' or @Name='Microsoft-Windows-WER-Diag' or @Name='Microsoft-Windows-Win32k' or @Name='Win32k'] and ( (EventID &gt;= 1 and EventID &lt;= 24)  or EventID=5 or EventID=260)]]</Select>
   <Select Path="System">*[System[Provider[@Name='Microsoft-Windows-Security-Mitigations' or @Name='Microsoft-Windows-WER-Diag' or @Name='Microsoft-Windows-Win32k' or @Name='Win32k'] and ( (EventID &gt;= 1 and EventID &lt;= 24)  or EventID=5 or EventID=260)]]</Select>
   <Select Path="Microsoft-Windows-Security-Mitigations/UserMode">*[System[Provider[@Name='Microsoft-Windows-Security-Mitigations' or @Name='Microsoft-Windows-WER-Diag' or @Name='Microsoft-Windows-Win32k' or @Name='Win32k'] and ( (EventID &gt;= 1 and EventID &lt;= 24)  or EventID=5 or EventID=260)]]</Select>
  </Query>
</QueryList>
```

#### <a name="xml-for-network-protection-events"></a>XML لأحداث حماية الشبكة

```xml
<QueryList>
 <Query Id="0" Path="Microsoft-Windows-Windows Defender/Operational">
  <Select Path="Microsoft-Windows-Windows Defender/Operational">*[System[(EventID=1125 or EventID=1126 or EventID=5007)]]</Select>
  <Select Path="Microsoft-Windows-Windows Defender/WHC">*[System[(EventID=1125 or EventID=1126 or EventID=5007)]]</Select>
 </Query>
</QueryList>
```

### <a name="list-of-attack-surface-reduction-events"></a>قائمة أحداث تقليل الأجزاء المعرضة للهجوم

تقع جميع أحداث تقليل الأجزاء المعرضة للهجوم ضمن سجلات **التطبيقات والخدمات > Microsoft > Windows** ثم المجلد أو الموفر كما هو مدرج في الجدول التالي.

يمكنك الوصول إلى هذه الأحداث في عارض أحداث Windows:

1. افتح قائمة **البدء** واكتب **عارض الأحداث**، ثم حدد **النتيجة عارض الأحداث**.
2. قم بتوسيع **سجلات التطبيقات والخدمات > Microsoft > Windows** ثم انتقل إلى المجلد المدرج ضمن **الموفر/المصدر** في الجدول أدناه.
3. انقر نقرا مزدوجا فوق العنصر الفرعي لمشاهدة الأحداث. قم بالتمرير عبر الأحداث للعثور على الحدث الذي تبحث عنه.

   ![رسم متحرك يظهر استخدام عارض الأحداث.](images/event-viewer.gif)

<br>

****

|ميزه|الموفر/المصدر|معرف الحدث|الوصف|
|---|---|:---:|---|
|الحماية من استغلال|Security-Mitigations (وضع النواة/وضع المستخدم)|1|تدقيق ACG|
|الحماية من استغلال|Security-Mitigations (وضع النواة/وضع المستخدم)|2|فرض ACG|
|الحماية من استغلال|Security-Mitigations (وضع النواة/وضع المستخدم)|3|عدم السماح بتدقيق العمليات التابعة|
|الحماية من استغلال|Security-Mitigations (وضع النواة/وضع المستخدم)|4|عدم السماح لكتلة العمليات التابعة|
|الحماية من استغلال|Security-Mitigations (وضع النواة/وضع المستخدم)|5|حظر تدقيق الصور منخفضة التكامل|
|الحماية من استغلال|Security-Mitigations (وضع النواة/وضع المستخدم)|6|حظر كتلة الصور منخفضة التكامل|
|الحماية من استغلال|Security-Mitigations (وضع النواة/وضع المستخدم)|7|حظر تدقيق الصور البعيدة|
|الحماية من استغلال|Security-Mitigations (وضع النواة/وضع المستخدم)|8|حظر كتلة الصور البعيدة|
|الحماية من استغلال|Security-Mitigations (وضع النواة/وضع المستخدم)|9|تعطيل تدقيق مكالمات نظام win32k|
|الحماية من استغلال|Security-Mitigations (وضع النواة/وضع المستخدم)|10|تعطيل كتلة مكالمات نظام win32k|
|الحماية من استغلال|Security-Mitigations (وضع النواة/وضع المستخدم)|11|تدقيق حماية تكامل التعليمات البرمجية|
|الحماية من استغلال|Security-Mitigations (وضع النواة/وضع المستخدم)|12|كتلة حماية تكامل التعليمات البرمجية|
|الحماية من استغلال|Security-Mitigations (وضع النواة/وضع المستخدم)|13|تدقيق EAF|
|الحماية من استغلال|Security-Mitigations (وضع النواة/وضع المستخدم)|14|فرض EAF|
|الحماية من استغلال|Security-Mitigations (وضع النواة/وضع المستخدم)|15|تدقيق EAF+|
|الحماية من استغلال|Security-Mitigations (وضع النواة/وضع المستخدم)|16|فرض EAF+|
|الحماية من استغلال|Security-Mitigations (وضع النواة/وضع المستخدم)|17|تدقيق IAF|
|الحماية من استغلال|Security-Mitigations (وضع النواة/وضع المستخدم)|18|فرض IAF|
|الحماية من استغلال|Security-Mitigations (وضع النواة/وضع المستخدم)|19|تدقيق ROP StackPivot|
|الحماية من استغلال|Security-Mitigations (وضع النواة/وضع المستخدم)|20|فرض ROP StackPivot|
|الحماية من استغلال|Security-Mitigations (وضع النواة/وضع المستخدم)|21|تدقيق ROP CallerCheck|
|الحماية من استغلال|Security-Mitigations (وضع النواة/وضع المستخدم)|22|فرض ROP CallerCheck|
|الحماية من استغلال|Security-Mitigations (وضع النواة/وضع المستخدم)|23|تدقيق ROP SimExec|
|الحماية من استغلال|Security-Mitigations (وضع النواة/وضع المستخدم)|24|فرض ROP SimExec|
|الحماية من استغلال|WER-Diagnostics|5|CFG Block|
|الحماية من استغلال|Win32K (تشغيلي)|260|خط غير موثوق به|
|حماية الشبكة|Windows Defender (تشغيلي)|5007|حدث عند تغيير الإعدادات|
|حماية الشبكة|Windows Defender (تشغيلي)|1125|حدث عند تشغيل حماية الشبكة في وضع التدقيق|
|حماية الشبكة|Windows Defender (تشغيلي)|1126|حدث عند تشغيل حماية الشبكة في وضع الحظر|
|الوصول إلى المجلدات الخاضعة للتحكم|Windows Defender (تشغيلي)|5007|حدث عند تغيير الإعدادات|
|الوصول إلى المجلدات الخاضعة للتحكم|Windows Defender (تشغيلي)|1124|حدث الوصول إلى المجلدات الخاضعة للرقابة التي تم تدقيقها|
|الوصول إلى المجلدات الخاضعة للتحكم|Windows Defender (تشغيلي)|1123|حدث الوصول إلى المجلدات المحظورة الخاضعة للرقابة|
|الوصول إلى المجلدات الخاضعة للتحكم|Windows Defender (تشغيلي)|1127|حدث كتلة الكتابة الخاصة بالوصول إلى المجلدات المحظورة|
|الوصول إلى المجلدات الخاضعة للتحكم|Windows Defender (تشغيلي)|1128|حدث كتلة الكتابة الخاصة بالوصول إلى المجلدات الخاضعة للرقابة التي تم تدقيقها|
|قواعد تقليل الأجزاء المعرضة للهجوم|Windows Defender (تشغيلي)|5007|حدث عند تغيير الإعدادات|
|قواعد تقليل الأجزاء المعرضة للهجوم|Windows Defender (تشغيلي)|1122|حدث عند تشغيل القاعدة في وضع التدقيق|
|قواعد تقليل الأجزاء المعرضة للهجوم|Windows Defender (تشغيلي)|1121|حدث عند تشغيل القاعدة في وضع الحظر|

>[!NOTE]
> من منظور المستخدم، يتم إجراء إعلامات وضع تحذير ASR كإعلامات منبثقة ل Windows لقواعد تقليل الأجزاء المعرضة للهجوم.
>
> في ASR، توفر Network Protection أوضاع التدقيق والحظر فقط.

## <a name="resources-to-learn-more-about-attack-surface-reduction"></a>موارد لمعرفة المزيد حول تقليل الأجزاء المعرضة للهجوم

كما ذكر في الفيديو، يتضمن Defender لنقطة النهاية العديد من قدرات تقليل الأجزاء المعرضة للهجوم. استخدم الموارد التالية لمعرفة المزيد:

| مقالة | الوصف |
|:---|:---|
| [العزل المستند إلى الأجهزة](/windows/security/threat-protection/microsoft-defender-application-guard/md-app-guard-overview) | حماية سلامة النظام والحفاظ عليها عند بدء تشغيله وأثناء تشغيله. التحقق من سلامة النظام من خلال الإثبات المحلي والبعيد. استخدم عزل الحاوية ل Microsoft Edge للمساعدة في الحماية من مواقع الويب الضارة. |
| [التحكم في التطبيق](/windows/security/threat-protection/windows-defender-application-control/windows-defender-application-control) | استخدم التحكم في التطبيق بحيث يجب أن تكتسب تطبيقاتك الثقة من أجل التشغيل. |
| [الوصول إلى المجلدات الخاضعة للتحكم](controlled-folders.md) | المساعدة في منع التطبيقات الضارة أو المشبوهة (بما في ذلك البرامج الضارة لبرامج الفدية الضارة لتشفير الملفات) من إجراء تغييرات على الملفات في مجلدات النظام الرئيسية (يتطلب برنامج الحماية من الفيروسات من Microsoft Defender). |
| [حماية الشبكة](network-protection.md) | توسيع نطاق الحماية لنسبة استخدام الشبكة والاتصال على أجهزة مؤسستك. (يتطلب برنامج الحماية من الفيروسات من Microsoft Defender). |
| [الحماية من استغلال](exploit-protection.md) | المساعدة في حماية أنظمة التشغيل والتطبيقات التي تستخدمها مؤسستك من الاستغلال. تعمل الحماية من الاستغلال أيضا مع حلول مكافحة الفيروسات من الجهات الخارجية. |
| [عنصر تحكم الجهاز](device-control-report.md) | يحمي من فقدان البيانات من خلال مراقبة الوسائط المستخدمة على الأجهزة والتحكم فيها، مثل التخزين القابل للإزالة ومحركات أقراص USB، في مؤسستك. |
| [دليل نشر قواعد الحد من سطح الهجوم (ASR)](attack-surface-reduction-rules-deployment.md) | يقدم معلومات النظرة العامة والمتطلبات الأساسية لنشر قواعد تقليل الأجزاء المعرضة للهجوم، متبوعة بإرشادات مفصلة خطوة بخطوة للاختبار والتمكين والمراقبة. |
| [تخطيط نشر قواعد تقليل الأجزاء المعرضة للهجوم (ASR)](attack-surface-reduction-rules-deployment-plan.md) | يسرد الخطوات الموصى بها لتوزيع قواعد تقليل الأجزاء المعرضة للهجوم. |
| [اختبار قواعد تقليل الأجزاء المعرضة للهجوم (ASR)](attack-surface-reduction-rules-deployment-test.md) | يوفر خطوات لاستخدام وضع التدقيق لاختبار قواعد تقليل الأجزاء المعرضة للهجوم. |
| [تمكين قواعد تقليل الأجزاء المعرضة للهجوم (ASR)](attack-surface-reduction-rules-deployment-implement.md) | يعرض خطوات نقل قواعد تقليل الأجزاء المعرضة للهجوم من وضع الاختبار (التدقيق) إلى الوضع النشط والممكن (حظر). |
| [تشغيل قواعد تقليل الأجزاء المعرضة للهجوم (ASR)](attack-surface-reduction-rules-deployment-operationalize.md) | يوفر معلومات حول أنشطة المراجعة والصيانة اليومية. |
| [مرجع قواعد تقليل الأجزاء المعرضة للهجوم](attack-surface-reduction-rules-reference.md) | يوفر تفاصيل حول كل قاعدة تقليل الأجزاء المعرضة للهجوم. |
| [قواعد تقليل الأجزاء المعرضة للهجوم](attack-surface-reduction.md) | تقليل الثغرات الأمنية (أسطح الهجوم) في تطبيقاتك باستخدام قواعد ذكية تساعد على إيقاف البرامج الضارة. (يتطلب برنامج الحماية من الفيروسات من Microsoft Defender). |
