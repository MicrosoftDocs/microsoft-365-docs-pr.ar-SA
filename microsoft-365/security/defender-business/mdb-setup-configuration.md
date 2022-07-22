---
title: إعداد Microsoft Defender for Business وتكوينها
description: تعرف على كيفية إعداد حل الأمان عبر الإنترنت ل Defender for Business. قم بإعداد الأجهزة ومراجعة النهج وتحرير الإعدادات حسب الحاجة.
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: overview
ms.prod: m365-security
ms.technology: mdb
ms.localizationpriority: medium
ms.reviewer: shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
- m365solution-mdb-setup
ms.openlocfilehash: e6489fa45e85c8c9561a29bfc7e47615a5c0ea33
ms.sourcegitcommit: 00948161a72d8cea8c2baba873743fc4a0e19f90
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/22/2022
ms.locfileid: "66969716"
---
# <a name="set-up-and-configure-microsoft-defender-for-business"></a>إعداد Microsoft Defender for Business وتكوينها

يوفر Defender for Business تجربة إعداد وتكوين مبسطة، مصممة خصيصا للأعمال الصغيرة والمتوسطة الحجم. استخدم هذه المقالة كدليل للعملية الشاملة.

> [!TIP]
> إذا استخدمت [معالج الإعداد](mdb-use-wizard.md)، فقد أكملت بالفعل عدة خطوات من عملية الإعداد الأساسية. في هذه الحالة، يمكنك:
> - [إلحاق المزيد من الأجهزة](mdb-onboard-devices.md)
> - [تكوين نهج الأمان وإعداداتك](mdb-configure-security-settings.md)
> - [تفضل بزيارة لوحة معلومات إدارة الثغرات الأمنية](mdb-view-tvm-dashboard.md)


## <a name="the-setup-and-configuration-process"></a>عملية الإعداد والتكوين

يصور الرسم التخطيطي التالي عملية الإعداد والتكوين الشاملة ل Defender for Business. إذا استخدمت معالج الإعداد، فمن المحتمل أن تكون قد أكملت الخطوات من 1 إلى 3، وربما الخطوة 4. 

:::image type="content" source="media/mdb-setup-process-2.png" alt-text="عملية الإعداد والتكوين ل Defender for Business.":::

| خطوه  | مقالة | الوصف  |
|---------|---------|--------|
| 1 | [مراجعة المتطلبات](mdb-requirements.md) | راجع المتطلبات، بما في ذلك أنظمة التشغيل المدعومة، ل Defender for Business. راجع [متطلبات Defender for Business](mdb-requirements.md). |
| 2 | [تعيين الأدوار والأذونات](mdb-roles-permissions.md)     | يحتاج الأشخاص في فريق الأمان إلى أذونات لتنفيذ المهام، مثل مراجعة التهديدات المكتشفة & إجراءات المعالجة، وعرض نهج تحرير &، وإعداد الأجهزة، واستخدام التقارير. يمكنك منح هذه الأذونات من خلال أدوار معينة. راجع [تعيين الأدوار والأذونات](mdb-roles-permissions.md).        |
| 3 | [إعداد إعلامات البريد الإلكتروني](mdb-email-notifications.md) | يمكنك تحديد من يجب أن يتلقى إعلامات البريد الإلكتروني عند تشغيل التنبيهات أو اكتشاف ثغرات أمنية جديدة. راجع [إعداد إعلامات البريد الإلكتروني](mdb-email-notifications.md).| 
| 4 | [إلحاق الأجهزة](mdb-onboard-devices.md)     | تم إعداد Defender for Business بحيث يمكنك الاختيار من بين عدة خيارات لإلحاق أجهزة شركتك. راجع [إلحاق الأجهزة ب Defender for Business](mdb-onboard-devices.md).         |
| 5 | [تكوين إعدادات الأمان ونهجه](mdb-configure-security-settings.md) | يمكنك الاختيار من بين عدة خيارات لتكوين إعدادات الأمان ونهجه، مثل [عملية التكوين المبسطة](mdb-simplified-configuration.md) في Defender for Business أو مركز إدارة Microsoft إدارة نقاط النهاية. راجع [تكوين إعدادات الأمان ونهجه](mdb-configure-security-settings.md). |

## <a name="next-steps"></a>الخطوات التالية

تابع إلى [الخطوة 1: مراجعة متطلبات Microsoft Defender for Business](mdb-requirements.md).
