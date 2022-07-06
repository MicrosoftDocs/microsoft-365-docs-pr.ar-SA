---
title: ترحيل نهج Exchange Online DLP إلى مركز التوافق
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
description: تعرف على كيفية التخطيط لنهج منع فقدان البيانات عبر الإنترنت في Exchange وترحيلها إلى DLP.
ms.openlocfilehash: 371dfafbbf6acf31587b0786a5b5594fb83571d9
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/06/2022
ms.locfileid: "66638268"
---
# <a name="migrate-exchange-online-data-loss-prevention-policies-to-microsoft-purview-compliance-portal"></a>ترحيل نهج منع فقدان البيانات Exchange Online إلى مدخل التوافق في Microsoft Purview

[يتم إهمال نهج منع فقدان البيانات (DLP) Exchange Online](/exchange/security-and-compliance/data-loss-prevention/data-loss-prevention). يتم تقديم [وظائف DLP أكثر ثراء](dlp-learn-about-dlp.md)، بما في ذلك Exchange Online DLP، في [مدخل التوافق في Microsoft Purview](https://compliance.microsoft.com/datalossprevention?viewid=policies). يمكنك استخدام معالج ترحيل نهج DLP لمساعدتك في إحضار نهج DLP Exchange Online إلى مركز التوافق حيث ستديرها.

يعمل معالج الترحيل من خلال قراءة تكوين نهج DLP في Exchange ثم إنشاء نهج مكررة في مركز التوافق. يقوم المعالج بشكل افتراضي بإنشاء الإصدارات الجديدة من النهج في وضع **الاختبار** ، حتى تتمكن من رؤية التأثير الذي قد يحدث في بيئتك دون فرض أي من الإجراءات. بمجرد أن تصبح جاهزا للانتقال بشكل كامل إلى إصدارات مركز التوافق، **_يجب عليك_**:

1. إلغاء تنشيط النهج المصدر أو حذفه في Exchange مسؤول Center (EAC).
1. تحرير إصدار مركز التوافق من النهج وتغيير حالته من **Test** إلى **Enforce**.

> [!WARNING]
> إذا لم تقم بحذف النهج المصدر أو إلغاء تنشيطه في EAC قبل تعيين إصدار مركز **التوافق لفرض كلتا** مجموعتي النهج، فستحاول فرض الإجراءات وستتلقى أحداثا متكررة. **_هذا تكوين غير معتمد._**

يقوم معالج الترحيل بترحيل نهج EXO وقواعد تدفق البريد المقترنة فقط. لا يتم ترحيل قواعد تدفق بريد Exchange المستقلة.

## <a name="migration-workflow"></a>سير عمل الترحيل

هناك أربع مراحل ترحيل نهج DLP من Exchange إلى وحدة تحكم إدارة DLP الموحدة في مركز التوافق.

1. التحضير لل ترحيل
    1. قم بتقييم نهج DLP Exchange Online (EXO) ونهج DLP لمركز التوافق لوظائف مكررة ومقارنتها.
    1. حدد نهج EXO DLP التي تريد إحضارها تماما كما هي، يمكنك استخدام المعالج بترحيلها.
    1. حدد نهج EXO DLP التي تريد دمجها ودمجها في مركز إدارة Exchange، ثم استخدم معالج الترحيل لإحضارها إلى مركز التوافق.
1. تنفيذ الترحيل - استخدام المعالج
1. الاختبار والتحقق من الصحة - فحص النتائج
1. تنشيط النهج التي تم ترحيلها

## <a name="before-you-begin"></a>قبل البدء

### <a name="licensing-and-versions"></a>الترخيص والإصدارات

قبل البدء في ترحيل نهج DLP، يجب عليك تأكيد [اشتراكك في Microsoft 365](https://www.microsoft.com/microsoft-365/compare-microsoft-365-enterprise-plans?rtc=1) وأي وظائف إضافية.

للوصول إلى معالج ترحيل النهج واستخدامه، يجب أن يكون لديك أحد هذه الاشتراكات أو الوظائف الإضافية

- Microsoft 365 E3
- Microsoft 365 E5
- Microsoft 365 A5 (EDU)
- التوافق Microsoft 365 E5
- التوافق Microsoft 365 A5
- Microsoft 365 E5 حماية المعلومات والحوكمة
- حماية المعلومات والحوكمة Microsoft 365 A5

للحصول على قائمة مفصلة بمتطلبات ترخيص DLP، راجع [إرشادات ترخيص Microsoft 365 للامتثال & الأمان، ومنع فقدان البيانات](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#information-protection)

### <a name="permissions"></a>الأذونات

يجب أن يكون للحساب الذي تستخدمه لتشغيل معالج الترحيل حق الوصول إلى كل من صفحة Exchange مسؤول Console DLP ووحدة تحكم DLP الموحدة في مركز التوافق.

## <a name="prepare-for-migration"></a>التحضير لل ترحيل

1. إذا كنت غير معتاد على DLP أو وحدة تحكم DLP لمركز التوافق أو وحدة تحكم DLP لمركز Exchange مسؤول، فيجب أن تتعرف على نفسك قبل محاولة ترحيل النهج.
    1. [نهج منع فقدان البيانات (DLP) Exchange Online](/exchange/security-and-compliance/data-loss-prevention/data-loss-prevention)
    1. [التعرّف على تفادي فقدان بيانات نقطة النهاية](endpoint-dlp-learn-about.md)
    1. [إنشاء نهج DLP واختباره وضبطه](create-test-tune-dlp-policy.md)
1. قم بتقييم نهج Exchange DLP ومركز التوافق من خلال طرح هذه الأسئلة:

|السؤال|العمل|إجراء الترحيل|
|---|---|---|
|هل لا تزال السياسة مطلوبة؟|إذا لم يكن الأمر كذلك، فحذفه أو قم بإلغاء تنشيطه|عدم الترحيل|
|هل يتداخل مع أي نهج Exchange أو Compliance center DLP أخرى؟|إذا كان الجواب نعم، هل يمكنك دمج النهج المتداخلة؟|- إذا تداخل مع نهج Exchange آخر، فتنشئ نهج DLP المدمج يدويا في مركز مسؤول Exchange، ثم استخدم معالج الترحيل. </br> - إذا تداخل مع نهج مركز التوافق الموجود، يمكنك تعديل نهج مركز التوافق الحالي ليتطابق، ولا تقم بترحيل إصدار Exchange|
|هل نهج Exchange DLP محدد النطاق بإحكام، وهل له شروط وإجراءات وتضمينات واستثناءات محددة جيدا؟|إذا كان الجواب نعم، فمن الجيد الترحيل باستخدام المعالج، فقم بتدوين النهج بحيث تتذكر العودة لحذفه لاحقا|الترحيل باستخدام المعالج|

## <a name="migration"></a>الترحيل

بعد تقييم كافة نهج DLP لمركز Exchange والامتثال للحاجة والتوافق، يمكنك استخدام معالج الترحيل.

1. افتح وحدة تحكم [DLP مدخل التوافق في Microsoft Purview](https://compliance.microsoft.com/datalossprevention?viewid=policies).
2. إذا كان هناك نهج Exchange DLP التي يمكن ترحيلها، فسيظهر شعار في أعلى الصفحة يعلمك بذلك.
3. اختر **نهج الترحيل** في الشعار لفتح معالج الترحيل. يتم سرد كافة نهج Exchange DLP. يتعذر تحديد النهج التي تم ترحيلها مسبقا.
4. حدد النهج التي تريد ترحيلها. يمكنك ترحيلها بشكل فردي، أو في مجموعات باستخدام نهج مرحلي أو كلها في وقت واحد. حدد **التالي**.
5. راجع جزء القائمة المنبثقة للاطلاع على أي تحذيرات أو رسائل. حل أي مشاكل قبل المتابعة.
6. حدد الوضع الذي تريد إنشاء نهج مركز التوافق الجديد فيه أو **نشط** أو **اختبار** أو **معطل**.  الإعداد الافتراضي هو **الاختبار**. حدد **التالي**.
7. إذا أردت، يمكنك إنشاء المزيد من النهج المستندة إلى نهج Exchange DLP لمواقع DLP الموحدة الأخرى. سيؤدي ذلك إلى نهج DLP موحد جديد لنهج Exchange الذي تم ترحيله ونهج DLP موحد جديد واحد لأي مواقع أخرى تختارها هنا.

> [!IMPORTANT]
> سيتم إسقاط أي شروط وإجراءات لنهج Exchange DLP غير معتمدة من قبل مواقع DLP الأخرى، مثل الأجهزة أو SharePoint أو OneDrive أو المحلي أو MCAS أو رسائل القناة من النهج الإضافي. أيضا، هناك عمل مسبق يجب القيام به للمواقع الأخرى. راجع:
>- [التعرّف على تفادي فقدان بيانات نقطة النهاية](endpoint-dlp-learn-about.md)
>- [للحصول على متطلبات إضافية لنشر Endpoint DLP، راجع البدء في تفادي فقدان البيانات على الأجهزة.](endpoint-dlp-getting-started.md)
>- [استخدام تفادي فقدان البيانات في نقطة النهاية](endpoint-dlp-using.md)
>- [التعرف على الماسح الضوئي المحلي لمنع فقدان البيانات](dlp-on-premises-scanner-learn.md)
>- [بدء استخدام الماسح الضوئي المحلي لمنع فقدان البيانات](dlp-on-premises-scanner-get-started.md)
>- [استخدام الماسح الضوئي المحلي لمنع فقدان بيانات Microsoft Purview](dlp-on-premises-scanner-use.md)
>- [استخدام نهج منع فقدان البيانات لتطبيقات السحابة غير التابعة ل Microsoft](dlp-use-policies-non-microsoft-cloud-apps.md)
 
8. راجع إعدادات جلسة عمل معالج الترحيل. حدد **التالي**.
9. راجع تقرير الترحيل. انتبه إلى أي حالات فشل تتضمن قواعد تدفق بريد Exchange. يمكنك إصلاحها وإعادة تهيئة النهج المقترنة بها.

ستظهر النهج التي تم ترحيلها الآن في قائمة نهج DLP في وحدة تحكم DLP لمركز الامتثال.

## <a name="common-errors-and-mitigation"></a>الأخطاء الشائعة والتخفيف من المخاطر

|رسالة خطأ|السبب|خطوات التخفيف/الموصى بها|
|---|---|---|
|يوجد بالفعل نهج توافق بالاسم `<Name of the policy>` في السيناريو (السيناريوهات `Dlp`).|من المحتمل أن يكون ترحيل النهج هذا قد تم في وقت سابق ثم تمت إعادة تنفيذه في نفس جلسة العمل|تحديث جلسة العمل لتحديث قائمة النهج المتوفرة لل ترحيل. يجب أن تكون كافة النهج التي تم ترحيلها مسبقا في الحالة `Already migrated` .|
|يوجد بالفعل نهج توافق بالاسم `<Name of the policy>` في السيناريو (السيناريوهات `Hold`).|يوجد نهج استبقاء بنفس الاسم في نفس المستأجر.|- إعادة تسمية نهج DLP في EAC باسم مختلف. </br> - إعادة محاولة الترحيل للنهج المتأثر.|
|`DLP-group@contoso.com` لا يمكن استخدامها كقيمة لشرط "المشتركة حسب" لأنها مجموعة توزيع أو مجموعة أمان ممكنة للبريد. استخدم "المشتركة من قبل عضو دالة التقييم" للكشف عن الأنشطة التي يقوم بها أعضاء مجموعات معينة.|تسمح قواعد النقل باستخدام المجموعات في `sender is` الشرط ولكن DLP الموحد لا يسمح بذلك.|تحديث قاعدة النقل لإزالة كافة عناوين البريد الإلكتروني للمجموعة `sender is` من الشرط وإضافة المجموعة إلى `sender is a member of` الشرط إذا لزم الأمر. إعادة محاولة الترحيل للنهج المتأثر|
|تعذر العثور على المستلم `DLP-group@contoso.com`. إذا تم إنشاؤه حديثا، فقم بإعادة محاولة العملية بعد وقت ما. إذا تم حذفها أو انتهت صلاحيتها، يرجى إعادة التعيين بقيم صالحة والمحاولة مرة أخرى.|من المحتمل أن يكون عنوان المجموعة المستخدم في `sender is a member of` أو `recipient is a member of` الشرط منتهيا أو غير صالح.|- إزالة/استبدال كافة عناوين البريد الإلكتروني للمجموعة غير الصالحة في قاعدة النقل في مركز إدارة Exchange. </br> - إعادة محاولة الترحيل للنهج المتأثر.|
|يجب أن تكون القيمة المحددة في `FromMemberOf` دالة التقييم مجموعة أمان ممكنة للبريد.|تسمح قواعد النقل للمستخدمين الفرديين باستخدام الشرط `sender is a member of` ولكن DLP الموحد لا يسمح بذلك.|- تحديث قاعدة النقل لإزالة كافة عناوين البريد الإلكتروني للمستخدم الفردية `sender is a member of` من الشرط وإضافة المستخدمين إلى `sender is` الشرط إذا لزم الأمر. </br> - إعادة محاولة الترحيل للنهج المتأثر.|
|يجب أن تكون القيمة المحددة في `SentToMemberOf` دالة التقييم مجموعة أمان ممكنة للبريد.|تسمح قواعد النقل للمستخدمين الفرديين باستخدام الشرط `recipient is a member of` ولكن DLP الموحد لا يسمح بذلك.|- تحديث قاعدة النقل لإزالة كافة عناوين البريد الإلكتروني للمستخدم الفردية `recipient is a member of` من الشرط وإضافة المستخدمين إلى `recipient is` الشرط إذا لزم الأمر. </br> - إعادة محاولة الترحيل للنهج المتأثر.|
|استخدام المعلمة `<Name of condition>` معتمد فقط ل Exchange. قم بإزالة هذه المعلمة أو قم بتشغيل موقع Exchange فقط.|من المحتمل وجود نهج آخر بنفس الاسم في مركز التوافق مع مواقع أخرى مثل SPO/ODB/Teams التي لا يتم اعتماد الشرط المذكور لها.|أعد تسمية نهج DLP في مركز إدارة Exchange وأعد محاولة الترحيل.|

## <a name="testing-and-validation---prateek-and-aakash-to-provide-a-list-of-supported-predicates-and-known-issues-before-publishing--"></a>الاختبار والتحقق من الصحة <!--PRATEEK AND AAKASH TO PROVIDE A LIST OF SUPPORTED PREDICATES AND KNOWN ISSUES BEFORE PUBLISHING-->

اختبر نهجك وراجعها.

1. اتبع إجراءات [نهج اختبار DLP](create-test-tune-dlp-policy.md#test-a-dlp-policy) .
2. راجع الأحداث التي تم إنشاؤها بواسطة النهج في [مستكشف النشاط](data-classification-activity-explorer.md).

## <a name="review-the-policy-matches-between-exchange-admin-center-dlp-and-microsoft-purview-unified-dlp"></a>مراجعة تطابقات النهج بين Exchange مسؤول Center DLP وMicrosoft Purview Unified DLP

للتأكد من أن النهج التي تم ترحيلها تتصرف كما هو متوقع، يمكنك تصدير التقارير من مركزي الإدارة وإجراء مقارنة بين تطابقات النهج.

1. الاتصال [Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).
2. تصدير [تقرير EAC DLP](/powershell/module/exchange/get-maildetaildlppolicyreport). يمكنك نسخ أمر cmdlet هذا وإدراج القيم المناسبة:

   ```powershell
   Get-MailDetailDlpPolicyReport -StartDate <dd/mm/yyyy -EndDate <dd/mm/yyyy> -PageSize 5000 | select Date, MessageId, DlpPolicy, TransportRule -Unique | Export-CSV <"C:\path\filename.csv">
   ```

3. تصدير [تقرير DLP الموحد](/powershell/module/exchange/get-dlpdetailreport). يمكنك نسخ أمر cmdlet هذا وإدراج القيم المناسبة:

   ```powershell
   Get-DlpDetailReport -StartDate <dd/mm/yyyy> -EndDate <dd/mm/yyyy> -PageSize 5000 | select Date, Location, DlpCompliancePolicy, DlpComplianceRule -Unique | Export-CSV <"C:\path\filename.csv">
   ```

## <a name="activate-your-migrated-policies"></a>تنشيط النهج التي تم ترحيلها

بمجرد أن تكون راضيا عن كيفية عمل النهج التي تم ترحيلها، يمكنك تعيينها إلى **فرض**.

1. افتح وحدة تحكم Exchange مسؤول Center DLP.
2. إلغاء تنشيط نهج المصدر أو حذفه.
3. افتح وحدة تحكم [DLP مدخل التوافق في Microsoft Purview](https://compliance.microsoft.com/datalossprevention?viewid=policies) وحدد النهج الذي تريد جعله نشطا لتحريره.
4. تغيير الحالة **لتشغيلها**.

## <a name="related-articles"></a>المقالات ذات الصلة

- [نهج منع فقدان البيانات (DLP) Exchange Online](/exchange/security-and-compliance/data-loss-prevention/data-loss-prevention)
- [التعرّف على تفادي فقدان البيانات](dlp-learn-about-dlp.md)
- [بدء استخدام مستكشف النشاط](data-classification-activity-explorer.md)
- [إنشاء نهج DLP واختباره وضبطه](create-test-tune-dlp-policy.md)
- [إنشاء نهج DLP من قالب](create-a-dlp-policy-from-a-template.md)
- [نهج منع فقدان البيانات (DLP) Exchange Online](/exchange/security-and-compliance/data-loss-prevention/data-loss-prevention)
