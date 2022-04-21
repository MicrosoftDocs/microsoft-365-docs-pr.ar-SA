---
title: المجالات الجديدة التي تتم إعادة توجيهها بتفاصيل البريد الإلكتروني
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
manager: dansimp
audience: ITPro
ms.topic: conceptual
ms.localizationpriority: medium
ms.assetid: ''
description: يمكن للمسؤولين معرفة كيفية استخدام المجالات الجديدة التي تتم إعادة توجيهها في لوحة معلومات تدفق البريد في مركز التوافق & الأمان للتحقق من وقت قيام المستخدمين بإعادة توجيه الرسائل إلى المجالات الخارجية التي لم تتم إعادة توجيهها أبدا.
ms.technology: mdo
ms.prod: m365-security
ms.collection: M365-security-compliance
ms.openlocfilehash: 1dbcf83d234611af1d209d83191cee24f5bee579
ms.sourcegitcommit: 45bc65972d4007b2aa7760d4457a0d2699f81926
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/20/2022
ms.locfileid: "64974334"
---
# <a name="new-domains-being-forwarded-email-insight-in-the-security--compliance-center"></a>المجالات الجديدة التي تتم إعادة توجيهها بتفاصيل البريد الإلكتروني في مركز توافق & الأمان

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**ينطبق على**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [خطة 1 وخطة 2 من Microsoft Defender لـ Office 365](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

هناك أسباب عمل صالحة لإعادة توجيه رسائل البريد الإلكتروني إلى مستلمين خارجيين في مجالات معينة. ومع ذلك، من المريب عندما يبدأ المستخدمون في مؤسستك فجأة في إعادة توجيه الرسائل إلى مجال لم يقم أي شخص في مؤسستك بإعادة توجيه الرسائل إليه (مجال جديد).

قد يشير هذا الشرط إلى اختراق حسابات المستخدمين. إذا كنت تشك في أن الحسابات قد تم اختراقها، فراجع [الاستجابة لحساب بريد إلكتروني تم اختراقه](responding-to-a-compromised-email-account.md).

تخطرك **المجالات الجديدة التي تتم إعادة توجيهها بتفاصيل البريد الإلكتروني** في [مركز التوافق & الأمان](https://protection.office.com) عندما يقوم المستخدمون في مؤسستك بإعادة توجيه الرسائل إلى مجالات جديدة.

تظهر هذه الرؤى فقط عند الكشف عن المشكلة، وتظهر في صفحة [تقرير إعادة التوجيه](view-mail-flow-reports.md#forwarding-report) .

:::image type="content" source="../../media/mfi-new-domains-being-forwarded.png" alt-text="نظرة ثاقبة حول البريد الإلكتروني للمجالات الجديدة التي تتم إعادة توجيهها" lightbox="../../media/mfi-new-domains-being-forwarded.png":::

عند النقر فوق عنصر واجهة المستخدم، تظهر قائمة منبثقة حيث يمكنك العثور على مزيد من التفاصيل حول الرسائل التي تمت إعادة توجيهها، بما في ذلك ارتباط إلى [تقرير إعادة التوجيه](view-mail-flow-reports.md#forwarding-report).

:::image type="content" source="../../media/mfi-new-domains-being-forwarded-details.png" alt-text="القائمة المنبثقة للتفاصيل التي تظهر بعد النقر فوق المجالات الجديدة التي تتم إعادة توجيهها بتفاصيل البريد الإلكتروني" lightbox="../../media/mfi-new-domains-being-forwarded-details.png":::

يمكنك أيضا الوصول إلى صفحة التفاصيل هذه عند تحديد نتيجة التحليلات بعد النقر فوق **"عرض الكل**" في **أعلى النتائج المعرفية & منطقة التوصيات** على (**لوحة معلومات** **التقارير** \> أو <https://protection.office.com/insightdashboard>).

لمنع إعادة توجيه الرسائل تلقائيا إلى المجالات الخارجية، قم بتكوين مجال بعيد لبعض المجالات الخارجية أو كلها. لمزيد من المعلومات، راجع [إدارة المجالات البعيدة في Exchange Online](/Exchange/mail-flow-best-practices/remote-domains/manage-remote-domains).

## <a name="related-topics"></a>المواضيع ذات الصلة

للحصول على معلومات حول نتائج التحليلات الأخرى في لوحة معلومات تدفق البريد، راجع [رؤى تدفق البريد في مركز التوافق & الأمان](mail-flow-insights-v2.md).
