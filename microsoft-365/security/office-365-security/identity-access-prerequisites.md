---
title: العمل المتطلب الأساسي لتنفيذ نهج الوصول إلى الهوية والجهاز - Microsoft 365 للشركات | Microsoft Docs
description: تصف هذه المقالة المتطلبات الأساسية التي تحتاج إلى تلبيتها لاستخدام ثقة معدومة نهج وتكوينات الوصول إلى الهوية والجهاز.
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
- zerotrust-solution
ms.technology: mdo
ms.openlocfilehash: 6883782a942b7fda8e2dedc721756b59a3e7ede6
ms.sourcegitcommit: 61b22df76e0f81e5ef11c587b129287886151c79
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/12/2022
ms.locfileid: "66749979"
---
# <a name="prerequisite-work-for-implementing-zero-trust-identity-and-device-access-policies"></a>العمل المتطلب الأساسي لتنفيذ ثقة معدومة نهج الهوية والوصول إلى الجهاز

تصف هذه المقالة المتطلبات الأساسية التي يجب على المسؤولين تلبيتها لاستخدام نهج الوصول إلى الهوية والجهاز ثقة معدومة الموصى بها، واستخدام الوصول المشروط. كما يناقش الإعدادات الافتراضية الموصى بها لتكوين الأنظمة الأساسية للعميل للحصول على أفضل تجربة تسجيل الدخول الأحادي.

## <a name="prerequisites"></a>المتطلبات الأساسية

قبل استخدام نهج الهوية والوصول إلى الأجهزة ثقة معدومة الموصى بها، تحتاج مؤسستك إلى تلبية المتطلبات الأساسية. تختلف المتطلبات لمختلف نماذج الهوية والمصادقة المدرجة:

- السحابة فقط
- مختلط مع مصادقة مزامنة تجزئة كلمة المرور (PHS)
- مختلط مع مصادقة المرور (PTA)
- الاتحاديه

يوضح الجدول التالي بالتفصيل ميزات المتطلبات الأساسية وتكوينها التي تنطبق على جميع نماذج الهوية، إلا إذا تمت الإشارة إليها.

|التكوين|الاستثناءات|الترخيص|
|---|:---:|---|
|[تكوين PHS](/azure/active-directory/hybrid/how-to-connect-password-hash-synchronization).  يجب تمكين هذا للكشف عن بيانات الاعتماد المسربة والعمل عليها للوصول المشروط المستند إلى المخاطر. **ملاحظه:** هذا مطلوب بغض النظر عما إذا كانت مؤسستك تستخدم مصادقة موحدة.|السحابة فقط|Microsoft 365 E3 أو E5|
|[تمكين تسجيل الدخول الأحادي السلس](/azure/active-directory/connect/active-directory-aadconnect-sso) لتسجيل دخول المستخدمين تلقائيا عند وجودهم على أجهزة المؤسسة المتصلة بشبكة مؤسستك.|السحابة فقط والفيدرالية|Microsoft 365 E3 أو E5|
|[تكوين المواقع المسماة](/azure/active-directory/reports-monitoring/quickstart-configure-named-locations). Azure AD Identity Protection يجمع ويحلل جميع بيانات جلسة العمل المتاحة لإنشاء درجة مخاطر. نوصي بتحديد نطاقات IP العامة لمؤسستك لشبكتك في تكوين المواقع المسماة Azure AD. يتم إعطاء نسبة استخدام الشبكة القادمة من هذه النطاقات درجة مخاطر أقل، ويتم إعطاء نسبة استخدام الشبكة من خارج بيئة المؤسسة درجة مخاطر أعلى.||Microsoft 365 E3 أو E5|
|[تسجيل جميع المستخدمين لإعادة تعيين كلمة مرور الخدمة الذاتية (SSPR) والمصادقة متعددة العوامل (MFA).](/azure/active-directory/authentication/concept-registration-mfa-sspr-converged) نوصي بتسجيل المستخدمين للمصادقة متعددة العوامل Azure AD قبل الوقت المحدد. تستخدم Azure AD Identity Protection Azure AD Multifactor Authentication لإجراء تحقق أمان إضافي. بالإضافة إلى ذلك، للحصول على أفضل تجربة لتسجيل الدخول، نوصي المستخدمين بتثبيت [تطبيق Microsoft Authenticator](/azure/active-directory/user-help/microsoft-authenticator-app-how-to) وتطبيق Microsoft Company Portal على أجهزتهم. يمكن تثبيتها من متجر التطبيقات لكل نظام أساسي.||Microsoft 365 E3 أو E5|
|[تمكين التسجيل التلقائي للجهاز لأجهزة كمبيوتر Windows المتصلة بالمجال](/azure/active-directory/active-directory-conditional-access-automatic-device-registration-setup). سيتأكد الوصول المشروط من أن الأجهزة المتصلة بالتطبيقات متصلة بالمجال أو متوافقة. لدعم ذلك على أجهزة كمبيوتر Windows، يجب تسجيل الجهاز مع Azure AD.  تناقش هذه المقالة كيفية تكوين تسجيل الجهاز التلقائي.|السحابة فقط|Microsoft 365 E3 أو E5|
|**إعداد فريق الدعم.** ضع خطة للمستخدمين الذين لا يمكنهم إكمال المصادقة متعددة العوامل. قد يكون ذلك إضافتهم إلى مجموعة استبعاد النهج، أو تسجيل معلومات MFA جديدة لهم. قبل إجراء أي من هذه التغييرات الحساسة للأمان، تحتاج إلى التأكد من أن المستخدم الفعلي يقوم بإجراء الطلب. تعد مطالبة مديري المستخدمين بالمساعدة في الموافقة خطوة فعالة.||Microsoft 365 E3 أو E5|
|[تكوين إعادة كتابة كلمة المرور إلى AD المحلي](/azure/active-directory/active-directory-passwords-getting-started). تسمح إعادة كتابة كلمة المرور Azure AD بمطلب تغيير المستخدمين كلمات المرور المحلية الخاصة بهم عند الكشف عن اختراق حساب عالي المخاطر. يمكنك تمكين هذه الميزة باستخدام Azure AD Connect بإحدى طريقتين: إما تمكين **"إعادة كتابة كلمة المرور**" في شاشة الميزات الاختيارية لإعداد Azure AD Connect، أو تمكينها عبر Windows PowerShell.|السحابة فقط|Microsoft 365 E3 أو E5|
|[تكوين الحماية بكلمة مرور Azure AD](/azure/active-directory/authentication/concept-password-ban-bad). Azure AD تكتشف الحماية بكلمة مرور كلمات المرور الضعيفة المعروفة ومتغيراتها وتحظرها، ويمكنها أيضا حظر المصطلحات الضعيفة الإضافية الخاصة بمؤسستك. يتم تطبيق قوائم كلمات المرور المحظورة العمومية الافتراضية تلقائيا على جميع المستخدمين في مستأجر Azure AD. يمكنك تحديد إدخالات إضافية في قائمة كلمات مرور محظورة مخصصة. عندما يغير المستخدمون كلمات المرور الخاصة بهم أو يعيدون تعيينها، يتم التحقق من قوائم كلمات المرور المحظورة هذه لفرض استخدام كلمات مرور قوية.||Microsoft 365 E3 أو E5|
|[تمكين Azure Active Directory Identity Protection](/azure/active-directory/identity-protection/overview-identity-protection). تمكنك Azure AD Identity Protection من اكتشاف الثغرات الأمنية المحتملة التي تؤثر على هويات مؤسستك وتكوين نهج معالجة تلقائي لمخاطر تسجيل الدخول ومخاطر المستخدم المنخفضة والمتوسطة وعالية.||Microsoft 365 E5 أو Microsoft 365 E3 باستخدام الوظيفة الإضافية E5 Security|
|**تمكين المصادقة الحديثة** [Exchange Online](/Exchange/clients-and-mobile-in-exchange-online/enable-or-disable-modern-authentication-in-exchange-online) ول [Skype for Business Online](https://social.technet.microsoft.com/wiki/contents/articles/34339.skype-for-business-online-enable-your-tenant-for-modern-authentication.aspx). المصادقة الحديثة هي شرط أساسي لاستخدام المصادقة متعددة العوامل. يتم تمكين المصادقة الحديثة بشكل افتراضي لعملاء Office 2016 و2019 وSharePoint OneDrive for Business.||Microsoft 365 E3 أو E5|
|[تمكين تقييم الوصول المستمر](microsoft-365-continuous-access-evaluation.md) Azure AD. يؤدي تقييم الوصول المستمر إلى إنهاء جلسات عمل المستخدم النشطة بشكل استباقي وفرض تغييرات نهج المستأجر في الوقت الفعلي القريب.||Microsoft 365 E3 أو E5|

## <a name="recommended-client-configurations"></a>تكوينات العميل الموصى بها

يصف هذا القسم تكوينات عميل النظام الأساسي الافتراضية التي نوصي بتوفير أفضل تجربة تسجيل الدخول الأحادي للمستخدمين، بالإضافة إلى المتطلبات الأساسية التقنية للوصول المشروط.

### <a name="windows-devices"></a>أجهزة Windows

نوصي Windows 11 أو Windows 10 (الإصدار 2004 أو الإصدارات الأحدث)، حيث تم تصميم Azure لتوفير تجربة تسجيل الدخول الأحادي الأكثر سلاسة الممكنة لكل من الموقع المحلي Azure AD. يجب تكوين الأجهزة الصادرة عن العمل أو المؤسسة التعليمية للانضمام Azure AD مباشرة أو إذا كانت المؤسسة تستخدم الانضمام إلى مجال AD المحلي، يجب تكوين هذه الأجهزة [للتسجيل تلقائيا وبصمت مع Azure AD](/azure/active-directory/active-directory-conditional-access-automatic-device-registration-setup).

بالنسبة إلى أجهزة BYOD Windows، يمكن للمستخدمين استخدام **إضافة حساب العمل أو المؤسسة التعليمية**. لاحظ أن مستخدمي مستعرض Google Chrome على أجهزة Windows 11 أو Windows 10 يحتاجون إلى [تثبيت ملحق](https://chrome.google.com/webstore/detail/windows-10-accounts/ppnbnpeolgkicgegkbkbjmhlideopiji?utm_source=chrome-app-launcher-info-dialog) للحصول على تجربة تسجيل الدخول السلسة نفسها التي يتمتع بها مستخدمو Microsoft Edge. أيضا، إذا كانت مؤسستك لديها Windows 8 أو 8.1 أجهزة مرتبطة بالمجال، يمكنك تثبيت Microsoft Workplace Join لأجهزة الكمبيوتر غير Windows 10. [قم بتنزيل الحزمة لتسجيل](https://www.microsoft.com/download/details.aspx?id=53554) الأجهزة باستخدام Azure AD.

### <a name="ios-devices"></a>أجهزة iOS

نوصي بتثبيت [تطبيق Microsoft Authenticator](/azure/multi-factor-authentication/end-user/microsoft-authenticator-app-how-to) على أجهزة المستخدم قبل نشر نهج الوصول المشروط أو المصادقة متعددة العوامل. كحد أدنى، يجب تثبيت التطبيق عندما يطلب من المستخدمين تسجيل أجهزتهم مع Azure AD عن طريق إضافة حساب العمل أو المؤسسة التعليمية، أو عند تثبيت تطبيق مدخل شركة Intune لتسجيل أجهزتهم في الإدارة. يعتمد هذا على نهج الوصول المشروط الذي تم تكوينه.

### <a name="android-devices"></a>أجهزة Android

نوصي المستخدمين بتثبيت [تطبيق Intune Company Portal](https://play.google.com/store/apps/details?id=com.microsoft.windowsintune.companyportal&hl=en) [وتطبيق Microsoft Authenticator](/azure/multi-factor-authentication/end-user/microsoft-authenticator-app-how-to) قبل نشر نهج الوصول المشروط أو عند الحاجة إليها أثناء محاولات مصادقة معينة. بعد تثبيت التطبيق، قد يطلب من المستخدمين التسجيل مع Azure AD أو تسجيل أجهزتهم في Intune. يعتمد هذا على نهج الوصول المشروط الذي تم تكوينه.

نوصي أيضا بأن يتم توحيد الأجهزة المملوكة للمؤسسة على الشركات المصنعة للأجهزة الأصلية والإصدارات التي تدعم Android for Work أو Samsung Knox للسماح بحسابات البريد، وإدارتها وحمايتها من خلال نهج Intune MDM.

### <a name="recommended-email-clients"></a>عملاء البريد الإلكتروني المستحسنون

يدعم عملاء البريد الإلكتروني التاليون المصادقة الحديثة والوصول المشروط.

|منصه|Client|الإصدار/الملاحظات|
|---|---|---|
|**بالنسبة لنظام التشغيل**|Outlook|2019, 2016, 2013 <p> [تمكين المصادقة الحديثة](../../admin/security-and-compliance/enable-modern-authentication.md) <p> [التحديثات المطلوبة](https://support.office.com/article/Outlook-Updates-472c2322-23a4-4014-8f02-bbc09ad62213)|
|**دائره الرقابه الداخليه**|Outlook for iOS|[احدث](https://itunes.apple.com/us/app/microsoft-outlook-email-and-calendar/id951937596?mt=8)|
|**الروبوت**|Outlook for Android|[احدث](https://play.google.com/store/apps/details?id=com.microsoft.office.outlook&hl=en)|
|**ماك**|Outlook|2019 و2016|
|**ينكس**|غير معتمد||

### <a name="recommended-client-platforms-when-securing-documents"></a>الأنظمة الأساسية الموصى بها للعميل عند تأمين المستندات

يوصى بالعملاء التاليين عند تطبيق نهج مستندات آمن.

|منصه|Word/Excel/PowerPoint|OneNote|تطبيق OneDrive|تطبيق SharePoint|[عميل المزامنة من OneDrive](/onedrive/enable-conditional-access)|
|---|---|---|---|---|---|
|Windows 11 أو Windows 10|دعم|دعم|N/A|N/A|دعم|
|Windows 8.1|دعم|دعم|N/A|N/A|دعم|
|الروبوت|دعم|دعم|دعم|دعم|N/A|
|دائره الرقابه الداخليه|دعم|دعم|دعم|دعم|N/A|
|ماك|دعم|دعم|N/A|N/A|غير معتمد|
|ينكس|غير معتمد|غير معتمد|غير معتمد|غير معتمد|غير معتمد|

### <a name="microsoft-365-client-support"></a>دعم عميل Microsoft 365

لمزيد من المعلومات حول دعم العميل في Microsoft 365، راجع المقالات التالية:

- [دعم تطبيق عميل Microsoft 365 - الوصول المشروط](../../enterprise/microsoft-365-client-support-conditional-access.md)
- [دعم تطبيق عميل Microsoft 365 - المصادقة متعددة العوامل](../../enterprise/microsoft-365-client-support-multi-factor-authentication.md)

## <a name="protecting-administrator-accounts"></a>حماية حسابات المسؤولين

بالنسبة إلى Microsoft 365 E3 أو E5 أو مع تراخيص منفصلة Azure AD Premium P1 أو P2، يمكنك طلب المصادقة متعددة العوامل لحسابات المسؤولين باستخدام نهج الوصول المشروط الذي تم إنشاؤه يدويا. راجع [الوصول المشروط: طلب المصادقة متعددة العوامل للمسؤولين](/azure/active-directory/conditional-access/howto-conditional-access-policy-admin-mfa) للحصول على التفاصيل.

بالنسبة لإصدارات Microsoft 365 أو Office 365 التي لا تدعم الوصول المشروط، يمكنك تمكين [إعدادات الأمان الافتراضية](/azure/active-directory/fundamentals/concept-fundamentals-security-defaults) لطلب المصادقة متعددة العوامل لجميع الحسابات.

فيما يلي بعض التوصيات الإضافية:

- استخدم [Azure AD إدارة الهويات المتميزة](/azure/active-directory/privileged-identity-management/pim-getting-started) لتقليل عدد الحسابات الإدارية الثابتة.
- [استخدم إدارة الوصول المتميزة](../../compliance/privileged-access-management-overview.md) لحماية مؤسستك من الخروقات التي قد تستخدم حسابات المسؤول المتميزة الحالية مع الوصول الدائم إلى البيانات الحساسة أو الوصول إلى إعدادات التكوين الهامة.
- إنشاء حسابات منفصلة يتم تعيين [أدوار مسؤول Microsoft 365](../../admin/add-users/about-admin-roles.md) لها *للإدارة فقط واستخدامها*. يجب أن يكون لدى المسؤولين حساب المستخدم الخاص بهم للاستخدام غير الإداري العادي واستخدام حساب إداري فقط عند الضرورة لإكمال مهمة مقترنة بدورهم أو دالتهم الوظيفية.
- اتبع [أفضل الممارسات](/azure/active-directory/admin-roles-best-practices) لتأمين الحسابات المتميزة في Azure AD.

## <a name="next-step"></a>الخطوة التالية

[![الخطوة 2: تكوين هوية ثقة معدومة الشائعة والوصول إلى نهج الوصول المشروط.](../../media/microsoft-365-policies-configurations/identity-device-access-steps-next-step-2.png#lightbox)](identity-access-policies.md)

[تكوين هوية ثقة معدومة الشائعة ونهج الوصول إلى الجهاز](identity-access-policies.md)
