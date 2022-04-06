---
title: إنشاء علامات الجهاز وإدارتها
description: استخدام علامات الجهاز لمجموعة الأجهزة لالتقاط السياق وتمكين إنشاء قائمة ديناميكية كجزء من حادث
keywords: العلامات، علامات الجهاز، مجموعات الأجهزة، المجموعات، المعالجة، المستوى، القواعد، المجموعة aad، الدور، تعيين، تصنيف
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 65df8553f5ee3b7dd7876557398e0d4aa22c7bd5
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/08/2022
ms.locfileid: "63583207"
---
# <a name="create-and-manage-device-tags"></a>إنشاء علامات الجهاز وإدارتها

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**
- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> هل تريد تجربة Microsoft Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

أضف علامات على الأجهزة لإنشاء انتماء مجموعة منطقي. تدعم علامات الجهاز التعيين المناسب للشبكة، مما يسمح لك بإرفاق علامات مختلفة لالتقاط السياق وتمكين إنشاء قائمة ديناميكية كجزء من حادث. يمكن استخدام العلامات كتصفية في طريقة **عرض** مخزون الجهاز أو لمجموعة الأجهزة. لمزيد من المعلومات حول تجميع الأجهزة، راجع [إنشاء مجموعات الأجهزة وإدارتها](machine-groups.md).

يمكنك إضافة علامات على الأجهزة باستخدام الطرق التالية:

- استخدام المدخل
- تعيين قيمة مفتاح تسجيل

> [!NOTE]
> قد يكون هناك بعض زمن زمن الوصول بين وقت إضافة علامة إلى جهاز ومدى توفرها في قائمة الأجهزة وصفحة الجهاز.

لإضافة علامات الجهاز باستخدام API، راجع [إضافة API علامات الجهاز أو إزالتها](add-or-remove-machine-tags.md).

## <a name="add-and-manage-device-tags-using-the-portal"></a>إضافة علامات الجهاز وإدارتها باستخدام المدخل

1. حدد الجهاز الذي تريد إدارة العلامات عليه. يمكنك تحديد جهاز أو البحث عنه من أي من طرق العرض التالية:

   - **لوحة معلومات عمليات الأمان** - حدد اسم الجهاز من القسم أهم الأجهزة التي بها تنبيهات نشطة.
   - **قائمة انتظار التنبيهات** - حدد اسم الجهاز إلى جانب أيقونة الجهاز من قائمة انتظار التنبيهات.
   - **مخزون الأجهزة** - حدد اسم الجهاز من قائمة الأجهزة.
   - **مربع البحث** - حدد الجهاز من القائمة المنسدلة وأدخل اسم الجهاز.

     يمكنك أيضا الوصول إلى صفحة التنبيه من خلال طريقتي عرض الملف وIP.

2. حدد **إدارة العلامات** من صف إجراءات الاستجابة.

    :::image type="content" alt-text="صورة للزر &quot;إدارة العلامات&quot;." source="images/manage-tags-option.png":::

3. الكتابة للعثور على العلامات أو إنشائها

    :::image type="content" alt-text="صورة لإضافة علامات على جهاز1." source="images/create-new-tag.png":::

تضاف العلامات إلى طريقة عرض الجهاز وستنعكس أيضا على طريقة عرض **مخزون** الأجهزة. يمكنك بعد ذلك **استخدام عامل تصفية** العلامات لرؤية قائمة الأجهزة ذات الصلة.

> [!NOTE]
> قد لا تعمل التصفية على أسماء العلامات التي تحتوي على أبوين.
>
> عند إنشاء علامة جديدة، يتم عرض قائمة علامات موجودة. تعرض القائمة العلامات التي تم إنشاؤها من خلال المدخل فقط. لن يتم عرض العلامات الموجودة التي تم إنشاؤها من أجهزة العميل.

يمكنك أيضا حذف العلامات من طريقة العرض هذه.

:::image type="content" alt-text="صورة لإضافة علامات على جهاز2." source="images/new-tag-label-display.png":::

## <a name="add-device-tags-by-setting-a-registry-key-value"></a>إضافة علامات الجهاز من خلال تعيين قيمة مفتاح التسجيل

> [!NOTE]
> ينطبق فقط على الأجهزة التالية:
>
> - Windows 11
> - Windows 10 الإصدار 1709 أو الإصدارات الأحدث
> - Windows Server، الإصدار 1803 أو الإصدارات الأحدث
> - Windows Server 2016‏
> - Windows Server 2012 R2
> - Windows Server 2008 R2 SP1
> - Windows 8.1
> - Windows 7 SP1

> [!NOTE]
> الحد الأقصى لعدد الأحرف التي يمكن تعيينها في علامة هو 200 حرف.

يمكن أن تكون الأجهزة ذات العلامات المماثلة في متناول يديك عندما تحتاج إلى تطبيق إجراء سياقي على قائمة معينة من الأجهزة.

استخدم إدخال مفتاح التسجيل التالي لإضافة علامة على جهاز:

- مفتاح السجل: `HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows Advanced Threat Protection\DeviceTagging\`
- قيمة مفتاح التسجيل (REG_SZ): `Group`
- بيانات مفتاح التسجيل: `Name of the tag you want to set`

> [!NOTE]
> علامة الجهاز هي جزء من تقرير معلومات الجهاز الذي يتم إنشاؤه مرة واحدة في اليوم. كبديل لذلك، يمكنك اختيار إعادة تشغيل نقطة النهاية التي ستنقل تقرير معلومات جهاز جديد.
>
> إذا كنت بحاجة إلى إزالة علامة تمت إضافتها باستخدام مفتاح السجل أعلاه، فمسح محتويات بيانات مفتاح السجل بدلا من إزالة المفتاح "مجموعة".
