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
ms.openlocfilehash: d108064edc361f25f9301c0d4511d68d0856d817
ms.sourcegitcommit: f30616b90b382409f53a056b7a6c8be078e6866f
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 05/03/2022
ms.locfileid: "65172304"
---
# <a name="add-users-and-assign-licenses-in-microsoft-defender-for-business"></a>إضافة مستخدمين وتعيين التراخيص في Microsoft Defender for Business

بمجرد التسجيل للحصول على Microsoft Defender for Business، فإن خطوتك الأولى هي إضافة مستخدمين وتعيين التراخيص. تصف هذه المقالة كيفية إضافة مستخدمين وتتضمن الخطوات التالية.

## <a name="add-users-and-assign-licenses"></a>إضافة مستخدمين وتعيين التراخيص

> [!IMPORTANT]
> يجب أن تكون مسؤولا عاما لتنفيذ هذه المهمة.  الشخص الذي سجل شركتك للحصول على Microsoft 365 أو Microsoft Defender for Business هو مسؤول عام بشكل افتراضي.

1. انتقل إلى مركز مسؤولي Microsoft 365 وسجل [https://admin.microsoft.com](https://admin.microsoft.com) الدخول.

2. انتقل إلى **مستخدمي UsersActive** > ، ثم حدد **"إضافة مستخدم**".

3. في جزء **"إعداد الأساسيات** "، املأ معلومات المستخدم الأساسية، ثم حدد **"التالي**".

   - **الاسم**: املأ الاسم الأول واسم العائلة واسم العرض واسم المستخدم.
   - **المجال** اختر المجال لحساب المستخدم. على سبيل المثال، إذا كان اسم المستخدم ، `Pat`والمجال هو `contoso.com`، فسيسجل الدخول باستخدام `pat@contoso.com`.
   - **إعدادات كلمة المرور**: اختر ما إذا كنت تريد استخدام كلمة المرور التي تم إنشاؤها تلقائيا أو لإنشاء كلمة مرور قوية خاصة بك للمستخدم. يجب على المستخدم تغيير كلمة المرور الخاصة به بعد 90 يوما. أو يمكنك تحديد خيار **مطالبة هذا المستخدم بتغيير كلمة المرور الخاصة به عند تسجيل الدخول لأول مرة**. يمكنك أيضا اختيار ما إذا كنت تريد إرسال كلمة مرور المستخدم بالبريد الإلكتروني عند إضافة المستخدم.

4. في صفحة **تعيين تراخيص المنتجات**، حدد Microsoft Defender for Business (أو Microsoft 365 Business Premium). ثم اختر **"التالي**". 

   إذا لم يكن لديك أي تراخيص متوفرة، فلا يزال بإمكانك إضافة مستخدم وشراء تراخيص إضافية. لمزيد من المعلومات حول إضافة مستخدمين، راجع [إضافة مستخدمين وتعيين التراخيص في الوقت نفسه](../../admin/add-users/add-users.md).

5. في صفحة **الإعدادات الاختيارية** ، يمكنك توسيع **معلومات ملف التعريف** وتعبئة التفاصيل، مثل عنوان jo الخاص بالمستخدم والقسم والموقع وما إلى ذلك. ثم اختر **"التالي**".

6. في صفحة **المراجعة والانتهاء** ، راجع التفاصيل، ثم حدد **"إنهاء الإضافة** " لإضافة المستخدم. إذا كنت بحاجة إلى إجراء أي تغييرات، فاختر **"رجوع** " للعودة إلى صفحة سابقة.

## <a name="next-steps"></a>الخطوات التالية

- [تفضّل بزيارة مدخل Microsoft 365 Defender](mdb-get-started.md)
- [استخدم معالج الإعداد في Microsoft Defender for Business](mdb-use-wizard.md).