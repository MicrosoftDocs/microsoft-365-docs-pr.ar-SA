---
title: إعداد Microsoft Defender لنقطة النهاية على سياسات macOS في Jamf Pro
description: تعرف على كيفية إعداد Microsoft Defender ل Endpoint على سياسات macOS في Jamf Pro
keywords: policies, microsoft, defender, Microsoft Defender for Endpoint, mac, installation, deploy, uninstallation, intune, jamfpro, macos, catalina, mojave, high sierra
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
ms.openlocfilehash: 23420223102eafeab7783f7b81ac60c06670626c
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/08/2022
ms.locfileid: "63570618"
---
# <a name="set-up-the-microsoft-defender-for-endpoint-on-macos-policies-in-jamf-pro"></a>إعداد Microsoft Defender لنقطة النهاية على سياسات macOS في Jamf Pro

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**ينطبق على:**
- [Defender for Endpoint على Mac](microsoft-defender-endpoint-mac.md)
- [خطة Microsoft Defender لنقطة النهاية 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

سترشدك هذه الصفحة خلال الخطوات التي تحتاج إلى اتخاذها لإعداد سياسات macOS في Jamf Pro.

ستحتاج إلى اتخاذ الخطوات التالية:

1. [الحصول على حزمة Microsoft Defender for Endpoint onboarding](#step-1-get-the-microsoft-defender-for-endpoint-onboarding-package)
2. [إنشاء ملف تعريف تكوين في Jamf Pro باستخدام حزمة التهيئة](#step-2-create-a-configuration-profile-in-jamf-pro-using-the-onboarding-package)
3. [تكوين Microsoft Defender لإعدادات نقطة النهاية](#step-3-configure-microsoft-defender-for-endpoint-settings)
4. [تكوين إعدادات إعلامات Microsoft Defender لنقطة النهاية](#step-4-configure-notifications-settings)
5. [تكوين Microsoft AutoUpdate (MAU)](#step-5-configure-microsoft-autoupdate-mau)
6. [منح حق الوصول الكامل للقرص إلى Microsoft Defender لنقطة النهاية](#step-6-grant-full-disk-access-to-microsoft-defender-for-endpoint)
7. [الموافقة على ملحق Kernel ل Microsoft Defender لنقطة النهاية](#step-7-approve-kernel-extension-for-microsoft-defender-for-endpoint)
8. [الموافقة على ملحقات النظام ل Microsoft Defender لنقطة النهاية](#step-8-approve-system-extensions-for-microsoft-defender-for-endpoint)
9. [تكوين ملحق الشبكة](#step-9-configure-network-extension)
10. [جدولة عمليات الفحص باستخدام Microsoft Defender ل Endpoint على macOS](/windows/security/threat-protection/microsoft-defender-atp/mac-schedule-scan-atp)
11. [نشر Microsoft Defender ل Endpoint على macOS](#step-11-deploy-microsoft-defender-for-endpoint-on-macos)

## <a name="step-1-get-the-microsoft-defender-for-endpoint-onboarding-package"></a>الخطوة 1: الحصول على حزمة Microsoft Defender for Endpoint onboarding

1. في [Microsoft 365 Defender](https://security.microsoft.com)، انتقل إلى الإعدادات > نقاط النهاية **> التكوين**.

2. حدد نظام التشغيل macOS ونظام التشغيل وإدارة أجهزة المحمول / Microsoft Intune كطريقة نشر.

    ![صورة Microsoft 365 Defender المدخل.](images/onboarding-macos.png)

3. حدد **تنزيل حزمة الboarding** (WindowsDefenderATPOnboardingPackage.zip).

4. استخراج `WindowsDefenderATPOnboardingPackage.zip`.

5. انسخ الملف إلى موقعك المفضل. على سبيل المثال، `C:\Users\JaneDoe_or_JohnDoe.contoso\Downloads\WindowsDefenderATPOnboardingPackage_macOS_MDM_contoso\jamf\WindowsDefenderATPOnboarding.plist`.

## <a name="step-2-create-a-configuration-profile-in-jamf-pro-using-the-onboarding-package"></a>الخطوة 2: إنشاء ملف تعريف تكوين في Jamf Pro باستخدام حزمة التهيئة

1. حدد موقع الملف `WindowsDefenderATPOnboarding.plist` من المقطع السابق.

   ![صورة لملف WindowsDefenderATPOnboarding.](images/plist-onboarding-file.png)

2. سجل الدخول إلى Jamf Pro، وانتقل إلى ملفات تعريف **تكوين** >  **أجهزة الكمبيوتر**، وحدد **جديد**.

    ![صورة لإنشاء لوحة معلومات جديدة Pro Jamf.](images/jamf-pro-configure-profile.png)

3. أدخل التفاصيل التالية:

   **عام**:

   - الاسم: ا متنهار MDE ل macOS
   - الوصف: MDE الكشف التلقائي والاستجابة على النقط النهائية ل macOS
   - الفئة: بلا
   - طريقة التوزيع: التثبيت تلقائيا
   - المستوى: مستوى الكمبيوتر

4.  انتقل إلى صفحة **التطبيق & "** الإعدادات **" وحدد** Upload  > **Add**.

    ![صورة لتكوين التطبيق والإعدادات المخصصة.](images/jamfpro-mac-profile.png)

5. حدد **Upload ملف (ملف PLIST)** ثم في **التفضيل أدخل مجال** التفضيل: `com.microsoft.wdav.atp`.

    ![صورة لملف تحميل jamfpro plist.](images/jamfpro-plist-upload.png)

    ![صورة لملف خاصية تحميل ملف القائمة.](images/jamfpro-plist-file.png)

6. حدد **فتح** وحدد ملف التكهين.

    ![صورة لملف الboarding.](images/jamfpro-plist-file-onboard.png)

7. حدد **Upload**.

    ![صورة لتحميل ملف plist.](images/jamfpro-upload-plist.png)

8. حدد علامة **التبويب** نطاق.

    ![صورة ل علامة تبويب النطاق.](images/jamfpro-scope-tab.png)

9. حدد أجهزة الكمبيوتر الهدف.

    ![صورة لأجهزة الكمبيوتر الهدف.](images/jamfpro-target-computer.png)

    ![صورة الأهداف.](images/jamfpro-targets.png)

10. حدد **حفظ**.

    ![صورة لأجهزة الكمبيوتر المستهدفة للنشر.](images/jamfpro-deployment-target.png)

    ![صورة لأجهزة الكمبيوتر الهدف المحددة.](images/jamfpro-target-selected.png)

11. حدد **تم**.

    ![صورة لأجهزة كمبيوتر المجموعة الهدف.](images/jamfpro-target-group.png)

    ![قائمة ملفات تعريف التكوين.](images/jamfpro-configuration-policies.png)

## <a name="step-3-configure-microsoft-defender-for-endpoint-settings"></a>الخطوة 3: تكوين Microsoft Defender لإعدادات نقطة النهاية

يمكنك إما استخدام JAMF Pro GUI لتحرير الإعدادات الفردية لتكوين Microsoft Defender لنقطة النهاية، أو استخدام الأسلوب القديم عن طريق إنشاء قائمة تكوين في محرر نص، وتحميلها إلى JAMF Pro.

تجدر الإشارة إلى أنه يجب استخدام `com.microsoft.wdav` "مجال التفضيل" بدقة، حيث يستخدم Microsoft Defender لنقطة `com.microsoft.wdav.ext` النهاية هذا الاسم فقط ولتحميل الإعدادات المدارة الخاصة به!

(قد `com.microsoft.wdav.ext` يتم استخدام الإصدار في حالات نادرة عندما تفضل استخدام أسلوب GUI، ولكن تحتاج أيضا إلى تكوين إعداد لم يتم إضافته إلى المخطط بعد.)

### <a name="gui-method"></a>أسلوب GUI

1. قم بتنزيل ملف schema.json من مستودع [GitHub Defender](https://github.com/microsoft/mdatp-xplat/tree/master/macos/schema) واحفظه في ملف محلي:

    ```bash
    curl -o ~/Documents/schema.json https://raw.githubusercontent.com/microsoft/mdatp-xplat/master/macos/schema/schema.json
    ```

2. إنشاء ملف تعريف تكوين جديد ضمن أجهزة الكمبيوتر -> ملفات تعريف التكوين، أدخل التفاصيل التالية في علامة **التبويب عام** :

    ![ملف تعريف جديد.](images/644e0f3af40c29e80ca1443535b2fe32.png)

    - الاسم: إعدادات تكوين MDATP MDAV
    - الوصف:\<blank\>
    - الفئة: بلا (افتراضي)
    - المستوى: مستوى الكمبيوتر (افتراضي)
    - طريقة التوزيع: التثبيت تلقائيا (افتراضي)

3. قم بالتمرير لأسفل وصولا إلى علامة التبويب & تطبيق **الإعدادات**، وحدد تطبيقات خارجية، وانقر فوق إضافة  مخطط مخصص واستخدامه كمصدر لاستخدامه لمجال التفضيل.

    ![إضافة مخطط مخصص.](images/4137189bc3204bb09eed3aabc41afd78.png)

4. أدخل `com.microsoft.wdav` كمجال التفضيل، وانقر فوق إضافة **مخطط Upload** الملف schema.json الذي تم تنزيله في الخطوة 1. انقر فوق **حفظ**.

    ![Upload مخطط.](images/a6f9f556037c42fabcfdcb1b697244cf.png)

5. يمكنك رؤية كل إعدادات تكوين نقطة النهاية ل Microsoft Defender المعتمدة أدناه، ضمن **خصائص مجال التفضيل**. انقر **فوق إضافة/إزالة** الخصائص لتحديد الإعدادات التي تريد إدارتها، ثم انقر فوق **موافق** لحفظ التغييرات. (الإعدادات غير محدد لليسار في التكوين المدار، سيتمكن المستخدم النهائي من تكوين هذه الإعدادات على أ جهازه.)

    ![حدد الإعدادات المدارة.](images/817b3b760d11467abe9bdd519513f54f.png)

6. يمكنك تغيير قيم الإعدادات إلى القيم المطلوبة. يمكنك النقر فوق **مزيد من المعلومات** للحصول على وثائق لإعداد معين. (يمكنك النقر فوق **معاينة Plist** لفحص الشكل الذي ستبدو عليه قائمة التكوين. انقر **فوق محرر النموذج** للعودة إلى المحرر المرئي.)

    ![تغيير قيم الإعدادات.](images/a14a79efd5c041bb8974cb5b12b3a9b6.png)

7. حدد علامة **التبويب** نطاق.

    ![نطاق ملف تعريف التكوين.](images/9fc17529e5577eefd773c658ec576a7d.png)

8. حدد **مجموعة ماكينة Contoso**.

9. حدد **إضافة**، ثم حدد **حفظ**.

    ![إعدادات التكوين - إضافة.](images/cf30438b5512ac89af1d11cbf35219a6.png)

    ![إعدادات التكوين - حفظ.](images/6f093e42856753a3955cab7ee14f12d9.png)

10. حدد **تم**. سترى ملف تعريف **التكوين الجديد**.

    ![إعدادات التكوين - تم.](images/dd55405106da0dfc2f50f8d4525b01c8.png)

يضيف Microsoft Defender ل Endpoint إعدادات جديدة مع مرور الوقت. وستضاف هذه الإعدادات الجديدة إلى المخطط، وسينشر إصدار جديد إلى غيثوب.
كل ما تحتاج إلى القيام به للحصول على تحديثات هو تنزيل مخطط محدث وتحرير ملف تعريف التكوين الموجود وتحرير المخطط في علامة التبويب  تطبيق & **بيانات** الإعدادات مخصصة.

### <a name="legacy-method"></a>الأسلوب القديم

1. استخدم إعدادات تكوين Microsoft Defender لنقطة النهاية التالية:

    - enableRealTimeProtection
    - passiveMode

    > [!NOTE]
    > غير م تشغيله بشكل افتراضي، إذا كنت تخطط لتشغيل AV من جهة خارجية ل macOS، فقم بتعيينه إلى `true`.

    - الاستثناءات
    - excludedPath
    - excludedFileExtension
    - excludedFileName
    - الاستثناءاتMergePolicy
    - allowedThreats

    > [!NOTE]
    > EICAR على العينة، إذا كنت تمر عبر إثبات المبدأ، فقم بإزالته خاصة إذا كنت تقوم باختبار EICAR.

    - disallowedThreatActions
    - potentially_unwanted_application
    - archive_bomb
    - cloudService
    - automaticSampleSubmission
    - العلامات
    - إخفاءStatusMenuIcon

     للحصول على معلومات، راجع [قائمة الخاصية لملف تعريف التكوين الكامل ل JAMF](mac-preferences.md#property-list-for-jamf-full-configuration-profile).

     ```XML
     <?xml version="1.0" encoding="UTF-8"?>
     <!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
     <plist version="1.0">
     <dict>
         <key>antivirusEngine</key>
         <dict>
             <key>enableRealTimeProtection</key>
             <true/>
             <key>passiveMode</key>
             <false/>
             <key>exclusions</key>
             <array>
                 <dict>
                     <key>$type</key>
                     <string>excludedPath</string>
                     <key>isDirectory</key>
                     <false/>
                     <key>path</key>
                     <string>/var/log/system.log</string>
                 </dict>
                 <dict>
                     <key>$type</key>
                     <string>excludedPath</string>
                     <key>isDirectory</key>
                     <true/>
                     <key>path</key>
                     <string>/home</string>
                 </dict>
                 <dict>
                     <key>$type</key>
                     <string>excludedFileExtension</string>
                     <key>extension</key>
                     <string>pdf</string>
                 </dict>
                 <dict>
                     <key>$type</key>
                     <string>excludedFileName</string>
                     <key>name</key>
                     <string>cat</string>
                 </dict>
             </array>
             <key>exclusionsMergePolicy</key>
             <string>merge</string>
             <key>allowedThreats</key>
             <array>
                 <string>EICAR-Test-File (not a virus)</string>
             </array>
             <key>disallowedThreatActions</key>
             <array>
                 <string>allow</string>
                 <string>restore</string>
             </array>
             <key>threatTypeSettings</key>
             <array>
                 <dict>
                     <key>key</key>
                     <string>potentially_unwanted_application</string>
                     <key>value</key>
                     <string>block</string>
                 </dict>
                 <dict>
                     <key>key</key>
                     <string>archive_bomb</string>
                     <key>value</key>
                     <string>audit</string>
                 </dict>
             </array>
             <key>threatTypeSettingsMergePolicy</key>
             <string>merge</string>
         </dict>
         <key>cloudService</key>
         <dict>
             <key>enabled</key>
             <true/>
             <key>diagnosticLevel</key>
             <string>optional</string>
             <key>automaticSampleSubmission</key>
             <true/>
         </dict>
         <key>edr</key>
         <dict>
             <key>tags</key>
             <array>
                 <dict>
                     <key>key</key>
                     <string>GROUP</string>
                     <key>value</key>
                     <string>ExampleTag</string>
                 </dict>
             </array>
         </dict>
         <key>userInterface</key>
         <dict>
             <key>hideStatusMenuIcon</key>
             <false/>
         </dict>
     </dict>
     </plist>
     ```

2. احفظ الملف ك `MDATP_MDAV_configuration_settings.plist`.

3. في لوحة معلومات Pro Jamf، افتح **أجهزة الكمبيوتر** **وملفات تعريف التكوين الخاصة بها**. انقر **فوق جديد** والتبديل إلى علامة **التبويب عام** .

    ![ملف تعريف جديد.](images/644e0f3af40c29e80ca1443535b2fe32.png)

4. أدخل التفاصيل التالية:

    **عام**

    - الاسم: إعدادات تكوين MDATP MDAV
    - الوصف:\<blank\>
    - الفئة: بلا (افتراضي)
    - طريقة التوزيع: التثبيت تلقائيا (افتراضي)
    - المستوى: مستوى الكمبيوتر(افتراضي)

    ![صورة لإعدادات تكوين MDATP MDAV.](images/3160906404bc5a2edf84d1d015894e3b.png)

5. في **تطبيق & مخصص الإعدادات** حدد **تكوين**.

    ![صورة للتطبيق والإعدادات المخصصة.](images/e1cc1e48ec9d5d688087b4d771e668d2.png)

6. حدد **Upload ملف (ملف PLIST)**.

    ![صورة لملف plist لإعدادات التكوين.](images/6f85269276b2278eca4bce84f935f87b.png)

7. في **مجال التفضيلات،** أدخل `com.microsoft.wdav`، ثم حدد Upload **ملف PLIST**.

    ![صورة لمجال تفضيلات إعدادات التكوين.](images/db15f147dd959e872a044184711d7d46.png)

8. حدد **اختيار ملف**.

    ![صورة لإعدادات التكوين اختر ملفا.](images/526e978761fc571cca06907da7b01fd6.png)

9. حدد **MDATP_MDAV_configuration_settings.plist**، ثم حدد **فتح**.

    ![صورة لإعدادات تكوين mdatpmdav.](images/98acea3750113b8dbab334296e833003.png)

10. حدد **Upload**.

    ![صورة تحميل إعداد التكوين.](images/0adb21c13206861ba9b30a879ade93d3.png)

    ![صورة لإعدادات التكوين تحميل صورة.](images/f624de59b3cc86e3e2d32ae5de093e02.png)

    > [!NOTE]
    > إذا حدث أن قمت بتحميل ملف Intune، فسوف تحصل على الخطأ التالي:
    >
    >![صورة لإعدادات التكوين في تحميل ملف intune.](images/8e69f867664668796a3b2904896f0436.png)

11. حدد **حفظ**.

    ![صورة لإعدادات التكوين حفظ الصورة.](images/1b6b5a4edcb42d97f1e70a6a0fa48e3a.png)

12. يتم تحميل الملف.

    ![صورة ملف إعدادات التكوين الذي تم تحميله.](images/33e2b2a1611fdddf6b5b79e54496e3bb.png)

    ![صورة لملف إعدادات التكوين تم تحميله.](images/a422e57fe8d45689227e784443e51bd1.png)

13. حدد علامة **التبويب** نطاق.

    ![صورة لنطاق إعدادات التكوين.](images/9fc17529e5577eefd773c658ec576a7d.png)

14. حدد **مجموعة ماكينة Contoso**.

15. حدد **إضافة**، ثم حدد **حفظ**.

    ![يتم إضافة صورة لإعدادات التكوين.](images/cf30438b5512ac89af1d11cbf35219a6.png)

    ![صورة لإعدادات التكوين حفظ إضافة.](images/6f093e42856753a3955cab7ee14f12d9.png)

16. حدد **تم**. سترى ملف تعريف **التكوين الجديد**.

    ![صورة لإعدادات التكوين صورة ملف تعريف التكوين.](images/dd55405106da0dfc2f50f8d4525b01c8.png)

## <a name="step-4-configure-notifications-settings"></a>الخطوة 4: تكوين إعدادات الإعلامات

تنطبق هذه الخطوات على macOS 10.15 (Catalina) أو أحدث.

1. في لوحة معلومات Pro Jamf، حدد **أجهزة الكمبيوتر**، ثم **ملفات تعريف التكوين**.

2. انقر **فوق جديد**، وأدخل التفاصيل التالية ل **خيارات**:

    - Tab **General**:
        - **الاسم**: إعدادات إعلام MDATP MDAV
        - **الوصف**: macOS 10.15 (Catalina) أو أحدث
        - **الفئة**: بلا *(افتراضي)*
        - **طريقة التوزيع**: التثبيت تلقائيا *(افتراضي)*
        - **المستوى**: مستوى الكمبيوتر *(افتراضي)*

        ![صورة لشاشة ملف تعريف تكوين macOS جديدة.](images/c9820a5ff84aaf21635c04a23a97ca93.png)

    - **إعلامات علامات** التبويب، **انقر فوق إضافة**، وأدخل القيم التالية:
        - **"معرّف الحزمة"**: `com.microsoft.wdav.tray`
        - **تنبيهات هامة**: انقر فوق **تعطيل**
        - **الإعلامات**: انقر فوق **تمكين**
        - **نوع تنبيه الشعار**: حدد **تضمين** **ومؤقت** *(افتراضي)*
        - **الإعلامات على شاشة التأمين**: انقر فوق **إخفاء**
        - **الإعلامات في مركز الإعلامات**: انقر فوق **عرض**
        - **أيقونة تطبيق الشارة**: انقر فوق **عرض**

        ![صورة لإعدادات التكوين mdatpmdav في علبة الإعلامات.](images/7f9138053dbcbf928e5182ee7b295ebe.png)

    - **إعلامات علامات** التبويب، **انقر فوق إضافة** مرة أخرى، ثم قم بالتمرير لأسفل وصولا إلى **إعلامات الإعدادات**
        - **"معرّف الحزمة"**: `com.microsoft.autoupdate2`
        - تكوين باقي الإعدادات إلى القيم نفسها كما هو أعلاه

        ![صورة لإعدادات التكوين mdatpmdav notifications mau.](images/4bac6ce277aedfb4a674f2d9fcb2599a.png)

        لاحظ أنه لديك الآن "جدولان" مع تكوينات الإعلامات، أحدهما لم **ID الحزمة: com.microsoft.wdav.tray**، وآخر لم **ID الحزمة: com.microsoft.autoupdate2**. على الرغم من أنه يمكنك تكوين إعدادات التنبيه وفقا لمتطلباتك، يجب أن تكون "معرف الحزمة" تماما كما هو موضح من قبل، ويجب أن يكون مفتاح التبديل "تضمين" على "**تشغيل"** **للإشعارات**.

3. حدد علامة **التبويب** نطاق، ثم حدد **إضافة**.

    ![إضافة صورة لنطاق إعدادات التكوين.](images/441aa2ecd36abadcdd8aed03556080b5.png)

4. حدد **مجموعة ماكينة Contoso**.

5. حدد **إضافة**، ثم حدد **حفظ**.

    ![صورة لإعدادات التكوين حفظ contoso machine grp.](images/09a275e321268e5e3ac0c0865d3e2db5.png)

    ![صورة إعدادات التكوين إضافة حفظ.](images/4d2d1d4ee13d3f840f425924c3df0d51.png)

6. حدد **تم**. سترى ملف تعريف **التكوين الجديد**.

    ![صورة لإعداد التكوين تم img.](images/633ad26b8bf24ec683c98b2feb884bdf.png)

## <a name="step-5-configure-microsoft-autoupdate-mau"></a>الخطوة 5: تكوين Microsoft AutoUpdate (MAU)

1. استخدم إعدادات تكوين Microsoft Defender لنقطة النهاية التالية:

      ```XML
   <?xml version="1.0" encoding="UTF-8"?>
   <!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
   <plist version="1.0">
   <dict>
    <key>ChannelName</key>
    <string>Current</string>
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

2. احفظه ك `MDATP_MDAV_MAU_settings.plist`.

3. في لوحة معلومات Pro Jamf، حدد **عام**.

    ![صورة صورة عامة لإعداد التكوين.](images/eaba2a23dd34f73bf59e826217ba6f15.png)

4. أدخل التفاصيل التالية:

    **عام**

    - الاسم: إعدادات MAU MDAV MAU MDATP
    - الوصف: إعدادات "إعادة التشغيل التلقائي ل Microsoft" ل MDATP ل macOS
    - الفئة: بلا (افتراضي)
    - طريقة التوزيع: التثبيت تلقائيا (افتراضي)
    - المستوى: مستوى الكمبيوتر(افتراضي)

5. في **تطبيق & مخصص الإعدادات** حدد **تكوين**.

    ![صورة تطبيق إعداد التكوين والإعدادات المخصصة.](images/1f72e9c15eaafcabf1504397e99be311.png)

6. حدد **Upload ملف (ملف PLIST)**.

    ![صورة إعداد التكوين plist.](images/1213872db5833aa8be535da57653219f.png)

7. في **مجال التفضيل** أدخل: `com.microsoft.autoupdate2`، ثم حدد Upload **ملف PLIST**.

    ![صورة لمجال pref لإعداد التكوين.](images/1213872db5833aa8be535da57653219f.png)

8. حدد **اختيار ملف**.

    ![صورة لإعداد التكوين choosefile.](images/335aff58950ce62d1dabc289ecdce9ed.png)

9. حدد **MDATP_MDAV_MAU_settings.plist**.

    ![صورة لإعداد التكوين من إعدادات mdatpmdavmau.](images/a26bd4967cd54bb113a2c8d32894c3de.png)

10. حدد **Upload**.
    ![صورة لإعداد التكوين.](images/4239ca0528efb0734e4ca0b490bfb22d.png)

    ![صورة لإعداد التكوين.](images/4ec20e72c8aed9a4c16912e01692436a.png)

11. حدد **حفظ**.

    ![صورة لإعداد التكوين saveimg.](images/253274b33e74f3f5b8d475cf8692ce4e.png)

12. حدد علامة **التبويب** نطاق.

     ![صورة لمدى نطاق إعداد التكوين.](images/10ab98358b2d602f3f67618735fa82fb.png)

13. حدد **إضافة**.

    ![صورة addimg1 لإعداد التكوين.](images/56e6f6259b9ce3c1706ed8d666ae4947.png)

    ![صورة addimg2 لإعداد التكوين.](images/38c67ee1905c4747c3b26c8eba57726b.png)

    ![صورة لإعداد التكوين addimg3.](images/321ba245f14743c1d5d51c15e99deecc.png)

14. حدد **تم**.

    ![صورة لإعداد التكوين doneimage.](images/ba44cdb77e4781aa8b940fb83e3c21f7.png)

## <a name="step-6-grant-full-disk-access-to-microsoft-defender-for-endpoint"></a>الخطوة 6: منح حق الوصول الكامل إلى Microsoft Defender لنقطة النهاية

1. في لوحة معلومات jamf Pro، حدد **ملفات تعريف التكوين**.

    ![صورة لملف تعريف إعداد التكوين.](images/264493cd01e62c7085659d6fdc26dc91.png)

2. حدد **+ جديد**.

3. أدخل التفاصيل التالية:

    **عام**
    - الاسم: MDATP MDAV - منح الوصول إلى القرص الكامل الكشف التلقائي والاستجابة على النقط النهائية وAV
    - الوصف: على macOS Catalina أو أحدث، عنصر التحكم الجديد في نهج تفضيلات الخصوصية
    - الفئة: بلا
    - طريقة التوزيع: التثبيت تلقائيا
    - المستوى: مستوى الكمبيوتر

    ![صورة لإعداد التكوين بشكل عام.](images/ba3d40399e1a6d09214ecbb2b341923f.png)

4. في **تكوين تفضيلات الخصوصية، حدد** **تكوين**.

    ![صورة عنصر تحكم نهج خصوصية التكوين.](images/715ae7ec8d6a262c489f94d14e1e51bb.png)

5. في **عنصر تحكم نهج تفضيلات الخصوصية**، أدخل التفاصيل التالية:

    - المعرف: `com.microsoft.wdav`
    - نوع المعرف: معرف المجموعة
    - متطلبات التعليمات البرمجية: `identifier "com.microsoft.wdav" and anchor apple generic and certificate 1[field.1.2.840.113635.100.6.2.6] /* exists */ and certificate leaf[field.1.2.840.113635.100.6.1.13] /* exists */ and certificate leaf[subject.OU] = UBF8T346G9`

    ![صورة تفاصيل التحكم في نهج تفضيلات الخصوصية لإعداد التكوين.](images/22cb439de958101c0a12f3038f905b27.png)

6. حدد **+ إضافة**.

    ![صورة إعداد التكوين إضافة نهج النظام لجميع الملفات.](images/bd93e78b74c2660a0541af4690dd9485.png)

    - ضمن التطبيق أو الخدمة: تعيين إلى **SystemPolicyAllFiles**

    - ضمن "access": تعيين إلى **السماح**

7. حدد **حفظ** (وليس تلك التي في الجزء السفلي الأيمن).

    ![صورة إعداد التكوين لحفظ الصور.](images/6de50b4a897408ddc6ded56a09c09fe2.png)

8. انقر فوق `+` العلامة بجانب **الوصول إلى التطبيق** لإضافة إدخال جديد.

    ![صورة الوصول إلى تطبيق إعداد التكوين.](images/tcc-add-entry.png)

9. أدخل التفاصيل التالية:

    - المعرف: `com.microsoft.wdav.epsext`
    - نوع المعرف: معرف المجموعة
    - متطلبات التعليمات البرمجية: `identifier "com.microsoft.wdav.epsext" and anchor apple generic and certificate 1[field.1.2.840.113635.100.6.2.6] /* exists */ and certificate leaf[field.1.2.840.113635.100.6.1.13] /* exists */ and certificate leaf[subject.OU] = UBF8T346G9`

10. حدد **+ إضافة**.

    ![صورة إدخال tcc epsext لإعداد التكوين.](images/tcc-epsext-entry.png)

    - ضمن التطبيق أو الخدمة: تعيين إلى **SystemPolicyAllFiles**

    - ضمن "access": تعيين إلى **السماح**

11. حدد **حفظ** (وليس تلك التي في الجزء السفلي الأيمن).

    ![صورة لإعداد التكوين tcc epsext image2.](images/tcc-epsext-entry2.png)

12. حدد علامة **التبويب** نطاق.

    ![صورة لنطاق إعداد التكوين.](images/2c49b16cd112729b3719724f581e6882.png)

13. حدد **+ إضافة**.

    ![صورة لإضافة إعداد التكوين.](images/57cef926d1b9260fb74a5f460cee887a.png)

14. حدد **مجموعات الكمبيوتر >** ضمن **اسم** > حدد **مجموعة أجهزة Contoso**.

    ![صورة لإعداد التكوين contoso machinegrp.](images/368d35b3d6179af92ffdbfd93b226b69.png)

15. حدد **إضافة**.

16. حدد **حفظ**.

17. حدد **تم**.

    ![صورة ل donimg لإعداد التكوين.](images/809cef630281b64b8f07f20913b0039b.png)

    ![صورة لإعداد التكوين donimg2.](images/6c8b406ee224335a8c65d06953dc756e.png)

بدلا من ذلك، يمكنك تنزيل [fulldisk.mobileconfig](https://github.com/microsoft/mdatp-xplat/blob/master/macos/mobileconfig/profiles/fulldisk.mobileconfig) وتحميله إلى ملفات تعريف تكوين JAMF كما هو موضح في نشر ملفات تعريف التكوين المخصصة باستخدام [Jamf Pro| الطريقة 2: Upload ملف تعريف التكوين إلى Jamf Pro](https://www.jamf.com/jamf-nation/articles/648/deploying-custom-configuration-profiles-using-jamf-pro).

## <a name="step-7-approve-kernel-extension-for-microsoft-defender-for-endpoint"></a>الخطوة 7: الموافقة على ملحق Kernel ل Microsoft Defender لنقطة النهاية

> [!CAUTION]
> لا تدعم أجهزة Apple Silicon (M1) KEXT. سيفشل تثبيت ملف تعريف تكوين يتكون من سياسات KEXT على هذه الأجهزة.

1. في ملفات **تعريف التكوين،** حدد **+ جديد**.

    ![لقطة شاشة لمن منشور وسائط اجتماعية يتم إنشاء الوصف تلقائيا.](images/6c8b406ee224335a8c65d06953dc756e.png)

2. أدخل التفاصيل التالية:

    **عام**

    - الاسم: MDATP MDAV Kernel Extension
    - الوصف: ملحق kernel MDATP (kext)
    - الفئة: بلا
    - طريقة التوزيع: التثبيت تلقائيا
    - المستوى: مستوى الكمبيوتر

    ![صورة لإعدادات التكوين mdatpmdav kernel.](images/24e290f5fc309932cf41f3a280d22c14.png)

3. في **تكوين ملحقات Kernel المعتمدة** ، حدد **تكوين**.

    ![صورة لإعدادات التكوين المعتمدة من kernel ext.](images/30be88b63abc5e8dde11b73f1b1ade6a.png)

4. في **ملحقات Kernel المعتمدة** أدخل التفاصيل التالية:

    - اسم العرض: Microsoft Corp.
    - ID الفريق: UBF8T346G9

    ![صورة لإعدادات التكوين ملحق kernel الخاص بالتكوين.](images/39cf120d3ac3652292d8d1b6d057bd60.png)

5. حدد علامة **التبويب** نطاق.

    ![صورة ل علامة تبويب نطاق إعدادات التكوين img.](images/0df36fc308ba569db204ee32db3fb40a.png)

6. حدد **+ إضافة**.

7. حدد **مجموعات الكمبيوتر >** ضمن **اسم** المجموعة > مجموعة **أجهزة Contoso**.

8. حدد **+ إضافة**.

    ![تضيف صورة إعدادات التكوين صورا.](images/0dde8a4c41110dbc398c485433a81359.png)

9. حدد **حفظ**.

    ![صورة لإعدادات التكوين saveimag.](images/0add8019b85a453b47fa5c402c72761b.png)

10. حدد **تم**.

    ![صورة لإعدادات التكوين doneimag.](images/1c9bd3f68db20b80193dac18f33c22d0.png)

بدلا من ذلك، يمكنك تنزيل [kext.mobileconfig](https://github.com/microsoft/mdatp-xplat/blob/master/macos/mobileconfig/profiles/kext.mobileconfig) وتحميله إلى ملفات تعريف تكوين JAMF كما هو موضح في نشر ملفات تعريف التكوين المخصصة باستخدام [Jamf Pro| الطريقة 2: Upload ملف تعريف التكوين إلى Jamf Pro](https://www.jamf.com/jamf-nation/articles/648/deploying-custom-configuration-profiles-using-jamf-pro).

## <a name="step-8-approve-system-extensions-for-microsoft-defender-for-endpoint"></a>الخطوة 8: الموافقة على ملحقات النظام ل Microsoft Defender لنقطة النهاية

1. في ملفات **تعريف التكوين،** حدد **+ جديد**.

    ![لقطة شاشة لمن منشور وسائط اجتماعية يتم إنشاء الوصف تلقائيا.](images/6c8b406ee224335a8c65d06953dc756e.png)

2. أدخل التفاصيل التالية:

    **عام**

    - الاسم: MDATP MDAV System Extensions
    - الوصف: ملحقات نظام MDATP
    - الفئة: بلا
    - طريقة التوزيع: التثبيت تلقائيا
    - المستوى: مستوى الكمبيوتر

    ![صورة لإعدادات التكوين sysext new prof.](images/sysext-new-profile.png)

3. في **ملحقات النظام** ، حدد **تكوين**.

   ![صورة لإعدادات التكوين sysext config.](images/sysext-configure.png)

4. في **ملحقات النظام** أدخل التفاصيل التالية:

   - اسم العرض: Microsoft Corp. ملحقات النظام
   - أنواع ملحقات النظام: ملحقات النظام المسموح بها
   - معرف الفريق: UBF8T346G9
   - ملحقات النظام المسموح بها:
     - **com.microsoft.wdav.epsext**
     - **com.microsoft.wdav.netext**

    ![صورة لإعدادات التكوين sysextconfig2.](images/sysext-configure2.png)

5. حدد علامة **التبويب** نطاق.

    ![صورة نطاق إعدادات التكوين.](images/0df36fc308ba569db204ee32db3fb40a.png)

6. حدد **+ إضافة**.

7. حدد **مجموعات الكمبيوتر >** ضمن **اسم** المجموعة > مجموعة **أجهزة Contoso**.

8. حدد **+ إضافة**.

   ![صورة لإعدادات التكوين addima.](images/0dde8a4c41110dbc398c485433a81359.png)

9. حدد **حفظ**.

   ![صورة لإعدادات التكوين نطاق sysext.](images/sysext-scope.png)

10. حدد **تم**.

    ![صورة لإعدادات التكوين sysext-final.](images/sysext-final.png)

## <a name="step-9-configure-network-extension"></a>الخطوة 9: تكوين ملحق الشبكة

كجزء من قدرات الكشف عن نقاط النهاية والاستجابة لها، يفحص Microsoft Defender ل Endpoint على نظام التشغيل macOS حركة مرور مآخذ التوصيل ويعيد Microsoft 365 Defender المدخل. يسمح النهج التالي لملحق الشبكة بتنفيذ هذه الوظيفة.

تنطبق هذه الخطوات على macOS 10.15 (Catalina) أو أحدث.

1. في لوحة معلومات Pro Jamf، حدد **أجهزة الكمبيوتر**، ثم **ملفات تعريف التكوين**.

2. انقر **فوق جديد**، وأدخل التفاصيل التالية ل **خيارات**:

    - Tab **General**:
        - **الاسم**: ملحق شبكة Microsoft Defender
        - **الوصف**: macOS 10.15 (Catalina) أو أحدث
        - **الفئة**: بلا *(افتراضي)*
        - **طريقة التوزيع**: التثبيت تلقائيا *(افتراضي)*
        - **المستوى**: مستوى الكمبيوتر *(افتراضي)*

    - عامل **تصفية محتوى علامة التبويب**:
        - **اسم عامل التصفية**: عامل تصفية محتوى Microsoft Defender
        - **المعرف**: `com.microsoft.wdav`
        - اترك **عنوان الخدمة،** **المؤسسة****، اسم المستخدم**، **كلمة المرور**، **الشهادة** **فارغة (***لم يتم تحديد* تضمين)
        - **ترتيب التصفية**: Inspector
        - **عامل تصفية مأخذ التوصيل**: `com.microsoft.wdav.netext`
        - **المتطلبات المعينة لتصفية مأخذ التوصيل**: `identifier "com.microsoft.wdav.netext" and anchor apple generic and certificate 1[field.1.2.840.113635.100.6.2.6] /* exists */ and certificate leaf[field.1.2.840.113635.100.6.1.13] /* exists */ and certificate leaf[subject.OU] = UBF8T346G9`
        - ترك **حقول عامل تصفية** الشبكة فارغة (**لم** *يتم تحديد* تضمين)

        تجدر الإشارة **إلى أن المعرف** وتصفية **مأخذ التوصيل** وتصفية مأخذ التوصيل **قد عينت** القيم الدقيقة للمتطلبات كما هو محدد أعلاه.

        ![صورة لإعداد التكوين mdatpmdav.](images/netext-create-profile.png)
        
 > [!NOTE]
 > يدعم Jamf إعدادات تصفية المحتوى المضمنة التي يمكن تعيينها مباشرة من خلال الواجهة.

3. حدد علامة **التبويب** نطاق.

   ![صورة علامة تبويب sco لإعدادات التكوين.](images/0df36fc308ba569db204ee32db3fb40a.png)

4. حدد **+ إضافة**.

5. حدد **مجموعات الكمبيوتر >** ضمن **اسم** المجموعة > مجموعة **أجهزة Contoso**.

6. حدد **+ إضافة**.

    ![صورة adim لإعدادات التكوين.](images/0dde8a4c41110dbc398c485433a81359.png)

7. حدد **حفظ**.

    ![صورة لإعدادات التكوين savimg netextscop.](images/netext-scope.png)

8. حدد **تم**.

    ![صورة لإعدادات التكوين netextfinal.](images/netext-final.png)

بدلا من ذلك، يمكنك تنزيل [netfilter.mobileconfig](https://github.com/microsoft/mdatp-xplat/blob/master/macos/mobileconfig/profiles/netfilter.mobileconfig) وتحميله إلى ملفات تعريف تكوين JAMF كما هو موضح في نشر ملفات تعريف التكوين المخصصة باستخدام [Jamf Pro| الطريقة 2: Upload ملف تعريف التكوين إلى Jamf Pro](https://www.jamf.com/jamf-nation/articles/648/deploying-custom-configuration-profiles-using-jamf-pro).

## <a name="step-10-schedule-scans-with-microsoft-defender-for-endpoint-on-macos"></a>الخطوة 10: جدولة عمليات الفحص باستخدام Microsoft Defender لنقطة النهاية على macOS

اتبع الإرشادات حول [جدولة عمليات الفحص باستخدام Microsoft Defender ل Endpoint على macOS](/windows/security/threat-protection/microsoft-defender-atp/mac-schedule-scan-atp).

## <a name="step-11-deploy-microsoft-defender-for-endpoint-on-macos"></a>الخطوة 11: نشر Microsoft Defender ل Endpoint على macOS

1. انتقل إلى المكان الذي حفظت فيه `wdav.pkg`.

    ![صورة لمستكشف الملفات wdav pkg.](images/8dde76b5463047423f8637c86b05c29d.png)

2. أعد تسميته إلى `wdav_MDM_Contoso_200329.pkg`.

    ![صورة مستكشف الملفات1 wdavmdmpkg.](images/fb2220fed3a530f4b3ef36f600da0c27.png)

3. افتح لوحة معلومات Pro Jamf.

    ![صورة لإعدادات التكوين jamfpro.](images/990742cd9a15ca9fdd37c9f695d1b9f4.png)

4. حدد الكمبيوتر وانقر فوق أيقونة الترس في الأعلى، ثم حدد **إدارة الكمبيوتر**.

    ![صورة لإعدادات التكوين compmgmt.](images/b6d671b2f18b89d96c1c8e2ea1991242.png)

5. في **الحزم**، حدد **+ جديد**.
    ![صورة تحتوي على وصف الطيور يتم إنشاء حزمة جديدة تلقائيا.](images/57aa4d21e2ccc65466bf284701d4e961.png)

6. في **حزمة جديدة** أدخل التفاصيل التالية:

    **علامة التبويب "عام"**
    - اسم العرض: اتركه فارغا في الوقت الحالي. لأنه سيتم إعادة تعيينه عند اختيار pkg.
    - الفئة: بلا (افتراضي)
    - اسم الملف: اختيار ملف

    ![صورة علامة التبويب العامة لإعدادات التكوين.](images/21de3658bf58b1b767a17358a3f06341.png)

    افتح الملف وأشير إلى أو `wdav.pkg` `wdav_MDM_Contoso_200329.pkg`.

    ![لقطة شاشة لوصف شاشة كمبيوتر يتم إنشاؤها تلقائيا.](images/1aa5aaa0a387f4e16ce55b66facc77d1.png)

7. حدد **فتح**. قم بتعيين **اسم العرض** للحماية المتقدمة من المخاطر من **Microsoft Defender برنامج الحماية من الفيروسات من Microsoft Defender**.

    **ملف البيان** غير مطلوب. يعمل Microsoft Defender لنقطة النهاية بدون ملف Manifest.

    **علامة التبويب "خيارات"**: الاحتفاظ بالقيم الافتراضية.

    **علامة تبويب القيود**: الاحتفاظ بالقيم الافتراضية.

     ![صورة ل علامة تبويب قيود إعدادات التكوين.](images/56dac54634d13b2d3948ab50e8d3ef21.png)

8. حدد **حفظ**. يتم تحميل الحزمة إلى Jamf Pro.

   ![صورة لإعدادات التكوين حزمة jamf pro.](images/33f1ecdc7d4872555418bbc3efe4b7a3.png)

   قد يستغرق الأمر بضع دقائق حتى تتوفر الحزمة للنشر.

   ![صورة لإعدادات التكوين حزمة upl.](images/1626d138e6309c6e87bfaab64f5ccf7b.png)

9. انتقل إلى **صفحة "السياسات** ".

    ![صورة لإعدادات التكوين polocies.](images/f878f8efa5ebc92d069f4b8f79f62c7f.png)

10. حدد **+ جديد** لإنشاء نهج جديد.

    ![صورة نهج جديد لإعدادات التكوين.](images/847b70e54ed04787e415f5180414b310.png)


11. بشكل **عام** ، أدخل التفاصيل التالية:

    - اسم العرض: MDATP Onboarding Contoso 200329 v100.86.92 أو أي وقت لاحق

    ![صورة لإعدادات التكوينmdatponboard.](images/625ba6d19e8597f05e4907298a454d28.png)

12. حدد **تسجيل الدخول المتكرر**.

    ![صورة إعدادات التكوين التي تتكرر.](images/68bdbc5754dfc80aa1a024dde0fce7b0.png)

13. حدد **حفظ**.

14. حدد **الحزم > تكوين**.

    ![صورة لحزمة إعدادات التكوين التي تم تكوينها.](images/8fb4cc03721e1efb4a15867d5241ebfb.png)

15. حدد الزر **إضافة** الموجود بجانب الحماية المتقدمة من المخاطر من **Microsoft Defender برنامج الحماية من الفيروسات من Microsoft Defender**.

    ![صورة لإعدادات التكوين إضافة MDATP و MDA.](images/526b83fbdbb31265b3d0c1e5fbbdc33a.png)

16. حدد **حفظ**.

    ![صورة لإعدادات التكوينsavimg.](images/9d6e5386e652e00715ff348af72671c6.png)

17. حدد علامة **التبويب** نطاق.

    ![صورة ل scptab إعدادات التكوين.](images/8d80fe378a31143db9be0bacf7ddc5a3.png)

18. حدد أجهزة الكمبيوتر الهدف.

    ![صورة لإعدادات التكوين tgtcomp.](images/6eda18a64a660fa149575454e54e7156.png)

    **النطاق**

    حدد **إضافة**.

    ![صورة لإعدادات التكوين ad1img.](images/1c08d097829863778d562c10c5f92b67.png)

    ![صورة لإعدادات التكوين ad2img.](images/216253cbfb6ae738b9f13496b9c799fd.png)

    **الخدمة الذاتية**

    ![صورة لإعدادات التكوين الخدمة الذاتية.](images/c9f85bba3e96d627fe00fc5a8363b83a.png)

19. حدد **تم**.

    ![صورة لإعدادات التكوين do1img.](images/99679a7835b0d27d0a222bc3fdaf7f3b.png)

    ![صورة لإعدادات التكوين do2img.](images/632aaab79ae18d0d2b8e0c16b6ba39e2.png)
