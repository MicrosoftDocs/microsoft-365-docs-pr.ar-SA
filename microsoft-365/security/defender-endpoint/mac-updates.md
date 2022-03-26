---
title: نشر تحديثات ل Microsoft Defender لنقطة النهاية على Mac
description: يمكنك التحكم في تحديثات Microsoft Defender لنقطة النهاية على Mac في بيئات المؤسسات.
keywords: microsoft، defender، Microsoft Defender ل Endpoint، mac، التحديثات، النشر
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
ms.openlocfilehash: ceff362daeb2054b6037ea0eecbeafbb9dbed4f3
ms.sourcegitcommit: 6e90baef421ae06fd790b0453d3bdbf624b7f9c0
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 02/12/2022
ms.locfileid: "63571515"
---
# <a name="deploy-updates-for-microsoft-defender-for-endpoint-on-macos"></a>نشر تحديثات ل Microsoft Defender ل Endpoint على macOS

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**ينطبق على:**

- [Microsoft Defender ل Endpoint على macOS](microsoft-defender-endpoint-mac.md)
- [خطة Microsoft Defender لنقطة النهاية 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> هل تريد تجربة Microsoft Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

تنشر Microsoft تحديثات البرامج بشكل منتظم لتحسين الأداء والأمان وتقديم ميزات جديدة.

لتحديث Microsoft Defender ل Endpoint على macOS، يتم استخدام برنامج يسمى التحديث التلقائي ل Microsoft (MAU). بشكل افتراضي، يتحقق MAU تلقائيا من وجود تحديثات يوميا، ولكن يمكنك تغيير ذلك إلى أسبوعيا أو شهريا أو يدويا.

![لقطة شاشة ل MAU.](images/MDATP-34-MAU.png)

إذا قررت نشر التحديثات باستخدام أدوات توزيع البرامج، يجب تكوين MAU للتحقق يدويا من وجود تحديثات البرامج. يمكنك نشر التفضيلات لتكوين كيفية و متى يتحقق MAU من وجود تحديثات ل Mac في مؤسستك.

## <a name="use-msupdate"></a>استخدام msupdate

تتضمن MAU أداة سطر الأوامر، تسمى *msupdate*، تم تصميمها لمسؤولي تكنولوجيا المعلومات بحيث يكون لديهم تحكم أكثر دقة في وقت تطبيق التحديثات. يمكن العثور على إرشادات حول كيفية استخدام هذه الأداة في [تحديث Office for Mac باستخدام msupdate](/deployoffice/mac/update-office-for-mac-using-msupdate).

في MAU، معرف التطبيق ل Microsoft Defender ل Endpoint على macOS هو *WDAV00*. لتنزيل آخر التحديثات ل Microsoft Defender ل Endpoint وتثبيتها على macOS، قم بتنفيذ الأمر التالي من نافذة المحطة الطرفية:

```dos
./msupdate --install --apps wdav00
```

## <a name="set-preferences-for-microsoft-autoupdate"></a>تعيين التفضيلات ل Microsoft AutoUpdate

يصف هذا القسم التفضيلات الأكثر شيوعا التي يمكن استخدامها لتكوين MAU. يمكن نشر هذه الإعدادات كملف تعريف تكوين من خلال وحدة تحكم الإدارة التي تستخدمها المؤسسة. يظهر مثال لملف تعريف التكوين في المقاطع التالية.

### <a name="set-the-channel-name"></a>تعيين اسم القناة

تحدد القناة نوع التحديثات التي يتم تقديمها من خلال MAU و مدى تكرارها. يمكن للأجهزة `Beta` في تجربة ميزات جديدة قبل الأجهزة في `Preview` و `Current`.

تحتوي `Current` القناة على الإصدار الأكثر استقرارا من المنتج.

> [!IMPORTANT]
> قبل الإصدار 4.29 من Microsoft AutoUpdate، كان للقنوات أسماء مختلفة:
>
> - `Beta` تم تسميته `InsiderFast` (Fast Insider)
> - `Preview` تم تسميته `External` (بطيء ل Insider)
> - `Current` تم تسميته `Production`

> [!TIP]
> من أجل معاينة الميزات الجديدة وتقديم الملاحظات المبكرة، من المستحسن تكوين بعض الأجهزة في المؤسسة إلى `Beta` أو `Preview`.

<br>

****

|مقطع|القيمة|
|---|---|
|**المجال**|`com.microsoft.autoupdate2`|
|**المفتاح**|ChannelName|
|**نوع البيانات**|سلسلة|
|**القيم المحتملة**|الإصدار بيتا <p> معاينة <p> الحالي|
|||

> [!WARNING]
> يغير هذا الإعداد القناة لجميع التطبيقات التي يتم تحديثها من خلال التحديث التلقائي ل Microsoft. لتغيير القناة ل Microsoft Defender for Endpoint على macOS `[channel-name]` فقط، نفذ الأمر التالي بعد استبدال القناة المطلوبة:
>
> ```bash
> defaults write com.microsoft.autoupdate2 Applications -dict-add "/Applications/Microsoft Defender.app" " { 'Application ID' = 'WDAV00' ; 'App Domain' = 'com.microsoft.wdav' ; LCID = 1033 ; ChannelName = '[channel-name]' ; }"
> ```

### <a name="set-update-check-frequency"></a>تعيين تكرار التحقق من التحديث

تغيير عدد مرات بحث MAU عن التحديثات.

<br>

****

|مقطع|القيمة|
|---|---|
|**المجال**|`com.microsoft.autoupdate2`|
|**المفتاح**|UpdateCheckFrequency|
|**نوع البيانات**|عدد صحيح|
|**القيمة الافتراضية**|720 (دقائق)|
|**تعليق**|يتم تعيين هذه القيمة بالدقائق.|
|||

### <a name="change-how-mau-interacts-with-updates"></a>تغيير كيفية تفاعل MAU مع التحديثات

تغيير طريقة بحث MAU عن التحديثات.

<br>

****

|مقطع|القيمة|
|---|---|
|**المجال**|`com.microsoft.autoupdate2`|
|**المفتاح**|HowToCheck|
|**نوع البيانات**|سلسلة|
|**القيم المحتملة**|يدوي <p> AutomaticCheck <p> AutomaticDownload|
|**تعليق**|لاحظ أن AutomaticDownload سيتم تنزيله وتثبيته بصمت إذا أمكن.|
|||

### <a name="change-whether-the-check-for-updates-button-is-enabled"></a>تغيير ما إذا كان الزر "التحقق من وجود تحديثات" ممكنا أم لا

تغيير ما إذا كان يمكن للمستخدمين المحليين النقر فوق الخيار "التحقق من وجود تحديثات" في واجهة مستخدم التحديث التلقائي من Microsoft.

<br>

****

|مقطع|القيمة|
|---|---|
|**المجال**|`com.microsoft.autoupdate2`|
|**المفتاح**|EnableCheckForUpdatesButton|
|**نوع البيانات**|منطقي|
|**القيم المحتملة**|True (افتراضي) <p> خطأ|
|||

### <a name="disable-insider-checkbox"></a>تعطيل خانة الاختيار Insider

تعيين إلى true لجعل "الانضمام إلى Office Insider..." خانة الاختيار غير متوفرة / باللون الرمادي للمستخدمين.

<br>

****

|مقطع|القيمة|
|---|---|
|**المجال**|`com.microsoft.autoupdate2`|
|**المفتاح**|DisableInsiderCheckbox|
|**نوع البيانات**|منطقي|
|**القيم المحتملة**|False (افتراضي) <p> True|
|||

### <a name="limit-the-telemetry-that-is-sent-from-mau"></a>الحد من بيانات التهية المرسلة من MAU

تعيين إلى خطأ لإرسال الحد الأدنى من بيانات دقات القلب، ولا يتم استخدام التطبيق، ولا تفاصيل البيئة.

<br>

****

|مقطع|القيمة|
|---|---|
|**المجال**|`com.microsoft.autoupdate2`|
|**المفتاح**|SendAllTelemetryEnabled|
|**نوع البيانات**|منطقي|
|**القيم المحتملة**|True (افتراضي) <p> خطأ|
|||

## <a name="example-configuration-profile"></a>مثال لملف تعريف التكوين

يتم استخدام ملف تعريف التكوين التالي ل:

- وضع الجهاز في قناة الإنتاج
- تنزيل التحديثات وتثبيتها تلقائيا
- تمكين الزر "التحقق من وجود تحديثات" في واجهة المستخدم
- السماح للمستخدمين على الجهاز بالتسجيل في قنوات Insider

> [!WARNING]
> التكوين أدناه هو تكوين مثال ويجب عدم استخدامه في الإنتاج بدون مراجعة الإعدادات بشكل صحيح وضبط التكوينات.

> [!TIP]
> من أجل معاينة الميزات الجديدة وتقديم الملاحظات المبكرة، من المستحسن تكوين بعض الأجهزة في المؤسسة إلى `Beta` أو `Preview`.

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

لتكوين MAU، يمكنك نشر ملف تعريف التكوين هذا من أداة الإدارة التي تستخدمها المؤسسة:

- من JAMF، قم بتحميل ملف تعريف التكوين هذا ثم قم بتعيين مجال التفضيل إلى *com.microsoft.autoupdate2*.
- من Intune، قم بتحميل ملف تعريف التكوين هذا ثم قم بتعيين اسم ملف تعريف التكوين المخصص إلى *com.microsoft.autoupdate2*.

## <a name="resources"></a>الموارد

- [مرجع msupdate](/deployoffice/mac/update-office-for-mac-using-msupdate)
