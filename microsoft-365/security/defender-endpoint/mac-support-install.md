---
title: استكشاف مشاكل تثبيت Microsoft Defender for Endpoint على Mac وإصلاحها
description: استكشاف مشاكل التثبيت وإصلاحها في Microsoft Defender for Endpoint على Mac.
keywords: microsoft، defender، Microsoft Defender ل Endpoint، mac، تثبيت
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: 5f56e28d472cb3fdf8dd089effcd4beac6e42374
ms.sourcegitcommit: 6e90baef421ae06fd790b0453d3bdbf624b7f9c0
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 02/12/2022
ms.locfileid: "63583050"
---
# <a name="troubleshoot-installation-issues-for-microsoft-defender-for-endpoint-on-macos"></a>استكشاف مشاكل تثبيت Microsoft Defender ل Endpoint على macOS وإصلاحها

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**ينطبق على:**

- [Microsoft Defender ل Endpoint على macOS](microsoft-defender-endpoint-mac.md)
- [خطة Microsoft Defender لنقطة النهاية 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> هل تريد تجربة Microsoft Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

## <a name="installation-failed"></a>فشل التثبيت

بالنسبة إلى التثبيت اليدوي، تقول صفحة الملخص لمعالج التثبيت، "حدث خطأ أثناء التثبيت. واجه المثبت خطأ تسبب في فشل التثبيت. اتصل بناشر البرنامج للحصول على المساعدة." بالنسبة إلى عمليات نشر MDM، يتم عرضها كفشل عام في التثبيت أيضا.

على الرغم من أننا لا نعرض خطأ دقيقا للمستخدم، فإننا نحتفظ بملف سجل مع تقدم التثبيت في `/Library/Logs/Microsoft/mdatp/install.log`. يتم إلحاق كل جلسة عمل تثبيت إلى ملف السجل هذا. يمكنك استخدام إخراج `sed` جلسة التثبيت الأخيرة فقط:

```bash
sed -n 'H; /^preinstall com.microsoft.wdav begin/h; ${g;p;}' /Library/Logs/Microsoft/mdatp/install.log
```
```Output
preinstall com.microsoft.wdav begin [2020-03-11 13:08:49 -0700] 804
INSTALLER_SECURE_TEMP=/Library/InstallerSandboxes/.PKInstallSandboxManager/CB509765-70FC-4679-866D-8A14AD3F13CC.activeSandbox/89FA879B-971B-42BF-B4EA-7F5BB7CB5695
correlation id=CB509765-70FC-4679-866D-8A14AD3F13CC
[ERROR] Downgrade from 100.88.54 to 100.87.80 is not permitted
preinstall com.microsoft.wdav end [2020-03-11 13:08:49 -0700] 804 => 1
```

في هذا المثال، يكون السبب الفعلي مسبقا ب `[ERROR]`.
فشل التثبيت لأن عملية تخفيض الدرجات بين هذه الإصدارات غير معتمدة.

## <a name="mdatp-install-log-missing-or-not-updated"></a>سجل تثبيت MDATP مفقود أو غير محدث

في حالات نادرة، لا يترك التثبيت أي تتبع في ملف /Library/Logs/Microsoft/mdatp/install.log الخاص ب MDATP.
أولا، تحقق من حدوث عملية تثبيت. ثم قم بتحليل الأخطاء المحتملة عن طريق الاستعلام عن سجلات macOS. من المفيد القيام بذلك في عمليات نشر MDM، في حالة عدم وجود واجهة مستخدم للعميل. نوصي باستخدام نافذة زمنية ضيقة لتشغيل استعلام وتصفية حسب اسم عملية التسجيل، حيث سيكون هناك كمية كبيرة من المعلومات.

```bash
grep '^2020-03-11 13:08' /var/log/install.log
```
```Output
log show --start '2020-03-11 13:00:00' --end '2020-03-11 13:08:50' --info --debug --source --predicate 'processImagePath CONTAINS[C] "install"' --style syslog
```
