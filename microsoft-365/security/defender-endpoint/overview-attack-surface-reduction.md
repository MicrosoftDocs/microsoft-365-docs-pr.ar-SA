---
title: فهم الحد من سطح الهجوم واستخدامه (ASR)
ms.reviewer: ''
description: تعرف على إمكانات الحد من سطح الهجوم ل Microsoft Defender لنقطة النهاية.
keywords: asr، تقليل سطح الهجوم، Microsoft Defender ل Endpoint، microsoft defender، برنامج الحماية من الفيروسات، av، windows defender
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
ms.date: 1/18/2022
ms.openlocfilehash: 9c489d28467582e0f95f3fde7440ff43022c44e1
ms.sourcegitcommit: b3530441288b2bc44342e00e9025a49721796903
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/20/2022
ms.locfileid: "63682031"
---
# <a name="understand-and-use-attack-surface-reduction-capabilities"></a>فهم إمكانات الحد من سطح الهجوم واستخدامها

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**

- [خطة Microsoft Defender لنقطة النهاية 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> [!TIP]
> هل تريد تجربة Microsoft Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

أسطح الهجمات هي كل الأماكن التي تكون فيها مؤسستك عرضة للهجمات ولهجمات الإنترنت. يتضمن Defender for Endpoint العديد من الإمكانات للمساعدة في تقليل أسطح الهجوم. شاهد الفيديو التالي لمعرفة المزيد حول تقليل مساحة الهجوم.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4woug]

## <a name="configure-attack-surface-reduction-capabilities"></a>تكوين إمكانات الحد من سطح الهجوم

لتكوين تقليل مساحة الهجوم في بيئتك، اتبع الخطوات التالية:

1. [تمكين عزل مستند إلى الأجهزة Microsoft Edge](/windows/security/threat-protection/microsoft-defender-application-guard/install-md-app-guard).

2. تمكين التحكم في التطبيق.

   1. مراجعة السياسات الأساسية في Windows. راجع [مثال على سياسات الأساس](/windows/security/threat-protection/windows-defender-application-control/example-wdac-base-policies).
   2. راجع دليل [تصميم Windows Defender Application Control](/windows/security/threat-protection/windows-defender-application-control/windows-defender-application-control-design-guide).
   3. راجع [نشر Windows Defender Application Control (WDAC)](/windows/security/threat-protection/windows-defender-application-control/windows-defender-application-control-deployment-guide) .

3. [تمكين الوصول المتحكم به إلى المجلدات](enable-controlled-folders.md).

4. [تشغيل حماية الشبكة](enable-network-protection.md).

5. [تمكين الحماية من استغلال.](enable-exploit-protection.md)

6. [نشر قواعد تقليل مساحة الهجوم](attack-surface-reduction-rules-deployment.md).

7. إعداد جدار الحماية للشبكة.

   1. احصل على نظرة عامة حول [Windows Defender مع أمان متقدم](/windows/security/threat-protection/windows-firewall/windows-firewall-with-advanced-security).
   2. استخدم دليل [Windows جدار](/windows/security/threat-protection/windows-firewall/windows-firewall-with-advanced-security-design-guide) الحماية ل Defender لتحديد الطريقة التي تريد بها تصميم سياسات جدار الحماية.
   3. استخدم دليل [Windows جدار](/windows/security/threat-protection/windows-firewall/windows-firewall-with-advanced-security-deployment-guide) الحماية ل Defender لإعداد جدار الحماية الخاص بالمنظمة باستخدام أمان متقدم.

> [!TIP]
> في معظم الحالات، عندما تقوم بتكوين إمكانات تقليل مساحة الهجوم، يمكنك الاختيار من بين عدة أساليب:
>
> - إدارة نقاط النهاية من Microsoft (التي تتضمن الآن Microsoft Intune Microsoft Endpoint Configuration Manager)
> - نهج المجموعة
> - PowerShell cmdlets

## <a name="test-attack-surface-reduction-in-microsoft-defender-for-endpoint"></a>اختبار تقليل سطح الهجوم في Microsoft Defender لنقطة النهاية

كجزء من فريق الأمان في مؤسستك، يمكنك تكوين قدرات تقليل مساحة الهجوم للتشغيل في وضع التدقيق لمعرفة كيفية عملها. في وضع التدقيق، يمكنك تمكين:

- قواعد تقليل الأجزاء المعرضة للهجوم
- الحماية من استغلال
- حماية الشبكة
- والوصول المتحكم به إلى المجلد في وضع التدقيق

يتيح لك وضع التدقيق الاطلاع على سجل لما *كان* سيحدث إذا قمت بتمكين الميزة.

يمكنك تمكين وضع التدقيق عند اختبار كيفية عمل الميزات. يساعد تمكين وضع التدقيق للاختبار فقط على منع وضع التدقيق من التأثير على تطبيقات خط العمل. يمكنك أيضا الحصول على فكرة حول عدد محاولات تعديل الملفات المريبة التي تحدث خلال فترة زمنية معينة.

لن تمنع الميزات تعديل التطبيقات أو البرامج النصية أو الملفات أو تمنعها. ومع ذلك، Windows سجل الأحداث الأحداث كما لو تم تمكين الميزات بالكامل. باستخدام وضع التدقيق، يمكنك مراجعة سجل الأحداث لمعرفة تأثير الميزة إذا تم تمكينها.

للعثور على الإدخالات التي تم تدقيقها، انتقل إلى **تطبيقات** \> **وخدمات Microsoft** \>  \> Windows **Windows Defender** \> **التشغيلية**.

استخدم Defender لنقطة النهاية للحصول على مزيد من التفاصيل حول كل حدث. هذه التفاصيل مفيدة بشكل خاص في التحقق من قواعد تقليل مساحة الهجوم. يتيح لك استخدام وحدة تحكم Defender for Endpoint [إمكانية التحقق من المشاكل كجزء من مخطط التنبيه الزمني وسيناريوهات الاستقصاء](investigate-alerts.md).

يمكنك تمكين وضع التدقيق باستخدام نهج المجموعة و PowerShell وموفري خدمات التكوين (CSPs).

> [!TIP]
> يمكنك أيضا زيارة موقع ويب Windows Defender Testground في demo.wd.microsoft.com للتأكد من [](https://demo.wd.microsoft.com?ocid=cx-wddocs-testground) أن الميزات تعمل وترى كيفية عملها.

> [!NOTE]
> تم إهمال موقع عرض Defender for Endpoint demo.wd.microsoft.com، وستزال في المستقبل.

| خيارات التدقيق | كيفية تمكين وضع التدقيق | كيفية عرض الأحداث |
|---|---|---|
| ينطبق التدقيق على كل الأحداث | [تمكين الوصول إلى المجلدات الخاضعة للتحكم](enable-controlled-folders.md) | [أحداث الوصول إلى المجلدات الخاضعة للتحكم](evaluate-controlled-folder-access.md#review-controlled-folder-access-events-in-windows-event-viewer) |
| ينطبق التدقيق على القواعد الفردية | [الخطوة 1: اختبار قواعد ASR باستخدام التدقيق](attack-surface-reduction-rules-deployment-test.md#step-1-test-asr-rules-using-audit) | [الخطوة 2: فهم صفحة إعداد التقارير حول قواعد تقليل مساحة الهجوم](attack-surface-reduction-rules-deployment-test.md#step-2-understand-the-attack-surface-reduction-rules-reporting-page-in-the-microsoft-365-defender-portal) |
| ينطبق التدقيق على كل الأحداث | [تمكين حماية الشبكة](enable-network-protection.md) | [أحداث حماية الشبكة](evaluate-network-protection.md#review-network-protection-events-in-windows-event-viewer) |
| ينطبق التدقيق على عمليات التخفيف الفردية | [تمكين الحماية من استغلال](enable-exploit-protection.md) | [أحداث الحماية من استغلال](exploit-protection.md#review-exploit-protection-events-in-windows-event-viewer) |

## <a name="view-attack-surface-reduction-events"></a>عرض أحداث الحد من سطح الهجوم

راجع أحداث الحد من سطح الهجوم في "عارض الأحداث" لمراقبة القواعد أو الإعدادات التي تعمل. يمكنك أيضا تحديد ما إذا كانت أي إعدادات "صاخبة" جدا أو تؤثر على سير العمل اليومي.

تكون مراجعة الأحداث في متناول يديك عند تقييم الميزات. يمكنك تمكين وضع التدقيق للميزات أو الإعدادات، ثم مراجعة ما كان سيحدث إذا تم تمكينها بالكامل.

يسرد هذا القسم كل الأحداث والميزات أو الإعدادات المقترنة بها، ويصف كيفية إنشاء طرق عرض مخصصة للتصفية حسب أحداث معينة.

احصل على تقارير مفصلة حول الأحداث والحظر والتحذيرات كجزء من أمن Windows إذا كان لديك اشتراك E5 واستخدام [Microsoft Defender لنقطة النهاية](microsoft-defender-endpoint.md).

### <a name="use-custom-views-to-review-attack-surface-reduction-capabilities"></a>استخدام طرق العرض المخصصة لمراجعة إمكانات الحد من سطح الهجوم

يمكنك إنشاء طرق عرض مخصصة في Windows الحدث لعرض الأحداث فقط للإمكانات والإعدادات المحددة. الطريقة الأسهل هي استيراد طريقة عرض مخصصة كملف XML. يمكنك نسخ XML مباشرة من هذه الصفحة.

يمكنك أيضا الانتقال يدويا إلى منطقة الحدث التي تتوافق مع الميزة.

#### <a name="import-an-existing-xml-custom-view"></a>استيراد طريقة عرض XML مخصصة موجودة

1. قم بإنشاء ملف .txt فارغ وانسخ XML ل طريقة العرض المخصصة التي تريد استخدامها في .txt الملف. يمكنك القيام بذلك لكل من طرق العرض المخصصة التي تريد استخدامها. أعد تسمية الملفات كما يلي (تأكد من تغيير النوع من .txt إلى .xml):
    - طريقة عرض مخصصة للأحداث التي يتم التحكم فيها للوصول إلى *المجلدات:cfa-events.xml*
    - طريقة عرض مخصصة للأحداث المتعلقة بالحماية *:ep-events.xml*
    - طريقة عرض مخصصة للأحداث المخفضة لسطح *الهجوم:asr-events.xml*
    - طريقة العرض المخصصة أحداث الشبكة/الحماية: *np-events.xml*

2. اكتب **عارض الأحداث** في قائمة البدء وعارض **الأحداث المفتوح**.

3. حدد **إجراء استيراد** \> **طريقة عرض مخصصة...**

   > [!div class="mx-imgBorder"]
   > ![تمييز الحركة استيراد طريقة عرض مخصصة على الجانب الأيسر من نافذة العارض "حتى".](images/events-import.gif)

4. انتقل إلى المكان الذي قمت باستخراج ملف XML ل طريقة العرض المخصصة التي تريدها وحدده.

5. حدد **فتح**.

6. سيتم إنشاء طريقة عرض مخصصة تقوم بالتصفية لإظهار الأحداث ذات الصلة بهذه الميزة فقط.

#### <a name="copy-the-xml-directly"></a>نسخ XML مباشرة

1. اكتب **عارض الأحداث** في قائمة البدء وافتح Windows **الحدث**.

2. في اللوحة اليسرى، ضمن **إجراءات**، حدد **إنشاء طريقة عرض مخصصة...**

   > [!div class="mx-imgBorder"]
   > ![حركة تسلط الضوء على خيار إنشاء طريقة عرض مخصصة في نافذة عارض الأحداث.](images/events-create.gif)

3. انتقل إلى علامة التبويب XML وحدد **تحرير الاستعلام يدويا**. سترى تحذيرا بأنه لا يمكنك تحرير الاستعلام باستخدام علامة التبويب **تصفية** إذا كنت تستخدم خيار XML. حدد **نعم**.

4. اللصق التعليمات البرمجية ل XML للميزة التي تريد تصفية الأحداث منها إلى مقطع XML.

5. حدد **موافق**. حدد اسما لتصفية. ينشئ هذا طريقة عرض مخصصة تقوم بالتصفية لإظهار الأحداث المرتبطة بهذه الميزة فقط.

#### <a name="xml-for-attack-surface-reduction-rule-events"></a>XML للأحداث الخاصة بخفض مساحة الهجوم

```xml
<QueryList>
  <Query Id="0" Path="Microsoft-Windows-Windows Defender/Operational">
   <Select Path="Microsoft-Windows-Windows Defender/Operational">*[System[(EventID=1121 or EventID=1122 or EventID=5007)]]</Select>
   <Select Path="Microsoft-Windows-Windows Defender/WHC">*[System[(EventID=1121 or EventID=1122 or EventID=5007)]]</Select>
  </Query>
</QueryList>
```

#### <a name="xml-for-controlled-folder-access-events"></a>XML للأحداث التي يتم التحكم فيها للوصول إلى المجلدات

```xml
<QueryList>
  <Query Id="0" Path="Microsoft-Windows-Windows Defender/Operational">
   <Select Path="Microsoft-Windows-Windows Defender/Operational">*[System[(EventID=1123 or EventID=1124 or EventID=5007)]]</Select>
   <Select Path="Microsoft-Windows-Windows Defender/WHC">*[System[(EventID=1123 or EventID=1124 or EventID=5007)]]</Select>
  </Query>
</QueryList>
```

#### <a name="xml-for-exploit-protection-events"></a>XML للأحداث المتعلقة بالحماية من استغلال

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

#### <a name="xml-for-network-protection-events"></a>XML للأحداث المتعلقة بحماية الشبكة

```xml
<QueryList>
 <Query Id="0" Path="Microsoft-Windows-Windows Defender/Operational">
  <Select Path="Microsoft-Windows-Windows Defender/Operational">*[System[(EventID=1125 or EventID=1126 or EventID=5007)]]</Select>
  <Select Path="Microsoft-Windows-Windows Defender/WHC">*[System[(EventID=1125 or EventID=1126 or EventID=5007)]]</Select>
 </Query>
</QueryList>
```

### <a name="list-of-attack-surface-reduction-events"></a>قائمة أحداث الحد من سطح الهجوم

تقع كل أحداث تقليل مساحة الهجوم ضمن سجلات الخدمات والتطبيقات > **Microsoft > Windows** ثم المجلد أو الموفر كما هو مذكور في الجدول التالي.

يمكنك الوصول إلى هذه الأحداث في Windows الحدث:

1. افتح قائمة **البدء** وا اكتب **عارض الأحداث**، ثم حدد نتيجة **عارض** الأحداث.
2. قم **بتوسيع سجلات الخدمات والتطبيقات > Microsoft > Windows ثم** انتقل إلى المجلد المدرج ضمن **الموفر/المصدر** في الجدول أدناه.
3. انقر نقرا مزدوجا فوق العنصر الفرعي لرؤية الأحداث. قم بالتمرير عبر الأحداث للعثور على الحدث الذي تبحث عنه.

   ![تظهر الحركة استخدام "عارض الأحداث".](images/event-viewer.gif)

<br>

****

|الميزة|الموفر/المصدر|"معرّف الحدث"|الوصف|
|---|---|:---:|---|
|الحماية من استغلال|Security-Mitigations (وضع Kernel/وضع المستخدم)|1|تدقيق ACG|
|الحماية من استغلال|Security-Mitigations (وضع Kernel/وضع المستخدم)|2|فرض ACG|
|الحماية من استغلال|Security-Mitigations (وضع Kernel/وضع المستخدم)|3|عدم السماح بتدقيق عمليات الأطفال|
|الحماية من استغلال|Security-Mitigations (وضع Kernel/وضع المستخدم)|4|عدم السماح بحظر العمليات الخاصة بالطفل|
|الحماية من استغلال|Security-Mitigations (وضع Kernel/وضع المستخدم)|5|حظر تدقيق الصور ذات التكامل المنخفض|
|الحماية من استغلال|Security-Mitigations (وضع Kernel/وضع المستخدم)|6|حظر حظر الصور ذات التكامل المنخفض|
|الحماية من استغلال|Security-Mitigations (وضع Kernel/وضع المستخدم)|7|حظر تدقيق الصور عن بعد|
|الحماية من استغلال|Security-Mitigations (وضع Kernel/وضع المستخدم)|8|حظر حظر الصور البعيدة|
|الحماية من استغلال|Security-Mitigations (وضع Kernel/وضع المستخدم)|9|تعطيل تدقيق مكالمات نظام win32k|
|الحماية من استغلال|Security-Mitigations (وضع Kernel/وضع المستخدم)|10|تعطيل حظر مكالمات نظام win32k|
|الحماية من استغلال|Security-Mitigations (وضع Kernel/وضع المستخدم)|11|تدقيق حماية تكامل التعليمات البرمجية|
|الحماية من استغلال|Security-Mitigations (وضع Kernel/وضع المستخدم)|12|كتلة حماية تكامل التعليمات البرمجية|
|الحماية من استغلال|Security-Mitigations (وضع Kernel/وضع المستخدم)|13|تدقيق EAF|
|الحماية من استغلال|Security-Mitigations (وضع Kernel/وضع المستخدم)|14|فرض EAF|
|الحماية من استغلال|Security-Mitigations (وضع Kernel/وضع المستخدم)|15|تدقيق EAF+|
|الحماية من استغلال|Security-Mitigations (وضع Kernel/وضع المستخدم)|16|فرض EAF+|
|الحماية من استغلال|Security-Mitigations (وضع Kernel/وضع المستخدم)|17|تدقيق IAF|
|الحماية من استغلال|Security-Mitigations (وضع Kernel/وضع المستخدم)|18|فرض IAF|
|الحماية من استغلال|Security-Mitigations (وضع Kernel/وضع المستخدم)|19|تدقيق ROP StackPivot|
|الحماية من استغلال|Security-Mitigations (وضع Kernel/وضع المستخدم)|20|فرض ROP StackPivot|
|الحماية من استغلال|Security-Mitigations (وضع Kernel/وضع المستخدم)|21|تدقيق ROP CallerCheck|
|الحماية من استغلال|Security-Mitigations (وضع Kernel/وضع المستخدم)|22|فرض ROP CallerCheck|
|الحماية من استغلال|Security-Mitigations (وضع Kernel/وضع المستخدم)|23|تدقيق ROP SimExec|
|الحماية من استغلال|Security-Mitigations (وضع Kernel/وضع المستخدم)|24|فرض ROP SimExec|
|الحماية من استغلال|WER-Diagnostics|5|كتلة CFG|
|الحماية من استغلال|Win32K (تشغيلي)|260|الخط غير الملوث|
|حماية الشبكة|Windows Defender (التشغيل)|5007|حدث عند تغيير الإعدادات|
|حماية الشبكة|Windows Defender (التشغيل)|1125|حدث عند تشغيل حماية الشبكة في وضع التدقيق|
|حماية الشبكة|Windows Defender (التشغيل)|1126|حدث عند تشغيل حماية الشبكة في وضع الحظر|
|الوصول إلى المجلدات الخاضعة للتحكم|Windows Defender (التشغيل)|5007|حدث عند تغيير الإعدادات|
|الوصول إلى المجلدات الخاضعة للتحكم|Windows Defender (التشغيل)|1124|حدث الوصول إلى المجلدات التي تم التحكم فيها التي تم تدقيقها|
|الوصول إلى المجلدات الخاضعة للتحكم|Windows Defender (التشغيل)|1123|حدث الوصول إلى المجلدات المحظورة الخاضعة للتحكم|
|الوصول إلى المجلدات الخاضعة للتحكم|Windows Defender (التشغيل)|1127|حدث كتلة كتلة الوصول إلى المجلدات المحظورة التي تم التحكم فيها|
|الوصول إلى المجلدات الخاضعة للتحكم|Windows Defender (التشغيل)|1128|حدث كتلة كتلة الوصول إلى المجلدات الخاضعة للتدقيق|
|الحد من سطح الهجوم|Windows Defender (التشغيل)|5007|حدث عند تغيير الإعدادات|
|الحد من سطح الهجوم|Windows Defender (التشغيل)|1122|حدث عند تشغيل القاعدة في وضع التدقيق|
|الحد من سطح الهجوم|Windows Defender (التشغيل)|1121|حدث عند تشغيل القاعدة في وضع الحظر|

>[!NOTE]
> من منظور المستخدم، يتم إجراء إعلامات وضع تحذير ASR Windows الإعلام المنبثق لقواعد الحد من سطح الهجوم.
>
> في ASR، توفر "حماية الشبكة" أوضاع التدقيق والحظر فقط.

## <a name="resources-to-learn-more-about-attack-surface-reduction"></a>الموارد لمعرفة المزيد حول الحد من سطح الهجوم

كما هو مذكور في الفيديو، يتضمن Defender for Endpoint العديد من إمكانات تقليل مساحة الهجوم. استخدم الموارد التالية لمعرفة المزيد:

| مقالة | الوصف |
|:---|:---|
| [عزل مستند إلى الأجهزة](/windows/security/threat-protection/microsoft-defender-application-guard/md-app-guard-overview) | حماية تكامل النظام والمحافظة عليه عند بدء تشغيله وأثناء تشغيله. تحقق من تكامل النظام من خلال المصادقة المحلية والنائية. استخدم عزل الحاويات Microsoft Edge للمساعدة في حماية مواقع الويب الضارة. |
| [عنصر تحكم التطبيق](/windows/security/threat-protection/windows-defender-application-control/windows-defender-application-control) | استخدم التحكم في التطبيق بحيث يجب أن تكسب تطبيقاتك الثقة لكي تتمكن من التشغيل. |
| [الوصول إلى المجلدات الخاضعة للتحكم](controlled-folders.md) | المساعدة على منع التطبيقات الضارة أو المريبة (بما في ذلك برامج الفدية الضارة المشفرة للملفات) من إجراء تغييرات على الملفات في مجلدات النظام الرئيسية (يتطلب برنامج الحماية من الفيروسات من Microsoft Defender) |
| [حماية الشبكة](network-protection.md) | توسيع الحماية لتشمل حركة مرور الشبكة واتصالها على أجهزة مؤسستك. (يتطلب برنامج الحماية من الفيروسات من Microsoft Defender) |
| [الحماية من استغلال](exploit-protection.md) | ساعد على حماية أنظمة التشغيل والتطبيقات التي تستخدمها مؤسستك من أن يتم استغلالها. تعمل الحماية من استغلال أيضا مع حلول الحماية من الفيروسات من جهة خارجية. |
| [قواعد تقليل الأجزاء المعرضة للهجوم](attack-surface-reduction.md) | يمكنك تقليل نقاط الضعف (أسطح الهجمات) في تطبيقاتك باستخدام القواعد الذكية التي تساعد على إيقاف البرامج الضارة. (يتطلب برنامج الحماية من الفيروسات من Microsoft Defender). |
| [عنصر تحكم الجهاز](device-control-report.md) | يحمي من فقدان البيانات من خلال مراقبة الوسائط المستخدمة على الأجهزة والتحكم بها، مثل التخزين القابل للإزالة ومحركات أقراص USB، في مؤسستك. |
