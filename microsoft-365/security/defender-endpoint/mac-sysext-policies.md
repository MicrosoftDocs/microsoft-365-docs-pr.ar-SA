---
title: ملفات تعريف التكوين الجديدة ل macOS Catalina والإصدارات الأحدث من macOS
description: يصف هذا الموضوع التغييرات التي يجب إدخالها للاستفادة من ملحقات النظام، التي تكون بديلا لملحقات kernel على macOS Catalina والإصدارات الأحدث من macOS.
keywords: microsoft، defender، Microsoft Defender ل Endpoint، mac، kernel، النظام، الملحقات، catalina
search.product: eADQiWindows 10XVcnh
search.appverid: met150
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
ROBOTS: noindex,nofollow
ms.technology: mde
ms.openlocfilehash: 0cdf60708e84b0972099330d48f19b22d26766ba
ms.sourcegitcommit: 6e90baef421ae06fd790b0453d3bdbf624b7f9c0
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 02/12/2022
ms.locfileid: "63570722"
---
# <a name="new-configuration-profiles-for-macos-catalina-and-newer-versions-of-macos"></a>ملفات تعريف التكوين الجديدة ل macOS Catalina والإصدارات الأحدث من macOS

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**
- [خطة Microsoft Defender لنقطة النهاية 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> هل تريد تجربة Microsoft Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

بالمحاذاة مع تطور macOS، نقوم بإعداد Microsoft Defender ل Endpoint على تحديث macOS الذي يعتمد ملحقات النظام بدلا من ملحقات kernel. لن ينطبق هذا التحديث إلا على macOS Catalina (10.15.4) والإصدارات الأحدث من macOS.

إذا قمت بنشر Microsoft Defender ل Endpoint على macOS في بيئة مدارة (من خلال JAMF أو Intune أو حل MDM آخر)، فيجب نشر ملفات تعريف تكوين جديدة. يؤدي الفشل في القيام بهذه الخطوات إلى الحصول على المستخدمين لمطالبات الموافقة لتشغيل هذه المكونات الجديدة.

## <a name="jamf"></a>JAMF

### <a name="jamf-system-extensions-policy"></a>نهج ملحقات نظام JAMF

للموافقة على ملحقات النظام، قم بإنشاء الحمولة التالية:

1. في **أجهزة الكمبيوتر > ملفات تعريف التكوين** حدد **خيارات > النظام**.
2. حدد **ملحقات النظام المسموح بها** من القائمة المنسدل **أنواع ملحقات** النظام.
3. استخدم **UBF8T346G9** لمعرف الفريق.
4. أضف معرفات المجموعة التالية إلى **القائمة ملحقات النظام المسموح** بها:

    - **com.microsoft.wdav.epsext**
    - **com.microsoft.wdav.netext**

    ![لقطة شاشة لملحقات النظام المعتمدة.](images/mac-approved-system-extensions.png)

### <a name="privacy-preferences-policy-control"></a>التحكم في نهج تفضيلات الخصوصية

أضف تحميل JAMF التالي لمنح "الوصول إلى القرص الكامل" إلى ملحق أمان نقطة نهاية نقطة النهاية ل Microsoft Defender. هذا النهج هو أحد المتطلبات الأساسية لتشغيل الملحق على جهازك.

1. حدد **خيارات التحكم** \> **في نهج تفضيلات الخصوصية**.
2. استخدم `com.microsoft.wdav.epsext` **كمعرف وكنوع** `Bundle ID` **مجموعة.**
3. تعيين متطلب التعليمات البرمجية إلى `identifier "com.microsoft.wdav.epsext" and anchor apple generic and certificate 1[field.1.2.840.113635.100.6.2.6] /* exists */ and certificate leaf[field.1.2.840.113635.100.6.1.13] /* exists */ and certificate leaf[subject.OU] = UBF8T346G9`
4. تعيين **التطبيق أو الخدمة إلى** **SystemPolicyAllFiles** والوصول إلى **السماح**.

    ![التحكم في نهج تفضيلات الخصوصية.](images/mac-system-extension-privacy.png)

### <a name="network-extension-policy"></a>نهج ملحق الشبكة

كجزء من قدرات الكشف عن نقاط النهاية والاستجابة لها، يفحص Microsoft Defender ل Endpoint على نظام التشغيل macOS حركة مرور مآخذ التوصيل ويعيد Microsoft 365 Defender المدخل. يسمح النهج التالي لملحق الشبكة بتنفيذ هذه الوظيفة.

> [!NOTE]
> لا تملك JAMF دعما مضمنا لنهج تصفية المحتوى، وهي شرط أساسي لتمكين ملحقات الشبكة التي يثبتها Microsoft Defender ل Endpoint على macOS على الجهاز. علاوة على ذلك، تغير JAMF في بعض الأحيان محتوى السياسات التي يتم نشرها.
> وعلى هذا النحو، توفر الخطوات التالية حلا بديل يتضمن توقيع ملف تعريف التكوين.

1. احفظ المحتوى التالي على جهازك باستخدام `com.microsoft.network-extension.mobileconfig` محرر نص:

    ```xml
    <?xml version="1.0" encoding="UTF-8"?><!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
    <plist version="1">
        <dict>
            <key>PayloadUUID</key>
            <string>DA2CC794-488B-4AFF-89F7-6686A7E7B8AB</string>
            <key>PayloadType</key>
            <string>Configuration</string>
            <key>PayloadOrganization</key>
            <string>Microsoft Corporation</string>
            <key>PayloadIdentifier</key>
            <string>DA2CC794-488B-4AFF-89F7-6686A7E7B8AB</string>
            <key>PayloadDisplayName</key>
            <string>Microsoft Defender Network Extension</string>
            <key>PayloadDescription</key>
            <string/>
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
                    <string>2BA070D9-2233-4827-AFC1-1F44C8C8E527</string>
                    <key>PayloadType</key>
                    <string>com.apple.webcontent-filter</string>
                    <key>PayloadOrganization</key>
                    <string>Microsoft Corporation</string>
                    <key>PayloadIdentifier</key>
                    <string>CEBF7A71-D9A1-48BD-8CCF-BD9D18EC155A</string>
                    <key>PayloadDisplayName</key>
                    <string>Approved Network Extension</string>
                    <key>PayloadDescription</key>
                    <string/>
                    <key>PayloadVersion</key>
                    <integer>1</integer>
                    <key>PayloadEnabled</key>
                    <true/>
                    <key>FilterType</key>
                    <string>Plugin</string>
                    <key>UserDefinedName</key>
                    <string>Microsoft Defender Network Extension</string>
                    <key>PluginBundleID</key>
                    <string>com.microsoft.wdav</string>
                    <key>FilterSockets</key>
                    <true/>
                    <key>FilterDataProviderBundleIdentifier</key>
                    <string>com.microsoft.wdav.netext</string>
                    <key>FilterDataProviderDesignatedRequirement</key>
                    <string>identifier "com.microsoft.wdav.netext" and anchor apple generic and certificate 1[field.1.2.840.113635.100.6.2.6] /* exists */ and certificate leaf[field.1.2.840.113635.100.6.1.13] /* exists */ and certificate leaf[subject.OU] = UBF8T346G9</string>
                </dict>
            </array>
        </dict>
    </plist>
    ```

2. تحقق من أنه تم نسخ الملف أعلاه بشكل صحيح عن طريق تشغيل الأداة `plutil` المساعدة في المحطة الطرفية:

    ```bash
    $ plutil -lint <PathToFile>/com.microsoft.network-extension.mobileconfig
    ```

    على سبيل المثال، إذا كان الملف مخزنا في المستندات:

    ```bash
    $ plutil -lint ~/Documents/com.microsoft.network-extension.mobileconfig
    ```

    تحقق من إخراج الأمر `OK`.

    ```bash
    <PathToFile>/com.microsoft.network-extension.mobileconfig: OK
    ```

3. اتبع الإرشادات الموجودة في [هذه الصفحة](https://www.jamf.com/jamf-nation/articles/649/creating-a-signing-certificate-using-jamf-pro-s-built-in-certificate-authority) لإنشاء شهادة توقيع باستخدام المرجع المضمن المضمن في JAMF.

4. بعد إنشاء الشهادة وتثبيتها على جهازك، قم بتشغيل الأمر التالي من المحطة الطرفية لتوقيع الملف:

    ```bash
    $ security cms -S -N "<CertificateName>" -i <PathToFile>/com.microsoft.network-extension.mobileconfig -o <PathToSignedFile>/com.microsoft.network-extension.signed.mobileconfig
    ```

    على سبيل المثال، إذا كان اسم الشهادة **SigningCertificate** والملف الموقع سيتم تخزينه في المستندات:

    ```bash
    $ security cms -S -N "SigningCertificate" -i ~/Documents/com.microsoft.network-extension.mobileconfig -o ~/Documents/com.microsoft.network-extension.signed.mobileconfig
    ```

5. من مدخل JAMF، انتقل إلى **ملفات تعريف التكوين** وانقر فوق **الزر** Upload. حدد `com.microsoft.network-extension.signed.mobileconfig` عند مطالبتك بالملف.

## <a name="intune"></a>Intune

### <a name="intune-system-extensions-policy"></a>نهج ملحقات النظام في Intune

للموافقة على ملحقات النظام:

1. في Intune، افتح **تكوين إدارة** \> **الجهاز**. حدد **إدارة ملفات** \> **التعريف** \> **إنشاء ملف تعريف**.
2. اختر اسما لملف التعريف. تغيير **Platform=macOS** إلى **Profile type=Extensions**. حدد **إنشاء**.
3. في علامة `Basics` التبويب، امنح اسما لملف التعريف الجديد هذا.
4. في علامة `Configuration settings` التبويب، أضف الإدخالات التالية في المقطع `Allowed system extensions` :

   <br>

   ****

   |معرف الحزمة|معرف الفريق|
   |---|---|
   |com.microsoft.wdav.epsext|UBF8T346G9|
   |com.microsoft.wdav.netext|UBF8T346G9|
   |||

   ![لقطة شاشة لملفات تعريف تكوين النظام.](images/mac-system-extension-intune2.png)

5. في علامة `Assignments` التبويب، قم بتعيين ملف التعريف هذا إلى جميع المستخدمين & **كافة الأجهزة**.
6. راجع ملف تعريف التكوين هذا وأنشئه.

### <a name="create-and-deploy-the-custom-configuration-profile"></a>إنشاء ملف تعريف تكوين مخصص ونشره

يمكن ملف تعريف التكوين التالي ملحق الشبكة ويمنح الوصول إلى القرص الكامل لملحق نظام أمان نقطة النهاية.

احفظ المحتوى التالي في **ملف يسمىsysext.xml**:

```xml
<?xml version="1.0" encoding="UTF-8"?><!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
<plist version="1">
    <dict>
        <key>PayloadUUID</key>
        <string>7E53AC50-B88D-4132-99B6-29F7974EAA3C</string>
        <key>PayloadType</key>
        <string>Configuration</string>
        <key>PayloadOrganization</key>
        <string>Microsoft Corporation</string>
        <key>PayloadIdentifier</key>
        <string>7E53AC50-B88D-4132-99B6-29F7974EAA3C</string>
        <key>PayloadDisplayName</key>
        <string>Microsoft Defender System Extensions</string>
        <key>PayloadDescription</key>
        <string/>
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
                <string>2BA070D9-2233-4827-AFC1-1F44C8C8E527</string>
                <key>PayloadType</key>
                <string>com.apple.webcontent-filter</string>
                <key>PayloadOrganization</key>
                <string>Microsoft Corporation</string>
                <key>PayloadIdentifier</key>
                <string>CEBF7A71-D9A1-48BD-8CCF-BD9D18EC155A</string>
                <key>PayloadDisplayName</key>
                <string>Approved Network Extension</string>
                <key>PayloadDescription</key>
                <string/>
                <key>PayloadVersion</key>
                <integer>1</integer>
                <key>PayloadEnabled</key>
                <true/>
                <key>FilterType</key>
                <string>Plugin</string>
                <key>UserDefinedName</key>
                <string>Microsoft Defender Network Extension</string>
                <key>PluginBundleID</key>
                <string>com.microsoft.wdav</string>
                <key>FilterSockets</key>
                <true/>
                <key>FilterDataProviderBundleIdentifier</key>
                <string>com.microsoft.wdav.netext</string>
                <key>FilterDataProviderDesignatedRequirement</key>
                <string>identifier &quot;com.microsoft.wdav.netext&quot; and anchor apple generic and certificate 1[field.1.2.840.113635.100.6.2.6] /* exists */ and certificate leaf[field.1.2.840.113635.100.6.1.13] /* exists */ and certificate leaf[subject.OU] = UBF8T346G9</string>
            </dict>
            <dict>
                <key>PayloadUUID</key>
                <string>56105E89-C7C8-4A95-AEE6-E11B8BEA0366</string>
                <key>PayloadType</key>
                <string>com.apple.TCC.configuration-profile-policy</string>
                <key>PayloadOrganization</key>
                <string>Microsoft Corporation</string>
                <key>PayloadIdentifier</key>
                <string>56105E89-C7C8-4A95-AEE6-E11B8BEA0366</string>
                <key>PayloadDisplayName</key>
                <string>Privacy Preferences Policy Control</string>
                <key>PayloadDescription</key>
                <string/>
                <key>PayloadVersion</key>
                <integer>1</integer>
                <key>PayloadEnabled</key>
                <true/>
                <key>Services</key>
                <dict>
                    <key>SystemPolicyAllFiles</key>
                    <array>
                        <dict>
                            <key>Identifier</key>
                            <string>com.microsoft.wdav.epsext</string>
                            <key>CodeRequirement</key>
                            <string>identifier "com.microsoft.wdav.epsext" and anchor apple generic and certificate 1[field.1.2.840.113635.100.6.2.6] /* exists */ and certificate leaf[field.1.2.840.113635.100.6.1.13] /* exists */ and certificate leaf[subject.OU] = UBF8T346G9</string>
                            <key>IdentifierType</key>
                            <string>bundleID</string>
                            <key>StaticCode</key>
                            <integer>0</integer>
                            <key>Allowed</key>
                            <integer>1</integer>
                        </dict>
                    </array>
                </dict>
            </dict>
        </array>
    </dict>
</plist>
```

تحقق من أنه تم نسخ الملف أعلاه بشكل صحيح. من المحطة الطرفية، تشغيل الأمر التالي والتحقق من أنه ناتج `OK`:

```bash
$ plutil -lint sysext.xml
sysext.xml: OK
```

لنشر ملف تعريف التكوين المخصص هذا:

1. في Intune، افتح **تكوين إدارة** \> **الجهاز**. حدد **إدارة** \> **ملفات التعريف** \> **إنشاء ملف تعريف**.
2. اختر اسما لملف التعريف. تغيير **Platform=macOS** و **Profile type=Custom**. حدد **تكوين**.
3. افتح ملف تعريف التكوين ثم قم **بتحميل** sysext.xml. تم إنشاء هذا الملف في الخطوة السابقة.
4. حدد **موافق**.

    ![ملحق النظام في لقطة شاشة Intune.](images/mac-system-extension-intune.png)

5. في علامة `Assignments` التبويب، قم بتعيين ملف التعريف هذا إلى جميع المستخدمين & **كافة الأجهزة**.
6. راجع ملف تعريف التكوين هذا وأنشئه.
