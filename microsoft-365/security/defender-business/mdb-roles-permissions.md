---
title: تعيين الأدوار والأذونات في Microsoft Defender for Business
description: تعرف على كيفية تعيين الأدوار والأذونات في Microsoft Defender for Business
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: overview
ms.date: 04/01/2022
ms.prod: m365-security
ms.technology: mdb
ms.localizationpriority: medium
ms.reviewer: shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
ms.openlocfilehash: 33fb7548d2dbd231368a459cd58b9d50e7c4673e
ms.sourcegitcommit: 7aa2441c1f2cc5b4b5495d6fdb993e563f86647f
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/04/2022
ms.locfileid: "64638235"
---
# <a name="assign-roles-and-permissions-in-microsoft-defender-for-business"></a>تعيين الأدوار والأذونات في Microsoft Defender for Business

> [!IMPORTANT]
> Microsoft Defender for Business هذه Microsoft 365 Business Premium العملاء، بدءا من 1 [](../../business-premium/index.md) مارس 2022. يتم عرض Defender for Business لاشتراك مستقل في المعاينة، وسينتهى طرحه تدريجيا للعملاء وشركاء المعلومات الذين سجلوا هنا [](https://aka.ms/mdb-preview) لطلبه. تتضمن [المعاينة مجموعة أولية من السيناريوهات](mdb-tutorials.md#try-these-preview-scenarios)، وسنضيف القدرات بشكل منتظم.
> 
> تتعلق بعض المعلومات الواردة في هذه المقالة بالمنتجات/الخدمات التي تم إصدارها مسبقا التي قد يتم تعديلها بشكل كبير قبل إصدارها تجاريا. لا تقدم Microsoft أي ضمانات، صريحة أو ضمنية، للمعلومات المتوفرة هنا. 

لتنفيذ المهام في مدخل Microsoft 365 Defender، مثل تكوين Microsoft Defender for Business أو عرض التقارير أو اتخاذ إجراءات الاستجابة بشأن التهديدات التي تم الكشف عنها، يجب تعيين الأذونات المناسبة لفريق الأمان. يتم منح الأذونات من خلال الأدوار التي تم تعيينها في مدخل Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)) أو [في Azure Active Directory](/azure/active-directory/roles/manage-roles-portal). 

## <a name="what-to-do"></a>ما يجب فعله

1. [تعرف على الأدوار في Defender for Business](#roles-in-defender-for-business).

2. [عرض تعيينات الدور أو تحريرها لفريق الأمان](#view-or-edit-role-assignments).

3. [تابع إلى الخطوات التالية](#next-steps).

>
> **هل لديك دقيقة؟**
> الرجاء إجراء <a href="https://microsoft.qualtrics.com/jfe/form/SV_0JPjTPHGEWTQr4y" target="_blank">استطلاع قصير حول Microsoft Defender for Business</a>. إننا نحب أن نستمع إلى هذه التكاتف!
>

## <a name="roles-in-defender-for-business"></a>الأدوار في Defender for Business

يصف الجدول التالي الأدوار الثلاثة التي يمكن تعيينها في Defender for Business. [تعرف على المزيد حول أدوار المسؤولين](../../admin/add-users/about-admin-roles.md). <br/><br/>

| مستوى الأذونات | الوصف |
|:---|:---|
| **المسؤولون العامون** (يشار أيضا إلى المسؤولين العامين) <br/><br/> *كأفضل ممارسة، حد من عدد المسؤولين العامين.* | يمكن للمسؤولين العامين تنفيذ كل أنواع المهام. يكون الشخص الذي قام Microsoft 365 شركتك Microsoft Defender for Business مسؤول عام بشكل افتراضي. <br/><br/> يمكن للمسؤولين العامين الوصول إلى/تغيير الإعدادات عبر Microsoft 365، مثل: <br/>- مركز مسؤولي Microsoft 365 ([https://admin.microsoft.com](https://admin.microsoft.com)) <br/>- Microsoft 365 Defender المدخل ([https://security.microsoft.com](https://security.microsoft.com)) |
| **مسؤولو الأمان** (يشار أيضا إلى مسؤولي الأمان) | يمكن لمسؤولي الأمان تنفيذ المهام التالية: <br/>- عرض سياسات الأمان وإدارتها <br/>- عرض التهديدات والتنبيهات الأمنية وإدارتها (تتضمن هذه الأنشطة اتخاذ إجراءات الاستجابة على نقاط النهاية) <br/>- عرض معلومات الأمان والتقارير |
| **قارئ الأمان** | يمكن لقاري الأمان تنفيذ المهام التالية: <br/>- عرض سياسات الأمان <br/>- عرض تهديدات الأمان والتنبيهات <br/>- عرض معلومات الأمان والتقارير  |


## <a name="view-or-edit-role-assignments"></a>عرض تعيينات الدور أو تحريرها

1. انتقل إلى Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)) ثم سجل الدخول.

2. في جزء التنقل، اختر **&** الأدوار، ثم ضمن **Azure AD**، حدد **الأدوار**.

3. حدد أحد الأدوار التالية لفتح الجزء الجانبي:

   - المسؤول العام
   - مسؤول الأمان
   - قارئ الأمان

   > [!IMPORTANT]
   > توصي Microsoft بمنح الأشخاص حق الوصول إلى ما يحتاجون إليه فقط لتنفيذ مهامهم. نطلق على هذا *المفهوم أقل امتياز* للأذونات. لمعرفة المزيد، راجع [أفضل الممارسات للوصول الأقل امتيازات للتطبيقات](/azure/active-directory/develop/secure-least-privileged-access). 

4. في الجزء الجانبي، حدد **الارتباط إدارة الأعضاء في Azure AD** . يأخذك هذا الإجراء إلى Azure Active Directory (Azure AD) حيث يمكنك عرض تعيينات الدور وإدارتها.

5. حدد مستخدما لفتح ملف التعريف الخاص به، ثم اختر **الأدوار المعينة**.

   - لإضافة دور، اختر **+ إضافة واجبات**.
   - لإزالة دور، اختر **X إزالة الواجبات**. 

## <a name="need-to-add-users"></a>هل تحتاج إلى إضافة مستخدمين؟

إذا لم تكن قد أضفت مستخدمين بالفعل إلى اشتراكك، فشاهد [إضافة مستخدمين وتعيين تراخيص في الوقت نفسه](../../admin/add-users/add-users.md).

## <a name="next-steps"></a>الخطوات التالية

تابع إلى:

- [الخطوة 3: إعداد إعلامات البريد الإلكتروني](mdb-email-notifications.md)

- [الخطوة 4: الأجهزة المجهزة Microsoft Defender for Business](mdb-onboard-devices.md)