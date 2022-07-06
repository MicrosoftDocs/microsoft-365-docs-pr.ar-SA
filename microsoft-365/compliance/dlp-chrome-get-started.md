---
title: بدء استخدام ملحق Microsoft Purview
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
description: التحضير ل Microsoft Purview Extension ونشره.
ms.openlocfilehash: 9593b75ea9bb858e9cd770ec4f40f4e6d7667a2e
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/06/2022
ms.locfileid: "66622932"
---
# <a name="get-started-with-microsoft-purview-extension"></a>بدء استخدام ملحق Microsoft Purview

استخدم هذه الإجراءات لطرح ملحق Microsoft Purview.

## <a name="before-you-begin"></a>قبل البدء

لاستخدام ملحق Microsoft Purview، يجب إلحاق الجهاز ب DLP لنقطة النهاية. راجع هذه المقالات إذا كنت جديدا على DLP أو DLP لنقطة النهاية

- [تعرف على ملحق Microsoft Purview](dlp-chrome-learn-about.md)
- [تعرف على تفادي فقدان البيانات في Microsoft Purview](dlp-learn-about-dlp.md)
- [إنشاء نهج DLP واختباره وضبطه](create-test-tune-dlp-policy.md)
- [إنشاء نهج DLP من قالب](create-a-dlp-policy-from-a-template.md)
- [التعرف على منع فقدان بيانات نقطة النهاية](endpoint-dlp-learn-about.md)
- [للحصول على متطلبات إضافية لنشر Endpoint DLP، راجع البدء في تفادي فقدان البيانات على الأجهزة.](endpoint-dlp-getting-started.md)
- [أدوات وأساليب الإلحاق للأجهزة Windows 10](device-onboarding-overview.md)
- [تكوين إعدادات اتصال الإنترنت ووكيل الجهاز حماية البيانات](device-onboarding-configure-proxy.md#configure-device-proxy-and-internet-connection-settings-for-information-protection)
- [استخدام تفادي فقدان البيانات في نقطة النهاية](endpoint-dlp-using.md)

### <a name="skusubscriptions-licensing"></a>ترخيص SKU/الاشتراكات

قبل البدء، يجب عليك تأكيد [اشتراكك في Microsoft 365](https://www.microsoft.com/microsoft-365/compare-microsoft-365-enterprise-plans?rtc=1) وأي وظائف إضافية. للوصول إلى وظيفة DLP لنقطة النهاية واستخدامها، يجب أن يكون لديك أحد هذه الاشتراكات أو الوظائف الإضافية.

- Microsoft 365 E5
- Microsoft 365 A5 (EDU)
- التوافق Microsoft 365 E5
- التوافق Microsoft 365 A5
- Microsoft 365 E5 حماية المعلومات والحوكمة
- حماية المعلومات والحوكمة Microsoft 365 A5

للحصول على إرشادات ترخيص مفصلة، راجع [إرشادات ترخيص Microsoft 365 للامتثال & الأمان](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#information-protection).

- يجب أن تكون مؤسستك مرخصة ل DLP لنقطة النهاية
- يجب أن تكون أجهزتك قيد التشغيل Windows 10 x64 الإصدار 1809 أو الإصدارات الأحدث.
- يجب أن يكون لدى الجهاز إصدار عميل مكافحة البرامج الضارة هو 4.18.2202.x أو أحدث. تحقق من الإصدار الحالي من خلال فتح تطبيق **أمن Windows**، وحدد أيقونة **"الإعدادات"**، ثم حدد **"حول**".


### <a name="permissions"></a>الأذونات

يمكن عرض البيانات من DLP نقطة النهاية في [مستكشف النشاط](data-classification-activity-explorer.md). هناك سبعة أدوار تمنح الإذن لمستكشف النشاط، يجب أن يكون الحساب الذي تستخدمه للوصول إلى البيانات عضوا في أي منها.

- مسؤول عمومي
- مسؤول التوافق
- مسؤول الأمان
- مسؤول بيانات التوافق
- القارئ العمومي
- قارئ الأمان
- قارئ التقارير

#### <a name="roles-and-role-groups-in-preview"></a>الأدوار ومجموعات الأدوار في المعاينة

هناك أدوار ومجموعات أدوار في المعاينة يمكنك اختبارها لضبط عناصر التحكم في الوصول.

فيما يلي قائمة بالأدوار القابلة للتطبيق الموجودة في المعاينة. لمعرفة المزيد عنها، راجع ["الأدوار" في مركز توافق & الأمان](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center)

- حماية البيانات مسؤول
- محلل حماية البيانات
- حماية البيانات المحقق
- قارئ حماية البيانات

فيما يلي قائمة بمجموعات الأدوار القابلة للتطبيق الموجودة في المعاينة. لمعرفة المزيد حول ذلك، راجع [مجموعات الأدوار في مركز توافق & الأمان](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#role-groups-in-the-security--compliance-center)

- حماية البيانات
- مسؤولو حماية البيانات
- حماية البيانات المحللين
- المحققون حماية البيانات
- قارئات حماية البيانات

### <a name="overall-installation-workflow"></a>سير عمل التثبيت الكلي

نشر الملحق هو عملية متعددة المراحل. يمكنك اختيار التثبيت على جهاز واحد في كل مرة، أو استخدام Microsoft إدارة نقاط النهاية أو نهج المجموعة لعمليات النشر على مستوى المؤسسة.

1. [قم بإعداد أجهزتك](#prepare-your-devices).
2. [المضيف الذاتي لجهاز واحد للإعداد الأساسي](#basic-setup-single-machine-selfhost)
3. [النشر باستخدام Microsoft إدارة نقاط النهاية](#deploy-using-microsoft-endpoint-manager)
4. [النشر باستخدام نهج المجموعة](#deploy-using-group-policy)
5. [اختبار الملحق](#test-the-extension)
6. [استخدام لوحة معلومات إدارة التنبيهات لعرض تنبيهات Chrome DLP](#use-the-alerts-management-dashboard-to-viewing-chrome-dlp-alerts)
7. [عرض بيانات Chrome DLP في مستكشف النشاط](#viewing-chrome-dlp-data-in-activity-explorer)

### <a name="prepare-infrastructure"></a>إعداد البنية الأساسية

إذا كنت تقوم بنشر الملحق إلى جميع أجهزة Windows 10 المراقبة، فيجب إزالة Google Chrome من التطبيق غير مسموح به وقوائم المستعرض غير مسموح بها. لمزيد من المعلومات، راجع [المستعرضات غير مسموح بها](dlp-configure-endpoint-settings.md#unallowed-browsers). إذا كنت تقوم بنشره على بعض الأجهزة فقط، يمكنك ترك Chrome على المستعرض غير مسموح به أو قوائم التطبيقات غير مسموح بها. سيتجاوز الملحق قيود كلتا القائمتين لأجهزة الكمبيوتر التي تم تثبيته فيها.

### <a name="prepare-your-devices"></a>إعداد أجهزتك

1. استخدم الإجراءات الواردة في هذه المواضيع لإلحاق أجهزتك:
    1. [للحصول على متطلبات إضافية لنشر Endpoint DLP، راجع البدء في تفادي فقدان البيانات على الأجهزة.](endpoint-dlp-getting-started.md)
    1. [إلحاق الأجهزة Windows 10 وأجهزة Windows 11](device-onboarding-overview.md)
    1. [تكوين إعدادات اتصال الإنترنت ووكيل الجهاز حماية البيانات](device-onboarding-configure-proxy.md#configure-device-proxy-and-internet-connection-settings-for-information-protection)

### <a name="basic-setup-single-machine-selfhost"></a>المضيف الذاتي لجهاز واحد للإعداد الأساسي

هذا هو الأسلوب الموصى به.

1. انتقل إلى [ملحق Microsoft Purview - Chrome Web Store (google.com).](https://chrome.google.com/webstore/detail/microsoft-compliance-exte/echcggldkblhodogklpincgchnpgcdco)

2. قم بتثبيت الملحق باستخدام الإرشادات الموجودة على صفحة Chrome Web Store.

### <a name="deploy-using-microsoft-endpoint-manager"></a>النشر باستخدام Microsoft إدارة نقاط النهاية

استخدم أسلوب الإعداد هذا لعمليات النشر على مستوى المؤسسة.

#### <a name="microsoft-endpoint-manager-force-install-steps"></a>Microsoft إدارة نقاط النهاية فرض خطوات التثبيت

قبل إضافة الملحق إلى قائمة الملحقات المثبتة بقوة، من المهم استيعاب Chrome ADMX. تم توثيق خطوات هذه العملية في Microsoft إدارة نقاط النهاية بواسطة Google: [إدارة مستعرض Chrome باستخدام Microsoft Intune - تعليمات Google Chrome Enterprise](https://support.google.com/chrome/a/answer/9102677?hl=en#zippy=%2Cstep-ingest-the-chrome-admx-file-into-intune).

 بعد استيعاب ADMX، يمكن اتباع الخطوات أدناه لإنشاء ملف تعريف تكوين لهذا الملحق.

1. سجل الدخول إلى مركز microsoft إدارة نقاط النهاية مسؤول (https://endpoint.microsoft.com).

2. انتقل إلى ملفات تعريف التكوين.

3. حدد **إنشاء ملف تعريف**.

4. حدد **Windows 10** كمنصة.

5. حدد **"مخصص** " كنوع ملف تعريف.

6. حدد علامة التبويب **"إعدادات** ".

7. حدد **"إضافة**".

8. أدخل معلومات النهج التالية.

    OMA-URI: `./Device/Vendor/MSFT/Policy/Config/Chrome~Policy~googlechrome~Extensions/ExtensionInstallForcelist`<br/>
    نوع البيانات: `String`<br/>
    قيمه: `<enabled/><data id="ExtensionInstallForcelistDesc" value="1&#xF000; echcggldkblhodogklpincgchnpgcdco;https://clients2.google.com/service/update2/crx"/>`

9. انقر فوق "إنشاء".

### <a name="deploy-using-group-policy"></a>النشر باستخدام نهج المجموعة

إذا كنت لا تريد استخدام Microsoft إدارة نقاط النهاية، يمكنك استخدام نهج المجموعة لنشر الملحق عبر مؤسستك.

#### <a name="adding-the-chrome-extension-to-the-forceinstall-list"></a>إضافة ملحق Chrome إلى قائمة ForceInstall

1. في محرر إدارة نهج المجموعة، انتقل إلى الوحدة التنظيمية.

2. قم بتوسيع المسار التالي **لقوالب** >  **نهج تكوين** >  >  الكمبيوتر/المستخدم الإدارية **للقوالب الإدارية الكلاسيكية** > **ل Google** > **Google Chrome** > **Extensions**. قد يختلف هذا المسار استنادا إلى التكوين الخاص بك.

3. حدد **تكوين قائمة الملحقات المثبتة بقوة**.

4. انقر بزر الماوس الأيمن وحدد **"تحرير**".

5. حدد **ممكن**.

6. حدد **"إظهار**".

7. ضمن **Value**، أضف الإدخال التالي: `echcggldkblhodogklpincgchnpgcdco;https://clients2.google.com/service/update2/crx`

8. حدد **"موافق** " ثم **"تطبيق**".

### <a name="test-the-extension"></a>اختبار الملحق

#### <a name="upload-to-cloud-service-or-access-by-unallowed-browsers-cloud-egress"></a>تحميل إلى خدمة السحابة، أو الوصول بواسطة المستعرضات غير مسموح بها Cloud Egress

1. قم بإنشاء عنصر حساس أو الحصول عليه، وحاول تحميل ملف إلى أحد مجالات الخدمة المقيدة في مؤسستك. يجب أن تتطابق البيانات الحساسة مع أحد [أنواع المعلومات الحساسة المضمنة](sensitive-information-type-entity-definitions.md)، أو أحد أنواع المعلومات الحساسة لمؤسستك. يجب أن تحصل على إعلام منبثق DLP على الجهاز الذي تختبر منه هذا الإجراء الذي يظهر أن هذا الإجراء غير مسموح به عند فتح الملف.

#### <a name="testing-other-dlp-scenarios-in-chrome"></a>اختبار سيناريوهات DLP الأخرى في Chrome

الآن بعد أن قمت بإزالة Chrome من قائمة المستعرضات/التطبيقات غير مسموح بها، يمكنك اختبار السيناريوهات أدناه لتأكيد أن السلوك يلبي متطلبات مؤسستك:

- نسخ البيانات من عنصر حساس إلى مستند آخر باستخدام الحافظة
  - للاختبار، افتح ملفا محميا ضد النسخ إلى إجراءات الحافظة في مستعرض Chrome وحاول نسخ البيانات من الملف.
  - النتيجة المتوقعة: إعلام منبثق DLP يظهر أن هذا الإجراء غير مسموح به عند فتح الملف.
- طباعة مستند
  - للاختبار، افتح ملفا محميا ضد إجراءات الطباعة في مستعرض Chrome وحاول طباعة الملف.
  - النتيجة المتوقعة: إعلام منبثق DLP يظهر أن هذا الإجراء غير مسموح به عند فتح الملف.
- نسخ إلى وسائط USB القابلة للإزالة
  - للاختبار، حاول حفظ الملف في مساحة تخزين وسائط قابلة للإزالة.
  - النتيجة المتوقعة: إعلام منبثق DLP يظهر أن هذا الإجراء غير مسموح به عند فتح الملف.
- نسخ إلى مشاركة الشبكة
  - للاختبار، حاول حفظ الملف إلى مشاركة شبكة.
  - النتيجة المتوقعة: إعلام منبثق DLP يظهر أن هذا الإجراء غير مسموح به عند فتح الملف.

### <a name="use-the-alerts-management-dashboard-to-viewing-chrome-dlp-alerts"></a>استخدام لوحة معلومات إدارة التنبيهات لعرض تنبيهات Chrome DLP

1. افتح صفحة **منع فقدان البيانات** في <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">مدخل التوافق في Microsoft Purview</a> وحدد **"Alerts**".

2. راجع الإجراءات في [كيفية تكوين وعرض التنبيهات لنهج DLP](dlp-configure-view-alerts-policies.md) لعرض التنبيهات لنهج DLP لنقطة النهاية.

### <a name="viewing-chrome-dlp-data-in-activity-explorer"></a>عرض بيانات Chrome DLP في مستكشف النشاط

1. افتح [صفحة تصنيف البيانات](https://compliance.microsoft.com/dataclassification?viewid=overview) لمجالك في <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">مدخل التوافق في Microsoft Purview</a> واختر **مستكشف النشاط**.

2. راجع الإجراءات في ["بدء استخدام مستكشف النشاط"](data-classification-activity-explorer.md) للوصول إلى جميع البيانات لأجهزة نقطة النهاية وتصفيتها.

   > [!div class="mx-imgBorder"]
   > ![عامل تصفية مستكشف النشاط لأجهزة نقطة النهاية.](../media/endpoint-dlp-4-getting-started-activity-explorer.png)

### <a name="known-issues-and-limitations"></a>المشاكل والقيود المعروفة

1. وضع التصفح المتخفي غير معتمد ويجب تعطيله.

## <a name="next-steps"></a>الخطوات التالية

الآن بعد أن قمت بإلحاق الأجهزة ويمكنك عرض بيانات النشاط في مستكشف النشاط، فأنت مستعد للانتقال إلى الخطوة التالية حيث يمكنك إنشاء نهج DLP التي تحمي العناصر الحساسة.

- [استخدام تفادي فقدان البيانات في نقطة النهاية](endpoint-dlp-using.md)

## <a name="see-also"></a>راجع أيضًا

- [التعرّف على تفادي فقدان بيانات نقطة النهاية](endpoint-dlp-learn-about.md)
- [استخدام تفادي فقدان البيانات في نقطة النهاية](endpoint-dlp-using.md)
- [التعرّف على تفادي فقدان البيانات](dlp-learn-about-dlp.md)
- [إنشاء نهج DLP واختباره وضبطه](create-test-tune-dlp-policy.md)
- [بدء استخدام مستكشف النشاط](data-classification-activity-explorer.md)
- [مشكلات الأداء في Microsoft Defender لنقطة النهاية](/windows/security/threat-protection/)
- [أدوات وأساليب الإلحاق للأجهزة Windows 10](/windows/security/threat-protection/microsoft-defender-atp/configure-endpoints)
- [اشتراك Microsoft 365](https://www.microsoft.com/microsoft-365/compare-microsoft-365-enterprise-plans?rtc=1)
- [Azure AD الأجهزة المتصلة](/azure/active-directory/devices/concept-azure-ad-join)
- [تنزيل Microsoft Edge الجديد استنادا إلى Chromium](https://support.microsoft.com/help/4501095/download-the-new-microsoft-edge-based-on-chromium)
