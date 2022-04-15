---
title: إلحاق الأجهزة Microsoft Defender for Business
description: تعرف على خيارات إلحاق الجهاز في Microsoft Defender for Business
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: overview
ms.date: 04/14/2022
ms.prod: m365-security
ms.technology: mdb
ms.localizationpriority: medium
ms.reviewer: inbadian, shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
- m365-initiative-defender-business
ms.openlocfilehash: ba816430521db2848273a4f7c6ca7d1a61703690
ms.sourcegitcommit: e3bc6563037bd2cce2abf108b3d1bcc2ccf538f6
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/15/2022
ms.locfileid: "64862248"
---
# <a name="onboard-devices-to-microsoft-defender-for-business"></a>إلحاق الأجهزة Microsoft Defender for Business

> [!NOTE]
> تم تضمين Microsoft Defender for Business الآن في [Microsoft 365 Business Premium](../../business-premium/index.md). 

باستخدام Microsoft Defender for Business، لديك العديد من الخيارات للاختيار من بينها لإلحاق أجهزة شركتك. ترشدك هذه المقالة عبر خياراتك وتتضمن نظرة عامة حول كيفية عمل الإلحاق.

>
> **هل لديك دقيقة؟**
> يرجى أخذ <a href="https://microsoft.qualtrics.com/jfe/form/SV_0JPjTPHGEWTQr4y" target="_blank">استطلاعنا القصير حول الأمان</a>. يسعدنا أن نستمع إليك!
>

## <a name="what-to-do"></a>ما يجب فعله

1. حدد علامة التبويب لنظام التشغيل: 

   - عملاء Windows
   - خادم Windows (معاينة)
   - أجهزة كمبيوتر macOS
   - الأجهزة المحمولة

2. اعرض خيارات الإلحاق واتبع الإرشادات الموجودة في علامة التبويب المحددة.

3. تابع إلى خطواتك التالية.

## <a name="windows-clients"></a>[**عملاء Windows**](#tab/WindowsClientDevices)

## <a name="windows-clients"></a>عملاء Windows

اختر أحد الخيارات التالية لإلحاق أجهزة العميل Windows إلى Defender for Business:

- [البرنامج النصي المحلي](#local-script-for-windows-clients) (لإعداد الأجهزة يدويا في مدخل Microsoft 365 Defender)
- [إدارة نقاط النهاية من Microsoft](#endpoint-manager-for-windows-clients) (مضمن في [Microsoft 365 Business Premium](../../business-premium/index.md))


### <a name="local-script-for-windows-clients"></a>البرنامج النصي المحلي لعملاء Windows

يمكنك استخدام برنامج نصي محلي لإلحاق أجهزة العميل Windows. عند تشغيل البرنامج النصي للإلحاق على جهاز، فإنه ينشئ ثقة مع Azure Active Directory (إذا لم تكن هذه الثقة موجودة بالفعل)، ويسجل الجهاز في إدارة نقاط النهاية من Microsoft (إذا لم يكن مسجلا بالفعل)، ثم يقوم بإلحاق الجهاز ب Defender for Business. يعمل أسلوب البرنامج النصي المحلي حتى إذا لم يكن لديك حاليا إدارة نقاط النهاية (أو Microsoft Intune). نوصي بإلحاق ما يصل إلى 10 أجهزة في كل مرة باستخدام هذا الأسلوب.

> [!TIP]
> نوصي بإعداد ما يصل إلى 10 أجهزة في وقت تستخدم فيه أسلوب البرنامج النصي المحلي.

1. انتقل إلى مدخل Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com))، وسجل الدخول.

2. في جزء التنقل، اختر **الإعدادات** >  **Endpoints**، ثم ضمن **إدارة الجهاز**، اختر **"إلحاق".**

3. حدد نظام تشغيل، مثل **Windows 10 و11**، ثم في قسم **أسلوب النشر**، اختر **البرنامج النصي المحلي**. 

4. حدد **تنزيل حزمة الإلحاق**. نوصي بحفظ حزمة الإلحاق إلى محرك أقراص قابل للإزالة.

5. على جهاز Windows، قم باستخراج محتويات حزمة التكوين إلى موقع، مثل مجلد سطح المكتب. يجب أن يكون لديك ملف باسم `WindowsDefenderATPLocalOnboardingScript.cmd`. 

6. افتح موجه الأوامر كمسؤول.

7. اكتب موقع ملف البرنامج النصي. على سبيل المثال، إذا قمت بنسخ الملف إلى مجلد سطح المكتب، فستكتب `%userprofile%\Desktop\WindowsDefenderATPLocalOnboardingScript.cmd`، ثم اضغط على مفتاح الإدخال Enter (أو حدد **"موافق**").

8. بعد تشغيل البرنامج النصي، تابع [إلى تشغيل اختبار الكشف](#running-a-detection-test-on-a-windows-client).

### <a name="endpoint-manager-for-windows-clients"></a>إدارة نقاط النهاية لعملاء Windows

إذا كان اشتراكك يتضمن [إدارة نقاط النهاية من Microsoft](/mem/endpoint-manager-overview)، يمكنك إلحاق العملاء Windows والأجهزة الأخرى في مركز إدارة إدارة نقاط النهاية من Microsoft ([https://endpoint.microsoft.com](https://endpoint.microsoft.com)). على سبيل المثال، إذا كان لديك [Microsoft 365 Business Premium](../../business/index.yml)، فلديك إدارة نقاط النهاية كجزء من اشتراكك. تتضمن إدارة نقاط النهاية [قدرات Microsoft Intune](/mem/intune/fundamentals/what-is-intune) و [Mobile إدارة الجهاز](/mem/intune/fundamentals/what-is-device-management). 

هناك العديد من الأساليب المتاحة لتسجيل الأجهزة في Intune. نوصي بالبدء بأحد الأساليب التالية:

- [تمكين التسجيل التلقائي Windows](/mem/intune/enrollment/windows-enroll) للأجهزة المملوكة للشركة أو التي تديرها الشركة
- [اطلب من المستخدمين تسجيل أجهزة Windows 10/11 الخاصة بهم في Intune](/mem/intune/user-help/enroll-windows-10-device)

#### <a name="to-enable-automatic-enrollment-for-windows-devices"></a>لتمكين التسجيل التلقائي للأجهزة Windows

عند إعداد التسجيل التلقائي، يضيف المستخدمون حساب العمل الخاص بهم إلى الجهاز. في الخلفية، يسجل الجهاز وينضم إلى Azure Active Directory (Azure AD)، ويتم تسجيله في Intune.

1. انتقل إلى مدخل Azure ([https://portal.azure.com/](https://portal.azure.com/)) وسجل الدخول. 

2. حدد **Azure Active DirectoryMobility** >  **(MDM وMAM)** > **Microsoft Intune**.

3. تكوين نطاق مستخدم MDM ونطاق مستخدم MAM.

   :::image type="content" source="media/mem-mam-scope-azure-ad.png" alt-text="لقطة شاشة لإعداد نطاق مستخدم MDM ونطاق مستخدم MAM في Intune.":::

   - بالنسبة إلى نطاق مستخدم MDM، نوصي بتحديد **الكل** حتى يتمكن جميع المستخدمين من تسجيل أجهزتهم Windows تلقائيا.
   - في قسم نطاق مستخدم MAM، نوصي باستخدام القيم الافتراضية التالية لعناوين URL:

       - **عنوان URL لشروط استخدام MDM**
       - **عنوان URL لاكتشاف MDM**
       - **عنوان URL لتوافق MDM**

4. اختر **"حفظ**".

5. بعد تسجيل جهاز في Intune، يمكنك إضافته إلى مجموعة أجهزة. [تعرف على المزيد حول مجموعات الأجهزة في Microsoft Defender for Business](mdb-create-edit-device-groups.md).


> [!TIP]
> لمعرفة المزيد حول التسجيل التلقائي، راجع [تمكين التسجيل التلقائي Windows](/mem/intune/enrollment/windows-enroll).

#### <a name="to-have-users-enroll-their-own-windows-devices"></a>لجعل المستخدمين يسجلون أجهزة Windows الخاصة بهم

1. شاهد الفيديو التالي لمعرفة كيفية عمل التسجيل: <br/><br/>

   > [!VIDEO https://www.youtube.com/embed/TKQxEckBHiE?rel=0]  

2. شارك هذه المقالة مع المستخدمين في مؤسستك: [تسجيل أجهزة Windows 10/11 في Intune](/mem/intune/user-help/enroll-windows-10-device).

3. بعد تسجيل جهاز في Intune، يمكنك إضافته إلى مجموعة أجهزة. [تعرف على المزيد حول مجموعات الأجهزة في Microsoft Defender for Business](mdb-create-edit-device-groups.md).

### <a name="running-a-detection-test-on-a-windows-client"></a>تشغيل اختبار الكشف على عميل Windows

بعد إلحاق أجهزة Windows ب Defender for Business، يمكنك تشغيل اختبار الكشف على جهاز Windows للتأكد من أن كل شيء يعمل بشكل صحيح.

1. على جهاز Windows، أنشئ مجلدا: `C:\test-MDATP-test`.

2. افتح موجه الأوامر كمسؤول.

3. في نافذة موجه الأوامر، قم بتشغيل أمر PowerShell التالي:

   ```powershell
   powershell.exe -NoExit -ExecutionPolicy Bypass -WindowStyle Hidden $ErrorActionPreference = 'silentlycontinue';(New-Object System.Net.WebClient).DownloadFile('http://127.0.0.1/1.exe', 'C:\\test-MDATP-test\\invoice.exe');Start-Process 'C:\\test-MDATP-test\\invoice.exe'
   ```

بعد تشغيل الأمر، سيتم إغلاق نافذة موجه الأوامر تلقائيا. إذا نجحت، سيتم وضع علامة على اختبار الكشف كمكتمل، وسيظهر تنبيه جديد في مدخل Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)) للجهاز الذي تم إلحاقه حديثا في حوالي 10 دقائق.

## <a name="view-a-list-of-onboarded-devices"></a>عرض قائمة بالأجهزة التي تم إلحاقها

لعرض قائمة الأجهزة التي تم إلحاقها ب Defender for Business، في مدخل Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com))، في جزء التنقل، ضمن **نقاط النهاية**، اختر **Device invetory**.

## <a name="next-steps"></a>الخطوات التالية

- إذا كان لديك أجهزة أخرى لإلحاقها، فحدد علامة التبويب التي تتوافق مع نظام التشغيل على الأجهزة [(Windows العملاء أو Windows Server أو macOS أو الأجهزة المحمولة](#what-to-do))، واتبع الإرشادات الواردة في علامة التبويب هذه.
- إذا انتهيت من إلحاق الأجهزة، فانضم إلى [الخطوة 5: تكوين إعدادات الأمان والنهج في Microsoft Defender for Business](mdb-configure-security-settings.md)
- راجع [بدء استخدام Microsoft Defender for Business](mdb-get-started.md).

## <a name="windows-server"></a>[**Windows Server**](#tab/WindowsServerEndpoints)

## <a name="windows-server-preview"></a>خادم Windows (معاينة)

يمكنك إلحاق جهاز خادم Windows باستخدام برنامج نصي محلي. 

> [!IMPORTANT]
> القدرة على إلحاق نقاط نهاية الخادم Windows قيد المعاينة حاليا.

1. انتقل إلى مدخل Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com))، وسجل الدخول.

2. في جزء التنقل، اختر **الإعدادات** >  **Endpoints**، ثم ضمن **إدارة الجهاز**، اختر **"إلحاق".**

3. حدد نظام تشغيل، مثل **Windows Server 1803 و2019 و2022**، ثم في قسم **أسلوب النشر**، اختر **البرنامج النصي المحلي**. 

   إذا حددت **Windows Server 2012 R2 و2016**، فستتوفر لديك حزمتان لتنزيلهما وتشغيلهما: حزمة تثبيت وحزمة إلحاق. تحتوي حزمة التثبيت على ملف MSI يقوم بتثبيت عامل Microsoft Defender for Business. تحتوي حزمة الإلحاق على البرنامج النصي لإلحاق نقطة نهاية خادم Windows إلى Defender for Business. 

4. حدد **تنزيل حزمة الإلحاق**. نوصي بحفظ حزمة الإلحاق إلى محرك أقراص قابل للإزالة.

   إذا قمت بتحديد **Windows Server 2012 R2 و2016**، فحدد أيضا **تنزيل حزمة التثبيت**، واحفظها في محرك أقراص قابل للإزالة

5. في نقطة نهاية Windows Server، قم باستخراج محتويات حزمة (حزم) التثبيت/الإلحاق إلى موقع، مثل مجلد سطح المكتب. يجب أن يكون لديك ملف باسم `WindowsDefenderATPLocalOnboardingScript.cmd`. 

   إذا كنت تقوم بإلحاق Windows Server 2012 R2 أو Windows Server 2016، فقم باستخراج حزمة التثبيت أولا.

6. افتح موجه الأوامر كمسؤول.

7. إذا كنت تقوم بإلحاق Windows Server 2012R2 أو Windows Server 2016، فقم بتشغيل الأمر التالي: `Msiexec /i md4ws.msi /quiet`. 

   إذا كنت تقوم بإلحاق Windows Server 1803 أو 2019 أو 2022، فتخطى هذه الخطوة وانتقل إلى الخطوة 8.

8. اكتب موقع ملف البرنامج النصي. على سبيل المثال، إذا قمت بنسخ الملف إلى مجلد سطح المكتب، فستكتب `%userprofile%\Desktop\WindowsDefenderATPLocalOnboardingScript.cmd`، ثم اضغط على مفتاح الإدخال Enter (أو حدد **"موافق**").

9. المتابعة [إلى تشغيل اختبار الكشف على Windows Server](#running-a-detection-test-on-windows-server)

### <a name="running-a-detection-test-on-windows-server"></a>تشغيل اختبار الكشف على Windows Server

بعد إلحاق نقطة نهاية Windows Server ب Defender for Business، يمكنك تشغيل اختبار الكشف للتأكد من أن كل شيء يعمل بشكل صحيح.

1. على جهاز Windows Server، أنشئ مجلدا: `C:\test-MDATP-test`.

2. افتح موجه الأوامر كمسؤول.

3. في نافذة موجه الأوامر، قم بتشغيل أمر PowerShell التالي:

   ```powershell
   powershell.exe -NoExit -ExecutionPolicy Bypass -WindowStyle Hidden $ErrorActionPreference = 'silentlycontinue';(New-Object System.Net.WebClient).DownloadFile('http://127.0.0.1/1.exe', 'C:\\test-MDATP-test\\invoice.exe');Start-Process 'C:\\test-MDATP-test\\invoice.exe'
   ```

بعد تشغيل الأمر، سيتم إغلاق نافذة موجه الأوامر تلقائيا. إذا نجحت، سيتم وضع علامة على اختبار الكشف كمكتمل، وسيظهر تنبيه جديد في مدخل Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)) للجهاز الذي تم إلحاقه حديثا في حوالي 10 دقائق.

## <a name="view-a-list-of-onboarded-devices"></a>عرض قائمة بالأجهزة التي تم إلحاقها

لعرض قائمة الأجهزة التي تم إلحاقها ب Defender for Business، في مدخل Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com))، في جزء التنقل، ضمن **نقاط النهاية**، اختر **Device invetory**.

## <a name="next-steps"></a>الخطوات التالية

- إذا كان لديك أجهزة أخرى لإلحاقها، فحدد علامة التبويب التي تتوافق مع نظام التشغيل على الأجهزة [(Windows العملاء أو Windows Server أو macOS أو الأجهزة المحمولة](#what-to-do))، واتبع الإرشادات الواردة في علامة التبويب هذه.
- إذا انتهيت من إلحاق الأجهزة، فانضم إلى [الخطوة 5: تكوين إعدادات الأمان والنهج في Microsoft Defender for Business](mdb-configure-security-settings.md)
- راجع [بدء استخدام Microsoft Defender for Business](mdb-get-started.md).

## <a name="macos"></a>[**ماك**](#tab/macOSdevices)

## <a name="macos-computers"></a>أجهزة كمبيوتر macOS

> [!NOTE]
> - نوصي باستخدام [برنامج نصي محلي لإلحاق أجهزة macOS](#local-script-for-macos). على الرغم من أنه يمكنك [إعداد التسجيل لأجهزة macOS في Intune](/mem/intune/enrollment/macos-enroll)، فإن البرنامج النصي المحلي هو أبسط طريقة لإلحاق أجهزة macOS ب Defender for Business. 

اختر أحد الخيارات التالية لإلحاق أجهزة macOS:

- [البرنامج النصي المحلي لنظام التشغيل macOS](#local-script-for-macos) (*مستحسن*)
- [إدارة نقاط النهاية لنظام التشغيل macOS](#endpoint-manager-for-macos)

### <a name="local-script-for-macos"></a>البرنامج النصي المحلي لنظام التشغيل macOS

عند تشغيل البرنامج النصي المحلي على جهاز macOS، فإنه ينشئ ثقة مع Azure Active Directory (إذا لم تكن هذه الثقة موجودة بالفعل)، ويسجل الجهاز في إدارة نقاط النهاية من Microsoft (إذا لم يكن مسجلا بالفعل)، ثم يقوم بإلحاق الجهاز ب Defender for Business. يعمل أسلوب البرنامج النصي المحلي حتى إذا لم يكن لديك حاليا إدارة نقاط النهاية (أو Microsoft Intune). نوصي بإلحاق ما يصل إلى 10 أجهزة في كل مرة باستخدام هذا الأسلوب.

1. انتقل إلى مدخل Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com))، وسجل الدخول.

2. في جزء التنقل، اختر **الإعدادات** >  **Endpoints**، ثم ضمن **إدارة الجهاز**، اختر **"إلحاق".**

3. حدد **macOS**، ثم في قسم **أسلوب النشر** ، اختر **البرنامج النصي المحلي**. 

4. حدد **"تنزيل حزمة الإلحاق**"، واحفظها في محرك أقراص قابل للإزالة. حدد أيضا **تنزيل حزمة التثبيت**، واحفظها على جهازك القابل للإزالة.

5. على جهاز macOS، احفظ حزمة التثبيت في `wdav.pkg` دليل محلي.

6. احفظ حزمة `WindowsDefenderATPOnboardingPackage.zip` الإلحاق بنفس الدليل الذي استخدمته لحزمة التثبيت.

7. استخدم "الباحث" للانتقال إليك `wdav.pkg` بعد حفظه، ثم افتحه.

8. حدد **"متابعة**"، وتوافق على شروط الترخيص، ثم أدخل كلمة المرور عند المطالبة.

9. ستتم مطالبتك بالسماح بتثبيت برنامج تشغيل من Microsoft (إما "تم حظر ملحق النظام" أو "التثبيت قيد الانتظار"، أو كليهما. يجب السماح بتثبيت برنامج التشغيل. للسماح بالتثبيت، حدد **"فتح تفضيلات الأمان**" أو **"فتح تفضيلات** >  النظام **" & الخصوصية**، ثم حدد **"السماح**".

10. استخدم أمر Python التالي في Bash لتشغيل حزمة الإلحاق: `/usr/bin/python MicrosoftDefenderATPOnboardingMacOs.py`

11. بعد تسجيل جهاز في Intune، يمكنك إضافته إلى مجموعة أجهزة. [تعرف على المزيد حول مجموعات الأجهزة في Microsoft Defender for Business](mdb-create-edit-device-groups.md).

### <a name="endpoint-manager-for-macos"></a>إدارة نقاط النهاية لنظام التشغيل macOS

إذا كان اشتراكك يتضمن [إدارة نقاط النهاية من Microsoft](/mem/endpoint-manager-overview)، يمكنك إلحاق أجهزة macOS في مركز إدارة إدارة نقاط النهاية من Microsoft ([https://endpoint.microsoft.com](https://endpoint.microsoft.com)). على سبيل المثال، إذا كان لديك [Microsoft 365 Business Premium](../../business/index.yml)، فلديك إدارة نقاط النهاية كجزء من اشتراكك. تتضمن إدارة نقاط النهاية [قدرات Microsoft Intune](/mem/intune/fundamentals/what-is-intune) و [Mobile إدارة الجهاز](/mem/intune/fundamentals/what-is-device-management). 

هناك العديد من الأساليب المتاحة لتسجيل الأجهزة في Intune. نوصي بالبدء بأحد الأساليب التالية:

- [اختيار خيار لأجهزة macOS المملوكة للشركة](#options-for-company-owned-macos-devices)
- [اطلب من المستخدمين تسجيل أجهزة macOS الخاصة بهم في Intune](#ask-users-to-enroll-their-own-macos-devices-in-intune)

#### <a name="options-for-company-owned-macos-devices"></a>خيارات لأجهزة macOS المملوكة للشركة

اختر أحد الخيارات في الجدول التالي لتسجيل أجهزة macOS التي تديرها الشركة في Intune:

| الخيار  | الوصف  |
|---------|---------|
| تسجيل جهاز Apple التلقائي |  استخدم هذه الطريقة لأتمتة تجربة التسجيل على الأجهزة التي تم شراؤها من خلال Apple Business Manager أو Apple School Manager. ينشر تسجيل الجهاز التلقائي ملف تعريف التسجيل عبر الهواء، لذلك لا تحتاج إلى الوصول الفعلي إلى الأجهزة. <br/><br/>اطلع [على تسجيل أجهزة macOS تلقائيا باستخدام Apple Business Manager أو Apple School Manager](/mem/intune/enrollment/device-enrollment-program-enroll-macos). |
| إدارة تسجيل الأجهزة (DEM)  |  استخدم هذا الأسلوب لعمليات النشر واسعة النطاق وعندما يكون هناك عدة أشخاص في مؤسستك يمكنهم المساعدة في إعداد التسجيل. يمكن لشخص ما له أذونات مدير تسجيل الأجهزة (DEM) تسجيل ما يصل إلى 1000 جهاز باستخدام حساب Azure Active Directory واحد. يستخدم هذا الأسلوب تطبيق Company Portal أو تطبيق Microsoft Intune لتسجيل الأجهزة. لا يمكنك استخدام حساب DEM لتسجيل الأجهزة عبر تسجيل الجهاز التلقائي.<br/><br/> راجع [تسجيل الأجهزة في Intune باستخدام حساب إدارة تسجيل الأجهزة](/mem/intune/enrollment/device-enrollment-manager-enroll).  |
| التسجيل المباشر  | تسجيل مباشر يسجل الأجهزة دون ترابط المستخدم، لذلك هذا الأسلوب هو الأفضل للأجهزة غير المرتبطة بمستخدم واحد. يتطلب منك هذا الأسلوب الوصول الفعلي إلى أجهزة Mac التي تقوم بتسجيلها. <br/><br/>راجع [استخدام التسجيل المباشر لأجهزة macOS](/mem/intune/enrollment/device-enrollment-direct-enroll-macos).      |

#### <a name="ask-users-to-enroll-their-own-macos-devices-in-intune"></a>اطلب من المستخدمين تسجيل أجهزة macOS الخاصة بهم في Intune

إذا كانت شركتك تفضل أن يقوم الأشخاص بتسجيل أجهزتهم الخاصة في Intune، فاطلب من المستخدمين اتباع الخطوات التالية:

1. انتقل إلى موقع ويب Company Portal ([https://portal.manage.microsoft.com/](https://portal.manage.microsoft.com/)) وسجل الدخول.

2. اتبع الإرشادات الموجودة على موقع ويب Company Portal لإضافة جهازه.

3. قم بتثبيت تطبيق Company Portal في [https://aka.ms/EnrollMyMac](https://aka.ms/EnrollMyMac)، واتبع الإرشادات الموجودة في التطبيق.

### <a name="confirm-that-a-macos-device-is-onboarded"></a>تأكد من إلحاق جهاز macOS

1. للتأكد من أن الجهاز مقترن بشركتك، استخدم أمر Python التالي في Bash: `mdatp health --field org_id`.

2. إذا كنت تستخدم macOS 10.15 (Catalina) أو إصدار أحدث، فامنح Defender for Business موافقة لحماية جهازك. انتقل إلى **System PreferencesSecurity** >  **&** **PrivacyPrivacyFull** >  >  **Disk Access**. حدد أيقونة التأمين لإجراء تغييرات (أسفل مربع الحوار)، ثم حدد **Microsoft Defender for Business** (أو **Defender لنقطة النهاية**، إذا كان هذا ما تراه).

3. للتحقق من أن الجهاز تم إلحاقه، استخدم الأمر التالي في Bash: `mdatp health --field real_time_protection_enabled`

4. بعد تسجيل جهاز في Intune، يمكنك إضافته إلى مجموعة أجهزة. [تعرف على المزيد حول مجموعات الأجهزة في Microsoft Defender for Business](mdb-create-edit-device-groups.md).

## <a name="view-a-list-of-onboarded-devices"></a>عرض قائمة بالأجهزة التي تم إلحاقها

لعرض قائمة الأجهزة التي تم إلحاقها ب Defender for Business، في مدخل Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com))، في جزء التنقل، ضمن **نقاط النهاية**، اختر **مخزون الجهاز**.

## <a name="next-steps"></a>الخطوات التالية

- إذا كان لديك أجهزة أخرى لإلحاقها، فحدد علامة التبويب التي تتوافق مع نظام التشغيل على الأجهزة ([Windows العملاء أو Windows Server أو macOS أو الأجهزة المحمولة](#what-to-do))، واتبع الإرشادات الواردة في علامة التبويب هذه.
- إذا انتهيت من إلحاق الأجهزة، فانضم إلى [الخطوة 5: تكوين إعدادات الأمان والنهج في Microsoft Defender for Business](mdb-configure-security-settings.md)
- راجع [بدء استخدام Microsoft Defender for Business](mdb-get-started.md).

## <a name="mobile-devices"></a>[**الأجهزة المحمولة**](#tab/mobiles)

## <a name="mobile-devices"></a>الأجهزة المحمولة

ستحتاج Microsoft Intune إلى إلحاق الأجهزة المحمولة، مثل أجهزة Android وiOS/iPadOS. إذا كان لديك [Microsoft 365 Business Premium](../../business/index.yml)، فلديك إدارة نقاط النهاية كجزء من اشتراكك. تتضمن إدارة نقاط النهاية [قدرات Microsoft Intune](/mem/intune/fundamentals/what-is-intune) و [Mobile إدارة الجهاز](/mem/intune/fundamentals/what-is-device-management). 

راجع الموارد التالية للحصول على المساعدة في تسجيل هذه الأجهزة في Intune:

- [تسجيل أجهزة Android](/mem/intune/enrollment/android-enroll)
- [تسجيل أجهزة iOS أو iPadOS](/mem/intune/enrollment/ios-enroll)

بعد تسجيل جهاز في Intune، يمكنك إضافته إلى مجموعة أجهزة. [تعرف على المزيد حول مجموعات الأجهزة في Microsoft Defender for Business](mdb-create-edit-device-groups.md).

## <a name="next-steps"></a>الخطوات التالية

- إذا كان لديك أجهزة أخرى لإلحاقها، فحدد علامة التبويب التي تتوافق مع نظام التشغيل على الأجهزة ([Windows العملاء أو Windows Server أو macOS أو الأجهزة المحمولة](#what-to-do))، واتبع الإرشادات الواردة في علامة التبويب هذه.
- إذا انتهيت من إلحاق الأجهزة، فانضم إلى [الخطوة 5: تكوين إعدادات الأمان والنهج في Microsoft Defender for Business](mdb-configure-security-settings.md)
- راجع [بدء استخدام Microsoft Defender for Business](mdb-get-started.md).
