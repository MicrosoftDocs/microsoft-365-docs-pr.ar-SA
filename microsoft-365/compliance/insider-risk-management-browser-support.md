---
title: التعرف على اكتشاف إشارة مستعرض إدارة المخاطر الداخلية وتكوينه
description: تعرف على اكتشاف إشارة مستعرض إدارة المخاطر الداخلية في Microsoft Purview
keywords: Microsoft 365، وMicrosoft Purview، والمخاطر الداخلية، وإدارة المخاطر، والتوافق
ms.localizationpriority: medium
ms.service: O365-seccomp
ms.topic: article
f1.keywords:
- NOCSH
ms.author: robmazz
author: robmazz
manager: laurawi
audience: itpro
ms.collection:
- m365-security-compliance
- m365solution-insiderrisk
- m365initiative-compliance
ms.openlocfilehash: d70c5a568e1b694229f3c2f1ba11fe9a2be807f6
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/06/2022
ms.locfileid: "66634170"
---
# <a name="learn-about-and-configure-insider-risk-management-browser-signal-detection"></a>التعرف على اكتشاف إشارة مستعرض إدارة المخاطر الداخلية وتكوينه

غالبا ما يستخدم المستخدمون مستعرضات الويب للوصول إلى كل من الملفات الحساسة وغير الحساسة داخل المؤسسة. تسمح إدارة المخاطر من Insider لمؤسستك بالكشف عن إشارات النقل غير المصرح به للمستعرض والعمل عليها لجميع الملفات غير القابلة للتنفيذ التي يتم عرضها في مستعرضي [Microsoft Edge](https://www.microsoft.com/edge) [وGoogle Chrome](https://www.google.com/chrome) . باستخدام هذه الإشارات، يمكن للمحللين والباحثين العمل بسرعة عند تنفيذ أي من الأنشطة التالية من قبل مستخدمي النهج داخل النطاق عند استخدام هذه المتصفحات:

- الملفات المنسوخة إلى التخزين السحابي الشخصي
- الملفات المطبوعة على الأجهزة المحلية أو أجهزة الشبكة
- الملفات المنقولة أو المنسوخة إلى مشاركة شبكة
- الملفات المنسوخة إلى أجهزة USB

يتم الكشف عن إشارات لهذه الأحداث في Microsoft Edge باستخدام قدرات المستعرض المضمنة واستخدام الوظيفة الإضافية *ملحق التوافق من Microsoft* . في Google Chrome، يستخدم العملاء *ملحق التوافق من Microsoft* للكشف عن الإشارات.

يلخص الجدول التالي الأنشطة المكتشفة ودعم الملحقات لكل مستعرض:

| **الأنشطة المكتشفة**                        | **Microsoft Edge** | **Google Chrome** |
| ---------------------------------------------- | ------------------ | ----------------- |
| الملفات المنسوخة إلى التخزين السحابي الشخصي         | الاصليه             | ملحق         |
| الملفات المطبوعة على الأجهزة المحلية أو أجهزة الشبكة      | الاصليه             | ملحق         |
| الملفات المنقولة أو المنسوخة إلى مشاركة شبكة | ملحق          | ملحق         |
| الملفات المنسوخة إلى أجهزة USB                    | ملحق          | ملحق         |

## <a name="common-requirements"></a>المتطلبات الشائعة

قبل تثبيت الوظيفة الإضافية Microsoft Edge أو ملحق Google Chrome، يحتاج العملاء إلى التأكد من أن الأجهزة الخاصة بمستخدمي النهج داخل النطاق تفي بالمتطلبات التالية:

- يوصى بأحدث إصدار Windows 10 x64، الحد الأدنى Windows 10 x64 build 1809 لدعم الكشف عن الإشارات. الكشف عن إشارة المستعرض غير معتمد حاليا على الأجهزة غير التي تعمل بنظام Windows.
- [اشتراك Microsoft 365](/microsoft-365/compliance/insider-risk-management-configure#subscriptions-and-licensing) الحالي مع دعم إدارة المخاطر الداخلية.
- [يجب إلحاق](/microsoft-365/compliance/insider-risk-management-settings#enable-device-indicators-and-onboard-devices) الأجهزة مدخل التوافق في Microsoft Purview.

للحصول على متطلبات تكوين مستعرض معينة، راجع قسمي Microsoft Edge وGoogle Chrome لاحقا في هذه المقالة.

## <a name="configure-browser-signal-detection-for-microsoft-edge"></a>تكوين الكشف عن إشارة المستعرض ل Microsoft Edge

### <a name="microsoft-edge-browser-requirements"></a>متطلبات مستعرض Microsoft Edge

- تلبية المتطلبات الشائعة
- Microsoft Edge x64، الإصدار 91.0.864.41 أو الإصدارات الأحدث
- *Microsoft Compliance Extension* add-on version 1.0.0.44 or higher
- لم يتم تكوين Edge.exe كمستعرض غير مسموح به

### <a name="option-1-basic-setup-recommended-for-testing-with-edge"></a>الخيار 1: الإعداد الأساسي (مستحسن للاختبار باستخدام Edge)

استخدم هذا الخيار لتكوين المضيف الذاتي لجهاز واحد لكل جهاز في مؤسستك عند اختبار الكشف عن إشارة المستعرض.

بالنسبة إلى خيار الإعداد الأساسي، أكمل الخطوات التالية:

1. انتقل إلى [ملحق التوافق من Microsoft](https://microsoftedge.microsoft.com/addons/detail/microsoft-compliance-exte/lcmcgbabdcbngcbcfabdncmoppkajglo).
2. تثبيت الملحق.

### <a name="option-2-intune-setup-for-edge"></a>الخيار 2: إعداد Intune ل Edge

استخدم هذا الخيار لتكوين الملحق والمتطلبات لمؤسستك باستخدام Intune.

بالنسبة إلى خيار إعداد Intune، أكمل الخطوات التالية:

1. تسجيل الدخول إلى [مركز إدارة نقاط النهاية مسؤول Microsoft](https://endpoint.microsoft.com) باستخدام أذونات المسؤول.
2. انتقل إلى **ملفات تعريف التكوين**.
3. حدد **إنشاء ملف تعريف**.
4. اختر **Windows 10** كمنصة.
5. اختر **"القوالب الإدارية** " *كنوع ملف تعريف* وحدد **"إنشاء".**
6. حدد علامة التبويب **"إعدادات** ".
7. حدد **Edge Version 77 والإصدارات الأحدث.**
8. ابحث عن **الملحقات** التي تمنحك نظرة عامة على جميع الإعدادات المتعلقة بالملحق.
9. حدد **الإعداد Control للملحقات المثبتة بصمت.**
10. حدد **ممكن.**
11. أضف معرف الملحق عند مطالبتك: *lcmcgbabdcbngcbcfabdncmoppkajglo***.**
12. حدد **"موافق".**

### <a name="option-3-group-policy-setup-for-edge"></a>الخيار 3: إعداد نهج المجموعة ل Edge

استخدم هذا الخيار لتكوين الملحق والمتطلبات على مستوى المؤسسة باستخدام نهج المجموعة.

للحصول على خيار إعداد نهج المجموعة، أكمل الخطوات التالية:

**الخطوة 1: استيراد أحدث ملف Microsoft Edge Administrative Template (.admx).**

يجب أن تكون الأجهزة قابلة للإدارة باستخدام نهج المجموعة ويجب استيراد جميع [قوالب Microsoft Edge الإدارية](https://www.microsoft.com/edge/business/download) إلى نهج المجموعة Central Store. لمزيد من المعلومات، راجع [كيفية إنشاء المخزن المركزي وإدارته للقوالب الإدارية نهج المجموعة في Windows](/troubleshoot/windows-client/group-policy/create-and-manage-central-store).

**الخطوة 2: إضافة الوظيفة الإضافية *ملحق التوافق من Microsoft* إلى قائمة *فرض التثبيت* .**

أكمل الخطوات التالية لإضافة الملحق:

1. في **محرر إدارة نهج المجموعة**، انتقل إلى الوحدة التنظيمية (OU).
2. قم بتوسيع المسار التالي  **لقوالب** \> **نهج تكوين** \> \> الكمبيوتر/المستخدم الإدارية **للقوالب الإدارية الكلاسيكية** \> **لملحقات Microsoft Edge** \> **.** قد يختلف هذا المسار استنادا إلى تكوين مؤسستك.
3. حدد **تكوين الملحقات المثبتة بصمت.**
4. انقر بزر الماوس الأيمن وحدد **"تحرير**".
5. تحقق من الزر **التبادلي الممكن** .
6. حدد **"إظهار**".
7. بالنسبة إلى **Value**، أضف الإدخال التالي: *lcmcgbabdcbngcbcfabdncmoppkajglo؛https://edge.microsoft.com/extensionwebstorebase/v1/crx*
8. حدد **"موافق** " وحدد **"Apply**".

## <a name="configure-browser-signal-detection-for-google-chrome"></a>تكوين الكشف عن إشارة المستعرض ل Google Chrome

يتم تمكين دعم الكشف عن إشارات مستعرض إدارة المخاطر من Insider ل Google Chrome من خلال *ملحق التوافق من Microsoft*. يدعم هذا الملحق أيضا DLP نقطة النهاية على Chrome. لمزيد من المعلومات حول دعم DLP لنقطة النهاية، راجع [بدء استخدام ملحق التوافق من Microsoft (معاينة).](/microsoft-365/compliance/dlp-chrome-get-started)

### <a name="google-chrome-browser-requirements"></a>متطلبات متصفح Google Chrome

- تلبية المتطلبات الشائعة
- أحدث إصدار من Google Chrome x64
- *إصدار ملحق التوافق من Microsoft* 2.0.0.183 أو الإصدارات الأحدث
- لم يتم تكوين Chrome.exe كمستعرض غير مسموح به

### <a name="option-1-basic-setup-recommended-for-testing-with-chrome"></a>الخيار 1: الإعداد الأساسي (مستحسن للاختبار باستخدام Chrome)

استخدم هذا الخيار لتكوين المضيف الذاتي لجهاز واحد لكل جهاز في مؤسستك عند اختبار الكشف عن إشارة المستعرض.

بالنسبة إلى خيار الإعداد الأساسي، أكمل الخطوات التالية:

**الخطوة 1: تمكين مفاتيح التسجيل المطلوبة باستخدام PowerShell**

```PowerShell
Get-Item -path "HKLM:\\SOFTWARE\\Microsoft\\Windows Defender\\Miscellaneous Configuration" | New-ItemProperty -Name DlpDisableBrowserCache -Value 0 -Force
```

>[!Important]
>مفاتيح التسجيل هذه مطلوبة لضمان الوظائف المناسبة للملحق. يجب تمكين مفاتيح التسجيل هذه قبل اختبار أي إشارات.*

**الخطوة 2: تثبيت *ملحق التوافق من Microsoft***

1. انتقل إلى [ملحق التوافق من Microsoft](https://chrome.google.com/webstore/detail/microsoft-compliance-exte/echcggldkblhodogklpincgchnpgcdco).
2. تثبيت الملحق.

### <a name="option-2-intune-setup-for-chrome"></a>الخيار 2: إعداد Intune ل Chrome

استخدم هذا الخيار لتكوين الملحق والمتطلبات لمؤسستك باستخدام Intune.

بالنسبة إلى خيار إعداد Intune، أكمل الخطوات التالية:

**الخطوة 1: تمكين مفتاح التسجيل المطلوب باستخدام Intune**

1. تشغيل البرنامج النصي PowerShell التالي:

```PowerShell
Get-Item -path "HKLM:\\SOFTWARE\\Microsoft\\Windows Defender\\Miscellaneous Configuration" | New-ItemProperty -Name DlpDisableBrowserCache -Value 0 -Force
```

2. تسجيل الدخول إلى [مركز microsoft إدارة نقاط النهاية مسؤول](https://endpoint.microsoft.com).
3. انتقل إلى **البرامج النصية** **للأجهزة** \> وحدد **"إضافة".**
4. استعرض وصولا إلى موقع البرنامج النصي الذي تم إنشاؤه عند المطالبة.
5. حدد الإعدادات التالية:

    - تشغيل هذا البرنامج النصي باستخدام بيانات اعتماد تسجيل الدخول: *نعم*
    - فرض التحقق من توقيع البرنامج النصي: *لا*
    - تشغيل البرنامج النصي في مضيف PowerShell 64 بت: *نعم*

6. حدد مجموعات الأجهزة المناسبة وطبق النهج.

**الخطوة 2: تكوين تثبيت قوة Intune**

قبل إضافة ملحق Microsoft DLP Chrome إلى قائمة الملحقات المثبتة بقوة، يجب تثبيت ملف Chrome Administrative Template (.admx) لإدارة Intune. للحصول على إرشادات مفصلة خطوة بخطوة، راجع [إدارة مستعرض Chrome باستخدام Microsoft Intune](https://support.google.com/chrome/a/answer/9102677?hl=en#zippy=%2Cstep-ingest-the-chrome-admx-file-into-intune). بعد تثبيت ملف القالب الإداري، أكمل الخطوات التالية:

1. تسجيل الدخول إلى [مركز microsoft إدارة نقاط النهاية مسؤول](https://endpoint.microsoft.com).
2. انتقل إلى **ملفات تعريف التكوين**.
3. حدد **إنشاء ملف تعريف**.
4. اختر **Windows 10** *كمنصة*.
5. اختر **"مخصص** " كنوع *ملف التعريف* .
6. حدد علامة التبويب **"إعدادات** ".
7. حدد **"إضافة".**
8. أدخل معلومات النهج التالية:

    - OMA-URI: *./Device/Vendor/MSFT/Policy/Config/Chrome~Policy~googlechrome~Extensions/ExtensionInstallForcelist*
    - نوع البيانات: *سلسلة*
    - قيمه: *\<enabled/\>\<data id="ExtensionInstallForcelistDesc" value="1&\#xF000; echcggldkblhodogklpincgchnpgcdco;https://clients2.google.com/service/update2/crx"/\>*

9. حدد **"إنشاء**".

### <a name="option-3-group-policy-setup-for-chrome"></a>الخيار 3: إعداد نهج المجموعة ل Chrome

استخدم هذا الخيار لتكوين الملحق والمتطلبات على مستوى المؤسسة باستخدام نهج المجموعة.

للحصول على خيار إعداد نهج المجموعة، أكمل الخطوات التالية:

**الخطوة 1: استيراد ملف القالب الإداري في Chrome**

يجب أن تكون أجهزتك قابلة للإدارة باستخدام نهج المجموعة ويجب استيراد جميع [قوالب Chrome الإدارية](https://chromeenterprise.google/browser/download/) إلى نهج المجموعة Central Store. لمزيد من المعلومات، راجع [كيفية إنشاء المخزن المركزي وإدارته للقوالب الإدارية نهج المجموعة في Windows](/troubleshoot/windows-client/group-policy/create-and-manage-central-store).

**الخطوة 2: تمكين مفتاح التسجيل المطلوب باستخدام PowerShell**

1. إنشاء برنامج نصي PowerShell بالمحتويات التالية:

    ```PowerShell
    Get-Item -path "HKLM:\\SOFTWARE\\Microsoft\\Windows Defender\\Miscellaneous Configuration" | New-ItemProperty -Name DlpDisableBrowserCache -Value 0 -Force
    ```

2. افتح **وحدة تحكم إدارة نهج المجموعة** وانتقل إلى الوحدة التنظيمية (OU).
3. انقر بزر الماوس الأيمن وحدد **"إنشاء عنصر نهج المجموعة" في هذا المجال وقم بربطه هنا**. عند المطالبة، قم بتعيين اسم وصفي لهذا الكائن نهج المجموعة (GPO). على سبيل المثال، *DLP Chrome فوري PowerShell Script*.
4. بعد إنشاء عنصر نهج المجموعة، انقر بزر الماوس الأيمن وحدد **"تحرير**". ينقلك هذا التحديد إلى الكائن نهج المجموعة.
5. انتقل إلى إعدادات \> **لوحة التحكم** **في تفضيلات** \> **تكوين** \> الكمبيوتر المهام **المجدولة**.
6. انقر بزر الماوس الأيمن فوق المنطقة الفارغة ضمن **المهام المجدولة** وحدد مهمة **فورية جديدة** \> **(على الأقل Windows 7).**
7. أدخل *اسم* المهمة *ووصفها*.
8. اختر الحساب المقابل لتشغيل المهمة الفورية. على سبيل المثال، *NT Authority*.
9. حدد **«Run with highest privileges»**.
10. تكوين نهج Windows 10.
11. في علامة التبويب **"إجراءات** "، اختر **"بدء برنامج**".
12. أدخل المسار إلى البرنامج/البرنامج النصي الذي تم إنشاؤه في **الخطوة 1**.
13. حدد **Apply**.

**الخطوة 3: إضافة ملحق Chrome إلى قائمة فرض التثبيت**

1. في **نهج المجموعة Management Editor**، انتقل إلى الوحدة التنظيمية (OU).
2. قم بتوسيع المسار التالي  **لقوالب** \> **نهج تكوين** \> \> الكمبيوتر/المستخدم الإدارية **للقوالب الإدارية الكلاسيكية** \> **ل Google** \> **Google Chrome** \> **Extensions**. قد يختلف هذا المسار استنادا إلى تكوين مؤسستك.
3. حدد **تكوين قائمة فرض الملحقات المثبتة**.
4. انقر بزر الماوس الأيمن وحدد **"تحرير**".
5. حدد الزر التبادلي **الممكن** .
6. حدد **"إظهار**".
7. بالنسبة إلى **Value**، أضف الإدخال التالي: *echcggldkblhodogklpincgchnpgcdco؛https://clients2.google.com/service/update2/crx*
8. حدد **"موافق** " وحدد **"Apply**".

## <a name="test-and-verify-insider-risk-management-browser-signal-detections"></a>اختبار والتحقق من اكتشافات إشارات مستعرض إدارة المخاطر الداخلية

1. إنشاء نهج إدارة المخاطر الداخلية مع تمكين مؤشرات الجهاز.
2. لاختبار الكشف عن الإشارات للملفات المنسوخة إلى التخزين السحابي الشخصي، أكمل الخطوات التالية من جهاز Windows معتمد:

    - افتح موقع ويب لمشاركة الملفات (Microsoft OneDrive وGoogle Drive وما إلى ذلك) باستخدام نوع المستعرض الذي قمت بتكوينه للكشف عن الإشارات.
    - مع المستعرض، قم بتحميل ملف غير قابل للتنفيذ إلى موقع الويب.
3. لاختبار الكشف عن الإشارات للملفات المطبوعة على أجهزة محلية أو أجهزة شبكة، والملفات المنقولة أو المنسوخة إلى مشاركة الشبكة، والملفات المنسوخة إلى أجهزة USB، أكمل الخطوات التالية من جهاز Windows معتمد:

    - افتح ملفا غير قابل للتنفيذ مباشرة في المستعرض. يجب فتح الملف مباشرة من خلال مستكشف الملفات أو فتحه في علامة تبويب مستعرض جديدة للعرض بدلا من صفحة ويب.
    - طباعة الملف.
    - احفظ الملف إلى جهاز USB.
    - احفظ الملف في محرك أقراص الشبكة.
  
4. بعد إنشاء نهج إدارة المخاطر الداخلية الأول، ستبدأ في تلقي التنبيهات من مؤشرات النشاط بعد حوالي 24 ساعة. تحقق من [لوحة معلومات التنبيهات](/microsoft-365/compliance/insider-risk-management-activities#alert-dashboard) للحصول على تنبيهات إدارة المخاطر الداخلية للأنشطة المختبرة.
