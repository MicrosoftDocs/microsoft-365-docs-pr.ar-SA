---
title: إضافة مستخدمين وتعيين التراخيص في Microsoft Defender for Business
description: إضافة مستخدمين وتعيين تراخيص Defender for Business لحماية أجهزتهم
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: article
ms.prod: m365-security
ms.technology: mdb
ms.localizationpriority: medium
ms.collection: M365-security-compliance
ms.reviewer: shlomiakirav
f1.keywords: NOCSH
ms.openlocfilehash: 7d1715352ab1a1392b06cae5bfc3ee81196bf3e2
ms.sourcegitcommit: fa90763559239c4c46c5e848939126763879d8e4
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/13/2022
ms.locfileid: "66772720"
---
# <a name="add-users-and-assign-licenses-in-microsoft-defender-for-business"></a>إضافة مستخدمين وتعيين التراخيص في Microsoft Defender for Business

بمجرد التسجيل في Defender for Business، فإن خطوتك الأولى هي إضافة مستخدمين وتعيين التراخيص. تصف هذه المقالة كيفية إضافة مستخدمين وتتضمن الخطوات التالية.

## <a name="add-users-and-assign-licenses"></a>إضافة مستخدمين وتعيين التراخيص

> [!IMPORTANT]
> يجب أن تكون مسؤولا عاما لتنفيذ هذه المهمة.  الشخص الذي سجل شركتك في Microsoft 365 أو Defender for Business هو مسؤول عام بشكل افتراضي.

1. انتقل إلى مركز مسؤولي Microsoft 365 وسجل [https://admin.microsoft.com](https://admin.microsoft.com) الدخول.

2. انتقل إلى **المستخدمين النشطين للمستخدمين** > ، ثم حدد **"إضافة مستخدم**".

3. في جزء **"إعداد الأساسيات** "، املأ معلومات المستخدم الأساسية، ثم حدد **"التالي**".

   - **الاسم**: املأ الاسم الأول واسم العائلة واسم العرض واسم المستخدم.
   - **المجال** اختر المجال لحساب المستخدم. على سبيل المثال، إذا كان اسم المستخدم ، `Pat`والمجال هو `contoso.com`، فسيسجل الدخول باستخدام `pat@contoso.com`.
   - **إعدادات كلمة المرور**: اختر ما إذا كنت تريد استخدام كلمة المرور التي تم إنشاؤها تلقائيا أو لإنشاء كلمة مرور قوية خاصة بك للمستخدم. يجب على المستخدم تغيير كلمة المرور الخاصة به بعد 90 يوما. أو يمكنك تحديد خيار **مطالبة هذا المستخدم بتغيير كلمة المرور الخاصة به عند تسجيل الدخول لأول مرة**. يمكنك أيضا اختيار ما إذا كنت تريد إرسال كلمة مرور المستخدم بالبريد الإلكتروني عند إضافة المستخدم.

4. في صفحة **تعيين تراخيص المنتجات**، حدد Defender for Business (أو Microsoft 365 Business Premium). ثم اختر **"التالي**". 

   إذا لم يكن لديك أي تراخيص متوفرة، فلا يزال بإمكانك إضافة مستخدم وشراء تراخيص إضافية. لمزيد من المعلومات حول إضافة مستخدمين، راجع [إضافة مستخدمين وتعيين التراخيص في الوقت نفسه](../../admin/add-users/add-users.md).

5. في صفحة **الإعدادات الاختيارية** ، يمكنك توسيع **معلومات ملف التعريف** وتعبئة التفاصيل، مثل عنوان jo الخاص بالمستخدم والقسم والموقع وما إلى ذلك. ثم اختر **"التالي**".

6. في صفحة **المراجعة والانتهاء** ، راجع التفاصيل، ثم حدد **"إنهاء الإضافة** " لإضافة المستخدم. إذا كنت بحاجة إلى إجراء أي تغييرات، فاختر **"رجوع** " للعودة إلى صفحة سابقة.

## <a name="next-steps"></a>الخطوات التالية

- [تفضّل بزيارة مدخل Microsoft 365 Defender](mdb-get-started.md)
- [استخدم معالج الإعداد في Defender for Business](mdb-use-wizard.md).