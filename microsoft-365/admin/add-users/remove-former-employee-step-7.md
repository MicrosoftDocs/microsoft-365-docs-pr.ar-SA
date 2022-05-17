---
title: الخطوة 7 - حذف حساب مستخدم موظف سابق
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
- SPO_Content
ms.custom:
- MSStore_Link
- TRN_M365B
- OKR_SMB_Videos
- AdminSurgePortfolio
- m365solution-removeemployee
search.appverid:
- BCS160
- MET150
- MOE150
description: بعد حفظ جميع بيانات مستخدم موظف سابق والوصول إليها، يمكنك حذف حساب الموظف السابق في مركز مسؤولي Microsoft 365.
ms.openlocfilehash: d6e53dd8d14add9383e3eff9d3c1d90a5087ec45
ms.sourcegitcommit: 9255a7e8b398f92d8dae09886ae95dc8577bf29a
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 05/17/2022
ms.locfileid: "65436254"
---
# <a name="step-7---delete-a-former-employees-user-account"></a>الخطوة 7 - حذف حساب مستخدم موظف سابق

بعد حفظ جميع بيانات مستخدم الموظف السابق والوصول إليها، يمكنك حذف حساب الموظف السابق.

> [!IMPORTANT]
> لا تحذف الحساب إذا قمت بإعداد إعادة توجيه البريد الإلكتروني أو تحويله إلى علبة بريد مشتركة. يحتاج كلاهما إلى الحساب لتثبيت إعادة التوجيه أو علبة البريد المشتركة.

1. في مركز الإدارة، انتقل إلى صفحة **المستخدمين النشطين للمستخدمين**\>.<a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank"></a>
2. حدد اسم الموظف الذي تريد حذفه.
3. ضمن اسم المستخدم، حدد **"حذف المستخدم**". اختر الخيارات التي تريدها لهذا المستخدم، ثم حدد **"حذف مستخدم**". إذا قمت بالفعل بمنح مستخدم آخر حق الوصول إلى البريد الإلكتروني لهذا المستخدم OneDrive، فلن تحتاج إلى القيام بذلك مرة أخرى هنا.

عندما تحذف مستخدما، يصبح الحساب غير نشط لمدة 30 يوما تقريبا. لديك حتى ذلك الحين لاستعادة الحساب قبل حذفه نهائيا.

## <a name="watch-delete-a-former-employees-user-account"></a>شاهد: حذف حساب مستخدم موظف سابق

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE1FOfR]

إذا وجدت هذا الفيديو مفيدا، فراجع [سلسلة التدريب الكاملة للشركات الصغيرة وتلك الجديدة على Microsoft 365](../../business-video/index.yml).

## <a name="does-your-organization-use-active-directory"></a>هل تستخدم مؤسستك Active Directory؟

إذا كانت مؤسستك تقوم بمزامنة حسابات المستخدمين إلى Microsoft 365 من بيئة Active Directory محلية، فيجب حذف حسابات المستخدمين هذه واستعادتها في خدمة Active Directory المحلية. لا يمكنك حذفها أو استعادتها في Office 365.

لمعرفة كيفية حذف حساب المستخدم واستعادته في Active Directory، راجع [حذف حساب مستخدم](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc753730(v=ws.11)).
  
إذا كنت تستخدم Azure Active Directory، فراجع [الأمر Remove-MsolUser](/powershell/module/msonline/remove-msoluser) PowerShell cmdlet.
  
## <a name="what-you-need-to-know-about-terminating-an-employees-email-session"></a>ما تحتاج إلى معرفته حول إنهاء جلسة عمل البريد الإلكتروني للموظف

فيما يلي معلومات حول كيفية إخراج موظف من البريد الإلكتروني (Exchange).

<br>

****

|ما يمكنك فعله|كيفية القيام بذلك|
|:-----|:-----|
|إنهاء جلسة عمل (مثل Outlook على ويب أو Outlook أو Exchange المزامنة النشطة وما إلى ذلك) وفرض فتح جلسة عمل جديدة|إعادة تعيين كلمة المرور|
|إنهاء جلسة عمل وحظر الوصول إلى جلسات العمل المستقبلية (لجميع البروتوكولات)|تعطيل الحساب. على سبيل المثال، (في مركز إدارة Exchange أو باستخدام PowerShell): <p>  `Set-Mailbox user@contoso.com -AccountDisabled:$true`|
|إنهاء جلسة العمل لبروتوكول معين (مثل ActiveSync)|تعطيل البروتوكول. على سبيل المثال، (في مركز إدارة Exchange أو باستخدام PowerShell): <p>  `Set-CASMailbox user@contoso.com -ActiveSyncEnabled:$false`|
|

يمكن تنفيذ العمليات المذكورة أعلاه في ثلاثة أماكن:
  
<br>

****

|إذا قمت بإنهاء جلسة العمل هنا|المدة التي يستغرقها|
|---|---|
|في مركز إدارة Exchange أو باستخدام PowerShell|التأخير المتوقع في غضون 30 دقيقة|
|في مركز إدارة Azure Active Directory|التأخير المتوقع هو 60 دقيقة|
|في بيئة محلية|التأخير المتوقع هو 3 ساعات أو أكثر|
|

### <a name="how-to-get-fastest-response-for-account-termination"></a>كيفية الحصول على أسرع استجابة لإنهاء الحساب

**الأسرع**: استخدم مركز إدارة Exchange (استخدام PowerShell) أو مركز إدارة Azure Active Directory. في بيئة محلية، قد يستغرق الأمر عدة ساعات لمزامنة التغيير من خلال DirSync.
  
**الأسرع للمستخدم الذي لديه حالة حضور في الموقع وفي مركز البيانات Exchange**: إنهاء جلسة العمل باستخدام مركز إدارة Azure Active Directory/مركز إدارة Exchange وإجراء التغيير في البيئة المحلية أيضا. وإلا، فسيتم الكتابة فوق التغيير في مركز إدارة Azure Active Directory/مركز إدارة Exchange بواسطة DirSync.
  
## <a name="related-content"></a>المحتويات ذات الصلة

[استعادة مستخدم](restore-user.md) (مقال)

[إعادة تعيين كلمات المرور](reset-passwords.md) (مقالة)
