---
title: بدء العمل باستخدام ملحق التوافق من Microsoft
f1.keywords:
- CSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: ''
audience: ITPro
ms.topic: conceptual
f1_keywords:
- ms.o365.cc.DLPLandingPage
ms.service: O365-seccomp
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
- m365solution-mip
- m365initiative-compliance
ms.custom: admindeeplinkCOMPLIANCE
search.appverid:
- MET150
description: التحضير لملحق التوافق من Microsoft ونشره.
ms.openlocfilehash: 5ffd04ee0b89c2e920f55c3e6fbefbab4c82983e
ms.sourcegitcommit: db2ed146b46ade9ea62eed9cb8efff5fea7a35e6
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/26/2022
ms.locfileid: "64481375"
---
# <a name="get-started-with-microsoft-compliance-extension"></a>بدء العمل باستخدام ملحق التوافق من Microsoft

استخدم هذه الإجراءات ل طرح ملحق التوافق من Microsoft.

## <a name="before-you-begin"></a>قبل البدء

لاستخدام ملحق التوافق من Microsoft، يجب أن يكون الجهاز ملحقا في نقطة النهاية DLP. راجع هذه المقالات إذا كنت جديدا في DLP أو نقطة النهاية DLP

- [التعرف على ملحق التوافق من Microsoft](dlp-chrome-learn-about.md)
- [التعرف على منع فقدان البيانات](dlp-learn-about-dlp.md)
- [إنشاء نهج DLP واختباره وضبطه](create-test-tune-dlp-policy.md)
- [إنشاء نهج DLP من قالب](create-a-dlp-policy-from-a-template.md)
- [التعرف على منع فقدان البيانات في نقطة النهاية](endpoint-dlp-learn-about.md)
- [بدء استخدام منع فقدان بيانات نقطة النهاية](endpoint-dlp-getting-started.md)
- [أدوات وأساليب التكهين للأجهزة Windows 10 الأجهزة](device-onboarding-overview.md)
- [تكوين إعدادات اتصال الإنترنت ووكيل الجهاز حماية البيانات](device-onboarding-configure-proxy.md#configure-device-proxy-and-internet-connection-settings-for-information-protection)
- [استخدام منع فقدان البيانات في نقطة النهاية](endpoint-dlp-using.md)

### <a name="skusubscriptions-licensing"></a>ترخيص SKU/الاشتراكات

قبل البدء، يجب عليك [تأكيد اشتراكك](https://www.microsoft.com/microsoft-365/compare-microsoft-365-enterprise-plans?rtc=1) Microsoft 365 الوظائف الإضافية وأي من الوظائف الإضافية. للوصول إلى وظائف DLP لنقطة النهاية واستخدامها، يجب أن يكون لديك أحد هذه الاشتراكات أو الوظائف الإضافية.

- Microsoft 365 E5
- Microsoft 365 A5 (EDU)
- Microsoft 365 E5 التوافق
- Microsoft 365 A5 التوافق
- Microsoft 365 E5 حماية المعلومات والحوكمة
- Microsoft 365 A5 حماية المعلومات والحوكمة

للحصول على إرشادات الترخيص التفصيلية، [راجع Microsoft 365 إرشادات الترخيص لتوافق & الأمان](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#information-protection).

- يجب أن تكون المؤسسة مرخصة ل Endpoint DLP
- يجب أن تعمل أجهزتك Windows 10 x64 1809 أو أي وقت لاحق.
- يجب أن يكون إصدار عميل مكافحة البرامج الضارة للجهاز هو 4.18.2202.x أو إصدار أحدث. تحقق من الإصدار الحالي عن **طريق** أمن Windows التطبيق، **وحدد** الإعدادات، ثم حدد **حول**.


### <a name="permissions"></a>الأذونات

يمكن عرض البيانات من نقطة النهاية DLP في ["مستكشف النشاط](data-classification-activity-explorer.md)". هناك سبعة أدوار تمنح إذنا لمستكشف النشاط، يجب أن يكون الحساب الذي تستخدمه للوصول إلى البيانات عضوا في أي منها.

- المسؤول العام
- مسؤول التوافق
- مسؤول الأمان
- مسؤول بيانات التوافق
- القارئ العام
- قارئ الأمان
- قارئ التقارير

#### <a name="roles-and-role-groups-in-preview"></a>الأدوار ومجموعات الأدوار في المعاينة

هناك أدوار ومجموعات أدوار في المعاينة يمكنك اختبارها لضبط عناصر التحكم بالوصول.

فيما يلي قائمة بأدوار حماية البيانات في Microsoft (MIP) في المعاينة. لمعرفة المزيد حولها، راجع [الأدوار في مركز & الأمان](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center)

- حماية البيانات المسؤول
- حماية البيانات محلل
- حماية البيانات العمل
- حماية البيانات قارئ الشاشة

فيما يلي قائمة مجموعات دور MIP التي تكون في المعاينة. لمعرفة المزيد حول، راجع [مجموعات الدور في مركز & الأمان](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#role-groups-in-the-security--compliance-center)

- حماية البيانات
- حماية البيانات المسؤولين
- حماية البيانات المحللون
- حماية البيانات نواة
- حماية البيانات القراء

### <a name="overall-installation-workflow"></a>سير عمل التثبيت الكلي

إن نشر ملحق التوافق من Microsoft عملية متعددة المراحل. يمكنك اختيار التثبيت على جهاز واحد في كل مرة، أو استخدام إدارة نقاط النهاية من Microsoft أو نهج المجموعة عمليات النشر على مستوى المؤسسة.

1. [تحضير أجهزتك](#prepare-your-devices).
2. [الإعداد الأساسي المفرد للجهاز](#basic-setup-single-machine-selfhost)
3. [النشر باستخدام إدارة نقاط النهاية من Microsoft](#deploy-using-microsoft-endpoint-manager)
4. [النشر باستخدام نهج المجموعة](#deploy-using-group-policy)
5. [اختبار الملحق](#test-the-extension)
6. [استخدام لوحة معلومات إدارة التنبيهات لعرض تنبيهات Chrome DLP](#use-the-alerts-management-dashboard-to-viewing-chrome-dlp-alerts)
7. [عرض بيانات DLP في Chrome في مستكشف النشاط](#viewing-chrome-dlp-data-in-activity-explorer)

### <a name="prepare-infrastructure"></a>إعداد البنية الأساسية

إذا كنت تقوم بإزالة ملحق التوافق من Microsoft إلى جميع الأجهزة التي Windows 10 مراقبتها، يجب إزالة Google Chrome من التطبيق غير المكفوف وقوائم المستعرض غير المدينة. لمزيد من المعلومات، راجع [المستعرضات غير مسموح بها](dlp-configure-endpoint-settings.md#unallowed-browsers). إذا كنت تقوم فقط بتركه في بعض الأجهزة، يمكنك ترك Chrome على المستعرض غير مسموح به أو قوائم التطبيقات غير مسموح بها. سيتجاوز ملحق التوافق ل Microsoft قيود القائمتين لأجهزة الكمبيوتر التي تم تثبيته عليها.

### <a name="prepare-your-devices"></a>تحضير أجهزتك

1. استخدم الإجراءات في هذه المواضيع لتكهين أجهزتك:
    1. [بدء استخدام منع فقدان بيانات نقطة النهاية](endpoint-dlp-getting-started.md)
    1. [أجهزة Windows 10 Windows 11 الأجهزة](device-onboarding-overview.md)
    1. [تكوين إعدادات اتصال الإنترنت ووكيل الجهاز حماية البيانات](device-onboarding-configure-proxy.md#configure-device-proxy-and-internet-connection-settings-for-information-protection)

### <a name="basic-setup-single-machine-selfhost"></a>الإعداد الأساسي المفرد للجهاز

هذا هو الأسلوب المستحسن.

1. انتقل إلى [ملحق التوافق من Microsoft - سوق Chrome الإلكتروني (google.com)](https://chrome.google.com/webstore/detail/microsoft-compliance-exte/echcggldkblhodogklpincgchnpgcdco).

2. ثبت الملحق باستخدام الإرشادات الموجودة على سوق Chrome الإلكتروني.

### <a name="deploy-using-microsoft-endpoint-manager"></a>النشر باستخدام إدارة نقاط النهاية من Microsoft

استخدم أسلوب الإعداد هذا للنشر على مستوى المؤسسة.

#### <a name="microsoft-endpoint-manager-force-install-steps"></a>إدارة نقاط النهاية من Microsoft فرض خطوات التثبيت

قبل إضافة ملحق التوافق من Microsoft إلى قائمة الملحقات المثبتة بالقوة، من المهم استخدام Chrome ADMX. تم توثيق خطوات هذه العملية إدارة نقاط النهاية من Microsoft Google: [إدارة مستعرض Chrome باستخدام Microsoft Intune - تعليمات Google Chrome Enterprise](https://support.google.com/chrome/a/answer/9102677?hl=en#zippy=%2Cstep-ingest-the-chrome-admx-file-into-intune).

 بعد استخدام ADMX، يمكن اتباع الخطوات أدناه لإنشاء ملف تعريف تكوين لهذا الملحق.

1. سجل الدخول إلى مركز إدارة إدارة نقاط النهاية من Microsoft (https://endpoint.microsoft.com).

2. انتقل إلى ملفات تعريف التكوين.

3. حدد **إنشاء ملف تعريف**.

4. حدد **Windows 10** ك النظام الأساسي.

5. حدد **مخصص** كنوع ملف تعريف.

6. حدد علامة **التبويب الإعدادات**.

7. حدد **إضافة**.

8. أدخل معلومات النهج التالية.

    OMA-URI: `./Device/Vendor/MSFT/Policy/Config/Chrome~Policy~googlechrome~Extensions/ExtensionInstallForcelist`<br/>
    نوع البيانات: `String`<br/>
    القيمة: `<enabled/><data id="ExtensionInstallForcelistDesc" value="1&#xF000; echcggldkblhodogklpincgchnpgcdco;https://clients2.google.com/service/update2/crx"/>`

9. انقر فوق إنشاء.

### <a name="deploy-using-group-policy"></a>النشر باستخدام نهج المجموعة

إذا كنت لا تريد استخدام إدارة نقاط النهاية من Microsoft، يمكنك استخدام سياسات المجموعة لنشر ملحق التوافق من Microsoft عبر مؤسستك.

#### <a name="adding-the-chrome-extension-to-the-forceinstall-list"></a>إضافة ملحق Chrome إلى القائمة "تثبيت القوة"

1. في محرر نهج المجموعة، انتقل إلى OU.

2. توسيع المسار التالي **تكوين الكمبيوتر/** > **المستخدمPoliciesAdministrative** >  **templates** >  >  الإداريةالقالب **الإداريةGoogleGoogle** >  **ChromeExtensions** > . قد يختلف هذا المسار وفقا لتكوينك.

3. حدد **تكوين قائمة الملحقات المثبتة بشكل إجباري**.

4. انقر بيمين وحدد **تحرير**.

5. حدد **تمكين**.

6. حدد **إظهار**.

7. ضمن **قيمة**، أضف الإدخال التالي: `echcggldkblhodogklpincgchnpgcdco;https://clients2.google.com/service/update2/crx`

8. حدد **موافق** ثم **تطبيق**.

### <a name="test-the-extension"></a>اختبار الملحق

#### <a name="upload-to-cloud-service-or-access-by-unallowed-browsers-cloud-egress"></a>Upload إلى خدمة السحابة، أو الوصول بواسطة المستعرضات غير Egress

1. قم بإنشاء عنصر حساس أو الحصول عليه، وحاول تحميل ملف إلى أحد مجالات الخدمة المقيدة في مؤسستك. يجب أن تتطابق البيانات الحساسة مع أحد أنواع المعلومات الحساسة المضمنة، أو أحد أنواع المعلومات الحساسة في مؤسستك.[](sensitive-information-type-entity-definitions.md) يجب أن تحصل على إعلام من المنبثق DLP على الجهاز الذي تقوم باختباره من الذي يظهر أن هذا الإجراء غير مسموح به عند فتح الملف.

#### <a name="testing-other-dlp-scenarios-in-chrome"></a>اختبار سيناريوهات DLP الأخرى في Chrome

الآن وقد قمت بإزالة Chrome من قائمة التطبيقات/المستعرضات غير مسموح بها، يمكنك اختبار السيناريوهات أدناه لتأكيد أن السلوك يلبي متطلبات مؤسستك:

- نسخ البيانات من عنصر حساس إلى مستند آخر باستخدام الحافظة
  - للاختبار، افتح ملفا محميا من إجراءات النسخ إلى الحافظة في مستعرض Chrome، ثم حاول نسخ البيانات من الملف.
  - النتيجة المتوقعة: إعلام من المنبثق ل DLP يظهر عدم السماح بهذا الإجراء عند فتح الملف.
- طباعة مستند
  - للاختبار، افتح ملفا محميا من إجراءات الطباعة في مستعرض Chrome، ثم حاول طباعة الملف.
  - النتيجة المتوقعة: إعلام من المنبثق ل DLP يظهر عدم السماح بهذا الإجراء عند فتح الملف.
- نسخ إلى وسائط USB القابلة للإزالة
  - للاختبار، حاول حفظ الملف في مساحة تخزين وسائط قابلة للإزالة.
  - النتيجة المتوقعة: إعلام من المنبثق ل DLP يظهر عدم السماح بهذا الإجراء عند فتح الملف.
- النسخ إلى مشاركة الشبكة
  - للاختبار، حاول حفظ الملف في مشاركة شبكة.
  - النتيجة المتوقعة: إعلام من المنبثق ل DLP يظهر عدم السماح بهذا الإجراء عند فتح الملف.

### <a name="use-the-alerts-management-dashboard-to-viewing-chrome-dlp-alerts"></a>استخدام لوحة معلومات إدارة التنبيهات لعرض تنبيهات Chrome DLP

1. افتح صفحة **منع فقدان** <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">البيانات في مركز التوافق في Microsoft 365</a> وحدد **تنبيهات**.

2. راجع الإجراءات في كيفية تكوين التنبيهات وعرضها لنهج [DLP](dlp-configure-view-alerts-policies.md) لعرض التنبيهات لنهج DLP في نقطة النهاية.

### <a name="viewing-chrome-dlp-data-in-activity-explorer"></a>عرض بيانات DLP في Chrome في مستكشف النشاط

1. افتح صفحة [تصنيف البيانات](https://compliance.microsoft.com/dataclassification?viewid=overview) لمجالك في <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">مركز التوافق في Microsoft 365 واختر</a> **مستكشف النشاط**.

2. راجع الإجراءات في بدء استخدام "[](data-classification-activity-explorer.md)مستكشف النشاط" للوصول إلى كل البيانات الخاصة بأجهزتك في نقطة النهاية وتصفيتها.

   > [!div class="mx-imgBorder"]
   > ![عامل تصفية مستكشف النشاط للأجهزة التي تعمل بنقطة النهاية.](../media/endpoint-dlp-4-getting-started-activity-explorer.png)

### <a name="known-issues-and-limitations"></a>المشاكل والقيود المعروفة

1. وضع التصفح المتخفي غير معتمد ويجب تعطيله.

## <a name="next-steps"></a>الخطوات التالية

الآن وقد أصبح لديك أجهزة مجهزه للعمل ويمكنك عرض بيانات النشاط في "مستكشف النشاط"، أنت جاهز للانتقال إلى الخطوة التالية حيث تقوم بإنشاء سياسات DLP التي تحمي العناصر الحساسة.

- [استخدام منع فقدان البيانات في نقطة النهاية](endpoint-dlp-using.md)

## <a name="see-also"></a>راجع أيضًا

- [التعرف على منع فقدان بيانات نقطة النهاية](endpoint-dlp-learn-about.md)
- [استخدام منع فقدان البيانات في نقطة النهاية](endpoint-dlp-using.md)
- [التعرف على منع فقدان البيانات](dlp-learn-about-dlp.md)
- [إنشاء نهج DLP واختباره وضبطه](create-test-tune-dlp-policy.md)
- [بدء استخدام "مستكشف النشاط"](data-classification-activity-explorer.md)
- [Microsoft Defender لنقطة النهاية](/windows/security/threat-protection/)
- [أدوات وأساليب ال متنبها Windows 10 الأجهزة](/windows/security/threat-protection/microsoft-defender-atp/configure-endpoints)
- [Microsoft 365 الاشتراك](https://www.microsoft.com/microsoft-365/compare-microsoft-365-enterprise-plans?rtc=1)
- [الأجهزة المنضمة إلى Azure AD](/azure/active-directory/devices/concept-azure-ad-join)
- [قم بتنزيل الملف Microsoft Edge استنادا إلى Chromium](https://support.microsoft.com/help/4501095/download-the-new-microsoft-edge-based-on-chromium)
