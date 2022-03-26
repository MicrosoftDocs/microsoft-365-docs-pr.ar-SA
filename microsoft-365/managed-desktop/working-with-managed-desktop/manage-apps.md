---
title: إدارة التطبيقات في Microsoft Managed Desktop
description: معلومات حول كيفية تحديث تطبيقات خط العمل التي يتم نشرها على أجهزة سطح المكتب المدارة من Microsoft
keywords: سطح المكتب المدار من Microsoft، Microsoft 365، الخدمة، الوثائق
ms.service: m365-md
author: tiaraquan
f1.keywords:
- NOCSH
ms.author: tiaraquan
manager: dougeby
ms.topic: article
ms.localizationpriority: medium
ms.date: 01/18/2019
ms.collection: M365-modern-desktop
ms.openlocfilehash: a51be2521924164a8c90a51fcf99328ecf511877
ms.sourcegitcommit: bae72428d229827cba4c807d9cd362417afbcccb
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 02/02/2022
ms.locfileid: "63566890"
---
# <a name="manage-line-of-business-apps-in-microsoft-managed-desktop"></a>إدارة تطبيقات خط العمل في Microsoft Managed Desktop

<!--Application management -->

هناك طريقتان لإدارة تحديثات التطبيقات، ونشر التحديثات على أجهزة سطح المكتب المدارة من Microsoft. يمكنك إجراء تحديثات التطبيق في مدخل Microsoft Managed Desktop أو Intune.

<span id="update-app-mmd" />

## <a name="update-line-of-business-apps-in-microsoft-managed-desktop"></a>تحديث تطبيقات خط العمل في Microsoft Managed Desktop

**لتحديث تطبيقات خط العمل في مدخل Microsoft Managed Desktop:**

1. سجل الدخول إلى [مدخل مسؤول سطح المكتب المدار من Microsoft](https://aka.ms/mmdportal).
1. ضمن **المخزون**، حدد **التطبيقات**.  
1. حدد التطبيق الذي تريد تحديثه، ثم حدد **تحرير**.
1. ضمن **إدارة**، حدد **خصائص**.
1. حدد **ملف حزمة التطبيق**، ثم استعرض لتحميل ملف حزمة تطبيق جديد.
1. حدد **ملف حزمة التطبيق**.
1. حدد أيقونة المجلد واستعرض موقع ملف التطبيق المحدث. حدد **فتح**. يتم تحديث معلومات التطبيق بمعلومات الحزمة.
1. تحقق من **أن إصدار التطبيق** يعكس حزمة التطبيق المحدثة.

سيتم نشر التطبيق المحدث على أجهزة المستخدم.

<span id="update-app-intune" />

## <a name="update-line-of-business-apps-in-intune"></a>تحديث تطبيقات خط العمل في Intune

**لتحديث تطبيقات خط العمل في Intune:**

1. سجل الدخول إلى [مدخل Azure](https://portal.azure.com).
2. حدد **كافة** **الخدماتIntune** > . يوجد Intune في **قسم المراقبة + الإدارة** .
3. حدد **تطبيقات العميل > التطبيقات**.
4. ابحث عن تطبيقك وحدده في قائمة التطبيقات.
5. في المقطع **نظرة عامة** ، حدد **خصائص**.
6. حدد **ملف حزمة التطبيق**.
7. حدد أيقونة المجلد واستعرض موقع ملف التطبيق المحدث. حدد **فتح**. يتم تحديث معلومات التطبيق بمعلومات الحزمة.
8. تحقق من **أن إصدار التطبيق** يعكس حزمة التطبيق المحدثة.

<span id="roll-back-app-mmd" />

## <a name="roll-back-an-app-to-a-previous-version"></a>التراجع عن تطبيق إلى إصدار سابق

عند نشر إصدار جديد من تطبيق ما، عثر على خطأ، يمكنك العودة إلى إصدار سابق. العملية الموضحة أدناه للتطبيقات التي يتم فيها إدراج النوع ك Windows **MSI أو** تطبيق Windows **(Win 32) - معاينة**

**لتراجع تطبيق خط العمل إلى إصدار سابق:**

1. سجل الدخول إلى [مدخل مسؤول سطح المكتب المدار من Microsoft](https://aka.ms/mmdportal).
2. ضمن **المخزون**، حدد **التطبيقات**.  
3. حدد التطبيق الذي تحتاج إلى التراجع فيه، ثم حدد **تحرير**.
4. ضمن **إدارة**، حدد **خصائص**.
    - بالنسبة **Windows تطبيق MSI لخط العمل**، حدد معلومات التطبيق، ثم ضمن **تجاهل** إصدار التطبيق، حدد **نعم**.
    - بالنسبة **Windows التطبيق (Win 32) -** معاينة التطبيقات، حدد **معلومات** التطبيق، وحدد قواعد **الكشف**، ثم حدد **إضافة**.
    إذا كانت هناك قاعدة MSI، فتحقق من تعيين التحقق من إصدار **منتج MSI** إلى **لا**.
5. [Upload إصدار سابق من الملف المصدر للتطبيق](../get-started/deploy-apps.md) إلى مدخل مسؤول سطح المكتب المدار من Microsoft.  
