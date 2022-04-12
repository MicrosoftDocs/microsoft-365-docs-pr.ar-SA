---
title: إمكانات التنقل والأمان الأساسيين
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
description: يمكن أن يساعدك التنقل الأساسي والأمان على تأمين أجهزتك المحمولة وإدارتها.
ms.openlocfilehash: 78cfa4582aa2e25a3b47a12d2e067082e8b41d07
ms.sourcegitcommit: ac0ae5c2888e2b323e36bad041a4abef196c9c96
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/12/2022
ms.locfileid: "64781216"
---
# <a name="capabilities-of-basic-mobility-and-security"></a>إمكانات التنقل والأمان الأساسيين

يمكن أن يساعدك Basic Mobility and Security على تأمين الأجهزة المحمولة وإدارتها مثل أجهزة iPhone وiPad وAndroids والهواتف Windows المستخدمة من قبل مستخدمي Microsoft 365 المرخصين في مؤسستك. يمكنك إنشاء نهج إدارة أجهزة المحمول مع إعدادات يمكن أن تساعد في التحكم في الوصول إلى البريد الإلكتروني Microsoft 365 الخاص بمؤسستك والمستندات للأجهزة المحمولة والتطبيقات المدعومة. في حالة فقدان جهاز أو سرقته، يمكنك مسح الجهاز عن بعد لإزالة معلومات المؤسسة الحساسة.

## <a name="supported-operating-systems"></a>أنظمة التشغيل المدعومة

اتبع دليل أنظمة التشغيل Microsoft Intune للحد الأدنى من أنظمة التشغيل المدعومة للأجهزة بواسطة Basic Mobility and Security. لمزيد من المعلومات، راجع [أنظمة التشغيل المدعومة من Intune](/mem/intune/fundamentals/supported-devices-browsers).

يمكنك استخدام Basic Mobility and Security لتأمين الأجهزة التالية وإدارتها.

- دائره الرقابه الداخليه
- Android (بما في ذلك Samsung Knox)<sup>1</sup>
- Windows <sup>2، 3</sup>

<sup>1</sup> بعد يونيو 2020، لا يمكن لإصدارات Android الأحدث من 9 إدارة إعدادات كلمة المرور إلا على أجهزة Samsung Knox.

<sup>2</sup> يقتصر التحكم بالوصول لأجهزة Windows 8.1 RT على Exchange ActiveSync.

<sup>3</sup> يتطلب التحكم بالوصول Windows 10 اشتراكا يتضمن Premium Azure AD ويجب أن ينضم الجهاز إلى Azure Active Directory.

> [!NOTE]
> تستمر الأجهزة المسجلة بالفعل في إصدارات نظام التشغيل السابقة في العمل على الرغم من أن القدرات قد تتغير دون إشعار.

إذا كان الأشخاص في مؤسستك يستخدمون أجهزة محمولة غير معتمدة من قبل Basic Mobility and Security، فقد ترغب في حظر وصول تطبيق Exchange ActiveSync إلى البريد الإلكتروني Microsoft 365 لتلك الأجهزة، للمساعدة في جعل بيانات مؤسستك أكثر أمانا. للحصول على خطوات لحظر Exchange ActiveSync، راجع [إدارة إعدادات الوصول إلى الجهاز في Basic Mobility and Security](manage-device-access-settings.md).

## <a name="access-control-for-microsoft-365-email-and-documents"></a>التحكم بالوصول Microsoft 365 البريد الإلكتروني والمستندات

تطالب التطبيقات المدعومة للأنواع المختلفة من الأجهزة المحمولة في الجدول التالي المستخدمين بالتسجيل في Basic Mobility and Security حيث يوجد نهج جديد لإدارة الأجهزة المحمولة ينطبق على جهاز المستخدم ولم يقم المستخدم بتسجيل الجهاز مسبقا. إذا لم يمتثل جهاز المستخدم لنهج ما، اعتمادا على كيفية إعداد النهج، فقد يتم حظر المستخدم من الوصول إلى موارد Microsoft 365 في هذه التطبيقات، أو قد يكون لديه حق الوصول ولكن Microsoft 365 يبلغ عن انتهاك النهج.

|المنتج|دائره الرقابه الداخليه|الروبوت|
|---|---|---|
|**تتضمن Exchange** Exchange ActiveSync البريد الإلكتروني المضمن وتطبيقات الجهات الخارجية، مثل TouchDown، التي تستخدم Exchange ActiveSync الإصدار 14.1 أو الإصدارات الأحدث.|البريد|البريد الالكتروني|
|**Office** **OneDrive for Business**|Outlook </br>OneDrive </br>Word </br>Excel </br>PowerPoint|**على الهواتف وأجهزة الكمبيوتر اللوحي**:<br/>Outlook <br/> OneDrive <br/> Word <br/> Excel <br/> PowerPoint <br/> **على الهواتف فقط:** <br/> Office Mobile|

> [!NOTE]
>
> - يتضمن دعم iOS 10.0 والإصدارات الأحدث أجهزة iPhone iPad.
> - إدارة أجهزة BlackBerry OS غير مدعومة من قبل Basic Security and Mobility. استخدم خدمات BlackBerry Business Cloud Services من BlackBerry لإدارة أجهزة BlackBerry OS. يتم دعم أجهزة Blackberry التي تعمل بنظام التشغيل Android كأجهزة Android قياسية
> - لن تتم مطالبة المستخدمين بالتسجيل ولن يتم حظرهم أو الإبلاغ عن انتهاك النهج إذا استخدموا مستعرض الجوال للوصول إلى مواقع Microsoft 365 SharePoint أو المستندات في Office Online أو البريد الإلكتروني في Outlook Web App.

يوضح الرسم التخطيطي التالي ما يحدث عندما يقوم مستخدم مزود بجهاز جديد بتسجيل الدخول إلى تطبيق يدعم التحكم في الوصول باستخدام Basic Mobility and Security. يتم حظر المستخدم من الوصول إلى موارد Microsoft 365 في التطبيق حتى يسجل جهازه.

:::image type="content" source="../../media/basic-mobility-security/bms-1-access-control.png" alt-text="التحكم الأساسي في التنقل والوصول إلى الأمان.":::

> [!NOTE]
> ستتجاوز النهج وقواعد الوصول التي تم إنشاؤها في Basic Mobility and Security for Microsoft 365 Business Standard Exchange ActiveSync نهج علبة بريد الأجهزة المحمولة وقواعد الوصول إلى الأجهزة التي تم إنشاؤها في مركز إدارة Exchange. بعد تسجيل جهاز في Basic Mobility and Security for Microsoft 365 Business Standard، سيتم تجاهل أي نهج Exchange ActiveSync لعل بريد الجهاز المحمول أو قاعدة الوصول إلى الجهاز المطبقة على الجهاز. لمعرفة المزيد حول Exchange ActiveSync، راجع [Exchange ActiveSync في Exchange Online](/exchange/clients-and-mobile-in-exchange-online/exchange-activesync/exchange-activesync).

## <a name="policy-settings-for-mobile-devices"></a>إعدادات النهج للأجهزة المحمولة

إذا قمت بإنشاء نهج لحظر الوصول مع تشغيل إعدادات معينة، يتم حظر المستخدمين من الوصول إلى موارد Microsoft 365 عند استخدام تطبيق معتمد مدرج في [عنصر تحكم Access للبريد الإلكتروني والمستندات Microsoft 365](capabilities.md).

الإعدادات التي يمكن أن تمنع المستخدمين من الوصول إلى موارد Microsoft 365 موجودة في هذه الأقسام:

- الأمان

- التشفير

- تم كسر عطل في الكبس

- ملف تعريف البريد الإلكتروني المدار

على سبيل المثال، يوضح الرسم التخطيطي التالي ما يحدث عندما لا يكون المستخدم الذي يستخدم جهازا مسجلا متوافقا مع إعداد أمان في نهج إدارة الأجهزة المحمولة الذي ينطبق على جهازه. يسجل المستخدم الدخول إلى تطبيق يدعم التحكم بالوصول باستخدام Basic Mobility and Security. يتم حظرهم من الوصول إلى موارد Microsoft 365 في التطبيق حتى يتوافق جهازهم مع إعداد الأمان.

:::image type="content" source="../../media/basic-mobility-security/bms-2-device-not-compliant.png" alt-text="رسالة التوافق الأساسية للتنقل والأمان.":::

تسرد الأقسام التالية إعدادات النهج التي يمكنك استخدامها للمساعدة في تأمين الأجهزة المحمولة التي تتصل بموارد المؤسسة Microsoft 365 وإدارتها.

## <a name="security-settings"></a>إعدادات الأمان

|إعداد الاسم|دائره الرقابه الداخليه|الروبوت|Samsung Knox|
|---|---|---|---|
|طلب كلمة مرور|نعم|نعم|نعم|
|منع كلمة المرور البسيطة|نعم|لا|لا|
|طلب كلمة مرور أبجدية رقمية|نعم|لا|لا|
|الحد الأدنى لطول كلمة المرور|نعم|نعم|نعم|
|عدد حالات فشل تسجيل الدخول قبل مسح الجهاز|نعم|نعم|نعم|
|دقائق من عدم النشاط قبل تأمين الجهاز|نعم|نعم|نعم|
|انتهاء صلاحية كلمة المرور (أيام)|نعم|نعم|نعم|
|تذكر محفوظات كلمة المرور ومنع إعادة الاستخدام|نعم|نعم|نعم|

## <a name="encryption-settings"></a>إعدادات التشفير

|إعداد الاسم|دائره الرقابه الداخليه|الروبوت|Samsung Knox|
|---|---|---|---|
|طلب تشفير البيانات على <sup>الأجهزة1</sup>|لا|نعم|نعم|

<sup>1</sup> باستخدام Samsung Knox، يمكنك أيضا طلب التشفير على بطاقات التخزين.

## <a name="jail-broken-setting"></a>إعداد كسر في الكسور

|إعداد الاسم|دائره الرقابه الداخليه|الروبوت|Samsung Knox|
|---|---|---|---|
|لا يمكن أن يكون الجهاز معطلا أو مأصلا|نعم|نعم|نعم|

## <a name="managed-email-profile-option"></a>خيار ملف تعريف البريد الإلكتروني المدار

يمكن أن يمنع الخيار التالي المستخدمين من الوصول إلى بريدهم الإلكتروني Microsoft 365 إذا كانوا يستخدمون ملف تعريف بريد إلكتروني تم إنشاؤه يدويا. يجب على المستخدمين على أجهزة iOS حذف ملف تعريف البريد الإلكتروني الذي تم إنشاؤه يدويا قبل أن يتمكنوا من الوصول إلى بريدهم الإلكتروني. بعد حذف ملف التعريف، يتم إنشاء ملف تعريف جديد تلقائيا على الجهاز. للحصول على إرشادات حول كيفية توافق المستخدمين النهائيين، راجع [العثور على حساب بريد إلكتروني موجود](/intune-user-help/existing-company-email-account-found).

|إعداد الاسم|دائره الرقابه الداخليه|الروبوت|Samsung Knox|
|---|---|---|---|
|تتم إدارة ملف تعريف البريد الإلكتروني|نعم|لا|لا|

## <a name="cloud-settings"></a>إعدادات السحابة

|إعداد الاسم|دائره الرقابه الداخليه|الروبوت|Samsung Knox|
|---|---|---|---|
|طلب نسخة احتياطية مشفرة|نعم|لا|لا|
|حظر النسخ الاحتياطي للسحابة|نعم|لا|لا|
|حظر مزامنة المستند|نعم|لا|لا|
|حظر مزامنة الصور|نعم|لا|لا|
|السماح بالنسخ الاحتياطي ل Google|N/A|لا|نعم|
|السماح بالمزامنة التلقائية لحساب Google|N/A|لا|نعم|

## <a name="system-settings"></a>إعدادات النظام

|إعداد الاسم|دائره الرقابه الداخليه|الروبوت|Samsung Knox|
|---|---|---|---|
|حظر التقاط الشاشة|نعم|لا|نعم|
|حظر إرسال البيانات التشخيصية من الجهاز|نعم|لا|نعم|

## <a name="application-settings"></a>إعدادات التطبيق

|إعداد الاسم|دائره الرقابه الداخليه|الروبوت|Samsung Knox|
|---|---|---|---|
|حظر مؤتمرات الفيديو على الجهاز|نعم|لا|لا|
|حظر الوصول إلى متجر التطبيقات|نعم|لا|نعم|
|طلب كلمة مرور عند الوصول إلى متجر التطبيقات|لا|نعم|نعم|

## <a name="device-capabilities-settings"></a>إعدادات قدرات الجهاز

|إعداد الاسم|دائره الرقابه الداخليه|الروبوت|Samsung Knox|
|---|---|---|---|
|حظر الاتصال بالتخزين القابل للإزالة|نعم|نعم|لا|
|حظر اتصال Bluetooth|نعم|نعم|لا|

## <a name="additional-settings"></a>إعدادات إضافية

يمكنك تعيين إعدادات النهج الإضافية التالية باستخدام Security & Compliance Center PowerShell cmdlets. لمزيد من المعلومات، راجع [Security & Compliance Center PowerShell](/powershell/exchange/scc-powershell).

|إعداد الاسم|دائره الرقابه الداخليه|الروبوت|
|---|---|---|
|الكاميرا القابلة للكاميرا|نعم|نعم|
|RegionRatings|نعم|لا|
|MoviesRatings|نعم|لا|
|TVShowsRating|نعم|لا|
|AppsRatings|نعم|لا|
|AllowVoiceDialing|نعم|لا|
|AllowVoiceAssistant|نعم|لا|
|AllowAssistantWhileLocked|نعم|لا|
|AllowPassbookWhileLocked|نعم|لا|
|MaxPasswordGracePeriod|نعم|لا|
|دقة كلمة المرور|لا|نعم|
|SystemSecurityTLS|نعم|لا|
|WLANEnabled|لا|لا|

## <a name="settings-supported-by-windows"></a>الإعدادات مدعوم من قبل Windows

يمكنك إدارة أجهزة Windows 10 عن طريق تسجيلها كأجهزة محمولة. بعد نشر نهج قابل للتطبيق، سيطلب من المستخدمين الذين لديهم أجهزة Windows 10 التسجيل في Basic Mobility and Security في المرة الأولى التي يستخدمون فيها تطبيق البريد الإلكتروني المضمن للوصول إلى بريدهم الإلكتروني Microsoft 365 (يتطلب اشتراك Azure AD المتميز).

الإعدادات التالية معتمدة للأجهزة Windows 10 المسجلة كأجهزة محمولة. لن يمنع هذا الإعداد المستخدمين من الوصول إلى موارد Microsoft 365.

### <a name="security-settings"></a>إعدادات الأمان

- طلب كلمة مرور أبجدية رقمية

- الحد الأدنى لطول كلمة المرور

- عدد حالات فشل تسجيل الدخول قبل مسح الجهاز

- دقائق من عدم النشاط قبل تأمين الجهاز

- انتهاء صلاحية كلمة المرور (أيام)

- تذكر محفوظات كلمة المرور ومنع إعادة الاستخدام

> [!NOTE]
> تتحكم الإعدادات التالية التي تنظم كلمات المرور في حسابات Windows المحلية فقط. لا تتأثر Windows الحسابات المقدمة من خلال الانضمام إلى مجال أو Azure Active Directory بهذه الإعدادات.

### <a name="system-settings"></a>إعدادات النظام

حظر إرسال البيانات التشخيصية من الجهاز.

### <a name="additional-settings"></a>إعدادات إضافية

يمكنك تعيين إعدادات النهج الإضافية هذه باستخدام PowerShell cmdlets:

- AllowConvenienceLogon

- UserAccountControlStatus

- FirewallStatus

- التحديث التلقائي لStatus

- AntiVirusStatus

- AntiVirusSignatureStatus

- SmartScreenEnabled

- WorkFoldersSyncUrl

## <a name="remotely-wipe-a-mobile-device"></a>مسح جهاز محمول عن بعد

في حالة فقدان جهاز أو سرقته، يمكنك إزالة البيانات التنظيمية الحساسة والمساعدة في منع الوصول إلى موارد المؤسسة Microsoft 365 عن طريق إجراء مسح من مركز التوافق & الأمان > **إدارة** **منع** >  فقدان البيانات. يمكنك إجراء مسح انتقائي لإزالة بيانات المؤسسة فقط أو مسح كامل لحذف كافة المعلومات من جهاز واستعادتها إلى إعدادات المصنع الخاصة به.

لمزيد من المعلومات، راجع [مسح جهاز محمول في Basic Mobility and Security](wipe-mobile-device.md).

## <a name="related-content"></a>محتوى ذي صلة

[نظرة عامة على Basic Mobility and Security for Microsoft 365](overview.md) (article)\
[إنشاء نهج أمان الجهاز في Basic Mobility and Security](create-device-security-policies.md) (مقالة)
