---
title: ما الجديد في Microsoft 365 التوافق
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
manager: laurawi
audience: Admin
ms.topic: reference
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- SPO160
- MOE150
- MET150
ms.assetid: e3c6df61-8513-499d-ad8e-8a91770bff63
ms.collection:
- M365-security-compliance
description: سواء كان ذلك بإضافة حلول جديدة إلى مركز التوافق أو تحديث الميزات الموجودة بالاستناد إلى ملاحظاتك أو طرح الوثائق الجديدة والمحدثة، يساعدك Microsoft 365 على البقاء على رأس مشهد التوافق المتغير باستمرار. تعرف على ما قمنا به هذا الشهر.
ms.custom: seo-marvel-mar2020
ms.openlocfilehash: 15a97fc419bc6e4264f3c3cd0bbe389b79e5c2f0
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/08/2022
ms.locfileid: "63566545"
---
# <a name="whats-new-in-microsoft-365-compliance"></a>ما الجديد في Microsoft 365 التوافق

سواء كنت تريد إضافة حلول جديدة إلى مركز التوافق في Microsoft 365، [](microsoft-365-compliance-center.md)أو تحديث الميزات الموجودة بالاستناد إلى ملاحظاتك، أو طرح وثائق جديدة ومحدثة، يساعدك Microsoft 365 على البقاء على رأس مشهد التوافق المتغير باستمرار. أطلع على أحدث ما هو جديد في Microsoft 365 اليوم.

> [!NOTE]
> يتم طرح بعض ميزات التوافق بسرعات مختلفة لعملائنا. إذا لم تكن ترى ميزة بعد، فحاول إضافة نفسك إلى [الإصدار المستهدف](/office365/admin/manage/release-options-in-office-365).

> [!TIP]
> هل أنت مهتم بما يحدث في مراكز الإدارة الأخرى؟ اطلع على المقالات التالية:
>
> - [ما الجديد في مركز مسؤولي Microsoft 365](/office365/admin/whats-new-in-preview)
> - [ما الجديد في مركز إدارة SharePoint](/sharepoint/what-s-new-in-admin-center)
> - [ما الجديد في Microsoft 365 Defender](../security/defender/whats-new.md)
>
> تفضل بزيارة [Microsoft 365 للتعرف](https://www.microsoft.com/microsoft-365/roadmap) على Microsoft 365 الميزات التي تم تشغيلها أو التي يتم طرحها أو في وضع التطوير أو تم إلغاؤها أو إصدارها مسبقا.

## <a name="february-2022"></a>فبراير 2022

### <a name="ediscovery"></a>eDiscovery

- [إدارة قوالب](advanced-ediscovery-communications-library.md) الاتصالات غير المهيأة في Advanced eDiscovery - يمكن لمديري eDiscovery الآن إنشاء قوالب اتصالات إمقارية يمكن استخدامها في أي Advanced eDiscovery أخرى في المؤسسة.
- إدارة [إصدار الموظفين في](advanced-ediscovery-issuing-officers.md) Advanced eDiscovery - يمكن لمديري eDiscovery إضافة قائمة بالوكلاء الذين يمكن تعيينهم إلى الاتصالات الضمية في أي Advanced eDiscovery حالية في المؤسسة.

### <a name="information-governance-and-records-management"></a>إدارة المعلومات وإدارة السجلات

- [تتوفر الآن النطاقات](retention.md#adaptive-or-static-policy-scopes-for-retention) التكييفية لنهج الاستبقاء ونهج تسميات الاستبقاء بشكل عام (GA). تتضمن إرشادات تكوين [](retention-settings.md#to-configure-an-adaptive-scope) نطاق تكييفي الآن المزيد من المعلومات حول نطاقات موقع SharePoint: مرجع منشور المدونة لاستخدام خصائص الموقع المخصصة وكيفية استخدام خاصية الموقع SiteTemplate لتضمين أنواع مواقع معينة أو استبعادها باستخدام منشئ الاستعلام المتقدم.
- [يتوفر الآن البحث عن](retention.md#policy-lookup) النهج في حل "إدارة المعلومات" بشكل عام (GA).
- PowerShell بديل لإعداد إدارة السجلات الذي يسمح للمستخدمين بحذف العناصر الملصقات في SharePoint و OneDrive باستخدام AllowFilesWithKeepLabelToBeDeletedSPO و AllowFilesWithKeepLabelToBeDeletedODB من [Get-PnPTenant](/powershell/module/sharepoint-pnp/get-pnptenant) و [Set-PnPTenant]( /powershell/module/sharepoint-pnp/set-pnptenant).

### <a name="sensitivity-labels"></a>تسميات الحساسية

- إرشادات جديدة لماذا اختر التسميات المضمنة [ل MIP عبر الوظائف الإضافية AIP لتطبيقات Office](sensitivity-labels-aip.md) إذا كنت تستخدم عميل التسمية الموحد لحماية معلومات Azure (AIP) لأجهزة الكمبيوتر Windows الكمبيوتر. تتضمن هذه الصفحة معلومات حول المعاينة الخاصة الجديدة Office التطبيقات.
- إعدادات جديدة لنهج [التسمية التلقائية](apply-sensitivity-label-automatically.md#how-to-configure-auto-labeling-policies-for-sharepoint-onedrive-and-exchange):
  - إعدادات إضافية للبريد الإلكتروني لدعم تطبيق تسمية حساسية متطابقة دائما، وتطبيق التشفير على البريد الإلكتروني الذي يتم تلقيه من خارج المؤسسة.
  - يتم دعم الاستثناءات لمثيلات معينة (المستخدمون والمجموعات والمواقع) باستخدام الخيار "مستبعد" الجديد عندما يكون التحديد الافتراضي لل الكل  محددا ل **"مضمن**".
- الآن في وضع المعاينة: تدعم الأجهزة المحمولة (iOS وAndroid) التأليف المشترك عندما يكون لديك الحد الأدنى من الإصدارات وتختار المشاركة في هذه المعاينة.[](sensitivity-labels-coauthoring.md)
- يتم توسيع الدعم لإعداد نوع ارتباط المشاركة الافتراضي ليشمل المستندات الفردية في SharePoint OneDrive. لمزيد من المعلومات، راجع المقالة الجديدة استخدام تسميات الحساسية لتكوين نوع ارتباط المشاركة الافتراضي للمواقع والمستندات في SharePoint [OneDrive]( sensitivity-labels-default-sharing-link.md).
- Teams إدارة المركز الآن تسميات الحاويات (تسميات الحساسية بنطاق المجموعات & المواقع).

## <a name="january-2022"></a>يناير 2022

### <a name="microsoft-information-governance"></a>إدارة معلومات Microsoft

- تمت مراجعة صفحة "إدارة المعلومات من Microsoft" في [Microsoft 365](manage-information-governance.md) وقسم الوثائق بشكل جذري وإعادة هيكلتها لمساعدتك في العثور على المعلومات المتعلقة بالحلول التي تقوم بتكوينها في مركز التوافق في Microsoft 365 بسهولة أكبر: موصلات البيانات وإدارة المعلومات وإدارة السجلات. وكجزء من هذه المراجعة، توفر الوثائق تمييزا أكثر وضوحا لسيناريوهات الاستبقاء لإدارة المعلومات مقابل إدارة السجلات.
- [تعرف على إدارة المعلومات](information-governance.md) - جديد، لدعم إعادة الهيكلة.
- [بدء استخدام إدارة](get-started-with-information-governance.md) المعلومات - جديد، لاستبدال "بدء استخدام الاستبقاء"، تتضمن هذه المقالة خطوات بدء استخدام كل قدرات إدارة المعلومات، التي تتضمن استبقاء.
- [إنشاء تسميات استبقاء لاستثناءات](create-retention-labels-information-governance.md) لنهج الاستبقاء - سيناريو جديد ومحدد لاستخدام تسميات الاستبقاء لإدارة المعلومات بدلا من إدارة السجلات.
- [تعرف على علب بريد الأرشيف](archive-mailboxes.md) - جديد، لدعم إعادة الهيكلة، يحتوي على معلومات تصورية كانت في السابق في تمكين علب بريد الأرشيف.

### <a name="microsoft-priva"></a>Microsoft Priva

- [أصبحت إدارة الخصوصية الآن Microsoft Priva](/privacy/priva/priva-overview) - التي تم تحديثها لإعادة تصميم المنتج وحلوله، وإدارة مخاطر الخصوصية في Priva وطلبات حقوق موضوع Priva.

### <a name="sensitivity-labels"></a>تسميات الحساسية

- دعم مجموعات أدوار [MIP الجديدة وأدوارها](get-started-with-sensitivity-labels.md#permissions-required-to-create-and-manage-sensitivity-labels)، الآن في المعاينة.
- قدرات [مراقبة جديدة](apply-sensitivity-label-automatically.md#monitoring-your-auto-labeling-policy) لنهج التسمية التلقائية.
- تم الآن طرح: التسمية الافتراضية للمستندات الموجودة في القناة الحالية (معاينة)، ونص التبرير Office على الويب.
- تم الإعلان عن قناة Semi-Annual يوليو مع الإصدار 2202+: التأليف المشترك والتدقيق Outlook.

## <a name="december-2021"></a>ديسمبر 2021

### <a name="compliance-and-service-assurance"></a>التوافق وضمان الخدمة

- [تم تحديث إعلام انتهاك Azure و Dynamics 365 و Windows](/compliance/regulatory/gdpr-breach-notification) بموجب القانون العام لحماية البيانات (GDPR) لتوضيح أن العملاء لا يحتاجون إلى استخدام خدمة دفع مثل Defender for Cloud لتلقي إعلامات الأمان والخصوصية

### <a name="ediscovery"></a>eDiscovery

- [Advanced eDiscovery سير عمل المحتوى](teams-workflow-in-advanced-ediscovery.md#reference-guide) في Microsoft Teams - تم تحديثه مع دليل مرجعي سريع جديد قابل للتنزيل لإدارة Teams في Advanced eDiscovery

### <a name="information-governance"></a>إدارة المعلومات

- [تمكين علب بريد الأرشيف في مركز التوافق](enable-archive-mailboxes.md#run-diagnostics-on-archive-mailboxes) - قسم مضاف حول أداة التشخيص الجديدة لعلب بريد الأرشيف
- [استخدام تحميل الشبكة لاستيراد ملفات PST](use-network-upload-to-import-pst-files.md#step-2-upload-your-pst-files-to-microsoft-365) في مؤسستك Microsoft 365 - يدعم استيراد PST الآن AzCopy v10
- [استعادة علبة بريد](restore-an-inactive-mailbox.md) غير نشطة - إجراء تمت مراجعته لاستعادة علبة بريد غير نشطة عن طريق إضافة LegacyExchangeDN أولا من علبة البريد غير النشطة إلى علبة البريد الهدف

### <a name="information-protection"></a>حماية المعلومات

- [نشر حل MIP](information-protection-solution.md) - إرشادات خطوة بخطوة جديدة للعملاء الذين يبحثون عن خارطة طريق وصفية لنشر حماية البيانات في Microsoft (MIP)

### <a name="retention-and-records-management"></a>إدارة الاستبقاء والسجلات

- إرشادات جديدة [حول المدة التي يستغرقها تطبيق سياسات الاستبقاء](create-retention-policies.md#how-long-it-takes-for-retention-policies-to-take-effect)
- يتم طرح إعدادات المستأجر الجديدة: إعداد إدارة السجلات الذي يمنع تحرير الخصائص لعناصر SharePoint الملصقات التي تم وضع علامة عليها كسجل ومقفلة، وإعدادات أخرى لمنع المستخدمين من إلغاء تأمين العناصر التي تم وضع علامة عليها كسجل

### <a name="sensitivity-labels"></a>تسميات الحساسية

- التسمية الإلزامية والتسمية الافتراضية ل Power BI متوفرة الآن بشكل عام (GA)

## <a name="november-2021"></a>نوفمبر 2021

### <a name="compliance-manager"></a>إدارة التوافق

يمكن عرض تحديثات المحتوى الجديدة في [ما الجديد في Microsoft Compliance Manager](compliance-manager-whats-new.md).

### <a name="device-onboarding"></a>تشغيل الجهاز

لقد تم إضافة المقالات التالية لضيف الجهاز:

- [أجهزة macOS المجهزة في Microsoft 365 عامة (معاينة)](device-onboarding-macos-overview.md)
- [أجهزة macOS التي يتم تشغيلها أو إيقاف تشغيلها في Microsoft 365 التوافق باستخدام Intune (معاينة)](device-onboarding-offboarding-macos-intune.md)
- [أجهزة macOS التي يتم تشغيلها أو إيقاف تشغيلها في حلول التوافق باستخدام Intune لعملاء نقطة النهاية ل Microsoft Defender (معاينة)](device-onboarding-offboarding-macos-intune-mde.md)
- [أجهزة macOS التي يتم تشغيلها أو إيقاف تشغيلها في Microsoft 365 التوافق باستخدام JAMF Pro (معاينة)](device-onboarding-offboarding-macos-jamfpro.md)
- [أجهزة macOS التي يتم تشغيلها أو إيقاف تشغيلها في حلول التوافق باستخدام JAMF Pro ل Microsoft Defender لعملاء نقطة النهاية (معاينة)](device-onboarding-offboarding-macos-jamfpro-mde.md)

### <a name="ediscovery"></a>eDiscovery

- [استخدام تنسيق الحالة الجديد في](advanced-ediscovery-new-case-format.md) Advanced eDiscovery تم إصدار تنسيق حالة جديدة إلى التوفر العام وإعادة تسميته من "تنسيق حالة كبيرة"

### <a name="retention-and-records-management"></a>إدارة الاستبقاء والسجلات
- طرح: إعدادات إدارة السجلات الجديدة التي تتحكم في ما إذا كان SharePoint أو OneDrive يمكن للمستخدمين حذفها. في السابق، كانت تسميات الاستبقاء التي تم تكوينها للاحتفاظ بالمحتوى ولم يتم وضع علامة على العناصر كسجلات تمنع المستخدمين من حذف المحتوى المسمى في SharePoint عند السماح بهذا الإجراء في OneDrive. لمزيد من المعلومات، راجع [كيفية عمل الاستبقاء SharePoint OneDrive](retention-policies-sharepoint.md#how-retention-works-for-sharepoint-and-onedrive).

### <a name="sensitive-information-types"></a>أنواع المعلومات الحساسة

إضافة المقالات الجديدة التالية:

- [التعرف على أنواع المعلومات الحساسة المستندة إلى مطابقة البيانات بدقة](sit-learn-about-exact-data-match-based-sits.md)
- [بدء استخدام أنواع المعلومات الحساسة المستندة إلى مطابقة البيانات بدقة](sit-get-started-exact-data-match-based-sits-overview.md)
- [تصدير بيانات المصدر لنوع المعلومات الحساسة المستندة إلى مطابقة البيانات بدقة](sit-get-started-exact-data-match-export-data.md)
- [إنشاء المخطط لأنواع المعلومات الحساسة المستندة إلى مطابقة البيانات بدقة](sit-get-started-exact-data-match-create-schema.md)
- [قم بتهش جدول مصدر المعلومات الحساس وتحميله للحصول على بيانات دقيقة تتطابق مع أنواع المعلومات الحساسة](sit-get-started-exact-data-match-hash-upload.md)
- [إنشاء بيانات دقيقة تتطابق مع نوع المعلومات الحساسة/حزمة القاعدة](sit-get-started-exact-data-match-create-rule-package.md)
- [اختبار نوع معلومات دقيق يطابق المعلومات الحساسة](sit-get-started-exact-data-match-test.md)
- [إدارة مخطط مطابقة البيانات بدقة](sit-use-exact-data-manage-schema.md)
- [تحديث ملف جدول مصدر المعلومات الحساس](sit-use-exact-data-refresh-data.md)

### <a name="sensitivity-labels"></a>تسميات الحساسية
- أصبح اسم نطاق تسميات [Azure Purview](/azure/purview/create-sensitivity-label) الآن "أصول البيانات المكيسمة".

## <a name="october-2021"></a>أكتوبر 2021

### <a name="app-governance"></a>إدارة التطبيق

- [تم إصدار الوظائف الإضافية لإدارة التطبيق ل Defender for Cloud Apps إلى التوفر العام](/cloud-app-security/app-governance-manage-app-governance). تم نقل وثائق إدارة التطبيق للانضمام إلى وثائق Defender for Cloud Apps.

### <a name="compliance--service-assurance"></a>ضمان & الخدمة

- [ضمان الخدمة](/compliance) - مراجعة تحديثات المحتوى ربع السنة للشهادات وبيانات قابلية التطبيق) إدارة أصول مركز البيانات
  - بنية مركز البيانات والبنية الأساسية
  - استمرارية أعمال مركز البيانات واسترداد حالات الكوارث
  - الضمانات البيئة في مركز البيانات
  - أمان الوصول الفعلي إلى مركز البيانات
  - Microsoft 365 توافق SDL
  - Microsoft 365 التحكم بالوصول إلى مهندسي الخدمة
  - دليل تقييم المخاطر ل MS Cloud

### <a name="data-loss-prevention"></a>منع فقدان البيانات

- [تعرف على تم تحديث "منع فقدان](endpoint-dlp-learn-about.md) البيانات" لدعم macOS وتصنيفه المتقدم؛ تم تحديثه لإنشاء نهج DLP مخصص لتدقيق نشاط كل أنواع الملفات المعتمدة.
- [بدء استخدام Microsoft 365 تم](endpoint-dlp-getting-started.md) تحديث منع فقدان بيانات نقطة النهاية ل دعم macOS والتصنيف المتقدم.
- [تم تحديث استخدام منع فقدان](endpoint-dlp-using.md) البيانات في نقطة النهاية ل دعم macOS والتصنيف المتقدم.
- [تم تحديث مرجع](dlp-policy-tips-reference.md) تلميحات نهج منع فقدان البيانات لدعم macOS والتصنيف المتقدم.
- [تم تحديث أجهزة macOS Microsoft 365 (معاينة)](device-onboarding-macos-overview.md) لدعم macOS والتصنيف المتقدم.
- أضفت الصفحات الجديدة التالية للأجهزة التي تم اضافتها:
  - [أجهزة macOS التي يتم تشغيلها أو إيقاف تشغيلها في Microsoft 365 التوافق باستخدام Intune (معاينة)](device-onboarding-offboarding-macos-intune.md)
  - [أجهزة macOS التي يتم تشغيلها أو إيقاف تشغيلها في حلول التوافق باستخدام Intune لعملاء نقطة النهاية ل Microsoft Defender (معاينة)](device-onboarding-offboarding-macos-intune-mde.md)
  - [أجهزة macOS التي يتم تشغيلها أو إيقاف تشغيلها في Microsoft 365 التوافق باستخدام JAMF Pro (معاينة)](device-onboarding-offboarding-macos-jamfpro.md)
  - [أجهزة macOS التي يتم تشغيلها أو إيقاف تشغيلها في حلول التوافق باستخدام JAMF Pro ل Microsoft Defender لعملاء نقطة النهاية (معاينة)](device-onboarding-offboarding-macos-jamfpro-mde.md)

### <a name="ediscovery"></a>eDiscovery

- تجميع مرفقات السحابة في [Advanced eDiscovery](advanced-ediscovery-cloud-attachments.md) بالإضافة إلى تجميع أحدث إصدار من مرفق السحابة، يمكنك تجميع الإصدار الذي تمت مشاركته في رسالة بريد إلكتروني أو محادثة دردشة Teams؛ يمكن تجميع الإصدار المشترك من خلال الإمكانية الجديدة لتطبيق تسمية استبقاء تلقائيا على مرفقات السحابة.
- إعداد [الإصدارات](advanced-ediscovery-historical-versions.md) السابقة في Advanced eDiscovery وظيفة جديدة تفهرس كل إصدارات المستندات المخزنة على موقع SharePoint للبحث؛ وهذا يعني أنه يتم إرجاع إصدارات المستندات التي تحتوي على محتوى يطابق استعلام مجموعة في نتائج البحث.

### <a name="encryption"></a>التشفير

- [استخدم التشفير من طرف إلى طرف لمحتوى](/microsoftteams/teams-end-to-end-encryption) جديد للمكالمات Microsoft Teams واحد إلى واحد (معاينة عامة) للمعاينة العامة.

### <a name="information-governance"></a>إدارة المعلومات

- [يسمح لك إعداد موصل](import-epic-data.md) لاستيراد موصل جديد لبيانات تدقيق Epic EHR باستيراد البيانات من نظام سجلات الرعاية الصحية الإلكترونية Epic لدعم سيناريو إساءة استخدام بيانات المرضى العام الجديد لإدارة مخاطر insider.
- [يتيح لك](import-healthcare-data.md) إعداد موصل لاستيراد بيانات تدقيق EHR الخاصة بالرعاية الصحية موصلا جديدا لاستيراد البيانات من نظام سجلات الرعاية الصحية الإلكترونية لدعم سيناريو إساءة استخدام بيانات المرضى العام الجديد لإدارة مخاطر insider.

### <a name="retention-and-records-management"></a>إدارة الاستبقاء والسجلات
- [يتم إصدار نطاقات النهج](retention.md#adaptive-or-static-policy-scopes-for-retention) التكييفية في المعاينة لنهج الاستبقاء ونهج تسميات الاستبقاء.
- يمكنك الآن [تطبيق تسمية استبقاء تلقائيا استنادا إلى تسمية الحساسية](apply-retention-labels-automatically.md#identify-files-and-emails-that-have-a-sensitivity-label).
- خطة الملف لديها عملية [استيراد جديدة](file-plan-manager.md#import-retention-labels-into-your-file-plan).
- [الإعدادات الشائعة](retention-settings.md) لنهج الاستبقاء ونهج تسميات الاستبقاء: مقالة جديدة للحصول على معلومات مفصلة حول تكوين النطاقات التكييفية والإعدادات الأخرى في كل من سياسات الاستبقاء ونهج تسميات الاستبقاء.

### <a name="sensitive-information-types"></a>أنواع المعلومات الحساسة

- [تعرف على المحتوى الجديد للكيانات المسماة (معاينة)](named-entities-learn.md) للكيانات المسماة.
- [استخدم الكيانات المسماة في المحتوى الجديد لنهج](named-entities-use.md) منع فقدان البيانات (معاينة) عند استخدام الكيانات المسماة.

### <a name="sensitivity-labels"></a>تسميات الحساسية

- [يتم طرح التسميات](mip-easy-trials.md) الافتراضية والسياسات الافتراضية للعملاء المؤهلين.

## <a name="september-2021"></a>سبتمبر 2021

### <a name="app-governance"></a>إدارة التطبيق

- [تم تغيير سير عمل معلومات](app-governance-get-started.md) بدء استخدام التطبيق المبسط وأضاف ارتباطات جديدة إلى تسجيل المعاينة العامة
- [إضافة تعريف تنبيهات الكشف الجديد](app-governance-anomaly-detection-alerts.md#app-made-high-volume-of-importance-mail-read-and-created-inbox-rule) (محدث؛ تعريف جديد مضاف لتنبيهات المجموعة)

### <a name="auditing"></a>التدقيق

- [تشغيل التدقيق أو](turn-audit-log-search-on-or-off.md) إيقاف تشغيله إضافة مقطع جديد حول كيفية تدقيق التغييرات التي يتم إدخالها على حالة التدقيق في المؤسسة نفسها؛ وهذا يعني أنه يتم تسجيل سجلات التدقيق عند تشغيل التدقيق أو إيقاف تشغيله؛ يمكنك البحث في Exchange تدقيق المسؤول لسجلات التدقيق هذه

### <a name="communication-compliance"></a>توافق الاتصالات

- [إرشادات توافق الاتصالات مع حلول SIEM](communication-compliance-siem.md) لتكامل توافق الاتصالات مع حلول SIEM)

### <a name="compliance-offerings"></a>عروض التوافق

- [أمان السحابة متعدد المستويات (MTCS)](/compliance/regulatory/offering-mtcs-singapore) تحديثات قياسية ل سنغافورة لتغطية Dynamics 365
- [صناعة بطاقات الدفع (PCI)](/compliance/regulatory/offering-pci-dss) تحديثات معايير أمان البيانات (DSS) SharePoint عبر الإنترنت
- إرشادات برنامج عميل جديد في القسم [508](/compliance/regulatory/offering-section-508-vpats) من الولايات المتحدة
- [إرشادات الوصول إلى](/compliance/regulatory/offering-wcag-2-1) محتوى ويب إرشادات برنامج العميل الجديد

### <a name="compliance--service-assurance"></a>ضمان & الخدمة

- [مراجعة تحديثات](/compliance/) المحتوى كل ثلاثة أشهر لضمان الخدمة للشهادات وبيانات إمكانية التطبيق
  - إتلاف الأجهزة التي تحمل البيانات
  - هجمات DDOS

### <a name="data-connectors"></a>موصلات البيانات

- [أرشفة بيانات](archiving-third-party-data.md#data-connectors-in-the-us-government-cloud) جهة خارجية في موصلات بيانات Microsoft 365 من CellTrust و17a-4 LLC متوفرة الآن في مؤسسات سحابة القطاع الحكومي في السحابة "الحكومة الأمريكية"
- [يوفر إعداد موصل لأرشفة بيانات YouTube](archive-youtube-data.md) إرشادات جديدة لهذه الميزة في المعاينة العامة.

### <a name="ediscovery"></a>eDiscovery

- استخدام محرر [KQL](ediscovery-kql-editor.md) لإنشاء استعلامات بحث معاينة عامة لطريقة جديدة لإنشاء استعلامات البحث في البحث في المحتوى و Core eDiscovery و Advanced eDiscovery؛ يوفر محرر KQL الإمداد التلقائي للخصائص والشروط المعتمدة القابلة للبحث ويعرض قوائم بالقيم المعتمدة للخصائص والشروط القياسية؛ كما يوفر محرر KQL اقتراحات للكشف عن الأخطاء واقتراحات لإصلاح الأخطاء المحتملة في استعلامات البحث

### <a name="information-barriers"></a>عوائق المعلومات

- [بدء استخدام ميزة المعاينة الجديدة لعوائق](information-barriers-policies.md#step-6-information-barriers-modes) المعلومات لأوضاع حواجز المعلومات
- [حواجز المعلومات مع Microsoft Teams](/microsoftteams/information-barriers-in-teams) معاينة جديدة لأوضاع عوائق المعلومات
- [حواجز المعلومات مع OneDrive](/onedrive/information-barriers) معاينة جديدة لأوضاع حواجز المعلومات
- [حواجز المعلومات مع SharePoint](/sharepoint/information-barriers) معاينة جديدة عبر الإنترنت لأوضاع حواجز المعلومات

### <a name="insider-risk-management"></a>إدارة مخاطر Insider

- [بدء استخدام ميزة معاينة جديدة لإدارة مخاطر insider](insider-risk-management-configure.md#recommended-actions-preview) للبدء في الإجراءات الموصى بها
- [التحقق من أنشطة مخاطر insider](insider-risk-management-activities.md#get-help-managing-your-insider-risk-alert-queue) الجديدة 'الحصول على المساعدة في إدارة قائمة انتظار تنبيهات المخاطر ل insider'
- [بدء استخدام إعدادات إدارة مخاطر insider](insider-risk-management-settings.md#admin-notifications) ميزة معاينة إعدادات إعلامات المسؤول الجديدة

### <a name="retention-and-records-management"></a>إدارة الاستبقاء والسجلات
- [تتوفر الآن مراجعة الترتيب](disposition.md) متعددة المراحل بشكل عام (GA)، مع أحداث [تدقيق جديدة](search-the-audit-log-in-security-and-compliance.md#disposition-review-activities). تسمح لك مراجعة الترتيب متعددة المراحل بتحديد ما يصل إلى خمس مراحل متتالية من مراجعة الترتيب لتسمية استبقاء، ويمكن للمراجعين إضافة مستخدمين آخرين إلى مرحلة مراجعة الترتيب الخاصة بهم. يمكنك أيضا تخصيص إعلامات البريد الإلكتروني والتذكيرات.
- تتوفر [القنوات الخاصة Teams](create-retention-policies.md#retention-policy-for-teams-locations) الاستبقاء الآن بشكل عام (GA).

### <a name="sensitivity-labels"></a>تسميات الحساسية
- [تتوفر](sensitivity-labels-coauthoring.md) الآن ميزة التأليف المشترك وال حفظ تلقائي بشكل عام (GA) ل Windows (إصدار 2107 كحد أدنى من القناة الحالية أو قناة المؤسسة الشهرية) و macOS (الإصدار 16.51 كحد أدنى).
- طرح Office التي تستخدم تسميات مضمنة: يدعم إعداد التسمية الافتراضي الآن المستندات الموجودة والمستندات الجديدة. يوفر هذا التغيير في السلوك المساواة مع عميل التسمية الموحد ل Azure Information Protection. لمزيد من المعلومات حول الإصدار لكل تطبيق والحد الأدنى من الإصدارات، راجع جدول الإمكانات ل Word Excel والإصدارات PowerPoint.[](sensitivity-labels-office-apps.md#sensitivity-label-capabilities-in-word-excel-and-powerpoint)
- تدعم تسميات الحاويات الآن [إعدادات ارتباط المشاركة الافتراضية باستخدام الإعدادات المتقدمة في PowerShell](sensitivity-labels-teams-groups-sites.md#configure-settings-for-the-default-sharing-link-type-for-a-site-by-using-powershell-advanced-settings).
- تتضمن [جداول الإمكانات](sensitivity-labels-office-apps.md#support-for-sensitivity-label-capabilities-in-apps) التي تتضمن الحد الأدنى للإصدارات المعتمدة للتسمية المضمنة الآن إصدارات للقناة الحالية، وقناة المؤسسة الشهرية، Semi-Annual Enterprise Channel.
