---
title: التعرف على Microsoft 365 فقدان البيانات
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
search.appverid:
- MET150
description: Microsoft 365 الماسح الضوئي لفقد البيانات في الموقع إلى توسيع مراقبة أنشطة الملفات والإجراءات المتعلقة بالحماية لتلك الملفات إلى عمليات مشاركة الملفات SharePoint المجلدات ومكتبات المستندات. يتم فحص الملفات وحمايتها بواسطة ماسح ضوئي لحماية معلومات Azure (AIP)
ms.openlocfilehash: c696d4c4e8504d07ce69554c6ff52f264b8ba491
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 10/06/2021
ms.locfileid: "63575691"
---
# <a name="learn-about-the-microsoft-365-data-loss-prevention-on-premises-scanner"></a>التعرف على Microsoft 365 فقدان البيانات

إن الماسح الضوئي المحلي لمنع فقدان البيانات من Microsoft هو جزء من مجموعة الميزات Microsoft 365 فقدان البيانات (DLP) التي يمكنك استخدامها لاكتشاف العناصر الحساسة وحمايتها عبر Microsoft 365 الخدمات. لمزيد من المعلومات حول كل عروض DLP من Microsoft، راجع [التعرف على منع فقدان البيانات](dlp-learn-about-dlp.md).

يتتبع **الماسح الضوئي ل DLP** في الموقع عملية تتبع ارتباطات البيانات في مكانها في مشاركة الملفات ومكتبات مستندات SharePoint ومجلداتها للعناصر الحساسة التي، إذا تم تسريبها، قد تشكل خطرا على مؤسستك أو تشكل خطر انتهاك نهج التوافق. يوفر لك ذلك إمكانية الرؤية والتحكم التي تحتاج إليها لضمان استخدام العناصر الحساسة وحمايتها بشكل صحيح، وللمساعدة على منع السلوك الخطر الذي قد يؤدي إلى اختراقها. يكشف الماسح الضوئي ل DLP في الموقع عن المعلومات الحساسة باستخدام أنواع المعلومات الحساسة [](create-a-custom-sensitive-information-type.md) المضمنة أو المخصصة [](sensitivity-labels.md) أو تسميات الحساسية أو خصائص الملف.[](sensitive-information-type-entity-definitions.md) تظهر المعلومات المتعلقة بما يفعله المستخدمون بالعناصر الحساسة في مستكشف النشاط، [](data-classification-activity-explorer.md) كما يمكنك فرض إجراءات الحماية على تلك العناصر عبر [سياسات DLP](create-test-tune-dlp-policy.md).

## <a name="the-dlp-on-premises-scanner-relies-on-azure-information-protection-scanner"></a>يعتمد الماسح الضوئي ل DLP في الموقع على ماسح حماية معلومات Azure

يعتمد الماسح الضوئي المحلي ل DLP على التنفيذ الكامل للماسح الضوئي Azure Information Protection (AIP) لمراقبة العناصر الحساسة وتسميتها وحمايتها. إذا لم تكن ملما بماسح AIP الضوئي، نوصي بشدة بالإلمام به. راجع المقالات التالية:

- [ما هو Azure Information Protection](/azure/information-protection/what-is-information-protection)
- [ما هو ماسح التسمية الموحد في Azure Information Protection](/azure/information-protection/deploy-aip-scanner)
- [متطلبات تثبيت ماسح التسمية الموحد في Azure Information Protection ونشره](/azure/information-protection/deploy-aip-scanner-prereqs)
- [البرنامج التعليمي: تثبيت ماسح التسمية الموحد ل Azure Information Protection (AIP)](/azure/information-protection/tutorial-install-scanner)
- [تكوين ماسح التسمية الموحد في Azure Information Protection وتثبيته](/azure/information-protection/deploy-aip-scanner-configure-install)
- [عميل التسمية الموحد في Azure Information Protection - محفوظات الإصدارات ونسخة الدعم](/azure/information-protection/rms-client/unifiedlabelingclient-version-release-history)

## <a name="dlp-on-premises-scanner-actions"></a>إجراءات الماسح الضوئي في DLP

يكشف الماسح الضوئي ل DLP في الموقع عن الملفات باستخدام إحدى الطرق الأربعة التالية:

- أنواع المعلومات الحساسة
- تسميات الحساسية
- ملحق الملف
- خصائص المستند المخصص على Office الملفات فقط 

عندما يشكل ملف تم اكتشافه خطرا محتملا إذا تم تسريبه أو انتهاك نهج التوافق، يمكن أن يتخذ الماسح الضوئي ل DLP في الموقع أحد هذه الإجراءات الأربعة.

|الإجراء |الوصف  |
|---------|---------|
|**منع هؤلاء الأشخاص من الوصول إلى الملفات المخزنة في الماسح الضوئي المحلية - الجميع** | عند فرض هذا الإجراء، يمنع الوصول إلى كل الحسابات باستثناء مالك المحتوى، آخر حساب عدل العنصر والمسؤول. يقوم بذلك عن طريق إزالة كل الحسابات من أذونات NTFS/SharePoint على مستوى الملف باستثناء مالك الملف ومالك المستودع (الذي تم تعيينه في إعداد تعيين مالك المستودع في مهمة فحص [](/azure/information-protection/deploy-aip-scanner-configure-install#use-a-data-loss-prevention-dlp-policy-public-preview) المحتوى) والمعدل الأخير (يمكن تعريفه في SharePoint فقط) والمسؤول. يتم أيضا منح حساب الماسح الضوئي حقوق FC على الملف.|
|**منع هؤلاء الأشخاص من الوصول إلى الملفات المخزنة في الماسح الضوئي المحلي - حظر الوصول على مستوى المؤسسة (عام)**    |عند فرض هذا الإجراء، يقوم هذا الإجراء بإزالة **_ملفات SID لمستخدمي Everyone_*_و_*_NT AUTHORITY\authenticated users_*_و_*_Domain Users_** من قائمة التحكم بالوصول إلى الملفات (ACL). لن يتمكن من الوصول إلى الملف إلا المستخدمون والمجموعات التي تم منحها حقوقا واضحة للملف أو المجلد الأصل.|
|**تعيين الأذونات على الملف**|عند فرض هذا الإجراء، يجبر الملف على توريث أذونات المجلد الأصل الخاص به. افتراضيا، لن يتم فرض هذا الإجراء إلا إذا كانت الأذونات في المجلد الأصل أكثر تقييدا من الأذونات التي تكون موجودة بالفعل على الملف. على سبيل المثال، إذا تم تعيين ACL على الملف للسماح فقط لمستخدمين ***معينين_* وتكوين المجلد الأصل للسماح لمجموعة _ _Domain Users_ _، لن يتم توارث أذونات المجلد الأصل بواسطة *الملف. يمكنك تجاوز هذا السلوك عن طريق تحديد الخيار _* Inherit حتى لو كانت الأذونات الأصل أقل تقييدا**.|
|**إزالة الملف من موقع غير مناسب**|عند فرض هذا الإجراء، يستبدل الملف الأصلي بملف كبل .txt ثم يضع نسخة من الملف الأصلي في مجلد عزل. 

## <a name="whats-different-in-the-on-premises-scanner"></a>ما هو مختلف في الماسح الضوئي

هناك بعض المفاهيم الإضافية التي يجب أن تكون على علم بها قبل أن تتعمق في الماسح الضوئي في الموقع.

### <a name="aip-repositories-and-content-scan-jobs"></a>مستودعات AIP ومهمات فحص المحتوى

يجب إنشاء مهام فحص محتوى AIP وتحديد المستودعات التي تستضيف الملفات التي تريد تقييمها بواسطة مشغل DLP. تأكد من تمكين قواعد DLP في مهمة فحص محتوى AIP التي تم إنشاؤها.

### <a name="policy-tips"></a>تلميحات النهج

[لا تتوفر](use-notifications-and-policy-tips.md) تلميحات النهج في الماسح الضوئي في الموقع.


### <a name="viewing-dlp-on-premises-scanner-events"></a>عرض أحداث الماسح الضوئي ل DLP في الموقع

يمكنك عرض بيانات الماسح الضوئي ل DLP على الموقع في مستكشف نشاط مركز توافق M365[.](data-classification-activity-explorer.md) 

## <a name="next-steps"></a>الخطوات التالية

الآن وقد تعرفت على الماسح الضوئي ل DLP في الموقع، فإن الخطوات التالية هي:

1. [بدء استخدام الماسح الضوئي ل DLP](dlp-on-premises-scanner-get-started.md)
2. [استخدام الماسح الضوئي ل DLP](dlp-on-premises-scanner-use.md)

## <a name="see-also"></a>راجع أيضًا

- [بدء استخدام الماسح الضوئي لفقد بيانات Microsoft](dlp-on-premises-scanner-get-started.md)
- [استخدام الماسح الضوئي لاتقاء فقدان البيانات في Microsoft](dlp-on-premises-scanner-use.md)
- [التعرف على منع فقدان البيانات](dlp-learn-about-dlp.md)
- [إنشاء نهج DLP واختباره وضبطه](create-test-tune-dlp-policy.md)
- [بدء استخدام "مستكشف النشاط"](data-classification-activity-explorer.md)