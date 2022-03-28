---
title: Microsoft 365 المستأجر متعدد الجغرافيا
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
description: في هذه المقالة، تعرف على كيفية إضافة مواقع الأقمار الصناعية وتكوين المستأجر Microsoft 365 Multi-Geo.
ms.openlocfilehash: 9842ff2295a64f544940f579d732c688735ae341
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/08/2022
ms.locfileid: "63575294"
---
# <a name="microsoft-365-multi-geo-tenant-configuration"></a>Microsoft 365 المستأجر متعدد الجغرافيا

قبل تكوين المستأجر Microsoft 365 Multi-Geo، تأكد من قراءة خطة Microsoft 365 [Multi-Geo](plan-for-multi-geo.md). لاتباع الخطوات الواردة في هذه المقالة، ستحتاج إلى قائمة بالمواقع الجغرافية التي تريد تمكينها كمواضع أقمار صناعية، ومستخدمي الاختبار الذين تريد توفيرهم لتلك المواقع.

## <a name="add-the-multi-geo-capabilities-in-your-microsoft-365-plan-to-your-tenant"></a>إضافة "القدرات الجغرافية المتعددة" في خطة Microsoft 365 إلى المستأجر

لاستخدام "Microsoft 365 الجغرافيا المتعددة"، ستحتاج إلى "القدرات الجغرافية المتعددة" _Microsoft 365_ التخطيطية. اعمل مع فريق حسابك لإضافة هذه الخطة إلى المستأجر. سيتصل فريق حسابك بمتخصص الترخيص المناسب ويحصل على المستأجر الذي تريد تكوينه.

تجدر الإشارة إلى أن "القدرات الجغرافية _المتعددة" في_ Microsoft 365 هي خطة خدمة على مستوى المستخدم. أنت بحاجة إلى ترخيص لكل مستخدم تريد استضافته في موقع القمر الصناعي. يمكنك إضافة المزيد من التراخيص مع مرور الوقت عند إضافة مستخدمين إلى مواقع الأقمار الصناعية.

بمجرد أن يتم توفير المستأجر الخاص بك باستخدام "القدرات الجغرافية المتعددة" في خطة Microsoft 365، ستصبح علامة التبويب  مواقع الجغرافيا متوفرة في OneDrive SharePoint الإدارة.

## <a name="add-satellite-locations-to-your-tenant"></a>إضافة مواقع الأقمار الصناعية إلى المستأجر

يجب إضافة موقع قمر صناعي لكل موقع جغرافي حيث تريد تخزين البيانات. يتم عرض المواقع الجغرافية المتوفرة في الجدول التالي:

[!INCLUDE [Microsoft 365 Multi-Geo locations](../includes/microsoft-365-multi-geo-locations.md)]

![لقطة شاشة لصفحة المواقع الجغرافية في SharePoint إدارة الموقع.](../media/sharepoint-multi-geo-admin-center.png)

لإضافة موقع قمر صناعي

1. افتح SharePoint الإدارة. واذهب إلى <a href="https://go.microsoft.com/fwlink/?linkid=2185076" target="_blank">**مواقع Geo**</a>.

1. حدد **إضافة موقع**.

1. حدد الموقع الذي تريد إضافته، ثم حدد **التالي**.

1. اكتب المجال الذي تريد استخدامه مع الموقع الجغرافي، ثم حدد **إضافة**.

1. حدد **إغلاق**.

قد يستغرق توفيره من بضع ساعات حتى 72 ساعة، استنادا إلى حجم المستأجر. بمجرد اكتمال عملية توفير موقع القمر الصناعي، ستتلقى تأكيدا للبريد الإلكتروني. عندما يظهر الموقع الجغرافي الجديد باللون الأزرق على الخريطة على علامة التبويب مواقع جغرافية  في مركز إدارة OneDrive، يمكنك المتابعة لتعيين موقع البيانات المفضل للمستخدمين إلى الموقع الجغرافي. 

> [!IMPORTANT]
> سيتم إعداد موقع القمر الصناعي الجديد باستخدام الإعدادات الافتراضية. سيسمح لك ذلك بتكوين موقع القمر الصناعي هذا بما يلائم احتياجات التوافق المحلية.

## <a name="setting-users-preferred-data-location"></a>تعيين موقع البيانات المفضلة للمستخدمين
<span id="_Setting_a_User's" class="anchor"><span id="_Toc508109326" class="anchor"></span></span> 

بمجرد تمكين مواقع الأقمار الصناعية المطلوبة، يمكنك تحديث حسابات المستخدمين لاستخدام موقع البيانات المفضل المناسب. نوصي بتعيين موقع بيانات مفضل لكل مستخدم، حتى لو كان هذا المستخدم يقيم في الموقع المركزي.

> [!IMPORTANT]
> إذا تم تعيين موقع البيانات المفضل للمستخدم إلى موقع لم يتم تكوينه كمواقع أقمار صناعية أو موقع مركزي، سيتم تعيين النظام بشكل افتراضي إلى الموقع المركزي عند توفير OneDrive SharePoint ومواقع علب بريد المجموعة.

> [!TIP]
> نوصي ببدء عمليات التحقق من الصحة مع مستخدم اختباري أو مجموعة صغيرة من المستخدمين قبل طرح بيانات متعددة الجغرافيا في مؤسستك على نطاق أوسع.

في Azure Active Directory (Azure AD) يوجد نوعان من كائنات المستخدمين: مستخدمو السحابة فقط والمستخدمون المتزامنون. يرجى اتباع الإرشادات المناسبة لنوع المستخدم.

### <a name="synchronize-users-preferred-data-location-using-azure-ad-connect"></a>مزامنة موقع البيانات المفضلة للمستخدم باستخدام Azure AD الاتصال 

إذا كان مستخدمو شركتك متزامنين من نظام Active Directory موقعي إلى Azure AD، فيجب ملء المفضلةDataLocation الخاصة بهم في AD ومزامنتها مع Azure AD.

اتبع العملية في مزامنة [Azure Active Directory الاتصال:](/azure/active-directory/hybrid/how-to-connect-sync-feature-preferreddatalocation) تكوين موقع البيانات المفضلة للموارد Microsoft 365 لتكوين مزامنة موقع البيانات المفضلة من خدمات مجال Active Directory المحلية (AD DS) إلى Azure AD.

نوصي بتضمين تعيين موقع البيانات المفضلة للمستخدم كجزء من سير عمل إنشاء المستخدم القياسي.

> [!IMPORTANT]
> للمستخدمين الجدد الذين لم يتم توفير OneDrive، قم بتراخيص الحساب وانتظر 48 ساعة على الأقل بعد مزامنة PDL الخاص بالمستخدم مع Azure AD لنشر التغييرات قبل أن يسجل المستخدم دخوله إلى OneDrive for Business. (يضمن تعيين موقع البيانات المفضل قبل تسجيل المستخدم دخوله لتوفير بيانات OneDrive for Business توفير البيانات الجديدة OneDrive المستخدم في الموقع الصحيح.)

### <a name="setting-preferred-data-location-for-cloud-only-users"></a>تعيين موقع البيانات المفضلة لمستخدمي السحابة فقط 

إذا لم يتم مزامنة مستخدمي شركتك من نظام Active Directory موقعي إلى Azure AD، مما يعني أنه تم إنشاؤهم في Microsoft 365 أو Azure AD، فيجب تعيين PDL باستخدام وحدة Microsoft Azure Active Directory النمطية Windows PowerShell.

تتطلب الإجراءات في هذا القسم Microsoft Azure Active Directory [الوحدة النمطية Windows PowerShell النمطية](https://www.powershellgallery.com/packages/MSOnline/1.1.166.0). إذا كانت هذه الوحدة النمطية مثبتة لديك بالفعل، فالرجاء التأكد من التحديث إلى الإصدار الأخير.

1.  [الاتصال تسجيل الدخول](/powershell/connect-to-microsoft-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell) باستخدام مجموعة من بيانات اعتماد المسؤول العام للمستأجر.

2.  استخدم [الأمر Cmdlet Set-MsolUser](/powershell/msonline/v1/set-msoluser) لتعيين موقع البيانات المفضل لكل مستخدم. على سبيل المثال:

    `Set-MsolUser -userprincipalName Robyn.Buckley@Contoso.com -PreferredDatalocation EUR`

    يمكنك التحقق للتأكد من تحديث موقع البيانات المفضلة بشكل صحيح باستخدام Get-MsolUser cmdlet. على سبيل المثال:

    `(Get-MsolUser -userprincipalName Robyn.Buckley@Contoso.com).PreferredDatalocation`

![لقطة شاشة من نافذة PowerShell تظهر set-msoluser.](../media/multi-geo-tenant-configuration-image3.png)

نوصي بتضمين تعيين موقع البيانات المفضلة للمستخدم كجزء من سير عمل إنشاء المستخدم القياسي.

> [!IMPORTANT]
> للمستخدمين الجدد الذين لم يتم توفير OneDrive، قم بتراخيص الحساب وانتظر 48 ساعة على الأقل بعد تعيين PDL الخاص بالمستخدم حتى يتم نشر التغييرات قبل أن يسجل المستخدم دخوله OneDrive. (يضمن تعيين موقع البيانات المفضل قبل تسجيل المستخدم دخوله لتوفير بيانات OneDrive for Business توفير البيانات الجديدة OneDrive المستخدم في الموقع الصحيح.)

## <a name="onedrive-provisioning-and-the-effect-of-pdl"></a>OneDrive توفير وتأثير PDL

إذا كان لدى المستخدم OneDrive تم إنشاؤه في المستأجر، فإن تعيين PDL لن يؤدي تلقائيا إلى نقل بياناته OneDrive. لنقل بيانات المستخدم OneDrive، راجع OneDrive for Business [Geo Move](move-onedrive-between-geo-locations.md).

> [!NOTE]
> Exchange Online تغيير موقع علبة بريد المستخدم تلقائيا إذا تم تغيير PLD ولم تعد علبة البريد المنطقة تطابق التعليمات البرمجية للموقع الجغرافي لقاعدة بيانات علبة البريد. لمزيد من المعلومات، [راجع Exchange Online علب البريد في بيئة متعددة الجغرافيا](./administering-exchange-online-multi-geo.md).

إذا لم يكن لدى المستخدم موقع OneDrive ضمن نطاق المستأجر، سيتم توفير OneDrive له وفقا لقيمته في PDL، مع افتراض أن PDL للمستخدم يتطابق مع أحد مواقع الأقمار الصناعية للشركة.

## <a name="configuring-multi-geo-search"></a>تكوين بحث متعدد الجغرافيا

سيكون لدى المستأجر متعدد الجغرافيا قدرات بحث مجمعة تسمح لاستعلام البحث بإرجاع النتائج من أي مكان ضمن نطاق المستأجر.

بشكل افتراضي، رجع عمليات البحث من نقاط الإدخال هذه النتائج التجميعية، على الرغم من وجود كل فهرس بحث ضمن موقعه الجغرافي ذي الصلة:

- OneDrive for Business

- Delve

- SharePoint الرئيسية

- مركز البحث

بالإضافة إلى ذلك بحث في مواقع جغرافية متعددة يمكن تكوين قدرات تطبيقات البحث المخصصة التي تستخدم SharePoint API للبحث.

الرجاء مراجعة [تكوين البحث عن OneDrive for Business الجغرافيا](configure-search-for-multi-geo.md) المتعددة للحصول على الإرشادات بما في ذلك أي قيود أو اختلافات.

## <a name="validating-the-microsoft-365-multi-geo-configuration"></a>التحقق من صحة Microsoft 365 Multi-Geo

فيما يلي بعض حالات الاستخدام الأساسية التي قد ترغب في تضمينها في خطة التحقق من الصحة قبل Microsoft 365 Multi-Geo إلى شركتك. بعد الانتهاء من هذه الاختبارات وأي حالات استخدام إضافية ذات صلة بالشركة، يمكنك اختيار الانتقال إلى إضافة المستخدمين في مجموعة التجربة الأولية.

**OneDrive for Business**

حدد OneDrive من Microsoft 365 التطبيق وتأكد من أنه يتم توجيهك تلقائيا إلى الموقع الجغرافي المناسب للمستخدم، استنادا إلى PDL الخاص به. OneDrive for Business يجب أن تبدأ الآن في توفير في ذلك الموقع. بمجرد توفيره، حاول تحميل بعض المستندات وتنزيلها.

**OneDrive Mobile App**

سجل الدخول إلى تطبيق OneDrive المحمول باستخدام بيانات اعتماد حساب الاختبار. تأكد من أنه يمكنك رؤية ملفاتك OneDrive for Business والتفاعل معها من جهازك المحمول.

**المزامنة من OneDrive العميل**

تأكد من أن المزامنة من OneDrive العميل يكشف تلقائيا عن OneDrive for Business الجغرافي عند تسجيل الدخول. إذا كنت بحاجة إلى تنزيل عميل المزامنة، يمكنك **النقر فوق مزامنة** OneDrive المكتبة.

**Office التطبيقات**

تأكد من أنه يمكنك الوصول إلى OneDrive for Business تسجيل الدخول من تطبيق Office، مثل Word. افتح Office وحدد "OneDrive – <TenantName>". Office عن موقع OneDrive وإظهار الملفات التي يمكنك فتحها.

**المشاركة**

حاول مشاركة OneDrive الملفات. تأكد من أن منتقي الأشخاص يعرض لك جميع SharePoint عبر الإنترنت بغض النظر عن موقعهم الجغرافي.
