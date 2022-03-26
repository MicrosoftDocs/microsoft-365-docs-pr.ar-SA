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
- AdminSurgePortfolio
- okr_smb
- AdminTemplateSet
search.appverid:
- BCS160
- MET150
- MOE150
- GEA150
ms.assetid: 40398b0b-bdd0-4afd-ab5e-b5ae6b7990bf
description: تعرف على كيفية تعقب أي مشاكل تواجهها أثناء إعداد مجال مخصص من خلال التأكد من إعداد سجلات DNS بشكل صحيح.
ms.openlocfilehash: 7fa5a18ff0e4b7f0db8749f5659fefdd89cb3fcd
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/08/2022
ms.locfileid: "63571020"
---
# <a name="find-and-fix-issues-after-adding-your-domain-or-dns-records"></a>البحث عن المشاكل وإصلاحها بعد إضافة مجالك أو سجلات DNS

 **[تحقق من الأسئلة الشائعة](../setup/domains-faq.yml)** حول المجالات إذا لم تعثر على ما تبحث عنه. 
  
قد يكون إعداد مجالك للعمل مع Microsoft 365 صعبا. لا يمكن استخدام نظام DNS بشكل رائع، كما يؤثر إعداد DNS لمجالك على أنشطة الأعمال المهمة، مثل البريد الإلكتروني!

> [!NOTE]
> يمكنك التحقق من وجود مشاكل في مجالك من خلال التحقق من حالة المجال. انتقل إلى **SetupDomains**  >  وانظر الإعلامات في **عمود** الحالة. إذا رأيت مشكلة، فحدد النقاط الثلاث (المزيد من الإجراءات)، ثم اختر **التحقق من الصحة**. سيصف الجزء الذي يتم فتحه أي مشاكل تحدث في مجالك.
  
## <a name="whats-going-on"></a>ماذا يحدث؟

- [هل لا يمكنك التحقق من مجالك؟](#cant-verify-your-domain)
    
- [Outlook لا تعمل؟](#outlook-isnt-working)
    
- [تم تبديل البريد الإلكتروني الخاص بالجميع إلى Microsoft 365 وأردت فقط تبديل بريدك الإلكتروني؟](#everyones-email-got-switched-to-microsoft-365-and-you-only-wanted-your-email-to-switch)

- [هل لا يمكنك تأكيد حالة حساب المؤسسات غير الربحية أو المدرسة؟](#cant-confirm-non-profit-or-school-account-status)

- [هل الخدمات لا تعمل مع مجالك؟](#services-not-working-with-your-domain)
    
- [هل الوصول إلى موقعك على ويب لا يعمل؟](#accessing-your-website-isnt-working)

## <a name="cant-verify-your-domain"></a>هل لا يمكنك التحقق من مجالك؟

ثمة سببان شائعان وراء عدم عمل التحقق من المجال كما يجب:
  
1. **قيمة سجل التحقق غير صحيحة تماما.** تحقق من أنك نسخت القيمة الدقيقة ولصقتها في سجل التحقق من صحة TXT لدى مضيف DNS. لا تتضمن إحدى المشاكل الشائعة الجزء "MS=" من السجل. نحتاج إلى ذلك أيضا! 
    
2. **لم يتم حفظ السجل.** في بعض مضيفي DNS، يجب عليك اتخاذ خطوة إضافية لحفظ ملف المنطقة (حيث يتم تخزين سجل DNS) بحيث يتم تحديثه عبر الإنترنت. تأكد من حفظ التغييرات حتى Microsoft 365 رؤية السجل والتحقق منه. 
    
3. **لم يتم تحديث السجل عبر الإنترنت.** يستغرق الأمر عادة بضع دقائق لكي نتمكن من رؤية السجل الجديد، ولكن قد يستغرق ذلك أحيانا بضع ساعات. 
    
## <a name="outlook-isnt-working"></a>Outlook لا تعمل؟

إذا قمت بإعداد سجل MX وسجلات DNS الأخرى بشكل صحيح لمجالك، ولكن البريد لا يعمل، فدعنا نساعدك في إصلاح [Outlook مشاكلك](/exchange/troubleshoot/outlook-connectivity/outlook-connection-issues).
  
## <a name="everyones-email-got-switched-to-microsoft-365-and-you-only-wanted-your-email-to-switch"></a>تم تبديل البريد الإلكتروني الخاص بالجميع إلى Microsoft 365 وأردت فقط تبديل بريدك الإلكتروني؟
<a name="BKMK_EmailSwitched"> </a>

عند إضافة مجالك إلى Microsoft 365، يتم عادة تحديث سجل MX لمجالك (من قبلك أو بواسطة Microsoft 365) بحيث يشير إلى Microsoft 365، وستبدأ جميع رسائل البريد الإلكتروني المرسلة إلى هذا المجال في Microsoft 365. تأكد من إنشاء علب بريد في Microsoft 365 لكل شخص لديه بريد إلكتروني على مجالك قبل تغيير سجل MX.
  
ماذا لو كنت لا تريد نقل البريد الإلكتروني لجميع الأشخاص على مجالك Microsoft 365؟ يمكنك تنفيذ الخطوات اللازمة Microsoft 365 [باستخدام بعض عناوين البريد الإلكتروني بدلا من ذلك](../setup/domains-faq.yml).
  
## <a name="cant-confirm-non-profit-or-school-account-status"></a>هل لا يمكنك تأكيد حالة حساب المؤسسات غير الربحية أو المدرسة؟
<a name="BKMK_validateAcct"> </a>

هناك بعض السيناريوهات عندما تحتاج فقط إلى التحقق من مجال مؤسستك وليس إعداد أي خدمات. على سبيل المثال، لإثبات Microsoft 365 أن مؤسستك مؤهلة للحصول على اشتراك مدرسة.
  
اطلع على الإرشادات في التحقق من Microsoft 365 [الخاص](../setup/domains-faq.yml) بك لإثبات الملكية أو حالة المؤسسات غير الربحية أو التعليم، أو لتنشيط Yammer للتأكد من أنك أكملت كل الخطوات المطلوبة. الأمر مختلف بعض الشيء لكل حالة. 
  
## <a name="services-not-working-with-your-domain"></a>هل الخدمات لا تعمل مع مجالك؟

يمكننا مساعدتك في تعقب المشاكل المتعلقة بإعداد DNS لمجالك. سيعرض لك مصلح المجالات ومصلحها في Microsoft 365 أي سجلات تحتاج إلى تصحيح، وما هي السجلات التي يجب تعيينها بالضبط. 

> [!TIP]
> هل تم إعداد DNS بشكل صحيح، ولكن البريد لا يعمل في Outlook سطح المكتب؟ اطلع على [سيناريوهات](/exchange/mail-flow-best-practices/mail-flow-best-practices) تدفق البريد المختلفة التي يمكنك Microsoft 365 للتأكد من إعداد الأشياء بشكل صحيح للأعمال. أو احصل على المزيد من تعليمات استكشاف الأخطاء وإصلاحها باستخدام البريد الإلكتروني هنا: [Outlook مشاكلك](/exchange/troubleshoot/outlook-connectivity/outlook-connection-issues). 
  
## <a name="accessing-your-website-isnt-working"></a>هل الوصول إلى موقعك على ويب لا يعمل؟

إذا قمت ب إصلاح أي مشاكل DNS ولا تزال تواجه مشكلة، فجرب أحد الخطوات التالية.
  
- لا يمكن للأشخاص الوصول إلى موقعك على *ويب في contoso.com*: [تعقب مشاكل موقع ويب](../setup/add-domain.md)
    
- لا يمكنك تحديث سجل A أو سجل CNAME لتشير إلى موقعك على ويب: تحديث [سجلات DNS المخصصة في Microsoft 365](../setup/add-domain.md)

## <a name="related-content"></a>المحتوى ذي الصلة

[استكشاف الأخطاء وإصلاحها: تدقيق البيانات عند التحقق](/azure/active-directory/reports-monitoring/troubleshoot-audit-data-verified-domain) من تغيير المجال (مقالة)\
[الأسئلة الشائعة حول المجالات](../setup/domains-faq.yml) (مقالة)

