---
title: تعيين الأدوار والأذونات في Microsoft Defender for Business
description: تعيين أدوار لفريق الأمان عبر الإنترنت. تعرف على هذه الأدوار والأذونات في Defender for Business.
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
ms.openlocfilehash: 5b321b15e608c96a18e756c2f6634b5fb4f69e6f
ms.sourcegitcommit: 66228a5506fdceb4cbf0d55b9de3f2943740134f
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 06/15/2022
ms.locfileid: "66089451"
---
# <a name="assign-roles-and-permissions-in-microsoft-defender-for-business"></a>تعيين الأدوار والأذونات في Microsoft Defender for Business

لتنفيذ المهام في مدخل Microsoft 365 Defender، مثل تكوين Microsoft Defender for Business أو عرض التقارير أو اتخاذ إجراءات استجابة بشأن التهديدات المكتشفة، يجب تعيين الأذونات المناسبة لفريق الأمان. يتم منح الأذونات من خلال الأدوار التي يتم تعيينها في مدخل Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)) أو في [Azure Active Directory](/azure/active-directory/roles/manage-roles-portal). 

## <a name="what-to-do"></a>ما يجب فعله

1. [تعرف على الأدوار في Defender for Business](#roles-in-defender-for-business).
2. [عرض تعيينات الأدوار أو تحريرها لفريق الأمان.](#view-or-edit-role-assignments)
3. [تابع إلى خطواتك التالية](#next-steps).


## <a name="roles-in-defender-for-business"></a>الأدوار في Defender for Business

يصف الجدول التالي الأدوار الثلاثة التي يمكن تعيينها في Defender for Business. [تعرف على المزيد حول أدوار المسؤولين](../../admin/add-users/about-admin-roles.md).

| مستوى الأذونات | الوصف |
|:---|:---|
| **المسؤولون العموميون** (يشار إليهم أيضا باسم المسؤولين العموميين) <br/><br/> *وكأفضل ممارسة، قم بتحديد عدد المسؤولين العموميين.* | يمكن للمسؤولين العموميين تنفيذ جميع أنواع المهام. الشخص الذي سجل شركتك للحصول على Microsoft 365 أو Microsoft Defender for Business هو مسؤول عام بشكل افتراضي. <br/><br/> يمكن للمسؤولين العموميين الوصول/تغيير الإعدادات عبر جميع بوابات Microsoft 365، مثل: <br/>- مركز مسؤولي Microsoft 365 ([https://admin.microsoft.com](https://admin.microsoft.com)) <br/>- مدخل Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)) |
| **مسؤولو الأمان** (يشار إليهم أيضا باسم مسؤولي الأمان) | يمكن لمسؤولي الأمان تنفيذ المهام التالية: <br/>- عرض نهج الأمان وإدارتها <br/>- عرض تهديدات الأمان والتنبيهات وإدارتها (تتضمن هذه الأنشطة اتخاذ إجراءات الاستجابة على نقاط النهاية) <br/>- عرض معلومات وتقارير الأمان |
| **قارئ الأمان** | يمكن لقارئي الأمان تنفيذ المهام التالية: <br/>- عرض نهج الأمان <br/>- عرض التهديدات والتنبيهات الأمنية <br/>- عرض معلومات وتقارير الأمان  |


## <a name="view-or-edit-role-assignments"></a>عرض تعيينات الأدوار أو تحريرها

1. انتقل إلى مدخل Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)) وسجل الدخول.

2. في جزء التنقل، اختر **"أذونات" & الأدوار**، ثم ضمن **"Azure AD**"، حدد **"Roles**".

3. حدد أحد الأدوار التالية لفتح الجزء الجانبي الخاص به:

   - المسؤول العام
   - مسؤول الأمان
   - قارئ الأمان

   > [!IMPORTANT]
   > توصي Microsoft بمنح الأشخاص حق الوصول إلى ما يحتاجون إليه فقط لأداء مهامهم. نطلق على هذا المفهوم *أقل امتياز* للأذونات. لمعرفة المزيد، راجع [أفضل الممارسات للوصول الأقل امتيازا للتطبيقات](/azure/active-directory/develop/secure-least-privileged-access). 

4. في الجزء الجانبي، حدد "**إدارة الأعضاء" في ارتباط Azure AD**. ينقلك هذا الإجراء إلى Azure Active Directory (Azure AD) حيث يمكنك عرض تعيينات الأدوار وإدارتها.

5. حدد مستخدما لفتح ملف التعريف الخاص به، ثم اختر **الأدوار المعينة**.

   - لإضافة دور، اختر **+ إضافة تعيينات**.
   - لإزالة دور، اختر **X Remove assignments**. 

## <a name="need-to-add-users"></a>هل تحتاج إلى إضافة مستخدمين؟

إذا لم تكن قد أضفت مستخدمين إلى اشتراكك، فراجع [إضافة مستخدمين وتعيين التراخيص في الوقت نفسه](mdb-add-users.md).

## <a name="next-steps"></a>الخطوات التالية

تابع إلى:

- [الخطوة 3: إعداد إعلامات البريد الإلكتروني](mdb-email-notifications.md)
- [الخطوة 4: إلحاق الأجهزة Microsoft Defender for Business](mdb-onboard-devices.md)