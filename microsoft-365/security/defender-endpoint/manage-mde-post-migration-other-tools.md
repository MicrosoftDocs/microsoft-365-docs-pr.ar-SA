---
title: إدارة Microsoft Defender لنقطة النهاية باستخدام PowerShell وWMI MPCmdRun.exe
description: تعرف على كيفية إدارة Microsoft Defender لنقطة النهاية باستخدام PowerShell وWMI MPCmdRun.exe
keywords: بعد الترحيل، والإدارة، والعمليات، والصيانة، والاستخدام، وPowerShell، وWMI، MPCmdRun.exe، Microsoft Defender لنقطة النهاية، edr
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
ms.custom: admindeeplinkDEFENDER
ms.topic: article
ms.reviewer: chventou
ms.openlocfilehash: 51ead270b8e8223b2fd67cfd5fb1cf4e9f8a05d4
ms.sourcegitcommit: e9692a40dfe1f8c2047699ae3301c114a01b0d3a
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/01/2022
ms.locfileid: "66603286"
---
# <a name="manage-microsoft-defender-for-endpoint-with-powershell-wmi-and-mpcmdrunexe"></a>إدارة Microsoft Defender لنقطة النهاية باستخدام PowerShell وWMI MPCmdRun.exe

**ينطبق على:**
- [الخطة 1 من Microsoft Defender لنقطة النهاية](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Defender for Endpoint الخطة 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> هل تريد تجربة Microsoft Defender لنقطة النهاية؟ [التسجيل للحصول على إصدار تجريبي مجاني.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

> [!NOTE]
> نوصي باستخدام [Microsoft إدارة نقاط النهاية](/mem) لإدارة ميزات الحماية من التهديدات في مؤسستك للأجهزة (يشار إليها أيضا بنقاط النهاية). تتضمن إدارة نقاط النهاية [Microsoft Intune](/mem/intune/fundamentals/what-is-intune) [ونقطة نهاية Microsoft Configuration Manager](/mem/configmgr/core/understand/introduction).
>
> - [تعرف على المزيد حول إدارة نقاط النهاية](/mem/endpoint-manager-overview)
> - [المشاركة في إدارة Microsoft Defender لنقطة النهاية على أجهزة Windows 10 وأجهزة Windows 11 باستخدام Configuration Manager وIntune](manage-mde-post-migration-intune.md)
> - [إدارة Microsoft Defender لنقطة النهاية باستخدام Intune](manage-mde-post-migration-intune.md)

يمكنك إدارة بعض إعدادات برنامج الحماية من الفيروسات من Microsoft Defender على الأجهزة باستخدام [PowerShell](#configure-microsoft-defender-for-endpoint-with-powershell)  [وWindows Management Instrumentation](#configure-microsoft-defender-for-endpoint-with-windows-management-instrumentation-wmi) (WMI) [والأداة المساعدة لسطر الأوامر للحماية من البرامج الضارة من Microsoft](#configure-microsoft-defender-for-endpoint-with-microsoft-malware-protection-command-line-utility-mpcmdrunexe) (MPCmdRun.exe). على سبيل المثال، يمكنك إدارة بعض إعدادات برنامج الحماية من الفيروسات من Microsoft Defender. وفي بعض الحالات، يمكنك تخصيص قواعد تقليل الأجزاء المعرضة للهجوم وإعدادات الحماية من الاستغلال.

> [!IMPORTANT]
> يمكن الكتابة فوق ميزات الحماية من التهديدات التي تقوم بتكوينها باستخدام PowerShell أو WMI أو MCPmdRun.exe بواسطة إعدادات التكوين التي يتم نشرها مع Intune أو Configuration Manager.

## <a name="configure-microsoft-defender-for-endpoint-with-powershell"></a>تكوين Microsoft Defender لنقطة النهاية باستخدام PowerShell

يمكنك استخدام PowerShell لإدارة برنامج الحماية من الفيروسات من Microsoft Defender وحماية الاستغلال وقواعد تقليل الأجزاء المعرضة للهجوم.

|المهمه|الموارد لمعرفة المزيد|
|---|---|
|**إدارة برنامج الحماية من الفيروسات من Microsoft Defender** <br/><br/> عرض حالة الحماية من البرامج الضارة، وتكوين تفضيلات عمليات فحص مكافحة الفيروسات & التحديثات، وإجراء تغييرات أخرى على الحماية من الفيروسات.*|[استخدام PowerShell cmdlets لتكوين برنامج الحماية من الفيروسات ل Microsoft Defender وإدارته](/windows/security/threat-protection/microsoft-defender-antivirus/use-powershell-cmdlets-microsoft-defender-antivirus) <br/><br/> [استخدام PowerShell cmdlets لتمكين الحماية المقدمة من السحابة](/windows/security/threat-protection/microsoft-defender-antivirus/enable-cloud-protection-microsoft-defender-antivirus#use-powershell-cmdlets-to-enable-cloud-delivered-protection)|
|**تكوين الحماية من الاستغلال** للتخفيف من التهديدات على أجهزة مؤسستك <br/><br/> *نوصي باستخدام الحماية من الاستغلال في [وضع التدقيق](/microsoft-365/security/defender-endpoint/evaluate-exploit-protection#powershell) في البداية. وبهذه الطريقة، يمكنك أن ترى كيف تؤثر الحماية من الاستغلال على التطبيقات التي تستخدمها مؤسستك.*|[تخصيص الحماية من استغلال](/microsoft-365/security/defender-endpoint/customize-exploit-protection) <br/><br/> [PowerShell cmdlets للحماية من الاستغلال](/microsoft-365/security/defender-endpoint/customize-exploit-protection#powershell-reference)|
|**تكوين قواعد تقليل الأجزاء المعرضة للهجوم** باستخدام PowerShell <br/><br/> *يمكنك استخدام PowerShell لاستبعاد الملفات والمجلدات من قواعد تقليل الأجزاء المعرضة للهجوم.*|[تخصيص قواعد تقليل الأجزاء المعرضة للهجوم: استخدم PowerShell لاستبعاد الملفات & المجلدات](/microsoft-365/security/defender-endpoint/enable-attack-surface-reduction) <br/><br/> راجع أيضا [أداة واجهة المستخدم الرسومية ل António Vasconcelo لإعداد قواعد تقليل الأجزاء المعرضة للهجوم باستخدام PowerShell](https://github.com/anvascon/MDATP_PoSh_Scripts/tree/master/ASR%20GUI).|
|**تمكين حماية الشبكة** باستخدام PowerShell <br/><br/> *يمكنك استخدام PowerShell لتمكين Network Protection.*|[تشغيل Network Protection باستخدام PowerShell](/microsoft-365/security/defender-endpoint/enable-network-protection#powershell)|
|**تكوين الوصول المتحكم به إلى المجلد** للحماية من برامج الفدية الضارة <br/><br/> *يشار أيضا إلى [الوصول إلى المجلدات الخاضعة](/microsoft-365/security/defender-endpoint/controlled-folders) للرقابة باسم الحماية من البرامج الضارة.*|[تمكين الوصول إلى المجلدات التي يتم التحكم فيها باستخدام PowerShell](/microsoft-365/security/defender-endpoint/enable-controlled-folders#powershell)|
|**تكوين جدار الحماية من Microsoft Defender** لحظر نسبة استخدام الشبكة غير المصرح بها التي تتدفق إلى أجهزة مؤسستك أو خارجها|[جدار الحماية من Microsoft Defender مع إدارة الأمان المتقدمة باستخدام Windows PowerShell](/windows/security/threat-protection/windows-firewall/windows-firewall-with-advanced-security-administration-with-windows-powershell)|
|**تكوين التشفير وBitLocker** لحماية المعلومات على أجهزة مؤسستك التي تعمل بنظام التشغيل Windows|[دليل مرجع BitLocker PowerShell](/powershell/module/bitlocker/)|

## <a name="configure-microsoft-defender-for-endpoint-with-windows-management-instrumentation-wmi"></a>تكوين Microsoft Defender لنقطة النهاية باستخدام Windows Management Instrumentation (WMI)

WMI هي واجهة برمجة نصية تسمح لك باسترداد الإعدادات وتعديلها وتحديثها. لمعرفة المزيد، راجع [استخدام WMI](/windows/win32/wmisdk/using-wmi).<br/><br/>

|المهمه|الموارد لمعرفة المزيد|
|---|---|
|**تمكين الحماية التي توفرها السحابة** على جهاز|[استخدام تعليمات إدارة Windows (WMI) لتمكين الحماية المقدمة من السحابة](/windows/security/threat-protection/microsoft-defender-antivirus/enable-cloud-protection-microsoft-defender-antivirus#use-windows-management-instruction-wmi-to-enable-cloud-delivered-protection)|
|استرداد إعدادات برنامج الحماية من الفيروسات من Microsoft Defender **وتعديلها وتحديثها**|[استخدم WMI لتكوين برنامج الحماية من الفيروسات من Microsoft Defender وإدارته] (/windows/security/threat-protection/microsoft-defender-antivirus/use-wmi-microsoft-defender-antivirus <br/><br/> [مراجعة قائمة فئات WMI المتوفرة وأمثلة البرامج النصية](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal) <br/><br/> راجع أيضا [المعلومات المرجعية لموفر Windows Defender WMIv2](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal?redirectedfrom=MSDN) المؤرشف|

## <a name="configure-microsoft-defender-for-endpoint-with-microsoft-malware-protection-command-line-utility-mpcmdrunexe"></a>تكوين Microsoft Defender لنقطة النهاية باستخدام الأداة المساعدة Command-Line حماية البرامج الضارة من Microsoft (MPCmdRun.exe)

على جهاز فردي، يمكنك تشغيل فحص، وبدء تتبع التشخيص، والتحقق من تحديثات معلومات الأمان، والمزيد باستخدام أداة سطر الأوامر mpcmdrun.exe. يمكنك العثور على الأداة المساعدة في `%ProgramFiles%\Windows Defender\MpCmdRun.exe`. قم بتشغيله من موجه الأوامر.

لمعرفة المزيد، راجع [تكوين برنامج الحماية من الفيروسات من Microsoft Defender وإدارته باستخدام mpcmdrun.exe](/windows/security/threat-protection/microsoft-defender-antivirus/command-line-arguments-microsoft-defender-antivirus).

## <a name="configure-your-microsoft-365-defender-portal"></a>تكوين مدخل Microsoft 365 Defender

إذا لم تكن قد فعلت ذلك بالفعل، فقم بتكوين <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">مدخل Microsoft 365 Defender</a> لعرض التنبيهات، وتكوين ميزات الحماية من التهديدات، وعرض معلومات مفصلة حول وضع الأمان العام لمؤسستك.

يمكنك أيضا تكوين ما إذا كان يمكن للمستخدمين النهائيين رؤيتها وما هي الميزات التي يمكنهم رؤيتها في مركز حماية Microsoft Defender.

- [نظرة عامة على مركز حماية Microsoft Defender](/microsoft-365/security/defender-endpoint/use)
- [حماية نقطة النهاية: مركز حماية Microsoft Defender](/mem/intune/protect/endpoint-protection-windows-10#microsoft-defender-security-center)

## <a name="next-steps"></a>الخطوات التالية

- [الحصول على نظرة عامة على إدارة المخاطر والثغرات الأمنية](/microsoft-365/security/defender-endpoint/next-gen-threat-and-vuln-mgt)
- [زيارة لوحة معلومات عمليات الأمان مركز حماية Microsoft Defender](/microsoft-365/security/defender-endpoint/security-operations-dashboard)
- [إدارة Microsoft Defender لنقطة النهاية باستخدام Intune](manage-mde-post-migration-intune.md)
