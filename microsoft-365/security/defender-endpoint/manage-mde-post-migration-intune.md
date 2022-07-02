---
title: إدارة Microsoft Defender لنقطة النهاية باستخدام Intune
description: تعرف على كيفية إدارة Microsoft Defender لنقطة النهاية باستخدام Intune
keywords: ما بعد الترحيل، والإدارة، والعمليات، والصيانة، والاستخدام، وintune، Microsoft Defender لنقطة النهاية، وedr
ms.prod: m365-security
ms.technology: mde
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: deniseb
author: denisebmsft
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
ms.topic: article
ms.date: 07/01/2022
ms.reviewer: chventou
ms.openlocfilehash: 1cbaff007a5ef2839cbcf51babc7a057c7b756c0
ms.sourcegitcommit: bfbe2574f487ced69e711b48ce140120bd99181b
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/02/2022
ms.locfileid: "66607444"
---
# <a name="manage-microsoft-defender-for-endpoint-with-intune"></a>إدارة Microsoft Defender لنقطة النهاية باستخدام Intune

**ينطبق على:**
- [الخطة 1 من Microsoft Defender لنقطة النهاية](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Defender for Endpoint الخطة 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)


> هل تريد تجربة Microsoft Defender لنقطة النهاية؟ [التسجيل للحصول على إصدار تجريبي مجاني.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

نوصي باستخدام [Microsoft إدارة نقاط النهاية](/mem)، والذي يتضمن Microsoft Intune (Intune) لإدارة ميزات الحماية من التهديدات الخاصة بمؤسستك للأجهزة (يشار إليها أيضا بنقاط النهاية). [تعرف على المزيد حول إدارة نقاط النهاية](/mem/endpoint-manager-overview).

تصف هذه المقالة كيفية العثور على إعدادات Microsoft Defender لنقطة النهاية في Intune، وسرد المهام المختلفة التي يمكنك تنفيذها.

## <a name="find-your-microsoft-defender-for-endpoint-settings-in-intune"></a>البحث عن إعدادات Microsoft Defender لنقطة النهاية في Intune

> [!IMPORTANT]
> يجب أن يكون لديك دور المسؤول العام أو مسؤول الخدمة المعين في Intune لتكوين الإعدادات الموضحة في هذه المقالة. لمعرفة المزيد، راجع **[أنواع المسؤولين (Intune).](/mem/intune/fundamentals/users-add#types-of-administrators)**

1. انتقل إلى مدخل Azure ([https://portal.azure.com](https://portal.azure.com)) وسجل الدخول.

2. ضمن **خدمات Azure**، اختر **Intune**.

3. في جزء التنقل على اليسار، اختر **تكوين الجهاز**، ثم ضمن **"إدارة**"، اختر **"ملفات التعريف**".

4. حدد ملف تعريف موجودا، أو قم بإنشاء ملف تعريف جديد.

> [!TIP]
> هل تحتاج إلى مساعدة؟ راجع **[استخدام Microsoft Defender لنقطة النهاية مع Intune](/mem/intune/protect/advanced-threat-protection#example-of-using-microsoft-defender-atp-with-intune)**.

## <a name="configure-microsoft-defender-for-endpoint-with-intune"></a>تكوين Microsoft Defender لنقطة النهاية مع Intune

يسرد الجدول التالي المهام المختلفة التي يمكنك تنفيذها لتكوين Microsoft Defender لنقطة النهاية مع Intune. ليس عليك تكوين كل شيء مرة واحدة؛ اختر مهمة، واقرأ الموارد المقابلة، ثم تابع.

|المهمه|الموارد لمعرفة المزيد|
|---|---|
|**إدارة أجهزة مؤسستك باستخدام Intune** لحماية تلك الأجهزة والبيانات المخزنة عليها|[حماية الأجهزة باستخدام Microsoft Intune](/mem/intune/protect/device-protect)|
|**دمج Microsoft Defender لنقطة النهاية مع Intune** كحل الدفاع عن تهديدات الجوال <br/>*(لأجهزة Android والأجهزة التي تعمل Windows 10 أو Windows 11)*|[فرض الامتثال Microsoft Defender لنقطة النهاية مع الوصول المشروط في Intune](/mem/intune/protect/advanced-threat-protection)|
|**استخدام الوصول المشروط** للتحكم في الأجهزة والتطبيقات التي يمكنها الاتصال ببريدك الإلكتروني وموارد الشركة|[تكوين الوصول المشروط في Microsoft Defender لنقطة النهاية](/microsoft-365/security/defender-endpoint/configure-conditional-access)|
|**تكوين إعدادات برنامج الحماية من الفيروسات ل Microsoft Defender** باستخدام موفر خدمة تكوين النهج ([Policy CSP](/windows/client-management/mdm/policy-configuration-service-provider))|[قيود الجهاز: برنامج الحماية من الفيروسات من Microsoft Defender](/mem/intune/configuration/device-restrictions-windows-10#microsoft-defender-antivirus) <br/><br/> [CSP النهج - Microsoft Defender لنقطة النهاية](/windows/client-management/mdm/policy-csp-defender)|
|**إذا لزم الأمر، حدد الاستثناءات لبرنامج الحماية من الفيروسات من Microsoft Defender** <br/><br/> *بشكل عام، يجب ألا تحتاج إلى تطبيق الاستثناءات. يتضمن برنامج الحماية من الفيروسات من Microsoft Defender عددا من الاستثناءات التلقائية استنادا إلى سلوكيات نظام التشغيل المعروفة وملفات الإدارة النموذجية، مثل تلك المستخدمة في إدارة المؤسسة وإدارة قاعدة البيانات وسيناريوهات المؤسسة الأخرى.*|[توصيات فحص الفيروسات لأجهزة الكمبيوتر الخاصة بالمؤسسات التي تعمل بإصدارات مدعومة حاليا من Windows](https://support.microsoft.com/help/822158/virus-scanning-recommendations-for-enterprise-computers) <br/><br/> [قيود الجهاز: استثناءات برنامج الحماية من الفيروسات من Microsoft Defender للأجهزة Windows 10 وأجهزة Windows 11](/mem/intune/configuration/device-restrictions-windows-10#microsoft-defender-antivirus-exclusions) <br/><br/> [تكوين استثناءات برنامج الحماية من الفيروسات من Microsoft Defender على Windows Server 2016 أو 2019 أو 2022](/windows/security/threat-protection/microsoft-defender-antivirus/configure-server-exclusions-microsoft-defender-antivirus)|
|**تكوين قواعد تقليل الأجزاء المعرضة للهجوم** لاستهداف سلوكيات البرامج التي غالبا ما يتم إساءة استخدامها من قبل المهاجمين <br/><br/> *تكوين قواعد تقليل الأجزاء المعرضة للهجوم في [وضع التدقيق](/microsoft-365/security/defender-endpoint/audit-windows-defender) في البداية (لمدة أسبوع واحد على الأقل وما يصل إلى شهرين). يمكنك مراقبة الحالة باستخدام Power BI ([الحصول على القالب](https://github.com/microsoft/MDATP-PowerBI-Templates/tree/master/Attack%20Surface%20Reduction%20rules))، ثم تعيين هذه القواعد إلى الوضع النشط عندما تكون جاهزا.*|[وضع التدقيق في Microsoft Defender لنقطة النهاية](/microsoft-365/security/defender-endpoint/audit-windows-defender) <br/><br/> [حماية نقطة النهاية: تقليل الأجزاء المعرضة للهجوم](/mem/intune/protect/endpoint-protection-windows-10?toc=/intune/configuration/toc.json&bc=/intune/configuration/breadcrumb/toc.json#attack-surface-reduction) <br/><br/> [تعرف على المزيد حول قواعد تقليل الأجزاء المعرضة للهجوم](/microsoft-365/security/defender-endpoint/attack-surface-reduction) <br/><br/> [نشر مدونة المجتمع التقني: إزالة الغموض عن قواعد تقليل الأجزاء المعرضة للهجوم - الجزء 1](https://techcommunity.microsoft.com/t5/microsoft-defender-atp/demystifying-attack-surface-reduction-rules-part-1/ba-p/1306420)|
|**تكوين تصفية الشبكة** لمنع الاتصالات الصادرة من أي تطبيق إلى عناوين IP أو المجالات ذات السمعة المنخفضة  <br/><br/> *يشار أيضا إلى تصفية الشبكة باسم [حماية الشبكة](/microsoft-365/security/defender-endpoint/network-protection).* <br/><br/> *تأكد من تثبيت أحدث [تحديثات النظام الأساسي لمكافحة البرامج الضارة](https://support.microsoft.com/help/4052623/update-for-microsoft-defender-antimalware-platform) على أجهزة Windows 10 وأجهزة Windows 11.*|[حماية نقطة النهاية: تصفية الشبكة](/mem/intune/protect/endpoint-protection-windows-10#network-filtering) <br/><br/> [مراجعة أحداث حماية الشبكة في Windows عارض الأحداث](/microsoft-365/security/defender-endpoint/evaluate-network-protection#review-network-protection-events-in-windows-event-viewer)|
|**تكوين الوصول المتحكم به إلى المجلد** للحماية من برامج الفدية الضارة <br/><br/> *يشار أيضا إلى [الوصول إلى المجلدات الخاضعة](/microsoft-365/security/defender-endpoint/controlled-folders) للرقابة باسم الحماية من البرامج الضارة.*|[حماية نقطة النهاية: الوصول المتحكم به إلى المجلد](/mem/intune/protect/endpoint-protection-windows-10#controlled-folder-access) <br/><br/> [تمكين الوصول المتحكم به إلى المجلد في Intune](/microsoft-365/security/defender-endpoint/enable-controlled-folders#intune)|
|**تكوين الحماية من الاستغلال** لحماية أجهزة مؤسستك من البرامج الضارة التي تستخدم مهاجمات لنشر الأجهزة الأخرى وإصابتها <br/><br/> *ويشار أيضا إلى [الحماية من الاستغلال](/microsoft-365/security/defender-endpoint/exploit-protection) باسم Exploit Guard.*|[حماية نقطة النهاية: حماية استغلال Microsoft Defender](/mem/intune/protect/endpoint-protection-windows-10#microsoft-defender-exploit-guard) <br/><br/> [تمكين الحماية من الاستغلال في Intune](/microsoft-365/security/defender-endpoint/enable-exploit-protection#intune)|
|**تكوين Microsoft Defender SmartScreen** للحماية من المواقع والملفات الضارة على الإنترنت. <br/><br/> *يجب تثبيت Microsoft Edge على أجهزة مؤسستك. للحماية على مستعرضات Google Chrome وFireFox، قم بتكوين الحماية من الاستغلال.*|[Microsoft Defender SmartScreen](/windows/security/threat-protection/microsoft-defender-smartscreen/microsoft-defender-smartscreen-overview) <br/><br/> [قيود الجهاز: Microsoft Defender SmartScreen](/mem/intune/configuration/device-restrictions-windows-10#microsoft-defender-smartscreen) <br/><br/> [إعدادات النهج لإدارة SmartScreen في Intune](/windows/security/threat-protection/microsoft-defender-smartscreen/microsoft-defender-smartscreen-available-settings#mdm-settings)|
|**تكوين جدار الحماية من Microsoft Defender** لحظر نسبة استخدام الشبكة غير المصرح بها التي تتدفق إلى أجهزة مؤسستك أو خارجها|[حماية نقطة النهاية: جدار الحماية من Microsoft Defender](/mem/intune/protect/endpoint-protection-windows-10#microsoft-defender-firewall) <br/><br/> [جدار الحماية من Microsoft Defender مع الأمان المتقدم](/windows/security/threat-protection/windows-firewall/windows-firewall-with-advanced-security)|
|**تكوين التشفير وBitLocker** لحماية المعلومات على أجهزة مؤسستك التي تعمل بنظام التشغيل Windows|[حماية نقطة النهاية: تشفير Windows](/mem/intune/protect/endpoint-protection-windows-10#windows-encryption) <br/><br/> [BitLocker للأجهزة Windows 10 وأجهزة Windows 11](/windows/security/information-protection/bitlocker/bitlocker-overview)|
|**تكوين حماية بيانات اعتماد Microsoft Defender** للحماية من هجمات سرقة بيانات الاعتماد|للحصول على Windows 10، Windows 11، وWindows Server 2016، وWindows Server 2019، وWindows Server 2022، راجع [حماية نقطة النهاية: حماية بيانات اعتماد Microsoft Defender](/mem/intune/protect/endpoint-protection-windows-10#microsoft-defender-credential-guard) <br/><br/> بالنسبة إلى Windows 7 SP1 وWindows Server 2008 R2 SP1 Windows 8.1 وWindows Server 2012 R2، راجع [التخفيف من هجمات Pass-the-Hash (PtH) وسرقة بيانات الاعتماد الأخرى والإصدارين 1 و2](https://www.microsoft.com/download/details.aspx?id=36036)|
|**تكوين التحكم في تطبيق Microsoft Defender** لاختيار ما إذا كنت تريد تدقيق التطبيقات أو الوثوق بها على أجهزة مؤسستك <br/><br/> *يشار أيضا إلى Microsoft Defender Application Control باسم [AppLocker](/windows/security/threat-protection/windows-defender-application-control/applocker/applocker-overview).*|[نشر نهج التحكم في تطبيق Microsoft Defender باستخدام Microsoft Intune](/windows/security/threat-protection/windows-defender-application-control/deploy-windows-defender-application-control-policies-using-intune) <br/><br/> [حماية نقطة النهاية: التحكم في تطبيق Microsoft Defender](/mem/intune/protect/endpoint-protection-windows-10#microsoft-defender-application-control) <br/><br/> [AppLocker CSP](/windows/client-management/mdm/applocker-csp)|
|**تكوين التحكم في الجهاز والوصول إلى الأجهزة الطرفية USB** للمساعدة في منع التهديدات في الأجهزة الطرفية غير المصرح بها من المساس بالأجهزة الطرفية|[التحكم في أجهزة USB والوسائط الأخرى القابلة للإزالة باستخدام Microsoft Defender لنقطة النهاية وIntune](/windows/security/threat-protection/device-control/control-usb-devices-using-intune)|

## <a name="configure-your-microsoft-365-defender-portal"></a>تكوين مدخل Microsoft 365 Defender

إذا لم تكن قد فعلت ذلك بالفعل، فقم بتكوين مدخل Microsoft 365 Defender لعرض التنبيهات، وتكوين ميزات الحماية من التهديدات، وعرض معلومات مفصلة حول الوضع الأمني العام لمؤسستك. راجع [Microsoft 365 Defender](/microsoft-365/security/defender/microsoft-365-defender). يمكنك أيضا تكوين ما إذا كان يمكن للمستخدمين النهائيين رؤيتها وما هي الميزات في مدخل Microsoft 365 Defender.

- [نظرة عامة على Microsoft 365 Defender](/microsoft-365/security/defender-endpoint/use)
- [حماية نقطة النهاية: Microsoft 365 Defender](/mem/intune/protect/endpoint-protection-windows-10#microsoft-defender-security-center)

## <a name="next-steps"></a>الخطوات التالية

- [الحصول على نظرة عامة على إدارة المخاطر والثغرات الأمنية](/microsoft-365/security/defender-endpoint/next-gen-threat-and-vuln-mgt)
- [تفضل بزيارة لوحة معلومات عمليات أمان مدخل Microsoft 365 Defender](/microsoft-365/security/defender-endpoint/security-operations-dashboard)
