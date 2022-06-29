---
title: مرجع قواعد تقليل الأجزاء المعرضة للهجوم
description: يسرد تفاصيل حول قواعد تقليل الأجزاء المعرضة للهجوم على أساس كل قاعدة.
keywords: قواعد تقليل الأجزاء المعرضة للهجوم، ASR، قواعد asr، hips، نظام منع الاختراق المضيف، قواعد الحماية، قواعد مكافحة الاستغلال، مكافحة الاستغلال، قواعد الاستغلال، قواعد منع العدوى، Microsoft Defender لنقطة النهاية، تكوين قواعد ASR، وصف قاعدة ASR
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
ms.openlocfilehash: 593eb801505275210862d9b776c6e2dca290ef89
ms.sourcegitcommit: d1b60ed9a11f5e6e35fbaf30ecaeb9dfd6dd197d
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 06/29/2022
ms.locfileid: "66493010"
---
# <a name="attack-surface-reduction-rules-reference"></a>مرجع قواعد تقليل الأجزاء المعرضة للهجوم

**ينطبق على:**

- [خطة Microsoft Microsoft 365 Defender لنقطة النهاية 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Defender for Endpoint الخطة 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)
- برنامج الحماية من الفيروسات من Microsoft Defender

**منصات:**

- بالنسبة لنظام التشغيل

توفر هذه المقالة معلومات حول قواعد تقليل الهجمات:

- [إصدارات نظام التشغيل المدعومة](#supported-operating-systems)
- [أنظمة إدارة التكوين المدعومة](#supported-configuration-management-systems)
- [تفاصيل التنبيه والإعلام لكل قاعدة](#per-rule-alert-and-notification-details)
- [قاعدة ASR إلى مصفوفة GUID](#asr-rule-to-guid-matrix)
- [أوضاع قاعدة ASR](#asr-rule-modes)
- [أوصاف لكل قاعدة](#per-rule-descriptions)

## <a name="supported-operating-systems"></a>أنظمة التشغيل المدعومة

يسرد الجدول التالي أنظمة التشغيل المدعومة للقواعد التي تم إصدارها حاليا للتوفر العام. يتم سرد القواعد بترتيب أبجدي في هذا الجدول.

> [!NOTE]
>
> ما لم تتم الإشارة إلى خلاف ذلك، فإن الحد الأدنى لنسخة Windows&nbsp;10 هو الإصدار 1709 (RS3، الإصدار 16299) أو أحدث؛ الحد الأدنى لإصدار Windows&nbsp;Server هو الإصدار 1809 أو أحدث.
>
> تتوفر قواعد تقليل الأجزاء المعرضة للهجوم في Windows&nbsp;Server&nbsp;2012&nbsp;R2 وWindows&nbsp;Server&nbsp;2016 للأجهزة التي تم إلحاقها باستخدام حزمة الحلول الموحدة الحديثة. لمزيد من المعلومات، راجع [الوظائف الجديدة في الحل الموحد الحديث ل Windows Server 2012 R2 و2016 Preview](/microsoft-365/security/defender-endpoint/configure-server-endpoints#new-functionality-in-the-modern-unified-solution-for-windows-server-2012-r2-and-2016-preview).

| اسم القاعدة| Windows&nbsp;11 <br>و<br> Windows&nbsp;10 | Windows&nbsp;Server <br> 2022 <br>و<br>  Windows&nbsp;Server <br> 2019 | Windows Server | Windows&nbsp;Server <br> 2016 <sup>[[1، 2](#fn1)]<sup></sup> | Windows&nbsp;Server <br> 2012&nbsp;R2 <sup>[[1, 2](#fn1)]<sup></sup> |
|:---|:---:|:---:|:---:|:---:|:---:|
| [حظر إساءة استخدام برامج التشغيل الموقعة المعرضة للخطر](#block-abuse-of-exploited-vulnerable-signed-drivers) | Y | Y | Y <br> الإصدار 1803 (قناة المؤسسة نصف السنوية) أو إصدار أحدث | Y | Y |
| [حظر Adobe Reader من إنشاء عمليات تابعة](#block-adobe-reader-from-creating-child-processes) | Y <br> الإصدار 1809 أو أحدث <sup>[[3](#fn1)]<sup></sup> | Y | Y | Y | Y |
| [حظر كافة تطبيقات Office من إنشاء عمليات تابعة](#block-all-office-applications-from-creating-child-processes) | Y | Y | Y | Y | Y |
| [حظر سرقة بيانات الاعتماد من نظام سلطة الأمان المحلية ل Windows (lsass.exe)](#block-credential-stealing-from-the-windows-local-security-authority-subsystem) | Y <br> الإصدار 1803 أو أحدث <sup>[[3](#fn1)]<sup></sup> | Y | Y | Y | Y |
| [حظر المحتوى القابل للتنفيذ من عميل البريد الإلكتروني والبريد الإلكتروني](#block-executable-content-from-email-client-and-webmail) | Y | Y | Y | Y | Y |
| [حظر تشغيل الملفات القابلة للتنفيذ إلا إذا كانت تفي بمعيار الانتشار أو العمر أو القائمة الموثوق بها](#block-executable-files-from-running-unless-they-meet-a-prevalence-age-or-trusted-list-criterion) | Y <br> الإصدار 1803 أو أحدث <sup>[[3](#fn1)]<sup></sup> | Y | Y | Y | Y |
| [حظر تنفيذ البرامج النصية التي يحتمل أن تكون مشتتة](#block-execution-of-potentially-obfuscated-scripts) | Y | Y | Y | Y | Y |
| [حظر JavaScript أو VBScript من بدء تشغيل المحتوى القابل للتنفيذ الذي تم تنزيله](#block-javascript-or-vbscript-from-launching-downloaded-executable-content) | Y | Y | Y | N | N |
| [حظر تطبيقات Office من إنشاء محتوى قابل للتنفيذ](#block-office-applications-from-creating-executable-content) | Y | Y | Y | Y | Y |
| [حظر تطبيقات Office من إدخال التعليمات البرمجية في عمليات أخرى](#block-office-applications-from-injecting-code-into-other-processes)  | Y | Y | Y | Y | Y |
| [حظر تطبيق اتصالات Office من إنشاء عمليات تابعة](#block-office-communication-application-from-creating-child-processes) | Y | Y | Y | Y | Y |
| [حظر الثبات من خلال اشتراك حدث WMI](#block-persistence-through-wmi-event-subscription) <br> \*_استثناءات الملفات والمجلدات غير معتمدة._ | Y <br> الإصدار 1903 (النسخة 18362) أو أحدث <sup>[[3](#fn1)]<sup></sup> | Y | Y <br> الإصدار 1903 (النسخة 18362) أو أحدث | N | N |
| [حظر عمليات الإنشاء التي تنشأ من أوامر PSExec وWMI](#block-process-creations-originating-from-psexec-and-wmi-commands) | Y <br> الإصدار 1803 أو أحدث <sup>[[3](#fn1)]<sup></sup> | Y | Y | Y | Y |
| [حظر العمليات غير الموثوق بها وغير الموقعة التي يتم تشغيلها من USB](#block-untrusted-and-unsigned-processes-that-run-from-usb) | Y | Y | Y | Y | Y |
| [حظر مكالمات واجهة برمجة تطبيقات Win32 من وحدات ماكرو Office](#block-win32-api-calls-from-office-macros) | Y | Y | Y | N | N |
| [استخدام الحماية المتقدمة من برامج الفدية الضارة](#use-advanced-protection-against-ransomware) | Y <br> الإصدار 1803 أو أحدث <sup>[[3](#fn1)]<sup></sup> | Y | Y | Y | Y |

(<a id="fn1">1</a>) يشير إلى الحل الموحد الحديث ل Windows Server 2012 و2016. لمزيد من المعلومات، راجع [إلحاق خوادم Windows بخدمة Defender لنقطة النهاية](configure-server-endpoints.md).

(<a id="fn1">2</a>) بالنسبة إلى Windows&nbsp;Server 2016 وWindows&nbsp;Server 2012&nbsp;R2، الحد الأدنى المطلوب من Configuration Manager نقطة النهاية من Microsoft هو الإصدار 2111.

(<a id="fn1">3</a>) ينطبق رقم الإصدار والنسخة على Windows&nbsp;10 فقط.

## <a name="supported-configuration-management-systems"></a>أنظمة إدارة التكوين المدعومة

يتم سرد الارتباطات إلى معلومات حول إصدارات نظام إدارة التكوين المشار إليها في هذا الجدول أسفل هذا الجدول.

|اسم القاعدة | Intune | إدارة نقاط النهاية من Microsoft |Microsoft Endpoint Configuration Manager |<sup>نهج المجموعة[[1](#fn1)]<sup></sup> | PowerShell<sup>[[1](#fn1)]<sup></sup>  |
|---|:---:|:---:|:---:|:---:|:---:|
|[حظر إساءة استخدام برامج التشغيل الموقعة المعرضة للخطر](#block-abuse-of-exploited-vulnerable-signed-drivers) | Y  | Y MEM OMA-URI |   | Y  |  Y  |
|[حظر Adobe Reader من إنشاء عمليات تابعة](#block-adobe-reader-from-creating-child-processes) | Y |   |  | Y  | Y  |
|[حظر كافة تطبيقات Office من إنشاء عمليات تابعة](#block-all-office-applications-from-creating-child-processes) | Y |   |Y <br><br> CB 1710 | Y  | Y  |
|[حظر سرقة بيانات الاعتماد من نظام سلطة الأمان المحلية ل Windows (lsass.exe)](#block-credential-stealing-from-the-windows-local-security-authority-subsystem) | Y  |   | Y <br><br>CB 1802 | Y  | Y  |
|[حظر المحتوى القابل للتنفيذ من عميل البريد الإلكتروني والبريد الإلكتروني](#block-executable-content-from-email-client-and-webmail) | Y |  |Y <br><br> CB 1710 | Y | Y  |
|[حظر تشغيل الملفات القابلة للتنفيذ إلا إذا كانت تفي بمعيار الانتشار أو العمر أو القائمة الموثوق بها](#block-executable-files-from-running-unless-they-meet-a-prevalence-age-or-trusted-list-criterion) | Y |   | Y <br><br> CB 1802 |  Y |  Y |
|[حظر تنفيذ البرامج النصية التي يحتمل أن تكون مشتتة](#block-execution-of-potentially-obfuscated-scripts) | Y |   |  Y  <br><br> CB 1710 | Y  | Y  |
|[حظر JavaScript أو VBScript من بدء تشغيل المحتوى القابل للتنفيذ الذي تم تنزيله](#block-javascript-or-vbscript-from-launching-downloaded-executable-content) | Y |   | Y <br><br> CB 1710 | Y  | Y  |
|[حظر تطبيقات Office من إنشاء محتوى قابل للتنفيذ](#block-office-applications-from-creating-executable-content) | Y |  |Y <br><br> CB 1710 | Y  | Y  |
|[حظر تطبيقات Office من إدخال التعليمات البرمجية في عمليات أخرى](#block-office-applications-from-injecting-code-into-other-processes) | Y |  | Y <br><br> CB 1710 | Y  | Y  |
|[حظر تطبيق اتصالات Office من إنشاء عمليات تابعة](#block-office-communication-application-from-creating-child-processes) | Y |  |Y <br><br> CB 1710 | Y  | Y  |
|[حظر الثبات من خلال اشتراك حدث WMI](#block-persistence-through-wmi-event-subscription) |  |  |  |Y   | Y  |
|[حظر عمليات الإنشاء التي تنشأ من أوامر PSExec وWMI](#block-process-creations-originating-from-psexec-and-wmi-commands) | Y |   |   |  Y | Y  |
|[حظر العمليات غير الموثوق بها وغير الموقعة التي يتم تشغيلها من USB](#block-untrusted-and-unsigned-processes-that-run-from-usb) | Y |   |Y <br><br> CB 1802  | Y  | Y  |
|[حظر مكالمات واجهة برمجة تطبيقات Win32 من وحدات ماكرو Office](#block-win32-api-calls-from-office-macros) | Y |   | Y <br><br> CB 1710  | Y  |  Y |
|[استخدام الحماية المتقدمة من برامج الفدية الضارة](#use-advanced-protection-against-ransomware) | Y |   | Y <br><br> CB 1802 | Y  | Y  |

  (<a id="fn1">1</a>) يمكنك تكوين قواعد تقليل الأجزاء المعرضة للهجوم على أساس كل قاعدة باستخدام GUID الخاص بأي قاعدة.

- [Configuration Manager CB 1710](/configmgr/core/servers/manage/updates)
- [Configuration Manager CB 1802](/configmgr/core/servers/manage/updates)
- [Microsoft إدارة نقاط النهاية CB 1710](/configmgr/core/servers/manage/updates)
- [System Center Configuration Manager (SCCM) CB 1710](/configmgr/core/servers/manage/updates) <br>_SCCM هي الآن نقطة نهاية Microsoft Configuration Manager._

## <a name="per-rule-alert-and-notification-details"></a>حسب تنبيه القاعدة وتفاصيل الإعلام

يتم إنشاء إعلامات منبثقة لكافة القواعد في وضع الحظر. لن تنشئ القواعد في أي وضع آخر إعلامات منبثقة

للقواعد التي تم تحديد "حالة القاعدة":

- يتم استخدام قواعد ASR مع \<ASR Rule, Rule State\> مجموعات لعرض التنبيهات (الإعلامات المنبثقة) على Microsoft Defender لنقطة النهاية فقط للأجهزة على مستوى كتلة السحابة العالية. لن تقوم الأجهزة غير عالية مستوى كتلة السحابة بإنشاء تنبيهات لأي <قاعدة ASR وقاعدة حالة القاعدة> مجموعات
- يتم إنشاء تنبيهات EDR لقواعد ASR في الحالات المحددة، ولكن فقط للأجهزة على مستوى كتلة سحابة عال.

| اسم القاعدة: | حالة القاعدة: | إنشاء تنبيهات في EDR؟ <br> (نعم&nbsp;\|&nbsp;لا) | إنشاء إعلامات منبثقة؟ <br> (نعم&nbsp;\|&nbsp;لا) |
|---|:---:|:---:|:---:|
|   |   |  _فقط للأجهزة على مستوى كتلة السحابة العالية_ | _في وضع الحظر فقط_ |
|[حظر إساءة استخدام برامج التشغيل الموقعة المعرضة للخطر](#block-abuse-of-exploited-vulnerable-signed-drivers) |   | N  | Y |
|[حظر Adobe Reader من إنشاء عمليات تابعة](#block-adobe-reader-from-creating-child-processes) | حظر  | Y <br> يتطلب جهازا على مستوى كتلة سحابة عال  | Y <br> يتطلب جهازا على مستوى كتلة سحابة عال |
|[حظر كافة تطبيقات Office من إنشاء عمليات تابعة](#block-all-office-applications-from-creating-child-processes) |   | N | Y |
|[حظر سرقة بيانات الاعتماد من نظام سلطة الأمان المحلية ل Windows (lsass.exe)](#block-credential-stealing-from-the-windows-local-security-authority-subsystem) |   | N | Y |
|[حظر المحتوى القابل للتنفيذ من عميل البريد الإلكتروني والبريد الإلكتروني](#block-executable-content-from-email-client-and-webmail) |   | Y <br> يتطلب جهازا على مستوى كتلة سحابة عال | Y <br> يتطلب جهازا على مستوى كتلة سحابة عال |
|[حظر تشغيل الملفات القابلة للتنفيذ إلا إذا كانت تفي بمعيار الانتشار أو العمر أو القائمة الموثوق بها](#block-executable-files-from-running-unless-they-meet-a-prevalence-age-or-trusted-list-criterion) |   | N | Y |
|[حظر تنفيذ البرامج النصية التي يحتمل أن تكون مشتتة](#block-execution-of-potentially-obfuscated-scripts) |  كتلة التدقيق&nbsp;\|&nbsp; | Y \| Y <br> يتطلب جهازا على مستوى كتلة سحابة عال  | N \| Y <br> يتطلب جهازا على مستوى كتلة سحابة عال |
|[حظر JavaScript أو VBScript من بدء تشغيل المحتوى القابل للتنفيذ الذي تم تنزيله](#block-javascript-or-vbscript-from-launching-downloaded-executable-content) | حظر | Y <br> يتطلب جهازا على مستوى كتلة سحابة عال  | Y <br> يتطلب جهازا على مستوى كتلة سحابة عال |
|[حظر تطبيقات Office من إنشاء محتوى قابل للتنفيذ](#block-office-applications-from-creating-executable-content) |   | N | Y |
|[حظر تطبيقات Office من إدخال التعليمات البرمجية في عمليات أخرى](#block-office-applications-from-injecting-code-into-other-processes)  |   | N | Y |
|[حظر تطبيق اتصالات Office من إنشاء عمليات تابعة](#block-office-communication-application-from-creating-child-processes) |  |  N | Y |
|[حظر الثبات من خلال اشتراك حدث WMI](#block-persistence-through-wmi-event-subscription) |  كتلة التدقيق&nbsp;\|&nbsp; | Y \| Y <br> يتطلب جهازا على مستوى كتلة سحابة عال  | N \| Y <br> يتطلب جهازا على مستوى كتلة سحابة عال |
|[حظر عمليات الإنشاء التي تنشأ من أوامر PSExec وWMI](#block-process-creations-originating-from-psexec-and-wmi-commands) |   | N | Y |
|[حظر العمليات غير الموثوق بها وغير الموقعة التي يتم تشغيلها من USB](#block-untrusted-and-unsigned-processes-that-run-from-usb) | كتلة التدقيق&nbsp;\|&nbsp; | Y \| Y <br> يتطلب جهازا على مستوى كتلة سحابة عال  | N \| Y <br> يتطلب جهازا على مستوى كتلة سحابة عال |
|[حظر مكالمات واجهة برمجة تطبيقات Win32 من وحدات ماكرو Office](#block-win32-api-calls-from-office-macros) |   | N | Y |
|[استخدام الحماية المتقدمة من برامج الفدية الضارة](#use-advanced-protection-against-ransomware) | كتلة التدقيق&nbsp;\|&nbsp; | Y \| Y <br> يتطلب جهازا على مستوى كتلة سحابة عال  | N \| Y <br> يتطلب جهازا على مستوى كتلة سحابة عال |
  
## <a name="asr-rule-to-guid-matrix"></a>قاعدة ASR إلى مصفوفة GUID

| اسم القاعدة | المعرف الفريد العمومي للقاعدة |
|:-----|:-----|
| حظر إساءة استخدام برامج التشغيل الموقعة المعرضة للخطر | 56a863a9-875e-4185-98a7-b882c64b5ce5 |
| حظر Adobe Reader من إنشاء عمليات تابعة | 7674ba52-37eb-4a4f-a9a1-f0f9a1619a2c |
| حظر كافة تطبيقات Office من إنشاء عمليات تابعة | d4f940ab-401b-4efc-aadc-ad5f3c50688a |
| حظر سرقة بيانات الاعتماد من نظام سلطة الأمان المحلية ل Windows (lsass.exe) | 9e6c4e1f-7d60-472f-ba1a-a39ef669e4b2 |
| حظر المحتوى القابل للتنفيذ من عميل البريد الإلكتروني والبريد الإلكتروني | be9ba2d9-53ea-4cdc-84e5-9b1ee46550 |
| حظر تشغيل الملفات القابلة للتنفيذ إلا إذا كانت تفي بمعيار الانتشار أو العمر أو القائمة الموثوق بها | 01443614-cd74-433a-b99e-2ecdc07bfc25 |
| حظر تنفيذ البرامج النصية التي يحتمل أن تكون مشتتة | 5beb7efe-fd9a-4556-801d-275e5ffc04cc |
| حظر JavaScript أو VBScript من بدء تشغيل المحتوى القابل للتنفيذ الذي تم تنزيله | d3e037e1-3eb8-44c8-a917-57927947596d |
| حظر تطبيقات Office من إنشاء محتوى قابل للتنفيذ | 3b576869-a4ec-4529-8536-b80a7769e899 |
| حظر تطبيقات Office من إدخال التعليمات البرمجية في عمليات أخرى | 75668c1f-73b5-4cf0-bb93-3ecf5cb7cc84 |
| حظر تطبيق اتصالات Office من إنشاء عمليات تابعة | 26190899-1602-49e8-8b27-eb1d0a1ce869 |
| حظر الثبات من خلال اشتراك حدث WMI <br>* استثناءات الملفات والمجلدات غير معتمدة. | e6db77e5-3df2-4cf1-b95a-636979351e5b |
| حظر عمليات الإنشاء التي تنشأ من أوامر PSExec وWMI | d1e49aac-8f56-4280-b9ba-993a6d77406c |
| حظر العمليات غير الموثوق بها وغير الموقعة التي يتم تشغيلها من USB | b2b3f03d-6a65-4f7b-a9c7-1c7ef74a9ba4 |
| حظر مكالمات واجهة برمجة تطبيقات Win32 من وحدات ماكرو Office | 92e97fa1-2edf-4476-bdd6-9dd0b4dddc7b |
| استخدام الحماية المتقدمة من برامج الفدية الضارة | c1db55ab-c21a-4637-bb3f-a12568109d35 |

## <a name="asr-rule-modes"></a>أوضاع قاعدة ASR

- **لم يتم تكوينها** أو **تعطيلها**: الحالة التي لم يتم فيها تمكين قاعدة ASR أو تعطيلها. التعليمات البرمجية لهذه الحالة = 0.
- **الكتلة**: الحالة التي يتم فيها تمكين قاعدة ASR. التعليمات البرمجية لهذه الحالة هي 1.
- **التدقيق**: الحالة التي يتم فيها تقييم قاعدة ASR للتأثير الذي سيكون لها على المؤسسة أو البيئة إذا تم تمكينها (تعيين إلى الحظر أو التحذير). التعليمات البرمجية لهذه الحالة هي 2.
- **تحذير** الحالة التي يتم فيها تمكين قاعدة ASR وتقدم إعلاما للمستخدم النهائي، ولكنها تسمح للمستخدم النهائي بتجاوز الكتلة. التعليمات البرمجية لهذه الحالة هي 6.

_وضع التحذير_ هو نوع وضع الحظر الذي ينبه المستخدمين إلى الإجراءات التي يحتمل أن تكون محفوفة بالمخاطر. يمكن للمستخدمين اختيار تجاوز رسالة تحذير الحظر والسماح بالإجراء الأساسي. يمكن للمستخدمين تحديد **"موافق** " لفرض الحظر، أو تحديد خيار التجاوز - **إلغاء الحظر** - من خلال الإعلام المنبثق المنبثق للمستخدم النهائي الذي يتم إنشاؤه في وقت الكتلة. بعد إلغاء حظر التحذير، يتم السماح بالعملية حتى المرة التالية التي تظهر فيها رسالة التحذير، وفي هذا الوقت سيحتاج المستخدم النهائي إلى إعادة أداء الإجراء.

عند النقر فوق زر السماح، سيتم منع الكتلة لمدة 24 ساعة. بعد 24 ساعة، سيحتاج المستخدم النهائي إلى السماح بالكتلة مرة أخرى. يتم دعم وضع التحذير لقواعد ASR فقط لأجهزة RS5+ (1809+). إذا تم تعيين تجاوز لقواعد ASR على الأجهزة ذات الإصدارات القديمة، فستكون القاعدة في وضع الحظر.

يمكنك أيضا تعيين قاعدة في وضع التحذير عبر PowerShell عن طريق تحديد AttackSurfaceReductionRules_Actions باسم "Warn". على سبيل المثال:

```powershell
-command "& {&'Add-MpPreference' -AttackSurfaceReductionRules_Ids 56a863a9-875e-4185-98a7-b882c64b5ce5 -AttackSurfaceReductionRules_Actions Warn"} 
```

## <a name="per-rule-descriptions"></a>حسب أوصاف القاعدة

### <a name="block-abuse-of-exploited-vulnerable-signed-drivers"></a>حظر إساءة استخدام برامج التشغيل الموقعة المعرضة للخطر

تمنع هذه القاعدة تطبيقا من كتابة برنامج تشغيل موقع عرضة للخطر على القرص. يمكن استغلال برامج التشغيل الموقعة المعرضة للخطر داخل البرية من قبل التطبيقات \- المحلية _التي لديها امتيازات_ \- كافية للوصول إلى النواة. تمكن برامج التشغيل الموقعة المعرضة للخطر المهاجمين من تعطيل حلول الأمان أو الالتفاف عليها، ما يؤدي في النهاية إلى اختراق النظام.

لا تمنع **إساءة استخدام الحظر لقاعدة برامج التشغيل الموقعة المعرضة للخطر** من تحميل برنامج تشغيل موجود بالفعل على النظام.

> [!NOTE]
>
> يمكنك تكوين هذه القاعدة باستخدام MEM OMA-URI. راجع [MEM OMA-URI](enable-attack-surface-reduction.md#mem) لتكوين القواعد المخصصة.
>
> يمكنك أيضا تكوين هذه القاعدة باستخدام [PowerShell](enable-attack-surface-reduction.md#powershell).
>
> لفحص برنامج تشغيل، استخدم موقع ويب هذا [لإرسال برنامج تشغيل للتحليل](https://www.microsoft.com/en-us/wdsi/driversubmission).

<!--The above link is the 'only link' that exists for having drivers examined. The 'en-us' component is required to make the link work. Any alterations to this link will result in a 404.
-->

اسم Intune: `Block abuse of exploited vulnerable signed drivers`

اسم Configuration Manager: غير متوفر بعد
  
GUID:  `56a863a9-875e-4185-98a7-b882c64b5ce5`

نوع إجراء التتبع المتقدم:

- AsrVulnerableSignedDriverAudited
- AsrVulnerableSignedDriverBlocked

<!-- 
Dependencies: none provided by engineering
-->

### <a name="block-adobe-reader-from-creating-child-processes"></a>حظر Adobe Reader من إنشاء عمليات تابعة

تمنع هذه القاعدة الهجمات عن طريق منع Adobe Reader من إنشاء العمليات.

يمكن للبرامج الضارة تنزيل البيانات الأساسية وبدء تشغيلها وفصلها من Adobe Reader من خلال الهندسة الاجتماعية أو الاستغلال. من خلال منع العمليات التابعة من الإنشاء بواسطة Adobe Reader، يتم منع البرامج الضارة التي تحاول استخدام Adobe Reader كمتجه هجوم من الانتشار.

اسم Intune: `Process creation from Adobe Reader (beta)`

اسم Configuration Manager: غير متوفر بعد

GUID: `7674ba52-37eb-4a4f-a9a1-f0f9a1619a2c`

نوع إجراء التتبع المتقدم:

- AsrAdobeReaderChildProcessAudited
- AsrAdobeReaderChildProcessBlocked

التبعيات: MDAV

### <a name="block-all-office-applications-from-creating-child-processes"></a>حظر كافة تطبيقات Office من إنشاء عمليات تابعة

تمنع هذه القاعدة تطبيقات Office من إنشاء عمليات تابعة. تتضمن تطبيقات Office Word وExcel وPowerPoint وOneNote وAccess.

إنشاء عمليات تابعة ضارة هو استراتيجية البرامج الضارة الشائعة. غالبا ما تقوم البرامج الضارة التي تسيء استخدام Office كمتجه بتشغيل وحدات ماكرو VBA واستخدام التعليمات البرمجية لتنزيل المزيد من الحمولات ومحاولة تشغيلها. ومع ذلك، قد تؤدي بعض تطبيقات خط الأعمال المشروعة أيضا إلى إنشاء عمليات تابعة لأغراض غير ضارة؛ مثل إنتاج موجه أوامر أو استخدام PowerShell لتكوين إعدادات التسجيل.

اسم Intune: `Office apps launching child processes`

اسم Configuration Manager:`Block Office application from creating child processes`

GUID: `d4f940ab-401b-4efc-aadc-ad5f3c50688a`

نوع إجراء التتبع المتقدم:

- AsrOfficeChildProcessAudited
- تم حظر AsrOfficeChildProcessBlocked

التبعيات: MDAV

### <a name="block-credential-stealing-from-the-windows-local-security-authority-subsystem"></a>حظر سرقة بيانات الاعتماد من النظام الفرعي لمرجع الأمان المحلي في Windows

تساعد هذه القاعدة على منع سرقة بيانات الاعتماد عن طريق تأمين خدمة النظام الفرعي لمرجع الأمان المحلي (LSASS).

يقوم LSASS بمصادقة المستخدمين الذين يسجلون الدخول على كمبيوتر يعمل بنظام التشغيل Windows. عادة ما تمنع حماية بيانات اعتماد Microsoft Defender في Windows محاولات استخراج بيانات الاعتماد من LSASS. لا يمكن لبعض المؤسسات تمكين "حماية بيانات الاعتماد" على جميع أجهزة الكمبيوتر الخاصة بها بسبب مشاكل التوافق مع برامج تشغيل البطاقة الذكية المخصصة أو البرامج الأخرى التي يتم تحميلها إلى "هيئة الأمان المحلية" (LSA). في هذه الحالات، يمكن للمهاجمين استخدام أدوات مثل Mimikatz لتنقيح كلمات مرور النص الواضح وتجزئة NTLM من LSASS.

> [!NOTE]
> في بعض التطبيقات، تقوم التعليمات البرمجية بتعداد جميع العمليات قيد التشغيل وتحاول فتحها بأذونات شاملة. ترفض هذه القاعدة الإجراء المفتوح لعملية التطبيق وتسجل التفاصيل في سجل أحداث الأمان. يمكن أن تولد هذه القاعدة الكثير من الضوضاء. إذا كان لديك تطبيق يقوم ببساطة بتعداد LSASS، ولكن ليس له تأثير حقيقي في الوظائف، فليست هناك حاجة لإضافته إلى قائمة الاستبعاد. في حد ذاته، لا يشير إدخال سجل الأحداث هذا بالضرورة إلى وجود تهديد ضار.
  
> [!IMPORTANT]
> ستتغير الحالة الافتراضية لقاعدة تقليل الأجزاء المعرضة للهجوم (ASR) "حظر سرقة بيانات الاعتماد من النظام الفرعي لمرجع الأمان المحلي ل Windows (lsass.exe)" من **"غير مكون** " إلى **"تم تكوينه** " وتعيين الوضع الافتراضي إلى **"حظر**". ستبقى كافة قواعد ASR الأخرى في حالتها الافتراضية: **لم يتم تكوينها**. تم بالفعل تضمين منطق تصفية إضافي في القاعدة لتقليل إعلامات المستخدم النهائي. يمكن للعملاء تكوين القاعدة إلى أوضاع **التدقيق** أو **التحذير** أو **التعطيل** ، والتي ستتجاوز الوضع الافتراضي. وظيفة هذه القاعدة هي نفسها، سواء تم تكوين القاعدة في الوضع الافتراضي، أو إذا قمت بتمكين وضع الحظر يدويا.

اسم Intune: `Flag credential stealing from the Windows local security authority subsystem`

اسم Configuration Manager:`Block credential stealing from the Windows local security authority subsystem`

GUID: `9e6c4e1f-7d60-472f-ba1a-a39ef669e4b2`

نوع إجراء التتبع المتقدم:

- AsrLsassCredentialTheftAudited
- AsrLsassCredentialTheftBlocked

التبعيات: MDAV

### <a name="block-executable-content-from-email-client-and-webmail"></a>حظر المحتوى القابل للتنفيذ من عميل البريد الإلكتروني والبريد الإلكتروني

تمنع هذه القاعدة أنواع الملفات التالية من التشغيل من البريد الإلكتروني المفتوح داخل تطبيق Microsoft Outlook، أو Outlook.com وموفري بريد ويب الآخرين الشائعين:

- الملفات القابلة للتنفيذ (مثل .exe أو .dll أو .scr)
- ملفات البرنامج النصي (مثل ملف .ps1 PowerShell أو Visual Basic .vbs أو JavaScript .js)

اسم Intune: `Execution of executable content (exe, dll, ps, js, vbs, etc.) dropped from email (webmail/mail client) (no exceptions)`

اسم microsoft إدارة نقاط النهاية:`Block executable content from email client and webmail`

GUID: `be9ba2d9-53ea-4cdc-84e5-9b1eeee46550`

نوع إجراء التتبع المتقدم:

- AsrExecutableEmailContentAudited
- AsrExecutableEmailContentBlocked

التبعيات: MDAV

> [!NOTE]
> يحتوي **المحتوى القابل للتنفيذ لكتلة القاعدة من عميل البريد الإلكتروني والبريد الإلكتروني** على الأوصاف البديلة التالية، اعتمادا على التطبيق الذي تستخدمه:
>
> - Intune (Configuration Profiles): تم إسقاط تنفيذ المحتوى القابل للتنفيذ (exe, dll, ps, js, vbs, etc.) من البريد الإلكتروني (webmail/mail client) (بدون استثناءات).
> - إدارة نقاط النهاية: حظر تنزيل المحتوى القابل للتنفيذ من عملاء البريد الإلكتروني والبريد الإلكتروني.
> - نهج المجموعة: حظر المحتوى القابل للتنفيذ من عميل البريد الإلكتروني والبريد الإلكتروني.

### <a name="block-executable-files-from-running-unless-they-meet-a-prevalence-age-or-trusted-list-criterion"></a>حظر تشغيل الملفات القابلة للتنفيذ إلا إذا كانت تفي بمعيار الانتشار أو العمر أو القائمة الموثوق بها

تمنع هذه القاعدة الملفات القابلة للتنفيذ، مثل .exe أو .dll أو scr. من التشغيل. ومن ثم، يمكن أن يكون تشغيل الملفات القابلة للتنفيذ غير الموثوق بها أو غير المعروفة محفوفا بالمخاطر، حيث قد لا يكون من الواضح في البداية ما إذا كانت الملفات ضارة.

> [!IMPORTANT]
> يجب [تمكين الحماية المقدمة من السحابة](/windows/security/threat-protection/microsoft-defender-antivirus/enable-cloud-protection-microsoft-defender-antivirus) لاستخدام هذه القاعدة.
>
> **الملفات القابلة للتنفيذ لحظر القاعدة من التشغيل إلا إذا كانت تفي بمعيار الانتشار أو العمر أو القائمة الموثوق بها** مع GUID `01443614-cd74-433a-b99e-2ecdc07bfc25` مملوكة من قبل Microsoft ولا يحددها المسؤولون. تستخدم هذه القاعدة الحماية التي توفرها السحابة لتحديث قائمتها الموثوق بها بانتظام.
>
> يمكنك تحديد ملفات أو مجلدات فردية (باستخدام مسارات المجلدات أو أسماء الموارد المؤهلة بالكامل) ولكن لا يمكنك تحديد القواعد أو الاستثناءات التي تنطبق عليها.

اسم Intune: `Executables that don't meet a prevalence, age, or trusted list criteria`

اسم Configuration Manager:`Block executable files from running unless they meet a prevalence, age, or trusted list criteria`

GUID: `01443614-cd74-433a-b99e-2ecdc07bfc25`

نوع إجراء التتبع المتقدم:

- AsrUntrustedExecutableAudited
- AsrUntrustedExecutableBlocked

التبعيات: MDAV، حماية السحابة

### <a name="block-execution-of-potentially-obfuscated-scripts"></a>حظر تنفيذ البرامج النصية التي يحتمل أن تكون مشتتة

تكتشف هذه القاعدة الخصائص المشبوهة داخل برنامج نصي مشوش.
  
> [!IMPORTANT]
> تم استبعاد البرامج النصية PowerShell مؤقتا من قاعدة "حظر تنفيذ البرامج النصية التي يحتمل أن تكون معقوفة" بسبب مشكلات FP واسعة النطاق التي واجهت في الماضي.

تعويم البرنامج النصي هو تقنية شائعة يستخدمها كل من مؤلفي البرامج الضارة والتطبيقات المشروعة لإخفاء الملكية الفكرية أو تقليل أوقات تحميل البرنامج النصي. كما يستخدم مؤلفو البرامج الضارة التشويش لجعل قراءة التعليمات البرمجية الضارة أكثر صعوبة، ما يعطل الفحص الدقيق من قبل البشر وبرامج الأمان.

> [!IMPORTANT]
> نظرا إلى العدد الكبير من الإيجابيات الخاطئة، لا تكشف هذه القاعدة حاليا عن البرامج النصية PowerShell؛ هذا هو الحل المؤقت. سيتم تحديث القاعدة وبدء إعادة الكشف عن البرامج النصية PowerShell قريبا.

اسم Intune: `Obfuscated js/vbs/ps/macro code`

اسم Configuration Manager:`Block execution of potentially obfuscated scripts`

GUID: `5beb7efe-fd9a-4556-801d-275e5ffc04cc`

نوع إجراء التتبع المتقدم:

- AsrObfuscatedScriptAudited
- AsrObfuscatedScriptBlocked

التبعيات: MDAV وAMSI

### <a name="block-javascript-or-vbscript-from-launching-downloaded-executable-content"></a>حظر JavaScript أو VBScript من بدء تشغيل المحتوى القابل للتنفيذ الذي تم تنزيله

تمنع هذه القاعدة البرامج النصية من بدء تشغيل محتوى تم تنزيله يحتمل أن يكون ضارا. غالبا ما تعمل البرامج الضارة المكتوبة بلغة JavaScript أو VBScript كمنزل لإحضار البرامج الضارة الأخرى وتشغيلها من الإنترنت.

على الرغم من أن تطبيقات خط العمل ليست شائعة، إلا أنها تستخدم أحيانا البرامج النصية لتنزيل المثبتات وتشغيلها.

اسم Intune: `js/vbs executing payload downloaded from Internet (no exceptions)`

اسم Configuration Manager:`Block JavaScript or VBScript from launching downloaded executable content`

GUID: `d3e037e1-3eb8-44c8-a917-57927947596d`

نوع إجراء التتبع المتقدم:

- AsrScriptExecutableDownloadAudited
- AsrScriptExecutableDownloadBlocked

التبعيات: MDAV وAMSI

### <a name="block-office-applications-from-creating-executable-content"></a>حظر تطبيقات Office من إنشاء محتوى قابل للتنفيذ

تمنع هذه القاعدة تطبيقات Office، بما في ذلك Word وExcel وPowerPoint، من إنشاء محتوى قابل للتنفيذ قد يكون ضارا، وذلك عن طريق حظر كتابة تعليمات برمجية ضارة على القرص.

قد تحاول البرامج الضارة التي تسيء استخدام Office كمتجه الخروج من Office وحفظ المكونات الضارة على القرص. هذه المكونات الضارة من شأنها أن تبقى على قيد الحياة إعادة تشغيل الكمبيوتر والاستمرار على النظام. لذلك، فإن هذه القاعدة دفاع ضد تقنية الثبات الشائعة.

اسم Intune: `Office apps/macros creating executable content`

اسم SCCM: `Block Office applications from creating executable content`

GUID: `3b576869-a4ec-4529-8536-b80a7769e899`

نوع إجراء التتبع المتقدم:

- AsrExecutableOfficeContentAudited
- AsrExecutableOfficeContentBlocked

التبعيات: MDAV، RPC

### <a name="block-office-applications-from-injecting-code-into-other-processes"></a>حظر تطبيقات Office من إدخال التعليمات البرمجية في عمليات أخرى

تمنع هذه القاعدة محاولات إدخال التعليمات البرمجية من تطبيقات Office إلى عمليات أخرى.

قد يحاول المهاجمون استخدام تطبيقات Office بترحيل تعليمات برمجية ضارة إلى عمليات أخرى من خلال إدخال التعليمات البرمجية، بحيث يمكن أن يتم تنميط التعليمات البرمجية كمعالجة نظيفة.

لا توجد أغراض تجارية شرعية معروفة لاستخدام حقن التعليمات البرمجية.

تنطبق هذه القاعدة على Word وExcel وPowerPoint.

اسم Intune: `Office apps injecting code into other processes (no exceptions)`

اسم Configuration Manager:`Block Office applications from injecting code into other processes`

GUID: `75668c1f-73b5-4cf0-bb93-3ecf5cb7cc84`

نوع إجراء التتبع المتقدم:

- AsrOfficeProcessInjectionAudited
- تم حظر AsrOfficeProcessInjectionBlocked

التبعيات: MDAV

### <a name="block-office-communication-application-from-creating-child-processes"></a>حظر تطبيق اتصالات Office من إنشاء عمليات تابعة

تمنع هذه القاعدة Outlook من إنشاء عمليات تابعة، مع الاستمرار في السماح بوظائف Outlook المشروعة.

تحمي هذه القاعدة من هجمات الهندسة الاجتماعية وتمنع استغلال التعليمات البرمجية من إساءة استخدام الثغرات الأمنية في Outlook. كما أنه يحمي [من عمليات استغلال قواعد Outlook وأشكاله](https://blogs.technet.microsoft.com/office365security/defending-against-rules-and-forms-injection/) التي يمكن للمهاجمين استخدامها عند اختراق بيانات اعتماد المستخدم.

> [!NOTE]
> تمنع هذه القاعدة تلميحات نهج DLP وتلميحات الأدوات في Outlook. تنطبق هذه القاعدة على Outlook Outlook.com فقط.

اسم Intune: `Process creation from Office communication products (beta)`

اسم Configuration Manager: غير متوفر

GUID: `26190899-1602-49e8-8b27-eb1d0a1ce869`

نوع إجراء التتبع المتقدم:

- AsrOfficeCommAppChildProcessAudited
- AsrOfficeCommAppChildProcessBlocked

التبعيات: MDAV

### <a name="block-persistence-through-wmi-event-subscription"></a>حظر الثبات من خلال اشتراك حدث WMI

تمنع هذه القاعدة البرامج الضارة من إساءة استخدام WMI لتحقيق الثبات على الجهاز.

> [!IMPORTANT]
> لا تنطبق استثناءات الملف والمجلدات على قاعدة تقليل الأجزاء المعرضة للهجوم هذه.

تستخدم التهديدات بلا ملف تكتيكات مختلفة للبقاء مخفيا، لتجنب رؤيتها في نظام الملفات، وللحصة على التحكم في التنفيذ الدوري. يمكن لبعض التهديدات إساءة استخدام مستودع WMI ونموذج الحدث للبقاء مخفيين.

اسم Intune: غير متوفر

اسم Configuration Manager: غير متوفر

GUID: `e6db77e5-3df2-4cf1-b95a-636979351e5b`

نوع إجراء التتبع المتقدم:

- AsrPersistenceThroughWmiAudited
- AsrPersistenceThroughWmiBlocked

التبعيات: MDAV، RPC

### <a name="block-process-creations-originating-from-psexec-and-wmi-commands"></a>حظر عمليات الإنشاء التي تنشأ من أوامر PSExec وWMI

تمنع هذه القاعدة العمليات التي تم إنشاؤها من خلال [PsExec](/sysinternals/downloads/psexec) [وWMI](/windows/win32/wmisdk/about-wmi) من التشغيل. يمكن لكل من PsExec وWMI تنفيذ التعليمات البرمجية عن بعد. هناك خطر من إساءة استخدام البرامج الضارة لوظائف PsExec وWMI لأغراض الأوامر والتحكم، أو لنشر إصابة في جميع أنحاء شبكة المؤسسة.

> [!WARNING]
> استخدم هذه القاعدة فقط إذا كنت تدير أجهزتك باستخدام [Intune](/intune) أو حل MDM آخر. هذه القاعدة غير متوافقة مع الإدارة من خلال [نقطة نهاية Microsoft Configuration Manager](/configmgr) لأن هذه القاعدة تمنع أوامر WMI التي يستخدمها العميل Configuration Manager للعمل بشكل صحيح.

اسم Intune: `Process creation from PSExec and WMI commands`

اسم Configuration Manager: غير قابل للتطبيق

GUID: `d1e49aac-8f56-4280-b9ba-993a6d77406c`

نوع إجراء التتبع المتقدم:

- AsrPsexecWmiChildProcessAudited
- تم حظر AsrPsexecWmiChildProcessBlocked

التبعيات: MDAV

### <a name="block-untrusted-and-unsigned-processes-that-run-from-usb"></a>حظر العمليات غير الموثوق بها وغير الموقعة التي يتم تشغيلها من USB

باستخدام هذه القاعدة، يمكن للمسؤولين منع تشغيل الملفات التنفيذية غير الموقعة أو غير الموثوق بها من محركات أقراص USB القابلة للإزالة، بما في ذلك بطاقات SD. تتضمن أنواع الملفات المحظورة ملفات قابلة للتنفيذ (مثل .exe أو .dll أو .scr)

> [!IMPORTANT]
> سيتم حظر الملفات المنسوخة من USB إلى محرك الأقراص بواسطة هذه القاعدة إذا ومتى سيتم تنفيذها على محرك الأقراص.

اسم Intune: `Untrusted and unsigned processes that run from USB`

اسم Configuration Manager:`Block untrusted and unsigned processes that run from USB`

GUID: `b2b3f03d-6a65-4f7b-a9c7-1c7ef74a9ba4`

نوع إجراء التتبع المتقدم:

- AsrUntrustedUsbProcessAudited
- AsrUntrustedUsbProcessBlocked

التبعيات: MDAV

### <a name="block-win32-api-calls-from-office-macros"></a>حظر مكالمات واجهة برمجة تطبيقات Win32 من وحدات ماكرو Office

تمنع هذه القاعدة وحدات ماكرو VBA من استدعاء واجهات برمجة تطبيقات Win32.

يتيح Office VBA استدعاءات واجهة برمجة تطبيقات Win32. يمكن للبرامج الضارة إساءة استخدام هذه الإمكانية، مثل [استدعاء واجهات برمجة تطبيقات Win32 لتشغيل shellcode ضار](https://www.microsoft.com/security/blog/2018/09/12/office-vba-amsi-parting-the-veil-on-malicious-macros/) دون كتابة أي شيء مباشرة إلى القرص. لا تعتمد معظم المؤسسات على القدرة على استدعاء واجهات برمجة تطبيقات Win32 في عملها اليومي، حتى لو كانت تستخدم وحدات الماكرو بطرق أخرى.

أنظمة التشغيل المدعومة:

- [Windows 10، الإصدار 1709](/windows/whats-new/whats-new-windows-10-version-1709)
- [Windows Server، الإصدار 1809](/windows-server/get-started/whats-new-in-windows-server-1809)
- [Windows Server 2019](/windows-server/get-started-19/whats-new-19)
- [Configuration Manager CB 1710](/configmgr/core/servers/manage/updates)

اسم Intune: `Win32 imports from Office macro code`

اسم Configuration Manager:`Block Win32 API calls from Office macros`

GUID: `92e97fa1-2edf-4476-bdd6-9dd0b4dddc7b`

نوع إجراء التتبع المتقدم:

- AsrOfficeMacroWin32ApiCallsAudited
- AsrOfficeMacroWin32ApiCallsBlocked

التبعيات: MDAV وAMSI

### <a name="use-advanced-protection-against-ransomware"></a>استخدام الحماية المتقدمة من برامج الفدية الضارة

توفر هذه القاعدة طبقة إضافية من الحماية من برامج الفدية الضارة. ويستخدم كلا من استدهايات العميل والسحابة لتحديد ما إذا كان الملف يشبه برامج الفدية الضارة. لا تحظر هذه القاعدة الملفات التي تحتوي على واحدة أو أكثر من الخصائص التالية:

- تم العثور على الملف بالفعل غير مشارك في سحابة Microsoft.
- الملف هو ملف موقع صالح.
- الملف شائع بما يكفي لعدم اعتباره برامج الفدية الضارة.

تميل القاعدة إلى الخطأ من جانب الحذر لمنع برامج الفدية الضارة.

> [!NOTE]
> يجب [تمكين الحماية المقدمة من السحابة](enable-cloud-protection-microsoft-defender-antivirus.md) لاستخدام هذه القاعدة.

اسم Intune: `Advanced ransomware protection`

اسم Configuration Manager:`Use advanced protection against ransomware`

GUID: `c1db55ab-c21a-4637-bb3f-a12568109d35`

نوع إجراء التتبع المتقدم:

- AsrRansomwareAudited
- تم حظر AsrRansomwareBlocked

التبعيات: MDAV، حماية السحابة
