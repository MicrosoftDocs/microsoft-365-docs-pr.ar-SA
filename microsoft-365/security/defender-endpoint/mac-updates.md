---
title: نشر تحديثات Microsoft Defender لنقطة النهاية على Mac
description: التحكم في تحديثات Microsoft Defender لنقطة النهاية على Mac في بيئات المؤسسة.
keywords: microsoft، defender، Microsoft Defender لنقطة النهاية، mac، التحديثات، التوزيع
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: 4612c7ca68ab0b55fa2a2f28821cb5baef6ff6e9
ms.sourcegitcommit: 6c2ab5e8efe74d0dc2df610e2d9d2fdda8aaf074
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 05/25/2022
ms.locfileid: "65669331"
---
# <a name="deploy-updates-for-microsoft-defender-for-endpoint-on-macos"></a>نشر تحديثات Microsoft Defender لنقطة النهاية على macOS

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**ينطبق على:**

- [Microsoft Defender لنقطة النهاية على macOS](microsoft-defender-endpoint-mac.md)
- [الخطة 1 من Microsoft Defender لنقطة النهاية](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Defender for Endpoint الخطة 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> هل تريد تجربة Microsoft Defender لنقطة النهاية؟ [التسجيل للحصول على إصدار تجريبي مجاني.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

تنشر Microsoft تحديثات البرامج بانتظام لتحسين الأداء والأمان وتقديم ميزات جديدة.

لتحديث Microsoft Defender لنقطة النهاية على macOS، يتم استخدام برنامج يسمى التحديث التلقائي لبرامج Microsoft (MAU). بشكل افتراضي، يتحقق MAU تلقائيا من وجود تحديثات يوميا، ولكن يمكنك تغيير ذلك إلى أسبوعيا أو شهريا أو يدويا.

:::image type="content" source="images/MDATP-34-MAU.png" alt-text="ماو" lightbox="images/MDATP-34-MAU.png":::

إذا قررت نشر التحديثات باستخدام أدوات توزيع البرامج، يجب تكوين MAU للتحقق يدويا من تحديثات البرامج. يمكنك نشر التفضيلات لتكوين كيفية ووقت قيام MAU بالتحقق من وجود تحديثات لأجهزة Mac في مؤسستك.

## <a name="use-msupdate"></a>استخدام msupdate

يتضمن MAU أداة سطر الأوامر، تسمى *msupdate*، التي تم تصميمها لمسؤولي تكنولوجيا المعلومات بحيث يكون لديهم تحكم أكثر دقة عند تطبيق التحديثات. يمكن العثور على إرشادات حول كيفية استخدام هذه الأداة في [تحديث Office for Mac باستخدام msupdate](/deployoffice/mac/update-office-for-mac-using-msupdate).

في MAU، معرف التطبيق Microsoft Defender لنقطة النهاية على macOS هو *WDAV00*. لتنزيل آخر التحديثات ل Microsoft Defender لنقطة النهاية وتثبيتها على macOS، نفذ الأمر التالي من نافذة Terminal:

```dos
cd /Library/Application\ Support/Microsoft/MAU2.0/Microsoft\ AutoUpdate.app/Contents/MacOS
./msupdate --install --apps wdav00
```

## <a name="set-preferences-for-microsoft-autoupdate"></a>تعيين تفضيلات التحديث التلقائي لبرامج Microsoft

يصف هذا القسم التفضيلات الأكثر شيوعا التي يمكن استخدامها لتكوين MAU. يمكن نشر هذه الإعدادات كملف تعريف تكوين من خلال وحدة تحكم الإدارة التي تستخدمها مؤسستك. يظهر مثال لملف تعريف التكوين في المقاطع التالية.

### <a name="set-the-channel-name"></a>تعيين اسم القناة

تحدد القناة نوع التحديثات التي يتم تقديمها من خلال MAU ومعدل تكرارها. يمكن للأجهزة الموجودة `Beta` تجربة ميزات جديدة قبل أن تعمل الأجهزة في `Preview` و `Current`.

`Current` تحتوي القناة على الإصدار الأكثر استقرارا من المنتج.

> [!IMPORTANT]
> قبل الإصدار 4.29 من التحديث التلقائي لبرامج Microsoft، كان للقنوات أسماء مختلفة:
>
> - `Beta` تمت تسمية `InsiderFast` (الإصدار الأولي العاجل ل Insider)
> - `Preview` تمت تسمية `External` (الإصدار الآجل ل Insider)
> - `Current` تمت تسمية `Production`

> [!TIP]
> من أجل معاينة الميزات الجديدة وتقديم ملاحظات مبكرة، يوصى بتكوين بعض الأجهزة في مؤسستك إلى `Beta` أو `Preview`.

<br>

****

|قسم|قيمه|
|---|---|
|**المجال**|`com.microsoft.autoupdate2`|
|**المفتاح**|اسم القناة|
|**نوع البيانات**|سلسلة|
|**القيم المحتملة**|الإصدار بيتا <p> معاينه <p> الحاليه|
|||

> [!WARNING]
> يغير هذا الإعداد القناة لكافة التطبيقات التي يتم تحديثها من خلال التحديث التلقائي لبرامج Microsoft. لتغيير القناة فقط Microsoft Defender لنقطة النهاية على macOS، نفذ الأمر التالي بعد استبدال `[channel-name]` القناة المطلوبة:
>
> ```bash
> defaults write com.microsoft.autoupdate2 Applications -dict-add "/Applications/Microsoft Defender.app" " { 'Application ID' = 'WDAV00' ; 'App Domain' = 'com.microsoft.wdav' ; LCID = 1033 ; ChannelName = '[channel-name]' ; }"
> ```

### <a name="set-update-check-frequency"></a>تعيين تكرار التحقق من التحديث

تغيير عدد مرات بحث MAU عن التحديثات.

<br>

****

|قسم|قيمه|
|---|---|
|**المجال**|`com.microsoft.autoupdate2`|
|**المفتاح**|UpdateCheckFrequency|
|**نوع البيانات**|صحيح|
|**القيمة الافتراضية**|720 (دقيقة)|
|**التعليق**|يتم تعيين هذه القيمة بالدقائق.|
|||

### <a name="change-how-mau-interacts-with-updates"></a>تغيير كيفية تفاعل MAU مع التحديثات

تغيير كيفية بحث MAU عن التحديثات.

<br>

****

|قسم|قيمه|
|---|---|
|**المجال**|`com.microsoft.autoupdate2`|
|**المفتاح**|HowToCheck|
|**نوع البيانات**|سلسلة|
|**القيم المحتملة**|دليل <p> التحديد التلقائي <p> التحميل التلقائي|
|**التعليق**|لاحظ أن AutomaticDownload سيقوم بتنزيل وتثبيت بصمت إذا أمكن.|
|||

### <a name="change-whether-the-check-for-updates-button-is-enabled"></a>تغيير ما إذا كان الزر "التحقق من وجود تحديثات" ممكنا

تغيير ما إذا كان سيتمكن المستخدمون المحليون من النقر فوق الخيار "التحقق من وجود تحديثات" في واجهة مستخدم التحديث التلقائي لبرامج Microsoft.

<br>

****

|قسم|قيمه|
|---|---|
|**المجال**|`com.microsoft.autoupdate2`|
|**المفتاح**|EnableCheckForUpdatesButton|
|**نوع البيانات**|منطقي|
|**القيم المحتملة**|صواب (افتراضي) <p> كاذبه|
|||

### <a name="disable-insider-checkbox"></a>تعطيل خانة الاختيار Insider

تعيين إلى true لجعل "الانضمام إلى Office برنامج Insider..." خانة الاختيار غير متوفرة / رمادية للمستخدمين.

<br>

****

|قسم|قيمه|
|---|---|
|**المجال**|`com.microsoft.autoupdate2`|
|**المفتاح**|DisableInsiderCheckbox|
|**نوع البيانات**|منطقي|
|**القيم المحتملة**|خطأ (افتراضي) <p> صحيح|
|||

### <a name="limit-the-telemetry-that-is-sent-from-mau"></a>تحديد بيانات تتبع الاستخدام التي يتم إرسالها من MAU

تعيين إلى خطأ لإرسال الحد الأدنى من بيانات كشف أخطاء الاتصال، وعدم استخدام التطبيق، وعدم وجود تفاصيل البيئة.

<br>

****

|قسم|قيمه|
|---|---|
|**المجال**|`com.microsoft.autoupdate2`|
|**المفتاح**|SendAllTelemetryEnabled|
|**نوع البيانات**|منطقي|
|**القيم المحتملة**|صواب (افتراضي) <p> كاذبه|
|||

## <a name="example-configuration-profile"></a>مثال على ملف تعريف التكوين

يتم استخدام ملف تعريف التكوين التالي من أجل:

- وضع الجهاز في قناة الإنتاج
- تنزيل التحديثات وتثبيتها تلقائيا
- تمكين الزر "التحقق من وجود تحديثات" في واجهة المستخدم
- السماح للمستخدمين على الجهاز بالتسجيل في قنوات Insider

> [!WARNING]
> التكوين أدناه هو تكوين مثال ولا ينبغي استخدامه في الإنتاج دون مراجعة مناسبة للإعدادات وخياط التكوينات.

> [!TIP]
> من أجل معاينة الميزات الجديدة وتقديم ملاحظات مبكرة، يوصى بتكوين بعض الأجهزة في مؤسستك إلى `Beta` أو `Preview`.

### <a name="jamf"></a>JAMF

```XML
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
<plist version="1.0">
<dict>
    <key>ChannelName</key>
    <string>Production</string>
    <key>HowToCheck</key>
    <string>AutomaticDownload</string>
    <key>EnableCheckForUpdatesButton</key>
    <true/>
    <key>DisableInsiderCheckbox</key>
    <false/>
    <key>SendAllTelemetryEnabled</key>
    <true/>
</dict>
</plist>
```

### <a name="intune"></a>Intune

```XML
<?xml version="1.0" encoding="utf-8"?>
<!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
<plist version="1">
    <dict>
        <key>PayloadUUID</key>
        <string>B762FF60-6ACB-4A72-9E72-459D00C936F3</string>
        <key>PayloadType</key>
        <string>Configuration</string>
        <key>PayloadOrganization</key>
        <string>Microsoft</string>
        <key>PayloadIdentifier</key>
        <string>com.microsoft.autoupdate2</string>
        <key>PayloadDisplayName</key>
        <string>Microsoft AutoUpdate settings</string>
        <key>PayloadDescription</key>
        <string>Microsoft AutoUpdate configuration settings</string>
        <key>PayloadVersion</key>
        <integer>1</integer>
        <key>PayloadEnabled</key>
        <true/>
        <key>PayloadRemovalDisallowed</key>
        <true/>
        <key>PayloadScope</key>
        <string>System</string>
        <key>PayloadContent</key>
        <array>
            <dict>
            <key>PayloadUUID</key>
            <string>5A6F350A-CC2C-440B-A074-68E3F34EBAE9</string>
            <key>PayloadType</key>
            <string>com.microsoft.autoupdate2</string>
            <key>PayloadOrganization</key>
            <string>Microsoft</string>
            <key>PayloadIdentifier</key>
            <string>com.microsoft.autoupdate2</string>
            <key>PayloadDisplayName</key>
            <string>Microsoft AutoUpdate configuration settings</string>
            <key>PayloadDescription</key>
            <string/>
            <key>PayloadVersion</key>
            <integer>1</integer>
            <key>PayloadEnabled</key>
            <true/>
            <key>ChannelName</key>
            <string>Production</string>
            <key>HowToCheck</key>
            <string>AutomaticDownload</string>
            <key>EnableCheckForUpdatesButton</key>
            <true/>
            <key>DisableInsiderCheckbox</key>
            <false/>
            <key>SendAllTelemetryEnabled</key>
            <true/>
            </dict>
        </array>
    </dict>
</plist>
```

لتكوين MAU، يمكنك نشر ملف تعريف التكوين هذا من أداة الإدارة التي تستخدمها مؤسستك:

- من JAMF، قم بتحميل ملف تعريف التكوين هذا وتعيين "مجال التفضيل" إلى *com.microsoft.autoupdate2*.
- من Intune، قم بتحميل ملف تعريف التكوين هذا وتعيين اسم ملف تعريف التكوين المخصص إلى *com.microsoft.autoupdate2*.

## <a name="resources"></a>الموارد

- [مرجع msupdate](/deployoffice/mac/update-office-for-mac-using-msupdate)
