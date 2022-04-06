---
title: حماية المجلدات المهمة من برامج الفدية الضارة من تشفير ملفاتك باستخدام الوصول المتحكم به إلى المجلدات
description: يمكن حماية الملفات الموجودة في المجلدات الافتراضية من أن يتم تغييرها بواسطة التطبيقات الضارة. منع برامج الفدية الضارة من تشفير ملفاتك.
keywords: الوصول إلى المجلدات الخاضعة للتحكم، windows 10، windows defender، برامج الفدية الضارة، الحماية، الملفات، المجلدات
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
author: denisebmsft
ms.author: deniseb
audience: ITPro
ms.reviewer: oogunrinde, sugamar
manager: dansimp
ms.custom: asr
ms.technology: mde
ms.topic: how-to
ms.collection: m365-security-compliance
ms.date: ''
ms.openlocfilehash: ea3e45a5469c9769f55f9ce90f799c54556de814
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/08/2022
ms.locfileid: "63583041"
---
# <a name="protect-important-folders-with-controlled-folder-access"></a>حماية المجلدات المهمة باستخدام الوصول المتحكم به إلى المجلدات

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**

- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> هل تريد تجربة Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-assignaccess-abovefoldlink)

## <a name="what-is-controlled-folder-access"></a>ما هو الوصول المتحكم به إلى المجلدات؟

يساعد الوصول المتحكم به إلى المجلدات على حماية بياناتك القيمة من التطبيقات الضارة والتهديدات، مثل برامج الفدية الضارة. يحمي الوصول إلى المجلدات الخاضعة للتحكم بياناتك من خلال التحقق من التطبيقات من قائمة التطبيقات المعروفة الموثوق بها. مدعوم على Windows Server 2019 و Windows Server 2022 و Windows 10 و Windows 11 العميلة، يمكن تشغيل الوصول المتحكم به إلى المجلدات باستخدام أمن Windows App، Microsoft Endpoint Configuration Manager أو Intune (للأجهزة المدارة).

> [!NOTE]
> إن محركات البرمجة النصية غير موثوق بها ولا يمكنك السماح لها بالوصول إلى المجلدات المحمية الخاضعة للتحكم. على سبيل المثال، PowerShell غير موثوق به من خلال الوصول المتحكم به إلى المجلد، حتى لو سمحت باستخدام مؤشرات [الشهادة والملفات](/microsoft-365/security/defender-endpoint/indicator-certificates).

يعمل الوصول المتحكم به إلى المجلدات بشكل أفضل مع [Microsoft Defender لنقطة](microsoft-defender-endpoint.md) النهاية، مما يوفر لك إعداد تقارير مفصلة حول أحداث وكتل الوصول إلى المجلدات التي يتم التحكم فيها كجزء من سيناريوهات التحقيق المعتادة [في التنبيهات](investigate-alerts.md).

> [!TIP]
> لا تنشئ كتل الوصول إلى المجلدات الخاضعة للتحكم تنبيهات في [قائمة انتظار التنبيهات](alerts-queue.md). ومع ذلك، يمكنك عرض معلومات حول كتل الوصول إلى المجلدات الخاضعة [](investigate-machines.md)للتحكم في طريقة عرض المخطط [](advanced-hunting-overview.md)الزمني للجهاز، أثناء استخدام الصيد المتقدم، أو قواعد [الكشف المخصصة](custom-detection-rules.md).

## <a name="how-does-controlled-folder-access-work"></a>كيف يعمل الوصول المتحكم به إلى المجلدات؟

يعمل الوصول المتحكم به إلى المجلدات فقط من خلال السماح للتطبيقات الموثوق بها بالوصول إلى المجلدات المحمية. يتم تحديد المجلدات المحمية عند تكوين الوصول إلى المجلدات الخاضعة للتحكم. عادة، يتم تضمين المجلدات الشائع استخدامها، مثل تلك المستخدمة للمستندات والصور والتنزيلات وما إلى ذلك، في قائمة المجلدات التي يتم التحكم فيها.

يعمل الوصول المتحكم به إلى المجلد مع قائمة التطبيقات الموثوق بها. تعمل التطبيقات المضمنة في قائمة البرامج الموثوق بها كما هو متوقع. يتم منع التطبيقات غير المضمنة في القائمة من إجراء أي تغييرات على الملفات داخل المجلدات المحمية.

تضاف التطبيقات إلى القائمة استنادا إلى انتشارها وسمعة هذه التطبيقات. تعتبر التطبيقات الأكثر انتشارا في مؤسستك ولم تعرض أي سلوك يعتبر ضارا موثوقا بها. تضاف هذه التطبيقات إلى القائمة تلقائيا.

يمكن أيضا إضافة التطبيقات يدويا إلى القائمة الموثوق بها باستخدام إدارة التكوين أو Intune. يمكن تنفيذ إجراءات إضافية من مدخل Microsoft 365 Defender.

## <a name="why-controlled-folder-access-is-important"></a>سبب أهمية الوصول إلى المجلدات الخاضعة للتحكم

إن إمكانية الوصول إلى المجلدات الخاضعة للتحكم مفيدة بشكل خاص في المساعدة على حماية مستنداتك ومعلوماتك من [برامج الفدية الضارة](https://www.microsoft.com/wdsi/threats/ransomware). في هجوم برامج الفدية الضارة، يمكن أن يتم تشفير ملفاتك أو احتجازها. عند وضع إمكانية الوصول إلى المجلدات الخاضعة للتحكم، يظهر إعلام على الكمبيوتر حيث حاول تطبيق إجراء تغييرات على ملف في مجلد محمي. يمكنك [تخصيص الإعلام بتفاصيل](attack-surface-reduction-rules-deployment-implement.md#customize-attack-surface-reduction-rules) الشركة ومعلومات الاتصال. يمكنك أيضا تمكين القواعد بشكل فردي لتخصيص تقنيات أجهزة عرض الميزات.

تتضمن [المجلدات المحمية](#review-controlled-folder-access-events-in-windows-event-viewer) مجلدات النظام الشائعة (بما في ذلك قطاعات التشغيل)، كما يمكنك [إضافة المزيد من المجلدات](customize-controlled-folders.md#protect-additional-folders). يمكنك أيضا [السماح للتطبيقات](customize-controlled-folders.md#allow-specific-apps-to-make-changes-to-controlled-folders) بالسماح لها بالوصول إلى المجلدات المحمية.

يمكنك استخدام [وضع التدقيق](audit-windows-defender.md) لتقييم كيفية تأثير الوصول المتحكم به إلى المجلدات على مؤسستك إذا تم تمكينه. يمكنك أيضا زيارة موقع ويب Windows Defender Test في demo.wd.microsoft.com للتأكد من أن [](https://demo.wd.microsoft.com?ocid=cx-wddocs-testground) الميزة تعمل وترى كيفية عملها.

> [!NOTE]
> تم إهمال موقع عرض Defender for Endpoint demo.wd.microsoft.com، وستزال في المستقبل.

يتم دعم الوصول إلى المجلدات الخاضعة للتحكم في الإصدارات التالية من Windows:

- [Windows 10 الإصدار 1709](/windows/whats-new/whats-new-windows-10-version-1709) والإصدارات الأحدث
- Windows 11
- [Windows Server 2019](/windows-server/get-started-19/whats-new-19)
- Windows Server 2022

## <a name="windows-system-folders-are-protected-by-default"></a>Windows مجلدات النظام المحمية بشكل افتراضي

Windows مجلدات النظام المحمية بشكل افتراضي، إلى جانب مجلدات أخرى متعددة:

تتضمن المجلدات المحمية مجلدات النظام الشائعة (بما في ذلك قطاعات التشغيل)، كما يمكنك إضافة مجلدات إضافية. يمكنك أيضا السماح للتطبيقات بالسماح لها بالوصول إلى المجلدات المحمية.  إن Windows مجلدات الأنظمة المحمية بشكل افتراضي هي:

- `c:\Users\<username>\Documents`
- `c:\Users\Public\Documents`
- `c:\Users\<username>\Pictures`
- `c:\Users\Public\Pictures`
- `c:\Users\Public\Videos`
- `c:\Users\<username>\Videos`
- `c:\Users\<username>\Music`
- `c:\Users\Public\Music`
- `c:\Users\<username>\Favorites`

تظهر المجلدات الافتراضية في ملف تعريف المستخدم، ضمن **هذا الكمبيوتر الشخصي**.
   > [!div class="mx-imgBorder"]
   > ![مجلدات Windows الأنظمة الافتراضية المحمية](images/defaultfolders.png)

> [!NOTE]
> يمكنك تكوين مجلدات إضافية كمحمية، ولكن لا يمكنك Windows مجلدات النظام المحمية بشكل افتراضي.

## <a name="requirements-for-controlled-folder-access"></a>متطلبات الوصول إلى المجلدات الخاضعة للتحكم

يتطلب الوصول إلى المجلدات الخاضعة [للتحكم برنامج الحماية من الفيروسات من Microsoft Defender الحماية في الوقت الحقيقي](configure-real-time-protection-microsoft-defender-antivirus.md).

## <a name="review-controlled-folder-access-events-in-the-microsoft-365-defender-portal"></a>مراجعة أحداث الوصول إلى المجلدات الخاضعة للتحكم في مدخل Microsoft 365 Defender

يوفر Defender for Endpoint تقارير تفصيلية حول الأحداث والحظر كجزء من سيناريوهات التحقيق [](investigate-alerts.md) في التنبيهات في مدخل Microsoft 365 Defender؛ راجع [Microsoft Defender ل Endpoint في Microsoft 365 Defender](../defender/microsoft-365-security-center-mde.md).

يمكنك الاستعلام عن بيانات Microsoft Defender لنقطة النهاية باستخدام [البحث المتقدم](advanced-hunting-overview.md). إذا كنت تستخدم وضع التدقيق[](audit-windows-defender.md)، يمكنك استخدام البحث المتقدم لمعرفة [](advanced-hunting-overview.md) كيف يمكن أن تؤثر إعدادات الوصول إلى المجلدات التي يتم التحكم بها على بيئتك إذا تم تمكينها.

مثال استعلام:

```PowerShell
DeviceEvents
| where ActionType in ('ControlledFolderAccessViolationAudited','ControlledFolderAccessViolationBlocked')
```

## <a name="review-controlled-folder-access-events-in-windows-event-viewer"></a>مراجعة أحداث الوصول إلى المجلدات الخاضعة للتحكم في Windows الحدث

يمكنك مراجعة Windows الأحداث لرؤية الأحداث التي يتم إنشاؤها عند التحكم في كتل الوصول إلى المجلد (أو عمليات التدقيق) للتطبيق:

1. قم [بتنزيل حزمة](https://aka.ms/mp7z2w) التقييم واستخراج الملف *cfa-events.xmlإلى موقع* يمكن الوصول إليه بسهولة على الجهاز.
2. اكتب **عارض الأحداث** في قائمة البدء لفتح Windows الحدث.
3. في اللوحة اليسرى، ضمن **إجراءات**، حدد **استيراد طريقة عرض مخصصة...**.
4. انتقل إلى المكان الذي *cfa-events.xmlمنه* وحدده. بدلا من ذلك [، انسخ XML مباشرة](event-views.md).
5. حدد **موافق**.

يعرض الجدول التالي الأحداث المتعلقة بالوصول المتحكم به إلى المجلدات:

<br/><br/>

|"معرّف الحدث"|الوصف|
|---|---|
|5007|حدث عند تغيير الإعدادات|
|1124|حدث الوصول إلى المجلدات التي تم تدقيقها|
|1123|حدث الوصول إلى المجلدات المحظورة التي تم التحكم فيها|

## <a name="view-or-change-the-list-of-protected-folders"></a>عرض قائمة المجلدات المحمية أو تغييرها

يمكنك استخدام تطبيق أمن Windows لعرض قائمة المجلدات المحمية بواسطة الوصول المتحكم به إلى المجلدات.

1. على جهاز Windows 10 أو Windows 11، افتح أمن Windows التطبيق.
2. حدد **الحماية من & الفيروسات**.
3. ضمن **الحماية من برامج الفدية الضارة**، حدد **إدارة الحماية من برامج الفدية الضارة**.
4. إذا تم إيقاف تشغيل الوصول إلى المجلدات الخاضعة للتحكم، ستحتاج إلى تشغيله. حدد **المجلدات المحمية**.
5. قم بتنفيذ أحد الخطوتين التاليين:
   - لإضافة مجلد، حدد **+ إضافة مجلد محمي**.
   - لإزالة مجلد، حدده، ثم حدد **إزالة**.

> [!NOTE]
> [Windows تكون مجلدات](#windows-system-folders-are-protected-by-default) النظام محمية بشكل افتراضي، ولا يمكنك إزالتها من القائمة.
