---
title: ابدأ باستخدام الماسح الضوئي المحلي لمنع فقدان البيانات
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
description: إعداد الماسح الضوئي المحلي لمنع فقدان البيانات
ms.openlocfilehash: a1bcebfb48a502a9d7c484d266d91fe105603f84
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/06/2022
ms.locfileid: "66625424"
---
# <a name="get-started-with-the-data-loss-prevention-on-premises-scanner"></a>بدء استخدام الماسح الضوئي المحلي لمنع فقدان البيانات

ترشدك هذه المقالة عبر المتطلبات الأساسية والتكوين لمنع فقدان بيانات Microsoft Purview محليا.

## <a name="before-you-begin"></a>قبل البدء

### <a name="skusubscriptions-licensing"></a>ترخيص SKU/الاشتراكات

قبل البدء باستخدام الماسح الضوئي المحلي ل DLP، يجب عليك تأكيد [اشتراكك في Microsoft 365](https://www.microsoft.com/microsoft-365/compare-microsoft-365-enterprise-plans?rtc=1) وأي وظائف إضافية. يجب تعيين أحد التراخيص التالية لحساب المسؤول الذي يقوم بإعداد قواعد DLP:

- Microsoft 365 E5
- التوافق في Microsoft 365 E5
- إدارة Microsoft 365 E5 حماية البيانات & 


للحصول على تفاصيل الترخيص الكامل، راجع: [إرشادات ترخيص Microsoft 365 للأمان & التوافق](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance)

> [!IMPORTANT]
> يحتاج جميع المستخدمين الذين يساهمون في الموقع الممسوح ضوئيا إما عن طريق إضافة ملفات أو استهلاك الملفات إلى الحصول على ترخيص، وليس فقط مستخدم الماسح الضوئي.

### <a name="permissions"></a>الأذونات

يمكن عرض البيانات من الماسح الضوئي المحلي DLP في [مستكشف النشاط](data-classification-activity-explorer.md). هناك أربعة أدوار تمنح الإذن لمستكشف النشاط، يجب أن يكون الحساب الذي تستخدمه للوصول إلى البيانات عضوا في أي منها.

- المسؤول العام
- مسؤول التوافق
- مسؤول الأمان
- مسؤول بيانات التوافق

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

### <a name="dlp-on-premises-scanner-prerequisites"></a>متطلبات الماسح الضوئي المحلي ل DLP

- ينفذ الماسح الضوئي ل Azure حماية البيانات (AIP) مطابقة نهج DLP وإنفاذ النهج. يتم تثبيت الماسح الضوئي كجزء من عميل AIP لذا يجب أن يفي التثبيت بجميع المتطلبات الأساسية ل AIP، عميل AIP، والماسح الضوئي الموحد للوصف AIP.
- توزيع عميل AIP والماسح الضوئي. لمزيد من المعلومات[، قم بتثبيت عميل التسمية الموحد ل AIP](/azure/information-protection/rms-client/install-unifiedlabelingclient-app) و[]، راجع [تكوين وتثبيت الماسح الضوئي الموحد للوصف في Azure حماية البيانات](/azure/information-protection/deploy-aip-scanner-configure-install).
- يجب نشر تسمية ونهج واحد على الأقل في المستأجر، حتى لو كانت جميع قواعد الكشف الخاصة بك تستند إلى أنواع المعلومات الحساسة فقط.

## <a name="deploy-the-dlp-on-premises-scanner"></a>توزيع الماسح الضوئي المحلي ل DLP

1. اتبع الإجراءات في [تثبيت عميل التسمية الموحد ل AIP](/azure/information-protection/rms-client/install-unifiedlabelingclient-app). 
2. اتبع الإجراءات في [تكوين وتثبيت الماسح الضوئي الموحد للوصف حماية البيانات Azure](/azure/information-protection/deploy-aip-scanner-configure-install) لإكمال تثبيت الماسح الضوئي.
    1. يعد تكوين مهام اكتشاف الشبكة خطوة اختيارية. يمكنك تخطيه وتحديد مستودعات معينة ليتم مسحها ضوئيا في مهمة فحص المحتوى.
    2. يجب إنشاء مهمة فحص المحتوى وتحديد المستودعات التي تستضيف الملفات التي تحتاج إلى تقييمها بواسطة محرك DLP.
    3. قم بتمكين قواعد DLP في مهمة فحص المحتوى التي تم إنشاؤها، وتعيين خيار **فرض** إلى **إيقاف التشغيل**، إلا إذا كنت تريد المتابعة مباشرة إلى مرحلة فرض DLP.
3. تحقق من تعيين مهمة فحص المحتوى إلى المجموعة الصحيحة. إذا لم تقم مع ذلك بإنشاء مهمة فحص محتوى، فتنشئ مهمة جديدة وتعينها إلى المجموعة التي تحتوي على عقد الماسح الضوئي.

4. اتصل [بملحق Azure حماية البيانات في مدخل Microsoft Azure](https://portal.azure.com/#blade/Microsoft_Azure_InformationProtection/DataClassGroupEditBlade/scannerProfilesBlade) وأضف مستودعاتك إلى مهمة فحص المحتوى التي ستقوم بإجراء الفحص.

5. قم بأحد الإجراءات التالية لتشغيل الفحص:
    1. تعيين جدول الماسح الضوئي
    1. استخدام الخيار " **المسح الضوئي الآن** " اليدوي في المدخل
    1. أو تشغيل **Start-AIPScan** PowerShell cmdlet

   > [!IMPORTANT]
   > تذكر أن الماسح الضوئي يقوم بتشغيل فحص دلتا للمستودع بشكل افتراضي وسيتم تخطي الملفات التي تم مسحها ضوئيا بالفعل في دورة الفحص السابقة إلا إذا تم تغيير الملف أو قمت ببدء إعادة فحص كامل. يمكن بدء إعادة التعيين الكامل باستخدام خيار **إعادة تعيين كافة الملفات** في واجهة المستخدم أو عن طريق تشغيل **Start-AIPScan-Reset**.

6.  افتح [صفحة منع فقدان البيانات](https://compliance.microsoft.com/datalossprevention?viewid=policies) في مدخل التوافق في Microsoft Purview.

7. اختر **إنشاء نهج** وإنشاء نهج اختبار DLP. راجع [إنشاء نهج DLP من قالب](create-a-dlp-policy-from-a-template.md) إذا كنت بحاجة إلى مساعدة في إنشاء نهج. تأكد من تشغيله في الاختبار حتى تشعر بالراحة مع هذه الميزة. استخدم هذه المعلمات لنهجك:
    1. تحديد نطاق قاعدة الماسح الضوئي المحلي DLP إلى مواقع محددة إذا لزم الأمر. إذا قمت بتحديد **نطاق المواقع** إلى **الكل**، فستخضع جميع الملفات التي تم مسحها ضوئيا بواسطة الماسح الضوئي لمطابقة قاعدة DLP وإنفاذها.
    1. عند تحديد المواقع، يمكنك استخدام قائمة الاستبعاد أو التضمين. يمكنك إما تعريف أن القاعدة ذات صلة فقط بالمسارات التي تطابق أحد الأنماط المدرجة في قائمة التضمين أو كافة الملفات، باستثناء الملفات المطابقة للنمط المدرج في قائمة التضمين. لا توجد مسارات محلية معتمدة. فيما يلي بعض الأمثلة على المسارات الصحيحة:
      - \\\server\share
      - \\\server\share\folder1\subfolderabc
      - \*\\المجلد1
      - \*.docx السرية\*
      - \*سر\*.\*
      - https:// sp2010.local/sites/HR
      - \*https:///الموارد البشرية 
    3. فيما يلي بعض الأمثلة على استخدام القيم غير المقبولة:
      - \*
      - \*\\a
      - Aaa
      - c:\
      - C:\test

> [!IMPORTANT]
> لقائمة الاستبعاد الأسبقية على قائمة التضمينات.

### <a name="viewing-dlp-on-premises-scanner-alerts-in-dlp-alerts-management-dashboard"></a>عرض تنبيهات الماسح الضوئي المحلي ل DLP في لوحة معلومات إدارة تنبيهات DLP

1. افتح [صفحة منع فقدان البيانات](https://compliance.microsoft.com/datalossprevention?viewid=policies) في مدخل التوافق في Microsoft Purview وحدد **Alerts**.

2. راجع الإجراءات في [كيفية تكوين وعرض التنبيهات لنهج DLP](dlp-configure-view-alerts-policies.md) لعرض التنبيهات لنهج DLP لنقطة النهاية.

### <a name="viewing-dlp-on-premises-scanner-in-activity-explorer-and-audit-log"></a>عرض الماسح الضوئي المحلي ل DLP في مستكشف النشاط وسجل التدقيق

> [!NOTE]
> يتطلب الماسح الضوئي المحلي تمكين التدقيق. في تدقيق Microsoft 365 يتم تمكينه بشكل افتراضي.

1. افتح [صفحة تصنيف البيانات](https://compliance.microsoft.com/dataclassification?viewid=overview) لمجالك في مدخل التوافق في Microsoft Purview وحدد مستكشف النشاط.

2. راجع الإجراءات الواردة في ["بدء استخدام مستكشف النشاط"](data-classification-activity-explorer.md) للوصول إلى جميع البيانات الخاصة بمواقع الماسح الضوئي المحلية وتصفيتها.

3. افتح [سجل التدقيق في مركز التوافق](https://security.microsoft.com/auditlogsearch). تتوفر تطابقات قاعدة DLP في واجهة مستخدم سجل التدقيق أو يمكن الوصول إليها بواسطة [Search-UnifiedAuditLog](/powershell/module/exchange/search-unifiedauditlog) PowerShell 


## <a name="next-steps"></a>الخطوات التالية
الآن بعد أن قمت بنشر نهج اختبار للمواقع المحلية DLP ويمكنك عرض بيانات النشاط في مستكشف النشاط، فأنت مستعد للانتقال إلى الخطوة التالية حيث يمكنك إنشاء نهج DLP التي تحمي العناصر الحساسة الخاصة بك.

- [استخدام DLP المحلي](dlp-on-premises-scanner-use.md)

## <a name="see-also"></a>راجع أيضًا

- [التعرف على الماسح الضوئي المحلي ل DLP](dlp-on-premises-scanner-learn.md)
- [استخدام الماسح الضوئي المحلي ل DLP](dlp-on-premises-scanner-use.md)
- [التعرّف على تفادي فقدان البيانات](dlp-learn-about-dlp.md)
- [إنشاء نهج DLP واختباره وضبطه](create-test-tune-dlp-policy.md)
- [بدء استخدام مستكشف النشاط](data-classification-activity-explorer.md)
- [اشتراك Microsoft 365](https://www.microsoft.com/microsoft-365/compare-microsoft-365-enterprise-plans?rtc=1)
