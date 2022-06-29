---
title: تشغيل محلل العميل على Windows
description: تعرف على كيفية تشغيل محلل عميل Microsoft Defender لنقطة النهاية على Windows.
keywords: محلل العميل، مستشعر استكشاف الأخطاء وإصلاحها، المحلل، mdeanalyzer، windows
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
ms.topic: conceptual
ms.technology: m365d
ms.openlocfilehash: 51eaa6ddcaf50a48ccbd8ffc000a79049c1d9842
ms.sourcegitcommit: d1b60ed9a11f5e6e35fbaf30ecaeb9dfd6dd197d
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 06/29/2022
ms.locfileid: "66489459"
---
# <a name="run-the-client-analyzer-on-windows"></a>تشغيل محلل العميل على Windows

**ينطبق على:**
- [Defender for Endpoint الخطة 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

1. قم بتنزيل [أداة MDE Client Analyzer](https://aka.ms/mdatpanalyzer) إلى جهاز Windows الذي تحتاج إلى التحقيق فيه.

2. استخراج محتويات MDEClientAnalyzer.zip على الجهاز.

3. فتح سطر أوامر غير مقيد:
    1. انتقل إلى **شاشة البدء** واكتب **cmd**.
    2. انقر بزر الماوس الأيمن فوق **موجه الأوامر** وحدد **"تشغيل كمسؤول**".

4. أدخل الأمر التالي واضغط على **مفتاح الإدخال Enter**:

   ```dos
   HardDrivePath\MDEClientAnalyzer.cmd
   ```

   **استبدل HardDrivePath بالمسار الذي تم استخراج الأداة إليه، على سبيل المثال:**

   ```dos
   C:\Work\tools\MDEClientAnalyzer\MDEClientAnalyzer.cmd
   ```

بالإضافة إلى ما سبق، هناك أيضا خيار [لجمع سجلات دعم المحلل باستخدام الاستجابة المباشرة.](troubleshoot-collect-support-log.md)

> [!NOTE]
> في Windows 10/11 أو Windows Server 2019/2022 أو Windows Server 2012R2/2016 مع تثبيت [الحل الموحد الحديث](configure-server-endpoints.md#new-windows-server-2012-r2-and-2016-functionality-in-the-modern-unified-solution)، يستدعي البرنامج النصي لمحلل العميل ملفا قابلا للتنفيذ يسمى `MDEClientAnalyzer.exe` لتشغيل اختبارات الاتصال إلى عناوين URL للخدمة السحابية.
>
> في Windows 8.1 أو Windows Server 2016 أو أي إصدار سابق من نظام التشغيل حيث يتم استخدام عامل مراقبة Microsoft (MMA) للإلحاق، يستدعي البرنامج النصي لمحلل العميل ملفا قابلا للتنفيذ يسمى `MDEClientAnalyzerPreviousVersion.exe` لتشغيل اختبارات الاتصال لعناوين URL للأوامر والتحكم (CnC) مع الاتصال أيضا بأداة `TestCloudConnection.exe` اتصال Microsoft Monitoring Agent لعناوين URL لقناة بيانات الإنترنت.


جميع البرامج النصية والوحدات النمطية PowerShell المضمنة مع المحلل موقعة من Microsoft.
إذا تم تعديل الملفات بأي طريقة، فمن المتوقع أن يخرج المحلل مع الخطأ التالي:

:::image type="content" source="images/sigerror.png" alt-text="خطأ محلل العميل" lightbox="images/sigerror.png":::


إذا ظهر هذا الخطأ، فسيحتوي إخراج issuerInfo.txt على معلومات مفصلة حول سبب حدوث ذلك والملف الذي تأثر:

:::image type="content" source="images/issuerinfo.png" alt-text="معلومات المصدر" lightbox="images/issuerinfo.png":::


محتويات المثال بعد تعديل MDEClientAnalyzer.ps1:

:::image type="content" source="images/modified-ps1.png" alt-text="ملف ps1 المعدل" lightbox="images/modified-ps1.png":::



## <a name="result-package-contents-on-windows"></a>محتويات حزمة النتائج على Windows

> [!NOTE]
> قد تتغير الملفات التي تم التقاطها بالضبط استنادا إلى عوامل مثل:
>
> - إصدار النوافذ التي يتم تشغيل المحلل عليها.
> - توفر قناة سجل الأحداث على الجهاز.
> - حالة بدء أداة استشعار EDR (يتم إيقاف أداة استشعار إذا لم يتم إلحاق الجهاز بعد).
> - إذا تم استخدام معلمة استكشاف الأخطاء وإصلاحها المتقدمة مع أمر المحلل.

بشكل افتراضي، سيحتوي ملف MDEClientAnalyzerResult.zip غير المحزم على العناصر التالية.

- MDEClientAnalyzer.htm

  هذا هو ملف إخراج HTML الرئيسي، والذي سيحتوي على النتائج والإرشادات التي يمكن أن ينتجها البرنامج النصي للمحلل على الجهاز.

- مجلد SystemInfoLogs \[\]
  - AddRemovePrograms.csv

    الوصف: قائمة البرامج المثبتة x64 على نظام التشغيل x64 التي تم جمعها من السجل.

  - AddRemoveProgramsWOW64.csv

    الوصف: قائمة البرامج المثبتة x86 على نظام التشغيل x64 التي تم جمعها من السجل.

    - CertValidate.log

      الوصف: نتيجة مفصلة من إبطال الشهادة المنفذة عن طريق الاتصال ب [CertUtil](/windows-server/administration/windows-commands/certutil).

    - dsregcmd.txt

      الوصف: الإخراج من تشغيل [dsregcmd](/azure/active-directory/devices/troubleshoot-device-dsregcmd). يوفر هذا تفاصيل حول حالة Azure AD للجهاز.

    - IFEO.txt

      الوصف: إخراج [خيارات تنفيذ ملف الصورة](/previous-versions/windows/desktop/xperf/image-file-execution-options) التي تم تكوينها على الجهاز

    - MDEClientAnalyzer.txt

      الوصف: هذا ملف نصي مطول يعرض تفاصيل تنفيذ البرنامج النصي للمحلل.

    - MDEClientAnalyzer.xml

      الوصف: تنسيق XML يحتوي على نتائج البرنامج النصي للمحلل.

    - RegOnboardedInfoCurrent.Json

      الوصف: معلومات الجهاز المدمج التي تم جمعها بتنسيق JSON من السجل.

  - RegOnboardingInfoPolicy.Json

    الوصف: تكوين نهج الإلحاق الذي تم جمعه بتنسيق JSON من السجل.

    - SCHANNEL.txt

      الوصف: تفاصيل حول [تكوين SCHANNEL](/windows-server/security/tls/manage-tls) المطبقة على الجهاز الذي تم جمعه من السجل.

    - SessionManager.txt

      الوصف: تجمع الإعدادات المحددة ل Session Manager من السجل.

    - SSL_00010002.txt

      الوصف: تفاصيل حول [تكوين SSL](/windows-server/security/tls/manage-tls) المطبقة على الجهاز الذي تم جمعه من السجل.

- EventLogs [Folder]

  - utc.evtx

    الوصف: تصدير سجل أحداث DiagTrack

  - senseIR.evtx

    الوصف: تصدير سجل أحداث التحقيق التلقائي

  - sense.evtx

    الوصف: تصدير سجل الأحداث الرئيسي لأداة الاستشعار

  - OperationsManager.evtx

    الوصف: تصدير سجل أحداث عامل مراقبة Microsoft




## <a name="see-also"></a>راجع أيضًا

- [نظرة عامة حول محلل العميل](overview-client-analyzer.md)
- [تنزيل محلل العميل وتشغيله](download-client-analyzer.md)
- [تجميع البيانات من أجل استكشاف الأخطاء وإصلاحها على Windows](data-collection-analyzer.md)
- [فهم تقرير HTML الخاص ب المحلل](analyzer-report.md)
