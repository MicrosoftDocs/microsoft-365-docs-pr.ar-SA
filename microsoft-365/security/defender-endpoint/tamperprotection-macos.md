---
title: حماية إعدادات أمان macOS باستخدام الحماية من العبث
description: استخدم الحماية من العبث لمنع التطبيقات الضارة من تغيير إعدادات أمان macOS المهمة.
keywords: macos، والحماية من العبث، وإعدادات الأمان، والبرامج الضارة
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 45a30d02992d3128ab1520c24927fb43c1180cf8
ms.sourcegitcommit: 1734c95ce72d9c8af695cb4b49b1e40d921a1fee
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/07/2022
ms.locfileid: "66857532"
---
# <a name="protect-macos-security-settings-with-tamper-protection"></a>حماية إعدادات أمان macOS باستخدام الحماية من العبث

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> هل تريد تجربة Defender لنقطة النهاية؟ [التسجيل للحصول على إصدار تجريبي مجاني.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-rbac-abovefoldlink)

[!include[Prerelease information](../../includes/prerelease.md)]


تساعد الحماية من العبث في macOS على منع إجراء التغييرات غير المرغوب فيها على إعدادات الأمان من قبل مستخدمين غير مصرح لهم. تساعد الحماية من العبث بالبيانات على منع الإزالة غير المصرح بها Microsoft Defender لنقطة النهاية على macOS. تساعد هذه الإمكانية أيضا ملفات الأمان والعمليات وإعدادات التكوين الهامة من العبث بها.

يمكنك تعيين الحماية من العبث في الأوضاع التالية:

|الموضوع|الوصف|
|---|---|
|ذوي الاحتياجات الخاصه|إيقاف تشغيل الحماية من العبث بالكامل (هذا هو الوضع الافتراضي بعد التثبيت)|
|مراجعه الحسابات|يتم تسجيل عمليات العبث، ولكن لا يتم حظرها|
|حظر|يتم الآن تشغيل الحماية من العبث، ويتم حظر عمليات العبث|

عند تعيين الحماية من العبث إلى وضع التدقيق أو الحظر، يمكنك توقع النتائج التالية:

**وضع التدقيق**:

- يتم تسجيل إجراءات إلغاء تثبيت Defender لعامل نقطة النهاية (تم تدقيقه)
- يتم تسجيل تحرير/تعديل ملفات Defender لنقطة النهاية (تدقيق)
- يتم تسجيل إنشاء ملفات جديدة ضمن موقع Defender لنقطة النهاية (مدقق)
- يتم تسجيل حذف ملفات Defender لنقطة النهاية (تدقيق)
- إعادة تسمية ملفات Defender لنقطة النهاية مسجلة (مدققة)

**وضع الحظر**:

- تم حظر إجراءات إلغاء تثبيت Defender لعامل نقطة النهاية
- يتم حظر تحرير/تعديل ملفات Defender لنقطة النهاية
- تم حظر إنشاء ملفات جديدة ضمن موقع Defender لنقطة النهاية
- تم حظر حذف ملفات Defender لنقطة النهاية
- تم حظر إعادة تسمية ملفات Defender لنقطة النهاية
- أوامر لإيقاف فشل العامل

فيما يلي مثال على رسالة النظام استجابة لإجراء محظور:

![صورة للعملية محظورة](images/operation-blocked.png)

يمكنك تكوين وضع الحماية من العبث عن طريق توفير اسم الوضع كمستوى الإنفاذ.

> [!NOTE]
>
> - سيتم تطبيق تغيير الوضع على الفور.
> - إذا استخدمت JAMF أثناء التكوين الأولي، فستحتاج إلى تحديث التكوين باستخدام JAMF أيضا.

## <a name="before-you-begin"></a>قبل البدء

- إصدارات macOS المدعومة: مونتاري (12)، بيج سور (11)، كاتالينا (10.15+).
- الحد الأدنى للإصدار المطلوب ل Defender لنقطة النهاية: 101.70.19.
- يجب أن تكون في قناة تحديث غير إنتاجية ([إما معاينة أو بيتا](/deployoffice/office-insider/deploy/microsoft-autoupdate))، بينما تكون ميزة الحماية من العبث في المعاينة. إذا كنت تستخدم قناة الإنتاج، فسيتم تجاهل وضع الحماية من العبث الذي تم تكوينه.

**الإعدادات الموصى بها بشدة:**

- تم تمكين System Integrity Protection (SIP). لمزيد من المعلومات، راجع [تعطيل وتمكين حماية تكامل النظام](https://developer.apple.com/documentation/security/disabling_and_enabling_system_integrity_protection).
- استخدم أداة إدارة أجهزة المحمول (MDM) لتكوين Microsoft Defender لنقطة النهاية.

## <a name="configure-tamper-protection-on-macos-devices"></a>تكوين الحماية من العبث بأجهزة macOS

هناك عدة طرق يمكنك من خلالها تكوين الحماية من العبث بالبيانات:

- [التكوين اليدوي](#manual-configuration)
- [JAMF](#jamf)
- [Intune](#intune)

### <a name="before-you-begin"></a>قبل البدء

تحقق من تعيين "tamper_protection" إلى "معطل" أو "تدقيق" لمراقبة تغيير الحالة.
تأكد أيضا من أن "release_ring" لا يبلغ عن "الإنتاج".

```bash
mdatp health
```

```console
healthy                                     : true
health_issues                               : []
licensed                                    : true
engine_version                              : "1.1.19300.3"
app_version                                 : "101.70.19"
org_id                                      : "..."
log_level                                   : "info"
machine_guid                                : "..."
release_ring                                : "InsiderFast"
product_expiration                          : Dec 29, 2022 at 09:48:37 PM
cloud_enabled                               : true
cloud_automatic_sample_submission_consent   : "safe"
cloud_diagnostic_enabled                    : false
passive_mode_enabled                        : false
real_time_protection_enabled                : true
real_time_protection_available              : true
real_time_protection_subsystem              : "endpoint_security_extension"
network_events_subsystem                    : "network_filter_extension"
device_control_enforcement_level            : "audit"
tamper_protection                           : "audit"
automatic_definition_update_enabled         : true
definitions_updated                         : Jul 06, 2022 at 01:57:03 PM
definitions_updated_minutes_ago             : 5
definitions_version                         : "1.369.896.0"
definitions_status                          : "up_to_date"
edr_early_preview_enabled                   : "disabled"
edr_device_tags                             : []
edr_group_ids                               : ""
edr_configuration_version                   : "20.199999.main.2022.07.05.02-ac10b0623fd381e28133debe14b39bb2dc5b61af"
edr_machine_id                              : "..."
conflicting_applications                    : []
network_protection_status                   : "stopped"
data_loss_prevention_status                 : "disabled"
full_disk_access_enabled                    : true
```

### <a name="manual-configuration"></a>التكوين اليدوي

1. استخدم الأمر التالي:

   ```console
   sudo mdatp config tamper-protection enforcement-level --value block
   ```

   ![صورة لأمر التكوين اليدوي](images/manual-config-cmd.png)

   > [!NOTE]
   > إذا كنت تستخدم التكوين اليدوي لتمكين الحماية من العبث، يمكنك أيضا تعطيل الحماية من العبث يدويا في أي وقت. على سبيل المثال، يمكنك إبطال الوصول إلى القرص الكامل من Defender في تفضيلات النظام يدويا. يجب استخدام MDM بدلا من التكوين اليدوي لمنع المسؤول المحلي من القيام بذلك.

2. تحقق من النتيجة.

  ```bash
  mdatp health
  ```

  ```console
  healthy                                     : true
  health_issues                               : []
  licensed                                    : true
  engine_version                              : "1.1.19300.3"
  app_version                                 : "101.70.19"
  org_id                                      : "..."
  log_level                                   : "info"
  machine_guid                                : "..."
  release_ring                                : "InsiderFast"
  product_expiration                          : Dec 29, 2022 at 09:48:37 PM
  cloud_enabled                               : true
  cloud_automatic_sample_submission_consent   : "safe"
  cloud_diagnostic_enabled                    : false
  passive_mode_enabled                        : false
  real_time_protection_enabled                : true
  real_time_protection_available              : true
  real_time_protection_subsystem              : "endpoint_security_extension"
  network_events_subsystem                    : "network_filter_extension"
  device_control_enforcement_level            : "audit"
  tamper_protection                           : "block"
  automatic_definition_update_enabled         : true
  definitions_updated                         : Jul 06, 2022 at 01:57:03 PM
  definitions_updated_minutes_ago             : 5
  definitions_version                         : "1.369.896.0"
  definitions_status                          : "up_to_date"
  edr_early_preview_enabled                   : "disabled"
  edr_device_tags                             : []
  edr_group_ids                               : ""
  edr_configuration_version                   : "20.199999.main.2022.07.05.02-ac10b0623fd381e28133debe14b39bb2dc5b61af"
  edr_machine_id                              : "..."
  conflicting_applications                    : []
  network_protection_status                   : "stopped"
  data_loss_prevention_status                 : "disabled"
  full_disk_access_enabled                    : true
  ```

لاحظ أن "tamper_protection" تم تعيينه الآن إلى "حظر".

### <a name="jamf"></a>JAMF

تكوين وضع الحماية من العبث في [ملف تعريف التكوين](mac-jamfpro-policies.md) Microsoft Defender لنقطة النهاية، عن طريق إضافة الإعدادات التالية:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
<plist version="1.0">
  <dict>
    <key>tamperProtection</key>
    <dict>
      <key>enforcementLevel</key>
      <string>block</string>
    </dict>
  </dict>
</plist>
```

> [!NOTE]
> إذا كان لديك بالفعل ملف تعريف تكوين Microsoft Defender لنقطة النهاية فأنت بحاجة إلى *إضافة* إعدادات إليه. لا تحتاج إلى إنشاء ملف تعريف تكوين ثان.

### <a name="intune"></a>Intune

اتبع مثال ملف تعريف Intune الموثق لتكوين الحماية من العبث من خلال Intune. لمزيد من المعلومات، راجع [تعيين تفضيلات Microsoft Defender لنقطة النهاية على macOS](mac-preferences.md).

أضف التكوين التالي في ملف تعريف Intune:

> [!NOTE]
> لتكوين Intune، يمكنك إنشاء ملف تكوين ملف تعريف جديد لإضافة تكوين الحماية من العبث، أو يمكنك إضافة هذه المعلمات إلى المعلمة الموجودة.

```xml
<?xml version="1.0" encoding="utf-8"?>
<!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
<plist version="1">
    <dict>
        <key>PayloadUUID</key>
        <string>C4E6A782-0C8D-44AB-A025-EB893987A295</string>
        <key>PayloadType</key>
        <string>Configuration</string>
        <key>PayloadOrganization</key>
        <string>Microsoft</string>
        <key>PayloadIdentifier</key>
        <string>com.microsoft.wdav</string>
        <key>PayloadDisplayName</key>
        <string>Microsoft Defender for Endpoint settings</string>
        <key>PayloadDescription</key>
        <string>Microsoft Defender for Endpoint configuration settings</string>
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
                <string>99DBC2BC-3B3A-46A2-A413-C8F9BB9A7295</string>
                <key>PayloadType</key>
                <string>com.microsoft.wdav</string>
                <key>PayloadOrganization</key>
                <string>Microsoft</string>
                <key>PayloadIdentifier</key>
                <string>com.microsoft.wdav</string>
                <key>PayloadDisplayName</key>
                <string>Microsoft Defender for Endpoint configuration settings</string>
                <key>PayloadDescription</key>
                <string/>
                <key>PayloadVersion</key>
                <integer>1</integer>
                <key>PayloadEnabled</key>
                <true/>
                <key>tamperProtection</key>
                <dict>
                             <key>enforcementLevel</key>
                             <string>block</string>
                </dict>
            </dict>
        </array>
    </dict>
</plist>
```

تحقق من حالة الحماية من العبث عن طريق تشغيل الأمر التالي:

`mdatp health --field tamper_protection`

ستظهر النتيجة "حظر" إذا كانت الحماية من العبث في:

![صورة الحماية من العبث في وضع الحظر](images/tp-block-mode.png)

يمكنك أيضا تشغيل كامل `mdatp health` والبحث عن "tamper_protection" في الإخراج

## <a name="verify-tamper-protection-preventive-capabilities"></a>التحقق من قدرات منع الحماية من العبث بالبيانات

يمكنك التحقق من تشغيل الحماية من العبث بطرق مختلفة.

### <a name="verify-block-mode"></a>التحقق من وضع الحظر

يتم رفع تنبيه العبث في مدخل Microsoft 365 Defender

![صورة تنبيه العبث الذي تم رفعه في مدخل Microsoft 365 Defender](images/tampering-sensor-portal.png)

### <a name="verify-block-mode-and-audit-modes"></a>التحقق من وضع الحظر وأوضاع التدقيق

- باستخدام التتبع المتقدم، سترى تنبيهات العبث بالتلاعب تظهر
- يمكن العثور على أحداث العبث في سجلات الأجهزة المحلية: `sudo grep -F '[{tamperProtection}]' /Library/Logs/Microsoft/mdatp/microsoft_defender_core.log`

![صورة سجل الحماية من العبث بالبيانات](images/tamper-protection-log.png)

### <a name="diy-scenarios"></a>سيناريوهات DIY

- مع تعيين الحماية من العبث ب "الحظر"، حاول أساليب مختلفة لإلغاء تثبيت Defender لنقطة النهاية. على سبيل المثال، اسحب لوحة التطبيق إلى سلة المهملات أو قم بإلغاء تثبيت الحماية من العبث باستخدام سطر الأوامر.
- حاول إيقاف عملية Defender لنقطة النهاية (إنهاء).
- حاول حذف ملفات Defender لنقطة النهاية وإعادة تسميتها وتعديلها ونقلها (على غرار ما يفعله المستخدم الضار)، على سبيل المثال:

  - /Applications/Microsoft Defender ATP.app/
  - /Library/LaunchDaemons/com.microsoft.fresno.plist
  - /Library/LaunchDaemons/com.microsoft.fresno.uninstall.plist
  - /Library/LaunchAgents/com.microsoft.wdav.tray.plist
  - /Library/Managed Preferences/com.microsoft.wdav.ext.plist
  - /Library/Managed Preferences/mdatp_managed.json
  - /Library/Managed Preferences/com.microsoft.wdav.atp.plist
  - /Library/Managed Preferences/com.microsoft.wdav.atp.offboarding.plist
  - /usr/local/bin/mdatp

## <a name="turning-off-tamper-protection"></a>إيقاف تشغيل الحماية من العبث بالبيانات

يمكنك إيقاف تشغيل الحماية من العبث باستخدام أي من الأساليب التالية.

### <a name="manual-configuration"></a>التكوين اليدوي

استخدم الأمر التالي:

```console
sudo mdatp config tamper-protection enforcement-level - -value disabled
```

## <a name="jamf"></a>JAMF
`enforcementLevel` قم بتغيير القيمة إلى "معطل" في ملف تعريف التكوين الخاص بك، وادفعها إلى الجهاز:

```console
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
<plist version="1.0">
  <dict>
    <key>tamperProtection</key>
    <dict>
      <key>enforcementLevel</key>
      <string>disabled</string>
    </dict>
  </dict>
</plist>

```

### <a name="intune"></a>Intune
أضف التكوين التالي في ملف تعريف Intune:

```XML
<?xml version="1.0" encoding="utf-8"?>
<!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
<plist version="1">
    <dict>
        <key>PayloadUUID</key>
        <string>C4E6A782-0C8D-44AB-A025-EB893987A295</string>
        <key>PayloadType</key>
        <string>Configuration</string>
        <key>PayloadOrganization</key>
        <string>Microsoft</string>
        <key>PayloadIdentifier</key>
        <string>com.microsoft.wdav</string>
        <key>PayloadDisplayName</key>
        <string>Microsoft Defender for Endpoint settings</string>
        <key>PayloadDescription</key>
        <string>Microsoft Defender for Endpoint configuration settings</string>
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
                <string>99DBC2BC-3B3A-46A2-A413-C8F9BB9A7295</string>
                <key>PayloadType</key>
                <string>com.microsoft.wdav</string>
                <key>PayloadOrganization</key>
                <string>Microsoft</string>
                <key>PayloadIdentifier</key>
                <string>com.microsoft.wdav</string>
                <key>PayloadDisplayName</key>
                <string>Microsoft Defender for Endpoint configuration settings</string>
                <key>PayloadDescription</key>
                <string/>
                <key>PayloadVersion</key>
                <integer>1</integer>
                <key>PayloadEnabled</key>
                <true/>
                <key>tamperProtection</key>
                <dict>
                             <key>enforcementLevel</key>
                             <string>disabled</string>
                </dict>
            </dict>
        </array>
    </dict>
</plist>
```

## <a name="troubleshooting-configuration-issues"></a>استكشاف مشكلات التكوين وإصلاحها

### <a name="issue-tamper-protection-is-reported-as-disabled"></a>المشكلة: تم الإبلاغ عن الحماية من العبث بالأشخاص على أنها معطلة

إذا كان تشغيل الأمر `mdatp health` يبلغ عن تعطيل الحماية من العبث، حتى إذا قمت بتمكينه وتم تمرير أكثر من ساعة منذ الإلحاق، يمكنك التحقق مما إذا كان لديك التكوين الصحيح عن طريق تشغيل الأمر التالي:

```console
$ sudo grep -F '\[{tamperProtection}\]: Feature state:' /Library/Logs/Microsoft/mdatp/microsoft_defender_core.log | tail -n 1


```

يجب أن يكون الوضع "حظر" (أو "تدقيق"). إذا لم يكن كذلك، فأنت لم تقم بتعيين وضع الحماية من العبث إما من خلال `mdatp config` الأمر أو من خلال Intune.
