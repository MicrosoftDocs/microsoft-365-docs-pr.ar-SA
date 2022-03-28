---
title: استخدم الدليل خطوة بخطوة لإضافة أجهزة Autopilot وملف التعريف
f1.keywords:
- NOCSH
ms.author: efrene
author: efrene
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.collection:
- M365-subscription-management
- M365-identity-device-management
- Adm_TOC
ms.localizationpriority: medium
ms.custom:
- Core_O365Admin_Migration
- MiniMaven
- MSB365
- OKR_SMB_M365
- seo-marvel-mar
- AdminSurgePortfolio
- AdminTemplateSet
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: be5b6d90-3344-4c5e-bf40-5733eb845beb
description: تعرف على كيفية استخدام Windows AutoPilot لإعداد أجهزة Windows 10 جديدة للأعمال بحيث تكون جاهزة لاستخدام الموظفين.
ms.openlocfilehash: 12e86102633ddfc19960fb561b2a626da29f0560
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/08/2022
ms.locfileid: "63575638"
---
# <a name="use-the-step-by-step-guide-to-add-autopilot-devices-and-profile"></a>استخدم الدليل خطوة بخطوة لإضافة أجهزة Autopilot وملف التعريف

> [!NOTE]
> يتم طرح Microsoft Defender for Business Microsoft 365 Business Premium العملاء، بدءا من 1 مارس 2022. يوفر هذا العرض ميزات أمان إضافية للأجهزة. [تعرف على المزيد حول Defender for Business](../../security/defender-business/mdb-overview.md).

يمكنك استخدام Windows AutoPilot لإعداد أجهزة Windows 10 جديدة للأعمال بحيث تكون  جاهزة للاستخدام عند منحها للموظفين.
  
## <a name="device-requirements"></a>متطلبات الجهاز

يجب أن تلبي الأجهزة هذه المتطلبات:
  
- Windows 10 الإصدار 1703 أو الإصدارات الأحدث
    
- الأجهزة الجديدة التي لم تمر عبر تجربة Windows غير المجهزة
    
## <a name="use-the-setup-guide-to-create-devices-and-profiles"></a>استخدام دليل الإعداد لإنشاء الأجهزة وملفات التعريف

إذا لم تكن قد أنشأت مجموعات الأجهزة أو ملفات التعريف بعد، فإن أفضل طريقة للبدء هي باستخدام الدليل خطوة بخطوة. يمكنك أيضا [إضافة أجهزة وتعيين](create-and-edit-autopilot-devices.md) [ملفات تعريف](create-and-edit-autopilot-profiles.md) إليها دون استخدام الدليل. 
  
1. انتقل إلى مركز الإدارة في <a href="https://go.microsoft.com/fwlink/p/?linkid=837890" target="_blank">https://admin.microsoft.com</a>.

2. في جزء التنقل الأيسر، اختر **الأجهزة** \> **AutoPilot**.

    ![في مركز الإدارة، اختر الأجهزة ثم AutoPilot.](../../media/AutoPilot.png)
  
2. في صفحة **AutoPilot** ، انقر فوق دليل البدء أو اضغط **عليه**.
    
    ![انقر فوق دليل البدء للحصول على إرشادات مفصلة خطوة بخطوة ل Autopilot.](../../media/31662655-d1e6-437d-87ea-c0dec5da56f7.png)
  
3. على الصفحة **Upload .csv** مع قائمة الأجهزة، استعرض بحثا عن موقع حيث تم إعداد ملف .CSV، ثم **افتح** \> **التالي**. يجب أن يحتوي الملف على ثلاثة رؤوس:
    
    - العمود A: الرقم التسلسلي للجهاز
    
    - العمود ب: Windows المنتج
    
    - العمود C: هاش الأجهزة
    
    يمكنك الحصول على هذه المعلومات من مورد الأجهزة، أو يمكنك استخدام البرنامج النصي [Get-WindowsAutoPilotInfo PowerShell](https://www.powershellgallery.com/packages/Get-WindowsAutoPilotInfo) لإنشاء ملف CSV. 
    
    لمزيد من المعلومات، راجع [قائمة الأجهزة ملف CSV](../misc/device-list.md). يمكنك أيضا تنزيل نموذج ملف على Upload .csv **الملف مع قائمة الأجهزة**. 
    
> [!NOTE]
> يستخدم هذا البرنامج النصي WMI لاسترداد الخصائص المطلوبة للعميل لتسجيل جهاز باستخدام Windows Autopilot. تجدر الإشارة إلى أنه من الطبيعي ألا يقوم ملف CSV الناتج بتجميع قيمة "ملف منتج Windows" (PKID) نظرا لأن هذا ليس مطلوبا لتسجيل جهاز وأن PKID يكون NULL في الإخراج CSV على ما يرام تماما. سيتم ملء الرقم التسلسلي وهاش الأجهزة فقط.
    
4. في الصفحة **تعيين ملف تعريف** ، يمكنك إما اختيار ملف تعريف موجود أو إنشاء ملف تعريف جديد. إذا لم يكن لديك واحدة بعد، فسوف يتم مطالبتك بإنشاء واحدة. 
    
    ملف التعريف عبارة عن مجموعة من الإعدادات التي يمكن تطبيقها على جهاز واحد أو على مجموعة من الأجهزة.
    
    الميزات الافتراضية مطلوبة، كما يتم تعيينها تلقائيا. الميزات الافتراضية هي:
    
    - تخطي Cortana تسجيل OneDrive و OEM.
    
    - يمكنك إنشاء تجربة تسجيل الدخول باستخدام العلامة التجارية للشركة.
    
    - الاتصال أجهزتك إلى حسابات Azure Active Directory، ثم سجلها تلقائيا لكي يتم إدارتها بواسطة Microsoft 365 Business Premium.
    
    لمزيد من المعلومات، راجع [حول إعدادات ملف تعريف AutoPilot](autopilot-profile-settings.md). 
    
5. الإعدادات الأخرى هي **تخطي إعدادات الخصوصية** ولا تسمح للمستخدم بأن **يصبح المسؤول المحلي**. يتم تعيين كل منهما إلى **إيقاف التشغيل** بشكل افتراضي. 
    
    اختر **التالي**.
    
6. **لقد انتهيت** مما يشير إلى أنه سيتم تطبيق ملف التعريف الذي أنشأته (أو اخترته) على مجموعة الأجهزة التي أنشأتها عن طريق تحميل قائمة الأجهزة. ستكون الإعدادات في وضع التنفيذ عندما يقوم مستخدمو الجهاز تسجيل الدخول بعد ذلك. اختر **إغلاق**.

## <a name="related-content"></a>المحتوى ذي الصلة

[حول إعدادات ملف تعريف AutoPilot](autopilot-profile-settings.md) (مقالة)\
[خيارات لحماية أجهزتك وبيانات التطبيق](../devices/choose-device-security.md) (مقالة) أفضل [10 طرق لتأمين Microsoft 365 لخطط الأعمال](../security-and-compliance/secure-your-business-data.md)