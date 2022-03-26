---
title: استخدام التسجيل الذاتي للخدمة في مؤسستك
f1.keywords:
- NOCSH
author: cmcatee-MSFT
ms.author: cmcatee
manager: scotv
ms.reviewer: seemg, pablom
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
ms.custom:
- commerce_signup
- AdminSurgePortfolio
- okr_SMB
search.appverid: MET150
description: تعرف على Microsoft 365 التسجيل الذاتي وبرامج الخدمة الذاتية المتوفرة مثل Microsoft Power Apps و Microsoft Power Automate و Dynamics 365 for Finance.
ms.date: 03/17/2021
ms.openlocfilehash: 67f0955a4485ea0f668b143f485b34cf2935404b
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/08/2022
ms.locfileid: "63567945"
---
# <a name="using-self-service-sign-up-in-your-organization"></a>استخدام التسجيل الذاتي للخدمة في مؤسستك

يسهل التسجيل الذاتي للخدمة على المستخدمين في مؤسستك التسجيل للحصول على خدمات عبر الإنترنت من Microsoft. نطلق على عملية التسجيل هذه "التسجيل الذاتي للخدمة" لأن المستخدمين يمكنهم التسجيل لاستخدام الخدمات المدفوعة بواسطة اشتراكك، أو استخدام الخدمات المجانية، دون أن نطلب منك اتخاذ إجراء بالنيابة عنهم.

## <a name="how-self-service-sign-up-works"></a>كيفية عمل التسجيل الذاتي للخدمة

يصف المثال التالي كيفية عمل التسجيل الذاتي لمدرسة. تعمل العملية نفسها مع أي مؤسسة تم تمكين برامج الخدمة الذاتية لها في المستأجر.

1. لدى الطلاب وأعضاء هيئة التدريس عناوين بريد إلكتروني للمؤسسة التعليمية تشير إلى أنهم مرتبطون بمؤسستك. على سبيل المثال، قد يشير عنوان jakob@uw.edu الإلكتروني إلى طالب في جامعة واشنطن.
2. يمكن للطلاب وهيئة التدريس الانتقال إلى [موقع](https://go.microsoft.com/fwlink/p/?LinkId=536628) الويب الخاص بك واستخدام عنوان بريدهم الإلكتروني التسجيل للحصول على الخدمات التي تقدمها مؤسستك، مثل Microsoft 365 Apps for enterprise. يمكنهم أيضا التسجيل للحصول على خدمات أخرى مجانية نقدمها.
3. نحن نتحقق من صحة عنوان بريدهم الإلكتروني، ومن ثم يمكنهم بدء استخدام Microsoft 365 أو Power BI أو خدمات أخرى على الفور.
4. ب أنت مسؤول الأعمال، يمكنك معرفة من قام بالاشتراك عن طريق تحديد الاشتراك على صفحة الترخيص في مركز مسؤولي Microsoft 365. بهذه الطريقة يمكنك معرفة وقت وجود تراخيص جديدة أو غير مفهمة للخدمات في المستأجر. للتحكم في ما إذا كان يمكن للمستخدمين التسجيل للحصول على اشتراكات الخدمة الذاتية، استخدم أمر cmdlet [Set-MsolCompanySettings](/powershell/module/msonline/set-msolcompanysettings) PowerShell مع المعلمة **AllowAdHocSubscriptions** . لمزيد من المعلومات، [راجع كيف يمكنني التحكم في إعدادات الخدمة الذاتية؟](/azure/active-directory/users-groups-roles/directory-self-service-signup#how-do-i-control-self-service-settings)

## <a name="available-self-service-programs"></a>برامج الخدمة الذاتية المتوفرة

فيما يلي برامج الخدمة الذاتية المتوفرة حاليا. سيتم تحديث هذه القائمة مع إضافة برامج جديدة.

| برنامج <br/> | الوصف <br/> | معلومات إضافية <br/> | موقع ويب التسجيل الذاتي للخدمة <br/> |
|:-----|:-----|:-----|:-----|
|Office 365 A1**** <br/> |يمكن لأي طالب أو مدرس استخدام عنوان البريد الإلكتروني الخاص بالمدرسة التسجيل للحصول على Office 365 المجاني والحصول على تطبيقات Office على الويب ومساحة تخزين سحابية من OneDrive ومساحة تخزين OneDrive على السحابة و SharePoint عبر الإنترنت لمواقع الفصل والفريق والمشاريع.  <br/> |[Office 365 Education الأسئلة الشائعة حول التقنية](/microsoft-365/education/deploy/office-365-education-self-sign-up) <br/> |[Office 365 Education](https://go.microsoft.com/fwlink/p/?linkid=140841) <br/> |
|**Office 365 A1 Plus** <br/> |يمكن للطلاب والمعلمين المؤهلين التسجيل للحصول على Office 365 A1 Plus، الذي يتضمن كل شيء مذكور أعلاه بالإضافة إلى Microsoft 365 Apps for enterprise. Microsoft 365 Apps for enterprise برنامج الإنتاجية، بما في ذلك Word PowerPoint و Excel و Outlook و OneNote و Publisher و Access و Skype for Business ، الذي تم تثبيته على كمبيوتر سطح المكتب أو الكمبيوتر المحمول.  <br/> |[Office 365 Education الأسئلة الشائعة حول التقنية](/microsoft-365/education/deploy/office-365-education-self-sign-up) <br/> |[Office 365 Education](https://go.microsoft.com/fwlink/p/?linkid=140841) <br/> |
|**Power BI** <br/> |يمكن Power BI المستخدمين من عرض البيانات ومشاركة الاكتشافات والتعاون بطرق بديهية جديدة. <br/> إذا كانت مؤسستك قد اشتركت بالفعل، فقد ترى أيضا تراخيص "Power BI Pro الإصدار التجريبي للمستخدم الفردي"، والتي توفر للمستخدمين إمكانية وصول محدودة ومجانية للإمكانات المتقدمة.  <br/> |[Power BI في مؤسستك](./power-bi-in-your-organization.md) <br/> |[Microsoft Power BI](https://go.microsoft.com/fwlink/p/?LinkId=536629) <br/> |
|**خدمات إدارة الحقوق (RMS)** <br/> |إن RMS للأفراد هو اشتراك مجاني للخدمة الذاتية للمستخدمين في مؤسسة تم إرسال ملفات حساسة محمية بواسطة Azure Rights Management (Azure RMS)، ولكن لم ينفذ قسم قسم المعلومات لديهم Azure Rights Management (Azure RMS) أو خدمات إدارة حقوق Active Directory (AD RMS).  <br/> |[إدارة حقوق الأفراد و Azure](/azure/information-protection/rms-for-individuals) <br/> |[مدخل Microsoft Rights Management](https://portal.azure.com/) حتى تتمكن من التحقق مما إذا كان يمكنك فتح مستند محمي بحقوق معينة.  <br/> |
|**Microsoft Power Apps** <br/> |في Power Apps، يمكنك إدارة بيانات المؤسسة عن طريق تشغيل تطبيق أنشأته أو قام شخص آخر بإنشاءه ومشاركته معك. يتم تشغيل التطبيقات على الأجهزة المحمولة مثل الهواتف، أو يمكنك تشغيلها في مستعرض عن طريق فتح Dynamics 365. يمكنك إنشاء مجموعة غير محدودة من التطبيقات - كل ذلك دون تعلم لغة برمجة مثل C#.  <br/> |[التسجيل الذاتي للخدمة في Power Apps](/powerapps/maker/signup-for-powerapps) <br/> |[Microsoft Power Apps](https://go.microsoft.com/fwlink/p/?linkid=841462) <br/> |
|**Dynamics 365 for Financials** <br/> |احصل على حل كامل للأعمال والإدارة المالية للشركات الصغيرة والمتوسطة الحجم. تسهل Dynamics 365 for Financials عملية الطلب والبيع وإعداد الفواتير وإعداد التقارير، بدءا من اليوم الأول.  <br/> |[Microsoft Dynamics 365 for Financials](https://go.microsoft.com/fwlink/p/?linkid=841466) <br/> |[Microsoft Dynamics 365 for Financials](https://go.microsoft.com/fwlink/p/?linkid=841466) <br/> |
|**Microsoft Dynamics 365 للعمليات** <br/> |زيادة سرعة القيام بأعمالك. توفر أدوات ERP الكاملة في Dynamics 365 for Operations قابلية التوسع العالمية والذكاء الرقمي لمساعدتك على النمو بسرعة.  <br/> |[Microsoft Dynamics 365 للعمليات](https://go.microsoft.com/fwlink/p/?linkid=841467) <br/> |[Microsoft Dynamics 365 للعمليات](https://go.microsoft.com/fwlink/p/?linkid=841467) <br/> |
|**Microsoft AppSource** <br/> |Microsoft AppSource هي وجهة لتطبيقات الأعمال البرمجية كخدمة التي تم إنشاؤها على النظام الأساسي السحابي ل Microsoft. يتميز AppSource بمئات التطبيقات والوظائف الإضافية وحزم المحتويات التي توسع وظائف منتجات Microsoft مثل Azure و Dynamics 365 Office 365 و Power BI.  <br/> |[Microsoft AppSource](https://go.microsoft.com/fwlink/p/?linkid=841474) <br/> |[Microsoft AppSource](https://go.microsoft.com/fwlink/p/?linkid=841474) <br/> |
|**محفزات شركاء Microsoft** <br/> |توفر شبكة شركاء Microsoft ثلاثة أنواع من العضويات. يوفر كل نوع مجموعة من المزايا لمساعدة شركتك على النمو. عندما تحقق أهدافك، شارك في البرنامج على المستوى الذي يناسب احتياجاتك الفريدة للوصول إلى المزيد من المزايا وتطوير علاقتك معنا ومع الشركاء الآخرين في الشبكة.  <br/> |[محفزات شركاء Microsoft](https://go.microsoft.com/fwlink/p/?linkid=841469) <br/> |[محفزات شركاء Microsoft](https://go.microsoft.com/fwlink/p/?linkid=841469) <br/> |
|**مركز أعمال Microsoft** <br/> |مركز أعمال Microsoft هو المدخل للعملاء الذين اشتروا من خلال اتفاقية منتجات وخدمات Microsoft (MPSA). <br/> |[بداية سريعة: التسجيل في مركز أعمال Microsoft](https://go.microsoft.com/fwlink/p/?linkid=841479) <br/> |[مركز أعمال Microsoft](https://go.microsoft.com/fwlink/p/?linkid=841470) <br/> |
|**مركز خدمات الترخيص الحجمي من Microsoft** <br/> |يعرض مركز خدمات الترخيص المجمع من Microsoft التراخيص التي تم شراؤها ضمن اتفاقيات المؤسسة وحدد والتعليم (الحرم الجامعي أو المؤسسة التعليمية) والقيمة المفتوحة والترخيص المفتوح واتفاقيات الحقوق الملكية ل ISV.  <br/> |[موارد وتدريبات VLSC](https://www.microsoft.com/en-us/Licensing/existing-customer/vlsc-training-and-resources.aspx) <br/> |[مركز خدمات الترخيص الكلي](https://www.microsoft.com/Licensing/servicecenter/default.aspx) <br/> |
|**Minecraft Education Edition** <br/> |باستخدام Minecraft كقناة أساسية للتعلم، يمكن للمعلمين العمل وإلهام كل طالب لتحقيق المزيد، وحفز الشغف للتعلم. انضم إلى مجتمع من المعلمين يتعلمون كيفية استخدام Minecraft لإلغاء تأمين إمكانات الطلاب.  <br/> |[Minecraft Education Edition](https://go.microsoft.com/fwlink/p/?linkid=841480) <br/> |[Minecraft Education Edition](https://go.microsoft.com/fwlink/p/?linkid=841471) <br/> |
|**Microsoft Stream** <br/> |Upload مقاطع الفيديو ومشاركتها عبر مؤسستك لتحسين التواصل والمشاركة والتعلم.  <br/> |[تجربة التسجيل &amp; في اليوم 0](https://go.microsoft.com/fwlink/p/?linkid=841472) <br/> |[Microsoft Stream](https://go.microsoft.com/fwlink/p/?linkid=841473) <br/> |
|**Power Automate** <br/> |Power Automate هو منتج لمساعدتك على إعداد مهام سير العمل التلقائية بين التطبيقات والخدمات المفضلة لديك لمزامنة الملفات والحصول على الإعلامات وجمع البيانات والمزيد.  <br/> |[التسجيل في Power Automate](/power-automate/sign-up-sign-in) <br/> |[Power Automate](https://go.microsoft.com/fwlink/p/?linkid=841465) <br/> |
|**Power Virtual Agents** <br/> |Power Virtual Agents إلى تمكين الفرق من إنشاء روبوتات فعالة بسهولة باستخدام واجهة رسومية موجهة بدون تعليمات برمجية دون الحاجة إلى أدوات تحليل البيانات أو المطورين. Power Virtual Agents العديد من المشاكل الرئيسية المتعلقة ببناء الروبوتات في هذه الصناعة اليوم. فهو يزيل الهوة بين خبراء المواضيع وفرق التطوير التي تقوم ببناء الروبوتات، وبين زمن زمن الوصول الطويل بين الفرق التي تدرك مشكلة ما وتحديث الروبوت لمعالجتها.  <br/> |[تفاصيل الترخيص والوصول](/power-virtual-agents/requirements-licensing) <br/> |[التسجيل للحصول على Power Virtual Agents](https://aka.ms/TryPVA) <br/> |
|**Azure AD B2B** <br/> |يتيح لك التعاون في Azure Active Directory (Azure AD) للأعمال (B2B) دعوة مستخدمين خارجيين (أو "مستخدمين ضيوف") لاستخدام خدمات Azure AD المدفوعة. بعض الميزات مجانية، ولكن لأي ميزات Azure AD مدفوعة، يمكنك دعوة ما يصل إلى خمسة مستخدمين ضيوف لكل ترخيص إصدار Azure AD تملكه لموظف أو مستخدم غير ضيف في المستأجر. <br/> |[الخدمة الذاتية ل Azure AD B2B التسجيل في التعاون](/azure/active-directory/b2b/self-service-portal) <br/> |[إرشادات ترخيص التعاون في Azure Active Directory B2B](/azure/active-directory/b2b/licensing-guidance) <br/> |
