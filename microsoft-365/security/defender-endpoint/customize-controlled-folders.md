---
title: تخصيص الوصول إلى المجلدات الخاضعة للتحكم
description: يمكنك إضافة مجلدات أخرى يجب حمايتها من خلال الوصول إلى المجلدات الخاضعة للتحكم، أو السماح للتطبيقات التي تمنع إجراء تغييرات على الملفات المهمة بشكل غير صحيح.
keywords: الوصول إلى المجلدات الخاضعة للتحكم، windows 10، windows 11، windows defender، برامج الفدية الضارة، الحماية، الملفات، المجلدات، تخصيص، إضافة مجلد، إضافة تطبيق، السماح، إضافة قابل للتنفيذ
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
ms.collection: m365initiative-m365-defender
ms.date: ''
ms.openlocfilehash: c290ad42702ddcb815880fedfe72d9de73065b8d
ms.sourcegitcommit: bae72428d229827cba4c807d9cd362417afbcccb
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 02/02/2022
ms.locfileid: "63578095"
---
# <a name="customize-controlled-folder-access"></a>تخصيص الوصول إلى المجلدات الخاضعة للتحكم

**ينطبق على:**
- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> [!TIP]
> هل تريد تجربة Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-assignaccess-abovefoldlink)

يساعدك الوصول المتحكم به إلى المجلد على حماية البيانات القيمة من التطبيقات الضارة والتهديدات، مثل برامج الفدية الضارة. يتم دعم الوصول المتحكم به إلى المجلدات على Windows Server 2019 Windows Server 2022 و Windows 10 و Windows 11 العملاء. تصف هذه المقالة كيفية تخصيص قدرات الوصول إلى المجلدات التي يتم التحكم بها، وتتضمن المقاطع التالية:

- [حماية مجلدات إضافية](#protect-additional-folders)
- [إضافة تطبيقات يجب السماح لها بالوصول إلى المجلدات المحمية](#allow-specific-apps-to-make-changes-to-controlled-folders)
- [السماح للملفات القابلة للتنفيذ الموقعة بالوصول إلى المجلدات المحمية](#allow-signed-executable-files-to-access-protected-folders)
- [تخصيص الإعلام](#customize-the-notification)

> [!IMPORTANT]
> ويراقب الوصول إلى المجلدات الخاضعة للتحكم تطبيقات الأنشطة التي يتم الكشف عنها كضارة. في بعض الأحيان، يتم حظر التطبيقات الشرعية من إجراء تغييرات على ملفاتك. إذا كان الوصول إلى المجلدات الخاضعة للتحكم يؤثر على إنتاجية مؤسستك، فقد تفكر في تشغيل هذه الميزة [](audit-windows-defender.md) في وضع التدقيق لتقييم التأثير بشكل كامل.

## <a name="protect-additional-folders"></a>حماية مجلدات إضافية

ينطبق الوصول المتحكم به إلى المجلدات على العديد من مجلدات النظام والمواقع الافتراضية، بما في ذلك المجلدات مثل **المستندات** **والصور والأفلام.** يمكنك إضافة مجلدات أخرى لحمايتها، ولكن لا يمكنك إزالة المجلدات الافتراضية في القائمة الافتراضية.

قد تكون إضافة مجلدات أخرى إلى الوصول إلى المجلدات الخاضعة للتحكم مفيدة في الحالات التي لا تقوم فيها بتخزين الملفات في مكتبات Windows الافتراضية، أو إذا قمت بتغيير الموقع الافتراضي لمكتباتك.

يمكنك أيضا تحديد أسهم الشبكة ومحركات الأقراص التي تم تعيينها. إن متغيرات البيئة و أحرف البدل معتمدة. للحصول على معلومات حول استخدام أحرف البدل، راجع استخدام أحرف البدل في اسم الملف ومسار [المجلد أو قوائم استثناءات الملحقات](configure-extension-file-exclusions-microsoft-defender-antivirus.md).

يمكنك استخدام تطبيق أمن Windows أو نهج المجموعة أو PowerShell cmdlets أو موفري خدمات تكوين إدارة أجهزة المحمول لإضافة المجلدات المحمية وإزالتها.

### <a name="use-the-windows-security-app-to-protect-additional-folders"></a>استخدام أمن Windows لحماية مجلدات إضافية

1. افتح أمن Windows عن طريق تحديد أيقونة الدرع في شريط المهام، أو عن طريق البحث عن الأمان في قائمة البدء.

2. حدد **الحماية من & الفيروسات**، ثم قم بالتمرير لأسفل وصولا إلى قسم **الحماية من برامج الفدية** الضارة.

3. حدد **إدارة الحماية من برامج الفدية** الضارة لفتح جزء **الحماية من برامج الفدية** الضارة.

4. ضمن المقطع **الوصول إلى المجلدات الخاضعة** للتحكم، حدد **المجلدات المحمية**.

5. اختر **نعم** على المطالبة **"التحكم بالوصول إلى** المستخدم". يتم **عرض جزء المجلدات** المحمية.

6. حدد **إضافة مجلد محمي** واتبع المطالبات لإضافة مجلدات.

### <a name="use-group-policy-to-protect-additional-folders"></a>استخدام "نهج المجموعة" لحماية مجلدات إضافية

1. على كمبيوتر إدارة نهج المجموعة، افتح [وحدة تحكم إدارة نهج المجموعة](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11)?preserve=true). 

2. انقر ب الماوس الأيمن فوق كائن نهج المجموعة الذي تريد تكوينه، ثم حدد **تحرير**.

3. في محرر **إدارة نهج المجموعة**، انتقل إلى **قوالب نهج** \> **تكوين** \> الكمبيوتر **الإدارية**.

4. قم بتوسيع الشجرة Windows **مكونات برنامج الحماية من الفيروسات من Microsoft Defender** \>  \> Windows الوصول إلى المجلدات التي يتحكم **بها Defender Exploit Guard** \> **.** <br/>**ملاحظة**: في الإصدارات القديمة من Windows، قد ترى **برنامج الحماية من الفيروسات لـ Windows Defender بدلا من** **برنامج الحماية من الفيروسات من Microsoft Defender.**

5. انقر نقرا **مزدوجا فوق المجلدات المحمية التي تم تكوينها**، ثم قم بتعيين الخيار إلى **تمكين**. حدد **إظهار**، وحدد كل مجلد تريد حمايته.

6. نشر كائن نهج المجموعة كما تفعل عادة.

### <a name="use-powershell-to-protect-additional-folders"></a>استخدام PowerShell لحماية مجلدات إضافية

1. اكتب **PowerShell** في قائمة البدء، وانقر بيمين **فوق Windows PowerShell** وحدد **تشغيل كمسؤول**

2. اكتب الأمر Cmdlet `<the folder to be protected>` التالي في PowerShell، مع استبداله بمسار المجلد (على سبيل المثال `"c:\apps\"`):

    ```PowerShell
    Add-MpPreference -ControlledFolderAccessProtectedFolders "<the folder to be protected>"
    ```
3. كرر الخطوة 2 لكل مجلد تريد حمايته. تكون المجلدات المحمية مرئية في تطبيق أمن Windows.

   :::image type="content" source="images/cfa-allow-folder-ps.png" alt-text="نافذة PowerShell مع عرض cmdlet.":::

> [!IMPORTANT]
> يتم `Add-MpPreference` استخدامها ل إلحاق التطبيقات أو إضافتها إلى القائمة وليس .`Set-MpPreference` سيكتم `Set-MpPreference` الكتابة فوق القائمة الموجودة باستخدام الأمر cmdlet.

### <a name="use-mdm-csps-to-protect-additional-folders"></a>استخدام MDM CSPs لحماية مجلدات إضافية

استخدم [موفر خدمة تكوين ./Vendor/MSFT/Policy/Config/Defender/GuardedFoldersList](/windows/client-management/mdm/policy-csp-defender#defender-guardedfolderslist) (CSP) للسماح للتطبيقات بإجراء تغييرات على المجلدات المحمية.

## <a name="allow-specific-apps-to-make-changes-to-controlled-folders"></a>السماح لتطبيقات معينة بإجراء تغييرات على المجلدات التي يتم التحكم فيها

يمكنك تحديد ما إذا كانت بعض التطبيقات تعتبر دائما آمنة وتعطي حق الوصول للكتابة إلى الملفات في المجلدات المحمية. قد يكون السماح للتطبيقات مفيدا إذا تم حظر تطبيق معين تعرفه وتثق به بواسطة ميزة الوصول إلى المجلدات الخاضعة للتحكم.

> [!IMPORTANT]
> بشكل افتراضي، Windows إضافة تطبيقات تعتبر سهلة الاستخدام إلى القائمة المسموح بها. لا يتم تسجيل مثل هذه التطبيقات التي تضاف تلقائيا في القائمة المعروضة في تطبيق أمن Windows أو باستخدام cmdlets المقترنة في PowerShell. يجب ألا تحتاج إلى إضافة معظم التطبيقات. يمكنك إضافة التطبيقات فقط إذا تم حظرها، كما يمكنك التحقق من جدارتها بالثقة.

عند إضافة تطبيق، يجب تحديد موقع التطبيق. سيتم السماح للتطبيق في هذا الموقع فقط بالوصول إلى المجلدات المحمية. إذا كان التطبيق (بالاسم نفسه) في موقع آخر، لن يضاف إلى قائمة السماح وقد يتم حظره بواسطة الوصول المتحكم به إلى المجلدات.

لا يمكن للتطبيق أو الخدمة المسموح بها سوى كتابة الوصول إلى مجلد متحكم به بعد بدء تشغيل التطبيق أو الخدمة المسموح بها. على سبيل المثال، ستستمر خدمة التحديث في تشغيل الأحداث بعد السماح بها حتى يتم إيقافها وإعادة تشغيلها.

### <a name="use-the-windows-defender-security-app-to-allow-specific-apps"></a>استخدام Windows أمان Defender للسماح لتطبيقات معينة

1. افتح أمن Windows من خلال البحث في قائمة البدء ل **الأمان**.

2. حدد لوحة **الحماية من &** الفيروسات (أو أيقونة الدرع على شريط القوائم الأيسر) ثم حدد **إدارة الحماية من برامج الفدية الضارة**.

3. ضمن المقطع **الوصول إلى المجلدات الخاضعة** للتحكم، حدد **السماح للتطبيق من خلال الوصول إلى المجلدات الخاضعة للتحكم**

4. حدد **إضافة تطبيق مسموح** به واتبع المطالبات لإضافة تطبيقات.

   :::image type="content" source="images/cfa-allow-app.png" alt-text="إضافة زر تطبيق مسموح به.":::

### <a name="use-group-policy-to-allow-specific-apps"></a>استخدام "نهج المجموعة" للسماح لتطبيقات معينة

1. على جهاز إدارة نهج المجموعة، افتح وحدة تحكم إدارة [نهج](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11)?preserve=true) المجموعة، وانقر بز الماوس الأيمن فوق كائن نهج المجموعة الذي تريد تكوينه وحدد **تحرير**.

2. في محرر **إدارة نهج المجموعة**، انتقل إلى **تكوين الكمبيوتر** وحدد **القوالب الإدارية**.

3. قم بتوسيع الشجرة Windows **مكونات برنامج الحماية من الفيروسات من Microsoft Defender** \>  \> Windows الوصول إلى المجلدات التي يتحكم **بها Defender Exploit Guard** \> **.**

4. انقر نقرا مزدوجا **فوق إعداد تكوين التطبيقات المسموح** بها ثم قم بتعيين الخيار إلى **تمكين**. حدد **إظهار** وأدخل كل تطبيق.

### <a name="use-powershell-to-allow-specific-apps"></a>استخدام PowerShell للسماح لتطبيقات معينة

1. اكتب **PowerShell** في قائمة البدء، وانقر بيمين **فوق Windows PowerShell** وحدد **تشغيل كمسؤول**
2. أدخل cmdlet التالي:

    ```PowerShell
    Add-MpPreference -ControlledFolderAccessAllowedApplications "<the app that should be allowed, including the path>"
    ```

    على سبيل المثال، لإضافة الملف *test.exe* الموجود في المجلد *C:\apps*، سيكون cmdlet كما يلي:

    ```PowerShell
    Add-MpPreference -ControlledFolderAccessAllowedApplications "c:\apps\test.exe"
    ```

   تابع الاستخدام `Add-MpPreference -ControlledFolderAccessAllowedApplications` لإضافة المزيد من التطبيقات إلى القائمة. ستظهر التطبيقات المضافة باستخدام الأمر cmdlet هذا في أمن Windows التطبيق.

   :::image type="content" source="images/cfa-allow-app-ps.png" alt-text="PowerShell cmdlet للسماح للتطبيق.":::

> [!IMPORTANT]
> يتم `Add-MpPreference` استخدامها ل إلحاق التطبيقات بالقائمة أو إضافتها. سيكتم `Set-MpPreference` الكتابة فوق القائمة الموجودة باستخدام الأمر cmdlet.

### <a name="use-mdm-csps-to-allow-specific-apps"></a>استخدام MDM CSPs للسماح لتطبيقات معينة

استخدم [موفر خدمة تكوين ./Vendor/MSFT/Policy/Config/Defender/GuardedFoldersAllowedApplications](/windows/client-management/mdm/policy-csp-defender#defender-guardedfoldersallowedapplications) (CSP) للسماح للتطبيقات بإجراء تغييرات على المجلدات المحمية.

## <a name="allow-signed-executable-files-to-access-protected-folders"></a>السماح للملفات القابلة للتنفيذ الموقعة بالوصول إلى المجلدات المحمية

يمكن لمؤشرات شهادات وملفات Microsoft Defender لنقطة النهاية السماح للملفات القابلة للتنفيذ الموقعة بالوصول إلى المجلدات المحمية. للحصول على تفاصيل التنفيذ، راجع [إنشاء مؤشرات استنادا إلى الشهادات](indicator-certificates.md).

> [!Note]
> لا ينطبق ذلك على محركات البرمجة النصية، بما في ذلك Powershell

## <a name="customize-the-notification"></a>تخصيص الإعلام

لمزيد من المعلومات حول تخصيص الإعلام عند تشغيل قاعدة وحظر تطبيق أو ملف، راجع تكوين إعلامات التنبيهات في [Microsoft Defender لنقطة النهاية](configure-email-notifications.md).

## <a name="see-also"></a>راجع أيضًا

- [حماية المجلدات المهمة باستخدام الوصول المتحكم به إلى المجلدات](controlled-folders.md)
- [تمكين الوصول إلى المجلدات الخاضعة للتحكم](enable-controlled-folders.md)
- [تقييم قواعد الحد من سطح الهجوم](evaluate-attack-surface-reduction.md)
