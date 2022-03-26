---
title: كيفية عمل المصادقة الحديثة لتطبيقات Office 2013 Office 2016
ms.author: tracyp
author: MSFTTracyP
manager: laurawi
ms.date: 8/1/2017
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
ms.localizationpriority: medium
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- seo-marvel-apr2020
search.appverid:
- MET150
- MOE150
- MED150
- GMA150
- GPA150
- GEA150
- BCS160
ms.assetid: e4c45989-4b1a-462e-a81b-2a13191cf517
ms.collection:
- M365-security-compliance
description: تعرف على Microsoft 365 ميزات المصادقة الحديثة بشكل مختلف لتطبيقات عميل Office 2013 و2016.
ms.openlocfilehash: c3586029a3c1ea73dae30696c74011e3dd22400d
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 10/06/2021
ms.locfileid: "63572880"
---
# <a name="how-modern-authentication-works-for-office-2013-office-2016-and-office-2019-client-apps"></a>كيفية عمل المصادقة الحديثة Office 2013 Office 2016 Office عميل 2019

*تنطبق هذه المقالة على كل من Microsoft 365 Enterprise Office 365 Enterprise.*

اقرأ هذه المقالة للتعرف على كيفية استخدام Office 2013 و Office 2016 و Office 2019 ميزات المصادقة الحديثة استنادا إلى تكوين المصادقة على مستأجر Microsoft 365 ل Exchange Online و SharePoint Online و Skype for Business Online.

> [!NOTE]
> لا تدعم تطبيقات العميل القديمة، مثل Office 2010 Office for Mac 2011، المصادقة الحديثة ويمكن استخدامها فقط مع المصادقة الأساسية.

## <a name="availability-of-modern-authentication-for-microsoft-365-services"></a>توفر المصادقة الحديثة لخدمات Microsoft 365

بالنسبة لخدمات Microsoft 365، تكون الحالة الافتراضية للمصادقة الحديثة هي:

- يتم **تشغيلها Exchange Online** بشكل افتراضي. راجع [تمكين المصادقة الحديثة أو تعطيلها في](https://support.office.com/article/58018196-f918-49cd-8238-56f57f38d662) Exchange Online لإيقاف تشغيلها أو تشغيلها.

- يتم **تشغيلها SharePoint** Online بشكل افتراضي.

- يتم **تشغيلها Skype for Business** عبر الإنترنت بشكل افتراضي. راجع [تمكين Skype for Business عبر الإنترنت للمصادقة الحديثة](https://social.technet.microsoft.com/wiki/contents/articles/34339.skype-for-business-online-enable-your-tenant-for-modern-authentication.aspx) ل إيقاف تشغيلها أو إيقاف تشغيلها.

> [!NOTE]
> بالنسبة للمستأجرين الذين تم **إنشاؤهم** قبل 1 أغسطس 2017، يتم إيقاف تشغيل المصادقة  الحديثة بشكل افتراضي Exchange Online Skype for Business Online.

## <a name="sign-in-behavior-of-office-client-apps"></a>سلوك تسجيل الدخول لتطبيقات Office العميل

Office تطبيقات عميل 2013 المصادقة القديمة بشكل افتراضي. تعني القديمة أنها تدعم إما مساعد تسجيل الدخول إلى Microsoft Online أو المصادقة الأساسية. لكي يستخدم هؤلاء العملاء ميزات المصادقة الحديثة، يجب أن Windows العميل مجموعة مفاتيح التسجيل. للحصول على الإرشادات، راجع تمكين المصادقة [الحديثة Office 2013 على Windows الأجهزة](https://support.office.com/article/7dc1c01a-090f-4971-9677-f1b192d6c910).

لتمكين المصادقة الحديثة لأي أجهزة تعمل Windows (على سبيل المثال، على أجهزة الكمبيوتر المحمولة وأجهزة الكمبيوتر اللوحية)، التي تم تثبيت Microsoft Office 2013 عليها، ستحتاج إلى تعيين مفاتيح التسجيل التالية. يجب تعيين المفاتيح على كل جهاز تريد تمكينه للمصادقة الحديثة:

|**مفتاح التسجيل**|**النوع**|**القيمة** |
|:-------|:------:|--------:|
|HKCU\SOFTWARE\Microsoft\Office\15.0\Common\Identity\EnableADAL  |REG_DWORD  |1  |
|HKCU\SOFTWARE\Microsoft\Office\15.0\Common\Identity\Version |REG_DWORD |1 |

اقرأ [كيفية استخدام المصادقة الحديثة (ADAL)](./hybrid-modern-auth-overview.md) مع Skype for Business للتعرف على كيفية عملها مع Skype for Business.

Office عملاء Office 2016 و2019 على المصادقة الحديثة بشكل افتراضي، ولا يلزم اتخاذ أي إجراء للعميل لاستخدام هذه التدفقات الجديدة. ومع ذلك، يجب اتخاذ إجراء صريح لاستخدام المصادقة القديمة.

انقر فوق الارتباطات أدناه للاطلاع على كيفية عمل Office 2013 و Office 2016 و Office 2019 مع خدمات Microsoft 365 استنادا إلى تشغيل المصادقة الحديثة أو عدم تشغيلها.

- [Exchange Online](modern-auth-for-office-2013-and-2016.md#BK_EchangeOnline)

- [SharePoint Online](modern-auth-for-office-2013-and-2016.md#BK_SharePointOnline)

- [Skype for Business Online](modern-auth-for-office-2013-and-2016.md#BK_SFBO)

<a name="BK_EchangeOnline"> </a>
### <a name="exchange-online"></a>Exchange Online

يصف الجدول التالي سلوك المصادقة لتطبيقات عميل Office 2013 و Office 2016 و Office 2019 عند اتصالها Exchange Online بالمصادقة الحديثة أو بدونها.

|Office تطبيق العميل****|مفتاح التسجيل موجود؟****|المصادقة الحديثة على?****|سلوك المصادقة مع تشغيل المصادقة الحديثة للمستأجر (افتراضي)****|سلوك المصادقة مع إيقاف تشغيل المصادقة الحديثة للمستأجر****|
|:-----|:-----|:-----|:-----|:-----|
|Office 2019  <br/> |لا <br> AlwaysUseMSOAuthForAutoDiscover = 1 <br/> |نعم  <br/> |يجبر المصادقة الحديثة Outlook 2013 أو 2016 أو 2019. <br/> [مزيد من المعلومات](https://support.microsoft.com/help/3126599/outlook-prompts-for-password-when-modern-authentication-is-enabled)|تتطلب المصادقة الحديثة داخل Outlook العميل.<br/> |
|Office 2019  <br/> |لا، أو EnableADAL = 1  <br/> |نعم  <br/> |يتم محاولة المصادقة الحديثة أولا. إذا رفض الخادم اتصال مصادقة حديثة، يتم استخدام المصادقة الأساسية. يرفض الخادم المصادقة الحديثة عند عدم تمكين المستأجر.  <br/> |يتم محاولة المصادقة الحديثة أولا. إذا رفض الخادم اتصال مصادقة حديثة، يتم استخدام المصادقة الأساسية. يرفض الخادم المصادقة الحديثة عند عدم تمكين المستأجر.  <br/> |
|Office 2019  <br/> |نعم، EnableADAL = 1  <br/> |نعم  <br/> |يتم محاولة المصادقة الحديثة أولا. إذا رفض الخادم اتصال مصادقة حديثة، يتم استخدام المصادقة الأساسية. يرفض الخادم المصادقة الحديثة عند عدم تمكين المستأجر.  <br/> |يتم محاولة المصادقة الحديثة أولا. إذا رفض الخادم اتصال مصادقة حديثة، يتم استخدام المصادقة الأساسية. يرفض الخادم المصادقة الحديثة عند عدم تمكين المستأجر.  <br/> |
|Office 2019  <br/> |نعم، EnableADAL=0  <br/> |لا  <br/> |المصادقة الأساسية  <br/> |المصادقة الأساسية  <br/> |
|Office 2016  <br/> |لا <br> AlwaysUseMSOAuthForAutoDiscover = 1 <br/> |نعم  <br/> |يجبر المصادقة الحديثة على 2013 أو 2016 أو 2019. <br/> [مزيد من المعلومات](https://support.microsoft.com/help/3126599/outlook-prompts-for-password-when-modern-authentication-is-enabled)|تتطلب المصادقة الحديثة داخل Outlook العميل.<br/> |
|Office 2016  <br/> |لا، أو EnableADAL = 1  <br/> |نعم  <br/> |يتم محاولة المصادقة الحديثة أولا. إذا رفض الخادم اتصال مصادقة حديثة، يتم استخدام المصادقة الأساسية. يرفض الخادم المصادقة الحديثة عند عدم تمكين المستأجر.  <br/> |يتم محاولة المصادقة الحديثة أولا. إذا رفض الخادم اتصال مصادقة حديثة، يتم استخدام المصادقة الأساسية. يرفض الخادم المصادقة الحديثة عند عدم تمكين المستأجر.  <br/> |
|Office 2016  <br/> |نعم، EnableADAL = 1  <br/> |نعم  <br/> |يتم محاولة المصادقة الحديثة أولا. إذا رفض الخادم اتصال مصادقة حديثة، يتم استخدام المصادقة الأساسية. يرفض الخادم المصادقة الحديثة عند عدم تمكين المستأجر.  <br/> |يتم محاولة المصادقة الحديثة أولا. إذا رفض الخادم اتصال مصادقة حديثة، يتم استخدام المصادقة الأساسية. يرفض الخادم المصادقة الحديثة عند عدم تمكين المستأجر.  <br/> |
|Office 2016  <br/> |نعم، EnableADAL=0  <br/> |لا  <br/> |المصادقة الأساسية  <br/> |المصادقة الأساسية  <br/> |
|Office 2013  <br/> |لا  <br/> |لا  <br/> |المصادقة الأساسية  <br/> |المصادقة الأساسية  <br/> |
|Office 2013  <br/> |نعم، EnableADAL = 1  <br/> |نعم  <br/> |يتم محاولة المصادقة الحديثة أولا. إذا رفض الخادم اتصال مصادقة حديثة، يتم استخدام المصادقة الأساسية. يرفض الخادم المصادقة الحديثة عند عدم تمكين المستأجر.  <br/> |يتم محاولة المصادقة الحديثة أولا. إذا رفض الخادم اتصال مصادقة حديثة، يتم استخدام المصادقة الأساسية. يرفض الخادم المصادقة الحديثة عند عدم تمكين المستأجر.  <br/> |

<a name="BK_SharePointOnline"> </a>
### <a name="sharepoint-online"></a>SharePoint Online

يصف الجدول التالي سلوك المصادقة لتطبيقات عميل Office 2013 و Office 2016 و Office 2019 عند اتصالها ب SharePoint Online باستخدام المصادقة الحديثة أو بدونها.

|Office تطبيق العميل****|مفتاح التسجيل موجود؟****|المصادقة الحديثة على?****|سلوك المصادقة مع تشغيل المصادقة الحديثة للمستأجر (افتراضي)****|سلوك المصادقة مع إيقاف تشغيل المصادقة الحديثة للمستأجر****|
|:-----|:-----|:-----|:-----|:-----|
|Office 2019  <br/> |لا، أو EnableADAL = 1  <br/> |نعم  <br/> |المصادقة الحديثة فقط.  <br/> |فشل الاتصال.  <br/> |
|Office 2019  <br/> |نعم، EnableADAL = 1  <br/> |نعم  <br/> |المصادقة الحديثة فقط.  <br/> |فشل الاتصال.  <br/> |
|Office 2019  <br/> |نعم، EnableADAL = 0  <br/> |لا  <br/> |مساعد تسجيل الدخول إلى Microsoft Online فقط.  <br/> |مساعد تسجيل الدخول إلى Microsoft Online فقط.  <br/> |
|Office 2016  <br/> |لا، أو EnableADAL = 1  <br/> |نعم  <br/> |المصادقة الحديثة فقط.  <br/> |فشل الاتصال.  <br/> |
|Office 2016  <br/> |نعم، EnableADAL = 1  <br/> |نعم  <br/> |المصادقة الحديثة فقط.  <br/> |فشل الاتصال.  <br/> |
|Office 2016  <br/> |نعم، EnableADAL = 0  <br/> |لا  <br/> |مساعد تسجيل الدخول إلى Microsoft Online فقط.  <br/> |مساعد تسجيل الدخول إلى Microsoft Online فقط.  <br/> |
|Office 2013  <br/> |لا  <br/> |لا  <br/> |مساعد تسجيل الدخول إلى Microsoft Online فقط.  <br/> |مساعد تسجيل الدخول إلى Microsoft Online فقط.  <br/> |
|Office 2013  <br/> |نعم، EnableADAL = 1  <br/> |نعم  <br/> |المصادقة الحديثة فقط.  <br/> |فشل الاتصال.  <br/> |

### <a name="skype-for-business-online"></a>Skype for Business Online
<a name="BK_SFBO"> </a>

يصف الجدول التالي سلوك المصادقة لتطبيقات عميل Office 2013 و Office 2016 و Office 2019 عند الاتصال ب Skype for Business عبر الإنترنت باستخدام المصادقة الحديثة أو بدونها.

|Office تطبيق العميل****|مفتاح التسجيل موجود؟****|المصادقة الحديثة على?****|سلوك المصادقة مع تشغيل المصادقة الحديثة للمستأجر****|سلوك المصادقة مع إيقاف تشغيل المصادقة الحديثة للمستأجر (افتراضي)****|
|:-----|:-----|:-----|:-----|:-----|
|Office 2019  <br/> |لا، أو EnableADAL = 1  <br/> |نعم  <br/> |يتم محاولة المصادقة الحديثة أولا. إذا رفض الخادم اتصال مصادقة حديثة، يتم استخدام مساعد تسجيل الدخول إلى Microsoft Online. يرفض الخادم المصادقة الحديثة Skype for Business لم يتم تمكين المستأجرين عبر الإنترنت.  <br/> |يتم محاولة المصادقة الحديثة أولا. إذا رفض الخادم اتصال مصادقة حديثة، يتم استخدام مساعد تسجيل الدخول إلى Microsoft Online. يرفض الخادم المصادقة الحديثة Skype for Business لم يتم تمكين المستأجرين عبر الإنترنت.  <br/> |
|Office 2019  <br/> |نعم، EnableADAL = 1  <br/> |نعم  <br/> |يتم محاولة المصادقة الحديثة أولا. إذا رفض الخادم اتصال مصادقة حديثة، يتم استخدام مساعد تسجيل الدخول إلى Microsoft Online. يرفض الخادم المصادقة الحديثة Skype for Business لم يتم تمكين المستأجرين عبر الإنترنت.  <br/> |يتم محاولة المصادقة الحديثة أولا. إذا رفض الخادم اتصال مصادقة حديثة، يتم استخدام مساعد تسجيل الدخول إلى Microsoft Online. يرفض الخادم المصادقة الحديثة Skype for Business لم يتم تمكين المستأجرين عبر الإنترنت.  <br/> |
|Office 2019  <br/> |نعم، EnableADAL = 0  <br/> |لا  <br/> |مساعد تسجيل الدخول إلى Microsoft Online فقط.  <br/> |مساعد تسجيل الدخول إلى Microsoft Online فقط.  <br/> |
|Office 2016  <br/> |لا، أو EnableADAL = 1  <br/> |نعم  <br/> |يتم محاولة المصادقة الحديثة أولا. إذا رفض الخادم اتصال مصادقة حديثة، يتم استخدام مساعد تسجيل الدخول إلى Microsoft Online. يرفض الخادم المصادقة الحديثة Skype for Business لم يتم تمكين المستأجرين عبر الإنترنت.  <br/> |يتم محاولة المصادقة الحديثة أولا. إذا رفض الخادم اتصال مصادقة حديثة، يتم استخدام مساعد تسجيل الدخول إلى Microsoft Online. يرفض الخادم المصادقة الحديثة Skype for Business لم يتم تمكين المستأجرين عبر الإنترنت.  <br/> |
|Office 2016  <br/> |نعم، EnableADAL = 1  <br/> |نعم  <br/> |يتم محاولة المصادقة الحديثة أولا. إذا رفض الخادم اتصال مصادقة حديثة، يتم استخدام مساعد تسجيل الدخول إلى Microsoft Online. يرفض الخادم المصادقة الحديثة Skype for Business لم يتم تمكين المستأجرين عبر الإنترنت.  <br/> |يتم محاولة المصادقة الحديثة أولا. إذا رفض الخادم اتصال مصادقة حديثة، يتم استخدام مساعد تسجيل الدخول إلى Microsoft Online. يرفض الخادم المصادقة الحديثة Skype for Business لم يتم تمكين المستأجرين عبر الإنترنت.  <br/> |
|Office 2016  <br/> |نعم، EnableADAL = 0  <br/> |لا  <br/> |مساعد تسجيل الدخول إلى Microsoft Online فقط.  <br/> |مساعد تسجيل الدخول إلى Microsoft Online فقط.  <br/> |
|Office 2013  <br/> |لا  <br/> |لا  <br/> |مساعد تسجيل الدخول إلى Microsoft Online فقط.  <br/> |مساعد تسجيل الدخول إلى Microsoft Online فقط.  <br/> |
|Office 2013  <br/> |نعم، EnableADAL = 1  <br/> |نعم  <br/> |يتم محاولة المصادقة الحديثة أولا. إذا رفض الخادم اتصال مصادقة حديثة، يتم استخدام مساعد تسجيل الدخول إلى Microsoft Online. يرفض الخادم المصادقة الحديثة Skype for Business لم يتم تمكين المستأجرين عبر الإنترنت.  <br/> |مساعد تسجيل الدخول إلى Microsoft Online فقط.  <br/> |

## <a name="see-also"></a>راجع أيضًا

[تمكين المصادقة الحديثة Office 2013 على Windows الأجهزة](../admin/security-and-compliance/enable-modern-authentication.md)

[المصادقة متعددة العوامل Microsoft 365](../admin/security-and-compliance/multi-factor-authentication-microsoft-365.md)

[تسجيل الدخول إلى Microsoft 365 المصادقة متعددة العوامل](https://support.microsoft.com/office/sign-in-to-microsoft-365-with-multi-factor-authentication-2b856342-170a-438e-9a4f-3c092394d3cb)

[Microsoft 365 Enterprise عامة](microsoft-365-overview.md)