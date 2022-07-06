---
title: إنشاء قوالب التقييم في Microsoft Purview Compliance Manager
f1.keywords:
- NOCSH
ms.author: chvukosw
author: chvukosw
manager: laurawi
audience: Admin
ms.topic: article
ms.custom: admindeeplinkMAC
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
- m365solution-compliancemanager
- m365initiative-compliance
search.appverid:
- MOE150
- MET150
description: فهم كيفية إنشاء قوالب للتقييمات في Microsoft Purview Compliance Manager. إنشاء قوالب وتعديلها باستخدام ملف Excel منسق.
ms.openlocfilehash: f7198d9b7bb9c30d388924d9c1b16a79e86bb8ee
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/06/2022
ms.locfileid: "66638643"
---
# <a name="create-an-assessment-template-in-microsoft-purview-compliance-manager"></a>إنشاء قالب تقييم في Microsoft Purview Compliance Manager

لإنشاء قالب جديد خاص بك للتقييمات المخصصة في Compliance Manager، ستستخدم جدول بيانات Excel منسقا بشكل خاص لتجميع بيانات التحكم الضرورية. بعد إكمال جدول البيانات، ستقوم باستيراده إلى Compliance Manager.

للتعرف على تنسيق جدول البيانات، راجع [تنسيق بيانات قالب التقييم باستخدام Excel](compliance-manager-templates-format-excel.md).

## <a name="required-roles"></a>الأدوار المطلوبة

يمكن فقط للمستخدمين الذين لديهم دور مسؤول عمومي أو إدارة Compliance Manager إنشاء القوالب وتعديلها. تعرف على المزيد حول [الأدوار والأذونات](compliance-manager-setup.md#set-user-permissions-and-assign-roles).

## <a name="create-new-template-in-compliance-manager"></a>إنشاء قالب جديد في Compliance Manager

1. انتقل إلى صفحة **قوالب التقييم** في Compliance Manager.
2. حدد **إنشاء قالب جديد**. سيتم فتح معالج إنشاء قالب.
3. اختر نوع القالب الذي تريد إنشاؤه. في هذه **الحالة، حدد "إنشاء قالب مخصص**"، ثم حدد **"التالي**".
4. في شاشة **"تحميل الملف** "، حدد **"استعراض** " للبحث عن ملف Excel المنسق الذي يحتوي على كافة بيانات القالب المطلوبة وتحميله.
5. إذا لم تكن هناك أي مشاكل في الملف، فسيتم عرض اسم الملف الذي تم تحميله. حدد **"التالي** " للمتابعة. (إذا كنت بحاجة إلى تغيير الملف، فحدد **"تحميل ملف مختلف**").
    - إذا كان هناك خطأ في الملف، فإن رسالة الخطأ في الأعلى تشرح ما هو الخطأ. ستحتاج إلى إصلاح الملف وتحميله مرة أخرى. ستحدث أخطاء إذا تم تنسيق جدول البيانات بشكل غير صحيح، أو إذا كانت هناك معلومات غير صحيحة في حقول معينة.
6. تعرض شاشة **المراجعة والانتهاء** عدد إجراءات التحسين وعناصر التحكم والحد الأقصى للدرجة للقالب. عندما تصبح جاهزا للموافقة، حدد **"إنشاء قالب".** (إذا كنت بحاجة إلى إجراء تغييرات، فحدد **"رجوع**").)
7. تؤكد الشاشة الأخيرة إنشاء قالب جديد. حدد **"تم** " لإنهاء المعالج.
8. ستصل إلى صفحة تفاصيل القالب الجديد، حيث يمكنك [إنشاء تقييمك](compliance-manager-assessments.md#create-assessments).
