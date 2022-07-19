---
title: الاستجابة لهجمات برامج الفدية الضارة
description: توفر هذه المقالة دليل مبادئ عموميا للاستجابة لهجمات برامج الفدية الضارة.
search.appverid: MET150
author: nic-name
ms.author: noriordan
manager: dolmont
audience: ITPro
ms.topic: article
ms.date: 05/30/2022
ms.prod: m365-security
ms.localizationpriority: medium
ms.collection: M365-security-compliance
f1.keywords: NOCSH
ms.openlocfilehash: a7c03947cc159ed9933854c9fd1041af63c3f55c
ms.sourcegitcommit: aff1732dfa21e9283b173d8e5ca5bcbeeaaa26d8
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 06/01/2022
ms.locfileid: "66857332"
---
# <a name="responding-to-ransomware-attacks"></a>الاستجابة لهجمات برامج الفدية الضارة

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

عندما تشك في أنك كنت أو تتعرض حاليا لهجوم برامج الفدية الضارة، قم بإنشاء اتصالات آمنة مع فريق الاستجابة للحوادث على الفور. يمكنهم تنفيذ مراحل الاستجابة التالية لتعطيل الهجوم وتخفيف الضرر:

* التحقيق والاحتواء
* مكافحة الهزات واسترداده

توفر هذه المقالة دليل مبادئ عموميا للاستجابة لهجمات برامج الفدية الضارة. ضع في اعتبارك تكييف الخطوات والمهام الموضحة في هذه المقالة مع دليل مبادئ عمليات الأمان.
ملاحظة: للحصول على معلومات حول منع هجمات برامج الفدية الضارة، راجع [الحماية السريعة من برامج الفدية الضارة والمسؤول عن العمل](/security/compass/protect-against-ransomware).

## <a name="containment"></a>الاحتواء

وينبغي أن يحدث الاحتواء والتحقيق في وقت واحد قدر الإمكان؛ ومع ذلك، يجب عليك التركيز على تحقيق الاحتواء بسرعة، بحيث يكون لديك المزيد من الوقت للتحقيق. تساعدك هذه الخطوات على تحديد نطاق الهجوم وعزله إلى الكيانات المتأثرة فقط، مثل حسابات المستخدمين والأجهزة.

### <a name="step-1-assess-the-scope-of-the-incident"></a>الخطوة 1: تقييم نطاق الحادث

قم بتشغيل قائمة الأسئلة والمهام هذه لاكتشاف مدى الهجوم. يمكن Microsoft 365 Defender تقديم عرض موحد لجميع الأصول المتأثرة أو المعرضة للخطر للمساعدة في تقييم الاستجابة للحوادث. راجع [الاستجابة للحوادث باستخدام Microsoft 365 Defender | Microsoftova dokumentacija](/incidents-overview.md). يمكنك استخدام التنبيهات وقائمة الأدلة في الحدث لتحديد:

* ما هي حسابات المستخدمين التي قد يتم اختراقها؟
  * ما هي الحسابات التي تم استخدامها لتسليم الحمولة؟
* ما هي الأجهزة [المكتشفة والملحقة](../defender-endpoint/investigate-machines.md) المتأثرة وكيف؟[](../defender-endpoint/device-discovery.md)
  * الأجهزة الأصلية
  * الأجهزة المتأثرة
  * الأجهزة المشبوهة
* تحديد أي اتصال شبكة مرتبط بالحادث.
* ما هي التطبيقات المتأثرة؟
* ما هي الحمولات التي تم نشرها؟
* كيف يتواصل المهاجم مع الأجهزة المخترقة؟ (يجب [تمكين](../defender-endpoint/enable-network-protection.md) حماية الشبكة):
  * انتقل إلى [صفحة المؤشرات](../defender-endpoint/indicator-ip-domain.md#create-indicators-for-ips-and-urlsdomains) لإضافة كتلة ل IP وURL (إذا كانت لديك تلك المعلومات).
* ما هو متوسط تسليم الحمولة؟

### <a name="step-2-preserve-existing-systems"></a>الخطوة 2: الحفاظ على الأنظمة الموجودة

قم بتشغيل قائمة المهام والأسئلة هذه لحماية الأنظمة الموجودة من الهجوم:

* إذا كانت لديك نسخ احتياطية عبر الإنترنت، ففكر في قطع اتصال نظام النسخ الاحتياطي بالشبكة حتى تكون واثقا من احتواء الهجوم، فراجع [خطة النسخ الاحتياطي والاستعادة للحماية من برامج الفدية الضارة | Microsoftova dokumentacija](/security/compass/backup-plan-to-protect-against-ransomware).
* إذا كنت تواجه أو تتوقع نشر برامج الفدية الضارة الداهمة والنشطة:
  * [تعد الحسابات المتميزة والمحلية](/investigate-users.md) التي تشك في أنها جزء من الهجوم مؤقتا. يمكنك القيام بذلك من علامة التبويب **"المستخدمون**" في خصائص الحدث في مدخل Microsoft 365 Defender.
  * إيقاف كافة [جلسات تسجيل الدخول عن بعد](/defender-for-identity/playbook-domain-dominance).
  * أعد تعيين كلمات مرور حساب المستخدم المخترقة واطلب من مستخدمي حسابات المستخدمين المخترقة تسجيل الدخول مرة أخرى.
  * قم بنفس الشيء لحسابات المستخدمين التي قد يتم اختراقها.
  * إذا تم اختراق الحسابات المحلية المشتركة، اطلب من مسؤول تكنولوجيا المعلومات مساعدتك لفرض تغيير كلمة المرور عبر جميع الأجهزة المكشوفة. مثال على استعلام Kusto:

```kusto
DeviceLogonEvents | where DeviceName  contains (AccountDomain) | take 10 
```

* للأجهزة التي لم يتم عزلها بعد وليست جزءا من البنية الأساسية الهامة:
  * اعزل الأجهزة المخترقة عن الشبكة ولكن لا توقف تشغيلها.
  * إذا قمت بتحديد الأجهزة الأصلية أو أجهزة نشر البيانات، فعزلها أولا.
* الحفاظ على الأنظمة المخترقة للتحليل.

### <a name="step-3-prevent-the-spread"></a>الخطوة 3: منع الانتشار

استخدم هذه القائمة لمنع انتشار الهجوم إلى كيانات إضافية.

* إذا كانت الحسابات المحلية المشتركة تستخدم في الهجوم، ففكر في [حظر الاستخدام عن بعد للحسابات المحلية](https://techcommunity.microsoft.com/t5/microsoft-security-baselines/blocking-remote-use-of-local-accounts/ba-p/701042).
  * استعلام Kusto لكافة عمليات تسجيل الدخول إلى الشبكة التي تكون مسؤولين محليين:

```kusto
DeviceLogonEvents
| where IsLocalAdmin == true and AccountDomain == DeviceName
| extend IsLocalLogon = tobool(todynamic(AdditionalFields).IsLocalLogon)
| where IsLocalLogon==false
```

* استعلام Kusto لتسجيلات الدخول غير RDP (أكثر واقعية لمعظم الشبكات):

```kusto
DeviceLogonEvents
| where IsLocalAdmin == true and AccountDomain == DeviceName and LogonType != 'RemoteInteractive'
| extend IsLocalLogon = tobool(todynamic(AdditionalFields).IsLocalLogon)
| where IsLocalLogon==false
```

* عزل وإضافة مؤشرات للملفات المصابة.
* تأكد من أن حل الحماية من الفيروسات الخاص بك قابل للتكوين في حالة الحماية المثلى. بالنسبة إلى برنامج الحماية من الفيروسات من Microsoft Defender، يشمل ذلك:
  * يتم تمكين [الحماية في الوقت الحقيقي](../defender-endpoint/configure-real-time-protection-microsoft-defender-antivirus.md).
  * يتم تمكين [الحماية من العبث](../defender-endpoint/prevent-changes-to-security-settings-with-tamper-protection.md). في مدخل Microsoft 365 Defender، حدد **"Settings > Endpoints > Advanced features > Tamper protection**".
  * يتم تمكين قواعد [تقليل الأجزاء المعرضة للهجوم (ASR](../defender-endpoint/enable-attack-surface-reduction.md)).
  * يتم تمكين [حماية السحابة](../defender-endpoint/enable-attack-surface-reduction.md).
* تعطيل Exchange ActiveSync المزامنة من OneDrive.
  * لتعطيل Exchange ActiveSync علبة بريد، راجع [كيفية تعطيل Exchange ActiveSync للمستخدمين في Exchange Online](/exchange/recipients-in-exchange-online/manage-user-mailboxes/enable-or-disable-exchange-activesync).
  * لتعطيل أنواع أخرى من الوصول إلى علبة البريد، راجع:
    * [تمكين MAPI لعلبة بريد أو تعطيلها](/exchange/recipients-in-exchange-online/manage-user-mailboxes/enable-or-disable-mapi).
    * [تمكين الوصول إلى POP3 أو IMAP4 أو تعطيله لمستخدم](/exchange/clients-and-mobile-in-exchange-online/pop3-and-imap4/enable-or-disable-pop3-or-imap4-access).
  * سيساعد إيقاف المزامنة من OneDrive مؤقتا على حماية بياناتك السحابية من التحديث بواسطة الأجهزة التي يحتمل أن تكون مصابة. لمزيد من المعلومات، راجع [كيفية إيقاف المزامنة مؤقتا واستئنافها في OneDrive](https://support.microsoft.com/office/how-to-pause-and-resume-sync-in-onedrive-2152bfa4-a2a5-4d3a-ace8-92912fb4421e).
* تطبيق التصحيحات ذات الصلة وتغييرات التكوين على الأنظمة المتأثرة.
* حظر اتصالات برامج الفدية الضارة باستخدام عناصر تحكم داخلية وخارجية.
* إزالة المحتوى المخزن مؤقتا

## <a name="investigation"></a>التحقيق

استخدم هذا القسم للتحقيق في الهجوم والتخطيط لاستجابتك.

### <a name="assess-your-current-situation"></a>تقييم حالتك الحالية

* ما الذي جعلك على علم بهجوم برامج الفدية الضارة في البداية؟
  * إذا حدد موظفو تكنولوجيا المعلومات التهديد الأولي، مثل تدوين النسخ الاحتياطية التي يتم حذفها، أو تنبيهات الحماية من الفيروسات، أو تنبيهات الكشف عن نقاط النهاية والاستجابة لها (EDR)، أو تغييرات النظام المشبوهة، فمن الممكن في كثير من الأحيان اتخاذ تدابير سريعة لمنع الهجوم، عادة بواسطة إجراءات الاحتواء الموضحة في هذه المقالة.
* ما التاريخ والوقت الذي تعلمته لأول مرة عن الحادث؟
  * ما تحديثات النظام والأمان التي لم يتم تثبيتها على الأجهزة في ذلك التاريخ؟ من المهم فهم الثغرات الأمنية التي ربما تم الاستفادة منها حتى يمكن معالجتها على أجهزة أخرى.
  * ما هي حسابات المستخدمين التي تم استخدامها في هذا التاريخ؟
  * ما هي حسابات المستخدمين الجديدة التي تم إنشاؤها منذ ذلك التاريخ؟
  * ما هي البرامج التي تمت إضافتها للبدء تلقائيا في وقت وقوع الحادث؟
* هل هناك أي إشارة إلى أن المهاجم يصل حاليا إلى الأنظمة؟
  * هل هناك أي أنظمة مشتبه في اختراقها تواجه نشاطا غير عادي؟
  * هل هناك أي حسابات مشتبه بها مخترقة يبدو أنها مستخدمة بنشاط من قبل الخصم؟
  * هل هناك أي دليل على خوادم الأوامر والتحكم النشطة (C2) في EDR وجدار الحماية و VPN وكيل الويب والسجلات الأخرى؟

### <a name="identify-the-ransomware-process"></a>تحديد عملية برامج الفدية الضارة

* باستخدام [التتبع المتقدم](/microsoft-365/security/defender/advanced-hunting-overview.md)، ابحث عن العملية المحددة في أحداث إنشاء العملية على أجهزة أخرى.

### <a name="look-for-exposed-credentials-in-the-infected-devices"></a>البحث عن بيانات الاعتماد المكشوفة في الأجهزة المصابة

* بالنسبة لحسابات المستخدمين التي يحتمل أن تكون بيانات الاعتماد الخاصة بها مخترقة، قم بإعادة تعيين كلمات مرور الحساب، واطلب من المستخدمين تسجيل الدخول مرة أخرى.
* قد تشير IOAs التالية إلى الحركة الجانبية:

<details>
  <summary>انقر للتوسيع</summary>

* أوامر مريبة
* MLFileBasedAlert
* IfeoDebuggerPersistence
* SuspiciousRemoteFileDropAndExecution
* استكشافيWindowsCommands
* IoaStickyKeys
* مكبر Mimikatz Defender
* أداة مسح الشبكة المستخدمة من قبل PARINACOTA
* DefenderServerAlertMSSQLServer
* SuspiciousLowReputationFileDrop
* SuspiciousServiceExecution
* AdminUserAddition
* MimikatzArtifactsDetector
* Scuba-WdigestEnabledToAccessCredentials
* DefenderMalware
* MLSuspCmdBehavior
* MLSuspiciousRemoteInvocation
* مريبRemoteComponentInvocation
* معالجة مريبة
* MLCmdBasedWithRemoting
* معالجة Accesses Lsass
* تنفيذ عملية Rundll32 مريب
* BitsAdmin
* DefenderCobaltStrikeDetection
* DefenderHacktool
* IoaSuspPSCommandline
* Metasploit
* MLSuspToolBehavior
* RegistryQueryForPasswords
* مريبWdavExclusion
* ASEPRegKey
* CobaltStrikeExecutionDetection
* DefenderBackdoor
* DefenderBehaviorSuspiciousActivity
* DefenderMalwareExecuted
* DefenderServerAlertDomainController
* DupTokenPrivilegeEscalationDetector
* FakeWindowsBinary
* IoaMaliciousCmdlets
* LivingOffTheLandBinary
* MicrosoftSignedBinaryAbuse
* MicrosoftSignedBinaryScriptletAbuse
* MLFileBasedWithRemoting
* MLSuspSvchostBehavior
* ReadSensitiveMemory
* RemoteCodeInjection-IREnabled
* Scuba-EchoSeenOverPipeOnLocalhost
* Scuba-SuspiciousWebScriptFileDrop
* تسجيل DLL مريب بواسطة odbcconf
* نشاط DPAPI مريب
* تنفيذ عملية Exchange المشبوهة
* تشغيل مهمة مجدولة مريبة
* مريبLdapQueryDetector
* علامة جدولة مريبة
* يفتح التطبيق غير الموثوق به اتصال RDP

</details>

### <a name="identify-the-line-of-business-lob-apps-that-are-unavailable-due-to-the-incident"></a>تحديد تطبيقات خط العمل (LOB) غير المتوفرة بسبب الحدث

* هل يتطلب التطبيق هوية؟
  * كيف يتم تنفيذ المصادقة؟
  * كيف يتم تخزين بيانات الاعتماد مثل الشهادات أو الأسرار وإدارتها؟
* هل النسخ الاحتياطية التي تم تقييمها للتطبيق وتكوينه وبياناته متوفرة؟
* تحديد عملية استرداد الاختراق.

## <a name="eradication-and-recovery"></a>مكافحة الهزات واسترداده

استخدم هذه الخطوات لإزالة المخاطر واسترداد الموارد التالفة.

### <a name="step-1-verify-your-backups"></a>الخطوة 1: التحقق من النسخ الاحتياطية

إذا كان لديك نسخ احتياطية دون اتصال، يمكنك على الأرجح استعادة البيانات التي تم تشفيرها بعد إزالة حمولة برامج الفدية الضارة (البرامج الضارة) من بيئتك وبعد التحقق من عدم وجود وصول غير مصرح به في مستأجر Microsoft 365.

### <a name="step-2-add-indicators"></a>الخطوة 2: إضافة مؤشرات

أضف أي قنوات اتصال مهاجم معروفة كمؤشرات، محظورة في جدران الحماية، وفي خوادم الوكيل، وعلى نقاط النهاية.

### <a name="step-3-reset-compromised-users"></a>الخطوة 3: إعادة تعيين المستخدمين المخترقين

إعادة تعيين كلمات المرور لأي حسابات مستخدمين معروفة تم اختراقها وتتطلب تسجيل دخول جديدا.

* ضع في اعتبارك إعادة تعيين كلمات المرور لأي حساب متميز ذي سلطة إدارية واسعة، مثل أعضاء مجموعة "مسؤولي المجال".
* إذا كان قد تم إنشاء حساب مستخدم من قبل مهاجم، فعطل الحساب. لا تحذف الحساب إلا إذا لم تكن هناك خطط لإجراء تحليلات أمنية أمنية للحادث.

### <a name="step-4-isolate-attacker-control-points"></a>الخطوة 4: عزل نقاط تحكم المهاجم

اعزل أي نقاط تحكم معروفة للمهاجمين داخل المؤسسة من الإنترنت.

### <a name="step-5-remove-malware"></a>الخطوة 5: إزالة البرامج الضارة

إزالة البرامج الضارة من الأجهزة المتأثرة.

* قم بتشغيل فحص كامل مكافحة الفيروسات الحالي على جميع أجهزة الكمبيوتر والأجهزة المشتبه بها للكشف عن الحمولة المقترنة ببرامج الفدية الضارة وإزالتها.
* لا تنس فحص الأجهزة التي تقوم بمزامنة البيانات أو أهداف محركات أقراص الشبكة المعينة.

### <a name="step-6-recover-files-on-a-cleaned-device"></a>الخطوة 6: استرداد الملفات على جهاز تم تنظيفه

استرداد الملفات على جهاز تم تنظيفه.

* يمكنك استخدام [محفوظات الملفات](https://support.microsoft.com/help/17128) في Windows 11 Windows 10 Windows 8.1 وحماية النظام في Windows 7 لمحاولة استرداد الملفات والمجلدات المحلية.

### <a name="step-7-recover-files-in-onedrive-for-business"></a>الخطوة 7: استرداد الملفات في OneDrive for Business

استرداد الملفات في OneDrive for Business.

* تسمح لك استعادة الملفات في OneDrive for Business باستعادة OneDrive بأكمله إلى نقطة زمنية سابقة خلال آخر 30 يوما. لمزيد من المعلومات، راجع [استعادة OneDrive](https://support.microsoft.com/office/restore-your-onedrive-fa231298-759d-41cf-bcd0-25ac53eb8a15).

### <a name="step-8-recover-deleted-email"></a>الخطوة 8: استرداد البريد الإلكتروني المحذوفة

استرداد البريد الإلكتروني المحذوفة.

* في الحالة النادرة التي حذفت برامج الفدية الضارة جميع رسائل البريد الإلكتروني في علبة بريد، يمكنك استرداد العناصر المحذوفة. راجع [استرداد الرسائل المحذوفة في علبة بريد المستخدم في Exchange Online](/exchange/recipients-in-exchange-online/manage-user-mailboxes/recover-deleted-messages).

### <a name="step-9-re-enable-exchange-activesync-and-onedrive-sync"></a>الخطوة 9: إعادة تمكين Exchange ActiveSync المزامنة من OneDrive

* بعد تنظيف أجهزة الكمبيوتر والأجهزة واسترداد البيانات، يمكنك إعادة تمكين Exchange ActiveSync المزامنة من OneDrive التي قمت بتعطيلها مسبقا في الخطوة 3 من الاحتواء.
