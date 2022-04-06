---
title: تجميع البيانات التشخيصية برنامج الحماية من الفيروسات من Microsoft Defender
description: استخدم أداة لتجميع البيانات من أجل استكشاف الأخطاء وإصلاحها برنامج الحماية من الفيروسات من Microsoft Defender
keywords: استكشاف الأخطاء وإصلاحها وإصلاحها وتحديث التوافق وoms وشاشة العرض والتقارير و Microsoft Defender av، كائن نهج المجموعة، الإعداد، البيانات التشخيصية
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.date: 06/29/2020
ms.reviewer: ''
manager: dansimp
ms.technology: mde
ms.topic: article
ms.collection: M365-security-compliance
ms.openlocfilehash: 099bd5c458a863576c8030a86d6923065228e307
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/25/2022
ms.locfileid: "64470714"
---
# <a name="collect-microsoft-defender-antivirus-diagnostic-data"></a>تجميع برنامج الحماية من الفيروسات من Microsoft Defender التشخيصية

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**ينطبق على:**

- [Microsoft Defender لنقطة النهاية 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

تصف هذه المقالة كيفية تجميع البيانات التشخيصية التي يمكن استخدامها من قبل فرق الدعم والهندسة من Microsoft للمساعدة في استكشاف المشاكل التي قد تواجهها عند استخدام برنامج الحماية من الفيروسات من Microsoft Defender.

> [!NOTE]
> كجزء من عملية التحقيق أو الاستجابة، يمكنك تجميع حزمة تحقيق من جهاز. إليك كيفية إجراء ذلك: [تجميع حزمة التحقيق من الأجهزة](/windows/security/threat-protection/microsoft-defender-atp/respond-machine-alerts#collect-investigation-package-from-devices).

على جهازين على الأقل يواجهان المشكلة نفسها، احصل على .cab التشخيصي باتباع الخطوات التالية:

1. افتح إصدارا على مستوى المسؤول من موجه الأوامر كما يلي:

    أ. افتح قائمة **البدء** .

    ب. اكتب **cmd**. انقر ب زر الماوس الأيمن فوق **موجه الأوامر** ثم حدد **تشغيل كمسؤول**.

    c. حدد بيانات اعتماد المسؤول أو وافق على المطالبة.

2. انتقل إلى الدليل الخاص برنامج الحماية من الفيروسات من Microsoft Defender. بشكل افتراضي، هذا هو `C:\Program Files\Windows Defender`.

   > [!NOTE]
   > إذا كنت تقوم بتشغيل إصدار نظام أساسي محدث من [Microsoft Defender لمكافحة](https://support.microsoft.com/help/4052623/update-for-microsoft-defender-antimalware-platform) البرامج الضارة، فيرجى `MpCmdRun` التشغيل من الموقع التالي: `C:\ProgramData\Microsoft\Windows Defender\Platform\<version>`.

3. اكتب الأمر التالي، ثم اضغط على **Enter**

    ```Dos
    mpcmdrun.exe -GetFiles
    ```

4. سيتم .cab ملف يحتوي على سجلات تشخيص متنوعة. سيتم تحديد موقع الملف في الإخراج في موجه الأوامر. بشكل افتراضي، يكون الموقع هو `C:\ProgramData\Microsoft\Microsoft Defender\Support\MpSupportFiles.cab`.

   > [!NOTE]
   > لإعادة توجيه ملف cab إلى مسار آخر أو مشاركة UNC، استخدم الأمر التالي:
   >
   > `mpcmdrun.exe -GetFiles -SupportLogLocation <path>`
   >
   > لمزيد من المعلومات، راجع [إعادة توجيه البيانات التشخيصية إلى مشاركة UNC](#redirect-diagnostic-data-to-a-unc-share).

5. انسخ .cab الملفات إلى موقع يمكن الوصول إليه بواسطة دعم Microsoft. على سبيل المثال، قد يكون مجلد OneDrive محمي بكلمة مرور يمكنك مشاركته معنا.

> [!NOTE]
> إذا كانت لديك مشكلة في توافق التحديث، فارسل بريدا إلكترونيا باستخدام قالب البريد الإلكتروني لدعم دعم تحديث <a href="mailto:ucsupport@microsoft.com?subject=WDAV assessment issue&body=I%20am%20encountering%20the%20following%20issue%20when%20using%20Windows%20Defender%20AV%20in%20Update%20Compliance%3a%20%0d%0aI%20have%20provided%20at%20least%202%20support%20.cab%20files%20at%20the%20following%20location%3a%20%3Caccessible%20share%2c%20including%20access%20details%20such%20as%20password%3E%0d%0aMy%20OMS%20workspace%20ID%20is%3a%20%0d%0aPlease%20contact%20me%20at%3a">التوافق</a>، ثم قم بتعبئة القالب بالمعلومات التالية:
>
> أواجه المشكلة التالية عند استخدام برنامج الحماية من الفيروسات من Microsoft Defender في تحديث التوافق:
>
> لقد قدمت ملفي دعم .cab على الأقل في الموقع التالي:
>
> \<accessible share, including access details such as password\>
>
> إن "معرّف مساحة عمل OMS" الخاص ب OMS هو:
>
> يرجى الاتصال بي على:

## <a name="redirect-diagnostic-data-to-a-unc-share"></a>إعادة توجيه البيانات التشخيصية إلى مشاركة UNC

لتجميع البيانات التشخيصية في مستودع مركزي، يمكنك تحديد معلمة SupportLogLocation.

```Dos
mpcmdrun.exe -GetFiles -SupportLogLocation <path>
```

نسخ البيانات التشخيصية إلى المسار المحدد. إذا لم يتم تحديد المسار، سيتم نسخ البيانات التشخيصية إلى الموقع المحدد في تكوين موقع سجل الدعم.

عند استخدام معلمة SupportLogLocation، سيتم إنشاء بنية مجلد كما يلي في المسار الوجهة:

```Dos
<path>\<MMDD>\MpSupport-<hostname>-<HHMM>.cab
```

<br>

****

|حقل|الوصف|
|---|---|
|مسار|المسار كما هو محدد على سطر الأوامر أو الذي تم استرداده من التكوين|
|MMDD|اليوم والشهر الذي تم فيه تجميع البيانات التشخيصية (على سبيل المثال، 0530)|
|hostname|اسم مضيف الجهاز الذي تم تجميع البيانات التشخيصية عليه|
|HHMM|الساعات والدقائق التي تم فيها تجميع البيانات التشخيصية (على سبيل المثال، 1422)|
|

> [!NOTE]
> عند استخدام مشاركة ملف، يرجى التأكد من أن الحساب المستخدم لتجميع حزمة التشخيص لديه حق الوصول للكتابة إلى المشاركة.

## <a name="specify-location-where-diagnostic-data-is-created"></a>تحديد موقع إنشاء البيانات التشخيصية

يمكنك أيضا تحديد مكان إنشاء .cab التشخيصي باستخدام نهج المجموعة كائن (GPO).

1. افتح محرر نهج المجموعة واعثر على SupportLogLocation GPO في: `HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows Defender\SupportLogLocation`.

2. حدد **تعريف مسار الدليل لنسخ ملفات سجل الدعم**.

   :::image type="content" source="images/GPO1-SupportLogLocationDefender.png" alt-text="محرر نهج المجموعة المحلي" lightbox="images/GPO1-SupportLogLocationDefender.png":::

   :::image type="content" source="images/GPO2-SupportLogLocationGPPage.png" alt-text="مسار تعريف إعداد ملفات السجل" lightbox="images/GPO2-SupportLogLocationGPPage.png":::

   :::image type="content" source="images/GPO1-SupportLogLocationDefender.png" alt-text="محرر نهج المجموعة المحلي" lightbox="images/GPO1-SupportLogLocationDefender.png"::: 
        
   :::image type="content" source="images/GPO2-SupportLogLocationGPPage.png" alt-text="مسار التعريف لتكوين إعداد ملفات السجل" lightbox="images/GPO2-SupportLogLocationGPPage.png":::
 
3. داخل محرر النهج، حدد **تمكين**.

4. حدد مسار الدليل حيث تريد نسخ ملفات سجل الدعم في **الحقل خيارات** .
   :::image type="content" source="images/GPO3-SupportLogLocationGPPageEnabledExample.png" alt-text="الإعداد المخصص لمسار الدليل الذي تم تمكينه" lightbox="images/GPO3-SupportLogLocationGPPageEnabledExample.png":::
5. حدد **موافق** أو **تطبيق**.

## <a name="see-also"></a>راجع أيضًا

- [استكشاف الأخطاء برنامج الحماية من الفيروسات من Microsoft Defender التقارير وإصلاحها](troubleshoot-reporting.md)
