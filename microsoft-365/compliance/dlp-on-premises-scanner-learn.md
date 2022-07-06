---
title: تعرّف على الماسح الضوئي المحلي لمنع فقدان البيانات
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
description: يوسع الماسح الضوئي المحلي لمنع فقدان البيانات مراقبة أنشطة الملفات وإجراءات الحماية لهذه الملفات إلى مشاركات الملفات المحلية ومجلدات SharePoint ومكتبات المستندات. يتم مسح الملفات ضوئيا وحمايتها بواسطة الماسح الضوئي ل Azure حماية البيانات (AIP)
ms.openlocfilehash: 8edf472fe65380b708a833864ccceedadb240191
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/06/2022
ms.locfileid: "66629806"
---
# <a name="learn-about-the-data-loss-prevention-on-premises-scanner"></a>التعرف على الماسح الضوئي المحلي لمنع فقدان البيانات

يعد الماسح الضوئي المحلي لمنع فقدان البيانات جزءا من مجموعة تفادي فقدان البيانات في Microsoft Purview (DLP) من الميزات التي يمكنك استخدامها لاكتشاف العناصر الحساسة وحمايتها عبر خدمات Microsoft 365. لمزيد من المعلومات حول جميع عروض DLP من Microsoft، راجع [التعرف على منع فقدان البيانات](dlp-learn-about-dlp.md).

يتتبع **الماسح الضوئي المحلي ل DLP** البيانات الثابتة المحلية في مشاركات الملفات ومكتبات مستندات SharePoint ومجلداته للعناصر الحساسة التي، إذا تم تسريبها، قد تشكل خطرا على مؤسستك أو تشكل خطرا على انتهاك نهج التوافق. يمنحك ذلك الرؤية والتحكم الذي تحتاجه لضمان استخدام العناصر الحساسة وحمايتها بشكل صحيح، وللمساعدة على منع السلوك المحفوظ بالمخاطر الذي قد يعرضها للخطر. يكشف الماسح الضوئي المحلي ل DLP عن المعلومات الحساسة باستخدام أنواع [المعلومات الحساسة](create-a-custom-sensitive-information-type.md) [المضمنة](sensitive-information-type-entity-definitions.md) أو المخصصة أو [تسميات الحساسية](sensitivity-labels.md) أو خصائص الملف. يتم إظهار المعلومات حول ما يفعله المستخدمون بالعناصر الحساسة في [مستكشف النشاط](data-classification-activity-explorer.md) ويمكنك فرض إجراءات الحماية على تلك العناصر عبر [نهج DLP](create-test-tune-dlp-policy.md).

## <a name="the-dlp-on-premises-scanner-relies-on-azure-information-protection-scanner"></a>يعتمد الماسح الضوئي المحلي ل DLP على الماسح الضوئي ل Azure حماية البيانات

يعتمد الماسح الضوئي المحلي ل DLP على التنفيذ الكامل للماسح الضوئي ل Azure حماية البيانات (AIP) لمراقبة العناصر الحساسة وتسميتها وحمايتها. إذا لم تكن على دراية بالماسح الضوئي ل AIP، نوصي بشدة بالتعرف عليه. راجع هذه المقالات:

- [ما هو Azure حماية البيانات](/azure/information-protection/what-is-information-protection)
- [ما هو الماسح الضوئي الموحد للوصف حماية البيانات Azure](/azure/information-protection/deploy-aip-scanner)
- [متطلبات تثبيت ونشر الماسح الضوئي الموحد للوصف حماية البيانات Azure](/azure/information-protection/deploy-aip-scanner-prereqs)
- [البرنامج التعليمي: تثبيت الماسح الضوئي الموحد للوصف حماية البيانات Azure (AIP)](/azure/information-protection/tutorial-install-scanner)
- [تكوين الماسح الضوئي الموحد للوصف حماية البيانات Azure وتثبيته](/azure/information-protection/deploy-aip-scanner-configure-install)
- [Azure حماية البيانات عميل التسمية الموحد - محفوظات إصدار الإصدار ونهج الدعم](/azure/information-protection/rms-client/unifiedlabelingclient-version-release-history)

## <a name="dlp-on-premises-scanner-actions"></a>إجراءات الماسح الضوئي المحلي ل DLP

يكشف الماسح الضوئي المحلي ل DLP عن الملفات باستخدام إحدى الطرق الأربعة التالية:

- أنواع المعلومات الحساسة
- أوصاف الحساسية
- ملحق الملف
- خصائص المستند المخصصة على ملفات Office فقط 

عندما يشكل الملف المكتشف خطرا محتملا إذا تم تسريبه أو انتهاك نهج الامتثال، يمكن أن يتخذ الماسح الضوئي المحلي ل DLP أحد هذه الإجراءات الأربعة.

|العمل |الوصف  |
|---------|---------|
|**حظر هؤلاء الأشخاص من الوصول إلى الملفات المخزنة في الماسح الضوئي المحلي - الجميع** | عند فرض هذا الإجراء، يحظر الوصول إلى كافة الحسابات باستثناء مالك المحتوى والحساب الأخير الذي عدل العنصر والمسؤول. يقوم بذلك عن طريق إزالة كافة الحسابات من أذونات NTFS/SharePoint على مستوى الملف باستثناء مالك الملف ومالك المستودع (المعين في إعداد [مالك المستودع المعين](/azure/information-protection/deploy-aip-scanner-configure-install#use-a-data-loss-prevention-dlp-policy-public-preview) في مهمة فحص المحتوى) والمعدل الأخير (يمكن تعريفه في SharePoint فقط) والمسؤول. يتم أيضا منح حساب الماسح الضوئي حقوق FC على الملف.|
|**حظر هؤلاء الأشخاص من الوصول إلى الملفات المخزنة في الماسح الضوئي المحلي - حظر الوصول على مستوى المؤسسة (العام)**    |عند فرض هذا الإجراء، يزيل **_Everyone_*_، و_*_NT AUTHORITY\authenticated users_*_، و_*_Domain Users_** SIDs من قائمة التحكم بالوصول إلى الملفات (ACL). سيتمكن المستخدمون والمجموعات الذين تم منحهم حقوقا صريحة للملف أو المجلد الأصل فقط من الوصول إلى الملف.|
|**تعيين الأذونات على الملف**|عند فرض هذا الإجراء، يجبر هذا الإجراء الملف على وراثة أذونات المجلد الأصل الخاص به. كن افتراضيا، سيتم فرض هذا الإجراء فقط إذا كانت الأذونات الموجودة في المجلد الأصل أكثر تقييدا من الأذونات الموجودة بالفعل في الملف. على سبيل المثال، إذا تم تعيين ACL على الملف للسماح **_بمستخدمين محددين_ *فقط وتم تكوين المجلد الأصل للسماح* بمجموعة _ _Domain Users_*_، فلن يتم توريث أذونات المجلد الأصل بواسطة الملف. يمكنك تجاوز هذا السلوك عن طريق تحديد الخيار _* Inherit حتى لو كانت الأذونات الأصل أقل تقييدا**.|
|**إزالة الملف من موقع غير صحيح**|عند فرض هذا الإجراء، يستبدل هذا الإجراء الملف الأصلي بملف كعب الروتين بملحق .txt ويضع نسخة من الملف الأصلي في مجلد العزل. 

## <a name="whats-different-in-the-on-premises-scanner"></a>ما هو المختلف في الماسح الضوئي المحلي

هناك بعض المفاهيم الإضافية التي تحتاج إلى أن تكون على علم بها قبل التعمق في الماسح الضوئي المحلي.

### <a name="aip-repositories-and-content-scan-jobs"></a>مستودعات AIP ومهام فحص المحتوى

يجب إنشاء مهام فحص محتوى AIP وتحديد المستودعات التي تستضيف الملفات التي تريد تقييمها بواسطة محرك DLP. تأكد من تمكين قواعد DLP في مهمة فحص محتوى AIP التي تم إنشاؤها.

### <a name="policy-tips"></a>تلميحات النهج

لا تتوفر [تلميحات النهج](use-notifications-and-policy-tips.md) في الماسح الضوئي المحلي.


### <a name="viewing-dlp-on-premises-scanner-events"></a>عرض أحداث الماسح الضوئي المحلي ل DLP

يمكنك عرض بيانات الماسح الضوئي المحلي ل DLP في [مستكشف نشاط](data-classification-activity-explorer.md) مركز التوافق M365. 

## <a name="next-steps"></a>الخطوات التالية

الآن بعد أن تعرفت على الماسح الضوئي المحلي ل DLP، فإن خطواتك التالية هي:

1. [بدء استخدام الماسح الضوئي المحلي ل DLP](dlp-on-premises-scanner-get-started.md)
2. [استخدام الماسح الضوئي المحلي ل DLP](dlp-on-premises-scanner-use.md)

## <a name="see-also"></a>راجع أيضًا

- [بدء استخدام الماسح الضوئي المحلي لمنع فقدان البيانات](dlp-on-premises-scanner-get-started.md)
- [استخدام الماسح الضوئي المحلي لمنع فقدان البيانات](dlp-on-premises-scanner-use.md)
- [التعرّف على تفادي فقدان البيانات](dlp-learn-about-dlp.md)
- [إنشاء نهج DLP واختباره وضبطه](create-test-tune-dlp-policy.md)
- [بدء استخدام مستكشف النشاط](data-classification-activity-explorer.md)
