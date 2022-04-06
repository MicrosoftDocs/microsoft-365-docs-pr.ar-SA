---
title: تسجيل الشريك
description: يمكن للشركاء تسجيل الأجهزة التي يمكن إدارتها بواسطة Microsoft Managed Desktop
ms.service: m365-md
author: tiaraquan
f1.keywords:
- NOCSH
ms.author: tiaraquan
ms.localizationpriority: medium
ms.collection: M365-modern-desktop
manager: dougeby
ms.topic: article
audience: Admin
ms.openlocfilehash: af1e187c77acde257fa3458709fae50616cf810d
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/08/2022
ms.locfileid: "63704833"
---
# <a name="partner-registration"></a>تسجيل الشريك

تصف هذه المقالة الخطوات اللازمة للشركاء لتسجيل الأجهزة. تم توثيق عملية تسجيل الأجهزة بنفسك في [التسجيل اليدوي](manual-registration.md).

## <a name="prepare-for-registration"></a>التحضير للتسجيل

قبل إكمال التسجيل للعميل، يجب أولا إنشاء علاقة معه في [مركز الشركاء](https://partner.microsoft.com/dashboard). لمزيد من المعلومات حول هذه العملية، راجع [وثائق الموافقة](/windows/deployment/windows-autopilot/registration-auth#csp-authorization). يمكن لأي شريك في CSP إضافة أجهزة نيابة عن أي عميل، طالما وافق العميل. يمكنك أيضا معرفة المزيد حول علاقات الشركاء وأذونات Autopilot في [تعليمات مركز الشريك](/partner-center/customers_revoke_admin_privileges#windows-autopilot).

> [!NOTE]
> هذه الوثائق للشركاء وشركاة الأعمال الأصلية فقط. يتم توثيق عملية التسجيل الذاتي في [التسجيل اليدوي](manual-registration.md).

## <a name="register-devices-using-the-partner-center"></a>تسجيل الأجهزة باستخدام مركز الشركاء

بعد إنشاء العلاقة مع العملاء، يمكنك استخدام مركز الشركاء لإضافة أجهزة إلى Autopilot لأي من العملاء.

**لتسجيل الأجهزة باستخدام مركز الشركاء:**

1. انتقل إلى [مركز الشركاء](https://partner.microsoft.com/dashboard).
2. حدد **العملاء** من القائمة مركز الشركاء، ثم حدد العميل الذي تريد إدارة أجهزته.
3. في صفحة تفاصيل العميل، حدد **الأجهزة**.
4. ضمن **تطبيق ملفات التعريف** على الأجهزة، حدد **إضافة أجهزة**.
5. أدخل علامة المجموعة المناسبة لملف تعريف الجهاز الذي حددته (كما هو موضح في الجدول التالي)، ثم حدد استعراض لتحميل قائمة العميل  (بتنسيق ملف .csv) إلى مركز الشركاء.

| [ملف تعريف الجهاز](../service-description/profiles.md) | علامة المجموعة |
| ----- | -----|
| البيانات الحساسة | **Microsoft365ManagedSensitiveData\_** |
| مستخدم الطاقة | **Microsoft365ManagedPowerUser\_** |
| Standard | **Microsoft365ManagedStandard\_** |

> [!IMPORTANT]
> يجب أن يكون اسم المجموعة مطابقا تماما لتلك المدرجة في الجدول، بما في ذلك الأحرف كبيرة الأحرف والأحرف الخاصة. سيسمح ذلك بتعيين الأجهزة المسجلة حديثا باستخدام ملف تعريف Autopilot لسطح المكتب المدار من Microsoft.

>[!NOTE]
> يجب أن تكون قد تلقيت .csv هذا الملف مع شراء جهازك. إذا لم تتلق ملفا .csv، يمكنك إنشاء ملف بنفسك باتباع الخطوات في إضافة أجهزة إلى Windows [Autopilot](/windows/deployment/windows-autopilot/add-devices#collecting-the-hardware-id-from-existing-devices-using-powershell). المتطلبات: <ul><li>الأعمدة الإضافية غير معتمدة.</li> <li>علامات الاقتباس غير معتمدة.</li> <li>يمكن استخدام الملفات النصية بتنسيق ANSI فقط (وليس Unicode).</li> <li>تتحسس رؤوس الاصهار حالة التحسس.</li></ul> لن يؤدي تحرير الملف Excel حفظه كملف CSV إلى إنشاء ملف قابل للاستخدام بسبب هذه المتطلبات. تأكد من الاحتفاظ بأي أصفار سفل في الأرقام التسلسلية للجهاز. يجب على الشركاء [استخدام Get-WindowsAutoPilotInfo](https://www.powershellgallery.com/packages/Get-WindowsAutoPilotInfo) لتسجيل الأجهزة لأجهزة سطح المكتب المدارة من Microsoft في مركز الشركاء.

إذا تلقيت رسالة خطأ أثناء محاولة تحميل الملف .csv، فتحقق من تنسيق الملف. تأكد من أن ترتيب العمود يتطابق مع ما هو موضح في استخدام Windows Autopilot على الأجهزة الجديدة لتخصيص تجربة العميل غير [المجهزة](/partner-center/autopilot#add-devices-to-a-customers-account). يمكنك أيضا استخدام نموذج .csv الذي تم توفيره من الارتباط إلى جانب **إضافة أجهزة** لإنشاء قائمة أجهزة.

لمزيد من المعلومات حول Autopilot في سيناريوهات الشريك، راجع [إضافة أجهزة إلى حساب عميل](/partner-center/autopilot#add-devices-to-a-customers-account).

## <a name="register-devices-by-using-the-oem-api"></a>تسجيل الأجهزة باستخدام API (API) في الشركات الأصلية

قبل إكمال تسجيل أحد العملاء، يجب أولا إنشاء علاقة معه. يجب أن يكون لديك ارتباط فريد لتوفيره للعملاء المعنيين. راجع [كيفية إنشاء علاقة OEM](/windows/deployment/windows-autopilot/registration-auth#oem-authorization).

بعد إنشاء العلاقة، يمكنك بدء تسجيل الأجهزة للعملاء باستخدام علامة المجموعة المناسبة لكل ملف تعريف جهاز تم تحديده:

| ملف تعريف الجهاز | علامة المجموعة |
| ----- | ----- |
| البيانات الحساسة | **Microsoft365ManagedSensitiveData\_** |
| مستخدم الطاقة | **Microsoft365ManagedPowerUser\_** |
| Standard | **Microsoft365ManagedStandard\_** |

> [!IMPORTANT]
> يجب أن تتطابق علامات المجموعة تماما مع تلك المدرجة في الجدول، بما في ذلك الأحرف الخاصة والأحرف الخاصة. سيسمح ذلك بتعيين الأجهزة المسجلة حديثا باستخدام ملف تعريف Autopilot لسطح المكتب المدار من Microsoft.
