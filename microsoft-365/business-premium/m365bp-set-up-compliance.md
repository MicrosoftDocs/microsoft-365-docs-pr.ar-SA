---
title: إعداد نُهج التوافق
f1.keywords:
- NOCSH
ms.author: deniseb
author: denisebmsft
manager: dansimp
audience: Admin
ms.topic: how-to
ms.service: o365-administration
ms.localizationpriority: high
ms.collection:
- M365-subscription-management
- M365-identity-device-management
- Adm_TOC
ms.custom:
- MiniMaven
- MSB365
- OKR_SMB_M365
- seo-marvel-mar
- AdminSurgePortfolio
search.appverid:
- BCS160
- MET150
description: قم بإعداد ميزات التوافق لمنع فقدان البيانات والمساعدة في الحفاظ على أمان المعلومات الحساسة لعملائك.
ms.openlocfilehash: db1993a99292f9b90a3b567007b96742b0f359b2
ms.sourcegitcommit: e9692a40dfe1f8c2047699ae3301c114a01b0d3a
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/01/2022
ms.locfileid: "66857495"
---
# <a name="set-up-compliance-features"></a>إعداد نُهج التوافق


اطلع على [تعليمات Microsoft 365 للشركات الصغيرة](https://go.microsoft.com/fwlink/?linkid=2197659) على YouTube.

يتضمن اشتراكك في Microsoft 365 Business Premium ميزات التوافق والخصوصية. تساعد هذه الإمكانات على حماية بيانات شركتك، والحفاظ على أمان المعلومات الحساسة لعملائك. تم تصميم هذه المقالة لمساعدتك على بدء استخدام ميزات التوافق الخاصة بك.


## <a name="before-you-begin"></a>قبل البدء

تأكد من تعيين أحد الأدوار التالية في Azure Active Directory:

- المسؤول العام
- مسؤول التوافق

لمعرفة المزيد، راجع [بدء استخدام صفحة الأدوار](../admin/add-users/admin-roles-page.md).

## <a name="use-compliance-manager-to-get-started"></a>استخدام Compliance Manager لبدء الاستخدام

:::image type="content" source="./media/m365bp-compliancemanager.png" alt-text="لقطة شاشة ل Compliance Manager في Microsoft 365 Business Premium.":::

تتضمن Microsoft 365 Business Premium Compliance Manager، والتي يمكن أن تساعدك على البدء في إعداد ميزات التوافق الخاصة بك. وتشمل هذه الميزات منع فقدان البيانات، وإدارة دورة حياة البيانات، وإدارة المخاطر الداخلية، على سبيل المثال لا الحصر. يمكن أن يوفر لك Compliance Manager الوقت من خلال تمييز التوصيات، ونقاط التوافق، وطرق تحسين درجاتك.

فيما يلي كيفية البدء:

1. انتقل إلى [https://compliance.microsoft.com](https://compliance.microsoft.com) وسجل الدخول.

2. في جزء التنقل، اختر **Compliance Manager**.

3. في علامة التبويب **"نظرة عامة** "، راجع المعلومات. حدد عنصرا أو ارتباطا لعرض مزيد من المعلومات، أو لاتخاذ إجراءات، مثل تكوين نهج منع فقدان البيانات (DLP). على سبيل المثال، في **"الحلول" التي تؤثر على قسم النقاط** ، يمكنك تحديد الارتباط في عمود **الإجراءات المتبقية** .

   :::image type="content" source="./media/m365bp-compliancesolutions.png" alt-text="لقطة شاشة للحلول التي تؤثر على جزء درجاتك.":::

   ينقلك هذا الإجراء إلى علامة التبويب **"إجراءات التحسين** "، التي تمت تصفيتها للعنصر الذي حددته. في هذا المثال نحن ننظر في نهج DLP لتكوينها.

   :::image type="content" source="./media/m365bp-dlppoliciestoconfigure.png" alt-text="لقطة شاشة لنهج DLP لتكوينها.":::

4. في علامة التبويب **"إجراءات التحسين** "، حدد عنصرا. في مثالنا، حددنا **إنشاء نهج DLP مخصصة أو معلومات تعريف شخصية**. تحميل صفحة يوفر مزيدا من المعلومات حول النهج الذي يجب تكوينه.

   :::image type="content" source="./media/m365bp-dlppolicyinfo.png" alt-text="لقطة شاشة لمعلومات حول نهج DLP لمحتوى العميل.":::

   اتبع المعلومات الموجودة على الشاشة لإعداد نهج DLP.

لمزيد من المعلومات حول ميزات التوافق في Microsoft 365 للأعمال، راجع [وثائق Microsoft Purview](../compliance/index.yml).

## <a name="use-sensitivity-labels"></a>استخدام أوصاف الحساسية

اطلع على هذا الفيديو وغيره على [قناتنا على YouTube](https://go.microsoft.com/fwlink/?linkid=2198022).

تتوفر أوصاف الحساسية في تطبيقات Office (مثل Outlook وWord وExcel وPowerPoint). تتضمن أمثلة التسميات ما يلي:

- العاديه
- Personal
- الخاصه
- السريه

ومع ذلك، يمكنك تعريف تسميات أخرى لشركتك أيضا.

استخدم المقالات التالية لبدء استخدام تسميات الحساسية:

1. [تعرف على تسميات الحساسية](../compliance/sensitivity-labels.md).

2. [ابدأ باستخدام أوصاف الحساسية](../compliance/get-started-with-sensitivity-labels.md).

3. [إنشاء وتكوين تسميات الحساسية ونهجها](../compliance/create-sensitivity-labels.md).

4. [إظهار كيفية استخدام أوصاف الحساسية للأشخاص في شركتك](https://support.microsoft.com/office/apply-sensitivity-labels-to-your-files-and-email-in-office-2f96e7cd-d5a4-403b-8bd7-4cc636bae0f9)