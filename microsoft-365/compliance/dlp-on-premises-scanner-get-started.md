---
title: بدء استخدام الماسح الضوئي Microsoft 365 فقدان البيانات
f1.keywords:
- CSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: ''
audience: ITPro
ms.topic: how-to
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
description: إعداد ماسح Microsoft 365 فقدان البيانات
ms.openlocfilehash: 1586489389931b3df19a1c84f0ae49ac7ff9c099
ms.sourcegitcommit: d37fce3b708ea5232b4102fd0e693f4bf17a8948
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 01/21/2022
ms.locfileid: "63575692"
---
# <a name="get-started-with-the-data-loss-prevention-on-premises-scanner"></a>بدء استخدام الماسح الضوئي لمنع فقدان البيانات

تتمشى هذه المقالة مع المتطلبات الأساسية وتكوين الماسح الضوئي Microsoft 365 فقدان البيانات.

## <a name="before-you-begin"></a>قبل البدء

### <a name="skusubscriptions-licensing"></a>ترخيص SKU/الاشتراكات

قبل بدء استخدام الماسح الضوئي ل DLP في الموقع، يجب عليك تأكيد اشتراكك [](https://www.microsoft.com/microsoft-365/compare-microsoft-365-enterprise-plans?rtc=1) في Microsoft 365 وأي من الوظائف الإضافية. يجب تعيين أحد التراخيص التالية لحساب المسؤول الذي يعين قواعد DLP:

- Microsoft 365 E5
- التوافق في Microsoft 365 E5
- Microsoft 365 E5 إدارة & المعلومات 


للحصول على تفاصيل الترخيص الكاملة، راجع: Microsoft 365 [إرشادات الترخيص لتوافق & الأمان](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance)

> [!IMPORTANT]
> يحتاج جميع المستخدمين الذين يساهمون في الموقع الممسوحة ضوئيا إما عن طريق إضافة الملفات أو استهلاك الملفات إلى الحصول على ترخيص، وليس فقط مستخدم الماسح الضوئي.

### <a name="permissions"></a>الأذونات

يمكن عرض البيانات من الماسح الضوئي ل DLP في الموقع في ["مستكشف النشاط](data-classification-activity-explorer.md)". هناك أربعة أدوار تمنح إذنا لمستكشف النشاط، يجب أن يكون الحساب الذي تستخدمه للوصول إلى البيانات عضوا في أي منها.

- المسؤول العام
- مسؤول التوافق
- مسؤول الأمان
- مسؤول بيانات التوافق

#### <a name="roles-and-role-groups-in-preview"></a>الأدوار ومجموعات الأدوار في المعاينة

هناك أدوار ومجموعات أدوار في المعاينة يمكنك اختبارها لضبط عناصر التحكم بالوصول.

فيما يلي قائمة بأدوار حماية البيانات في Microsoft (MIP) في المعاينة. لمعرفة المزيد حولها، راجع [الأدوار في مركز & الأمان](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center)

- مسؤول حماية المعلومات
- محلل حماية المعلومات
- حماية المعلوماتمحقق
- قارئ حماية المعلومات

فيما يلي قائمة مجموعات دور MIP التي تكون في المعاينة. لمعرفة المزيد حول، راجع [مجموعات الدور في مركز & الأمان](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#role-groups-in-the-security--compliance-center)

- حماية المعلومات
- مسؤولو حماية المعلومات
- محللو حماية المعلومات
- الباحثون عن حماية المعلومات
- قراء حماية المعلومات

### <a name="dlp-on-premises-scanner-prerequisites"></a>متطلبات الماسح الضوئي ل DLP في الموقع

- ينفذ الماسح الضوئي Azure Information Protection (AIP) مطابقة نهج DLP وتطبيق النهج. يتم تثبيت الماسح الضوئي كجزء من عميل AIP، لذا يجب أن يلبي التثبيت كل المتطلبات الأساسية ل AIP، والعميل AIP، وماسح التسمية الموحد ل AIP.
- نشر عميل AIP والماسح الضوئي. لمزيد من المعلومات [قم بتثبيت عميل تسمية AIP](/azure/information-protection/rms-client/install-unifiedlabelingclient-app) الموحد و[]، راجع تكوين ماسح ضوئي موحد لتسمية [Azure Information Protection وتثبيته](/azure/information-protection/deploy-aip-scanner-configure-install).
- يجب نشر تسمية ونهية واحدة على الأقل في المستأجر، حتى لو كانت كل قواعد الكشف تستند إلى أنواع المعلومات الحساسة فقط.

## <a name="deploy-the-dlp-on-premises-scanner"></a>نشر الماسح الضوئي ل DLP

1. اتبع الإجراءات في تثبيت عميل [تسمية AIP الموحد](/azure/information-protection/rms-client/install-unifiedlabelingclient-app). 
2. اتبع الإجراءات الواردة في تكوين ماسح تسميات [Azure Information Protection](/azure/information-protection/deploy-aip-scanner-configure-install) الموحد وتثبيته لإكمال تثبيت الماسح الضوئي.
    1. تكوين مهام اكتشاف الشبكة خطوة اختيارية. يمكنك تخطيه وتحديد مستودعات معينة لفحصها في مهمة فحص المحتوى.
    2. يجب إنشاء مهمة فحص المحتوى وتحديد المستودعات التي تستضيف الملفات التي يجب تقييمها بواسطة مشغل DLP.
    3. قم بتمكين قواعد DLP في مهمة فحص المحتوى التي تم إنشاؤها،  ثم قم بتعيين الخيار فرض إلى إيقاف التشغيل، إلا إذا كنت تريد المتابعة مباشرة إلى مرحلة فرض DLP.
3. تحقق من تعيين مهمة فحص المحتوى إلى المجموعة الصحيحة. إذا لم تنشئ بعد مهمة فحص محتوى، فنشئ مهمة جديدة وتعيينها إلى المجموعة التي تحتوي على عقد الماسح الضوئي.

4. الاتصال إلى [ملحق Azure Information Protection في مدخل Azure](https://portal.azure.com/#blade/Microsoft_Azure_InformationProtection/DataClassGroupEditBlade/scannerProfilesBlade) وأضف مستودعاتك إلى مهمة فحص المحتوى التي ستؤدي عملية الفحص.

5. قم بوا أحد الخطوات التالية لتشغيل الفحص:
    1. تعيين جدول الماسح الضوئي
    1. استخدام الخيار " **المسح الضوئي الآن** " اليدوي في المدخل
    1. أو تشغيل **Start-AIPScan** PowerShell cmdlet

   > [!IMPORTANT]
   > تذكر أن الماسح الضوئي يقوم بتشغيل فحص دلتا للمستودع بشكل افتراضي، وأن الملفات التي تم فحصها مسبقا في دورة الفحص السابقة سيتم تخطيها ما لم يتم تغيير الملف أو قمت بشروع عملية إعادة فحص كاملة. يمكن بدء إعادة الضبط بالكامل باستخدام خيار إعادة التحقق  من كل الملفات في واجهة المستخدم أو عن طريق تشغيل **Start-AIPScan-Reset**.

6.  افتح صفحة [منع فقدان البيانات](https://compliance.microsoft.com/datalossprevention?viewid=policies) في Microsoft 365 التوافق.

7. اختر **إنشاء نهج** وإنشاء نهج DLP اختباري. راجع [إنشاء نهج DLP من قالب](create-a-dlp-policy-from-a-template.md) إذا كنت بحاجة إلى مساعدة في إنشاء نهج. تأكد من تشغيله في الاختبار حتى ترتاح في استخدام هذه الميزة. استخدم هذه المعلمات لن نهجك:
    1. نطاق قاعدة الماسح الضوئي ل DLP في موقع معين إذا لزم الأمر. إذا قمت بمسح **نطاق المواقع** إلى **الكل**، فإن جميع الملفات التي تم مسحها ضوئيا بواسطة الماسح الضوئي ستخضع لقاعدة DLP المطابقة والتنفيذ.
    1. عند تحديد المواقع، يمكنك استخدام قائمة الاستثناء أو التضمين. يمكنك إما تحديد أن القاعدة ذات صلة فقط بالمسارات المطابقة لأحد الأنماط المدرجة في قائمة التضمين أو جميع الملفات، باستثناء الملفات المطابقة للنمط المدرج في قائمة التضمين. لا توجد مسارات محلية معتمدة. فيما يلي بعض الأمثلة على المسارات الصحيحة:
      - \\\server\share
      - \\\server\share\folder1\subfolderabc
      - \*\\folder1
      - \*.docx\*
      - \*سرية\*.\*
      - https:// sp2010.local/sites/HR
      - \*https:///الموارد البشرية 
    3. فيما يلي بعض الأمثلة حول استخدام القيم غير المقبولة:
      - \*
      - \*\\a
      - Aaa
      - c:\
      - C:\test

> [!IMPORTANT]
> تكون لقائمة الاستثناء الأسبقية على قائمة التضمينات.

### <a name="viewing-dlp-on-premises-scanner-alerts-in-dlp-alerts-management-dashboard"></a>عرض تنبيهات الماسح الضوئي ل DLP في لوحة معلومات إدارة تنبيهات DLP

1. افتح صفحة [منع فقدان البيانات](https://compliance.microsoft.com/datalossprevention?viewid=policies) في Microsoft 365 التوافق وحدد **تنبيهات**.

2. راجع الإجراءات في كيفية تكوين التنبيهات وعرضها لنهج [DLP](dlp-configure-view-alerts-policies.md) لعرض التنبيهات لنهج DLP في نقطة النهاية.

### <a name="viewing-dlp-on-premises-scanner-in-activity-explorer-and-audit-log"></a>عرض الماسح الضوئي ل DLP في مستكشف النشاط وسجل التدقيق

> [!NOTE]
> يتطلب الماسح الضوئي الداخلي تمكين التدقيق. في Microsoft 365 يتم تمكين التدقيق بشكل افتراضي.

1. افتح صفحة [تصنيف البيانات](https://compliance.microsoft.com/dataclassification?viewid=overview) لمجالك في Microsoft 365 التوافق وحدد مستكشف النشاط.

2. راجع الإجراءات في بدء استخدام "[](data-classification-activity-explorer.md)مستكشف النشاط" للوصول إلى كل البيانات وتصفيتها لمواقع الماسح الضوئي الداخلي.

3. افتح [سجل التدقيق في مركز التوافق](https://security.microsoft.com/auditlogsearch). تتوفر تطابقات قواعد DLP في واجهة مستخدم سجل التدقيق أو يمكن الوصول إليها بواسطة [Search-UnifiedAuditLog](/powershell/module/exchange/search-unifiedauditlog) PowerShell 


## <a name="next-steps"></a>الخطوات التالية
الآن بعد أن قمت بنشر نهج اختبار لمواقع DLP في الموقع في الموقع ويمكنك عرض بيانات النشاط في "مستكشف النشاط"، أصبحت جاهزا للانتقال إلى الخطوة التالية حيث يمكنك إنشاء نهج DLP التي تحمي العناصر الحساسة.

- [استخدام DLP في الموقع](dlp-on-premises-scanner-use.md)

## <a name="see-also"></a>راجع أيضًا

- [تعرف على ماسح DLP في الموقع](dlp-on-premises-scanner-learn.md)
- [استخدام الماسح الضوئي ل DLP في الموقع](dlp-on-premises-scanner-use.md)
- [التعرف على منع فقدان البيانات](dlp-learn-about-dlp.md)
- [إنشاء نهج DLP واختباره وضبطه](create-test-tune-dlp-policy.md)
- [بدء استخدام "مستكشف النشاط"](data-classification-activity-explorer.md)
- [Microsoft 365 الاشتراك](https://www.microsoft.com/microsoft-365/compare-microsoft-365-enterprise-plans?rtc=1)
