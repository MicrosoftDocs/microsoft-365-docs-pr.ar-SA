---
title: ضبط الإعدادات بعد التسجيل
description: كيفية استبعاد حسابات Microsoft معينة
keywords: سطح المكتب المدار من Microsoft، Microsoft 365، الخدمة، الوثائق
ms.service: m365-md
author: tiaraquan
ms.localizationpriority: medium
ms.collection: M365-modern-desktop
ms.author: tiaraquan
manager: dougeby
ms.topic: article
ms.openlocfilehash: a5ff8a9a662eb442b7a18726463f14e914d4a133
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/08/2022
ms.locfileid: "63566583"
---
# <a name="adjust-settings-after-enrollment"></a>ضبط الإعدادات بعد التسجيل

بعد الانتهاء من التسجيل في Microsoft Managed Desktop، قد تحتاج بعض إعدادات الإدارة إلى تعديل. للتحقق والضبط إذا لزم الأمر، اتبع الخطوات التالية:

1. راجع إعدادات Microsoft Intune Azure Active Directory الموضحة في القسم التالي.
2. إذا كان أي من العناصر ينطبق على بيئتك، ف قم بإجراء التعديلات كما هو موضح.
3. إذا كنت تريد التحقق مرة أخرى من صحة كل الإعدادات، يمكنك إعادة تشغيل أداة تقييم الجهوزية لضمان عدم تعارض أي شيء مع Microsoft Managed Desktop.[](https://aka.ms/mmdart)

> [!NOTE]
> مع استمرار العمليات في الأشهر التالية، إذا قمت بإجراء تغييرات بعد التسجيل في سياسات Microsoft Intune أو Azure Active Directory أو Microsoft 365 التي تؤثر على Microsoft Managed Desktop، فمن المحتمل أن يتوقف Microsoft Managed Desktop عن العمل بشكل صحيح. لتجنب حدوث مشاكل في الخدمة، تحقق من الإعدادات المحددة الموضحة في [](../get-ready/readiness-assessment-fix.md) إصلاح المشاكل التي عثرت عليها أداة تقييم الجهوزية قبل تغيير السياسات المدرجة هناك. يمكنك أيضا إعادة تشغيل أداة تقييم الجهوزية في أي وقت.

## <a name="microsoft-intune-settings"></a>Microsoft Intune الإعدادات

| الإعداد | الوصف |
| ------ | ------ |
| ملف تعريف نشر Autopilot | إذا كنت تستخدم أي من سياسات Autopilot، فحدث كل منها لاستبعاد أجهزة **مكان العمل الحديثة -كل** مجموعة Azure AD. <br><br> **لتحديث سياسات Autopilot:** <br><br> ضمن **الواجبات**، في المجموعات المستبعدة، حدد أجهزة مكان العمل الحديثة **-** كل مجموعة Azure AD التي تم إنشاؤها أثناء تسجيل سطح المكتب المدار من Microsoft. <br><br> سينشئ Microsoft Managed Desktop أيضا ملف تعريف Autopilot، الذي سيكون "Modern Workplace" في الاسم (ملف تعريف **Autopilot** في مكان العمل الحديث). عند تحديث ملفات تعريف Autopilot الخاصة بك، تأكد من أنك لا  تستبعد مجموعة أجهزة مكان العمل الحديثة **-** كل Azure AD من ملف تعريف **Autopilot** في مكان العمل الحديث الذي تم إنشاؤه بواسطة Microsoft Managed Desktop. |
| نهج الوصول المشروط | إذا قمت بإنشاء أي سياسات وصول شرطي جديدة ذات صلة ب Azure AD أو Microsoft Intune أو Microsoft 365 Defender لنقطة النهاية بعد تسجيل Microsoft Managed Desktop، فاستبعد مجموعة حسابات خدمة مكان العمل **الحديثة Azure** AD منها. لمزيد من المعلومات، راجع [الوصول الشرطي: المستخدمون والمجموعات](/azure/active-directory/conditional-access/concept-conditional-access-users-groups). يحافظ Microsoft Managed Desktop على سياسات وصول شرطي منفصلة لتقييد الوصول إلى هذه الحسابات. <br><br> **لمراجعة نهج الوصول الشرطي لسطح المكتب المدار من Microsoft (مساحة العمل الحديثة – محطة عمل آمنة):** <br><br> انتقل إلى إدارة نقاط النهاية من Microsoft وانتقل إلى **الوصول الشرطي** في **أمان نقطة النهاية**. لا تعدل أي من سياسات الوصول الشرطي في Azure AD التي تم إنشاؤها بواسطة Microsoft Managed Desktop التي لها "مساحة عمل حديثة" في الاسم. |
| المصادقة متعددة العوامل | إذا قمت بإنشاء أي متطلبات مصادقة متعددة العوامل جديدة في نهج الوصول الشرطي المتعلقة ب Azure AD أو Intune أو Microsoft 365 Defender لنقطة النهاية بعد تسجيل Microsoft Managed Desktop، فاستبعد مجموعة حسابات خدمة مكان العمل **الحديثة Azure** AD منها. لمزيد من المعلومات، راجع [الوصول الشرطي: المستخدمون والمجموعات](/azure/active-directory/conditional-access/concept-conditional-access-users-groups). يحافظ Microsoft Managed Desktop على سياسات وصول شرطي منفصلة لتقييد الوصول إلى أعضاء هذه المجموعة. <br><br> **لمراجعة نهج الوصول الشرطي لسطح المكتب المدار من Microsoft (Modern Workplace -):** <br><br> انتقل إلى إدارة نقاط النهاية من Microsoft وانتقل إلى **الوصول الشرطي** في **أمان نقطة النهاية**.
| Windows 10 التحديث | بالنسبة لأي Windows 10 نهج حلقة التحديث التي أنشأتها، قم باستبعاد مجموعة أجهزة مكان العمل الحديثة **-كل** Azure AD من كل نهج. لمزيد من المعلومات، راجع [إنشاء حلقات التحديث وتعيينها](/mem/intune/protect/windows-10-update-rings#create-and-assign-update-rings). <br><br> سينشئ سطح المكتب المدار من Microsoft أيضا بعض سياسات حلقة التحديث، وكلها سيكون لها "مكان عمل حديث" في الاسم. على سبيل المثال: <ul><li>نهج تحديث مكان العمل الحديث [واسع]</li><li>نهج تحديث مساحة العمل الحديثة [سريع]</li><li>نهج تحديث مساحة العمل الحديثة [أولا]</li><li>نهج تحديث مساحة العمل الحديثة [اختبار]</li></ul> <br>عند تحديث سياساتك الخاصة، تأكد من أنك لا تستبعد مجموعة أجهزة مكان العمل الحديثة **-** كل Azure AD من تلك التي أنشأها Microsoft Managed Desktop. |

## <a name="azure-active-directory-settings"></a>إعدادات Azure Active Directory

إعادة تعيين كلمة مرور الخدمة الذاتية: إذا كنت تستخدم إعادة تعيين كلمة مرور الخدمة الذاتية لجميع المستخدمين، فضبط الواجب لاستبعاد حسابات خدمة سطح المكتب المدار من Microsoft.

**لضبط هذا الواجب:**

1. إنشاء مجموعة Azure AD ديناميكية لجميع المستخدمين *باستثناء حسابات* خدمة سطح المكتب المدار من Microsoft
1. استخدم هذه المجموعة للوا تعيين بدلا من "جميع المستخدمين".

لمساعدتك في العثور على حسابات الخدمة واستبعادها، إليك مثال على استعلام ديناميكي يمكنك استخدامه:

```Console
(user.objectID -ne null) and (user.userPrincipalName -ne "MSADMIN@TENANT.onmicrosoft.com") and (user.userPrincipalName -ne "MSADMININT@TENANT.onmicrosoft.com") and (user.userPrincipalName -ne "MWAAS_SOC_RO@TENANT.onmicrosoft.com") and (user.userPrincipalName -ne "MWAAS_WDGSOC@TENANT.onmicrosoft.com") and (user.userPrincipalName -ne "MSTEST@TENANT.onmicrosoft.com")
```

في هذا الاستعلام، استبدل `@TENANT` باسم مجال المستأجر.

## <a name="steps-to-get-started-with-microsoft-managed-desktop"></a>خطوات بدء تشغيل Microsoft Managed Desktop

1. مدخل [مسؤول Access](access-admin-portal.md).
1. [إضافة جهات اتصال المسؤول والتحقق منها في مدخل المسؤول](add-admin-contacts.md).
1. ضبط الإعدادات بعد التسجيل (هذه المقالة).
1. نشر [Intune Company Portal.](company-portal.md)
1. [تعيين التراخيص](assign-licenses.md).
1. [نشر التطبيقات](deploy-apps.md).
1. [تحضير الأجهزة](prepare-devices.md).
1. قم بإعداد [تجربة التشغيل الأولي باستخدام Autopilot وصفحة حالة التسجيل](esp-first-run.md).
1. [تمكين ميزات دعم المستخدم](enable-support.md).
1. [اجهز المستخدمين لاستخدام الأجهزة](get-started-devices.md).
1. [بدء استخدام عنصر تحكم التطبيق](get-started-app-control.md).
