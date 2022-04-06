---
title: إدارة مخطط مطابقة البيانات بدقة
f1.keywords:
- NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
audience: Admin
ms.topic: how-to
ms.service: O365-seccomp
ms.date: ''
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
search.appverid:
- MOE150
- MET150
description: تعرف على كيفية تحرير مخطط مطابقة البيانات الدقيق أو إزالته.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 8e06cb25db0a8c616b5b692a423d9827e8918dc9
ms.sourcegitcommit: 3fb76db6b34e24569417f4c8a41b99f46a780389
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/17/2022
ms.locfileid: "63583739"
---
# <a name="manage-your-exact-data-match-schema"></a>إدارة مخطط مطابقة البيانات بدقة

## <a name="editing-the-schema-for-edm-based-classification-manually"></a>تحرير مخطط التصنيف المستند إلى EDM يدويا

إذا كنت تريد إجراء تغييرات على مخطط EDM، على سبيل المثال ملف **edm.xml** ، مثل تغيير الحقول المستخدمة للتصنيف المستند إلى EDM، فاتبع الخطوات التالية:

> [!TIP]
> يمكنك تغيير مخطط EDM وملف مصدر جدول المعلومات الحساس للاستفادة من **مطابقة قابلة للتكوين**. عند تكوينه، ستتجاهل EDM اختلافات حالات العمل وبعض المفاهم عند تقييم عنصر. من خلال هذا الأمر، يصبح تعريف مخطط xml وملفات البيانات الحساسة أكثر سهولة. لمعرفة المزيد، [راجع استخدام حقول caseInsensitive وتجاهلDelimiters](sit-get-started-exact-data-match-create-schema.md#using-the-caseinsensitive-and-ignoreddelimiters-fields).

1. تحرير ملف **edm.xml** (هذا هو الملف الذي تمت مناقشته في المخطط إنشاء المخطط لأنواع المعلومات الحساسة المستندة إلى مطابقة البيانات [بدقة](sit-get-started-exact-data-match-create-schema.md#create-the-schema-for-exact-data-match-based-sensitive-information-types).

2. [الاتصال إلى مركز & التوافق PowerShell](/powershell/exchange/connect-to-scc-powershell).

3. لتحديث مخطط قاعدة البيانات، قم بتشغيل الأمر التالي:

      ```powershell
      Set-DlpEdmSchema -FileData ([System.IO.File]::ReadAllBytes('.\\edm.xml')) -Confirm:$true
      ```

      وستطلب منك التأكيد، كما يلي:

      > تأكيد
      >
      > هل تريد بالتأكيد تنفيذ هذا الإجراء؟
      >
      > سيتم تحديث مخطط EDM لمخزن البيانات 'patientrecords'.
      >
      > \[Y\] نعم \[نعم\] لجميع \[N\] No \[L\] No to All \[؟\] تعليمات (الإعداد الافتراضي هو "Y"):

      > [!TIP]
      > إذا كنت تريد إجراء تغييراتك بدون تأكيد، فلا تستخدمها `-Confirm:$true` في الخطوة 3.

      > [!NOTE]
      > قد يستغرق تحديث EDMSchema مع الإضافات ما بين 10 إلى 60 دقيقة. يجب إكمال التحديث قبل تنفيذ الخطوات التي تستخدم الإضافات.

## <a name="removing-the-schema-for-edm-based-classification-manually"></a>إزالة مخطط التصنيف المستند إلى EDM يدويا

إذا كنت تريد إزالة المخطط الذي تستخدمه للتصنيف المستند إلى EDM، فاتبع الخطوات التالية:

1. [الاتصال إلى مركز & التوافق PowerShell](/powershell/exchange/connect-to-scc-powershell).

2. قم بتشغيل الأمر التالي، مع الازاحه عن اسم مخزن البيانات ل "سجلات المرضى" بالاسم الذي تريد إزالته (باستخدام مخزن المرضى كمثال):

      ```powershell
      Remove-DlpEdmSchema -Identity 'patientrecords'
      ```

      سيطلب منك تأكيد:

      > تأكيد
      >
      > هل تريد بالتأكيد تنفيذ هذا الإجراء؟
      >
      > سيتم إزالة مخطط EDM لمخزن البيانات 'patientrecords'.
      >
      > \[Y\] نعم \[نعم\] لجميع \[N\] No \[L\] No to All \[؟\] تعليمات (الإعداد الافتراضي هو "Y"):

      > [!TIP]
      > إذا كنت تريد إجراء التغييرات بدون تأكيد، فلا تستخدم في `-Confirm:$true` الخطوة 2.

### <a name="edit-or-delete-the-edm-schema-with-the-wizard"></a>تحرير مخطط EDM أو حذفه باستخدام المعالج

1. فتح **تصنيف بيانات مركز** \> **التوافق** \> **تطابقات البيانات الدقيقة**.

2. اختر **المخططات EDM**.

3. اختر EDM SIT الذي تريد تحريره.

4. اختر **تحرير مخطط EDM** أو حذف مخطط **EDM** من flyout.

> [!IMPORTANT]
> إذا كنت تريد إزالة مخطط، وكان مقترن بالفعل بنوع معلومات حساسة ل EDM، فيجب أولا حذف نوع المعلومات الحساسة ل EDM، ثم يمكنك حذف المخطط.
