---
title: الأجهزة المشتركة
description: كيفية استخدام وضع الجهاز المشترك ومتى
keywords: Microsoft Managed Desktop، Microsoft 365، الخدمة، الوثائق
ms.service: m365-md
author: tiaraquan
ms.author: tiaraquan
ms.localizationpriority: medium
ms.collection: M365-modern-desktop
manager: dougeby
ms.topic: article
ms.openlocfilehash: 5cb1f14f8f9dc8c645621c1a12c651db8a790b71
ms.sourcegitcommit: e13c8fc28c68422308c9d356109797cfcf6f77be
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/14/2022
ms.locfileid: "64841928"
---
# <a name="shared-devices"></a>الأجهزة المشتركة

يسمح لك Microsoft Managed Desktop بتسجيل الأجهزة في "وضع الجهاز المشترك"، على غرار وضع الجهاز المشترك الذي يقدمه [Microsoft Intune](/mem/intune/configuration/shared-user-device-settings).

تم تحسين الأجهزة في هذا الوضع للحالات التي لا يرتبط فيها المستخدمون بمكتب واحد ويتغيرون بشكل متكرر في الأجهزة. على سبيل المثال، العاملون في الخطوط الأمامية مثل صرافي البنوك أو موظفو الرعية. يمكنك تطبيق أي من [ملفات تعريف](profiles.md) Microsoft Managed Desktop على الأجهزة في هذا الوضع. تحتوي الأجهزة المسجلة في هذا الوضع على بعض الاختلافات الهامة:

- تم تحسين [تخزين الجهاز](#device-storage) للمستخدمين المشتركين.
- يتم حذف [الحسابات غير النشطة](#deletion-of-inactive-accounts).
- [حسابات الضيوف](#guest-accounts) غير معتمدة بشكل افتراضي.
- [تم تحسين Microsoft 365 التطبيقات](#microsoft-365-apps-for-enterprise) لترخيص المؤسسة للأجهزة المشتركة.

نظرا لأنك تختار استخدام وضع الجهاز المشترك عند نقطة التسجيل في Microsoft Managed Desktop، إذا كنت تريد التغيير خارج هذا الوضع في وقت لاحق، يجب إلغاء تسجيله وتسجيله مرة أخرى.

## <a name="when-to-use-shared-device-mode"></a>متى تستخدم وضع الجهاز المشترك

استخدم وضع الجهاز المشترك في الحالات التي يقوم فيها المستخدمون بتغيير الأجهزة بشكل متكرر.

على سبيل المثال، قد يكون صرافو البنك في موقع واحد يديرون الإيداعات، ولكن ينتقلون إلى مكتب خلفي لمساعدة العملاء في الحصول على رهن. في كل موقع من هذه المواقع، يقوم الجهاز بتشغيل تطبيقات مختلفة ويتم تحسينه لهذه المهام، على الرغم من استخدامها من قبل عدة أشخاص.

عادة ما يتنقل الموظفون في الفنادق بين الغرف والمكاتب في أثناء تفاعلهم مع المرضى. يمكنهم تسجيل الدخول إلى محطة عمل في مكتب، ولكن الاتصال بسطح المكتب البعيد وتدوين الملاحظات، وتكرار هذه العملية في غرفة مختلفة مع مريض مختلف.

## <a name="when-not-to-use-shared-device-mode"></a>متى لا تستخدم وضع الجهاز المشترك

وضع الجهاز المشترك ليس خيارا جيدا في هذه الحالات:

- عندما تحتاج ملفات المستخدم إلى تخزينها محليا بدلا من تخزينها في السحابة.
- إذا كانت تجربة المستخدم تحتاج إلى أن تكون مختلفة للمستخدمين المختلفين على الجهاز.
- إذا كانت مجموعة التطبيقات التي يحتاجها كل مستخدم تختلف اختلافا كبيرا.

## <a name="register-new-devices-using-the-windows-autopilot-self-deploying-mode-profile"></a>تسجيل أجهزة جديدة باستخدام ملف تعريف وضع النشر الذاتي Windows Autopilot

سواء كنت أنت أو شريك تتعامل مع تسجيل الجهاز، يمكنك اختيار استخدام ملف تعريف [وضع النشر الذاتي Windows Autopilot](/mem/autopilot/self-deploying) في Microsoft Managed Desktop.

### <a name="before-you-begin"></a>قبل البدء

راجع متطلبات وضع النشر الذاتي Windows Autopilot:

> [!IMPORTANT]
> لا يمكنك إعادة تسجيل جهاز تلقائيا من خلال Autopilot بعد التوزيع الأولي في وضع النشر الذاتي. بدلا من ذلك، احذف سجل الجهاز في [مركز إدارة إدارة نقاط النهاية من Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431). لحذف سجل الجهاز من مركز الإدارة، حدد **أجهزة DevicesAll**  >  > حدد الأجهزة التي تريد حذفها > **حذف**.  لمزيد من المعلومات، راجع [تحديثات تجربة تسجيل الدخول والنشر Windows Autopilot](https://techcommunity.microsoft.com/t5/intune-customer-success/updates-to-the-windows-autopilot-sign-in-and-deployment/ba-p/2848452).

#### <a name="trusted-platform-module"></a>وحدة النظام الأساسي الموثوق بها

يستخدم وضع النشر الذاتي جهاز TPM 2.0 الخاص بالجهاز لمصادقة الجهاز في مستأجر Azure Active Directory للمؤسسة. لذلك، لا يمكن للأجهزة التي لا تحتوي على TPM 2.0 استخدام هذا الوضع. يجب أن تدعم الأجهزة أيضا إثبات جهاز وحدة النظام الأساسي الموثوق بها. يجب أن تفي جميع أجهزة Windows الجديدة بهذه المتطلبات. تتطلب عملية إثبات وحدة النظام الأساسي الموثوق بها أيضا الوصول إلى مجموعة من عناوين URL HTTPS الفريدة لكل موفر TPM. لمزيد من المعلومات، راجع إدخال وضع النشر الذاتي ل Autopilot والتزويد المسبق ل Autopilot في [متطلبات الشبكات](/mem/autopilot/self-deploying#requirements). لمزيد من المعلومات حول متطلبات برنامج autopilot Windows، راجع [Windows متطلبات برنامج Autopilot](/mem/autopilot/software-requirements).

> [!TIP]
> إذا حاولت نشر وضع النشر الذاتي على جهاز لا يحتوي على دعم TPM 2.0 أو أنه على جهاز ظاهري، فستفشل العملية عند التحقق من الجهاز باستخدام الخطأ التالي: 0x800705B4 خطأ المهلة (لا يتم دعم الأجهزة الظاهرية TPMs ل Hyper-V). لاحظ أيضا أن Windows 10 الإصدار 1903 أو الإصدارات الأحدث مطلوب لاستخدام وضع النشر الذاتي بسبب المشاكل المتعلقة بشهادة جهاز وحدة النظام الأساسي الموثوق بها في Windows 10 الإصدار 1809. نظرا لأن Windows 10 Enterprise 2019 LTSC يستند إلى الإصدار 1809 من Windows 10، فإن وضع النشر الذاتي غير معتمد أيضا على Windows 10 Enterprise LTSC 2019.
>
> لمزيد من المعلومات حول المشكلات الأخرى المعروفة ومراجعة الحلول، راجع [Windows المشاكل المعروفة في Autopilot](/mem/autopilot/known-issues) واستكشاف [أخطاء استيراد جهاز Autopilot وتسجيله وإصلاحها](/mem/autopilot/troubleshoot-device-enrollment).

### <a name="steps-to-register-devices-to-use-the-windows-autopilot-self-deploying-mode-profile"></a>خطوات تسجيل الأجهزة لاستخدام ملف تعريف وضع النشر الذاتي Windows Autopilot

إذا كنت تقوم بتسجيل الأجهزة بنفسك، يجب استيراد أجهزة جديدة إلى جزء أجهزة autopilot Windows.

**لاستيراد أجهزة جديدة إلى جزء أجهزة Windows Autopilot:**

1. جمع [تجزئة الأجهزة](../get-started/manual-registration.md#obtain-the-hardware-hash) للأجهزة الجديدة التي تريد تعيين ملف تعريف وضع النشر الذاتي Windows Autopilot إليها.
2. انتقل إلى مدخل [إدارة نقاط النهاية من Microsoft](https://endpoint.microsoft.com).
2. حدد **الأجهزة** من قائمة التنقل اليمنى.
3. في قسم **النظام الأساسي حسب**، حدد **Windows**. ثم حدد **Windows التسجيل**.
4. في قسم **برنامج Windows Autopilot Deployment**، حدد **الأجهزة**.
5. [قم باستيراد](../get-started/manual-registration.md#register-devices-by-using-the-admin-portal) ملف .CSV الذي يحتوي على كافة تجزئة الأجهزة التي تم جمعها في الخطوة رقم 1.
6. بعد تحميل أجهزة Windows Autopilot، يجب تحرير سمة علامة مجموعة الأجهزة المستوردة حتى تتمكن Microsoft Managed Desktop من تسجيلها باستخدام ملف تعريف وضع النشر الذاتي Windows Autopilot. انظر أدناه لسمات علامة المجموعة. يجب إلحاق **-Shared** بعلامة المجموعة، كما هو موضح في الجدول أدناه:

| ملف تعريف الجهاز | علامة مجموعة Autopilot (الوضع القياسي) | علامة المجموعة (وضع الجهاز المشترك) |
| ----- | ----- | ----- |
| البيانات الحساسة | Microsoft365Managed_SensitiveData |  Microsoft365Managed_SensitiveData-Shared |
| مستخدم الطاقة | Microsoft365Managed_PowerUser | غير معتمد |
| Standard  | Microsoft365Managed_Standard | Microsoft365Managed_Standard-Shared |

> [!WARNING]
> لا تحاول تحرير سمة علامة تبويب المجموعة عن طريق إلحاق **-Shared** إلى الأجهزة التي تم استيرادها مسبقا إلى Windows Autopilot. الأجهزة التي تم استيرادها بالفعل إلى Windows Autopilot، باستخدام إحدى علامات مجموعة Microsoft Managed Desktop بدءا *من Microsoft365Managed_*، ولكن بدون **-Shared** في البداية الملحقة، هي بالفعل جزء من مجموعة Azure Active Directory مختلفة. لا تحتوي مجموعة Azure Active Directory هذه على ملف تعريف وضع النشر الذاتي Windows Autopilot المعين لها. إذا كان عليك إعادة توجيه جهاز موجود ليكون جهازا مشتركا، فيجب حذف الجهاز وإعادة تسجيله في Windows Autopilot مرة أخرى.

إذا كنت تستخدم أجهزة تسجيل شريك، فاتبع الخطوات الواردة في [تسجيل الشريك](../get-started/partner-registration.md)، ولكن قم بإلحاق **-Shared** بعلامة المجموعة، كما هو موضح في الجدول أعلاه.

## <a name="consequences-of-shared-device-mode"></a>عواقب وضع الجهاز المشترك

### <a name="device-storage"></a>تخزين الجهاز

يجب أن يقوم مستخدمو الأجهزة المشتركة بنسخ بياناتهم احتياطيا على السحابة حتى تتمكن من متابعتهم إلى أجهزة أخرى. بمجرد تسجيل الأجهزة في وضع الجهاز المشترك، تأكد من تمكين ميزات إعادة توجيه [الملفات عند الطلب](https://support.microsoft.com/office/save-disk-space-with-onedrive-files-on-demand-for-windows-10-0e6860d3-d9f3-4971-b321-7092438fb38e#:~:text=%20Turn%20on%20Files%20On-Demand%20%201%20Make,files%20as%20you%20use%20them%20box.%20More%20) في OneDrive [والمجلدات المعروفة](/onedrive/redirect-known-folders). يقلل هذا الأسلوب من تأثير كل ملف تعريف مستخدم على تخزين الجهاز. تحذف الأجهزة الموجودة في وضع الجهاز المشترك ملفات تعريف المستخدمين تلقائيا إذا انخفضت مساحة القرص المجانية إلى أقل من 25٪. تتم جدولة هذا النشاط في منتصف الليل في التوقيت المحلي للجهاز، ما لم يصبح التخزين محدودا للغاية.

Microsoft Managed Desktop تستخدم [SharedPC](/mem/intune/configuration/shared-user-device-settings-windows) CSP للقيام بهذه العمليات، لذا تأكد من أنك لا تستخدم موفري خدمة العملاء هذه بنفسك.

> [!IMPORTANT]
> تدريب المستخدمين على أنه بعد تنزيل ملف كبير، يجب أن يؤكدوا أنهم يرون أيقونة الاختيار الخضراء على الملف قبل تسجيل الخروج. إذا تم حذف حسابه كجزء من عمليات التنظيف ولم يتم تحميل الملف بالكامل في OneDrive، فسيتم فقدان الملف بشكل دائم.

### <a name="deletion-of-inactive-accounts"></a>حذف الحسابات غير النشطة

يزيل وضع الجهاز المشترك أي حسابات لم يتم تسجيل الدخول إليها لأكثر من 30 يوما.

### <a name="guest-accounts"></a>حسابات الضيوف

تسمح الأجهزة في وضع الجهاز المشترك فقط بالحسابات المتصلة بمجال. إذا كنت بحاجة إلى حسابات الضيوف على جهاز، يمكنك تقديم [طلب تغيير](../working-with-managed-desktop/admin-support.md) لطلب تمكينها.

### <a name="microsoft-365-apps-for-enterprise"></a>Microsoft 365 Apps for enterprise

تسمح [Microsoft 365 Apps for enterprise](/microsoft-365/managed-desktop/get-started/m365-apps) عادة لمستخدم معين بتثبيت هذه التطبيقات على خمسة أجهزة فقط في الوقت نفسه. في وضع الجهاز المشترك، لا يتم احتساب التطبيقات مقابل الحد الأقصى، حتى يتمكنوا من استخدامها أثناء التجوال بين الأجهزة. Microsoft 365 Apps for enterprise يعمل نشر Microsoft 365 Apps for enterprise وتحديثاتها كالمعتاد.

### <a name="device-profiles"></a>ملفات تعريف الأجهزة

في وضع الجهاز المشترك، يمكنك الحصول على [ملف تعريف جهاز](profiles.md) واحد فقط على جهاز معين. كما أن ملف تعريف جهاز مستخدم Power غير معتمد حاليا في وضع الجهاز المشترك.

### <a name="apps-and-policies-assigned-to-users"></a>التطبيقات والنهج المعينة للمستخدمين

على الأجهزة المشتركة، يجب تعيين أي تطبيقات أو نهج تديرها بنفسك *لمجموعات الأجهزة*، وليس لمجموعات المستخدمين. يضمن التعيين لمجموعات الأجهزة أن كل مستخدم لديه تجربة أكثر اتساقا. الاستثناء [هو Company Portal](#deploying-apps-with-company-portal).

## <a name="limitations-of-shared-device-mode"></a>قيود وضع الجهاز المشترك

### <a name="windows-hello"></a>Windows Hello

يستخدم Windows Hello محاكاة البطاقة الذكية لتخزين [أرقام التعريف الشخصية للمستخدمين مؤقتا](/windows/security/identity-protection/hello-for-business/hello-faq) بشكل آمن، ما يقلل عدد المرات التي يتعين على المستخدمين المصادقة فيها. ومع ذلك، Windows يسمح فقط ب 10 بطاقات ذكية في كل مرة على جهاز معين. عندما يسجل المستخدم الحادي عشر الدخول للمرة الأولى، سيفقد أحد الحسابات الموجودة بطاقته الذكية. سيتمكنون من تسجيل الدخول، ولكن لن يتم تخزين رقم التعريف الشخصي (PIN) الخاص بهم مؤقتا.

### <a name="universal-print"></a>طباعة عامة

عندما تقوم الطباعة العامة بتثبيت طابعة لمستخدم واحد على جهاز مشترك، تصبح الطابعة متوفرة لجميع مستخدمي هذا الجهاز. لا توجد طريقة لعزل الطابعات بين المستخدمين على الأجهزة المشتركة.

## <a name="limitations-of-shared-device-mode-in-the-public-preview-release"></a>قيود وضع الجهاز المشترك في إصدار المعاينة العامة

### <a name="primary-user"></a>المستخدم الأساسي

يحتوي كل جهاز Microsoft Intune على مستخدم أساسي، والذي يتم تعيينه عند إعداد جهاز بواسطة Autopilot. ولكن عند مشاركة الأجهزة، يتطلب Intune إزالة المستخدم الأساسي.

> [!IMPORTANT]
> أثناء وجود وضع الجهاز المشترك في المعاينة العامة، تأكد من إزالة المستخدم الأساسي باتباع الخطوات التالية: تسجيل الدخول إلى مركز إدارة إدارة نقاط النهاية من Microsoft، وتحديد **أجهزة DevicesAll**>، وتحديد جهاز، ثم تحديد **المستخدم الأساسي PropertiesRemove**>، وحذف المستخدم المدرج هناك.

### <a name="deploying-apps-with-company-portal"></a>نشر التطبيقات باستخدام Company Portal

قد لا تحتاج بعض التطبيقات إلى التواجد على جميع الأجهزة، لذلك قد تفضل أن يقوم المستخدمون بتثبيت هذه التطبيقات فقط عندما يحتاجون إليها من [Company Portal](/mem/intune/user-help/install-apps-cpapp-windows).

يقوم Microsoft Managed Desktop بتعطيل Company Portal بشكل افتراضي للأجهزة في وضع الجهاز المشترك. إذا كنت تريد تمكين Company Portal، يمكنك تقديم [طلب تغيير](../working-with-managed-desktop/admin-support.md). ومع ذلك، يجب أن تكون على دراية ببعض القيود في هذه الميزة في هذه المعاينة العامة:

- لتوفير تطبيق للمستخدمين في Company Portal، [قم بتعيين مجموعة مستخدمين](/mem/intune/apps/apps-deploy) لهذا التطبيق في Intune ثم أضف كل مستخدم إلى مجموعة المستخدمين هذه.
- لا يمكن أن يكون للأجهزة [مستخدم أساسي](#primary-user).
- لإلغاء تثبيت تطبيق قام المستخدم بتثبيته من خلال Company Portal، يجب إلغاء تثبيت التطبيق من جميع المستخدمين على هذا الجهاز.

> [!CAUTION]
> لا يدعم Company Portal التطبيقات المعينة لمجموعات الأجهزة كما هو متوفر.

### <a name="redeployment-of-microsoft-365-apps-for-enterprise"></a>إعادة نشر Microsoft 365 Apps للمؤسسة

أثناء المعاينة العامة، إذا كان يجب إعادة نشر Microsoft 365 Apps، يجب على المستخدمين الاتصال بموظفي الدعم المحليين لطلب رفع مستوى العامل وإعادة تثبيت Microsoft 365 Apps for enterprise على هذا الجهاز.

### <a name="microsoft-teams"></a>Microsoft Teams

عندما يبدأ مستخدم Teams للمرة الأولى، ستتم مطالبته بتحديث التطبيق قبل أن يتمكن من استخدامه. بمجرد السماح بالتحديث، سيحافظ Teams على تحديث نفسه في الخلفية.
