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
ms.openlocfilehash: 1114bebe4b57f89989b0e21a3d73a72fd1b3e99e
ms.sourcegitcommit: fa90763559239c4c46c5e848939126763879d8e4
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/13/2022
ms.locfileid: "66772872"
---
# <a name="microsoft-defender-for-business-requirements"></a>متطلبات Microsoft Defender for Business

تصف هذه المقالة متطلبات Defender for Business.

## <a name="what-to-do"></a>ما يجب فعله

1. [راجع المتطلبات وتأكد من تلبيتها](#review-the-requirements).
2. [تابع إلى خطواتك التالية](#next-steps).


## <a name="review-the-requirements"></a>مراجعة المتطلبات

يسرد الجدول التالي المتطلبات الأساسية التي تحتاجها لتكوين Defender for Business واستخدامه.

| شرط | الوصف |
|:---|:---|
| الاشتراك | Microsoft 365 Business Premium أو Defender for Business (مستقل). اطلع [على كيفية الحصول على Defender for Business](get-defender-business.md).<p>لاحظ أنه إذا كان لديك اشتراكات متعددة، فإن أعلى اشتراك له الأسبقية. على سبيل المثال، إذا كان لديك Microsoft Defender لنقطة النهاية الخطة 2 (الاشتراك الذي تم شراؤه أو الاشتراك التجريبي)، وتحصل على Defender for Business، فإن Defender for Endpoint Plan 2 له الأسبقية. في هذه الحالة، لن ترى تجربة Defender for Business. هل ترى [ماذا يحدث إذا كان لدي مزيج من اشتراكات Microsoft 365 Defender](mdb-faq.yml#what-happens-if-i-have-a-mix-of-microsoft-endpoint-security-subscriptions)؟  |
| Datacenter | أحد مواقع مراكز البيانات التالية: <ul><li>الاتحاد الأوروبي</li><li>المملكة المتحدة</li><li>الولايات المتحدة</li></ul> |
| حسابات المستخدمين |<ul><li>يتم إنشاء حسابات المستخدمين في مركز مسؤولي Microsoft 365 ([https://admin.microsoft.com](https://admin.microsoft.com)).</li><li>يتم تعيين تراخيص Defender for Business (أو Microsoft 365 Business Premium) في مركز مسؤولي Microsoft 365.</li></ul>للحصول على تعليمات حول هذه المهمة، راجع [إضافة مستخدمين وتعيين التراخيص](mdb-add-users.md). |
| الأذونات  | للتسجيل في Defender for Business، يجب أن تكون مسؤول عمومي.<p>للوصول إلى مدخل Microsoft 365 Defender، يجب أن يكون لدى المستخدمين أحد [الأدوار التالية في Azure AD](mdb-roles-permissions.md) المعينة:<ul><li>قارئ الأمان</li><li>مسؤول الأمان</li><li>مسؤول العمومية</li></ul>لمعرفة المزيد، راجع [الأدوار والأذونات في Defender for Business](mdb-roles-permissions.md). |
| متطلبات المستعرض | Microsoft Edge أو Google Chrome |
| نظام تشغيل جهاز العميل | لإدارة الأجهزة في مدخل Microsoft 365 Defender، يجب أن تعمل أجهزتك بأحد أنظمة التشغيل التالية: <ul><li>Windows 10 أو 11 Business</li><li>Windows 10 أو 11 Professional</li><li>Windows 10 أو 11 Enterprise</li><li>Mac (الإصدارات الثلاثة الأحدث مدعومة)</li></ul><p>تأكد من تثبيت [KB5006738](https://support.microsoft.com/topic/october-26-2021-kb5006738-os-builds-19041-1320-19042-1320-and-19043-1320-preview-ccbce6bf-ae00-4e66-9789-ce8e7ea35541) على أجهزة Windows. <p>إذا كنت تدير أجهزة بالفعل في Microsoft Intune، يمكنك الاستمرار في استخدام مركز إدارة Microsoft إدارة نقاط النهاية. في هذه الحالة، يتم دعم أنظمة التشغيل الأخرى التالية: <ul><li>iOS وiPadOS</li><li>نظام التشغيل Android</li></ul> |
| متطلبات الخادم | إذا كنت تخطط لإلحاق مثيل من Windows Server أو Linux Server، يجب عليك تلبية المتطلبات التالية: <ul><li>تم تشغيل إعداد **ميزات المعاينة** . في مدخل Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com))، انتقل إلى **ميزات معاينة الميزات** المتقدمة **العامة** > **لنقاط النهاية** **للإعدادات** >  >  > .</li><li>نطاق فرض Windows Server قيد التشغيل. في مدخل Microsoft 365 Defender، انتقل إلى **نطاق فرض** **إدارة** >  تكوين **نقاط النهاية** **للإعدادات** >  > . حدد **"استخدام MDE" لفرض إعدادات تكوين الأمان من MEM**، وحدد  **Windows Server**، ثم حدد **"حفظ**".</li><li>تفي نقاط نهاية Linux Server [بالمتطلبات الأساسية Microsoft Defender لنقطة النهاية على Linux](../defender-endpoint/microsoft-defender-endpoint-linux.md#prerequisites).</li></ul> |

> [!NOTE]
> يتم استخدام [Azure Active Directory (Azure AD)](/azure/active-directory/fundamentals/active-directory-whatis) لإدارة أذونات المستخدم ومجموعات الأجهزة. يتم تضمين Azure AD في اشتراك Defender for Business. 
> - إذا لم يكن لديك اشتراك في Microsoft 365 قبل بدء الإصدار التجريبي، فسيتم توفير Azure AD لك أثناء عملية التنشيط. 
> - إذا كان لديك اشتراك Microsoft 365 آخر عند بدء تشغيل الإصدار التجريبي من Defender for Business، يمكنك استخدام خدمة Azure AD الموجودة. 
> - إذا كنت تستخدم [Microsoft 365 Business Premium](../../business/index.yml) عند بدء تشغيل الإصدار التجريبي من Defender for Business، فلديك خيار إدارة أجهزتك باستخدام Intune.

## <a name="next-steps"></a>الخطوات التالية

انتقل إلى [الخطوة 2: تعيين الأدوار والأذونات في Defender for Business](mdb-roles-permissions.md).
 
