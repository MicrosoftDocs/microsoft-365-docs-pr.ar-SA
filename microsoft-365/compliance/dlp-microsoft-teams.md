---
title: منع فقدان البيانات وMicrosoft Teams
f1.keywords:
- NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: ''
audience: ITPro
ms.topic: conceptual
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
search.appverid:
- MET150
description: تدعم دردشات وقنوات Microsoft Teams نهج منع فقدان البيانات (DLP).
ms.openlocfilehash: 5d2ee7cefc23a85aec1a75fbe9fe121feacbb51f
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/06/2022
ms.locfileid: "66638356"
---
# <a name="data-loss-prevention-and-microsoft-teams"></a>منع فقدان البيانات وMicrosoft Teams

إذا كان لدى مؤسستك تفادي فقدان البيانات في Microsoft Purview (DLP)، يمكنك تحديد النهج التي تمنع الأشخاص من مشاركة المعلومات الحساسة في قناة Microsoft Teams أو جلسة محادثة. فيما يلي بعض الأمثلة على كيفية عمل هذه الحماية:

- **مثال 1: حماية المعلومات الحساسة في الرسائل**. لنفترض أن شخصا ما يحاول مشاركة المعلومات الحساسة في دردشة Teams أو قناته مع ضيوف (مستخدمين خارجيين). إذا كان لديك نهج DLP محدد لمنع ذلك، يتم حذف الرسائل التي تحتوي على معلومات حساسة يتم إرسالها إلى مستخدمين خارجيين. يحدث هذا تلقائيا، وفي غضون ثوان، وفقا لكيفية تكوين نهج DLP الخاص بك.

    > [!NOTE]
    > يحظر DLP ل Microsoft Teams المحتوى الحساس عند مشاركته مع مستخدمي Microsoft Teams الذين لديهم:<br/>- [وصول الضيف](/MicrosoftTeams/guest-access) في الفرق والقنوات؛ او<br/>- [الوصول الخارجي](/MicrosoftTeams/manage-external-access) في الاجتماعات وجلسات الدردشة. <p>لن تعمل DLP لجلسات الدردشة الخارجية إلا إذا كان كل من المرسل والمستلم في وضع Teams فقط واستخدام [الاتحاد الأصلي ل Microsoft Teams](/microsoftteams/manage-external-access). لا تحظر DLP ل Teams الرسائل في [interop](/microsoftteams/teams-and-skypeforbusiness-coexistence-and-interoperability#interoperability-of-teams-and-skype-for-business) مع جلسات محادثة Skype for Business أو غير أصلية.

- **مثال 2: حماية المعلومات الحساسة في المستندات**. لنفترض أن شخصا ما يحاول مشاركة مستند مع الضيوف في قناة أو دردشة Microsoft Teams، ويحتوي المستند على معلومات حساسة. إذا كان لديك نهج DLP محدد لمنع حدوث ذلك، فلن يتم فتح المستند لهؤلاء المستخدمين. يجب أن يتضمن نهج DLP SharePoint وOneDrive لكي تكون الحماية في مكانها. هذا مثال على DLP ل SharePoint الذي يظهر في Microsoft Teams، وبالتالي يتطلب ترخيص المستخدمين ل DLP Office 365 (مضمن في Office 365 E3)، ولكنه لا يتطلب ترخيص المستخدمين خدمات الامتثال المتطورة في Office 365.)

- **مثال 3: حماية الاتصالات في القنوات المشتركة ل Teams**. بالنسبة للقنوات المشتركة، يتم تطبيق نهج DLP لفريق Teams المضيف. على سبيل المثال، لنفترض أن هناك قناة مشتركة تملكها TeamA من Contoso. لدى TeamA نهج DLP P1. هناك 3 طرق لمشاركة قناة:
    - **المشاركة مع العضو**: يمكنك دعوة user1 من Contoso للانضمام إلى القناة المشتركة دون جعله عضوا في TeamA. ستتم تغطية كل شخص في هذه القناة المشتركة، بما في ذلك user1، بواسطة P1.
    - **المشاركة مع الفريق (داخليا):** يمكنك مشاركة القناة مع TeamB آخر في Contoso. قد يكون لدى هذا الفريق الآخر نهج DLP مختلف، ولكن هذا لا يهم. سيتم تطبيق P1 على كل شخص في هذه القناة المشتركة، بما في ذلك مستخدمي TeamA و TeamB.
    - **المشاركة مع الفريق (عبر المستأجرين):** يمكنك مشاركة القناة مع فريق TeamF في Fabrikam. قد يكون لدى Fabrikam نهج DLP الخاص بها، ولكن هذا لا يهم. سيتم تطبيق P1 على كل شخص في هذه القناة المشتركة، بما في ذلك كل من مستخدمي TeamA (Contoso) و TeamF (Fabrikam).
 
## <a name="dlp-licensing-for-microsoft-teams"></a>ترخيص DLP ل Microsoft Teams

تتضمن قدرات [منع فقدان البيانات](dlp-learn-about-dlp.md) دردشة Microsoft Teams ورسائل القناة، **بما في ذلك رسائل القناة الخاصة** ل:

- Office 365 E5/A5/G5
- Microsoft 365 E5/A5/G5
- Microsoft 365 E5/A5/G5 حماية البيانات والحوكمة
- التوافق Microsoft 365 E5/A5/G5/F5 وتوافق & الأمان F5

تتضمن Office 365 Microsoft 365 E3 حماية DLP ل SharePoint Online وOneDrive Exchange Online. يتضمن هذا أيضا الملفات التي تتم مشاركتها من خلال Teams لأن Teams يستخدم SharePoint Online وOneDrive لمشاركة الملفات.

يتطلب دعم حماية DLP في Teams Chat E5.

لمعرفة المزيد حول متطلبات الترخيص، راجع [إرشادات ترخيص خدمات Microsoft 365 Tenant-Level](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).

> [!IMPORTANT]
> ينطبق DLP فقط على الرسائل الفعلية في المحادثة أو مؤشر ترابط القناة. **لا** يتم تضمين إعلامات النشاط - التي تتضمن معاينة رسالة قصيرة وتظهر استنادا إلى إعدادات إعلام المستخدم - في Teams DLP. ستبقى أي معلومات حساسة موجودة في جزء الرسالة التي تظهر في المعاينة مرئية في الإعلام حتى بعد تطبيق نهج DLP وإزالته من المعلومات الحساسة للرسالة نفسها.

## <a name="scope-of-dlp-protection"></a>نطاق حماية DLP

يتم تطبيق حماية DLP بشكل مختلف على كيانات Teams.

|عندما يكون النهج في نطاق |كيانات Teams هذه |سيكون لديك حماية DLP متوفرة|
|---------|---------|---------|
|حسابات المستخدمين الفردية     |دردشات 1:1/n         |نعم         |
|     |رسائل القناة القياسية والمشتركة         |لا         |
|     |رسائل القناة الخاصة         |نعم         |
|مجموعات الأمان/قوائم التوزيع  | دردشات 1:1/n         |نعم         |
|     |رسائل القناة القياسية والمشتركة  |لا         |
|     |رسائل القناة الخاصة         |نعم        |
|مجموعة Microsoft 365    |دردشات 1:1/n          |لا         |
|     |رسائل القناة القياسية والمشتركة          |نعم        |
|     |رسائل القناة الخاصة|لا| 


## <a name="policy-tips-help-educate-users"></a>تلميحات النهج التي تساعد على تعليم المستخدمين

على غرار طريقة عمل DLP في [Exchange وOutlook Outlook على ويب](data-loss-prevention-policies.md#policy-evaluation-in-exchange-online-outlook-and-outlook-on-the-web) [وSharePoint Online ومواقع OneDrive for Business](data-loss-prevention-policies.md#policy-evaluation-in-onedrive-for-business-and-sharepoint-online-sites) [وعملاء Office لسطح المكتب](data-loss-prevention-policies.md#policy-evaluation-in-the-office-desktop-programs)، تظهر تلميحات النهج عند تشغيل إجراء باستخدام نهج DLP. فيما يلي مثال على تلميح نهج:

![إعلام الرسالة المحظورة في Teams.](../media/dlp-teams-blockedmessage-notification.png)

هنا، حاول المرسل مشاركة رقم الضمان الاجتماعي في قناة Microsoft Teams. يفتح الارتباط **"ماذا يمكنني أن أفعل"؟** مربع حوار يوفر خيارات للمرسل لحل المشكلة. لاحظ أنه يمكن للمرسل اختيار تجاوز النهج، أو إعلام مسؤول لمراجعته وحله.

![خيارات لحل الرسالة المحظورة.](../media/dlp-teams-blockedmessage-possibleactions.png)

في مؤسستك، يمكنك اختيار السماح للمستخدمين بتجاوز نهج DLP. عند تكوين نهج DLP، يمكنك استخدام تلميحات النهج الافتراضية، أو [تخصيص تلميحات النهج](#to-customize-policy-tips) لمؤسستك.

بالعودة إلى مثالنا، حيث شارك المرسل رقم ضمان اجتماعي في قناة Teams، إليك ما شاهده المستلم:

> [!div class="mx-imgBorder"]
> ![تم حظر الرسالة.](../media/dlp-teams-blockedmessage-notification-to-user.png)

### <a name="to-customize-policy-tips"></a>لتخصيص تلميحات النهج

لتنفيذ هذه المهمة، يجب تعيين دور له أذونات لتحرير نهج DLP. لمعرفة المزيد، راجع [الأذونات](data-loss-prevention-policies.md#permissions).

1. انتقل إلى مركز الامتثال ل Purview ([https://compliance.microsoft.com](https://compliance.microsoft.com)) وسجل الدخول.

2. اختر **نهج** **منع** >  فقدان البيانات.

3. حدد نهجا، واختر **"تحرير**" إلى جانب **إعدادات النهج**.

4. إما إنشاء قاعدة جديدة، أو تحرير قاعدة موجودة للنهج.

5. في علامة التبويب **"إعلامات المستخدم** "، حدد **تخصيص نص البريد الإلكتروني** و/أو **تخصيص خيارات نص تلميح النهج** .

6. حدد النص الذي تريد استخدامه لإعلامات البريد الإلكتروني و/أو تلميحات النهج، ثم اختر **"حفظ**".

7. في علامة التبويب **"إعدادات النهج"** ، اختر **"حفظ**".

السماح بساعة واحدة تقريبا للتغييرات الخاصة بك للعمل في طريقها من خلال مركز البيانات الخاص بك والمزامنة مع حسابات المستخدمين.
 <!-- why are these syncing to user accounts? -->

## <a name="add-microsoft-teams-as-a-location-to-existing-dlp-policies"></a>إضافة Microsoft Teams كموقع إلى نهج DLP الموجودة

لتنفيذ هذه المهمة، يجب تعيين دور له أذونات لتحرير نهج DLP. لمعرفة المزيد، راجع [الأذونات](data-loss-prevention-policies.md#permissions).

1. انتقل إلى مركز التوافق ([https://compliance.microsoft.com](https://compliance.microsoft.com)) وسجل الدخول.

2. اختر **نهج** **منع** >  فقدان البيانات.

3. حدد نهجا، وانظر إلى القيم ضمن **"المواقع**". إذا رأيت **دردشة Teams ورسائل القناة**، فأنت جاهز تماما. إذا لم تفعل ذلك، فانقر فوق **"تحرير**".

4. في عمود **"الحالة** "، قم بتشغيل نهج **الدردشة ورسائل القناة في Teams**.

5. في علامة التبويب **"اختيار المواقع** "، احتفظ بالإعداد الافتراضي لكافة الحسابات، أو حدد **"السماح لي باختيار مواقع معينة**". يمكنك تحديد:

    1. ما يصل إلى 1000 حساب فردي لتضمينه أو استبعاده
    1. قوائم التوزيع ومجموعات الأمان المراد تضمينها أو استبعادها. 
    <!-- 1. the shared mailbox of a shared channel. **This is a public preview feature.**--> 
    
6. ثم اختر **"التالي**".

7. انقر فوق **حفظ**.

السماح بساعة واحدة تقريبا للتغييرات الخاصة بك للعمل في طريقها من خلال مركز البيانات الخاص بك والمزامنة مع حسابات المستخدمين.
<!-- again, why user accounts? -->

## <a name="define-a-new-dlp-policy-for-microsoft-teams"></a>تحديد نهج DLP جديد ل Microsoft Teams

لتنفيذ هذه المهمة، يجب تعيين دور له أذونات لتحرير نهج DLP. لمعرفة المزيد، راجع [الأذونات](data-loss-prevention-policies.md#permissions).

1. انتقل إلى مركز التوافق ([https://compliance.microsoft.com](https://compliance.microsoft.com)) وسجل الدخول.

2. اختر **نهج** >  منع  > **فقدان البيانات****+ إنشاء نهج**.

3. اختر [قالبا](data-loss-prevention-policies.md#dlp-policy-templates)، ثم اختر **"التالي**".

    في مثالنا، اخترنا قالب بيانات معلومات التعريف الشخصية الأمريكية.

4. في علامة التبويب **"الاسم" في النهج** ، حدد اسما ووصفا للنهج، ثم اختر **"التالي**".

5. في علامة التبويب **"اختيار المواقع** "، احتفظ بالإعداد الافتراضي لكافة الحسابات، أو حدد **"السماح لي باختيار مواقع معينة**". يمكنك تحديد:

    1. ما يصل إلى 1000 حساب فردي لتضمينه أو استبعاده
    1. قوائم التوزيع ومجموعات الأمان المراد تضمينها أو استبعادها. **هذه ميزة معاينة عامة.**
    <!-- 1. the shared mailbox of a shared channel. **This is a public preview feature.**-->  

 
    > [!NOTE]
    > إذا كنت تريد التأكد من عدم مشاركة المستندات التي تحتوي على معلومات حساسة بشكل غير مناسب في Teams، فتأكد من تشغيل **مواقع SharePoint** **وحسابات OneDrive** ، بالإضافة إلى **رسائل الدردشة والقنوات في Teams**.

6. ضمن علامة التبويب **"إعدادات النهج** "، ضمن **"تخصيص نوع المحتوى الذي تريد حمايته**"، احتفظ بالإعدادات البسيطة الافتراضية، أو اختر **"استخدام الإعدادات المتقدمة**"، ثم اختر **"التالي**". إذا اخترت إعدادات متقدمة، يمكنك إنشاء قواعد للنهج أو تحريرها. للحصول على تعليمات حول هذا الأمر، راجع [الإعدادات البسيطة مقابل الإعدادات المتقدمة](data-loss-prevention-policies.md#simple-settings-vs-advanced-settings).

7.  ضمن علامة التبويب **"Policy settings** "، ضمن **"ماذا تريد أن تفعل إذا اكتشفنا معلومات حساسة؟**"، راجع الإعدادات. إليك المكان الذي يمكنك فيه اختيار الاحتفاظ [بتلميحات النهج الافتراضية وإعلامات البريد الإلكتروني](use-notifications-and-policy-tips.md)، أو تخصيصها.



    عند الانتهاء من مراجعة الإعدادات أو تحريرها، اختر **"التالي**".

8. في علامة التبويب **"إعدادات النهج** "، ضمن **"هل تريد تشغيل النهج أو اختبار الأمور أولا"؟**، اختر ما إذا كنت تريد تشغيل النهج أو [اختباره أولا](dlp-overview-plan-for-dlp.md#policy-deployment) أو إبقائه متوقفا عن التشغيل في الوقت الحالي، ثم اختر **"التالي**".

9. في علامة التبويب **"مراجعة الإعدادات"** ، راجع إعدادات النهج الجديد. اختر **"تحرير"** لإجراء تغييرات. عند الانتهاء، اختر **"إنشاء**".

السماح لنهجك الجديد بساعة واحدة تقريبا للعمل في طريقه من خلال مركز البيانات والمزامنة مع حسابات المستخدمين.

## <a name="prevent-external-access-to-sensitive-documents"></a>منع الوصول الخارجي إلى المستندات الحساسة

للتأكد من أنه يتعذر على الضيوف الخارجيين الوصول إلى مستندات SharePoint التي تحتوي على معلومات حساسة إما من SharePoint أو Teams بشكل افتراضي، حدد ما يلي:

- يمكنك التأكد من حماية المستندات حتى يقوم DLP بفحصها ووضع علامة عليها على أنها آمنة لمشاركتها عن طريق [وضع علامة على الملفات الجديدة كحساسة بشكل افتراضي](/sharepoint/sensitive-by-default).

- بنية نهج DLP الموصى بها

    - **الظروف**
        - يحتوي المحتوى على أي من أنواع المعلومات الحساسة هذه: [حدد كل ما ينطبق]
        
        - تتم مشاركة المحتوى من Microsoft 365 مع أشخاص من خارج مؤسستي
        
          > [!div class="mx-imgBorder"]
          > ![شروط DLP للكشف عن المشاركة الخارجية للمحتوى الحساس.](../media/dlp-teams-external-sharing/external-condition.png)

    - **الاجراءات**
        - تقييد الوصول إلى المحتوى للمستخدمين الخارجيين
        
        - إعلام المستخدمين بتلميحات حول البريد الإلكتروني والنهج
        
        - إرسال تقارير الحوادث إلى المسؤول
        
        > [!div class="mx-imgBorder"]
        > ![إجراء DLP لحظر المشاركة الخارجية للمحتوى الحساس.](../media/dlp-teams-external-sharing/external-action.png)

نهج DLP قيد التنفيذ عند محاولة مشاركة مستند في SharePoint يحتوي على معلومات حساسة مع ضيف خارجي:

> [!div class="mx-imgBorder"]
> ![تم حظر المشاركة الخارجية.](../media/dlp-teams-external-sharing/external-sharing-blocked.png)

<!--DLP policy in action when guest attempts to open a document in Teams with block external:
can't use the below image it contains a non-approved name.
> [!div class="mx-imgBorder"]
> ![External access blocked.](../media/dlp-teams-external-sharing/external-access-blocked.png)-->

## <a name="related-articles"></a>المقالات ذات الصلة

- [إنشاء نهج DLP واختباره وضبطه](create-test-tune-dlp-policy.md)
- [إرسال إعلامات بالبريد الإلكتروني وإظهار تلميحات النهج لنهج DLP](use-notifications-and-policy-tips.md)
