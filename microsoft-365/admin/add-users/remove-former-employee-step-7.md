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
description: اتبع هذه الخطوات لحذف حساب مستخدم موظف سابق.
ms.openlocfilehash: 631405b66c777060463a4e98620ff3c8b06c7e77
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 10/06/2021
ms.locfileid: "63574291"
---
# <a name="step-7---delete-a-former-employees-user-account"></a>الخطوة 7 - حذف حساب مستخدم موظف سابق

بعد حفظ كل بيانات المستخدم الخاصة بالموظف السابق والوصول إليها، يمكنك حذف حساب الموظف السابق.

> [!IMPORTANT]
> لا تحذف الحساب إذا قمت بإعداد إعادة توجيه البريد الإلكتروني أو تحويله إلى علبة بريد مشتركة. يحتاج كل منهما إلى الحساب لإرساء إعادة توجيه علبة البريد أو علبة البريد المشتركة.

1. في مركز الإدارة، انتقل إلى صفحة **المستخدمون** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">النشطون</a> .
2. حدد اسم الموظف الذي تريد حذفه.
3. ضمن اسم المستخدم، حدد **حذف مستخدم**. حدد الخيارات التي تريدها لهذا المستخدم، ثم حدد **حذف مستخدم**. إذا منحت مستخدما آخر حق الوصول إلى البريد الإلكتروني لهذا المستخدم OneDrive، فلا تحتاج إلى القيام بذلك مرة أخرى هنا.

عندما تحذف مستخدما، يصبح الحساب غير نشط لمدة 30 يوما تقريبا. لديك حتى ذلك الحين لاستعادة الحساب قبل أن يتم حذفه نهائيا.

## <a name="watch-delete-a-former-employees-user-account"></a>شاهد: حذف حساب مستخدم موظف سابق

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE1FOfR]

إذا وجدت هذا الفيديو مفيدا، فتحقق من سلسلة التدريب الكاملة للشركات الصغيرة وتلك الجديدة [Microsoft 365.](../../business-video/index.yml)

## <a name="does-your-organization-use-active-directory"></a>هل تستخدم مؤسستك Active Directory؟

إذا كانت مؤسستك تقوم بمزامنة حسابات المستخدمين Microsoft 365 من بيئة Active Directory محلية، فيجب حذف حسابات المستخدمين هذه واستعادتها في خدمة Active Directory المحلية. لا يمكنك حذفها أو استعادتها في Office 365.

لمعرفة كيفية حذف حساب المستخدم واستعادته في Active Directory، راجع [حذف حساب مستخدم](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc753730(v=ws.11)).
  
إذا كنت تستخدم Azure Active Directory، فشاهد الأمر [cmdlet Remove-MsolUser](/powershell/module/msonline/remove-msoluser) PowerShell.
  
## <a name="what-you-need-to-know-about-terminating-an-employees-email-session"></a>ما تحتاج إلى معرفته حول إنهاء جلسة عمل البريد الإلكتروني الخاصة بالموظف

إليك معلومات حول كيفية تخلص موظف من البريد الإلكتروني (Exchange).

<br>

****

|ما يمكنك فعله|كيفية القيام بذلك|
|:-----|:-----|
|إنهاء جلسة عمل (مثل Outlook على ويب أو Outlook أو Exchange نشطة وغير ذلك) مع فرض فتح جلسة عمل جديدة|إعادة تعيين كلمة المرور|
|إنهاء جلسة عمل وحظر الوصول إلى الجلسات المستقبلية (لكل البروتوكولات)|تعطيل الحساب. على سبيل المثال، (في مركز إدارة Exchange أو باستخدام PowerShell): <p>  `Set-Mailbox user@contoso.com -AccountDisabled:$true`|
|إنهاء جلسة العمل لبروتوكول معين (مثل ActiveSync)|تعطيل البروتوكول. على سبيل المثال، (في مركز إدارة Exchange أو باستخدام PowerShell): <p>  `Set-CASMailbox user@contoso.com -ActiveSyncEnabled:$false`|
|

يمكن تنفيذ العمليات أعلاه في ثلاثة أماكن:
  
<br>

****

|إذا قمت بإنهاء جلسة العمل هنا|المدة التي يستغرقها|
|---|---|
|في مركز Exchange أو باستخدام PowerShell|التأخير المتوقع في غضون 30 دقيقة|
|في مركز إدارة Azure Active Directory|التأخير المتوقع هو 60 دقيقة|
|في بيئة المحلية|التأخير المتوقع هو 3 ساعات أو أكثر|
|

### <a name="how-to-get-fastest-response-for-account-termination"></a>كيفية الحصول على أسرع استجابة لإنهاء الحساب

**الأسرع**: استخدم مركز إدارة Exchange (استخدم PowerShell) أو مركز إدارة Azure Active Directory. في البيئة المحلية، قد يستغرق الأمر عدة ساعات لمزامنة التغيير من خلال DirSync.
  
الأسرع للمستخدم الذي له حالة حضور في الموقع المحلي وفي مركز بيانات **Exchange**: إنهاء جلسة العمل باستخدام مركز إدارة Azure Active Directory/مركز إدارة Exchange وأدر التغيير في البيئة المحلية أيضا. وإلا، سيتم الكتابة فوق التغيير في مركز إدارة Azure Active Directory/Exchange بواسطة DirSync.
  
## <a name="related-content"></a>المحتوى ذي الصلة

[استعادة مستخدم](restore-user.md) (مقالة)

[إعادة تعيين كلمات المرور](reset-passwords.md) (مقالة)
