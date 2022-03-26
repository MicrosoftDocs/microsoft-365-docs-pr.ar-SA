---
title: منع فقدان البيانات Microsoft Teams
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
description: Microsoft Teams الدردشات والقنوات على دعم سياسات منع فقدان البيانات (DLP).
ms.openlocfilehash: 693b71181f34e948c0456779c7207fa22861dd5f
ms.sourcegitcommit: 46456ca009c9d50622e57e24269be74986184654
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/22/2022
ms.locfileid: "63715334"
---
# <a name="data-loss-prevention-and-microsoft-teams"></a>منع فقدان البيانات Microsoft Teams

إذا كانت مؤسستك لديها منع فقدان البيانات (DLP)، يمكنك تعريف سياسات تمنع الأشخاص من مشاركة المعلومات الحساسة في قناة Microsoft Teams أو جلسة محادثة. فيما يلي بعض الأمثلة حول كيفية عمل هذه الحماية:

- **المثال 1: حماية المعلومات الحساسة في الرسائل**. لنفترض أن أحد الأشخاص يحاول مشاركة المعلومات الحساسة في Teams أو قناة مع ضيوف (مستخدمين خارجيين). إذا كان لديك نهج DLP معرف لمنع حدوث ذلك، يتم حذف الرسائل التي بها معلومات حساسة يتم إرسالها إلى مستخدمين خارجيين. يحدث هذا تلقائيا، وفي غضون ثوان، وفقا لكيفية تكوين نهج DLP.

    > [!NOTE]
    > تمنع DLP for Microsoft Teams الحساسة عند مشاركتها مع Microsoft Teams الذين لديهم:<br/>- [وصول الضيف](/MicrosoftTeams/guest-access) في الفرق والقنوات؛ أو<br/>- [الوصول الخارجي](/MicrosoftTeams/manage-external-access) في الاجتماعات وجلسات المحادثة. <p>لن تعمل DLP لجلسات المحادثة الخارجية إلا إذا كان كل من المرسل والمستلم في وضع Teams فقط واستخدام Microsoft Teams [الأصلي](/microsoftteams/manage-external-access). لا تقوم DLP Teams حظر الرسائل في حالة التفاعل مع Skype for Business [](/microsoftteams/teams-and-skypeforbusiness-coexistence-and-interoperability#interoperability-of-teams-and-skype-for-business) أو جلسات دردشة متداخلة غير أصلية.

- **المثال 2: حماية المعلومات الحساسة في المستندات**. لنفترض أن أحد الأشخاص يحاول مشاركة مستند مع ضيوف في قناة Microsoft Teams أو دردشة، ويحتوي المستند على معلومات حساسة. إذا كان لديك نهج DLP معرف لمنع حدوث ذلك، فلن يتم فتح المستند لهؤلاء المستخدمين. يجب أن يتضمن نهج DLP SharePoint OneDrive حتى تكون الحماية في مكانها. هذا مثال ل DLP ل SharePoint الذي يظهر في Microsoft Teams، وبالتالي يتطلب ترخيص المستخدمين ل DLP Office 365 (المضمن في Office 365 E3)، ولكنه لا يتطلب ترخيص المستخدمين ل خدمات الامتثال المتطورة في Office 365.)

- **المثال 3: حماية الاتصالات في Teams المشتركة**. بالنسبة للقنوات المشتركة، يتم تطبيق نهج DLP الخاص Teams المضيف. على سبيل المثال، لنقل أن هناك قناة مشتركة يملكها TeamA من Contoso. TeamA لديه نهج DLP P1. هناك 3 طرق لمشاركة قناة:
    - **المشاركة مع العضو**: يمكنك دعوة المستخدم1 من Contoso للانضمام إلى القناة المشتركة دون أن تجعله عضوا في TeamA. سيتم تغطية كل شخص في هذه القناة المشتركة، بما في ذلك المستخدم1، بواسطة P1.
    - **المشاركة مع الفريق (داخليا)**: يمكنك مشاركة القناة مع فريق آخر TeamB في Contoso. قد يكون لدى فريق آخر نهج DLP مختلف، ولكن هذا لا يهم. سيتم تطبيق P1 على جميع الأشخاص في هذه القناة المشتركة، بما في ذلك مستخدمي TeamA و TeamB.
    - **المشاركة مع الفريق (المستأجر عبر المستأجر)**: يمكنك مشاركة القناة مع فريق TeamF في Fabrikam. قد يكون لدى شركة Fabrikam نهج DLP الخاص بها، ولكن هذا لا يهم. سيتم تطبيق P1 على جميع الأشخاص في هذه القناة المشتركة، بما في ذلك مستخدمي TeamA (Contoso) و TeamF (Fabrikam).
 
## <a name="dlp-licensing-for-microsoft-teams"></a>ترخيص DLP Microsoft Teams

[تم توسيع إمكانات منع](dlp-learn-about-dlp.md) فقدان البيانات لتتضمن Microsoft Teams رسائل الدردشة والقناة، بما في ذلك **رسائل القناة الخاصة** ل:

- Office 365 E5/A5/G5
- Microsoft 365 E5/A5/G5
- Microsoft 365 E5/A5/G5 حماية المعلومات والحوكمة
- Microsoft 365 E5/A5/G5/F5 والتوافق مع الأمان & F5

Office 365 Microsoft 365 E3 حماية DLP SharePoint عبر الإنترنت OneDrive و Exchange Online. يشمل ذلك أيضا الملفات التي تمت مشاركتها عبر Teams لأن Teams يستخدم SharePoint عبر الإنترنت OneDrive مشاركة الملفات.

يتطلب دعم حماية DLP في Teams الدردشة E5.

لمعرفة المزيد حول متطلبات الترخيص، راجع Microsoft 365 Tenant-Level [ترخيص الخدمات](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).

> [!IMPORTANT]
> تنطبق DLP فقط على الرسائل الفعلية في المحادثة أو مؤشر ترابط القناة. لا يتم تضمين إعلامات النشاط، التي تتضمن معاينة قصيرة للرسالة وتظهر استنادا إلى إعدادات إعلامات المستخدم،  في Teams DLP. ستبقى أي معلومات حساسة موجودة في جزء الرسالة التي تظهر في المعاينة مرئية في الإعلام حتى بعد تطبيق نهج DLP وإزالة المعلومات الحساسة للرسالة نفسها.

## <a name="scope-of-dlp-protection"></a>نطاق حماية DLP

يتم تطبيق حماية DLP بشكل مختلف على Teams أخرى.

|عند تحديد نطاق النهج بواسطة |هذه Teams الكيانات |ستتوفر حماية DLP|
|---------|---------|---------|
|حسابات المستخدمين الفردية     |دردشات 1:1/n         |نعم         |
|     |رسائل القناة القياسية والمشتركة         |لا         |
|     |رسائل القناة الخاصة         |نعم         |
|مجموعات الأمان/قوائم التوزيع  | دردشات 1:1/n         |نعم         |
|     |رسائل القناة القياسية والمشتركة  |لا         |
|     |رسائل القناة الخاصة         |نعم        |
|Microsoft 365 المجموعة    |دردشات 1:1/n          |لا         |
|     |رسائل القناة القياسية والمشتركة          |نعم        |
|     |رسائل القناة الخاصة|لا| 


## <a name="policy-tips-help-educate-users"></a>تلميحات النهج تساعد على تعليم المستخدمين

على غرار طريقة عمل DLP في [عملاء Exchange](data-loss-prevention-policies.md#policy-evaluation-in-exchange-online-outlook-and-outlook-on-the-web) و Outlook و Outlook على ويب و [SharePoint عبر](data-loss-prevention-policies.md#policy-evaluation-in-onedrive-for-business-and-sharepoint-online-sites) الإنترنت و OneDrive for Business و [عملاء سطح مكتب Office](data-loss-prevention-policies.md#policy-evaluation-in-the-office-desktop-programs)، تظهر تلميحات النهج عند تشغيل أحد الإجراءات باستخدام نهج DLP. فيما يلي مثال على تلميح نهج:

![إعلام الرسالة المحظورة في Teams.](../media/dlp-teams-blockedmessage-notification.png)

هنا، حاول المرسل مشاركة رقم الضمان الاجتماعي في Microsoft Teams أخرى. يفتح **الارتباط ما الذي يمكنني فعله؟** مربع حوار يوفر خيارات للمرسل لحل المشكلة. لاحظ أنه يمكن للمرسل أن يختار تجاوز النهج، أو إعلام المسؤول لمراجعته وحله.

![خيارات لحل الرسالة المحظورة.](../media/dlp-teams-blockedmessage-possibleactions.png)

في مؤسستك، يمكنك اختيار السماح للمستخدمين بتجاوز نهج DLP. عند تكوين نهج DLP، يمكنك استخدام تلميحات النهج الافتراضية أو [تخصيص](#to-customize-policy-tips) تلميحات النهج لم المؤسسة.

بالعودة إلى مثالنا، حيث شارك مرسل رقم الضمان الاجتماعي في قناة Teams، إليك ما شاهده المستلم:

> [!div class="mx-imgBorder"]
> ![تم حظر الرسالة.](../media/dlp-teams-blockedmessage-notification-to-user.png)

### <a name="to-customize-policy-tips"></a>لتخصيص تلميحات النهج

لتنفيذ هذه المهمة، يجب أن يتم تعيين دور له أذونات لتحرير سياسات DLP. لمعرفة المزيد، راجع [الأذونات](data-loss-prevention-policies.md#permissions).

1. انتقل إلى مركز التوافق ([https://compliance.microsoft.com](https://compliance.microsoft.com)) ثم سجل الدخول.

2. اختر **منع فقدان** **البياناتPolicy** > .

3. حدد نهج، ثم إلى بجانب **إعدادات النهج**، اختر **تحرير**.

4. يمكنك إنشاء قاعدة جديدة أو تحرير قاعدة موجودة في النهج.

    > [!div class="mx-imgBorder"]
    > ![تحرير قاعدة لن نهج.](../media/dlp-teams-editrule.png)

5. على علامة **التبويب إعلامات** المستخدم، حدد **تخصيص نص البريد الإلكتروني** و/أو **تخصيص خيارات نص تلميح** النهج.

    > [!div class="mx-imgBorder"]
    > ![تخصيص إعلامات المستخدم وتلميحات النهج.](../media/dlp-teams-editrule-usernotifications.png)<br/>  

6. حدد النص الذي تريد استخدامه في إعلامات البريد الإلكتروني و/أو تلميحات النهج، ثم اختر **حفظ**.

7. على علامة **التبويب إعدادات النهج** ، اختر **حفظ**.

اسمح لساعة واحدة تقريبا لكي تعمل التغييرات عبر مركز البيانات الخاص بك والمزامنة مع حسابات المستخدمين.
 <!-- why are these syncing to user accounts? -->

## <a name="add-microsoft-teams-as-a-location-to-existing-dlp-policies"></a>إضافة Microsoft Teams كم موقع إلى سياسات DLP الموجودة

لتنفيذ هذه المهمة، يجب أن يتم تعيين دور له أذونات لتحرير سياسات DLP. لمعرفة المزيد، راجع [الأذونات](data-loss-prevention-policies.md#permissions).

1. انتقل إلى مركز التوافق ([https://compliance.microsoft.com](https://compliance.microsoft.com)) ثم سجل الدخول.

2. اختر **منع فقدان** **البياناتPolicy** > .

3. حدد نهج، وانظر إلى القيم الموجودة ضمن **المواقع**. إذا رأيت Teams **رسائل الدردشة** والقناة، تكون قد تم إعداد كل شيء. إذا لم تفعل ذلك، انقر فوق **تحرير**.

    > [!div class="mx-imgBorder"]
    > ![مواقع النهج الحالي.](../media/dlp-teams-editexistingpolicy.png)

4. في العمود **الحالة**، قم تشغيل نهج Teams **رسائل القناة والدردشة**.

    > [!div class="mx-imgBorder"]
    > ![DLP Teams الدردشات والقنوات.](../media/dlp-teams-addteamschatschannels.png)

5. على علامة **التبويب اختيار المواقع** ، احتفظ بإعداد كل الحسابات الافتراضي، أو حدد **السماح لي باختيار مواقع معينة**. يمكنك تحديد:

    1. ما يصل إلى 1000 حساب فردي لتضمينها أو استبعادها
    1. قوائم التوزيع ومجموعات الأمان لتضمينها أو استبعادها. 
    <!-- 1. the shared mailbox of a shared channel. **This is a public preview feature.**--> 
    
6. ثم اختر **التالي**.

7. انقر فوق **حفظ**.

اسمح لساعة واحدة تقريبا لكي تعمل التغييرات عبر مركز البيانات الخاص بك والمزامنة مع حسابات المستخدمين.
<!-- again, why user accounts? -->

## <a name="define-a-new-dlp-policy-for-microsoft-teams"></a>تعريف نهج DLP جديد Microsoft Teams

لتنفيذ هذه المهمة، يجب أن يتم تعيين دور له أذونات لتحرير سياسات DLP. لمعرفة المزيد، راجع [الأذونات](data-loss-prevention-policies.md#permissions).

1. انتقل إلى مركز التوافق ([https://compliance.microsoft.com](https://compliance.microsoft.com)) ثم سجل الدخول.

2. اختر **منع فقدان** **البياناتPolicy** >  > **+ إنشاء نهج**.

3. اختر [قالبا](data-loss-prevention-policies.md#dlp-policy-templates)، ثم اختر **التالي**.

    في مثالنا، اخترنا قالب بيانات المعلومات الشخصية في الولايات المتحدة.

    > [!div class="mx-imgBorder"]
    > ![قالب الخصوصية لن نهج DLP.](../media/dlp-teams-createnewpolicy-template.png)<br/>

4. على علامة **التبويب تسمية النهج** ، حدد اسما ووصفا النهج، ثم اختر **التالي**.

5. على علامة **التبويب اختيار المواقع** ، احتفظ بإعداد كل الحسابات الافتراضي، أو حدد **السماح لي باختيار مواقع معينة**. يمكنك تحديد:

    1. ما يصل إلى 1000 حساب فردي لتضمينها أو استبعادها
    1. قوائم التوزيع ومجموعات الأمان لتضمينها أو استبعادها. **هذه ميزة معاينة عامة.**
    <!-- 1. the shared mailbox of a shared channel. **This is a public preview feature.**-->  

    ![مواقع نهج DLP.](../media/dlp-teams-selectlocationsnewpolicy.png)

    > [!NOTE]
    > إذا كنت تريد التأكد من عدم مشاركة المستندات التي تحتوي على معلومات حساسة بشكل غير مناسب في Teams، فتأكد من تشغيل SharePoint مواقع  OneDrive وحسابات **OneDrive**، إلى جانب رسائل Teams والدردشة والقنوات **.**

6. على علامة **التبويب** إعدادات النهج، ضمن تخصيص نوع المحتوى الذي تريد حمايته، احتفظ بإعدادات بسيطة افتراضية، أو اختر استخدام الإعدادات **المتقدمة**، ثم اختر **التالي**. إذا اخترت إعدادات متقدمة، يمكنك إنشاء قواعد نهجك أو تحريرها. للحصول على تعليمات حول ذلك، راجع [الإعدادات البسيطة مقابل الإعدادات المتقدمة](data-loss-prevention-policies.md#simple-settings-vs-advanced-settings).

7.  على علامة **التبويب إعدادات** النهج، ضمن **ما الذي تريد فعله** إذا اكتشفنا معلومات حساسة؟، راجع الإعدادات. إليك المكان الذي يمكنك فيه اختيار الاحتفاظ بتلميحات النهج الافتراضية وإعامات البريد [الإلكتروني أو](use-notifications-and-policy-tips.md) تخصيصها.

    > [!div class="mx-imgBorder"]
    > ![إعدادات نهج DLP مع التلميحات والإعلامات.](../media/dlp-teams-policysettings-tipsemails.png)

    عند الانتهاء من مراجعة الإعدادات أو تحريرها، اختر **التالي**.

8. على علامة  التبويب إعدادات النهج، ضمن هل تريد تشغيل النهج أو اختبار الأشياء أولا **؟**، اختر ما إذا كنت تريد تشغيل النهج أو اختباره أولا أو إبقه [](dlp-overview-plan-for-dlp.md#policy-deployment)م إيقاف التشغيل الآن، ثم اختر **التالي**.

    > [!div class="mx-imgBorder"]
    > ![حدد ما إذا كنت تريد تشغيل النهج أم لا.](../media/dlp-teams-policysettings-turnonnow.png)

9. على علامة **التبويب مراجعة الإعدادات** ، راجع إعدادات النهج الجديد. اختر **تحرير** من أجل إجراء تغييرات. عند الانتهاء، اختر **إنشاء**.

السماح بساعة واحدة تقريبا لكي يعمل النهج الجديد في مركز البيانات والمزامنة مع حسابات المستخدمين.

## <a name="prevent-external-access-to-sensitive-documents"></a>منع الوصول الخارجي إلى المستندات الحساسة

للتأكد من SharePoint الوصول إلى المستندات التي تحتوي على معلومات حساسة من قبل ضيوف خارجيين إما من SharePoint أو Teams بشكل افتراضي، حدد ما يلي:

- يمكنك التأكد من حماية المستندات حتى تقوم بمسح DLP ووضع علامة عليها كآمنة للمشاركة من خلال وضع علامة على الملفات الجديدة كحساسة [بشكل افتراضي](/sharepoint/sensitive-by-default).

- بنية نهج DLP الموصى بها

    - **الشروط**
        - يحتوي المحتوى على أي من أنواع المعلومات الحساسة التالية: [تحديد كل ما ينطبق]
        
        - يتم مشاركة المحتوى من Microsoft 365 مع أشخاص من خارج المؤسسة
        
          > [!div class="mx-imgBorder"]
          > ![شروط DLP للكشف عن المشاركة الخارجية للمحتوى الحساس.](../media/dlp-teams-external-sharing/external-condition.png)

    - **الإجراءات**
        - تقييد الوصول إلى المحتوى للمستخدمين الخارجيين
        
        - إعلام المستخدمين بالبريد الإلكتروني وتلميحات النهج
        
        - إرسال تقارير الأحداث إلى المسؤول
        
        > [!div class="mx-imgBorder"]
        > ![إجراء DLP لحظر المشاركة الخارجية للمحتوى الحساس.](../media/dlp-teams-external-sharing/external-action.png)

نهج DLP أثناء العمل عند محاولة مشاركة مستند في SharePoint يحتوي على معلومات حساسة مع ضيف خارجي:

> [!div class="mx-imgBorder"]
> ![تم حظر المشاركة الخارجية.](../media/dlp-teams-external-sharing/external-sharing-blocked.png)


نهج DLP أثناء العمل عندما يحاول الضيف فتح مستند في Teams مع حظر خارجي:

> [!div class="mx-imgBorder"]
> ![تم حظر الوصول الخارجي.](../media/dlp-teams-external-sharing/external-access-blocked.png)

## <a name="related-articles"></a>المقالات ذات الصلة

- [إنشاء نهج DLP واختباره وضبطه](create-test-tune-dlp-policy.md)
- [إرسال إعلامات بالبريد الإلكتروني وإظهار تلميحات النهج لنهج DLP](use-notifications-and-policy-tips.md)
