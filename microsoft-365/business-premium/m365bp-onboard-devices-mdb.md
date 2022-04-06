---
title: اجهزه مؤسستك Microsoft Defender for Business
description: اجهزه مؤسستك Microsoft Defender for Business
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: overview
ms.date: 04/01/2022
ms.prod: m365-security
ms.technology: mdb
ms.localizationpriority: medium
ms.reviewer: inbadian, shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
- m365-initiative-defender-business
ms.openlocfilehash: e9810b453136025e094ef8a0e88bff526f2c5a51
ms.sourcegitcommit: adea59259a5900cad5de29ddf46d1ca9e9e1c82f
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/04/2022
ms.locfileid: "64634768"
---
# <a name="onboard-managed-devices-to-microsoft-defender-for-business"></a>الأجهزة المدارة على Microsoft Defender for Business

يجب على الأجهزة Microsoft Defender for Business لحمايتها من خلال حماية الجيل التالي (الحماية من الفيروسات والحماية من البرامج الضارة والحماية التي يتم تسليمها من السحابة) وحماية جدار الحماية وتصفية محتوى الويب والمزيد. 

للأجهزة المجهزة، يمكنك الاختيار من بين عدة خيارات:

- [استخدام الالتحاق التلقائي للأجهزة Windows التي تم تسجيلها بالفعل في إدارة نقاط النهاية من Microsoft](#use-automatic-onboarding-for-windows-devices-that-are-already-enrolled-in-microsoft-endpoint-manager)

- [استخدام برنامج نصي محلي ل Windows وأجهزة macOS](#use-a-local-script-to-onboard-windows-and-macos-devices)

- [استخدم إدارة نقاط النهاية لتسجيل](#use-microsoft-endpoint-manager-to-enroll-devices) الأجهزة (Windows و macOS و iOS و Android) ثم طبق سياسات Defender for Business على هذه الأجهزة

تتضمن هذه المقالة أيضا:

- [كيفية تشغيل اختبار الكشف على جهاز Windows](#run-a-detection-test-on-a-windows-device)

- [كيفية االأجهزة المجهزة تدريجيا](#onboard-devices-gradually)

- [كيفية إيقاف تشغيل جهاز إذا](#offboard-a-device) تم استبدال جهاز أو ترك شخص ما المؤسسة

> [!IMPORTANT]
> إذا حدث خطأ ما وفشلت عملية التكعيب، [فشاهد Microsoft Defender for Business وإصلاحها](../security/defender-business/mdb-troubleshooting.yml).

## <a name="use-automatic-onboarding-for-windows-devices-that-are-already-enrolled-in-microsoft-endpoint-manager"></a>استخدام الالتحاق التلقائي للأجهزة Windows التي تم تسجيلها بالفعل في إدارة نقاط النهاية من Microsoft

ينطبق خيار التكهين التلقائي على Windows الأجهزة فقط. تتوفر ميزة التوفر التلقائي إذا كانت مؤسستك تستخدم إدارة نقاط النهاية من Microsoft أو Microsoft Intune أو Mobile إدارة الجهاز (MDM) في Microsoft Intune قبل الحصول على Defender for Business، وكان لديك Windows  الأجهزة التي تم تسجيلها في إدارة نقاط النهاية. 

إذا Windows تم تسجيل أجهزة أخرى بالفعل في إدارة نقاط النهاية، سيكشف Defender for Business عن هذه الأجهزة أثناء عملية إعداد Defender for Business وتكوينه. سيتم سؤالك عما إذا كنت تريد استخدام التركب التلقائي لجميع أجهزة الكمبيوتر Windows أو بعضها. يمكنك الإضافة إلى جميع Windows مرة واحدة، أو تحديد أجهزة معينة للبدء بها، ثم إضافة المزيد من الأجهزة في وقت لاحق.

لمعرفة المزيد حول الإعداد التلقائي، راجع الخطوة 2 في [استخدام المعالج لإعداد](../security/defender-business/mdb-use-wizard.md) Microsoft Defender for Business.

## <a name="use-a-local-script-to-onboard-windows-and-macos-devices"></a>استخدام برنامج نصي محلي ل Windows وأجهزة macOS

يمكنك استخدام برنامج نصي محلي ل Windows وأجهزة macOS. عند تشغيل البرنامج النصي إلحاق على جهاز، فإنه ينشئ الثقة مع Azure Active Directory (إذا لم تكن هذه الثقة موجودة بالفعل)، ويسجل الجهاز في إدارة نقاط النهاية من Microsoft (إذا لم يكن مسجلا بالفعل)، ثم يقوم ب إلحاق الجهاز ب Defender for Business. 

يمكنك إعداد ما يصل إلى 10 أجهزة في كل مرة باستخدام هذا الأسلوب.

1. انتقل إلى Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com))، ثم سجل الدخول.

2. في جزء التنقل **، اختر الإعدادات** >  **Endpoints**، ثم ضمن **إدارة الأجهزة**، اختر **إلحاق**.

3. حدد نظام تشغيل، مثل **Windows 10 و11**، ثم ضمن **جهاز** على لوحة، في المقطع أسلوب النشر، اختر **برنامج نصي محلي**. 

4. حدد **تنزيل حزمة التكهيل**. نوصيك ب حفظ حزمة التكفير إلى محرك أقراص قابل للإزالة.

5. اتبع الإرشادات في المقالات التالية:

   - Windows الأجهزة: [Windows الأجهزة باستخدام برنامج نصي محلي](../security/defender-endpoint/configure-endpoints-script.md#onboard-windows-devices-using-a-local-script)

   - أجهزة macOS: [النشر اليدوي Microsoft Defender لنقطة النهاية على macOS](../security/defender-endpoint/mac-install-manually.md#download-installation-and-onboarding-packages)

## <a name="use-microsoft-endpoint-manager-to-enroll-devices"></a>استخدام إدارة نقاط النهاية من Microsoft لتسجيل الأجهزة

إذا كنت تستخدم إدارة نقاط النهاية (الذي يتضمن Microsoft Intune وجوال إدارة الجهاز)، قبل الحصول على Defender for Business، يمكنك الاستمرار في استخدام إدارة نقاط النهاية لضم أجهزة مؤسستك. باستخدام إدارة نقاط النهاية، يمكنك تشغيل أجهزة الكمبيوتر وأجهزة الكمبيوتر اللوحية والهواتف، بما في ذلك أجهزة iOS وAndroid.

إذا كانت مؤسستك تستخدم أجهزة Android، فاستخدم هذه الطريقة.

راجع [تسجيل الجهاز في Microsoft Intune](/mem/intune/enrollment/device-enrollment).


## <a name="run-a-detection-test-on-a-windows-device"></a>تشغيل اختبار الكشف على جهاز Windows

بعد أن قمت Windows الأجهزة إلى Defender for Business، يمكنك تشغيل اختبار الكشف على جهاز Windows للتأكد من أن كل شيء يعمل بشكل صحيح.

1. على Windows، أنشئ مجلدا: `C:\test-MDATP-test`.

2. افتح موجه الأوامر كمسؤول.

3. في نافذة موجه الأوامر، تشغيل الأمر PowerShell التالي:

   ```powershell
   powershell.exe -NoExit -ExecutionPolicy Bypass -WindowStyle Hidden $ErrorActionPreference = 'silentlycontinue';(New-Object System.Net.WebClient).DownloadFile('http://127.0.0.1/1.exe', 'C:\\test-MDATP-test\\invoice.exe');Start-Process 'C:\\test-MDATP-test\\invoice.exe'
   ```

بعد تشغيل الأمر، سيتم إغلاق نافذة موجه الأوامر تلقائيا. إذا نجح، سيتم وضع علامة على اختبار الكشف كمكتمل، وسيظهر تنبيه جديد في مدخل Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)) للجهاز الذي تم تحديثه حديثا في غضون 10 دقائق.

## <a name="onboard-devices-gradually"></a>الأجهزة المجهزة تدريجيا

إذا كنت تفضل الأجهزة المجهزة في مراحل، والتي نطلق عليها االأجهزة تدريجيا، فاتبع الخطوات التالية: 

1. تحديد مجموعة من الأجهزة لل متنها.

2. انتقل إلى Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com))، ثم سجل الدخول.

3. في جزء التنقل **، اختر الإعدادات** >  **Endpoints**، ثم ضمن **إدارة الأجهزة**، اختر **إلحاق**.

4. حدد نظام تشغيل (مثل **Windows 10 و11)**، ثم اختر أسلوبا لل متن الطائرة (مثل **البرنامج النصي المحلي**). اتبع الإرشادات المتوفرة لطريقة تحديدك.

5. كرر هذه العملية لكل مجموعة من الأجهزة التي تريد اعادتها. 

> [!TIP]
> لست بحاجة إلى استخدام نفس حزمة الإستخدام في كل مرة تقوم فيها بأجهزة الإستخدام. على سبيل المثال، يمكنك استخدام برنامج نصي محلي للوح بعض الأجهزة، وفي وقت لاحق، يمكنك اختيار طريقة أخرى للوح المزيد من الأجهزة.

## <a name="offboard-a-device"></a>إيقاف تشغيل جهاز

إذا كنت تريد إيقاف تشغيل جهاز، فاتبع الخطوات التالية:

1. انتقل إلى Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)) ثم سجل الدخول.

2. في جزء التنقل **، اختر الإعدادات**، ثم اختر **نقاط النهاية**.

3. ضمن **إدارة الأجهزة**، اختر **إيقاف التشغيل**.

4. حدد نظام تشغيل، مثل **Windows 10 و11**، ثم ضمن **إيقاف** تشغيل جهاز، في المقطع أسلوب النشر، اختر **برنامج نصي محلي**. 

5. في شاشة التأكيد، راجع المعلومات، ثم اختر **تنزيل** للمتابعة.

6. حدد **تنزيل حزمة إيقاف التشغيل**. نوصيك ب حفظ حزمة إيقاف التشغيل إلى محرك أقراص قابل للإزالة.

7. تشغيل البرنامج النصي على كل جهاز تريد إيقاف تشغيله. هل تحتاج إلى مساعدة في هذه المهمة؟ راجع الموارد التالية:   

   - Windows الأجهزة: [إيقاف Windows الأجهزة باستخدام برنامج نصي محلي](../security/defender-endpoint/configure-endpoints-script.md#offboard-devices-using-a-local-script)
   
   - أجهزة macOS: [إلغاء تثبيت على macOS](../security/defender-endpoint/mac-resources.md#uninstalling)

> [!IMPORTANT]
> يؤدي إيقاف تشغيل الجهاز إلى إيقاف الأجهزة عن إرسال البيانات إلى Defender for Business. ومع ذلك، يتم الاحتفاظ بالبيانات التي تم تلقيها قبل الخروج لمدة تصل إلى ستة (6) أشهر.

## <a name="next-steps"></a>الخطوات التالية

[مراجعة إجراءات المعالجة في Microsoft 365 Business Premium](m365bp-review-remediation-actions-devices.md)