---
title: التعرف على الكشف عن إشارة إدارة مخاطر insider وتكوينها
description: تعرف على اكتشاف إشارة مستعرض إدارة مخاطر insider في Microsoft 365
keywords: Microsoft 365، إدارة مخاطر insider، وإدارة المخاطر، والتوافق
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
ms.openlocfilehash: c3cb9e432f3ea94f88c63cfad928ba577471b420
ms.sourcegitcommit: 007822d16e332522546e948f5c216327254a4d49
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 02/17/2022
ms.locfileid: "63575623"
---
# <a name="learn-about-and-configure-insider-risk-management-browser-signal-detection"></a>التعرف على الكشف عن إشارة إدارة مخاطر insider وتكوينها

غالبا ما يستخدم المستخدمون مستعرضات الويب للوصول إلى كل من الملفات الحساسة وغير الحساسة داخل المؤسسة. تسمح إدارة مخاطر Insider لمنظمتك بالكشف عن إشارات الملء في المستعرض والعمل عليها لكل الملفات غير القابلة للتنفيذ التي يتم عرضها [في](https://www.microsoft.com/edge) Microsoft Edge و Google [Chrome](https://www.google.com/chrome). باستخدام هذه الإشارات، يمكن للمحللين والمحللين العمل بسرعة عند تنفيذ أي من الأنشطة التالية من قبل مستخدمي النهج داخل النطاق عند استخدام المستعرضات التالية:

- الملفات المنسوخة إلى مساحة التخزين الشخصية على السحابة
- الملفات المطبوعة على أجهزة محلية أو على الشبكة
- الملفات المنقولة أو المنسوخة إلى مشاركة شبكة
- الملفات المنسوخة إلى أجهزة USB

يتم اكتشاف الإشارات الخاصة بهذه الأحداث في Microsoft Edge المستعرض باستخدام إمكانات المستعرض المضمنة واستخدام الوظائف الإضافية ملحق التوافق من *Microsoft*. في Google Chrome، يستخدم العملاء *ملحق التوافق من Microsoft* للكشف عن الإشارات.

يلخص الجدول التالي الأنشطة المكتشفة ودعم الملحقات لكل مستعرض:

| **الأنشطة التي تم الكشف عنها**                        | **Microsoft Edge** | **Google Chrome** |
| ---------------------------------------------- | ------------------ | ----------------- |
| الملفات المنسوخة إلى مساحة التخزين الشخصية على السحابة         | أصلي             | الملحق         |
| الملفات المطبوعة على أجهزة محلية أو على الشبكة      | أصلي             | الملحق         |
| الملفات المنقولة أو المنسوخة إلى مشاركة شبكة | الملحق          | الملحق         |
| الملفات المنسوخة إلى أجهزة USB                    | الملحق          | الملحق         |

## <a name="common-requirements"></a>المتطلبات الشائعة

قبل تثبيت Microsoft Edge الإضافية أو ملحق Google Chrome، يحتاج العملاء إلى التأكد من أن الأجهزة لمستخدمي النهج داخل النطاق تلبي المتطلبات التالية:

- يوصى Windows 10 الإصدار x64، Windows 10 x64 الإصدار 1809 لدعم الكشف عن الإشارات. الكشف عن إشارة المستعرض غير معتمد حاليا على الأجهزة Windows الأخرى.
- اشتراك [Microsoft 365 الحالي](/microsoft-365/compliance/insider-risk-management-configure#subscriptions-and-licensing) مع دعم إدارة مخاطر insider.
- يجب أن تكون [الأجهزة مجهزه](/microsoft-365/compliance/insider-risk-management-settings#enable-device-indicators-and-onboard-devices) في مدخل Microsoft 365 التوافق.

للحصول على متطلبات تكوين مستعرض معينة، راجع Microsoft Edge مقاطع Google Chrome لاحقا في هذه المقالة.

## <a name="configure-browser-signal-detection-for-microsoft-edge"></a>تكوين الكشف عن إشارة المستعرض Microsoft Edge

### <a name="microsoft-edge-browser-requirements"></a>Microsoft Edge المستعرض

- تلبية المتطلبات الشائعة
- Microsoft Edge x64، 91.0.864.41 أو إصدار أحدث
- *ملحق التوافق من Microsoft* الإصدار 1.0.0.44 أو الإصدارات الأحدث
- Edge.exe لم يتم تكوينه كمستعرض غير مسموح به

### <a name="option-1-basic-setup-recommended-for-testing-with-edge"></a>الخيار 1: الإعداد الأساسي (مستحسن للاختبار باستخدام Edge)

استخدم هذا الخيار لتكوين المستعرض الذاتي لجهاز واحد لكل جهاز في مؤسستك عند اختبار الكشف عن إشارة المستعرض.

بالنسبة إلى خيار الإعداد الأساسي، أكمل الخطوات التالية:

1. انتقل إلى [ملحق توافق Microsoft](https://microsoftedge.microsoft.com/addons/detail/microsoft-compliance-exte/lcmcgbabdcbngcbcfabdncmoppkajglo).
2. تثبيت الملحق.

### <a name="option-2-intune-setup-for-edge"></a>الخيار 2: إعداد Intune ل Edge

استخدم هذا الخيار لتكوين الملحق والمتطلبات لمنظمتك باستخدام Intune.

بالنسبة إلى خيار إعداد Intune، أكمل الخطوات التالية:

1. سجل الدخول إلى مركز إدارة إدارة نقاط النهاية من Microsoft [باستخدام](https://endpoint.microsoft.com) أذونات المسؤول.
2. انتقل إلى **ملفات تعريف التكوين**.
3. حدد **إنشاء ملف تعريف**.
4. اختر **Windows 10** ك النظام الأساسي.
5. اختر **قوالب إدارية كنوع** *ملف تعريف* وحدد **إنشاء.**
6. حدد علامة **التبويب الإعدادات**.
7. حدد **إصدار Edge 77 والإصدارات الأحدث.**
8. ابحث عن **الملحقات** التي توفر لك نظرة عامة على كل الإعدادات ذات الصلة بالملحقات.
9. حدد الإعداد **التحكم في الملحقات التي يتم تثبيتها بصمت.**
10. حدد **تمكين.**
11. قم بإضافة ملحق الما بعد مطالبتك: *lcmcgbabdcbngcbcfabdncmoppkajglo***.**
12. حدد **موافق.**

### <a name="option-3-group-policy-setup-for-edge"></a>الخيار 3: إعداد نهج المجموعة ل Edge

استخدم هذا الخيار لتكوين الملحق والمتطلبات على مستوى المؤسسة باستخدام "نهج المجموعة".

بالنسبة إلى خيار إعداد نهج المجموعة، أكمل الخطوات التالية:

**الخطوة 1: استيراد أحدث ملف Microsoft Edge الإداري (admx.).**

يجب أن تكون الأجهزة قابلة للإدارة باستخدام "نهج المجموعة[" ويجب](https://www.microsoft.com/edge/business/download) استيراد Microsoft Edge "القوالب الإدارية" إلى "المتجر المركزي لنهج المجموعة". للحصول على مزيد من المعلومات، [راجع كيفية إنشاء](/troubleshoot/windows-client/group-policy/create-and-manage-central-store) المتجر المركزي للقالب الإدارية لن نهج المجموعة وإدارته في Windows.

**الخطوة 2: إضافة ملحق *التوافق من Microsoft* إلى القائمة *فرض* التثبيت.**

أكمل الخطوات التالية لإضافة الملحق:

1. في محرر **إدارة نهج المجموعة**، انتقل إلى الوحدة التنظيمية (OU).
2. قم بتوسيع المسار التالي **لنهج** تكوين الكمبيوتر/ \> \> المستخدم **قوالب** \>  \> \> إدارية كلاسيكية Microsoft Edge **الملحقات**. قد يختلف هذا المسار استنادا إلى تكوين مؤسستك.
3. حدد **تكوين الملحقات التي تم تثبيتها بصمت.**
4. انقر ب الماوس الأيمن وحدد **تحرير**.
5. تحقق من **الزر الراديوي** التمكيني.
6. حدد **إظهار**.
7. بالنسبة **للقيمة**، أضف الإدخال التالي: *lcmcgbabdcbngcbcfabdncmoppkajglo;https://edge.microsoft.com/extensionwebstorebase/v1/crx*
8. حدد **موافق** وحدد **تطبيق**.

## <a name="configure-browser-signal-detection-for-google-chrome"></a>تكوين الكشف عن إشارة المستعرض ل Google Chrome

يتم تمكين دعم الكشف عن إشارات مستعرض إدارة المخاطر ل Insider ل Google Chrome من خلال *ملحق التوافق من Microsoft*. يدعم هذا الملحق أيضا DLP نقطة النهاية على Chrome. لمزيد من المعلومات حول دعم DLP لنقطة النهاية، راجع [بدء استخدام ملحق التوافق من Microsoft (معاينة).](/microsoft-365/compliance/dlp-chrome-get-started).

### <a name="google-chrome-browser-requirements"></a>متطلبات مستعرض Google Chrome

- تلبية المتطلبات الشائعة
- أحدث إصدار من Google Chrome x64
- *إصدار ملحق التوافق من Microsoft* 2.0.0.183 أو إصدار أحدث
- Chrome.exe لم يتم تكوينه كمستعرض غير مسموح به

### <a name="option-1-basic-setup-recommended-for-testing-with-chrome"></a>الخيار 1: الإعداد الأساسي (مستحسن للاختبار باستخدام Chrome)

استخدم هذا الخيار لتكوين المستعرض الذاتي لجهاز واحد لكل جهاز في مؤسستك عند اختبار الكشف عن إشارة المستعرض.

بالنسبة إلى خيار الإعداد الأساسي، أكمل الخطوات التالية:

**الخطوة 1: تمكين مفاتيح التسجيل المطلوبة باستخدام PowerShell**

```PowerShell
Get-Item -path "HKLM:\\SOFTWARE\\Microsoft\\Windows Defender\\Miscellaneous Configuration" | New-ItemProperty -Name DlpDisableBrowserCache -Value 0 -Force
```

>[!Important]
>مفاتيح التسجيل هذه مطلوبة لضمان الأداء الوظيفي المناسب للملحق. يجب تمكين مفاتيح التسجيل هذه قبل اختبار أي إشارات.*

**الخطوة 2: تثبيت *ملحق التوافق من Microsoft***

1. انتقل إلى [ملحق توافق Microsoft](https://chrome.google.com/webstore/detail/microsoft-compliance-exte/echcggldkblhodogklpincgchnpgcdco).
2. تثبيت الملحق.

### <a name="option-2-intune-setup-for-chrome"></a>الخيار 2: إعداد Intune ل Chrome

استخدم هذا الخيار لتكوين الملحق والمتطلبات لمنظمتك باستخدام Intune.

بالنسبة إلى خيار إعداد Intune، أكمل الخطوات التالية:

**الخطوة 1: تمكين مفتاح السجل المطلوب باستخدام Intune**

1. تشغيل البرنامج النصي PowerShell التالي:

```PowerShell
Get-Item -path "HKLM:\\SOFTWARE\\Microsoft\\Windows Defender\\Miscellaneous Configuration" | New-ItemProperty -Name DlpDisableBrowserCache -Value 0 -Force
```

2. سجل الدخول إلى مركز إدارة إدارة نقاط النهاية من Microsoft[.](https://endpoint.microsoft.com)
3. انتقل إلى **البرامج** \> **النصية للأجهزة** وحدد **إضافة.**
4. استعرض بحثا عن موقع البرنامج النصي الذي تم إنشاؤه عند مطالبتك بذلك.
5. حدد الإعدادات التالية:

    - تشغيل هذا البرنامج النصي باستخدام بيانات الاعتماد التي تم تسجيل دخولها: *نعم*
    - فرض التحقق من توقيع البرنامج النصي: *لا*
    - تشغيل البرنامج النصي في مضيف PowerShell بالبت 64 بت: *نعم*

6. حدد مجموعات الأجهزة المناسبة وطبق النهج.

**الخطوة 2: تكوين تثبيت فرض Intune**

قبل إضافة ملحق Microsoft DLP Chrome إلى قائمة الملحقات المثبتة للقوة، يجب تثبيت ملف قالب Chrome الإداري (admx.) لإدارة Intune. للحصول على إرشادات خطوة بخطوة، راجع [إدارة مستعرض Chrome باستخدام Microsoft Intune](https://support.google.com/chrome/a/answer/9102677?hl=en#zippy=%2Cstep-ingest-the-chrome-admx-file-into-intune). بعد تثبيت ملف القالب الإداري، أكمل الخطوات التالية:

1. سجل الدخول إلى مركز إدارة إدارة نقاط النهاية من Microsoft[.](https://endpoint.microsoft.com)
2. انتقل إلى **ملفات تعريف التكوين**.
3. حدد **إنشاء ملف تعريف**.
4. اختر **Windows 10** ك النظام *الأساسي*.
5. اختر **مخصص** كنوع *ملف* التعريف.
6. حدد علامة **التبويب الإعدادات**.
7. حدد **إضافة.**
8. أدخل معلومات النهج التالية:

    - OMA-URI: *./Device/Vendor/MSFT/Policy/Config/Chrome~Policy~googlechrome~Extensions/ExtensionInstallForcelist*
    - نوع البيانات: *سلسلة*
    - القيمة: *\<enabled/\>\<data id=”ExtensionInstallForcelistDesc” value=”1&\#xF000; echcggldkblhodogklpincgchnpgcdco;https://clients2.google.com/service/update2/crx″/\>*

9. حدد **إنشاء**.

### <a name="option-3-group-policy-setup-for-chrome"></a>الخيار 3: إعداد نهج المجموعة ل Chrome

استخدم هذا الخيار لتكوين الملحق والمتطلبات على مستوى المؤسسة باستخدام "نهج المجموعة".

بالنسبة إلى خيار إعداد نهج المجموعة، أكمل الخطوات التالية:

**الخطوة 1: استيراد ملف القالب الإداري في Chrome**

يجب أن تكون أجهزتك قابلة للإدارة باستخدام "نهج المجموعة" ويجب استيراد كل القوالب الإدارية في [Chrome](https://chromeenterprise.google/browser/download/) إلى المتجر المركزي لنهية المجموعة. للحصول على مزيد من المعلومات، [راجع كيفية إنشاء](/troubleshoot/windows-client/group-policy/create-and-manage-central-store) المتجر المركزي للقالب الإدارية لن نهج المجموعة وإدارته في Windows.

**الخطوة 2: تمكين مفتاح السجل المطلوب باستخدام PowerShell**

1. إنشاء برنامج نصي PowerShell بالمحتويات التالية:

    ```PowerShell
    Get-Item -path "HKLM:\\SOFTWARE\\Microsoft\\Windows Defender\\Miscellaneous Configuration" | New-ItemProperty -Name DlpDisableBrowserCache -Value 0 -Force
    ```

2. افتح وحدة **تحكم إدارة نهج المجموعة** وانتقل إلى الوحدة التنظيمية (OU).
3. انقر بضغطة زر الماوس الأيمن وحدد **إنشاء GPO في هذا المجال واربطه هنا**. عند المطالبة، قم بتعيين اسم وصفي إلى كائن نهج المجموعة هذا (GPO). على سبيل المثال *، DLP Chrome Immediate PowerShell Script*.
4. بعد إنشاء GPO، انقر بيمين وحدد **تحرير**. سيأخذك هذا التحديد إلى كائن نهج المجموعة.
5. انتقل إلى **تفضيلات** \> **تكوين** \> الكمبيوتر **إعدادات لوحة التحكم المهام** \> **المجدولة**.
6. انقر ب الماوس الأيمن فوق المنطقة الفارغة ضمن المهام المجدولة **وحدد**  \> مهمة فورية جديدة (على الأقل **Windows 7).**
7. أدخل اسم المهمة *ووصفها*.
8. اختر الحساب المقابل لتشغيل المهمة الفورية. على سبيل المثال *، مرجع NT*.
9. حدد **تشغيل مع أعلى امتيازات**.
10. تكوين نهج Windows 10.
11. على علامة **التبويب إجراءات** ، اختر **بدء برنامج**.
12. أدخل المسار إلى البرنامج/البرنامج النصي الذي تم إنشاؤه في **الخطوة 1**.
13. حدد **تطبيق**.

**الخطوة 3: إضافة ملحق Chrome إلى القائمة فرض التثبيت**

1. في محرر **إدارة نهج المجموعة**، انتقل إلى الوحدة التنظيمية (OU).
2.  قم بتوسيع المسار التالي **سياسات** تكوين الكمبيوتر/\>  \> المستخدم **قوالب** \> \> إدارية كلاسيكية **في Google** \> **Chrome** \> **Extensions**. قد يختلف هذا المسار استنادا إلى تكوين مؤسستك.
3. حدد **تكوين قائمة فرض الملحقات المثبتة**.
4. انقر ب الماوس الأيمن وحدد **تحرير**.
5. حدد **الزر الراديوي** التمكيني.
6. حدد **إظهار**.
7. بالنسبة **للقيمة**، أضف الإدخال التالي: *echcggldkblhodogklpincgchnpgcdco;https://clients2.google.com/service/update2/crx*
8. حدد **موافق** وحدد **تطبيق**.

## <a name="test-and-verify-insider-risk-management-browser-signal-detections"></a>اختبار الكشف عن إشارات مستعرض إدارة مخاطر insider والتحقق منها

1. إنشاء نهج إدارة مخاطر insider مع تمكين مؤشرات الجهاز.
2. لاختبار الكشف عن الإشارات للملفات المنسوخة إلى التخزين السحابي الشخصي، أكمل الخطوات التالية من جهاز Windows معتمد:

    - افتح موقع ويب لمشاركة الملفات (Microsoft OneDrive Google Drive وما إلى ذلك) باستخدام نوع المستعرض الذي قمت بتكوينه للكشف عن الإشارات.
    - باستخدام المستعرض، قم بتحميل ملف غير قابل للتنفيذ إلى موقع الويب.
3. لاختبار الكشف عن الإشارات للملفات المطبوعة على أجهزة محلية أو على الشبكة والملفات المنقولة أو المنسوخة إلى مشاركة شبكة والملفات المنسوخة إلى أجهزة USB، أكمل الخطوات التالية من جهاز Windows معتمد:

    - افتح ملفا غير قابل للتنفيذ مباشرة في المستعرض. يجب فتح الملف مباشرة من خلال "مستكشف الملفات" أو فتحه في علامة تبويب مستعرض جديدة للعرض بدلا من صفحة ويب.
    - طباعة الملف.
    - احفظ الملف على جهاز USB.
    - احفظ الملف في محرك أقراص الشبكة.
  
4. بعد إنشاء نهج إدارة مخاطر insider الأول، ستبدأ في تلقي تنبيهات من مؤشرات النشاط بعد حوالي 24 ساعة. تحقق من [لوحة معلومات التنبيهات](/microsoft-365/compliance/insider-risk-management-activities#alert-dashboard) لتنبيهات إدارة مخاطر insider الخاصة بالأنشطة التي تم اختبارها.
