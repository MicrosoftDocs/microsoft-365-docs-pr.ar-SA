---
title: قيم مستوى الشكاوى المجمعة
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: conceptual
ms.localizationpriority: medium
search.appverid:
- MET150
ms.assetid: a5b03b3c-37dd-429e-8e9b-2c1b25031794
ms.collection:
- M365-security-compliance
description: يمكن للمسؤولين التعرف على قيم مستوى الشكاوى المجمعة (BCL) المستخدمة في Exchange Online Protection (EOP).
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 08e747b704faa18aa73110256624d70c79d0307b
ms.sourcegitcommit: 725a92b0b1555572b306b285a0e7a7614d34e5e5
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 05/24/2022
ms.locfileid: "65647370"
---
# <a name="bulk-complaint-level-bcl-in-eop"></a>مستوى الشكاوى المجمعة (BCL) في EOP

**ينطبق على**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [خطة 1 وخطة 2 من Microsoft Defender لـ Office 365](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

في المؤسسات Microsoft 365 التي تحتوي على علب بريد في Exchange Online أو مؤسسات Exchange Online Protection مستقلة (EOP) بدون علب بريد Exchange Online، يقوم EOP بتعيين مستوى شكاوى مجمع (BCL) للرسائل الواردة من علب البريد المجمعة. تتم إضافة BCL إلى الرسالة في رأس X ويشبه [مستوى الثقة في البريد العشوائي (SCL)](spam-confidence-levels.md) المستخدم لتعريف الرسائل على أنها بريد عشوائي. يشير BCL الأعلى إلى أن الرسالة المجمعة من المرجح أن تولد شكاوى (ومن ثم من المرجح أن تكون بريدا عشوائيا). تستخدم Microsoft كلا من المصادر الداخلية ومصادر الجهات الخارجية لتعريف البريد المجمع وتحديد BCL المناسب.

تختلف مراسلات البريد المجمعة في أنماط الإرسال وإنشاء المحتوى وممارسات الحصول على المستلم. يرسل البريد المجمع الجيد الرسائل المطلوبة ذات المحتوى ذي الصلة إلى المشتركين. تولد هذه الرسائل القليل من الشكاوى من المستلمين. ترسل مراسلات مجمعة أخرى رسائل غير مطلوبة تشبه البريد العشوائي إلى حد كبير وتولد العديد من الشكاوى من المستلمين. تعرف الرسائل الواردة من مرسل بريد مجمع باسم البريد المجمع أو البريد الرمادي.

 تقوم تصفية البريد العشوائي بوضع علامة على الرسائل **كبريد إلكتروني مجمع** استنادا إلى حد BCL (القيمة الافتراضية أو القيمة التي تحددها) وتتخذ الإجراء المحدد على الرسالة (الإجراء الافتراضي هو تسليم الرسالة إلى مجلد البريد الإلكتروني غير الهام للمستلم). لمزيد من المعلومات، راجع [تكوين نهج مكافحة البريد العشوائي](configure-your-spam-filter-policies.md) وما [الفرق بين البريد الإلكتروني غير الهام والبريد الإلكتروني المجمع؟](what-s-the-difference-between-junk-email-and-bulk-email.md)

يتم وصف عتبات BCL في الجدول التالي.

|BCL|الوصف|
|:---:|---|
|0|الرسالة ليست من مرسل مجمع.|
|1, 2, 3|الرسالة من مرسل مجمع ينشئ شكاوى قليلة.|
|4, 5, 6, 7<sup>\*</sup>|الرسالة من مرسل مجمع ينشئ عددا مختلطا من الشكاوى.|
|8, 9|الرسالة من مرسل مجمع ينشئ عددا كبيرا من الشكاوى.|

<sup>\*</sup> هذه هي قيمة الحد الافتراضي المستخدمة في نهج مكافحة البريد العشوائي.
