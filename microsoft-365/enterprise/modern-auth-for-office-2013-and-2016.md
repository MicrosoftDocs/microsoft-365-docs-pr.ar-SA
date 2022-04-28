---
title: كيفية عمل المصادقة الحديثة لتطبيقات عميل Office 2013 و Office 2016
ms.author: tracyp
author: MSFTTracyP
manager: scotv
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
description: تعرف على كيفية عمل ميزات المصادقة الحديثة Microsoft 365 بشكل مختلف لتطبيقات عميل Office 2013 و2016.
ms.openlocfilehash: 9c4cdc384ceded4ce3bb78ae4e67e0f4c5a503de
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/27/2022
ms.locfileid: "65093361"
---
# <a name="how-modern-authentication-works-for-office-2013-office-2016-and-office-2019-client-apps"></a>كيفية عمل المصادقة الحديثة لتطبيقات عميل Office 2013 و Office 2016 و Office 2019

*تنطبق هذه المقالة على كل من Microsoft 365 Enterprise و Office 365 Enterprise.*

اقرأ هذه المقالة لمعرفة كيفية استخدام تطبيقات عميل Office 2013 و Office 2016 و Office 2019 لميزات المصادقة الحديثة استنادا إلى تكوين المصادقة على المستأجر Microsoft 365 ل Exchange Online و SharePoint Online و Skype for Business Online.

> [!NOTE]
> تطبيقات العميل القديمة، مثل Office 2010 Office for Mac 2011، لا تدعم المصادقة الحديثة ويمكن استخدامها فقط مع المصادقة الأساسية.

## <a name="availability-of-modern-authentication-for-microsoft-365-services"></a>توفر المصادقة الحديثة لخدمات Microsoft 365

بالنسبة لخدمات Microsoft 365، تكون الحالة الافتراضية للمصادقة الحديثة هي:

- قيد **التشغيل** Exchange Online بشكل افتراضي. راجع [تمكين المصادقة الحديثة أو تعطيلها في Exchange Online](https://support.office.com/article/58018196-f918-49cd-8238-56f57f38d662) لإيقاف تشغيلها أو إيقاف تشغيلها.

- تم **تشغيل** SharePoint Online بشكل افتراضي.

- تم **تشغيل** Skype for Business Online بشكل افتراضي. راجع [تمكين Skype for Business Online للمصادقة الحديثة](https://social.technet.microsoft.com/wiki/contents/articles/34339.skype-for-business-online-enable-your-tenant-for-modern-authentication.aspx) لإيقاف تشغيلها أو إيقاف تشغيلها.

> [!NOTE]
> بالنسبة للمستأجرين الذين تم إنشاؤهم **قبل** 1 أغسطس 2017، يتم **إيقاف تشغيل** المصادقة الحديثة بشكل افتراضي Exchange Online و Skype for Business Online.

## <a name="sign-in-behavior-of-office-client-apps"></a>سلوك تسجيل الدخول لتطبيقات العميل Office

تدعم تطبيقات عميل Office 2013 المصادقة القديمة بشكل افتراضي. تعني القديمة أنها تدعم إما مساعد تسجيل الدخول إلى Microsoft Online أو المصادقة الأساسية. لكي يستخدم هؤلاء العملاء ميزات المصادقة الحديثة، يجب أن يكون لدى العميل Windows مفاتيح تسجيل معينة. للحصول على الإرشادات، راجع [تمكين المصادقة الحديثة Office 2013 على أجهزة Windows](https://support.office.com/article/7dc1c01a-090f-4971-9677-f1b192d6c910).

لتمكين المصادقة الحديثة لأي أجهزة تعمل Windows (على سبيل المثال على أجهزة الكمبيوتر المحمولة وأجهزة الكمبيوتر اللوحي)، التي تم تثبيت Microsoft Office 2013 عليها، تحتاج إلى تعيين مفاتيح التسجيل التالية. يجب تعيين المفاتيح على كل جهاز تريد تمكينه للمصادقة الحديثة:

|**مفتاح التسجيل**|**نوع**|**قيمه** |
|:-------|:------:|--------:|
|HKCU\SOFTWARE\Microsoft\Office\15.0\Common\Identity\EnableADAL  |REG_DWORD  |1  |
|HKCU\SOFTWARE\Microsoft\Office\15.0\Common\Identity\Version |REG_DWORD |1 |

اقرأ [كيفية استخدام المصادقة الحديثة (ADAL) مع Skype for Business](./hybrid-modern-auth-overview.md) للتعرف على كيفية عملها مع Skype for Business.

يدعم عملاء Office 2016 Office 2019 المصادقة الحديثة بشكل افتراضي، ولا يلزم اتخاذ أي إجراء للعميل لاستخدام هذه التدفقات الجديدة. ومع ذلك، هناك حاجة إلى إجراء صريح لاستخدام المصادقة القديمة.

انقر فوق الارتباطات أدناه لمعرفة كيفية عمل مصادقة عميل Office 2013 Office 2016 Office 2019 مع خدمات Microsoft 365 استنادا إلى ما إذا كانت المصادقة الحديثة قيد التشغيل أم لا.

- [Exchange Online](modern-auth-for-office-2013-and-2016.md#BK_EchangeOnline)

- [SharePoint Online](modern-auth-for-office-2013-and-2016.md#BK_SharePointOnline)

- [Skype for Business Online](modern-auth-for-office-2013-and-2016.md#BK_SFBO)

<a name="BK_EchangeOnline"> </a>
### <a name="exchange-online"></a>Exchange Online

يصف الجدول التالي سلوك المصادقة لتطبيقات عميل Office 2013 و Office 2016 Office 2019 عند اتصالها Exchange Online بمصادقة حديثة أو بدونها.

|Office إصدار تطبيق العميل****|هل مفتاح التسجيل موجود؟****|المصادقة الحديثة على?****|سلوك المصادقة مع تشغيل المصادقة الحديثة للمستأجر (افتراضي)****|سلوك المصادقة مع إيقاف تشغيل المصادقة الحديثة للمستأجر****|
|:-----|:-----|:-----|:-----|:-----|
|Office 2019  <br/> |لا <br> AlwaysUseMSOAuthForAutoDiscover = 1 <br/> |نعم  <br/> |فرض المصادقة الحديثة على Outlook 2013 أو 2016 أو 2019. <br/> [مزيد من المعلومات](https://support.microsoft.com/help/3126599/outlook-prompts-for-password-when-modern-authentication-is-enabled)|فرض المصادقة الحديثة داخل عميل Outlook.<br/> |
|Office 2019  <br/> |لا، أو EnableADAL = 1  <br/> |نعم  <br/> |تتم محاولة المصادقة الحديثة أولا. إذا رفض الخادم اتصال مصادقة حديث، فسيتم استخدام المصادقة الأساسية. يرفض الخادم المصادقة الحديثة عندما لا يتم تمكين المستأجر.  <br/> |تتم محاولة المصادقة الحديثة أولا. إذا رفض الخادم اتصال مصادقة حديث، فسيتم استخدام المصادقة الأساسية. يرفض الخادم المصادقة الحديثة عندما لا يتم تمكين المستأجر.  <br/> |
|Office 2019  <br/> |نعم، EnableADAL = 1  <br/> |نعم  <br/> |تتم محاولة المصادقة الحديثة أولا. إذا رفض الخادم اتصال مصادقة حديث، فسيتم استخدام المصادقة الأساسية. يرفض الخادم المصادقة الحديثة عندما لا يتم تمكين المستأجر.  <br/> |تتم محاولة المصادقة الحديثة أولا. إذا رفض الخادم اتصال مصادقة حديث، فسيتم استخدام المصادقة الأساسية. يرفض الخادم المصادقة الحديثة عندما لا يتم تمكين المستأجر.  <br/> |
|Office 2019  <br/> |نعم، EnableADAL=0  <br/> |لا  <br/> |المصادقة الأساسية  <br/> |المصادقة الأساسية  <br/> |
|Office 2016  <br/> |لا <br> AlwaysUseMSOAuthForAutoDiscover = 1 <br/> |نعم  <br/> |فرض المصادقة الحديثة في 2013 أو 2016 أو 2019. <br/> [مزيد من المعلومات](https://support.microsoft.com/help/3126599/outlook-prompts-for-password-when-modern-authentication-is-enabled)|فرض المصادقة الحديثة داخل عميل Outlook.<br/> |
|Office 2016  <br/> |لا، أو EnableADAL = 1  <br/> |نعم  <br/> |تتم محاولة المصادقة الحديثة أولا. إذا رفض الخادم اتصال مصادقة حديث، فسيتم استخدام المصادقة الأساسية. يرفض الخادم المصادقة الحديثة عندما لا يتم تمكين المستأجر.  <br/> |تتم محاولة المصادقة الحديثة أولا. إذا رفض الخادم اتصال مصادقة حديث، فسيتم استخدام المصادقة الأساسية. يرفض الخادم المصادقة الحديثة عندما لا يتم تمكين المستأجر.  <br/> |
|Office 2016  <br/> |نعم، EnableADAL = 1  <br/> |نعم  <br/> |تتم محاولة المصادقة الحديثة أولا. إذا رفض الخادم اتصال مصادقة حديث، فسيتم استخدام المصادقة الأساسية. يرفض الخادم المصادقة الحديثة عندما لا يتم تمكين المستأجر.  <br/> |تتم محاولة المصادقة الحديثة أولا. إذا رفض الخادم اتصال مصادقة حديث، فسيتم استخدام المصادقة الأساسية. يرفض الخادم المصادقة الحديثة عندما لا يتم تمكين المستأجر.  <br/> |
|Office 2016  <br/> |نعم، EnableADAL=0  <br/> |لا  <br/> |المصادقة الأساسية  <br/> |المصادقة الأساسية  <br/> |
|Office 2013  <br/> |لا  <br/> |لا  <br/> |المصادقة الأساسية  <br/> |المصادقة الأساسية  <br/> |
|Office 2013  <br/> |نعم، EnableADAL = 1  <br/> |نعم  <br/> |تتم محاولة المصادقة الحديثة أولا. إذا رفض الخادم اتصال مصادقة حديث، فسيتم استخدام المصادقة الأساسية. يرفض الخادم المصادقة الحديثة عندما لا يتم تمكين المستأجر.  <br/> |تتم محاولة المصادقة الحديثة أولا. إذا رفض الخادم اتصال مصادقة حديث، فسيتم استخدام المصادقة الأساسية. يرفض الخادم المصادقة الحديثة عندما لا يتم تمكين المستأجر.  <br/> |

<a name="BK_SharePointOnline"> </a>
### <a name="sharepoint-online"></a>SharePoint Online

يصف الجدول التالي سلوك المصادقة لتطبيقات عميل Office 2013 و Office 2016 و Office 2019 عند الاتصال SharePoint Online باستخدام المصادقة الحديثة أو بدونها.

|Office إصدار تطبيق العميل****|هل مفتاح التسجيل موجود؟****|المصادقة الحديثة على?****|سلوك المصادقة مع تشغيل المصادقة الحديثة للمستأجر (افتراضي)****|سلوك المصادقة مع إيقاف تشغيل المصادقة الحديثة للمستأجر****|
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

يصف الجدول التالي سلوك المصادقة لتطبيقات عميل Office 2013 و Office 2016 و Office 2019 عند الاتصال Skype for Business Online باستخدام المصادقة الحديثة أو بدونها.

|Office إصدار تطبيق العميل****|هل مفتاح التسجيل موجود؟****|المصادقة الحديثة على?****|سلوك المصادقة مع تشغيل المصادقة الحديثة للمستأجر****|سلوك المصادقة مع إيقاف تشغيل المصادقة الحديثة للمستأجر (افتراضي)****|
|:-----|:-----|:-----|:-----|:-----|
|Office 2019  <br/> |لا، أو EnableADAL = 1  <br/> |نعم  <br/> |تتم محاولة المصادقة الحديثة أولا. إذا رفض الخادم اتصال مصادقة حديث، فسيتم استخدام مساعد تسجيل الدخول إلى Microsoft Online. يرفض الخادم المصادقة الحديثة عندما لا يتم تمكين المستأجرين عبر الإنترنت Skype for Business.  <br/> |تتم محاولة المصادقة الحديثة أولا. إذا رفض الخادم اتصال مصادقة حديث، فسيتم استخدام مساعد تسجيل الدخول إلى Microsoft Online. يرفض الخادم المصادقة الحديثة عندما لا يتم تمكين المستأجرين عبر الإنترنت Skype for Business.  <br/> |
|Office 2019  <br/> |نعم، EnableADAL = 1  <br/> |نعم  <br/> |تتم محاولة المصادقة الحديثة أولا. إذا رفض الخادم اتصال مصادقة حديث، فسيتم استخدام مساعد تسجيل الدخول إلى Microsoft Online. يرفض الخادم المصادقة الحديثة عندما لا يتم تمكين المستأجرين عبر الإنترنت Skype for Business.  <br/> |تتم محاولة المصادقة الحديثة أولا. إذا رفض الخادم اتصال مصادقة حديث، فسيتم استخدام مساعد تسجيل الدخول إلى Microsoft Online. يرفض الخادم المصادقة الحديثة عندما لا يتم تمكين المستأجرين عبر الإنترنت Skype for Business.  <br/> |
|Office 2019  <br/> |نعم، EnableADAL = 0  <br/> |لا  <br/> |مساعد تسجيل الدخول إلى Microsoft Online فقط.  <br/> |مساعد تسجيل الدخول إلى Microsoft Online فقط.  <br/> |
|Office 2016  <br/> |لا، أو EnableADAL = 1  <br/> |نعم  <br/> |تتم محاولة المصادقة الحديثة أولا. إذا رفض الخادم اتصال مصادقة حديث، فسيتم استخدام مساعد تسجيل الدخول إلى Microsoft Online. يرفض الخادم المصادقة الحديثة عندما لا يتم تمكين المستأجرين عبر الإنترنت Skype for Business.  <br/> |تتم محاولة المصادقة الحديثة أولا. إذا رفض الخادم اتصال مصادقة حديث، فسيتم استخدام مساعد تسجيل الدخول إلى Microsoft Online. يرفض الخادم المصادقة الحديثة عندما لا يتم تمكين المستأجرين عبر الإنترنت Skype for Business.  <br/> |
|Office 2016  <br/> |نعم، EnableADAL = 1  <br/> |نعم  <br/> |تتم محاولة المصادقة الحديثة أولا. إذا رفض الخادم اتصال مصادقة حديث، فسيتم استخدام مساعد تسجيل الدخول إلى Microsoft Online. يرفض الخادم المصادقة الحديثة عندما لا يتم تمكين المستأجرين عبر الإنترنت Skype for Business.  <br/> |تتم محاولة المصادقة الحديثة أولا. إذا رفض الخادم اتصال مصادقة حديث، فسيتم استخدام مساعد تسجيل الدخول إلى Microsoft Online. يرفض الخادم المصادقة الحديثة عندما لا يتم تمكين المستأجرين عبر الإنترنت Skype for Business.  <br/> |
|Office 2016  <br/> |نعم، EnableADAL = 0  <br/> |لا  <br/> |مساعد تسجيل الدخول إلى Microsoft Online فقط.  <br/> |مساعد تسجيل الدخول إلى Microsoft Online فقط.  <br/> |
|Office 2013  <br/> |لا  <br/> |لا  <br/> |مساعد تسجيل الدخول إلى Microsoft Online فقط.  <br/> |مساعد تسجيل الدخول إلى Microsoft Online فقط.  <br/> |
|Office 2013  <br/> |نعم، EnableADAL = 1  <br/> |نعم  <br/> |تتم محاولة المصادقة الحديثة أولا. إذا رفض الخادم اتصال مصادقة حديث، فسيتم استخدام مساعد تسجيل الدخول إلى Microsoft Online. يرفض الخادم المصادقة الحديثة عندما لا يتم تمكين المستأجرين عبر الإنترنت Skype for Business.  <br/> |مساعد تسجيل الدخول إلى Microsoft Online فقط.  <br/> |

## <a name="see-also"></a>راجع أيضًا

[تمكين المصادقة الحديثة ل Office 2013 على أجهزة Windows](../admin/security-and-compliance/enable-modern-authentication.md)

[المصادقة متعددة العوامل Microsoft 365](../admin/security-and-compliance/multi-factor-authentication-microsoft-365.md)

[تسجيل الدخول إلى Microsoft 365 باستخدام المصادقة متعددة العوامل](https://support.microsoft.com/office/sign-in-to-microsoft-365-with-multi-factor-authentication-2b856342-170a-438e-9a4f-3c092394d3cb)

[نظرة عامة على Microsoft 365 Enterprise](microsoft-365-overview.md)