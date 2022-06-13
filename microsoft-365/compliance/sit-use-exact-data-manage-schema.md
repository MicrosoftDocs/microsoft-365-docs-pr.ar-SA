---
title: إدارة مخطط مطابقة البيانات بالضبط
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
ms.openlocfilehash: 29cfefbd6bf9bb9f92fe5ed7664575ec75adfa12
ms.sourcegitcommit: 133bf9097785309da45df6f374a712a48b33f8e9
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 06/10/2022
ms.locfileid: "66014663"
---
# <a name="manage-your-exact-data-match-schema"></a>إدارة مخطط مطابقة البيانات بالضبط

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

## <a name="editing-the-schema-for-edm-based-classification-manually"></a>تحرير مخطط التصنيف المستند إلى EDM يدويا

إذا كنت تريد إجراء تغييرات على مخطط EDM، على سبيل المثال **ملفedm.xml** ، مثل تغيير الحقول المستخدمة للتصنيف المستند إلى EDM، فاتبع الخطوات التالية:

> [!TIP]
> يمكنك تغيير مخطط EDM وملف مصدر جدول المعلومات الحساسة للاستفادة من **المطابقة القابلة للتكوين**. عند التكوين، ستتجاهل EDM اختلافات الحالة وبعض المحددات عند تقييم عنصر. وهذا يجعل من السهل تحديد مخطط xml وملفات البيانات الحساسة. لمعرفة المزيد، [استخدم حقول caseInsensitive وتجاهلDelimiters](sit-get-started-exact-data-match-create-schema.md#using-the-caseinsensitive-and-ignoreddelimiters-fields).

1. قم بتحرير ملف **edm.xml** (هذا هو الملف الذي تمت مناقشته في [إنشاء المخطط لأنواع المعلومات الحساسة المستندة إلى تطابق البيانات الدقيقة](sit-get-started-exact-data-match-create-schema.md#create-the-schema-for-exact-data-match-based-sensitive-information-types).

2. [الاتصال إلى Security & Compliance PowerShell](/powershell/exchange/connect-to-scc-powershell).

3. لتحديث مخطط قاعدة البيانات، قم بتشغيل الأمر التالي:

      ```powershell
      Set-DlpEdmSchema -FileData ([System.IO.File]::ReadAllBytes('.\\edm.xml')) -Confirm:$true
      ```

      ستتم مطالبتك بالتأكيد، كما يلي:

      > تاكيد
      >
      > هل تريد بالتأكيد تنفيذ هذا الإجراء؟
      >
      > سيتم تحديث مخطط EDM لمخزن البيانات "patientrecords".
      >
      > \[Y نعم نعم للكل \[N\] No \[L\] No للكل\[؟\]\] \[\] التعليمات (الإعداد الافتراضي هو "Y"):

      > [!TIP]
      > إذا كنت تريد إجراء التغييرات بدون تأكيد، فلا تستخدمها `-Confirm:$true` في الخطوة 3.

      > [!NOTE]
      > قد يستغرق تحديث EDMSchema بالإضافات ما بين 10 إلى 60 دقيقة. يجب أن يكتمل التحديث قبل تنفيذ الخطوات التي تستخدم الإضافات.

## <a name="removing-the-schema-for-edm-based-classification-manually"></a>إزالة مخطط التصنيف المستند إلى EDM يدويا

إذا كنت تريد إزالة المخطط الذي تستخدمه للتصنيف المستند إلى EDM، فاتبع الخطوات التالية:

1. [الاتصال إلى Security & Compliance PowerShell](/powershell/exchange/connect-to-scc-powershell).

2. قم بتشغيل الأمر التالي، مع استبدال اسم مخزن البيانات "سجلات المرضى" مع الاسم الذي تريد إزالته (باستخدام مخزن patientrecords كمثال):

      ```powershell
      Remove-DlpEdmSchema -Identity 'patientrecords'
      ```

      ستتم مطالبتك بتأكيد:

      > تاكيد
      >
      > هل تريد بالتأكيد تنفيذ هذا الإجراء؟
      >
      > ستتم إزالة مخطط EDM لمخزن البيانات "patientrecords".
      >
      > \[Y نعم نعم للكل \[N\] No \[L\] No للكل\[؟\]\] \[\] التعليمات (الإعداد الافتراضي هو "Y"):

      > [!TIP]
      > إذا كنت تريد إجراء التغييرات بدون تأكيد، فلا تستخدمها `-Confirm:$true` في الخطوة 2.

### <a name="edit-or-delete-the-edm-schema-with-the-wizard"></a>تحرير مخطط EDM أو حذفه باستخدام المعالج

1. **تطابقات البيانات الدقيقة** **لتصنيف** \> بيانات **مركز** \> التوافق المفتوح.

2. اختر **مخططات EDM**.

3. اختر EDM SIT الذي تريد تحريره.

4. اختر **تحرير مخطط EDM** أو **حذف مخطط EDM** من القائمة المنبثقة.

> [!IMPORTANT]
> إذا كنت تريد إزالة مخطط، وكان مقترنا بالفعل بنوع معلومات حساسة ل EDM، يجب أولا حذف نوع المعلومات الحساسة ل EDM، ثم يمكنك حذف المخطط.
