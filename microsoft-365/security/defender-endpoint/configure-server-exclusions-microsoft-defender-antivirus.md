---
title: تكوين برنامج الحماية من الفيروسات من Microsoft Defender استثناءات على Windows Server
ms.reviewer: pahuijbr
manager: dansimp
description: Windows Server استثناءات تلقائية، استنادا إلى دور الخادم. يمكنك أيضا إضافة استثناءات مخصصة.
keywords: الاستثناءات، الخادم، الاستثناءات التلقائية، التلقائية، المخصصة، عمليات الفحص، برنامج الحماية من الفيروسات من Microsoft Defender
ms.prod: m365-security
ms.technology: mde
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
author: denisebmsft
ms.author: deniseb
ms.topic: article
ms.custom: nextgen
ms.date: 02/04/2022
ms.collection: M365-security-compliance
ms.openlocfilehash: 442172afc9caf5dbd2af8c91cda531494fabd05d
ms.sourcegitcommit: 954c8af658adb270fe843991e048c6a30e86e77c
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 02/06/2022
ms.locfileid: "63578171"
---
# <a name="configure-microsoft-defender-antivirus-exclusions-on-windows-server"></a>تكوين برنامج الحماية من الفيروسات من Microsoft Defender استثناءات على Windows Server


**ينطبق على:**

- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- برنامج الحماية من الفيروسات من Microsoft Defender

برنامج الحماية من الفيروسات من Microsoft Defender على Windows Server 2016 Windows Server 2019 تسجيلك تلقائيا في استثناءات معينة، كما هو محدد بواسطة دور الخادم المحدد. لا تظهر هذه الاستثناءات في قوائم الاستثناء القياسية التي تظهر في [أمن Windows التطبيق](microsoft-defender-security-center-antivirus.md).

بالإضافة إلى الاستثناءات التلقائية المعرفة بدور الخادم، يمكنك إضافة استثناءات مخصصة أو إزالتها. للقيام بذلك، يمكنك الرجوع إلى المقالات التالية:
- [تكوين الاستثناءات والتحقق من صحتها استنادا إلى اسم الملف والملحق وموقع المجلد](configure-extension-file-exclusions-microsoft-defender-antivirus.md)
- [تكوين الاستثناءات والتحقق من صحتها للملفات التي يتم فتحها بواسطة العمليات](configure-process-opened-file-exclusions-microsoft-defender-antivirus.md)

## <a name="a-few-points-to-keep-in-mind"></a>بعض النقاط التي يجب تذكرها

ضع النقاط الهامة التالية في الاعتبار:

- وتأخذ الاستثناءات المخصصة الأسبقية على الاستثناءات التلقائية.
- تنطبق الاستثناءات التلقائية فقط على مسح الحماية في الوقت الحقيقي (RTP). لا يتم احترام الاستثناءات التلقائية أثناء الفحص الكامل أو السريع أو عند الطلب.
- لا تتضارب الاستثناءات المخصصة والمكررة مع الاستثناءات التلقائية.
- برنامج الحماية من الفيروسات من Microsoft Defender استخدام أدوات "نشر خدمة الصور وإدارتها" (DISM) لتحديد الأدوار المثبتة على الكمبيوتر.
- Windows لا تتوفر في Server 2012 R2 برنامج الحماية من الفيروسات من Microsoft Defender كميزة قابلة للتثبيت. عندما تقوم بتركيب هذه الخوادم في Defender for Endpoint، سيتم تثبيت برنامج الحماية من الفيروسات لـ Windows Defender، كما يتم تطبيق الاستثناءات الافتراضية لملفات نظام التشغيل. ومع ذلك، لا تنطبق الاستثناءات لأدوار الخادم (كما هو محدد أدناه) تلقائيا، ويجب عليك تكوين هذه الاستثناءات حسب الاقتضاء. لمعرفة المزيد، راجع [Windows إلى خدمة Microsoft Defender for Endpoint](configure-server-endpoints.md).

توفر هذه المقالة نظرة عامة حول الاستثناءات برنامج الحماية من الفيروسات من Microsoft Defender على Windows Server 2016 أو أي وقت لاحق.

نظرا برنامج الحماية من الفيروسات من Microsoft Defender الملفات مضمنة في Windows Server 2016 واللاحقة، تحدث الاستثناءات لملفات نظام التشغيل وأدوار الخادم تلقائيا. ومع ذلك، يمكنك تعريف الاستثناءات المخصصة. يمكنك أيضا إلغاء الاشتراك في الاستثناءات التلقائية إذا لزم الأمر.

تتضمن هذه المقالة المقاطع التالية:

<br/><br/>

|مقطع|الوصف|
|---|---|
|[الاستثناءات التلقائية على Windows Server 2016 أو أي وقت لاحق](#automatic-exclusions-on-windows-server-2016-or-later)|يصف النوعين الأساسيين من الاستثناءات التلقائية ويتضمن قائمة مفصلة بالاستثناءات التلقائية|
|[إلغاء الاشتراك في الاستثناءات التلقائية](#opting-out-of-automatic-exclusions)|يتضمن اعتبارات وإجراءات هامة تصف كيفية إلغاء الاشتراك في الاستثناءات التلقائية|
|[تحديد الاستثناءات المخصصة](#defining-custom-exclusions)|توفير ارتباطات إلى معلومات المساعدة لتعريف الاستثناءات المخصصة|

## <a name="automatic-exclusions-on-windows-server-2016-or-later"></a>الاستثناءات التلقائية على Windows Server 2016 أو أي وقت لاحق

في Windows Server 2016 أو أي وقت لاحق، يجب ألا تحتاج إلى تعريف الاستثناءات التالية:

- ملفات نظام التشغيل
- أدوار الخادم وأي ملفات يتم إضافتها من خلال أدوار الخادم

نظرا برنامج الحماية من الفيروسات من Microsoft Defender مضمنة، فإنه لا يتطلب استثناءات لملفات نظام التشغيل على Windows Server 2016 أو أي وقت لاحق. بالإضافة إلى ذلك، عند تشغيل Windows Server 2016 أو أي وقت لاحق وتثبيت دور، يتضمن برنامج الحماية من الفيروسات من Microsoft Defender استثناءات تلقائية لدور الخادم وأي ملفات مضافة أثناء تثبيت الدور.

لا تظهر استثناءات نظام التشغيل واستثناءات دور الخادم في قوائم الاستثناء القياسية التي تظهر [في تطبيق أمن Windows.](microsoft-defender-security-center-antivirus.md)

> [!NOTE]
> لا تنطبق الاستثناءات التلقائية لأدوار الخادم وملفات نظام التشغيل على Windows Server 2012. يمكن تطبيق الاستثناءات التلقائية إذا كانت الخوادم Windows Server 2012 R2 قيد التشغيل في Defender for Endpoint. (راجع [Windows إلى خدمة Microsoft Defender for Endpoint](configure-server-endpoints.md).)


### <a name="the-list-of-automatic-exclusions"></a>قائمة الاستثناءات التلقائية

تحتوي المقاطع التالية على الاستثناءات التي يتم تسليمها مع مسارات ملفات الاستثناءات التلقائية وأنواع الملفات.

#### <a name="default-exclusions-for-all-roles"></a>الاستثناءات الافتراضية لكل الأدوار

يسرد هذا القسم الاستثناءات الافتراضية لكل الأدوار في Windows Server 2016 و Windows Server 2019 و Windows Server 2022.

> [!NOTE]
> قد تختلف المواقع الافتراضية عما هو مذكور في هذه المقالة.

##### <a name="windows-tempedb-files"></a>Windows ملفات "temp.edb"

- `%windir%\SoftwareDistribution\Datastore\*\tmp.edb`
- `%ProgramData%\Microsoft\Search\Data\Applications\Windows\windows.edb`

##### <a name="windows-update-files-or-automatic-update-files"></a>Windows تحديث الملفات أو التحديث التلقائي

- `%windir%\SoftwareDistribution\Datastore\*\Datastore.edb`
- `%windir%\SoftwareDistribution\Datastore\*\edb.chk`
- `%windir%\SoftwareDistribution\Datastore\*\edb\*.log`
- `%windir%\SoftwareDistribution\Datastore\*\Edb\*.jrs`
- `%windir%\SoftwareDistribution\Datastore\*\Res\*.log`

##### <a name="windows-security-files"></a>أمن Windows الملفات

- `%windir%\Security\database\*.chk`
- `%windir%\Security\database\*.edb`
- `%windir%\Security\database\*.jrs`
- `%windir%\Security\database\*.log`
- `%windir%\Security\database\*.sdb`

##### <a name="group-policy-files"></a>ملفات نهج المجموعة

- `%allusersprofile%\NTUser.pol`
- `%SystemRoot%\System32\GroupPolicy\Machine\registry.pol`
- `%SystemRoot%\System32\GroupPolicy\User\registry.pol`

##### <a name="wins-files"></a>ملفات WINS

- `%systemroot%\System32\Wins\*\*.chk`
- `%systemroot%\System32\Wins\*\*.log`
- `%systemroot%\System32\Wins\*\*.mdb`
- `%systemroot%\System32\LogFiles\`
- `%systemroot%\SysWow64\LogFiles\`

##### <a name="file-replication-service-frs-exclusions"></a>استثناءات خدمة النسخ المتماثل للملفات (FRS)

- الملفات الموجودة في مجلد العمل خدمة النسخ المتماثل للملفات (FRS). تم تحديد مجلد عمل FRS في مفتاح التسجيل `HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\NtFrs\Parameters\Working Directory`

  - `%windir%\Ntfrs\jet\sys\*\edb.chk`
  - `%windir%\Ntfrs\jet\*\Ntfrs.jdb`
  - `%windir%\Ntfrs\jet\log\*\*.log`

- ملفات سجل قاعدة بيانات FRS. يتم تحديد مجلد ملف سجل قاعدة بيانات FRS في مفتاح التسجيل `HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\Ntfrs\Parameters\DB Log File Directory`

  - `%windir%\Ntfrs\*\Edb\*.log`

- مجلد ترحيل FRS. يتم تحديد مجلد الترحيل في مفتاح التسجيل `HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\NtFrs\Parameters\Replica Sets\GUID\Replica Set Stage`

  - `%systemroot%\Sysvol\*\Ntfrs_cmp*\`

- المجلد FRS الذي تم تثبيته مسبقا. يتم تحديد هذا المجلد بواسطة المجلد `Replica_root\DO_NOT_REMOVE_NtFrs_PreInstall_Directory`

  - `%systemroot%\SYSVOL\domain\DO_NOT_REMOVE_NtFrs_PreInstall_Directory\*\Ntfrs*\`

- قاعدة بيانات ومجلدات العمل لتكرار نظام الملفات الموزع (DFSR). يتم تحديد هذه المجلدات بواسطة مفتاح التسجيل `HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\DFSR\Parameters\Replication Groups\GUID\Replica Set Configuration File`

  > [!NOTE]
  > بالنسبة للمواقع المخصصة، راجع [إلغاء الاشتراك في الاستثناءات التلقائية](#opting-out-of-automatic-exclusions).

  - `%systemdrive%\System Volume Information\DFSR\$db_normal$`
  - `%systemdrive%\System Volume Information\DFSR\FileIDTable_*`
  - `%systemdrive%\System Volume Information\DFSR\SimilarityTable_*`
  - `%systemdrive%\System Volume Information\DFSR\*.XML`
  - `%systemdrive%\System Volume Information\DFSR\$db_dirty$`
  - `%systemdrive%\System Volume Information\DFSR\$db_clean$`
  - `%systemdrive%\System Volume Information\DFSR\$db_lostl$`
  - `%systemdrive%\System Volume Information\DFSR\Dfsr.db`
  - `%systemdrive%\System Volume Information\DFSR\*.frx`
  - `%systemdrive%\System Volume Information\DFSR\*.log`
  - `%systemdrive%\System Volume Information\DFSR\Fsr*.jrs`
  - `%systemdrive%\System Volume Information\DFSR\Tmp.edb`

##### <a name="process-exclusions"></a>استثناءات العملية

- `%systemroot%\System32\dfsr.exe`
- `%systemroot%\System32\dfsrs.exe`

##### <a name="hyper-v-exclusions"></a>Hyper-V استثناءات

يسرد الجدول التالي استثناءات أنواع الملفات واستثناءات المجلدات واستثناءات العمليات التي يتم تسليمها تلقائيا عند تثبيت Hyper-V الملف.

<br><br/>

|نوع الاستثناء|تفاصيل|
|---|---|
|أنواع الملفات|`*.vhd` <br/> `*.vhdx` <br/> `*.avhd` <br/> `*.avhdx` <br/> `*.vsv` <br/> `*.iso` <br/> `*.rct` <br/> `*.vmcx` <br/> `*.vmrs`|
|المجلدات|`%ProgramData%\Microsoft\Windows\Hyper-V` <br/> `%ProgramFiles%\Hyper-V` <br/> `%SystemDrive%\ProgramData\Microsoft\Windows\Hyper-V\Snapshots` <br/> `%Public%\Documents\Hyper-V\Virtual Hard Disks`|
|العمليات|`%systemroot%\System32\Vmms.exe` <br/> `%systemroot%\System32\Vmwp.exe`|

##### <a name="sysvol-files"></a>ملفات SYSVOL

- `%systemroot%\Sysvol\Domain\*.adm`
- `%systemroot%\Sysvol\Domain\*.admx`
- `%systemroot%\Sysvol\Domain\*.adml`
- `%systemroot%\Sysvol\Domain\Registry.pol`
- `%systemroot%\Sysvol\Domain\*.aas`
- `%systemroot%\Sysvol\Domain\*.inf`
- `%systemroot%\Sysvol\Domain\*Scripts.ini`
- `%systemroot%\Sysvol\Domain\*.ins`
- `%systemroot%\Sysvol\Domain\Oscfilter.ini`


#### <a name="active-directory-exclusions"></a>استثناءات Active Directory

يسرد هذا القسم الاستثناءات التي يتم تسليمها تلقائيا عند تثبيت خدمات مجال Active Directory (AD DS).

##### <a name="ntds-database-files"></a>ملفات قاعدة بيانات NTDS

يتم تحديد ملفات قاعدة البيانات في مفتاح التسجيل `HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\NTDS\Parameters\DSA Database File`

- `%windir%\Ntds\ntds.dit`
- `%windir%\Ntds\ntds.pat`

##### <a name="the-ad-ds-transaction-log-files"></a>ملفات سجل معاملات AD DS

يتم تحديد ملفات سجل المعاملات في مفتاح التسجيل `HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\NTDS\Parameters\Database Log Files Path`

- `%windir%\Ntds\EDB*.log`
- `%windir%\Ntds\Res*.log`
- `%windir%\Ntds\Edb*.jrs`
- `%windir%\Ntds\Ntds*.pat`
- `%windir%\Ntds\TEMP.edb`

##### <a name="the-ntds-working-folder"></a>مجلد العمل NTDS

تم تحديد هذا المجلد في مفتاح التسجيل `HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\NTDS\Parameters\DSA Working Directory`

- `%windir%\Ntds\Temp.edb`
- `%windir%\Ntds\Edb.chk`

##### <a name="process-exclusions-for-ad-ds-and-ad-ds-related-support-files"></a>استثناءات العملية لملفات الدعم ذات الصلة ب AD DS و AD DS

- `%systemroot%\System32\ntfrs.exe`
- `%systemroot%\System32\lsass.exe`

#### <a name="dhcp-server-exclusions"></a>استثناءات خادم DHCP

يسرد هذا القسم الاستثناءات التي يتم تسليمها تلقائيا عند تثبيت دور خادم DHCP. يتم تحديد مواقع ملفات DHCP Server بواسطة معلمات *DatabasePath* *وDhcpLogFilePath* و *BackupDatabasePath* في مفتاح التسجيل `HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\DHCPServer\Parameters`

- `%systemroot%\System32\DHCP\*\*.mdb`
- `%systemroot%\System32\DHCP\*\*.pat`
- `%systemroot%\System32\DHCP\*\*.log`
- `%systemroot%\System32\DHCP\*\*.chk`
- `%systemroot%\System32\DHCP\*\*.edb`

#### <a name="dns-server-exclusions"></a>استثناءات خادم DNS

يسرد هذا القسم استثناءات الملفات والمجلدات واستثناءات العملية التي يتم تسليمها تلقائيا عند تثبيت دور خادم DNS.

##### <a name="file-and-folder-exclusions-for-the-dns-server-role"></a>استثناءات الملفات والمجلدات لدور DNS Server

- `%systemroot%\System32\Dns\*\*.log`
- `%systemroot%\System32\Dns\*\*.dns`
- `%systemroot%\System32\Dns\*\*.scc`
- `%systemroot%\System32\Dns\*\BOOT`

##### <a name="process-exclusions-for-the-dns-server-role"></a>استثناءات العملية لدور DNS Server

- `%systemroot%\System32\dns.exe`

#### <a name="file-and-storage-services-exclusions"></a>استثناءات خدمات التخزين والملفات

يسرد هذا القسم استثناءات الملفات والمجلدات التي يتم تسليمها تلقائيا عند تثبيت دور "خدمات التخزين والملفات". لا تتضمن الاستثناءات المذكورة أدناه استثناءات لدور "تجميع".

- `%SystemDrive%\ClusterStorage`
- `%clusterserviceaccount%\Local Settings\Temp`
- `%SystemDrive%\mscs`

#### <a name="print-server-exclusions"></a>استثناءات خادم الطباعة

يسرد هذا القسم استثناءات أنواع الملفات واستثناءات المجلدات واستثناءات العملية التي يتم تسليمها تلقائيا عند تثبيت دور خادم الطباعة.

##### <a name="file-type-exclusions"></a>استثناءات أنواع الملفات

- `*.shd`
- `*.spl`

##### <a name="folder-exclusions"></a>استثناءات المجلدات

تم تحديد هذا المجلد في مفتاح التسجيل `HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Print\Printers\DefaultSpoolDirectory`

- `%system32%\spool\printers\*`

##### <a name="process-exclusions"></a>استثناءات العملية

- `spoolsv.exe`

#### <a name="web-server-exclusions"></a>استثناءات Web Server

يسرد هذا القسم استثناءات المجلدات واستثناءات العملية التي يتم تسليمها تلقائيا عند تثبيت دور Web Server.

##### <a name="folder-exclusions"></a>استثناءات المجلدات

- `%SystemRoot%\IIS Temporary Compressed Files`
- `%SystemDrive%\inetpub\temp\IIS Temporary Compressed Files`
- `%SystemDrive%\inetpub\temp\ASP Compiled Templates`
- `%systemDrive%\inetpub\logs`
- `%systemDrive%\inetpub\wwwroot`

##### <a name="process-exclusions"></a>استثناءات العملية

- `%SystemRoot%\system32\inetsrv\w3wp.exe`
- `%SystemRoot%\SysWOW64\inetsrv\w3wp.exe`
- `%SystemDrive%\PHP5433\php-cgi.exe`

##### <a name="turning-off-scanning-of-files-in-the-sysvolsysvol-folder-or-the-sysvol_dfsrsysvol-folder"></a>إيقاف تشغيل مسح الملفات في مجلد Sysvol\Sysvol أو مجلد SYSVOL_DFSR\Sysvol

الموقع الحالي للمجلد `Sysvol\Sysvol` أو `SYSVOL_DFSR\Sysvol` وجميع المجلدات الفرعية هو هدف إعادة تحديد نظام الملفات لجذر مجموعة النسخ المتماثلة. يستخدم `Sysvol\Sysvol` المجلدان `SYSVOL_DFSR\Sysvol` و المواقع التالية بشكل افتراضي:

- `%systemroot%\Sysvol\Domain`
- `%systemroot%\Sysvol_DFSR\Domain`

تشير مشاركة `SYSVOL` NETLOGON إلى المسار إلى النشطة حاليا ويمكن تحديده بواسطة اسم قيمة SysVol في المفتاح الفرعي التالي: `HKEY_LOCAL_MACHINE\SYSTEM\ControlSet001\Services\Netlogon\Parameters`

استبعاد الملفات التالية من هذا المجلد وجميع المجلدات الفرعية الخاصة به:

- `*.adm`
- `*.admx`
- `*.adml`
- `Registry.pol`
- `Registry.tmp`
- `*.aas`
- `*.inf`
- `Scripts.ini`
- `*.ins`
- `Oscfilter.ini`

#### <a name="windows-server-update-services-exclusions"></a>خادم Windows Server Update Services استثناءات

يسرد هذا القسم استثناءات المجلدات التي يتم تسليمها تلقائيا عند تثبيت خادم Windows Server Update Services (WSUS). تم تحديد مجلد WSUS في مفتاح التسجيل `HKEY_LOCAL_MACHINE\Software\Microsoft\Update Services\Server\Setup`

- `%systemroot%\WSUS\WSUSContent`
- `%systemroot%\WSUS\UpdateServicesDBFiles`
- `%systemroot%\SoftwareDistribution\Datastore`
- `%systemroot%\SoftwareDistribution\Download`

## <a name="opting-out-of-automatic-exclusions"></a>إلغاء الاشتراك في الاستثناءات التلقائية

في Windows Server 2016 واللاحقة، لا تستبعد الاستثناءات المحددة مسبقا التي يتم تسليمها بواسطة تحديثات معلومات الأمان سوى المسارات الافتراضية لدور أو ميزة. إذا قمت بتثبيت دور أو ميزة في مسار مخصص، أو إذا كنت تريد التحكم يدويا في مجموعة الاستثناءات، فتأكد من إلغاء الاشتراك في الاستثناءات التلقائية التي يتم تسليمها في تحديثات معلومات الأمان. ولكن ضع في اعتبارك أنه تم تحسين الاستثناءات التي يتم تسليمها تلقائيا Windows Server 2016 واللاحقة. راجع [التوصيات تعريف الاستثناءات](configure-exclusions-microsoft-defender-antivirus.md#recommendations-for-defining-exclusions) قبل تعريف قوائم الاستثناء.

> [!WARNING]
> قد يؤثر إلغاء الاشتراك في الاستثناءات التلقائية سلبا على الأداء، أو قد يؤدي إلى تلف البيانات. يتم تحسين الاستثناءات التي يتم تسليمها تلقائيا لأدوار Windows Server 2016 و Windows Server 2019 و Windows Server 2022.

نظرا لأن الاستثناءات المحددة مسبقا تستبعد المسارات الافتراضية فقط، إذا قمت بنقل مجلدات NTDS وSYSVOL إلى محرك أقراص أو مسار آخر يختلف عن المسار الأصلي، فيجب إضافة الاستثناءات يدويا. راجع [تكوين قائمة الاستثناءات استنادا إلى اسم المجلد أو ملحق الملف](configure-extension-file-exclusions-microsoft-defender-antivirus.md#configure-the-list-of-exclusions-based-on-folder-name-or-file-extension).

يمكنك تعطيل قوائم الاستثناء التلقائي باستخدام "نهج المجموعة" و"PowerShell cmdlets" و"WMI".

### <a name="use-group-policy-to-disable-the-auto-exclusions-list-on-windows-server-2016-windows-server-2019-and-windows-server-2022"></a>استخدام نهج المجموعة لتعطيل قائمة الاستثناءات التلقائية على Windows Server 2016 و Windows Server 2019 و Windows Server 2022

1. على كمبيوتر إدارة نهج المجموعة، افتح [وحدة تحكم إدارة نهج المجموعة](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc725752(v=ws.11)). انقر ب الماوس الأيمن فوق كائن نهج المجموعة الذي تريد تكوينه، ثم حدد **تحرير**.

2. في محرر **إدارة نهج المجموعة** ، انتقل إلى **تكوين الكمبيوتر**، ثم حدد **القوالب الإدارية**.

3. قم بتوسيع الشجرة Windows **مكونات برنامج الحماية من الفيروسات من Microsoft Defender** \>  \> **الاستثناءات**.

4. انقر نقرا **مزدوجا فوق إيقاف تشغيل** الاستثناءات التلقائية، ثم قم بتعيين الخيار إلى **تمكين**. ثم حدد **موافق**.

### <a name="use-powershell-cmdlets-to-disable-the-auto-exclusions-list-on-windows-server"></a>استخدام PowerShell cmdlets لتعطيل قائمة الاستثناءات التلقائية على Windows Server

استخدم cmdlets التالية:

```PowerShell
Set-MpPreference -DisableAutoExclusions $true
```

لمعرفة المزيد، راجع الموارد التالية:

- [استخدم PowerShell cmdlets لتكوين برنامج الحماية من الفيروسات من Microsoft Defender](use-powershell-cmdlets-microsoft-defender-antivirus.md).
- [استخدم PowerShell مع برنامج الحماية من الفيروسات من Microsoft Defender](/powershell/module/defender/).

### <a name="use-windows-management-instruction-wmi-to-disable-the-auto-exclusions-list-on-windows-server"></a>استخدام Windows الإدارة (WMI) لتعطيل قائمة الاستثناءات التلقائية على Windows Server

استخدم **الأسلوب Set** للفئة [MSFT_MpPreference](/previous-versions/windows/desktop/defender/msft-mppreference) للخصائص التالية:

```WMI
DisableAutoExclusions
```

راجع ما يلي لمزيد من المعلومات والمعلمات المسموح بها:

- [Windows واجهات برمجة التطبيقات ل Defender WMIv2](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal)

## <a name="defining-custom-exclusions"></a>تحديد الاستثناءات المخصصة

إذا لزم الأمر، يمكنك إضافة استثناءات مخصصة أو إزالتها. للقيام بذلك، راجع المقالات التالية:

- [تكوين الاستثناءات والتحقق من صحتها استنادا إلى اسم الملف والملحق وموقع المجلد](configure-extension-file-exclusions-microsoft-defender-antivirus.md)
- [تكوين الاستثناءات والتحقق من صحتها للملفات التي يتم فتحها بواسطة العمليات](configure-process-opened-file-exclusions-microsoft-defender-antivirus.md)

## <a name="see-also"></a>راجع أيضًا

- [تكوين الاستثناءات والتحقق من صحتها برنامج الحماية من الفيروسات من Microsoft Defender المسح الضوئي](configure-exclusions-microsoft-defender-antivirus.md)
- [تكوين الاستثناءات والتحقق من صحتها استنادا إلى اسم الملف والملحق وموقع المجلد](configure-extension-file-exclusions-microsoft-defender-antivirus.md)
- [تكوين الاستثناءات والتحقق من صحتها للملفات التي يتم فتحها بواسطة العمليات](configure-process-opened-file-exclusions-microsoft-defender-antivirus.md)
- [الأخطاء الشائعة التي يجب تجنبها عند تعريف الاستثناءات](common-exclusion-mistakes-microsoft-defender-antivirus.md)
- [تخصيص نتائج عمليات المسح برنامج الحماية من الفيروسات من Microsoft Defender والوساطة وبدءها ومراجعتها](customize-run-review-remediate-scans-microsoft-defender-antivirus.md)
- [برنامج الحماية من الفيروسات من Microsoft Defender في Windows 10](microsoft-defender-antivirus-in-windows-10.md)
