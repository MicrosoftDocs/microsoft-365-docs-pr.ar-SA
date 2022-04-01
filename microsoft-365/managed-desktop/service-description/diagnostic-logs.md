---
title: سجلات التشخيص
description: السجلات التي قد يتم تجميعها من الأجهزة أثناء استكشاف الأخطاء وإصلاحها وكيفية تخزينها
keywords: سطح المكتب المدار من Microsoft، Microsoft 365، الخدمة، الوثائق
ms.service: m365-md
author: tiaraquan
ms.localizationpriority: medium
ms.collection: M365-modern-desktop
ms.author: tiaraquan
manager: dougeby
ms.topic: article
ms.openlocfilehash: 808ce2e426a0540c95195f26c9872f569e595715
ms.sourcegitcommit: 559df2c86a7822463ce0597140537bab260c746a
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 02/15/2022
ms.locfileid: "63579586"
---
# <a name="diagnostic-logs"></a>سجلات التشخيص

سواء كنت قد قمت ب التقارير عن مشكلة أو تم التعرف على مشكلة من خلال خدمتنا، فقد نحتاج إلى جمع سجلات تشخيص معينة من الجهاز دون تدخل من المستخدم.

لا نجمع أي محتوى أو معلومات تم إنشاؤها من قبل المستخدم من دليل المستخدم. نحن نجمع فقط بيانات التشخيص والسجل التي تتعلق بصحة الجهاز ووضعه.

نقوم بتخزين أي سجلات تم تجميعها لمدة 28 يوما، ثم نحذفها. نحن نعالج أي سجلات يتم تجميعها من جهاز باتباع [معايير معالجة البيانات لدينا](privacy-personal-data.md).

## <a name="data-collected"></a>البيانات التي يتم تجميعها

تتضمن هذه القائمة أدناه كل المجلدات أو سجلات الأحداث أو الملفات القابلة للتنفيذ أو مواقع التسجيل التي قد يقوم Microsoft Managed Desktop بتجميع سجلات تشخيص منها. ستكون البيانات الفعلية التي يتم تجميعها مجموعة فرعية من هذه القائمة وتعتمد على المشكلة المحددة.

### <a name="registry-keys"></a>مفاتيح التسجيل

- HKLMSYSTEMCurrentControlSetServices\\\\\\
- HKLMSOFTWAREMicrosoftSurface\\\\\\
- HKLMSOFTWAREPoliciesMicrosoft\\\\\\\\ Windows\\ WindowsUpdate
- HKLMSYSTEMCurrentControlSetControlMUIUILanguages\\\\\\\\\\
- HKLMSoftwarePoliciesMicrosoftWindowsStore\\\\\\\\
- HKLMSoftwareMicrosoft\\\\\\ Windows\\ CurrentVersionWindowsStoreWindowsUpdate\\\\
- HKLMSOFTWAREMicrosoft\\\\ Windows\\ NTCurrentVersion\\
- HKLMSOFTWAREMicrosoft\\\\ Windows\\ NTCurrentVersion\\
- HKLMSOFTWAREMicrosoft\\\\\\ Windows\\ CurrentVersionAppModel\\
- HKLMSYSTEMCurrentControlSetControlFirmwareResources\\\\\\\\
- HKLMSOFTWAREMicrosoftWindowsSelfhost\\\\\\
- HKLMSOFTWAREMicrosoftWindowsUpdate\\\\\\
- HKLMSOFTWAREMicrosoft\\\\\\ Windows\\ CurrentVersionAppx\\
- HKLMSOFTWAREMicrosoft\\\\ Windows\\ NTCurrentVersionSuperfetch\\\\
- HKLMSYSTEMSetup\\\\
- HKLMSoftwareMicrosoftIntuneManagementExtension\\\\\\
- HKLMSOFTWAREMicrosoftSystemCertificatesAuthRoot\\\\\\\\
- HKLMSOFTWAREMicrosoft\\\\\\ Windows المتقدمة للحماية من المخاطر
- HKLMSOFTWAREMicrosoft\\\\\\ Windows\\ CurrentVersionAuthenticationLogonUI\\\\
- HKLMSOFTWAREMicrosoft\\\\\\ Windows\\ CurrentVersionInternet\\ الإعدادات
- HKLMSoftwareMicrosoft\\\\\\ Windows\\ CurrentVersionUninstall\\
- HKLMSoftwarePolicies\\\\
- HKLMSOFTWAREPoliciesMicrosoftCryptographyConfigurationSL\\\\\\\\\\\\
- HKLMSOFTWAREPoliciesMicrosoft\\\\\\\\ Windows المتقدمة للحماية من المخاطر
- HKLMSOFTWAREWOW6432NodeMicrosoft\\\\\\\\ Windows\\ CurrentVersionUninstall\\
- HKLMSYSTEMCurrentControlSetControlSecurityProvidersSCHANNEL\\\\\\\\\\

### <a name="commands"></a>الأوامر

- ٪programfiles٪\\windows defendermpcmdrun.exe\\ -GetFiles
- ٪windir٪\\system32\\certutil.exe -store
- ٪windir٪\\system32\\certutil.exe -store -user my
- ٪windir٪\\system32\\Dsregcmd.exe /status
- ٪windir٪\\system32\\ipconfig.exe /all
- ٪windir٪\\system32\\ipconfig.exe /displaydns
- ٪windir٪\\system32\\mdmdiagnosticstool.exe
- ٪windir٪\\system32\\msinfo32.exe /report ٪temp٪\\MDMDiagnosticsmsinfo32.log\\
- ٪windir٪\\system32\\netsh.exe advfirewall إظهار allprofiles
- ٪windir٪\\system32\\netsh.exe advfirewall إظهار عام
- ٪windir٪\\system32\\netsh.exe lan إظهار ملفات التعريف
- ٪windir٪\\system32\\netsh.exe winhttp إظهار الوكيل
- ٪windir٪\\system32\\netsh.exe wlan إظهار ملفات التعريف
- ٪windir٪\\system32\\netsh.exe wlan إظهار wlanreport
- ٪windir٪\\system32\\ping.exe -n 50 localhost
- ٪windir٪\\system32\\powercfg.exe /batteryreport /output ٪temp٪\\MDMDiagnosticsbattery-report.html\\
- ٪windir٪\\system32\\powercfg.exe /energy /output ٪temp٪\\MDMDiagnosticsenergy-report.html\\
- bitsadmin /list /allusers /verbose
- fltMC.exe
- bcdedit /enum all /v
- manage-bde -protectors -get
- Windows PowerShell الأوامر:
    - Get-appxpackage -allusers
    - Get-appxpackage -packagetype package
    - Get-Service wuauserv
    - Get-NetFirewallRule
    - Get-WmiObject -Class win32product\_
    - Get-ComputerInfo
    - Get-Service
    - Get-Process
    - Get-WmiObject Win32PnPSignedDriver\_

### <a name="event-logs"></a>سجلات الأحداث

- Application
- Microsoft-Windows-AppLocker/EXE و DLL
- Microsoft-Windows-AppLocker/MSI والنص النصي
- Microsoft-Windows-AppLocker/Packaged app-Deployment
- Microsoft-Windows-AppLocker/Packaged app-Execution
- Microsoft-Windows-Bitlocker/Bitlocker Management
- Microsoft-Windows-SENSE/التشغيلية
- Microsoft-Windows-SenseIR/التشغيلية
- الإعداد
- النظام

### <a name="files"></a>الملفات

- ٪ProgramData٪\\MicrosoftDiagnosticLogCSPCollectors.etl\\\\\\\*
- ٪ProgramData٪\\MicrosoftIntuneManagementExtensionLogs\\\\\\\*.\*
- ٪ProgramData٪\\Microsoft\\ Windows DefenderSupport\\MpSupportFiles.cab\\
- ٪ProgramData٪\\Microsoft\\ Windows\\ WlanReportwlan-report-latest.html\\
- ٪ProgramData٪\\Microsoft\\ Windows\\ WlanReport -SourceFileName wlan-report-latest.html
- ٪windir٪\\ccmlogs.log\\\*
- ٪windir٪\\ccmsetuplogs.log\\\*
- ٪windir٪\\logsCBScbs.log\\\\
- ٪windir٪\\logsmeasuredboot\*\\.\*
- ٪windir٪\\LogsWindowsUpdate.etl\\\*
- ٪windir٪\\inf.log\\\*
- ٪windir٪\\servicingsesions\\ActionList.xml\\
- ٪windir٪\\servicingsesions\\Sessions.xml\\
- ٪windir٪\\SoftwareDistributionDataStoreLogsedb.log\\\\\\
- ٪windir٪\\SoftwareDistributionDataStoreDataStore.edb\\\\
- ٪windir٪\\logsdismdism.log\\\\
- ٪SystemRoot٪\\System32WinevtLogs\\\\\\
- ٪appdata٪\\Microsoft\\ Teams\\ media-stack.blog\\\*
- ٪appdata٪\\Microsoft\\ Teams\\ skylib.blog\\\*
- ٪appdata٪\\Microsoft\\ Teams\\ media-stack.etl\\\*
- ٪appdata٪Microsoft\\ Teams\\\\logs.txt
- ٪windir٪\\Windows System32winevt\\\\\*.\\\*