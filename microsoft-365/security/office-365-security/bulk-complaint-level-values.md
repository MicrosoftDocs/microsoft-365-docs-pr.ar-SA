---
title: قيم مستوى الشكوى المجمعة
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
description: يمكن للمسؤولين التعرف على قيم مستوى الشكوى المجمعة (BCL) المستخدمة في Exchange Online Protection (EOP).
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 8c50ca25a355ca142e36c67d03fad42c3aa461a2
ms.sourcegitcommit: b3530441288b2bc44342e00e9025a49721796903
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/20/2022
ms.locfileid: "63679863"
---
# <a name="bulk-complaint-level-bcl-in-eop"></a>مستوى الشكوى المجمعة (BCL) في EOP

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**ينطبق على**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender Office 365 الخطة 1 الخطة 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

في Microsoft 365 المؤسسات التي بها علب بريد في Exchange Online أو مؤسسات Exchange Online Protection (EOP) مستقلة بدون علب بريد Exchange Online، يعين EOP مستوى شكاوى مجمعة (BCL) للرسائل الواردة من البريد المجمع. يضاف BCL إلى الرسالة في رأس X ويشبه مستوى الثقة في البريد العشوائي [(SCL)](spam-confidence-levels.md) المستخدم لتعريف الرسائل كرسالة عشوائية. يشير أعلى BCL إلى أن الرسالة المجمعة من المرجح أن تنشئ شكاوى (وبالتالي من المرجح أن تكون بريدا عشوائيا). تستخدم Microsoft كلا من المصادر الداخلية ومصادر  الأطراف الخارجية لتحديد البريد المجمع وتحديد BCL المناسب.

تختلف المراسلات المجمعة في أنماط الإرسال وإنشاء المحتوى وممارسات الحصول على المستلمين. يرسل مرسلو البريد المجمع الجيدون الرسائل المطلوبة ذات المحتوى ذي الصلة إلى مشتركيها. تنشئ هذه الرسائل بعض الشكوى من المستلمين. يرسل مرسلو البريد المجمعون الآخرين رسائل غير مرغوب فيها تشبه البريد العشوائي إلى حد كبير وتولد الكثير من الشكوى من المستلمين. تعرف الرسائل الواردة من مرسل بريد مجمع باسم البريد المجمع أو البريد الرمادي.

 تقوم تصفية البريد العشوائي بتعيين الرسائل  كبريد إلكتروني مجمع استنادا إلى حد BCL (القيمة الافتراضية أو القيمة التي تحددها) وتأخذ الإجراء المحدد على الرسالة (الإجراء الافتراضي هو تسليم الرسالة إلى مجلد البريد الإلكتروني غير الهام للمستلم). لمزيد من المعلومات، راجع [تكوين سياسات](configure-your-spam-filter-policies.md) مكافحة البريد العشوائي وما الفرق بين البريد الإلكتروني غير الهام [والبريد الإلكتروني المجمع؟](what-s-the-difference-between-junk-email-and-bulk-email.md)

يتم وصف عتبات BCL في الجدول التالي.

|BCL|الوصف|
|:---:|---|
|0|الرسالة ليست من مرسل مجمع.|
|1, 2, 3|يتم إرسال الرسالة من مرسل مجمع ويولد بعض الشكوى.|
|4, 5, 6, 7<sup>\*</sup>|يتم إرسال الرسالة من مرسل مجمع ينشئ عددا مختلطا من الشكوى.|
|8, 9|الرسالة مرسلة من مرسل مجمع ينتج عنها عدد كبير من الشكوى.|

<sup>\*</sup> هذه هي قيمة العتبة الافتراضية المستخدمة في سياسات مكافحة البريد العشوائي.
