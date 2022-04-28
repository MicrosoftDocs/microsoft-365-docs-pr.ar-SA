---
title: مهلة جلسة العمل الخاملة Microsoft 365
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
description: تعيين المدة التي ستستمر فيها جلسة عمل المستخدم في Microsoft 365 قبل انتهاء مهلتها.
ms.openlocfilehash: fba4871d88b7398aea955ec4afe1a0c134f52067
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/27/2022
ms.locfileid: "65094251"
---
# <a name="idle-session-timeout-for-microsoft-365-public-preview"></a>مهلة جلسة العمل الخاملة Microsoft 365 (معاينة عامة)

<!-- Add metadata: localization, AdminSurgePortfolio, admindeeplinkMAC. remove robots nofollow -->

استخدم مهلة جلسة العمل الخاملة لتكوين نهج حول المدة التي يكون فيها المستخدمون غير نشطين في مؤسستك قبل تسجيل خروجهم من تطبيقات الويب Microsoft 365. يساعد ذلك على حماية بيانات الشركة الحساسة ويضيف طبقة أمان أخرى للمستخدمين النهائيين الذين يعملون على أجهزة غير شركية أو مشتركة.

عندما يصل مستخدم إلى جلسة مهلة الخمول التي قمت بتعيينها، سيتلقى إعلاما بأنه على وشك تسجيل الخروج. يجب عليهم تحديد البقاء في وضع تسجيل الدخول أو سيتم تسجيل خروجهم تلقائيا من جميع تطبيقات الويب Microsoft 365.

> [!IMPORTANT]
> لا تؤثر مهلة جلسة العمل الخاملة على Microsoft 365 تطبيقات سطح المكتب والأجهزة المحمولة.

## <a name="turn-on-idle-session-timeout"></a>تشغيل عطل جلسة العمل

إذا لم تكن مسؤولا عاما Microsoft 365 أو Office 365، فلن ترى علامة تبويب **الخصوصية & الأمان**.

1. في مركز مسؤولي Microsoft 365، حدد علامة تبويب [خصوصية & الأمان الإعدادات](https://go.microsoft.com/fwlink/p/?linkid=2072756) **المؤسسة** **->** وحدد **مهلة جلسة العمل خاملة**.  

2. في **"مهلة جلسة العمل الخاملة** "، حدد التبديل لتشغيله. يمكنك اختيار إعداد افتراضي أو اختيار الوقت المخصص الخاص بك. سيستغرق الأمر بضع دقائق قبل تشغيل جلسة العمل الخاملة في مؤسستك.

> [!NOTE]
> إذا قمت بإعداد نهج مهلة جلسة العمل الخاملة [لتطبيق ويب Outlook](https://support.microsoft.com/topic/description-of-the-activity-based-authentication-timeout-for-owa-in-office-365-0c101e1b-020e-69c1-a0b0-26532d60c0a4) و [SharePoint Online](/sharepoint/sign-out-inactive-users)، فسيؤدي تشغيل مهلة جلسة العمل الخاملة في مركز مسؤولي Microsoft 365 إلى تجاوز تطبيق الويب Outlook وإعدادات SharePoint.

مهلة جلسة العمل الخاملة هي واحدة من العديد من إجراءات الأمان في Microsoft 365. للتعرف على مهام الأمان الأخرى في Microsoft 365، راجع [أهم مهام الأمان في Microsoft 365](../../security/top-security-tasks-for-remote-work.md).  

## <a name="what-users-will-see"></a>ما سيرى المستخدمون

عندما يكون المستخدم غير نشط في Microsoft 365 تطبيقات الويب للفترة الزمنية التي اخترتها، فسيرى المطالبة التالية. يجب عليهم تحديد **"البقاء في وضع تسجيل الدخول** " أو سيتم تسجيل خروجهم.

:::image type="content" source="../../media/idle-session-timeout.png" alt-text="لقطة شاشة: مطالبتك بإعلامك بأن جلسة العمل على وشك الانتهاء. حدد &quot;البقاء في وضع تسجيل الدخول&quot; حتى لا يتم تسجيل خروجك من Microsoft 365 تطبيقات الويب":::

## <a name="details-about-idle-session-timeout"></a>تفاصيل حول مهلة جلسة العمل الخاملة

- يتم دعم تطبيقات الويب Microsoft 365 التالية. ستتم إضافة المزيد من تطبيقات الويب قريبا.

    - Outlook Web App

    - OneDrive for Business

    - SharePoint Online (SPO)

    - Office.com وصفحات البدء الأخرى

    - Office (Word، Excel، PowerPoint) على الويب

    - مركز مسؤول Microsoft 365

- يشير النشاط إلى أي تفاعل مستخدم من جانب العميل يحدث في سياق تطبيق الويب. على سبيل المثال، النقر بالماوس والضغط على لوحة المفاتيح.  

- تعمل مهلة جلسة العمل الخاملة على أساس جلسة عمل لكل مستعرض. يتم التعامل مع نشاط المستخدم على Microsoft Edge بشكل مختلف عن نشاطه في مستعرضات أخرى مثل Google Chrome. سيتم تسجيل خروج المستخدمين من جميع علامات التبويب المطابقة لحسابهم ضمن جلسة عمل المستعرض هذه.

- بمجرد تشغيل مهلة جلسة العمل الخاملة، يتم تطبيقها على مؤسستك بأكملها ولا يمكن تحديد نطاقها لمستخدمين محددين أو وحدات تنظيمية أو مجموعات معينة. استخدم نهج [الوصول المشروط إلى Azure AD](/azure/active-directory/conditional-access/) لمستخدمين ومجموعات مختلفة للوصول إلى SharePoint Exchange Online.

- يجب أن يكون المستخدمون غير نشطين على جميع علامات تبويب تطبيق الويب Microsoft 365 طوال المدة التي تم تكوينها. إذا كان المستخدم نشطا على علامة تبويب واحدة (على سبيل المثال OWA) أثناء عدم تنشيطه على علامة تبويب أخرى (مثل SPO)، فسيتم اعتباره نشطا ولن يتم تسجيل الخروج.  

- لن يتم تسجيل خروج المستخدمين في هذه الحالات.
    - إذا تم تسجيل الدخول الأحادي (SSO) إلى تطبيق الويب من حساب الجهاز المنضم أو حدد **"البقاء قيد تسجيل الدخول** " في وقت تسجيل الدخول. لمزيد من المعلومات حول إخفاء هذا الخيار لمؤسستك، راجع [إضافة علامة تجارية إلى صفحة تسجيل الدخول الخاصة بمؤسستك](/azure/active-directory/fundamentals/customize-branding).
    - إذا كانوا على جهاز مدار (جهاز متوافق أو منضم إلى مجال) ويستخدم مستعرضا مدعوما مثل Microsoft Edge أو Google Chrome (مع [ملحق حسابات Windows](https://chrome.google.com/webstore/detail/windows-accounts/ppnbnpeolgkicgegkbkbjmhlideopiji)). لكي لا يتم تشغيل هذه الميزة على جهاز مدار، يلزم وجود اشتراك مؤهل في Azure AD Premium P1 أو P2 ونهج وصول مشروط محدد. راجع أدناه للحصول على مزيد من التفاصيل.

> [!IMPORTANT]
> مهلة جلسة العمل الخاملة غير متوفرة Microsoft 365 المشغلة بواسطة 21Vianet أو Microsoft 365 ألمانيا.

## <a name="idle-session-timeout-on-unmanaged-devices"></a>مهلة جلسة العمل الخاملة على الأجهزة غير المدارة  

لكي يتم تشغيل مهلة جلسة العمل الخاملة على الأجهزة غير المدارة، ستحتاج إلى إضافة نهج الوصول المشروط في مركز إدارة Azure AD.

1. في **| الوصول المشروط صفحة النهج** الخاصة بمركز إدارة Azure AD، حدد **نهج جديد** وأدخل اسما للنهج.

2. حدد **المستخدمين أو هويات حمل العمل**، ثم حدد **كافة المستخدمين**.

3. حدد **تطبيقات السحابة أو إجراءاتها**، **وحدد التطبيقات**، وابحث عن **Office 365**. حدد **Office 365**، ثم **حدد**.  

4. حدد **الشروط** **وتطبيقات العميل** **وقم بتكوين إلى "نعم**" و" **المستعرض**"، ثم حدد **"تم**".

5. حدد **"Session"**، **واستخدم القيود المفروضة على التطبيق**، ثم **حدد**.

6. قم بتشغيل النهج وحدد **Create**.

## <a name="frequently-asked-questions"></a>الأسئلة الشائعة

### <a name="are-there-any-browsers-or-browser-scenarios-in-which-idle-session-timeout-feature-doesnt-work"></a>هل هناك أي مستعرضات أو سيناريوهات مستعرض لا تعمل فيها ميزة مهلة جلسة العمل الخاملة؟  

لا يتم اعتماد مهلة جلسة العمل الخاملة عند تعطيل ملفات تعريف الارتباط التابعة لجهة خارجية في المستعرض. لن يرى المستخدمون أي مطالبات بتسجيل الخروج. نوصي بالاحتفاظ بإعداد منع التعقب إلى [متوازن (افتراضي)](/microsoft-edge/web-platform/tracking-prevention) Microsoft Edge وملفات تعريف الارتباط التابعة لجهة خارجية ممكنة في المستعرضات الأخرى. توقفت Microsoft 365 التطبيقات والخدمات عن دعم Internet Explorer 11 منذ 17 أغسطس 2021.

### <a name="how-should-i-prepare-if-my-organization-is-already-using-existing-outlook-web-app-and-sharepoint-online-idle-timeout-policies"></a>كيف يمكنني الاستعداد إذا كانت مؤسستي تستخدم بالفعل تطبيق ويب Outlook الحالي ونهج مهلة الخمول SharePoint Online؟  

إذا كنت تستخدم بالفعل تطبيق ويب Outlook موجود ونهج مهلة الخمول SharePoint Online، فلا يزال بإمكانك تشغيل ميزة مهلة جلسة العمل الخاملة. عند تشغيل نهج المهلة الخاملة، فإنه يأخذ الأسبقية على تطبيق الويب Outlook الحالي ونهج SharePoint Online. نخطط لإهمال تطبيق الويب Outlook الحالي ونهج SharePoint Online في المستقبل القريب. لإعداد مؤسستك بشكل أفضل، نوصي بتشغيل مهلة جلسة العمل الخاملة.

### <a name="what-happens-if-i-am-inactive-on-an-included-microsoft-365-web-app-but-active-on-a-microsoft-web-app-or-saas-web-app-that-doesnt-have-idle-session-timeout-turned-on"></a>ماذا يحدث إذا كنت غير نشط على تطبيق ويب Microsoft 365 مضمن، ولكن نشط على تطبيق ويب Microsoft أو تطبيق ويب SaaS لم يتم تشغيل مهلة جلسة العمل الخاملة؟  

يتم دعم تطبيقات الويب Microsoft 365 التالية.

- Outlook Web App

- OneDrive for Business

- SharePoint Online (SPO)

- Office.com وصفحات البدء الأخرى

- Office (Word، Excel، PowerPoint) على الويب

- مركز مسؤول Microsoft 365

إذا كنت تعمل على تطبيق ويب مختلف بنفس الحساب، فلن يتم تطبيق النشاط في تطبيق الويب هذا على مهلة جلسة العمل الخاملة.

### <a name="i-want-to-make-changes-to-the-idle-session-timeout-policy-or-delete-it-how-can-i-do-that"></a>أريد إجراء تغييرات على نهج مهلة جلسة العمل الخاملة أو حذفها. كيف يمكنني القيام بذلك؟

تحديث النهج:

1. في مركز مسؤولي Microsoft 365، حدد **إعدادات "المؤسسة"**، وانتقل إلى علامة التبويب **"خصوصية & الأمان**" وحدد **مهلة جلسة العمل "خامل**".

2. في القائمة المنسدلة، حدد قيمة مهلة مختلفة ثم **احفظ**.  

حذف النهج:

1. في مركز مسؤولي Microsoft 365، حدد **إعدادات "المؤسسة"**، وانتقل إلى علامة التبويب **"خصوصية & الأمان**" وحدد **مهلة جلسة العمل "خامل**".

2. قم بإلغاء تحديد **"تشغيل" لتعيين فترة عدم النشاط للمستخدمين الذين سيتم تسجيل خروجهم من Office تطبيقات الويب** وحدد **"حفظ**".
