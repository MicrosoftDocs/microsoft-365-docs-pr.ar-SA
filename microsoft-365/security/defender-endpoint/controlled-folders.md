---
title: حماية المجلدات المهمة من برامج الفدية الضارة من تشفير ملفاتك باستخدام الوصول المتحكم به إلى المجلد
description: يمكن حماية الملفات الموجودة في المجلدات الافتراضية من تغييرها بواسطة التطبيقات الضارة. منع برامج الفدية الضارة من تشفير ملفاتك.
keywords: الوصول إلى المجلد المتحكم به، windows 10، windows defender، برامج الفدية الضارة، الحماية، الملفات، المجلدات
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
ms.openlocfilehash: 02017a614544cfb10eb43d375212fc7e37124ad3
ms.sourcegitcommit: a7cd723fd62b4b0aae9c2c2df04ead3c28180084
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 06/02/2022
ms.locfileid: "65840376"
---
# <a name="protect-important-folders-with-controlled-folder-access"></a>حماية المجلدات المهمة باستخدام الوصول المتحكم به إلى المجلدات

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**

- [Defender for Endpoint الخطة 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)
- برنامج الحماية من الفيروسات من Microsoft Defender

**ينطبق على**
- بالنسبة لنظام التشغيل


> هل تريد تجربة Defender لنقطة النهاية؟ [التسجيل للحصول على إصدار تجريبي مجاني.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-assignaccess-abovefoldlink)

## <a name="what-is-controlled-folder-access"></a>ما هو الوصول إلى المجلدات التي يتم التحكم فيها؟

يساعد الوصول المتحكم به إلى المجلد على حماية بياناتك القيمة من التطبيقات والتهديدات الضارة، مثل برامج الفدية الضارة. يحمي الوصول المتحكم به إلى المجلدات بياناتك من خلال التحقق من التطبيقات مقابل قائمة بالتطبيقات المعروفة الموثوق بها. يمكن تشغيل الوصول إلى المجلدات التي يتم التحكم فيها باستخدام تطبيق أمن Windows، وذلك معتمدا على عملاء Windows Server 2019 وserver Windows Server 2022 و Windows 10 Windows 11. Microsoft Endpoint Configuration Manager أو Intune (للأجهزة المدارة).

> [!NOTE]
> محركات البرمجة النصية غير موثوق بها ولا يمكنك السماح لها بالوصول إلى المجلدات المحمية التي يتم التحكم فيها. على سبيل المثال، PowerShell غير موثوق به من قبل الوصول المتحكم به إلى المجلد، حتى لو سمحت باستخدام [مؤشرات الشهادة والملفات](/microsoft-365/security/defender-endpoint/indicator-certificates).

يعمل الوصول إلى المجلدات التي يتم التحكم فيها بشكل أفضل مع [Microsoft Defender لنقطة النهاية](microsoft-defender-endpoint.md)، والذي يمنحك تقارير مفصلة حول أحداث الوصول إلى المجلدات التي يتم التحكم فيها والكتل كجزء من [سيناريوهات التحقيق في التنبيه المعتادة](investigate-alerts.md).

> [!TIP]
> لا تنشئ كتل الوصول إلى المجلدات التي يتم التحكم فيها تنبيهات في [قائمة انتظار التنبيهات](alerts-queue.md). ومع ذلك، يمكنك عرض معلومات حول كتل الوصول إلى المجلدات التي يتم التحكم فيها في [طريقة عرض المخطط الزمني للجهاز](investigate-machines.md)، أثناء استخدام [التتبع المتقدم](advanced-hunting-overview.md)، أو مع [قواعد الكشف المخصصة](custom-detection-rules.md).

## <a name="how-does-controlled-folder-access-work"></a>كيف يعمل الوصول إلى المجلدات التي يتم التحكم فيها؟

يعمل الوصول إلى المجلدات الخاضعة للتحكم من خلال السماح للتطبيقات الموثوق بها بالوصول إلى المجلدات المحمية فقط. يتم تحديد المجلدات المحمية عند تكوين الوصول إلى المجلدات التي يتم التحكم فيها. عادة ما يتم تضمين المجلدات شائعة الاستخدام، مثل تلك المستخدمة للمستندات والصور والتنزيلات وما إلى ذلك، في قائمة المجلدات التي يتم التحكم فيها.

يعمل الوصول إلى المجلدات الخاضعة للرقابة مع قائمة بالتطبيات الموثوق بها. تعمل التطبيقات المضمنة في قائمة البرامج الموثوق بها كما هو متوقع. يتم منع التطبيقات غير المضمنة في القائمة من إجراء أي تغييرات على الملفات داخل المجلدات المحمية.

تتم إضافة التطبيقات إلى القائمة استنادا إلى انتشارها وسمعتها. تعتبر التطبيقات المنتشرة بشكل كبير في جميع أنحاء مؤسستك والتي لم تعرض أي سلوك يعتبر ضارا موثوقا بها. تتم إضافة هذه التطبيقات إلى القائمة تلقائيا.

يمكن أيضا إضافة التطبيقات يدويا إلى القائمة الموثوق بها باستخدام Configuration Manager أو Intune. يمكن تنفيذ إجراءات إضافية من مدخل Microsoft 365 Defender.

## <a name="why-controlled-folder-access-is-important"></a>ما أهمية الوصول إلى المجلدات التي يتم التحكم فيها

يعد الوصول إلى المجلدات الخاضعة للرقابة مفيدا بشكل خاص في المساعدة على حماية مستنداتك ومعلوماتك من [برامج الفدية الضارة](https://www.microsoft.com/wdsi/threats/ransomware). في هجوم برامج الفدية الضارة، يمكن تشفير ملفاتك وتثبيتها. مع وجود وصول متحكم به للمجلد، يظهر إعلام على الكمبيوتر حيث حاول تطبيق إجراء تغييرات على ملف في مجلد محمي. يمكنك [تخصيص الإعلام](attack-surface-reduction-rules-deployment-implement.md#customize-attack-surface-reduction-rules) باستخدام تفاصيل الشركة ومعلومات الاتصال. يمكنك أيضا تمكين القواعد بشكل فردي لتخصيص التقنيات التي تراقبها الميزة.

تتضمن [المجلدات المحمية](#review-controlled-folder-access-events-in-windows-event-viewer) مجلدات النظام الشائعة (بما في ذلك قطاعات التمهيد)، ويمكنك [إضافة المزيد من المجلدات](customize-controlled-folders.md#protect-additional-folders). يمكنك أيضا [السماح للتطبيقات](customize-controlled-folders.md#allow-specific-apps-to-make-changes-to-controlled-folders) بمنحها حق الوصول إلى المجلدات المحمية.

يمكنك استخدام [وضع التدقيق](audit-windows-defender.md) لتقييم كيفية تأثير الوصول المتحكم به إلى المجلدات على مؤسستك إذا تم تمكينه. يمكنك أيضا زيارة موقع ويب Windows Defender Test على [demo.wd.microsoft.com](https://demo.wd.microsoft.com?ocid=cx-wddocs-testground) لتأكيد عمل الميزة ومعرفة كيفية عملها.

> [!NOTE]
> تم إهمال الموقع التجريبي ل Defender لنقطة النهاية في demo.wd.microsoft.com وستتم إزالته في المستقبل.

يتم دعم الوصول إلى المجلدات التي يتم التحكم فيها على الإصدارات التالية من Windows:

- [Windows 10، الإصدار 1709 والإصدارات](/windows/whats-new/whats-new-windows-10-version-1709) الأحدث
- Windows 11
- Windows 2012 R2
- Windows 2016
- [Windows Server 2019](/windows-server/get-started-19/whats-new-19)
- Windows Server 2022

## <a name="windows-system-folders-are-protected-by-default"></a>Windows مجلدات النظام محمية بشكل افتراضي

Windows مجلدات النظام محمية بشكل افتراضي، إلى جانب عدة مجلدات أخرى:

تتضمن المجلدات المحمية مجلدات النظام الشائعة (بما في ذلك قطاعات التمهيد)، ويمكنك إضافة مجلدات إضافية. يمكنك أيضا السماح للتطبيقات بمنحها حق الوصول إلى المجلدات المحمية.  مجلدات أنظمة Windows المحمية بشكل افتراضي هي:

- `c:\Users\<username>\Documents`
- `c:\Users\Public\Documents`
- `c:\Users\<username>\Pictures`
- `c:\Users\Public\Pictures`
- `c:\Users\Public\Videos`
- `c:\Users\<username>\Videos`
- `c:\Users\<username>\Music`
- `c:\Users\Public\Music`
- `c:\Users\<username>\Favorites`

تظهر المجلدات الافتراضية في ملف تعريف المستخدم، ضمن **هذا الكمبيوتر.**
   > [!div class="mx-imgBorder"]
   > ![مجلدات الأنظمة الافتراضية Windows المحمية](images/defaultfolders.png)

> [!NOTE]
> يمكنك تكوين مجلدات إضافية كمحمية، ولكن لا يمكنك إزالة مجلدات النظام Windows المحمية بشكل افتراضي.

## <a name="requirements-for-controlled-folder-access"></a>متطلبات الوصول إلى المجلدات التي يتم التحكم فيها

يتطلب الوصول إلى المجلدات التي يتم التحكم فيها تمكين [الحماية برنامج الحماية من الفيروسات من Microsoft Defender في الوقت الحقيقي](configure-real-time-protection-microsoft-defender-antivirus.md).

## <a name="review-controlled-folder-access-events-in-the-microsoft-365-defender-portal"></a>مراجعة أحداث الوصول إلى المجلدات التي تم التحكم فيها في مدخل Microsoft 365 Defender

يوفر Defender لنقطة النهاية تقارير مفصلة عن الأحداث والكتل كجزء من [سيناريوهات التحقيق في التنبيه](investigate-alerts.md) في مدخل Microsoft 365 Defender؛ راجع [Microsoft Defender لنقطة النهاية في Microsoft 365 Defender](../defender/microsoft-365-security-center-mde.md).

يمكنك الاستعلام عن بيانات Microsoft Defender لنقطة النهاية باستخدام [التتبع المتقدم](advanced-hunting-overview.md). إذا كنت تستخدم [وضع التدقيق](audit-windows-defender.md)، يمكنك استخدام [التتبع المتقدم](advanced-hunting-overview.md) لمعرفة كيفية تأثير إعدادات الوصول إلى المجلدات التي يتم التحكم فيها على بيئتك إذا تم تمكينها.

مثال على الاستعلام:

```PowerShell
DeviceEvents
| where ActionType in ('ControlledFolderAccessViolationAudited','ControlledFolderAccessViolationBlocked')
```

## <a name="review-controlled-folder-access-events-in-windows-event-viewer"></a>مراجعة أحداث الوصول إلى المجلدات التي يتم التحكم فيها في Windows عارض الأحداث

يمكنك مراجعة سجل أحداث Windows للاطلاع على الأحداث التي يتم إنشاؤها عند التحكم في كتل الوصول إلى المجلدات (أو عمليات التدقيق) للتطبيق:

1. قم بتنزيل [حزمة التقييم](https://aka.ms/mp7z2w) واستخراج *الملفcfa-events.xml* إلى موقع يمكن الوصول إليه بسهولة على الجهاز.
2. اكتب **عارض الأحداث** في قائمة البدء لفتح Windows عارض الأحداث.
3. في اللوحة اليمنى، ضمن **"إجراءات"**، حدد **"استيراد طريقة عرض مخصصة"...**.
4. انتقل إلى المكان الذي قمت باستخراج *cfa-events.xml* وحدده. بدلا من ذلك، [انسخ XML مباشرة](event-views.md).
5. حدد **موافق**.

يعرض الجدول التالي الأحداث المتعلقة بالوصول إلى المجلدات التي يتم التحكم فيها:

<br/><br/>

|معرف الحدث|الوصف|
|---|---|
|5007|حدث عند تغيير الإعدادات|
|1124|حدث الوصول إلى المجلدات المتحكم فيها الذي تم تدقيقه|
|1123|حدث الوصول إلى المجلدات المتحكم فيها المحظور|

## <a name="view-or-change-the-list-of-protected-folders"></a>عرض قائمة المجلدات المحمية أو تغييرها

يمكنك استخدام تطبيق أمن Windows لعرض قائمة المجلدات المحمية بالوصول إلى المجلدات التي يتم التحكم فيها.

1. على جهازك Windows 10 أو Windows 11، افتح تطبيق أمن Windows.
2. حدد **الحماية من الفيروسات والمخاطر**.
3. ضمن **الحماية من برامج الفدية الضارة**، حدد **إدارة الحماية من برامج الفدية الضارة**.
4. إذا تم إيقاف تشغيل الوصول إلى المجلد الذي يتم التحكم فيه، فستحتاج إلى تشغيله. حدد **المجلدات المحمية**.
5. قم بتنفيذ أحد الخطوتين التاليين:
   - لإضافة مجلد، حدد **+ إضافة مجلد محمي**.
   - لإزالة مجلد، حدده، ثم حدد **"إزالة**".

> [!NOTE]
> [Windows مجلدات النظام](#windows-system-folders-are-protected-by-default) محمية بشكل افتراضي، ولا يمكنك إزالتها من القائمة.
