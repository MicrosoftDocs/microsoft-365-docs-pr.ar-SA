---
title: ترحيل الخوادم من Microsoft Monitoring Agent إلى الحل الموحد
description: تعرف على كيفية ترحيل الخوادم ذات المستوى الأدنى من Microsoft Monitoring Agent إلى الحل الموحد الجديد خطوة بخطوة من هذه المقالة.
keywords: ترحيل الخادم والخادم و2012r2 و2016 وترحيل الخادم على خوادم Microsoft Defender لنقطة النهاية MECM وMicrosoft Monitoring Agent وMMA والخادم المعطل والحل الموحد وUA
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
author: alekyaj
ms.author: macapara
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.openlocfilehash: fef1a5a7b8e47c4f97d36d4002ccf00401948d12
ms.sourcegitcommit: 2aa5c026cc06ed39a9c1c2bcabd1f563bf5a1859
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/09/2022
ms.locfileid: "66696286"
---
# <a name="migrating-servers-from-microsoft-monitoring-agent-to-the-unified-solution"></a>ترحيل الخوادم من Microsoft Monitoring Agent إلى الحل الموحد

**ينطبق على:**

- Windows Server 2012 R2
- Windows Server 2016‏

ترشدك هذه المقالة في ترحيل الخوادم ذات المستوى الأدنى من عامل مراقبة Microsoft (MMA) إلى الحل الموحد.

## <a name="prerequisites"></a>المتطلبات الأساسية

- نقطة نهاية Microsoft Configuration Manager (MECM) أقدم من 2207.
- أجهزة نظام التشغيل ذات المستوى الأدنى في بيئتك الملحقة ب Microsoft Monitoring Agent. للتأكيد، تحقق من أنه `MsSenseS.exe` قيد التشغيل في "إدارة المهام".
- وجود عامل MMA. يمكنك التحقق من ذلك عن طريق التحقق مما إذا كان معرف مساحة العمل الصحيح موجودا في لوحة التحكم> Microsoft Monitoring Agent.
- مدخل Microsoft 365 Defender نشط مع الأجهزة الملحقة.
- تم إعداد مجموعة أجهزة تحتوي على خوادم ذات مستوى أدنى مثل Windows Server 2012 R2 أو Windows Server 2016 باستخدام عامل MMA في مثيل MECM.

لمزيد من المعلومات حول تثبيت المتطلبات الأساسية المدرجة، راجع قسم [المواضيع ذات الصلة](#related-topics) .

## <a name="gather-required-files"></a>جمع الملفات المطلوبة

انسخ حزمة الحلول الموحدة، وإعداد البرنامج النصي والترحيل النصي إلى نفس مصدر المحتوى الذي تقوم بنشر تطبيقات أخرى باستخدام MECM.

1. قم بتنزيل البرنامج النصي للإلحاق والحل الموحد من [صفحة إعدادات Microsoft 365 Defender](https://sip.security.microsoft.com/preferences2/onboarding).
      :::image type="content" source="images/onboarding-script.png" alt-text="لقطة شاشة للبرنامج النصي الإلحاقي وتنزيل الحل الموحد." lightbox="images/onboarding-script.png":::
2. قم بتنزيل البرنامج النصي لل ترحيل من المستند: [سيناريوهات ترحيل الخادم من حل Microsoft Defender لنقطة النهاية السابق المستند إلى MMA](server-migration.md). يمكن أيضا العثور على هذا البرنامج النصي على GitHub: [GitHub - microsoft/mdefordownlevelserver](https://github.com/microsoft/mdefordownlevelserver).
3. احفظ جميع الملفات الثلاثة في مجلد مشترك يستخدمه MECM كمصدر برامج.
     :::image type="content" source="images/ua-migration.png" alt-text="لقطة شاشة لحفظ المجلد المشترك بواسطة MECM.":::

## <a name="create-the-package-as-an-application"></a>إنشاء الحزمة كتطبيق

1. في وحدة تحكم MECM، اتبع الخطوات التالية: **مكتبة البرامج>التطبيقات>إنشاء تطبيق**.
2. حدد **يدويا تحديد معلومات التطبيق**.
      :::image type="content" source="images/manual-application-information.png" alt-text="لقطة شاشة لتحديد تحديد معلومات التطبيق يدويا." lightbox="images/manual-application-information.png":::
3. انقر فوق **"التالي** " على شاشة "مركز البرامج" للمعالج.
4. على "أنواع النشر"، انقر فوق **"إضافة**".
5. حدد **يدويا لتحديد معلومات نوع النشر** وانقر فوق **"التالي**".
6. امنح اسما لنشر البرنامج النصي وانقر فوق **"التالي**".
     :::image type="content" source="images/manual-deployment-information.png" alt-text="لقطة شاشة تحدد معلومات نشر البرنامج النصي.":::
7. في هذه الخطوة، انسخ مسار UNC الذي يوجد فيه المحتوى. مثال: `\\Cm1\h$\SOFTWARE_SOURCE\UAmigrate`.
     :::image type="content" source="images/deployment-type-wizard.png" alt-text="لقطة شاشة تعرض نسخة مسار UNC.":::
8. بالإضافة إلى ذلك، قم بتعيين ما يلي على أنه برنامج التثبيت:

     ```powershell
       Powershell.exe -ExecutionPolicy ByPass -File install.ps1 -Log -Etl -RemoveMMA 48594f03-7e66-4e15-8b60-d9da2f92d564 -OnboardingScript .\WindowsDefenderATP.onboarding
     ```

9. انقر فوق **"التالي** " وانقر فوق "إضافة عبارة".
10. ستبحث العبارة في السجل لمعرفة ما إذا كان المفتاح التالي موجودا:  `HKEY_LOCAL_MACHINESOFTWARE\Classes\Installer\Products\63FAD065BFFD18F1926692665F704C6D`

     توفير الإدخالات التالية:
     - القيمة: **ProductName**
     - نوع البيانات: **سلسلة**
     - تحقق من الخيار: **يجب إنهاء إعداد التسجيل هذا على النظام الهدف للإشارة إلى وجود هذا التطبيق.**

     :::image type="content" source="images/detection-rule-wizard.png" alt-text="Screenshot that shows registry key detection.":::

     >[!TIP]
     >تم الحصول على قيمة مفتاح التسجيل هذه عن طريق تشغيل أمر PowerShell التالي على جهاز تم تثبيت الحل الموحد عليه. يمكن أيضا استخدام أساليب إبداعية أخرى للكشف. الهدف هو تحديد ما إذا كان الحل الموحد قد تم تثبيته بالفعل على جهاز معين.

     ```powershell
     PowerShell Cmd:  get-wmiobject Win32_Product | Sort-Object -Property Name |Format-Table IdentifyingNumber, Name, LocalPackage -AutoSize
     ```

11. في قسم **"تجربة المستخدم** "، يمكنك اختيار ما يناسب بيئتك والنقر فوق **"التالي**". بالنسبة **إلى رؤية برنامج التثبيت**، ينصح بالتثبيت مع **الرؤية العادية** أثناء اختبار المرحلة ثم تغييره إلى **"مصغر"** للنشر العام.
     >[!TIP]
     > يمكن خفض الحد الأقصى لوقت التشغيل المسموح به من (افتراضي) من 120 دقيقة إلى 30 دقيقة.

     :::image type="content" source="images/user-experience-in-deployment-type-wizard.png" alt-text="لقطة شاشة تعرض تجربة المستخدم في معالج نوع التوزيع.":::

12. انقر فوق **"التالي** " على المتطلبات.
13. انقر فوق **"التالي** " على التبعيات.
14. انقر فوق **"التالي** " حتى تظهر شاشة الإكمال، ثم **"إغلاق**".
15. استمر في النقر فوق التالي حتى اكتمال معالج التطبيق. تحقق من أن الكل قد تم تحديده باللون الأخضر.
16. أغلق المعالج، وانقر بزر الماوس الأيمن فوق التطبيق الذي تم إنشاؤه مؤخرا وانقر فوقه في مجموعة الخادم ذات المستوى الأدنى.
     :::image type="content" source="images/deploy-application.png" alt-text="Screenshot that shows deployment of created application." lightbox="images/deploy-application.png":::
17. تحقق من حالة هذا الترحيل في MECM>Monitoring>Deployments.

      :::image type="content" source="images/deployment-status.png" alt-text="لقطة شاشة تعرض التحقق من حالة النشر." lightbox="images/deployment-status.png":::

## <a name="related-topics"></a>المواضيع ذات الصلة

- [إعداد عامل مراقبة Microsoft](/services-hub/health/mma-setup)
- [توزيع التطبيقات - Configuration Manager](/mem/configmgr/apps/deploy-use/deploy-applications)
- [Microsoft Defender لنقطة النهاية - Configuration Manager](/mem/configmgr/protect/deploy-use/defender-advanced-threat-protection)
- [إلحاق خوادم Windows بخدمة Microsoft Defender لنقطة النهاية](configure-server-endpoints.md)
- [Microsoft Defender لنقطة النهاية: الدفاع عن Windows Server 2012 R2 و2016](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/defending-windows-server-2012-r2-and-2016/ba-p/2783292)
