---
title: المجالات الجديدة التي يتم إعادة توجيهها رؤى البريد الإلكتروني
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
manager: dansimp
audience: ITPro
ms.topic: conceptual
ms.localizationpriority: medium
ms.assetid: ''
description: يمكن للمسؤولين معرفة كيفية استخدام المجالات الجديدة التي يتم إعادة توجيهها رؤى البريد الإلكتروني في لوحة معلومات تدفق البريد في مركز التوافق ل الأمان & للتحقق من وقت إعادة توجيه المستخدمين للرسائل إلى مجالات خارجية لم يتم إعادة توجيهها من قبل.
ms.technology: mdo
ms.prod: m365-security
ms.collection: M365-security-compliance
ms.openlocfilehash: df4f9e79439d435059374dd066a5298ba73d329b
ms.sourcegitcommit: b3530441288b2bc44342e00e9025a49721796903
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/20/2022
ms.locfileid: "63679643"
---
# <a name="new-domains-being-forwarded-email-insight-in-the-security--compliance-center"></a>المجالات الجديدة التي يتم إعادة توجيهها رؤى البريد الإلكتروني في مركز التوافق & الأمان

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**ينطبق على**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender Office 365 الخطة 1 الخطة 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

هناك أسباب عمل صحيحة تدعو إلى إعادة توجيه رسائل البريد الإلكتروني إلى مستلمين خارجيين في مجالات معينة. ومع ذلك، من المريب أن يبدأ المستخدمون في مؤسستك فجأة في إعادة توجيه الرسائل إلى مجال لم يقوم فيه أي شخص في مؤسستك من قبل إعادة توجيه الرسائل إلى (مجال جديد).

قد يشير هذا الشرط إلى أن حسابات المستخدمين قد تم اختراقها. إذا كنت تشك في أن الحسابات قد تم اختراقها، فشاهد الرد [على حساب بريد إلكتروني م اختراق](responding-to-a-compromised-email-account.md).

**تطلعك** معرفة المجالات الجديدة التي يتم إعادة توجيهها [](https://protection.office.com) بالبريد الإلكتروني في مركز & الأمان على الوقت الذي يقوم فيه المستخدمون في مؤسستك ب إعادة توجيه الرسائل إلى مجالات جديدة.

تظهر هذه المعرفة فقط عند اكتشاف المشكلة، كما تظهر على صفحة [تقرير إعادة](view-mail-flow-reports.md#forwarding-report) توجيه.

![المجالات الجديدة التي يتم إعادة توجيهها رؤى البريد الإلكتروني.](../../media/mfi-new-domains-being-forwarded.png)

عند النقر فوق عنصر واجهة المستخدم، تظهر عنصر واجهة مستخدم حيث يمكنك العثور على مزيد من التفاصيل حول الرسائل التي تم إعادة توجيهها، بما في ذلك ارتباط إلى [تقرير إعادة توجيه](view-mail-flow-reports.md#forwarding-report).

![تفاصيل قائمة منسقة تظهر بعد النقر فوق المجالات الجديدة التي يتم إعادة توجيهها رؤى البريد الإلكتروني.](../../media/mfi-new-domains-being-forwarded-details.png)

يمكنك أيضا الوصول إلى صفحة التفاصيل هذه عند تحديد المعرفة الدقيقة بعد النقر فوق عرض الكل في  منطقة أهم & **توصيات** **في (** \> لوحة **معلومات التقارير أو** <https://protection.office.com/insightdashboard>).

لمنع إعادة توجيه الرسائل تلقائيا إلى مجالات خارجية، قم بتكوين مجال بعيد لبعض المجالات الخارجية أو كلها. لمزيد من المعلومات، راجع إدارة المجالات البعيدة [في Exchange Online](/Exchange/mail-flow-best-practices/remote-domains/manage-remote-domains).

## <a name="related-topics"></a>المواضيع ذات الصلة

للحصول على معلومات حول رؤى أخرى في لوحة معلومات تدفق البريد، راجع تحليلات تدفق البريد في مركز التوافق & [الأمان](mail-flow-insights-v2.md).