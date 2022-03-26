---
title: عملية "عملية"، من "HIPS" جهة خارجية إلى قواعد ASR
description: يصف كيفية الاقتراب من عملية ترحيل من حل نظام منع اقتحام المضيف (HIPS) من جهة خارجية إلى قواعد ASR.
keywords: قواعد الحد من سطح الهجوم، قواعد asr، asr، الوركين، نظام منع اقتحام المضيف، قواعد الحماية، مكافحة استغلال، مكافحة استغلال، استغلال، منع الإصابة، Microsoft Defender ل Endpoint
ms.topic: article
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
audience: ITPro
author: lovina-saldanha
ms.author: dansimp
manager: dansimp
ms.custom: asr
ms.technology: mde
ms.collection: M365-security-compliance
ms.openlocfilehash: 2530f38bdcfdbb74bdd9a80c59c53c9e273e1449
ms.sourcegitcommit: 282f3a58b8e11615b3e53328e6b89a6ac52008e9
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 12/17/2021
ms.locfileid: "63570215"
---
# <a name="migrating-from-a-third-party-hips-to-asr-rules"></a>عملية "عملية"، من "HIPS" جهة خارجية إلى قواعد ASR

**ينطبق على:**
- [خطة Microsoft Defender لنقطة النهاية 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

تساعدك هذه المقالة على تعيين القواعد الشائعة إلى Microsoft Defender لنقطة النهاية.

## <a name="scenarios-when-migrating-from-a-third-party-hips-product-to-asr-rules"></a>السيناريوهات عند القيام بالاستبدال من منتج HIPS من جهة خارجية إلى قواعد ASR

### <a name="block-creation-of-specific-files"></a>حظر إنشاء ملفات معينة

- **ينطبق على**- جميع العمليات
- **العملية**- إنشاء ملف
- أمثلة على الملفات/المجلدات ومفاتيح **التسجيل/** القيم والعمليات والخدمات- *.zepto و*.odin و*.locky و *.jaff و *.lukitus و *.wnry و *.krab
- **قواعد تقليل مساحة الهجوم** - تمنع قواعد ASR تقنيات الهجوم وليس مؤشرات اختراق (IOC). لا يعد حظر ملحق ملف معين مفيدا دائما، حيث إنه لا يمنع أي جهاز من اختراقه. إلا أنه لا يفشل في الهجوم إلا جزئيا حتى ينشئ المهاجمون نوع ملحق جديد للحمل.
- **الميزات الموصى بها الأخرى**- من المستحسن بشدة تمكين Microsoft Defender AV، إلى جانب تحليل السلوك وحماية السحابة. نوصيك باستخدام منع آخر، مثل قاعدة ASR "استخدام حماية متقدمة من برامج الفدية الضارة". يوفر ذلك مستوى حماية أكبر من هجمات برامج الفدية الضارة. علاوة على ذلك، يتم مراقبة العديد من مفاتيح التسجيل هذه بواسطة Microsoft Defender ل Endpoint، مثل تقنيات ASEP، التي ستقوم بتشغيل تنبيهات معينة. تتطلب مفاتيح التسجيل المستخدمة حدا أدنى من امتيازات المسؤول المحلي أو المثبت الموثوق به يمكن تعديلها. من المستحسن استخدام بيئة مؤمنة، مع الحد الأدنى من الحسابات أو الحقوق الإدارية. يمكن تمكين تكوينات النظام الأخرى، بما في ذلك "تعطيل SeDebug للأدوار غير المطلوبة" التي تكون جزءا من توصيات الأمان الأوسع.

### <a name="block-creation-of-specific-registry-keys"></a>إنشاء كتلة لمفاتيح تسجيل معينة

- **ينطبق على**- كافة العمليات
- **العمليات**- N/A
- **العملية**- تعديلات السجل
- **أمثلة للملفات/المجلدات ومفاتيح/قيم السجل والعمليات والخدمات**-  *\* Software,HKCU\Environment\UserInitMprLogonScript,HKLM\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Accessibility\ATs *\StartExe, HKLM\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Image File Execution Options*\Debugger, HKEY_CURRENT_USER\Software\Microsoft\HtmlHelp Author\location, HKLM\SOFTWARE\Microsoft\Windows NT\CurrentVersion\SilentProcessExit*\MonitorProcess
- **قواعد تقليل مساحة الهجوم** - تمنع قواعد ASR تقنيات الهجوم وليس مؤشرات اختراق (IOC). لا يعد حظر ملحق ملف معين مفيدا دائما، لأنه لا يمنع أي جهاز من اختراقه. إلا أنه لا يفشل في الهجوم إلا جزئيا حتى ينشئ المهاجمون نوع ملحق جديد للحمل.
- **الميزات الموصى بها الأخرى**- من المستحسن بشدة تمكين Microsoft Defender AV، إلى جانب تحليل السلوك وحماية السحابة. نوصيك باستخدام منع إضافي، مثل قاعدة ASR "استخدام حماية متقدمة من برامج الفدية الضارة". يوفر ذلك مستوى حماية أكبر من هجمات برامج الفدية الضارة. علاوة على ذلك، يتم مراقبة العديد من مفاتيح التسجيل هذه بواسطة Microsoft Defender ل Endpoint، مثل تقنيات ASEP، التي ستقوم بتشغيل تنبيهات معينة. بالإضافة إلى ذلك، تتطلب مفاتيح التسجيل المستخدمة حدا أدنى من امتيازات المسؤول المحلي أو المثبت الموثوق به يمكن تعديلها. من المستحسن استخدام بيئة مؤمنة، مع الحد الأدنى من الحسابات أو الحقوق الإدارية. يمكن تمكين تكوينات النظام الأخرى، بما في ذلك "تعطيل SeDebug للأدوار غير المطلوبة" التي تكون جزءا من توصيات الأمان الأوسع.

### <a name="block-untrusted-programs-from-running-from-removable-drives"></a>حظر تشغيل البرامج غير الملوثة من محركات الأقراص القابلة للإزالة

- **ينطبق على** البرامج غير المصدقة من USB
- **العمليات**- *
- **العملية**- تنفيذ العملية
- **أمثلة للملفات/المجلدات ومفاتيح/قيم السجل والعمليات والخدمات:-*
- قواعد تقليل مساحة **الهجوم - قواعد** ASR لديها قاعدة مضمنة لمنع تشغيل البرامج غير المضمنة وغير الموقعة من محركات الأقراص القابلة للإزالة: "حظر العمليات غير المضمنة وغير الموقعة التي يتم تشغيلها من USB"، GUID "b2b3f03d-6a65-4f7b-a9c7-1c7ef74a9ba4".
- **ميزات أخرى مستحسنة**- الرجاء استكشاف عناصر تحكم إضافية للأجهزة USB وغيرها من الوسائط القابلة للإزالة باستخدام Microsoft Defender ل Endpoint:كيفية التحكم في أجهزة USB والتوسطات الأخرى القابلة للإزالة باستخدام [Microsoft Defender ل Endpoint](/windows/security/threat-protection/device-control/control-usb-devices-using-intune).

### <a name="block-mshta-from-launching-certain-child-processes"></a>منع Mshta من بدء تشغيل عمليات معينة للأطفال

- **ينطبق على**- Mshta
- **العمليات**- mshta.exe
- **العملية**- تنفيذ العملية
- **أمثلة للملفات/المجلدات** ومفاتيح/قيم السجل والعمليات والخدمات- powershell.exe cmd.exe regsvr32.exe
- **قواعد تقليل مساحة الهجوم** - لا تحتوي قواعد ASR على أي قاعدة محددة لمنع العمليات الطفلة من "mshta.exe". يوجد عنصر التحكم هذا ضمن نطاق الحماية من استغلال أو Windows التحكم في تطبيق Defender.
- **الميزات الموصى بها الأخرى**- Windows التحكم في تطبيق Defender لمنع تنفيذ mshta.exe تماما. إذا كانت مؤسستك تتطلب "mshta.exe" لتطبيقات خط العمل، ف قم بتكوين قاعدة حماية استغلال خاصة Windows Defender، لمنع mshta.exe تشغيل عمليات الأطفال.

### <a name="block-outlook-from-launching-child-processes"></a>منع Outlook بدء تشغيل عمليات الأطفال

- **ينطبق على**- Outlook
- **العمليات**- outlook.exe
- **العملية**- تنفيذ العملية
- **أمثلة للملفات/المجلدات ومفاتيح/قيم السجل والعمليات والخدمات**- powershell.exe
- قواعد تقليل مساحة **الهجوم - قواعد** ASR لديها قاعدة مضمنة لمنع تطبيقات اتصالات Office (Outlook و Skype و Teams) من بدء عمليات الأطفال: "منع تطبيق اتصالات Office من إنشاء عمليات الطفل"، GUID "26190899-1602-49e8-8b27-eb1d0a1ce869".
- **الميزات المستحسنة الأخرى**- نوصي بتمكين وضع اللغة المقيدة في PowerShell لتقليل سطح الهجوم من PowerShell.

### <a name="block-office-apps-from-launching-child-processes"></a>حظر Office التطبيقات من بدء تشغيل عمليات الأطفال

- **ينطبق على**- Office
- **العمليات**- winword.exe، powerpnt.exe، excel.exe
- **العملية**- تنفيذ العملية
- **أمثلة على الملفات/** المجلدات ومفاتيح التسجيل/القيم والعمليات والخدمات- powershell.exe و cmd.exe wscript.exe mshta.exe EQNEDT32.EXE regsrv32.exe
- **قواعد تقليل** سطح الهجوم - قواعد ASR لديها قاعدة مضمنة لمنع تطبيقات Office من بدء عمليات الأطفال: "حظر جميع تطبيقات Office من إنشاء عمليات الأطفال"، GUID "d4f940ab-401b-4efc-aadc-ad5f3c50688a".
- **الميزات الموصى بها الأخرى**- N/A

### <a name="block-office-apps-from-creating-executable-content"></a>منع Office من إنشاء محتوى قابل للتنفيذ

- **ينطبق على**- Office
- **العمليات**- winword.exe، powerpnt.exe، excel.exe
- **العملية**- إنشاء ملف
- **أمثلة للملفات/المجلدات ومفاتيح التسجيل/القيم والعمليات والخدمات**- C:\Users *\AppData **.exe، C:\ProgramData**.exe، C:\ProgramData**.com، C:\UsersAppData*\Local\**Temp.com، C:\Users*\Downloads**.exe، C:\Users *\AppData.scf **، C:\ProgramData.scf**، C:\Users\public*.exe، C:\Users*\Desktop***.exe
- **قواعد تقليل مساحة الهجوم**- N/A.

### <a name="block-wscript-from-reading-certain-types-of-files"></a>حظر Wscript من قراءة أنواع معينة من الملفات

- **ينطبق على**- Wscript
- **العمليات**- wscript.exe
- **العملية** - قراءة الملف
- **أمثلة للملفات/** المجلدات ومفاتيح التسجيل/القيم والعمليات والخدمات- C:\Users *\AppData**.js، C:\Users*\Downloads**.js
- **قواعد تقليل سطح** الهجوم- نظرا لقضايا الوثوقية والأداء، لا تملك قواعد ASR القدرة على منع عملية معينة من قراءة نوع ملف نصي معين. لدينا قاعدة لمنع متجهات الهجمات التي قد تنشأ من هذه السيناريوهات. اسم القاعدة هو "حظر JavaScript أو VBScript من بدء تشغيل المحتوى القابل للتنفيذ الذي تم تنزيله" (GUID "d3e037e1-3eb8-44c8-a917-57927947596d ") و"حظر التنفيذ من البرامج النصية التي يحتمل أن تكون مبهمة" (GUID " 5beb7efe-fd9a-4556-801d-275e5ffc04cc").
- ميزات **أخرى** مستحسنة- على الرغم من وجود قواعد ASR معينة تخفف من بعض متجهات الهجمات ضمن هذه السيناريوهات، فمن المهم الإشارة إلى أن AV قادر بشكل افتراضي على فحص البرامج النصية (PowerShell و Windows Script Host و JavaScript و VBScript والمزيد) في الوقت الحقيقي، من خلال واجهة مسح البرامج الضارة (AMSI). تتوفر المزيد من المعلومات هنا: [واجهة مسح البرامج الضارة (AMSI).](/windows/win32/amsi/antimalware-scan-interface-portal)

### <a name="block-launch-of-child-processes"></a>حظر تشغيل العمليات الخاصة

- **ينطبق على**- Adobe Acrobat
- **العمليات**- AcroRd32.exe، Acrobat.exe
- **العملية**- تنفيذ العملية
- **أمثلة للملفات/المجلدات** ومفاتيح/قيم السجل والعمليات والخدمات- cmd.exe powershell.exe wscript.exe
- **قواعد تقليل مساحة الهجوم** - تسمح قواعد ASR بحظر Adobe Reader من بدء عمليات الأطفال. اسم القاعدة هو "منع Adobe Reader من إنشاء عمليات الطفل"، GUID "7674ba52-37eb-4a4f-a9a1-f0f9a1619a2c".
- **الميزات الموصى بها الأخرى**- N/A

### <a name="block-download-or-creation-of-executable-content"></a>حظر تنزيل محتوى قابل للتنفيذ أو إنشائه

- **ينطبق على**- CertUtil: حظر التنزيل أو إنشاء قابل للتنفيذ
- **العمليات**- certutil.exe
- **العملية**- إنشاء ملف
- **أمثلة على الملفات/المجلدات ومفاتيح التسجيل/القيم والعمليات والخدمات**- *.exe
- **قواعد تقليل مساحة الهجوم** - لا تدعم قواعد ASR هذه السيناريوهات لأنها جزء من برنامج الحماية من الفيروسات من Microsoft Defender الحماية.
- **الميزات المستحسنة الأخرى**- يمنع Microsoft Defender AV CertUtil من إنشاء محتوى قابل للتنفيذ أو تنزيله.

### <a name="block-processes-from-stopping-critical-system-components"></a>منع العمليات من إيقاف مكونات النظام الهامة

- **ينطبق على**- كافة العمليات
- **العمليات**- *
- **العملية**- إنهاء العملية
- أمثلة للملفات/المجلدات ومفاتيح **التسجيل/** القيم والعمليات والخدمات- MsSense.exe و MsMpEng.exe و NisSrv.exe و svchost.exe*و services.exe و csrss.exe و smss.exe و wininit.exe والمزيد.
- **قواعد تقليل مساحة** الهجوم - لا تدعم قواعد ASR هذه السيناريوهات لأنها محمية Windows حماية أمان مضمنة.
- **الميزات المستحسنة الأخرى**: ELAM (التشغيل المبكر للحماية من البرامج الضارة) و PPL (ضوء عملية الحماية) و PPL AntiMalware Light و System Guard.

### <a name="block-specific-launch-process-attempt"></a>حظر محاولة عملية تشغيل معينة

- **ينطبق على** عمليات محددة
- **العمليات**- "تسمية العملية"
- **العملية**- تنفيذ العملية
- **أمثلة على الملفات/** المجلدات ومفاتيح التسجيل/القيم والعمليات والخدمات- tor.exe bittorrent.exe cmd.exe powershell.exe والمزيد
- **قواعد تقليل مساحة الهجوم**- بشكل عام، لم يتم تصميم قواعد ASR لتعمل كمدير تطبيق.
- **ميزات موصى بها أخرى**- لمنع المستخدمين من بدء تشغيل عمليات أو برامج معينة، من المستحسن استخدام Windows Defender Application Control. يمكن استخدام مؤشري Microsoft Defender لملف نقطة النهاية و Cert في سيناريو استجابة للحوادث (يجب ألا يتم النظر إليه كآلية تحكم في التطبيق).

### <a name="block-unauthorized-changes-to-microsoft-defender-antivirus-configurations"></a>حظر التغييرات غير المصرح بها برنامج الحماية من الفيروسات من Microsoft Defender تكوينات

- **ينطبق على**- كافة العمليات
- **العمليات**- *
- **العملية**- تعديلات السجل
- أمثلة على الملفات/المجلدات ومفاتيح **التسجيل/** القيم والعمليات والخدمات- HKLM\SOFTWARE\Policies\Microsoft\Windows Defender\DisableAntiSpyware وHKLM\SOFTWARE\Policies\Microsoft\Windows Defender\Policy Manager\AllowRealTimeMonitoring، وما إلى ذلك.
- **قواعد تقليل مساحة** الهجوم - لا تغطي قواعد ASR هذه السيناريوهات لأنها جزء من الحماية المضمنة ل Microsoft Defender ل Endpoint.
- ميزات أخرى موصى **بها- تمنع** ميزة الحماية من العبث (الاشتراك، المدارة من Intune) إجراء تغييرات غير مصرح بها على DisableAntiVirus و DisableAntiSpyware و DisableRealtimeMonitoring و DisableOnAccessProtection و DisableBehaviorMonitoring و DisableIOAVProtection (والمزيد).

راجع أيضًا

- [الأسئلة الشائعة حول الحد من سطح الهجوم](attack-surface-reduction-faq.yml)
- [تمكين قواعد الحد من سطح الهجوم](enable-attack-surface-reduction.md)
- [تقييم قواعد الحد من سطح الهجوم](evaluate-attack-surface-reduction.md)
