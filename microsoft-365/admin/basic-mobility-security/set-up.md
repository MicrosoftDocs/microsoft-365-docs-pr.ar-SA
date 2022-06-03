---
title: إعداد التنقل والأمان الأساسيين
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
search.appverid:
- MET150
description: قم بإعداد Basic Mobility and Security لتأمين الأجهزة المحمولة للمستخدمين وإدارتها من خلال تنفيذ إجراءات مثل مسح الجهاز عن بعد.
ms.openlocfilehash: 04480e59177dc9b51bc50e413715e0ad82c7f461
ms.sourcegitcommit: 1fa0b15f86470c49dddf0d6de59d553a38ae259b
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 06/03/2022
ms.locfileid: "65863152"
---
# <a name="set-up-basic-mobility-and-security"></a>إعداد التنقل والأمان الأساسيين

يساعدك Basic Mobility and Security المدمج ل Microsoft 365 على تأمين وإدارة الأجهزة المحمولة للمستخدمين مثل أجهزة iPhone وiPad وAndroids والهواتف Windows. يمكنك إنشاء نهج أمان الجهاز وإدارتها، ومسح جهاز عن بعد، وعرض تقارير مفصلة عن الجهاز.

هل لديك أسئلة؟ For a FAQ to help address common questions, see [Basic Mobility and Security Frequently-asked questions (FAQ)](frequently-asked-questions.yml). تجدر الإشارة إلى أنه لا يمكنك استخدام حساب مسؤول مفوض لإدارة Basic Mobility and Security. لمزيد من المعلومات، راجع [الشركاء: عرض الإدارة المفوضة](https://support.microsoft.com/office/partners-offer-delegated-administration-26530dc0-ebba-415b-86b1-b55bc06b073e). 

إدارة الأجهزة هي جزء من مركز التوافق & الأمان لذلك ستحتاج إلى الانتقال إلى هناك لبدء إعداد Basic Mobility and Security.

## <a name="activate-the-basic-mobility-and-security-service"></a>تنشيط خدمة Basic Mobility and Security

1. سجل الدخول إلى Microsoft 365 باستخدام حساب المسؤول العام.

2. انتقل إلى [تنشيط التنقل الأساسي والأمان](https://admin.microsoft.com/EAdmin/Device/IntuneInventory.aspx).

   قد يستغرق تنشيط Basic Mobility and Security بعض الوقت. عند الانتهاء، ستتلقى رسالة بريد إلكتروني تشرح الخطوات التالية التي يجب اتخاذها.

## <a name="set-up-mobile-device-management"></a>إعداد إدارة الجهاز الجوال

عندما تكون الخدمة جاهزة، أكمل الخطوات التالية لإنهاء الإعداد.

### <a name="step-1-required-configure-domains-for-basic-mobility-and-security"></a>الخطوة 1: (مطلوب) تكوين المجالات للتنقل الأساسي والأمان

إذا لم يكن لديك مجال مخصص مقترن Microsoft 365 أو إذا لم تكن تدير أجهزة Windows، يمكنك تخطي هذا المقطع. وإلا، فستحتاج إلى إضافة سجلات DNS للمجال لدى مضيف DNS. إذا قمت بإضافة السجلات بالفعل، كجزء من إعداد مجالك باستخدام Microsoft 365، فأنت جاهز تماما. بعد إضافة السجلات، تتم إعادة توجيه Microsoft 365 المستخدمين في مؤسستك الذين يسجلون الدخول على جهاز Windows الخاص بهم باستخدام عنوان بريد إلكتروني يستخدم مجالك المخصص للتسجيل في Basic Mobility and Security.

هل تحتاج إلى مساعدة في إعداد السجلات؟ ابحث عن جهة تسجيل المجالات وحدد اسم جهة التسجيل للانتقال إلى تعليمات مفصلة خطوة بخطوة لإنشاء سجل DNS في القائمة المتوفرة في ["إضافة سجلات DNS" لتوصيل مجالك](/office365/admin/get-help-with-domains/create-dns-records-at-any-dns-hosting-provider). استخدم هذه الإرشادات لإنشاء سجلات CNAME الموضحة في [تبسيط التسجيل Windows دون Azure AD Premium](/mem/intune/enrollment/windows-enroll#simplify-windows-enrollment-without-azure-ad-premium).

بعد إضافة سجلي CNAME، عد إلى مركز توافق & الأمان وانتقل إلى **إدارة جهاز** **منع** >  فقدان البيانات لإكمال الخطوة التالية.

### <a name="step-2-required-configure-an-apns-certificate-for-ios-devices"></a>الخطوة 2: (مطلوب) تكوين شهادة APNs لأجهزة iOS

لإدارة أجهزة iOS مثل iPad وiPhones، تحتاج إلى إنشاء شهادة APNs.

1. سجل الدخول إلى Microsoft 365 باستخدام حساب المسؤول العام.

2. انتقل إلى [مركز مسؤولي Microsoft 365](https://portal.office.com/adminportal/home?#/MifoDevices)، واختر **شهادة APNs لنظام التشغيل iOS**.

4. في صفحة الإعدادات شهادة الإعلامات المؤقتة من Apple، اختر **"التالي**".

5. حدد **"تنزيل ملف CSR** " واحفظ طلب توقيع الشهادة في مكان ما على الكمبيوتر الذي ستتذكره. حدد **التالي**.

6. في صفحة إنشاء شهادة APNs:

   - حدد مدخل Apple APNS لفتح مدخل Apple Push Certificates.
   - سجل الدخول باستخدام معرف Apple.

     > [!IMPORTANT]
     > استخدم معرف Apple للشركة المقترن بحساب بريد إلكتروني سيبقى مع مؤسستك حتى لو ترك المستخدم الذي يدير الحساب. احفظ هذا المعرف لأنك ستحتاج إلى استخدام المعرف نفسه عندما يكون الوقت قد حان لتجديد الشهادة.

   - حدد إنشاء شهادة واقبل شروط الاستخدام.
   - استعرض وصولا إلى طلب توقيع الشهادة الذي قمت بتنزيله إلى الكمبيوتر من Microsoft 365 وحددUpload.
   - قم بتنزيل شهادة APN التي تم إنشاؤها بواسطة Apple Push Certificate Portal إلى الكمبيوتر.

     > [!TIP]
     > إذا كنت تواجه مشكلة في تنزيل الشهادة، فقم بتحديث المستعرض.

7. ارجع إلى Microsoft 365 وحدد **"التالي**".

8. استعرض وصولا إلى شهادة APN التي قمت بتنزيلها من مدخل Apple Push Certificates.

9. حدد **إنهاء**.

### <a name="step-3-recommended-set-up-multi-factor-authentication"></a>الخطوة 3: (مستحسن) إعداد المصادقة متعددة العوامل

تساعد المصادقة متعددة العوامل على تأمين تسجيل الدخول إلى Microsoft 365 لتسجيل الأجهزة المحمولة عن طريق طلب نموذج ثان من المصادقة. يطلب من المستخدمين الإقرار بمكالمة هاتفية أو رسالة نصية أو إعلام تطبيق على أجهزتهم المحمولة بعد إدخال كلمة مرور حساب العمل بشكل صحيح. يمكنهم تسجيل أجهزتهم فقط بعد اكتمال هذا النموذج الثاني من المصادقة. بعد تسجيل أجهزة المستخدم في Basic Mobility and Security، يمكن للمستخدمين الوصول إلى موارد Microsoft 365 باستخدام حساب العمل الخاص بهم فقط.

لمعرفة كيفية تشغيل المصادقة متعددة العوامل في مدخل Azure AD، راجع [إعداد المصادقة متعددة العوامل](../security-and-compliance/set-up-multi-factor-authentication.md).

بعد إعداد المصادقة متعددة العوامل، عد إلى مركز توافق & الأمان وانتقل إلى **نهج جهاز** **إدارة** >  الأجهزة **لمنع** >  فقدان البيانات لإكمال الخطوة التالية.

### <a name="step-4-recommended-manage-device-security-policies"></a>الخطوة 4: (مستحسن) إدارة نهج أمان الجهاز

الخطوة التالية هي إنشاء نهج أمان الجهاز ونشرها للمساعدة في حماية بيانات المؤسسة Microsoft 365. على سبيل المثال، يمكنك المساعدة في منع فقدان البيانات إذا فقد المستخدم جهازه عن طريق إنشاء نهج لتأمين الأجهزة بعد خمس دقائق من عدم النشاط ومسح الأجهزة بعد ثلاث حالات فشل في تسجيل الدخول.

1. سجل الدخول إلى Microsoft 365 باستخدام حساب المسؤول العام.

2. حدد [تنشيط إدارة الجهاز الجوال](https://admin.microsoft.com/EAdmin/Device/IntuneInventory.aspx). إذا تم تنشيط الخدمة، فبدلا من خطوات التنشيط، سترى ارتباطا [لإدارة الأجهزة](https://admin.microsoft.com/adminportal/home#/MifoDevices) .

3. انتقل إلى **نهج الجهاز**.

   :::image type="content" source="../../media/basic-mobility-security/basic-mobility-microsoft-purview.png" alt-text="إعدادات نهج الأمان والتنقل الأساسية.":::

4. إنشاء نهج أمان الجهاز المناسبة لمؤسستك ونشرها باتباع الخطوات الواردة في [إنشاء نهج أمان الجهاز في Basic Mobility and Security](create-device-security-policies.md).

> [!TIP]
>
> - عند إنشاء نهج جديد، قد تحتاج إلى تعيين النهج للسماح بالوصول والإبلاغ عن انتهاك النهج عندما لا يكون جهاز المستخدم متوافقا مع النهج. يسمح لك هذا بمعرفة عدد الأجهزة المحمولة المتأثرة بالنهج دون حظر الوصول إلى Microsoft 365.
>
> - قبل نشر نهج جديد لجميع الأشخاص في مؤسستك، نوصي باختباره على الأجهزة التي يستخدمها عدد قليل من المستخدمين.
>
> - أيضا، قبل نشر النهج، دع مؤسستك تعرف التأثيرات المحتملة لتسجيل جهاز في Basic Mobility and Security. استنادا إلى كيفية إعداد النهج، يمكن حظر الأجهزة التي لا تتوافق مع النهج (الأجهزة غير المتوافقة) من الوصول إلى Microsoft 365. قد تحتوي الأجهزة غير المتوافقة أيضا على تطبيقات مثبتة وصور ومعلومات شخصية أخرى يمكن حذفها، على جهاز مسجل، إذا تم مسح الجهاز. لمزيد من المعلومات، راجع [مسح جهاز محمول في Basic Mobility and Security](wipe-mobile-device.md).

## <a name="make-sure-users-enroll-their-devices"></a>تأكد من تسجيل المستخدمين أجهزتهم

بعد إنشاء نهج إدارة أجهزة المحمول وتوزيعه، يتلقى كل مستخدم مرخص Microsoft 365 في مؤسستك يطبقه نهج الجهاز رسالة تسجيل في المرة التالية التي يسجل فيها دخوله إلى Microsoft 365 من جهازه المحمول. يجب عليهم إكمال خطوات التسجيل والتنشيط قبل أن يتمكنوا من الوصول إلى Microsoft 365 البريد الإلكتروني والمستندات. لمزيد من المعلومات، راجع [تسجيل جهازك المحمول باستخدام Basic Mobility and Security](enroll-your-mobile-device.md).

> [!IMPORTANT]
> إذا لم تكن اللغة المفضلة للمستخدم مدعومة من قبل عملية التسجيل، فقد يتلقى المستخدمون إعلام التسجيل والخطوات على أجهزتهم المحمولة بلغة أخرى. لا يتم حاليا دعم جميع اللغات المعتمدة في Microsoft 365 لعملية التسجيل على الأجهزة المحمولة.

يطلب من المستخدمين الذين لديهم أجهزة Android أو iOS تثبيت تطبيق Company Portal كجزء من عملية التسجيل.

## <a name="related-content"></a>المحتويات ذات الصلة

[قدرات Basic Mobility and Security](capabilities.md) (article)\
[إنشاء نهج أمان الجهاز في Basic Mobility and Security](create-device-security-policies.md) (مقالة)
