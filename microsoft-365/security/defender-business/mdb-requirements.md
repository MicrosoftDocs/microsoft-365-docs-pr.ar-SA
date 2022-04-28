---
title: متطلبات Microsoft Defender for Business
description: متطلبات الترخيص والأجهزة والبرامج Microsoft Defender for Business
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: overview
ms.date: 04/20/2022
ms.prod: m365-security
ms.technology: mdb
ms.localizationpriority: medium
ms.reviewer: shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
- m365-initiative-defender-business
ms.openlocfilehash: 32d0c7d762dd142fcf6cf14faf3f739422c6a3f9
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/27/2022
ms.locfileid: "65095477"
---
# <a name="microsoft-defender-for-business-requirements"></a>متطلبات Microsoft Defender for Business

> [!NOTE]
> تم تضمين Microsoft Defender for Business الآن في [Microsoft 365 Business Premium](../../business-premium/index.md). 

تصف هذه المقالة متطلبات Microsoft Defender for Business.

## <a name="what-to-do"></a>ما يجب فعله

1. [راجع المتطلبات وتأكد من تلبيتها](#review-the-requirements).

2. [تابع إلى خطواتك التالية](#next-steps).

>
> **هل لديك دقيقة؟**
> يرجى أخذ <a href="https://microsoft.qualtrics.com/jfe/form/SV_0JPjTPHGEWTQr4y" target="_blank">استطلاعنا القصير حول الأمان</a>. يسعدنا أن نستمع إليك!
>

## <a name="review-the-requirements"></a>مراجعة المتطلبات

يسرد الجدول التالي المتطلبات الأساسية لتكوين Microsoft Defender for Business واستخدامها.

| شرط | الوصف |
|:---|:---|
| الاشتراك | Microsoft 365 Business Premium <br/>--- أو ---<br/>Microsoft Defender for Business (مستقل؛ قيد المعاينة حاليا). <br/><br/> اطلع [على كيفية الحصول على Microsoft Defender for Business](get-defender-business.md).<br/><br/>لاحظ أنه إذا كان لديك اشتراكات متعددة، فإن أعلى اشتراك له الأسبقية. على سبيل المثال، إذا كان لديك Microsoft Defender لنقطة النهاية الخطة 2 (الاشتراك الذي تم شراؤه أو الاشتراك التجريبي)، وتحصل على Microsoft Defender for Business، فإن Defender for Endpoint Plan 2 له الأسبقية. في هذه الحالة، لن ترى تجربة Defender for Business.  |
| Datacenter | أحد مواقع مراكز البيانات التالية: <br/>- الاتحاد الأوروبي <br/>- المملكة المتحدة <br/>- الولايات المتحدة |
| حسابات المستخدمين | يتم إنشاء حسابات المستخدمين في مركز مسؤولي Microsoft 365 ([https://admin.microsoft.com](https://admin.microsoft.com))<br/><br/>يتم تعيين تراخيص Microsoft Defender for Business في مركز مسؤولي Microsoft 365<br/><br/>للحصول على تعليمات حول هذه المهمة، راجع [إضافة مستخدمين وتعيين التراخيص](mdb-add-users.md). |
| الأذونات  | للتسجيل للحصول على Microsoft Defender for Business، يجب أن تكون مسؤولا عاما.<br/><br/>للوصول إلى مدخل Microsoft 365 Defender، يجب أن يكون لدى المستخدمين أحد [الأدوار التالية في Azure AD](mdb-roles-permissions.md) المعين: <br/>- قارئ الأمان<br/>- مسؤول الأمان<br/>- المسؤول العام<br/><br/>لمعرفة المزيد، راجع [الأدوار والأذونات في Microsoft Defender for Business](mdb-roles-permissions.md). |
| متطلبات المستعرض | Microsoft Edge أو Google Chrome |
| نظام التشغيل | لإدارة الأجهزة في Microsoft Defender for Business، يجب أن تعمل أجهزتك بأحد أنظمة التشغيل التالية: <br/>- Windows 10 Business أو أحدث <br/>- Windows 10 Professional أو إصدار أحدث <br/>- Windows 10 Enterprise أو أحدث <br/>- macOS (الإصدارات الثلاثة الأحدث مدعومة)<br/><br/>تأكد من تثبيت [KB5006738](https://support.microsoft.com/topic/october-26-2021-kb5006738-os-builds-19041-1320-19042-1320-and-19043-1320-preview-ccbce6bf-ae00-4e66-9789-ce8e7ea35541) . <br/><br/>إذا كنت تدير بالفعل الأجهزة في Microsoft Intune (أو إدارة نقاط النهاية من Microsoft)، يمكنك إلحاق هذه الأجهزة ب Defender for Business. |

> [!NOTE]
> يتم استخدام [Azure Active Directory (Azure AD)](/azure/active-directory/fundamentals/active-directory-whatis) لإدارة أذونات المستخدم ومجموعات الأجهزة. يتم تضمين Azure AD في اشتراك Defender for Business. 
> - إذا لم يكن لديك اشتراك Microsoft 365 قبل بدء الإصدار التجريبي، فسيتم توفير Azure AD لك أثناء عملية التنشيط. 
> - إذا كان لديك اشتراك Microsoft 365 آخر عند بدء تشغيل الإصدار التجريبي من Defender for Business، يمكنك استخدام خدمة Azure AD الحالية. 
> - إذا كنت تستخدم [Microsoft 365 Business Premium](../../business/index.yml) عند بدء تشغيل الإصدار التجريبي من Defender for Business، فسيتوفر لديك خيار إدارة الأجهزة في Microsoft Intune. 

## <a name="next-steps"></a>الخطوات التالية

تابع إلى [الخطوة 2: تعيين الأدوار والأذونات في Microsoft Defender for Business](mdb-roles-permissions.md).
 
