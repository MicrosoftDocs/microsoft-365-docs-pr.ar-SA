---
title: متطلبات Microsoft Defender for Business
description: متطلبات الترخيص والأجهزة والبرامج Microsoft Defender for Business
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: overview
ms.prod: m365-security
ms.technology: mdb
ms.localizationpriority: medium
ms.reviewer: shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
- m365-initiative-defender-business
ms.openlocfilehash: ab24e3898d897df6813338fd0d2131c3787f0a09
ms.sourcegitcommit: 66228a5506fdceb4cbf0d55b9de3f2943740134f
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 06/15/2022
ms.locfileid: "66089573"
---
# <a name="microsoft-defender-for-business-requirements"></a>متطلبات Microsoft Defender for Business

تصف هذه المقالة متطلبات Microsoft Defender for Business.

## <a name="what-to-do"></a>ما يجب فعله

1. [راجع المتطلبات وتأكد من تلبيتها](#review-the-requirements).
2. [تابع إلى خطواتك التالية](#next-steps).


## <a name="review-the-requirements"></a>مراجعة المتطلبات

يسرد الجدول التالي المتطلبات الأساسية لتكوين Microsoft Defender for Business واستخدامها.

| شرط | الوصف |
|:---|:---|
| الاشتراك | Microsoft 365 Business Premium أو Microsoft Defender for Business (مستقل). اطلع [على كيفية الحصول على Microsoft Defender for Business](get-defender-business.md).<br/><br/>لاحظ أنه إذا كان لديك اشتراكات متعددة، فإن أعلى اشتراك له الأسبقية. على سبيل المثال، إذا كان لديك Microsoft Defender لنقطة النهاية الخطة 2 (الاشتراك الذي تم شراؤه أو الاشتراك التجريبي)، وتحصل على Microsoft Defender for Business، فإن Defender for Endpoint Plan 2 له الأسبقية. في هذه الحالة، لن ترى تجربة Defender for Business.  |
| Datacenter | أحد مواقع مراكز البيانات التالية: <br/>- الاتحاد الأوروبي <br/>- المملكة المتحدة <br/>- الولايات المتحدة |
| حسابات المستخدمين | - يتم إنشاء حسابات المستخدمين في مركز مسؤولي Microsoft 365 ([https://admin.microsoft.com](https://admin.microsoft.com))<br/>- يتم تعيين تراخيص Microsoft Defender for Business في مركز مسؤولي Microsoft 365<br/><br/>للحصول على تعليمات حول هذه المهمة، راجع [إضافة مستخدمين وتعيين التراخيص](mdb-add-users.md). |
| الأذونات  | للتسجيل للحصول على Microsoft Defender for Business، يجب أن تكون مسؤول عمومية.<br/><br/>للوصول إلى مدخل Microsoft 365 Defender، يجب أن يكون لدى المستخدمين أحد [الأدوار التالية في Azure AD](mdb-roles-permissions.md) المعينة: <br/>- قارئ الأمان<br/>- مسؤول الأمان<br/>- مسؤول العالمية<br/><br/>لمعرفة المزيد، راجع [الأدوار والأذونات في Microsoft Defender for Business](mdb-roles-permissions.md). |
| متطلبات المستعرض | Microsoft Edge أو Google Chrome |
| نظام التشغيل | لإدارة الأجهزة في مدخل Microsoft 365 Defender، يجب أن تعمل أجهزتك بأحد أنظمة التشغيل التالية: <br/>- Windows 10 Business أو أحدث <br/>- Windows 10 Professional أو إصدار أحدث <br/>- Windows 10 Enterprise أو أحدث <br/>- macOS (الإصدارات الثلاثة الأحدث مدعومة)<br/><br/>تأكد من تثبيت [KB5006738](https://support.microsoft.com/topic/october-26-2021-kb5006738-os-builds-19041-1320-19042-1320-and-19043-1320-preview-ccbce6bf-ae00-4e66-9789-ce8e7ea35541) على أجهزة Windows. <br/><br/>إذا كنت تدير الأجهزة بالفعل في Microsoft Intune، يمكنك الاستمرار في استخدام مركز إدارة إدارة نقاط النهاية من Microsoft. |

> [!NOTE]
> يتم استخدام [Azure Active Directory (Azure AD)](/azure/active-directory/fundamentals/active-directory-whatis) لإدارة أذونات المستخدم ومجموعات الأجهزة. يتم تضمين Azure AD في اشتراك Defender for Business. 
> - إذا لم يكن لديك اشتراك Microsoft 365 قبل بدء الإصدار التجريبي، فسيتم توفير Azure AD لك أثناء عملية التنشيط. 
> - إذا كان لديك اشتراك Microsoft 365 آخر عند بدء تشغيل الإصدار التجريبي من Defender for Business، يمكنك استخدام خدمة Azure AD الموجودة. 
> - إذا كنت تستخدم [Microsoft 365 Business Premium](../../business/index.yml) عند بدء تشغيل الإصدار التجريبي من Defender for Business، فسيتوفر لديك خيار إدارة أجهزتك باستخدام Intune. 

## <a name="next-steps"></a>الخطوات التالية

تابع إلى [الخطوة 2: تعيين الأدوار والأذونات في Microsoft Defender for Business](mdb-roles-permissions.md).
 
