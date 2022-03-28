---
title: الخطوة 6 - إزالة ترخيص Microsoft 365 من موظف سابق وحذفه
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
description: اتبع هذه الخطوات لإزالة Microsoft 365 من موظف سابق.
ms.openlocfilehash: b724e8d65c990396ad376544de86d4ffd0cb5fdc
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/08/2022
ms.locfileid: "63575504"
---
# <a name="step-6---remove-and-delete-the-microsoft-365-license-from-a-former-employee"></a>الخطوة 6 - إزالة ترخيص Microsoft 365 من موظف سابق وحذفه

إذا كنت لا تريد الدفع مقابل ترخيص بعد أن يترك شخص ما مؤسستك، ستحتاج إلى إزالة ترخيص Microsoft 365 ثم حذفه من اشتراكك. يمكنك تعيين ترخيص لمستخدم آخر إذا لم تحذفه.

إذا كان يجب الوصول إلى علبة البريد من قبل الأشخاص المخولا الذين تم منحهم أذونات eDiscovery للتوافق أو لأسباب قانونية، فيجب تعيين ترخيص الخطة 2 من Exchange Online (أو ترخيص الخطة 1 من Exchange Online مع ترخيص الوظائف الإضافية أرشفة Exchange Online) حتى يمكن تطبيق الاستمرار على علبة البريد قبل حذفها. بعد حذف حساب المستخدم، سيكون Exchange Online ترخيص مقترن باستخدام حساب المستخدم متوفرا لتعيينه إلى مستخدم جديد.
  
عند إزالة الترخيص، يتم تخزين كل بيانات المستخدم لمدة 30 يوما. يمكنك [الوصول](get-access-to-and-back-up-a-former-user-s-data.md) إلى البيانات، أو [استعادة](restore-user.md) الحساب إذا عاد المستخدم مرة أخرى. بعد مرور 30 يوما، يتم حذف كل بيانات المستخدم (باستثناء المستندات المخزنة على SharePoint Online) بشكل دائم من Microsoft 365 ولا يمكن استردادها.

1. في مركز الإدارة، انتقل إلى صفحة **المستخدمون** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">النشطون</a> .
2. حدد اسم الموظف الذي تريد حظره، ثم حدد علامة التبويب **التراخيص والتطبيقات** .
3. قم بمسح خانات الاختيار الخاصة بالترخيص (التراخيص) الذي تريد إزالته، ثم حدد **حفظ التغييرات**.

**لتقليل عدد التراخيص التي** تدفع مقابلها حتى تقوم بتوظيف شخص آخر، قم بالخطوات التالية:

1. في مركز الإدارة، انتقل إلى **صفحة فوترة** \> منتجاتك، وحدد <a href="https://go.microsoft.com/fwlink/p/?linkid=842054" target="_blank"></a> **علامة التبويب** المنتجات.
2. حدد الاشتراك الذي تريد إزالة التراخيص منه.
3. في صفحة التفاصيل، حدد **إزالة التراخيص**.
4. في الجزء **إزالة التراخيص**، ضمن كمية جديدة، في المربع إجمالي التراخيص، أدخل العدد الإجمالي للتراخيص التي تريدها لهذا الاشتراك. على سبيل المثال، إذا كان لديك 25 ترخيصا وتريد إزالة أحدها، أدخل 24.
5. حدد **حفظ**.

عند [إضافة شخص آخر](add-users.md) إلى شركتك، سيطلب منك شراء ترخيص في الوقت نفسه، بخطوة واحدة فقط!

للحصول على مزيد من المعلومات حول إدارة تراخيص المستخدمين Microsoft 365 للأعمال، راجع تعيين تراخيص للمستخدمين في [Microsoft 365](../manage/assign-licenses-to-users.md) للأعمال، وغير تعيين التراخيص من المستخدمين في Microsoft 365 [للأعمال](../manage/remove-licenses-from-users.md).
  
## <a name="how-the-deleted-employee-account-affects-skype-for-business"></a>كيفية تأثير حساب الموظف المحذوف Skype for Business

عند إزالة ترخيص مستخدم من Office 365، سيتم إصدار رقم الاتصال PSTN المقترن بالمستخدم. يمكنك تعيينه إلى مستخدم آخر.
  
إذا كان المستخدم ينتمي إلى مجموعة قائمة انتظار، لن يكون هدفا قابلا للتطبيق من وكلاء قائمة انتظار الاتصال. لذلك، نوصي أيضا بإزالة المستخدم من المجموعات المقترنة ب قائمة انتظار المكالمة.

## <a name="set-up-call-forwarding-to-people-in-your-organization"></a>إعداد إعادة توجيه الاتصال للأشخاص في مؤسستك

إذا كنت بحاجة إلى إعداد إعادة توجيه المكالمات لرقم هاتف الموظف الذي تم إنهاؤه، يمكن إعداد إعادة توجيه الاتصال ضمن سياسات الاتصال بإعداد إعادة توجيه حيث يمكن إعادة توجيه المكالمات الواردة إلى مستخدمين آخرين أو يمكن أن يتصل شخص آخر في الوقت نفسه. لمزيد من المعلومات، راجع [الاتصال ب والسياسات في Microsoft Teams](/microsoftteams/teams-calling-policy).
