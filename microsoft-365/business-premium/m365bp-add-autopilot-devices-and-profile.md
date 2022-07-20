---
title: استخدم هذا الدليل المفصل خطوة بخطوة لإضافة أجهزة Autopilot وملف التعريف
f1.keywords:
- NOCSH
ms.author: deniseb
author: denisebmsft
manager: dansimp
audience: Admin
ms.topic: how-to
ms.service: o365-administration
ms.collection: ''
ms.localizationpriority: high
ms.date: 07/19/2022
ms.custom:
- MiniMaven
- OKR_SMB_M365
search.appverid:
- BCS160
- MET150
- MOE150
description: تعرف على كيفية استخدام Windows Autopilot لإعداد أجهزة Windows 10 جديدة لأعمالك بحيث تكون جاهزة لاستخدام الموظفين.
ms.openlocfilehash: 72a35557d3ab70c5e11f91f366b9cbe003b0c4c6
ms.sourcegitcommit: c1eaea74c8ffce2f9f477c9469342e88e4a70c14
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/20/2022
ms.locfileid: "66893244"
---
# <a name="use-this-step-by-step-guide-to-add-autopilot-devices-and-profile"></a>استخدم هذا الدليل المفصل خطوة بخطوة لإضافة أجهزة Autopilot وملف التعريف

يمكنك استخدام Windows Autopilot لإعداد أجهزة Windows 10 **جديدة** لعملك بحيث تكون جاهزة للاستخدام عند منحها لموظفيك.
  
## <a name="device-requirements"></a>متطلبات الجهاز

يجب أن تفي الأجهزة بهذه المتطلبات:
  
- Windows 10، الإصدار 1703 أو أحدث

- الأجهزة الجديدة التي لم تمر بتجربة Windows الجاهزة

## <a name="use-the-setup-guide-to-add-devices-and-profiles"></a>استخدام دليل الإعداد لإضافة الأجهزة وملفات التعريف

إذا لم تكن قد أنشأت مجموعات أجهزة أو ملفات تعريف حتى الآن، فإن أفضل طريقة للبدء هي باستخدام الدليل المفصل خطوة بخطوة. يمكنك أيضا [إضافة أجهزة Autopilot](m365bp-create-and-edit-Autopilot-devices.md) [وتعيين ملفات تعريف](../admin/devices/create-and-edit-Autopilot-profiles.md) إليها دون استخدام الدليل.
  
1. الانتقال إلى مركز الإدارة في <a href="https://go.microsoft.com/fwlink/p/?linkid=837890" target="_blank">https://admin.microsoft.com</a>.

2. في جزء التنقل الأيمن، اختر **Devices** \> **Autopilot**.

    ![في مركز الإدارة، اختر الأجهزة ثم Autopilot.](../media/Autopilot.png)
  
3. في صفحة **Autopilot** ، انقر فوق **دليل البدء** أو اضغط عليه.

    ![انقر فوق دليل البدء للحصول على إرشادات مفصلة خطوة بخطوة ل Autopilot.](../media/31662655-d1e6-437d-87ea-c0dec5da56f7.png)
  
4. في **ملف "تحميل .csv" مع صفحة قائمة الأجهزة** ، استعرض وصولا إلى موقع حيث تم إعداد ملف .CSV، ثم **افتح** \> **"التالي**". يجب أن يحتوي الملف على ثلاثة رؤوس:

    - العمود A: الرقم التسلسلي للجهاز
    - العمود B: معرف منتج Windows
    - العمود C: تجزئة الأجهزة

يمكنك الحصول على هذه المعلومات من مورد الأجهزة، أو يمكنك استخدام [البرنامج النصي Get-WindowsAutopilotInfo PowerShell](https://www.powershellgallery.com/packages/Get-WindowsAutopilotInfo) لإنشاء ملف CSV.

لمزيد من المعلومات، راجع [ملف CSV لقائمة الأجهزة](../admin/misc/device-list.md). يمكنك أيضا تنزيل نموذج ملف على **ملف Upload .csv مع صفحة قائمة الأجهزة** .

> [!NOTE]
> يستخدم هذا البرنامج النصي WMI لاسترداد الخصائص اللازمة للعميل لتسجيل جهاز باستخدام Windows Autopilot. لاحظ أنه من الطبيعي أن لا يجمع ملف CSV الناتج قيمة معرف منتج Windows (PKID) لأن هذا غير مطلوب لتسجيل جهاز وPKID كونها NULL في إخراج CSV جيد تماما. سيتم ملء الرقم التسلسلي وتجزئة الأجهزة فقط.

5. في صفحة **"تعيين ملف تعريف** "، يمكنك اختيار ملف تعريف موجود أو إنشاء ملف تعريف جديد. إذا لم يكن لديك واحد حتى الآن، فستتم مطالبتك بإنشاء واحد.

    ملف التعريف هو مجموعة من الإعدادات التي يمكن تطبيقها على جهاز واحد أو على مجموعة من الأجهزة.

    الميزات الافتراضية مطلوبة ويتم تعيينها تلقائيا. الميزات الافتراضية هي:

    - تخطي تسجيل Cortana وOneDrive وOEM.

    - إنشاء تجربة تسجيل الدخول باستخدام العلامة التجارية لشركتك.

    - قم بتوصيل أجهزتك بحسابات Azure Active Directory، وقم بتسجيلها تلقائيا لتتم إدارتها بواسطة Microsoft 365 Business Premium.

    لمزيد من المعلومات، راجع [حول إعدادات ملف تعريف Autopilot](m365bp-Autopilot-profile-settings.md).

6. الإعدادات الأخرى هي **إعدادات تخطي الخصوصية** **ولا تسمح للمستخدم بأن يصبح المسؤول المحلي**. يتم تعيين هذين الخيارين إلى **"إيقاف تشغيل"** بشكل افتراضي.

    اختر **"التالي**".

7. **لقد انتهيت** من ذلك يشير إلى أنه سيتم تطبيق ملف التعريف الذي أنشأته (أو اخترته) على مجموعة الأجهزة التي أنشأتها عن طريق تحميل قائمة الأجهزة. ستكون الإعدادات سارية عند تسجيل دخول مستخدمي الجهاز بعد ذلك. اختر **"إغلاق**".

## <a name="related-content"></a>المحتويات ذات الصلة

- [حول إعدادات ملف تعريف Autopilot](../business-premium/m365bp-Autopilot-profile-settings.md) (مقالة)\
- [خيارات لحماية أجهزتك وبيانات التطبيق](../admin/devices/choose-device-security.md) (مقالة)
- [أفضل الممارسات لتأمين خطط Microsoft 365 للأعمال](../admin/security-and-compliance/secure-your-business-data.md)
