---
title: التحكم في الجهاز ل macOS
description: تعرف على كيفية تكوين Microsoft Defender ل Endpoint على Mac لتقليل التهديدات من التخزين القابل للإزالة مثل أجهزة USB.
keywords: microsoft، defender، Microsoft Defender ل Endpoint، mac، الجهاز، التحكم، usb، قابل للإزالة، الوسائط
ms.prod: m365-security
ms.mktglfcycl: security
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
ms.openlocfilehash: 5cb41b0bd3f185237055daa2d282f0a1d6975a49
ms.sourcegitcommit: 6e90baef421ae06fd790b0453d3bdbf624b7f9c0
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 02/12/2022
ms.locfileid: "63569842"
---
# <a name="device-control-for-macos"></a>التحكم في الجهاز ل macOS

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**
- [خطة Microsoft Defender لنقطة النهاية 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> هل تريد تجربة Microsoft Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

## <a name="requirements"></a>المتطلبات

عنصر تحكم الجهاز ل macOS له المتطلبات الأساسية التالية:

> [!div class="checklist"]
>
> - استحقاق Microsoft Defender لنقطة النهاية (يمكن أن يكون تجريبيا)
> - الحد الأدنى من إصدار نظام التشغيل: macOS 11 أو إصدار أحدث
> - الحد الأدنى للإصدار: 101.34.20

## <a name="device-control-policy"></a>نهج التحكم في الجهاز

لتكوين التحكم في الجهاز ل macOS، يجب إنشاء نهج يصف القيود التي تريد وضعها داخل مؤسستك.

يتم تضمين نهج التحكم في الجهاز في ملف تعريف التكوين المستخدم لتكوين كل إعدادات المنتج الأخرى. لمزيد من المعلومات، راجع [بنية ملف تعريف التكوين](mac-preferences.md#configuration-profile-structure).

ضمن ملف تعريف التكوين، يتم تعريف نهج التحكم في الجهاز في المقطع التالي:

<br>

****

|مقطع|القيمة|
|---|---|
|**المجال**|`com.microsoft.wdav`|
|**المفتاح**|deviceControl|
|**نوع البيانات**|القاموس (التفضيل المتداخل)|
|**التعليقات**|راجع المقاطع التالية للحصول على وصف لمحتويات القاموس.|
|

يمكن استخدام نهج التحكم في الجهاز من أجل:

- [تخصيص هدف URL للإشعارات التي يتم رفعها بواسطة عنصر تحكم الجهاز](#customize-url-target-for-notifications-raised-by-device-control)
- [السماح بالأجهزة القابلة للإزالة أو حظرها](#allow-or-block-removable-devices)

### <a name="customize-url-target-for-notifications-raised-by-device-control"></a>تخصيص هدف URL للإشعارات التي يتم رفعها بواسطة عنصر تحكم الجهاز

عندما يتم فرض نهج التحكم في الجهاز الذي وضعته على جهاز (على سبيل المثال، يكون الوصول إلى جهاز وسائط قابل للإزالة مقيدا)، يتم عرض إعلام للمستخدم.

![إعلام التحكم في الجهاز.](images/mac-device-control-notification.png)

عندما ينقر المستخدمون فوق هذا الإعلام، يتم فتح صفحة ويب في المستعرض الافتراضي. يمكنك تكوين عنوان URL الذي يتم فتحه عندما ينقر المستخدمون فوق الإعلام.

<br>

****

|مقطع|القيمة|
|---|---|
|**المجال**|`com.microsoft.wdav`|
|**المفتاح**|navigationTarget|
|**نوع البيانات**|سلسلة|
|**التعليقات**|إذا لم يكن معرفا، يستخدم المنتج عنوان URL افتراضيا يشير إلى صفحة عامة تشرح الإجراء الذي اتخذه المنتج.|
|

### <a name="allow-or-block-removable-devices"></a>السماح بالأجهزة القابلة للإزالة أو حظرها

يتم استخدام قسم الوسائط القابلة للإزالة من نهج التحكم في الجهاز لتقييد الوصول إلى الوسائط القابلة للإزالة.

> [!NOTE]
> يتم حاليا دعم الأنواع التالية من الوسائط القابلة للإزالة ويمكن تضمينها في النهج: أجهزة تخزين USB.

<br>

****

|مقطع|القيمة|
|---|---|
|**المجال**|`com.microsoft.wdav`|
|**المفتاح**|removableMediaPolicy|
|**نوع البيانات**|القاموس (التفضيل المتداخل)|
|**التعليقات**|راجع المقاطع التالية للحصول على وصف لمحتويات القاموس.|
|

هذا القسم من النهج هرمي، مما يسمح بأقصى قدر من المرونة ويغطي مجموعة واسعة من حالات الاستخدام. في المستوى الأعلى، يوجد موردون، يتم تعريفهم بواسطة معرف المورد. بالنسبة لكل مورد، توجد منتجات، يتم تعريفها بواسطة معرف المنتج. وأخيرا، توجد أرقام تسلسلية تشير إلى أجهزة معينة لكل منتج.

```text
|-- policy top level
    |-- vendor 1
        |-- product 1
            |-- serial number 1
            ...
            |-- serial number N
        ...
        |-- product N
    ...
    |-- vendor N
```

للحصول على معلومات حول كيفية العثور على معرفات الجهاز، راجع [البحث عن معرفات الجهاز](#look-up-device-identifiers).

يتم تقييم النهج من الإدخال الأكثر تحديدا إلى الإدخال الأكثر عمومية. بمعنى أنه عند توصيل جهاز، يحاول المنتج العثور على التطابق الأكثر تحديدا في النهج لكل جهاز وسائط قابل للإزالة وتطبيق الأذونات على هذا المستوى. إذا لم يكن هناك تطابق، يتم تطبيق أفضل تطابق بعد ذلك، كل ذلك إلى الإذن المحدد في المستوى الأعلى، وهو الإعداد الافتراضي عندما لا يتطابق الجهاز مع أي إدخال آخر في النهج.

#### <a name="policy-enforcement-level"></a>مستوى فرض النهج

ضمن مقطع الوسائط القابلة للإزالة، يوجد خيار لتعيين مستوى التنفيذ، الذي يمكن أن يستغرق إحدى القيم التالية:

- `audit` - ضمن مستوى التنفيذ هذا، إذا كان الوصول إلى جهاز مقيدا، فيعرض إعلام للمستخدم، ومع ذلك يمكن استخدام الجهاز. يمكن أن يكون مستوى التنفيذ هذا مفيدا لتقييم فعالية النهج.
- `block` - ضمن مستوى التنفيذ هذا، تقتصر العمليات التي يمكن للمستخدم تنفيذها على الجهاز على ما تم تعريفه في النهج. علاوة على ذلك، يتم رفع إعلام للمستخدم.

> [!NOTE]
> بشكل افتراضي، يتم تعيين مستوى التنفيذ إلى `audit`.

<br>

****

|مقطع|القيمة|
|---|---|
|**المجال**|`com.microsoft.wdav`|
|**المفتاح**|enforcementLevel|
|**نوع البيانات**|سلسلة|
|**القيم المحتملة**|التدقيق (افتراضي) <p> حظر|
|

#### <a name="default-permission-level"></a>مستوى الأذونات الافتراضي

في المستوى الأعلى من مقطع الوسائط القابلة للإزالة، يمكنك تكوين مستوى الأذونات الافتراضي للأجهزة التي لا تتطابق مع أي شيء آخر في النهج.

يمكن تعيين هذا الإعداد إلى:

- `none` - لا يمكن تنفيذ أي عمليات على الجهاز
- مجموعة من القيم التالية:
  - `read` - يسمح بعمليات القراءة على الجهاز
  - `write` - يسمح بعمليات الكتابة على الجهاز
  - `execute` - يسمح بتنفيذ العمليات على الجهاز

> [!NOTE]
> إذا `none` كان موجودا على مستوى الأذونات، سيتم تجاهل أي أذونات أخرى (`write``read``execute`أو أو ) .
>
> يشير `execute` الإذن إلى تنفيذ الثنائيات Mach-O فقط. ولا يتضمن تنفيذ البرامج النصية أو أنواع أخرى من التحميلات.

<br>

****

|مقطع|القيمة|
|---|---|
|**المجال**|`com.microsoft.wdav`|
|**المفتاح**|إذن|
|**نوع البيانات**|صفيف من السلاسل|
|**القيم المحتملة**|بلا <p> قراءة <p> كتابة <p> تنفيذ|
|

#### <a name="restrict-removable-media-by-vendor-product-and-serial-number"></a>تقييد الوسائط القابلة للإزالة حسب المورد والمنتج والرقم التسلسلي

كما هو موضح في [السماح](#allow-or-block-removable-devices) بالأجهزة القابلة للإزالة أو حظرها، يمكن تعريف الوسائط القابلة للإزالة مثل أجهزة USB بواسطة معرف المورد ومعرف المنتج والرقم التسلسلي.

في المستوى الأعلى لنهج الوسائط القابلة للإزالة، يمكنك بشكل اختياري تحديد قيود أكثر تفردا على مستوى المورد.

يحتوي `vendors` القاموس على إدخال واحد أو أكثر، مع تحديد كل إدخال بواسطة معرف المورد.

<br>

****

|مقطع|القيمة|
|---|---|
|**المجال**|`com.microsoft.wdav`|
|**المفتاح**|موردون|
|**نوع البيانات**|القاموس (التفضيل المتداخل)|
|

لكل مورد، يمكنك تحديد مستوى الأذونات المطلوب للأجهزة من ذلك المورد.

<br>

****

|مقطع|القيمة|
|---|---|
|**المجال**|`com.microsoft.wdav`|
|**المفتاح**|إذن|
|**نوع البيانات**|صفيف من السلاسل|
|**القيم المحتملة**|نفس مستوى [الأذونات الافتراضي](#default-permission-level)|
|

علاوة على ذلك، يمكنك اختياريا تحديد مجموعة المنتجات التابعة لهذا المورد الذي تم تعريف أذونات أكثر تحديدا لها. يحتوي `products` القاموس على إدخال واحد أو أكثر، مع تحديد كل إدخال بواسطة معرف المنتج.

<br>

****

|مقطع|القيمة|
|---|---|
|**المجال**|`com.microsoft.wdav`|
|**المفتاح**|المنتجات|
|**نوع البيانات**|القاموس (التفضيل المتداخل)|
|

لكل منتج، يمكنك تحديد مستوى الأذونات المطلوب لهذا المنتج.

<br>

****

|مقطع|القيمة|
|---|---|
|**المجال**|`com.microsoft.wdav`|
|**المفتاح**|إذن|
|**نوع البيانات**|صفيف من السلاسل|
|**القيم المحتملة**|نفس مستوى [الأذونات الافتراضي](#default-permission-level)|
|

علاوة على ذلك، يمكنك تحديد مجموعة اختيارية من الأرقام التسلسلية التي يتم تعريف أذونات أكثر تحديدا لها.

يحتوي `serialNumbers` القاموس على إدخال واحد أو أكثر، مع تحديد كل إدخال بواسطة الرقم التسلسلي.

<br>

****

|مقطع|القيمة|
|---|---|
|**المجال**|`com.microsoft.wdav`|
|**المفتاح**|serialNumbers|
|**نوع البيانات**|القاموس (التفضيل المتداخل)|
|

لكل رقم تسلسلي، يمكنك تحديد مستوى الأذونات المطلوب.

<br>

****

|مقطع|القيمة|
|---|---|
|**المجال**|`com.microsoft.wdav`|
|**المفتاح**|إذن|
|**نوع البيانات**|صفيف من السلاسل|
|**القيم المحتملة**|نفس مستوى [الأذونات الافتراضي](#default-permission-level)|
|

#### <a name="example-device-control-policy"></a>مثال على نهج التحكم في الجهاز

يوضح المثال التالي كيفية دمج كل المفاهيم أعلاه في نهج التحكم في الجهاز. في المثال التالي، لاحظ الطبيعة الهيكلية لنهج الوسائط القابلة للإزالة.

```xml
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
<plist version="1.0">
<dict>
    <key>deviceControl</key>
    <dict>
        <key>navigationTarget</key>
        <string>[custom URL for notifications]</string>
        <key>removableMediaPolicy</key>
        <dict>
            <key>enforcementLevel</key>
            <string>[enforcement level]</string> <!-- audit / block -->
            <key>permission</key>
            <array>
                <string>[permission]</string> <!-- none / read / write / execute -->
                <!-- other permissions -->
            </array>
            <key>vendors</key>
            <dict>
                <key>[vendor id]</key>
                <dict>
                    <key>permission</key>
                    <array>
                        <string>[permission]</string> <!-- none / read / write / execute -->
                        <!-- other permissions -->
                    </array>
                    <key>products</key>
                    <dict>
                        <key>[product id]</key>
                        <dict>
                            <key>permission</key>
                            <array>
                                <string>[permission]</string> <!-- none / read / write / execute -->
                                <!-- other permissions -->
                            </array>
                            <key>serialNumbers</key>
                            <dict>
                                <key>[serial-number]</key>
                                <array>
                                    <string>[permission]</string> <!-- none / read / write / execute -->
                                    <!-- other permissions -->
                                </array>
                                <!-- other serial numbers -->
                            </dict>
                        </dict>
                        <!-- other products -->
                    </dict>
                </dict>
                <!-- other vendors -->
            </dict>
        </dict>
    </dict>
</dict>
</plist>
```

لقد قمنا بضم المزيد من الأمثلة حول سياسات التحكم في الجهاز في المستندات التالية:

- [أمثلة حول سياسات التحكم في الجهاز ل Intune](mac-device-control-intune.md)
- [أمثلة حول سياسات التحكم في الجهاز ل JAMF](mac-device-control-jamf.md)

#### <a name="look-up-device-identifiers"></a>البحث عن معرفات الجهاز

للعثور على المعرف المورد ومعرف المنتج والرقم التسلسلي لجهاز USB:

1. سجل الدخول إلى جهاز Mac.
1. قم بتوصيل جهاز USB الذي تريد البحث عن المعرف الخاص به.
1. في قائمة المستوى الأعلى من macOS، حدد **حول هذا Mac**.

    ![حول جهاز Mac هذا.](images/mac-device-control-lookup-1.png)

1. حدد **تقرير النظام**.

    ![تقرير النظام.](images/mac-device-control-lookup-2.png)

1. من العمود الأيمن، حدد **USB**.

    ![عرض جميع أجهزة USB.](images/mac-device-control-lookup-3.png)

1. ضمن **شجرة أجهزة USB**، انتقل إلى جهاز USB الذي قمت بتوصيله.

    ![تفاصيل جهاز USB.](images/mac-device-control-lookup-4.png)

1. يتم عرض "معرِّف المورد" و"معرِّف المنتج" و"الرقم التسلسلي". عند إضافة "معرِّف المورد" و"معرِّف المنتج" إلى نهج الوسائط القابلة للإزالة، يجب إضافة الجزء بعد .`0x` على سبيل المثال، في الصورة أدناه، يكون "مورد" `1000` هو "مورد" وم ID المنتج هو `090c`.

#### <a name="discover-usb-devices-in-your-organization"></a>اكتشاف أجهزة USB في مؤسستك

يمكنك عرض أحداث تغيير الصوت والدفع والتركيب التي تنشأ من أجهزة USB في Microsoft Defender للصيد المتقدم لنقطة النهاية. يمكن أن تكون هذه الأحداث مفيدة لتحديد نشاط استخدام مريب أو إجراء عمليات تحقيق داخلية.

```bash
DeviceEvents
    | where ActionType == "UsbDriveMounted" or ActionType == "UsbDriveUnmounted" or ActionType == "UsbDriveDriveLetterChanged"
    | where DeviceId == "<device ID>"
```

## <a name="device-control-policy-deployment"></a>نشر نهج التحكم في الجهاز

يجب تضمين نهج التحكم في الجهاز بجانب إعدادات المنتج الأخرى، كما هو موضح في تعيين التفضيلات ل [Microsoft Defender ل Endpoint على macOS](mac-preferences.md).

يمكن نشر ملف التعريف هذا باستخدام الإرشادات المدرجة في [نشر ملف تعريف التكوين](mac-preferences.md#configuration-profile-deployment).

## <a name="troubleshooting-tips"></a>تلميحات استكشاف الأخطاء وإصلاحها

بعد دفع ملف تعريف التكوين عبر Intune أو JAMF، يمكنك التحقق مما إذا كان المنتج قد انتقه بنجاح عن طريق تشغيل الأمر التالي من المحطة الطرفية:

```bash
mdatp device-control removable-media policy list
```

سيطبع هذا الأمر حتى يتم إخراج نهج التحكم في الجهاز الذي يستخدمه المنتج بشكل قياسي. `Policy is empty`في حالة طباعة هذا ، تأكد من أنه (أ) تم بالفعل دفع ملف تعريف التكوين إلى جهازك من وحدة تحكم الإدارة، و(ب) هو نهج صالح للتحكم في الجهاز، كما هو موضح في هذا المستند.

على جهاز تم تسليم النهج فيه بنجاح وحيث يوجد جهاز واحد أو أكثر موصل، يمكنك تشغيل الأمر التالي لقائمة جميع الأجهزة والأذونات الفعالة المطبقة عليها.

```bash
mdatp device-control removable-media devices list
```

مثال الإخراج:

```Output
.Device(s)
|-o Name: Untitled 1, Permission ["read", "execute"]
| |-o Vendor: General "fff0"
| |-o Product: USB Flash Disk "1000"
| |-o Serial number: "04ZSSMHI2O7WBVOA"
| |-o Mount point: "/Volumes/TESTUSB"
```

في المثال أعلاه `read` `execute` ، لا يوجد سوى جهاز وسائط واحد قابل للإزالة موصول و لديه وأذونات، وفقا لن نهج التحكم في الجهاز الذي تم تسليمه إلى الجهاز.

## <a name="related-topics"></a>المواضيع ذات الصلة

- [أمثلة حول سياسات التحكم في الجهاز ل Intune](mac-device-control-intune.md)
- [أمثلة حول سياسات التحكم في الجهاز ل JAMF](mac-device-control-jamf.md)
