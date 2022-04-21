---
title: إضافة أعضاء أو إزالتهم من حالة
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.assetid: ''
description: تعرف على كيفية إضافة الأعضاء الذين يمكنهم الوصول إلى حالة أو إزالتهم عند إدارة حالة eDiscovery (Premium).
ms.custom: seo-marvel-mar2020
ms.openlocfilehash: ae0404199506d5da18fb1579fbe6a125350afcde
ms.sourcegitcommit: caedcf7f16eed23596487d97c375d4bc4c8f3566
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/20/2022
ms.locfileid: "65001665"
---
# <a name="add-or-remove-members-from-a-case"></a>إضافة أعضاء أو إزالتهم من حالة

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

يمكنك إضافة أعضاء أو إزالتهم لإدارة من يمكنه الوصول إلى الحالة. ومع ذلك، قبل أن يتمكن أحد الأعضاء من الوصول إلى حالة eDiscovery (Premium) (وتنفيذ المهام في هذه الحالة)، يجب إضافة المستخدم إلى مجموعة أدوار eDiscovery Manager على صفحة **الأذونات** في مدخل توافق Microsoft Purview. لمزيد من المعلومات، راجع [تعيين أذونات eDiscovery](./assign-ediscovery-permissions.md).

1. في صفحة **eDiscovery (Premium)،** انتقل إلى الحالة التي تريد إضافة عضو إليها.

2. انقر فوق علامة تبويب **الإعدادات** ثم انقر فوق **"تحديد**" في لوحة **أذونات & Access**.

3. ضمن **"إدارة الأعضاء**"، انقر فوق **"إضافة** " لإضافة أعضاء إلى الحالة. يمكنك أيضا اختيار إضافة مجموعة أدوار إلى الحالة بالنقر فوق  **"إضافة"** ضمن **"إدارة مجموعات الأدوار**".

4. في قائمة الأشخاص أو مجموعات الأدوار التي يمكن إضافتها كأعضاء في الحالة، حدد خانة الاختيار إلى جانب أسماء الأشخاص أو مجموعات الأدوار التي تريد إضافتها.

   > [!NOTE]
   > عند إضافة مجموعة أدوار إلى حالة، يمكنك فقط إضافة مجموعات الأدوار التي أنت عضو فيها.

5. بعد تحديد الأشخاص أو مجموعات الأدوار لإضافتها كأعضاء في الحالة، انقر فوق **"إضافة**".

6. في الصفحة المنبثقة **"إدارة هذه الحالة** "، انقر فوق **"حفظ"** لحفظ القائمة الجديدة لأعضاء الحالة.

> [!IMPORTANT]
> إذا تمت إضافة دور أو إزالته من مجموعة أدوار أضفتها كعضو في حالة ما، فستتم إزالة مجموعة الأدوار تلقائيا كعضو في الحالة (أو في أي حالة تكون مجموعة الأدوار عضوا فيها). والسبب في ذلك هو حماية مؤسستك من توفير أذونات إضافية عن غير قصد لأعضاء حالة ما. وبالمثل، إذا تم حذف مجموعة أدوار، فستتم إزالتها من جميع الحالات التي كانت عضوا فيها. لمزيد من المعلومات، راجع [تعيين أذونات eDiscovery](assign-ediscovery-permissions.md#adding-role-groups-as-members-of-ediscovery-cases).

## <a name="removing-members-from-a-case"></a>إزالة أعضاء من حالة

يمكن [فقط لمسؤول eDiscovery](assign-ediscovery-permissions.md) إزالة الأعضاء من حالة. حتى إذا تم تعيينك إلى مجموعة أدوار eDiscovery Manager أو قمت بإنشاء الحالة في البداية، فلن تتمكن من إزالة نفسك أو أعضاء آخرين من حالة ما لم تكن أيضا مسؤول eDiscovery. لإزالة نفسك أو أعضاء آخرين من حالة ما، اتصل بمسؤول eDiscovery في مؤسستك.
