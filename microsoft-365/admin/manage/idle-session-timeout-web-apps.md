---
title: فترة عطل جلسة العمل Microsoft 365
f1.keywords:
- NOCSH
ms.author: kwekua
author: kwekua
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection: Adm_TOC
description: تعيين المدة الزمنية لجلسة عمل المستخدم في Microsoft 365 قبل  انتهاء  المدة.
ms.openlocfilehash: 215b900315b2d98b01a8cf87b14a6fa65289e121
ms.sourcegitcommit: 8423f47fce3905a48db9daefe69c21c841da43a0
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/15/2022
ms.locfileid: "63705363"
---
# <a name="idle-session-timeout-for-microsoft-365-public-preview"></a>فترة عطل جلسة العمل Microsoft 365 (معاينة عامة)

<!-- Add metadata: localization, AdminSurgePortfolio, admindeeplinkMAC. remove robots nofollow -->

استخدم فترة عطل جلسة العمل لتكوين نهج حول المدة التي يكون فيها المستخدمون غير نشطين في مؤسستك قبل أن يتم Microsoft 365 ويب. يساعد ذلك على حماية بيانات الشركة الحساسة ويضيف طبقة أمان أخرى للمستخدمين الذين يعملون على أجهزة غير خاصة بالشركة أو أجهزة مشتركة.

عندما يصل أحد المستخدمين إلى جلسة 2016 التي قمت بتعيينها، سيحصل على إعلام بأنه على وشك تسجيل الخروج. يجب أن يختاروا البقاء في وضع تسجيل الدخول أو سيتم تسجيل الخروج تلقائيا من جميع Microsoft 365 الويب.

> [!IMPORTANT]
> لا يؤثر عطل عطل جلسة العمل على Microsoft 365 سطح المكتب وتطبيقات الأجهزة المحمولة.

## <a name="turn-on-idle-session-timeout"></a>تشغيل عطل جلسة العمل

إذا لم تكن أحد Microsoft 365 أو Office 365 عام، فلن ترى علامة التبويب **أمان & الخصوصية**.

1. في مركز مسؤولي Microsoft 365، حدد **المؤسسة** **->** الإعدادات [أمان &](https://go.microsoft.com/fwlink/p/?linkid=2072756) الخصوصية وحدد عطل **عطل جلسة العمل**.  

2. في **عطل جلسة العمل،** حدد تبديل تشغيلها. يمكنك اختيار إعداد افتراضي أو اختيار الوقت المخصص الخاص بك. سيستغرق الأمر بضع دقائق قبل تشغيل جلسة العمل الخاملة في مؤسستك.

> [!NOTE]
> إذا قمت بإعداد سياسات عطل عطل جلسة العمل لتطبيق [ويب Outlook](https://support.microsoft.com/topic/description-of-the-activity-based-authentication-timeout-for-owa-in-office-365-0c101e1b-020e-69c1-a0b0-26532d60c0a4) و [SharePoint Online](/sharepoint/sign-out-inactive-users)، فإن تشغيل عطل عطل جلسة العمل في مركز مسؤولي Microsoft 365 سيتجاوز إعدادات Outlook على الويب SharePoint.

إن عطل عطل جلسة العمل هو أحد العديد من إجراءات الأمان في Microsoft 365. للتعرف على مهام الأمان الأخرى في Microsoft 365، راجع أهم مهام الأمان [في](../../security/top-security-tasks-for-remote-work.md) Microsoft 365.  

## <a name="what-users-will-see"></a>ما سيشاهده المستخدمون

عندما يكون المستخدم غير نشط في Microsoft 365 ويب خلال الفترة الزمنية التي اخترتها، سيشاهد المطالبة التالية. يجب عليهم تحديد **البقاء قيد الدخول أو** سيتم توقيعهم.

:::image type="content" source="../../media/idle-session-timeout.png" alt-text="لقطة شاشة: مطالبة تعلمك بأن جلسة عملك على وشك الانتهاء. حدد &quot;البقاء قيد الدخول&quot; حتى لا يتم Microsoft 365 ويب":::

## <a name="details-about-idle-session-timeout"></a>تفاصيل حول عطل عطل جلسة العمل

- يتم دعم Microsoft 365 الويب التالية. سيتم إضافة المزيد من تطبيقات الويب قريبا.

    - Outlook Web App

    - OneDrive for Business

    - SharePoint Online (SPO)

    - Office.com وصفحات البدء الأخرى

    - Office (Word Excel PowerPoint) على الويب

    - مسؤول Microsoft 365 المركز

- يشير النشاط إلى أي تفاعل مستخدم من جانب العميل يحدث في سياق تطبيق الويب. على سبيل المثال، النقر بالماوس وضغطات لوحة المفاتيح.  

- تعمل عطلات جلسة العمل على أساس جلسة عمل كل مستعرض. يتم التعامل مع نشاط المستخدم على Microsoft Edge بشكل مختلف عن نشاطه في المستعرضات الأخرى مثل Google Chrome. سيتم توقيع المستخدمين من كل علامات التبويب المطابقة لحسابهم ضمن جلسة عمل المستعرض هذه.

- بمجرد تشغيل عطل جلسة العمل، فإنه ينطبق على مؤسستك بكاملها ولا يمكن تحديد نطاقها لمستخدمين معينين أو وحدات تنظيمية أو مجموعات معينة. استخدم [Azure AD Conditional Access](/azure/active-directory/conditional-access/) لنهج المستخدمين والمجموعات المختلفة.

- يجب أن يكون المستخدمون غير نشطين على Microsoft 365 علامات تبويب تطبيق الويب للمدة التي تم تكوينها. إذا كان المستخدم نشطا على علامة تبويب واحدة (على مثال OWA) أثناء عدم نشاطه على علامة تبويب أخرى (مثل SPO)، سيتم اعتباره نشطا ولن يتم تسجيل الخروج.  

- لن يتم توقيع المستخدمين في هذه الحالات.
    - إذا تم تسجيل الدخول مرة واحدة (SSO) إلى تطبيق الويب من حساب الجهاز المنضم أو حدد البقاء في وضع  تسجيل الدخول في وقت تسجيل الدخول. لمزيد من المعلومات حول إخفاء هذا الخيار لمنظمتك، راجع إضافة علامة تجارية إلى صفحة [تسجيل الدخول إلى مؤسستك](/azure/active-directory/fundamentals/customize-branding).
    - إذا كانوا يستخدمون جهازا مدارا (جهازا متوافقا أو منضما إلى مجال) يستخدمون مستعرضا معتمدا مثل Microsoft Edge أو Google Chrome (باستخدام ملحق حسابات Windows[).](https://chrome.google.com/webstore/detail/windows-accounts/ppnbnpeolgkicgegkbkbjmhlideopiji) لكي لا يتم تشغيل هذه الميزة على جهاز مدار، يلزم وجود اشتراك Azure AD Premium P1 أو P2 مؤهل ون نهج وصول شرطي معين. راجع أدناه للحصول على مزيد من التفاصيل.

> [!IMPORTANT]
> لا تتوفر 21Vianet Microsoft 365 جلسة العمل الخاملة أو Microsoft 365 ألمانيا.

## <a name="idle-session-timeout-on-unmanaged-devices"></a>فترة عطل جلسة العمل على الأجهزة غير مدارة  

لكي يتم تشغيل عطل جلسة العمل على أجهزة غير مدارة، ستحتاج إلى إضافة نهج الوصول الشرطي في مركز إدارة Azure AD.

1. على **"الوصول الشرطي" | صفحة النهج** في مركز إدارة Azure AD، حدد **نهج جديد** وأدخل اسما النهج.

2. حدد **المستخدمون أو هويات حمل** العمل، ثم حدد **جميع المستخدمين**.

3. حدد **تطبيقات السحابة أو إجراءاتها****، وحدد التطبيقات**، **وابحث عن Office 365**. حدد **Office 365**، ثم **حدد**.  

4. حدد **الشروط**، **تطبيقات العميل****، تكوين إلى نعم**، **مستعرض**، ثم حدد **تم**.

5. حدد **جلسة** عمل، **استخدم القيود المفروضة على** التطبيق، ثم **حدد**.

6. قم تشغيل النهج وحدد **إنشاء**.

## <a name="frequently-asked-questions"></a>الأسئلة المتكررة

### <a name="are-there-any-browsers-or-browser-scenarios-in-which-idle-session-timeout-feature-doesnt-work"></a>هل هناك أي مستعرضات أو سيناريوهات مستعرض لا تعمل فيها ميزة عطل جلسة العمل؟  

لا يتم دعم عطل عطل جلسة العمل عند تعطيل ملفات تعريف الارتباط الخاصة ب جهة خارجية في المستعرض. لن يرى المستخدمون أي مطالبة تسجيل الخروج. نوصي بإبقاء إعداد منع التعقب إلى "متوازن" [(افتراضي)](/microsoft-edge/web-platform/tracking-prevention) لملفات تعريف الارتباط Microsoft Edge وملفات تعريف الارتباط الخاصة ب جهة خارجية التي تم تمكينها في المستعرضات الأخرى. Microsoft 365 التطبيقات والخدمات عن دعم Internet Explorer 11 منذ 17 أغسطس 2021.

### <a name="how-should-i-prepare-if-my-organization-is-already-using-existing-outlook-web-app-and-sharepoint-online-idle-timeout-policies"></a>كيف يمكنني التحضير إذا كانت المؤسسة تستخدم بالفعل Outlook ويب SharePoint عطل عبر الإنترنت؟  

إذا كنت تستخدم بالفعل Outlook ويب SharePoint ونهج عطل عطل عبر الإنترنت، ما زال بإمكانك تشغيل ميزة عطل جلسة العمل. عند تشغيل نهج عطل 2010، يكون له الأسبقية على Outlook ويب SharePoint Online. نحن نخطط ل إهمال تطبيق الويب Outlook الحالي SharePoint عبر الإنترنت في المستقبل القريب. لإعداد مؤسستك بشكل أفضل، نوصيك ب تشغيل عطل جلسة العمل.

### <a name="what-happens-if-i-am-inactive-on-an-included-microsoft-365-web-app-but-active-on-a-microsoft-web-app-or-saas-web-app-that-doesnt-have-idle-session-timeout-turned-on"></a>ماذا يحدث إذا لم أكن نشطا على تطبيق Microsoft 365 ويب مضمن، ولكن نشط على تطبيق Microsoft على الويب أو تطبيق SaaS على الويب الذي لم يتم تشغيل عطلته في جلسة العمل؟  

يتم دعم Microsoft 365 الويب التالية.

- Outlook Web App

- OneDrive for Business

- SharePoint Online (SPO)

- Office.com وصفحات البدء الأخرى

- Office (Word Excel PowerPoint) على الويب

- مسؤول Microsoft 365 المركز

إذا كنت تعمل على تطبيق ويب آخر باستخدام الحساب نفسه، فلن يتم تطبيق النشاط في تطبيق الويب هذا على عطل جلسة العمل.

### <a name="i-want-to-make-changes-to-the-idle-session-timeout-policy-or-delete-it-how-can-i-do-that"></a>أريد إجراء تغييرات على نهج عطل جلسة العمل أو حذفه. كيف يمكنني القيام بذلك؟

تحديث النهج:

1. في مركز مسؤولي Microsoft 365، حدد **إعدادات** المؤسسة، واذهب إلى علامة التبويب أمان & **الخصوصية** وحدد فترة **عطل جلسة العمل**.

2. في القائمة المنسدلة، حدد قيمة انتهاء مختلفة ثم **حفظ**.  

حذف النهج:

1. في مركز مسؤولي Microsoft 365، حدد **إعدادات** المؤسسة، واذهب إلى علامة التبويب أمان & **الخصوصية** وحدد فترة **عطل جلسة العمل**.

2. قم ب **إلغاء تحديد تشغيل لتعيين** فترة عدم النشاط للمستخدمين الذين سيتم توقيعهم Office ويب وحدد **حفظ**.
