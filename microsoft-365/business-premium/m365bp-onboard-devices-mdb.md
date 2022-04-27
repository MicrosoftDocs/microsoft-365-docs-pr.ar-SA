---
title: إلحاق أجهزة مؤسستك Microsoft Defender for Business
description: إلحاق أجهزة مؤسستك Microsoft Defender for Business
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: overview
ms.date: 04/01/2022
ms.prod: m365-security
ms.technology: mdb
ms.localizationpriority: high
ms.reviewer: shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
ms.openlocfilehash: 774c23a4da7d368f46607fd588a07ffb01e92f53
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/27/2022
ms.locfileid: "65094186"
---
# <a name="onboard-enrolled-devices-to-microsoft-defender-for-business"></a>إلحاق الأجهزة المسجلة Microsoft Defender for Business

الآن بعد أن قمت بتسجيل الأجهزة، يجب عليك إلحاقها Microsoft Defender for Business لتنفيذ حماية الجيل التالي (الحماية من الفيروسات والحماية من البرامج الضارة والحماية المقدمة من السحابة) وحماية جدار الحماية وتصفية محتوى الويب والمزيد. 

لإلحاق الأجهزة، يمكنك الاختيار من بين عدة خيارات:

- [استخدام الإلحاق التلقائي للأجهزة Windows المسجلة بالفعل في إدارة نقاط النهاية من Microsoft](#use-automatic-onboarding-for-windows-devices-that-are-already-enrolled-in-microsoft-endpoint-manager)

- [استخدام برنامج نصي محلي لإلحاق أجهزة Windows وmacOS](#use-a-local-script-to-onboard-windows-and-macos-devices)

- [استخدم إدارة نقاط النهاية لتسجيل الأجهزة](#use-microsoft-endpoint-manager-to-enroll-devices) (Windows وmacOS وiOS وAndroid) ثم طبق نهج Defender for Business على تلك الأجهزة

تتضمن هذه المقالة أيضا:

- [كيفية تشغيل اختبار الكشف على جهاز Windows](#run-a-detection-test-on-a-windows-device)

- [كيفية إلحاق الأجهزة تدريجيا](#onboard-devices-gradually)

- [كيفية إيقاف تشغيل جهاز](#offboard-a-device) إذا تم استبدال جهاز أو إذا غادر شخص ما المؤسسة

> [!IMPORTANT]
> إذا حدث خطأ ما وفشلت عملية الإلحاق، فراجع [Microsoft Defender for Business استكشاف الأخطاء وإصلاحها](../security/defender-business/mdb-troubleshooting.yml).

## <a name="use-automatic-onboarding-for-windows-devices-that-are-already-enrolled-in-microsoft-endpoint-manager"></a>استخدام الإلحاق التلقائي للأجهزة Windows المسجلة بالفعل في إدارة نقاط النهاية من Microsoft

ينطبق خيار الإلحاق التلقائي على أجهزة Windows فقط. يتوفر الإلحاق التلقائي إذا تم استيفاء الشروط التالية:

- كانت مؤسستك تستخدم بالفعل إدارة نقاط النهاية من Microsoft أو Microsoft Intune أو إدارة الجهاز الأجهزة المحمولة (MDM) في Microsoft Intune قبل حصولك على Defender for Business (Microsoft 365 Business Premium  لدى العملاء بالفعل Microsoft Intune).

- لديك بالفعل أجهزة Windows مسجلة في إدارة نقاط النهاية.

إذا كانت أجهزة Windows مسجلة بالفعل في إدارة نقاط النهاية، يكتشف Defender for Business هذه الأجهزة أثناء عملية إعداد وتكوين Defender for Business. سيتم سؤالك عما إذا كنت تريد استخدام الإلحاق التلقائي لجميع أجهزة Windows أو بعضها. يمكنك إلحاق جميع الأجهزة Windows في وقت واحد، أو تحديد أجهزة معينة للبدء بها، ثم إضافة المزيد من الأجهزة لاحقا.

> [!TIP]
> نوصي بتحديد خيار "جميع الأجهزة المسجلة". وبهذه الطريقة، عندما يتم تسجيل أجهزة Windows في إدارة نقاط النهاية لاحقا، سيتم إلحاقها ب Defender for Business تلقائيا.
لمعرفة المزيد حول الإلحاق التلقائي، راجع الخطوة 2 في [استخدام المعالج لإعداد Microsoft Defender for Business](../security/defender-business/mdb-use-wizard.md).

## <a name="use-a-local-script-to-onboard-windows-and-macos-devices"></a>استخدام برنامج نصي محلي لإلحاق أجهزة Windows وmacOS

يمكنك استخدام برنامج نصي محلي لإلحاق أجهزة Windows وMac. عند تشغيل البرنامج النصي للإلحاق على جهاز، فإنه ينشئ ثقة مع Azure Active Directory (إذا لم تكن هذه الثقة موجودة بالفعل)، ويسجل الجهاز في إدارة نقاط النهاية من Microsoft (إذا لم يكن مسجلا بالفعل)، ثم يقوم بإلحاق الجهاز ب Defender for Business. هذا الأسلوب مفيد لإلحاق الأجهزة في Defender for Business. يمكنك إلحاق ما يصل إلى 10 أجهزة في كل مرة.

1. انتقل إلى مدخل Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com))، وسجل الدخول.

2. في جزء التنقل، اختر **الإعدادات** >  **Endpoints**، ثم ضمن **إدارة الجهاز**، اختر **"إلحاق".**

3. حدد نظام تشغيل، مثل **Windows 10 و11** أو **macOS**، ثم في قسم **أسلوب النشر**، اختر **البرنامج النصي المحلي**. 

4. حدد **تنزيل حزمة الإلحاق**. نوصي بحفظ حزمة الإلحاق إلى محرك أقراص قابل للإزالة. (إذا قمت بتحديد **macOS**، فحدد أيضا **تنزيل حزمة التثبيت** وحفظها على جهازك القابل للإزالة.)

5. استخدم الإرشادات التالية:

   - أجهزة Windows: [إلحاق أجهزة Windows باستخدام برنامج نصي محلي](../security/defender-endpoint/configure-endpoints-script.md#onboard-windows-devices-using-a-local-script)

   - أجهزة macOS: [النشر اليدوي Microsoft Defender لنقطة النهاية على macOS](../security/defender-endpoint/mac-install-manually.md#download-installation-and-onboarding-packages)

## <a name="use-microsoft-endpoint-manager-to-enroll-devices"></a>استخدام إدارة نقاط النهاية من Microsoft لتسجيل الأجهزة

لتسجيل جهاز، قم بتسجيله بنفسك، أو اطلب من المستخدمين تسجيل الدخول إلى مدخل الشركة وتسجيل أي تطبيقات مطلوبة وتثبيتها. 

إذا كنت تستخدم إدارة نقاط النهاية بالفعل (والتي تتضمن Microsoft Intune و Mobile إدارة الجهاز)، قبل حصولك على Defender for Business، يمكنك الاستمرار في استخدام إدارة نقاط النهاية لإلحاق أجهزة مؤسستك. باستخدام إدارة نقاط النهاية، يمكنك إلحاق أجهزة الكمبيوتر وأجهزة الكمبيوتر اللوحية والهواتف، بما في ذلك أجهزة iOS وAndroid.

راجع [تسجيل الجهاز في Microsoft Intune](/mem/intune/enrollment/device-enrollment). 

## <a name="run-a-detection-test-on-a-windows-device"></a>تشغيل اختبار الكشف على جهاز Windows

بعد إلحاق أجهزة Windows ب Defender for Business، يمكنك تشغيل اختبار الكشف على جهاز Windows للتأكد من أن كل شيء يعمل بشكل صحيح.

1. على جهاز Windows، أنشئ مجلدا: `C:\test-MDATP-test`.

2. افتح موجه الأوامر كمسؤول.

3. في نافذة موجه الأوامر، قم بتشغيل أمر PowerShell التالي:

   ```powershell
   powershell.exe -NoExit -ExecutionPolicy Bypass -WindowStyle Hidden $ErrorActionPreference = 'silentlycontinue';(New-Object System.Net.WebClient).DownloadFile('http://127.0.0.1/1.exe', 'C:\\test-MDATP-test\\invoice.exe');Start-Process 'C:\\test-MDATP-test\\invoice.exe'
   ```

بعد تشغيل الأمر، يتم إغلاق نافذة موجه الأوامر تلقائيا. إذا نجح، يتم وضع علامة على اختبار الكشف كمكتمل، ويظهر تنبيه جديد في مدخل Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)) للجهاز الذي تم إلحاقه حديثا في حوالي عشر دقائق.

## <a name="onboard-devices-gradually"></a>إلحاق الأجهزة تدريجيا

إذا كنت تفضل إلحاق الأجهزة على مراحل، والتي نطلق *عليها اسم الإعداد التدريجي للجهاز*، فاتبع الخطوات التالية: 

1. تحديد مجموعة من الأجهزة لإلحاقها.

2. انتقل إلى مدخل Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com))، وسجل الدخول.

3. في جزء التنقل، اختر **الإعدادات** >  **Endpoints**، ثم ضمن **إدارة الجهاز**، اختر **"إلحاق".**

4. حدد نظام تشغيل (مثل **Windows 10 و11)،** ثم اختر أسلوب إلحاق (مثل **البرنامج النصي المحلي**). اتبع الإرشادات المقدمة للأسلوب الذي حددته.

5. كرر هذه العملية لكل مجموعة من الأجهزة التي تريد إلحاقها. 

> [!TIP]
> لا يتعين عليك استخدام حزمة الإلحاق نفسها في كل مرة تقوم فيها بإلحاق الأجهزة. على سبيل المثال، يمكنك استخدام برنامج نصي محلي لإلحاق بعض الأجهزة، وفي وقت لاحق، يمكنك اختيار طريقة أخرى لإلحاق المزيد من الأجهزة.

## <a name="offboard-a-device"></a>إيقاف تشغيل جهاز

إذا كنت تريد إيقاف تشغيل جهاز، فاستخدم أحد الإجراءات التالية:

1. في جزء التنقل، اختر **الإعدادات**، ثم اختر **نقاط النهاية**.

1. ضمن **إدارة الأجهزة**، اختر **"إيقاف الإلحاق**".

1. حدد نظام تشغيل، مثل **Windows 10 و11**، ثم ضمن **"Offboard a device**"، في قسم **أسلوب النشر**، اختر **البرنامج النصي المحلي**. 

1. في شاشة التأكيد، راجع المعلومات، ثم اختر **"تنزيل"** للمتابعة.

1. حدد **تنزيل حزمة إيقاف الإلحاق**. نوصي بحفظ حزمة الإلحاق إلى محرك أقراص قابل للإزالة.

1. قم بتشغيل البرنامج النصي على كل جهاز تريد إيقاف تشغيله. هل تحتاج إلى مساعدة في هذه المهمة؟ راجع الموارد التالية:   

   - أجهزة Windows: [إيقاف تشغيل أجهزة Windows باستخدام برنامج نصي محلي](../security/defender-endpoint/configure-endpoints-script.md#offboard-devices-using-a-local-script)
   
   - أجهزة macOS: [إلغاء التثبيت على macOS](../security/defender-endpoint/mac-resources.md#uninstalling)

> [!IMPORTANT]
> يؤدي إلغاء إلحاق جهاز إلى توقف الأجهزة عن إرسال البيانات إلى Defender for Business. ومع ذلك، يتم الاحتفاظ بالبيانات التي تم تلقيها قبل الإلحاق لمدة تصل إلى ستة (6) أشهر.

## <a name="next-objective"></a>الهدف التالي

خذ بعض الوقت [لمراجعة وتحرير poicies](m365bp-view-edit-create-mdb-policies.md).

