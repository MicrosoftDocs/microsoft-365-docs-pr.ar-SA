---
title: إنشاء نهج أمان الأجهزة في Basic Mobility and Security
f1.keywords:
- NOCSH
ms.author: kwekua
author: kwekua
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
ms.custom:
- AdminSurgePortfolio
- AdminTemplateSet
- admindeeplinkEXCHANGE
search.appverid:
- MET150
description: استخدم Basic Mobility and Security لإنشاء نهج الأجهزة التي تحمي معلومات مؤسستك.
ms.openlocfilehash: f6cbcd72f5e5cae93b7fa775d7bce6f2906f454e
ms.sourcegitcommit: 1fa0b15f86470c49dddf0d6de59d553a38ae259b
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 06/03/2022
ms.locfileid: "65863217"
---
# <a name="create-device-security-policies-in-basic-mobility-and-security"></a>إنشاء نهج أمان الأجهزة في Basic Mobility and Security

يمكنك استخدام Basic Mobility and Security لإنشاء نهج الأجهزة التي تساعد على حماية معلومات مؤسستك على Microsoft 365 من الوصول غير المصرح به. يمكنك تطبيق النهج على أي جهاز محمول في مؤسستك حيث يكون لدى مستخدم الجهاز ترخيص Microsoft 365 قابل للتطبيق وقد سجل الجهاز في Basic Mobility and Security.

## <a name="before-you-begin"></a>قبل البدء

> [!IMPORTANT]
> قبل أن تتمكن من إنشاء نهج جهاز محمول، يجب تنشيط وإعداد Basic Mobility and Security. لمزيد من المعلومات، راجع نظرة عامة على التنقل الأساسي والأمان.

- تعرف على الأجهزة وتطبيقات الأجهزة المحمولة وإعدادات الأمان التي يدعمها Basic Mobility and Security. راجع [قدرات التنقل الأساسي والأمان](capabilities.md).
- أنشئ مجموعات أمان تتضمن Microsoft 365 المستخدمين الذين تريد نشر النهج لهم ولمستخدمين قد ترغب في استبعادهم من حظر الوصول إلى Microsoft 365. نوصي بأن تقوم باختبار النهج قبل نشر نهج جديد إلى مؤسستك عن طريق نشره على عدد قليل من المستخدمين. يمكنك إنشاء مجموعة أمان تتضمن نفسك فقط أو عدد صغير Microsoft 365 المستخدمين الذين يمكنهم اختبار النهج نيابة عنك واستخدامها. لمعرفة المزيد حول مجموعات الأمان، راجع [إنشاء مجموعة أمان أو تحريرها أو حذفها](../email/create-edit-or-delete-a-security-group.md).
- لإنشاء نهج التنقل والأمان الأساسية ونشرها في Microsoft 365، يجب أن تكون مسؤولا عاما Microsoft 365. لمزيد من المعلومات، راجع [الأذونات في مركز توافق & الأمان](../../security/office-365-security/permissions-in-the-security-and-compliance-center.md).
- قبل نشر النهج، قم بإعلام مؤسستك بالتأثيرات المحتملة لتسجيل جهاز في Basic Mobility and Security. استنادا إلى كيفية إعداد النهج، يمكن حظر الأجهزة غير المتوافقة من الوصول إلى Microsoft 365 والبيانات، بما في ذلك التطبيقات المثبتة والصور والمعلومات الشخصية على جهاز مسجل، ويمكن حذف البيانات.

> [!NOTE]
> تتجاوز النهج وقواعد الوصول التي تم إنشاؤها في Basic Mobility and Security for Microsoft 365 Business Standard Exchange ActiveSync نهج علبة بريد الأجهزة المحمولة وقواعد الوصول إلى الأجهزة التي تم إنشاؤها في <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">مركز إدارة Exchange</a>. بعد تسجيل جهاز في Basic Mobility and Security for Microsoft 365 Business Standard، يتم تجاهل أي نهج Exchange ActiveSync لعلبة بريد الجهاز المحمول أو قاعدة الوصول إلى الجهاز المطبقة على الجهاز. لمعرفة المزيد حول Exchange ActiveSync، راجع [Exchange ActiveSync في Exchange Online](/exchange/clients-and-mobile-in-exchange-online/exchange-activesync/exchange-activesync).

## <a name="step-1-create-a-device-policy-and-deploy-to-a-test-group"></a>الخطوة 1: إنشاء نهج جهاز ونشره في مجموعة اختبار

قبل أن تتمكن من البدء، تأكد من تنشيط وإعداد Basic Mobility and Security. للحصول على الإرشادات، راجع [نظرة عامة على التنقل الأساسي والأمان](overview.md).

1. من المستعرض، اكتب <https://compliance.microsoft.com/basicmobilityandsecurity>.

2. حدد **إنشاء نهج**.

   :::image type="content" source="../../media/basic-mobility-security/basic-mobility-microsoft-purview.png" alt-text="إعدادات نهج التنقل والأمان الأساسية.":::

3. في صفحة **إعدادات النهج** ، حدد المتطلبات التي تريد تطبيقها على الأجهزة المحمولة في مؤسستك.

4. **تتطلب إدارة ملف تعريف البريد الإلكتروني**: عند تمكينها، تعتبر الأجهزة التي لا تحتوي على ملف تعريف بريد إلكتروني مدار بواسطة Basic Mobility and Security غير متوافقة. لا يمكن أن يكون للجهاز ملف تعريف بريد إلكتروني مدار عندما لا يكون مستهدفا بشكل صحيح، أو إذا قام المستخدم بإعداد حساب البريد الإلكتروني يدويا على الجهاز. عند تركه **غير ممكن** (افتراضي)، لا يتم تقييم هذا الإعداد للتوافق أو عدم التوافق. للحصول على إرشادات حول كيفية توافق المستخدمين عند تحديد هذا الخيار، راجع العثور على [حساب بريد إلكتروني موجود](/intune-user-help/existing-company-email-account-found).

5. في الصفحة **هل تريد تطبيق هذا النهج الآن؟** اختر المجموعات التي تريد تطبيق هذا النهج عليها.

6. حدد **إنشاء هذا النهج**.

يتم دفع النهج إلى جهاز كل مستخدم ينطبق النهج على المرة التالية التي يسجل فيها الدخول إلى Microsoft 365 باستخدام جهازه المحمول. إذا لم يكن لدى المستخدمين نهج مطبق على أجهزتهم المحمولة من قبل، بعد نشر النهج، فسيحصلون على إعلام على أجهزتهم يتضمن خطوات تسجيل وتفعيل Basic Mobility and Security. لمزيد من المعلومات، راجع [تسجيل جهازك المحمول باستخدام Basic Mobility and Security](enroll-your-mobile-device.md). حتى يكمل التسجيل في Basic Mobility and Security التي تستضيفها خدمة Intune، يتم تقييد الوصول إلى البريد الإلكتروني OneDrive والخدمات الأخرى. بعد إكمال التسجيل باستخدام تطبيق Intune Company Portal، يمكنهم استخدام الخدمات ويتم تطبيق النهج على أجهزتهم.

## <a name="step-2-verify-that-your-policy-works"></a>الخطوة 2: التحقق من عمل النهج الخاص بك

بعد إنشاء نهج جهاز، تحقق من أن النهج يعمل كما تتوقع قبل نشره في مؤسستك.

1. من المستعرض، اكتب [https://compliance.microsoft.com/basicmobilityandsecurity](https://compliance.microsoft.com/basicmobilityandsecurity).
2. حدد **عرض قائمة الأجهزة المدارة**.
3. تحقق من حالة أجهزة المستخدم التي تم تطبيق النهج عليها. تريد إدارة **حالة** الأجهزة **.**
4. يمكنك أيضا إجراء مسح كامل أو انتقائي على جهاز بالنقر فوق **إعادة تعيين المصنع** أو **إزالة بيانات الشركة** من الزر **"إدارة** " بعد تحديد جهاز. للحصول على الإرشادات، راجع [مسح جهاز محمول في Microsoft 365.

## <a name="step-3-deploy-a-policy-to-your-organization"></a>الخطوة 3: نشر نهج إلى مؤسستك

بعد إنشاء نهج الجهاز والتحقق من أنه يعمل كما هو متوقع، قم بنشره في مؤسستك.

1. من نوع المستعرض: [https://compliance.microsoft.com/basicmobilityandsecurity](https://compliance.microsoft.com/basicmobilityandsecurity).
2. حدد النهج الذي تريد نشره، واختر **"تحرير"** إلى جانب **المجموعات المطبقة عليه.**
3. ابحث عن مجموعة لإضافتها وانقر فوق **"تحديد**".
4. حدد **الإعداد "إغلاق** وتغيير **".**
5. حدد **نهج الإغلاق** **والتحرير.**

يتم دفع النهج إلى الجهاز المحمول لكل مستخدم ينطبق النهج على المرة التالية التي يسجل فيها الدخول إلى Microsoft 365 من جهازه المحمول. إذا لم يكن لدى المستخدمين نهج مطبق على أجهزتهم المحمولة، فسيحصلون على إعلام على أجهزتهم يتضمن خطوات لتسجيله وتنشيطه ل Basic Mobility and Security. بعد إكمال التسجيل، يتم تطبيق النهج على جهازه. لمزيد من المعلومات، راجع [تسجيل جهازك المحمول باستخدام Basic Mobility and Security](enroll-your-mobile-device.md).

## <a name="step-4-block-email-access-for-unsupported-devices"></a>الخطوة 4: حظر الوصول إلى البريد الإلكتروني للأجهزة غير المعتمدة

للمساعدة في تأمين معلومات مؤسستك، يجب حظر وصول التطبيق إلى البريد الإلكتروني Microsoft 365 للأجهزة المحمولة التي لا يدعمها Basic Mobility and Security. للحصول على قائمة بالأجهزة المدعومة، راجع [الأجهزة المدعومة](../../admin/basic-mobility-security/capabilities.md).

**لحظر الوصول إلى التطبيق:**

1. من المستعرض، اكتب [https://compliance.microsoft.com/basicmobilityandsecurity](https://compliance.microsoft.com/basicmobilityandsecurity).
2. حدد **إدارة إعدادات الوصول إلى الجهاز على مستوى المؤسسة**.
3. لحظر الأجهزة غير المعتمدة، اختر **Access** ضمن **"إذا لم يكن الجهاز مدعوما بواسطة Basic Mobility and Security for Microsoft 365**"، ثم حدد **"حفظ**".

   :::image type="content" source="../../media/basic-mobility-security/basic-mobility-access.png" alt-text="خيار الوصول إلى حظر التنقل والأمان الأساسي.":::

## <a name="step-5-choose-security-groups-to-be-excluded-from-conditional-access-checks"></a>الخطوة 5: اختيار مجموعات الأمان التي سيتم استبعادها من عمليات التحقق من الوصول المشروط

إذا كنت تريد استبعاد بعض الأشخاص من عمليات التحقق من الوصول المشروط على أجهزتهم المحمولة وأنشأت مجموعة أمان واحدة أو أكثر لهؤلاء الأشخاص، فإضافة مجموعات الأمان هنا. لن يكون لدى الأشخاص في هذه المجموعات أي نهج مفروضة على أجهزتهم المحمولة المدعومة. هذا هو الخيار الموصى به إذا لم تعد ترغب في استخدام Basic Mobility and Security في مؤسستك.

1. من المستعرض، اكتب [https://compliance.microsoft.com/basicmobilityandsecurity](https://compliance.microsoft.com/basicmobilityandsecurity).

2. حدد **إدارة إعدادات الوصول إلى الجهاز على مستوى المؤسسة**.

   :::image type="content" source="../../media/basic-mobility-security/basic-mobility-microsoft-purview.png" alt-text="يقوم التنقل الأساسي والأمان بإنشاء خيار نهج.":::

3. حدد **"إضافة"** لإضافة مجموعة الأمان التي تحتوي على مستخدمين تريد استبعادهم من حظر الوصول إلى Microsoft 365. عند إضافة مستخدم إلى هذه القائمة، يمكنه الوصول إلى Microsoft 365 البريد الإلكتروني عند استخدام جهاز غير معتمد.

4. حدد مجموعة الأمان التي تريد استخدامها في لوحة **تحديد المجموعة** .

5. حدد الاسم، ثم **أضف** > **حفظا**.

6. في لوحة **إعدادات الوصول إلى الجهاز على مستوى المؤسسة** ، اختر **"حفظ**".

   :::image type="content" source="../../media/basic-mobility-security/basic-mobility-groups.png" alt-text="يسمح التنقل الأساسي والأمان بخيار الوصول.":::

## <a name="what-is-the-impact-of-security-policies-on-different-device-types"></a>ما تأثير نهج الأمان على أنواع الأجهزة المختلفة؟

عند تطبيق نهج على أجهزة المستخدم، يختلف التأثير على كل جهاز إلى حد ما بين أنواع الأجهزة. راجع الجدول التالي للحصول على أمثلة حول تأثير النهج على الأجهزة المختلفة.

|**نهج الأمان**|**الروبوت**|**Samsung KNOX**|**دائره الرقابه الداخليه**|**ملاحظات**|
|:-----|:-----|:-----|:-----|:-----|
|طلب نسخة احتياطية مشفرة|لا|نعم|نعم|النسخ الاحتياطي المشفر لنظام التشغيل iOS مطلوب.|
|حظر النسخ الاحتياطي للسحابة|نعم|نعم|نعم|حظر النسخ الاحتياطي من Google على Android (باللون الرمادي)، والنسخ الاحتياطي السحابي على iOS.|
|حظر مزامنة المستند|لا|لا|نعم|iOS: حظر المستندات في السحابة.|
|حظر مزامنة الصور |لا|لا|نعم|iOS (أصلي): حظر دفق الصور.|
|حظر التقاط الشاشة |لا|نعم|نعم|تم حظره عند محاولته.|
|حظر مؤتمر الفيديو |لا|لا|نعم|تم حظر FaceTime على iOS، وليس على Skype أو غيرها.|
|حظر إرسال البيانات التشخيصية |لا|نعم|نعم|حظر إرسال تقرير تعطل Google على Android.|
|حظر الوصول إلى متجر التطبيقات |لا|نعم|نعم|أيقونة متجر التطبيقات مفقودة على الصفحة الرئيسية لنظام التشغيل Android، معطلة على Windows، مفقودة على iOS.|
|طلب كلمة مرور لمتجر التطبيقات |لا|لا|نعم|iOS: كلمة المرور المطلوبة لمشتريات iTunes.|
|حظر الاتصال بالتخزين القابل للإزالة |لا|نعم|N/A|Android: تظهر بطاقة SD باللون الرمادي في الإعدادات، Windows إعلام المستخدم، والتطبيقات المثبتة غير متوفرة|
|حظر اتصال Bluetooth |عرض الملاحظات|عرض الملاحظات|نعم|لا يمكننا تعطيل BlueTooth كإعداد على Android. بدلا من ذلك، نقوم بتعطيل جميع المعاملات التي تتطلب BlueTooth: Advanced Audio Distribution و Audio/Video Remote Control والأجهزة الخالية من اليدين وسماعة الرأس الهاتف Book Access والمنفذ التسلسلي. تظهر رسالة منبثقة صغيرة في أسفل الصفحة عند استخدام أي من هذه الرسائل.|

## <a name="what-happens-when-you-delete-a-policy-or-remove-a-user-from-the-policy"></a>ماذا يحدث عند حذف نهج أو إزالة مستخدم من النهج؟

عند حذف نهج أو إزالة مستخدم من مجموعة تم نشر النهج إليها، قد تتم إزالة إعدادات النهج Microsoft 365 ملف تعريف البريد الإلكتروني ورسائل البريد الإلكتروني المخزنة مؤقتا من جهاز المستخدم. راجع الجدول التالي لمعرفة ما تمت إزالته لأنواع الأجهزة المختلفة.

|**ما الذي تمت إزالته**|**دائره الرقابه الداخليه**|**Android (بما في ذلك Samsung KNOX**|
|:-----|:-----|:-----|
|ملفات تعريف البريد الإلكتروني<sup>المدارة 1</sup>|نعم|لا|
|حظر النسخ الاحتياطي للسحابة|نعم|لا|

<sup>1</sup> إذا تم نشر النهج مع تحديد **الخيار "ملف تعريف البريد الإلكتروني** "، يتم حذف ملف تعريف البريد الإلكتروني المدار ورسائل البريد الإلكتروني المخزنة مؤقتا في ملف التعريف هذا من جهاز المستخدم.

تتم إزالة النهج من الجهاز المحمول لكل مستخدم يطبق النهج على المرة التالية التي يتحقق فيها جهازه باستخدام Basic Mobility and Security. إذا قمت بنشر نهج جديد ينطبق على أجهزة المستخدم هذه، فستتم مطالبتها بإعادة التسجيل في Basic Mobility and Security.

يمكنك أيضا مسح جهاز إما بشكل كامل، أو مسح المعلومات التنظيمية بشكل انتقائي من الجهاز. لمزيد من المعلومات، راجع [مسح جهاز محمول في Basic Mobility and Security](wipe-mobile-device.md).

## <a name="related-content"></a>المحتويات ذات الصلة

[نظرة عامة على التنقل الأساسي والأمان](overview.md) (مقال)\
[قدرات التنقل الأساسي والأمان](capabilities.md) (مقالة)