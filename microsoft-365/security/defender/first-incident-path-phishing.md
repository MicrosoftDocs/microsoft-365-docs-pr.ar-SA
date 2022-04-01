---
title: مثال على هجوم بريد إلكتروني تصيد احتيالي
description: خطوة عبر مثال لتحليل هجوم تصيد احتيالي.
keywords: الأحداث والتنبيهات والتحري والارتباط والهجمة والأجهزة والأجهزة والمستخدمين والهويات والهوية علبة البريد والبريد الإلكتروني و365 و microsoft و m365
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
ms.topic: conceptual
search.appverid:
- MOE150
- MET150
ms.technology: m365d
ms.openlocfilehash: 112bfd63a5f3667b22378790b62f3e33fba784d6
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/08/2022
ms.locfileid: "63579574"
---
# <a name="example-of-a-phishing-email-attack"></a>مثال على هجوم بريد إلكتروني تصيد احتيالي

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**ينطبق على:**
- Microsoft 365 Defender

Microsoft 365 Defender المساعدة في الكشف عن المرفقات الضارة التي يتم تسليمها عبر البريد الإلكتروني. بما [أن Office 365](https://protection.office.com/) الأمان والتوافق يتكامل مع Microsoft 365 Defender، يمكن لمحللين الأمان رؤية التهديدات الواردة من Office 365، مثل مرفقات البريد الإلكتروني.

على سبيل المثال، تم تعيين حادث متعدد المراحل لمحلل.
 
:::image type="content" source="../../media/first-incident-path-phishing/first-incident-phishing-incident.png" alt-text="مثال لحادث متعدد المراحل."::: 

في علامة **التبويب تنبيهات** للحادث، يتم عرض التنبيهات من Defender for Office 365 و Microsoft Defender لتطبيقات السحابة. يمكن للمحلل التنقل لأسفل في تنبيهات Office 365 عن طريق تحديد تنبيهات رسائل البريد الإلكتروني. يتم عرض تفاصيل التنبيه على الجزء الجانبي.

:::image type="content" source="../../media/first-incident-path-phishing/first-incident-phishing-alerts.png" alt-text="مثال لتنبيه بريد إلكتروني.":::
 
من خلال التمرير لأسفل، يتم عرض المزيد من المعلومات، مع عرض الملفات الضارة والمستخدم الذي تم التأثير عليه.

:::image type="content" source="../../media/first-incident-path-phishing/first-incident-phishing-impact.png" alt-text="مثال على تأثير المستخدم والملف لتنبيه بريد إلكتروني.":::
  
يأخذك **تحديد فتح صفحة التنبيه** إلى التنبيه المحدد حيث يمكن عرض المعلومات المختلفة بتفاصيل أكبر عن طريق تحديد الارتباط. يمكن عرض رسالة البريد الإلكتروني الفعلية عن طريق تحديد عرض الرسائل في **المستكشف** في أسفل اللوحة.
 
:::image type="content" source="../../media/first-incident-path-phishing/first-incident-phishing-event-explorer.png" alt-text="مثال التفاصيل الخاصة بتنبيه."::: 

ويأخذ هذا المحلل إلى صفحة إدارة المخاطر حيث يتم عرض البريد الإلكتروني الموضوع والمستلم والمرسل ومعلومات أخرى. **يخبر ZAP** ضمن **الإجراءات** الخاصة المحلل بأنه تم تنفيذ ميزة إزالة تلقائية لمدة ساعة صفرية. يكشف ZAP تلقائيا عن الرسائل الضارة ورسائل البريد العشوائي ويزيلها من علب البريد عبر المؤسسة. لمزيد من المعلومات، راجع إزالة تلقائية [لمدة ساعة (ZAP) في](../office-365-security/zero-hour-auto-purge.md) Exchange Online.

يمكن اتخاذ إجراءات أخرى على رسائل معينة عن طريق تحديد **إجراءات**. 
 
:::image type="content" source="../../media/first-incident-path-phishing/first-incident-phishing-actions.png" alt-text="مثال على الإجراءات الأخرى التي يمكن اتخاذها على رسائل البريد الإلكتروني."::: 

## <a name="next-step"></a>الخطوة التالية

راجع [مسار التحقيق في الهجمات المستندة](first-incident-path-identity.md) إلى الهوية.

## <a name="see-also"></a>راجع أيضًا

- [نظرة عامة حول الأحداث](incidents-overview.md)
- [التحقيق في الأحداث](investigate-incidents.md)
- [إدارة الأحداث](manage-incidents.md)
