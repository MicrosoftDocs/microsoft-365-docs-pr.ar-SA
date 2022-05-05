---
title: تخصيص الوصول إلى المجلدات الخاضعة للتحكم
description: أضف مجلدات أخرى يجب حمايتها بواسطة الوصول المتحكم به إلى المجلدات، أو اسمح للتطبيقات التي تحظر التغييرات على الملفات المهمة بشكل غير صحيح.
keywords: الوصول المتحكم به إلى المجلد، windows 10، windows 11، windows defender، برامج الفدية الضارة، الحماية، الملفات، المجلدات، تخصيص، إضافة مجلد، إضافة تطبيق، السماح، إضافة قابل للتنفيذ
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.localizationpriority: medium
audience: ITPro
author: denisebmsft
ms.author: deniseb
ms.reviewer: oogunrinde, dbodorin, vladiso, nixanm, anvascon
manager: dansimp
ms.technology: mde
ms.topic: how-to
ms.collection: M365-security-compliance
ms.date: ''
ms.openlocfilehash: ba9102f96ea08bf33f72a260779b4b37d6a6f0f4
ms.sourcegitcommit: b3f5fe84a319741583954ef8ff2ec9ec6da69bcf
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 05/05/2022
ms.locfileid: "65217365"
---
# <a name="customize-controlled-folder-access"></a>تخصيص الوصول إلى المجلدات الخاضعة للتحكم

**ينطبق على:**
- [Defender for Endpoint الخطة 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)
- برنامج الحماية من الفيروسات من Microsoft Defender

**الأنظمة الأساسية**
- بالنسبة لنظام التشغيل

> [!TIP]
> هل تريد تجربة Defender لنقطة النهاية؟ [التسجيل للحصول على إصدار تجريبي مجاني.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-assignaccess-abovefoldlink)

يساعدك الوصول المتحكم به إلى المجلد على حماية البيانات القيمة من التطبيقات والتهديدات الضارة، مثل برامج الفدية الضارة. يتم دعم الوصول إلى المجلدات التي يتم التحكم فيها على عملاء Windows Server 2019 و Windows Server 2022 و Windows 10 و Windows 11. تصف هذه المقالة كيفية تخصيص إمكانيات الوصول إلى المجلدات التي يتم التحكم فيها، وتتضمن الأقسام التالية:

- [حماية مجلدات إضافية](#protect-additional-folders)
- [إضافة تطبيقات يجب السماح لها بالوصول إلى المجلدات المحمية](#allow-specific-apps-to-make-changes-to-controlled-folders)
- [السماح للملفات التنفيذية الموقعة بالوصول إلى المجلدات المحمية](#allow-signed-executable-files-to-access-protected-folders)
- [تخصيص الإعلام](#customize-the-notification)

> [!IMPORTANT]
> يراقب الوصول إلى المجلدات الخاضعة للرقابة تطبيقات الأنشطة التي يتم اكتشافها على أنها ضارة. في بعض الأحيان، يتم حظر التطبيقات المشروعة من إجراء تغييرات على ملفاتك. إذا كان الوصول إلى المجلد الذي يتم التحكم فيه يؤثر على إنتاجية مؤسستك، فقد تفكر في تشغيل هذه الميزة في [وضع التدقيق](audit-windows-defender.md) لتقييم التأثير بشكل كامل.

## <a name="protect-additional-folders"></a>حماية مجلدات إضافية

ينطبق الوصول إلى المجلدات التي يتم التحكم فيها على العديد من مجلدات النظام والمواقع الافتراضية، بما في ذلك مجلدات مثل **المستندات** **والصور** **والأفلام**. يمكنك إضافة مجلدات أخرى محمية، ولكن لا يمكنك إزالة المجلدات الافتراضية في القائمة الافتراضية.

قد تكون إضافة مجلدات أخرى إلى الوصول إلى المجلدات التي يتم التحكم فيها مفيدة للحالات التي لا تقوم فيها بتخزين الملفات في مكتبات Windows الافتراضية، أو إذا قمت بتغيير الموقع الافتراضي لمكتباتك.

يمكنك أيضا تحديد مشاركات الشبكة ومحركات الأقراص المعينة. يتم دعم متغيرات البيئة وأحرف البدل. للحصول على معلومات حول استخدام أحرف البدل، راجع [استخدام أحرف البدل في اسم الملف ومسار المجلد أو قوائم استثناء الملحق](configure-extension-file-exclusions-microsoft-defender-antivirus.md).

يمكنك استخدام تطبيق أمن Windows أو نهج المجموعة أو PowerShell cmdlets أو موفري خدمة تكوين إدارة الأجهزة المحمولة لإضافة مجلدات محمية وإزالتها.

### <a name="use-the-windows-security-app-to-protect-additional-folders"></a>استخدام تطبيق أمن Windows لحماية مجلدات إضافية

1. افتح تطبيق أمن Windows عن طريق تحديد أيقونة الدرع في شريط المهام، أو عن طريق البحث عن *الأمان* في قائمة البدء.

2. حدد **الحماية من الفيروسات & التهديدات**، ثم قم بالتمرير لأسفل إلى قسم **الحماية من برامج الفدية الضارة** .

3. حدد **إدارة حماية برامج الفدية الضارة** لفتح جزء **الحماية من برامج الفدية الضارة** .

4. ضمن قسم **الوصول إلى المجلدات الخاضعة للرقابة** ، حدد **"المجلدات المحمية**".

5. اختر **"نعم** " في موجه **التحكم في وصول المستخدم** . يتم عرض جزء **المجلدات المحمية** .

6. حدد **"إضافة مجلد محمي** " واتبع المطالبات لإضافة مجلدات.

### <a name="use-group-policy-to-protect-additional-folders"></a>استخدام نهج المجموعة لحماية مجلدات إضافية

1. على كمبيوتر إدارة نهج المجموعة، افتح [وحدة تحكم إدارة نهج المجموعة](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11)?preserve=true). 

2. انقر بزر الماوس الأيمن فوق الكائن نهج المجموعة الذي تريد تكوينه، ثم حدد **"تحرير**".

3. في **نهج المجموعة Management Editor**، انتقل إلى  **القوالب الإدارية لنهج** **تكوين** \> \> الكمبيوتر.

4. قم بتوسيع الشجرة إلى **مكونات** \> Windows **برنامج الحماية من الفيروسات من Microsoft Defender** \> الوصول إلى **المجلد المتحكم به** **Windows Defender Exploit Guard**\>. <br/>**ملاحظة**: في الإصدارات القديمة من Windows، قد ترى **برنامج الحماية من الفيروسات لـ Windows Defender** بدلا من **برنامج الحماية من الفيروسات من Microsoft Defender**.

5. انقر نقرا مزدوجا فوق **المجلدات المحمية المكونة**، ثم قم بتعيين الخيار إلى **ممكن**. حدد **"إظهار**"، وحدد كل مجلد تريد حمايته.

6. نشر كائن نهج المجموعة كما تفعل عادة.

### <a name="use-powershell-to-protect-additional-folders"></a>استخدام PowerShell لحماية مجلدات إضافية

1. اكتب **PowerShell** في قائمة البدء، وانقر بزر **الماوس الأيمن فوق Windows PowerShell** وحدد **"تشغيل" كمسؤول**

2. اكتب أمر Cmdlet PowerShell التالي، مع استبداله `<the folder to be protected>` بمسار المجلد (مثل `"c:\apps\"`):

    ```PowerShell
    Add-MpPreference -ControlledFolderAccessProtectedFolders "<the folder to be protected>"
    ```
3. كرر الخطوة 2 لكل مجلد تريد حمايته. تظهر المجلدات المحمية في تطبيق أمن Windows.

   :::image type="content" source="images/cfa-allow-folder-ps.png" alt-text="نافذة PowerShell مع عرض cmdlet" lightbox="images/cfa-allow-folder-ps.png":::

> [!IMPORTANT]
> يستخدم `Add-MpPreference` لإلحاق التطبيقات أو إضافتها إلى القائمة وليس `Set-MpPreference`. `Set-MpPreference` سيؤدي استخدام cmdlet إلى الكتابة فوق القائمة الموجودة.

### <a name="use-mdm-csps-to-protect-additional-folders"></a>استخدام MDM CSPs لحماية مجلدات إضافية

استخدم موفر خدمة تكوين [./Vendor/MSFT/Policy/Config/Defender/GuardedFoldersList](/windows/client-management/mdm/policy-csp-defender#defender-guardedfolderslist) (CSP) للسماح للتطبيقات بإجراء تغييرات على المجلدات المحمية.

## <a name="allow-specific-apps-to-make-changes-to-controlled-folders"></a>السماح لتطبيقات معينة بإجراء تغييرات على المجلدات التي يتم التحكم فيها

يمكنك تحديد ما إذا كانت بعض التطبيقات تعتبر آمنة دائما وتمنح حق الوصول للكتابة إلى الملفات في المجلدات المحمية. يمكن أن يكون السماح بالتطبيقات مفيدا إذا تم حظر تطبيق معين تعرفه وتثق به بواسطة ميزة الوصول إلى المجلدات التي يتم التحكم فيها.

> [!IMPORTANT]
> بشكل افتراضي، يضيف Windows التطبيقات التي تعتبر مألوفة للقائمة المسموح بها. لا يتم تسجيل هذه التطبيقات التي تتم إضافتها تلقائيا في القائمة المعروضة في تطبيق أمن Windows أو باستخدام أوامر PowerShell cmdlets المقترنة. يجب ألا تحتاج إلى إضافة معظم التطبيقات. أضف التطبيقات فقط إذا تم حظرها ويمكنك التحقق من جدارتها بالثقة.

عند إضافة تطبيق، يجب تحديد موقع التطبيق. سيتم السماح للتطبيق في هذا الموقع فقط بالوصول إلى المجلدات المحمية. إذا كان التطبيق (بالاسم نفسه) في موقع مختلف، فلن تتم إضافته إلى قائمة السماح وقد يتم حظره بواسطة الوصول إلى المجلد الذي يتم التحكم فيه.

يتوفر للتطبيق أو الخدمة المسموح بها حق الوصول للكتابة إلى مجلد يتم التحكم فيه فقط بعد بدء تشغيله. على سبيل المثال، ستستمر خدمة التحديث في تشغيل الأحداث بعد السماح بها حتى يتم إيقافها وإعادة تشغيلها.

### <a name="use-the-windows-defender-security-app-to-allow-specific-apps"></a>استخدام تطبيق Windows Defender Security للسماح بتطبيقات معينة

1. افتح تطبيق أمن Windows عن طريق البحث في قائمة البدء عن **الأمان**.

2. حدد لوحة **الحماية من التهديدات & الفيروسات** (أو أيقونة الدرع على شريط القوائم الأيسر) ثم حدد **إدارة الحماية من برامج الفدية الضارة**.

3. ضمن قسم **الوصول إلى المجلدات الخاضعة للرقابة** ، حدد **"السماح بتطبيق" من خلال الوصول إلى المجلدات الخاضعة للرقابة**

4. حدد **إضافة تطبيق مسموح به** واتبع المطالبات لإضافة تطبيقات.

   :::image type="content" source="images/cfa-allow-app.png" alt-text="الزر &quot;إضافة تطبيق مسموح به&quot;" lightbox="images/cfa-allow-app.png":::

### <a name="use-group-policy-to-allow-specific-apps"></a>استخدام نهج المجموعة للسماح بتطبيقات معينة

1. على جهاز إدارة نهج المجموعة، افتح [وحدة تحكم إدارة نهج المجموعة](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11)?preserve=true)، وانقر بزر الماوس الأيمن فوق العنصر نهج المجموعة الذي تريد تكوينه وحدد **"تحرير**".

2. في **محرر إدارة نهج المجموعة**، انتقل إلى **تكوين الكمبيوتر** وحدد **القوالب الإدارية**.

3. قم بتوسيع الشجرة إلى **مكونات** \> Windows **برنامج الحماية من الفيروسات من Microsoft Defender** \> الوصول إلى **المجلد المتحكم به** **Windows Defender Exploit Guard**\>.

4. انقر نقرا مزدوجا فوق إعداد **تكوين التطبيقات المسموح بها** وقم بتعيين الخيار إلى **ممكن**. حدد **"إظهار** " وأدخل كل تطبيق.

### <a name="use-powershell-to-allow-specific-apps"></a>استخدام PowerShell للسماح بتطبيقات معينة

1. اكتب **PowerShell** في قائمة البدء، وانقر بزر **الماوس الأيمن فوق Windows PowerShell** وحدد **"تشغيل" كمسؤول**
2. أدخل cmdlet التالي:

    ```PowerShell
    Add-MpPreference -ControlledFolderAccessAllowedApplications "<the app that should be allowed, including the path>"
    ```

    على سبيل المثال، لإضافة *test.exe* القابلة للتنفيذ الموجودة في المجلد *C:\apps*، سيكون cmdlet كما يلي:

    ```PowerShell
    Add-MpPreference -ControlledFolderAccessAllowedApplications "c:\apps\test.exe"
    ```

   تابع الاستخدام `Add-MpPreference -ControlledFolderAccessAllowedApplications` لإضافة المزيد من التطبيقات إلى القائمة. ستظهر التطبيقات المضافة باستخدام أمر cmdlet هذا في تطبيق أمن Windows.

   :::image type="content" source="images/cfa-allow-app-ps.png" alt-text="Cmdlet PowerShell للسماح بتطبيق" lightbox="images/cfa-allow-app-ps.png":::

> [!IMPORTANT]
> يستخدم `Add-MpPreference` لإلحاق التطبيقات أو إضافتها إلى القائمة. `Set-MpPreference` سيؤدي استخدام cmdlet إلى الكتابة فوق القائمة الموجودة.

### <a name="use-mdm-csps-to-allow-specific-apps"></a>استخدام MDM CSPs للسماح بتطبيقات معينة

استخدم موفر خدمة تكوين [./Vendor/MSFT/Policy/Config/Defender/ControlledFolderAccessAllowedApplications](/windows/client-management/mdm/policy-csp-defender#defender-guardedfoldersallowedapplications) للسماح للتطبيقات بإجراء تغييرات على المجلدات المحمية.

## <a name="allow-signed-executable-files-to-access-protected-folders"></a>السماح للملفات التنفيذية الموقعة بالوصول إلى المجلدات المحمية

Microsoft Defender لنقطة النهاية مؤشرات الشهادات والملفات يمكن أن تسمح للملفات التنفيذية الموقعة بالوصول إلى المجلدات المحمية. للحصول على تفاصيل التنفيذ، راجع [إنشاء مؤشرات استنادا إلى الشهادات](indicator-certificates.md).

> [!Note]
> لا ينطبق هذا على محركات البرمجة النصية، بما في ذلك Powershell

## <a name="customize-the-notification"></a>تخصيص الإعلام

لمزيد من المعلومات حول تخصيص الإعلام عند تشغيل قاعدة وحظر تطبيق أو ملف، راجع [تكوين إعلامات التنبيه في Microsoft Defender لنقطة النهاية](configure-email-notifications.md).

## <a name="see-also"></a>راجع أيضًا

- [حماية المجلدات المهمة باستخدام الوصول المتحكم به إلى المجلدات](controlled-folders.md)
- [تمكين الوصول إلى المجلدات الخاضعة للتحكم](enable-controlled-folders.md)
- [تقييم قواعد تقليل الأجزاء المعرضة للهجوم](evaluate-attack-surface-reduction.md)
