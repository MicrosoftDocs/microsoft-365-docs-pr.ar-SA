---
title: دليل المبادئ التجريبي Microsoft Defender for Business
f1.keywords:
- NOCSH
ms.author: deniseb
author: denisebmsft
manager: dansimp
audience: Admin
ms.topic: article
ms.collection: m365-security-compliance
ms.localizationpriority: high
ms.prod: m365-security
ms.technology: mdb
search.appverid:
- MOE150
- MET150
description: تحقيق أقصى استفادة من الإصدار التجريبي من Defender for Business باستخدام دليل المبادئ هذا. ابدأ الإعداد بسرعة وابدأ باستخدام قدرات الأمان الجديدة.
ms.custom: trial-playbook
ms.openlocfilehash: 73a3bd1421b9891c07e582e791df2dfd86088ccf
ms.sourcegitcommit: c6f1486617b39565bfd8f662ee6ad65a9cefd3e3
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 06/29/2022
ms.locfileid: "66530754"
---
# <a name="trial-playbook-microsoft-defender-for-business"></a>دليل المبادئ التجريبي: Microsoft Defender for Business

**مرحبا بك في دليل المبادئ التجريبي ل Defender for Business!** 

دليل المبادئ هذا هو دليل بسيط لمساعدتك على تحقيق أقصى استفادة من الإصدار التجريبي المجاني لمدة 30 يوما. باستخدام التوصيات الواردة في هذه المقالة من فريق Microsoft Defender، ستتعرف على كيفية مساعدة Defender for Business في الارتقاء بأمانك من الحماية التقليدية من الفيروسات إلى حماية الجيل التالي واكتشاف نقطة النهاية والاستجابة لها إدارة المخاطر والثغرات الأمنية. 

## <a name="what-is-defender-for-business"></a>ما هو Defender for Business؟ 

Defender for Business هو حل أمان نقطة نهاية جديد تم تصميمه خصيصا للشركات الصغيرة والمتوسطة الحجم (ما يصل إلى 300 موظف). باستخدام حل أمان نقطة النهاية هذا، تكون أجهزة مؤسستك محمية بشكل أفضل من برامج الفدية الضارة والبرامج الضارة والتصيد الاحتيالي والتهديدات الأخرى. 

:::image type="content" source="media/mdb-offering-overview.png" alt-text="Microsoft Defender for Business الميزات والقدرات.":::

**لنبدأ!**

## <a name="set-up-your-trial"></a>إعداد الإصدار التجريبي

فيما يلي كيفية إعداد اشتراكك التجريبي:

1. [إضافة مستخدمين وتعيين التراخيص](#step-1-add-users-and-assign-licenses).
2. [تفضل بزيارة مدخل Microsoft 365 Defender](#step-2-visit-the-microsoft-365-defender-portal).
3. [استخدم معالج الإعداد](#step-3-use-the-setup-wizard-in-defender-for-business-recommended).
4. [إعداد وتكوين Defender for Business](#step-4-set-up-and-configure-defender-for-business).

### <a name="step-1-add-users-and-assign-licenses"></a>الخطوة 1: إضافة مستخدمين وتعيين التراخيص

بمجرد التسجيل في Defender for Business، فإن خطوتك الأولى هي **[إضافة مستخدمين وتعيين التراخيص](mdb-add-users.md)**.

> [!NOTE]
> يجب أن تكون مسؤولا عاما لتنفيذ هذه المهمة. الشخص الذي سجل شركتك للحصول على Microsoft 365 أو Defender for Business هو المسؤول العام بشكل افتراضي. [تعرف على المزيد حول الأدوار والأذونات](mdb-roles-permissions.md).

### <a name="step-2-visit-the-microsoft-365-defender-portal"></a>الخطوة 2: زيارة مدخل Microsoft 365 Defender
 
مدخل Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)) هو متجرك الوحيد لاستخدام Defender for Business وإدارته. يتضمن شعار ترحيب و وسائل شرح لمساعدتك على البدء، وبطاقات تعرض المعلومات ذات الصلة، وشريط تنقل لمنحك إمكانية الوصول السهل إلى الميزات والقدرات المختلفة. 

- **[تفضل بزيارة مدخل Microsoft 365 Defender](mdb-get-started.md)**.
- **[استكشف شريط التنقل](mdb-get-started.md#the-navigation-bar)** على الجانب الأيمن من الشاشة للوصول إلى الحوادث وعرض التقارير وإدارة نهج الأمان وإعداداتك. 

### <a name="step-3-use-the-setup-wizard-in-defender-for-business-recommended"></a>الخطوة 3: استخدام معالج الإعداد في Defender for Business (مستحسن)

تم تصميم Defender for Business لتوفير الوقت والجهد للشركات الصغيرة والمتوسطة الحجم. يمكنك إجراء الإعداد والتكوين الأوليين باستخدام معالج الإعداد. يرشدك معالج الإعداد من خلال منح حق الوصول إلى فريق الأمان وإعداد إعلامات البريد الإلكتروني لفريق الأمان الخاص بك وإعداد أجهزة Windows الخاصة بالشركة. **[استخدم معالج الإعداد](mdb-use-wizard.md)**.

> [!NOTE]
> يمكنك استخدام معالج الإعداد مرة واحدة فقط. 

#### <a name="setup-wizard-flow-what-to-expect"></a>تدفق معالج الإعداد: ما يجب توقعه

> [!TIP]
> **استخدام معالج الإعداد اختياري** (راجع [ماذا يحدث إذا لم أستخدم المعالج؟](mdb-use-wizard.md#what-happens-if-i-dont-use-the-wizard)). إذا اخترت عدم استخدام المعالج، أو إذا كان المعالج مغلقا قبل اكتمال عملية الإعداد، يمكنك إكمال عملية الإعداد والتكوين بنفسك. راجع [الخطوة 4](#step-4-set-up-and-configure-defender-for-business). 

1. **[تعيين أذونات المستخدم](mdb-roles-permissions.md#view-or-edit-role-assignments)**. منح فريق الأمان حق الوصول إلى مدخل Microsoft 365 Defender.

2. **[إعداد إعلامات البريد الإلكتروني](mdb-email-notifications.md#view-and-edit-email-notifications)** لفريق الأمان.

3. **[إعداد أجهزة Windows وتكوينها](mdb-onboard-devices.md)**. يساعد إلحاق الأجهزة على الفور على حماية هذه الأجهزة من اليوم الأول.

   > [!NOTE]
   > أثناء استخدام معالج الإعداد، سيكتشف النظام ما إذا كان لديك أجهزة Windows مسجلة بالفعل في Intune. سيتم سؤالك عما إذا كنت تريد استخدام الإلحاق التلقائي لجميع هذه الأجهزة أو بعضها. يمكنك إلحاق جميع أجهزة Windows في وقت واحد، أو تحديد أجهزة معينة للبدء بها، ثم إضافة المزيد من الأجهزة لاحقا. [تعرف على المزيد حول الإلحاق التلقائي](mdb-use-wizard.md#what-is-automatic-onboarding).
   
   لإلحاق الأجهزة الأخرى، راجع [الخطوة 4](#step-4-set-up-and-configure-defender-for-business).

4.  **[قم بعرض نهج الأمان وتحريرها إذا لزم الأمر](mdb-configure-security-settings.md)**. يتضمن Defender for Business نهج أمان افتراضية لحماية الجيل التالي وحماية جدار الحماية التي يمكن تطبيقها على أجهزة شركتك. تستخدم نهج الأمان التي تم تكوينها مسبقا الإعدادات الموصى بها بحيث تكون محميا بمجرد إلحاق أجهزتك ب Defender for Business. ولا تزال لديك القدرة على تحرير النهج أو إنشاء نهج جديدة. 

### <a name="step-4-set-up-and-configure-defender-for-business"></a>الخطوة 4: إعداد وتكوين Defender for Business

إذا اخترت عدم استخدام معالج الإعداد، فإن الرسم التخطيطي التالي يصور [عملية الإعداد والتكوين الإجمالية](mdb-setup-configuration.md#the-setup-and-configuration-process) ل Defender for Business. 

[:::image type="content" source="media/mdb-setup-process-2.png" alt-text="عملية الإعداد والتكوين Microsoft Defender for Business.":::](mdb-setup-configuration.md)

إذا استخدمت معالج الإعداد، ولكنك تحتاج إلى إلحاق المزيد من الأجهزة، مثل الأجهزة غير التي تعمل بنظام Windows، فانتقل مباشرة إلى الخطوة 4 في الإجراء التالي: 

1. **[راجع متطلبات](mdb-requirements.md)** تكوين Defender for Business واستخدامه. 

2. **[تعيين الأدوار والأذونات](mdb-roles-permissions.md)** في مدخل Microsoft 365 Defender.

   - [تعرف على الأدوار في Defender for Business](mdb-roles-permissions.md#roles-in-defender-for-business). 
   - [عرض تعيينات الأدوار أو تحريرها لفريق الأمان.](mdb-roles-permissions.md#view-or-edit-role-assignments)

3. **[إعداد إعلامات البريد الإلكتروني](mdb-email-notifications.md)** لفريق الأمان.

   - [تعرف على أنواع إعلامات البريد الإلكتروني](mdb-email-notifications.md#types-of-email-notifications).
   - [عرض إعدادات إعلام البريد الإلكتروني وتحريرها](mdb-email-notifications.md#view-and-edit-email-notifications).

4. **[إلحاق الأجهزة](mdb-onboard-devices.md)**. باستخدام Defender for Business، لديك العديد من الخيارات للاختيار من بينها لإلحاق أجهزة شركتك. ابدأ بتحديد نظام التشغيل الذي تريد إلحاقه. 

   | الاجهزه | أساليب الإلحاق |
   |:---|:---|
   | [عملاء Windows](mdb-onboard-devices.md) | اختر أحد الخيارات التالية لإلحاق أجهزة عميل Windows ب Defender for Business:<br/>- البرنامج النصي المحلي (لإلحاق الأجهزة يدويا في مدخل Microsoft 365 Defender)<br/>- نهج المجموعة (إذا كنت تستخدم بالفعل نهج المجموعة وتفضل هذا الأسلوب)<br/>- Microsoft Intune (*مستحسن*؛ مضمن في [Microsoft 365 Business Premium](../../business-premium/index.md)) |
   | [أجهزة كمبيوتر macOS](mdb-onboard-devices.md) | اختر أحد الخيارات التالية لإلحاق أجهزة macOS:<br/>- البرنامج النصي المحلي لنظام التشغيل macOS (*مستحسن*) <br/>- Microsoft Intune لنظام التشغيل macOS (Intune مضمن في [Microsoft 365 Business Premium](../../business-premium/index.md))<br/><br/>نوصي باستخدام برنامج نصي محلي لإلحاق أجهزة macOS. على الرغم من أنه يمكنك [إعداد التسجيل لأجهزة macOS في Intune](/mem/intune/enrollment/macos-enroll)، فإن البرنامج النصي المحلي هو أبسط طريقة لإلحاق أجهزة macOS ب Defender for Business. |
   | خوادم Windows Server وLinux | *خوادم Windows Server وLinux غير معتمدة حاليا. ستتوفر قدرات إلحاق الخادم والأمان قريبا إلى Defender for Business*. |
   | [الأجهزة المحمولة](mdb-onboard-devices.md) | ستحتاج Microsoft Intune إلى إلحاق الأجهزة المحمولة، مثل أجهزة Android وiOS/iPadOS. إذا كان لديك [Microsoft 365 Business Premium](../../business-premium/index.md)، فقد قمت ب Intune كجزء من اشتراكك. يمكن أيضا شراء Intune بشكل منفصل. راجع الموارد التالية للحصول على المساعدة في تسجيل هذه الأجهزة في Intune:<br/>- [تسجيل أجهزة Android](/mem/intune/enrollment/android-enroll)<br/>- [تسجيل أجهزة iOS أو iPadOS](/mem/intune/enrollment/ios-enroll) |

5. **[قم بعرض نهج الأمان الخاصة بك، وإذا لزم الأمر، فكونها](mdb-configure-security-settings.md)**. بعد إلحاق أجهزة شركتك Microsoft Defender for Business، تكون خطوتك التالية هي عرض نهج الأمان وإعداداتك وتحريرها إذا لزم الأمر. يتضمن Defender for Business نهج أمان مكونة مسبقا تستخدم الإعدادات الموصى بها. ومع ذلك، يمكنك تحرير الإعدادات لتناسب احتياجات عملك.

   | العمل | الوصف |
   |:---|:---|
   | [اختر مكان إدارة نهج الأمان والأجهزة](mdb-configure-security-settings.md#choose-where-to-manage-security-policies-and-devices). | إذا قمت بتحديد [عملية التكوين المبسطة](mdb-simplified-configuration.md)، يمكنك عرض نهج الأمان الخاصة بك وإدارتها في مدخل Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)). ومع ذلك، لا تقتصر على هذا الخيار. إذا كنت تستخدم [Intune](/mem/intune/protect/)، يمكنك الاستمرار في استخدام مركز إدارة Microsoft إدارة نقاط النهاية لإدارة نهج الأمان والأجهزة. |
   | [عرض نهج الحماية من الجيل التالي أو تحريرها](mdb-configure-security-settings.md#view-or-edit-your-next-generation-protection-policies). | تتضمن إعدادات الحماية من الجيل التالي الحماية في الوقت الحقيقي، والحظر من النظرة الأولى، وحماية الشبكة، والإجراءات التي يجب اتخاذها على التطبيقات التي يحتمل أن تكون غير مرغوب فيها، ومسح الحماية من الفيروسات المجدول.  |
   | [عرض نهج جدار الحماية أو تحريرها](mdb-configure-security-settings.md#view-or-edit-your-firewall-policies-and-custom-rules). | تحدد حماية جدار الحماية نسبة استخدام الشبكة المسموح لها بالتدفق من أو إلى أجهزة شركتك. يمكن استخدام [القواعد المخصصة](mdb-custom-rules-firewall.md) لتعريف الاستثناءات لنهج جدار الحماية. |
   | [إعداد تصفية محتوى ويب](mdb-configure-security-settings.md#set-up-web-content-filtering). | تتيح تصفية محتوى الويب لفريق الأمان تعقب الوصول إلى مواقع الويب وتنظيمها استنادا إلى فئات المحتوى الخاصة بها، مثل محتوى البالغين أو النطاق الترددي العالي أو المسؤولية القانونية أو الترفيه أو غير مصنف. |
   | [مراجعة الإعدادات للميزات المتقدمة](mdb-configure-security-settings.md#review-settings-for-advanced-features). | في Defender for Business، يتم تكوين ميزات الأمان مسبقا باستخدام الإعدادات الموصى بها؛ ومع ذلك، يمكنك مراجعتها، وإذا لزم الأمر، فحرر الإعدادات لتناسب احتياجات عملك. <br/><br/>للوصول إلى إعدادات الميزات المتقدمة، في مدخل Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com))، انتقل إلى **الميزات** >  المتقدمة **العامة** > **لنقاط النهاية** **للإعدادات** > . |
   | [عرض إعدادات أخرى وتحريرها](mdb-configure-security-settings.md#access-your-settings-in-the-microsoft-365-defender-portal) في مدخل Microsoft 365 Defender. | بالإضافة إلى نهج الأمان التي يتم تطبيقها على الأجهزة، هناك إعدادات أخرى يمكنك عرضها وتحريرها في Defender for Business. على سبيل المثال، يمكنك تحديد المنطقة الزمنية التي يجب استخدامها، ويمكنك إلحاق (أو إلغاء إلحاق) الأجهزة. |

## <a name="start-using-defender-for-business"></a>بدء استخدام Defender for Business

في ال 30 يوما القادمة، نوصي بتجربة قدرات الأمان الجديدة، كما هو موضح في الأقسام التالية:

- [استخدام لوحة معلومات إدارة الثغرات الأمنية & المخاطر](#use-your-threat--vulnerability-management-dashboard) 
- [عرض التهديدات المكتشفة والاستجابة لها](#view-and-respond-to-detected-threats)
- [مراجعة نهج الأمان](#review-security-policies)
- [الاستعداد لإدارة الأمان المستمرة](#prepare-for-ongoing-security-management)

### <a name="use-your-threat--vulnerability-management-dashboard"></a>استخدام لوحة معلومات إدارة الثغرات الأمنية & المخاطر

يتضمن Defender for Business لوحة معلومات إدارة المخاطر & الثغرات الأمنية المصممة لتوفير وقت فريق الأمان والجهد. [استخدم لوحة معلومات إدارة المخاطر & الثغرات الأمنية](mdb-view-tvm-dashboard.md).

- عرض درجة التعرض، المقترنة بالأجهزة في مؤسستك.   
- عرض أفضل توصيات الأمان، مثل معالجة الاتصالات الضعيفة مع الأجهزة، أو تشغيل حماية جدار الحماية، أو تحديث تعريفات برنامج الحماية من الفيروسات من Microsoft Defender.   
- عرض أنشطة المعالجة، مثل أي ملفات تم إرسالها إلى العزل، أو الثغرات الأمنية الموجودة على الأجهزة.

### <a name="view-and-respond-to-detected-threats"></a>عرض التهديدات المكتشفة والاستجابة لها

مع اكتشاف التهديدات وتشغيل التنبيهات، يتم إنشاء الحوادث. يمكن لفريق الأمان في مؤسستك عرض الحوادث وإدارتها في مدخل Microsoft 365 Defender. [عرض التهديدات المكتشفة والاستجابة لها](mdb-view-manage-incidents.md). 

- [عرض الأحداث وإدارتها](mdb-view-manage-incidents.md).
- [الاستجابة للتهديدات والتخفيف من حدتها](mdb-respond-mitigate-threats.md).
- [مراجعة إجراءات التوسط في مركز الصيانة](mdb-review-remediation-actions.md).
- [عرض التقارير واستخدامها](mdb-reports.md).

### <a name="review-security-policies"></a>مراجعة نهج الأمان

في Defender for Business، يتم تكوين إعدادات الأمان من خلال النهج التي يتم تطبيقها على الأجهزة. يتضمن Defender for Business سياسات تم تكوينها مسبقا للمساعدة في حماية أجهزة شركتك بمجرد إلحاقها، ما يحمي مؤسستك من تهديدات أمان الهوية والجهاز والتطبيق والمستند. [مراجعة نهج الأمان](mdb-view-edit-create-policies.md).

- [تعرف على نهجك الافتراضية](mdb-view-edit-create-policies.md#default-policies-in-defender-for-business).
- [عرض النهج الموجودة](mdb-view-edit-create-policies.md#view-your-existing-policies).
- [فهم ترتيب النهج](mdb-policy-order.md). 
- [فهم إعدادات تكوين الجيل التالي](mdb-next-gen-configuration-settings.md).
- [راجع إعدادات جدار الحماية الافتراضية](mdb-firewall.md#default-firewall-settings-in-defender-for-business).
- [فهم إعدادات جدار الحماية التي يمكنك تكوينها](mdb-firewall.md#firewall-settings-you-can-configure-in-defender-for-business).
- [إعداد تصفية محتوى ويب](mdb-configure-security-settings.md#set-up-web-content-filtering). تمكن تصفية محتوى الويب فريق الأمان من تعقب الوصول إلى مواقع الويب وتنظيمه استنادا إلى فئات المحتوى الخاصة بها. لا يتم تشغيله بشكل افتراضي، لذلك ستحتاج إلى إعداده إذا كنت تريد هذه الإمكانية لمؤسستك.
  
### <a name="prepare-for-ongoing-security-management"></a>الاستعداد لإدارة الأمان المستمرة

تتطلب أحداث الأمان الجديدة، مثل عمليات الكشف عن التهديدات على جهاز، وإضافة أجهزة جديدة، والموظفين الذين ينضمون إلى المؤسسة أو يغادرونها إدارة أمانك. في Microsoft Defender for Business، هناك العديد من الطرق لإدارة أمان الجهاز. 

- [عرض قائمة بالأجهزة الملحقة](mdb-manage-devices.md#view-the-list-of-onboarded-devices) لمعرفة مستوى المخاطر ومستوى التعرض وحالتها الصحية.
- [اتخاذ إجراء على جهاز](mdb-manage-devices.md#take-action-on-a-device-that-has-threat-detections) لديه عمليات الكشف عن التهديدات.
- [إلحاق جهاز ب Defender for Business](mdb-manage-devices.md#onboard-a-device).
- [إيقاف تشغيل جهاز من Defender for Business](mdb-manage-devices.md#offboard-a-device).

## <a name="additional-resources"></a>موارد إضافية

- [نظرة عامة على Microsoft Defender for Business](mdb-overview.md)
- [البرامج التعليمية والمحاكاة في Microsoft Defender for Business](mdb-tutorials.md)
- [فيديو: حماية Enterprise-Grade للشركات الصغيرة & متوسطة الحجم](https://youtu.be/umhUNzMqZto)
- [الحصول على Microsoft Defender for Business](get-defender-business.md)
