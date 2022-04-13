---
title: إعداد Microsoft Defender لنقطة النهاية على نهج macOS في Jamf Pro
description: تعرف على كيفية إعداد Microsoft Defender لنقطة النهاية على نهج macOS في Jamf Pro
keywords: النهج، microsoft، defender، Microsoft Defender لنقطة النهاية، mac، التثبيت، التوزيع، إلغاء التثبيت، intune، jamfpro، macos، catalina، mojave، high sierra
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
ms.openlocfilehash: 8d248eef175da6de3e329b4ec9b75b1111c668a6
ms.sourcegitcommit: 195e4734d9a6e8e72bd355ee9f8bca1f18577615
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/13/2022
ms.locfileid: "64824707"
---
# <a name="set-up-the-microsoft-defender-for-endpoint-on-macos-policies-in-jamf-pro"></a>إعداد Microsoft Defender لنقطة النهاية على نهج macOS في Jamf Pro

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**ينطبق على:**
- [Defender لنقطة النهاية على Mac](microsoft-defender-endpoint-mac.md)
- [Microsoft Defender لنقطة النهاية الخطة 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender لنقطة النهاية الخطة 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

ستوجهك هذه الصفحة خلال الخطوات التي تحتاج إلى اتخاذها لإعداد نهج macOS في Jamf Pro.

ستحتاج إلى اتخاذ الخطوات التالية:

1. [الحصول على حزمة Microsoft Defender لنقطة النهاية الإلحاق](#step-1-get-the-microsoft-defender-for-endpoint-onboarding-package)
2. [إنشاء ملف تعريف تكوين في Jamf Pro باستخدام حزمة الإلحاق](#step-2-create-a-configuration-profile-in-jamf-pro-using-the-onboarding-package)
3. [تكوين إعدادات Microsoft Defender لنقطة النهاية](#step-3-configure-microsoft-defender-for-endpoint-settings)
4. [تكوين إعدادات إعلامات Microsoft Defender لنقطة النهاية](#step-4-configure-notifications-settings)
5. [تكوين التحديث التلقائي لبرامج Microsoft (MAU)](#step-5-configure-microsoft-autoupdate-mau)
6. [منح حق الوصول الكامل للقرص إلى Microsoft Defender لنقطة النهاية](#step-6-grant-full-disk-access-to-microsoft-defender-for-endpoint)
7. [الموافقة على ملحق Kernel Microsoft Defender لنقطة النهاية](#step-7-approve-kernel-extension-for-microsoft-defender-for-endpoint)
8. [الموافقة على ملحقات النظام Microsoft Defender لنقطة النهاية](#step-8-approve-system-extensions-for-microsoft-defender-for-endpoint)
9. [تكوين ملحق الشبكة](#step-9-configure-network-extension)
10. [جدولة عمليات الفحص باستخدام Microsoft Defender لنقطة النهاية على macOS](/windows/security/threat-protection/microsoft-defender-atp/mac-schedule-scan-atp)
11. [نشر Microsoft Defender لنقطة النهاية على macOS](#step-11-deploy-microsoft-defender-for-endpoint-on-macos)

## <a name="step-1-get-the-microsoft-defender-for-endpoint-onboarding-package"></a>الخطوة 1: الحصول على حزمة Microsoft Defender لنقطة النهاية الإلحاق

1. في [Microsoft 365 Defender](https://security.microsoft.com)، انتقل إلى **نقاط النهاية الإعدادات > > الإلحاق**.

2. حدد macOS كنظام التشغيل و Mobile إدارة الجهاز / Microsoft Intune كأسلوب نشر.

   :::image type="content" source="images/onboarding-macos.png" alt-text="الصفحة الإعدادات من مركز حماية Microsoft Defender" lightbox="images/onboarding-macos.png":::

3. حدد **تنزيل حزمة الإلحاق** (WindowsDefenderATPOnboardingPackage.zip).

4. استخراج `WindowsDefenderATPOnboardingPackage.zip`.

5. انسخ الملف إلى موقعك المفضل. على سبيل المثال، `C:\Users\JaneDoe_or_JohnDoe.contoso\Downloads\WindowsDefenderATPOnboardingPackage_macOS_MDM_contoso\jamf\WindowsDefenderATPOnboarding.plist`.

## <a name="step-2-create-a-configuration-profile-in-jamf-pro-using-the-onboarding-package"></a>الخطوة 2: إنشاء ملف تعريف تكوين في Jamf Pro باستخدام حزمة الإلحاق

1. حدد موقع الملف `WindowsDefenderATPOnboarding.plist` من المقطع السابق.

   :::image type="content" source="images/plist-onboarding-file.png" alt-text="ملف إلحاق Windows Defender ATP" lightbox="images/plist-onboarding-file.png":::

2. سجل الدخول إلى Jamf Pro، وانتقل إلى **ComputersConfiguration** >  Profiles، وحدد **"جديد**".

   :::image type="content" source="images/jamf-pro-configure-profile.png" alt-text="الصفحة التي تقوم فيها بإنشاء لوحة معلومات Pro Jamf جديدة" lightbox="images/jamf-pro-configure-profile.png":::

3. أدخل التفاصيل التالية:

   **عام**:

   - الاسم: إلحاق MDE لنظام التشغيل macOS
   - الوصف: إعداد MDE الكشف التلقائي والاستجابة على النقط النهائية لنظام التشغيل macOS
   - الفئة: بلا
   - طريقة التوزيع: التثبيت تلقائيا
   - المستوى: مستوى الكمبيوتر

4.  انتقل إلى صفحة **الإعدادات المخصصة & التطبيق** وحدد **Upload** >  **Add**.

   :::image type="content" source="images/jamfpro-mac-profile.png" alt-text="تكوين التطبيق والإعدادات المخصصة" lightbox="images/jamfpro-mac-profile.png":::

5. حدد **Upload File (ملف PLIST)** ثم في **مفتاح الإدخال Enter لمجال التفضيل**: `com.microsoft.wdav.atp`.

   :::image type="content" source="images/jamfpro-plist-upload.png" alt-text="ملف تحميل jamfpro plist" lightbox="images/jamfpro-plist-upload.png":::

   :::image type="content" source="images/jamfpro-plist-file.png" alt-text="ملف قائمة خصائص ملف التحميل" lightbox="images/jamfpro-plist-file.png":::

6. حدد **"فتح** " وحدد ملف الإلحاق.

   :::image type="content" source="images/jamfpro-plist-file-onboard.png" alt-text="ملف الإلحاق" lightbox="images/jamfpro-plist-file-onboard.png":::

7. حدد **Upload**.

   :::image type="content" source="images/jamfpro-upload-plist.png" alt-text="ملف plist الذي يتم تحميله" lightbox="images/jamfpro-upload-plist.png":::

8. حدد علامة التبويب **"النطاق** ".

   :::image type="content" source="images/jamfpro-scope-tab.png" alt-text="علامة التبويب &quot;نطاق&quot;" lightbox="images/jamfpro-scope-tab.png":::

9. حدد أجهزة الكمبيوتر الهدف.

   :::image type="content" source="images/jamfpro-target-computer.png" alt-text="أجهزة الكمبيوتر الهدف" lightbox="images/jamfpro-target-computer.png":::

   :::image type="content" source="images/jamfpro-targets.png" alt-text="الأهداف" lightbox="images/jamfpro-targets.png":::

10. حدد **"حفظ**".

   :::image type="content" source="images/jamfpro-deployment-target.png" alt-text="نشر أجهزة الكمبيوتر الهدف" lightbox="images/jamfpro-deployment-target.png":::

   :::image type="content" source="images/jamfpro-target-selected.png" alt-text="تحديد أجهزة الكمبيوتر الهدف" lightbox="images/jamfpro-target-selected.png":::

11. حدد **«Done»**.

    :::image type="content" source="images/jamfpro-target-group.png" alt-text="أجهزة الكمبيوتر الخاصة بمجموعة مستهدفة" lightbox="images/jamfpro-target-group.png":::

    :::image type="content" source="images/jamfpro-configuration-policies.png" alt-text="قائمة ملفات تعريف التكوين" lightbox="images/jamfpro-configuration-policies.png":::

## <a name="step-3-configure-microsoft-defender-for-endpoint-settings"></a>الخطوة 3: تكوين إعدادات Microsoft Defender لنقطة النهاية

يمكنك إما استخدام JAMF Pro واجهة المستخدم الرسومية لتحرير الإعدادات الفردية لتكوين Microsoft Defender لنقطة النهاية، أو استخدام الأسلوب القديم عن طريق إنشاء قائمة تكوين في محرر نص، وتحميلها إلى PRO JAMF.

لاحظ أنه يجب عليك استخدام هذا الاسم بالضبط `com.microsoft.wdav` **كمجال التفضيل**، Microsoft Defender لنقطة النهاية يستخدم هذا الاسم فقط ولحمل `com.microsoft.wdav.ext` الإعدادات المدارة الخاصة به!

`com.microsoft.wdav.ext`(قد يتم استخدام الإصدار في حالات نادرة عندما تفضل استخدام أسلوب واجهة المستخدم الرسومية، ولكن تحتاج أيضا إلى تكوين إعداد لم تتم إضافته إلى المخطط بعد.)

### <a name="gui-method"></a>أسلوب واجهة المستخدم الرسومية

1. قم بتنزيل ملف schema.json من [مستودع GitHub Defender](https://github.com/microsoft/mdatp-xplat/tree/master/macos/schema) واحفظه في ملف محلي:

    ```bash
    curl -o ~/Documents/schema.json https://raw.githubusercontent.com/microsoft/mdatp-xplat/master/macos/schema/schema.json
    ```

2. إنشاء ملف تعريف تكوين جديد ضمن Computers -> Configuration Profiles، أدخل التفاصيل التالية في علامة التبويب **"عام** ":

   :::image type="content" source="images/644e0f3af40c29e80ca1443535b2fe32.png" alt-text="ملف تعريف جديد" lightbox="images/644e0f3af40c29e80ca1443535b2fe32.png":::

    - الاسم: إعدادات تكوين MDATP MDAV
    - وصف:\<blank\>
    - الفئة: بلا (افتراضي)
    - المستوى: مستوى الكمبيوتر (افتراضي)
    - طريقة التوزيع: التثبيت تلقائيا (افتراضي)

3. قم بالتمرير لأسفل إلى علامة التبويب **"تطبيق & Custom الإعدادات**"، وحدد **"التطبيقات الخارجية**"، وانقر فوق **"إضافة** **مخطط مخصص" واستخدامه** كمصدر لاستخدامه لمجال التفضيل.

   :::image type="content" source="images/4137189bc3204bb09eed3aabc41afd78.png" alt-text="إضافة مخطط مخصص" lightbox="images/4137189bc3204bb09eed3aabc41afd78.png":::

4. أدخل `com.microsoft.wdav` كمجال التفضيل، وانقر فوق **"إضافة مخطط**" **Upload** ملف schema.json الذي تم تنزيله في الخطوة 1. انقر فوق **حفظ**.

   :::image type="content" source="images/a6f9f556037c42fabcfdcb1b697244cf.png" alt-text="مخطط Upload" lightbox="images/a6f9f556037c42fabcfdcb1b697244cf.png":::

5. يمكنك مشاهدة كافة إعدادات تكوين Microsoft Defender لنقطة النهاية المعتمدة أدناه، ضمن **"خصائص مجال التفضيل**". انقر فوق **"إضافة/إزالة الخصائص** " لتحديد الإعدادات التي تريد إدارتها، ثم انقر فوق **"موافق** " لحفظ التغييرات. (لن يتم تضمين الإعدادات المتبقية غير المحددة في التكوين المدار، سيتمكن المستخدم النهائي من تكوين هذه الإعدادات على أجهزته.)

   :::image type="content" source="images/817b3b760d11467abe9bdd519513f54f.png" alt-text="الإعدادات المدارة المختارة" lightbox="images/817b3b760d11467abe9bdd519513f54f.png":::

6. تغيير قيم الإعدادات إلى القيم المطلوبة. يمكنك النقر فوق **"مزيد من المعلومات** " للحصول على وثائق لإعداد معين. (يمكنك النقر فوق **معاينة Plist** لفحص شكل قائمة التكوين. انقر فوق **"محرر النموذج** " للعودة إلى المحرر المرئي.)

   :::image type="content" source="images/a14a79efd5c041bb8974cb5b12b3a9b6.png" alt-text="الصفحة التي تقوم بتغيير قيم الإعدادات عليها" lightbox="images/a14a79efd5c041bb8974cb5b12b3a9b6.png":::

7. حدد علامة التبويب **"النطاق** ".

   :::image type="content" source="images/9fc17529e5577eefd773c658ec576a7d.png" alt-text="نطاق ملف تعريف التكوين" lightbox="images/9fc17529e5577eefd773c658ec576a7d.png":::

8. حدد **مجموعة الأجهزة الخاصة ب Contoso**.

9. حدد **"إضافة**"، ثم حدد **"حفظ**".

   :::image type="content" source="images/cf30438b5512ac89af1d11cbf35219a6.png" alt-text="الصفحة التي يمكنك إضافة إعدادات التكوين عليها" lightbox="images/cf30438b5512ac89af1d11cbf35219a6.png":::

   :::image type="content" source="images/6f093e42856753a3955cab7ee14f12d9.png" alt-text="الصفحة التي يمكنك حفظ إعدادات التكوين عليها" lightbox="images/6f093e42856753a3955cab7ee14f12d9.png":::

10. حدد **«Done»**. سترى **ملف تعريف التكوين** الجديد.

    :::image type="content" source="images/dd55405106da0dfc2f50f8d4525b01c8.png" alt-text="الصفحة التي تكمل فيها إعدادات التكوين" lightbox="images/dd55405106da0dfc2f50f8d4525b01c8.png":::

يضيف Microsoft Defender لنقطة النهاية إعدادات جديدة بمرور الوقت. ستتم إضافة هذه الإعدادات الجديدة إلى المخطط، وسيتم نشر إصدار جديد إلى Github.
كل ما عليك القيام به للحصول على تحديثات هو تنزيل مخطط محدث وتحرير ملف تعريف التكوين الموجود **وتحرير المخطط** في علامة التبويب **"تطبيق & Custom الإعدادات**".

### <a name="legacy-method"></a>أسلوب قديم

1. استخدم إعدادات تكوين Microsoft Defender لنقطة النهاية التالية:

    - enableRealTimeProtection
    - نموذج سلبي

    > [!NOTE]
    > غير مشغل بشكل افتراضي، إذا كنت تخطط لتشغيل AV تابع لجهة خارجية لنظام التشغيل macOS، فقم بتعيينه إلى `true`.

    - الاستبعادات
    - excludedPath
    - excludedFileExtension
    - excludedFileName
    - exclusionsMergePolicy
    - الميزات المسموح بها

    > [!NOTE]
    > EICAR على العينة، إذا كنت تمر بإثبات المفهوم، قم بإزالته خاصة إذا كنت تختبر EICAR.

    - عدم السماح بThreatActions
    - potentially_unwanted_application
    - archive_bomb
    - cloudService
    - automaticSampleSubmission
    - العلامات
    - إخفاءStatusMenuIcon

     للحصول على معلومات، راجع [قائمة الخصائص لملف تعريف التكوين الكامل ل JAMF](mac-preferences.md#property-list-for-jamf-full-configuration-profile).

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

2. حفظ الملف ك `MDATP_MDAV_configuration_settings.plist`.

3. في لوحة معلومات Pro Jamf، افتح **أجهزة الكمبيوتر** **وملفات تعريف التكوين الخاصة بها**. انقر فوق **"جديد"** وقم بالتبديل إلى علامة التبويب **"عام** ".

   :::image type="content" source="images/644e0f3af40c29e80ca1443535b2fe32.png" alt-text="الصفحة التي تعرض ملف تعريف جديد" lightbox="images/644e0f3af40c29e80ca1443535b2fe32.png":::

4. أدخل التفاصيل التالية:

    **عام**

    - الاسم: إعدادات تكوين MDATP MDAV
    - وصف:\<blank\>
    - الفئة: بلا (افتراضي)
    - طريقة التوزيع: التثبيت تلقائيا (افتراضي)
    - المستوى: مستوى الكمبيوتر (افتراضي)

    :::image type="content" source="images/3160906404bc5a2edf84d1d015894e3b.png" alt-text="إعدادات تكوين MDATP MDAV" lightbox="images/3160906404bc5a2edf84d1d015894e3b.png":::

5. في **تطبيق & مخصص الإعدادات** حدد **Configure**.

   :::image type="content" source="images/e1cc1e48ec9d5d688087b4d771e668d2.png" alt-text="التطبيق والإعدادات المخصصة" lightbox="images/e1cc1e48ec9d5d688087b4d771e668d2.png":::

6. حدد **ملف Upload (ملف PLIST).**

   :::image type="content" source="images/6f85269276b2278eca4bce84f935f87b.png" alt-text="ملف قائمة إعدادات التكوين" lightbox="images/6f85269276b2278eca4bce84f935f87b.png":::

7. في **مجال التفضيلات**، أدخل`com.microsoft.wdav`، ثم حدد **Upload ملف PLIST**.

   :::image type="content" source="images/db15f147dd959e872a044184711d7d46.png" alt-text="مجال تفضيلات إعدادات التكوين" lightbox="images/db15f147dd959e872a044184711d7d46.png":::

8. حدد **"اختيار ملف**".

    :::image type="content" source="images/526e978761fc571cca06907da7b01fd6.png" alt-text="المطالبة باختيار ملف plist" lightbox="images/526e978761fc571cca06907da7b01fd6.png":::

9. حدد **MDATP_MDAV_configuration_settings.plist**، ثم حدد **Open**.

   :::image type="content" source="images/98acea3750113b8dbab334296e833003.png" alt-text="إعدادات تكوين mdatpmdav" lightbox="images/98acea3750113b8dbab334296e833003.png":::

10. حدد **Upload**.

    :::image type="content" source="images/0adb21c13206861ba9b30a879ade93d3.png" alt-text="تحميل إعداد التكوين" lightbox="images/0adb21c13206861ba9b30a879ade93d3.png":::

    :::image type="content" source="images/f624de59b3cc86e3e2d32ae5de093e02.png" alt-text="المطالبة بتحميل الصورة المتعلقة بإعدادات التكوين" lightbox="images/f624de59b3cc86e3e2d32ae5de093e02.png":::

    > [!NOTE]
    > إذا حدث لك تحميل ملف Intune، فستحصل على الخطأ التالي:
    >
    > :::image type="content" source="images/8e69f867664668796a3b2904896f0436.png" alt-text="المطالبة بتحميل ملف intune المتعلق بإعدادات التكوين" lightbox="images/8e69f867664668796a3b2904896f0436.png":::

11. حدد **"حفظ**".

    :::image type="content" source="images/1b6b5a4edcb42d97f1e70a6a0fa48e3a.png" alt-text="خيار حفظ الصورة المتعلقة بإعدادات التكوين" lightbox="images/1b6b5a4edcb42d97f1e70a6a0fa48e3a.png":::

12. يتم تحميل الملف.

    :::image type="content" source="images/33e2b2a1611fdddf6b5b79e54496e3bb.png" alt-text="الملف الذي تم تحميله المتعلق بإعدادات التكوين" lightbox="images/33e2b2a1611fdddf6b5b79e54496e3bb.png":::

    :::image type="content" source="images/a422e57fe8d45689227e784443e51bd1.png" alt-text="صفحة إعدادات التكوين" lightbox="images/a422e57fe8d45689227e784443e51bd1.png":::

13. حدد علامة التبويب **"النطاق** ".

    :::image type="content" source="images/9fc17529e5577eefd773c658ec576a7d.png" alt-text="نطاق إعدادات التكوين" lightbox="images/9fc17529e5577eefd773c658ec576a7d.png":::

14. حدد **مجموعة الأجهزة الخاصة ب Contoso**.

15. حدد **"إضافة**"، ثم حدد **"حفظ**".

    :::image type="content" source="images/cf30438b5512ac89af1d11cbf35219a6.png" alt-text="إضافة إعدادات التكوين" lightbox="images/cf30438b5512ac89af1d11cbf35219a6.png":::

    :::image type="content" source="images/6f093e42856753a3955cab7ee14f12d9.png" alt-text="إعلام إعدادات التكوين" lightbox="images/6f093e42856753a3955cab7ee14f12d9.png":::

16. حدد **«Done»**. سترى **ملف تعريف التكوين** الجديد.

    ![صورة لصورة ملف تعريف تكوين إعدادات التكوين.](images/dd55405106da0dfc2f50f8d4525b01c8.png)
     :::image type="content" source="images/dd55405106da0dfc2f50f8d4525b01c8.png" alt-text="إعدادات ملف تعريف التكوين" lightbox="images/dd55405106da0dfc2f50f8d4525b01c8.png":::

## <a name="step-4-configure-notifications-settings"></a>الخطوة 4: تكوين إعدادات الإعلامات

تنطبق هذه الخطوات على macOS 10.15 (Catalina) أو الأحدث.

1. في لوحة معلومات Pro Jamf، حدد **"Computers**"، ثم **"Configuration Profiles**".

2. انقر فوق **"جديد**"، وأدخل التفاصيل التالية **للخيارات**:

    - علامة التبويب **العامة**:
        - **الاسم**: إعدادات إعلام MDATP MDAV
        - **الوصف**: macOS 10.15 (Catalina) أو أحدث
        - **الفئة**: بلا *(افتراضي)*
        - **طريقة التوزيع**: التثبيت تلقائيا *(افتراضي)*
        - **المستوى**: مستوى الكمبيوتر *(افتراضي)*

        :::image type="content" source="images/c9820a5ff84aaf21635c04a23a97ca93.png" alt-text="صفحة ملف تعريف تكوين macOS الجديدة" lightbox="images/c9820a5ff84aaf21635c04a23a97ca93.png":::

    - **إعلامات** علامة التبويب، انقر فوق **"إضافة**"، وأدخل القيم التالية:
        - **معرف المجموعة**: `com.microsoft.wdav.tray`
        - **التنبيهات الهامة**: انقر فوق **تعطيل**
        - **الإعلامات**: انقر فوق **"تمكين"**
        - **نوع تنبيه الشعار**: حدد **"تضمين** " و **"مؤقت"** *(افتراضي)*
        - **الإعلامات على شاشة التأمين**: انقر فوق **"إخفاء"**
        - **الإعلامات في مركز الإعلامات**: انقر فوق **"عرض"**
        - **أيقونة تطبيق الشارة**: انقر فوق **"عرض"**

        :::image type="content" source="images/7f9138053dbcbf928e5182ee7b295ebe.png" alt-text="أدوات إعلامات mdatpmdav لإعدادات التكوين" lightbox="images/7f9138053dbcbf928e5182ee7b295ebe.png":::

    - **إعلامات** علامات التبويب، انقر فوق **"إضافة** مرة أخرى"، ثم قم بالتمرير لأسفل إلى **"إعلامات جديدة" الإعدادات**
        - **معرف المجموعة**: `com.microsoft.autoupdate.fba`
        - تكوين باقي الإعدادات إلى نفس القيم كما هو موضح أعلاه

        :::image type="content" source="images/4bac6ce277aedfb4a674f2d9fcb2599a.png" alt-text="إعدادات التكوين mdatpmdav notifications mau" lightbox="images/4bac6ce277aedfb4a674f2d9fcb2599a.png":::

        لاحظ أن لديك الآن "جدولين" مع تكوينات الإعلام، أحدهما **لمعرف المجموعة: com.microsoft.wdav.tray**، وآخر **لمعرف الحزمة: com.microsoft.autoupdate.fba**. بينما يمكنك تكوين إعدادات التنبيه وفقا لمتطلباتك، يجب أن تكون معرفات المجموعة هي نفسها تماما كما هو موضح من قبل، ويجب أن يكون مفتاح **التضمين** **قيد التشغيل** **للإعلامات**.

3. حدد علامة التبويب **"نطاق** "، ثم حدد **"إضافة**".

   :::image type="content" source="images/441aa2ecd36abadcdd8aed03556080b5.png" alt-text="الصفحة التي يمكنك إضافة قيم لإعدادات التكوين عليها" lightbox="images/441aa2ecd36abadcdd8aed03556080b5.png":::

4. حدد **مجموعة الأجهزة الخاصة ب Contoso**.

5. حدد **"إضافة**"، ثم حدد **"حفظ**".

   :::image type="content" source="images/09a275e321268e5e3ac0c0865d3e2db5.png" alt-text="الصفحة التي يمكنك حفظ القيم فيها لمجموعة أجهزة contoso لإعدادات التكوين" lightbox="images/09a275e321268e5e3ac0c0865d3e2db5.png":::

   :::image type="content" source="images/4d2d1d4ee13d3f840f425924c3df0d51.png" alt-text="الصفحة التي تعرض إعلام الإكمال لإعدادات التكوين" lightbox="images/4d2d1d4ee13d3f840f425924c3df0d51.png":::

6. حدد **«Done»**. سترى **ملف تعريف التكوين** الجديد.

   :::image type="content" source="images/633ad26b8bf24ec683c98b2feb884bdf.png" alt-text="إعدادات التكوين المكتملة" lightbox="images/633ad26b8bf24ec683c98b2feb884bdf.png":::

## <a name="step-5-configure-microsoft-autoupdate-mau"></a>الخطوة 5: تكوين التحديث التلقائي لبرامج Microsoft (MAU)

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

3. في لوحة معلومات Pro Jamf، حدد **"عام**".

   :::image type="content" source="images/eaba2a23dd34f73bf59e826217ba6f15.png" alt-text="إعدادات التكوين" lightbox="images/eaba2a23dd34f73bf59e826217ba6f15.png":::

4. أدخل التفاصيل التالية:

    **عام**

    - الاسم: إعدادات MDATP MDAV MAU
    - الوصف: إعدادات التحديث التلقائي لبرامج Microsoft ل MDATP لنظام التشغيل macOS
    - الفئة: بلا (افتراضي)
    - طريقة التوزيع: التثبيت تلقائيا (افتراضي)
    - المستوى: مستوى الكمبيوتر (افتراضي)

5. في **تطبيق & مخصص الإعدادات** حدد **Configure**.

   :::image type="content" source="images/1f72e9c15eaafcabf1504397e99be311.png" alt-text="تطبيق إعداد التكوين والإعدادات المخصصة" lightbox="images/1f72e9c15eaafcabf1504397e99be311.png":::

6. حدد **ملف Upload (ملف PLIST).**

7. في **مجال التفضيل**، أدخل: `com.microsoft.autoupdate2`ثم حدد **Upload ملف PLIST**.

   :::image type="content" source="images/1213872db5833aa8be535da57653219f.png" alt-text="مجال تفضيل إعداد التكوين" lightbox="images/1213872db5833aa8be535da57653219f.png":::
    

8. حدد **"اختيار ملف**".

   :::image type="content" source="images/335aff58950ce62d1dabc289ecdce9ed.png" alt-text="المطالبة باختيار الملف المتعلق بإعداد التكوين" lightbox="images/335aff58950ce62d1dabc289ecdce9ed.png":::

9. حدد **MDATP_MDAV_MAU_settings.plist**.

   :::image type="content" source="images/a26bd4967cd54bb113a2c8d32894c3de.png" alt-text="إعدادات mdatpmdavmau" lightbox="images/a26bd4967cd54bb113a2c8d32894c3de.png":::

10. حدد **Upload**.
    :::image type="content" source="images/4239ca0528efb0734e4ca0b490bfb22d.png" alt-text="تحميل الملف فيما يتعلق بإعداد التكوين" lightbox="images/4239ca0528efb0734e4ca0b490bfb22d.png":::

    :::image type="content" source="images/4ec20e72c8aed9a4c16912e01692436a.png" alt-text="الصفحة التي تعرض خيار التحميل للملف فيما يتعلق بإعداد التكوين" lightbox="images/4ec20e72c8aed9a4c16912e01692436a.png":::

11. حدد **"حفظ**".

    :::image type="content" source="images/253274b33e74f3f5b8d475cf8692ce4e.png" alt-text="الصفحة التي تعرض خيار الحفظ للملف فيما يتعلق بإعداد التكوين" lightbox="images/253274b33e74f3f5b8d475cf8692ce4e.png":::

12. حدد علامة التبويب **"النطاق** ".

    :::image type="content" source="images/10ab98358b2d602f3f67618735fa82fb.png" alt-text="علامة التبويب &quot;النطاق&quot; لإعدادات التكوين" lightbox="images/10ab98358b2d602f3f67618735fa82fb.png":::

13. حدد **"إضافة**".

    :::image type="content" source="images/56e6f6259b9ce3c1706ed8d666ae4947.png" alt-text="خيار إضافة أهداف النشر" lightbox="images/56e6f6259b9ce3c1706ed8d666ae4947.png":::

    :::image type="content" source="images/38c67ee1905c4747c3b26c8eba57726b.png" alt-text="الصفحة التي تضيف فيها المزيد من القيم إلى إعدادات التكوين" lightbox="images/38c67ee1905c4747c3b26c8eba57726b.png":::

    :::image type="content" source="images/321ba245f14743c1d5d51c15e99deecc.png" alt-text="الصفحة التي يمكنك إضافة المزيد من القيم إليها إلى إعدادات التكوين" lightbox="images/321ba245f14743c1d5d51c15e99deecc.png":::

14. حدد **«Done»**.

    :::image type="content" source="images/ba44cdb77e4781aa8b940fb83e3c21f7.png" alt-text="إعلام الإكمال فيما يتعلق بإعدادات التكوين" lightbox="images/ba44cdb77e4781aa8b940fb83e3c21f7.png":::

## <a name="step-6-grant-full-disk-access-to-microsoft-defender-for-endpoint"></a>الخطوة 6: منح حق الوصول الكامل إلى القرص Microsoft Defender لنقطة النهاية

1. في لوحة معلومات Pro Jamf، حدد **Configuration Profiles**.

   :::image type="content" source="images/264493cd01e62c7085659d6fdc26dc91.png" alt-text="ملف التعريف الذي سيتم تكوين الإعدادات له" lightbox="images/264493cd01e62c7085659d6fdc26dc91.png":::

2. حدد **+ جديد**.

3. أدخل التفاصيل التالية:

    **عام**
    - الاسم: MDATP MDAV - منح حق الوصول إلى القرص الكامل إلى الكشف التلقائي والاستجابة على النقط النهائية وAV
    - الوصف: على macOS Catalina أو الأحدث، عنصر تحكم نهج تفضيلات الخصوصية الجديد
    - الفئة: بلا
    - طريقة التوزيع: التثبيت تلقائيا
    - المستوى: مستوى الكمبيوتر

    :::image type="content" source="images/ba3d40399e1a6d09214ecbb2b341923f.png" alt-text="إعداد التكوين بشكل عام" lightbox="images/ba3d40399e1a6d09214ecbb2b341923f.png":::
    

4. في **تكوين عنصر تحكم نهج تفضيلات الخصوصية** ، حدد **Configure**.

   :::image type="content" source="images/715ae7ec8d6a262c489f94d14e1e51bb.png" alt-text="التحكم في نهج خصوصية التكوين" lightbox="images/715ae7ec8d6a262c489f94d14e1e51bb.png":::

5. في **التحكم في نهج تفضيلات الخصوصية**، أدخل التفاصيل التالية:

    - المعرف: `com.microsoft.wdav`
    - نوع المعرف: معرف المجموعة
    - متطلبات التعليمات البرمجية: `identifier "com.microsoft.wdav" and anchor apple generic and certificate 1[field.1.2.840.113635.100.6.2.6] /* exists */ and certificate leaf[field.1.2.840.113635.100.6.1.13] /* exists */ and certificate leaf[subject.OU] = UBF8T346G9`

    :::image type="content" source="images/22cb439de958101c0a12f3038f905b27.png" alt-text="تفاصيل التحكم في نهج تفضيلات الخصوصية لإعداد التكوين" lightbox="images/22cb439de958101c0a12f3038f905b27.png":::

6. حدد **+ إضافة**.

   :::image type="content" source="images/bd93e78b74c2660a0541af4690dd9485.png" alt-text="يضيف إعداد التكوين خيار كافة الملفات لنهج النظام" lightbox="images/bd93e78b74c2660a0541af4690dd9485.png":::

    - ضمن التطبيق أو الخدمة: تعيين إلى **SystemPolicyAllFiles**

    - ضمن "access": تعيين إلى **السماح**

7. حدد **"حفظ** " (وليس الحفظ الموجود في أسفل اليمين).

   :::image type="content" source="images/6de50b4a897408ddc6ded56a09c09fe2.png" alt-text="عملية الحفظ لإعداد التكوين" lightbox="images/6de50b4a897408ddc6ded56a09c09fe2.png":::

8. `+` انقر فوق العلامة الموجودة بجانب **App Access** لإضافة إدخال جديد.

   :::image type="content" source="images/tcc-add-entry.png" alt-text="عملية الحفظ المتعلقة بإعداد التكوين" lightbox="images/tcc-add-entry.png":::

9. أدخل التفاصيل التالية:

    - المعرف: `com.microsoft.wdav.epsext`
    - نوع المعرف: معرف المجموعة
    - متطلبات التعليمات البرمجية: `identifier "com.microsoft.wdav.epsext" and anchor apple generic and certificate 1[field.1.2.840.113635.100.6.2.6] /* exists */ and certificate leaf[field.1.2.840.113635.100.6.1.13] /* exists */ and certificate leaf[subject.OU] = UBF8T346G9`

10. حدد **+ إضافة**.

    :::image type="content" source="images/tcc-epsext-entry.png" alt-text="إدخال tcc epsext لإعداد التكوين" lightbox="images/tcc-epsext-entry.png":::

    - ضمن التطبيق أو الخدمة: تعيين إلى **SystemPolicyAllFiles**

    - ضمن "access": تعيين إلى **السماح**

11. حدد **"حفظ** " (وليس الحفظ الموجود في أسفل اليمين).

    :::image type="content" source="images/tcc-epsext-entry2.png" alt-text="المثيل الآخر لإعداد التكوين tcc epsext" lightbox="images/tcc-epsext-entry2.png":::

12. حدد علامة التبويب **"النطاق** ".

    :::image type="content" source="images/2c49b16cd112729b3719724f581e6882.png" alt-text="الصفحة التي تصور نطاق إعداد التكوين" lightbox="images/2c49b16cd112729b3719724f581e6882.png":::

13. حدد **+ إضافة**.

    :::image type="content" source="images/57cef926d1b9260fb74a5f460cee887a.png" alt-text="الصفحة التي تصور إعداد التكوين" lightbox="images/57cef926d1b9260fb74a5f460cee887a.png":::

14. حدد " **مجموعات الكمبيوتر** " > ضمن **"اسم المجموعة** " > حدد **"مجموعة الأجهزة" الخاصة ب Contoso**.

    :::image type="content" source="images/368d35b3d6179af92ffdbfd93b226b69.png" alt-text="مجموعة أجهزة contoso لإعداد التكوين" lightbox="images/368d35b3d6179af92ffdbfd93b226b69.png":::

15. حدد **"إضافة**".

16. حدد **"حفظ**".

17. حدد **«Done»**.

    :::image type="content" source="images/809cef630281b64b8f07f20913b0039b.png" alt-text="مجموعة أجهزة contoso لإعداد التكوين" lightbox="images/809cef630281b64b8f07f20913b0039b.png":::

    :::image type="content" source="images/6c8b406ee224335a8c65d06953dc756e.png" alt-text="رسم توضيحي لإعداد التكوين" lightbox="images/6c8b406ee224335a8c65d06953dc756e.png":::

بدلا من ذلك، يمكنك تنزيل [fulldisk.mobileconfig](https://github.com/microsoft/mdatp-xplat/blob/master/macos/mobileconfig/profiles/fulldisk.mobileconfig) وتحميله إلى ملفات تعريف تكوين JAMF كما هو موضح في [نشر ملفات تعريف التكوين المخصصة باستخدام Jamf Pro| الطريقة 2: Upload ملف تعريف التكوين إلى Jamf Pro](https://www.jamf.com/jamf-nation/articles/648/deploying-custom-configuration-profiles-using-jamf-pro).

## <a name="step-7-approve-kernel-extension-for-microsoft-defender-for-endpoint"></a>الخطوة 7: الموافقة على ملحق Kernel Microsoft Defender لنقطة النهاية

> [!CAUTION]
> لا تدعم أجهزة Apple Silicon (M1) KEXT. سيفشل تثبيت ملف تعريف تكوين يتكون من نهج KEXT على هذه الأجهزة.

1. في **ملفات تعريف التكوين**، حدد **+ جديد**.

   :::image type="content" source="images/6c8b406ee224335a8c65d06953dc756e.png" alt-text="وصف نشر وسائل التواصل الاجتماعي الذي تم إنشاؤه تلقائيا" lightbox="images/6c8b406ee224335a8c65d06953dc756e.png":::

2. أدخل التفاصيل التالية:

    **عام**

    - الاسم: ملحق MDATP MDAV Kernel
    - الوصف: ملحق kernel MDATP (kext)
    - الفئة: بلا
    - طريقة التوزيع: التثبيت تلقائيا
    - المستوى: مستوى الكمبيوتر

    :::image type="content" source="images/24e290f5fc309932cf41f3a280d22c14.png" alt-text="نواة إعدادات التكوين mdatpmdav" lightbox="images/24e290f5fc309932cf41f3a280d22c14.png":::

3. في **تكوين ملحقات Kernel المعتمدة** ، حدد **Configure**.

   :::image type="content" source="images/30be88b63abc5e8dde11b73f1b1ade6a.png" alt-text="الصفحة التي تعرض إعدادات التكوين المعتمدة لملحقات النواة" lightbox="images/30be88b63abc5e8dde11b73f1b1ade6a.png":::

4. في **ملحقات Kernel المعتمدة** ، أدخل التفاصيل التالية:

    - اسم العرض: Microsoft Corp.
    - معرف الفريق: UBF8T346G9

    :::image type="content" source="images/39cf120d3ac3652292d8d1b6d057bd60.png" alt-text="جزء ملحقات Kernel المعتمدة" lightbox="images/39cf120d3ac3652292d8d1b6d057bd60.png":::

5. حدد علامة التبويب **"النطاق** ".

   :::image type="content" source="images/0df36fc308ba569db204ee32db3fb40a.png" alt-text="علامة التبويب &quot;النطاق&quot; للتكوين" lightbox="images/0df36fc308ba569db204ee32db3fb40a.png":::

6. حدد **+ إضافة**.

7. حدد مجموعات **الكمبيوتر** > ضمن **اسم المجموعة** > حدد **مجموعة الأجهزة الخاصة ب Contoso**.

8. حدد **+ إضافة**.

   :::image type="content" source="images/0dde8a4c41110dbc398c485433a81359.png" alt-text="الصفحة التي تقوم بتعريف قيم إضافية لإعدادات التكوين عليها" lightbox="images/0dde8a4c41110dbc398c485433a81359.png":::

9. حدد **"حفظ**".

   :::image type="content" source="images/0add8019b85a453b47fa5c402c72761b.png" alt-text="ملحق MDATP MDAV Kernel" lightbox="images/0add8019b85a453b47fa5c402c72761b.png":::

10. حدد **«Done»**.

    :::image type="content" source="images/1c9bd3f68db20b80193dac18f33c22d0.png" alt-text="صفحة تفاصيل ملفات تعريف التكوين" lightbox="images/1c9bd3f68db20b80193dac18f33c22d0.png":::

بدلا من ذلك، يمكنك تنزيل [kext.mobileconfig](https://github.com/microsoft/mdatp-xplat/blob/master/macos/mobileconfig/profiles/kext.mobileconfig) وتحميله إلى ملفات تعريف تكوين JAMF كما هو موضح في [نشر ملفات تعريف التكوين المخصصة باستخدام Jamf Pro| الطريقة 2: Upload ملف تعريف التكوين إلى Jamf Pro](https://www.jamf.com/jamf-nation/articles/648/deploying-custom-configuration-profiles-using-jamf-pro).

## <a name="step-8-approve-system-extensions-for-microsoft-defender-for-endpoint"></a>الخطوة 8: الموافقة على ملحقات النظام Microsoft Defender لنقطة النهاية

1. في **ملفات تعريف التكوين**، حدد **+ جديد**.

   :::image type="content" source="images/6c8b406ee224335a8c65d06953dc756e.png" alt-text="وصف منشور وسائل التواصل الاجتماعي الذي تم إنشاؤه تلقائيا" lightbox="images/6c8b406ee224335a8c65d06953dc756e.png":::

2. أدخل التفاصيل التالية:

    **عام**

    - الاسم: ملحقات نظام MDATP MDAV
    - الوصف: ملحقات نظام MDATP
    - الفئة: بلا
    - طريقة التوزيع: التثبيت تلقائيا
    - المستوى: مستوى الكمبيوتر

    :::image type="content" source="images/sysext-new-profile.png" alt-text="ملف تعريف جديد لإعدادات التكوين sysext" lightbox="images/sysext-new-profile.png":::

3. في **System Extensions** حدد **Configure**.

   :::image type="content" source="images/sysext-configure.png" alt-text="الجزء مع خيار &quot;تكوين&quot; لملحقات النظام" lightbox="images/sysext-configure.png":::

4. في **System Extensions** أدخل التفاصيل التالية:

   - اسم العرض: Microsoft Corp. System Extensions
   - أنواع ملحقات النظام: ملحقات النظام المسموح بها
   - معرف الفريق: UBF8T346G9
   - ملحقات النظام المسموح بها:
     - **com.microsoft.wdav.epsext**
     - **com.microsoft.wdav.netext**

    :::image type="content" source="images/sysext-configure2.png" alt-text="جزء ملحقات نظام MDATP MDAV" lightbox="images/sysext-configure2.png":::

5. حدد علامة التبويب **"النطاق** ".

   :::image type="content" source="images/0df36fc308ba569db204ee32db3fb40a.png" alt-text="جزء تحديد أجهزة الكمبيوتر الهدف" lightbox="images/0df36fc308ba569db204ee32db3fb40a.png":::

6. حدد **+ إضافة**.

7. حدد مجموعات **الكمبيوتر** > ضمن **اسم المجموعة** > حدد **مجموعة الأجهزة الخاصة ب Contoso**.

8. حدد **+ إضافة**.

   :::image type="content" source="images/0dde8a4c41110dbc398c485433a81359.png" alt-text="جزء ملف تعريف تكوين macOS الجديد" lightbox="images/0dde8a4c41110dbc398c485433a81359.png":::

9. حدد **"حفظ**".

   :::image type="content" source="images/sysext-scope.png" alt-text="عرض الخيارات المتعلقة بملحقات نظام MDATP MDAV" lightbox="images/sysext-scope.png":::

10. حدد **«Done»**.

    :::image type="content" source="images/sysext-final.png" alt-text="إعدادات التكوين sysext - النهائي" lightbox="images/sysext-final.png":::

## <a name="step-9-configure-network-extension"></a>الخطوة 9: تكوين ملحق الشبكة

كجزء من قدرات الكشف عن نقطة النهاية والاستجابة لها، يقوم Microsoft Defender لنقطة النهاية على macOS بفحص حركة مرور مأخذ التوصيل ويبلغ عن هذه المعلومات إلى مدخل Microsoft 365 Defender. يسمح النهج التالي لملحق الشبكة بتنفيذ هذه الوظيفة.

تنطبق هذه الخطوات على macOS 10.15 (Catalina) أو الأحدث.

1. في لوحة معلومات Pro Jamf، حدد **"Computers**"، ثم **"Configuration Profiles**".

2. انقر فوق **"جديد**"، وأدخل التفاصيل التالية **للخيارات**:

    - علامة التبويب **العامة**:
        - **الاسم**: ملحق شبكة Microsoft Defender
        - **الوصف**: macOS 10.15 (Catalina) أو أحدث
        - **الفئة**: بلا *(افتراضي)*
        - **طريقة التوزيع**: التثبيت تلقائيا *(افتراضي)*
        - **المستوى**: مستوى الكمبيوتر *(افتراضي)*

    - **عامل تصفية محتوى** علامة التبويب:
        - **اسم عامل التصفية**: عامل تصفية محتوى Microsoft Defender
        - **المعرف**: `com.microsoft.wdav`
        - اترك **عنوان الخدمة** **والمؤسسة** **واسم المستخدم** **وكلمة المرور** **والشهادة** فارغة (*لم* يتم تحديد **"تضمين**")
        - **ترتيب عامل التصفية**: مركز التحكم
        - **عامل تصفية مأخذ التوصيل**: `com.microsoft.wdav.netext`
        - **المتطلب المعين لتصفية مأخذ التوصيل**: `identifier "com.microsoft.wdav.netext" and anchor apple generic and certificate 1[field.1.2.840.113635.100.6.2.6] /* exists */ and certificate leaf[field.1.2.840.113635.100.6.1.13] /* exists */ and certificate leaf[subject.OU] = UBF8T346G9`
        - ترك حقول **"تصفية الشبكة"** فارغة (*لم* يتم تحديد **"تضمين**")

        لاحظ أن **المعرف** **وعامل تصفية مأخذ التوصيل** **وعامل تصفية مأخذ التوصيل قيم المتطلب المحددة** بالضبط كما هو محدد أعلاه.

        :::image type="content" source="images/netext-create-profile.png" alt-text="إعداد تكوين mdatpmdav" lightbox="images/netext-create-profile.png":::

3. حدد علامة التبويب **"النطاق** ".

   :::image type="content" source="images/0df36fc308ba569db204ee32db3fb40a.png" alt-text="علامة التبويب sco لإعدادات التكوين" lightbox="images/0df36fc308ba569db204ee32db3fb40a.png":::

4. حدد **+ إضافة**.

5. حدد مجموعات **الكمبيوتر** > ضمن **اسم المجموعة** > حدد **مجموعة الأجهزة الخاصة ب Contoso**.

6. حدد **+ إضافة**.

   :::image type="content" source="images/0dde8a4c41110dbc398c485433a81359.png" alt-text="adim لإعدادات التكوين" lightbox="images/0dde8a4c41110dbc398c485433a81359.png":::

7. حدد **"حفظ**".

   :::image type="content" source="images/netext-scope.png" alt-text="جزء &quot;تصفية المحتوى&quot;" lightbox="images/netext-scope.png":::

8. حدد **«Done»**.

   :::image type="content" source="images/netext-final.png" alt-text="netext لإعدادات التكوين - النهائي" lightbox="images/netext-final.png":::

بدلا من ذلك، يمكنك تنزيل [netfilter.mobileconfig](https://github.com/microsoft/mdatp-xplat/blob/master/macos/mobileconfig/profiles/netfilter.mobileconfig) وتحميله إلى ملفات تعريف تكوين JAMF كما هو موضح في [نشر ملفات تعريف التكوين المخصصة باستخدام Jamf Pro| الطريقة 2: Upload ملف تعريف التكوين إلى Jamf Pro](https://www.jamf.com/jamf-nation/articles/648/deploying-custom-configuration-profiles-using-jamf-pro).

## <a name="step-10-schedule-scans-with-microsoft-defender-for-endpoint-on-macos"></a>الخطوة 10: جدولة عمليات الفحص باستخدام Microsoft Defender لنقطة النهاية على macOS

اتبع الإرشادات المتعلقة [بمسح الجدول باستخدام Microsoft Defender لنقطة النهاية على macOS](/windows/security/threat-protection/microsoft-defender-atp/mac-schedule-scan-atp).

## <a name="step-11-deploy-microsoft-defender-for-endpoint-on-macos"></a>الخطوة 11: نشر Microsoft Defender لنقطة النهاية على macOS

1. انتقل إلى المكان الذي حفظت `wdav.pkg`فيه.

   :::image type="content" source="images/8dde76b5463047423f8637c86b05c29d.png" alt-text="حزمة مستكشف الملفات wdav" lightbox="images/8dde76b5463047423f8637c86b05c29d.png":::

2. إعادة تسميته إلى `wdav_MDM_Contoso_200329.pkg`.

   :::image type="content" source="images/fb2220fed3a530f4b3ef36f600da0c27.png" alt-text="حزمة مستكشف الملفات1 wdavmdm" lightbox="images/fb2220fed3a530f4b3ef36f600da0c27.png":::

3. افتح لوحة معلومات Pro Jamf.

   :::image type="content" source="images/990742cd9a15ca9fdd37c9f695d1b9f4.png" alt-text="إعدادات التكوين ل jamfpro" lightbox="images/990742cd9a15ca9fdd37c9f695d1b9f4.png":::

4. حدد الكمبيوتر وانقر فوق أيقونة الترس في الأعلى، ثم حدد **إدارة الكمبيوتر**.

   :::image type="content" source="images/b6d671b2f18b89d96c1c8e2ea1991242.png" alt-text="إعدادات التكوين - إدارة الكمبيوتر" lightbox="images/b6d671b2f18b89d96c1c8e2ea1991242.png":::

5. في **الحزم**، حدد **+ جديد**.
   :::image type="content" source="images/57aa4d21e2ccc65466bf284701d4e961.png" alt-text="وصف الطيور لحزمة تم إنشاؤها تلقائيا" lightbox="images/57aa4d21e2ccc65466bf284701d4e961.png":::

6. في **الحزمة الجديدة** ، أدخل التفاصيل التالية:

    **علامة التبويب "عام"**
    - اسم العرض: اتركه فارغا في الوقت الحالي. لأنه سيتم إعادة تعيينه عند اختيار pkg.
    - الفئة: بلا (افتراضي)
    - اسم الملف: اختيار ملف

    :::image type="content" source="images/21de3658bf58b1b767a17358a3f06341.png" alt-text="علامة التبويب &quot;عام&quot; لإعدادات التكوين" lightbox="images/21de3658bf58b1b767a17358a3f06341.png":::

    افتح الملف وأشر إليه `wdav.pkg` أو `wdav_MDM_Contoso_200329.pkg`.

    :::image type="content" source="images/1aa5aaa0a387f4e16ce55b66facc77d1.png" alt-text="شاشة الكمبيوتر التي تعرض وصف حزمة تم إنشاؤها تلقائيا" lightbox="images/1aa5aaa0a387f4e16ce55b66facc77d1.png":::

7. حدد **"فتح**". تعيين **اسم العرض** إلى **الحماية المتقدمة من التهديدات من Microsoft Defender برنامج الحماية من الفيروسات من Microsoft Defender**.

    **ملف البيان** غير مطلوب. يعمل Microsoft Defender لنقطة النهاية بدون ملف البيان.

    **علامة التبويب "خيارات"**: الاحتفاظ بالقيم الافتراضية.

    **علامة التبويب "قيود"**: احتفظ بالقيم الافتراضية.

    :::image type="content" source="images/56dac54634d13b2d3948ab50e8d3ef21.png" alt-text="علامة تبويب القيد لإعدادات التكوين" lightbox="images/56dac54634d13b2d3948ab50e8d3ef21.png":::

8. حدد **"حفظ**". يتم تحميل الحزمة إلى Jamf Pro.

   :::image type="content" source="images/33f1ecdc7d4872555418bbc3efe4b7a3.png" alt-text="عملية تحميل حزمة إعدادات التكوين للحزمة المتعلقة بإعدادات التكوين" lightbox="images/33f1ecdc7d4872555418bbc3efe4b7a3.png":::

   قد يستغرق الأمر بضع دقائق حتى تكون الحزمة متوفرة للتوزيع.

   :::image type="content" source="images/1626d138e6309c6e87bfaab64f5ccf7b.png" alt-text="مثيل لتحميل الحزمة لإعدادات التكوين" lightbox="images/1626d138e6309c6e87bfaab64f5ccf7b.png":::

9. انتقل إلى صفحة **النهج** .

   :::image type="content" source="images/f878f8efa5ebc92d069f4b8f79f62c7f.png" alt-text="نهج إعدادات التكوين" lightbox="images/f878f8efa5ebc92d069f4b8f79f62c7f.png":::

10. حدد **+ جديد** لإنشاء نهج جديد.

    :::image type="content" source="images/847b70e54ed04787e415f5180414b310.png" alt-text="نهج إعدادات التكوين الجديد" lightbox="images/847b70e54ed04787e415f5180414b310.png":::


11. **بشكل عام**، أدخل التفاصيل التالية:

    - اسم العرض: MDATP Onboarding Contoso 200329 v100.86.92 أو إصدار أحدث

      :::image type="content" source="images/625ba6d19e8597f05e4907298a454d28.png" alt-text="إعدادات التكوين - إلحاق MDATP" lightbox="images/625ba6d19e8597f05e4907298a454d28.png":::

12. حدد **"إيداع متكرر**".

    :::image type="content" source="images/68bdbc5754dfc80aa1a024dde0fce7b0.png" alt-text="إيداع متكرر لإعدادات التكوين" lightbox="images/68bdbc5754dfc80aa1a024dde0fce7b0.png":::

13. حدد **"حفظ**".

14. حدد **"Packages > Configure**".

    :::image type="content" source="images/8fb4cc03721e1efb4a15867d5241ebfb.png" alt-text="خيار تكوين الحزم" lightbox="images/8fb4cc03721e1efb4a15867d5241ebfb.png":::

15. حدد الزر **"إضافة**" إلى جانب **الحماية المتقدمة من التهديدات من Microsoft Defender برنامج الحماية من الفيروسات من Microsoft Defender**.

    :::image type="content" source="images/526b83fbdbb31265b3d0c1e5fbbdc33a.png" alt-text="خيار إضافة المزيد من الإعدادات إلى MDATP MDA" lightbox="images/526b83fbdbb31265b3d0c1e5fbbdc33a.png":::

16. حدد **"حفظ**".

    :::image type="content" source="images/9d6e5386e652e00715ff348af72671c6.png" alt-text="خيار الحفظ لإعدادات التكوين" lightbox="images/9d6e5386e652e00715ff348af72671c6.png":::

17. حدد علامة التبويب **"النطاق** ".

    :::image type="content" source="images/8d80fe378a31143db9be0bacf7ddc5a3.png" alt-text="علامة التبويب &quot;النطاق&quot; المتعلقة بإعدادات التكوين" lightbox="images/8d80fe378a31143db9be0bacf7ddc5a3.png":::

18. حدد أجهزة الكمبيوتر الهدف.

    :::image type="content" source="images/6eda18a64a660fa149575454e54e7156.png" alt-text="خيار إضافة مجموعات الكمبيوتر" lightbox="images/6eda18a64a660fa149575454e54e7156.png":::

    **نطاق**

    حدد **"إضافة**".

    :::image type="content" source="images/1c08d097829863778d562c10c5f92b67.png" alt-text="إعدادات التكوين - ad1" lightbox="images/1c08d097829863778d562c10c5f92b67.png":::

    :::image type="content" source="images/216253cbfb6ae738b9f13496b9c799fd.png" alt-text="إعدادات التكوين - ad2" lightbox="images/216253cbfb6ae738b9f13496b9c799fd.png":::

    **الخدمة الذاتية**

    :::image type="content" source="images/c9f85bba3e96d627fe00fc5a8363b83a.png" alt-text="علامة التبويب &quot;الخدمة الذاتية&quot; لإعدادات التكوين" lightbox="images/c9f85bba3e96d627fe00fc5a8363b83a.png":::

19. حدد **«Done»**.

    :::image type="content" source="images/99679a7835b0d27d0a222bc3fdaf7f3b.png" alt-text="حالة الإلحاق في Contoso مع خيار لإكماله" lightbox="images/99679a7835b0d27d0a222bc3fdaf7f3b.png":::

    :::image type="content" source="images/632aaab79ae18d0d2b8e0c16b6ba39e2.png" alt-text="صفحة النهج" lightbox="images/632aaab79ae18d0d2b8e0c16b6ba39e2.png":::
