---
title: أجهزة البنية الأساسية لسطح المكتب الظاهري (VDI) غير الثابتة
description: نشر حزمة التكوين على جهاز البنية الأساسية لسطح المكتب الظاهري (VDI) بحيث يتم إلحاقها بخدمة Microsoft Defender لنقطة النهاية.
keywords: تكوين جهاز البنية الأساسية لسطح المكتب الظاهري (VDI)، vdi، إدارة الجهاز، تكوين Microsoft Defender لنقطة النهاية، نقاط النهاية
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.custom: admindeeplinkDEFENDER
ms.topic: article
ms.date: 02/14/2022
ms.technology: mde
ms.openlocfilehash: fe86b09588f08a05183de146092b50b5cb530d0e
ms.sourcegitcommit: 195e4734d9a6e8e72bd355ee9f8bca1f18577615
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/13/2022
ms.locfileid: "64825003"
---
# <a name="onboard-non-persistent-virtual-desktop-infrastructure-vdi-devices-in-microsoft-365-defender"></a>إلحاق أجهزة البنية الأساسية لسطح المكتب الظاهري (VDI) غير الثابتة في Microsoft 365 Defender

البنية الأساسية لسطح المكتب الظاهري (VDI) هي مفهوم بنية أساسية لت تكنولوجيا المعلومات يتيح للمستخدمين النهائيين الوصول إلى مثيلات أجهزة سطح المكتب الظاهرية للمؤسسة من أي جهاز تقريبا (مثل الكمبيوتر الشخصي أو الهاتف الذكي أو الكمبيوتر اللوحي)، مما يلغي الحاجة إلى المؤسسة لتزويد المستخدمين بالأجهزة المادية. يؤدي استخدام أجهزة VDI إلى تقليل التكلفة لأن أقسام تكنولوجيا المعلومات لم تعد مسؤولة عن إدارة نقاط النهاية الفعلية وإصلاحها واستبدالها. يمكن للمستخدمين المعتمدين الوصول إلى نفس خوادم الشركة وملفاتها وتطبيقاتها وخدماتها من أي جهاز معتمد من خلال عميل سطح مكتب آمن أو مستعرض.

مثل أي نظام آخر في بيئة تكنولوجيا المعلومات، يجب أن يكون لديهم أيضا حل الكشف عن نقطة النهاية والاستجابة (الكشف التلقائي والاستجابة على النقط النهائية) والحماية من التهديدات والهجمات المتقدمة.


[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**
- [Microsoft Defender لنقطة النهاية الخطة 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)
- أجهزة البنية الأساسية لسطح المكتب الظاهري (VDI)
- Windows 10، Windows 11، Windows Server 2019، Windows Server 2022، Windows Server 2008R2/2012R2/2016

> هل تريد تجربة Defender لنقطة النهاية؟ [التسجيل للحصول على إصدار تجريبي مجاني.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-configvdi-abovefoldlink)

 > [!NOTE]
  > **VDI** -  الثابت تتم معالجة [إلحاق جهاز VDI ثابت](configure-endpoints.md) في Microsoft Defender لنقطة النهاية بنفس الطريقة التي يتم بها إلحاق جهاز فعلي، مثل سطح المكتب أو الكمبيوتر المحمول. يمكن استخدام نهج المجموعة إدارة نقاط النهاية من Microsoft وأساليب أخرى لإلحاق جهاز ثابت. في مدخل Microsoft 365 Defender، (https://security.microsoft.com)ضمن الإعداد، حدد أسلوب الإلحاق المفضل لديك، واتبع الإرشادات الخاصة بهذا النوع. 

## <a name="onboarding-non-persistent-virtual-desktop-infrastructure-vdi-devices"></a>إلحاق أجهزة البنية الأساسية الظاهرية لسطح المكتب (VDI) غير الثابتة

يدعم Defender لنقطة النهاية إعداد جلسة VDI غير الثابتة.

قد تكون هناك تحديات مرتبطة عند إلحاق مثيلات VDI. فيما يلي تحديات نموذجية لهذا السيناريو:

- الإعداد المبكر الفوري لجلسة قصيرة الأمد، والتي يجب إلحاقها ب Defender لنقطة النهاية قبل التوفير الفعلي.
- عادة ما يعاد استخدام اسم الجهاز لجلسات عمل جديدة.

في بيئة VDI، يمكن أن يكون لمثيلات VDI عمر قصير. يمكن أن تظهر أجهزة VDI في مدخل Defender لنقطة النهاية كما يلي:


- إدخال مدخل واحد لكل مثيل VDI. إذا تم بالفعل إلحاق مثيل VDI Microsoft Defender لنقطة النهاية وعند حذفه في مرحلة ما ثم إعادة إنشائه باسم المضيف نفسه، فلن يتم إنشاء كائن جديد يمثل مثيل VDI هذا في المدخل. 


  > [!NOTE]
  > في هذه الحالة، يجب تكوين *نفس* اسم الجهاز عند إنشاء جلسة العمل، على سبيل المثال باستخدام ملف إجابات غير المراقب.

- إدخالات متعددة لكل جهاز - واحد لكل مثيل VDI.

ستوجهك الخطوات التالية خلال إلحاق أجهزة VDI وستسلط الضوء على خطوات الإدخالات الفردية والمضاعفة.

> [!WARNING]
> بالنسبة إلى البيئات التي توجد فيها تكوينات موارد منخفضة، قد يؤدي إجراء تمهيد VDI إلى إبطاء أداة استشعار Defender لنقطة النهاية.

### <a name="for-windows-10-or-windows-11-or-windows-server-2012-r2-and-later"></a>ل Windows 10 أو Windows 11 أو Windows Server 2012 R2 والإصدارات الأحدث

> [!NOTE]
> يجب إعداد Windows Server 2016 وserver Windows 2012 R2 من خلال تطبيق حزمة التثبيت أولا باستخدام الإرشادات الموجودة في [خوادم Windows](/microsoft-365/security/defender-endpoint/configure-server-endpoints#windows-server-2012-r2-and-windows-server-2016) الملحقة لكي تعمل هذه الميزة.

1.  افتح ملف .zip حزمة تكوين VDI (*WindowsDefenderATPOnboardingPackage.zip*) الذي قمت بتنزيله من معالج إلحاق الخدمة. يمكنك أيضا الحصول على الحزمة من <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">مدخل Microsoft 365 Defender</a>:

    1. في جزء التنقل، حدد **الإعدادات** >  **EndpointsDevice** >  **managementOnboarding** > .

    1. حدد نظام التشغيل.

    1.  في حقل **أسلوب النشر** ، حدد **البرامج النصية لإلحاق VDI لنقاط النهاية غير الثابتة**.

    1. انقر فوق **"تنزيل الحزمة** " واحفظ ملف .zip.

2. انسخ الملفات من مجلد WindowsDefenderATPOnboardingPackage المستخرج من ملف .zip إلى الصورة الذهبية/الرئيسية أسفل المسار `C:\WINDOWS\System32\GroupPolicy\Machine\Scripts\Startup`.
    1. إذا كنت تقوم بتنفيذ إدخالات متعددة لكل جهاز - واحد لكل جلسة عمل، انسخ WindowsDefenderATPOnboardingScript.cmd.
    2. إذا كنت تقوم بتنفيذ إدخال واحد لكل جهاز، فقم بنسخ كل من Onboard-NonPersistentMachine.ps1 وWindowsDefenderATPOnboardingScript.cmd.

    > [!NOTE]
    > إذا لم تتمكن من `C:\WINDOWS\System32\GroupPolicy\Machine\Scripts\Startup` رؤية المجلد، فقد يكون مخفيا. ستحتاج إلى اختيار الخيار **"إظهار الملفات والمجلدات المخفية**" من مستكشف الملفات.

3. افتح نافذة محرر نهج المجموعة المحلي وانتقل إلى بدء **تشغيل** البرامج **النصية** \> **Windows الإعدادات** \> **تكوين** \> الكمبيوتر.

   > [!NOTE]
   > يمكن أيضا استخدام نهج المجموعة المجال لإلحاق أجهزة VDI غير الثابتة.

4. استنادا إلى الأسلوب الذي تريد تنفيذه، اتبع الخطوات المناسبة:
    - لإدخال واحد لكل جهاز:

         حدد علامة التبويب **PowerShell Scripts**، ثم انقر فوق **"إضافة**" (Windows سيفتح المستكشف مباشرة في المسار حيث نسخت البرنامج النصي للإلحاق سابقا). انتقل إلى إعداد البرنامج النصي `Onboard-NonPersistentMachine.ps1`PowerShell. ليست هناك حاجة لتحديد الملف الآخر، حيث سيتم تشغيله تلقائيا.

    - للإدخالات المتعددة لكل جهاز:

         حدد علامة التبويب **"البرامج النصية**"، ثم انقر فوق **"إضافة**" (Windows سيفتح المستكشف مباشرة في المسار حيث نسخت البرنامج النصي للإلحاق سابقا). انتقل إلى البرنامج النصي `WindowsDefenderATPOnboardingScript.cmd`bash الإلحاق.

5. اختبار الحل الخاص بك:
   1. إنشاء تجمع مع جهاز واحد.
   2. تسجيل الدخول إلى الجهاز.
   3. تسجيل الخروج من الجهاز.
   4. تسجيل الدخول إلى الجهاز مع مستخدم آخر.
   5. استنادا إلى الأسلوب الذي تريد تنفيذه، اتبع الخطوات المناسبة:
      - لإدخال واحد لكل جهاز: تحقق من إدخال واحد فقط في مدخل Microsoft 365 Defender.
      - للحصول على إدخالات متعددة لكل جهاز: تحقق من إدخالات متعددة في مدخل Microsoft 365 Defender.

6. انقر فوق **قائمة الأجهزة** في جزء التنقل.

7. استخدم دالة البحث عن طريق إدخال اسم الجهاز وحدد **الجهاز** كنوع بحث.

## <a name="for-downlevel-skus-windows-server-2008-r2"></a>بالنسبة إلى وحدات SKU المعطلة (Windows Server 2008 R2)

> [!NOTE]
> تنطبق هذه الإرشادات لإصدارات خادم Windows الأخرى أيضا إذا كنت تقوم بتشغيل Microsoft Defender لنقطة النهاية السابقة لخادم Windows 2016 وخادم Windows 2012 R2 الذي يتطلب MMA. توجد إرشادات الترحيل إلى الحل الموحد الجديد في [سيناريوهات ترحيل الخادم في Microsoft Defender لنقطة النهاية](/microsoft-365/security/defender-endpoint/server-migration).

> [!NOTE]
> يكون السجل التالي ذا صلة فقط عندما يكون الهدف هو تحقيق "إدخال واحد لكل جهاز".

1. تعيين قيمة التسجيل إلى:

    ```console
   [HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows Advanced Threat Protection\DeviceTagging]
    "VDI"="NonPersistent"
    ```

    أو استخدام سطر الأوامر:

    ```console
    reg add "HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows Advanced Threat Protection\DeviceTagging" /v VDI /t REG_SZ /d "NonPersistent" /f
    ```

2. اتبع [عملية إلحاق الخادم](configure-server-endpoints.md). 

## <a name="updating-non-persistent-virtual-desktop-infrastructure-vdi-images"></a>تحديث صور البنية الأساسية لسطح المكتب الظاهري (VDI) غير الثابتة

مع القدرة على نشر التحديثات بسهولة إلى الأجهزة الظاهرية التي تعمل في VDIs، قمنا بتقصير هذا الدليل للتركيز على كيفية الحصول على التحديثات على أجهزتك بسرعة وسهولة. لم تعد بحاجة إلى إنشاء الصور الذهبية وإغلاقها على أساس دوري، حيث يتم توسيع التحديثات إلى وحدات البت المكونة الخاصة بها على الخادم المضيف ثم تنزيلها مباشرة إلى الجهاز الظاهري عند تشغيله.

لمزيد من المعلومات، اتبع الإرشادات الواردة في [دليل النشر برنامج الحماية من الفيروسات من Microsoft Defender في بيئة البنية الأساسية لسطح المكتب الظاهري (VDI](/security/defender-endpoint/deployment-vdi-microsoft-defender-antivirus)).


## <a name="related-topics"></a>المواضيع ذات الصلة
- [أجهزة Windows باستخدام نهج المجموعة](configure-endpoints-gp.md)
- [أجهزة Windows التي تستخدم Microsoft Endpoint Configuration Manager](configure-endpoints-sccm.md)
- [أجهزة Windows باستخدام أدوات الأجهزة المحمولة إدارة الجهاز المحمول](configure-endpoints-mdm.md)
- [أجهزة Windows باستخدام برنامج نصي محلي](configure-endpoints-script.md)
- [استكشاف أخطاء إلحاق Microsoft Defender لنقطة النهاية وإصلاحها](troubleshoot-onboarding.md)
