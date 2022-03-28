---
title: متطلبات Microsoft Defender for Business
description: متطلبات ترخيص Microsoft Defender for Business والأجهزة والبرامج
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: overview
ms.date: 03/15/2022
ms.prod: m365-security
ms.technology: mdb
ms.localizationpriority: medium
ms.reviewer: shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
- m365-initiative-defender-business
ms.openlocfilehash: 17954ec9c01a053f847a7d8a74188edf2f4e4091
ms.sourcegitcommit: 3fb76db6b34e24569417f4c8a41b99f46a780389
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/17/2022
ms.locfileid: "63575170"
---
# <a name="microsoft-defender-for-business-requirements"></a>متطلبات Microsoft Defender for Business

> [!IMPORTANT]
> يتم طرح Microsoft Defender for Business Microsoft 365 Business Premium العملاء[](../../business-premium/index.md)، بدءا من 1 مارس 2022. يتم عرض Defender for Business لاشتراك مستقل في المعاينة، وسينتهى طرحه تدريجيا للعملاء وشركاء المعلومات الذين سجلوا هنا [](https://aka.ms/mdb-preview) لطلبه. تتضمن [المعاينة مجموعة أولية من السيناريوهات](mdb-tutorials.md#try-these-preview-scenarios)، وسنضيف القدرات بشكل منتظم.
> 
> تتعلق بعض المعلومات الواردة في هذه المقالة بالمنتجات/الخدمات التي تم إصدارها مسبقا التي قد يتم تعديلها بشكل كبير قبل إصدارها تجاريا. لا تقدم Microsoft أي ضمانات، صريحة أو ضمنية، للمعلومات المتوفرة هنا. 

تصف هذه المقالة متطلبات Microsoft Defender for Business.

## <a name="what-to-do"></a>ما يجب فعله

1. [راجع المتطلبات وتأكد من تلبيتها](#review-the-requirements).

2. [تابع إلى الخطوات التالية](#next-steps).

>
> **هل لديك دقيقة؟**
> الرجاء إجراء <a href="https://microsoft.qualtrics.com/jfe/form/SV_0JPjTPHGEWTQr4y" target="_blank">استطلاع قصير حول Microsoft Defender for Business</a>. إننا نحب أن نستمع إلى هذه التكاتف!
>

## <a name="review-the-requirements"></a>مراجعة المتطلبات

يسرد الجدول التالي المتطلبات الأساسية لتكوين Microsoft Defender for Business واستخدامه. <br/><br/>

| المتطلب | الوصف |
|:---|:---|
| الاشتراك | Microsoft 365 Business Premium <br/>--- أو ---<br/>Microsoft Defender for Business (مستقل؛ حاليا في وضع المعاينة). <br/><br/> راجع [كيفية الحصول على Microsoft Defender for Business](get-defender-business.md).<br/><br/>لاحظ أنه إذا كان لديك اشتراكات متعددة، فإن أعلى اشتراك له الأسبقية. على سبيل المثال، إذا كان لديك Microsoft Defender لخطة نقطة النهاية 2 (التي تم شراؤها أو الاشتراك التجريبي)، وكان ل Microsoft Defender for Business، فإن Defender for Endpoint Plan 2 له الأسبقية. في هذه الحالة، لن ترى تجربة Defender for Business.  |
| Datacenter | أحد مواقع مراكز البيانات التالية: <br/>- الاتحاد الأوروبي <br/>- المملكة المتحدة <br/>- الولايات المتحدة |
| حسابات المستخدمين | يتم إنشاء حسابات المستخدمين في مركز مسؤولي Microsoft 365 ([https://admin.microsoft.com](https://admin.microsoft.com))<br/><br/>يتم تعيين تراخيص Microsoft Defender for Business في مركز مسؤولي Microsoft 365<br/><br/>للحصول على تعليمات حول هذه المهمة، راجع [إضافة مستخدمين وتعيين تراخيص](../../admin/add-users/add-users.md). |
| الأذونات  | التسجيل في Microsoft Defender for Business، يجب أن تكون المسؤول العام.<br/><br/>للوصول إلى Microsoft 365 Defender، يجب أن يكون للمستخدمين أحد الأدوار [التالية في Azure AD](mdb-roles-permissions.md) المعين: <br/>- قارئ الأمان<br/>- مسؤول الأمان<br/>- المسؤول العام<br/><br/>لمعرفة المزيد، راجع [الأدوار والأذونات في Microsoft Defender for Business](mdb-roles-permissions.md). |
| متطلبات المستعرض | Microsoft Edge أو Google Chrome |
| نظام التشغيل | لإدارة الأجهزة في Microsoft Defender for Business، يجب أن تقوم أجهزتك بتشغيل أحد أنظمة التشغيل التالية: <br/>- Windows 10 Business أو أي وقت لاحق <br/>- Windows 10 Professional أو أي وقت لاحق <br/>- Windows 10 Enterprise أو لاحقا <br/><br/>تأكد من تثبيت [KB5006738](https://support.microsoft.com/topic/october-26-2021-kb5006738-os-builds-19041-1320-19042-1320-and-19043-1320-preview-ccbce6bf-ae00-4e66-9789-ce8e7ea35541) . <br/><br/>إذا كنت تقوم بالفعل بإدارة الأجهزة في Microsoft Intune (أو إدارة نقاط النهاية من Microsoft)، يمكنك اجهزتك على Defender for Business. |
| التكامل مع إدارة نقاط النهاية من Microsoft  | إذا كنت تخطط لتهيئة الأجهزة المجهزة للعمل باستخدام [تكوين أمان Microsoft Defender for Business](mdb-onboard-devices.md#microsoft-defender-for-business-security-configuration)، فيجب تلبية المتطلبات التالية:<br/><br/>يجب أن تكون المتطلبات الأساسية [متطلبا أساسيا لإدارة الأمان ل Microsoft Defender لنقطة النهاية](/mem/intune/protect/mde-security-integration).<br/>- يجب تكوين Azure AD حتى يتم إنشاء الثقة بين أجهزة الشركة و Azure AD. <br/>- يجب تمكين إدارة الأمان في Defender for Business في إدارة نقاط النهاية من Microsoft.<br/><br/>يجب أن تكون الأجهزة قادرة على الاتصال عناوين URL التالية:<br/>- `enterpriseregistration.windows.net` (للتسجيل في Azure AD)<br/>- `login.microsoftonline.com` (للتسجيل في Azure AD)<br/>- `*.dm.microsoft.com` (يدعم أحرف البدل (*) نقاط نهاية الخدمة السحابية المستخدمة للتسجيل والتحقق من الوصول وإعداد التقارير، ويمكن أن تتغير مع تغيير مقياس الخدمة.) |

> [!NOTE]
> [يتم استخدام Azure Active Directory (Azure AD)](/azure/active-directory/fundamentals/active-directory-whatis) لإدارة أذونات المستخدمين ومجموعات الأجهزة. يتم تضمين Azure AD في اشتراك Defender for Business. 
> - إذا لم يكن لديك اشتراك Microsoft 365 قبل بدء الإصدار التجريبي، سيتم توفير Azure AD لك أثناء عملية التنشيط. 
> - إذا كان لديك اشتراك Microsoft 365 آخر عند بدء تشغيل الإصدار التجريبي من Defender for Business، يمكنك استخدام خدمة Azure AD الموجودة. 
> - إذا كنت [تستخدم Microsoft 365 Business Premium الإصدار](../../business/index.yml) التجريبي من Defender for Business، سيكون لديك خيار إدارة الأجهزة في Microsoft Intune. 

## <a name="next-steps"></a>الخطوات التالية

تابع إلى:

- [الخطوة 2: تعيين الأدوار والأذونات في Microsoft Defender for Business](mdb-roles-permissions.md) 
 