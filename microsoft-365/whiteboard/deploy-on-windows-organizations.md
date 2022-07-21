---
title: نشر Microsoft Whiteboard على أجهزة Windows 10
ms.author: chucked
author: chuckedmonson
manager: alexfaulkner
ms.reviewer: ''
audience: admin
ms.topic: article
ms.custom: ''
ms.prod: microsoft-365-enterprise
search.appverid: MET150
ms.collection: ''
ms.localizationpriority: medium
description: تعرف على كيفية نشر Microsoft Whiteboard على الأجهزة التي تعمل Windows 10 أو الإصدارات الأحدث.
ms.openlocfilehash: 31341bc446313c54d95e14efdf569ba6e0b5263f
ms.sourcegitcommit: 24827a509b3e78959ce67679646e572a0c996282
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/21/2022
ms.locfileid: "66917178"
---
# <a name="deploy-microsoft-whiteboard-on-windows-10-devices"></a>نشر Microsoft Whiteboard على أجهزة Windows 10

يمكن نشر لوح المعلومات على الأجهزة التي تعمل Windows 10 أو الأحدث باستخدام Microsoft Intune أو Microsoft Configuration Manager (المعروف سابقا Configuration Manager مركز النظام). لوح المعلومات غير معتمد على Windows Server.

- **Microsoft Intune باستخدام وضع ترخيص عبر الإنترنت** – تسمح لك هذه العملية بتحديد مجموعات من المستخدمين الذين سيتلقون حق الوصول إلى تطبيق Whiteboard.

- **microsoft Configuration Manager باستخدام التثبيت والتحديثات اليدوية دون اتصال** – تسمح لك هذه العملية بتثبيت Whiteboard ثم تحديثه يدويا كل 2-4 أسابيع.

>[!NOTE]
> نوصي باستخدام Microsoft Intune. يتطلب استخدام Microsoft Configuration Manager من تكنولوجيا المعلومات إعادة حزم التحديثات وتثبيتها باستمرار لضمان تشغيل المستخدمين لإصدار محدث.

## <a name="install-whiteboard-using-microsoft-intune"></a>تثبيت لوح المعلومات باستخدام Microsoft Intune

1. أضف Whiteboard كتطبيق متوفر باستخدام الخطوات الواردة في هذه المقالة: [إضافة تطبيقات Microsoft Store إلى Microsoft Intune](/mem/intune/apps/store-apps-windows).

2. قم بتعيين التطبيق إلى مجموعة باستخدام الخطوات الواردة في هذه المقالة: [تعيين التطبيقات إلى مجموعات ذات Microsoft Intune](/mem/intune/apps/apps-deploy).

## <a name="install-whiteboard-using-microsoft-configuration-manager"></a>تثبيت Whiteboard باستخدام Microsoft Configuration Manager

1. باستخدام حساب مسؤول عام، سجل الدخول إلى [Microsoft Store للأعمال](https://businessstore.microsoft.com).

2. في الرأس، حدد **"إدارة**".

3. في جزء التنقل الأيمن، حدد **"إعدادات"**، ثم قم بتشغيل **"إظهار التطبيقات دون اتصال**".

4. انتظر من 10 إلى 15 دقيقة حتى يتم النشر.

5. بعد ذلك، انتقل إلى [تطبيق Whiteboard](https://businessstore.microsoft.com/store/details/microsoft-whiteboard/9mspc6mp8fm4).

6. حدد **الحصول على التطبيق**، ثم اقبل شروط الترخيص.

7. ارجع إلى صفحة التطبيق.

8. في القائمة المنسدلة **"نوع الترخيص** "، حدد **"دون اتصال**".

9. حدد **"إدارة**".

10. ينقلك هذا الإجراء إلى صفحة إدارة المخزون، والتي ستوفر الآن خيار **تنزيل الحزمة للاستخدام دون اتصال**.

11. اختر إصدار البنية، ثم قم بتنزيله.

12. بمجرد تنزيل التطبيق، يمكنك نشره من خلال Configuration Manager. لإنشاء حزمة تحديث، اتبع الخطوات من 7 إلى 10 لتنزيل إصدار أحدث وتعبئته Configuration Manager.

13. لمزيد من المعلومات، راجع [تثبيت التطبيقات لجهاز](/mem/configmgr/apps/deploy-use/install-app-for-device).

## <a name="see-also"></a>راجع أيضًا

[إدارة الوصول إلى Whiteboard](manage-whiteboard-access-organizations.md)

[إدارة البيانات ل Whiteboard](manage-data-organizations.md)

[إدارة المشاركة ل Whiteboard](manage-sharing-organizations.md)

