---
title: مرجع قواعد الحد من سطح الهجوم
description: تسرد تفاصيل حول قواعد الحد من سطح الهجوم على أساس كل قاعدة.
keywords: قواعد الحد من سطح الهجوم، قواعد ASR، قواعد asr، الوركين، نظام منع اقتحام المضيف، قواعد الحماية، قواعد مكافحة استغلال، مكافحة استغلال، قواعد استغلال، قواعد منع الإصابة، Microsoft Defender ل Endpoint، تكوين قواعد ASR، وصف قاعدة ASR
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
audience: ITPro
author: jweston-1
ms.author: v-jweston
ms.reviewer: oogunrinde, sugamar,
manager: dansimp
ms.custom: asr
ms.technology: mde
ms.topic: article
ms.collection: M365-security-compliance
ms.date: 02/04/2022
ms.openlocfilehash: 5ffbe15fe9fa06e7c06546f9452d6c4f2bddfc39
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/08/2022
ms.locfileid: "63578591"
---
# <a name="attack-surface-reduction-rules-reference"></a>مرجع قواعد الحد من سطح الهجوم

**ينطبق على:**

- [خطة Microsoft Defender لنقطة النهاية 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

توفر هذه المقالة معلومات حول قواعد الحد من الهجمات:

- [إصدارات نظام التشغيل المعتمدة](#supported-operating-systems)
- [أنظمة إدارة التكوين المعتمدة](#supported-configuration-management-systems)
- [تفاصيل الإعلامات والتنبيهات لكل قاعدة](#per-rule-alert-and-notification-details)
- [الأوصاف لكل قاعدة](#per-rule-descriptions)
  - أوصاف القاعدة
  - GUIDs
  - أسماء قواعد نظام إدارة التكوين

## <a name="public-preview-supported-operating-systems"></a>المعاينة العامة: أنظمة التشغيل المعتمدة

> [!IMPORTANT]
> تتعلق بعض المعلومات بالمنتج الذي تم إصداره مسبقا والذي قد يتم تعديله بشكل كبير قبل طرحه تجاريا. لا تقدم Microsoft أي ضمانات، صريحة أو ضمنية، فيما يتعلق بالمعلومات المتوفرة هنا.

يسرد الجدول التالي أنظمة التشغيل المعتمدة لقواعد الحد من سطح الهجوم التي تكون حاليا منتجا مسبقا. يتم سرد القواعد بالترتيب الأبجدي. ما لم يتم الإشارة إلى خلاف ذلك، فإن الحد الأدنى لنسخة Windows&nbsp; 10 هو الإصدار 1709 (RS3، النسخة 16299) أو الإصدارات الأحدث؛ الحد الأدنى لنسخة Windows&nbsp; Server هو الإصدار 1809 أو إصدار أحدث.

> [!NOTE]
> تتوفر قواعد تقليل مساحة الهجوم في Windows&nbsp; Server2012R2&nbsp;&nbsp;&nbsp; و Windows Server2016&nbsp; للأجهزة المجهزة باستخدام حزمة الحلول الموحدة الحديثة. لمزيد من المعلومات، راجع وظائف جديدة في الحل الموحد الحديث Windows [Server 2012 R2 و2016 Preview](/microsoft-365/security/defender-endpoint/configure-server-endpoints#new-functionality-in-the-modern-unified-solution-for-windows-server-2012-r2-and-2016-preview).
>

| اسم القاعدة | &nbsp;Windows Server 2016 <sup>[[1](#fn1)]<sup></sup> | &nbsp;Windows Server 2012 R2 <sup>[[1](#fn1)]<sup></sup> |
|---|:---:|:---:|
|[حظر إساءة استخدام برامج التشغيل الموقعة المعرضة للاستغلال](#block-abuse-of-exploited-vulnerable-signed-drivers) | Y | Y |
|[منع Adobe Reader من إنشاء عمليات الأطفال](#block-adobe-reader-from-creating-child-processes) | Y | Y |
|[حظر جميع Office من إنشاء عمليات الأطفال](#block-all-office-applications-from-creating-child-processes) | Y | Y |
|[حظر سرقة بيانات الاعتماد من Windows فرعي لسلطات الأمان المحلية (lsass.exe)](#block-credential-stealing-from-the-windows-local-security-authority-subsystem) | Y | Y |
|[حظر المحتوى القابل للتنفيذ من عميل البريد الإلكتروني والبريد الإلكتروني](#block-executable-content-from-email-client-and-webmail) | Y | Y |
|[حظر تشغيل الملفات القابلة للتنفيذ إلا إذا كانت تلبي معيار قائمة ذات عمر أو عمر أو قائمة موثوق بها](#block-executable-files-from-running-unless-they-meet-a-prevalence-age-or-trusted-list-criterion) | Y | Y |
|[حظر تنفيذ البرامج النصية التي يحتمل أن تكون غير مهية](#block-execution-of-potentially-obfuscated-scripts) | Y | Y |
|[حظر JavaScript أو VBScript من بدء تشغيل المحتوى القابل للتنفيذ الذي تم تنزيله](#block-javascript-or-vbscript-from-launching-downloaded-executable-content) | N | N |
|[حظر Office من إنشاء محتوى قابل للتنفيذ](#block-office-applications-from-creating-executable-content) | Y | Y |
|[حظر Office من إدخال التعليمات البرمجية في عمليات أخرى](#block-office-applications-from-injecting-code-into-other-processes)  | Y | Y |
|[منع Office الاتصالات من إنشاء عمليات الطفل](#block-office-communication-application-from-creating-child-processes) | Y | Y |
|[حظر الثبات عبر اشتراك حدث](#block-persistence-through-wmi-event-subscription) \* WMI _استثناءات الملفات والمجلدات غير معتمدة._ | N | N |
|[إنشاءات عملية الحظر التي تنشأ من أوامر PSExec و WMI](#block-process-creations-originating-from-psexec-and-wmi-commands) | Y | Y |
|[حظر العمليات غير الملوثة وغير الموقعة التي يتم تشغيلها من USB](#block-untrusted-and-unsigned-processes-that-run-from-usb) | Y | Y |
|[حظر مكالمات Win32 API من وحدات Office الماكرو](#block-win32-api-calls-from-office-macros) | N | N |
|[استخدام الحماية المتقدمة من برامج الفدية الضارة](#use-advanced-protection-against-ransomware) | Y | Y |
|  |  |  |

(<a id="fn1">1</a>) يشير إلى الحل الموحد الحديث Windows Server 2012 و2016. لمزيد من المعلومات، راجع [Windows إلى خدمة Defender for Endpoint](configure-server-endpoints.md).

_إنهاء المعاينة العامة: أنظمة التشغيل المعتمدة_

## <a name="supported-operating-systems"></a>أنظمة التشغيل المعتمدة

يسرد الجدول التالي أنظمة التشغيل المعتمدة للقواعد التي يتم إصدارها حاليا للتوفر العام. يتم سرد القواعد بالترتيب الأبجدي.

> [!Note]
>
> ما لم يتم الإشارة إلى خلاف ذلك، فإن الحد الأدنى لنسخة Windows&nbsp; 10 هو الإصدار 1709 (RS3، النسخة 16299) أو الإصدارات الأحدث؛ الحد الأدنى لنسخة Windows&nbsp; Server هو الإصدار 1809 أو إصدار أحدث.
>

|اسم القاعدة|&nbsp;Windows 10|&nbsp;Windows Server 2019|&nbsp;Windows Server|
|---|:---:|:---:|:---:|
|[حظر إساءة استخدام برامج التشغيل الموقعة المعرضة للاستغلال](#block-abuse-of-exploited-vulnerable-signed-drivers) | Y | Y | Y <br><br> الإصدار 1803 (قناة نصف سنوية) أو إصدار أحدث |
|[منع Adobe Reader من إنشاء عمليات الأطفال](#block-adobe-reader-from-creating-child-processes) | الإصدار Y 1809 أو الإصدارات الأحدث | Y | Y  <br><br> |
|[حظر جميع Office من إنشاء عمليات الأطفال](#block-all-office-applications-from-creating-child-processes) | Y | Y | Y <br><br> |
|[حظر سرقة بيانات الاعتماد من Windows فرعي لسلطات الأمان المحلية (lsass.exe)](#block-credential-stealing-from-the-windows-local-security-authority-subsystem) | الإصدار Y 1803 أو الإصدارات الأحدث | Y <br><br> | Y <br><br> |
|[حظر المحتوى القابل للتنفيذ من عميل البريد الإلكتروني والبريد الإلكتروني](#block-executable-content-from-email-client-and-webmail) | Y | Y <br><br> | Y <br><br> |
|[حظر تشغيل الملفات القابلة للتنفيذ إلا إذا كانت تلبي معيار قائمة ذات عمر أو عمر أو قائمة موثوق بها](#block-executable-files-from-running-unless-they-meet-a-prevalence-age-or-trusted-list-criterion) | الإصدار Y 1803 أو الإصدارات الأحدث | Y <br><br> | Y <br><br> |
|[حظر تنفيذ البرامج النصية التي يحتمل أن تكون غير مهية](#block-execution-of-potentially-obfuscated-scripts) | Y | Y <br><br> | Y <br><br> |
|[حظر JavaScript أو VBScript من بدء تشغيل المحتوى القابل للتنفيذ الذي تم تنزيله](#block-javascript-or-vbscript-from-launching-downloaded-executable-content) | Y | Y <br><br> | Y <br><br> |
|[حظر Office من إنشاء محتوى قابل للتنفيذ](#block-office-applications-from-creating-executable-content) | Y | Y <br><br> | Y <br><br> |
|[حظر Office من إدخال التعليمات البرمجية في عمليات أخرى](#block-office-applications-from-injecting-code-into-other-processes)  | Y | Y <br><br> | Y <br><br> |
|[منع Office الاتصالات من إنشاء عمليات الطفل](#block-office-communication-application-from-creating-child-processes) | Y | Y <br><br> | Y <br><br> |
|[حظر الثبات عبر اشتراك حدث WMI](#block-persistence-through-wmi-event-subscription) <br><br> \*_استثناءات الملفات والمجلدات غير معتمدة._ | الإصدار Y 1903 (النسخة 18362) أو الإصدارات الأحدث| Y | Y <br><br> الإصدار 1903 (النسخة 18362) أو الإصدارات الأحدث |
|[إنشاءات عملية الحظر التي تنشأ من أوامر PSExec و WMI](#block-process-creations-originating-from-psexec-and-wmi-commands) | الإصدار Y 1803 أو الإصدارات الأحدث | Y <br><br> | Y <br><br>  |
|[حظر العمليات غير الملوثة وغير الموقعة التي يتم تشغيلها من USB](#block-untrusted-and-unsigned-processes-that-run-from-usb) | Y | Y <br><br> | Y <br><br> |
|[حظر مكالمات Win32 API من وحدات Office الماكرو](#block-win32-api-calls-from-office-macros) | Y | Y <br><br> | Y <br><br> |
|[استخدام الحماية المتقدمة من برامج الفدية الضارة](#use-advanced-protection-against-ransomware) | الإصدار Y 1803 أو الإصدارات الأحدث | Y <br><br> | Y <br><br> |
|  |  |  |  |

## <a name="supported-configuration-management-systems"></a>أنظمة إدارة التكوين المعتمدة

يتم سرد الارتباطات إلى معلومات حول إصدارات نظام إدارة التكوين المشار إليها في هذا الجدول أسفل هذا الجدول.

|اسم القاعدة | Intune | إدارة نقاط النهاية من Microsoft |Microsoft Endpoint Configuration Manager |نهج المجموعة<sup>[[1](#fn1)]<sup></sup> | PowerShell<sup>[[1](#fn1)]<sup></sup>  |
|---|:---:|:---:|:---:|:---:|:---:|
|[حظر إساءة استخدام برامج التشغيل الموقعة المعرضة للاستغلال](#block-abuse-of-exploited-vulnerable-signed-drivers) | Y  | Y MEM OMA-URI |   | Y  |  Y |
|[منع Adobe Reader من إنشاء عمليات الأطفال](#block-adobe-reader-from-creating-child-processes) | Y |   | Y | Y  | Y  |
|[حظر جميع Office من إنشاء عمليات الأطفال](#block-all-office-applications-from-creating-child-processes) | Y |   |Y <br><br> CB 1710 | Y  | Y  |
|[حظر سرقة بيانات الاعتماد من Windows فرعي لسلطات الأمان المحلية (lsass.exe)](#block-credential-stealing-from-the-windows-local-security-authority-subsystem) | Y  |   | Y <br><br>CB 1802 | Y  | Y  |
|[حظر المحتوى القابل للتنفيذ من عميل البريد الإلكتروني والبريد الإلكتروني](#block-executable-content-from-email-client-and-webmail) | Y |  |Y <br><br> CB 1710 | Y | Y  |
|[حظر تشغيل الملفات القابلة للتنفيذ إلا إذا كانت تلبي معيار قائمة ذات عمر أو عمر أو قائمة موثوق بها](#block-executable-files-from-running-unless-they-meet-a-prevalence-age-or-trusted-list-criterion) | Y |   | Y <br><br> CB 1802 |  Y |  Y |
|[حظر تنفيذ البرامج النصية التي يحتمل أن تكون غير مهية](#block-execution-of-potentially-obfuscated-scripts) | Y |   |  Y  <br><br> CB 1710 | Y  | Y  |
|[حظر JavaScript أو VBScript من بدء تشغيل المحتوى القابل للتنفيذ الذي تم تنزيله](#block-javascript-or-vbscript-from-launching-downloaded-executable-content) | Y |   | Y <br><br> CB 1710 | Y  | Y  |
|[حظر Office من إنشاء محتوى قابل للتنفيذ](#block-office-applications-from-creating-executable-content) | Y |  |Y <br><br> CB 1710 | Y  | Y  |
|[حظر Office من إدخال التعليمات البرمجية في عمليات أخرى](#block-office-applications-from-injecting-code-into-other-processes) | Y |  | Y <br><br> CB 1710 | Y  | Y  |
|[منع Office الاتصالات من إنشاء عمليات الطفل](#block-office-communication-application-from-creating-child-processes) | Y |  |Y <br><br> CB 1710 | Y  | Y  |
|[حظر الثبات عبر اشتراك حدث WMI](#block-persistence-through-wmi-event-subscription) |  |  |  |Y   | Y  |
|[إنشاءات عملية الحظر التي تنشأ من أوامر PSExec و WMI](#block-process-creations-originating-from-psexec-and-wmi-commands) | Y |   |   |  Y | Y  |
|[حظر العمليات غير الملوثة وغير الموقعة التي يتم تشغيلها من USB](#block-untrusted-and-unsigned-processes-that-run-from-usb) | Y |   |Y <br><br> CB 1802  | Y  | Y  |
|[حظر مكالمات Win32 API من وحدات Office الماكرو](#block-win32-api-calls-from-office-macros) | Y |   | Y <br><br> CB 1710  | Y  |  Y |
|[استخدام الحماية المتقدمة من برامج الفدية الضارة](#use-advanced-protection-against-ransomware) | Y |   | Y <br><br> CB 1802 | Y  | Y  |
|  |  |  |  |  |  |

  (<a id="fn1">1</a>) يمكنك تكوين قواعد الحد من سطح الهجوم على أساس كل قاعدة باستخدام GUID الخاص بأي قاعدة.

- [Configuration Manager CB 1710](/configmgr/core/servers/manage/updates)
- [Configuration Manager CB 1802](/configmgr/core/servers/manage/updates)
- [إدارة نقاط النهاية من Microsoft CB 1710](/configmgr/core/servers/manage/updates)
- [System Center Configuration Manager (SCCM) CB 1710](/configmgr/core/servers/manage/updates) <br>_تم الآن Microsoft Endpoint Configuration Manager SCCM._

## <a name="per-rule-alert-and-notification-details"></a>تفاصيل الإعلامات والتنبيه لكل قاعدة

يتم إنشاء الإعلامات المنبثقة لجميع القواعد في وضع الحظر. لن تنشئ القواعد في أي وضع آخر إعلامات منت المنبثقة

بالنسبة إلى القواعد التي تم تحديد "حالة القاعدة":

- يتم استخدام قواعد \<ASR Rule, Rule State\> ASR ذات التركيبات لسطح التنبيهات (الإعلامات المنبثقة) على Microsoft Defender لنقطة النهاية فقط للأجهزة على مستوى الكتلة السحابية العالية. لن تنشئ الأجهزة التي لا تعمل على مستوى كتلة سحابية عالية تنبيهات لأي <قاعدة ASR أو مجموعة> قاعدة
- الكشف التلقائي والاستجابة على النقط النهائية التنبيهات لقواعد ASR في الحالات المحددة، ولكن فقط للأجهزة التي تعمل بمستوى كتلة سحابية عال.

| اسم القاعدة: | حالة القاعدة: | إنشاء تنبيهات في الكشف التلقائي والاستجابة على النقط النهائية؟ <br> (نعم&nbsp;\|&nbsp;لا) | هل تنشئ إعلامات منت المنبثقة؟ <br> (نعم&nbsp;\|&nbsp;لا) |
|---|:---:|:---:|:---:|
|   |   |  _فقط للأجهزة على مستوى الكتلة السحابية العالية_ | _في وضع الحظر فقط_ |
|[حظر إساءة استخدام برامج التشغيل الموقعة المعرضة للاستغلال](#block-abuse-of-exploited-vulnerable-signed-drivers) |   | N  | Y |
|[منع Adobe Reader من إنشاء عمليات الأطفال](#block-adobe-reader-from-creating-child-processes) | حظر  | Y <br> يتطلب جهازا على مستوى كتلة عالية السحابة  | Y <br> يتطلب جهازا على مستوى كتلة عالية السحابة |
|[حظر جميع Office من إنشاء عمليات الأطفال](#block-all-office-applications-from-creating-child-processes) |   | N | Y |
|[حظر سرقة بيانات الاعتماد من Windows فرعي لسلطات الأمان المحلية (lsass.exe)](#block-credential-stealing-from-the-windows-local-security-authority-subsystem) |   | N | Y |
|[حظر المحتوى القابل للتنفيذ من عميل البريد الإلكتروني والبريد الإلكتروني](#block-executable-content-from-email-client-and-webmail) |   | Y <br> يتطلب جهازا على مستوى كتلة عالية السحابة | Y <br> يتطلب جهازا على مستوى كتلة عالية السحابة |
|[حظر تشغيل الملفات القابلة للتنفيذ إلا إذا كانت تلبي معيار قائمة ذات عمر أو عمر أو قائمة موثوق بها](#block-executable-files-from-running-unless-they-meet-a-prevalence-age-or-trusted-list-criterion) |   | N | Y |
|[حظر تنفيذ البرامج النصية التي يحتمل أن تكون غير مهية](#block-execution-of-potentially-obfuscated-scripts) |  AuditBlock&nbsp;\|&nbsp; | Y \| Y <br> يتطلب جهازا على مستوى كتلة عالية السحابة  | N \| Y <br> يتطلب جهازا على مستوى كتلة عالية السحابة |
|[حظر JavaScript أو VBScript من بدء تشغيل المحتوى القابل للتنفيذ الذي تم تنزيله](#block-javascript-or-vbscript-from-launching-downloaded-executable-content) | حظر | Y <br> يتطلب جهازا على مستوى كتلة عالية السحابة  | Y <br> يتطلب جهازا على مستوى كتلة عالية السحابة |
|[حظر Office من إنشاء محتوى قابل للتنفيذ](#block-office-applications-from-creating-executable-content) |   | N | Y |
|[حظر Office من إدخال التعليمات البرمجية في عمليات أخرى](#block-office-applications-from-injecting-code-into-other-processes)  |   | N | Y |
|[منع Office الاتصالات من إنشاء عمليات الطفل](#block-office-communication-application-from-creating-child-processes) |  |  N | Y |
|[حظر الثبات عبر اشتراك حدث WMI](#block-persistence-through-wmi-event-subscription) |  AuditBlock&nbsp;\|&nbsp; | Y \| Y <br> يتطلب جهازا على مستوى كتلة عالية السحابة  | N \| Y <br> يتطلب جهازا على مستوى كتلة عالية السحابة |
|[إنشاءات عملية الحظر التي تنشأ من أوامر PSExec و WMI](#block-process-creations-originating-from-psexec-and-wmi-commands) |   | N | Y |
|[حظر العمليات غير الملوثة وغير الموقعة التي يتم تشغيلها من USB](#block-untrusted-and-unsigned-processes-that-run-from-usb) | AuditBlock&nbsp;\|&nbsp; | Y \| Y <br> يتطلب جهازا على مستوى كتلة عالية السحابة  | N \| Y <br> يتطلب جهازا على مستوى كتلة عالية السحابة |
|[حظر مكالمات Win32 API من وحدات Office الماكرو](#block-win32-api-calls-from-office-macros) |   | N | Y |
|[استخدام الحماية المتقدمة من برامج الفدية الضارة](#use-advanced-protection-against-ransomware) | AuditBlock&nbsp;\|&nbsp; | Y \| Y <br> يتطلب جهازا على مستوى كتلة عالية السحابة  | N \| Y <br> يتطلب جهازا على مستوى كتلة عالية السحابة |
|   |   |   |   |
  
## <a name="asr-rule-modes"></a>أوضاع قواعد ASR

- **غير مكون أو** **تعطيل**: هذه هي الحالة التي لم يتم فيها تمكين قاعدة ASR أو تعطيلها. التعليمة البرمجية لهذه الحالة = 0.
- **كتلة**: هذه هي الحالة التي يتم فيها تمكين قاعدة ASR. التعليمة البرمجية لهذه الحالة هي 1.
- **التدقيق**: هذه هي الحالة التي يتم فيها تقييم قاعدة ASR للسلوك التأثيري تجاه المؤسسة أو البيئة التي يتم نشرها فيها. التعليمة البرمجية لهذه الحالة هي 2.
- **تحذير** هذه هي الحالة التي يتم فيها تمكين قاعدة ASR وهي تقدم إعلاما للمستخدم النهائي، ولكنها تسمح للمستخدم بتجاوز الحظر. التعليمة البرمجية لهذه الحالة هي 6.

_وضع التحذير_ هو نوع وضع الحظر الذي ينبه المستخدمين إلى الإجراءات التي قد تكون ذات مخاطر. يمكن للمستخدمين اختيار تجاوز رسالة تحذير الحظر والسماح بالتحرك الأساسي. يمكن للمستخدمين تحديد **موافق** لفرض الحظر، أو تحديد خيار التجاوز - إلغاء **الحظر** - من خلال الإعلام المنبثق المنبثق للمستخدم النهائي الذي يتم إنشاؤه في وقت الحظر. بعد إلغاء حظر التحذير، يتم السماح بالعملية حتى المرة التالية التي تظهر فيها رسالة التحذير، وفي الوقت الذي يحتاج فيه المستخدم إلى إعادة أداء الإجراء.

إذا تم النقر فوق زر السماح، سيتم إيقاف الحظر لمدة 24 ساعة. بعد مرور 24 ساعة، سيحتاج المستخدم إلى السماح بالحظر مرة أخرى. يتم دعم وضع التحذير لقواعد ASR فقط للأجهزة التي تعمل ب RS5+ (1809+). إذا تم تعيين تجاوز لقواعد ASR على الأجهزة ذات الإصدارات القديمة، ستكون القاعدة في الوضع المحظور.

يمكنك أيضا تعيين قاعدة في وضع التحذير عبر PowerShell عن طريق تحديد قاعدة AttackSurfaceReductionRules_Actions ك "تحذير". على سبيل المثال:

```powershell
-command "& {&'Add-MpPreference' -AttackSurfaceReductionRules_Ids 56a863a9-875e-4185-98a7-b882c64b5ce5 -AttackSurfaceReductionRules_Actions Warn"} 
```

## <a name="per-rule-descriptions"></a>أوصاف لكل قاعدة

### <a name="block-abuse-of-exploited-vulnerable-signed-drivers"></a>حظر إساءة استخدام برامج التشغيل الموقعة المعرضة للاستغلال

تمنع هذه القاعدة تطبيقا من كتابة برنامج تشغيل موقع ضعيف على القرص. يمكن استغلال برامج \-  \- التشغيل الموقعة المعرضة للخطر داخل البرية بواسطة التطبيقات المحلية التي تملك امتيازات كافية للوصول إلى النواة. تمكن برامج التشغيل الموقعة الضعيفة المهاجمين من تعطيل حلول الأمان أو التحايل عليها، مما يؤدي في النهاية إلى اختراق النظام.

لا **تمنع قاعدة حظر إساءة** استخدام برامج التشغيل الموقعة المعرضة للاستغلال تحميل برنامج تشغيل موجود بالفعل على النظام.

> [!NOTE]
>
> يمكنك تكوين هذه القاعدة باستخدام MEM OMA-URI. راجع [MEM OMA-URI](enable-attack-surface-reduction.md#mem) لتكوين القواعد المخصصة.
>
> يمكنك أيضا تكوين هذه القاعدة باستخدام [PowerShell](enable-attack-surface-reduction.md#powershell).
>
> لفحص برنامج تشغيل، استخدم موقع الويب هذا [لإرسال برنامج تشغيل للتحليل](https://www.microsoft.com/en-us/wdsi/driversubmission).

<!--The above link is the 'only link' that exists for having drivers examined. The 'en-us' component is required to make the link work. Any alterations to this link will result in a 404.
-->

اسم Intune: `Block abuse of exploited vulnerable signed drivers` (غير متوفر بعد)

اسم مدير التكوين: غير متوفر بعد
  
GUID:  `56a863a9-875e-4185-98a7-b882c64b5ce5`

<!-- Hide this intro with no subsequent list items
Advanced hunting action type:
-->

<!-- 
Dependencies:
-->

### <a name="block-adobe-reader-from-creating-child-processes"></a>منع Adobe Reader من إنشاء عمليات الأطفال

تمنع هذه القاعدة الهجمات من خلال منع Adobe Reader من إنشاء العمليات.

من خلال الهندسة الاجتماعية أو عمليات استغلال، يمكن للبرامج الضارة تنزيل الحمولات وإطلاقها، والخروج من Adobe Reader. من خلال منع إنشاء عمليات الأطفال بواسطة Adobe Reader، يتم منع البرامج الضارة التي تحاول استخدامها كمتجه من الانتشار.

اسم Intune: `Process creation from Adobe Reader (beta)`

اسم مدير التكوين: غير متوفر بعد

GUID: `7674ba52-37eb-4a4f-a9a1-f0f9a1619a2c`

نوع إجراء الصيد المتقدم:

- AsrAdobeReaderChildProcessAudited
- AsrAdobeReaderChildProcessBlocked

التبعيات: MDAV

### <a name="block-all-office-applications-from-creating-child-processes"></a>حظر جميع Office من إنشاء عمليات الأطفال

تمنع هذه القاعدة Office التطبيقات من إنشاء عمليات الطفل. Office تطبيقات Word Excel و PowerPoint و OneNote و Access.

إنشاء عمليات الأطفال الضارة هي استراتيجية برامج ضارة شائعة. غالبا ما Office البرامج الضارة التي تستخدمها كمتجه إلى تشغيل وحدات ماكرو VBA وتستغل التعليمات البرمجية لتنزيل المزيد من التحميلات ومحاولة تشغيلها. ومع ذلك، قد تنشئ بعض تطبيقات خط العمل المشروعة أيضا عمليات طفل لأغراض غير مهينة؛ مثل تباعد موجه أوامر أو استخدام PowerShell لتكوين إعدادات التسجيل.

اسم Intune: `Office apps launching child processes`

اسم مدير التكوين: `Block Office application from creating child processes`

GUID: `d4f940ab-401b-4efc-aadc-ad5f3c50688a`

نوع إجراء الصيد المتقدم:

- AsrOfficeChildProcessAudited
- AsrOfficeChildProcessBlocked

التبعيات: MDAV

### <a name="block-credential-stealing-from-the-windows-local-security-authority-subsystem"></a>حظر سرقة بيانات الاعتماد من Windows فرعي لسلطات الأمان المحلية

تساعد هذه القاعدة على منع سرقة بيانات الاعتماد من خلال تأمين خدمة النظام الفرعي لسلطات الأمان المحلية (LSASS).

يصادق LSASS المستخدمين الذين سجلوا الدخول على Windows كمبيوتر. يمنع Microsoft Defender Credential Guard Windows عادة محاولات استخراج بيانات الاعتماد من LSASS. ومع ذلك، لا يمكن لبعض المؤسسات تمكين "حماية بيانات الاعتماد" على جميع أجهزة الكمبيوتر الخاصة بها بسبب مشاكل التوافق مع برامج تشغيل البطاقات الذكية المخصصة أو البرامج الأخرى التي يتم تحميلها إلى "هيئة الأمان المحلية" (LSA). في هذه الحالات، يمكن للمهاجمين استخدام أدوات اختراق مثل Mimikatz لمسح كلمات مرور نصية وهاشطات NTLM من LSASS.

> [!NOTE]
> في بعض التطبيقات، تقوم التعليمة البرمجية تعداد جميع العمليات قيد التشغيل ومحاولة فتحها باستخدام أذونات شاملة. وترفض هذه القاعدة الإجراء المفتوح لعملية التطبيق وتسجل التفاصيل في سجل أحداث الأمان. قد ينتج عن هذه القاعدة الكثير من الضوضاء. إذا كان لديك تطبيق يعدد ببساطة LSASS، ولكن ليس له أي تأثير حقيقي في الوظائف، فلا حاجة إلى إضافته إلى قائمة الاستثناء. في حد ذاته، لا يشير إدخال سجل الأحداث هذا بالضرورة إلى وجود خطر ضار.
  
> [!IMPORTANT]
> ستتغير الحالة الافتراضية لقاعدة تقليل مساحة الهجوم (ASR) "حظر سرقة بيانات الاعتماد من نظام فرعي لسلطات الأمان المحلية في Windows (lsass.exe)") من غير تكوين إلى "تكوين" وسيتغير  الوضع الافتراضي إلى **حظر**. ستبقى كل قواعد ASR الأخرى في حالتها الافتراضية: **لم يتم تكوينها**. تم بالفعل تضمين منطق تصفية إضافي في القاعدة لتقليل إعلامات المستخدم. يمكن للعملاء تكوين القاعدة إلى الأوضاع **تدقيق** أو تحذير  أو تعطيل، والتي ستتجاوز الوضع الافتراضي. وظيفة هذه القاعدة هي نفسها، سواء تم تكوين القاعدة في الوضع الافتراضي، أو إذا قمت بتمكين وضع الحظر يدويا.  

اسم Intune: `Flag credential stealing from the Windows local security authority subsystem`

اسم مدير التكوين: `Block credential stealing from the Windows local security authority subsystem`

GUID: `9e6c4e1f-7d60-472f-ba1a-a39ef669e4b2`

نوع إجراء الصيد المتقدم:

- AsrLsasCredentialTheftAudited
- AsrLsasCredentialTheftBlocked

التبعيات: MDAV

### <a name="block-executable-content-from-email-client-and-webmail"></a>حظر المحتوى القابل للتنفيذ من عميل البريد الإلكتروني والبريد الإلكتروني

تمنع هذه القاعدة أنواع الملفات التالية من التشغيل من البريد الإلكتروني المفتوح ضمن تطبيق Microsoft Outlook أو Outlook.com وموفري بريد الويب الشائعين الآخرين:

- الملفات القابلة للتنفيذ (مثل .exe أو .dll أو .scr)
- ملفات البرامج النصية (مثل ملف powerShell .ps أو Visual Basic .vbs أو JavaScript .js)

اسم Intune: `Execution of executable content (exe, dll, ps, js, vbs, etc.) dropped from email (webmail/mail client) (no exceptions)`

إدارة نقاط النهاية من Microsoft الاسم:`Block executable content from email client and webmail`

GUID: `be9ba2d9-53ea-4cdc-84e5-9b1eeee46550`

نوع إجراء الصيد المتقدم:

- AsrExecutableEmailContentAudited
- AsrExecutableEmailContentBlocked

التبعيات: MDAV

> [!NOTE]
> القاعدة حظر **المحتوى القابل للتنفيذ من عميل البريد** الإلكتروني والبريد على الويب له الأوصاف البديلة التالية، استنادا إلى التطبيق الذي تستخدمه:
>
> - Intune (ملفات تعريف التكوين): تم إسقاط تنفيذ المحتوى القابل للتنفيذ (مثل، dll، ps، js، vbs، إلخ.) من البريد الإلكتروني (webmail/mail client) (بدون استثناءات).
> - إدارة نقاط النهاية: حظر تنزيل المحتوى القابل للتنفيذ من البريد الإلكتروني والعملاء على بريد الويب.
> - نهج المجموعة: حظر المحتوى القابل للتنفيذ من عميل البريد الإلكتروني والبريد الإلكتروني.

### <a name="block-executable-files-from-running-unless-they-meet-a-prevalence-age-or-trusted-list-criterion"></a>حظر تشغيل الملفات القابلة للتنفيذ إلا إذا كانت تلبي معيار قائمة ذات عمر أو عمر أو قائمة موثوق بها

تمنع هذه القاعدة الملفات القابلة للتنفيذ، مثل .exe أو .dll أو .scr، من بدء تشغيلها. وبالتالي، قد يكون تشغيل الملفات القابلة للتنفيذ غير الهامة أو غير المعروفة خطرا، حيث قد لا يكون من الواضح في البداية ما إذا كانت الملفات ضارة.

> [!IMPORTANT]
> يجب تمكين [الحماية التي يتم تسليمها من السحابة](/windows/security/threat-protection/microsoft-defender-antivirus/enable-cloud-protection-microsoft-defender-antivirus) لاستخدام هذه القاعدة.
>
> القاعدة حظر **تشغيل** الملفات القابلة للتنفيذ ما لم تكن تلبي معيار قائمة غير مقبول أو عمري أو موثوق به بواسطة GUID `01443614-cd74-433a-b99e-2ecdc07bfc25` تملكه Microsoft ولا يحدده المسؤولون. تستخدم هذه القاعدة الحماية التي يتم تسليمها من السحابة لتحديث قائمتها الموثوق بها بشكل منتظم.
>
> يمكنك تحديد الملفات أو المجلدات الفردية (باستخدام مسارات المجلدات أو أسماء الموارد المؤهلة بالكامل) ولكن لا يمكنك تحديد القواعد أو الاستثناءات التي تنطبق عليها.

اسم Intune: `Executables that don't meet a prevalence, age, or trusted list criteria`

اسم مدير التكوين: `Block executable files from running unless they meet a prevalence, age, or trusted list criteria`

GUID: `01443614-cd74-433a-b99e-2ecdc07bfc25`

نوع إجراء الصيد المتقدم:

- AsrUntrustedExecutableAudited
- AsrUntrustedExecutableBlocked

التبعيات: MDAV والحماية السحابية

### <a name="block-execution-of-potentially-obfuscated-scripts"></a>حظر تنفيذ البرامج النصية التي يحتمل أن تكون غير مهية

تكتشف هذه القاعدة الخصائص المريبة ضمن برنامج نصي غير مهمل.

تزيين البرنامج النصي هو أسلوب شائع يستخدمه كتاب البرامج الضارة والتطبيقات الشرعية لإخفاء الملكية الفكرية أو تقليل أوقات تحميل البرامج النصية. يستخدم كتاب البرامج الضارة أيضا التهكم لجعل قراءة التعليمات البرمجية الضارة أكثر صعوبة، مما يمنع فحص حقوق الإنسان وبرامج الأمان عن كثب.

اسم Intune: `Obfuscated js/vbs/ps/macro code`

اسم مدير التكوين: `Block execution of potentially obfuscated scripts`

GUID: `5beb7efe-fd9a-4556-801d-275e5ffc04cc`

نوع إجراء الصيد المتقدم:

- AsrObfuscatedScriptAudited
- AsrObfuscatedScriptBlocked

التبعيات: MDAV و AMSI

### <a name="block-javascript-or-vbscript-from-launching-downloaded-executable-content"></a>حظر JavaScript أو VBScript من بدء تشغيل المحتوى القابل للتنفيذ الذي تم تنزيله

تمنع هذه القاعدة البرامج النصية من تشغيل محتوى من المحتمل أن يكون ضارا تم تنزيله. غالبا ما تعمل البرامج الضارة المكتوبة ب JavaScript أو VBScript كمنزيل لإحضار البرامج الضارة الأخرى من الإنترنت و تشغيلها.

على الرغم من أن تطبيقات خط العمل غير شائعة، إلا أنها تستخدم في بعض الأحيان البرامج النصية لتنزيل المثبتات و تشغيلها.

اسم Intune: `js/vbs executing payload downloaded from Internet (no exceptions)`

اسم مدير التكوين: `Block JavaScript or VBScript from launching downloaded executable content`

GUID: `d3e037e1-3eb8-44c8-a917-57927947596d`

نوع إجراء الصيد المتقدم:

- AsrScriptExecutableDownloadAudited
- AsrScriptExecutableDownloadBlocked

التبعيات: MDAV و AMSI

### <a name="block-office-applications-from-creating-executable-content"></a>حظر Office من إنشاء محتوى قابل للتنفيذ

تمنع هذه القاعدة Office، بما في ذلك Word Excel و PowerPoint، من إنشاء محتوى يحتمل أن يكون ضارا قابلا للتنفيذ، عن طريق منع كتابة التعليمات البرمجية الضارة على القرص.

قد تحاول البرامج الضارة Office التي تسيء استخدامها كمتجهات الخروج من Office وحفظ المكونات الضارة على القرص. ستبقى هذه المكونات الضارة بعد إعادة تشغيل الكمبيوتر وثابرة على النظام. وبالتالي، فإن هذه القاعدة يتم الدفاع عنها في مقابل أسلوب استمرارية شائع.

اسم Intune: `Office apps/macros creating executable content`

اسم SCCM: `Block Office applications from creating executable content`

GUID: `3b576869-a4ec-4529-8536-b80a7769e899`

نوع إجراء الصيد المتقدم:

- AsrExecutableOfficeContentAudited
- AsrExecutableOfficeContentBlocked

التبعيات: MDAV وRPC

### <a name="block-office-applications-from-injecting-code-into-other-processes"></a>حظر Office من إدخال التعليمات البرمجية في عمليات أخرى

تمنع هذه القاعدة محاولات استخدام التعليمات البرمجية Office التطبيقات إلى عمليات أخرى.

قد يحاول المتطفلون استخدام Office لترحيل التعليمات البرمجية الضارة إلى عمليات أخرى من خلال عملية ضخ التعليمات البرمجية، بحيث يمكن أن تتهكم التعليمات البرمجية ك عملية نظيفة.

لا توجد أي أغراض عمل شرعية معروفة لاستخدام عملية ضخ التعليمات البرمجية.

تنطبق هذه القاعدة على Word Excel و PowerPoint.

اسم Intune: `Office apps injecting code into other processes (no exceptions)`

اسم مدير التكوين: `Block Office applications from injecting code into other processes`

GUID: `75668c1f-73b5-4cf0-bb93-3ecf5cb7cc84`

نوع إجراء الصيد المتقدم:

- AsrOfficeProcessInjectionAudited
- AsrOfficeProcessInjectionBlocked

التبعيات: MDAV

### <a name="block-office-communication-application-from-creating-child-processes"></a>منع Office الاتصالات من إنشاء عمليات الطفل

تمنع هذه القاعدة Outlook من إنشاء عمليات الأطفال، مع السماح في الوقت Outlook دالات شرعية.

تحمي هذه القاعدة من هجمات الهندسة الاجتماعية وتمنع استغلال التعليمات البرمجية من استغلال نقاط الضعف في Outlook. كما أنه [يحمي من Outlook](https://blogs.technet.microsoft.com/office365security/defending-against-rules-and-forms-injection/) والنماذج التي يمكن للمهاجمين استخدامها عند اختراق بيانات اعتماد المستخدم.

> [!NOTE]
> تمنع هذه القاعدة تلميحات نهج DLP وتلميحات الأدوات في Outlook. تنطبق هذه القاعدة على Outlook Outlook.com فقط.

اسم Intune: `Process creation from Office communication products (beta)`

اسم مدير التكوين: غير متوفر

GUID: `26190899-1602-49e8-8b27-eb1d0a1ce869`

نوع إجراء الصيد المتقدم:

- AsrOfficeCommAppChildProcessAudited
- AsrOfficeCommAppChildProcessBlocked

التبعيات: MDAV

### <a name="block-persistence-through-wmi-event-subscription"></a>حظر الثبات عبر اشتراك حدث WMI

تمنع هذه القاعدة البرامج الضارة من استخدام WMI لتحقيق الثبات على جهاز.

> [!IMPORTANT]
> لا تنطبق استثناءات الملفات والمجلدات على قاعدة تقليل مساحة الهجوم هذه.

تستخدم التهديدات بدون ملفات أساليب مختلفة للبقاء مخفيا، وتجنب رؤية الملفات في نظام الملفات، واكتساب التحكم في التنفيذ الدوري. قد تسيء بعض التهديدات استخدام نموذج الحدث ومستودع WMI للبقاء مخفيين.

اسم Intune: غير متوفر

اسم مدير التكوين: غير متوفر

GUID: `e6db77e5-3df2-4cf1-b95a-636979351e5b`

نوع إجراء الصيد المتقدم:

- AsrPersistenceThroughWmiAudited
- AsrPersistenceThroughWmiBlocked

التبعيات: MDAV وRPC

### <a name="block-process-creations-originating-from-psexec-and-wmi-commands"></a>إنشاءات عملية الحظر التي تنشأ من أوامر PSExec و WMI

تمنع هذه القاعدة العمليات التي يتم إنشاؤها من [خلال PsExec](/sysinternals/downloads/psexec) [و WMI](/windows/win32/wmisdk/about-wmi) من التشغيل. يمكن لكل من PsExec و WMI تنفيذ التعليمات البرمجية عن بعد، لذلك هناك خطر من استخدام البرامج الضارة لهذه الوظيفة لأغراض الأمر والتحكم، أو لنشر إصابة عبر شبكة المؤسسة.

> [!WARNING]
> استخدم هذه القاعدة فقط إذا كنت تدير أجهزتك باستخدام [Intune](/intune) أو حل MDM آخر. لا تتوافق هذه القاعدة مع الإدارة من خلال [](/configmgr) Microsoft Endpoint Configuration Manager لأن هذه القاعدة تمنع أوامر WMI التي يستخدمها عميل "إدارة التكوين" لكي تعمل بشكل صحيح.

اسم Intune: `Process creation from PSExec and WMI commands`

اسم مدير التكوين: غير قابل للتطبيق

GUID: `d1e49aac-8f56-4280-b9ba-993a6d77406c`

نوع إجراء الصيد المتقدم:

- AsrPsexecWmiChildProcessAudited
- AsrPsexecWmiChildProcessBlocked

التبعيات: MDAV

### <a name="block-untrusted-and-unsigned-processes-that-run-from-usb"></a>حظر العمليات غير الملوثة وغير الموقعة التي يتم تشغيلها من USB

باستخدام هذه القاعدة، يمكن للمسؤولين منع تشغيل الملفات القابلة للتنفيذ غير الموقعة أو غير المضمنة من محركات أقراص USB القابلة للإزالة، بما في ذلك بطاقات SD. تتضمن أنواع الملفات المحظورة ملفات قابلة للتنفيذ (مثل .exe أو .dll أو .scr)

اسم Intune: `Untrusted and unsigned processes that run from USB`

اسم مدير التكوين: `Block untrusted and unsigned processes that run from USB`

GUID: `b2b3f03d-6a65-4f7b-a9c7-1c7ef74a9ba4`

نوع إجراء الصيد المتقدم:

- AsrUntrustedUsbProcessAudited
- AsrUntrustedUsbProcessBlocked

التبعيات: MDAV

### <a name="block-win32-api-calls-from-office-macros"></a>حظر مكالمات Win32 API من وحدات Office الماكرو

تمنع هذه القاعدة وحدات ماكرو VBA من استدعاء واجهات برمجة التطبيقات ل Win32.

Office VBA مكالمات Win32 API. يمكن للبرامج الضارة إساءة استخدام هذه الإمكانية، مثل [الاتصال ب واجهات برمجة التطبيقات ل Win32 ل تشغيل رمز shellcode](https://www.microsoft.com/security/blog/2018/09/12/office-vba-amsi-parting-the-veil-on-malicious-macros/) الضار دون كتابة أي شيء مباشرة على القرص. لا تعتمد معظم المؤسسات على القدرة على الاتصال ب واجهات برمجة التطبيقات ل Win32 في وظائفها اليومية، حتى لو كانت تستخدم وحدات الماكرو بطرق أخرى.

أنظمة التشغيل المعتمدة:

- [Windows 10، الإصدار 1709](/windows/whats-new/whats-new-windows-10-version-1709)
- [Windows Server، الإصدار 1809](/windows-server/get-started/whats-new-in-windows-server-1809)
- [Windows Server 2019](/windows-server/get-started-19/whats-new-19)
- [Configuration Manager CB 1710](/configmgr/core/servers/manage/updates)

اسم Intune: `Win32 imports from Office macro code`

اسم مدير التكوين: `Block Win32 API calls from Office macros`

GUID: `92e97fa1-2edf-4476-bdd6-9dd0b4dddc7b`

نوع إجراء الصيد المتقدم:

- AsrOfficeMacroWin32ApiCallsAudited
- AsrOfficeMacroWin32ApiCallsBlocked

التبعيات: MDAV و AMSI

### <a name="use-advanced-protection-against-ransomware"></a>استخدام الحماية المتقدمة من برامج الفدية الضارة

توفر هذه القاعدة طبقة إضافية من الحماية من برامج الفدية الضارة. فهو يستخدم كلا من العميل ومعاينات السحابة لتحديد ما إذا كان الملف يشبه برامج الفدية الضارة أم لا. لا تمنع هذه القاعدة الملفات التي لها واحدة أو أكثر من السمات التالية:

- تم العثور بالفعل على الملف غير مبهج في سحابة Microsoft.
- الملف هو ملف موقع صالح.
- الملف شائع بما يكفي لكي لا يعتبر برامج الفدية الضارة.

تميل القاعدة إلى احذر لمنع برامج الفدية الضارة.

> [!NOTE]
> يجب تمكين [الحماية التي يتم تسليمها من السحابة](enable-cloud-protection-microsoft-defender-antivirus.md) لاستخدام هذه القاعدة.

اسم Intune: `Advanced ransomware protection`

اسم مدير التكوين: `Use advanced protection against ransomware`

GUID: `c1db55ab-c21a-4637-bb3f-a12568109d35`

نوع إجراء الصيد المتقدم:

- AsrRansomwareAudited
- AsrRansomwareBlocked

التبعيات: MDAV والحماية السحابية
