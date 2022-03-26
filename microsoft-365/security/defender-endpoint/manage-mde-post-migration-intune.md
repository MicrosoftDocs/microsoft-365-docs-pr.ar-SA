---
title: إدارة Microsoft Defender لنقطة النهاية باستخدام Intune
description: تعرف على كيفية إدارة Microsoft Defender لنقطة النهاية باستخدام Intune
keywords: بعد الترحيل، والإدارة، والعمليات، والصيانة، والاستخدام، و intune، و Microsoft Defender ل Endpoint، وedr
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
- m365solution-scenario
ms.topic: article
ms.date: 11/29/2021
ms.reviewer: chventou
ms.openlocfilehash: 290d98f3f4136cfd07b5ea5abc21988ac8d9867a
ms.sourcegitcommit: 4c207a9bdbb6c8ba372ae37907ccefca031a49f8
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 02/09/2022
ms.locfileid: "63572086"
---
# <a name="manage-microsoft-defender-for-endpoint-with-intune"></a>إدارة Microsoft Defender لنقطة النهاية باستخدام Intune

**ينطبق على:**
- [خطة Microsoft Defender لنقطة النهاية 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)


> هل تريد تجربة Microsoft Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

نوصي باستخدام [إدارة نقاط النهاية من Microsoft](/mem)، التي تتضمن Microsoft Intune (Intune) لإدارة ميزات الحماية من المخاطر للأجهزة في مؤسستك (يشار إليها أيضا بنقاط النهاية). [تعرف على المزيد حول إدارة نقاط النهاية](/mem/endpoint-manager-overview).

تصف هذه المقالة كيفية العثور على إعدادات Microsoft Defender لنقطة النهاية في Intune، كما تسرد المهام المختلفة التي يمكنك تنفيذها.

## <a name="find-your-microsoft-defender-for-endpoint-settings-in-intune"></a>البحث عن إعدادات Microsoft Defender لنقطة النهاية في Intune

> [!IMPORTANT]
> يجب تعيين دور مسؤول الخدمة أو المسؤول العام في Intune لتكوين الإعدادات الموضحة في هذه المقالة. لمعرفة المزيد، راجع **[أنواع المسؤولين (Intune)](/mem/intune/fundamentals/users-add#types-of-administrators)**.

1. انتقل إلى مدخل Azure ([https://portal.azure.com](https://portal.azure.com)) ثم سجل الدخول.

2. ضمن **Azure Services**، اختر **Intune**.

3. في جزء التنقل على اليمين، اختر **تكوين الجهاز**، ثم ضمن **إدارة**، اختر **ملفات التعريف**.

4. حدد ملف تعريف موجود، أو قم بإنشاء ملف تعريف جديد.

> [!TIP]
> هل تحتاج إلى مساعدة؟ راجع **[استخدام Microsoft Defender لنقطة النهاية مع Intune](/mem/intune/protect/advanced-threat-protection#example-of-using-microsoft-defender-atp-with-intune)**.

## <a name="configure-microsoft-defender-for-endpoint-with-intune"></a>تكوين Microsoft Defender لنقطة النهاية باستخدام Intune

يسرد الجدول التالي المهام المختلفة التي يمكنك تنفيذها لتكوين Microsoft Defender ل Endpoint باستخدام Intune. لست بحاجة إلى تكوين كل شيء مرة واحدة؛ اختر مهمة، واقرأ الموارد المقابلة، ثم تابع.

<br/><br/>

|مهمة|الموارد لمعرفة المزيد|
|---|---|
|**إدارة أجهزة مؤسستك باستخدام Intune** لحماية تلك الأجهزة والبيانات المخزنة عليها|[حماية الأجهزة باستخدام Microsoft Intune](/mem/intune/protect/device-protect)|
|**دمج Microsoft Defender لنقطة النهاية مع Intune** كحل "الدفاع ضد تهديدات الأجهزة المحمولة" <br/>*(لأجهزة Android والأجهزة التي تعمل بنظام التشغيل Windows 10 أو Windows 11)*|[فرض التوافق ل Microsoft Defender لنقطة النهاية باستخدام الوصول الشرطي في Intune](/mem/intune/protect/advanced-threat-protection)|
|**استخدام الوصول الشرطي** للتحكم في الأجهزة والتطبيقات التي يمكنها الاتصال بالبريد الإلكتروني وموارد الشركة|[تكوين الوصول الشرطي في Microsoft Defender لنقطة النهاية](/microsoft-365/security/defender-endpoint/configure-conditional-access)|
|**تكوين إعدادات برنامج الحماية من الفيروسات من Microsoft Defender** باستخدام موفر خدمة تكوين النهج ([النهج CSP](/windows/client-management/mdm/policy-configuration-service-provider))|[قيود الجهاز: برنامج الحماية من الفيروسات من Microsoft Defender](/mem/intune/configuration/device-restrictions-windows-10#microsoft-defender-antivirus) <br/><br/> [نهج CSP - Microsoft Defender لنقطة النهاية](/windows/client-management/mdm/policy-csp-defender)|
|**إذا لزم الأمر، حدد الاستثناءات برنامج الحماية من الفيروسات من Microsoft Defender** <br/><br/> *بشكل عام، يجب ألا تحتاج إلى تطبيق الاستثناءات. برنامج الحماية من الفيروسات من Microsoft Defender على عدد من الاستثناءات التلقائية استنادا إلى سلوكيات نظام التشغيل المعروفة وملفات الإدارة النموذجية، مثل تلك المستخدمة في إدارة المؤسسة وإدارة قاعدة البيانات وسيناريوهات المؤسسة الأخرى.*|[توصيات فحص الفيروسات لأجهزة الكمبيوتر الخاصة بالمؤسسات التي تعمل بالإصدارات المدعمة حاليا من Windows](https://support.microsoft.com/help/822158/virus-scanning-recommendations-for-enterprise-computers) <br/><br/> [قيود الجهاز: برنامج الحماية من الفيروسات من Microsoft Defender استثناءات الأجهزة Windows 10 Windows 11 الأجهزة](/mem/intune/configuration/device-restrictions-windows-10#microsoft-defender-antivirus-exclusions) <br/><br/> [تكوين برنامج الحماية من الفيروسات من Microsoft Defender الاستثناءات على Windows Server 2016 أو 2019 أو 2022](/windows/security/threat-protection/microsoft-defender-antivirus/configure-server-exclusions-microsoft-defender-antivirus)|
|**تكوين قواعد الحد من سطح** الهجوم لاستهداف سلوكيات البرامج التي غالبا ما يتم إساءة استخدامها من قبل المهاجمين <br/><br/> *قم بتكوين قواعد تقليل مساحة الهجوم في وضع [التدقيق](/microsoft-365/security/defender-endpoint/audit-windows-defender) أولا (لمدة أسبوع واحد على الأقل وما يصل إلى شهرين). يمكنك مراقبة الحالة باستخدام Power BI ([الحصول على](https://github.com/microsoft/MDATP-PowerBI-Templates/tree/master/Attack%20Surface%20Reduction%20rules) القالب)، ثم تعيين هذه القواعد إلى الوضع النشط عندما تكون جاهزا.*|[وضع التدقيق في Microsoft Defender لنقطة النهاية](/microsoft-365/security/defender-endpoint/audit-windows-defender) <br/><br/> [حماية نقطة النهاية: تقليل مساحة الهجوم](/mem/intune/protect/endpoint-protection-windows-10?toc=/intune/configuration/toc.json&bc=/intune/configuration/breadcrumb/toc.json#attack-surface-reduction) <br/><br/> [تعرف على المزيد حول قواعد الحد من سطح الهجوم](/microsoft-365/security/defender-endpoint/attack-surface-reduction) <br/><br/> [منشور مدونة المجتمع التقني: إزالة الغموض عن قواعد الحد من سطح الهجوم - الجزء 1](https://techcommunity.microsoft.com/t5/microsoft-defender-atp/demystifying-attack-surface-reduction-rules-part-1/ba-p/1306420)|
|**تكوين تصفية الشبكة لحظر** الاتصالات الصادرة من أي تطبيق إلى عناوين IP أو المجالات ذات السمعة المنخفضة  <br/><br/> *يشار أيضا إلى تصفية الشبكة بحماية [الشبكة](/microsoft-365/security/defender-endpoint/network-protection).* <br/><br/> *تأكد من تثبيت Windows 10 البرامج الضارة Windows 11 الأجهزة بأحدث تحديثات النظام الأساسي [لمكافحة البرامج الضارة](https://support.microsoft.com/help/4052623/update-for-microsoft-defender-antimalware-platform).*|[حماية نقطة النهاية: تصفية الشبكة](/mem/intune/protect/endpoint-protection-windows-10#network-filtering) <br/><br/> [مراجعة أحداث حماية الشبكة في Windows الحدث](/microsoft-365/security/defender-endpoint/evaluate-network-protection#review-network-protection-events-in-windows-event-viewer)|
|**تكوين الوصول إلى المجلدات الخاضعة للتحكم** للحماية من برامج الفدية الضارة <br/><br/> *[يشار أيضا إلى الوصول](/microsoft-365/security/defender-endpoint/controlled-folders) إلى المجلدات الخاضعة للتحكم بالحماية من البرامج الضارة.*|[حماية نقطة النهاية: الوصول إلى المجلدات الخاضعة للتحكم](/mem/intune/protect/endpoint-protection-windows-10#controlled-folder-access) <br/><br/> [تمكين الوصول إلى المجلدات الخاضعة للتحكم في Intune](/microsoft-365/security/defender-endpoint/enable-controlled-folders#intune)|
|**تكوين حماية استغلال** لحماية أجهزة مؤسستك من البرامج الضارة التي تستخدم استغلالات لنشر أجهزة أخرى وإصابتها <br/><br/> *[يشار أيضا](/microsoft-365/security/defender-endpoint/exploit-protection) إلى الحماية من استغلال ب "الحماية من استغلال".*|[حماية نقطة النهاية: الحماية من مخاطر الهجمات من Microsoft Defender](/mem/intune/protect/endpoint-protection-windows-10#microsoft-defender-exploit-guard) <br/><br/> [تمكين الحماية من استغلال في Intune](/microsoft-365/security/defender-endpoint/enable-exploit-protection#intune)|
|**قم بتكوين Microsoft Defender SmartScreen** الحماية من المواقع والملفات الضارة على الإنترنت. <br/><br/> *Microsoft Edge أن تكون مثبتة على أجهزة مؤسستك. للحماية على مستعرضات Google Chrome وFireFox، قم بتكوين الحماية من استغلال.*|[Microsoft Defender SmartScreen](/windows/security/threat-protection/microsoft-defender-smartscreen/microsoft-defender-smartscreen-overview) <br/><br/> [قيود الجهاز: Microsoft Defender SmartScreen](/mem/intune/configuration/device-restrictions-windows-10#microsoft-defender-smartscreen) <br/><br/> [إعدادات النهج لإدارة SmartScreen في Intune](/windows/security/threat-protection/microsoft-defender-smartscreen/microsoft-defender-smartscreen-available-settings#mdm-settings)|
|**تكوين جدار حماية Microsoft Defender** لحظر تدفق حركة مرور الشبكة غير المصرح بها إلى أجهزة مؤسستك أو خارجها|[حماية نقطة النهاية: جدار الحماية ل Microsoft Defender](/mem/intune/protect/endpoint-protection-windows-10#microsoft-defender-firewall) <br/><br/> [جدار الحماية ل Microsoft Defender مع الأمان المتقدم](/windows/security/threat-protection/windows-firewall/windows-firewall-with-advanced-security)|
|**قم بتكوين التشفير و BitLocker** لحماية المعلومات على أجهزة المؤسسة التي تعمل Windows|[حماية نقطة النهاية: Windows التشفير](/mem/intune/protect/endpoint-protection-windows-10#windows-encryption) <br/><br/> [BitLocker للأجهزة Windows 10 وأجهزة Windows 11](/windows/security/information-protection/bitlocker/bitlocker-overview)|
|**تكوين "حماية بيانات اعتماد Microsoft Defender"** للحماية من هجمات سرقة بيانات الاعتماد|بالنسبة Windows 10 و Windows 11 و Windows Server 2016 و Windows Server 2019 و Windows Server 2022، راجع حماية نقطة النهاية[: Microsoft Defender Credential Guard](/mem/intune/protect/endpoint-protection-windows-10#microsoft-defender-credential-guard) <br/><br/> بالنسبة إلى Windows 7 SP1 و Windows Server 2008 R2 SP1 و Windows 8.1 و Windows Server 2012 R2، راجع تخفيف هجمات [Pass-the-hash (PtH)](https://www.microsoft.com/download/details.aspx?id=36036) وسرقة بيانات الاعتماد الأخرى، الإصدارين 1 و2|
|**تكوين عنصر تحكم تطبيق Microsoft Defender** لاختيار ما إذا كنت تريد تدقيق التطبيقات أو الوثوق بها على أجهزة مؤسستك <br/><br/> *يشار أيضا إلى Microsoft Defender Application Control باسم [AppLocker](/windows/security/threat-protection/windows-defender-application-control/applocker/applocker-overview).*|[نشر سياسات Microsoft Defender Application Control باستخدام Microsoft Intune](/windows/security/threat-protection/windows-defender-application-control/deploy-windows-defender-application-control-policies-using-intune) <br/><br/> [حماية نقطة النهاية: عنصر تحكم تطبيق Microsoft Defender](/mem/intune/protect/endpoint-protection-windows-10#microsoft-defender-application-control) <br/><br/> [AppLocker CSP](/windows/client-management/mdm/applocker-csp)|
|**تكوين التحكم في الجهاز والوصول إلى الأجهزة الطرفية USB** للمساعدة في منع التهديدات في الأجهزة الطرفية غير المصرح بها من التأثير على أجهزتك|[التحكم في أجهزة USB وغيرها من الوسائط القابلة للإزالة باستخدام Microsoft Defender لنقطة النهاية و Intune](/windows/security/threat-protection/device-control/control-usb-devices-using-intune)|

## <a name="configure-your-microsoft-365-defender-portal"></a>تكوين مدخل Microsoft 365 Defender

إذا لم تكن قد فعلت ذلك بعد، ف قم بتكوين مدخل Microsoft 365 Defender لعرض التنبيهات وتكوين ميزات الحماية من المخاطر وعرض معلومات مفصلة حول الوضع الأمني العام لم مؤسستك. راجع [Microsoft 365 Defender](/microsoft-365/security/defender/microsoft-365-defender). يمكنك أيضا تكوين الميزات التي يمكن للمستخدمين رؤياها في مدخل Microsoft 365 Defender وما هي الميزات.

- [نظرة عامة على Microsoft 365 Defender](/microsoft-365/security/defender-endpoint/use)
- [حماية نقطة النهاية: Microsoft 365 Defender](/mem/intune/protect/endpoint-protection-windows-10#microsoft-defender-security-center)

## <a name="next-steps"></a>الخطوات التالية

- [احصل على نظرة عامة حول إدارة المخاطر والثغرات الأمنية](/microsoft-365/security/defender-endpoint/next-gen-threat-and-vuln-mgt)
- [زيارة لوحة Microsoft 365 Defender عمليات أمان المدخل](/microsoft-365/security/defender-endpoint/security-operations-dashboard)
