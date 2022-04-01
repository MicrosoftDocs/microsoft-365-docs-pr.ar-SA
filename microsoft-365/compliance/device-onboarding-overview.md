---
title: عرض Windows 10 أو Windows 11 الأجهزة في Microsoft 365 عامة
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
description: أجهزة Windows 10 Windows 11 في Microsoft 365
ms.openlocfilehash: ea1038554349b6c035c52bd3d3429d71d7d866bc
ms.sourcegitcommit: 9d563faeaa50b59b0b468dbb373d886e5270f58e
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/24/2022
ms.locfileid: "64387122"
---
# <a name="onboard-windows-10-and-windows-11-devices-into-microsoft-365-overview"></a>عرض Windows 10 الأجهزة Windows 11 في Microsoft 365 عامة

**ينطبق على:**

- [منع فقدان بيانات نقطة النهاية (DLP)](./endpoint-dlp-learn-about.md)
- [إدارة مخاطر Insider](insider-risk-management.md#learn-about-insider-risk-management-in-microsoft-365)

يتطلب منع فقدان بيانات نقطة النهاية (DLP) وإدارة مخاطر insider أن Windows 10 Windows و Windows 11 أجهزة في الخدمة بحيث يمكنهم إرسال بيانات المراقبة إلى الخدمات.
 
تسمح لك نقطة النهاية DLP بمراقبة أجهزة Windows 10 أو Windows 11 والكشف عن وقت استخدام العناصر الحساسة ومشاركتها. يوفر لك ذلك إمكانية الرؤية والتحكم التي تحتاج إليها لضمان استخدامها وحمايتها بشكل صحيح، وللمساعدة على منع السلوك الخطر الذي قد يؤدي إلى اختراقها. لمزيد من المعلومات حول كل عروض DLP من Microsoft، راجع [التعرف على منع فقدان البيانات](dlp-learn-about-dlp.md). لمعرفة المزيد حول نقطة النهاية DLP، راجع [التعرف على منع فقدان بيانات نقطة النهاية](endpoint-dlp-learn-about.md).

تستخدم إدارة مخاطر Insider الاتساع الكامل للخدمة ومؤشرات 3 من جهة خارجية لمساعدتك على تحديد نشاط المستخدم الخطر وفرزه والعمل عليه بسرعة. باستخدام السجلات من Microsoft 365 و Microsoft Graph، تسمح لك إدارة مخاطر insider بتحديد سياسات معينة لتحديد مؤشرات المخاطر واتخاذ إجراء للحد من هذه المخاطر. لمزيد من المعلومات، راجع [التعرف على إدارة مخاطر insider في Microsoft 365](insider-risk-management.md#learn-about-insider-risk-management-in-microsoft-365).

يتم مشاركة تشغيل الجهاز عبر Microsoft 365 Microsoft Defender لنقطة النهاية (MDE). إذا قمت بالفعل بضم الأجهزة إلى MDE، ستظهر في قائمة الأجهزة المدارة ولا يلزم اتخاذ أي خطوات إضافية لضم هذه الأجهزة المحددة. كما أن أجهزة التكهين في مركز التوافق تعمل أيضا على اجهزتها في MDE.

## <a name="before-you-begin"></a>قبل البدء

### <a name="skusubscriptions-licensing"></a>ترخيص SKU/الاشتراكات

تحقق من متطلبات الترخيص [هنا](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#information-protection-data-loss-prevention-for-exchange-online-sharepoint-online-and-onedrive-for-business).

### <a name="permissions"></a>الأذونات

لتمكين إدارة الأجهزة، يجب أن يكون الحساب الذي تستخدمه عضوا في أي من هذه الأدوار:

- المسؤول العام
- مسؤول الأمان
- مسؤول التوافق

إذا كنت تريد استخدام حساب مخصص لعرض إعدادات إدارة الأجهزة، فيجب أن يكون في أحد الأدوار التالية:

- المسؤول العام
- مسؤول التوافق
- مسؤول بيانات التوافق
- القارئ العام

إذا كنت تريد استخدام حساب مخصص للوصول إلى صفحة الإستخدام/إيقاف التشغيل، فيجب أن يكون في أحد الأدوار التالية:

- المسؤول العام
- مسؤول التوافق

إذا كنت تريد استخدام حساب مخصص ل تشغيل/إيقاف تشغيل مراقبة الجهاز، فيجب أن يكون في أحد هذه الأدوار:

- المسؤول العام
- مسؤول التوافق

### <a name="prepare-your-windows-devices"></a>تحضير الأجهزة Windows الخاصة بك

تأكد من أن Windows التي تحتاج إلى ا متنها تلبي هذه المتطلبات.

1. يجب تشغيل Windows 10 x64 1809 أو أي وقت لاحق أو Windows 11.

2. إصدار عميل مكافحة البرامج الضارة هو 4.18.2110 أو إصدار أحدث. تحقق من الإصدار الحالي عن طريق أمن Windows التطبيق، وحدد الإعدادات، ثم حدد حول. يتم سرد رقم الإصدار ضمن إصدار عميل مكافحة البرامج الضارة. قم بتحديث إصدار عميل مكافحة البرامج الضارة الأخير Windows Update KB4052623.

   > [!NOTE]
   > لا أمن Windows أي من المكونات النشطة، ولكن يجب تمكين جهاز عرض الحماية والسلوك في [](/windows/security/threat-protection/microsoft-defender-antivirus/configure-real-time-protection-microsoft-defender-antivirus)الوقت الحقيقي.

3. يتم تثبيت Windows تحديثات Windows 10 للأجهزة التي سيتم مراقبتها.

   > [!NOTE]
   > هذه التحديثات ليست من المتطلبات الأساسية لتركيب جهاز، ولكنها تحتوي على تصحيحات ل المشاكل الهامة وبالتالي يجب تثبيتها قبل استخدام المنتج.
   >
    > - بالنسبة Windows 10 1809 - KB4559003، KB4577069، KB4580390
    > - بالنسبة Windows 10 1903 أو 1909 - KB4559004، KB4577062، KB4580386
    > - بالنسبة Windows 10 2004 - KB4568831، KB4577063

4. يجب أن تكون جميع الأجهزة واحدة من هذه الأجهزة:

   - [تم انضمام Microsoft Azure Active Directory (Azure AD)](/azure/active-directory/devices/concept-azure-ad-join)
   - [مُسجل عبر hybrid Azure AD](/azure/active-directory/devices/concept-azure-ad-join-hybrid)
   - [AAD (دليل Azure النشط) مسجل](/azure/active-directory/user-help/user-help-register-device-on-network)

5. يتم تثبيت إصدار Microsoft Office محدث ومحدث. للحصول على أفضل حماية وتجربة مستخدم، تأكد Microsoft 365 Apps تثبيت الإصدار 16.0.14701.0 أو الإصدار الأحدث.
> [!NOTE]
   > - إذا كنت تقوم بتشغيل Office 365 - يجب 4577063 KB.
   > - إذا كنت على التحديث الشهري للمؤسسة Microsoft 365 Apps الإصدارات 2004-2008، يجب التحديث إلى الإصدار 2009 أو الإصدارات الأحدث. راجع [تحديث محفوظات Microsoft 365 Apps (مدرجة حسب التاريخ)](/officeupdates/update-history-microsoft365-apps-by-date) للإصدارات الحالية. لمعرفة المزيد حول المشكلة المعروفة، راجع Office مجموعة ملاحظات الإصدارات الخاصة [بإطلاقات القناة الحالية في 2020](/officeupdates/current-channel#version-2010-october-27).

6. إذا كانت لديك نقاط نهاية تستخدم وكيل جهاز للاتصال بالإنترنت، فاتبع الإجراءات في تكوين إعدادات اتصال وكيل الجهاز [والإنترنت](device-onboarding-configure-proxy.md#configure-device-proxy-and-internet-connection-settings-for-information-protection) حماية البيانات.

## <a name="onboarding-windows-10-or-windows-11-devices"></a>أجهزة Windows 10 أو أجهزة Windows 11

يجب تمكين مراقبة الجهاز وإلوحاء نقاط النهاية قبل أن تتمكن من مراقبة العناصر الحساسة على جهاز وحمايتها. يتم كلا هذين الإجراءات في مدخل Microsoft 365 التوافق.

عندما تريد أن تقوم بتركب الأجهزة التي لم يتم تشغيلها بعد، يمكنك تنزيل البرنامج النصي المناسب ونشره على تلك الأجهزة. اتبع إجراءات تشغيل الجهاز أدناه.

إذا كان لديك بالفعل أجهزة مجهزه [Microsoft Defender لنقطة النهاية، ستظهر](/windows/security/threat-protection/) بالفعل في قائمة الأجهزة المدارة.

في سيناريو النشر هذا، سوف تقوم Windows 10 أو Windows 11 الأجهزة التي لم يتم اجهزتك بعد.

1. افتح [مركز توافق Microsoft](https://compliance.microsoft.com). اختر **الإعدادات** >  **مراقبة الأجهزة القابلة للانهاء**.

   > [!NOTE]
   > على الرغم من أن تمكين تشغيل الجهاز يستغرق عادة حوالي 60 ثانية، يرجى السماح بما يصل إلى 30 دقيقة قبل التفاعل مع دعم Microsoft.

2. افتح صفحة إعدادات مركز التوافق واختر **تشغيل Windows الأجهزة**.

3. اختر **إدارة الأجهزة** لفتح **قائمة** الأجهزة. 

> [!NOTE]
> إذا قمت مسبقا بنشر Microsoft Defender لنقطة النهاية، سيتم إدراج جميع الأجهزة التي تم إدراجها أثناء هذه العملية في **قائمة** الأجهزة. لن تحتاج إلى ا متنها مرة أخرى.

4. اختر **"التكهين** " لبدء عملية التكهين.

5. اختر الطريقة التي تريد نشرها على هذه الأجهزة الإضافية من قائمة **أسلوب** النشر، ثم **قم بتنزيل الحزمة**.

6. اختر الإجراء المناسب الذي يجب اتباعه من الجدول أدناه:

الموضوع | الوصف
:---|:---
[أجهزة Windows 10 أو 11 جهازا تستخدم نهج المجموعة](device-onboarding-gp.md) | استخدم نهج المجموعة لنشر حزمة التكوين على الأجهزة.
[أجهزة Windows 10 أو 11 جهازا تستخدم Microsoft Endpoint Configuration Manager](device-onboarding-sccm.md) | يمكنك استخدام Microsoft Endpoint Configuration Manager (الفرع الحالي) الإصدار 1606 أو Microsoft Endpoint Configuration Manager (الفرع الحالي) الإصدار 1602 أو إصدار سابق لنشر حزمة التكوين على الأجهزة.
[أجهزة Windows 10 أو 11 جهازا باستخدام إدارة الجهاز المحمول](device-onboarding-mdm.md) | استخدم أدوات إدارة الجهاز أو Microsoft Intune المحمول لنشر حزمة التكوين على الجهاز.
[أجهزة Windows 10 أو 11 جهازا باستخدام برنامج نصي محلي](device-onboarding-script.md) | تعرف على كيفية استخدام البرنامج النصي المحلي لنشر حزمة التكوين على نقاط النهاية.
[أجهزة البنية الأساسية لسطح المكتب الظاهري (VDI) غير الثابتة](device-onboarding-vdi.md) | تعرف على كيفية استخدام حزمة التكوين لتكوين أجهزة VDI.

بمجرد أن يتم ضم جهاز، يجب أن يكون مرئيا في قائمة الأجهزة وأن يبدأ أيضا في الإبلاغ عن سجلات نشاط التدقيق إلى "مستكشف النشاط".

### <a name="viewing-endpoint-dlp-alerts-in-dlp-alerts-management-dashboard"></a>عرض تنبيهات DLP لنقطة النهاية في لوحة معلومات إدارة تنبيهات DLP

1. افتح صفحة منع فقدان <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">البيانات في مركز التوافق في Microsoft 365</a> واختر تنبيهات.

2. راجع الإجراءات في كيفية تكوين التنبيهات وعرضها لنهج [DLP](dlp-configure-view-alerts-policies.md) لعرض التنبيهات لنهج DLP في نقطة النهاية.

### <a name="viewing-endpoint-dlp-data-in-activity-explorer"></a>عرض بيانات DLP لنقطة النهاية في مستكشف النشاط

1. افتح صفحة [تصنيف البيانات](https://compliance.microsoft.com/dataclassification?viewid=overview) لمجالك في Microsoft 365 التوافق واختر مستكشف النشاط.

2. راجع الإجراءات في بدء استخدام "[](data-classification-activity-explorer.md)مستكشف النشاط" للوصول إلى كل البيانات الخاصة بأجهزتك في نقطة النهاية وتصفيتها.

   > [!div class="mx-imgBorder"]
   > ![عامل تصفية مستكشف النشاط للأجهزة التي تعمل بنقطة النهاية.](../media/endpoint-dlp-4-getting-started-activity-explorer.png)


## <a name="see-also"></a>راجع أيضًا

- [تعرف على إدارة مخاطر insider في Microsoft 365](insider-risk-management.md#learn-about-insider-risk-management-in-microsoft-365)
- [التعرف على منع فقدان بيانات نقطة النهاية](endpoint-dlp-learn-about.md)
- [استخدام منع فقدان البيانات في نقطة النهاية](endpoint-dlp-using.md)
- [التعرف على منع فقدان البيانات](dlp-learn-about-dlp.md)
- [إنشاء نهج DLP واختباره وضبطه](create-test-tune-dlp-policy.md)
- [بدء استخدام "مستكشف النشاط"](data-classification-activity-explorer.md)
- [Microsoft Defender لنقطة النهاية](/windows/security/threat-protection/)
- [أدوات وأساليب ال متنبها Windows 10 الأجهزة](/windows/security/threat-protection/microsoft-defender-atp/configure-endpoints)
- [Microsoft 365 الاشتراك](https://www.microsoft.com/microsoft-365/compare-microsoft-365-enterprise-plans?rtc=1)
- [الأجهزة المنضمة إلى Azure AD](/azure/active-directory/devices/concept-azure-ad-join)
- [قم بتنزيل الملف Microsoft Edge استنادا إلى Chromium](https://support.microsoft.com/help/4501095/download-the-new-microsoft-edge-based-on-chromium)
