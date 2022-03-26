---
title: إدارة Microsoft Defender لنقطة النهاية باستخدام PowerShell و WMI MPCmdRun.exe
description: تعرف على كيفية إدارة Microsoft Defender ل Endpoint باستخدام PowerShell و WMI MPCmdRun.exe
keywords: بعد الترحيل، والإدارة، والعمليات، والصيانة، والاستخدام، و PowerShell، و WMI، MPCmdRun.exe، و Microsoft Defender ل Endpoint، وedr
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
ms.custom: admindeeplinkDEFENDER
ms.topic: article
ms.date: 11/29/2021
ms.reviewer: chventou
ms.openlocfilehash: b5794b978e35faa23df51528a077fe90444fdce1
ms.sourcegitcommit: 4af23696ff8b44872330202fe5dbfd2a69d9ddbf
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 11/30/2021
ms.locfileid: "63570906"
---
# <a name="manage-microsoft-defender-for-endpoint-with-powershell-wmi-and-mpcmdrunexe"></a>إدارة Microsoft Defender لنقطة النهاية باستخدام PowerShell و WMI MPCmdRun.exe

**ينطبق على:**
- [خطة Microsoft Defender لنقطة النهاية 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> هل تريد تجربة Microsoft Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

> [!NOTE]
> نوصي [باستخدام إدارة نقاط النهاية من Microsoft لإدارة](/mem) ميزات الحماية من المخاطر في مؤسستك للأجهزة (يشار إليها أيضا بنقاط النهاية). إدارة نقاط النهاية [تتضمن Microsoft Intune](/mem/intune/fundamentals/what-is-intune) [Microsoft Endpoint Configuration Manager.](/mem/configmgr/core/understand/introduction)
>
> - [تعرف على المزيد حول إدارة نقاط النهاية](/mem/endpoint-manager-overview)
> - [المشاركة في إدارة Microsoft Defender لنقطة النهاية على أجهزة Windows 10 Windows 11 باستخدام "إدارة التكوين" و"Intune"](manage-mde-post-migration-intune.md)
> - [إدارة Microsoft Defender لنقطة النهاية باستخدام Intune](manage-mde-post-migration-intune.md)

يمكنك إدارة بعض إعدادات برنامج الحماية من الفيروسات من Microsoft Defender على الأجهزة باستخدام [PowerShell](#configure-microsoft-defender-for-endpoint-with-powershell) Windows [إدارة](#configure-microsoft-defender-for-endpoint-with-windows-management-instrumentation-wmi) الأجهزة (WMI) وأدوات سطر أوامر الحماية من البرامج الضارة من [Microsoft](#configure-microsoft-defender-for-endpoint-with-microsoft-malware-protection-command-line-utility-mpcmdrunexe) (MPCmdRun.exe). على سبيل المثال، يمكنك إدارة بعض برنامج الحماية من الفيروسات من Microsoft Defender الإعدادات. وفي بعض الحالات، يمكنك تخصيص قواعد تقليل مساحة الهجوم وإعدادات الحماية من الهجمات.

> [!IMPORTANT]
> يمكن الكتابة فوق ميزات الحماية من المخاطر التي تقوم بتكوينها باستخدام PowerShell أو WMI أو MCPmdRun.exe بواسطة إعدادات التكوين التي يتم نشرها باستخدام Intune أو Configuration Manager.

## <a name="configure-microsoft-defender-for-endpoint-with-powershell"></a>تكوين Microsoft Defender لنقطة النهاية باستخدام PowerShell

يمكنك استخدام PowerShell لإدارة برنامج الحماية من الفيروسات من Microsoft Defender والحماية من الهجمات وقواعد الحد من الهجمات.<br/><br/>

|مهمة|الموارد لمعرفة المزيد|
|---|---|
|**إدارة برنامج الحماية من الفيروسات من Microsoft Defender** <br/><br/> عرض حالة الحماية من البرامج الضارة وتكوين التفضيلات لمسح برامج الحماية من الفيروسات & التحديثات، وأ إجراء تغييرات أخرى على الحماية من الفيروسات.*|[استخدم PowerShell cmdlets لتكوين وإدارة برنامج الحماية من الفيروسات من Microsoft Defender](/windows/security/threat-protection/microsoft-defender-antivirus/use-powershell-cmdlets-microsoft-defender-antivirus) <br/><br/> [استخدام PowerShell cmdlets لتمكين الحماية التي يتم تسليمها من السحابة](/windows/security/threat-protection/microsoft-defender-antivirus/enable-cloud-protection-microsoft-defender-antivirus#use-powershell-cmdlets-to-enable-cloud-delivered-protection)|
|**تكوين الحماية من المخاطر** للحد من المخاطر على أجهزة مؤسستك <br/><br/> *نوصي باستخدام الحماية من استغلال في [وضع التدقيق](/microsoft-365/security/defender-endpoint/evaluate-exploit-protection#powershell) في بادئ الأمر. بهذه الطريقة، يمكنك معرفة كيف تؤثر الحماية من استغلال التطبيقات التي تستخدمها مؤسستك.*|[تخصيص الحماية من استغلال](/microsoft-365/security/defender-endpoint/customize-exploit-protection) <br/><br/> [PowerShell cmdlets للحماية من استغلال](/microsoft-365/security/defender-endpoint/customize-exploit-protection#powershell-reference)|
|**تكوين قواعد الحد من سطح الهجوم** باستخدام PowerShell <br/><br/> *يمكنك استخدام PowerShell لاستبعاد الملفات والمجلدات من قواعد تقليل مساحة الهجوم.*|[تخصيص قواعد تقليل مساحة الهجوم: استخدام PowerShell لاستبعاد الملفات & المجلدات](/microsoft-365/security/defender-endpoint/customize-attack-surface-reduction#use-powershell-to-exclude-files-and-folders) <br/><br/> راجع أيضا أداة واجهة المستخدم الرسومية الخاصة ب [António Vasconcelo](https://github.com/anvascon/MDATP_PoSh_Scripts/tree/master/ASR%20GUI) لإعداد قواعد تقليل مساحة الهجوم باستخدام PowerShell.|
|**تمكين حماية الشبكة** باستخدام PowerShell <br/><br/> *يمكنك استخدام PowerShell لتمكين "حماية الشبكة".*|[تشغيل "حماية الشبكة" باستخدام PowerShell](/microsoft-365/security/defender-endpoint/enable-network-protection#powershell)|
|**تكوين الوصول إلى المجلدات الخاضعة للتحكم** للحماية من برامج الفدية الضارة <br/><br/> *[يشار أيضا إلى الوصول](/microsoft-365/security/defender-endpoint/controlled-folders) إلى المجلدات الخاضعة للتحكم بالحماية من البرامج الضارة.*|[تمكين الوصول المتحكم به إلى المجلدات باستخدام PowerShell](/microsoft-365/security/defender-endpoint/enable-controlled-folders#powershell)|
|**تكوين جدار حماية Microsoft Defender** لحظر تدفق حركة مرور الشبكة غير المصرح بها إلى أجهزة مؤسستك أو خارجها|[جدار الحماية ل Microsoft Defender مع إدارة الأمان المتقدمة باستخدام Windows PowerShell](/windows/security/threat-protection/windows-firewall/windows-firewall-with-advanced-security-administration-with-windows-powershell)|
|**قم بتكوين التشفير و BitLocker** لحماية المعلومات على أجهزة المؤسسة التي تعمل Windows|[دليل مرجعي BitLocker PowerShell](/powershell/module/bitlocker/)|

## <a name="configure-microsoft-defender-for-endpoint-with-windows-management-instrumentation-wmi"></a>تكوين Microsoft Defender لنقطة النهاية Windows أدوات الإدارة (WMI)

WMI هو واجهة النصية التي تسمح لك باسترداد الإعدادات وتعديلها وتحديثها. لمعرفة المزيد، راجع [استخدام WMI](/windows/win32/wmisdk/using-wmi).<br/><br/>

|مهمة|الموارد لمعرفة المزيد|
|---|---|
|**تمكين الحماية التي يتم تسليمها من السحابة** على جهاز|[استخدام Windows إدارة الخدمة (WMI) لتمكين الحماية التي يتم تسليمها من السحابة](/windows/security/threat-protection/microsoft-defender-antivirus/enable-cloud-protection-microsoft-defender-antivirus#use-windows-management-instruction-wmi-to-enable-cloud-delivered-protection)|
|**استرداد إعدادات الإعدادات وتعديلها وتحديثها** برنامج الحماية من الفيروسات من Microsoft Defender|[استخدم WMI لتكوين برنامج الحماية من الفيروسات من Microsoft Defender](/windows/security/threat-protection/microsoft-defender-antivirus/use-wmi-microsoft-defender-antivirus <br/><br/> [مراجعة قائمة فئات WMI المتوفرة وأمثلة البرامج النصية](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal) <br/><br/> راجع أيضا المعلومات المرجعية Windows [Defender WMIv2](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal?redirectedfrom=MSDN)|

## <a name="configure-microsoft-defender-for-endpoint-with-microsoft-malware-protection-command-line-utility-mpcmdrunexe"></a>تكوين Microsoft Defender لنقطة النهاية باستخدام الأداة المساعدة للحماية من البرامج الضارة Command-Line Microsoft (MPCmdRun.exe)

على جهاز فردي، يمكنك تشغيل عملية فحص، وبدء تتبع التشخيص، والتحقق من وجود تحديثات لذكاء الأمان، والمزيد باستخدام mpcmdrun.exe سطر الأوامر. يمكنك العثور على الأداة المساعدة في `%ProgramFiles%\Windows Defender\MpCmdRun.exe`. تشغيله من موجه أوامر.

لمعرفة المزيد، راجع تكوين [وإدارة برنامج الحماية من الفيروسات من Microsoft Defender باستخدام mpcmdrun.exe](/windows/security/threat-protection/microsoft-defender-antivirus/command-line-arguments-microsoft-defender-antivirus).

## <a name="configure-your-microsoft-365-defender-portal"></a>تكوين مدخل Microsoft 365 Defender

إذا لم تكن قد فعلت ذلك بعد، ف قم <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">بتكوين</a> مدخل Microsoft 365 Defender لعرض التنبيهات وتكوين ميزات الحماية من المخاطر وعرض معلومات مفصلة حول الوضع الأمني العام لم مؤسستك.

يمكنك أيضا تكوين الميزات التي يمكن للمستخدمين رؤياها في مركز حماية Microsoft Defender.

- [نظرة عامة على مركز حماية Microsoft Defender](/microsoft-365/security/defender-endpoint/use)

- [حماية نقطة النهاية: مركز حماية Microsoft Defender](/mem/intune/protect/endpoint-protection-windows-10#microsoft-defender-security-center)

## <a name="next-steps"></a>الخطوات التالية

- [احصل على نظرة عامة حول إدارة المخاطر والثغرات الأمنية](/microsoft-365/security/defender-endpoint/next-gen-threat-and-vuln-mgt)

- [زيارة لوحة مركز حماية Microsoft Defender عمليات الأمان](/microsoft-365/security/defender-endpoint/security-operations-dashboard)

- [إدارة Microsoft Defender لنقطة النهاية باستخدام Intune](manage-mde-post-migration-intune.md)
