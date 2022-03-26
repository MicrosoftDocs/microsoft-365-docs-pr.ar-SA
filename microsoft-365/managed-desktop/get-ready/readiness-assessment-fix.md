---
title: إصلاح المشاكل التي تم العثور عليها بواسطة أداة تقييم الجهوزية
description: الإجراءات المفصلة التي يجب اتخاذها لكل مشكلة تعثر عليها الأداة
keywords: سطح المكتب المدار من Microsoft، Microsoft 365، الخدمة، الوثائق
ms.service: m365-md
author: tiaraquan
ms.localizationpriority: medium
ms.collection: M365-modern-desktop
ms.author: tiaraquan
manager: dougeby
ms.topic: article
audience: Admin
ms.openlocfilehash: badf2d65f2b29e265a1312cb1d5f4802a44f3cb3
ms.sourcegitcommit: 6e90baef421ae06fd790b0453d3bdbf624b7f9c0
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 02/12/2022
ms.locfileid: "63572964"
---
# <a name="fix-issues-found-by-the-readiness-assessment-tool"></a>إصلاح المشاكل التي تم العثور عليها بواسطة أداة تقييم الجهوزية

لكل عملية تحقق، ستظهر الأداة نتيجة واحدة من أربع نتائج محتملة:

| النتيجة  | المعنى |
| ----- | ----- |
| جاهز | لا يلزم اتخاذ أي إجراء قبل إكمال التسجيل. |
| استشارات | اتبع الخطوات في الأداة أو هذه المقالة للحصول على أفضل تجربة مع التسجيل والمستخدمين. <br><br> يمكنك *إكمال* التسجيل، ولكن يجب إصلاح هذه المشاكل قبل نشر جهازك الأول. |
| غير جاهز | **سيفشل التسجيل إذا لم تصلح هذه المشاكل.** <br><br> اتبع الخطوات في الأداة أو هذه المقالة لحلها. |
| الخطأ | لا يوجد لدى دور Azure Active Directory (AD) الذي تستخدمه الإذن الكافي لتشغيل هذا الاختيار. |

> [!NOTE]
> تعكس النتائج التي تم إعدادها بواسطة هذه الأداة حالة الإعدادات فقط في الوقت الذي قمت فيه بضبطها. إذا قمت بإجراء تغييرات في وقت لاحق على Microsoft Intune أو Azure Active Directory أو Microsoft 365، يمكن أن تصبح العناصر التي كانت "جاهزة" "غير جاهزة". لتجنب المشاكل المتعلقة بعمليات سطح المكتب المدار من Microsoft، تحقق من الإعدادات المحددة الموضحة في هذه المقالة قبل تغيير أي سياسات.

## <a name="microsoft-intune-settings"></a>Microsoft Intune الإعدادات

يمكنك الوصول إلى إعدادات Intune في إدارة نقاط النهاية من Microsoft [الإدارة](https://endpoint.microsoft.com).

### <a name="autopilot-deployment-profile"></a>ملف تعريف نشر Autopilot

يجب ألا يكون لديك أي ملفات تعريف Autopilot موجودة تستهدف المجموعات المعينة أو الديناميكية مع أجهزة سطح المكتب المدارة من Microsoft. يستخدم Microsoft Managed Desktop Autopilot لتكوين أجهزة جديدة. إذا كان لديك ملف تعريف نشر Autopilot موجود، فيجب تعيين الإعداد تحويل كل الأجهزة المستهدفة إلى **Autopilot** إلى **لا** لكي ينجح اختبار الجهوزية Autopilot لسطح المكتب المدار من Microsoft.

| النتيجة  | المعنى |
| ----- | ----- |
| غير جاهز | لديك ملف تعريف Autopilot تم تعيينه إلى جميع الأجهزة. <br><br> لمزيد من المعلومات، [راجع Windows الأجهزة في Intune باستخدام Windows Autopilot](/mem/autopilot/enrollment-autopilot). بعد تسجيل سطح المكتب المدار من Microsoft، قم بتعيين نهج Autopilot لاستبعاد **أجهزة مساحة العمل الحديثة - كل** مجموعة Azure AD.
| استشارات | تأكد من أن ملفات تعريف Autopilot تستهدف مجموعة Azure AD معينة أو ديناميكية لا تتضمن أجهزة سطح المكتب المدارة من Microsoft. <br><br> لمزيد من المعلومات، [راجع Windows الأجهزة في Intune باستخدام Windows Autopilot](/mem/autopilot/enrollment-autopilot). بعد تسجيل سطح المكتب المدار من Microsoft، قم بتعيين ملفات تعريف Autopilot لاستبعاد **أجهزة مساحة العمل الحديثة - كل** مجموعة Azure AD. |

### <a name="certificate-connectors"></a>موصلات الشهادة

إذا كان لديك أي موصلات شهادات سيتم استخدامها من قبل الأجهزة التي تريد تسجيلها في Microsoft Managed Desktop، فلا يجب أن تحدث أي أخطاء في الموصلات. سيتم تطبيق واحد فقط من الإستشارات التالية على وضعك، لذا تحقق منها بعناية.

| النتيجة  | المعنى |
| ----- | ----- |
| استشارات | لا توجد موصلات شهادات. من المحتمل أنك لا تحتاج إلى أي موصلات، ولكن يجب تقييم ما إذا كنت قد تحتاج إلى بعض الاتصال بالشبكة على أجهزة سطح المكتب المدارة من Microsoft. <br><br> لمزيد من المعلومات، راجع [إعداد الشهادات وملفات تعريف الشبكة لسطح المكتب المدار من Microsoft](certs-wifi-lan.md). |
| استشارات | هناك خطأ في موصل شهادة واحد على الأقل. إذا كنت بحاجة إلى هذا الموصل لتوفير الشهادات لأجهزة سطح المكتب المدارة من Microsoft، فيجب حل الخطأ. <br><br> لمزيد من المعلومات، راجع [إعداد الشهادات وملفات تعريف الشبكة لسطح المكتب المدار من Microsoft](certs-wifi-lan.md). |
| استشارات | لديك موصل شهادة واحد على الأقل، ولا يتم إعلامك عن أي أخطاء. ومع ذلك، في إطار التحضير للنشر، قد تحتاج إلى إنشاء ملف تعريف لإعادة استخدام الموصل لأجهزة سطح المكتب المدارة من Microsoft. <br><br> لمزيد من المعلومات، راجع [إعداد الشهادات وملفات تعريف الشبكة لسطح المكتب المدار من Microsoft](certs-wifi-lan.md). |

### <a name="company-portal"></a>Company Portal

يتطلب سطح المكتب المدار من Microsoft أن يقوم مسؤولي تكنولوجيا Intune Company Portal بتثبيت أجهزة سطح المكتب المدارة من Microsoft للمستخدمين.

| النتيجة  | المعنى |
| ----- | ----- |
| غير جاهز | لم يتم تثبيت Company Portal للمستخدمين. قم Company Portal فرض المزامنة بين Intune Microsoft Store للأعمال. <br><br> لمزيد من المعلومات، [راجع تثبيت Intune Company Portal على الأجهزة](../get-started/company-portal.md).

### <a name="conditional-access-policies"></a>سياسات الوصول الشرطي

لا يمكن لنهج الوصول الشرطي منع Microsoft Managed Desktop من إدارة مؤسسة Azure AD (المستأجر) في Intune و Azure AD.

| النتيجة  | المعنى |
| ----- | ----- |
| غير جاهز | لديك نهج وصول شرطي واحد على الأقل يستهدف جميع المستخدمين. <br><br> أثناء التسجيل، سنستبعد حسابات خدمات سطح المكتب المدار من Microsoft من سياسات الوصول الشرطي ذات الصلة وسنطبق سياسات وصول شرطي جديدة لتقييد الوصول إلى هذه الحسابات. <br><br> بعد التسجيل، يمكنك مراجعة نهج الوصول الشرطي لسطح المكتب المدار من Microsoft في إدارة نقاط النهاية من Microsoft. لمزيد من المعلومات حول حسابات الخدمات هذه، راجع [إجراءات التشغيل القياسية](../service-description/operations-and-monitoring.md#standard-operating-procedures). |
| استشارات | لديك سياسات وصول شرطي قد تمنع Microsoft Managed Desktop من إدارة خدمة Microsoft Managed Desktop. <br><br> أثناء التسجيل، سنستبعد حسابات خدمات سطح المكتب المدار من Microsoft من سياسات الوصول الشرطي ذات الصلة وسنطبق سياسات وصول شرطي جديدة لتقييد الوصول إلى هذه الحسابات. <br><br> لمزيد من المعلومات حول حسابات الخدمات هذه، راجع [إجراءات التشغيل القياسية](../service-description/operations-and-monitoring.md#standard-operating-procedures). |
| الخطأ | لا يوجد في دور مسؤول Intune أذونات كافية لهذا الاختيار. ستحتاج أيضا إلى تعيين أدوار Azure AD هذه لتشغيل هذا الاختيار: <ul><li>قارئ الأمان</li><li>مسؤول الأمان</li><li>مسؤول الوصول الشرطي</li><li>القارئ العام</li><li>مسؤول الأجهزة</li></ul>
### <a name="device-compliance-policies"></a>سياسات توافق الأجهزة

قد تؤثر سياسات توافق أجهزة Intune في مؤسسة Azure AD على أجهزة سطح المكتب المدارة من Microsoft.

| النتيجة  | المعنى |
| ----- | ----- |
| استشارات | لديك نهج توافق واحد على الأقل ينطبق على جميع المستخدمين. يتضمن Microsoft Managed Desktop أيضا سياسات التوافق التي سيتم تطبيقها على أجهزة سطح المكتب المدارة من Microsoft. راجع كل سياسات التوافق التي أنشأتها مؤسستك التي تنطبق على أجهزة سطح المكتب المدارة من Microsoft للتأكد من عدم وجود تعارضات. <br><br> لمزيد من المعلومات، راجع [إنشاء نهج توافق في Microsoft Intune](/mem/intune/protect/create-compliance-policy). |

### <a name="device-configuration-profiles"></a>ملفات تعريف تكوين الجهاز

لا يمكن لملفات تعريف تكوين جهاز Intune في مؤسسة Azure AD استهداف أي أجهزة Microsoft Manage Desktop أو المستخدمين.

| النتيجة  | المعنى |
| ----- | ----- |
| غير جاهز | لديك ملف تعريف تكوين واحد على الأقل ينطبق على جميع المستخدمين أو كل الأجهزة أو كليهما. أعد تعيين ملف التعريف لتطبيقه على مجموعة Azure AD معينة لا تتضمن أي أجهزة Microsoft Managed Desktop. <br><br> لمزيد من المعلومات، راجع [إنشاء ملف تعريف بإعدادات مخصصة في Microsoft Intune](/mem/intune/configuration/custom-settings-configure). |
| استشارات | تأكد من أن أي سياسات تكوين لديك لا تتضمن أي أجهزة أو مستخدمين لسطح المكتب المدار من Microsoft. <br><br> لمزيد من المعلومات، راجع [إنشاء ملف تعريف بإعدادات مخصصة في Microsoft Intune](/mem/intune/configuration/custom-settings-configure). |

### <a name="device-type-restrictions"></a>قيود نوع الجهاز

يجب السماح لأجهزة سطح المكتب المدارة من Microsoft بالتسجيل في Intune.

| النتيجة  | المعنى |
| ----- | ----- |
| غير جاهز | لديك حاليا نهج تقييد تسجيل واحد على الأقل تم تكوينه لمنع Windows الأجهزة من التسجيل في Intune. <br><br> اتبع الخطوات في تعيين [](/mem/intune/enrollment/enrollment-restrictions-set) قيود التسجيل لكل نهج تقييد تسجيل يستهدف مستخدمي Microsoft Managed Desktop وتغيير Windows **(MDM)** إلى **السماح**. ومع ذلك، يمكنك تعيين أي أجهزة  مملوكة Windows **(MDM)** إلى **حظر**. |

### <a name="enrollment-status-page"></a>صفحة حالة التسجيل

لديك حاليا صفحة حالة التسجيل (ESP) تم تمكينها. إذا كنت تنوي المشاركة في المعاينة العامة لسطح المكتب المدار من Microsoft لهذه الميزة، يمكنك تجاهل هذا العنصر. لمزيد من المعلومات، راجع [تجربة التشغيل الأولي باستخدام Autopilot وصفحة حالة التسجيل](../get-started/esp-first-run.md).

| النتيجة  | المعنى |
| ----- | ----- |
| غير جاهز | لديك ملف تعريف ESP الافتراضي معين إلى **إظهار تقدم تكوين ملف التعريف والتطبيق**. <br><br> قم بتعطيل هذا الإعداد أو تأكد من أن الواجبات لأي مجموعة Azure AD لا تتضمن أجهزة سطح المكتب المدارة من Microsoft باتباع الخطوات في [إعداد صفحة حالة التسجيل](/mem/intune/enrollment/windows-enrollment-status). |
| استشارات | تأكد من عدم تعيين أي ملفات تعريف تتضمن إعداد  تقدم تكوين تكوين ملف التعريف والتطبيق إلى أي مجموعة Azure AD تتضمن أجهزة سطح المكتب المدارة من Microsoft. <br><br> لمزيد من المعلومات، راجع [إعداد صفحة حالة التسجيل](/mem/intune/enrollment/windows-enrollment-status). |

### <a name="microsoft-store-for-business"></a>Microsoft Store للأعمال

نحن نستخدم Microsoft Store للأعمال ونشر تطبيق Company Portal على Microsoft Managed Desktop. تسمح هذه الطريقة للمستخدمين بتثبيت بعض التطبيقات بشكل اختياري، مثل Microsoft Project و Microsoft Visio (إذا كان ذلك مسموحا به).

| النتيجة  | المعنى |
| ----- | ----- |
| غير جاهز | Microsoft Store للأعمال تكون إما غير تمكينية أو غير متزامنة مع Intune. <br><br> لمزيد من المعلومات، راجع كيفية إدارة التطبيقات التي تم شراؤها من Microsoft Store للأعمال [باستخدام](/mem/intune/apps/windows-store-for-business) Microsoft Intune [وتثبيت Intune Company Portal على الأجهزة](../get-started/company-portal.md). |

### <a name="multi-factor-authentication"></a>المصادقة متعددة العوامل

لا يمكن للمصادقة متعددة العوامل منع Microsoft Managed Desktop من إدارة مؤسسة Azure AD (المستأجر) في Intune و Azure AD.

| النتيجة  | المعنى |
| ----- | ----- |
| غير جاهز | لديك بعض نهج المصادقة متعددة العوامل المعينة كما **هو مطلوب** لنهج الوصول الشرطي التي تم تعيينها لجميع المستخدمين. <br><br> أثناء التسجيل، سنستبعد حسابات خدمات سطح المكتب المدار من Microsoft من سياسات الوصول الشرطي ذات الصلة وسنطبق سياسات وصول شرطي جديدة لتقييد الوصول إلى هذه الحسابات. <br><br> لمزيد من المعلومات حول حسابات الخدمات هذه، راجع [إجراءات التشغيل القياسية](../service-description/operations-and-monitoring.md#standard-operating-procedures). |
| استشارات | لديك مصادقة متعددة العوامل مطلوبة على نهج الوصول الشرطي التي قد تمنع Microsoft Managed Desktop من إدارة خدمة Microsoft Managed Desktop. <br><br> أثناء التسجيل، قم باستبعاد حسابات خدمات سطح المكتب المدارة من Microsoft من سياسات الوصول الشرطي ذات الصلة وتطبيق سياسات وصول شرطي جديدة لتقييد الوصول إلى هذه الحسابات. لمزيد من المعلومات حول حسابات الخدمات هذه، راجع [إجراءات التشغيل القياسية](../service-description/operations-and-monitoring.md#standard-operating-procedures). |
| الخطأ | لا يوجد في دور مسؤول Intune أذونات كافية لهذا الاختيار. ستحتاج أيضا إلى تعيين أدوار Azure AD هذه لتشغيل هذا الاختيار: <ul><li>قارئ الأمان</li><li>مسؤول الأمان</li><li>مسؤول الوصول الشرطي</li><li>القارئ العام</li><li>مسؤول الأجهزة</li></ul>

### <a name="powershell-scripts"></a>برامج PowerShell النصية

Windows PowerShell تعيين البرامج النصية بطريقة تستهدف أجهزة سطح المكتب المدارة من Microsoft.

| النتيجة  | المعنى |
| ----- | ----- |
| استشارات | تأكد من أن Windows PowerShell البرامج النصية في مؤسسة Azure AD لا تستهدف أي أجهزة Microsoft Manage Desktop أو المستخدمين. لا يعين برنامج PowerShell النصي لاستهداف جميع المستخدمين أو كل الأجهزة أو كليهما. قم بتغيير النهج لاستخدام واجب يستهدف مجموعة Azure AD معينة لا تتضمن أي أجهزة سطح مكتب مدارة من Microsoft أو مستخدمين. <br><br> لمزيد من المعلومات، راجع [استخدام برامج PowerShell النصية Windows 10 في Intune](/mem/intune/apps/intune-management-extension). |

### <a name="region"></a>المنطقة

يجب أن تكون المنطقة مدعومة من قبل Microsoft Managed Desktop.

| النتيجة  | المعنى |
| ----- | ----- |
| غير جاهز | منطقة مؤسسة Azure AD غير معتمدة حاليا من قبل Microsoft Managed Desktop. <br><br> لمزيد من المعلومات، راجع [المناطق واللغات المعتمدة لسطح](../service-description/regions-languages.md) المكتب المدار من Microsoft. |
| استشارات | لا يدعم Microsoft Managed Desktop بلد واحد أو أكثر من البلدان التي تقع فيها مؤسسة Azure AD. <br><br> لمزيد من المعلومات، راجع [المناطق واللغات المعتمدة لسطح](../service-description/regions-languages.md) المكتب المدار من Microsoft. |

### <a name="security-baselines"></a>خطوط الأمان الأساسية

يجب ألا تستهدف سياسات الأمان الأساسية أي أجهزة سطح مكتب مدارة من Microsoft.

| النتيجة  | المعنى |
| ----- | ----- |
| غير جاهز | لديك ملف تعريف أساسي أمان يستهدف جميع المستخدمين أو كل الأجهزة أو كليهما. غير النهج لاستخدام واجب يستهدف مجموعة Azure AD معينة لا تتضمن أي أجهزة سطح مكتب مدارة من Microsoft. <br><br> لمزيد من المعلومات، راجع [استخدام خطوط الأمان الأساسية لتكوين Windows 10 في Intune](/mem/intune/protect/security-baselines). أثناء التسجيل، نقوم بتطبيق أساس أمان جديد على جميع أجهزة سطح المكتب المدارة من Microsoft. بعد التسجيل، يمكنك مراجعة نهج أساسي أمان سطح المكتب المدار من Microsoft في منطقة  نهج التكوين في إدارة نقاط النهاية من Microsoft. |
| استشارات | تأكد من أن أي سياسات أساسية أمان قمت باستبعاد أجهزة سطح المكتب المدارة من Microsoft. لمزيد من المعلومات، راجع [استخدام خطوط الأمان الأساسية لتكوين Windows 10 في Intune](/mem/intune/protect/security-baselines). <br><br> أثناء التسجيل، نقوم بتطبيق أساس أمان جديد على جميع أجهزة سطح المكتب المدارة من Microsoft. أجهزة **مكان العمل الحديثة - إن** كل مجموعة Azure AD هي مجموعة ديناميكية ننشئها عند التسجيل في Microsoft Managed Desktop. يجب عليك العودة لاستبعاد هذه المجموعة بعد التسجيل. |

### <a name="unlicensed-admins"></a>المسؤولون غير مرخصين

يجب تمكين هذا الإعداد لتجنب حدوث خطأ "عدم وجود أذونات" عند التفاعل مع مؤسسة Azure AD.

| النتيجة  | المعنى |
| ----- | ----- |
| غير جاهز | **يجب تمكين** السماح بالوصول إلى المسؤولين غير مرخصين. لمزيد من المعلومات، راجع [المتطلبات الأساسية الخاصة وحسابات الضيوف](/microsoft-365/managed-desktop/get-ready/guest-accounts). |

### <a name="windows-apps"></a>Windows التطبيقات

راجع التطبيقات التي تريد أن يكون لدى مستخدمي Microsoft Managed Desktop.

| النتيجة  | المعنى |
| ----- | ----- |
| استشارات | يجب أن تقوم بإعداد مخزون للتطبيقات التي تريد أن يكون لدى مستخدمي Microsoft Managed Desktop. نظرا لأنه يجب نشر هذه التطبيقات بواسطة Intune، قم بتقييم إعادة استخدام تطبيقات Intune الموجودة. يمكنك استخدام Company Portal (راجع تثبيت Intune Company Portal على [الأجهزة](../get-started/company-portal.md) وصفحة حالة التسجيل (ESP) لتوزيع التطبيقات على المستخدمين. <br><br> لمزيد من المعلومات، راجع [التطبيقات في Microsoft Managed Desktop](apps.md) وتجربة التشغيل الأول [مع Autopilot وصفحة حالة التسجيل](../get-started/esp-first-run.md). <br><br> يمكنك أن تطلب من ممثل حساب Microsoft استعلاما في Microsoft Endpoint Configuration Manager لتعريف التطبيقات الجاهزة للترحيل إلى Intune أو التي تحتاج إلى ضبط. |

### <a name="windows-hello-for-business"></a>Windows Hello for Business

يتطلب Microsoft Managed Desktop Windows Hello For Business لتمكينه.

| النتيجة  | المعنى |
| ----- | ----- |
| استشارات | Windows Hello يتم تعطيل for Business أو عدم إعداده. قم بتمكينه باتباع الخطوات في [إنشاء نهج Windows Hello للأعمال](/mem/intune/protect/windows-hello#create-a-windows-hello-for-business-policy). |

### <a name="windows-10-update-rings"></a>Windows 10 حلقات التحديث

يجب ألا يستهدف Windows 10 "حلقة التحديث" في Intune أي أجهزة سطح مكتب مدارة من Microsoft.

| النتيجة  | المعنى |
| ----- | ----- |
| غير جاهز | لديك نهج "حلقة التحديث" الذي يستهدف جميع الأجهزة أو جميع المستخدمين أو كليهما. غير النهج لاستخدام واجب يستهدف مجموعة Azure AD معينة لا تتضمن أي أجهزة سطح مكتب مدارة من Microsoft. <br><br> لمزيد من المعلومات، [راجع إدارة Windows 10 البرامج في Intune](/mem/intune/protect/windows-update-for-business-configure). |
| استشارات | تأكد من أن أي من سياسات حلقة التحديث التي قمت باستبعادها هي **أجهزة مساحة العمل الحديثة - كل** مجموعة Azure AD. إذا قمت بتعيين مجموعات مستخدمي Azure AD إلى هذه النهج، فتأكد من أن أي سياسات حلقة تحديث قمت باستبعادها أيضا "مساحة العمل الحديثة **" -** كل مجموعة Azure AD التي تضيف مستخدمي Microsoft Managed Desktop إلى (أو مجموعة مماثلة). <br><br> لمزيد من المعلومات، [راجع إدارة Windows 10 البرامج في Intune](/mem/intune/protect/windows-update-for-business-configure). إن كل من **أجهزة مساحة العمل الحديثة -** كل من مكان العمل الحديث و **مكان العمل الحديث -** كل مجموعات Azure AD هي مجموعات ننشئها عند التسجيل في Microsoft Managed Desktop. يجب عليك العودة لاستبعاد هذه المجموعة بعد التسجيل. |

## <a name="azure-active-directory-settings"></a>إعدادات Azure Active Directory

يمكنك الوصول إلى إعدادات Azure Active Directory في مدخل [Azure](https://portal.azure.com).

### <a name="intune-enrollment"></a>تسجيل Intune

Windows 10 الأجهزة في مؤسسة Azure AD التسجيل تلقائيا في Intune.

| النتيجة  | المعنى |
| ----- | ----- |
| استشارات | تأكد من تعيين **نطاق مستخدم MDM** إلى **"بعض** " أو **"الكل**"، وليس إلى **"بلا**". <br><br> إذا اخترت **بعض**، فرجع بعد التسجيل وحدد مساحة العمل الحديثة **-** كل مجموعة Azure AD **للمجموعات** أو مجموعة مكافئة تستهدف جميع مستخدمي Microsoft Managed Desktop. <br><br> لمزيد من المعلومات، راجع إعداد التسجيل [للأجهزة Windows باستخدام Microsoft Intune](/mem/intune/enrollment/windows-enroll#enable-windows-10-automatic-enrollment). |

### <a name="ad-hoc-subscriptions"></a>الاشتراكات المخصصة

تنصح بكيفية التحقق من إعداد، إذا تم تعيينه إلى "خطأ"، فقد يمنع تجوال حالة المؤسسة من العمل بشكل صحيح.

| النتيجة  | المعنى |
| ----- | ----- |
| استشارات | تأكد من **تعيين AllowAdHocSubscriptions** إلى **True**. وإلا، فقد لا يعمل التجوال في حالة المؤسسة. <br><br> لمزيد من المعلومات، راجع [Set-MsolCompanySettings](/powershell/module/msonline/set-msolcompanysettings). |

### <a name="enterprise-state-roaming"></a>تجوال حالة المؤسسة

يجب تمكين تجوال حالة المؤسسة.

| النتيجة  | المعنى |
| ----- | ----- |
| استشارات | تأكد من تمكين "تجوال حالة المؤسسة" **لل الكل** أو **للمجموعات** المحددة. <br><br> لمزيد من المعلومات، راجع [تمكين تجوال حالة المؤسسة في Azure Active Directory](/azure/active-directory/devices/enterprise-state-roaming-enable). |

### <a name="guest-invitation-settings"></a>إعدادات دعوة الضيف

يوصي Microsoft Managed Desktop بضبط إعدادات دعوة الضيف، نظرا لأن الإعداد الافتراضي يسمح لجميع المستخدمين والضيوف في الدليل بدعوة الضيوف.

| النتيجة  | المعنى |
| ----- | ----- |
| استشارات | **يمكن للمستخدمين الأعضاء والمستخدمين المعينين لأدوار** إدارة معينة دعوة الضيف بما في ذلك الضيوف الذين لديهم أذونات الأعضاء يجب تمكينهم. <br><br> لمزيد من المعلومات، راجع [المتطلبات الأساسية الخاصة وحسابات الضيوف](/microsoft-365/managed-desktop/get-ready/guest-accounts). |

### <a name="guest-user-access"></a>وصول المستخدم الضيف

يوصي Microsoft Managed Desktop بضبط وصول الضيف، نظرا لأن الإعداد الافتراضي يسمح لجميع الضيوف في الدليل بالوصول نفسه للأعضاء.

| النتيجة  | المعنى |
| ----- | ----- |
| استشارات | **يجب تمكين وصول المستخدمين الضيوف بشكل** محدود إلى خصائص كائنات الدليل وعضوياتها. <br><br> لمزيد من المعلومات، راجع [المتطلبات الأساسية الخاصة وحسابات الضيوف](/microsoft-365/managed-desktop/get-ready/guest-accounts). |

### <a name="licenses"></a>التراخيص

يلزم توفر العديد من التراخيص لاستخدام Microsoft Managed Desktop.

| النتيجة  | المعنى |
| ----- | ----- |
| غير جاهز | ليس لديك كل التراخيص التي تحتاج إليها لاستخدام Microsoft Managed Desktop. <br><br> لمزيد من المعلومات، راجع [تقنيات سطح المكتب المدار من Microsoft](../intro/technologies.md) [والمزيد حول التراخيص](prerequisites.md#more-about-licenses). |

### <a name="microsoft-managed-desktop-service-accounts"></a>حسابات خدمات سطح المكتب المدارة من Microsoft

قد تتضارب بعض أسماء الحسابات مع أسماء الحسابات التي أنشأها Microsoft Managed Desktop لإدارة خدمة Microsoft Managed Desktop.

| النتيجة  | المعنى |
| ----- | ----- |
| غير جاهز | لديك اسم حساب واحد على الأقل سيتضارب مع أسماء الحسابات التي تم إنشاؤها بواسطة Microsoft Managed Desktop. العمل مع ممثل حساب Microsoft لاستبعاد أسماء الحسابات هذه. لا نقوم سرد أسماء الحسابات بشكل عام لتقليل مخاطر الأمان.

### <a name="security-administrator-roles"></a>أدوار مسؤولي الأمان

يجب تعيين هذه الأدوار للمستخدمين الذين لديهم أدوار أمان معينة في Microsoft Defender لنقطة النهاية.

| النتيجة  | المعنى |
| ----- | ----- |
| استشارات | إذا تم تعيين مستخدمين إلى أي من هذه الأدوار في مؤسسة Azure AD، فتأكد من تعيين هذه الأدوار أيضا في Microsoft Defender لنقطة النهاية. وإلا، فلن يتمكن المسؤولون الذين لهم هذه الأدوار من الوصول إلى مدخل المسؤول. <ul><li>عامل تشغيل الأمان</li><li>القارئ العام</li></ul> <br> لمزيد من المعلومات، راجع [إنشاء أدوار](/windows/security/threat-protection/microsoft-defender-atp/user-roles) للتحكم بالوصول المستند إلى الدور وإدارتها.

### <a name="security-default"></a>الأمان الافتراضي

ستمنع إعدادات الأمان الافتراضية في Azure Active Directory Microsoft Managed Desktop من إدارة أجهزتك.

| النتيجة  | المعنى |
| ----- | ----- |
| غير جاهز | لديك إعدادات أمان افتراضية تم تشغيلها. قم إيقاف تشغيل إعدادات الأمان الافتراضية، ثم قم بإعداد سياسات الوصول الشرطي. <br><br> لمزيد من المعلومات، راجع [سياسات الوصول الشرطي الشائعة](/azure/active-directory/conditional-access/concept-conditional-access-policy-common). |

### <a name="self-service-password-reset"></a>إعادة تعيين كلمة المرور للخدمة الذاتية

يمكن تمكين إعادة تعيين كلمة المرور للخدمة الذاتية (SSPR) لجميع مستخدمي سطح المكتب المدار من Microsoft باستثناء حسابات خدمة سطح المكتب المدار من Microsoft. <br><br> لمزيد من المعلومات، راجع البرنامج التعليمي: تمكين المستخدمين من إلغاء تأمين حسابهم أو إعادة تعيين كلمات المرور باستخدام إعادة تعيين كلمة مرور الخدمة الذاتية ل [Azure Active Directory](/azure/active-directory/authentication/tutorial-enable-sspr).

| النتيجة  | المعنى |
| ----- | ----- |
| استشارات | تأكد من أن إعداد SSPR **المحدد** يتضمن مستخدمي Microsoft Managed Desktop، ولكنه يستثني حسابات خدمة سطح المكتب المدار من Microsoft. لا يمكن أن تعمل حسابات خدمات Microsoft Managed Desktop كما هو متوقع عند تمكين SSPR. |

### <a name="standard-user-role"></a>دور المستخدم القياسي

وب غير المستخدمين الذين تم تعيين أدوارهم إلى مسؤول عام ومسؤول الجهاز Azure Active Directory، سيكون مستخدمو Microsoft Managed Desktop مستخدمين قياسيين بدون امتيازات المسؤول المحلي. سيتم تعيين دور مستخدم قياسي لجميع المستخدمين الآخرين عند بدء تشغيل جهاز سطح المكتب المدار من Microsoft.

| النتيجة  | المعنى |
| ----- | ----- |
| استشارات | لن يكون لدى مستخدمي Microsoft Managed Desktop امتيازات المسؤول المحلي على أجهزة سطح المكتب المدارة من Microsoft بعد التسجيل. |

## <a name="microsoft-365-apps-for-enterprise"></a>Microsoft 365 Apps for enterprise

### <a name="onedrive"></a>OneDrive

**سيتضارب الإعداد السماح بالمزامنة فقط على أجهزة الكمبيوتر الشخصية** التي تم ضمها إلى مجالات معينة مع Microsoft Managed Desktop. يمكنك الوصول OneDrive الإعدادات في OneDrive [الإدارة](https://admin.onedrive.com).

| النتيجة  | المعنى |
| ----- | ----- |
| استشارات | أنت تستخدم الإعداد **السماح بالمزامنة فقط على أجهزة الكمبيوتر الشخصية التي تم ضمها إلى مجالات** محددة. لن يعمل هذا الإعداد مع Microsoft Managed Desktop. تعطيل هذا الإعداد. بدلا من ذلك، OneDrive استخدام نهج وصول شرطي. <br><br> لمزيد من المعلومات، راجع [تخطيط نشر الوصول الشرطي](/azure/active-directory/conditional-access/plan-conditional-access) للحصول على المساعدة. |
