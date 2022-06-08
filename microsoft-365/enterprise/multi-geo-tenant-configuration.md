---
title: تكوين مستأجر Microsoft 365 Multi-Geo
ms.reviewer: adwood
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.collection:
- SPO_Content
- Strat_SP_gtc
f1.keywords:
- NOCSH
ms.custom: seo-marvel-apr2020
ms.localizationpriority: medium
description: في هذه المقالة، تعرف على كيفية إضافة مواقع الأقمار الصناعية وتكوين المستأجر ل Microsoft 365 Multi-Geo.
ms.openlocfilehash: 2a82872e7c917421c0eb418cf0582eb33d2a53c9
ms.sourcegitcommit: 61bdfa84f2d6ce0b61ba5df39dcde58df6b3b59d
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 06/08/2022
ms.locfileid: "65941185"
---
# <a name="microsoft-365-multi-geo-tenant-configuration"></a>تكوين مستأجر Microsoft 365 Multi-Geo

قبل تكوين المستأجر ل Microsoft 365 Multi-Geo، تأكد من قراءة [الخطة ل Microsoft 365 Multi-Geo](plan-for-multi-geo.md). لاتباع الخطوات الواردة في هذه المقالة، ستحتاج إلى قائمة بالمواقع الجغرافية التي تريد تمكينها كمواقع أقمار صناعية، ومستخدمي الاختبار الذين تريد توفيرهم لتلك المواقع.

## <a name="add-the-multi-geo-capabilities-in-your-microsoft-365-plan-to-your-tenant"></a>إضافة الإمكانات متعددة المناطق الجغرافية في خطة Microsoft 365 إلى المستأجر

لاستخدام Microsoft 365 Multi-Geo، تحتاج إلى _الإمكانات متعددة المناطق الجغرافية في خطة Microsoft 365_ . اعمل مع فريق حسابك لإضافة هذه الخطة إلى المستأجر. سيقوم فريق حسابك بتوصيلك بمتخصص الترخيص المناسب وتكوين المستأجر الخاص بك.

لاحظ أن _الإمكانات متعددة المناطق الجغرافية في خطة Microsoft 365_ هي خطة خدمة على مستوى المستخدم. تحتاج إلى ترخيص لكل مستخدم تريد استضافته في موقع قمر صناعي. يمكنك إضافة المزيد من التراخيص بمرور الوقت أثناء إضافة مستخدمين في مواقع الأقمار الصناعية.

بمجرد توفير المستأجر الخاص بك باستخدام  _الإمكانات متعددة المناطق الجغرافية في خطة Microsoft 365_ ، ستصبح علامة تبويب **المواقع الجغرافية** متوفرة في مركزي إدارة OneDrive وSharePoint.

## <a name="add-satellite-locations-to-your-tenant"></a>إضافة مواقع الأقمار الصناعية إلى المستأجر الخاص بك

يجب إضافة موقع قمر صناعي لكل موقع جغرافي تريد تخزين البيانات فيه. يتم عرض المواقع الجغرافية المتوفرة في الجدول التالي:

[!INCLUDE [Microsoft 365 Multi-Geo locations](../includes/microsoft-365-multi-geo-locations.md)]

![لقطة شاشة لصفحة المواقع الجغرافية في مركز إدارة SharePoint.](../media/sharepoint-multi-geo-admin-center.png)

لإضافة موقع قمر صناعي

1. افتح مركز إدارة SharePoint. وانتقل إلى <a href="https://go.microsoft.com/fwlink/?linkid=2185076" target="_blank">**المواقع الجغرافية**</a>.

1. حدد **"إضافة موقع**".

1. حدد الموقع الذي تريد إضافته، ثم حدد **"التالي**".

1. اكتب المجال الذي تريد استخدامه مع الموقع الجغرافي، ثم حدد **"إضافة**".

1. حدد **"إغلاق**".

قد يستغرق التوفير من بضع ساعات حتى 72 ساعة، اعتمادا على حجم المستأجر الخاص بك. بمجرد اكتمال توفير موقع قمر صناعي، ستتلقى تأكيد بريد إلكتروني. عندما يظهر الموقع الجغرافي الجديد باللون الأزرق على الخريطة على علامة تبويب **المواقع الجغرافية** في مركز إدارة OneDrive، يمكنك المتابعة لتعيين موقع البيانات المفضل للمستخدمين إلى هذا الموقع الجغرافي.

> [!IMPORTANT]
> سيتم إعداد موقع القمر الصناعي الجديد مع الإعدادات الافتراضية. سيسمح لك هذا بتكوين موقع الأقمار الصناعية هذا بما يتناسب مع احتياجات التوافق المحلية الخاصة بك.

## <a name="setting-users-preferred-data-location"></a>تعيين موقع البيانات المفضل للمستخدمين
<span id="_Setting_a_User's" class="anchor"><span id="_Toc508109326" class="anchor"></span></span>

بمجرد تمكين مواقع الأقمار الصناعية المطلوبة، يمكنك تحديث حسابات المستخدمين لاستخدام موقع البيانات المفضل المناسب. نوصي بتعيين موقع بيانات مفضل لكل مستخدم، حتى لو كان هذا المستخدم يقيم في الموقع المركزي.

> [!IMPORTANT]
> إذا تم تعيين موقع البيانات المفضل للمستخدم إلى موقع لم يتم تكوينه كموقع تابع أو الموقع المركزي، فسيعين النظام افتراضيا إلى الموقع المركزي عند توفير مواقع OneDrive ومواقع SharePoint وعلب بريد المجموعة.

> [!TIP]
> نوصي ببدء عمليات التحقق من الصحة مع مستخدم اختبار أو مجموعة صغيرة من المستخدمين قبل طرح متعدد المناطق الجغرافية لمؤسستك الأوسع.

في Azure Active Directory (Azure AD) هناك نوعان من كائنات المستخدم: المستخدمين السحابيين فقط والمستخدمين المتزامنين. الرجاء اتباع الإرشادات المناسبة لنوع المستخدم.

### <a name="synchronize-users-preferred-data-location-using-azure-ad-connect"></a>مزامنة موقع البيانات المفضل للمستخدم باستخدام Azure AD Connect

إذا تمت مزامنة مستخدمي شركتك من نظام Active Directory محلي إلى Azure AD، فيجب تعبئة PreferredDataLocation في AD ومزامنتها مع Azure AD.

اتبع العملية في [مزامنة Azure Active Directory Connect: تكوين موقع البيانات المفضل لموارد Microsoft 365](/azure/active-directory/hybrid/how-to-connect-sync-feature-preferreddatalocation) لتكوين مزامنة موقع البيانات المفضل من خدمات مجال Active Directory المحلية (AD DS) إلى Azure AD.

نوصي بتضمين تعيين موقع البيانات المفضل للمستخدم كجزء من سير عمل إنشاء المستخدم القياسي.

> [!IMPORTANT]
> بالنسبة للمستخدمين الجدد الذين لم يتم توفير OneDrive لهم، قم بترخيص الحساب وانتظر 48 ساعة على الأقل بعد مزامنة PDL الخاص بالمستخدم مع Azure AD ليتم نشر التغييرات قبل تسجيل دخول المستخدم إلى OneDrive for Business. (يؤدي تعيين موقع البيانات المفضل قبل تسجيل دخول المستخدم لتوفير OneDrive for Business إلى ضمان توفير OneDrive الجديد للمستخدم في الموقع الصحيح.)

### <a name="setting-preferred-data-location-for-cloud-only-users"></a>تعيين موقع البيانات المفضل لمستخدمي السحابة فقط

إذا لم تتم مزامنة مستخدمي شركتك من نظام Active Directory محلي إلى Azure AD، بمعنى أنه تم إنشاؤهم في Microsoft 365 أو Azure AD، فيجب تعيين PDL باستخدام وحدة Microsoft Azure Active Directory النمطية ل Windows PowerShell.

تتطلب الإجراءات في هذا القسم [وحدة Microsoft Azure Active Directory النمطية ل Windows PowerShell](https://www.powershellgallery.com/packages/MSOnline/1.1.166.0). إذا كان لديك بالفعل هذه الوحدة النمطية مثبتة، فيرجى التأكد من التحديث إلى أحدث إصدار.

1. [الاتصال وتسجيل الدخول](/connect-to-microsoft-365-powershell?view=o365-worldwide#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell&preserve-view=true) باستخدام مجموعة من بيانات اعتماد المسؤول العام للمستأجر الخاص بك.

2. استخدم [Set-MsolUser](/powershell/module/msonline/set-msoluser?view=azureadps-1.0&preserve-view=true) cmdlet لتعيين موقع البيانات المفضل لكل مستخدم. على سبيل المثال:

   ```powershell
   Set-MsolUser -UserPrincipalName Robyn.Buckley@Contoso.com -PreferredDatalocation EUR
   ```

    يمكنك التحقق للتأكد من تحديث موقع البيانات المفضل بشكل صحيح باستخدام Get-MsolUser cmdlet. على سبيل المثال:

   ```powershell
   (Get-MsolUser -UserPrincipalName Robyn.Buckley@Contoso.com).PreferredDatalocation
   ```

![لقطة شاشة لنافذة PowerShell تعرض set-msoluser.](../media/multi-geo-tenant-configuration-image3.png)

نوصي بتضمين تعيين موقع البيانات المفضل للمستخدم كجزء من سير عمل إنشاء المستخدم القياسي.

> [!IMPORTANT]
> بالنسبة للمستخدمين الجدد الذين لم يتم توفير OneDrive لهم، قم بترخيص الحساب وانتظر 48 ساعة على الأقل بعد تعيين PDL الخاص بالمستخدم لنشر التغييرات قبل تسجيل دخول المستخدم إلى OneDrive. (يؤدي تعيين موقع البيانات المفضل قبل تسجيل دخول المستخدم لتوفير OneDrive for Business إلى ضمان توفير OneDrive الجديد للمستخدم في الموقع الصحيح.)

## <a name="onedrive-provisioning-and-the-effect-of-pdl"></a>توفير OneDrive وتأثير PDL

إذا كان لدى المستخدم بالفعل موقع OneDrive تم إنشاؤه في المستأجر، فلن يؤدي تعيين PDL الخاص به إلى نقل OneDrive الموجود لديه تلقائيا. لنقل OneDrive الخاص بالمستخدم، راجع [النقل الجغرافي ل OneDrive for Business](move-onedrive-between-geo-locations.md).

> [!NOTE]
> يقوم Exchange Online تلقائيا بنقل علبة بريد المستخدم إذا تغيرت PLD ولم يعد MailboxRegion يطابق رمز الموقع الجغرافي لقاعدة بيانات علبة البريد. لمزيد من المعلومات، راجع [إدارة علب بريد Exchange Online في بيئة متعددة المناطق الجغرافية](./administering-exchange-online-multi-geo.md).

إذا لم يكن لدى المستخدم موقع OneDrive داخل المستأجر، فسيتم توفير OneDrive له وفقا لقيمة PDL الخاصة به، على افتراض أن PDL للمستخدم يطابق أحد مواقع الأقمار الصناعية للشركة.

## <a name="configuring-multi-geo-search"></a>تكوين البحث متعدد المناطق الجغرافية

سيكون للمستأجر متعدد المناطق الجغرافية قدرات بحث مجمعة تسمح لاستعلام البحث بإرجاع النتائج من أي مكان داخل المستأجر.

بشكل افتراضي، سترجع عمليات البحث من نقاط الإدخال هذه النتائج المجمعة، على الرغم من أن كل فهرس بحث موجود داخل موقعه الجغرافي ذي الصلة:

- OneDrive for Business
- الخوض
- SharePoint Home
- مركز البحث

بالإضافة إلى ذلك، يمكن تكوين قدرات البحث متعددة المناطق الجغرافية لتطبيقات البحث المخصصة التي تستخدم واجهة برمجة تطبيقات البحث في SharePoint.

الرجاء مراجعة [تكوين البحث عن OneDrive for Business Multi-Geo](configure-search-for-multi-geo.md) للحصول على إرشادات تتضمن أي قيود واختلافات.

## <a name="validating-the-microsoft-365-multi-geo-configuration"></a>التحقق من صحة تكوين Microsoft 365 Multi-Geo

فيما يلي بعض حالات الاستخدام الأساسية التي قد ترغب في تضمينها في خطة التحقق من الصحة قبل طرح Microsoft 365 Multi-Geo إلى شركتك على نطاق واسع. بمجرد الانتهاء من هذه الاختبارات وأي حالات استخدام إضافية ذات صلة بشركتك، يمكنك اختيار الانتقال إلى إضافة المستخدمين في مجموعة الإصدار التجريبي الأولي.

**OneDrive for Business**:

حدد OneDrive من مشغل تطبيق Microsoft 365 وتأكد من توجيهك تلقائيا إلى الموقع الجغرافي المناسب للمستخدم، استنادا إلى PDL الخاص بالمستخدم. يجب أن يبدأ OneDrive for Business الآن في التوفير في هذا الموقع. بمجرد التزويد، حاول تحميل بعض المستندات وتنزيلها.

**تطبيق OneDrive للأجهزة المحمولة**:

سجل الدخول إلى تطبيق OneDrive للأجهزة المحمولة باستخدام بيانات اعتماد حساب الاختبار. تأكد من أنه يمكنك رؤية ملفات OneDrive for Business الخاصة بك ويمكنك التفاعل معها من جهازك المحمول.

**عميل مزامنة OneDrive**:

تأكد من أن عميل مزامنة OneDrive يكتشف تلقائيا موقعك الجغرافي في OneDrive for Business عند تسجيل الدخول. إذا كنت بحاجة إلى تنزيل عميل المزامنة، يمكنك النقر فوق **"مزامنة** " في مكتبة OneDrive.

**تطبيقات Office**:

تأكد من أنه يمكنك الوصول إلى OneDrive for Business عن طريق تسجيل الدخول من تطبيق Office، مثل Word. افتح تطبيق Office وحدد "OneDrive – \<TenantName\>". سيكتشف Office موقع OneDrive ويعرض لك الملفات التي يمكنك فتحها.

**المشاركة**:

حاول مشاركة ملفات OneDrive. تأكد من أن منتقي الأشخاص يعرض لك جميع مستخدمي SharePoint عبر الإنترنت بغض النظر عن موقعهم الجغرافي.
