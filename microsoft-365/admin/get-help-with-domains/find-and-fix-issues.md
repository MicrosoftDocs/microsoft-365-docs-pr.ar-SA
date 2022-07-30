---
title: البحث عن المشاكل وإصلاحها بعد إضافة مجالك أو سجلات DNS
f1.keywords:
- NOCSH
ms.author: efrene
author: efrene
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
- Adm_O365_Setup
ms.custom:
- VSBFY23
- AdminSurgePortfolio
- okr_smb
- AdminTemplateSet
search.appverid:
- BCS160
- MET150
- MOE150
- GEA150
ms.assetid: 40398b0b-bdd0-4afd-ab5e-b5ae6b7990bf
description: تعلم كيفية تعقب أي مشاكل تواجهها أثناء إعداد مجال مخصص من خلال التأكد من إعداد سجلات DNS بشكل صحيح.
ms.openlocfilehash: 2e4f69b19fd87f45017a304414018995e90703a7
ms.sourcegitcommit: 2f6a7410e9919f753a759c1ada441141e18f06fd
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/30/2022
ms.locfileid: "67085148"
---
# <a name="find-and-fix-issues-after-adding-your-domain-or-dns-records"></a>البحث عن المشاكل وإصلاحها بعد إضافة مجالك أو سجلات DNS

 **[تحقق من الأسئلة المتداولة حول المجالات](../setup/domains-faq.yml)** إذا لم تعثر على ما تبحث عنه. 
  
قد يكون إعداد مجالك للعمل مع Microsoft 365 أمرا صعبا. نظام DNS غير تقليدي للعمل معه، ويؤثر إعداد DNS لمجالك على أنشطة الأعمال المهمة، مثل البريد الإلكتروني!

> [!NOTE]
> يمكنك التحقق من وجود مشاكل في مجالك عن طريق التحقق من حالته. انتقل إلى **"مجالات الإعداد** > **"** واعرض الإعلامات في عمود **"الحالة** ". إذا رأيت مشكلة، فحدد النقاط الثلاث (مزيد من الإجراءات)، ثم اختر **"التحقق من الصحة**". سيصف الجزء الذي يفتح أي مشاكل تحدث في مجالك.
  
## <a name="whats-going-on"></a>ماذا يحدث؟

- [هل يتعذر عليك التحقق من مجالك؟](#cant-verify-your-domain)
    
- [هل Outlook لا يعمل؟](#outlook-isnt-working)
    
- [تم تبديل البريد الإلكتروني للجميع إلى Microsoft 365 وتريد فقط تبديل بريدك الإلكتروني؟](#everyones-email-got-switched-to-microsoft-365-and-you-only-wanted-your-email-to-switch)

- [هل يتعذر عليك تأكيد حالة حساب المؤسسة التعليمية أو غير الربحية؟](#cant-confirm-non-profit-or-school-account-status)

- [هل الخدمات لا تعمل مع مجالك؟](#services-not-working-with-your-domain)
    
- [هل الوصول إلى موقعك على ويب لا يعمل؟](#accessing-your-website-isnt-working)

## <a name="cant-verify-your-domain"></a>هل يتعذر عليك التحقق من مجالك؟

هناك سببان شائعان لعدم عمل التحقق من المجال كما يجب:
  
1. **قيمة سجل التحقق غير صحيحة تماما.** تأكد من نسخ القيمة الدقيقة ولصقها في سجل التحقق من TXT لدى مضيف DNS. إحدى المشاكل الشائعة هي عدم تضمين جزء "MS=" من السجل. نحن بحاجة إلى ذلك أيضا! 
    
2. **لم يتم حفظ السجل.** في بعض مضيفي DNS، يجب عليك اتخاذ خطوة إضافية لحفظ ملف المنطقة (حيث يتم تخزين سجل DNS) بحيث يتم تحديثه عبر الإنترنت. تأكد من حفظ التغييرات حتى يتمكن Microsoft 365 من رؤية السجل والتحقق منه. 
    
3. **لم يتم تحديث السجل عبر الإنترنت.** عادة ما يستغرق الأمر بضع دقائق حتى نتمكن من رؤية السجل الجديد، ولكن قد يستغرق الأمر أحيانا بضع ساعات. 
    
## <a name="outlook-isnt-working"></a>هل Outlook لا يعمل؟

إذا قمت بإعداد سجل MX وسجلات DNS أخرى بشكل صحيح لمجالك، ولكن البريد لا يعمل، [فلنساعدك على إصلاح مشاكل Outlook](/exchange/troubleshoot/outlook-connectivity/outlook-connection-issues).
  
## <a name="everyones-email-got-switched-to-microsoft-365-and-you-only-wanted-your-email-to-switch"></a>تم تبديل البريد الإلكتروني للجميع إلى Microsoft 365 وتريد فقط تبديل بريدك الإلكتروني؟
<a name="BKMK_EmailSwitched"> </a>

عند إضافة مجالك إلى Microsoft 365، يتم عادة تحديث سجل MX لمجالك (بواسطةك أنت أو Microsoft 365) للإشارة إلى Microsoft 365، وستبدأ جميع رسائل البريد الإلكتروني المرسلة إلى هذا المجال في الانتهاء من Microsoft 365. تأكد من إنشاء علب بريد في Microsoft 365 لكل شخص لديه بريد إلكتروني على مجالك قبل تغيير سجل MX.
  
ماذا لو كنت لا تريد نقل البريد الإلكتروني لجميع الأشخاص في مجالك إلى Microsoft 365؟ يمكنك اتخاذ خطوات [للبدء في Microsoft 365 باستخدام عدد قليل من عناوين البريد الإلكتروني بدلا من ذلك](../setup/domains-faq.yml).
  
## <a name="cant-confirm-non-profit-or-school-account-status"></a>هل يتعذر عليك تأكيد حالة حساب المؤسسة التعليمية أو غير الربحية؟
<a name="BKMK_validateAcct"> </a>

هناك بعض السيناريوهات عندما تحتاج فقط إلى التحقق من مجال مؤسستك وعدم إعداد أي خدمات. على سبيل المثال، لإثبات ل Microsoft 365 أن مؤسستك مؤهلة لاشتراك مؤسسة تعليمية.
  
اطلع على الإرشادات الواردة في [التحقق من مجال Microsoft 365 لإثبات الملكية أو حالة المؤسسات غير الربحية أو التعليم، أو لتنشيط Yammer](../setup/domains-faq.yml) للتأكد من إكمال جميع الخطوات المطلوبة. الأمر مختلف قليلا لكل موقف. 
  
## <a name="services-not-working-with-your-domain"></a>هل الخدمات لا تعمل مع مجالك؟

يمكننا مساعدتك في تعقب المشاكل المتعلقة بإعداد DNS لمجالك. سيعرض لك مستكشف أخطاء المجالات ومصلحها في Microsoft 365 أي سجلات تحتاج إلى إصلاح، وما يجب تعيين السجلات إليه بالضبط. 

> [!TIP]
> هل قمت بإعداد DNS بشكل صحيح، ولكن البريد لا يعمل في Outlook على سطح المكتب؟ اطلع على [سيناريوهات تدفق البريد المختلفة التي يمكنك استخدامها مع Microsoft 365](/exchange/mail-flow-best-practices/mail-flow-best-practices) للتأكد من أن لديك أشياء تم إعدادها بشكل صحيح لعملك. أو احصل على المزيد من التعليمات حول استكشاف الأخطاء وإصلاحها باستخدام البريد الإلكتروني هنا: [إصلاح مشاكل Outlook](/exchange/troubleshoot/outlook-connectivity/outlook-connection-issues). 
  
## <a name="accessing-your-website-isnt-working"></a>هل الوصول إلى موقعك على ويب لا يعمل؟

إذا قمت بتصحيح أي مشكلات في DNS ولا تزال تواجه مشكلة، فجرب أحد الإجراءات التالية.
  
- يتعذر على الأشخاص الوصول إلى موقعك على ويب في *contoso.com*: [تعقب مشاكل موقع الويب](../setup/add-domain.md)
    
- لا يمكنك تحديث سجل A أو سجل CNAME للإشارة إلى موقعك على ويب: [تحديث سجلات DNS المخصصة في Microsoft 365](../setup/add-domain.md)

## <a name="related-content"></a>المحتويات ذات الصلة

[استكشاف الأخطاء وإصلاحها: تدقيق البيانات على تغيير المجال المتحقق منه](/azure/active-directory/reports-monitoring/troubleshoot-audit-data-verified-domain) (مقالة)\
[الأسئلة المتداولة حول المجالات](../setup/domains-faq.yml) (مقالة)

