---
title: ترحيل Exchange Online منع فقدان البيانات إلى مركز التوافق
f1.keywords:
- CSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: ''
audience: ITPro
ms.topic: article
f1_keywords:
- ms.o365.cc.DLPLandingPage
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
- SPO_Content
search.appverid:
- MET150
description: تعرف على كيفية التخطيط لنهج منع فقدان Exchange البيانات عبر الإنترنت وترحيلها إلى Microsoft 365 DLP.
ms.openlocfilehash: 07d0eb19155a7f91b30feb8d7938ea574b0e75f9
ms.sourcegitcommit: 355ab75eb7b604c6afbe9a5a1b97ef16a1dec4fc
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 02/14/2022
ms.locfileid: "63575074"
---
# <a name="migrate-exchange-online-data-loss-prevention-policies-to-compliance-center"></a>ترحيل Exchange Online منع فقدان البيانات إلى مركز التوافق

[Exchange Online يتم إهمال](/exchange/security-and-compliance/data-loss-prevention/data-loss-prevention) سياسات منع فقدان البيانات (DLP). [يتم توفير وظائف DLP](dlp-learn-about-dlp.md) الغنية، بما في Exchange Online DLP، [في Microsoft 365 التوافق](https://compliance.microsoft.com/datalossprevention?viewid=policies). يمكنك استخدام معالج ترحيل نهج DLP لمساعدتك على Exchange Online نهج DLP إلى مركز التوافق حيث يمكنك إدارتها.

يعمل معالج الترحيل من خلال قراءة تكوين سياسات DLP في Exchange ثم إنشاء سياسات مكررة في مركز التوافق. بشكل افتراضي، ينشئ المعالج الإصدارات الجديدة من السياسات في وضع الاختبار، بحيث  يمكنك معرفة تأثيرها في بيئتك دون فرض أي من الإجراءات. بمجرد أن تكون جاهزا للانتقال بشكل كامل إلى إصدارات مركز التوافق، **_يجب:_**

1. إلغاء تنشيط نهج المصدر أو حذفه في مركز إدارة Exchange (EAC).
1. قم بتحرير إصدار مركز التوافق من النهج وتغيير حالة التطبيق من **اختبار** إلى **فرض**. 

> [!WARNING]
> إذا لم تحذف نهج المصدر أو تحذفه في EAC قبل تعيين إصدار مركز التوافق لفرض مجموعتي النهج، فإن محاولة  فرض الإجراءات ستتلقى أحداثا مكررة. **_هذا تكوين غير معتمد._**


يقوم معالج الترحيل بترحيل سياسات EXO وقواعد تدفق البريد المقترنة فقط. لا يتم Exchange قواعد تدفق البريد بشكل مستقل.

## <a name="migration-workflow"></a>سير عمل الترحيل

هناك أربع مراحل هجاء نهج DLP من Exchange إلى وحدة تحكم إدارة DLP الموحدة في مركز التوافق.  

1. التحضير ل الترحيل
    1. يمكنك تقييم سياسات DLP Exchange Online (EXO) ومقارنتها ونهج DLP الخاصة بمركز التوافق للحصول على وظائف مكررة.
    1. تحديد سياسات EXO DLP التي تريد إحضارها تماما كما هي، يمكنك استخدام المعالج لترحيلها.
    1. تحديد سياسات EXO DLP التي تريد دمجها ودمجها في مركز إدارة Exchange، ثم استخدم معالج الترحيل لإحضارها إلى مركز التوافق.
1. تنفيذ عملية الترحيل - استخدام المعالج
1. الاختبار والتحقق من الصحة - فحص النتائج
1. تنشيط السياسات التي تم ترحيلها

## <a name="before-you-begin"></a>قبل البدء

### <a name="licensing-and-versions"></a>الترخيص والإصدارات

قبل أن تبدأ بتهجر سياسات DLP، يجب عليك تأكيد اشتراكك Microsoft 365 أي [](https://www.microsoft.com/microsoft-365/compare-microsoft-365-enterprise-plans?rtc=1) من الوظائف الإضافية. 

للوصول إلى معالج ترحيل النهج واستخدامه، يجب أن يكون لديك أحد هذه الاشتراكات أو الوظائف الإضافية

- Microsoft 365 E3
- Microsoft 365 E5
- Microsoft 365 A5 (EDU)
- Microsoft 365 E5 التوافق
- Microsoft 365 A5 التوافق
- Microsoft 365 E5 حماية المعلومات والحوكمة
- Microsoft 365 A5 حماية المعلومات والحوكمة

للحصول على قائمة مفصلة بمتطلبات ترخيص DLP، راجع Microsoft 365 إرشادات الترخيص لتوافق الأمان & البيانات [ومنع فقدان البيانات](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#information-protection)


### <a name="permissions"></a>الأذونات

يجب أن يكون للحساب الذي تستخدمه لتشغيل معالج الترحيل حق الوصول إلى كل من Exchange وحدة تحكم المسؤول DLP ووحدة تحكم DLP الموحدة في مركز التوافق.

## <a name="prepare-for-migration"></a>التحضير ل الترحيل

1. إذا لم تألف استخدام DLP أو وحدة تحكم DLP في مركز التوافق أو وحدة تحكم DLP في مركز إدارة Exchange، يجب عليك التعرف على نفسك قبل محاولة ترحيل النهج.
    1. [Exchange Online منع فقدان البيانات (DLP)](/exchange/security-and-compliance/data-loss-prevention/data-loss-prevention)
    1. [التعرف على Microsoft 365 فقدان بيانات نقطة النهاية](endpoint-dlp-learn-about.md#learn-about-microsoft-365-endpoint-data-loss-prevention)
    1. [إنشاء نهج DLP واختباره وضبطه](create-test-tune-dlp-policy.md)
1. قم بتقييم Exchange DLP ومركز التوافق عن طريق طرح هذه الأسئلة:


|سؤال  |الإجراء  | إجراء الترحيل|
|---------|---------|---------|
|هل ما زال النهج مطلوبا؟    |إذا لم يكن الأمر كذلك، فاحذفه أو قم إلغاء تنشيطه |عدم الترحيل|
|هل تتداخل مع أي سياسات أخرى Exchange مركز التوافق DLP؟     |إذا كانت الإجابة نعم، هل يمكنك دمج السياسات المتراكبة؟         |- إذا تداخل مع نهج Exchange آخر، فنشئ يدويا نهج DLP المجمع في مركز إدارة Exchange، ثم استخدم معالج الترحيل. </br> - إذا تداخل مع نهج مركز التوافق الموجود، يمكنك تعديل نهج مركز التوافق الحالي للمطابقة، ولا تقوم بترحيل Exchange الحالي|
|هل نهج Exchange DLP محدد بشكل ضيق، وهل له شروط والإجراءات والتضمينات والاستثناءات محددة بشكل جيد؟     |إذا كانت الإجابة نعم، فمن الجيد الترحيل باستخدام المعالج، دون النهج حتى تتذكر العودة لحذفه لاحقا         | الترحيل باستخدام المعالج|

## <a name="migration"></a>الترحيل

بعد تقييم كل Exchange DLP لمركز التوافق والتوافق للحاجة والتوافق، يمكنك استخدام معالج الترحيل.

1. افتح وحدة Microsoft 365 [مركز](https://compliance.microsoft.com/datalossprevention?viewid=policies) التوافق DLP.
2. إذا كان Exchange من سياسات DLP التي يمكن ترحيلها، سيظهر شعار في أعلى الصفحة يعلمك بذلك.
3. اختر **ترحيل السياسات** في الشعار لفتح معالج الترحيل. يتم سرد Exchange DLP. لا يمكن تحديد السياسات التي تم ترحيلها مسبقا.
4. حدد السياسات التي تريد ترحيلها. يمكنك ترحيلها بشكل فردي أو في مجموعات باستخدام نهج مرحلي أو كلها في وقت واحد. حدد **التالي**.
5. راجع جزء "النشرة المستعرضة" للحصول على أي تحذيرات أو رسائل. حل أي مشاكل قبل المتابعة.
6. حدد الوضع الذي تريد إنشاء نهج مركز التوافق الجديد فيه أو نشط **أو اختبار** أو **معطل**.   الإعداد الافتراضي هو **Test**. حدد **التالي**.
7. يمكنك إنشاء المزيد من نهج تستند إلى نهج DLP Exchange مواقع DLP الموحدة الأخرى، إذا أردت ذلك. سينتج عن ذلك نهج DLP موحد واحد جديد Exchange الترحيل ونهج DLP موحد واحد جديد لأي مواقع أخرى تختارها هنا.

> [!IMPORTANT]
> سيتم إسقاط أي شروط أو إجراءات نهج DLP Exchange لا تدعمها مواقع DLP أخرى، مثل الأجهزة أو SharePoint أو OneDrive أو المحلية أو MCAS أو Teams رسائل الدردشة والقناة من النهج الإضافي. هناك أيضا عمل مسبق يجب القيام به للمواقع الأخرى. راجع:
>- [التعرف على Microsoft 365 فقدان بيانات نقطة النهاية](endpoint-dlp-learn-about.md#learn-about-microsoft-365-endpoint-data-loss-prevention)
>- [بدء استخدام منع فقدان بيانات نقطة النهاية](endpoint-dlp-getting-started.md#get-started-with-endpoint-data-loss-prevention)
>- [استخدام منع فقدان البيانات في نقطة النهاية](endpoint-dlp-using.md#using-endpoint-data-loss-prevention)
>- [التعرف على Microsoft 365 فقدان البيانات](dlp-on-premises-scanner-learn.md#learn-about-the-microsoft-365-data-loss-prevention-on-premises-scanner)
>- [بدء استخدام الماسح الضوئي لمنع فقدان البيانات](dlp-on-premises-scanner-get-started.md#get-started-with-the-data-loss-prevention-on-premises-scanner)
>- [استخدام الماسح الضوئي Microsoft 365 فقدان البيانات](dlp-on-premises-scanner-use.md#use-the-microsoft-365-data-loss-prevention-on-premises-scanner)
>- [استخدام سياسات منع فقدان البيانات للتطبيقات السحابية غير الخاصة ب Microsoft](dlp-use-policies-non-microsoft-cloud-apps.md#use-data-loss-prevention-policies-for-non-microsoft-cloud-apps)
 
8. راجع إعدادات جلسة عمل معالج الترحيل. حدد **التالي**.
9. راجع تقرير الترحيل. انتبه إلى أي حالات فشل Exchange تدفق البريد الإلكتروني. يمكنك إصلاحها وهجراتها المقترنة.

ستظهر الآن السياسات التي تم ترحيلها في قائمة سياسات DLP في وحدة تحكم DLP في مركز التوافق. 

## <a name="common-errors-and-mitigation"></a>الأخطاء الشائعة وتخفيف المخاطر
|رسالة خطأ  |السبب  | خطوات التخفيف/الموصى بها|
|---------|---------|---------|
|يوجد نهج توافق بالاسم `<Name of the policy>` بالفعل في السيناريو (السيناريو) `Dlp`.    |من المرجح أن عملية ترحيل النهج هذه قد تم في وقت سابق ثم إعادة إجراءها في جلسة العمل نفسها |قم بتحديث جلسة العمل لتحديث قائمة السياسات المتوفرة ل الترحيل. يجب أن تكون كل السياسات التي تم ترحيلها مسبقا في `Already migrated` الولاية.|
|يوجد نهج توافق بالاسم `<Name of the policy>` بالفعل في السيناريو (السيناريو) `Hold`.     |يوجد نهج استبقاء بالاسم نفسه في المستأجر نفسه.       |- أعد تسمية نهج DLP في EAC باسم مختلف. </br> - إعادة محاولة الترحيل للحصول على النهج الذي تم التأثير عليه. |
|`DLP-group@contoso.com` لا يمكن استخدامه كقيمة للشرط المشتركة بواسطة لأنه مجموعة توزيع أو مجموعة أمان تمكين البريد. استخدم Shared by Member of predicate للكشف عن أنشطة أعضاء مجموعات معينة.     |تسمح قواعد النقل بأن يتم استخدام المجموعات `sender is` في الشرط ولكن DLP الموحد لا يسمح بذلك.         | قم بتحديث قاعدة النقل لإزالة كل عناوين البريد الإلكتروني للمجموعة `sender is` من الشرط وإضافة المجموعة إلى `sender is a member of` الشرط إذا لزم الأمر. إعادة محاولة الترحيل للحصول على النهج الذي تم التأثير عليه|
|لم يتم العثور على المستلم `DLP-group@contoso.com`. إذا تم إنشاؤها حديثا، ف إعادة محاولة العملية بعد وقت ما. إذا تم حذفها أو انتهت صلاحيتها، فيرجى إعادة التعيين باستخدام قيم صالحة والمحاولة مرة أخرى.     |من المرجح أن يكون عنوان المجموعة المستخدم `sender is a member of` `recipient is a member of` في أو الشرط منتهيا الصلاحية أو غير صالح.         | - إزالة/استبدال كل عناوين البريد الإلكتروني للمجموعة غير الصالحة في قاعدة النقل Exchange مركز الإدارة. </br> - إعادة محاولة الترحيل للحصول على النهج الذي تم التأثير عليه.|
|يجب أن تكون القيمة المحددة `FromMemberOf` في عملية التكرير مجموعة أمان تم تمكين البريد لها.     |تسمح قواعد النقل للمستخدمين الفرديين بأن يتم استخدامهم `sender is a member of` في الشرط ولكن DLP الموحد لا يسمح بذلك.         | - قم بتحديث قاعدة النقل لإزالة كل `sender is a member of` عناوين البريد الإلكتروني للمستخدم الفردية من الشرط وإضافة المستخدمين إلى `sender is` الشرط إذا لزم الأمر. </br> - إعادة محاولة الترحيل للحصول على النهج الذي تم التأثير عليه.|
|يجب أن تكون القيمة المحددة `SentToMemberOf` في عملية التكرير مجموعة أمان تم تمكين البريد لها.    |تسمح قواعد النقل للمستخدمين الفرديين بأن يتم استخدامهم `recipient is a member of` بموجب هذا الشرط ولكن DLP الموحد لا يسمح بذلك.         | - قم بتحديث قاعدة النقل لإزالة كل `recipient is a member of` عناوين البريد الإلكتروني للمستخدم الفردية من الشرط وإضافة المستخدمين إلى `recipient is` الشرط إذا لزم الأمر. </br> - إعادة محاولة الترحيل للحصول على النهج الذي تم التأثير عليه.|
|استخدام المعلمة `<Name of condition>` معتمد فقط Exchange. قم بإزالة هذه المعلمة أو تشغيل Exchange الموقع فقط.         | من المرجح وجود نهج آخر بالاسم نفسه في مركز التوافق مع مواقع أخرى مثل SPO/ODB/Teams التي لا يتم دعم الشرط المذكور لها. | أعد تسمية نهج DLP Exchange مركز الإدارة ثم أعد محاولة الترحيل.|

## <a name="testing-and-validation---prateek-and-aakash-to-provide-a-list-of-supported-predicates-and-known-issues-before-publishing--"></a>الاختبار والتحقق من الصحة <!--PRATEEK AND AAKASH TO PROVIDE A LIST OF SUPPORTED PREDICATES AND KNOWN ISSUES BEFORE PUBLISHING-->

اختبر سياساتك وراجعها.

1. اتبع إجراءات [اختبار نهج DLP](create-test-tune-dlp-policy.md#test-a-dlp-policy) .
2. راجع الأحداث التي تم إنشاؤها بواسطة النهج في ["مستكشف النشاط](data-classification-activity-explorer.md)".

## <a name="review-the-policy-matches-between-exchange-admin-center-dlp-and-microsoft-365-unified-dlp"></a>مراجعة تطابقات النهج بين Exchange إدارة DLP Microsoft 365 DLP الموحدة

لضمان عمل النهج التي تم ترحيلها كما هو متوقع، يمكنك تصدير التقارير من كل من مركزي الإدارة ومقارنة تطابقات النهج.

1. الاتصال إلى [Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).
2. تصدير تقرير [EAC DLP](/powershell/module/exchange/get-maildetaildlppolicyreport). يمكنك نسخ الأمر cmdlet هذا وإدراج القيم المناسبة:

```powershell
Get-MailDetailDlpPolicyReport -StartDate <dd/mm/yyyy -EndDate <dd/mm/yyyy> -PageSize 5000 | select Date, MessageId, DlpPolicy, TransportRule -Unique | Export-CSV <"C:\path\filename.csv"> 
```

3. تصدير [تقرير DLP الموحد](/powershell/module/exchange/get-dlpdetailreport). يمكنك نسخ الأمر cmdlet هذا وإدراج القيم المناسبة:

```powershell
Get-DlpDetailReport -StartDate <dd/mm/yyyy> -EndDate <dd/mm/yyyy> -PageSize 5000 | select Date, Location, DlpCompliancePolicy, DlpComplianceRule -Unique | Export-CSV <"C:\path\filename.csv">  
```

## <a name="activate-your-migrated-policies"></a>تنشيط سياساتك التي تم ترحيلها

بعد أن تقتنع بكيفية عمل سياساتك التي تم ترحيلها، يمكنك تعيينها إلى **فرض**.

1. افتح وحدة Exchange DLP في مركز الإدارة.
2. إلغاء تنشيط نهج المصدر أو حذفه.
3. افتح وحدة [Microsoft 365 مركز](https://compliance.microsoft.com/datalossprevention?viewid=policies) التوافق DLP وحدد النهج الذي تريد جعله نشطا لتحريره.
4. قم بتغيير الحالة إلى **تشغيل**.

## <a name="related-articles"></a>المقالات ذات الصلة

- [Exchange Online منع فقدان البيانات (DLP)](/exchange/security-and-compliance/data-loss-prevention/data-loss-prevention)
- [التعرف على منع فقدان البيانات](dlp-learn-about-dlp.md#learn-about-data-loss-prevention)
- [بدء استخدام "مستكشف النشاط"](data-classification-activity-explorer.md)
- [إنشاء نهج DLP واختباره وضبطه](create-test-tune-dlp-policy.md)
- [إنشاء نهج DLP من قالب](create-a-dlp-policy-from-a-template.md)
- [Exchange Online منع فقدان البيانات (DLP)](/exchange/security-and-compliance/data-loss-prevention/data-loss-prevention)
