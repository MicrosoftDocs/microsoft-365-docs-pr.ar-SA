---
title: نظرة عامة حول استخدام أساسيات Microsoft 365 Lighthouse لنشر تكوينات المستأجر القياسية
f1.keywords: CSH
ms.author: sharik
author: SKjerland
manager: scotv
ms-reviewer: shcallaw, kywirpel
audience: Admin
ms.topic: article
ms.prod: microsoft-365-lighthouse
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
ms.custom:
- AdminSurgePortfolio
- M365-Lighthouse
search.appverid: MET150
description: بالنسبة لموفري الخدمات المدارة (MSPs) الذين يستخدمون Microsoft 365 Lighthouse، تعرف على كيفية استخدام الخطوط الأساسية لنشر تكوينات المستأجر القياسية.
ms.openlocfilehash: 9261be531db428c3d081e87c6717dfc8710a5026
ms.sourcegitcommit: 23a53b5c5e372a2a7ad5e175850224d3d464f6dd
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/28/2022
ms.locfileid: "67056625"
---
# <a name="overview-of-using-microsoft-365-lighthouse-baselines-to-deploy-standard-tenant-configurations"></a>نظرة عامة حول استخدام أساسيات Microsoft 365 Lighthouse لنشر تكوينات المستأجر القياسية 

توفر أساسيات Microsoft 365 Lighthouse طريقة قابلة للتكرار وقابلة للتطوير لإدارة إعدادات أمان Microsoft 365 عبر العديد من مستأجري العملاء. توفر الخطوط الأساسية تكوينات المستأجر القياسية التي تنشر نهج الأمان الأساسية ومعايير التوافق التي تحافظ على أمان مستخدمي المستأجرين والأجهزة والبيانات.

يمكنك عرض الأساس الافتراضي وخطوات النشر الخاصة به من داخل Lighthouse. لتطبيق أساس على مستأجر، حدد **المستأجرين** في جزء التنقل الأيمن، ثم حدد مستأجرا. بعد ذلك، انتقل إلى علامة التبويب **"خطة النشر** " لبدء النشر.

## <a name="lighthouse-baseline"></a>أساس Lighthouse

تم تصميم تكوينات أساس Lighthouse للتأكد من أن جميع المستأجرين المدارين آمنون ومتوافقون. حدد **الخطوط الأساسية** في جزء التنقل الأيمن لعرض الأساس الافتراضي الذي ينطبق على كافة المستأجرين. لعرض خطوات النشر المضمنة في الأساس الافتراضي، حدد **"عرض الأساس** " لفتح صفحة **الأساس الافتراضي** . حدد أيا من خطوات النشر لعرض تفاصيل النشر وتأثير المستخدم.

:::image type="content" source="../media/m365-lighthouse-deploy-baselines/default-baseline-page.png" alt-text="لقطة شاشة لصفحة الأساس الافتراضي.":::

### <a name="default-lighthouse-configurations"></a>تكوينات Lighthouse الافتراضية

| تكوين الأساس | الوصف |
|--|--|
| طلب المصادقة متعددة العوامل للمسؤولين | نهج الوصول المشروط الذي يتطلب مصادقة متعددة العوامل لجميع المسؤولين. وهي مطلوبة لجميع تطبيقات السحابة. لمزيد من المعلومات حول هذا الأساس، راجع [الوصول المشروط: طلب المصادقة متعددة العوامل لجميع المسؤولين](/azure/active-directory/conditional-access/howto-conditional-access-policy-admin-mfa).|
| طلب المصادقة متعددة العوامل للمستخدمين النهائيين | نهج الوصول المشروط الذي يتطلب مصادقة متعددة العوامل لجميع المستخدمين.  وهي مطلوبة لجميع تطبيقات السحابة. لمزيد من المعلومات حول هذا الأساس، راجع [الوصول المشروط: طلب المصادقة متعددة العوامل لجميع المستخدمين](/azure/active-directory/conditional-access/howto-conditional-access-policy-all-users-mfa). |
| حظر المصادقة القديمة | نهج الوصول المشروط لحظر مصادقة العميل القديمة. لمزيد من المعلومات حول هذا الأساس، راجع [مصادقة الحظر القديمة Azure AD باستخدام الوصول المشروط](/azure/active-directory/conditional-access/block-legacy-authentication).|
| إعداد تسجيل الجهاز | تسجيل الجهاز للسماح لأجهزة المستأجر بالتسجيل في Microsoft Endpoint Manager. يتم ذلك عن طريق إعداد التسجيل التلقائي بين Azure Active Directory وMicrosoft Endpoint Manager. لمزيد من المعلومات حول هذا الأساس، راجع [إعداد التسجيل لأجهزة Windows](/mem/intune/enrollment/windows-enroll). |
| إعداد Microsoft Defender for Business | توفير المستأجر Microsoft Defender for Business وإلحاق الأجهزة المسجلة بالفعل في Microsoft Endpoint Manager إلى Microsoft Defender for Business. لمزيد من المعلومات، راجع [ما هو Microsoft Defender for Business؟](../security/defender-business/mdb-overview.md) |
| إعداد Exchange Online Protection و Pertahanan Microsoft untuk Office 365 | نهج لتطبيق نهج موصى به لمكافحة البريد العشوائي ومكافحة البرامج الضارة ومكافحة التصيد الاحتيالي والارتباطات الآمنة ونهج المرفقات الآمنة للمستأجرين Exchange Online علب البريد. |
| تكوين برنامج الحماية من الفيروسات من Microsoft Defender Windows 10 والإصدارات الأحدث | ملف تعريف تكوين الجهاز لأجهزة Windows مع إعدادات الحماية من الفيروسات ل Microsoft Defender المكونة مسبقا. لمزيد من المعلومات حول هذا الأساس، راجع [تكوين Pertahanan Microsoft untuk Titik Akhir في Intune](/mem/intune/protect/advanced-threat-protection-configure).|
| تكوين جدار الحماية من Microsoft Defender Windows 10 والإصدارات الأحدث | نهج جدار الحماية للمساعدة في تأمين الأجهزة عن طريق منع نسبة استخدام الشبكة غير المرغوب فيها وغير المصرح بها. لمزيد من المعلومات حول هذا الأساس، راجع [أفضل الممارسات لتكوين جدار حماية Windows Defender](/windows/security/threat-protection/windows-firewall/best-practices-configuring).  |
| تكوين نهج توافق الجهاز Windows 10 والإصدارات الأحدث | نهج جهاز Windows مع إعدادات تم تكوينها مسبقا لتلبية متطلبات التوافق الأساسية. لمزيد من المعلومات حول هذا الأساس، راجع [الوصول المشروط: يتطلب جهازا متوافقا أو مختلطا Azure AD الانضمام](/azure/active-directory/conditional-access/howto-conditional-access-policy-compliant-device). |

## <a name="deployment-plans"></a>خطط النشر

يحتوي كل مستأجر نشط على خطة نشر تتضمن خطوات النشر من أساس Microsoft 365 Lighthouse. للوصول إلى خطة نشر المستأجر، حدد مستأجرا نشطا من القائمة على صفحة **المستأجرين** ، ثم حدد علامة التبويب **"خطة النشر** ".

:::image type="content" source="../media/m365-lighthouse-deploy-baselines/deployment-plan-tab.png" alt-text="لقطة شاشة لعلامة التبويب «Deployment Plan».":::

تتضمن علامة التبويب "خطة النشر" المعلومات التالية:


|العمود  |الوصف  |
|---------|---------|
|خطوة النشر     |  وصف خطوة النشر.       |
|حاله     |حالة خطوة النشر.         |
|الاساس     |الأساس الذي يتم اشتقاق خطوة النشر منه.         |
|الفئة     | ما إذا كانت خطوة النشر مقترنة بإدارة الأجهزة أو الهوية أو البيانات.        |
|تاريخ التحديث الأخير    | التاريخ الذي تم فيه آخر تحديث لخطوة النشر.        |


تتضمن علامة التبويب "خطة النشر" أيضا الخيارات التالية:

- **تصدير:** حدد لتصدير بيانات خطوة النشر إلى ملف قيم مفصولة بفواصل Excel (.csv).
- **تحديث:** حدد لاسترداد أحدث بيانات خطوة النشر.
- **البحث:** أدخل الكلمات الأساسية لتحديد موقع خطوة نشر معينة بسرعة في القائمة.

## <a name="deployment-steps-and-processes"></a>خطوات التوزيع وعملياته

تتضمن خطة نشر كل مستأجر خطوات النشر من أساس Microsoft 365 Lighthouse. تتضمن كل خطوة نشر عملية واحدة أو أكثر تحتاج إلى إكمال. عندما يصبح المستأجر الجديد نشطا، يجب إكمال أنشطة النشر المقترنة بخطوات التوزيع وعملياته.

لكل خطوة نشر، يمكنك اتخاذ الإجراءات التالية:

|العمل  |الوصف  |
|---------|---------|
| المشاركة    |  تمكين مشاركة محتويات خطوة النشر من خلال ارتباط أو عبر البريد الإلكتروني.    |
| المراجعة والنشر    |  تمكين المستخدم من: <ul><li>عند الدعم، قارن إعدادات التكوين في خطوة النشر بالإعدادات في أي نهج موجودة دون نشر الإعدادات إلى المستأجر.<br>تدعم خطوات النشر التالية المقارنة:</br><ul><li>تكوين نهج توافق الجهاز Windows 10 والإصدارات الأحدث</li><li>طلب المصادقة متعددة العوامل للمستخدمين النهائيين</li><li>طلب المصادقة متعددة العوامل للمسؤولين</li><li>حظر المصادقة القديمة</li></ul></li> <li>نشر إعدادات التكوين إلى المستأجر.</li></ul>**ملاحظه:** الخطوات التي لا تدعم القدرة على المقارنة دون نشر الإعدادات إلى المستأجر ستمكنك من مراجعة إعدادات التكوين ونشرها.|
| تحديث حالة خطة العمل    |  تمكين المستخدم من الإبلاغ عن حالة خطة العمل الخاصة به لخطوة النشر.      |

## <a name="related-content"></a>المحتويات ذات الصلة

[نشر أساسيات Microsoft 365 Lighthouse](m365-lighthouse-deploy-baselines.md) (مقالة)\
[نهج الوصول المشروط الشائعة](/azure/active-directory/conditional-access/concept-conditional-access-policy-common) (المقالة)\
[الأسئلة المتداولة حول Microsoft 365 Lighthouse](m365-lighthouse-faq.yml) (مقالة)
