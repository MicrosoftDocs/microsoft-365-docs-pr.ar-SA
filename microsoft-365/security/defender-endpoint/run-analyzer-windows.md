---
title: تشغيل محلل العميل على Windows
description: تعرف على كيفية تشغيل Microsoft Defender لنقطة النهاية العميل على Windows.
keywords: محلل العميل، استكشاف الأخطاء وإصلاحها، محلل، mdeanalyzer، windows
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
ms.openlocfilehash: 5fa284f5c57214f356bb6b90e12ca60ae019d277
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/25/2022
ms.locfileid: "64467126"
---
# <a name="run-the-client-analyzer-on-windows"></a>تشغيل محلل العميل على Windows

**ينطبق على:**
- [Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

1. قم [بتنزيل أداة محلل عميل MDE](https://aka.ms/mdatpanalyzer) إلى Windows الذي تحتاج إلى التحقق منه.

2. استخراج محتويات MDEClientAnalyzer.zip على الجهاز.

3. فتح سطر أوامر مرتفع:
    1. انتقل إلى **ابدأ** وا اكتب **cmd**.
    2. انقر ب الماوس **الأيمن فوق موجه الأوامر** وحدد **تشغيل كمسؤول**.

4. أدخل الأمر التالي واضغط على **Enter**:

   ```dos
   HardDrivePath\MDEClientAnalyzer.cmd
   ```

   **استبدل HardDrivePath بالمسار الذي تم استخراج الأداة منه، على سبيل المثال:**

   ```dos
   C:\Work\tools\MDEClientAnalyzer\MDEClientAnalyzer.cmd
   ```

بالإضافة إلى ما ذكر أعلاه، هناك أيضا خيار لتجميع سجلات دعم المحلل [باستخدام الاستجابة المباشرة.](troubleshoot-collect-support-log.md).

> [!NOTE]
> في Windows 10/11 أو Windows Server 2019/2022 أو Windows Server 2012R2/2016 [](configure-server-endpoints.md#new-windows-server-2012-r2-and-2016-functionality-in-the-modern-unified-solution-preview) `MDEClientAnalyzer.exe` مع تثبيت الحل الموحد الحديث، يستدعي البرنامج النصي لمحلل العميل ملفا قابلا للتنفيذ لتشغيل اختبارات الاتصال إلى عناوين URL للخدمة السحابية.
>
> في Windows 8.1 أو Windows Server 2016 أو أي إصدار سابق من نظام التشغيل يستخدم فيه Microsoft Monitoring Agent (MMA) `MDEClientAnalyzerPreviousVersion.exe` للتكميل، يستدعي البرنامج النصي لمحلل العميل ملفا قابلا للتنفيذ يسمى لتشغيل اختبارات الاتصال الخاصة عناوين URL الخاصة ب Command and Control (CnC) أثناء الاتصال أيضا في أداة اتصال وكيل مراقبة Microsoft `TestCloudConnection.exe` عناوين URL الخاصة قناة بيانات الإنترنت.


تم توقيع Microsoft على كل البرامج النصية والوحدات النمطية في PowerShell المضمنة مع المحلل.
إذا تم تعديل الملفات بأي طريقة، فمن المتوقع أن يخرج المحلل بالخطأ التالي:

:::image type="content" source="images/sigerror.png" alt-text="خطأ محلل العميل" lightbox="images/sigerror.png":::


إذا تم عرض هذا الخطأ، فإن issuerInfo.txt سيحتوي على معلومات مفصلة حول سبب حدوث ذلك والملف الذي تأثر به:

:::image type="content" source="images/issuerinfo.png" alt-text="معلومات مصدر" lightbox="images/issuerinfo.png":::


مثال للمحتويات بعد MDEClientAnalyzer.ps1 تعديل:

:::image type="content" source="images/modified-ps1.png" alt-text="ملف ps1 المعدل" lightbox="images/modified-ps1.png":::



## <a name="result-package-contents-on-windows"></a>محتويات حزمة النتائج على Windows

> [!NOTE]
> قد تتغير الملفات الدقيقة التي تم التقاطها استنادا إلى عوامل مثل:
>
> - إصدار النوافذ التي يتم تشغيل المحلل عليها.
> - توفر قناة سجل الأحداث على الجهاز.
> - حالة بدء مستشعر الكشف التلقائي والاستجابة على النقط النهائية (يتم إيقاف استشعار إذا لم يتم تشغيل الجهاز بعد).
> - إذا تم استخدام معلمة استكشاف الأخطاء وإصلاحها المتقدمة مع أمر المحلل.

بشكل افتراضي، سيحتوي الملف MDEClientAnalyzerResult.zip الذي تم فك حزمه على العناصر التالية.

- MDEClientAnalyzer.htm

  هذا هو ملف إخراج HTML الرئيسي، الذي سيحتوي على النتائج والإرشادات التي يمكن أن ينتجها البرنامج النصي للمحلل على الجهاز.

- SystemInfoLogs \[Folder\]
  - AddRemovePrograms.csv

    الوصف: قائمة البرامج المثبتة على x86 على برامج نظام التشغيل x64 التي تم تجميعها من السجل.

  - AddRemoveProgramsWOW64.csv

    الوصف: قائمة البرامج المثبتة على x86 على برامج نظام التشغيل x64 التي تم تجميعها من السجل.

    - CertValidate.log

      الوصف: نتيجة تفصيلية من إلغاء الشهادة التي تم تنفيذها عن طريق الاتصال ب [CertUtil](/windows-server/administration/windows-commands/certutil).

    - dsregcmd.txt

      الوصف: الإخراج من تشغيل [dsregcmd](/azure/active-directory/devices/troubleshoot-device-dsregcmd). يوفر ذلك تفاصيل حول حالة Azure AD للجهاز.

    - IFEO.txt

      الوصف: إخراج خيارات [تنفيذ ملف الصورة](/previous-versions/windows/desktop/xperf/image-file-execution-options) التي تم تكوينها على الجهاز

    - MDEClientAnalyzer.txt

      الوصف: هذا هو ملف نصي مطو يعرض تفاصيل تنفيذ البرنامج النصي للمحلل.

    - MDEClientAnalyzer.xml

      الوصف: تنسيق XML الذي يحتوي على نتائج البرنامج النصي للمحلل.

    - RegOnboardedInfoCurrent.Json

      الوصف: معلومات الجهاز التي تم جمعها بتنسيق JSON من السجل.

  - RegOnboardingInfoPolicy.Json

    الوصف: تكوين نهج التهيئة الذي تم جمعه بتنسيق JSON من السجل.

    - SCHANNEL.txt

      الوصف: تفاصيل حول [تكوين SCHANNEL](/windows-server/security/tls/manage-tls) المطبق على الجهاز الذي تم جمعه من السجل.

    - SessionManager.txt

      الوصف: يتم جمع الإعدادات الخاصة ب "إدارة جلسات العمل" من السجل.

    - SSL_00010002.txt

      الوصف: تفاصيل حول [تكوين SSL](/windows-server/security/tls/manage-tls) المطبق على الجهاز الذي تم جمعه من السجل.

- EventLogs [Folder]

  - utc.evtx

    الوصف: تصدير سجل أحداث DiagTrack

  - senseIR.evtx

    الوصف: تصدير سجل أحداث "التحقيق التلقائي"

  - sense.evtx

    الوصف: تصدير سجل أحداث المستشعر الرئيسي

  - OperationsManager.evtx

    الوصف: تصدير سجل أحداث Microsoft Monitoring Agent




## <a name="see-also"></a>راجع أيضًا

- [نظرة عامة حول محلل العميل](overview-client-analyzer.md)
- [تنزيل محلل العميل وتشغيله](download-client-analyzer.md)
- [تجميع البيانات من أجل استكشاف الأخطاء وإصلاحها على Windows](data-collection-analyzer.md)
- [فهم تقرير HTML الخاص ب المحلل](analyzer-report.md)
