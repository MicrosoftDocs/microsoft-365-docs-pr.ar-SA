---
title: العمل الأساسي لتطبيق سياسات الوصول إلى الهوية والجهاز - Microsoft 365 للمؤسسات | Microsoft Docs
description: تصف هذه المقالة المتطلبات الأساسية التي تحتاج إلى تلبيتها لاستخدام ثقة معدومة الشخصية ونهج الوصول إلى الجهاز وتكويناتها.
ms.author: dansimp
author: dansimp
manager: dansimp
ms.prod: m365-security
ms.topic: article
audience: Admin
f1.keywords:
- NOCSH
ms.reviewer: martincoetzer
ms.custom:
- it-pro
- goldenconfig
ms.collection:
- M365-identity-device-management
- M365-security-compliance
- m365solution-identitydevice
- m365solution-scenario
ms.technology: mdo
ms.openlocfilehash: 8123b3602569ec1effcbf79cb12d242ab19d960e
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/25/2022
ms.locfileid: "64472342"
---
# <a name="prerequisite-work-for-implementing-zero-trust-identity-and-device-access-policies"></a>عمل المتطلبات الأساسية لتطبيق ثقة معدومة الهوية ونهج الوصول إلى الجهاز

تصف هذه المقالة المتطلبات الأساسية التي يجب على المسؤولين تلبيتها لاستخدام ثقة معدومة الهوية ونهج الوصول إلى الجهاز الموصى بها، واستخدام الوصول الشرطي. كما يناقش الإعدادات الافتراضية الموصى بها لتكوين الأنظمة الأساسية للعميل للحصول على أفضل تجربة تسجيل الدخول الفردي (SSO).

## <a name="prerequisites"></a>المتطلبات الأساسية

قبل استخدام ثقة معدومة الهوية ونهج الوصول إلى الجهاز الموصى بها، تحتاج مؤسستك إلى تلبية المتطلبات الأساسية. تختلف المتطلبات لنماذج الهوية والمصادقة المختلفة المدرجة:

- السحابة فقط
- مختلط مع مصادقة مزامنة كلمة المرور (PHS)
- مختلط مع مصادقة تمريرية (PTA)
- المتحدة

يستعرض الجدول التالي تفاصيل ميزات المتطلبات الأساسية وتكوينها التي تنطبق على كل نماذج الهوية، باستثناء الحالات التي تم ذكرها.

|تكوين|الاستثناءات|الترخيص|
|---|:---:|---|
|[تكوين PHS](/azure/active-directory/hybrid/how-to-connect-password-hash-synchronization).  يجب تمكين ذلك للكشف عن بيانات الاعتماد التي تم تسريبها والعمل عليها للوصول الشرطي المستند إلى المخاطر. **ملاحظة:** هذا مطلوب بغض النظر عما إذا كانت مؤسستك تستخدم المصادقة الخارجية أم لا.|السحابة فقط|Microsoft 365 E3 أو E5|
|[قم بتمكين تسجيل الدخول المفرد السلس](/azure/active-directory/connect/active-directory-aadconnect-sso) إلى تسجيل الدخول تلقائيا للمستخدمين عند وجودهم على أجهزة المؤسسة المتصلة بشبكة مؤسستك.|السحابة فقط والمتّحجرة|Microsoft 365 E3 أو E5|
|[تكوين المواقع المسماة](/azure/active-directory/reports-monitoring/quickstart-configure-named-locations). تجمع Azure AD Identity Protection كل بيانات جلسة العمل المتوفرة وتحللها لإنشاء درجة مخاطر. نوصي بتحديد نطاقات IP العامة في مؤسستك للشبكة في تكوين المواقع المسماة Azure AD. يتم منح حركة المرور القادمة من هذه النطاقات درجة مخاطر أقل، ويتم منح حركة المرور من خارج بيئة المؤسسة درجة مخاطر أعلى.||Microsoft 365 E3 أو E5|
|[قم بتسجيل جميع المستخدمين لإعادة تعيين كلمة المرور للخدمة الذاتية (SSPR) والمصادقة متعددة العوامل (MFA).](/azure/active-directory/authentication/concept-registration-mfa-sspr-converged) نوصي بتسجيل المستخدمين ل Azure AD متعددة العوامل المصادقة قبل الوقت المحدد. تستخدم Azure AD Identity Protection مصادقة Azure AD متعددة العوامل لتنفيذ التحقق الإضافي من الأمان. بالإضافة إلى ذلك، للحصول على أفضل تجربة تسجيل الدخول، نوصي [المستخدمين بتثبيت](/azure/active-directory/user-help/microsoft-authenticator-app-how-to) تطبيق Microsoft Authenticator تطبيق Microsoft Company Portal على أجهزتهم. يمكن تثبيتها من متجر التطبيقات لكل نظام أساسي.||Microsoft 365 E3 أو E5|
|[تمكين تسجيل الجهاز التلقائي لأجهزة الكمبيوتر Windows المجال](/azure/active-directory/active-directory-conditional-access-automatic-device-registration-setup). سيتأكد الوصول الشرطي من أن الأجهزة التي تتصل التطبيقات متوافقة أو منضمة إلى المجال. لدعم ذلك على أجهزة الكمبيوتر Windows، يجب أن يكون الجهاز مسجلا في Azure AD.  تتناول هذه المقالة كيفية تكوين التسجيل التلقائي للجهاز.|السحابة فقط|Microsoft 365 E3 أو E5|
|**قم بإعداد فريق الدعم**. ضع خطة للمستخدمين الذين لا يمكنهم إكمال MFA. قد يؤدي ذلك إلى إضافتها إلى مجموعة استثناءات نهج، أو تسجيل معلومات MFA جديدة لها. قبل إجراء أي من هذه التغييرات الحساسة والأمان، تحتاج إلى التأكد من أن المستخدم الفعلي هو من يقوم بإجراء الطلب. إن مطالبة مديري المستخدمين للمساعدة في الموافقة خطوة فعالة.||Microsoft 365 E3 أو E5|
|[تكوين إعادة كتابة كلمة المرور إلى AD في الموقع.](/azure/active-directory/active-directory-passwords-getting-started) تتيح كتابة كلمة المرور ل Azure AD أن يطلب من المستخدمين تغيير كلمات المرور الخاصة بهم في الموقع عند الكشف عن اختراق حساب عالي الخطورة. يمكنك تمكين هذه الميزة باستخدام Azure AD الاتصال باستخدام إحدى طريقتين: إما تمكين ميزة "كتابة كلمة المرور" في شاشة الميزات الاختيارية لإعداد Azure AD الاتصال أو تمكينها عبر Windows PowerShell.|السحابة فقط|Microsoft 365 E3 أو E5|
|[تكوين حماية كلمة مرور Azure AD](/azure/active-directory/authentication/concept-password-ban-bad). يكشف Azure AD Password Protection عن كلمات المرور الضعيفة المعروفة ومتغيراتها ويحظرها، كما يمكنه حظر مصطلحات ضعيفة إضافية خاصة بمنظمتك. يتم تطبيق قوائم كلمات المرور المحظورة بشكل افتراضي تلقائيا على جميع المستخدمين في مستأجر Azure AD. يمكنك تعريف إدخالات إضافية في قائمة كلمات مرور محظورة مخصصة. عندما يقوم المستخدمون بتغيير كلمات المرور أو إعادة تعيينها، يتم التحقق من قوائم كلمات المرور المحظورة هذه لفرض استخدام كلمات مرور قوية.||Microsoft 365 E3 أو E5|
|[تمكين حماية هوية Azure Active Directory](/azure/active-directory/identity-protection/overview-identity-protection). تمكنك Azure AD Identity Protection من الكشف عن نقاط الضعف المحتملة التي تؤثر على هويات مؤسستك وتكوين نهج المعالجة التلقائية إلى مخاطر تسجيل الدخول المنخفضة والمتوسطة والأعلى ومخاطر المستخدم.||Microsoft 365 E5 أو Microsoft 365 E3 باستخدام الوظائف الإضافية أمان E5|
|**تمكين المصادقة** [الحديثة Exchange Online](/Exchange/clients-and-mobile-in-exchange-online/enable-or-disable-modern-authentication-in-exchange-online) و Skype for Business [Online](https://social.technet.microsoft.com/wiki/contents/articles/34339.skype-for-business-online-enable-your-tenant-for-modern-authentication.aspx). المصادقة الحديثة هي أحد المتطلبات الأساسية لاستخدام المصادقة MFA. يتم تمكين المصادقة الحديثة بشكل افتراضي لعملاء Office 2016 و2019 SharePoint OneDrive for Business.||Microsoft 365 E3 أو E5|
|[تمكين تقييم الوصول المستمر](microsoft-365-continuous-access-evaluation.md) ل Azure AD. ينهي تقييم الوصول المستمر جلسات المستخدم النشطة بشكل استباقي ويفرض تغييرات نهج المستأجر في الوقت الحقيقي تقريبا.||Microsoft 365 E3 أو E5|

## <a name="recommended-client-configurations"></a>تكوينات العميل المستحسنة

يصف هذا القسم تكوينات عميل النظام الأساسي الافتراضية التي نوصي بتوفير أفضل تجربة SSO للمستخدمين، بالإضافة إلى المتطلبات التقنية الأساسية للوصول الشرطي.

### <a name="windows-devices"></a>Windows الأجهزة

نوصي Windows 11 أو Windows 10 (الإصدار 2004 أو الإصدارات الأحدث)، حيث تم تصميم Azure لتوفير تجربة SSO الأكثر سلاسة الممكنة لكل من Azure AD المحلي و Azure. يجب تكوين أجهزة العمل أو المؤسسة المدرسية للانضمام إلى Azure AD مباشرة أو إذا كانت المؤسسة تستخدم صلة مجال AD في الموقع، يجب تكوين هذه الأجهزة للتسجيل تلقائيا وبصمت مع [Azure AD](/azure/active-directory/active-directory-conditional-access-automatic-device-registration-setup).

بالنسبة إلى أجهزة BYOD Windows، يمكن للمستخدمين استخدام **إضافة حساب العمل أو المدرسة**. تجدر الإشارة إلى أن مستخدمي مستعرض Google Chrome Windows 11 أو Windows 10 الأجهزة بحاجة إلى تثبيت ملحق للحصول على تجربة تسجيل [](https://chrome.google.com/webstore/detail/windows-10-accounts/ppnbnpeolgkicgegkbkbjmhlideopiji?utm_source=chrome-app-launcher-info-dialog) الدخول السلسة نفسها التي يحصل عليها Microsoft Edge المستخدمون. أيضا، إذا كانت مؤسستك لديها أجهزة Windows 8 أو 8.1، يمكنك تثبيت Microsoft Workplace Join لأجهزة الكمبيوتر Windows 10 الكمبيوتر. [قم بتنزيل الحزمة لتسجيل](https://www.microsoft.com/download/details.aspx?id=53554) الأجهزة باستخدام Azure AD.

### <a name="ios-devices"></a>أجهزة iOS

نوصي بتثبيت تطبيق Microsoft Authenticator [على](/azure/multi-factor-authentication/end-user/microsoft-authenticator-app-how-to) أجهزة المستخدمين قبل نشر سياسات الوصول الشرطي أو MFA. كحد أدنى، يجب تثبيت التطبيق عندما يطلب من المستخدمين تسجيل جهازهم باستخدام Azure AD عن طريق إضافة حساب العمل أو المدرسة، أو عند تثبيت تطبيق مدخل شركة Intune لتسجيل أ جهازهم في الإدارة. يعتمد ذلك على نهج الوصول الشرطي الذي تم تكوينه.

### <a name="android-devices"></a>أجهزة Android

نوصي المستخدمين بتثبيت Intune Company Portal [التطبيق](https://play.google.com/store/apps/details?id=com.microsoft.windowsintune.companyportal&hl=en) Microsoft Authenticator قبل نشر سياسات [](/azure/multi-factor-authentication/end-user/microsoft-authenticator-app-how-to) الوصول الشرطي أو عند الحاجة أثناء محاولات مصادقة معينة. بعد تثبيت التطبيق، قد يطلب من المستخدمين التسجيل في Azure AD أو تسجيل جهازهم في Intune. يعتمد ذلك على نهج الوصول الشرطي الذي تم تكوينه.

نوصي أيضا بأن يتم توحيد الأجهزة المملوكة لمنظمه على OEMs والإصدارات التي تدعم Android for Work أو Samsung Knox للسماح بإدارة حسابات البريد وحمايتها بواسطة نهج Intune MDM.

### <a name="recommended-email-clients"></a>عملاء البريد الإلكتروني الموصى به

يدعم عملاء البريد الإلكتروني التالي المصادقة الحديثة والوصول الشرطي.

|النظام الأساسي|Client|الإصدار/الملاحظات|
|---|---|---|
|**بالنسبة لنظام التشغيل**|Outlook|2019, 2016, 2013 <p> [تمكين المصادقة الحديثة](../../admin/security-and-compliance/enable-modern-authentication.md) <p> [التحديثات المطلوبة](https://support.office.com/article/Outlook-Updates-472c2322-23a4-4014-8f02-bbc09ad62213)|
|**iOS**|Outlook ل iOS|[الأحدث](https://itunes.apple.com/us/app/microsoft-outlook-email-and-calendar/id951937596?mt=8)|
|**Android**|Outlook ل Android|[الأحدث](https://play.google.com/store/apps/details?id=com.microsoft.office.outlook&hl=en)|
|**macOS**|Outlook|2019 و2016|
|**Linux**|غير معتمد||

### <a name="recommended-client-platforms-when-securing-documents"></a>الأنظمة الأساسية للعميل الموصى بها عند تأمين المستندات

يوصى بإجراء العملاء التاليين عند تطبيق نهج مستندات آمن.

|النظام الأساسي|Word/Excel/PowerPoint|OneNote|OneDrive التطبيق|SharePoint التطبيق|[المزامنة من OneDrive العميل](/onedrive/enable-conditional-access)|
|---|---|---|---|---|---|
|Windows 11 أو Windows 10|معتمد|معتمد|N/A|N/A|معتمد|
|Windows 8.1|معتمد|معتمد|N/A|N/A|معتمد|
|Android|معتمد|معتمد|معتمد|معتمد|N/A|
|iOS|معتمد|معتمد|معتمد|معتمد|N/A|
|macOS|معتمد|معتمد|N/A|N/A|غير معتمد|
|Linux|غير معتمد|غير معتمد|غير معتمد|غير معتمد|غير معتمد|

### <a name="microsoft-365-client-support"></a>Microsoft 365 دعم العملاء

لمزيد من المعلومات حول دعم العملاء في Microsoft 365، راجع المقالات التالية:

- [Microsoft 365 دعم تطبيق العميل - الوصول الشرطي](../../enterprise/microsoft-365-client-support-conditional-access.md)
- [Microsoft 365 دعم تطبيق العميل - المصادقة متعددة العوامل](../../enterprise/microsoft-365-client-support-multi-factor-authentication.md)

## <a name="protecting-administrator-accounts"></a>حماية حسابات المسؤولين

بالنسبة Microsoft 365 E3 أو E5 أو باستخدام تراخيص Azure AD Premium P1 أو P2 منفصلة، يمكنك طلب MFA حسابات المسؤولين باستخدام نهج الوصول الشرطي الذي تم إنشاؤه يدويا. راجع [الوصول الشرطي: طلب MFA للمسؤولين](/azure/active-directory/conditional-access/howto-conditional-access-policy-admin-mfa) للحصول على التفاصيل.

بالنسبة إلى إصدارات Microsoft 365 أو Office 365 التي لا تدعم الوصول الشرطي، يمكنك تمكين إعدادات الأمان الافتراضية التي تتطلب MFA لكل الحسابات[](/azure/active-directory/fundamentals/concept-fundamentals-security-defaults).

فيما يلي بعض التوصيات الإضافية:

- استخدم [Azure AD إدارة الهويات المتميزة](/azure/active-directory/privileged-identity-management/pim-getting-started) لتقليل عدد الحسابات الإدارية الثابتة.
- [استخدم إدارة الوصول](../../compliance/privileged-access-management-overview.md) المتميز لحماية مؤسستك من الخروقات التي قد تستخدم حسابات المسؤول المتميزة الموجودة مع إمكانية الوصول الدائم إلى البيانات الحساسة أو الوصول إلى إعدادات التكوين الهامة.
- أنشئ حسابات منفصلة تم تعيينها Microsoft 365 [أدوار المسؤولين للإدارة](../../admin/add-users/about-admin-roles.md) *فقط*. يجب أن يكون لدى المسؤولين حساب المستخدم الخاص بهم للاستخدام العادي غير الإداري، واستخدام حساب إداري فقط عند الضرورة لإكمال مهمة مقترنة بدورهم أو وظيفتهم.
- اتبع [أفضل الممارسات](/azure/active-directory/admin-roles-best-practices) لتأمين الحسابات المتميزة في Azure AD.

## <a name="next-step"></a>الخطوة التالية

[![الخطوة 2: تكوين الهوية ثقة معدومة المشترك والوصول إلى سياسات الوصول الشرطي.](../../media/microsoft-365-policies-configurations/identity-device-access-steps-next-step-2.png#lightbox)](identity-access-policies.md)

[تكوين ونهج الوصول إلى ثقة معدومة البيانات الشائعة](identity-access-policies.md)