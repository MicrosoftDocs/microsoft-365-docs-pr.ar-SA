---
title: إنشاء قوالب التقييم في Microsoft Compliance Manager
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
description: تعرف على كيفية إنشاء قوالب للتقييمات في Microsoft Compliance Manager. إنشاء قوالب وتعديلها باستخدام ملف Excel تنسيقه.
ms.openlocfilehash: 1c7ccbe01d3411ace40cfe6ccdbe4fcb4d90480b
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/08/2022
ms.locfileid: "63579948"
---
# <a name="create-an-assessment-template-in-microsoft-compliance-manager"></a>إنشاء قالب تقييم في Microsoft Compliance Manager

لإنشاء قالب جديد خاص بك للتقييمات المخصصة في إدارة التوافق، سوف تستخدم جدول بيانات تم تنسيقه Excel خاص لتجميع بيانات عنصر التحكم الضرورية. بعد إكمال جدول البيانات، سيتم استيراده إلى إدارة التوافق.

للتعرف على تنسيق جدول البيانات، راجع تنسيق بيانات قالب [التقييم باستخدام Excel](compliance-manager-templates-format-excel.md).

## <a name="required-roles"></a>الأدوار المطلوبة

يمكن للمستخدمين الذين لديهم دور مسؤول عام أو إدارة التوافق فقط إنشاء القوالب وتعديلها. تعرف على المزيد [حول الأدوار والأذونات](compliance-manager-setup.md#set-user-permissions-and-assign-roles).

## <a name="create-new-template-in-compliance-manager"></a>إنشاء قالب جديد في إدارة التوافق

1. انتقل إلى **صفحة قوالب التقييم** في إدارة التوافق.
2. حدد **إنشاء قالب جديد**. سيتم فتح معالج إنشاء قالب.
3. اختر نوع القالب الذي تريد إنشاؤه. في هذه الحالة، حدد **إنشاء قالب مخصص**، ثم حدد **التالي**.
4. في شاشة **Upload،** حدد استعراض للعثور على الملف Excel  الذي يحتوي على كل بيانات القالب المطلوبة وتحميله.
5. إذا لم تكن هناك أي مشاكل في الملف، سيتم عرض اسم الملف الذي تم تحميله. حدد **التالي** للمتابعة. (إذا كنت بحاجة إلى تغيير الملف، **فحدد Upload ملف مختلف**).
    - إذا حدث خطأ في الملف، فإن رسالة خطأ في الأعلى تشرح الخطأ. ستحتاج إلى إصلاح الملف وتحميله مرة أخرى. ستنتج الأخطاء إذا تم تنسيق جدول البيانات بشكل غير صحيح، أو إذا كانت هناك معلومات غير صحيحة في حقول معينة.
6. تعرض **شاشة المراجعة** والانتهاء عدد إجراءات التحسين و عناصر التحكم والحد الأقصى لالنتيجة الخاصة بالقالب. عندما تكون جاهزا للموافقة، حدد **إنشاء قالب.** (إذا كنت بحاجة إلى إجراء تغييرات، فحدد **الخلف**.)
7. تؤكد الشاشة الأخيرة أنه تم إنشاء قالب جديد. حدد **تم** للخروج من المعالج.
8. ستصل إلى صفحة تفاصيل القالب الجديد، حيث يمكنك [إنشاء تقييمك](compliance-manager-assessments.md#create-assessments).
