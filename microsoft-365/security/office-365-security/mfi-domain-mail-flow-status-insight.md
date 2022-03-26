---
title: معرفة حالة تدفق البريد للمجال العلوي في لوحة معلومات تدفق البريد
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
manager: dansimp
audience: ITPro
ms.topic: conceptual
ms.localizationpriority: medium
ms.assetid: ''
ms.custom:
- seo-marvel-apr2020
description: يمكن للمسؤولين التعرف على كيفية استخدام معلومات حالة تدفق البريد للمجالات العليا في لوحة معلومات تدفق البريد في مركز التوافق ل & الأمان استكشاف مشاكل تدفق البريد المرتبطة بسجلات MX وإصلاحها.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: e4ed59e31cd21826eebf306e566610d54635f0c4
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 10/06/2021
ms.locfileid: "63566553"
---
# <a name="top-domain-mail-flow-status-insight-in-the-security--compliance-center"></a>معرفة حالة تدفق بريد المجال العلوي في مركز & الأمان

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**ينطبق على**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender Office 365 الخطة 1 الخطة 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

توفر **لك معرفة حالة تدفق البريد** للمجال العلوي [](mail-flow-insights-v2.md) في لوحة معلومات تدفق البريد [في](https://protection.office.com) مركز التوافق & الأمان حالة تدفق البريد الحالية لمنظمتك.

تساعدك هذه المعرفة على تحديد المجالات التي تواجه مشاكل في ***تدفق*** البريد وإصلاحها. على سبيل المثال، يتعذر على المجال تلقي بريد إلكتروني خارجي بسبب انتهاء صلاحية المجال أو لأن المجال لديه سجل MX غير صحيح.

![عنصر واجهة مستخدم حالة تدفق المجال العلوي في لوحة معلومات تدفق البريد في مركز & الأمان.](../../media/mfi-top-domain-mail-flow-status-widget.png)

عند النقر فوق **عرض التفاصيل** في عنصر واجهة المستخدم، تظهر  عنصر تحكم منسدل حالة المجال يعرض لك المزيد من التفاصيل حول حالة كل مجال:

- **المجال**
- **سجل MX السابق**
- **سجل MX الحالي**
- **حالة استلام البريد الإلكتروني**
- حالة **المجال: تشير** علامة الاختيار الخضراء إلى أن سجل MX الحالي (في الوقت الذي نقرت فيه فوق عنصر واجهة المستخدم) يتطابق مع القيمة التي لدينا في السجل، وقد تلقى المجال بريدا إلكترونيا خلال الساعتين الماضيتين.

  تشير X باللون الأحمر إلى أنه تم تغيير سجل MX، ولم يتلق المجال أي بريد إلكتروني خلال الساعات الستة الماضية. من المرجح أن يشير ذلك إلى أن مجالك قد انتهت صلاحيته، أو أن سجل MX قد تم تحديثه بشكل غير صحيح. تحقق من جهة تسجيل المجالات أو خدمة استضافة DNS لمعرفة ما إذا انتهت صلاحية المجال، أو إذا كان سجل MX للمجال غير صحيح.

يمكنك النقر فوق **عرض المزيد** للاطلاع على المعلومات نفسها لمزيد من المجالات.

![القائمة العلوية لالتفاصيل في معرفة حالة تدفق بريد المجال العلوي.](../../media/mfi-top-domain-mail-flow-status-view-details.png)

## <a name="see-also"></a>راجع أيضًا

للحصول على معلومات حول رؤى أخرى في لوحة معلومات تدفق البريد، راجع تحليلات تدفق البريد في مركز التوافق & [الأمان](mail-flow-insights-v2.md).
